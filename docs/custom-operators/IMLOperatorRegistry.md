---
author: eliotcowley
title: Интерфейс IMLOperatorRegistry
description: Представляет экземпляр реестра для пользовательского оператора ядра и схемы.
ms.author: elcowle
ms.date: 11/8/2018
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
ms.openlocfilehash: e3e2edd778a63a06760c6fd46b096e88db4f5cdb
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474081"
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
| **Минимальная версия клиента** | Windows 10, сборки 17763 |
| **Минимальная версия сервера** | Windows Server 2019 с возможностями рабочего стола |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
