---
author: eliotcowley
title: Интерфейс IMLOperatorTensor
description: Представление тензорные, используемых при вычислениях ядер пользовательского оператора.
ms.author: elcowle
ms.date: 11/8/2018
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
ms.openlocfilehash: e8058a31a86ac71724b1bee887049553bd418134
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474201"
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
| **Минимальная версия клиента** | Windows 10, сборки 17763 |
| **Минимальная версия сервера** | Windows Server 2019 с возможностями рабочего стола |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
