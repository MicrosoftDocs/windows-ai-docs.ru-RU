---
author: eliotcowley
title: Метод IMLOperatorTypeInferenceContext.IsInputValid
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
- IMLOperatorTypeInferenceContext.IsInputValid
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 12a18d3c8ffb023d3bff94e193681718c6cd3cd2
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2019
ms.locfileid: "59475011"
---
# <a name="imloperatortypeinferencecontextisinputvalid-method"></a>Метод IMLOperatorTypeInferenceContext.IsInputValid

Возвращает значение true, если входными данными для оператора является допустимым. Эта функция всегда возвращает значение true, за исключением необязательных набора входных данных.

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
