---
author: eliotcowley
title: Метод IMLOperatorKernelCreationContext.GetTensorShapeDescription
description: Получает описание фигуры ввода-вывода по краям оператор.
ms.author: elcowle
ms.date: 11/8/2018
ms.topic: article
keywords: Windows 10, windows машинного обучения, WinML, настраиваемые операторы, GetTensorShapeDescription
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorKernelCreationContext.GetTensorShapeDescription
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 7832d281a2c5b0c5699840e4c431a4bf87886a39
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474501"
---
# <a name="imloperatorkernelcreationcontextgettensorshapedescription-method"></a>Метод IMLOperatorKernelCreationContext.GetTensorShapeDescription

Получает описание фигуры ввода-вывода по краям оператор.

```cpp
void GetTensorShapeDescription(
    _COM_Outptr_ IMLOperatorTensorShapeDescription** shapeDescription)
```

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальная версия клиента** | Windows 10, сборки 17763 |
| **Минимальная версия сервера** | Windows Server 2019 с возможностями рабочего стола |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
