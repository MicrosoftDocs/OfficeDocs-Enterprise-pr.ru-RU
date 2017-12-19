---
title: "Сценарии гибридного облака для Azure PaaS"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Visuals
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: 5f4f5d0d-4638-48e8-a517-bd804856b617
description: "Сводка. Сведения о гибридной архитектуре и сценариях для облачных предложений на основе Microsoft PaaS в Azure."
ms.openlocfilehash: f6d7d1c9ca04c0b7bbaa020a771cf84734e5d385
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2017
---
# <a name="hybrid-cloud-scenarios-for-azure-paas"></a><span data-ttu-id="5bca1-103">Сценарии гибридного облака для Azure PaaS</span><span class="sxs-lookup"><span data-stu-id="5bca1-103">Hybrid cloud scenarios for Azure PaaS</span></span>

 <span data-ttu-id="5bca1-104">**Сводка.** Сведения о гибридной архитектуре и сценариях для облачных предложений на основе Microsoft PaaS в Azure.</span><span class="sxs-lookup"><span data-stu-id="5bca1-104">**Summary:** Understand the hybrid architecture and scenarios for Microsoft's Platform as a Service (PaaS)-based cloud offerings in Azure.</span></span>
  
<span data-ttu-id="5bca1-105">Объедините локальные данные или вычислительные ресурсы с новыми либо преобразованными приложениями, работающими в Azure PaaS. Это позволит воспользоваться преимуществами производительности, надежности и масштабирования облачных решений, а также улучшить поддержку пользователей мобильных приложений.</span><span class="sxs-lookup"><span data-stu-id="5bca1-105">Combine on-premises data or computing resources with new or converted applications running in Azure PaaS, which can take advantage of cloud performance, reliability, and scale and provide better support for mobile users.</span></span> 
  
## <a name="azure-paas-hybrid-scenario-architecture"></a><span data-ttu-id="5bca1-106">Архитектура гибридного сценария Azure PaaS</span><span class="sxs-lookup"><span data-stu-id="5bca1-106">Azure PaaS hybrid scenario architecture</span></span>

<span data-ttu-id="5bca1-107">На рисунке 1 показана архитектура гибридных сценариев на основе Microsoft PaaS в Azure.</span><span class="sxs-lookup"><span data-stu-id="5bca1-107">Figure 1 shows the architecture of Microsoft PaaS-based hybrid scenarios in Azure.</span></span>
  
<span data-ttu-id="5bca1-108">**Рис. 1. Гибридные сценарии на основе Microsoft PaaS в Azure**</span><span class="sxs-lookup"><span data-stu-id="5bca1-108">**Figure 1: Microsoft PaaS-based hybrid scenarios in Azure**</span></span>

![Гибридные сценарии на основе Microsoft PaaS в Azure](images/Hybrid_Poster/Hybrid_Cloud_Stack_PaaS.png)
  
<span data-ttu-id="5bca1-110">Для каждого слоя архитектуры:</span><span class="sxs-lookup"><span data-stu-id="5bca1-110">For each layer of the architecture:</span></span>
  
- <span data-ttu-id="5bca1-111">Приложения и сценарии</span><span class="sxs-lookup"><span data-stu-id="5bca1-111">Apps and scenarios</span></span>
    
    <span data-ttu-id="5bca1-112">Гибридное приложение PaaS выполняется в Azure и использует локальные вычислительные ресурсы или ресурсы хранилища.</span><span class="sxs-lookup"><span data-stu-id="5bca1-112">A hybrid PaaS application runs in Azure and uses on-premises compute or storage resources.</span></span>
    
- <span data-ttu-id="5bca1-113">Удостоверение</span><span class="sxs-lookup"><span data-stu-id="5bca1-113">Identity</span></span>
    
    <span data-ttu-id="5bca1-114">Включает синхронизацию службы каталогов или федерацию со сторонним поставщиком удостоверений.</span><span class="sxs-lookup"><span data-stu-id="5bca1-114">Consists of either directory synchronization or federation with a third-party identity provider.</span></span>
    
- <span data-ttu-id="5bca1-115">Сеть</span><span class="sxs-lookup"><span data-stu-id="5bca1-115">Network</span></span>
    
    <span data-ttu-id="5bca1-p101">Состоит из имеющегося интернет-канала или подключения ExpressRoute с открытым пирингом к Azure PaaS. Приложению Azure PaaS необходимо предоставить доступ к локальным вычислительным ресурсам или ресурсам хранилища.</span><span class="sxs-lookup"><span data-stu-id="5bca1-p101">Consists of either your existing Internet pipe or an ExpressRoute connection with public peering to Azure PaaS. You must include a way for the Azure PaaS application to access the on-premises compute or storage resource.</span></span>
    
- <span data-ttu-id="5bca1-118">Локальная среда</span><span class="sxs-lookup"><span data-stu-id="5bca1-118">On-premises</span></span>
    
    <span data-ttu-id="5bca1-119">Состоит из инфраструктуры удостоверений и безопасности, а также имеющихся бизнес-приложений или серверов баз данных, к которым приложение Azure PaaS может получить безопасный доступ.</span><span class="sxs-lookup"><span data-stu-id="5bca1-119">Consists of identity and security infrastructure and existing line of business (LOB) applications or database servers, which an Azure PaaS application can securely access.</span></span>
    
## <a name="azure-paas-hybrid-application"></a><span data-ttu-id="5bca1-120">Гибридное приложение Azure PaaS</span><span class="sxs-lookup"><span data-stu-id="5bca1-120">Azure PaaS hybrid application</span></span>

<span data-ttu-id="5bca1-121">На рисунке 2 показана конфигурация гибридного приложения, выполняемого в Azure.</span><span class="sxs-lookup"><span data-stu-id="5bca1-121">Figure 2 shows the configuration of a hybrid application running in Azure.</span></span>
  
<span data-ttu-id="5bca1-122">**Рис. 2. Гибридное приложение на основе Azure PaaS**</span><span class="sxs-lookup"><span data-stu-id="5bca1-122">**Figure 2: Azure PaaS-based hybrid application**</span></span>

![Гибридное приложение на основе Azure PaaS](images/Hybrid_Poster/Hybrid_Cloud_Stack_PaaS_Apps.png)
  
<span data-ttu-id="5bca1-p102">На рисунке 2 показана локальная сеть, в которой на серверах размещаются хранилище или приложения, а также зона DMZ, содержащая прокси-сервер. Локальная сеть подключена к службам Azure PaaS через интернет-канал или с помощью подключения ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="5bca1-p102">In Figure 2, an on-premises network hosts storage or apps on servers and a DMZ containing a proxy server. It is connected to Azure PaaS services either over the Internet or with an ExpressRoute connection.</span></span>
  
<span data-ttu-id="5bca1-126">Организации могут предоставить гибридному приложению Azure PaaS доступ к своим вычислительным ресурсам или ресурсам хранилища следующими способами:</span><span class="sxs-lookup"><span data-stu-id="5bca1-126">An organization can make its compute or storage resources available to the Azure PaaS hybrid application by:</span></span>
  
- <span data-ttu-id="5bca1-127">разместив ресурсы на серверах в DMZ;</span><span class="sxs-lookup"><span data-stu-id="5bca1-127">Hosting the resource on servers in the DMZ.</span></span>
    
- <span data-ttu-id="5bca1-128">разместив обратный прокси-сервер в DMZ, что обеспечивает входящим запросам на основе HTTPS, прошедшим проверку подлинности, доступ к локальному ресурсу.</span><span class="sxs-lookup"><span data-stu-id="5bca1-128">Hosting a reverse proxy server in the DMZ, which allows authenticated, inbound, HTTPS-based requests to the resource that is located on-premises.</span></span>
    
<span data-ttu-id="5bca1-129">Приложение Azure может использовать учетные данные:</span><span class="sxs-lookup"><span data-stu-id="5bca1-129">The Azure app can use credentials from:</span></span>
  
- <span data-ttu-id="5bca1-130">из службы Azure AD, которую можно синхронизировать с локальным поставщиком удостоверений, например Windows Server AD; </span><span class="sxs-lookup"><span data-stu-id="5bca1-130">Azure AD, which can be synchronized with your on-premises identity provider, such as Windows Server AD.</span></span>
    
- <span data-ttu-id="5bca1-131">от стороннего поставщика удостоверений.</span><span class="sxs-lookup"><span data-stu-id="5bca1-131">A third-party identity provider.</span></span>
    
### <a name="example-azure-paas-hybrid-application"></a><span data-ttu-id="5bca1-132">Пример гибридного приложения Azure PaaS</span><span class="sxs-lookup"><span data-stu-id="5bca1-132">Example Azure PaaS hybrid application</span></span>

<span data-ttu-id="5bca1-133">На рисунке 3 показан пример гибридного приложения, выполняемого в Azure.</span><span class="sxs-lookup"><span data-stu-id="5bca1-133">Figure 3 shows an example hybrid application running in Azure.</span></span>
  
<span data-ttu-id="5bca1-134">**Рис. 3. Пример гибридного приложения на основе Azure PaaS**</span><span class="sxs-lookup"><span data-stu-id="5bca1-134">**Figure 3: An example Azure PaaS-based hybrid application**</span></span>

![Пример гибридного приложения на основе Azure PaaS](images/Hybrid_Poster/Hybrid_Cloud_Stack_PaaS_Apps_Ex.png)
  
<span data-ttu-id="5bca1-p103">На рисунке 3 показана локальная сеть, в которой размещается бизнес-приложение. В Azure PaaS находится настраиваемое мобильное приложение. Подключенный к Интернету смартфон получает доступ к настраиваемому мобильному приложению в Azure, которое отправляет запросы данных локальному бизнес-приложению.</span><span class="sxs-lookup"><span data-stu-id="5bca1-p103">In Figure 3, an on-premises network hosts an LOB app. Azure PaaS hosts a custom mobile app. A smartphone on the Internet accesses the custom mobile app in Azure, which sends data requests to the on-premises LOB app.</span></span>
  
<span data-ttu-id="5bca1-p104">В этом примере гибридное приложение Azure PaaS представляет собой настраиваемое мобильное приложение, которое предоставляет обновленные контактные данные сотрудников. Сквозной гибридный сценарий включает:</span><span class="sxs-lookup"><span data-stu-id="5bca1-p104">This example Azure PaaS hybrid application is a custom mobile app that provides up-to-date contact information on employees. The end-to-end hybrid scenario consists of:</span></span>
  
- <span data-ttu-id="5bca1-141">приложение для смартфона, для запуска которого требуются проверенные локальные учетные данные;</span><span class="sxs-lookup"><span data-stu-id="5bca1-141">A smartphone app that requires validated, on-premises credentials to run.</span></span>
    
- <span data-ttu-id="5bca1-142">настраиваемое мобильное приложение, выполняемое в Azure PaaS, которое запрашивает сведения о конкретных сотрудниках на основе запросов, полученных от приложения для смартфона пользователя;</span><span class="sxs-lookup"><span data-stu-id="5bca1-142">A custom mobile app running in Azure PaaS, which requests information about specific employees based on queries from a user's smartphone app.</span></span>
    
- <span data-ttu-id="5bca1-143">обратный прокси-сервер в DMZ, который проверяет настраиваемое мобильное приложение и пересылает запрос;</span><span class="sxs-lookup"><span data-stu-id="5bca1-143">A reverse proxy server in the DMZ that validates the custom mobile app and forwards the request.</span></span>
    
- <span data-ttu-id="5bca1-144">ферму серверов бизнес-приложений, которая обслуживает запрос контактных данных при наличии соответствующих разрешений в учетной записи пользователя.</span><span class="sxs-lookup"><span data-stu-id="5bca1-144">An LOB application server farm that services the contact request, subject to the permissions of the user's account.</span></span>
    
<span data-ttu-id="5bca1-145">Так как локальный поставщик удостоверений синхронизирован с Azure AD, настраиваемое мобильное приложение и бизнес-приложение могут проверить имя учетной записи пользователя, отправившего запрос.</span><span class="sxs-lookup"><span data-stu-id="5bca1-145">Because the on-premises identity provider has been synchronized with Azure AD, both the custom mobile app and the LOB app can validate the requesting user's account name.</span></span>
  
## <a name="stretch-database-with-sql-server-2016"></a><span data-ttu-id="5bca1-146">База данных Stretch с SQL Server 2016</span><span class="sxs-lookup"><span data-stu-id="5bca1-146">Stretch Database with SQL Server 2016</span></span>

<span data-ttu-id="5bca1-147">База данных Stretch — это функция SQL Server 2016, которая позволяет прозрачно и безопасно переместить редко используемые данные, например данные о закрытой компании в большой таблице со сведениями о заказах клиентов, в базу данных Stretch в SQL Azure.</span><span class="sxs-lookup"><span data-stu-id="5bca1-147">Stretch database is a feature of SQL Server 2016 that allows you to transparently and securely move cold data, such as closed business data in a large table that contains customer order information, to a SQL Stretch database in Azure.</span></span>
  
<span data-ttu-id="5bca1-p105">При использовании функции Stretch содержимое экземпляра SQL Server, база данных или даже одна таблица являются сочетанием локальных данных на сервере SQL Server 2016 и удаленных данных в Azure. SQL Server 2016 автоматически перемещает в Azure данные, которые поддерживают функцию Stretch.</span><span class="sxs-lookup"><span data-stu-id="5bca1-p105">When stretched, the contents of a SQL Server instance, a database, or even a single table is the combination of local data in SQL Server 2016 server and remote data in Azure. Data that becomes eligible for stretch is automatically moved to Azure by SQL Server 2016.</span></span>
  
<span data-ttu-id="5bca1-150">На рисунке 4 показана база данных Stretch в SQL Server 2016.</span><span class="sxs-lookup"><span data-stu-id="5bca1-150">Figure 4 shows Stretch Database with SQL Server 2016.</span></span>
  
<span data-ttu-id="5bca1-151">**Рис. 4. База данных Stretch в SQL Server 2016**</span><span class="sxs-lookup"><span data-stu-id="5bca1-151">**Figure 4: Stretch Database with SQL Server 2016**</span></span>

![База данных Stretch с SQL Server 2016](images/Hybrid_Poster/Hybrid_Cloud_Stack_PaaS_Apps_SQL.png)
  
<span data-ttu-id="5bca1-p106">На рисунке 4 показана локальная сеть, в которой размещен сервер SQL Server 2016 с небольшой локальной базой данных. В Azure PaaS размещен экземпляр растянутой базы данных Stretch сервера SQL Azure. Запросы T-SQL, отправляемые от локальных пользователей на локальный сервер SQL, безопасно перенаправляются в базу данных Stretch SQL Azure, которая возвращает результаты запросов пользователям.</span><span class="sxs-lookup"><span data-stu-id="5bca1-p106">In Figure 4, an on-premises network hosts a server running SQL Server 2016 with a small local database. Azure PaaS hosts an instance of Azure SQL Server Stretch Database with the stretched portion of the database. T-SQL queries from an on-premises user sent to the on-premises SQL server are securely forwarded to the Azure SQL Stretch Database, which returns the results to the requesting user.</span></span>
  
 <span data-ttu-id="5bca1-p107"> 

Запросы пользователей, которые содержат архивные данные, прозрачно перенаправляются в базу данных Stretch в SQL Azure. Несмотря на то что таблица растягивается, запросы не нужно записывать повторно. 

</span><span class="sxs-lookup"><span data-stu-id="5bca1-p107">User queries that include the historical data are transparently forwarded to Azure SQL Stretch database. The queries do not need to be re-written, even though the table is stretched.</span></span>
  
<span data-ttu-id="5bca1-p108">База данных Stretch представляет собой экономически эффективное решение для долгосрочного хранения архивных данных и прозрачного доступа к ним. Кроме того, она позволяет решить проблемы производительности и доступности, возникающие при значительном увеличении таблиц.</span><span class="sxs-lookup"><span data-stu-id="5bca1-p108">Stretch database provides a cost-effective option for long-term storage and transparent access to historical data. It also solves performance and availability problems that arise when tables become very large.</span></span>
  
<span data-ttu-id="5bca1-160">Дополнительные сведения см. в статье [База данных Stretch](https://msdn.microsoft.com/library/dn935011.aspx).</span><span class="sxs-lookup"><span data-stu-id="5bca1-160">For more information, see [Stretch Database](https://msdn.microsoft.com/library/dn935011.aspx).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="5bca1-161">См. также</span><span class="sxs-lookup"><span data-stu-id="5bca1-161">See Also</span></span>

[<span data-ttu-id="5bca1-162">Гибридное облако Майкрософт для корпоративных архитекторов</span><span class="sxs-lookup"><span data-stu-id="5bca1-162">Microsoft Hybrid Cloud for Enterprise Architects</span></span>](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[<span data-ttu-id="5bca1-163">Ресурсы для администраторов, посвященные архитектуре Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="5bca1-163">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="5bca1-164">Стратегия Enterprise Cloud корпорации Майкрософт: ресурсы для лиц, принимающих решения в области ИТ</span><span class="sxs-lookup"><span data-stu-id="5bca1-164">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



