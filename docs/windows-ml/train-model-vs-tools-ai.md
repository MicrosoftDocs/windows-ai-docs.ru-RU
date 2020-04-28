---
author: rosanevallim
title: Способы обучения модели для Windows ML в Visual Studio
description: В этом пошаговом руководстве описывается, как обучить модель для Windows ML с помощью Visual Studio Tools for AI.
ms.author: rovalli
ms.date: 4/2/2019
ms.topic: article
keywords: windows 10, uwp, Windows machine learning, visual studio
ms.localizationpriority: medium
ms.openlocfilehash: 27c2fb2cdce9d19c6219c40f885ad9d720029f12
ms.sourcegitcommit: 2139506ff12b7205283288c4bbac866ddfa812f3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/24/2020
ms.locfileid: "66179966"
---
# <a name="train-a-model-with-cntk"></a>Обучение модели с использованием CNTK

В рамках этого руководства мы будем обучать модель с использованием расширения [Visual Studio Tools for AI](http://aka.ms/vstoolsforai), которое разработано для создания, тестирования и развертывания решений глубокого обучения и искусственного интеллекта (ИИ). <!--for the MNIST sample app in [Get Started (UWP)](get-started-uwp.md)-->

Мы будем обучать модель с помощью платформы [CNTK (Microsoft Cognitive Toolkit)](http://www.microsoft.com/en-us/cognitive-toolkit) и [набора данных MNIST](http://yann.lecun.com/exdb/mnist/), содержащего обучающий набор с 60 000 примеров и тестовый набор с 10 000 примеров рукописных цифр. Затем мы сохраним модель в формате [ONNX (Open Neural Network Exchange)](https://onnx.ai/) для использования с Windows ML.

## <a name="prerequisites"></a>Предварительные условия
### <a name="install-visual-studio-tools-for-ai"></a>Установка Visual Studio Tools for AI
Для начала вам потребуется скачать и установить [Visual Studio](https://www.visualstudio.com/downloads/). Открыв Visual Studio, активируйте расширение **Visual Studio Tools for AI**:

1. В строке меню Visual Studio выберите пункт "Расширения и обновления...".
2. Щелкните вкладку "В сети" и выберите "Search Visual Studio Marketplace" (Поиск в Visual Studio Marketplace).
3. Найдите Visual Studio Tools for AI. 
3. Нажмите кнопку **Скачать**. 
4. После установки перезапустите Visual Studio. 

Это расширение станет активным после перезагрузки Visual Studio. Если возникают проблемы, ознакомьтесь с разделом [Поиск расширений Visual Studio](hhttps://docs.microsoft.com/visualstudio/ide/finding-and-using-visual-studio-extensions).

### <a name="download-sample-code"></a>Скачивание примера кода
Скачайте репозиторий [с примерами для ИИ](https://github.com/Microsoft/samples-for-ai) с сайта GitHub. В этих примерах показано, как начать работу с глубоким обучением на таких платформах, как TensorFlow, CNTK, Theano и др.

### <a name="install-cntk"></a>Установка CNTK
Установите [CNTK для Python в Windows](https://docs.microsoft.com/en-us/cognitive-toolkit/setup-windows-python?tabs=cntkpy24). Обратите внимание, что необходимо также установить Python, если вы еще не сделали этого.

Другой способ подготовки компьютера для разработки модели глубинного обучения см. в разделе [Подготовка среды разработки](https://github.com/Microsoft/samples-for-ai/blob/master/README.md), где можно найти упрощенную процедуру для установки Python, CNTK, TensorFlow, драйверов GPU NVIDIA (необязательно) и многое другое.

## <a name="1-open-project"></a>1. Открытие проекта

Запустите Visual Studio и выберите **Файл > Открыть > Решение или проект**. В репозитории с примерами для ИИ выберите папку **examples\cntk\python** и откройте файл **CNTKPythonExamples.sln**.

![Открытие решения](../images/open-solution.png)

## <a name="2-train-the-model"></a>2. Обучение модели

Чтобы проект MNIST запускался автоматически, щелкните правой кнопкой мыши имя проекта Python и выберите пункт **Назначить автозагружаемым проектом**.

![Открытие решения](../images/mnist-startup.png)

Затем откройте файл train_mnist_onnx.py и **запустите** проект, нажав клавишу **F5** или зеленую кнопку **Запустить**.

## <a name="3-view-the-model-and-add-it-to-your-app"></a>3. Просмотр модели и добавление модели в приложение

Теперь файл обученной модели **mnist.onnx** должен размещаться в папке samples-for-ai/examples/cntk/python/MNIST. <!--You can use this trained **mnist.onnx** model file to build the MNIST sample app in [Get Started (UWP)](get-started-uwp.md)!-->

## <a name="4-learn-more"></a>4. Дополнительные сведения
Чтобы узнать, как ускорить обучение моделей глубокого обучения с помощью [виртуальных машин Azure с графическими процессорами](https://docs.microsoft.com/en-us/visualstudio/ai/tensorflow-vm) и получить другую информацию, см. страницу [Microsoft Artificial Intelligence](https://www.microsoft.com/ai) (Искусственный интеллект в корпорации Майкрософт) и [документацию по Машинному обучению Azure](https://docs.microsoft.com/en-us/azure/machine-learning/#other-microsoft-machine-learning-technologies).

[!INCLUDE [help](../includes/get-help.md)]
