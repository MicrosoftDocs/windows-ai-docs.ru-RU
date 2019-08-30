---
title: Имлоператоркернел. COMPUTE, метод
description: Выполняет вычисление выходных данных ядра.
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, машинное обучение Windows, WinML, пользовательские операторы, вычисление
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorKernel.Compute
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: d29b07d8e66e0666db29cfb66adde15191393eb4
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157585"
---
# <a name="imloperatorkernelcompute-method"></a>Имлоператоркернел. COMPUTE, метод

Выполняет вычисление выходных данных ядра. Реализация этого метода должна быть потокобезопасной. Один и тот же экземпляр ядра может вычисляться одновременно в разных потоках.

```cpp
void Compute(
    IMLOperatorKernelContext* context)
```

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборка 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | Млоператораусор. h |

[!INCLUDE [help](../../includes/get-help.md)]
