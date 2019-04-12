---
author: eliotcowley
title: Метод IMLOperatorAttributes.GetAttributeElementCount
description: Возвращает количество элементов в атрибуте.
ms.author: elcowle
ms.date: 11/8/2018
ms.topic: article
keywords: Windows 10, windows машинного обучения, WinML, настраиваемые операторы, GetAttributeElementCount
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorAttributes.GetAttributeElementCount
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: bbec1f1edf3678679136136ce045185935dc041d
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474921"
---
# <a name="imloperatorattributesgetattributeelementcount-method"></a>Метод IMLOperatorAttributes.GetAttributeElementCount

Возвращает количество элементов в атрибуте. Это может пригодиться для определения, если он существует и определить число элементов атрибута типа массива.

```cpp
void GetAttributeElementCount(
    _In_z_ const char* name,
    MLOperatorAttributeType type,
    _Out_ uint32_t* elementCount)
```

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальная версия клиента** | Windows 10, сборки 17763 |
| **Минимальная версия сервера** | Windows Server 2019 с возможностями рабочего стола |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
