---
author: eliotcowley
title: Пользовательские операторы
description: Этот раздел содержит документацию для пользовательского оператора API-интерфейсов Win32.
ms.author: elcowle
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, windows машинного обучения, WinML, пользовательские операторы
ms.localizationpriority: medium
ms.openlocfilehash: 5f901b97f392278cad101b0581813cbcd32fcf80
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66180896"
---
# <a name="custom-operators"></a>Пользовательские операторы

Пользовательский оператор машинного обучения Windows API-интерфейсов Win32, находятся в **MLOperatorAuthor.h**.

## <a name="apis"></a>Интерфейсы API

Ниже приведен список интерфейсов API с их синтаксис и описания пользовательского оператора.

### <a name="enumerations"></a>Перечисления

| Имя | Описание |
|------|-------------|
| [MLOperatorAttributeType](custom-operators/MLOperatorAttributeType.md) | Указывает тип атрибута. Каждый тип атрибута соответствует числовом виде соответствующего типа ONNX. |
| [MLOperatorEdgeType](custom-operators/MLOperatorEdgeType.md) | Указывает типы ребро входного или выходного оператора. |
| [MLOperatorExecutionType](custom-operators/MLOperatorExecutionType.md) | Указывает, использует ли ядро ЦП или GPU для вычислений. |
| [MLOperatorKernelOptions](custom-operators/MLOperatorKernelOptions.md) | Определяет параметры, используемые при регистрации пользовательского оператора ядра. |
| [MLOperatorParameterOptions](custom-operators/MLOperatorParameterOptions.md) | Указывает флаги параметров, входных и выходных границ операторов. |
| [MLOperatorSchemaEdgeTypeFormat](custom-operators/MLOperatorSchemaEdgeTypeFormat.md) | Указывает способ, в какие типы входных и выходных данных описаны краев. |
| [MLOperatorTensorDataType](custom-operators/MLOperatorTensorDataType.md) | Указывает тип данных тензорные. Каждый тип данных соответствует числовом виде соответствующего типа ONNX. |

### <a name="functions"></a>Функции

| Имя | Описание |
|------|-------------|
| [MLCreateOperatorRegistry](custom-operators/MLCreateOperatorRegistry.md) | Создает экземпляр класса [IMLOperatorRegistry](custom-operators/IMLOperatorRegistry.md) которого может использоваться для регистрации пользовательского оператора ядра и схемы пользовательского оператора. |

### <a name="interfaces"></a>Интерфейсы

| Имя | Описание |
|------|-------------|
| [IMLOperatorAttributes](custom-operators/IMLOperatorAttributes.md) | Представляет значения атрибутов оператора, как определено в модели, с помощью оператора. |
| [IMLOperatorKernel](custom-operators/IMLOperatorKernel.md) | Реализуется ядра пользовательского оператора. |
| [IMLOperatorKernelContext](custom-operators/IMLOperatorKernelContext.md) | Предоставляет сведения об использовании оператора, хотя вычисляются ядра. |
| [IMLOperatorKernelCreationContext](custom-operators/IMLOperatorKernelCreationContext.md) | Предоставляет сведения об использовании оператора, при создании ядра. |
| [IMLOperatorKernelFactory](custom-operators/IMLOperatorKernelFactory.md) | Реализованы автором ядра пользовательского оператора для создания экземпляров этого ядра. |
| [IMLOperatorRegistry](custom-operators/IMLOperatorRegistry.md) | Представляет экземпляр реестра для пользовательского оператора ядра и схемы. |
| [IMLOperatorShapeInferenceContext](custom-operators/IMLOperatorShapeInferenceContext.md) | Предоставляет сведения об использовании оператора, хотя вызываются inferrers фигуры. |
| [IMLOperatorShapeInferrer](custom-operators/IMLOperatorShapeInferrer.md) | Реализуется inferrers фигуры вывести фигур границ тензорные выходные данные оператора. |
| [IMLOperatorTensor](custom-operators/IMLOperatorTensor.md) | Представление тензорные, используемых при вычислениях ядер пользовательского оператора. |
| [IMLOperatorTensorShapeDescription](custom-operators/IMLOperatorTensorShapeDescription.md) | Представляет набор фигур входных и выходных тензорные оператора. |
| [IMLOperatorTypeInferenceContext](custom-operators/IMLOperatorTypeInferenceContext.md) | Предоставляет сведения об использовании оператора, хотя вызываются inferrers типа. |
| [IMLOperatorTypeInferrer](custom-operators/IMLOperatorTypeInferrer.md) | Реализованный тип inferrers определить типы оператора выходных краев. |

### <a name="structures"></a>Структуры

| Имя | Описание |
|------|-------------|
| [MLOperatorAttribute](custom-operators/MLOperatorAttribute.md) | Указывает имя и свойства атрибута пользовательского оператора. |
| [MLOperatorAttributeNameValue](custom-operators/MLOperatorAttributeNameValue.md) | Указывает имя и значения атрибута для пользовательского оператора. |
| [MLOperatorEdgeDescription](custom-operators/MLOperatorEdgeDescription.md) | Задает свойства границы входного или выходного оператора. |
| [MLOperatorEdgeTypeConstraint](custom-operators/MLOperatorEdgeTypeConstraint.md) | Задает ограничения по типам краев, поддерживается в пользовательского оператора ядра и схемы. |
| [MLOperatorKernelDescription](custom-operators/MLOperatorKernelDescription.md) | Описание пользовательского оператора ядра, используемые для регистрации этой схемы. |
| [MLOperatorSchemaDescription](custom-operators/MLOperatorSchemaDescription.md) | Описание схемы пользовательский оператор, используемый для регистрации этой схемы. |
| [MLOperatorSchemaEdgeDescription](custom-operators/MLOperatorSchemaEdgeDescription.md) | Указывает сведения о ребро входного или выходного оператора. |
| [MLOperatorSetId](custom-operators/MLOperatorSetId.md) | Задает удостоверение оператор набора. |

[!INCLUDE [help](../includes/get-help.md)]
