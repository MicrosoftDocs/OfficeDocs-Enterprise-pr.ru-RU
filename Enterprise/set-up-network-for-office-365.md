---
title: Настройка сети для Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/01/2018
ms.audience: ITPro
ms.topic: hub-page
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: ''
description: Сводка. Статьи с общими сведениями об организации сети для Office 365.
ms.openlocfilehash: b86d4afaf204cfdd22cb4ca7c85608b384ca431a
ms.sourcegitcommit: eb52922c0ee34791fd71ae78338ab203f7761eec
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/28/2019
ms.locfileid: "30341920"
---
# <a name="set-up-your-network-for-office-365"></a><span data-ttu-id="694f2-103">Настройка сети для Office 365</span><span class="sxs-lookup"><span data-stu-id="694f2-103">Set up your network for Office 365</span></span>

<span data-ttu-id="694f2-104">**Сводка.** Статьи с общими сведениями об организации сети для Office 365.</span><span class="sxs-lookup"><span data-stu-id="694f2-104">**Summary:** See these articles to understand networking for Office 365.</span></span>
  
<span data-ttu-id="694f2-p101">Важной частью миграции на Office 365 является обеспечение настройки сети и подключений к Интернету для оптимизации доступа. Настройка локальной сети для доступа к глобально распределенным облачным предложениям программного обеспечения как услуги (SaaS) отличается от традиционной сети, оптимизированной для трафика к локальным центрам обработки данных.</span><span class="sxs-lookup"><span data-stu-id="694f2-p101">An important part of your Office 365 onboarding is to first ensure that your network and Internet connections are set up for optimized access. Configuring your on-premises network to access a globally distributed Software-as-a-Service (SaaS) cloud is different from a traditional network that is optimized for traffic to on-premises datacenters.</span></span> 

<span data-ttu-id="694f2-107">С помощью этих статей можно ознакомиться с основными различиями пограничных устройств, клиентских компьютеров и локальной сети, а также изменять их для обеспечения оптимальной производительности.</span><span class="sxs-lookup"><span data-stu-id="694f2-107">Use these articles to understand the key differences and to modify your  edge devices, client computers, and on-premises network to get the best user performance.</span></span>

## <a name="how-office-365-networking-works"></a><span data-ttu-id="694f2-108">Как выполняется организация сети Office 365</span><span class="sxs-lookup"><span data-stu-id="694f2-108">How Office 365 networking works</span></span>

<span data-ttu-id="694f2-109">В указанных ниже статьях рассматриваются возможности подключения для Office 365.</span><span class="sxs-lookup"><span data-stu-id="694f2-109">See these articles for an overview of connectivity for Office 365:</span></span>

- [<span data-ttu-id="694f2-110">Обзор возможности сетевого подключения к Office 365</span><span class="sxs-lookup"><span data-stu-id="694f2-110">Office 365 networking connectivity overview</span></span>](office-365-networking-overview.md)
- [<span data-ttu-id="694f2-111">Принципы сетевого подключения к Office 365</span><span class="sxs-lookup"><span data-stu-id="694f2-111">Office 365 network connectivity principles</span></span>](office-365-network-connectivity-principles.md)
- [<span data-ttu-id="694f2-112">Сетевое подключение к Office 365</span><span class="sxs-lookup"><span data-stu-id="694f2-112">Network connectivity to Office 365</span></span>](network-connectivity.md)

<span data-ttu-id="694f2-113">Советы по повышению производительности см. в статье [Планирование сети и настройка производительности для Office 365](network-planning-and-performance.md).</span><span class="sxs-lookup"><span data-stu-id="694f2-113">For advice on enhancing performance, see [Network planning and performance tuning for Office 365](network-planning-and-performance.md).</span></span>

## <a name="support-office-365-networking-as-a-network-equipment-vendor"></a><span data-ttu-id="694f2-114">Поддержка организации сети Office 365 поставщиком сетевого оборудования</span><span class="sxs-lookup"><span data-stu-id="694f2-114">Support Office 365 networking as a network equipment vendor</span></span>

<span data-ttu-id="694f2-p102">Если вы являетесь поставщиком сетевого оборудования, присоединяйтесь к [партнерской программе Office 365 для поставщиков сетевых устройств и служб](office-365-networking-partner-program.md). Зарегистрируйтесь в программе, чтобы встроить принципы сетевого подключения к Office 365 в свои продукты и решения.</span><span class="sxs-lookup"><span data-stu-id="694f2-p102">If you are a network equipment vendor, join the [Office 365 Networking Partner Program](office-365-networking-partner-program.md). Enroll in the program to build Office 365 network connectivity principles into your products and solutions.</span></span> 

## <a name="office-365-endpoints"></a><span data-ttu-id="694f2-117">Конечные точки Office 365</span><span class="sxs-lookup"><span data-stu-id="694f2-117">Office 365 endpoints</span></span>

<span data-ttu-id="694f2-118">Конечные точки — это набор конечных IP-адресов, доменных имен DNS и URL-адресов для трафика Office 365 в Интернете.</span><span class="sxs-lookup"><span data-stu-id="694f2-118">Endpoints are the set of destination IP addresses, DNS domain names, and URLs for Office 365 traffic on the Internet.</span></span> 

<span data-ttu-id="694f2-p103">Чтобы повысить производительность облачных служб Office 365, этим конечным точкам требуется специальная обработка клиентскими браузерами и устройствами в сети периметра. К этим устройствам относятся брандмауэры, устройства расшифровки и анализа SSL-трафика, устройства анализа пакетов и системы защиты от потери данных.</span><span class="sxs-lookup"><span data-stu-id="694f2-p103">To optimize performance to Office 365 cloud-based services, these endpoints need special handling by your client browsers and the devices in your edge network. These devices include firewalls, SSL Break and Inspect and packet inspection devices, and data loss prevention systems.</span></span>

<span data-ttu-id="694f2-121">Подробные сведения см. в статье [Управление конечными точками Office 365](managing-office-365-endpoints.md).</span><span class="sxs-lookup"><span data-stu-id="694f2-121">See [Managing Office 365 endpoints](managing-office-365-endpoints.md) for the details.</span></span>

<span data-ttu-id="694f2-p104">В настоящее время существует пять разных облаков Office 365. Эта таблица позволяет перейти к списку конечных точек для каждого из них.</span><span class="sxs-lookup"><span data-stu-id="694f2-p104">There are currently five different Office 365 clouds. This table takes you to the list of endpoints for each one.</span></span>

|||
|:-------|:-----|
| [<span data-ttu-id="694f2-124">Глобальные конечные точки</span><span class="sxs-lookup"><span data-stu-id="694f2-124">Worldwide endpoints</span></span>](urls-and-ip-address-ranges.md) | <span data-ttu-id="694f2-125">Конечные точки для подписок на Office 365 во всем мире, которые включают облако сообщества государственных организаций США (GCC).</span><span class="sxs-lookup"><span data-stu-id="694f2-125">The endpoints for worldwide Office 365 subscriptions, which include the United States Government Community Cloud (GCC).</span></span> |
| [<span data-ttu-id="694f2-126">Конечные точки U.S. Government DoD</span><span class="sxs-lookup"><span data-stu-id="694f2-126">U.S. Government DoD endpoints</span></span>](office-365-u-s-government-dod-endpoints.md) | <span data-ttu-id="694f2-127">Конечные точки для подписок Министерства обороны США (DoD).</span><span class="sxs-lookup"><span data-stu-id="694f2-127">The endpoints for United States Department of Defense (DoD) subscriptions.</span></span> |
| [<span data-ttu-id="694f2-128">Конечные точки U.S. Government GCC High</span><span class="sxs-lookup"><span data-stu-id="694f2-128">U.S. Government GCC High endpoints</span></span>](office-365-u-s-government-gcc-high-endpoints.md) | <span data-ttu-id="694f2-129">Конечные точки для подписок GCC High государственных организаций США.</span><span class="sxs-lookup"><span data-stu-id="694f2-129">The endpoints for United States Government Community Cloud High (GCC High) subscriptions.</span></span> |
| [<span data-ttu-id="694f2-130">Конечные точки Office 365 под управлением 21Vianet</span><span class="sxs-lookup"><span data-stu-id="694f2-130">Office 365 operated by 21Vianet endpoints</span></span>](urls-and-ip-address-ranges-21vianet.md) | <span data-ttu-id="694f2-131">Конечные точки для Office 365 под управлением компании 21Vianet, соответствующие требованиям для Office 365 в Китае.</span><span class="sxs-lookup"><span data-stu-id="694f2-131">The endpoints for Office 365 operated by 21Vianet, which is designed to meet the needs for Office 365 in China.</span></span> |
| [<span data-ttu-id="694f2-132">Конечные точки Office 365 Germany</span><span class="sxs-lookup"><span data-stu-id="694f2-132">Office 365 Germany endpoints</span></span>](office-365-germany-endpoints.md) | <span data-ttu-id="694f2-133">Конечные точки отдельного облака в Европе для наиболее регулируемых клиентов в Германии, Европейском Союзе (ЕС) и Европейской ассоциации свободной торговли (ЕАСТ).</span><span class="sxs-lookup"><span data-stu-id="694f2-133">The endpoints for a separate cloud in Europe for the most regulated customers in Germany, the European Union (EU), and the European Free Trade Association (EFTA).</span></span> |
|||

<span data-ttu-id="694f2-134">Чтобы автоматизировать получение актуального списка конечных точек для облачной службы Office 365, см. статью [Веб-служба IP-адресов и URL-адресов в Office 365](office-365-ip-web-service.md).</span><span class="sxs-lookup"><span data-stu-id="694f2-134">To automate getting the latest list of endpoints for your Office 365 cloud, see the [Office 365 IP Address and URL Web service](office-365-ip-web-service.md).</span></span>

<span data-ttu-id="694f2-135">Сведения о дополнительных конечных точках см. в этих статьях:</span><span class="sxs-lookup"><span data-stu-id="694f2-135">For additional endpoints, see these articles:</span></span>

- [<span data-ttu-id="694f2-136">Дополнительные конечные точки, отсутствующие в веб-службе</span><span class="sxs-lookup"><span data-stu-id="694f2-136">Additional endpoints not included in the Web service</span></span>](additional-office365-ip-addresses-and-urls.md)
- [<span data-ttu-id="694f2-137">Сетевые запросы в Office 2016 для Mac</span><span class="sxs-lookup"><span data-stu-id="694f2-137">Network requests in Office 2016 for Mac</span></span>](network-requests-in-office-2016-for-mac.md)


## <a name="additional-topics-for-office-365-networking"></a><span data-ttu-id="694f2-138">Дополнительные разделы об организации сети Office 365</span><span class="sxs-lookup"><span data-stu-id="694f2-138">Additional topics for Office 365 networking</span></span>

<span data-ttu-id="694f2-139">Специальные разделы, касающиеся организации сети Office 365, см. в указанных ниже статьях.</span><span class="sxs-lookup"><span data-stu-id="694f2-139">See these articles for specialized topics in Office 365 networking:</span></span>

- [<span data-ttu-id="694f2-140">Сети доставки содержимого</span><span class="sxs-lookup"><span data-stu-id="694f2-140">Content delivery networks</span></span>](content-delivery-networks.md)
- [<span data-ttu-id="694f2-141">Поддержка IPv6 в службах Office 365</span><span class="sxs-lookup"><span data-stu-id="694f2-141">IPv6 support in Office 365 services</span></span>](ipv6-support.md)
- [<span data-ttu-id="694f2-142">Поддержка NAT в Office 365</span><span class="sxs-lookup"><span data-stu-id="694f2-142">NAT support with Office 365</span></span>](nat-support-with-office-365.md)

## <a name="expressroute-for-office-365"></a><span data-ttu-id="694f2-143">ExpressRoute для Office 365</span><span class="sxs-lookup"><span data-stu-id="694f2-143">ExpressRoute for Office 365</span></span>

<span data-ttu-id="694f2-144">Сведения об использовании ExpressRoute для трафика Office 365 см. в указанных ниже статьях.</span><span class="sxs-lookup"><span data-stu-id="694f2-144">See these articles for information on the use of ExpressRoute for Office 365 traffic:</span></span>

- [<span data-ttu-id="694f2-145">Azure ExpressRoute для Office 365</span><span class="sxs-lookup"><span data-stu-id="694f2-145">Azure ExpressRoute for Office 365</span></span>](azure-expressroute.md)
- [<span data-ttu-id="694f2-146">Реализация ExpressRoute для Office 365</span><span class="sxs-lookup"><span data-stu-id="694f2-146">Implementing ExpressRoute for Office 365</span></span>](implementing-expressroute.md)
- [<span data-ttu-id="694f2-147">Планирование сети при использовании ExpressRoute для Office 365</span><span class="sxs-lookup"><span data-stu-id="694f2-147">Network planning with ExpressRoute for Office 365</span></span>](network-planning-with-expressroute.md)
- [<span data-ttu-id="694f2-148">Маршрутизация с использованием ExpressRoute для Office 365</span><span class="sxs-lookup"><span data-stu-id="694f2-148">Routing with ExpressRoute for Office 365</span></span>](routing-with-expressroute.md)
