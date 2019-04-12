---
author: eliotcowley
title: Интерфейс IMLOperatorKernelFactory
description: Реализованы автором ядра пользовательского оператора для создания экземпляров этого ядра.
ms.author: elcowle
ms.date: 11/8/2018
ms.topic: article
keywords: Windows 10, windows машинного обучения, WinML, настраиваемые операторы, IMLOperatorKernelFactory
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorKernelFactory
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 28bae41fe0e3e3e97d3b50451e29219b0cdbebbd
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474461"
---
# <a name="imloperatorkernelfactory-interface"></a>Интерфейс IMLOperatorKernelFactory

Реализованы автором ядра пользовательского оператора для создания экземпляров этого ядра.

## <a name="methods"></a>Методы

| Имя | Описание |
|------|-------------|
| [CreateKernel](IMLOperatorKernelFactory_CreateKernel.md) | Создает экземпляр ядра связанный оператор, учитывая сведения об использовании оператора в модель, описанную в указанный объект контекста. |

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальная версия клиента** | Windows 10, сборки 17763 |
| **Минимальная версия сервера** | Windows Server 2019 с возможностями рабочего стола |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
