---
author: eliotcowley
title: Создание приложения универсальной платформы Windows машины обучения Windows (C#)
description: Создание первого приложения универсальной платформы Windows с помощью машинного Обучения Windows в этого пошагового руководства.
ms.author: elcowle
ms.date: 3/14/2019
ms.topic: article
keywords: windows 10, uwp, машинное обучение в windows, winml, windows ML
ms.localizationpriority: medium
ms.custom: RS5
ms.openlocfilehash: 6110f2e8032a2cd6084306c1e92c1b673e881211
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474451"
---
# <a name="tutorial-create-a-windows-machine-learning-uwp-application-c"></a>Учебник. Создание приложения универсальной платформы Windows машины обучения Windows (C#)

В этом руководстве мы создадим простое приложение универсальной платформы Windows, которое использует обученная модель машинного обучения для распознавания цифры нарисованного пользователем. В первую очередь это руководство посвящено как для загрузки и использования машинного Обучения Windows в приложении универсальной платформы Windows.

С образцом, этот учебник создан на основе показаны в следующем видеоролике.

<br/>

> [!VIDEO https://www.youtube.com/embed/yC3HKAv0aj4]

Если вы хотите просто взгляните на код завершения учебника, его можно найти в [репозиторий WinML GitHub](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/MNIST/UWP/cs). Он также доступен в [ C++/CX](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/MNIST/UWP/cppcx).

## <a name="prerequisites"></a>предварительные требования

- Windows 10 (версия 1809 или более поздней версии)
- [Пакет SDK для Windows 10](https://www.microsoft.com/software-download/windowsinsiderpreviewSDK) (сборка 17763 или более поздней версии)
- [Visual Studio 2017](https://developer.microsoft.com/windows/downloads)
- [Расширение Visual STUDIO 2017 генератор кода Windows машины обучения](https://marketplace.visualstudio.com/items?itemName=WinML.mlgen)
- Некоторые основные универсальной платформы Windows и C# базы знаний

## <a name="1-open-the-project-in-visual-studio"></a>1. Откройте проект в Visual Studio

После загрузки проекта из GitHub, запустите Visual Studio и откройте **MNIST_Demo.sln** файл (он должен быть расположен в  **&lt;путь к репозиторию&gt;\Windows-Machine-Learning\Samples\ MNIST\Tutorial\cs**). Если решение отображается как недоступный, нужно будет щелкнуть правой кнопкой мыши проект в **обозревателе решений** и выберите **перезагрузить проект**.

Мы предлагаем шаблон с реализованными событиями и элементами управления XAML, включая:

- [InkCanvas](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inkcanvas) для написания цифр.
- [Кнопки](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.button) для интерпретации цифр и очистки холста.
- Вспомогательные процедуры для преобразования **InkCanvas** вывода [VideoFrame](https://docs.microsoft.com/uwp/api/windows.media.videoframe).

Внутри **обозревателе решений**, проект имеет три файла основного кода:

- **MainPage.xaml** -все наш код XAML для создания пользовательского интерфейса **InkCanvas**, кнопки и метки.
- **MainPage.xaml.cs** — там, где находятся прикладном коде.
- **Helper.cs** -форматы изображений вспомогательные процедуры для обрезки и преобразования.

![Обозреватель решений Visual Studio с файлами проекта](images/get-started1.png)

## <a name="2-build-and-run-the-project"></a>2. Сборка и запуск проекта

В панели инструментов Visual Studio измените **платформа решения** для **x64** для запуска проекта на локальном компьютере, если устройство является 64-разрядная версия, или **x86** Если это 32-разрядной. (Можно проверить в настройках Windows приложения: **Система > о > характеристики устройства > системный тип**.)

Чтобы запустить проект, нажмите кнопку **начать отладку** кнопку на панели инструментов или клавишу **F5**. Приложение должно отображаться **InkCanvas** там, где пользователи могут писать цифры, **Recognize** кнопку, чтобы интерпретировать число, пустая метка, где интерпретированных цифр будет отображаться как текст и  **Очистить цифра** кнопку для очистки **InkCanvas**.

![Снимок экрана приложения](images/get-started2.png)

> [!NOTE]
> Если проект не построен, может потребоваться изменение целевой версии проекта развертывания. Щелкните правой кнопкой мыши проект в **обозревателе решений** и выберите **свойства**. В **приложения** вкладке **целевой версии** и **Минимальная версия** в соответствии с ОС и пакета SDK.

> [!NOTE]
> Если вы получаете предупреждение, что приложение уже установлено, просто выберите **Да** продолжить развертывание. Может потребоваться закрыть Visual Studio и снова откройте, если он по-прежнему не работает.

## <a name="3-download-a-model"></a>3. Загрузить модель

Теперь давайте модели машинного обучения, чтобы добавить к нашему приложению. В этом учебнике мы будем использовать предварительно обученную модель MNIST, обучена на [Microsoft Cognitive Toolkit (CNTK)](https://docs.microsoft.com/cognitive-toolkit/) и [экспортировать в формат ONNX](https://github.com/onnx/tutorials/blob/master/tutorials/CntkOnnxExport.ipynb).

Модель MNIST уже был включен в ваш **активы** папки и нужно будет добавить его в приложение в качестве существующего элемента. Также можно скачать предварительно обученную модель из раздела [ONNX Model Zoo](https://github.com/onnx/models) на GitHub.

## <a name="4-add-the-model"></a>4. Добавьте модель

Щелкните правой кнопкой мыши **активы** папку в **обозревателе решений**и выберите **добавить** > **существующий элемент**. Указать расположение модели ONNX средства выбора файлов, а затем нажмите кнопку **добавить**.

В проекте должны появиться два новых файла:

- **mnist.onnx** -обученной модели.
- **mnist.cs** -код, созданный Windows машинного Обучения.

![Обозреватель решений с новыми файлами](images/get-started3.png)

Чтобы убедиться, что модель формирует, когда мы компиляции приложения, щелкните правой кнопкой мыши **mnist.onnx** файла и выберите **свойства**. Для **Действия при сборке** выберите **Содержимое**.

Теперь давайте рассмотрим созданный код в **mnist.cs** файла. У нас есть три класса:

- **mnistModel** создает машинного обучения модели представления, создает сеанс на устройство по умолчанию системы, привязывает заданных входных данных и выводит в модель и асинхронно вычисляет модели. 
- **mnistInput** инициализирует типов входных данных, которые ожидает модели. В этом случае ожидает входные данные [ImageFeatureValue](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.imagefeaturevalue).
- **mnistOutput** инициализирует типы, которые будут выходные данные модели. В этом случае выходные данные будут список, который называется **Plus214_Output_0** типа [TensorFloat](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.tensorfloat).

Теперь мы используем эти классы для загрузки, привязки и оценки модели в нашем проекте.

## <a name="5-load-bind-and-evaluate-the-model"></a>5. Загрузки, привязки и оценка модели

Для приложений Windows машинного Обучения является шаблон, который мы хотим выполните: Нагрузки > привязать > оценки.

1. Загрузка модели машинного обучения.
2. Привязка входных и выходных данных к модели.
3. Оценка модели и просмотр результатов.

Мы будем использовать интерфейс код, созданный в **mnist.cs** для загрузки, привязки и оценка модели в нашем приложении.

Во-первых, в **MainPage.xaml.cs**, давайте создать экземпляр модели, входные и выходные данные. Добавьте следующие переменные-члены для **MainPage** класса:

```csharp
private mnistModel ModelGen;
private mnistInput ModelInput = new mnistInput();
private mnistOutput ModelOutput;
```

Затем в **LoadModelAsync**, мы загрузим модели. Этот метод должен вызываться, прежде чем мы будет использовать любой из методов модели (то есть на **MainPage** [Loaded](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement.loaded) событий, в [OnNavigatedTo](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.page.onnavigatedto) переопределение, или в любом месте перед **recognizeButton_Click** вызывается). **MnistModel** класс представляет модель MNIST и создает сеанс на устройстве системы по умолчанию. Для загрузки модели, мы называем **CreateFromStreamAsync** , передавая в файле ONNX в качестве параметра.

```csharp
private async Task LoadModelAsync()
{
    // Load a machine learning model
    StorageFile modelFile = await StorageFile.GetFileFromApplicationUriAsync(new Uri($"ms-appx:///Assets/mnist.onnx"));
    ModelGen = await mnistModel.CreateFromStreamAsync(modelFile as IRandomAccessStreamReference);
}
```

> [!NOTE]
> Если вы получаете красными линиями в разделе **IRandomAccessStreamReference**, необходимо включить его пространство имен. Поместите курсор над ним, нажмите клавишу **Ctrl +.** и выберите **с помощью Windows.Storage.Streams** в раскрывающемся меню.

Далее необходимо привязать наших входные и выходные данные к модели. Созданный код также включает **mnistInput** и **mnistOutput** классы-оболочки. **MnistInput** класс представляет ожидаемые входные данные модели и **mnistOutput** класс представляет ожидаемые выходные данные модели.

Чтобы инициализировать входной объект модели, вызовите **mnistInput** класса конструктор и передав данные приложения и убедитесь, что входные данные соответствует тип входных данных, который ожидает, что модель. **MnistInput** ожидает, что класс **ImageFeatureValue**, поэтому мы используем вспомогательный метод для получения **ImageFeatureValue** для входных данных.

С помощью наших включены вспомогательные функции в **helper.cs**, мы будет копировать содержимое **InkCanvas**, преобразуйте его в тип **ImageFeatureValue**и привязать его к нашей модели.

```csharp
private async void recognizeButton_Click(object sender, RoutedEventArgs e)
{
    // Bind model input with contents from InkCanvas
    VideoFrame vf = await helper.GetHandWrittenImage(inkGrid);
    ModelInput.Input3 = ImageFeatureValue.CreateFromVideoFrame(vf);
}
```

Для вывода, мы просто вызываем **EvaluateAsync** с определенным входом. После инициализации входные данные, вызовите модели **EvaluateAsync** метод оценке модели входным данным. **EvaluateAsync** привязывает входные данные и выводит на объект модели и оценивает модель на основе входных данных.

Так как модель возвращает тензорные выходные данные, мы сначала нужно преобразовать его в понятные тип данных и затем проанализировать возвращаемый список, чтобы определить количество десятичных разрядов, наибольшей вероятностью и отобразить один.

```csharp
private async void recognizeButton_Click(object sender, RoutedEventArgs e)
{
    // Bind model input with contents from InkCanvas
    VideoFrame vf = await helper.GetHandWrittenImage(inkGrid);
    ModelInput.Input3 = ImageFeatureValue.CreateFromVideoFrame(vf);

    // Evaluate the model
    ModelOutput = await ModelGen.EvaluateAsync(ModelInput);

    // Convert output to datatype
    IReadOnlyList<float> vectorImage = ModelOutput.Plus214_Output_0.GetAsVectorView();
    IList<float> imageList = vectorImage.ToList();

    // Query to check for highest probability digit
    var maxIndex = imageList.IndexOf(imageList.Max());

    // Display the results
    numberLabel.Text = maxIndex.ToString();
}
```

Наконец, нам понадобятся Очистить **InkCanvas** пользователям рисовать другой номер.

```csharp
private void clearButton_Click(object sender, RoutedEventArgs e)
{
    inkCanvas.InkPresenter.StrokeContainer.Clear();
    numberLabel.Text = "";
}
```

## <a name="6-launch-the-application"></a>6. Запустите приложение

После создания и запуска приложения (нажмите клавишу **F5**), мы будем может распознавать несколько на **InkCanvas**.

![готовое приложение](images/get-started4.png)

Вот и все — вы внесли в приложение машинного Обучения Windows! Дополнительные примеры, демонстрирующие способы использования машинного Обучения Windows, ознакомьтесь с нашей [Windows-Machine-Learning](https://github.com/Microsoft/Windows-Machine-Learning) на сайте GitHub.

[!INCLUDE [help](includes/get-help.md)]
