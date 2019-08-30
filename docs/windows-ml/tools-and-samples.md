---
title: Средства и примеры
description: Узнайте о различных средствах и примерах, доступных для Windows Машинное обучение.
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, машинное обучение Windows, WinML, примеры, средства
ms.localizationpriority: medium
ms.openlocfilehash: 453d43796e559a69591d4c8290b3acc5fb66f302
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157970"
---
# <a name="tools-and-samples"></a>Средства и примеры

[Репозиторий машинного обучения на сайте GitHub](https://github.com/Microsoft/Windows-Machine-Learning) содержит примеры приложений, демонстрирующих использование машинное обучение Windows, а также средства, помогающие проверять модели и устранять проблемы во время разработки.

## <a name="tools"></a>Сервис

На сайте GitHub доступны следующие средства.

| Имя | Описание |
|------|-------------|
| [Генератор кода WinML (млжен)](https://marketplace.visualstudio.com/items?itemName=WinML.mlgen) | Расширение Visual Studio, которое поможет приступить к работе с API WinML в приложениях UWP путем создания кода шаблона при добавлении обученного файла ONNX в проект UWP. Доступно для [Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=WinML.mlgen) и [2019](https://marketplace.visualstudio.com/items?itemName=WinML.MLGenV2). Дополнительные сведения см. в [документации](mlgen.md) .
| [Панель мониторинга WinML (Предварительная версия)](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Tools/WinMLDashboard) | Инструмент на основе графического пользовательского интерфейса для просмотра, редактирования, преобразования и проверки моделей машинного обучения для механизма вывода Windows ML. |
| [винмлруннер](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Tools/WinMLRunner) | Программа командной строки, которая может выполнять onnx или Pb-модели, где входные и выходные переменные являются десятками или изображениями. Полезно, так как она позволяет запускать API WinML для модели и видеть, не возникли ли проблемы перед попыткой интегрировать ее в приложение. |
| [винмлтулс](https://pypi.org/project/winmltools/) | Пакет Python, который обеспечивает преобразование модели из различных наборов средств ML в ONNX, а также средство дискретизация для уменьшения объема памяти, занимаемого моделью. |

## <a name="samples"></a>Примеры

Следующие примеры приложений доступны на сайте GitHub.

| Имя | Описание |
|------|-------------|
| [Адаптерселектион (Win32 C++)](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/AdapterSelection/AdapterSelection/cpp) | Классическое приложение, которое показывает, как выбрать конкретный адаптер устройства для выполнения модели. |
| [Пример настраиваемого оператора ( C++Win32)](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/CustomOperatorCPU/desktop/cpp) | Классическое приложение, определяющее несколько пользовательских операторов ЦП. Один из них — оператор отладки, который можно интегрировать в собственный рабочий процесс. |
| [Пользовательские Тенсоризатион (Win32 C++)](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/CustomTensorization) | Показывает, как тенсоризе входной образ с помощью интерфейсов API WinML как для ЦП, так и для GPU. |
| [Пользовательское визуальное распознавание (UWP C#)](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/custom-vision-onnx-windows-ml) | Показывает, как обучить модель ONNX в облаке с помощью Пользовательское визуальное распознавание и интегрировать ее в приложение с WinML. |
| [Emoji8 (UWP C#)](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/Emoji8/UWP/cs) | Здесь показано, как можно использовать WinML для получения привлекательного распознавания эмоций приложения. |
| [Перенос стилей ФНС (UWP C#)](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/FNSCandyStyleTransfer) | Использует модель перемещения в стиле ФНС для повторного создания изображений или видеопотоков. |
| [MNIST (UWP C#/C++)](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/MNIST) | [Соответствует учебнику: Создайте приложение Windows Машинное обучение UWP (C#).](get-started-uwp.md) Начните с пошаговой работы с учебником или запустите завершенный проект. |
| [Планеидентифиер (UWP C#, WPF C#)](https://github.com/Microsoft/Windows-AppConsult-Samples-UWP/tree/master/PlaneIdentifier) | Использует предварительно обученную модель машинного обучения, созданную с помощью службы Пользовательское визуальное распознавание в Azure, чтобы определить, содержит ли данный образ определенный объект: плоскость. |
| [Обнаружение объектов Скуизенет (Win32 C++, UWP C#/жаваскрипт)](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/SqueezeNetObjectDetection) | Использует Скуизенет, предварительно обученную модель машинного обучения для обнаружения предварительного объекта в изображении, выбранном пользователем из файла. |
| [Обнаружение объектов Скуизенет (Azure IoT Edge в Windows, C#)](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/EdgeModules/SqueezeNetObjectDetection/cs) | Это пример модуля, демонстрирующий запуск Windows ML в Azure IoT Edgeном модуле, работающем под управлением Windows. Изображения предоставляются подключенной камерой, выводятся в соответствии с моделью Скуизенет и отправляются в центр Интернета вещей. |
| [winml_tracker (рос C++)](https://github.com/ms-iot/winml_tracker) | Узел рос (робот операционной системы), который использует WinML для мониторинга людей (или других объектов) в кадрах камеры. |

[!INCLUDE [help](../includes/get-help.md)]
