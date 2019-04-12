---
author: eliotcowley
title: Интерфейс IMLOperatorTypeInferenceContext
description: Предоставляет сведения об использовании оператора, хотя вызываются inferrers типа.
ms.author: elcowle
ms.date: 11/8/2018
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
ms.openlocfilehash: 5b351018b5e4506017ead09c1553958468aed204
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474061"
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
| **Минимальная версия клиента** | Windows 10, сборки 17763 |
| **Минимальная версия сервера** | Windows Server 2019 с возможностями рабочего стола |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
