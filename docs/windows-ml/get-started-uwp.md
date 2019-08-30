---
title: Создание приложения Windows Машинное обучение UWP (C#)
description: В этом пошаговом руководстве показано, как вы можете создать свое первое приложение UWP с помощью Машинного обучения Windows.
ms.date: 5/10/2019
ms.topic: article
keywords: windows 10, uwp, машинное обучение в windows, winml, windows ML
ms.localizationpriority: medium
ms.custom: RS5
ms.openlocfilehash: 4a8e46835b0018a8057c1056c6dd59b9589b0f9c
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70156734"
---
# <a name="tutorial-create-a-windows-machine-learning-uwp-application-c"></a>Учебник. Создание приложения Windows Машинное обучение UWP (C#)

В этом руководстве мы создадим простое приложение универсальная платформа Windows, которое использует обученную модель машинного обучения для распознавания числовой цифры, рисуемой пользователем. В этом руководстве основное внимание уделяется тому, как загружать и использовать Windows ML в приложении UWP.

В следующем видео рассматривается пример, на котором основан этот учебник.

<br/>

> [!VIDEO https://www.youtube.com/embed/yC3HKAv0aj4]

Если вы предпочитаете ознакомиться с кодом завершенного учебника, его можно найти в [репозитории WinML GitHub](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/MNIST/UWP/cs). Он также доступен в языке [ C++/CX](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/MNIST/UWP/cppcx).

## <a name="prerequisites"></a>Предварительные требования

- Windows 10 (версия 1809 или более поздняя)
- [Пакет SDK для Windows 10](https://www.microsoft.com/software-download/windowsinsiderpreviewSDK) (Сборка 17763 или более поздняя)
- [Visual Studio 2019](https://developer.microsoft.com/windows/downloads) (или Visual Studio 2017, версия 15.7.4 или более поздняя)
- Расширение генератора кода Windows Машинное обучение для [Visual Studio 2019](https://marketplace.visualstudio.com/items?itemName=WinML.MLGenV2) или [2017](https://marketplace.visualstudio.com/items?itemName=WinML.mlgen)
- Основные UWP и C# набор знаний

## <a name="1-open-the-project-in-visual-studio"></a>1. Открытие проекта в Visual Studio

После загрузки проекта из GitHub запустите Visual Studio и откройте файл **MNIST_Demo. sln** (он должен находиться по  **&lt;пути к репозиторию&gt;\виндовс-Мачине-леарнинг\самплес\мнист\туториал\кс**). Если решение отображается как недоступное, необходимо щелкнуть правой кнопкой мыши проект в **Обозреватель решений** и выбрать **Перезагрузить проект**.

Мы предлагаем шаблон с реализованными событиями и элементами управления XAML, включая:

- [InkCanvas](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inkcanvas) для написания цифр.
- [Кнопки](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.button) для интерпретации цифр и очистки холста.
- Вспомогательные подпрограммы для преобразования вывода **InkCanvas** в [видеофраме](https://docs.microsoft.com/uwp/api/windows.media.videoframe).

Внутри **Обозреватель решений**проект содержит три основных файла кода:

- **MainPage. XAML** — весь наш код XAML для создания пользовательского интерфейса для **InkCanvas**, кнопок и меток.
- **MainPage.XAML.CS** — там, где находится наш код приложения.
- **Helper.CS** — вспомогательные подпрограммы для кадрирования и преобразования форматов изображений.

![Обозреватель решений Visual Studio с файлами проекта](../images/get-started1.png)

## <a name="2-build-and-run-the-project"></a>2. Сборка и запуск проекта

На панели инструментов Visual Studio измените **платформу решения** на **x64** , чтобы запустить проект на локальном компьютере, если устройство является 64-разрядным, или **x86** , если оно 32-бит. (Вы можете проверить приложение "Параметры Windows": **Системные > о > спецификациях устройств > системном типе**.)

Чтобы запустить проект, нажмите кнопку **начать отладку** на панели инструментов или нажмите клавишу **F5**. Приложение должно отображать **InkCanvas** , где пользователи могут писать цифру, кнопку **распознавания** для интерпретации числа, пустое поле метки, в котором интерпретируемая цифра будет отображаться как текст, и кнопку « **очистить цифру** », чтобы очистить  **InkCanvas**.

![Снимок экрана приложения](../images/get-started2.png)

> [!NOTE]
> Если проект не будет построен, может потребоваться изменить целевую версию развертывания проекта. Щелкните правой кнопкой мыши проект в **Обозреватель решений** и выберите пункт **свойства**. На вкладке **приложение** задайте **целевую версию** и **версию минимальной версии** в соответствии с ОС и пакетом SDK.

> [!NOTE]
> Если вы получаете предупреждение о том, что приложение уже установлено, просто выберите **Да** , чтобы продолжить развертывание. Возможно, потребуется закрыть Visual Studio и снова открыть его, если он по-прежнему не работает.

## <a name="3-download-a-model"></a>3. Загрузка модели

Теперь давайте создадим модель машинного обучения для добавления в наше приложение. В этом руководстве мы будем использовать предварительно обученную модель MNIST, которая была обучена [Microsoft Cognitive Toolkit (CNTK)](https://docs.microsoft.com/cognitive-toolkit/) и [экспортирована в формат ONNX](https://github.com/onnx/tutorials/blob/master/tutorials/CntkOnnxExport.ipynb).

Модель MNIST уже включена в папку Assets, и ее необходимо будет добавить в приложение в качестве существующего элемента. Также можно скачать предварительно обученную модель из раздела [ONNX Model Zoo](https://github.com/onnx/models) на GitHub.

## <a name="4-add-the-model"></a>4. Добавьте модель

Щелкните правой кнопкой мыши папку Assets в **Обозреватель решений**и выберите команду **добавить** > **существующий элемент**. Укажите в средстве выбора файлов расположение модели ONNX и нажмите кнопку **Добавить**.

В проекте должны появиться два новых файла:

- **mnist. onnx** — ваша обученная модель.
- **mnist.CS** — код, созданный машинным кодом Windows.

![Обозреватель решений с новыми файлами](../images/get-started3.png)

Чтобы обеспечить построение модели при компиляции приложения, щелкните правой кнопкой мыши файл **mnist. onnx** и выберите пункт **свойства**. Для **Действия при сборке** выберите **Содержимое**.

Теперь рассмотрим только что созданный код в файле **mnist.CS** . У нас есть три класса:

- **мнистмодел** создает представление модели машинного обучения, создает сеанс на системном устройстве по умолчанию, привязывает определенные входные и выходные данные к модели и оценивает модель в асинхронном режиме.
- **мнистинпут** инициализирует входные типы, которые предположительно представляются в модели. В этом случае входные данные предполагают [имажефеатуревалуе](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.imagefeaturevalue).
- **мнистаутпут** инициализирует типы, которые будут выводиться в модели. В этом случае выходные данные будут представлять собой список с именем **Plus214_Output_0** типа [тенсорфлоат](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.tensorfloat).

Теперь мы используем эти классы для загрузки, привязки и оценки модели в нашем проекте.

## <a name="5-load-bind-and-evaluate-the-model"></a>5. Загрузка, привязка и оценка модели

Для приложений машинного обучения Windows требуется следующий шаблон: > Вычисления привязки > Load.

1. Загрузка модели машинного обучения.
2. Привязка входных и выходных данных к модели.
3. Оценка модели и просмотр результатов.

Мы будем использовать код интерфейса, созданный в **mnist.CS** для загрузки, привязки и вычисления модели в нашем приложении.

Во первых, в **MainPage.XAML.CS**, давайте создадим экземпляр модели, входные и выходные данные. Добавьте следующие переменные члена в класс **MainPage** :

```csharp
private mnistModel ModelGen;
private mnistInput ModelInput = new mnistInput();
private mnistOutput ModelOutput;
```

Затем в **лоадмоделасинк**мы загружаем модель. Этот метод следует вызывать перед использованием любого из методов модели (т. е. в [загруженном](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement.loaded) событии **MainPage**, при переопределении [OnNavigatedTo](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.page.onnavigatedto) или в любом месте до вызова **recognizeButton_Click** ). Класс **мнистмодел** представляет модель MNIST и создает сеанс на системном устройстве по умолчанию. Чтобы загрузить модель, мы вызываем метод **креатефромстреамасинк** , передав в него файл ONNX в качестве параметра.

```csharp
private async Task LoadModelAsync()
{
    // Load a machine learning model
    StorageFile modelFile = await StorageFile.GetFileFromApplicationUriAsync(new Uri($"ms-appx:///Assets/mnist.onnx"));
    ModelGen = await mnistModel.CreateFromStreamAsync(modelFile as IRandomAccessStreamReference);
}
```

> [!NOTE]
> Если в разделе **ирандомакцессстреамреференце**появляется красная подчеркивание, необходимо включить его пространство имен. Наведите курсор на него, нажмите клавиши **CTRL +.** и выберите в раскрывающемся меню пункт **Использование Windows. Storage. Streams** .

Далее необходимо привязать наших входные и выходные данные к модели. Созданный код также содержит классы-оболочки **мнистинпут** и **мнистаутпут** . Класс **мнистинпут** представляет ожидаемые входные данные модели, а класс **мнистаутпут** представляет ожидаемые выходные данные модели.

Чтобы инициализировать входной объект модели, вызовите конструктор класса **мнистинпут** , передав данные приложения, и убедитесь, что входные данные соответствуют типу входных данных, предполагаемому для вашей модели. Класс **мнистинпут** ожидает **имажефеатуревалуе**, поэтому мы используем вспомогательный метод для получения **имажефеатуревалуе** для входных данных.

Используя наши вспомогательные функции в **Helper.CS**, мы будем копировать содержимое **InkCanvas**, преобразовывать его в тип **имажефеатуревалуе**и привязывать его к нашей модели.

```csharp
private async void recognizeButton_Click(object sender, RoutedEventArgs e)
{
    // Bind model input with contents from InkCanvas
    VideoFrame vf = await helper.GetHandWrittenImage(inkGrid);
    ModelInput.Input3 = ImageFeatureValue.CreateFromVideoFrame(vf);
}
```

Для выходных данных мы просто вызываем **евалуатеасинк** с указанными входными данными. После инициализации входных данных вызовите метод **евалуатеасинк** модели для вычисления модели на входные данные. **Евалуатеасинк** привязывает входные и выходные данные к объекту модели и вычисляет модель для входных данных.

Поскольку модель возвращает выходной тензорные, сначала нужно преобразовать его в понятный тип данных, а затем проанализировать возвращенный список, чтобы определить, какая цифра имела наибольшую вероятность, и отобразить ее.

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

Наконец, мы хотим удалить **InkCanvas** , чтобы пользователи могли нарисовать еще одно число.

```csharp
private void clearButton_Click(object sender, RoutedEventArgs e)
{
    inkCanvas.InkPresenter.StrokeContainer.Clear();
    numberLabel.Text = "";
}
```

## <a name="6-launch-the-application"></a>6. Запуск приложения

После сборки и запуска приложения (нажмите клавишу **F5**) мы сможем распознать число, нарисованное на **InkCanvas**.

![завершить приложение](../images/get-started4.png)

Мы сделали свое первое приложение для машинного обучения Windows! Дополнительные примеры, демонстрирующие использование Windows ML, см. в репозитории [машинного обучения Windows](https://github.com/Microsoft/Windows-Machine-Learning) на сайте GitHub.

[!INCLUDE [help](../includes/get-help.md)]
