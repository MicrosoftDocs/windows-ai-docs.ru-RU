---
title: Создание сеанса
description: Сведения о том, как создать сеанс для привязки модели к устройству, чтобы на нем запускать и оценивать модель.
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10, windows ai, windows ml, winml, windows machine learning
ms.localizationpriority: medium
ms.openlocfilehash: feb1dd5e2837039ea573361ea338cbd8c387ebab
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70156054"
---
# <a name="create-a-session"></a>Создание сеанса

После загрузки [LearningModel](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodel) создайте объект [LearningModelSession](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodelsession), который привязывает модель к устройству для ее выполнения и оценки.

## <a name="choose-a-device"></a>Выбор устройства

Устройство можно выбрать при создании сеанса. Это должно быть одно из следующих устройств с типом [LearningModelDeviceKind](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodeldevicekind):

* **По умолчанию**
    * Система самостоятельно решит, какое устройство следует использовать. Сейчас в качестве устройства по умолчанию используется ЦП.
* **ЦП**
    * Будет использоваться ЦП, даже если доступны другие устройства.
* **DirectX**
    * Будет использоваться устройство аппаратного ускорения DirectX, а точнее первый адаптер, полученный вызовом [IDXGIFactory1:: EnumAdapters1](https://docs.microsoft.com/windows/desktop/api/dxgi/nf-dxgi-idxgifactory1-enumadapters1).
* **DirectXHighPerformance**
    * То же, что и **DirectX**, но для получения списка адаптеров используется [DXGI_GPU_PREFERENCE_HIGH_PERFORMANCE](https://docs.microsoft.com/windows/desktop/api/dxgi1_6/ne-dxgi1_6-dxgi_gpu_preference).
* **DirectXMinPower**
    * То же, что и **DirectX**, но для получения списка адаптеров используется [DXGI_GPU_PREFERENCE_MINIMUM_POWER](https://docs.microsoft.com/windows/desktop/api/dxgi1_6/ne-dxgi1_6-dxgi_gpu_preference).

Если устройство не указано, система использует вариант **По умолчанию**. Мы рекомендуем всегда выбирать вариант **По умолчанию**, чтобы сохранять гибкость в выборе устройств системой.

В следующем видео представлены более подробные сведения о каждом из типов устройств.

<br/>

> [!VIDEO https://www.youtube.com/embed/NM5CYUMMp-w]

## <a name="example"></a>Пример

В следующем примере показано, как создать сеанс для модели и устройства.

```cs
private void CreateSession(LearningModel model, LearningModelDeviceKind kind)
{
    // Create the evaluation session with the model and device
    LearningModelSession session =
        new LearningModelSession(model, new LearningModelDevice(kind));
}
```

## <a name="see-also"></a>См. также статью

* Предыдущая статья: [Загрузка модели](load-a-model.md)
* Далее: [Привязка модели](bind-a-model.md)

[!INCLUDE [help](../includes/get-help.md)]
