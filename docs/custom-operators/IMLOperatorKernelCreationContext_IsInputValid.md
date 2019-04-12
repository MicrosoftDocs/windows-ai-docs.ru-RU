---
author: eliotcowley
title: Метод IMLOperatorKernelCreationContext.IsInputValid
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
- IMLOperatorKernelCreationContext.IsInputValid
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 9790098f3e3e69236b75ba00d30022bdd1e375b8
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474781"
---
# <a name="imloperatorkernelcreationcontextisinputvalid-method"></a>Метод IMLOperatorKernelCreationContext.IsInputValid

Возвращает значение true, если входными данными для оператора является допустимым. Эта функция всегда возвращает значение true, за исключением необязательных набора входных данных.

```cpp
bool IsInputValid(uint32_t inputIndex)
```

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальная версия клиента** | Windows 10, сборки 17763 |
| **Минимальная версия сервера** | Windows Server 2019 с возможностями рабочего стола |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
