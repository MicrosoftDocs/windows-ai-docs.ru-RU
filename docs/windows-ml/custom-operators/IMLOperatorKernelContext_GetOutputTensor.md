---
author: eliotcowley
title: Метод IMLOperatorKernelContext.GetOutputTensor
description: Получает тензорные выходные данные оператора по указанному индексу.
ms.author: elcowle
ms.date: 4/1/2019
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
ms.openlocfilehash: 28b32a8061d0edfc7c466460d8080d800ff715ee
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66181206"
---
# <a name="imloperatorkernelcontextgetoutputtensor-method"></a>Метод IMLOperatorKernelContext.GetOutputTensor

## <a name="overloads"></a>Перегрузки

| | |
|-|-|
| [GetOutputTensor (uint32_t, IMLOperatorTensor **)](#GetOutputTensor1) | Получает тензорные выходные данные оператора по указанному индексу. |
| [GetOutputTensor (uint32_t, uint32_t, const uint32_t *, IMLOperatorTensor **)](#GetOutputTensor2) | Получает тензорные выходные данные оператора по указанному индексу, а при объявлении его форму. |

<a name="GetOutputTensor1"></a>
## <a name="getoutputtensoruint32t-imloperatortensor"></a>GetOutputTensor(uint32_t, IMLOperatorTensor**)

Получает тензорные выходные данные оператора по указанному индексу. Это задает тензорные **nullptr** необязательно варианты выходных данных, которые не существуют. Если оператор ядра был зарегистрирован без метод определения фигуры, а затем перегрузку **GetOutputTensor** что обуславливает тензорные фигуры необходимо вызвать вместо этого. Возвращает ошибку, если выходные данные по указанному индексу не тензорные.

```cpp
void GetOutputTensor(
    uint32_t outputIndex, 
    _COM_Outptr_result_maybenull_ IMLOperatorTensor** tensor)
```

<a name="GetOutputTensor2"></a>
## <a name="getoutputtensoruint32t-uint32t-const-uint32t-imloperatortensor"></a>GetOutputTensor(uint32_t, uint32_t, const uint32_t*, IMLOperatorTensor**)

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
| **Минимальный поддерживаемый клиент** | Windows 10, сборки 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
