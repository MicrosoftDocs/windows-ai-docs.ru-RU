---
author: eliotcowley
title: Метод IMLOperatorShapeInferenceContext.SetOutputTensorShape
description: Задает выводимый форму тензорные выходных данных.
ms.author: elcowle
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, windows машинного обучения, WinML, настраиваемые операторы, SetOutputTensorShape
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorShapeInferenceContext.SetOutputTensorShape
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 40013b7248050afaad6d8f59cebd7a0074b14a9a
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66181026"
---
# <a name="imloperatorshapeinferencecontextsetoutputtensorshape-method"></a>Метод IMLOperatorShapeInferenceContext.SetOutputTensorShape

Задает выводимый форму тензорные выходных данных. Возвращает ошибку, если выходные данные по указанному индексу не тензорные.

```cpp
void SetOutputTensorShape(
    uint32_t outputIndex, 
    uint32_t dimensionCount, 
    const uint32_t* dimensions)
```

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборки 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
