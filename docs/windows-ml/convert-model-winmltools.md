---
author: wschin
title: Преобразование ONNX с WinMLTools моделей машинного Обучения
description: Сведения об использовании WinMLTools для преобразования в формат ONNX моделей машинного Обучения.
ms.author: wechi
ms.date: 4/18/2019
ms.topic: article
keywords: Windows 10, windows машинное обучение, WinML, WinMLTools, ONNX, ONNXMLTools, scikit-изучить, Core машинное Обучение, Keras
ms.localizationpriority: medium
ms.openlocfilehash: 76d3436cf52a8e658881e7b8cbdd437a53a00bb1
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66180866"
---
# <a name="convert-ml-models-to-onnx-with-winmltools"></a>Преобразование ONNX с WinMLTools моделей машинного Обучения

[WinMLTools](https://pypi.org/project/winmltools/) позволяет преобразовать моделей машинного обучения, созданных с помощью платформ разными обучающими в ONNX. Он является расширением [ONNXMLTools](https://github.com/onnx/onnxmltools) и [TF2ONNX](https://github.com/onnx/tensorflow-onnx) преобразуемый моделями ONNX для использования с Windows машинного Обучения.

WinMLTools в настоящее время поддерживает преобразование из следующих платформ:

- Apple Core ML
- Keras
- scikit-сведения
- lightgbm
- xgboost
- этой библиотеки
- TensorFlow (экспериментальная функция)

Чтобы узнать, как экспортировать из других платформ машинного Обучения, взгляните на [ONNX учебники](https://github.com/onnx/tutorials) на сайте GitHub.

В этой статье мы покажем, как использовать WinMLTools для:

- Преобразовать в ONNX моделей машинного Обучения Core
- Преобразовать scikit-Узнайте моделей в ONNX
- Преобразование модели TensorFlow в ONNX
- Применить после обучения вес квантования с моделями ONNX
- Преобразование числа с плавающей запятой моделей для 16-разрядное число с плавающей точки точности модели
- Создайте пользовательские операторы ONNX

>[!NOTE]
>[Последнюю версию WinMLTools](https://pypi.org/project/winmltools/1.3.0/) поддерживает преобразование ONNX версии 1.2.2 и предыдущие версии 1.3, согласно соответственно opsets ONNX 7 и 8. Предыдущие версии средства не поддерживается для ONNX 1.3.

## <a name="install-winmltools"></a>Установка WinMLTools

WinMLTools — это пакет Python (**winmltools**), поддерживающий Python версий 2.7 и 3.6. При работе над проектом анализа данных рекомендуется установить научный дистрибутив Python, например Anaconda.

> [!NOTE]
> WinMLTools сейчас не поддерживает Python 3.7.

Следует за WinMLTools [процесс установки пакетов стандартный Python](https://packaging.python.org/installing/). В среде Python выполните следующую команду:

```console
pip install winmltools
```

WinMLTools имеет следующие зависимости:

- **numpy** v1.10.0 +
- **protobuf** v.3.6.0+
- **onnx** v1.3.0 +
- **onnxmltools** v1.3.0 +
- **tf2onnx** v0.3.2 +

Для обновления зависимых пакетов, запустите `pip` с `-U` аргумент.

```console
pip install -U winmltools
```

Для разных преобразователей необходимо установить разные пакеты.

Для **libsvm**, вы можете скачать **колесика этой библиотеки** из различных источников web. Одним из примеров можно найти в [Калифорнийского Университета в Ирвайне веб-сайт](https://www.lfd.uci.edu/~gohlke/pythonlibs/#libsvm).

Для **coremltools**, в настоящее время Apple не распространяет упаковки Core ML на Windows. Вы можете установить из источника:

```console
pip install git+https://github.com/apple/coremltools
```

Выполните [onnxmltools](https://github.com/onnx/onnxmltools) на GitHub для получения дополнительных сведений о **onnxmltools** зависимости.

Дополнительные сведения об использовании WinMLTools можно найти в документации по конкретных пакетов с `help` функции.

```console
help(winmltools)
```

## <a name="convert-core-ml-models"></a>Преобразование моделей Core ML

Здесь мы предполагаем, что путь к файлу примера модели Core ML такой: *example.mlmodel*.

~~~python
from coremltools.models.utils import load_spec
# Load model file
model_coreml = load_spec('example.mlmodel')
from winmltools import convert_coreml
# Convert it!
# The automatic code generator (mlgen) uses the name parameter to generate class names.
model_onnx = convert_coreml(model_coreml, 7, name='ExampleModel')
~~~

> [!NOTE]
> Второй параметр в вызове convert_coreml() — target_opset, и он ссылается на номер версии операторов в пространство имен по умолчанию `ai.onnx`. Дополнительные сведения см. в разделе об этих операторах [здесь](https://github.com/onnx/onnx/blob/master/docs/Operators.md). Этот параметр доступен только на последнюю версию WinMLTools, позволяя разработчикам предназначены для различных версий ONNX (в настоящее время поддерживаются версии 1.2.2 и 1.3). Для преобразования моделей для работы с Windows 10 октября 2018 обновление, используйте `target_opset` 7 (ONNX v1.2.2). Для Windows 10 сборок больше, чем 17763, WinML принимает моделей с `target_opset` 7 и 8 (ONNX v.1.3). [Заметки о выпуске](release-notes.md) раздел также содержит значения min и max ONNX версии поддерживаемых WinML в разных сборках.

`model_onnx` является ONNX [ModelProto](https://github.com/onnx/onnxmltools/blob/0f453c3f375c1ae928b83a4c7909c82c013a5bff/onnxmltools/proto/onnx-ml.proto#L176) объекта. Его можно сохранить в двух разных форматах.

~~~python
from winmltools.utils import save_model
# Save the produced ONNX model in binary format
save_model(model_onnx, 'example.onnx')
# Save the produced ONNX model in text format
from winmltools.utils import save_text
save_text(model_onnx, 'example.txt')
~~~

> [!NOTE]
>Core MLTools — это пакет Python, предоставляемых компанией Apple, но не доступна в Windows. Если необходимо установить этот пакет в Windows, установите пакет непосредственно из репозитория:

```console
pip install git+https://github.com/apple/coremltools
```

## <a name="convert-core-ml-models-with-image-inputs-or-outputs"></a>Преобразование моделей машинного Обучения ядра с образа входных и выходных данных

Из-за недостаточной типы изображений в ONNX для преобразования моделей Core ML изображений (то есть к моделям использование изображений в качестве входных и выходных данных) необходимо некоторые шаги предварительной обработки и постобработки.

Целью предварительной обработки является обеспечение того, чтобы входное изображение было правильно отформатировано в виде тензора ONNX. Предположим, *X* — это входное изображение с формой [C, H, W] в Core ML. В ONNX переменная *X* будет тензором с плавающей запятой с той же формой, а *X*[0, :, :]/*X*[1, :, :]/*X*[2, :, :] сохраняет красный, зеленый и синий каналы изображения. Для образов в машинном Обучении Core оттенки серого их формат-[1, H, W]-tensors в ONNX так, как только у нас есть один канал.

Если первоначальная модель Core ML выводит изображение, вручную преобразуйте выходные тензоры с плавающей запятой ONNX обратно в изображения. Предусмотрены два простых этапа. Первым шагом является усечение значений больше 255 до 255 и замена всех отрицательных значений на 0. Второй шаг — округлить все значения пикселей до целых чисел (путем добавления 0,5 и усечения дробной части). В модели машинного Обучения Core указывается порядок выходных каналов (например, RGB или BGR). Для создания верного выходного изображения нам может потребоваться выполнить транспозицию или отображение в случайном порядке для восстановления требуемого формата.

Здесь мы рассмотрим модель Core ML, FNS-Candy, скачанную с [GitHub](https://github.com/likedan/Awesome-CoreML-Models), в качестве конкретного примера преобразования для демонстрации разницы между форматами ONNX и Core ML. Обратите внимание на то, что все последующие команды выполняются в среде Python.

Во-первых, мы загружаем модель Core ML и проверяем ее входной и выходной форматы.

~~~python
from coremltools.models.utils import load_spec
model_coreml = load_spec('FNS-Candy.mlmodel')
model_coreml.description # Print the content of Core ML model description
~~~

Вывод на экран:

~~~console
...
input {
    ...
      imageType {
      width: 720
      height: 720
      colorSpace: BGR
    ...
}
...
output {
    ...
      imageType {
      width: 720
      height: 720
      colorSpace: BGR
    ...
}
...
~~~

В этом случае входные и выходные данные — это вариант BGR 720 x 720-образы. Следующий шаг — преобразование модели Core ML с помощью WinMLTools.

~~~python
# The automatic code generator (mlgen) uses the name parameter to generate class names.
from winmltools import convert_coreml
model_onnx = convert_coreml(model_coreml, 7, name='FNSCandy')
~~~

Альтернативный метод для просмотра модели входных данных и форматы в ONNX выходных данных является использование следующую команду:

~~~python
model_onnx.graph.input # Print out the ONNX input tensor's information
~~~

Вывод на экран:

~~~console
...
  tensor_type {
    elem_type: FLOAT
    shape {
      dim {
        dim_param: "None"
      }
      dim {
        dim_value: 3
      }
      dim {
        dim_value: 720
      }
      dim {
        dim_value: 720
      }
    }
  }
...
~~~

Полученные входные данные (обозначенные *X*) в ONNX представляют собой четырехмерный тензор. Последними тремя осями являются: C, H и W, соответственно. Первое измерение — «None», и это означает, что эта модель ONNX может применяться к любому количеству изображений. Для применения этой модели в целях обработки пакета из 2 изображений первое изображение соответствует *X*[0, :, :, :], тогда как *X*[1, :, :, :] соответствует второму изображению. Синий, зеленый и красный каналы первого изображения — *X*[0, 0, :, :]/*X*[0, 1, :, :]/*X*[0, 2, :, :]; аналогично для второго изображения.

~~~python
model_onnx.graph.output # Print out the ONNX output tensor's information
~~~

Вывод на экран:

~~~console
...
  tensor_type {
    elem_type: FLOAT
    shape {
      dim {
        dim_param: "None"
      }
      dim {
        dim_value: 3
      }
      dim {
        dim_value: 720
      }
      dim {
        dim_value: 720
      }
    }
  }
...
~~~

Как можно увидеть, создаваемый формат идентичен формату входных данных исходной модели. Тем не менее, в этом случае это не изображение, поскольку значения пикселей представлены целыми числами, а не числами с плавающей запятой. Чтобы преобразовать обратно в изображение, усеките числа больше 255 до 255, измените отрицательные значения на 0 и округлите все десятичные до целых чисел.

## <a name="convert-scikit-learn-models"></a>Преобразовать scikit-Узнайте моделей

В следующем фрагменте кода метод опорных векторов обучается в scikit-learn, и модель преобразуется в ONNX.

~~~python
# First, we create a toy data set.
# The training matrix X contains three examples, with two features each.
# The label vector, y, stores the labels of all examples.
X = [[0.5, 1.], [-1., -1.5], [0., -2.]]
y = [1, -1, -1]

# Then, we create a linear classifier and train it.
from sklearn.svm import LinearSVC
linear_svc = LinearSVC()
linear_svc.fit(X, y)

# To convert scikit-learn models, we need to specify the input feature's name and type for our converter.
# The following line means we have a 2-D float feature vector, and its name is "input" in ONNX.
# The automatic code generator (mlgen) uses the name parameter to generate class names.
from winmltools import convert_sklearn
from winmltools.convert.common.data_types import FloatTensorType
linear_svc_onnx = convert_sklearn(linear_svc, 7, name='LinearSVC',
                                  initial_types=[('input', FloatTensorType([1, 2]))])

# Now, we save the ONNX model into binary format.
from winmltools.utils import save_model
save_model(linear_svc_onnx, 'linear_svc.onnx')

# If you'd like to load an ONNX binary file, our tool can also help.
from winmltools.utils import load_model
linear_svc_onnx = load_model('linear_svc.onnx')

# To see the produced ONNX model, we can print its contents or save it in text format.
print(linear_svc_onnx)
from winmltools.utils import save_text
save_text(linear_svc_onnx, 'linear_svc.txt')

# The conversion of linear regression is very similar. See the example below.
from sklearn.svm import LinearSVR
linear_svr = LinearSVR()
linear_svr.fit(X, y)
linear_svr_onnx = convert_sklearn(linear_svr, 7, name='LinearSVR',
                                  initial_types=[('input', FloatTensorType([1, 2]))])
~~~

Как и раньше `convert_sklearn` принимает scikit-Дополнительные сведения о модели в качестве первого аргумента и `target_opset` второго аргумента. Пользователи могут заменить `LinearSVC` другими моделями scikit-learn, такими как `RandomForestClassifier`. Следует учитывать, что [mlgen](mlgen.md) использует `name` сформировать имена классов и переменных. Если `name` не предоставляется, создается идентификатор GUID, который не будет соответствовать соглашениям об именовании для таких языков, как C++/C#.

## <a name="convert-scikit-learn-pipelines"></a>Преобразовать scikit-дополнительные конвейеры

Далее рассмотрим, как конвейеры scikit-learn можно преобразовать в ONNX.

~~~python
# First, we create a toy data set.
# Notice that the first example's last feature value, 300, is large.
X = [[0.5, 1., 300.], [-1., -1.5, -4.], [0., -2., -1.]]
y = [1, -1, -1]

# Then, we declare a linear classifier.
from sklearn.svm import LinearSVC
linear_svc = LinearSVC()

# One common trick to improve a linear model's performance is to normalize the input data.
from sklearn.preprocessing import Normalizer
normalizer = Normalizer()

# Here, we compose our scikit-learn pipeline.
# First, we apply our normalization.
# Then we feed the normalized data into the linear model.
from sklearn.pipeline import make_pipeline
pipeline = make_pipeline(normalizer, linear_svc)
pipeline.fit(X, y)

# Now, we convert the scikit-learn pipeline into ONNX format.
# Compared to the previous example, notice that the specified feature dimension becomes 3.
# The automatic code generator (mlgen) uses the name parameter to generate class names.
from winmltools import convert_sklearn
from winmltools.convert.common.data_types import FloatTensorType, Int64TensorType
pipeline_onnx = convert_sklearn(linear_svc, name='NormalizerLinearSVC',
                                input_features=[('input', FloatTensorType([1, 3]))])

# We can print the fresh ONNX model.
print(pipeline_onnx)

# We can also save the ONNX model into a binary file for later use.
from winmltools.utils import save_model
save_model(pipeline_onnx, 'pipeline.onnx')

# Our conversion framework provides limited support of heterogeneous feature values.
# We cannot have numerical types and string types in one feature vector.
# Let's assume that the first two features are floats and the last feature is integers (encoded a categorical attribute).
X_heter = [[0.5, 1., 300], [-1., -1.5, 400], [0., -2., 100]]

# One popular way to represent categorical is one-hot encoding.
from sklearn.preprocessing import OneHotEncoder
one_hot_encoder = OneHotEncoder(categorical_features=[2])

# Let's initialize a classifier.
# It will be right after the one-hot encoder in our pipeline.
linear_svc = LinearSVC()

# Then, we form a two-stage pipeline.
another_pipeline = make_pipeline(one_hot_encoder, linear_svc)
another_pipeline.fit(X_heter, y)

# Now, we convert, save, and load the converted model.
# For heterogeneous feature vectors, we need to separately specify their types for
# all homogeneous segments.
# The automatic code generator (mlgen) uses the name parameter to generate class names.
another_pipeline_onnx = convert_sklearn(another_pipeline, name='OneHotLinearSVC',
                                        input_features=[('input', FloatTensorType([1, 2])),
                                        ('another_input', Int64TensorType([1, 1]))])
save_model(another_pipeline_onnx, 'another_pipeline.onnx')
from winmltools.utils import load_model
loaded_onnx_model = load_model('another_pipeline.onnx')

# Of course, we can print the ONNX model to see if anything went wrong.
print(another_pipeline_onnx)
~~~

## <a name="convert-tensorflow-models"></a>Преобразование модели TensorFlow

Ниже приведен пример того, как преобразовать модели из замороженной модели TensorFlow. Для получения возможные выходных имена модели TensorFlow, можно использовать [summarize_graph средство](https://github.com/tensorflow/tensorflow/tree/master/tensorflow/tools/graph_transforms).

~~~python
import winmltools
import tensorflow

filename = 'frozen-model.pb'
output_names = ['output:0']

graph_def = graph_pb2.GraphDef()
with open(filename, 'rb') as file:
  graph_def.ParseFromString(file.read())
g = tf.import_graph_def(graph_def, name='')

with tf.Session(graph=g) as sess:
  converted_model = winmltools.convert_tensorflow(sess.graph, 7, output_names=['output:0'])
  winmltools.save_model(converted_model)
~~~

Использует преобразователь WinMLTools `tf2onnx.tfonnx.process_tf_graph` в [TF2ONNX](https://github.com/onnx/tensorflow-onnx).

## <a name="convert-to-floating-point-16"></a>Преобразовать в число с плавающей запятой 16

WinMLTools поддерживает преобразование моделей, в число с плавающей запятой, 32, в число с плавающей точки 16 представление (IEEE 754 половина), что сжатие модели за счет уменьшения его размера, в два раза.

> [!NOTE]
> Преобразование числа с плавающей запятой 16 модели может привести к потере точности. Убедитесь, что перед развертыванием в приложение проверки точности модели.

Ниже приведен полный пример, если вы хотите преобразовать непосредственно из двоичного файла ONNX.

~~~python
from winmltools.utils import convert_float_to_float16
from winmltools.utils import load_model, save_model
onnx_model = load_model('model.onnx')
new_onnx_model = convert_float_to_float16(onnx_model)
save_model(new_onnx_model, 'model_fp16.onnx')
~~~

С помощью `help(winmltools.utils.convert_float_to_float16)`, можно найти дополнительные сведения об этом средстве. С плавающей запятой 16 в WinMLTools в настоящее время только соответствует [IEEE 754 с плавающей запятой стандарта точек (2008)](https://en.wikipedia.org/wiki/Half-precision_floating-point_format).

## <a name="post-training-weight-quantization"></a>После обучения вес квантования

WinMLTools также поддерживает сжатие моделей, в число с плавающей запятой 32 в представления 8-разрядное целое число. Это может вызвать снижение объема диска до 75% в зависимости от модели. Это сокращение выполняется через метод, который называется после обучения вес квантования, где анализируется модели и веса хранимых тензорные уменьшаются из 32-разрядных данных с плавающей запятой в 8-разрядные данные.

> [!NOTE]
> После обучения квантования вес может привести к потере точности в создаваемой модели. Убедитесь, что перед развертыванием в приложение проверки точности модели.

Ниже приведен полный пример, в котором показано, как преобразовать непосредственно из двоичного файла ONNX.

```python
import winmltools

model = winmltools.load_model('model.onnx')
packed_model = winmltools.quantize(model, per_channel=True, nbits=8, use_dequantize_linear=True)
winmltools.save_model(packed_model, 'quantized.onnx')
```

Вот некоторые сведения о входных параметров для `quantize`:

- `per_channel`. Если значение `True`, это будет линейно квантования каждый канал для каждого инициализированный тензорные в формате [n, c, h, w]. По умолчанию этот параметр имеет значение `True`.
- `nbits`. Количество битов для представления Сегментированные значения. В настоящее время поддерживается только 8 бит.
- `use_dequantize_linear`. Если значение `True`, это будет линейно dequantize каждого канала в инициализированный tensors для операторов Прео в формате [n, c, h, w]. По умолчанию, это имеет значение `True`.

## <a name="create-custom-onnx-operators"></a>Создайте пользовательские операторы ONNX

При преобразовании из Keras или Core ML модели, можно написать функцию пользовательского оператора для внедрения пользовательского [операторы](https://github.com/onnx/onnx/blob/master/docs/Operators.md) в граф ONNX. Во время преобразования преобразователь вызывает функцию для преобразования на уровне Keras или LayerParameter ML Core оператору ONNX, а затем он подключается узел оператора в весь граф.

1. Создайте пользовательскую функцию для создания подграф ONNX.
2. Вызовите `winmltools.convert_keras` или `winmltools.convert_coreml` с картой имени пользовательского уровня пользовательской функции.
3. Если это применимо, реализации пользовательского уровня для определения среды выполнения.  

Следующий пример показывает, как она работает в Keras.

~~~python
# Define the activation layer.
class ParametricSoftplus(keras.layers.Layer):
    def __init__(self, alpha, beta, **kwargs):
    ...
    ...
    ...

# Create the convert function.
def convert_userPSoftplusLayer(scope, operator, container):
      return container.add_node('ParametricSoftplus', operator.input_full_names, operator.output_full_names,
        op_version=1, alpha=operator.original_operator.alpha, beta=operator.original_operator.beta)

winmltools.convert_keras(keras_model, 7,
    custom_conversion_functions={ParametricSoftplus: convert_userPSoftplusLayer })
~~~

[!INCLUDE [help](../includes/get-help.md)]
