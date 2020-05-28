---
author: QuinnRadich
title: Перенос существующего приложения WinML в пакет NuGet
description: Узнайте, как перевести существующее классическое приложение WinML на использование распространяемого пакета NuGet.
ms.author: quradic
ms.date: 5/19/2020
ms.topic: article
keywords: windows 10, ии windows, windows ml, winml, машинное обучение windows, NuGet
ms.localizationpriority: medium
ms.openlocfilehash: 56ab40ca13c5ca46d21ca4b6ea7bc207920ad440
ms.sourcegitcommit: f41fad7e6b6280bbbaf4157703f03fb7f23de676
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2020
ms.locfileid: "83632806"
---
# <a name="port-an-existing-winml-app-to-nuget-package-c"></a>Перенос существующего приложения WinML в пакет NuGet (C++) 

В этом руководстве описан перевод существующего классического приложения WinML на использование [распространяемого пакета NuGet](https://github.com/microsoft/Windows-Machine-Learning/tree/master/Samples/SqueezeNetObjectDetection/Desktop/cpp). 

## <a name="prerequisites"></a>Предварительные условия

* Приложение WinML. Если вы создаете новое приложение, см. это руководство: Создание классического приложения (C++) для Windows Machine Learning 
* Windows 8.1 или выше 
* Visual Studio 2019 (или Visual Studio 2017 версии 15.7.4 и выше)

## <a name="add-the-nuget-package-to-your-project"></a>Добавление пакета NuGet в проект

В проекте Visual Studio для существующего приложения перейдите в обозреватель решений и щелкните элемент **Управление пакетами NuGet** для решения. Выберите пакет NuGet `Microsoft.AI.MachineLearning`. Убедитесь, что вы добавляете пакет в требуемый проект, и нажмите кнопку **Установить**.

Затем снова выполните сборку решения. Набор средств C++/WinRT будет анализировать новые заголовки и метаданные из пакета NuGet `Microsoft.AI.MachineLearning`, чтобы избежать путаницы на следующем шаге.

## <a name="include-the-new-header"></a>Добавление нового заголовка

Для удобства добавьте управляющий флаг, который позволяет приложению переключаться между использованием стандартного решения Windows ML и пакета NuGet.

```c++
#ifdef USE_WINML_NUGET
#include “winrt/Microsoft.AI.MachineLearning.h” 
#endif
```

## <a name="change-the-namespace"></a>Изменение пространства имен

Затем разрешите `Windows::AI::Machinelearning` переключиться на пространство имен `Microsoft::AI::MachineLearning` с помощью управляющего флага. Если внести такое изменение, код будет автоматически использовать пакет NuGet, если это применимо.

```c++
#ifdef USE_WINML_NUGET 

Using namespace Microsoft::AI::MachineLearning 

#else 

Using namespace Windows::AI::MachineLearning 

#endif 
```

## <a name="change-the-preprocessor-definitions"></a>Изменение определений препроцессора

В окне **Обозреватель решений** щелкните проект правой кнопкой мыши и выберите элемент **Свойства**. В окне **Свойства** перейдите на страницу **Препроцессор**. Замените значение в поле **Определения препроцессора** на `USE_WINML_NUGET:_DEBUG`.

## <a name="build-and-run"></a>Сборка и запуск

Теперь приложение успешно использует пакет NuGet WinML.