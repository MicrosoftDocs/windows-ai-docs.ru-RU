---
author: rosanevallim
title: Способы обучения модели для Windows ML в Visual Studio
description: Узнайте, как обучить модель для Windows ML с помощью Visual Studio Tools for AI в этом пошаговом руководстве.
ms.author: rovalli
ms.date: 4/2/2019
ms.topic: article
keywords: windows 10, uwp, winml, машинное обучение в Windows, visual studio
ms.localizationpriority: medium
ms.openlocfilehash: 27c2fb2cdce9d19c6219c40f885ad9d720029f12
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66179966"
---
# <a name="train-a-model-with-cntk"></a>Обучение модели с помощью CNTK

В этом руководстве мы будем использовать [инструменты Visual Studio для ии](http://aka.ms/vstoolsforai), это расширение разработки для сборки, тестирования и развертывания решения для глубокого обучения и искусственного Интеллекта, для обучения модели. <!--for the MNIST sample app in [Get Started (UWP)](get-started-uwp.md)-->

Мы будем обучать модель с помощью платформы [Microsoft Cognitive Toolkit (CNTK)](http://www.microsoft.com/en-us/cognitive-toolkit) и [набора данных MNIST](http://yann.lecun.com/exdb/mnist/), содержащего учебный набор с 60 000 примеров и тестовый набор с 10 000 примеров рукописных цифр. Затем мы сохраним модель в формате [Open Neural Network Exchange (ONNX)](https://onnx.ai/) для использования с Windows ML.

## <a name="prerequisites"></a>предварительные требования
### <a name="install-visual-studio-tools-for-ai"></a>Установите Visual Studio Tools for AI
Для начала вам потребуется скачать и установить [Visual Studio](https://www.visualstudio.com/downloads/). Открыв Visual Studio, активируйте расширение **Visual Studio Tools for AI**:

1. В меню Visual Studio выберите пункт "Расширения и обновления...".
2. Нажмите вкладку "В сети" и выберите "Поиск в Visual Studio Marketplace".
3. Найдите "Visual Studio Tools for AI". 
3. Нажмите кнопку **Скачать**. 
4. После установки перезапустите Visual Studio. 

Это расширение будет активно после перезагрузки Visual Studio. Если возникают проблемы, ознакомьтесь с разделом [Поиск расширений Visual Studio](h https://docs.microsoft.com/visualstudio/ide/finding-and-using-visual-studio-extensions).

### <a name="download-sample-code"></a>Загрузка примера кода
Скачайте репозиторий [Примеры для ИИ](https://github.com/Microsoft/samples-for-ai) на GitHub. Эти примеры описывают, как начать работу с глубинным обучением на примерах из TensorFlow, CNTK, Theano и других платформ.

### <a name="install-cntk"></a>Установка CNTK
Установите [CNTK для Python для Windows](https://docs.microsoft.com/en-us/cognitive-toolkit/setup-windows-python?tabs=cntkpy24). Обратите внимание, что необходимо также установить Python, если вы еще не сделали этого.

Другой способ подготовки компьютера для разработки модели глубинного обучения см. в разделе [Подготовка среды разработки](https://github.com/Microsoft/samples-for-ai/blob/master/README.md), где можно найти упрощенную процедуру для установки Python, CNTK, TensorFlow, драйверы графического процессора NVIDIA (необязательно) и многое другое.

## <a name="1-open-project"></a>1. Открытие проекта

Запустите Visual Studio 2015 и выберите **Файл > Открыть > Проект/Решение**. В репозитории "Примеры для ИИ" выберите папку **examples\cntk\python** и откройте файл **CNTKPythonExamples.sln**.

![Откройте решение](../images/open-solution.png)

## <a name="2-train-the-model"></a>2. Обучение модели

Чтобы задать проект MNIST как запускаемый автоматически, щелкните правой кнопкой мыши по проекту python и выберите пункт **Назначить запускаемым проектом**.

![Откройте решение](../images/mnist-startup.png)

Затем откройте файл train_mnist_onnx.py и **запуска** проект, нажав клавишу **F5** или зеленую **запуска** кнопки.

## <a name="3-view-the-model-and-add-it-to-your-app"></a>3. Просмотр модели и добавьте его в приложение

Теперь файл обученной модели **mnist.onnx** должен размещаться в папке samples-for-ai/examples/cntk/python/MNIST. <!--You can use this trained **mnist.onnx** model file to build the MNIST sample app in [Get Started (UWP)](get-started-uwp.md)!-->

## <a name="4-learn-more"></a>4. Узнайте больше
Чтобы узнать, как ускорить обучение моделей глубинного обучения с помощью [Виртуальных машин с графическими процессорами Azure](https://docs.microsoft.com/en-us/visualstudio/ai/tensorflow-vm) и получить другую информацию, посетите страницу [Искусственный интеллект в корпорации Майкрософт](https://www.microsoft.com/ai) и [Технологии машинного обучения Майкрософт](https://docs.microsoft.com/en-us/azure/machine-learning/#other-microsoft-machine-learning-technologies).

[!INCLUDE [help](../includes/get-help.md)]
