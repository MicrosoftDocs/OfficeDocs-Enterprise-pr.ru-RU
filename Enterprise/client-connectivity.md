---
title: Возможности подключения клиента
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 7/6/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 4232abcf-4ae5-43aa-bfa1-9a078a99c78b
description: Сводка. Информация о том, каким образом клиентские компьютеры подключаются к клиентам Office 365 в зависимости от их местоположения.
ms.openlocfilehash: 9455147e70a391619e1602f2e36d9162ff2c0928
ms.sourcegitcommit: ad5bdc53ca67ee6a663c27648511c1ad768a76d4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/28/2018
ms.locfileid: "23223041"
---
# <a name="client-connectivity"></a><span data-ttu-id="47c67-103">Возможности подключения клиента</span><span class="sxs-lookup"><span data-stu-id="47c67-103">Client connectivity</span></span>

 <span data-ttu-id="47c67-104">**Сводка.** Информация о том, каким образом клиентские компьютеры подключаются к клиентам Office 365 в зависимости от их местоположения.</span><span class="sxs-lookup"><span data-stu-id="47c67-104">**Summary:** Explains how client computers connect to Office 365 tenants, depending on the location of the client computer and Office 365 tenant datacenter.</span></span>
  
<span data-ttu-id="47c67-p101">Office 365 находится в центрах обработки данных Майкрософт по всему миру которого защитить службы копирование и выполнение даже в том случае, когда в одной области, например землетрясения или электроэнергии существует серьезной проблемы. При подключении к клиенту Office 365, подключение к клиенту будут направлены в соответствующий центр обработки данных размещение вашего клиента. Правила, определяющие размещение вашего клиента определяются соглашение с корпорацией Майкрософт. Правила, которые определяют, как клиент получает данные из этого расположения центра обработки данных зависят от архитектуры службу, которую вы используете.</span><span class="sxs-lookup"><span data-stu-id="47c67-p101">Office 365 resides in Microsoft datacenters around the world which help keep the service up and running even when there's a major problem in one region, such as an earthquake or a power outage. When you connect to your Office 365 tenant, the client connection will be directed to the appropriate datacenter where your tenant is being hosted. The rules that determine where your tenant can be hosted are defined by your agreement with Microsoft. The rules that determine how your client acquires the data from that datacenter location depend on the architecture of the service you're using.</span></span>
  
<span data-ttu-id="47c67-p102">К примеру при входе в систему портала Office 365 вы обычно подключенных в ближайший центр обработки данных клиента и направлены в зависимости от службы, используйте следующий. Если запуска электронной почты соединение для отображения пользовательского интерфейса по-прежнему могут поступать из ближайшего центра обработки данных, но может быть открыт подключение между ближайшего центра обработки данных и центра обработки данных, расположение вашего клиента для отображения, возможности по электронной почте можно прочитать. Microsoft работает в одной из верхней десять в мире, приведшего к чрезвычайно fast центра обработки данных для datacenter подключений fast.</span><span class="sxs-lookup"><span data-stu-id="47c67-p102">For example, when you log on to the Office 365 portal, you're usually connected to the closest datacenter to the client and then directed depending on the service you use next. If you launch email, the initial connection to display the UI may still come from the nearest datacenter, but a second connection might be opened between the nearest datacenter and the datacenter where your tenant is located to show you what's in the emails you read. Microsoft operates one of the top ten networks in the world resulting in incredibly fast datacenter-to-datacenter connections fast.</span></span>
  
<span data-ttu-id="47c67-112">После прочтения статьи будет скорее всего понять, почему мы не предоставляют [диапазоны IP-адресов и URL-адреса Office 365 адресов](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2) каждого центра обработки данных, это просто слишком подключенными друг к другу и количество друг от друга, чтобы убедиться, что невозможно.</span><span class="sxs-lookup"><span data-stu-id="47c67-112">After you read the article, you'll likely understand why we don't provide [Office 365 URLs and IP address ranges](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2) per datacenter, they are simply too interconnected and reliant on each other to make that feasible.</span></span>
  
<span data-ttu-id="47c67-p103">Если вы используете Azure ExpressRoute для Office 365, в большинстве случаев подключения к будут поступать через частного подключения к Office 365 вместо открытое подключение, описанных здесь. Принципы о как клиенты могут подключаться по-прежнему правильность. Дополнительные сведения о [ExpressRoute Azure для Office 365](azure-expressroute.md).</span><span class="sxs-lookup"><span data-stu-id="47c67-p103">If you're using Azure ExpressRoute for Office 365, in most cases your connectivity will go over a private connection to Office 365 instead of the public connection described here. The principles about how clients connect are still accurate. Learn more about [Azure ExpressRoute for Office 365](azure-expressroute.md).</span></span>
  
<span data-ttu-id="47c67-116">Для более подробно на Скайп Business сетевых запросов ознакомьтесь со статьей [качество мультимедиа и производительность подключения к сети в Скайп для бизнеса в Интернет](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917).</span><span class="sxs-lookup"><span data-stu-id="47c67-116">For more depth on Skype for Business network requests, read the article [Media Quality and Network Connectivity Performance in Skype for Business Online](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917).</span></span>

||
|:-----|
| <span data-ttu-id="47c67-117">В этой статье является частью [сети планирование и настройка производительности для Office 365](https://aka.ms/tune).</span><span class="sxs-lookup"><span data-stu-id="47c67-117">This article is part of [Network planning and performance tuning for Office 365](https://aka.ms/tune).</span></span>|

> [!NOTE]
> <span data-ttu-id="47c67-p104">Мы принимаем меры безопасности для управления данными клиента, чтобы сделать его конфиденциальной в нашем центров обработки данных. Сведения о действиях, которые мы принимаем Управление параметрами конфиденциальности включены в [Центр управления безопасностью](https://go.microsoft.com/fwlink/?LinkID=397383).</span><span class="sxs-lookup"><span data-stu-id="47c67-p104">We take great care to manage customer data so it's secure and private in our datacenters. Details about the steps we take to manage privacy are included in the [Trust Center](https://go.microsoft.com/fwlink/?LinkID=397383).</span></span>
  
## <a name="connecting-to-the-nearest-datacenter"></a><span data-ttu-id="47c67-120">Подключение к ближайшему центру обработки данных</span><span class="sxs-lookup"><span data-stu-id="47c67-120">Connecting to the nearest datacenter</span></span>

<span data-ttu-id="47c67-p105">Это наиболее распространенный тип подключения и ее использовании с портала Office 365 и Exchange Online. В этом случае клиенты пытаются подключиться к Office 365, его компьютер DNS-запрос определяет регионе, откуда его компьютер и Office 365 перенаправляет запрос ближайшего центра обработки данных.</span><span class="sxs-lookup"><span data-stu-id="47c67-p105">This is the most common type of connection, and it's used by both the Office 365 portal and Exchange Online. In this situation, when clients attempt to connect to Office 365, their computer's DNS query determines the region of the world their computer is coming from, and Office 365 redirects the request to the nearest datacenter.</span></span>
  
<span data-ttu-id="47c67-123">Подключения к порталу остановите ближайшего центра обработки данных, и клиентский компьютер получает сведения о своем клиенте из этого расположения.</span><span class="sxs-lookup"><span data-stu-id="47c67-123">Connections to the portal stop at the nearest datacenter, and the client computer is presented with information about the client's tenant from that location.</span></span>
  
<span data-ttu-id="47c67-p106">Exchange Online идет шаг дальше. После подключения клиентского компьютера к ближайшему центру обработки данных Exchange server в центре данных подключается к центру обработки данных где клиента находится фактически показанным в *как выполняет следующее работы раздел* ниже. Сервер Exchange Online в ближайший центр обработки данных и прокси-сервера запросов с клиентского компьютера на сервере почтовых ящиков. Это ускоряет работы на клиентском компьютере путем перемещения сложных задач извлечения по электронной почте и элементы календаря в сеть Microsoft.</span><span class="sxs-lookup"><span data-stu-id="47c67-p106">Exchange Online goes a step further. Once the client computer is connected to the nearest datacenter, an Exchange server in that datacenter connects to the datacenter where the tenant is actually located as illustrated in the  *How does this work section*  below. The Exchange Online servers in the nearest datacenter then proxy the requests from the client computer to the mailbox server. This speeds up the experience for the client computer by moving the heavy lifting of retrieving emails and calendar items to the Microsoft network.</span></span>
  
## <a name="how-does-this-work-for-standard-cloud-offerings"></a><span data-ttu-id="47c67-128">Как это работает для стандартных облака?</span><span class="sxs-lookup"><span data-stu-id="47c67-128">How does this work for standard cloud offerings?</span></span>

<span data-ttu-id="47c67-p107">Этот процесс подключения стандартных для большой сетевой трафик, высокое значение веб-приложений, такие как Office 365. В этом разделе мы структуры и показаны этапы процесса. Если на клиентском компьютере не в той же области, как клиента, подключение значительно отличается в зависимости от службу, которую клиент подключается к.</span><span class="sxs-lookup"><span data-stu-id="47c67-p107">This connection process is standard for high traffic, high value web applications like Office 365. In this section, we outline and illustrate the steps in the process. When the client computer is not in the same region as the tenant, the connection looks much different depending on the service the client is connecting to.</span></span>
  
 <span data-ttu-id="47c67-p108">На этом рисунке изображена клиента, используя стандартное предложение Office 365 с помощью клиента в Северной Америке. В этом сценарии пользователь, делающего запрос поездок в Европе и с помощью Office 365 из этого расположения.</span><span class="sxs-lookup"><span data-stu-id="47c67-p108">This diagram depicts a customer using a standard Office 365 offering with a tenant in North America. In this scenario, the person making the request has traveled to Europe and is using Office 365 from that location.</span></span>
  
1. <span data-ttu-id="47c67-134">Клиентский компьютер запрашивает у локальных DNS-серверов IP-адрес, связанный с Office 365.</span><span class="sxs-lookup"><span data-stu-id="47c67-134">The client computer asks the local DNS servers for the IP address associated with Office 365.</span></span>

2. <span data-ttu-id="47c67-135">Локальные DNS-серверы клиентского компьютера запрашивают Microsoft DNS-серверов IP-адрес, связанный с Office 365.</span><span class="sxs-lookup"><span data-stu-id="47c67-135">The client computer's local DNS servers ask the Microsoft DNS servers for the IP address associated with Office 365.</span></span>

3. <span data-ttu-id="47c67-136">DNS-серверов корпорации Майкрософт возвращает имя региональных сервера (на основе местоположения клиента DNS-серверов), а на клиентском компьютере повторяет шаги 1 и 2 для получения IP-адрес региональный центр обработки данных Office 365.</span><span class="sxs-lookup"><span data-stu-id="47c67-136">Microsoft's DNS servers return the regional server name (based on the location of the client's DNS servers), and the client computer repeats steps 1 and 2 to obtain the IP address of the regional Office 365 datacenter.</span></span>

4. <span data-ttu-id="47c67-137">Клиентский компьютер подключается к IP-адресу регионального центра обработки данных.</span><span class="sxs-lookup"><span data-stu-id="47c67-137">The client computer connects to the regional datacenter IP address.</span></span>

5. <span data-ttu-id="47c67-138">Сервер Exchange Online установить подключение к активному центру обработки данных, где расположен клиент пользователя.</span><span class="sxs-lookup"><span data-stu-id="47c67-138">The Exchange Online servers establish a connection to the active datacenter where the customer's tenant resides.</span></span>

![Ближайший региональный центр обработки данных](media/4ea108e9-a299-4e3d-b0d3-469b434ff899.png)
  
## <a name="how-does-this-work-for-sovereign-cloud-offerings"></a><span data-ttu-id="47c67-140">Как это трудозатраты для sovereign облако и услуги</span><span class="sxs-lookup"><span data-stu-id="47c67-140">How does this work for sovereign cloud offerings?</span></span>

<span data-ttu-id="47c67-p109">Это подключение несколько отличаются sovereign облака, такие как Office 365, которой с 21 Vianet. С помощью клиента в sovereign экземпляр Office 365 ближайшего серверы Office 365, которые будут принимать подключения портала, серверов внутри sovereign области, в котором расположен клиента. Аналогично пользователям доступ к SharePoint Online в нашем sovereign облаке или стандартный и услуги будут направлены для серверов переднего плана, где находится клиента. В разделе подключение к активному центру обработки данных ниже.</span><span class="sxs-lookup"><span data-stu-id="47c67-p109">This connection is slightly different for sovereign cloud offerings such as Office 365 operated by 21 Vianet. With the tenant in a sovereign instance of Office 365, the nearest Office 365 servers that will accept portal connections are the servers within the sovereign region where the tenant resides. Similarly, customers accessing SharePoint Online in our sovereign cloud or standard offerings will be directed to front end servers where the tenant resides. See connecting to the active datacenter below.</span></span>
  
1. <span data-ttu-id="47c67-145">Клиентский компьютер запрашивает у локальных DNS-серверов IP-адрес, связанный с Office 365.</span><span class="sxs-lookup"><span data-stu-id="47c67-145">The client computer asks the local DNS servers for the IP address associated with Office 365.</span></span>

2. <span data-ttu-id="47c67-146">Локальные DNS-серверы клиентского компьютера запрашивают Microsoft DNS-серверов IP-адрес, связанный с Office 365.</span><span class="sxs-lookup"><span data-stu-id="47c67-146">The client computer's local DNS servers ask the Microsoft DNS servers for the IP address associated with Office 365.</span></span>

3. <span data-ttu-id="47c67-147">DNS-серверов корпорации Майкрософт возвращает имя региональных сервера (на основе местоположения клиента DNS-серверов), а на клиентском компьютере повторяет шаги 1 и 2 для получения IP-адрес региональный центр обработки данных Office 365.</span><span class="sxs-lookup"><span data-stu-id="47c67-147">Microsoft's DNS servers return the regional server name (based on the location of the client's DNS servers), and the client computer repeats steps 1 and 2 to obtain the IP address of the regional Office 365 datacenter.</span></span>

4. <span data-ttu-id="47c67-148">Клиентский компьютер подключается к IP-адресу регионального центра обработки данных.</span><span class="sxs-lookup"><span data-stu-id="47c67-148">The client computer connects to the regional datacenter IP address.</span></span>

5. <span data-ttu-id="47c67-149">Сервер Exchange Online установить подключение к активному центру обработки данных, где расположен клиент пользователя.</span><span class="sxs-lookup"><span data-stu-id="47c67-149">The Exchange Online servers establish a connection to the active datacenter where the customer's tenant resides.</span></span>

![Ближайший региональный центр обработки данных в США](media/c0628c54-0059-48c5-8a0f-41bf392ee182.png)
  
## <a name="connecting-to-the-active-datacenter"></a><span data-ttu-id="47c67-151">Подключение к активному центру обработки данных</span><span class="sxs-lookup"><span data-stu-id="47c67-151">Connecting to the active datacenter</span></span>

<span data-ttu-id="47c67-p110">Подключение к активному центру обработки данных предназначена для более тяжелых рабочих нагрузок передачи данных и в настоящее время используется SharePoint Online. В этом случае при попытке подключения к Office 365 их браузер перенаправляется в активный центр обработки данных для их SharePoint Online клиента.</span><span class="sxs-lookup"><span data-stu-id="47c67-p110">Connecting to the active datacenter is designed for heavier data transfer workloads and is currently used by SharePoint Online. In this situation, when clients attempt to connect to Office 365, their browser is redirected to the active datacenter for their SharePoint Online tenant.</span></span>
  
## <a name="how-does-this-work"></a><span data-ttu-id="47c67-154">Как это работает?</span><span class="sxs-lookup"><span data-stu-id="47c67-154">How does this work?</span></span>

<span data-ttu-id="47c67-p111">Когда клиентский компьютер подключается к SharePoint Online из другого региона, подключение перенаправляется в активный центр обработки данных SharePoint Online. В этом сценарии пользователь использует стандартное предложение, и из портала подключения оставшегося локального, а SharePoint Online будут направлены активному центру обработки данных.</span><span class="sxs-lookup"><span data-stu-id="47c67-p111">When the client computer is connecting to SharePoint Online from a different region, the connection is redirected to the active SharePoint Online datacenter. In this scenario, the customer is using a standard offering, resulting in the portal connections remaining local and the SharePoint Online connections being directed to the active datacenter.</span></span>
  
1. <span data-ttu-id="47c67-157">Клиентский компьютер запрашивает у локальных DNS-серверов IP-адрес, связанный с Office 365.</span><span class="sxs-lookup"><span data-stu-id="47c67-157">The client computer asks the local DNS servers for the IP address associated with Office 365.</span></span>

2. <span data-ttu-id="47c67-158">Локальные DNS-серверы клиентского компьютера запрашивают Microsoft DNS-серверов IP-адрес, связанный с Office 365.</span><span class="sxs-lookup"><span data-stu-id="47c67-158">The client computer's local DNS servers ask the Microsoft DNS servers for the IP address associated with Office 365.</span></span>

3. <span data-ttu-id="47c67-159">DNS-серверов корпорации Майкрософт возвращает имя сервера активных центра данных SharePoint Online (на основе местоположения клиента Office 365 клиента), а на клиентском компьютере повторяет шаги 1 и 2 для получения IP-адрес активному центру обработки данных Office 365.</span><span class="sxs-lookup"><span data-stu-id="47c67-159">Microsoft's DNS servers return the server name of the active SharePoint Online datacenter (based on the location of the client's Office 365 tenant), and the client computer repeats steps 1 and 2 to obtain the IP address of the active Office 365 datacenter.</span></span>

4. <span data-ttu-id="47c67-160">Клиентский компьютер подключается к IP-адресу активного центра обработки данных.</span><span class="sxs-lookup"><span data-stu-id="47c67-160">The client computer connects to the active datacenter IP address.</span></span>

![Активный центр обработки данных в США](media/c6d2933f-49cb-4536-bea7-c868707755ae.png)
  
## <a name="connecting-over-virtual-private-networks-vpns"></a><span data-ttu-id="47c67-162">Подключение через виртуальные частные сети (VPN)</span><span class="sxs-lookup"><span data-stu-id="47c67-162">Connecting over Virtual Private Networks (VPNs)</span></span>

<span data-ttu-id="47c67-p112">Этот тип подключения применяется только при использовании виртуальной частной сети (VPN) с клиентских компьютеров. На самом деле, просто не будет изменено поведение Office 365 так, как используется виртуальной частной сети, но VPN часто используются для управления как клиентских компьютерах устанавливать подключения к Office 365 и обычно результаты в ухудшение качества, поэтому важно на случай.</span><span class="sxs-lookup"><span data-stu-id="47c67-p112">This type of connection applies only when a virtual private network (VPN) is used by client computers. In reality, Office 365 behavior isn't changed simply because a VPN is used, but VPNs are commonly used to control how client computers establish connections to Office 365 and usually results in a degraded experience, so it's important to cover.</span></span>
  
## <a name="how-does-this-work"></a><span data-ttu-id="47c67-165">Как это работает?</span><span class="sxs-lookup"><span data-stu-id="47c67-165">How does this work?</span></span>

<span data-ttu-id="47c67-p113">Если на клиентском компьютере устанавливает VPN-подключение к организации в другой регион, DNS-серверов на этом узле office используются вместо DNS-серверов на клиентском компьютере расположение. В большинстве случаев это дополнительное подключение через VPN приведет к снижению работу в Office 365. Для подключения клиента службы как закрыть для конечного пользователя в качестве возможных оптимизированы служб Office 365. Многие службы используют Azure Пограничная сеть, содержимого сети доставки и мощность надежной сети в сети Microsoft для доставки наиболее комфортную работу при сети для служб Office 365 запросе почти достиг на клиентском компьютере по мере возможности.</span><span class="sxs-lookup"><span data-stu-id="47c67-p113">When the client computer establishes a VPN connection to a corporate office in a different region, the DNS servers at that office are used instead of the DNS servers at the client computer's location. In most cases, this extra connection over the VPN will degrade the Office 365 experience. The Office 365 services are optimized to service customer connections as close to the end user as possible. Many services leverage the Azure edge network, Content Delivery Networks, and the reliable network capacity on the Microsoft network to deliver the best possible user experience when network requests for Office 365 services are made as close to the client computer as possible.</span></span>
  
1. <span data-ttu-id="47c67-170">Клиентский компьютер запрашивает у VPN DNS серверов IP-адрес, связанный с Office 365.</span><span class="sxs-lookup"><span data-stu-id="47c67-170">The client computer asks the VPN DNS servers for the IP address associated with Office 365.</span></span>

2. <span data-ttu-id="47c67-171">Серверы VPN DNS клиентского компьютера запрашивают у Microsoft DNS-серверов IP-адрес, связанный с Office 365.</span><span class="sxs-lookup"><span data-stu-id="47c67-171">The client computer's VPN DNS servers ask the Microsoft DNS servers for the IP address associated with Office 365.</span></span>

3. <span data-ttu-id="47c67-172">DNS-серверов корпорации Майкрософт возвращает имя региональных сервера (на основе местоположения VPN DNS-серверов), а на клиентском компьютере повторяет шаги 1 и 2 для получения IP-адресе региональный центр обработки данных Office 365.</span><span class="sxs-lookup"><span data-stu-id="47c67-172">Microsoft's DNS servers return the regional server name (based on the location of the VPN DNS servers), and the client computer repeats steps 1 and 2 to obtain the IP address information of the regional Office 365 datacenter.</span></span>

4. <span data-ttu-id="47c67-173">Клиентский компьютер подключается к центру обработки данных IP-адрес, который является ближайшим к главному офису, с которым установлено подключение по сети VPN.</span><span class="sxs-lookup"><span data-stu-id="47c67-173">The client computer connects to the datacenter IP address that's closest to the corporate office they established a VPN connection with.</span></span>

![Подключение к центру обработки данных VPN](media/b5f4c06c-65a3-462d-aae8-9a4602dd8d9e.png)
  
<span data-ttu-id="47c67-175">Ниже приводится краткое связь, которую можно использовать для возврата:[https://aka.ms/o365clientconnectivity](https://aka.ms/o365clientconnectivity)</span><span class="sxs-lookup"><span data-stu-id="47c67-175">Here's a short link you can use to come back: [https://aka.ms/o365clientconnectivity](https://aka.ms/o365clientconnectivity)</span></span>
  
## <a name="see-also"></a><span data-ttu-id="47c67-176">См. также</span><span class="sxs-lookup"><span data-stu-id="47c67-176">See also</span></span>

[<span data-ttu-id="47c67-177">Управление конечных точках Office 365</span><span class="sxs-lookup"><span data-stu-id="47c67-177">Managing Office 365 endpoints</span></span>](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[<span data-ttu-id="47c67-178">Сетевое подключение к Office 365</span><span class="sxs-lookup"><span data-stu-id="47c67-178">Network connectivity to Office 365</span></span>](network-connectivity.md)
