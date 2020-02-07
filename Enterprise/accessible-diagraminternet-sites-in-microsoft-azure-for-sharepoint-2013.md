---
title: Доступная схема — веб-сайты в Microsoft Azure для SharePoint 2013
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 71636974-fb99-487c-ac67-f15e9401acba
f1.keywords:
- NOCSH
description: Данная статья представляет собой текстовую версию схемы "Веб-сайты в Microsoft Azure для SharePoint Server 2013".
ms.openlocfilehash: a68c5f8a0e92c45e3c33caaca77be0d841aa6003
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/07/2020
ms.locfileid: "41843900"
---
# <a name="accessible-diagram---internet-sites-in-microsoft-azure-for-sharepoint-2013"></a><span data-ttu-id="2dbf9-103">Доступная схема — веб-сайты в Microsoft Azure для SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="2dbf9-103">Accessible diagram - Internet sites in Microsoft Azure for SharePoint 2013</span></span>

<span data-ttu-id="2dbf9-104">**Сводка:** Эта статья представляет собой текстовую версию схемы с именем "веб-сайты" в Microsoft Azure для SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="2dbf9-104">**Summary:** This article is an accessible text version of the diagram named Internet sites in Microsoft Azure for SharePoint 2013.</span></span>
  
<span data-ttu-id="2dbf9-p101">На этом плакате рассказано и показано, какие преимущества для общедоступных веб-сайтов дают гибкие облачные решения и использование Azure Active Directory для учетных записей клиентов. На плакате имеется шесть указанных ниже сценариев, d которых рассказывается, какие преимущества получают веб-сайты от использования Azure. </span><span class="sxs-lookup"><span data-stu-id="2dbf9-p101">This poster describes and illustrates how public-facing Internet sites benefit from cloud elasticity and Azure AD for customer accounts. There are six different scenarios that describe how Internet sites benefit from Azure:</span></span> 
  
- <span data-ttu-id="2dbf9-107">Разработка и выбор размера топологии фермы. </span><span class="sxs-lookup"><span data-stu-id="2dbf9-107">Design and size the farm topology.</span></span> 
    
- <span data-ttu-id="2dbf9-108">Настройка для Azure. </span><span class="sxs-lookup"><span data-stu-id="2dbf9-108">Fine-tune for Azure.</span></span> 
    
- <span data-ttu-id="2dbf9-109">Выбор модели Active Directory. </span><span class="sxs-lookup"><span data-stu-id="2dbf9-109">Choose the Active Directory model.</span></span> 
    
- <span data-ttu-id="2dbf9-110">Планирование функций управления удостоверениями, работы с зонами и проверки подлинности. </span><span class="sxs-lookup"><span data-stu-id="2dbf9-110">Design for identity management, zones, and authentication.</span></span> 
    
- <span data-ttu-id="2dbf9-111">Планирование сайтов и URL-адресов для межсайтовой публикации. </span><span class="sxs-lookup"><span data-stu-id="2dbf9-111">Design sites and URLs for cross-site publishing.</span></span> 
    
- <span data-ttu-id="2dbf9-112">Разработка среды Azure. </span><span class="sxs-lookup"><span data-stu-id="2dbf9-112">Design the Azure environment.</span></span> 
    
## <a name="design-and-size-the-farm-topology"></a><span data-ttu-id="2dbf9-113">Разработка и выбор размера топологии фермы</span><span class="sxs-lookup"><span data-stu-id="2dbf9-113">Design and size the farm topology</span></span>

<span data-ttu-id="2dbf9-114">Создание топологии фермы с помощью топологии, емкости и руководств по производительности для SharePoint 2013 на сайте TechNet.</span><span class="sxs-lookup"><span data-stu-id="2dbf9-114">Use the topology, capacity, and performance guidance for SharePoint 2013 on TechNet to design the farm topology.</span></span> 
  
<span data-ttu-id="2dbf9-115">Необходимо, чтобы разрабатываемая вами ферма соответствовала требованиям к мощности и производительности. </span><span class="sxs-lookup"><span data-stu-id="2dbf9-115">Ensure the farm you design meets the objectives for capacity and performance.</span></span> 
  
### <a name="example-medium-internet-sites-farm-85-page-views-per-second"></a><span data-ttu-id="2dbf9-116">Пример: ферма среднего размера для веб-сайтов (около 85 просмотров страниц в секунду)</span><span class="sxs-lookup"><span data-stu-id="2dbf9-116">Example: Medium Internet Sites farm (~85 page views per second)</span></span>

<span data-ttu-id="2dbf9-117">Эта ферма предоставляет отказоустойчивую топологию фермы поиска SharePoint 2013, оптимизированную для собрании, содержащего 3 400 000 элементов.</span><span class="sxs-lookup"><span data-stu-id="2dbf9-117">This farm provides a fault-tolerant SharePoint 2013 search farm topology that is optimized for a corpus that contains 3,400,000 items.</span></span> 
  
<span data-ttu-id="2dbf9-118">В примере ферма обрабатывает 100-200 документов в секунду, в зависимости от языка, а также поддерживает представления страниц 85 в секунду и запросы 100 в секунду.</span><span class="sxs-lookup"><span data-stu-id="2dbf9-118">The example farm processes 100-200 documents per second, depending on the language, and it accommodates 85 page views per second and 100 queries per second.</span></span> 
  
<span data-ttu-id="2dbf9-119">На сопроводительной схеме показана ферма среднего размера для веб-сайтов с тремя указанными ниже типами серверов. </span><span class="sxs-lookup"><span data-stu-id="2dbf9-119">The accompanying diagram shows a medium internet sites farm with three types of servers:</span></span> 
  
- <span data-ttu-id="2dbf9-120">Веб-серверы</span><span class="sxs-lookup"><span data-stu-id="2dbf9-120">Web servers</span></span> 
    
- <span data-ttu-id="2dbf9-121">Серверы приложений</span><span class="sxs-lookup"><span data-stu-id="2dbf9-121">Application servers</span></span> 
    
- <span data-ttu-id="2dbf9-122">Серверы баз данных</span><span class="sxs-lookup"><span data-stu-id="2dbf9-122">Database servers</span></span> 
    
#### <a name="web-servers"></a><span data-ttu-id="2dbf9-123">Веб-серверы</span><span class="sxs-lookup"><span data-stu-id="2dbf9-123">Web servers</span></span>

<span data-ttu-id="2dbf9-p102">В разделе веб-серверов имеются три веб-сервера: "Узел A", "Узел B" и "Узел C". На каждом веб-сервере есть распределенный кэш, профили пользователей, управляемые метаданные и средства обработки запросов. Кроме того, они содержат реплику раздела индекса, имеющегося в каждом сервере.  </span><span class="sxs-lookup"><span data-stu-id="2dbf9-p102">In the web servers section, there are three web servers, Host A, Host B, and Host C. Each web server contains a distributed cache, user profiles, managed metadata, and query processing capabilities. They also contain an index partition replica that is in each server.</span></span> 
  
<span data-ttu-id="2dbf9-126">Для горизонтального масштабирования службы добавьте дополнительный веб-сервер с такими же возможностями, позволяющий увеличить скорость обработки на 28 просмотров страниц в секунду. </span><span class="sxs-lookup"><span data-stu-id="2dbf9-126">To scale out, add an additional web server with the same capabilities, which allows for an additional 28 page views per second.</span></span> 
  
#### <a name="application-servers"></a><span data-ttu-id="2dbf9-127">Серверы приложений</span><span class="sxs-lookup"><span data-stu-id="2dbf9-127">Application servers</span></span>

<span data-ttu-id="2dbf9-p103">В разделе серверов приложений есть три сервера приложений: "Узел D", "Узел E" и "Узел F". "Узел D" содержит компоненты обхода контента, администрирования, аналитики и обработки контента. "Узел E" содержит компоненты обхода контента, администрирования и обработки контента. "Узел F" содержит компоненты обхода и обработки контента. </span><span class="sxs-lookup"><span data-stu-id="2dbf9-p103">In the application servers section, there are three application servers, Host D, Host E, and Host F. Host D contains Crawl, Admin, Analytics, and Content processing components. Host E contains Crawl, Admin, and Content processing components. Host F contains Crawl and Content processing components.</span></span> 
  
<span data-ttu-id="2dbf9-131">Для горизонтального масштабирования службы добавьте один сервер приложений с компонентами обхода и обработки контента, чтобы увеличить скорость обработки на 40 документов в секунду. </span><span class="sxs-lookup"><span data-stu-id="2dbf9-131">To scale out, add one application server with a crawl component and a content processing component to process an additional 40 documents per second.</span></span> 
  
#### <a name="database-servers"></a><span data-ttu-id="2dbf9-132">Серверы баз данных</span><span class="sxs-lookup"><span data-stu-id="2dbf9-132">Database servers</span></span>

<span data-ttu-id="2dbf9-133">В разделе серверов баз данных имеются два сервера: "Узел G" и "Узел H". Для обеспечения отказоустойчивости серверы баз данных располагаются в сопряженных узлах. </span><span class="sxs-lookup"><span data-stu-id="2dbf9-133">In the database servers section, there are two servers, Host G and Host H. The database servers are in paired hosts for fault tolerance.</span></span> 
  
<span data-ttu-id="2dbf9-p104">"Узел G" содержит все базы данных SharePoint, включая базу данных администрирования поиска, базу данных ссылок, две базы данных обхода контента, базу данных аналитики и все остальные базы данных SharePoint. "Узел H" содержит все базы данных SharePoint, включая избыточные копии всех баз данных, использующих кластеризацию и зеркальное отображение SQL или SQL Server 2012 AlwaysOn. </span><span class="sxs-lookup"><span data-stu-id="2dbf9-p104">Host G contains all SharePoint database, including Search admin database, Link database, two Crawl databases, an Analytics database, and all other SharePoint databases. Host H contains all SharePoint databases, including redundant copies of all databases using SQL clustering, mirroring, or SQL Server 2012 AlwaysOn.</span></span> 
  
## <a name="fine-tune-for-azure"></a><span data-ttu-id="2dbf9-136">Настройка для Azure</span><span class="sxs-lookup"><span data-stu-id="2dbf9-136">Fine-tune for Azure</span></span>

<span data-ttu-id="2dbf9-p105">Возможно, вам потребуется настроить ферму SharePoint для групп доступности на платформе Azure. Чтобы обеспечить высокую доступность всех компонентов, убедитесь, что все роли серверов настроены одинаково.</span><span class="sxs-lookup"><span data-stu-id="2dbf9-p105">The SharePoint farm might need to be fine-tuned for availability sets in the Azure platform. To ensure high availability of all components, ensure that the server roles are all identically configured.</span></span> 
  
<span data-ttu-id="2dbf9-139">В примере топологии на схеме: </span><span class="sxs-lookup"><span data-stu-id="2dbf9-139">In the example topology in the diagram:</span></span> 
  
- <span data-ttu-id="2dbf9-140">веб-серверы и серверы баз данных настроены одинаково; </span><span class="sxs-lookup"><span data-stu-id="2dbf9-140">The web servers and the database servers are identically configured.</span></span> 
    
- <span data-ttu-id="2dbf9-p106">три сервера приложений настроены по-разному. Необходимо настроить эти роли серверов для групп доступности в Azure.</span><span class="sxs-lookup"><span data-stu-id="2dbf9-p106">The three application servers are not identically configured. These server roles require fine tuning for availability sets in Azure.</span></span> 
    
### <a name="before"></a><span data-ttu-id="2dbf9-143">До</span><span class="sxs-lookup"><span data-stu-id="2dbf9-143">Before</span></span>

<span data-ttu-id="2dbf9-p107">В верхней части схемы показана ферма SharePoint до ее настройки для групп доступности в Azure. На схеме три сервера приложений настроены по-разному. Количество компонентов определяется требуемыми производительностью и мощностью фермы. Эти три сервера настроены указанным ниже образом. </span><span class="sxs-lookup"><span data-stu-id="2dbf9-p107">The top portion of the diagram shows the SharePoint farm before it has been fine-tuned for availability sets in Azure. In the diagram, the three host application servers are not identically configured. The number of components is determined by the performance and capacity targets for the farm. The three servers are configured as follows:</span></span> 
  
- <span data-ttu-id="2dbf9-148">Для сервера приложений "Узел D" настроены роли обхода контента, администрирования, аналитики и обработки контента. </span><span class="sxs-lookup"><span data-stu-id="2dbf9-148">Host D application server is configured with Crawl, Admin, Analytics, and Content processing roles.</span></span> 
    
- <span data-ttu-id="2dbf9-149">Для сервера приложений "Узел E" настроены роли обхода контента, администрирования и обработки контента. </span><span class="sxs-lookup"><span data-stu-id="2dbf9-149">Host E application server is configured with Crawl, Admin, and Content processing roles.</span></span> 
    
- <span data-ttu-id="2dbf9-150">Для сервера приложений "Узел F" настроены роли обхода и обработки контента. </span><span class="sxs-lookup"><span data-stu-id="2dbf9-150">Host F application server is configured with Crawl and Content processing roles.</span></span> 
    
### <a name="after"></a><span data-ttu-id="2dbf9-151">After</span><span class="sxs-lookup"><span data-stu-id="2dbf9-151">After</span></span>

<span data-ttu-id="2dbf9-152">На этой части схемы показана ферма SharePoint после ее настройки для групп доступности в Azure.</span><span class="sxs-lookup"><span data-stu-id="2dbf9-152">This part of the diagram shows the SharePoint farm after it has been fine-tuned for availability sets in Azure.</span></span> <span data-ttu-id="2dbf9-153">Чтобы адаптировать эту архитектуру для Azure, мы реплицируем четыре компонента на всех трех серверах.</span><span class="sxs-lookup"><span data-stu-id="2dbf9-153">To adapt this architecture for Azure, we'll replicate the four components across all three servers.</span></span> <span data-ttu-id="2dbf9-154">Таким образом, количество компонентов будет превышать необходимое.</span><span class="sxs-lookup"><span data-stu-id="2dbf9-154">This increases the number of components beyond what is necessary for performance and capacity.</span></span> <span data-ttu-id="2dbf9-155">Выгода состоит в том, что такая схема обеспечивает высокую доступность всех четырех компонентов на платформе Azure, если эти три виртуальные машины добавлены в группу доступности.</span><span class="sxs-lookup"><span data-stu-id="2dbf9-155">The tradeoff is that this design ensures high availability of all four components in the Azure platform when these three virtual machines are assigned to an availability set.</span></span> 
  
<span data-ttu-id="2dbf9-156">Все три сервера имеют роли обхода контента, администрирования, аналитики и обработки контента. </span><span class="sxs-lookup"><span data-stu-id="2dbf9-156">The three servers are configured to all have the Crawl, Admin, Analytics, and Content processing roles.</span></span> 
  
## <a name="choose-the-active-directory-model"></a><span data-ttu-id="2dbf9-157">Выбор модели Active Directory</span><span class="sxs-lookup"><span data-stu-id="2dbf9-157">Choose the Active Directory model</span></span>

<span data-ttu-id="2dbf9-p109">Для всех решений SharePoint требуются доменные службы Windows Active Directory. В настоящий момент существует два варианта решений SharePoint в Azure.  </span><span class="sxs-lookup"><span data-stu-id="2dbf9-p109">All SharePoint solutions require Windows Active Directory Domain Services (AD DS). At this time, there are two options for SharePoint solutions in Azure.</span></span> 
  
- <span data-ttu-id="2dbf9-160">Вариант 1: выделенный домен — вы можете развернуть выделенный и изолированный домен в Azure для поддержки фермы SharePoint.</span><span class="sxs-lookup"><span data-stu-id="2dbf9-160">Option 1: Dedicated domain — You can deploy a dedicated and isolated domain to Azure to support a SharePoint farm.</span></span> <span data-ttu-id="2dbf9-161">Этот вариант хорошо подходит для общедоступных сайтов в Интернете.</span><span class="sxs-lookup"><span data-stu-id="2dbf9-161">This is a good choice for public-facing Internet sites.</span></span> 
    
- <span data-ttu-id="2dbf9-162">Вариант 2: расширение локального домена через VPN-подключение типа "сеть-сеть".</span><span class="sxs-lookup"><span data-stu-id="2dbf9-162">Option 2: Extend the on-premises domain through a site-to-site VPN connection.</span></span> <span data-ttu-id="2dbf9-163">При расширении локального домена с помощью VPN-подключения типа "сеть-сеть" пользователи получают доступ к ферме SharePoint так, будто она размещена локально.</span><span class="sxs-lookup"><span data-stu-id="2dbf9-163">When you extend the on-premises domain through a site-to-site VPN connection, users access the SharePoint farm as if it were hosted on-premises.</span></span> <span data-ttu-id="2dbf9-164">Вы можете воспользоваться преимуществами существующей реализации Active Directory и DNS.</span><span class="sxs-lookup"><span data-stu-id="2dbf9-164">You can take advantage of your existing Active Directory and DNS implementations.</span></span> 
    
## <a name="design-for-identity-management-zones-and-authentication"></a><span data-ttu-id="2dbf9-165">Планирование функций управления удостоверениями, работы с зонами и проверки подлинности</span><span class="sxs-lookup"><span data-stu-id="2dbf9-165">Design for identity management, zones, and authentication</span></span>

### <a name="design-for-accounts-and-authentication"></a><span data-ttu-id="2dbf9-166">Учетные записи и проверка подлинности</span><span class="sxs-lookup"><span data-stu-id="2dbf9-166">Design for accounts and authentication</span></span>

<span data-ttu-id="2dbf9-167">Определите, как будет выполняться управление учетными записями и какой тип проверки подлинности будет использоваться. </span><span class="sxs-lookup"><span data-stu-id="2dbf9-167">Determine how accounts will be managed and which type of authentication will be used.</span></span> 
  
#### <a name="accounts-for-site-developers-and-authors"></a><span data-ttu-id="2dbf9-168">Учетные записи для разработчиков сайта и авторов</span><span class="sxs-lookup"><span data-stu-id="2dbf9-168">Accounts for site developers and authors</span></span>

- <span data-ttu-id="2dbf9-169">Добавьте учетные записи к домену в Azure. </span><span class="sxs-lookup"><span data-stu-id="2dbf9-169">Add accounts to the domain in Azure.</span></span> 
    
- <span data-ttu-id="2dbf9-170">Используйте локальные службы федерации Active Directory для создания федерации внутренних учетных записей с доменом в Azure. </span><span class="sxs-lookup"><span data-stu-id="2dbf9-170">Use Active Directory Federation Services (AD FS) on premises to federate the internal accounts to the domain in Azure.</span></span> 
    
- <span data-ttu-id="2dbf9-171">Если схема включает VPN-подключение типа "сеть-сеть", используйте внутренние учетные записи. </span><span class="sxs-lookup"><span data-stu-id="2dbf9-171">If the design includes a site-to-site VPN connection, use the internal accounts.</span></span> 
    
#### <a name="accounts-for-customers"></a><span data-ttu-id="2dbf9-172">Учетные записи для клиентов</span><span class="sxs-lookup"><span data-stu-id="2dbf9-172">Accounts for customers</span></span>

- <span data-ttu-id="2dbf9-173">Используйте Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="2dbf9-173">Use Azure Active Directory.</span></span> 
    
- <span data-ttu-id="2dbf9-174">Используйте другого поставщика на основе SAML. </span><span class="sxs-lookup"><span data-stu-id="2dbf9-174">Use a different SAML-based provider.</span></span> 
    
### <a name="design-for-zones"></a><span data-ttu-id="2dbf9-175">Зоны</span><span class="sxs-lookup"><span data-stu-id="2dbf9-175">Design for zones</span></span>

<span data-ttu-id="2dbf9-176">В SharePoint 2013 управление удостоверениями учитывается в конфигурации зон и при проверке подлинности. </span><span class="sxs-lookup"><span data-stu-id="2dbf9-176">In SharePoint 2013, identity management is factored into the configuration of zones and authentication.</span></span> 
  
<span data-ttu-id="2dbf9-177">Такая схема обеспечивает четкое отделение учетных записей клиентов от всех остальных учетных записей. </span><span class="sxs-lookup"><span data-stu-id="2dbf9-177">This design provides clear separation of customer accounts from all other accounts.</span></span> 
  
- <span data-ttu-id="2dbf9-178">Используйте эту схему, если необходимо обрабатывать учетные записи клиентов совершенно другим способом, чем внутренние учетные записи для авторов и разработчиков сайта. </span><span class="sxs-lookup"><span data-stu-id="2dbf9-178">Use this design if you want customer accounts to be treated entirely different from the internal accounts for authors and site developers.</span></span> 
    
- <span data-ttu-id="2dbf9-179">Эта схема позволяет использовать политики зон для ограничения действий клиентов в веб- приложении. </span><span class="sxs-lookup"><span data-stu-id="2dbf9-179">By using this design, you can use zone policies to limit customer actions within a web application.</span></span> 
    
- <span data-ttu-id="2dbf9-180">При использовании этой схемы учетные записи клиентов и внутренние учетные записи будут иметь разные URL-адреса. </span><span class="sxs-lookup"><span data-stu-id="2dbf9-180">This design results in different URLs for customer accounts and internal accounts.</span></span> 
    
<span data-ttu-id="2dbf9-181">В этом примере:</span><span class="sxs-lookup"><span data-stu-id="2dbf9-181">In this example:</span></span> 
  
- <span data-ttu-id="2dbf9-182">настройка зоны по умолчанию для внутренних учетных записей;</span><span class="sxs-lookup"><span data-stu-id="2dbf9-182">Configure the default zone for internal accounts.</span></span> 
    
- <span data-ttu-id="2dbf9-p112">настройка зоны экстрасети для доступа клиентов с проверкой подлинности. Для учетных записей клиентов используйте службу Microsoft Azure Active Directory или другого поставщика на основе SAML; </span><span class="sxs-lookup"><span data-stu-id="2dbf9-p112">Configure the extranet zone for customer authenticated access. Use Azure Active Directory (AD) for customer accounts, or use a different SAML-based provider.</span></span> 
    
- <span data-ttu-id="2dbf9-185">настройка зоны Интернета для анонимного доступа.</span><span class="sxs-lookup"><span data-stu-id="2dbf9-185">Configure the Internet zone for anonymous access.</span></span> 
    
<span data-ttu-id="2dbf9-186">Не используйте конструкцию с двумя зонами, в которой все пользователи, прошедшие проверку подлинности, настроены для использования зоны по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="2dbf9-186">Don't use a two-zone design in which all authenticated users are configured to use the default zone.</span></span> 
  
<span data-ttu-id="2dbf9-187">На сопроводительной схеме показана схема с тремя зонами и отделением внутренних учетных записей от учетных записей клиентов.  </span><span class="sxs-lookup"><span data-stu-id="2dbf9-187">The accompanying diagram shows a three-zone design with separation of internal and customer accounts.</span></span> 
  
<span data-ttu-id="2dbf9-188">Посетители и клиенты получают доступ к клиенту Azure AD в ферме SharePoint 2013 через веб-приложения в одной из двух зон.</span><span class="sxs-lookup"><span data-stu-id="2dbf9-188">Visitors and customers access the Azure AD Tenant in the SharePoint 2013 farm through web applications in one of two zones.</span></span> <span data-ttu-id="2dbf9-189">Ниже перечислены эти две зоны.</span><span class="sxs-lookup"><span data-stu-id="2dbf9-189">The two zones include:</span></span> 
  
- <span data-ttu-id="2dbf9-190">Зона: Интернет для анонимных пользователей </span><span class="sxs-lookup"><span data-stu-id="2dbf9-190">Zone: Internet for anonymous users</span></span> 
    
- <span data-ttu-id="2dbf9-191">Зона: экстрасеть для пользователей, прошедших проверку подлинности </span><span class="sxs-lookup"><span data-stu-id="2dbf9-191">Zone: Extranet for authenticated users</span></span> 
    
<span data-ttu-id="2dbf9-p114">Пользователи с внутренними учетными записями получают доступ к клиенту Azure Active Directory из доменных служб Active Directory и служб федерации Active Directory в локальной среде через VPN-туннель к Azure Active Directory. Зона по умолчанию обеспечивает проверку подлинности Windows (NTLM). </span><span class="sxs-lookup"><span data-stu-id="2dbf9-p114">Users with internal accounts access the Azure Active Directory Tenant from AD DS and AD FS in the on-premises environment through the VPN tunnel to Azure AD. The Default zone provides Windows Authentication (NTLM).</span></span> 
  
### <a name="design-for-connecting-to-azure-ad"></a><span data-ttu-id="2dbf9-194">Подключение к Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="2dbf9-194">Design for connecting to Azure AD</span></span>

 <span data-ttu-id="2dbf9-p115">Служба Azure Active Directory предоставляет возможности управления удостоверениями и доступом для облачных служб. Вы сможете использовать облачное хранилище для данных каталогов и базовый набор служб идентификации, в том числе процессы входа пользователей и службы проверки подлинности, а также службы федерации Active Directory. Службы идентификации, входящие в состав Azure Active Directory, можно легко интегрировать с локальными развертываниями доменных служб Active Directory. Они обеспечивают полную поддержку сторонних поставщиков удостоверений.</span><span class="sxs-lookup"><span data-stu-id="2dbf9-p115">Azure AD provides identity management and access control capabilities for cloud services. Capabilities include a cloud-based store for directory data and a core set of identity services, including user logon processes, authentication services, and AD FS. The identity services that are included with Azure AD easily integrate with your on-premises AD DS deployments and fully support third-party identity providers.</span></span>
  
<span data-ttu-id="2dbf9-198">На сопроводительной схеме показан указанный ниже сценарий. </span><span class="sxs-lookup"><span data-stu-id="2dbf9-198">The accompanying diagram shows the following scenario:</span></span> 
  
<span data-ttu-id="2dbf9-199">При интеграции SharePoint 2013 с Azure Active Directory служба контроля доступа Azure (ACS) выполняет две задачи:</span><span class="sxs-lookup"><span data-stu-id="2dbf9-199">When integrating SharePoint 2013 with Azure Active Directory, an Azure Access Control Service (ACS) serves two purposes:</span></span> 
  
-  <span data-ttu-id="2dbf9-p116"> Azure Active Directory использует SAML 2.0, а SharePoint поддерживает только SAML 1.1. Служба контроля доступа поддерживает оба формата и выступает в роли посредника, преобразовывая форматы маркеров, передаваемых между SharePoint и Azure AD.   </span><span class="sxs-lookup"><span data-stu-id="2dbf9-p116">Azure AD uses SAML 2.0, and SharePoint only works with SAML 1.1. ACS understands both formats and serves as the intermediary to transform the token formats between SharePoint and Azure AD.</span></span>
    
- <span data-ttu-id="2dbf9-202">Служба контроля доступа позволяет не использовать службу маркеров безопасности поставщика удостоверений (IP-STS) для этого сценария SAML. </span><span class="sxs-lookup"><span data-stu-id="2dbf9-202">ACS replaces the need for the identity provider security token service (IP-STS) for this SAML scenario.</span></span> 
    
<span data-ttu-id="2dbf9-203">Дополнительные сведения см. в статье "Настройка Azure Active Directory с SharePoint 2013" в библиотеке TechNet. </span><span class="sxs-lookup"><span data-stu-id="2dbf9-203">For more information, see Configure Azure AD with SharePoint 2013 in the TechNet library.</span></span> 
  
## <a name="design-sites-and-urls-for-cross-site-publishing"></a><span data-ttu-id="2dbf9-204">Планирование сайтов и URL-адресов для межсайтовой публикации</span><span class="sxs-lookup"><span data-stu-id="2dbf9-204">Design sites and URLs for cross-site publishing</span></span>

<span data-ttu-id="2dbf9-205">Схема с одним веб-приложением рекомендуется для сценариев публикации. </span><span class="sxs-lookup"><span data-stu-id="2dbf9-205">A one web-application design is recommended for publishing scenarios.</span></span> 
  
- <span data-ttu-id="2dbf9-206">Сайты разработки и публикации находятся в одном и том же веб-приложении. </span><span class="sxs-lookup"><span data-stu-id="2dbf9-206">Both authoring and publishing sites are in the same web application.</span></span> 
    
- <span data-ttu-id="2dbf9-207">Для публикации активов используется функция межсайтовой публикации. </span><span class="sxs-lookup"><span data-stu-id="2dbf9-207">Cross-site publishing is used to publish assets.</span></span> 
    
<span data-ttu-id="2dbf9-208">Использование семейств веб-сайтов с именами на основе путей и узлов.</span><span class="sxs-lookup"><span data-stu-id="2dbf9-208">Use path-based and host-named site collections.</span></span> 
  
- <span data-ttu-id="2dbf9-p117">Необходимо корневое семейство веб-сайтов. Создайте его в виде сайта с именем на основе пути. </span><span class="sxs-lookup"><span data-stu-id="2dbf9-p117">A root site collection is a requirement. Create this site as a path-based site.</span></span> 
    
- <span data-ttu-id="2dbf9-211">Создайте все остальные семейства веб-сайтов с именами на основе узла. </span><span class="sxs-lookup"><span data-stu-id="2dbf9-211">Create all other site collections as host-named site collections.</span></span> 
    
<span data-ttu-id="2dbf9-212">URL-адреса веб-приложения и корневого сайта </span><span class="sxs-lookup"><span data-stu-id="2dbf9-212">Web application and root site URLs</span></span> 
  
- <span data-ttu-id="2dbf9-p118">В качестве URL-адреса веб-приложения используйте внутреннее имя. В качестве имени по умолчанию SharePoint использует имя локальной машины, если не указано другое имя. Вы можете использовать доменное имя, зарезервированное для внутренней сетевой среды.  </span><span class="sxs-lookup"><span data-stu-id="2dbf9-p118">Use an internal name for the web application URL. SharePoint uses the local machine name as the default name unless a different name is specified. You can use a domain name that is reserved for the internal network environment.</span></span> 
    
- <span data-ttu-id="2dbf9-p119">При создании веб-приложения SharePoint назначает нестандартный номер порта. Используйте этот номер порта вместо порта 80 или 443. Кроме того, можно использовать другой нестандартный номер порта. </span><span class="sxs-lookup"><span data-stu-id="2dbf9-p119">SharePoint assigns a nonstandard port number when the web application is created. Use this port number instead of port 80 or port 443. Or use a different but nonstandard port number.</span></span> 
    
- <span data-ttu-id="2dbf9-219">Используйте те же имя и номер порта для корневого семейства веб-сайтов с именем на основе пути. </span><span class="sxs-lookup"><span data-stu-id="2dbf9-219">Use the same name and port number for the root site collection, which is a path-based site collection.</span></span> 
    
<span data-ttu-id="2dbf9-p120">На сопроводительной схеме показаны службы пула приложений (например, служба поиска), взаимодействующие с семействами веб-сайтов с помощью веб-приложений. Ниже перечислены показанные на схеме семейства веб-сайтов. </span><span class="sxs-lookup"><span data-stu-id="2dbf9-p120">The accompanying diagram shows application pool services such as Search interacting with site collections using web applications. The site collections shown include:</span></span> 
  
- <span data-ttu-id="2dbf9-222">Семейство сайтов на основе пути, расположенное в https://internal:8000 каталоге (корневой сайт).</span><span class="sxs-lookup"><span data-stu-id="2dbf9-222">Path-based site collection located at https://internal:8000 (root site).</span></span> 
    
- <span data-ttu-id="2dbf9-223">Обход: семейства сайтов с именем на основе узла, расположенные по https://authoring.contoso.com:8000адресу, например.</span><span class="sxs-lookup"><span data-stu-id="2dbf9-223">Crawl: Host-named site collections located at an address such as https://authoring.contoso.com:8000.</span></span> 
    
- <span data-ttu-id="2dbf9-224">Запросы Два отдельных семейства веб-сайтов с именами на основе узлов, расположенные, например, по указанным ниже адресам. </span><span class="sxs-lookup"><span data-stu-id="2dbf9-224">Queries: 2 separate Host-named site collections located at addresses such as:</span></span> 
    
  - https://www.contoso.com 
    
  - https://secure.contoso.com 
    
  - https://www.contoso.com:8000 
    
  - https://assets.contoso.com 
    
  - https://secureassets.contoso.com 
    
  - https://assets.contoso.com:8000 
    
## <a name="design-the-azure-environment"></a><span data-ttu-id="2dbf9-225">Разработка среды Azure</span><span class="sxs-lookup"><span data-stu-id="2dbf9-225">Design the Azure environment</span></span>

<span data-ttu-id="2dbf9-226">Этот пример архитектуры включает указанные ниже элементы. </span><span class="sxs-lookup"><span data-stu-id="2dbf9-226">This example architecture includes the following elements:</span></span> 
  
- <span data-ttu-id="2dbf9-227">Необязательное VPN-подключение типа "сеть-сеть" позволяет расширить локальную среду доменных служб Active Directory и DNS, связав ее с виртуальной сетью в Azure. </span><span class="sxs-lookup"><span data-stu-id="2dbf9-227">A site-to-site VPN connection is optional and extends the on-premises Windows AD DS and DNS environment to the virtual network in Azure.</span></span> 
    
- <span data-ttu-id="2dbf9-228">При желании для поддержки фермы SharePoint можно использовать выделенный домен в Azure. </span><span class="sxs-lookup"><span data-stu-id="2dbf9-228">Optionally, use a dedicated domain in Azure to support the SharePoint farm.</span></span> 
    
- <span data-ttu-id="2dbf9-229">Серверы распределены между облачными службами Azure в зависимости от их ролей. </span><span class="sxs-lookup"><span data-stu-id="2dbf9-229">Servers are split across Azure cloud services based on role.</span></span> 
    
- <span data-ttu-id="2dbf9-230">Группы доступности обеспечивают высокую доступность серверов, для которых настроены одинаковые роли.  </span><span class="sxs-lookup"><span data-stu-id="2dbf9-230">Availability sets ensure high availability of identically configured server roles.</span></span> 
    
<span data-ttu-id="2dbf9-231">Дополнительные сведения см. в следующей статье на веб-сайте TechNet: "Архитектуры Azure для решений SharePoint". </span><span class="sxs-lookup"><span data-stu-id="2dbf9-231">For more information, see the following article on TechNet: Azure Architectures for SharePoint Solutions.</span></span> 
  
<span data-ttu-id="2dbf9-232">На сопроводительной схеме показан пример локальной среды, подключенной к виртуальной сети Azure.   </span><span class="sxs-lookup"><span data-stu-id="2dbf9-232">The accompanying diagram shows an example of an on-premises environment connecting with an Azure virtual network.</span></span> 
  
<span data-ttu-id="2dbf9-233">В локальную среду, являющуюся необязательным элементом среды Azure, включены указанные ниже компоненты. </span><span class="sxs-lookup"><span data-stu-id="2dbf9-233">Included in the on-premises environment, which is an optional element of the Azure environment, are the following components:</span></span> 
  
- <span data-ttu-id="2dbf9-234">Windows Server 2012 RRAS</span><span class="sxs-lookup"><span data-stu-id="2dbf9-234">Windows Server 2012 RRAS</span></span> 
    
- <span data-ttu-id="2dbf9-235">Доменные службы Active Directory</span><span class="sxs-lookup"><span data-stu-id="2dbf9-235">AD DS</span></span> 
    
- <span data-ttu-id="2dbf9-236">VPN-шлюз, отделяющий Windows Server и доменных служб Active Directory от подсети активного VPN-шлюза </span><span class="sxs-lookup"><span data-stu-id="2dbf9-236">A VPN gateway from Windows Server and AD DS to the Active VPN Gateway subnet</span></span> 
    
<span data-ttu-id="2dbf9-237">Среда виртуальной сети Azure включает указанные ниже компоненты. </span><span class="sxs-lookup"><span data-stu-id="2dbf9-237">The Azure virtual network environment includes the following components:</span></span> 
  
- <span data-ttu-id="2dbf9-238">Подсеть активного VPN-шлюза (при необходимости перекрывающаяся с локальной средой) </span><span class="sxs-lookup"><span data-stu-id="2dbf9-238">The Active VPN Gateway subnet (overlapping with the on-premises environment, if applicable)</span></span> 
    
- <span data-ttu-id="2dbf9-239">Облачная служба, включающая доменные службы Active Directory и группу доступности DNS (два сервера) </span><span class="sxs-lookup"><span data-stu-id="2dbf9-239">Cloud service that includes AD DS and DNS availability set (two servers)</span></span> 
    
- <span data-ttu-id="2dbf9-240">Облачная служба, включающая группу доступности сервера переднего плана (три сервера SharePoint) и группу доступности сервера приложений App (три сервера SharePoint) </span><span class="sxs-lookup"><span data-stu-id="2dbf9-240">Cloud service that include the front-end server availability set (three SharePoint servers) and the App server availability set (three SharePoint servers)</span></span> 
    
- <span data-ttu-id="2dbf9-241">Облачная служба, содержащая две группы доступности баз данных </span><span class="sxs-lookup"><span data-stu-id="2dbf9-241">Cloud service that contains two database availability sets</span></span> 
    

