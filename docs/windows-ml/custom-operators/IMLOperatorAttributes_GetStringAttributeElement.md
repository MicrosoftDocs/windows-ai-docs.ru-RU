---
title: Имлоператораттрибутес. Жетстрингаттрибутилемент, метод
description: Возвращает значение элемента атрибута, имеющего строковый тип.
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, машинное обучение Windows, WinML, пользовательские операторы, Жетстрингаттрибутилемент
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorAttributes.GetStringAttributeElement
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 971312a00bb7d8995cf1c1fc1a19dafb20143854
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157107"
---
# <a name="imloperatorattributesgetstringattributeelement-method"></a>Имлоператораттрибутес. Жетстрингаттрибутилемент, метод

Возвращает значение элемента атрибута, имеющего строковый тип. Для атрибутов, которые являются строковыми массивами, этот метод запрашивает значение отдельного элемента в атрибуте по указанному индексу. Строка имеет формат UTF-8. Размер включает завершающий символ null.

```cpp
void GetStringAttributeElement(
    _In_z_ const char* name,
    uint32_t elementIndex,
    uint32_t attributeElementByteSize,
    _Out_writes_(uint32_t) char* attributeElement)
```

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборка 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | Млоператораусор. h |

[!INCLUDE [help](../../includes/get-help.md)]
