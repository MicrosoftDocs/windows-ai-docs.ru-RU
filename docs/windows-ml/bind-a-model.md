---
author: eliotcowley
title: Привязка модели
description: Узнайте, как привязать входные и выходные данные для передачи информации в действие и из модели элемента модели.
ms.author: elcowle
ms.date: 5/29/2019
ms.topic: article
keywords: windows 10, windows ai, windows ml, winml, windows machine learning
ms.localizationpriority: medium
ms.openlocfilehash: 32c99fa3cb46eaa3bb1f98ab128308eb37361651
ms.sourcegitcommit: 4ad0fea02000c8f6dbb9a919fb6ce1f435d0e8d6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/12/2019
ms.locfileid: "67027907"
---
# <a name="bind-a-model"></a>Привязка модели

Модель машинного обучения имеет входные и выходные данные функций, которые передачи информации в действие и из модели.

После загрузки моделей в виде [LearningModel](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodel), можно использовать [LearningModel.InputFeatures](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodel.inputfeatures) и [LearningModel.OutputFeatures](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodel.outputfeatures) для получения [ ILearningModelFeatureDescriptor](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.ilearningmodelfeaturedescriptor) объектов. Эти списка модели ожидаемое ввода и вывода типов компонентов.

Использовании [LearningModelBinding](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodelbinding) для привязки значений к функции, ссылающиеся на **ILearningModelFeatureDescriptor** по его [имя](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.ilearningmodelfeaturedescriptor.name) свойство.

Следующее видео дается краткий обзор привязки функций моделей машинного обучения.

<br/>

> [!VIDEO https://www.youtube.com/embed/WD5bNZwz2A8]

## <a name="types-of-features"></a>Типы компонентов

Машинное Обучение Windows поддерживает все типы ONNX компонентов, которые перечислены в [LearningModelFeatureKind](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodelfeaturekind). Это связано с класса различных функциональных дескрипторов:

* **Тензорные**: [TensorFeatureDescriptor](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.tensorfeaturedescriptor)
* **Последовательность**: [SequenceFeatureDescriptor](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.sequencefeaturedescriptor)
* **Карта**: [MapFeatureDescriptor](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.mapfeaturedescriptor)
* **Образ**. [ImageFeatureDescriptor](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.imagefeaturedescriptor)

### <a name="tensors"></a>Tensors

Tensors многомерных массивов, а наиболее распространенных тензорные тензорные из 32-разрядных значения с плавающей запятой. Измерения tensors — построчный, с помощью эффективно блоков данных, представляющий каждого измерения. Общий размер тензорные — это совокупность размеров каждого измерения.

### <a name="sequences"></a>Последовательности

Последовательности являются векторами значений. Обычно указанных типов последовательности используется вектор вероятностей число с плавающей запятой, которые возвращают некоторые модели классификации, указывающее оценку точности для каждого прогноза.

### <a name="maps"></a>Карты

Карты являются пар ключ/значение сведений. Модели классификации часто возвращают карту строка или число с плавающей запятой, которая описывает вероятность число с плавающей запятой для каждого имени с метками классификации. Например, может быть выходные данные модели, которая пытается прогнозировать в своем классе dog изображения `["Boston terrier", 90.0], ["Golden retriever", 7.4], ["Poodle", 2.6]`.

#### <a name="scalars"></a>Скаляры

Большинство карты и последовательности будут иметь значения, которые являются скалярные значения. Они отображаются where **TensorFeatureDescriptor.Shape.Size** равно нулю (0). В этом случае карты или последовательность будет иметь скалярный тип. Чаще всего это связано `float`. Например строка, число с плавающей запятой карты будет следующим:

```cs
MapFeatureDescriptor.KeyKind == TensorKind.String
MapFeatureDescriptor.ValueDescriptor.Kind == LearningModelFeatureKind.Tensor
MapFeatureDescriptor.ValueDescriptor.as<TensorFeatureDescriptor>().Shape.Size == 0
```

Значение функции фактическое карты будет `IMap<string, float>`.

#### <a name="sequence-of-maps"></a>Последовательность из maps

Последовательность из maps — просто вектор пар "ключ значение". Например, последовательность из maps строка float будут иметь тип `IVector<IMap<string, float>>`. Приведенные выше выходные данные прогнозов в своем классе dog `["Boston terrier", 90.0], ["Golden retriever", 7.4], ["Poodle", 2.6]` является примером последовательность из maps.

### <a name="images"></a>Изображений

При работе с образами, необходимо знать о форматов изображений и tensorization.

#### <a name="image-formats"></a>Форматы изображений

Модели обучаются с использованием образа обучающие данные и весовые коэффициенты сохраняются и специально созданные для этого обучающего набора. При передаче образа ввести в модель, его формат должен полностью соответствовать формату обучающие изображения.

Во многих случаях модель описывает формат ожидаемое изображение; Можно использовать моделями ONNX [метаданных](https://github.com/onnx/onnx/blob/master/docs/MetadataProps.md) для описания форматов ожидаемое изображение.  

Большинство моделей использовать следующие форматы, но это не универсальными для всех моделей:

* **Image.BitmapPixelFormat**: Bgr8
* **Image.ColorSpaceGamma**: SRGB
* **Image.NominalPixelRange**: NominalRange_0_255

#### <a name="tensorization"></a>Tensorization

Образы, представлены в машинном Обучении Windows в формате тензорные. Tensorization — это процесс преобразования изображения в тензорные и происходит во время привязки.

Машинное Обучение Windows преобразует изображения в 4-мерные tensors из 32-разрядных значений с плавающей запятой в «NCHW тензорные формат»:

* **N**: Размер пакета (или несколько образов). Windows машинного Обучения в настоящее время поддерживает размер пакета N 1.
* **C**: Число каналов (1 для Gray8, 3 для Bgr8).
* **H**: Высота.
* **W**: Ширина.

Каждого пикселя изображения — это число 8-разрядный цвет, который хранится в диапазоне от 0 до 255 и упакованные в 32-разрядное число с плавающей запятой.

#### <a name="how-to-pass-images-into-the-model"></a>Способ передачи изображений в модель

Существует два способа, можно передать изображения в модели:

* [ImageFeatureValue](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.imagefeaturevalue)

    Мы рекомендуем использовать **ImageFeatureValue** связывания изображения как входные и выходные данные, так как она отвечает за преобразование и tensorization, поэтому изображения соответствует формату требуемому модели. Типы формата, поддерживаемых в настоящее время модели, **Gray8**, **Rgb8**, и **Bgr8**, поддерживаемых в настоящее время пикселей диапазон — от 0 до 255.

    Можно создать **ImageFeatureValue** с помощью статического метода [ImageFeatureValue.CreateFromVideoFrame](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.imagefeaturevalue.createfromvideoframe).

    Чтобы узнать, какой формат модели, WinML использует следующий порядок логики и приоритет:

    1. [Привязка (String, Object, IPropertySet)](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodelbinding.bind#Windows_AI_MachineLearning_LearningModelBinding_Bind_System_String_System_Object_Windows_Foundation_Collections_IPropertySet_) Переопределите все параметры изображения.
    2. Метаданные модели будет установлен и используется, если он доступен.
    3. Если отсутствуют метаданные модели, и вызывающий объект предоставленные свойства, среда выполнения будет пытаться внести наилучшее соответствие. Если тензорные выглядит как NCHW (4-мерные float32, N == 1), среда выполнения считает, либо **Gray8** или **Bgr8** в зависимости от числа каналов.

    Существует несколько необязательные свойства, которые можно передать в [привязки (String, Object, IPropertySet)](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodelbinding.bind#Windows_AI_MachineLearning_LearningModelBinding_Bind_System_String_System_Object_Windows_Foundation_Collections_IPropertySet_):

    * [BitmapBounds](https://docs.microsoft.com/uwp/api/windows.graphics.imaging.bitmapbounds): Если указано, это границы обрезки для применения перед отправкой образа в модель.
    * [BitmapPixelFormat](https://docs.microsoft.com/uwp/api/windows.graphics.imaging.bitmappixelformat): Если указано, это формат пикселей, который будет использоваться в качестве формата пикселей модели во время преобразования изображения.

    Для фигур изображений модели можно указать определенные фигуры, что он принимает (например, принимает SqueezeNet 224,224) или модели можно указать бесплатный измерения все фигуры изображения (многие StyleTransfer типа модели может занять переменной размера изображения). Вызывающий объект может использовать **BitmapBounds** выбрать, какие части изображения они бы хотели использовать. Если не указано, среда выполнения будет масштабирования изображения до размера модели (соблюдение пропорции) и затем центра обрезки.  

* [TensorFloat](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.tensorfloat)

    Если машинного Обучения Windows не поддерживает формат цвета своей модели или пикселей, затем можно реализовать преобразования и tensorization. Вы создадите четырехмерный тензорные NCHW для 32-разрядных значения с плавающей запятой для входного значения. См. в разделе [пример пользовательской Tensorization](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/CustomTensorization) пример того, как это сделать.

    Когда этот метод используется, все метаданные образа на модели учитывается.

## <a name="example"></a>Пример

Приведенный ниже показано, как выполнить привязку к модели входных данных. В этом случае мы создадим привязку от *сеанса*, создание **ImageFeatureValue** из *inputFrame*и привязка входных изображений к модели, *inputName* .

```cs
private void BindModel(
    LearningModelSession session,
    VideoFrame inputFrame,
    string inputName)
{
    // Create a binding object from the session
    LearningModelBinding binding = new LearningModelBinding(session);

    // Create an image tensor from a video frame
    ImageFeatureValue image =
        ImageFeatureValue.CreateFromVideoFrame(inputFrame);

    // Bind the image to the input
    binding.Bind(inputName, image);
}
```

## <a name="see-also"></a>См. также

* Предыдущих: [Создание сеанса](create-a-session.md)
* Далее: [Оценка входных данных модели](evaluate-model-inputs.md)

[!INCLUDE [help](../includes/get-help.md)]
