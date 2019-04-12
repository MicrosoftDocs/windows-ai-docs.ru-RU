---
author: eliotcowley
title: Метод IMLOperatorTensor.GetShape
description: Получает размер измерений в тензорные.
ms.author: elcowle
ms.date: 11/8/2018
ms.topic: article
keywords: Windows 10, windows машинного обучения, WinML, настраиваемые операторы, GetShape
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorTensor.GetShape
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 37d0485f8495832f854009500e49d7fae1f4ed04
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474421"
---
# <a name="imloperatortensorgetshape-method"></a>Метод IMLOperatorTensor.GetShape

Получает размер измерений в тензорные.

```cpp
void GetShape(
    uint32_t dimensionCount,
    _Out_writes_(dimensionCount) uint32_t* dimensions)
```

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальная версия клиента** | Windows 10, сборки 17763 |
| **Минимальная версия сервера** | Windows Server 2019 с возможностями рабочего стола |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
