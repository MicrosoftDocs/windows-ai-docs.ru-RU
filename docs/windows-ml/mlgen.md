---
author: rosanevallim
title: Автоматическое создание кода с помощью mlgen
description: Генератор кода mlgen для Windows ML создает интерфейс (для C#, C++/WinRT и C++/CX), который позволяет легко загружать модель в приложение, привязывать и оценивать ее.
ms.author: rovalli
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10, windows ai, windows ml, winml, windows machine learning
ms.localizationpriority: medium
ms.openlocfilehash: 7658b35a6bb19133380cf021a47d9c35ffc62a3b
ms.sourcegitcommit: 2139506ff12b7205283288c4bbac866ddfa812f3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/24/2020
ms.locfileid: "66181896"
---
# <a name="automatic-code-generation-with-mlgen"></a>Автоматическое создание кода с помощью mlgen

<br/>

> [!VIDEO https://www.youtube.com/embed/8MCDSlm326U]

<br/>

Генератор кода **mlgen** для Windows Machine Learning создает интерфейс (для C#, [C++/WinRT](https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/) и C++/CX) с классами-оболочками для вызова [API Windows ML](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning), который позволяет легко загружать, привязывать и оценивать модель в проекте.

Средство **mlgen** поставляется в формате расширения [Visual Studio](https://visualstudio.microsoft.com/downloads/) для создания приложений WinML в Visual Studio 2017 или более поздней версии.

В Windows 10 версии 1903 и более поздних средство **mlgen** больше не входит в состав пакета SDK для Windows 10, поэтому вам придется отдельно скачать и установить его. Существуют отдельные версии для [Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=WinML.mlgen) и [Visual Studio 2019](https://marketplace.visualstudio.com/items?itemName=WinML.mlgenv2).

Завершив установку **mlgen**, добавьте ONNX-файл внутри проекта Visual Studio в папку **Assets**, и Visual Studio автоматически создаст классы-оболочки для Windows ML в файле нового интерфейса. Эти классы и методы помогут вам интегрировать модель в приложение. В руководстве [ Создание приложения UWP (C#) для Windows Machine Learning](get-started-uwp.md) вы найдете инструкции по интеграции модели с использованием этого метода.

[!INCLUDE [help](../includes/get-help.md)]
