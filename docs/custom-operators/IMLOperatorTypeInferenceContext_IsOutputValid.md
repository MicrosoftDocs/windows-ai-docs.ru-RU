---
author: eliotcowley
title: Метод IMLOperatorTypeInferenceContext.IsOutputValid
description: Возвращает значение true, если выходные данные оператора является допустимым.
ms.author: elcowle
ms.date: 11/8/2018
ms.topic: article
keywords: Windows 10, windows машинного обучения, WinML, настраиваемые операторы, IsOutputValid
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorTypeInferenceContext.IsOutputValid
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: ec33aabec34cd9de96372934845e2dab39b55515
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474441"
---
# <a name="imloperatortypeinferencecontextisoutputvalid-method"></a>Метод IMLOperatorTypeInferenceContext.IsOutputValid

Возвращает значение true, если выходные данные оператора является допустимым. Эта функция всегда возвращает значение true, за исключением необязательные выходные данные.

```cpp
bool IsOutputValid(
    uint32_t outputIndex)
```

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальная версия клиента** | Windows 10, сборки 17763 |
| **Минимальная версия сервера** | Windows Server 2019 с возможностями рабочего стола |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
