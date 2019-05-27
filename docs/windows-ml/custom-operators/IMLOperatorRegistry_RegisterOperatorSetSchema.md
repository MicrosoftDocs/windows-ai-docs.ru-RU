---
author: eliotcowley
title: Метод IMLOperatorRegistry.RegisterOperatorSetSchema
description: Регистрирует набор схемы пользовательского оператора, включающего в себя набор оператор.
ms.author: elcowle
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, windows машинного обучения, WinML, настраиваемые операторы, RegisterOperatorSetSchema
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorRegistry.RegisterOperatorSetSchema
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: bb7778112cbc54f4bf13150f4a132b17f3b68681
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66180696"
---
# <a name="imloperatorregistryregisteroperatorsetschema-method"></a>Метод IMLOperatorRegistry.RegisterOperatorSetSchema

Регистрирует набор схемы пользовательского оператора, включающего в себя набор оператор. Задает оператор проектировании управления версиями ONNX. Вызывающие объекты должны предоставить схему для всех операторов, которые изменились между версией указанной базовой версии и версии, указанной в *operatorSetId*. Это предотвращает использование в модели, благодаря которым импорта новой версии набора оператор более старых версиях ядер. Inferrer типа должно быть указано, если [MLOperatorSchemaDescription](MLOperatorSchemaDescription.md) структура не может представлять, как определяются типы выходных данных. Для проверки модели, можно дополнительно указать inferrer фигуры.

```cpp
void RegisterOperatorSetSchema(
    const MLOperatorSetId* operatorSetId,
    int32_t baselineVersion,
    _In_reads_opt_(schemaCount) const MLOperatorSchemaDescription* const* schema,
    uint32_t schemaCount,
    _In_opt_ IMLOperatorTypeInferrer* typeInferrer,
    _In_opt_ IMLOperatorShapeInferrer* shapeInferrer)
```

## <a name="requirements"></a>Требования

| | |
|-|-|
| **Минимальный поддерживаемый клиент** | Windows 10, сборки 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
