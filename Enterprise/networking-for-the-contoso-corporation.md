---
title: Сеть корпорации Contoso
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 014b3710-e6e9-485c-8550-975d510eb2fc
description: 'Сводка: Сведения о сетевой инфраструктуры Contoso и как его использовать ExpressRoute для оптимизированного доступа в облаке и услуги корпорации Майкрософт.'
ms.openlocfilehash: 89d4182d8a5ef44f936977ec51cc002b51f4b379
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915224"
---
# <a name="networking-for-the-contoso-corporation"></a><span data-ttu-id="b3d03-103">Сеть корпорации Contoso</span><span class="sxs-lookup"><span data-stu-id="b3d03-103">Networking for the Contoso Corporation</span></span>

 <span data-ttu-id="b3d03-104">**Сводка:** Сведения Contoso сетевой инфраструктуры и как его использовать ExpressRoute для оптимизированного доступа в облаке и услуги корпорации Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="b3d03-104">**Summary:** Understand the Contoso networking infrastructure and how it can use ExpressRoute for optimized acccess to Microsoft's cloud offerings.</span></span>
  
<span data-ttu-id="b3d03-p101">Принятие включительно облачной инфраструктуры, инженеров сети организации Contoso поняли фундаментальные shift, сетевой трафик на облачные службы путешествии как. Вместо только оптимизации трафика для локальных серверов и центров обработки данных, равное внимание должны быть оплачены для оптимизации трафика для пограничного сервера Интернета и через Интернет.</span><span class="sxs-lookup"><span data-stu-id="b3d03-p101">To adopt a cloud-inclusive infrastructure, Contoso's network engineers realized the fundamental shift in the way that network traffic to cloud-based services travels. Instead of only optimizing traffic to on-premises servers and datacenters, equal attention must be paid to optimizing traffic to the Internet edge and across the Internet.</span></span>
  
## <a name="contosos-networking-infrastructure"></a><span data-ttu-id="b3d03-107">Сетевой инфраструктуры организации Contoso</span><span class="sxs-lookup"><span data-stu-id="b3d03-107">Contoso's networking infrastructure</span></span>

<span data-ttu-id="b3d03-108">Сетевая инфраструктура корпорации Contoso представлена на рис. 1.</span><span class="sxs-lookup"><span data-stu-id="b3d03-108">Contoso has the networking infrastructure shown in Figure 1.</span></span>
  
<span data-ttu-id="b3d03-109">**Рис. 1. Инфраструктура глобальной сети корпорации Contoso**</span><span class="sxs-lookup"><span data-stu-id="b3d03-109">**Figure 1: Contoso's WAN infrastructure**</span></span>

![WAN-инфраструктура Contoso для главного офиса, региональных центров и дополнительных офисов](media/Contoso-Poster/Contoso-WW-Net.png)
  
<span data-ttu-id="b3d03-111">На рис. 1 показаны региональные и подчиненные офисы корпорации Contoso по всему миру, а также система связи между ними по глобальной сети.</span><span class="sxs-lookup"><span data-stu-id="b3d03-111">Figure 1 shows the Contoso's offices across the globe and the set of regional and satellite office WAN links between them.</span></span>
  
<span data-ttu-id="b3d03-112">Кроме того, сеть включает в себя такие дополнительные элементы:</span><span class="sxs-lookup"><span data-stu-id="b3d03-112">Additional elements of their network are the following:</span></span>
  
- <span data-ttu-id="b3d03-113">Локальная сеть</span><span class="sxs-lookup"><span data-stu-id="b3d03-113">On-premises network</span></span>
    
    <span data-ttu-id="b3d03-p102">Каналов связи ГЛОБАЛЬНОЙ сети подключения штаб-квартире Париж региональные подразделения и региональные подразделения в филиалах в конфигурации Звездообразная и сервер-концентратор. В каждом офисе маршрутизаторы доставить трафика узлов или точки беспроводного доступа в подсетях, использующих адресное пространство частных IP-адресов.</span><span class="sxs-lookup"><span data-stu-id="b3d03-p102">WAN links connect the Paris headquarters to regional offices and regional offices to satellite offices in a spoke and hub configuration. Within each office, routers deliver traffic to hosts or wireless access points on subnets, which use the private IP address space.</span></span>
    
- <span data-ttu-id="b3d03-116">Подключение к Интернету.</span><span class="sxs-lookup"><span data-stu-id="b3d03-116">Internet connectivity</span></span>
    
    <span data-ttu-id="b3d03-p103">Каждый office имеет свой собственный подключение к Интернету через прокси-сервер. Обычно это реализуется как через ГЛОБАЛЬНУЮ ссылка на локальной сети поставщика услуг Интернета, который также предоставляет общедоступный IP-адресов для прокси-сервера.</span><span class="sxs-lookup"><span data-stu-id="b3d03-p103">Each office has its own Internet connectivity via a proxy server. This is typically implemented as a WAN link to a local ISP that also provides public IP addresses for the proxy server.</span></span>
    
- <span data-ttu-id="b3d03-119">Интернет-представительство</span><span class="sxs-lookup"><span data-stu-id="b3d03-119">Internet presence</span></span>
    
    <span data-ttu-id="b3d03-p104">Компания Contoso владеет имя общедоступного домена contoso.com. Contoso общедоступного веб-сайта для упорядочения продуктов представляют собой набор серверов в центре данных подключенными к Интернету в Париж территории. Contoso использует /24 общедоступных диапазон IP-адресов в Интернете.</span><span class="sxs-lookup"><span data-stu-id="b3d03-p104">Contoso owns the contoso.com public domain name. The Contoso public web site for ordering products is a set of servers in an Internet-connected datacenter in the Paris campus. Contoso uses a /24 public IP address range on the Internet.</span></span>
    
## <a name="contosos-app-infrastructure"></a><span data-ttu-id="b3d03-123">Инфраструктура приложения организации Contoso</span><span class="sxs-lookup"><span data-stu-id="b3d03-123">Contoso's app infrastructure</span></span>

<span data-ttu-id="b3d03-124">Корпорация Contoso разработала архитектуру приложений и серверов в указанных ниже целях.



</span><span class="sxs-lookup"><span data-stu-id="b3d03-124">Contoso has architected its application and server infrastructure for the following:</span></span>
  
<span data-ttu-id="b3d03-125">**Рис. 2. Инфраструктура корпорации Contoso для внутренних приложений**</span><span class="sxs-lookup"><span data-stu-id="b3d03-125">**Figure 2: Contoso's infrastructure for internal applications**</span></span>

![Инфраструктура корпорации Contoso для внутренних приложений](media/Contoso-Poster/App-Infra.png)
  
- <span data-ttu-id="b3d03-127">Подчиненные офисы используют локальные серверы кэширования для хранения часто используемых документов и внутренних веб-сайтов.</span><span class="sxs-lookup"><span data-stu-id="b3d03-127">Satellite offices use local caching servers to store frequently-accessed documents and internal web sites.</span></span>
    
- <span data-ttu-id="b3d03-p105">
Региональные центральные офисы используют региональные серверы приложений для региональных и подчиненных офисов. Эти серверы синхронизируются с серверами главного офиса в Париже.</span><span class="sxs-lookup"><span data-stu-id="b3d03-p105">Regional hubs use regional application servers for the regional and satellite offices. These servers synchronize with servers in the Paris headquarters.</span></span>
    
- <span data-ttu-id="b3d03-130">В кампусе в Париже расположены центры данных с централизованными серверами приложений, которые обслуживают всю организацию.</span><span class="sxs-lookup"><span data-stu-id="b3d03-130">The Paris campus has the datacenters that contain the centralized application servers that serve the entire organization.</span></span>
    
<span data-ttu-id="b3d03-p106">60 % ресурсов, необходимых сотрудникам подчиненных или региональных центральных офисов, могут обслуживаться серверами подчиненных и региональных центральных офисов. Дополнительные 40 % запросов на ресурсы должны передаваться в кампус в Париже по каналу глобальной сети.</span><span class="sxs-lookup"><span data-stu-id="b3d03-p106">For users in satellite or regional hub offices, 60% of the resources needed by employees can be served by satellite and regional hub office servers. The additional 40% of resource requests must go over the WAN link to the Paris campus.</span></span>
  
## <a name="contosos-network-analysis"></a><span data-ttu-id="b3d03-133">Анализ сетевых Contoso</span><span class="sxs-lookup"><span data-stu-id="b3d03-133">Contoso's network analysis</span></span>

<span data-ttu-id="b3d03-134">Ниже приведены результаты анализа Contoso изменений, необходимых в сети с использованием различных категорий облака корпорации Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="b3d03-134">Here are the results of Contoso's analysis of the changes needed on their network to accommodate the different categories of Microsoft's cloud offerings:</span></span>
  
|<span data-ttu-id="b3d03-135">**SaaS и услуги в облаке: Office 365, Командной и Dynamics 365**</span><span class="sxs-lookup"><span data-stu-id="b3d03-135">**SaaS cloud offerings: Office 365, EMS, and Dynamics 365**</span></span>|<span data-ttu-id="b3d03-136">**Azure PaaS: Приложения для мобильных устройств**</span><span class="sxs-lookup"><span data-stu-id="b3d03-136">**Azure PaaS: Mobile applications**</span></span>|<span data-ttu-id="b3d03-137">**Azure IaaS: Рабочие нагрузки на стороне сервера**</span><span class="sxs-lookup"><span data-stu-id="b3d03-137">**Azure IaaS: Server-based workloads**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="b3d03-138">Для достижения высокой популярности служб SaaS у пользователей необходимо высокодоступное и производительное подключение к Интернету или напрямую к службам Microsoft Cloud.
</span><span class="sxs-lookup"><span data-stu-id="b3d03-138">Successful adoption of SaaS services by users depends on highly-available and performant connectivity to the Internet, or directly to Microsoft cloud services.</span></span>  <br/> <span data-ttu-id="b3d03-139">Текущее подключение мобильных пользователей к Интернету считается достаточным.
</span><span class="sxs-lookup"><span data-stu-id="b3d03-139">For mobile users, their current Internet access is assumed to be adequate.</span></span>  <br/> <span data-ttu-id="b3d03-140">Для пользователей в интрасети компании Contoso каждого office необходимо проанализировать и оптимизированные с учетом пропускной способности в Интернет и время приема-передачи размещения клиентов Office 365, Командной и Dynamics 365 центр обработки данных Европа корпорации Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="b3d03-140">For users on the Contoso intranet, each office must be analyzed and optimized for throughput to the Internet and round-trip times to Microsoft's Europe datacenter hosting the Office 365, EMS, and Dynamics 365 tenants.</span></span>  <br/> |<span data-ttu-id="b3d03-p107">Чтобы улучшить поддержку мобильных сотрудников, устаревшие приложения и некоторые сайты обмена файлами дорабатываются и развертываются в качестве приложений Azure PaaS. Для оптимальной производительности корпорация Contoso планирует развертывать новые приложения из нескольких центров данных Azure по всему миру. Диспетчер трафика Azure отправляет запросы клиентских приложений (созданные мобильным пользователем или на компьютере в офисе) в ближайший центр данных Azure, в котором размещено приложение.</span><span class="sxs-lookup"><span data-stu-id="b3d03-p107">To better support mobile workers, legacy apps and some file sharing sites are being reworked and deployed as Azure PaaS apps. For optimum performance, Contoso plans to deploy the new apps from multiple Azure datacenters across the world. Azure Traffic Manager to send client app requests, whether they originate from a mobile user or a computer in the office, to the nearest Azure datacenter hosting the app.</span></span>  <br/>  <span data-ttu-id="b3d03-144"> 

ИТ-отделу понадобится повысить производительность приложения PaaS и добавить возможность распределения трафика в свое решение для наблюдения за работоспособностью системы.</span><span class="sxs-lookup"><span data-stu-id="b3d03-144">The IT department will need to add PaaS application performance and traffic distribution to their network health monitoring solution.</span></span> <br/> |<span data-ttu-id="b3d03-145">Чтобы переместить некоторые устаревшие и архивные серверы из центров данных в кампусе в Париже и при необходимости добавить серверы для обработки данных на конец квартала, корпорация Contoso планирует использовать виртуальные машины, запущенные в службах инфраструктуры Azure. 

</span><span class="sxs-lookup"><span data-stu-id="b3d03-145">To move some legacy and archival servers out of the Paris campus datacenters and add servers as needed for quarter-end processing, Contoso plans to use virtual machines running in Azure infrastructure services.</span></span>  <br/> <span data-ttu-id="b3d03-146">Виртуальные сети Azure, которые содержат эти серверы, необходимо спроектировать таким образом, чтобы исключить перекрытие адресных пространств, маршрутизации и интегрированной службы доменных имен (DNS).

</span><span class="sxs-lookup"><span data-stu-id="b3d03-146">The Azure virtual networks that contain these servers must be designed for non-overlapping address spaces, routing, and integrated DNS.</span></span>  <br/> <span data-ttu-id="b3d03-147">ИТ-отдел должен включить эти новые серверы в свою систему управления сетями и их мониторинга.</span><span class="sxs-lookup"><span data-stu-id="b3d03-147">The IT department must include these new servers in their network management and monitoring system.</span></span>  <br/> |
   
## <a name="contosos-use-of-expressroute"></a><span data-ttu-id="b3d03-148">Использование Contoso ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="b3d03-148">Contoso's use of ExpressRoute</span></span>

<span data-ttu-id="b3d03-p108">ExpressRoute является выделенным глобальной сети из своего местоположения в Microsoft авторами расположение, которое подключается к сети Microsoft cloud вашей сети. ExpressRoute подключения обеспечивают прогнозируемый производительности и 99,9% времени работоспособности соглашения об уровне ОБСЛУЖИВАНИЯ. .</span><span class="sxs-lookup"><span data-stu-id="b3d03-p108">ExpressRoute is a dedicated WAN connection from your location to a Microsoft peering location that connects your network to the Microsoft cloud network. ExpressRoute connections provide predictable performance and a 99.9% uptime SLA. .</span></span>
  
<span data-ttu-id="b3d03-p109">Подключение к ExpressRoute подключенные к сети облаке Майкрософт и все расположения центра обработки данных Майкрософт в одном континент. Трафик между расположение авторами облако и центре обработки данных Майкрософт назначения, перенесенных в облаке сети Microsoft</span><span class="sxs-lookup"><span data-stu-id="b3d03-p109">With an ExpressRoute connection, you are connected to the Microsoft cloud network and all the Microsoft datacenter locations in the same continent. The traffic between the cloud peering location and the destination Microsoft datacenter is carried over the Microsoft cloud network</span></span>
  
<span data-ttu-id="b3d03-154">**Рис. 3. Всемирная сеть Microsoft Cloud**</span><span class="sxs-lookup"><span data-stu-id="b3d03-154">**Figure 3: The Microsoft cloud network worldwide**</span></span>

![Всемирная облачная сеть Майкрософт](media/Contoso-Poster/MS-WW-Cloud.png)
  
<span data-ttu-id="b3d03-156">На рис. 3 показана объединенная сеть Microsoft Cloud для различных регионов мира.</span><span class="sxs-lookup"><span data-stu-id="b3d03-156">Figure 3 shows the interconnected Microsoft cloud network for the various regions of the world.</span></span>
  
<span data-ttu-id="b3d03-p110">С помощью ExpressRoute Premium вы можете передавать данные в любой центр обработки данных Майкрософт на любом континенте из любого расположения пиринга Майкрософт на любом континенте. Трафик между континентами передается по сети Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="b3d03-p110">With ExpressRoute Premium, you can reach any Microsoft datacenter on any continent from any Microsoft peering location on any continent. The traffic between continents is carried over the Microsoft cloud network.</span></span>
  
<span data-ttu-id="b3d03-159">На основании анализа текущие и будущие трафика в облаке и услуги корпорации Майкрософт, Contoso выполнена оценка сеть и внедрения подключения к любой к любой ExpressRoute (на основе MPLS) для доступа к ресурсам Azure, с частной и общедоступной авторами связи в штаб-квартире Париж к месту авторами Майкрософт в Европе.</span><span class="sxs-lookup"><span data-stu-id="b3d03-159">Based on the analysis of current and future traffic to Microsoft's cloud offerings, Contoso has performed a network assessment and implemented an any-to-any (MPLS-based) ExpressRoute connection for access to Azure resources, with private and public peering relationships, from the Paris headquarters to the Microsoft peering location in Europe.</span></span>
  
<span data-ttu-id="b3d03-160">Благодаря этому подключению у ИТ-отдела корпорации Contoso появятся следующие возможности:</span><span class="sxs-lookup"><span data-stu-id="b3d03-160">This connection will give Contoso's IT department:</span></span>
  
- <span data-ttu-id="b3d03-161">Стабильная производительность для администрирования распределенных приложений Azure PaaS</span><span class="sxs-lookup"><span data-stu-id="b3d03-161">Consistent performance for administration of distributed Azure PaaS apps</span></span>
    
    <span data-ttu-id="b3d03-p111">Все разработчики приложений и базовой инфраструктуры ИТ Contoso Администраторы, в Париж территории. С помощью приложения Azure PaaS распространять на другой Azure центров обработки данных по всему миру Contoso должно согласованные производительности из территории Париж на администрирование приложений и их ресурсов хранения, которые состоят из ТБ документов.</span><span class="sxs-lookup"><span data-stu-id="b3d03-p111">All of Contoso's application developers and core infrastructure IT administrators are in the Paris campus. With Azure PaaS apps distributed to different Azure datacenters around the world, Contoso needs consistent performance from the Paris campus to administer the apps and their storage resources, which consist of TB of documents.</span></span>
    
- <span data-ttu-id="b3d03-164">Стабильная производительность для администрирования серверов в Azure IaaS</span><span class="sxs-lookup"><span data-stu-id="b3d03-164">Consistent performance for administration of servers in Azure IaaS</span></span>
    
    <span data-ttu-id="b3d03-p112">Администраторы организации Contoso центра обработки данных, в Париж территории и серверы для развертывания в Azure, расширение Париж центра обработки данных. Contoso необходимо согласованные производительности эти новые серверы для доступа к прежних версий приложений и архивирования хранилища и обработка окончания квартала.</span><span class="sxs-lookup"><span data-stu-id="b3d03-p112">Contoso's datacenter administrators are in the Paris campus and the servers to be deployed in Azure are an extension of the Paris datacenter. Contoso needs consistent performance to these new servers for access to legacy apps and archival storage and for end-of-quarter processing.</span></span>
    
## <a name="contosos-path-to-cloud-networking-readiness"></a><span data-ttu-id="b3d03-167">Путь Contoso в облако проверки готовности к сети</span><span class="sxs-lookup"><span data-stu-id="b3d03-167">Contoso's path to cloud networking readiness</span></span>

<span data-ttu-id="b3d03-168">Подготовка сети корпорации Contoso для работы с Microsoft Cloud включает в себя следующие этапы:</span><span class="sxs-lookup"><span data-stu-id="b3d03-168">Contoso uses the following steps to ready their network for the Microsoft cloud:</span></span>
  
1. <span data-ttu-id="b3d03-169">Оптимизация компьютеров сотрудников для доступа к Интернету
</span><span class="sxs-lookup"><span data-stu-id="b3d03-169">Optimize employee computers for Internet access</span></span>
    
    <span data-ttu-id="b3d03-170">Отдельные компьютеры будут проверены, чтобы убедиться в наличии на них последних версий стека TCP/IP, браузера, драйверов сетевого адаптера, а также обновлений для системы безопасности и операционной системы.</span><span class="sxs-lookup"><span data-stu-id="b3d03-170">Individual computers will be checked to ensure that the latest TCP/IP stack, browser, NIC drivers, and security and operating system updates are installed.</span></span>
    
2. <span data-ttu-id="b3d03-171">Анализ использования подключения к Интернету в каждом офисе и его увеличение при необходимости</span><span class="sxs-lookup"><span data-stu-id="b3d03-171">Analyze Internet connection utilization at each office and increase as needed</span></span>
    
    <span data-ttu-id="b3d03-172">
Текущее использование Интернета будет проанализировано для каждого офиса. Пропускная способность канала глобальной сети будет увеличена, если Интернет используется на 70 % или выше.</span><span class="sxs-lookup"><span data-stu-id="b3d03-172">Each office will be analyzed for the current Internet usage and WAN link bandwidth will be increased if operating at 70% or above utilization.</span></span>
    
3. <span data-ttu-id="b3d03-173">Анализ систем DMZ в каждом офисе для оптимальной производительности
</span><span class="sxs-lookup"><span data-stu-id="b3d03-173">Analyze DMZ systems at each office for optimal performance</span></span>
    
    <span data-ttu-id="b3d03-p113">Для оптимальной производительности будут проанализированы брандмауэры, IDS и другие системы, использующие Интернет. Прокси-серверы будут при необходимости обновлены.</span><span class="sxs-lookup"><span data-stu-id="b3d03-p113">Firewalls, IDSs, and other systems in the Internet path will be analyzed for optimal performance. Proxy servers will be updated or upgraded as needed.</span></span>
    
4. <span data-ttu-id="b3d03-176">Добавление подключения ExpressRoute для кампуса в Париже</span><span class="sxs-lookup"><span data-stu-id="b3d03-176">Add ExpressRoute for the Paris campus</span></span>
    
    <span data-ttu-id="b3d03-177">Это обеспечит постоянный доступ к ресурсам Azure для администрирования рабочих нагрузок Azure PaaS и IaaS.</span><span class="sxs-lookup"><span data-stu-id="b3d03-177">Provides consistent access to Azure resources for administration of Azure PaaS and IaaS workloads.</span></span>
    
5. <span data-ttu-id="b3d03-178">Создание и проверка профиля диспетчера трафика Azure для приложений Azure PaaS</span><span class="sxs-lookup"><span data-stu-id="b3d03-178">Create and test an Azure Traffic Manager profile for Azure PaaS apps</span></span>
    
    <span data-ttu-id="b3d03-179">Проверка профиля диспетчера трафика Azure, который использует метод маршрутизации производительности для распределения интернет-трафика между региональными расположениями.</span><span class="sxs-lookup"><span data-stu-id="b3d03-179">Test an Azure Traffic Manager profile that uses the performance routing method to gain experience in distributing Internet traffic to regional locations.</span></span>
    
6. <span data-ttu-id="b3d03-180">Резервирование частного адресного пространства для виртуальных сетей Azure
</span><span class="sxs-lookup"><span data-stu-id="b3d03-180">Reserve private address space for Azure VNets</span></span>
    
    <span data-ttu-id="b3d03-181">Резервирование частного адресного пространства для виртуальных сетей Azure и их подсетей в зависимости от запланированного количества кратко- и долгосрочных серверов.</span><span class="sxs-lookup"><span data-stu-id="b3d03-181">Based on the numbers of projected short and long-term servers in Azure IaaS, reserve private address space for Azure VNets and their subnets.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="b3d03-182">See Also</span><span class="sxs-lookup"><span data-stu-id="b3d03-182">See Also</span></span>

[<span data-ttu-id="b3d03-183">Contoso в Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="b3d03-183">Contoso in the Microsoft Cloud</span></span>](contoso-in-the-microsoft-cloud.md)
  
[<span data-ttu-id="b3d03-184">Ресурсы для администраторов, посвященные архитектуре Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="b3d03-184">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="b3d03-185">Стратегия Enterprise Cloud корпорации Майкрософт: ресурсы для лиц, принимающих решения в области ИТ</span><span class="sxs-lookup"><span data-stu-id="b3d03-185">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



