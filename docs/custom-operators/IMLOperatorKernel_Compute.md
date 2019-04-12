---
author: eliotcowley
title: Метод IMLOperatorKernel.Compute
description: Вычисляет выходные данные ядра.
ms.author: elcowle
ms.date: 11/8/2018
ms.topic: article
keywords: Windows 10, windows машинное обучение, WinML, пользовательские операторы Compute
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorKernel.Compute
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: bcdf39f14e84872624a2c20cfcef437c80010b76
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474751"
---
# <a name="imloperatorkernelcompute-method"></a>Метод IMLOperatorKernel.Compute

Вычисляет выходные данные ядра. Реализация этого метода должны быть потокобезопасными. Один и тот же экземпляр ядра могут вычисляться одновременно в разных потоках.

```cpp
void Compute(
    IMLOperatorKernelContext* context)
```

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальная версия клиента** | Windows 10, сборки 17763 |
| **Минимальная версия сервера** | Windows Server 2019 с возможностями рабочего стола |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
