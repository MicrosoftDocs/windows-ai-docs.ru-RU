---
title: Создание приложения UWP для навыков создания концепции
description: Приучите этот учебник, чтобы интегрировать навык в приложение UWP.
ms.date: 4/25/2019
ms.topic: article
keywords: Windows 10, Windows AI, навыки работы с концепцией Windows, UWP
ms.localizationpriority: medium
ms.openlocfilehash: d6e5b42ab86b1317d90555b72895df747daf9206
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70156958"
---
# <a name="tutorial-create-a-windows-vision-skill-uwp-application"></a>Учебник. Создание приложения UWP для навыков создания концепции Windows

> [!NOTE]
> Некоторые сведения относятся к предварительной версии продукта, в которую перед коммерческим выпуском могут быть внесены существенные изменения. Майкрософт не дает никаких гарантий, явных или подразумеваемых, в отношении предоставленной здесь информации.

В предыдущем [учебном курсе](tutorial.md)мы узнали, как создать и упаковать навык работы с Windows. Теперь давайте Научитесь интегрировать это приложение в универсальная платформа Windows (UWP). Вы можете скачать полный пример, доступный на сайте [GitHub](https://github.com/microsoft/WindowsVisionSkillsPreview/tree/master/samples/SentimentAnalyzerCustomSkill/cs) , чтобы увидеть, как он выглядит после завершения.

Также имеющие отношение к этому руководству, можно найти здесь Дополнительные сведения о загрузке *[VideoFrames](https://docs.microsoft.com/uwp/api/Windows.Media.VideoFrame)* из следующих источников:
- [существующий *софтваребитмап* ](https://docs.microsoft.com/uwp/api/windows.media.videoframe.createwithsoftwarebitmap#Windows_Media_VideoFrame_CreateWithSoftwareBitmap_Windows_Graphics_Imaging_SoftwareBitmap_)
- [файл изображения](https://docs.microsoft.com/windows/uwp/audio-video-camera/imaging#create-a-softwarebitmap-from-an-image-file-with-bitmapdecoder)
- Камера через [фрамереадер](https://docs.microsoft.com/windows/uwp/audio-video-camera/process-media-frames-with-mediaframereader)
- Камера с помощью Microsoft. Toolkit: [Камерапревиев](https://docs.microsoft.com/windows/communitytoolkit/controls/camerapreview), [камерахелпер](https://docs.microsoft.com/windows/communitytoolkit/helpers/camerahelper)

---
## <a name="prerequisites"></a>Предварительные требования

- Завершение работы с предыдущим руководством по [созданию собственного навыка представления Windows](tutorial.md)
---

## <a name="api-flow"></a>Поток API
Мы вернемся к потоку API, описанному на странице [важные концепции API](important-api-concepts.md#APIFlow) , но теперь с конкретным набором классов C#в. Полный пример кода доступен на сайте [GitHub](https://github.com/microsoft/WindowsVisionSkillsPreview/blob/master/samples/SentimentAnalyzerCustomSkill/cs/Apps/FaceSentimentAnalysisApp_UWP/MainPage.xaml.cs).

Мы расскажем о строках кода, относящихся к API-интерфейсу концепции Windows:

+ Создание экземпляра производного класса [искиллдескриптор][ISkillDescriptor]

    ```csharp
    ...

    // member variable to hold the skill descriptor
    private FaceSentimentAnalyzerDescriptor m_skillDescriptor = null;

    ...

    // Instatiate skill descriptor to display details about the skill and populate UI
    m_skillDescriptor = new FaceSentimentAnalyzerDescriptor();

    ...
    ```

+ Запрос доступных устройств выполнения с помощью экземпляра [искиллдескриптор][ISKillDescriptor]
    ```csharp
    ...

    // member variable to hold the available execution devices
    private IReadOnlyList<ISkillExecutionDevice> m_availableExecutionDevices = null;

    ...

    m_availableExecutionDevices = await m_skillDescriptor.GetSupportedExecutionDevicesAsync();

    ...
    ```

+ Создание экземпляра навыка с помощью экземпляра [искиллдескриптор][ISKillDescriptor] и требуемого [искиллексекутиондевице][ISkillExecutionDevice]
    ```csharp
    ...

    // member variable to hold the skill
    private FaceSentimentAnalyzerSkill m_skill = null;

    ...

    // Initialize skill with the selected supported device
    m_skill = await m_skillDescriptor.CreateSkillAsync(m_availableExecutionDevices[UISkillExecutionDevices.SelectedIndex]) as FaceSentimentAnalyzerSkill;

    ...
    ```

+ Создание экземпляра объекта привязки навыков с помощью экземпляра [Kill][ISKill]
    ```csharp
    ...

    // member variable to hold the skill binding
    private FaceSentimentAnalyzerBinding m_binding = null;

    ...

   // Instantiate a binding object that will hold the skill's input and output resource
   m_binding = await m_skill.CreateSkillBindingAsync() as FaceSentimentAnalyzerBinding;

    ...
    ```

+ Получите примитив ввода (*видеофраме*) и привяжите его к объекту привязки, обратившись к соответствующему [искиллфеатуре][ISkillFeature] , индексируемому по имени. Обратите внимание, что этот навык объявляет удобный метод Set *сетинпутимаже*
    ```csharp
    ...

    // Retrieve a VideoFrame from an image file
    VideoFrame frame = await LoadVideoFrameFromFilePickedAsync();

    ...

    // Update input image feature
    await m_binding.SetInputImageAsync(frame);

    ...
    ```
    Этот удобный метод можно обойти и использовать тот же результат, что и при задании значения непосредственно следующим образом:

    ```csharp
    // Update input image feature
    await m_binding["InputImage"].SetFeatureValueAsync(frame);
    ```

+ Запуск навыков по объекту привязки
    ```csharp
    // Evaluate the binding
    await m_skill.EvaluateAsync(m_binding);
    ```

+ Извлеките выходные примитивы из объекта привязки. Обратите внимание, что этот навык объявляет удобное свойство метода получения с именем *исфацефаунд*.
    ```csharp
    // Retrieve results
    if (m_binding.IsFaceFound)
    {
        IReadOnlyList<float> scores = (m_binding["FaceSentimentScores"].FeatureValue as SkillFeatureTensorFloatValue).GetAsVectorView();
    }
    ```

    Этот удобный метод, как описано в предыдущем руководстве и ниже, имеет тот же результат, что и получение выходного компонента непосредственно из привязки, и проверка его значений не равна нулю.

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
