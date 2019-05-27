---
author: eliotcowley
title: Структура MLOperatorSchemaEdgeDescription
description: Указывает сведения о ребро входного или выходного оператора.
ms.author: elcowle
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, windows машинного обучения, WinML, настраиваемые операторы, MLOperatorSchemaEdgeDescription
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- MLOperatorSchemaEdgeDescription
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 82566b25ae7d3f446b4e53a4d0c3d619f21732ca
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66181336"
---
# <a name="mloperatorschemaedgedescription-struct"></a>Структура MLOperatorSchemaEdgeDescription

Указывает сведения о ребро входного или выходного оператора. Это используется при определении схемы пользовательского оператора.

## <a name="fields"></a>Поля

| Имя | Тип | Описание |
|------|------|-------------|
| edgeDescription | [MLOperatorEdgeDescription](MLOperatorEdgeDescription.md) | Поддержка структура описания типа. Это используется при **typeFormat** — **MLOperatorSchemaEdgeTypeFormat::EdgeDescription**. |
| параметры | [MLOperatorParameterOptions](MLOperatorParameterOptions.md) | Параметры с переменным числом аргументов или параметр, включая ли он является необязательным. |
| Зарезервировано | **void*** | |
| typeFormat | [MLOperatorSchemaEdgeTypeFormat](MLOperatorSchemaEdgeTypeFormat.md) | Так, в котором определены ограничения типов и сопоставления типов. |
| typeLabel | **Char*** | Метка типа строка создан как в схеме оператор ONNX. Например, «T». Это используется при **typeFormat** — **MLOperatorSchemaEdgeTypeFormat::Label**. |

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборки 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
