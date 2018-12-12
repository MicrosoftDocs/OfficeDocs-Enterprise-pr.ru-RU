---
title: Открытая диаграмма — варианты платформы Microsoft Exchange 2013
ms.author: josephd
author: JoeDavies-MSFT
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 129f4e45-647e-4cf1-92a6-4d86d8396e73
description: Эта статья  открытая текстовая версия диаграммыВарианты платформы Microsoft Exchange 2013, доступная в разделе Технические схемы.
ms.openlocfilehash: e1c4957c9152c5a23008c657d7e2d0d47b5cce0f
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
ms.locfileid: "17503132"
---
# <a name="accessible-diagram---microsoft-exchange-2013-platform-options"></a><span data-ttu-id="6a3b4-103">Открытая диаграмма — варианты платформы Microsoft Exchange 2013</span><span class="sxs-lookup"><span data-stu-id="6a3b4-103">Accessible diagram - Microsoft Exchange 2013 Platform Options</span></span>

<span data-ttu-id="6a3b4-104">**Сводка.** Эта статья — удобная текстовая версия схемы "Варианты платформы для Microsoft Exchange 2013", которая доступна в разделе [Технические схемы](http://go.microsoft.com/fwlink/?LinkID=519139&amp;clcid=0x409).</span><span class="sxs-lookup"><span data-stu-id="6a3b4-104">**Summary:** This article is an accessible text version of the diagram named Microsoft Exchange 2013 Platform Options, which is available at [Technical Diagrams](http://go.microsoft.com/fwlink/?LinkID=519139&amp;clcid=0x409).</span></span>
  
<span data-ttu-id="6a3b4-105">На этом плакате представлена информация о развертывании Exchange Online и Exchange Server, которая необходима лицам, принимающим деловые решения (BDM), и архитекторам. Плакат содержит:</span><span class="sxs-lookup"><span data-stu-id="6a3b4-105">This poster describes what business decision makers (BDMs) and architects need to know about Exchange Online and Exchange Server deployments and includes:</span></span> 
  
- <span data-ttu-id="6a3b4-106">Сравнение четырех доступных вариантов платформы для Exchange 2013: облачной службы Exchange Online (Office 365), гибридного развертывания Exchange, локального сервера Exchange Server и службы Exchange с размещением у поставщика.</span><span class="sxs-lookup"><span data-stu-id="6a3b4-106">A comparison of four available platform options for Exchange 2013: Exchange Online (Office 365), Exchange Hybrid, Exchange Server on-premises, and Provider-Hosted Exchange.</span></span> 
    
- <span data-ttu-id="6a3b4-107">Описания трех новых или обновленных компонентов Exchange 2013.</span><span class="sxs-lookup"><span data-stu-id="6a3b4-107">Descriptions of three new or updated features in Exchange 2013.</span></span> 
    
## <a name="comparison-of-four-different-deployments-for-the-exchange-2013-platform"></a><span data-ttu-id="6a3b4-108">Сравнение четырех различных вариантов развертывания платформы Exchange 2013</span><span class="sxs-lookup"><span data-stu-id="6a3b4-108">Comparison of four different deployments for the Exchange 2013 platform</span></span>

<span data-ttu-id="6a3b4-109">В сравнении по каждому варианту развертывания представлена следующая информация:</span><span class="sxs-lookup"><span data-stu-id="6a3b4-109">The comparison provides information about each deployment option in the following areas:</span></span> 
  
- <span data-ttu-id="6a3b4-110">обзор различных компонентов развертывания;</span><span class="sxs-lookup"><span data-stu-id="6a3b4-110">An overview of the different deployment features</span></span> 
    
- <span data-ttu-id="6a3b4-111">преимущества каждого из вариантов развертывания;</span><span class="sxs-lookup"><span data-stu-id="6a3b4-111">Benefits of implementing each deployment option</span></span> 
    
- <span data-ttu-id="6a3b4-112">требования лицензирования;</span><span class="sxs-lookup"><span data-stu-id="6a3b4-112">Licensing requirements</span></span> 
    
- <span data-ttu-id="6a3b4-113">необходимые архитектурные задачи;</span><span class="sxs-lookup"><span data-stu-id="6a3b4-113">Required architectural tasks</span></span> 
    
- <span data-ttu-id="6a3b4-114">обязанности ИТ-специалистов по внедрению каждого варианта развертывания.</span><span class="sxs-lookup"><span data-stu-id="6a3b4-114">IT Pro responsibilities for implementing each deployment option</span></span> 
    
### <a name="overview"></a><span data-ttu-id="6a3b4-115">Обзор</span><span class="sxs-lookup"><span data-stu-id="6a3b4-115">Overview</span></span>

#### <a name="exchange-online-office-365"></a><span data-ttu-id="6a3b4-116">Exchange Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="6a3b4-116">Exchange Online (Office 365)</span></span>

<span data-ttu-id="6a3b4-117">Больше эффективности и меньше затрат благодаря Office 365.</span><span class="sxs-lookup"><span data-stu-id="6a3b4-117">You gain efficiency and reduce costs with Office 365.</span></span>
  
<span data-ttu-id="6a3b4-p101">На сопутствующей диаграмме представлена служба Exchange Online с клиентом Azure Active Directory, которая синхронизирует имена и пароли учетных записей между локальной средой доменных служб Active Directory (AD DS) и клиентом Azure Active Directory. Для единого входа необходимы службы федерации Active Directory (AD FS).</span><span class="sxs-lookup"><span data-stu-id="6a3b4-p101">The accompanying diagram shows Exchange Online with an Azure Active Directory tenant which synchronizes account names and passwords between the on-premises Active Directory Domain Services (AD DS) environment and the Azure Active Directory tenant. Active Directory Federation Services (AD FS) is necessary for single sign-on.</span></span> 
  
<span data-ttu-id="6a3b4-120">Описание компонентов и функций:</span><span class="sxs-lookup"><span data-stu-id="6a3b4-120">Description of features and functionality:</span></span>
  
- <span data-ttu-id="6a3b4-121">Обслуживанием серверов и серверного программного обеспечения занимается Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="6a3b4-121">The operation of servers and server software is handled by Microsoft.</span></span>
    
- <span data-ttu-id="6a3b4-122">Обширный набор компонентов Exchange Server 2013 как облачной службы.</span><span class="sxs-lookup"><span data-stu-id="6a3b4-122">Rich feature set of Exchange Server 2013 as a cloud-based service.</span></span>
    
- <span data-ttu-id="6a3b4-123">Регулярное обновление компонентов.</span><span class="sxs-lookup"><span data-stu-id="6a3b4-123">Always up-to-date with the newest features.</span></span>
    
- <span data-ttu-id="6a3b4-124">Служба Exchange Online Protection (EOP) для защиты от спама и вредоносных программ.</span><span class="sxs-lookup"><span data-stu-id="6a3b4-124">Exchange Online Protection (EOP) is included for anti-spam/anti-malware protection.</span></span>
    
- <span data-ttu-id="6a3b4-125">Гарантия высокой доступности 99,9 % времени по условиям соглашения об уровне обслуживания (SLA).</span><span class="sxs-lookup"><span data-stu-id="6a3b4-125">Built-in high availability with a 99.9% Service Level Agreement (SLA).</span></span>
    
- <span data-ttu-id="6a3b4-p102">Синхронизация каталогов, в том числе паролей, между локальными доменными службами Active Directory (AD DS) и клиентом Azure Active Directory. Для единого входа необходимы службы федерации Active Directory (AD FS).</span><span class="sxs-lookup"><span data-stu-id="6a3b4-p102">Directory synchronization including passwords between the on-premises Active Directory Domain Services (AD DS) and the Azure Active Directory tenant. Active Directory Federation Services (AD FS) is necessary for single sign-on.</span></span>
    
#### <a name="exchange-hybrid"></a><span data-ttu-id="6a3b4-128">Гибридное развертывание Exchange</span><span class="sxs-lookup"><span data-stu-id="6a3b4-128">Exchange Hybrid</span></span>

<span data-ttu-id="6a3b4-129">Пользуйтесь преимуществами Office 365, сохранив локальный сервер Exchange Server.</span><span class="sxs-lookup"><span data-stu-id="6a3b4-129">You can leverage the benefits of Office 365 while maintaining Exchange Server on-premises.</span></span>
  
<span data-ttu-id="6a3b4-p103">На сопутствующей диаграмме представлен вариант Office 365 с Exchange Online, где некоторые пользователи размещены локально, а некоторые  в сети. Кроме того, на диаграмме представлен клиент Azure Active Directory, который синхронизирует имена и пароли учетных записей между локальной средой доменных служб Active Directory (AD DS) и клиентом Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="6a3b4-p103">The accompanying diagram shows Office 365 with Exchange Online where some users are homed on-premises and some users are homed online. It also shows an Azure Active Directory tenant which synchronizes account names and passwords between the on-premises Active Directory Domain Services (AD DS) environment and the Azure Active Directory tenant.</span></span>
  
<span data-ttu-id="6a3b4-132">Описание компонентов и функций:</span><span class="sxs-lookup"><span data-stu-id="6a3b4-132">Description of features and functionality:</span></span>
  
- <span data-ttu-id="6a3b4-133">Одни пользователи размещены локально, другие — в сети. Пользователи совместно используют общее адресное пространство электронной почты.</span><span class="sxs-lookup"><span data-stu-id="6a3b4-133">Some users are homed on-premises and some users are homed online, and users share the same e-mail address space.</span></span>
    
- <span data-ttu-id="6a3b4-134">Используется существующая инфраструктура Exchange Server.</span><span class="sxs-lookup"><span data-stu-id="6a3b4-134">Leverages your existing Exchange Server infrastructure.</span></span>
    
- <span data-ttu-id="6a3b4-135">Постепенный переход с локальной среды Exchange на Exchange Online согласно вашему расписанию.</span><span class="sxs-lookup"><span data-stu-id="6a3b4-135">Migrate from Exchange on-premises to Exchange Online over time, on your schedule.</span></span>
    
- <span data-ttu-id="6a3b4-136">Интеграция с другими приложениями Office 365, в том числе Lync Online и SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="6a3b4-136">Integrate with other Office 365 applications, including Lync Online and SharePoint Online.</span></span>
    
#### <a name="exchange-server-on-premises"></a><span data-ttu-id="6a3b4-137">Локальный сервер Exchange Server</span><span class="sxs-lookup"><span data-stu-id="6a3b4-137">Exchange Server on-premises</span></span>

<span data-ttu-id="6a3b4-138">Вы можете спроектировать и обслуживать собственную инфраструктуру Exchange Server 2013.</span><span class="sxs-lookup"><span data-stu-id="6a3b4-138">You can design and manage your own Exchange Server 2013 infrastructure.</span></span>
  
<span data-ttu-id="6a3b4-139">На сопутствующей диаграмме представлена инфраструктура Exchange Server с локальной средой доменных служб Active Directory (AD DS), где пользователи размещены локально.</span><span class="sxs-lookup"><span data-stu-id="6a3b4-139">The accompanying diagram shows an Exchange Server infrastructure with an on-premises Active Directory Domain Services (AD DS) environment where users are homed on-premises.</span></span>
  
<span data-ttu-id="6a3b4-140">Описание компонентов и функций:</span><span class="sxs-lookup"><span data-stu-id="6a3b4-140">Description of features and functionality:</span></span>
  
- <span data-ttu-id="6a3b4-141">Максимальная степень контроля и настройки для вашей конфигурации.</span><span class="sxs-lookup"><span data-stu-id="6a3b4-141">Greatest degree of control and customization for your configuration.</span></span>
    
- <span data-ttu-id="6a3b4-142">Независимость от сходства сеансов на уровне балансировки нагрузки.</span><span class="sxs-lookup"><span data-stu-id="6a3b4-142">No dependency on maintaining session affinity at the load balancing layer.</span></span>
    
- <span data-ttu-id="6a3b4-143">Высокая доступность и устойчивость сайта за счет групп обеспечения доступности баз данных (DAGs).</span><span class="sxs-lookup"><span data-stu-id="6a3b4-143">Simple high availability and site resilience using database availability groups (DAGs).</span></span>
    
- <span data-ttu-id="6a3b4-144">Средства управления доступностью для высокого уровня взаимодействия с пользователями.</span><span class="sxs-lookup"><span data-stu-id="6a3b4-144">Managed availability that helps you maintain a great user experience.</span></span>
    
- <span data-ttu-id="6a3b4-145">Использование существующего оборудования и инфраструктуры системы хранения данных.</span><span class="sxs-lookup"><span data-stu-id="6a3b4-145">Leverage existing hardware and storage infrastructure.</span></span>
    
#### <a name="provider-hosted-exchange"></a><span data-ttu-id="6a3b4-146">Exchange с размещением у поставщика</span><span class="sxs-lookup"><span data-stu-id="6a3b4-146">Provider-Hosted Exchange</span></span>

<span data-ttu-id="6a3b4-147">Вы можете передать обработку рабочих нагрузок Exchange Server поставщику решений Exchange Server.</span><span class="sxs-lookup"><span data-stu-id="6a3b4-147">You can outsource your Exchange Server workload to an Exchange Server solutions provider.</span></span>
  
<span data-ttu-id="6a3b4-148">На сопутствующей диаграмме представлена среда Exchange Server, которую обслуживает внешний поставщик.</span><span class="sxs-lookup"><span data-stu-id="6a3b4-148">The accompanying diagram shows an Exchange Server environment that is operated and maintained by a provider.</span></span>
  
<span data-ttu-id="6a3b4-149">Описание компонентов и функций:</span><span class="sxs-lookup"><span data-stu-id="6a3b4-149">Description of features and functionality:</span></span>
  
- <span data-ttu-id="6a3b4-150">Обслуживанием серверов и серверного программного обеспечения занимается ваш поставщик.</span><span class="sxs-lookup"><span data-stu-id="6a3b4-150">The operation of servers and server software is handled by your provider.</span></span>
    
- <span data-ttu-id="6a3b4-151">Планирование, определение размеров, масштабирование и техническое обслуживание инфраструктуры Exchange Server поручаются вашему поставщику.</span><span class="sxs-lookup"><span data-stu-id="6a3b4-151">Planning, sizing, scaling, and maintenance of the Exchange Server infrastructure are delegated to your provider.</span></span>
    
- <span data-ttu-id="6a3b4-152">Эксплуатационным обслуживанием занимается ваш поставщик.</span><span class="sxs-lookup"><span data-stu-id="6a3b4-152">Service maintenance is handled by your provider.</span></span>
    
- <span data-ttu-id="6a3b4-153">Набор компонентов Exchange зависит от версии программного обеспечения, развернутого вашим поставщиком.</span><span class="sxs-lookup"><span data-stu-id="6a3b4-153">The Exchange feature set is limited to the software version deployed by your provider.</span></span>
    
### <a name="benefits-of-implementing-each-deployment-option"></a><span data-ttu-id="6a3b4-154">Преимущества каждого из вариантов развертывания</span><span class="sxs-lookup"><span data-stu-id="6a3b4-154">Benefits of implementing each deployment option</span></span>

#### <a name="exchange-online-office-365"></a><span data-ttu-id="6a3b4-155">Exchange Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="6a3b4-155">Exchange Online (Office 365)</span></span>

<span data-ttu-id="6a3b4-156">Этот вариант наиболее подходит:</span><span class="sxs-lookup"><span data-stu-id="6a3b4-156">This deployment option is best for:</span></span>
  
- <span data-ttu-id="6a3b4-157">для организаций, которым нужно снизить эксплуатационные расходы на локально развернутые службы Exchange;</span><span class="sxs-lookup"><span data-stu-id="6a3b4-157">Organizations looking to reduce operations costs for on-premises Exchange deployments.</span></span>
    
- <span data-ttu-id="6a3b4-158">организаций, которые намерены воспользоваться другими предложениями Office 365, такими как SharePoint Online и Lync Online.</span><span class="sxs-lookup"><span data-stu-id="6a3b4-158">Organizations that plan to leverage other Office 365 offerings, such as SharePoint Online and Lync Online.</span></span>
    
#### <a name="exchange-hybrid"></a><span data-ttu-id="6a3b4-159">Гибридное развертывание Exchange</span><span class="sxs-lookup"><span data-stu-id="6a3b4-159">Exchange Hybrid</span></span>

<span data-ttu-id="6a3b4-160">Этот вариант наиболее подходит:</span><span class="sxs-lookup"><span data-stu-id="6a3b4-160">This deployment option is best for:</span></span>
  
- <span data-ttu-id="6a3b4-161">для ускорения перехода с локальной среды Exchange на Exchange Online;</span><span class="sxs-lookup"><span data-stu-id="6a3b4-161">Facilitating a migration from Exchange on-premises to Exchange Online.</span></span>
    
- <span data-ttu-id="6a3b4-162">поддержки удаленных сайтов без вложений в создание инфраструктуры филиалов;</span><span class="sxs-lookup"><span data-stu-id="6a3b4-162">Supporting remote sites without investing in branch office infrastructure.</span></span>
    
- <span data-ttu-id="6a3b4-163">транснациональных корпораций с дочерними компаниями, которым необходимо локальное размещение данных.</span><span class="sxs-lookup"><span data-stu-id="6a3b4-163">Multinational corporations with subsidiaries that require data to reside on-premises.</span></span>
    
#### <a name="exchange-server-on-premises"></a><span data-ttu-id="6a3b4-164">Локальный сервер Exchange Server</span><span class="sxs-lookup"><span data-stu-id="6a3b4-164">Exchange Server on-premises</span></span>

<span data-ttu-id="6a3b4-165">Этот вариант наиболее подходит:</span><span class="sxs-lookup"><span data-stu-id="6a3b4-165">This deployment option is best for:</span></span>
  
- <span data-ttu-id="6a3b4-166">для решений с широкими возможностями настройки;</span><span class="sxs-lookup"><span data-stu-id="6a3b4-166">Highly customized solutions.</span></span>
    
- <span data-ttu-id="6a3b4-167">устаревших решений со сторонними компонентами, которые работают на аппаратном и программном обеспечении, не поддерживаемом службой Exchange Online;</span><span class="sxs-lookup"><span data-stu-id="6a3b4-167">Legacy solutions with third-party components that depend on hardware and software that are not supported by Exchange Online.</span></span>
    
- <span data-ttu-id="6a3b4-168">организаций, регулярно проходящих процедуры контроля управления данными, по причине чего необходимо локальное размещение данных;</span><span class="sxs-lookup"><span data-stu-id="6a3b4-168">Organizations subject to data governance regulations that require data to reside on-premises.</span></span>
    
- <span data-ttu-id="6a3b4-169">организаций, которым необходимо сохранить полный контроль над платформой и решением.</span><span class="sxs-lookup"><span data-stu-id="6a3b4-169">Organizations that wish to retain control of the entire platform and solution.</span></span>
    
#### <a name="provider-hosted-exchange"></a><span data-ttu-id="6a3b4-170">Exchange с размещением у поставщика</span><span class="sxs-lookup"><span data-stu-id="6a3b4-170">Provider-Hosted Exchange</span></span>

<span data-ttu-id="6a3b4-171">Этот вариант наиболее подходит:</span><span class="sxs-lookup"><span data-stu-id="6a3b4-171">This deployment option is best for:</span></span>
  
- <span data-ttu-id="6a3b4-172">для организаций, которым нужны функции Exchange Server без необходимости самостоятельно развертывать и обслуживать платформу;</span><span class="sxs-lookup"><span data-stu-id="6a3b4-172">Organizations that need Exchange Server functionality, but want to outsource its deployment and maintenance.</span></span>
    
- <span data-ttu-id="6a3b4-173">организаций, которым необходимы специальные варианты поддержки;</span><span class="sxs-lookup"><span data-stu-id="6a3b4-173">Organizations that need personalized support options.</span></span>
    
- <span data-ttu-id="6a3b4-174">специальных решений и интеграции с настраиваемыми приложениями от поставщика;</span><span class="sxs-lookup"><span data-stu-id="6a3b4-174">Customized solutions and integration with custom applications offered by the provider.</span></span>
    
- <span data-ttu-id="6a3b4-175">устаревших решений со сторонними компонентами, которые работают на аппаратном и программном обеспечении, не поддерживаемом службой Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="6a3b4-175">Legacy solutions with third-party components that depend on hardware and software that are not supported by Exchange Online.</span></span>
    
### <a name="license-requirements"></a><span data-ttu-id="6a3b4-176">Требования лицензирования</span><span class="sxs-lookup"><span data-stu-id="6a3b4-176">License requirements</span></span>

<span data-ttu-id="6a3b4-177">В следующей таблице подробно описаны требования лицензирования для каждого варианта развертывания.</span><span class="sxs-lookup"><span data-stu-id="6a3b4-177">The following table details the license requirements for each deployment option.</span></span>
  
|<span data-ttu-id="6a3b4-178">**Вариант развертывания**</span><span class="sxs-lookup"><span data-stu-id="6a3b4-178">**Deployment option**</span></span>|<span data-ttu-id="6a3b4-179">**Требования лицензирования**</span><span class="sxs-lookup"><span data-stu-id="6a3b4-179">**License requirements**</span></span>|
|:-----|:-----|
|<span data-ttu-id="6a3b4-180">Exchange Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="6a3b4-180">Exchange Online (Office 365)</span></span>  <br/> |<span data-ttu-id="6a3b4-181">Модель подписки</span><span class="sxs-lookup"><span data-stu-id="6a3b4-181">Subscription model</span></span>  <br/> |
|<span data-ttu-id="6a3b4-182">Гибридное развертывание Exchange</span><span class="sxs-lookup"><span data-stu-id="6a3b4-182">Exchange Hybrid</span></span>  <br/> | <span data-ttu-id="6a3b4-183">Office 365  модель подписки</span><span class="sxs-lookup"><span data-stu-id="6a3b4-183">Office 365 - Subscription model</span></span> <br/>  <span data-ttu-id="6a3b4-184">Локальное развертывание  действительны все локальные лицензии (проверьте лицензии для локального сервера Exchange Server)</span><span class="sxs-lookup"><span data-stu-id="6a3b4-184">On-premises - All on-premises licenses apply (review licenses for Exchanges Server on-premises)</span></span> <br/>  <span data-ttu-id="6a3b4-185">Лицензия на гибридный сервер\*</span><span class="sxs-lookup"><span data-stu-id="6a3b4-185">Hybrid server license\*</span></span> <br/> |
|<span data-ttu-id="6a3b4-186">Локальный сервер Exchange Server</span><span class="sxs-lookup"><span data-stu-id="6a3b4-186">Exchange Server on-premises</span></span>  <br/> | <span data-ttu-id="6a3b4-187">Серверная операционная система</span><span class="sxs-lookup"><span data-stu-id="6a3b4-187">Server Operating System</span></span> <br/>  <span data-ttu-id="6a3b4-188">Серверная лицензия Exchange 2013</span><span class="sxs-lookup"><span data-stu-id="6a3b4-188">Exchange 2013 Server License</span></span> <br/>  <span data-ttu-id="6a3b4-189">Клиентская лицензия Exchange 2013</span><span class="sxs-lookup"><span data-stu-id="6a3b4-189">Exchange 2013 Client Access License</span></span> <br/> |
|<span data-ttu-id="6a3b4-190">Exchange с размещением у поставщика</span><span class="sxs-lookup"><span data-stu-id="6a3b4-190">Provider-Hosted Exchange</span></span>  <br/> |<span data-ttu-id="6a3b4-191">Стоимость регулируется соглашением с поставщиком</span><span class="sxs-lookup"><span data-stu-id="6a3b4-191">Costs are based on the agreement with the provider</span></span>  <br/> |
   
### <a name="architecture-tasks"></a><span data-ttu-id="6a3b4-192">Архитектурные задачи</span><span class="sxs-lookup"><span data-stu-id="6a3b4-192">Architecture tasks</span></span>

<span data-ttu-id="6a3b4-193">В этом разделе перечислены архитектурные задачи для каждого варианта развертывания.</span><span class="sxs-lookup"><span data-stu-id="6a3b4-193">This section lists the architectural tasks for each deployment option.</span></span>
  
#### <a name="exchange-online-office-365"></a><span data-ttu-id="6a3b4-194">Exchange Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="6a3b4-194">Exchange Online (Office 365)</span></span>

- <span data-ttu-id="6a3b4-195">Создание плана и проекта синхронизации каталогов.</span><span class="sxs-lookup"><span data-stu-id="6a3b4-195">Plan and design the directory synchronization.</span></span>
    
- <span data-ttu-id="6a3b4-196">Обеспечение достаточной пропускной способности сети и надежного подключения через брандмауэры, прокси-серверы, шлюзы и каналы глобальной сети (WAN).</span><span class="sxs-lookup"><span data-stu-id="6a3b4-196">Ensure network capacity and connectivity through firewalls, proxy servers, gateways, and across WAN links.</span></span>
    
#### <a name="exchange-hybrid"></a><span data-ttu-id="6a3b4-197">Гибридное развертывание Exchange</span><span class="sxs-lookup"><span data-stu-id="6a3b4-197">Exchange Hybrid</span></span>

<span data-ttu-id="6a3b4-198">Помимо выполнения архитектурных задач для Office 365 и локальной среды, необходимо следующее:</span><span class="sxs-lookup"><span data-stu-id="6a3b4-198">In addition to the architecture tasks for both the Office 365 and on-premises environments:</span></span>
  
- <span data-ttu-id="6a3b4-199">Принять решение о предоставлении возможности единого входа.</span><span class="sxs-lookup"><span data-stu-id="6a3b4-199">Decide whether to provide a single-sign on experience.</span></span>
    
- <span data-ttu-id="6a3b4-200">Принять решение о направлении входящих сообщений электронной почты через локальную среду либо через службу Exchange Online Protection.</span><span class="sxs-lookup"><span data-stu-id="6a3b4-200">Decide whether to route inbound Internet mail through an on-premises organization or through Exchange Online Protection.</span></span>
    
#### <a name="exchange-server-on-premises"></a><span data-ttu-id="6a3b4-201">Локальный сервер Exchange Server</span><span class="sxs-lookup"><span data-stu-id="6a3b4-201">Exchange Server on-premises</span></span>

- <span data-ttu-id="6a3b4-202">Разработка топологии Exchange.</span><span class="sxs-lookup"><span data-stu-id="6a3b4-202">Design the Exchange topology.</span></span>
    
- <span data-ttu-id="6a3b4-203">Расчет емкости для серверного оборудования.</span><span class="sxs-lookup"><span data-stu-id="6a3b4-203">Plan the capacity for server hardware.</span></span>
    
- <span data-ttu-id="6a3b4-204">Разработка топологии маршрутизации сообщений.</span><span class="sxs-lookup"><span data-stu-id="6a3b4-204">Design the message routing topology.</span></span>
    
- <span data-ttu-id="6a3b4-205">Разработка схемы балансировки нагрузки для серверов клиентского доступа.</span><span class="sxs-lookup"><span data-stu-id="6a3b4-205">Design load balancing for Client Access servers.</span></span>
    
- <span data-ttu-id="6a3b4-206">Создание плана поддержания высокой доступности за счет групп обеспечения доступности баз данных.</span><span class="sxs-lookup"><span data-stu-id="6a3b4-206">Plan for high availability using database availability groups.</span></span>
    
#### <a name="provider-hosted-exchange"></a><span data-ttu-id="6a3b4-207">Exchange с размещением у поставщика</span><span class="sxs-lookup"><span data-stu-id="6a3b4-207">Provider-Hosted Exchange</span></span>

<span data-ttu-id="6a3b4-208">Необходимо убедиться, что ваш поставщик располагает достаточной пропускной способностью сети и надежным подключением через брандмауэры, прокси-серверы, шлюзы и каналы глобальной сети (WAN).</span><span class="sxs-lookup"><span data-stu-id="6a3b4-208">Ensure that the network capacity and availability through firewalls, proxy servers, gateways, and across WAN links are available to your provider.</span></span>
  
### <a name="it-pro-responsibilities"></a><span data-ttu-id="6a3b4-209">Обязанности ИТ-специалистов</span><span class="sxs-lookup"><span data-stu-id="6a3b4-209">IT Pro responsibilities</span></span>

<span data-ttu-id="6a3b4-210">В этом разделе перечислены обязанности ИТ-специалистов по внедрению каждого варианта развертывания.</span><span class="sxs-lookup"><span data-stu-id="6a3b4-210">This section lists the IT Pro responsibilities for each deployment option.</span></span>
  
#### <a name="exchange-online-office-365"></a><span data-ttu-id="6a3b4-211">Exchange Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="6a3b4-211">Exchange Online (Office 365)</span></span>

- <span data-ttu-id="6a3b4-212">Внедрение плана синхронизации каталогов.</span><span class="sxs-lookup"><span data-stu-id="6a3b4-212">Implement the directory synchronization plan.</span></span>
    
- <span data-ttu-id="6a3b4-213">Планирование внутренних и внешних записей DNS и маршрутизации.</span><span class="sxs-lookup"><span data-stu-id="6a3b4-213">Plan and implement internal and external DNS records and routing.</span></span>
    
- <span data-ttu-id="6a3b4-214">Настройка прокси-сервера или брандмауэра для IP-адреса Office 365 и требований URL-адреса.</span><span class="sxs-lookup"><span data-stu-id="6a3b4-214">Configure the proxy server or firewall for the Office 365 IP address and URL requirements.</span></span>
    
- <span data-ttu-id="6a3b4-215">Администрирование учетных записей пользователей и настроек Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="6a3b4-215">Administer the user accounts and the Exchange Online settings.</span></span>
    
#### <a name="exchange-hybrid"></a><span data-ttu-id="6a3b4-216">Гибридное развертывание Exchange</span><span class="sxs-lookup"><span data-stu-id="6a3b4-216">Exchange Hybrid</span></span>

<span data-ttu-id="6a3b4-217">Помимо выполнения ИТ-специалистами Office 365 и локальной среды своих обязанностей, необходимо следующее:</span><span class="sxs-lookup"><span data-stu-id="6a3b4-217">In addition to the IT Pro responsibilities for both the Office 365 and on-premises environments:</span></span>
  
- <span data-ttu-id="6a3b4-218">Настройка служб федерации Active Directory (AD FS) для единого входа (при необходимости).</span><span class="sxs-lookup"><span data-stu-id="6a3b4-218">Configure Active Directory Federation Services (AD FS) for single-sign on (if desired).</span></span>
    
- <span data-ttu-id="6a3b4-219">Настройка сертификатов Exchange для безопасных соединений между серверами Exchange 2013 и Office 365.</span><span class="sxs-lookup"><span data-stu-id="6a3b4-219">Configure Exchange certificates for secure communications between Exchange 2013 servers and Office 365.</span></span>
    
- <span data-ttu-id="6a3b4-220">Настройка записей DNS для указания необходимого маршрута входящих сообщений электронной почты.</span><span class="sxs-lookup"><span data-stu-id="6a3b4-220">Configure DNS records for the desired inbound Internet mail path.</span></span>
    
#### <a name="exchange-server-on-premises"></a><span data-ttu-id="6a3b4-221">Локальный сервер Exchange Server</span><span class="sxs-lookup"><span data-stu-id="6a3b4-221">Exchange Server on-premises</span></span>

- <span data-ttu-id="6a3b4-222">Настройка необходимых сертификатов для служб Exchange.</span><span class="sxs-lookup"><span data-stu-id="6a3b4-222">Configure the necessary certificates for Exchange services.</span></span>
    
- <span data-ttu-id="6a3b4-223">Подготовка серверов к работе.</span><span class="sxs-lookup"><span data-stu-id="6a3b4-223">Provision the servers.</span></span>
    
- <span data-ttu-id="6a3b4-224">Внедрение топологии маршрутизации сообщений Exchange.</span><span class="sxs-lookup"><span data-stu-id="6a3b4-224">Implement the Exchange message routing topology.</span></span>
    
- <span data-ttu-id="6a3b4-225">Внедрение групп обеспечения доступности баз данных.</span><span class="sxs-lookup"><span data-stu-id="6a3b4-225">Implement database availability groups.</span></span>
    
- <span data-ttu-id="6a3b4-226">Обновление и обслуживание серверов Exchange.</span><span class="sxs-lookup"><span data-stu-id="6a3b4-226">Update and maintain Exchange servers.</span></span>
    
- <span data-ttu-id="6a3b4-227">Добавление или отключение серверов в зависимости от нагрузки.</span><span class="sxs-lookup"><span data-stu-id="6a3b4-227">Depending on utilization, add or remove servers as needed.</span></span>
    
#### <a name="provider-hosted-exchange"></a><span data-ttu-id="6a3b4-228">Exchange с размещением у поставщика</span><span class="sxs-lookup"><span data-stu-id="6a3b4-228">Provider-Hosted Exchange</span></span>

<span data-ttu-id="6a3b4-229">Поставщик отвечает за следующие функции:</span><span class="sxs-lookup"><span data-stu-id="6a3b4-229">The provider's responsibilities include:</span></span>
  
- <span data-ttu-id="6a3b4-230">Системное и эксплуатационное обслуживание.</span><span class="sxs-lookup"><span data-stu-id="6a3b4-230">System and service maintenance.</span></span>
    
- <span data-ttu-id="6a3b4-231">Внедрение новых компонентов.</span><span class="sxs-lookup"><span data-stu-id="6a3b4-231">Feature rollouts.</span></span>
    
- <span data-ttu-id="6a3b4-232">Защита данных и аварийное восстановление.</span><span class="sxs-lookup"><span data-stu-id="6a3b4-232">Data protection and disaster recovery.</span></span>
    
<span data-ttu-id="6a3b4-233">В обязанности ИТ-специалистов вашей организации входит создание и контроль учетных записей пользователей.</span><span class="sxs-lookup"><span data-stu-id="6a3b4-233">The IT staff's responsibilities in your organization include creating and managing user accounts.</span></span>
  
#### <a name="more-information"></a><span data-ttu-id="6a3b4-234">Подробнее</span><span class="sxs-lookup"><span data-stu-id="6a3b4-234">More information</span></span>

<span data-ttu-id="6a3b4-235">Подробные сведения об Exchange Online (Office 365) см. в следующих разделах:</span><span class="sxs-lookup"><span data-stu-id="6a3b4-235">To learn more about Exchange Online (Office 365), see the following:</span></span>
  
- [<span data-ttu-id="6a3b4-236">Описание службы Exchange Online</span><span class="sxs-lookup"><span data-stu-id="6a3b4-236">Exchange Online service description</span></span>](https://aka.ms/EXOSD)
    
- [<span data-ttu-id="6a3b4-237">Библиотека статей об Exchange Online на TechNet</span><span class="sxs-lookup"><span data-stu-id="6a3b4-237">Exchange Online library on TechNet</span></span>](https://aka.ms/EXOTN)
    
- [<span data-ttu-id="6a3b4-238">Портал Exchange Online</span><span class="sxs-lookup"><span data-stu-id="6a3b4-238">Exchange Online portal</span></span>](https://aka.ms/EXO)
    
<span data-ttu-id="6a3b4-239">Подробные сведения о гибридном развертывании Exchange см. по следующим ссылкам:</span><span class="sxs-lookup"><span data-stu-id="6a3b4-239">To learn more about Exchange Hybrid, see the following:</span></span>
  
- <span data-ttu-id="6a3b4-p104">[Гибридные развертывания Exchange 2013](https://aka.ms/ExchangeHybrid). Обратите внимание, что лицензия на гибридный сервер необходима только в следующих конфигурациях: организация Exchange 2010 с гибридным сервером Exchange 2013 либо организация Exchange 2007 с гибридным сервером Exchange 2013 или Exchange 2010.</span><span class="sxs-lookup"><span data-stu-id="6a3b4-p104">[Exchange 2013 hybrid deployments](https://aka.ms/ExchangeHybrid). You should note that the Hybrid server license is only required for the following scenarios: Exchange 2010 organization with Exchange 2013 hybrid server and Exchange 2007 organization with Exchange 2013 or Exchange 2010 hybrid server.</span></span>
    
- [<span data-ttu-id="6a3b4-242">Вход в учетную запись Office 365</span><span class="sxs-lookup"><span data-stu-id="6a3b4-242">Office 365 Sign in</span></span>](https://aka.ms/HybridKey)
    
<span data-ttu-id="6a3b4-243">Подробнее о локальном сервере Exchange Server см. по следующим ссылкам:</span><span class="sxs-lookup"><span data-stu-id="6a3b4-243">To learn more about Exchange Server on-premises, see the following:</span></span>
  
- [<span data-ttu-id="6a3b4-244">Библиотека статей об Exchange Server 2013 на TechNet</span><span class="sxs-lookup"><span data-stu-id="6a3b4-244">Exchange Server 2013 library on TechNet</span></span>](https://aka.ms/Ex2013TN)
    
- [<span data-ttu-id="6a3b4-245">Портал Exchange Server 2013</span><span class="sxs-lookup"><span data-stu-id="6a3b4-245">Exchange Server 2013 portal</span></span>](https://aka.ms/Exchange2013)
    
- [<span data-ttu-id="6a3b4-246">Архитектура Exchange Server 2013</span><span class="sxs-lookup"><span data-stu-id="6a3b4-246">Exchange Server 2013 architecture</span></span>](https://aka.ms/Ex2013SP1ArchPoster)
    
<span data-ttu-id="6a3b4-247">Подробнее об Exchange с размещением у поставщика см. по следующим ссылкам:</span><span class="sxs-lookup"><span data-stu-id="6a3b4-247">To learn more about Provider-Hosted Exchange, see the following:</span></span>
  
[<span data-ttu-id="6a3b4-248">Решения и руководства по размещению и мультитенантности, касающиеся Exchange Server 2013</span><span class="sxs-lookup"><span data-stu-id="6a3b4-248">Exchange Server 2013 hosting and multi-tenancy solutions and guidance</span></span>](https://aka.ms/Ex2013Hosting)
  
## <a name="descriptions-of-three-new-or-updated-features-in-exchange-2013"></a><span data-ttu-id="6a3b4-249">Описания трех новых или обновленных компонентов Exchange 2013</span><span class="sxs-lookup"><span data-stu-id="6a3b4-249">Descriptions of three new or updated features in Exchange 2013</span></span>

### <a name="exchange-online-protection"></a><span data-ttu-id="6a3b4-250">Exchange Online Protection</span><span class="sxs-lookup"><span data-stu-id="6a3b4-250">Exchange Online Protection</span></span>

<span data-ttu-id="6a3b4-p105">Служба Exchange Online Protection (EOP) обеспечивает защиту любого варианта развертывания от спама и вредоносных программ при помощи набора защитных компонентов, которые внедряются в глобальной сети центров обработки данных. Это позволяет упростить контроль сред обмена сообщениями. Служба EOP включена в набор подписок Exchange Online, но ее также можно использовать для гибридного или локального развертывания.</span><span class="sxs-lookup"><span data-stu-id="6a3b4-p105">Exchange Online Protection (EOP) provides anti-spam and anti-malware protection for any deployment by providing a layer of protection features that are deployed across a global network of data centers. This helps you to simplify the management of your messaging environments. EOP is included in Exchange Online subscriptions, but you can also leverage it for hybrid and on-premises deployments.</span></span>
  
<span data-ttu-id="6a3b4-254">На сопутствующих диаграммах представлены варианты развертывания для Exchange Online, гибридного развертывания Exchange и локальной среды Exchange, которые включают службу EOP в глобальной сети.</span><span class="sxs-lookup"><span data-stu-id="6a3b4-254">The accompanying diagrams show deployments for Exchange Online, Exchange Hybrid, and Exchange on-premises that include the EOP layer in the global network.</span></span>
  
### <a name="exchange-server-deployment-assistant"></a><span data-ttu-id="6a3b4-255">Помощник по развертыванию Exchange Server</span><span class="sxs-lookup"><span data-stu-id="6a3b4-255">Exchange Server Deployment Assistant</span></span>

<span data-ttu-id="6a3b4-p106">Помощник по развертыванию Exchange Server — это веб-инструмент, который запрашивает у вас определенную информацию о существующей среде и поэтапно составляет индивидуальный контрольный список, чтобы облегчить развертывание Exchange Server для разных сценариев. Помощник по развертыванию Exchange Server составляет индивидуальный контрольный список развертывания именно для вашего сценария, будь то переход с более ранней версии Exchange на Exchange 2013, переход на Exchange Online или построение гибридной инфраструктуры.</span><span class="sxs-lookup"><span data-stu-id="6a3b4-p106">The Exchange Server Deployment Assistant is a web-based tool that asks you a few questions about your current environment, and then generates a custom step-by-step checklist to help you deploy Exchange Server for different types of scenarios. Whether you are migrating from a previous version of Exchange to Exchange 2013, migrating to Exchange Online, or planning a hybrid infrastructure, the Exchange Server Deployment Assistant creates a customized deployment checklist for your scenario.</span></span>
  
<span data-ttu-id="6a3b4-258">На сопутствующем изображении представлен пример контрольного списка, составленного средствами Помощника по развертыванию Exchange Server.</span><span class="sxs-lookup"><span data-stu-id="6a3b4-258">The accompanying screenshot shows an example checklist that was created using the Exchange Server Deployment Assistant.</span></span>
  
### <a name="integration-with-lync-and-sharepoint"></a><span data-ttu-id="6a3b4-259">Интеграция с Lync и SharePoint</span><span class="sxs-lookup"><span data-stu-id="6a3b4-259">Integration with Lync and SharePoint</span></span>

<span data-ttu-id="6a3b4-p107">В состав Exchange Server 2013 входит множество компонентов, интегрируемых с Lync Server 2013 и SharePoint Server 2013. В совокупности эти продукты располагают обширным набором функций и позволяют улучшить взаимодействие сотрудников внутри организации.</span><span class="sxs-lookup"><span data-stu-id="6a3b4-p107">Exchange Server 2013 includes many features that integrate with Lync Server 2013 and SharePoint Server 2013. Together, these products offer a rich suite of features and improve collaboration across your organization.</span></span> 
  
<span data-ttu-id="6a3b4-262">На сопутствующей диаграмме представлен плакат по функциям проверки подлинности сервера и ссылка на него.</span><span class="sxs-lookup"><span data-stu-id="6a3b4-262">An accompanying diagram shows the Server-to-Server Authentication poster and includes a link to the poster.</span></span> 
  
- <span data-ttu-id="6a3b4-263">Архивация, хранение и обнаружение электронных данных</span><span class="sxs-lookup"><span data-stu-id="6a3b4-263">Archiving, hold and eDiscovery</span></span>
    
- <span data-ttu-id="6a3b4-264">Почтовые ящики сайта</span><span class="sxs-lookup"><span data-stu-id="6a3b4-264">Site mailboxes</span></span>
    
- <span data-ttu-id="6a3b4-265">Единое хранилище контактов</span><span class="sxs-lookup"><span data-stu-id="6a3b4-265">Unified contact store</span></span>
    
- <span data-ttu-id="6a3b4-266">Фотографии пользователей в высоком разрешении</span><span class="sxs-lookup"><span data-stu-id="6a3b4-266">High-resolution user photos</span></span>
    
- <span data-ttu-id="6a3b4-267">Сведения о присутствии Lync в Outlook и Outlook Web App</span><span class="sxs-lookup"><span data-stu-id="6a3b4-267">Lync presence in Outlook and Outlook Web App</span></span>
    
- <span data-ttu-id="6a3b4-268">Проверка подлинности сервера</span><span class="sxs-lookup"><span data-stu-id="6a3b4-268">Server-to-server authentication</span></span>
    
- <span data-ttu-id="6a3b4-269">Голосовая почта</span><span class="sxs-lookup"><span data-stu-id="6a3b4-269">Voicemail</span></span>
    
- <span data-ttu-id="6a3b4-270">Записи собраний</span><span class="sxs-lookup"><span data-stu-id="6a3b4-270">Meeting recordings</span></span>
    
- <span data-ttu-id="6a3b4-271">Синхронизация задач Exchange</span><span class="sxs-lookup"><span data-stu-id="6a3b4-271">Exchange task synchronization</span></span>
    
<span data-ttu-id="6a3b4-272">На сопутствующей диаграмме представлен плакат, посвященный архитектуре Exchange Server 2013 с пакетом обновления 1 (SP1) и ссылка на него.</span><span class="sxs-lookup"><span data-stu-id="6a3b4-272">An accompanying diagram shows the Exchange Server 2013 SP1 Architecture poster and includes a link to the poster.</span></span>
  

