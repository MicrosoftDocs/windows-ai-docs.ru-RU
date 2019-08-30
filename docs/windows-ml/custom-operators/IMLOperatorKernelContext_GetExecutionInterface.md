---
title: Имлоператоркернелконтекст. Жетексекутионинтерфаце, метод
description: Возвращает объект, Поддерживаемые интерфейсы которого различаются в зависимости от типа ядра.
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, машинное обучение Windows, WinML, пользовательские операторы, Жетексекутионинтерфаце
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorKernelContext.GetExecutionInterface
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: fa342999351dd2c1a218ffd086bcd09a1ec9405f
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157284"
---
# <a name="imloperatorkernelcontextgetexecutioninterface-method"></a>Имлоператоркернелконтекст. Жетексекутионинтерфаце, метод

Возвращает объект, Поддерживаемые интерфейсы которого различаются в зависимости от типа ядра. Для ядер, зарегистрированных с помощью [млоператорексекутионтипе:: CPU](MLOperatorExecutionType.md), *ексекутионобжект* будет иметь значение **nullptr**. Для ядер, зарегистрированных с помощью **млоператорексекутионтипе::D 3d12**, *ексекутионобжект* будет поддерживать интерфейс [ID3D12GraphicsCommandList](https://docs.microsoft.com/windows/desktop/api/d3d12/nn-d3d12-id3d12graphicscommandlist) . Это может быть объект, отличный от предоставленного для [имлоператоркернелкреатионконтекст:: жетексекутионинтерфаце](IMLOperatorKernelCreationContext_GetExecutionInterface.md) при создании экземпляра ядра.

```cpp
void GetExecutionInterface(
    _COM_Outptr_result_maybenull_ IUnknown** executionObject)
```

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборка 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | Млоператораусор. h |

[!INCLUDE [help](../../includes/get-help.md)]
