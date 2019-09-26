---
title: ИИ Windows
description: Получите справку по выбору решения искусственного интеллекта Microsoft для вашего приложения.
author: mattwojo
ms.author: mattwoj
ms.date: 09/18/2019
ms.topic: article
keywords: Windows 10, Windows AI, Windows ml, winml, машинное обучение Windows, Microsoft AI, сравнение, сравнение, навыки работы с Windows, Direct ML
ms.localizationpriority: medium
ms.openlocfilehash: f6648a891244d76f96658b7e1e9d8b69b0b34f8b
ms.sourcegitcommit: 478efb930668f2d16dfa18c9b52853f7e2e6dcd8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/25/2019
ms.locfileid: "71278503"
---
# <a name="which-ai-solution-is-right-for-me"></a>Какое решение искусственного интеллекта подходит мне?

Корпорация Майкрософт предлагает несколько решений ИИ. Это означает, что вы не ограничены одним вариантом. Но как выбрать подходящий для приложения? Давайте разберемся.

### <a name="i-want-to-integrate-a-machine-learning-model-into-my-application-and-run-it-on-the-device-by-taking-full-advantage-of-hardware-acceleration"></a>Мне нужно интегрировать модель машинного обучения в свое приложение и запустить его на устройстве, используя все преимущества аппаратного ускорения

Для вас наилучший вариант — [машинное обучение Windows](windows-ml/index.md). Эти высокоуровневые интерфейсы API WinRT работают с приложениями Windows 10 (UWP, классические приложения) и выполняют оценку моделей непосредственно на устройстве. Вы можете даже использовать GPU устройства (при наличии), чтобы повысить производительность.

### <a name="i-want-to-integrate-computer-vision-into-my-application-and-take-advantage-of-platform-optimizations"></a>Я хочу интегрировать компьютерное зрение в свое приложение и воспользоваться преимуществами оптимизации платформы

Наилучший вариант в этом случае — [платформа навыков компьютерного зрения Windows](windows-vision-skills/index.md). Эта простая платформа позволяет создавать пользовательские приложения компьютерного зрения, использующие аппаратное ускорение на пограничных устройствах. Вы можете объединить готовые библиотеки для распространенных сценариев обработки изображений с моделями машинного обучения для выполнения специализированных задач.

### <a name="i-want-to-have-fuller-control-over-resource-utilization-during-model-execution-for-high-intensive-applications"></a>Мне нужно полностью контролировать использование ресурсов во время выполнения модели для ресурсоемких приложений

Вам подойдет [DirectML](https://docs.microsoft.com/windows/desktop/direct3d12/dml). Эти интерфейсы API типа DirectX предоставляют программную парадигму, привычную для разработчиков игр на C++, и позволяют воспользоваться всеми преимуществами оборудования.

### <a name="i-want-to-train-test-and-deploy-ml-models-with-a-framework-that-is-familiar-to-a-net-developer"></a>Мне нужно обучать, тестировать и развертывать модели машинного обучения на платформе, привычной для разработчиков .NET

Опробуйте возможности [ML.NET](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet), платформы машинного обучения для разработчиков .NET.

### <a name="i-want-to-leverage-the-power-of-the-azure-cloud-for-training-and-deploying-ml-models"></a>Я хочу использовать возможности облака Azure для обучения и развертывания моделей машинного обучения

См. [полный список решений машинного обучения от Майкрософт](https://docs.microsoft.com/azure/architecture/data-guide/technology-choices/data-science-and-machine-learning). Здесь также указано множество продуктов и служб, работающих в Azure.
