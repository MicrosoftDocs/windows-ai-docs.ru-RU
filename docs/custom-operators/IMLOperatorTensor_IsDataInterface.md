---
author: eliotcowley
title: Метод IMLOperatorTensor.IsDataInterface
description: Ли содержимое тензорные представлены тип интерфейса или байтовой адресацией памяти.
ms.author: elcowle
ms.date: 11/8/2018
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
ms.openlocfilehash: 410f74d1518229813b9504bc4f78d076a68ef6f5
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474041"
---
# <a name="imloperatortensorisdatainterface-method"></a>Метод IMLOperatorTensor.IsDataInterface

Ли содержимое тензорные представлены тип интерфейса или байтовой адресацией памяти. Это возвращает true, если ядер регистрируются с использованием [MLOperatorExecutionType::D3D12](MLOperatorExecutionType.md).

```cpp
bool IsDataInterface()
```

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальная версия клиента** | Windows 10, сборки 17763 |
| **Минимальная версия сервера** | Windows Server 2019 с возможностями рабочего стола |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
