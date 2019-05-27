---
author: eliotcowley
title: Интерфейс IMLOperatorKernelContext
description: Предоставляет сведения об использовании оператора, хотя вычисляются ядра.
ms.author: elcowle
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, windows машинного обучения, WinML, настраиваемые операторы, IMLOperatorKernelContext
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorKernelContext
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 3e6708a905d3ff9277fa80793329eb149fbafb2c
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66181176"
---
# <a name="imloperatorkernelcontext-interface"></a>Интерфейс IMLOperatorKernelContext

Предоставляет сведения об использовании оператора, хотя вычисляются ядра.

## <a name="methods"></a>Методы

| Имя | Описание |
|------|-------------|
| [AllocateTemporaryData](IMLOperatorKernelContext_AllocateTemporaryData.md) | Выделяет временных данных, который будет использоваться в качестве промежуточных памяти в течение всего вызова [IMLOperatorKernel::Compute](IMLOperatorKernel_Compute.md). |
| [GetExecutionInterface](IMLOperatorKernelContext_GetExecutionInterface.md) | Возвращает объект, различаются, поддерживаемые интерфейсы на основе ядра типа. |
| [GetInputTensor](IMLOperatorKernelContext_GetInputTensor.md) | Получает входной тензорные оператора по указанному индексу. |
| [GetOutputTensor (uint32_t, IMLOperatorTensor **)](IMLOperatorKernelContext_GetOutputTensor.md#GetOutputTensor1) | Получает тензорные выходные данные оператора по указанному индексу. |
| [GetOutputTensor (uint32_t, uint32_t, const uint32_t *, IMLOperatorTensor **)](IMLOperatorKernelContext_GetOutputTensor.md#GetOutputTensor2) | Получает тензорные выходные данные оператора по указанному индексу, а при объявлении его форму. |

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборки 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
