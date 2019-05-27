---
author: eliotcowley
title: MLOperatorKernelOptions enum
description: Определяет параметры, используемые при регистрации пользовательского оператора ядра.
ms.author: elcowle
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, windows машинного обучения, WinML, настраиваемые операторы, MLOperatorKernelOptions
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- MLOperatorKernelOptions
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 26861c7d8b1d154aa9ae9f8c5fc12e7e06f6ad7e
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66182036"
---
# <a name="mloperatorkerneloptions-enum"></a>MLOperatorKernelOptions enum

Определяет параметры, используемые при регистрации пользовательского оператора ядра.

## <a name="fields"></a>Поля

| Имя | Значение | Описание |
|------|-------|-------------|
| Нет | 0 | |
| AllowDynamicInputShapes | 1 | Указывает, формы ввода tensors, разрешено ли изменяться между вызовами экземпляр ядра оператор. Если это значение не задано, экземпляры ядра может запрашивать входной тензорные фигур во время создания и front-load работы инициализации, который зависит от этих фигур. Установка этого параметра может повысить производительность, если фигуры динамически изменяться между операциями определение и реализация ядра обрабатывает это эффективно. |

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборки 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
