---
author: eliotcowley
title: Интерфейс IMLOperatorTypeInferrer
description: Реализованный тип inferrers определить типы оператора выходных краев.
ms.author: elcowle
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, windows машинного обучения, WinML, настраиваемые операторы, IMLOperatorTypeInferrer
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorTypeInferrer
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: dd979f3a40b5b9f921a14a3a8acf70386591e4ee
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66182116"
---
# <a name="imloperatortypeinferrer-interface"></a>Интерфейс IMLOperatorTypeInferrer

Реализованный тип inferrers определить типы оператора выходных краев. Inferrers тип должен быть указан при регистрации схемы пользовательские операторы, если [MLOperatorSchemaDescription](MLOperatorSchemaDescription.md) структура не может представлять, как определяются типы выходных данных&mdash;например, когда атрибут оператор определяет тип данных одного из выходных данных этого оператора.

## <a name="methods"></a>Методы

| Имя | Описание |
|------|-------------|
| [InferOutputTypes](IMLOperatorTypeInferrer_InferOutputTypes.md) | Вызывается, чтобы вывести типы границ выходные данные оператора. |

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборки 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
