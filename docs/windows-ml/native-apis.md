---
title: WinML собственные API
description: Этот раздел содержит документацию для собственных API-интерфейсов WinML.
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, машинное обучение Windows, WinML
ms.localizationpriority: medium
ms.openlocfilehash: 6fee01e711fb94681a61914dcc4ec317577689b9
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70156589"
---
# <a name="winml-native-apis"></a>WinML собственные API

Встроенные интерфейсы API Windows Машинное обучение расположены в **Windows. AI. machinelearning. Native. h**.

## <a name="apis"></a>Интерфейсы API

Ниже приведен список собственных API-интерфейсов WinML с их синтаксисом и описаниями.

### <a name="interfaces"></a>Интерфейсы

| Имя | Описание |
|------|-------------|
| [ILearningModelDeviceFactoryNative](native-apis/ILearningModelDeviceFactoryNative.md) | Предоставляет доступ к заводским методам, которые позволяют создавать объекты [илеарнингмоделдевице](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodeldevice) с помощью [ID3D12CommandQueue](https://docs.microsoft.com/windows/desktop/api/d3d12/nn-d3d12-id3d12commandqueue). |
| [ITensorNative](native-apis/ITensorNative.md) | Предоставляет доступ к [итенсор](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.itensor) в виде массива объектов Byte или [ID3D12Resource](https://docs.microsoft.com/windows/desktop/api/d3d12/nn-d3d12-id3d12resource) . |
| [ITensorStaticsNative](native-apis/ITensorStaticsNative.md) | Предоставляет доступ к заводским методам, которые позволяют создавать объекты [итенсор](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.itensor) с помощью [ID3D12Resource](https://docs.microsoft.com/windows/desktop/api/d3d12/nn-d3d12-id3d12resource). |

### <a name="structures"></a>Структуры

| Имя | Описание |
|------|-------------|
| [ILearningModelOperatorProviderNative](native-apis/ILearningModelOperatorProviderNative.md) | Предоставляет доступ к объектам [имлоператоррегистри](custom-operators/IMLOperatorRegistry.md) , содержащим пользовательские регистрации операторов. |

[!INCLUDE [help](../includes/get-help.md)]
