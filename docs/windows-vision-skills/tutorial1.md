---
author: eliotcowley
title: Создание компьютерного зрения навык приложения универсальной платформы Windows
description: Интеграция навык концепции в приложение универсальной платформы Windows с помощью этого руководства.
ms.author: elcowle
ms.date: 4/25/2019
ms.topic: article
keywords: Windows 10, искусственный интеллект windows, windows визуального распознавания навыки, универсальной платформы Windows
ms.localizationpriority: medium
ms.openlocfilehash: 75aa0082002dcc75277811f4d1d747d5e7ad64bb
ms.sourcegitcommit: 4ad0fea02000c8f6dbb9a919fb6ce1f435d0e8d6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/12/2019
ms.locfileid: "67334155"
---
# <a name="tutorial-create-a-windows-vision-skill-uwp-application"></a>Учебник. Создание приложения UWP навыков концепции Windows

> [!NOTE]
> Некоторые сведения относятся к предварительной версии продукта, в которую перед коммерческим выпуском могут быть внесены существенные изменения. Майкрософт не дает никаких гарантий, явных или подразумеваемых, в отношении предоставленной здесь информации.

В предыдущем [руководстве](tutorial.md), мы узнали, как создание и упаковка навык концепции Windows. Теперь давайте узнаем, как интегрировать, в приложении универсальной платформы Windows (UWP). Можно скачать полный пример на [GitHub](https://github.com/microsoft/WindowsVisionSkillsPreview/tree/master/samples/SentimentAnalyzerCustomSkill/cs) чтобы увидеть, что получится после завершения.

Также имеющие отношение к этому руководству, можно найти здесь Дополнительные сведения о загрузке *[VideoFrames](https://docs.microsoft.com/uwp/api/Windows.Media.VideoFrame)* из следующих источников:
- [существующие *SoftwareBitmap*](https://docs.microsoft.com/uwp/api/windows.media.videoframe.createwithsoftwarebitmap#Windows_Media_VideoFrame_CreateWithSoftwareBitmap_Windows_Graphics_Imaging_SoftwareBitmap_)
- [файл изображения](https://docs.microsoft.com/windows/uwp/audio-video-camera/imaging#create-a-softwarebitmap-from-an-image-file-with-bitmapdecoder)
- камеры с помощью [FrameReader](https://docs.microsoft.com/windows/uwp/audio-video-camera/process-media-frames-with-mediaframereader)
- камера через Microsoft.Toolkit: [CameraPreview](https://docs.microsoft.com/windows/communitytoolkit/controls/camerapreview), [CameraHelper](https://docs.microsoft.com/windows/communitytoolkit/helpers/camerahelper)

---
## <a name="prerequisites"></a>предварительные требования

- Завершение работы с предыдущим учебником на [Создание собственных навыков концепции Windows](tutorial.md)
---

## <a name="api-flow"></a>API потока
Мы вернемся к потоку API, описанные в [основные понятия важные API](important-api-concepts.md#APIFlow) странице но сейчас с помощью конкретного набора классов в C#. Полный пример кода доступен на [GitHub](https://github.com/microsoft/WindowsVisionSkillsPreview/blob/master/samples/SentimentAnalyzerCustomSkill/cs/Apps/FaceSentimentAnalysisApp_UWP/MainPage.xaml.cs). 

Мы обсудим в строках кода, относящиеся к API Windows концепции навыков: 

+ Создать экземпляр [ISkillDescriptor][ISkillDescriptor] производных

    ```csharp
    ...
    
    // member variable to hold the skill descriptor
    private FaceSentimentAnalyzerDescriptor m_skillDescriptor = null;
    
    ...
    
    // Instatiate skill descriptor to display details about the skill and populate UI
    m_skillDescriptor = new FaceSentimentAnalyzerDescriptor();

    ...
    ```

+ Запрос доступных выполнения устройств с помощью [ISKillDescriptor][ISKillDescriptor] экземпляра
    ```csharp
    ...
    
    // member variable to hold the available execution devices
    private IReadOnlyList<ISkillExecutionDevice> m_availableExecutionDevices = null;
    
    ...
    
    m_availableExecutionDevices = await m_skillDescriptor.GetSupportedExecutionDevicesAsync();

    ...
    ```

+ Создать экземпляр навыков с помощью [ISKillDescriptor][ISKillDescriptor] экземпляра и требуемыми [ISkillExecutionDevice][ISkillExecutionDevice]
    ```csharp
    ...
    
    // member variable to hold the skill
    private FaceSentimentAnalyzerSkill m_skill = null;
    
    ...
    
    // Initialize skill with the selected supported device
    m_skill = await m_skillDescriptor.CreateSkillAsync(m_availableExecutionDevices[UISkillExecutionDevices.SelectedIndex]) as FaceSentimentAnalyzerSkill;

    ...
    ```

+ Создать экземпляр навык привязки с использованием объекта [ISKill][ISKill] экземпляра
    ```csharp
    ...
    
    // member variable to hold the skill binding
    private FaceSentimentAnalyzerBinding m_binding = null;
    
    ...
    
   // Instantiate a binding object that will hold the skill's input and output resource
   m_binding = await m_skill.CreateSkillBindingAsync() as FaceSentimentAnalyzerBinding;

    ...
    ```

+ Получить ваши примитивов ввода (*VideoFrame*) и привязать к объект привязки, обратившись к соответствующему [ISkillFeature][ISkillFeature] индексированную при помощи его имя. Обратите внимание, что этот навык объявляет метод set удобства *SetInputImage*
    ```csharp
    ...

    // Retrieve a VideoFrame from an image file
    VideoFrame frame = await LoadVideoFrameFromFilePickedAsync();

    ...

    // Update input image feature
    await m_binding.SetInputImageAsync(frame);

    ...
    ```
    Этот метод может быть пропущены и действует так же, как и поэтому Настройка непосредственно like значение:

    ```csharp
    // Update input image feature
    await m_binding["InputImage"].SetFeatureValueAsync(frame);
    ```

+ Работа вашей квалификации через объект привязки
    ```csharp
    // Evaluate the binding
    await m_skill.EvaluateAsync(m_binding);
    ```

+ Получить свои примитивы выходные данные из объекта привязки. Обратите внимание, что этот навык объявляется свойство getter удобства *IsFaceFound*.
    ```csharp
    // Retrieve results
    if (m_binding.IsFaceFound)
    {
        IReadOnlyList<float> scores = (m_binding["FaceSentimentScores"].FeatureValue as SkillFeatureTensorFloatValue).GetAsVectorView();
    }
    ```

    Этот метод, как описано в предыдущем учебном курсе и Далее, имеет тот же эффект, как получить возможность выходных данных непосредственно из привязки и проверки его значения не нули.

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
