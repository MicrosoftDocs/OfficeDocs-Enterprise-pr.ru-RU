---
title: Доступная схема — сетевая интеграция серверных продуктов Microsoft Office
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 89f564eb-95c3-4077-bb92-75bf71b51270
f1.keywords:
- NOCSH
description: Эта статья представляет собой текстовую версию схемы "Интеграция сети продуктов Microsoft Office Server".
ms.openlocfilehash: def94a4523ad78676d6a9532a60dcba78032f23b
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/07/2020
ms.locfileid: "41843870"
---
# <a name="accessible-diagram---network-integration-of-microsoft-office-server-products"></a><span data-ttu-id="8121d-103">Доступная схема — сетевая интеграция серверных продуктов Microsoft Office</span><span class="sxs-lookup"><span data-stu-id="8121d-103">Accessible diagram - Network Integration of Microsoft Office Server Products</span></span>

<span data-ttu-id="8121d-104">**Сводка:** Эта статья представляет собой текстовую версию схемы "Интеграция сети продуктов Microsoft Office Server".</span><span class="sxs-lookup"><span data-stu-id="8121d-104">**Summary:** This article is an accessible text version of the diagram named Network Integration of Microsoft Office Server Products.</span></span>
  
<span data-ttu-id="8121d-105">На этом плакате представлена общая иллюстрация сетевой среды, включающей Lync Server 2013, SharePoint 2013 и Exchange Server 2013.</span><span class="sxs-lookup"><span data-stu-id="8121d-105">This poster provides a general illustration of a network environment that includes Lync Server 2013, SharePoint 2013, and Exchange Server 2013.</span></span> <span data-ttu-id="8121d-106">В нем также показаны следующие элементы сети, общие для этих продуктов: удаленный и внутренний доступ, проверка подлинности, клиентский трафик и маршрутизация трафика через общие устройства.</span><span class="sxs-lookup"><span data-stu-id="8121d-106">It also illustrates the following networking elements that are common across these products: remote and internal access, authentication, client traffic, and routing traffic through shared devices.</span></span> 
  
## <a name="high-level-concepts-for-lync-exchange-sharepoint-server-and-office-web-apps"></a><span data-ttu-id="8121d-107">Высокоуровневые концепции для Lync, Exchange, SharePoint Server и Office Web Apps</span><span class="sxs-lookup"><span data-stu-id="8121d-107">High-level concepts for Lync, Exchange, SharePoint Server, and Office Web Apps</span></span>

### <a name="about-the-design"></a><span data-ttu-id="8121d-108">Сведения о проектировании</span><span class="sxs-lookup"><span data-stu-id="8121d-108">About the design</span></span>

#### <a name="streamlined-network-design"></a><span data-ttu-id="8121d-109">Упрощенный дизайн сети</span><span class="sxs-lookup"><span data-stu-id="8121d-109">Streamlined network design</span></span>

<span data-ttu-id="8121d-110">Эта топология иллюстрирует локальное развертывание сети для SharePoint 2013, Exchange Server 2013 и Lync Server 2013.</span><span class="sxs-lookup"><span data-stu-id="8121d-110">This topology illustrates an on-premises network deployment of SharePoint 2013, Exchange Server 2013, and Lync Server 2013.</span></span> <span data-ttu-id="8121d-111">Здесь также показано использование облачной службы Майкрософт, Exchange Online Protection, которая обеспечивает защиту от нежелательной почты и вредоносных программ для входящего трафика SMTP из Интернета.</span><span class="sxs-lookup"><span data-stu-id="8121d-111">It also shows the use of the Microsoft cloud-based service, Exchange Online Protection, which provides spam and malware protection for inbound Simple Mail Transfer Protocol (SMTP) traffic from the Internet.</span></span> 
  
<span data-ttu-id="8121d-112">Эта структура сети оптимизирована для использования минимального набора сетевых компонентов.</span><span class="sxs-lookup"><span data-stu-id="8121d-112">This network design is streamlined to a minimum set of network features.</span></span> <span data-ttu-id="8121d-113">При проектировании не учитывается дополнительная безопасность или функции инфраструктуры, которые могут потребоваться некоторым организациям.</span><span class="sxs-lookup"><span data-stu-id="8121d-113">The design does not take into account additional security or infrastructure features that some organizations might require.</span></span> 
  
<span data-ttu-id="8121d-114">Эта схема:</span><span class="sxs-lookup"><span data-stu-id="8121d-114">This diagram:</span></span> 
  
- <span data-ttu-id="8121d-115">Пример сетевой топологии, иллюстрирующий входящий и исходящий трафик через маршрутизатор шлюза и балансировку нагрузки трафика клиентского сеанса (внешнего и внутреннего) на соответствующие уровни SharePoint, Exchange и Lync Server.</span><span class="sxs-lookup"><span data-stu-id="8121d-115">Provides an example network topology illustrating inbound and outbound traffic through a gateway router and load balancing of client session traffic (external and internal) to the appropriate SharePoint, Exchange, and Lync server tiers.</span></span> 
    
- <span data-ttu-id="8121d-116">Показывает использование необязательных серверов удаленного доступа, таких как сторонний шлюз VPN или сервер DirectAccess, для обеспечения безопасной связи для перемещаемых или удаленных сотрудников.</span><span class="sxs-lookup"><span data-stu-id="8121d-116">Shows the use of optional remote access servers, such as a third-party VPN gateway or DirectAccess server, to provide secure communication for roaming or remote employees.</span></span> 
    
- <span data-ttu-id="8121d-117">Подробные сведения о потоке трафика SharePoint, Exchange и Lync от клиента к каждому уровню сервера платформы.</span><span class="sxs-lookup"><span data-stu-id="8121d-117">Details the SharePoint, Exchange, and Lync traffic flow from the client to each platform server tier.</span></span> 
    
- <span data-ttu-id="8121d-118">Определяет тип подключения удаленного или внутреннего доступа на основе клиента (например, "партнер" или "сотрудник") и используемого метода проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="8121d-118">Identifies the type of remote or internal access connection based on client (such as partner or employee), and the authentication method used.</span></span> 
    
- <span data-ttu-id="8121d-119">Разбивает платформы SharePoint, Exchange и Lync с помощью необходимых ролей сервера, определяя интерфейсный сервер, приложение, базу данных и другие уровни.</span><span class="sxs-lookup"><span data-stu-id="8121d-119">Breaks down the SharePoint, Exchange, and Lync platforms by required server roles, identifying the front end, application, database, and other levels.</span></span> 
    
<span data-ttu-id="8121d-120">Архитектура, используемая в SharePoint, Lync и Exchange, не предлагает предпочтительный способ реализации этих платформ.</span><span class="sxs-lookup"><span data-stu-id="8121d-120">The architecture used here for SharePoint, Lync, and Exchange does not suggest a preferred way of implementing these platforms.</span></span> <span data-ttu-id="8121d-121">Он просто предоставляет пример, так как топологии различаются на основе уникальных требований к сети и соображений безопасности.</span><span class="sxs-lookup"><span data-stu-id="8121d-121">It merely provides an example as topologies differ based on unique network requirements and security considerations.</span></span> 
  
#### <a name="gateway-router"></a><span data-ttu-id="8121d-122">Маршрутизатор шлюза</span><span class="sxs-lookup"><span data-stu-id="8121d-122">Gateway router</span></span>

<span data-ttu-id="8121d-123">В этой топологии маршрутизатор шлюза располагается на границе сети и направляет весь входящий и исходящий трафик в интрасеть и из нее.</span><span class="sxs-lookup"><span data-stu-id="8121d-123">For this topology, the gateway router sits at the edge of the network and routes all incoming and outgoing traffic to and from the intranet.</span></span> <span data-ttu-id="8121d-124">Кроме того, могут быть также другие компоненты, которые приводят к мосту между маршрутизатором шлюза и подсистемой балансировки нагрузки, например с несколькими уровнями межсетевых экранов.</span><span class="sxs-lookup"><span data-stu-id="8121d-124">Alternatively, there could also be other components that bridge the gap between the gateway router and the load balancer shown, such as multiple layers of firewalls.</span></span> <span data-ttu-id="8121d-125">Эта топология представляет только один способ развертывания сети из множества.</span><span class="sxs-lookup"><span data-stu-id="8121d-125">This topology represents just one way to deploy your network out of many.</span></span> <span data-ttu-id="8121d-126">В этой конфигурации шлюз настраивается с помощью списков управления доступом (ACL) для предоставления очень конкретного входящего и исходящего IP-трафика на интерфейсах маршрутизатора.</span><span class="sxs-lookup"><span data-stu-id="8121d-126">In this configuration, the gateway is configured with access control lists (ACLs) to permit very specific incoming and outgoing IP-based traffic on the router interfaces.</span></span> <span data-ttu-id="8121d-127">Списки управления доступом, расширенная проверка и преобразование сетевых адресов (NAT) также могут быть выполнены на других устройствах, таких как брандмауэры, в сети.</span><span class="sxs-lookup"><span data-stu-id="8121d-127">ACLs, advanced inspection, or Network Address Translation (NAT) can also be performed on other devices, such as firewalls, throughout your network.</span></span> 
  
#### <a name="load-balancer-and-reverse-proxy-devices"></a><span data-ttu-id="8121d-128">Подсистема балансировки нагрузки и устройства обратного прокси-сервера</span><span class="sxs-lookup"><span data-stu-id="8121d-128">Load balancer and reverse proxy devices</span></span>

<span data-ttu-id="8121d-129">Вы можете использовать аппаратные и программные решения балансировки нагрузки для перенаправления трафика для сегментов, включая интерфейсные веб-серверы SharePoint и серверы клиентского доступа Exchange (касс).</span><span class="sxs-lookup"><span data-stu-id="8121d-129">You can use hardware or software load balancing solutions to redirect traffic for segments including SharePoint front-end web servers and Exchange Client Access Servers (CASs).</span></span> <span data-ttu-id="8121d-130">В некоторых случаях рекомендуется использовать аппаратный балансировщик нагрузки для уровня 7, так как его можно улучшить с помощью сведений в запросе, например файлов cookie или заголовков.</span><span class="sxs-lookup"><span data-stu-id="8121d-130">In some cases it's optimal to use a layer 7 hardware-based load balancer for persistence requirements as it can perform better by using information in the request, such as cookies or headers.</span></span> <span data-ttu-id="8121d-131">Тем не менее, такие факторы, как затраты и повышенное использование и Рабочая нагрузка из такого решения, могут быть нежелательны для конкретных потребностей.</span><span class="sxs-lookup"><span data-stu-id="8121d-131">However, factors like cost and increased utilization and workload from such a solution might not be desirable for your specific needs.</span></span> <span data-ttu-id="8121d-132">Рассмотрите следующие моменты для балансировки нагрузки в SharePoint, Exchange и Lync:</span><span class="sxs-lookup"><span data-stu-id="8121d-132">Consider the following points for load balancing across SharePoint, Exchange, and Lync:</span></span> 
  
- <span data-ttu-id="8121d-133">SharePoint для SharePoint 2013, нет необходимости включать сходство для интерфейсных веб-серверов.</span><span class="sxs-lookup"><span data-stu-id="8121d-133">SharePoint - For SharePoint 2013, you do not need to enable affinity for your front-end web servers.</span></span> <span data-ttu-id="8121d-134">Обычно это используется для создания залипания сеансов и предотвращения нескольких запросов проверки подлинности от клиентов к каждому интерфейсному веб-серверу.</span><span class="sxs-lookup"><span data-stu-id="8121d-134">Normally, this would be used for creating sticky sessions and avoiding multiple authentication requests from clients to each front-end web server.</span></span> <span data-ttu-id="8121d-135">Новая служба распределенного кэша в SharePoint 2013 хранит и распространяет маркеры входа на веб-серверах фермы SharePoint.</span><span class="sxs-lookup"><span data-stu-id="8121d-135">The new Distributed Cache service in SharePoint 2013 stores and distributes logon tokens across the web servers of the SharePoint farm.</span></span> 
    
- <span data-ttu-id="8121d-136">Exchange-in Exchange 2013, роль CAS разработана для использования балансировки нагрузки 4 уровня и распределения запросов на транспортном уровне.</span><span class="sxs-lookup"><span data-stu-id="8121d-136">Exchange - In Exchange 2013, the CAS role is designed to use layer 4 load balancing, distributing requests at the transport layer.</span></span> <span data-ttu-id="8121d-137">Это может значительно снизить загрузку и загрузку подсистемы балансировки нагрузки.</span><span class="sxs-lookup"><span data-stu-id="8121d-137">This can significantly decrease load balancer utilization and workload.</span></span> 
    
- <span data-ttu-id="8121d-138">Lync — балансировка нагрузки системы доменных имен (DNS) рекомендуется для трафика SIP для пулов Lync.</span><span class="sxs-lookup"><span data-stu-id="8121d-138">Lync - Domain Name System (DNS) load balancing is recommended for Session Initiation Protocol (SIP) traffic for Lync pools.</span></span> <span data-ttu-id="8121d-139">Аппаратная балансировка нагрузки (HLB) необходима для трафика Lync Web (HTTPS).</span><span class="sxs-lookup"><span data-stu-id="8121d-139">Hardware load balancing (HLB) is required for Lync Web (HTTPS) traffic.</span></span> 
    
### <a name="remote-access-options"></a><span data-ttu-id="8121d-140">Варианты для удаленного доступа</span><span class="sxs-lookup"><span data-stu-id="8121d-140">Remote access options</span></span>

<span data-ttu-id="8121d-141">Существует несколько параметров, которые могут публиковать ресурсы интрасети для партнеров в Интернете или обеспечивать безопасный удаленный доступ для удаленных или перемещаемых сотрудников.</span><span class="sxs-lookup"><span data-stu-id="8121d-141">There are several options that can publish intranet resources for partners on the Internet or provide secure remote access for remote or roaming employees.</span></span> <span data-ttu-id="8121d-142">К таким примерам относятся обратные прокси-серверы, DirectAccess и сторонние VPN-шлюзы.</span><span class="sxs-lookup"><span data-stu-id="8121d-142">Such examples include reverse proxies, DirectAccess, and third-party VPN gateways.</span></span> <span data-ttu-id="8121d-143">Решения удаленного доступа, описываемые далее в этом разделе, это возможности SharePoint, Lync и Exchange, а также любая комбинация этих серверов в локальном развертывании.</span><span class="sxs-lookup"><span data-stu-id="8121d-143">The remote access solutions discussed later in this section are possibilities for SharePoint, Lync, and Exchange, or any combination of these servers in an on-premises deployment.</span></span> <span data-ttu-id="8121d-144">Однако некоторые удаленные параметры могут не работать с определенным решением.</span><span class="sxs-lookup"><span data-stu-id="8121d-144">However, some remote options might not work with a particular solution.</span></span> 
  
<span data-ttu-id="8121d-145">Обратный прокси — обратный прокси-сервер поддерживает шифрование трафика, например SSL, и с его помощью вы можете публиковать приложения интрасети и веб-ресурсы для пользователей и партнеров, прошедших проверку подлинности, в Интернете.</span><span class="sxs-lookup"><span data-stu-id="8121d-145">Reverse Proxy - A reverse proxy supports traffic encryption, such as Secure Sockets Layer (SSL), and with it you can publish intranet applications and web resources to authenticated users and partners on the Internet.</span></span> <span data-ttu-id="8121d-146">В качестве примера используется Microsoft Forefront Unified Access Gateway (UAG).</span><span class="sxs-lookup"><span data-stu-id="8121d-146">An example is Microsoft Forefront Unified Access Gateway (UAG).</span></span> <span data-ttu-id="8121d-147">Многие аппаратные подсистемы балансировки нагрузки также поддерживают функции обратного прокси-сервера.</span><span class="sxs-lookup"><span data-stu-id="8121d-147">Many hardware load balancers also support reverse proxy functionality.</span></span> <span data-ttu-id="8121d-148">Тем не менее существуют сценарии для использования автономного решения в зависимости от ваших потребностей и требований, таких как изоляция трафика, безопасность обособления и оптимизация производительности.</span><span class="sxs-lookup"><span data-stu-id="8121d-148">However, there are still valid scenarios for using a standalone solution based on your needs and requirements, such as traffic isolation, security compartmentalization, and performance optimization.</span></span> 
  
<span data-ttu-id="8121d-149">Преимущества обратного прокси-сервера и рекомендации:</span><span class="sxs-lookup"><span data-stu-id="8121d-149">Reverse-proxy benefits and considerations:</span></span> 
  
- <span data-ttu-id="8121d-150">Предоставляет доступ к ресурсам интрасети для пользователей, прошедших проверку подлинности, и безопасный доступ к ресурсам интрасети (использует SSL (TCP 443) между клиентом и обратным прокси-сервером).</span><span class="sxs-lookup"><span data-stu-id="8121d-150">Provides authenticated and secured access for partners or users accessing intranet resources (uses SSL (TCP 443) between the client and reverse proxy server).</span></span> 
    
- <span data-ttu-id="8121d-151">Для Exchange преимуществом использования обратного прокси-сервера, такого как Forefront UAG, является предварительная проверка подлинности перед доступом к серверу клиентского доступа Exchange.</span><span class="sxs-lookup"><span data-stu-id="8121d-151">For Exchange, a benefit of using a reverse proxy such as Forefront UAG is pre-authentication before accessing the Exchange Client access server.</span></span> <span data-ttu-id="8121d-152">Пользователи удаленного доступа, использующие опубликованные приложения, такие как Outlook Web Access (OWA), могут выполнять проверку подлинности с помощью методов Basic, NTLM или Kerberos до того, как они достигают внутренней сети.</span><span class="sxs-lookup"><span data-stu-id="8121d-152">Remote access users using published applications such as Outlook Web Access (OWA) can authenticate with the basic, NTLM, or Kerberos methods before they reach the internal network.</span></span> 
    
- <span data-ttu-id="8121d-153">Для Exchange и SharePoint такие решения, как Forefront UAG, могут прерывать подключения SSL и снижать нагрузку на сервер ресурсов интрасети, в то же время обеспечивая единую точку управления для сертификатов.</span><span class="sxs-lookup"><span data-stu-id="8121d-153">For Exchange and SharePoint, solutions like Forefront UAG can terminate SSL connections and decrease the load of the intranet resources server while providing a single point of management for certificates.</span></span> 
    
- <span data-ttu-id="8121d-154">Для сети Lync трафик через Интернет (HTTPS) проходит через обратный прокси-сервер (TCP 443) для связи с клиентом.</span><span class="sxs-lookup"><span data-stu-id="8121d-154">For Lync, Web (HTTPS) traffic goes through the reverse proxy (TCP 443) for client communication.</span></span> <span data-ttu-id="8121d-155">Обратные прокси-серверы HTTPS-подключения к веб-службам Lync, Exchange CA и Office Web Apps.</span><span class="sxs-lookup"><span data-stu-id="8121d-155">The reverse proxy proxies the HTTPS connection to Lync Web Services, Exchange CAS, and Office Web Apps.</span></span> <span data-ttu-id="8121d-156">Lync Server 2013 не поддерживает UAG.</span><span class="sxs-lookup"><span data-stu-id="8121d-156">Lync Server 2013 does not support UAG.</span></span> 
    
<span data-ttu-id="8121d-157">DirectAccess — технология удаленного доступа, использующая безопасность протокола IP (IPsec) для проверки подлинности и шифрования трафика между клиентом и сервером DirectAccess.</span><span class="sxs-lookup"><span data-stu-id="8121d-157">DirectAccess - A remote access technology that relies on Internet Protocol security (IPsec) for authentication and for encrypting traffic between the DirectAccess client and server.</span></span> <span data-ttu-id="8121d-158">DirectAccess предоставляет одновременный доступ к ресурсам Интернета и интрасети для роуминга и удаленных сотрудников без необходимости запуска подключения.</span><span class="sxs-lookup"><span data-stu-id="8121d-158">DirectAccess provides simultaneous access to both Internet and intranet resources for roaming and remote employees without having to initiate a connection.</span></span> 
  
<span data-ttu-id="8121d-159">Факторы DirectAccess, которые следует рассмотреть:</span><span class="sxs-lookup"><span data-stu-id="8121d-159">DirectAccess points to consider:</span></span> 
  
- <span data-ttu-id="8121d-160">DirectAccess использует защищенный трафик IPsec (протокол 50 и 51 и UDP 500) между клиентом и сервером DirectAccess.</span><span class="sxs-lookup"><span data-stu-id="8121d-160">DirectAccess uses IPsec protected traffic (protocol 50 and 51 and UDP 500) between the DirectAccess client and server.</span></span> 
    
- <span data-ttu-id="8121d-161">Для DirectAccess для Windows Server 2012 и Windows 8 не требуется развертывание инфраструктуры открытых ключей (PKI) для проверки подлинности сервера и клиента.</span><span class="sxs-lookup"><span data-stu-id="8121d-161">DirectAccess for Windows Server 2012 and Windows 8 does not need a public key infrastructure (PKI) deployment for server and client authentication.</span></span> 
    
- <span data-ttu-id="8121d-162">Мы рекомендуем использовать DirectAccess с Lync Server 2013 из-за проблем с задержкой звука и видео, связанными с шифрованием и расшифрованием IPsec.</span><span class="sxs-lookup"><span data-stu-id="8121d-162">We recommend against using DirectAccess with Lync Server 2013 because of audio and video latency issues associated with IPsec encryption and decryption.</span></span> 
    
    <span data-ttu-id="8121d-163">VPN-шлюз — типичные шлюзы VPN обеспечивают подключение удаленного доступа, в котором клиентский компьютер удаленного доступа логически проецируется на интрасеть через туннельное и инициированное пользователем подключение.</span><span class="sxs-lookup"><span data-stu-id="8121d-163">VPN Gateway - Typical VPN gateways provide a remote access connection in which a remote access client computer is logically projected onto the intranet through a tunneled and user-initiated connection.</span></span> <span data-ttu-id="8121d-164">Вы можете использовать единый удаленный доступ в Windows Server 2012 или нескольких сторонних решениях, чтобы обеспечить безопасный доступ к интрасети для перемещенных или удаленных сотрудников.</span><span class="sxs-lookup"><span data-stu-id="8121d-164">You can use Unified Remote Access in Windows Server 2012 or several third-party solutions to provide secured access to the intranet for roaming or remote employees.</span></span> <span data-ttu-id="8121d-165">VPN не рекомендуется для Lync.</span><span class="sxs-lookup"><span data-stu-id="8121d-165">VPN is not recommended for Lync.</span></span> <span data-ttu-id="8121d-166">Удаленный трафик Lync должен использовать пограничные серверы и раздельное туннелирование.</span><span class="sxs-lookup"><span data-stu-id="8121d-166">Remote Lync traffic should use the Edge Servers and split tunneling.</span></span> 
    
### <a name="domain-name-system-dns-considerations"></a><span data-ttu-id="8121d-167">Вопросы, касающиеся системы доменных имен (DNS)</span><span class="sxs-lookup"><span data-stu-id="8121d-167">Domain Name System (DNS) considerations</span></span>

<span data-ttu-id="8121d-168">Необходимо запланировать набор записей DNS, позволяющих пользователям Интернета и интрасети разрешать DNS-имена в соответствующие IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="8121d-168">You need to plan for the set of DNS records that allow both Internet and intranet users to resolve DNS names to the appropriate IP addresses.</span></span> 
  
- <span data-ttu-id="8121d-169">Для партнеров в Интернете и перемещенных или удаленных сотрудников DNS-записи, зарегистрированные с помощью DNS-серверов в Интернете, предоставляют разрешение на набор общедоступных IP-адресов, соответствующих маршрутизатору шлюза, пограничному серверу Lync, набору виртуальных IP-адресов (VIP) на Подсистема балансировки нагрузки и шлюз DirectAccess или VPN по мере необходимости.</span><span class="sxs-lookup"><span data-stu-id="8121d-169">For Internet-based partners and roaming or remote employees, DNS records registered with Internet DNS servers provide resolution to the set of public IP addresses corresponding to the gateway router, the Lync Edge Server, the set of virtual IP addresses (VIPs) on the load balancer, and the DirectAccess or VPN gateway as needed.</span></span> 
    
- <span data-ttu-id="8121d-170">Для пользователей на основе интрасети записи DNS, зарегистрированные с помощью DNS-серверов интрасети, обеспечивают разрешение для набора виртуальных IP-адресов (VIP) в подсистеме балансировки нагрузки для доступа к ресурсам SharePoint, Lync и Exchange.</span><span class="sxs-lookup"><span data-stu-id="8121d-170">For intranet-based users, DNS records registered with intranet DNS servers provide resolution to the set of virtual IP addresses (VIPs) on the load balancer for access to SharePoint, Lync, and Exchange resources.</span></span> 
    
- <span data-ttu-id="8121d-171">Клиенты DirectAccess используют DNS-серверы интрасети для имен, соответствующих пространству имен DNS в интрасети и DNS-серверам Интернета для имен, которые не поддерживаются.</span><span class="sxs-lookup"><span data-stu-id="8121d-171">DirectAccess clients use intranet DNS servers for names corresponding to the intranet DNS name space and Internet DNS servers for names that do not.</span></span> <span data-ttu-id="8121d-172">Чтобы упростить работу DirectAccess, рассмотрите возможность использования разделенной реализации DNS, использующей различные пространства имен DNS для имен интрасети и Интернета.</span><span class="sxs-lookup"><span data-stu-id="8121d-172">To simplify the operation of DirectAccess, consider the use of a split DNS implementation that uses different DNS namespaces for intranet and Internet-based names.</span></span> <span data-ttu-id="8121d-173">Например, используйте contoso.com для пространства имен Интернета и corp.contoso.com для пространства имен интрасети.</span><span class="sxs-lookup"><span data-stu-id="8121d-173">For example, use contoso.com for Internet namespace and corp.contoso.com for the intranet namespace.</span></span> 
    
- <span data-ttu-id="8121d-174">Exchange использует разделенную модель DNS, в которой разрешение Host to IP отличается от трафика с общедоступным маршрутом из сети Организации.</span><span class="sxs-lookup"><span data-stu-id="8121d-174">Exchange uses a split DNS model where host to IP resolution differs on publicly routed traffic from that on the corporate network.</span></span> <span data-ttu-id="8121d-175">Как минимум, необходимо иметь записи DNS для URL-адресов OWA, автообнаружения, ActiveSync для клиентского трафика и запись MX для входящей почты.</span><span class="sxs-lookup"><span data-stu-id="8121d-175">At a minimum, you need to have DNS records for OWA, Autodiscover, ActiveSync URLs for client traffic, and an MX record for inbound mail.</span></span> 
    
- <span data-ttu-id="8121d-176">Если вы используете Exchange Online Protection (EOP), запись MX указывает на эту службу, а не на ферму Exchange.</span><span class="sxs-lookup"><span data-stu-id="8121d-176">If you are using Exchange Online Protection (EOP), your MX record points to that service instead of your Exchange farm.</span></span> 
    
- <span data-ttu-id="8121d-177">Для Exchange требуется проверка владельца записи TXT в общедоступной службе DNS, а также идентификатор Федерации для настройки федеративного общего доступа.</span><span class="sxs-lookup"><span data-stu-id="8121d-177">For Exchange, you need a proof of ownership TXT record in your public DNS, and a Federation Org ID to set up federated sharing.</span></span> 
    
- <span data-ttu-id="8121d-178">VPN-клиенты удаленного доступа могут быть настроены на использование только DNS-серверов в интрасети, когда VPN-подключение удаленного доступа активно.</span><span class="sxs-lookup"><span data-stu-id="8121d-178">Remote access VPN clients can be configured to use only intranet DNS servers when the remote access VPN connection is active.</span></span> 
    
### <a name="diagram-description"></a><span data-ttu-id="8121d-179">Описание схемы</span><span class="sxs-lookup"><span data-stu-id="8121d-179">Diagram Description</span></span>

<span data-ttu-id="8121d-180">На этой схеме показан пример топологии сети, иллюстрирующий входящий и исходящий трафик через маршрутизатор шлюза и балансировку нагрузки трафика клиентского сеанса (внешнего и внутреннего) на соответствующие уровни SharePoint, Exchange и Lync Server.</span><span class="sxs-lookup"><span data-stu-id="8121d-180">This diagram provides an example network topology illustrating inbound and outbound traffic through a gateway router and load balancing of client session traffic (external and internal) to the appropriate SharePoint, Exchange, and Lync server tiers.</span></span> <span data-ttu-id="8121d-181">Описание этой схемы разделено на две части:</span><span class="sxs-lookup"><span data-stu-id="8121d-181">The description of this diagram is divided into two parts:</span></span> 
  
- <span data-ttu-id="8121d-182">Описание компонентов, показанных на схеме</span><span class="sxs-lookup"><span data-stu-id="8121d-182">Description of components shown in the diagram</span></span> 
    
- <span data-ttu-id="8121d-183">Описание способа перемещения трафика через компоненты на уровни серверов SharePoint, Exchange, Lync и Office Web Apps.</span><span class="sxs-lookup"><span data-stu-id="8121d-183">Description of how traffic moves through the components to the SharePoint, Exchange, Lync, and Office Web Apps server tiers.</span></span> 
    
#### <a name="description-of-components-shown-in-the-diagram"></a><span data-ttu-id="8121d-184">Описание компонентов, показанных на схеме</span><span class="sxs-lookup"><span data-stu-id="8121d-184">Description of components shown in the diagram</span></span>

#### <a name="user-types"></a><span data-ttu-id="8121d-185">Типы пользователей.</span><span class="sxs-lookup"><span data-stu-id="8121d-185">User types</span></span>

<span data-ttu-id="8121d-186">Существует четыре типа пользователей, три за прев сети и облачные службы, а также один внутренний, включающий:</span><span class="sxs-lookup"><span data-stu-id="8121d-186">There are four different types of users, three outside the network and cloud services and one internal, which include:</span></span> 
  
- <span data-ttu-id="8121d-187">Партнерские компании (деловые отношения) — внешние</span><span class="sxs-lookup"><span data-stu-id="8121d-187">Partner companies (business-to-business)-external</span></span> 
    
- <span data-ttu-id="8121d-188">Отдельные партнеры (SharePoint и анонимные (Lync)) — внешние</span><span class="sxs-lookup"><span data-stu-id="8121d-188">Individual partners (SharePoint and anonymous (Lync))-external</span></span> 
    
- <span data-ttu-id="8121d-189">Роуминг и удаленные сотрудники — внешние</span><span class="sxs-lookup"><span data-stu-id="8121d-189">Roaming and remote employees-external</span></span> 
    
- <span data-ttu-id="8121d-190">Внутренние сотрудники</span><span class="sxs-lookup"><span data-stu-id="8121d-190">Internal employees</span></span> 
    
#### <a name="cloud-based-email-traffic"></a><span data-ttu-id="8121d-191">Трафик электронной почты на основе облака</span><span class="sxs-lookup"><span data-stu-id="8121d-191">Cloud-based email traffic</span></span>

<span data-ttu-id="8121d-192">Существует облачный компонент для трафика электронной почты на основе SMTP: почтовые узлы Интернета или Exchange Online Protection.</span><span class="sxs-lookup"><span data-stu-id="8121d-192">There is a cloud-based component for SMTP-based email traffic, either Internet Mail Hosts or Exchange Online Protection.</span></span> 
  
#### <a name="authentication-for-external-access"></a><span data-ttu-id="8121d-193">Проверка подлинности для внешнего доступа</span><span class="sxs-lookup"><span data-stu-id="8121d-193">Authentication for external access</span></span>

<span data-ttu-id="8121d-194">Существует определенный набор процедур проверки подлинности для Lync, SharePoint и Exchange для каждого из типов пользователей.</span><span class="sxs-lookup"><span data-stu-id="8121d-194">There is a specific set of authentication procedures for Lync, SharePoint, and Exchange for each of the user types.</span></span> <span data-ttu-id="8121d-195">Они более подробно описаны далее в этом документе.</span><span class="sxs-lookup"><span data-stu-id="8121d-195">They are described in more detail later in this document.</span></span> 
  
#### <a name="gateway-router-with-acls"></a><span data-ttu-id="8121d-196">Маршрутизатор шлюза со списками управления доступом</span><span class="sxs-lookup"><span data-stu-id="8121d-196">Gateway router with ACLs</span></span>

<span data-ttu-id="8121d-197">Маршрутизатор шлюза располагается на границе сети и направляет весь входящий и исходящий трафик в интрасеть и из нее.</span><span class="sxs-lookup"><span data-stu-id="8121d-197">The gateway router sits at the edge of the network and routes all incoming and outgoing traffic to and from the intranet.</span></span> 
  
#### <a name="remote-access-servers-for-lync-and-sharepoint"></a><span data-ttu-id="8121d-198">Серверы удаленного доступа для Lync и SharePoint</span><span class="sxs-lookup"><span data-stu-id="8121d-198">Remote access servers for Lync and SharePoint</span></span>

<span data-ttu-id="8121d-199">Эта топология включает пограничный сервер Lync и VPN-шлюз SharePoint или сервер DirectAccess.</span><span class="sxs-lookup"><span data-stu-id="8121d-199">This topology includes a Lync Edge server, and a SharePoint VPN gateway or DirectAccess server.</span></span> 
  
#### <a name="load-balancer-and-reverse-proxy-device"></a><span data-ttu-id="8121d-200">Подсистема балансировки нагрузки и устройство обратного прокси-сервера</span><span class="sxs-lookup"><span data-stu-id="8121d-200">Load balancer and reverse proxy device</span></span>

<span data-ttu-id="8121d-201">Вы можете использовать аппаратные и программные решения балансировки нагрузки для перенаправления трафика для сегментов, включая интерфейсные веб-серверы SharePoint и серверы клиентского доступа Exchange (касс).</span><span class="sxs-lookup"><span data-stu-id="8121d-201">You can use hardware or software load balancing solutions to redirect traffic for segments including SharePoint front-end web servers and Exchange Client Access Servers (CASs).</span></span> <span data-ttu-id="8121d-202">Эта топология отображает компоненты Lync VIP, SharePoint VIP и виртуальные IP-адреса Exchange в подсистеме балансировки нагрузки.</span><span class="sxs-lookup"><span data-stu-id="8121d-202">This topology shows Lync VIP, SharePoint VIP, and Exchange VIP components in the load balancer.</span></span> 
  
#### <a name="servers"></a><span data-ttu-id="8121d-203">Servers</span><span class="sxs-lookup"><span data-stu-id="8121d-203">Servers</span></span>

<span data-ttu-id="8121d-204">Существует четыре сервера: Lync, SharePoint, Exchange и сервер Office Web Apps.</span><span class="sxs-lookup"><span data-stu-id="8121d-204">There are four servers: Lync, SharePoint, Exchange, and Office Web Apps Server.</span></span> <span data-ttu-id="8121d-205">Каждый сервер может иметь три уровня: интерфейсный сервер, уровень клиентского доступа, уровень приложений, а также уровень базы данных/хранилища.</span><span class="sxs-lookup"><span data-stu-id="8121d-205">Each server can have three tiers: a front-end, client-access tier, an application tier, and a database/storage tier.</span></span>
  
#### <a name="front-end-client-access-tier"></a><span data-ttu-id="8121d-206">Уровень сервера переднего плана, клиентского доступа</span><span class="sxs-lookup"><span data-stu-id="8121d-206">Front-end, client-access tier</span></span>

<span data-ttu-id="8121d-207">На этом уровне есть компоненты на всех четырех серверах:</span><span class="sxs-lookup"><span data-stu-id="8121d-207">This tier has components on all four servers:</span></span> 
  
- <span data-ttu-id="8121d-208">Пул Lync (интерфейсный сервер).</span><span class="sxs-lookup"><span data-stu-id="8121d-208">Lync pool (front end).</span></span> <span data-ttu-id="8121d-209">На схеме показаны две базы данных Lync.</span><span class="sxs-lookup"><span data-stu-id="8121d-209">The diagram shows two Lync databases.</span></span> 
    
- <span data-ttu-id="8121d-210">Интерфейсный сервер и распределенный кэш SharePoint.</span><span class="sxs-lookup"><span data-stu-id="8121d-210">SharePoint front end and distributed cache.</span></span> <span data-ttu-id="8121d-211">На схеме показаны три базы данных SharePoint.</span><span class="sxs-lookup"><span data-stu-id="8121d-211">The diagram shows three SharePoint databases.</span></span> 
    
- <span data-ttu-id="8121d-212">ЦС Exchange.</span><span class="sxs-lookup"><span data-stu-id="8121d-212">Exchange CAS.</span></span> <span data-ttu-id="8121d-213">На схеме показаны две базы данных Exchange.</span><span class="sxs-lookup"><span data-stu-id="8121d-213">The diagram shows two Exchange databases.</span></span> 
    
- <span data-ttu-id="8121d-214">Сервер Office Web Apps.</span><span class="sxs-lookup"><span data-stu-id="8121d-214">Office Web Apps Server.</span></span> <span data-ttu-id="8121d-215">На схеме показаны две базы данных Office Web Apps.</span><span class="sxs-lookup"><span data-stu-id="8121d-215">The diagram shows two Office Web Apps databases.</span></span> 
    
#### <a name="application-tier"></a><span data-ttu-id="8121d-216">Уровень приложений</span><span class="sxs-lookup"><span data-stu-id="8121d-216">Application tier</span></span>

<span data-ttu-id="8121d-217">На этом уровне есть компоненты только на сервере SharePoint:</span><span class="sxs-lookup"><span data-stu-id="8121d-217">This tier has components only on the SharePoint server:</span></span> 
  
- <span data-ttu-id="8121d-218">Поиск (запрос, индекс, администратор).</span><span class="sxs-lookup"><span data-stu-id="8121d-218">Search (query, index, admin).</span></span> <span data-ttu-id="8121d-219">На схеме показаны три базы данных SharePoint.</span><span class="sxs-lookup"><span data-stu-id="8121d-219">The diagram shows three SharePoint databases.</span></span> 
    
- <span data-ttu-id="8121d-220">Пакетная обработка.</span><span class="sxs-lookup"><span data-stu-id="8121d-220">Batch processing.</span></span> <span data-ttu-id="8121d-221">На схеме показаны три базы данных SharePoint.</span><span class="sxs-lookup"><span data-stu-id="8121d-221">The diagram shows three SharePoint databases.</span></span> 
    
#### <a name="databasestorage-tier"></a><span data-ttu-id="8121d-222">Уровень базы данных или хранилища</span><span class="sxs-lookup"><span data-stu-id="8121d-222">Database/storage tier</span></span>

<span data-ttu-id="8121d-223">На этом уровне есть компоненты на серверах Lync, SharePoint и Exchange:</span><span class="sxs-lookup"><span data-stu-id="8121d-223">This tier has components on the Lync, SharePoint, and Exchange servers:</span></span> 
  
- <span data-ttu-id="8121d-224">База данных Lync (внутренний сервер).</span><span class="sxs-lookup"><span data-stu-id="8121d-224">Lync Database (backend).</span></span> <span data-ttu-id="8121d-225">На схеме показаны три базы данных Lync.</span><span class="sxs-lookup"><span data-stu-id="8121d-225">The diagram shows three Lync databases.</span></span> 
    
- <span data-ttu-id="8121d-226">База данных SharePoint.</span><span class="sxs-lookup"><span data-stu-id="8121d-226">SharePoint Database.</span></span> <span data-ttu-id="8121d-227">На схеме показаны три базы данных SharePoint.</span><span class="sxs-lookup"><span data-stu-id="8121d-227">The diagram shows three SharePoint databases.</span></span> 
    
- <span data-ttu-id="8121d-228">Сервер почтовых ящиков Exchange.</span><span class="sxs-lookup"><span data-stu-id="8121d-228">Exchange Mailbox server.</span></span> <span data-ttu-id="8121d-229">На схеме показаны два сервера почтовых ящиков Exchange.</span><span class="sxs-lookup"><span data-stu-id="8121d-229">The diagram shows two Exchange Mailbox servers.</span></span> 
    
<span data-ttu-id="8121d-230">Дополнительные сведения о компонентах, установленных в каждой из ролей SharePoint Server, представлены в разделе [оптимизированные топологии для sharepoint 2013](https://aka.ms/Ma5cgk).</span><span class="sxs-lookup"><span data-stu-id="8121d-230">For more information about components installed on each of the SharePoint server roles, see [Streamlined Topologies for SharePoint 2013](https://aka.ms/Ma5cgk).</span></span> 
  
#### <a name="description-of-how-traffic-moves-through-the-components-to-the-different-server-tiers"></a><span data-ttu-id="8121d-231">Описание способа перемещения трафика через компоненты на различные уровни серверов</span><span class="sxs-lookup"><span data-stu-id="8121d-231">Description of how traffic moves through the components to the different server tiers</span></span>

<span data-ttu-id="8121d-232">В этом разделе описывается, как запросы пользователей перемещаются по топологии сети.</span><span class="sxs-lookup"><span data-stu-id="8121d-232">This section describes how user requests move through the network topology.</span></span> 
  
#### <a name="authentication-and-routing-for-external-access"></a><span data-ttu-id="8121d-233">Проверка подлинности и маршрутизация для внешнего доступа</span><span class="sxs-lookup"><span data-stu-id="8121d-233">Authentication and routing for external access</span></span>

<span data-ttu-id="8121d-234">Существует три типа клиентов за прев своем сети и облачных службах, в том числе:</span><span class="sxs-lookup"><span data-stu-id="8121d-234">There are three different types of clients outside the network and cloud services, which include:</span></span> 
  
- <span data-ttu-id="8121d-235">Партнерские компании (деловые отношения) — внешние</span><span class="sxs-lookup"><span data-stu-id="8121d-235">Partner companies (business-to-business)-external</span></span> 
    
- <span data-ttu-id="8121d-236">Отдельные партнеры (SharePoint и анонимные (Lync)) — внешние</span><span class="sxs-lookup"><span data-stu-id="8121d-236">Individual partners (SharePoint and anonymous (Lync))-external</span></span> 
    
- <span data-ttu-id="8121d-237">Роуминг и удаленные сотрудники — внешние</span><span class="sxs-lookup"><span data-stu-id="8121d-237">Roaming and remote employees-external</span></span> 
    
<span data-ttu-id="8121d-238">Процесс проверки подлинности и маршрутизации для каждого внешнего типа пользователей описывается по отдельности.</span><span class="sxs-lookup"><span data-stu-id="8121d-238">The authentication and routing process for each external user type is described individually.</span></span> 
  
#### <a name="partner-companies-business-to-business-httpspartnerwebcontosocom"></a><span data-ttu-id="8121d-239">Партнерские компании (Business-to-предприятие) (https://partnerweb.contoso.com)</span><span class="sxs-lookup"><span data-stu-id="8121d-239">Partner companies (business-to-business) (https://partnerweb.contoso.com)</span></span>

- <span data-ttu-id="8121d-240">Lync: доверие федерации с другими организациями, Skype и общедоступная служба обмена мгновенными сообщениями (PIC) с AOL.</span><span class="sxs-lookup"><span data-stu-id="8121d-240">Lync: federation trust with other organizations, Skype and Public IM Connectivity (PIC) with AOL.</span></span> <span data-ttu-id="8121d-241">Трафик Федерации Lync проходит через маршрутизатор шлюза на пограничный сервер Lync, в виртуальный IP-адрес Lync (подсистема балансировки нагрузки/обратное прокси-сервер), а затем на сервер Lync Server.</span><span class="sxs-lookup"><span data-stu-id="8121d-241">The Lync federation traffic goes through the gateway router to the Lync Edge Server, to the Lync VIP (load balancer/reverse proxy server), and then to the Lync Server.</span></span> 
    
- <span data-ttu-id="8121d-242">SharePoint: доверенный поставщик удостоверений партнеров с проверкой подлинности SAML.</span><span class="sxs-lookup"><span data-stu-id="8121d-242">SharePoint: Trusted partner identity provider with SAML authentication.</span></span> <span data-ttu-id="8121d-243">Трафик клиента SharePoint проходит через маршрутизатор шлюза к виртуальному IP-адресу SharePoint (балансировщик нагрузки или обратный прокси-сервер), а затем к серверу SharePoint.</span><span class="sxs-lookup"><span data-stu-id="8121d-243">The SharePoint client traffic goes through the Gateway router to the SharePoint VIP (load balancer/reverse proxy server), and then to the SharePoint Server.</span></span> 
    
- <span data-ttu-id="8121d-244">Exchange: взаимная проверка подлинности TLS для почтового трафика, проверка подлинности SAML для федеративного общего доступа.</span><span class="sxs-lookup"><span data-stu-id="8121d-244">Exchange: Mutual Auth TLS for mail traffic, SAML authentication for Federated Sharing.</span></span> <span data-ttu-id="8121d-245">Трафик клиента Exchange проходит через маршрутизатор шлюза к виртуальному IP-адресу Exchange (балансировщик нагрузки/обратный прокси-сервер), а затем к серверу Exchange Server.</span><span class="sxs-lookup"><span data-stu-id="8121d-245">The Exchange client traffic goes through the Gateway router to the Exchange VIP (load balancer/reverse proxy server), and then to the Exchange Server.</span></span> 
    
- <span data-ttu-id="8121d-246">Трафик SMTP проходит через маршрутизатор шлюза и через виртуальный IP-адрес Exchange (подсистема балансировки нагрузки/обратного прокси-сервера) на сервер Exchange Server.</span><span class="sxs-lookup"><span data-stu-id="8121d-246">SMTP traffic goes through the Gateway router and through the Exchange VIP (load balancer/reverse proxy server) to the Exchange server.</span></span> 
    
#### <a name="individual-partners-sharepoint-and-anonymous-lync-httpspartnerwebcontosocom-and-httpsmeetcontosocom"></a><span data-ttu-id="8121d-247">Отдельные партнеры (SharePoint) и анонимные (Lync)https://partnerweb.contoso.com (иhttps://meet.contoso.com)</span><span class="sxs-lookup"><span data-stu-id="8121d-247">Individual partners (SharePoint) and anonymous (Lync) (https://partnerweb.contoso.com and https://meet.contoso.com)</span></span>

- <span data-ttu-id="8121d-248">Lync: анонимные пользователи могут присоединяться только к собраниям Lync, организованным сотрудниками.</span><span class="sxs-lookup"><span data-stu-id="8121d-248">Lync: anonymous users can only join Lync meetings organized by employees.</span></span> <span data-ttu-id="8121d-249">Трафик Федерации Lync проходит через маршрутизатор шлюза на пограничный сервер Lync, в виртуальный IP-адрес Lync (подсистема балансировки нагрузки/обратное прокси-сервер), а затем на сервер Lync Server.</span><span class="sxs-lookup"><span data-stu-id="8121d-249">The Lync federation traffic goes through the Gateway router to the Lync Edge Server, to the Lync VIP (load balancer/reverse proxy server), and then to the Lync Server.</span></span> 
    
- <span data-ttu-id="8121d-250">SharePoint: доверенный поставщик удостоверений партнеров с проверкой подлинности SAML или проверкой подлинности на основе форм.</span><span class="sxs-lookup"><span data-stu-id="8121d-250">SharePoint: Trusted partner identity provider with SAML authentication or forms-based authentication.</span></span> <span data-ttu-id="8121d-251">Трафик клиента SharePoint проходит через маршрутизатор шлюза к виртуальному IP-адресу SharePoint (балансировщик нагрузки или обратный прокси-сервер), а затем к серверу SharePoint.</span><span class="sxs-lookup"><span data-stu-id="8121d-251">The SharePoint client traffic goes through the Gateway router to the SharePoint VIP (load balancer/reverse proxy server), and then to the SharePoint Server.</span></span> 
    
- <span data-ttu-id="8121d-252">Exchange: не применяется.</span><span class="sxs-lookup"><span data-stu-id="8121d-252">Exchange: Does not apply.</span></span> 
    
- <span data-ttu-id="8121d-253">Веб-трафик Lync передается через маршрутизатор шлюза на пограничный сервер Lync, в виртуальный IP-адрес Lync (подсистема балансировки нагрузки/обратное прокси-сервер) на аппаратный балансировщик нагрузки, необходимый для трафика HTTPS, а затем на сервер Lync Server.</span><span class="sxs-lookup"><span data-stu-id="8121d-253">Lync Web traffic goes through the Gateway router to the Lync Edge Server, to the Lync VIP (load balancer/reverse proxy server), to a hardware load balancer, which is required for HTTPS traffic, and then to the Lync Server.</span></span> 
    
#### <a name="roaming-and-remote-employees"></a><span data-ttu-id="8121d-254">Перемещение и удаленные сотрудники</span><span class="sxs-lookup"><span data-stu-id="8121d-254">Roaming and remote employees</span></span>

1. https://intranet.contoso.com 
    
2. https://teams.contoso.com 
    
3. https://my.contoso.com
    
4. https://partnerweb.contoso.com 
    
5. https://mail.contoso.com* 
    
6. https://dial.contoso.com*
    
7. https://meet.contoso.com*
    
* <span data-ttu-id="8121d-255">URL-адрес Exchange содержит следующие виртуальные каталоги: автообнаружения, ECP, EWS, Microsoft-Server-ActiveSync, OAB, OWA, PowerShell</span><span class="sxs-lookup"><span data-stu-id="8121d-255">The Exchange URL has the following virtual directories: Autodiscover, ecp, EWS, Microsoft-Server-ActiveSync, OAB, owa, PowerShell</span></span> 
  
- <span data-ttu-id="8121d-256">Lync: TLS — ДСК или проверка подлинности NTLM.</span><span class="sxs-lookup"><span data-stu-id="8121d-256">Lync: TLS-DSK or NTLM authentication.</span></span> <span data-ttu-id="8121d-257">Трафик клиента Lync проходит через маршрутизатор шлюза на пограничный сервер Lync, в виртуальный IP-адрес Lync (подсистема балансировки нагрузки/обратное прокси-сервер), а затем на сервер Lync Server.</span><span class="sxs-lookup"><span data-stu-id="8121d-257">The Lync client traffic goes through the Gateway router to the Lync Edge Server, to the Lync VIP (load balancer/reverse proxy server), and then to the Lync Server.</span></span> 
    
- <span data-ttu-id="8121d-258">SharePoint: доменные службы Active Directory (AD DS), проверка подлинности на основе форм или проверка подлинности SAML.</span><span class="sxs-lookup"><span data-stu-id="8121d-258">SharePoint: Active Directory Domain Services (AD DS), forms-based authentication, or SAML authentication.</span></span> <span data-ttu-id="8121d-259">Трафик клиента SharePoint проходит через VPN-шлюз или сервер DirectAccess в виртуальный IP-адрес SharePoint (балансировщик нагрузки и обратный прокси-сервер), а затем на сервер SharePoint.</span><span class="sxs-lookup"><span data-stu-id="8121d-259">The SharePoint client traffic goes through the VPN gateway or the DirectAccess server to the SharePoint VIP (load balancer/reverse proxy server), and then to the SharePoint server.</span></span> 
    
- <span data-ttu-id="8121d-260">Exchange: обычная проверка подлинности через SSL (ActiveSync, автообнаружение), проверка подлинности на основе форм (OWA).</span><span class="sxs-lookup"><span data-stu-id="8121d-260">Exchange: Basic authentication over SSL (ActiveSync, Autodiscover), forms-based authentication (OWA).</span></span> <span data-ttu-id="8121d-261">Трафик клиента Exchange проходит через маршрутизатор шлюза к виртуальному IP-адресу Exchange (балансировщик нагрузки/обратный прокси-сервер), а затем к серверу Exchange Server.</span><span class="sxs-lookup"><span data-stu-id="8121d-261">The Exchange client traffic goes through the Gateway router to the Exchange VIP (load balancer/reverse proxy server), and then to the Exchange Server.</span></span> 
    
- <span data-ttu-id="8121d-262">Трафик клиента Lync проходит через маршрутизатор шлюза к ВИРТУАЛЬному подсистеме Lync (подсистема балансировки нагрузки и обратного прокси-сервера) к аппаратному подсистеме балансировки нагрузки, который требуется для трафика HTTPS, а затем на сервер Lync Server.</span><span class="sxs-lookup"><span data-stu-id="8121d-262">Lync client traffic goes through the Gateway router to the Lync VIP (load balancer/reverse proxy server) to a hardware load balancer, which is required for HTTPS traffic, and then to the Lync Server.</span></span> 
    
#### <a name="authentication-for-internal-access"></a><span data-ttu-id="8121d-263">Проверка подлинности для внутреннего доступа</span><span class="sxs-lookup"><span data-stu-id="8121d-263">Authentication for internal access</span></span>

#### <a name="internal-employees"></a><span data-ttu-id="8121d-264">Внутренние сотрудники</span><span class="sxs-lookup"><span data-stu-id="8121d-264">Internal employees</span></span>

> https://intranet.contoso.com 
    
> https://teams.contoso.com 
    
> https://my.contoso.com
    
> https://partnerweb.contoso.com
    
> https://mail.contoso.com* 
    
> https://dial.contoso.com 
    
> https://meet.contoso.com
    
> https://admin.contoso.com
    
- <span data-ttu-id="8121d-265">Lync: Kerberos, TLS — ДСК или проверка подлинности NTLM.</span><span class="sxs-lookup"><span data-stu-id="8121d-265">Lync: Kerberos, TLS-DSK, or NTLM authentication.</span></span> <span data-ttu-id="8121d-266">Трафик клиента Lync передается в виртуальный IP-адрес Lync (подсистема балансировки нагрузки или обратный прокси-сервер), а затем на сервер Lync Server.</span><span class="sxs-lookup"><span data-stu-id="8121d-266">The Lync client traffic goes to the Lync VIP (load balancer/reverse proxy server), and then to the Lync Server.</span></span> 
    
- <span data-ttu-id="8121d-267">SharePoint: доменные службы Active Directory (AD DS), проверка подлинности на основе форм или проверка подлинности SAML.</span><span class="sxs-lookup"><span data-stu-id="8121d-267">SharePoint: Active Directory Domain Services (AD DS), forms-based authentication, or SAML authentication.</span></span> <span data-ttu-id="8121d-268">Трафик клиента SharePoint передается в виртуальный IP-адрес SharePoint (подсистема балансировки нагрузки или обратный прокси-сервер), а затем на сервер SharePoint.</span><span class="sxs-lookup"><span data-stu-id="8121d-268">The SharePoint client traffic goes to the SharePoint VIP (load balancer/reverse proxy server), and then to the SharePoint Server.</span></span> 
    
- <span data-ttu-id="8121d-269">Exchange: AD DS, проверка подлинности на основе форм.</span><span class="sxs-lookup"><span data-stu-id="8121d-269">Exchange: AD DS, forms-based authentication.</span></span> <span data-ttu-id="8121d-270">Трафик клиента Exchange передается в виртуальный IP-адрес Exchange (подсистема балансировки нагрузки или обратный прокси-сервер), а затем на сервер Exchange Server.</span><span class="sxs-lookup"><span data-stu-id="8121d-270">The Exchange client traffic goes to the Exchange VIP (load balancer/reverse proxy server), and then to the Exchange Server.</span></span> 
    
- <span data-ttu-id="8121d-271">Трафик клиента Lync передается в виртуальный IP-адрес Lync (подсистема балансировки нагрузки или обратный прокси-сервер) на аппаратный балансировщик нагрузки, необходимый для трафика HTTPS, а затем на сервер Lync Server.</span><span class="sxs-lookup"><span data-stu-id="8121d-271">Lync client traffic goes to the Lync VIP (load balancer/reverse proxy server) to a hardware load balancer, which is required for HTTPS traffic, and then to the Lync Server.</span></span> 
    
#### <a name="cloud-based-email-traffic"></a><span data-ttu-id="8121d-272">Трафик электронной почты на основе облака</span><span class="sxs-lookup"><span data-stu-id="8121d-272">Cloud-based email traffic</span></span>

<span data-ttu-id="8121d-273">Облачный компонент для трафика электронной почты на основе SMTP состоит из почтовых узлов Интернета или Exchange Online Protection.</span><span class="sxs-lookup"><span data-stu-id="8121d-273">The cloud-based component for SMTP-based email traffic consists of either Internet Mail Hosts or Exchange Online Protection.</span></span>
  
<span data-ttu-id="8121d-274">Эти компоненты находят трафик электронной почты по сети с помощью SMTP.</span><span class="sxs-lookup"><span data-stu-id="8121d-274">These components move email traffic over the network using SMTP.</span></span> <span data-ttu-id="8121d-275">Трафик проходит через маршрутизатор шлюза в виртуальный IP-адрес Exchange (подсистема балансировки нагрузки или обратный прокси-сервер), а затем на сервер Exchange Server.</span><span class="sxs-lookup"><span data-stu-id="8121d-275">The traffic goes through the Gateway router to the Exchange VIP (load balancer/reverse proxy server), and then to the Exchange Server.</span></span> 
  
### <a name="network-traffic-legend"></a><span data-ttu-id="8121d-276">Условные обозначения сетевого трафика</span><span class="sxs-lookup"><span data-stu-id="8121d-276">Network traffic legend</span></span>

<span data-ttu-id="8121d-277">В поле условных обозначений показаны различные типы трафика, показанного на диаграмме в различных цветных строках, следующим образом:</span><span class="sxs-lookup"><span data-stu-id="8121d-277">The legend box graphically shows the different types of traffic depicted on the graph in different colored lines as follows:</span></span> 
  
- <span data-ttu-id="8121d-278">Зеленая линия: трафик SIP для Lync</span><span class="sxs-lookup"><span data-stu-id="8121d-278">Green line: Lync SIP traffic</span></span> 
    
- <span data-ttu-id="8121d-279">Синяя линия: веб-трафик Lync</span><span class="sxs-lookup"><span data-stu-id="8121d-279">Blue line: Lync Web traffic</span></span> 
    
- <span data-ttu-id="8121d-280">Фиолетовая линия: трафик клиента SharePoint</span><span class="sxs-lookup"><span data-stu-id="8121d-280">Purple line: SharePoint client traffic</span></span> 
    
- <span data-ttu-id="8121d-281">Оранжевая линия: трафик клиента Exchange</span><span class="sxs-lookup"><span data-stu-id="8121d-281">Orange line: Exchange client traffic</span></span> 
    
- <span data-ttu-id="8121d-282">Серая линия: трафик почтового сервера Exchange между локальной системой Exchange и Exchange Online Protection.</span><span class="sxs-lookup"><span data-stu-id="8121d-282">Gray line: Exchange Mail Server traffic between Exchange on-premises and Exchange Online Protection.</span></span> 
    
<span data-ttu-id="8121d-283">Различные типы трафика и используемые ими порты также описаны в поле Условные обозначения.</span><span class="sxs-lookup"><span data-stu-id="8121d-283">The different types of traffic and the ports that they use are also described in the legend box.</span></span> 
  
#### <a name="lync-sip-traffic-and-lync-web-traffic"></a><span data-ttu-id="8121d-284">Трафик SIP Lync и веб-трафик Lync</span><span class="sxs-lookup"><span data-stu-id="8121d-284">Lync SIP traffic and Lync web traffic</span></span>

<span data-ttu-id="8121d-285">Для взаимодействия с внешними пользователями пограничный сервер Lync использует следующие порты:</span><span class="sxs-lookup"><span data-stu-id="8121d-285">The Lync Edge Server uses the following ports for external user communication:</span></span> 
  
- <span data-ttu-id="8121d-286">Передача сигналов/обмена мгновенными сообщениями (SIP/SIMPLE): TCP-порт 443 (открытая для входящего трафика)</span><span class="sxs-lookup"><span data-stu-id="8121d-286">Signaling/IM traffic (SIP/SIMPLE): TCP port 443 (open for inbound traffic)</span></span> 
    
- <span data-ttu-id="8121d-287">Трафик веб-конференций (PSOM): TCP 443 (открыть для входящего трафика)</span><span class="sxs-lookup"><span data-stu-id="8121d-287">Web conferencing traffic (PSOM): TCP 443 (open for inbound traffic)</span></span> 
    
- <span data-ttu-id="8121d-288">Поток аудио-и видеоданных (SRTP): TCP 443, UDP 3478 и TCP 50000-59999 (необязательно) (открытая для входящего и исходящего трафика).</span><span class="sxs-lookup"><span data-stu-id="8121d-288">A/V traffic (SRTP): TCP 443, UDP 3478 and TCP 50000-59999 (optional) (open for inbound and outbound traffic)</span></span> 
    
<span data-ttu-id="8121d-289">Для связи Федерации пограничный сервер Lync использует следующие порты:</span><span class="sxs-lookup"><span data-stu-id="8121d-289">Lync Edge Server uses the following ports for federation communication:</span></span> 
  
- <span data-ttu-id="8121d-290">TCP-порты 5061 (SIP), 5269 (XMPP), 443 и UDP 3478 (SRTP) (открытая для входящего и исходящего трафика).</span><span class="sxs-lookup"><span data-stu-id="8121d-290">TCP ports 5061 (SIP), 5269 (XMPP), 443 and UDP 3478 (SRTP) (open for inbound and outbound traffic)</span></span> 
    
#### <a name="sharepoint-client-traffic"></a><span data-ttu-id="8121d-291">Трафик клиента SharePoint</span><span class="sxs-lookup"><span data-stu-id="8121d-291">SharePoint client traffic</span></span>

<span data-ttu-id="8121d-292">В SharePoint можно использовать TCP-порт 443 (SSL) для шифрования связи между клиентом и подсистемой балансировки нагрузки.</span><span class="sxs-lookup"><span data-stu-id="8121d-292">SharePoint can use TCP port 443 (SSL) for encrypted communication between the client and the load balancer.</span></span> <span data-ttu-id="8121d-293">Для внешнего доступа из Интернета этот порт должен быть открыт для входящего и исходящего трафика на маршрутизаторе шлюза (или внешнем брандмауэре).</span><span class="sxs-lookup"><span data-stu-id="8121d-293">For external access from the Internet, this port needs to be opened for inbound and outbound traffic on the gateway router (or external firewall).</span></span> 
  
#### <a name="exchange-client-traffic-and-exchange-mail-server-traffic"></a><span data-ttu-id="8121d-294">Трафик клиента Exchange и трафик почтового сервера Exchange</span><span class="sxs-lookup"><span data-stu-id="8121d-294">Exchange client traffic and Exchange mail server traffic</span></span>

<span data-ttu-id="8121d-295">Exchange использует TCP-порт 25 (SMTP) для обмена данными между серверами.</span><span class="sxs-lookup"><span data-stu-id="8121d-295">Exchange uses TCP port 25 (SMTP) for server-to-server communications.</span></span> <span data-ttu-id="8121d-296">Большая часть клиентского трафика (OWA, ActiveSync, автообнаружение, мобильный Outlook) обрабатывается через порт 443 (HTTPS).</span><span class="sxs-lookup"><span data-stu-id="8121d-296">Most client traffic (OWA, ActiveSync, Autodiscover, Outlook Anywhere) is handled over port 443 (HTTPS).</span></span> <span data-ttu-id="8121d-297">Если у вас есть клиенты POP или IMAP, порты 110 (POP3), 995 (Encrypting POP3), 143 (IMAP4), 993 (encrypted IMAP4) и 587 (SMTP) также используются для поддержки этих клиентов.</span><span class="sxs-lookup"><span data-stu-id="8121d-297">If you have POP or IMAP clients, ports 110 (POP3), 995 (encrypted POP3), 143 (IMAP4), 993 (encrypted IMAP4), and 587 (SMTP) are also used to support these clients.</span></span> 
  
#### <a name="more-on-lync-network-traffic"></a><span data-ttu-id="8121d-298">Дополнительные сведения о сетевом трафике Lync</span><span class="sxs-lookup"><span data-stu-id="8121d-298">More on Lync network traffic?</span></span>

<span data-ttu-id="8121d-299">Узнайте, как Lync Server поможет вашей организации обеспечить обмен мгновенными сообщениями, веб-конференции, общий доступ к приложениям и голосовую связь.</span><span class="sxs-lookup"><span data-stu-id="8121d-299">Learn how Lync Server can help your organization provide instant messaging, web conferencing, application sharing, and voice communication.</span></span> <span data-ttu-id="8121d-300">Для получения дополнительных сведений ознакомьтесь с разработкой [загрузок протокола Microsoft Lync Server 2013](https://aka.ms/G5jzjo).</span><span class="sxs-lookup"><span data-stu-id="8121d-300">For more information, see [Microsoft Lync Server 2013 Protocol Workloads Poster](https://aka.ms/G5jzjo).</span></span> 
  
<span data-ttu-id="8121d-301">На плакате также имеется QR-код для доступа к этой информации.</span><span class="sxs-lookup"><span data-stu-id="8121d-301">The poster also includes a QR code to access this information.</span></span> 
  

