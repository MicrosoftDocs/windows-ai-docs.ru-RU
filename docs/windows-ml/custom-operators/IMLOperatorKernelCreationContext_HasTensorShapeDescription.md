---
author: eliotcowley
title: Метод IMLOperatorKernelCreationContext.HasTensorShapeDescription
description: Возвращает значение true, если описание фигуры входных и выходных подключен к краям оператор может запрашиваться с помощью **GetTensorShapeDescription**.
ms.author: elcowle
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, windows машинного обучения, WinML, настраиваемые операторы, HasTensorShapeDescription
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorKernelCreationContext.HasTensorShapeDescription
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: ac854a1e6701055b99b3c79bfc8558887b20f279
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66181696"
---
# <a name="imloperatorkernelcreationcontexthastensorshapedescription-method"></a>Метод IMLOperatorKernelCreationContext.HasTensorShapeDescription

Возвращает значение true, если описание фигуры входных и выходных подключен к краям оператор может запрашиваться с помощью [IMLOperatorKernelCreationContext::GetTensorShapeDescription](IMLOperatorKernelCreationContext_GetTensorShapeDescription.md). Это возвращает значение true, если оператор был зарегистрирован с помощью [MLOperatorKernelOptions::AllowDynamicInputShapes](MLOperatorKernelOptions.md) флаг.

```cpp
bool HasTensorShapeDescription()
```

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборки 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
