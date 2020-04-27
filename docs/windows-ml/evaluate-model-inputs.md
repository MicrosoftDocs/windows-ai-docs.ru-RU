---
title: Оценка входных данных модели
description: Сведения о том, как выполнять оценку входных данных модели для получения прогнозов.
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10, windows ai, windows ml, winml, windows machine learning
ms.localizationpriority: medium
ms.openlocfilehash: 9f23b272f85f1bd3beb60bfea341c522941fa854
ms.sourcegitcommit: 2139506ff12b7205283288c4bbac866ddfa812f3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/24/2020
ms.locfileid: "70156716"
---
# <a name="evaluate-the-model-inputs"></a>Оценка входных данных модели

Выполнив привязку значений к входам и выходам модели, вы можете оценить входные данные модели и получить результаты прогнозирования.

Чтобы запустить модель, вызовите любой метод **Evaluate*** из [LearningModelSession](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodelsession). Выходные признаки можно проверить с помощью [LearningModelEvaluationResult](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodelevaluationresult).

## <a name="example"></a>Пример

В следующем примере мы выполним оценку в сеансе, передавая ему привязку и уникальный идентификатор корреляции. Затем мы проанализируем выходные данные, которые содержат список вероятностей, сопоставим их со списком меток для распознаваемых моделью сущностей, и выведем результаты в консоль.

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

Если устройство становится недоступным или вы хотите использовать другое устройство, необходимо закрыть текущий сеанс и создать новый.

В некоторых случаях нужно выгрузить и перезагрузить графическое устройство, как описано в [документации по DirectX](https://docs.microsoft.com/windows/uwp/gaming/handling-device-lost-scenarios).

При использовании Windows ML нужно отслеживать такую ситуацию, чтобы корректно закрыть сеанс. Чтобы возобновить работу после удаления или повторной инициализации устройства, создайте новый сеанс. Это действие приводит к повторному применению логики выбора устройства.

Такая ошибка чаще всего возникает при выполнении [LearningModelSession.Evaluate](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodelsession.evaluate). После удаления или сброса настроек устройства параметр [LearningModelEvaluationResult.ErrorStatus](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodelevaluationresult.errorstatus) принимает значение [DXGI_ERROR_DEVICE_REMOVED](https://docs.microsoft.com/windows/desktop/direct3ddxgi/dxgi-error) или [DXGI_ERROR_DEVICE_RESET](https://docs.microsoft.com/windows/desktop/direct3ddxgi/dxgi-error).

## <a name="see-also"></a>См. также статью

* Предыдущая статья: [Привязка модели](bind-a-model.md)

[!INCLUDE [help](../includes/get-help.md)]
