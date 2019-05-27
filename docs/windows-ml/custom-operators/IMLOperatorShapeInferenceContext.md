---
author: eliotcowley
title: Интерфейс IMLOperatorShapeInferenceContext
description: Предоставляет сведения об использовании оператора, хотя вызываются inferrers фигуры.
ms.author: elcowle
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, windows машинного обучения, WinML, настраиваемые операторы, IMLOperatorShapeInferenceContext
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorShapeInferenceContext
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 1c7734348c598f857379444d0f4188ba3753e0a0
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66180636"
---
# <a name="imloperatorshapeinferencecontext-interface"></a>Интерфейс IMLOperatorShapeInferenceContext

Предоставляет сведения об использовании оператора, хотя вызываются inferrers фигуры.

## <a name="methods"></a>Методы

| Имя | Описание |
|------|-------------|
| [GetInputCount](IMLOperatorShapeInferenceContext_GetInputCount.md) | Получает количество входных данных для оператора. |
| [GetInputEdgeDescription](IMLOperatorShapeInferenceContext_GetInputEdgeDescription.md) | Возвращает описание указанного входного края оператора. |
| [GetInputTensorDimensionCount](IMLOperatorShapeInferenceContext_GetInputTensorDimensionCount.md) | Получает размерность вывода тензорные оператора. |
| [GetInputTensorShape](IMLOperatorShapeInferenceContext_GetInputTensorShape.md) | Возвращает размеры измерений из входного тензорные оператора. |
| [GetOutputCount](IMLOperatorShapeInferenceContext_GetOutputCount.md) | Получает количество выходов оператору. |
| [IsInputValid](IMLOperatorShapeInferenceContext_IsInputValid.md) | Возвращает значение true, если входными данными для оператора является допустимым. |
| [IsOutputValid](IMLOperatorShapeInferenceContext_IsOutputValid.md) | Возвращает значение true, если выходные данные оператора является допустимым. |
| [SetOutputTensorShape](IMLOperatorShapeInferenceContext_SetOutputTensorShape.md) | Задает выводимый форму тензорные выходных данных. |

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборки 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
