---
author: eliotcowley
title: Перечисление MLOperatorTensorDataType
description: Указывает тип данных тензорные. Каждый тип данных соответствует числовом виде соответствующего типа ONNX.
ms.author: elcowle
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, windows машинного обучения, WinML, настраиваемые операторы, MLOperatorTensorDataType
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- MLOperatorTensorDataType
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: ee7a8ecd9af0b5b67f57cbb7d09b8517d583829b
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66181276"
---
# <a name="mloperatortensordatatype-enum"></a>Перечисление MLOperatorTensorDataType

Указывает тип данных тензорные. Каждый тип данных соответствует числовом виде соответствующего типа ONNX.

## <a name="fields"></a>Поля

| Имя       | Значение | Описание                             |
|------------|-------|-----------------------------------------|
| Не определено  | 0     | Не определено (неиспользуемого).                     |
| Плавающий      | 1     | 32-разрядное число с плавающей запятой IEEE.             |
| UInt8      | 2     | 8-разрядное целое число без знака.                 |
| Int8       | 3     | 8-разрядное знаковое целое число.                   |
| UInt16     | 4     | 16-разрядное целое число без знака.                |
| Int16      | 5     | 16-разрядное знаковое целое число.                  |
| Int32      | 6     | 32-разрядное знаковое целое число.                  |
| Int64      | 7     | 64-разрядное знаковое целое число.                  |
| Строка     | 8     | Строка (не поддерживается).                   |
| Bool       | 9     | 8-битовое логическое значение. Значения, отличные от них приводят к неопределенному поведению. |
| Float16    | 10    | 16-разрядное число с плавающей запятой IEEE.             |
| Double     | 11    | 64-разрядное число с плавающей запятой двойной точности. |
| UInt32     | 12    | 32-разрядное целое число без знака.                |
| UInt64     | 13    | 64-разрядного целого числа без знака.                |
| Complex64  | 14    | 64-разрядных сложный тип (не поддерживается).      |
| Complex128 | 15    | Сложный тип, 128 бит (не поддерживается).     |

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборки 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
