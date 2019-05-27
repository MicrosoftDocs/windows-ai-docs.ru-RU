---
author: eliotcowley
title: Метод IMLOperatorAttributes.GetStringAttributeElementLength
description: Возвращает длину элемента атрибута, который имеет строковый тип.
ms.author: elcowle
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, windows машинного обучения, WinML, настраиваемые операторы, GetStringAttributeElementLength
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorAttributes.GetStringAttributeElementLength
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 31159c558c7740d35642072e33b373a75e50a77b
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66181136"
---
# <a name="imloperatorattributesgetstringattributeelementlength-method"></a>Метод IMLOperatorAttributes.GetStringAttributeElementLength

Возвращает длину элемента атрибута, который имеет строковый тип. Для атрибутов, которые являются массивы строк этот метод запрашивает размер отдельного элемента внутри атрибута по указанному индексу. Строка представлена в формате UTF-8.  Размер включает последний нулевой символ.

```cpp
void GetStringAttributeElementLength(
    _In_z_ const char* name,
    uint32_t elementIndex,
    _Out_ uint32_t* attributeElementByteSize)
```

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборки 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
