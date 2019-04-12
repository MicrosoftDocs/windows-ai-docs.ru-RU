---
author: eliotcowley
title: Метод IMLOperatorAttributes.GetStringAttributeElementLength
description: Возвращает длину элемента атрибута, который имеет строковый тип.
ms.author: elcowle
ms.date: 11/8/2018
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
ms.openlocfilehash: 633e97ce0533b514a6540b848fef397b87cbc008
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474541"
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
| **Минимальная версия клиента** | Windows 10, сборки 17763 |
| **Минимальная версия сервера** | Windows Server 2019 с возможностями рабочего стола |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
