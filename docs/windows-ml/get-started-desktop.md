---
title: Учебник по Windows Машинное обучение дляC++Desktop ()
description: В этом руководстве показано, как создать простое классическое приложение для Машинного обучения Windows.
ms.date: 5/10/2019
ms.topic: article
keywords: windows 10, windows ai, windows ml, winml, windows machine learning
ms.localizationpriority: medium
ms.custom: RS5
ms.openlocfilehash: 619a0c39b824abc2ed2eaee1ca8f95f95a4aa9c7
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157668"
---
# <a name="tutorial-create-a-windows-machine-learning-desktop-application-c"></a>Учебник. Создание классического приложения Windows Машинное обучение (C++)

Для взаимодействия с моделями машинного обучения в C++ приложениях для настольных систем (Win32) можно использовать API-интерфейсы Windows ml. С помощью трех этапов загрузки, привязки и оценки приложение может воспользоваться преимуществами машинного обучения.

![Оценка > привязки > нагрузки](../images/load-bind-evaluate.png)

Мы создадим несколько упрощенную версию примера обнаружения объектов Скуизенет, которая доступна на сайте [GitHub](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/SqueezeNetObjectDetection/Desktop/cpp). Вы можете скачать полный пример, если вы хотите узнать, как он будет выглядеть после завершения.

Мы будем использовать C++/WinRT для доступа к интерфейсам API WinML. Дополнительные сведения см. в разделе [ C++/WinRT](https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/) .

В этом учебнике вы научитесь:

> [!div class="checklist"]
> * Загрузка модели машинного обучения
> * Загрузка изображения в виде [видеофраме](https://docs.microsoft.com/uwp/api/windows.media.videoframe)
> * Привязка входных и выходных данных модели
> * Оценка модели и печать значимых результатов

## <a name="prerequisites"></a>Предварительные требования

* [Visual Studio 2019](https://developer.microsoft.com/windows/downloads) (или Visual Studio 2017, версия 15.7.4 или более поздняя)
* [Windows 10, версия 1809 или более поздняя](https://www.microsoft.com/software-download/windows10)
* [Windows SDK, сборка 17763 или более поздняя](https://www.microsoft.com/software-download/windowsinsiderpreviewSDK
)
* Расширение Visual Studio для C++/WinRT
    1. В Visual Studio выберите **инструменты > расширения и обновления**.
    2. В левой области выберите в **сети** и выполните поиск по запросу "WinRT" с помощью поля поиска справа.
    3. Выберите  **C++/WinRT**, нажмите кнопку **скачать**и закройте Visual Studio.
    4. Следуйте инструкциям по установке, а затем снова откройте Visual Studio.
* [Репозиторий GitHub для машинного обучения Windows](https://github.com/Microsoft/Windows-Machine-Learning) (вы можете скачать его как ZIP-файл или клонировать на свой компьютер).

## <a name="create-the-project"></a>Создание проекта

Сначала мы создадим проект в Visual Studio:

1. Выберите **файл > создать > проект** , чтобы открыть окно **Новый проект** .
2. В левой области выберите **установлено > Visual C++ > Рабочий стол Windows**, а в среднем выберите **консольное приложение Windows (C++/WinRT)** .
3. Присвойте проекту **имя** и **Расположение**, а затем нажмите кнопку **ОК**.
4. В окне **новый универсальная платформа Windows проект** задайте для параметра **Целевая** и **Минимальная версии** значение сборка 17763 или более поздняя и нажмите кнопку **ОК**.
5. Убедитесь, что в раскрывающихся меню на верхней панели инструментов задано значение **Отладка** и либо **x64** , либо **x86** , в зависимости от архитектуры компьютера.
6. Нажмите клавиши **CTRL + F5** , чтобы запустить программу без отладки. Должен открыться терминал с текстом "Hello World". Нажмите любую клавишу, чтобы закрыть его.

## <a name="load-the-model"></a>Загрузка модели

Далее мы загрузим модель ONNX в нашу программу с помощью [леарнингмодел. лоадфромфилепас](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodel.loadfromfilepath):

1. В файле **PCH. h** (в папке « **файлы** заголовков») `include` добавьте следующие инструкции (они предоставляют нам доступ ко всем API, которые нам понадобятся):
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

2. В файле **Main. cpp** (в папке **исходных файлов** ) добавьте следующие `using` инструкции:
    ```cpp
    using namespace Windows::AI::MachineLearning;
    using namespace Windows::Foundation::Collections;
    using namespace Windows::Graphics::Imaging;
    using namespace Windows::Media;
    using namespace Windows::Storage;

    using namespace std;
    ```

3. Добавьте следующие объявления переменных после `using` операторов:
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

4. После глобальных переменных добавьте следующие прямые объявления:
    ```cpp
    // Forward declarations
    void LoadModel();
    VideoFrame LoadImageFile(hstring filePath);
    void BindModel();
    void EvaluateModel();
    void PrintResults(IVectorView<float> results);
    void LoadLabels();
    ```

5. В **Main. cpp**удалите код "Hello World" (все, что находится `main` в функции после `init_apartment`).
6. Найдите файл **скуизенет. onnx** в локальном клоне репозитория **Windows-Machine-Learning** . Он должен находиться в **\виндовс-Мачине-леарнинг\шаредконтент\моделс**.
7. Скопируйте путь к файлу и назначьте его `modelPath` переменной, где мы определили его в верхней части. Не забудьте добавить в строку символ `L` , чтобы сделать его строкой расширенных символов, чтобы она правильно `hstring`работала с, и для экранирования символов обратной косой черты (`\`) с дополнительной обратной косой чертой. Пример:
    ```cpp
    hstring modelPath = L"C:\\Repos\\Windows-Machine-Learning\\SharedContent\\models\\SqueezeNet.onnx";
    ```

8. Во первых, мы реализуем `LoadModel` метод. Добавьте следующий метод после `main` метода. Этот метод загружает модель и выводит, как долго она заняла:
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

9. Наконец, вызовите этот метод из `main` метода:
    ```cpp
    LoadModel();
    ```

10. Запустите программу без отладки. Вы должны убедиться, что модель успешно загружена.

## <a name="load-the-image"></a>Загрузить изображение

Далее мы загрузим файл изображения в нашу программу:

1. Добавьте следующий метод. Этот метод загрузит изображение из заданного пути и создаст из него [видеофраме](https://docs.microsoft.com/uwp/api/windows.media.videoframe) :
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

3. Найдите папку **Media** в локальном клоне репозитория **Windows-Machine-Learning** . Он должен находиться по адресу **\виндовс-Мачине-леарнинг\шаредконтент\медиа**.
4. Выберите одно из изображений в этой папке и назначьте путь `imagePath` к файлу переменной, в которой она была определена в верхней части. Не забудьте добавить `L` в него символ, чтобы сделать его строкой расширенных символов, и отмечать символы обратной косой черты другой обратной косой чертой. Пример:
    ```cpp
    hstring imagePath = L"C:\\Repos\\Windows-Machine-Learning\\SharedContent\\media\\kitten_224.png";
    ```

5. Запустите программу без отладки. Вы должны увидеть, что образ успешно загружен.

## <a name="bind-the-input-and-output"></a>Привязка входных и выходных данных

Далее предстоит создать сеанс на основе модели и привязать входные и выходные данные из сеанса с помощью [леарнингмоделбиндинг. Bind](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodelbinding.bind). Дополнительные сведения о привязке см. в разделе [Привязка модели](bind-a-model.md).

1. Реализуйте `BindModel` метод. При этом создается сеанс на основе модели и устройства, а также привязка, основанная на этом сеансе. Затем мы привязывать входные и выходные данные к переменным, созданным с помощью их имен. Мы хотим заранее выяснить, что входные функции имеют имя «data_0», а функция Output имеет имя «softmaxout_1». Эти свойства можно просмотреть для любой модели, открыв их в [нетрон](https://lutzroeder.github.io/Netron/)— средстве визуализации модели в сети.
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

2. Добавьте вызов `BindModel` `main` из метода:
    ```cpp
    BindModel();
    ```

3. Запустите программу без отладки. Входные и выходные данные модели должны быть привязаны успешно. Почти готово!

## <a name="evaluate-the-model"></a>Оценка модели

Теперь на последнем шаге на схеме в начале этого руководства вы **оцените**. Мы будем оценивать модель с помощью [леарнингмоделсессион. Оцените](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodelsession.evaluate):

1. Реализуйте `EvaluateModel` метод. Этот метод принимает наш сеанс и вычисляет его, используя нашу привязку и идентификатор корреляции. Идентификатор корреляции можно использовать позже для сопоставления определенного вызова оценки с результатами вывода. Опять же, мы заранее понимаем, что имя выхода — «softmaxout_1».
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

2. Теперь выполним реализацию `PrintResults`. Этот метод получает три верхние вероятности для того, какой объект может быть в изображении, и выводит их на печать:
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

3. Также необходимо реализовать `LoadLabels`. Этот метод открывает файл меток, содержащий все различные объекты, которые модель может распознать, и анализирует ее:
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

4. Нахождение файла **labels. txt** в локальном клоне репозитория **Windows-Machine-Learning** . Он должен быть в **\виндовс-Мачине-леарнинг\самплес\скуизенетобжектдетектион\десктоп\кпп**.
5. Назначьте этот путь к файлу переменной `labelsFilePath` , в которой он был определен сверху. Не забудьте экранировать символы обратной косой черты с другой обратной косой чертой. Пример:
    ```cpp
    string labelsFilePath = "C:\\Repos\\Windows-Machine-Learning\\Samples\\SqueezeNetObjectDetection\\Desktop\\cpp\\Labels.txt";
    ```

6. Добавьте вызов `EvaluateModel` `main` в метод:
    ```cpp
    EvaluateModel();
    ```

7. Запустите программу без отладки. Теперь он должен правильно распознать, что есть в изображении. Ниже приведен пример того, что может выводиться:
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

Радостных, что функция обнаружения объектов работает в C++ классическом приложении! Затем можно попробовать использовать аргументы командной строки для ввода файлов модели и изображения, а не прописано их, как и для примера на GitHub. Вы также можете попробовать выполнить оценку на другом устройстве, например GPU, чтобы увидеть, как отличается производительность.

Поиграйте с другими примерами на GitHub и расширьте их, но вам нравится!

## <a name="see-also"></a>См. также

* [Примеры машинного обучения Windows (GitHub)](https://github.com/Microsoft/Windows-Machine-Learning/tree/master)
* [Пространство имен Windows. AI. MachineLearning](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning)
* [Windows ML](index.md)

[!INCLUDE [help](../includes/get-help.md)]
