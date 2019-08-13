---
title: Веб-служба IP-адресов и URL-адресов в Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 8/6/2019
audience: ITPro
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
description: Веб-служба IP-адресов и URL-адресов в Office 365 позволяет лучше выявлять и разграничивать сетевой трафик Office 365, упрощая оценку, настройку и обновление.
ms.openlocfilehash: 90de20f28e271e3fb174a883eb9cda3fb1228fb4
ms.sourcegitcommit: 6db61b95b1b5b4312dd6bc42bec6597e359b1bd7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/06/2019
ms.locfileid: "36212984"
---
# <a name="office-365-ip-address-and-url-web-service"></a><span data-ttu-id="7fe72-103">Веб-служба IP-адресов и URL-адресов в Office 365</span><span class="sxs-lookup"><span data-stu-id="7fe72-103">Office 365 IP Address and URL Web service</span></span>

<span data-ttu-id="7fe72-104">Веб-служба IP-адресов и URL-адресов в Office 365 позволяет лучше выявлять и разграничивать сетевой трафик Office 365, упрощая оценку, настройку и обновление.</span><span class="sxs-lookup"><span data-stu-id="7fe72-104">The Office 365 IP Address and URL web service helps you better identify and differentiate Office 365 network traffic, making it easier for you to evaluate, configure, and stay up to date with changes.</span></span> <span data-ttu-id="7fe72-105">Эта веб-служба на основе REST заменяет собой ранее доступные скачиваемые XML-файлы, поддержка которых была прекращена 2 октября 2018 г.</span><span class="sxs-lookup"><span data-stu-id="7fe72-105">This REST-based web service replaces the previous XML downloadable files, which were phased out on October 2, 2018.</span></span>

<span data-ttu-id="7fe72-106">Будучи клиентом или поставщиком устройств сети периметра, вы можете создавать решения с использованием веб-службы для записей FQDN и IP-адресов в Office 365.</span><span class="sxs-lookup"><span data-stu-id="7fe72-106">As a customer or a network perimeter device vendor, you can build against the new REST-based web service for the Office 365 IP address and FQDN entries. You can access the data directly in a web browser using these URLs.</span></span> <span data-ttu-id="7fe72-107">Доступ к данным можно получить непосредственно в браузере с помощью этих URL-адресов:</span><span class="sxs-lookup"><span data-stu-id="7fe72-107">You can access the data directly in a web browser using these URLs:</span></span>

- <span data-ttu-id="7fe72-108">Для получения последней версии диапазонов IP-адресов и URL-адресов Office 365 перейдите на веб-страницу [https://endpoints.office.com/version](https://endpoints.office.com/version?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span><span class="sxs-lookup"><span data-stu-id="7fe72-108">For the latest version of the Office 365 URLs and IP address ranges, use [https://endpoints.office.com/version](https://endpoints.office.com/version?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span></span>
- <span data-ttu-id="7fe72-109">Для получения данных на странице диапазонов IP-адресов и URL-адресов Office 365 для брандмауэров и прокси-серверов перейдите на веб-страницу [https://endpoints.office.com/endpoints/worldwide](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span><span class="sxs-lookup"><span data-stu-id="7fe72-109">For the data on the Office 365 URLs and IP address ranges page for firewalls and proxy servers, use [https://endpoints.office.com/endpoints/worldwide](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span></span>
- <span data-ttu-id="7fe72-110">Для получения всех последних изменений с июля 2018 года (тогда стала доступной веб-служба) перейдите на веб-страницу [https://endpoints.office.com/changes/worldwide/0000000000](https://endpoints.office.com/changes/worldwide/0000000000?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span><span class="sxs-lookup"><span data-stu-id="7fe72-110">To get all the latest changes since the end of July 2018 when the web service was first available, use [https://endpoints.office.com/changes/worldwide/0000000000](https://endpoints.office.com/changes/worldwide/0000000000?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span></span>

<span data-ttu-id="7fe72-111">Как клиент вы можете использовать эту веб-службу, чтобы:</span><span class="sxs-lookup"><span data-stu-id="7fe72-111">As a customer, you can use this web service to:</span></span>

- <span data-ttu-id="7fe72-112">обновлять скрипты PowerShell для получения данных конечной точки Office 365 и изменять форматирование для сетевых устройств;</span><span class="sxs-lookup"><span data-stu-id="7fe72-112">Update your PowerShell scripts to obtain Office 365 endpoint data and modify any formatting for your networking devices.</span></span>
- <span data-ttu-id="7fe72-113">применять эту информацию для обновления PAC-файлов, развернутых на клиентских компьютерах.</span><span class="sxs-lookup"><span data-stu-id="7fe72-113">Use this information to update PAC files deployed to client computers.</span></span>

<span data-ttu-id="7fe72-114">Как поставщик устройств сети периметра вы можете использовать эту веб-службу, чтобы:</span><span class="sxs-lookup"><span data-stu-id="7fe72-114">As a network perimeter device vendor, you can use this web service to:</span></span>

- <span data-ttu-id="7fe72-115">создавать и тестировать программное обеспечение устройств для скачивания списка с целью автоматической настройки;</span><span class="sxs-lookup"><span data-stu-id="7fe72-115">Create and test device software to download the list for automated configuration.</span></span>
- <span data-ttu-id="7fe72-116">проверять текущую версию;</span><span class="sxs-lookup"><span data-stu-id="7fe72-116">Check for the current version.</span></span>
- <span data-ttu-id="7fe72-117">получать текущие изменения.</span><span class="sxs-lookup"><span data-stu-id="7fe72-117">Get the current changes.</span></span>

> [!NOTE]
> <span data-ttu-id="7fe72-118">Если вы используете Azure ExpressRoute для подключения к Office 365, см. статью [Azure ExpressRoute для Office 365](https://docs.microsoft.com/office365/enterprise/azure-expressroute), чтобы ознакомиться со службами Office 365, поддерживаемыми в Azure ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="7fe72-118">If you are using Azure ExpressRoute to connect to Office 365, please review [Azure ExpressRoute for Office 365](https://docs.microsoft.com/office365/enterprise/azure-expressroute) to familiarize yourself with the Office 365 services supported over Azure ExpressRoute.</span></span> <span data-ttu-id="7fe72-119">Чтобы понимать, какие сетевые запросы для приложений Office 365 требуют подключения в Интернету, см. статью [URL-адреса и диапазоны IP-адресов Office 365](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges?redirectSourcePath=%252farticle%252fOffice-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2).</span><span class="sxs-lookup"><span data-stu-id="7fe72-119">Also review the article [Office 365 URLs and IP address ranges](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges?redirectSourcePath=%252farticle%252fOffice-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) to understand which network requests for Office 365 applications require Internet connectivity.</span></span> <span data-ttu-id="7fe72-120">Это поможет вам лучше настроить устройства периметра безопасности.</span><span class="sxs-lookup"><span data-stu-id="7fe72-120">This will help to better configure your perimeter security devices.</span></span>

<span data-ttu-id="7fe72-121">Подробнее:</span><span class="sxs-lookup"><span data-stu-id="7fe72-121">For more information, see:</span></span>

- [<span data-ttu-id="7fe72-122">Объявление в записи блога на форуме Tech Community Office 365.</span><span class="sxs-lookup"><span data-stu-id="7fe72-122">Announcement blog post in the Office 365 Tech Community Forum</span></span>](https://techcommunity.microsoft.com/t5/Office-365-Blog/Announcing-Office-365-endpoint-categories-and-Office-365-IP/ba-p/177638)
- [<span data-ttu-id="7fe72-123">Форум Tech Community Office 365, содержащий сведения об использовании веб-служб.</span><span class="sxs-lookup"><span data-stu-id="7fe72-123">Office 365 Tech Community Forum for questions about use of the web services</span></span>](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)

## <a name="common-parameters"></a><span data-ttu-id="7fe72-124">Общие параметры</span><span class="sxs-lookup"><span data-stu-id="7fe72-124">Common parameters</span></span>

<span data-ttu-id="7fe72-125">Эти параметры являются общими для всех методов веб-службы:</span><span class="sxs-lookup"><span data-stu-id="7fe72-125">These parameters are common across all the web service methods:</span></span>

- <span data-ttu-id="7fe72-126">**format=<JSON | CSV>**. По умолчанию данные возвращаются в формате JSON.</span><span class="sxs-lookup"><span data-stu-id="7fe72-126">**format=<JSON | CSV>** - By default, the returned data format is JSON.</span></span> <span data-ttu-id="7fe72-127">Используйте этот необязательный параметр для возврата данных в формате данных с разделителями-запятыми (CSV).</span><span class="sxs-lookup"><span data-stu-id="7fe72-127">Use this optional parameter to return the data in comma-separated values (CSV) format.</span></span>
- <span data-ttu-id="7fe72-128">**ClientRequestId=\<guid>**. Обязательный GUID, создаваемый для сопоставления клиента.</span><span class="sxs-lookup"><span data-stu-id="7fe72-128">**ClientRequestId=\<guid>** - A required GUID that you generate for client association.</span></span> <span data-ttu-id="7fe72-129">Создайте уникальный GUID для каждого компьютера, который вызывает веб-службу (скрипты, указанные на этой странице, позволяют создать GUID).</span><span class="sxs-lookup"><span data-stu-id="7fe72-129">Generate a unique GUID for each machine that calls the web service (the scripts included on this page generate a GUID for you).</span></span> <span data-ttu-id="7fe72-130">Не используйте GUID, показанные в примерах ниже, так как они могут быть заблокированы веб-службой в будущем.</span><span class="sxs-lookup"><span data-stu-id="7fe72-130">Do not use the GUIDs shown in the following examples because they may be blocked by the web service in the future.</span></span> <span data-ttu-id="7fe72-131">Формат GUID: _xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx_. Здесь "x" означает шестнадцатеричное число.</span><span class="sxs-lookup"><span data-stu-id="7fe72-131">GUID format is _xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx_, where x represents a hexadecimal number.</span></span>

  <span data-ttu-id="7fe72-132">Чтобы создать GUID, можно использовать команду PowerShell [New-Guid](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-guid?view=powershell-6) или веб-службу, например [Online GUID Generator](https://www.guidgenerator.com/).</span><span class="sxs-lookup"><span data-stu-id="7fe72-132">To generate a GUID, you can use the [New-Guid](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-guid?view=powershell-6) PowerShell command, or use an online service such as [Online GUID Generator](https://www.guidgenerator.com/).</span></span>

## <a name="version-web-method"></a><span data-ttu-id="7fe72-133">Веб-метод версии</span><span class="sxs-lookup"><span data-stu-id="7fe72-133">Version web method</span></span>

<span data-ttu-id="7fe72-134">Корпорация Майкрософт обновляет записи IP-адресов и FQDN Office 365 в конце каждого месяца.</span><span class="sxs-lookup"><span data-stu-id="7fe72-134">Microsoft updates the Office 365 IP address and FQDN entries at the end of each month.</span></span> <span data-ttu-id="7fe72-135">Иногда обновления публикуются вне цикла для устранения инцидентов, поддержки обновлений для системы безопасности или выполнения других операционных требований.</span><span class="sxs-lookup"><span data-stu-id="7fe72-135">Out-of-band updates are sometimes published due to support incidents, security updates or other operational requirements.</span></span>

<span data-ttu-id="7fe72-136">Данным для каждого опубликованного экземпляра назначается номер версии, а веб-метод версии позволяет проверить наличие последней версии каждого экземпляра службы Office 365.</span><span class="sxs-lookup"><span data-stu-id="7fe72-136">The data for each published instance is assigned a version number, and the version web method enables you to check for the latest version of each Office 365 service instance.</span></span> <span data-ttu-id="7fe72-137">Рекомендуем проверять версию не чаще, чем раз в час.</span><span class="sxs-lookup"><span data-stu-id="7fe72-137">We recommend that you check the version not more than once an hour.</span></span>

<span data-ttu-id="7fe72-138">Параметры для веб-метода версии:</span><span class="sxs-lookup"><span data-stu-id="7fe72-138">Parameters for the version web method are:</span></span>

- <span data-ttu-id="7fe72-139">**AllVersions=<true | false>**. По умолчанию возвращается последний номер версии.</span><span class="sxs-lookup"><span data-stu-id="7fe72-139">**AllVersions=<true | false>** - By default, the version returned is the latest.</span></span> <span data-ttu-id="7fe72-140">Включите этот необязательный параметр для запрашивания всех версий, опубликованных с момента первого выпуска веб-службы.</span><span class="sxs-lookup"><span data-stu-id="7fe72-140">Include this optional parameter to request all published versions since the web service was first released.</span></span>
- <span data-ttu-id="7fe72-141">**Format=<JSON | CSV | RSS>**. Кроме форматов JSON и CSV, веб-метод версии поддерживает RSS.</span><span class="sxs-lookup"><span data-stu-id="7fe72-141">**Format=<JSON | CSV | RSS>** – In addition to the JSON and CSV formats, the version web method also supports RSS.</span></span> <span data-ttu-id="7fe72-142">Вы можете использовать этот необязательный параметр вместе с параметром _AllVersions=true_ для запрашивания RSS-канала, который можно применять в Outlook или других средствах чтения RSS.</span><span class="sxs-lookup"><span data-stu-id="7fe72-142">You can use this optional parameter along with the _AllVersions=true_ parameter to request an RSS feed which can be used with Outlook or other RSS readers.</span></span>
- <span data-ttu-id="7fe72-143">**Instance=<Worldwide | China | Germany | USGovDoD | USGovGCCHigh>**. Этот необязательный параметр указывает экземпляр, для которого возвращается версия.</span><span class="sxs-lookup"><span data-stu-id="7fe72-143">**Instance=<Worldwide | China | Germany | USGovDoD | USGovGCCHigh>** - This optional parameter specifies the instance to return the version for.</span></span> <span data-ttu-id="7fe72-144">Если его опустить, будут возвращены все экземпляры.</span><span class="sxs-lookup"><span data-stu-id="7fe72-144">If omitted, all instances are returned.</span></span> <span data-ttu-id="7fe72-145">Допустимые экземпляры: Worldwide, China, Germany, USGovDoD, USGovGCCHigh.</span><span class="sxs-lookup"><span data-stu-id="7fe72-145">Valid instances are: Worldwide, China, Germany, USGovDoD, USGovGCCHigh.</span></span>

<span data-ttu-id="7fe72-146">Веб-метод версии не имеет ограничения по частоте и не возвращает HTTP-код отклика 429.</span><span class="sxs-lookup"><span data-stu-id="7fe72-146">The version web method is not rate limited and does not ever return 429 HTTP Response Codes.</span></span> <span data-ttu-id="7fe72-147">Отклик для веб-метода версии включает заголовок с контролем кэша, рекомендующий кэширование данных в течение 1 часа.</span><span class="sxs-lookup"><span data-stu-id="7fe72-147">The response to the version web method does include a cache-control header recommending caching of the data for 1 hour.</span></span> <span data-ttu-id="7fe72-148">Результатом веб-метода версии может быть отдельная запись или массив записей.</span><span class="sxs-lookup"><span data-stu-id="7fe72-148">The result from the version web method can be a single record or an array of records.</span></span> <span data-ttu-id="7fe72-149">Ниже перечислены элементы каждой записи.</span><span class="sxs-lookup"><span data-stu-id="7fe72-149">The elements of each record are:</span></span>

- <span data-ttu-id="7fe72-150">instance — короткое имя экземпляра службы Office 365.</span><span class="sxs-lookup"><span data-stu-id="7fe72-150">instance - The short name of the Office 365 service instance.</span></span>
- <span data-ttu-id="7fe72-151">latest — последняя версия для конечных точек указанного экземпляра.</span><span class="sxs-lookup"><span data-stu-id="7fe72-151">latest - The latest version for endpoints of the specified instance.</span></span>
- <span data-ttu-id="7fe72-152">versions — список всех предыдущих версий для указанного экземпляра.</span><span class="sxs-lookup"><span data-stu-id="7fe72-152">versions - A list of all previous versions for the specified instance. This element is only included if the AllVersions parameter is true.</span></span> <span data-ttu-id="7fe72-153">Этот элемент включается, только если параметр _AllVersions_ имеет значение true.</span><span class="sxs-lookup"><span data-stu-id="7fe72-153">versions - A list of all previous versions for the specified instance. This element is only included if the AllVersions parameter is true.</span></span>

### <a name="examples"></a><span data-ttu-id="7fe72-154">Примеры:</span><span class="sxs-lookup"><span data-stu-id="7fe72-154">Examples:</span></span>

<span data-ttu-id="7fe72-155">Пример 1. Запрос URI: [https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="7fe72-155">Example 1 request URI: [https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="7fe72-p113">Этот URI возвращает последнюю версию каждого экземпляра службы Office 365. Пример результата:</span><span class="sxs-lookup"><span data-stu-id="7fe72-p113">This URI returns the latest version of each Office 365 service instance. Example result:</span></span>

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
> <span data-ttu-id="7fe72-p114">GUID для параметра ClientRequestID в этих URI приведен только в качестве примера. Чтобы попробовать применить URI веб-службы, создайте собственный GUID. GUID, показанные в этих примерах, могут быть заблокированы веб-службой в будущем.</span><span class="sxs-lookup"><span data-stu-id="7fe72-p114">The GUID for the ClientRequestID parameter in these URIs are only an example. To try the web service URIs out, generate your own GUID. The GUIDs shown in these examples may be blocked by the web service in the future.</span></span>

<span data-ttu-id="7fe72-161">Пример 2. Запрос URI: [https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="7fe72-161">Example 2 request URI: [https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="7fe72-p115">Этот URI возвращает последнюю версию указанного экземпляра службы Office 365. Пример результата:</span><span class="sxs-lookup"><span data-stu-id="7fe72-p115">This URI returns the latest version of the specified Office 365 service instance. Example result:</span></span>

```json
{
 "instance": "Worldwide",
 "latest": "2018063000"
}
```

<span data-ttu-id="7fe72-164">Пример 3. Запрос URI: [https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="7fe72-164">Example 3 request URI: [https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="7fe72-p116">Этот URI показывает выходные данные в формате CSV. Пример результата:</span><span class="sxs-lookup"><span data-stu-id="7fe72-p116">This URI shows output in CSV format. Example result:</span></span>

```csv
instance,latest
Worldwide,2018063000
```

<span data-ttu-id="7fe72-167">Пример 4. Запрос URI: [https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="7fe72-167">Example 4 request URI: [https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="7fe72-p117">Этот URI показывает все более ранние версии, которые были опубликованы для экземпляра службы Office 365 Worldwide. Пример результата:</span><span class="sxs-lookup"><span data-stu-id="7fe72-p117">This URI shows all prior versions that have been published for the Office 365 worldwide service instance. Example result:</span></span>

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

<span data-ttu-id="7fe72-170">Пример 5. URI RSS-канала: [https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS](https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS)</span><span class="sxs-lookup"><span data-stu-id="7fe72-170">Example 5 RSS Feed URI: [https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS](https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS)</span></span>

<span data-ttu-id="7fe72-p118">Этот URI показывает RSS-канал опубликованных версий, которые содержат ссылки на список изменений для каждой версии. Пример результата:</span><span class="sxs-lookup"><span data-stu-id="7fe72-p118">This URI shows an RSS feed of the published versions that include links to the list of changes for each version. Example result:</span></span>

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

## <a name="endpoints-web-method"></a><span data-ttu-id="7fe72-173">Веб-метод конечных точек</span><span class="sxs-lookup"><span data-stu-id="7fe72-173">Endpoints web method</span></span>

<span data-ttu-id="7fe72-174">Веб-метод конечных точек возвращает все записи для диапазонов IP-адресов и URL-адресов, входящих в службу Office 365.</span><span class="sxs-lookup"><span data-stu-id="7fe72-174">The endpoints web method returns all records for IP address ranges and URLs that make up the Office 365 service.</span></span> <span data-ttu-id="7fe72-175">Для настройки сетевого устройства всегда следует использовать новейшие данные от веб-метода конечных точек.</span><span class="sxs-lookup"><span data-stu-id="7fe72-175">The latest data from the endpoints web method should always be used for network device configuration.</span></span> <span data-ttu-id="7fe72-176">Корпорация Майкрософт отправляет уведомление за 30 дней до публикации новых дополнений, чтобы вы успели обновить списки управления доступом и списки обхода прокси-сервера.</span><span class="sxs-lookup"><span data-stu-id="7fe72-176">Microsoft provides advance notice 30 days prior to publishing new additions to give you time to update access control lists and proxy server bypass lists.</span></span> <span data-ttu-id="7fe72-177">Рекомендуем вызывать веб-метод конечных точек еще раз, только когда веб-метод версии указывает на доступность новой версии данных.</span><span class="sxs-lookup"><span data-stu-id="7fe72-177">We recommend you only call the endpoints web method again when the version web method indicates a new version of the data is available.</span></span>

<span data-ttu-id="7fe72-178">Параметры веб-метода конечных точек представлены ниже.</span><span class="sxs-lookup"><span data-stu-id="7fe72-178">Parameters for the endpoints web method are:</span></span>

- <span data-ttu-id="7fe72-179">**ServiceAreas=<Common | Exchange | SharePoint | Skype>**. Список областей обслуживания, разделенных запятыми.</span><span class="sxs-lookup"><span data-stu-id="7fe72-179">**ServiceAreas=<Common | Exchange | SharePoint | Skype>** - A comma-separated list of service areas.</span></span> <span data-ttu-id="7fe72-180">Допустимые элементы: _Common_, _Exchange_, _SharePoint_ и _Skype_.</span><span class="sxs-lookup"><span data-stu-id="7fe72-180">Valid items are _Common_, _Exchange_, _SharePoint_, and _Skype_.</span></span> <span data-ttu-id="7fe72-181">Так как элементы области обслуживания _Common_ обязательны для всех других областей обслуживания, веб-служба всегда включает их.</span><span class="sxs-lookup"><span data-stu-id="7fe72-181">Because Common service area items are a prerequisite for all other service areas, the web service will always include them.</span></span> <span data-ttu-id="7fe72-182">Если не включить этот параметр, будут возвращены все области обслуживания.</span><span class="sxs-lookup"><span data-stu-id="7fe72-182">If you do not include this parameter, all service areas are returned.</span></span>
- <span data-ttu-id="7fe72-183">**TenantName=<имя_клиента>**. Имя клиента Office 365.</span><span class="sxs-lookup"><span data-stu-id="7fe72-183">**TenantName=<tenant_name>** - Your Office 365 tenant name.</span></span> <span data-ttu-id="7fe72-184">Веб-служба получает предоставленное вами имя и вставляет его в части URL-адресов, которые включают имя клиента.</span><span class="sxs-lookup"><span data-stu-id="7fe72-184">The web service takes your provided name and inserts it in parts of URLs that include the tenant name.</span></span> <span data-ttu-id="7fe72-185">Если вы не предоставляете имя клиента, эти части URL-адресов будут содержать подстановочный знак (\*).</span><span class="sxs-lookup"><span data-stu-id="7fe72-185">If you don't provide a tenant name, those parts of URLs have the wildcard character (\*).</span></span>
- <span data-ttu-id="7fe72-186">**NoIPv6=<true | false>**. Установите для него значение _true_, чтобы исключить адреса IPv6 из выходных данных, если в вашей сети не используется IPv6.</span><span class="sxs-lookup"><span data-stu-id="7fe72-186">**NoIPv6=<true | false>** - Set this to true to exclude IPv6 addresses from the output, for example, if you don't use IPv6 in your network.</span></span>
- <span data-ttu-id="7fe72-187">**Instance=<Worldwide | China | Germany | USGovDoD | USGovGCCHigh>**. Этот обязательный параметр указывает экземпляр, из которого должны быть возвращены конечные точки.</span><span class="sxs-lookup"><span data-stu-id="7fe72-187">**Instance=<Worldwide | China | Germany | USGovDoD | USGovGCCHigh>** - This required parameter specifies the instance to return the endpoints for.</span></span> <span data-ttu-id="7fe72-188">Допустимые экземпляры: _Worldwide_, _China_, _Germany_, _USGovDoD_ и _USGovGCCHigh_.</span><span class="sxs-lookup"><span data-stu-id="7fe72-188">Valid instances are: _Worldwide_, _China_, _Germany_, _USGovDoD_, and _USGovGCCHigh_.</span></span>

<span data-ttu-id="7fe72-189">Если вы вызываете веб-метод конечных точек слишком часто с одного клиентского IP-адреса, то можете получить код HTTP-отклика _429 (слишком большое количество запросов)_.</span><span class="sxs-lookup"><span data-stu-id="7fe72-189">If you call the endpoints web method a large number of times from the same client IP address, you may receive HTTP response code 429 (Too Many Requests).</span></span> <span data-ttu-id="7fe72-190">Если вы получили этот код отклика, подождите 1 час перед повтором своего запроса или сгенерируйте новый GUID для запроса.</span><span class="sxs-lookup"><span data-stu-id="7fe72-190">If you get this response code, wait 1 hour before repeating your request, or generate a new GUID for the request.</span></span> <span data-ttu-id="7fe72-191">Рекомендуется запланировать вызов веб-метода конечных точек, только если веб-метод версии указывает, что доступна новая версия.</span><span class="sxs-lookup"><span data-stu-id="7fe72-191">Plan to only call the endpoints web method when the version web method indicates there is a new version available.</span></span>

<span data-ttu-id="7fe72-192">Результат веб-метода конечных точек — массив записей, в котором каждая запись представляет собой определенный набор конечных точек.</span><span class="sxs-lookup"><span data-stu-id="7fe72-192">The result from the endpoints web method is an array of records in which each record represents a specific endpoint set.</span></span> <span data-ttu-id="7fe72-193">Элементы каждой записи:</span><span class="sxs-lookup"><span data-stu-id="7fe72-193">The elements for each record are:</span></span>

- <span data-ttu-id="7fe72-194">id — неизменяемый идентификатор набора конечных точек.</span><span class="sxs-lookup"><span data-stu-id="7fe72-194">id - The immutable id number of the endpoint set.</span></span>
- <span data-ttu-id="7fe72-195">serviceArea — область обслуживания, которая является частью _Common_, _Exchange_, _SharePoint_ или _Skype_.</span><span class="sxs-lookup"><span data-stu-id="7fe72-195">serviceArea - The service area that this is part of: Common, Exchange, SharePoint, or Skype.</span></span>
- <span data-ttu-id="7fe72-196">urls — URL-адреса для набора конечных точек.</span><span class="sxs-lookup"><span data-stu-id="7fe72-196">urls — URLs for the endpoint set.</span></span> <span data-ttu-id="7fe72-197">Массив JSON записей DNS.</span><span class="sxs-lookup"><span data-stu-id="7fe72-197">A JSON array of DNS records.</span></span> <span data-ttu-id="7fe72-198">Если значение не указано, опускается.</span><span class="sxs-lookup"><span data-stu-id="7fe72-198">Omitted if blank.</span></span>
- <span data-ttu-id="7fe72-199">tcpPorts — TCP-порты для набора конечных точек.</span><span class="sxs-lookup"><span data-stu-id="7fe72-199">tcpPorts — TCP ports for the endpoint set.</span></span> <span data-ttu-id="7fe72-200">Все элементы портов отформатированы в виде списка портов с разделителями-запятыми или диапазонов портов, разделенных символами дефиса (-).</span><span class="sxs-lookup"><span data-stu-id="7fe72-200">tcpPorts - TCP ports for the endpoint set. All ports elements are formatted as a comma-separated list of ports or port ranges separated by a dash character (-). Ports apply to all IP addresses and all URLs in that endpoint set for that category. Omitted if blank.</span></span> <span data-ttu-id="7fe72-201">Порты применяются ко всем IP-адресам и URL-адресам в наборе конечных точек для данной категории.</span><span class="sxs-lookup"><span data-stu-id="7fe72-201">Ports apply to all IP addresses and all URLs in the endpoint set for a given category.</span></span> <span data-ttu-id="7fe72-202">Если значение не указано, опускается.</span><span class="sxs-lookup"><span data-stu-id="7fe72-202">Omitted if blank.</span></span>
- <span data-ttu-id="7fe72-203">udpPorts — порты UDP для диапазонов IP-адресов в этом наборе конечных точек.</span><span class="sxs-lookup"><span data-stu-id="7fe72-203">udpPorts - UDP ports for the IP address ranges in this endpoint set. Omitted if blank.</span></span> <span data-ttu-id="7fe72-204">Если значение не указано, опускается.</span><span class="sxs-lookup"><span data-stu-id="7fe72-204">Omitted if blank.</span></span>
- <span data-ttu-id="7fe72-205">ips — диапазоны IP-адресов, связанные с этим набором конечных точек (с перечисленными портами TCP или UDP).</span><span class="sxs-lookup"><span data-stu-id="7fe72-205">ips - The IP address ranges associated with this endpoint set as associated with the listed TCP or UDP ports. A JSON array of IP Address ranges. Omitted if blank.</span></span> <span data-ttu-id="7fe72-206">Массив JSON, включающий диапазоны IP-адресов.</span><span class="sxs-lookup"><span data-stu-id="7fe72-206">A JSON array of IP address ranges.</span></span> <span data-ttu-id="7fe72-207">Если значение не указано, опускается.</span><span class="sxs-lookup"><span data-stu-id="7fe72-207">Omitted if blank.</span></span>
- <span data-ttu-id="7fe72-208">category — категория возможности подключения к набору конечных точек.</span><span class="sxs-lookup"><span data-stu-id="7fe72-208">category — The connectivity category for the endpoint set.</span></span> <span data-ttu-id="7fe72-209">Допустимые значения: _Optimize_, _Allow_ и _Default_.</span><span class="sxs-lookup"><span data-stu-id="7fe72-209">Valid values are _Optimize_, _Allow_, and _Default_.</span></span> <span data-ttu-id="7fe72-210">Если выходные данные веб-метода конечных точек используются для поиска определенного IP- или URL-адреса, запрос может возвращать несколько категорий.</span><span class="sxs-lookup"><span data-stu-id="7fe72-210">If you search the endpoints web method output for the category of a specific IP address or URL, it is possible that your query will return multiple categories.</span></span> <span data-ttu-id="7fe72-211">В таком случае необходимо следовать рекомендациям для категории с наивысшим приоритетом.</span><span class="sxs-lookup"><span data-stu-id="7fe72-211">In such a case, follow the recommendation for the highest priority category.</span></span> <span data-ttu-id="7fe72-212">Например, если для конечной точки выводятся значения _Optimize_ и _Allow_, следует выполнять требования для значения _Optimize_.</span><span class="sxs-lookup"><span data-stu-id="7fe72-212">For example, if the endpoint appears in both _Optimize_ and _Allow_, you should follow the requirements for _Optimize_.</span></span> <span data-ttu-id="7fe72-213">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="7fe72-213">Required.</span></span>
- <span data-ttu-id="7fe72-214">expressRoute имеет значение _True_, если для этого набора конечных точек выполняется маршрутизация через ExpressRoute. В противном случае он получает значение _False_.</span><span class="sxs-lookup"><span data-stu-id="7fe72-214">expressRoute - True or False if this endpoint set is routed over ExpressRoute.</span></span>
- <span data-ttu-id="7fe72-215">required имеет значение _True_, если этот набор конечных точек требуется для подключения к Office 365.</span><span class="sxs-lookup"><span data-stu-id="7fe72-215">required - True if this endpoint set is required to have connectivity for Office 365 to be supported. False if this endpoint set is optional.</span></span> <span data-ttu-id="7fe72-216">Имеет значение _False_, если этот набор конечных точек необязателен.</span><span class="sxs-lookup"><span data-stu-id="7fe72-216">_False_ if this endpoint set is optional.</span></span>
- <span data-ttu-id="7fe72-217">notes — текст, который в случае необязательных конечных точек описывает функциональность Office 365, которая будет недоступна, если IP- или URL-адреса в этом наборе конечных точек не могут быть доступны на сетевом уровне.</span><span class="sxs-lookup"><span data-stu-id="7fe72-217">notes - For optional endpoints, this text describes Office 365 functionality that will be missing if IP addresses or URLs in this endpoint set cannot be accessed at the network layer. Omitted if blank.</span></span> <span data-ttu-id="7fe72-218">Если значение не указано, опускается.</span><span class="sxs-lookup"><span data-stu-id="7fe72-218">Omitted if blank.</span></span>

### <a name="examples"></a><span data-ttu-id="7fe72-219">Примеры:</span><span class="sxs-lookup"><span data-stu-id="7fe72-219">Examples:</span></span>

<span data-ttu-id="7fe72-220">Пример 1. Запрос URI: [https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="7fe72-220">Example 1 request URI: [https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="7fe72-221">Этот URI получает все конечные точки для экземпляра Office 365 Worldwide для всех рабочих нагрузок.</span><span class="sxs-lookup"><span data-stu-id="7fe72-221">This URI obtains all endpoints for the Office 365 worldwide instance for all workloads. Example result showing an excerpt of the output:</span></span> <span data-ttu-id="7fe72-222">В примере результата показан фрагмент выходных данных:</span><span class="sxs-lookup"><span data-stu-id="7fe72-222">Example result that shows an excerpt of the output:</span></span>

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

<span data-ttu-id="7fe72-223">Обратите внимание, что полные выходные данные запроса в этом примере будут содержать другие наборы конечных точек.</span><span class="sxs-lookup"><span data-stu-id="7fe72-223">Note that the full output of the request in this example would contain other endpoint sets.</span></span>

<span data-ttu-id="7fe72-224">Пример 2. Запрос URI: [https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="7fe72-224">Example 2 request URI: [https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="7fe72-225">В этом примере получены конечные точки для экземпляра Office 365 Worldwide в отношении Exchange Online и зависимостей.</span><span class="sxs-lookup"><span data-stu-id="7fe72-225">This example obtains endpoints for the Office 365 Worldwide instance for Exchange Online and dependencies only.</span></span>

<span data-ttu-id="7fe72-226">Выходные данные в примере 2 аналогичны таковым в примере 1, но результаты не будут включать конечные точки для SharePoint Online или Skype бизнеса в Интернете.</span><span class="sxs-lookup"><span data-stu-id="7fe72-226">The output for example 2 is similar to example 1 except that the results will not include endpoints for SharePoint Online or Skype for Business Online.</span></span>

## <a name="changes-web-method"></a><span data-ttu-id="7fe72-227">Веб-метод изменений</span><span class="sxs-lookup"><span data-stu-id="7fe72-227">Changes web method</span></span>

<span data-ttu-id="7fe72-228">Веб-метод изменений возвращает самые последние опубликованные обновления. Как правило, это изменения диапазонов IP- и URL-адресов за предыдущий месяц.</span><span class="sxs-lookup"><span data-stu-id="7fe72-228">The changes web method returns the most recent updates that have been published, typically the previous month's changes to IP address ranges and URLs.</span></span>

<span data-ttu-id="7fe72-229">Наиболее критические изменения в данных конечных точек — это новые URL- и IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="7fe72-229">The most critical changes to endpoints data are new URLs and IP addresses.</span></span> <span data-ttu-id="7fe72-230">Неудачная попытка добавить IP-адрес в список управления доступом брандмауэра или добавить URL-адрес в список обхода прокси-сервера может привести к простою пользователей Office 365 за этим сетевым устройством.</span><span class="sxs-lookup"><span data-stu-id="7fe72-230">Failure to add an IP address to a firewall access control list or a URL to a proxy server bypass list can cause an outage for Office 365 users behind that network device.</span></span> <span data-ttu-id="7fe72-231">Несмотря на операционные требования, новые конечные точки публикуются в веб-службе за 30 дней до даты подготовки конечных точек к использованию, чтобы вы успели обновить списки управления доступом и списки обхода прокси-сервера.</span><span class="sxs-lookup"><span data-stu-id="7fe72-231">Notwithstanding operational requirements, new endpoints are published to the web service 30 days in advance of the date the endpoints are provisioned for use to give you time to update access control lists and proxy server bypass lists.</span></span>

<span data-ttu-id="7fe72-232">Обязательный параметр веб-метода изменений:</span><span class="sxs-lookup"><span data-stu-id="7fe72-232">The required parameter for the changes web method is:</span></span>

- <span data-ttu-id="7fe72-233">**Version=\<ГГГГММДДЧЧ>**  — обязательный параметр маршрутизации URL-адресов.</span><span class="sxs-lookup"><span data-stu-id="7fe72-233">**Version=\<YYYYMMDDNN>** - Required URL route parameter.</span></span> <span data-ttu-id="7fe72-234">Этим значением является используемая в настоящий момент версия.</span><span class="sxs-lookup"><span data-stu-id="7fe72-234">This value should be the version that you have currently implemented.</span></span> <span data-ttu-id="7fe72-235">Веб-служба возвращает изменения, внесенные с момента этой версии.</span><span class="sxs-lookup"><span data-stu-id="7fe72-235">The web service will return the changes since that version.</span></span> <span data-ttu-id="7fe72-236">Формат: _ГГГГММДДЧЧ_, где _ЧЧ_ — натуральное число, увеличивающееся, если в один день нужно опубликовать больше одной версии, при этом значение _00_ представляет первое обновление дня.</span><span class="sxs-lookup"><span data-stu-id="7fe72-236">The format is _YYYYMMDDNN_, where _NN_ is a natural number incremented if there are multiple versions required to be published on a single day, with _00_ representing the first update for a given day.</span></span> <span data-ttu-id="7fe72-237">Веб-служба требует, чтобы параметр _version_ содержал ровно 10 цифр.</span><span class="sxs-lookup"><span data-stu-id="7fe72-237">The web service requires the _version_ parameter to contain exactly 10 digits.</span></span>

<span data-ttu-id="7fe72-238">Веб-метод изменений ограничен по частоте аналогично веб-методу конечных точек.</span><span class="sxs-lookup"><span data-stu-id="7fe72-238">The changes web method is rate limited in the same way as the endpoints web method.</span></span> <span data-ttu-id="7fe72-239">Если вы получили код отклика HTTP 429, подождите 1 час перед повтором своего запроса или сгенерируйте новый GUID для запроса.</span><span class="sxs-lookup"><span data-stu-id="7fe72-239">If you receive a 429 HTTP response code, wait 1 hour before repeating your request or generate a new GUID for the request.</span></span>

<span data-ttu-id="7fe72-240">Результат веб-метода изменений — массив записей, в котором каждая запись представляет собой изменение в определенной версии конечных точек.</span><span class="sxs-lookup"><span data-stu-id="7fe72-240">The result from the changes web method is an array of records with each record representing a change in a specific version of the endpoints. The elements for each record are:</span></span> <span data-ttu-id="7fe72-241">Элементы каждой записи:</span><span class="sxs-lookup"><span data-stu-id="7fe72-241">The elements for each record are:</span></span>

- <span data-ttu-id="7fe72-242">id: неизменяемый идентификатор записи изменения.</span><span class="sxs-lookup"><span data-stu-id="7fe72-242">id - The immutable id of the change record.</span></span>
- <span data-ttu-id="7fe72-243">endpointSetId: идентификатор записи набора конечных точек, который был изменен.</span><span class="sxs-lookup"><span data-stu-id="7fe72-243">endpointSetId - The ID of the endpoint set record that is changed.</span></span>
- <span data-ttu-id="7fe72-244">disposition: описание того, как именно изменена запись набора конечных точек.</span><span class="sxs-lookup"><span data-stu-id="7fe72-244">disposition — Describes what the change did to the endpoint set record.</span></span> <span data-ttu-id="7fe72-245">Значения: _change_, _add_ или _remove_.</span><span class="sxs-lookup"><span data-stu-id="7fe72-245">Values are _change_, _add_, or _remove_.</span></span>
- <span data-ttu-id="7fe72-246">impact: не все изменения будут одинаково важны для каждой среды.</span><span class="sxs-lookup"><span data-stu-id="7fe72-246">impact — Not all changes will be equally important to every environment.</span></span> <span data-ttu-id="7fe72-247">Данный элемент описывает ожидаемое влияние на среду периметра корпоративной сети в результате этого изменения.</span><span class="sxs-lookup"><span data-stu-id="7fe72-247">This element describes the expected impact to an enterprise network perimeter environment as a result of this change.</span></span> <span data-ttu-id="7fe72-248">Этот элемент включается только в записи изменений версии **2018112800** и более поздних.</span><span class="sxs-lookup"><span data-stu-id="7fe72-248">This element is included only in change records of version **2018112800** and later.</span></span> <span data-ttu-id="7fe72-249">Доступны указанные далее варианты для элемента impact. AddedIp: IP-адрес был добавлен в Office 365 и будет доступен в службе в ближайшее время.</span><span class="sxs-lookup"><span data-stu-id="7fe72-249">Options for the impact are: — AddedIp – An IP address was added to Office 365 and will be live on the service soon.</span></span> <span data-ttu-id="7fe72-250">Этот элемент представляет изменения, которые вам необходимо внести для брандмауэра или другого устройства периметра 3 уровня сети.</span><span class="sxs-lookup"><span data-stu-id="7fe72-250">This represents a change you need to take on a proxy server or URL parsing network perimeter device.</span></span> <span data-ttu-id="7fe72-251">Если вы не добавили этот элемент перед началом его использования, могут возникать сбои.</span><span class="sxs-lookup"><span data-stu-id="7fe72-251">If you don’t add this before we start using it, you may experience an outage.</span></span>
  <span data-ttu-id="7fe72-252">AddedUrl: URL-адрес был добавлен в Office 365 и будет доступен в службе в ближайшее время.</span><span class="sxs-lookup"><span data-stu-id="7fe72-252">AddedUrl – A URL was added to Office 365 and will be live on the service soon.</span></span> <span data-ttu-id="7fe72-253">Этот элемент представляет изменения, которые вам необходимо внести для прокси-сервера или устройства периметра сети, анализирующего URL-адреса.</span><span class="sxs-lookup"><span data-stu-id="7fe72-253">This represents a change you need to take on a proxy server or URL parsing network perimeter device.</span></span> <span data-ttu-id="7fe72-254">Если вы не добавили этот URL-адрес перед началом его использования, могут возникать сбои.</span><span class="sxs-lookup"><span data-stu-id="7fe72-254">If you don’t add this before we start using it, you may experience an outage.</span></span>
  <span data-ttu-id="7fe72-255">AddedIpAndUrl: IP-адрес и URL-адрес были добавлены.</span><span class="sxs-lookup"><span data-stu-id="7fe72-255">— AddedIpAndUrl — Both an IP address and a URL were added.</span></span> <span data-ttu-id="7fe72-256">Этот элемент представляет изменение, которое вам необходимо внести на устройстве 3 уровня брандмауэра, прокси-сервере или устройстве анализа URL-адреса.</span><span class="sxs-lookup"><span data-stu-id="7fe72-256">AddedIpAndUrl - Both an IP Address and a URL were added. This represents a change you need to take on either a firewall layer 3 device or a proxy server or URL parsing device. If you don’t add this before we start using it, you may experience an outage.</span></span> <span data-ttu-id="7fe72-257">Если вы не добавили эту пару IP- и URL-адресов перед началом ее использования, могут возникать сбои.</span><span class="sxs-lookup"><span data-stu-id="7fe72-257">If you don’t add this before we start using it, you may experience an outage.</span></span>
  <span data-ttu-id="7fe72-258">RemovedIpOrUrl: минимум один IP- или URL-адрес удален из Office 365.</span><span class="sxs-lookup"><span data-stu-id="7fe72-258">— RemovedIpOrUrl – At least one IP address or URL was removed from Office 365.</span></span> <span data-ttu-id="7fe72-259">Удалите конечные точки сети со своих устройств периметра, но четкого срока, когда вы должны это сделать, не установлено.</span><span class="sxs-lookup"><span data-stu-id="7fe72-259">RemovedIpOrUrl – At least one IP Address or URL was removed from Office 365. You should remove the network endpoints from your perimeter devices, but there’s no deadline for you to do this.</span></span>
  <span data-ttu-id="7fe72-260">ChangedIsExpressRoute: изменен атрибут поддержки ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="7fe72-260">— ChangedIsExpressRoute – The ExpressRoute support attribute was changed.</span></span> <span data-ttu-id="7fe72-261">Если вы используете ExpressRoute, может потребоваться выполнить определенные действия в зависимости от вашей конфигурации.</span><span class="sxs-lookup"><span data-stu-id="7fe72-261">ChangedIsExpressRoute – The ExpressRoute support attribute was changed. If you use ExpressRoute then you may need to take action depending on your configuration.</span></span>
  <span data-ttu-id="7fe72-262">MovedIpOrUrl: мы перенесли IP-адрес или URL-адрес в другой набор конечных точек.</span><span class="sxs-lookup"><span data-stu-id="7fe72-262">MovedIpOrUrl – We moved an IP Address or Url between this endpoint set and another one. Generally no action is required.</span></span> <span data-ttu-id="7fe72-263">Как правило, никаких дополнительных действий не требуется.</span><span class="sxs-lookup"><span data-stu-id="7fe72-263">Generally no action is required.</span></span>
  <span data-ttu-id="7fe72-264">RemovedDuplicateIpOrUrl: мы удалили повторяющийся IP- или URL-адрес, но он по-прежнему опубликован для Office 365.</span><span class="sxs-lookup"><span data-stu-id="7fe72-264">RemovedDuplicateIpOrUrl – We removed a duplicate IP Address or Url but it’s still published for Office 365. Generally no action is required.</span></span> <span data-ttu-id="7fe72-265">Как правило, никаких дополнительных действий не требуется.</span><span class="sxs-lookup"><span data-stu-id="7fe72-265">Generally no action is required.</span></span>
  <span data-ttu-id="7fe72-266">OtherNonPriorityChanges: мы изменили что-то менее критическое, чем все прочие параметры (например, содержимое поля заметки).</span><span class="sxs-lookup"><span data-stu-id="7fe72-266">OtherNonPriorityChanges – We changed something less critical than all of the other options like a note field</span></span>
- <span data-ttu-id="7fe72-267">version — версия опубликованного набора конечных точек, в который внесено изменение.</span><span class="sxs-lookup"><span data-stu-id="7fe72-267">version — The version of the published endpoint set in which the change was introduced.</span></span> <span data-ttu-id="7fe72-268">Формат номеров версий: _ГГГГММДДЧЧ_, где _ЧЧ_ — натуральное число, увеличивающееся, если в один день нужно опубликовать больше одной версии.</span><span class="sxs-lookup"><span data-stu-id="7fe72-268">version - The version of the published endpoint set in which the change was introduced. Version numbers are of the format _YYYYMMDDNN_, where NN is a natural number incremented if there are multiple versions required to be published on a single day.</span></span>
- <span data-ttu-id="7fe72-269">previous — подструктура с подробным указанием предыдущих значений измененных элементов в наборе конечных точек.</span><span class="sxs-lookup"><span data-stu-id="7fe72-269">previous - A substructure detailing previous values of changed elements on the endpoint set.</span></span> <span data-ttu-id="7fe72-270">Не будет включена для новых добавляемых наборов конечных точек.</span><span class="sxs-lookup"><span data-stu-id="7fe72-270">This will not be included for newly added endpoint sets.</span></span> <span data-ttu-id="7fe72-271">Включает _ExpressRoute_, _serviceArea_, _category_, _required_, _tcpPorts_, _udpPorts_ и _notes_.</span><span class="sxs-lookup"><span data-stu-id="7fe72-271">Includes  _ExpressRoute_, _serviceArea_, _category_, _required_, _tcpPorts_, _udpPorts_, and _notes_.</span></span>
- <span data-ttu-id="7fe72-272">current — подструктура с подробным указанием обновленных значений измененных элементов в наборе конечных точек.</span><span class="sxs-lookup"><span data-stu-id="7fe72-272">current - A substructure detailing updated values of changes elements on the endpoint set.</span></span> <span data-ttu-id="7fe72-273">Включает _ExpressRoute_, _serviceArea_, _category_, _required_, _tcpPorts_, _udpPorts_ и _notes_.</span><span class="sxs-lookup"><span data-stu-id="7fe72-273">Includes _ExpressRoute_, _serviceArea_, _category_, _required_, _tcpPorts_, _udpPorts_, and _notes_.</span></span>
- <span data-ttu-id="7fe72-274">add — подструктура с подробным указанием элементов, добавляемых в коллекции наборов конечных точек.</span><span class="sxs-lookup"><span data-stu-id="7fe72-274">add - A substructure detailing items to be added to endpoint set collections. Omitted if there are no additions.</span></span> <span data-ttu-id="7fe72-275">Опускается, если добавлений нет.</span><span class="sxs-lookup"><span data-stu-id="7fe72-275">Omitted if there are no removals.</span></span>
  <span data-ttu-id="7fe72-276">effectiveDate определяет дату начала использования добавлений в службе.</span><span class="sxs-lookup"><span data-stu-id="7fe72-276">effectiveDate - Defines the data when the additions will be live in the service.</span></span>
  <span data-ttu-id="7fe72-277">ips — элементы, добавляемые в массив _ips_.</span><span class="sxs-lookup"><span data-stu-id="7fe72-277">ips - Items to be added to the _ips_ array.</span></span>
  <span data-ttu-id="7fe72-278">urls — элементы, добавляемые в массив _urls_.</span><span class="sxs-lookup"><span data-stu-id="7fe72-278">urls- Items to be added to the _urls_ array.</span></span>
- <span data-ttu-id="7fe72-279">remove — подструктура с подробным указанием элементов, удаляемых из набора конечных точек.</span><span class="sxs-lookup"><span data-stu-id="7fe72-279">remove - A substructure detailing items to be removed from the endpoint set.</span></span> <span data-ttu-id="7fe72-280">Опускается, если удаленных элементов нет.</span><span class="sxs-lookup"><span data-stu-id="7fe72-280">Omitted if there are no removals.</span></span>
  <span data-ttu-id="7fe72-281">ips — элементы, удаляемые из массива _ips_.</span><span class="sxs-lookup"><span data-stu-id="7fe72-281">ips - Items to be removed from the _ips_ array.</span></span>
  <span data-ttu-id="7fe72-282">urls — элементы, удаляемые из массива _urls_.</span><span class="sxs-lookup"><span data-stu-id="7fe72-282">urls- Items to be removed from the _urls_ array.</span></span>

### <a name="examples"></a><span data-ttu-id="7fe72-283">Примеры:</span><span class="sxs-lookup"><span data-stu-id="7fe72-283">Examples:</span></span>

<span data-ttu-id="7fe72-284">Пример 1. Запрос URI: [https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="7fe72-284">Example 1 request URI: [https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="7fe72-p144">Запрашивает все предыдущие изменения в экземпляре службы Office 365 Worldwide. Пример результата:</span><span class="sxs-lookup"><span data-stu-id="7fe72-p144">This requests all previous changes to the Office 365 worldwide service instance. Example result:</span></span>

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

<span data-ttu-id="7fe72-287">Пример 2. Запрос URI: [https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="7fe72-287">Example 2 request URI: [https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="7fe72-p145">Запрашивает изменения, внесенные в экземпляр Office 365 Worldwide после выхода указанной версии. В этом случае указанная версия является последней. Пример результата:</span><span class="sxs-lookup"><span data-stu-id="7fe72-p145">This requests changes since the specified version to the Office 365 Worldwide instance. In this case, the version specified is the latest. Example result:</span></span>

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

## <a name="example-powershell-script"></a><span data-ttu-id="7fe72-291">Пример скрипта PowerShell</span><span class="sxs-lookup"><span data-stu-id="7fe72-291">Example PowerShell Script</span></span>

<span data-ttu-id="7fe72-292">Этот скрипт PowerShell позволяет узнать, нужно ли выполнить действия для обновленных данных.</span><span class="sxs-lookup"><span data-stu-id="7fe72-292">Here is a PowerShell script that you can run to see if there are actions you need to take for updated data.</span></span> <span data-ttu-id="7fe72-293">Этот скрипт можно запустить в качестве запланированной задачи, чтобы проверить наличие обновления версии.</span><span class="sxs-lookup"><span data-stu-id="7fe72-293">You can run this script as a scheduled task to check for a version update.</span></span> <span data-ttu-id="7fe72-294">Чтобы избежать чрезмерной нагрузки на веб-службу, не запускайте этот скрипт чаще одного раза в час.</span><span class="sxs-lookup"><span data-stu-id="7fe72-294">To avoid excessive load on the web service, try not to run the script more than once an hour.</span></span>

<span data-ttu-id="7fe72-295">Этот скрипт выполняет следующее:</span><span class="sxs-lookup"><span data-stu-id="7fe72-295">The ExchUcUtil.ps1 script does the following:</span></span>

- <span data-ttu-id="7fe72-296">Проверяет номер версии текущих конечных точек экземпляра Office 365 Worldwide, вызывая API REST веб-службы.</span><span class="sxs-lookup"><span data-stu-id="7fe72-296">Checks the version number of the current Office 365 Worldwide instance endpoints by calling the web service REST API.</span></span>
- <span data-ttu-id="7fe72-297">Проверяет наличие текущего файла версии по адресу _$Env:TEMP\O365_endpoints_latestversion.txt_.</span><span class="sxs-lookup"><span data-stu-id="7fe72-297">Checks for a current version file at _$Env:TEMP\O365_endpoints_latestversion.txt_.</span></span> <span data-ttu-id="7fe72-298">Как правило, путь для глобальной переменной **$Env:TEMP** — _C:\Users\\<username\>\AppData\Local\Temp_.</span><span class="sxs-lookup"><span data-stu-id="7fe72-298">The path of the global variable **$Env:TEMP** is usually _C:\Users\\<username\>\AppData\Local\Temp_.</span></span>
- <span data-ttu-id="7fe72-299">Если этот скрипт выполняется впервые, он возвращает текущую версию и все текущие IP- и URL-адреса, записывает версию конечных точек в файл _$Env:TEMP\O365_endpoints_latestversion.txt_, а выходные данные конечных точек — в файл _$Env:TEMP\O365_endpoints_data.txt_.</span><span class="sxs-lookup"><span data-stu-id="7fe72-299">If this is the first time the script has been run, the script returns the current version and all current IP addresses and URLs, writes the endpoints version to the file _$Env:TEMP\O365_endpoints_latestversion.txt_ and the endpoints data output to the file _$Env:TEMP\O365_endpoints_data.txt_.</span></span> <span data-ttu-id="7fe72-300">Вы можете изменить путь и/или имя выходного файла, изменив следующие строки:</span><span class="sxs-lookup"><span data-stu-id="7fe72-300">You can modify the path and/or name of the output file by editing these lines:</span></span>

    ``` powershell
    $versionpath = $Env:TEMP + "\O365_endpoints_latestversion.txt"
    $datapath = $Env:TEMP + "\O365_endpoints_data.txt"
    ```

- <span data-ttu-id="7fe72-301">Если при каждом последующем выполнении скрипта последняя версия веб-службы идентична версии в файле _O365_endpoints_latestversion.txt_, скрипт завершает работу, не внося каких-либо изменений.</span><span class="sxs-lookup"><span data-stu-id="7fe72-301">On each subsequent execution of the script, if the latest web service version is identical to the version in the _O365_endpoints_latestversion.txt_ file, the script exits without making any changes.</span></span>
- <span data-ttu-id="7fe72-302">Если последняя версия веб-службы новее версии в файле _O365_endpoints_latestversion.txt_, скрипт возвращает конечные точки и фильтры для конечных точек категорий **Allow** и **Optimize**, обновляет версию в файле _O365_endpoints_latestversion.txt_ и записывает обновленные данные в файл _O365_endpoints_data.txt_.</span><span class="sxs-lookup"><span data-stu-id="7fe72-302">When the latest web service version is newer than the version in the _O365_endpoints_latestversion.txt_ file, the script returns the endpoints and filters for the **Allow** and **Optimize** category endpoints, updates the version in the _O365_endpoints_latestversion.txt_ file, and writes the updated data to the _O365_endpoints_data.txt_ file.</span></span>

<span data-ttu-id="7fe72-303">Скрипт создает уникальный _ClientRequestId_ для компьютера, на котором выполняется, и повторно использует этот идентификатор для нескольких вызовов.</span><span class="sxs-lookup"><span data-stu-id="7fe72-303">The script generates a unique _ClientRequestId_ for the computer it is executed on, and reuses this ID across multiple calls.</span></span> <span data-ttu-id="7fe72-304">Этот идентификатор хранится в файле _O365_endpoints_latestversion.txt_.</span><span class="sxs-lookup"><span data-stu-id="7fe72-304">This ID is stored in the _O365_endpoints_latestversion.txt_ file.</span></span>

### <a name="to-run-the-powershell-script"></a><span data-ttu-id="7fe72-305">Запуск скрипта PowerShell</span><span class="sxs-lookup"><span data-stu-id="7fe72-305">To run the ExchUCUtil Windows PowerShell script</span></span>

1. <span data-ttu-id="7fe72-306">Скопируйте скрипт и сохраните его на локальном жестком диске или в папке со скриптами под именем _Get-O365WebServiceUpdates.ps1_.</span><span class="sxs-lookup"><span data-stu-id="7fe72-306">Copy the script and save it to your local hard drive or script location as _Get-O365WebServiceUpdates.ps1_.</span></span>
1. <span data-ttu-id="7fe72-307">Выполните скрипт в предпочитаемом редакторе скриптов, например VS Code или интегрированной среде сценариев PowerShell, или из консоли PowerShell с помощью следующей команды:</span><span class="sxs-lookup"><span data-stu-id="7fe72-307">Execute the script in your preferred script editor such as the PowerShell ISE or VS Code, or from a PowerShell console using the following command:</span></span>

    ``` powershell
   powershell.exe -file <path>\Get-O365WebServiceUpdates.ps1
    ```

    <span data-ttu-id="7fe72-308">Отсутствуют параметры для передачи в скрипт.</span><span class="sxs-lookup"><span data-stu-id="7fe72-308">There are no parameters to pass to the script.</span></span>

```powershell
<# Get-O365WebServiceUpdates.ps1
From https://aka.ms/ipurlws
v1.1 8/6/2019

DESCRIPTION
This script calls the REST API of the Office 365 IP and URL Web Service (Worldwide instance)
and checks to see if there has been a new update since the version stored in an existing
$Env:TEMP\O365_endpoints_latestversion.txt file in your user directory's temp folder
(usually C:\Users\<username>\AppData\Local\Temp).
If the file doesn't exist, or the latest version is newer than the current version in the
file, the script returns IPs and/or URLs that have been changed, added or removed in the latest
update and writes the new version and data to the output file $Env:TEMP\O365_endpoints_data.txt.

USAGE
Run as a scheduled task every 60 minutes.

PARAMETERS
n/a

PREREQUISITES
PS script execution policy: Bypass
PowerShell 3.0 or later
Does not require elevation
#>

#Requires -Version 3.0

# web service root URL
$ws = "https://endpoints.office.com"
# path where output files will be stored
$versionpath = $Env:TEMP + "\O365_endpoints_latestversion.txt"
$datapath = $Env:TEMP + "\O365_endpoints_data.txt"

# fetch client ID and version if version file exists; otherwise create new file and client ID
if (Test-Path $versionpath) {
    $content = Get-Content $versionpath
    $clientRequestId = $content[0]
    $lastVersion = $content[1]
    Write-Output ("Version file exists! Current version: " + $lastVersion)
}
else {
    Write-Output ("First run! Creating version file at " + $versionpath + ".")
    $clientRequestId = [GUID]::NewGuid().Guid
    $lastVersion = "0000000000"
    @($clientRequestId, $lastVersion) | Out-File $versionpath
}

# call version method to check the latest version, and pull new data if version number is different
$version = Invoke-RestMethod -Uri ($ws + "/version/Worldwide?clientRequestId=" + $clientRequestId)
if ($version.latest -gt $lastVersion) {
    Write-Host "New version of Office 365 worldwide commercial service instance endpoints detected"
    # write the new version number to the version file
    @($clientRequestId, $version.latest) | Out-File $versionpath
    # invoke endpoints method to get the new data
    $endpointSets = Invoke-RestMethod -Uri ($ws + "/endpoints/Worldwide?clientRequestId=" + $clientRequestId)
    # filter results for Allow and Optimize endpoints, and transform these into custom objects with port and category
    # URL results
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
    # IPv4 results
    $flatIp4s = $endpointSets | ForEach-Object {
        $endpointSet = $_
        $ips = $(if ($endpointSet.ips.Count -gt 0) { $endpointSet.ips } else { @() })
        # IPv4 strings contain dots
        $ip4s = $ips | Where-Object { $_ -like '*.*' }
        $ip4CustomObjects = @()
        if ($endpointSet.category -in ("Allow", "Optimize")) {
            $ip4CustomObjects = $ip4s | ForEach-Object {
                [PSCustomObject]@{
                    category = $endpointSet.category;
                    ip = $_;
                    tcpPorts = $endpointSet.tcpPorts;
                    udpPorts = $endpointSet.udpPorts;
                }
            }
        }
        $ip4CustomObjects
    }
    # IPv6 results
    $flatIp6s = $endpointSets | ForEach-Object {
        $endpointSet = $_
        $ips = $(if ($endpointSet.ips.Count -gt 0) { $endpointSet.ips } else { @() })
        # IPv6 strings contain colons
        $ip6s = $ips | Where-Object { $_ -like '*:*' }
        $ip6CustomObjects = @()
        if ($endpointSet.category -in ("Optimize")) {
            $ip6CustomObjects = $ip6s | ForEach-Object {
                [PSCustomObject]@{
                    category = $endpointSet.category;
                    ip = $_;
                    tcpPorts = $endpointSet.tcpPorts;
                    udpPorts = $endpointSet.udpPorts;
                }
            }
        }
        $ip6CustomObjects
    }

    # write output to screen
    Write-Output ("Client Request ID: " + $clientRequestId)
    Write-Output ("Last Version: " + $lastVersion)
    Write-Output ("New Version: " + $version.latest)
    Write-Output ""
    Write-Output "IPv4 Firewall IP Address Ranges"
    ($flatIp4s.ip | Sort-Object -Unique) -join "," | Out-String
    Write-Output "IPv6 Firewall IP Address Ranges"
    ($flatIp6s.ip | Sort-Object -Unique) -join "," | Out-String
    Write-Output "URLs for Proxy Server"
    ($flatUrls.url | Sort-Object -Unique) -join "," | Out-String
    Write-Output ("IP and URL data written to " + $datapath)

    # write output to data file
    Write-Output "Office 365 IP and UL Web Service data" | Out-File $datapath
    Write-Output "Worldwide instance" | Out-File $datapath -Append
    Write-Output "" | Out-File $datapath -Append
    Write-Output ("Version: " + $version.latest) | Out-File $datapath -Append
    Write-Output "" | Out-File $datapath -Append
    Write-Output "IPv4 Firewall IP Address Ranges" | Out-File $datapath -Append
    ($flatIp4s.ip | Sort-Object -Unique) -join "," | Out-File $datapath -Append
    Write-Output "" | Out-File $datapath -Append
    Write-Output "IPv6 Firewall IP Address Ranges" | Out-File $datapath -Append
    ($flatIp6s.ip | Sort-Object -Unique) -join "," | Out-File $datapath -Append
    Write-Output "" | Out-File $datapath -Append
    Write-Output "URLs for Proxy Server" | Out-File $datapath -Append
    ($flatUrls.url | Sort-Object -Unique) -join "," | Out-File $datapath -Append
}
else {
    Write-Host "Office 365 worldwide commercial service instance endpoints are up-to-date."
}
```

## <a name="example-python-script"></a><span data-ttu-id="7fe72-309">Пример скрипта на Python</span><span class="sxs-lookup"><span data-stu-id="7fe72-309">Example Python Script</span></span>

<span data-ttu-id="7fe72-p150">Ниже показан скрипт на Python, протестированный с использованием Python 3.6.3 на Windows 10. Он позволяет узнать, нужно ли выполнить действия для обновленных данных, проверяя номер версии для конечных точек экземпляра Office 365 Worldwide. Если изменение есть, скрипт скачивает конечные точки и фильтрует результаты для категорий _Allow_ и _Optimize_. Он также использует уникальный ClientRequestId для нескольких вызовов и сохраняет последнюю версию, обнаруженную во временном файле. Вам нужно вызывать этот скрипт раз в час для проверки наличия обновления версии.</span><span class="sxs-lookup"><span data-stu-id="7fe72-p150">Here is a Python script, tested with Python 3.6.3 on Windows 10, that you can run to see if there are actions you need to take for updated data. This script checks the version number for the Office 365 Worldwide instance endpoints. When there is a change, it downloads the endpoints and filters for the _Allow_ and _Optimize_ category endpoints. It also uses a unique ClientRequestId across multiple calls and saves the latest version found in a temporary file. You should call this script once an hour to check for a version update.</span></span>

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

## <a name="web-service-interface-versioning"></a><span data-ttu-id="7fe72-315">Управление версиями интерфейса веб-службы</span><span class="sxs-lookup"><span data-stu-id="7fe72-315">Web Service interface versioning</span></span>

<span data-ttu-id="7fe72-316">В будущем могут понадобиться обновления параметров или результатов для этих методов веб-служб.</span><span class="sxs-lookup"><span data-stu-id="7fe72-316">Updates to the parameters or results for these web service methods may be required in the future.</span></span> <span data-ttu-id="7fe72-317">После публикации общедоступной версии веб-служб корпорация Майкрософт примет разумные меры для заблаговременного уведомления о существенных обновлениях веб-службы.</span><span class="sxs-lookup"><span data-stu-id="7fe72-317">After the general availability version of these web services is published, Microsoft will make reasonable efforts to provide advance notice of material updates to the web service.</span></span> <span data-ttu-id="7fe72-318">Если корпорация Майкрософт сочтет, что обновление потребует изменений клиентов, использующих веб-службы, она сохранит доступ к предыдущей версии веб-службы в течение как минимум 12 месяцев после выпуска новой версии.</span><span class="sxs-lookup"><span data-stu-id="7fe72-318">When Microsoft believes that an update will require changes to clients using the web service, Microsoft will keep the previous version (one version back) of the web service available for at least 12 months after the release of the new version.</span></span> <span data-ttu-id="7fe72-319">Пользователи, которые не выполнят обновление в течение этого времени, могут лишиться доступа к веб-службе и ее методам.</span><span class="sxs-lookup"><span data-stu-id="7fe72-319">Customers who do not upgrade during that time may be unable to access the web service and its methods.</span></span> <span data-ttu-id="7fe72-320">Пользователи должны убедиться, что клиенты веб-службы продолжат работать без ошибок, если такие изменения будут внесены в подпись интерфейса веб-службы:</span><span class="sxs-lookup"><span data-stu-id="7fe72-320">Customers must ensure that clients of the web service continue working without error if the following changes are made to the web service interface signature:</span></span>

- <span data-ttu-id="7fe72-321">Добавление нового необязательного параметра к существующему веб-методу, который необязательно должны предоставлять старые клиенты и который не влияет на результат, получаемый старым клиентом.</span><span class="sxs-lookup"><span data-stu-id="7fe72-321">Adding a new optional parameter to an existing web method that doesn't have to be provided by older clients and doesn't impact the result an older client receives.</span></span>
- <span data-ttu-id="7fe72-322">Добавление нового именованного атрибута в один из элементов REST отклика или дополнительных столбцов в файл CSV отклика.</span><span class="sxs-lookup"><span data-stu-id="7fe72-322">Adding a new named attribute in one of the response REST items or additional columns to the response CSV.</span></span>
- <span data-ttu-id="7fe72-323">Добавление нового веб-метода с новым именем, который не вызывается старыми клиентами.</span><span class="sxs-lookup"><span data-stu-id="7fe72-323">Adding a new web method with a new name that is not called by the older clients.</span></span>

## <a name="update-notifications"></a><span data-ttu-id="7fe72-324">Уведомления об обновлениях</span><span class="sxs-lookup"><span data-stu-id="7fe72-324">Update notifications</span></span>

<span data-ttu-id="7fe72-325">Вы можете использовать несколько различных методов, чтобы получать по электронной почте уведомления о публикации изменений IP- и URL-адресов в веб-службе.</span><span class="sxs-lookup"><span data-stu-id="7fe72-325">You can use a few different methods to get email notifications when changes to the IP addresses and URLs are published to the web service.</span></span>

- <span data-ttu-id="7fe72-326">Сведения о решении Microsoft Flow см. в статье [Использование Microsoft Flow для получения электронных сообщений об изменениях URL-адресов и IP-адресов Office 365](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/m-p/240651).</span><span class="sxs-lookup"><span data-stu-id="7fe72-326">To use a Microsoft Flow solution, see [Use Microsoft Flow to receive an email for changes to Office 365 IP Addresses and URLs](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/m-p/240651).</span></span>
- <span data-ttu-id="7fe72-327">Сведения о развертывании Azure Logic App с помощью шаблона ARM см. на странице [Уведомление об обновлении Office 365 (версия 1.1)](https://aka.ms/ipurlws-updates-template).</span><span class="sxs-lookup"><span data-stu-id="7fe72-327">To deploy an Azure Logic App using an ARM template, see [Office 365 Update Notification (v1.1)](https://aka.ms/ipurlws-updates-template).</span></span>
- <span data-ttu-id="7fe72-328">Сведения о записи собственного скрипта уведомлений с помощью PowerShell см. в статье [Send-MailMessage](https://docs.microsoft.com/ru-RU/powershell/module/microsoft.powershell.utility/send-mailmessage).</span><span class="sxs-lookup"><span data-stu-id="7fe72-328">To write your own notification script using PowerShell, see [Send-MailMessage](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/send-mailmessage).</span></span>

## <a name="exporting-a-proxy-pac-file"></a><span data-ttu-id="7fe72-329">Экспорт PAC-файла прокси-сервера</span><span class="sxs-lookup"><span data-stu-id="7fe72-329">Exporting a Proxy PAC file</span></span>

<span data-ttu-id="7fe72-330">[Get-PacFile](https://www.powershellgallery.com/packages/Get-PacFile) — это скрипт PowerShell, который считывает последние конечные точки сети из IP-адреса и веб-службы URL-адресов Office 365 и создает пример PAC-файла.</span><span class="sxs-lookup"><span data-stu-id="7fe72-330">[Get-PacFile](https://www.powershellgallery.com/packages/Get-PacFile) is a PowerShell script that reads the latest network endpoints from the Office 365 IP Address and URL web service and creates a sample PAC file.</span></span> <span data-ttu-id="7fe72-331">Сведения об использовании этого скрипта см. в статье [Использование PAC-файла для прямой маршрутизации обязательного трафика Office 365](managing-office-365-endpoints.md#use-a-pac-file-for-direct-routing-of-vital-office-365-traffic).</span><span class="sxs-lookup"><span data-stu-id="7fe72-331">For information on using Get-PacFile, see [Use a PAC file for direct routing of vital Office 365 traffic](managing-office-365-endpoints.md#use-a-pac-file-for-direct-routing-of-vital-office-365-traffic).</span></span>

## <a name="related-topics"></a><span data-ttu-id="7fe72-332">Статьи по теме</span><span class="sxs-lookup"><span data-stu-id="7fe72-332">Related Topics</span></span>
  
[<span data-ttu-id="7fe72-333">URL-адреса и диапазоны IP-адресов для Office 365</span><span class="sxs-lookup"><span data-stu-id="7fe72-333">Office 365 URLs and IP address ranges</span></span>](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)

[<span data-ttu-id="7fe72-334">Управление конечными точками Office 365</span><span class="sxs-lookup"><span data-stu-id="7fe72-334">Managing Office 365 endpoints</span></span>](managing-office-365-endpoints.md)
  
[<span data-ttu-id="7fe72-335">Вопросы и ответы о конечных точках Office 365</span><span class="sxs-lookup"><span data-stu-id="7fe72-335">Office 365 endpoints FAQ</span></span>](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)

[<span data-ttu-id="7fe72-336">Принципы сетевого подключения к Office 365</span><span class="sxs-lookup"><span data-stu-id="7fe72-336">Office 365 Network Connectivity Principles</span></span>](office-365-network-connectivity-principles.md)

[<span data-ttu-id="7fe72-337">Сеть Office 365 и настройка производительности</span><span class="sxs-lookup"><span data-stu-id="7fe72-337">Office 365 network and performance tuning</span></span>](network-planning-and-performance.md)

[<span data-ttu-id="7fe72-338">Оценка сетевого подключения к Office 365</span><span class="sxs-lookup"><span data-stu-id="7fe72-338">Office 365 network connectivity principles</span></span>](assessing-network-connectivity.md)
  
[<span data-ttu-id="7fe72-339">Качество мультимедиа и характеристики сетевого подключения в случае Skype для бизнеса Online</span><span class="sxs-lookup"><span data-stu-id="7fe72-339">Media Quality and Network Connectivity Performance in Skype for Business Online</span></span>](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[<span data-ttu-id="7fe72-340">Оптимизация сети для Skype для бизнеса Online</span><span class="sxs-lookup"><span data-stu-id="7fe72-340">Optimizing your network for Skype for Business Online</span></span>](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)

[<span data-ttu-id="7fe72-341">Настройка производительности Office 365 с помощью базовых показателей и журнала производительности</span><span class="sxs-lookup"><span data-stu-id="7fe72-341">Office 365 performance tuning using baselines and performance history</span></span>](performance-tuning-using-baselines-and-history.md)
  
[<span data-ttu-id="7fe72-342">План устранения проблем с производительностью Office 365</span><span class="sxs-lookup"><span data-stu-id="7fe72-342">Performance troubleshooting plan for Office 365</span></span>](performance-troubleshooting-plan.md)
