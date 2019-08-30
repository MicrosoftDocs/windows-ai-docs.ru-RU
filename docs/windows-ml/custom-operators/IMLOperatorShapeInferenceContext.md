---
title: Интерфейс Имлоператоршапеинференцеконтекст
description: Предоставляет сведения об использовании оператора во время вызова ссылок на фигурные источники.
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, машинное обучение Windows, WinML, пользовательские операторы, Имлоператоршапеинференцеконтекст
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorShapeInferenceContext
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 4d8d9ac610c7285a560e76ac87ae9622afc43f53
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157018"
---
# <a name="imloperatorshapeinferencecontext-interface"></a>Интерфейс Имлоператоршапеинференцеконтекст

Предоставляет сведения об использовании оператора во время вызова ссылок на фигурные источники.

## <a name="methods"></a>Методы

| Имя | Описание |
|------|-------------|
| [GetInputCount](IMLOperatorShapeInferenceContext_GetInputCount.md) | Возвращает число входов для оператора. |
| [GetInputEdgeDescription](IMLOperatorShapeInferenceContext_GetInputEdgeDescription.md) | Возвращает описание указанной входной границы оператора. |
| [GetInputTensorDimensionCount](IMLOperatorShapeInferenceContext_GetInputTensorDimensionCount.md) | Возвращает число измерений тензорные выходных данных оператора. |
| [GetInputTensorShape](IMLOperatorShapeInferenceContext_GetInputTensorShape.md) | Возвращает размеры измерений входного тензорные оператора. |
| [GetOutputCount](IMLOperatorShapeInferenceContext_GetOutputCount.md) | Возвращает число выходов для оператора. |
| [IsInputValid](IMLOperatorShapeInferenceContext_IsInputValid.md) | Возвращает значение true, если входные данные оператора являются допустимыми. |
| [IsOutputValid](IMLOperatorShapeInferenceContext_IsOutputValid.md) | Возвращает значение true, если выходные данные оператора являются допустимыми. |
| [SetOutputTensorShape](IMLOperatorShapeInferenceContext_SetOutputTensorShape.md) | Задает выводимую форму выходного тензорные. |

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборка 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | Млоператораусор. h |

[!INCLUDE [help](../../includes/get-help.md)]
