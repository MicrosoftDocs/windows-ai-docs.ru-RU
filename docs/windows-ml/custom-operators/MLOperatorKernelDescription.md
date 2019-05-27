---
author: eliotcowley
title: Структура MLOperatorKernelDescription
description: Описание пользовательского оператора ядра, используемые для регистрации этой схемы.
ms.author: elcowle
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, windows машинного обучения, WinML, настраиваемые операторы, MLOperatorKernelDescription
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- MLOperatorKernelDescription
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 69497372f547da6e26a003185f9eba84a19de1be
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66181376"
---
# <a name="mloperatorkerneldescription-struct"></a>Структура MLOperatorKernelDescription

Описание пользовательского оператора ядра, используемые для регистрации этой схемы.

## <a name="fields"></a>Поля

| Имя | Тип | Описание |
|------|------|-------------|
| defaultAttributeCount | **uint32_t** | Число значений атрибутов по умолчанию. |
| defaultAttributes | **const** [MLOperatorAttributeNameValue](MLOperatorAttributeNameValue.md)* | По умолчанию значения атрибутов. Они будут применены, если атрибуты отсутствуют в модели, содержащей тип оператора. |
| домен | **const char*** | Завершающаяся нулем UTF-8 строка, представляющая имя домена оператора. |
| executionOptions | **uint32_t** | Зарезервировано для дополнительных параметров. Должно быть 0. |
| executionType | [MLOperatorExecutionType](MLOperatorExecutionType.md) | Указывает, использует ли ядро ЦП или GPU для вычислений. |
| minimumOperatorSetVersion | **int32_t** | Задает минимальную версию оператора, для которой это ядро является допустимым. Максимальная версия определяется на основе регистраций оператор set схемы в последующих версиях тому же домену. |
| name | **const char*** | Завершающаяся нулем UTF-8 строка, представляющая имя оператора. |
| параметры | [MLOperatorKernelOptions](MLOperatorKernelOptions.md) | Параметры ядра которых применяются ко всем типам выполнения поставщика. |
| typeConstraintCount | **uint32_t** | Номер ограничения на тип. |
| typeConstraints | **const** [MLOperatorEdgeTypeConstraint](MLOperatorEdgeTypeConstraint.md)* | Массив ограничений типа. Каждое ограничение ограничивает входные и выходные данные, связанные со строкой типа метки для одного или нескольких типов edge. |

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборки 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
