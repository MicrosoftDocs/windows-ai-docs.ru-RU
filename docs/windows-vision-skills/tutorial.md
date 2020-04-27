---
title: Создание навыка компьютерного зрения (C#/C++)
description: Узнайте о том, как создать собственный навык компьютерного зрения Windows.
ms.author: lobourre
ms.date: 8/26/2019
ms.topic: article
keywords: windows 10, windows ai, windows vision skills
ms.localizationpriority: medium
ms.openlocfilehash: 0b61a7261b04d8e01a3ca8ce5e9acd8a770f1cdf
ms.sourcegitcommit: 2139506ff12b7205283288c4bbac866ddfa812f3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/24/2020
ms.locfileid: "70156213"
---
# <a name="tutorial-create-your-own-windows-vision-skill-c"></a>Руководство: Создание навыка компьютерного зрения Windows (C#)

> [!NOTE]
> Некоторые сведения относятся к предварительным версиям продуктов, которые могут быть существенно изменены перед коммерческим выпуском. Майкрософт не дает никаких гарантий, явных или подразумеваемых, в отношении предоставленной здесь информации.

Если у вас уже есть пользовательское решение компьютерного зрения, это руководство поможет вам создать оболочку для него с помощью Windows Vision Skills, расширив базовый API [Microsoft.AI.Skills.SkillInterfacePreview][SkillInterfacePreview].

Мы создадим навык анализа выражения лица, используя следующие возможности.

- API [Windows.Media.FaceAnalysis](https://docs.microsoft.com/uwp/api/windows.media.faceanalysis) и [Windows.AI.MachineLearning](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning).
- Модель машинного обучения в формате ONNX, которая выводит выражения на основе изображений лиц.

Этот навык принимает следующие данные:

- входное изображение.

И возвращает следующие данные:

- тензор значений оценки одинарной точности в диапазоне [0,1] для каждого оцениваемого выражения;
- тензор значений с плавающей запятой в диапазоне [0,1], которые определяют относительные координаты ограничивающего прямоугольника: left (x, y), top (x, y), right (x, y) и bottom (x, y).

![Схема с примером входных и выходных данных навыка FaceSentimentAnalysis](../images/vision-skills-FaceSentimentAnalysis.png)

Полный исходный код версий этого примера на C# и C++/WinRT доступен в этом репозитории GitHub:

- [пример навыка на C#](https://github.com/microsoft/WindowsVisionSkillsPreview/tree/master/samples/SentimentAnalyzerCustomSkill/cs);
- [пример навыка на C++/WinRT](https://github.com/microsoft/WindowsVisionSkillsPreview/tree/master/samples/SentimentAnalyzerCustomSkill/cpp).

В этом руководстве рассматриваются следующие процедуры:

1. [реализация основных интерфейсов](#CreateMainClasses) для навыка компьютерного зрения Windows;
2. [создание файла .nuspec](#CreateNuspec) для создания пакета NuGet;
3. [маскировка и демаскировка](#Obfuscation) файлов для скрытия содержимого.

## <a name="prerequisites"></a>Предварительные условия

- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/) (или Visual Studio 2017 версии 15.7.4 и выше);
- Windows 10 версии 1809 или более поздней.
- [пакет SDK для Windows 10](https://developer.microsoft.com/windows/downloads/windows-10-sdk) версии 1809 и выше;
- пакет NuGet [Microsoft.AI.Skills.SkillInterfacePreview](https://www.nuget.org/packages/Microsoft.AI.Skills.SkillInterfacePreview/).

## <a name="1-create-and-implement-the-main-skill-classes"></a>1. Создание и реализация основных классов навыка <a name="CreateMainClasses"></a>

Для начала нам нужно реализовать основные классы навыка (см. [важные понятия, связанные с API](important-api-concepts.md)):

- [ISkillDescriptor](#ISkillDescriptor);
- [ISkillBinding](#ISkillBinding);
- [ISkill](#ISkill).

Откройте пользовательское решение компьютерного зрения в Visual Studio.

### <a name="a-iskilldescriptor"></a>a. ISkillDescriptor <a name="ISkillDescriptor"></a>

Создайте и реализуйте класс с дескриптором навыка, наследуемый от [ISkillDescriptor][ISkillDescriptor]. Этот класс предоставляет сведения о навыке, список поддерживаемых устройств для выполнения (ЦП, GPU и т. д.) и выполняет роль объекта фабрики для навыка.

1. Импортируйте пространство имен [Microsoft.AI.Skills.SkillInterfacePreview][SkillInterfacePreview] и унаследуйте класс от интерфейса [ISkillDescriptor][ISkillDescriptor].

    ```csharp
    ...
    using Microsoft.AI.Skills.SkillInterfacePreview;
    ...

    public sealed class FaceSentimentAnalyzerDescriptor : ISkillDescriptor
    {
        ...
    }
    ```

2. Создайте два экземпляра переменных-членов, которые будут содержать описания входных и выходных данных для навыка. Затем укажите в конструкторе дескриптора соответствующие дескрипторы входных и выходных данных. Кроме того, создайте объект *SkillInformation*, который предоставляет все необходимые свойства для описания навыка.

    ```csharp
    ...
    // Member variables to hold input and output descriptions
    private List<ISkillFeatureDescriptor> m_inputSkillDesc;
    private List<ISkillFeatureDescriptor> m_outputSkillDesc;

    // Properties required by the interface
    public IReadOnlyList<ISkillFeatureDescriptor> InputFeatureDescriptors => m_inputSkillDesc;
    public IReadOnlyDictionary<string, string> Metadata => null;
    public IReadOnlyList<ISkillFeatureDescriptor> OutputFeatureDescriptors => m_outputSkillDesc;

    // Constructor
    public FaceSentimentAnalyzerDescriptor()
    {
        Information = SkillInformation.Create(
                "FaceSentimentAnalyzer", // Name
                "Finds a face in the image and infers its predominant sentiment from a set of 8 possible labels", // Description
                new Guid(0xf8d275ce, 0xc244, 0x4e71, 0x8a, 0x39, 0x57, 0x33, 0x5d, 0x29, 0x13, 0x88), // Id
                new Windows.ApplicationModel.PackageVersion() { Major = 0, Minor = 0, Build = 0, Revision = 8 }, // Version
                "Contoso Developer", // Author
                "Contoso Publishing" // Publisher
            );

        // Describe input feature
        m_inputSkillDesc = new List<ISkillFeatureDescriptor>();
        m_inputSkillDesc.Add(
            new SkillFeatureImageDescriptor(
                "InputImage", // skill input feature name
                "the input image onto which the sentiment analysis runs",
                true, // isRequired (since this is an input, it is required to be bound before the evaluation occurs)
                -1, // width
                -1, // height
                -1, // maxDimension
                BitmapPixelFormat.Nv12,
                BitmapAlphaMode.Ignore)
        );

        // Describe first output feature
        m_outputSkillDesc = new List<ISkillFeatureDescriptor>();
        m_outputSkillDesc.Add(
            new SkillFeatureTensorDescriptor(
                "FaceRectangle", // skill output feature name
                "a face bounding box in relative coordinates (left, top, right, bottom)",
                false, // isRequired (since this is an output, it automatically get populated after the evaluation occurs)
                new List<long>() { 4 }, // tensor shape
                SkillElementKind.Float)
            );

        // Describe second output feature
        m_outputSkillDesc.Add(
            new SkillFeatureTensorDescriptor(
                FaceSentimentScores, // skill output feature name
                "the prediction score for each class",
                false, // isRequired (since this is an output, it automatically get populated after the evaluation occurs)
                new List<long>() { 1, 8 }, // tensor shape
                SkillElementKind.Float)
            );
    }

    ```

3. Реализуйте обязательный метод, который ищет доступные поддерживаемые устройства для выполнения навыка и возвращает их список пользователю. В нашем примере возвращаются устройства ЦП и DirectX, поддерживающие D3D версии 12 и выше.

    ```csharp
    public IAsyncOperation<IReadOnlyList<ISkillExecutionDevice>> GetSupportedExecutionDevicesAsync()
    {
        return AsyncInfo.Run(async (token) =>
        {
            return await Task.Run(() =>
            {
                var result = new List<ISkillExecutionDevice>();

                // Add CPU as supported device
                result.Add(SkillExecutionDeviceCPU.Create());

                // Retrieve a list of DirectX devices available on the system and filter them by keeping only the ones that support DX12+ feature level
                var devices = SkillExecutionDeviceDirectX.GetAvailableDirectXExecutionDevices();
                var compatibleDevices = devices.Where((device) => (device as SkillExecutionDeviceDirectX).MaxSupportedFeatureLevel >= D3DFeatureLevelKind.D3D_FEATURE_LEVEL_12_0);
                result.AddRange(compatibleDevices);

                return result as IReadOnlyList<ISkillExecutionDevice>;
            });
        });

    ```

4. Реализуйте обязательные методы для создания экземпляра навыка.

    - Один из них выбирает лучшее устройство из числа доступных:

        ```csharp
        public IAsyncOperation<ISkill> CreateSkillAsync()
        {
            return AsyncInfo.Run(async (token) =>
            {
                // Retrieve the available execution devices
                var supportedDevices = await GetSupportedExecutionDevicesAsync();
                ISkillExecutionDevice deviceToUse = supportedDevices.First();

                // Either use the first device returned (CPU) or the highest performing GPU
                int powerIndex = int.MaxValue;
                foreach (var device in supportedDevices)
                {
                    if (device.ExecutionDeviceKind == SkillExecutionDeviceKind.Gpu)
                    {
                        var directXDevice = device as SkillExecutionDeviceDirectX;
                        if (directXDevice.HighPerformanceIndex < powerIndex)
                        {
                            deviceToUse = device;
                            powerIndex = directXDevice.HighPerformanceIndex;
                        }
                    }
                }
                return await CreateSkillAsync(deviceToUse);
            });
        }
        ```

    - Второй использует указанное устройство выполнения:

        ```csharp
        public IAsyncOperation<ISkill> CreateSkillAsync(ISkillExecutionDevice executionDevice)
        {
            return AsyncInfo.Run(async (token) =>
            {
                // Create a skill instance with the executionDevice supplied
                var skillInstance = await FaceSentimentAnalyzerSkill.CreateAsync(this, executionDevice);

                return skillInstance as ISkill;
            });
        }
        ```

### <a name="b-iskillbinding"></a>b. **ISkillBinding** <a name="ISkillBinding"></a>

Создайте и реализуйте класс привязки навыков, наследуемый от интерфейса [ISkillBinding][ISkillBinding]. Он содержит входные и выходные переменные, используемые и создаваемые этим навыком.

1. Импортируйте пространство имен [Microsoft.AI.Skills.SkillInterfacePreview][SkillInterfacePreview], а затем унаследуйте класс от интерфейса [ISkillBinding][ISkillBinding] и обязательного для него типа коллекции.

    ```csharp
    ...
    using Microsoft.AI.Skills.SkillInterfacePreview;
    ...

    public sealed class FaceSentimentAnalyzerBinding : IReadOnlyDictionary<string, ISkillFeature>, ISkillBinding
    {
        ...

    ```

2. Создайте два экземпляра переменных-членов:

    - Один из них содержит вспомогательный класс [VisionSkillBindingHelper][VisionSkillBindingHelper], предоставленный в базовом интерфейсе для хранения признака входного изображения с именем InputImage.

    ```csharp
    private VisionSkillBindingHelper m_bindingHelper = null;
    ```

    - Другой содержит привязку LearningModelBinding, которая позже в классе навыка передается в качестве аргумента в конструктор LearningModelSession.

    ```csharp
    // WinML related member variables
    internal LearningModelBinding m_winmlBinding = null;
    ```

    Объявите обязательные свойства:

    ```csharp
    // ISkillBinding
    public ISkillExecutionDevice Device => m_bindingHelper.Device;

    // IReadOnlyDictionary
    public bool ContainsKey(string key) => m_bindingHelper.ContainsKey(key);
    public bool TryGetValue(string key, out ISkillFeature value) => m_bindingHelper.TryGetValue(key, out value);
    public ISkillFeature this[string key] => m_bindingHelper[key];
    public IEnumerable<string> Keys => m_bindingHelper.Keys;
    public IEnumerable<ISkillFeature> Values => m_bindingHelper.Values;
    public int Count => m_bindingHelper.Count;
    public IEnumerator<KeyValuePair<string, ISkillFeature>> GetEnumerator() => m_bindingHelper.AsEnumerable().GetEnumerator();
    IEnumerator IEnumerable.GetEnumerator() => m_bindingHelper.AsEnumerable().GetEnumerator();
    ```

    А теперь реализуйте конструктор. Обратите внимание, что этот конструктор является *внутренним*. Так как в нашем примере экземпляры ISkillBinding создаются самим навыком, им не нужен отдельный конструктор.

    ```csharp
     // Constructor
    internal FaceSentimentAnalyzerBinding(
        ISkillDescriptor descriptor,
        ISkillExecutionDevice device,
        LearningModelSession session)
    {
        m_bindingHelper = new VisionSkillBindingHelper(descriptor, device);

        // Create WinML binding
        m_winmlBinding = new LearningModelBinding(session);
    }
    ```

3. Создание перечисление, которое упрощает чтение данных о типах выражений, создаваемых нашим навыком.

    ```csharp
    /// Defines the set of possible emotion label scored by this skill
    public enum SentimentType
    {
        neutral = 0,
        happiness,
        surprise,
        sadness,
        anger,
        disgust,
        fear,
        contempt
    };
    ```

4. Реализуйте необязательные дополнительные методы, которые упрощают получение и настройку операций для привязки.

    ```csharp
    /// Returns whether or not a face is found given the bound outputs
    public bool IsFaceFound
    {
        get
        {
            ISkillFeature feature = null;
            if (m_bindingHelper.TryGetValue(FaceSentimentAnalyzerConst.SKILL_OUTPUTNAME_FACERECTANGLE, out feature))
            {
                var faceRect = (feature.FeatureValue as SkillFeatureTensorFloatValue).GetAsVectorView();
                return !(faceRect[0] == 0.0f &&
                    faceRect[1] == 0.0f &&
                    faceRect[2] == 0.0f &&
                    faceRect[3] == 0.0f);
            }
            else
            {
                return false;
            }
        }
    }

    /// Returns the sentiment with the highest score
    public SentimentType PredominantSentiment
    {
        get
        {
            SentimentType predominantSentiment = SentimentType.neutral;
            ISkillFeature feature = null;
            if (m_bindingHelper.TryGetValue(FaceSentimentAnalyzerConst.SKILL_OUTPUTNAME_FACESENTIMENTSCORES, out feature))
            {
                var faceSentimentScores = (feature.FeatureValue as SkillFeatureTensorFloatValue).GetAsVectorView();

                float maxScore = float.MinValue;
                for (int i = 0; i < faceSentimentScores.Count; i++)
                {
                    if (faceSentimentScores[i] > maxScore)
                    {
                        predominantSentiment = (SentimentType)i;
                        maxScore = faceSentimentScores[i];
                    }
                }
            }

            return predominantSentiment;
        }
    }

    /// Returns the face rectangle
    public IReadOnlyList<float> FaceRectangle
    {
        get
        {
            ISkillFeature feature = null;
            if (m_bindingHelper.TryGetValue(FaceSentimentAnalyzerConst.SKILL_OUTPUTNAME_FACERECTANGLE, out feature))
            {
                return (feature.FeatureValue as SkillFeatureTensorFloatValue).GetAsVectorView();
            }
            else
            {
                return null;
            }
        }
    }
    ```

### <a name="c-iskill"></a>c. **ISkill** <a name="ISkill"></a>

Создайте и реализуйте класс навыка, наследуемый от интерфейса [ISkill][ISkill], который выполняет логику навыка и создает выходные данные на основе полученного набора входных данных. Он также выполняет роль объекта фабрики для дочерних классов ISkillBinding.

1. Импортируйте пространство имен [Microsoft.AI.Skills.SkillInterfacePreview][SkillInterfacePreview] и унаследуйте класс от интерфейса [ISkill][ISkill].

    ```csharp
    ...
    using Microsoft.AI.Skills.SkillInterfacePreview;
    ...

    public sealed class FaceSentimentAnalyzerSkill : ISkill
    {
        ...
    ```

2. Создайте два экземпляра переменных-членов:

    - Один для размещения FaceDetector и поиска лиц на входном изображении.

    ```csharp
    private FaceDetector m_faceDetector = null;
    ```

    - Второй для хранения LearningModelSession и вычисления модели анализа выражений.

    ```csharp
    private LearningModelSession m_winmlSession = null;
    ```

    Объявите обязательные свойства:

    ```csharp
    public ISkillDescriptor SkillDescriptor { get; private set; }
    public ISkillExecutionDevice Device { get; private set; }
    ```

    А теперь реализуйте конструктор и статический метод фабрики. Обратите внимание, что этот конструктор является *частным*, а метод фабрики — *внутренним*. Так как в нашем примере экземпляры ISkill создаются дескриптором навыком, им не нужен отдельный конструктор.

    ```csharp
     // Constructor
    private FaceSentimentAnalyzerSkill(
            ISkillDescriptor description,
            ISkillExecutionDevice device)
    {
        SkillDescriptor = description;
        Device = device;
    }

    // ISkill Factory method
    internal static IAsyncOperation<FaceSentimentAnalyzerSkill> CreateAsync(
        ISkillDescriptor descriptor,
        ISkillExecutionDevice device)
    {
        return AsyncInfo.Run(async (token) =>
        {
            // Create instance
            var skillInstance = new FaceSentimentAnalyzerSkill(descriptor, device);

            // Instantiate the FaceDetector
            skillInstance.m_faceDetector = await FaceDetector.CreateAsync();

            // Load ONNX model and instantiate LearningModel
            var modelFile = await StorageFile.GetFileFromApplicationUriAsync(new Uri($"ms-appx:///Contoso.FaceSentimentAnalyzer/emotion_ferplus.onnx"));
            var winmlModel = LearningModel.LoadFromFilePath(modelFile.Path);

            // Create LearningModelSession
            skillInstance.m_winmlSession = new LearningModelSession(winmlModel, GetWinMLDevice(device));

            return skillInstance;
        });
    }
    ```

3. Затем реализуйте метод фабрики ISkillBinding:

    ```csharp
    // ISkillBinding Factory method
    public IAsyncOperation<ISkillBinding> CreateSkillBindingAsync()
    {
        return AsyncInfo.Run((token) =>
        {
            var completedTask = new TaskCompletionSource<ISkillBinding>();
            completedTask.SetResult(new FaceSentimentAnalyzerBinding(SkillDescriptor, Device, m_winmlSession));
            return completedTask.Task;
        });
    }
    ```

4. Теперь нужно реализовать основную логику навыка в методе EvaluateAsync(), объявленном в базовом интерфейсе. Сначала мы проверим работоспособность, а затем извлечем выходные признаки для заполнения.

    ```csharp
    // Skill core logic
    public IAsyncAction EvaluateAsync(ISkillBinding binding)
    {
        FaceSentimentAnalyzerBinding bindingObj = binding as FaceSentimentAnalyzerBinding;
        if (bindingObj == null)
        {
            throw new ArgumentException("Invalid ISkillBinding parameter: This skill handles evaluation of FaceSentimentAnalyzerBinding instances only");
        }

        return AsyncInfo.Run(async (token) =>
        {
            // Retrieve input frame from the binding object
            VideoFrame inputFrame = (binding[FaceSentimentAnalyzerConst.SKILL_INPUTNAME_IMAGE].FeatureValue as SkillFeatureImageValue).VideoFrame;
            SoftwareBitmap softwareBitmapInput = inputFrame.SoftwareBitmap;

            // Retrieve a SoftwareBitmap to run face detection
            if (softwareBitmapInput == null)
            {
                if (inputFrame.Direct3DSurface == null)
                {
                    throw (new ArgumentNullException("An invalid input frame has been bound"));
                }
                softwareBitmapInput = await SoftwareBitmap.CreateCopyFromSurfaceAsync(inputFrame.Direct3DSurface);
            }

            // Retrieve face rectangle output feature from the binding object
            var faceRectangleFeature = binding[FaceSentimentAnalyzerConst.SKILL_OUTPUTNAME_FACERECTANGLE];

            // Retrieve face sentiment scores output feature from the binding object
            var faceSentimentScores = binding[FaceSentimentAnalyzerConst.SKILL_OUTPUTNAME_FACESENTIMENTSCORES];
            ...
    ```

    Затем нужно выполнить два шага.

    - **Шаг 1**. Запустите FaceDetector для изображения и извлеките ограничивающий прямоугольник лица.

    ```csharp
            ...
            // Run face detection and retrieve face detection result
            var faceDetectionResult = await m_faceDetector.DetectFacesAsync(softwareBitmapInput);
            ...
    ```

    - **Шаг 2**. Если лицо обнаружено, скорректируйте ограничивающий прямоугольник, нормализуйте его координаты, чтобы упростить использование, и переходите к анализу выражения для этой части изображения, используя Windows.AI.MachineLearning. По завершении обновите оценку для каждого возможного выражения, полученного в качестве результата.

    ```csharp
            ...
            // If a face is found, update face rectangle feature
            if (faceDetectionResult.Count > 0)
            {
                // Retrieve the face bound and enlarge it by a factor of 1.5x while also ensuring clamping to frame dimensions
                BitmapBounds faceBound = faceDetectionResult[0].FaceBox;
                var additionalOffset = faceBound.Width / 2;
                faceBound.X = Math.Max(0, faceBound.X - additionalOffset);
                faceBound.Y = Math.Max(0, faceBound.Y - additionalOffset);
                faceBound.Width = (uint)Math.Min(faceBound.Width + 2 * additionalOffset, softwareBitmapInput.PixelWidth - faceBound.X);
                faceBound.Height = (uint)Math.Min(faceBound.Height + 2 * additionalOffset, softwareBitmapInput.PixelHeight - faceBound.Y);

                // Set the face rectangle SkillFeatureValue in the skill binding object
                // note that values are in normalized coordinates between [0, 1] for ease of use
                await faceRectangleFeature.SetFeatureValueAsync(
                    new List<float>()
                    {
                            (float)faceBound.X / softwareBitmapInput.PixelWidth, // left
                            (float)faceBound.Y / softwareBitmapInput.PixelHeight, // top
                            (float)(faceBound.X + faceBound.Width) / softwareBitmapInput.PixelWidth, // right
                            (float)(faceBound.Y + faceBound.Height) / softwareBitmapInput.PixelHeight // bottom
                    });

                // Bind the WinML input frame with the adequate face bounds specified as metadata
                bindingObj.m_winmlBinding.Bind(
                    "Input3", // WinML input feature name defined in ONNX protobuf
                    inputFrame, // VideoFrame
                    new PropertySet() // VideoFrame bounds
                    {
                        { "BitmapBounds",
                            PropertyValue.CreateUInt32Array(new uint[]{ faceBound.X, faceBound.Y, faceBound.Width, faceBound.Height })
                        }
                    });

                // Run WinML evaluation
                var winMLEvaluationResult = await m_winmlSession.EvaluateAsync(bindingObj.m_winmlBinding, "");

                // Retrieve result using the WinML output feature name defined in ONNX protobuf
                var winMLModelResult = (winMLEvaluationResult.Outputs["Plus692_Output_0"] as TensorFloat).GetAsVectorView();

                // Set the SkillFeatureValue in the skill binding object related to the face sentiment scores for each possible SentimentType
                // note that we SoftMax the output of WinML to give a score normalized between [0, 1] for ease of use
                var predictionScores = SoftMax(winMLModelResult);
                await faceSentimentScores.SetFeatureValueAsync(predictionScores);
            }
            else // if no face found, reset output SkillFeatureValues with 0s
            {
                await faceRectangleFeature.SetFeatureValueAsync(FaceSentimentAnalyzerConst.ZeroFaceRectangleCoordinates);
                await faceSentimentScores.SetFeatureValueAsync(FaceSentimentAnalyzerConst.ZeroFaceSentimentScores);
            }
        });
    }
    ```

## <a name="2-package-your-skill-to-nuget"></a>2. Упаковка навыка в пакет NuGet <a name="CreateNuspec"></a>

Теперь вам нужно скомпилировать навык и создать на его основе пакет NuGet, чтобы приложение могло его обрабатывать.

([*Подробнее о пакетах NuGet*](https://docs.microsoft.com/nuget/what-is-nuget))

Чтобы создать пакет NuGet, запишите данные в *NUSPEC*-файл в представленном ниже формате ([см. исходный файл в репозитории Git](https://github.com/microsoft/WindowsVisionSkillsPreview/blob/master/samples/SentimentAnalyzerCustomSkill/build/Contoso.FaceSentimentAnalyzer_CS.nuspec)). Этот файл состоит из двух основных разделов:

- **metadata**. Эта часть содержит имя и описание, автора и владельца, лицензию и зависимости. Обратите внимание, что в нашем примере есть зависимость от пакета NuGet [Microsoft.AI.Skills.SkillInterfacePreview][SkillInterfacePreview]. Этот пакет NuGet также содержит ссылку на лицензию и активирует запрос на подтверждение лицензии перед приемом данных.

- **files**. Этот раздел указывает на скомпилированные двоичные данные и активы. Обратите внимание, что целевое расположение указывает на платформу версии uap10.0.17763. Если приложение, которое принимает такой пакет, предназначено для использования более ранней версии, чем 10.0.17763 (это минимальная необходимая версия ОС для этого навыка), мы получим сообщение об ошибке.

```xml
<?xml version="1.0" encoding="utf-8"?>
<package xmlns="http://schemas.microsoft.com/packaging/2010/07/nuspec.xsd">
    <metadata>
        <!-- Required elements-->
        <id>Contoso.FaceSentimentAnalyzer_CS</id>
        <title>Contoso.FaceSentimentAnalyzer_CS</title>
        <version>0.0.0.5</version>
        <description>Face Sentiment Analyzer skill sample that extends the Microsoft.AI.Skills.SkillInterfacePreview APIs</description>
        <authors>Contoso</authors>
        <owners>Contoso</owners>
        <copyright>Copyright (c) Microsoft Corporation.  All rights reserved.</copyright>
        <requireLicenseAcceptance>true</requireLicenseAcceptance>
        <licenseUrl>https://github.com/Microsoft/WindowsVisionSkillsPreview/blob/master/license/doc/LICENSE_package.md</licenseUrl>
        <projectUrl>https://github.com/Microsoft/WindowsVisionSkillsPreview</projectUrl>
        <iconUrl>https://github.com/Microsoft/WindowsVisionSkillsPreview/blob/master/doc/Logo.png?raw=true</iconUrl>
        <releaseNotes>v0.0.0.5 release https://github.com/Microsoft/WindowsVisionSkillsPreview/releases</releaseNotes>
        <dependencies>
            <dependency id="Microsoft.AI.Skills.SkillInterfacePreview" version="0.5.2.12" />
        </dependencies>
        <tags>ComputerVision AI VisionSkill</tags>
    </metadata>

    <files>
        <!-- WinMD, Intellisense and resource files-->
        <file src="..\common\emotion_ferplus.onnx" target="lib\uap10.0.17763\Contoso.FaceSentimentAnalyzer" />
        <file src="..\cs\FaceSentimentAnalyzer\bin\Release\Contoso.FaceSentimentAnalyzer.winmd" target="lib\uap10.0.17763" />
        <file src="..\cs\FaceSentimentAnalyzer\bin\Release\Contoso.FaceSentimentAnalyzer.pri" target="lib\uap10.0.17763" />
        <file src="..\common\Contoso.FaceSentimentAnalyzer.xml" target="lib\uap10.0.17763" />
    </files>
</package>
```

Теперь упакуйте *NUSPEC*-файл с помощью nuget.exe ([его можно скачать на официальном сайте](https://www.nuget.org/downloads)) и получите *NUPKG*-файл с пакетом NuGet.
Откройте командную строку и перейдите в каталог, где размещается средство nuget.exe, а затем вызовите такую команду:

```cmd
> .\nuget.exe pack <path to your .nuspec>
```

Для локального тестирования пакета этот *NUPKG*-файл можно разместить в папке, которую вы указали в Visual Studio в качестве веб-канала NuGet (см. [инструкции](https://github.com/microsoft/WindowsVisionSkillsPreview/tree/master/samples/SentimentAnalyzerCustomSkill/README.md#PrivateNuGetFeed)).

Поздравляем, вы создали свой первый навык компьютерного зрения Windows! Готовый пакет навыка можно передать на сайт [NuGet.org](https://www.nuget.org/).

## <a name="3-one-more-thing-obfuscating-and-deobfuscating-asset-files-to-conceal-your-intellectual-property"></a>3. И последнее: маскировка и демаскировка файлов для скрытия скрыть интеллектуальной собственности<a name="Obfuscation"></a>

Чтобы предотвратить несанкционированное изменение активов навыка (файлов моделей, изображений и т. д.) или получение доступа к ним, вы можете дополнительно замаскировать файлы перед сборкой, а затем демаскировать их во время выполнения. Наш [пример на сайте GitHub](https://github.com/microsoft/WindowsVisionSkillsPreview/tree/master/samples/SentimentAnalyzerCustomSkill/cpp/Skill/FaceSentimentAnalyzer) содержит реализацию вспомогательных классов, которые с помощью [Windows.Security.Cryptography](https://docs.microsoft.com/uwp/api/Windows.Security.Cryptography) [маскируют](https://github.com/microsoft/WindowsVisionSkillsPreview/tree/master/samples/SentimentAnalyzerCustomSkill/cpp/Skill/Obfuscator) файлы во время компиляции и [демаскируют](https://github.com/microsoft/WindowsVisionSkillsPreview/tree/master/samples/SentimentAnalyzerCustomSkill/cpp/Skill/Deobfuscator) их во время выполнения. Обратите внимание, что эта часть представлена только в версии навыка для C++/WinRT, чтобы упростить реализацию для C#.  

- Маскировка — это событие, выполняемое для проекта перед сборкой либо постоянно, либо однократно с последующим использованием выходных данных в качестве ресурса напрямую. В этом примере используется специальное компилируемое средство (Obfuscator.exe). Прежде чем вызывать это средство в качестве события перед сборкой, вам нужно скомпилировать его. Обратите внимание, что оно выполняется во время компиляции на компьютере разработки, поэтому его можно скомпилировать один раз для любого сочетания платформы и целевого устройства (в нашем примере это *Debug/Win32*).

    Это событие перед сборкой можно задать в Visual Studio следующим образом:

- Для проекта C++: **щелкните проект навыка правой кнопкой мыши**, разверните **Событие сборки**, выберите **Событие перед сборкой** и укажите **Командная строка**;
- Для проекта C#: **щелкните проект навыка правой кнопкой мыши**, разверните **Событие сборки** и укажите **Командная строка события перед сборкой**.

    Эта команда выполняет следующие действия: 1. Копирует файл ресурса на локальное устройство. 2. Шифрует файл в *CRYPT*-файл (которому можно присвоить любое расширение) с использованием определенной логики, для которой требуется ключ GUID. 3. Удаляет файл с локального устройства.

> [!NOTE]
> Мы рекомендуем изменить логику шифрования, предложенную в нашем примере, чтобы она была уникальной для вашего навыка.

    ```cmd
    copy $(ProjectDir)..\..\Common\emotion_ferplus.onnx $(ProjectDir) &amp;&amp; ^$(ProjectDir)..\Obfuscator\Win32\Debug\Obfuscator.exe $(ProjectDir)emotion_ferplus.onnx $(ProjectDir) emotion_ferplus.crypt 678BD455-4190-45D3-B5DA-41543283C092 &amp;&amp; ^del $(ProjectDir)emotion_ferplus.onnx
    ```

- Демаскировка выполняется с помощью простого вспомогательного компонента среды выполнения Windows, принимаемого навыком. Логика демаскировки в нем соответствует логике шифрования, которую мы задали на предыдущем шаге.

    ```cpp
    // FaceSentimentAnalyzerSkill.cpp
    ...
    #include "winrt/DeobfuscationHelper.h"
    ...

    // ISkill Factory method
    Windows::Foundation::IAsyncOperation<winrt::Contoso::FaceSentimentAnalyzer::FaceSentimentAnalyzerSkill> FaceSentimentAnalyzerSkill::CreateAsync(
        ISkillDescriptor descriptor,
        ISkillExecutionDevice device)
    {
        ...

        // Load WinML model
        auto modelFile = Windows::Storage::StorageFile::GetFileFromApplicationUriAsync(Windows::Foundation::Uri(L"ms-appx:///Contoso.FaceSentimentAnalyzer/" + WINML_MODEL_FILENAME)).get();

        // Deobfuscate model file and retrieve LearningModel instance
        LearningModel learningModel = winrt::DeobfuscationHelper::Deobfuscator::DeobfuscateModelAsync(modelFile, descriptor.Id()).get();

        ...

    ```

[!INCLUDE [help](../includes/get-help-vision.md)]

[SkillInterfacePreview]: https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview

[ISkillDescriptor]: https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskilldescriptor

[ISkill]: https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskill

[ISkillBinding]: https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillbinding

[VisionSkillBindingHelper]: https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.visionskillbindinghelper
