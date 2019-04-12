---
author: eliotcowley
title: Метод IMLOperatorTensorShapeDescription.GetInputTensorShape
description: Возвращает размеры измерений из входного тензорные оператора.
ms.author: elcowle
ms.date: 11/8/2018
ms.topic: article
keywords: Windows 10, windows машинного обучения, WinML, настраиваемые операторы, GetInputTensorShape
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorTensorShapeDescription.GetInputTensorShape
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 5e602bec3e76994fcd85488551dde20db3d08c59
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474051"
---
# <a name="imloperatortensorshapedescriptiongetinputtensorshape-method"></a>Метод IMLOperatorTensorShapeDescription.GetInputTensorShape

Возвращает размеры измерений из входного тензорные оператора. Возвращает ошибку, если входные данные по указанному индексу не тензорные.

```cpp
void GetInputTensorShape(
    uint32_t inputIndex, 
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
