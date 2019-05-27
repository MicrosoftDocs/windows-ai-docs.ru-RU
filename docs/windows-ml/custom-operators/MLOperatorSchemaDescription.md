---
author: eliotcowley
title: Структура MLOperatorSchemaDescription
description: Описание схемы пользовательский оператор, используемый для регистрации этой схемы.
ms.author: elcowle
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, windows машинного обучения, WinML, настраиваемые операторы, MLOperatorSchemaDescription
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- MLOperatorSchemaDescription
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 22abc2d02ab6cfeeeeb5007f8b3503c2a3f22039
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66181366"
---
# <a name="mloperatorschemadescription-struct"></a>Структура MLOperatorSchemaDescription

Описание схемы пользовательский оператор, используемый для регистрации этой схемы.

## <a name="fields"></a>Поля

| Имя | Тип | Описание |
|------|------|-------------|
| attributeCount | **uint32_t** | Число предоставленных атрибутов. |
| атрибуты | **const** [MLOperatorAttribute](MLOperatorAttribute.md)* | Набор атрибутов, поддерживаемых типом оператора. |
| defaultAttributeCount | **uint32_t** | Число значений атрибутов по умолчанию. |
| defaultAttributes | **const** [MLOperatorAttributeNameValue](MLOperatorAttributeNameValue.md)* | По умолчанию значения атрибутов. Они будут применены, если атрибуты отсутствуют в модели, содержащей тип оператора. |
| inputCount | **uint32_t** | Количество входных данных от оператора. |
| Способы ввода | **const** [MLOperatorSchemaEdgeDescription](MLOperatorSchemaEdgeDescription.md)* | Массив, содержащий описания оператора входных краев. |
| name | **const char*** | Завершающаяся нулем UTF-8 строка, представляющая имя оператора. |
| operatorSetVersionAtLastChange | **int32_t** | Оператор задать версию, по которому этот оператор была введена или последнего изменения. |
| outputCount | **uint32_t** | Количество выходов оператора. |
| Выходные данные | **const** [MLOperatorSchemaEdgeDescription](MLOperatorSchemaEdgeDescription.md)* | Массив, содержащий описания оператора выходных краев. |
| typeConstraintCount | **uint32_t** | Номер ограничения на тип. |
| typeConstraints | **const** [MLOperatorEdgeTypeConstraint](MLOperatorEdgeTypeConstraint.md)* | Массив ограничений типа. Каждое ограничение ограничивает входные и выходные данные, связанные со строкой типа метки для одного или нескольких типов edge. |

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборки 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
