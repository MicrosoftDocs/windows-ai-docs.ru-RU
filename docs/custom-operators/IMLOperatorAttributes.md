---
author: eliotcowley
title: Интерфейс IMLOperatorAttributes
description: Представляет значения атрибутов оператора, как определено в модели, с помощью оператора.
ms.author: elcowle
ms.date: 11/8/2018
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
ms.openlocfilehash: 0099e28cd0f542fc59880f299e7e874f088c4fb5
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474941"
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
| **Минимальная версия клиента** | Windows 10, сборки 17763 |
| **Минимальная версия сервера** | Windows Server 2019 с возможностями рабочего стола |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
