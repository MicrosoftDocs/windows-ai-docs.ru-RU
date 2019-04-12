---
author: eliotcowley
title: Метод IMLOperatorKernelContext.AllocateTemporaryData
description: Выделяет временных данных, который будет использоваться в качестве промежуточных памяти в течение всего вызова **IMLOperatorKernel::Compute**.
ms.author: elcowle
ms.date: 11/8/2018
ms.topic: article
keywords: Windows 10, windows машинного обучения, WinML, настраиваемые операторы, AllocateTemporaryData
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorKernelContext.AllocateTemporaryData
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: b0b6668f89c8c5afb15d714d7ebbc3a5be679280
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474811"
---
# <a name="imloperatorkernelcontextallocatetemporarydata-method"></a>Метод IMLOperatorKernelContext.AllocateTemporaryData

Выделяет временных данных, который будет использоваться в качестве промежуточных памяти в течение всего вызова [IMLOperatorKernel::Compute](IMLOperatorKernel_Compute.md). Это может пригодиться ядра, зарегистрированный при помощи [MLOperatorExecutionType::D3D12](MLOperatorExecutionType.md). Объект данных поддерживает [ID3D12Resource](https://docs.microsoft.com/windows/desktop/api/d3d12/nn-d3d12-id3d12resource) интерфейс, и является буфером GPU.

```cpp
void AllocateTemporaryData(
    size_t size, 
    _COM_Outptr_ IUnknown** data)
```

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальная версия клиента** | Windows 10, сборки 17763 |
| **Минимальная версия сервера** | Windows Server 2019 с возможностями рабочего стола |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
