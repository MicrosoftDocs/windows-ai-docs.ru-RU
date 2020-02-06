---
title: Что собой представляет модель машинного обучения
description: Сведения о концепции модели в контексте Windows Machine Learning.
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10, windows ai, windows ml, winml, windows machine learning
ms.localizationpriority: medium
ms.openlocfilehash: a2c43090d44d6ac3c9e3c095ff83da5d58976265
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70156261"
---
# <a name="what-is-a-machine-learning-model"></a>Что собой представляет модель машинного обучения

Моделью машинного обучения называется файл, который обучен распознаванию определенных типов закономерностей. Обучение модели выполняется по некоторому набору данных с использованием алгоритма, который позволяет анализировать предоставленные данные и запоминать полученные результаты.

Завершив обучение модели, вы сможете применить ее для принятия решений и выполнения прогнозов по данным, которые ранее не встречались. Предположим, вам нужно создать приложение для распознавания эмоций пользователя по его выражению лица. Вы можете обучить модель по набору изображений лиц, каждое из которых отмечено тегом определенной эмоции, а затем применить эту модель в приложении для распознавания эмоций пользователя. Примером такого приложения служит [Emoji8](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/Emoji8/UWP/cs).

Windows Machine Learning использует для своих моделей формат [ONNX (Open Neural Network Exchange)](https://onnx.ai/). Вы можете скачать предварительно обученную модель или обучить собственную. Дополнительные сведения о получении моделей ONNX для Windows ML см. в [этой статье](get-onnx-model.md).

[!INCLUDE [help](../includes/get-help.md)]
