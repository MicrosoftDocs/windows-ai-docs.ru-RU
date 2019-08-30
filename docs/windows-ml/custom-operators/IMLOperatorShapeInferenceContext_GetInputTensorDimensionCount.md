---
title: Имлоператоршапеинференцеконтекст. Жетинпуттенсордименсионкаунт, метод
description: Возвращает число измерений тензорные выходных данных оператора.
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, машинное обучение Windows, WinML, пользовательские операторы, Жетинпуттенсордименсионкаунт
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorShapeInferenceContext.GetInputTensorDimensionCount
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 8d191d379045918422c62c80eeac2d8573931860
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157742"
---
# <a name="imloperatorshapeinferencecontextgetinputtensordimensioncount-method"></a>Имлоператоршапеинференцеконтекст. Жетинпуттенсордименсионкаунт, метод

Возвращает число измерений тензорные выходных данных оператора.

```cpp
void GetInputTensorDimensionCount(
    uint32_t inputIndex,
    _Out_ uint32_t* dimensionCount)
```

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборка 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | Млоператораусор. h |

[!INCLUDE [help](../../includes/get-help.md)]
