---
title: Имлоператортенсоршапедескриптион. Жетинпуттенсордименсионкаунт, метод
description: Возвращает количество измерений тензорные входных данных оператора.
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, машинное обучение Windows, WinML, пользовательские операторы, Жетинпуттенсордименсионкаунт
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorTensorShapeDescription.GetInputTensorDimensionCount
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 0a7b95025b95b0779d2fae2aa751a32a47392ec9
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157798"
---
# <a name="imloperatortensorshapedescriptiongetinputtensordimensioncount-method"></a>Имлоператортенсоршапедескриптион. Жетинпуттенсордименсионкаунт, метод

Возвращает количество измерений тензорные входных данных оператора. Возвращает ошибку, если входные данные по указанному индексу не являются тензорные.

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
