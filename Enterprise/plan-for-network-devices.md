---
title: Планирование для сетевых устройств, подключающихся к службам Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/29/2016
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 073433ca-3511-4db9-b173-7a2edca57691
description: 'Сводка: в этой статье описаны рекомендации по пропускной способности сети, ускорителям глобальной сети и устройствам балансировки нагрузки, которые используются для подключения к Office 365.'
ms.openlocfilehash: c384ba043e64ec83eda74b234937efaf72f29815
ms.sourcegitcommit: ad5bdc53ca67ee6a663c27648511c1ad768a76d4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/28/2018
ms.locfileid: "23223071"
---
# <a name="plan-for-network-devices-that-connect-to-office-365-services"></a><span data-ttu-id="86b18-103">Планирование для сетевых устройств, подключающихся к службам Office 365</span><span class="sxs-lookup"><span data-stu-id="86b18-103">Plan for network devices that connect to Office 365 services</span></span>

 <span data-ttu-id="86b18-104">**Сводка**: в этой статье описаны рекомендации по пропускной способности сети, ускорителям глобальной сети и устройствам балансировки нагрузки, которые используются для подключения к Office 365.</span><span class="sxs-lookup"><span data-stu-id="86b18-104">**Summary**: Describes considerations for network capacity, WAN accelerators, and load balancing devices that are used to connect to Office 365.</span></span>
  
<span data-ttu-id="86b18-p101">Некоторые сетевого оборудования могут иметь ограничения на количество одновременных сеансов, которые поддерживаются. Для организаций, более 2 000 пользователей мы рекомендуем, что они отслеживать их сетевых устройств, чтобы убедиться, что они способны дополнительный трафик службы Office 365. Сетевого протокола SNMP (Simple Management) отслеживании программного обеспечения, которые помогут сделать это.</span><span class="sxs-lookup"><span data-stu-id="86b18-p101">Some network hardware may have limitations on the number of concurrent sessions that are supported. For organizations having more than 2,000 users, we recommend that they monitor their network devices to ensure they are capable of handling the additional Office 365 service traffic. Simple Network Management Protocol (SNMP) monitoring software can help you do this.</span></span>

||
|:-----|
| <span data-ttu-id="86b18-108">В этой статье является частью [сети планирование и настройка производительности для Office 365](https://aka.ms/tune).</span><span class="sxs-lookup"><span data-stu-id="86b18-108">This article is part of [Network planning and performance tuning for Office 365](https://aka.ms/tune).</span></span>|

<span data-ttu-id="86b18-p102">Локальный исходящий параметры прокси-сервера Интернета также влияет на возможность подключения к службам Office 365 для клиентских приложений. Необходимо также настроить сетевые устройства прокси-сервер для подключений для URL-адреса, Microsoft облачных служб и приложений. Отличается любой организации. Чтобы получить представление для как Microsoft управляют этот процесс и пропускной способности, мы временного [исследований](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365).</span><span class="sxs-lookup"><span data-stu-id="86b18-p102">On-premises outgoing Internet proxy settings also affect connectivity to Office 365 services for your client applications. You must also configure your network proxy devices to allow connections for Microsoft cloud services URLs and applications. Every organization is different. To get an idea for how Microsoft manages this process and the amount of bandwidth we provision, [read the case study](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365).</span></span>
  
<span data-ttu-id="86b18-113">Следующие Скайп для статьи справки Business получить больше информации о Скайп для параметров бизнеса:</span><span class="sxs-lookup"><span data-stu-id="86b18-113">The following Skype for Business Help articles have more information about Skype for Business settings:</span></span>
  
- [<span data-ttu-id="86b18-114">Устранение неполадок Скайп для бизнеса входа ошибки (для администраторов)</span><span class="sxs-lookup"><span data-stu-id="86b18-114">Troubleshooting Skype for Business Sign-in Errors (Administrators)</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=243624)

- [<span data-ttu-id="86b18-115">Не удается подключиться к Скайп для бизнеса или некоторые функции не работают, так как локальный брандмауэр блокирует подключение</span><span class="sxs-lookup"><span data-stu-id="86b18-115">You cannot connect to Skype for Business, or certain features do not work, because an on-premises firewall blocks the connection</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=243625)

> [!NOTE]
> <span data-ttu-id="86b18-116">Хотя многие из этих параметров Скайп для конкретного бизнеса, общие рекомендации по настройке сети можно использовать для всех служб Office 365.</span><span class="sxs-lookup"><span data-stu-id="86b18-116">While many of these settings are Skype for Business-specific, the general guidance on network configuration is useful for all Office 365 services.</span></span>
  
## <a name="determining-network-capacity"></a><span data-ttu-id="86b18-117">Определение пропускной способности сети</span><span class="sxs-lookup"><span data-stu-id="86b18-117">Determining Network Capacity</span></span>

<span data-ttu-id="86b18-p103">Каждое сетевое устройство, функционирующее при подключении к сети, имеет предельную пропускную способность. К таким устройствам относятся сетевые адаптеры сервера или клиента, маршрутизаторы, коммутаторы, а также концентраторы, которые служат для их соединения. Пропускная способность сети считается достаточной, если устройства сети не перегружаются. Отслеживание сетевой активности имеет большое значение в процессе контроля фактической нагрузки на все сетевые устройства, которая должна быть ниже максимального значения их пропускной способности. Пропускная способность сети влияет на производительность прокси-устройства.</span><span class="sxs-lookup"><span data-stu-id="86b18-p103">Every network device that exists on a connection has its capacity limit. These devices include the client and server network adapters, routers, switches, and hubs that interconnect them. Adequate network capacity means that none of them are saturated. Monitoring network activity is essential to help ensure that the actual loads on all network devices are less than their maximum capacity. Network capacity affects proxy device performance.</span></span>
  
<span data-ttu-id="86b18-p104">В большинстве случаев пропускной способности подключения к Интернету задается ограничение объема трафика. Слабый производительности трафика пиковые часы, вероятно, вызваны чрезмерное использование ссылки на Internet. Это также относится к филиале, где branch office прокси-сервера сервера компьютеры подключены к устройства прокси-сервера в штаб-квартире филиала через медленное подключение Wide сети (WAN).</span><span class="sxs-lookup"><span data-stu-id="86b18-p104">In most situations, the Internet connection bandwidth sets the limit for the amount of traffic. Weak performance during peak traffic hours is probably caused by excessive use of the Internet link. This situation also applies to a branch office scenario, where branch office proxy server computers are connected to the proxy device at the branch's headquarters over a slow Wide Area Network (WAN) link.</span></span>
  
<span data-ttu-id="86b18-p105">Для тестирования пропускная способность сети, отслеживать активность сети в интерфейсе прокси-сервера. Если это более 75% максимальная пропускная способность для любого сетевого интерфейса, следует увеличить пропускную способность сетевой инфраструктуры, который не отвечает требованиям. Также следует рассмотреть возможность использования дополнительных функций, таких как сжатия HTTP.</span><span class="sxs-lookup"><span data-stu-id="86b18-p105">To test network capacity, monitor the network activity on the proxy network interface. If it's more than 75 percent of the maximum bandwidth of any network interface, consider increasing the bandwidth of the network infrastructure that's inadequate. Or, consider using advanced features, such as HTTP compression.</span></span>
  
## <a name="wan-accelerators"></a><span data-ttu-id="86b18-129">Ускорители глобальной сети</span><span class="sxs-lookup"><span data-stu-id="86b18-129">WAN Accelerators</span></span>

<span data-ttu-id="86b18-p106">Если организация использует глобальной сети (WAN) ускорения прокси-устройства, могут возникнуть проблемы при получении доступа к службам Office 365. Может потребоваться оптимизации сетевого устройства или устройства, чтобы убедиться, что пользователи имеют согласованную работу при доступе к Office 365. Например службам Office 365 шифрования часть содержимого Office 365 и заголовке TCP. Устройства могут быть обрабатывать такого рода трафика.</span><span class="sxs-lookup"><span data-stu-id="86b18-p106">If your organization uses wide area network (WAN) acceleration proxy appliances, you may encounter issues when you access the Office 365 services. You may need to optimize your network device or devices to ensure that your users have a consistent experience when accessing Office 365. For example, Office 365 services encrypt some Office 365 content and the TCP header. Your device may not be able to handle this kind of traffic.</span></span>
  
<span data-ttu-id="86b18-134">Поддержка заявление о [с помощью глобальной сети контроллер оптимизации или трафика/проверка на наличие устройств с помощью Office 365](https://support.microsoft.com/kb/2690045).</span><span class="sxs-lookup"><span data-stu-id="86b18-134">Read our support statement about [Using WAN Optimization Controller or Traffic/Inspection devices with Office 365](https://support.microsoft.com/kb/2690045).</span></span>
  
## <a name="hardware-and-software-load-balancing-devices"></a><span data-ttu-id="86b18-135">Аппаратные и программные устройства балансировки нагрузки</span><span class="sxs-lookup"><span data-stu-id="86b18-135">Hardware and Software Load-balancing Devices</span></span>

<span data-ttu-id="86b18-p107">В организации потребуется использовать устройство балансировки нагрузки или балансировку сетевой нагрузки (HLB или NLB), чтобы распределять запросы серверам AD FS и/или гибридным серверам Exchange. Устройства балансировки нагрузки управляют сетевым трафиком для локальных серверов. Эти серверы имеют решающее значение для обеспечения доступности единого входа и гибридного развертывания Exchange.</span><span class="sxs-lookup"><span data-stu-id="86b18-p107">Your organization needs to use a hardware load balancer (HLB) or a Network Load Balancing (NLB) solution to distribute requests to your Active Directory Federation Services (AD FS) servers and/or your Exchange hybrid servers. Load-balancing devices control the network traffic to the on-premises servers. These servers are crucial in helping to ensure the availability of single sign-on and Exchange hybrid deployment.</span></span>
  
<span data-ttu-id="86b18-p108">Мы представляют собой решение балансировки сетевой Нагрузки на основе программного обеспечения, встроенной в Windows Server. Office 365 поддерживает это решение для балансировки нагрузки.</span><span class="sxs-lookup"><span data-stu-id="86b18-p108">We provide a software-based NLB solution built into Windows Server. Office 365 supports this solution to achieve load balancing.</span></span>
  
## <a name="firewalls-and-proxies"></a><span data-ttu-id="86b18-141">Брандмауэров и прокси-серверов</span><span class="sxs-lookup"><span data-stu-id="86b18-141">Firewalls and proxies</span></span>

<span data-ttu-id="86b18-142">Для получения дополнительных сведений о настройке брандмауэров и прокси-серверы для подключения к Office 365, [конечные точки управления Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a), [сетевое подключение к Office 365](network-connectivity.md)и [часто задаваемые вопросы о конечных точках Office 365](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d) для получения дополнительных сведений об устройствах и выделения канала.</span><span class="sxs-lookup"><span data-stu-id="86b18-142">For more details on configuring firewalls and proxies to connect to Office 365, read [Managing Office 365 endpoints](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a), [Network connectivity to Office 365](network-connectivity.md), and [Office 365 endpoints FAQ](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d) to learn more about devices and circuit selection.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="86b18-143">См. также</span><span class="sxs-lookup"><span data-stu-id="86b18-143">See also</span></span>

[<span data-ttu-id="86b18-144">Помощники по развертыванию служб Office 365</span><span class="sxs-lookup"><span data-stu-id="86b18-144">Deployment advisors for Office 365 services</span></span>](deployment-advisors-for-office-365.md)
