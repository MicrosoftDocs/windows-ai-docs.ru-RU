---
author: eliotcowley
title: Обучение модели с PyTorch и экспорта для ONNX
description: Узнайте, как для обучения модели ONNX с PyTorch.
ms.author: elcowle
ms.date: 7/10/2019
ms.topic: article
keywords: Windows 10, windows искусственного интеллекта, машинного обучения windows, winml, машинного обучения windows, pytorch
ms.localizationpriority: medium
ms.openlocfilehash: 6c1f9ac16bfa2359b01b26ecd297b9087caa8c14
ms.sourcegitcommit: 785057dc180cb252ce63460efaaff321e046a0dd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2019
ms.locfileid: "67804774"
---
# <a name="train-a-model-with-pytorch-and-export-to-onnx"></a>Обучение модели с PyTorch и экспорта для ONNX

С помощью [PyTorch](https://pytorch.org/) framework и [службы машинного обучения Azure](https://azure.microsoft.com/services/machine-learning-service/), можно обучить модель в облаке и скачать его как файл ONNX для локального выполнения с помощью машинного обучения Windows.

## <a name="train-the-model"></a>Обучение модели

С помощью машинного Обучения Azure вы можете обучить модель PyTorch в облаке, получить преимущества быстрого масштабирования, развертывания и многое другое. См. в разделе [Train и регистрация PyTorch моделирует нужного масштаба с помощью службы машинного обучения Azure](https://docs.microsoft.com/azure/machine-learning/service/how-to-train-pytorch) Дополнительные сведения.

## <a name="export-to-onnx"></a>Экспорт в ONNX

После обучения модели, его можно экспортировать как файл ONNX, который можно запустить локально с помощью машинного Обучения Windows. Прежде чем начинать экспорта, тем не менее, проверьте [построения ONNX версии и Windows](https://docs.microsoft.com/windows/ai/windows-ml/onnx-versions) для определения, какие версии ONNX поддерживаются на целевой платформой является построение Windows.

Когда вы будете готовы для экспорта, см. в разделе [модель Экспорт из PyTorch ONNX](https://github.com/onnx/tutorials/blob/master/tutorials/PytorchOnnxExport.ipynb).

## <a name="integrate-with-windows-ml"></a>Интеграция с Windows машинного Обучения

После экспорта модели ONNX вы готовы интегрировать его в приложении Windows машинного Обучения. Машинного Обучения Windows доступна на нескольких языках программирования, поэтому ознакомьтесь с руководством язык, который наиболее удобно с.

* **C#:** [Создание приложения универсальной платформы Windows машины обучения Windows (C#)](https://docs.microsoft.com/windows/ai/windows-ml/get-started-uwp)

* **Python.** [Создание приложения Windows машинного обучения с помощью Python](https://github.com/Microsoft/xlang/tree/master/samples/python/winml_tutorial)

* **C++:** [Создание приложения рабочем столе Windows компьютера обучения (C++)](https://docs.microsoft.com/windows/ai/windows-ml/get-started-desktop)

[!INCLUDE [help](../includes/get-help.md)]
