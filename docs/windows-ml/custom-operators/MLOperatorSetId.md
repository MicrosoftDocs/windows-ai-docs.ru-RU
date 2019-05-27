---
author: eliotcowley
title: Структура MLOperatorSetId
description: Задает удостоверение оператор набора.
ms.author: elcowle
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, windows машинного обучения, WinML, настраиваемые операторы, MLOperatorSetId
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- MLOperatorSetId
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 6c3af6b616a93b9dbf1bdc8d9d951ca2770a6a46
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66181306"
---
# <a name="mloperatorsetid-struct"></a>Структура MLOperatorSetId

Задает удостоверение оператор набора.

## <a name="fields"></a>Поля

| Имя | Тип | Описание |
|------|------|-------------|
| домен | **const char*** | Домен оператора, например, «ai.onnx.ml» или пустую строку для домена ONNX. |
| version | **int32_t** | Версия домена оператор. |

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборки 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
