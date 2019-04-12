---
author: eliotcowley
title: Метод IMLOperatorShapeInferenceContext.IsInputValid
description: Возвращает значение true, если входными данными для оператора является допустимым.
ms.author: elcowle
ms.date: 11/8/2018
ms.topic: article
keywords: Windows 10, windows машинного обучения, WinML, настраиваемые операторы, IsInputValid
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorShapeInferenceContext.IsInputValid
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 0bfda42be228353b3913ad15a93e6def9d9911d6
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2019
ms.locfileid: "59473831"
---
# <a name="imloperatorshapeinferencecontextisinputvalid-method"></a>Метод IMLOperatorShapeInferenceContext.IsInputValid

Возвращает значение true, если входными данными для оператора является допустимым. Эта функция всегда возвращает значение true, за исключением необязательных входных данных и недопустимый индексов.

```cpp
bool IsInputValid(
    uint32_t inputIndex)
```

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальная версия клиента** | Windows 10, сборки 17763 |
| **Минимальная версия сервера** | Windows Server 2019 с возможностями рабочего стола |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
