---
title: Обучение модели с помощью PyTorch и экспорт в ONNX
description: Узнайте, как обучить модель ONNX с помощью PyTorch.
ms.date: 7/10/2019
ms.topic: article
keywords: Windows 10, Windows AI, Windows ml, winml, машинное обучение Windows, pytorch
ms.localizationpriority: medium
ms.openlocfilehash: d2d20b20ab790247ad7746d0cf8f221f9276e823
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70156327"
---
# <a name="train-a-model-with-pytorch-and-export-to-onnx"></a>Обучение модели с помощью PyTorch и экспорт в ONNX

С помощью [PyTorch](https://pytorch.org/) Framework и [службы машинное обучение Azure](https://azure.microsoft.com/services/machine-learning-service/)можно обучить модель в облаке и загрузить ее в виде файла ONNX для локального запуска с Windows машинное обучение.

## <a name="train-the-model"></a>Обучение модели

С помощью машинного обучения Azure вы можете обучить модель PyTorch в облаке, получить преимущества быстрого масштабирования, развертывания и многого другого. Дополнительные сведения см. в статьях [обучение и регистрация моделей PyTorch в масштабе с помощью службы машинное обучение Azure](https://docs.microsoft.com/azure/machine-learning/service/how-to-train-pytorch) .

## <a name="export-to-onnx"></a>Экспорт в ONNX

После обучения модели ее можно экспортировать в виде файла ONNX, чтобы его можно было запускать локально с помощью машинного обучения Windows. Инструкции по экспорту из PyTorch в собственном формате см. в разделе [Export PyTorch models for Windows ML](https://github.com/onnx/tutorials/blob/master/tutorials/ExportModelFromPyTorchForWinML.md) .


## <a name="integrate-with-windows-ml"></a>Интеграция с Windows ML

После экспорта модели в ONNX вы можете интегрировать ее в приложение машинного обучения Windows. Windows ML доступна на нескольких разных языках программирования, поэтому ознакомьтесь с руководством на языке, с которым вам удобнее работать.

* **C#:** [Создание приложения Windows Машинное обучение UWP (C#)](https://docs.microsoft.com/windows/ai/windows-ml/get-started-uwp)

* **Языке** [Создание приложения Машинное обучение Windows с помощью Python](https://github.com/Microsoft/xlang/tree/master/samples/python/winml_tutorial)

* **C++:** [Создание классического приложения Windows Машинное обучение (C++)](https://docs.microsoft.com/windows/ai/windows-ml/get-started-desktop)

[!INCLUDE [help](../includes/get-help.md)]
