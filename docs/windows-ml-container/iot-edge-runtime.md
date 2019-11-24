---
title: Среда выполнения Azure IoT Edge
description: Узнайте, как добавить контейнер Windows ML на устройство с помощью Azure IoT Edge
ms.date: 10/14/2019
ms.topic: article
keywords: windows 10, контейнер Windows ML, контейнер, Интернет вещей, Edge
ms.localizationpriority: medium
ms.openlocfilehash: 4c8f327505216321a0ff5a1939e25d4fba6a8cf2
ms.sourcegitcommit: f5945af6d1f534b490eea7860f72804dc1c9fea8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/15/2019
ms.locfileid: "72315408"
---
# <a name="use-the-windows-ml-container-insider-preview-with-azure-iot-edge-runtime"></a>Использование предварительной версии контейнера машинного обучения Windows с Azure IoT Edge Runtime

Из-за соответствия требованиям к версии ОС и контейнеров для использования среды выполнения Azure IoT Edge с предварительной версией контейнера машинного обучения Windows необходимо выполнить несколько действий для подготовки среды выполнения Azure IoT Edge.  

> [!IMPORTANT]
> В приведенных ниже действиях предполагается некоторое удобство и знакомство с использованием [DOCKER](https://docs.docker.com/engine/reference/commandline/cli/) и [Azure IOT Edge](https://docs.microsoft.com/azure/iot-edge/).

## <a name="environment-setup"></a>Настройка среды

На хост-компьютере предварительной версии Windows Insider Preview с соответствующей версией для установленного контейнера машинного обучения Windows выполните следующие действия.
- [Установите пакет SDK для .NET Core](https://dotnet.microsoft.com/download).
- [Установите Git](https://git-scm.com/downloads).
- Установите DOCKER из хозяина DOCKER, следуя инструкциям в разделе [Приступая к работе](getting-started.md).
- [Установите Azure CLI](https://docs.microsoft.com/cli/azure/install-azure-cli-windows?view=azure-cli-latest).
- [Создайте частный реестр контейнеров](https://docs.microsoft.com/azure/container-registry/container-registry-get-started-portal) в реестре контейнеров Azure для хранения модулей Azure IOT Edge. (Обратите внимание, что при включении [учетной записи администратора](https://docs.microsoft.com/azure/container-registry/container-registry-authentication) может быть проще войти в систему.)
- [Создание центра Интернета вещей Azure](https://docs.microsoft.com/en-us/azure/iot-hub/iot-hub-create-through-portal) для управления устройствами и развертываниями в облаке.

## <a name="build-private-azure-iot-edge-runtime-module"></a>Создание закрытого модуля среды выполнения Azure IoT Edge

### <a name="prepare-base-os-image"></a>Подготовка базового образа ОС

- Запустите CMD или PowerShell от имени администратора,
- Войдите в реестр контейнеров Azure из DOCKER.
- Вытяните базовый образ контейнера машинного обучения Windows (*измените тег, чтобы он совпадал с версией вашего узла Insider*), с помощью следующих команд.
    - `docker pull mcr.microsoft.com/windows/ml/insider:10.0.18999.1`
    - `docker tag mcr.microsoft.com/windows/ml/insider:10.0.18999.1 windowsml:latest`
- Клонировать Azure IoT Edge в `C:\iotedge`.
    - `cd /d c:\`
    - `git clone https://github.com/Azure/iotedge.git`

### <a name="build-edge-hub-container"></a>Создание контейнера концентратора ребра

Выполните следующие команды, чтобы создать контейнер концентратора ребра.

- `cd c:\iotedge\edge-hub\src\Microsoft.Azure.Devices.Edge.Hub.Service\`
- `dotnet publish -r win-x64`
- `cd bin\Debug\netcoreapp2.1\win-x64\`

- Создайте Dockerfile с содержимым, как показано ниже, и сохраните его на `c:\iotedge\edge-hub\src\Microsoft.Azure.Devices.Edge.Hub.Service\bin\Debug\netcoreapp2.1\win-x64`:

    ```console
    FROM windowsml:latest
    WORKDIR /app
    COPY publish/ ./
    # Expose MQTT, AMQP and HTTPS ports-
    EXPOSE 8883/tcp
    EXPOSE 5671/tcp
    EXPOSE 443/tcp
    CMD ["Microsoft.Azure.Devices.Edge.Hub.Service.exe"]
    ```

    Выполните следующие команды.

    - `docker build . -t your-own-registry.azurecr.io/hub:latest`
    - `docker push your-own-registry.azurecr.io/hub:latest`

### <a name="build-agent-container"></a>Контейнер агента сборки

Выполните следующие команды, чтобы создать контейнер агента.

- `cd c:\iotedge\edge-agent\src\Microsoft.Azure.Devices.Edge.Agent.Service\`
- `dotnet publish -r win-x64`
- `cd bin\Debug\netcoreapp2.1\win-x64`

- Создайте Dockerfile с содержимым, как в следующем примере, и сохраните его в: `c:\iotedge\edge-agent\src\Microsoft.Azure.Devices.Edge.Agent.Service\bin\Debug\netcoreapp2.1\win-x64`
    ```console
    FROM windowsml:latest
    # Configure web servers to bind to port 80 when present
    ENV ASPNETCORE_URLS=http://+:80
    WORKDIR /app
    COPY publish/ ./
    CMD ["Microsoft.Azure.Devices.Edge.Agent.Service.exe"]
    ```

Выполните следующие команды.

- `docker build . -t your-own-registry.azurecr.io/agent:latest`
- `docker push your-own-registry.azurecr.io/agent:latest`

### <a name="build-other-azure-iot-edge-modules"></a>Создание других модулей Azure IoT Edge

Если существуют другие модули, которые будут развернуты на пограничном устройстве, на котором выполняется Azure IoT Edge и контейнер предварительной версии Windows ML Insider на узле Windows Insider, потребуется перестроить эти модули на основе того же образа контейнера Insider для Windows, который соответствует версия узла программы предварительной оценки Windows.

## <a name="configure-iot-edge-in-the-azure-iot-hub-portal"></a>Настройка IoT Edge на портале Центра Интернета вещей Azure

- Создание устройства IoT Edge в центре Интернета вещей Azure.
    ![iotedge01](./images/iotedge01.png)

- Назовите устройство **тестдевице** и выберите симметричный ключ.
    ![iotedge02](./images/iotedge02.png)

- Выберите **задать модули**.
    ![iotedge03](./images/iotedge03.png)

- Укажите сведения о реестре контейнеров, в которые были помещены закрытые модули.
    ![iotedge04](./images/iotedge04.png)

- На странице Set modules (Настройка модулей) нажмите кнопку **настроить дополнительные параметры среды выполнения ребра** , а затем задайте для концентратора ребра и агента ребра, где вы опубликовали закрытые контейнеры.
    ![iotedge05](./images/iotedge05.png)

- Нажмите кнопку **сохранить** .
- Не забудьте выбрать **Next-> следующий-Submit** .

С этого момента при необходимости можно добавить некоторые модули развертывания на устройство.

## <a name="setting-up-azure-iot-edge-on-windows-ml-container-host"></a>Настройка Azure IoT Edge на узле контейнера Windows ML

> [!IMPORTANT]
> При настройке Azure IoT Edge убедитесь, что версия ОС контейнера совпадает с версией узла контейнера, который использовался для создания модулей концентратора ребра и пограничных агентов.

- Устройство, на котором выполняется установка IoT Edge, **не** должно работать с DOCKER.
- Службу DOCKER можно отключить, если вы поэкспериментируем с компьютером сборки контейнера, приведенным выше.

### <a name="download-and-modify-installation-powershell-script"></a>Скачать и изменить сценарий PowerShell для установки

- Сохраните копию `IoTEdgeSecurityDaemon.ps1` локально, выполнив эту команду из командной строки с *повышенными привилегиями* .

```console
curl -o c:\IotEdgeSecurityDaemon.ps1 -L  https://raw.githubusercontent.com/Azure/iotedge/1.0.8/scripts/windows/setup/IotEdgeSecurityDaemon.ps1
```

- Изменение `IoTEdgeSecurityDaemon.ps1` для отключения ограничений версии сборки
-   В функции `Initialize-IoTedge` закомментируйте следующую строку.

```console
 #   if (-not (Setup-Environment -ContainerOs $ContainerOs -SkipArchCheck -SkipBatteryCheck)) {
 #       return
 #   }
```
-   В функции `Install-Packages` закомментируйте следующую строку:

```console
#    if (-not (Setup-Environment -ContainerOs $ContainerOs -SkipArchCheck:$SkipArchCheck -SkipBatteryCheck:$SkipBatteryCheck)) {
#        return
#    }
```

### <a name="install-iot-edge"></a>Установка IoT Edge

- Выполните следующую команду из экземпляра PowerShell с *повышенными привилегиями* :

```console
. {Invoke-WebRequest -useb c:\IotEdgeSecurityDaemon.ps1} | Invoke-Expression;  Deploy-IoTEdge
```

- Если устройство перезагружается, дождитесь его перезапуска. При необходимости снова запустите экземпляр PowerShell с *повышенными привилегиями* и выполните следующую команду.

> [!NOTE]
> Не забудьте заменить реестр контейнеров, имя пользователя, пароль и строку подключения в следующем примере.

```console
. {Invoke-WebRequest -useb c:\IotEdgeSecurityDaemon.ps1} | Invoke-Expression; Initialize-IoTEdge -AgentImage your-container-registry.azurecr.io/agent:latest  -Username yourRegistryUserName -Password $(ConvertTo-SecureString yourregistryPassword -AsPlainText -Force)  -Manual -DeviceConnectionString connectionstringOfTestDevice
```

- Подождите несколько минут, пока завершится процесс, а затем выполните следующую команду.

```console
PS C:\> iotedge list
```

Вы увидите, что агент и концентратор работают, как показано ниже.

```
NAME             STATUS           DESCRIPTION      CONFIG
edgeHub          running          Up 9 seconds     winmlc.azurecr.io/hub:latest
edgeAgent        running          Up 22 seconds    winmlc.azurecr.io/agent:latest
```
