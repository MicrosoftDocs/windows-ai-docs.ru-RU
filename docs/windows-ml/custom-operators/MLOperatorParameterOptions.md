---
title: Перечисление Млоператорпараметероптионс
description: Задает флаги параметров входных и выходных границ операторов.
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, машинное обучение Windows, WinML, пользовательские операторы, Млоператорпараметероптионс
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- MLOperatorParameterOptions
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 15bfeb20412bc1e9ee3db032fe26fb1d86ab2dc5
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157707"
---
# <a name="mloperatorparameteroptions-enum"></a>Перечисление Млоператорпараметероптионс

Задает флаги параметров входных и выходных границ операторов. Эти параметры используются при определении пользовательской схемы оператора.

## <a name="fields"></a>Поля

| Имя | Значение | Описание |
|------|-------|-------------|
| Single | 0 | Существует один экземпляр входных или выходных данных. |
| Необязательный | 1 | Входные или выходные данные могут быть опущены. |
| Variadic | 2 | Число экземпляров оператора — переменная. Параметры Variadic должны быть последними в наборе входных или выходных данных. |

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборка 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | Млоператораусор. h |

[!INCLUDE [help](../../includes/get-help.md)]
