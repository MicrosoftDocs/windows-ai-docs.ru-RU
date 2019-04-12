---
author: eliotcowley
title: Метод IMLOperatorTensor.GetDataInterface
description: Возвращает указатель интерфейса для тензорные.
ms.author: elcowle
ms.date: 11/8/2018
ms.topic: article
keywords: Windows 10, windows машинного обучения, WinML, настраиваемые операторы, GetDataInterface
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorTensor.GetDataInterface
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: fc434a519ce895b8cb5cc0e3bd2d96884e9bda0b
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474401"
---
# <a name="imloperatortensorgetdatainterface-method"></a>Метод IMLOperatorTensor.GetDataInterface

Возвращает указатель интерфейса для тензорные. Это может быть, используемого при [IMLOperatorTensor::IsDataInterface](IMLOperatorTensor_IsDataInterface.md) возвращается значение true, так как ядро был зарегистрирован с помощью [MLOperatorExecutionType::D3D12](MLOperatorExecutionType.md). *DataInterface* поддерживает [ID3D12Resource интерфейс](https://docs.microsoft.com/windows/desktop/api/d3d12/nn-d3d12-id3d12resource), и является буфером GPU.

```cpp
void GetDataInterface(
    _COM_Outptr_result_maybenull_ IUnknown** dataInterface)
```

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальная версия клиента** | Windows 10, сборки 17763 |
| **Минимальная версия сервера** | Windows Server 2019 с возможностями рабочего стола |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
