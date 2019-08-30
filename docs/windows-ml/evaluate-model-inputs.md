---
title: Оценка входных данных модели
description: Узнайте, как выполнить оценку входных данных модели для получения прогнозов.
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10, windows ai, windows ml, winml, windows machine learning
ms.localizationpriority: medium
ms.openlocfilehash: 9f23b272f85f1bd3beb60bfea341c522941fa854
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70156716"
---
# <a name="evaluate-the-model-inputs"></a>Оценка входных данных модели

После привязки значений к входным и выходным данным модели вы можете оценить входные данные модели и получить ее прогнозы.

Чтобы запустить модель, вызовите любой из методов **Evaluate*** в [леарнингмоделсессион](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodelsession). Вы можете использовать [леарнингмоделевалуатионресулт](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodelevaluationresult) для просмотра выходных функций.

## <a name="example"></a>Пример

В следующем примере выполняется оценка сеанса, передача привязки и уникального идентификатора корреляции. Затем мы анализируем выходные данные в виде списка вероятностей, сопоставляюте их со списком меток для различных вещей, которые может распознать наша модель, и записывают результаты в консоль:

```cs
// How many times an evaluation has been run
private int runCount = 0;

private void EvaluateModel(
    LearningModelSession session,
    LearningModelBinding binding,
    string outputName,
    List<string> labels)
{
    // Process the frame with the model
    var results =
        await session.EvaluateAsync(binding, $"Run {++runCount}");

    // Retrieve the results of evaluation
    var resultTensor = results.Outputs[outputName] as TensorFloat;
    var resultVector = resultTensor.GetAsVectorView();

    // Find the top 3 probabilities
    List<(int index, float probability)> indexedResults = new List<(int, float)>();

    for (int i = 0; i < resultVector.Count; i++)
    {
        indexedResults.Add((index: i, probability: resultVector.ElementAt(i)));
    }

    // Sort the results in order of highest probability
    indexedResults.Sort((a, b) =>
    {
        if (a.probability < b.probability)
        {
            return 1;
        }
        else if (a.probability > b.probability)
        {
            return -1;
        }
        else
        {
            return 0;
        }
    });

    // Display the results
    for (int i = 0; i < 3; i++)
    {
        Debug.WriteLine(
            $"\"{labels[indexedResults[i].index]}\" with confidence of {indexedResults[i].probability}");
    }
}
```

## <a name="device-removal"></a>Удаление устройства

Если устройство становится недоступным или вы хотите использовать другое устройство, необходимо закрыть сеанс и создать новый сеанс.

В некоторых случаях может потребоваться выгрузить и перезагрузить графические устройства, как описано в [документации DirectX](https://docs.microsoft.com/windows/uwp/gaming/handling-device-lost-scenarios).

При использовании Windows ML необходимо обнаружить этот случай и закрыть сеанс. Чтобы выполнить восстановление после удаления или повторной инициализации устройства, необходимо создать новый сеанс, который запускает логику выбора устройства для повторного запуска.

Наиболее распространенный случай, когда вы увидите эту ошибку во время [леарнингмоделсессион. Evaluate](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodelsession.evaluate). В случае удаления или сброса устройства [леарнингмоделевалуатионресулт. еррорстатус](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodelevaluationresult.errorstatus) будет иметь значение [DXGI_ERROR_DEVICE_REMOVED](https://docs.microsoft.com/windows/desktop/direct3ddxgi/dxgi-error) или [DXGI_ERROR_DEVICE_RESET](https://docs.microsoft.com/windows/desktop/direct3ddxgi/dxgi-error).

## <a name="see-also"></a>См. также

* Прошлом [Привязка модели](bind-a-model.md)

[!INCLUDE [help](../includes/get-help.md)]
