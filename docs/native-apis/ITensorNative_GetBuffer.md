---
author: eliotcowley
title: Метод ITensorNative.GetBuffer
description: Получает тензорные буфер в виде массива байтов.
ms.author: elcowle
ms.date: 11/8/2018
ms.topic: article
keywords: Windows 10, windows машинного обучения, WinML, GetBuffer
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- ITensorNative.GetBuffer
api_location:
- windows.ai.machinelearning.native.h
ms.openlocfilehash: 803dedf5b00446169f66cdcba4a87b04f0c9961a
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474561"
---
# <a name="itensornativegetbuffer-method"></a>Метод ITensorNative.GetBuffer

Получает тензорные буфер в виде массива байтов.

```cpp
HRESULT GetBuffer(
    [out, size_is(, *capacity)] BYTE **value, 
    [out] UINT32 *capacity);
```

## <a name="parameters"></a>Параметры

| Имя | Тип | Описание |
|------|------|-------------|
| value | **БАЙТОВ**\*\* | Тензорные буфер. |
| емкость | **UINT32**\* | Емкость буфера. |

## <a name="returns"></a>Возвращает

**HRESULT** результат операции.

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

* [Пример пользовательского Tensorization](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/CustomTensorization)

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальная версия клиента** | Windows 10, сборки 17763 |
| **Минимальная версия сервера** | Windows Server 2019 с возможностями рабочего стола |
| **Header** | Windows.AI.machinelearning.Native.h |

[!INCLUDE [help](../includes/get-help.md)]
