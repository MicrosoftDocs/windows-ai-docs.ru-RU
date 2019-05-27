---
author: eliotcowley
title: Интерфейс IMLOperatorAttributes
description: Представляет значения атрибутов оператора, как определено в модели, с помощью оператора.
ms.author: elcowle
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, windows машинного обучения, WinML, настраиваемые операторы, IMLOperatorAttributes
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorAttributes
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: c04adcd91142d7b3ec0bdae5011a9293d5c19e17
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66180996"
---
# <a name="imloperatorattributes-interface"></a>Интерфейс IMLOperatorAttributes

Представляет значения атрибутов оператора, как определено в модели, с помощью оператора. Этот интерфейс вызывается путем реализации пользовательского оператора ядер и реализации inferrers фигуры и тип.

## <a name="methods"></a>Методы

| Имя | Описание |
|------|-------------|
| [GetAttribute](IMLOperatorAttributes_GetAttribute.md) | Получает значение атрибута элемента, являющегося числового типа. |
| [GetAttributeElementCount](IMLOperatorAttributes_GetAttributeElementCount.md) | Возвращает количество элементов в атрибуте. |
| [GetStringAttributeElement](IMLOperatorAttributes_GetStringAttributeElement.md) | Получает значение элемента атрибута, который имеет строковый тип. |
| [GetStringAttributeElementLength](IMLOperatorAttributes_GetStringAttributeElementLength.md) | Возвращает длину элемента атрибута, который имеет строковый тип. |

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборки 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
