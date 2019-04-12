---
author: eliotcowley
title: Метод IMLOperatorShapeInferenceContext.GetInputEdgeDescription
description: Возвращает описание указанного входного края оператора.
ms.author: elcowle
ms.date: 11/8/2018
ms.topic: article
keywords: Windows 10, windows машинного обучения, WinML, настраиваемые операторы, GetInputEdgeDescription
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorShapeInferenceContext.GetInputEdgeDescription
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 265aff2a2d69a42ac45476c5d7a4f979e65a307f
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474221"
---
# <a name="imloperatorshapeinferencecontextgetinputedgedescription-method"></a>Метод IMLOperatorShapeInferenceContext.GetInputEdgeDescription

Возвращает описание указанного входного края оператора.

```cpp
void GetInputEdgeDescription(
    uint32_t inputIndex,
    _Out_ MLOperatorEdgeDescription* edgeDescription)
```

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальная версия клиента** | Windows 10, сборки 17763 |
| **Минимальная версия сервера** | Windows Server 2019 с возможностями рабочего стола |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
