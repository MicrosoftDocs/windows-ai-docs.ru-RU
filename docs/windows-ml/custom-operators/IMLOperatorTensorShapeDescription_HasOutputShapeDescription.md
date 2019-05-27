---
author: eliotcowley
title: Метод IMLOperatorTensorShapeDescription.HasOutputShapeDescription
description: Возвращает значение true, если выходные данные фигуры может запрашиваться с помощью **GetOutputTensorDimensionCount** и **GetOutputTensorShape**.
ms.author: elcowle
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, windows машинного обучения, WinML, настраиваемые операторы, HasOutputShapeDescription
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorTensorShapeDescription.HasOutputShapeDescription
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 927fc48cd6554d1d35292490892edb4534f90c82
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66181856"
---
# <a name="imloperatortensorshapedescriptionhasoutputshapedescription-method"></a>Метод IMLOperatorTensorShapeDescription.HasOutputShapeDescription

Возвращает значение true, если выходные данные фигуры может запрашиваться с помощью [IMLOperatorTensorShapeDescription::GetOutputTensorDimensionCount](IMLOperatorTensorShapeDescription_GetOutputTensorDimensionCount.md) и [IMLOperatorTensorShapeDescription::GetOutputTensorShape](IMLOperatorTensorShapeDescription_GetOutputTensorShape.md). Это значение равно true, если ядро был зарегистрирован inferrer фигуры.

```cpp
bool HasOutputShapeDescription()
```

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборки 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
