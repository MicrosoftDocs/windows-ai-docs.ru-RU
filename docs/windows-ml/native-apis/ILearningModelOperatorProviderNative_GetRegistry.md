---
title: Илеарнингмоделоператорпровидернативе... Registry, метод
description: Возвращает объект Имлоператоррегистри, содержащий определения пользовательских операторов.
ms.date: 4/2/2019
ms.topic: article
keywords: Windows 10, машинное обучение Windows, WinML, Registry
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- ILearningModelOperatorProviderNative.GetRegistry
api_location:
- windows.ai.machinelearning.native.h
ms.openlocfilehash: b82be2740d5c44ff343ec4c16380626abd0852b3
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70156521"
---
# <a name="ilearningmodeloperatorprovidernativegetregistry-method"></a>Илеарнингмоделоператорпровидернативе... Registry, метод

Возвращает объект [имлоператоррегистри](../custom-operators/IMLOperatorRegistry.md) , содержащий определения пользовательских операторов.

```cpp
void GetRegistry(
    IMLOperatorRegistry** ppOperatorRegistry);
```

## <a name="parameters"></a>Параметры

| Имя | Тип | Описание |
|------|------|-------------|
| ппоператоррегистри | [имлоператоррегистри](../custom-operators/IMLOperatorRegistry.md)** | Объект **имлоператоррегистри** , содержащий определения пользовательских операторов. |

## <a name="returns"></a>Возвращает

**void** Этот метод не возвращает значение.

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборка 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | Windows. AI. machinelearning. Native. h |

[!INCLUDE [help](../../includes/get-help.md)]
