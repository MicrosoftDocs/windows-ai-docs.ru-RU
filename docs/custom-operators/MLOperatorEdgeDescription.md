---
author: eliotcowley
title: Структура MLOperatorEdgeDescription
description: Задает свойства границы входного или выходного оператора.
ms.author: elcowle
ms.date: 11/8/2018
ms.topic: article
keywords: Windows 10, windows машинного обучения, WinML, настраиваемые операторы, MLOperatorEdgeDescription
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- MLOperatorEdgeDescription
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 8d578d29b5e24e7e64ab1d3f704503fb0f46eeb1
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474381"
---
# <a name="mloperatoredgedescription-struct"></a>Структура MLOperatorEdgeDescription

Задает свойства границы входного или выходного оператора.

## <a name="fields"></a>Поля

| Имя           | Тип                     | Описание           |
|----------------|--------------------------|-----------------------|
| edgeType       | [MLOperatorEdgeType](MLOperatorEdgeType.md)       | Тип границы. |
| Зарезервировано       | **uint64_t**                 |                       |
| tensorDataType | [MLOperatorTensorDataType](MLOperatorTensorDataType.md) | Тип данных тензорные. Используется, когда **edgeType** присваивается **Тензорные**. |

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальная версия клиента** | Windows 10, сборки 17763 |
| **Минимальная версия сервера** | Windows Server 2019 с возможностями рабочего стола |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
