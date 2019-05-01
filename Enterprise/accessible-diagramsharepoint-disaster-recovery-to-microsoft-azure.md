---
title: Доступная схема — аварийное восстановление SharePoint в Microsoft Azure
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 4b855224-8e67-4efa-a3a4-908ee0ca6412
description: Данная статья представляет собой текстовую версию схемы "Аварийное восстановление SharePoint в Microsoft Azure".
ms.openlocfilehash: 545aaae05e3becbde60fe01c0e50e5610ee69f98
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487725"
---
# <a name="accessible-diagram---sharepoint-disaster-recovery-to-microsoft-azure"></a><span data-ttu-id="bf5f9-103">Доступная схема — аварийное восстановление SharePoint в Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="bf5f9-103">Accessible diagram - SharePoint Disaster Recovery to Microsoft Azure</span></span>

<span data-ttu-id="bf5f9-104">**Сводка:** Эта статья представляет собой текстовую версию схемы с именем "аварийное восстановление SharePoint" в Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="bf5f9-104">**Summary:** This article is an accessible text version of the diagram named SharePoint Disaster Recovery to Microsoft Azure.</span></span>
  
<span data-ttu-id="bf5f9-105">На этом плакате приведены примеры архитектур, используемых для создания среды восстановления в Azure.</span><span class="sxs-lookup"><span data-stu-id="bf5f9-105">This poster provides examples of architectures for building a recovery environment in Azure.</span></span> 
  
## <a name="on-premises-environment-with-an-azure-recovery-environment"></a><span data-ttu-id="bf5f9-106">Локальная среда со средой восстановления Azure</span><span class="sxs-lookup"><span data-stu-id="bf5f9-106">On-premises environment with an Azure recovery environment</span></span>

<span data-ttu-id="bf5f9-107">На схеме показан пример архитектуры, используемой для рабочей среды, размещенной в локальной среде, в которой, в свою очередь, применяется Azure для восстановления.</span><span class="sxs-lookup"><span data-stu-id="bf5f9-107">The diagram shows an example of architecture used for the production environment of an on-premises environment that uses Azure for recovery.</span></span> 
  
### <a name="on-premises-production-environment"></a><span data-ttu-id="bf5f9-108">Локальная рабочая среда</span><span class="sxs-lookup"><span data-stu-id="bf5f9-108">On-premises production environment</span></span>

<span data-ttu-id="bf5f9-109">На сопроводительной схеме показана динамическая рабочая среда с фермой серверов, разбитой на четыре уровня.</span><span class="sxs-lookup"><span data-stu-id="bf5f9-109">The accompanying diagram shows a live production environment with four tiers of servers in a server farm.</span></span> 
  
#### <a name="tier-1"></a><span data-ttu-id="bf5f9-110">Уровень 1</span><span class="sxs-lookup"><span data-stu-id="bf5f9-110">Tier 1</span></span>

<span data-ttu-id="bf5f9-p101">На этом уровне расположены два сервера для служб переднего плана и обработки запросов. Кроме того, здесь есть раздел индекса, в котором имеются реплики обоих серверов. </span><span class="sxs-lookup"><span data-stu-id="bf5f9-p101">There are two servers for front-end services and query processing. There is an index partition that provides a replica of both servers.</span></span> 
  
#### <a name="tier-2"></a><span data-ttu-id="bf5f9-113">Уровень 2</span><span class="sxs-lookup"><span data-stu-id="bf5f9-113">Tier 2</span></span>

<span data-ttu-id="bf5f9-114">На этом уровне расположены два сервера для распределенного кэша.</span><span class="sxs-lookup"><span data-stu-id="bf5f9-114">There are two servers for distributed cache in this tier.</span></span> 
  
#### <a name="tier-3"></a><span data-ttu-id="bf5f9-115">Уровень 3</span><span class="sxs-lookup"><span data-stu-id="bf5f9-115">Tier 3</span></span>

<span data-ttu-id="bf5f9-p102">На этом уровне расположены три сервера. Каждый сервер предоставляет указанные ниже службы. </span><span class="sxs-lookup"><span data-stu-id="bf5f9-p102">There are three servers in this tier. Each server provides the following services:</span></span> 
  
- <span data-ttu-id="bf5f9-118">Внутренние службы</span><span class="sxs-lookup"><span data-stu-id="bf5f9-118">Backend services</span></span> 
    
- <span data-ttu-id="bf5f9-119">Admin</span><span class="sxs-lookup"><span data-stu-id="bf5f9-119">Admin</span></span> 
    
- <span data-ttu-id="bf5f9-120">Диспетчер бизнес-правил</span><span class="sxs-lookup"><span data-stu-id="bf5f9-120">Workflow manager</span></span> 
    
- <span data-ttu-id="bf5f9-121">Обход контента</span><span class="sxs-lookup"><span data-stu-id="bf5f9-121">Crawl</span></span> 
    
- <span data-ttu-id="bf5f9-122">Обработка контента</span><span class="sxs-lookup"><span data-stu-id="bf5f9-122">Content processing</span></span> 
    
- <span data-ttu-id="bf5f9-123">Аналитика</span><span class="sxs-lookup"><span data-stu-id="bf5f9-123">Analytics</span></span> 
    
#### <a name="tier-4"></a><span data-ttu-id="bf5f9-124">Уровень 4</span><span class="sxs-lookup"><span data-stu-id="bf5f9-124">Tier 4</span></span>

<span data-ttu-id="bf5f9-p103">На этом уровне расположены два сервера. У каждого сервера имеется три указанные ниже группы доступности. </span><span class="sxs-lookup"><span data-stu-id="bf5f9-p103">There are two servers in this tier. Both servers have three availability groups, as follows:</span></span> 
  
- <span data-ttu-id="bf5f9-127">Группа доступности 1 обеспечивает возможности поиска.</span><span class="sxs-lookup"><span data-stu-id="bf5f9-127">Availability group #1 provides search capabilities.</span></span> 
    
- <span data-ttu-id="bf5f9-128">Группа доступности 2 предоставляет контент, сведения о конфигурации и приложения-службы.</span><span class="sxs-lookup"><span data-stu-id="bf5f9-128">Availability group #2 provides content, configuration, and service applications.</span></span> 
    
- <span data-ttu-id="bf5f9-129">Группа доступности 3 предоставляет контент.</span><span class="sxs-lookup"><span data-stu-id="bf5f9-129">Availability group #3 provides content.</span></span> 
    
<span data-ttu-id="bf5f9-p104">Кроме того, на этом уровне имеется сервер для общего доступа к файлам. Для обмена данными с этим сервером серверы уровня 4 используют функцию доставки журналов. Этот сервер посредством репликации распределенной файловой системы обменивается данными с сервером для общего доступа к файлам в среде восстановления Azure с "горячим" резервированием, как описано в разделе ниже. </span><span class="sxs-lookup"><span data-stu-id="bf5f9-p104">There is also a file sharing server in this tier. The tier 4 servers use log shipping to communicate with this server. This server, in turn, communicates over Distributed File System Replication (DFSR) to a file share server in the Azure warm standby recovery environment, as described in the following section.</span></span> 
  
### <a name="azure-recovery-environment"></a><span data-ttu-id="bf5f9-133">Среда восстановления Azure</span><span class="sxs-lookup"><span data-stu-id="bf5f9-133">Azure recovery environment</span></span>

#### <a name="warm-standby-environment-running-virtual-machines"></a><span data-ttu-id="bf5f9-134">Среда с "горячим" резервированием, в которой работают виртуальные машины</span><span class="sxs-lookup"><span data-stu-id="bf5f9-134">Warm standby environment running virtual machines</span></span>

<span data-ttu-id="bf5f9-p105">На сопроводительной схеме показана локальная среда, точно реплицированная в среде восстановления Azure. В этой среде сервер для общего доступа к файлам связан с локальной средой посредством репликации распределенной файловой системы. Репликация распределенной файловой системы передает журналы из рабочей среды в среду восстановления через сервер для общего доступа к файлам. </span><span class="sxs-lookup"><span data-stu-id="bf5f9-p105">The accompanying diagram shows the on-premises environment replicated exactly in the Azure recovery environment. The file share server in this environment is linked to the on-premises environment through DFSR. DFSR transfers logs from the production environment to the recovery environment through the file share server.</span></span> 
  
### <a name="overview"></a><span data-ttu-id="bf5f9-138">Общие сведения</span><span class="sxs-lookup"><span data-stu-id="bf5f9-138">Overview</span></span>

<span data-ttu-id="bf5f9-139">Среда аварийного восстановления для локальной фермы SharePoint 2013 может быть размещена в Azure.</span><span class="sxs-lookup"><span data-stu-id="bf5f9-139">The disaster recovery environment for an on-premises SharePoint 2013 farm can be hosted in Azure.</span></span> 
  
-  <span data-ttu-id="bf5f9-140">Службы инфраструктуры Azure обеспечивают дополнительный центр данных.</span><span class="sxs-lookup"><span data-stu-id="bf5f9-140">Azure Infrastructure Services provides a secondary datacenter.</span></span>
    
- <span data-ttu-id="bf5f9-141">Вы платите только за используемые ресурсы.</span><span class="sxs-lookup"><span data-stu-id="bf5f9-141">Pay only for the resources you use.</span></span> 
    
- <span data-ttu-id="bf5f9-142">Чтобы соблюсти требования к масштабу и емкости, после аварии можно развернуть небольшие фермы восстановления.</span><span class="sxs-lookup"><span data-stu-id="bf5f9-142">Small recovery farms can be scaled out after a disaster to meet scale and capacity targets.</span></span> 
    
<span data-ttu-id="bf5f9-143">Ферма восстановления в Azure настраивается (насколько это возможно) так же, как и рабочая локальная ферма.</span><span class="sxs-lookup"><span data-stu-id="bf5f9-143">The recovery farm in Azure is configured as identically as possible to the production on-premises farm.</span></span> 
  
- <span data-ttu-id="bf5f9-144">Одинаковое представление ролей серверов.</span><span class="sxs-lookup"><span data-stu-id="bf5f9-144">Same representation of server roles.</span></span> 
    
- <span data-ttu-id="bf5f9-145">Одинаковая конфигурация настроек.</span><span class="sxs-lookup"><span data-stu-id="bf5f9-145">Same configuration of customizations.</span></span> 
    
- <span data-ttu-id="bf5f9-146">Одинаковая конфигурация компонентов поиска (они могут размещаться на рабочей ферме меньшей версии).</span><span class="sxs-lookup"><span data-stu-id="bf5f9-146">Same configuration of search features (these can be on a smaller version of the production farm).</span></span> 
    
<span data-ttu-id="bf5f9-147">Доставка журналов и репликация распределенной файловой системы используются для копирования резервных копий баз данных и журналов транзакций в ферму Azure.</span><span class="sxs-lookup"><span data-stu-id="bf5f9-147">Log shipping and DFSR are used to copy database backups and transaction logs to the Azure farm.</span></span> 
  
- <span data-ttu-id="bf5f9-p106">Репликация распределенной файловой системы используется для передачи журналов из рабочей среды в среду восстановления. В глобальной сети сценарий с использованием репликации распределенной файловой системы более эффективен, чем доставка журналов непосредственно на дополнительный сервер в Azure.</span><span class="sxs-lookup"><span data-stu-id="bf5f9-p106">DFSR is used to transfer logs from the production environment to the recovery environment. In a WAN scenario, DFSR is more efficient than shipping the logs directly to the secondary server in Azure.</span></span> 
    
- <span data-ttu-id="bf5f9-150">Журналы воспроизводятся на компьютерах под управлением SQL Server на основе Azure.</span><span class="sxs-lookup"><span data-stu-id="bf5f9-150">Logs are replayed to the Azure-based SQL Server computers.</span></span> 
    
- <span data-ttu-id="bf5f9-151">Базы данных, доставленные с журналами, не прикрепляются к ферме, пока не будет выполнено восстановление.</span><span class="sxs-lookup"><span data-stu-id="bf5f9-151">Log-shipped databases are not attached to the farm until a recovery exercise is performed.</span></span> 
    
<span data-ttu-id="bf5f9-152">Процедуры отработки отказа.</span><span class="sxs-lookup"><span data-stu-id="bf5f9-152">Failover procedures:</span></span> 
  
1. <span data-ttu-id="bf5f9-153">Остановите доставку журналов.</span><span class="sxs-lookup"><span data-stu-id="bf5f9-153">Stop log shipping.</span></span> 
    
2. <span data-ttu-id="bf5f9-154">Остановите прием трафика основной фермы.</span><span class="sxs-lookup"><span data-stu-id="bf5f9-154">Stop accepting traffic to the primary farm.</span></span> 
    
3. <span data-ttu-id="bf5f9-155">Воспроизведите журналы транзакций.</span><span class="sxs-lookup"><span data-stu-id="bf5f9-155">Replay the final transaction logs.</span></span> 
    
4. <span data-ttu-id="bf5f9-156">Присоедините базу данных контента к ферме.</span><span class="sxs-lookup"><span data-stu-id="bf5f9-156">Attach the content databases to the farm.</span></span> 
    
5. <span data-ttu-id="bf5f9-157">Запустите полный обход.</span><span class="sxs-lookup"><span data-stu-id="bf5f9-157">Start a full crawl.</span></span> 
    
6. <span data-ttu-id="bf5f9-158">Восстановите приложения-службы из служб реплицированных баз данных.</span><span class="sxs-lookup"><span data-stu-id="bf5f9-158">Restore service applications from the replicated services databases.</span></span> 
    
<span data-ttu-id="bf5f9-159">Ниже перечислены цели восстановления для этого решения.</span><span class="sxs-lookup"><span data-stu-id="bf5f9-159">Recovery objectives provided by this solution include:</span></span> 
  
- <span data-ttu-id="bf5f9-160">Сайты и контент</span><span class="sxs-lookup"><span data-stu-id="bf5f9-160">Sites and content</span></span> 
    
- <span data-ttu-id="bf5f9-161">Поиск (повторный обход контента, без журнала поиска)</span><span class="sxs-lookup"><span data-stu-id="bf5f9-161">Search (re-crawled, no search history)</span></span> 
    
- <span data-ttu-id="bf5f9-162">Службы</span><span class="sxs-lookup"><span data-stu-id="bf5f9-162">Services</span></span>
    
<span data-ttu-id="bf5f9-163">С помощью консультационных служб или партнеров корпорации Майкрософт можно решить указанные ниже дополнительные вопросы.</span><span class="sxs-lookup"><span data-stu-id="bf5f9-163">Additional items that can be addressed by Microsoft Consulting Services or a partner:</span></span> 
  
- <span data-ttu-id="bf5f9-164">Синхронизация решений пользовательской фермы</span><span class="sxs-lookup"><span data-stu-id="bf5f9-164">Synchronizing custom farm solutions</span></span> 
    
- <span data-ttu-id="bf5f9-165">Подключения к локальным источникам данных (подключение к бизнес-данным и источники поиска контента)</span><span class="sxs-lookup"><span data-stu-id="bf5f9-165">Connections to data sources on premises (Business Data Connectivity (BDC) and search content sources)</span></span> 
    
- <span data-ttu-id="bf5f9-166">Сценарии восстановления поиска</span><span class="sxs-lookup"><span data-stu-id="bf5f9-166">Search restore scenarios</span></span> 
    
- <span data-ttu-id="bf5f9-167">Целевое время восстановления (RTO) и целевая точка восстановления (RPO)</span><span class="sxs-lookup"><span data-stu-id="bf5f9-167">Recovery Time Objectives (RTO) and Recovery Point Objectives (RPO)</span></span> 
    
#### <a name="cold-standby-environment-running-virtual-machines"></a><span data-ttu-id="bf5f9-168">Среда с холодным резервированием, в которой работают виртуальные машины</span><span class="sxs-lookup"><span data-stu-id="bf5f9-168">Cold standby environment running virtual machines</span></span>

<span data-ttu-id="bf5f9-169">Среды с холодным резервированием запускаются дольше, но они дешевле.</span><span class="sxs-lookup"><span data-stu-id="bf5f9-169">Cold standby environments take longer to start but are less expensive.</span></span> 
  
- <span data-ttu-id="bf5f9-p107">Ферма создается в полном масштабе, но после создания фермы виртуальные машины будут остановлены. Вы оплачиваете только затраты на обработку, когда виртуальные машины работают. Кроме того, может взиматься плата за использование хранилища и передачу данных по сети. </span><span class="sxs-lookup"><span data-stu-id="bf5f9-p107">The farm is fully built, but the virtual machines are stopped after the farm is created. You pay only processing costs when the virtual machines are running, but storage and network data transfer costs apply.</span></span> 
    
- <span data-ttu-id="bf5f9-172">При аварии все виртуальные машины фермы запускаются и получают исправления.</span><span class="sxs-lookup"><span data-stu-id="bf5f9-172">In the event of a disaster, all the virtual machines in the farm are started and patched.</span></span> 
    
- <span data-ttu-id="bf5f9-173">К базам данных фермы применяются резервные копии и журналы транзакций.</span><span class="sxs-lookup"><span data-stu-id="bf5f9-173">Backups and transaction logs are applied to the farm databases.</span></span> 
    
<span data-ttu-id="bf5f9-174">Ниже перечислены дополнительные процедуры, которые необходимо выполнять в средах с холодным резервированием.</span><span class="sxs-lookup"><span data-stu-id="bf5f9-174">The following list describes additional procedures for cold standby environments:</span></span> 
  
- <span data-ttu-id="bf5f9-175">Регулярно включайте виртуальные машины для получения исправлений и обновлений, а также для проверки среды.</span><span class="sxs-lookup"><span data-stu-id="bf5f9-175">Turn on virtual machines regularly to patch, update, and verify the environment.</span></span> 
    
- <span data-ttu-id="bf5f9-176">Выполняйте процедуры обновления DNS и IP-адресов.</span><span class="sxs-lookup"><span data-stu-id="bf5f9-176">Run procedures to refresh DNS and IP addresses.</span></span> 
    
- <span data-ttu-id="bf5f9-177">Настройте SQL AlwaysOn после отработки отказа.</span><span class="sxs-lookup"><span data-stu-id="bf5f9-177">Set up SQL AlwaysOn after a failover.</span></span> 
    
<span data-ttu-id="bf5f9-p108">На сопроводительной схеме показана реплицированная среда восстановления на базе виртуальных машин. После отработки отказа путем перехода в среду с холодным резервированием будут запущены все виртуальные машины, а группы доступности будут настроены с помощью журналов воспроизведения. Это сделает серверы баз данных доступными. </span><span class="sxs-lookup"><span data-stu-id="bf5f9-p108">The accompanying diagram shows a replicated recovery environment on virtual machines. After failover to a cold standby environment, all virtual machines are started, and the availability groups are configured using replay logs to make the database servers available.</span></span> 
  
## <a name="sharepoint-recovery-environment-in-azure"></a><span data-ttu-id="bf5f9-180">Среда восстановления SharePoint в Azure</span><span class="sxs-lookup"><span data-stu-id="bf5f9-180">SharePoint recovery environment in Azure</span></span>

<span data-ttu-id="bf5f9-181">Проектирование и создание среды отработки отказов в Azure.</span><span class="sxs-lookup"><span data-stu-id="bf5f9-181">Design and build the failover environment in Azure.</span></span> 
  
- <span data-ttu-id="bf5f9-182">Создайте виртуальную сеть в Azure.</span><span class="sxs-lookup"><span data-stu-id="bf5f9-182">Create a virtual network in Azure.</span></span> 
    
- <span data-ttu-id="bf5f9-p109">Подключите локальную сеть к виртуальной сети в Azure с помощью VPN-подключения типа "сеть-сеть". Это подключение использует динамический шлюз в Azure. </span><span class="sxs-lookup"><span data-stu-id="bf5f9-p109">Connect the on-premises network with the virtual network in Azure with a site-to-site VPN connection. This connection uses a dynamic gateway in Azure.</span></span> 
    
- <span data-ttu-id="bf5f9-p110">Разверните один или несколько контроллеров доменов в виртуальной сети Azure и настройте их для работы с вашим локальным доменом. Эти контроллеры доменов представляют собой серверы каталогов. </span><span class="sxs-lookup"><span data-stu-id="bf5f9-p110">Deploy one or more domain controllers to the Azure virtual network, and configure these to work with your on-premises domain. These domain controllers are catalog servers.</span></span> 
    
- <span data-ttu-id="bf5f9-187">Настройте ферму SharePoint для облачных служб и групп доступности.</span><span class="sxs-lookup"><span data-stu-id="bf5f9-187">Adapt the SharePoint farm for cloud services and availability sets.</span></span> 
    
- <span data-ttu-id="bf5f9-188">Разверните ферму SharePoint и файловый сервер, чтобы разместить на них файловые ресурсы.</span><span class="sxs-lookup"><span data-stu-id="bf5f9-188">Deploy the SharePoint farm plus a file server to host file shares.</span></span> 
    
- <span data-ttu-id="bf5f9-189">Настройте доставку журналов и репликацию распределенной файловой системы между локальной средой и средой восстановления на основе Azure.</span><span class="sxs-lookup"><span data-stu-id="bf5f9-189">Set up log shipping and DFSR between the on-premises environment and the Azure-based recovery environment.</span></span> 
    
<span data-ttu-id="bf5f9-190">На сопроводительной схеме показаны локальная среда и виртуальная сеть Azure с указанными ниже компонентами.</span><span class="sxs-lookup"><span data-stu-id="bf5f9-190">The accompanying diagram shows the on-premises environment and the Azure virtual network with the following features:</span></span> 
  
### <a name="on-premises-environment"></a><span data-ttu-id="bf5f9-191">Локальная среда</span><span class="sxs-lookup"><span data-stu-id="bf5f9-191">On-premises environment</span></span>

- <span data-ttu-id="bf5f9-192">Windows Server 2012 RRAS</span><span class="sxs-lookup"><span data-stu-id="bf5f9-192">Windows Server 2012 RRAS</span></span> 
    
- <span data-ttu-id="bf5f9-193">Сервер Active Directory</span><span class="sxs-lookup"><span data-stu-id="bf5f9-193">Active Directory server</span></span> 
    
<span data-ttu-id="bf5f9-194">Локальные сетевые интерфейсы с виртуальной сетью Azure на базе VPN-шлюза.</span><span class="sxs-lookup"><span data-stu-id="bf5f9-194">The on-premises network interfaces with the Azure virtual network over a virtual private network (VPN) gateway.</span></span> 
  
### <a name="azure-virtual-network"></a><span data-ttu-id="bf5f9-195">Виртуальная сеть Azure</span><span class="sxs-lookup"><span data-stu-id="bf5f9-195">Azure virtual network</span></span>

<span data-ttu-id="bf5f9-196">Интерфейсы VPN-шлюза с активной подсетью VPN-шлюза.</span><span class="sxs-lookup"><span data-stu-id="bf5f9-196">The VPN gateway interfaces with an active VPN gateway subnet.</span></span> 
  
<span data-ttu-id="bf5f9-197">В виртуальной сети Azure имеются три указанные ниже облачные службы.</span><span class="sxs-lookup"><span data-stu-id="bf5f9-197">There are three cloud services in the Azure virtual network:</span></span> 
  
- <span data-ttu-id="bf5f9-198">В первой облачной службе имеются два сервера Active Directory и DNS с группой доступности. </span><span class="sxs-lookup"><span data-stu-id="bf5f9-198">The first cloud service has two Active Directory and DNS servers with an availability set.</span></span> 
    
- <span data-ttu-id="bf5f9-199">Вторая облачная служба содержит три набора серверов: два сервера распределенного кэша с набором доступности.</span><span class="sxs-lookup"><span data-stu-id="bf5f9-199">The second cloud service has three sets of servers: Two distributed cache servers with an availability set.</span></span> <span data-ttu-id="bf5f9-200">Два сервера переднего плана с набором доступности.</span><span class="sxs-lookup"><span data-stu-id="bf5f9-200">Two front-end servers with an availability set.</span></span> <span data-ttu-id="bf5f9-201">Три внутренних сервера с набором доступности.</span><span class="sxs-lookup"><span data-stu-id="bf5f9-201">Three backend servers with an availability set.</span></span>
    
- <span data-ttu-id="bf5f9-p112">В третьей облачной службе имеются три сервера баз данных с группой доступности. Один из этих серверов баз данных представляет собой файловый ресурс для доставки журналов и третий узел большинства узлов для SQL Server AlwaysOn. </span><span class="sxs-lookup"><span data-stu-id="bf5f9-p112">The third cloud service has three database servers with an availability set. One of these database servers is a file share for log shipping and a third node of a node majority for SQL Server AlwaysOn.</span></span> 
    
### <a name="build-the-ad-ds-hybrid-environment"></a><span data-ttu-id="bf5f9-204">Создание гибридной среды доменных служб Active Directory</span><span class="sxs-lookup"><span data-stu-id="bf5f9-204">Build the AD DS hybrid environment</span></span>

<span data-ttu-id="bf5f9-205">Конфигурация доменных служб Active Directory для этого решения представляет собой сценарий гибридного развертывания, в котором эти службы развертываются частично на локальных виртуальных машинах и частично — на виртуальных машинах Azure. </span><span class="sxs-lookup"><span data-stu-id="bf5f9-205">The configuration of AD DS for this solution constitutes a hybrid deployment scenario in which AD DS is partly deployed on-premises and partly deployed on Azure virtual machines.</span></span> 
  
<span data-ttu-id="bf5f9-206">Важно! перед развертыванием доменных служб Active Directory в Azure ознакомьтесь с рекомендациями по развертыванию Windows Server Active Directory наhttp://msdn.microsoft.com/en-us/library/windowsazure/jj156090.aspx)виртуальных машинах Microsoft Azure (.</span><span class="sxs-lookup"><span data-stu-id="bf5f9-206">Important — Before you deploy AD DS in Azure, read Guidelines for Deploying Windows Server Active Directory on Microsoft Azure Virtual Machines (http://msdn.microsoft.com/en-us/library/windowsazure/jj156090.aspx).</span></span> 
  
<span data-ttu-id="bf5f9-207">Для получения более подробных инструкций по проектированию и развертыванию http://TechNet.microsoft.comсред Active Directory, ознакомьтесь со статьей.</span><span class="sxs-lookup"><span data-stu-id="bf5f9-207">For complete guidance on designing and deploying Active Directory environments, see http://TechNet.microsoft.com.</span></span> 
  
<span data-ttu-id="bf5f9-208">Данная эталонная архитектура включает две виртуальные машины, настроенные в качестве контроллеров доменов.</span><span class="sxs-lookup"><span data-stu-id="bf5f9-208">This reference architecture includes two virtual machines configured as domain controllers.</span></span> <span data-ttu-id="bf5f9-209">Каждая виртуальная машина настраивается указанным ниже образом.</span><span class="sxs-lookup"><span data-stu-id="bf5f9-209">Each is configured as follows:</span></span> 
  
- <span data-ttu-id="bf5f9-210">Размер: малый.</span><span class="sxs-lookup"><span data-stu-id="bf5f9-210">Size — Small.</span></span> 
    
- <span data-ttu-id="bf5f9-211">Операционная система: Windows Server 2012.</span><span class="sxs-lookup"><span data-stu-id="bf5f9-211">Operating system — Windows Server 2012.</span></span> 
    
- <span data-ttu-id="bf5f9-p114">Роль: контроллер домена доменных служб Active Directory, назначенный в качестве сервера глобального каталога. В этой конфигурация уменьшается выходной трафик, проходящий через VPN-подключение. В среде с несколькими доменами и высокой скоростью изменения необходимо настроить локальные контроллеры доменов так, чтобы они не синхронизировались с серверами глобального каталога в Azure.  </span><span class="sxs-lookup"><span data-stu-id="bf5f9-p114">Role — AD DS domain controller designated as a global catalog server. This configuration reduces egress traffic across the VPN connection. In a multi-domain environment with high rates of change, configure domain controllers on-premises to not sync with the global catalog servers in Azure.</span></span> 
    
- <span data-ttu-id="bf5f9-215">Диски данных — разМестите базы данных AD DS, журналы и SYSVOL на дисках с данными Azure.</span><span class="sxs-lookup"><span data-stu-id="bf5f9-215">Data disks — Place the AD DS database, logs, and SYSVOL on Azure data disks.</span></span> <span data-ttu-id="bf5f9-216">Не размещайте их на диске операционной системы и временных дисках, предоставленных Azure.</span><span class="sxs-lookup"><span data-stu-id="bf5f9-216">Do not place these on the operating system disk or the temporary disks provided by Azure.</span></span> <span data-ttu-id="bf5f9-217">Это важно.</span><span class="sxs-lookup"><span data-stu-id="bf5f9-217">This is important.</span></span> 
    
- <span data-ttu-id="bf5f9-218">Role — установите и настройте Windows DNS на контроллерах домена.</span><span class="sxs-lookup"><span data-stu-id="bf5f9-218">Role — Install and configure Windows DNS on the domain controllers.</span></span> 
    
- <span data-ttu-id="bf5f9-219">IP-адреса — используйте динамические IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="bf5f9-219">IP addresses — Use dynamic IP addresses.</span></span> <span data-ttu-id="bf5f9-220">Для этого необходимо создать виртуальную сеть Azure.</span><span class="sxs-lookup"><span data-stu-id="bf5f9-220">This requires you to create an Azure Virtual Network.</span></span> 
    

