---
title: Структура Млоператораттрибуте
description: Задает имя и свойства атрибута пользовательского оператора.
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, машинное обучение Windows, WinML, пользовательские операторы, Млоператораттрибуте
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- MLOperatorAttribute
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 7ddd6fa76b920c4901aae9d2583f6b9d15a17c75
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157948"
---
# <a name="mloperatorattribute-struct"></a>Структура Млоператораттрибуте

Задает имя и свойства атрибута пользовательского оператора. Используется при регистрации ядер пользовательских операторов и схемы настраиваемого оператора.

## <a name="fields"></a>Поля

| Имя     | Тип                    | Описание |
|----------|-------------------------|-------------|
| name     | **типа***                   | Строка UTF-8, заканчивающаяся нулем, представляющая имя атрибута в связанном типе оператора. |
| обязательные | **логическом**                    | Является ли атрибут обязательным в любой модели с помощью связанного типа оператора. |
| type     | [MLOperatorAttributeType](MLOperatorAttributeType.md) | Тип атрибута в связанном типе оператора. |

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборка 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | Млоператораусор. h |

[!INCLUDE [help](../../includes/get-help.md)]
