---
title: Создание приложения UWP с навыком компьютерного зрения
description: Узнайте из этого руководства, как интегрировать навык компьютерного зрения в приложение UWP.
ms.date: 4/25/2019
ms.topic: article
keywords: windows 10, искусственный интеллект windows, навыки компьютерного зрения, uwp
ms.localizationpriority: medium
ms.openlocfilehash: d6e5b42ab86b1317d90555b72895df747daf9206
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70156958"
---
# <a name="tutorial-create-a-windows-vision-skill-uwp-application"></a>Руководство: Создание приложения UWP с навыком компьютерного зрения Windows

> [!NOTE]
> Некоторые сведения относятся к предварительной версии продукта, в которую перед коммерческим выпуском могут быть внесены существенные изменения. Майкрософт не дает никаких гарантий, явных или подразумеваемых, в отношении предоставленной здесь информации.

Из предыдущего [руководства](tutorial.md) мы узнали, как создавать и упаковывать навык компьютерного зрения Windows. Теперь мы узнаем, как интегрировать этот навык в приложение универсальной платформы Windows (UWP). Вы можете скачать полный пример из репозитория [GitHub](https://github.com/microsoft/WindowsVisionSkillsPreview/tree/master/samples/SentimentAnalyzerCustomSkill/cs), если хотите изучить его окончательную версию.

Кроме того, при работе с этим руководством вам помогут дополнительные данные о загрузке *[VideoFrames](https://docs.microsoft.com/uwp/api/Windows.Media.VideoFrame)* из следующих источников:
- [существующий *SoftwareBitmap*](https://docs.microsoft.com/uwp/api/windows.media.videoframe.createwithsoftwarebitmap#Windows_Media_VideoFrame_CreateWithSoftwareBitmap_Windows_Graphics_Imaging_SoftwareBitmap_);
- [файл изображения](https://docs.microsoft.com/windows/uwp/audio-video-camera/imaging#create-a-softwarebitmap-from-an-image-file-with-bitmapdecoder);
- камера с поддержкой [FrameReader](https://docs.microsoft.com/windows/uwp/audio-video-camera/process-media-frames-with-mediaframereader);
- камера с поддержкой Microsoft.Toolkit: [CameraPreview](https://docs.microsoft.com/windows/communitytoolkit/controls/camerapreview), [CameraHelper](https://docs.microsoft.com/windows/communitytoolkit/helpers/camerahelper).

---
## <a name="prerequisites"></a>Предварительные условия

- Выполните инструкции из предыдущего руководства по [созданию собственного навыка компьютерного зрения Windows](tutorial.md).
---

## <a name="api-flow"></a>Поток API
Здесь мы снова применим поток API, описанный на странице [Важные понятия об API](important-api-concepts.md#APIFlow), но на этот раз для него есть конкретный набор классов C#. Полный пример кода размещен на веб-сайте [GitHub](https://github.com/microsoft/WindowsVisionSkillsPreview/blob/master/samples/SentimentAnalyzerCustomSkill/cs/Apps/FaceSentimentAnalysisApp_UWP/MainPage.xaml.cs).

Мы рассмотрим следующие строки кода, имеющие отношение к API Windows Vision Skill.

+ Создание экземпляра производного класса [ISkillDescriptor][ISkillDescriptor].

    ```csharp
    ...

    // member variable to hold the skill descriptor
    private FaceSentimentAnalyzerDescriptor m_skillDescriptor = null;

    ...

    // Instatiate skill descriptor to display details about the skill and populate UI
    m_skillDescriptor = new FaceSentimentAnalyzerDescriptor();

    ...
    ```

+ Запрос доступных устройств выполнения с помощью экземпляра [ISKillDescriptor][ISKillDescriptor].
    ```csharp
    ...

    // member variable to hold the available execution devices
    private IReadOnlyList<ISkillExecutionDevice> m_availableExecutionDevices = null;

    ...

    m_availableExecutionDevices = await m_skillDescriptor.GetSupportedExecutionDevicesAsync();

    ...
    ```

+ Создание экземпляра навыка с помощью экземпляра [ISKillDescriptor][ISKillDescriptor] и выбранного устройства [ISkillExecutionDevice][ISkillExecutionDevice].
    ```csharp
    ...

    // member variable to hold the skill
    private FaceSentimentAnalyzerSkill m_skill = null;

    ...

    // Initialize skill with the selected supported device
    m_skill = await m_skillDescriptor.CreateSkillAsync(m_availableExecutionDevices[UISkillExecutionDevices.SelectedIndex]) as FaceSentimentAnalyzerSkill;

    ...
    ```

+ Создание экземпляра объекта привязки навыков с помощью экземпляра [ISKill][ISKill].
    ```csharp
    ...

    // member variable to hold the skill binding
    private FaceSentimentAnalyzerBinding m_binding = null;

    ...

   // Instantiate a binding object that will hold the skill's input and output resource
   m_binding = await m_skill.CreateSkillBindingAsync() as FaceSentimentAnalyzerBinding;

    ...
    ```

+ Получите примитив входных данных (*VideoFrame*) и привяжите его к объекту привязки, используя соответствующий [ISkillFeature][ISkillFeature] с индексом по имени. Обратите внимание, что этот навык объявляет удобный метод присвоения *SetInputImage*.
    ```csharp
    ...

    // Retrieve a VideoFrame from an image file
    VideoFrame frame = await LoadVideoFrameFromFilePickedAsync();

    ...

    // Update input image feature
    await m_binding.SetInputImageAsync(frame);

    ...
    ```
    Этот удобный метод можно обойти, и его применение аналогично прямому заданию соответствующего значения:

    ```csharp
    // Update input image feature
    await m_binding["InputImage"].SetFeatureValueAsync(frame);
    ```

+ Выполнение навыка для объекта привязки
    ```csharp
    // Evaluate the binding
    await m_skill.EvaluateAsync(m_binding);
    ```

+ Извлеките выходные примитивы из объекта привязки. Обратите внимание, что этот навык объявляет удобное свойство получения с именем *IsFaceFound*.
    ```csharp
    // Retrieve results
    if (m_binding.IsFaceFound)
    {
        IReadOnlyList<float> scores = (m_binding["FaceSentimentScores"].FeatureValue as SkillFeatureTensorFloatValue).GetAsVectorView();
    }
    ```

    Этот удобный метод, как описано в предыдущем руководстве и ниже, аналогичен прямому получению выходных признаков из привязки с проверкой на отсутствие нулевого значения.

    ```csharp
    public bool FaceSentimentAnalyzerBinding.IsFaceFound
    {
        get
        {
            ISkillFeature feature = null;
            if (m_bindingHelper.TryGetValue("FaceRectangle", out feature))
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
    ```



[!INCLUDE [help](../includes/get-help-vision.md)]

[SkillInterfacePreview]: https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview

[ISkillDescriptor]: https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskilldescriptor

[ISkill]: https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskill

[ISkillBinding]: https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillbinding

[ISkillExecutionDevice]: https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillexecutiondevice

[ISkillFeature]: https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillfeature

[ISkillFeatureValue]: https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillfeaturevalue
