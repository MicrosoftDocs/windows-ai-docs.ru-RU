---
author: eliotcowley
title: Метод IMLOperatorKernelCreationContext.IsOutputValid
description: Возвращает значение true, если выходные данные оператора является допустимым.
ms.author: elcowle
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, windows машинного обучения, WinML, настраиваемые операторы, IsOutputValid
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorKernelCreationContext.IsOutputValid
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: b39a2c57a5deec11ff1b1d6cdfd133f982ef0f5b
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66180486"
---
# <a name="imloperatorkernelcreationcontextisoutputvalid-method"></a>Метод IMLOperatorKernelCreationContext.IsOutputValid

Возвращает значение true, если выходные данные оператора является допустимым. Эта функция всегда возвращает значение true, за исключением необязательные выходные данные.

```cpp
bool IsOutputValid(uint32_t outputIndex)
```

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборки 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
