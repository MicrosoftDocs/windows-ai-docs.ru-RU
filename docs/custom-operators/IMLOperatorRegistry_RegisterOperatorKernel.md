---
author: eliotcowley
title: Метод IMLOperatorRegistry.RegisterOperatorKernel
description: Регистрирует ядра пользовательского оператора.
ms.author: elcowle
ms.date: 11/8/2018
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
ms.openlocfilehash: d98ff79c38020cb4ad94496ffd8f6933c31a44bf
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474291"
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
| **Минимальная версия клиента** | Windows 10, сборки 17763 |
| **Минимальная версия сервера** | Windows Server 2019 с возможностями рабочего стола |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
