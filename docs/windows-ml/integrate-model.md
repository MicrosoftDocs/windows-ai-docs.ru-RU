---
author: walrusmcd
title: Интеграция модели в приложение
description: Сведения о том, как интегрировать обученные модели машинного обучения в приложения Windows с помощью Windows ML.
ms.author: paulm
ms.date: 5/10/2019
ms.topic: article
keywords: windows 10, windows ai, windows ml, winml, windows machine learning
ms.localizationpriority: medium
ms.openlocfilehash: af2af3fd6af4353171def886625271df97a55f35
ms.sourcegitcommit: 2139506ff12b7205283288c4bbac866ddfa812f3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/24/2020
ms.locfileid: "66181936"
---
# <a name="integrate-a-model-into-your-app-with-windows-ml"></a>Интеграция модели в приложения с использованием Windows ML

В этом руководстве описывается, как использовать API-интерфейсы Windows ML для интеграции модели в приложение Windows. Если вы предпочитаете использовать автоматический генератор кода Windows ML, ознакомьтесь с документацией по [mlgen](mlgen.md).

> **Важные API**: [Windows.AI.MachineLearning](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning)

Мы рассмотрим базовые стандартные блоки Windows ML:

* модели;
* сеансы;
* Устройства
* Привязки

С их помощью вы загрузите, привяжете и оцените модели в Windows ML.

Мы также рекомендуем ознакомиться с [примерами приложений на сайте GitHub](https://github.com/Microsoft/Windows-Machine-Learning/tree/master), где представлены полные примеры кода для Windows ML.

Следующее видео содержит краткую демонстрацию применения этих API.

<br/>

> [!VIDEO https://www.youtube.com/embed/Nc2wstifyoE]

## <a name="using-winml-apis-in-c"></a>Использование API-интерфейсов WinML в C++

Хотя API-интерфейсы WinML доступны для C++/CX и C++/WinRT мы рекомендуем использовать версию для C++/WinRT, так как она поддерживает более естественную разработку кода на C++ и позволяет более спокойно двигаться вперед. Приведенные ниже инструкции подходят под конкретные ситуации применения API-интерфейсов C++/WinRT.

* Если вы создаете новое приложение C++, см. руководство [ Создание классического приложения (C++) для Windows ML](https://docs.microsoft.com/windows/ai/get-started-desktop) и выполните из него шаги по **загрузке модели**.
* Если у вас есть приложение C++ (которое еще не настроено для C++/WinRT), выполните следующие действия по настройке приложения для C++/WinRT.
    1. Убедитесь, что у вас установлена последняя версия [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/) (любого выпуска).
    2. Убедитесь, что у вас есть [пакет SDK для Windows 10](https://developer.microsoft.com/windows/downloads/windows-10-sdk) версии 1803 или более поздней.
    3. Скачайте и установите [расширение C++/WinRT для Visual Studio (VSIX)](https://aka.ms/cppwinrt/vsix) из [Visual Studio Marketplace](https://marketplace.visualstudio.com/).
    4. Добавьте свойство `<CppWinRTEnabled>true</CppWinRTEnabled>` в VCXPROJ-файл проекта.
        ```xml
        <Project ...>
            <PropertyGroup Label="Globals">
                <CppWinRTEnabled>true</CppWinRTEnabled>
        ...
        ```
    5. Для C++/WinRT требуются некоторые компоненты стандарта C++17, поэтому в свойствах проекта нужно указать **C/C++ > Язык > Стандарт языка C++ > Стандарт ISO C++17 (/std:c++17)** .
    6. Установите **Режим совместимости: Да (/permissive-)** в свойствах проекта.
    7. Еще одно важное свойство для проекта: **C/C++ > Общие > Обрабатывать предупреждения как ошибки**. Задайте для него значение **Да (/WX)** или **Нет (/WX-)** по своему желанию. Иногда исходные файлы, созданные инструментом **cppwinrt.exe**, выдают предупреждения до тех пор, пока вы не добавите в них свою реализацию.
    8. VSIX также поддерживает визуализацию встроенной отладки Visual Studio (natvis) проецированных типов C++/ WinRT, что обеспечивает возможности, аналогичные отладке на C#. Natvis автоматически используется для сборок отладки. Вы можете выбрать сборки выпуска, указав символ **WINRT_NATVIS**.
    9. Теперь проект настроен для работы с C++/WinRT. Дополнительные сведения см. в документации по [C++/WinRT](https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/).

## <a name="related-topics"></a>Связанные темы

* [mlgen](mlgen.md)
* [Производительность и память](performance-memory.md)
* [Справочник по API](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning)
* [Примеры кода](https://github.com/Microsoft/Windows-Machine-Learning/tree/master)

[!INCLUDE [help](../includes/get-help.md)]
