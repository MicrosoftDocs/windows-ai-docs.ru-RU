---
author: rosanevallim
title: Выполнение нескольких моделей машинного обучения в цепочке
description: В этом руководстве показано, как последовательно выполнять несколько моделей машинного обучения, сохраняя максимальную производительность графического процессора.
ms.author: rovalli
ms.date: 4/18/2019
ms.topic: article
keywords: windows 10, windows ai, windows ml, winml, windows machine learning
ms.localizationpriority: medium
ms.openlocfilehash: 4fd0c47a04b96922bf9ea6f498d54d827c5f257d
ms.sourcegitcommit: 2139506ff12b7205283288c4bbac866ddfa812f3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/24/2020
ms.locfileid: "66180836"
---
# <a name="executing-multiple-ml-models-in-a-chain"></a>Выполнение нескольких моделей машинного обучения в цепочке

Windows ML поддерживает высокопроизводительные методы загрузки и выполнения цепочек моделей, тщательно оптимизируя применение графического процессора. Цепочки моделей состоят из двух и более моделей, которые выполняются последовательно с передачей выходных данных одной модели на вход следующей модели в цепочке. 

Мы опишем эффективное применение цепочек моделей в Windows ML на примере модели ONNX "FNS-Candy Style Transfer". Этот тип модели вы найдете в папке с примером "FNS-Candy Style Transfer" нашего репозитория на [GitHub](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/FNSCandyStyleTransfer).

Предположим, что мы хотим выполнить цепочку из двух экземпляров одной модели FNS-Candy с именем **mosaic.onnx**. Код приложения передает изображение в первую модель цепочки, дожидается ее выходных данных и передает преобразованное изображение другому экземпляру FNS-Candy, которая и создает окончательное изображение.  

В следующих шагах показано, как выполнить этот процесс в Windows ML.

>[!Note]
>В реальном сценарии вы, скорее всего, примените две разные модели, но наш пример позволяет в общих чертах понять концепции.

1. Для начала давайте загрузим модель **mosaic.onnx**, чтобы мы могли ее использовать.
  ```cpp
  std::wstring filePath = L"path\\to\\mosaic.onnx"; 
  LearningModel model = LearningModel::LoadFromFilePath(filePath);
  ```

  ```cs
  string filePath = "path\\to\\mosaic.onnx";
  LearningModel model = LearningModel.LoadFromFilePath(filePath);
  ```

2. Затем мы создадим два одинаковых сеанса на используемом по умолчанию графическом процессоре устройства, указав одну и ту же модель в качестве входного параметра. 
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
>Чтобы получить повышение производительности от использования цепочки, нам нужно создать идентичные сеансы графического процессора для всех моделей. Без этого данные будут дополнительно перемещаться из графического процессора в ЦП, что снизит производительность.

3. Следующие строки кода позволяют создать привязки для каждого сеанса:
  ```cpp
  LearningModelBinding binding1(session1);
  LearningModelBinding binding2(session2);
  ```

  ```cs
  LearningModelBinding binding1 = new LearningModelBinding(session1);
  LearningModelBinding binding2 = new LearningModelBinding(session2);
  ```

4. Теперь мы привяжем входные данные к первой модели. Здесь мы передаем изображение, размещенное в том же пути, что и сама модель. В нашем примере это изображение с именем fish_720.png.
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

5. Чтобы следующая модель в цепочке использовала выходные данные из первой модели, нам нужно создать пустой выходной тензор и привязать к нему выходные данные, чтобы получить маркер для связывания.
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
>При привязке выходных данных укажите тип данных **TensorFloat**. Это предотвратит дополнительное преобразование из формата тензора после оценки первой модели, то есть избавит от дополнительных очередей в графическом процессоре для операций загрузки и привязки второй модели.

6. Теперь выполните оценку первой модели и создайте привязку между ее выходными данными и входными данными следующей модели:
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

7. Наконец, давайте получим окончательный результат выполнения обеих моделей с помощью следующей строки кода.
  ```cpp
  auto finalOutput = session2AsyncOp.get().Outputs().First().Current().Value();
  ```

  ```cs
  var finalOutput = results.Outputs.First().Value;
  ```

Вот и все! Теперь обе модели могут выполняться последовательно, чтобы максимально эффективно использовать ресурсы графического процессора. 

[!INCLUDE [help](../includes/get-help.md)]
