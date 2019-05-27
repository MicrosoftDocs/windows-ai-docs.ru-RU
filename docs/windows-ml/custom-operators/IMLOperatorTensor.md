---
author: eliotcowley
title: Интерфейс IMLOperatorTensor
description: Представление тензорные, используемых при вычислениях ядер пользовательского оператора.
ms.author: elcowle
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, windows машинного обучения, WinML, настраиваемые операторы, IMLOperatorTensor
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorTensor
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: a26cd2eb5a1a4be45ff7077c265c972258bbf60d
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66181656"
---
# <a name="imloperatortensor-interface"></a>Интерфейс IMLOperatorTensor

Представление тензорные, используемых при вычислениях ядер пользовательского оператора.

## <a name="methods"></a>Методы

| Имя | Описание |
|------|-------------|
| [GetData](IMLOperatorTensor_GetData.md) | Возвращает указатель на память байтовой адресацией для тензорные. |
| [GetDataInterface](IMLOperatorTensor_GetDataInterface.md) | Возвращает указатель интерфейса для тензорные. |
| [GetDimensionCount](IMLOperatorTensor_GetDimensionCount.md) | Получает число измерений в тензорные. |
| [GetShape](IMLOperatorTensor_GetShape.md) | Получает размер измерений в тензорные. |
| [GetTensorDataType](IMLOperatorTensor_GetTensorDataType.md) | Возвращает тип данных тензорные. |
| [IsCpuData](IMLOperatorTensor_IsCpuData.md) | Указывает, является ли память, занятая тензорные ЦП адресацию. |
| [IsDataInterface](IMLOperatorTensor_IsDataInterface.md) | Ли содержимое тензорные представлены тип интерфейса или байтовой адресацией памяти. |

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборки 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
