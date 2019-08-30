---
title: Интерфейс Итенсорстатикснативе
description: Предоставляет доступ к заводским методам, которые позволяют создавать объекты Итенсор с помощью ID3D12Resource.
ms.date: 4/2/2019
ms.topic: article
keywords: Windows 10, машинное обучение Windows, WinML, Итенсорстатикснативе
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- ITensorStaticsNative
api_location:
- windows.ai.machinelearning.native.h
ms.openlocfilehash: 1b828c1611535d4c5c41a1380b12664959b1dc28
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70156436"
---
# <a name="itensorstaticsnative-interface"></a>Интерфейс Итенсорстатикснативе

Предоставляет доступ к заводским методам, которые позволяют создавать объекты [итенсор](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.itensor) с помощью [ID3D12Resource](https://docs.microsoft.com/windows/desktop/api/d3d12/nn-d3d12-id3d12resource).

## <a name="methods"></a>Методы

| Имя | Описание |
|------|-------------|
| [CreateFromD3D12Resource](ITensorStaticsNative_CreateFromD3D12Resource.md) | Создает объект тензорные ([тенсорфлоат](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.tensorfloat), [TensorInt32Bit](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.tensorint32bit)) из указанного пользователем [ID3D12Resource](https://docs.microsoft.com/windows/desktop/api/d3d12/nn-d3d12-id3d12resource). |

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборка 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | Windows. AI. machinelearning. Native. h |

[!INCLUDE [help](../../includes/get-help.md)]
