---
author: eliotcowley
title: Структура MLOperatorAttributeNameValue
description: Указывает имя и значения атрибута для пользовательского оператора.
ms.author: elcowle
ms.date: 11/8/2018
ms.topic: article
keywords: Windows 10, windows машинного обучения, WinML, настраиваемые операторы, MLOperatorAttributeNameValue
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- MLOperatorAttributeNameValue
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: eedef4a8eeca543a6ab6dfaa1d11feb58a5b3045
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474681"
---
# <a name="mloperatorattributenamevalue-struct"></a>Структура MLOperatorAttributeNameValue

Указывает имя и значения атрибута для пользовательского оператора. Это используется при регистрации пользовательского оператора ядра и схемы пользовательского оператора.

## <a name="fields"></a>Поля

| Имя       | Тип                    | Описание |
|------------|-------------------------|-------------|
| числа с плавающей запятой     | **const число с плавающей запятой***            | значения точки, с плавающей запятой с 32-разрядной. Используется, когда поле типа **MLOperatorAttributeType::Float** или **MLOperatorAttributeType::FloatArray**. |
| целые числа       | **const int64_t***          | 64-разрядного целого значения. Используется, когда поле типа **MLOperatorAttributeType::Int** или **MLOperatorAttributeType::IntArray**. |
| name       | **const char***             | Завершающаяся нулем UTF-8 строка, представляющая имя атрибута в тип связанного оператора. |
| Зарезервировано   | **const void***             |             |
| Строки    | **const char\* const***      | Завершающаяся нулем UTF-8 строке журнала значения. Используется, когда поле типа **MLOperatorAttributeType::String** или **MLOperatorAttributeType::StringArray**. |
| Тип       | [MLOperatorAttributeType](MLOperatorAttributeType.md) | Тип атрибута в тип связанного оператора. |
| valueCount | **uint32_t**                | Число элементов в значении атрибута. Это должен быть 1, за исключением атрибутов, которые имеют тип массива. |

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальная версия клиента** | Windows 10, сборки 17763 |
| **Минимальная версия сервера** | Windows Server 2019 с возможностями рабочего стола |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
