---
author: eliotcowley
title: Метод IMLOperatorKernelCreationContext.GetTensorShapeDescription
description: Получает описание фигуры ввода-вывода по краям оператор.
ms.author: elcowle
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, windows машинного обучения, WinML, настраиваемые операторы, GetTensorShapeDescription
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorKernelCreationContext.GetTensorShapeDescription
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 215dc45fd4ed2d7cb3a7ddd38af13a2e86bc3d5f
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66181726"
---
# <a name="imloperatorkernelcreationcontextgettensorshapedescription-method"></a>Метод IMLOperatorKernelCreationContext.GetTensorShapeDescription

Получает описание фигуры ввода-вывода по краям оператор.

```cpp
void GetTensorShapeDescription(
    _COM_Outptr_ IMLOperatorTensorShapeDescription** shapeDescription)
```

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборки 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
