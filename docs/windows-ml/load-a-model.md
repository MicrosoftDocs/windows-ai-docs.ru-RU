---
title: Загрузка модели
description: Узнайте, как загрузить модель ONNX в приложение для использования Машинное обучение Windows.
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10, windows ai, windows ml, winml, windows machine learning
ms.localizationpriority: medium
ms.openlocfilehash: c0fd10c4f970659d4560fbb4b4d259c6d30b11c4
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70156604"
---
# <a name="load-a-model"></a>Загрузка модели

> [!IMPORTANT]
> Для Машинное обучение Windows требуются модели ONNX версии 1,2 или более поздней.

После [получения обученной модели ONNX](get-onnx-model.md)вы распространяете файлы модели. ONNX вместе с приложением. Вы можете включить onnx-файлы в пакет APPX или, для классических приложений, они могут находиться в любом месте, где ваше приложение может получить доступ к жесткому диску.

Существует несколько способов загрузить модель с помощью статических методов в классе [леарнингмодел](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodel) :

* [Леарнингмодел. Лоадфромстреамасинк](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodel.loadfromstreamasync)
* [Леарнингмодел. Лоадфромстреам](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodel.loadfromstream)
* [Леарнингмодел. Лоадфромсторажефилеасинк](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodel.loadfromstoragefileasync)
* [Леарнингмодел. Лоадфромфилепас](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodel.loadfromfilepath)

Методы **лоадфромстреам*** позволяют приложениям иметь больший контроль над местом, откуда берется модель. Например, приложение может выбрать модель, зашифрованную на диске, и расшифровать ее только в памяти до вызова одного из методов **лоадфромстреам***. Другие параметры включают загрузку потока модели из общей сетевой папки или с другого носителя.

> [!TIP]
> Загрузка модели может занять некоторое время, поэтому не следует вызывать метод **Load*** из потока пользовательского интерфейса.

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

## <a name="see-also"></a>См. также

* Далее: [Создание сеанса](create-a-session.md)

[!INCLUDE [help](../includes/get-help.md)]
