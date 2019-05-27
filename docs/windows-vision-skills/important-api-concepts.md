---
author: eliotcowley
title: Основные понятия API
description: Изучите важные понятия для API Windows компьютерного зрения навыки.
ms.author: elcowle
ms.date: 4/25/2019
ms.topic: article
keywords: Windows 10, искусственный интеллект windows, windows визуального распознавания навыки
ms.localizationpriority: medium
ms.openlocfilehash: f34b3916c713892e3bd2bbd2f7cd1e7483df6ddb
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66179946"
---
# <a name="important-api-concepts"></a>Основные понятия API

> [!NOTE]
> Некоторая информация имеет отношение к предварительному выпуску продукта, который может быть значительно изменен перед коммерческим выпуском. Майкрософт не дает никаких гарантий, явных или подразумеваемых, в отношении предоставленной здесь информации.

[Microsoft.AI.Skills.SkillInterfacePreview](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview) пространство имен предоставляет набор базовых интерфейсов, чтобы расширить все навыки, а также классы и вспомогательные методы для квалификации разработчиков в Windows.

Этот API предназначен для оптимизировать способ навыки работы и как разработчикам взаимодействовать с ними. Целью является абстрагируют specificities API каждого навыка логики и использовать вместо этого интуиция согласованные разработчика широкий набор решений и приложений. Он также предназначен для использования Windows примитивы, которые упрощают взаимодействие с API операционной системы. Это представляет собой шаблон для наследования от, стандартизирует потоком разработчика и API взаимодействия через все навыки.

Таким образом все навыки, должны быть реализованы по крайней мере следующие интерфейсы:

<br/>

| Имя | Описание |
|------|-------------|
| [ISkillDescriptor](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskilldescriptor) | Предоставляет сведения о навыках и предоставляет ее требования (ввод, вывод, версии, и т.д.). Выступает в качестве фабрики для [ISkill](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskill). |
| [ISkillBinding](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillbinding) | Служит в качестве индексированных контейнер [ISkillFeature](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillfeature). Он действует в качестве канала для входных и выходных переменных для передачи туда и обратно к [ISkill](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskill). Он обрабатывает предварительной обработки и постобработки входных и выходных данных и упрощает их доступ. |
| [ISkill](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskill) | Предоставляет основную логику обработки входных данных и формирует его выходных данных с помощью [ISkillBinding](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillbinding). Выступает в качестве фабрики для [ISkillBinding](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillbinding). |

Навыки предназначены для оптимально использовать возможности оборудования (ЦП, GPU и т.д.) каждой системы, в которой они выполняются. Эти устройства аппаратного ускорения представляются путем наследования [ISkillExecutionDevice](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillexecutiondevice) интерфейса, связанного с [SkillExecutionDeviceKind](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.skillexecutiondevicekind). Таким образом [ISkillDescriptor](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskilldescriptor) производные нужно найти, фильтровать и предоставляют набор [ISkillExecutionDevice](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillexecutiondevice) объектов, доступных в системе узла, который может выполнить [ ISkill](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskill) логики.

Таким образом, что разработчик, использующие пакет навыков наиболее выбрать способ задействуйте поддерживаемых аппаратных ресурсов на компьютере пользователя во время выполнения. Существуют некоторые [ISkillExecutionDevice](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillexecutiondevice) производные классы уже определенные и доступные для удобства ([SkillExecutionDeviceCPU](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.skillexecutiondevicecpu) и [SkillExecutionDeviceDirectX](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.skillexecutiondevicedirectx)).

Чтобы убедиться, что входные и выходные переменные передаются в правильном формате навыка, [ISkillFeature](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillfeature) определенный интерфейс. Он предназначен для инкапсуляции значение в предопределенном формате. Это значение, представленное, производный от [ISkillFeatureValue](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillfeaturevalue), который имеет несколько распространенных производные, уже определенные и доступные для удобства ([ISkillFeatureTensorValue](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillfeaturetensorvalue), [ SkillFeatureImageValue](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.skillfeatureimagevalue), и [SkillFeatureMapValue](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.skillfeaturemapvalue)).

Каждый [ISkillFeatureValue](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillfeaturevalue) производных имеет соответствующий [ISkillFeatureDescriptor](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillfeaturedescriptor) производных определенные, описывающий ожидаемый формат, поддерживаемый этим навыком ([ ISkillFeatureTensorDescriptor](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillfeaturetensordescriptor), [ISkillFeatureImageDescriptor](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillfeatureimagedescriptor), и [ISkillFeatureMapDescriptor](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillfeaturemapdescriptor)). Эти [ISkillFeatureDescriptor](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillfeaturedescriptor) производные также выступать в качестве фабрики объектов для [ISkillFeatureValue](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillfeaturevalue) объекты, они описывают.

Во время создания экземпляра, если примитив используется для присвоения [ISkillFeatureValue](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillfeaturevalue) не соответствует описанию, предоставленному с его [ISkillFeatureDescriptor](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillfeaturedescriptor) какой, автоматическое преобразование определенных для каждого типа может произойти без проблем (например, перекодировка при привязке изображения в другом формате, чем требуется, или обрезки, если пропорции отличаются).

## API потока <a name="APIFlow"></a>

Поскольку все навыки, являются производными тот же набор базовых интерфейсов из [Microsoft.AI.Skills.SkillInterfacePreview](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview), все они следуют тому же потоку, который обычно сводится к следующим операциям:

<div style="text-align:center" markdown="1">

![Схема потока API навыков компьютерного зрения для Windows, с отображением стандартную последовательность вызовов API из приложения приема навык концепции Windows](../images/vision-skills-flow.png)

</div>

1) Создать экземпляр [ISkillDescriptor](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskilldescriptor) производных продуктов.

2) Запрос имеющихся вычислительных устройств, используя экземпляр из шага 1 (с помощью [ISkillDescriptor.GetSupportedExecutionDevicesAsync](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskilldescriptor.getsupportedexecutiondevicesasync)) или пропустить и напрямую попытки шаг 3.

3) Создать экземпляр навык, используя экземпляр из шага 1 и устройство нужный выполнения из шага 2 (с помощью [ISkillDescriptor.CreateSkillAsync(ISkillExecutionDevice)](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskilldescriptor.createskillasync)) или значение по умолчанию один этот вопрос будет решен разработчиком навыков (с помощью [ ISkillDescriptor.CreateAsync()](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskilldescriptor.createskillasync)).

4) Создание экземпляра объекта привязки навыков с помощью экземпляра навыков из шага 3 (с помощью [ISkill.CreateSkillBindingAsync](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskill.createskillbindingasync)).

5) Получить свои примитивы ([VideoFrame](https://docs.microsoft.com/uwp/api/windows.media.videoframe), [IVectorView](https://docs.microsoft.com/uwp/api/windows.foundation.collections.ivectorview_t_), [IMapView](https://docs.microsoft.com/uwp/api/windows.foundation.collections.imapview_k_v_)т. д.) из вашего приложения и привязки их объект привязки из шага 4 (путем доступа к соответствующий [ISkillFeature](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillfeature) индексированных с помощью имени и при вызове метода [ISkillFeature.SetFeatureValueAsync(Object)](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillfeature.setfeaturevalueasync)).

6) Работа вашей квалификации через объект привязки (путем вызова [ISkill.EvaluateAsync](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskill.evaluateasync)).

7) Получить свои примитивы выходные данные из объекта binding создан на шаге 4 (, обратившись к соответствующему [ISkillFeature](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillfeature) индексированных с помощью имени и вызов метода получения [ISkillFeature.FeatureValue](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillfeature.featurevalue)).

8) Прополощите и повторите шаг 5. Использование одного объекта привязки и новых примитивов.

Чтобы увидеть это в действии, см. в руководстве о массовом получении [навыков концепции Windows из приложения](tutorial1.md).

[!INCLUDE [help](../includes/get-help-vision.md)]
