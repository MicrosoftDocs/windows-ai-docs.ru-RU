---
author: eliotcowley
title: Структура MLOperatorSetId
description: Задает удостоверение оператор набора.
ms.author: elcowle
ms.date: 11/8/2018
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
ms.openlocfilehash: 54dc199488fc158315b71e8087b6bd3341d800e2
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2019
ms.locfileid: "59473991"
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
| **Минимальная версия клиента** | Windows 10, сборки 17763 |
| **Минимальная версия сервера** | Windows Server 2019 с возможностями рабочего стола |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
