---
title: Важные понятия API
description: Сведения о важных понятиях для API-интерфейса "навыки работы с Windows".
ms.date: 4/25/2019
ms.topic: article
keywords: Windows 10, Windows AI, навыки работы с Windows
ms.localizationpriority: medium
ms.openlocfilehash: af73ceb559129bdb78477b41caa4d3741f78d5f7
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70156299"
---
# <a name="important-api-concepts"></a>Важные понятия API

> [!NOTE]
> Некоторые сведения относятся к предварительной версии продукта, в которую перед коммерческим выпуском могут быть внесены существенные изменения. Майкрософт не дает никаких гарантий, явных или подразумеваемых, в отношении предоставленной здесь информации.

Пространство имен [Microsoft. AI. Skills. скиллинтерфацепревиев](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview) предоставляет набор базовых интерфейсов, которые расширяются всеми навыками, а также классами и вспомогательными методами для реализации навыков в Windows.

Этот API предназначен для упрощения работы навыков и того, как разработчики взаимодействуют с ними. Цель состоит в том, чтобы сделать абстракцию особенности API для логики каждого навыка и использовать, а не интуиция разработчика на широком наборе решений и приложений. Он также предназначен для использования примитивов Windows, которые упрощают взаимодействие с интерфейсами API операционной системы. Это состоит из шаблона, производного от, который стандартизации потока разработки и взаимодействия API во всех навыках.

Поэтому все навыки должны быть реализованы по крайней мере в следующих интерфейсах:

<br/>

| Имя | Описание |
|------|-------------|
| [искиллдескриптор](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskilldescriptor) | Предоставляет сведения о навыке и предоставляет его требования (ввод, вывод, версия и т. д.). Выступает в качестве фабрики для функции [Kill](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskill). |
| [искиллбиндинг](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillbinding) | Служит индексированным контейнером [искиллфеатуре](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillfeature). Он выступает в качестве источника для входных и выходных переменных, передаваемых обратно и назад в функцию [Kill](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskill). Он обрабатывает операции предварительной обработки и последующей обработки входных и выходных данных и упрощает их доступ. |
| [Уничтожить](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskill) | Предоставляет основную логику обработки входных данных и формирование ее выходных данных через [искиллбиндинг](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillbinding). Выступает в качестве фабрики для [искиллбиндинг](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillbinding). |

Навыки предназначены для оптимального использования аппаратных возможностей (ЦП, GPU и т. д.) для каждой системы, на которой они работают. Эти устройства аппаратного ускорения представлены путем наследования интерфейса [искиллексекутиондевице](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillexecutiondevice) , связанного с [скиллексекутиондевицекинд](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.skillexecutiondevicekind). Таким образом, производные [искиллдескриптор](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskilldescriptor) должны найти, отфильтровать и предоставить набор объектов [искиллексекутиондевице](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillexecutiondevice) , доступных в данный момент в системе размещения, которая может выполнять логику [Kill](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskill) .

Это позволит разработчику, использующему пакет навыков, выбрать, как использовать поддерживаемые аппаратные ресурсы во время выполнения в системе пользователя. Некоторые [искиллексекутиондевице](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillexecutiondevice) производные классы уже определены и доступны для удобства ([скиллексекутиондевицекпу](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.skillexecutiondevicecpu) и [скиллексекутиондевицедиректкс](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.skillexecutiondevicedirectx)).

Чтобы гарантировать, что входные и выходные переменные передаются в нужный формат для навыка, определяется интерфейс [искиллфеатуре](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillfeature) . Оно должно инкапсулировать значение в заранее определенном формате. Это значение представлено производным от [искиллфеатуревалуе](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillfeaturevalue), который имеет несколько общих производных, уже определенных и доступных для удобства ([искиллфеатуретенсорвалуе](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillfeaturetensorvalue), [скиллфеатуреимажевалуе](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.skillfeatureimagevalue)и [ Скиллфеатуремапвалуе](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.skillfeaturemapvalue)).

Каждый производный [искиллфеатуревалуе](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillfeaturevalue) имеет соответствующий определенный производный [искиллфеатуредескриптор](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillfeaturedescriptor) , который описывает ожидаемый формат, поддерживаемый навыком ([искиллфеатуретенсордескриптор](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillfeaturetensordescriptor), [ Искиллфеатуреимажедескриптор](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillfeatureimagedescriptor)и [искиллфеатуремапдескриптор](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillfeaturemapdescriptor)). Эти [искиллфеатуредескриптор](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillfeaturedescriptor) производные объекты также играют роль объектов фабрики для объектов [искиллфеатуревалуе](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillfeaturevalue) , которые они описывают.

В момент создания экземпляра, если примитив, используемый для присваивания [искиллфеатуревалуе](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillfeaturevalue) , не соответствует описанию, предоставленному его аналогом [искиллфеатуредескриптор](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillfeaturedescriptor) , автоматическое преобразование, относящееся к каждому типу, может выполняться без проблем (для Например, перекодирование при привязке изображения в другом формате, отличном от требуемого, или обрезка, если пропорции отличаются друг от друга.

## Поток API<a name="APIFlow"></a>

Поскольку все навыки получают один и тот же набор базовых интерфейсов из [Microsoft. AI. Skills. скиллинтерфацепревиев](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview), все они следуют тому же потоку, который обычно сводится к следующим операциям:

<div style="text-align:center" markdown="1">

![Схема потока API-интерфейса для демонстрации Windows, демонстрирующий обычную последовательность вызовов API из приложения, принимающего навык для зрения Windows](../images/vision-skills-flow.png)

</div>

1) Создайте экземпляр производного класса [искиллдескриптор](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskilldescriptor) .

2) Запросите доступные устройства выполнения с помощью экземпляра из шага 1 (с помощью [искиллдескриптор. жетсуппортедексекутиондевицесасинк](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskilldescriptor.getsupportedexecutiondevicesasync)) или пропустите и непосредственно попытайтесь выполнить шаг 3.

3) Создайте экземпляр навыка, используя экземпляр из шага 1 и требуемое устройство выполнения из шага 2 (с помощью [искиллдескриптор. креатескилласинк (искиллексекутиондевице)](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskilldescriptor.createskillasync)) или по умолчанию, принятое разработчиком навыков (с помощью [ Искиллдескриптор. CreateAsync ()](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskilldescriptor.createskillasync)).

4) Создайте экземпляр объекта привязки навыков с помощью экземпляра навыка из шага 3 (с помощью функции [Kill. креатескиллбиндингасинк](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskill.createskillbindingasync)).

5) Получите примитивы ([видеофраме](https://docs.microsoft.com/uwp/api/windows.media.videoframe), [IVectorView](https://docs.microsoft.com/uwp/api/windows.foundation.collections.ivectorview_t_), [IMapView](https://docs.microsoft.com/uwp/api/windows.foundation.collections.imapview_k_v_)и т. д.) из приложения и привяжите их к объекту привязки из шага 4 (путем доступа к соответствующей [искиллфеатуре](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillfeature) с помощью имени и вызова метода [Искиллфеатуре. сетфеатуревалуеасинк (объект)](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillfeature.setfeaturevalueasync)).

6) Выполняйте свои знания по объекту привязки (путем вызова метода [евалуатеасинк](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskill.evaluateasync)).

7) Извлеките выходные примитивы из объекта привязки, созданного на шаге 4 (путем доступа к соответствующему [искиллфеатуре](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillfeature) индексу с помощью его имени и вызова метода получения [искиллфеатуре. феатуревалуе](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillfeature.featurevalue)).

8) Отшлифовка и повторите шаг 5, используя один и тот же объект привязки и новые примитивы.

Чтобы увидеть это в действии, ознакомьтесь с руководством по принятию опыта работы [с Windows из приложения](tutorial1.md).

[!INCLUDE [help](../includes/get-help-vision.md)]
