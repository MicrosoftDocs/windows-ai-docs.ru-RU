---
author: eliotcowley
title: Метод IMLOperatorTensor.IsDataInterface
description: Ли содержимое тензорные представлены тип интерфейса или байтовой адресацией памяти.
ms.author: elcowle
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, windows машинного обучения, WinML, настраиваемые операторы, IsDataInterface
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorTensor.IsDataInterface
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 475311c07442660f83c0a9336468d6e9d2dbed00
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66180296"
---
# <a name="imloperatortensorisdatainterface-method"></a>Метод IMLOperatorTensor.IsDataInterface

Ли содержимое тензорные представлены тип интерфейса или байтовой адресацией памяти. Это возвращает true, если ядер регистрируются с использованием [MLOperatorExecutionType::D3D12](MLOperatorExecutionType.md).

```cpp
bool IsDataInterface()
```

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборки 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
