---
author: eliotcowley
title: Структура MLOperatorKernelDescription
description: Описание пользовательского оператора ядра, используемые для регистрации этой схемы.
ms.author: elcowle
ms.date: 11/8/2018
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
ms.openlocfilehash: b3d57c918adf4b2d6c875f35894b36c38dd39043
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474151"
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
| **Минимальная версия клиента** | Windows 10, сборки 17763 |
| **Минимальная версия сервера** | Windows Server 2019 с возможностями рабочего стола |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
