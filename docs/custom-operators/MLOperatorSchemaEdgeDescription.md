---
author: eliotcowley
title: Структура MLOperatorSchemaEdgeDescription
description: Указывает сведения о ребро входного или выходного оператора.
ms.author: elcowle
ms.date: 11/8/2018
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
ms.openlocfilehash: 28bcd8fff05f99cfaa007ea57b9b17674ba2c3f3
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474411"
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
| **Минимальная версия клиента** | Windows 10, сборки 17763 |
| **Минимальная версия сервера** | Windows Server 2019 с возможностями рабочего стола |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
