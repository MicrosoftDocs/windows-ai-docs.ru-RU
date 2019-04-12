---
author: rosanevallim
title: Заметки о выпуске
description: Последние обновления на платформе Windows искусственного Интеллекта.
ms.author: rovalli
ms.date: 2/25/2019
ms.topic: article
keywords: Windows 10, windows искусственного интеллекта, машинного обучения windows, winml, windows машинное обучение
ms.localizationpriority: medium
ms.openlocfilehash: 14a28d38c9ea50588c1d4ba4ef1863e0aa6811ff
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474911"
---
# <a name="release-notes"></a>Заметки о выпуске

Это страница записей обновления для машинного Обучения Windows в последних сборках пакета SDK для Windows 10.

## <a name="build-18829"></a>Сборки 18829

* [mlgen](mlgen.md) был удален из пакета SDK для Windows 10. Вместо этого установите одно из следующих расширений Visual Studio в зависимости от используемой версии.
    * Visual Studio 2017: [Windows в машинном обучении генератора кода Visual STUDIO 2017](https://marketplace.visualstudio.com/items?itemName=WinML.mlgen)
    * Visual Studio 2019 г.: [Генератор кода обучения компьютера Windows](https://marketplace.visualstudio.com/items?itemName=WinML.mlgenv2)

## <a name="build-18290"></a>Сборки 18290
- Минимальная поддерживаемая версия ONNX = 1.2.2 (opset 7)
- Максимальная поддерживаемая версия ONNX = 1.3 (opset 8)
- Поддерживает линейно квантованных модели. Можно использовать последнюю версию WinMLTools для [квантования моделей](convert-model-winmltools.md#quantize-onnx-model).

## <a name="build-17763"></a>Сборки 17763

* Первый официального выпуска Windows машинного обучения.
* Требуется ONNX [v1.2](https://github.com/onnx/onnx/tree/rel-1.2.2).
* [Пространство имен Windows.AI.MachineLearning.Preview](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.preview) заменяется [пространства имен Windows.AI.MachineLearning](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning).

### <a name="known-issues"></a>Известные проблемы

* Для моделей, содержащую последовательности, создает MLGen **IList&lt;словарь&lt;*ключ*, *значение* &gt; &gt;**  вместо соответствующих **IList&lt;IDictionary&lt;*ключ*, *значение*&gt;&gt;**, что приведет к Пустые результаты. Чтобы устранить эту проблему, просто замените автоматически созданный код с соответствующим **IList&lt;IDictionary&lt;*ключ*, *значение* &gt; &gt;**  вместо этого.

## <a name="build-17723"></a>Сборки 17723

- Требуется ONNX [v1.2](https://github.com/onnx/onnx/tree/rel-1.2.2).
- Поддерживает типы данных F16 с выводы модель на основе GPU для [более высокую производительность](performance-memory.md) и уменьшить занимаемое место в модели. Можно использовать WinMLTools для [преобразование вашей моделей из FP32 FP16](convert-model-winmltools.md#convert-to-floating-point-16).
- Позволяет классических приложений для использования [API-интерфейсы Windows.AI.MachineLearning](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning) с [WinRT /C++](https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/).

[!INCLUDE [help](includes/get-help.md)]
