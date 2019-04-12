---
author: eliotcowley
title: Метод ITensorStaticsNative.CreateFromD3D12Resource
description: Создает объект тензорные (TensorFloat, TensorInt32Bit) из ID3D12Resource, определяемое пользователем.
ms.author: elcowle
ms.date: 11/8/2018
ms.topic: article
keywords: Windows 10, windows машинного обучения, WinML, CreateFromD3D12Resource
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- ITensorStaticsNative.CreateFromD3D12Resource
api_location:
- windows.ai.machinelearning.native.h
ms.openlocfilehash: 9fdcbb444f872f8fc8292c41e9253325f1e73176
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474981"
---
# <a name="itensorstaticsnativecreatefromd3d12resource-method"></a>Метод ITensorStaticsNative.CreateFromD3D12Resource

Создает объект тензорные ([TensorFloat](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.tensorfloat), [TensorInt32Bit](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.tensorint32bit)) из указанного [ID3D12Resource](https://docs.microsoft.com/windows/desktop/api/d3d12/nn-d3d12-id3d12resource).

```cpp
HRESULT CreateFromD3D12Resource(
    ID3D12Resource *value, 
    [size_is(shapeCount)] __int64 *shape, 
    int shapeCount, 
    [out] IUnknown ** result);
```

## <a name="parameters"></a>Параметры

| Имя | Тип | Описание |
|------|------|-------------|
| value | [ID3D12Resource](https://docs.microsoft.com/windows/desktop/api/d3d12/nn-d3d12-id3d12resource)* | **ID3D12Resource** из которого требуется создать тензорные. |
| Фигуры | **__int64**\* | Форма тензорные. |
| shapeCount | **ssNoversion** | Число измерений тензорные. |
| результат | [IUnknown](https://docs.microsoft.com/windows/desktop/api/unknwn/nn-unknwn-iunknown)** | Итоговый тензорные. |

## <a name="returns"></a>Возвращает

**HRESULT** результат операции.

## <a name="examples"></a>Примеры

```cpp
TensorFloat SoftwareBitmapToDX12Tensor(SoftwareBitmap softwareBitmap)
{
    // ...
    
    // GPU tensorize
    com_ptr<ITensorStaticsNative> tensorfactory = get_activation_factory<TensorFloat, ITensorStaticsNative>();
    com_ptr<::IUnknown> spUnkTensor;
    TensorFloat input1imagetensor(nullptr);
    int64_t shapes[4] = { 1,3, softwareBitmap.PixelWidth(), softwareBitmap.PixelHeight() };
    CHECK_HRESULT(tensorfactory->CreateFromD3D12Resource(pGPUResource.get(), shapes, 4, spUnkTensor.put()));
    spUnkTensor.try_as(input1imagetensor);

    // ...
}
```

## <a name="see-also"></a>См. также

* [Пример пользовательского Tensorization](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/CustomTensorization)

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальная версия клиента** | Windows 10, сборки 17763 |
| **Минимальная версия сервера** | Windows Server 2019 с возможностями рабочего стола |
| **Header** | Windows.AI.machinelearning.Native.h |

[!INCLUDE [help](../includes/get-help.md)]
