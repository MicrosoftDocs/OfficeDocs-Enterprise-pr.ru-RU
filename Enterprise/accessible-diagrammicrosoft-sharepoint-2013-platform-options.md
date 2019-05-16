---
title: Доступная схема — варианты платформы Microsoft SharePoint 2013
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: b88200bf-ced0-4ae6-bbe5-5517377d1be1
description: Эта статья представляет собой текстовую версию схемы "Варианты платформы Microsoft SharePoint 2013".
ms.openlocfilehash: 4a0b068ffb8abbe11c2286f3daa70c5f62295425
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068605"
---
# <a name="accessible-diagram---microsoft-sharepoint-2013-platform-options"></a><span data-ttu-id="1923e-103">Доступная схема — варианты платформы Microsoft SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="1923e-103">Accessible diagram - Microsoft SharePoint 2013 Platform Options</span></span>

<span data-ttu-id="1923e-104">**Сводка:** Эта статья представляет собой текстовую версию схемы, именуемую вариантами платформы Microsoft SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="1923e-104">**Summary:** This article is an accessible text version of the diagram named Microsoft SharePoint 2013 Platform Options.</span></span>
  
<span data-ttu-id="1923e-105">Какие лица, принимающие решения в Организации (вариантах развертывания) и архитекторы, должны знать о разрешениях для Office 365, Microsoft Azure и локальных развертываний.</span><span class="sxs-lookup"><span data-stu-id="1923e-105">What business decision makers (BDMs) and architects need to know about Office 365, Microsoft Azure, and on-premises deployments.</span></span> 
  
<span data-ttu-id="1923e-106">Этот плакат состоит из двух следующих разделов.</span><span class="sxs-lookup"><span data-stu-id="1923e-106">This poster has two sections:</span></span> 
  
- <span data-ttu-id="1923e-107">Сравнение четырех различных развертываний для SharePoint 2013: SharePoint в Office 365, гибридной среды Office 365 с локальным развертыванием SharePoint 2013, Azure и локальным развертыванием SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="1923e-107">A comparison of four different deployments for SharePoint 2013: SharePoint in Office 365, a hybrid of Office 365 with an on-premises deployment of SharePoint 2013, Azure, and an on-premises deployment of SharePoint 2013.</span></span> 
    
- <span data-ttu-id="1923e-108">Описание трех типичных рабочих нагрузок для перемещения в Azure.</span><span class="sxs-lookup"><span data-stu-id="1923e-108">A description of three typical workloads to move to Azure.</span></span> 
    
## <a name="comparison-of-four-different-deployments-for-the-sharepoint-2013-platform"></a><span data-ttu-id="1923e-109">Сравнение четырех различных вариантов развертывания платформы SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="1923e-109">Comparison of four different deployments for the SharePoint 2013 platform</span></span>

<span data-ttu-id="1923e-110">В сравнении по каждому варианту развертывания представлена следующая информация:</span><span class="sxs-lookup"><span data-stu-id="1923e-110">The comparison provides information about each deployment option related to the following areas:</span></span> 
  
- <span data-ttu-id="1923e-111">обзор различных компонентов развертывания;</span><span class="sxs-lookup"><span data-stu-id="1923e-111">An overview of the different deployment features</span></span> 
    
- <span data-ttu-id="1923e-112">рекомендации по оптимальному использованию каждого типа развертывания; </span><span class="sxs-lookup"><span data-stu-id="1923e-112">What each type of deployment is best for</span></span> 
    
- <span data-ttu-id="1923e-113">Требования лицензирования</span><span class="sxs-lookup"><span data-stu-id="1923e-113">License requirements</span></span> 
    
- <span data-ttu-id="1923e-114">архитектурные задачи, необходимые для реализации решения; </span><span class="sxs-lookup"><span data-stu-id="1923e-114">Architecture tasks required to implement</span></span> 
    
- <span data-ttu-id="1923e-115">обязанности ИТ-специалистов в отношении реализации решения. </span><span class="sxs-lookup"><span data-stu-id="1923e-115">IT pro responsibilities for implementation</span></span> 
    
### <a name="overview"></a><span data-ttu-id="1923e-116">Обзор</span><span class="sxs-lookup"><span data-stu-id="1923e-116">Overview</span></span>

#### <a name="sharepoint-2013-in-office-365"></a><span data-ttu-id="1923e-117">SharePoint 2013 в Office 365</span><span class="sxs-lookup"><span data-stu-id="1923e-117">SharePoint 2013 in Office 365</span></span>

<span data-ttu-id="1923e-118">Повысить эффективность и оптимизировать стоимость с помощью планов Office 365 для нескольких клиентов.</span><span class="sxs-lookup"><span data-stu-id="1923e-118">Gain efficiency and optimize for cost with Office 365 multitenant plans.</span></span> 
  
<span data-ttu-id="1923e-119">На сопроводительной схеме показана среда SharePoint Online с клиентом Azure Active Directory, которая синхронизирует имена и пароли учетных записей между локальной средой Active Directory и клиентом Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="1923e-119">The accompanying diagram shows SharePoint Online with an Azure Active Directory tenant, which synchronizes account names and passwords between the on-premises Active Directory environment and the Azure Active Directory tenant.</span></span> 
  
<span data-ttu-id="1923e-120">Описание функций</span><span class="sxs-lookup"><span data-stu-id="1923e-120">Description of features:</span></span> 
  
- <span data-ttu-id="1923e-121">Программное обеспечение как услуга (SaaS).</span><span class="sxs-lookup"><span data-stu-id="1923e-121">Software as a Service (SaaS).</span></span> 
    
- <span data-ttu-id="1923e-122">Широкий спектр функций постоянно обновляется. </span><span class="sxs-lookup"><span data-stu-id="1923e-122">Rich feature set is always up to date.</span></span> 
    
- <span data-ttu-id="1923e-123">Включает клиент Azure Active Directory (может использоваться с другими приложениями).</span><span class="sxs-lookup"><span data-stu-id="1923e-123">Includes an Azure Active Directory tenant (can be used with other applications).</span></span> 
    
- <span data-ttu-id="1923e-124">Интеграция каталогов включает синхронизацию имен учетных записей и паролей между локальной средой Active Directory и клиентом Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="1923e-124">Directory integration includes synchronizing account names and passwords between the on-premises Active Directory environment and the Azure Active Directory tenant.</span></span> 
    
- <span data-ttu-id="1923e-125">Если необходима функция единого входа, можно реализовать службы федерации Active Directory (AD FS).  </span><span class="sxs-lookup"><span data-stu-id="1923e-125">If single sign-on (SSO) is a requirement, Active Directory Federation Services (AD FS) can be implemented.</span></span> 
    
- <span data-ttu-id="1923e-126">Связь с клиентом через Интернет шифруется и сопровождается проверкой подлинности (через порт 443). </span><span class="sxs-lookup"><span data-stu-id="1923e-126">Client communication over the Internet through encrypted and authenticated access (port 443).</span></span> 
    
- <span data-ttu-id="1923e-127">Перенос данных ограничен данными, которые можно отправить через Интернет. </span><span class="sxs-lookup"><span data-stu-id="1923e-127">Data migration is limited to what can be uploaded over the Internet.</span></span> 
    
- <span data-ttu-id="1923e-128">Настройки: приложения для Office и SharePoint, SharePoint Designer 2013. </span><span class="sxs-lookup"><span data-stu-id="1923e-128">Customizations: Apps for Office, SharePoint, and SharePoint Designer 2013.</span></span> 
    
#### <a name="hybrid-with-office-365"></a><span data-ttu-id="1923e-129">Гибридная среда с Office 365</span><span class="sxs-lookup"><span data-stu-id="1923e-129">Hybrid with Office 365</span></span>

<span data-ttu-id="1923e-130">Объедините преимущества Office 365 с локальным развертыванием SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="1923e-130">Combine the benefits of Office 365 with an on-premises deployment of SharePoint 2013.</span></span> 
  
<span data-ttu-id="1923e-131">На сопроводительной схеме показано Office 365 с SharePoint Online с помощью Business Connectivity Services (BCS) для подключения к локальной ферме SharePoint Server 2013.</span><span class="sxs-lookup"><span data-stu-id="1923e-131">The accompanying diagram shows Office 365 with SharePoint Online using Business Connectivity Services (BCS) to connect to an on-premises SharePoint Server 2013 farm.</span></span> 
  
<span data-ttu-id="1923e-132">Выберите функцию для интеграции из перечисленных ниже. </span><span class="sxs-lookup"><span data-stu-id="1923e-132">Choose which of the following features to integrate:</span></span> 
  
<span data-ttu-id="1923e-133">Поиск SharePoint</span><span class="sxs-lookup"><span data-stu-id="1923e-133">SharePoint Search</span></span> 
  
- <span data-ttu-id="1923e-134">Пользователи могут просматривать результаты поиска в обеих средах.  </span><span class="sxs-lookup"><span data-stu-id="1923e-134">Users can see search results from both environments.</span></span> 
    
- <span data-ttu-id="1923e-135">Пользователи экстрасети могут выполнять удаленный вход в локальную учетную запись Active Directory и пользоваться всеми доступными функциями гибридной среды. </span><span class="sxs-lookup"><span data-stu-id="1923e-135">Extranet users can remotely log on with an on-premises Active Directory account and use all available hybrid functionality.</span></span> 
    
<span data-ttu-id="1923e-136">BCS</span><span class="sxs-lookup"><span data-stu-id="1923e-136">BCS</span></span>
  
<span data-ttu-id="1923e-p101">Из SharePoint Online: пользователи могут выполнять операции чтения и записи. Служба BCS подключается к локальной ферме SharePoint Server 2013. Служба BCS, настроенная на локальной ферме, выступает в роли посредника соединения с конечными точками локальной службы OData.  </span><span class="sxs-lookup"><span data-stu-id="1923e-p101">From SharePoint Online: Users can perform both read and write operations. The BCS service connects to an on-premises SharePoint Server 2013 farm. The BCS service configured on the on-premises farm brokers the connection to on-premises OData Service endpoints.</span></span> 
  
<span data-ttu-id="1923e-140">Duet Enterprise Online</span><span class="sxs-lookup"><span data-stu-id="1923e-140">Duet Enterprise Online</span></span> 
  
<span data-ttu-id="1923e-141">Из SharePoint Online пользователи могут выполнять операции чтения и записи по отношению к локальной системе SAP. </span><span class="sxs-lookup"><span data-stu-id="1923e-141">From SharePoint Online, users can perform read and write operations against an on-premises SAP system.</span></span> 
  
#### <a name="azure"></a><span data-ttu-id="1923e-142">Azure</span><span class="sxs-lookup"><span data-stu-id="1923e-142">Azure</span></span>

<span data-ttu-id="1923e-143">Пользуйтесь облачными службами, сохраняя при этом полный контроль над платформой и компонентами.  </span><span class="sxs-lookup"><span data-stu-id="1923e-143">Take advantage of the cloud while maintaining full control of the platform and features.</span></span> 
  
<span data-ttu-id="1923e-144">На сопроводительной схеме показана служба Azure, которая содержит две облачные службы, ферму SharePoint 2013 и Windows Server Active Directory с DNS-подключением к пользователям через Интернет или подключением к локальной службе Active Directory через VPN-туннель.</span><span class="sxs-lookup"><span data-stu-id="1923e-144">The accompanying diagram shows Azure, which contains two cloud services, a SharePoint 2013 farm, and Windows Server Active Directory with DNS connecting to users over the Internet or connecting to on-premises Active Directory via VPN tunnel.</span></span> 
  
<span data-ttu-id="1923e-145">Поддерживаются перечисленные ниже возможности. </span><span class="sxs-lookup"><span data-stu-id="1923e-145">Features include:</span></span> 
  
-  <span data-ttu-id="1923e-146">Azure — это платформа, предоставляющая инфраструктуру и службы приложений, необходимые для размещения фермы SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="1923e-146">Azure is a platform that provides the infrastructure and app services needed to host a SharePoint 2013 farm.</span></span>
    
- <span data-ttu-id="1923e-147">Службы инфраструктуры.</span><span class="sxs-lookup"><span data-stu-id="1923e-147">Infrastructure Services.</span></span> 
    
- <span data-ttu-id="1923e-148">Лучшая собственная облачная платформа для SQL Server и SharePoint. </span><span class="sxs-lookup"><span data-stu-id="1923e-148">Best native cloud platform for SQL Server and SharePoint.</span></span> 
    
- <span data-ttu-id="1923e-149">Вычислительные ресурсы доступны практически сразу без каких-либо обязательств. </span><span class="sxs-lookup"><span data-stu-id="1923e-149">Computing resources are available almost immediately with no commitment.</span></span> 
    
- <span data-ttu-id="1923e-150">Сосредоточьтесь на приложениях, а не центрах обработки данных и инфраструктуре. </span><span class="sxs-lookup"><span data-stu-id="1923e-150">Focus on applications, instead of datacenters and infrastructure.</span></span> 
    
- <span data-ttu-id="1923e-151">Недорогие среды разработки и тестирования. </span><span class="sxs-lookup"><span data-stu-id="1923e-151">Inexpensive development and test environments.</span></span> 
    
- <span data-ttu-id="1923e-152">Решения SharePoint могут быть доступны из Интернета или только из корпоративной среды через VPN-туннель типа "сеть-сеть". </span><span class="sxs-lookup"><span data-stu-id="1923e-152">SharePoint solutions can be accessible from the Internet or accessible only from a corporate environment through a site-to-site VPN tunnel.</span></span> 
    
- <span data-ttu-id="1923e-153">Спектр настроек неограничен. </span><span class="sxs-lookup"><span data-stu-id="1923e-153">Customizations are not limited.</span></span> 
    
#### <a name="on-premises"></a><span data-ttu-id="1923e-154">Локальная среда</span><span class="sxs-lookup"><span data-stu-id="1923e-154">On premises</span></span>

<span data-ttu-id="1923e-155">Все под вашим контролем.  </span><span class="sxs-lookup"><span data-stu-id="1923e-155">You own everything.</span></span> 
  
<span data-ttu-id="1923e-156">На сопроводительной схеме показана локальная среда с веб-серверами, серверами приложений и службой Active Directory, которая обменивается контентом со всеми базами данных и серверами приложений, выделенными для поиска. </span><span class="sxs-lookup"><span data-stu-id="1923e-156">The accompanying diagram shows an on-premises environment with web servers, application servers, and Active Directory communicating with all databases and dedicated application servers for search.</span></span> 
  
<span data-ttu-id="1923e-157">Поддерживаются перечисленные ниже возможности. </span><span class="sxs-lookup"><span data-stu-id="1923e-157">Features include:</span></span> 
  
- <span data-ttu-id="1923e-158">Планирование загрузки и определение конфигурации оборудования.</span><span class="sxs-lookup"><span data-stu-id="1923e-158">Capacity planning and sizing.</span></span> 
    
- <span data-ttu-id="1923e-159">Приобретение и настройка серверов. </span><span class="sxs-lookup"><span data-stu-id="1923e-159">Server acquisition and setup.</span></span> 
    
- <span data-ttu-id="1923e-160">Развертывание.</span><span class="sxs-lookup"><span data-stu-id="1923e-160">Deployment.</span></span> 
    
- <span data-ttu-id="1923e-161">Горизонтальное масштабирование, применение исправлений и эксплуатация.  </span><span class="sxs-lookup"><span data-stu-id="1923e-161">Scaling out, patching, and operations.</span></span> 
    
- <span data-ttu-id="1923e-162">Резервное копирование данных.</span><span class="sxs-lookup"><span data-stu-id="1923e-162">Backing up data.</span></span> 
    
- <span data-ttu-id="1923e-163">Поддержка среды аварийного восстановления.  </span><span class="sxs-lookup"><span data-stu-id="1923e-163">Maintaining a disaster recovery environment.</span></span> 
    
- <span data-ttu-id="1923e-164">Спектр настроек неограничен. </span><span class="sxs-lookup"><span data-stu-id="1923e-164">Customizations are not limited.</span></span> 
    
### <a name="deployment-type-is-best-for---"></a><span data-ttu-id="1923e-p102">Тип развертывания лучше всего подходит для...</span><span class="sxs-lookup"><span data-stu-id="1923e-p102">Deployment type is best for . . .</span></span>

#### <a name="sharepoint-2013-in-office-365"></a><span data-ttu-id="1923e-168">SharePoint 2013 в Office 365</span><span class="sxs-lookup"><span data-stu-id="1923e-168">SharePoint 2013 in Office 365</span></span>

- <span data-ttu-id="1923e-p103">Безопасный обмен данными и совместная работа. (Уникальная функция!) </span><span class="sxs-lookup"><span data-stu-id="1923e-p103">Secure external sharing and collaboration. (Unique feature!)</span></span> 
    
- <span data-ttu-id="1923e-171">Интрасеть — сайты группы, личные сайты и внутренняя совместная работа. </span><span class="sxs-lookup"><span data-stu-id="1923e-171">Intranet — Team sites, My Sites, and internal collaboration.</span></span> 
    
- <span data-ttu-id="1923e-172">Хранение документов и управление их версиями в облаке. </span><span class="sxs-lookup"><span data-stu-id="1923e-172">Document storage and versioning in the cloud.</span></span> 
    
- <span data-ttu-id="1923e-173">Простой общедоступный веб-сайт. </span><span class="sxs-lookup"><span data-stu-id="1923e-173">Basic public-facing website.</span></span> 
    
<span data-ttu-id="1923e-174">Дополнительные функции для специализированных планов подписки на Office 365:</span><span class="sxs-lookup"><span data-stu-id="1923e-174">Additional features with Office 365 Dedicated subscription plans:</span></span> 
  
- <span data-ttu-id="1923e-175">Оборудование центра обработки данных Майкрософт, которое предназначено специально для вашей организации и не используется совместно с другими компаниями.  </span><span class="sxs-lookup"><span data-stu-id="1923e-175">Microsoft datacenter equipment that is dedicated to your organization and not shared with any other organization.</span></span> 
    
- <span data-ttu-id="1923e-176">Среда каждого заказчика размещается в физически отдельной сети. </span><span class="sxs-lookup"><span data-stu-id="1923e-176">Each customer environment resides in a physically separate network.</span></span> 
    
- <span data-ttu-id="1923e-p104">Связь с клиентом осуществляется в виртуальной частной сети, защищенной IPsec, или через частное подключение заказчика. Двухфакторная проверка подлинности необязательна. </span><span class="sxs-lookup"><span data-stu-id="1923e-p104">Client communication across an IPSec-secured VPN or customer-owned private connection. Two-factor authentication is optional.</span></span> 
    
- <span data-ttu-id="1923e-179">Планы, соответствующие международным правилам торговли оружием (ITAR). </span><span class="sxs-lookup"><span data-stu-id="1923e-179">ITAR-support plans.</span></span> 
    
#### <a name="hybrid-with-office-365"></a><span data-ttu-id="1923e-180">Гибридная среда с Office 365</span><span class="sxs-lookup"><span data-stu-id="1923e-180">Hybrid with Office 365</span></span>

- <span data-ttu-id="1923e-181">Используйте Office 365 для внешнего общего доступа и совместной работы, а не для настройки среды экстрасети.</span><span class="sxs-lookup"><span data-stu-id="1923e-181">Use Office 365 for external sharing and collaboration instead of setting up an extranet environment.</span></span> 
    
- <span data-ttu-id="1923e-182">Возможность перемещения личных сайтов (OneDrive для бизнеса) в облако упрощает удаленный доступ пользователей к своим файлам.  </span><span class="sxs-lookup"><span data-stu-id="1923e-182">Move My Sites (OneDrive for Business) to the cloud to make it easier for users to access their files remotely.</span></span> 
    
- <span data-ttu-id="1923e-183">Запустите новые сайты групп в Office 365.</span><span class="sxs-lookup"><span data-stu-id="1923e-183">Start new team sites in Office 365.</span></span> 
    
- <span data-ttu-id="1923e-184">Интеграция сайта Office 365 с локальной средой BCS SharePoint.</span><span class="sxs-lookup"><span data-stu-id="1923e-184">Integrate an Office 365 site with on-premises BCS SharePoint environment.</span></span> 
    
#### <a name="azure"></a><span data-ttu-id="1923e-185">Azure</span><span class="sxs-lookup"><span data-stu-id="1923e-185">Azure</span></span>

- <span data-ttu-id="1923e-186">SharePoint для веб-сайтов — общедоступные сайты.</span><span class="sxs-lookup"><span data-stu-id="1923e-186">SharePoint for Internet Sites — Public facing sites.</span></span> <span data-ttu-id="1923e-187">Воспользуйтесь преимуществами Azure AD для учетных записей клиентов и проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="1923e-187">Take advantage of Azure AD for customer accounts and authentication.</span></span> 
    
- <span data-ttu-id="1923e-188">Среды разработки и тестирования, а также промежуточные среды — быстрая подготовка и отзыв всех компонентов среды. </span><span class="sxs-lookup"><span data-stu-id="1923e-188">Developer, test, and staging environments — Quickly provision and deprovision entire environments.</span></span> 
    
- <span data-ttu-id="1923e-189">Гибридные приложения — приложения, охватывающие центр обработки данных и облако. </span><span class="sxs-lookup"><span data-stu-id="1923e-189">Hybrid applications — Applications that span your datacenter and the cloud.</span></span> 
    
- <span data-ttu-id="1923e-p106">Среда аварийного восстановления — быстрое восстановление системы после сбоев. Оплата только за использование. </span><span class="sxs-lookup"><span data-stu-id="1923e-p106">Disaster recovery environment — Quickly recover from a disaster. Pay only for use.</span></span> 
    
- <span data-ttu-id="1923e-192">Фермы, требующие подробной отчетности или аудита. </span><span class="sxs-lookup"><span data-stu-id="1923e-192">Farms that require deep reporting or auditing.</span></span> 
    
- <span data-ttu-id="1923e-193">Web Analytics.</span><span class="sxs-lookup"><span data-stu-id="1923e-193">Web analytics.</span></span> 
    
- <span data-ttu-id="1923e-194">Шифрование данных, не перемещающихся в сети (данные шифруются в базах данных SQL). </span><span class="sxs-lookup"><span data-stu-id="1923e-194">Data encryption at rest (data is encrypted in the SQL databases).</span></span> 
    
#### <a name="data-encryption-at-rest-data-is-encrypted-in-the-sql-databases"></a><span data-ttu-id="1923e-195">Шифрование данных, не перемещающихся в сети (данные шифруются в базах данных SQL):</span><span class="sxs-lookup"><span data-stu-id="1923e-195">Data encryption at rest (data is encrypted in the SQL databases)</span></span>

- <span data-ttu-id="1923e-196">для ферм внутри страны (когда данные должны находиться в пределах определенной юрисдикции); </span><span class="sxs-lookup"><span data-stu-id="1923e-196">In-country farms (when data is required to reside within a jurisdiction).</span></span> 
    
- <span data-ttu-id="1923e-197">для сложных решений бизнес-аналитики (BI), которые должны размещаться вблизи данных бизнес-аналитики; </span><span class="sxs-lookup"><span data-stu-id="1923e-197">Complex BI solutions that must reside close to BI data.</span></span> 
    
- <span data-ttu-id="1923e-198">для частных облачных решений; </span><span class="sxs-lookup"><span data-stu-id="1923e-198">Private cloud solutions.</span></span> 
    
- <span data-ttu-id="1923e-199">для решений с широкими возможностями настройки;</span><span class="sxs-lookup"><span data-stu-id="1923e-199">Highly customized solutions.</span></span> 
    
- <span data-ttu-id="1923e-200">Устаревшие решения со сторонними компонентами, которые зависят от аппаратного и программного обеспечения, которые не поддерживаются в службах инфраструктуры Azure.</span><span class="sxs-lookup"><span data-stu-id="1923e-200">Legacy solutions with third-party components that depend on hardware and software that are not supported on Azure Infrastructure Services.</span></span> 
    
- <span data-ttu-id="1923e-201">Ограничения конфиденциальности, которые предотвращают синхронизацию учетных записей Active Directory с Azure Active Directory (требование для Office 365).</span><span class="sxs-lookup"><span data-stu-id="1923e-201">Privacy restrictions that prevent synchronization of Active Directory accounts with Azure Active Directory (a requirement for Office 365).</span></span> 
    
- <span data-ttu-id="1923e-202">для организаций, которым необходим контроль над всей платформой и решением.</span><span class="sxs-lookup"><span data-stu-id="1923e-202">Organizations that prefer control of the entire platform and solution.</span></span> 
    
### <a name="license-requirements"></a><span data-ttu-id="1923e-203">Требования лицензирования</span><span class="sxs-lookup"><span data-stu-id="1923e-203">License requirements</span></span>

#### <a name="sharepoint-2013-in-office-365"></a><span data-ttu-id="1923e-204">SharePoint 2013 в Office 365</span><span class="sxs-lookup"><span data-stu-id="1923e-204">SharePoint 2013 in Office 365</span></span>

<span data-ttu-id="1923e-205">Модель с использованием подписки.</span><span class="sxs-lookup"><span data-stu-id="1923e-205">Subscription model.</span></span> <span data-ttu-id="1923e-206">Дополнительные лицензии не требуются.</span><span class="sxs-lookup"><span data-stu-id="1923e-206">No additional licenses needed.</span></span> 
  
#### <a name="hybrid-with-office-365"></a><span data-ttu-id="1923e-207">Гибридная среда с Office 365</span><span class="sxs-lookup"><span data-stu-id="1923e-207">Hybrid with Office 365</span></span>

- <span data-ttu-id="1923e-p108">Для Office 365: модель с использованием подписки. Дополнительные лицензии не требуются.</span><span class="sxs-lookup"><span data-stu-id="1923e-p108">Office 365 — Subscription model. No additional licenses needed.</span></span> 
    
- <span data-ttu-id="1923e-210">Для локальной среды: можно применять все локальные лицензии.</span><span class="sxs-lookup"><span data-stu-id="1923e-210">On-premises — All on-premises licenses apply.</span></span> 
    
#### <a name="azure"></a><span data-ttu-id="1923e-211">Azure</span><span class="sxs-lookup"><span data-stu-id="1923e-211">Azure</span></span>

-  <span data-ttu-id="1923e-212">Подписка на Azure (включая операционную систему сервера)</span><span class="sxs-lookup"><span data-stu-id="1923e-212">Azure subscription (includes the server operating system)</span></span>
    
- <span data-ttu-id="1923e-213">SQL Server</span><span class="sxs-lookup"><span data-stu-id="1923e-213">SQL Server</span></span> 
    
- <span data-ttu-id="1923e-214">Лицензия на сервер SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="1923e-214">SharePoint 2013 Server License</span></span> 
    
- <span data-ttu-id="1923e-215">Клиентская лицензия на SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="1923e-215">SharePoint 2013 Client Access License</span></span> 
    
#### <a name="on-premises"></a><span data-ttu-id="1923e-216">Локальная среда</span><span class="sxs-lookup"><span data-stu-id="1923e-216">On premises</span></span>

- <span data-ttu-id="1923e-217">Серверная операционная система</span><span class="sxs-lookup"><span data-stu-id="1923e-217">Server operating system</span></span> 
    
- <span data-ttu-id="1923e-218">SQL Server</span><span class="sxs-lookup"><span data-stu-id="1923e-218">SQL Server</span></span> 
    
- <span data-ttu-id="1923e-219">Лицензия на сервер SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="1923e-219">SharePoint 2013 Server License</span></span> 
    
- <span data-ttu-id="1923e-220">Клиентская лицензия на SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="1923e-220">SharePoint 2013 Client Access License</span></span> 
    
### <a name="architecture-tasks"></a><span data-ttu-id="1923e-221">Архитектурные задачи</span><span class="sxs-lookup"><span data-stu-id="1923e-221">Architecture tasks</span></span>

#### <a name="sharepoint-2013-in-office-365"></a><span data-ttu-id="1923e-222">SharePoint 2013 в Office 365</span><span class="sxs-lookup"><span data-stu-id="1923e-222">SharePoint 2013 in Office 365</span></span>

- <span data-ttu-id="1923e-223">Планирование и проектирование интеграции каталогов.</span><span class="sxs-lookup"><span data-stu-id="1923e-223">Plan and design directory integration.</span></span> <span data-ttu-id="1923e-224">Два варианта.</span><span class="sxs-lookup"><span data-stu-id="1923e-224">Two options.</span></span> <span data-ttu-id="1923e-225">Любой из этих вариантов можно развертывать в локальной среде или в Azure: Синхронизация паролей (требуется 1 64-разрядный сервер).</span><span class="sxs-lookup"><span data-stu-id="1923e-225">Either option can be deployed on premises or in Azure: Password sync (requires one 64-bit server).</span></span> <span data-ttu-id="1923e-226">SSO (требуется AD FS и несколько серверов).</span><span class="sxs-lookup"><span data-stu-id="1923e-226">SSO (requires AD FS and multiple servers).</span></span> 
    
- <span data-ttu-id="1923e-227">Обеспечение доступности и достаточной пропускной способности сети при использовании брандмауэров, прокси-серверов, шлюзов и каналов глобальной сети.</span><span class="sxs-lookup"><span data-stu-id="1923e-227">Ensure network capacity and availability through firewalls, proxy servers, gateways, and across WAN links.</span></span> 
    
- <span data-ttu-id="1923e-228">Получение сторонних SSL-сертификатов для обеспечения безопасности на корпоративном уровне для служб Office 365.</span><span class="sxs-lookup"><span data-stu-id="1923e-228">Acquire third-party SSL certificates to provide enterprise-security for Office 365 service offerings.</span></span> 
    
- <span data-ttu-id="1923e-229">Планирование имени клиента, моделирование архитектуры семейства веб-сайтов и управления. </span><span class="sxs-lookup"><span data-stu-id="1923e-229">Plan the tenant name, and design the site collection architecture and governance.</span></span> 
    
- <span data-ttu-id="1923e-230">Планирование настроек, решений и приложений для SharePoint Online. </span><span class="sxs-lookup"><span data-stu-id="1923e-230">Plan customizations, solutions, and apps for SharePoint Online.</span></span> 
    
- <span data-ttu-id="1923e-231">Решите, следует ли подключаться к Office 365 с помощью протокола IP 6 (IPv6).</span><span class="sxs-lookup"><span data-stu-id="1923e-231">Decide if you want to connect to Office 365 by using the Internet Protocol 6 (IPv6).</span></span> <span data-ttu-id="1923e-232">Это нетипичный сценарий.</span><span class="sxs-lookup"><span data-stu-id="1923e-232">This is not common.</span></span> 
    
#### <a name="hybrid-with-office-365"></a><span data-ttu-id="1923e-233">Гибридная среда с Office 365</span><span class="sxs-lookup"><span data-stu-id="1923e-233">Hybrid with Office 365</span></span>

<span data-ttu-id="1923e-234">В дополнение к задачам для Office 365 и локальных сред:</span><span class="sxs-lookup"><span data-stu-id="1923e-234">In addition to tasks for both the Office 365 and on-premises environments:</span></span> 
  
- <span data-ttu-id="1923e-p111">Определите необходимую степень интеграции и выберите гибридную топологию. См. плакат этой модели: "Какую гибридную топологию следует использовать?". </span><span class="sxs-lookup"><span data-stu-id="1923e-p111">Determine how much feature integration you want and choose the hybrid topology. See this model poster: Which hybrid topology should I use?</span></span> 
    
- <span data-ttu-id="1923e-237">При необходимости определите, какое устройство прокси-сервера будет использоваться. </span><span class="sxs-lookup"><span data-stu-id="1923e-237">If required, determine which proxy server device will be used.</span></span> 
    
#### <a name="azure"></a><span data-ttu-id="1923e-238">Azure</span><span class="sxs-lookup"><span data-stu-id="1923e-238">Azure</span></span>

<span data-ttu-id="1923e-239">Проектирование сетевой среды Azure:</span><span class="sxs-lookup"><span data-stu-id="1923e-239">Design the Azure network environment:</span></span> 
  
- <span data-ttu-id="1923e-240">Виртуальная сеть в Azure, включая подсети.</span><span class="sxs-lookup"><span data-stu-id="1923e-240">Virtual network within Azure, including subnets.</span></span> 
    
- <span data-ttu-id="1923e-241">Доменная среда и интеграция с локальными серверами. </span><span class="sxs-lookup"><span data-stu-id="1923e-241">Domain environment and integration with on-premises servers.</span></span> 
    
- <span data-ttu-id="1923e-242">IP-адреса и DNS. </span><span class="sxs-lookup"><span data-stu-id="1923e-242">IP addresses and DNS.</span></span> 
    
- <span data-ttu-id="1923e-243">Территориальные группы и учетные записи хранения. </span><span class="sxs-lookup"><span data-stu-id="1923e-243">Affinity groups and storage accounts.</span></span> 
    
<span data-ttu-id="1923e-244">Проектирование среды SharePoint в Azure:</span><span class="sxs-lookup"><span data-stu-id="1923e-244">Design the SharePoint environment in Azure:</span></span> 
  
- <span data-ttu-id="1923e-245">Топология и логическая архитектура ферм SharePoint. </span><span class="sxs-lookup"><span data-stu-id="1923e-245">SharePoint farm topology and logical architecture.</span></span> 
    
-  <span data-ttu-id="1923e-246">Наборы доступности Azure и домены обновления.</span><span class="sxs-lookup"><span data-stu-id="1923e-246">Azure availability sets and update domains.</span></span>
    
- <span data-ttu-id="1923e-247">Размеры виртуальных машин.  </span><span class="sxs-lookup"><span data-stu-id="1923e-247">Virtual machines sizes.</span></span> 
    
- <span data-ttu-id="1923e-248">Конечная точка с распределенной нагрузкой. </span><span class="sxs-lookup"><span data-stu-id="1923e-248">Load balanced endpoint.</span></span> 
    
- <span data-ttu-id="1923e-249">Внешние конечные точки для общего доступа (при необходимости).  </span><span class="sxs-lookup"><span data-stu-id="1923e-249">External endpoints for public access, if that is preferable.</span></span> 
    
- <span data-ttu-id="1923e-250">Среда аварийного восстановления. </span><span class="sxs-lookup"><span data-stu-id="1923e-250">Disaster recovery environment.</span></span> 
    
#### <a name="on-premises"></a><span data-ttu-id="1923e-251">Локальная среда</span><span class="sxs-lookup"><span data-stu-id="1923e-251">On premises</span></span>

<span data-ttu-id="1923e-252">Разработка среды SharePoint в существующей локальной среде </span><span class="sxs-lookup"><span data-stu-id="1923e-252">Design the SharePoint environment in an existing on-premises environment:</span></span> 
  
- <span data-ttu-id="1923e-253">Топология и логическая архитектура ферм SharePoint. </span><span class="sxs-lookup"><span data-stu-id="1923e-253">SharePoint farm topology and logical architecture.</span></span> 
    
- <span data-ttu-id="1923e-254">Серверное оборудование.</span><span class="sxs-lookup"><span data-stu-id="1923e-254">Server hardware.</span></span> 
    
- <span data-ttu-id="1923e-255">Виртуальная среда, если она используется. </span><span class="sxs-lookup"><span data-stu-id="1923e-255">Virtual environment, if used.</span></span> 
    
- <span data-ttu-id="1923e-256">Балансировка нагрузки.</span><span class="sxs-lookup"><span data-stu-id="1923e-256">Load balancing.</span></span> 
    
- <span data-ttu-id="1923e-257">Интеграция с доменными службами Active Directory и DNS.  </span><span class="sxs-lookup"><span data-stu-id="1923e-257">Integration with AD DS and DNS.</span></span> 
    
- <span data-ttu-id="1923e-258">Среда аварийного восстановления. </span><span class="sxs-lookup"><span data-stu-id="1923e-258">Disaster recovery environment.</span></span> 
    
### <a name="it-pro-responsibilities"></a><span data-ttu-id="1923e-259">Обязанности ИТ-специалистов</span><span class="sxs-lookup"><span data-stu-id="1923e-259">IT pro responsibilities</span></span>

#### <a name="sharepoint-2013-in-office-365"></a><span data-ttu-id="1923e-260">SharePoint 2013 в Office 365</span><span class="sxs-lookup"><span data-stu-id="1923e-260">SharePoint 2013 in Office 365</span></span>

- <span data-ttu-id="1923e-261">Убедитесь, что рабочие станции пользователей отвечают требованиям Office 365 клиента.</span><span class="sxs-lookup"><span data-stu-id="1923e-261">Ensure user workstations meet Office 365 client prerequisites.</span></span> 
    
- <span data-ttu-id="1923e-262">Реализация плана интеграции каталогов.</span><span class="sxs-lookup"><span data-stu-id="1923e-262">Implement the directory integration plan.</span></span> 
    
- <span data-ttu-id="1923e-263">Планирование внутренних и внешних записей DNS и маршрутизации.</span><span class="sxs-lookup"><span data-stu-id="1923e-263">Plan and implement internal and external DNS records and routing.</span></span> 
    
- <span data-ttu-id="1923e-264">Настройте прокси-сервер или брандмауэр для Office 365, а также требования к URL-адресу.</span><span class="sxs-lookup"><span data-stu-id="1923e-264">Configure the proxy or firewall for Office 365 IP address and URL requirements.</span></span> 
    
- <span data-ttu-id="1923e-265">Создание семейств веб-сайтов и назначение им разрешений. </span><span class="sxs-lookup"><span data-stu-id="1923e-265">Create and assign permissions to site collections.</span></span> 
    
- <span data-ttu-id="1923e-266">Внедрение настроек, решений и приложений для SharePoint Online. </span><span class="sxs-lookup"><span data-stu-id="1923e-266">Implement customizations, solutions, and apps for SharePoint Online.</span></span> 
    
- <span data-ttu-id="1923e-267">Контроль доступности сети и поиск возможных причин снижения производительности. </span><span class="sxs-lookup"><span data-stu-id="1923e-267">Monitor network availability and identify possible bottlenecks.</span></span> 
    
#### <a name="hybrid-with-office-365"></a><span data-ttu-id="1923e-268">Гибридная среда с Office 365</span><span class="sxs-lookup"><span data-stu-id="1923e-268">Hybrid with Office 365</span></span>

<span data-ttu-id="1923e-269">В дополнение к задачам для Office 365 и локальных сред:</span><span class="sxs-lookup"><span data-stu-id="1923e-269">In addition to tasks for both the Office 365 and on-premises environments:</span></span> 
  
- <span data-ttu-id="1923e-270">Настроить устройства прокси-сервера (при необходимости).</span><span class="sxs-lookup"><span data-stu-id="1923e-270">Configure the proxy server device, if required.</span></span> 
    
- <span data-ttu-id="1923e-271">Настроить гибридную инфраструктуру управления удостоверениями: проверку подлинности между двумя средами в режиме единого входа и между серверами. </span><span class="sxs-lookup"><span data-stu-id="1923e-271">Configure the hybrid identity management infrastructure: SSO and server-to-server authentication between the two environments.</span></span> 
    
- <span data-ttu-id="1923e-272">Настроить интеграцию выбранных компонентов: поиск, BCS, Duet Enterprise Online. </span><span class="sxs-lookup"><span data-stu-id="1923e-272">Configure the integration of chosen features: Search, BCS, Duet Enterprise Online.</span></span> 
    
#### <a name="azure"></a><span data-ttu-id="1923e-273">Azure</span><span class="sxs-lookup"><span data-stu-id="1923e-273">Azure</span></span>

<span data-ttu-id="1923e-274">Развертывание и управление средой Azure и SharePoint:</span><span class="sxs-lookup"><span data-stu-id="1923e-274">Deploy and manage the Azure and SharePoint environment:</span></span> 
  
- <span data-ttu-id="1923e-275">Реализация и управление сетевой средой Azure;</span><span class="sxs-lookup"><span data-stu-id="1923e-275">Implement and manage the Azure network environment.</span></span> 
    
- <span data-ttu-id="1923e-276">Развертывание среды SharePoint.</span><span class="sxs-lookup"><span data-stu-id="1923e-276">Deploy the SharePoint environment.</span></span> 
    
- <span data-ttu-id="1923e-277">Обновление серверов фермы SharePoint. </span><span class="sxs-lookup"><span data-stu-id="1923e-277">Update SharePoint farm servers.</span></span> 
    
- <span data-ttu-id="1923e-278">Добавление и отключение виртуальных машин по мере необходимости в зависимости от уровня использования фермы. </span><span class="sxs-lookup"><span data-stu-id="1923e-278">Add or shut down virtual machines as needed based on farm utilization.</span></span> 
    
- <span data-ttu-id="1923e-279">При необходимости размеры виртуальных машин можно увеличивать и уменьшать. </span><span class="sxs-lookup"><span data-stu-id="1923e-279">Increase or decrease virtual machine sizes, as needed.</span></span> 
    
- <span data-ttu-id="1923e-280">Резервное копирование среды SharePoint.</span><span class="sxs-lookup"><span data-stu-id="1923e-280">Back up the SharePoint environment.</span></span> 
    
- <span data-ttu-id="1923e-281">Реализация среды аварийного восстановления и протокола. </span><span class="sxs-lookup"><span data-stu-id="1923e-281">Implement the disaster recovery environment and protocol.</span></span> 
    
#### <a name="on-premises"></a><span data-ttu-id="1923e-282">Локальная среда</span><span class="sxs-lookup"><span data-stu-id="1923e-282">On premises</span></span>

<span data-ttu-id="1923e-283">Развертывание локальной среды SharePoint и управление ею </span><span class="sxs-lookup"><span data-stu-id="1923e-283">Deploy and manage the SharePoint on premises environment:</span></span> 
  
- <span data-ttu-id="1923e-284">Подготовка серверов к работе.</span><span class="sxs-lookup"><span data-stu-id="1923e-284">Provision servers.</span></span> 
    
- <span data-ttu-id="1923e-285">Развертывание среды SharePoint.</span><span class="sxs-lookup"><span data-stu-id="1923e-285">Deploy the SharePoint environment.</span></span> 
    
- <span data-ttu-id="1923e-286">Обновление серверов фермы SharePoint. </span><span class="sxs-lookup"><span data-stu-id="1923e-286">Update SharePoint farm servers.</span></span> 
    
- <span data-ttu-id="1923e-287">Добавление серверов в ферму и их удаление по мере необходимости в зависимости от уровня использования фермы. </span><span class="sxs-lookup"><span data-stu-id="1923e-287">Add or remove farm servers as needed based on farm utilization.</span></span> 
    
- <span data-ttu-id="1923e-288">Резервное копирование среды SharePoint.</span><span class="sxs-lookup"><span data-stu-id="1923e-288">Back up the SharePoint environment.</span></span> 
    
- <span data-ttu-id="1923e-289">Реализация среды аварийного восстановления и протокола. </span><span class="sxs-lookup"><span data-stu-id="1923e-289">Implement the disaster recovery environment and protocol.</span></span> 
    
## <a name="three-typical-workloads-to-move-to-azure"></a><span data-ttu-id="1923e-290">Три типичных рабочих нагрузки для перемещения в Azure</span><span class="sxs-lookup"><span data-stu-id="1923e-290">Three typical workloads to move to Azure</span></span>

### <a name="office-365-plus-directory-components-in-azure"></a><span data-ttu-id="1923e-291">Office 365 Plus компоненты каталога в Azure</span><span class="sxs-lookup"><span data-stu-id="1923e-291">Office 365 plus Directory Components in Azure</span></span>

<span data-ttu-id="1923e-292">Развертывание компонентов интеграции каталогов Office 365 в Azure выполняется быстрее, так как он позволяет развертывать виртуальные машины по запросу.</span><span class="sxs-lookup"><span data-stu-id="1923e-292">Deploying Office 365 directory integration components in Azure is faster because it can deploy virtual machines on-demand.</span></span> 
  
#### <a name="directory-synchronization-server-only"></a><span data-ttu-id="1923e-293">Только сервер синхронизации службы каталогов</span><span class="sxs-lookup"><span data-stu-id="1923e-293">Directory synchronization server only</span></span>

<span data-ttu-id="1923e-294">Вместо того чтобы развертывать 64 – разрядный сервер синхронизации каталогов в локальной среде, необходимо подготовить виртуальную машину в Azure.</span><span class="sxs-lookup"><span data-stu-id="1923e-294">Instead of deploying the 64-bit directory synchronization server in your on-premises environment, provision a virtual machine in Azure instead.</span></span> 
  
<span data-ttu-id="1923e-295">На сопроводительной схеме показана среда SharePoint Online с клиентом Azure Active Directory, которая синхронизирует имена и пароли учетных записей между локальной средой Active Directory и клиентом Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="1923e-295">The accompanying diagram shows SharePoint Online with an Azure Active Directory tenant, which synchronizes account names and passwords between the on-premises Active Directory environment and the Azure Active Directory tenant.</span></span> 
  
#### <a name="directory-synchronization-plus-ad-fs"></a><span data-ttu-id="1923e-296">Синхронизация службы каталогов и службы AD FS</span><span class="sxs-lookup"><span data-stu-id="1923e-296">Directory synchronization plus AD FS</span></span>

<span data-ttu-id="1923e-297">Этот вариант позволяет поддерживать федеративные удостоверения Office 365, не добавляя оборудование в локальную инфраструктуру.</span><span class="sxs-lookup"><span data-stu-id="1923e-297">This option allows you to support Office 365 federated identities (SSO) without adding hardware to your on-premises infrastructure.</span></span> <span data-ttu-id="1923e-298">Кроме того, при использовании этого варианта обеспечивается устойчивость системы в случае недоступности локальной среды Active Directory.</span><span class="sxs-lookup"><span data-stu-id="1923e-298">It also provides resiliency if the on-premises Active Directory environment is unavailable.</span></span> 
  
- <span data-ttu-id="1923e-299">Компоненты интеграции каталогов хранятся в Azure.</span><span class="sxs-lookup"><span data-stu-id="1923e-299">Directory integration components reside in Azure.</span></span> 
    
- <span data-ttu-id="1923e-300">СЛУЖБЫ AD FS публикуются в Интернете через прокси-серверы AD FS в Azure.</span><span class="sxs-lookup"><span data-stu-id="1923e-300">AD FS is published to the Internet through AD FS proxies in Azure.</span></span> 
    
- <span data-ttu-id="1923e-301">Трафик проверки подлинности клиента для пользователей, подключающихся из любого расположения, обрабатывается серверами AD FS и прокси-серверами, развернутыми в Azure.</span><span class="sxs-lookup"><span data-stu-id="1923e-301">Client authentication traffic, for users that are connecting from any location, is handled by AD FS servers and proxies that are deployed on Azure.</span></span> 
    
### <a name="public-facing-internet-site-and-azure-ad-for-customer-authentication"></a><span data-ttu-id="1923e-302">Общедоступный Интернет-сайт и Azure AD для проверки подлинности клиентов</span><span class="sxs-lookup"><span data-stu-id="1923e-302">Public-facing Internet site and Azure AD for customer authentication</span></span>

<span data-ttu-id="1923e-303">Воспользуйтесь возможностью легко масштабироваться по запросу, разместив сайт Интернета в Azure.</span><span class="sxs-lookup"><span data-stu-id="1923e-303">Take advantage of the ability to easily scale to demand by placing your Internet site in Azure.</span></span> <span data-ttu-id="1923e-304">Используйте Azure AD для хранения учетных записей клиентов.</span><span class="sxs-lookup"><span data-stu-id="1923e-304">Use Azure AD to store customer accounts.</span></span> 
  
#### <a name="azure-advantages-for-internet-sites"></a><span data-ttu-id="1923e-305">Преимущества Azure для Интернет-сайтов</span><span class="sxs-lookup"><span data-stu-id="1923e-305">Azure advantages for Internet sites</span></span>

- <span data-ttu-id="1923e-306">Вы платите только за необходимые ресурсы, изменяя количество виртуальных машин в зависимости от того, насколько интенсивно используется ферма. </span><span class="sxs-lookup"><span data-stu-id="1923e-306">Pay only for the resources you need by scaling the number of virtual machines based on farm utilization.</span></span> 
    
- <span data-ttu-id="1923e-307">Вы можете добавить подробную отчетность и веб-аналитику.</span><span class="sxs-lookup"><span data-stu-id="1923e-307">Add deep reporting and web analytics.</span></span> 
    
- <span data-ttu-id="1923e-308">Вы можете сосредоточиться на разработке хорошего сайта, а не создании инфраструктуры.</span><span class="sxs-lookup"><span data-stu-id="1923e-308">Focus on developing a great site rather than building infrastructure.</span></span> 
    
#### <a name="azure-ad"></a><span data-ttu-id="1923e-309">Azure AD</span><span class="sxs-lookup"><span data-stu-id="1923e-309">Azure AD</span></span>

<span data-ttu-id="1923e-310">Azure AD предоставляет возможности управления удостоверениями и управления доступом для облачных служб.</span><span class="sxs-lookup"><span data-stu-id="1923e-310">Azure AD provides identity management and access control capabilities for cloud services.</span></span> <span data-ttu-id="1923e-311">Возможности включают облачное хранилище для данных каталога и основной набор служб удостоверений, в том числе процессы входа пользователей, службы проверки подлинности и службы федерации Active Directory.</span><span class="sxs-lookup"><span data-stu-id="1923e-311">Capabilities include a cloud-based store for directory data and a core set of identity services, including user logon processes, authentication services, and AD FS.</span></span> <span data-ttu-id="1923e-312">Службы удостоверений, включенные в Azure AD, легко интегрируются с локальными развертываниями Active Directory и полностью поддерживают сторонние поставщики удостоверений.</span><span class="sxs-lookup"><span data-stu-id="1923e-312">The identity services that are included with Azure AD easily integrate with your on-premises Active Directory deployments and fully support third-party identity providers.</span></span> 
  
<span data-ttu-id="1923e-313">На сопроводительной схеме показана конфигурация зон и проверки подлинности, важная для общедоступных веб-сайтов.</span><span class="sxs-lookup"><span data-stu-id="1923e-313">The accompanying diagram shows the configuration of zones and authentication that is important for Internet-facing sites.</span></span> <span data-ttu-id="1923e-314">На схеме показан клиент Azure Active Directory, который содержит ферму SharePoint в Azure с двумя зонами:</span><span class="sxs-lookup"><span data-stu-id="1923e-314">The diagram shows the Azure Active Directory Tenant, which contains a SharePoint Farm on Azure with two zones:</span></span> 
  
- <span data-ttu-id="1923e-315">зоной Интернета, взаимодействующей с анонимными и прошедшими проверку подлинности пользователями и клиентами, которые не входят в сеть; </span><span class="sxs-lookup"><span data-stu-id="1923e-315">An Internet zone that interacts with Anonymous and Authenticated visitors and customers outside the network</span></span> 
    
- <span data-ttu-id="1923e-316">зоной по умолчанию зоны, которая содержит NTLM для обхода контента и проверки подлинности Windows, а также взаимодействует с локальным развертыванием Active Directory через VPN-туннель.  </span><span class="sxs-lookup"><span data-stu-id="1923e-316">A default zone that contains NTLM for Crawl and Windows Authentication that interacts with your on-premises Active Directory deployment over a VPN tunnel.</span></span> 
    
### <a name="on-premises-farm-plus-disaster-recovery-in-azure"></a><span data-ttu-id="1923e-317">Локальная ферма и аварийное восстановление в Azure</span><span class="sxs-lookup"><span data-stu-id="1923e-317">On-premises Farm plus Disaster Recovery in Azure</span></span>

<span data-ttu-id="1923e-318">Выберите вариант аварийного восстановления, который соответствует требованиям вашей компании.</span><span class="sxs-lookup"><span data-stu-id="1923e-318">Choose a disaster recovery option that matches your business requirements.</span></span> <span data-ttu-id="1923e-319">Azure предоставляет варианты уровня ввода для компаний, которые приступит к работе с аварийным восстановлением и дополнительными возможностями для предприятий с высокими требованиями к устойчивости.</span><span class="sxs-lookup"><span data-stu-id="1923e-319">Azure provides entry-level options for companies getting started with disaster recovery and advanced options for enterprises with high resiliency requirements.</span></span> 
  
#### <a name="cold-standby"></a><span data-ttu-id="1923e-320">Холодное резервирование</span><span class="sxs-lookup"><span data-stu-id="1923e-320">Cold standby</span></span>

- <span data-ttu-id="1923e-321">Ферма создается в полном масштабе, но виртуальные машины останавливаются.</span><span class="sxs-lookup"><span data-stu-id="1923e-321">The farm is fully built, but the virtual machines are stopped.</span></span> <span data-ttu-id="1923e-322">(Вы оплачиваете только при выполнении!)</span><span class="sxs-lookup"><span data-stu-id="1923e-322">(You're paying only when they're running!)</span></span> 
    
- <span data-ttu-id="1923e-323">Обслуживание среды включает запуск виртуальных машин по мере необходимости, а также исправление, обновление и проверку среды.</span><span class="sxs-lookup"><span data-stu-id="1923e-323">Maintaining the environment includes starting the virtual machines from time-to-time, patching, updating, and verifying the environment.</span></span> 
    
- <span data-ttu-id="1923e-324">Полный запуск среды в случае сбоя.</span><span class="sxs-lookup"><span data-stu-id="1923e-324">Start the full environment in the event of a disaster.</span></span> 
    
#### <a name="warm-standby"></a><span data-ttu-id="1923e-325">Резервный сервер</span><span class="sxs-lookup"><span data-stu-id="1923e-325">Warm standby</span></span>

- <span data-ttu-id="1923e-326">Включает небольшую ферму, которая уже подготовлена к работе и запущена.  </span><span class="sxs-lookup"><span data-stu-id="1923e-326">This includes a small farm that is provisioned and running.</span></span> 
    
- <span data-ttu-id="1923e-327">При отработке отказа эта ферма может мгновенно обеспечить обслуживание пользователей.  </span><span class="sxs-lookup"><span data-stu-id="1923e-327">The farm can immediately serve users in the event of a failover.</span></span> 
    
- <span data-ttu-id="1923e-328">Быстрое масштабирование фермы для обслуживания всех пользователей. </span><span class="sxs-lookup"><span data-stu-id="1923e-328">Scale out the farm quickly to serve the full user base.</span></span> 
    
#### <a name="hot-standby"></a><span data-ttu-id="1923e-329">Сервер горячей замены</span><span class="sxs-lookup"><span data-stu-id="1923e-329">Hot standby</span></span>

<span data-ttu-id="1923e-330">Полноразмерная ферма подготавливается к работе и запускается в ждущем режиме.</span><span class="sxs-lookup"><span data-stu-id="1923e-330">A fully-sized farm is provisioned and running on standby.</span></span> 
  
<span data-ttu-id="1923e-331">На сопроводительной схеме показана локальная ферма, которая взаимодействует с средой аварийного восстановления SharePoint в Azure.</span><span class="sxs-lookup"><span data-stu-id="1923e-331">The accompanying diagram shows an on-premises farm interacting with the SharePoint Disaster Recovery Environment on Azure.</span></span> <span data-ttu-id="1923e-332">Локальные базы данных используют доставку журналов SQL Server через VPN-туннель для доступа к среде аварийного восстановления SharePoint, включающей два сервера баз данных SQL, которые содержат базы данных SharePoint, два веб-сервера переднего плана и два сервера приложений SharePoint.</span><span class="sxs-lookup"><span data-stu-id="1923e-332">The on-premises databases use SQL Server Log Shipping over the VPN tunnel to access the SharePoint Disaster Recovery environment, which includes two SQL database servers that contain the SharePoint databases, two Web Front End servers, and two SharePoint Application servers.</span></span> 
  

