---
author: eliotcowley
title: Создание классического приложения vision навыков (C++)
description: Сведения о создании Windows классического приложения (не UWP), использующий навыки концепции Windows.
ms.author: elcowle
ms.date: 4/25/2019
ms.topic: article
keywords: Windows 10, искусственный интеллект windows, windows визуального распознавания навыков, рабочего стола
ms.localizationpriority: medium
ms.openlocfilehash: d61417a200902979ed8cfa5d9f37ab5b1b078e15
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66179886"
---
# <a name="tutorial-create-a-vision-skill-desktop-application-c"></a>Учебник. Создание классического приложения vision навыков (C++)

> [!NOTE]
> Некоторая информация имеет отношение к предварительному выпуску продукта, который может быть значительно изменен перед коммерческим выпуском. Майкрософт не дает никаких гарантий, явных или подразумеваемых, в отношении предоставленной здесь информации.

> [!NOTE]
> Если вы создаете навыка, необходимо использовать в приложении не UWP, таких как классического приложения Win32 или .NET Core.
Вам потребуется изменить свои навыки, убедитесь, что навык учитывает среды.

В этом руководстве вы узнаете, как:

- Изменение пакета навыков будут учитывать контейнера.
- Укажите манифест и файлами заголовков.

---

## <a name="prerequisites"></a>Предварительные требования

- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/) (или Visual Studio 2017 версии 15.7.4 или более поздней версии)
- Windows 10, 1809 или более поздней версии
- [Пакет SDK для Windows 10](https://developer.microsoft.com/windows/downloads/windows-10-sdk), 1809 или более поздней версии

---

1. Убедитесь, что навык виду контейнер универсальной платформы Windows:

- Обнаружение среды контейнеров приложений из навыков:

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

- Если навыков вызывается из контейнера приложения универсальной платформы Windows или UWP упакованные контейнера доступ к файлам ограничивается пути пакета приложения. Таким образом любой файл модели или зависимости должны быть упаковываются и загружаются из путей к контейнеру.
Тем не менее если навык вызывается из среде не являющиеся контейнерами, например регулярных cpp или .net core настольном приложении win32, функция среды контейнеров приложений будет недоступна. Вместо этого большинство обращений к диску, будут доступны в соответствии с разрешениями рабочего стола приложения, которое использует свои навыки. Может быть хорошей практикой для сохранения файлов модели и другие ресурсы в одном расположении в расположение dll навыков

Пример кода:

```csharp
winrt::Windows::Storage::StorageFile modelFile = nullptr;
if (IsUWPContainer())
{
    auto modelFile = Windows::Storage::StorageFile::GetFileFromApplicationUriAsync(Windows::Foundation::Uri(L"ms-appx:///Contoso.FaceSentimentAnalyzer/" + WINML_MODEL_FILENAME)).get();
}
else
{
    WCHAR DllPath[MAX_PATH] = { 0 };
    GetModuleFileName(NULL, DllPath, _countof(DllPath));
    auto file = Windows::Storage::StorageFile::GetFileFromPathAsync(DllPath).get();
    auto folder = file.GetParentAsync().get();
    modelFile = folder.GetFileAsync(WINML_MODEL_FILENAME).get();
```

1. Укажите (пакетов в Nuget) файлы заголовков (.h) и файлы с расширением MANIFEST для удобства использования Win32 cpp или .net core разработчиков приложений.

1. Файлы заголовков для C++ приложений

- Компонент WINRT cpp = > Свойства проекта "->" MIDL "->" выходные данные "->" файл заголовка
- WinRT C# компонент = > winmdidl средство для преобразования .winmd в .idl; и midlrt преобразуемый .idl в файлах заголовков.
- Создайте .idl из. winmd winmdidl <filename.winmd> /utf8 /metadata_dir:<path-to-sdk-unionmetadata> /metadata_dir: <path-to-additional-winmds> /outdir:<output-path>
- Всегда создайте .h из /ns_prefix /metadata_dir < путь к sdk-unionmetadata > .idl midlrt < filename.idl >.

    2. Для загрузки параллельно навыков в приложениях, не упакованных манифеста: я. Формат:

```xml
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<assembly xmlns="urn:schemas-microsoft-com:asm.v3" manifestVersion="1.0">
    <assemblyIdentity
        type="win32"
        name="manifest Identityname preferable same as dll name without extension and same as filename of this manifest"
        version="1.0.0.0"/>

<file name="name of dll of the skill component including extension">

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

Формат манифеста на стороне приложения:
<div style="text-align:center" markdown="1">

![Схема манифеста для загрузки SxS компонентов WinRT](../images/vision-skills-manifest.png)

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

Ура квалификации теперь готов для использования в приложении рабочего стола. Полный исходный код для примера, скоро будут доступны на сайте GitHub.
Поэкспериментируйте с другими образцами [GitHub](https://github.com/Microsoft/WindowsVisionSkillsPreview/tree/master/samples/SentimentAnalyzerCustomSkill) и расширить их так, как вам нравится.

[!INCLUDE [help](../includes/get-help-vision.md)]
