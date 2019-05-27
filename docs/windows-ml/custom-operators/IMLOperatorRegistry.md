---
author: eliotcowley
title: Интерфейс IMLOperatorRegistry
description: Представляет экземпляр реестра для пользовательского оператора ядра и схемы.
ms.author: elcowle
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, windows машинного обучения, WinML, настраиваемые операторы, IMLOperatorRegistry
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorRegistry
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 7c1e9f1a026780bfae4fedfdae5244918f07e9bd
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66181736"
---
# <a name="imloperatorregistry-interface"></a>Интерфейс IMLOperatorRegistry

Представляет экземпляр реестра для пользовательского оператора ядра и схемы. Пользовательские операторы могут использоваться с интерфейсами API Windows.AI.MachineLearning возвращаются экземпляры **IMLOperatorRegistry** через **ILearningModelOperatorProviderNative**.

## <a name="methods"></a>Методы

| Имя | Описание |
|------|-------------|
| [RegisterOperatorKernel](IMLOperatorRegistry_RegisterOperatorKernel.md) | Регистрирует ядра пользовательского оператора. |
| [RegisterOperatorSetSchema](IMLOperatorRegistry_RegisterOperatorSetSchema.md) | Регистрирует набор схемы пользовательского оператора, включающего в себя набор оператор. |

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборки 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
