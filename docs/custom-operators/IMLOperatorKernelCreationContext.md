---
author: eliotcowley
title: IMLOperatorKernelCreationContext interface
description: Предоставляет сведения об использовании оператора, при создании ядра.
ms.author: elcowle
ms.date: 11/8/2018
ms.topic: article
keywords: Windows 10, windows машинного обучения, WinML, настраиваемые операторы, IMLOperatorKernelCreationContext
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorKernelCreationContext
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: be2f47f682f7289d48d007c8d42af3049f6e3d46
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474741"
---
# <a name="imloperatorkernelcreationcontext-interface"></a>IMLOperatorKernelCreationContext interface

Предоставляет сведения об использовании оператора, при создании ядра.

## <a name="methods"></a>Методы

| Имя | Описание |
|------|-------------|
| [GetExecutionInterface](IMLOperatorKernelCreationContext_GetExecutionInterface.md) | Возвращает объект, различаются, поддерживаемые интерфейсы на основе ядра типа. |
| [GetInputCount](IMLOperatorKernelCreationContext_GetInputCount.md) | Получает количество входных данных для оператора. |
| [GetInputEdgeDescription](IMLOperatorKernelCreationContext_GetInputEdgeDescription.md) | Возвращает описание указанного входного края оператора. |
| [GetOutputCount](IMLOperatorKernelCreationContext_GetOutputCount.md) | Получает количество выходов оператору. |
| [GetOutputEdgeDescription](IMLOperatorKernelCreationContext_GetOutputEdgeDescription.md) | Получает описание указанный выходной края оператора. |
| [GetTensorShapeDescription](IMLOperatorKernelCreationContext_GetTensorShapeDescription.md) | Получает описание фигуры ввода-вывода по краям оператор. |
| [HasTensorShapeDescription](IMLOperatorKernelCreationContext_HasTensorShapeDescription.md) | Возвращает значение true, если описание фигуры входных и выходных подключен к краям оператор может запрашиваться с помощью **GetTensorShapeDescription**. |
| [IsInputValid](IMLOperatorKernelCreationContext_IsInputValid.md) | Возвращает значение true, если входными данными для оператора является допустимым. Эта функция всегда возвращает значение true, за исключением необязательных набора входных данных. |
| [IsOutputValid](IMLOperatorKernelCreationContext_IsOutputValid.md) | Возвращает значение true, если выходные данные оператора является допустимым. Эта функция всегда возвращает значение true, за исключением необязательные выходные данные. |

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальная версия клиента** | Windows 10, сборки 17763 |
| **Минимальная версия сервера** | Windows Server 2019 с возможностями рабочего стола |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
