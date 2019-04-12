---
author: eliotcowley
title: Структура MLOperatorAttribute
description: Указывает имя и свойства атрибута пользовательского оператора.
ms.author: elcowle
ms.date: 11/8/2018
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
ms.openlocfilehash: eaf1265d545c34833b67a6695bc2496a1258b0c4
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474801"
---
# <a name="mloperatorattribute-struct"></a>Структура MLOperatorAttribute

Указывает имя и свойства атрибута пользовательского оператора. Это используется при регистрации пользовательского оператора ядра и схемы пользовательского оператора.

## <a name="fields"></a>Поля

| Имя     | Тип                    | Описание |
|----------|-------------------------|-------------|
| name     | **Char***                   | Завершающаяся нулем UTF-8 строка, представляющая имя атрибута в тип связанного оператора. |
| обязательные | **bool**                    | Ли атрибут обязателен в любой модели, используя тип связанный оператор. |
| Тип     | [MLOperatorAttributeType](MLOperatorAttributeType.md) | Тип атрибута в тип связанного оператора. |

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальная версия клиента** | Windows 10, сборки 17763 |
| **Минимальная версия сервера** | Windows Server 2019 с возможностями рабочего стола |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
