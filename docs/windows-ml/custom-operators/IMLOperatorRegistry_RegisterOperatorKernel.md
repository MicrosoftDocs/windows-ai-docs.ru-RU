---
author: eliotcowley
title: Метод IMLOperatorRegistry.RegisterOperatorKernel
description: Регистрирует ядра пользовательского оператора.
ms.author: elcowle
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, windows машинного обучения, WinML, настраиваемые операторы, RegisterOperatorKernel
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorRegistry.RegisterOperatorKernel
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: ee74cda25980361adc8c435e903dd8ddbc0717cf
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66181706"
---
# <a name="imloperatorregistryregisteroperatorkernel-method"></a>Метод IMLOperatorRegistry.RegisterOperatorKernel

Регистрирует ядра пользовательского оператора. При необходимости может быть оказана inferrer фигуры.  Это может повысить производительность и обеспечивает ядра для запроса вида tensors его выходные данные при его создании и вычислить.

```cpp
void RegisterOperatorKernel(
    const MLOperatorKernelDescription* operatorKernel,
    IMLOperatorKernelFactory* operatorKernelFactory,
    _In_opt_ IMLOperatorShapeInferrer* shapeInferrer)
```

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборки 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
