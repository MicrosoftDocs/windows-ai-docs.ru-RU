---
author: rosanevallim
title: Получить моделями ONNX для машинного Обучения Windows
description: Машинное Обучение Windows оценивает моделей в формат ONNX, позволяя обмена моделей в различных платформ машинного Обучения и средства.
ms.author: rovalli
ms.date: 2/20/2019
ms.topic: article
keywords: Windows 10, windows искусственного интеллекта, машинного обучения windows, winml, windows машинное обучение
ms.localizationpriority: medium
ms.openlocfilehash: adc7bd875a40ebd44043799ab6e52fe7252e3f15
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474101"
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

[!INCLUDE [help](includes/get-help.md)]
