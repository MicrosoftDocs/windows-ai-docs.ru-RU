---
author: eliotcowley
title: Интерфейс ILearningModelDeviceFactoryNative
description: Предоставляет доступ к методам фабрики, позволяющие создавать ILearningModelDevice объектов, с помощью ID3D12CommandQueue.
ms.author: elcowle
ms.date: 4/2/2019
ms.topic: article
keywords: Windows 10, windows машинного обучения, WinML, ILearningModelDeviceFactoryNative
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- ILearningModelDeviceFactoryNative
api_location:
- windows.ai.machinelearning.native.h
ms.openlocfilehash: 035ff6dd7e765dcf1f2f21382eb6c488bdb66f63
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66181876"
---
# <a name="ilearningmodeldevicefactorynative-interface"></a>Интерфейс ILearningModelDeviceFactoryNative

Предоставляет доступ к методам фабрики, которые обеспечивают создание [ILearningModelDevice](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodeldevice) объектов с помощью [ID3D12CommandQueue](https://docs.microsoft.com/windows/desktop/api/d3d12/nn-d3d12-id3d12commandqueue).

## <a name="methods"></a>Методы

| Имя | Описание |
|------|-------------|
| [CreateFromD3D12CommandQueue](ILearningModelDeviceFactoryNative_CreateFromD3D12CommandQueue.md) | Создает [LearningModelDevice](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodeldevice) вывода, которые будут работать на определяемый пользователем [ID3D12CommandQueue](https://docs.microsoft.com/windows/desktop/api/d3d12/nn-d3d12-id3d12commandqueue). |

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборки 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | Windows.AI.machinelearning.Native.h |

[!INCLUDE [help](../../includes/get-help.md)]
