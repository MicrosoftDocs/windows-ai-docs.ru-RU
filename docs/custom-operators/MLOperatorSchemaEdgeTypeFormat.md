---
author: eliotcowley
title: Перечисление MLOperatorSchemaEdgeTypeFormat
description: Указывает способ, в какие типы входных и выходных данных описаны краев.
ms.author: elcowle
ms.date: 11/8/2018
ms.topic: article
keywords: Windows 10, windows машинного обучения, WinML, настраиваемые операторы, MLOperatorSchemaEdgeTypeFormat
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- MLOperatorSchemaEdgeTypeFormat
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: afaaa167f1608b55c982e7400f2b032c6e444b20
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474571"
---
# <a name="mloperatorschemaedgetypeformat-enum"></a>Перечисление MLOperatorSchemaEdgeTypeFormat

Указывает способ, в какие типы входных и выходных данных описаны краев. Это используется в [MLOperatorSchemaEdgeDescription](MLOperatorSchemaEdgeDescription.md) при определении схемы пользовательского оператора.

## <a name="fields"></a>Поля

| Имя | Значение | Описание |
|------|-------|-------------|
| EdgeDescription | 0 | Этот тип определен с помощью [MLOperatorEdgeDescription](MLOperatorEdgeDescription.md). |
| Метка | 1 | Тип определяется строковый тип, созданный как в схеме оператор ONNX. |

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальная версия клиента** | Windows 10, сборки 17763 |
| **Минимальная версия сервера** | Windows Server 2019 с возможностями рабочего стола |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
