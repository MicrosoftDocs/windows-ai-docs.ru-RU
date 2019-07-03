---
author: eliotcowley
title: ONNX версиях и сборках Windows
description: Проверьте, какие версии ONNX поддерживаются с каждой сборки Windows 10.
ms.author: elcowle
ms.date: 7/2/2019
ms.topic: article
keywords: Windows 10, windows искусственного интеллекта, машинного обучения windows, winml, машинного обучения windows, onnx
ms.localizationpriority: medium
ms.openlocfilehash: 46a98f886fdd31002bf30023a534b10ac3a3bec4
ms.sourcegitcommit: 8c18dfc753694e26067e3155509cf6d7c970a765
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2019
ms.locfileid: "67515716"
---
# <a name="onnx-versions-and-windows-builds"></a>ONNX версиях и сборках Windows

Машинное обучение Windows поддерживает определенные версии в формат ONNX в сборках выпуска Windows. Чтобы модель для работы с машинным Обучением Windows, необходимо будет убедитесь, что в вашей версии модели ONNX поддерживается для выпуска Windows нацелено приложение.

Приведенной ниже таблице перечислены все распространяемой версии Windows "машинное обучение" и соответствующие поддерживаемые версии ONNX.

| Выпуск Windows | Поддерживаемые версии ONNX | Поддерживается opsets ONNX |
|-----------------|-------------------------|-----------------------|
| Windows 10 версии 1903 (сборка 18362) | 1.2.2 и 1.3 | 7 и 8 |
| Windows 10 версии 1809 (сборка 17763) | 1.2.2 | 7 |

Если вы разрабатываете с использованием сборок Windows Insider рейсов, проверьте наших [заметки о выпуске](release-notes.md) для минимального и максимального поддерживаемых версий ONNX в авиарейсов из пакета SDK для Windows 10.

## <a name="onnx-opset-converter"></a>Преобразователь opset ONNX

ONNX API предоставляет библиотеку для преобразования моделями ONNX между версиями различных opset. Благодаря этому разработчики и специалисты по анализу данных или обновление существующей модели ONNX до более новой версии, или понизить модели для более старой версии спецификации ONNX.

[Преобразователь версии](https://github.com/onnx/onnx/blob/master/docs/VersionConverter.md) может быть вызван с помощью C++ или API Python. Имеется также [руководстве](https://github.com/onnx/tutorials/blob/master/tutorials/ExportModelFromPyTorchToDifferentONNXOpsetVersions.md) о том, как повышение или понижение модель ONNX для новых opset целевой объект, предоставляющий несколько примеров.

[!INCLUDE [help](../includes/get-help.md)]
