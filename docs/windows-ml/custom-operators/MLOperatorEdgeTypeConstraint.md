---
author: eliotcowley
title: Структура MLOperatorEdgeTypeConstraint
description: Задает ограничения по типам краев, поддерживается в пользовательского оператора ядра и схемы.
ms.author: elcowle
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, windows машинного обучения, WinML, настраиваемые операторы, MLOperatorEdgeTypeConstraint
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- MLOperatorEdgeTypeConstraint
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: bb9e1e948ab3ed5373c24e4ec4ceb7724cd9e74c
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66181396"
---
# <a name="mloperatoredgetypeconstraint-struct"></a>Структура MLOperatorEdgeTypeConstraint

Задает ограничения по типам краев, поддерживается в пользовательского оператора ядра и схемы. Введите метки в спецификации ONNX для тот же оператор соответствует строке метки предоставленного типа. Для настраиваемой схемы, он соответствует введите метки, указанные в [MLOperatorSchemaEdgeDescription](MLOperatorSchemaEdgeDescription.md) при регистрации схемы оператора.

## <a name="fields"></a>Поля

| Имя | Тип | Описание |
|------|------|-------------|
| allowedTypeCount | **uint32_t** | |
| allowedTypes | [MLOperatorEdgeDescription](MLOperatorEdgeDescription.md)* | Набор допустимых типов для ограничения. |
| typeLabel | **Char*** | Метка типа, для которого определено ограничение. Это создается как в схеме оператор ONNX. Например, «T». |

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборки 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
