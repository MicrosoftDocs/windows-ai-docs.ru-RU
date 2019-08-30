---
title: Структура Млоператорсчемаеджедескриптион
description: Задает сведения о внешнем входном или выходном крае оператора.
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, машинное обучение Windows, WinML, пользовательские операторы, Млоператорсчемаеджедескриптион
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- MLOperatorSchemaEdgeDescription
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 49f0e77e0e97a6f2e4cc6454eed261b1961f89a6
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70156767"
---
# <a name="mloperatorschemaedgedescription-struct"></a>Структура Млоператорсчемаеджедескриптион

Задает сведения о внешнем входном или выходном крае оператора. Используется при определении пользовательской схемы оператора.

## <a name="fields"></a>Поля

| Имя | Тип | Описание |
|------|------|-------------|
| еджедескриптион | [MLOperatorEdgeDescription](MLOperatorEdgeDescription.md) | Структура, описывающая поддержку типов. Используется, если **typeFormat** имеет **Млоператорсчемаеджетипеформат:: еджедескриптион**. |
| параметры | [MLOperatorParameterOptions](MLOperatorParameterOptions.md) | Параметры параметра, включая, является ли он необязательным или Variadic. |
| процессу | **void*** | |
| typeFormat | [MLOperatorSchemaEdgeTypeFormat](MLOperatorSchemaEdgeTypeFormat.md) | Способ определения ограничений типа и сопоставления типов. |
| типелабел | **типа*** | Строка метки типа, созданная как схема оператора ONNX. Например, "T". Используется, если **typeFormat** имеет **Млоператорсчемаеджетипеформат:: Label**. |

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборка 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | Млоператораусор. h |

[!INCLUDE [help](../../includes/get-help.md)]
