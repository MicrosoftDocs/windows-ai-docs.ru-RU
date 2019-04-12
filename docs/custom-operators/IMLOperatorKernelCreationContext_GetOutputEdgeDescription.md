---
author: eliotcowley
title: IMLOperatorKernelCreationContext.GetOutputEdgeDescription method
description: Получает описание указанный выходной края оператора.
ms.author: elcowle
ms.date: 11/8/2018
ms.topic: article
keywords: Windows 10, windows машинного обучения, WinML, настраиваемые операторы, GetOutputEdgeDescription
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorKernelCreationContext.GetOutputEdgeDescription
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 3f8322710c1f6406269368e24270dd15ae233bd2
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474111"
---
# <a name="imloperatorkernelcreationcontextgetoutputedgedescription-method"></a>IMLOperatorKernelCreationContext.GetOutputEdgeDescription method

Получает описание указанный выходной края оператора.

```cpp
void GetOutputEdgeDescription(
    uint32_t outputIndex, 
    _Out_ MLOperatorEdgeDescription* edgeDescription)
```

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальная версия клиента** | Windows 10, сборки 17763 |
| **Минимальная версия сервера** | Windows Server 2019 с возможностями рабочего стола |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
