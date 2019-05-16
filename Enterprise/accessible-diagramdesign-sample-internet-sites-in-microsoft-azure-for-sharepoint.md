---
title: Доступная схема — пример структуры веб-сайтов в Microsoft Azure для SharePoint 2013
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.collection: Ent_O365
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: b91124bc-c7ec-4929-b77c-d6293db9f15e
description: 'Эта статья представляет собой текстовую версию схемы "Пример проектирования: веб-сайты в Microsoft Azure для SharePoint 2013.'
ms.openlocfilehash: 28cf28739c476638b5775d170508001f2a9730ed
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068804"
---
# <a name="accessible-diagram---design-sample-internet-sites-in-microsoft-azure-for-sharepoint-2013"></a><span data-ttu-id="6fc3f-103">Доступная схема — пример проекта: веб-сайты в Microsoft Azure для SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="6fc3f-103">Accessible diagram - Design sample: Internet sites in Microsoft Azure for SharePoint 2013</span></span>

<span data-ttu-id="6fc3f-104">**Сводка:** Эта статья представляет собой текстовую версию схемы "Пример дизайна": веб-сайты в Microsoft Azure для SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="6fc3f-104">**Summary:** This article is an accessible text version of the diagram named Design sample: Internet sites in Microsoft Azure for SharePoint 2013.</span></span>
  
<span data-ttu-id="6fc3f-105">Используйте этот пример структуры в качестве отправной точки для веб-сайта в Azure с помощью SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="6fc3f-105">Use this design example as a starting point for an Internet-facing site in Azure using SharePoint 2013.</span></span>
  
<span data-ttu-id="6fc3f-106">На этом плакате показан пример создания следующих аспектов SharePoint 2013:</span><span class="sxs-lookup"><span data-stu-id="6fc3f-106">This poster shows an example of how to design the following aspects of SharePoint 2013:</span></span>
  
- <span data-ttu-id="6fc3f-107">Пользователи</span><span class="sxs-lookup"><span data-stu-id="6fc3f-107">Users</span></span>
    
- <span data-ttu-id="6fc3f-108">Зоны и проверка подлинности</span><span class="sxs-lookup"><span data-stu-id="6fc3f-108">Zones and authentication</span></span>
    
- <span data-ttu-id="6fc3f-109">Ферма серверов</span><span class="sxs-lookup"><span data-stu-id="6fc3f-109">Server farm</span></span>
    
- <span data-ttu-id="6fc3f-110">Сайт администрирования</span><span class="sxs-lookup"><span data-stu-id="6fc3f-110">Administration site</span></span>
    
- <span data-ttu-id="6fc3f-111">Службы</span><span class="sxs-lookup"><span data-stu-id="6fc3f-111">Services</span></span>
    
- <span data-ttu-id="6fc3f-112">Пулы приложений и веб-приложения</span><span class="sxs-lookup"><span data-stu-id="6fc3f-112">Application pools and web applications</span></span>
    
- <span data-ttu-id="6fc3f-113">Семейства веб-сайтов</span><span class="sxs-lookup"><span data-stu-id="6fc3f-113">Site collections</span></span>
    
- <span data-ttu-id="6fc3f-114">Сайты</span><span class="sxs-lookup"><span data-stu-id="6fc3f-114">Sites</span></span>
    
- <span data-ttu-id="6fc3f-115">Базы данных контента</span><span class="sxs-lookup"><span data-stu-id="6fc3f-115">Content databases</span></span>
    
- <span data-ttu-id="6fc3f-116">Зоны и URL-адреса</span><span class="sxs-lookup"><span data-stu-id="6fc3f-116">Zones and URLs</span></span>
    
## <a name="users-zones-and-authentication"></a><span data-ttu-id="6fc3f-117">Пользователи, зоны и проверка подлинности</span><span class="sxs-lookup"><span data-stu-id="6fc3f-117">Users, zones and authentication</span></span>

<span data-ttu-id="6fc3f-p101">Этот проект включает учетные записи пользователей четырех типов. Каждый тип учетной записи связан с сайтом для доступа и зоной, использующей определенный тип проверки подлинности. </span><span class="sxs-lookup"><span data-stu-id="6fc3f-p101">There are four types of user accounts in this design. Each type of account is associated with a site for access and with a zone that uses a specific type of authentication.</span></span> 
  
- <span data-ttu-id="6fc3f-120">Анонимные клиенты — анонимные клиенты получают доступ через сайт, http://www.contoso.comнапример.</span><span class="sxs-lookup"><span data-stu-id="6fc3f-120">Anonymous customers — Anonymous customers have access through a site such as http://www.contoso.com.</span></span> <span data-ttu-id="6fc3f-121">Используемая зона — "Интернет-зона/Аноним", которая использует анонимную проверку подлинности.</span><span class="sxs-lookup"><span data-stu-id="6fc3f-121">The zone they use is the "Internet zone / anonymous", which uses anonymous authentication.</span></span>
    
- <span data-ttu-id="6fc3f-122">Проверенные клиенты — пользователи, прошедшие проверку подлинности, имеют https://secure.contoso.comдоступ через сайт, например.</span><span class="sxs-lookup"><span data-stu-id="6fc3f-122">Authenticated customers — Authenticated customers have access through a site such as https://secure.contoso.com.</span></span> <span data-ttu-id="6fc3f-123">Используемая зона — это "зона экстрасети/SAML", которая использует Azure Active Directory с проверкой подлинности SAML.</span><span class="sxs-lookup"><span data-stu-id="6fc3f-123">The zone they use is the "Extranet zone / SAML", which uses Azure Active Directory with SAML authentication.</span></span>
    
- <span data-ttu-id="6fc3f-124">Авторы и разработчики сайтов — Авторы и разработчики сайтов имеют доступ к таким сайтам http://authoring.contoso.com:8000 , http://www.contoso.com:8000как или.</span><span class="sxs-lookup"><span data-stu-id="6fc3f-124">Site authors and developers — Site authors and developers have access through sites such as http://authoring.contoso.com:8000 or http://www.contoso.com:8000.</span></span> <span data-ttu-id="6fc3f-125">Используемая зона — это "зона по умолчанию/встроенная система Windows", которая использует доменные службы Active Directory (AD DS).</span><span class="sxs-lookup"><span data-stu-id="6fc3f-125">The zone they use is the "Default zone / Windows integrated", which uses Active Directory Domain Services (AD DS).</span></span>
    
- <span data-ttu-id="6fc3f-126">Учетная запись обхода поиска — у учетной записи обхода контента есть доступ http://authoring.contoso.com:8000 к http://www.contoso.com:8000сайтам, таким как или.</span><span class="sxs-lookup"><span data-stu-id="6fc3f-126">Search Crawl Account — The search crawl account has access through sites such as http://authoring.contoso.com:8000 or http://www.contoso.com:8000.</span></span> <span data-ttu-id="6fc3f-127">Используемая зона — это "Стандартная зона/встроенная система Windows", которая использует доменные службы Active Directory с проверкой подлинности Windows NTLM.</span><span class="sxs-lookup"><span data-stu-id="6fc3f-127">The zone it uses is the "Default zone / Windows integrated", which uses AD DS with Windows NTLM authentication.</span></span>
    
## <a name="server-farm"></a><span data-ttu-id="6fc3f-128">Ферма серверов</span><span class="sxs-lookup"><span data-stu-id="6fc3f-128">Server farm</span></span>

<span data-ttu-id="6fc3f-p106">Пользователи получают доступ к ферме серверов через службу Azure. Ферма серверов содержит один или несколько веб-серверов.</span><span class="sxs-lookup"><span data-stu-id="6fc3f-p106">The users access the server farm through Azure. The server farm contains one or more Web servers.</span></span>
  
## <a name="administration-site"></a><span data-ttu-id="6fc3f-131">Сайт администрирования</span><span class="sxs-lookup"><span data-stu-id="6fc3f-131">Administration site</span></span>

<span data-ttu-id="6fc3f-p107">Сайт администрирования включает несколько серверов приложений, обменивающихся данными с пулом приложений (пулом приложений 1 в примере), который использует веб-приложение "Сайт центра администрирования". Сайт центра администрирования предоставляет доступ к семействам веб-сайтов в пределах организации.</span><span class="sxs-lookup"><span data-stu-id="6fc3f-p107">The administration site contains several application servers, which communicate with an Application Pool (Application Pool 1 in the example) that uses the web application Central Administration Site. The Central Administration Site provides access to site collections within the organization.</span></span>
  
<span data-ttu-id="6fc3f-134">Сайт администрирования также содержит серверы базы данных SQL, которые представляют из себя серверы базы данных с установленным сервером SQL Server, настроенным для поддержки кластеризации SQL, зеркального отображения или компонента AlwaysOn (последний используется только в SQL Server 2012).</span><span class="sxs-lookup"><span data-stu-id="6fc3f-134">The administration site also contains SQL Database servers, which are database servers with SQL Server installed and configured to support SQL clustering, mirroring, or AlwaysOn (AlwaysOn applies to SQL Server 2012 only).</span></span>
  
## <a name="services"></a><span data-ttu-id="6fc3f-135">Службы</span><span class="sxs-lookup"><span data-stu-id="6fc3f-135">Services</span></span>

<span data-ttu-id="6fc3f-p108">В этом примере проекта показан веб-сайт служб IIS, веб-службы SharePoint. Веб-службы SharePoint включают пул приложений (пул приложений 2) с тремя службами (службами профилей пользователей, поиска и управляемых метаданных).</span><span class="sxs-lookup"><span data-stu-id="6fc3f-p108">The design example shows an Internet Information Services (IIS) website, SharePoint Web Services. SharePoint Web Services contains an application pool (Application Pool 2) with three services, User Profile, Search, and Managed Metadata.</span></span>
  
<span data-ttu-id="6fc3f-138">Примечания относительно служб для веб-сайтов</span><span class="sxs-lookup"><span data-stu-id="6fc3f-138">Notes on Services for Internet sites:</span></span>
  
> <span data-ttu-id="6fc3f-139">Управляемые метаданные. Обязательно установите флажок **Это приложение-служба является используемым по умолчанию местом хранения для наборов терминов, определяемых столбцом**.</span><span class="sxs-lookup"><span data-stu-id="6fc3f-139">Managed Metadata — Be sure to select **This service application is the default storage location for column specific term sets**.</span></span>
    
> <span data-ttu-id="6fc3f-140">Управление приложениями. Мы не рекомендуем использовать приложения на общедоступном веб-сайте в Azure.</span><span class="sxs-lookup"><span data-stu-id="6fc3f-140">App Management — We do not recommend using apps in a public-facing Internet site in Azure.</span></span>
    
## <a name="application-pools-and-web-applications"></a><span data-ttu-id="6fc3f-141">Пулы приложений и веб-приложения</span><span class="sxs-lookup"><span data-stu-id="6fc3f-141">Application pools and web applications</span></span>

<span data-ttu-id="6fc3f-142">Группа по умолчанию в службе Azure включает пул приложений 3, содержащий веб-приложение с именем Contoso Sites.</span><span class="sxs-lookup"><span data-stu-id="6fc3f-142">The Default Group in Azure shows Application Pool 3, which contains a web application named Contoso Sites.</span></span> <span data-ttu-id="6fc3f-143">Это семейство веб-сайтов на основе путей расположено по адресу http://internal:8000.</span><span class="sxs-lookup"><span data-stu-id="6fc3f-143">This path-based site collection is located at http://internal:8000.</span></span>
  
## <a name="site-collections-and-sites"></a><span data-ttu-id="6fc3f-144">Семейства веб-сайтов и сайты</span><span class="sxs-lookup"><span data-stu-id="6fc3f-144">Site collections and sites</span></span>

<span data-ttu-id="6fc3f-145">Семейства веб-сайтов в пуле приложений включают следующие компоненты:</span><span class="sxs-lookup"><span data-stu-id="6fc3f-145">The site collections contained in the application pool include:</span></span>
  
- <span data-ttu-id="6fc3f-146">Семейство веб-сайтов с именем на основе узла 1 для обхода (пример расположенияhttp://authoring.contoso.com:8000)</span><span class="sxs-lookup"><span data-stu-id="6fc3f-146">Host-named site collection 1 for crawling (example location http://authoring.contoso.com:8000)</span></span>
    
- <span data-ttu-id="6fc3f-147">Семейство сайтов с именем на основе узла 2 для запросов ( http://www.contoso.comпримеры https://secure.contoso.comрасположений,http://www.contoso.com:8000)</span><span class="sxs-lookup"><span data-stu-id="6fc3f-147">Host-named site collection 2 for queries (sample locations http://www.contoso.com, https://secure.contoso.com, http://www.contoso.com:8000)</span></span>
    
- <span data-ttu-id="6fc3f-148">Семейство сайтов с именем на основе узла 3 для запросов ( http://assets.contoso.comпримеры https://secureassets.contoso.comрасположений,http://assets.contoso.com:8000)</span><span class="sxs-lookup"><span data-stu-id="6fc3f-148">Host-named site collection 3 for queries (sample locations http://assets.contoso.com, https://secureassets.contoso.com, http://assets.contoso.com:8000)</span></span>
    
## <a name="content-databases"></a><span data-ttu-id="6fc3f-149">Базы данных контента</span><span class="sxs-lookup"><span data-stu-id="6fc3f-149">Content databases</span></span>

<span data-ttu-id="6fc3f-150">В этом примере показаны две базы данных контента.</span><span class="sxs-lookup"><span data-stu-id="6fc3f-150">The example shows two content databases.</span></span> <span data-ttu-id="6fc3f-151">Один — для семейства веб-сайтов 1, используемого для обходаhttp://authoring.contoso.com:8000)контента (.</span><span class="sxs-lookup"><span data-stu-id="6fc3f-151">One is for the site collection 1 used for crawling (http://authoring.contoso.com:8000).</span></span> <span data-ttu-id="6fc3f-152">Другой — для двух семейств веб-сайтов 2 и 3, используемых для запросовhttp://www.contoso.com( https://secure.contoso.com, http://www.contoso.com:8000,, http://assets.contoso.comили https://secureassets.contoso.com, http://assets.contoso.com:8000),.</span><span class="sxs-lookup"><span data-stu-id="6fc3f-152">The other is for the two site collections 2 and 3 used for queries (http://www.contoso.com, https://secure.contoso.com, http://www.contoso.com:8000, or http://assets.contoso.com, https://secureassets.contoso.com, http://assets.contoso.com:8000).</span></span>
  
## <a name="zones-and-urls"></a><span data-ttu-id="6fc3f-153">Зоны и URL-адреса</span><span class="sxs-lookup"><span data-stu-id="6fc3f-153">Zones and URLs</span></span>

<span data-ttu-id="6fc3f-154">В этом примере приведены три зоны со связанными URL-адресами с балансировкой нагрузки, которые используются различными учетными записями. </span><span class="sxs-lookup"><span data-stu-id="6fc3f-154">The example shows three zones with the associated load-balanced URLs that are used by different user accounts.</span></span> 
  
<span data-ttu-id="6fc3f-155">Первый список зон и URL-адресов связан с семейством веб-сайтов 1 и содержит следующую информацию:</span><span class="sxs-lookup"><span data-stu-id="6fc3f-155">The first list of zones and URLs is related to site collection 1, and it contains the following information:</span></span>
  
- <span data-ttu-id="6fc3f-156">Пользователи — авторы сайтов</span><span class="sxs-lookup"><span data-stu-id="6fc3f-156">Users - Site authors</span></span>
    
- <span data-ttu-id="6fc3f-157">Зона — по умолчанию</span><span class="sxs-lookup"><span data-stu-id="6fc3f-157">Zone - Default</span></span>
    
- <span data-ttu-id="6fc3f-158">URL-адрес с балансировкой нагрузки —http://authoring.contoso.com:8000</span><span class="sxs-lookup"><span data-stu-id="6fc3f-158">Load-balanced URL - http://authoring.contoso.com:8000</span></span>
    
<span data-ttu-id="6fc3f-p111">Второй список зон и URL-адресов включает пользователей трех типов в трех различных зонах. Этот список связан с семейством веб-сайтов 2 и содержит следующую информацию.</span><span class="sxs-lookup"><span data-stu-id="6fc3f-p111">The second list of zones and URLs has three different types of users in three different zones. It is related to site collection 2, and it contains the following information:</span></span>
  
<span data-ttu-id="6fc3f-161">Первая зона:</span><span class="sxs-lookup"><span data-stu-id="6fc3f-161">First zone:</span></span>
  
- <span data-ttu-id="6fc3f-162">Пользователи — авторы сайтов</span><span class="sxs-lookup"><span data-stu-id="6fc3f-162">Users - Site authors</span></span>
    
- <span data-ttu-id="6fc3f-163">Зона — по умолчанию</span><span class="sxs-lookup"><span data-stu-id="6fc3f-163">Zone - Default</span></span>
    
- <span data-ttu-id="6fc3f-164">URL-адрес с балансировкой нагрузки —http://www.contoso.com:8000</span><span class="sxs-lookup"><span data-stu-id="6fc3f-164">Load-balanced URL - http://www.contoso.com:8000</span></span>
    
<span data-ttu-id="6fc3f-165">Вторая зона:</span><span class="sxs-lookup"><span data-stu-id="6fc3f-165">Second zone:</span></span>
  
- <span data-ttu-id="6fc3f-166">Пользователи — анонимные клиенты</span><span class="sxs-lookup"><span data-stu-id="6fc3f-166">Users - Anonymous customers</span></span>
    
- <span data-ttu-id="6fc3f-167">Зона — Интернет</span><span class="sxs-lookup"><span data-stu-id="6fc3f-167">Zone - Internet</span></span>
    
- <span data-ttu-id="6fc3f-168">URL-адрес с балансировкой нагрузки —http://www.contoso.com</span><span class="sxs-lookup"><span data-stu-id="6fc3f-168">Load-balanced URL - http://www.contoso.com</span></span>
    
<span data-ttu-id="6fc3f-169">Третья зона:</span><span class="sxs-lookup"><span data-stu-id="6fc3f-169">Third zone:</span></span>
  
- <span data-ttu-id="6fc3f-170">Клиенты с проверкой подлинности пользователей</span><span class="sxs-lookup"><span data-stu-id="6fc3f-170">Users - Authenticated customers</span></span>
    
- <span data-ttu-id="6fc3f-171">Зона — экстрасеть</span><span class="sxs-lookup"><span data-stu-id="6fc3f-171">Zone - Extranet</span></span>
    
- <span data-ttu-id="6fc3f-172">URL-адрес с балансировкой нагрузки —https://secure.contoso.com</span><span class="sxs-lookup"><span data-stu-id="6fc3f-172">Load-balanced URL - https://secure.contoso.com</span></span>
    
<span data-ttu-id="6fc3f-p112">Третий список зон и URL-адресов включает пользователей трех типов в трех различных зонах. Этот список связан с семейством веб-сайтов 3 и содержит следующую информацию.</span><span class="sxs-lookup"><span data-stu-id="6fc3f-p112">The third list of zones and URLs has three different types of users in three different zones. It is related to site collection 3, and it contains the following information:</span></span>
  
<span data-ttu-id="6fc3f-175">Первая зона:</span><span class="sxs-lookup"><span data-stu-id="6fc3f-175">First zone:</span></span>
  
- <span data-ttu-id="6fc3f-176">Пользователи — авторы сайтов</span><span class="sxs-lookup"><span data-stu-id="6fc3f-176">Users - Site authors</span></span>
    
- <span data-ttu-id="6fc3f-177">Зона — Интернет</span><span class="sxs-lookup"><span data-stu-id="6fc3f-177">Zone - Internet</span></span>
    
- <span data-ttu-id="6fc3f-178">URL-адрес с балансировкой нагрузки —http://assets.contoso.com:8000</span><span class="sxs-lookup"><span data-stu-id="6fc3f-178">Load-balanced URL - http://assets.contoso.com:8000</span></span>
    
<span data-ttu-id="6fc3f-179">Вторая зона:</span><span class="sxs-lookup"><span data-stu-id="6fc3f-179">Second zone:</span></span>
  
- <span data-ttu-id="6fc3f-180">Пользователи — анонимные клиенты</span><span class="sxs-lookup"><span data-stu-id="6fc3f-180">Users - Anonymous customers</span></span>
    
- <span data-ttu-id="6fc3f-181">Зона — Интернет</span><span class="sxs-lookup"><span data-stu-id="6fc3f-181">Zone - Internet</span></span>
    
- <span data-ttu-id="6fc3f-182">URL-адрес с балансировкой нагрузки —http://assets.contoso.com</span><span class="sxs-lookup"><span data-stu-id="6fc3f-182">Load-balanced URL - http://assets.contoso.com</span></span>
    
<span data-ttu-id="6fc3f-183">Третья зона:</span><span class="sxs-lookup"><span data-stu-id="6fc3f-183">Third zone:</span></span>
  
- <span data-ttu-id="6fc3f-184">Клиенты с проверкой подлинности пользователей</span><span class="sxs-lookup"><span data-stu-id="6fc3f-184">Users - Authenticated customers</span></span>
    
- <span data-ttu-id="6fc3f-185">Зона — экстрасеть</span><span class="sxs-lookup"><span data-stu-id="6fc3f-185">Zone - Extranet</span></span>
    
- <span data-ttu-id="6fc3f-186">URL-адрес с балансировкой нагрузки —http://secureassets.contoso.com</span><span class="sxs-lookup"><span data-stu-id="6fc3f-186">Load-balanced URL - http://secureassets.contoso.com</span></span>
    

