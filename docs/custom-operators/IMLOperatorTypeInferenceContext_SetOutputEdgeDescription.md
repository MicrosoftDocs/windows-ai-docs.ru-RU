---
author: eliotcowley
title: Метод IMLOperatorTypeInferenceContext.SetOutputEdgeDescription
description: Задает выведенный тип ребро выходных данных.
ms.author: elcowle
ms.date: 11/8/2018
ms.topic: article
keywords: Windows 10, windows машинного обучения, WinML, настраиваемые операторы, SetOutputEdgeDescription
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorTypeInferenceContext.SetOutputEdgeDescription
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 7f180051c6eef1b1b2194116594374fd0b807816
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474021"
---
# <a name="imloperatortypeinferencecontextsetoutputedgedescription-method"></a>Метод IMLOperatorTypeInferenceContext.SetOutputEdgeDescription

Задает выведенный тип ребро выходных данных.

```cpp
void SetOutputEdgeDescription(
    uint32_t outputIndex, 
    const MLOperatorEdgeDescription* edgeDescription)
```

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальная версия клиента** | Windows 10, сборки 17763 |
| **Минимальная версия сервера** | Windows Server 2019 с возможностями рабочего стола |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
