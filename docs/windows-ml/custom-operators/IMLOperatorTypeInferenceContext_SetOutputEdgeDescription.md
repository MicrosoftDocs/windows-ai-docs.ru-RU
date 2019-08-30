---
title: Имлоператортипеинференцеконтекст. Сетаутпутеджедескриптион, метод
description: Задает выводимый тип выходного края.
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, машинное обучение Windows, WinML, пользовательские операторы, Сетаутпутеджедескриптион
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorTypeInferenceContext.SetOutputEdgeDescription
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: ca3248c16d449a0a21521e00883446f1fd70e47e
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157927"
---
# <a name="imloperatortypeinferencecontextsetoutputedgedescription-method"></a>Имлоператортипеинференцеконтекст. Сетаутпутеджедескриптион, метод

Задает выводимый тип выходного края.

```cpp
void SetOutputEdgeDescription(
    uint32_t outputIndex,
    const MLOperatorEdgeDescription* edgeDescription)
```

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборка 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | Млоператораусор. h |

[!INCLUDE [help](../../includes/get-help.md)]
