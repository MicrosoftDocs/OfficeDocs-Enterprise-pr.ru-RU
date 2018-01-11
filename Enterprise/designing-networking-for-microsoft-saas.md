---
title: "Разработка сети для Microsoft SaaS"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 4194020a-3847-4259-9f2d-5c556a4510f9
description: "Сводка. В этой статье рассказано, как оптимизировать сеть для доступа к службам SaaS корпорации Майкрософт, в том числе к Office 365, Microsoft Intune и Dynamics 365."
ms.openlocfilehash: 970d27e50e06f4d872de67589295c490aaa6e0e7
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/11/2018
---
# <a name="designing-networking-for-microsoft-saas"></a><span data-ttu-id="b9747-103">Разработка сети для Microsoft SaaS</span><span class="sxs-lookup"><span data-stu-id="b9747-103">Designing networking for Microsoft SaaS</span></span>

 <span data-ttu-id="b9747-104">**Сводка.** В этой статье рассказано, как оптимизировать сеть для доступа к службам SaaS корпорации Майкрософт, в том числе к Office 365, Microsoft Intune и Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="b9747-104">**Summary:** Understand how to optimize your network for access to Microsoft's SaaS services, including Office 365, Microsoft Intune, and Dynamics 365.</span></span>
  
<span data-ttu-id="b9747-105">Оптимизация сети для использования служб Microsoft SaaS требует тщательного анализа характера взаимодействия с Интернетом, клиентских устройств и типичных ИТ-операций.</span><span class="sxs-lookup"><span data-stu-id="b9747-105">Optimizing your network for Microsoft SaaS services requires careful analysis of your Internet edge, your client devices, and typical IT operations.</span></span>
  
## <a name="steps-to-prepare-your-network-for-microsoft-saas-services"></a><span data-ttu-id="b9747-106">Действия по подготовке сети для служб Microsoft SaaS</span><span class="sxs-lookup"><span data-stu-id="b9747-106">Steps to prepare your network for Microsoft SaaS services</span></span>

<span data-ttu-id="b9747-107">Чтобы оптимизировать свою сеть для служб Microsoft SaaS, выполните указанные ниже действия.</span><span class="sxs-lookup"><span data-stu-id="b9747-107">Follow these steps to optimize your network for Microsoft SaaS services:</span></span>
  
1. <span data-ttu-id="b9747-108">Выполните **действия по подготовке сети для облачных служб (Майкрософт)**, описанные в статье [Общие элементы подключения к облаку Майкрософт](common-elements-of-microsoft-cloud-connectivity.md).</span><span class="sxs-lookup"><span data-stu-id="b9747-108">Go through the **Steps to prepare your network for Microsoft cloud services** section in [Common elements of Microsoft cloud connectivity](common-elements-of-microsoft-cloud-connectivity.md).</span></span>
    
2. <span data-ttu-id="b9747-109">Оптимизируйте выход в Интернет для служб Microsoft SaaS, используя рекомендации по прокси-серверам.</span><span class="sxs-lookup"><span data-stu-id="b9747-109">Optimize your Internet egress for Microsoft SaaS services using the proxy server recommendations.</span></span>
    
3. <span data-ttu-id="b9747-110">Оптимизируйте пропускную способность подключения к Интернету, используя рекомендации касательно близости и расположений.</span><span class="sxs-lookup"><span data-stu-id="b9747-110">Optimize your Internet throughput using the proximity and location recommendations.</span></span>
    
4. <span data-ttu-id="b9747-111">Оптимизируйте производительность клиентских компьютеров и интрасети, в которой они расположены, применив рекомендации по использованию клиентов.</span><span class="sxs-lookup"><span data-stu-id="b9747-111">Optimize the performance of your client computers and the intranet on which they are located using the client usage considerations.</span></span>
    
5. <span data-ttu-id="b9747-112">При необходимости оптимизируйте производительность миграций и синхронизации данных, используя рекомендации по ИТ-операциям.</span><span class="sxs-lookup"><span data-stu-id="b9747-112">As needed, optimize the performance of data migrations and synchronization using the IT operations considerations.</span></span>
    
## <a name="internet-edge-considerations"></a><span data-ttu-id="b9747-113">Рекомендации по границе Интернета</span><span class="sxs-lookup"><span data-stu-id="b9747-113">Internet edge considerations</span></span>

<span data-ttu-id="b9747-114">Ниже перечислен ряд рекомендаций по оптимизации границы Интернета и пропускной способности для служб Microsoft SaaS.</span><span class="sxs-lookup"><span data-stu-id="b9747-114">Here are some things to consider optimize your Internet edge and throughput to Microsoft SaaS services.</span></span>
  
<span data-ttu-id="b9747-115">**Рис. 1. Варианты подключения для служб Microsoft SaaS**</span><span class="sxs-lookup"><span data-stu-id="b9747-115">**Figure 1: Connection options for Microsoft SaaS services**</span></span>

![Рис. 1. Варианты подключения для служб Microsoft SaaS](images/Network_Poster/SaaS1.png)
  
<span data-ttu-id="b9747-117">На рис. 1 показано подключение локальной сети к службам Microsoft SaaS через интернет-канал или ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="b9747-117">Figure 1 shows an on-premises network connecting to Microsoft SaaS services over an Internet pipe or ExpressRoute.</span></span>
  
<span data-ttu-id="b9747-118">Рекомендации по оптимизации прокси-сервера:</span><span class="sxs-lookup"><span data-stu-id="b9747-118">Here are some recommendations to optimize your proxy server:</span></span>
  
- <span data-ttu-id="b9747-119">настраивайте веб-клиенты с помощью WPAD, PAC или GPO;</span><span class="sxs-lookup"><span data-stu-id="b9747-119">Configure web clients using WPAD, PAC, or GPO</span></span>
    
- <span data-ttu-id="b9747-120">не используйте перехват SSL;</span><span class="sxs-lookup"><span data-stu-id="b9747-120">Don't use SSL interception</span></span>
    
- <span data-ttu-id="b9747-121">используйте PAC-файл, чтобы обойти прокси-сервер для DNS-имен службы Microsoft SaaS;</span><span class="sxs-lookup"><span data-stu-id="b9747-121">Use a PAC file to bypass the proxy for Microsoft SaaS service DNS names</span></span>
    
- <span data-ttu-id="b9747-122">разрешите трафик, чтобы стала возможной проверка с помощью CRL или OCSP.</span><span class="sxs-lookup"><span data-stu-id="b9747-122">Allow traffic for CRL/OCSP verification</span></span>
    
<span data-ttu-id="b9747-123">Узкие места прокси-сервера, которые необходимо проверить:</span><span class="sxs-lookup"><span data-stu-id="b9747-123">Here are some proxy server bottlenecks to check:</span></span>
  
- <span data-ttu-id="b9747-124">недостаточное количество постоянных подключений (Outlook);</span><span class="sxs-lookup"><span data-stu-id="b9747-124">Insufficient persistent connections (Outlook)</span></span>
    
- <span data-ttu-id="b9747-125">недостаточная мощность;</span><span class="sxs-lookup"><span data-stu-id="b9747-125">Insufficient capacity</span></span>
    
- <span data-ttu-id="b9747-126">выполнение оценки вне сети;</span><span class="sxs-lookup"><span data-stu-id="b9747-126">Doing off-network evaluation</span></span>
    
- <span data-ttu-id="b9747-127">требование проверки подлинности;</span><span class="sxs-lookup"><span data-stu-id="b9747-127">Requiring authentication</span></span>
    
- <span data-ttu-id="b9747-128">отсутствие поддержки трафика UDP (Skype для бизнеса).</span><span class="sxs-lookup"><span data-stu-id="b9747-128">No support for UDP traffic (Skype for Business)</span></span>
    
<span data-ttu-id="b9747-129">Рекомендации касательно близости и расположения:</span><span class="sxs-lookup"><span data-stu-id="b9747-129">Here are some proximity and location recommendations:</span></span>
  
- <span data-ttu-id="b9747-130">не маршрутизируйте интернет-трафик через частную глобальную сеть;</span><span class="sxs-lookup"><span data-stu-id="b9747-130">Don't route your Internet traffic over the private WAN</span></span>
    
- <span data-ttu-id="b9747-131">используйте внутрирегиональные DNS и поток интернет-трафика для пользователей из других регионов;</span><span class="sxs-lookup"><span data-stu-id="b9747-131">Use in-region DNS and Internet traffic flow for out-of-region users</span></span>
    
- <span data-ttu-id="b9747-132">используйте подключение ExpressRoute для увеличения пропускной способности при работе с Office 365 и организации одновременных подключений к службам Azure.</span><span class="sxs-lookup"><span data-stu-id="b9747-132">Use ExpressRoute for high bandwidth to Office 365 and concurrent connectivity with Azure services</span></span>
    
<span data-ttu-id="b9747-133">Исходящие порты, необходимые для трафика Office 365:</span><span class="sxs-lookup"><span data-stu-id="b9747-133">Here are the outbound ports needed for Office 365 traffic:</span></span>
  
- <span data-ttu-id="b9747-134">TCP 80 (для проверок CRL и OCSP);</span><span class="sxs-lookup"><span data-stu-id="b9747-134">TCP 80 (for CRL/OCSP checks)</span></span>
    
- <span data-ttu-id="b9747-135">TCP 443;</span><span class="sxs-lookup"><span data-stu-id="b9747-135">TCP 443</span></span>
    
- <span data-ttu-id="b9747-136">UDP 3478;</span><span class="sxs-lookup"><span data-stu-id="b9747-136">UDP 3478</span></span>
    
- <span data-ttu-id="b9747-137">TCP 5223;</span><span class="sxs-lookup"><span data-stu-id="b9747-137">TCP 5223</span></span>
    
- <span data-ttu-id="b9747-138">TCP 50000-59999;</span><span class="sxs-lookup"><span data-stu-id="b9747-138">TCP 50000-59999</span></span>
    
- <span data-ttu-id="b9747-139">UDP 50000-59999.</span><span class="sxs-lookup"><span data-stu-id="b9747-139">UDP 50000-59999</span></span>
    
## <a name="client-usage-considerations"></a><span data-ttu-id="b9747-140">Рекомендации по использованию клиентов</span><span class="sxs-lookup"><span data-stu-id="b9747-140">Client usage considerations</span></span>

<span data-ttu-id="b9747-141">Прежде всего настройте службы, которые будут использоваться вашими клиентами, например указанные ниже.</span><span class="sxs-lookup"><span data-stu-id="b9747-141">First, configure the set of services that your clients will be using, such as:</span></span>
  
- <span data-ttu-id="b9747-142">Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="b9747-142">Azure Active Directory</span></span>
    
- <span data-ttu-id="b9747-143">Office 365:</span><span class="sxs-lookup"><span data-stu-id="b9747-143">Office 365</span></span>
    
  - <span data-ttu-id="b9747-144">клиентские приложения Office;</span><span class="sxs-lookup"><span data-stu-id="b9747-144">Office client apps</span></span>
    
  - <span data-ttu-id="b9747-145">SharePoint Online;</span><span class="sxs-lookup"><span data-stu-id="b9747-145">SharePoint Online</span></span>
    
  - <span data-ttu-id="b9747-146">Exchange Online;</span><span class="sxs-lookup"><span data-stu-id="b9747-146">Exchange Online</span></span>
    
  - <span data-ttu-id="b9747-147">Skype для бизнеса.</span><span class="sxs-lookup"><span data-stu-id="b9747-147">Skype for Business</span></span>
    
- <span data-ttu-id="b9747-148">Microsoft Intune.</span><span class="sxs-lookup"><span data-stu-id="b9747-148">Microsoft Intune</span></span>
    
- <span data-ttu-id="b9747-149">Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="b9747-149">Dynamics 365</span></span>
    
<span data-ttu-id="b9747-150">Для клиентских компьютеров определите такие параметры:</span><span class="sxs-lookup"><span data-stu-id="b9747-150">For your client computers, determine the following:</span></span>
  
- <span data-ttu-id="b9747-151">максимальное количество одновременно работающих клиентов (в определенное время дня, по сезонам, во время пиков и спадов использования);</span><span class="sxs-lookup"><span data-stu-id="b9747-151">Maximum number at any one time (time of day, seasonal, peaks and troughs in usage)</span></span>
    
- <span data-ttu-id="b9747-152">общая пропускная способность, необходимая во время пиков;</span><span class="sxs-lookup"><span data-stu-id="b9747-152">Total bandwidth needed for peaks</span></span>
    
- <span data-ttu-id="b9747-153">задержка на устройстве выхода в Интернет;</span><span class="sxs-lookup"><span data-stu-id="b9747-153">Latency to the Internet egress device</span></span>
    
- <span data-ttu-id="b9747-154">взаимное расположение страны, в которой вы находитесь, и страны, в которой расположен центр обработки данных.</span><span class="sxs-lookup"><span data-stu-id="b9747-154">Country of origin vs. country of datacenter co-location</span></span>
    
<span data-ttu-id="b9747-155">Для каждого типа клиента (ПК, смартфон или планшет) проверьте актуальность таких компонентов:</span><span class="sxs-lookup"><span data-stu-id="b9747-155">For each type of client (PC, smartphone, tablet), ensure the current:</span></span>
  
- <span data-ttu-id="b9747-156">операционная система;</span><span class="sxs-lookup"><span data-stu-id="b9747-156">Operating system</span></span>
    
- <span data-ttu-id="b9747-157">веб-браузер;</span><span class="sxs-lookup"><span data-stu-id="b9747-157">Internet browser</span></span>
    
- <span data-ttu-id="b9747-158">стек TCP/IP;</span><span class="sxs-lookup"><span data-stu-id="b9747-158">TCP/IP stack</span></span>
    
- <span data-ttu-id="b9747-159">сетевое оборудование;</span><span class="sxs-lookup"><span data-stu-id="b9747-159">Network hardware</span></span>
    
- <span data-ttu-id="b9747-160">драйверы ОС для сетевого оборудования;</span><span class="sxs-lookup"><span data-stu-id="b9747-160">OS drivers for network hardware</span></span>
    
- <span data-ttu-id="b9747-161">наличие обновлений и исправлений.</span><span class="sxs-lookup"><span data-stu-id="b9747-161">Updates and patches are installed</span></span>
    
<span data-ttu-id="b9747-162">Кроме того, оптимизируйте пропускную способность подключений к интрасети (проводного, беспроводного или VPN).</span><span class="sxs-lookup"><span data-stu-id="b9747-162">Additionally, optimize intranet connection throughput (wired, wireless, or VPN).</span></span>
  
<span data-ttu-id="b9747-163">Дополнительные сведения см. в статье [Поддержка NAT в Office 365]((https://support.office.com/article/NAT-support-with-Office-365-170e96ea-d65d-4e51-acac-1de56abe39b9)).</span><span class="sxs-lookup"><span data-stu-id="b9747-163">For more information, see [NAT support with Office 365]((https://support.office.com/article/NAT-support-with-Office-365-170e96ea-d65d-4e51-acac-1de56abe39b9)).</span></span>
  
<span data-ttu-id="b9747-164">Самые актуальные рекомендации по использованию ExpressRoute в Office 365 представлены в статье [Azure ExpressRoute для Office 365]((https://support.office.com/article/Azure-ExpressRoute-for-Office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd)).</span><span class="sxs-lookup"><span data-stu-id="b9747-164">For the latest recommendations for using ExpressRoute with Office 365, see [ExpressRoute for Office 365]((https://support.office.com/article/Azure-ExpressRoute-for-Office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd)).</span></span>
  
<span data-ttu-id="b9747-165">Чтобы оптимизировать производительность интрасети, выполните указанные ниже действия.</span><span class="sxs-lookup"><span data-stu-id="b9747-165">To optimize your intranet performance, do the following:</span></span>
  
- <span data-ttu-id="b9747-166">Используйте средства для измерения времени кругового пути до ваших пограничных устройств Интернета (PsPing, Ping, Tracert, TraceTCP, Network Monitor)</span><span class="sxs-lookup"><span data-stu-id="b9747-166">Use tools to gauge round trip times (RTTs) to your Internet edge devices (PsPing, Ping, Tracert, TraceTCP, Network Monitor)</span></span>
    
- <span data-ttu-id="b9747-167">Проанализируйте исходящий путь с помощью протоколов потока</span><span class="sxs-lookup"><span data-stu-id="b9747-167">Perform egress path analysis using flow protocols</span></span>
    
- <span data-ttu-id="b9747-168">Проанализируйте промежуточные устройства (их возраст, работоспособность, и т. д.)</span><span class="sxs-lookup"><span data-stu-id="b9747-168">Perform analysis of intermediate devices (age, health, etc.)</span></span>
    
<span data-ttu-id="b9747-169">Дополнительные сведения см. в статье [Средство PsPing]((https://technet.microsoft.com/sysinternals/jj729731.aspx)).</span><span class="sxs-lookup"><span data-stu-id="b9747-169">For more information, see the [PsPing tool]((https://technet.microsoft.com/sysinternals/jj729731.aspx)).</span></span>
  
## <a name="it-operations-considerations"></a><span data-ttu-id="b9747-170">Рекомендации по ИТ-операциям</span><span class="sxs-lookup"><span data-stu-id="b9747-170">IT operations considerations</span></span>

<span data-ttu-id="b9747-171">Ниже приведен ряд рекомендаций, касающихся использования рабочих ИТ-нагрузок в службе Microsoft SaaS.</span><span class="sxs-lookup"><span data-stu-id="b9747-171">Here are some things to consider when operating an IT workload in a Microsoft SaaS service.</span></span>
  
### <a name="one-time-migrations"></a><span data-ttu-id="b9747-172">Разовые миграции</span><span class="sxs-lookup"><span data-stu-id="b9747-172">One-time migrations</span></span>

<span data-ttu-id="b9747-173">Примеры разовых миграций: массовая передача данных в облачные приложения или архивное хранилище.</span><span class="sxs-lookup"><span data-stu-id="b9747-173">Examples of one-time migrations are bulk data transfer for cloud-based applications or archival storage.</span></span>
  
<span data-ttu-id="b9747-174">Чтобы оптимизировать сеть для разовых миграций, выполните указанные ниже действия.</span><span class="sxs-lookup"><span data-stu-id="b9747-174">To optimize your network for on-time migrations:</span></span>
  
- <span data-ttu-id="b9747-175">Не выполняйте такую миграцию во время пиков использования сети и периодов применения исправлений на компьютерах.</span><span class="sxs-lookup"><span data-stu-id="b9747-175">Avoid peak network usage and computer patching times</span></span>
    
- <span data-ttu-id="b9747-176">Перед выполнением миграции разработайте базовый план, выполните пилотную миграцию, оцените работоспособность сети и устраните все проблемы.</span><span class="sxs-lookup"><span data-stu-id="b9747-176">Should be baselined and piloted, assess network health and resolve issues before attempting actual migration</span></span>
    
- <span data-ttu-id="b9747-177">Проанализируйте причины проблем, чтобы избежать их во время будущих миграций.</span><span class="sxs-lookup"><span data-stu-id="b9747-177">Perform post-mortem for future migrations</span></span>
    
### <a name="ongoing-synchronizations"></a><span data-ttu-id="b9747-178">Непрерывная синхронизация</span><span class="sxs-lookup"><span data-stu-id="b9747-178">Ongoing synchronizations</span></span>

<span data-ttu-id="b9747-179">Примеры непрерывной синхронизации: синхронизации сведений о каталогах, параметрах или файлах.</span><span class="sxs-lookup"><span data-stu-id="b9747-179">Examples of ongoing synchronizations are directory information, settings, or files.</span></span>
  
<span data-ttu-id="b9747-180">Чтобы оптимизировать сеть для непрерывной синхронизации, выполните указанные ниже действия.</span><span class="sxs-lookup"><span data-stu-id="b9747-180">To optimize your network for ongoing synchronizations:</span></span>
  
- <span data-ttu-id="b9747-181">Убедитесь, что у вас имеется система мониторинга пропускной способности сети, устраните причины ошибок, зарегистрированных этой системой.</span><span class="sxs-lookup"><span data-stu-id="b9747-181">Ensure that a network bandwidth monitoring system is in place, resolve or dismiss collected errors</span></span>
    
- <span data-ttu-id="b9747-182">Используйте результаты мониторинга полосы пропускания, чтобы определить необходимость изменений сети (горизонтального или вертикального масштабирования, добавления новых линий или устройств).</span><span class="sxs-lookup"><span data-stu-id="b9747-182">Use bandwidth monitoring results to determine need for network changes (scale-up/out, new circuits, or adding devices)</span></span>
    
<span data-ttu-id="b9747-183">Дополнительные сведения см. в следующих разделах:</span><span class="sxs-lookup"><span data-stu-id="b9747-183">For more information, see:</span></span>
  
- <span data-ttu-id="b9747-184">[Планирование миграции и использования сети для Office 365]((https://aka.ms/tune))</span><span class="sxs-lookup"><span data-stu-id="b9747-184">[Network and migration planning for Office 365]((https://aka.ms/tune))</span></span>
    
- <span data-ttu-id="b9747-185">[Курс Microsoft Virtual Academy по управлению производительностью Office 365]((https://aka.ms/o365perf))</span><span class="sxs-lookup"><span data-stu-id="b9747-185">[Office 365 Performance Management Microsoft Virtual Academy course]((https://aka.ms/o365perf))</span></span>
    
- <span data-ttu-id="b9747-186">[ExpressRoute для Office 365]((https://aka.ms/expressrouteoffice365))</span><span class="sxs-lookup"><span data-stu-id="b9747-186">[ExpressRoute for Office 365]((https://aka.ms/expressrouteoffice365))</span></span>
    
## <a name="see-also"></a><span data-ttu-id="b9747-187">См. также</span><span class="sxs-lookup"><span data-stu-id="b9747-187">See Also</span></span>

[<span data-ttu-id="b9747-188">Облачные сети Майкрософт для корпоративных архитекторов</span><span class="sxs-lookup"><span data-stu-id="b9747-188">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="b9747-189">Ресурсы для администраторов, посвященные архитектуре Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="b9747-189">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

<span data-ttu-id="b9747-190">[Стратегия Enterprise Cloud корпорации Майкрософт: ресурсы для лиц, принимающих решения в области ИТ]((https://sway.com/FJ2xsyWtkJc2taRD))</span><span class="sxs-lookup"><span data-stu-id="b9747-190">[Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers]((https://sway.com/FJ2xsyWtkJc2taRD))</span></span>



