---
title: Имлоператоррегистри. Регистероператоркернел, метод
description: Регистрирует ядро пользовательского оператора.
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, машинное обучение Windows, WinML, пользовательские операторы, Регистероператоркернел
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorRegistry.RegisterOperatorKernel
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 86dd68896d6855295915d7b37ef1e88e933c7ccd
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157646"
---
# <a name="imloperatorregistryregisteroperatorkernel-method"></a>Имлоператоррегистри. Регистероператоркернел, метод

Регистрирует ядро пользовательского оператора. При необходимости можно указать источники ссылок на фигуру.  Это может повысить производительность и позволяет ядру запрашивать форму выходных десятков при создании и вычислении.

```cpp
void RegisterOperatorKernel(
    const MLOperatorKernelDescription* operatorKernel,
    IMLOperatorKernelFactory* operatorKernelFactory,
    _In_opt_ IMLOperatorShapeInferrer* shapeInferrer)
```

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборка 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | Млоператораусор. h |

[!INCLUDE [help](../../includes/get-help.md)]
