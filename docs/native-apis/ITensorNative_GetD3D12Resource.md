---
author: eliotcowley
title: Метод ITensorNative.GetD3D12Resource
description: Получает буфер тензорные как ID3D12Resource.
ms.author: elcowle
ms.date: 11/8/2018
ms.topic: article
keywords: Windows 10, windows машинного обучения, WinML, GetD3D12Resource
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- ITensorNative.GetD3D12Resource
api_location:
- windows.ai.machinelearning.native.h
ms.openlocfilehash: 5c694e4ba199dc604534b88a5f60a91cb90d016a
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2019
ms.locfileid: "59475041"
---
# <a name="itensornativegetd3d12resource-method"></a>Метод ITensorNative.GetD3D12Resource

Получает буфер тензорные как [ID3D12Resource](https://docs.microsoft.com/windows/desktop/api/d3d12/nn-d3d12-id3d12resource).

```cpp
HRESULT GetD3D12Resource(
    [out] ID3D12Resource ** result);
```

## <a name="parameters"></a>Параметры

| Имя | Тип | Описание |
|------|------|-------------|
| результат | [ID3D12Resource](https://docs.microsoft.com/windows/desktop/api/d3d12/nn-d3d12-id3d12resource)** | Тензорные буфера в качестве **ID3D12Resource**. |

## <a name="returns"></a>Возвращает

**HRESULT** результат операции.

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальная версия клиента** | Windows 10, сборки 17763 |
| **Минимальная версия сервера** | Windows Server 2019 с возможностями рабочего стола |
| **Header** | Windows.AI.machinelearning.Native.h |

[!INCLUDE [help](../includes/get-help.md)]
