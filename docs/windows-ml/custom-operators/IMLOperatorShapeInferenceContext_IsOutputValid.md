---
title: Имлоператоршапеинференцеконтекст. Исаутпутвалид, метод
description: Возвращает значение true, если выходные данные оператора являются допустимыми.
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, машинное обучение Windows, WinML, пользовательские операторы, Исаутпутвалид
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorShapeInferenceContext.IsOutputValid
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 8dd8ef2987fc5400c66fa549f173e2f6fded6744
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157761"
---
# <a name="imloperatorshapeinferencecontextisoutputvalid-method"></a>Имлоператоршапеинференцеконтекст. Исаутпутвалид, метод

Возвращает значение true, если выходные данные оператора являются допустимыми. Это всегда возвращает значение true, за исключением необязательных выходов и недопустимых индексов.

```cpp
bool IsOutputValid(
    uint32_t outputIndex)
```

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборка 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | Млоператораусор. h |

[!INCLUDE [help](../../includes/get-help.md)]
