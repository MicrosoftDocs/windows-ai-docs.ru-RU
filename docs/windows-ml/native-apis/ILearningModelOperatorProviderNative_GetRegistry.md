---
author: eliotcowley
title: Метод ILearningModelOperatorProviderNative.GetRegistry
description: Получает объект IMLOperatorRegistry, содержащий определения пользовательского оператора.
ms.author: elcowle
ms.date: 4/2/2019
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
ms.openlocfilehash: 9207ae651cc7f8985b3c81f3971834c2c6b629ce
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66180126"
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
| **Минимальный поддерживаемый клиент** | Windows 10, сборки 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | Windows.AI.machinelearning.Native.h |

[!INCLUDE [help](../../includes/get-help.md)]
