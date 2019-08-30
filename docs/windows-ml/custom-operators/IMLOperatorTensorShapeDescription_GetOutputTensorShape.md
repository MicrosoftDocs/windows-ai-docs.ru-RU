---
title: Имлоператортенсоршапедескриптион. Жетаутпуттенсоршапе, метод
description: Возвращает размеры размеров тензорные выходных данных оператора.
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, машинное обучение Windows, WinML, пользовательские операторы, Жетаутпуттенсоршапе
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorTensorShapeDescription.GetOutputTensorShape
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 5d7672315ef36203bfdd6985526c39057d23760b
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157827"
---
# <a name="imloperatortensorshapedescriptiongetoutputtensorshape-method"></a>Имлоператортенсоршапедескриптион. Жетаутпуттенсоршапе, метод

Возвращает размеры размеров тензорные выходных данных оператора. Возвращает ошибку, если выходные данные по указанному индексу не являются тензорные.

```cpp
GetOutputTensorShape(
    uint32_t outputIndex,
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
