---
title: Создание сеанса
description: Сведения о том, как создать сеанс для привязки модели к устройству, чтобы на нем запускать и оценивать модель.
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10, windows ai, windows ml, winml, windows machine learning
ms.localizationpriority: medium
ms.openlocfilehash: c4b2e330efce5b0d5b7a2f5729adc94a97fb604e
ms.sourcegitcommit: 2139506ff12b7205283288c4bbac866ddfa812f3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/24/2020
ms.locfileid: "80231596"
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

## <a name="advanced-device-creation"></a>Расширенное создание устройств

Средства ИИ Windows позволяют использовать устройство, созданное вызывающим объектом.  Это можно сделать разными способами:

* [CreateFromDirect3D11Device.](https://docs.microsoft.com/en-us/uwp/api/windows.ai.machinelearning.learningmodeldevice.createfromdirect3d11device)  Этот вариант подходит, если у вас уже есть IDirect3DDevice.  Средства ИИ Windows будут использовать тот же адаптер для создания устройства d3d12 для рабочих нагрузок Машинного обучения.  Это полезно, если у вас есть камера, использующая устройство d3d11 для VideoFrame, и вы хотите использовать это устройство для LearningModelSession.  Во многих случаях это позволяет избежать копирования в память.  Примечание. Преобразование в тензор VideoFrame — это единственная рабочая нагрузка d3d11, которая есть в средства ИИ Windows.  Если вы не используете эту функцию, совместное использование или создание устройства d3d11 не связано с каким-либо преимуществами.
* [CreateFromD3D12CommandQueue (собственное решение).](https://docs.microsoft.com/en-us/windows/ai/windows-ml/native-apis/ilearningmodeldevicefactorynative_createfromd3d12commandqueue)  Используйте этот вариант при наличии устройства d3d12, которое вы хотите повторно использовать.  Средства ИИ Windows будут использовать эту очередь команд для своих рабочих нагрузок Машинного обучения.   Также будет создано устройство d3d11 с помощью D3D11On12CreateDevice.  Это делается только при необходимости и будет использоваться для всех рабочих нагрузок d3d11, таких как преобразование в тензор VideoFrame.  Доступ к этому новому устройству можно получить с помощью свойства LearningModelDevice.Direct3D11Device.

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
