---
title: Интерфейс Имлоператоррегистри
description: Представляет экземпляр реестра для ядра и схемы пользовательского оператора.
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, машинное обучение Windows, WinML, пользовательские операторы, Имлоператоррегистри
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorRegistry
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: fc24c8e43a76b4258471dfed37c5b528699b69db
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157617"
---
# <a name="imloperatorregistry-interface"></a>Интерфейс Имлоператоррегистри

Представляет экземпляр реестра для ядра и схемы пользовательского оператора. Пользовательские операторы можно использовать с API-интерфейсами Windows. AI. MachineLearning, возвращая экземпляры **имлоператоррегистри** через **илеарнингмоделоператорпровидернативе**.

## <a name="methods"></a>Методы

| Имя | Описание |
|------|-------------|
| [RegisterOperatorKernel](IMLOperatorRegistry_RegisterOperatorKernel.md) | Регистрирует ядро пользовательского оператора. |
| [RegisterOperatorSetSchema](IMLOperatorRegistry_RegisterOperatorSetSchema.md) | Регистрирует набор пользовательских схем операторов, включающих набор операторов. |

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборка 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | Млоператораусор. h |

[!INCLUDE [help](../../includes/get-help.md)]
