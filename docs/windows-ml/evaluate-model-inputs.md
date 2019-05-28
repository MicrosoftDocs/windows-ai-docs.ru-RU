---
author: eliotcowley
title: Оценка входных данных модели
description: Узнайте, как выполнить оценку входные данные модели, чтобы получить прогнозы.
ms.author: elcowle
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10, windows ai, windows ml, winml, windows machine learning
ms.localizationpriority: medium
ms.openlocfilehash: a06a4b55745eaf9c1a0035cfa9249b757c525bf7
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66181246"
---
# <a name="evaluate-the-model-inputs"></a>Оценка входных данных модели

После значения привязки к входные и выходные данные модели, все готово для оценки входные данные модели и получать ее прогнозы.

Для запуска модели, вызвать любую **Evaluate*** методы на вашей [LearningModelSession](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodelsession). Можно использовать [LearningModelEvaluationResult](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodelevaluationresult) для просмотра выходных данных функции.

## <a name="example"></a>Пример

В следующем примере мы выполнить оценку сеанса, передавая привязки и корреляции уникальный идентификатор. Затем мы проанализировать выходные данные, как список вероятностей, сопоставить его список меток для выполнения различных задач в нашей модели могли распознавать и записывать результаты на консоль:

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

Если устройство становится недоступным, или если вы хотите использовать другое устройство, необходимо закрыть сеанс и создать новый сеанс.

В некоторых случаях графических устройств может потребоваться быть выгружен или перезагружен, как описано в [Документация DirectX](https://docs.microsoft.com/windows/uwp/gaming/handling-device-lost-scenarios).

При использовании машинного Обучения Windows, необходимо обнаружить этот случай и закрыть сеанс. Чтобы выполнить восстановление после удаления устройства или повторной инициализации, вы создадите новый сеанс, который запускает логику выбора устройств для повторного запуска.

— Наиболее распространенный случай, где вы увидите эту ошибку во время [LearningModelSession.Evaluate](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodelsession.evaluate). В случае удаления устройства или сбросе [LearningModelEvaluationResult.ErrorStatus](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodelevaluationresult.errorstatus) будет [DXGI_ERROR_DEVICE_REMOVED](https://docs.microsoft.com/windows/desktop/direct3ddxgi/dxgi-error) или [DXGI_ERROR_DEVICE_RESET](https://docs.microsoft.com/windows/desktop/direct3ddxgi/dxgi-error).

## <a name="see-also"></a>См. также

* Предыдущих: [Привязка модели](bind-a-model.md)

[!INCLUDE [help](../includes/get-help.md)]