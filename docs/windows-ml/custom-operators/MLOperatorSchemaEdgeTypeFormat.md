---
title: Перечисление Млоператорсчемаеджетипеформат
description: Указывает способ описания типов входных и выходных границ.
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, машинное обучение Windows, WinML, пользовательские операторы, Млоператорсчемаеджетипеформат
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- MLOperatorSchemaEdgeTypeFormat
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 12afc60826f4a6f2ac4badbed4a876600544f81d
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157673"
---
# <a name="mloperatorschemaedgetypeformat-enum"></a>Перечисление Млоператорсчемаеджетипеформат

Указывает способ описания типов входных и выходных границ. Он используется в [млоператорсчемаеджедескриптион](MLOperatorSchemaEdgeDescription.md) при определении пользовательской схемы оператора.

## <a name="fields"></a>Поля

| Имя | Значение | Описание |
|------|-------|-------------|
| еджедескриптион | 0 | Тип определяется с помощью [млоператореджедескриптион](MLOperatorEdgeDescription.md). |
| Метка | 1 | Тип определяется строкой типа, созданной в схеме оператора ONNX. |

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборка 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | Млоператораусор. h |

[!INCLUDE [help](../../includes/get-help.md)]
