---
author: eliotcowley
title: Метод IMLOperatorTensor.GetData
description: Возвращает указатель на память байтовой адресацией для тензорные.
ms.author: elcowle
ms.date: 11/8/2018
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
ms.openlocfilehash: f3a5e926901c315124dd235b18bc3e6aa5072b6e
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474301"
---
# <a name="imloperatortensorgetdata-method"></a>Метод IMLOperatorTensor.GetData

Возвращает указатель на память байтовой адресацией для тензорные. Это может быть, используемого при [IMLOperatorTensor::IsDataInterface](IMLOperatorTensor_IsDataInterface.md) возвращает false, так как ядро был зарегистрирован с помощью [MLOperatorExecutionType::Cpu](MLOperatorExecutionType.md). Размер данных является производным от тензорные фигуры. Полностью, он упаковывается в памяти.

```cpp
void* GetData()
```

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальная версия клиента** | Windows 10, сборки 17763 |
| **Минимальная версия сервера** | Windows Server 2019 с возможностями рабочего стола |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
