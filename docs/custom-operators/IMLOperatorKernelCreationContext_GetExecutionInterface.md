---
author: eliotcowley
title: Метод IMLOperatorKernelCreationContext.GetExecutionInterface
description: Возвращает объект, различаются, поддерживаемые интерфейсы на основе ядра типа.
ms.author: elcowle
ms.date: 11/8/2018
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
ms.openlocfilehash: 3111f983491ff4effe09727bf5220a36f9498fd0
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474901"
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
| **Минимальная версия клиента** | Windows 10, сборки 17763 |
| **Минимальная версия сервера** | Windows Server 2019 с возможностями рабочего стола |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
