---
author: eliotcowley
title: Метод IMLOperatorTensorShapeDescription.GetOutputTensorShape
description: Получает размеры измерениях тензорные выходных данных оператора.
ms.author: elcowle
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, windows машинного обучения, WinML, настраиваемые операторы, GetOutputTensorShape
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorTensorShapeDescription.GetOutputTensorShape
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 56056d0eea93405d036d43ba4f8a8108ad67f0ba
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66181516"
---
# <a name="imloperatortensorshapedescriptiongetoutputtensorshape-method"></a>Метод IMLOperatorTensorShapeDescription.GetOutputTensorShape

Получает размеры измерениях тензорные выходных данных оператора. Возвращает ошибку, если выходные данные по указанному индексу не тензорные.

```cpp
GetOutputTensorShape(
    uint32_t outputIndex, 
    uint32_t dimensionCount, 
    _Out_writes_(dimensionCount) uint32_t* dimensions)
```

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборки 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
