---
author: QuinnRadich
title: Использование опыта работы с Windows из классического приложения (C++)
description: Узнайте, как подготавливать и использовать навыки работы с Windows в настольном приложении (не UWP).
ms.author: lobourre
ms.date: 8/26/2019
ms.topic: article
keywords: Windows 10, Windows AI, навыки работы с концепцией Windows, Настольный компьютер
ms.localizationpriority: medium
ms.openlocfilehash: a40d4ad18dda21ea73f9bf0e8e9144180fb5aee3
ms.sourcegitcommit: 900b428a26955f6366f3c03128dc225f52ffd3bc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/28/2019
ms.locfileid: "70065730"
---
# <a name="tutorial-create-a-vision-skill-desktop-application-c"></a>Учебник. Создание классического приложения для навыков работыC++с видением ()

> [!NOTE]
> Некоторые сведения относятся к предварительной версии продукта, в которую перед коммерческим выпуском могут быть внесены существенные изменения. Майкрософт не дает никаких гарантий, явных или подразумеваемых, в отношении предоставленной здесь информации.

> [!NOTE]
> Если вы создаете навык для концепции Windows, который должен использоваться в приложении, не относящемся к UWP (т. е. в классическом приложении Win32 или .NET Core), необходимо убедиться в том, что навык осведомлен о среде выполнения.

В этом учебнике вы научитесь:

- Измените пакет навыков, чтобы он знал о среде выполнения. В частности, навыку необходимо знать, работает ли он в контейнере приложения UWP.
- Укажите файлы манифеста и заголовка, необходимые для работы навыка в приложении, не относящемся к UWP.

---

## <a name="prerequisites"></a>Предварительные требования

- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/) (или Visual Studio 2017, версия 15.7.4 или более поздняя)
- Windows 10 версии 1809 или более поздней.
- [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk), версия 1809 или более поздняя

---

1. Убедитесь в том, что в среде выполнения для навыка учитывается UWP-Container:

- Обнаружение среды выполнения контейнера приложения UWP в рамках навыка:

Пример кода:

```cpp
// helper function to determine if the skill is being called from a UWP app container or not.
bool IsUWPContainer()
{
    HANDLE hProcessToken = INVALID_HANDLE_VALUE;
    HANDLE hProcess;
    hProcess = GetCurrentProcess();

    if (!OpenProcessToken(hProcess, TOKEN_QUERY, &hProcessToken))
    {
        throw winrt::hresult(HRESULT_FROM_WIN32(GetLastError()));
    }

    BOOL bIsAppContainer = false;
    DWORD dwLength;

    if (!GetTokenInformation(hProcessToken, TokenIsAppContainer, &bIsAppContainer, sizeof(bIsAppContainer), &dwLength))
    {
        // if we were denied token information we are definitely not in an app container.
        bIsAppContainer = false;
    }

    return bIsAppContainer;
}
```

- Если навык вызывается из контейнера приложения UWP или из упакованного контейнера UWP, доступ к файлу ограничен путями пакета приложения. Таким образом, все файлы или зависимости модели должны быть упакованы и загружены из путей к контейнеру.

Однако если навык вызывается из среды, отличной от контейнера, такой как Win32 C++ или .NET Core 3,0, то среда контейнера приложения UWP недоступна. Вместо этого большая часть доступа к диску будет доступна в соответствии с разрешениями классического приложения, использующего этот навык. Поэтому рекомендуется размещать файлы моделей и другие ресурсы в том же расположении, где находится библиотека навыков (*DLL*).

Пример кода:

```csharp
winrt::Windows::Storage::StorageFile modelFile = nullptr;

// if running from within a UWP app container, access resources using a URI relative to its path
if (IsUWPContainer())
{
    auto modelFile = Windows::Storage::StorageFile::GetFileFromApplicationUriAsync(Windows::Foundation::Uri(L"ms-appx:///Contoso.FaceSentimentAnalyzer/" + WINML_MODEL_FILENAME)).get();
}
// If running from a regular app process such as a Desktop app, access resources using the full system path
else
{
    WCHAR DllPath[MAX_PATH] = { 0 };
    GetModuleFileName(NULL, DllPath, _countof(DllPath));
    // Get path of current DLL
    auto file = Windows::Storage::StorageFile::GetFileFromPathAsync(DllPath).get();
    // Use the path of the parent directory to access other resources bundled with the DLL
    auto folder = file.GetParentAsync().get();
    modelFile = folder.GetFileAsync(WINML_MODEL_FILENAME).get();
```

2. Предоставьте файлы заголовков (. h) и *manifest* -файлы (пакет в NuGet) для простоты использования разработчиками приложений Win32 или .NET Core 3,0.

    2.1. Создание файлов заголовков ( *. h*) для C++ приложений.
В Visual Studio выберите свой проект. Затем:
    - Компонент C++ WinRT: Выберите проект-> Свойства — > файле выходных данных > MIDL->
    - Компонент C# WinRT: Поскольку нет возможности создавать файлы заголовков в C# проекте, необходимо сначала преобразовать созданные файлы метаданных ( *. winmd*) в файлы определения интерфейса (*IDL*), а затем преобразовать их в файлы заголовков ( *. h*). Это можно сделать с помощью командной строки разработчика Visual Studio:
      - Создание *IDL* -файла из файла *WinMD* с помощью [winmdidl. exe](https://docs.microsoft.com/cpp/cppcx/wrl/use-winmdidl-and-midlrt-to-create-h-files-from-windows-metadata?view=vs-2019)
      ```
      > winmdidl <filename.winmd> /utf8 /metadata_dir:<path-to-sdk-unionmetadata> /metadata_dir: <path-to-additional-winmds> /outdir:<output-path>
      ```
      - Создание *h* из *IDL* -файла с помощью [midlrt. exe](https://docs.microsoft.com/windows/win32/midl/midlrt-and-windows-runtime-components)
      ```
      > midlrt <filename.idl> /metadata_dir  <path-to-sdk-unionmetadata> /ns_prefix
      ```

    2.2. Создайте файл манифеста, чтобы обеспечить параллельную регистрацию навыков в приложениях без упаковки. В этом файле перечислены классы среды выполнения, определенные в компоненте WinRT, чтобы их можно было зарегистрировать и загрузить во время выполнения. Мы предоставляем [удобные скрипты](https://github.com/microsoft/WindowsVisionSkillsPreview/blob/master/samples/Scripts/genSxSManifest.ps1) , которые могут создать манифест путем анализа файлов определения интерфейса (*IDL*). Чтобы получить комплексную демонстрацию, ознакомьтесь с [примерами навыков](https://github.com/microsoft/WindowsVisionSkillsPreview/tree/master/samples/SentimentAnalyzerCustomSkill) .


    2.2.1. Формат манифеста параллельно:

```xml
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
    <assembly xmlns="urn:schemas-microsoft-com:asm.v3" manifestVersion="1.0">
        <assemblyIdentity
        type="win32"
        name="manifest Identityname, preferably same as dll name without extension and same as filename of this manifest"
        version="1.0.0.0"/>

        <file name="dll name of the skill component, including extension">

            <activatableClass
            name="runtimeclassname1"
            threadingModel="both"
            xmlns="urn:schemas-microsoft-com:winrt.v1" />

            <activatableClass
            name="runtimeclassname2"
            threadingModel="both"
            xmlns="urn:schemas-microsoft-com:winrt.v1" />

        </file>
    </assembly>
```

2.3. В приложении добавьте файл манифеста, в котором упоминается только что созданный манифест навыков.

2.3.1. Параметры проекта приложения для создания файла манифеста на стороне приложения и формат файла манифеста на стороне:
<div style="text-align:center" markdown="1">

![Схема манифеста для загрузки компонентов WinRT в SxS](../images/vision-skills-manifest.png)

</div>

```xml

<?xml version="1.0" encoding="utf-8"?>
<assembly manifestVersion="1.0" xmlns="urn:schemas-microsoft-com:asm.v1">
    <assemblyIdentity version="1.0.0.0" name="MyApplication.app"/>
    <dependency>
        <dependentAssembly>
            <assemblyIdentity
                type="win32"
                name="Microsoft.AI.Skills.SkillInterfacePreview"
                version="1.0.0.0"/>
        </dependentAssembly>
    </dependency>

    <dependency>
        <dependentAssembly>
            <assemblyIdentity
                type="win32"
                name="<name-of-manifest-file-without-extension>"
                version="1.0.0.0"/>
        </dependentAssembly>
    </dependency>

</assembly>
```

## <a name="next-steps"></a>Следующие шаги

Радостных, теперь ваш навык готов к использованию в классическом приложении. Поиграйте с примерами навыков на [GitHub](https://github.com/microsoft/WindowsVisionSkillsPreview/tree/master/samples) и расширяйте их по своему усмотрению.

[!INCLUDE [help](../includes/get-help-vision.md)]
