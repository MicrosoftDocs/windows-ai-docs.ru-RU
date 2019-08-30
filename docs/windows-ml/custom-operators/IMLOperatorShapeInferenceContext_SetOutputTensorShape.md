---
title: Имлоператоршапеинференцеконтекст. Сетаутпуттенсоршапе, метод
description: Задает выводимую форму выходного тензорные.
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, машинное обучение Windows, WinML, пользовательские операторы, Сетаутпуттенсоршапе
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorShapeInferenceContext.SetOutputTensorShape
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: f4500e42f3ee6c8f47f555d8e7eb7d50c8a929ab
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157607"
---
# <a name="imloperatorshapeinferencecontextsetoutputtensorshape-method"></a>Имлоператоршапеинференцеконтекст. Сетаутпуттенсоршапе, метод

Задает выводимую форму выходного тензорные. Возвращает ошибку, если выходные данные по указанному индексу не являются тензорные.

```cpp
void SetOutputTensorShape(
    uint32_t outputIndex,
    uint32_t dimensionCount,
    const uint32_t* dimensions)
```

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборка 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | Млоператораусор. h |

[!INCLUDE [help](../../includes/get-help.md)]
