---
author: eliotcowley
title: MLOperatorParameterOptions enum
description: Указывает флаги параметров, входных и выходных границ операторов.
ms.author: elcowle
ms.date: 11/8/2018
ms.topic: article
keywords: Windows 10, windows машинного обучения, WinML, настраиваемые операторы, MLOperatorParameterOptions
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- MLOperatorParameterOptions
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 61e14be6c729c52312ee3d3a47bfd6bc49a58f5b
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474191"
---
# <a name="mloperatorparameteroptions-enum"></a>MLOperatorParameterOptions enum

Указывает флаги параметров, входных и выходных границ операторов. Эти параметры используются при определении схемы пользовательского оператора.

## <a name="fields"></a>Поля

| Имя | Значение | Описание |
|------|-------|-------------|
| Единый | 0 | Имеется один экземпляр входных или выходных параметров. |
| Необязательный | 1 | Входные или выходные данные можно опустить. |
| С переменным числом аргументов | 2 | Число экземпляров от оператора — переменная. Параметры с переменным числом аргументов должен быть последним среди набора входных и выходных данных. |

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальная версия клиента** | Windows 10, сборки 17763 |
| **Минимальная версия сервера** | Windows Server 2019 с возможностями рабочего стола |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
