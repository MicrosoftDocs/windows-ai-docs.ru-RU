---
author: eliotcowley
title: Интерфейс IMLOperatorKernelFactory
description: Реализованы автором ядра пользовательского оператора для создания экземпляров этого ядра.
ms.author: elcowle
ms.date: 4/1/2019
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
ms.openlocfilehash: 7c0883e426d5c85f013827e3d48193ab14415426
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66180456"
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
| **Минимальный поддерживаемый клиент** | Windows 10, сборки 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
