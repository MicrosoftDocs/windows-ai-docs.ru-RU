---
author: eliotcowley
title: Метод IMLOperatorTensorShapeDescription.GetInputTensorDimensionCount
description: Получает размерность тензорные ввода оператора.
ms.author: elcowle
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, windows машинного обучения, WinML, настраиваемые операторы, GetInputTensorDimensionCount
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorTensorShapeDescription.GetInputTensorDimensionCount
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 0f2d26e85ef38a2d7be6cbdd460be02b415ff3cc
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66181766"
---
# <a name="imloperatortensorshapedescriptiongetinputtensordimensioncount-method"></a>Метод IMLOperatorTensorShapeDescription.GetInputTensorDimensionCount

Получает размерность тензорные ввода оператора. Возвращает ошибку, если входные данные по указанному индексу не тензорные.

```cpp
void GetInputTensorDimensionCount(
    uint32_t inputIndex, 
    _Out_ uint32_t* dimensionCount)
```

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборки 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
