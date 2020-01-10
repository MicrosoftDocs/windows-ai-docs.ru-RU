---
author: rosanevallim
title: Модели ONNX
description: Windows ML оценивает модели в формате ONNX, позволяя использовать модели для обмена моделями между различными платформами и инструментами машинного обучения.
ms.author: rovalli
ms.date: 6/5/2019
ms.topic: article
keywords: Windows 10, Windows AI, Windows ml, winml, машинное обучение Windows, onnx
ms.localizationpriority: medium
ms.openlocfilehash: d1b43ca0f0ea47b81ff29e3e196fc77c5319c647
ms.sourcegitcommit: ecd33843dd548e443a1292d6a22e1a4029298944
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2020
ms.locfileid: "75737417"
---
# <a name="onnx-models"></a>Модели ONNX

Windows Машинное обучение поддерживает модели в формате [открытого нейронного сетевого обмена (ONNX)](https://onnx.ai/) . ONNX — это открытый формат для моделей машинного обучения, позволяющий выполнять обмен моделями между различными [платформами и инструментами машинного обучения](https://onnx.ai/supported-tools).

Существует несколько способов получить модель в формате ONNX, включая:

- [ONNX Model Zoo](https://github.com/onnx/models): содержит несколько предварительно обученных моделей ONNX для различных типов задач. Скачайте версию, поддерживаемую Windows ML, и все готово к работе.

- [Собственный экспорт из платформ обучения ML](https://onnx.ai/supported-tools). несколько платформ обучения поддерживают собственные функции экспорта в ONNX, такие как chaining, Caffee2 и PyTorch, что позволяет сохранить обученную модель в определенных версиях формата ONNX. Кроме того, такие службы, как [машинное обучение Azure](https://azure.microsoft.com/services/machine-learning-service/) и [Azure пользовательское визуальное распознавание](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/getting-started-build-a-classifier) , также предоставляют собственный экспорт ONNX.
    - Сведения о том, как обучать и экспортировать модель ONNX в облаке с помощью Пользовательское визуальное распознавание, см. в [руководстве по использованию модели ONNX из пользовательское визуальное распознавание с помощью Windows ml (Предварительная версия)](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/custom-vision-onnx-windows-ml).

- [Преобразование существующих моделей с помощью винмлтулс](https://docs.microsoft.com/windows/ai/windows-ml/convert-model-winmltools). Этот пакет Python позволяет преобразовывать модели из нескольких форматов инфраструктуры обучения в ONNX. Разработчик может указать, в какую версию ONNX вы хотите преобразовать модель, в зависимости от того, какие сборки Windows предназначены для приложения. Если вы не знакомы с Python, вы можете использовать [панель мониторинга на основе пользовательского интерфейса машинного обучения Windows](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Tools/WinMLDashboard) для простого преобразования моделей всего за несколько щелчков мышью.

> [!IMPORTANT]
> Не все версии ONNX поддерживаются в Windows ML. Чтобы узнать, какие версии ONNX официально поддерживаются в версиях Windows, предназначенных для вашего приложения, проверьте [версии ONNX и сборки Windows](onnx-versions.md).

После создания модели ONNX вы [интегрируете модель](https://docs.microsoft.com/windows/ai/windows-ml/integrate-model) в код приложения, а затем сможете использовать машинное обучение в приложениях и устройствах Windows!

[!INCLUDE [help](../includes/get-help.md)]
