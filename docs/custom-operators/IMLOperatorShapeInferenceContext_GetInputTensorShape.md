---
author: eliotcowley
title: Метод IMLOperatorShapeInferenceContext.GetInputTensorShape
description: Возвращает размеры измерений из входного тензорные оператора.
ms.author: elcowle
ms.date: 11/8/2018
ms.topic: article
keywords: Windows 10, windows машинного обучения, WinML, настраиваемые операторы, GetInputTensorShape
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorShapeInferenceContext.GetInputTensorShape
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 9db3129765e89dea3923ef28cb171e292b34e27e
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2019
ms.locfileid: "59473851"
---
# <a name="imloperatorshapeinferencecontextgetinputtensorshape-method"></a>Метод IMLOperatorShapeInferenceContext.GetInputTensorShape

Возвращает размеры измерений из входного тензорные оператора. Возвращает ошибку, если входные данные по указанному индексу не тензорные.

```cpp
void GetInputTensorShape(
    uint32_t inputIndex,
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
