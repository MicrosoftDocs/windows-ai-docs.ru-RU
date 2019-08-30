---
title: Итенсорнативе. GetD3D12Resource, метод
description: Возвращает буфер тензорные как ID3D12Resource.
ms.date: 4/2/2019
ms.topic: article
keywords: Windows 10, машинное обучение Windows, WinML, GetD3D12Resource
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- ITensorNative.GetD3D12Resource
api_location:
- windows.ai.machinelearning.native.h
ms.openlocfilehash: 9384311d5060df0cf0e4542fd202bdd20cfb73e0
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70156462"
---
# <a name="itensornativegetd3d12resource-method"></a>Итенсорнативе. GetD3D12Resource, метод

Возвращает буфер тензорные как [ID3D12Resource](https://docs.microsoft.com/windows/desktop/api/d3d12/nn-d3d12-id3d12resource).

```cpp
HRESULT GetD3D12Resource(
    [out] ID3D12Resource ** result);
```

## <a name="parameters"></a>Параметры

| Имя | Тип | Описание |
|------|------|-------------|
| результат | [ID3D12Resource](https://docs.microsoft.com/windows/desktop/api/d3d12/nn-d3d12-id3d12resource)** | Буфер тензорные как **ID3D12Resource**. |

## <a name="returns"></a>Возвращает

**Значение HRESULT** Результат операции.

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборка 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | Windows. AI. machinelearning. Native. h |

[!INCLUDE [help](../../includes/get-help.md)]
