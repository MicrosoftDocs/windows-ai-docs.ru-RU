---
author: eliotcowley
title: Интерфейс IMLOperatorShapeInferrer
description: Реализуется inferrers фигуры вывести фигур границ тензорные выходные данные оператора.
ms.author: elcowle
ms.date: 11/8/2018
ms.topic: article
keywords: Windows 10, windows машинного обучения, WinML, настраиваемые операторы, IMLOperatorShapeInferrer
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorShapeInferrer
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 7c887e5ebe2b7574136555910fb0613a5d2cbf2d
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474511"
---
# <a name="imloperatorshapeinferrer-interface"></a>Интерфейс IMLOperatorShapeInferrer

Реализуется inferrers фигуры вывести фигур границ тензорные выходные данные оператора. Inferrers фигуры могут предоставляться при регистрации пользовательского оператора ядра для повышения производительности и включения ядра для запроса вида tensors его выходные данные при его создании и вычислить. Inferrers фигуры также могут предоставляться при регистрации пользовательского оператора схемы для улучшения проверки модели.

## <a name="methods"></a>Методы

| Имя | Описание |
|------|-------------|
| [InferOutputShapes](IMLOperatorShapeInferrer_InferOutputShapes.md) | Вызывается, чтобы определить фигуры границ выходные данные оператора. |

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальная версия клиента** | Windows 10, сборки 17763 |
| **Минимальная версия сервера** | Windows Server 2019 с возможностями рабочего стола |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
