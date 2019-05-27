---
author: eliotcowley
title: Метод IMLOperatorKernelContext.AllocateTemporaryData
description: Выделяет временных данных, который будет использоваться в качестве промежуточных памяти в течение всего вызова **IMLOperatorKernel::Compute**.
ms.author: elcowle
ms.date: 4/1/2019
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
ms.openlocfilehash: 0c1ffe8d50052e37e109f869346228031c35bb36
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66180676"
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
| **Минимальный поддерживаемый клиент** | Windows 10, сборки 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
