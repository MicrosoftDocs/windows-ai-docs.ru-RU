---
title: Интерфейс Имлоператортенсор
description: Представление тензорные, используемое при вычислении ядер пользовательских операторов.
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, машинное обучение Windows, WinML, пользовательские операторы, Имлоператортенсор
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorTensor
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: c5cda4b43175cb78372abc1211083ab9d3232a00
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157785"
---
# <a name="imloperatortensor-interface"></a>Интерфейс Имлоператортенсор

Представление тензорные, используемое при вычислении ядер пользовательских операторов.

## <a name="methods"></a>Методы

| Имя | Описание |
|------|-------------|
| [GetData](IMLOperatorTensor_GetData.md) | Возвращает указатель на память с адресацией по байтам для тензорные. |
| [GetDataInterface](IMLOperatorTensor_GetDataInterface.md) | Возвращает указатель интерфейса для тензорные. |
| [GetDimensionCount](IMLOperatorTensor_GetDimensionCount.md) | Возвращает количество измерений в тензорные. |
| [GetShape](IMLOperatorTensor_GetShape.md) | Возвращает размер измерений в тензорные. |
| [GetTensorDataType](IMLOperatorTensor_GetTensorDataType.md) | Возвращает тип данных тензорные. |
| [IsCpuData](IMLOperatorTensor_IsCpuData.md) | Указывает, является ли память, используемая тензорные, поддерживаемой ЦП. |
| [IsDataInterface](IMLOperatorTensor_IsDataInterface.md) | Представляет ли содержимое тензорные тип интерфейса или память с адресацией по байтам. |

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборка 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | Млоператораусор. h |

[!INCLUDE [help](../../includes/get-help.md)]
