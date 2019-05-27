---
author: eliotcowley
title: MLOperatorParameterOptions enum
description: Указывает флаги параметров, входных и выходных границ операторов.
ms.author: elcowle
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, windows машинного обучения, WinML, настраиваемые операторы, MLOperatorParameterOptions
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- MLOperatorParameterOptions
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: e348d8a41d1c940f396474844db296f8e1ad323b
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66181356"
---
# <a name="mloperatorparameteroptions-enum"></a>MLOperatorParameterOptions enum

Указывает флаги параметров, входных и выходных границ операторов. Эти параметры используются при определении схемы пользовательского оператора.

## <a name="fields"></a>Поля

| Имя | Значение | Описание |
|------|-------|-------------|
| Единый | 0 | Имеется один экземпляр входных или выходных параметров. |
| Необязательный | 1 | Входные или выходные данные можно опустить. |
| С переменным числом аргументов | 2 | Число экземпляров от оператора — переменная. Параметры с переменным числом аргументов должен быть последним среди набора входных и выходных данных. |

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборки 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
