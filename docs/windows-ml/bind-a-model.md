---
title: Привязка модели
description: Узнайте, как привязать входные и выходные данные модели для передачи информации в модель и из нее.
ms.date: 5/29/2019
ms.topic: article
keywords: windows 10, windows ai, windows ml, winml, windows machine learning
ms.localizationpriority: medium
ms.openlocfilehash: a2f83c0b3eedc64019e6c60fbc3d14cdb573a524
ms.sourcegitcommit: 81bd558d96d56735d49d522883957ce4b09f00cc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/19/2019
ms.locfileid: "75216967"
---
# <a name="bind-a-model"></a>Привязка модели

Модель машинного обучения имеет функции ввода и вывода, которые передают информацию в модель и из нее.

После загрузки модели в качестве [леарнингмодел](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodel)можно использовать [леарнингмодел. инпутфеатурес](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodel.inputfeatures) и [леарнингмодел. аутпутфеатурес](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodel.outputfeatures) для получения объектов [илеарнингмоделфеатуредескриптор](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.ilearningmodelfeaturedescriptor) . В них перечислены ожидаемые типы входных и выходных данных модели.

Для привязки значений к компоненту используется [леарнингмоделбиндинг](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodelbinding) , ссылающийся на **илеарнингмоделфеатуредескриптор** по свойству [Name](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.ilearningmodelfeaturedescriptor.name) .

В следующем видео приводится краткий обзор функций привязки моделей машинного обучения.

<br/>

> [!VIDEO https://www.youtube.com/embed/WD5bNZwz2A8]

## <a name="types-of-features"></a>Типы функций

Windows ML поддерживает все типы компонентов ONNX, перечисленные в [леарнингмоделфеатурекинд](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodelfeaturekind). Они сопоставлены с различными классами дескрипторов компонентов:

* **Тензорные**: [тенсорфеатуредескриптор](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.tensorfeaturedescriptor)
* **Последовательность**: [секуенцефеатуредескриптор](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.sequencefeaturedescriptor)
* **Map**: [мапфеатуредескриптор](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.mapfeaturedescriptor)
* **Изображение**: [имажефеатуредескриптор](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.imagefeaturedescriptor)

### <a name="tensors"></a>Десятки

Десятки — многомерные массивы, а наиболее распространенный тензорные — тензорные с плавающей запятой 32-бит. Измерениями десятков являются главные строки, с тесно упакованными непрерывными данными, представляющими каждое измерение. Общий размер тензорные — это произведение размеров каждого измерения.

### <a name="sequences"></a>Пакет

Последовательности — это векторы значений. Типичное использование типов последовательности — это вектор вероятностей с плавающей запятой, которые некоторые модели классификации возвращают для указания оценки точности для каждого прогноза.

### <a name="maps"></a>Карты

Карты — это пары "ключ — значение" информации. Модели классификации часто возвращают строку или таблицу с плавающей запятой, которая описывает вероятность с плавающей запятой для каждого имени классификации с меткой. Например, выходные данные модели, которые пытаются предсказать породу собаки на рисунке, могут быть `["Boston terrier", 90.0], ["Golden retriever", 7.4], ["Poodle", 2.6]`.

#### <a name="scalars"></a>Скаляры

Большинство карт и последовательностей будут иметь скалярные значения. Они показывают, где **тенсорфеатуредескриптор. Shape. size** равен нулю (0). В этом случае схема или последовательность будет иметь скалярный тип. Наиболее распространенный — `float`. Например, строка для отображения с плавающей запятой будет выглядеть следующим образом:

```cs
MapFeatureDescriptor.KeyKind == TensorKind.String
MapFeatureDescriptor.ValueDescriptor.Kind == LearningModelFeatureKind.Tensor
MapFeatureDescriptor.ValueDescriptor.as<TensorFeatureDescriptor>().Shape.Size == 0
```

Фактическое значение функции Map будет `IMap<string, float>`.

#### <a name="sequence-of-maps"></a>Последовательность карт

Последовательность сопоставлений — это просто вектор пар «ключ-значение». Например, последовательность сопоставлений строк с плавающей запятой будет иметь тип `IVector<IMap<string, float>>`. Приведенные выше выходные данные прогнозирования собаки `["Boston terrier", 90.0], ["Golden retriever", 7.4], ["Poodle", 2.6]` — пример последовательности карт.

### <a name="images"></a>образы,

При работе с образами необходимо иметь в виду форматы изображений и тенсоризатион.

#### <a name="image-formats"></a>Форматы изображений

Модели обрабатываются с помощью обучающих данных по изображениям, а весовые коэффициенты сохраняются и подстраиваются для этого обучающего набора. При передаче входных данных изображения в модель ее формат должен соответствовать формату обучающих изображений.

Во многих случаях модель описывает ожидаемый формат изображения. Модели ONNX могут использовать [метаданные](https://github.com/onnx/onnx/blob/master/docs/MetadataProps.md) для описания ожидаемых форматов изображений.  

В большинстве моделей используются следующие форматы, но они не являются универсальными для всех моделей:

* **Image. битмаппикселформат**: Bgr8
* **Image. колорспацегамма**: sRGB
* **Image. номиналпикселранже**: NominalRange_0_255

#### <a name="tensorization"></a>тенсоризатион

Образы представлены в формате тензорные в Windows ML. Тенсоризатион — это процесс преобразования изображения в тензорные и происходит во время привязки.

Windows ML преобразует изображения в 4-мерных десятки 32-битных элементов с плавающей запятой в формате НЧВ тензорные:

* **N**: размер пакета (или количество образов). В настоящее время Windows ML поддерживает размер пакета N из 1.
* **C**: число каналов (1 для Gray8, 3 для Bgr8).
* **H**: высота.
* **W**: ширина.

Каждый пиксель изображения — это 8-разрядное цветовое значение, хранящееся в диапазоне 0-255 и упакованное в 32-бит float.

#### <a name="how-to-pass-images-into-the-model"></a>Передача изображений в модель

В модели можно передавать изображения двумя способами:

* [ImageFeatureValue](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.imagefeaturevalue)

    Мы рекомендуем использовать **имажефеатуревалуе** для привязки изображений в качестве входных и выходных данных, так как он выполняет как преобразование, так и тенсоризатион, поэтому изображения соответствуют требуемому формату изображения модели. В настоящее время поддерживаются следующие типы форматов модели: **Gray8**, **Rgb8**и **Bgr8**, а в настоящее время поддерживаемый диапазон пикселей — 0-255.

    Вы можете создать **имажефеатуревалуе** с помощью статического метода [имажефеатуревалуе. креатефромвидеофраме](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.imagefeaturevalue.createfromvideoframe).

    Чтобы узнать, какой формат требуется для модели, WinML использует следующую логику и порядок очередности:

    1. [BIND (строка, объект, ипропертисет)](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodelbinding.bind#Windows_AI_MachineLearning_LearningModelBinding_Bind_System_String_System_Object_Windows_Foundation_Collections_IPropertySet_) переопределяет все параметры изображения.
    2. Метаданные модели будут проверяться и использоваться, если они доступны.
    3. Если метаданные модели не предоставлены и не предоставлены свойства вызывающей стороны, среда выполнения попытается выбрать лучшее соответствие. 
    * Если тензорные выглядит как НЧВ (4-мерный float32, N = = 1), среда выполнения предполагает либо **Gray8** (c = = 1), либо **Bgr8** (c = = 3) в зависимости от числа каналов.
    * Предполагается, NominalRange_0_255
    * Будет предполагаться использование SRGB

    Существует несколько необязательных свойств, которые можно передать в [BIND (строка, объект, ипропертисет)](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodelbinding.bind#Windows_AI_MachineLearning_LearningModelBinding_Bind_System_String_System_Object_Windows_Foundation_Collections_IPropertySet_):

    * [Битмапбаундс](https://docs.microsoft.com/uwp/api/windows.graphics.imaging.bitmapbounds): Если указано, это границы обрезки, которые необходимо применить перед отправкой изображения в модель.
    * [Битмаппикселформат](https://docs.microsoft.com/uwp/api/windows.graphics.imaging.bitmappixelformat): Если указано, это формат пикселей, который будет использоваться в качестве формата пикселей модели во время преобразования изображения.

    Для фигур изображений в модели можно указать определенную форму (например, Скуизенет принимает 224 224), или модель может задавать свободные измерения для любого изображения фигуры (многие модели Стилетрансфер-Type могут принимать изображения с переменным размером). Вызывающий объект может использовать **битмапбаундс** , чтобы выбрать раздел изображения, который они хотели бы использовать. Если значение не указано, среда выполнения масштабирует изображение до размера модели (в соответствии с пропорциями), а затем обрезать по центру.  

* [TensorFloat](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.tensorfloat)

    Если Windows ML не поддерживает цветовой формат модели или диапазон пикселей, можно реализовать преобразования и тенсоризатион. Вы создадите НЧВ трехмерный тензорные для 32-разрядного числа с плавающей запятой для входного значения. Пример того, как это сделать, см. в примере [Custom тенсоризатион](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/CustomTensorization) .

    При использовании этого метода все метаданные изображения в модели игнорируются.

## <a name="example"></a>Пример

В следующем примере показано, как выполнить привязку к входным данным модели. В этом случае мы создаем привязку из *сеанса*, создаем **имажефеатуревалуе** из *инпутфраме*и связываем изображение с входными данными модели *inputName*.

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

* Назад. [Создание сеанса](create-a-session.md)
* Далее: [Оценка входных данных модели](evaluate-model-inputs.md)

[!INCLUDE [help](../includes/get-help.md)]
