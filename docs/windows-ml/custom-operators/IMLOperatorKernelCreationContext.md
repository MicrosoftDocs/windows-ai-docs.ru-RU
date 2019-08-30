---
title: Интерфейс Имлоператоркернелкреатионконтекст
description: Предоставляет сведения об использовании оператора во время создания ядер.
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, машинное обучение Windows, WinML, пользовательские операторы, Имлоператоркернелкреатионконтекст
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorKernelCreationContext
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: df366d878a9ff05b3802e1791cb5476ae50225af
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70156832"
---
# <a name="imloperatorkernelcreationcontext-interface"></a>Интерфейс Имлоператоркернелкреатионконтекст

Предоставляет сведения об использовании оператора во время создания ядер.

## <a name="methods"></a>Методы

| Имя | Описание |
|------|-------------|
| [GetExecutionInterface](IMLOperatorKernelCreationContext_GetExecutionInterface.md) | Возвращает объект, Поддерживаемые интерфейсы которого различаются в зависимости от типа ядра. |
| [GetInputCount](IMLOperatorKernelCreationContext_GetInputCount.md) | Возвращает число входов для оператора. |
| [GetInputEdgeDescription](IMLOperatorKernelCreationContext_GetInputEdgeDescription.md) | Возвращает описание указанной входной границы оператора. |
| [GetOutputCount](IMLOperatorKernelCreationContext_GetOutputCount.md) | Возвращает число выходов для оператора. |
| [GetOutputEdgeDescription](IMLOperatorKernelCreationContext_GetOutputEdgeDescription.md) | Возвращает описание указанного края вывода оператора. |
| [GetTensorShapeDescription](IMLOperatorKernelCreationContext_GetTensorShapeDescription.md) | Возвращает описание входных и выходных фигур, подключенных к краям операторов. |
| [HasTensorShapeDescription](IMLOperatorKernelCreationContext_HasTensorShapeDescription.md) | Возвращает значение true, если описание входных и выходных фигур, подключенных к краям оператора, может быть запрошено с помощью **жеттенсоршапедескриптион**. |
| [IsInputValid](IMLOperatorKernelCreationContext_IsInputValid.md) | Возвращает значение true, если входные данные оператора являются допустимыми. Это всегда возвращает значение true, за исключением необязательных входов. |
| [IsOutputValid](IMLOperatorKernelCreationContext_IsOutputValid.md) | Возвращает значение true, если выходные данные оператора являются допустимыми. Это всегда возвращает значение true, за исключением необязательных выходов. |

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборка 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | Млоператораусор. h |

[!INCLUDE [help](../../includes/get-help.md)]
