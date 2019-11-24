---
title: Приступая к работе с контейнером Windows ML
description: Приступая к работе с контейнером Windows ML на устройстве IoT
ms.date: 10/14/2019
ms.topic: article
keywords: Windows 10, контейнер Windows ml, ML, AI, контейнер, IOT, ребро
ms.localizationpriority: medium
ms.openlocfilehash: 729d348a5606b97fd493382609919dac730edc76
ms.sourcegitcommit: e08b8ae92e48c1b82bb6f94fefcb32cd817453d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72443018"
---
# <a name="getting-started"></a>Начало работы

Контейнер Windows ML предназначен для разработчиков, которые уже знакомы с основами разработки IoT и Windows ML. Дополнительные сведения об использовании Windows ML см. [в документации по Windows ML](../windows-ml/index.md).

## <a name="prerequisites-and-environment-setup"></a>Предварительные требования и настройка среды

Чтобы установить предварительную версию Windows, необходимо [присоединиться к программе предварительной оценки Windows](https://insider.windows.com/register/).

После установки предварительной версии узла Windows можно запустить `winver` в командной строке, чтобы найти версию узла.

![winver](./images/winver.png)

В приведенном выше примере используется версия узла `18999.1`.

### <a name="host-os-and-container-version-matching-requirements"></a>Требования соответствия для ОС узла и версии контейнера

Контейнер Windows ML выполняется поверх узла Windows Enterprise. Ваша версия контейнера машинного обучения Windows должна точно соответствовать версии **сборки быстрого вызова Windows 10 Insider Preview (20H1)** .

### <a name="windows-ml-container-on-docker-hub"></a>Контейнер Windows ML в концентраторе DOCKER

Определив версию узла, найдите соответствующий тег на странице центра DOCKER для программы [предварительной оценки контейнера Windows ML](https://hub.docker.com/_/microsoft-windows-ml-insider). Нахождение соответствующего тега версии и URL-адреса для извлечения DOCKER.

```console
10.0.18999.1 (20H1)
docker pull mcr.microsoft.com/windows/ml/insider:10.0.18999.1
```

### <a name="visual-studio-2019"></a>Visual Studio 2019

При разработке для контейнера Windows ML рекомендуется использовать Visual Studio 2019. Последний выпуск Community Edition доступен бесплатно [на сайте Visual Studio](https://visualstudio.microsoft.com/vs/). Если вы еще не работали с Visual Studio, следуйте инструкциям и рекомендациям на сайте, чтобы получить дополнительные сведения.

При настройке установки Visual Studio убедитесь, что установлены следующие пакеты:
- "Разработка приложений для универсальной платформы Windows".
- Средства разработки .NET Core для кросс-платформенных development.NET Core 2,2

![vs_install1](./images/vs_install1.png)

![vs_install2](./images/vs_install2.png)

### <a name="windows-sdk-insider-preview"></a>Предварительная версия Windows SDK предварительной версии

Убедитесь, что версия контейнера машинного обучения Windows и Windows SDK предварительной версии Insider можно найти максимально точно. Точное совпадение версий не требуется, но чем больше несовпадений, тем больше вероятность ошибок или других проблем.

[Последний пакет SDK для предварительной версии доступен здесь.](https://www.microsoft.com/software-download/windowsinsiderpreviewSDK)

### <a name="configure-visual-studio-2019-nuget-package-source"></a>Настройка источника пакета NuGet для Visual Studio 2019

Пока контейнер Windows ML находится на этапе предварительной версии, контракт среды выполнения [Windows без монитора](api-list.md) предоставляется через пакет NuGet из отдельного источника пакета.

Убедитесь, что в источнике пакета находятся следующие источники:

- https://api.nuget.org/v3/index.json
- https://pkgs.dev.azure.com/WindowsSDK/PublicArtifactsPreview/_packaging/WindowsSDKFlight/nuget/v3/index.json

Чтобы добавить новый источник, выполните следующие действия.

- Откройте Visual Studio 2019
- Выберите **инструменты-> диспетчер пакетов NuGet — > параметры диспетчера пакетов — > источники пакетов** и добавьте URL-адрес источника рейса пакета SDK.

![vs_install3](./images/vs_install3.png)

![vs_install4](./images/vs_install4.png)

### <a name="gpu-support"></a>Поддержка GPU

Чтобы ускорение GPU поддерживалось контейнером, узел должен иметь возможность использовать графический процессор и графический драйвер, отвечающие следующим требованиям:

#### <a name="gpu-requirements"></a>Требования к графическому процессору:


|Разработчика   |Architecture (Архитектура)        |Стандартные имена GPU для клиентов  |
|---------|--------------------|-----------------------------------|
|AMD      | GCN 4 или более поздней версии     |Серия 400 и более поздних версий или Radeon Pro WX|
|Intel    | Каби Lake или более поздней версии |Intel HD Graphics 600 или более поздняя версия |
|NVIDIA   | Kepler или более поздняя версия    |Серии GeForce 600 или более поздней версии или Куадро серии K или более поздней|

#### <a name="graphics-driver-requirements"></a>Требования к графическим драйверам

|Разработчика|Минимальная версия драйвера  |
|------|--------------------|
|AMD   |26.20.12002.65 |
|Intel |26.20.100.6812 |
|NVIDIA|26.21.14.3086  |

Если GPU или драйвер не соответствуют приведенным выше требованиям или операционная система узла контейнера работает на виртуальной машине, то поддерживается только вывод на основе ЦП.

#### <a name="graphics-driver-installation"></a>Установка драйвера графики

Загрузите последние версии графических драйверов для вашей системы, перейдя к **параметрам > обновление & безопасность > Центр обновления Windows > проверить наличие обновлений**.

![дриверупдате](./images/windowsupdate.png)

#### <a name="troubleshooting-graphics-driver"></a>Устранение неполадок графического драйвера

Убедитесь, что ваша версия драйвера соответствует минимальным требованиям, перейдя к **Device Manager > адаптеров дисплея**, щелкнув правой кнопкой мыши графический адаптер и выбрав пункт **свойства**, а затем перейдя на вкладку **драйвер** :

![устранить неполадки](./images/troubleshoot.png)

Если не удается загрузить графический драйвер с помощью Центр обновления Windows, который соответствует минимальным требованиям к версии, отправьте сообщение по электронной почте winmlc-questions@microsoft.com с присоединенными сведениями о DxDiag вашей системы. Инструкции по запуску и сохранению сведений DxDiag [см. на этой странице поддержки](https://support.microsoft.com/help/4028644/windows-open-and-run-dxdiagexe).

## <a name="set-up-and-test-a-basic-environment"></a>Настройка и тестирование базовой среды

1.  Убедитесь, что ОС узла и образ контейнера Windows ML имеют одинаковый номер версии.

2.  Включите функциональные возможности **контейнеров** в ОС узла.

    В окне командной строки с *повышенными привилегиями* выполните следующую команду.  Может появиться запрос на перезагрузку системы.

```console
dism /online /Enable-Feature /FeatureName:Containers
```

3.  Загрузите ночные сборки для версий DOCKER. exe и dockerd. exe.

```console
curl.exe -o %windir%\system32\dockerd.exe https://master.dockerproject.org/windows/x86_64/dockerd.exe
```
```console
curl.exe -o %windir%\system32\docker.exe https://master.dockerproject.org/windows/x86_64/docker.exe
```

Зарегистрируйте и запустите службу DOCKER.

```console
dockerd.exe --register-service

net start docker
```

Должно отобразиться следующее выходное сообщение.

```console
The Docker Engine service is starting.
The Docker Engine service was started successfully.
```

4.  Вы можете убедиться, что DOCKER правильно работает, выполнив следующую команду.

```console
docker version
```

Это должно привести к появлению следующего выходного сообщения.

```console
Client:
    Version:           master-dockerproject-2019-08-03
    API version:       1.40
    Go version:        go1.12.7
    Git commit:        e505a7c2
    Built:             Sun Aug  4 00:02:51 2019
    OS/Arch:           windows/amd64
    Experimental:      false

Server:
    Engine:
    Version:          master-dockerproject-2019-08-03
    API version:      1.41 (minimum version 1.24)
    Go version:       go1.12.7
    Git commit:       7449ca3
    Built:            Sun Aug  4 00:12:27 2019
    OS/Arch:          windows/amd64
    Experimental:     false
```

5.  После запуска DOCKER импортируйте файл образа контейнера в DOCKER с помощью следующей команды.

```console
docker pull mcr.microsoft.com/windows/ml/insider:10.0.18999.1
docker tag mcr.microsoft.com/windows/ml/insider:10.0.18999.1 windowsml:latest
```

6.  После установки образа можно запустить `docker images`, чтобы перечислить все доступные образы контейнеров. По умолчанию этот образ не будет содержать имя или тег репозитория. Вы можете указать один из них или просто использовать идентификатор образа из предоставленного хэша для ссылки на образ в последующих шагах.

Результат может выглядеть примерно так.

```console
C:\Windows\system32>docker images
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
<none>              <none>              a9d5d08d079f        10 seconds ago      319MB

C:\Windows\system32>docker tag a9d5d08d079f windowsml:latest

C:\Windows\system32>docker images
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
windowsml           latest              a9d5d08d079f        25 seconds ago      319MB
```


7.  Скачайте Винмлруннер v 1.2.1.1 из https://github.com/microsoft/Windows-Machine-Learning/releases/tag/1.2.1.1 с помощью следующей команды.

```console
curl -o WinMLRunner.zip -L https://github.com/microsoft/Windows-Machine-Learning/releases/download/1.2.1.1/WinMLRunner.v1.2.1.1.zip
```

Затем распакуйте ZIP-файл в текущую папку.

8.  Скачайте пример Скуизенет. onnx из https://github.com/microsoft/Windows-Machine-Learning/tree/1.2.1.1/SharedContent/models с помощью следующей команды.

```console
curl -o SqueezeNet.onnx -L https://github.com/microsoft/Windows-Machine-Learning/raw/1.2.1.1/SharedContent/models/SqueezeNet.onnx
```

9.  Создайте Dockerfile, чтобы скопировать необходимые файлы в импортированный образ контейнера машинного обучения Windows.

Вы можете скопировать приведенные ниже команды для непосредственного создания Dockerfile:     

```console
echo FROM windowsml:latest               >  Dockerfile
echo WORKDIR C:/App                      >> Dockerfile
echo COPY ./x64/WinMLRunner.exe C:/App/  >> Dockerfile
echo COPY ./SqueezeNet.onnx C:/App/      >> Dockerfile
```

```console
C:\tgz>type Dockerfile
FROM windowsml:latest
WORKDIR C:/App
COPY ./x64/WinMLRunner.exe C:/App/
COPY ./SqueezeNet.onnx C:/App/
```


10. Создайте новый контейнер на основе Dockerfile с `docker build command`.

```console
C:\tgz>docker build -t winmlrunner:latest .
```

Результаты будут похожи на приведенные ниже.


```console
Sending build context to Docker daemon  5.525MB
Step 1/4 : FROM windowsml:latest
 ---> a9d5d08d079f
Step 2/4 : WORKDIR C:/App
 ---> Running in 37e9d759365f
Removing intermediate container 37e9d759365f
 ---> 8ab270ff4deb
Step 3/4 : COPY ./x64/WinMLRunner.exe C:/App/
 ---> 16e2b23a5de0
Step 4/4 : COPY ./SqueezeNet.onnx C:/App/
 ---> 05269bb7c5f8
Successfully built 05269bb7c5f8
Successfully tagged winmlrunner:latest

C:\tgz>docker images
REPOSITORY          TAG                 IMAGE ID            CREATED              SIZE
winmlrunner         latest              ed74203b2655        About a minute ago   325MB
windowsml           latest              a9d5d08d079f        23 minutes ago       319MB
```

11. Запустите контейнер изолированных процессов с поддержкой GPU на основе контейнера Windows ML и образа Винмлруннер.

```console
docker run -it --isolation process --device class/5B45201D-F2F2-4F3B-85BB-30FF1F953599 winmlrunner:latest cmd /k
```

Существует несколько важных аргументов, которые необходимо указать для запуска контейнеров Windows ML с помощью DOCKER.

- `-it`  
    Используется, чтобы разрешить компонентам интерактивной оболочки пересылать `stdin` и использовать `tty`. Если опустить этот аргумент, интерфейс командной строки будет работать неправильно.
- `--isolation process` указывает тип контейнера в качестве контейнера, изолированного от процесса.
- `--device class/5B45201D-F2F2-4F3B-85BB-30FF1F953599` указывает идентификатор GUID класса для устройства, которое должно быть предоставлено в контейнер. `class/5B45201D-F2F2-4F3B-85BB-30FF1F953599` относится к `GUID_DEVINTERFACE_DISPLAY_ADAPTER`, который включает DirectX GPU.
- `winmlrunner:latest` указывает образ для выполнения, созданный на предыдущих шагах. Это может быть имя репозитория и тег, указанные во время выполнения команды `docker tag`, или идентификатор или хэш образа. Если в качестве имени тега использовался **последний** , его можно опустить.
- `cmd /k`  
    Это команда, которую DOCKER будет выполнять в контейнере.

12. В командной строке контейнера запустите Винмлруннер с помощью ЦП.

```console
WinMLRunner.exe -model C:/App/SqueezeNet.onnx -cpu
```

Выходные данные должны выглядеть следующим образом.

```console
DXGI module not found.
Loading model (path = C:/App/SqueezeNet.onnx)...
=================================================================
Name: squeezenet_old
Author: onnx-caffe2
Version: 9223372036854775807
Domain:
Description:
Path: C:/App/SqueezeNet.onnx
Support FP16: false

Input Feature Info:
Name: data_0
Feature Kind: Float

Output Feature Info:
Name: softmaxout_1
Feature Kind: Float

=================================================================


Creating Session with CPU device
Binding (device = CPU, iteration = 1, inputBinding = CPU, inputDataType = Tensor, deviceCreationLocation = WinML)...[SUCCESS]
Evaluating (device = CPU, iteration = 1, inputBinding = CPU, inputDataType = Tensor, deviceCreationLocation = WinML)...[SUCCESS]
```
Поздравляем, теперь ваша среда правильно настроена для использования контейнера Windows ML.

13. Вы также можете запустить Винмлруннер с помощью GPU. Укажите один из процессоров AMD Radeon, NVIDIA или Intel с помощью аргумента командной строки `-GPUAdapterName`.

```console
WinMLRunner.exe -model C:/App/SqueezeNet.onnx -GPUAdapterName [radeon/nvidia/intel]
```

## <a name="build-apps-the-for-windows-ml-container"></a>Создание приложений для контейнера машинного обучения Windows

### <a name="samples-for-windows-ml-container"></a>Примеры для контейнера машинного обучения Windows

Чтобы приступить к работе, убедитесь, что Visual Studio 2019 настроена и настраивается в соответствии с приведенными выше инструкциями. Затем попробуйте выполнить следующие примеры:

- [Кустомвисион](https://github.com/imingc/Windows-Machine-Learning/tree/winml_container/Samples/CustomVision). В этом примере используется модель, обученная [Пользовательская служба визуального распознавания Azure](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home). Обученная модель [экспортируется как файл ONNX](https://docs.microsoft.com/en-us/azure/cognitive-services/custom-vision-service/custom-vision-onnx-windows-ml) и входит в состав примера приложения, выполняемого внутри контейнера.
- [Скуизенетобжектдетектион](https://github.com/microsoft/Windows-Machine-Learning/tree/master/Samples/SqueezeNetObjectDetection). Это приложение (только для\# cpp и c) использует модель Скуизенет для обнаружения основного объекта в изображении.

### <a name="create-a-visual-studio-2019-c-project-from-scratch"></a>Создание проекта Visual Studio 2019 C# с нуля

Контейнер Windows ML поддерживает только [подмножество API Windows](api-list.md) из-за небольшого размера. При создании проекта Visual Studio можно указать эту меньшую поверхность API, чтобы обнаружить неподдерживаемые API до выполнения.

Чтобы использовать неавтономный контракт API WinRT:

1. В Visual Studio 2019 создайте новый проект **консольного приложения C\# (.NET Core)** .

![вспрож](./images/vs_project1.png)

1. Выберите **инструменты-> NuGet — консоль диспетчера пакетов >**

1. В консоли диспетчера пакетов выполните:

```console
Install-Package Microsoft.Windows.SDK.Headless.Contracts -Prerelease
```

### <a name="create-a-visual-studio-2019-c-project-from-scratch"></a>Создание проекта Visual Studio 2019 C++ с нуля

1. В Visual Studio 2019 создайте новый  **C++ проект консольного приложения** .

![вспрож](./images/vs_project2.png)

1. Выберите **инструменты-> NuGet — консоль диспетчера пакетов >**

1. В консоли диспетчера пакетов выполните:

```console
Install-Package Microsoft.Windows.SDK.Headless.Contracts -Prerelease
Install-Package Microsoft.Windows.CppWinRT -Version 2.0.190730.2
```

4. Обновите проект, чтобы использовать `windowscoreheadless.lib`:
    1. Щелкните проект правой кнопкой мыши.
    1. Выбор свойств
    1. В диалоговом окне выберите компоновщик — > входные данные.
    1. Обновите дополнительные зависимости, чтобы включить `windowscoreheadless.lib`. Например:
        1. `windowscoreheadless.lib;%(...AdditionalDependencies...)`

![vsproj3](./images/vs_project3.png)
