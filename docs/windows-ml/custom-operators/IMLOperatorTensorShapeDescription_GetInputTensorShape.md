---
author: eliotcowley
title: Метод IMLOperatorTensorShapeDescription.GetInputTensorShape
description: Возвращает размеры измерений из входного тензорные оператора.
ms.author: elcowle
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, windows машинного обучения, WinML, настраиваемые операторы, GetInputTensorShape
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorTensorShapeDescription.GetInputTensorShape
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 7064fd5fc81e3718a6b091ca73cc5aa9d0308daf
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66181616"
---
# <a name="imloperatortensorshapedescriptiongetinputtensorshape-method"></a>Метод IMLOperatorTensorShapeDescription.GetInputTensorShape

Возвращает размеры измерений из входного тензорные оператора. Возвращает ошибку, если входные данные по указанному индексу не тензорные.

```cpp
void GetInputTensorShape(
    uint32_t inputIndex, 
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
