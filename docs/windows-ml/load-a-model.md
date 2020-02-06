---
title: Загрузка модели
description: Сведения о том, как загрузить в приложение модель ONNX, чтобы использовать ее в Windows Machine Learning.
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10, windows ai, windows ml, winml, windows machine learning
ms.localizationpriority: medium
ms.openlocfilehash: c0fd10c4f970659d4560fbb4b4d259c6d30b11c4
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70156604"
---
# <a name="load-a-model"></a>Загрузка модели

> [!IMPORTANT]
> Для Windows Machine Learning требуются модели ONNX версии 1.2 или более поздней.

[Получив обученную модель ONNX](get-onnx-model.md), файлы этой модели вы распространяете в составе приложения. ONNX-файлы можно напрямую включить в пакет APPX или (для классических приложений) расположить в любом месте на жестком диске, откуда ваше приложение сможет их получить.

Есть несколько способов загрузить модель с использованием статических методов класса [LearningModel](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodel):

* [LearningModel.LoadFromStreamAsync](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodel.loadfromstreamasync);
* [LearningModel.LoadFromStream](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodel.loadfromstream);
* [LearningModel.LoadFromStorageFileAsync](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodel.loadfromstoragefileasync);
* [LearningModel.LoadFromFilePath](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodel.loadfromfilepath).

Методы **LoadFromStream*** позволяют реализовать в приложениях более строгий контроль источников модели. Например, приложение может использовать зашифрованную модель, которая размещена на диске, и расшифровать ее в памяти прямо перед вызовом одного из методов **LoadFromStream***. Также можно загружать поток модели из общей сетевой папки или с другого носителя.

> [!TIP]
> Загрузка модели может занять некоторое время, поэтому метод **Load*** не следует вызывать из потока пользовательского интерфейса.

В следующем примере показано, как можно загрузить модель в приложение.

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

## <a name="see-also"></a>См. также статью

* Далее: [Создание сеанса](create-a-session.md)

[!INCLUDE [help](../includes/get-help.md)]
