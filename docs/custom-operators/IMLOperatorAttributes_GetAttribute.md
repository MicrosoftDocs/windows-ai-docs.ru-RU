---
author: eliotcowley
title: Метод IMLOperatorAttributes.GetAttribute
description: Получает значение атрибута элемента, являющегося числового типа.
ms.author: elcowle
ms.date: 11/8/2018
ms.topic: article
keywords: Windows 10, windows машинного обучения, WinML, настраиваемые операторы, GetAttribute
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorAttributes.GetAttribute
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 6d048cf3f4a38ba066940f73060bc6238aed87a4
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474601"
---
# <a name="imloperatorattributesgetattribute-method"></a>Метод IMLOperatorAttributes.GetAttribute

Получает значение атрибута элемента, являющегося числового типа. Для атрибутов, которые являются массивом типов этот метод запрашивает отдельном элементе атрибута по указанному индексу.

```cpp
void GetAttribute(
    _In_z_ const char* name,
    MLOperatorAttributeType type,
    uint32_t elementCount,
    size_t elementByteSize,
    _Out_writes_bytes_(elementCount * elementByteSize) void* value)
```

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальная версия клиента** | Windows 10, сборки 17763 |
| **Минимальная версия сервера** | Windows Server 2019 с возможностями рабочего стола |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
