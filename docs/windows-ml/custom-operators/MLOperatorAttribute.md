---
author: eliotcowley
title: Структура MLOperatorAttribute
description: Указывает имя и свойства атрибута пользовательского оператора.
ms.author: elcowle
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, windows машинного обучения, WinML, настраиваемые операторы, MLOperatorAttribute
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- MLOperatorAttribute
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 6d5b9aeb6cc20a9aae48971a1c0735ef5b4c7049
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66182086"
---
# <a name="mloperatorattribute-struct"></a>Структура MLOperatorAttribute

Указывает имя и свойства атрибута пользовательского оператора. Это используется при регистрации пользовательского оператора ядра и схемы пользовательского оператора.

## <a name="fields"></a>Поля

| Имя     | Тип                    | Описание |
|----------|-------------------------|-------------|
| name     | **Char***                   | Завершающаяся нулем UTF-8 строка, представляющая имя атрибута в тип связанного оператора. |
| обязательные | **bool**                    | Ли атрибут обязателен в любой модели, используя тип связанный оператор. |
| type     | [MLOperatorAttributeType](MLOperatorAttributeType.md) | Тип атрибута в тип связанного оператора. |

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборки 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
