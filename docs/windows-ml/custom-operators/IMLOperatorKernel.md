---
title: Интерфейс Имлоператоркернел
description: Реализуется с помощью пользовательских ядер операторов.
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, машинное обучение Windows, WinML, пользовательские операторы, Имлоператоркернел
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorKernel
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: b00ced7748b55f8153c346c7e5f2c1083cb18bfd
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157092"
---
# <a name="imloperatorkernel-interface"></a>Интерфейс Имлоператоркернел

Реализуется с помощью пользовательских ядер операторов. Фабрика, которая создает экземпляры этого интерфейса, предоставляется при регистрации ядер пользовательских операторов с помощью [имлоператоррегистри:: регистероператоркернел](IMLOperatorRegistry_RegisterOperatorKernel.md).

## <a name="methods"></a>Методы

| Имя | Описание |
|------|-------------|
| [Compute](IMLOperatorKernel_Compute.md) | Выполняет вычисление выходных данных ядра. |

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборка 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | Млоператораусор. h |

[!INCLUDE [help](../../includes/get-help.md)]
