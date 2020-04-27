---
title: Привязка модели
description: Сведения о том, как создавать привязки к входам и выходам модели для передачи информации в модель и из нее.
ms.date: 5/29/2019
ms.topic: article
keywords: windows 10, windows ai, windows ml, winml, windows machine learning
ms.localizationpriority: medium
ms.openlocfilehash: a2f83c0b3eedc64019e6c60fbc3d14cdb573a524
ms.sourcegitcommit: 2139506ff12b7205283288c4bbac866ddfa812f3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/24/2020
ms.locfileid: "75216967"
---
# <a name="bind-a-model"></a>Привязка модели

Модель машинного обучения имеет выходные и выходные признаки для передачи информации в модель и из нее.

Выполнив загрузку модели в объект [LearningModel](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodel), вы можете применить [LearningModel.InputFeatures](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodel.inputfeatures) и [LearningModel.OutputFeatures](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodel.outputfeatures) для получения объектов [ILearningModelFeatureDescriptor](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.ilearningmodelfeaturedescriptor). Они позволяют получить списки ожидаемых типов входных и выходных признаков модели.

Используйте [LearningModelBinding](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodelbinding) для привязки значений к этим признакам, указав ссылку на **ILearningModelFeatureDescriptor** по значению свойства [Name](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.ilearningmodelfeaturedescriptor.name) (Имя).

В следующем видео представлен краткий обзор процесса привязки признаков для модели машинного обучения.

<br/>

> [!VIDEO https://www.youtube.com/embed/WD5bNZwz2A8]

## <a name="types-of-features"></a>Типы признаков

Windows ML поддерживает все типы признаков ONNX, которые перечислены в [LearningModelFeatureKind](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodelfeaturekind). Они сопоставляются с разными классами дескрипторов признаков.

* **Тензор**: [TensorFeatureDescriptor](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.tensorfeaturedescriptor)
* **Последовательность**: [SequenceFeatureDescriptor](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.sequencefeaturedescriptor)
* **Карта**: [MapFeatureDescriptor](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.mapfeaturedescriptor)
* **Образ**. [ImageFeatureDescriptor](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.imagefeaturedescriptor)

### <a name="tensors"></a>Тензоры

Тензорами называют многомерные массивы, из которых наиболее распространены тензоры с 32-разрядными значениями с плавающей запятой. Размерности тензоров развертываются по строкам, а каждая размерность представлена плотно упакованными смежными данными. Общий размер тензора вычисляется как произведение размеров каждого измерения.

### <a name="sequences"></a>Последовательности

Последовательности — это векторы значений. Типы последовательностей чаще всего применяются для хранения вектора вероятностей с плавающей запятой, которые некоторые модели классификации возвращают как оценку точности каждого прогноза.

### <a name="maps"></a>Карты

Карты содержат информацию в формате пар "ключ — значение". Модели классификации часто возвращают карту строковых значений и чисел с плавающей запятой, которые обозначают численную вероятность для каждой метки имен классификации. Например, выходные данные модели, прогнозирующей породу собаки на изображении, могут выглядеть так: `["Boston terrier", 90.0], ["Golden retriever", 7.4], ["Poodle", 2.6]`.

#### <a name="scalars"></a>Скаляры

Большинство карт и последовательностей содержат скалярные значения. Они используются, когда значение **TensorFeatureDescriptor.Shape.Size** равно нулю (0). В этом случае карта или последовательность будет иметь скалярный тип. Наиболее распространенным является `float`. Например, карта сопоставления строк с числами с плавающей запятой будет выглядеть следующим образом:

```cs
MapFeatureDescriptor.KeyKind == TensorKind.String
MapFeatureDescriptor.ValueDescriptor.Kind == LearningModelFeatureKind.Tensor
MapFeatureDescriptor.ValueDescriptor.as<TensorFeatureDescriptor>().Shape.Size == 0
```

Фактическое значение признака карты выражается как `IMap<string, float>`.

#### <a name="sequence-of-maps"></a>Последовательность карт

Последовательность карт является простым вектором пар "ключ — значение". Например, последовательность карт для сопоставления строк и чисел с плавающей запятой будет иметь тип `IVector<IMap<string, float>>`. Приведенные выше выходные данные прогнозирования породы собак `["Boston terrier", 90.0], ["Golden retriever", 7.4], ["Poodle", 2.6]`типичный пример последовательности карт.

### <a name="images"></a>образы,

При работе с изображениями важно понимать форматы изображений и процесс преобразования в тензор.

#### <a name="image-formats"></a>Форматы изображений

Модели обучаются по обучающему набору изображений, для которого подбираются и сохраняются весовые коэффициенты. Формат изображения, передаваемого в качестве входных данных в эту модель, должен соответствовать формату обучающих изображений.

Во многих случаях модель сама описывает ожидаемый формат изображений. Например, модели ONNX могут использовать [метаданные](https://github.com/onnx/onnx/blob/master/docs/MetadataProps.md) для описания ожидаемых форматов.  

В большинстве моделей, хотя и не во всех, используются следующие форматы.

* **Image.BitmapPixelFormat**: Bgr8
* **Image.ColorSpaceGamma**: SRGB
* **Image.NominalPixelRange**: NominalRange_0_255

#### <a name="tensorization"></a>Преобразование в тензор

В Windows ML изображения представлены в формате тензоров. Преобразование изображения в тензор выполняется во время привязки.

Windows ML позволяет преобразовать изображения в 4-мерные тензоры 32-разрядных чисел с плавающей запятой (формат NCHW).

* **N** — размер пакета (количество изображений). В настоящее время Windows ML поддерживает только размер пакета N=1.
* **C** — число каналов (1 для формата Gray8 или 3 для Bgr8).
* **H** — высота изображения.
* **W** — ширина изображения.

Каждый пиксель на изображении представлен 8-разрядным значением цвета в диапазоне от 0 до 255, которые упаковываются в 32-разрядные числа с плавающей запятой.

#### <a name="how-to-pass-images-into-the-model"></a>Передача изображений в модель

Существует два способа передать изображения в модель.

* [ImageFeatureValue](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.imagefeaturevalue)

    Мы рекомендуем использовать объект **ImageFeatureValue** для привязки изображений в качестве входных и выходных данных, так как он выполняет преобразование формата и преобразование в тензор в соответствии с требованиями модели к изображениям. В настоящее время для моделей поддерживаются следующие типы форматов: **Gray8**, **Rgb8** и **Bgr8** с диапазоном значений пикселей от 0 до 255.

    Вы можете создать **ImageFeatureValue** с помощью статического метода [ImageFeatureValue.CreateFromVideoFrame](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.imagefeaturevalue.createfromvideoframe).

    Чтобы узнать, какой формат нужен для модели, WinML использует следующую логику и порядок очередности.

    1. [Bind(String, Object, IPropertySet)](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodelbinding.bind#Windows_AI_MachineLearning_LearningModelBinding_Bind_System_String_System_Object_Windows_Foundation_Collections_IPropertySet_) переопределяет все параметры изображения.
    2. После этого проверяются и применяются метаданные модели, если они доступны.
    3. Если для модели не предоставлено ни метаданных, ни свойств от вызывающей стороны, среда выполнения пытается выбрать лучшее соответствие. 
    * Если тензор имеет формат, близкий к NCHW (4-мерный со значениями float32, где N==1), среда выполнения применит формат **Gray8** (C==1) или **Bgr8** (C==3) в зависимости от количества каналов.
    * Подразумевается NominalRange_0_255
    * Подразумевается SRGB

    В вызов [Bind(String, Object, IPropertySet)](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodelbinding.bind#Windows_AI_MachineLearning_LearningModelBinding_Bind_System_String_System_Object_Windows_Foundation_Collections_IPropertySet_) можно передать несколько необязательных свойств.

    * [BitmapBounds](https://docs.microsoft.com/uwp/api/windows.graphics.imaging.bitmapbounds). Это свойство используется для обозначения границ для обрезки перед отправкой изображения в модель.
    * [BitmapPixelFormat](https://docs.microsoft.com/uwp/api/windows.graphics.imaging.bitmappixelformat). Это свойство используется как формат пикселей для модели во время преобразования изображения.

    Для размера изображений в модели можно указать определенную форму (например, SqueezeNet принимает размер 224×224) или произвольные размеры для изображения любой формы (многие модели типа StyleTransfer могут принимать изображения с переменным размером). Вызывающая сторона может применить **BitmapBounds** для выбора используемого фрагмента изображения. Если это значение не указано, среда выполнения масштабирует изображение до размера модели с сохранением пропорций, а затем обрезает его по центру.  

* [TensorFloat](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.tensorfloat)

    Если Windows ML не поддерживает выбранный для модели цветовой формат или диапазон значений пикселей, вы можете реализовать собственную процедуру преобразования. Для входящего значения создайте четырехмерный тензор формата NCHW с 32-разрядными числами с плавающей запятой. Пример таких преобразований вы найдете [здесь](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/CustomTensorization).

    При использовании этого метода игнорируются все заданные в модели метаданные изображения.

## <a name="example"></a>Пример

В следующем примере показано, как выполнить привязку ко входу модели. В нашем примере мы создаем привязку из *сеанса*, затем создаем **ImageFeatureValue** из *inputName* и выполняем привязку изображения ко входу модели (*inputName*).

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

## <a name="see-also"></a>См. также статью

* Предыдущая статья: [Создание сеанса](create-a-session.md)
* Далее: [Оценка входных данных модели](evaluate-model-inputs.md)

[!INCLUDE [help](../includes/get-help.md)]
