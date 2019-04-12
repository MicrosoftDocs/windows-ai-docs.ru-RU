---
author: walrusmcd
title: Интеграция модели в приложение
description: Узнайте, как с помощью машинного Обучения Windows интегрировать обученных моделей машинного обучения в приложения Windows.
ms.author: paulm
ms.date: 2/15/2019
ms.topic: article
keywords: Windows 10, windows искусственного интеллекта, машинного обучения windows, winml, windows машинное обучение
ms.localizationpriority: medium
ms.openlocfilehash: e9a09d798afe163be399b50d31bc4a8a2e85b96a
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2019
ms.locfileid: "59475021"
---
# <a name="integrate-a-model-into-your-app-with-windows-ml"></a>Интеграция модели в приложения с использованием Windows ML

В этом руководстве мы обсудим, как использовать API-интерфейсы машинного Обучения Windows для интеграции модели в ваше приложение Windows. Кроме того, если вы хотите использовать генератор кода для машинного Обучения Windows, см. статью [mlgen](mlgen.md).

> **Важные API**: [Windows.AI.MachineLearning](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning)

Здесь будут предоставлены основные стандартные блоки машинного Обучения Windows, которые являются:

* Модели
* Сессии
* Устройства
* Привязки

Вы используете их для загрузки, привязки и оценки моделей с машинным Обучением Windows.

Кроме того, рекомендуется рассмотреть наши [примеры приложений на сайте GitHub](https://github.com/Microsoft/Windows-Machine-Learning/tree/master) примеры кода Windows ML end-to-end.

В следующем видео показано эти API-интерфейсы в действии в короткую демонстрацию.

<br/>

> [!VIDEO https://www.youtube.com/embed/Nc2wstifyoE]

## <a name="using-winml-apis-in-c"></a>С помощью интерфейсов API WinML вC++

Хотя в состав сред API WinML C++/CX и C++/WinRT, мы рекомендуем использовать C++/WinRT версии, так как он позволяет более естественным C++ написание кода и является, где будет фокусироваться большая часть усилий по разработке в дальнейшем. Можно выполните приведенные ниже инструкции, которые относятся к конкретной ситуации для использования C++API-интерфейсы WinRT:

* Если вы создаете новый C++ приложения, см. в разделе [руководства: Создание приложения рабочем столе Windows компьютера обучения (C++)](https://docs.microsoft.com/windows/ai/get-started-desktop) и следуйте инструкциям до **загрузки модели**.
* Если у вас есть C++ приложения (который еще не установлено для C++/WinRT), выполните следующие действия, чтобы настроить приложение для C++/WinRT:
    1. Убедитесь, что у вас есть последняя версия [Visual Studio 2017](https://visualstudio.microsoft.com/downloads/) установлен (любой выпуск).
    2. Убедитесь, что у вас есть [пакета SDK для Windows 10](https://developer.microsoft.com/windows/downloads/windows-10-sdk), 1803 или более поздней версии.
    3. Скачайте и установите [ C++WinRT Visual Studio Extension (VSIX)](https://aka.ms/cppwinrt/vsix) из [Visual Studio Marketplace](https://marketplace.visualstudio.com/).
    4. Добавление `<CppWinRTEnabled>true</CppWinRTEnabled>` свойства проекта VCXPROJ-файл:
        ```xml
        <Project ...>
            <PropertyGroup Label="Globals">
                <CppWinRTEnabled>true</CppWinRTEnabled>
        ...
        ```
    5. C++/ WinRT требуются возможности в стандарте C ++ 17, поэтому в свойствах проекта, задайте **C /C++ > язык > C++ стандартом языка > стандарт ISO C ++ 17 (/ std: c ++ 17)**.
    6. Задайте **режим совместимости: Да (/ permissive-)** в свойствах проекта.
    7. — Для другого свойства проекта, которые следует учитывать **C /C++ > Общие > обрабатывать предупреждения как ошибки**. Задайте значение **Да (/WX)** или **нет (/ WX-)** для стиля. В некоторых случаях исходные файлы, созданные **cppwinrt.exe** средство формировать предупреждения, пока вы не добавите реализации к ним.
    8. VSIX также дает визуализации отладки машинного кода в Visual Studio (natvis) из C++/WinRT проецировать типы, используйте стараемся аналогичную C# отладки. Natvis используется автоматически для сборок отладки. Вы можете выбрать его сборок выпуска, определив символ **WINRT_NATVIS**.
    9. Проекта теперь должны быть установлены для C++/WinRT. См. в разделе [ C++/WinRT](https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/) Дополнительные сведения.

## <a name="related-topics"></a>См. также

* [mlgen](mlgen.md)
* [Производительности и использования памяти](performance-memory.md)
* [Справочник по API](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning)
* [Примеры кода](https://github.com/Microsoft/Windows-Machine-Learning/tree/master)

[!INCLUDE [help](includes/get-help.md)]
