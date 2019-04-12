---
author: eliotcowley
title: Метод IMLOperatorShapeInferenceContext.IsOutputValid
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
- IMLOperatorShapeInferenceContext.IsOutputValid
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: a761249ce973b228664cb6dccb828ce72692868d
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474331"
---
# <a name="imloperatorshapeinferencecontextisoutputvalid-method"></a>Метод IMLOperatorShapeInferenceContext.IsOutputValid

Возвращает значение true, если выходные данные оператора является допустимым. Эта функция всегда возвращает значение true, за исключением необязательные выходные данные и индексы недопустимый.

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
