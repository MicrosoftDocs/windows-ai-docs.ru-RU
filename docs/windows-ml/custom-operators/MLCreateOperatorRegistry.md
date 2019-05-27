---
author: eliotcowley
title: Функция MLCreateOperatorRegistry
description: Создает экземпляр класса **IMLOperatorRegistry** которого может использоваться для регистрации пользовательского оператора ядра и схемы пользовательского оператора.
ms.author: elcowle
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, windows машинного обучения, WinML, настраиваемые операторы, MLCreateOperatorRegistry
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- MLCreateOperatorRegistry
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: a94b68f559e4a959a0a39b196f26f49923326c30
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66181486"
---
# <a name="mlcreateoperatorregistry-function"></a>Функция MLCreateOperatorRegistry

Создает экземпляр класса [IMLOperatorRegistry](IMLOperatorRegistry.md) которого может использоваться для регистрации пользовательского оператора ядра и схемы пользовательского оператора.

```cpp
HRESULT MLCreateOperatorRegistry(
    _COM_Outptr_ IMLOperatorRegistry** registry)
```

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборки 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
