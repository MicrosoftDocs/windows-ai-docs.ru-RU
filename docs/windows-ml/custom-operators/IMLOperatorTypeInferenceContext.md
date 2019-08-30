---
title: Интерфейс Имлоператортипеинференцеконтекст
description: Предоставляет сведения об использовании оператора во время вызова источников ссылок типов.
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, машинное обучение Windows, WinML, пользовательские операторы, Имлоператортипеинференцеконтекст
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorTypeInferenceContext
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 43eadcd6deb99e3f525788ceb9b5f2598d6da863
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157905"
---
# <a name="imloperatortypeinferencecontext-interface"></a>Интерфейс Имлоператортипеинференцеконтекст

Предоставляет сведения об использовании оператора во время вызова источников ссылок типов.

## <a name="methods"></a>Методы

| Имя | Описание |
|------|-------------|
| [GetInputCount](IMLOperatorTypeInferenceContext_GetInputCount.md) | Возвращает число входов для оператора. |
| [GetInputEdgeDescription](IMLOperatorTypeInferenceContext_GetInputEdgeDescription.md) | Возвращает описание указанной входной границы оператора. |
| [GetOutputCount](IMLOperatorTypeInferenceContext_GetOutputCount.md) | Возвращает число выходов для оператора. |
| [IsInputValid](IMLOperatorTypeInferenceContext_IsInputValid.md) | Возвращает значение true, если входные данные оператора являются допустимыми. |
| [IsOutputValid](IMLOperatorTypeInferenceContext_IsOutputValid.md) | Возвращает значение true, если выходные данные оператора являются допустимыми. |
| [SetOutputEdgeDescription](IMLOperatorTypeInferenceContext_SetOutputEdgeDescription.md) | Задает выводимый тип выходного края. |

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборка 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | Млоператораусор. h |

[!INCLUDE [help](../../includes/get-help.md)]
