---
author: eliotcowley
title: Метод IMLOperatorTensorShapeDescription.GetInputTensorDimensionCount
description: Получает размерность тензорные ввода оператора.
ms.author: elcowle
ms.date: 11/8/2018
ms.topic: article
keywords: Windows 10, windows машинного обучения, WinML, настраиваемые операторы, GetInputTensorDimensionCount
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorTensorShapeDescription.GetInputTensorDimensionCount
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: b3d7b39f635b830f2d7d031a3b889c916b90c6bf
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474261"
---
# <a name="imloperatortensorshapedescriptiongetinputtensordimensioncount-method"></a>Метод IMLOperatorTensorShapeDescription.GetInputTensorDimensionCount

Получает размерность тензорные ввода оператора. Возвращает ошибку, если входные данные по указанному индексу не тензорные.

```cpp
void GetInputTensorDimensionCount(
    uint32_t inputIndex, 
    _Out_ uint32_t* dimensionCount)
```

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальная версия клиента** | Windows 10, сборки 17763 |
| **Минимальная версия сервера** | Windows Server 2019 с возможностями рабочего стола |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
