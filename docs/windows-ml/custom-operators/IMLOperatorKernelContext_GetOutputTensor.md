---
title: Имлоператоркернелконтекст. Жетаутпуттенсор, метод
description: Возвращает выходной тензорные оператора по указанному индексу.
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, машинное обучение Windows, WinML, пользовательские операторы, Жетаутпуттенсор
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorKernelContext.GetOutputTensor
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 3755c292420d858ebef696fd422bb8b705809d0c
ms.sourcegitcommit: 841189060a505c15cf6b1d7d20419648afc20b9c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/24/2020
ms.locfileid: "80160087"
---
# <a name="imloperatorkernelcontextgetoutputtensor-method"></a>Имлоператоркернелконтекст. Жетаутпуттенсор, метод

## <a name="overloads"></a>Перегрузки

| | |
|-|-|
| [Жетаутпуттенсор (uint32_t, Имлоператортенсор * *)](#GetOutputTensor1) | Возвращает выходной тензорные оператора по указанному индексу. |
| [Жетаутпуттенсор (uint32_t, uint32_t, const uint32_t *, Имлоператортенсор * *)](#GetOutputTensor2) | Возвращает выходной тензорные оператора по указанному индексу при объявлении его фигуры. |

<a name="GetOutputTensor1"></a>
## <a name="getoutputtensoruint32_t-imloperatortensor"></a>GetOutputTensor(uint32_t, IMLOperatorTensor**)

Возвращает выходной тензорные оператора по указанному индексу. Это устанавливает тензорные в значение **nullptr** для необязательных выходов, которые не существуют. Если ядро оператора зарегистрировано без метода определения формы, то перегрузка **жетаутпуттенсор** , которая использует форму тензорные, должна вызываться. Возвращает ошибку, если выходные данные по указанному индексу не являются тензорные.

```cpp
void GetOutputTensor(
    uint32_t outputIndex,
    _COM_Outptr_result_maybenull_ IMLOperatorTensor** tensor)
```

<a name="GetOutputTensor2"></a>
## <a name="getoutputtensoruint32_t-uint32_t-const-uint32_t-imloperatortensor"></a>GetOutputTensor(uint32_t, uint32_t, const uint32_t*, IMLOperatorTensor**)

Возвращает выходной тензорные оператора по указанному индексу при объявлении его фигуры. Это возвращает **nullptr** для необязательных выходов, которые не существуют. Если ядро оператора зарегистрировано в методе определения формы, то перегрузка **жетаутпуттенсор** , которая не потребляет фигуру, также может быть вызвана. Возвращает ошибку, если выходные данные по указанному индексу не являются тензорные.

```cpp
void GetOutputTensor(
    uint32_t outputIndex,
    uint32_t dimensionCount,
    _In_reads_(dimensionCount) const uint32_t* dimensionSizes,
    _COM_Outptr_result_maybenull_ IMLOperatorTensor** tensor)
```

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборка 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | Млоператораусор. h |

[!INCLUDE [help](../../includes/get-help.md)]
