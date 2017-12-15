---
title: "Подписки, лицензии и учетные записи корпорации Contoso"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: ec3b08f0-288c-4ba3-b822-dbf6352fa761
description: "Сводка: Сведения о структура подписок облачной организации Contoso, лицензий, учетные записи пользователей и клиентов."
ms.openlocfilehash: 6bc90d7b166d5e0983eac8ed47ba16bede57426d
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2017
---
# <a name="subscriptions-licenses-and-user-accounts-for-the-contoso-corporation"></a><span data-ttu-id="b7e50-103">Подписки, лицензии и учетные записи корпорации Contoso</span><span class="sxs-lookup"><span data-stu-id="b7e50-103">Subscriptions, licenses, and user accounts for the Contoso Corporation</span></span>

 <span data-ttu-id="b7e50-104">**Сводка:** Изучить структуру подписок облачной организации Contoso, лицензий, учетные записи пользователей и клиентов.</span><span class="sxs-lookup"><span data-stu-id="b7e50-104">**Summary:** Understand the structure of Contoso's cloud subscriptions, licenses, user accounts, and tenants.</span></span>
  
<span data-ttu-id="b7e50-105">Чтобы достичь согласованного использования идентификаторов и выставления счетов для всех облачных предложений, Майкрософт обеспечивает иерархию на уровне организации, подписок, лицензий и учетных записей пользователей:</span><span class="sxs-lookup"><span data-stu-id="b7e50-105">To provide a consistent use of identities and billing for all cloud offerings, Microsoft provides an organization/subscriptions/licenses/user accounts hierarchy:</span></span>
  
- <span data-ttu-id="b7e50-106">Организация</span><span class="sxs-lookup"><span data-stu-id="b7e50-106">Organization</span></span>
    
    <span data-ttu-id="b7e50-107">Коммерческое предприятие, использующее облачные предложения корпорации Майкрософт. Как правило, она определяется по общедоступному доменному имени DNS, например contoso.com.</span><span class="sxs-lookup"><span data-stu-id="b7e50-107">The business entity that is using Microsoft cloud offerings, typically identified by a public DNS domain name, such as contoso.com.</span></span>
    
- <span data-ttu-id="b7e50-108">Подписки</span><span class="sxs-lookup"><span data-stu-id="b7e50-108">Subscriptions</span></span>
    
    <span data-ttu-id="b7e50-p101">Для Microsoft SaaS cloud (Office 365, Intune/Командной и Dynamics 365) и услуги, подписка — конкретный товар и приобретенные набор пользовательских лицензий. Для Azure подписка обеспечивает выставления счетов Потребленная облачных служб для организации.</span><span class="sxs-lookup"><span data-stu-id="b7e50-p101">For Microsoft SaaS cloud offerings (Office 365, Intune/EMS, and Dynamics 365), a subscription is a specific product and a purchased set of user licenses. For Azure, a subscription allows for billing of consumed cloud services to the organization.</span></span>
    
- <span data-ttu-id="b7e50-111">Лицензии</span><span class="sxs-lookup"><span data-stu-id="b7e50-111">Licenses</span></span>
    
    <span data-ttu-id="b7e50-p102">Для Microsoft SaaS облака лицензия позволяет учетной записи пользователя для использования облачных служб. Для Azure лицензий на программное обеспечение встроены в службу цена, но в некоторых случаях, вам потребуется приобрести лицензии дополнительное программное обеспечение.</span><span class="sxs-lookup"><span data-stu-id="b7e50-p102">For Microsoft SaaS cloud offerings, a license allows a specific user account to use cloud services. For Azure, software licenses are built into service pricing, but in some cases you will need to purchase additional software licenses.</span></span>
    
- <span data-ttu-id="b7e50-114">Учетные записи пользователей</span><span class="sxs-lookup"><span data-stu-id="b7e50-114">User accounts</span></span>
    
    <span data-ttu-id="b7e50-115">Учетные записи пользователей хранятся в клиенте Azure AD и могут быть синхронизированы с локальным поставщиком удостоверений, например Windows Server AD.</span><span class="sxs-lookup"><span data-stu-id="b7e50-115">User accounts are stored in an Azure AD tenant and can be synchronized from an on-premises identity provider such as Windows Server AD.</span></span>
    
## <a name="contosos-structure"></a><span data-ttu-id="b7e50-116">Структура организации Contoso</span><span class="sxs-lookup"><span data-stu-id="b7e50-116">Contoso's structure</span></span>

<span data-ttu-id="b7e50-117">Организация Contoso определила следующую структуру для себя и своих подписок, лицензий, учетных записей и клиентов:</span><span class="sxs-lookup"><span data-stu-id="b7e50-117">Contoso determined the following structure for the organization and its subscriptions, licenses, accounts, and tenants:</span></span>
  
<span data-ttu-id="b7e50-118">**На рисунке 1: Contoso организации, подписок, лицензий, учетные записи пользователей и клиентов**</span><span class="sxs-lookup"><span data-stu-id="b7e50-118">**Figure 1: Contoso's organization, subscriptions, licenses, user accounts and tenants**</span></span>

![Организация Contoso и ее подписки, лицензии, учетные записи пользователей и клиенты](images/Contoso_Poster/Subscriptions.png)
  
<span data-ttu-id="b7e50-120">На рис. 1 показано, что организация Contoso включает множество подписок и связана с общим клиентом Azure AD, содержащим учетные записи пользователей, которые синхронизируются из леса Windows Server AD на contoso.com.</span><span class="sxs-lookup"><span data-stu-id="b7e50-120">Figure 1 shows how the Contoso organization includes multiple subscriptions and is tied to a common Azure AD tenant that contains the user accounts synchronized from the contoso.com Windows Server AD forest.</span></span>
  
- <span data-ttu-id="b7e50-121">**Организация** Contoso Corporation определяется по имени его общедоступного домена contoso.com.</span><span class="sxs-lookup"><span data-stu-id="b7e50-121">**Organization** The Contoso Corporation is identified by its public domain name contoso.com.</span></span>
    
  - <span data-ttu-id="b7e50-122">**Подписки и лицензии** Корпорации Contoso с помощью следующих:</span><span class="sxs-lookup"><span data-stu-id="b7e50-122">**Subscriptions and licenses** The Contoso Corporation is using the following:</span></span>
    
  - <span data-ttu-id="b7e50-123">Продукт Office 365 для предприятий E3 с 5000 лицензий</span><span class="sxs-lookup"><span data-stu-id="b7e50-123">The Office 365 Enterprise E3 product with 5,000 licenses</span></span>
    
  - <span data-ttu-id="b7e50-124">продукт Office 365 корпоративный E5 с 200 лицензиями;</span><span class="sxs-lookup"><span data-stu-id="b7e50-124">The Office 365 Enterprise E5 product with 200 licenses</span></span>
    
  - <span data-ttu-id="b7e50-125">Продукт Командной с 5000 лицензий</span><span class="sxs-lookup"><span data-stu-id="b7e50-125">The EMS product with 5,000 licenses</span></span>
    
  - <span data-ttu-id="b7e50-126">Продукт Dynamics 365 с 100 лицензий</span><span class="sxs-lookup"><span data-stu-id="b7e50-126">The Dynamics 365 product with 100 licenses</span></span>
    
  - <span data-ttu-id="b7e50-127">множество подписок Azure для разных регионов.</span><span class="sxs-lookup"><span data-stu-id="b7e50-127">Multiple Azure subscriptions based on regions</span></span>
    
  - <span data-ttu-id="b7e50-128">**Учетные записи пользователей** Распространенные клиента Azure AD содержит список учетных записей пользователей и групп используется всех подписок Contoso, за исключением разработку и тестирование Azure подписок.</span><span class="sxs-lookup"><span data-stu-id="b7e50-128">**User accounts** A common Azure AD tenant contains the list of user accounts and groups used by all of Contoso's subscriptions, with the exception of dev/test Azure subscriptions.</span></span>
    
<span data-ttu-id="b7e50-129">Для клиентов Contoso:</span><span class="sxs-lookup"><span data-stu-id="b7e50-129">For Contoso's tenants:</span></span>
  
- <span data-ttu-id="b7e50-p103">Для SaaS облака клиента — региональных расположение, которое содержит серверов, обеспечивающих работу облачных служб. Contoso выбрал европейских региона для размещения его клиентов Office 365, Командной и Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="b7e50-p103">For SaaS cloud offerings, the tenant is the regional location that houses the servers providing cloud services. Contoso chose the European region to host its Office 365, EMS, and Dynamics 365 tenants.</span></span> 
    
- <span data-ttu-id="b7e50-p104">Azure PaaS служб и приложений и рабочие нагрузки ИТ IaaS может иметь аренде в любой Azure центра обработки данных по всему миру. Клиент Azure AD — это определенный экземпляр Azure AD, содержащий учетные записи и группы.</span><span class="sxs-lookup"><span data-stu-id="b7e50-p104">Azure PaaS services and apps and IaaS IT workloads can have tenancy in any Azure datacenter across the world. An Azure AD tenant is a specific instance of Azure AD containing accounts and groups.</span></span>
    
- <span data-ttu-id="b7e50-134">Распространенные клиента Azure AD, содержащий синхронизированного учетные записи для Contoso Windows Server AD лес предоставляет IDaaS в облаке и услуги корпорации Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="b7e50-134">The common Azure AD tenant that contains the synchronized accounts for the Contoso Windows Server AD forest provides IDaaS across Microsoft's cloud offerings.</span></span>
    
<span data-ttu-id="b7e50-135">Для получения дополнительных сведений см [подписок, лицензий, учетные записи и для корпорации Майкрософт облака клиентов](subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings.md).</span><span class="sxs-lookup"><span data-stu-id="b7e50-135">For more information, see [Subscriptions, licenses, accounts, and tenants for Microsoft's cloud offerings](subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings.md).</span></span>
  
## <a name="contosos-azure-subscriptions"></a><span data-ttu-id="b7e50-136">Contoso Azure подписки</span><span class="sxs-lookup"><span data-stu-id="b7e50-136">Contoso's Azure subscriptions</span></span>

<span data-ttu-id="b7e50-137">На рисунке 2 показано, иерархические структуры Contoso Azure подписки:</span><span class="sxs-lookup"><span data-stu-id="b7e50-137">Figure 2 shows the hierarchical design of Contoso's Azure subscriptions:</span></span>
  
<span data-ttu-id="b7e50-138">**На рисунке 2: Структура организации Contoso для Azure подписок**</span><span class="sxs-lookup"><span data-stu-id="b7e50-138">**Figure 2: Contoso's structure for Azure subscriptions**</span></span>

![Структура подписок Azure для Contoso](images/Contoso_Poster/Subscriptions_Nested.png)
  
- <span data-ttu-id="b7e50-140">Contoso находится на верхнем уровне по соглашению Enterprise с корпорацией Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="b7e50-140">Contoso is at the top, based on its Enterprise Agreement with Microsoft.</span></span>
    
- <span data-ttu-id="b7e50-141">Существует набор учетных записей, соответствующий в разные регионы Contoso Corporation по всему миру, на основании доменов леса Windows Server AD организации Contoso.</span><span class="sxs-lookup"><span data-stu-id="b7e50-141">There are a set of accounts corresponding to the different regions of the Contoso Corporation around the world, based on the domains of Contoso's Windows Server AD forest.</span></span>
    
- <span data-ttu-id="b7e50-142">В каждом регионе существует один или несколько подписок на основании потребностей развертывания разработки, тестирования и рабочей области.</span><span class="sxs-lookup"><span data-stu-id="b7e50-142">Within each region, there are one or more subscriptions based on the region's development, testing, and production deployment needs.</span></span>
    
<span data-ttu-id="b7e50-p105">Каждая подписка Azure может быть связана с одним клиентом Azure AD, содержащим учетные записи пользователей и группы для проверки подлинности и авторизации в службах Azure. Рабочие подписки используют общий клиент Contoso Azure AD.</span><span class="sxs-lookup"><span data-stu-id="b7e50-p105">Each Azure subscription can be associated with a single Azure AD tenant that contains user accounts and groups for authentication and authorization to Azure services. Production subscriptions use the common Contoso Azure AD tenant.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="b7e50-145">See Also</span><span class="sxs-lookup"><span data-stu-id="b7e50-145">See Also</span></span>

[<span data-ttu-id="b7e50-146">Contoso в Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="b7e50-146">Contoso in the Microsoft Cloud</span></span>](contoso-in-the-microsoft-cloud.md)
  
[<span data-ttu-id="b7e50-147">Ресурсы для администраторов, посвященные архитектуре Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="b7e50-147">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="b7e50-148">Стратегия Enterprise Cloud корпорации Майкрософт: ресурсы для лиц, принимающих решения в области ИТ</span><span class="sxs-lookup"><span data-stu-id="b7e50-148">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)




