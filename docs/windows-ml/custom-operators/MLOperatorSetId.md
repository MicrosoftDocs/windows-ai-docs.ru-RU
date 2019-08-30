---
title: Структура Млоператорсетид
description: Задает удостоверение набора операторов.
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, машинное обучение Windows, WinML, пользовательские операторы, Млоператорсетид
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- MLOperatorSetId
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 3288a9b6057db9349295d9d20f83f0ab93229c90
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70156751"
---
# <a name="mloperatorsetid-struct"></a>Структура Млоператорсетид

Задает удостоверение набора операторов.

## <a name="fields"></a>Поля

| Имя | Тип | Описание |
|------|------|-------------|
| домен | **const char*** | Домен оператора, например "ai.onnx.ml", или пустая строка для домена ONNX. |
| version | **int32_t** | Версия домена оператора. |

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборка 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | Млоператораусор. h |

[!INCLUDE [help](../../includes/get-help.md)]
