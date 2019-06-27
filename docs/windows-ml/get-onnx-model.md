---
author: rosanevallim
title: Модели ONNX
description: Машинное Обучение Windows оценивает моделей в формат ONNX, позволяя обмена моделей в различных платформ машинного Обучения и средства.
ms.author: rovalli
ms.date: 6/5/2019
ms.topic: article
keywords: Windows 10, windows искусственного интеллекта, машинного обучения windows, winml, машинного обучения windows, onnx
ms.localizationpriority: medium
ms.openlocfilehash: 35baba048337402f3ed8ceafe79115423962bcba
ms.sourcegitcommit: 12993277cf7f97c9c6a02908e4a4f1f91b689edb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/06/2019
ms.locfileid: "66740492"
---
# <a name="onnx-models"></a>Модели ONNX

Машинное обучение Windows поддерживает моделей в [откройте нейронной сети Exchange (ONNX)](https://onnx.ai/) формат. ONNX есть открытом формате для моделей машинного Обучения, позволяя обмена моделей между различными [платформ машинного Обучения и средства](https://onnx.ai/supported-tools).

Существует несколько способов, в которых можно получить модели в формат ONNX, включая:

- [Zoo модели ONNX](https://github.com/onnx/models): Содержит несколько предварительно обученные модели ONNX для различных типов задач. Скачайте версию, которая поддерживается машинного Обучения Windows и приступать к работе!

- [Собственного экспорта из платформы обучения ML](https://onnx.ai/supported-tools): Несколько платформ обучения поддерживает возможность собственного экспорта ONNX, например формирователя цепочки, Caffee2 и PyTorch, позволяя сохранять обученной модели к конкретным версиям в формат ONNX. Кроме того, службы, такие как [службы машинного обучения Azure](https://azure.microsoft.com/services/machine-learning-service/) и [Azure Custom Vision](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/getting-started-build-a-classifier) также предоставляют собственный ONNX экспорта.
    - Чтобы узнать, как обучать и экспортировать модели ONNX в облаке, используя настраиваемый концепции, извлечь [руководства: Использовать модель ONNX из Custom Vision с машинным Обучением Windows (Предварительная версия)](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/custom-vision-onnx-windows-ml).

- [Преобразование существующих моделей, с помощью WinMLTools](https://docs.microsoft.com/windows/ai/windows-ml/convert-model-winmltools): Этот пакет Python, можно преобразовать из нескольких форматов framework обучения ONNX моделей. Как разработчик можно указать версию ONNX, вы хотите преобразовать модели, в зависимости от того, какие сборки ваше приложение предназначено для Windows. Если вы не знакомы с Python, можно использовать [панели мониторинга на основе пользовательского интерфейса машинного Обучения Windows](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Tools/WinMLDashboard) чтобы без труда Выполняйте преобразование моделей с помощью нескольких щелчков.

> [!IMPORTANT]
> Не все версии ONNX поддерживаются Windows машинного Обучения. Чтобы узнать, какие версии ONNX официально поддерживаются в версиях Windows, используемая в приложении, ознакомьтесь с [ONNX версии и Windows создает](onnx-versions.md).

При наличии модели ONNX, вы будете [интегрировать модели](https://docs.microsoft.com/windows/ai/windows-ml/integrate-model) в коде приложения, а затем будет иметь возможность использовать машинное обучение в приложениях Windows и устройств!

[!INCLUDE [help](../includes/get-help.md)]
