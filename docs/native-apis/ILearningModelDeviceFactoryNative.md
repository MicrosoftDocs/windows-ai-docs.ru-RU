---
author: eliotcowley
title: Интерфейс ILearningModelDeviceFactoryNative
description: Предоставляет доступ к методам фабрики, позволяющие создавать ILearningModelDevice объектов, с помощью ID3D12CommandQueue.
ms.author: elcowle
ms.date: 11/8/2018
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
ms.openlocfilehash: 2779415326f2e74ff96c73141a38fa0a90e43fd3
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2019
ms.locfileid: "59475071"
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
| **Минимальная версия клиента** | Windows 10, сборки 17763 |
| **Минимальная версия сервера** | Windows Server 2019 с возможностями рабочего стола |
| **Header** | Windows.AI.machinelearning.Native.h |

[!INCLUDE [help](../includes/get-help.md)]
