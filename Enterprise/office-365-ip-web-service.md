---
title: Веб-служба IP-адресов и URL-адресов в Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 5/7/2019
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
ms.openlocfilehash: c87f297c6bc1fc4cf317db60d3fd2ef2e4b8443b
ms.sourcegitcommit: a35d23929bfbfd956ee853b5e828b36e2978bf36
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/07/2019
ms.locfileid: "33655793"
---
# <a name="office-365-ip-address-and-url-web-service"></a><span data-ttu-id="a9763-104">Веб-служба IP-адресов и URL-адресов в Office 365</span><span class="sxs-lookup"><span data-stu-id="a9763-104">Office 365 IP Address and URL Web service</span></span>

<span data-ttu-id="a9763-p102">Чтобы помочь вам выявлять и дифференцировать сетевой трафик Office 365, новая веб-служба публикует конечные точки Office 365, упрощая оценку, настройку и обновление. Эта новая веб-служба заменяет собой скачиваемые XML-файлы, доступные в настоящее время. Прекращение поддержки формата XML планируется на 2 октября 2018 г.</span><span class="sxs-lookup"><span data-stu-id="a9763-p102">To help you better identify and differentiate Office 365 network traffic, a new web service publishes Office 365 endpoints, making it easier for you to evaluate, configure, and stay up to date with changes. This new web service replaces the XML downloadable files that are currently available. The XML format is planned to be phased out on October 2, 2018.</span></span>

<span data-ttu-id="a9763-p103">Будучи клиентом или поставщиком устройств сети периметра, вы можете создавать решения с использованием новой веб-службы на основе REST для записей FQDN и IP-адресов в Office 365. Доступ к данным можно получить непосредственно в браузере с помощью этих URL-адресов.</span><span class="sxs-lookup"><span data-stu-id="a9763-p103">As a customer or a network perimeter device vendor, you can build against the new REST-based web service for the Office 365 IP address and FQDN entries. You can access the data directly in a web browser using these URLs.</span></span>

- <span data-ttu-id="a9763-110">Для получения последней версии диапазонов IP-адресов и URL-адресов Office 365 перейдите на веб-страницу [https://endpoints.office.com/version](https://endpoints.office.com/version?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span><span class="sxs-lookup"><span data-stu-id="a9763-110">For the latest version of the Office 365 URLs and IP address ranges, use [https://endpoints.office.com/version](https://endpoints.office.com/version?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span></span>
- <span data-ttu-id="a9763-111">Для получения данных на странице диапазонов IP-адресов и URL-адресов Office 365 для брандмауэров и прокси-серверов перейдите на веб-страницу [https://endpoints.office.com/endpoints/worldwide](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span><span class="sxs-lookup"><span data-stu-id="a9763-111">For the data on the Office 365 URLs and IP address ranges page for firewalls and proxy servers, use [https://endpoints.office.com/endpoints/worldwide](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span></span>
- <span data-ttu-id="a9763-112">Для получения всех последних изменений с конца июля 2018 года (тогда стала доступной веб-служба) перейдите на веб-страницу [https://endpoints.office.com/changes/worldwide/0000000000](https://endpoints.office.com/changes/worldwide/0000000000?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span><span class="sxs-lookup"><span data-stu-id="a9763-112">To get all the latest changes since the end of July 2018 when the web service was first available, use [https://endpoints.office.com/changes/worldwide/0000000000](https://endpoints.office.com/changes/worldwide/0000000000?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span></span>

<span data-ttu-id="a9763-113">Как клиент вы можете использовать эту веб-службу, чтобы:</span><span class="sxs-lookup"><span data-stu-id="a9763-113">As a customer, you can use this web service to:</span></span>

- <span data-ttu-id="a9763-114">обновлять скрипты PowerShell для получения данных конечной точки Office 365 и изменять форматирование для сетевых устройств;</span><span class="sxs-lookup"><span data-stu-id="a9763-114">Update your PowerShell scripts to obtain Office 365 endpoint data and modify any formatting for your networking devices.</span></span>
- <span data-ttu-id="a9763-115">применять эту информацию для обновления PAC-файлов, развернутых на клиентских компьютерах.</span><span class="sxs-lookup"><span data-stu-id="a9763-115">Use this information to update PAC files deployed to client computers.</span></span>

<span data-ttu-id="a9763-116">Как поставщик устройств сети периметра вы можете использовать эту веб-службу, чтобы:</span><span class="sxs-lookup"><span data-stu-id="a9763-116">As a network perimeter device vendor, you can use this web service to:</span></span>

- <span data-ttu-id="a9763-117">создавать и тестировать программное обеспечение устройств для скачивания списка с целью автоматической настройки;</span><span class="sxs-lookup"><span data-stu-id="a9763-117">Create and test device software to download the list for automated configuration.</span></span>
- <span data-ttu-id="a9763-118">проверять текущую версию;</span><span class="sxs-lookup"><span data-stu-id="a9763-118">Check for the current version.</span></span>
- <span data-ttu-id="a9763-119">получать текущие изменения.</span><span class="sxs-lookup"><span data-stu-id="a9763-119">Get the current changes.</span></span>

> [!NOTE]
> <span data-ttu-id="a9763-120">Если вы используете Azure ExpressRoute для подключения к Office 365, см. статью [Azure ExpressRoute для Office 365](https://docs.microsoft.com/office365/enterprise/azure-expressroute), чтобы ознакомиться со службами Office 365, поддерживаемыми в Azure ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="a9763-120">If you are using Azure ExpressRoute to connect to Office 365, please review [Azure ExpressRoute for Office 365](https://docs.microsoft.com/office365/enterprise/azure-expressroute) to familiarize yourself with the Office 365 services supported over Azure ExpressRoute.</span></span> <span data-ttu-id="a9763-121">Чтобы понимать, какие сетевые запросы для приложений Office 365 требуют подключения в Интернету, см. статью [URL-адреса и диапазоны IP-адресов Office 365](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges?redirectSourcePath=%252farticle%252fOffice-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2).</span><span class="sxs-lookup"><span data-stu-id="a9763-121">Also review the article [Office 365 URLs and IP address ranges](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges?redirectSourcePath=%252farticle%252fOffice-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) to understand which network requests for Office 365 applications require Internet connectivity.</span></span> <span data-ttu-id="a9763-122">Это поможет вам лучше настроить устройства периметра безопасности.</span><span class="sxs-lookup"><span data-stu-id="a9763-122">This will help to better configure your perimeter security devices.</span></span>

<span data-ttu-id="a9763-123">Дополнительные сведения:</span><span class="sxs-lookup"><span data-stu-id="a9763-123">For additional information, see:</span></span>

- [<span data-ttu-id="a9763-124">Объявление в записи блога на форуме Tech Community Office 365.</span><span class="sxs-lookup"><span data-stu-id="a9763-124">Announcement blog post in the Office 365 Tech Community Forum</span></span>](https://techcommunity.microsoft.com/t5/Office-365-Blog/Announcing-Office-365-endpoint-categories-and-Office-365-IP/ba-p/177638)
- [<span data-ttu-id="a9763-125">Форум Tech Community Office 365, содержащий сведения об использовании веб-служб.</span><span class="sxs-lookup"><span data-stu-id="a9763-125">Office 365 Tech Community Forum for questions about use of the web services</span></span>](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)

## <a name="common-parameters"></a><span data-ttu-id="a9763-126">Общие параметры</span><span class="sxs-lookup"><span data-stu-id="a9763-126">Common parameters</span></span>

<span data-ttu-id="a9763-127">Эти параметры являются общими для всех методов веб-службы:</span><span class="sxs-lookup"><span data-stu-id="a9763-127">These parameters are common across all the web service methods:</span></span>

- <span data-ttu-id="a9763-128">**format=<JSON | CSV>**. По умолчанию данные возвращаются в формате JSON.</span><span class="sxs-lookup"><span data-stu-id="a9763-128">**format=<JSON | CSV>** - By default, the returned data format is JSON.</span></span> <span data-ttu-id="a9763-129">Используйте этот необязательный параметр для возврата данных в формате значений с разделителями-запятыми (CSV).</span><span class="sxs-lookup"><span data-stu-id="a9763-129">Use this optional parameter to return the data in comma-separated values (CSV) format.</span></span>
- <span data-ttu-id="a9763-130">**ClientRequestId=\<guid>**. Обязательный GUID, создаваемый для связывания клиента.</span><span class="sxs-lookup"><span data-stu-id="a9763-130">**ClientRequestId=\<guid>** - A required GUID that you generate for client association.</span></span> <span data-ttu-id="a9763-131">Нужно создавать GUID для каждого компьютера, вызывающего веб-службу.</span><span class="sxs-lookup"><span data-stu-id="a9763-131">You should generate a GUID for each machine that calls the web service.</span></span> <span data-ttu-id="a9763-132">Не используйте GUID, показанные в примерах ниже, так как они могут быть заблокированы веб-службой в будущем.</span><span class="sxs-lookup"><span data-stu-id="a9763-132">Do not use the GUIDs shown in the following examples because they may be blocked by the web service in the future.</span></span> <span data-ttu-id="a9763-133">Формат GUID следующий: _xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx_. Здесь "x" означает шестнадцатеричное число.</span><span class="sxs-lookup"><span data-stu-id="a9763-133">GUID format is _xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx_, where x represents a hexadecimal number.</span></span> <span data-ttu-id="a9763-134">Для создания GUID используйте команду [New-Guid](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-guid?view=powershell-6) PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a9763-134">To generate a GUID, use the [New-Guid](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-guid?view=powershell-6) PowerShell command.</span></span>

## <a name="version-web-method"></a><span data-ttu-id="a9763-135">Веб-метод версии</span><span class="sxs-lookup"><span data-stu-id="a9763-135">Version web method</span></span>

<span data-ttu-id="a9763-p107">Майкрософт обновляет записи IP-адресов и FQDN Office 365 в конце каждого месяца и иногда вне цикла для выполнения операционных требований или требований поддержки. Данным для каждого опубликованного экземпляра назначается номер версии. Веб-метод версии позволяет проводить опрос для получения последней версии каждого экземпляра службы Office 365. Рекомендуем проверять версию ежедневно (максимум ежечасно). Появление новых версий ожидается в начале каждого месяца. Иногда ввиду инцидентов поддержки, безопасности или других операционных требований новые версии будут появляться в течение месяца.</span><span class="sxs-lookup"><span data-stu-id="a9763-p107">Microsoft updates the Office 365 IP address and FQDN entries at the end of each month and occasionally out of cycle for operational or support requirements. The data for each published instance is assigned a version number. The version web method lets you poll for the latest version for each Office 365 service instance. We recommend you check the version daily, or at the most, hourly. New versions should be expected at the start of each month. Sometimes due to support incident, security, or other operational requirements there will be new versions during the month.</span></span>

<span data-ttu-id="a9763-142">Параметры для веб-метода версии:</span><span class="sxs-lookup"><span data-stu-id="a9763-142">Parameters for the version web method are:</span></span>

- <span data-ttu-id="a9763-143">**AllVersions=<true | false>**. По умолчанию возвращается последний номер версии.</span><span class="sxs-lookup"><span data-stu-id="a9763-143">**AllVersions=<true | false>** - By default, the version returned is the latest.</span></span> <span data-ttu-id="a9763-144">Включите этот необязательный параметр для запроса всех версий, опубликованных с момента первого выпуска веб-службы.</span><span class="sxs-lookup"><span data-stu-id="a9763-144">Include this optional parameter to request all published versions since the web service was first released.</span></span>
- <span data-ttu-id="a9763-145">**Format=<JSON | CSV | RSS>**. Кроме форматов JSON и CSV, веб-метод версии поддерживает RSS.</span><span class="sxs-lookup"><span data-stu-id="a9763-145">**Format=<JSON | CSV | RSS>** – In addition to the JSON and CSV formats, the version web method also supports RSS.</span></span> <span data-ttu-id="a9763-146">Вы можете использовать его вместе с необязательным параметром _AllVersions=true_ для запрашивания RSS-канала, который можно применять в Outlook или других средствах чтения RSS.</span><span class="sxs-lookup"><span data-stu-id="a9763-146">You can use this optional parameter along with the _AllVersions=true_ parameter to request an RSS feed which can be used with Outlook or other RSS readers.</span></span>
- <span data-ttu-id="a9763-147">**Instance=<Worldwide | China | Germany | USGovDoD | USGovGCCHigh>**. Этот необязательный параметр указывает экземпляр, для которого возвращается версия.</span><span class="sxs-lookup"><span data-stu-id="a9763-147">**Instance=<Worldwide | China | Germany | USGovDoD | USGovGCCHigh>** - This optional parameter specifies the instance to return the version for.</span></span> <span data-ttu-id="a9763-148">Если его опустить, будут возвращены все экземпляры.</span><span class="sxs-lookup"><span data-stu-id="a9763-148">If omitted, all instances are returned.</span></span> <span data-ttu-id="a9763-149">Допустимые экземпляры: Worldwide, China, Germany, USGovDoD, USGovGCCHigh.</span><span class="sxs-lookup"><span data-stu-id="a9763-149">Valid instances are: Worldwide, China, Germany, USGovDoD, USGovGCCHigh.</span></span>

<span data-ttu-id="a9763-p111">Веб-метод версии не имеет ограничения по частоте и не возвращает HTTP-код отклика 429. Отклик для веб-метода версии включает заголовок с контролем кэша, рекомендующий кэширование данных в течение 1 часа. Результатом веб-метода версии может быть отдельная запись или массив записей. Ниже перечислены элементы каждой записи:</span><span class="sxs-lookup"><span data-stu-id="a9763-p111">The version web method is not rate limited and does not ever return 429 HTTP Response Codes. The response to the version web method does include a cache-control header recommending caching of the data for 1 hour. The result from the version web method may be a single record or an array of records. The elements of each record are:</span></span>

- <span data-ttu-id="a9763-154">instance — короткое имя экземпляра службы Office 365.</span><span class="sxs-lookup"><span data-stu-id="a9763-154">instance - The short name of the Office 365 service instance.</span></span>
- <span data-ttu-id="a9763-155">latest — последняя версия для конечных точек указанного экземпляра.</span><span class="sxs-lookup"><span data-stu-id="a9763-155">latest - The latest version for endpoints of the specified instance.</span></span>
- <span data-ttu-id="a9763-p112">versions — список всех предыдущих версий для указанного экземпляра. Этот элемент включен, только если параметр AllVersions имеет значение true.</span><span class="sxs-lookup"><span data-stu-id="a9763-p112">versions - A list of all previous versions for the specified instance. This element is only included if the AllVersions parameter is true.</span></span>

<span data-ttu-id="a9763-p113">Вы можете использовать Microsoft Flow для получения уведомлений об изменениях IP-адресов и URL-адресов по электронной почте. См. статью [Использование Microsoft Flow для получения электронных сообщений об изменениях URL-адресов и IP-адресов Office 365](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/m-p/240651).</span><span class="sxs-lookup"><span data-stu-id="a9763-p113">You can use Microsoft Flow to get email notifications of changes to the IP Addresses and URLs. See [Use Microsoft Flow to receive an email for changes to Office 365 IP Addresses and URLs](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/m-p/240651).</span></span>

### <a name="examples"></a><span data-ttu-id="a9763-160">Примеры:</span><span class="sxs-lookup"><span data-stu-id="a9763-160">Examples:</span></span>

<span data-ttu-id="a9763-161">Пример 1. Запрос URI: [https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="a9763-161">Example 1 request URI: [https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="a9763-p114">Этот URI возвращает последнюю версию каждого экземпляра службы Office 365. Пример результата:</span><span class="sxs-lookup"><span data-stu-id="a9763-p114">This URI returns the latest version of each Office 365 service instance. Example result:</span></span>

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
> <span data-ttu-id="a9763-p115">GUID для параметра ClientRequestID в этих URI приведен только в качестве примера. Чтобы попробовать применить URI веб-службы, создайте собственный GUID. GUID, показанные в этих примерах, могут быть заблокированы веб-службой в будущем.</span><span class="sxs-lookup"><span data-stu-id="a9763-p115">The GUID for the ClientRequestID parameter in these URIs are only an example. To try the web service URIs out, generate your own GUID. The GUIDs shown in these examples may be blocked by the web service in the future.</span></span>

<span data-ttu-id="a9763-167">Пример 2. Запрос URI: [https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="a9763-167">Example 2 request URI: [https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="a9763-p116">Этот URI возвращает последнюю версию указанного экземпляра службы Office 365. Пример результата:</span><span class="sxs-lookup"><span data-stu-id="a9763-p116">This URI returns the latest version of the specified Office 365 service instance. Example result:</span></span>

```json
{
 "instance": "Worldwide",
 "latest": "2018063000"
}
```

<span data-ttu-id="a9763-170">Пример 3. Запрос URI: [https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="a9763-170">Example 3 request URI: [https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="a9763-p117">Этот URI показывает выходные данные в формате CSV. Пример результата:</span><span class="sxs-lookup"><span data-stu-id="a9763-p117">This URI shows output in CSV format. Example result:</span></span>

```csv
instance,latest
Worldwide,2018063000
```

<span data-ttu-id="a9763-173">Пример 4. Запрос URI: [https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="a9763-173">Example 4 request URI: [https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="a9763-p118">Этот URI показывает все более ранние версии, которые были опубликованы для экземпляра службы Office 365 Worldwide. Пример результата:</span><span class="sxs-lookup"><span data-stu-id="a9763-p118">This URI shows all prior versions that have been published for the Office 365 worldwide service instance. Example result:</span></span>

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

<span data-ttu-id="a9763-176">Пример 5. URI RSS-канала: [https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS](https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS)</span><span class="sxs-lookup"><span data-stu-id="a9763-176">Example 5 RSS Feed URI: [https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS](https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS)</span></span>

<span data-ttu-id="a9763-p119">Этот URI показывает RSS-канал опубликованных версий, которые содержат ссылки на список изменений для каждой версии. Пример результата:</span><span class="sxs-lookup"><span data-stu-id="a9763-p119">This URI shows an RSS feed of the published versions that include links to the list of changes for each version. Example result:</span></span>

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
```

## <a name="endpoints-web-method"></a><span data-ttu-id="a9763-179">Веб-метод конечных точек</span><span class="sxs-lookup"><span data-stu-id="a9763-179">Endpoints web method</span></span>

<span data-ttu-id="a9763-180">Веб-метод конечных точек возвращает все записи для диапазонов IP-адресов и URL-адресов, входящих в службу Office 365.</span><span class="sxs-lookup"><span data-stu-id="a9763-180">The endpoints web method returns all records for IP address ranges and URLs that make up the Office 365 service.</span></span> <span data-ttu-id="a9763-181">Хотя для настройки сетевого устройства нужно использовать новейшие данные от веб-метода конечных точек, данные можно кэшировать на 30 дней после их публикации ввиду заблаговременного уведомления в отношении дополнений.</span><span class="sxs-lookup"><span data-stu-id="a9763-181">While the latest data from the endpoints web method should be used for network device configuration, the data can be cached for up to 30 days after it is published due to the advance notice provided for additions.</span></span> <span data-ttu-id="a9763-182">Рекомендуется вызывать веб-метод конечных точек еще раз, только когда веб-метод версии указывает на доступность новой версии данных.</span><span class="sxs-lookup"><span data-stu-id="a9763-182">We recommend you only call the endpoints web method again when the version web method indicates a new version of the data is available.</span></span>

<span data-ttu-id="a9763-183">Параметры веб-метода конечных точек представлены ниже.</span><span class="sxs-lookup"><span data-stu-id="a9763-183">Parameters for the endpoints web method are:</span></span>

- <span data-ttu-id="a9763-184">**ServiceAreas=<Common | Exchange | SharePoint | Skype>**. Список областей обслуживания, разделенных запятыми.</span><span class="sxs-lookup"><span data-stu-id="a9763-184">**ServiceAreas=<Common | Exchange | SharePoint | Skype>** - A comma-separated list of service areas.</span></span> <span data-ttu-id="a9763-185">Допустимые элементы: _Common_, _Exchange_, _SharePoint_ и _Skype_.</span><span class="sxs-lookup"><span data-stu-id="a9763-185">Valid items are _Common_, _Exchange_, _SharePoint_, and _Skype_.</span></span> <span data-ttu-id="a9763-186">Так как элементы области обслуживания Common обязательны для всех других областей обслуживания, веб-служба всегда будет их включать.</span><span class="sxs-lookup"><span data-stu-id="a9763-186">Because Common service area items are a prerequisite for all other service areas, the web service will always include them.</span></span> <span data-ttu-id="a9763-187">Если не включить этот параметр, будут возвращены все области обслуживания.</span><span class="sxs-lookup"><span data-stu-id="a9763-187">If you do not include this parameter, all service areas are returned.</span></span>
- <span data-ttu-id="a9763-188">**TenantName=<имя_клиента>**. Имя клиента Office 365.</span><span class="sxs-lookup"><span data-stu-id="a9763-188">**TenantName=<tenant_name>** - Your Office 365 tenant name.</span></span> <span data-ttu-id="a9763-189">Веб-служба получает предоставленное вами имя и вставляет его в части URL-адресов, которые включают имя клиента.</span><span class="sxs-lookup"><span data-stu-id="a9763-189">The web service takes your provided name and inserts it in parts of URLs that include the tenant name.</span></span> <span data-ttu-id="a9763-190">Если вы не предоставляете имя клиента, эти части URL-адресов будут содержать подстановочный знак (\*).</span><span class="sxs-lookup"><span data-stu-id="a9763-190">If you don't provide a tenant name, those parts of URLs have the wildcard character (\*).</span></span>
- <span data-ttu-id="a9763-191">**NoIPv6=<true | false>**. Установите для него значение true, чтобы исключить адреса IPv6 из выходных данных (например, если в вашей сети не используется IPv6).</span><span class="sxs-lookup"><span data-stu-id="a9763-191">**NoIPv6=<true | false>** - Set this to true to exclude IPv6 addresses from the output, for example, if you don't use IPv6 in your network.</span></span>
- <span data-ttu-id="a9763-192">**Instance=<Worldwide | China | Germany | USGovDoD | USGovGCCHigh>**. Этот обязательный параметр указывает экземпляр, для которого должны быть возвращены конечные точки.</span><span class="sxs-lookup"><span data-stu-id="a9763-192">**Instance=<Worldwide | China | Germany | USGovDoD | USGovGCCHigh>** - This required parameter specifies the instance to return the endpoints for.</span></span> <span data-ttu-id="a9763-193">Допустимые экземпляры: _Worldwide_, _China_, _Germany_, _USGovDoD_ и _USGovGCCHigh_.</span><span class="sxs-lookup"><span data-stu-id="a9763-193">Valid instances are: Worldwide, China, Germany, USGovDoD, USGovGCCHigh.</span></span>

<span data-ttu-id="a9763-194">Если вы вызываете веб-метод конечных точек много раз с одного клиентского IP-адреса, вы можете получить код HTTP-отклика 429 (слишком большое количество запросов).</span><span class="sxs-lookup"><span data-stu-id="a9763-194">If you call the endpoints web method a large number of times from the same client IP address, you may receive HTTP response code 429 (Too Many Requests).</span></span> <span data-ttu-id="a9763-195">Большинство пользователей никогда не увидит данный код.</span><span class="sxs-lookup"><span data-stu-id="a9763-195">Most people will never see this.</span></span> <span data-ttu-id="a9763-196">Если вы получили этот код отклика, подождите 1 час перед повтором своего запроса.</span><span class="sxs-lookup"><span data-stu-id="a9763-196">If you get this response code, wait 1 hour before repeating your request.</span></span> <span data-ttu-id="a9763-197">Запланируйте вызов веб-метода конечных точек только в том случае, если веб-метод версии указывает, что доступна новая версия.</span><span class="sxs-lookup"><span data-stu-id="a9763-197">Plan to only call the endpoints web method when the version web method indicates there is a new version available.</span></span>

<span data-ttu-id="a9763-p125">Результат веб-метода конечных точек — массив, в который входят все записи, представляющие набор конечных точек. Элементы каждой записи:</span><span class="sxs-lookup"><span data-stu-id="a9763-p125">The result from the endpoints web method is an array of records with each record representing an endpoint set. The elements for each record are:</span></span>

- <span data-ttu-id="a9763-200">id — неизменяемый идентификатор набора конечных точек.</span><span class="sxs-lookup"><span data-stu-id="a9763-200">id - The immutable id number of the endpoint set.</span></span>
- <span data-ttu-id="a9763-201">serviceArea — область обслуживания, которая является частью Common, Exchange, SharePoint или Skype.</span><span class="sxs-lookup"><span data-stu-id="a9763-201">serviceArea - The service area that this is part of: Common, Exchange, SharePoint, or Skype.</span></span>
- <span data-ttu-id="a9763-p126">urls — URL-адреса для набора конечных точек. Массив JSON записей DNS. Если значение не указано, опускается.</span><span class="sxs-lookup"><span data-stu-id="a9763-p126">urls - URLs for the endpoint set. A JSON array of DNS records. Omitted if blank.</span></span>
- <span data-ttu-id="a9763-p127">tcpPorts — TCP-порты для набора конечных точек. Все элементы портов отформатированы в виде списка портов с разделителями-запятыми или диапазонов портов, разделенных символами дефиса (-). Порты применяются ко всем IP-адресам и всем URL-адресам в этом наборе конечных точек для этой категории. Если значение не указано, опускается.</span><span class="sxs-lookup"><span data-stu-id="a9763-p127">tcpPorts - TCP ports for the endpoint set. All ports elements are formatted as a comma-separated list of ports or port ranges separated by a dash character (-). Ports apply to all IP addresses and all URLs in that endpoint set for that category. Omitted if blank.</span></span>
- <span data-ttu-id="a9763-p128">udpPorts — порты UDP для диапазонов IP-адресов в этом наборе конечных точек. Если значение не указано, опускается.</span><span class="sxs-lookup"><span data-stu-id="a9763-p128">udpPorts - UDP ports for the IP address ranges in this endpoint set. Omitted if blank.</span></span>
- <span data-ttu-id="a9763-p129">ips — диапазоны IP-адресов, связанные с этим набором конечных точек (с перечисленными портами TCP или UDP). Массив JSON диапазонов IP-адресов. Если значение не указано, опускается.</span><span class="sxs-lookup"><span data-stu-id="a9763-p129">ips - The IP address ranges associated with this endpoint set as associated with the listed TCP or UDP ports. A JSON array of IP Address ranges. Omitted if blank.</span></span>
- <span data-ttu-id="a9763-p130">category — категория возможности подключения к набору конечных точек. Допустимые значения: Optimize, Allow и Default. При использовании данных конечной точки для поиска категории IP- или URL-адреса запрос может возвращать несколько категорий. Это может происходить по нескольким причинам. В таких случаях необходимо следовать рекомендациям для категории с наивысшим приоритетом. Например, если для конечной точки выводятся значения Optimize и Allow, следует выполнять требования для значения Optimize. Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="a9763-p130">category - The connectivity category for the endpoint set. Valid values are Optimize, Allow, and Default. If using the endpoint data to search for the category of an IP Address or URL, it is possible that your query may return multiple categories. There are a few reasons why that may happen. In these cases you should follow the recommendations for the highest priority category. For example, if the endpoint appears in both Optimize and Allow, you should follow the requirements for Optimize. Required.</span></span>
- <span data-ttu-id="a9763-221">expressRoute имеет значение True или False, если для этого набора конечных точек выполняется маршрутизация через ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="a9763-221">expressRoute - True or False if this endpoint set is routed over ExpressRoute.</span></span>
- <span data-ttu-id="a9763-p131">required имеет значение True, если этот набор конечных точек требуется для подключения к Office 365. False, если этот набор конечных точек необязателен.</span><span class="sxs-lookup"><span data-stu-id="a9763-p131">required - True if this endpoint set is required to have connectivity for Office 365 to be supported. False if this endpoint set is optional.</span></span>
- <span data-ttu-id="a9763-p132">notes — текст, который в случае необязательных конечных точек описывает функциональность Office 365, которая будет отсутствовать, если IP-адреса или URL-адреса в этом наборе конечных точек не могут быть доступны на сетевом уровне. Если значение не указано, опускается.</span><span class="sxs-lookup"><span data-stu-id="a9763-p132">notes - For optional endpoints, this text describes Office 365 functionality that will be missing if IP addresses or URLs in this endpoint set cannot be accessed at the network layer. Omitted if blank.</span></span>

### <a name="examples"></a><span data-ttu-id="a9763-226">Примеры</span><span class="sxs-lookup"><span data-stu-id="a9763-226">Examples:</span></span>

<span data-ttu-id="a9763-227">Пример 1. Запрос URI: [https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="a9763-227">Example 1 request URI: [https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="a9763-p133">Этот URI получает все конечные точки для экземпляра Office 365 Worldwide для всех рабочих нагрузок. В примере результата показан фрагмент выходных данных:</span><span class="sxs-lookup"><span data-stu-id="a9763-p133">This URI obtains all endpoints for the Office 365 worldwide instance for all workloads. Example result showing an excerpt of the output:</span></span>

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
```

<span data-ttu-id="a9763-230">Дополнительные наборы конечных точек не включены в этот пример.</span><span class="sxs-lookup"><span data-stu-id="a9763-230">Additional endpoint sets are not included in this example.</span></span>

<span data-ttu-id="a9763-231">Пример 2. Запрос URI: [https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="a9763-231">Example 2 request URI: [https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="a9763-232">В этом примере получены конечные точки для экземпляра Office 365 Worldwide в отношении Exchange Online и зависимостей.</span><span class="sxs-lookup"><span data-stu-id="a9763-232">This example obtains endpoints for the Office 365 Worldwide instance for Exchange Online and dependencies only.</span></span>

<span data-ttu-id="a9763-233">Выходные данные в примере 2 аналогичны таковым в примере 1, но результаты не включают конечные точки для SharePoint Online или Skype для бизнеса Online.</span><span class="sxs-lookup"><span data-stu-id="a9763-233">The output for example 2 is similar to example 1 except that the results will not include endpoints for SharePoint Online or Skype for Business Online.</span></span>

## <a name="changes-web-method"></a><span data-ttu-id="a9763-234">Веб-метод изменений</span><span class="sxs-lookup"><span data-stu-id="a9763-234">Changes web method</span></span>

<span data-ttu-id="a9763-p134">Веб-метод изменений возвращает самые последние опубликованные обновления. Как правило, это изменения диапазонов IP-адресов и URL-адресов за предыдущий месяц. Наиболее критические изменения для обработки возникают, когда добавляются новые URL-адреса или IP-адреса, так как неудачная попытка добавить IP-адрес в список управления доступом брандмауэра или добавить URL-адрес в список обхода прокси-сервера может привести к простою пользователей Office 365 за этим сетевым устройством. Несмотря на операционные требования, операции _Add_ добавляются с 30-дневным уведомлением до того, как может возникнуть такой простой.</span><span class="sxs-lookup"><span data-stu-id="a9763-p134">The changes web method returns the most recent updates that have been published. This is typically the previous month's changes to IP address ranges and URLs. The most critical changes to be processed are when new URLs or IP Addresses are added since failing to add an IP Address to a firewall access control list, or a URL to a proxy server bypass list can cause an outage for Office 365 users behind that network device. Notwithstanding operational requirements, _Add_ operations are added with 30 days' notice before such an outage would occur.</span></span>

<span data-ttu-id="a9763-239">Обязательный параметр веб-метода изменений:</span><span class="sxs-lookup"><span data-stu-id="a9763-239">The required parameter for the changes web method is:</span></span>

- <span data-ttu-id="a9763-240">**Version=\<ГГГГММДДЧЧ>** — обязательный параметр маршрутизации URL-адресов.</span><span class="sxs-lookup"><span data-stu-id="a9763-240">**Version=\<YYYYMMDDNN>** - Required URL route parameter.</span></span> <span data-ttu-id="a9763-241">Этим значением должна быть используемая в настоящий момент версия.</span><span class="sxs-lookup"><span data-stu-id="a9763-241">This value should be the version that you have currently implemented.</span></span> <span data-ttu-id="a9763-242">Веб-служба возвращает изменения, внесенные с момента этой версии.</span><span class="sxs-lookup"><span data-stu-id="a9763-242">The web service will return the changes since that version.</span></span> <span data-ttu-id="a9763-243">Формат: _ГГГГММДДЧЧ_, где _ЧЧ_ — натуральное число, увеличивающееся, если в один день нужно опубликовать больше одной версии, при этом значение _00_ представляет первое обновление дня.</span><span class="sxs-lookup"><span data-stu-id="a9763-243">The format is _YYYYMMDDNN_, where _NN_ is a natural number incremented if there are multiple versions required to be published on a single day, with _00_ representing the first update for a given day.</span></span> <span data-ttu-id="a9763-244">Веб-служба требует, чтобы параметр _version_ содержал ровно 10 цифр.</span><span class="sxs-lookup"><span data-stu-id="a9763-244">The web service requires this parameter to contain exactly 10 digits.</span></span>

<span data-ttu-id="a9763-245">Веб-метод изменений ограничен по частоте аналогично веб-методу конечных точек.</span><span class="sxs-lookup"><span data-stu-id="a9763-245">The changes web method is rate limited in the same way as the endpoints web method.</span></span> <span data-ttu-id="a9763-246">Если вы получили код отклика HTTP 429, подождите 1 час перед повтором своего запроса.</span><span class="sxs-lookup"><span data-stu-id="a9763-246">If you receive a 429 HTTP response code, wait 1 hour before repeating your request.</span></span>

<span data-ttu-id="a9763-p137">Результат веб-метода изменений — массив записей, каждая из которых представляет изменение в конкретной версии конечной точки. Элементы каждой записи:</span><span class="sxs-lookup"><span data-stu-id="a9763-p137">The result from the changes web method is an array of records with each record representing a change in a specific version of the endpoints. The elements for each record are:</span></span>

- <span data-ttu-id="a9763-249">id — неизменяемый идентификатор записи изменения.</span><span class="sxs-lookup"><span data-stu-id="a9763-249">id - The immutable id of the change record.</span></span>
- <span data-ttu-id="a9763-250">endpointSetId — идентификатор записи набора конечных точек, который был изменен.</span><span class="sxs-lookup"><span data-stu-id="a9763-250">endpointSetId - The ID of the endpoint set record that is changed.</span></span>
- <span data-ttu-id="a9763-251">disposition — это может быть изменение, добавление или удаление, а также описание того, как именно была изменена запись набора конечных точек.</span><span class="sxs-lookup"><span data-stu-id="a9763-251">disposition - This can be either of change, add, or remove and describes what the change did to the endpoint set record.</span></span>
- <span data-ttu-id="a9763-p138">impact — не все изменения будут одинаково важны для каждой среды. Данный элемент описывает ожидаемое влияние на среду периметра корпоративной сети в результате этого изменения. Этот атрибут включается только в записи изменений версии **2018112800** и более поздних версий. Доступны следующие варианты для атрибута impact:</span><span class="sxs-lookup"><span data-stu-id="a9763-p138">impact - Not all changes will be equally important to every environment. This describes the expected impact to an enterprise network perimeter environment as a result of this change. This attribute is included only in change records of version 2018112800 and later. Options for the impact are:</span></span>
  - <span data-ttu-id="a9763-p139">AddedIp — IP-адрес, который был добавлен в Office 365 и будет доступен в режиме реального времени в ближайшее время. Этот элемент представляет изменения, которые вам необходимо внести для брандмауэра или другого устройства периметра 3 уровня сети. Если вы не добавили данный элемент ранее, прежде чем мы стали использовать его, могут возникать сбои.</span><span class="sxs-lookup"><span data-stu-id="a9763-p139">AddedIp – An IP Address was added to Office 365 and will be live on the service soon. This represents a change you need to take on a firewall or other layer 3 network perimeter device. If you don’t add this before we start using it, you may experience an outage.</span></span>
  - <span data-ttu-id="a9763-259">AddedUrl — URL-адрес был добавлен в Office 365 и будет доступен в службе в ближайшее время.</span><span class="sxs-lookup"><span data-stu-id="a9763-259">AddedUrl – A URL was added to Office 365 and will be live on the service soon.</span></span> <span data-ttu-id="a9763-260">Этот элемент представляет изменения, которые вам необходимо внести для прокси-сервера или устройства сетевого периметра, анализирующего URL-адреса.</span><span class="sxs-lookup"><span data-stu-id="a9763-260">This represents a change you need to take on a proxy server or URL parsing network perimeter device.</span></span> <span data-ttu-id="a9763-261">Если вы не добавили этот элемент перед началом его использования, могут возникать сбои.</span><span class="sxs-lookup"><span data-stu-id="a9763-261">If you don’t add this before we start using it, you may experience an outage.</span></span>
  - <span data-ttu-id="a9763-p141">AddedIpAndUrl - Были добавлены IP-адрес и URL-адрес. Этот элемент представляет изменение, которое вам необходимо внести на устройстве 3 уровня брандмауэра, прокси-сервере или устройстве анализа URL-адреса. Если вы не добавили данный элемент до того, как мы начали использовать его, могут возникать сбои.</span><span class="sxs-lookup"><span data-stu-id="a9763-p141">AddedIpAndUrl - Both an IP Address and a URL were added. This represents a change you need to take on either a firewall layer 3 device or a proxy server or URL parsing device. If you don’t add this before we start using it, you may experience an outage.</span></span>
  - <span data-ttu-id="a9763-p142">RemovedIpOrUrl — Минимум один IP-адрес или URL-адрес был удален из Office 365. Вы должны удалить конечные точки сети со своих устройств периметра, но четкого срока, когда вы должны это сделать, не установлено.</span><span class="sxs-lookup"><span data-stu-id="a9763-p142">RemovedIpOrUrl – At least one IP Address or URL was removed from Office 365. You should remove the network endpoints from your perimeter devices, but there’s no deadline for you to do this.</span></span>
  - <span data-ttu-id="a9763-p143">ChangedIsExpressRoute — Атрибут поддержки ExpressRoute был изменен. Если вы используете ExpressRoute, может потребоваться выполнение определенных действий в зависимости от вашей конфигурации.</span><span class="sxs-lookup"><span data-stu-id="a9763-p143">ChangedIsExpressRoute – The ExpressRoute support attribute was changed. If you use ExpressRoute then you may need to take action depending on your configuration.</span></span>
  - <span data-ttu-id="a9763-p144">MovedIpOrUrl — Мы перенесли IP-адрес или URL-адрес между данным набором конечной точки и другим набором. Как правило, никаких дополнительных действий не требуется.</span><span class="sxs-lookup"><span data-stu-id="a9763-p144">MovedIpOrUrl – We moved an IP Address or Url between this endpoint set and another one. Generally no action is required.</span></span>
  - <span data-ttu-id="a9763-p145">RemovedDuplicateIpOrUrl — Мы удалили повторяющийся IP-адрес или URL-адрес, но он по-прежнему опубликован для Office 365. Обычно никаких действий не требуется.</span><span class="sxs-lookup"><span data-stu-id="a9763-p145">RemovedDuplicateIpOrUrl – We removed a duplicate IP Address or Url but it’s still published for Office 365. Generally no action is required.</span></span>
  - <span data-ttu-id="a9763-273">OtherNonPriorityChanges — Мы изменили что-то менее критическое, чем другие прочие параметры, например поле заметки.</span><span class="sxs-lookup"><span data-stu-id="a9763-273">OtherNonPriorityChanges – We changed something less critical than all of the other options like a note field</span></span>
- <span data-ttu-id="a9763-p146">version — версия опубликованного набора конечных точек, в который внесено изменение. Формат номеров версий: _ГГГГММДДЧЧ_, где "ЧЧ" — натуральное число, увеличивающееся, если в один день нужно опубликовать больше одной версии.</span><span class="sxs-lookup"><span data-stu-id="a9763-p146">version - The version of the published endpoint set in which the change was introduced. Version numbers are of the format _YYYYMMDDNN_, where NN is a natural number incremented if there are multiple versions required to be published on a single day.</span></span>
- <span data-ttu-id="a9763-276">previous — подструктура с подробным указанием предыдущих значений измененных элементов в наборе конечных точек.</span><span class="sxs-lookup"><span data-stu-id="a9763-276">previous - A substructure detailing previous values of changed elements on the endpoint set.</span></span> <span data-ttu-id="a9763-277">Не будет включена для новых добавляемых наборов конечных точек.</span><span class="sxs-lookup"><span data-stu-id="a9763-277">This will not be included for newly added endpoint sets.</span></span> <span data-ttu-id="a9763-278">Включает _ExpressRoute_, _serviceArea_, _category_, _required_, _tcpPorts_, _udpPorts_ и _notes_.</span><span class="sxs-lookup"><span data-stu-id="a9763-278">Includes  _ExpressRoute_, _serviceArea_, _category_, _required_, _tcpPorts_, _udpPorts_, and _notes_.</span></span>
- <span data-ttu-id="a9763-279">current — подструктура с подробным указанием обновленных значений измененных элементов в наборе конечных точек.</span><span class="sxs-lookup"><span data-stu-id="a9763-279">current - A substructure detailing updated values of changes elements on the endpoint set.</span></span> <span data-ttu-id="a9763-280">Включает _ExpressRoute_, _serviceArea_, _category_, _required_, _tcpPorts_, _udpPorts_ и _notes_.</span><span class="sxs-lookup"><span data-stu-id="a9763-280">Includes _ExpressRoute_, _serviceArea_, _category_, _required_, _tcpPorts_, _udpPorts_, and _notes_.</span></span>
- <span data-ttu-id="a9763-p149">add — подструктура с подробным указанием элементов, добавляемых в коллекции наборов конечных точек. Опускается, если добавлений нет.</span><span class="sxs-lookup"><span data-stu-id="a9763-p149">add - A substructure detailing items to be added to endpoint set collections. Omitted if there are no additions.</span></span>
  - <span data-ttu-id="a9763-283">effectiveDate определяет дату начала использования добавлений в службе.</span><span class="sxs-lookup"><span data-stu-id="a9763-283">effectiveDate - Defines the data when the additions will be live in the service.</span></span>
  - <span data-ttu-id="a9763-284">ips — элементы, добавляемые в массив _ips_.</span><span class="sxs-lookup"><span data-stu-id="a9763-284">ips - Items to be added to the _ips_ array.</span></span>
  - <span data-ttu-id="a9763-285">urls — элементы, добавляемые в массив _urls_.</span><span class="sxs-lookup"><span data-stu-id="a9763-285">urls- Items to be added to the _urls_ array.</span></span>
- <span data-ttu-id="a9763-286">remove — подструктура с подробным указанием элементов, удаляемых из набора конечных точек.</span><span class="sxs-lookup"><span data-stu-id="a9763-286">remove - A substructure detailing items to be removed from the endpoint set.</span></span> <span data-ttu-id="a9763-287">Опускается, если удаленных элементов нет.</span><span class="sxs-lookup"><span data-stu-id="a9763-287">Omitted if there are no removals.</span></span>
  - <span data-ttu-id="a9763-288">ips — элементы, удаляемые из массива _ips_.</span><span class="sxs-lookup"><span data-stu-id="a9763-288">ips - Items to be removed from the _ips_ array.</span></span>
  - <span data-ttu-id="a9763-289">urls — элементы, удаляемые из массива _urls_.</span><span class="sxs-lookup"><span data-stu-id="a9763-289">urls- Items to be removed from the _urls_ array.</span></span>

### <a name="examples"></a><span data-ttu-id="a9763-290">Примеры:</span><span class="sxs-lookup"><span data-stu-id="a9763-290">Examples:</span></span>

<span data-ttu-id="a9763-291">Пример 1. Запрос URI: [https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="a9763-291">Example 1 request URI: [https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="a9763-p151">Запрашивает все предыдущие изменения в экземпляре службы Office 365 Worldwide. Пример результата:</span><span class="sxs-lookup"><span data-stu-id="a9763-p151">This requests all previous changes to the Office 365 worldwide service instance. Example result:</span></span>

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
```

<span data-ttu-id="a9763-294">Пример 2. Запрос URI: [https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="a9763-294">Example 2 request URI: [https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="a9763-p152">Запрашивает изменения, внесенные в экземпляр Office 365 Worldwide после выхода указанной версии. В этом случае указанная версия является последней. Пример результата:</span><span class="sxs-lookup"><span data-stu-id="a9763-p152">This requests changes since the specified version to the Office 365 Worldwide instance. In this case, the version specified is the latest. Example result:</span></span>

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

## <a name="example-powershell-script"></a><span data-ttu-id="a9763-298">Пример скрипта PowerShell</span><span class="sxs-lookup"><span data-stu-id="a9763-298">Example PowerShell Script</span></span>

<span data-ttu-id="a9763-299">Этот скрипт PowerShell позволяет узнать, нужно ли выполнить действия для обновленных данных.</span><span class="sxs-lookup"><span data-stu-id="a9763-299">Here is a PowerShell script that you can run to see if there are actions you need to take for updated data.</span></span> <span data-ttu-id="a9763-300">Он проверяет номер версии для конечных точек экземпляра Office 365 Worldwide.</span><span class="sxs-lookup"><span data-stu-id="a9763-300">This script checks the version number for the Office 365 Worldwide instance endpoints.</span></span> <span data-ttu-id="a9763-301">Если изменение есть, скрипт скачивает конечные точки и фильтрует результаты для категорий Allow и Optimize.</span><span class="sxs-lookup"><span data-stu-id="a9763-301">When there is a change, it downloads the endpoints and filters for the "Allow" and "Optimize" category endpoints.</span></span> <span data-ttu-id="a9763-302">Он также использует уникальный _ClientRequestId_ для нескольких вызовов и сохраняет последнюю версию, обнаруженную во временном файле.</span><span class="sxs-lookup"><span data-stu-id="a9763-302">It also uses a unique _ClientRequestId_ across multiple calls and saves the latest version found in a temporary file.</span></span> <span data-ttu-id="a9763-303">Этот скрипт нужно вызывать раз в час для проверки наличия обновления версии.</span><span class="sxs-lookup"><span data-stu-id="a9763-303">You should call this script once an hour to check for a version update.</span></span>

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

## <a name="example-python-script"></a><span data-ttu-id="a9763-304">Пример скрипта на Python</span><span class="sxs-lookup"><span data-stu-id="a9763-304">Example Python Script</span></span>

<span data-ttu-id="a9763-p154">Ниже показан скрипт на Python, протестированный с использованием Python 3.6.3 на Windows 10. Он позволяет узнать, нужно ли выполнить действия для обновленных данных, проверяя номер версии для конечных точек экземпляра Office 365 Worldwide. Если изменение есть, скрипт скачивает конечные точки и фильтрует результаты для категорий _Allow_ и _Optimize_. Он также использует уникальный ClientRequestId для нескольких вызовов и сохраняет последнюю версию, обнаруженную во временном файле. Вам нужно вызывать этот скрипт раз в час для проверки наличия обновления версии.</span><span class="sxs-lookup"><span data-stu-id="a9763-p154">Here is a Python script, tested with Python 3.6.3 on Windows 10, that you can run to see if there are actions you need to take for updated data. This script checks the version number for the Office 365 Worldwide instance endpoints. When there is a change, it downloads the endpoints and filters for the _Allow_ and _Optimize_ category endpoints. It also uses a unique ClientRequestId across multiple calls and saves the latest version found in a temporary file. You should call this script once an hour to check for a version update.</span></span>

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

## <a name="web-service-interface-versioning"></a><span data-ttu-id="a9763-310">Управление версиями интерфейса веб-службы</span><span class="sxs-lookup"><span data-stu-id="a9763-310">Web Service interface versioning</span></span>

<span data-ttu-id="a9763-p155">В будущем могут понадобиться обновления параметров или результатов для этих методов веб-служб. После публикации общедоступной версии веб-служб корпорация Майкрософт примет разумные меры для заблаговременного уведомления о существенных обновлениях веб-службы. Если корпорация Майкрософт сочтет, что обновление потребует изменений клиентов, использующих веб-службы, она сохранит доступ к предыдущей версии веб-службы в течение как минимум 12 месяцев после выпуска новой версии. Пользователи, которые не выполнят обновление в течение этого времени, могут лишиться доступа к веб-службе и ее методам. Пользователи должны убедиться, что клиенты веб-службы продолжат работать без ошибок, если такие изменения будут внесены в подпись интерфейса веб-службы:</span><span class="sxs-lookup"><span data-stu-id="a9763-p155">Updates to the parameters or results for these web service methods may be required in the future. After the general availability version of these web services is published, Microsoft will make reasonable efforts to provide advance notice of material updates to the web service. When Microsoft believes that an update will require changes to clients using the web service, Microsoft will keep the previous version (one version back) of the web service available for at least twelve (12) months after the release of the new version. Customers who do not upgrade during that time may be unable to access the web service and its methods. Customers must ensure that clients of the web service continue working without error if the following changes are made to the web service interface signature:</span></span>

- <span data-ttu-id="a9763-316">Добавление нового необязательного параметра к существующему веб-методу, который необязательно должны предоставлять старые клиенты и который не влияет на результат, получаемый старым клиентом.</span><span class="sxs-lookup"><span data-stu-id="a9763-316">Adding a new optional parameter to an existing web method that doesn't have to be provided by older clients and doesn't impact the result an older client receives.</span></span>
- <span data-ttu-id="a9763-317">Добавление нового именованного атрибута в один из элементов REST отклика или дополнительных столбцов в файл CSV отклика.</span><span class="sxs-lookup"><span data-stu-id="a9763-317">Adding a new named attribute in one of the response REST items or additional columns to the response CSV.</span></span>
- <span data-ttu-id="a9763-318">Добавление нового веб-метода с новым именем, который не вызывается старыми клиентами.</span><span class="sxs-lookup"><span data-stu-id="a9763-318">Adding a new web method with a new name that is not called by the older clients.</span></span>

## <a name="office-365-endpoint-functions-module"></a><span data-ttu-id="a9763-319">Модуль функций конечных точек Office 365</span><span class="sxs-lookup"><span data-stu-id="a9763-319">Office 365 Endpoint Functions Module</span></span>

<span data-ttu-id="a9763-320">Майкрософт содержит службу REST для получения самых новых и последних URI для служб Office 365.</span><span class="sxs-lookup"><span data-stu-id="a9763-320">Microsoft is hosting a REST Service to get the newest and latest URI for the Office 365 services.</span></span>  <span data-ttu-id="a9763-321">Чтобы использовать URI как коллекцию, можно применять этот модуль с несколькими удобными командлетами.</span><span class="sxs-lookup"><span data-stu-id="a9763-321">To be able to use the URI as a collection, you can use this module with a few helpful cmdlets.</span></span>

### <a name="calling-the-rest-service"></a><span data-ttu-id="a9763-322">Вызов службы REST</span><span class="sxs-lookup"><span data-stu-id="a9763-322">Calling the REST service</span></span>

<span data-ttu-id="a9763-323">Чтобы использовать этот модуль, просто скопируйте файл модуля [O365EndpointFunctions.psm1](https://github.com/samurai-ka/PS-Module-O365EndpointService/blob/master/O365EndpointFunctions.psm1) в любое место на своем жестком диске и импортируйте его непосредственно с помощью этой команды:</span><span class="sxs-lookup"><span data-stu-id="a9763-323">To use this module, simply copy the module file [O365EndpointFunctions.psm1](https://github.com/samurai-ka/PS-Module-O365EndpointService/blob/master/O365EndpointFunctions.psm1) somewhere on your hard disk and import it directly with this command:</span></span>

```powershell
    Import-Module O365EndpointFunctions.psm1
```

<span data-ttu-id="a9763-324">После импорта модуля вы сможете вызывать службу REST.</span><span class="sxs-lookup"><span data-stu-id="a9763-324">After you have imported the module, you will be able to call the REST service.</span></span> <span data-ttu-id="a9763-325">Она возвращает URI как коллекцию, которую можно обработать непосредственно в PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a9763-325">This will return the URI as a collection that you can now process in PowerShell directly.</span></span> <span data-ttu-id="a9763-326">Необходимо ввести имя вашего клиента Office 365, как указано в следующей команде:</span><span class="sxs-lookup"><span data-stu-id="a9763-326">You must enter the name of your Office 365 tenant, as described in the following command:</span></span>

```powershell
    Invoke-O365EndpointService -tenantName [Name of your tenant]
```

#### <a name="parameters"></a><span data-ttu-id="a9763-327">Параметры</span><span class="sxs-lookup"><span data-stu-id="a9763-327">Parameters</span></span>

- <span data-ttu-id="a9763-328">**tenantName**. Имя вашего клиента Office 365.</span><span class="sxs-lookup"><span data-stu-id="a9763-328">**tenantName** - The name of your Office 365 tenant.</span></span> <span data-ttu-id="a9763-329">Это обязательный параметр.</span><span class="sxs-lookup"><span data-stu-id="a9763-329">This parameter is mandatory.</span></span>
- <span data-ttu-id="a9763-330">**ForceLatest**. Этот параметр заставляет API REST всегда возвращать весь список последних URI.</span><span class="sxs-lookup"><span data-stu-id="a9763-330">**ForceLatest** -This switch will force the REST API to always return the entire list of the latest URI.</span></span>
- <span data-ttu-id="a9763-331">**IPv6**. Этот параметр дополнительно возвращает адреса IPv6.</span><span class="sxs-lookup"><span data-stu-id="a9763-331">**IPv6** -This switch will return the IPv6 addresses as well.</span></span> <span data-ttu-id="a9763-332">По умолчанию возвращаются только адреса IPv4.</span><span class="sxs-lookup"><span data-stu-id="a9763-332">As default only IPv4 will be returned.</span></span>

### <a name="examples"></a><span data-ttu-id="a9763-333">Примеры</span><span class="sxs-lookup"><span data-stu-id="a9763-333">Examples</span></span>

<span data-ttu-id="a9763-334">Возвращение полного списка всех URI, включая адреса IPv6</span><span class="sxs-lookup"><span data-stu-id="a9763-334">Return the complete list of all URIs including the IPv6 addresses</span></span>

```powershell
    Invoke-O365EndpointService -tenantName [Name of your tenant] -ForceLatest -IPv6 | Format-Table -AutoSize
```

<span data-ttu-id="a9763-335">Возвращение только IP-адресов для службы Exchange Online</span><span class="sxs-lookup"><span data-stu-id="a9763-335">Return only the IP addresses for Exchange Online Service</span></span>

```powershell
    Invoke-O365EndpointService -tenantName [Name of your tenant] -ForceLatest | where{($_.serviceArea -eq "Exchange") -and ($_.protocol -eq "ip")}| Format-Table -AutoSize
```

### <a name="exporting-a-proxy-pac-file"></a><span data-ttu-id="a9763-336">Экспорт PAC-файла прокси-сервера</span><span class="sxs-lookup"><span data-stu-id="a9763-336">Exporting a Proxy PAC file</span></span>

<span data-ttu-id="a9763-337">Этот модуль можно использовать для создания PAC-файла прокси-сервера.</span><span class="sxs-lookup"><span data-stu-id="a9763-337">You can use this module to create a Proxy PAC file.</span></span> <span data-ttu-id="a9763-338">В этом примере сначала возвращаются конечные точки, а затем результаты фильтруются для выбора URL-адресов.</span><span class="sxs-lookup"><span data-stu-id="a9763-338">In this example you first get the endpoints and filter the result to select the URLs.</span></span> <span data-ttu-id="a9763-339">Эти URL-адреса передаются для экспорта.</span><span class="sxs-lookup"><span data-stu-id="a9763-339">These URLs are piped to be exported.</span></span>  

```powershell
 Invoke-O365EndpointService -tenantName [Name of your tenant] -ForceLatest | where{($_.Protocol -eq "Url") -and (($_.Category -eq "Optimize") -or ($_.category -eq "Allow"))} | select uri -Unique | Export-O365ProxyPacFile
```

## <a name="related-topics"></a><span data-ttu-id="a9763-340">Статьи по теме</span><span class="sxs-lookup"><span data-stu-id="a9763-340">Related Topics</span></span>
  
[<span data-ttu-id="a9763-341">Диапазоны IP-адресов и URL-адреса Office 365</span><span class="sxs-lookup"><span data-stu-id="a9763-341">Office 365 URLs and IP address ranges</span></span>](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[<span data-ttu-id="a9763-342">Вопросы и ответы о конечных точках Office 365</span><span class="sxs-lookup"><span data-stu-id="a9763-342">Office 365 endpoints FAQ</span></span>](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)

[<span data-ttu-id="a9763-343">Принципы сетевого подключения к Office 365</span><span class="sxs-lookup"><span data-stu-id="a9763-343">Office 365 Network Connectivity Principles</span></span>](office-365-network-connectivity-principles.md)

[<span data-ttu-id="a9763-344">Сеть Office 365 и настройка производительности</span><span class="sxs-lookup"><span data-stu-id="a9763-344">Office 365 network and performance tuning</span></span>](network-planning-and-performance.md)

[<span data-ttu-id="a9763-345">Сетевое подключение к Office 365</span><span class="sxs-lookup"><span data-stu-id="a9763-345">Network connectivity to Office 365</span></span>](network-connectivity.md)
  
[<span data-ttu-id="a9763-346">Качество мультимедиа и характеристики сетевого подключения в случае Skype для бизнеса Online</span><span class="sxs-lookup"><span data-stu-id="a9763-346">Media Quality and Network Connectivity Performance in Skype for Business Online</span></span>](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[<span data-ttu-id="a9763-347">Оптимизация сети для Skype для бизнеса Online</span><span class="sxs-lookup"><span data-stu-id="a9763-347">Optimizing your network for Skype for Business Online</span></span>](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)

[<span data-ttu-id="a9763-348">Настройка производительности Office 365 с помощью базовых показателей и журнала производительности</span><span class="sxs-lookup"><span data-stu-id="a9763-348">Office 365 performance tuning using baselines and performance history</span></span>](performance-tuning-using-baselines-and-history.md)
  
[<span data-ttu-id="a9763-349">План устранения проблем с производительностью Office 365</span><span class="sxs-lookup"><span data-stu-id="a9763-349">Performance troubleshooting plan for Office 365</span></span>](performance-troubleshooting-plan.md)
