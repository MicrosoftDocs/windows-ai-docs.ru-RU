---
author: rosanevallim
title: Часто задаваемые вопросы (часто задаваемые вопросы)
description: Эта страница содержит ответы на самые популярные вопросы от сообщества.
ms.author: rovalli
ms.date: 2/12/2019
ms.topic: article
keywords: Windows 10, windows искусственного интеллекта, машинного обучения windows, winml, windows машинное обучение
ms.localizationpriority: medium
ms.openlocfilehash: 4d0aab37ee9020ae29502653cf867ac673199f96
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474471"
---
# <a name="faq-frequently-asked-questions"></a>Часто задаваемые вопросы (часто задаваемые вопросы)

Эта страница содержит ответы на самые популярные вопросы от сообщества.

## <a name="how-do-i-know-if-the-onnx-model-i-have-will-run-with-windows-ml"></a>Как узнать, если модели ONNX, у меня будет выполняться с помощью машинного Обучения Windows?

Минимальная версия ONNX, поддерживаемого Windows API машинного Обучения — 1.2.2. При обучении модели, проверьте, поддерживает ли ваша платформа сохранение моделей для 1.2.2 формат.

## <a name="how-do-i-convert-a-model-of-a-different-format-to-onnx"></a>Как преобразовать модель другой формат ONNX?

Можно использовать [WinMLTools](convert-model-winmltools.md) для преобразования моделей из нескольких различных форматов, таких как Apple CoreML и scikit-научитесь ONNX.

## <a name="which-version-of-winmltools-should-i-use"></a>Какая версия WinMLTools следует использовать?

Мы всегда рекомендуем вам загрузить и установить последнюю версию **winmltools** пакета. Это гарантирует, что можно создавать модели ONNX, предназначенных для последних версий Windows.

## <a name="can-i-use-onnxmltools-instead-of-winmltools"></a>Можно ли использовать onnxmltools вместо winmltools?

Да, вы можете, но необходимо будет установить правильную версию [onnxmltools](https://github.com/onnx/onnxmltools) для работы с v1.2.2 ONNX, который является минимальной версией ONNX, поддерживаемых Windows машинного Обучения. Если вы не уверены, какая версия для установки, рекомендуется установить последнюю версию **winmltools** вместо этого. Это позволит гарантировать, что вы сможете ориентированы на версию ONNX, поддерживаемых Windows.

## <a name="which-version-of-visual-studio-should-i-use-in-order-to-get-automatic-code-generation-mlgen"></a>Какие версии Visual Studio следует использовать для получения автоматическое создание кода (mlgen)?

Минимальный рекомендуемый версии [Visual Studio](https://visualstudio.microsoft.com/vs/) с поддержкой [mlgen](mlgen.md) является 15.8.7. В Windows 10, версия 1903 и более поздние версии, **mlgen** больше не входит в пакет SDK, поэтому вам потребуется загрузить и установить расширение. Имеется один для [Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=WinML.mlgen) и один для [Visual Studio 2019](https://marketplace.visualstudio.com/items?itemName=WinML.mlgenv2).

## <a name="i-get-an-error-message-when-trying-to-run-mlgen-and-no-code-is-generated-what-could-possibly-be-happening"></a>Получено сообщение об ошибке при попытке запуска mlgen и код не создается. Что бы возможно это значило?

Ниже приведены две наиболее распространенные ошибки при попытке выполнения mlgen.

* **Отсутствует необходимый атрибут «consumed_inputs»**: При возникновении это сообщение об ошибке, затем скорее вы пытаетесь запустить модель v1.2 ONNX с версией пакета SDK Windows 10 старше 17763; Мы рекомендуем проверить установленную версию пакета SDK и обновить его до версии 17763 или более поздней версии.
* **Ошибка типа: Тип (map(string,tensor(float))) из выходных данных arg (потеря) узла (ZipMap) не соответствует ожидаемому типу...** : При возникновении этой ошибки, скорее всего модели ONNX, то более старой версии, чем принимаемое WinML, начиная со сборки 17763. Мы рекомендуем обновить преобразователь пакет до последней доступной версии и выполните повторное преобразование модели до версии 1.2 ONNX.

## <a name="why-cant-i-load-a-model"></a>Почему не удается загрузить модель?

Существует несколько причин, почему могут возникнуть проблемы при загрузке модели, но одна из самых распространенных рисков при разработке для универсальной платформы Windows — из-за ограничений доступа к файлам. По умолчанию приложения универсальной платформы Windows можно только некоторые части файловой системы и требует наличия разрешения пользователя или дополнительные возможности для доступа к другим расположениям. См. в разделе [разрешения доступа](https://docs.microsoft.com/windows/uwp/files/file-access-permissions) Дополнительные сведения.

## <a name="what-does-winml-run-on-by-default"></a>Что WinML запускать на по умолчанию?

Если не указать устройство под управлением с [LearningModelDeviceKind](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodeldevicekind), или если вы используете **LearningModelDeviceKind.Default**, система определит, какие устройства будет оценивать модели. Обычно это ЦП. Для запуска WinML на GPU, укажите одно из следующих значений при создании [LearningModelDevice](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodeldevice):

* **LearningModelDeviceKind.DirectX**
* **LearningModelDeviceKind.DirectXHighPerformance**
* **LearningModelDeviceKind.DirectXMinPower**

[!INCLUDE [help](includes/get-help.md)]
