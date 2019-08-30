---
title: Имлоператортипеинференцеконтекст. Исаутпутвалид, метод
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
- IMLOperatorTypeInferenceContext.IsOutputValid
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: c112e4f1ad3e09ae4a02f1cc7a5b38fa90413911
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70156068"
---
# <a name="imloperatortypeinferencecontextisoutputvalid-method"></a>Имлоператортипеинференцеконтекст. Исаутпутвалид, метод

Возвращает значение true, если выходные данные оператора являются допустимыми. Это всегда возвращает значение true, за исключением необязательных выходов.

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
