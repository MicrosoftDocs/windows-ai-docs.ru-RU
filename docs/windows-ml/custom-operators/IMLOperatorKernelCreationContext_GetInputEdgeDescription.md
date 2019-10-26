---
title: Имлоператоркернелкреатионконтекст. Жетинпутеджедескриптион, метод
description: Возвращает описание указанной входной границы оператора.
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, машинное обучение Windows, WinML, пользовательские операторы, Жетинпутеджедескриптион
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorKernelCreationContext.IsOutputValid
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 2871baadd40bbc028f2449892f86a1d3e4fdd86a
ms.sourcegitcommit: 7dbb3e690a8a7608d6d74cdaeabe717f661437ba
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/24/2019
ms.locfileid: "72892860"
---
# <a name="imloperatorkernelcreationcontextgetinputedgedescription-method"></a>Имлоператоркернелкреатионконтекст. Жетинпутеджедескриптион, метод

Возвращает описание указанной входной границы оператора.

```cpp
void GetInputEdgeDescription(
    uint32_t inputIndex,
    _Out_ MLOperatorEdgeDescription* edgeDescription)
```

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборка 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | Млоператораусор. h |

[!INCLUDE [help](../../includes/get-help.md)]
