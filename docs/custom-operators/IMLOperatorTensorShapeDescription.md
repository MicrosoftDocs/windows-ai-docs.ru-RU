---
author: eliotcowley
title: Интерфейс IMLOperatorTensorShapeDescription
description: Представляет набор фигур входных и выходных тензорные оператора.
ms.author: elcowle
ms.date: 11/8/2018
ms.topic: article
keywords: Windows 10, windows машинного обучения, WinML, настраиваемые операторы, IMLOperatorTensorShapeDescription
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorTensorShapeDescription
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: f097e97ab9d79b48a44dcab5ae37696d3ed21c2e
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474281"
---
# <a name="imloperatortensorshapedescription-interface"></a>Интерфейс IMLOperatorTensorShapeDescription

Представляет набор фигур входных и выходных тензорные оператора. Этот интерфейс вызывает объекты фабрики, зарегистрированные для создания ядра. Он станет доступен в эти объекты фабрик, если соответствующий ядра они регистрируются с помощью [MLOperatorKernelOptions::AllowDynamicInputShapes](MLOperatorKernelOptions.md) флаг.

## <a name="methods"></a>Методы

| Имя | Описание |
|------|-------------|
| [GetInputTensorDimensionCount](IMLOperatorTensorShapeDescription_GetInputTensorDimensionCount.md) | Получает размерность тензорные ввода оператора. |
| [GetInputTensorShape](IMLOperatorTensorShapeDescription_GetInputTensorShape.md) | Возвращает размеры измерений из входного тензорные оператора. |
| [GetOutputTensorDimensionCount](IMLOperatorTensorShapeDescription_GetOutputTensorDimensionCount.md) | Получает размерность вывода тензорные оператора. |
| [GetOutputTensorShape](IMLOperatorTensorShapeDescription_GetOutputTensorShape.md) | Получает размеры измерениях тензорные выходных данных оператора. |
| [HasOutputShapeDescription](IMLOperatorTensorShapeDescription_HasOutputShapeDescription.md) | Возвращает значение true, если выходные данные фигуры может запрашиваться с помощью **GetOutputTensorDimensionCount** и **GetOutputTensorShape**. |

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальная версия клиента** | Windows 10, сборки 17763 |
| **Минимальная версия сервера** | Windows Server 2019 с возможностями рабочего стола |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
