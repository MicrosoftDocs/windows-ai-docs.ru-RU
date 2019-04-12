---
author: walrusmcd
title: Производительность машинного Обучения Windows и памяти
description: Узнайте, как повысить производительность приложения, при использовании машинного Обучения Windows.
ms.author: paulm
ms.date: 10/02/2018
ms.topic: article
keywords: Windows 10, windows искусственного интеллекта, машинного обучения windows, winml, windows машинное обучение
ms.localizationpriority: medium
ms.openlocfilehash: 2aee4f680fd44f5b99c49e117f87fcc7ba3abf65
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474791"
---
# <a name="windows-ml-performance-and-memory"></a>Производительность машинного Обучения Windows и памяти

В этой статье мы обсудим, как повысить производительность приложения, при использовании машинного Обучения Windows.

## <a name="memory-utilization"></a>Уровень использования памяти приложением

Каждый экземпляр [ **LearningModel** ](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodel) и [ **LearningModelSession** ](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodelsession) имеет копию модели в памяти. Если вы работаете с небольшой моделями, вас может не возникнуть, но если вы работаете с очень большими моделями, это становится важным.

Чтобы освободить память, вызовите Dispose() по модели или сеанса. Только не удалить их, так как некоторые языки выполняют отложенная сборка мусора.

**LearningModel** будет хранить в памяти, чтобы разрешить создание нового сеанса. При реализации LearningModel, все существующие сеансы будут продолжать работать.  Тем не менее вы больше не сможете создавать новые сеансы с этим экземпляром LearningModel. Для больших моделей можно создавать модели и сеанса и затем dispose модели. С помощью одного сеанса для всех вызовов Evaluate(), вы получите на одну копию такого крупных моделей в памяти.

<TODO Asynchronous calling patterns>

## <a name="float16-support"></a>Поддержка Float16

Для повышения производительности и объем ограниченной модели, можно использовать [WinMLTools](convert-model-winmltools.md#convert-to-floating-point-16) преобразуемый float16 модели.

После преобразования всех весовые коэффициенты и входные данные являются float16. Вот, как работают float16 входными и выходными данными:

* [**ImageFeatureValue**](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.imagefeaturevalue)
    * Рекомендуемый способ использования.
    * Преобразует цвета и tensorizes в float16.
    * Поддерживает bgr8 и 8-разрядное форматы изображений, которые можно безопасно преобразовать в float16 без потери данных.  
* [**TensorFloat**](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.tensorfloat)
    * Дополнительный путь.
    * Приведение float16 Float32.
    * Для образов, этом безопасно выполнить приведение, как bgr8 мал и части.
    * Для не образов Bind() завершится ошибкой и будет необходимо передать в TensorFloat16Bit, вместо этого.
* [**TensorFloat16Bit**](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.tensorfloat16bit)
    * Дополнительный путь.
    * Необходимо преобразовать в float16 и передать входные данные в качестве float32, в которой будут приводиться в float16.

**Примечание**. В большинстве случаев, оператор продолжает выполнять математические 32-разрядная версия. Снижается риск для переполнения, и результат усекается до float16. Тем не менее если оборудование, объявляет поддержку float16, среда выполнения будет использовать его.

[!INCLUDE [help](includes/get-help.md)]
