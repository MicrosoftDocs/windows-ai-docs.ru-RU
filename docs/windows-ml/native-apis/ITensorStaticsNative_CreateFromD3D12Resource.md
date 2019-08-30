---
title: Итенсорстатикснативе. CreateFromD3D12Resource, метод
description: Создает объект тензорные (Тенсорфлоат, TensorInt32Bit) из указанного пользователем ID3D12Resource.
ms.date: 4/2/2019
ms.topic: article
keywords: Windows 10, машинное обучение Windows, WinML, CreateFromD3D12Resource
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- ITensorStaticsNative.CreateFromD3D12Resource
api_location:
- windows.ai.machinelearning.native.h
ms.openlocfilehash: 251c45c0f444affc2c154de056e4916a5ba1ba93
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70156419"
---
# <a name="itensorstaticsnativecreatefromd3d12resource-method"></a>Итенсорстатикснативе. CreateFromD3D12Resource, метод

Создает объект тензорные ([тенсорфлоат](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.tensorfloat), [TensorInt32Bit](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.tensorint32bit)) из указанного пользователем [ID3D12Resource](https://docs.microsoft.com/windows/desktop/api/d3d12/nn-d3d12-id3d12resource).

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
| value | [ID3D12Resource](https://docs.microsoft.com/windows/desktop/api/d3d12/nn-d3d12-id3d12resource)* | **ID3D12Resource** , из которого создается тензорные. |
| сектор | **__int64**\* | Форма тензорные. |
| шапекаунт | **int** | Число измерений тензорные. |
| результат | [IUnknown](https://docs.microsoft.com/windows/desktop/api/unknwn/nn-unknwn-iunknown)** | Результирующий тензорные. |

## <a name="returns"></a>Возвращает

**Значение HRESULT** Результат операции.

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

* [Пользовательский пример Тенсоризатион](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/CustomTensorization)

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборка 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | Windows. AI. machinelearning. Native. h |

[!INCLUDE [help](../../includes/get-help.md)]
