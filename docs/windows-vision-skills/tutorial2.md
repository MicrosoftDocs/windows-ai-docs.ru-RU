---
title: Использование навыка компьютерного зрения Windows из классического приложения на C++
description: Узнайте о том, как подготавливать и использовать навыки компьютерного зрения Windows в классическом приложении (не UWP).
ms.author: lobourre
ms.date: 8/26/2019
ms.topic: article
keywords: windows 10, windows ai, windows vision skills, desktop
ms.localizationpriority: medium
ms.openlocfilehash: 0a5b8e1068bceaa805667d5d4c88495d80c290b7
ms.sourcegitcommit: 2139506ff12b7205283288c4bbac866ddfa812f3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/24/2020
ms.locfileid: "70156170"
---
# <a name="tutorial-create-a-vision-skill-desktop-application-c"></a>Руководство: Создание классического приложения с навыком компьютерного зрения (C++)

> [!NOTE]
> Некоторые сведения относятся к предварительной версии продукта, в которую перед коммерческим выпуском могут быть внесены существенные изменения. Майкрософт не дает никаких гарантий, явных или подразумеваемых, в отношении предоставленной здесь информации.

> [!NOTE]
> Если вы создаете навык компьютерного зрения Windows, который будет использоваться не в приложении UWP (т. е. в классическом приложении для Win32 или .NET Core), вам нужно передать в этот навык сведения о среде выполнения.

В этом руководстве описано, как выполнять следующие операции:

- Изменение пакета навыков для предоставления сведений о среде выполнения. В частности, навыку нужно передать сведения о том, выполняется ли он в контейнере приложения UWP.
- Предоставить файлы манифеста и заголовка, которые потребуются для выполнения навыка на платформе, отличающейся от UWP.

---

## <a name="prerequisites"></a>Предварительные условия

- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/) (или Visual Studio 2017 версии 15.7.4 и выше);
- Windows 10 версии 1809 или более поздней.
- [пакет SDK для Windows 10](https://developer.microsoft.com/windows/downloads/windows-10-sdk) версии 1809 и выше.

---

1. Убедитесь в том, что навык получает сведения о контейнере UWP в среде выполнения:

- Обнаружение контейнера приложения UWP в среде выполнения из контекста навыка:

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

- Если навык вызывается из контейнера приложения UWP или упакованного контейнера UWP, доступ к файлам ограничивается путями установки пакета приложения. Это означает, что все файлы и зависимости модели нужно упаковать и загружать из каталогов, доступных контейнеру.

Если же навык вызывается из среды без использования контейнеров, например из классического приложения Win32 C++ или .NET Core 3.0, ему недоступна среда контейнера приложения UWP. Но зато навыку доступно почти все пространство на диске с учетом разрешений для того приложения, из которого вызван этот навык. Поэтому мы рекомендуем размещать файлы моделей и другие ресурсы в том же расположении, что и библиотека навыка (*DLL*-файл).

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

2. Предоставьте (включите в пакет NuGet) файлы заголовков (.h) и манифестов ( *.manifest*), чтобы разработчикам приложений Win32 или .Net Core 3.0 было проще работать с ними.

    2.1. Создание файлов заголовков ( *.h*) для приложений C++.
Выберите нужный проект в Visual Studio. Затем:
    - Для компонента C++/WinRT: щелкните "Проект" -> "Свойства" -> "MIDL" -> выходные данные -> "Файл заголовка".
    - Для компонента C#/WinRT: так как вы не можете создавать файлы заголовков в проекте C#, необходимо сначала преобразовать созданные файлы метаданных ( *.winmd*) в файлы определения интерфейса ( *.idl*), а затем преобразовать эти файлы *.idl* в файлы заголовков ( *.h*). Это можно сделать из командной строки разработчика Visual Studio:
      - для создания *.idl* из *.winmd* выполните [winmdidl.exe](https://docs.microsoft.com/cpp/cppcx/wrl/use-winmdidl-and-midlrt-to-create-h-files-from-windows-metadata?view=vs-2019);
      ```
      > winmdidl <filename.winmd> /utf8 /metadata_dir:<path-to-sdk-unionmetadata> /metadata_dir: <path-to-additional-winmds> /outdir:<output-path>
      ```
      - для создания *.h* из *.idl* выполните [midlrt.exe](https://docs.microsoft.com/windows/win32/midl/midlrt-and-windows-runtime-components).
      ```
      > midlrt <filename.idl> /metadata_dir  <path-to-sdk-unionmetadata> /ns_prefix
      ```

    2.2. Создайте файл манифеста, чтобы включить параллельную регистрацию навыков в приложениях без пакетов. В этом файле перечислены все классы среды выполнения, которые определены в компоненте WinRT. Это позволяет зарегистрировать и загрузить их во время выполнения. Мы предоставляем [удобные скрипты](https://github.com/microsoft/WindowsVisionSkillsPreview/blob/master/samples/Scripts/genSxSManifest.ps1), которые могут создать манифест путем анализа файлов определения интерфейса (*IDL*-файлов). Весь этот процесс представлен [примерах навыков](https://github.com/microsoft/WindowsVisionSkillsPreview/tree/master/samples/SentimentAnalyzerCustomSkill).


    2.2.1. Формат параллельного манифеста:

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

2.3. Добавьте в приложение файл манифеста, в котором упоминается только что созданный манифест навыка.

2.3.1. Параметры проекта приложения для создания файла манифеста на стороне приложения и формат стороннего файла манифеста:
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

## <a name="next-steps"></a>Дальнейшие действия

Итак, ваш навык готов к использованию в классическом приложении. Потренируйтесь также на других примерах навыков с [GitHub](https://github.com/microsoft/WindowsVisionSkillsPreview/tree/master/samples) и дополните их на свой вкус!

[!INCLUDE [help](../includes/get-help-vision.md)]
