---
author: eliotcowley
title: Интерфейс IMLOperatorTypeInferenceContext
description: Предоставляет сведения об использовании оператора, хотя вызываются inferrers типа.
ms.author: elcowle
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, windows машинного обучения, WinML, настраиваемые операторы, IMLOperatorTypeInferenceContext
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorTypeInferenceContext
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 7af793410357500436142c987b1d3010a6f9b2e4
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66180286"
---
# <a name="imloperatortypeinferencecontext-interface"></a>Интерфейс IMLOperatorTypeInferenceContext

Предоставляет сведения об использовании оператора, хотя вызываются inferrers типа.

## <a name="methods"></a>Методы

| Имя | Описание |
|------|-------------|
| [GetInputCount](IMLOperatorTypeInferenceContext_GetInputCount.md) | Получает количество входных данных для оператора. |
| [GetInputEdgeDescription](IMLOperatorTypeInferenceContext_GetInputEdgeDescription.md) | Возвращает описание указанного входного края оператора. |
| [GetOutputCount](IMLOperatorTypeInferenceContext_GetOutputCount.md) | Получает количество выходов оператору. |
| [IsInputValid](IMLOperatorTypeInferenceContext_IsInputValid.md) | Возвращает значение true, если входными данными для оператора является допустимым. |
| [IsOutputValid](IMLOperatorTypeInferenceContext_IsOutputValid.md) | Возвращает значение true, если выходные данные оператора является допустимым. |
| [SetOutputEdgeDescription](IMLOperatorTypeInferenceContext_SetOutputEdgeDescription.md) | Задает выведенный тип ребро выходных данных. |

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборки 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
