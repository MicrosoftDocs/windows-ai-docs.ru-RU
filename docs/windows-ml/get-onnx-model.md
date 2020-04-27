---
author: rosanevallim
title: Модели ONNX
description: Windows ML оценивает модели в формате ONNX, что позволяет перемещать модели между разными платформами и инструментами машинного обучения.
ms.author: rovalli
ms.date: 6/5/2019
ms.topic: article
keywords: windows 10, windows ai, windows ml, winml, windows machine learning, onnx
ms.localizationpriority: medium
ms.openlocfilehash: d1b43ca0f0ea47b81ff29e3e196fc77c5319c647
ms.sourcegitcommit: 2139506ff12b7205283288c4bbac866ddfa812f3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/24/2020
ms.locfileid: "75737417"
---
# <a name="onnx-models"></a>Модели ONNX

Windows Machine Learning поддерживает модели в формате [ONNX (Open Neural Network Exchange)](https://onnx.ai/). Открытый формат моделей машинного обучения ONNX позволяет перемещать модели между разными [платформами и инструментами машинного обучения](https://onnx.ai/supported-tools).

Есть несколько способов получить модель в формате ONNX, часть из которых перечислена далее.

- [ONNX Model Zoo](https://github.com/onnx/models). Содержит несколько предварительно обученных моделей ONNX для разных типов задач. Скачайте версию, поддерживаемую Машинным обучением Windows, и можно сразу приступать к работе.

- [Встроенные функции экспорта из платформ обучения для машинного обучения](https://onnx.ai/supported-tools). Некоторые платформы обучения, например Chainer, Caffee2 и PyTorch, имеют собственные компоненты экспорта в ONNX, что позволяет сохранять обученную модель в определенных версиях формата ONNX. Кроме того, встроенная поддержка ONNX реализована в таких службах, как [Машинное обучение Azure](https://azure.microsoft.com/services/machine-learning-service/) и [Пользовательское визуальное распознавание Azure](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/getting-started-build-a-classifier).
    - Сведения о том, как обучать и экспортировать модель ONNX в облаке с помощью службы "Пользовательское визуальное распознавание", вы найдете в [руководстве по использованию модели ONNX из службы "Пользовательское визуальное распознавание" в Windows ML (предварительная версия)](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/custom-vision-onnx-windows-ml).

- [Преобразование существующих моделей с помощью WinMLTools](https://docs.microsoft.com/windows/ai/windows-ml/convert-model-winmltools). Этот пакет Python позволяет преобразовывать в ONNX модели нескольких форматов разных платформ обучения. Разработчик может указать, в какую версию ONNX нужно преобразовать модель, с учетом целевой сборки Windows для вашего приложения. Если вы не знакомы с Python, попробуйте применить [панели мониторинга на основе пользовательского интерфейса Машинного обучения Windows](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Tools/WinMLDashboard), чтобы несколькими щелчками мыши преобразовать существующие модели.

> [!IMPORTANT]
> Не все версии ONNX поддерживаются в Windows ML. Чтобы узнать, какие версии ONNX официально поддерживаются теми версиями Windows, для которых предназначено ваше приложение, просмотрите [этот список](onnx-versions.md).

После создания модели ONNX ее можно [интегрировать](https://docs.microsoft.com/windows/ai/windows-ml/integrate-model) в код приложения, после чего вы сможете использовать машинное обучение в приложениях и на устройствах Windows.

[!INCLUDE [help](../includes/get-help.md)]
