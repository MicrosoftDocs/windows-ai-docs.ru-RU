---
author: eliotcowley
title: Метод IMLOperatorKernelContext.GetOutputTensor
description: Получает тензорные выходные данные оператора по указанному индексу.
ms.author: elcowle
ms.date: 11/8/2018
ms.topic: article
keywords: Windows 10, windows машинного обучения, WinML, настраиваемые операторы, GetOutputTensor
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorKernelContext.GetOutputTensor
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 0c0f708acfad55a1d4d7d8fe33b81da9f7289e42
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474871"
---
# <a name="imloperatorkernelcontextgetoutputtensor-method"></a>Метод IMLOperatorKernelContext.GetOutputTensor

## <a name="overloads"></a>Перегрузки

| | |
|-|-|
| [GetOutputTensor (uint32_t, IMLOperatorTensor **)](#GetOutputTensor1) | Получает тензорные выходные данные оператора по указанному индексу. |
| [GetOutputTensor (uint32_t, uint32_t, const uint32_t *, IMLOperatorTensor **)](#GetOutputTensor2) | Получает тензорные выходные данные оператора по указанному индексу, а при объявлении его форму. |

<a name="GetOutputTensor1"></a>
## <a name="getoutputtensoruint32t-imloperatortensor"></a>GetOutputTensor (uint32_t, IMLOperatorTensor **)

Получает тензорные выходные данные оператора по указанному индексу. Это задает тензорные **nullptr** необязательно варианты выходных данных, которые не существуют. Если оператор ядра был зарегистрирован без метод определения фигуры, а затем перегрузку **GetOutputTensor** что обуславливает тензорные фигуры необходимо вызвать вместо этого. Возвращает ошибку, если выходные данные по указанному индексу не тензорные.

```cpp
void GetOutputTensor(
    uint32_t outputIndex, 
    _COM_Outptr_result_maybenull_ IMLOperatorTensor** tensor)
```

<a name="GetOutputTensor2"></a>
## <a name="getoutputtensoruint32t-uint32t-const-uint32t-imloperatortensor"></a>GetOutputTensor (uint32_t, uint32_t, const uint32_t *, IMLOperatorTensor **)

Получает тензорные выходные данные оператора по указанному индексу, а при объявлении его форму. Эта команда возвращает **nullptr** необязательно варианты выходных данных, которые не существуют. Если оператор ядра был зарегистрирован метод определения фигуры, а затем перегрузку **GetOutputTensor** которого не потребляет фигуры также может называться. Возвращает ошибку, если выходные данные по указанному индексу не тензорные.

```cpp
void GetOutputTensor(
    uint32_t outputIndex,
    uint32_t dimensionCount,
    _In_reads_(dimensionCount) const uint32_t* dimensionSizes,
    _COM_Outptr_result_maybenull_ IMLOperatorTensor** tensor)
```

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальная версия клиента** | Windows 10, сборки 17763 |
| **Минимальная версия сервера** | Windows Server 2019 с возможностями рабочего стола |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
