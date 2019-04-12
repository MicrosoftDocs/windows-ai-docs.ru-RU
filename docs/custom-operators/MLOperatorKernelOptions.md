---
author: eliotcowley
title: MLOperatorKernelOptions enum
description: Определяет параметры, используемые при регистрации пользовательского оператора ядра.
ms.author: elcowle
ms.date: 11/8/2018
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
ms.openlocfilehash: 078694e26e255bf2e4d2472e8fe3cc8e41f92534
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474711"
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
| **Минимальная версия клиента** | Windows 10, сборки 17763 |
| **Минимальная версия сервера** | Windows Server 2019 с возможностями рабочего стола |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
