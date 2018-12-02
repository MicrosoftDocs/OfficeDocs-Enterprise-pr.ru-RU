---
title: Веб-служба IP-адресов и URL-адресов в Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 9/4/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365
ms.reviewer: pandrew
search.appverid:
- MET150
- MOE150
- BCS160
description: Чтобы помочь вам выявлять и дифференцировать сетевой трафик Office 365, новая веб-служба публикует конечные точки Office 365, упрощая оценку, настройку и обновление. Эта новая веб-служба заменяет собой скачиваемые XML-файлы, доступные в настоящее время.
ms.openlocfilehash: 8a9b3981f833705b0d77e87a6f0588730b9fb170
ms.sourcegitcommit: 7db45f3c81f38908ac2d6f64ceb79a4f334ec3cf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/29/2018
ms.locfileid: "26985774"
---
# <a name="office-365-ip-address-and-url-web-service"></a>**Веб-служба IP-адресов и URL-адресов в Office 365**

Чтобы помочь вам выявлять и дифференцировать сетевой трафик Office 365, новая веб-служба публикует конечные точки Office 365, упрощая оценку, настройку и обновление. Эта новая веб-служба заменяет собой скачиваемые XML-файлы, доступные в настоящее время. Прекращение поддержки формата XML планируется на 2 октября 2018 г.

Будучи клиентом или поставщиком устройств сети периметра, вы можете создавать решения с использованием новой веб-службы на основе REST для записей FQDN и IP-адресов в Office 365. Доступ к данным можно получить непосредственно в браузере с помощью этих URL-адресов.

- Для получения последней версии диапазонов IP-адресов и URL-адресов Office 365 перейдите на веб-страницу [https://endpoints.office.com/version](https://endpoints.office.com/version?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).
- Для получения данных на странице диапазонов IP-адресов и URL-адресов Office 365 для брандмауэров и прокси-серверов перейдите на веб-страницу [https://endpoints.office.com/endpoints/worldwide](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).
- Для получения всех последних изменений с конца июля 2018 года (тогда стала доступной веб-служба) перейдите на веб-страницу [https://endpoints.office.com/changes/worldwide/0000000000](https://endpoints.office.com/changes/worldwide/0000000000?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).

Как клиент вы можете использовать эту веб-службу, чтобы:

- обновлять скрипты PowerShell для получения данных конечной точки Office 365 и изменять форматирование для сетевых устройств;
- применять эту информацию для обновления PAC-файлов, развернутых на клиентских компьютерах.

Как поставщик устройств сети периметра вы можете использовать эту веб-службу, чтобы:

- создавать и тестировать программное обеспечение устройств для скачивания списка с целью автоматической настройки;
- проверять текущую версию;
- получать текущие изменения.

Дополнительные сведения:

- [Объявление в записи блога на форуме Tech Community Office 365.](https://techcommunity.microsoft.com/t5/Office-365-Blog/Announcing-Office-365-endpoint-categories-and-Office-365-IP/ba-p/177638)
- [Форум Tech Community Office 365, содержащий сведения об использовании веб-служб.](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)

## <a name="common-parameters"></a>**Общие параметры**

Эти параметры являются общими для всех методов веб-службы:

- **format=CSV | JSON**. Параметр строки запроса. По умолчанию данные возвращаются в формате JSON. Включайте этот необязательный параметр для возврата данных в формате значений с разделителями-запятыми (CSV).
- **ClientRequestId**. Параметр строки запроса. Обязательный GUID, который вы создаете для связи клиента. Нужно создавать GUID для каждого компьютера, который вызывает веб-службу. Не используйте GUID, показанные в примерах ниже, так как они могут быть заблокированы веб-службой в будущем. Формат GUID следующий: _xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx_. Здесь "x" означает шестнадцатеричное число. Для создания GUID используйте команду [New-Guid](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-guid?view=powershell-6) PowerShell.

## <a name="version-web-method"></a>**Веб-метод версии**

Майкрософт обновляет записи IP-адресов и FQDN Office 365 в конце каждого месяца и иногда вне цикла для выполнения операционных требований или требований поддержки. Данным для каждого опубликованного экземпляра назначается номер версии. Веб-метод версии позволяет проводить опрос для получения последней версии каждого экземпляра службы Office 365. Рекомендуем проверять версию ежедневно (максимум ежечасно). Появление новых версий ожидается в начале каждого месяца. Иногда ввиду инцидентов поддержки, безопасности или других операционных требований новые версии будут появляться в течение месяца.

Для веб-метода версии предусмотрен один параметр:

- **AllVersions=true**. Параметр строки запроса. По умолчанию возвращается последний номер версии. Включите этот дополнительный параметр для запроса всех опубликованных версий.
- **Format=JSON** | **CSV** | **RSS**. Кроме форматов JSON и CSV, веб-метод версии поддерживает RSS. Вы можете использовать его вместе с параметром allVersions=true для запрашивания RSS-канала, который можно применять в Outlook или других средствах чтения RSS.
- **Instance**. Параметр маршрутизации. Этот необязательный параметр указывает экземпляр, для которого возвращается версия. Если его опустить, будут возвращены все экземпляры. Допустимые экземпляры: Worldwide, China, Germany, USGovDoD, USGovGCCHigh.

Веб-метод версии не имеет ограничения по частоте и не возвращает HTTP-код отклика 429. Отклик для веб-метода версии включает заголовок с контролем кэша, рекомендующий кэширование данных в течение 1 часа. Результатом веб-метода версии может быть отдельная запись или массив записей. Ниже перечислены элементы каждой записи:

- instance — короткое имя экземпляра службы Office 365.
- latest — последняя версия для конечных точек указанного экземпляра.
- versions — список всех предыдущих версий для указанного экземпляра. Этот элемент включен, только если параметр AllVersions имеет значение true.

Вы можете использовать Microsoft Flow для получения уведомлений об изменениях IP-адресов и URL-адресов по электронной почте. См. статью [Использование Microsoft Flow для получения электронных сообщений об изменениях URL-адресов и IP-адресов Office 365](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/m-p/240651).

### <a name="examples"></a>**Примеры**

Пример 1. Запрос URI: [https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

Этот URI возвращает последнюю версию каждого экземпляра службы Office 365. Пример результата:

```json
[
 {
  "instance": "Worldwide",
  "latest": "2018063000"
 },
 {
  "instance": "USGovDoD",
  "latest": "2018063000"
 },
 {
  "instance": "USGovGCCHigh",
  "latest": "2018063000"
 },
 {
  "instance": "China",
  "latest": "2018063000"
 },
 {
  "instance": "Germany",
  "latest": "2018063000"
 }
]
```

> [!IMPORTANT]
> GUID для параметра ClientRequestID в этих URI приведен только в качестве примера. Чтобы попробовать применить URI веб-службы, создайте собственный GUID. GUID, показанные в этих примерах, могут быть заблокированы веб-службой в будущем.

Пример 2. Запрос URI: [https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

Этот URI возвращает последнюю версию указанного экземпляра службы Office 365. Пример результата:

```json
{
 "instance": "Worldwide",
 "latest": "2018063000"
}

```

Пример 3. Запрос URI: [https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

Этот URI показывает выходные данные в формате CSV. Пример результата:

```csv
instance,latest
Worldwide,2018063000
```

Пример 4. Запрос URI: [https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

Этот URI показывает все более ранние версии, которые были опубликованы для экземпляра службы Office 365 Worldwide. Пример результата:

```json
{
  "instance": "Worldwide",
  "latest": "2018063000",
  "versions": [
    "2018063000",
    "2018062000"
  ]
}
```

Пример 5. URI RSS-канала: [https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS](https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS)

Этот URI показывает RSS-канал опубликованных версий, которые содержат ссылки на список изменений для каждой версии. Пример результата:

```xml
<?xml version="1.0" encoding="ISO-8859-1"?>
<rss version="2.0" xmlns:a10="http://www.w3.org/2005/Atom">
<channel>
<link>http://aka.ms/o365ip</link>
<description/>
<language>en-us</language>
<lastBuildDate>Thu, 02 Aug 2018 00:00:00 Z</lastBuildDate>
<item>
<guid isPermaLink="false">2018080200</guid>
<link>https://endpoints.office.com/changes/Worldwide/2018080200?singleVersion&clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7</link> <description>Version 2018080200 includes 2 changes. IPs: 2 added and 0 removed.</description>
<pubDate>Thu, 02 Aug 2018 00:00:00 Z</pubDate>
</item>
...
```

## <a name="endpoints-web-method"></a>**Веб-метод конечных точек**

Веб-метод конечных точек возвращает все записи для диапазонов IP-адресов и URL-адресов, входящих в службу Office 365. Хотя для настройки сетевого устройства нужно использовать новейшие данные от веб-метода конечных точек, данные можно кэшировать в течение 30 дней после их публикации ввиду заблаговременного уведомления в отношении дополнений. Мы рекомендуем вам вызывать веб-метод конечных точек еще раз, только когда версия веб-метода обнаруживает доступность новой версии данных. Параметры веб-метода конечных точек показаны ниже:

- **ServiceAreas**. Параметр строки запроса. Список областей обслуживания, разделенных запятыми. Допустимые элементы: Common, Exchange, SharePoint, Skype. Так как элементы области обслуживания Common обязательны для всех других областей обслуживания, веб-служба всегда будет их включать. Если не включить этот параметр, будут возвращены все области обслуживания.
- **TenantName**. Параметр строки запроса. Имя клиента Office 365. Веб-служба получает предоставленное вами имя и вставляет его в части URL-адресов, которые включают имя клиента. Если вы не предоставляете имя клиента, эти части URL-адресов будут содержать подстановочный знак (\*).
- **NoIPv6**. Параметр строки запроса. Установите для него значение true, чтобы исключить адреса IPv6 из выходных данных (например, если в вашей сети не используется IPv6).
- **Instance**. Параметр маршрутизации. Этот обязательный параметр указывает экземпляр, для которого должны быть возвращены конечные точки. Допустимые экземпляры: Worldwide, China, Germany, USGovDoD, USGovGCCHigh.

Если вы вызываете веб-метод конечных точек необоснованное количество раз с одного клиентского IP-адреса, вы можете получить код HTTP-отклика 429 (Слишком большое количество запросов). Большинство пользователей никогда не увидит данный код. Если вы получили этот код отклика, вы должны подождать 1 час, прежде чем вызывать этот метод еще раз. Запланируйте вызов веб-метода конечных точек только тогда, когда веб-версия веб-метода указывает на то, что доступна новая версия. 

Результат веб-метода конечных точек — массив, в который входят все записи, представляющие набор конечных точек. Элементы каждой записи:

- id — неизменяемый идентификатор набора конечных точек.
- serviceArea — область обслуживания, которая является частью Common, Exchange, SharePoint или Skype.
- urls — URL-адреса для набора конечных точек. Массив JSON записей DNS. Если значение не указано, опускается.
- tcpPorts — TCP-порты для набора конечных точек. Все элементы портов отформатированы в виде списка портов с разделителями-запятыми или диапазонов портов, разделенных символами дефиса (-). Порты применяются ко всем IP-адресам и всем URL-адресам в этом наборе конечных точек для этой категории. Если значение не указано, опускается.
- udpPorts — порты UDP для диапазонов IP-адресов в этом наборе конечных точек. Если значение не указано, опускается.
- ips — диапазоны IP-адресов, связанные с этим набором конечных точек (с перечисленными портами TCP или UDP). Массив JSON диапазонов IP-адресов. Если значение не указано, опускается.
- category — категория возможности подключения к набору конечных точек. Допустимые значения: Optimize, Allow и Default. При использовании данных конечной точки для поиска категории IP- или URL-адреса запрос может возвращать несколько категорий. Это может происходить по нескольким причинам. В таких случаях необходимо следовать рекомендациям для категории с наивысшим приоритетом. Например, если для конечной точки выводятся значения Optimize и Allow, следует выполнять требования для значения Optimize. Обязательный элемент. 
- expressRoute имеет значение True или False, если для этого набора конечных точек выполняется маршрутизация через ExpressRoute.
- required имеет значение True, если этот набор конечных точек требуется для подключения к Office 365. False, если этот набор конечных точек необязателен.
- notes — текст, который в случае необязательных конечных точек описывает функциональность Office 365, которая будет отсутствовать, если IP-адреса или URL-адреса в этом наборе конечных точек не могут быть доступны на сетевом уровне. Если значение не указано, опускается.

### <a name="examples"></a>Примеры

Пример 1. Запрос URI: [https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

Этот URI получает все конечные точки для экземпляра Office 365 Worldwide для всех рабочих нагрузок. В примере результата показан фрагмент выходных данных:

```json
[
 {
  "id": 1,
  "serviceArea": "Exchange",
  "serviceAreaDisplayName": "Exchange Online",
  "urls":
   [
    "*.protection.outlook.com"
   ],
  "ips":
   [
    "2a01:111:f403::/48", "23.103.132.0/22", "23.103.136.0/21", "23.103.198.0/23", "23.103.212.0/22", "40.92.0.0/14", "40.107.0.0/17", "40.107.128.0/18", "52.100.0.0/14", "213.199.154.0/24", "213.199.180.128/26", "94.245.120.64/26", "207.46.163.0/24", "65.55.88.0/24", "216.32.180.0/23", "23.103.144.0/20", "65.55.169.0/24", "207.46.100.0/24", "2a01:111:f400:7c00::/54", "157.56.110.0/23", "23.103.200.0/22", "104.47.0.0/17", "2a01:111:f400:fc00::/54", "157.55.234.0/24", "157.56.112.0/24", "52.238.78.88/32"
   ],
  "tcpPorts": "443",
  "expressRoute": true,
  "category": "Allow"
 },
 {
  "id": 2,
  "serviceArea": "Exchange",
  "serviceAreaDisplayName": "Exchange Online",
  "urls":
   [
    "*.mail.protection.outlook.com"
   ],
...
```

Дополнительные наборы конечных точек не включены в этот пример.

Пример 2. Запрос URI: [https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

В этом примере получены конечные точки для экземпляра Office 365 Worldwide в отношении Exchange Online и зависимостей.

Выходные данные в примере 2 аналогичны таковым в примере 1, но результаты не включают конечные точки для SharePoint Online или Skype для бизнеса Online.

## <a name="changes-web-method"></a>Веб-метод изменений

Веб-метод изменений возвращает самые последние опубликованные обновления. Как правило, это изменения диапазонов IP-адресов и URL-адресов за предыдущий месяц. Наиболее критические изменения для обработки возникают, когда добавляются новые URL-адреса или IP-адреса, так как неудачная попытка добавить IP-адрес в список управления доступом брандмауэра или добавить URL-адрес в список обхода прокси-сервера может привести к простою пользователей Office 365 за этим сетевым устройством. Несмотря на операционные требования, операции _Add_ добавляются с 30-дневным уведомлением до того, как может возникнуть такой простой.

Параметр веб-метода изменений:

- **Version** — обязательный параметр маршрутизации URL-адресов. Используемая в настоящий момент версия, а также изменения после ее выхода. Формат: _ГГГГММДДЧЧ_.

Веб-метод изменений имеет ограничения по частоте, реализованное таким же образом, что и веб-метод конечных точек. Если вы получили HTTP-код отклика 429, вы должны подождать 1 час, прежде чем выполнять вызов еще раз. 

Результат веб-метода изменений — массив записей, каждая из которых представляет изменение в конкретной версии конечной точки. Элементы каждой записи:

- id — неизменяемый идентификатор записи изменения.
- endpointSetId — идентификатор записи набора конечных точек, который был изменен. Обязательный элемент.
- disposition - это может быть либо изменение, добавление или удаление, а также описание того, как именно была изменена запись набора конечных точек. Обязательный элемент.
- impact — не все изменения будут одинаково важны для каждой среды. Данный элемент описывает ожидаемое влияние на среду периметра корпоративной сети в результате этого изменения. Этот атрибут включается только в записи изменений версии 2018112800 и более поздних версий. Доступны следующие варианты для влияния:
  - AddedIp — IP-адрес, который был добавлен в Office 365 и будет доступен в режиме реального времени в ближайшее время. Этот элемент представляет изменения, которые вам необходимо внести для брандмауэра или другого устройства периметра 3 уровня сети. Если вы не добавили данный элемент ранее, прежде чем мы стали использовать его, могут возникать сбои.
  - AddedIp — URL-адрес, который был добавлен в Office 365 и будет доступен в режиме реального времени в ближайшее время. Этот элемент представляет изменения, которые вам необходимо внести для прокси-сервера или устройства сетевого периметра, анализирующее URL-адреса. Если вы не добавили данный элемент ранее, прежде чем мы стали использовать его, могут возникать сбои.
  - AddedIpAndUrl - Были добавлены IP-адрес и URL-адрес. Этот элемент представляет изменение, которое вам необходимо внести на устройстве 3 уровня брандмауэра, прокси-сервере или устройстве анализа URL-адреса. Если вы не добавили данный элемент до того, как мы начали использовать его, могут возникать сбои.
  - RemovedIpOrUrl — Минимум один IP-адрес или URL-адрес был удален из Office 365. Вы должны удалить конечные точки сети со своих устройств периметра, но четкого срока, когда вы должны это сделать, не установлено.
  - ChangedIsExpressRoute — Атрибут поддержки ExpressRoute был изменен. Если вы используете ExpressRoute, может потребоваться выполнение определенных действий в зависимости от вашей конфигурации.
  - MovedIpOrUrl — Мы перенесли IP-адрес или URL-адрес между данным набором конечной точки и другим набором. Как правило, никаких дополнительных действий не требуется.
  - RemovedDuplicateIpOrUrl — Мы удалили повторяющийся IP-адрес или URL-адрес, но он по-прежнему опубликован для Office 365. Обычно никаких действий не требуется.
  - OtherNonPriorityChanges — Мы изменили что-то менее критическое, чем другие прочие параметры, например поле заметки.
- version — версия опубликованного набора конечных точек, в который внесено изменение. Формат номеров версий: _ГГГГММДДЧЧ_, где "ЧЧ" — натуральное число, увеличивающееся, если в один день нужно опубликовать больше одной версии.
- previous — подструктура с подробным указанием предыдущих значений измененных элементов в наборе конечных точек. Не будет включена для новых добавляемых наборов конечных точек. Включает tcpPorts, udpPorts, ExpressRoute, category, required, notes.
- current — подструктура с подробным указанием значений измененных элементов в наборе конечных точек. Включает tcpPorts, udpPorts, ExpressRoute, category, required, notes.
- add — подструктура с подробным указанием элементов, добавляемых в коллекции наборов конечных точек. Опускается, если добавлений нет.
  - effectiveDate определяет дату начала использования добавлений в службе.
  - ips — элементы, которые будут добавлены в массив ips.
  - urls — элементы, добавляемые в массив urls.
- remove — подструктура с подробным указанием элементов, удаляемых из набора конечных точек. Опускается, если удаленных элементов нет.
  - ips — элементы, удаляемые из массива ips.
  - urls — элементы, удаляемые из массива urls.

### <a name="examples"></a>**Примеры**

Пример 1. Запрос URI: [https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

Запрашивает все предыдущие изменения в экземпляре службы Office 365 Worldwide. Пример результата:

```json
[
 {
  "id": 424,
  "endpointSetId": 32,
  "disposition": "Change",
  "version": "2018062700",
  "remove":
   {
    "urls":
     [
      "*.api.skype.com", "skypegraph.skype.com"
     ]
   }
 },
 {
  "id": 426,
  "endpointSetId": 31,
  "disposition": "Change",
  "version": "2018062700",
  "add":
   {
    "effectiveDate": "20180609",
    "ips":
     [
      "51.140.203.190/32"
     ]
   },
  "remove":
   {
    "ips":
     [
...
```

Пример 2. Запрос URI: [https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

Запрашивает изменения, внесенные в экземпляр Office 365 Worldwide после выхода указанной версии. В этом случае указанная версия является последней. Пример результата:

```json
[
  {
    "id":3,
    "endpointSetId":33,
    "changeDescription":"Removing old IP prefixes",
    "disposition":"Change",
    "version":"2018031301",
    "remove":{
      "ips":["65.55.127.0/24","66.119.157.192/26","66.119.158.0/25",
      "111.221.76.128/25","111.221.77.0/26","207.46.5.0/24"]
    }
  },
  {
    "id":4,
    "endpointSetId":45,
    "changeDescription":"Removing old IP prefixes",
    "disposition":"Change",
    "version":"2018031301",
    "remove":{
      "ips":["13.78.93.8/32","40.113.87.220/32","40.114.149.220/32",
      "40.117.100.83/32","40.118.214.164/32","104.208.31.113/32"]
    }
  }
]
```

## <a name="example-powershell-script"></a>**Пример скрипта PowerShell**

Этот скрипт PowerShell позволяет узнать, нужно ли выполнить действия для обновленных данных. Он проверяет номер версии для конечных точек экземпляра Office 365 Worldwide. Если изменение есть, скрипт скачивает конечные точки и фильтрует результаты для категорий &quot;Allow&quot; и &quot;Optimize&quot;. Он также использует уникальный ClientRequestId для нескольких вызовов и сохраняет последнюю версию, обнаруженную во временном файле. Вам нужно вызывать этот скрипт раз в час для проверки наличия обновления версии.

```powershell
# webservice root URL
$ws = "https://endpoints.office.com"
# path where client ID and latest version number will be stored
$datapath = $Env:TEMP + "\endpoints_clientid_latestversion.txt"
# fetch client ID and version if data file exists; otherwise create new file
if (Test-Path $datapath) {
    $content = Get-Content $datapath
    $clientRequestId = $content[0]
    $lastVersion = $content[1]
}
else {
    $clientRequestId = [GUID]::NewGuid().Guid
    $lastVersion = "0000000000"
    @($clientRequestId, $lastVersion) | Out-File $datapath
}
# call version method to check the latest version, and pull new data if version number is different
$version = Invoke-RestMethod -Uri ($ws + "/version/Worldwide?clientRequestId=" + $clientRequestId)
if ($version.latest -gt $lastVersion) {
    Write-Host "New version of Office 365 worldwide commercial service instance endpoints detected"

    # write the new version number to the data file
    @($clientRequestId, $version.latest) | Out-File $datapath
    # invoke endpoints method to get the new data
    $endpointSets = Invoke-RestMethod -Uri ($ws + "/endpoints/Worldwide?clientRequestId=" + $clientRequestId)
    # filter results for Allow and Optimize endpoints, and transform these into custom objects with port and category
    $flatUrls = $endpointSets | ForEach-Object {
        $endpointSet = $_
        $urls = $(if ($endpointSet.urls.Count -gt 0) { $endpointSet.urls } else { @() })
        $urlCustomObjects = @()
        if ($endpointSet.category -in ("Allow", "Optimize")) {
            $urlCustomObjects = $urls | ForEach-Object {
                [PSCustomObject]@{
                    category = $endpointSet.category;
                    url      = $_;
                    tcpPorts = $endpointSet.tcpPorts;
                    udpPorts = $endpointSet.udpPorts;
                }
            }
        }
        $urlCustomObjects
    }
    $flatIps = $endpointSets | ForEach-Object {
        $endpointSet = $_
        $ips = $(if ($endpointSet.ips.Count -gt 0) { $endpointSet.ips } else { @() })
        # IPv4 strings have dots while IPv6 strings have colons
        $ip4s = $ips | Where-Object { $_ -like '*.*' }

        $ipCustomObjects = @()
        if ($endpointSet.category -in ("Allow", "Optimize")) {
            $ipCustomObjects = $ip4s | ForEach-Object {
                [PSCustomObject]@{
                    category = $endpointSet.category;
                    ip = $_;
                    tcpPorts = $endpointSet.tcpPorts;
                    udpPorts = $endpointSet.udpPorts;
                }
            }
        }
        $ipCustomObjects
    }
    Write-Output "IPv4 Firewall IP Address Ranges"
    ($flatIps.ip | Sort-Object -Unique) -join "," | Out-String
    Write-Output "URLs for Proxy Server"
    ($flatUrls.url | Sort-Object -Unique) -join "," | Out-String
    # TODO Call Send-MailMessage with new endpoints data
}
else {
    Write-Host "Office 365 worldwide commercial service instance endpoints are up-to-date"
}
```

## <a name="example-python-script"></a>**Пример скрипта на Python**

Ниже показан скрипт на Python, протестированный с использованием Python 3.6.3 на Windows 10. Он позволяет узнать, нужно ли выполнить действия для обновленных данных, проверяя номер версии для конечных точек экземпляра Office 365 Worldwide. Если изменение есть, скрипт скачивает конечные точки и фильтрует результаты для категорий _Allow_ и _Optimize_. Он также использует уникальный ClientRequestId для нескольких вызовов и сохраняет последнюю версию, обнаруженную во временном файле. Вам нужно вызывать этот скрипт раз в час для проверки наличия обновления версии.

```python
import json
import os
import urllib.request
import uuid
# helper to call the webservice and parse the response
def webApiGet(methodName, instanceName, clientRequestId):
    ws = "https://endpoints.office.com"
    requestPath = ws + '/' + methodName + '/' + instanceName + '?clientRequestId=' + clientRequestId
    request = urllib.request.Request(requestPath)
    with urllib.request.urlopen(request) as response:
        return json.loads(response.read().decode())
# path where client ID and latest version number will be stored
datapath = os.environ['TEMP'] + '\endpoints_clientid_latestversion.txt'
# fetch client ID and version if data exists; otherwise create new file
if os.path.exists(datapath):
    with open(datapath, 'r') as fin:
        clientRequestId = fin.readline().strip()
        latestVersion = fin.readline().strip()
else:
    clientRequestId = str(uuid.uuid4())
    latestVersion = '0000000000'
    with open(datapath, 'w') as fout:
        fout.write(clientRequestId + '\n' + latestVersion)
# call version method to check the latest version, and pull new data if version number is different
version = webApiGet('version', 'Worldwide', clientRequestId)
if version['latest'] > latestVersion:
    print('New version of Office 365 worldwide commercial service instance endpoints detected')
    # write the new version number to the data file
    with open(datapath, 'w') as fout:
        fout.write(clientRequestId + '\n' + version['latest'])
    # invoke endpoints method to get the new data
    endpointSets = webApiGet('endpoints', 'Worldwide', clientRequestId)
    # filter results for Allow and Optimize endpoints, and transform these into tuples with port and category
    flatUrls = []
    for endpointSet in endpointSets:
        if endpointSet['category'] in ('Optimize', 'Allow'):
            category = endpointSet['category']
            urls = endpointSet['urls'] if 'urls' in endpointSet else []
            tcpPorts = endpointSet['tcpPorts'] if 'tcpPorts' in endpointSet else ''
            udpPorts = endpointSet['udpPorts'] if 'udpPorts' in endpointSet else ''
            flatUrls.extend([(category, url, tcpPorts, udpPorts) for url in urls])
    flatIps = []
    for endpointSet in endpointSets:
        if endpointSet['category'] in ('Optimize', 'Allow'):
            ips = endpointSet['ips'] if 'ips' in endpointSet else []
            category = endpointSet['category']
            # IPv4 strings have dots while IPv6 strings have colons
            ip4s = [ip for ip in ips if '.' in ip]
            tcpPorts = endpointSet['tcpPorts'] if 'tcpPorts' in endpointSet else ''
            udpPorts = endpointSet['udpPorts'] if 'udpPorts' in endpointSet else ''
            flatIps.extend([(category, ip, tcpPorts, udpPorts) for ip in ip4s])
    print('IPv4 Firewall IP Address Ranges')
    print(','.join(sorted(set([ip for (category, ip, tcpPorts, udpPorts) in flatIps]))))
    print('URLs for Proxy Server')
    print(','.join(sorted(set([url for (category, url, tcpPorts, udpPorts) in flatUrls]))))

    # TODO send mail (e.g. with smtplib/email modules) with new endpoints data
else:
    print('Office 365 worldwide commercial service instance endpoints are up-to-date')
```

## <a name="web-service-interface-versioning"></a>**Управление версиями интерфейса веб-службы**

В будущем могут понадобиться обновления параметров или результатов для этих методов веб-служб. После публикации общедоступной версии веб-служб корпорация Майкрософт примет разумные меры для заблаговременного уведомления о существенных обновлениях веб-службы. Если корпорация Майкрософт сочтет, что обновление потребует изменений клиентов, использующих веб-службы, она сохранит доступ к предыдущей версии веб-службы в течение как минимум 12 месяцев после выпуска новой версии. Пользователи, которые не выполнят обновление в течение этого времени, могут лишиться доступа к веб-службе и ее методам. Пользователи должны убедиться, что клиенты веб-службы продолжат работать без ошибок, если такие изменения будут внесены в подпись интерфейса веб-службы:

- Добавление нового необязательного параметра к существующему веб-методу, который необязательно должны предоставлять старые клиенты и который не влияет на результат, получаемый старым клиентом.
- Добавление нового именованного атрибута в один из элементов REST отклика или дополнительных столбцов в файл CSV отклика.
- Добавление нового веб-метода с новым именем, который не вызывается старыми клиентами.

## <a name="related-topics"></a>Статьи по теме
  
[Диапазоны IP-адресов и URL-адреса Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Вопросы и ответы о конечных точках Office 365](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)

[Принципы сетевого подключения к Office 365](office-365-network-connectivity-principles.md)

[Сеть Office 365 и настройка производительности](network-planning-and-performance.md)

[Сетевое подключение к Office 365](network-connectivity.md)
  
[Качество мультимедиа и характеристики сетевого подключения в случае Skype для бизнеса Online](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[Оптимизация сети для Skype для бизнеса Online](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)

[Настройка производительности Office 365 с помощью базовых показателей и журнала производительности](performance-tuning-using-baselines-and-history.md)
  
[План устранения проблем с производительностью Office 365](performance-troubleshooting-plan.md)
