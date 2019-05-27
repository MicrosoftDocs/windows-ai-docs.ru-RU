---
author: eliotcowley
title: Метод IMLOperatorKernelCreationContext.GetExecutionInterface
description: Возвращает объект, различаются, поддерживаемые интерфейсы на основе ядра типа.
ms.author: elcowle
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, windows машинного обучения, WinML, настраиваемые операторы, GetExecutionInterface
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorKernelCreationContext.GetExecutionInterface
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: d410e8ee9129cf09230bc46a3c1bb03d6431674e
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66180566"
---
# <a name="imloperatorkernelcreationcontextgetexecutioninterface-method"></a>Метод IMLOperatorKernelCreationContext.GetExecutionInterface

Возвращает объект, различаются, поддерживаемые интерфейсы на основе ядра типа. Для зарегистрированных ядра с [MLOperatorExecutionType::Cpu](MLOperatorExecutionType.md), *executionObject* будет присвоено **nullptr**. Для зарегистрированных ядра с **MLOperatorExecutionType::D3D12**, *executionObject* будет поддерживать [ID3D12GraphicsCommandList](https://docs.microsoft.com/windows/desktop/api/d3d12/nn-d3d12-id3d12graphicscommandlist) интерфейс.

```cpp
void GetExecutionInterface(
    _COM_Outptr_result_maybenull_ IUnknown** executionObject)
```

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборки 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
