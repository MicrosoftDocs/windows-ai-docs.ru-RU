---
author: eliotcowley
title: Интерфейс IMLOperatorKernel
description: Реализуется ядра пользовательского оператора.
ms.author: elcowle
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, windows машинного обучения, WinML, настраиваемые операторы, IMLOperatorKernel
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorKernel
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 20799a9544cb880da5f63b37ba53b054dbd5afae
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66180706"
---
# <a name="imloperatorkernel-interface"></a>Интерфейс IMLOperatorKernel

Реализуется ядра пользовательского оператора. Фабрика, которая создает экземпляры этого интерфейса предоставляется при регистрации пользовательского оператора ядер, с помощью [IMLOperatorRegistry::RegisterOperatorKernel](IMLOperatorRegistry_RegisterOperatorKernel.md).

## <a name="methods"></a>Методы

| Имя | Описание |
|------|-------------|
| [Вычислений](IMLOperatorKernel_Compute.md) | Вычисляет выходные данные ядра. |

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборки 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
