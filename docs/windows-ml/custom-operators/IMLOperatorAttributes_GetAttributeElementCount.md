---
title: Имлоператораттрибутес. Жетаттрибутилементкаунт, метод
description: Возвращает число элементов в атрибуте.
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, машинное обучение Windows, WinML, пользовательские операторы, Жетаттрибутилементкаунт
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorAttributes.GetAttributeElementCount
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 49495e21eb79e04dae926bf03e67be3de0e396e3
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157048"
---
# <a name="imloperatorattributesgetattributeelementcount-method"></a>Имлоператораттрибутес. Жетаттрибутилементкаунт, метод

Возвращает число элементов в атрибуте. Это может использоваться для определения существования атрибута и для определения количества элементов в атрибуте типа массива.

```cpp
void GetAttributeElementCount(
    _In_z_ const char* name,
    MLOperatorAttributeType type,
    _Out_ uint32_t* elementCount)
```

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборка 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | Млоператораусор. h |

[!INCLUDE [help](../../includes/get-help.md)]
