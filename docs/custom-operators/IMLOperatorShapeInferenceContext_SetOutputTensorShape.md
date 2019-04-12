---
author: eliotcowley
title: Метод IMLOperatorShapeInferenceContext.SetOutputTensorShape
description: Задает выводимый форму тензорные выходных данных.
ms.author: elcowle
ms.date: 11/8/2018
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
ms.openlocfilehash: 4e80f060dc544fd320a0aa2010c73731d108e3de
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474621"
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
| **Минимальная версия клиента** | Windows 10, сборки 17763 |
| **Минимальная версия сервера** | Windows Server 2019 с возможностями рабочего стола |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
