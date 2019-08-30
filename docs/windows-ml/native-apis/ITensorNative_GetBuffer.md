---
title: Итенсорнативе. @ buffer, метод
description: Возвращает буфер тензорные в виде массива байтов.
ms.date: 4/2/2019
ms.topic: article
keywords: Windows 10, машинное обучение Windows, WinML, буфер
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- ITensorNative.GetBuffer
api_location:
- windows.ai.machinelearning.native.h
ms.openlocfilehash: f20f49ad4f16905ab53bccc3d3316d41f615b041
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70156496"
---
# <a name="itensornativegetbuffer-method"></a>Итенсорнативе. @ buffer, метод

Возвращает буфер тензорные в виде массива байтов.

```cpp
HRESULT GetBuffer(
    [out, size_is(, *capacity)] BYTE **value,
    [out] UINT32 *capacity);
```

## <a name="parameters"></a>Параметры

| Имя | Тип | Описание |
|------|------|-------------|
| value | **ДВУХБАЙТОВЫХ**\*\* | Буфер тензорные. |
| ресурсов | **ЗНАЧЕНИЕМ**\* | Емкость буфера. |

## <a name="returns"></a>Возвращает

**Значение HRESULT** Результат операции.

## <a name="examples"></a>Примеры

```cpp
TensorFloat SoftwareBitmapToSoftwareTensor(SoftwareBitmap softwareBitmap)
{
    // 1. Get access to the buffer of softwareBitmap
    BYTE* pData = nullptr;
    UINT32 size = 0;
    BitmapBuffer spBitmapBuffer(softwareBitmap.LockBuffer(BitmapBufferAccessMode::Read));
    winrt::Windows::Foundation::IMemoryBufferReference reference = spBitmapBuffer.CreateReference();
    auto spByteAccess = reference.as<::Windows::Foundation::IMemoryBufferByteAccess>();
    CHECK_HRESULT(spByteAccess->GetBuffer(&pData, &size));

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
