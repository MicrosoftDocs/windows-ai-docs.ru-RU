---
title: ONNX версии и сборки Windows
description: Проверьте, какие версии ONNX поддерживаются каждой сборкой Windows 10.
ms.date: 7/2/2019
ms.topic: article
keywords: Windows 10, Windows AI, Windows ml, winml, машинное обучение Windows, onnx
ms.localizationpriority: medium
ms.openlocfilehash: 0124f1a5d66a2b8801aaab10237ed731faddf44f
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70156366"
---
# <a name="onnx-versions-and-windows-builds"></a>ONNX версии и сборки Windows

Windows Машинное обучение поддерживает определенные версии формата ONNX в выпущенных сборках Windows. Чтобы ваша модель работала с Windows ML, необходимо убедиться, что версия модели ONNX поддерживается для выпуска Windows, предназначенного для вашего приложения.

В таблице ниже приведены все выпущенные в настоящее время версии Windows ML и соответствующие поддерживаемые версии ONNX.

| Выпуск Windows | Поддерживаемые версии ONNX | ONNX опсетс поддерживается |
|-----------------|-------------------------|-----------------------|
| Windows 10, версия 1903 (сборка 18362) | 1.2.2 и 1,3 | 7 и 8 |
| Windows 10, версия 1809 (сборка 17763) | 1.2.2 | 7 |

Если вы разрабатываете с помощью сборок Insider Preview для Windows, просмотрите [заметки](release-notes.md) о выпуске для минимальной и максимальной поддерживаемой версии ONNX в РЕЙСАХ пакета SDK для Windows 10.

## <a name="onnx-opset-converter"></a>Преобразователь ONNX опсет

API ONNX предоставляет библиотеку для преобразования моделей ONNX между различными версиями опсет. Это позволяет разработчикам и специалистам по обработке и анализу данных либо обновить существующую модель ONNX до более новой версии, либо понизить модель до более старой версии спецификации ONNX.

[Преобразователь версий](https://github.com/onnx/onnx/blob/master/docs/VersionConverter.md) можно вызвать с помощью C++ API-интерфейсов или из Python. Кроме того, в этом [руководстве](https://github.com/onnx/tutorials/blob/master/tutorials/ExportModelFromPyTorchToDifferentONNXOpsetVersions.md) представлено несколько примеров того, как обновить и понизить модель ONNX до новой целевой опсет.

[!INCLUDE [help](../includes/get-help.md)]
