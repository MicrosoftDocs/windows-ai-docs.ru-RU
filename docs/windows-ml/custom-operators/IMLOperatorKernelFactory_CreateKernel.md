---
author: eliotcowley
title: Метод IMLOperatorKernelFactory.CreateKernel
description: Создает экземпляр ядра связанный оператор, учитывая сведения об использовании оператора в модель, описанную в указанный объект контекста.
ms.author: elcowle
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, windows машинного обучения, WinML, настраиваемые операторы, CreateKernel
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorKernelFactory.CreateKernel
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 8bf4b931267581e719d40e7166c59c8c813fe1ad
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66180876"
---
# <a name="imloperatorkernelfactorycreatekernel-method"></a>Метод IMLOperatorKernelFactory.CreateKernel

Создает экземпляр ядра связанный оператор, учитывая сведения об использовании оператора в модель, описанную в указанный объект контекста.

```cpp
void CreateKernel(
    IMLOperatorKernelCreationContext* context,
    _COM_Outptr_ IMLOperatorKernel** kernel)
```

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборки 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
