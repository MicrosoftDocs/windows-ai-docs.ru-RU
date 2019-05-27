---
author: eliotcowley
title: Метод IMLOperatorTensor.GetDataInterface
description: Возвращает указатель интерфейса для тензорные.
ms.author: elcowle
ms.date: 4/1/2019
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
ms.openlocfilehash: c57f09e7c041343f67587892757754d78baa43ad
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66180606"
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
| **Минимальный поддерживаемый клиент** | Windows 10, сборки 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
