---
title: "Доступно диаграмму — пример структуры веб-сайтов в Microsoft Azure для SharePoint 2013"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.collection: Ent_O365
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: b91124bc-c7ec-4929-b77c-d6293db9f15e
description: "Эта статья представляет собой текстовую версию схемы \"Пример проектирования: веб-сайты в Microsoft Azure для SharePoint 2013."
ms.openlocfilehash: 0d42a96f80d47b360084557fea47c4155d106d30
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="accessible-diagram---design-sample-internet-sites-in-microsoft-azure-for-sharepoint-2013"></a><span data-ttu-id="34436-103">Доступная схема — пример проекта: веб-сайты в Microsoft Azure для SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="34436-103">Accessible diagram - Design sample: Internet sites in Microsoft Azure for SharePoint 2013</span></span>

<span data-ttu-id="34436-104">**Сводка:** Эта статья является доступным текстовая версия схемы с именем пример разработки: веб-сайты в Microsoft Azure для SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="34436-104">**Summary:** This article is an accessible text version of the diagram named Design sample: Internet sites in Microsoft Azure for SharePoint 2013.</span></span>
  
<span data-ttu-id="34436-105">Используйте этот пример проекта в качестве отправной точки для использования в Интернете сайта в Azure с использованием SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="34436-105">Use this design example as a starting point for an Internet-facing site in Azure using SharePoint 2013.</span></span>
  
<span data-ttu-id="34436-106">На этом плакате показан пример того, как создать следующие аспекты SharePoint 2013:</span><span class="sxs-lookup"><span data-stu-id="34436-106">This poster shows an example of how to design the following aspects of SharePoint 2013:</span></span>
  
- <span data-ttu-id="34436-107">Пользователи</span><span class="sxs-lookup"><span data-stu-id="34436-107">Users</span></span>
    
- <span data-ttu-id="34436-108">Зоны и проверка подлинности</span><span class="sxs-lookup"><span data-stu-id="34436-108">Zones and authentication</span></span>
    
- <span data-ttu-id="34436-109">Ферма серверов</span><span class="sxs-lookup"><span data-stu-id="34436-109">Server farm</span></span>
    
- <span data-ttu-id="34436-110">Сайт администрирования</span><span class="sxs-lookup"><span data-stu-id="34436-110">Administration site</span></span>
    
- <span data-ttu-id="34436-111">Службы</span><span class="sxs-lookup"><span data-stu-id="34436-111">Services</span></span>
    
- <span data-ttu-id="34436-112">Пулы приложений и веб-приложения</span><span class="sxs-lookup"><span data-stu-id="34436-112">Application pools and web applications</span></span>
    
- <span data-ttu-id="34436-113">Семейства веб-сайтов</span><span class="sxs-lookup"><span data-stu-id="34436-113">Site collections</span></span>
    
- <span data-ttu-id="34436-114">Сайты</span><span class="sxs-lookup"><span data-stu-id="34436-114">Sites</span></span>
    
- <span data-ttu-id="34436-115">Базы данных контента</span><span class="sxs-lookup"><span data-stu-id="34436-115">Content databases</span></span>
    
- <span data-ttu-id="34436-116">Зоны и URL-адреса</span><span class="sxs-lookup"><span data-stu-id="34436-116">Zones and URLs</span></span>
    
## <a name="users-zones-and-authentication"></a><span data-ttu-id="34436-117">Пользователи, зоны и проверка подлинности</span><span class="sxs-lookup"><span data-stu-id="34436-117">Users, zones and authentication</span></span>

<span data-ttu-id="34436-p101">Этот проект включает учетные записи пользователей четырех типов. Каждый тип учетной записи связан с сайтом для доступа и зоной, использующей определенный тип проверки подлинности. </span><span class="sxs-lookup"><span data-stu-id="34436-p101">There are four types of user accounts in this design. Each type of account is associated with a site for access and with a zone that uses a specific type of authentication.</span></span> 
  
- <span data-ttu-id="34436-120">Анонимные пользователи — анонимные пользователи имеют доступ через сайта, например http://www.contoso.com. — Это зона, они используют «зона Интернета аудио- и анонимных», которая использует анонимный доступ.</span><span class="sxs-lookup"><span data-stu-id="34436-120">Anonymous customers — Anonymous customers have access through a site such as http://www.contoso.com. The zone they use is the "Internet zone / anonymous", which uses anonymous authentication.</span></span>
    
- <span data-ttu-id="34436-121">Проверка подлинности клиентов — имеют доступ заказчики проверкой подлинности через сайта, например https://secure.contoso.com. — Это зона, они используют «зона экстрасети / SAML», которая использует Azure Active Directory с проверкой подлинности SAML.</span><span class="sxs-lookup"><span data-stu-id="34436-121">Authenticated customers — Authenticated customers have access through a site such as https://secure.contoso.com. The zone they use is the "Extranet zone / SAML", which uses Azure Active Directory with SAML authentication.</span></span>
    
- <span data-ttu-id="34436-p102">Веб-сайтов авторов и разработчиков — веб-страниц и разработчики имеют доступ через сайты, такие как http://authoring.contoso.com:8000 или http://www.contoso.com:8000. — Это зона, они используют «зоны по умолчанию аудио- и встроенная Windows», с использованием доменных служб Active Directory (AD DS).</span><span class="sxs-lookup"><span data-stu-id="34436-p102">Site authors and developers — Site authors and developers have access through sites such as http://authoring.contoso.com:8000 or http://www.contoso.com:8000. The zone they use is the "Default zone / Windows integrated", which uses Active Directory Domain Services (AD DS).</span></span>
    
- <span data-ttu-id="34436-p103">Учетная запись обхода поиска — Учетная запись обхода поиска имеет доступ через сайты, такие как http://authoring.contoso.com:8000 или http://www.contoso.com:8000. — Это зона, она использует «зоны по умолчанию аудио- и встроенная Windows», которая использует Доменные службы Active Directory с проверкой подлинности Windows NTLM.</span><span class="sxs-lookup"><span data-stu-id="34436-p103">Search Crawl Account — The search crawl account has access through sites such as http://authoring.contoso.com:8000 or http://www.contoso.com:8000. The zone it uses is the "Default zone / Windows integrated", which uses AD DS with Windows NTLM authentication.</span></span>
    
## <a name="server-farm"></a><span data-ttu-id="34436-126">Ферма серверов</span><span class="sxs-lookup"><span data-stu-id="34436-126">Server farm</span></span>

<span data-ttu-id="34436-p104">Пользователи получают доступ к ферме серверов через службу Azure. Ферма серверов содержит один или несколько веб-серверов.</span><span class="sxs-lookup"><span data-stu-id="34436-p104">The users access the server farm through Azure. The server farm contains one or more Web servers.</span></span>
  
## <a name="administration-site"></a><span data-ttu-id="34436-129">Сайт администрирования</span><span class="sxs-lookup"><span data-stu-id="34436-129">Administration site</span></span>

<span data-ttu-id="34436-p105">Сайт администрирования включает несколько серверов приложений, обменивающихся данными с пулом приложений (пулом приложений 1 в примере), который использует веб-приложение "Сайт центра администрирования". Сайт центра администрирования предоставляет доступ к семействам веб-сайтов в пределах организации.</span><span class="sxs-lookup"><span data-stu-id="34436-p105">The administration site contains several application servers, which communicate with an Application Pool (Application Pool 1 in the example) that uses the web application Central Administration Site. The Central Administration Site provides access to site collections within the organization.</span></span>
  
<span data-ttu-id="34436-132">Сайт администрирования также содержит серверы базы данных SQL, которые представляют из себя серверы базы данных с установленным сервером SQL Server, настроенным для поддержки кластеризации SQL, зеркального отображения или компонента AlwaysOn (последний используется только в SQL Server 2012).</span><span class="sxs-lookup"><span data-stu-id="34436-132">The administration site also contains SQL Database servers, which are database servers with SQL Server installed and configured to support SQL clustering, mirroring, or AlwaysOn (AlwaysOn applies to SQL Server 2012 only).</span></span>
  
## <a name="services"></a><span data-ttu-id="34436-133">Службы</span><span class="sxs-lookup"><span data-stu-id="34436-133">Services</span></span>

<span data-ttu-id="34436-p106">В этом примере проекта показан веб-сайт служб IIS, веб-службы SharePoint. Веб-службы SharePoint включают пул приложений (пул приложений 2) с тремя службами (службами профилей пользователей, поиска и управляемых метаданных).</span><span class="sxs-lookup"><span data-stu-id="34436-p106">The design example shows an Internet Information Services (IIS) website, SharePoint Web Services. SharePoint Web Services contains an application pool (Application Pool 2) with three services, User Profile, Search, and Managed Metadata.</span></span>
  
<span data-ttu-id="34436-136">Примечания относительно служб для веб-сайтов</span><span class="sxs-lookup"><span data-stu-id="34436-136">Notes on Services for Internet sites:</span></span>
  
> <span data-ttu-id="34436-137">Управляемые метаданные — Убедитесь, что для выбора **этого приложения-службы — это место хранения по умолчанию для наборов терминов, определяемых столбца**.</span><span class="sxs-lookup"><span data-stu-id="34436-137">Managed Metadata — Be sure to select **This service application is the default storage location for column specific term sets**.</span></span>
    
> <span data-ttu-id="34436-138">Управление приложениями. Мы не рекомендуем использовать приложения на общедоступном веб-сайте в Azure.</span><span class="sxs-lookup"><span data-stu-id="34436-138">App Management — We do not recommend using apps in a public-facing Internet site in Azure.</span></span>
    
## <a name="application-pools-and-web-applications"></a><span data-ttu-id="34436-139">Пулы приложений и веб-приложения</span><span class="sxs-lookup"><span data-stu-id="34436-139">Application pools and web applications</span></span>

<span data-ttu-id="34436-p107">Группа по умолчанию в службе Azure включает пул приложений 3, содержащий веб-приложение с именем Contoso Sites. Это семейство веб-сайтов с именем на основе пути расположено по адресу http://internal:8000.</span><span class="sxs-lookup"><span data-stu-id="34436-p107">The Default Group in Azure shows Application Pool 3, which contains a web application named Contoso Sites. This path-based site collection is located at http://internal:8000.</span></span>
  
## <a name="site-collections-and-sites"></a><span data-ttu-id="34436-142">Семейства веб-сайтов и сайты</span><span class="sxs-lookup"><span data-stu-id="34436-142">Site collections and sites</span></span>

<span data-ttu-id="34436-143">Семейства веб-сайтов в пуле приложений включают следующие компоненты:</span><span class="sxs-lookup"><span data-stu-id="34436-143">The site collections contained in the application pool include:</span></span>
  
- <span data-ttu-id="34436-144">семейство веб-сайтов 1 с указанием узла в имени для обхода контента (пример расположения — http://authoring.contoso.com:8000);</span><span class="sxs-lookup"><span data-stu-id="34436-144">Host-named site collection 1 for crawling (example location http://authoring.contoso.com:8000)</span></span>
    
- <span data-ttu-id="34436-145">семейство веб-сайтов 2 с указанием узла в имени для запросов (примеры расположений — http://www.contoso.com, https://secure.contoso.com, http://www.contoso.com:8000);</span><span class="sxs-lookup"><span data-stu-id="34436-145">Host-named site collection 2 for queries (sample locations http://www.contoso.com, https://secure.contoso.com, http://www.contoso.com:8000)</span></span>
    
- <span data-ttu-id="34436-146">семейство веб-сайтов 3 с указанием узла в имени для запросов (примеры расположений — http://assets.contoso.com, https://secureassets.contoso.com, http://assets.contoso.com:8000).</span><span class="sxs-lookup"><span data-stu-id="34436-146">Host-named site collection 3 for queries (sample locations http://assets.contoso.com, https://secureassets.contoso.com, http://assets.contoso.com:8000)</span></span>
    
## <a name="content-databases"></a><span data-ttu-id="34436-147">Базы данных контента</span><span class="sxs-lookup"><span data-stu-id="34436-147">Content databases</span></span>

<span data-ttu-id="34436-p108">В этом примере показаны две базы данных контента. Одна предназначена для семейства веб-сайтов 1, используемого для обхода контента (http://authoring.contoso.com:8000). Вторая предназначена для двух семейств веб-сайтов 2 и 3, используемых для запросов (http://www.contoso.com, https://secure.contoso.com, http://www.contoso.com:8000, or http://assets.contoso.com, https://secureassets.contoso.com, http://assets.contoso.com:8000).</span><span class="sxs-lookup"><span data-stu-id="34436-p108">The example shows two content databases. One is for the site collection 1 used for crawling (http://authoring.contoso.com:8000). The other is for the two site collections 2 and 3 used for queries (http://www.contoso.com, https://secure.contoso.com, http://www.contoso.com:8000, or http://assets.contoso.com, https://secureassets.contoso.com, http://assets.contoso.com:8000).</span></span>
  
## <a name="zones-and-urls"></a><span data-ttu-id="34436-151">Зоны и URL-адреса</span><span class="sxs-lookup"><span data-stu-id="34436-151">Zones and URLs</span></span>

<span data-ttu-id="34436-152">В этом примере приведены три зоны со связанными URL-адресами с балансировкой нагрузки, которые используются различными учетными записями. </span><span class="sxs-lookup"><span data-stu-id="34436-152">The example shows three zones with the associated load-balanced URLs that are used by different user accounts.</span></span> 
  
<span data-ttu-id="34436-153">Первый список зон и URL-адресов связан с семейством веб-сайтов 1 и содержит следующую информацию:</span><span class="sxs-lookup"><span data-stu-id="34436-153">The first list of zones and URLs is related to site collection 1, and it contains the following information:</span></span>
  
- <span data-ttu-id="34436-154">Пользователей — веб-страниц</span><span class="sxs-lookup"><span data-stu-id="34436-154">Users - Site authors</span></span>
    
- <span data-ttu-id="34436-155">Зона — по умолчанию</span><span class="sxs-lookup"><span data-stu-id="34436-155">Zone - Default</span></span>
    
- <span data-ttu-id="34436-156">Подсистемы балансировки нагрузки URL-адрес - http://authoring.contoso.com:8000</span><span class="sxs-lookup"><span data-stu-id="34436-156">Load-balanced URL - http://authoring.contoso.com:8000</span></span>
    
<span data-ttu-id="34436-p109">Второй список зон и URL-адресов включает пользователей трех типов в трех различных зонах. Этот список связан с семейством веб-сайтов 2 и содержит следующую информацию.</span><span class="sxs-lookup"><span data-stu-id="34436-p109">The second list of zones and URLs has three different types of users in three different zones. It is related to site collection 2, and it contains the following information:</span></span>
  
<span data-ttu-id="34436-159">Первая зона:</span><span class="sxs-lookup"><span data-stu-id="34436-159">First zone:</span></span>
  
- <span data-ttu-id="34436-160">Пользователей — веб-страниц</span><span class="sxs-lookup"><span data-stu-id="34436-160">Users - Site authors</span></span>
    
- <span data-ttu-id="34436-161">Зона — по умолчанию</span><span class="sxs-lookup"><span data-stu-id="34436-161">Zone - Default</span></span>
    
- <span data-ttu-id="34436-162">Подсистемы балансировки нагрузки URL-адрес - http://www.contoso.com:8000</span><span class="sxs-lookup"><span data-stu-id="34436-162">Load-balanced URL - http://www.contoso.com:8000</span></span>
    
<span data-ttu-id="34436-163">Вторая зона:</span><span class="sxs-lookup"><span data-stu-id="34436-163">Second zone:</span></span>
  
- <span data-ttu-id="34436-164">Пользователи - анонимных пользователей</span><span class="sxs-lookup"><span data-stu-id="34436-164">Users - Anonymous customers</span></span>
    
- <span data-ttu-id="34436-165">Зона - Интернета</span><span class="sxs-lookup"><span data-stu-id="34436-165">Zone - Internet</span></span>
    
- <span data-ttu-id="34436-166">Подсистемы балансировки нагрузки URL-адрес - http://www.contoso.com</span><span class="sxs-lookup"><span data-stu-id="34436-166">Load-balanced URL - http://www.contoso.com</span></span>
    
<span data-ttu-id="34436-167">Третья зона:</span><span class="sxs-lookup"><span data-stu-id="34436-167">Third zone:</span></span>
  
- <span data-ttu-id="34436-168">Пользователи - прошедшего проверку подлинности клиентов</span><span class="sxs-lookup"><span data-stu-id="34436-168">Users - Authenticated customers</span></span>
    
- <span data-ttu-id="34436-169">Зона - экстрасети</span><span class="sxs-lookup"><span data-stu-id="34436-169">Zone - Extranet</span></span>
    
- <span data-ttu-id="34436-170">Подсистемы балансировки нагрузки URL-адрес - https://secure.contoso.com</span><span class="sxs-lookup"><span data-stu-id="34436-170">Load-balanced URL - https://secure.contoso.com</span></span>
    
<span data-ttu-id="34436-p110">Третий список зон и URL-адресов включает пользователей трех типов в трех различных зонах. Этот список связан с семейством веб-сайтов 3 и содержит следующую информацию.</span><span class="sxs-lookup"><span data-stu-id="34436-p110">The third list of zones and URLs has three different types of users in three different zones. It is related to site collection 3, and it contains the following information:</span></span>
  
<span data-ttu-id="34436-173">Первая зона:</span><span class="sxs-lookup"><span data-stu-id="34436-173">First zone:</span></span>
  
- <span data-ttu-id="34436-174">Пользователей — веб-страниц</span><span class="sxs-lookup"><span data-stu-id="34436-174">Users - Site authors</span></span>
    
- <span data-ttu-id="34436-175">Зона - Интернета</span><span class="sxs-lookup"><span data-stu-id="34436-175">Zone - Internet</span></span>
    
- <span data-ttu-id="34436-176">Подсистемы балансировки нагрузки URL-адрес - http://assets.contoso.com:8000</span><span class="sxs-lookup"><span data-stu-id="34436-176">Load-balanced URL - http://assets.contoso.com:8000</span></span>
    
<span data-ttu-id="34436-177">Вторая зона:</span><span class="sxs-lookup"><span data-stu-id="34436-177">Second zone:</span></span>
  
- <span data-ttu-id="34436-178">Пользователи - анонимных пользователей</span><span class="sxs-lookup"><span data-stu-id="34436-178">Users - Anonymous customers</span></span>
    
- <span data-ttu-id="34436-179">Зона - Интернета</span><span class="sxs-lookup"><span data-stu-id="34436-179">Zone - Internet</span></span>
    
- <span data-ttu-id="34436-180">Подсистемы балансировки нагрузки URL-адрес - http://assets.contoso.com</span><span class="sxs-lookup"><span data-stu-id="34436-180">Load-balanced URL - http://assets.contoso.com</span></span>
    
<span data-ttu-id="34436-181">Третья зона:</span><span class="sxs-lookup"><span data-stu-id="34436-181">Third zone:</span></span>
  
- <span data-ttu-id="34436-182">Пользователи - прошедшего проверку подлинности клиентов</span><span class="sxs-lookup"><span data-stu-id="34436-182">Users - Authenticated customers</span></span>
    
- <span data-ttu-id="34436-183">Зона - экстрасети</span><span class="sxs-lookup"><span data-stu-id="34436-183">Zone - Extranet</span></span>
    
- <span data-ttu-id="34436-184">Подсистемы балансировки нагрузки URL-адрес - http://secureassets.contoso.com</span><span class="sxs-lookup"><span data-stu-id="34436-184">Load-balanced URL - http://secureassets.contoso.com</span></span>
    

