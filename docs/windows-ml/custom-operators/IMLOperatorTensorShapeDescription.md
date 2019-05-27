---
author: eliotcowley
title: Интерфейс IMLOperatorTensorShapeDescription
description: Представляет набор фигур входных и выходных тензорные оператора.
ms.author: elcowle
ms.date: 4/1/2019
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
ms.openlocfilehash: 1ec7c6f185b65b6920887570ce3758d1f21a3d0b
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66181666"
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
| **Минимальный поддерживаемый клиент** | Windows 10, сборки 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
