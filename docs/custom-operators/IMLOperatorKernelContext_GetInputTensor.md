---
author: eliotcowley
title: Метод IMLOperatorKernelContext.GetInputTensor
description: Получает входной тензорные оператора по указанному индексу.
ms.author: elcowle
ms.date: 11/8/2018
ms.topic: article
keywords: Windows 10, windows машинного обучения, WinML, настраиваемые операторы, GetInputTensor
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorKernelContext.GetInputTensor
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 288e2f13f1eaf92a435047fd48c739f017b1d877
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474351"
---
# <a name="imloperatorkernelcontextgetinputtensor-method"></a>Метод IMLOperatorKernelContext.GetInputTensor

Получает входной тензорные оператора по указанному индексу. Это задает тензорные **nullptr** для необязательных набора входных данных, которые не существуют. Возвращает ошибку, если входные данные по указанному индексу не тензорные.

```cpp
void GetInputTensor(
    uint32_t inputIndex, 
    _COM_Outptr_result_maybenull_ IMLOperatorTensor** tensor)
```

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальная версия клиента** | Windows 10, сборки 17763 |
| **Минимальная версия сервера** | Windows Server 2019 с возможностями рабочего стола |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
