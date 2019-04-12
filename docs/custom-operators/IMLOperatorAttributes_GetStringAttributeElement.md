---
author: eliotcowley
title: Метод IMLOperatorAttributes.GetStringAttributeElement
description: Получает значение элемента атрибута, который имеет строковый тип.
ms.author: elcowle
ms.date: 11/8/2018
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
ms.openlocfilehash: 0dce6fabffcbe9bb6176ba86a4632facd9c9635b
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474771"
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
| **Минимальная версия клиента** | Windows 10, сборки 17763 |
| **Минимальная версия сервера** | Windows Server 2019 с возможностями рабочего стола |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
