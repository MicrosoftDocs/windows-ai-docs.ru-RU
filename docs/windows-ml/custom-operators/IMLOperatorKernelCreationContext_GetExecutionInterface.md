---
title: Имлоператоркернелкреатионконтекст. Жетексекутионинтерфаце, метод
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
- IMLOperatorKernelCreationContext.GetExecutionInterface
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 8cec5c1da7fbd4c0aa211f9c6fb7f020eb46c6cd
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157371"
---
# <a name="imloperatorkernelcreationcontextgetexecutioninterface-method"></a>Имлоператоркернелкреатионконтекст. Жетексекутионинтерфаце, метод

Возвращает объект, Поддерживаемые интерфейсы которого различаются в зависимости от типа ядра. Для ядер, зарегистрированных с помощью [млоператорексекутионтипе:: CPU](MLOperatorExecutionType.md), *ексекутионобжект* будет иметь значение **nullptr**. Для ядер, зарегистрированных с помощью **млоператорексекутионтипе::D 3d12**, *ексекутионобжект* будет поддерживать интерфейс [ID3D12GraphicsCommandList](https://docs.microsoft.com/windows/desktop/api/d3d12/nn-d3d12-id3d12graphicscommandlist) .

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
