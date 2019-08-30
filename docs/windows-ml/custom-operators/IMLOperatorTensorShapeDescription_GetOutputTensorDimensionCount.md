---
title: Имлоператортенсоршапедескриптион. Жетаутпуттенсордименсионкаунт, метод
description: Возвращает число измерений тензорные выходных данных оператора.
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, машинное обучение Windows, WinML, пользовательские операторы, Жетаутпуттенсордименсионкаунт
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorTensorShapeDescription.GetOutputTensorDimensionCount
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: c1010e2f0abbb92b36399d5c1938673b4a002c53
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157815"
---
# <a name="imloperatortensorshapedescriptiongetoutputtensordimensioncount-method"></a>Имлоператортенсоршапедескриптион. Жетаутпуттенсордименсионкаунт, метод

Возвращает число измерений тензорные выходных данных оператора. Возвращает ошибку, если выходные данные по указанному индексу не являются тензорные.

```cpp
GetOutputTensorDimensionCount(
    uint32_t outputIndex,
    _Out_ uint32_t* dimensionCount)
```

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборка 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | Млоператораусор. h |

[!INCLUDE [help](../../includes/get-help.md)]
