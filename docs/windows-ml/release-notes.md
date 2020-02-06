---
author: rosanevallim
title: Заметки о выпуске
description: Последние обновления платформы Windows AI.
ms.author: rovalli
ms.date: 4/18/2019
ms.topic: article
keywords: windows 10, windows ai, windows ml, winml, windows machine learning
ms.localizationpriority: medium
ms.openlocfilehash: e306d8d1af0a421b8da7814f212483d3f7870fa9
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66180036"
---
# <a name="release-notes"></a>Заметки о выпуске

На этой странице представлена история обновлений Windows ML в последних сборках пакета SDK для Windows 10.

## <a name="build-18362-windows-10-version-1903"></a>Сборка 18362 (Windows 10, версия 1903)

Все компоненты и обновления из предыдущих тестовых сборок.

* Поддержка ONNX 1.3
* Поддержка уменьшения размера модели путем квантования весовых коэффициентов после обучения. Вы можете использовать последнюю версию WinMLTools для сжатия весовых коэффициентов модели до формата 8-разрядного целого числа.
* Удаление mlgen из пакета SDK для Windows 10 — теперь вместо него следует использовать одно из следующих расширений Visual Studio.
    * Visual Studio 2017: [Генератор кода VS 2017 для Windows Machine Learning (WinML)](https://marketplace.visualstudio.com/items?itemName=WinML.mlgen)
    * Visual Studio 2019: [Генератор кода для Windows Machine Learning (WinML)](https://marketplace.visualstudio.com/items?itemName=WinML.mlgenv2)

## <a name="build-18829"></a>Сборка 18829

* Из пакета SDK для Windows 10 удалено средство [mlgen](mlgen.md). Вместо него установите одно из следующих расширений Visual Studio в зависимости от используемой версии.
    * Visual Studio 2017: [Генератор кода VS 2017 для Windows Machine Learning (WinML)](https://marketplace.visualstudio.com/items?itemName=WinML.mlgen)
    * Visual Studio 2019: [Генератор кода для Windows Machine Learning (WinML)](https://marketplace.visualstudio.com/items?itemName=WinML.mlgenv2)

## <a name="build-18290"></a>Сборка 18290
- Минимальная поддерживаемая версия ONNX — 1.2.2 (набор операций 7)
- Минимальная поддерживаемая версия ONNX — 1.3 (набор операций 8)
- Поддержка снижения размера модели путем дискретизации весовых коэффициентов после обучения. Вы можете использовать последнюю версию WinMLTools для сжатия весовых коэффициентов модели до формата 8-разрядного целого числа.

## <a name="build-17763-windows-10-version-1809"></a>Сборка 17763 (Windows 10, версия 1809)

* Первый официальный выпуск Windows Machine Learning.
* Требуется ONNX [версии 1.2](https://github.com/onnx/onnx/tree/rel-1.2.2).
* [Пространство имен Windows.AI.MachineLearning.Preview](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.preview) объявлено устаревшим и заменяется на [пространство имен Windows.AI.MachineLearning](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning).

### <a name="known-issues"></a>Известные проблемы

* Для моделей с последовательностями MLGen создает объект **IList&lt;Dictionary&lt;*key*, *value*&gt;&gt;** вместо нужного **IList&lt;IDictionary&lt;*key*, *value*&gt;&gt;** , что приводит к выдаче пустых результатов. Чтобы устранить эту проблему, просто подставьте в автоматически созданный код строку **IList&lt;IDictionary&lt;*key*, *value*&gt;&gt;** .

## <a name="build-17723"></a>Сборка 17723

- Требуется ONNX [версии 1.2](https://github.com/onnx/onnx/tree/rel-1.2.2).
- Поддерживает типы данных F16 для вывода модели на основе GPU, что позволяет [повысить производительность](performance-memory.md) и снизить объем модели. WinMLTools можно использовать для [преобразования моделей из FP32 в FP16](convert-model-winmltools.md#convert-to-floating-point-16).
- Позволяет классическим приложениям использовать [API-интерфейсы Windows.AI.MachineLearning](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning) для [C++/WinRT](https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/).

[!INCLUDE [help](../includes/get-help.md)]
