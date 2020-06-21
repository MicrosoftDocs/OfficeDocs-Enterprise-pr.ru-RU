---
title: Подписки, лицензии, учетные записи и клиенты для облачных предложений корпорации Майкрософт
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/08/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Ent_Architecture
ms.assetid: c720cffc-f9b5-4f43-9100-422f86a1027c
description: Сводка. Общие сведения о связи между организациями, подписками, лицензиями, учетными записями пользователей и клиентами в облачных предложениях корпорации Майкрософт.
ms.openlocfilehash: ad4307b2725fa37f6b28540b92895fc78f097c6c
ms.sourcegitcommit: c112869b3ecc0f574b7054ee1edc8c57132f8237
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2020
ms.locfileid: "44735967"
---
# <a name="subscriptions-licenses-accounts-and-tenants-for-microsofts-cloud-offerings"></a><span data-ttu-id="1979b-103">Подписки, лицензии, учетные записи и клиенты для облачных предложений корпорации Майкрософт</span><span class="sxs-lookup"><span data-stu-id="1979b-103">Subscriptions, licenses, accounts, and tenants for Microsoft's cloud offerings</span></span>

 <span data-ttu-id="1979b-104">**Сводка.** Общие сведения о связи между организациями, подписками, лицензиями, учетными записями пользователей и клиентами в облачных предложениях корпорации Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="1979b-104">**Summary:** Understand the relationships of organizations, subscriptions, licenses, user accounts, and tenants across Microsoft's cloud offerings.</span></span>
  
<span data-ttu-id="1979b-105">Для облачных решений Майкрософт предусмотрена иерархия организаций, подписок, лицензий и учетных записей пользователей. Это обеспечивает согласованное использование удостоверений и выставление счетов.</span><span class="sxs-lookup"><span data-stu-id="1979b-105">Microsoft provides a hierarchy of organizations, subscriptions, licenses, and user accounts for consistent use of identities and billing across its cloud offerings:</span></span>
  
- <span data-ttu-id="1979b-106">Microsoft Office 365</span><span class="sxs-lookup"><span data-stu-id="1979b-106">Microsoft Office 365</span></span>
- <span data-ttu-id="1979b-107">Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="1979b-107">Microsoft Azure</span></span>
- <span data-ttu-id="1979b-108">Microsoft Intune и Enterprise Mobility + Security (EMS)</span><span class="sxs-lookup"><span data-stu-id="1979b-108">Microsoft Intune and Enterprise Mobility + Security (EMS)</span></span>
- <span data-ttu-id="1979b-109">Microsoft Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="1979b-109">Microsoft Dynamics 365</span></span>

<span data-ttu-id="1979b-110">[Microsoft 365](https://docs.microsoft.com/microsoft-365/) объединяет Office 365, EMS и Windows 10 Корпоративная в одну подписку и набор интегрированных служб.</span><span class="sxs-lookup"><span data-stu-id="1979b-110">[Microsoft 365](https://docs.microsoft.com/microsoft-365/) combines Office 365, EMS, and Windows 10 Enterprise into a single subscription and set of integrated services.</span></span>

## <a name="elements-of-the-hierarchy"></a><span data-ttu-id="1979b-111">Элементы иерархии</span><span class="sxs-lookup"><span data-stu-id="1979b-111">Elements of the hierarchy</span></span>

<span data-ttu-id="1979b-112">Ниже перечислены элементы иерархии.</span><span class="sxs-lookup"><span data-stu-id="1979b-112">Here are the elements of the hierarchy:</span></span>
  
### <a name="organization"></a><span data-ttu-id="1979b-113">Организация</span><span class="sxs-lookup"><span data-stu-id="1979b-113">Organization</span></span>

<span data-ttu-id="1979b-114">An organization represents a business entity that is using Microsoft cloud offerings, typically identified by one or more public Domain Name System (DNS) domain names, such as contoso.com.</span><span class="sxs-lookup"><span data-stu-id="1979b-114">An organization represents a business entity that is using Microsoft cloud offerings, typically identified by one or more public Domain Name System (DNS) domain names, such as contoso.com.</span></span> <span data-ttu-id="1979b-115">The organization is a container for subscriptions.</span><span class="sxs-lookup"><span data-stu-id="1979b-115">The organization is a container for subscriptions.</span></span>
  
### <a name="subscriptions"></a><span data-ttu-id="1979b-116">Подписки</span><span class="sxs-lookup"><span data-stu-id="1979b-116">Subscriptions</span></span>

<span data-ttu-id="1979b-117">Подписка — это соглашение с корпорацией Майкрософт на использование одной или нескольких облачных платформ или служб Майкрософт, за которые взимается плата (по лицензиям отдельных пользователей или по использованию облачных ресурсов).</span><span class="sxs-lookup"><span data-stu-id="1979b-117">A subscription is an agreement with Microsoft to use one or more Microsoft cloud platforms or services, for which charges accrue based on either a per-user license fee or on cloud-based resource consumption.</span></span> 

- <span data-ttu-id="1979b-118">В облачных предложениях корпорации Майкрософт на основе SaaS (Office 365, Intune/EMS и Dynamics 365) оплата взимается за лицензии пользователей.</span><span class="sxs-lookup"><span data-stu-id="1979b-118">Microsoft's Software as a Service (SaaS)-based cloud offerings (Office 365, Intune/EMS, and Dynamics 365) charge per-user license fees.</span></span> 
- <span data-ttu-id="1979b-119">В облачных предложениях корпорации Майкрософт (Azure) на основе PaaS (платформа как услуга) и IaaS (инфраструктура как услуга) оплата взимается за использование облачных ресурсов.</span><span class="sxs-lookup"><span data-stu-id="1979b-119">Microsoft's Platform as a Service (PaaS) and Infrastructure as a Service (IaaS) cloud offerings (Azure) charge based on cloud resource consumption.</span></span>
 
<span data-ttu-id="1979b-120">You can also use a trial subscription, but the subscription expires after a specific amount of time or consumption charges.</span><span class="sxs-lookup"><span data-stu-id="1979b-120">You can also use a trial subscription, but the subscription expires after a specific amount of time or consumption charges.</span></span> <span data-ttu-id="1979b-121">You can convert a trial subscription to a paid subscription.</span><span class="sxs-lookup"><span data-stu-id="1979b-121">You can convert a trial subscription to a paid subscription.</span></span>
  
<span data-ttu-id="1979b-122">У организации может быть несколько подписок на облачные предложения корпорации Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="1979b-122">Organizations can have multiple subscriptions for Microsoft's cloud offerings.</span></span> <span data-ttu-id="1979b-123">На рисунке 1 показана одна организация с несколькими подписками на Office 365 и Azure, подпиской на Intune и подпиской на Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="1979b-123">Figure 1 shows a single organization that has multiple Office 365 subscriptions, an Intune subscription, a Dynamics 365 subscription, and multiple Azure subscriptions.</span></span>

<span data-ttu-id="1979b-124">**Рис. 1. Пример использования нескольких подписок для организации**</span><span class="sxs-lookup"><span data-stu-id="1979b-124">**Figure 1: Example of multiple subscriptions for an organization**</span></span>

![Пример организации с несколькими подписками на облачные предложения корпорации Майкрософт.](media/Subscriptions/Subscriptions-Fig1.png)

  
### <a name="licenses"></a><span data-ttu-id="1979b-126">Лицензии</span><span class="sxs-lookup"><span data-stu-id="1979b-126">Licenses</span></span>

<span data-ttu-id="1979b-127">В случае облачных предложений корпорации Майкрософт на основе SaaS лицензия позволяет определенному пользователю пользоваться услугами облачной службы.</span><span class="sxs-lookup"><span data-stu-id="1979b-127">For Microsoft's SaaS cloud offerings, a license allows a specific user account to use the services of the cloud offering.</span></span> <span data-ttu-id="1979b-128">В рамках подписки ежемесячно взимается фиксированная плата.</span><span class="sxs-lookup"><span data-stu-id="1979b-128">You are charged a fixed monthly fee as part of your subscription.</span></span> <span data-ttu-id="1979b-129">Администраторы назначают лицензии отдельным учетным записям пользователей в подписке.</span><span class="sxs-lookup"><span data-stu-id="1979b-129">Administrators assign licenses to individual user accounts in the subscription.</span></span> <span data-ttu-id="1979b-130">Например, на рис. 2 у корпорации Contoso есть подписка на Office 365 корпоративный E5 со 100 лицензиями, что позволяет 100 отдельным пользователям использовать функции и службы Office 365 корпоративный E5.</span><span class="sxs-lookup"><span data-stu-id="1979b-130">For the example in Figure 2, the Contoso Corporation has an Office 365 Enterprise E5 subscription with 100 licenses, which allows to up to 100 individual user accounts to use Office 365 Enterprise E5 features and services.</span></span>
  
<span data-ttu-id="1979b-131">**Рис. 2. Лицензии в рамках подписок на основе SaaS для организации**</span><span class="sxs-lookup"><span data-stu-id="1979b-131">**Figure 2: Licenses within the SaaS-based subscriptions for an organization**</span></span>

![Пример нескольких лицензий в подписках на облачные предложения корпорации Майкрософт на основе SaaS.](media/Subscriptions/Subscriptions-Fig2.png)
  
<span data-ttu-id="1979b-133">В случае облачных служб на основе Azure PaaS стоимость лицензий на программное обеспечение включается в цену службы.</span><span class="sxs-lookup"><span data-stu-id="1979b-133">For Azure PaaS-based cloud services, software licenses are built into the service pricing.</span></span>
  
<span data-ttu-id="1979b-134">For Azure IaaS-based virtual machines, additional licenses to use the software or application installed on a virtual machine image might be required.</span><span class="sxs-lookup"><span data-stu-id="1979b-134">For Azure IaaS-based virtual machines, additional licenses to use the software or application installed on a virtual machine image might be required.</span></span> <span data-ttu-id="1979b-135">Some virtual machine images have licensed versions of software installed and the cost is included in the per-minute rate for the server.</span><span class="sxs-lookup"><span data-stu-id="1979b-135">Some virtual machine images have licensed versions of software installed and the cost is included in the per-minute rate for the server.</span></span> <span data-ttu-id="1979b-136">Examples are the virtual machine images for SQL Server 2014 and SQL Server 2016.</span><span class="sxs-lookup"><span data-stu-id="1979b-136">Examples are the virtual machine images for SQL Server 2014 and SQL Server 2016.</span></span> 
  
<span data-ttu-id="1979b-137">Some virtual machine images have trial versions of applications installed and need additional software application licenses for use beyond the trial period.</span><span class="sxs-lookup"><span data-stu-id="1979b-137">Some virtual machine images have trial versions of applications installed and need additional software application licenses for use beyond the trial period.</span></span> <span data-ttu-id="1979b-138">For example, the SharePoint Server 2016 Trial virtual machine image includes a trial version of SharePoint Server 2016 pre-installed.</span><span class="sxs-lookup"><span data-stu-id="1979b-138">For example, the SharePoint Server 2016 Trial virtual machine image includes a trial version of SharePoint Server 2016 pre-installed.</span></span> <span data-ttu-id="1979b-139">To continue using SharePoint Server 2016 after the trial expiration date, you must purchase a SharePoint Server 2016 license and client licenses from Microsoft.</span><span class="sxs-lookup"><span data-stu-id="1979b-139">To continue using SharePoint Server 2016 after the trial expiration date, you must purchase a SharePoint Server 2016 license and client licenses from Microsoft.</span></span> <span data-ttu-id="1979b-140">These charges are separate from the Azure subscription and the per-minute rate to run the virtual machine still applies.</span><span class="sxs-lookup"><span data-stu-id="1979b-140">These charges are separate from the Azure subscription and the per-minute rate to run the virtual machine still applies.</span></span>
  
### <a name="user-accounts"></a><span data-ttu-id="1979b-141">Учетные записи пользователей</span><span class="sxs-lookup"><span data-stu-id="1979b-141">User accounts</span></span>

<span data-ttu-id="1979b-142">Учетные записи для всех облачных предложений корпорации Майкрософт хранятся в клиенте Azure Active Directory (Azure AD), содержащем учетные записи и группы пользователей.</span><span class="sxs-lookup"><span data-stu-id="1979b-142">User accounts for all of Microsoft's cloud offerings are stored in an Azure Active Directory (Azure AD) tenant, which contains user accounts and groups.</span></span> <span data-ttu-id="1979b-143">Клиент Azure AD можно синхронизировать с имеющимися учетными записями доменных служб Active Directory (AD DS) с помощью Azure AD Connect, серверной службы Windows.</span><span class="sxs-lookup"><span data-stu-id="1979b-143">An Azure AD tenant can be synchronized with your existing Active Directory Domain Services (AD DS) accounts using Azure AD Connect, a Windows server-based service.</span></span> <span data-ttu-id="1979b-144">Это называется синхронизацией службы каталогов.</span><span class="sxs-lookup"><span data-stu-id="1979b-144">This is known as directory synchronization.</span></span>
  
<span data-ttu-id="1979b-145">На рис. 3 показан пример нескольких подписок организации, использующих общий клиент Azure AD с учетными записями организации.</span><span class="sxs-lookup"><span data-stu-id="1979b-145">Figure 3 shows an example of multiple subscriptions of an organization using a common Azure AD tenant that contains the organization's accounts.</span></span>
  
<span data-ttu-id="1979b-146">**Рис. 3. Несколько подписок организации, использующих один клиент Azure AD**</span><span class="sxs-lookup"><span data-stu-id="1979b-146">**Figure 3: Multiple subscriptions of an organization that use the same Azure AD tenant**</span></span>

![Пример организации с несколькими подписками, использующими один и тот же клиент Azure AD.](media/Subscriptions/Subscriptions-Fig3.png)
  
### <a name="tenants"></a><span data-ttu-id="1979b-148">Клиенты</span><span class="sxs-lookup"><span data-stu-id="1979b-148">Tenants</span></span>

<span data-ttu-id="1979b-149">For SaaS cloud offerings, the tenant is the regional location that houses the servers providing cloud services.</span><span class="sxs-lookup"><span data-stu-id="1979b-149">For SaaS cloud offerings, the tenant is the regional location that houses the servers providing cloud services.</span></span> <span data-ttu-id="1979b-150">For example, the Contoso Corporation chose the European region to host its Office 365, EMS, and Dynamics 365 tenants for the 15,000 workers in their Paris headquarters.</span><span class="sxs-lookup"><span data-stu-id="1979b-150">For example, the Contoso Corporation chose the European region to host its Office 365, EMS, and Dynamics 365 tenants for the 15,000 workers in their Paris headquarters.</span></span>
  
<span data-ttu-id="1979b-151">Azure PaaS services and virtual machine-based workloads hosted in Azure IaaS can have tenancy in any Azure datacenter across the world.</span><span class="sxs-lookup"><span data-stu-id="1979b-151">Azure PaaS services and virtual machine-based workloads hosted in Azure IaaS can have tenancy in any Azure datacenter across the world.</span></span> <span data-ttu-id="1979b-152">You specify the Azure datacenter, known as the location, when you create the Azure PaaS app or service or element of an IaaS workload.</span><span class="sxs-lookup"><span data-stu-id="1979b-152">You specify the Azure datacenter, known as the location, when you create the Azure PaaS app or service or element of an IaaS workload.</span></span>
  
<span data-ttu-id="1979b-153">An Azure AD tenant is a specific instance of Azure AD containing accounts and groups.</span><span class="sxs-lookup"><span data-stu-id="1979b-153">An Azure AD tenant is a specific instance of Azure AD containing accounts and groups.</span></span> <span data-ttu-id="1979b-154">Paid or trial subscriptions of Office 365, Dynamics 365, or Intune/EMS include a free Azure AD tenant.</span><span class="sxs-lookup"><span data-stu-id="1979b-154">Paid or trial subscriptions of Office 365, Dynamics 365, or Intune/EMS include a free Azure AD tenant.</span></span> <span data-ttu-id="1979b-155">This Azure AD tenant does not include other Azure services and is not the same as an Azure trial or paid subscription.</span><span class="sxs-lookup"><span data-stu-id="1979b-155">This Azure AD tenant does not include other Azure services and is not the same as an Azure trial or paid subscription.</span></span>
  
### <a name="summary-of-the-hierarchy"></a><span data-ttu-id="1979b-156">Сводка по иерархии</span><span class="sxs-lookup"><span data-stu-id="1979b-156">Summary of the hierarchy</span></span>

<span data-ttu-id="1979b-157">Краткая сводка:</span><span class="sxs-lookup"><span data-stu-id="1979b-157">Here is a quick recap:</span></span>
  
- <span data-ttu-id="1979b-158">У организации может быть несколько подписок</span><span class="sxs-lookup"><span data-stu-id="1979b-158">An organization can have multiple subscriptions</span></span>
    
  - <span data-ttu-id="1979b-159">В одной подписке может быть несколько лицензий</span><span class="sxs-lookup"><span data-stu-id="1979b-159">A subscription can have multiple licenses</span></span>
    
  - <span data-ttu-id="1979b-160">Лицензии можно назначать отдельным учетным записям</span><span class="sxs-lookup"><span data-stu-id="1979b-160">Licenses can be assigned to individual user accounts</span></span>
    
  - <span data-ttu-id="1979b-161">Учетные записи хранятся в клиенте Azure AD</span><span class="sxs-lookup"><span data-stu-id="1979b-161">User accounts are stored in an Azure AD tenant</span></span>
    
<span data-ttu-id="1979b-162">Ниже приведен пример связи между организациями, подписками, лицензиями и учетными записями пользователей.</span><span class="sxs-lookup"><span data-stu-id="1979b-162">Here is an example of the relationship of organizations, subscriptions, licenses, and user accounts:</span></span>
  
- <span data-ttu-id="1979b-163">Организация определяется по имени общедоступного домена.</span><span class="sxs-lookup"><span data-stu-id="1979b-163">An organization identified by its public domain name.</span></span>
    
  - <span data-ttu-id="1979b-164">Подписка Office 365 корпоративный E3 с лицензиями "на пользователя".</span><span class="sxs-lookup"><span data-stu-id="1979b-164">An Office 365 Enterprise E3 subscription with user licenses.</span></span>
    
    <span data-ttu-id="1979b-165">Подписка Office 365 корпоративный E5 с лицензиями "на пользователя".</span><span class="sxs-lookup"><span data-stu-id="1979b-165">An Office 365 Enterprise E5 subscription with user licenses.</span></span>
    
    <span data-ttu-id="1979b-166">Подписка на EMS с лицензиями "на пользователя".</span><span class="sxs-lookup"><span data-stu-id="1979b-166">An EMS subscription with user licenses.</span></span>
    
    <span data-ttu-id="1979b-167">Подписка на Dynamics 365 с лицензиями "на пользователя".</span><span class="sxs-lookup"><span data-stu-id="1979b-167">A Dynamics 365 subscription with user licenses.</span></span>
    
    <span data-ttu-id="1979b-168">Несколько подписок на Azure.</span><span class="sxs-lookup"><span data-stu-id="1979b-168">Multiple Azure subscriptions.</span></span>
    
  - <span data-ttu-id="1979b-169">Учетные записи пользователей организации на общем клиенте Azure AD.</span><span class="sxs-lookup"><span data-stu-id="1979b-169">The organization's user accounts in a common Azure AD tenant.</span></span>
    
<span data-ttu-id="1979b-170">Для нескольких подписок на облачные решения Майкрософт может использоваться один клиент Azure AD, выступающий в качестве поставщика удостоверений.</span><span class="sxs-lookup"><span data-stu-id="1979b-170">Multiple Microsoft cloud offering subscriptions can use the same Azure AD tenant that acts as a common identity provider.</span></span> <span data-ttu-id="1979b-171">Благодаря центральному клиенту Azure AD, содержащему синхронизированные учетные записи из локальной службы AD DS, возможно предоставление удостоверений как услуги (IDaaS) для организации.</span><span class="sxs-lookup"><span data-stu-id="1979b-171">A central Azure AD tenant that contains the synchronized accounts of your on-premises AD DS provides cloud-based Identity as a Service (IDaaS) for your organization.</span></span> 
  
<span data-ttu-id="1979b-172">**Рис. 4. Синхронизированные локальные учетные записи и IDaaS для организации**</span><span class="sxs-lookup"><span data-stu-id="1979b-172">**Figure 4: Synchronized on-premises accounts and IDaaS for an organization**</span></span>

![Идентификация как служба (IDaaS) для организации.](media/Subscriptions/Subscriptions-Fig4.png)
  
<span data-ttu-id="1979b-174">Figure 4 shows how a common Azure AD tenant is used by Microsoft's SaaS cloud offerings, Azure PaaS apps, and virtual machines in Azure IaaS that use Azure AD Domain Services.</span><span class="sxs-lookup"><span data-stu-id="1979b-174">Figure 4 shows how a common Azure AD tenant is used by Microsoft's SaaS cloud offerings, Azure PaaS apps, and virtual machines in Azure IaaS that use Azure AD Domain Services.</span></span> <span data-ttu-id="1979b-175">Azure AD Connect synchronizes the on-premises AD DS forest with the Azure AD tenant.</span><span class="sxs-lookup"><span data-stu-id="1979b-175">Azure AD Connect synchronizes the on-premises AD DS forest with the Azure AD tenant.</span></span>
  
## <a name="combining-subscriptions-for-multiple-microsoft-cloud-offerings"></a><span data-ttu-id="1979b-176">Объединение подписок для нескольких облачных предложений корпорации Майкрософт</span><span class="sxs-lookup"><span data-stu-id="1979b-176">Combining subscriptions for multiple Microsoft cloud offerings</span></span>

<span data-ttu-id="1979b-177">В приведенной ниже таблице показано, как объединить несколько облачных предложений корпорации Майкрософт на основе имеющейся подписки на облачное предложение одного типа (подписи в первом столбце) и добавленной подписки на другое решение (поперек столбцов).</span><span class="sxs-lookup"><span data-stu-id="1979b-177">The following table describes how you can combine multiple Microsoft cloud offerings based on already having a subscription for one type of cloud offering (the labels going down the first column) and adding a subscription for a different cloud offering (going across the columns).</span></span>
  
||<span data-ttu-id="1979b-178">**Office 365**</span><span class="sxs-lookup"><span data-stu-id="1979b-178">**Office 365**</span></span>|<span data-ttu-id="1979b-179">**Azure**</span><span class="sxs-lookup"><span data-stu-id="1979b-179">**Azure**</span></span>|<span data-ttu-id="1979b-180">**Intune/EMS**</span><span class="sxs-lookup"><span data-stu-id="1979b-180">**Intune/EMS**</span></span>|<span data-ttu-id="1979b-181">**Dynamics 365**</span><span class="sxs-lookup"><span data-stu-id="1979b-181">**Dynamics 365**</span></span>|
|:-----|:-----|:-----|:-----|:-----|
|<span data-ttu-id="1979b-182">**Office 365**</span><span class="sxs-lookup"><span data-stu-id="1979b-182">**Office 365**</span></span> <br/> |<span data-ttu-id="1979b-183">Н/Д</span><span class="sxs-lookup"><span data-stu-id="1979b-183">NA</span></span>  <br/> |<span data-ttu-id="1979b-184">Добавьте подписку Azure для организации с помощью портала Azure.</span><span class="sxs-lookup"><span data-stu-id="1979b-184">You add an Azure subscription to your organization from the Azure portal.</span></span>  <br/> |<span data-ttu-id="1979b-185">Добавьте подписку Intune/EMS для организации в Центре администрирования Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="1979b-185">You add an Intune/EMS subscription to your organization from the Microsoft 365 admin center.</span></span>  <br/> |<span data-ttu-id="1979b-186">Добавьте подписку на Dynamics 365 для организации в Центре администрирования Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="1979b-186">You add a Dynamics 365 subscription to your organization from the Microsoft 365 admin center.</span></span>  <br/> |
|<span data-ttu-id="1979b-187">**Azure**</span><span class="sxs-lookup"><span data-stu-id="1979b-187">**Azure**</span></span> <br/> |<span data-ttu-id="1979b-188">Добавьте подписку на Office 365 для организации.</span><span class="sxs-lookup"><span data-stu-id="1979b-188">You add an Office 365 subscription to your organization.</span></span>  <br/> |<span data-ttu-id="1979b-189">Недоступно</span><span class="sxs-lookup"><span data-stu-id="1979b-189">NA</span></span>  <br/> |<span data-ttu-id="1979b-190">Добавьте подписку Intune/EMS для организации.</span><span class="sxs-lookup"><span data-stu-id="1979b-190">You add an Intune/EMS subscription to your organization.</span></span>  <br/> |<span data-ttu-id="1979b-191">Добавьте подписку Dynamics 365 для организации.</span><span class="sxs-lookup"><span data-stu-id="1979b-191">You add a Dynamics 365 subscription to your organization.</span></span>  <br/> |
|<span data-ttu-id="1979b-192">**Intune/EMS**</span><span class="sxs-lookup"><span data-stu-id="1979b-192">**Intune/EMS**</span></span> <br/> |<span data-ttu-id="1979b-193">Добавьте подписку на Office 365 для организации.</span><span class="sxs-lookup"><span data-stu-id="1979b-193">You add an Office 365 subscription to your organization.</span></span>  <br/> |<span data-ttu-id="1979b-194">Добавьте подписку Azure для организации с помощью портала Azure.</span><span class="sxs-lookup"><span data-stu-id="1979b-194">You add an Azure subscription to your organization from the Azure portal.</span></span>  <br/> |<span data-ttu-id="1979b-195">Недоступно</span><span class="sxs-lookup"><span data-stu-id="1979b-195">NA</span></span>  <br/> |<span data-ttu-id="1979b-196">Добавьте подписку Dynamics 365 для организации.</span><span class="sxs-lookup"><span data-stu-id="1979b-196">You add a Dynamics 365 subscription to your organization.</span></span>  <br/> |
|<span data-ttu-id="1979b-197">**Dynamics 365**</span><span class="sxs-lookup"><span data-stu-id="1979b-197">**Dynamics 365**</span></span> <br/> |<span data-ttu-id="1979b-198">Добавьте подписку на Office 365 для организации.</span><span class="sxs-lookup"><span data-stu-id="1979b-198">You add an Office 365 subscription to your organization.</span></span>  <br/> |<span data-ttu-id="1979b-199">Добавьте подписку Azure для организации с помощью портала Azure.</span><span class="sxs-lookup"><span data-stu-id="1979b-199">You add an Azure subscription to your organization from the Azure portal.</span></span>  <br/> |<span data-ttu-id="1979b-200">Добавьте подписку Intune/EMS для организации.</span><span class="sxs-lookup"><span data-stu-id="1979b-200">You add an Intune/EMS subscription to your organization.</span></span>  <br/> |<span data-ttu-id="1979b-201">Н/Д</span><span class="sxs-lookup"><span data-stu-id="1979b-201">NA</span></span>  <br/> |
   
<span data-ttu-id="1979b-202">Вы можете с легкостью добавить подписки на службы Майкрософт на основе SaaS для организации, используя Центр администрирования.</span><span class="sxs-lookup"><span data-stu-id="1979b-202">An easy way to add subscriptions to your organization for Microsoft SaaS-based services is through the admin center:</span></span>
  
1. <span data-ttu-id="1979b-203">Войдите в Центр администрирования Microsoft 365 ([https://admin.microsoft.com](https://admin.microsoft.com)) с помощью учетной записи глобального администратора.</span><span class="sxs-lookup"><span data-stu-id="1979b-203">Sign in to the Microsoft 365 admin center ([https://admin.microsoft.com](https://admin.microsoft.com)) with your global administrator account.</span></span>
    
2. <span data-ttu-id="1979b-204">В левой части главной страницы **Центра администрирования** выберите **Выставление счетов** > **Приобретение служб**.</span><span class="sxs-lookup"><span data-stu-id="1979b-204">From the left navigation of the **Admin center** home page, click **Billing**, and then **Purchase services**.</span></span>
    
3. <span data-ttu-id="1979b-205">На странице **Приобретение служб** купите новые подписки.</span><span class="sxs-lookup"><span data-stu-id="1979b-205">On the **Purchase services** page, purchase your new subscriptions.</span></span>
    
<span data-ttu-id="1979b-206">Центр администрирования назначает организации и клиенту Azure AD, у которых есть подписка на Office 365, новые подписки на облачные решения на основе SaaS.</span><span class="sxs-lookup"><span data-stu-id="1979b-206">The admin center assigns the organization and Azure AD tenant of your Office 365 subscription to the new subscriptions for SaaS-based cloud offerings.</span></span>
  
<span data-ttu-id="1979b-207">Чтобы добавить подписку Azure с теми же организацией и клиентом Azure AD, что и в подписке на Office 365:</span><span class="sxs-lookup"><span data-stu-id="1979b-207">To add an Azure subscription with the same organization and Azure AD tenant as your Office 365 subscription:</span></span>
  
1. <span data-ttu-id="1979b-208">Войдите на портал Azure ([https://portal.azure.com](https://portal.azure.com)), используя учетную запись глобального администратора Office 365.</span><span class="sxs-lookup"><span data-stu-id="1979b-208">Sign in to the Azure portal ([https://portal.azure.com](https://portal.azure.com)) with your Office 365 global administrator account.</span></span>
    
2. <span data-ttu-id="1979b-209">В области навигации слева выберите **Подписки** > **Добавить**.</span><span class="sxs-lookup"><span data-stu-id="1979b-209">In the left navigation, click **Subscriptions**, and then click **Add**.</span></span>
    
3. <span data-ttu-id="1979b-210">На странице **Добавление подписки** выберите предложение, а затем укажите платежную информацию и примите условия лицензионного соглашения.</span><span class="sxs-lookup"><span data-stu-id="1979b-210">On the **Add subscription** page, select an offer and complete the payment information and agreement.</span></span>
    
<span data-ttu-id="1979b-211">Если вы приобрели подписки на Azure и Office 365 отдельно и хотите получить доступ к клиенту Azure AD в Office 365, воспользуйтесь инструкциями в статье [Добавление существующей подписки на Azure с клиентом Azure Active Directory](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-how-subscriptions-associated-directory).</span><span class="sxs-lookup"><span data-stu-id="1979b-211">If you purchased Azure and Office 365 subscriptions separately and want to access the Office 365 Azure AD tenant from your Azure subscription, see the instructions in [Add an existing Azure subscription to your Azure Active Directory tenant](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-how-subscriptions-associated-directory).</span></span>
 
## <a name="see-also"></a><span data-ttu-id="1979b-212">См. также</span><span class="sxs-lookup"><span data-stu-id="1979b-212">See also</span></span>

[<span data-ttu-id="1979b-213">Ресурсы, посвященные ИТ-архитектуре Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="1979b-213">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)
  
[<span data-ttu-id="1979b-214">Архитектурные модели для SharePoint, Exchange, Skype для бизнеса и Lync</span><span class="sxs-lookup"><span data-stu-id="1979b-214">Architectural models for SharePoint, Exchange, Skype for Business, and Lync</span></span>](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[<span data-ttu-id="1979b-215">Гибридные решения</span><span class="sxs-lookup"><span data-stu-id="1979b-215">Hybrid solutions</span></span>](hybrid-solutions.md)

## <a name="next-step"></a><span data-ttu-id="1979b-216">Следующий шаг</span><span class="sxs-lookup"><span data-stu-id="1979b-216">Next step</span></span>

[<span data-ttu-id="1979b-217">Доступ к сетевому подключению Office 365</span><span class="sxs-lookup"><span data-stu-id="1979b-217">Assessing Office 365 network connectivity</span></span>](assessing-network-connectivity.md)
  
