---
author: walrusmcd
title: Производительность машинного Обучения Windows и памяти
description: Узнайте, как повысить производительность приложения, при использовании машинного Обучения Windows.
ms.author: paulm
ms.date: 6/24/2019
ms.topic: article
keywords: windows 10, windows ai, windows ml, winml, windows machine learning
ms.localizationpriority: medium
ms.openlocfilehash: 7b858e143af00ed0bf3c34986b07a0ad1f3dc01d
ms.sourcegitcommit: edfaeda957977f26056b425a5cdda73d7a4f4ea1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/24/2019
ms.locfileid: "67334133"
---
# <a name="windows-ml-performance-and-memory"></a>Производительность машинного Обучения Windows и памяти

В этой статье мы обсудим, как повысить производительность приложения, при использовании Windows машинного обучения.

## <a name="memory-utilization"></a>Уровень использования памяти приложением

Каждый экземпляр [LearningModel](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodel) и [LearningModelSession](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodelsession) имеет копию модели в памяти. Если вы работаете с небольшой моделями, вас может не возникнуть, но если вы работаете с очень большими моделями, это становится важным.

Чтобы освободить память, вызовите **Dispose** на модели или сеанса. Только не удалить их, так как некоторые языки выполняют отложенная сборка мусора.

**LearningModel** будет хранить в памяти, чтобы разрешить создание нового сеанса. Если реализация **LearningModel**, все существующие сеансы будут продолжать работать.  Тем не менее, вы больше нельзя создать новые сеансы с, **LearningModel** экземпляра. Для больших моделей можно создавать модели и сеанса и затем dispose модели. С помощью одного сеанса для всех вызовов [Evaluate](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodelsession.evaluate), вы получите на одну копию такого крупных моделей в памяти.

<!--
<TODO Asynchronous calling patterns>
-->

## <a name="float16-support"></a>Поддержка Float16

Для повышения производительности и объем ограниченной модели, можно использовать [WinMLTools](convert-model-winmltools.md#convert-to-floating-point-16) преобразуемый float16 модели.

После преобразования всех весовые коэффициенты и входные данные являются float16. Вот, как работают float16 входными и выходными данными:

* [ImageFeatureValue](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.imagefeaturevalue)
    * Рекомендуемый способ использования.
    * Преобразует цвета и tensorizes в float16.
    * Поддерживает bgr8 и 8-битовое изображение форматов, которые можно безопасно преобразовать в float16 без потери данных.

* [TensorFloat](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.tensorfloat)
    * Дополнительный путь.
    * Приведение float16 Float32.
    * Для образов это безопасно выполнить приведение, как bgr8 мал и части.
    * Для не образов [привязать](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodelbinding.bind) будет сбой и необходимость передачи в [TensorFloat16Bit](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.tensorfloat16bit) вместо этого.

* [TensorFloat16Bit](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.tensorfloat16bit)
    * Дополнительный путь.
    * Необходимо преобразовать в float16 и передать входные данные в качестве float32, в которой будут приводиться в float16.

> [!NOTE]
> В большинстве случаев, оператор продолжает выполнять математические 32-разрядной. Снижается риск для переполнения, и результат усекается до float16. Тем не менее если оборудование, объявляет поддержку float16, среда выполнения будет использовать его.

## <a name="pre-processing-input-data"></a>Перед обработкой входных данных

WinML выполняет некоторые шаги предварительной обработки, на самом деле для обработки входных данных, проще и эффективнее. Например, данный входные изображения может быть в различных форматов цвета и фигур и может отличаться от ожидает модели. WinML выполняет преобразование изображения в соответствии с их, снижая нагрузку на разработчика.

WinML также использует стек всего оборудования (ЦП, GPU и т. д.) для обеспечения наиболее эффективного преобразования для конкретного устройства и сценария.

Однако в некоторых случаях может потребоваться вручную tensorize входные данные из-за некоторые специфические требования, к которым у вас есть. Например, может быть нежелательно использовать [VideoFrame](https://docs.microsoft.com/uwp/api/windows.media.videoframe) для изображения, или вы хотите, чтобы нормализовать на значениях пикселов из диапазона от 0 до 255 в диапазоне 0 – 1. В таких случаях можно выполнить собственные пользовательские tensorization данных. См. в разделе [пример пользовательской Tensorization](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/CustomTensorization) пример этого.

[!INCLUDE [help](../includes/get-help.md)]
