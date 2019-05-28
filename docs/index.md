---
layout: LandingPage
author: eliotcowley
title: ИИ Windows
description: Преобразуйте свое приложение Windows с помощью возможностей ИИ.
ms.author: elcowle
ms.date: 4/17/2019
ms.topic: landing-page
keywords: windows 10, windows ai
ms.localizationpriority: medium
ms.openlocfilehash: 9161d0494b64035385e46908a53aa81b8e107099
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66175746"
---
# <a name="windows-ai"></a>ИИ Windows

Преобразуйте свое приложение Windows с помощью возможностей искусственного интеллекта. Средства ИИ Windows позволят вам и вашей компании достичь высоких результатов с помощью интеллектуальных решений для выполнения сложных задач.

<br/>

<div style="text-align:center">
    <img src="images/windows-ai-photo.png" alt="AI on farm"/>
</div>

<ul class="cardsK panelContent">
    <li>
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage bgdAccent1">
                            <a href="windows-ml/index.md">
                                <img src="https://docs.microsoft.com/media/hubs/windows/windows-ai.svg"
                                    alt="WinML graphic"
                                    data-linktype="external"
                                    class="x-hidden-focus"/>
                            </a>
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>
                            <a href="windows-ml/index.md">Машинное обучение Windows</a>
                        </h3>
                        <p>Узнайте, как интегрировать обученные модели машинного обучения в приложения Windows.</p>
                        <br/>
                        <ul>
                            <li><a href="windows-ml/get-started-uwp.md">Руководство. Создание приложения UWP WinML (C#)</a></li>
                            <li><a href="windows-ml/what-is-a-machine-learning-model.md">Что собой представляет модель машинного обучения</a></li>
                            <li><a href="windows-ml/api-reference.md">Справочник по API WinML</a></li>
                        </ul>
                    </div>
                </div>
            </div>
        </div>
    </li>
    <li>
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage bgdAccent1">
                            <a href="windows-vision-skills/index.md">
                                <img src="https://docs.microsoft.com/media/hubs/cortana/cortana-get-started-build-skill-language.svg" alt="Windows Vision Skills graphic" data-linktype="external" class="x-hidden-focus"/>
                            </a>
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>
                            <a href="windows-vision-skills/index.md">Навыки компьютерного зрения Windows</a>
                        </h3>
                        <p>Устраняйте сложности реализации компьютерного зрения с помощью навыков.</p>
                        <br/>
                        <ul>
                            <li><a href="windows-vision-skills/tutorial.md">Руководство. Создание собственного навыка компьютерного зрения (C#)</a></li>
                            <li><a href="windows-vision-skills/tutorial1.md">Руководство. Создание приложения UWP навыков компьютерного зрения Windows (C#)</a></li>
                            <li><a href="windows-vision-skills/important-api-concepts.md">Важные понятия, касающиеся API</a></li>
                            <li><a href="windows-vision-skills/samples.md">Примеры навыков компьютерного зрения Windows</a></li>
                        </ul>
                    </div>
                </div>
            </div>
        </div>
    </li>
    <li>
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage bgdAccent1">
                            <a href="https://docs.microsoft.com/windows/desktop/direct3d12/dml">
                                <img src="https://docs.microsoft.com/media/hubs/cortana/cortana-resources-samples.svg" alt="DirectML graphic" data-linktype="external" class="x-hidden-focus"/>
                            </a>
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>
                            <a href="https://docs.microsoft.com/windows/desktop/direct3d12/dml">Непосредственное машинное обучение (DirectML)</a>
                        </h3>
                        <p>Реализуйте высокопроизводительные технологии машинного обучения с помощью низкоуровневых интерфейсов API типа DirectX.</p>
                        <br/>
                        <ul>
                            <li><a href="https://docs.microsoft.com/windows/desktop/direct3d12/dml-intro">Введение в DirectML</a></li>
                            <li><a href="https://docs.microsoft.com/windows/desktop/direct3d12/dml-binding">Привязывание в DirectML</a></li>
                            <li><a href="https://docs.microsoft.com/windows/desktop/direct3d12/dml-min-app">Примеры приложений DirectML</a></li>
                        </ul>
                    </div>
                </div>
            </div>
        </div>
    </li>
</ul>

## <a name="which-solution-is-right-for-me"></a>Как найти подходящее решение?

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
