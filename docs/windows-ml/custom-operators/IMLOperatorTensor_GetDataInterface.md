---
title: Имлоператортенсор. Жетдатаинтерфаце, метод
description: Возвращает указатель интерфейса для тензорные.
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, машинное обучение Windows, WinML, пользовательские операторы, Жетдатаинтерфаце
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorTensor.GetDataInterface
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 84903d4a3be68494de5352ee7368056b9ac1b6f8
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157865"
---
# <a name="imloperatortensorgetdatainterface-method"></a>Имлоператортенсор. Жетдатаинтерфаце, метод

Возвращает указатель интерфейса для тензорные. Это может использоваться, когда [имлоператортенсор:: исдатаинтерфаце](IMLOperatorTensor_IsDataInterface.md) возвращает true, так как ядро зарегистрировано с помощью [Млоператорексекутионтипе::D 3d12](MLOperatorExecutionType.md). Объект *Interface* поддерживает [интерфейс ID3D12Resource](https://docs.microsoft.com/windows/desktop/api/d3d12/nn-d3d12-id3d12resource), а — буфер GPU.

```cpp
void GetDataInterface(
    _COM_Outptr_result_maybenull_ IUnknown** dataInterface)
```

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборка 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | Млоператораусор. h |

[!INCLUDE [help](../../includes/get-help.md)]
