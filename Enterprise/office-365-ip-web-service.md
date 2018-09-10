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
ms.openlocfilehash: 3abd6a0692ae4d66c76f8c0d65653b83646c6e23
ms.sourcegitcommit: d07feeba2e886febc6a57a5c33b0df02b3db5631
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/04/2018
ms.locfileid: "23830896"
---
# <a name="office-365-ip-address-and-url-web-service"></a><span data-ttu-id="cacfd-104">**Веб-служба IP-адресов и URL-адресов в Office 365**</span><span class="sxs-lookup"><span data-stu-id="cacfd-104">**Office 365 IP Address and URL Web service**</span></span>

<span data-ttu-id="cacfd-p102">Чтобы помочь вам выявлять и дифференцировать сетевой трафик Office 365, новая веб-служба публикует конечные точки Office 365, упрощая оценку, настройку и обновление. Эта новая веб-служба заменяет собой скачиваемые XML-файлы, доступные в настоящее время. Прекращение поддержки формата XML планируется на 2 октября 2018 г.</span><span class="sxs-lookup"><span data-stu-id="cacfd-p102">To help you better identify and differentiate Office 365 network traffic, a new web service publishes Office 365 endpoints, making it easier for you to evaluate, configure, and stay up to date with changes. This new web service replaces the XML downloadable files that are currently available. The XML format is planned to be phased out on October 2, 2018.</span></span>

<span data-ttu-id="cacfd-p103">Будучи клиентом или поставщиком устройств сети периметра, вы можете создавать решения с использованием новой веб-службы на основе REST для записей FQDN и IP-адресов в Office 365. Доступ к данным можно получить непосредственно в браузере с помощью этих URL-адресов.</span><span class="sxs-lookup"><span data-stu-id="cacfd-p103">As a customer or a network perimeter device vendor, you can build against the new REST-based web service for the Office 365 IP address and FQDN entries. You can access the data directly in a web browser using these URLs.</span></span>

- <span data-ttu-id="cacfd-110">Для получения последней версии диапазонов IP-адресов и URL-адресов Office 365 перейдите на веб-страницу [https://endpoints.office.com/version](https://endpoints.office.com/version?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span><span class="sxs-lookup"><span data-stu-id="cacfd-110">For the latest version of the Office 365 URLs and IP address ranges, use [https://endpoints.office.com/version](https://endpoints.office.com/version?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span></span>
- <span data-ttu-id="cacfd-111">Для получения данных на странице диапазонов IP-адресов и URL-адресов Office 365 для брандмауэров и прокси-серверов перейдите на веб-страницу [https://endpoints.office.com/endpoints/worldwide](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span><span class="sxs-lookup"><span data-stu-id="cacfd-111">For the data on the Office 365 URLs and IP address ranges page for firewalls and proxy servers, use [https://endpoints.office.com/endpoints/worldwide](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span></span>
- <span data-ttu-id="cacfd-112">Для получения всех последних изменений с конца июля 2018 года (тогда стала доступной веб-служба) перейдите на веб-страницу [https://endpoints.office.com/changes/worldwide/0000000000](https://endpoints.office.com/changes/worldwide/0000000000?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span><span class="sxs-lookup"><span data-stu-id="cacfd-112">To get all the latest changes since the end of July 2018 when the web service was first available, use [https://endpoints.office.com/changes/worldwide/0000000000](https://endpoints.office.com/changes/worldwide/0000000000?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span></span>

<span data-ttu-id="cacfd-113">Как клиент вы можете использовать эту веб-службу, чтобы:</span><span class="sxs-lookup"><span data-stu-id="cacfd-113">As a customer, you can use this web service to:</span></span>

- <span data-ttu-id="cacfd-114">обновлять скрипты PowerShell для получения данных конечной точки Office 365 и изменять форматирование для сетевых устройств;</span><span class="sxs-lookup"><span data-stu-id="cacfd-114">Update your PowerShell scripts to obtain Office 365 endpoint data and modify any formatting for your networking devices.</span></span>
- <span data-ttu-id="cacfd-115">применять эту информацию для обновления PAC-файлов, развернутых на клиентских компьютерах.</span><span class="sxs-lookup"><span data-stu-id="cacfd-115">Use this information to update PAC files deployed to client computers.</span></span>

<span data-ttu-id="cacfd-116">Как поставщик устройств сети периметра вы можете использовать эту веб-службу, чтобы:</span><span class="sxs-lookup"><span data-stu-id="cacfd-116">As a network perimeter device vendor, you can use this web service to:</span></span>

- <span data-ttu-id="cacfd-117">создавать и тестировать программное обеспечение устройств для скачивания списка с целью автоматической настройки;</span><span class="sxs-lookup"><span data-stu-id="cacfd-117">Create and test device software to download the list for automated configuration.</span></span>
- <span data-ttu-id="cacfd-118">проверять текущую версию;</span><span class="sxs-lookup"><span data-stu-id="cacfd-118">Check for the current version.</span></span>
- <span data-ttu-id="cacfd-119">получать текущие изменения.</span><span class="sxs-lookup"><span data-stu-id="cacfd-119">Get the current changes.</span></span>

<span data-ttu-id="cacfd-120">Дополнительные сведения:</span><span class="sxs-lookup"><span data-stu-id="cacfd-120">For additional information about planning backups, see:</span></span>

- [<span data-ttu-id="cacfd-121">Объявление в записи блога на форуме Tech Community Office 365.</span><span class="sxs-lookup"><span data-stu-id="cacfd-121">Announcement blog post in the Office 365 Tech Community Forum</span></span>](https://techcommunity.microsoft.com/t5/Office-365-Blog/Announcing-Office-365-endpoint-categories-and-Office-365-IP/ba-p/177638)
- [<span data-ttu-id="cacfd-122">Форум Tech Community Office 365, содержащий сведения об использовании веб-служб.</span><span class="sxs-lookup"><span data-stu-id="cacfd-122">Office 365 Tech Community Forum for questions about use of the web services</span></span>](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)

## <a name="common-parameters"></a><span data-ttu-id="cacfd-123">**Общие параметры**</span><span class="sxs-lookup"><span data-stu-id="cacfd-123">**Common parameters**</span></span>

<span data-ttu-id="cacfd-124">Эти параметры являются общими для всех методов веб-службы:</span><span class="sxs-lookup"><span data-stu-id="cacfd-124">These parameters are common across all the web service methods:</span></span>

- <span data-ttu-id="cacfd-p104">**format=CSV | JSON**. Параметр строки запроса. По умолчанию данные возвращаются в формате JSON. Включайте этот необязательный параметр для возврата данных в формате значений с разделителями-запятыми (CSV).</span><span class="sxs-lookup"><span data-stu-id="cacfd-p104">**format=CSV | JSON** - Query string parameter. By default, the returned data format is JSON. Include this optional parameter to return the data in comma-separated values (CSV) format.</span></span>
- <span data-ttu-id="cacfd-p105">**ClientRequestId**. Параметр строки запроса. Обязательный GUID, который вы создаете для связи клиента. Нужно создавать GUID для каждого компьютера, который вызывает веб-службу. Не используйте GUID, показанные в примерах ниже, так как они могут быть заблокированы веб-службой в будущем. Формат GUID следующий: _xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx_. Здесь "x" означает шестнадцатеричное число. Для создания GUID используйте команду [New-Guid](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-guid?view=powershell-6) PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cacfd-p105">**ClientRequestId** - Query string parameter. A required GUID that you generate for client association. You should generate a GUID for each machine that calls the web service. Do not use the GUIDs shown in the following examples because they may be blocked by the web service in the future. GUID format is _xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx_, where x represents a hexadecimal number. To generate a GUID, use the [New-Guid](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-guid?view=powershell-6) PowerShell command.</span></span>

## <a name="version-web-method"></a><span data-ttu-id="cacfd-134">**Веб-метод версии**</span><span class="sxs-lookup"><span data-stu-id="cacfd-134">**Version web method**</span></span>

<span data-ttu-id="cacfd-p106">Майкрософт обновляет записи IP-адресов и FQDN Office 365 в конце каждого месяца и иногда вне цикла для выполнения операционных требований или требований поддержки. Данным для каждого опубликованного экземпляра назначается номер версии. Веб-метод версии позволяет проводить опрос для получения последней версии каждого экземпляра службы Office 365. Рекомендуем проверять версию ежедневно (максимум ежечасно). Появление новых версий ожидается в начале каждого месяца. Иногда ввиду инцидентов поддержки, безопасности или других операционных требований новые версии будут появляться в течение месяца.</span><span class="sxs-lookup"><span data-stu-id="cacfd-p106">Microsoft updates the Office 365 IP address and FQDN entries at the end of each month and occasionally out of cycle for operational or support requirements. The data for each published instance is assigned a version number. The version web method lets you poll for the latest version for each Office 365 service instance. We recommend you check the version daily, or at the most, hourly. New versions should be expected at the start of each month. Sometimes due to support incident, security, or other operational requirements there will be new versions during the month.</span></span>

<span data-ttu-id="cacfd-141">Для веб-метода версии предусмотрен один параметр:</span><span class="sxs-lookup"><span data-stu-id="cacfd-141">There is one parameter for the version web method:</span></span>

- <span data-ttu-id="cacfd-p107">**AllVersions=true**. Параметр строки запроса. По умолчанию возвращается последний номер версии. Включите этот дополнительный параметр для запроса всех опубликованных версий.</span><span class="sxs-lookup"><span data-stu-id="cacfd-p107">**AllVersions=true** - Query string parameter. By default, the version returned is the latest. Include this optional parameter to request all published versions.</span></span>
- <span data-ttu-id="cacfd-p108">**Format=JSON** | **CSV** | **RSS**. Кроме форматов JSON и CSV, веб-метод версии поддерживает RSS. Вы можете использовать его вместе с параметром allVersions=true для запрашивания RSS-канала, который можно применять в Outlook или других средствах чтения RSS.</span><span class="sxs-lookup"><span data-stu-id="cacfd-p108">**Format=JSON** | **CSV** | **RSS** – In addition to the JSON and CSV formats, the version web method also supports RSS. You can use this along with the allVersions=true parameter to request an RSS feed which can be used with Outlook or other RSS readers.</span></span>
- <span data-ttu-id="cacfd-p109">**Instance**. Параметр маршрутизации. Этот необязательный параметр указывает экземпляр, для которого возвращается версия. Если его опустить, будут возвращены все экземпляры. Допустимые экземпляры: Worldwide, China, Germany, USGovDoD, USGovGCCHigh.</span><span class="sxs-lookup"><span data-stu-id="cacfd-p109">**Instance** - Route parameter. This optional parameter specifies the instance to return the version for. If omitted, all instances are returned. Valid instances are: Worldwide, China, Germany, USGovDoD, USGovGCCHigh</span></span>

<span data-ttu-id="cacfd-p110">Результат из веб-метода версии может быть одной записью или массивом записей. Ниже перечислены элементы каждой записи.</span><span class="sxs-lookup"><span data-stu-id="cacfd-p110">The result from the version web method may be a single record or an array of records. The elements of each record are:</span></span>

- <span data-ttu-id="cacfd-153">instance — короткое имя экземпляра службы Office 365.</span><span class="sxs-lookup"><span data-stu-id="cacfd-153">instance - The short name of the Office 365 service instance.</span></span>
- <span data-ttu-id="cacfd-154">latest — последняя версия для конечных точек указанного экземпляра.</span><span class="sxs-lookup"><span data-stu-id="cacfd-154">latest - The latest version for endpoints of the specified instance.</span></span>
- <span data-ttu-id="cacfd-p111">versions — список всех предыдущих версий для указанного экземпляра. Этот элемент включен, только если параметр AllVersions имеет значение true.</span><span class="sxs-lookup"><span data-stu-id="cacfd-p111">versions - A list of all previous versions for the specified instance. This element is only included if the AllVersions parameter is true.</span></span>

### <a name="examples"></a><span data-ttu-id="cacfd-157">**Примеры**</span><span class="sxs-lookup"><span data-stu-id="cacfd-157">**Examples:**</span></span>

<span data-ttu-id="cacfd-158">Пример 1. Запрос URI: [https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="cacfd-158">Example 1 request URI: [https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="cacfd-p112">Этот URI возвращает последнюю версию каждого экземпляра службы Office 365. Пример результата:</span><span class="sxs-lookup"><span data-stu-id="cacfd-p112">This URI returns the latest version of each Office 365 service instance. Example result:</span></span>

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

[!IMPORTANT]
<span data-ttu-id="cacfd-p113">GUID для параметра ClientRequestID в этих URI приведен только в качестве примера. Чтобы попробовать применить URI веб-службы, создайте собственный GUID. GUID, показанные в этих примерах, могут быть заблокированы веб-службой в будущем.</span><span class="sxs-lookup"><span data-stu-id="cacfd-p113">The GUID for the ClientRequestID parameter in these URIs are only an example. To try the web service URIs out, generate your own GUID. The GUIDs shown in these examples may be blocked by the web service in the future.</span></span>

<span data-ttu-id="cacfd-164">Пример 2. Запрос URI: [https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="cacfd-164">Example 2 request URI: [https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="cacfd-p114">Этот URI возвращает последнюю версию указанного экземпляра службы Office 365. Пример результата:</span><span class="sxs-lookup"><span data-stu-id="cacfd-p114">This URI returns the latest version of the specified Office 365 service instance. Example result:</span></span>

```json
{
 "instance": "Worldwide",
 "latest": "2018063000"
}

```

<span data-ttu-id="cacfd-167">Пример 3. Запрос URI: [https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="cacfd-167">Example 3 request URI: [https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="cacfd-p115">Этот URI показывает выходные данные в формате CSV. Пример результата:</span><span class="sxs-lookup"><span data-stu-id="cacfd-p115">This URI shows output in CSV format. Example result:</span></span>

```csv
instance,latest
Worldwide,2018063000
```

<span data-ttu-id="cacfd-170">Пример 4. Запрос URI: [https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="cacfd-170">Example 4 request URI: [https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="cacfd-p116">Этот URI показывает все более ранние версии, которые были опубликованы для экземпляра службы Office 365 Worldwide. Пример результата:</span><span class="sxs-lookup"><span data-stu-id="cacfd-p116">This URI shows all prior versions that have been published for the Office 365 worldwide service instance. Example result:</span></span>

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

<span data-ttu-id="cacfd-173">Пример 5. URI RSS-канала: [https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS](https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS)</span><span class="sxs-lookup"><span data-stu-id="cacfd-173">Example 5 RSS Feed URI: [https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS](https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS)</span></span>

<span data-ttu-id="cacfd-p117">Этот URI показывает RSS-канал опубликованных версий, которые содержат ссылки на список изменений для каждой версии. Пример результата:</span><span class="sxs-lookup"><span data-stu-id="cacfd-p117">This URI shows an RSS feed of the published versions that include links to the list of changes for each version. Example result:</span></span>

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

## <a name="endpoints-web-method"></a><span data-ttu-id="cacfd-176">**Веб-метод конечных точек**</span><span class="sxs-lookup"><span data-stu-id="cacfd-176">**Endpoints web method**</span></span>

<span data-ttu-id="cacfd-p118">Веб-метод конечных точек возвращает все записи для диапазонов IP-адресов и URL-адресов, входящих в службу Office 365. Хотя для настройки сетевого устройства нужно использовать новейшие данные от веб-метода конечных точек, данные можно кэшировать на 30 дней после их публикации ввиду заблаговременного уведомления в отношении дополнений. Параметры веб-метода конечных точек показаны ниже.</span><span class="sxs-lookup"><span data-stu-id="cacfd-p118">The endpoints web method returns all records for IP address ranges and URLs that make up the Office 365 service. While the latest data from the endpoints web method should be used for network device configuration, the data can be cached for up to 30 days after it is published due to the advance notice provided for additions. Parameters for the endpoints web method are:</span></span>

- <span data-ttu-id="cacfd-p119">**ServiceAreas**. Параметр строки запроса. Список областей обслуживания, разделенных запятыми. Допустимые элементы: Common, Exchange, SharePoint, Skype. Так как элементы области обслуживания Common обязательны для всех других областей обслуживания, веб-служба всегда будет их включать. Если не включить этот параметр, будут возвращены все области обслуживания.</span><span class="sxs-lookup"><span data-stu-id="cacfd-p119">**ServiceAreas** - Query string parameter. A comma-separated list of service areas. Valid items are Common,Exchange,SharePoint,Skype. Because Common service area items are a prerequisite for all other service areas, the web service will always include them. If you do not include this parameter, all service areas are returned.</span></span>
- <span data-ttu-id="cacfd-p120">**TenantName**. Параметр строки запроса. Имя клиента Office 365. Веб-служба получает предоставленное вами имя и вставляет его в части URL-адресов, которые включают имя клиента. Если вы не предоставляете имя клиента, эти части URL-адресов будут содержать подстановочный знак (\*).</span><span class="sxs-lookup"><span data-stu-id="cacfd-p120">**TenantName** - Query string parameter. Your Office 365 tenant name. The web service takes your provided name and inserts it in parts of URLs that include the tenant name. If you don't provide a tenant name, those parts of URLs have the wildcard character (\*).</span></span>
- <span data-ttu-id="cacfd-p121">**NoIPv6**. Параметр строки запроса. Установите для него значение true, чтобы исключить адреса IPv6 из выходных данных (например, если в вашей сети не используется IPv6).</span><span class="sxs-lookup"><span data-stu-id="cacfd-p121">**NoIPv6** - Query string parameter. Set this to true to exclude IPv6 addresses from the output, for example, if you don't use IPv6 in your network.</span></span>
- <span data-ttu-id="cacfd-p122">**Instance**. Параметр маршрутизации. Этот обязательный параметр указывает экземпляр, для которого должны быть возвращены конечные точки. Допустимые экземпляры: Worldwide, China, Germany, USGovDoD, USGovGCCHigh.</span><span class="sxs-lookup"><span data-stu-id="cacfd-p122">**Instance** - Route parameter. This required parameter specifies the instance to return the endpoints for. Valid instances are: Worldwide, China, Germany, USGovDoD, USGovGCCHigh.</span></span>

<span data-ttu-id="cacfd-p123">Результат веб-метода конечных точек — массив, в который входят все записи, представляющие набор конечных точек. Элементы каждой записи:</span><span class="sxs-lookup"><span data-stu-id="cacfd-p123">The result from the endpoints web method is an array of records with each record representing an endpoint set. The elements for each record are:</span></span>

- <span data-ttu-id="cacfd-196">id — неизменяемый идентификатор набора конечных точек.</span><span class="sxs-lookup"><span data-stu-id="cacfd-196">id - The immutable id number of the endpoint set.</span></span>
- <span data-ttu-id="cacfd-197">serviceArea — область обслуживания, которая является частью Common, Exchange, SharePoint или Skype.</span><span class="sxs-lookup"><span data-stu-id="cacfd-197">serviceArea - The service area that this is part of: Common, Exchange, SharePoint, or Skype.</span></span>
- <span data-ttu-id="cacfd-p124">urls — URL-адреса для набора конечных точек. Массив JSON записей DNS. Если значение не указано, опускается.</span><span class="sxs-lookup"><span data-stu-id="cacfd-p124">urls - URLs for the endpoint set. A JSON array of DNS records. Omitted if blank.</span></span>
- <span data-ttu-id="cacfd-p125">tcpPorts — TCP-порты для набора конечных точек. Все элементы портов отформатированы в виде списка портов с разделителями-запятыми или диапазонов портов, разделенных символами дефиса (-). Порты применяются ко всем IP-адресам и всем URL-адресам в этом наборе конечных точек для этой категории. Если значение не указано, опускается.</span><span class="sxs-lookup"><span data-stu-id="cacfd-p125">tcpPorts - TCP ports for the endpoint set. All ports elements are formatted as a comma-separated list of ports or port ranges separated by a dash character (-). Ports apply to all IP addresses and all URLs in that endpoint set for that category. Omitted if blank.</span></span>
- <span data-ttu-id="cacfd-p126">udpPorts — порты UDP для диапазонов IP-адресов в этом наборе конечных точек. Если значение не указано, опускается.</span><span class="sxs-lookup"><span data-stu-id="cacfd-p126">udpPorts - UDP ports for the IP address ranges in this endpoint set. Omitted if blank.</span></span>
- <span data-ttu-id="cacfd-p127">ips — диапазоны IP-адресов, связанные с этим набором конечных точек (с перечисленными портами TCP или UDP). Массив JSON диапазонов IP-адресов. Если значение не указано, опускается.</span><span class="sxs-lookup"><span data-stu-id="cacfd-p127">ips - The IP address ranges associated with this endpoint set as associated with the listed TCP or UDP ports. A JSON array of IP Address ranges. Omitted if blank.</span></span>
- <span data-ttu-id="cacfd-p128">category — категория возможности подключения к набору конечных точек. Допустимые значения: Optimize, Allow и Default. Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="cacfd-p128">category - The connectivity category for the endpoint set. Valid values are Optimize, Allow, and Default. Required.</span></span>
- <span data-ttu-id="cacfd-213">expressRoute имеет значение True или False, если для этого набора конечных точек выполняется маршрутизация через ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="cacfd-213">expressRoute - True or False if this endpoint set is routed over ExpressRoute.</span></span>
- <span data-ttu-id="cacfd-p129">required имеет значение True, если этот набор конечных точек требуется для подключения к Office 365. False, если этот набор конечных точек необязателен.</span><span class="sxs-lookup"><span data-stu-id="cacfd-p129">required - True if this endpoint set is required to have connectivity for Office 365 to be supported. False if this endpoint set is optional.</span></span>
- <span data-ttu-id="cacfd-p130">notes — текст, который в случае необязательных конечных точек описывает функциональность Office 365, которая будет отсутствовать, если IP-адреса или URL-адреса в этом наборе конечных точек не могут быть доступны на сетевом уровне. Если значение не указано, опускается.</span><span class="sxs-lookup"><span data-stu-id="cacfd-p130">notes - For optional endpoints, this text describes Office 365 functionality that will be missing if IP addresses or URLs in this endpoint set cannot be accessed at the network layer. Omitted if blank.</span></span>

### <a name="examples"></a><span data-ttu-id="cacfd-218">Примеры</span><span class="sxs-lookup"><span data-stu-id="cacfd-218">Examples:</span></span>

<span data-ttu-id="cacfd-219">Пример 1. Запрос URI: [https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="cacfd-219">Example 1 request URI: [https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="cacfd-p131">Этот URI получает все конечные точки для экземпляра Office 365 Worldwide для всех рабочих нагрузок. В примере результата показан фрагмент выходных данных:</span><span class="sxs-lookup"><span data-stu-id="cacfd-p131">This URI obtains all endpoints for the Office 365 worldwide instance for all workloads. Example result showing an excerpt of the output:</span></span>

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

<span data-ttu-id="cacfd-222">Дополнительные наборы конечных точек не включены в этот пример.</span><span class="sxs-lookup"><span data-stu-id="cacfd-222">Additional endpoint sets are not included in this example.</span></span>

<span data-ttu-id="cacfd-223">Пример 2. Запрос URI: [https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="cacfd-223">Example 2 request URI: [https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="cacfd-224">В этом примере получены конечные точки для экземпляра Office 365 Worldwide в отношении Exchange Online и зависимостей.</span><span class="sxs-lookup"><span data-stu-id="cacfd-224">This example obtains endpoints for the Office 365 Worldwide instance for Exchange Online and dependencies only.</span></span>

<span data-ttu-id="cacfd-225">Выходные данные в примере 2 аналогичны таковым в примере 1, но результаты не включают конечные точки для SharePoint Online или Skype для бизнеса Online.</span><span class="sxs-lookup"><span data-stu-id="cacfd-225">The output for example 2 is similar to example 1 except that the results will not include endpoints for SharePoint Online or Skype for Business Online.</span></span>

## <a name="changes-web-method"></a><span data-ttu-id="cacfd-226">Веб-метод изменений</span><span class="sxs-lookup"><span data-stu-id="cacfd-226">Changes web method</span></span>

<span data-ttu-id="cacfd-p132">Веб-метод изменений возвращает самые последние опубликованные обновления. Как правило, это изменения диапазонов IP-адресов и URL-адресов за предыдущий месяц. Наиболее критические изменения для обработки возникают, когда добавляются новые URL-адреса или IP-адреса, так как неудачная попытка добавить IP-адрес в список управления доступом брандмауэра или добавить URL-адрес в список обхода прокси-сервера может привести к простою пользователей Office 365 за этим сетевым устройством. Несмотря на операционные требования, операции _Add_ добавляются с 30-дневным уведомлением до того, как может возникнуть такой простой.</span><span class="sxs-lookup"><span data-stu-id="cacfd-p132">The changes web method returns the most recent updates that have been published. This is typically the previous month's changes to IP address ranges and URLs. The most critical changes to be processed are when new URLs or IP Addresses are added since failing to add an IP Address to a firewall access control list, or a URL to a proxy server bypass list can cause an outage for Office 365 users behind that network device. Notwithstanding operational requirements, _Add_ operations are added with 30 days' notice before such an outage would occur.</span></span>

<span data-ttu-id="cacfd-231">Параметр веб-метода изменений:</span><span class="sxs-lookup"><span data-stu-id="cacfd-231">The parameter for the changes web method is:</span></span>

- <span data-ttu-id="cacfd-p133">**Version** — обязательный параметр маршрутизации URL-адресов. Используемая в настоящий момент версия, а также изменения после ее выхода. Формат: _ГГГГММДДЧЧ_.</span><span class="sxs-lookup"><span data-stu-id="cacfd-p133">**Version** - Required URL route parameter. The version that you have currently implemented, and you want to see the changes since that version. The format is _YYYYMMDDNN_.</span></span>

<span data-ttu-id="cacfd-p134">Результат веб-метода изменений — массив записей, каждая из которых представляет изменение в конкретной версии конечной точки. Элементы каждой записи:</span><span class="sxs-lookup"><span data-stu-id="cacfd-p134">The result from the changes web method is an array of records with each record representing a change in a specific version of the endpoints. The elements for each record are:</span></span>

- <span data-ttu-id="cacfd-237">id — неизменяемый идентификатор записи изменения.</span><span class="sxs-lookup"><span data-stu-id="cacfd-237">id - The immutable id of the change record.</span></span>
- <span data-ttu-id="cacfd-p135">endpointSetId — идентификатор записи набора конечных точек, который был изменен. Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="cacfd-p135">endpointSetId - The ID of the endpoint set record that is changed. Required.</span></span>
- <span data-ttu-id="cacfd-p136">disposition может представлять изменение, добавление или удаление. Описывает, как именно была изменена запись набора конечных точек. Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="cacfd-p136">disposition - This can be either of change, add, or remove and describes what the change did to the endpoint set record. Required.</span></span>
- <span data-ttu-id="cacfd-p137">version — версия опубликованного набора конечных точек, в который внесено изменение. Формат номеров версий: _ГГГГММДДЧЧ_, где "ЧЧ" — натуральное число, увеличивающееся, если в один день нужно опубликовать больше одной версии.</span><span class="sxs-lookup"><span data-stu-id="cacfd-p137">version - The version of the published endpoint set in which the change was introduced. Version numbers are of the format _YYYYMMDDNN_, where NN is a natural number incremented if there are multiple versions required to be published on a single day.</span></span>
- <span data-ttu-id="cacfd-p138">previous — подструктура с подробным указанием предыдущих значений измененных элементов в наборе конечных точек. Не будет включена для новых добавляемых наборов конечных точек. Включает tcpPorts, udpPorts, ExpressRoute, category, required, notes.</span><span class="sxs-lookup"><span data-stu-id="cacfd-p138">previous - A substructure detailing previous values of changed elements on the endpoint set. This will not be included for newly added endpoint sets. Includes tcpPorts, udpPorts, ExpressRoute, category, required, notes.</span></span>
- <span data-ttu-id="cacfd-p139">current — подструктура с подробным указанием значений измененных элементов в наборе конечных точек. Включает tcpPorts, udpPorts, ExpressRoute, category, required, notes.</span><span class="sxs-lookup"><span data-stu-id="cacfd-p139">current - A substructure detailing updated values of changes elements on the endpoint set. Includes tcpPorts, udpPorts, ExpressRoute, category, required, notes.</span></span>
- <span data-ttu-id="cacfd-p140">add — подструктура с подробным указанием элементов, добавляемых в коллекции наборов конечных точек. Опускается, если добавлений нет.</span><span class="sxs-lookup"><span data-stu-id="cacfd-p140">add - A substructure detailing items to be added to endpoint set collections. Omitted if there are no additions.</span></span>
  - <span data-ttu-id="cacfd-251">effectiveDate определяет дату начала использования добавлений в службе.</span><span class="sxs-lookup"><span data-stu-id="cacfd-251">effectiveDate - Defines the data when the additions will be live in the service.</span></span>
  - <span data-ttu-id="cacfd-252">ips — элементы, которые будут добавлены в массив ips.</span><span class="sxs-lookup"><span data-stu-id="cacfd-252">ips - Items to be added to the ips array.</span></span>
  - <span data-ttu-id="cacfd-253">urls — элементы, добавляемые в массив urls.</span><span class="sxs-lookup"><span data-stu-id="cacfd-253">urls- Items to be added to the urls array.</span></span>
- <span data-ttu-id="cacfd-p141">remove — подструктура с подробным указанием элементов, удаляемых из набора конечных точек. Опускается, если удаленных элементов нет.</span><span class="sxs-lookup"><span data-stu-id="cacfd-p141">remove - A substructure detailing items to be removed from the endpoint set. Omitted if there are no removals.</span></span>
  - <span data-ttu-id="cacfd-256">ips — элементы, удаляемые из массива ips.</span><span class="sxs-lookup"><span data-stu-id="cacfd-256">ips - Items to be removed from the ips array.</span></span>
  - <span data-ttu-id="cacfd-257">urls — элементы, удаляемые из массива urls.</span><span class="sxs-lookup"><span data-stu-id="cacfd-257">urls- Items to be removed from the urls array.</span></span>

### <a name="examples"></a><span data-ttu-id="cacfd-258">**Примеры**</span><span class="sxs-lookup"><span data-stu-id="cacfd-258">**Examples:**</span></span>

<span data-ttu-id="cacfd-259">Пример 1. Запрос URI: [https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="cacfd-259">Example 1 request URI: [https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="cacfd-p142">Запрашивает все предыдущие изменения в экземпляре службы Office 365 Worldwide. Пример результата:</span><span class="sxs-lookup"><span data-stu-id="cacfd-p142">This requests all previous changes to the Office 365 worldwide service instance. Example result:</span></span>

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

<span data-ttu-id="cacfd-262">Пример 2. Запрос URI: [https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="cacfd-262">Example 2 request URI: [https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="cacfd-p143">Запрашивает изменения, внесенные в экземпляр Office 365 Worldwide после выхода указанной версии. В этом случае указанная версия является последней. Пример результата:</span><span class="sxs-lookup"><span data-stu-id="cacfd-p143">This requests changes since the specified version to the Office 365 Worldwide instance. In this case, the version specified is the latest. Example result:</span></span>

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

## <a name="example-powershell-script"></a><span data-ttu-id="cacfd-266">**Пример скрипта PowerShell**</span><span class="sxs-lookup"><span data-stu-id="cacfd-266">**Example PowerShell Script**</span></span>

<span data-ttu-id="cacfd-p144">Этот скрипт PowerShell позволяет узнать, нужно ли выполнить действия для обновленных данных. Он проверяет номер версии для конечных точек экземпляра Office 365 Worldwide. Если изменение есть, скрипт скачивает конечные точки и фильтрует результаты для категорий &quot;Allow&quot; и &quot;Optimize&quot;. Он также использует уникальный ClientRequestId для нескольких вызовов и сохраняет последнюю версию, обнаруженную во временном файле. Вам нужно вызывать этот скрипт раз в час для проверки наличия обновления версии.</span><span class="sxs-lookup"><span data-stu-id="cacfd-p144">Here is a PowerShell script that you can run to see if there are actions you need to take for updated data. This script checks the version number for the Office 365 Worldwide instance endpoints. When there is a change, it downloads the endpoints and filters for the &quot;Allow&quot; and &quot;Optimize&quot; category endpoints. It also uses a unique ClientRequestId across multiple calls and saves the latest version found in a temporary file. You should call this script once an hour to check for a version update.</span></span>

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

## <a name="example-python-script"></a><span data-ttu-id="cacfd-272">**Пример скрипта на Python**</span><span class="sxs-lookup"><span data-stu-id="cacfd-272">**Example Python Script**</span></span>

<span data-ttu-id="cacfd-p145">Ниже показан скрипт на Python, протестированный с использованием Python 3.6.3 на Windows 10. Он позволяет узнать, нужно ли выполнить действия для обновленных данных, проверяя номер версии для конечных точек экземпляра Office 365 Worldwide. Если изменение есть, скрипт скачивает конечные точки и фильтрует результаты для категорий _Allow_ и _Optimize_. Он также использует уникальный ClientRequestId для нескольких вызовов и сохраняет последнюю версию, обнаруженную во временном файле. Вам нужно вызывать этот скрипт раз в час для проверки наличия обновления версии.</span><span class="sxs-lookup"><span data-stu-id="cacfd-p145">Here is a Python script, tested with Python 3.6.3 on Windows 10, that you can run to see if there are actions you need to take for updated data. This script checks the version number for the Office 365 Worldwide instance endpoints. When there is a change, it downloads the endpoints and filters for the _Allow_ and _Optimize_ category endpoints. It also uses a unique ClientRequestId across multiple calls and saves the latest version found in a temporary file. You should call this script once an hour to check for a version update.</span></span>

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

## <a name="web-service-interface-versioning"></a><span data-ttu-id="cacfd-278">**Управление версиями интерфейса веб-службы**</span><span class="sxs-lookup"><span data-stu-id="cacfd-278">**Web Service interface versioning**</span></span>

<span data-ttu-id="cacfd-p146">В будущем могут понадобиться обновления параметров или результатов для этих методов веб-служб. После публикации общедоступной версии веб-служб корпорация Майкрософт примет разумные меры для заблаговременного уведомления о существенных обновлениях веб-службы. Если корпорация Майкрософт сочтет, что обновление потребует изменений клиентов, использующих веб-службы, она сохранит доступ к предыдущей версии веб-службы в течение как минимум 12 месяцев после выпуска новой версии. Пользователи, которые не выполнят обновление в течение этого времени, могут лишиться доступа к веб-службе и ее методам. Пользователи должны убедиться, что клиенты веб-службы продолжат работать без ошибок, если такие изменения будут внесены в подпись интерфейса веб-службы:</span><span class="sxs-lookup"><span data-stu-id="cacfd-p146">Updates to the parameters or results for these web service methods may be required in the future. After the general availability version of these web services is published, Microsoft will make reasonable efforts to provide advance notice of material updates to the web service. When Microsoft believes that an update will require changes to clients using the web service, Microsoft will keep the previous version (one version back) of the web service available for at least twelve (12) months after the release of the new version. Customers who do not upgrade during that time may be unable to access the web service and its methods. Customers must ensure that clients of the web service continue working without error if the following changes are made to the web service interface signature:</span></span>

- <span data-ttu-id="cacfd-284">Добавление нового необязательного параметра к существующему веб-методу, который необязательно должны предоставлять старые клиенты и который не влияет на результат, получаемый старым клиентом.</span><span class="sxs-lookup"><span data-stu-id="cacfd-284">Adding a new optional parameter to an existing web method that doesn't have to be provided by older clients and doesn't impact the result an older client receives.</span></span>
- <span data-ttu-id="cacfd-285">Добавление нового именованного атрибута в один из элементов REST отклика или дополнительных столбцов в файл CSV отклика.</span><span class="sxs-lookup"><span data-stu-id="cacfd-285">Adding a new named attribute in one of the response REST items or additional columns to the response CSV.</span></span>
- <span data-ttu-id="cacfd-286">Добавление нового веб-метода с новым именем, который не вызывается старыми клиентами.</span><span class="sxs-lookup"><span data-stu-id="cacfd-286">Adding a new web method with a new name that is not called by the older clients.</span></span>

## <a name="related-topics"></a><span data-ttu-id="cacfd-287">Статьи по теме</span><span class="sxs-lookup"><span data-stu-id="cacfd-287">Related Topics</span></span>
  
[<span data-ttu-id="cacfd-288">Диапазоны IP-адресов и URL-адреса Office 365</span><span class="sxs-lookup"><span data-stu-id="cacfd-288">Office 365 URLs and IP address ranges</span></span>](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[<span data-ttu-id="cacfd-289">Вопросы и ответы о конечных точках Office 365</span><span class="sxs-lookup"><span data-stu-id="cacfd-289">Office 365 Germany endpoints</span></span>](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)

[<span data-ttu-id="cacfd-290">Принципы сетевого подключения к Office 365</span><span class="sxs-lookup"><span data-stu-id="cacfd-290">Office 365 Network Connectivity Principles</span></span>](office-365-network-connectivity-principles.md)

[<span data-ttu-id="cacfd-291">Сеть Office 365 и настройка производительности</span><span class="sxs-lookup"><span data-stu-id="cacfd-291">Office 365 network and performance tuning</span></span>](network-planning-and-performance.md)

[<span data-ttu-id="cacfd-292">Сетевое подключение к Office 365</span><span class="sxs-lookup"><span data-stu-id="cacfd-292">Network connectivity to Office 365</span></span>](network-connectivity.md)
  
[<span data-ttu-id="cacfd-293">Azure ExpressRoute для Office 365</span><span class="sxs-lookup"><span data-stu-id="cacfd-293">Azure ExpressRoute for Office 365</span></span>](azure-expressroute.md)
  
[<span data-ttu-id="cacfd-294">Использование ExpressRoute для подключения к Office 365</span><span class="sxs-lookup"><span data-stu-id="cacfd-294">Managing ExpressRoute for Office 365 connectivity</span></span>](managing-expressroute-for-connectivity.md)
  
[<span data-ttu-id="cacfd-295">Маршрутизация с использованием ExpressRoute для Office 365</span><span class="sxs-lookup"><span data-stu-id="cacfd-295">Routing with ExpressRoute for Office 365</span></span>](routing-with-expressroute.md)
  
[<span data-ttu-id="cacfd-296">Реализация ExpressRoute для Office 365</span><span class="sxs-lookup"><span data-stu-id="cacfd-296">Implementing ExpressRoute for Office 365</span></span>](implementing-expressroute.md)
  
[<span data-ttu-id="cacfd-297">Использование сообществ BGP в ExpressRoute для сценариев Office 365 (предварительная версия)</span><span class="sxs-lookup"><span data-stu-id="cacfd-297">Using BGP communities in ExpressRoute for Office 365 scenarios (preview)</span></span>](bgp-communities-in-expressroute.md)
  
[<span data-ttu-id="cacfd-298">Качество мультимедиа и характеристики сетевого подключения в случае Skype для бизнеса Online</span><span class="sxs-lookup"><span data-stu-id="cacfd-298">Media Quality and Network Connectivity Performance in Skype for Business Online</span></span>](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[<span data-ttu-id="cacfd-299">Оптимизация сети для Skype для бизнеса Online</span><span class="sxs-lookup"><span data-stu-id="cacfd-299">Optimizing your network for Skype for Business Online</span></span>](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)
  
[<span data-ttu-id="cacfd-300">ExpressRoute и качество обслуживания в Skype для бизнеса Online</span><span class="sxs-lookup"><span data-stu-id="cacfd-300">ExpressRoute and QoS in Skype for Business Online</span></span>](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[<span data-ttu-id="cacfd-301">Поток вызовов с использованием ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="cacfd-301">Call flow using ExpressRoute</span></span>](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[<span data-ttu-id="cacfd-302">Настройка производительности Office 365 с помощью базовых показателей и журнала производительности</span><span class="sxs-lookup"><span data-stu-id="cacfd-302">Office 365 performance tuning using baselines and performance history</span></span>](performance-tuning-using-baselines-and-history.md)
  
[<span data-ttu-id="cacfd-303">План устранения проблем с производительностью Office 365</span><span class="sxs-lookup"><span data-stu-id="cacfd-303">Performance troubleshooting plan for Office 365</span></span>](performance-troubleshooting-plan.md)
