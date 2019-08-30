---
title: Структура Млоператореджетипеконстраинт
description: Задает ограничения для типов краев, поддерживаемых в ядрах и схемах пользовательских операторов.
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, машинное обучение Windows, WinML, пользовательские операторы, Млоператореджетипеконстраинт
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- MLOperatorEdgeTypeConstraint
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: d2f1b6132f744eece3d25e0cb9732e7c196ee2cf
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157730"
---
# <a name="mloperatoredgetypeconstraint-struct"></a>Структура Млоператореджетипеконстраинт

Задает ограничения для типов краев, поддерживаемых в ядрах и схемах пользовательских операторов. Указанная строка метки типа соответствует меткам типа в спецификации ONNX для одного и того же оператора. Для пользовательской схемы она соответствует меткам типа, заданной в [млоператорсчемаеджедескриптион](MLOperatorSchemaEdgeDescription.md) при регистрации схемы оператора.

## <a name="fields"></a>Поля

| Имя | Тип | Описание |
|------|------|-------------|
| алловедтипекаунт | **uint32_t** | |
| алловедтипес | [млоператореджедескриптион](MLOperatorEdgeDescription.md)* | Набор разрешенных типов для ограничения. |
| типелабел | **типа*** | Метка типа, для которого определяется ограничение. Он создается как схема оператора ONNX. Например, "T". |

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборка 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | Млоператораусор. h |

[!INCLUDE [help](../../includes/get-help.md)]
