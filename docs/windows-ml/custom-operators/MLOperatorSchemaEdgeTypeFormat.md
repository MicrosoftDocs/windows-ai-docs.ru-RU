---
author: eliotcowley
title: Перечисление MLOperatorSchemaEdgeTypeFormat
description: Указывает способ, в какие типы входных и выходных данных описаны краев.
ms.author: elcowle
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, windows машинного обучения, WinML, настраиваемые операторы, MLOperatorSchemaEdgeTypeFormat
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- MLOperatorSchemaEdgeTypeFormat
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 736ce313193b722ac0d42b2c35c3aae0c45abc33
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66181326"
---
# <a name="mloperatorschemaedgetypeformat-enum"></a>Перечисление MLOperatorSchemaEdgeTypeFormat

Указывает способ, в какие типы входных и выходных данных описаны краев. Это используется в [MLOperatorSchemaEdgeDescription](MLOperatorSchemaEdgeDescription.md) при определении схемы пользовательского оператора.

## <a name="fields"></a>Поля

| Имя | Значение | Описание |
|------|-------|-------------|
| edgeDescription | 0 | Этот тип определен с помощью [MLOperatorEdgeDescription](MLOperatorEdgeDescription.md). |
| Метка | 1 | Тип определяется строковый тип, созданный как в схеме оператор ONNX. |

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборки 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
