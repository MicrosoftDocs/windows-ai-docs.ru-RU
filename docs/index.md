---
author: rosanevallim
title: Машинное обучение Windows
description: Windows ML позволяет использовать обученные модели машинного обучения в приложениях Windows.
ms.author: rovalli
ms.date: 12/12/2018
ms.topic: article
keywords: windows 10, windows ai, windows ml, winml, windows machine learning
ms.localizationpriority: medium
ms.custom: RS5
ms.openlocfilehash: 011cf35c131b5f33891bb51722cb5f544d3e5193
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2019
ms.locfileid: "59473731"
---
# <a name="windows-machine-learning"></a>Машинное обучение Windows

С помощью Windows ML вы сможете интегрировать обученные модели машинного обучения в приложения Windows.

![Графическое изображение Windows ML](images/winml-graphic.png)

## <a name="overview"></a>Обзор

:::row:::
    :::column:::
    Windows ML позволяет использовать обученные модели машинного обучения в приложениях Windows (C#, C++ и JavaScript). Подсистема вывода Windows ML обеспечивает локальную оценку обученных моделей на устройствах с Windows. Это позволяет не беспокоиться о подключении, пропускной способности и конфиденциальности данных. Кроме того, за счет оптимизации оборудования для ЦП и GPU повышается производительность для быстрого получения результатов оценки.

    Сведения о последних функциях и исправлениях в Windows ML см. в наших [заметках о выпуске](release-notes.md).
    :::column-end:::
    :::column:::
        ![windows ml layers](images/overview-diagram.png)
    :::column-end:::
:::row-end:::

В следующем видео представлен краткий обзор машинного обучения Windows.

<br/>

> [!VIDEO https://www.youtube.com/embed/riGxT0Pd6IA]

## <a name="develop"></a>Разработка

![Процесс разработки в Windows ML](images/winml-flow.png)

Чтобы создавать приложения с помощью Windows ML, вам потребуется:

1. [Получить обученную модель ONNX](get-onnx-model.md) или преобразовать модели, обученные на других платформах ML, в ONNX с использованием [WinMLTools](convert-model-winmltools.md).
1. Добавить файл модели ONNX в свое приложение.
1. [Интегрировать модель](integrate-model.md) в код своего приложения.
1. Запустить приложение на любом устройстве с Windows.

Чтобы оценить Windows ML в действии, вы можете поработать с примерами приложений из репозитория [Windows-Machine-Learning](https://github.com/Microsoft/Windows-Machine-Learning/tree/master) на сайте GitHub. Дополнительные сведения об использовании Windows ML вы найдете в нашей документации.

## <a name="other-machine-learning-solutions-from-microsoft"></a>Другие решения машинного обучения от корпорации Майкрософт

Майкрософт предлагает широкий набор решений, среди которых вы обязательно найдете подходящее. Эти решения запускаются в облаке, в локальной среде и на локальном устройстве. Дополнительные сведения см. в статье о [вариантах продуктов для машинного обучения от корпорации Майкрософт](https://docs.microsoft.com/azure/machine-learning/service/overview-more-machine-learning).

[!INCLUDE [help](includes/get-help.md)]
