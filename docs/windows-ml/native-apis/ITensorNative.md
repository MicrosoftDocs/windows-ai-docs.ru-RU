---
title: Интерфейс Итенсорнативе
description: Предоставляет доступ к Итенсор в виде массива объектов Byte или ID3D12Resource.
ms.date: 4/2/2019
ms.topic: article
keywords: Windows 10, машинное обучение Windows, WinML, Итенсорнативе
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- ITensorNative
api_location:
- windows.ai.machinelearning.native.h
ms.openlocfilehash: 9432f01613522bc2564eb9525c5b5943f9b464d4
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157971"
---
# <a name="itensornative-interface"></a>Интерфейс Итенсорнативе

Предоставляет доступ к [итенсор](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.itensor) в виде массива объектов Byte или [ID3D12Resource](https://docs.microsoft.com/windows/desktop/api/d3d12/nn-d3d12-id3d12resource) .

## <a name="methods"></a>Методы

| Имя | Описание |
|------|-------------|
| [GetBuffer](ITensorNative_GetBuffer.md) | Возвращает буфер тензорные в виде массива байтов. |
| [GetD3D12Resource](ITensorNative_GetD3D12Resource.md) | Возвращает буфер тензорные как [ID3D12Resource](https://docs.microsoft.com/windows/desktop/api/d3d12/nn-d3d12-id3d12resource). |

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборка 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | Windows. AI. machinelearning. Native. h |

[!INCLUDE [help](../../includes/get-help.md)]
