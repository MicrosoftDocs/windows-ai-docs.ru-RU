---
author: wschin
title: Преобразование моделей машинного обучения в формат ONNX с помощью WinMLTools
description: Узнайте о том, как с помощью WinMLTools преобразовывать модели машинного обучения в формат ONNX.
ms.author: wechi
ms.date: 4/18/2019
ms.topic: article
keywords: windows 10, windows machine learning, WinML, WinMLTools, ONNX, ONNXMLTools, scikit-learn, Core ML, Keras
ms.localizationpriority: medium
ms.openlocfilehash: 76d3436cf52a8e658881e7b8cbdd437a53a00bb1
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66180866"
---
# <a name="convert-ml-models-to-onnx-with-winmltools"></a>Преобразование моделей машинного обучения в формат ONNX с помощью WinMLTools

[WinMLTools](https://pypi.org/project/winmltools/) позволяет преобразовывать модели машинного обучения, созданные с использованием разных платформ обучения, в формат ONNX. Это расширение [ONNXMLTools](https://github.com/onnx/onnxmltools) и [TF2ONNX](https://github.com/onnx/tensorflow-onnx), предназначенное для преобразования моделей в формат ONNX для использования с Windows ML.

Сейчас WinMLTools поддерживает преобразование из следующих платформ:

- Apple Core ML;
- Keras;
- scikit-learn;
- lightgbm;
- xgboost;
- libSVM;
- TensorFlow (в экспериментальном режиме).

См. сведения о том, как экспортировать модели из других платформ машинного обучения, в [руководствах по ONNX](https://github.com/onnx/tutorials) на GitHub.

В этой статье описано, как с помощью WinMLTools выполнять следующие действия:

- преобразование моделей Core ML в формат ONNX;
- преобразование моделей scikit-learn в формат ONNX;
- преобразование моделей TensorFlow в формат ONNX;
- применение дискретизации весовых коэффициентов к моделям ONNX после обучения;
- преобразование моделей с плавающей запятой в модели 16-разрядной точности с плавающей запятой;
- создание пользовательских операторов ONNX.

>[!NOTE]
>[Последняя версия WinMLTools](https://pypi.org/project/winmltools/1.3.0/) поддерживает преобразование в формат ONNX версий 1.2.2 и 1.3 (определяется наборами операций ONNX версий 7 и 8 соответственно). Предыдущие версии средства не поддерживают ONNX версии 1.3.

## <a name="install-winmltools"></a>Установка WinMLTools

WinMLTools предоставляется в виде пакета Python (**winmltools**), который поддерживает Python версий 2.7 и 3.6. При работе над проектом анализа данных лучше всего применять такой дистрибутив Python для научных вычислений, как Anaconda.

> [!NOTE]
> Сейчас WinMLTools не поддерживает Python версии 3.7.

WinMLTools поддерживает [стандартный процесс установки пакетов Python](https://packaging.python.org/installing/). В среде Python выполните следующую команду:

```console
pip install winmltools
```

WinMLTools имеет следующие зависимости:

- **numpy** версии 1.10.0 и выше;
- **protobuf** версии 3.6.0 или выше;
- **onnx** версии 1.3.0 и выше;
- **onnxmltools** версии 1.3.0 и выше;
- **tf2onnx** версии 0.3.2 и выше.

Чтобы обновить зависимые пакеты, выполните команду `pip` с аргументом `-U`.

```console
pip install -U winmltools
```

Для разных преобразователей нужно использовать разные пакеты.

Для **libsvm**можно скачать **libsvm wheel** из любого источника в Интернете. Один из примеров доступен на веб-сайте [Калифорнийского университета в Ирвайне](https://www.lfd.uci.edu/~gohlke/pythonlibs/#libsvm).

Для **coremltools** компания Apple пока не предоставляет пакет Core ML для Windows. Вы можете выполнить установку из исходного кода:

```console
pip install git+https://github.com/apple/coremltools
```

Подпишитесь на [onnxmltools](https://github.com/onnx/onnxmltools) на GitHub, чтобы получать дополнительные сведения о зависимостях **onnxmltools**.

См. сведения о том, как использовать WinMLTools, в документации по пакетам с помощью функции `help`.

```console
help(winmltools)
```

## <a name="convert-core-ml-models"></a>Преобразование моделей Core ML

Здесь мы предполагаем, что файл примера модели Core ML размещен в каталоге *example.mlmodel*.

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
> Вторым параметром в вызове convert_coreml() является target_opset. Он обозначает номер версии операторов в пространстве имен по умолчанию `ai.onnx`. См. сведения об [этих операциях](https://github.com/onnx/onnx/blob/master/docs/Operators.md). Этот параметр доступен только в последней версии WinMLTools. Он позволяет разработчикам использовать разные версии ONNX (сейчас поддерживаются версии 1.2.2 и 1.3). Чтобы преобразовать модели для работы с обновлением Windows от 10 октября 2018 г., используйте `target_opset` версии 7 (ONNX 1.2.2). В Windows 10 сборки 17763 и выше WinML поддерживаются модели с `target_opset` версий 7 и 8 (ONNX 1.3). В разделе [заметок о выпуске](release-notes.md) также указаны минимальная и максимальная версии ONNX, поддерживаемые в WinML разных сборок.

`model_onnx` является объектом ONNX [ModelProto](https://github.com/onnx/onnxmltools/blob/0f453c3f375c1ae928b83a4c7909c82c013a5bff/onnxmltools/proto/onnx-ml.proto#L176). Его можно сохранить в двух разных форматах.

~~~python
from winmltools.utils import save_model
# Save the produced ONNX model in binary format
save_model(model_onnx, 'example.onnx')
# Save the produced ONNX model in text format
from winmltools.utils import save_text
save_text(model_onnx, 'example.txt')
~~~

> [!NOTE]
>CoreMLTools — это пакет Python, предоставляемый компанией Apple, который недоступен для Windows. Если вам нужно установить этот пакет в Windows, установите его непосредственно из репозитория:

```console
pip install git+https://github.com/apple/coremltools
```

## <a name="convert-core-ml-models-with-image-inputs-or-outputs"></a>Преобразование моделей Core ML с форматом изображений для входных и выходных данных

Из-за отсутствия типов изображений в ONNX для преобразования моделей изображений Core ML (т. е. моделей, в которых изображения используются в качестве входных или выходных данных) требуется предварительные обработка и постобработка.

Задача предварительной обработки — правильное форматирование входного изображения в виде тензора ONNX. Предположим, *X* — это входное изображение Core ML с размерами [C, H, W]. В ONNX переменная *X* будет тензором с плавающей запятой тех же размеров, а *X*[0, :, :]/*X*[1, :, :]/*X*[2, :, :] содержат красный, зеленый и синий каналы изображения соответственно. Для изображений Core ML в градациях серого тензоры ONNX будут иметь формат [1, H, W], так как используется только один канал.

Если первоначальная модель Core ML выводит изображение, вручную преобразуйте выходные тензоры с плавающей запятой ONNX обратно в изображения. Для этого выполните два шага: Первый — усечение всех значений больше 255 до 255 и изменение всех отрицательных значений на 0. Второй — округление всех значений пикселей до целых чисел (путем добавления 0,5 и усечения дробной части). Порядок выходных каналов (например, RGB или BGR) указывается в модели Core ML. Для создания допустимого выходного изображения нам может потребоваться выполнить транспозицию или изменение порядка для восстановления требуемого формата.

Здесь мы рассмотрим преобразование на примере модели Core ML, FNS-Candy, скачанной на [GitHub](https://github.com/likedan/Awesome-CoreML-Models). Этот пример демонстрирует разницу между форматами ONNX и Core ML. Обратите внимание, что все последующие команды выполняются в среде Python.

Во-первых, мы загружаем модель Core ML и проверяем ее входной и выходной форматы.

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

В нашем случае входные и выходные данные представлены изображением BGR размером 720 x 720 пикселей. Следующий шаг — преобразование модели Core ML с помощью WinMLTools.

~~~python
# The automatic code generator (mlgen) uses the name parameter to generate class names.
from winmltools import convert_coreml
model_onnx = convert_coreml(model_coreml, 7, name='FNSCandy')
~~~

Альтернативный метод просмотра входного и выходного форматов модели в ONNX — использовать следующую команду:

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

Полученные входные данные (обозначены как *X*) в ONNX представляют собой четырехмерный тензор. Последними тремя осями являются: C, H и W соответственно. Первое измерение обозначается как None, то есть эта модель ONNX может применяться к любому количеству изображений. Если эта модель применяется для обработки пакета, состоящего из двух изображений, первому изображение соответствует *X*[0, :, :, :], а второму — *X*[1, :, :, :]. Синий, зеленый и красный каналы первого изображения сохраняются в *X*[0, 0, :, :]/*X*[0, 1, :, :]/*X*[0, 2, :, :]. То же справедливо и для второго изображения.

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

Как видно, создаваемый формат идентичен формату входных данных исходной модели. Но этот пример не является изображением, так как значения пикселей представлены целыми числами, а не числами с плавающей запятой. Чтобы преобразовать его обратно в изображение, усеките числа больше 255 до 255, измените отрицательные значения на 0 и округлите все десятичные числа до целых чисел.

## <a name="convert-scikit-learn-models"></a>Преобразование моделей scikit-learn

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

Как и раньше, `convert_sklearn` принимает модель scikit-learn в качестве первого аргумента и `target_opset` в качестве второго. Пользователи могут заменить `LinearSVC` другими моделями scikit-learn, например `RandomForestClassifier`. Обратите внимание, что [mlgen](mlgen.md) использует для создания имен классов и переменных параметр `name`. Если `name` не предоставляется, создается идентификатор GUID, который не будет соответствовать соглашениям об именовании для таких языков, как C++/C#.

## <a name="convert-scikit-learn-pipelines"></a>Преобразование конвейеров scikit-learn

Теперь мы рассмотрим, как преобразовать в формат ONNX конвейеры scikit-learn.

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

## <a name="convert-tensorflow-models"></a>Преобразование моделей TensorFlow

Следующий пример кода преобразует зафиксированную модель TensorFlow. Чтобы получить возможные выходные имена модели TensorFlow, можно использовать [средство summarize_graph](https://github.com/tensorflow/tensorflow/tree/master/tensorflow/tools/graph_transforms).

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

Преобразователь WinMLTools использует `tf2onnx.tfonnx.process_tf_graph` в [TF2ONNX](https://github.com/onnx/tensorflow-onnx).

## <a name="convert-to-floating-point-16"></a>Преобразование в 16-разрядные значения с плавающей запятой

WinMLTools поддерживает преобразование моделей, представленных в формате 32-разрядных значений с плавающей запятой, в представление 16-разрядных значений с плавающей запятой (IEEE 754 half), что позволяет вдвое уменьшить размер модели.

> [!NOTE]
> Преобразование модели в 16-разрядным значениям с плавающей запятой может привести к снижению точности. Не забудьте проверить точность модели перед ее развертыванием в приложении.

Ниже приведен полный пример преобразования непосредственно из двоичного файла ONNX.

~~~python
from winmltools.utils import convert_float_to_float16
from winmltools.utils import load_model, save_model
onnx_model = load_model('model.onnx')
new_onnx_model = convert_float_to_float16(onnx_model)
save_model(new_onnx_model, 'model_fp16.onnx')
~~~

См. сведения об этом средстве с помощью `help(winmltools.utils.convert_float_to_float16)`. 16-разрядные значения с плавающей запятой в WinMLTools сейчас соответствуют только [числам с плавающей запятой половинной точности (стандарт IEEE 754 (2008))](https://en.wikipedia.org/wiki/Half-precision_floating-point_format).

## <a name="post-training-weight-quantization"></a>Применение дискретизации весовых коэффициентов после обучения

WinMLTools также поддерживает сжатие моделей, представленных в формате 32-разрядных значений с плавающей запятой, в 8-разрядные целочисленные представления. Это может снизить размер модели на диске на 75 %, в зависимости от модели. Такое сокращение выполняется методом дискретизации весовых коэффициентов, в котором значения параметров модели анализируются. При этом сохраненные в тензоре весовые коэффициенты преобразуются из 32-разрядных чисел с плавающей запятой в 8-разрядные данные.

> [!NOTE]
> Дискретизация весовых коэффициентов после обучения может привести к снижению точности результирующей модели. Не забудьте проверить точность модели перед ее развертыванием в приложении.

Ниже приведен полный пример, в котором демонстрируется преобразование непосредственно из двоичного файла ONNX.

```python
import winmltools

model = winmltools.load_model('model.onnx')
packed_model = winmltools.quantize(model, per_channel=True, nbits=8, use_dequantize_linear=True)
winmltools.save_model(packed_model, 'quantized.onnx')
```

Вот еще некоторые сведения о входных параметрах `quantize`:

- `per_channel`: Если задано значение `True`, применяется линейная дискретизация каждого канала для каждого инициализированного тензора в формате [n, c, h, w]. По умолчанию этот параметр имеет значение `True`.
- `nbits`: Число битов для представления квантованных значений. Сейчас поддерживается только 8 битов.
- `use_dequantize_linear`: Если задано значение `True`, применяется линейный процесс, обратный квантованию каждого канала, в инициализированных тензорах для операторов Conv в формате [n, c, h, w]. По умолчанию устанавливается значение `True`.

## <a name="create-custom-onnx-operators"></a>создание пользовательских операторов ONNX.

Для преобразования модели Keras или Core ML можно написать пользовательскую функцию оператора, чтобы внедрять пользовательские [операторы](https://github.com/onnx/onnx/blob/master/docs/Operators.md) в граф ONNX. Во время преобразования преобразователь вызывает эту функцию, чтобы перевести слой Keras или объект LayerParameter из Core ML в оператор ONNX, а затем подключает узел оператора ко всему графу.

1. Создайте пользовательскую функцию для создания вложенного графа ONNX.
2. Вызовите `winmltools.convert_keras` или `winmltools.convert_coreml` с картой сопоставления имен пользовательских слоев и пользовательских функций.
3. Если применимо, реализуйте пользовательский слой для среды выполнения вывода.  

В следующем примере показано, как это работает в Keras.

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
