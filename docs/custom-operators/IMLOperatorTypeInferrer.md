---
author: eliotcowley
title: Интерфейс IMLOperatorTypeInferrer
description: Реализованный тип inferrers определить типы оператора выходных краев.
ms.author: elcowle
ms.date: 11/8/2018
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
ms.openlocfilehash: 70fe73eecb38e41be5a73e34a3fbf6390aecf99f
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474551"
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
| **Минимальная версия клиента** | Windows 10, сборки 17763 |
| **Минимальная версия сервера** | Windows Server 2019 с возможностями рабочего стола |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
