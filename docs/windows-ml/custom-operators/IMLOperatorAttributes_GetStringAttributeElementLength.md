---
title: Имлоператораттрибутес. Жетстрингаттрибутилементленгс, метод
description: Возвращает длину элемента атрибута, имеющего строковый тип.
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, машинное обучение Windows, WinML, пользовательские операторы, Жетстрингаттрибутилементленгс
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorAttributes.GetStringAttributeElementLength
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 66726d80d535837344912fafab561a57b87dee98
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157230"
---
# <a name="imloperatorattributesgetstringattributeelementlength-method"></a>Имлоператораттрибутес. Жетстрингаттрибутилементленгс, метод

Возвращает длину элемента атрибута, имеющего строковый тип. Для атрибутов, которые являются строковыми массивами, этот метод запрашивает размер отдельного элемента в пределах атрибута по указанному индексу. Строка имеет формат UTF-8.  Размер включает завершающий символ null.

```cpp
void GetStringAttributeElementLength(
    _In_z_ const char* name,
    uint32_t elementIndex,
    _Out_ uint32_t* attributeElementByteSize)
```

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборка 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | Млоператораусор. h |

[!INCLUDE [help](../../includes/get-help.md)]
