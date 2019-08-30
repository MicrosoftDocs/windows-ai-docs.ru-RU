---
title: Имлоператоррегистри. Регистероператорсетсчема, метод
description: Регистрирует набор пользовательских схем операторов, включающих набор операторов.
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, машинное обучение Windows, WinML, пользовательские операторы, Регистероператорсетсчема
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorRegistry.RegisterOperatorSetSchema
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: f8746ecd7c58b759f7c46115759f4f977c1578a8
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157625"
---
# <a name="imloperatorregistryregisteroperatorsetschema-method"></a>Имлоператоррегистри. Регистероператорсетсчема, метод

Регистрирует набор пользовательских схем операторов, включающих набор операторов. Наборы операторов соответствуют проекту управления версиями ONNX. Вызывающие объекты должны предоставить схему для всех операторов, которые изменились между указанной базовой версией и версией, указанной в *операторсетид*. Это предотвращает использование старых версий ядра в моделях, которые импортируют новую версию набора операторов. Если структура [млоператорсчемадескриптион](MLOperatorSchemaDescription.md) не может выразить, как определяются типы вывода, необходимо указать источник ссылок типа. Для включения проверки модели можно дополнительно предоставить ссылки на фигурные источники.

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
| **Минимальный поддерживаемый клиент** | Windows 10, сборка 17763 |
| **Минимальный поддерживаемый сервер** | Windows Server 2019 с возможностями рабочего стола |
| **Заголовок** | Млоператораусор. h |

[!INCLUDE [help](../../includes/get-help.md)]
