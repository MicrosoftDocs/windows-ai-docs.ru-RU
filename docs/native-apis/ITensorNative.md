---
author: eliotcowley
title: Интерфейс ITensorNative
description: Предоставляет доступ к ITensor как массив байтов или ID3D12Resource объектов.
ms.author: elcowle
ms.date: 11/8/2018
ms.topic: article
keywords: Windows 10, windows машинного обучения, WinML, ITensorNative
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- ITensorNative
api_location:
- windows.ai.machinelearning.native.h
ms.openlocfilehash: cb64322047641d1dba4743605535dca4876b225f
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474121"
---
# <a name="itensornative-interface"></a>Интерфейс ITensorNative

Предоставляет доступ к [ITensor](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.itensor) как массив байтов или [ID3D12Resource](https://docs.microsoft.com/windows/desktop/api/d3d12/nn-d3d12-id3d12resource) объектов.

## <a name="methods"></a>Методы

| Имя | Описание |
|------|-------------|
| [GetBuffer](ITensorNative_GetBuffer.md) | Получает тензорные буфер в виде массива байтов. |
| [GetD3D12Resource](ITensorNative_GetD3D12Resource.md) | Получает буфер тензорные как [ID3D12Resource](https://docs.microsoft.com/windows/desktop/api/d3d12/nn-d3d12-id3d12resource). |

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальная версия клиента** | Windows 10, сборки 17763 |
| **Минимальная версия сервера** | Windows Server 2019 с возможностями рабочего стола |
| **Header** | Windows.AI.machinelearning.Native.h |

[!INCLUDE [help](../includes/get-help.md)]
