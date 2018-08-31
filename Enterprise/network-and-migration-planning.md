---
title: Планирование сети и миграции для Office 365
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/29/2018
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- MET150
- BCS160
ms.assetid: f5ee6c33-bcd7-4b0b-b0f8-dc1d9fb8d132
description: Содержит ссылки на сведения о планировании сети и тестирования и миграции в Office 365.
ms.openlocfilehash: e2434a65b48c12f38d7371a569ba8e0bc282ae06
ms.sourcegitcommit: ad5bdc53ca67ee6a663c27648511c1ad768a76d4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/28/2018
ms.locfileid: "23223061"
---
# <a name="network-and-migration-planning-for-office-365"></a><span data-ttu-id="0f917-103">Планирование сети и миграции для Office 365</span><span class="sxs-lookup"><span data-stu-id="0f917-103">Network and migration planning for Office 365</span></span>

<span data-ttu-id="0f917-104">В этой статье содержатся ссылки на сведения о сетевых планирования и тестирования и миграции в Office 365.</span><span class="sxs-lookup"><span data-stu-id="0f917-104">This article contains links to information about network planning and testing, and migration to Office 365.</span></span>
  
<span data-ttu-id="0f917-105">Прежде чем выполнять первое развертывание или миграцию на Office 365, с помощью информации из этих статей оцените необходимую полосу пропускания, а затем проверьте, достаточно ли пропускной способности для развертывания или миграции на Office 365.</span><span class="sxs-lookup"><span data-stu-id="0f917-105">Before you deploy for the first time or migrate to Office 365, you can use the information in these topics to estimate the bandwidth you need and then to test and verify that you have enough bandwidth to deploy or migrate to Office 365.</span></span>

||
|:-----|
| <span data-ttu-id="0f917-106">В этой статье является частью [сети планирование и настройка производительности для Office 365](https://aka.ms/tune).</span><span class="sxs-lookup"><span data-stu-id="0f917-106">This article is part of [Network planning and performance tuning for Office 365](https://aka.ms/tune).</span></span>|

|||
|:-----|:-----|
|![Сети облаке Майкрософт для плакат архитекторы предприятия отображается](media/3094be9f-2407-4fa5-896d-aa66ef7b9bb9.png)|<span data-ttu-id="0f917-108">Для действия, чтобы оптимизировать сети для Office 365 и другими облачными платформами и службами изучите плакат [Microsoft Cloud сети для архитекторов Enterprise](https://aka.ms/cloudarchnetworking) .</span><span class="sxs-lookup"><span data-stu-id="0f917-108">For the steps to optimize your network for Office 365 and other Microsoft cloud platforms and services, see the [Microsoft Cloud Networking for Enterprise Architects](https://aka.ms/cloudarchnetworking) poster.</span></span> |
   
## <a name="estimate-network-bandwidth-requirements"></a><span data-ttu-id="0f917-109">Оценка требований к полосе пропускания сети</span><span class="sxs-lookup"><span data-stu-id="0f917-109">Estimate network bandwidth requirements</span></span>
<span data-ttu-id="0f917-110"><a name="EstimateBandwidthRequirements"> </a></span><span class="sxs-lookup"><span data-stu-id="0f917-110"></span></span>

<span data-ttu-id="0f917-p101">С помощью Office 365 может увеличить использование цепи Интернета вашей организации. Не важно определить пропускной способности, доступные в настоящее время достаточно, чтобы обрабатывать предполагаемый повышение после завершения развертывания Office 365 при этом по крайней мере 20% емкости для обработки максимальной загрузки в днях.</span><span class="sxs-lookup"><span data-stu-id="0f917-p101">Using Office 365 may increase the utilization of your organization's internet circuit. It's important to determine if the amount of bandwidth currently available is enough to handle the estimated increase once Office 365 is fully deployed while leaving at least 20% capacity to handle the busiest of days.</span></span>
  
<span data-ttu-id="0f917-113">Чтобы оценить пропускной способности, выполните следующие действия:</span><span class="sxs-lookup"><span data-stu-id="0f917-113">To estimate the bandwidth, use the following steps:</span></span>
  
1. <span data-ttu-id="0f917-p102">Оцените число клиентов, которые будут использовать каждый выходной Интернета. Позволяют обрабатывать большего количества по мере возможности подключения к сети несколькими терабит.</span><span class="sxs-lookup"><span data-stu-id="0f917-p102">Assess the number of clients that will use each Internet egress. Let our multi-terabit network handle as much of the connection as possible.</span></span> 
    
2. <span data-ttu-id="0f917-p103">Определите, какие службы Office 365 и функции будут доступны для использования клиентами. Скорее всего, будет групп пользователей, имеющих различных служб и профилями использования.</span><span class="sxs-lookup"><span data-stu-id="0f917-p103">Determine which Office 365 services and features will be available for clients to use. You will likely have groups of people with different services or usage profiles.</span></span>
    
3. <span data-ttu-id="0f917-p104">Измерьте использование сети для пилотной группы клиентов. Убедитесь, что в пилотном используются представителя различные профили пользователей в организации, а также другим географическим расположениям. Вы может проверяйте результаты с нашего старого калькуляторы для [Exchange ](https://go.microsoft.com/fwlink/p/?LinkId=321550)и [Скайп для бизнеса](https://go.microsoft.com/fwlink/p/?LinkId=321551) или [внедрения](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365) , мы выполнили в собственной сети.</span><span class="sxs-lookup"><span data-stu-id="0f917-p104">Measure the network use for a pilot group of clients. Ensure the pilot clients are representative of the different profiles of people in the organization as well as the different geographic locations. You can cross-check your results against our old calculators for [Exchange ](https://go.microsoft.com/fwlink/p/?LinkId=321550)and [Skype for Business](https://go.microsoft.com/fwlink/p/?LinkId=321551) or the [case study](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365) we performed on our own network.</span></span> 
    
4. <span data-ttu-id="0f917-121">Использование измерения из пилотной группы экстраполировав требованиям во всей организации и повторное тестирование, чтобы проверить оценок до внесения изменений в вашей сети.</span><span class="sxs-lookup"><span data-stu-id="0f917-121">Use the measurements from the pilot group to extrapolate the entire organization's needs and re-test to validate the estimations before making any changes to your network.</span></span>
    
## <a name="test-your-existing-network"></a><span data-ttu-id="0f917-122">Тестирование сети</span><span class="sxs-lookup"><span data-stu-id="0f917-122">Test your existing network</span></span>
<span data-ttu-id="0f917-123"><a name="calculators"> </a></span><span class="sxs-lookup"><span data-stu-id="0f917-123"></span></span>

 <span data-ttu-id="0f917-p105">**Сетевые средства.** Тестирование и проверка вашей пропускной способности сети для определения ограничения файл для загрузки, отправляемых и задержки. Эти средства помогают определить возможности сети для миграции, а также после полностью в случае развертывания.</span><span class="sxs-lookup"><span data-stu-id="0f917-p105">**Network tools.** Test and validate your Internet bandwidth to determine download, upload, and latency constraints. These tools will help you determine the capabilities of your network for migration as well as after you're fully deployed.</span></span> 
  
- <span data-ttu-id="0f917-p106">[Анализатор Microsoft сообщения](https://technet.microsoft.com/library/jj649776.aspx): анализатор соответствия сообщение — эффективный инструмент для устранения неполадок в сети. Анализатор сообщения захватывает и отображает служит для анализа на основе протокола трафика сообщений и сообщений системы. Анализатор сообщение также позволяет импортировать, сбора и анализа данных из файлов журналов и трассировки.</span><span class="sxs-lookup"><span data-stu-id="0f917-p106">[Microsoft Message Analyzer](https://technet.microsoft.com/library/jj649776.aspx): Message Analyzer is an effective tool for troubleshooting network issues. Message Analyzer captures, displays, and analyzes protocol-based messaging traffic and system messages. Message Analyzer also lets you import, aggregate, and analyze data from log and trace files.</span></span>
    
- <span data-ttu-id="0f917-130">[Анализатора удаленного подключения Майкрософт](https://go.microsoft.com/fwlink/p/?LinkId=517243): проверяется подключение в среде Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="0f917-130">[Microsoft Remote Connectivity Analyzer](https://go.microsoft.com/fwlink/p/?LinkId=517243): Tests connectivity in your Exchange Online environment.</span></span>
    
- <span data-ttu-id="0f917-131">Используйте [службы поддержки Майкрософт и помощник по восстановлению для Office 365](https://diagnostics.office.com/#/Download?env=SOC) для исправления неполадок Outlook и Office 365.</span><span class="sxs-lookup"><span data-stu-id="0f917-131">Use the [Microsoft Support and Recovery Assistant for Office 365](https://diagnostics.office.com/#/Download?env=SOC) to fix Outlook and Office 365 problems.</span></span> 
    
## <a name="best-practices-for-network-planning-and-improving-migration-performance-for-office-365"></a><span data-ttu-id="0f917-132">Best practices for network planning and improving migration performance for Office 365</span><span class="sxs-lookup"><span data-stu-id="0f917-132">Best practices for network planning and improving migration performance for Office 365</span></span>
<span data-ttu-id="0f917-133"><a name="BestPractices"> </a></span><span class="sxs-lookup"><span data-stu-id="0f917-133"></span></span>

<span data-ttu-id="0f917-134">Более глубоко в эти рекомендации по работе с Дополнительные сведения об улучшении работы в Office 365.</span><span class="sxs-lookup"><span data-stu-id="0f917-134">Dig a little deeper into these best practices for more information about improving your Office 365 experience.</span></span>
  
1. <span data-ttu-id="0f917-p107">Хотите, чтобы приступить к работе сразу как помочь пользователям? Советы по использованию Office 365, включая SharePoint Online, Exchange Online и Lync Online, когда сети просто не будет совместной работы над видеть [Советы и рекомендации по использованию Office 365 в медленных сетях](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166) . В этой статье привязывающего загрузки контента на сайте TechNet и Support.office.com для оптимальной работы Office 365 и включает сведения о возможности для настройки веб-страниц и как задать параметры Internet Explorer для обеспечения наилучшего взаимодействия Office 365.</span><span class="sxs-lookup"><span data-stu-id="0f917-p107">Want to get started helping your users right away? See [Best practices for using Office 365 on a slow network](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166) for tips on using Office 365, including SharePoint Online, Exchange Online, and Lync Online, when your network just isn't cooperating. This article links out to loads of content on TechNet and Support.office.com for optimizing your Office 365 experience and includes information on easy ways to customize your web pages and how to set your Internet Explorer settings for the best Office 365 experience.</span></span> 
    
2. <span data-ttu-id="0f917-p108">Чтение [Сетевого подключения к Office 365 принципы](https://aka.ms/o365networkingprinciples) понять принципы подключения для безопасного управления Office 365 трафика и начало обеспечить максимально высокую производительность. Эта статья поможет вам понять самые последние сведения по оптимизации проблем, безопасное подключение к сети Office 365.</span><span class="sxs-lookup"><span data-stu-id="0f917-p108">Read [Office 365 Network Connectivity Principles](https://aka.ms/o365networkingprinciples) to understand the connectivity principles for securely managing Office 365 traffic and getting the best possible performance. This article will help you understand the most recent guidance for securely optimizing Office 365 network connectivity.</span></span> 
    
3. <span data-ttu-id="0f917-p109">Повысить производительность миграции почты, тщательно управление расписание обновления Windows. Можно обновить на клиентских компьютерах в пакетах и убедитесь, что все клиентские компьютеры обновляются до миграции в Office 365 регулировать использование пропускной способности сети. Дополнительные сведения можно [вручную обновлять и настройка настольных компьютеров для Office 365 для получения последних обновлений](https://support.microsoft.com/gp/office-2013-365-update).</span><span class="sxs-lookup"><span data-stu-id="0f917-p109">Improve mail migration performance by carefully managing the schedule for Windows Updates. You can update your client computers in batches and ensure that all client computers are updated before migrating to Office 365 to regulate the use of network bandwidth. For more information, see [Manually update and configure desktops for Office 365 for the latest updates](https://support.microsoft.com/gp/office-2013-365-update).</span></span>
    
4. <span data-ttu-id="0f917-p110">Office 365 сетевого трафика выполняет лучше всего, когда оно считаться доверенной службы Интернета и разрешенных для обхода большей части традиционных фильтрации и сканирование, в некоторых организациях поместить на сетевой трафик к ненадежному Интернет-служб. Это обычно включает в себя удаление исходящей обработки, такие как проверка подлинности пользователя прокси-сервера и проверка пакетов, а также обеспечение локального исходящего трафика в Интернет с помощью соответствующих прав преобразования сетевых адресов (NAT) и достаточную емкость пропускной способности обрабатывать увеличенный сетевые запросы. Обратитесь к [конечные точки управления Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)для Дополнительные инструкции по настройке сети для обработки Office 365 в качестве доверенной службы Интернета в сети.</span><span class="sxs-lookup"><span data-stu-id="0f917-p110">Office 365 network traffic performs best when it's treated as a trusted Internet service and allowed to bypass much of the traditional filtering and scanning that some organizations place on network traffic to untrusted Internet services. This typically includes removing outbound processing such as proxy user authentication and packet inspection, as well as ensuring local egress to the Internet with the proper Network Address Translation (NAT) and enough bandwidth capacity to handle the increased network requests. Refer to [Managing Office 365 endpoints](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)for additional guidance on configuring your network to handle Office 365 as a trusted Internet service on your network.</span></span>
    
1. <span data-ttu-id="0f917-p111">Убедитесь в [конечных точках управления Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a). Дополнительный трафик, переход на Office 365 приводит к увеличение прокси-сервера исходящих подключений, а также при увеличении безопасного трафика по протоколу TLS/SSL.</span><span class="sxs-lookup"><span data-stu-id="0f917-p111">Ensure [Managing Office 365 endpoints](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a). The additional traffic going to Office 365 results in an increase of outbound proxy connections as well as an increase in secure traffic over TLS/SSL.</span></span>
    
2. <span data-ttu-id="0f917-p112">Если исходящих прокси требуется проверка подлинности пользователя могут возникнуть медленное подключение и потерю функциональности. Обход требование проверки подлинности для Office 365 доменов можно уменьшить данную дополнительную нагрузку.</span><span class="sxs-lookup"><span data-stu-id="0f917-p112">If your outbound proxies require user authentication you may experience slow connectivity or a loss of functionality. Bypassing the authentication requirement for the Office 365 domains can reduce this overhead.</span></span>
    
3. <span data-ttu-id="0f917-p113">Когда у вас много общих календарей и почтовых ящиков, может увеличиться количество подключений от Outlook к Exchange. Например, клиент Outlook может открыть до двух дополнительных подключений для каждого используемого общего календаря. В такой ситуации убедитесь, что выходной прокси-сервер способен обрабатывать эти подключения, или организуйте эти подключения к Office 365 для Outlook в обход прокси-сервера.</span><span class="sxs-lookup"><span data-stu-id="0f917-p113">If you have a large number of shared calendars and mailboxes, you may see an increase in the number of connections from Outlook to Exchange. For instance, the Outlook client may open up to two additional connections for each shared calendar in use. In this situation, ensure that the egress proxy can handle the connections, or bypass the proxy for connections to Office 365 for Outlook.</span></span>
    
4. <span data-ttu-id="0f917-p114">Определите максимальное число поддерживаемых устройств для общедоступный IP-адрес и как для балансировки нагрузки между несколькими IP-адресами. Для получения дополнительных сведений см [NAT с помощью Office 365](nat-support-with-office-365.md).</span><span class="sxs-lookup"><span data-stu-id="0f917-p114">Determine the maximum number of supported devices for a public IP address and how to load balance across multiple IP addresses. For more information, see [NAT support with Office 365](nat-support-with-office-365.md).</span></span>
    
5. <span data-ttu-id="0f917-p115">Если изучение исходящих подключений с компьютеров в сети обход фильтрации, в Office 365 домены улучшит производительность и возможность подключения. Кроме того обход исходящей проверки часто устраняет необходимость для одного исходящего трафика Интернета и позволяет локального исходящего трафика Интернета для Office 365, предназначенные сетевых запросов.</span><span class="sxs-lookup"><span data-stu-id="0f917-p115">If you're inspecting outbound connections from computers on your network, bypassing this filtering to the Office 365 domains will improve connectivity and performance. Additionally, bypassing outbound inspection often removes the need for a single Internet egress and enables local Internet egress for Office 365 destined network requests.</span></span>
    
6. <span data-ttu-id="0f917-p116">Некоторые клиенты ознакомьтесь с параметрами внутренней сети может повлиять на производительность. Параметров, таких как максимальный размер блока данных (MTU), сетевой автоматическое согласование или автоматическое определение и неоптимального маршрутов к Интернету, распространенные источники поиска.</span><span class="sxs-lookup"><span data-stu-id="0f917-p116">Some customers find internal network settings may affect performance. Settings such as maximum transmission unit (MTU) size, network auto-negotiation or auto-detection, and sub-optimal routes to the Internet are common places to look.</span></span>
    
## <a name="network-planning-reference-for-office-365"></a><span data-ttu-id="0f917-159">Ресурсы по планированию сети для Office 365</span><span class="sxs-lookup"><span data-stu-id="0f917-159">Network planning reference for Office 365</span></span>
<span data-ttu-id="0f917-160"><a name="NetReference"> </a></span><span class="sxs-lookup"><span data-stu-id="0f917-160"></span></span>

<span data-ttu-id="0f917-161">Следующие разделы содержат подробные сведения Справочник по сети Office 365.</span><span class="sxs-lookup"><span data-stu-id="0f917-161">These topics contain detailed Office 365 network reference information.</span></span>
  
- [<span data-ttu-id="0f917-162">Управление конечных точках Office 365</span><span class="sxs-lookup"><span data-stu-id="0f917-162">Managing Office 365 endpoints</span></span>](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
    
- [<span data-ttu-id="0f917-163">Подключение клиентских компьютеров</span><span class="sxs-lookup"><span data-stu-id="0f917-163">Client connectivity</span></span>](client-connectivity.md)
    
- [<span data-ttu-id="0f917-164">Сети доставки содержимого</span><span class="sxs-lookup"><span data-stu-id="0f917-164">Content delivery networks</span></span>](content-delivery-networks.md)
    
- [<span data-ttu-id="0f917-165">Внешние записи доменных имен для Office 365</span><span class="sxs-lookup"><span data-stu-id="0f917-165">External Domain Name System records for Office 365</span></span>](external-domain-name-system-records.md)
    
- [<span data-ttu-id="0f917-166">Поддержка IPv6 в службах Office 365</span><span class="sxs-lookup"><span data-stu-id="0f917-166">IPv6 support in Office 365 services</span></span>](ipv6-support.md)
    
- [<span data-ttu-id="0f917-167">Принципы сетевого подключения к Office 365</span><span class="sxs-lookup"><span data-stu-id="0f917-167">Office 365 Network Connectivity Principles</span></span>](https://aka.ms/o365networkingprinciples)
    
- [<span data-ttu-id="0f917-168">Виртуальных Academy Майкрософт: Управление производительностью Office 365</span><span class="sxs-lookup"><span data-stu-id="0f917-168">Microsoft Virtual Academy: Office 365 Performance Management</span></span>](https://mva.microsoft.com/en-us/training-courses/office-365-performance-management-8416)
    
- [<span data-ttu-id="0f917-169">Office 365 видео сети часто задаваемые вопросы и ответы</span><span class="sxs-lookup"><span data-stu-id="0f917-169">Office 365 video networking Frequently Asked Questions (FAQ)</span></span>](office-365-video-networking-faq.md)
    
- [<span data-ttu-id="0f917-170">Планирование сетевых устройств, подключающихся к службам Office 365</span><span class="sxs-lookup"><span data-stu-id="0f917-170">Plan for network devices that connect to Office 365 services</span></span>](plan-for-network-devices.md)
    
- [<span data-ttu-id="0f917-171">Помощники по развертыванию служб Office 365</span><span class="sxs-lookup"><span data-stu-id="0f917-171">Deployment advisors for Office 365 services</span></span>](deployment-advisors-for-office-365.md)
    

