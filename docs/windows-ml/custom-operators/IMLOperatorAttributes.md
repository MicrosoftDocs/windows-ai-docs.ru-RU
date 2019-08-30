---
title: Интерфейс Имлоператораттрибутес
description: Представляет значения атрибутов оператора, как определено моделью с помощью оператора.
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, машинное обучение Windows, WinML, пользовательские операторы, Имлоператораттрибутес
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorAttributes
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: ac15ec91bceeebb57c7cd7b45989aacfaebd69c9
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157069"
---
# <a name="imloperatorattributes-interface"></a>Интерфейс Имлоператораттрибутес

Представляет значения атрибутов оператора, как определено моделью с помощью оператора. Этот интерфейс вызывается реализациями пользовательских ядер операторов и реализациями фигур и типов источников ссылок.

## <a name="methods"></a>Методы

| Имя | Описание |
|------|-------------|
| [GetAttribute](IMLOperatorAttributes_GetAttribute.md) | Возвращает значение элемента атрибута, имеющего числовой тип. |
| [GetAttributeElementCount](IMLOperatorAttributes_GetAttributeElementCount.md) | Возвращает число элементов в атрибуте. |
| [GetStringAttributeElement](IMLOperatorAttributes_GetStringAttributeElement.md) | Возвращает значение элемента атрибута, имеющего строковый тип. |
| [GetStringAttributeElementLength](IMLOperatorAttributes_GetStringAttributeElementLength.md) | Возвращает длину элемента атрибута, имеющего строковый тип. |

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборка 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | Млоператораусор. h |

[!INCLUDE [help](../../includes/get-help.md)]
