---
author: eliotcowley
title: Создание собственных навыков vision (C#/C++)
description: Сведения о создании собственных навыков концепции Windows с помощью этого руководства.
ms.author: elcowle
ms.date: 5/10/2019
ms.topic: article
keywords: Windows 10, искусственный интеллект windows, windows визуального распознавания навыки
ms.localizationpriority: medium
ms.openlocfilehash: 6b02069ece8394f439dd2cdf8005b0fb9297645f
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66179976"
---
# <a name="tutorial-create-your-own-windows-vision-skill-c"></a>Учебник. Создание собственных навыков концепции Windows (C#)

> [!NOTE]
> Некоторая информация имеет отношение к предварительному выпуску продукта, который может быть значительно изменен перед коммерческим выпуском. Майкрософт не дает никаких гарантий, явных или подразумеваемых, в отношении предоставленной здесь информации.

Если вы уже имеется решение пользовательской службе визуального распознавания, этом руководстве показано, как перенос решения в навык концепции Windows путем расширения [Microsoft.AI.Skills.SkillInterfacePreview] [ SkillInterfacePreview] базовый API.

Давайте создадим навыка анализатора тональности лиц, использует следующие:

- [Windows.Media.FaceAnalysis](https://docs.microsoft.com/uwp/api/windows.media.faceanalysis) и [Windows.AI.MachineLearning](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning) API-интерфейсов
- Модели машинного обучения в формат ONNX, который выводит мнения, выраженные в изображений лиц

Принимает этот навык:

- Входные изображения

И выводит его:

- Тензорные значения оценки одиночной точности в диапазоне [0,1] для каждого тональности оно оценивается как
- Тензорные значений с плавающей запятой в диапазоне [0,1], определение ограничивающего прямоугольника поле относительные координаты грани: left (x, y), top (x, y), правой кнопкой мыши (x, y) и нижней (x, y)

![Схема квалификации FaceSentimentAnalysis пример входных и выходных данных](../images/vision-skills-FaceSentimentAnalysis.png)

Полный исходный код для C# и C++/WinRT версии этого примера доступен в репозитории GitHub пример:

- [C#Пример навыков](https://github.com/Microsoft/WindowsVisionSkillsPreview/tree/master/samples/SentimentAnalyzerCustomSkill/cs/FaceSentimentAnalyzer)
- [C++/ Пример навыков WinRT](https://github.com/Microsoft/WindowsVisionSkillsPreview/tree/master/samples/SentimentAnalyzerCustomSkill/cpp/FaceSentimentAnalyzer)

Этот учебник поможет выполнить:

1. [Реализация основных интерфейсов](#CreateMainClasses) необходимые для навыка концепции Windows
2. [Создание файла nuspec](#CreateNuspec) для создания пакета NuGet
3. [Запутывание и deobfuscating](#Obfuscation) файлы, чтобы скрыть их содержимого

## <a name="prerequisites"></a>Предварительные требования

- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/) (или Visual Studio 2017 версии 15.7.4 или более поздней версии)
- Windows 10, 1809 или более поздней версии
- [Пакета SDK для Windows 10](https://developer.microsoft.com/windows/downloads/windows-10-sdk), 1809 или более поздней версии
- [Пакет Microsoft.AI.Skills.SkillInterfacePreview NuGet](https://www.nuget.org/packages/Microsoft.AI.Skills.SkillInterfacePreview/)

## 1. Создайте и реализуйте классы основных навыков <a name="CreateMainClasses"></a>

Во-первых, нам нужно реализовать классы основных навыков (см. в разделе [основные понятия важные API](important-api-concepts.md) Дополнительные сведения):

- [ISkillDescriptor](#ISkillDescriptor)
- [ISkillBinding](#ISkillBinding)
- [ISkill](#ISkill)

Откройте в Visual Studio решение пользовательской службе визуального распознавания.

### 1. ISkillDescriptor <a name="ISkillDescriptor"></a>

Создайте и Реализуйте класс дескриптора навык, унаследованные от [ISkillDescriptor] [ ISkillDescriptor] , предоставляет сведения о навыках, предоставляет список устройств, поддерживаемых выполнения (ЦП, GPU и т. д.) и выступает в роли объект фабрики для квалификации.

1. Импорт [Microsoft.AI.Skills.SkillInterfacePreview] [ SkillInterfacePreview] пространства имен и являются производными от класса [ISkillDescriptor] [ ISkillDescriptor] интерфейс.

    ```csharp
    ...
    using Microsoft.AI.Skills.SkillInterfacePreview;
    ...

    public sealed class FaceSentimentAnalyzerDescriptor : ISkillDescriptor
    {
        ...
    }
    ```

2. Создайте две переменные-члены, которые будут содержать описания входов и выходов, необходимый навык. Затем в дескрипторе конструктор, заполнения их соответствующим образом с помощью функции ввода и вывода дескрипторы и присвоения значений все свойства, предоставляемые в базовом интерфейс, который описывают ваших навыков.

    ```csharp
    ...
    // Member variables to hold input and output descriptions
    private List<ISkillFeatureDescriptor> m_inputSkillDesc;
    private List<ISkillFeatureDescriptor> m_outputSkillDesc;

    // Properties required by the interface
    public string Description { get; private set; }
    public Guid Id { get; }
    public IReadOnlyList<ISkillFeatureDescriptor> InputFeatureDescriptors => m_inputSkillDesc;
    public IReadOnlyDictionary<string, string> Metadata => null;
    public string Name { get; private set; }
    public IReadOnlyList<ISkillFeatureDescriptor> OutputFeatureDescriptors => m_outputSkillDesc;
    public SkillVersion Version { get; }

    // Constructor
    public FaceSentimentAnalyzerDescriptor()
    {
        Name = "FaceSentimentAnalyzer";

        Description = "Finds a face in the image and infers its predominant sentiment from a set of 8 possible labels";

        // Unique ID {F8D275CE-C244-4E71-8A39-57335D291388}
        Id = new Guid(0xf8d275ce, 0xc244, 0x4e71, 0x8a, 0x39, 0x57, 0x33, 0x5d, 0x29, 0x13, 0x88);

        Version = SkillVersion.Create(
                    0,  // major version
                    1,  // minor version
                    "Contoso Developer", // Author name
                    "Contoso Publishing" // Publisher name
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

3. Реализуйте необходимые метод, который выполняет поиск доступных выполнения поддерживаемых устройств для выполнения навык в и возвращает их объекту-получателю. В нашем случае мы возвращаем ЦП и всех устройств DirectX D3D версии 12 или более поздней версии.

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

4. Реализуйте необходимые методы для создания экземпляра ваших навыков.

    - Один из них выбирает лучше всего устройств:

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

    - Другой использует устройство указанного выполнения:

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

### 2. **ISkillBinding** <a name="ISkillBinding"></a>

Создайте и реализуйте навык привязки класс, наследуемый от [ISkillBinding] [ ISkillBinding] интерфейса, который содержит входные и выходные переменные полученные и созданные рабочими навыками.

1. Импорт [Microsoft.AI.Skills.SkillInterfacePreview] [ SkillInterfacePreview] пространства имен и являются производными от класса [ISkillBinding] [ ISkillBinding] интерфейс и его тип коллекции.

    ```csharp
    ...
    using Microsoft.AI.Skills.SkillInterfacePreview;
    ...

    public sealed class FaceSentimentAnalyzerBinding : IReadOnlyDictionary<string, ISkillFeature>, ISkillBinding
    {
        ...

    ```

2. Сначала создайте две переменные-члены:

    - Один является вспомогательным классом [VisionSkillBindingHelper] [ VisionSkillBindingHelper] условии в базовый интерфейс для хранения входного изображения функция с именем «InputImage».

    ```csharp
    private VisionSkillBindingHelper m_bindingHelper = null;
    ```

    - Другое содержит LearningModelBinding, используемым для передачи в наших LearningModelSession, указанная в качестве аргумента наших конструктору позже в классе навыков.

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

    И реализуйте конструктор. Обратите внимание, что конструктор *внутренней*; в нашем парадигме ISkillBinding экземпляры создаются по квалификации и таким образом, не должны предоставлять конструктор автономный:

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

3. Создать перечисление, которое упрощает чтение выходных данных мнений типы по квалификации

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

4. Реализовать необязательные дополнительные методы, которые упрощают get и операций на привязку установки

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

### В. **ISkill** <a name="ISkill"></a>

Создайте и реализуйте навыков класс, наследуемый от [ISkill] [ ISkill] интерфейс, который выполняет логику навыков и создает выходные данные, исходя из набора входных данных. Он также служит объект фабрики для производных ISkillBinding.

1. Импорт [Microsoft.AI.Skills.SkillInterfacePreview] [ SkillInterfacePreview] пространства имен и являются производными от класса [ISkill] [ ISkill] интерфейс.

    ```csharp
    ...
    using Microsoft.AI.Skills.SkillInterfacePreview;
    ...

    public sealed class FaceSentimentAnalyzerSkill : ISkill
    {
        ...
    ```

2. Сначала создайте две переменные-члены:

    - Один для хранения FaceDetector искомый фрагмент на изображения.

    ```csharp
    private FaceDetector m_faceDetector = null;
    ```

    - Еще один для хранения LearningModelSession, используемых для оценки модель анализа тональности:

    ```csharp
    private LearningModelSession m_winmlSession = null;
    ```

    Объявите обязательные свойства:

    ```csharp
    public ISkillDescriptor SkillDescriptor { get; private set; }
    public ISkillExecutionDevice Device { get; private set; }
    ```

    И реализовать конструктор и статический фабричный метод. Обратите внимание, что конструктор *частного* и фабричный метод *внутренней*; в нашем парадигме ISkill экземпляры создаются дескриптором навыков и таким образом, не должны предоставлять конструктор автономный :

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

4. Для реализации теперь остается основная логика навыков с помощью EvaluateAsync() метод, объявленный в базовом интерфейсе. Сначала мы сделать некоторые проверочной меры и извлечения выходных признаков данные для заполнения.

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

    Затем этот навык определенного осуществляется в два шага:

    - **Шаг 1**. Запустите FaceDetector образе и получения ограничивающего лицо.

    ```csharp
            ...
            // Run face detection and retrieve face detection result
            var faceDetectionResult = await m_faceDetector.DetectFacesAsync(softwareBitmapInput);
            ...
    ```

    - **Шаг 2**: Если фрагмент был обнаружен, настройте ограничивающий прямоугольник, нормализовать координат для удобства использования и продолжить анализ тональности этой части образ с помощью Windows.AI.MachineLearning. По окончании вывод обновите оценку тональности каждого возможных, возвращен как результат.

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

## 2. Упаковка ваших навыков в NuGet  <a name="CreateNuspec"></a>

Все остается — скомпилировать ваших навыков и создание пакета NuGet из ваших навыков, таким образом, приложение может обрабатывать его.

([*Дополнительные сведения о пакетах NuGet здесь*](https://docs.microsoft.com/nuget/what-is-nuget))

Чтобы создать пакет NuGet, необходимо написать *файлу nuspec* файла, как показано ниже [исходного файла в репозитории Git см. в разделе](https://github.com/Microsoft/WindowsVisionSkillsPreview/blob/master/samples/SentimentAnalyzerCustomSkill/build/SentimentAnalyzer_CS.nuspec). Этот файл состоит из двух основных разделов:

- **Метаданные**: Эта часть содержит имя, описание, автора и владелец, лицензии и зависимости. Обратите внимание, что в нашем случае мы зависят от [Microsoft.AI.Skills.SkillInterfacePreview] [ SkillInterfacePreview] пакет NuGet. Этот пакет NuGet также содержит ссылки на лицензии и запускает запрос на его утверждение перед приемом данных.

- **файлы**: Эта часть указывает скомпилированные данные и ресурсы. Обратите внимание на то, что целевое расположение указывает uap10.0.17763 версии framework. Это гарантирует, что прием пакета приложений, предназначенных для более ранней версии, чем 10.0.17763 (Минимальная версия ОС требуется этот навык) будет получать сообщение об ошибке.

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

Затем необходимо скомпоновать вашей *файлу nuspec* с использованием nuget.exe ([загрузить в официальном центре](https://www.nuget.org/downloads)) для создания *.nupkg* файл пакета NuGet.
Откройте командную строку и перейдите к расположению nuget.exe, затем вызовите:

```cmd
> .\nuget.exe pack <path to your .nuspec>
```

Для проверки пакета локально, можно будет поместить это *.nupkg* файл в папке, которая будет служить NuGet, веб-канала в Visual Studio ([см. в разделе руководства, посвященные здесь](https://github.com/Microsoft/WindowsVisionSkillsPreview/blob/master/samples/SentimentAnalyzerCustomSkill/README.md#PrivateNuGetFeed)).

Ура вы создали первый квалификации концепции Windows! Вы можете отправить свои навыки упакованные [NuGet.org](https://www.nuget.org/)!

## 3. И ещё.. запутывание и deobfuscating файлов ресурсов для скрытия интеллектуальной собственности<a name="Obfuscation"></a>

Потребитель обезвреживания использование или доступ к ресурсам навыков (файлы модели, изображения, и т.д.), можно замаскировать файлы в качестве шага перед сборкой и deobfuscate файлов во время выполнения. [Пример, в нашем примере GitHub](https://github.com/Microsoft/WindowsVisionSkillsPreview/tree/master/samples/SentimentAnalyzerCustomSkill/cpp) содержит реализацию вспомогательные классы, которые используют [Windows.Security.Cryptography](https://docs.microsoft.com/uwp/api/Windows.Security.Cryptography) для [запутывания](https://github.com/Microsoft/WindowsVisionSkillsPreview/tree/master/samples/SentimentAnalyzerCustomSkill/cpp/Obfuscator) файлов во время компиляции и [deobfuscate](https://github.com/Microsoft/WindowsVisionSkillsPreview/tree/master/samples/SentimentAnalyzerCustomSkill/cpp/Deobfuscator) их во время выполнения. Обратите внимание, что эта часть отображается только в C++/WinRT версию сохранить свои навыки пример C# более простой версии.  

- Запутывания — это событие перед сборкой, можно настроить проект на выполнение постоянно или выполняются один раз и использовать выходные данные как ресурс напрямую. В этом примере мы используем выделенный скомпилированного средство (Obfuscator.exe). Необходимо убедиться, что сначала скомпилировать это средство прежде, чем ее можно вызвать как часть своего времени компиляции навыков событие перед сборкой. Обратите внимание, что так как выполняется на компьютере разработки во время компиляции, можно скомпилировать его один раз, используя любой целевой объект и поддерживаемые платформы (т. е. в этом случае *Debug/Win32*).

    В Visual Studio, можно задать это событие перед сборкой:

- C++проект: ***щелкнув правой кнопкой мыши проект навыков*** "->" uncollapse ***события сборки*** -> выберите ***событие перед построением*** "->" введите ***командной строки***
- C#проект: ***щелкнув правой кнопкой мыши проект навыков*** -> выберите ***события сборки*** "->" введите ***Командная строка события перед сборкой***

    Эта команда:
- Сначала скопирует его активов на локальном компьютере
- шифрует его *.crypt* (может иметь любое имя расширения) файла с помощью логикой, определенной в, требуется ключ GUID
- затем удаляет локальный файл

    ** **Обратите внимание на то, что мы рекомендуем изменить логику шифрования, предложенные в примере, чтобы сделать его уникальным для ваших навыков.** **

    ```cmd
    copy $(ProjectDir)..\..\Common\emotion_ferplus.onnx $(ProjectDir) &amp;&amp; ^$(ProjectDir)..\Obfuscator\Win32\Debug\Obfuscator.exe $(ProjectDir)emotion_ferplus.onnx $(ProjectDir) emotion_ferplus.crypt 678BD455-4190-45D3-B5DA-41543283C092 &amp;&amp; ^del $(ProjectDir)emotion_ferplus.onnx
    ```

- Deobfuscation выполняется через простой вспомогательный компонент среды выполнения Windows, полученных навыков. Логику расшифровки следует шифрования один определенный на предыдущем шаге.

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
