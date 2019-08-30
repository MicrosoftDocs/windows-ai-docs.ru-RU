---
title: Имлоператоркернелконтекст. Аллокатетемпораридата, метод
description: 'Выделяет временные данные, которые будут использоваться в качестве промежуточной памяти для длительности вызова **имлоператоркернел:: COMPUTE**.'
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, машинное обучение Windows, WinML, пользовательские операторы, Аллокатетемпораридата
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorKernelContext.AllocateTemporaryData
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: ccc7e98f928ab77d7265c647165774e9fb74312a
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157247"
---
# <a name="imloperatorkernelcontextallocatetemporarydata-method"></a>Имлоператоркернелконтекст. Аллокатетемпораридата, метод

Выделяет временные данные, которые будут использоваться в качестве промежуточной памяти для длительности вызова [имлоператоркернел:: COMPUTE](IMLOperatorKernel_Compute.md). Это может быть использовано для ядер, зарегистрированных с помощью [млоператорексекутионтипе::D 3d12](MLOperatorExecutionType.md). Объект данных поддерживает интерфейс [ID3D12Resource](https://docs.microsoft.com/windows/desktop/api/d3d12/nn-d3d12-id3d12resource) , а — буфер GPU.

```cpp
void AllocateTemporaryData(
    size_t size,
    _COM_Outptr_ IUnknown** data)
```

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборка 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | Млоператораусор. h |

[!INCLUDE [help](../../includes/get-help.md)]
