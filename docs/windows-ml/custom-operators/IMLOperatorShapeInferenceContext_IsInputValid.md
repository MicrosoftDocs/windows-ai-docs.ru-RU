---
title: Имлоператоршапеинференцеконтекст. Исинпутвалид, метод
description: Возвращает значение true, если входные данные оператора являются допустимыми.
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, машинное обучение Windows, WinML, пользовательские операторы, Исинпутвалид
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorShapeInferenceContext.IsInputValid
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 4520b1d8a4621dc7d837cfa1e19c4fb170ebf6c3
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70156979"
---
# <a name="imloperatorshapeinferencecontextisinputvalid-method"></a>Имлоператоршапеинференцеконтекст. Исинпутвалид, метод

Возвращает значение true, если входные данные оператора являются допустимыми. Это всегда возвращает значение true, за исключением необязательных входов и недопустимых индексов.

```cpp
bool IsInputValid(
    uint32_t inputIndex)
```

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборка 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | Млоператораусор. h |

[!INCLUDE [help](../../includes/get-help.md)]
