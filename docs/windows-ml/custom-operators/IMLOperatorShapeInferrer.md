---
author: eliotcowley
title: Интерфейс IMLOperatorShapeInferrer
description: Реализуется inferrers фигуры вывести фигур границ тензорные выходные данные оператора.
ms.author: elcowle
ms.date: 4/1/2019
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
ms.openlocfilehash: 41fefb1dfe04f99ec41ceae82cc247668b3f43c5
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66180956"
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
| **Минимальный поддерживаемый клиент** | Windows 10, сборки 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
