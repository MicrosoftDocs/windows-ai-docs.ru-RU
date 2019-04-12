---
author: eliotcowley
title: Обучение модели с PyTorch
description: Узнайте, как для обучения модели ONNX с PyTorch.
ms.author: elcowle
ms.date: 11/5/2018
ms.topic: article
keywords: Windows 10, windows искусственного интеллекта, машинного обучения windows, winml, машинного обучения windows, pytorch
ms.localizationpriority: medium
ms.openlocfilehash: 3077447e06e3898328a1f5f8939efec4288aefe4
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474311"
---
# <a name="train-a-model-with-pytorch"></a>Обучение модели с PyTorch

С помощью [PyTorch](https://pytorch.org/) framework, можно обучить модель локально или в облаке и затем загрузить модель как файл ONNX для локального выполнения с помощью машинного обучения Windows.

## <a name="train-locally"></a>Обучение локально

См. в разделе [mnist.py](https://github.com/Azure/MachineLearningNotebooks/blob/master/onnx/mnist.py) в хранилище Azure/MachineLearningNotebooks пример того, как для обучения MNIST модели локально с помощью PyTorch.

Дополнительные сведения о PyTorch, см. в разделе PyTorch [учебники](https://pytorch.org/tutorials/) и [документации](https://pytorch.org/docs/stable/index.html).

## <a name="train-in-the-cloud"></a>Обучение в облаке

С помощью машинного обучения Azure и PyTorch можно обучить модель в облаке и скачайте его для локального выполнения с помощью машинного обучения Windows. [GitHub-репозитории Azure/MachineLearningNotebooks](https://github.com/Azure/MachineLearningNotebooks) имеет несколько примеров и руководств для машинного Обучения Azure, большинство из которых являются [записные книжки Jupyter](https://jupyter.org/). См. в разделе [README](https://github.com/Azure/MachineLearningNotebooks/blob/master/README.md) сведения о запуске этих учебников машинного Обучения Azure с помощью записных книжек Azure или собственный сервер записной книжки Jupyter.

Когда вы азы все настроено, можно открыть [классификации рукописных цифр MNIST, с помощью ONNX и машинного Обучения Azure](https://github.com/Azure/MachineLearningNotebooks/blob/master/onnx/onnx-train-pytorch-aml-deploy-mnist.ipynb) записной книжки и следуйте руководству, чтобы узнать, как для обучения MNIST модели с помощью PyTorch и машинного Обучения Azure. (Можно пропустить **развертывание веб-службы** раздел, если вы используете для запуска модели WinML.)

[!INCLUDE [help](includes/get-help.md)]
