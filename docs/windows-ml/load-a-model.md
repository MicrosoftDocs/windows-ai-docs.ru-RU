---
author: eliotcowley
title: Загрузка модели
description: Узнайте, как загрузить модели ONNX в приложения для машинного обучения Windows для использования.
ms.author: elcowle
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10, windows ai, windows ml, winml, windows machine learning
ms.localizationpriority: medium
ms.openlocfilehash: a65eb38f666b2e2c2d72290804cb25430ac7ca8a
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66181916"
---
# <a name="load-a-model"></a>Загрузка модели

> [!IMPORTANT]
> Windows машинного обучения требует моделями ONNX, 1.2 или более поздней версии.

Когда вы [получить обученной модели ONNX](get-onnx-model.md), вы будете распространять файлы модели .onnx с вашим приложением. Файлы .onnx можно включить в пакет APPX или для классических приложений, их можно везде, где приложение может обращаться к на жестком диске.

Существует несколько способов загрузки модели с помощью статических методов на [LearningModel](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodel) класса:

* [LearningModel.LoadFromStreamAsync](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodel.loadfromstreamasync)
* [LearningModel.LoadFromStream](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodel.loadfromstream)
* [LearningModel.LoadFromStorageFileAsync](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodel.loadfromstoragefileasync)
* [LearningModel.LoadFromFilePath](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodel.loadfromfilepath)

**LoadFromStream*** методы позволяют приложениям более строгий контроль над образуется модели. Например, приложение можно в модели, в зашифрованном виде на диске и расшифровать его только в памяти до вызова одного из **LoadFromStream*** методы. Другие варианты включают загрузке модели потока из общей сетевой папке или другого носителя.

> [!TIP]
> Загрузка модели может занять некоторое время, так что будьте осторожны не для вызова **нагрузки*** метод из потока пользовательского интерфейса.

В следующем примере показано, как можно загрузить модель в приложение:

```cs
private async LearningModel LoadModelAsync(string modelPath)
{
    // Load and create the model 
    var modelFile = await StorageFile.GetFileFromApplicationUriAsync(
        new Uri(modelPath));

    LearningModel model = 
        await LearningModel.LoadFromStorageFileAsync(modelFile);

    return model;
}
```

## <a name="see-also"></a>См. также

* Далее: [Создание сеанса](create-a-session.md)

[!INCLUDE [help](../includes/get-help.md)]
