---
title: Имлоператораттрибутес. OutAttribute, метод
description: Возвращает значение элемента атрибута, имеющего числовой тип.
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, машинное обучение Windows, WinML, пользовательские операторы, OutAttribute
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorAttributes.GetAttribute
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 69c886c7b8b837cff01d12d369debf924a3d9160
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157077"
---
# <a name="imloperatorattributesgetattribute-method"></a>Имлоператораттрибутес. OutAttribute, метод

Возвращает значение элемента атрибута, имеющего числовой тип. Для атрибутов, которые относятся к типам массивов, этот метод запрашивает отдельный элемент в атрибуте по указанному индексу.

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
| **Минимальный поддерживаемый клиент** | Windows 10, сборка 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | Млоператораусор. h |

[!INCLUDE [help](../../includes/get-help.md)]
