---
title: Илеарнингмоделдевицефакторинативе. CreateFromD3D12CommandQueue, метод
description: Создает Леарнингмоделдевице, который будет выполнять вывод на заданном пользователем ID3D12CommandQueue.
ms.date: 4/2/2019
ms.topic: article
keywords: Windows 10, машинное обучение Windows, WinML, CreateFromD3D12CommandQueue
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- ILearningModelDeviceFactoryNative.CreateFromD3D12CommandQueue
api_location:
- windows.ai.machinelearning.native.h
ms.openlocfilehash: bdc255f22d0bafe43d9f8ba9470615a5ce15a5c9
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70156570"
---
# <a name="ilearningmodeldevicefactorynativecreatefromd3d12commandqueue-method"></a>Илеарнингмоделдевицефакторинативе. CreateFromD3D12CommandQueue, метод

Создает [леарнингмоделдевице](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodeldevice) , который будет выполнять вывод на заданном пользователем [ID3D12CommandQueue](https://docs.microsoft.com/windows/desktop/api/d3d12/nn-d3d12-id3d12commandqueue).

```cpp
HRESULT CreateFromD3D12CommandQueue(
    ID3D12CommandQueue * value,
    [out] IUnknown ** result);
```

## <a name="parameters"></a>Параметры

| Имя | Тип | Описание |
|------|------|-------------|
| value | [ID3D12CommandQueue](https://docs.microsoft.com/windows/desktop/api/d3d12/nn-d3d12-id3d12commandqueue)* | **ID3D12CommandQueue** , для которого будет выполняться **леарнингмоделдевице** . |
| результат | [IUnknown](https://docs.microsoft.com/windows/desktop/api/unknwn/nn-unknwn-iunknown)** | Создаваемый **леарнингмоделдевице** . |

## <a name="returns"></a>Возвращает

**Значение HRESULT** Результат операции.

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

* [Пользовательский пример Тенсоризатион](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/CustomTensorization)

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборка 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | Windows. AI. machinelearning. Native. h |

[!INCLUDE [help](../../includes/get-help.md)]
