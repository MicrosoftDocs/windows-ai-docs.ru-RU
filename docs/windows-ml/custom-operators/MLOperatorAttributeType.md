---
author: eliotcowley
title: Перечисление MLOperatorAttributeType
description: Указывает тип атрибута. Каждый тип атрибута соответствует числовом виде соответствующего типа ONNX.
ms.author: elcowle
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, windows машинного обучения, WinML, настраиваемые операторы, MLOperatorAttributeType
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- MLOperatorAttributeType
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 09e847c7ebfce894249ef06b778cdb5ec3039a79
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66182056"
---
# <a name="mloperatorattributetype-enum"></a>Перечисление MLOperatorAttributeType

Указывает тип атрибута. Каждый тип атрибута соответствует числовом виде соответствующего типа ONNX.

## <a name="fields"></a>Поля

| Имя        | Значение | Описание                            |
|-------------|-------|----------------------------------------|
| Не определено   | 0     | Не определено (неиспользуемого).                    |
| Плавающий       | 2     | 32-разрядное число с плавающей запятой.                 |
| int         | 3     | 64-разрядное целое число.                        |
| Строка      | 4     | Строковое значение.                          |
| FloatArray  | 7     | Массив 32-разрядных значений с плавающей запятой. |
| IntArray    | 8     | Массив 64-разрядных целых значений.        |
| StringArray | 9     | Массив строковых значений.                |

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборки 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
