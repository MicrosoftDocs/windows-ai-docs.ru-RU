---
author: eliotcowley
title: Метод IMLOperatorTensorShapeDescription.HasOutputShapeDescription
description: Возвращает значение true, если выходные данные фигуры может запрашиваться с помощью **GetOutputTensorDimensionCount** и **GetOutputTensorShape**.
ms.author: elcowle
ms.date: 11/8/2018
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
ms.openlocfilehash: 963f5dbb6358ff0f04b653be8dfbfab691c591c7
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474391"
---
# <a name="imloperatortensorshapedescriptionhasoutputshapedescription-method"></a>Метод IMLOperatorTensorShapeDescription.HasOutputShapeDescription

Возвращает значение true, если выходные данные фигуры может запрашиваться с помощью [IMLOperatorTensorShapeDescription::GetOutputTensorDimensionCount](IMLOperatorTensorShapeDescription_GetOutputTensorDimensionCount.md) и [IMLOperatorTensorShapeDescription::GetOutputTensorShape](IMLOperatorTensorShapeDescription_GetOutputTensorShape.md). Это значение равно true, если ядро был зарегистрирован inferrer фигуры.

```cpp
bool HasOutputShapeDescription()
```

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальная версия клиента** | Windows 10, сборки 17763 |
| **Минимальная версия сервера** | Windows Server 2019 с возможностями рабочего стола |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
