---
author: rosanevallim
title: Автоматическое создание кода с помощью mlgen
description: Mlgen генератор кода Windows ML создает интерфейс (C#, C++/WinRT, и C++/CX), позволяющий легко загрузить, привязки и оценить модель в приложении.
ms.author: rovalli
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10, windows ai, windows ml, winml, windows machine learning
ms.localizationpriority: medium
ms.openlocfilehash: 7658b35a6bb19133380cf021a47d9c35ffc62a3b
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66181896"
---
# <a name="automatic-code-generation-with-mlgen"></a>Автоматическое создание кода с помощью mlgen

<br/>

> [!VIDEO https://www.youtube.com/embed/8MCDSlm326U]

<br/>

Генератор кода Windows машинного обучения **mlgen** создает интерфейс (C#, [ C++/WinRT](https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/), и C++/CX) с помощью программы-оболочки классов этого вызова [API машинного Обучения Windows](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning) для вас, что позволяет легко загрузить, привязки и оценить модель в проекте.

**mlgen** предоставляется в качестве [Visual Studio](https://visualstudio.microsoft.com/downloads/) расширения, позволяющие разработчикам создавать приложения WinML в Visual STUDIO 2017 или более поздней версии.

В Windows 10, версия 1903 и более поздние версии, **mlgen** больше не входит в пакет SDK для Windows 10, поэтому необходимо загрузить и установить расширение. Имеется один для [Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=WinML.mlgen) и один для [Visual Studio 2019](https://marketplace.visualstudio.com/items?itemName=WinML.mlgenv2).

При наличии **mlgen** установлен, внутри проекта Visual Studio, добавьте ONNX файл проекта **активы** папки и VS будут создавать классы-оболочки Windows машинного Обучения в новом файле интерфейс. Эти классы и методы можно использовать для интеграции модели в приложение. См. в разделе [руководства: Создание приложения универсальной платформы Windows машины обучения Windows (C#)](get-started-uwp.md) учебник, интегрирует модели с помощью этого метода.

[!INCLUDE [help](../includes/get-help.md)]
