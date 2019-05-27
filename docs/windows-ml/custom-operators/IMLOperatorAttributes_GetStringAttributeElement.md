---
author: eliotcowley
title: Метод IMLOperatorAttributes.GetStringAttributeElement
description: Получает значение элемента атрибута, который имеет строковый тип.
ms.author: elcowle
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, windows машинного обучения, WinML, настраиваемые операторы, GetStringAttributeElement
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorAttributes.GetStringAttributeElement
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 1012fdb8dde7e30e65cfea0a1c2874032383c3b4
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66181066"
---
# <a name="imloperatorattributesgetstringattributeelement-method"></a>Метод IMLOperatorAttributes.GetStringAttributeElement

Получает значение элемента атрибута, который имеет строковый тип. Для атрибутов, которые являются массивы строк этот метод запрашивает значение отдельного элемента внутри атрибута по указанному индексу. Строка представлена в формате UTF-8. Размер включает последний нулевой символ.

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
| **Минимальный поддерживаемый клиент** | Windows 10, сборки 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
