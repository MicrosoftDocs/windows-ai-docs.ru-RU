---
title: Имлоператоркернелконтекст. Жетинпуттенсор, метод
description: Возвращает входной тензорные оператора по указанному индексу.
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, машинное обучение Windows, WinML, пользовательские операторы, Жетинпуттенсор
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorKernelContext.GetInputTensor
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 8d35408495d4ee08ae42d11d77103bf64fb2bb3f
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157304"
---
# <a name="imloperatorkernelcontextgetinputtensor-method"></a>Имлоператоркернелконтекст. Жетинпуттенсор, метод

Возвращает входной тензорные оператора по указанному индексу. Это устанавливает тензорные в значение **nullptr** для необязательных входных данных, которые не существуют. Возвращает ошибку, если входные данные по указанному индексу не являются тензорные.

```cpp
void GetInputTensor(
    uint32_t inputIndex,
    _COM_Outptr_result_maybenull_ IMLOperatorTensor** tensor)
```

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборка 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | Млоператораусор. h |

[!INCLUDE [help](../../includes/get-help.md)]
