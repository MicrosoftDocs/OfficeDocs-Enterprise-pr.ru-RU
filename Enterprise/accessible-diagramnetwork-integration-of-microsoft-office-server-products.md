---
title: "Доступная схема — сетевая интеграция серверных продуктов Microsoft Office"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 89f564eb-95c3-4077-bb92-75bf71b51270
description: "Данная статья представляет собой текстовую версию схемы \"Сетевая интеграция серверных продуктов Microsoft Office\"."
ms.openlocfilehash: 3fa27b99bf0babf00c536057b9d21da784b6d94f
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="accessible-diagram---network-integration-of-microsoft-office-server-products"></a><span data-ttu-id="448f1-103">Доступная схема — сетевая интеграция серверных продуктов Microsoft Office</span><span class="sxs-lookup"><span data-stu-id="448f1-103">Accessible diagram - Network Integration of Microsoft Office Server Products</span></span>

<span data-ttu-id="448f1-104">**Сводка:** Эта статья является доступным текстовая версия схемы с именем сети интеграции из продуктов Microsoft Office Server.</span><span class="sxs-lookup"><span data-stu-id="448f1-104">**Summary:** This article is an accessible text version of the diagram named Network Integration of Microsoft Office Server Products.</span></span>
  
<span data-ttu-id="448f1-p101">На этом плакате приводятся общие иллюстрация сетевая среда, которая включает в себя Lync Server 2013, SharePoint 2013 и Exchange Server 2013. Демонстрация следующих сетевых элементов, которые являются общими для всех таких продуктов: внутренний и удаленного доступа, проверки подлинности, клиентского трафика и трафик через общедоступные устройства.</span><span class="sxs-lookup"><span data-stu-id="448f1-p101">This poster provides a general illustration of a network environment that includes Lync Server 2013, SharePoint 2013, and Exchange Server 2013. It also illustrates the following networking elements that are common across these products: remote and internal access, authentication, client traffic, and routing traffic through shared devices.</span></span> 
  
## <a name="high-level-concepts-for-lync-exchange-sharepoint-server-and-office-web-apps"></a><span data-ttu-id="448f1-107">Общие понятия для Lync, Exchange, SharePoint Server и Office Web Apps</span><span class="sxs-lookup"><span data-stu-id="448f1-107">High-level concepts for Lync, Exchange, SharePoint Server, and Office Web Apps</span></span>

### <a name="about-the-design"></a><span data-ttu-id="448f1-108">Сведения о структуре</span><span class="sxs-lookup"><span data-stu-id="448f1-108">About the design</span></span>

#### <a name="streamlined-network-design"></a><span data-ttu-id="448f1-109">Упрощенная структура сети</span><span class="sxs-lookup"><span data-stu-id="448f1-109">Streamlined network design</span></span>

<span data-ttu-id="448f1-p102">Эта топология показана сети локальное развертывание SharePoint 2013, Exchange Server 2013 и Lync Server 2013. Также демонстрируется использование облачной службе Microsoft, Exchange Online Protection, которая обеспечивает защиту от нежелательной почты и вредоносных программ для входящего трафика Simple Mail Transfer Protocol (SMTP) из Интернета.</span><span class="sxs-lookup"><span data-stu-id="448f1-p102">This topology illustrates an on-premises network deployment of SharePoint 2013, Exchange Server 2013, and Lync Server 2013. It also shows the use of the Microsoft cloud-based service, Exchange Online Protection, which provides spam and malware protection for inbound Simple Mail Transfer Protocol (SMTP) traffic from the Internet.</span></span> 
  
<span data-ttu-id="448f1-p103">Эта структура сети упрощена до такой степени, что в ней используется минимальный набор сетевых функций. В ней не учитываются дополнительные функции безопасности и инфраструктуры, которые могут потребоваться некоторым организациям.  </span><span class="sxs-lookup"><span data-stu-id="448f1-p103">This network design is streamlined to a minimum set of network features. The design does not take into account additional security or infrastructure features that some organizations might require.</span></span> 
  
<span data-ttu-id="448f1-114">На этой схеме: </span><span class="sxs-lookup"><span data-stu-id="448f1-114">This diagram:</span></span> 
  
- <span data-ttu-id="448f1-115">представлен пример топологии сети, иллюстрирующий прохождение входящего и исходящего трафика через маршрутизатор шлюза и балансировку нагрузки для трафика сеанса клиента (внешнего и внутреннего) к серверам SharePoint, Exchange и Lync соответствующего уровня;  </span><span class="sxs-lookup"><span data-stu-id="448f1-115">Provides an example network topology illustrating inbound and outbound traffic through a gateway router and load balancing of client session traffic (external and internal) to the appropriate SharePoint, Exchange, and Lync server tiers.</span></span> 
    
- <span data-ttu-id="448f1-116">показано использование необязательных серверов удаленного доступа, например стороннего VPN-шлюза или сервера DirectAccess, для обеспечения безопасной связи с разъездными или удаленными сотрудниками; </span><span class="sxs-lookup"><span data-stu-id="448f1-116">Shows the use of optional remote access servers, such as a third-party VPN gateway or DirectAccess server, to provide secure communication for roaming or remote employees.</span></span> 
    
- <span data-ttu-id="448f1-117">представлены подробные сведения о потоке трафика SharePoint, Exchange и Lync от клиента к серверам платформы всех уровней; </span><span class="sxs-lookup"><span data-stu-id="448f1-117">Details the SharePoint, Exchange, and Lync traffic flow from the client to each platform server tier.</span></span> 
    
- <span data-ttu-id="448f1-118">определены типы подключений для удаленного или внутреннего доступа на основе клиентов (например, для партнеров или сотрудников) и используемые методы проверки подлинности; </span><span class="sxs-lookup"><span data-stu-id="448f1-118">Identifies the type of remote or internal access connection based on client (such as partner or employee), and the authentication method used.</span></span> 
    
- <span data-ttu-id="448f1-119">Устранение платформы SharePoint, Exchange и Lync с необходимые роли сервера, идентифицирующий переднего плана, приложения, базы данных и других уровнях.</span><span class="sxs-lookup"><span data-stu-id="448f1-119">Breaks down the SharePoint, Exchange, and Lync platforms by required server roles, identifying the front end, application, database, and other levels.</span></span> 
    
<span data-ttu-id="448f1-p104">Архитектура, используемая здесь для SharePoint, Lync и Exchange, не является предпочитаемым способом реализации этих платформ. Она приведена исключительно в качестве примера, так как топологии зависят от уникальных требований к сети и соображений безопасности. </span><span class="sxs-lookup"><span data-stu-id="448f1-p104">The architecture used here for SharePoint, Lync, and Exchange does not suggest a preferred way of implementing these platforms. It merely provides an example as topologies differ based on unique network requirements and security considerations.</span></span> 
  
#### <a name="gateway-router"></a><span data-ttu-id="448f1-122">Маршрутизатор шлюза</span><span class="sxs-lookup"><span data-stu-id="448f1-122">Gateway router</span></span>

<span data-ttu-id="448f1-p105">В этой топологии маршрутизатор шлюза находится на краю сети и выполняет маршрутизацию всего входящего и исходящего трафика в интрасеть и из нее. Кроме того, могут использоваться другие компоненты, заполняющие разрыв между показанными маршрутизатором шлюза и подсистемой балансировки нагрузки, например несколько уровней брандмауэров. Эта топология — всего лишь один из способов развертывания вашей сети. В этой конфигурации шлюз настроен с использованием списков управления доступом, чтобы разрешать только определенный входящий и исходящий IP-трафик в интерфейсах маршрутизатора. Кроме того, можно применить списки управления доступом, средства расширенной проверки или функцию преобразования сетевых адресов к другим устройствам, например брандмауэрам, во всей вашей сети. </span><span class="sxs-lookup"><span data-stu-id="448f1-p105">For this topology, the gateway router sits at the edge of the network and routes all incoming and outgoing traffic to and from the intranet. Alternatively, there could also be other components that bridge the gap between the gateway router and the load balancer shown, such as multiple layers of firewalls. This topology represents just one way to deploy your network out of many. In this configuration, the gateway is configured with access control lists (ACLs) to permit very specific incoming and outgoing IP-based traffic on the router interfaces. ACLs, advanced inspection, or Network Address Translation (NAT) can also be performed on other devices, such as firewalls, throughout your network.</span></span> 
  
#### <a name="load-balancer-and-reverse-proxy-devices"></a><span data-ttu-id="448f1-128">Устройства подсистемы балансировки нагрузки и обратного прокси-сервера</span><span class="sxs-lookup"><span data-stu-id="448f1-128">Load balancer and reverse proxy devices</span></span>

<span data-ttu-id="448f1-p106">Решения балансировки нагрузки оборудования или программного обеспечения можно использовать для перенаправления потока данных для сегментов, включая SharePoint интерфейсных веб-серверов и серверов клиентского доступа Exchange (классов). В некоторых случаях является оптимальным на использование подсистему балансировки нагрузки на основе оборудования уровня 7 сохраняемость требований к, как его можно лучше выполнять с помощью информации в запросе, такие как файлы cookie или заголовки. Тем не менее факторов, таких как затраты и увеличивает и рабочей нагрузки из такого решения может быть нежелательно для конкретных потребностей. Помните о следующих балансировки нагрузки между SharePoint, Exchange и Lync.</span><span class="sxs-lookup"><span data-stu-id="448f1-p106">You can use hardware or software load balancing solutions to redirect traffic for segments including SharePoint front-end web servers and Exchange Client Access Servers (CASs). In some cases it's optimal to use a layer 7 hardware-based load balancer for persistence requirements as it can perform better by using information in the request, such as cookies or headers. However, factors like cost and increased utilization and workload from such a solution might not be desirable for your specific needs. Consider the following points for load balancing across SharePoint, Exchange, and Lync:</span></span> 
  
- <span data-ttu-id="448f1-p107">SharePoint — для SharePoint 2013 Включение сходства для интерфейсных веб-серверов не нужно. Как правило это будет использоваться для создания решения о сеансах и избежать нескольких запросов проверки подлинности клиентов на каждом интерфейсном веб-сервере. Новые службы распределенного кэша в SharePoint 2013 хранит и распределяет маркеры входа в систему на веб-серверах в ферме SharePoint.</span><span class="sxs-lookup"><span data-stu-id="448f1-p107">SharePoint - For SharePoint 2013, you do not need to enable affinity for your front-end web servers. Normally, this would be used for creating sticky sessions and avoiding multiple authentication requests from clients to each front-end web server. The new Distributed Cache service in SharePoint 2013 stores and distributes logon tokens across the web servers of the SharePoint farm.</span></span> 
    
- <span data-ttu-id="448f1-p108">Exchange - в Exchange 2013, роль сервера клиентского доступа позволяет использовать Балансировка нагрузки на уровне 4, распределения запросов на транспортном уровне. Это может существенно сократить использование балансировки нагрузки и рабочей нагрузки.</span><span class="sxs-lookup"><span data-stu-id="448f1-p108">Exchange - In Exchange 2013, the CAS role is designed to use layer 4 load balancing, distributing requests at the transport layer. This can significantly decrease load balancer utilization and workload.</span></span> 
    
- <span data-ttu-id="448f1-p109">Lync - Балансировка нагрузки на доменных имен (DNS) рекомендуется для трафика Session Initiation Protocol (SIP) для пулов Lync. Аппаратная Балансировка (аппаратного балансировщика Нагрузки) нагрузки является обязательным для трафика Lync Web (HTTPS).</span><span class="sxs-lookup"><span data-stu-id="448f1-p109">Lync - Domain Name System (DNS) load balancing is recommended for Session Initiation Protocol (SIP) traffic for Lync pools. Hardware load balancing (HLB) is required for Lync Web (HTTPS) traffic.</span></span> 
    
### <a name="remote-access-options"></a><span data-ttu-id="448f1-140">Средства удаленного доступа</span><span class="sxs-lookup"><span data-stu-id="448f1-140">Remote access options</span></span>

<span data-ttu-id="448f1-p110">Существует несколько способов публикации ресурсов интрасети в Интернете для партнеров или предоставления безопасного удаленного доступа для выездных или удаленных сотрудников. Это, например, обратные прокси-серверы, технология DirectAccess и сторонние VPN-шлюзы. Рассматриваемые далее решения для удаленного доступа предоставляют соответствующие возможности для серверов SharePoint, Lync и Exchange, а также для любого их сочетания в локальном развертывании. Тем не менее некоторые способы удаленного доступа могут не работать с определенными решениями.  </span><span class="sxs-lookup"><span data-stu-id="448f1-p110">There are several options that can publish intranet resources for partners on the Internet or provide secure remote access for remote or roaming employees. Such examples include reverse proxies, DirectAccess, and third-party VPN gateways. The remote access solutions discussed later in this section are possibilities for SharePoint, Lync, and Exchange, or any combination of these servers in an on-premises deployment. However, some remote options might not work with a particular solution.</span></span> 
  
<span data-ttu-id="448f1-p111">Обратный прокси-сервер — обратный прокси-сервер поддерживает шифрование трафика, например Secure Sockets Layer (SSL) и с ним, которые могут публиковать приложения интрасети и веб-ресурсы для прошедших проверку пользователей и партнеров в Интернете. Например, Microsoft Forefront Unified Access Gateway (UAG). Многие аппаратных балансировщиков нагрузки также поддерживает функции обратного прокси-сервера. Тем не менее будут по-прежнему действительный сценарии использования отдельных решения на основе потребности и требования, такие как изоляции трафика, разделение ответственности безопасности и оптимизации производительности.</span><span class="sxs-lookup"><span data-stu-id="448f1-p111">Reverse Proxy - A reverse proxy supports traffic encryption, such as Secure Sockets Layer (SSL), and with it you can publish intranet applications and web resources to authenticated users and partners on the Internet. An example is Microsoft Forefront Unified Access Gateway (UAG). Many hardware load balancers also support reverse proxy functionality. However, there are still valid scenarios for using a standalone solution based on your needs and requirements, such as traffic isolation, security compartmentalization, and performance optimization.</span></span> 
  
<span data-ttu-id="448f1-149">Преимущества и соображения, связанные с использованием обратных прокси-серверов. </span><span class="sxs-lookup"><span data-stu-id="448f1-149">Reverse-proxy benefits and considerations:</span></span> 
  
- <span data-ttu-id="448f1-150">Обратные прокси-серверы обеспечивают защищенный доступ с проверкой подлинности для партнеров или пользователей, использующих ресурсы интрасети. При этом между клиентом и обратным прокси-сервером используется SSL (TCP-порт 443). </span><span class="sxs-lookup"><span data-stu-id="448f1-150">Provides authenticated and secured access for partners or users accessing intranet resources (uses SSL (TCP 443) between the client and reverse proxy server).</span></span> 
    
- <span data-ttu-id="448f1-p112">Для Exchange преимущество использования обратного прокси-сервера, например Forefront UAG, состоит в возможности предварительной проверки подлинности перед получением доступа к серверу клиентского доступа Exchange. Чтобы войти во внутреннюю сеть, пользователи с удаленным доступом, использующие опубликованные приложения, например Outlook Web Access, могут проходить проверку подлинности с помощью основного метода, а также с помощью методов NTLM или Kerberos. </span><span class="sxs-lookup"><span data-stu-id="448f1-p112">For Exchange, a benefit of using a reverse proxy such as Forefront UAG is pre-authentication before accessing the Exchange Client access server. Remote access users using published applications such as Outlook Web Access (OWA) can authenticate with the basic, NTLM, or Kerberos methods before they reach the internal network.</span></span> 
    
- <span data-ttu-id="448f1-153">Для Exchange и SharePoint такие решения, как Forefront UAG, могут завершать SSL-подключения и уменьшать нагрузку на сервер ресурсов в интрасети. При этом они обеспечивают единую точку управления сертификатами. </span><span class="sxs-lookup"><span data-stu-id="448f1-153">For Exchange and SharePoint, solutions like Forefront UAG can terminate SSL connections and decrease the load of the intranet resources server while providing a single point of management for certificates.</span></span> 
    
- <span data-ttu-id="448f1-p113">Для Lync Web (HTTPS) трафик проходит через обратный прокси-сервер (TCP 443) связь с клиентами. Прокси-серверы обратного прокси-сервера HTTPS подключения к Lync веб-служб, сервер клиентского доступа Exchange и Office Web Apps. Lync Server 2013 не поддерживает UAG.</span><span class="sxs-lookup"><span data-stu-id="448f1-p113">For Lync, Web (HTTPS) traffic goes through the reverse proxy (TCP 443) for client communication. The reverse proxy proxies the HTTPS connection to Lync Web Services, Exchange CAS, and Office Web Apps. Lync Server 2013 does not support UAG.</span></span> 
    
<span data-ttu-id="448f1-p114">DirectAccess - технология удаленного доступа, которая использует безопасности протокола IP (IPsec) для проверки подлинности и шифрования трафика между сервером и клиентом DirectAccess. DirectAccess предоставляет одновременный доступ к ресурсам Интернета и интрасети для перемещения и удаленных сотрудников без необходимости установки подключения.</span><span class="sxs-lookup"><span data-stu-id="448f1-p114">DirectAccess - A remote access technology that relies on Internet Protocol security (IPsec) for authentication and for encrypting traffic between the DirectAccess client and server. DirectAccess provides simultaneous access to both Internet and intranet resources for roaming and remote employees without having to initiate a connection.</span></span> 
  
<span data-ttu-id="448f1-159">Ниже приведены соображения касательно DirectAccess, на которые необходимо обратить внимание. </span><span class="sxs-lookup"><span data-stu-id="448f1-159">DirectAccess points to consider:</span></span> 
  
- <span data-ttu-id="448f1-160">Для обмена данными между клиентом и сервером DirectAccess используется защищенный трафик IPsec (протоколы 50 и 51, а также UDP 500). </span><span class="sxs-lookup"><span data-stu-id="448f1-160">DirectAccess uses IPsec protected traffic (protocol 50 and 51 and UDP 500) between the DirectAccess client and server.</span></span> 
    
- <span data-ttu-id="448f1-161">DirectAccess для Windows Server 2012 и Windows 8 не требует развертывания инфраструктуры открытых ключей для проверки подлинности сервера и клиента. </span><span class="sxs-lookup"><span data-stu-id="448f1-161">DirectAccess for Windows Server 2012 and Windows 8 does not need a public key infrastructure (PKI) deployment for server and client authentication.</span></span> 
    
- <span data-ttu-id="448f1-162">Мы не рекомендуем с помощью DirectAccess с Lync Server 2013 из-за проблем задержка аудио- и видеоконференций, связанных с IPsec шифрования и расшифровки.</span><span class="sxs-lookup"><span data-stu-id="448f1-162">We recommend against using DirectAccess with Lync Server 2013 because of audio and video latency issues associated with IPsec encryption and decryption.</span></span> 
    
    <span data-ttu-id="448f1-p115">Шлюз VPN - типичного VPN шлюзы предоставляют подключения удаленного доступа, в которой клиентский компьютер удаленного доступа логически отображаться на интрасети через подключение к Туннелированные и инициированных пользователем. Можно использовать единую удаленного доступа в Windows Server 2012 или несколько решений сторонних производителей для обеспечения безопасный доступ к интрасети для мобильных или удаленных сотрудников. VPN не рекомендуется для Lync. Трафик Lync следует использовать пограничных серверов и разделение туннелирование.</span><span class="sxs-lookup"><span data-stu-id="448f1-p115">VPN Gateway - Typical VPN gateways provide a remote access connection in which a remote access client computer is logically projected onto the intranet through a tunneled and user-initiated connection. You can use Unified Remote Access in Windows Server 2012 or several third-party solutions to provide secured access to the intranet for roaming or remote employees. VPN is not recommended for Lync. Remote Lync traffic should use the Edge Servers and split tunneling.</span></span> 
    
### <a name="domain-name-system-dns-considerations"></a><span data-ttu-id="448f1-167">Соображения касательно DNS</span><span class="sxs-lookup"><span data-stu-id="448f1-167">Domain Name System (DNS) considerations</span></span>

<span data-ttu-id="448f1-168">Вам потребуется спланировать набор записей DNS, который позволит пользователям в Интернете и в интрасети сопоставлять DNS-имена с соответствующими IP-адресами. </span><span class="sxs-lookup"><span data-stu-id="448f1-168">You need to plan for the set of DNS records that allow both Internet and intranet users to resolve DNS names to the appropriate IP addresses.</span></span> 
  
- <span data-ttu-id="448f1-169">Для партнеров, получающих доступ через Интернет, и выездных и удаленных сотрудников записи DNS, зарегистрированные с помощью DNS-серверов в Интернете, обеспечивают сопоставление с набором общедоступных IP-адресов, соответствующих маршрутизатору шлюза, пограничному серверу Lync, набору виртуальных IP-адресов в подсистеме балансировки нагрузки и DirectAccess или VPN-шлюзу. </span><span class="sxs-lookup"><span data-stu-id="448f1-169">For Internet-based partners and roaming or remote employees, DNS records registered with Internet DNS servers provide resolution to the set of public IP addresses corresponding to the gateway router, the Lync Edge Server, the set of virtual IP addresses (VIPs) on the load balancer, and the DirectAccess or VPN gateway as needed.</span></span> 
    
- <span data-ttu-id="448f1-170">Для пользователей, получающих доступ из интрасети, записи DNS, зарегистрированные с помощью DNS-серверов в интрасети, обеспечивают сопоставление с набором виртуальных IP-адресов в подсистеме балансировки нагрузки для доступа к ресурсам SharePoint, Lync и Exchange. </span><span class="sxs-lookup"><span data-stu-id="448f1-170">For intranet-based users, DNS records registered with intranet DNS servers provide resolution to the set of virtual IP addresses (VIPs) on the load balancer for access to SharePoint, Lync, and Exchange resources.</span></span> 
    
- <span data-ttu-id="448f1-p116">Клиенты DirectAccess используют DNS-серверы интрасети для имен, входящих в пространство имен DNS интрасети, и DNS-серверы в Интернете — для всех остальных имен. Чтобы упростить эксплуатацию DirectAccess, рассмотрим использование разделенной реализации DNS, в которой для имен в интрасети и в Интернете применяются различные пространства имен DNS. Например, можно использовать имя contoso.com для пространства имен в Интернете и имя corp.contoso.com для пространства имен в интрасети. </span><span class="sxs-lookup"><span data-stu-id="448f1-p116">DirectAccess clients use intranet DNS servers for names corresponding to the intranet DNS name space and Internet DNS servers for names that do not. To simplify the operation of DirectAccess, consider the use of a split DNS implementation that uses different DNS namespaces for intranet and Internet-based names. For example, use contoso.com for Internet namespace and corp.contoso.com for the intranet namespace.</span></span> 
    
- <span data-ttu-id="448f1-p117">Exchange использует модель разделенной DNS, в которой сопоставленный IP-адрес узла будет различным для трафика из общедоступной сети и трафика в корпоративной сети. Как минимум, вам понадобятся записи DNS для URL-адресов Outlook Web Access, службы автообнаружения и ActiveSync для трафика от клиента и запись MX для входящей почты. </span><span class="sxs-lookup"><span data-stu-id="448f1-p117">Exchange uses a split DNS model where host to IP resolution differs on publicly routed traffic from that on the corporate network. At a minimum, you need to have DNS records for OWA, Autodiscover, ActiveSync URLs for client traffic, and an MX record for inbound mail.</span></span> 
    
- <span data-ttu-id="448f1-176">Если вы используете Exchange Online Protection, то запись MX будет указывать на эту службу, а не на вашу ферму Exchange. </span><span class="sxs-lookup"><span data-stu-id="448f1-176">If you are using Exchange Online Protection (EOP), your MX record points to that service instead of your Exchange farm.</span></span> 
    
- <span data-ttu-id="448f1-177">При использовании Exchange вам потребуется доказательство права собственности на запись TXT в общедоступном DNS и код организации федерации для настройки федеративного общего доступа. </span><span class="sxs-lookup"><span data-stu-id="448f1-177">For Exchange, you need a proof of ownership TXT record in your public DNS, and a Federation Org ID to set up federated sharing.</span></span> 
    
- <span data-ttu-id="448f1-178">Можно настроить VPN-клиенты удаленного доступа таким образом, чтобы когда VPN-подключение удаленного доступа активно, они использовали только DNS-серверы в интрасети. </span><span class="sxs-lookup"><span data-stu-id="448f1-178">Remote access VPN clients can be configured to use only intranet DNS servers when the remote access VPN connection is active.</span></span> 
    
### <a name="diagram-description"></a><span data-ttu-id="448f1-179">Описание схемы</span><span class="sxs-lookup"><span data-stu-id="448f1-179">Diagram Description</span></span>

<span data-ttu-id="448f1-p118">На этой схеме представлен пример топологии сети, иллюстрирующий прохождение входящего и исходящего трафика через маршрутизатор шлюза и балансировку нагрузки для трафика сеанса клиента (внешнего и внутреннего) к серверам SharePoint, Exchange и Lync соответствующего уровня. Описание этой схемы состоит из двух указанных ниже частей. </span><span class="sxs-lookup"><span data-stu-id="448f1-p118">This diagram provides an example network topology illustrating inbound and outbound traffic through a gateway router and load balancing of client session traffic (external and internal) to the appropriate SharePoint, Exchange, and Lync server tiers. The description of this diagram is divided into two parts:</span></span> 
  
- <span data-ttu-id="448f1-182">Описание компонентов, показанных на схеме </span><span class="sxs-lookup"><span data-stu-id="448f1-182">Description of components shown in the diagram</span></span> 
    
- <span data-ttu-id="448f1-183">Описание того, как трафик проходит через различные компоненты к уровням серверов SharePoint, Exchange, Lync и Office Web Apps. </span><span class="sxs-lookup"><span data-stu-id="448f1-183">Description of how traffic moves through the components to the SharePoint, Exchange, Lync, and Office Web Apps server tiers.</span></span> 
    
#### <a name="description-of-components-shown-in-the-diagram"></a><span data-ttu-id="448f1-184">Описание компонентов, показанных на схеме </span><span class="sxs-lookup"><span data-stu-id="448f1-184">Description of components shown in the diagram</span></span>

#### <a name="user-types"></a><span data-ttu-id="448f1-185">Типы пользователей</span><span class="sxs-lookup"><span data-stu-id="448f1-185">User types</span></span>

<span data-ttu-id="448f1-186">Существуют четыре указанных ниже типа пользователей. Три из них располагаются за пределами сети и облачных служб, а четвертый — внутри них. </span><span class="sxs-lookup"><span data-stu-id="448f1-186">There are four different types of users, three outside the network and cloud services and one internal, which include:</span></span> 
  
- <span data-ttu-id="448f1-187">Компании-партнеры (бизнес-бизнес) — внешние пользователи </span><span class="sxs-lookup"><span data-stu-id="448f1-187">Partner companies (business-to-business)-external</span></span> 
    
- <span data-ttu-id="448f1-188">Индивидуальные партнеры (SharePoint) и анонимные пользователи (Lync) — внешние пользователи </span><span class="sxs-lookup"><span data-stu-id="448f1-188">Individual partners (SharePoint and anonymous (Lync))-external</span></span> 
    
- <span data-ttu-id="448f1-189">Выездные и удаленные сотрудники — внешние пользователи </span><span class="sxs-lookup"><span data-stu-id="448f1-189">Roaming and remote employees-external</span></span> 
    
- <span data-ttu-id="448f1-190">Внутренние сотрудники</span><span class="sxs-lookup"><span data-stu-id="448f1-190">Internal employees</span></span> 
    
#### <a name="cloud-based-email-traffic"></a><span data-ttu-id="448f1-191">Трафик облачной электронной почты</span><span class="sxs-lookup"><span data-stu-id="448f1-191">Cloud-based email traffic</span></span>

<span data-ttu-id="448f1-192">На схеме имеется облачный компонент для SMTP-трафика электронной почты. Это либо узлы электронной почты в Интернете, либо Exchange Online Protection. </span><span class="sxs-lookup"><span data-stu-id="448f1-192">There is a cloud-based component for SMTP-based email traffic, either Internet Mail Hosts or Exchange Online Protection.</span></span> 
  
#### <a name="authentication-for-external-access"></a><span data-ttu-id="448f1-193">Проверка подлинности для внешнего доступа</span><span class="sxs-lookup"><span data-stu-id="448f1-193">Authentication for external access</span></span>

<span data-ttu-id="448f1-p119">Существует определенный набор процедур проверки подлинности для Lync, SharePoint и Exchange для каждого типа пользователей. Они будут описаны более подробно далее в этом документе. </span><span class="sxs-lookup"><span data-stu-id="448f1-p119">There is a specific set of authentication procedures for Lync, SharePoint, and Exchange for each of the user types. They are described in more detail later in this document.</span></span> 
  
#### <a name="gateway-router-with-acls"></a><span data-ttu-id="448f1-196">Маршрутизатор шлюза со списками управления доступом</span><span class="sxs-lookup"><span data-stu-id="448f1-196">Gateway router with ACLs</span></span>

<span data-ttu-id="448f1-197">Маршрутизатор шлюза находится на границе сети и выполняет маршрутизацию всего входящего и исходящего трафика в интрасеть и из нее. </span><span class="sxs-lookup"><span data-stu-id="448f1-197">The gateway router sits at the edge of the network and routes all incoming and outgoing traffic to and from the intranet.</span></span> 
  
#### <a name="remote-access-servers-for-lync-and-sharepoint"></a><span data-ttu-id="448f1-198">Серверы удаленного доступа для Lync и SharePoint</span><span class="sxs-lookup"><span data-stu-id="448f1-198">Remote access servers for Lync and SharePoint</span></span>

<span data-ttu-id="448f1-199">Эта топология включает пограничный сервер Lync и VPN-шлюз SharePoint или сервер DirectAccess. </span><span class="sxs-lookup"><span data-stu-id="448f1-199">This topology includes a Lync Edge server, and a SharePoint VPN gateway or DirectAccess server.</span></span> 
  
#### <a name="load-balancer-and-reverse-proxy-device"></a><span data-ttu-id="448f1-200">Устройство подсистемы балансировки нагрузки и обратного прокси-сервера</span><span class="sxs-lookup"><span data-stu-id="448f1-200">Load balancer and reverse proxy device</span></span>

<span data-ttu-id="448f1-p120">Вы можете использовать как аппаратные, так и программные решения для балансировки нагрузки, чтобы перенаправлять трафик в различные сегменты, включая веб-серверы переднего плана SharePoint и серверы клиентского доступа Exchange. В этой топологии показаны компоненты виртуальных IP-адресов Lync, SharePoint и Exchange в подсистеме балансировки нагрузки. </span><span class="sxs-lookup"><span data-stu-id="448f1-p120">You can use hardware or software load balancing solutions to redirect traffic for segments including SharePoint front-end web servers and Exchange Client Access Servers (CASs). This topology shows Lync VIP, SharePoint VIP, and Exchange VIP components in the load balancer.</span></span> 
  
#### <a name="servers"></a><span data-ttu-id="448f1-203">Серверы</span><span class="sxs-lookup"><span data-stu-id="448f1-203">Servers</span></span>

<span data-ttu-id="448f1-p121">Существует четыре сервера: Lync, SharePoint, Exchange и сервера Office Web Apps. Каждый сервер может иметь три уровня: сервером переднего плана, клиентского доступа уровня, уровня приложений и уровня хранилища и базы данных.</span><span class="sxs-lookup"><span data-stu-id="448f1-p121">There are four servers: Lync, SharePoint, Exchange, and Office Web Apps Server. Each server can have three tiers: a front-end, client-access tier, an application tier, and a database/storage tier.</span></span>
  
#### <a name="front-end-client-access-tier"></a><span data-ttu-id="448f1-206">Уровень переднего плана для клиентского доступа</span><span class="sxs-lookup"><span data-stu-id="448f1-206">Front-end, client-access tier</span></span>

<span data-ttu-id="448f1-207">Компоненты этого уровня имеются на всех четырех серверах. </span><span class="sxs-lookup"><span data-stu-id="448f1-207">This tier has components on all four servers:</span></span> 
  
- <span data-ttu-id="448f1-p122">Пул Lync (переднего плана). На схеме показаны две базы данных Lync. </span><span class="sxs-lookup"><span data-stu-id="448f1-p122">Lync pool (front end). The diagram shows two Lync databases.</span></span> 
    
- <span data-ttu-id="448f1-p123">Передний план и распределенный кэш SharePoint. На схеме показаны три базы данных SharePoint.  </span><span class="sxs-lookup"><span data-stu-id="448f1-p123">SharePoint front end and distributed cache. The diagram shows three SharePoint databases.</span></span> 
    
- <span data-ttu-id="448f1-p124">Сервер клиентского доступа Exchange. На схеме показаны две базы данных Exchange. </span><span class="sxs-lookup"><span data-stu-id="448f1-p124">Exchange CAS. The diagram shows two Exchange databases.</span></span> 
    
- <span data-ttu-id="448f1-p125">Сервер Office Web Apps. На схеме показаны две базы данных Office Web Apps. </span><span class="sxs-lookup"><span data-stu-id="448f1-p125">Office Web Apps Server. The diagram shows two Office Web Apps databases.</span></span> 
    
#### <a name="application-tier"></a><span data-ttu-id="448f1-216">Уровень приложений</span><span class="sxs-lookup"><span data-stu-id="448f1-216">Application tier</span></span>

<span data-ttu-id="448f1-217">Компоненты этого уровня имеются только в сервере SharePoint. </span><span class="sxs-lookup"><span data-stu-id="448f1-217">This tier has components only on the SharePoint server:</span></span> 
  
- <span data-ttu-id="448f1-p126">Поиск (запросы, индексирование, администрирование). На схеме показаны три базы данных SharePoint. </span><span class="sxs-lookup"><span data-stu-id="448f1-p126">Search (query, index, admin). The diagram shows three SharePoint databases.</span></span> 
    
- <span data-ttu-id="448f1-p127">Пакетная обработка. На схеме показаны три базы данных SharePoint.  </span><span class="sxs-lookup"><span data-stu-id="448f1-p127">Batch processing. The diagram shows three SharePoint databases.</span></span> 
    
#### <a name="databasestorage-tier"></a><span data-ttu-id="448f1-222">Уровень базы данных и хранилища</span><span class="sxs-lookup"><span data-stu-id="448f1-222">Database/storage tier</span></span>

<span data-ttu-id="448f1-223">Компоненты этого уровня имеются на серверах Lync, SharePoint и Exchange. </span><span class="sxs-lookup"><span data-stu-id="448f1-223">This tier has components on the Lync, SharePoint, and Exchange servers:</span></span> 
  
- <span data-ttu-id="448f1-p128">База данных Lync (внутренняя). На схеме показаны три базы данных Lync. </span><span class="sxs-lookup"><span data-stu-id="448f1-p128">Lync Database (backend). The diagram shows three Lync databases.</span></span> 
    
- <span data-ttu-id="448f1-p129">База данных SharePoint. На схеме показаны три базы данных SharePoint. </span><span class="sxs-lookup"><span data-stu-id="448f1-p129">SharePoint Database. The diagram shows three SharePoint databases.</span></span> 
    
- <span data-ttu-id="448f1-p130">Сервер почтовых ящиков Exchange. На схеме показаны два сервера почтовых ящиков Exchange. </span><span class="sxs-lookup"><span data-stu-id="448f1-p130">Exchange Mailbox server. The diagram shows two Exchange Mailbox servers.</span></span> 
    
<span data-ttu-id="448f1-230">Дополнительные сведения о компонентах, установленных на каждой роли сервера SharePoint можно [Оптимизированные топологии для SharePoint 2013](https://aka.ms/Ma5cgk).</span><span class="sxs-lookup"><span data-stu-id="448f1-230">For more information about components installed on each of the SharePoint server roles, see [Streamlined Topologies for SharePoint 2013](https://aka.ms/Ma5cgk).</span></span> 
  
#### <a name="description-of-how-traffic-moves-through-the-components-to-the-different-server-tiers"></a><span data-ttu-id="448f1-231">Описание процесса перемещения трафика через компоненты на различные уровни серверов</span><span class="sxs-lookup"><span data-stu-id="448f1-231">Description of how traffic moves through the components to the different server tiers</span></span>

<span data-ttu-id="448f1-232">В этом разделе описано, как запросы пользователей перемещаются в пределах топологии сети.  </span><span class="sxs-lookup"><span data-stu-id="448f1-232">This section describes how user requests move through the network topology.</span></span> 
  
#### <a name="authentication-and-routing-for-external-access"></a><span data-ttu-id="448f1-233">Проверка подлинности и маршрутизация для внешнего доступа</span><span class="sxs-lookup"><span data-stu-id="448f1-233">Authentication and routing for external access</span></span>

<span data-ttu-id="448f1-234">Существуют три указанных ниже типа клиентов, располагающихся за пределами сети и облачных служб. </span><span class="sxs-lookup"><span data-stu-id="448f1-234">There are three different types of clients outside the network and cloud services, which include:</span></span> 
  
- <span data-ttu-id="448f1-235">Компании-партнеры (бизнес-бизнес) — внешние пользователи </span><span class="sxs-lookup"><span data-stu-id="448f1-235">Partner companies (business-to-business)-external</span></span> 
    
- <span data-ttu-id="448f1-236">Индивидуальные партнеры (SharePoint) и анонимные пользователи (Lync) — внешние пользователи </span><span class="sxs-lookup"><span data-stu-id="448f1-236">Individual partners (SharePoint and anonymous (Lync))-external</span></span> 
    
- <span data-ttu-id="448f1-237">Выездные и удаленные сотрудники — внешние пользователи </span><span class="sxs-lookup"><span data-stu-id="448f1-237">Roaming and remote employees-external</span></span> 
    
<span data-ttu-id="448f1-238">Процессы проверки подлинности и маршрутизации для каждого типа внешнего пользователя описаны отдельно. </span><span class="sxs-lookup"><span data-stu-id="448f1-238">The authentication and routing process for each external user type is described individually.</span></span> 
  
#### <a name="partner-companies-business-to-business-httpspartnerwebcontosocom"></a><span data-ttu-id="448f1-239">Компании-партнеры (бизнес-бизнес) (https://partnerweb.contoso.com)</span><span class="sxs-lookup"><span data-stu-id="448f1-239">Partner companies (business-to-business) (https://partnerweb.contoso.com)</span></span>

- <span data-ttu-id="448f1-p131">Lync: доверие федерации с другими организациями, Skype и возможность подключения к общедоступным службам обмена мгновенными сообщениями c AOL. Трафик федерации Lync проходит через маршрутизатор шлюза на пограничный сервер Lync, потом — на виртуальный IP-адрес Lync (подсистема балансировки нагрузки и обратный прокси-сервер), а затем — на сервер Lync. </span><span class="sxs-lookup"><span data-stu-id="448f1-p131">Lync: federation trust with other organizations, Skype and Public IM Connectivity (PIC) with AOL. The Lync federation traffic goes through the gateway router to the Lync Edge Server, to the Lync VIP (load balancer/reverse proxy server), and then to the Lync Server.</span></span> 
    
- <span data-ttu-id="448f1-p132">SharePoint: надежный партнер — поставщик удостоверений с проверкой подлинности SAML. Трафик клиента SharePoint проходит через маршрутизатор шлюза на виртуальный IP-адрес SharePoint (подсистема балансировки нагрузки и обратный прокси-сервер), а затем — на сервер SharePoint. </span><span class="sxs-lookup"><span data-stu-id="448f1-p132">SharePoint: Trusted partner identity provider with SAML authentication. The SharePoint client traffic goes through the Gateway router to the SharePoint VIP (load balancer/reverse proxy server), and then to the SharePoint Server.</span></span> 
    
- <span data-ttu-id="448f1-p133">Exchange: взаимная проверка подлинности TLS для почтового трафика, проверка подлинности SAML для федеративного общего доступа. Трафик клиента Exchange проходит через маршрутизатор шлюза на виртуальный IP-адрес Exchange (подсистема балансировки нагрузки и обратный прокси-сервер), а затем — на сервер Exchange. </span><span class="sxs-lookup"><span data-stu-id="448f1-p133">Exchange: Mutual Auth TLS for mail traffic, SAML authentication for Federated Sharing. The Exchange client traffic goes through the Gateway router to the Exchange VIP (load balancer/reverse proxy server), and then to the Exchange Server.</span></span> 
    
- <span data-ttu-id="448f1-246">Трафик SMTP проходит через маршрутизатор шлюза и виртуальный IP-адрес Exchange (подсистема балансировки нагрузки и обратный прокси-сервер) на сервер Exchange. </span><span class="sxs-lookup"><span data-stu-id="448f1-246">SMTP traffic goes through the Gateway router and through the Exchange VIP (load balancer/reverse proxy server) to the Exchange server.</span></span> 
    
#### <a name="individual-partners-sharepoint-and-anonymous-lync-httpspartnerwebcontosocom-and-httpsmeetcontosocom"></a><span data-ttu-id="448f1-247">Индивидуальные партнеры (SharePoint) и анонимные пользователи (Lync). (https://partnerweb.contoso.com и https://meet.contoso.com.)</span><span class="sxs-lookup"><span data-stu-id="448f1-247">Individual partners (SharePoint) and anonymous (Lync) (https://partnerweb.contoso.com and https://meet.contoso.com)</span></span>

- <span data-ttu-id="448f1-p134">Lync: анонимные пользователи могут только присоединяться к собраниям Lync, организованным сотрудниками. Трафик федерации Lync проходит через маршрутизатор шлюза на пограничный сервер Lync, потом — на виртуальный IP-адрес Lync (подсистема балансировки нагрузки и обратный прокси-сервер), а затем — на сервер Lync.  </span><span class="sxs-lookup"><span data-stu-id="448f1-p134">Lync: anonymous users can only join Lync meetings organized by employees. The Lync federation traffic goes through the Gateway router to the Lync Edge Server, to the Lync VIP (load balancer/reverse proxy server), and then to the Lync Server.</span></span> 
    
- <span data-ttu-id="448f1-p135">SharePoint: надежный партнер-поставщик удостоверений с проверкой подлинности SAML или проверкой подлинности на основе форм. Трафик клиента SharePoint проходит через маршрутизатор шлюза на виртуальный IP-адрес SharePoint (подсистема балансировки нагрузки и обратный прокси-сервер), а затем — на сервер SharePoint. </span><span class="sxs-lookup"><span data-stu-id="448f1-p135">SharePoint: Trusted partner identity provider with SAML authentication or forms-based authentication. The SharePoint client traffic goes through the Gateway router to the SharePoint VIP (load balancer/reverse proxy server), and then to the SharePoint Server.</span></span> 
    
- <span data-ttu-id="448f1-252">Exchange: не применяется.</span><span class="sxs-lookup"><span data-stu-id="448f1-252">Exchange: Does not apply.</span></span> 
    
- <span data-ttu-id="448f1-253">Веб-трафик Lync проходит через маршрутизатор шлюза на пограничный сервер Lync, на виртуальный IP-адрес Lync (подсистема балансировки нагрузки и обратный прокси-сервер), потом — на аппаратную подсистему балансировки нагрузки, а затем — на сервер Lync. </span><span class="sxs-lookup"><span data-stu-id="448f1-253">Lync Web traffic goes through the Gateway router to the Lync Edge Server, to the Lync VIP (load balancer/reverse proxy server), to a hardware load balancer, which is required for HTTPS traffic, and then to the Lync Server.</span></span> 
    
#### <a name="roaming-and-remote-employees"></a><span data-ttu-id="448f1-254">Выездные и удаленные сотрудники</span><span class="sxs-lookup"><span data-stu-id="448f1-254">Roaming and remote employees</span></span>

1. <span data-ttu-id="448f1-255">https://Intranet.contoso.com</span><span class="sxs-lookup"><span data-stu-id="448f1-255">https://intranet.contoso.com</span></span> 
    
2. <span data-ttu-id="448f1-256">https://teams.contoso.com</span><span class="sxs-lookup"><span data-stu-id="448f1-256">https://teams.contoso.com</span></span> 
    
3. <span data-ttu-id="448f1-257">https://My.contoso.com</span><span class="sxs-lookup"><span data-stu-id="448f1-257">https://my.contoso.com</span></span>
    
4. <span data-ttu-id="448f1-258">https://partnerweb.contoso.com</span><span class="sxs-lookup"><span data-stu-id="448f1-258">https://partnerweb.contoso.com</span></span> 
    
5. <span data-ttu-id="448f1-259">https://Mail.contoso.com \*</span><span class="sxs-lookup"><span data-stu-id="448f1-259">https://mail.contoso.com\*</span></span> 
    
6. <span data-ttu-id="448f1-260">https://Dial.contoso.com \*</span><span class="sxs-lookup"><span data-stu-id="448f1-260">https://dial.contoso.com\*</span></span>
    
7. <span data-ttu-id="448f1-261">https://Meet.contoso.com \*</span><span class="sxs-lookup"><span data-stu-id="448f1-261">https://meet.contoso.com\*</span></span>
    
* <span data-ttu-id="448f1-262">URL-адрес Exchange имеет следующие виртуальные каталоги: автообнаружения, ecp, веб-служб Exchange, Microsoft-Server-ActiveSync, автономной адресной книги, owa, PowerShell</span><span class="sxs-lookup"><span data-stu-id="448f1-262">The Exchange URL has the following virtual directories: Autodiscover, ecp, EWS, Microsoft-Server-ActiveSync, OAB, owa, PowerShell</span></span> 
  
- <span data-ttu-id="448f1-p136">Lync: проверка подлинности TLS-DSK или NTLM. Трафик клиента Lync проходит через маршрутизатор шлюза на пограничный сервер Lync, потом — на виртуальный IP-адрес Lync (подсистема балансировки нагрузки и обратный прокси-сервер), а затем — на сервер Lync. </span><span class="sxs-lookup"><span data-stu-id="448f1-p136">Lync: TLS-DSK or NTLM authentication. The Lync client traffic goes through the Gateway router to the Lync Edge Server, to the Lync VIP (load balancer/reverse proxy server), and then to the Lync Server.</span></span> 
    
- <span data-ttu-id="448f1-p137">SharePoint: доменные службы Active Directory, проверка подлинности на основе форм или проверка подлинности SAML. Трафик клиента SharePoint проходит через VPN-шлюз или сервер DirectAccess на виртуальный IP-адрес SharePoint (подсистема балансировка нагрузки и обратный прокси-сервер), а затем — на сервер SharePoint. </span><span class="sxs-lookup"><span data-stu-id="448f1-p137">SharePoint: Active Directory Domain Services (AD DS), forms-based authentication, or SAML authentication. The SharePoint client traffic goes through the VPN gateway or the DirectAccess server to the SharePoint VIP (load balancer/reverse proxy server), and then to the SharePoint server.</span></span> 
    
- <span data-ttu-id="448f1-p138">Exchange: обычная проверка подлинности через SSL (ActiveSync, автообнаружение), проверка подлинности на основе форм (Outlook Web Access). Трафик клиента Exchange проходит через маршрутизатор шлюза на виртуальный IP-адрес Exchange (подсистема балансировки нагрузки и обратный прокси-сервер), а затем — на сервер Exchange. </span><span class="sxs-lookup"><span data-stu-id="448f1-p138">Exchange: Basic authentication over SSL (ActiveSync, Autodiscover), forms-based authentication (OWA). The Exchange client traffic goes through the Gateway router to the Exchange VIP (load balancer/reverse proxy server), and then to the Exchange Server.</span></span> 
    
- <span data-ttu-id="448f1-269">Трафик клиента Lync проходит через маршрутизатор шлюза на виртуальный IP-адрес Lync (подсистема балансировки нагрузки и обратный прокси-сервер), потом — на аппаратную подсистему балансировки нагрузки (которая необходима для обработки HTTPS-трафика), а затем — на сервер Lync. </span><span class="sxs-lookup"><span data-stu-id="448f1-269">Lync client traffic goes through the Gateway router to the Lync VIP (load balancer/reverse proxy server) to a hardware load balancer, which is required for HTTPS traffic, and then to the Lync Server.</span></span> 
    
#### <a name="authentication-for-internal-access"></a><span data-ttu-id="448f1-270">Проверка подлинности для внутреннего доступа</span><span class="sxs-lookup"><span data-stu-id="448f1-270">Authentication for internal access</span></span>

#### <a name="internal-employees"></a><span data-ttu-id="448f1-271">Внутренние сотрудники</span><span class="sxs-lookup"><span data-stu-id="448f1-271">Internal employees</span></span>

> <span data-ttu-id="448f1-272">https://Intranet.contoso.com</span><span class="sxs-lookup"><span data-stu-id="448f1-272">https://intranet.contoso.com</span></span> 
    
> <span data-ttu-id="448f1-273">https://teams.contoso.com</span><span class="sxs-lookup"><span data-stu-id="448f1-273">https://teams.contoso.com</span></span> 
    
> <span data-ttu-id="448f1-274">https://My.contoso.com</span><span class="sxs-lookup"><span data-stu-id="448f1-274">https://my.contoso.com</span></span>
    
> <span data-ttu-id="448f1-275">https://partnerweb.contoso.com</span><span class="sxs-lookup"><span data-stu-id="448f1-275">https://partnerweb.contoso.com</span></span>
    
> <span data-ttu-id="448f1-276">https://Mail.contoso.com \*</span><span class="sxs-lookup"><span data-stu-id="448f1-276">https://mail.contoso.com\*</span></span> 
    
> <span data-ttu-id="448f1-277">https://Dial.contoso.com</span><span class="sxs-lookup"><span data-stu-id="448f1-277">https://dial.contoso.com</span></span> 
    
> <span data-ttu-id="448f1-278">https://Meet.contoso.com</span><span class="sxs-lookup"><span data-stu-id="448f1-278">https://meet.contoso.com</span></span>
    
> <span data-ttu-id="448f1-279">https://Admin.contoso.com</span><span class="sxs-lookup"><span data-stu-id="448f1-279">https://admin.contoso.com</span></span>
    
- <span data-ttu-id="448f1-p139">Lync: проверка подлинности Kerberos, TLS-DSK или NTLM. Трафик клиента Lync проходит на виртуальный IP-адрес Lync (подсистема балансировки нагрузки и обратный прокси-сервер), а затем — на сервер Lync. </span><span class="sxs-lookup"><span data-stu-id="448f1-p139">Lync: Kerberos, TLS-DSK, or NTLM authentication. The Lync client traffic goes to the Lync VIP (load balancer/reverse proxy server), and then to the Lync Server.</span></span> 
    
- <span data-ttu-id="448f1-p140">SharePoint: доменные службы Active Directory, проверка подлинности на основе форм или проверка подлинности SAML. Трафик клиента SharePoint проходит на виртуальный IP-адрес SharePoint (подсистема балансировки нагрузки и обратный прокси-сервер), а затем — на сервер SharePoint. </span><span class="sxs-lookup"><span data-stu-id="448f1-p140">SharePoint: Active Directory Domain Services (AD DS), forms-based authentication, or SAML authentication. The SharePoint client traffic goes to the SharePoint VIP (load balancer/reverse proxy server), and then to the SharePoint Server.</span></span> 
    
- <span data-ttu-id="448f1-p141">Exchange: доменные службы Active Directory, проверка подлинности на основе форм. Трафик клиента Exchange проходит на виртуальный IP-адрес Exchange (подсистема балансировки нагрузки и обратный прокси-сервер), а затем — на сервер Exchange. </span><span class="sxs-lookup"><span data-stu-id="448f1-p141">Exchange: AD DS, forms-based authentication. The Exchange client traffic goes to the Exchange VIP (load balancer/reverse proxy server), and then to the Exchange Server.</span></span> 
    
- <span data-ttu-id="448f1-286">Трафик клиента Lync проходит на виртуальный IP-адрес Lync (подсистема балансировки нагрузки и обратный прокси-сервер), потом — на аппаратную подсистему балансировки нагрузки (которая необходима для обработки HTTPS-трафика), а затем — на сервер Lync. </span><span class="sxs-lookup"><span data-stu-id="448f1-286">Lync client traffic goes to the Lync VIP (load balancer/reverse proxy server) to a hardware load balancer, which is required for HTTPS traffic, and then to the Lync Server.</span></span> 
    
#### <a name="cloud-based-email-traffic"></a><span data-ttu-id="448f1-287">Трафик облачной электронной почты</span><span class="sxs-lookup"><span data-stu-id="448f1-287">Cloud-based email traffic</span></span>

<span data-ttu-id="448f1-288">Компонент на основе облака для электронной почты на основе SMTP-трафика состоит из Интернет-почты узлов или Exchange Online Protection.</span><span class="sxs-lookup"><span data-stu-id="448f1-288">The cloud-based component for SMTP-based email traffic consists of either Internet Mail Hosts or Exchange Online Protection.</span></span>
  
<span data-ttu-id="448f1-p142">Эти компоненты перемещают почтовый трафик по сети с помощью SMTP. Трафик проходит через маршрутизатор шлюза на виртуальный IP-адрес Exchange (подсистема балансировки нагрузки и обратный прокси-сервер), а затем — на сервер Exchange. </span><span class="sxs-lookup"><span data-stu-id="448f1-p142">These components move email traffic over the network using SMTP. The traffic goes through the Gateway router to the Exchange VIP (load balancer/reverse proxy server), and then to the Exchange Server.</span></span> 
  
### <a name="network-traffic-legend"></a><span data-ttu-id="448f1-291">Условные обозначения для сетевого трафика</span><span class="sxs-lookup"><span data-stu-id="448f1-291">Network traffic legend</span></span>

<span data-ttu-id="448f1-292">В поле условных обозначений указаны типы трафика, представленные в графе такими цветными линиями: </span><span class="sxs-lookup"><span data-stu-id="448f1-292">The legend box graphically shows the different types of traffic depicted on the graph in different colored lines as follows:</span></span> 
  
- <span data-ttu-id="448f1-293">Зеленый строки: Lync SIP трафика</span><span class="sxs-lookup"><span data-stu-id="448f1-293">Green line: Lync SIP traffic</span></span> 
    
- <span data-ttu-id="448f1-294">Синяя: веб-трафик Lync. </span><span class="sxs-lookup"><span data-stu-id="448f1-294">Blue line: Lync Web traffic</span></span> 
    
- <span data-ttu-id="448f1-295">Сиреневая: трафик клиента SharePoint. </span><span class="sxs-lookup"><span data-stu-id="448f1-295">Purple line: SharePoint client traffic</span></span> 
    
- <span data-ttu-id="448f1-296">Оранжевая: трафик клиента Exchange. </span><span class="sxs-lookup"><span data-stu-id="448f1-296">Orange line: Exchange client traffic</span></span> 
    
- <span data-ttu-id="448f1-297">Серая: трафик почтового сервера Exchange между локальной средой Exchange и Exchange Online Protection. </span><span class="sxs-lookup"><span data-stu-id="448f1-297">Gray line: Exchange Mail Server traffic between Exchange on-premises and Exchange Online Protection.</span></span> 
    
<span data-ttu-id="448f1-298">Кроме того, в поле условных обозначений описаны различные типы трафика и используемые ими порты. </span><span class="sxs-lookup"><span data-stu-id="448f1-298">The different types of traffic and the ports that they use are also described in the legend box.</span></span> 
  
#### <a name="lync-sip-traffic-and-lync-web-traffic"></a><span data-ttu-id="448f1-299">Трафик SIP для Lync и веб-трафик Lync</span><span class="sxs-lookup"><span data-stu-id="448f1-299">Lync SIP traffic and Lync web traffic</span></span>

<span data-ttu-id="448f1-300">Для обмена данными с внешними пользователями пограничный сервер Lync использует указанные ниже порты.  </span><span class="sxs-lookup"><span data-stu-id="448f1-300">The Lync Edge Server uses the following ports for external user communication:</span></span> 
  
- <span data-ttu-id="448f1-301">Трафик служб передачи сигналов и обмена мгновенными сообщениями (SIP и SIMPLE): TCP-порт 443 (открыт для входящего трафика) </span><span class="sxs-lookup"><span data-stu-id="448f1-301">Signaling/IM traffic (SIP/SIMPLE): TCP port 443 (open for inbound traffic)</span></span> 
    
- <span data-ttu-id="448f1-302">Трафик веб-конференций (PSOM): порт TCP 443 (открыт для входящего трафика) </span><span class="sxs-lookup"><span data-stu-id="448f1-302">Web conferencing traffic (PSOM): TCP 443 (open for inbound traffic)</span></span> 
    
- <span data-ttu-id="448f1-303">Трафик аудио и видео (SRTP): порты TCP 443, UDP 3478 и TCP 50000–59999 (дополнительные). Они открыты для входящего и исходящего трафика </span><span class="sxs-lookup"><span data-stu-id="448f1-303">A/V traffic (SRTP): TCP 443, UDP 3478 and TCP 50000-59999 (optional) (open for inbound and outbound traffic)</span></span> 
    
<span data-ttu-id="448f1-304">Для обмена данными в пределах федерации пограничный сервер Lync использует указанные ниже порты.  </span><span class="sxs-lookup"><span data-stu-id="448f1-304">Lync Edge Server uses the following ports for federation communication:</span></span> 
  
- <span data-ttu-id="448f1-305">Порты TCP 5061 (SIP), 5269 (XMPP), 443 и UDP 3478 (SRTP). Они открыты для входящего и исходящего трафика </span><span class="sxs-lookup"><span data-stu-id="448f1-305">TCP ports 5061 (SIP), 5269 (XMPP), 443 and UDP 3478 (SRTP) (open for inbound and outbound traffic)</span></span> 
    
#### <a name="sharepoint-client-traffic"></a><span data-ttu-id="448f1-306">Трафик клиента SharePoint.</span><span class="sxs-lookup"><span data-stu-id="448f1-306">SharePoint client traffic</span></span>

<span data-ttu-id="448f1-p143">SharePoint может использовать TCP-порт 443 (SSL) для шифрования данных, передаваемых между клиентом и подсистемой балансировки нагрузки. Чтобы можно было получать внешний доступ из Интернета, этот порт должен быть открыт для входящего и исходящего трафика на маршрутизаторе шлюза (или во внешнем брандмауэре). </span><span class="sxs-lookup"><span data-stu-id="448f1-p143">SharePoint can use TCP port 443 (SSL) for encrypted communication between the client and the load balancer. For external access from the Internet, this port needs to be opened for inbound and outbound traffic on the gateway router (or external firewall).</span></span> 
  
#### <a name="exchange-client-traffic-and-exchange-mail-server-traffic"></a><span data-ttu-id="448f1-309">Трафик клиента Exchange и почтового сервера Exchange</span><span class="sxs-lookup"><span data-stu-id="448f1-309">Exchange client traffic and Exchange mail server traffic</span></span>

<span data-ttu-id="448f1-p144">Для communications server на сервере Exchange используется TCP-порт 25 (SMTP). Большинство клиентского трафика (OWA, ActiveSync, автообнаружение, мобильный Outlook) обрабатывается через порт 443 (HTTPS). Если у вас есть клиентов POP или IMAP, порты 110 (POP3), 995 (зашифрованные POP3), 143 (IMAP4), 993 (зашифрованные IMAP4) и 587 (SMTP) также используются для поддержки этих клиентов.</span><span class="sxs-lookup"><span data-stu-id="448f1-p144">Exchange uses TCP port 25 (SMTP) for server-to-server communications. Most client traffic (OWA, ActiveSync, Autodiscover, Outlook Anywhere) is handled over port 443 (HTTPS). If you have POP or IMAP clients, ports 110 (POP3), 995 (encrypted POP3), 143 (IMAP4), 993 (encrypted IMAP4), and 587 (SMTP) are also used to support these clients.</span></span> 
  
#### <a name="more-on-lync-network-traffic"></a><span data-ttu-id="448f1-313">Нужны дополнительные сведения о сетевом трафике Lync?</span><span class="sxs-lookup"><span data-stu-id="448f1-313">More on Lync network traffic?</span></span>

<span data-ttu-id="448f1-p145">Узнайте, как Lync Server может помочь организации обмена мгновенными сообщениями, веб-конференций, общий доступ к приложениям и голосовой связи. Для получения дополнительных сведений см [Microsoft Lync Server 2013 протокол рабочих нагрузок (en)](https://aka.ms/G5jzjo).</span><span class="sxs-lookup"><span data-stu-id="448f1-p145">Learn how Lync Server can help your organization provide instant messaging, web conferencing, application sharing, and voice communication. For more information, see [Microsoft Lync Server 2013 Protocol Workloads Poster](https://aka.ms/G5jzjo).</span></span> 
  
<span data-ttu-id="448f1-316">На плакате также имеется QR-код для доступа к этой информации. </span><span class="sxs-lookup"><span data-stu-id="448f1-316">The poster also includes a QR code to access this information.</span></span> 
  

