---
title: Интерфейс Имлоператортипеинферрер
description: Реализуется по типам источников ссылок для определения типов краев выходных данных оператора.
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, машинное обучение Windows, WinML, пользовательские операторы, Имлоператортипеинферрер
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorTypeInferrer
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 5c72857c03c2d55fe0c194a8903199f76512135d
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70156205"
---
# <a name="imloperatortypeinferrer-interface"></a>Интерфейс Имлоператортипеинферрер

Реализуется по типам источников ссылок для определения типов краев выходных данных оператора. При регистрации схемы пользовательских операторов необходимо указать источники ссылок на типы, если структура [млоператорсчемадескриптион](MLOperatorSchemaDescription.md) не может выразить, как определяются&mdash;типы вывода, например, когда атрибут определяет данные. тип одного из выходных данных этого оператора.

## <a name="methods"></a>Методы

| Имя | Описание |
|------|-------------|
| [InferOutputTypes](IMLOperatorTypeInferrer_InferOutputTypes.md) | Вызывается для определения типов краев выходных данных оператора. |

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборка 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | Млоператораусор. h |

[!INCLUDE [help](../../includes/get-help.md)]
