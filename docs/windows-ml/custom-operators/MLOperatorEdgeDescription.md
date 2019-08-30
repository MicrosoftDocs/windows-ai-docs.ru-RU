---
title: Структура Млоператореджедескриптион
description: Задает свойства границы входного или выходного объекта оператора.
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, машинное обучение Windows, WinML, пользовательские операторы, Млоператореджедескриптион
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- MLOperatorEdgeDescription
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 76fde8dcb9c8ddcb89de272cf478c8b56e8ebeaa
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70156826"
---
# <a name="mloperatoredgedescription-struct"></a>Структура Млоператореджедескриптион

Задает свойства границы входного или выходного объекта оператора.

## <a name="fields"></a>Поля

| Имя           | Тип                     | Описание           |
|----------------|--------------------------|-----------------------|
| еджетипе       | [MLOperatorEdgeType](MLOperatorEdgeType.md)       | Тип границы. |
| процессу       | **uint64_t**                 |                       |
| тенсордататипе | [MLOperatorTensorDataType](MLOperatorTensorDataType.md) | Тип данных тензорные. Используется, если для **еджетипе** задано значение **тензорные**. |

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборка 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | Млоператораусор. h |

[!INCLUDE [help](../../includes/get-help.md)]
