---
title: Имлоператоркернелкреатионконтекст. Хастенсоршапедескриптион, метод
description: Возвращает значение true, если описание входных и выходных фигур, подключенных к краям оператора, может быть запрошено с помощью **жеттенсоршапедескриптион**.
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, машинное обучение Windows, WinML, пользовательские операторы, Хастенсоршапедескриптион
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorKernelCreationContext.HasTensorShapeDescription
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: bee295251bd04c0d7b6bda6bdd6d1f1e835f4543
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157534"
---
# <a name="imloperatorkernelcreationcontexthastensorshapedescription-method"></a>Имлоператоркернелкреатионконтекст. Хастенсоршапедескриптион, метод

Возвращает значение true, если описание входных и выходных фигур, подключенных к краям оператора, может быть запрошено с помощью [имлоператоркернелкреатионконтекст:: жеттенсоршапедескриптион](IMLOperatorKernelCreationContext_GetTensorShapeDescription.md). Это возвращает значение true, если оператор не был зарегистрирован с помощью флага [млоператоркернелоптионс:: алловдинамиЦинпутшапес](MLOperatorKernelOptions.md) .

```cpp
bool HasTensorShapeDescription()
```

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборка 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | Млоператораусор. h |

[!INCLUDE [help](../../includes/get-help.md)]
