---
title: Интерфейс Имлоператоркернелфактори
description: Реализуется автором пользовательского оператора в ядре для создания экземпляров этого ядра.
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, машинное обучение Windows, WinML, пользовательские операторы, Имлоператоркернелфактори
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorKernelFactory
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 67943742b596426512772a39c41ba42250131e1f
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157599"
---
# <a name="imloperatorkernelfactory-interface"></a>Интерфейс Имлоператоркернелфактори

Реализуется автором пользовательского оператора в ядре для создания экземпляров этого ядра.

## <a name="methods"></a>Методы

| Имя | Описание |
|------|-------------|
| [CreateKernel](IMLOperatorKernelFactory_CreateKernel.md) | Создает экземпляр связанного оператора ядра, учитывая сведения об использовании оператора в модели, описанной в предоставленном объекте контекста. |

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборка 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | Млоператораусор. h |

[!INCLUDE [help](../../includes/get-help.md)]
