---
author: eliotcowley
title: Перечисление MLOperatorAttributeType
description: Указывает тип атрибута. Каждый тип атрибута соответствует числовом виде соответствующего типа ONNX.
ms.author: elcowle
ms.date: 11/8/2018
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
ms.openlocfilehash: b6f1fd8772ca183339ff03a672fcab69b1377c17
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474731"
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
| **Минимальная версия клиента** | Windows 10, сборки 17763 |
| **Минимальная версия сервера** | Windows Server 2019 с возможностями рабочего стола |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
