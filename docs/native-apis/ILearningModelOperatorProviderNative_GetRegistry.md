---
author: eliotcowley
title: Метод ILearningModelOperatorProviderNative.GetRegistry
description: Получает объект IMLOperatorRegistry, содержащий определения пользовательского оператора.
ms.author: elcowle
ms.date: 11/8/2018
ms.topic: article
keywords: Windows 10, windows машинного обучения, WinML, GetRegistry
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- ILearningModelOperatorProviderNative.GetRegistry
api_location:
- windows.ai.machinelearning.native.h
ms.openlocfilehash: 7c058cac69137e1a3a622d1b1bcb8833deaa2342
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2019
ms.locfileid: "59473971"
---
# <a name="ilearningmodeloperatorprovidernativegetregistry-method"></a>Метод ILearningModelOperatorProviderNative.GetRegistry

Получает [IMLOperatorRegistry](../custom-operators/IMLOperatorRegistry.md) объект, содержащий определения пользовательского оператора.

```cpp
void GetRegistry(
    IMLOperatorRegistry** ppOperatorRegistry);
```

## <a name="parameters"></a>Параметры

| Имя | Тип | Описание |
|------|------|-------------|
| ppOperatorRegistry | [IMLOperatorRegistry](../custom-operators/IMLOperatorRegistry.md)** | **IMLOperatorRegistry** объект, содержащий определения пользовательского оператора. |

## <a name="returns"></a>Возвращает

**void** этот метод не возвращает значение.

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальная версия клиента** | Windows 10, сборки 17763 |
| **Минимальная версия сервера** | Windows Server 2019 с возможностями рабочего стола |
| **Header** | Windows.AI.machinelearning.Native.h |

[!INCLUDE [help](../includes/get-help.md)]
