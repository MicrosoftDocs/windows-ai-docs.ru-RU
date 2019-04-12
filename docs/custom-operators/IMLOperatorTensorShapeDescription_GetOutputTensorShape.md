---
author: eliotcowley
title: Метод IMLOperatorTensorShapeDescription.GetOutputTensorShape
description: Получает размеры измерениях тензорные выходных данных оператора.
ms.author: elcowle
ms.date: 11/8/2018
ms.topic: article
keywords: Windows 10, windows машинного обучения, WinML, настраиваемые операторы, GetOutputTensorShape
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorTensorShapeDescription.GetOutputTensorShape
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: e0ee2405831213e8ee537bf3e8a1960acf328bc1
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474031"
---
# <a name="imloperatortensorshapedescriptiongetoutputtensorshape-method"></a>Метод IMLOperatorTensorShapeDescription.GetOutputTensorShape

Получает размеры измерениях тензорные выходных данных оператора. Возвращает ошибку, если выходные данные по указанному индексу не тензорные.

```cpp
GetOutputTensorShape(
    uint32_t outputIndex, 
    uint32_t dimensionCount, 
    _Out_writes_(dimensionCount) uint32_t* dimensions)
```

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальная версия клиента** | Windows 10, сборки 17763 |
| **Минимальная версия сервера** | Windows Server 2019 с возможностями рабочего стола |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
