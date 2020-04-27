---
title: Создание приложения UWP (C#) для Windows Machine Learning
description: В этом пошаговом руководстве показано, как вы можете создать свое первое приложение UWP с помощью Машинного обучения Windows.
ms.date: 5/10/2019
ms.topic: article
keywords: windows 10, uwp, машинное обучение windows, winml, windows ML
ms.localizationpriority: medium
ms.custom: RS5
ms.openlocfilehash: 4a8e46835b0018a8057c1056c6dd59b9589b0f9c
ms.sourcegitcommit: 2139506ff12b7205283288c4bbac866ddfa812f3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/24/2020
ms.locfileid: "70156734"
---
# <a name="tutorial-create-a-windows-machine-learning-uwp-application-c"></a>Руководство: Создание приложения UWP (C#) для Windows Machine Learning

В этом руководстве описано, как создать простое приложение на универсальной платформе Windows, которое использует обученную модель для распознавания цифр, написанных пользователем. В основном это руководство посвящено тому, как загрузить и использовать Windows ML в приложении UWP.

Соответствующие инструкции можно просмотреть в формате видео.

<br/>

> [!VIDEO https://www.youtube.com/embed/yC3HKAv0aj4]

Если вы предпочитаете просмотреть финальную версию кода для этого руководства, см. [репозиторий WinML на GitHub](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/MNIST/UWP/cs). Также доступен аналогичный код на [C++/CX](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/MNIST/UWP/cppcx).

## <a name="prerequisites"></a>Предварительные условия

- Windows 10 версии 1809 и выше;
- [пакет SDK для Windows 10](https://www.microsoft.com/software-download/windowsinsiderpreviewSDK) (сборка 17763 и выше);
- [Visual Studio 2019](https://developer.microsoft.com/windows/downloads) (или Visual Studio 2017 версии 15.7.4 и выше);
- Расширение генератора кода Windows Machine Learning для [Visual Studio 2019](https://marketplace.visualstudio.com/items?itemName=WinML.MLGenV2) или [Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=WinML.mlgen);
- Общие сведения об UWP и C#.

## <a name="1-open-the-project-in-visual-studio"></a>1. Открытие проекта в Visual Studio

Скачав проект из GitHub, запустите Visual Studio и откройте файл **MNIST_Demo.sln** (он должен находиться в папке **&lt;путь_к_репозиторию&gt;\Windows-Machine-Learning\Samples\MNIST\Tutorial\cs**). Если решение отображается как недоступное, нужно щелкнуть проект правой кнопкой мыши в **обозревателе решений** и выбрать **Перезагрузить проект**.

Мы предлагаем шаблон с реализованными событиями и элементами управления XAML, включая следующие:

- [InkCanvas](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inkcanvas) для написания цифр;
- [кнопки](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.button) для интерпретации цифр и очистки холста;
- вспомогательные процедуры для преобразования выходных данных **InkCanvas** в формат [VideoFrame](https://docs.microsoft.com/uwp/api/windows.media.videoframe).

В **обозревателе решений** проект содержит три основных файла с кодом:

- **MainPage.xaml** — весь XAML-код для создания пользовательского интерфейса для **InkCanvas**, кнопок и меток.
- **MainPage.xaml.cs** — здесь находится код приложения.
- **Helper.cs** — вспомогательные процедуры для обрезки и преобразования форматов изображений.

![Обозреватель решений Visual Studio с файлами проекта](../images/get-started1.png)

## <a name="2-build-and-run-the-project"></a>2. Сборка и запуск проекта

Для запуска проекта на локальном компьютере на панели инструментов Visual Studio укажите для параметра **Платформа решения** значение **x64** для 64-битного устройства и значение **x86** для 32-битного. (Разрядность платформы можно проверить в приложении "Параметры" для Windows, щелкнув **Система > О системе > Спецификации устройств > Тип системы**.)

Чтобы запустить проект, нажмите кнопку **Начать отладку** на панели инструментов или клавишу **F5**. Приложение отобразит элемент **InkCanvas**, где пользователи могут написать цифру, кнопку **Распознать**, чтобы интерпретировать эту цифру, поле с пустой меткой, где интерпретированная цифра отобразится в виде текста, и кнопку **Удалить цифру** для очистки **InkCanvas**.

![Снимок экрана приложения](../images/get-started2.png)

> [!NOTE]
> Если проект не компилируется, возможно, нужно изменить целевую версию развертывания для этого проекта. В **обозревателе решений** щелкните проект правой кнопкой мыши и выберите **Свойства**. На вкладке **Приложение** установите значения **целевой** и **минимальной** версий в соответствии с используемыми ОС и SDK.

> [!NOTE]
> Если вы увидите предупреждение о том, что приложение уже установлено, просто щелкните **Да**, чтобы продолжить развертывание. Если и после этого операция не будет выполняться, попробуйте перезапустить Visual Studio.

## <a name="3-download-a-model"></a>3. Скачивание модели

Теперь мы получим модель машинного обучения и добавим ее в приложение. В этом руководстве мы применим предварительно подготовленную модель MNIST, обученную с помощью [Microsoft Cognitive Toolkit (CNTK)](https://docs.microsoft.com/cognitive-toolkit/) и [экспортированную в формат ONNX](https://github.com/onnx/tutorials/blob/master/tutorials/CntkOnnxExport.ipynb).

Модель MNIST уже содержится в папке **Assets**, и вам нужно добавить ее в приложение в качестве существующего элемента. Также вы можете скачать предварительно обученную модель в репозитории [ONNX Model Zoo](https://github.com/onnx/models) на GitHub.

## <a name="4-add-the-model"></a>4. Добавление модели

Щелкните правой кнопкой мыши папку **Assets** в **обозревателе решений** и выберите **Добавить** > **Существующий элемент**. В средстве выбора файлов найдите расположение с моделью ONNX и щелкните **Добавить**.

В проекте должны появиться два новых файла:

- **mnist.onnx** содержит обученную модель;
- **mnist.cs** содержит сгенерированный код Windows ML.

![Обозреватель решений с новыми файлами](../images/get-started3.png)

Чтобы обеспечить сборку модели при компиляции приложения, щелкните правой кнопкой мыши файл **mnist.onnx** и выберите **Свойства**. Для параметра **Действия при сборке** выберите значение **Содержимое**.

Теперь мы перейдем к только что созданному коду в файле **mnist.onnx**. Здесь есть три класса.

- **mnistModel** создает представление модели машинного обучения и сеанс на системном устройстве по умолчанию, привязывает к модели определенные входные и выходные данные, а также асинхронно анализирует модель.
- **mnistInput** инициализирует входные типы, которые ожидает получить модель. В нашем примере на входе ожидается [ImageFeatureValue](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.imagefeaturevalue).
- **mnistOutput** инициализирует типы, которые модель выводит. В нашем примере выходными данными будет список с именем **Plus214_Output_0** и типом [TensorFloat](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.tensorfloat).

Мы применим эти классы для загрузки, привязки и анализа модели в нашем проекте.

## <a name="5-load-bind-and-evaluate-the-model"></a>5. Загрузка, привязка и анализ модели

Для приложений Windows ML мы стараемся придерживаться следующей последовательности действий: загрузка > привязка > анализ.

1. Загрузите модель машинного обучения.
2. Привяжите входные и выходные данные к модели.
3. Выполните анализ модели и просмотрите результаты.

Мы применим код интерфейса, созданный в **mnist.cs**, для загрузки, привязки и анализа модели в нашем приложении.

Во-первых, мы создадим в **MainPage.xaml.cs** экземпляры модели, а также входных и выходных данных. Добавьте следующие переменные-члены в класс **MainPage**.

```csharp
private mnistModel ModelGen;
private mnistInput ModelInput = new mnistInput();
private mnistOutput ModelOutput;
```

Затем мы загрузим модель в **LoadModelAsync**. Этот метод нужно вызывать перед использованием любого из методов модели (то есть в событии [Loaded](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement.loaded) объекта **MainPage**, в переопределении [OnNavigatedTo](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.page.onnavigatedto) или в любом месте до вызова **recognizeButton_Click**). Класс **mnistModel** представляет модель MNIST и создает сеанс на системном устройстве по умолчанию. Чтобы загрузить эту модель, мы вызовем метод **CreateFromStreamAsync**, передавая в качестве параметра ONNX-файл.

```csharp
private async Task LoadModelAsync()
{
    // Load a machine learning model
    StorageFile modelFile = await StorageFile.GetFileFromApplicationUriAsync(new Uri($"ms-appx:///Assets/mnist.onnx"));
    ModelGen = await mnistModel.CreateFromStreamAsync(modelFile as IRandomAccessStreamReference);
}
```

> [!NOTE]
> Если слово **IRandomAccessStreamReference** будет подчеркиваться красной линией, необходимо включить соответствующее пространство имен. Наведите на него курсор и нажмите клавиши **CTRL+.** , а затем выберите в раскрывающемся меню вариант **С использованием Windows.Storage.Streams**.

Теперь нам нужно привязать к модели входные и выходные данные. Созданный код содержит также классы-оболочки **mnistInput** и **mnistOutput**. Класс **mnistInput** представляет ожидаемые входные данные модели, а класс **mnistOutput** — выходные данные модели.

Чтобы инициализировать входной объект модели, вызовите конструктор класса **mnistInput** и передайте ему данные приложения. При этом тип входных данных должен соответствовать тому, который ожидает модель. Класс **mnistInput** ожидает получить **ImageFeatureValue**, поэтому мы создадим для него **ImageFeatureValue** с помощью вспомогательного метода.

Используя включенные в **helper.cs** вспомогательные функции, мы скопируем содержимое **InkCanvas**, преобразуем его в тип **ImageFeatureValue** и привяжем к нашей модели.

```csharp
private async void recognizeButton_Click(object sender, RoutedEventArgs e)
{
    // Bind model input with contents from InkCanvas
    VideoFrame vf = await helper.GetHandWrittenImage(inkGrid);
    ModelInput.Input3 = ImageFeatureValue.CreateFromVideoFrame(vf);
}
```

Для выходных данных мы просто вызовем метод **EvaluateAsync**, передав ему указанные входные данные. После инициализации входных данных вызовите метод **EvaluateAsync** модели, чтобы проанализировать ее по полученным входным данным. **EvaluateAsync** привязывает входные и выходные данные к объекту модели и анализирует модель по входным данным.

Так как модель возвращает тензор, нам необходимо преобразовать его в удобный тип данных и проанализировать полученный список, чтобы найти и отобразить цифру с наибольшей вероятностью.

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

Наконец, мы очистим **InkCanvas**, чтобы пользователь мог написать новую цифру.

```csharp
private void clearButton_Click(object sender, RoutedEventArgs e)
{
    inkCanvas.InkPresenter.StrokeContainer.Clear();
    numberLabel.Text = "";
}
```

## <a name="6-launch-the-application"></a>6. Запуск приложения

Завершив сборку приложения и запустив его (с помощью клавиши **F5**), мы сможем распознать цифру, написанную на **InkCanvas**.

![Полная версия приложения](../images/get-started4.png)

Все готово! Вы создали первое приложение для Windows ML. Дополнительные примеры, демонстрирующие способы использования Windows ML, см. в репозитории [Windows-Machine-Learning](https://github.com/Microsoft/Windows-Machine-Learning) на GitHub.

[!INCLUDE [help](../includes/get-help.md)]
