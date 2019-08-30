---
title: Интерфейс Имлоператортенсоршапедескриптион
description: Представляет набор входных и выходных тензорные фигур оператора.
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, машинное обучение Windows, WinML, пользовательские операторы, Имлоператортенсоршапедескриптион
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorTensorShapeDescription
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 17f8c02a79d71bb6265e4c9d2061014db2454fcb
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157837"
---
# <a name="imloperatortensorshapedescription-interface"></a>Интерфейс Имлоператортенсоршапедескриптион

Представляет набор входных и выходных тензорные фигур оператора. Этот интерфейс вызывается объектами фабрики, зарегистрированными для создания ядер. Он доступен для этих объектов фабрики, если соответствующие ядра не зарегистрированы с помощью флага [млоператоркернелоптионс:: алловдинамиЦинпутшапес](MLOperatorKernelOptions.md) .

## <a name="methods"></a>Методы

| Имя | Описание |
|------|-------------|
| [GetInputTensorDimensionCount](IMLOperatorTensorShapeDescription_GetInputTensorDimensionCount.md) | Возвращает количество измерений тензорные входных данных оператора. |
| [GetInputTensorShape](IMLOperatorTensorShapeDescription_GetInputTensorShape.md) | Возвращает размеры измерений входного тензорные оператора. |
| [GetOutputTensorDimensionCount](IMLOperatorTensorShapeDescription_GetOutputTensorDimensionCount.md) | Возвращает число измерений тензорные выходных данных оператора. |
| [GetOutputTensorShape](IMLOperatorTensorShapeDescription_GetOutputTensorShape.md) | Возвращает размеры размеров тензорные выходных данных оператора. |
| [HasOutputShapeDescription](IMLOperatorTensorShapeDescription_HasOutputShapeDescription.md) | Возвращает значение true, если выходные формы можно запрашивать с помощью **жетаутпуттенсордименсионкаунт** и **жетаутпуттенсоршапе**. |

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборка 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | Млоператораусор. h |

[!INCLUDE [help](../../includes/get-help.md)]
