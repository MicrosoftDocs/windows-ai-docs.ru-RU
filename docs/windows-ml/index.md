---
author: rosanevallim
title: Машинное обучение Windows
description: Windows ML позволяет использовать обученные модели машинного обучения в приложениях Windows.
ms.author: rovalli
ms.date: 4/17/2019
ms.topic: article
keywords: windows 10, windows ai, windows ml, winml, windows machine learning
ms.localizationpriority: medium
ms.custom: RS5
ms.openlocfilehash: c6ed47251d9d5372fcf0b998ab3a0a0ca7d9e25a
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66179795"
---
# <a name="windows-machine-learning"></a>Машинное обучение Windows

Реализуйте технологии ИИ в приложениях Windows с помощью Windows ML &mdash; высокопроизводительного и надежного API для выполнения зависимостей машинного обучения на устройствах с Windows.

![Графическое изображение Windows ML](../images/winml-graphic.png)

## <a name="overview"></a>Обзор

С помощью Windows ML разработчики могут использовать обученные модели машинного обучения в приложениях для Windows, написанных на C#, C++ или JavaScript, либо локально на устройстве с Windows 10 или компьютере с Windows Server 2019. Включить обученные модели машинного обучения в код приложения просто. Достаточно нескольких действий:

![Среда обучения, добавление ссылки на модель, приложение, Windows ML](../images/winml-flow.png)

1. Получите обученную модель Open Neural Network Exchange (ONNX) или преобразуйте модели, обученные на других платформах машинного обучения, в ONNX с помощью [WinMLTools](convert-model-winmltools.md).

2. Добавьте файл модели ONNX в свое приложение или сделайте его доступным на целевом устройстве другим методом.

3. Интегрируйте модель в код приложения, а затем выполните его сборку и развертывание.

:::row:::
    :::column:::
    При запуске приложения среда выполнения Windows ML (которая содержит подсистему зависимостей модели ONNX) оценивает обученную модель на устройстве с Windows 10 (или Windows Server 2019, если код предназначен для развертывания сервера). Windows ML абстрагирует оборудование, что позволяет разработчикам использовать множество процессоров &mdash; ЦП, GPU и, в будущем, ускорители ИИ. Аппаратное ускорение Windows ML основано на [DirectML](https://docs.microsoft.com/windows/desktop/direct3d12/dml), высокопроизводительном низкоуровневом API из семейства DirectX, предназначенном для выполнения зависимостей машинного обучения.
    :::column-end:::
    :::column:::
        ![windows ml layers](../images/overview-diagram.png)
    :::column-end:::
:::row-end:::

Windows ML предоставляет разработчикам следующие преимущества:

- **Простота развертывания.** Решение Windows ML встроено в последние версии Windows 10 и Windows Server 2019, поэтому все, что вам потребуется, — это Visual Studio и обученная модели ONNX, которую можно распространять вместе с приложением Windows.

- **Поддержка широкого спектра оборудования.** Windows ML позволяет однократно написать код для рабочей нагрузки машинного обучения и автоматически оптимизировать производительность для оборудования различных поставщиков и с различными процессорами, такими как ЦП, GPU и ускорители ИИ. Кроме того, Windows ML гарантирует согласованную работу всего поддерживаемого оборудования.

- **Минимальная задержка, получение результатов в режиме реального времени.** Модели машинного обучения можно оценить, используя возможности обработки на устройстве с Windows. Это позволяет выполнять локальный анализ больших объемов данных (например, изображения и видео) в режиме реального времени. Результаты выводятся быстро и эффективно, что особенно важно для рабочих нагрузок, требующих высокой производительности, таких как игровые движки или фоновые задачи, например индексирование для службы поиска.

- **Повышенная гибкость.** Возможность локально оценивать модели машинного обучения на устройствах с Windows позволяет реализовать более широкий диапазон сценариев. Например, оценка модели машинного обучения может выполняться, пока устройство находится в автономном режиме, а также при прерывистом подключении. Кроме того, вы можете реализовать сценарии, в которых не все данные отправляются в облако из соображений конфиденциальности или защиты суверенитета данных.

- **Сокращение операционных расходов.** Обучение моделей машинного обучения в облаке и их последующая локальная оценка на устройствах с Windows значительно сокращают затраты на оплату полосы пропускания. В облако отправляется минимальный объем данных &mdash; достаточный для постоянного совершенствования модели машинного обучения. Кроме того, при развертывании модели машинного обучения в сценарии с использованием сервера разработчики могут применять аппаратное ускорение Windows ML, чтобы ускорить обслуживание модели и сократить число компьютеров для обработки рабочей нагрузки.

Чтобы оценить Windows ML в действии, вы можете поработать с примерами приложений из [репозитория Windows-Machine-Learning на сайте GitHub](https://github.com/Microsoft/Windows-Machine-Learning).

Сведения о последних функциях и исправлениях в Windows ML см. в наших [заметках о выпуске](release-notes.md).

В следующем видео представлен краткий обзор машинного обучения Windows.

<br/>

> [!VIDEO https://www.youtube.com/embed/riGxT0Pd6IA]

## <a name="other-machine-learning-solutions-from-microsoft"></a>Другие решения машинного обучения от корпорации Майкрософт

Майкрософт предлагает широкий набор решений, среди которых вы обязательно найдете подходящее. Эти решения запускаются в облаке, в локальной среде и на локальном устройстве. Дополнительные сведения см. в статье о [вариантах продуктов для машинного обучения от корпорации Майкрософт](https://docs.microsoft.com/azure/machine-learning/service/overview-more-machine-learning).

[!INCLUDE [help](../includes/get-help.md)]