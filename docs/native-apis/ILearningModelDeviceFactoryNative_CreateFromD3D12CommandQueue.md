---
author: eliotcowley
title: Метод ILearningModelDeviceFactoryNative.CreateFromD3D12CommandQueue
description: Создает LearningModelDevice, который будет выполняться вывод на ID3D12CommandQueue определяемое пользователем.
ms.author: elcowle
ms.date: 11/8/2018
ms.topic: article
keywords: Windows 10, windows машинного обучения, WinML, CreateFromD3D12CommandQueue
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- ILearningModelDeviceFactoryNative.CreateFromD3D12CommandQueue
api_location:
- windows.ai.machinelearning.native.h
ms.openlocfilehash: 1061c2fd3cb5ca662bca0bcb2945631f2d3c8dc2
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474011"
---
# <a name="ilearningmodeldevicefactorynativecreatefromd3d12commandqueue-method"></a>Метод ILearningModelDeviceFactoryNative.CreateFromD3D12CommandQueue

Создает [LearningModelDevice](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodeldevice) вывода, которые будут работать на определяемый пользователем [ID3D12CommandQueue](https://docs.microsoft.com/windows/desktop/api/d3d12/nn-d3d12-id3d12commandqueue).

```cpp
HRESULT CreateFromD3D12CommandQueue(
    ID3D12CommandQueue * value, 
    [out] IUnknown ** result);
```

## <a name="parameters"></a>Параметры

| Имя | Тип | Описание |
|------|------|-------------|
| value | [ID3D12CommandQueue](https://docs.microsoft.com/windows/desktop/api/d3d12/nn-d3d12-id3d12commandqueue)* | **ID3D12CommandQueue** которой **LearningModelDevice** будет выполняться. |
| результат | [IUnknown](https://docs.microsoft.com/windows/desktop/api/unknwn/nn-unknwn-iunknown)** | **LearningModelDevice** должен быть создан. |

## <a name="returns"></a>Возвращает

**HRESULT** результат операции.

## <a name="examples"></a>Примеры

```cpp
 // 1. create the d3d device.
com_ptr<ID3D12Device> pD3D12Device = nullptr;
CHECK_HRESULT(D3D12CreateDevice(
    nullptr, 
    D3D_FEATURE_LEVEL::D3D_FEATURE_LEVEL_11_0, 
    __uuidof(ID3D12Device), 
    reinterpret_cast<void**>(&pD3D12Device)));

// 2. create the command queue.
com_ptr<ID3D12CommandQueue> dxQueue = nullptr;
D3D12_COMMAND_QUEUE_DESC commandQueueDesc = {};
commandQueueDesc.Type = D3D12_COMMAND_LIST_TYPE_DIRECT;
CHECK_HRESULT(pD3D12Device->CreateCommandQueue(
    &commandQueueDesc, 
    __uuidof(ID3D12CommandQueue), 
    reinterpret_cast<void**>(&dxQueue)));
com_ptr<ILearningModelDeviceFactoryNative> devicefactory = 
    get_activation_factory<LearningModelDevice, ILearningModelDeviceFactoryNative>();
com_ptr<::IUnknown> spUnk;
CHECK_HRESULT(devicefactory->CreateFromD3D12CommandQueue(dxQueue.get(), spUnk.put()));
```

## <a name="see-also"></a>См. также

* [Пример пользовательского Tensorization](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/CustomTensorization)

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальная версия клиента** | Windows 10, сборки 17763 |
| **Минимальная версия сервера** | Windows Server 2019 с возможностями рабочего стола |
| **Header** | Windows.AI.machinelearning.Native.h |

[!INCLUDE [help](../includes/get-help.md)]
