---
title: Интерфейс Илеарнингмоделдевицефакторинативе
description: Предоставляет доступ к заводским методам, которые позволяют создавать объекты Илеарнингмоделдевице с помощью ID3D12CommandQueue.
ms.date: 4/2/2019
ms.topic: article
keywords: Windows 10, машинное обучение Windows, WinML, Илеарнингмоделдевицефакторинативе
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- ILearningModelDeviceFactoryNative
api_location:
- windows.ai.machinelearning.native.h
ms.openlocfilehash: 0f6fdf7a32c768690a47dc3028b8a01adffce056
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70156577"
---
# <a name="ilearningmodeldevicefactorynative-interface"></a>Интерфейс Илеарнингмоделдевицефакторинативе

Предоставляет доступ к заводским методам, которые позволяют создавать объекты [илеарнингмоделдевице](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodeldevice) с помощью [ID3D12CommandQueue](https://docs.microsoft.com/windows/desktop/api/d3d12/nn-d3d12-id3d12commandqueue).

## <a name="methods"></a>Методы

| Имя | Описание |
|------|-------------|
| [CreateFromD3D12CommandQueue](ILearningModelDeviceFactoryNative_CreateFromD3D12CommandQueue.md) | Создает [леарнингмоделдевице](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodeldevice) , который будет выполнять вывод на заданном пользователем [ID3D12CommandQueue](https://docs.microsoft.com/windows/desktop/api/d3d12/nn-d3d12-id3d12commandqueue). |

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборка 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | Windows. AI. machinelearning. Native. h |

[!INCLUDE [help](../../includes/get-help.md)]
