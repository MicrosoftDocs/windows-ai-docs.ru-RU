---
author: eliotcowley
title: Средства и примеры
description: Дополнительные сведения о различных средств и примеров, доступных для Windows машинного обучения.
ms.author: elcowle
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, windows в машинном обучении, WinML, примеры, средства
ms.localizationpriority: medium
ms.openlocfilehash: d305184d493549c7d2f9ed126975f3310d4e1279
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66179956"
---
# <a name="tools-and-samples"></a>Средства и примеры

[GitHub-репозитории Windows-Machine-Learning](https://github.com/Microsoft/Windows-Machine-Learning) содержит примеры приложений, демонстрирующие способы использования машинного обучения Windows, а также средства для проверки моделей и устранение неполадок во время разработки.

## <a name="tools"></a>Инструменты

Следующие средства доступны на сайте GitHub.

| Имя | Описание |
|------|-------------|
| [Генератор кода WinML (mlgen)](https://marketplace.visualstudio.com/items?itemName=WinML.mlgen) | Расширение Visual Studio, которые помогут приступить к работе с помощью API-интерфейсы WinML в приложениях UWP путем создания код шаблона, при добавлении файла обученной ONNX в проект универсальной платформы Windows. Для [Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=WinML.mlgen) и [2019](https://marketplace.visualstudio.com/items?itemName=WinML.MLGenV2). См. в разделе [документации](mlgen.md) Дополнительные сведения.
| [Панель мониторинга WinML (Предварительная версия)](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Tools/WinMLDashboard) | Средство для просмотра, редактирования, преобразование и проверку моделей машинного обучения для машинного Обучения Windows механизм вывода Графическим пользовательским интерфейсом. |
| [WinMLRunner](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Tools/WinMLRunner) | Средство командной строки, можно запустить .onnx или .pb моделей, где находятся входные и выходные переменные tensors или изображения. Это удобно, так как он позволяет запустить WinML API-интерфейсы для модели и см. в разделе, если оно попадет все проблемы, прежде чем пытаться интегрировать в приложения. |
| [WinMLTools](https://pypi.org/project/winmltools/) | Пакет Python, который предоставляет преобразование моделей из разных наборов средств машинного Обучения в ONNX, а также средство квантования чтобы уменьшить объем памяти для модели. |

## <a name="samples"></a>Примеры

Следующие образцы приложений доступны на сайте GitHub.

| Имя | Описание |
|------|-------------|
| [AdapterSelection (Win32 C++)](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/AdapterSelection/AdapterSelection/cpp) | Классическое приложение, демонстрирующий Выбор адаптером конкретного устройства с помощью вашей модели. |
| [Пример пользовательского оператора (Win32 C++)](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/CustomOperatorCPU/desktop/cpp) | Настольным приложением, которое определяет несколько пользовательских операторов ЦП. Один из них является оператором отладки, можно интегрировать в собственные рабочего процесса. |
| [Пользовательские Tensorization (Win32 C++)](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/CustomTensorization) | Показано, как tensorize входные изображения с помощью API WinML на ЦП и GPU. |
| [Custom Vision (UWP C#)](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/custom-vision-onnx-windows-ml) | Показано, как для обучения модели ONNX в облаке, используя Custom Vision и интегрировать в приложение с WinML. |
| [Emoji8 (UWP C#)](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/Emoji8/UWP/cs) | Показано, как можно использовать для создания мощных интересную WinML обнаружение эмоций приложения. |
| [Передачи в стиле FNS (UWP C#)](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/FNSCandyStyleTransfer) | Использует модель передачи FNS сладости стиля для повторного применения стиля изображения или видео потоков. |
| [MNIST (UWP C#/C++)](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/MNIST) | Соответствует [руководства: Создание приложения универсальной платформы Windows машины обучения Windows (C#)](get-started-uwp.md). Запустить из основы и работы с учебником или готового проекта. |
| [PlaneIdentifier (UWP C#, WPF C#)](https://github.com/Microsoft/Windows-AppConsult-Samples-UWP/tree/master/PlaneIdentifier) | Использует предварительно обученная модель машинного обучения, созданные с помощью Custom Vision службы в Azure, для определения того, если заданное изображение содержит определенного объекта: плоскость. |
| [Обнаружение объектов SqueezeNet (Win32 C++, UWP C#/JavaScript)](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/SqueezeNetObjectDetection) | Использует SqueezeNet, модель предварительно обучена машинное обучение для распознавания объектов преобладает в изображении, выбранного пользователем из файла. |
| [Обнаружение объектов SqueezeNet (Azure IoT Edge в Windows, C#)](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/EdgeModules/SqueezeNetObjectDetection/cs) | Это пример модуля, в котором показано, как для формирования выводов машинного Обучения Windows в модуль Edge Интернета вещей Azure, под управлением Windows. Образы предоставляемые подключенной камеры, inferenced применительно к модели SqueezeNet и отправляется в центр Интернета вещей. |
| [winml_tracker (ROS C++)](https://github.com/ms-iot/winml_tracker) | Узел ROS (робота операционная система), который использует WinML для отслеживания пользователей (или другие объекты) в camera кадры. |

[!INCLUDE [help](../includes/get-help.md)]
