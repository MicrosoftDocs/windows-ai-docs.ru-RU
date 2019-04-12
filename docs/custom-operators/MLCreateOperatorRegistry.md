---
author: eliotcowley
title: Функция MLCreateOperatorRegistry
description: Создает экземпляр класса **IMLOperatorRegistry** которого может использоваться для регистрации пользовательского оператора ядра и схемы пользовательского оператора.
ms.author: elcowle
ms.date: 11/8/2018
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
ms.openlocfilehash: d0cc289af9b7746dbb9015cf6108995467f79cd2
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2019
ms.locfileid: "59473981"
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
| **Минимальная версия клиента** | Windows 10, сборки 17763 |
| **Минимальная версия сервера** | Windows Server 2019 с возможностями рабочего стола |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
