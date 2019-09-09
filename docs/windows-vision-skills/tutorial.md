---
title: Создание собственного навыка для концепцииC#(C++/)
description: Узнайте, как создать собственный навык для концепции Windows с помощью этого руководства.
ms.author: lobourre
ms.date: 8/26/2019
ms.topic: article
keywords: Windows 10, Windows AI, навыки работы с Windows
ms.localizationpriority: medium
ms.openlocfilehash: 0b61a7261b04d8e01a3ca8ce5e9acd8a770f1cdf
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70156213"
---
# <a name="tutorial-create-your-own-windows-vision-skill-c"></a>Учебник. Создание собственного навыка для концепцийC#Windows ()

> [!NOTE]
> Некоторые сведения относятся к предварительным выпускам продуктов, которые могут быть значительно изменены до выпуска коммерческой версии. Майкрософт не дает никаких гарантий, явных или подразумеваемых, в отношении предоставленной здесь информации.

Если у вас уже есть пользовательское решение для работы с видением, в этом руководстве показано, как создать оболочку решения в навыке Windows, расширив базовый API [Microsoft. AI. Skills. скиллинтерфацепревиев][SkillInterfacePreview] .

Давайте создадим лицо тональности Analyzer, которое использует следующие возможности:

- Интерфейсы API [Windows. Media. фацеаналисис](https://docs.microsoft.com/uwp/api/windows.media.faceanalysis) и [Windows. AI. MachineLearning](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning)
- Модель машинного обучения в формате ONNX, которая определяет тональности из изображений лиц

Этот навык имеет следующие преимущества:

- Входной образ

И выводит:

- Тензорные значений оценки одиночной точности в диапазоне [0, 1] для каждого тональности, на котором он вычисляется.
- Тензорные значений float в диапазоне [0, 1] определение относительных координат ограничивающего прямоугольника: Left (x, y), Top (x, y), Right (x, y) и Bottom (x, y)

![Схема входных и выходных данных навыка Фацесентиментаналисис](../images/vision-skills-FaceSentimentAnalysis.png)

Полный исходный код для C# и C++/WinRT версий этого примера доступен в образце репозитория GitHub:

- [C#Пример навыка](https://github.com/microsoft/WindowsVisionSkillsPreview/tree/master/samples/SentimentAnalyzerCustomSkill/cs)
- [C++Пример навыка/WinRT](https://github.com/microsoft/WindowsVisionSkillsPreview/tree/master/samples/SentimentAnalyzerCustomSkill/cpp)

В этом учебнике рассматриваются следующие этапы.

1. [Реализация основных интерфейсов,](#CreateMainClasses) необходимых для навыка зрения Windows
2. [Создание nuspec](#CreateNuspec) для создания пакета NuGet
3. [Маскировка и демаскировка](#Obfuscation) файлов для скрытия содержимого

## <a name="prerequisites"></a>Предварительные требования

- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/) (или Visual Studio 2017, версия 15.7.4 или более поздняя)
- Windows 10 версии 1809 или более поздней.
- [Пакет SDK для Windows 10](https://developer.microsoft.com/windows/downloads/windows-10-sdk)версии 1809 или более поздней
- [Пакет NuGet Microsoft. AI. Skills. скиллинтерфацепревиев](https://www.nuget.org/packages/Microsoft.AI.Skills.SkillInterfacePreview/)

## 1. Создание и реализация основных классов навыков<a name="CreateMainClasses"></a>

Сначала необходимо реализовать основные классы навыков (Дополнительные сведения см. в разделе [важные понятия API](important-api-concepts.md) ):

- [искиллдескриптор](#ISkillDescriptor)
- [искиллбиндинг](#ISkillBinding)
- [Уничтожить](#ISkill)

Откройте решение пользовательской концепции в Visual Studio.

### 1\. искиллдескриптор<a name="ISkillDescriptor"></a>

Создание и реализация класса дескриптора квалификации, унаследованного от [искиллдескриптор][ISkillDescriptor] , который предоставляет сведения о навыке, предоставляет список поддерживаемых устройств выполнения (ЦП, GPU и т. д.) и выступает в качестве объекта фабрики для навыка.

1. Импортируйте пространство имен [Microsoft. AI. Skills. скиллинтерфацепревиев][SkillInterfacePreview] и создайте класс, производный от интерфейса [искиллдескриптор][ISkillDescriptor] .

    ```csharp
    ...
    using Microsoft.AI.Skills.SkillInterfacePreview;
    ...

    public sealed class FaceSentimentAnalyzerDescriptor : ISkillDescriptor
    {
        ...
    }
    ```

2. Создайте две переменные члена, которые будут содержать описания входных и выходных данных, необходимых для навыка. Затем в конструкторе дескриптора заполните их в соответствии с дескрипторами входных и выходных данных. Кроме того, создайте объект *скиллинформатион* , который предоставляет все необходимые свойства описания навыка.

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

3. Реализуйте необходимый метод, который ищет доступные Поддерживаемые устройства выполнения для выполнения навыков в и возвращает их потребителю. В нашем примере мы возвращаем ЦП и все устройства DirectX, поддерживающие D3D версии 12 или более поздней.

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

4. Реализуйте необходимые методы для создания экземпляра навыка.

    - Один из них выбирает лучшее доступное устройство:

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

    - В другом используется указанное устройство выполнения:

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

### 2\. **Искиллбиндинг**<a name="ISkillBinding"></a>

Создайте и Реализуйте класс привязки навыков, унаследованный от интерфейса [искиллбиндинг][ISkillBinding] , который содержит входные и выходные переменные, используемые и формируемые навыком.

1. Импортируйте пространство имен [Microsoft. AI. Skills. скиллинтерфацепревиев][SkillInterfacePreview] и создайте производный класс от интерфейса [искиллбиндинг][ISkillBinding] и его требуемого типа коллекции.

    ```csharp
    ...
    using Microsoft.AI.Skills.SkillInterfacePreview;
    ...

    public sealed class FaceSentimentAnalyzerBinding : IReadOnlyDictionary<string, ISkillFeature>, ISkillBinding
    {
        ...

    ```

2. Сначала создайте две переменные члена:

    - Один из них — это вспомогательный класс [висионскиллбиндингхелпер][VisionSkillBindingHelper] , предоставляемый в базовом интерфейсе для хранения функции образа входных данных с именем "инпутимаже".

    ```csharp
    private VisionSkillBindingHelper m_bindingHelper = null;
    ```

    - Другой содержит Леарнингмоделбиндинг, используемый для передачи в наш Леарнингмоделсессион, указанный в качестве аргумента в наш конструктор в дальнейшем в классе навыка.

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

    И реализуйте конструктор. Обратите внимание, что конструктор является *внутренним*; в нашей парадигме экземпляры Искиллбиндинг создаются навыком и поэтому не должны предоставлять изолированный конструктор:

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

3. Создание перечисления, которое упрощает чтение выходных данных типов тональности по навыку

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

4. Реализуйте дополнительные методы, которые упрощают получение и задание операций на привязку.

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

### В. **Уничтожить**<a name="ISkill"></a>

Создание и реализация класса навыка, унаследованного от интерфейса [Kill][ISkill] , который выполняет логику навыков и выдает выходные данные с заданным набором входных данных. Он также выступает в качестве объекта фабрики для Искиллбиндинг, производного от.

1. Импортируйте пространство имен [Microsoft. AI. Skills. скиллинтерфацепревиев][SkillInterfacePreview] и создайте производный класс от интерфейса [onkill][ISkill] .

    ```csharp
    ...
    using Microsoft.AI.Skills.SkillInterfacePreview;
    ...

    public sealed class FaceSentimentAnalyzerSkill : ISkill
    {
        ...
    ```

2. Сначала создайте две переменные члена:

    - Один для размещения Фацедетектор для поиска грани на входном изображении.

    ```csharp
    private FaceDetector m_faceDetector = null;
    ```

    - Другой для хранения Леарнингмоделсессион, используемого для вычисления модели анализа тональности:

    ```csharp
    private LearningModelSession m_winmlSession = null;
    ```

    Объявите обязательные свойства:

    ```csharp
    public ISkillDescriptor SkillDescriptor { get; private set; }
    public ISkillExecutionDevice Device { get; private set; }
    ```

    И реализуйте конструктор и статический фабричный метод. Обратите внимание, что конструктор является *частным* , а фабричный метод является *внутренним*. в нашей парадигме экземпляры уничтожения создаются с помощью дескриптора навыков и поэтому не должны предоставлять изолированный конструктор:

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

3. Затем реализуйте метод фабрики Искиллбиндинг:

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

4. Все, что остается реализованным, теперь является основной логикой навыка с помощью метода Евалуатеасинк (), объявленного в базовом интерфейсе. Сначала мы проработоспособности проверку и извлеките выходные функции для заполнения.

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

    Затем этот конкретный навык продолжается в два этапа:

    - **Шаг 1**. Запустите Фацедетектор с изображением и извлеките ограничивающий прямоугольник.

    ```csharp
            ...
            // Run face detection and retrieve face detection result
            var faceDetectionResult = await m_faceDetector.DetectFacesAsync(softwareBitmapInput);
            ...
    ```

    - **Шаг 2**. Если обнаружено лицо, измените ограничивающий прямоугольник, нормализовать его координату для простоты использования и продолжайте анализ тональностиности этой части изображения с помощью Windows. AI. MachineLearning. После завершения вывода обновите оценку каждого возможного тональности, возвращенного в качестве результата.

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

## 2. Упакуйте свой навык в NuGet<a name="CreateNuspec"></a>

Все осталось, чтобы скомпилировать свой навык и создать пакет NuGet из навыка, чтобы приложение может его принять.

([*Дополнительные сведения о пакетах NuGet*](https://docs.microsoft.com/nuget/what-is-nuget)см. здесь)

Чтобы создать пакет NuGet, необходимо написать файл *. nuspec* , как показано ниже, [см. исходный файл в репозитории Git](https://github.com/microsoft/WindowsVisionSkillsPreview/blob/master/samples/SentimentAnalyzerCustomSkill/build/Contoso.FaceSentimentAnalyzer_CS.nuspec). Этот файл состоит из двух основных разделов:

- **метаданные**: Эта часть содержит имя, описание, автора и владельца, лицензию и зависимости. Обратите внимание, что в нашем случае мы зависели от пакета NuGet [Microsoft. AI. Skills. скиллинтерфацепревиев][SkillInterfacePreview] . Этот пакет NuGet также ссылается на лицензию и запускает запрос на утверждение до приема.

- **файлы**: Эта часть указывает на скомпилированные биты и активы. Обратите внимание, что целевое расположение указывает на платформу версии UAP 10.0.17763. Это гарантирует, что приложения, принимающие пакет, предназначенный для более ранней версии, чем 10.0.17763 (минимальная версия ОС, необходимая для этого навыка), получит сообщение об ошибке.

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

Затем необходимо упаковать *. nuspec* с помощью NuGet. exe ([Скачайте с официального сайта](https://www.nuget.org/downloads)), чтобы создать файл пакета NuGet *. nupkg* .
Откройте командную строку и перейдите в расположение NuGet. exe, а затем вызовите:

```cmd
> .\nuget.exe pack <path to your .nuspec>
```

Чтобы протестировать пакет локально, можно разместить этот *nupkg* -файл в папке, заданной в качестве веб-канала NuGet в Visual Studio ([см. здесь](https://github.com/microsoft/WindowsVisionSkillsPreview/tree/master/samples/SentimentAnalyzerCustomSkill/README.md#PrivateNuGetFeed)).

Радостных, вы создали свой первый навык для концепций Windows! Вы можете отправить пакетный навык в [NuGet.org](https://www.nuget.org/).

## 3. И ещё.. Маскировка и демаскировка файлов ресурсов для скрытия интеллектуальной собственности<a name="Obfuscation"></a>

Чтобы предотвратить несанкционированное изменение или доступ к вашим навыкам (файлы моделей, образы и т. д.), вы можете замаскировать файлы как шаг перед сборкой и демаскировать файлы во время выполнения. [Пример в нашем примере GitHub](https://github.com/microsoft/WindowsVisionSkillsPreview/tree/master/samples/SentimentAnalyzerCustomSkill/cpp/Skill/FaceSentimentAnalyzer) содержит реализацию вспомогательных классов, использующих [Windows. Security. Cryptography](https://docs.microsoft.com/uwp/api/Windows.Security.Cryptography) для [маскировки](https://github.com/microsoft/WindowsVisionSkillsPreview/tree/master/samples/SentimentAnalyzerCustomSkill/cpp/Skill/Obfuscator) файлов во время компиляции и [маскировки](https://github.com/microsoft/WindowsVisionSkillsPreview/tree/master/samples/SentimentAnalyzerCustomSkill/cpp/Skill/Deobfuscator) их в среде выполнения. Обратите внимание, что эта часть показана C++только в/WinRT версии примера навыка, чтобы C# упростить эту версию.  

- Маскировка — это событие перед сборкой, которое позволяет настроить проект для выполнения всего времени или выполнить один раз и использовать выходные данные в качестве ресурса-контейнера напрямую. В этом примере используется выделенное средство компиляции (запутывания. exe). Перед вызовом этого средства в качестве события перед сборкой во время компиляции навыков необходимо убедиться в том, что вы компилируете этот инструмент. Обратите внимание, что поскольку оно выполняется на компьютере разработки во время компиляции, его можно компилировать один раз с помощью любой поддерживаемой цели и платформы (т. е. в этом случае это *Отладка/Win32*).

    Это событие перед сборкой можно задать в Visual Studio следующим образом:

- C++Проект: щелкните **правой кнопкой мыши проект навыка** — > отменить сворачивание **сборки** > выберите **событие перед сборкой** — > введите **командную строку** .
- C#Проект: **щелкните правой кнопкой мыши проект с навыками** — > выбрать **событие сборки** — > введите **командную строку события перед сборкой** .

    Эта команда: 1. Копирует файл ресурса локально 2: Шифрует файл в файл *.* шифр (может быть любым именем расширения), используя логику, определенную в, для которой требуется ключ GUID 3: Удаляет локальный файл

> [!NOTE]
> Мы рекомендуем изменить логику шифрования, предложенную в примере, чтобы сделать ее уникальной для вашего навыка.

    ```cmd
    copy $(ProjectDir)..\..\Common\emotion_ferplus.onnx $(ProjectDir) &amp;&amp; ^$(ProjectDir)..\Obfuscator\Win32\Debug\Obfuscator.exe $(ProjectDir)emotion_ferplus.onnx $(ProjectDir) emotion_ferplus.crypt 678BD455-4190-45D3-B5DA-41543283C092 &amp;&amp; ^del $(ProjectDir)emotion_ferplus.onnx
    ```

- Средство демаскировки предоставляется с помощью простого вспомогательного среда выполнения Windows компонента, принимаемого навыком. Логика расшифровки соответствует шифрованию, заданному на предыдущем шаге.

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
