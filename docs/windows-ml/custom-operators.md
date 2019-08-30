---
title: Пользовательские операторы
description: Этот раздел содержит документацию для пользовательских операторов Win32 API.
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, машинное обучение Windows, WinML, пользовательские операторы
ms.localizationpriority: medium
ms.openlocfilehash: 188d6aa5000f60954b91a980dc02d500557c2d90
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157051"
---
# <a name="custom-operators"></a>Пользовательские операторы

API-интерфейсы Win32 настраиваемого оператора Windows Машинное обучение находятся в **млоператораусор. h**.

## <a name="apis"></a>Интерфейсы API

Ниже приведен список API-интерфейсов пользовательских операторов с их синтаксисом и описаниями.

### <a name="enumerations"></a>Перечисления

| Имя | Описание |
|------|-------------|
| [MLOperatorAttributeType](custom-operators/MLOperatorAttributeType.md) | Указывает тип атрибута. Каждый тип атрибута в числовом соответствии с соответствующим типом ONNX. |
| [MLOperatorEdgeType](custom-operators/MLOperatorEdgeType.md) | Указывает типы входного или выходного края оператора. |
| [MLOperatorExecutionType](custom-operators/MLOperatorExecutionType.md) | Указывает, использует ли ядро ЦП или GPU для вычислений. |
| [MLOperatorKernelOptions](custom-operators/MLOperatorKernelOptions.md) | Указывает параметры, используемые при регистрации ядер пользовательских операторов. |
| [MLOperatorParameterOptions](custom-operators/MLOperatorParameterOptions.md) | Задает флаги параметров входных и выходных границ операторов. |
| [MLOperatorSchemaEdgeTypeFormat](custom-operators/MLOperatorSchemaEdgeTypeFormat.md) | Указывает способ описания типов входных и выходных границ. |
| [MLOperatorTensorDataType](custom-operators/MLOperatorTensorDataType.md) | Указывает тип данных тензорные. Каждый тип данных в числовом соответствии с соответствующим типом ONNX. |

### <a name="functions"></a>Функции

| Имя | Описание |
|------|-------------|
| [MLCreateOperatorRegistry](custom-operators/MLCreateOperatorRegistry.md) | Создает экземпляр [имлоператоррегистри](custom-operators/IMLOperatorRegistry.md) , который может использоваться для регистрации пользовательского оператора ядра и схемы пользовательского оператора. |

### <a name="interfaces"></a>Интерфейсы

| Имя | Описание |
|------|-------------|
| [IMLOperatorAttributes](custom-operators/IMLOperatorAttributes.md) | Представляет значения атрибутов оператора, как определено моделью с помощью оператора. |
| [IMLOperatorKernel](custom-operators/IMLOperatorKernel.md) | Реализуется с помощью пользовательских ядер операторов. |
| [IMLOperatorKernelContext](custom-operators/IMLOperatorKernelContext.md) | Предоставляет сведения об использовании оператора при вычислении ядра. |
| [IMLOperatorKernelCreationContext](custom-operators/IMLOperatorKernelCreationContext.md) | Предоставляет сведения об использовании оператора во время создания ядер. |
| [IMLOperatorKernelFactory](custom-operators/IMLOperatorKernelFactory.md) | Реализуется автором пользовательского оператора в ядре для создания экземпляров этого ядра. |
| [IMLOperatorRegistry](custom-operators/IMLOperatorRegistry.md) | Представляет экземпляр реестра для ядра и схемы пользовательского оператора. |
| [IMLOperatorShapeInferenceContext](custom-operators/IMLOperatorShapeInferenceContext.md) | Предоставляет сведения об использовании оператора во время вызова ссылок на фигурные источники. |
| [IMLOperatorShapeInferrer](custom-operators/IMLOperatorShapeInferrer.md) | Реализуется с помощью фигурных источников, чтобы вывести фигуры выходных тензорные границ оператора. |
| [IMLOperatorTensor](custom-operators/IMLOperatorTensor.md) | Представление тензорные, используемое при вычислении ядер пользовательских операторов. |
| [IMLOperatorTensorShapeDescription](custom-operators/IMLOperatorTensorShapeDescription.md) | Представляет набор входных и выходных тензорные фигур оператора. |
| [IMLOperatorTypeInferenceContext](custom-operators/IMLOperatorTypeInferenceContext.md) | Предоставляет сведения об использовании оператора во время вызова источников ссылок типов. |
| [IMLOperatorTypeInferrer](custom-operators/IMLOperatorTypeInferrer.md) | Реализуется по типам источников ссылок для определения типов краев выходных данных оператора. |

### <a name="structures"></a>Структуры

| Имя | Описание |
|------|-------------|
| [MLOperatorAttribute](custom-operators/MLOperatorAttribute.md) | Задает имя и свойства атрибута пользовательского оператора. |
| [MLOperatorAttributeNameValue](custom-operators/MLOperatorAttributeNameValue.md) | Задает имя и значение (-ов) атрибута пользовательского оператора. |
| [MLOperatorEdgeDescription](custom-operators/MLOperatorEdgeDescription.md) | Задает свойства границы входного или выходного объекта оператора. |
| [MLOperatorEdgeTypeConstraint](custom-operators/MLOperatorEdgeTypeConstraint.md) | Задает ограничения для типов краев, поддерживаемых в ядрах и схемах пользовательских операторов. |
| [MLOperatorKernelDescription](custom-operators/MLOperatorKernelDescription.md) | Описание ядра пользовательского оператора, используемого для регистрации этой схемы. |
| [MLOperatorSchemaDescription](custom-operators/MLOperatorSchemaDescription.md) | Описание схемы пользовательского оператора, используемой для регистрации этой схемы. |
| [MLOperatorSchemaEdgeDescription](custom-operators/MLOperatorSchemaEdgeDescription.md) | Задает сведения о внешнем входном или выходном крае оператора. |
| [MLOperatorSetId](custom-operators/MLOperatorSetId.md) | Задает удостоверение набора операторов. |

[!INCLUDE [help](../includes/get-help.md)]
