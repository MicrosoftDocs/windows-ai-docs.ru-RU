---
author: rosanevallim
title: Получить моделями ONNX для машинного Обучения Windows
description: Машинное Обучение Windows оценивает моделей в формат ONNX, позволяя обмена моделей в различных платформ машинного Обучения и средства.
ms.author: rovalli
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10, windows ai, windows ml, winml, windows machine learning
ms.localizationpriority: medium
ms.openlocfilehash: ca8140389f416001314e9000121ed99f7d6da112
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66181196"
---
# <a name="get-onnx-models-for-windows-ml"></a>Получить моделями ONNX для машинного Обучения Windows

Машинное Обучение Windows оценивает моделей в [откройте нейронной сети Exchange (ONNX)](https://onnx.ai) формат. ONNX есть открытом формате для моделей машинного Обучения, позволяя обмена моделей между различными [платформ машинного Обучения и средства](http://onnx.ai/supported-tools).

> [!IMPORTANT]
> Машинное Обучение Windows требует моделями ONNX [версии 1.2](https://github.com/onnx/onnx/tree/rel-1.2.2) или более поздней версии.

Чтобы получить модель ONNX для использования с машинным Обучением Windows, вы можете:

- Скачать предварительно обученной модели ONNX из [Zoo модели ONNX](https://github.com/onnx/models).
- Обучение модели с помощью служб, таких как [пользовательская служба визуального распознавания Azure](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/getting-started-build-a-classifier), [машинного обучения Azure](https://azure.microsoft.com/overview/machine-learning/), или [инструменты Visual STUDIO для ии](https://visualstudio.microsoft.com/downloads/ai-tools-vs/)и экспортировать в формат ONNX.
    - Чтобы узнать, как обучить модель в облаке, используя настраиваемый концепции, извлечь [руководства: Использовать модель ONNX из Custom Vision с машинным Обучением Windows (Предварительная версия)](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/custom-vision-onnx-windows-ml).
- Преобразование модели, обучение в других платформ машинного Обучения в формат ONNX с [WinMLTools](convert-model-winmltools.md) преобразователи типов или [ONNX учебники](https://github.com/onnx/tutorials).

При наличии модели ONNX, вы будете [интегрировать модели](integrate-model.md) в коде приложения, а затем будет иметь возможность использовать машинное обучение в приложениях Windows и устройств!

[!INCLUDE [help](../includes/get-help.md)]
