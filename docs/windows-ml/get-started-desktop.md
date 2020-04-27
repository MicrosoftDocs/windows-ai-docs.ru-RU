---
title: Руководство по машинному обучению Windows для классических приложений (C++)
description: В этом руководстве показано, как создать простое классическое приложение для Машинного обучения Windows.
ms.date: 5/10/2019
ms.topic: article
keywords: windows 10, windows ai, windows ml, winml, windows machine learning
ms.localizationpriority: medium
ms.custom: RS5
ms.openlocfilehash: 619a0c39b824abc2ed2eaee1ca8f95f95a4aa9c7
ms.sourcegitcommit: 2139506ff12b7205283288c4bbac866ddfa812f3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/24/2020
ms.locfileid: "70157668"
---
# <a name="tutorial-create-a-windows-machine-learning-desktop-application-c"></a>Руководство: Создание классического приложения (C++) для Windows Machine Learning

Для взаимодействия с моделями машинного обучения в классических приложениях C++ (Win32) можно использовать API Windows ML. Трехэтапный процесс загрузки, привязки и оценки позволяет включить в любое приложение мощные функции машинного обучения.

![Загрузка > привязка > анализ.](../images/load-bind-evaluate.png)

В этом руководстве описано, как создать упрощенную версию примера SqueezeNet для обнаружения объектов, который размещен на [GitHub](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/SqueezeNetObjectDetection/Desktop/cpp). Вы можете скачать полный пример, если хотите изучить его финальную версию.

Для доступа к API WinML мы будем использовать C++/WinRT. Дополнительные сведения см. в документации по [C++/WinRT](https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/).

В этом руководстве описано, как выполнять следующие операции:

> [!div class="checklist"]
> * загрузка модели машинного обучения;
> * загрузка изображения в формате [VideoFrame](https://docs.microsoft.com/uwp/api/windows.media.videoframe);
> * привязка входных и выходных данных к модели;
> * анализ модели и вывод информативных результатов.

## <a name="prerequisites"></a>Предварительные условия

* [Visual Studio 2019](https://developer.microsoft.com/windows/downloads) (или Visual Studio 2017 версии 15.7.4 и выше)
* [Windows 10 версии 1809 и выше](https://www.microsoft.com/software-download/windows10)
* [Windows SDK сборки 17763 и выше](https://www.microsoft.com/software-download/windowsinsiderpreviewSDK
)
* Расширение C++/WinRT для Visual Studio
    1. В Visual Studio щелкните **Сервис > Расширения и обновления**.
    2. Выберите **В сети** на панели слева и выполните поиск по запросу WinRT в поле поиска справа.
    3. Выберите **C++/WinRT**, щелкните **Загрузить** и закройте Visual Studio.
    4. Выполните инструкции по установке, затем снова откройте Visual Studio.
* [Репозиторий Windows-Machine-Learning на сайте GitHub](https://github.com/Microsoft/Windows-Machine-Learning) (вы можете скачать его как ZIP-файл или клонировать на локальный компьютер).

## <a name="create-the-project"></a>Создание проекта

Первым делом мы создадим проект в Visual Studio.

1. Щелкните **Файл > Создать > Проект**, чтобы открыть окно **Новый проект**.
2. На панели слева щелкните **Установленные > Visual C++ > Windows Desktop**, а затем в средней части выберите **Консольное приложение для Windows (C++/WinRT)** .
3. Укажите для нового проекта **имя** и **расположение**, а затем щелкните **OK**.
4. В окне **Новый проект приложения для универсальной платформы Windows** задайте для **целевой** и **минимальной** версий значение не ниже сборки 17763, а затем щелкните **ОК**.
5. Убедитесь, что в раскрывающихся меню на панели инструментов вверху выбраны значения **Отладка** и **x64** или **x86** в соответствии с архитектурой вашего компьютера.
6. Чтобы запустить программу без отладки, нажмите клавиши **CTRL+F5**. Должен открыться терминал с текстом Hello world. Нажмите любую клавишу, чтобы закрыть его.

## <a name="load-the-model"></a>Загрузка модели

Теперь мы загрузим модель ONNX в нашу программу с помощью [LearningModel.LoadFromFilePath](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodel.loadfromfilepath):

1. В **pch.h** (в папке **Header Files**) добавьте следующие инструкции `include` (они предоставляют доступ ко всем нужным API):
    ```cpp
    #include <winrt/Windows.AI.MachineLearning.h>
    #include <winrt/Windows.Foundation.Collections.h>
    #include <winrt/Windows.Graphics.Imaging.h>
    #include <winrt/Windows.Media.h>
    #include <winrt/Windows.Storage.h>

    #include <string>
    #include <fstream>

    #include <Windows.h>
    ```

2. В **main.cpp** (в папке **Source Files**) добавьте следующие инструкции `using`:
    ```cpp
    using namespace Windows::AI::MachineLearning;
    using namespace Windows::Foundation::Collections;
    using namespace Windows::Graphics::Imaging;
    using namespace Windows::Media;
    using namespace Windows::Storage;

    using namespace std;
    ```

3. Добавьте следующие объявления переменных после инструкций `using`:
    ```cpp
    // Global variables
    hstring modelPath;
    string deviceName = "default";
    hstring imagePath;
    LearningModel model = nullptr;
    LearningModelDeviceKind deviceKind = LearningModelDeviceKind::Default;
    LearningModelSession session = nullptr;
    LearningModelBinding binding = nullptr;
    VideoFrame imageFrame = nullptr;
    string labelsFilePath;
    vector<string> labels;
    ```

4. Добавьте следующие опережающие объявления после глобальных переменных:
    ```cpp
    // Forward declarations
    void LoadModel();
    VideoFrame LoadImageFile(hstring filePath);
    void BindModel();
    void EvaluateModel();
    void PrintResults(IVectorView<float> results);
    void LoadLabels();
    ```

5. В **main.cpp** удалите код Hello World (все строки в функции `main` после `init_apartment`).
6. Найдите файл **SqueezeNet.onnx** в локальной копии репозитория **Windows-Machine-Learning**. Он должен располагаться в папке **\Windows-Machine-Learning\SharedContent\models**.
7. Скопируйте путь к этому файлу и сохраните его в переменной `modelPath`, добавив в строку определения выше. Не забудьте добавить к строке префикс `L`, чтобы она принимала расширенные символы и правильно работала с `hstring`, а также экранировать все символы обратной косой черты (`\`), добавив к ним еще одну обратную косую черту. Например:
    ```cpp
    hstring modelPath = L"C:\\Repos\\Windows-Machine-Learning\\SharedContent\\models\\SqueezeNet.onnx";
    ```

8. Прежде всего мы реализуем метод `LoadModel`. Теперь добавьте следующий метод после метода `main`. Этот метод загружает модель и выводит затраченное на это время:
    ```cpp
    void LoadModel()
    {
        // load the model
        printf("Loading modelfile '%ws' on the '%s' device\n", modelPath.c_str(), deviceName.c_str());
        DWORD ticks = GetTickCount();
        model = LearningModel::LoadFromFilePath(modelPath);
        ticks = GetTickCount() - ticks;
        printf("model file loaded in %d ticks\n", ticks);
    }
    ```

9. И наконец, добавьте вызов этого метода из метода `main`:
    ```cpp
    LoadModel();
    ```

10. Запустите программу без отладки. Вы увидите, что модель успешно загружена.

## <a name="load-the-image"></a>Загрузка изображения

Далее мы загрузим в программу файл изображения:

1. Добавьте следующий метод. Этот метод загрузит изображение из заданного пути и создаст соответствующий объект [VideoFrame](https://docs.microsoft.com/uwp/api/windows.media.videoframe):
    ```cpp
    VideoFrame LoadImageFile(hstring filePath)
    {
        printf("Loading the image...\n");
        DWORD ticks = GetTickCount();
        VideoFrame inputImage = nullptr;

        try
        {
            // open the file
            StorageFile file = StorageFile::GetFileFromPathAsync(filePath).get();
            // get a stream on it
            auto stream = file.OpenAsync(FileAccessMode::Read).get();
            // Create the decoder from the stream
            BitmapDecoder decoder = BitmapDecoder::CreateAsync(stream).get();
            // get the bitmap
            SoftwareBitmap softwareBitmap = decoder.GetSoftwareBitmapAsync().get();
            // load a videoframe from it
            inputImage = VideoFrame::CreateWithSoftwareBitmap(softwareBitmap);
        }
        catch (...)
        {
            printf("failed to load the image file, make sure you are using fully qualified paths\r\n");
            exit(EXIT_FAILURE);
        }

        ticks = GetTickCount() - ticks;
        printf("image file loaded in %d ticks\n", ticks);
        // all done
        return inputImage;
    }
    ```

2. Добавьте вызов этого метода в метод `main`:
    ```cpp
    imageFrame = LoadImageFile(imagePath);
    ```

3. Найдите папку **media** в локальной копии репозитория **Windows-Machine-Learning**. Она должна располагаться в каталоге **\Windows-Machine-Learning\SharedContent\media**.
4. Выберите любое изображение из этой папки и сохраните путь к нему в переменной`imagePath`, добавив его в строку определения выше. Не забудьте добавить к пути префикс `L`, чтобы он принимал расширенные символы, а также экранировать все символы обратной косой черты, добавив еще одну обратную косую черту. Например:
    ```cpp
    hstring imagePath = L"C:\\Repos\\Windows-Machine-Learning\\SharedContent\\media\\kitten_224.png";
    ```

5. Запустите программу без отладки. Вы увидите, что изображение успешно загружено.

## <a name="bind-the-input-and-output"></a>Привязка входных и выходных данных

Теперь нам нужно создать сеанс на основе модели и привязать входные и выходные данные этого сеанса с помощью [LearningModelBinding.Bind](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodelbinding.bind). См. сведения о том, как выполнять [привязку модели](bind-a-model.md).

1. Реализуйте метод `BindModel`. Он создает сеанс на основе модели и устройства, а также реализует привязку на основе этого сеанса. Затем мы привяжем входные и выходные данные к ранее созданным переменным, указывая их имена. Мы знаем, что компонент входных данных имеет имя data_0, а выходных данных — softmaxout_1. Эти свойства для любой модели можно просмотреть, открыв их в интерактивном средстве визуализации моделей [Netron](https://lutzroeder.github.io/Netron/).
    ```cpp
    void BindModel()
    {
        printf("Binding the model...\n");
        DWORD ticks = GetTickCount();

        // now create a session and binding
        session = LearningModelSession{ model, LearningModelDevice(deviceKind) };
        binding = LearningModelBinding{ session };
        // bind the intput image
        binding.Bind(L"data_0", ImageFeatureValue::CreateFromVideoFrame(imageFrame));
        // bind the output
        vector<int64_t> shape({ 1, 1000, 1, 1 });
        binding.Bind(L"softmaxout_1", TensorFloat::Create(shape));

        ticks = GetTickCount() - ticks;
        printf("Model bound in %d ticks\n", ticks);
    }
    ```

2. Добавьте вызов `BindModel` из метода `main`:
    ```cpp
    BindModel();
    ```

3. Запустите программу без отладки. Вы увидите, что входные и выходные данные модели успешно привязаны. Осталось совсем немного.

## <a name="evaluate-the-model"></a>Анализ модели

Теперь нам надо выполнить последний шаг, **Анализ**, как показано на схеме в начале этого руководства. Для этого мы применим [LearningModelSession.Evaluate](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodelsession.evaluate):

1. Реализуйте метод `EvaluateModel`. Этот метод принимает сеанс и вычисляет его, используя указанную ранее привязку и идентификатор корреляции. Идентификатор корреляции мы можем применить позже для сопоставления определенного вызова анализа с выходными результатами. Опять же, мы знаем, что выход имеет имя softmaxout_1.
    ```cpp
    void EvaluateModel()
    {
        // now run the model
        printf("Running the model...\n");
        DWORD ticks = GetTickCount();

        auto results = session.Evaluate(binding, L"RunId");

        ticks = GetTickCount() - ticks;
        printf("model run took %d ticks\n", ticks);

        // get the output
        auto resultTensor = results.Outputs().Lookup(L"softmaxout_1").as<TensorFloat>();
        auto resultVector = resultTensor.GetAsVectorView();
        PrintResults(resultVector);
    }
    ```

2. Теперь мы реализуем `PrintResults`. Этот метод получает три значения вероятности того, что объект будет представлен на изображении, и выводит их:
    ```cpp
    void PrintResults(IVectorView<float> results)
    {
        // load the labels
        LoadLabels();
        // Find the top 3 probabilities
        vector<float> topProbabilities(3);
        vector<int> topProbabilityLabelIndexes(3);
        // SqueezeNet returns a list of 1000 options, with probabilities for each, loop through all
        for (uint32_t i = 0; i < results.Size(); i++)
        {
            // is it one of the top 3?
            for (int j = 0; j < 3; j++)
            {
                if (results.GetAt(i) > topProbabilities[j])
                {
                    topProbabilityLabelIndexes[j] = i;
                    topProbabilities[j] = results.GetAt(i);
                    break;
                }
            }
        }
        // Display the result
        for (int i = 0; i < 3; i++)
        {
            printf("%s with confidence of %f\n", labels[topProbabilityLabelIndexes[i]].c_str(), topProbabilities[i]);
        }
    }
    ```

3. Нам также нужно реализовать `LoadLabels`. Этот метод открывает файл меток, который содержит все распознаваемые моделью объекты, и анализирует его:
    ```cpp
    void LoadLabels()
    {
        // Parse labels from labels file.  We know the file's entries are already sorted in order.
        ifstream labelFile{ labelsFilePath, ifstream::in };
        if (labelFile.fail())
        {
            printf("failed to load the %s file.  Make sure it exists in the same folder as the app\r\n", labelsFilePath.c_str());
            exit(EXIT_FAILURE);
        }

        std::string s;
        while (std::getline(labelFile, s, ','))
        {
            int labelValue = atoi(s.c_str());
            if (labelValue >= labels.size())
            {
                labels.resize(labelValue + 1);
            }
            std::getline(labelFile, s);
            labels[labelValue] = s;
        }
    }
    ```

4. Найдите файл **Labels.txt** в локальной копии репозитория **Windows-Machine-Learning**. Он должен находиться в каталоге **\Windows-Machine-Learning\Samples\SqueezeNetObjectDetection\Desktop\cpp**.
5. Сохраните путь к этому файлу в переменной `labelsFilePath`, добавив в строку определения выше. Не забудьте экранировать все символы обратной косой черты, добавив еще одну обратную косую черту. Например:
    ```cpp
    string labelsFilePath = "C:\\Repos\\Windows-Machine-Learning\\Samples\\SqueezeNetObjectDetection\\Desktop\\cpp\\Labels.txt";
    ```

6. Добавьте вызов `EvaluateModel` в метод `main`:
    ```cpp
    EvaluateModel();
    ```

7. Запустите программу без отладки. Теперь она должна правильно распознать, что представлено на изображении. Ниже приведен типичный пример выходных данных.
    ```sh
    Loading modelfile 'C:\Repos\Windows-Machine-Learning\SharedContent\models\SqueezeNet.onnx' on the 'default' device
    model file loaded in 250 ticks
    Loading the image...
    image file loaded in 78 ticks
    Binding the model...Model bound in 15 ticks
    Running the model...
    model run took 16 ticks
    tabby, tabby cat with confidence of 0.931461
    Egyptian cat with confidence of 0.065307
    Persian cat with confidence of 0.000193
    ```

## <a name="next-steps"></a>Дальнейшие действия

Браво! Вы реализовали функцию распознавания объектов в классическом приложении C++! Теперь вы можете настроить аргументы командной строки для ввода файлов модели, как реализовано в примере на GitHub, чтобы не прописывать эти значения в коде программы. Вы также можете выполнить анализ на другом устройстве, например в графическом процессоре, и сравнить производительность работы.

Потренируйтесь также на других примерах с GitHub и дополните их на свой вкус!

## <a name="see-also"></a>См. также статью

* [Примеры для Windows ML (GitHub)](https://github.com/Microsoft/Windows-Machine-Learning/tree/master)
* [Пространство имен Windows.AI.MachineLearning](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning)
* [Windows ML](index.md)

[!INCLUDE [help](../includes/get-help.md)]
