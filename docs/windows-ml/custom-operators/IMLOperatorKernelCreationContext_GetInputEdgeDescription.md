---
title: Имлоператоркернелкреатионконтекст. Исаутпутвалид, метод
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
ms.openlocfilehash: d6cba37f20e71fce7870ab38aec46d7af4d40a84
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157455"
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
