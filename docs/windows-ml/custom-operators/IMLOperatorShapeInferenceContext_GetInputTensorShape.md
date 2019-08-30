---
title: Имлоператоршапеинференцеконтекст. Жетинпуттенсоршапе, метод
description: Возвращает размеры измерений входного тензорные оператора.
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, машинное обучение Windows, WinML, пользовательские операторы, Жетинпуттенсоршапе
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorShapeInferenceContext.GetInputTensorShape
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: e8ca3e5c74d0471948d0a3ad7b2fe7f7715c373d
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157633"
---
# <a name="imloperatorshapeinferencecontextgetinputtensorshape-method"></a>Имлоператоршапеинференцеконтекст. Жетинпуттенсоршапе, метод

Возвращает размеры измерений входного тензорные оператора. Возвращает ошибку, если входные данные по указанному индексу не являются тензорные.

```cpp
void GetInputTensorShape(
    uint32_t inputIndex,
    uint32_t dimensionCount,
    _Out_writes_(dimensionCount) uint32_t* dimensions)
```

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборка 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | Млоператораусор. h |

[!INCLUDE [help](../../includes/get-help.md)]
