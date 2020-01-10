---
title: Обучение модели с помощью PyTorch и экспорт в ONNX
description: Узнайте, как обучить модель ONNX с помощью PyTorch.
ms.date: 7/10/2019
ms.topic: article
keywords: Windows 10, Windows AI, Windows ml, winml, машинное обучение Windows, pytorch
ms.localizationpriority: medium
ms.openlocfilehash: 7aa1091cf3622f532c6601a040fad5c80746d6b3
ms.sourcegitcommit: ecd33843dd548e443a1292d6a22e1a4029298944
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2020
ms.locfileid: "75737407"
---
# <a name="train-a-model-with-pytorch-and-export-to-onnx"></a>Обучение модели с помощью PyTorch и экспорт в ONNX

[PyTorch](https://pytorch.org/) framework и [машинное обучение Azure](https://azure.microsoft.com/services/machine-learning-service/), вы можете обучить модель в облаке и загрузить ее как файл ONNX для локального запуска с Windows машинное обучение.

## <a name="train-the-model"></a>обучение модели;

С помощью машинного обучения Azure вы можете обучить модель PyTorch в облаке, получить преимущества быстрого масштабирования, развертывания и многого другого. Дополнительные сведения см. в статьях [обучение и регистрация моделей PyTorch в масштабе с помощью машинное обучение Azure](https://docs.microsoft.com/azure/machine-learning/service/how-to-train-pytorch) .

## <a name="export-to-onnx"></a>Экспорт в ONNX

После обучения модели ее можно экспортировать в виде файла ONNX, чтобы его можно было запускать локально с помощью машинного обучения Windows. Инструкции по экспорту из PyTorch в собственном формате см. в разделе [Export PyTorch models for Windows ML](https://github.com/onnx/tutorials/blob/master/tutorials/ExportModelFromPyTorchForWinML.md) .


## <a name="integrate-with-windows-ml"></a>Интеграция с Windows ML

После экспорта модели в ONNX вы можете интегрировать ее в приложение машинного обучения Windows. Windows ML доступна на нескольких разных языках программирования, поэтому ознакомьтесь с руководством на языке, с которым вам удобнее работать.

* : Создание [приложения Windows машинное обучение UWPC#()](https://docs.microsoft.com/windows/ai/windows-ml/get-started-uwp)  **C#**

* **Python:** [создание приложения Windows машинное обучение с помощью Python](https://github.com/Microsoft/xlang/tree/master/samples/python/winml_tutorial)

* : Создание [классического приложения Windows машинное обучение (C++)](https://docs.microsoft.com/windows/ai/windows-ml/get-started-desktop)  **C++**

[!INCLUDE [help](../includes/get-help.md)]
