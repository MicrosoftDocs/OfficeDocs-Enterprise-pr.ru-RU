---
title: Подписки, лицензии, учетные записи и клиенты для облачных предложений корпорации Майкрософт
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/12/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_Architecture
ms.assetid: c720cffc-f9b5-4f43-9100-422f86a1027c
description: Сводка. Общие сведения о связи между организациями, подписками, лицензиями, учетными записями пользователей и клиентами в облачных предложениях корпорации Майкрософт.
ms.openlocfilehash: 5f434fef42777034d32970dd55e15be35b76961e
ms.sourcegitcommit: d0f1f34b1702e304fec85ca72f1f660e9b328dd5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/20/2018
ms.locfileid: "24022078"
---
# <a name="subscriptions-licenses-accounts-and-tenants-for-microsofts-cloud-offerings"></a><span data-ttu-id="b781b-103">Подписки, лицензии, учетные записи и клиенты для облачных предложений корпорации Майкрософт</span><span class="sxs-lookup"><span data-stu-id="b781b-103">Subscriptions, licenses, accounts, and tenants for Microsoft's cloud offerings</span></span>

 <span data-ttu-id="b781b-104">**Сводка.** Общие сведения о связи между организациями, подписками, лицензиями, учетными записями пользователей и клиентами в облачных предложениях корпорации Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="b781b-104">**Summary:** Understand the relationships of organizations, subscriptions, licenses, user accounts, and tenants across Microsoft's cloud offerings.</span></span>
  
<span data-ttu-id="b781b-105">Для облачных решений Майкрософт предусмотрена иерархия организаций, подписок, лицензий и учетных записей пользователей. Это обеспечивает согласованное использование удостоверений и выставление счетов.</span><span class="sxs-lookup"><span data-stu-id="b781b-105">Microsoft provides a hierarchy of organizations, subscriptions, licenses, and user accounts for consistent use of identities and billing across its cloud offerings:</span></span>
  
- <span data-ttu-id="b781b-106">Microsoft Office 365</span><span class="sxs-lookup"><span data-stu-id="b781b-106">Microsoft Office 365</span></span>
    
    <span data-ttu-id="b781b-107">[Планы для бизнеса и цены](https://products.office.com/business/compare-office-365-for-business-plans)</span><span class="sxs-lookup"><span data-stu-id="b781b-107">See [business plans and pricing](https://products.office.com/business/compare-office-365-for-business-plans) for more information.</span></span>
    
- <span data-ttu-id="b781b-108">Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="b781b-108">Microsoft Azure</span></span>
    
    <span data-ttu-id="b781b-109">[Цены на Azure](https://azure.microsoft.com/pricing/)</span><span class="sxs-lookup"><span data-stu-id="b781b-109">See [Azure pricing](https://azure.microsoft.com/pricing/) for more information.</span></span>
    
- <span data-ttu-id="b781b-110">Microsoft Intune и Enterprise Mobility + Security (EMS)</span><span class="sxs-lookup"><span data-stu-id="b781b-110">Microsoft Intune and the Enterprise Mobility + Security (EMS)</span></span>
    
    <span data-ttu-id="b781b-111">[Цены на Intune](https://www.microsoft.com/cloud-platform/microsoft-intune-pricing)</span><span class="sxs-lookup"><span data-stu-id="b781b-111">See [Intune pricing](https://www.microsoft.com/cloud-platform/microsoft-intune-pricing) for more information.</span></span>
    
- <span data-ttu-id="b781b-112">Microsoft Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="b781b-112">Microsoft Dynamics 365</span></span>
    
    <span data-ttu-id="b781b-113">[Цены на Dynamics 365](https://dynamics.microsoft.com/)</span><span class="sxs-lookup"><span data-stu-id="b781b-113">See [Dynamics 365 pricing](https://dynamics.microsoft.com/) for more information.</span></span>
    
## <a name="elements-of-the-hierarchy"></a><span data-ttu-id="b781b-114">Элементы иерархии</span><span class="sxs-lookup"><span data-stu-id="b781b-114">Elements of the hierarchy</span></span>

<span data-ttu-id="b781b-115">Ниже перечислены элементы иерархии.</span><span class="sxs-lookup"><span data-stu-id="b781b-115">Here are the elements of the hierarchy:</span></span>
  
### <a name="organization"></a><span data-ttu-id="b781b-116">Организация</span><span class="sxs-lookup"><span data-stu-id="b781b-116">Organization</span></span>

<span data-ttu-id="b781b-p101">Организация представляет субъект бизнес-деятельности, использующий облачные решения Майкрософт. Как правило, он определяется по одному или нескольким именам общедоступного домена службы доменных имен (DNS), например contoso.com. Организация является контейнером для подписок.</span><span class="sxs-lookup"><span data-stu-id="b781b-p101">An organization represents a business entity that is using Microsoft cloud offerings, typically identified by one or more public Domain Name System (DNS) domain names, such as contoso.com. The organization is a container for subscriptions.</span></span>
  
### <a name="subscriptions"></a><span data-ttu-id="b781b-119">Подписки</span><span class="sxs-lookup"><span data-stu-id="b781b-119">Subscriptions</span></span>

<span data-ttu-id="b781b-p102">Подписка — это соглашение с корпорацией Майкрософт на использование одной или нескольких платформ или служб Майкрософт, за которые взимается плата (по лицензиям отдельных пользователей или по использованию облачных ресурсов). В облачных предложениях корпорации Майкрософт на основе SaaS (Office 365, Intune/EMS и Dynamics 365) оплата взимается за лицензии пользователей. В облачных предложениях корпорации Майкрософт (Azure) на основе PaaS (платформа как услуга) и IaaS (инфраструктура как услуга) оплата взимается за использование облачных ресурсов.</span><span class="sxs-lookup"><span data-stu-id="b781b-p102">A subscription is an agreement with Microsoft to use one or more Microsoft cloud platforms or services, for which charges accrue based on either a per-user license fee or on cloud-based resource consumption. Microsoft's Software as a Service (SaaS)-based cloud offerings (Office 365, Intune/EMS, and Dynamics 365) charge per-user license fees. Microsoft's Platform as a Service (PaaS) and Infrastructure as a Service (IaaS) cloud offerings (Azure) charge based on cloud resource consumption.</span></span>
  
<span data-ttu-id="b781b-p103">Вы также можете использовать пробную подписку, срок действия которой истекает через определенное время или после использования определенного количества ресурсов. Вы можете преобразовать пробную подписку в платную.</span><span class="sxs-lookup"><span data-stu-id="b781b-p103">You can also use a trial subscription, but the subscription expires after a specific amount of time or consumption charges. You can convert a trial subscription to a paid subscription.</span></span>
  
<span data-ttu-id="b781b-p104">У организации может быть несколько подписок на облачные предложения корпорации Майкрософт, как показано на рис. 1.</span><span class="sxs-lookup"><span data-stu-id="b781b-p104">Organizations can have multiple subscriptions for Microsoft's cloud offerings. Figure 1 shows an example.</span></span>
  
<span data-ttu-id="b781b-127">**Рис. 1. Пример использования нескольких подписок для организации**</span><span class="sxs-lookup"><span data-stu-id="b781b-127">**Figure 1: Example of multiple subscriptions for an organization**</span></span>

![Пример организации с несколькими подписками на облачные предложения корпорации Майкрософт.](media/Subscriptions/Subscriptions-Fig1.png)

  
<span data-ttu-id="b781b-129">На изображении 1 показана одна организация с несколькими подписками на Office 365 и Azure, подпиской на Intune и подпиской на Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="b781b-129">Figure 1 shows a single organization that has multiple Office 365 subscriptions, an Intune subscription, a Dynamics 365 subscription, and multiple Azure subscriptions.</span></span>
  
### <a name="licenses"></a><span data-ttu-id="b781b-130">Лицензии</span><span class="sxs-lookup"><span data-stu-id="b781b-130">Licenses</span></span>

<span data-ttu-id="b781b-p105">В случае облачных предложений корпорации Майкрософт на основе SaaS лицензия позволяет определенному пользователю пользоваться услугами облачной службы. В рамках подписки ежемесячно взимается плата. Администраторы назначают лицензии отдельным учетным записям пользователей в подписке. Например, на рис. 2 у корпорации Contoso есть подписка на Office 365 корпоративный E5 со 100 лицензиями, что позволяет 100 отдельным пользователям использовать функции и службы Office 365 корпоративный E5.</span><span class="sxs-lookup"><span data-stu-id="b781b-p105">For Microsoft's SaaS cloud offerings, a license allows a specific user account to use the services of the cloud offering. You are charged a fixed monthly fee as part of your subscription. Administrators assign licenses to individual user accounts in the subscription. For the example in Figure 2, the Contoso Corporation has an Office 365 Enterprise E5 subscription with 100 licenses, which allows to up to 100 individual user accounts to use Enterprise E5 features and services.</span></span>
  
<span data-ttu-id="b781b-135">**Рис. 2. Лицензии в рамках подписок на основе SaaS для организации**</span><span class="sxs-lookup"><span data-stu-id="b781b-135">**Figure 2: Licenses within the SaaS-based subscriptions for an organization**</span></span>

![Пример нескольких лицензий в подписках на облачные предложения корпорации Майкрософт на основе SaaS.](media/Subscriptions/Subscriptions-Fig2.png)
  
<span data-ttu-id="b781b-137">В случае облачных служб на основе Azure PaaS стоимость лицензий на программное обеспечение включается в цену службы.</span><span class="sxs-lookup"><span data-stu-id="b781b-137">For Azure PaaS-based cloud services, software licenses are built into the service pricing.</span></span>
  
<span data-ttu-id="b781b-p106">Для виртуальных машин на основе Azure IaaS могут потребоваться дополнительные лицензии на использование ПО или приложений, установленных в образе виртуальной машины. В некоторых образах виртуальных машин установлены лицензированные версии программного обеспечения, цены которых включаются в поминутный тариф для сервера. К примерам таких виртуальных машин относятся образы для SQL Server 2014 и SQL Server 2016.</span><span class="sxs-lookup"><span data-stu-id="b781b-p106">For Azure IaaS-based virtual machines, additional licenses to use the software or application installed on a virtual machine image might be required. Some virtual machine images have licensed versions of software installed and the cost is included in the per-minute rate for the server. Examples are the virtual machine images for SQL Server 2014 and SQL Server 2016.</span></span> 
  
<span data-ttu-id="b781b-p107">В некоторых образах виртуальных машин установлены пробные версии приложений, а для их использования по завершении пробного периода требуются дополнительные лицензии. Например, образ виртуальной машины для пробной версии SharePoint Server 2016 включает предустановленную пробную версию SharePoint Server 2016. Чтобы продолжать использовать SharePoint Server 2016 по истечении пробного периода, необходимо приобрести у корпорации Майкрософт лицензию на SharePoint Server 2016 и клиентские лицензии. Эта плата взимается отдельно от платы за подписку Azure и не отменяет поминутный тариф на работу виртуальной машины.</span><span class="sxs-lookup"><span data-stu-id="b781b-p107">Some virtual machine images have trial versions of applications installed and need additional software application licenses for use beyond the trial period. For example, the SharePoint Server 2016 Trial virtual machine image includes a trial version of SharePoint Server 2016 pre-installed. To continue using SharePoint Server 2016 after the trail expiration date, you must purchase a SharePoint Server 2016 license and client licenses from Microsoft. These charges are separate from the Azure subscription and the per-minute rate to run the virtual machine still applies.</span></span>
  
### <a name="user-accounts"></a><span data-ttu-id="b781b-145">Учетные записи пользователей</span><span class="sxs-lookup"><span data-stu-id="b781b-145">User accounts</span></span>

<span data-ttu-id="b781b-p108">Учетные записи для всех облачных предложений корпорации Майкрософт хранятся в клиенте Azure AD, содержащем учетные записи и группы пользователей. Клиент Azure AD можно синхронизировать с имеющимися учетными записями Windows Server AD с помощью Azure AD Connect, серверной службы Windows. Это называется синхронизацией службы каталогов, или DirSync.</span><span class="sxs-lookup"><span data-stu-id="b781b-p108">User accounts for all of Microsoft's cloud offerings are stored in an Azure Active Directory (AD) tenant, which contains user accounts and groups. An Azure AD tenant can be synchronized with your existing Windows Server AD accounts using Azure AD Connect, a Windows server-based service. This is known as directory synchronization (DirSync).</span></span>
  
<span data-ttu-id="b781b-149">На рис. 3 показан пример нескольких подписок организации, использующих общий клиент Azure AD с учетными записями организации.</span><span class="sxs-lookup"><span data-stu-id="b781b-149">Figure 3 shows an example of multiple subscriptions of an organization using a common Azure AD tenant that contains the organization's accounts.</span></span>
  
<span data-ttu-id="b781b-150">**Рис. 3. Несколько подписок организации, использующих один клиент Azure AD**</span><span class="sxs-lookup"><span data-stu-id="b781b-150">**Figure 3: Multiple subscriptions of an organization that use the same Azure AD tenant**</span></span>

![Пример организации с несколькими подписками, использующими один и тот же клиент Azure AD.](media/Subscriptions/Subscriptions-Fig3.png)
  
### <a name="tenants"></a><span data-ttu-id="b781b-152">Клиенты</span><span class="sxs-lookup"><span data-stu-id="b781b-152">Tenants</span></span>

<span data-ttu-id="b781b-p109">В случае облачных предложений на основе SaaS клиент — это регион, в котором располагаются серверы, предоставляющие облачные службы. Например, корпорация Contoso выбрала европейский регион для размещения клиентов Office 365, EMS и Dynamics 365, которыми пользуются 15 000 сотрудников главного офиса компании в Париже.</span><span class="sxs-lookup"><span data-stu-id="b781b-p109">For SaaS cloud offerings, the tenant is the regional location that houses the servers providing cloud services. For example, the Contoso Corporation chose the European region to host its Office 365, EMS, and Dynamics 365 tenants for the 15,000 workers in their Paris headquarters.</span></span>
  
<span data-ttu-id="b781b-p110">Службы PaaS Azure и рабочие нагрузки на основе виртуальных машин, размещенные на платформе IaaS Azure, могут находиться в центре обработки данных Azure в любой точке мира. Центр обработки данных Azure, или расположение, указывается при создании приложения или службы PaaS Azure либо элемента рабочей нагрузки IaaS.</span><span class="sxs-lookup"><span data-stu-id="b781b-p110">Azure PaaS services and virtual machine-based workloads hosted in Azure IaaS can have tenancy in any Azure datacenter across the world. You specify the Azure datacenter, known as the location, when you create the Azure PaaS app or service or element of an IaaS workload.</span></span>
  
<span data-ttu-id="b781b-p111">Клиент Azure AD — это определенный экземпляр Azure AD, содержащий учетные записи и группы. Платные и пробные подписки Office 365, Dynamics 365 или Intune/EMS включают бесплатный клиент Azure AD. Этот клиент Azure AD не включает службы Azure и не предоставляется с пробной или платной подпиской Azure.</span><span class="sxs-lookup"><span data-stu-id="b781b-p111">An Azure AD tenant is a specific instance of Azure AD containing accounts and groups. Paid or trial subscriptions of Office 365, Dynamics 365, or Intune/EMS include a free Azure AD tenant. This Azure AD tenant does not include other Azure services and is not the same as an Azure trial or paid subscription.</span></span>
  
### <a name="summary-of-the-hierarchy"></a><span data-ttu-id="b781b-160">Сводка по иерархии</span><span class="sxs-lookup"><span data-stu-id="b781b-160">Summary of the hierarchy</span></span>

<span data-ttu-id="b781b-161">Краткая сводка:</span><span class="sxs-lookup"><span data-stu-id="b781b-161">Here is a quick recap:</span></span>
  
- <span data-ttu-id="b781b-162">У организации может быть несколько подписок</span><span class="sxs-lookup"><span data-stu-id="b781b-162">An organization can have multiple subscriptions</span></span>
    
  - <span data-ttu-id="b781b-163">В одной подписке может быть несколько лицензий</span><span class="sxs-lookup"><span data-stu-id="b781b-163">A subscription can have multiple licenses</span></span>
    
  - <span data-ttu-id="b781b-164">Лицензии можно назначать отдельным учетным записям</span><span class="sxs-lookup"><span data-stu-id="b781b-164">Licenses can be assigned to individual user accounts</span></span>
    
  - <span data-ttu-id="b781b-165">Учетные записи хранятся в клиенте Azure AD</span><span class="sxs-lookup"><span data-stu-id="b781b-165">User accounts are stored in an Azure AD tenant</span></span>
    
<span data-ttu-id="b781b-166">Ниже приведен пример связи между организациями, подписками, лицензиями и учетными записями пользователей.</span><span class="sxs-lookup"><span data-stu-id="b781b-166">Here is an example of the relationship of organizations, subscriptions, licenses, and user accounts:</span></span>
  
- <span data-ttu-id="b781b-167">Организация определяется по имени общедоступного домена.</span><span class="sxs-lookup"><span data-stu-id="b781b-167">An organization identified by its public domain name.</span></span>
    
  - <span data-ttu-id="b781b-168">Подписка Office 365 корпоративный E3 с лицензиями "на пользователя".</span><span class="sxs-lookup"><span data-stu-id="b781b-168">An Office 365 Enterprise E3 subscription with user licenses.</span></span>
    
    <span data-ttu-id="b781b-169">Подписка Office 365 корпоративный E5 с лицензиями "на пользователя".</span><span class="sxs-lookup"><span data-stu-id="b781b-169">An Office 365 Enterprise E5 subscription with user licenses.</span></span>
    
    <span data-ttu-id="b781b-170">Подписка на EMS с лицензиями "на пользователя".</span><span class="sxs-lookup"><span data-stu-id="b781b-170">An EMS subscription with user licenses.</span></span>
    
    <span data-ttu-id="b781b-171">Подписка на Dynamics 365 с лицензиями "на пользователя".</span><span class="sxs-lookup"><span data-stu-id="b781b-171">A Dynamics 365 subscription with user licenses.</span></span>
    
    <span data-ttu-id="b781b-172">Несколько подписок на Azure.</span><span class="sxs-lookup"><span data-stu-id="b781b-172">Multiple Azure subscriptions.</span></span>
    
  - <span data-ttu-id="b781b-173">Учетные записи пользователей организации на общем клиенте Azure AD.</span><span class="sxs-lookup"><span data-stu-id="b781b-173">The organization's user accounts in a common Azure AD tenant.</span></span>
    
<span data-ttu-id="b781b-p112">Для нескольких подписок на облачные решения Майкрософт может использоваться один клиент Azure AD, выступающий в качестве поставщика удостоверений. Благодаря центральному клиенту Azure AD, содержащему синхронизированные учетные записи из локальной службы Active Directory в составе Windows Server, возможно предоставление удостоверений как услуги (IDaaS) для организации. Это показано на рисунке 4.</span><span class="sxs-lookup"><span data-stu-id="b781b-p112">Multiple Microsoft cloud offering subscriptions can use the same Azure AD tenant that acts as a common identity provider. A central Azure AD tenant that contains the synchronized accounts of your on-premises Windows Server AD provides cloud-based Identity as a Service (IDaaS) for your organization. This is shown in Figure 4.</span></span>
  
<span data-ttu-id="b781b-177">**Рис. 4. Синхронизированные локальные учетные записи и IDaaS для организации**</span><span class="sxs-lookup"><span data-stu-id="b781b-177">**Figure 4: Synchronized on-premises accounts and IDaaS for an organization**</span></span>

![Идентификация как служба (IDaaS) для организации.](media/Subscriptions/Subscriptions-Fig4.png)
  
<span data-ttu-id="b781b-p113">На рисунке 4 показано, как взаимодействуют с общим клиентом Azure AD облачные решения SaaS Майкрософт, приложения PaaS Azure и виртуальные машины на платформе IaaS Azure, использующие доменные службы Azure AD. Клиент Azure AD синхронизируется с локальным лесом Active Directory Windows Server с помощью Azure AD Connect.</span><span class="sxs-lookup"><span data-stu-id="b781b-p113">Figure 4 shows how a common Azure AD tenant is utilized by Microsoft's SaaS cloud offerings, Azure PaaS apps, and virtual machines in Azure IaaS that use Azure AD Domain Services. Azure AD Connect synchronizes the on-premises Windows Server AD forest with the Azure AD tenant.</span></span>
  
<span data-ttu-id="b781b-181">Дополнительные сведения об интеграции идентификации между облачными решениями Майкрософт см. в разделе [Идентификация в Microsoft Cloud для корпоративных архитекторов](https://aka.ms/cloudarchidentity).</span><span class="sxs-lookup"><span data-stu-id="b781b-181">For more information about identity integration across Microsoft's cloud offerings, see [Microsoft Cloud Identity for Enterprise Architects](https://aka.ms/cloudarchidentity).</span></span>
  
## <a name="combining-subscriptions-for-multiple-microsoft-cloud-offerings"></a><span data-ttu-id="b781b-182">Объединение подписок для нескольких облачных предложений корпорации Майкрософт</span><span class="sxs-lookup"><span data-stu-id="b781b-182">Combining subscriptions for multiple Microsoft cloud offerings</span></span>

<span data-ttu-id="b781b-183">В приведенной ниже таблице показано, как объединить несколько облачных предложений корпорации Майкрософт на основе имеющейся подписки на облачное предложение одного типа (подписи в первом столбце) и добавленной подписки на другое решение (поперек столбцов).</span><span class="sxs-lookup"><span data-stu-id="b781b-183">The following table describes how you can combine multiple Microsoft cloud offerings based on already having a subscription for one type of cloud offering (the labels going down the first column) and adding a subscription for a different cloud offering (going across the columns).</span></span>
  
||<span data-ttu-id="b781b-184">**Office 365**</span><span class="sxs-lookup"><span data-stu-id="b781b-184">**Office 365**</span></span>|<span data-ttu-id="b781b-185">**Azure**</span><span class="sxs-lookup"><span data-stu-id="b781b-185">**Azure**</span></span>|<span data-ttu-id="b781b-186">**Intune/EMS**</span><span class="sxs-lookup"><span data-stu-id="b781b-186">**Intune/EMS**</span></span>|<span data-ttu-id="b781b-187">**Dynamics 365**</span><span class="sxs-lookup"><span data-stu-id="b781b-187">**Dynamics 365**</span></span>|
|:-----|:-----|:-----|:-----|:-----|
|<span data-ttu-id="b781b-188">**Office 365**</span><span class="sxs-lookup"><span data-stu-id="b781b-188">**Office 365**</span></span> <br/> |<span data-ttu-id="b781b-189">Н/Д</span><span class="sxs-lookup"><span data-stu-id="b781b-189">NA</span></span>  <br/> |<span data-ttu-id="b781b-190">Добавьте подписку Azure для организации с помощью портала Azure.</span><span class="sxs-lookup"><span data-stu-id="b781b-190">You add an Azure subscription to your organization from the Azure portal.</span></span>  <br/> |<span data-ttu-id="b781b-191">Добавьте подписку Intune/EMS для организации с помощью портала Office 365.</span><span class="sxs-lookup"><span data-stu-id="b781b-191">You add an Intune/EMS subscription to your organization from the Office 365 portal.</span></span>  <br/> |<span data-ttu-id="b781b-192">Добавьте подписку на Dynamics 365 для организации на портале Office 365.</span><span class="sxs-lookup"><span data-stu-id="b781b-192">You add a Dynamics 365 subscription to your organization from the Office 365 portal.</span></span>  <br/> |
|<span data-ttu-id="b781b-193">**Azure**</span><span class="sxs-lookup"><span data-stu-id="b781b-193">**Azure**</span></span> <br/> |<span data-ttu-id="b781b-194">Добавьте подписку на Office 365 для организации.</span><span class="sxs-lookup"><span data-stu-id="b781b-194">You add an Office 365 subscription to your organization.</span></span>  <br/> |<span data-ttu-id="b781b-195">Недоступно</span><span class="sxs-lookup"><span data-stu-id="b781b-195">NA</span></span>  <br/> |<span data-ttu-id="b781b-196">Добавьте подписку Intune/EMS для организации.</span><span class="sxs-lookup"><span data-stu-id="b781b-196">You add an Intune/EMS subscription to your organization.</span></span>  <br/> |<span data-ttu-id="b781b-197">Добавьте подписку Dynamics 365 для организации.</span><span class="sxs-lookup"><span data-stu-id="b781b-197">You add a Dynamics 365 subscription to your organization.</span></span>  <br/> |
|<span data-ttu-id="b781b-198">**Intune/EMS**</span><span class="sxs-lookup"><span data-stu-id="b781b-198">**Intune/EMS**</span></span> <br/> |<span data-ttu-id="b781b-199">Добавьте подписку на Office 365 для организации.</span><span class="sxs-lookup"><span data-stu-id="b781b-199">You add an Office 365 subscription to your organization.</span></span>  <br/> |<span data-ttu-id="b781b-200">Добавьте подписку Azure для организации с помощью портала Azure.</span><span class="sxs-lookup"><span data-stu-id="b781b-200">You add an Azure subscription to your organization from the Azure portal.</span></span>  <br/> |<span data-ttu-id="b781b-201">Недоступно</span><span class="sxs-lookup"><span data-stu-id="b781b-201">NA</span></span>  <br/> |<span data-ttu-id="b781b-202">Добавьте подписку Dynamics 365 для организации.</span><span class="sxs-lookup"><span data-stu-id="b781b-202">You add a Dynamics 365 subscription to your organization.</span></span>  <br/> |
|<span data-ttu-id="b781b-203">**Dynamics 365**</span><span class="sxs-lookup"><span data-stu-id="b781b-203">**Dynamics 365**</span></span> <br/> |<span data-ttu-id="b781b-204">Добавьте подписку на Office 365 для организации.</span><span class="sxs-lookup"><span data-stu-id="b781b-204">You add an Office 365 subscription to your organization.</span></span>  <br/> |<span data-ttu-id="b781b-205">Добавьте подписку Azure для организации с помощью портала Azure.</span><span class="sxs-lookup"><span data-stu-id="b781b-205">You add an Azure subscription to your organization from the Azure portal.</span></span>  <br/> |<span data-ttu-id="b781b-206">Добавьте подписку Intune/EMS для организации.</span><span class="sxs-lookup"><span data-stu-id="b781b-206">You add an Intune/EMS subscription to your organization.</span></span>  <br/> |<span data-ttu-id="b781b-207">Недоступно</span><span class="sxs-lookup"><span data-stu-id="b781b-207">NA</span></span>  <br/> |
   
<span data-ttu-id="b781b-208">Вы можете легко добавлять подписки на службы Майкрософт на основе SaaS, используя Центр администрирования Office 365:</span><span class="sxs-lookup"><span data-stu-id="b781b-208">An easy way to add subscriptions to your organization for Microsoft SaaS-based services is through the Office 365 Admin center:</span></span>
  
1. <span data-ttu-id="b781b-209">Войдите на портал Office 365 ([https://portal.office.com](https://portal.office.com)), используя учетную запись глобального администратора, и выберите **Администрирование**.</span><span class="sxs-lookup"><span data-stu-id="b781b-209">Sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) with your global administrator account, and then click **Admin**.</span></span>
    
2. <span data-ttu-id="b781b-210">В левой части главной страницы **Центра администрирования** выберите **Выставление счетов** > **Приобретение служб**.</span><span class="sxs-lookup"><span data-stu-id="b781b-210">From the left navigation of the **Admin center** home page, click **Billing**, and then **Purchase services**.</span></span>
    
3. <span data-ttu-id="b781b-211">На странице **Приобретение служб** купите новые подписки.</span><span class="sxs-lookup"><span data-stu-id="b781b-211">On the **Purchase services** page, purchase your new subscriptions.</span></span>
    
<span data-ttu-id="b781b-212">Центр администрирования Office 365 назначает для новых подписок на облачные решения SaaS соответствующие организацию и клиента Azure AD, указанные для подписки на Office 365.</span><span class="sxs-lookup"><span data-stu-id="b781b-212">The Office 365 Admin center assigns the organization and Azure AD tenant of your Office 365 subscription to the new subscriptions for SaaS-based cloud offerings.</span></span>
  
<span data-ttu-id="b781b-213">Чтобы добавить подписку Azure с теми же организацией и клиентом Azure AD, что и в подписке на Office 365:</span><span class="sxs-lookup"><span data-stu-id="b781b-213">To add an Azure subscription with the same organization and Azure AD tenant as your Office 365 subscription:</span></span>
  
1. <span data-ttu-id="b781b-214">Войдите на портал Azure ([https://portal.azure.com](https://portal.azure.com)), используя учетную запись глобального администратора Office 365.</span><span class="sxs-lookup"><span data-stu-id="b781b-214">Sign in to the Azure portal ([https://portal.azure.com](https://portal.azure.com)) with your Office 365 global administrator account.</span></span>
    
2. <span data-ttu-id="b781b-215">В области навигации слева выберите **Подписки** > **Добавить**.</span><span class="sxs-lookup"><span data-stu-id="b781b-215">In the left navigation, click **Subscriptions**, and then click **Add**.</span></span>
    
3. <span data-ttu-id="b781b-216">На странице **Добавление подписки** выберите предложение, а затем укажите платежную информацию и примите условия лицензионного соглашения.</span><span class="sxs-lookup"><span data-stu-id="b781b-216">On the **Add subscription** page, select an offer and complete the payment information and agreement.</span></span>
    
<span data-ttu-id="b781b-217">Если вы приобрели подписки на Azure и Office 365 отдельно и хотите получить доступ к клиенту Azure AD в Office 365, воспользуйтесь инструкциями в статье [Связывание клиента Office 365 с подпиской на Azure](https://channel9.msdn.com/Series/Microsoft-Azure-Tutorials/Associate-an-Office-365-tenant-with-an-Azure-subscription).</span><span class="sxs-lookup"><span data-stu-id="b781b-217">If you purchased Azure and Office 365 subscriptions separately and want to access the Office 365 Azure AD tenant from your Azure subscription, see the instructions in [Associate an Office 365 tenant with an Azure subscription](https://channel9.msdn.com/Series/Microsoft-Azure-Tutorials/Associate-an-Office-365-tenant-with-an-Azure-subscription).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="b781b-218">См. также</span><span class="sxs-lookup"><span data-stu-id="b781b-218">See Also</span></span>

[<span data-ttu-id="b781b-219">Ресурсы для администраторов, посвященные архитектуре Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="b781b-219">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)
  
[<span data-ttu-id="b781b-220">Руководства по лаборатории тестирования для принятия облачных решений</span><span class="sxs-lookup"><span data-stu-id="b781b-220">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="b781b-221">Архитектурные модели для SharePoint, Exchange, Skype для бизнеса и Lync</span><span class="sxs-lookup"><span data-stu-id="b781b-221">Architectural models for SharePoint, Exchange, Skype for Business, and Lync</span></span>](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[<span data-ttu-id="b781b-222">Гибридные решения</span><span class="sxs-lookup"><span data-stu-id="b781b-222">Hybrid solutions</span></span>](hybrid-solutions.md)
  
