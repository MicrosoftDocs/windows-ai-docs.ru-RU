---
author: eliotcowley
title: WinML собственные API-интерфейсы
description: Этот раздел содержит документацию по WinML собственных API.
ms.author: elcowle
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, windows машинное обучение, WinML
ms.localizationpriority: medium
ms.openlocfilehash: 0da51c115e7f951609122dc0df88d82d82425924
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66181886"
---
# <a name="winml-native-apis"></a>WinML собственные API-интерфейсы

Собственные API-интерфейсы машинного обучения Windows находятся в папке **windows.ai.machinelearning.native.h**.

## <a name="apis"></a>Интерфейсы API

Ниже приведен список собственных API WinML их синтаксис и описаниями.

### <a name="interfaces"></a>Интерфейсы

| Имя | Описание |
|------|-------------|
| [ILearningModelDeviceFactoryNative](native-apis/ILearningModelDeviceFactoryNative.md) | Предоставляет доступ к методам фабрики, которые обеспечивают создание [ILearningModelDevice](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodeldevice) объектов с помощью [ID3D12CommandQueue](https://docs.microsoft.com/windows/desktop/api/d3d12/nn-d3d12-id3d12commandqueue). |
| [ITensorNative](native-apis/ITensorNative.md) | Предоставляет доступ к [ITensor](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.itensor) как массив байтов или [ID3D12Resource](https://docs.microsoft.com/windows/desktop/api/d3d12/nn-d3d12-id3d12resource) объектов. |
| [ITensorStaticsNative](native-apis/ITensorStaticsNative.md) | Предоставляет доступ к методам фабрики, которые обеспечивают создание [ITensor](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.itensor) объектов с помощью [ID3D12Resource](https://docs.microsoft.com/windows/desktop/api/d3d12/nn-d3d12-id3d12resource). |

### <a name="structures"></a>Структуры

| Имя | Описание |
|------|-------------|
| [ILearningModelOperatorProviderNative](native-apis/ILearningModelOperatorProviderNative.md) | Предоставляет доступ к [IMLOperatorRegistry](custom-operators/IMLOperatorRegistry.md) объектов, содержащих регистрации пользовательского оператора. |

[!INCLUDE [help](../includes/get-help.md)]
