---
author: eliotcowley
title: Интерфейс IMLOperatorKernel
description: Реализуется ядра пользовательского оператора.
ms.author: elcowle
ms.date: 11/8/2018
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
ms.openlocfilehash: 37fb0283336c69d920794726284d774e049e1ec6
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474251"
---
# <a name="imloperatorkernel-interface"></a>Интерфейс IMLOperatorKernel

Реализуется ядра пользовательского оператора. Фабрика, которая создает экземпляры этого интерфейса предоставляется при регистрации пользовательского оператора ядер, с помощью [IMLOperatorRegistry::RegisterOperatorKernel](IMLOperatorRegistry_RegisterOperatorKernel.md).

## <a name="methods"></a>Методы

| Имя | Описание |
|------|-------------|
| [Вычисления](IMLOperatorKernel_Compute.md) | Вычисляет выходные данные ядра. |

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальная версия клиента** | Windows 10, сборки 17763 |
| **Минимальная версия сервера** | Windows Server 2019 с возможностями рабочего стола |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
