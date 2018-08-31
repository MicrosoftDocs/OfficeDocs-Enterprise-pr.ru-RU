---
title: Поддержка NAT в Office 365
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 1/24/2017
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- BCS160
ms.assetid: 170e96ea-d65d-4e51-acac-1de56abe39b9
description: Сводка. Данная статья содержит информацию о том, как приблизительно определить правильное количество пользователей, использующих один IP-адрес, в пределах вашей организации с помощью службы преобразования сетевых адресов (NAT).
ms.openlocfilehash: 733d591bded599cfaece988a624baa7a3c0d4b06
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542288"
---
# <a name="nat-support-with-office-365"></a><span data-ttu-id="34de8-103">Поддержка NAT в Office 365</span><span class="sxs-lookup"><span data-stu-id="34de8-103">NAT support with Office 365</span></span>

 <span data-ttu-id="34de8-104">**Сводка.** Данная статья содержит информацию о том, как приблизительно определить правильное количество пользователей, использующих один IP-адрес, в пределах вашей организации с помощью службы преобразования сетевых адресов (NAT).</span><span class="sxs-lookup"><span data-stu-id="34de8-104">**Summary:** Provides details about how to approximate the correct number of clients you can use per IP address within your organization using Network Address Translation (NAT).</span></span> 
  
<span data-ttu-id="34de8-105">Ранее руководство предложенных, что максимальное число клиентов Exchange, которую следует использовать на IP-адрес для подключения к Office 365 был примерно 2 000 клиентов на порт сети.</span><span class="sxs-lookup"><span data-stu-id="34de8-105">Previously, guidance suggested that the maximum number of Exchange clients you should use per IP address to connect to Office 365 was about 2,000 clients per network port.</span></span>
  
## <a name="why-use-nat"></a><span data-ttu-id="34de8-106">Зачем использовать NAT?</span><span class="sxs-lookup"><span data-stu-id="34de8-106">Why use NAT?</span></span>

<span data-ttu-id="34de8-107">С помощью NAT, тысячи людей в корпоративной сети могут «совместно использовать» несколько публично маршрутизируемых IP-адресов.</span><span class="sxs-lookup"><span data-stu-id="34de8-107">By using NAT, thousands of people on a corporate network can "share" a few publicly routable IP addresses.</span></span>
  
<span data-ttu-id="34de8-p101">Большинство корпоративных сетей используют частное пространство IP-адресов (RFC1918). Пространство частных адресов выделяется Администрацией адресного пространства Интернета (IANA) и предназначено исключительно для сетей, которые не маршрутизируются напрямую в глобальную сеть Интернет или из нее.</span><span class="sxs-lookup"><span data-stu-id="34de8-p101">Most corporate networks use private (RFC1918) IP address space. Private address space is allocated by the Internet Assigned Numbers Authority (IANA) and intended solely for networks that do not route directly to and from the global Internet.</span></span>
  
<span data-ttu-id="34de8-p102">Чтобы обеспечить доступ к Интернету для устройств на закрытый адресное пространство IP-адресов, организации используют шлюза технологии, такие как брандмауэров и прокси-серверы, которые обеспечивают преобразование сетевых адресов (NAT) или службы (PAT) сетевых адресов порт. Эти шлюзы сделать трафик от внутренних устройств в Интернет (в том числе Office 365), по-видимому, поступающих от одного или нескольких открыто маршрутизируемыми IP-адресов. Всех исходящих подключений с внутреннего устройства преобразуется в другой источник TCP-порт на общедоступный IP-адрес.</span><span class="sxs-lookup"><span data-stu-id="34de8-p102">To provide Internet access to devices on a private IP address space, organizations use gateway technologies like firewalls and proxies that provide network address translation (NAT) or port address translation (PAT) services. These gateways make traffic from internal devices to the Internet (including Office 365) appear to be coming from one or more publicly routable IP addresses. Each outbound connection from an internal device translates to a different source TCP port on the public IP address.</span></span> 
  
## <a name="why-do-you-need-to-have-so-many-connections-open-to-office-365-at-the-same-time"></a><span data-ttu-id="34de8-113">Почему необходимо иметь слишком большом числе подключений открытый в Office 365, в то же время?</span><span class="sxs-lookup"><span data-stu-id="34de8-113">Why do you need to have so many connections open to Office 365 at the same time?</span></span>

<span data-ttu-id="34de8-p103">Outlook может открыть восемь и более подключений (в случаях, когда есть надстройки, общие календари, почтовые ящики и др.). Так как на NAT-устройстве под управлением Windows доступно максимум 64 000 портов, то до момента, когда все порты будут исчерпаны, возможно наличие максимум 8000 пользователей на IP-адрес. Помните, что если клиенты используют устройства для NAT, работающие не под управлением операционной системы Windows, общее количество доступных портов зависит от того, какое NAT-устройство или программное обеспечение используется. В этом случае максимальное количество портов может быть менее 64 000. Кроме того, доступность портов зависит и от других факторов. Например, Windows резервирует 4000 портов для собственного использования, что сокращает общее количество доступных портов до 60 000. Могут существовать и другие приложения, например Internet Explorer, которые подключаются в это же время, требуя дополнительные порты.</span><span class="sxs-lookup"><span data-stu-id="34de8-p103">Outlook may open eight or more connections (in situations where there are add-ins, shared calendars, mailboxes, etc.). Because there are a maximum of 64,000 ports available on a Windows-based NAT device, there can be a maximum of 8,000 users behind an IP address before the ports are exhausted. Note that if customers are using non-Windows OS-based devices for NAT, the total available ports are dependent on what NAT device or software is being used. In this scenario, the maximum number of ports could be less than 64,000. Availability of ports is also affected by other factors such as Windows restricting 4,000 ports for its own use, which reduces the total number of available ports to 60,000.There may be other applications, such as Internet Explorer, that could connect at the same time, requiring additional ports.</span></span>
  
## <a name="calculating-maximum-supported-devices-behind-a-single-public-ip-address-with-office-365"></a><span data-ttu-id="34de8-119">Вычисление максимального числа поддерживаемых устройств на один общий IP-адрес адрес с помощью Office 365</span><span class="sxs-lookup"><span data-stu-id="34de8-119">Calculating maximum supported devices behind a single public IP address with Office 365</span></span>

<span data-ttu-id="34de8-p104">Чтобы определить максимальное число устройств один общий IP-адрес, необходимо отслеживать сетевой трафик, чтобы определить пиковое потребление порта на клиента. Кроме того пик-фактором предназначена для использования портов (менее 4).</span><span class="sxs-lookup"><span data-stu-id="34de8-p104">To determine the maximum number of devices behind a single public IP address, you should monitor network traffic to determine peak port consumption per client. Also, a peak factor should be used for the port usage (minimum 4).</span></span> 
  
 <span data-ttu-id="34de8-122">**Используйте следующую формулу для вычисления количества поддерживаемых устройств на IP-адрес:**</span><span class="sxs-lookup"><span data-stu-id="34de8-122">**Use the following formula to calculate the number of supported devices per IP address:**</span></span>
  
<span data-ttu-id="34de8-123">Максимальное число поддерживаемых устройств на один общий IP-адрес адрес = (64,000 - 制限されたポート) / (пиковое потребление порта + пик-фактор)</span><span class="sxs-lookup"><span data-stu-id="34de8-123">Maximum supported devices behind a single public IP address = (64,000 - restricted ports)/(Peak port consumption + peak factor)</span></span>
  
 <span data-ttu-id="34de8-124">**Например, если следующее значение true:**</span><span class="sxs-lookup"><span data-stu-id="34de8-124">**For example, if the following were true:**</span></span>
  
- <span data-ttu-id="34de8-125">**Зарезервированные порты:** 4000 для операционной системы</span><span class="sxs-lookup"><span data-stu-id="34de8-125">**Restricted ports:** 4,000 for the operating system</span></span> 
    
- <span data-ttu-id="34de8-126">**Пиковое потребление порта:** 6 для каждого устройства</span><span class="sxs-lookup"><span data-stu-id="34de8-126">**Peak port consumption:** 6 per device</span></span> 
    
- <span data-ttu-id="34de8-127">**ピーク係数:** 4</span><span class="sxs-lookup"><span data-stu-id="34de8-127">**Peak factor:** 4</span></span> 
    
<span data-ttu-id="34de8-128">Затем, максимальное число поддерживаемых устройств на один общий IP-адрес адрес = (64,000-4,000) / (6 + 4) = 6 000</span><span class="sxs-lookup"><span data-stu-id="34de8-128">Then, the maximum supported devices behind a single public IP address = (64,000 - 4,000)/(6 + 4) = 6,000</span></span>
  
<span data-ttu-id="34de8-p105">В выпуске размещение пакета, включенных в обновления от сентября 2011 г. для Microsoft Office Outlook 2007 или ноября 2011 г. для Microsoft Outlook 2010 или более поздней версии, число подключений из Outlook (обоих Office Outlook 2007 с помощью службы Office 365 Пакет обновления 2 и Outlook 2010) для Exchange может быть всего лишь 2. Вам потребуется выделения в разных операционных системах поведения пользователя, и так далее, чтобы определить минимальный и максимальный количество портов, которые требуют сети в пиковые.</span><span class="sxs-lookup"><span data-stu-id="34de8-p105">With the release of Office 365 hosting pack, included in the updates from September 2011 for Microsoft Office Outlook 2007, or November 2011 for Microsoft Outlook 2010, or a later update, the number of connections from Outlook (both Office Outlook 2007 with Service Pack 2 and Outlook 2010) to Exchange can be as few as 2. You'll need to factor in the different operating systems, user behaviors, and so on to determine the minimum and maximum number of ports that your network will require at peak.</span></span>
  
<span data-ttu-id="34de8-131">Если вы хотите поддерживать несколько устройств один общий IP-адрес, выполните действия, предназначенные для получения максимальное число устройств, которые могут быть поддержаны.</span><span class="sxs-lookup"><span data-stu-id="34de8-131">If you want to support more devices behind a single public IP address, follow the steps outlined to assess the maximum number of devices that can be supported:</span></span>
  
<span data-ttu-id="34de8-p106">Мониторинг сетевой трафик, чтобы определить пиковое потребление порта на клиента. Необходимо собрать эти данные:</span><span class="sxs-lookup"><span data-stu-id="34de8-p106">Monitor network traffic to determine peak port consumption per client. You should collect this data:</span></span>
  
- <span data-ttu-id="34de8-134">Из нескольких расположений</span><span class="sxs-lookup"><span data-stu-id="34de8-134">From multiple locations</span></span>
    
- <span data-ttu-id="34de8-135">Из нескольких устройств</span><span class="sxs-lookup"><span data-stu-id="34de8-135">From multiple devices</span></span>
    
- <span data-ttu-id="34de8-136">Несколько раз</span><span class="sxs-lookup"><span data-stu-id="34de8-136">At multiple times</span></span>
    
<span data-ttu-id="34de8-137">Используйте эту формулу для подсчета максимального числа пользователей на один IP-адрес, которые могут поддерживаться в их среде.</span><span class="sxs-lookup"><span data-stu-id="34de8-137">Use the preceding formula to calculate the maximum users per IP address that can be supported in their environment.</span></span>
  
<span data-ttu-id="34de8-p107">Существуют различные методы для распределения нагрузки клиента по дополнительные общедоступный IP-адреса. Возможные стратегии зависят от возможностей решений корпоративного шлюза. Самое простое решение — сегмента вашей пространства адресов пользователя и статическое «назначение» число IP-адресов для каждого шлюза. Другой способ, предлагают много шлюзы является возможность использования пула IP-адресов. Преимущество пула адресов — это намного более динамичную и, скорее всего сделать обязательным наличие корректировка по мере роста базы пользователей.</span><span class="sxs-lookup"><span data-stu-id="34de8-p107">There are various methods for distributing client load across additional public IP addresses. Strategies available depend on the capabilities of the corporate gateway solution. The simplest solution is to segment your user address space and statically "assign" a number of IP addresses to each gateway. Another alternative that many gateway devices offer is the ability to use a pool of IP addresses. The benefit of the address pool is that it is much more dynamic and less likely to require adjustment as your user base grows.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="34de8-143">См. также</span><span class="sxs-lookup"><span data-stu-id="34de8-143">See also</span></span>

[<span data-ttu-id="34de8-144">Управление конечных точках Office 365</span><span class="sxs-lookup"><span data-stu-id="34de8-144">Managing Office 365 endpoints</span></span>](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[<span data-ttu-id="34de8-145">Конечные точки Office 365 вопросы и ответы</span><span class="sxs-lookup"><span data-stu-id="34de8-145">Office 365 endpoints FAQ</span></span>](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)

