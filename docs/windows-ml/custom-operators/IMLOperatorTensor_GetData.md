---
title: Имлоператортенсор. GetData, метод
description: Возвращает указатель на память с адресацией по байтам для тензорные.
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, машинное обучение Windows, WinML, пользовательские операторы, GetData
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorTensor.GetData
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 150def2eb9f33e0ffdcb1c77e6429862f4697705
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157887"
---
# <a name="imloperatortensorgetdata-method"></a>Имлоператортенсор. GetData, метод

Возвращает указатель на память с адресацией по байтам для тензорные. Это может использоваться, когда [имлоператортенсор:: исдатаинтерфаце](IMLOperatorTensor_IsDataInterface.md) возвращает значение false, так как ядро зарегистрировано с помощью [Млоператорексекутионтипе:: CPU](MLOperatorExecutionType.md). Размер данных является производным от фигуры тензорные. Он полностью упакован в память.

```cpp
void* GetData()
```

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборка 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | Млоператораусор. h |

[!INCLUDE [help](../../includes/get-help.md)]
