---
author: eliotcowley
title: Интерфейс IMLOperatorShapeInferenceContext
description: Предоставляет сведения об использовании оператора, хотя вызываются inferrers фигуры.
ms.author: elcowle
ms.date: 11/8/2018
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
ms.openlocfilehash: bf5a479c735d06d4609ad9841559dccaf8d0dd30
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474211"
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
| **Минимальная версия клиента** | Windows 10, сборки 17763 |
| **Минимальная версия сервера** | Windows Server 2019 с возможностями рабочего стола |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
