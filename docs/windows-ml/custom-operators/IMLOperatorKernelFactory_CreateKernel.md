---
title: Имлоператоркернелфактори. Креатекернел, метод
description: Создает экземпляр связанного оператора ядра, учитывая сведения об использовании оператора в модели, описанной в предоставленном объекте контекста.
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, машинное обучение Windows, WinML, пользовательские операторы, Креатекернел
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorKernelFactory.CreateKernel
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: fa1b909903d803bdc2e4b22c7edc92f5a4c6a288
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157561"
---
# <a name="imloperatorkernelfactorycreatekernel-method"></a>Имлоператоркернелфактори. Креатекернел, метод

Создает экземпляр связанного оператора ядра, учитывая сведения об использовании оператора в модели, описанной в предоставленном объекте контекста.

```cpp
void CreateKernel(
    IMLOperatorKernelCreationContext* context,
    _COM_Outptr_ IMLOperatorKernel** kernel)
```

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборка 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | Млоператораусор. h |

[!INCLUDE [help](../../includes/get-help.md)]
