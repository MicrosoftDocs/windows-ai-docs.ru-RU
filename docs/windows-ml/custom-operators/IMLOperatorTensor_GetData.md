---
author: eliotcowley
title: Метод IMLOperatorTensor.GetData
description: Возвращает указатель на память байтовой адресацией для тензорные.
ms.author: elcowle
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, windows машинного обучения, WinML, настраиваемые операторы, GetData
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorTensor.GetData
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 52ec28b5929fb9ee6eb987c6210e41ce5634bb62
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66181076"
---
# <a name="imloperatortensorgetdata-method"></a>Метод IMLOperatorTensor.GetData

Возвращает указатель на память байтовой адресацией для тензорные. Это может быть, используемого при [IMLOperatorTensor::IsDataInterface](IMLOperatorTensor_IsDataInterface.md) возвращает false, так как ядро был зарегистрирован с помощью [MLOperatorExecutionType::Cpu](MLOperatorExecutionType.md). Размер данных является производным от тензорные фигуры. Полностью, он упаковывается в памяти.

```cpp
void* GetData()
```

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборки 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
