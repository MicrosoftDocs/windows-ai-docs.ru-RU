---
author: eliotcowley
title: Метод IMLOperatorKernelContext.GetInputTensor
description: Получает входной тензорные оператора по указанному индексу.
ms.author: elcowle
ms.date: 4/1/2019
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
ms.openlocfilehash: b848390fb31231bd30bbe3beaa3020d97f729b68
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66180786"
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
| **Минимальный поддерживаемый клиент** | Windows 10, сборки 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
