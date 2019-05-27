---
author: eliotcowley
title: Метод IMLOperatorKernelContext.GetExecutionInterface
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
- IMLOperatorKernelContext.GetExecutionInterface
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 1425dca9dadd2a8a2c44b0c4c9ac5037e635244c
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66181166"
---
# <a name="imloperatorkernelcontextgetexecutioninterface-method"></a>Метод IMLOperatorKernelContext.GetExecutionInterface

Возвращает объект, различаются, поддерживаемые интерфейсы на основе ядра типа. Для зарегистрированных ядра с [MLOperatorExecutionType::Cpu](MLOperatorExecutionType.md), *executionObject* будет присвоено **nullptr**. Для зарегистрированных ядра с **MLOperatorExecutionType::D3D12**, *executionObject* будет поддерживать [ID3D12GraphicsCommandList](https://docs.microsoft.com/windows/desktop/api/d3d12/nn-d3d12-id3d12graphicscommandlist) интерфейс. Это может быть другой объект, не была предоставлена [IMLOperatorKernelCreationContext::GetExecutionInterface](IMLOperatorKernelCreationContext_GetExecutionInterface.md) при создании экземпляра ядра.

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
