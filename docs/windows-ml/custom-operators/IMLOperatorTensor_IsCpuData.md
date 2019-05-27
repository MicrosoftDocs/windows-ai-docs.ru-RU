---
author: eliotcowley
title: Метод IMLOperatorTensor.IsCpuData
description: Указывает, является ли память, занятая тензорные ЦП адресацию.
ms.author: elcowle
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, windows машинного обучения, WinML, настраиваемые операторы, IsCpuData
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorTensor.IsCpuData
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 41bf7d78013dd6f8445e8e671974ec5745e99502
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66180386"
---
# <a name="imloperatortensoriscpudata-method"></a>Метод IMLOperatorTensor.IsCpuData

Указывает, является ли память, занятая тензорные ЦП адресацию. Это касается ядра они регистрируются с помощью [MLOperatorExecutionType::Cpu](MLOperatorExecutionType.md).

```cpp
bool IsCpuData()
```

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборки 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
