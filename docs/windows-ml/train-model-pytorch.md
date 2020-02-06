---
title: Обучение модели с помощью PyTorch и экспорт в формат ONNX
description: Сведения о том, как обучить модель ONNX с помощью PyTorch.
ms.date: 7/10/2019
ms.topic: article
keywords: windows 10, windows ai, windows ml, winml, windows machine learning, pytorch
ms.localizationpriority: medium
ms.openlocfilehash: 7aa1091cf3622f532c6601a040fad5c80746d6b3
ms.sourcegitcommit: ecd33843dd548e443a1292d6a22e1a4029298944
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2020
ms.locfileid: "75737407"
---
# <a name="train-a-model-with-pytorch-and-export-to-onnx"></a>Обучение модели с помощью PyTorch и экспорт в формат ONNX

Используя платформу [PyTorch](https://pytorch.org/) и [Машинное обучение Azure](https://azure.microsoft.com/services/machine-learning-service/), можно обучить модель в облаке и скачать ее в формате ONNX-файла для локального выполнения в Windows Machine Learning.

## <a name="train-the-model"></a>Обучение модели

С помощью Машинного обучения Azure вы можете обучить модель PyTorch в облаке, используя все преимущества быстрого масштабирования, развертывания и т. п. Дополнительные сведения см. в статье [об обучении и регистрации моделей PyTorch в большом масштабе с помощью Машинного обучения Azure](https://docs.microsoft.com/azure/machine-learning/service/how-to-train-pytorch).

## <a name="export-to-onnx"></a>Экспорт в формат ONNX

Выполнив обучение модели, вы можете экспортировать ее в ONNX-файл, чтобы выполнять локально в Windows ML. Инструкции по экспорту моделей из PyTorch в формате, пригодном для Windows ML, см. в [этой статье](https://github.com/onnx/tutorials/blob/master/tutorials/ExportModelFromPyTorchForWinML.md).


## <a name="integrate-with-windows-ml"></a>Интеграция с Windows ML

Когда вы выполните экспорт модели в формат ONNX, ее можно будет интегрировать в приложение Windows ML. Решение Windows ML доступно для нескольких языков программирования, и вы можете выбрать руководство для того языка, с которым вам удобнее работать.

* **C#:** [Создание приложения UWP (C#) для Windows Machine Learning](https://docs.microsoft.com/windows/ai/windows-ml/get-started-uwp).

* **Python:** [Создание приложения UWP на Python для Windows Machine Learning](https://github.com/Microsoft/xlang/tree/master/samples/python/winml_tutorial).

* **C++:** [Создание классического приложения (C++) для Windows Machine Learning](https://docs.microsoft.com/windows/ai/windows-ml/get-started-desktop).

[!INCLUDE [help](../includes/get-help.md)]
