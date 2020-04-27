---
author: rosanevallim
title: Часто задаваемые вопросы
description: На этой странице собраны ответы на самые популярные вопросы сообщества.
ms.author: rovalli
ms.date: 7/2/2019
ms.topic: article
keywords: windows 10, windows ai, windows ml, winml, windows machine learning
ms.localizationpriority: medium
ms.openlocfilehash: 0067de7380560337feb06186ff28ba431b167c93
ms.sourcegitcommit: 2139506ff12b7205283288c4bbac866ddfa812f3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/24/2020
ms.locfileid: "67523621"
---
# <a name="faq-frequently-asked-questions"></a>Часто задаваемые вопросы

На этой странице собраны ответы на самые популярные вопросы сообщества.

## <a name="how-do-i-know-if-the-onnx-model-i-have-will-run-with-windows-ml"></a>Как узнать, будет ли моя модель ONNX работать с Windows ML?

Чтобы проверить, будет ли модель запускаться в Windows ML, проще всего воспользоваться средством [WinML Model Runner](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Tools/WinMLRunner). Также вы можете изучить статью [Версии ONNX и сборки Windows](onnx-versions.md), где собраны сведения обо всех поддерживаемых версиях ONNX для конкретных выпусков Windows.

## <a name="how-do-i-convert-a-model-of-a-different-format-to-onnx"></a>Как преобразовать модель другого формата в ONNX?

Для преобразования моделей некоторых популярных форматов, например Apple CoreML и scikit-learn, в формат ONNX, можно использовать [WinMLTools](convert-model-winmltools.md).

## <a name="i-am-getting-errors-when-trying-to-export-andor-convert-my-model-to-onnx-that-say-my-model-has-unsupported-operators-what-should-i-do"></a>При попытке экспорта и (или) преобразования модели в ONNX возникают ошибки с сообщением о том, что модель содержит "неподдерживаемые операторы". Что с этим делать?

Некоторые операторы исходных платформ машинного обучения не поддерживаются некоторыми версиями ONNX. Мы рекомендуем вам прежде всего проверить [поддерживаемые версии ONNX для целевой сборки Windows](onnx-versions.md) и, если это возможно, преобразовать модель в максимальную поддерживаемую версию. Более поздние версии ONNX поддерживают более широкий набор операторов по сравнению с предыдущими версиями.

Если проблемы сохранятся, попробуйте связаться со специалистами по обработке и анализу данных, чтобы совместно с ними избавиться от неподдерживаемых операторов. Для достижения этого мы рекомендуем изменить архитектуру модели на исходной платформе и повторно конвертировать или экспортировать модель в целевую версию ONNX. Обратите внимание, что повторно обучать модель пока не нужно. Сначала попробуйте преобразовать архитектуру, а к обучению можно перейти уже после успешной конвертации.

## <a name="why-cant-i-load-a-model"></a>Почему не удается загрузить модель?

Проблемы с загрузкой модели могут возникать по нескольким причинам, из которых при разработке на платформе UWP чаще всего встречается ограничение на доступ к файлам. По умолчанию приложения UWP могут обращаться только к определенным частям файловой системы, а для доступа к другим расположениям им нужны разрешения пользователя или дополнительные компоненты. Дополнительные сведения см. в статье [Разрешения на доступ к файлам](https://docs.microsoft.com/windows/uwp/files/file-access-permissions).

## <a name="which-version-of-winmltools-should-i-use"></a>Какую версию WinMLTools нужно использовать?

Мы всегда рекомендуем скачивать и устанавливать последнюю версию пакета **winmltools**. Так вы сможете создавать модели ONNX, предназначенные для последних версий Windows.

## <a name="can-i-use-onnxmltools-instead-of-winmltools"></a>Можно ли использовать onnxmltools вместо winmltools?

Да, можно, но нужно убедиться в наличии правильной версии [onnxmltools](https://github.com/onnx/onnxmltools), которая позволяет нацеливаться на ONNX версии 1.2.2. Это минимальная версия ONNX, поддерживаемая в Windows ML. Если вы не уверены в выборе версии для установки, лучше используйте последнюю версию **winmltools**. Это гарантирует возможность нацеливания на поддерживаемую в Windows версию ONNX.

## <a name="which-version-of-visual-studio-should-i-use-in-order-to-get-automatic-code-generation-mlgen"></a>Какую версию Visual Studio следует использовать для автоматического создания кода (mlgen)?

Минимальная рекомендуемая версия [Visual Studio](https://visualstudio.microsoft.com/vs/) с поддержкой [mlgen](mlgen.md) — это версия 15.8.7. В Windows 10 версии 1903 и более поздних средство **mlgen** уже не входит в состав пакета SDK, поэтому вам придется отдельно скачать и установить его в качестве расширения. Существуют отдельные версии для [Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=WinML.mlgen) и [Visual Studio 2019](https://marketplace.visualstudio.com/items?itemName=WinML.mlgenv2).

## <a name="i-get-an-error-message-when-trying-to-run-mlgen-and-no-code-is-generated-what-could-possibly-be-happening"></a>При попытке запустить mlgen появляется сообщение об ошибке, и код не создается. С чем это может быть связано?

Вот две наиболее распространенные ошибки, которые возникают при попытке выполнить mlgen.

* **Required attribute 'consumed_inputs' is missing** (Отсутствует необходимый атрибут "consumed_inputs"). Если вы увидите такое сообщение об ошибке, вы скорее всего пытаетесь выполнить модель ONNX версии 1.2 с пакетом SDK для Windows 10 версии старше, чем 17763. Мы рекомендуем проверить версию пакета SDK и обновить его до версии 17763 или более поздней.
* **Type Error: Type (map(string,tensor(float))) of output arg (loss) of node (ZipMap) does not match the expected type...** (Ошибка типа. Тип (map(string,tensor(float))) выходного аргумента (loss) узла (ZipMap) не соответствует ожидаемому...). Если вы увидите такую ошибку, ваша модель ONNX скорее всего имеет более старую версию, чем поддерживаемая в WinML сборки 17763 и более поздних. Мы рекомендуем обновить пакет преобразователя до последней доступной версии и повторно преобразовать модель в ONNX версии 1.2.

## <a name="what-does-winml-run-on-by-default"></a>Где выполняется WinML по умолчанию?

Если вы не укажете устройство для выполнения с помощью параметра [LearningModelDeviceKind](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodeldevicekind) или указали в нем значение **LearningModelDeviceKind.Default**, устройство для оценки модели будет автоматически выбрано системой. Чаще всего используется устройство ЦП. Чтобы выполнить WinML на GPU, укажите при создании [LearningModelDevice](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodeldevice) одно из следующих значений:

* **LearningModelDeviceKind.DirectX**;
* **LearningModelDeviceKind.DirectXHighPerformance**;
* **LearningModelDeviceKind.DirectXMinPower**.

[!INCLUDE [help](../includes/get-help.md)]
