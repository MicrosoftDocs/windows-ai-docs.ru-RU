---
author: eliotcowley
title: Создание сеанса
description: Узнайте, как создать сеанс, который можно использовать для привязки модели устройства, который можно запустить и оценка модели.
ms.author: elcowle
ms.date: 2/14/2019
ms.topic: article
keywords: Windows 10, windows искусственного интеллекта, машинного обучения windows, winml, windows машинное обучение
ms.localizationpriority: medium
ms.openlocfilehash: a06f08793e1178d49b6c3e7d98afdaa13ccd130b
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474171"
---
# <a name="create-a-session"></a>Создание сеанса

После загрузки [LearningModel](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodel), создании [LearningModelSession](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodelsession), который выполняет привязку модели к устройству, которое выполняется и результатом является модель.

## <a name="choose-a-device"></a>Выберите нужное устройство

Устройства можно выбрать при создании сеанса. Выберите устройства типа [LearningModelDeviceKind](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodeldevicekind):

* **Значение по умолчанию**
    * Позвольте системе решить, какое устройство используется. В настоящее время на устройстве по умолчанию является использование ЦП.
* **ЦП**
    * Использование ЦП, даже если доступны другие устройства.
* **DirectX**
    * Используйте DirectX аппаратного ускорения устройства, в частности первый адаптер, перечисленный с помощью [IDXGIFactory1::EnumAdapters1](https://docs.microsoft.com/windows/desktop/api/dxgi/nf-dxgi-idxgifactory1-enumadapters1).
* **DirectXHighPerformance**
    * Совпадение с кодом **DirectX**, но будет использовать [DXGI_GPU_PREFERENCE_HIGH_PERFORMANCE](https://docs.microsoft.com/windows/desktop/api/dxgi1_6/ne-dxgi1_6-dxgi_gpu_preference) при перечислении адаптеров.
* **DirectXMinPower**
    * Совпадение с кодом **DirectX**, но будет использовать [DXGI_GPU_PREFERENCE_MINIMUM_POWER](https://docs.microsoft.com/windows/desktop/api/dxgi1_6/ne-dxgi1_6-dxgi_gpu_preference) при перечислении адаптеров.

Если вы не укажете устройства, система использует **по умолчанию**. Мы рекомендуем использовать **по умолчанию** для получения принимает системы выбрать для вас в будущем.

Следующий видеоролик содержит более подробные сведения обо всех типах устройств.

<br/>

> [!VIDEO https://www.youtube.com/embed/NM5CYUMMp-w]

## <a name="example"></a>Пример

Приведенный ниже показано, как создать сеанс из модели и устройство:

```cs
private void CreateSession(LearningModel model, LearningModelDeviceKind kind) 
{
    // Create the evaluation session with the model and device
    LearningModelSession session = 
        new LearningModelSession(model, new LearningModelDevice(kind));
}
```

## <a name="see-also"></a>См. также

* Предыдущих: [Загрузка модели](load-a-model.md)
* Далее: [Привязка модели](bind-a-model.md)

[!INCLUDE [help](includes/get-help.md)]
