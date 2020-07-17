---
title: Настройка сети для Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/19/2019
audience: ITPro
ms.topic: hub-page
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Ent_TLGs
ms.assetid: ''
description: 'Сводка: в этих статьях вы найдете сведения о сети для Microsoft 365.'
ms.openlocfilehash: 4c414d8cbf597af9165e991a71e5d6a6a330e33a
ms.sourcegitcommit: c112869b3ecc0f574b7054ee1edc8c57132f8237
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2020
ms.locfileid: "44735665"
---
# <a name="set-up-your-network-for-microsoft-365"></a><span data-ttu-id="03ad9-103">Настройка сети для Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="03ad9-103">Set up your network for Microsoft 365</span></span>

<span data-ttu-id="03ad9-104">*Эта статья относится как к Microsoft 365 Enterprise, так и к Office 365 корпоративный.*</span><span class="sxs-lookup"><span data-stu-id="03ad9-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="03ad9-p101">Важная часть вашей входящей миграции Microsoft 365 — убедиться в том, что в сети и подключения к Интернету настроена Оптимизация доступа. Настройка локальной сети для доступа к глобально распределенному облачному программному обеспечению (SaaS) отличается от традиционной сети, оптимизированной для трафика в локальных центрах обработки данных и центрального подключения к Интернету.</span><span class="sxs-lookup"><span data-stu-id="03ad9-p101">An important part of your Microsoft 365 onboarding is to ensure that your network and Internet connections are set up for optimized access. Configuring your on-premises network to access a globally distributed Software-as-a-Service (SaaS) cloud is different from a traditional network that is optimized for traffic to on-premises datacenters and a central Internet connection.</span></span> 

<span data-ttu-id="03ad9-107">С помощью этих статей можно ознакомиться с основными различиями пограничных устройств, клиентских компьютеров и локальной сети, а также изменять их для обеспечения оптимальной производительности для локальных пользователей.</span><span class="sxs-lookup"><span data-stu-id="03ad9-107">Use these articles to understand the key differences and to modify your edge devices, client computers, and on-premises network to get the best performance for your on-premises users.</span></span>

## <a name="how-microsoft-365-networking-works"></a><span data-ttu-id="03ad9-108">Работа сети Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="03ad9-108">How Microsoft 365 networking works</span></span>

<span data-ttu-id="03ad9-109">В этих статьях представлены общие сведения о подключении к Microsoft 365:</span><span class="sxs-lookup"><span data-stu-id="03ad9-109">See these articles for an overview of connectivity for Microsoft 365:</span></span>

- [<span data-ttu-id="03ad9-110">Обзор возможности сетевого подключения к Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="03ad9-110">Microsoft 365 networking connectivity overview</span></span>](office-365-networking-overview.md)
- [<span data-ttu-id="03ad9-111">Принципы сетевого подключения Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="03ad9-111">Microsoft 365 network connectivity principles</span></span>](office-365-network-connectivity-principles.md)
- [<span data-ttu-id="03ad9-112">Оценка сетевого подключения Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="03ad9-112">Assessing Microsoft 365 network connectivity</span></span>](assessing-network-connectivity.md)

<span data-ttu-id="03ad9-113">Советы по повышению производительности можно найти в [статье Планирование сети и настройка производительности для Microsoft 365](network-planning-and-performance.md).</span><span class="sxs-lookup"><span data-stu-id="03ad9-113">For advice on enhancing performance, see [Network planning and performance tuning for Microsoft 365](network-planning-and-performance.md).</span></span>

## <a name="support-microsoft-365-networking-as-a-network-equipment-vendor"></a><span data-ttu-id="03ad9-114">Поддержка сети Microsoft 365 в качестве поставщика сетевого оборудования</span><span class="sxs-lookup"><span data-stu-id="03ad9-114">Support Microsoft 365 networking as a network equipment vendor</span></span>

<span data-ttu-id="03ad9-p102">Если вы являетесь поставщиком сетевого оборудования, присоединяйтесь к [партнерской программе Office 365 для поставщиков сетевых устройств и служб](office-365-networking-partner-program.md). Зарегистрируйтесь в программе, чтобы встроить принципы сетевого подключения к Office 365 в свои продукты и решения.</span><span class="sxs-lookup"><span data-stu-id="03ad9-p102">If you are a network equipment vendor, join the [Office 365 Networking Partner Program](office-365-networking-partner-program.md). Enroll in the program to build Office 365 network connectivity principles into your products and solutions.</span></span> 

## <a name="office-365-endpoints"></a><span data-ttu-id="03ad9-117">Конечные точки Office 365</span><span class="sxs-lookup"><span data-stu-id="03ad9-117">Office 365 endpoints</span></span>

<span data-ttu-id="03ad9-118">Конечные точки — это набор конечных IP-адресов, доменных имен DNS и URL-адресов для трафика Office 365 в Интернете.</span><span class="sxs-lookup"><span data-stu-id="03ad9-118">Endpoints are the set of destination IP addresses, DNS domain names, and URLs for Office 365 traffic on the Internet.</span></span> 

<span data-ttu-id="03ad9-p103">Чтобы повысить производительность облачных служб Office 365, некоторым конечным точкам требуется специальная обработка клиентскими браузерами и устройствами в сети периметра. К этим устройствам относятся брандмауэры, устройства расшифровки и анализа SSL-трафика, устройства анализа пакетов и системы защиты от потери данных.</span><span class="sxs-lookup"><span data-stu-id="03ad9-p103">To optimize performance to Office 365 cloud-based services, some endpoints need special handling by your client browsers and the devices in your edge network. These devices include firewalls, SSL Break and Inspect and packet inspection devices, and data loss prevention systems.</span></span>

<span data-ttu-id="03ad9-121">Подробные сведения см. в статье [Управление конечными точками Office 365](managing-office-365-endpoints.md).</span><span class="sxs-lookup"><span data-stu-id="03ad9-121">See [Managing Office 365 endpoints](managing-office-365-endpoints.md) for the details.</span></span>

<span data-ttu-id="03ad9-p104">В настоящее время существует пять разных облаков Office 365. Эта таблица позволяет перейти к списку конечных точек для каждого из них.</span><span class="sxs-lookup"><span data-stu-id="03ad9-p104">There are currently five different Office 365 clouds. This table takes you to the list of endpoints for each one.</span></span>

|||
|:-------|:-----|
| [<span data-ttu-id="03ad9-124">Глобальные конечные точки</span><span class="sxs-lookup"><span data-stu-id="03ad9-124">Worldwide endpoints</span></span>](urls-and-ip-address-ranges.md) | <span data-ttu-id="03ad9-125">Конечные точки для подписок на Office 365 во всем мире, которые включают облако сообщества государственных организаций США (GCC).</span><span class="sxs-lookup"><span data-stu-id="03ad9-125">The endpoints for worldwide Office 365 subscriptions, which include the United States Government Community Cloud (GCC).</span></span> |
| [<span data-ttu-id="03ad9-126">Конечные точки U.S. Government DoD</span><span class="sxs-lookup"><span data-stu-id="03ad9-126">U.S. Government DoD endpoints</span></span>](office-365-u-s-government-dod-endpoints.md) | <span data-ttu-id="03ad9-127">Конечные точки для подписок Министерства обороны США (DoD).</span><span class="sxs-lookup"><span data-stu-id="03ad9-127">The endpoints for United States Department of Defense (DoD) subscriptions.</span></span> |
| [<span data-ttu-id="03ad9-128">Конечные точки U.S. Government GCC High</span><span class="sxs-lookup"><span data-stu-id="03ad9-128">U.S. Government GCC High endpoints</span></span>](office-365-u-s-government-gcc-high-endpoints.md) | <span data-ttu-id="03ad9-129">Конечные точки для подписок GCC High государственных организаций США.</span><span class="sxs-lookup"><span data-stu-id="03ad9-129">The endpoints for United States Government Community Cloud High (GCC High) subscriptions.</span></span> |
| [<span data-ttu-id="03ad9-130">Конечные точки Office 365 под управлением 21Vianet</span><span class="sxs-lookup"><span data-stu-id="03ad9-130">Office 365 operated by 21Vianet endpoints</span></span>](urls-and-ip-address-ranges-21vianet.md) | <span data-ttu-id="03ad9-131">Конечные точки для Office 365 под управлением компании 21Vianet, соответствующие требованиям для Office 365 в Китае.</span><span class="sxs-lookup"><span data-stu-id="03ad9-131">The endpoints for Office 365 operated by 21Vianet, which is designed to meet the needs for Office 365 in China.</span></span> |
| [<span data-ttu-id="03ad9-132">Конечные точки Office 365 Germany</span><span class="sxs-lookup"><span data-stu-id="03ad9-132">Office 365 Germany endpoints</span></span>](office-365-germany-endpoints.md) | <span data-ttu-id="03ad9-133">Конечные точки отдельного облака в Европе для наиболее регулируемых клиентов в Германии, Европейском Союзе (ЕС) и Европейской ассоциации свободной торговли (ЕАСТ).</span><span class="sxs-lookup"><span data-stu-id="03ad9-133">The endpoints for a separate cloud in Europe for the most regulated customers in Germany, the European Union (EU), and the European Free Trade Association (EFTA).</span></span> |
|||

<span data-ttu-id="03ad9-134">Чтобы автоматизировать получение актуального списка конечных точек для облачной службы Office 365, см. статью [Веб-служба IP-адресов и URL-адресов в Office 365](office-365-ip-web-service.md).</span><span class="sxs-lookup"><span data-stu-id="03ad9-134">To automate getting the latest list of endpoints for your Office 365 cloud, see the [Office 365 IP Address and URL Web service](office-365-ip-web-service.md).</span></span>

<span data-ttu-id="03ad9-135">Сведения о дополнительных конечных точках см. в этих статьях:</span><span class="sxs-lookup"><span data-stu-id="03ad9-135">For additional endpoints, see these articles:</span></span>

- [<span data-ttu-id="03ad9-136">Дополнительные конечные точки, отсутствующие в веб-службе</span><span class="sxs-lookup"><span data-stu-id="03ad9-136">Additional endpoints not included in the Web service</span></span>](additional-office365-ip-addresses-and-urls.md)
- [<span data-ttu-id="03ad9-137">Сетевые запросы в Office 2016 для Mac</span><span class="sxs-lookup"><span data-stu-id="03ad9-137">Network requests in Office 2016 for Mac</span></span>](network-requests-in-office-2016-for-mac.md)


## <a name="additional-topics-for-microsoft-365-networking"></a><span data-ttu-id="03ad9-138">Дополнительные разделы, посвященные Microsoft 365 Network</span><span class="sxs-lookup"><span data-stu-id="03ad9-138">Additional topics for Microsoft 365 networking</span></span>

<span data-ttu-id="03ad9-139">В следующих статьях представлены специализированные разделы, посвященные Microsoft 365 Network:</span><span class="sxs-lookup"><span data-stu-id="03ad9-139">See these articles for specialized topics in Microsoft 365 networking:</span></span>

- [<span data-ttu-id="03ad9-140">Сети доставки содержимого</span><span class="sxs-lookup"><span data-stu-id="03ad9-140">Content delivery networks</span></span>](content-delivery-networks.md)
- [<span data-ttu-id="03ad9-141">Поддержка IPv6 в службах Office 365</span><span class="sxs-lookup"><span data-stu-id="03ad9-141">IPv6 support in Office 365 services</span></span>](ipv6-support.md)
- [<span data-ttu-id="03ad9-142">Поддержка NAT в Office 365</span><span class="sxs-lookup"><span data-stu-id="03ad9-142">NAT support with Office 365</span></span>](nat-support-with-office-365.md)

## <a name="expressroute-for-microsoft-365"></a><span data-ttu-id="03ad9-143">ExpressRoute для Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="03ad9-143">ExpressRoute for Microsoft 365</span></span>

<span data-ttu-id="03ad9-144">Сведения об использовании ExpressRoute для трафика Office 365 см. в указанных ниже статьях.</span><span class="sxs-lookup"><span data-stu-id="03ad9-144">See these articles for information on the use of ExpressRoute for Office 365 traffic:</span></span>

- [<span data-ttu-id="03ad9-145">Azure ExpressRoute для Office 365</span><span class="sxs-lookup"><span data-stu-id="03ad9-145">Azure ExpressRoute for Office 365</span></span>](azure-expressroute.md)
- [<span data-ttu-id="03ad9-146">Реализация ExpressRoute для Office 365</span><span class="sxs-lookup"><span data-stu-id="03ad9-146">Implementing ExpressRoute for Office 365</span></span>](implementing-expressroute.md)
- [<span data-ttu-id="03ad9-147">Планирование сети при использовании ExpressRoute для Office 365</span><span class="sxs-lookup"><span data-stu-id="03ad9-147">Network planning with ExpressRoute for Office 365</span></span>](network-planning-with-expressroute.md)
- [<span data-ttu-id="03ad9-148">Маршрутизация с использованием ExpressRoute для Office 365</span><span class="sxs-lookup"><span data-stu-id="03ad9-148">Routing with ExpressRoute for Office 365</span></span>](routing-with-expressroute.md)
