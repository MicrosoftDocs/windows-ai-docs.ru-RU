---
title: Версии ONNX и сборки Windows
description: Проверьте, какие версии ONNX поддерживаются для каждой сборки Windows 10.
ms.date: 2/12/2020
ms.topic: article
keywords: windows 10, windows ai, windows ml, winml, windows machine learning, onnx
ms.localizationpriority: medium
ms.openlocfilehash: 0788674e75a4a77948444f7bcedd47cfa9a30db4
ms.sourcegitcommit: 2139506ff12b7205283288c4bbac866ddfa812f3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/24/2020
ms.locfileid: "78935235"
---
# <a name="onnx-versions-and-windows-builds"></a>Версии ONNX и сборки Windows

Windows Machine Learning поддерживает определенные версии формата ONNX в выпущенных сборках Windows. Чтобы ваша модель работала с Windows ML, следите за тем, чтобы версия модели ONNX поддерживалась в выпуске Windows, для которого предназначено ваше приложение.

В таблице ниже перечислены все выпущенные в настоящее время версии Windows ML и поддерживаемые в них версии ONNX.

| Выпуск Windows | Поддерживаемые версии ONNX | Поддерживаемые наборы операций ONNX |
|-----------------|-------------------------|-----------------------|
| Windows 10, версия 1909 | 1.2.2 и 1.3 | 7 и 8 |
| Windows 10, версия 1903 (сборка 18362) | 1.2.2 и 1.3 | 7 и 8 |
| Windows 10, версия 1809 (сборка 17763) | 1.2.2 | 7 |

Если вы ведете разработку в тестовых сборках по программе предварительной оценки Windows, ознакомьтесь с [заметками о выпуске](release-notes.md), где указаны минимальная и максимальная поддерживаемые версии ONNX для тестовых сборок пакета SDK для Windows 10.

## <a name="onnx-opset-converter"></a>Преобразователь наборов операций ONNX

API ONNX содержит библиотеку для преобразования версий наборов операций для моделей ONNX. Это позволяет разработчикам, а также специалистам по обработке и анализу данных обновить существующую модель ONNX до более новой версии либо понизить модель до более ранней версии спецификации ONNX.

[Преобразователь версий](https://github.com/onnx/onnx/blob/master/docs/VersionConverter.md) можно вызывать через API-интерфейсы для C++ или Python. Существует также [руководство](https://github.com/onnx/tutorials/blob/master/tutorials/ExportModelFromPyTorchToDifferentONNXOpsetVersions.md) с примерами обновления модели ONNX до более новой версии или перехода на более раннюю версию набора операций.

[!INCLUDE [help](../includes/get-help.md)]
