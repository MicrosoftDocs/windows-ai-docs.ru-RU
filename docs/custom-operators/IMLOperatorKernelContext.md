---
author: eliotcowley
title: Интерфейс IMLOperatorKernelContext
description: Предоставляет сведения об использовании оператора, хотя вычисляются ядра.
ms.author: elcowle
ms.date: 11/8/2018
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
ms.openlocfilehash: 08accb1a8a1b0c9d2fb2f85c1e76034508bc6de7
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474671"
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
| **Минимальная версия клиента** | Windows 10, сборки 17763 |
| **Минимальная версия сервера** | Windows Server 2019 с возможностями рабочего стола |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
