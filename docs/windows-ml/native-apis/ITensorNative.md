---
author: eliotcowley
title: Интерфейс ITensorNative
description: Предоставляет доступ к ITensor как массив байтов или ID3D12Resource объектов.
ms.author: elcowle
ms.date: 4/2/2019
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
ms.openlocfilehash: 2427a5916244e72b19c95a78d1b02ee425c357db
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66180136"
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
| **Минимальный поддерживаемый клиент** | Windows 10, сборки 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | Windows.AI.machinelearning.Native.h |

[!INCLUDE [help](../../includes/get-help.md)]
