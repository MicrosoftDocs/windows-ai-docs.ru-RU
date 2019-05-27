---
author: rosanevallim
title: Заметки о выпуске
description: Последние обновления на платформе Windows искусственного Интеллекта.
ms.author: rovalli
ms.date: 4/18/2019
ms.topic: article
keywords: windows 10, windows ai, windows ml, winml, windows machine learning
ms.localizationpriority: medium
ms.openlocfilehash: e306d8d1af0a421b8da7814f212483d3f7870fa9
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66180036"
---
# <a name="release-notes"></a>Заметки о выпуске

Это страница записей обновления для машинного Обучения Windows в последних сборках пакета SDK для Windows 10.

## <a name="build-18362-windows-10-version-1903"></a>Построение 18362 (Windows 10, версия 1903)

Все функции и обновления с предыдущих потерянная сборок:

* Поддержка ONNX 1.3
* Поддержка для уменьшения размера модели с помощью после обучения квантования вес. Можно использовать последнюю версию WinMLTools упаковать весовых коэффициентов модели до int8.
* Удаление mlgen из пакета SDK для Windows 10&mdash;вместо этого используйте один из следующих расширений Visual Studio:
    * Visual Studio 2017: [Windows в машинном обучении генератора кода Visual STUDIO 2017](https://marketplace.visualstudio.com/items?itemName=WinML.mlgen)
    * Visual Studio 2019 г.: [Генератор кода обучения компьютера Windows](https://marketplace.visualstudio.com/items?itemName=WinML.mlgenv2)

## <a name="build-18829"></a>Сборки 18829

* [mlgen](mlgen.md) был удален из пакета SDK для Windows 10. Вместо этого установите одно из следующих расширений Visual Studio в зависимости от используемой версии.
    * Visual Studio 2017: [Windows в машинном обучении генератора кода Visual STUDIO 2017](https://marketplace.visualstudio.com/items?itemName=WinML.mlgen)
    * Visual Studio 2019 г.: [Генератор кода обучения компьютера Windows](https://marketplace.visualstudio.com/items?itemName=WinML.mlgenv2)

## <a name="build-18290"></a>Сборки 18290
- Минимальная поддерживаемая версия ONNX = 1.2.2 (opset 7)
- Максимальная поддерживаемая версия ONNX = 1.3 (opset 8)
- Поддерживает модель, уменьшение размера через после обучения квантования вес. Можно использовать последнюю версию WinMLTools упаковать весовых коэффициентов модели до int8.

## <a name="build-17763-windows-10-version-1809"></a>Построение 17763 (Windows 10, версия 1809)

* Первый официального выпуска Windows машинного обучения.
* Требуется ONNX [v1.2](https://github.com/onnx/onnx/tree/rel-1.2.2).
* [Пространство имен Windows.AI.MachineLearning.Preview](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.preview) заменяется [пространства имен Windows.AI.MachineLearning](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning).

### <a name="known-issues"></a>Известные проблемы

* Для моделей, содержащую последовательности, создает MLGen **IList&lt;словарь&lt;*ключ*, *значение* &gt; &gt;**  вместо соответствующих **IList&lt;IDictionary&lt;*ключ*, *значение*&gt;&gt;**, что приведет к Пустые результаты. Чтобы устранить эту проблему, просто замените автоматически созданный код с соответствующим **IList&lt;IDictionary&lt;*ключ*, *значение* &gt; &gt;**  вместо этого.

## <a name="build-17723"></a>Сборка 17723

- Требуется ONNX [v1.2](https://github.com/onnx/onnx/tree/rel-1.2.2).
- Поддерживает типы данных F16 с выводы модель на основе GPU для [более высокую производительность](performance-memory.md) и уменьшить занимаемое место в модели. Можно использовать WinMLTools для [преобразование вашей моделей из FP32 FP16](convert-model-winmltools.md#convert-to-floating-point-16).
- Позволяет классических приложений для использования [API-интерфейсы Windows.AI.MachineLearning](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning) с [WinRT /C++](https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/).

[!INCLUDE [help](../includes/get-help.md)]
