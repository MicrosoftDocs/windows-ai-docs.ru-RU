---
author: rosanevallim
title: Выполнение нескольких моделей машинного Обучения в цепочке
description: Этом руководстве показано, как для последовательного выполнения нескольких моделей машинного обучения с максимальной производительности GPU
ms.author: rovalli
ms.date: 4/18/2019
ms.topic: article
keywords: windows 10, windows ai, windows ml, winml, windows machine learning
ms.localizationpriority: medium
ms.openlocfilehash: 4fd0c47a04b96922bf9ea6f498d54d827c5f257d
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66180836"
---
# <a name="executing-multiple-ml-models-in-a-chain"></a>Выполнение нескольких моделей машинного Обучения в цепочке

Машинное Обучение Windows поддерживает высокой производительности нагрузочных тестов и выполнения цепочек модели, тщательно, оптимизировав его пути GPU. Цепочки модели определяются двумя или более моделями, которые выполняются последовательно, где выходные данные одной модели становятся входные данные для модели далее вниз цепочке. 

Чтобы объяснить, эффективно сцепление моделей с машинным Обучением Windows, воспользуемся модели ONNX передачи FNS сладости стиль в качестве примера toy. Модели такого типа можно найти в папке примера FNS сладости стиля передачи в наших [GitHub](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/FNSCandyStyleTransfer).

Предположим, мы хотим выполнить цепь, состоит из двух экземпляров той же модели FNS сладости, здесь называется **mosaic.onnx**. Код приложения следует передать изображение первой модели в цепочке, перейдите к нему вычисления выходные данные, а затем передайте этот преобразованный образ с другим экземпляром FNS сладости, создания окончательного образа.  

Ниже описано, как это сделать с помощью машинного Обучения Windows.

>[!Note]
>В сценарии реальных word вы скорее всего, будет использовать две различные модели, но это должен быть достаточно, чтобы продемонстрировать основные понятия.

1. Во-первых загрузим **mosaic.onnx** модели таким образом, можно использовать их.
  ```cpp
  std::wstring filePath = L"path\\to\\mosaic.onnx"; 
  LearningModel model = LearningModel::LoadFromFilePath(filePath);
  ```

  ```cs
  string filePath = "path\\to\\mosaic.onnx";
  LearningModel model = LearningModel.LoadFromFilePath(filePath);
  ```

2. Затем создадим два идентичных сеанса включено по умолчанию устройства GPU, с помощью той же модели в качестве входного параметра. 
  ```cpp
  LearningModelSession session1(model, LearningModelDevice(LearningModelDeviceKind::DirectX));
  LearningModelSession session2(model, LearningModelDevice(LearningModelDeviceKind::DirectX));
  ```

  ```cs
  LearningModelSession session1 = 
    new LearningModelSession(model, new LearningModelDevice(LearningModelDeviceKind.DirectX));
  LearningModelSession session2 = 
    new LearningModelSession(model, new LearningModelDevice(LearningModelDeviceKind.DirectX));
  ```

> [!NOTE]
>Чтобы воспользоваться всеми преимуществами производительности цепочек, необходимо создавать идентичные сеансы GPU для всех моделей. Это не приведет дополнительное перемещение данных из графического Процессора и поместить в использование ЦП, которое может снизить производительность.

3. Приведенный ниже код создаст привязок для каждого сеанса:
  ```cpp
  LearningModelBinding binding1(session1);
  LearningModelBinding binding2(session2);
  ```

  ```cs
  LearningModelBinding binding1 = new LearningModelBinding(session1);
  LearningModelBinding binding2 = new LearningModelBinding(session2);
  ```

4. После этого выполняется привязка входных данных для нашей первой модели. Мы передаст в образ, который находится в том же расположении, что нашей модели. В этом примере изображение называется «fish_720.png».
  ```cpp
  //get the input descriptor
  ILearningModelFeatureDescriptor input = model.InputFeatures().GetAt(0);
  //load a SoftwareBitmap
  hstring imagePath = L"path\\to\\fish_720.png";

  // Get the image and bind it to the model's input
  try
  {
    StorageFile file = StorageFile::GetFileFromPathAsync(imagePath).get();
    IRandomAccessStream stream = file.OpenAsync(FileAccessMode::Read).get();
    BitmapDecoder decoder = BitmapDecoder::CreateAsync(stream).get();
    SoftwareBitmap softwareBitmap = decoder.GetSoftwareBitmapAsync().get();
    VideoFrame videoFrame = VideoFrame::CreateWithSoftwareBitmap(softwareBitmap);
    ImageFeatureValue image = ImageFeatureValue::CreateFromVideoFrame(videoFrame);
    binding1.Bind(input.Name(), image);
  }
  catch (...)
  {
    printf("Failed to load/bind image\n");
  }
  ```

  ```cs
  //get the input descriptor
  ILearningModelFeatureDescriptor input = model.InputFeatures[0];
  //load a SoftwareBitmap
  string imagePath = "path\\to\\fish_720.png";

  // Get the image and bind it to the model's input
  try
  {
      StorageFile file = await StorageFile.GetFileFromPathAsync(imagePath);
      IRandomAccessStream stream = await file.OpenAsync(FileAccessMode.Read);
      BitmapDecoder decoder = await BitmapDecoder.CreateAsync(stream);
      SoftwareBitmap softwareBitmap = await decoder.GetSoftwareBitmapAsync();
      VideoFrame videoFrame = VideoFrame.CreateWithSoftwareBitmap(softwareBitmap);
      ImageFeatureValue image = ImageFeatureValue.CreateFromVideoFrame(videoFrame);
      binding1.Bind(input.Name, image);
  }
  catch
  {
      Console.WriteLine("Failed to load/bind image");
  }
  ```

5. Далее модели в цепочке могла использовать выходные данные оценки первая модель необходимо создать пустые выходные тензорные и привязки выходных данных, у нас есть маркер в цепочку с:
  ```cpp
  //get the output descriptor
  ILearningModelFeatureDescriptor output = model.OutputFeatures().GetAt(0);
  //create an empty output tensor 
  std::vector<int64_t> shape = {1, 3, 720, 720};
  TensorFloat outputValue = TensorFloat::Create(shape); 
  //bind the (empty) output
  binding1.Bind(output.Name(), outputValue);
  ```

  ```cs
  //get the output descriptor
  ILearningModelFeatureDescriptor output = model.OutputFeatures[0];
  //create an empty output tensor 
  List<long> shape = new List<long> { 1, 3, 720, 720 };
  TensorFloat outputValue = TensorFloat.Create(shape);
  //bind the (empty) output
  binding1.Bind(output.Name, outputValue);
  ```

> [!NOTE]
>Необходимо использовать **TensorFloat** типа данных при привязке выходные данные. Это не позволит отменить tensorization шли после завершения оценки в первой модели, таким образом также избежать дополнительных GPU постановка в очередь для загрузки и привязать операций второй модели.

6. Теперь мы запустить вычисление первая модель и привязать его выходных данных для ввода Далее модели:
  ```cpp
  //run session1 evaluation
  session1.EvaluateAsync(binding1, L"");
  //bind the output to the next model input
  binding2.Bind(input.Name(), outputValue);
  //run session2 evaluation
  auto session2AsyncOp = session2.EvaluateAsync(binding2, L"");
  ```

  ```cs
  //run session1 evaluation
  await session1.EvaluateAsync(binding1, "");
  //bind the output to the next model input
  binding2.Bind(input.Name, outputValue);
  //run session2 evaluation
  LearningModelEvaluationResult results = await session2.EvaluateAsync(binding2, "");
  ```

7. Наконец давайте извлечем окончательные выходные данные после выполнения команды обе модели, используя следующую строку кода.
  ```cpp
  auto finalOutput = session2AsyncOp.get().Outputs().First().Current().Value();
  ```

  ```cs
  var finalOutput = results.Outputs.First().Value;
  ```

Вот и все! Обе модели теперь можно выполнить последовательно, эффективно доступные ресурсы графического Процессора. 

[!INCLUDE [help](../includes/get-help.md)]
