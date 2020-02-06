---
title: Средства и примеры
description: Сведения о некоторых средствах и примерах, доступных для Windows Machine Learning.
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10, windows machine learning, WinML, примеры, средства
ms.localizationpriority: medium
ms.openlocfilehash: 453d43796e559a69591d4c8290b3acc5fb66f302
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157970"
---
# <a name="tools-and-samples"></a>Средства и примеры

[Репозиторий Windows-Machine-Learning на сайте GitHub](https://github.com/Microsoft/Windows-Machine-Learning) содержит примеры приложений, в которых показано использование Windows Machine Learning, а также средств для проверки моделей и устранения проблем при разработке.

## <a name="tools"></a>Инструменты

На GitHub доступны следующие средства.

| Название | Описание |
|------|-------------|
| [Генератор кода WinML (mlgen)](https://marketplace.visualstudio.com/items?itemName=WinML.mlgen) | Расширение Visual Studio, которое поможет приступить к использованию API WinML в приложениях UWP. Оно создает шаблон кода, когда вы добавляете обученный файл ONNX в проект UWP. Это средство доступно для [Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=WinML.mlgen) и [Visual Studio 2019](https://marketplace.visualstudio.com/items?itemName=WinML.MLGenV2). Дополнительные сведения см. в [документации](mlgen.md).
| [Панель мониторинга WinML (предварительная версия)](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Tools/WinMLDashboard) | Инструмент с графическим пользовательским интерфейсом для просмотра, редактирования, преобразования и проверки моделей машинного обучения для подсистемы вывода данных в Windows ML. |
| [WinMLRunner](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Tools/WinMLRunner) | Программа командной строки, которая запускает ONNX или PB-файлы моделей, у которых переменные входа и выхода имеют формат тензоров или изображений. Программа полезна тем, что позволяет запустить для модели API WinML и убедиться в отсутствии проблем перед попыткой интегрировать ее в приложение. |
| [WinMLTools](https://pypi.org/project/winmltools/) | Этот пакет Python обеспечивает преобразование моделей из форматов разных наборов средств машинного обучения в формат ONNX, а также позволяет выполнить квантование для уменьшения объема занимаемой моделью памяти. |

## <a name="samples"></a>примеры

На GitHub доступны следующие примеры приложений.

| Название | Описание |
|------|-------------|
| [AdapterSelection (Win32 C++)](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/AdapterSelection/AdapterSelection/cpp) | Классическое приложение, которое демонстрирует выбор конкретного адаптера устройства для выполнения модели. |
| [Пример пользовательского оператора (Win32 C++)](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/CustomOperatorCPU/desktop/cpp) | Классическое приложение, которое определяет несколько пользовательских операторов ЦП. Один из них предназначен для отладки и его можно интегрировать в собственный рабочий процесс. |
| [Пользовательское преобразование в тензор (Win32 C++)](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/CustomTensorization) | Демонстрация процесса преобразования изображения в тензор с применением интерфейсов API WinML на ЦП и GPU. |
| [Пользовательское визуальное распознавание (UWP C#)](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/custom-vision-onnx-windows-ml) | Демонстрация процессов обучения модели ONNX в облаке с помощью службы "Пользовательское визуальное распознавание" с последующей интеграцией в приложение с помощью WinML. |
| [Emoji8 (UWP C#)](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/Emoji8/UWP/cs) | Демонстрация применения WinML для создания развлекательного приложения с распознаванием эмоций. |
| [FNS Style Transfer (UWP C#)](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/FNSCandyStyleTransfer) | Применение модели переноса стилей FNS-Candy для изменения стиля изображений или видеопотоков. |
| [MNIST (UWP C#/C++)](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/MNIST) | Пример для руководства [ Создание приложения UWP (C#) для Windows Machine Learning](get-started-uwp.md). Его можно создать поэтапно, работая с руководством, или сразу запустить готовый проект. |
| [PlaneIdentifier (UWP C#, WPF C#)](https://github.com/Microsoft/Windows-AppConsult-Samples-UWP/tree/master/PlaneIdentifier) | Применение предварительно обученной модели машинного обучения, созданной с помощью службы "Пользовательское визуальное распознавание" в Azure, для поиска конкретных объектов (в этом случае самолетов) на переданном изображении. |
| [Обнаружение объектов SqueezeNet (Win32 C++, UWP C#/JavaScript)](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/SqueezeNetObjectDetection) | Применение предварительно обученной модели машинного обучения SqueezeNet для обнаружения основного объекта на изображении, выбранном пользователем из файла. |
| [Обнаружение объектов SqueezeNet (Azure IoT Edge на Windows, C#)](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/EdgeModules/SqueezeNetObjectDetection/cs) | Это пример модуля, в котором показан запуск Windows ML в модуле Azure IoT Edge на ОС Windows. Изображения передаются с подключенной камеры, обрабатываются моделью SqueezeNet и отправляются в Центр Интернета вещей. |
| [winml_tracker (ROS C++)](https://github.com/ms-iot/winml_tracker) | Узел ROS (операционной системы для роботов), который использует WinML для обнаружения людей (или других объектов) на кадрах, полученных с камеры. |

[!INCLUDE [help](../includes/get-help.md)]
