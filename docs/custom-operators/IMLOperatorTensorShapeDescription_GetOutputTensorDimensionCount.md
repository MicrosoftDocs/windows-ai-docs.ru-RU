---
author: eliotcowley
title: Метод IMLOperatorTensorShapeDescription.GetOutputTensorDimensionCount
description: Получает размерность вывода тензорные оператора.
ms.author: elcowle
ms.date: 11/8/2018
ms.topic: article
keywords: Windows 10, windows машинного обучения, WinML, настраиваемые операторы, GetOutputTensorDimensionCount
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorTensorShapeDescription.GetOutputTensorDimensionCount
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 24b2c467fbb0e9cec55f48fefac145db6174b1bb
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474881"
---
# <a name="imloperatortensorshapedescriptiongetoutputtensordimensioncount-method"></a>Метод IMLOperatorTensorShapeDescription.GetOutputTensorDimensionCount

Получает размерность вывода тензорные оператора. Возвращает ошибку, если выходные данные по указанному индексу не тензорные.

```cpp
GetOutputTensorDimensionCount(
    uint32_t outputIndex, 
    _Out_ uint32_t* dimensionCount)
```

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальная версия клиента** | Windows 10, сборки 17763 |
| **Минимальная версия сервера** | Windows Server 2019 с возможностями рабочего стола |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
