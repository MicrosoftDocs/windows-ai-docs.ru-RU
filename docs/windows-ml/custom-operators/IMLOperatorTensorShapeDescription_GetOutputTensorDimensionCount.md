---
author: eliotcowley
title: Метод IMLOperatorTensorShapeDescription.GetOutputTensorDimensionCount
description: Получает размерность вывода тензорные оператора.
ms.author: elcowle
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, windows машинного обучения, WinML, настраиваемые операторы, GetOutputTensorDimensionCount
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorTensorShapeDescription.GetOutputTensorDimensionCount
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 0f03d53fc9339930f9b42b5739230cba420b2e25
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66181586"
---
# <a name="imloperatortensorshapedescriptiongetoutputtensordimensioncount-method"></a>Метод IMLOperatorTensorShapeDescription.GetOutputTensorDimensionCount

Получает размерность вывода тензорные оператора. Возвращает ошибку, если выходные данные по указанному индексу не тензорные.

```cpp
GetOutputTensorDimensionCount(
    uint32_t outputIndex, 
    _Out_ uint32_t* dimensionCount)
```

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборки 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
