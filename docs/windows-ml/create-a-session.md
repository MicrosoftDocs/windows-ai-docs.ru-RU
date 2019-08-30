---
title: Создание сеанса
description: Узнайте, как создать сеанс, который можно использовать для привязки модели к устройству, которое затем может запустить и оценить модель.
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10, windows ai, windows ml, winml, windows machine learning
ms.localizationpriority: medium
ms.openlocfilehash: feb1dd5e2837039ea573361ea338cbd8c387ebab
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70156054"
---
# <a name="create-a-session"></a>Создание сеанса

После загрузки [леарнингмодел](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodel)создается [леарнингмоделсессион](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodelsession), который привязывает модель к устройству, которое выполняет и оценивает модель.

## <a name="choose-a-device"></a>Выбор устройства

Вы можете выбрать устройство при создании сеанса. Вы выбираете устройство типа [леарнингмоделдевицекинд](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodeldevicekind):

* **Default**
    * Позвольте системе решить, какое устройство следует использовать. В настоящее время устройство по умолчанию — это ЦП.
* **CPU**
    * Используйте ЦП, даже если доступны другие устройства.
* **DirectX**
    * Используйте устройство аппаратного ускорения DirectX, в частности первый адаптер, перечисленный с помощью [IDXGIFactory1:: EnumAdapters1](https://docs.microsoft.com/windows/desktop/api/dxgi/nf-dxgi-idxgifactory1-enumadapters1).
* **директксхигхперформанце**
    * То же, что и **DirectX**, но при перечислении адаптеров будет использоваться [DXGI_GPU_PREFERENCE_HIGH_PERFORMANCE](https://docs.microsoft.com/windows/desktop/api/dxgi1_6/ne-dxgi1_6-dxgi_gpu_preference) .
* **директксминповер**
    * То же, что и **DirectX**, но при перечислении адаптеров будет использоваться [DXGI_GPU_PREFERENCE_MINIMUM_POWER](https://docs.microsoft.com/windows/desktop/api/dxgi1_6/ne-dxgi1_6-dxgi_gpu_preference) .

Если устройство не указано, система использует **значение по умолчанию**. Мы рекомендуем использовать **значение по умолчанию** , чтобы обеспечить гибкость, позволяющую системе выбирать в будущем.

В следующем видео приведены более подробные сведения о каждом из типов устройств.

<br/>

> [!VIDEO https://www.youtube.com/embed/NM5CYUMMp-w]

## <a name="example"></a>Пример

В следующем примере показано, как создать сеанс из модели и устройства.

```cs
private void CreateSession(LearningModel model, LearningModelDeviceKind kind)
{
    // Create the evaluation session with the model and device
    LearningModelSession session =
        new LearningModelSession(model, new LearningModelDevice(kind));
}
```

## <a name="see-also"></a>См. также

* Прошлом [Загрузка модели](load-a-model.md)
* Далее: [Привязка модели](bind-a-model.md)

[!INCLUDE [help](../includes/get-help.md)]
