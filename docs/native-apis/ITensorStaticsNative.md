---
author: eliotcowley
title: Интерфейс ITensorStaticsNative
description: Предоставляет доступ к методам фабрики, позволяющие создавать ITensor объектов, с помощью ID3D12Resource.
ms.author: elcowle
ms.date: 11/8/2018
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
ms.openlocfilehash: 7c58025159e48f0cbaddccc45e9e86d97c054aa0
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2019
ms.locfileid: "59473841"
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
| **Минимальная версия клиента** | Windows 10, сборки 17763 |
| **Минимальная версия сервера** | Windows Server 2019 с возможностями рабочего стола |
| **Header** | Windows.AI.machinelearning.Native.h |

[!INCLUDE [help](../includes/get-help.md)]
