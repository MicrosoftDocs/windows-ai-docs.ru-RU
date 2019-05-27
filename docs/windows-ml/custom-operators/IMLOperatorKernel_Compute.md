---
author: eliotcowley
title: Метод IMLOperatorKernel.Compute
description: Вычисляет выходные данные ядра.
ms.author: elcowle
ms.date: 4/1/2019
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
ms.openlocfilehash: c753516f3739b75292f5d52ce805d61faf168c3f
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66181146"
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
| **Минимальный поддерживаемый клиент** | Windows 10, сборки 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
