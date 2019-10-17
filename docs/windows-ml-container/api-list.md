---
title: Список API
description: Изучите API-интерфейсы список разрешений для использования в контейнере Windows ML
ms.date: 10/14/2019
ms.topic: article
keywords: windows 10, контейнер Windows ML, контейнер, Интернет вещей, Edge
ms.localizationpriority: medium
ms.openlocfilehash: 6567256c71feb0f110cfac71ed239efac3037add
ms.sourcegitcommit: e08b8ae92e48c1b82bb6f94fefcb32cd817453d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72443014"
---
# <a name="api-list"></a>Список API

API-интерфейсы, экспортированные [библиотекой "OneCore. lib](https://docs.microsoft.com/windows/win32/apiindex/umbrella-lib-onecore) ", доступны для собственных приложений в контейнере Windows ml.

Из-за небольшого размера контейнера машинного обучения Windows в образе контейнера доступны только подмножество API-интерфейсов WinRT.  Приведенный ниже список предназначен для исчерпывающего перечисления типов, включенных в базовый образ ОС.  Если требуется тип, который не включается, отправьте сообщение электронной почты winmlcfb@microsoft.com.

## <a name="windowsai"></a>Windows.AI

### <a name="windowsaimachinelearninghttpsdocsmicrosoftcomuwpapiwindowsaimachinelearning"></a>[Windows.AI.MachineLearning](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning)

ILearningModelFeatureDescriptor </br> ILearningModelFeatureValue </br> ILearningModelOperatorProvider </br> ITensor </br> ImageFeatureDescriptor </br> ImageFeatureValue </br> LearningModel </br> LearningModelBinding </br> LearningModelDevice </br> LearningModelDeviceKind </br> LearningModelEvaluationResult </br> LearningModelFeatureKind </br> LearningModelSession </br> LearningModelSessionOptions </br> мачинелеарнингконтракт </br> MapFeatureDescriptor </br> SequenceFeatureDescriptor </br> TensorBoolean </br> TensorDouble </br> TensorFeatureDescriptor </br> TensorFloat </br> TensorFloat16Bit </br> TensorInt16Bit </br> TensorInt32Bit </br> TensorInt64Bit </br> TensorInt8Bit </br> TensorKind </br> TensorString </br> TensorUInt16Bit </br> TensorUInt32Bit </br> TensorUInt64Bit </br> TensorUInt8Bit

## <a name="windowsapplicationmodel"></a>Windows.ApplicationModel

### <a name="windowsapplicationmodelbackgroundhttpsdocsmicrosoftcomuwpapiwindowsapplicationmodelbackground"></a>[Windows.ApplicationModel.Background](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Background)

девицеватчертригжер </br> ибаккграундтригжер

## <a name="windowsdata"></a>Windows.Data

### <a name="windowsdatahtmlhttpsdocsmicrosoftcomuwpapiwindowsdatahtml"></a>[Windows. Data. HTML](https://docs.microsoft.com/uwp/api/Windows.Data.Html)

хтмлутилитиес

### <a name="windowsdatajsonhttpsdocsmicrosoftcomuwpapiwindowsdatajson"></a>[Windows. Data. JSON](https://docs.microsoft.com/uwp/api/Windows.Data.Json)

ижсонвалуе </br> жсонаррай </br> жсонеррор </br> жсонеррорстатус </br> JsonObject </br> жсонвалуе </br> жсонвалуетипе

### <a name="windowsdatatexthttpsdocsmicrosoftcomuwpapiwindowsdatatext"></a>[Windows.Data.Text](https://docs.microsoft.com/uwp/api/Windows.Data.Text)

алтернатенормализатионформат </br> алтернатевордформ </br> селектаблевордсегмент </br> селектаблевордсегментстокенизингхандлер </br> селектаблевордссегментер </br> семантиктексткуери </br> текстконверсионженератор </br> текстфонеме </br> текстпредиктионженератор </br> TextPredictionOptions </br> текстреверсеконверсионженератор </br> текстсегмент </br> уникодечарактерс </br> уникодеженералкатегори </br> уникоденумериктипе </br> вордсегмент </br> вордсегментстокенизингхандлер </br> вордссегментер

### <a name="windowsdataxmldomhttpsdocsmicrosoftcomuwpapiwindowsdataxmldom"></a>[Windows. Data. XML. DOM](https://docs.microsoft.com/uwp/api/Windows.Data.Xml.Dom)

дтдентити </br> дтднотатион </br> иксмлчарактердата </br> иксмлноде </br> иксмлнодеселектор </br> иксмлнодесериализер </br> Иксмлтекст br > NodeType </br> XmlAttribute </br> ксмлкдатасектион </br> ксмлкоммент </br> XmlDocument </br> XmlDocumentFragment </br> XmlDocumentType </br> ксмлдомимплементатион </br> XmlElement </br> XmlEntityReference </br> ксмллоадсеттингс </br> XmlNamedNodeMap </br> Объекте </br> XmlProcessingInstruction </br> XmlText

### <a name="windowsdataxmlxslhttpsdocsmicrosoftcomuwpapiwindowsdataxmlxsl"></a>[Windows. Data. XML. xsl](https://docs.microsoft.com/uwp/api/Windows.Data.Xml.Xsl)

XsltProcessor

## <a name="windowsdevices"></a>Windows.Devices

### <a name="windowsdeviceshttpsdocsmicrosoftcomuwpapiwindowsdevices"></a>[Windows. Devices](https://docs.microsoft.com/uwp/api/windows.devices)

иловлевелдевицесаггрегатепровидер </br> ловлевелдевицесаггрегатепровидер </br> ловлевелдевицесконтроллер

### <a name="windowsdevicesadchttpsdocsmicrosoftcomuwpapiwindowsdevicesadc"></a>[Windows. Devices. ADC](https://docs.microsoft.com/uwp/api/windows.devices.adc)

адкчаннел </br> адкчаннелмоде </br> адкконтроллер

### <a name="windowsdevicesadcproviderhttpsdocsmicrosoftcomuwpapiwindowsdevicesadcprovider"></a>[Windows. Devices. ADC. Provider](https://docs.microsoft.com/uwp/api/windows.devices.adc.provider)

провидерадкчаннелмоде

### <a name="windowsdevicesbackgroundhttpsdocsmicrosoftcomuwpapiwindowsdevicesbackground"></a>[Windows. Devices. Background](https://docs.microsoft.com/uwp/api/windows.devices.background)

девицесервиЦингдетаилс </br> девицеуседетаилс

### <a name="windowsdevicesbluetoothhttpsdocsmicrosoftcomuwpapiwindowsdevicesbluetooth"></a>[Windows. Devices. Bluetooth](https://docs.microsoft.com/uwp/api/Windows.Devices.Bluetooth)

блуетусадаптер </br> блуетусаддресстипе </br> блуетускачемоде </br> блуетусклассофдевице </br> блуетусконнектионстатус </br> блуетусдевице </br> блуетусдевицеид </br> блуетусеррор </br> блуетуслеаппеаранце </br> блуетуслеаппеаранцекатегориес </br> блуетуслеаппеаранцесубкатегориес </br> блуетуследевице </br> блуетусмажоркласс </br> блуетусминоркласс </br> блуетуссервицекапабилитиес </br> блуетуссигналстренгсфилтер </br> блуетусууидхелпер

### <a name="windowsdevicesbluetoothadvertisementhttpsdocsmicrosoftcomuwpapiwindowsdevicesbluetoothadvertisement"></a>[Windows. Devices. Bluetooth. Advertisement](https://docs.microsoft.com/uwp/api/Windows.Devices.Bluetooth.Advertisement)

блуетуслеадвертисемент </br> блуетуслеадвертисементбитепаттерн </br> блуетуслеадвертисементдатасектион </br> блуетуслеадвертисементдататипес </br> блуетуслеадвертисементфилтер </br> блуетуслеадвертисементфлагс </br> блуетуслеадвертисементпублишер </br> блуетуслеадвертисементпублишерстатус </br> блуетуслеадвертисементпублишерстатусчанжедевентаргс </br> блуетуслеадвертисементрецеиведевентаргс </br> блуетуслеадвертисементтипе </br> блуетуслеадвертисементватчер </br> блуетуслеадвертисементватчерстатус </br> блуетуслеадвертисементватчерстоппедевентаргс </br> блуетуслемануфактурердата </br> блуетуслесканнингмоде

### <a name="windowsdevicesbluetoothbackgroundhttpsdocsmicrosoftcomuwpapiwindowsdevicesbluetoothbackground"></a>[Windows. Devices. Bluetooth. Background](https://docs.microsoft.com/uwp/api/Windows.Devices.Bluetooth.Background)

блуетусевенттригжерингмоде </br> блуетуслеадвертисементпублишертригжердетаилс </br> блуетуслеадвертисементватчертригжердетаилс </br> гаттчарактеристикнотификатионтригжердетаилс </br> гаттсервицепровидерконнектион </br> гаттсервицепровидертригжердетаилс </br> рфкоммконнектионтригжердетаилс </br> рфкомминбаундконнектионинформатион </br> рфкоммаутбаундконнектионинформатион

### <a name="windowsdevicesbluetoothgenericattributeprofilehttpsdocsmicrosoftcomuwpapiwindowsdevicesbluetoothgenericattributeprofile"></a>[Windows.Devices.Bluetooth.GenericAttributeProfile](https://docs.microsoft.com/uwp/api/Windows.Devices.Bluetooth.GenericAttributeProfile)

гаттчарактеристик </br> гаттчарактеристикпропертиес </br> гаттчарактеристикууидс </br> гаттчарактеристиксресулт </br> гаттклиентчарактеристикконфигуратиондескрипторвалуе </br> гаттклиентнотификатионресулт </br> гатткоммуникатионстатус </br> гаттдескриптор </br> гаттдескрипторууидс </br> гаттдескрипторсресулт </br> гаттдевицесервице </br> гаттдевицесервицесресулт </br> гаттлокалчарактеристик </br> гаттлокалчарактеристикпараметерс </br> гаттлокалчарактеристикресулт </br> гаттлокалдескриптор </br> гаттлокалдескрипторпараметерс </br> гаттлокалдескрипторресулт </br> гаттлокалсервице </br> гаттопенстатус </br> гаттпресентатионформат </br> гаттпресентатионформаттипес </br> гаттпротектионлевел </br> гаттпротоколеррор </br> гаттреадклиентчарактеристикконфигуратиондескрипторресулт </br> гаттреадрекуест </br> гаттреадрекуестедевентаргс </br> гаттреадресулт </br> гаттрелиаблевритетрансактион </br> гаттрекуестстате </br> гаттрекуестстатечанжедевентаргс </br> гаттсервицепровидер </br> гаттсервицепровидерадвертисементстатус </br> гаттсервицепровидерадвертисементстатусчанжедевентаргс </br> гаттсервицепровидерадвертисингпараметерс </br> гаттсервицепровидерресулт </br> гаттсервицеууидс </br> гаттсессион </br> гаттсессионстатус </br> гаттсессионстатусчанжедевентаргс </br> гаттшарингмоде </br> гаттсубскрибедклиент </br> гаттвалуечанжедевентаргс </br> гаттвритеоптион </br> гаттвритерекуест </br> гаттвритерекуестедевентаргс </br> гаттвритересулт

### <a name="windowsdevicesbluetoothrfcommhttpsdocsmicrosoftcomuwpapiwindowsdevicesbluetoothrfcomm"></a>[Windows. Devices. Bluetooth. RFCOMM](https://docs.microsoft.com/uwp/api/Windows.Devices.Bluetooth.Rfcomm)

рфкоммдевицесервице </br> рфкоммдевицесервицесресулт </br> рфкоммсервицеид </br> рфкоммсервицепровидер

### <a name="windowsdevicescustomhttpsdocsmicrosoftcomuwpapiwindowsdevicescustom"></a>[Windows. Devices. Custom](https://docs.microsoft.com/uwp/api/Windows.Devices.Custom)

кустомдевице </br> кустомдевицеконтракт </br> девицеакцессмоде </br> девицешарингмоде </br> иоконтролкоде </br> кновндевицетипес

### <a name="windowsdevicesenumerationhttpsdocsmicrosoftcomuwpapiwindowsdevicesenumeration"></a>[Windows.Devices.Enumeration](https://docs.microsoft.com/uwp/api/Windows.Devices.Enumeration)

девицеакцессчанжедевентаргс </br> девицеакцессинформатион </br> девицеакцессстатус </br> DeviceClass </br> девицеконнектиончанжетригжердетаилс </br> девицедисконнектбуттонкликкедевентаргс </br> DeviceInformation </br> девицеинформатионколлектион </br> девицеинформатионкустомпаиринг </br> девицеинформатионкинд </br> девицеинформатионпаиринг </br> девицеинформатионупдате </br> девицепаирингкиндс </br> девицепаирингпротектионлевел </br> девицепаирингрекуестедевентаргс </br> девицепаирингресулт </br> девицепаирингресултстатус </br> девицепиккердисплайстатусоптионс </br> девицепиккерфилтер </br> девицеселектедевентаргс </br> девицесумбнаил </br> девицеунпаирингресулт </br> девицеунпаирингресултстатус </br> девицеватчер </br> девицеватчеревент </br> девицеватчеревенткинд </br> девицеватчерстатус </br> девицеватчертригжердетаилс </br> енклосурелокатион </br> идевицепаирингсеттингс </br> Панель

### <a name="windowsdevicesenumerationpnphttpsdocsmicrosoftcomuwpapiwindowsdevicesenumerationpnp"></a>[Windows. Devices. Enumeration. PnP](https://docs.microsoft.com/uwp/api/Windows.Devices.Enumeration.Pnp)

пнпобжект </br> пнпобжектколлектион </br> пнпобжекттипе </br> пнпобжектупдате </br> пнпобжектватчер

### <a name="windowsdevicesgpiohttpsdocsmicrosoftcomuwpapiwindowsdevicesgpio"></a>[Windows. Devices. GPIO](https://docs.microsoft.com/uwp/api/Windows.Devices.Gpio)

гпиочанжекаунт </br> гпиочанжекаунтер </br> гпиочанжеполарити </br> гпиочанжереадер </br> гпиочанжерекорд </br> гпиоконтроллер </br> гпиупенстатус </br> гпиопин </br> гпиопиндривемоде </br> гпиопинедже </br> гпиопинвалуе </br> гпиопинвалуечанжедевентаргс </br> гпиошарингмоде

### <a name="windowsdevicesgpioproviderhttpsdocsmicrosoftcomuwpapiwindowsdevicesgpioprovider"></a>[Windows. Devices. GPIO. Provider](https://docs.microsoft.com/uwp/api/Windows.Devices.Gpio.Provider)

гпиопинпровидервалуечанжедевентаргс </br> игпиоконтроллерпровидер </br> игпиопинпровидер </br> игпиопровидер </br> провидергпиопиндривемоде </br> провидергпиопинедже </br> провидергпиопинвалуе </br> провидергпиошарингмоде

### <a name="windowsdeviceshumaninterfacedevicehttpsdocsmicrosoftcomuwpapiwindowsdeviceshumaninterfacedevice"></a>[Windows. Devices. Хуманинтерфацедевице](https://docs.microsoft.com/uwp/api/Windows.Devices.HumanInterfaceDevice)

хидбулеанконтрол </br> хидбулеанконтролдескриптион </br> хидколлектион </br> хидколлектионтипе </br> хиддевице </br> хидфеатуререпорт </br> хидинпутрепорт </br> хидинпутрепортрецеиведевентаргс </br> хиднумерикконтрол </br> хиднумерикконтролдескриптион </br> хидаутпутрепорт </br> хидрепорттипе

### <a name="windowsdevicesi2chttpsdocsmicrosoftcomuwpapiwindowsdevicesi2c"></a>[Windows. Devices. I2C](https://docs.microsoft.com/uwp/api/Windows.Devices.I2c)

I2cBusSpeed </br> I2cConnectionSettings </br> I2cController </br> I2cDevice </br> I2cSharingMode </br> I2cTransferResult </br> I2cTransferStatus </br> II2cDeviceStatics

### <a name="windowsdevicesi2cproviderhttpsdocsmicrosoftcomuwpapiwindowsdevicesi2cprovider"></a>[Windows. Devices. I2C. Provider](https://docs.microsoft.com/uwp/api/Windows.Devices.I2c.Provider)

II2cControllerProvider </br> II2cDeviceProvider </br> II2cProvider </br> ProviderI2cBusSpeed </br> ProviderI2cConnectionSettings </br> ProviderI2cSharingMode </br> ProviderI2cTransferResult </br> ProviderI2cTransferStatus

### <a name="windowsdevicespowerhttpsdocsmicrosoftcomuwpapiwindowsdevicespower"></a>[Windows. Devices. Power](https://docs.microsoft.com/uwp/api/Windows.Devices.Power)

"Батарея" </br> баттерирепорт

### <a name="windowsdevicespwmhttpsdocsmicrosoftcomuwpapiwindowsdevicespwm"></a>[Windows. Devices. модулятор](https://docs.microsoft.com/uwp/api/Windows.Devices.Pwm)

пвмконтроллер </br> пвмпин </br> пвмпулсеполарити

### <a name="windowsdevicespwmproviderhttpsdocsmicrosoftcomuwpapiwindowsdevicespwmprovider"></a>[Windows. Devices. модулятор. Provider](https://docs.microsoft.com/uwp/api/Windows.Devices.Pwm.Provider)

ипвмконтроллерпровидер </br> ипвмпровидер

### <a name="windowsdevicesradioshttpsdocsmicrosoftcomuwpapiwindowsdevicesradios"></a>[Windows. Devices. Радио](https://docs.microsoft.com/uwp/api/Windows.Devices.Radios)

Помех </br> радиоакцессстатус </br> радиокинд </br> радиостате

### <a name="windowsdevicessensorshttpsdocsmicrosoftcomuwpapiwindowsdevicessensors"></a>[Windows.Devices.Sensors](https://docs.microsoft.com/uwp/api/Windows.Devices.Sensors)

Accelerometer (акселерометр) </br> акцелерометердатасрешолд </br> акцелерометерреадинг </br> акцелерометерреадингчанжедевентаргс </br> акцелерометерреадингтипе </br> акцелерометершакеневентаргс </br> активитисенсор </br> активитисенсорреадинг </br> активитисенсорреадингчанжерепорт </br> активитисенсорреадингчанжедевентаргс </br> активитисенсорреадингконфиденце </br> активитисенсортригжердетаилс </br> ActivityType </br> Высотометр </br> алтиметерреадинг </br> алтиметерреадингчанжедевентаргс </br> Барометр </br> барометердатасрешолд </br> барометерреадинг </br> барометерреадингчанжедевентаргс </br> Compass (компас) </br> компассдатасрешолд </br> компассреадинг </br> компассреадингчанжедевентаргс </br> Gyrometer (гирометр) </br> гирометердатасрешолд </br> гирометерреадинг </br> гирометерреадингчанжедевентаргс </br> хинжеанглереадинг </br> хинжеанглесенсор </br> хинжеанглесенсорреадингчанжедевентаргс </br> исенсордатасрешолд </br>  Инклинометр </br> инклинометердатасрешолд </br> инклинометерреадинг </br> инклинометерреадингчанжедевентаргс </br> LightSensor </br> лигхтсенсордатасрешолд </br> лигхтсенсорреадинг </br> лигхтсенсорреадингчанжедевентаргс </br> Магнитометр </br> магнетометераккураци </br> магнетометердатасрешолд </br> магнетометерреадинг </br> магнетометерреадингчанжедевентаргс </br> OrientationSensor </br> ориентатионсенсорреадинг </br> ориентатионсенсорреадингчанжедевентаргс </br> Шагомер </br> педометердатасрешолд </br> педометерреадинг </br> педометерреадингчанжедевентаргс </br> педометерстепкинд </br> проксимитисенсор </br> проксимитисенсордатасрешолд </br> проксимитисенсордисплайоноффконтроллер </br> проксимитисенсорреадинг </br> проксимитисенсорреадингчанжедевентаргс </br> сенсордатасрешолдтригжердетаилс </br> сенсороптимизатионгоал </br> сенсоркуатернион </br> сенсорреадингтипе </br> сенсорротатионматрикс </br> сенсортипе </br> SimpleOrientation </br> симплеориентатионсенсор </br> симплеориентатионсенсорориентатиончанжедевентаргс

### <a name="windowsdevicessensorscustomhttpsdocsmicrosoftcomuwpapiwindowsdevicessensorscustom"></a>[Windows. Devices. Sensors. Custom](https://docs.microsoft.com/uwp/api/Windows.Devices.Sensors.Custom)

кустомсенсор </br> кустомсенсорреадинг </br> кустомсенсорреадингчанжедевентаргс

### <a name="windowsdevicesserialcommunicationhttpsdocsmicrosoftcomuwpapiwindowsdevicesserialcommunication"></a>[Windows. Devices. Сериалкоммуникатион](https://docs.microsoft.com/uwp/api/Windows.Devices.SerialCommunication)

ерроррецеиведевентаргс </br> пинчанжедевентаргс </br> сериалдевице </br> сериалеррор </br> сериалхандшаке </br> сериалпарити </br> сериалпинчанже </br> сериалстопбиткаунт

### <a name="windowsdevicesspihttpsdocsmicrosoftcomuwpapiwindowsdevicesspi"></a>[Windows. Devices. SPI](https://docs.microsoft.com/uwp/api/Windows.Devices.Spi)

испидевицестатикс </br> спибусинфо </br> спиконнектионсеттингс </br> спиконтроллер </br> спидевице </br> спимоде </br> спишарингмоде

### <a name="windowsdevicesspiproviderhttpsdocsmicrosoftcomuwpapiwindowsdevicesspiprovider"></a>[Windows. Devices. SPI. Provider](https://docs.microsoft.com/uwp/api/Windows.Devices.Spi.Provider)

испиконтроллерпровидер </br> испидевицепровидер </br> испипровидер </br> провидерспиконнектионсеттингс </br> провидерспимоде </br> провидерспишарингмоде

### <a name="windowsdevicesusbhttpsdocsmicrosoftcomuwpapiwindowsdevicesusb"></a>[Windows. Devices. USB](https://docs.microsoft.com/uwp/api/Windows.Devices.Usb)

усббулкинендпоинтдескриптор </br> усббулкинпипе </br> усббулкаутендпоинтдескриптор </br> усббулкаутпипе </br> усбконфигуратион </br> усбконфигуратиондескриптор </br> усбконтролреЦипиент </br> усбконтролрекуесттипе </br> усбконтролтрансфертипе </br> усбдескриптор </br> усбдевице </br> усбдевицекласс </br> усбдевицеклассес </br> усбдевицедескриптор </br> усбендпоинтдескриптор </br> усбендпоинттипе </br> усбинтерфаце </br> усбинтерфацедескриптор </br> усбинтерфацесеттинг </br> усбинтерруптинендпоинтдескриптор </br> усбинтерруптиневентаргс </br> усбинтерруптинпипе </br> усбинтерруптаутендпоинтдескриптор </br> усбинтерруптаутпипе </br> усбреадоптионс </br> усбсетуппаккет </br> усбтрансфердиректион </br> усбвритеоптионс

### <a name="windowsdeviceswifihttpsdocsmicrosoftcomuwpapiwindowsdeviceswifi"></a>[Windows. Devices. Wi-Fi](https://docs.microsoft.com/uwp/api/Windows.Devices.WiFi)

вифиакцессстатус </br> вифиадаптер </br> вифиаваилабленетворк </br> вификоннектионмесод </br> вификоннектионресулт </br> вификоннектионстатус </br> вифинетворккинд </br> вифинетворкрепорт </br> вифификинд </br> вифиреконнектионкинд </br> вифивпсконфигуратионресулт </br> вифивпсконфигуратионстатус </br> вифивпскинд

## <a name="windowsfoundation"></a>Windows.Foundation

### <a name="windowsfoundationhttpsdocsmicrosoftcomuwpapiwindowsfoundation"></a>[Windows.Foundation](https://docs.microsoft.com/uwp/api/Windows.Foundation)

асинкактионкомплетедхандлер </br> асинкактионпрогресшандлер </br> асинкактионвиспрогресскомплетедхандлер </br> асинкоператионкомплетедхандлер </br> асинкоператионпрогресшандлер </br> асинкоператионвиспрогресскомплетедхандлер </br> асинкстатус </br> DateTime </br> Разницы </br> деферралкомплетедхандлер </br> EventHandler </br> EventRegistrationToken </br> фаундатионконтракт </br> GuidHelper </br> HResult </br> IAsyncAction </br> IAsyncActionWithProgress </br> иасинЦинфо </br> IAsyncOperationWithProgress </br> IAsyncOperation </br> IClosable </br> ижетактиватионфактори </br> имеморибуффер </br> имеморибуфферреференце </br> IPropertyValue </br> иреференцеаррай </br> IReference </br> IStringable </br> ивввформурлдекодерентри </br> Параметр memorybuffer </br> отчетов </br> PropertyType </br> PropertyValue </br> Rect </br> Size (Размер) </br> TimeSpan </br> TypedEventHandler </br> универсалапиконтракт </br> Универсальный код ресурса (URI) </br> вввформурлдекодер </br> вввформурлдекодерентри

### <a name="windowsfoundationcollectionshttpsdocsmicrosoftcomuwpapiwindowsfoundationcollections"></a>[Windows. Foundation. Collections](https://docs.microsoft.com/uwp/api/Windows.Foundation.Collections)

коллектиончанже </br> иитерабле </br> иитератор </br> IKeyValuePair </br> имапчанжедевентаргс </br> IMapView </br> Ошибоч </br> IObservableMap </br> иобсерваблевектор </br> ипропертисет </br> ивекторчанжедевентаргс </br> IVectorView </br> IVector </br> мапчанжедевенсандлер </br> PropertySet </br> стрингмап </br> ValueSet </br> VectorChangedEventHandler

### <a name="windowsfoundationdiagnosticshttpsdocsmicrosoftcomuwpapiwindowsfoundationdiagnostics"></a>[Windows. Foundation. Diagnostics](https://docs.microsoft.com/uwp/api/Windows.Foundation.Diagnostics)

асинккаусалититрацер </br> каусалитирелатион </br> каусалитисаурце </br> каусалитисинчронаусворк </br> каусалититрацелевел </br> ErrorDetails </br> ерророптионс </br> филелоггингсессион </br> иерроррепортингсеттингс </br> ифилелоггингсессион </br> илоггингчаннел </br> илоггингсессион </br> илоггингтаржет </br> логфилеженератедевентаргс </br> логгингактивити </br> LoggingChannel </br> логгингчаннелоптионс </br> логгингфиелдформат </br> логгингфиелдс </br> LoggingLevel </br> логгингопкоде </br> логгингоптионс </br> логгингсессион </br> рунтимеброкереррорсеттингс </br> траЦингстатусчанжедевентаргс

### <a name="windowsfoundationmetadatahttpsdocsmicrosoftcomuwpapiwindowsfoundationmetadata"></a>[Windows. Foundation. Metadata](https://docs.microsoft.com/uwp/api/Windows.Foundation.Metadata)

активатаблеаттрибуте </br> алловфорвебаттрибуте </br> алловмултиплеаттрибуте </br> апиконтрактаттрибуте </br> апиинформатион </br> аттрибутенамеаттрибуте </br> AttributeTargets </br> AttributeUsageAttribute </br> компосаблеаттрибуте </br> компоситионтипе </br> контрактверсионаттрибуте </br> креатефромстрингаттрибуте </br> дефаултаттрибуте </br> DefaultOverloadAttribute </br> DeprecatedAttribute </br> DeprecationType </br> дуалапипартитионаттрибуте </br> ексклусиветоаттрибуте </br> експерименталаттрибуте </br> фастабиаттрибуте </br> FeatureAttribute» </br> феатурестаже </br> гкпрессуреамаунт </br> гкпрессуреаттрибуте </br> GuidAttribute </br> хасвариантаттрибуте </br> интерналаттрибуте </br> ленгсисаттрибуте </br> MarshalingBehaviorAttribute </br> маршалингтипе </br> метадатамаршалаттрибуте </br> мусеаттрибуте </br> ноексцептионаттрибуте </br> оверлоадаттрибуте </br> оверридаблеаттрибуте </br> Платформа </br> платформаттрибуте </br> превиаусконтрактверсионаттрибуте </br> протектедаттрибуте </br> ранжеаттрибуте </br> ремотеасинкаттрибуте </br> статикаттрибуте </br> среадингаттрибуте </br> ThreadingModel </br> вариантаттрибуте </br> версионаттрибуте </br> вебхоссидденаттрибуте

### <a name="windowsfoundationnumericshttpsdocsmicrosoftcomuwpapiwindowsfoundationnumerics"></a>[Windows. Foundation. Numerics](https://docs.microsoft.com/uwp/api/Windows.Foundation.Numerics)

Matrix3x2 </br> Matrix4x4 </br> Плоскости </br> Quaternion </br> Основной </br> Vector2 </br> Vector3 </br> Vector4

## <a name="windowsglobalization"></a>Windows.Globalization

### <a name="windowsglobalizationhttpsdocsmicrosoftcomuwpapiwindowsglobalization"></a>[Windows.Globalization](https://docs.microsoft.com/uwp/api/Windows.Globalization)

аппликатионлангуажес </br> Calendar </br> календаридентифиерс </br> клоккидентифиерс </br> CurrencyAmount </br> курренциидентифиерс </br> DayOfWeek </br> GeographicRegion </br> "Язык" </br> лангуажелайаутдиректион </br> нумералсистемидентифиерс

### <a name="windowsglobalizationcollationhttpsdocsmicrosoftcomuwpapiwindowsglobalizationcollation"></a>[Windows. Globalization. Collation](https://docs.microsoft.com/uwp/api/Windows.Globalization.Collation)

чарактерграупинг </br> чарактерграупингс

### <a name="windowsglobalizationdatetimeformattinghttpsdocsmicrosoftcomuwpapiwindowsglobalizationdatetimeformatting"></a>[Windows. Globalization. Датетимеформаттинг](https://docs.microsoft.com/uwp/api/Windows.Globalization.DateTimeFormatting)

DateTimeFormatter </br> дайформат </br> DayOfWeekFormat </br> хаурформат </br> минутеформат </br> монсформат </br> секондформат </br> еарформат

### <a name="windowsglobalizationnumberformattinghttpsdocsmicrosoftcomuwpapiwindowsglobalizationnumberformatting"></a>[Windows. Globalization. Нумберформаттинг](https://docs.microsoft.com/uwp/api/Windows.Globalization.NumberFormatting)

курренциформаттер </br> курренциформаттермоде </br> деЦималформаттер </br> инумберформаттер </br> INumberFormatter2 </br> инумберформаттероптионс </br> инумберпарсер </br> инумберраундер </br> инумберраундероптион </br> исигнедзеруптион </br> исигнификантдигитсоптион </br> инкрементнумберраундер </br> нумералсистемтранслатор </br> перцентформаттер </br> пермиллеформаттер </br> раундингалгорисм </br> сигнификантдигитснумберраундер

### <a name="windowsglobalizationphonenumberformattinghttpsdocsmicrosoftcomuwpapiwindowsglobalizationphonenumberformatting"></a>[Windows. Globalization. Фоненумберформаттинг](https://docs.microsoft.com/uwp/api/Windows.Globalization.PhoneNumberFormatting)

фоненумберформат </br> фоненумберформаттер </br> фоненумберинфо </br> фоненумберматчресулт </br> фоненумберпарсересулт </br> предиктедфоненумберкинд

## <a name="windowsgraphics"></a>Windows.Graphics

### <a name="windowsgraphicshttpsdocsmicrosoftcomuwpapiwindowsgraphics"></a>[Windows. Graphics](https://docs.microsoft.com/uwp/api/Windows.Graphics)

дисплайадаптерид

### <a name="windowsgraphicsdirectxhttpsdocsmicrosoftcomuwpapiwindowsgraphicsdirectx"></a>[Windows.Graphics.DirectX](https://docs.microsoft.com/uwp/api/Windows.Graphics.DirectX)

директкспикселформат

### <a name="windowsgraphicsdirectxdirect3d11httpsdocsmicrosoftcomuwpapiwindowsgraphicsdirectxdirect3d11"></a>[Windows. Graphics. DirectX. Direct3D11](https://docs.microsoft.com/uwp/api/Windows.Graphics.DirectX.Direct3D11)

Direct3DMultisampleDescription </br> Direct3DSurfaceDescription </br> IDirect3DDevice </br> IDirect3DSurface

### <a name="windowsgraphicsdisplayhttpsdocsmicrosoftcomuwpapiwindowsgraphicsdisplay"></a>[Windows. Graphics. дисплей](https://docs.microsoft.com/uwp/api/Windows.Graphics.Display)

Windows. Graphics. дисплей. Перечисление displayorientations

### <a name="windowsgraphicsimaginghttpsdocsmicrosoftcomuwpapiwindowsgraphicsimaging"></a>[Windows.Graphics.Imaging](https://docs.microsoft.com/uwp/api/Windows.Graphics.Imaging)

> [!NOTE]
> Некоторые интерфейсы API в этом пространстве имен имеют ограничения при использовании в контейнере Windows ML. Дополнительные сведения см. в разделе [**ограничения**](#limitations) .

битмапалфамоде </br> битмапбаундс </br> битмапбуффер </br> битмапбуфферакцессмоде </br> битмапкодеЦинформатион </br> BitmapDecoder завершает </br> BitmapEncoder </br> битмапфлип </br> BitmapFrame </br> битмапинтерполатионмоде </br> битмаппикселформат </br> битмаппланедескриптион </br> битмаппропертиес </br> битмаппропертиесвиев </br> битмаппропертисет </br> битмапротатион </br> битмапсизе </br> битмаптрансформ </br> битмаптипедвалуе </br> колорманажементмоде </br> ексифориентатионмоде </br> ибитмапфраме </br> ибитмапфрамевиссофтваребитмап </br> ибитмаппропертиесвиев </br> имажестреам </br> жпегсубсамплингмоде </br> пикселдатапровидер </br> пнгфилтермоде </br> SoftwareBitmap </br> тиффкомпрессионмоде

## <a name="windowsmedia"></a>Windows.Media

### <a name="windowsmediahttpsdocsmicrosoftcomuwpapiwindowsmedia"></a>[Windows. Media](https://docs.microsoft.com/uwp/api/Windows.Media)

аудиобуффер </br> аудиобуфферакцессмоде </br> аудиофраме </br> аудиопроцессинг </br> ауторепеатмодечанжерекуестедевентаргс </br> имедиаекстенсион </br> имедиафраме </br> имедиамаркер </br> имедиамаркерс </br> имажедисплайпропертиес </br> медиамаркертипес </br> медиаплайбаккауторепеатмоде </br> медиаплайбаккстатус </br> медиаплайбакктипе </br> медиапроцессингтригжердетаилс </br> медиатимеранже </br> медиатимелинеконтроллер </br> медиатимелинеконтроллерфаиледевентаргс </br> медиатимелинеконтроллерстате </br> мусикдисплайпропертиес </br> плайбаккпоситиончанжерекуестедевентаргс </br> плайбаккратечанжерекуестедевентаргс </br> шуффлинабледчанжерекуестедевентаргс </br> саундлевел </br> системмедиатранспортконтролс </br> системмедиатранспортконтролсбуттон </br> системмедиатранспортконтролсбуттонпресседевентаргс </br> системмедиатранспортконтролсдисплайупдатер </br> системмедиатранспортконтролспроперти </br> системмедиатранспортконтролспропертичанжедевентаргс </br> системмедиатранспортконтролстимелинепропертиес </br> видеодисплайпропертиес </br> видеоеффектс </br> видеофраме

## <a name="windowsnetworking"></a>Windows.Networking

### <a name="windowsnetworkinghttpsdocsmicrosoftcomuwpapiwindowsnetworking"></a>[Windows. Networking](https://docs.microsoft.com/uwp/api/Windows.Networking)

домаиннаметипе </br> ендпоинтпаир </br> HostName </br> хостнамесортоптионс </br> хостнаметипе

### <a name="windowsnetworkingbackgroundtransferhttpsdocsmicrosoftcomuwpapiwindowsnetworkingbackgroundtransfer"></a>[Windows. Networking. Баккграундтрансфер](https://docs.microsoft.com/uwp/api/Windows.Networking.BackgroundTransfer)

баккграунддовнлоадпрогресс </br> баккграундтрансфербехавиор </br> баккграундтрансферкомплетионграуп </br> баккграундтрансферкомплетионграуптригжердетаилс </br> баккграундтрансферконтентпарт </br> баккграундтрансферкостполици </br> баккграундтрансфереррор </br> баккграундтрансферфилеранже </br> баккграундтрансферграуп </br> баккграундтрансферприорити </br> баккграундтрансферранжесдовнлоадедевентаргс </br> баккграундтрансферстатус </br> баккграундуплоадпрогресс </br> контентпрефетчер </br> довнлоадоператион </br> ибаккграундтрансфербасе </br> ибаккграундтрансферконтентпартфактори </br> ибаккграундтрансфероператион </br> ибаккграундтрансфероператионприорити </br> респонсеинформатион </br> унконстраинедтрансферрекуестресулт </br> уплоадоператион

### <a name="windowsnetworkingconnectivityhttpsdocsmicrosoftcomuwpapiwindowsnetworkingconnectivity"></a>[Windows.Networking.Connectivity](https://docs.microsoft.com/uwp/api/Windows.Networking.Connectivity)

аттрибутеднетворкусаже </br> целлуларапнаусентикатионтипе </br> целлуларапнконтекст </br> коннектионкост </br> ConnectionProfile </br> ConnectionProfileDeleteStatus </br> коннектионпрофилефилтер </br> коннектионсессион </br> коннективитинтервал </br> коннективитиманажер </br> датапланстатус </br> датапланусаже </br> DataUsage </br> датаусажегрануларити </br> домаинконнективитилевел </br> ланидентифиер </br> ланидентифиердата </br> NetworkAdapter </br> нетворкаусентикатионтипе </br> нетворкконнективитилевел </br> нетворккосттипе </br> нетворкенкриптионтипе </br> NetworkInformation </br> нетворкитем </br> нетворксекуритисеттингс </br> нетворкстатечанжеевентдетаилс </br> нетворкстатусчанжедевенсандлер </br> нетворктипес </br> нетворкусаже </br> нетворкусажестатес </br> провидернетворкусаже </br> проксиконфигуратион </br> роамингстатес </br> раутеполици </br> тристатес </br> вланконнектионпрофиледетаилс </br> вванконнектионпрофиледетаилс </br> вванконтракт </br> ввандатакласс </br> вваннетворкипкинд </br> вваннетворкрегистратионстате

### <a name="windowsnetworkingsocketshttpsdocsmicrosoftcomuwpapiwindowsnetworkingsockets"></a>[Windows.Networking.Sockets](https://docs.microsoft.com/uwp/api/Windows.Networking.Sockets)

бандвидсстатистикс </br> ControlChannelTrigger </br> контролчаннелтригжерконтракт </br> контролчаннелтригжерресетреасон </br> контролчаннелтригжерресаурцетипе </br> контролчаннелтригжерстатус </br> DatagramSocket </br> датаграмсоккетконтрол </br> датаграмсоккетинформатион </br> DatagramSocketMessageReceivedEventArgs </br> иконтролчаннелтригжеревентдетаилс </br> иконтролчаннелтригжерресетевентдетаилс </br> ивебсоккет </br> ивебсоккетконтрол </br> IWebSocketControl2 </br> ивебсоккетинформатион </br> IWebSocketInformation2 </br> MessageWebSocket </br> MessageWebSocketControl </br> MessageWebSocketInformation </br> MessageWebSocketMessageReceivedEventArgs </br> мессажевебсоккетрецеивемоде </br> раундтриптиместатистикс </br> сервермессажевебсоккет </br> сервермессажевебсоккетконтрол </br> сервермессажевебсоккетинформатион </br> серверстреамвебсоккет </br> серверстреамвебсоккетинформатион </br> соккетактивитиконнектедстандбяктион </br> соккетактивитиконтекст </br> соккетактивитинформатион </br> соккетактивитикинд </br> соккетактивититригжердетаилс </br> соккетактивититригжерреасон </br> соккетеррор </br> SocketErrorStatus </br> SocketMessageType </br> SocketProtectionLevel </br> соккеткуалитйофсервице </br> соккетсслеррорсеверити </br> StreamSocket </br> стреамсоккетконтрол </br> стреамсоккетинформатион </br> StreamSocketListener </br> StreamSocketListenerConnectionReceivedEventArgs </br> стреамсоккетлистенерконтрол </br> стреамсоккетлистенеринформатион </br> StreamWebSocket </br> StreamWebSocketControl </br> StreamWebSocketInformation </br> вебсоккетклоседевентаргс </br> вебсоккетеррор </br> вебсоккетсерверкустомвалидатионрекуестедевентаргс

## <a name="windowssecurity"></a>Windows. Security

### <a name="windowssecuritycredentialshttpsdocsmicrosoftcomuwpapiwindowssecuritycredentials"></a>[Windows. Security. Credentials](https://docs.microsoft.com/uwp/api/Windows.Security.Credentials)

PasswordCredential

### <a name="windowssecuritycryptographyhttpsdocsmicrosoftcomuwpapiwindowssecuritycryptography"></a>[Windows. Security. Cryptography](https://docs.microsoft.com/uwp/api/Windows.Security.Cryptography)

бинаристринженкодинг </br> криптографикбуффер

### <a name="windowssecuritycryptographycertificateshttpsdocsmicrosoftcomuwpapiwindowssecuritycryptographycertificates"></a>[Windows. Security. Cryptography. Certificates](https://docs.microsoft.com/uwp/api/Windows.Security.Cryptography.Certificates)

Certificate </br> цертификатечаин </br> цертификатечаинполици </br> цертификатинроллментманажер </br> цертификатикстенсион </br> цертификатекэйусажес </br> CertificateQuery </br> CertificateRequestProperties </br> CertificateStore </br> цертификатесторес </br> чаинбуилдингпараметерс </br> чаинвалидатионпараметерс </br> чаинвалидатионресулт </br> кмсаттачедсигнатуре </br> кмсдетачедсигнатуре </br> кмссигнеринфо </br> кмстиместампинфо </br> енроллкэйусажес </br> експортоптион </br> инсталлоптионс </br> кэйалгорисмнамес </br> кэйаттестатионхелпер </br> KeyProtectionLevel </br> KeySize </br> KeyStorageProviderNames </br> пфксимпортпараметерс </br> сигнатуревалидатионресулт </br> стандардцертификатесторенамес </br> субжекталтернативенамеинфо </br> усерцертификатинроллментманажер </br> усерцертификатесторе

### <a name="windowssecuritycryptographycorehttpsdocsmicrosoftcomuwpapiwindowssecuritycryptographycore"></a>[Windows. Security. Cryptography. Core](https://docs.microsoft.com/uwp/api/Windows.Security.Cryptography.Core)

асимметрикалгорисмнамес </br> асимметриккэйалгорисмпровидер </br> Capi1KdfTargetAlgorithm </br> криптографиценгине </br> криптографичаш </br> криптографиккэй </br> криптографикпаддинг </br> криптографикприватекэйблобтипе </br> криптографикпубликкэйблобтипе </br> екккурвенамес </br> енкриптедандаусентикатеддата </br> хашалгорисмнамес </br> хашалгорисмпровидер </br> кэйдериватионалгорисмнамес </br> кэйдериватионалгорисмпровидер </br> кэйдериватионпараметерс </br> макалгорисмнамес </br> макалгорисмпровидер </br> персистедкэйпровидер </br> симметрикалгорисмнамес </br> симметриккэйалгорисмпровидер

### <a name="windowssecuritycryptographydataprotectionhttpsdocsmicrosoftcomuwpapiwindowssecuritycryptographydataprotection"></a>[Windows. Security. Cryptography. Защита](https://docs.microsoft.com/uwp/api/Windows.Security.Cryptography.DataProtection)

датапротектионпровидер

### <a name="windowssecurityenterprisedatahttpsdocsmicrosoftcomuwpapiwindowssecurityenterprisedata"></a>[Windows. Security. Ентерприседата](https://docs.microsoft.com/uwp/api/Windows.Security.EnterpriseData)

буфферпротектунпротектресулт </br> DataProtectionInfo </br> DataProtectionManager </br> датапротектионстатус </br> енфорцементлевел </br> ентерприседатаконтракт </br> FileProtectionInfo </br> FileProtectionManager </br> FileProtectionStatus </br> филеревокатионманажер </br> филеунпротектоптионс </br> протектедакцессресумедевентаргс </br> протектедакцесссуспендинжевентаргс </br> протектедконтаинерекспортресулт </br> протектедконтаинеримпортресулт </br> протектедконтентревокедевентаргс </br> протектедфилекреатересулт </br> протектедимпортекспортстатус </br> протектионполициаудитактион </br> протектионполициаудитинфо </br> ProtectionPolicyEvaluationResult </br> ProtectionPolicyManager </br> протектионполицирекуестакцессбехавиор </br> среаднетворкконтекст

### <a name="windowssecurityexchangeactivesyncprovisioninghttpsdocsmicrosoftcomuwpapiwindowssecurityexchangeactivesyncprovisioning"></a>[Windows. Security. Ексчанжеактивесинкпровисионинг](https://docs.microsoft.com/uwp/api/Windows.Security.ExchangeActiveSyncProvisioning)

еасклиентдевицеинформатион </br> еасклиентсекуритиполици </br> еаскомплианцересултс </br> еасконтракт </br> еасдисалловконвениенцелогонресулт </br> еасенкриптионпровидертипе </br> еасмаксинактивититимелоккресулт </br> еасмакспассвордфаиледаттемптсресулт </br> еасминпассвордкомплексчарактерсресулт </br> еасминпассвордленгсресулт </br> еаспассвордекспиратионресулт </br> еаспассвордхисториресулт </br> еасрекуиринкриптионресулт

## <a name="windowsstorage"></a>Windows.Storage

### <a name="windowsstoragehttpsdocsmicrosoftcomuwpapiwindowsstorage"></a>[Windows. Storage](https://docs.microsoft.com/uwp/api/Windows.Storage)

аппдатапасс </br> ApplicationData </br> аппликатиондатакомпоситевалуе </br> ApplicationDataContainer </br> аппликатиондатаконтаинерсеттингс </br> аппликатиондатакреатедиспоситион </br> аппликатиондаталокалити </br> аппликатиондатасетверсионхандлер </br> качедфилеманажер </br> креатионколлисионоптион </br> довнлоадсфолдер </br> филеакцессмоде </br> FileAttributes </br> FileIO </br> исторажефиле </br> IStorageFile2 </br> исторажефилепропертиесвисаваилабилити </br> исторажефолдер </br> IStorageFolder2 </br> исторажеитем </br> IStorageItem2 </br> исторажеитемпропертиес </br> IStorageItemProperties2 </br> исторажеитемпропертиесвиспровидер </br> истреамедфиледатарекуест </br> кновнфолдерид </br> кновнфолдерс </br> кновнфолдерсакцессстатус </br> кновнлибрарид </br> намеколлисионоптион </br> PathIO </br> сетверсиондеферрал </br> сетверсионрекуест </br> сторажеделетеоптион </br> StorageFile </br> сторажефолдер </br> сторажеитемтипес </br> сторажелибрари </br> сторажелибраричанже </br> сторажелибраричанжереадер </br> сторажелибраричанжетраккер </br> сторажелибраричанжетипе </br> сторажеопеноптионс </br> сторажепровидер </br> сторажестреамтрансактион </br> стреамедфиледатарекуест </br> стреамедфиледатарекуестедхандлер </br> стреамедфилефаилуремоде </br> системаудиопропертиес </br> системдатапасс </br> системгпспропертиес </br> системимажепропертиес </br> системмедиапропертиес </br> системмусикпропертиес </br> системфотопропертиес </br> системпропертиес </br> системвидеопропертиес </br> усердатапасс

### <a name="windowsstorageaccesscachehttpsdocsmicrosoftcomuwpapiwindowsstorageaccesscache"></a>[Windows.Storage.AccessCache](https://docs.microsoft.com/uwp/api/Windows.Storage.AccessCache)

акцесскачеоптионс </br> акцесслистентри </br> акцесслистентривиев </br> исторажеитемакцесслист </br> итемремоведевентаргс </br> рецентсторажеитемвисибилити </br> сторажеаппликатионпермиссионс </br> сторажеитемакцесслист </br> сторажеитеммострецентлюседлист

### <a name="windowsstoragebulkaccesshttpsdocsmicrosoftcomuwpapiwindowsstoragebulkaccess"></a>[Windows. Storage. Булкакцесс](https://docs.microsoft.com/uwp/api/Windows.Storage.BulkAccess)

филеинформатион </br> филеинформатионфактори </br> фолдеринформатион </br> исторажеитеминформатион

### <a name="windowsstoragecompressionhttpsdocsmicrosoftcomuwpapiwindowsstoragecompression"></a>[Windows. Storage. Compression](https://docs.microsoft.com/uwp/api/Windows.Storage.Compression)

компрессалгорисм </br> Упаковщик </br> Распаковщик

### <a name="windowsstoragefilepropertieshttpsdocsmicrosoftcomuwpapiwindowsstoragefileproperties"></a>[Windows. Storage. Филепропертиес](https://docs.microsoft.com/uwp/api/Windows.Storage.FileProperties)

басикпропертиес </br> DocumentProperties </br> исторажеитемекстрапропертиес </br> имажепропертиес </br> мусикпропертиес </br> Фотоориентация </br> пропертипрефетчоптионс </br> сторажеитемконтентпропертиес </br> сторажеитемсумбнаил </br> сумбнаилмоде </br> сумбнаилоптионс </br> сумбнаилтипе </br> видеуриентатион </br> видеопропертиес

### <a name="windowsstorageproviderhttpsdocsmicrosoftcomuwpapiwindowsstorageprovider"></a>[Windows.Storage.Provider](https://docs.microsoft.com/uwp/api/Windows.Storage.Provider)

качедфилеоптионс </br> качедфилетаржет </br> качедфилеупдатер </br> качедфилеупдатеруи </br> клаудфилесконтракт </br> филеупдатерекуест </br> филеупдатерекуестдеферрал </br> филеупдатерекуестедевентаргс </br> филеупдатестатус </br>  исторажепровидеритемпропертисаурце </br> исторажепровидерпропертикапабилитиес </br> исторажепровидерурисаурце </br> реадактиватионмоде </br> сторажепровидерфилетипеинфо </br> сторажепровидержетконтентинфофорпасресулт </br> сторажепровидержетпасфорконтентуриресулт </br> сторажепровидерхардлинкполици </br> сторажепровидерхидратионполици </br> сторажепровидерхидратионполицимодифиер </br> сторажепровидеринсинкполици </br> сторажепровидеритемпропертиес </br> сторажепровидеритемпроперти </br> сторажепровидеритемпропертидефинитион </br> сторажепровидерпопулатионполици </br> сторажепровидерпротектионмоде </br> сторажепровидерсинкрутинфо </br> сторажепровидерсинкрутманажер </br> сторажепровидерурисаурцестатус </br> уистатус </br> вритеактиватионмоде

### <a name="windowsstoragesearchhttpsdocsmicrosoftcomuwpapiwindowsstoragesearch"></a>[Windows. Storage. Search](https://docs.microsoft.com/uwp/api/Windows.Storage.Search)

коммонфилекуери </br> коммонфолдеркуери </br> контентиндексер </br> контентиндексеркуери </br> датестаккоптион </br> фолдердепс </br> ииндексаблеконтент </br> исторажефолдеркуерйоператионс </br> исторажекуериресултбасе </br> индексаблеконтент </br> индекседстате </br> индексероптион </br> куерйоптионс </br> сортентри </br> сортентривектор </br> сторажефилекуериресулт </br> сторажефолдеркуериресулт </br> сторажеитемкуериресулт </br> сторажелибраричанжетраккертригжердетаилс </br> сторажелибрариконтентчанжедтригжердетаилс </br> валуеандлангуаже

### <a name="windowsstoragestreamshttpsdocsmicrosoftcomuwpapiwindowsstoragestreams"></a>[Windows.Storage.Streams](https://docs.microsoft.com/uwp/api/Windows.Storage.Streams)

Буфер </br> битеордер </br> DataReader </br> датареадерлоадоператион </br> DataWriter </br> датавритерстореоператион </br> FileInputStream </br> филеопендиспоситион </br> FileOutputStream </br> FileRandomAccessStream </br> IBuffer </br>  иконтенттипепровидер </br> IDataReader </br> IInputStream </br> иинпутстреамреференце </br> IOutputStream </br> IRandomAccessStream </br> ирандомакцессстреамреференце </br> ирандомакцессстреамвисконтенттипе </br> инмеморирандомакцессстреам </br> инпутстреамоптионс </br> инпутстреамоверстреам </br> аутпутстреамоверстреам </br> рандомакцессстреам </br> рандомакцессстреамоверстреам </br> рандомакцессстреамреференце </br> UnicodeEncoding

## <a name="windowssystem"></a>Windows.System

### <a name="windowssystemhttpsdocsmicrosoftcomuwpapiwindowssystem"></a>[Windows.System](https://docs.microsoft.com/uwp/api/Windows.System)

аппдиагностиЦинфоватчерстатус </br> аппексекутионстатечанжересулт </br> аппмеморирепорт </br> аппмеморюсажелевел </br> аппмеморюсажелимитчангинжевентаргс </br> аппресаурцеграупбаккграундтаскрепорт </br> аппресаурцеграупенергикуотастате </br> аппресаурцеграупексекутионстате </br> аппресаурцеграупинфоватчерстатус </br> аппресаурцеграупмеморирепорт </br> аппресаурцеграупстатерепорт </br> AppUriHandlerHost </br> AppUriHandlerRegistration </br> AppUriHandlerRegistrationManager </br> аутаупдатетимезонестатус </br> датетимесеттингс </br> диагностикакцессстатус </br> DispatcherQueue </br> диспатчеркуеуеконтроллер </br> диспатчеркуеуехандлер </br> диспатчеркуеуеприорити </br> диспатчеркуеуешутдовнстартинжевентаргс </br> диспатчеркуеуетимер </br> кновнусерпропертиес </br> лаунчфилестатус </br> лаунчкуерисуппортстатус </br> лаунчкуерисуппорттипе </br> лаунчуриресулт </br> лаунчуристатус </br> мемориманажер </br> Установлен </br> процесслаунчер </br> процесслаунчероптионс </br> процесслаунчерресулт </br> процессмеморирепорт </br> ProcessorArchitecture </br> протоколфорресултсоператион </br> ремотелаунчуристатус </br> ремотелаунчероптионс </br> шутдовнкинд </br> шутдовнманажер </br> системманажементконтракт </br> тимезонесеттингс

### <a name="windowssystemdiagnosticshttpsdocsmicrosoftcomuwpapiwindowssystemdiagnostics"></a>[Windows. System. Diagnostics](https://docs.microsoft.com/uwp/api/Windows.System.Diagnostics)

диагностикактионресулт </br> диагностикактионстате </br> диагностиЦинвокер </br> процесскпуусаже </br> процесскпуусажерепорт </br> процессдискусаже </br> процессдискусажерепорт </br> процессмеморюсаже </br> процессмеморюсажерепорт </br> системкпуусаже </br> системкпуусажерепорт </br> системдиагностиЦинфо </br> системмеморюсаже </br> системмеморюсажерепорт

### <a name="windowssystemdiagnosticstelemetryhttpsdocsmicrosoftcomuwpapiwindowssystemdiagnosticstelemetry"></a>[Windows. System. Diagnostics. телеметрии](https://docs.microsoft.com/uwp/api/Windows.System.Diagnostics.Telemetry)

платформтелеметриклиент </br> платформтелеметрирегистратионресулт </br> платформтелеметрирегистратионсеттингс </br> платформтелеметрирегистратионстатус

### <a name="windowssystemdiagnosticstracereportinghttpsdocsmicrosoftcomuwpapiwindowssystemdiagnosticstracereporting"></a>[Windows. System. Diagnostics. Трацерепортинг](https://docs.microsoft.com/uwp/api/Windows.System.Diagnostics.TraceReporting)

платформдиагностикактионстате </br> платформдиагностикактионс </br> платформдиагностицескалатионтипе </br> платформдиагностицевентбуфферлатенЦиес </br> платформдиагностиктрацеинфо </br> платформдиагностиктрацеприорити </br> платформдиагностиктрацерунтимеинфо </br> платформдиагностиктрацеслотстате </br> платформдиагностиктрацеслоттипе

### <a name="windowssystemdisplayhttpsdocsmicrosoftcomuwpapiwindowssystemdisplay"></a>[Windows. System. дисплей](https://docs.microsoft.com/uwp/api/Windows.System.Display)

DisplayRequest

### <a name="windowssysteminventoryhttpsdocsmicrosoftcomuwpapiwindowssysteminventory"></a>[Windows. System. Inventory](https://docs.microsoft.com/uwp/api/Windows.System.Inventory)

инсталледдесктопапп

### <a name="windowssystempowerhttpsdocsmicrosoftcomuwpapiwindowssystempower"></a>[Windows. System. Power](https://docs.microsoft.com/uwp/api/Windows.System.Power)

баккграунденергиманажер </br> баттеристатус </br> енергисаверстатус </br> фореграунденергиманажер </br> поверманажер </br> поверсупплистатус

### <a name="windowssystempowerdiagnosticshttpsdocsmicrosoftcomuwpapiwindowssystempowerdiagnostics"></a>[Windows. System. Power. Diagnostics](https://docs.microsoft.com/uwp/api/Windows.System.Power.Diagnostics)

баккграунденергидиагностикс </br> фореграунденергидиагностикс

### <a name="windowssystemprofilehttpsdocsmicrosoftcomuwpapiwindowssystemprofile"></a>[Windows.System.Profile](https://docs.microsoft.com/uwp/api/Windows.System.Profile)

аналитиксинфо </br> аналитиксверсионинфо </br> AppApplicability </br> едукатионсеттингс </br> хардвареидентификатион </br> хардваретокен </br> кновнретаилинфопропертиес </br> платформдатаколлектионлевел </br> платформдиагностиксандусажедатасеттингс </br> профилехардваретокенконтракт </br> профилеретаилинфоконтракт </br> профилешаредмодеконтракт </br> ретаилинфо </br> шаредмодесеттингс </br> системидентификатион </br> системидентификатионинфо </br> системидентификатионсаурце </br> SystemOutOfBoxExperienceState </br> SystemSetupInfo </br> UnsupportedAppRequirement </br> UnsupportedAppRequirementReasons </br> WindowsIntegrityPolicy

### <a name="windowssystemprofilesystemmanufacturershttpsdocsmicrosoftcomuwpapiwindowssystemprofilesystemmanufacturers"></a>[Windows.System.Profile.SystemManufacturers](https://docs.microsoft.com/uwp/api/Windows.System.Profile.SystemManufacturers)

оемсуппортинфо </br> смбиосинформатион </br> системмануфактурерсконтракт </br> SystemSupportDeviceInfo </br> системсуппортинфо

### <a name="windowssystemthreadinghttpsdocsmicrosoftcomuwpapiwindowssystemthreading"></a>[Windows. System. Threading](https://docs.microsoft.com/uwp/api/Windows.System.Threading)

Пула </br> ThreadPoolTimer </br> тимердестройедхандлер </br> тимерелапседхандлер </br> воркитемхандлер </br> воркитемоптионс </br> воркитемприорити

### <a name="windowssystemthreadingcorehttpsdocsmicrosoftcomuwpapiwindowssystemthreadingcore"></a>[Windows. System. Threading. Core](https://docs.microsoft.com/uwp/api/Windows.System.Threading.Core)

преаллокатедворкитем </br> сигналхандлер </br> сигналнотифиер

### <a name="windowssystemuserhttpsdocsmicrosoftcomuwpapiwindowssystemuser"></a>[Windows. System. пользователь](https://docs.microsoft.com/uwp/api/Windows.System.User)

Пользователь </br> усераусентикатионстатус </br> усераусентикатионстатусчанжедеферрал </br> усераусентикатионстатусчангинжевентаргс </br> усерчанжедевентаргс </br> Сущность userdeviceassociation </br> усердевицеассоЦиатиончанжедевентаргс </br> усерпиккер </br> усерпиктуресизе </br> userType </br> усерватчер </br> усерватчерстатус </br> усерватчерупдатекинд </br> виртуалкэй </br> виртуалкэймодифиерс

## <a name="windowsui"></a>Windows.UI

### <a name="windowsuitextcorehttpsdocsmicrosoftcomuwpapiwindowsuitextcore"></a>[Windows.UI.Text.Core](https://docs.microsoft.com/uwp/api/Windows.UI.Text.Core)

коретекстинпутскопе

## <a name="windowsweb"></a>Windows.Web

### <a name="windowswebhttpsdocsmicrosoftcomuwpapiwindowsweb"></a>[Windows. Web](https://docs.microsoft.com/uwp/api/Windows.Web)

иуритостреамресолвер </br> Ошибка </br> WebErrorStatus

### <a name="windowswebatompubhttpsdocsmicrosoftcomuwpapiwindowswebatompub"></a>[Windows. Web. AtomPub](https://docs.microsoft.com/uwp/api/Windows.Web.AtomPub)

атомпубклиент </br> ресаурцеколлектион </br> сервицедокумент </br> Рабочая область

### <a name="windowswebhttphttpsdocsmicrosoftcomuwpapiwindowswebhttp"></a>[Windows.Web.Http](https://docs.microsoft.com/uwp/api/Windows.Web.Http)

хттпбуфферконтент </br> HttpClient </br> хттпкомплетионоптион </br> HttpCookie </br> хттпкукиеколлектион </br> хттпкукиеманажер </br> хттпформурленкодедконтент </br> HttpGetBufferResult </br> HttpGetInputStreamResult </br> HttpGetStringResult </br> httpMethod </br> хттпмултипартконтент </br> хттпмултипартформдатаконтент </br> хттппрогресс </br> хттппрогрессстаже </br> HttpRequestMessage </br> HttpRequestResult </br> HttpResponseMessage </br> хттпреспонсемессажесаурце </br> HttpStatusCode </br> хттпстреамконтент </br> хттпстрингконтент </br> хттптранспортинформатион </br> хттпверсион </br> ихттпконтент

### <a name="windowswebhttpdiagnosticshttpsdocsmicrosoftcomuwpapiwindowswebhttpdiagnostics"></a>[Windows. Web. http. Diagnostics](https://docs.microsoft.com/uwp/api/Windows.Web.Http.Diagnostics)

хттпдиагностикпровидер </br> хттпдиагностикпровидеррекуестреспонсекомплетедевентаргс </br> хттпдиагностикпровидеррекуестреспонсетиместампс </br> хттпдиагностикпровидеррекуестсентевентаргс </br> хттпдиагностикпровидерреспонсерецеиведевентаргс </br> хттпдиагностикрекуестинитиатор </br> хттпдиагностиксаурцелокатион </br> хттпдиагностиксконтракт

### <a name="windowswebhttpfiltershttpsdocsmicrosoftcomuwpapiwindowswebhttpfilters"></a>[Windows.Web.Http.Filters](https://docs.microsoft.com/uwp/api/Windows.Web.Http.Filters)

HttpBaseProtocolFilter </br> хттпкачеконтрол </br> хттпкачереадбехавиор </br> хттпкачевритебехавиор </br> хттпкукиеусажебехавиор </br> хттпсерверкустомвалидатионрекуестедевентаргс </br> ихттпфилтер

### <a name="windowswebhttpheadershttpsdocsmicrosoftcomuwpapiwindowswebhttpheaders"></a>[Windows. Web. http. Headers](https://docs.microsoft.com/uwp/api/Windows.Web.Http.Headers)

хттпкачедирективехеадервалуеколлектион </br> хттпчалленжехеадервалуе </br> хттпчалленжехеадервалуеколлектион </br> хттпконнектионоптионхеадервалуе </br> хттпконнектионоптионхеадервалуеколлектион </br> хттпконтенткодингхеадервалуе </br> хттпконтенткодингхеадервалуеколлектион </br> хттпконтенткодингвискуалитихеадервалуе </br> хттпконтенткодингвискуалитихеадервалуеколлектион </br> хттпконтентдиспоситионхеадервалуе </br> хттпконтенсеадерколлектион </br> хттпконтентранжехеадервалуе </br> хттпкукиепаирхеадервалуе </br> хттпкукиепаирхеадервалуеколлектион </br> хттпкредентиалшеадервалуе </br> хттпдатеорделтахеадервалуе </br> хттпекспектатионхеадервалуе </br> хттпекспектатионхеадервалуеколлектион </br> хттплангуажехеадервалуеколлектион </br> хттплангуажеранжевискуалитихеадервалуе </br> хттплангуажеранжевискуалитихеадервалуеколлектион </br> хттпмедиатипехеадервалуе </br> хттпмедиатипевискуалитихеадервалуе </br> хттпмедиатипевискуалитихеадервалуеколлектион </br> хттпмесодхеадервалуеколлектион </br> хттпнамевалуехеадервалуе </br> хттппродуксеадервалуе </br> хттппродуктинфохеадервалуе </br> хттппродуктинфохеадервалуеколлектион </br> хттпрекуессеадерколлектион </br> хттпреспонсехеадерколлектион </br> хттптрансферкодингхеадервалуе </br> хттптрансферкодингхеадервалуеколлектион

### <a name="windowswebsyndicationhttpsdocsmicrosoftcomuwpapiwindowswebsyndication"></a>[Windows. Web. синдикации](https://docs.microsoft.com/uwp/api/Windows.Web.Syndication)

исиндикатионклиент </br> исиндикатионноде </br> исиндикатионтекст </br> ретриевалпрогресс </br> синдикатионаттрибуте </br> синдикатионкатегори </br> синдикатионклиент </br> синдикатионконтент </br> синдикатионеррор </br> синдикатионеррорстатус </br> SyndicationFeed </br> синдикатионформат </br> синдикатионженератор </br> SyndicationItem </br> синдикатионлинк </br> синдикатионноде </br> синдикатионперсон </br> синдикатионтекст </br> синдикатионтексттипе </br> трансферпрогресс

## <a name="limitations"></a>Ограничения

### <a name="windowsgraphicsimaging"></a>Windows. Graphics. Imaging

Некоторые интерфейсы API в пространстве имен [Windows. Graphics. Imaging](https://docs.microsoft.com/uwp/api/windows.graphics.imaging) подчиняются ограничениям при использовании в контейнере Windows ml. Эти ограничения приведены ниже.

* Windows. Graphics. Imaging поддерживает кодирование и декодирование только для форматов файлов JPG, PNG, GIF, TIFF и BMP.
* При использовании формата BMP с BI_BITFIELDS сжатием поддерживаются только форматы 16bppBGR555, 16bppBGR565 и 32bppBGRA.
* Не поддерживается CMYK, высокий динамический диапазон, формат пикселей с половиной плавающей запятой, форматы пикселей с фиксированной запятой или изображения с более чем четырьмя каналами.
* Форматы пикселей 32bppRGBE, 16bppYQuantizedDctCoefficients, 16bppCbQuantizedDctCoefficients и 16bppCrQuantizedDctCoefficients не поддерживаются.
* Отсутствует поддержка чтения или записи метаданных XMP или [политик метаданных фотографий](https://docs.microsoft.com/windows/win32/wic/photo-metadata-policies). При перекодировке API попытается сохранить метаданные XMP, если это возможно.
* Колорспаце манипуляции и диалога не поддерживается.
* Имеется *частичная* поддержка флага `ColorManageToSRgb` в [жетпикселдатаасинк](https://docs.microsoft.com/uwp/api/windows.graphics.imaging.bitmapdecoder.getpixeldataasync) и [жетсофтваребитмапасинк](https://docs.microsoft.com/uwp/api/windows.graphics.imaging.bitmapframe.getsoftwarebitmapasync). Если указан флаг, операция будет выполнена успешно, если образ имеет обычно распознаваемый цветовой профиль sRGB. В противном случае будет возвращено значение HRESULT, эквивалентное `ERROR_ICM_NOT_ENABLED`.
