---
author: eliotcowley
title: Метод IMLOperatorKernelCreationContext.HasTensorShapeDescription
description: Возвращает значение true, если описание фигуры входных и выходных подключен к краям оператор может запрашиваться с помощью **GetTensorShapeDescription**.
ms.author: elcowle
ms.date: 11/8/2018
ms.topic: article
keywords: Windows 10, windows машинного обучения, WinML, настраиваемые операторы, HasTensorShapeDescription
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorKernelCreationContext.HasTensorShapeDescription
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: cc72e6ab688d72cf124cf4b795f236ddc7554048
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2019
ms.locfileid: "59475061"
---
# <a name="imloperatorkernelcreationcontexthastensorshapedescription-method"></a>Метод IMLOperatorKernelCreationContext.HasTensorShapeDescription

Возвращает значение true, если описание фигуры входных и выходных подключен к краям оператор может запрашиваться с помощью [IMLOperatorKernelCreationContext::GetTensorShapeDescription](IMLOperatorKernelCreationContext_GetTensorShapeDescription.md). Это возвращает значение true, если оператор был зарегистрирован с помощью [MLOperatorKernelOptions::AllowDynamicInputShapes](MLOperatorKernelOptions.md) флаг.

```cpp
bool HasTensorShapeDescription()
```

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальная версия клиента** | Windows 10, сборки 17763 |
| **Минимальная версия сервера** | Windows Server 2019 с возможностями рабочего стола |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
