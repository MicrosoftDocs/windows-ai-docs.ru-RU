---
title: Интерфейс Имлоператоршапеинферрер
description: Реализуется с помощью фигурных источников, чтобы вывести фигуры выходных тензорные границ оператора.
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, машинное обучение Windows, WinML, пользовательские операторы, Имлоператоршапеинферрер
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorShapeInferrer
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 64917ecf3cf490ccb98db86bc670189acbb43c78
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157776"
---
# <a name="imloperatorshapeinferrer-interface"></a>Интерфейс Имлоператоршапеинферрер

Реализуется с помощью фигурных источников, чтобы вывести фигуры выходных тензорные границ оператора. Источники ссылок на фигуру могут быть предоставлены при регистрации ядер пользовательских операторов, чтобы повысить производительность и позволить ядру запрашивать форму выходных десятков при создании и вычислении. Источники ссылок фигур также могут быть предоставлены при регистрации пользовательской схемы оператора для улучшения проверки модели.

## <a name="methods"></a>Методы

| Имя | Описание |
|------|-------------|
| [InferOutputShapes](IMLOperatorShapeInferrer_InferOutputShapes.md) | Вызывается для вывода форм краев выходных данных оператора. |

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборка 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | Млоператораусор. h |

[!INCLUDE [help](../../includes/get-help.md)]
