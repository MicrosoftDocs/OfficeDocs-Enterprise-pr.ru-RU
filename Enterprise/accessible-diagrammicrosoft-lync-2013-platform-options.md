---
title: "Текстовая версия схемы, в которой представлены варианты платформы Microsoft Lync 2013"
ms.author: josephd
author: JoeDavies-MSFT
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 2858d1e7-be37-4484-b121-a99779742a38
description: "Эта статья \x97 удобная текстовая версия схемы, показывающей варианты платформы Microsoft Lync 2013, которая доступна в статье Технические схемы."
ms.openlocfilehash: 79342a30a0391980cf16304f3615f6a7e64d51ff
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2017
---
# <a name="accessible-diagram---microsoft-lync-2013-platform-options"></a><span data-ttu-id="0cb70-103">Текстовая версия схемы, в которой представлены варианты платформы Microsoft Lync 2013</span><span class="sxs-lookup"><span data-stu-id="0cb70-103">Accessible diagram - Microsoft Lync 2013 Platform Options</span></span>

<span data-ttu-id="0cb70-104">**Сводка:** Эта статья является доступным текстовая версия схемы с именем варианты платформы Microsoft Lync 2013, доступный в [Технических схем](http://go.microsoft.com/fwlink/?LinkID=519139&amp;clcid=0x409).</span><span class="sxs-lookup"><span data-stu-id="0cb70-104">**Summary:** This article is an accessible text version of the diagram named Microsoft Lync 2013 Platform Options, which is available at [Technical Diagrams](http://go.microsoft.com/fwlink/?LinkID=519139&amp;clcid=0x409).</span></span>
  
<span data-ttu-id="0cb70-105">На этом плакате представлены сведения о вариантах развертывания Lync Online (Office 365) и Lync Server, которые должны знать архитекторы и лица, принимающие бизнес-решения.</span><span class="sxs-lookup"><span data-stu-id="0cb70-105">This poster describes what business decision makers (BDMs) and architects need to know about Lync Online (Office 365) and Lync Server deployments and includes:</span></span>
  
- <span data-ttu-id="0cb70-106">Сравнение четырех различных вариантов развертывания: Lync Online (Office 365), гибридная среда Lync Online и Lync Server, Lync Server и Lync Server с размещением у поставщика.</span><span class="sxs-lookup"><span data-stu-id="0cb70-106">A comparison of four different deployment options: Lync Online (Office 365), Lync Online/Server Hybrid, Lync Server, and Provider-Hosted Lync Server.</span></span> 
    
- <span data-ttu-id="0cb70-107">Два примера сценариев развертывания Lync 2013.</span><span class="sxs-lookup"><span data-stu-id="0cb70-107">Two example scenarios for deploying Lync 2013.</span></span>
    
## <a name="comparison-of-four-different-deployments-for-the-lync-2013-platform"></a><span data-ttu-id="0cb70-108">Сравнение четырех различных вариантов развертывания платформы Lync 2013</span><span class="sxs-lookup"><span data-stu-id="0cb70-108">Comparison of four different deployments for the Lync 2013 platform</span></span>

<span data-ttu-id="0cb70-109">В сравнении по каждому варианту развертывания представлена следующая информация:</span><span class="sxs-lookup"><span data-stu-id="0cb70-109">The comparison provides information about each deployment option in the following areas:</span></span> 
  
- <span data-ttu-id="0cb70-110">обзор различных компонентов развертывания;</span><span class="sxs-lookup"><span data-stu-id="0cb70-110">An overview of the different deployment features</span></span>
    
- <span data-ttu-id="0cb70-111">преимущества каждого из вариантов развертывания;</span><span class="sxs-lookup"><span data-stu-id="0cb70-111">Benefits of implementing each deployment option</span></span>
    
- <span data-ttu-id="0cb70-112">требования лицензирования;</span><span class="sxs-lookup"><span data-stu-id="0cb70-112">Licensing requirements</span></span>
    
- <span data-ttu-id="0cb70-113">необходимые архитектурные задачи;</span><span class="sxs-lookup"><span data-stu-id="0cb70-113">Required architectural tasks</span></span>
    
- <span data-ttu-id="0cb70-114">обязанности ИТ-специалистов по внедрению каждого варианта развертывания.</span><span class="sxs-lookup"><span data-stu-id="0cb70-114">IT Pro responsibilities for implementing each deployment option</span></span>
    
### <a name="overview"></a><span data-ttu-id="0cb70-115">Общие сведения</span><span class="sxs-lookup"><span data-stu-id="0cb70-115">Overview</span></span>

#### <a name="lync-online-office-365"></a><span data-ttu-id="0cb70-116">Lync Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="0cb70-116">Lync Online (Office 365)</span></span>

<span data-ttu-id="0cb70-117">Повысьте эффективность работы и сократите затраты с помощью мультитенантных планов Office 365.</span><span class="sxs-lookup"><span data-stu-id="0cb70-117">You gain efficiency and optimize for cost with Office 365 multitenant plans.</span></span>
  
<span data-ttu-id="0cb70-118">На сопроводительной схеме показана служба Lync Online с клиентом Azure Active Directory, который синхронизирует имена и пароли учетных записей между локальной средой доменных служб Active Directory и клиентом Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="0cb70-118">The accompanying diagram shows Lync Online with an Azure Active Directory tenant, which synchronizes account names and passwords between the on-premises Active Directory Domain Services (AD DS) environment and the Azure Active Directory tenant.</span></span> 
  
<span data-ttu-id="0cb70-119">Описание компонентов и функций:</span><span class="sxs-lookup"><span data-stu-id="0cb70-119">Description of features and functionality:</span></span>
  
- <span data-ttu-id="0cb70-120">Программное обеспечение как услуга (SaaS).</span><span class="sxs-lookup"><span data-stu-id="0cb70-120">Software as a Service (SaaS).</span></span>
    
- <span data-ttu-id="0cb70-121">Большой набор всегда обновленных компонентов.</span><span class="sxs-lookup"><span data-stu-id="0cb70-121">Rich feature set that is always up to date.</span></span>
    
- <span data-ttu-id="0cb70-122">В том числе и клиент Azure Active Directory для учетных записей интернет-служб, который можно использовать с другими приложениями.</span><span class="sxs-lookup"><span data-stu-id="0cb70-122">Includes an Azure Active Directory tenant for online accounts, which can be used with other applications.</span></span> 
    
- <span data-ttu-id="0cb70-123">Благодаря функции интеграции каталогов можно синхронизировать имена и пароли учетных записей между локальными доменными службами Active Directory и клиентом Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="0cb70-123">Directory integration includes synchronizing account names and passwords between the on-premises Active Directory Domain Services (AD DS) environment and the Azure Active Directory tenant.</span></span>
    
- <span data-ttu-id="0cb70-124">Если необходима функция единого входа, потребуется реализовать службы федерации Active Directory.</span><span class="sxs-lookup"><span data-stu-id="0cb70-124">If single sign-on (SSO) is a requirement, Active Directory Federation Services (AD FS) must be implemented.</span></span> 
    
- <span data-ttu-id="0cb70-125">Данные, которыми клиент обменивается через Интернет, шифруются. При их передаче используется аутентификация.</span><span class="sxs-lookup"><span data-stu-id="0cb70-125">Client communication over the Internet is encrypted and authenticated.</span></span>
    
- <span data-ttu-id="0cb70-126">Возможность подключения устаревшего телефонного оборудования (телефонной сети общего пользования, ТСОП) с помощью сторонних поставщиков.</span><span class="sxs-lookup"><span data-stu-id="0cb70-126">Legacy phone equipment, public switched telephone network (PSTN), connectivity is available through third-party providers.</span></span>
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a><span data-ttu-id="0cb70-127">Гибридная среда Lync Online и Lync Server (с разделенным доменом)</span><span class="sxs-lookup"><span data-stu-id="0cb70-127">Lync Online/Server Hybrid (split domain)</span></span>

<span data-ttu-id="0cb70-128">Вы можете использовать преимущества Office 365 и при локальном развертывании Lync 2013.</span><span class="sxs-lookup"><span data-stu-id="0cb70-128">You can combine the benefits of Office 365 with an on-premises deployment of Lync 2013.</span></span>
  
<span data-ttu-id="0cb70-p101">На сопроводительной схеме показаны Office 365 с Lync Online, при этом часть пользователей размещена в локальной среде, а другая часть  в Интернете. Кроме того, на схеме имеется пограничный сервер, развернутый в локальной среде.</span><span class="sxs-lookup"><span data-stu-id="0cb70-p101">The accompanying diagram shows Office 365 with Lync Online where some users are homed on-premises and some users are homed online. An Edge Server that is deployed on-premises is also shown.</span></span>
  
<span data-ttu-id="0cb70-131">Описание компонентов и функций:</span><span class="sxs-lookup"><span data-stu-id="0cb70-131">Description of features and functionality:</span></span>
  
- <span data-ttu-id="0cb70-132">Часть пользователей размещена в локальной среде, а другая часть  в Интернете, но все они используют один домен SIP, например contoso.com.</span><span class="sxs-lookup"><span data-stu-id="0cb70-132">Some users are homed on premises and some users are homed online, but the users share the same SIP domain (such as contoso.com).</span></span>
    
- <span data-ttu-id="0cb70-133">Использование существующей инфраструктуры Lync Server 2013, в том числе подключений к ТСОП.</span><span class="sxs-lookup"><span data-stu-id="0cb70-133">Leverage your existing Lync Server 2013 infrastructure, including the connections to the PSTN.</span></span>
    
- <span data-ttu-id="0cb70-134">Простое добавление новых пользователей Lync Online, которым не требуется доступ к ТСОП.</span><span class="sxs-lookup"><span data-stu-id="0cb70-134">Add new Lync Online users easily when they do not require PSTN.</span></span>
    
- <span data-ttu-id="0cb70-135">Миграция из локальной среды Lync в Lync Online согласно заданному вами расписанию.</span><span class="sxs-lookup"><span data-stu-id="0cb70-135">Migrate from Lync on-premises to Lync Online over time, on your schedule.</span></span>
    
- <span data-ttu-id="0cb70-136">Интеграция с другими приложениями Office 365, в том числе с Exchange Online и SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="0cb70-136">Integrate with other Office 365 applications, including Exchange Online and SharePoint Online.</span></span>
    
#### <a name="lync-server"></a><span data-ttu-id="0cb70-137">Lync Server</span><span class="sxs-lookup"><span data-stu-id="0cb70-137">Lync Server</span></span>

<span data-ttu-id="0cb70-p102">При таком варианте развертывания все ресурсы находятся под вашим контролем. На сопроводительной схеме показана инфраструктура Lync Server с локальной средой доменных служб Active Directory, в которой пользователи размещены локально.</span><span class="sxs-lookup"><span data-stu-id="0cb70-p102">In this deployment, you own everything. The accompanying diagram shows a Lync Server infrastructure with an on-premises Active Directory Domain Services (AD DS) environment where users are homed on-premises.</span></span>
  
<span data-ttu-id="0cb70-140">Описание компонентов и функций:</span><span class="sxs-lookup"><span data-stu-id="0cb70-140">Description of features and functionality:</span></span>
  
- <span data-ttu-id="0cb70-141">Планирование загрузки и определение конфигурации оборудования.</span><span class="sxs-lookup"><span data-stu-id="0cb70-141">Capacity planning and sizing.</span></span>
    
- <span data-ttu-id="0cb70-142">Приобретение и настройка серверов.</span><span class="sxs-lookup"><span data-stu-id="0cb70-142">Server acquisition and setup.</span></span>
    
- <span data-ttu-id="0cb70-143">Развертывание.</span><span class="sxs-lookup"><span data-stu-id="0cb70-143">Deployment.</span></span>
    
- <span data-ttu-id="0cb70-144">Горизонтальное масштабирование, применение исправлений и эксплуатация.</span><span class="sxs-lookup"><span data-stu-id="0cb70-144">Scaling out, patching, and operations.</span></span>
    
- <span data-ttu-id="0cb70-145">Резервное копирование данных.</span><span class="sxs-lookup"><span data-stu-id="0cb70-145">Backing up data.</span></span>
    
- <span data-ttu-id="0cb70-146">Обслуживание средств отработки отказа и аварийного восстановления.</span><span class="sxs-lookup"><span data-stu-id="0cb70-146">Maintaining failover and disaster recovery.</span></span>
    
- <span data-ttu-id="0cb70-147">Подключение инфраструктуры Lync Server 2013 к ТСОП.</span><span class="sxs-lookup"><span data-stu-id="0cb70-147">Connecting your Lync Server 2013 infrastructure to the PSTN.</span></span>
    
- <span data-ttu-id="0cb70-148">Интеграция с существующим телефонным оборудованием, например с частными УАТС.</span><span class="sxs-lookup"><span data-stu-id="0cb70-148">Integration with existing phone equipment, such as private branch exchanges (PBXs).</span></span>
    
#### <a name="provider-hosted-lync-server"></a><span data-ttu-id="0cb70-149">Lync Server с размещением у поставщика</span><span class="sxs-lookup"><span data-stu-id="0cb70-149">Provider-Hosted Lync Server</span></span>

<span data-ttu-id="0cb70-p103">При таком варианте развертывания все ресурсы находятся под контролем поставщика. На сопроводительной схеме показана сеть поставщика, включающая серверы и оборудование, подключенная к локальной среде.</span><span class="sxs-lookup"><span data-stu-id="0cb70-p103">In this deployment, your provider owns everything. The accompanying diagram shows a provider's network including their servers and equipment with a connection to an on-premises environment.</span></span>
  
<span data-ttu-id="0cb70-152">Описание компонентов и функций:</span><span class="sxs-lookup"><span data-stu-id="0cb70-152">Description of features and functionality:</span></span>
  
- <span data-ttu-id="0cb70-153">Планирование загрузки и определение конфигурации оборудования.</span><span class="sxs-lookup"><span data-stu-id="0cb70-153">Capacity planning and sizing.</span></span>
    
- <span data-ttu-id="0cb70-154">Приобретение и настройка серверов.</span><span class="sxs-lookup"><span data-stu-id="0cb70-154">Server acquisition and setup.</span></span>
    
- <span data-ttu-id="0cb70-155">Развертывание.</span><span class="sxs-lookup"><span data-stu-id="0cb70-155">Deployment.</span></span>
    
- <span data-ttu-id="0cb70-156">Горизонтальное масштабирование, применение исправлений и эксплуатация.</span><span class="sxs-lookup"><span data-stu-id="0cb70-156">Scaling out, patching, and operations.</span></span>
    
- <span data-ttu-id="0cb70-157">Резервное копирование данных.</span><span class="sxs-lookup"><span data-stu-id="0cb70-157">Backing up data.</span></span>
    
- <span data-ttu-id="0cb70-158">Обслуживание средств отработки отказа и аварийного восстановления.</span><span class="sxs-lookup"><span data-stu-id="0cb70-158">Maintaining failover and disaster recovery.</span></span>
    
- <span data-ttu-id="0cb70-159">Интеграция с существующим телефонным оборудованием, например с частными УАТС.</span><span class="sxs-lookup"><span data-stu-id="0cb70-159">Integration with existing phone equipment, such as private branch exchanges (PBXs).</span></span>
    
- <span data-ttu-id="0cb70-160">Кроме того, поставщик может:</span><span class="sxs-lookup"><span data-stu-id="0cb70-160">In addition, the provider can:</span></span>
    
  - <span data-ttu-id="0cb70-161">Установить свои серверы и оборудование в собственной сети с подключением к вашей локальной среде (сплошная линия).</span><span class="sxs-lookup"><span data-stu-id="0cb70-161">Install their servers and equipment in their own network with a connection to your premises (solid line).</span></span>
    
  - <span data-ttu-id="0cb70-162">Установить свои серверы в вашей локальной среде (пунктирная линия).</span><span class="sxs-lookup"><span data-stu-id="0cb70-162">Install their servers on your premises (dotted line).</span></span>
    
### <a name="benefits-of-implementing-each-deployment-option"></a><span data-ttu-id="0cb70-163">Преимущества каждого из вариантов развертывания</span><span class="sxs-lookup"><span data-stu-id="0cb70-163">Benefits of implementing each deployment option</span></span>

#### <a name="lync-online-office-365"></a><span data-ttu-id="0cb70-164">Lync Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="0cb70-164">Lync Online (Office 365)</span></span>

- <span data-ttu-id="0cb70-165">Отсутствие операционных затрат на локальные серверы или серверное программное обеспечение.</span><span class="sxs-lookup"><span data-stu-id="0cb70-165">No operational burden of on-premises servers or server software.</span></span>
    
- <span data-ttu-id="0cb70-166">Возможности для общения, доступные благодаря облачной службе Lync Server 2013.</span><span class="sxs-lookup"><span data-stu-id="0cb70-166">Communication capabilities of Lync Server 2013 as a cloud-based service.</span></span>
    
- <span data-ttu-id="0cb70-167">Lync предоставляет такие возможности: получение сведений о присутствии, обмен мгновенными сообщениями, использование аудио- и видеосвязи, проведение собраний по сети и веб-конференций.</span><span class="sxs-lookup"><span data-stu-id="0cb70-167">Lync presence, instant messaging, audio and video calling, rich online meetings, and extensive web conferencing capabilities.</span></span>
    
- <span data-ttu-id="0cb70-168">Данный вариант используется географически разрозненными организациями или организациями с большим количеством мобильных сотрудников.</span><span class="sxs-lookup"><span data-stu-id="0cb70-168">Used with geographically-dispersed organizations or with primarily mobile employees.</span></span>
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a><span data-ttu-id="0cb70-169">Гибридная среда Lync Online и Lync Server (с разделенным доменом)</span><span class="sxs-lookup"><span data-stu-id="0cb70-169">Lync Online/Server Hybrid (split domain)</span></span>

- <span data-ttu-id="0cb70-170">Использование Lync Online для связи с удаленными пользователями и деловыми партнерами.</span><span class="sxs-lookup"><span data-stu-id="0cb70-170">Use Lync Online for remote users and integration with business partners.</span></span>
    
- <span data-ttu-id="0cb70-171">Упрощение миграции из локальной среды Lync в Lync Online.</span><span class="sxs-lookup"><span data-stu-id="0cb70-171">Facilitate a migration from Lync on-premises to Lync Online.</span></span>
    
- <span data-ttu-id="0cb70-172">Связь с филиалами без использования соответствующих устройств.</span><span class="sxs-lookup"><span data-stu-id="0cb70-172">Support remote sites without using a branch office appliance.</span></span>
    
- <span data-ttu-id="0cb70-173">Простота внедрения Lync для новых подразделений организации.</span><span class="sxs-lookup"><span data-stu-id="0cb70-173">Ease of adding Lync support for new business acquisitions.</span></span>
    
#### <a name="lync-server"></a><span data-ttu-id="0cb70-174">Lync Server</span><span class="sxs-lookup"><span data-stu-id="0cb70-174">Lync Server</span></span>

- <span data-ttu-id="0cb70-175">Решения для частного облака.</span><span class="sxs-lookup"><span data-stu-id="0cb70-175">Private cloud solutions.</span></span>
    
- <span data-ttu-id="0cb70-176">Решения с широкими возможностями настройки.</span><span class="sxs-lookup"><span data-stu-id="0cb70-176">Highly customized solutions.</span></span>
    
- <span data-ttu-id="0cb70-177">Lync Online не поддерживает устаревшие решения со сторонними компонентами, зависящими от оборудования и программного обеспечения.</span><span class="sxs-lookup"><span data-stu-id="0cb70-177">Legacy solutions with third-party components that depend on hardware and software that are not supported by Lync Online.</span></span>
    
- <span data-ttu-id="0cb70-178">Ограничения конфиденциальности, мешающие синхронизации учетных записей доменных служб Active Directory с Office 365.</span><span class="sxs-lookup"><span data-stu-id="0cb70-178">Privacy restrictions that prevent synchronization of AD DS accounts with Office 365.</span></span>
    
- <span data-ttu-id="0cb70-179">Организации, которым необходим контроль над всей платформой и решением.</span><span class="sxs-lookup"><span data-stu-id="0cb70-179">Organizations that desire control of the entire platform and solution.</span></span>
    
- <span data-ttu-id="0cb70-180">Замена УАТС на Корпоративную голосовую связь Lync.</span><span class="sxs-lookup"><span data-stu-id="0cb70-180">PBX replacement with Lync Enterprise Voice.</span></span>
    
#### <a name="provider-hosted-lync-server"></a><span data-ttu-id="0cb70-181">Lync Server с размещением у поставщика</span><span class="sxs-lookup"><span data-stu-id="0cb70-181">Provider-Hosted Lync Server</span></span>

- <span data-ttu-id="0cb70-182">Организации, которым необходимо использовать возможности Lync Server, но так, чтобы развертыванием и обслуживанием занималась другая компания.</span><span class="sxs-lookup"><span data-stu-id="0cb70-182">Organizations that want Lync Server functionality but want to outsource its deployment and maintenance.</span></span>
    
- <span data-ttu-id="0cb70-183">Решения с привлечением поставщика.</span><span class="sxs-lookup"><span data-stu-id="0cb70-183">Provider-based solutions.</span></span>
    
- <span data-ttu-id="0cb70-184">Решения с широкими возможностями настройки.</span><span class="sxs-lookup"><span data-stu-id="0cb70-184">Highly customized solutions.</span></span>
    
- <span data-ttu-id="0cb70-185">Lync Online не поддерживает устаревшие решения со сторонними компонентами, зависящими от оборудования и программного обеспечения.</span><span class="sxs-lookup"><span data-stu-id="0cb70-185">Legacy solutions with third-party components that depend on hardware and software that are not supported by Lync Online.</span></span>
    
- <span data-ttu-id="0cb70-186">Замена УАТС на Корпоративную голосовую связь Lync.</span><span class="sxs-lookup"><span data-stu-id="0cb70-186">PBX replacement with Lync Enterprise Voice.</span></span>
    
### <a name="license-requirements"></a><span data-ttu-id="0cb70-187">Требования лицензирования</span><span class="sxs-lookup"><span data-stu-id="0cb70-187">License requirements</span></span>

#### <a name="lync-online-office-365"></a><span data-ttu-id="0cb70-188">Lync Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="0cb70-188">Lync Online (Office 365)</span></span>

<span data-ttu-id="0cb70-189">Модель с использованием подписки.</span><span class="sxs-lookup"><span data-stu-id="0cb70-189">Subscription model.</span></span>
  
#### <a name="lync-onlineserver-hybrid-split-domain"></a><span data-ttu-id="0cb70-190">Гибридная среда Lync Online и Lync Server (с разделенным доменом)</span><span class="sxs-lookup"><span data-stu-id="0cb70-190">Lync Online/Server Hybrid (split domain)</span></span>

- <span data-ttu-id="0cb70-p104">Для Office 365: модель с использованием подписки. Дополнительные лицензии не требуются.</span><span class="sxs-lookup"><span data-stu-id="0cb70-p104">Office 365 — Subscription model. No additional licenses needed.</span></span> 
    
- <span data-ttu-id="0cb70-193">Для локальной среды: можно применять все локальные лицензии.</span><span class="sxs-lookup"><span data-stu-id="0cb70-193">On-premises — All on-premises licenses apply.</span></span> 
    
#### <a name="lync-server"></a><span data-ttu-id="0cb70-194">Lync Server</span><span class="sxs-lookup"><span data-stu-id="0cb70-194">Lync Server</span></span>

- <span data-ttu-id="0cb70-195">Серверная операционная система</span><span class="sxs-lookup"><span data-stu-id="0cb70-195">Server Operating System</span></span>
    
- <span data-ttu-id="0cb70-196">SQL Server</span><span class="sxs-lookup"><span data-stu-id="0cb70-196">SQL Server</span></span>
    
- <span data-ttu-id="0cb70-197">Серверная лицензия для Lync 2013</span><span class="sxs-lookup"><span data-stu-id="0cb70-197">Lync 2013 Server License</span></span>
    
- <span data-ttu-id="0cb70-198">Клиентская лицензия для Lync 2013</span><span class="sxs-lookup"><span data-stu-id="0cb70-198">Lync 2013 Client Access License</span></span>
    
#### <a name="provider-hosted-lync-server"></a><span data-ttu-id="0cb70-199">Lync Server с размещением у поставщика</span><span class="sxs-lookup"><span data-stu-id="0cb70-199">Provider-Hosted Lync Server</span></span>

<span data-ttu-id="0cb70-200">Затраты зависят от соглашения с поставщиком решения Lync.</span><span class="sxs-lookup"><span data-stu-id="0cb70-200">Costs are based on the agreement with your Lync solution provider.</span></span>
  
### <a name="architecture-tasks"></a><span data-ttu-id="0cb70-201">Архитектурные задачи</span><span class="sxs-lookup"><span data-stu-id="0cb70-201">Architecture tasks</span></span>

<span data-ttu-id="0cb70-202">В этом разделе перечислены архитектурные задачи для каждого варианта развертывания.</span><span class="sxs-lookup"><span data-stu-id="0cb70-202">This section lists the architectural tasks for each deployment option.</span></span>
  
#### <a name="lync-online-office-365"></a><span data-ttu-id="0cb70-203">Lync Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="0cb70-203">Lync Online (Office 365)</span></span>

- <span data-ttu-id="0cb70-204">Планирование и проектирование синхронизации каталогов.</span><span class="sxs-lookup"><span data-stu-id="0cb70-204">Plan and design directory synchronization.</span></span>
    
- <span data-ttu-id="0cb70-205">Обеспечение доступности и достаточной пропускной способности сети при использовании брандмауэров, прокси-серверов, шлюзов и каналов глобальной сети.</span><span class="sxs-lookup"><span data-stu-id="0cb70-205">Ensure network capacity and availability through firewalls, proxy servers, gateways, and across WAN links.</span></span>
    
- <span data-ttu-id="0cb70-206">Приобретение сторонних SSL-сертификатов, позволяющих обеспечить защиту корпоративного уровня для служб Office 365.</span><span class="sxs-lookup"><span data-stu-id="0cb70-206">Acquire third-party SSL certificates to provide enterprise-security for Office 365 service offerings.</span></span>
    
- <span data-ttu-id="0cb70-207">Принятие решения о том, необходимо ли подключаться к Office 365 по протоколу IP версии 6 (IPv6).</span><span class="sxs-lookup"><span data-stu-id="0cb70-207">Decide if you want to connect to Office 365 with Internet Protocol version 6 (IPv6).</span></span>
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a><span data-ttu-id="0cb70-208">Гибридная среда Lync Online и Lync Server (с разделенным доменом)</span><span class="sxs-lookup"><span data-stu-id="0cb70-208">Lync Online/Server Hybrid (split domain)</span></span>

<span data-ttu-id="0cb70-209">Кроме решения задач для среды Office 365 и локальной среды, нужно:</span><span class="sxs-lookup"><span data-stu-id="0cb70-209">In addition to tasks for both the Office 365 and on-premises environments:</span></span>
  
- <span data-ttu-id="0cb70-210">Определить необходимую степень интеграции компонентов для локальных и веб-версий Exchange Server и SharePoint.</span><span class="sxs-lookup"><span data-stu-id="0cb70-210">Determine how much feature integration you want to use with on-premises and online versions of Exchange Server and SharePoint.</span></span>
    
- <span data-ttu-id="0cb70-211">При необходимости следует определить, какое устройство прокси-сервера будет использоваться для запросов из Office 365.</span><span class="sxs-lookup"><span data-stu-id="0cb70-211">If required, determine which proxy server device will be used for requests from Office 365.</span></span>
    
#### <a name="lync-server"></a><span data-ttu-id="0cb70-212">Lync Server</span><span class="sxs-lookup"><span data-stu-id="0cb70-212">Lync Server</span></span>

<span data-ttu-id="0cb70-213">Проектирование среды Lync в существующей локальной среде.</span><span class="sxs-lookup"><span data-stu-id="0cb70-213">Design the Lync environment in an existing on-premises environment:</span></span>
  
- <span data-ttu-id="0cb70-214">Топология Lync для центрального офиса и филиалов.</span><span class="sxs-lookup"><span data-stu-id="0cb70-214">Lync topology for central and branch offices.</span></span>
    
- <span data-ttu-id="0cb70-215">Серверное оборудование, в том числе для виртуализации.</span><span class="sxs-lookup"><span data-stu-id="0cb70-215">Server hardware, including virtualization.</span></span>
    
- <span data-ttu-id="0cb70-216">Интеграция с доменными службами Active Directory и DNS.</span><span class="sxs-lookup"><span data-stu-id="0cb70-216">Integration with Active Directory Domain Services (AD DS) and DNS.</span></span>
    
- <span data-ttu-id="0cb70-217">Балансировка нагрузки для пулов серверов Lync.</span><span class="sxs-lookup"><span data-stu-id="0cb70-217">Load balancing for Lync server pools.</span></span>
    
- <span data-ttu-id="0cb70-218">Отработка отказа и аварийное восстановление.</span><span class="sxs-lookup"><span data-stu-id="0cb70-218">Failover and disaster recovery.</span></span>
    
#### <a name="provider-hosted-lync-server"></a><span data-ttu-id="0cb70-219">Lync Server с размещением у поставщика</span><span class="sxs-lookup"><span data-stu-id="0cb70-219">Provider-Hosted Lync Server</span></span>

- <span data-ttu-id="0cb70-220">В случае установки в облачной среде необходимо определить способ подключения к сети поставщика услуг.</span><span class="sxs-lookup"><span data-stu-id="0cb70-220">For a cloud-based installation, determine the connection to the service provider's network.</span></span>
    
- <span data-ttu-id="0cb70-221">В случае установки в локальной среде необходимо определить способ размещения серверов Lync поставщика в вашей сети.</span><span class="sxs-lookup"><span data-stu-id="0cb70-221">For an on-premises installation, determine the placement of the provider's Lync servers on your network.</span></span>
    
- <span data-ttu-id="0cb70-222">В случае использования обоих типов установки необходимо определить способ интеграции с доменными службами Active Directory и оборудованием УАТС.</span><span class="sxs-lookup"><span data-stu-id="0cb70-222">For both types, determine the integration with AD DS and your PBX equipment.</span></span>
    
### <a name="it-pro-responsibilities"></a><span data-ttu-id="0cb70-223">Обязанности ИТ-специалистов</span><span class="sxs-lookup"><span data-stu-id="0cb70-223">IT Pro responsibilities</span></span>

<span data-ttu-id="0cb70-224">В этом разделе перечислены обязанности ИТ-специалистов по внедрению каждого варианта развертывания.</span><span class="sxs-lookup"><span data-stu-id="0cb70-224">This section lists the IT Pro responsibilities for each deployment option.</span></span>
  
#### <a name="lync-online-office-365"></a><span data-ttu-id="0cb70-225">Lync Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="0cb70-225">Lync Online (Office 365)</span></span>

<span data-ttu-id="0cb70-226">Развертывание службы Lync Online (Office 365) и управление ею.</span><span class="sxs-lookup"><span data-stu-id="0cb70-226">Deploy and manage Lync Online (Office 365):</span></span>
  
- <span data-ttu-id="0cb70-227">Внедрение плана синхронизации каталогов.</span><span class="sxs-lookup"><span data-stu-id="0cb70-227">Implement the directory synchronization plan.</span></span>
    
- <span data-ttu-id="0cb70-228">Планирование внутренних и внешних записей DNS и маршрутизации.</span><span class="sxs-lookup"><span data-stu-id="0cb70-228">Plan and implement internal and external DNS records and routing.</span></span>
    
- <span data-ttu-id="0cb70-229">Настройка прокси-сервера или брандмауэра согласно требованиям Office 365 к IP-адресу и URL-адресам.</span><span class="sxs-lookup"><span data-stu-id="0cb70-229">Configure your proxy or firewall for Office 365 IP address and URL requirements.</span></span>
    
- <span data-ttu-id="0cb70-230">Администрирование учетных записей пользователей и параметров Lync Online.</span><span class="sxs-lookup"><span data-stu-id="0cb70-230">Administer user accounts and Lync Online settings.</span></span>
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a><span data-ttu-id="0cb70-231">Гибридная среда Lync Online и Lync Server (с разделенным доменом)</span><span class="sxs-lookup"><span data-stu-id="0cb70-231">Lync Online/Server Hybrid (split domain)</span></span>

<span data-ttu-id="0cb70-232">Кроме решения задач для среды Office 365 и локальной среды, нужно:</span><span class="sxs-lookup"><span data-stu-id="0cb70-232">In addition to tasks for both the Office 365 and on-premises environments:</span></span>
  
- <span data-ttu-id="0cb70-233">Настроить устройства прокси-сервера (при необходимости).</span><span class="sxs-lookup"><span data-stu-id="0cb70-233">Configure the proxy server device, if required.</span></span>
    
- <span data-ttu-id="0cb70-234">Настроить интеграцию компонентов с локальными и веб-версиями Exchange Server и SharePoint.</span><span class="sxs-lookup"><span data-stu-id="0cb70-234">Configure the integration of features with on-premises and online versions of Exchange Server and SharePoint.</span></span>
    
#### <a name="lync-server"></a><span data-ttu-id="0cb70-235">Lync Server</span><span class="sxs-lookup"><span data-stu-id="0cb70-235">Lync Server</span></span>

<span data-ttu-id="0cb70-236">Развертывание Lync Server в локальной среде и управление им.</span><span class="sxs-lookup"><span data-stu-id="0cb70-236">Deploy and manage Lync Server in an on-premises environment:</span></span>
  
- <span data-ttu-id="0cb70-237">Подготовка серверов к работе.</span><span class="sxs-lookup"><span data-stu-id="0cb70-237">Provision the servers.</span></span>
    
- <span data-ttu-id="0cb70-238">Развертывание топологии Lync.</span><span class="sxs-lookup"><span data-stu-id="0cb70-238">Deploy the Lync topology.</span></span>
    
- <span data-ttu-id="0cb70-239">Обновление серверов Lync.</span><span class="sxs-lookup"><span data-stu-id="0cb70-239">Update Lync servers.</span></span>
    
- <span data-ttu-id="0cb70-240">Добавление серверов топологии в ферму или их удаление в зависимости от загруженности ресурсов.</span><span class="sxs-lookup"><span data-stu-id="0cb70-240">Add or remove topology servers as needed based on utilization.</span></span>
    
- <span data-ttu-id="0cb70-241">Реализация среды для отработки отказа и аварийного восстановления.</span><span class="sxs-lookup"><span data-stu-id="0cb70-241">Implement the failover and disaster recovery environment.</span></span>
    
#### <a name="provider-hosted-lync-server"></a><span data-ttu-id="0cb70-242">Lync Server с размещением у поставщика</span><span class="sxs-lookup"><span data-stu-id="0cb70-242">Provider-Hosted Lync Server</span></span>

<span data-ttu-id="0cb70-243">Задачи, которые нужно выполнить вместе с поставщиком:</span><span class="sxs-lookup"><span data-stu-id="0cb70-243">Work with the provider to:</span></span>
  
- <span data-ttu-id="0cb70-244">Интеграция Lync Server в вашу сеть.</span><span class="sxs-lookup"><span data-stu-id="0cb70-244">Integrate Lync Server into your network.</span></span>
    
- <span data-ttu-id="0cb70-245">Интеграция Lync Server с другими продуктами Майкрософт или с собственными решениями.</span><span class="sxs-lookup"><span data-stu-id="0cb70-245">Integrate Lync Server with other Microsoft products or custom solutions.</span></span>
    
- <span data-ttu-id="0cb70-246">Отслеживание выполнения соглашений об уровне обслуживания поставщиком.</span><span class="sxs-lookup"><span data-stu-id="0cb70-246">Monitor adherence with provider service level agreement (SLA).</span></span>
    
## <a name="two-example-scenarios-for-deploying-lync-2013"></a><span data-ttu-id="0cb70-247">Два примера сценариев развертывания Lync 2013.</span><span class="sxs-lookup"><span data-stu-id="0cb70-247">Two example scenarios for deploying Lync 2013</span></span>

### <a name="directory-synchronization-components-in-microsoft-azure"></a><span data-ttu-id="0cb70-248">Компоненты средства синхронизации каталогов в Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="0cb70-248">Directory Synchronization components in Microsoft Azure</span></span>

<span data-ttu-id="0cb70-249">Развертывание компонентов для синхронизации каталогов Office 365 в Azure происходит быстрее, так как виртуальные машины можно развертывать по запросу.</span><span class="sxs-lookup"><span data-stu-id="0cb70-249">Deploying Office 365 directory synchronization components in Azure is faster due to the ability to deploy virtual machines on-demand.</span></span>
  
<span data-ttu-id="0cb70-250">На сопроводительной схеме показана служба Lync Online с клиентом Azure Active Directory, которая синхронизирует имена и пароли учетных записей между локальной средой Active Directory и клиентом Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="0cb70-250">The accompanying diagram shows Lync Online with an Azure Active Directory tenant, which synchronizes account names and passwords between the on-premises Active Directory environment and the Azure Active Directory tenant.</span></span>
  
 <span data-ttu-id="0cb70-p105">**Только сервер синхронизации каталогов**. Чтобы не развертывать в локальной среде 64-разрядную версию сервера синхронизации каталогов, можно через Интернет подготовить к работе виртуальную машину в Azure.</span><span class="sxs-lookup"><span data-stu-id="0cb70-p105">**Directory synchronization server only**. Instead of deploying the 64-bit directory synchronization server in your on-premises environment, you provision a virtual machine in Azure over the Internet.</span></span>
  
 <span data-ttu-id="0cb70-p106">**Средство синхронизации каталогов и службы федерации Active Directory**. Этот вариант позволяет поддерживать федеративные удостоверения Office 365, не добавляя оборудование в локальную инфраструктуру. Кроме того, при использовании этого варианта обеспечивается устойчивость системы в случае недоступности локальной среды Active Directory. Ниже перечислены возможности, доступные при использовании этого варианта.</span><span class="sxs-lookup"><span data-stu-id="0cb70-p106">**Directory synchronization + AD FS**. This option allows you to support Office 365 federated identities (SSO) without adding hardware to your on-premises infrastructure. It also provides resiliency if the on-premises Active Directory environment is unavailable. The features of this option include:</span></span>
  
- <span data-ttu-id="0cb70-257">Компоненты интеграции каталогов работают как виртуальные машины Azure.</span><span class="sxs-lookup"><span data-stu-id="0cb70-257">Directory integration components run as Azure virtual machines.</span></span>
    
- <span data-ttu-id="0cb70-258">Службы федерации Active Directory публикуются в Интернете через прокси-серверы этих служб, работающие как виртуальные машины Azure.</span><span class="sxs-lookup"><span data-stu-id="0cb70-258">AD FS is published to the Internet through AD FS proxies running as Azure virtual machines.</span></span>
    
- <span data-ttu-id="0cb70-259">Для пользователей, подключающихся из любого расположения, трафик проверки подлинности клиентов обрабатывается серверами службы федерации Active Directory и прокси-серверами, развернутыми в качестве виртуальных машин Azure.</span><span class="sxs-lookup"><span data-stu-id="0cb70-259">Client authentication traffic, for users that are connecting from any location, is handled by AD FS servers and proxies that are deployed as Azure virtual machines.</span></span>
    
### <a name="lync-integration-with-exchange-and-sharepoint-in-office-365"></a><span data-ttu-id="0cb70-260">Интеграция Lync с Exchange и SharePoint в Office 365</span><span class="sxs-lookup"><span data-stu-id="0cb70-260">Lync integration with Exchange and SharePoint in Office 365</span></span>

#### <a name="lync-server-with-exchange-online-and-sharepoint-online"></a><span data-ttu-id="0cb70-261">Lync Server с Exchange Online и SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="0cb70-261">Lync Server with Exchange Online and SharePoint Online</span></span>

<span data-ttu-id="0cb70-262">На сопроводительной схеме вы можете видеть Office 365 с Exchange Online и SharePoint Online, подключенными к локальной ферме Lync Server 2013.</span><span class="sxs-lookup"><span data-stu-id="0cb70-262">The accompanying diagram shows Office 365 with Exchange Online and SharePoint Online connected to an on-premises Lync Server 2013 farm.</span></span>
  
<span data-ttu-id="0cb70-263">При таком варианте развертывания можно:</span><span class="sxs-lookup"><span data-stu-id="0cb70-263">The advantages of this deployment allow you to:</span></span>
  
- <span data-ttu-id="0cb70-264">Использовать все возможности Lync Server 2013.</span><span class="sxs-lookup"><span data-stu-id="0cb70-264">Use the full feature set of Lync Server 2013.</span></span>
    
- <span data-ttu-id="0cb70-265">Использовать существующее локальное телефонное оборудование, например УАТС.</span><span class="sxs-lookup"><span data-stu-id="0cb70-265">Leverage your existing on-premises phone equipment, such as PBXs.</span></span>
    
- <span data-ttu-id="0cb70-266">Использовать Exchange Online для электронной почты и уменьшения нагрузки на локальные почтовые серверы и хранилища.</span><span class="sxs-lookup"><span data-stu-id="0cb70-266">Use Exchange Online for email, off-loading the burden of on-premises email servers and storage.</span></span>
    
- <span data-ttu-id="0cb70-267">Использовать SharePoint Online для совместной работы и уменьшения нагрузки по обслуживанию локальных серверов SharePoint.</span><span class="sxs-lookup"><span data-stu-id="0cb70-267">Use SharePoint Online for collaboration, off-loading the burden of maintaining on-premises SharePoint servers.</span></span>
    
- <span data-ttu-id="0cb70-268">Использовать интегрированные функции Lync, Exchange и SharePoint, включая единую систему обмена сообщениями, в Office 365.</span><span class="sxs-lookup"><span data-stu-id="0cb70-268">Use Lync, Exchange, and SharePoint integrated features, including Unified Messaging (UM) in Office 365.</span></span>
    
#### <a name="exchange-server-with-lync-online"></a><span data-ttu-id="0cb70-269">Exchange Server с Lync Online</span><span class="sxs-lookup"><span data-stu-id="0cb70-269">Exchange Server with Lync Online</span></span>

<span data-ttu-id="0cb70-270">На сопроводительной схеме можно увидеть Office 365 с Lync Online, подключенные к локальной ферме Exchange Server.</span><span class="sxs-lookup"><span data-stu-id="0cb70-270">The accompanying diagram shows Office 365 with Lync Online connected to an on-premises Exchange Server farm.</span></span>
  
<span data-ttu-id="0cb70-271">При таком варианте развертывания можно:</span><span class="sxs-lookup"><span data-stu-id="0cb70-271">The advantages of this deployment allow you to:</span></span>
  
- <span data-ttu-id="0cb70-272">Использовать существующую инфраструктуру Exchange.</span><span class="sxs-lookup"><span data-stu-id="0cb70-272">Leverage your existing Exchange infrastructure.</span></span>
    
- <span data-ttu-id="0cb70-273">Использовать Lync Online для получения сведений о присутствии, обмена мгновенными сообщениями и проведения конференций.</span><span class="sxs-lookup"><span data-stu-id="0cb70-273">Use Lync Online for presence, instant messaging, and conferencing capabilities.</span></span>
    

