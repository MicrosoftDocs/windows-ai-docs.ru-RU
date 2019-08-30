---
title: Интерфейс Имлоператоркернелконтекст
description: Предоставляет сведения об использовании оператора при вычислении ядра.
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, машинное обучение Windows, WinML, пользовательские операторы, Имлоператоркернелконтекст
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorKernelContext
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: c1358ad70c4807c45a3ad6b130c770fe5bac82a5
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157209"
---
# <a name="imloperatorkernelcontext-interface"></a>Интерфейс Имлоператоркернелконтекст

Предоставляет сведения об использовании оператора при вычислении ядра.

## <a name="methods"></a>Методы

| Имя | Описание |
|------|-------------|
| [AllocateTemporaryData](IMLOperatorKernelContext_AllocateTemporaryData.md) | Выделяет временные данные, которые будут использоваться в качестве промежуточной памяти для длительности вызова [имлоператоркернел:: COMPUTE](IMLOperatorKernel_Compute.md). |
| [GetExecutionInterface](IMLOperatorKernelContext_GetExecutionInterface.md) | Возвращает объект, Поддерживаемые интерфейсы которого различаются в зависимости от типа ядра. |
| [GetInputTensor](IMLOperatorKernelContext_GetInputTensor.md) | Возвращает входной тензорные оператора по указанному индексу. |
| [Жетаутпуттенсор (uint32_t, Имлоператортенсор * *)](IMLOperatorKernelContext_GetOutputTensor.md#GetOutputTensor1) | Возвращает выходной тензорные оператора по указанному индексу. |
| [Жетаутпуттенсор (uint32_t, uint32_t, const uint32_t *, Имлоператортенсор * *)](IMLOperatorKernelContext_GetOutputTensor.md#GetOutputTensor2) | Возвращает выходной тензорные оператора по указанному индексу при объявлении его фигуры. |

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборка 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | Млоператораусор. h |

[!INCLUDE [help](../../includes/get-help.md)]
