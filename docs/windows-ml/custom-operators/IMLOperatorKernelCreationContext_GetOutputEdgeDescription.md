---
title: Имлоператоркернелкреатионконтекст. Жетаутпутеджедескриптион, метод
description: Возвращает описание указанного края вывода оператора.
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, машинное обучение Windows, WinML, пользовательские операторы, Жетаутпутеджедескриптион
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorKernelCreationContext.GetOutputEdgeDescription
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 9c937fe574e60fd8bfd0dff0baaef5d72d3c0106
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157512"
---
# <a name="imloperatorkernelcreationcontextgetoutputedgedescription-method"></a>Имлоператоркернелкреатионконтекст. Жетаутпутеджедескриптион, метод

Возвращает описание указанного края вывода оператора.

```cpp
void GetOutputEdgeDescription(
    uint32_t outputIndex,
    _Out_ MLOperatorEdgeDescription* edgeDescription)
```

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборка 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | Млоператораусор. h |

[!INCLUDE [help](../../includes/get-help.md)]
