---
author: eliotcowley
title: Структура MLOperatorEdgeTypeConstraint
description: Задает ограничения по типам краев, поддерживается в пользовательского оператора ядра и схемы.
ms.author: elcowle
ms.date: 11/8/2018
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
ms.openlocfilehash: ccc3f7abed0be9b5a217c3172b3b02ae35197147
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474361"
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
| **Минимальная версия клиента** | Windows 10, сборки 17763 |
| **Минимальная версия сервера** | Windows Server 2019 с возможностями рабочего стола |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
