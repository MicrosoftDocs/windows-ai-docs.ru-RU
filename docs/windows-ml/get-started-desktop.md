---
author: eliotcowley
title: Машинное обучение Windows для настольных ПК (C++) руководства
description: Этом руководстве показано, как создать простое приложение Windows машинного Обучения для рабочего стола.
ms.author: elcowle
ms.date: 5/10/2019
ms.topic: article
keywords: windows 10, windows ai, windows ml, winml, windows machine learning
ms.localizationpriority: medium
ms.custom: RS5
ms.openlocfilehash: 084b9254f8a22bd9163c5494943bc1b48559c9ee
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66182016"
---
# <a name="tutorial-create-a-windows-machine-learning-desktop-application-c"></a>Учебник. Создание приложения рабочем столе Windows компьютера обучения (C++)

API-интерфейсы машинного Обучения Windows можно использовать для взаимодействия с помощью моделей машинного обучения в C++ приложения для настольных компьютеров (Win32). Используя соответствующие трем этапам загрузки, привязки и оценить, приложения могут использовать преимущества возможности машинного обучения.

![Load -> Привязка -> оценки](../images/load-bind-evaluate.png)

Мы создадим несколько упрощенную версию образца SqueezeNet обнаружения объекта, который можно найти в [GitHub](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/SqueezeNetObjectDetection/Desktop/cpp). Вы можете скачать полный пример, если вы хотите увидеть, что ему будет после завершения.

Мы будем использовать C++/WinRT для доступа к API WinML. См. в разделе [ C++/WinRT](https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/) Дополнительные сведения.

В этом руководстве вы узнаете, как:

> [!div class="checklist"]
> * Загрузить модели машинного обучения
> * Загрузить изображение в виде [VideoFrame](https://docs.microsoft.com/uwp/api/windows.media.videoframe)
> * Привязка модели входные и выходные данные
> * Оценка модели и печати значимые результаты

## <a name="prerequisites"></a>предварительные требования

* [Visual Studio 2019](https://developer.microsoft.com/windows/downloads) (или Visual Studio 2017 версии 15.7.4 или более поздней версии)
* [Windows 10, 1809 или более поздней версии](https://www.microsoft.com/software-download/windows10)
* [Пакет SDK для Windows, сборки 17763 или более поздней версии](https://www.microsoft.com/software-download/windowsinsiderpreviewSDK
)
* Расширение Visual Studio для C++/WinRT
    1. В Visual Studio выберите **Сервис > расширения и обновления**.
    2. Выберите **Online** в левой панели и найдите «WinRT», с помощью поля поиска справа.
    3. Выберите  **C++/WinRT**, нажмите кнопку **загрузить**и закройте Visual Studio.
    4. Следуйте инструкциям по установке, а затем снова откройте Visual Studio.
* [Репозиторий Github для Windows-Machine-Learning](https://github.com/Microsoft/Windows-Machine-Learning) (можно скачать его как ZIP-файл или клонировать на компьютер)

## <a name="create-the-project"></a>Создание проекта

Во-первых мы создадим проект в Visual Studio.

1. Выберите **файл > Создать > проект** открыть **новый проект** окна.
2. В левой области выберите **установленные > Visual C++ > Windows Desktop**и в середине, выберите **консольное приложение Windows (C++/WinRT)**.
3. Присвойте проекту **имя** и **расположение**, затем нажмите кнопку **ОК**.
4. В **новый проект универсальной платформы Windows** окне **целевой** и **версий менее** сборки 17763 или более поздней версии, и нажмите кнопку **ОК**.
5. Убедитесь, что заданы раскрывающиеся меню в верхней части панели инструментов **Отладка** и либо **x64** или **x86** в зависимости от архитектуры компьютера.
6. Нажмите клавишу **Ctrl + F5** запускать программу без отладки. Окно терминала следует открывать с определенным текстом «Hello world». Нажмите любую клавишу, чтобы закрыть его.

## <a name="load-the-model"></a>Загрузить модель

Далее, мы загрузим модели ONNX в нашей программы с помощью [LearningModel.LoadFromFilePath](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodel.loadfromfilepath):

1. В **pch.h** (в **файлы заголовков** папку), добавьте следующий `include` инструкций (это предоставить нам доступ ко всем API, которые потребуются):
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

2. В **main.cpp** (в **исходные файлы** папку), добавьте следующий `using` инструкции:
    ```cpp
    using namespace Windows::AI::MachineLearning;
    using namespace Windows::Foundation::Collections;
    using namespace Windows::Graphics::Imaging;
    using namespace Windows::Media;
    using namespace Windows::Storage;

    using namespace std;
    ```

3. Добавьте следующие объявления переменных после `using` инструкции:
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

4. Добавьте следующие объявления прямой после глобальные переменные:
    ```cpp
    // Forward declarations
    void LoadModel();
    VideoFrame LoadImageFile(hstring filePath);
    void BindModel();
    void EvaluateModel();
    void PrintResults(IVectorView<float> results);
    void LoadLabels();
    ```

5. В **main.cpp**, удалите код, «Hello world» (все, что в `main` работать после `init_apartment`).
6. Найти **SqueezeNet.onnx** файл в своей локальной копии **Windows-Machine-Learning** репозитория. Он должен быть расположен в **\Windows-Machine-Learning\SharedContent\models**.
7. Копировать путь к файлу и назначьте его вашей `modelPath` переменной, где мы определили вверху. Не забудьте перед строкой `L` для упрощения строку расширенных символов, чтобы она правильно работает с `hstring`и чтобы экранировать все символы обратной косой черты (`\`) с помощью дополнительной обратной косой черты. Пример:
    ```cpp
    hstring modelPath = L"C:\\Repos\\Windows-Machine-Learning\\SharedContent\\models\\SqueezeNet.onnx";
    ```

8. Во-первых, мы реализуем `LoadModel` метод. Добавьте следующий метод после `main` метод. Этот метод загружает модель и выводит, сколько времени прошло:
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

9. Наконец, вызовите этот метод из `main` метод:
    ```cpp
    LoadModel();
    ```

10. Запуск программы без отладки. Вы увидите, что модель успешно загружает!

## <a name="load-the-image"></a>Загрузить изображение

После этого мы загрузим файл изображения в нашей программе:

1. Добавьте следующий метод. Этот метод будет загружать изображения из заданного пути и создавать [VideoFrame](https://docs.microsoft.com/uwp/api/windows.media.videoframe) от него:
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

2. Добавьте вызов этого метода в `main` метод:
    ```cpp
    imageFrame = LoadImageFile(imagePath);
    ```

3. Найти **мультимедиа** папки в своей локальной копии **Windows-Machine-Learning** репозитория. Он должен быть расположен в **\Windows-Machine-Learning\SharedContent\media**.
4. Выберите один из образов в этой папке и присвойте его путь к `imagePath` переменной, где мы определили вверху. Не забудьте перед ними `L` казаться строку расширенных символов и чтобы экранировать все символы обратной косой черты с дополнительную обратную косую черту. Пример:
    ```cpp
    hstring imagePath = L"C:\\Repos\\Windows-Machine-Learning\\SharedContent\\media\\kitten_224.png";
    ```

5. Запустите программу без отладки. Вы должны увидеть образ успешно загружен.

## <a name="bind-the-input-and-output"></a>Привязки входных и выходных данных

Далее мы создадим на основе модели сеанса и привязать вход и выход из сеанса с помощью [LearningModelBinding.Bind](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodelbinding.bind). Дополнительные сведения о привязке см. в разделе [привязка модели](bind-a-model.md).

1. Реализуйте `BindModel` метод. При этом создается сеанс, основываясь на модели и устройства и привязке, основанные на этом сеансе. Затем привязки к переменных, которые мы создали, используя их имена входов и выходов. Мы смогли узнать заранее входных признаков с именем «data_0» и возможность выходных данных с именем «softmaxout_1». Эти свойства для любой модели можно просмотреть, открыв их в [Netron](https://lutzroeder.github.io/Netron/), средство визуализации модель online.
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

2. Добавьте вызов `BindModel` из `main` метод:
    ```cpp
    BindModel();
    ```

3. Запустите программу без отладки. Входные и выходные данные модели должен быть привязан успешно. Нам осталось совсем немного!

## <a name="evaluate-the-model"></a>Оценка модели

Теперь вы в последний шаг в диаграмме в начале этого руководства, **Evaluate**. Мы будем оценивать модели с помощью [LearningModelSession.Evaluate](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodelsession.evaluate):

1. Реализуйте `EvaluateModel` метод. Этот метод принимает наши сеанса и оценивает его с помощью нашей привязкой и идентификатор корреляции. Идентификатор корреляции — это то, что мы теоретически могут использовать позже в соответствии с конкретной оценки вызов выходные результаты. Опять же мы знаем, заранее, что имя выходных данных является «softmaxout_1».
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

2. Теперь давайте реализуем `PrintResults`. Этот метод возвращает верхний три значения вероятности для какой объект может быть на рисунке и выводит их:
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

3. Кроме того, нам нужно реализовать `LoadLabels`. Этот метод открывает файл метки, который содержит все разных объектов модели можно узнать что выполняет синтаксический анализ его:
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

4. Найдите **Labels.txt** файл в своей локальной копии **Windows-Machine-Learning** репозитория. Он должен находиться в **\Windows-Machine-Learning\Samples\SqueezeNetObjectDetection\Desktop\cpp**.
5. Назначьте путь к файлу `labelsFilePath` переменной, где мы определили вверху. Не забудьте экранировать все символы обратной косой черты с дополнительную обратную косую черту. Пример:
    ```cpp
    string labelsFilePath = "C:\\Repos\\Windows-Machine-Learning\\Samples\\SqueezeNetObjectDetection\\Desktop\\cpp\\Labels.txt";
    ```

6. Добавьте вызов `EvaluateModel` в `main` метод:
    ```cpp
    EvaluateModel();
    ```
    
7. Запустите программу без отладки. Он должен теперь правильно распознает что такое образ! Ниже приведен пример, что он может выводить:
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

## <a name="next-steps"></a>Следующие шаги

Ура, у вас есть определение объекта, работа C++ классического приложения! После этого попробуйте использовать аргументы командной строки для ввода модели и файлов изображений, а не жестко их, аналогичную образцы на GitHub. Вы также можете попробовать под управлением ознакомительную версию на другом устройстве, таких как GPU, чтобы увидеть, как отличается производительность.

Поэкспериментируйте с другими примерами на GitHub и расширить их так, как вам нравится!

## <a name="see-also"></a>См. также

* [Примеры машинного Обучения Windows (GitHub)](https://github.com/Microsoft/Windows-Machine-Learning/tree/master)
* [Пространство имен Windows.AI.MachineLearning](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning)
* [Windows ML](index.md)

[!INCLUDE [help](../includes/get-help.md)]
