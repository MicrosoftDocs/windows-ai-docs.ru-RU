---
author: eliotcowley
title: Интерфейс ITensorStaticsNative
description: Предоставляет доступ к методам фабрики, позволяющие создавать ITensor объектов, с помощью ID3D12Resource.
ms.author: elcowle
ms.date: 4/2/2019
ms.topic: article
keywords: Windows 10, windows машинного обучения, WinML, ITensorStaticsNative
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- ITensorStaticsNative
api_location:
- windows.ai.machinelearning.native.h
ms.openlocfilehash: b10f44d7f43d62434dd4adbf770659b58088c6ad
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66180096"
---
# <a name="itensorstaticsnative-interface"></a>Интерфейс ITensorStaticsNative

Предоставляет доступ к методам фабрики, которые обеспечивают создание [ITensor](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.itensor) объектов с помощью [ID3D12Resource](https://docs.microsoft.com/windows/desktop/api/d3d12/nn-d3d12-id3d12resource).

## <a name="methods"></a>Методы

| Имя | Описание |
|------|-------------|
| [CreateFromD3D12Resource](ITensorStaticsNative_CreateFromD3D12Resource.md) | Создает объект тензорные ([TensorFloat](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.tensorfloat), [TensorInt32Bit](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.tensorint32bit)) из указанного [ID3D12Resource](https://docs.microsoft.com/windows/desktop/api/d3d12/nn-d3d12-id3d12resource). |

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборки 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | Windows.AI.machinelearning.Native.h |

[!INCLUDE [help](../../includes/get-help.md)]
