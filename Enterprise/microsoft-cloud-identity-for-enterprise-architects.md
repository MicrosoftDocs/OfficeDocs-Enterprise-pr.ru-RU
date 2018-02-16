---
title: "Облачное удостоверение Майкрософт для корпоративных архитекторов"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Strat_O365_Enterprise
- O365ITProTrain
- Ent_Architecture
ms.assetid: d27b5085-7325-4ab9-9d9a-438908a65d2c
description: "Сводка. Разработка решения для работы с удостоверениями для облачных служб и платформ Майкрософт."
ms.openlocfilehash: 07a27a63972163948148da117084800171a304b7
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2018
---
# <a name="microsoft-cloud-identity-for-enterprise-architects"></a><span data-ttu-id="8c882-103">Облачное удостоверение Майкрософт для корпоративных архитекторов</span><span class="sxs-lookup"><span data-stu-id="8c882-103">Microsoft Cloud Identity for Enterprise Architects</span></span>

 <span data-ttu-id="8c882-104">**Сводка.** Разработка решения для работы с удостоверениями для облачных служб и платформ Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="8c882-104">**Summary:** Design your identity solution for Microsoft cloud services and platforms.</span></span>
  
<span data-ttu-id="8c882-p101">В этой статье представлены сведения для ИТ-архитекторов о создании системы удостоверений для организаций, использующих облачные службы и платформы Майкрософт. Вы также можете просмотреть эту статью в виде 5-страничного плаката и распечатать его на листах формата A3.</span><span class="sxs-lookup"><span data-stu-id="8c882-p101">This article describes what IT architects need to know about designing identity for organizations using Microsoft cloud services and platforms. You can also view this article as a 5-page poster and print it in tabloid format (also known as ledger, 11 x 17, or A3).</span></span>
  
<span data-ttu-id="8c882-107">[![Эскиз: модель идентификации в облаке Майкрософт](images/ffa145a1-97e6-4c36-b08b-01c4a4ae8b9b.png) 
](https://www.microsoft.com/download/details.aspx?id=54431)</span><span class="sxs-lookup"><span data-stu-id="8c882-107">[![Thumb image for Microsoft cloud identity model](images/ffa145a1-97e6-4c36-b08b-01c4a4ae8b9b.png) 
](https://www.microsoft.com/download/details.aspx?id=54431)</span></span>
  
<span data-ttu-id="8c882-108">![PDF-файл](images/ITPro_Other_PDFicon.png)[PDF](https://go.microsoft.com/fwlink/p/?LinkId=524586) | ![Файл Visio](images/ITPro_Other_VisioIcon.jpg)[Visio](https://download.microsoft.com/download/2/3/8/238228E6-9017-4F6C-BD3C-5559E6708F82/MSFT_cloud_architecture_identity.vsd) | ![Страница с версиями на других языках](images/e16c992d-b0f8-48ae-bf44-db7a9fcaab9e.png)[Другие языки](https://www.microsoft.com/download/details.aspx?id=54431)</span><span class="sxs-lookup"><span data-stu-id="8c882-108">![PDF file](images/ITPro_Other_PDFicon.png)[PDF](https://go.microsoft.com/fwlink/p/?LinkId=524586) | ![Visio file](images/ITPro_Other_VisioIcon.jpg)[Visio](https://download.microsoft.com/download/2/3/8/238228E6-9017-4F6C-BD3C-5559E6708F82/MSFT_cloud_architecture_identity.vsd) | ![See a page with versions in additional languages](images/e16c992d-b0f8-48ae-bf44-db7a9fcaab9e.png)[More languages](https://www.microsoft.com/download/details.aspx?id=54431)</span></span>
  
<span data-ttu-id="8c882-109">Все модели можно найти в статье [Ресурсы по ИТ-архитектуре Microsoft Cloud](microsoft-cloud-it-architecture-resources.md). Вы также можете просмотреть [материалы по схеме корпоративного облака Майкрософт для ИТ-менеджеров](https://aka.ms/cloudarchitecture).</span><span class="sxs-lookup"><span data-stu-id="8c882-109">You can also see all of the models in the [Microsoft Cloud IT architecture resources](microsoft-cloud-it-architecture-resources.md) and swipe through [Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers](https://aka.ms/cloudarchitecture).</span></span>
  
> [!NOTE]
> <span data-ttu-id="8c882-p102">Эта статья основана на версии плаката **Идентификация в облаке Майкрософт для корпоративных архитекторов** за январь 2016 г. Она не содержит изменения, внесенные в апреле 2016 г. и позже.</span><span class="sxs-lookup"><span data-stu-id="8c882-p102">This article reflects the January 2016 version of the **Microsoft cloud identity for enterprise architects** poster. It does not contain the changes for the April 2016 or later versions of the poster.</span></span>
  
## <a name="designing-identity-for-the-microsoft-cloud"></a><span data-ttu-id="8c882-112">Разработка идентификации для облака Майкрософт</span><span class="sxs-lookup"><span data-stu-id="8c882-112">Designing identity for the Microsoft cloud</span></span>

<span data-ttu-id="8c882-p103">Интеграция удостоверений с облаком Майкрософт предоставляет доступ к широкому выбору служб и облачных платформ. Существует два основных сценария:</span><span class="sxs-lookup"><span data-stu-id="8c882-p103">Integrating your identities with the Microsoft cloud provides access to a broad range of services and cloud platform options. There are two main options:</span></span>
  
- <span data-ttu-id="8c882-p104">Вы можете выполнить интеграцию с Microsoft Azure Active Directory (AD). В частности, вам придется синхронизировать локальные учетные записи с Azure AD, поставщиком удостоверений для облака Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="8c882-p104">You can integrate with Microsoft Azure Active Directory (AD). This involves synchronizing your on-premises accounts to Azure AD, the identity provider for the Microsoft cloud.</span></span>
    
- <span data-ttu-id="8c882-117">Вы можете расширить локальную среду доменных служб Active Directory (AD DS) на виртуальные машины, работающие в службах инфраструктуры Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="8c882-117">You can extend your on-premises Active Directory Domain Services (AD DS) environment to virtual machines running in Microsoft Azure infrastructure services.</span></span>
    
![Параметры для разработки облачных удостоверений](images/08277e96-e4d2-43cb-a56f-a11c7647881a.png)
  
 <span data-ttu-id="8c882-119">**Рисунок 1. Варианты разработки удостоверений в облаке**</span><span class="sxs-lookup"><span data-stu-id="8c882-119">**Figure 1: Options for designing your identities in the cloud**</span></span>
  
<span data-ttu-id="8c882-120">На рис. 1 показано, что служба Azure AD является поставщиком удостоверений для служб "программное обеспечение как услуга" (SaaS) от Майкрософт и приложений Azure "платформа как услуга" (PaaS), а бизнес-приложения могут использовать локальные службы AD DS.</span><span class="sxs-lookup"><span data-stu-id="8c882-120">Figure 1 shows how Azure AD is the identity provider for Microsoft Software as a Service (SaaS) services and Azure Platform as a Service (PaaS) applications and how line-of-business applications can use on-premises AD DS.</span></span> 
  
### <a name="azure-active-directory"></a><span data-ttu-id="8c882-121">Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="8c882-121">Azure Active Directory</span></span>

<span data-ttu-id="8c882-p105">Microsoft Azure AD это размещаемая в облаке Майкрософт служба удостоверений и управления доступом. Она находится в центре облачных служб и платформ Майкрософт. Интеграция Azure AD предоставляет доступ ко всем SaaS-службам Майкрософт с помощью текущего набора учетных записей и паролей. Такая интеграция также предоставляет облачное удостоверение для приложений Azure PaaS.</span><span class="sxs-lookup"><span data-stu-id="8c882-p105">Microsoft Azure AD is the Microsoft cloud-hosted identity and access management service. It's at the center of Microsoft cloud services and platforms. Integrating with Azure AD provides access to all of the Microsoft SaaS services using your current set of accounts and passwords. That integration also provides cloud-based identity for Azure PaaS applications.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="8c882-126">Azure AD не избавляет от необходимости использовать локальные доменные службы Active Directory для предприятий или виртуальных машин под управлением Windows, работающих в Azure "инфраструктура как услуга" (IaaS).</span><span class="sxs-lookup"><span data-stu-id="8c882-126">Azure AD does not replace the need for AD DS on-premises for enterprise organizations or for Windows -based virtual machines running in Azure Infrastructure as a Service (IaaS).</span></span> 
  
<span data-ttu-id="8c882-127">Существует три выпуска Azure AD: бесплатный, базовый и расширенный.</span><span class="sxs-lookup"><span data-stu-id="8c882-127">There are three editions of Azure AD: Free, Basic, and Premium.</span></span> 
  
||||
|:-----|:-----|:-----|
|<span data-ttu-id="8c882-128">**Бесплатно**</span><span class="sxs-lookup"><span data-stu-id="8c882-128">**Free**</span></span> <br/> |<span data-ttu-id="8c882-129">**Базовый**</span><span class="sxs-lookup"><span data-stu-id="8c882-129">**Basic**</span></span> <br/> |<span data-ttu-id="8c882-130">**Расширенный**</span><span class="sxs-lookup"><span data-stu-id="8c882-130">**Premium**</span></span> <br/> |
| <span data-ttu-id="8c882-131">	Управление учетными записями пользователей</span><span class="sxs-lookup"><span data-stu-id="8c882-131">Manage user accounts</span></span> <br/>  <span data-ttu-id="8c882-132">Синхронизация с локальными каталогами</span><span class="sxs-lookup"><span data-stu-id="8c882-132">Synchronize with on-premises directories</span></span> <br/>  <span data-ttu-id="8c882-133">Единый вход в Azure, Office 365 и тысячах других популярных приложений SaaS, например Salesforce, Workday, Concur, DocuSign, Google Apps, Box, ServiceNow, Dropbox и многих других</span><span class="sxs-lookup"><span data-stu-id="8c882-133">Single sign-on across Azure, Office 365, and thousands of other popular SaaS applications, such as Salesforce, Workday, Concur, DocuSign, Google Apps, Box, ServiceNow, Dropbox, and more</span></span> <br/> | <span data-ttu-id="8c882-134">Включает все возможности бесплатного выпуска, а также:</span><span class="sxs-lookup"><span data-stu-id="8c882-134">Includes all of the abilities in the Free edition, plus:</span></span> <br/>  <span data-ttu-id="8c882-135">Фирменная символика</span><span class="sxs-lookup"><span data-stu-id="8c882-135">Company branding</span></span> <br/>  <span data-ttu-id="8c882-136">Групповой доступ к приложениям</span><span class="sxs-lookup"><span data-stu-id="8c882-136">Group-based application access</span></span> <br/>  <span data-ttu-id="8c882-137">Самостоятельный сброс пароля</span><span class="sxs-lookup"><span data-stu-id="8c882-137">Self-service password reset</span></span> <br/>  <span data-ttu-id="8c882-138">Корпоративное соглашение об уровне обслуживания 99,9 %</span><span class="sxs-lookup"><span data-stu-id="8c882-138">Enterprise SLA of 99.9%</span></span> <br/> | <span data-ttu-id="8c882-139">Включает все функции бесплатного и базового выпусков, а также:</span><span class="sxs-lookup"><span data-stu-id="8c882-139">Includes all of the features of the Free and Basic editions, plus:</span></span> <br/>  <span data-ttu-id="8c882-140">Самостоятельное управление группами</span><span class="sxs-lookup"><span data-stu-id="8c882-140">Self-service group management</span></span> <br/>  <span data-ttu-id="8c882-141">	Расширенные отчеты и оповещения безопасности</span><span class="sxs-lookup"><span data-stu-id="8c882-141">Advanced security reports and alerts</span></span> <br/>  <span data-ttu-id="8c882-142">Многофакторная проверка подлинности.</span><span class="sxs-lookup"><span data-stu-id="8c882-142">Multi-factor authentication</span></span> <br/>  <span data-ttu-id="8c882-143">Сброс пароля с обратной записью в локальные службы AD DS</span><span class="sxs-lookup"><span data-stu-id="8c882-143">Password reset with write-back to on-premises AD DS</span></span> <br/>  <span data-ttu-id="8c882-144">Двунаправленная синхронизация с помощью средства Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="8c882-144">Azure AD Connect tool bidirectional synchronization</span></span> <br/>  <span data-ttu-id="8c882-145">Прокси приложения Azure AD</span><span class="sxs-lookup"><span data-stu-id="8c882-145">Azure AD Application Proxy</span></span> <br/>  <span data-ttu-id="8c882-146">	Microsoft Forefront Identity Manager (MIM)</span><span class="sxs-lookup"><span data-stu-id="8c882-146">Microsoft Forefront Identity Manager (MIM)</span></span> <br/> |
   
<span data-ttu-id="8c882-147">Дополнительные сведения о версиях см. в статье [Выпуски Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524280).</span><span class="sxs-lookup"><span data-stu-id="8c882-147">For more information about versions, see [Azure Active Directory editions](https://go.microsoft.com/fwlink/p/?LinkId=524280).</span></span>
  
### <a name="option-1-integrate-with-azure-active-directory"></a><span data-ttu-id="8c882-148">Вариант 1. Интеграция с Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="8c882-148">Option 1: Integrate with Azure Active Directory</span></span>

<span data-ttu-id="8c882-p106">Большинство организаций синхронизируют стандартный набор объектов и атрибутов со своим клиентом Azure AD. Средство Azure AD Connect синхронизирует учетные записи между локальными службами AD DS и клиентом Azure AD.</span><span class="sxs-lookup"><span data-stu-id="8c882-p106">Most organizations synchronize a standard set of objects and attributes to their Azure AD tenant. The Azure AD Connect tool synchronizes your accounts between on-premises AD DS and an Azure AD tenant.</span></span>
  
![Интеграция с Azure AD](images/3ce05e49-2cb6-4cdc-99ab-d96c5bd12fe8.png)
  
 <span data-ttu-id="8c882-152">**Рисунок 2. Интеграция с Azure AD**</span><span class="sxs-lookup"><span data-stu-id="8c882-152">**Figure 2: Integrating with Azure AD**</span></span>
  
<span data-ttu-id="8c882-p107">На рис. 2 показано, как средство Azure AD Connect получает изменения AD DS и отправляет их в клиент Azure AD. В этом случае клиент Azure AD является размещаемой в облаке копией важного содержимого локальных каталогов.</span><span class="sxs-lookup"><span data-stu-id="8c882-p107">Figure 2 shows how the Azure AD Connect tool obtains AD DS changes and sends them to your Azure AD tenant. In this case, your Azure AD tenant is a cloud-hosted duplicate of essential on-premises directory content.</span></span>
  
<span data-ttu-id="8c882-p108">Во многих организациях AD DS используется в качестве локального поставщика удостоверений. В локальной среде можно использовать поставщик удостоверений другого типа (например, с использованием LDAP) и синхронизировать эти удостоверения с Azure AD.</span><span class="sxs-lookup"><span data-stu-id="8c882-p108">Many organizations use AD DS as their on-premises identity provider. You can use a different type of identity provider on-premises (such as one that uses LDAP), and synchronize these to Azure AD.</span></span>
  
### <a name="option-2-extend-ad-ds-to-azure"></a><span data-ttu-id="8c882-157">Вариант 2. Расширение доменных служб Active Directory в Azure</span><span class="sxs-lookup"><span data-stu-id="8c882-157">Option 2: Extend AD DS to Azure</span></span>

<span data-ttu-id="8c882-p109">По сравнению с синхронизацией с Azure AD, при расширении AD DS на виртуальные машины в службах инфраструктуры Azure поддерживается другой набор решений и приложений. Вот два из них:</span><span class="sxs-lookup"><span data-stu-id="8c882-p109">Extending AD DS to virtual machines running in Azure infrastructure services supports a different set of solutions and applications compared to synchronization with Azure AD. Here are two:</span></span>
  
- <span data-ttu-id="8c882-160">Поддерживаются облачные решения, которым требуется проверка подлинности NTLM или Kerberos, или присоединенные к домену AD DS виртуальные машины.</span><span class="sxs-lookup"><span data-stu-id="8c882-160">Supports cloud-based solutions that require NTLM or Kerberos authentication, or AD DS domain-joined virtual machines.</span></span>
    
- <span data-ttu-id="8c882-161">Дополнительный потенциал интеграции для облачных служб и приложений в облачных службах и платформах Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="8c882-161">Adds additional integration potential for cloud services and applications across Microsoft cloud services and platforms.</span></span>
    
![Расширение доменных служб Active Directory в Azure](images/4675cf17-962c-4840-b1dc-bbd1d8894a27.png)
  
 <span data-ttu-id="8c882-163">**Рисунок 3. Расширение доменных служб Active Directory в Azure**</span><span class="sxs-lookup"><span data-stu-id="8c882-163">**Figure 3: Extending AD DS to Azure**</span></span>
  
<span data-ttu-id="8c882-p110">На рис. 3 показан контроллер домена AD DS, подключенный к виртуальной сети Azure через локальное VPN-устройство и VPN-шлюз Azure. Виртуальная сеть Azure содержит серверы для бизнес-приложения и собственный набор контроллеров доменов AD DS.</span><span class="sxs-lookup"><span data-stu-id="8c882-p110">Figure 3 shows an AD DS domain controller connected to an Azure virtual network through an on-premises VPN device and an Azure VPN gateway. The Azure virtual network contains servers for a line-of-business application and its own set of AD DS domain controllers.</span></span>
  
### <a name="more-information"></a><span data-ttu-id="8c882-166">Дополнительные сведения</span><span class="sxs-lookup"><span data-stu-id="8c882-166">More Information</span></span>

- [<span data-ttu-id="8c882-167">Синхронизация каталога с Office 365  это просто!</span><span class="sxs-lookup"><span data-stu-id="8c882-167">Synchronizing your directory with Office 365 is easy</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524281)
    
- [<span data-ttu-id="8c882-168">Инфографика. Управление удостоверениями и доступом в облаке</span><span class="sxs-lookup"><span data-stu-id="8c882-168">Infographic: Cloud identity and access management</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524282)
    
- [<span data-ttu-id="8c882-169">Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="8c882-169">Azure Active Directory</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524283)
    
## <a name="integrate-your-on-premises-ad-ds-accounts-with-microsoft-azure-ad"></a><span data-ttu-id="8c882-170">Интеграция локальных учетных записей AD DS с Microsoft Azure AD</span><span class="sxs-lookup"><span data-stu-id="8c882-170">Integrate your on-premises AD DS accounts with Microsoft Azure AD</span></span>

<span data-ttu-id="8c882-171">После синхронизации локальных учетных записей AD DS с Azure AD пользователи смогут использовать свои локальные учетные записи AD DS для доступа:</span><span class="sxs-lookup"><span data-stu-id="8c882-171">By synchronizing your on-premises AD DS accounts with Azure AD, your users can use their on-premises AD DS accounts to access:</span></span>
  
- <span data-ttu-id="8c882-172">ко всем SaaS-службам Майкрософт (Office 365, Microsoft Intune и Dynamics CRM Online);</span><span class="sxs-lookup"><span data-stu-id="8c882-172">All of the Microsoft SaaS services (Office 365, Microsoft Intune, and Dynamics CRM Online)</span></span>
    
- <span data-ttu-id="8c882-173">к приложениям, работающим в Azure PaaS.</span><span class="sxs-lookup"><span data-stu-id="8c882-173">Your applications running in Azure PaaS</span></span>
    
<span data-ttu-id="8c882-174">Два способа настройки этой интеграции:</span><span class="sxs-lookup"><span data-stu-id="8c882-174">There are two ways to configure this integration:</span></span>
  
- <span data-ttu-id="8c882-175">синхронизация каталогов и паролей;</span><span class="sxs-lookup"><span data-stu-id="8c882-175">Directory and password synchronization</span></span>
    
- <span data-ttu-id="8c882-176">федерация и единый вход.</span><span class="sxs-lookup"><span data-stu-id="8c882-176">Federation and single sign-on</span></span>
    
<span data-ttu-id="8c882-p111">Начните с простейшего варианта, который соответствует вашим требованиям. При необходимости вы можете переключаться между этими вариантами.</span><span class="sxs-lookup"><span data-stu-id="8c882-p111">Start with the simplest option that meets your needs. You can switch between these options, if needed.</span></span>
  
> [!NOTE]
> <span data-ttu-id="8c882-179">В организациях корпоративного уровня не рекомендуется использовать облачные учетные записи (без интеграции с локальными доменными службами Active Directory).</span><span class="sxs-lookup"><span data-stu-id="8c882-179">Using cloud-only accounts (not integrating with your on-premises AD DS) is not recommended for enterprise-scale organizations.</span></span> 
  
### <a name="directory-and-password-synchronization"></a><span data-ttu-id="8c882-180">синхронизация каталогов и паролей;</span><span class="sxs-lookup"><span data-stu-id="8c882-180">Directory and password synchronization</span></span>

<span data-ttu-id="8c882-181">Это самый простой вариант, для которого требуется только сервер со средством Azure AD Connect.</span><span class="sxs-lookup"><span data-stu-id="8c882-181">This is the simplest option and requires only a server running the Azure AD Connect tool.</span></span> 
  
![Конфигурация синхронизации каталогов и паролей](images/e7dcfe8f-dab5-461e-89cc-d7a48f58dc0f.png)
  
 <span data-ttu-id="8c882-183">**Рисунок 4. Конфигурация синхронизации каталогов и паролей**</span><span class="sxs-lookup"><span data-stu-id="8c882-183">**Figure 4: Directory and password synchronization configuration**</span></span>
  
<span data-ttu-id="8c882-p112">На рис. 4 показан локальный или частный облачный центр обработки данных с контроллером домена AD DS. Сервер, на котором запущено средство Azure AD Connect, синхронизирует список имен учетных записей с Azure AD.</span><span class="sxs-lookup"><span data-stu-id="8c882-p112">Figure 4 shows an on-premises or private cloud datacenter with an AD DS domain controller. A server running the Azure AD Connect tool synchronizes the list of account names with Azure AD.</span></span>
  
<span data-ttu-id="8c882-186">При использовании этого варианта:</span><span class="sxs-lookup"><span data-stu-id="8c882-186">With this option:</span></span>
  
- <span data-ttu-id="8c882-p113">Учетные записи пользователей из локальных доменных служб Active Directory (или другого поставщика удостоверений) синхронизируются с клиентом Azure AD. Локальный каталог остается полномочным источником учетных записей, в котором вы управляете всеми их изменениями.</span><span class="sxs-lookup"><span data-stu-id="8c882-p113">User accounts are synchronized from your on-premises AD DS (or other identity provider) to your Azure AD tenant. The on-premises directory remains the authoritative source for accounts and you manage all account changes from there.</span></span>
    
- <span data-ttu-id="8c882-189">Azure AD выполняет все проверки подлинности для SaaS-служб Майкрософт и приложений Azure PaaS.</span><span class="sxs-lookup"><span data-stu-id="8c882-189">Azure AD performs all authentication for Microsoft SaaS-based services and Azure PaaS applications.</span></span>
    
- <span data-ttu-id="8c882-190">Вы также можете настроить синхронизацию для нескольких лесов AD DS.</span><span class="sxs-lookup"><span data-stu-id="8c882-190">You can also configure synchronization for multiple AD DS forests.</span></span>
    
<span data-ttu-id="8c882-191">Если используется синхронизация паролей:</span><span class="sxs-lookup"><span data-stu-id="8c882-191">With password synchronization:</span></span>
  
- <span data-ttu-id="8c882-192">При доступе к облачным службам пользователям предлагается ввести тот же пароль, который они используют для локальных ресурсов.</span><span class="sxs-lookup"><span data-stu-id="8c882-192">Users are prompted to enter a password when accessing cloud services, which is the same password that they use for on-premises resources.</span></span>
    
- <span data-ttu-id="8c882-p114">Пароли пользователей никогда не отправляются в Azure AD открытым текстом. Вместо этого используется хэш пароля. Его криптографически невозможно расшифровать или реконструировать, чтобы получить открытый текст пароля.</span><span class="sxs-lookup"><span data-stu-id="8c882-p114">User passwords are never sent as cleartext to Azure AD. Instead, a hash of the password is used. It is cryptographically impossible to decrypt or reverse-engineer the password hash and obtain the cleartext password.</span></span> 
    
<span data-ttu-id="8c882-196">При многофакторной проверке подлинности (MFA):</span><span class="sxs-lookup"><span data-stu-id="8c882-196">With multi-factor authentication (MFA):</span></span>
  
- <span data-ttu-id="8c882-197">Вы можете пользоваться основными функциями MFA, включенными в Office 365.</span><span class="sxs-lookup"><span data-stu-id="8c882-197">You can take advantage of basic MFA features offered with Office 365.</span></span>
    
- <span data-ttu-id="8c882-198">Разработчики приложений Azure PaaS могут пользоваться преимуществами службы многофакторной проверки подлинности Azure.</span><span class="sxs-lookup"><span data-stu-id="8c882-198">Azure PaaS application developers can take advantage of the Azure Multi-Factor Authentication service.</span></span>
    
<span data-ttu-id="8c882-199">Синхронизация каталогов не обеспечивает интеграцию с локальными решениями MFA.</span><span class="sxs-lookup"><span data-stu-id="8c882-199">Directory synchronization does not provide integration with on-premises MFA solutions.</span></span>
  
### <a name="federation-and-single-sign-on"></a><span data-ttu-id="8c882-200">федерация и единый вход.</span><span class="sxs-lookup"><span data-stu-id="8c882-200">Federation and single sign-on</span></span>

<span data-ttu-id="8c882-201">Для этого варианта требуются дополнительные серверы и инфраструктура.</span><span class="sxs-lookup"><span data-stu-id="8c882-201">This option requires additional servers and infrastructure.</span></span> 
  
![Сервера, необходимые для федеративной проверки подлинности](images/1e54f0d2-e650-4eb5-957f-4f1d3c44da16.png)
  
 <span data-ttu-id="8c882-203">**Рисунок 5. Серверы, необходимые для федеративной проверки подлинности**</span><span class="sxs-lookup"><span data-stu-id="8c882-203">**Figure 5: Servers needed for federated authentication**</span></span>
  
<span data-ttu-id="8c882-p115">На рис. 5 показан набор компонентов для федеративной проверки подлинности. Azure AD связывается с прокси-службой веб-приложения, отправляющей запрос проверки подлинности на сервер служб федерации Active Directory (AD FS), который отправляет запрос контроллеру домена AD DS для оценки и ответа. Сервер, на котором запущено средство Azure AD Connect, синхронизирует список имен учетных записей из AD DS с Azure AD.</span><span class="sxs-lookup"><span data-stu-id="8c882-p115">Figure 5 shows the set of components for federated authentication. Azure AD contacts a web application proxy, which forwards the authentication request to an Active Directory Federation Services (AD FS) server, which forwards the request to an AD DS domain controller for evaluation and response. A server running the Azure AD Connect tool synchronizes the list of account names from AD DS to Azure AD.</span></span>
  
<span data-ttu-id="8c882-207">Федерация предоставляет предприятиям следующие дополнительные возможности:</span><span class="sxs-lookup"><span data-stu-id="8c882-207">Federation provides these additional enterprise capabilities:</span></span>
  
- <span data-ttu-id="8c882-208">Все запросы проверки подлинности, отправленные в Azure AD, направляются локальному поставщику удостоверений и выполняются в нем через AD FS.</span><span class="sxs-lookup"><span data-stu-id="8c882-208">All authentication requests sent to Azure AD are forwarded to and performed against the on-premises identity provider through AD FS.</span></span>
    
- <span data-ttu-id="8c882-209">Поддерживаются поставщики удостоверений сторонних поставщиков.</span><span class="sxs-lookup"><span data-stu-id="8c882-209">Works with non-Microsoft identity providers.</span></span>
    
- <span data-ttu-id="8c882-210">Синхронизация хэша паролей может служить запасным вариантом для федеративного входа (например, в случае сбоя федеративной проверки подлинности).</span><span class="sxs-lookup"><span data-stu-id="8c882-210">Password hash synchronization can act as a sign-in backup for federated sign-in (for example, if the federated authentication fails).</span></span>
    
<span data-ttu-id="8c882-211">Используйте федерацию, если:</span><span class="sxs-lookup"><span data-stu-id="8c882-211">Use federation if:</span></span>
  
- <span data-ttu-id="8c882-p116">Необходим единый вход. С единым входом пользователям не предлагается вводить учетные данные (имя пользователя и пароль) при доступе к облачной службе.</span><span class="sxs-lookup"><span data-stu-id="8c882-p116">Single sign-on is required. With single sign-on, users are not prompted to enter any credentials (user name or password), when accessing a cloud service.</span></span>
    
- <span data-ttu-id="8c882-214">Службы федерации Active Directory уже развернуты.</span><span class="sxs-lookup"><span data-stu-id="8c882-214">AD FS is already deployed.</span></span>
    
- <span data-ttu-id="8c882-215">Используется сторонний поставщик удостоверений.</span><span class="sxs-lookup"><span data-stu-id="8c882-215">You use a third-party identity provider.</span></span>
    
- <span data-ttu-id="8c882-216">Используется Forefront Identity Manager 2010 R2 (не поддерживается синхронизация хэша паролей).</span><span class="sxs-lookup"><span data-stu-id="8c882-216">You use Forefront Identity Manager 2010 R2 (does not support password hash synchronization).</span></span>
    
- <span data-ttu-id="8c882-217">У вас есть локальная встроенная смарт-карта или другое решение MFA.</span><span class="sxs-lookup"><span data-stu-id="8c882-217">You have an on-premises integrated smart card or other MFA solution.</span></span>
    
- <span data-ttu-id="8c882-218">Требуется аудит входа и/или отключение учетных записей.</span><span class="sxs-lookup"><span data-stu-id="8c882-218">You require sign-in audit and/or disablement of accounts.</span></span>
    
- <span data-ttu-id="8c882-219">Организации требуются ограничения входа клиентов по сетевому расположению или рабочим часам.</span><span class="sxs-lookup"><span data-stu-id="8c882-219">Your organization requires client sign-in restrictions by network location or work hours.</span></span>
    
- <span data-ttu-id="8c882-220">Организация должна соответствовать Федеральному стандарту обработки информации (FIPS).</span><span class="sxs-lookup"><span data-stu-id="8c882-220">You must comply with Federal Information Processing Standards (FIPS).</span></span>
    
<span data-ttu-id="8c882-221">Для федеративной проверки подлинности требуется больше инвестиций в локальную инфраструктуру.</span><span class="sxs-lookup"><span data-stu-id="8c882-221">Federated authentication requires a greater investment in infrastructure on-premises.</span></span>
  
- <span data-ttu-id="8c882-p117">Локальные серверы должны быть доступны из Интернета через корпоративный брандмауэр. Корпорация Майкрософт рекомендует использовать серверы прокси-служб веб-приложений, развернутые в сети периметра.</span><span class="sxs-lookup"><span data-stu-id="8c882-p117">The on-premises servers must be Internet-accessible through a corporate firewall. Microsoft recommends the use of Web Application Proxy servers deployed in your perimeter network.</span></span>
    
- <span data-ttu-id="8c882-224">Необходимы оборудование, лицензии и операции для серверов AD FS, прокси-серверов AD FS или серверов прокси-служб веб-приложений, брандмауэров и подсистем балансировки нагрузки.</span><span class="sxs-lookup"><span data-stu-id="8c882-224">Requires hardware, licenses, and operations for AD FS servers, AD FS proxy or Web Application Proxy servers, firewalls, and load balancers.</span></span> 
    
- <span data-ttu-id="8c882-225">Доступность и производительность важны, чтобы пользователи имели доступ к Office 365 и другим облачным приложениям.</span><span class="sxs-lookup"><span data-stu-id="8c882-225">Availability and performance are important to ensure users can access Office 365 and other cloud applications.</span></span>
    
### <a name="more-information"></a><span data-ttu-id="8c882-226">Дополнительные сведения</span><span class="sxs-lookup"><span data-stu-id="8c882-226">More Information</span></span>

- [<span data-ttu-id="8c882-227">Синхронизация каталога с Office 365  это просто!</span><span class="sxs-lookup"><span data-stu-id="8c882-227">Synchronizing your directory with Office 365 is easy</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524281)
    
- [<span data-ttu-id="8c882-228">Подготовка пользователей к работе путем синхронизации каталогов с Office 365</span><span class="sxs-lookup"><span data-stu-id="8c882-228">Prepare to provision users through directory synchronization to Office 365</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524284)
    
- [<span data-ttu-id="8c882-229">Многофакторная проверка подлинности для Office 365</span><span class="sxs-lookup"><span data-stu-id="8c882-229">Multi-Factor Authentication for Office 365</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=392012)
    
- [<span data-ttu-id="8c882-230">Многофакторная проверка подлинности Azure</span><span class="sxs-lookup"><span data-stu-id="8c882-230">Azure Multi-Factor Authentication</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524285)
    
- [<span data-ttu-id="8c882-231">TechEd 2014. Интеграция каталогов: создание одного каталога с Active Directory и Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="8c882-231">TechEd 2014: Directory Integration: Creating One Directory with Active Directory and Azure Active Directory</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524286)
    
## <a name="extend-ad-ds-to-azure"></a><span data-ttu-id="8c882-232">Расширение доменных служб Active Directory в Azure</span><span class="sxs-lookup"><span data-stu-id="8c882-232">Extend AD DS to Azure</span></span>

<span data-ttu-id="8c882-233">Расширение AD DS в Azure — это первый шаг к поддержке бизнес-приложений, выполняющихся на виртуальных машинах в службах инфраструктуры Azure, которые предоставляют:</span><span class="sxs-lookup"><span data-stu-id="8c882-233">Extending AD DS to Azure is the first step to support line-of-business applications running on virtual machines in Azure infrastructure services, which provides:</span></span>
  
- <span data-ttu-id="8c882-234">поддержку облачных решений, которым требуется проверка подлинности NTLM или Kerberos, либо виртуальных машин, присоединенных к домену AD DS;</span><span class="sxs-lookup"><span data-stu-id="8c882-234">Support for cloud-based solutions that require NTLM or Kerberos authentication, or AD DS domain-joined virtual machines.</span></span>
    
- <span data-ttu-id="8c882-235">дополнительный потенциал интеграции для облачных служб и приложений с возможностью добавления в любой момент.</span><span class="sxs-lookup"><span data-stu-id="8c882-235">Additional integration potential for cloud services and applications and can be added at any time.</span></span>
    
![Расширение доменных служб Active Directory в виртуальной сети Azure](images/9fe2e27d-7fc8-441a-a694-1db4b9f6d03f.png)
  
 <span data-ttu-id="8c882-237">**Рисунок 6. Расширение доменных служб Active Directory в виртуальной сети Azure**</span><span class="sxs-lookup"><span data-stu-id="8c882-237">**Figure 6: Extending AD DS to an Azure virtual network**</span></span>
  
<span data-ttu-id="8c882-p118">На рис. 6 показан локальный или частный облачный центр обработки данных с доменными службами Active Directory, подключенными к виртуальной сети Azure с подключением ExpressRoute или VPN-подключением типа "сеть-сеть". Виртуальная сеть Azure содержит серверы для бизнес-приложения и собственный набор контроллеров доменов AD DS. Эта конфигурация является гибридным развертыванием AD DS в локальной среде и службах инфраструктуры Azure. Для нее требуется следующее:</span><span class="sxs-lookup"><span data-stu-id="8c882-p118">Figure 6 shows an on-premises or private cloud datacenter with AD DS connected to an Azure virtual network with a site-to-site VPN or ExpressRoute connection. The Azure virtual network contains servers for a line-of-business application and its own set of AD DS domain controllers. This configuration is a hybrid deployment of AD DS on-premises and in Azure infrastructure services. It requires:</span></span>
  
- <span data-ttu-id="8c882-242">виртуальная сеть Azure;</span><span class="sxs-lookup"><span data-stu-id="8c882-242">An Azure virtual network.</span></span>
    
- <span data-ttu-id="8c882-243">соединение между устройством локальной виртуальной частной сети (VPN) или маршрутизатором и VPN-шлюзом Azure;</span><span class="sxs-lookup"><span data-stu-id="8c882-243">A connection between an on-premises virtual private network (VPN) device or router and an Azure VPN gateway.</span></span>
    
- <span data-ttu-id="8c882-244">часть локального пространства IP-адресов, отведенная под виртуальные машины в виртуальной сети;</span><span class="sxs-lookup"><span data-stu-id="8c882-244">Using a portion of your on-premises IP address space for the virtual machines in the virtual network.</span></span>
    
- <span data-ttu-id="8c882-245">развертывание одного или нескольких контроллеров доменов в виртуальной сети, назначенных серверами глобального каталога (это снижает исходящий трафик в VPN-подключении).</span><span class="sxs-lookup"><span data-stu-id="8c882-245">Deploying one or more domain controllers in the virtual network designated as global catalog servers (reduces egress traffic across the VPN connection).</span></span>
    
<span data-ttu-id="8c882-246">По сравнению с синхронизацией с Azure AD, эта архитектура удостоверений поддерживает другой набор решений и приложений.</span><span class="sxs-lookup"><span data-stu-id="8c882-246">This identity architecture supports a different set of solutions and applications compared to synchronization with Azure AD.</span></span>
  
### <a name="on-premises-to-azure-connection-options"></a><span data-ttu-id="8c882-247">Варианты подключения локальной среды к Azure</span><span class="sxs-lookup"><span data-stu-id="8c882-247">On-premises to Azure connection options</span></span>

<span data-ttu-id="8c882-248">Чтобы подключить локальную сеть к виртуальной сети Azure, вы можете использовать:</span><span class="sxs-lookup"><span data-stu-id="8c882-248">To connect your on-premises network to an Azure virtual network, you can use:</span></span>
  
- <span data-ttu-id="8c882-249">VPN-подключение типа "сеть-сеть", которое может объединить 1-10 сайтов (включая другие виртуальные сети Azure) в одну виртуальную сеть Azure;</span><span class="sxs-lookup"><span data-stu-id="8c882-249">A site-to-site VPN connection, which can connect 1-10 sites (including other Azure virtual networks) to a single Azure virtual network.</span></span>
    
- <span data-ttu-id="8c882-p119">ExpressRoute, частное, защищенное подключение глобальной сети к Azure через партнерскую сеть и поставщика служб центра обработки данных. Подключения ExpressRoute могут обеспечивать повышенную надежность, увеличенную пропускную способность и сокращенное время задержки.</span><span class="sxs-lookup"><span data-stu-id="8c882-p119">ExpressRoute, a private, secure WAN link to Azure through a partner network and datacenter services provider. ExpressRoute connections can offer increased reliability, higher bandwidth, and lower latencies.</span></span>
    
### <a name="more-information"></a><span data-ttu-id="8c882-252">Дополнительные сведения</span><span class="sxs-lookup"><span data-stu-id="8c882-252">More Information</span></span>

- [<span data-ttu-id="8c882-253">О безопасных распределенных подключениях для виртуальных сетей</span><span class="sxs-lookup"><span data-stu-id="8c882-253">Cross-premises connectivity for virtual networks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524293)
    
- [<span data-ttu-id="8c882-254">Технический обзор ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="8c882-254">ExpressRoute Technical Overview</span></span>](https://go.microsoft.com/fwlink/?LinkID=392081)
    
- [<span data-ttu-id="8c882-255">Руководства по развертыванию Windows Server Active Directory на виртуальных машинах Azure</span><span class="sxs-lookup"><span data-stu-id="8c882-255">Guidelines for Deploying Windows Server Active Directory on Azure Virtual Machines</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524295)
    
## <a name="integrate-your-applications-with-cloud-identities"></a><span data-ttu-id="8c882-256">Интеграция приложений с облачными удостоверениями</span><span class="sxs-lookup"><span data-stu-id="8c882-256">Integrate your applications with cloud identities</span></span>

<span data-ttu-id="8c882-p120">Во время проектирования и разработки приложений, работающих в облаке, следует ориентироваться на согласованность пользовательского интерфейса для процесса проверки подлинности, включая набор необходимых учетных данных. Например, при использовании учетных данных Windows в Azure AD или расширенных доменных службах Active Directory, убедитесь, что пользователи могут быстро пройти проверку подлинности и сосредоточиться на своих задачах.</span><span class="sxs-lookup"><span data-stu-id="8c882-p120">When designing and developing applications that run in the cloud, you should aim for consistency of the user experience for the authentication process, including the set of required credentials. For example, when using Windows credentials, whether against Azure AD or an extended AD DS, ensure that users can quickly authenticate and focus on their tasks.</span></span>
  
![Интеграция приложений с облачными удостоверениями](images/1e6304b0-fa15-4f80-a3b4-7507a28808ae.png)
  
 <span data-ttu-id="8c882-260">**Рисунок 7. Интеграция приложений с облачными удостоверениями**</span><span class="sxs-lookup"><span data-stu-id="8c882-260">**Figure 7: Integrate your applications with cloud identities**</span></span>
  
<span data-ttu-id="8c882-261">На рис. 7 показано три варианта интеграции приложения с облачными удостоверениями.</span><span class="sxs-lookup"><span data-stu-id="8c882-261">Figure 7 shows three options for integrating your application with cloud identities.</span></span>
  
1. <span data-ttu-id="8c882-262">Регистрация размещаемых в облаке приложений с Azure AD.</span><span class="sxs-lookup"><span data-stu-id="8c882-262">Register your cloud-hosted applications with Azure AD.</span></span>
    
    <span data-ttu-id="8c882-p121">См. статью [Интеграция приложений с Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524303) на портале MSDN. Это позволяет использовать Azure AD для проверки подлинности при доступе к приложению PaaS, а также позволяет пользователям или администраторам предоставлять права доступа к приложению, чтобы другие пользователи могли получать доступ к содержимому от их имени из других облачных служб, например Office 365. Дополнительные сведения и примеры кода можно найти в статье[Сценарии проверки подлинности в Azure AD](https://go.microsoft.com/fwlink/p/?LinkId=524304) на портале MSDN.</span><span class="sxs-lookup"><span data-stu-id="8c882-p121">See the MSDN article [Integrating Applications with Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524303). This lets you use Azure AD to authenticate access to your PaaS application, as well as allowing users or administrators to grant rights to your application to access content on their behalf from other cloud services, such as Office 365. More details and code samples can be found in the MSDN article [Authentication Scenarios for Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524304).</span></span> 
    
2. <span data-ttu-id="8c882-266">Приложения, которым необходима программная проверка подлинности для доступа к приложению, защищенному с помощью AD DS, AD FS на сервере Windows Server 2012 R2 или Azure AD, могут использовать:</span><span class="sxs-lookup"><span data-stu-id="8c882-266">Applications that require programmatic authentication to gain access to an application secured by AD SD, AD FS on Windows Server 2012 R2, or Azure AD can use:</span></span>
    
  - <span data-ttu-id="8c882-267">[Azure AD Graph API](https://go.microsoft.com/fwlink/p/?LinkId=524305);</span><span class="sxs-lookup"><span data-stu-id="8c882-267">The [Azure AD Graph API](https://go.microsoft.com/fwlink/p/?LinkId=524305)</span></span>
    
  - <span data-ttu-id="8c882-268">[библиотеку проверки подлинности Active Directory (ADAL)](https://go.microsoft.com/fwlink/p/?LinkID=524297).</span><span class="sxs-lookup"><span data-stu-id="8c882-268">[Active Directory Authentication Library (ADAL)](https://go.microsoft.com/fwlink/p/?LinkID=524297)</span></span>
    
    <span data-ttu-id="8c882-p122">Azure AD Graph API поддерживает OAuth и OpenID Connect. Этот интерфейс также поддерживает приложения PaaS.</span><span class="sxs-lookup"><span data-stu-id="8c882-p122">The Azure AD Graph API supports OAuth and OpenID Connect. It also works with PaaS applications.</span></span>
    
3. <span data-ttu-id="8c882-p123">Настройте локальные приложения или бизнес-приложения, работающие на виртуальных машинах в виртуальной сети Azure, на непосредственное использование проверки подлинности Windows (NTLM или Kerberos). Это обеспечивает максимальное удобство для пользователей и упрощает настройку для разработчиков серверных приложений.</span><span class="sxs-lookup"><span data-stu-id="8c882-p123">Configure on-premises applications or line-of-business applications running on virtual machines in an Azure virtual network to use Windows authentication (NTLM or Kerberos) directly. This is the best experience for users and requires the least configuration for server application developers.</span></span>
    
### <a name="application-integration-example"></a><span data-ttu-id="8c882-273">Пример интеграции приложений</span><span class="sxs-lookup"><span data-stu-id="8c882-273">Application integration example</span></span>

<span data-ttu-id="8c882-p124">Организация создает приложение ASP.NET, которое открывает конечную точку REST, где другие приложения могут получать последние данные о продажах. Доступ к этой конечной точке REST защищен с помощью Azure AD. Приложения должны предоставлять учетные данные, которые может проверить служба Azure AD, прежде чем приложение ASP.NET отправит запрашиваемые данные. Затем другие разработчики в организации могут создавать собственные приложения, использующие данные о продажах из конечной точки REST.</span><span class="sxs-lookup"><span data-stu-id="8c882-p124">An organization builds an ASP.NET application that exposes a REST endpoint where other applications can obtain the latest sales data. Access to that REST endpoint is secured with Azure AD. Applications must provide credentials that can be authenticated by Azure AD before the ASP.NET application sends the requested data. Other developers in the organization can then write their own applications that use the sales data from the REST endpoint.</span></span>
  
<span data-ttu-id="8c882-p125">Чтобы пройти проверку подлинности в Azure AD и получить данные, ADAL управляет процессом проверки подлинности пользователя и передает маркер доступа приложению, чтобы его можно было использовать для доступа к данным о продажах. ADAL избавляет от большинства сложностей, связанных с получением и анализом маркеров, потоков OAuth и других элементов. ADAL — это еще одна стремительно развивающаяся технология, поэтому разработчикам следует искать последнюю версию на сайте NuGet.</span><span class="sxs-lookup"><span data-stu-id="8c882-p125">To authenticate to Azure AD and retrieve data, ADAL manages the user authentication process and hands the access token off to the application so it can be used to gain access to the sales data. ADAL abstracts out much of the complexity of obtaining and parsing tokens, OAuth flows, and other elements. ADAL is another technology solution that is rapidly changing so developers should look for the latest version on NuGet.</span></span>
  
## <a name="deploying-directory-components-in-azure"></a><span data-ttu-id="8c882-281">Развертывание компонентов каталога в Azure</span><span class="sxs-lookup"><span data-stu-id="8c882-281">Deploying directory components in Azure</span></span>

<span data-ttu-id="8c882-p126">Вы можете развертывать компоненты каталогов, например серверы для синхронизации паролей или федеративной проверки подлинности, в виртуальной сети Azure, а не в локальном центре обработки данных. Учитывайте ее преимущества, особенно если вы планируете расширить AD DS в Azure.</span><span class="sxs-lookup"><span data-stu-id="8c882-p126">You can deploy directory components, such as servers for password synchronization or federated authentication, in an Azure virtual network rather than an on-premises datacenter. Consider its benefits, especially if you plan to extend AD DS into Azure.</span></span>
  
<span data-ttu-id="8c882-284">В виртуальную сеть Azure можно поместить следующие компоненты:</span><span class="sxs-lookup"><span data-stu-id="8c882-284">Here are the directory components that can be put in an Azure virtual network:</span></span>
  
- <span data-ttu-id="8c882-285">средство Azure AD Connect;</span><span class="sxs-lookup"><span data-stu-id="8c882-285">Azure AD Connect tool</span></span>
    
- <span data-ttu-id="8c882-286">компоненты федеративной проверки подлинности;</span><span class="sxs-lookup"><span data-stu-id="8c882-286">Federated authentication components</span></span>
    
- <span data-ttu-id="8c882-287">автономная среда AD DS.</span><span class="sxs-lookup"><span data-stu-id="8c882-287">A standalone AD DS environment</span></span>
    
### <a name="ad-connect-tool"></a><span data-ttu-id="8c882-288">Средство AD Connect</span><span class="sxs-lookup"><span data-stu-id="8c882-288">AD Connect tool</span></span>

<span data-ttu-id="8c882-p127">Средство Azure AD Connect можно разместить в облачной виртуальной сети Azure. Учитывайте следующие преимущества развертывания этой рабочей нагрузки в Azure:</span><span class="sxs-lookup"><span data-stu-id="8c882-p127">The Azure AD Connect tool can be hosted in the cloud on an Azure virtual network. Consider these benefits of deploying this workload to Azure:</span></span>
  
- <span data-ttu-id="8c882-291">потенциально ускоренная подготовка и сниженная стоимость операций;</span><span class="sxs-lookup"><span data-stu-id="8c882-291">Potentially faster provisioning and lower cost of operations</span></span>
    
- <span data-ttu-id="8c882-292">Повышенная доступность</span><span class="sxs-lookup"><span data-stu-id="8c882-292">Increased availability</span></span>
    
![Средство AD Connect, работающее в службах инфраструктуры Azure](images/97593481-e06a-4e34-b8b5-cc63acb5f9f1.png)
  
 <span data-ttu-id="8c882-294">**Рисунок 8. Средство AD Connect, запущенное в Azure**</span><span class="sxs-lookup"><span data-stu-id="8c882-294">**Figure 8: The AD Connect tool running in Azure**</span></span>
  
<span data-ttu-id="8c882-p128">На рис. 8 показано средство AD Connect, работающее на виртуальной машине в виртуальной сети Azure, которая отправляет запрос изменений учетных записей локальному контроллеру домена AD DS, а затем отправляет эти изменения в Office 365. Это решение работает:</span><span class="sxs-lookup"><span data-stu-id="8c882-p128">Figure 8 shows the AD Connect tool running on a virtual machine in an Azure virtual network, which queries an on-premises AD DS domain controller for account changes and then sends those changes to Office 365. This solution works with:</span></span>
  
- <span data-ttu-id="8c882-297">со службами Office 365;</span><span class="sxs-lookup"><span data-stu-id="8c882-297">Office 365 services.</span></span>
    
- <span data-ttu-id="8c882-298">с приложениями Azure PaaS, доступными через Интернет;</span><span class="sxs-lookup"><span data-stu-id="8c882-298">Azure PaaS applications that are available over the Internet.</span></span>
    
- <span data-ttu-id="8c882-299">с бизнес-приложениями в Azure, доступными из локальных сред через подключение ExpressRoute или VPN-подключение типа "сеть-сеть".</span><span class="sxs-lookup"><span data-stu-id="8c882-299">Line-of-business applications in Azure that are available from on-premises environments through the site-to-site VPN or ExpressRoute connection.</span></span>
    
<span data-ttu-id="8c882-300">Дополнительные сведения см. в статье [Интеграция локальных удостоверений с Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524307).</span><span class="sxs-lookup"><span data-stu-id="8c882-300">For more information, see [Integrating your on-premises identities with Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524307).</span></span>
  
### <a name="federated-authentication-infrastructure"></a><span data-ttu-id="8c882-301">Инфраструктура федеративной проверки подлинности</span><span class="sxs-lookup"><span data-stu-id="8c882-301">Federated authentication infrastructure</span></span>

<span data-ttu-id="8c882-302">Если вы еще не развернули AD FS в локальной среде, учитывайте следующие преимущества развертывания рабочей нагрузки в Azure:</span><span class="sxs-lookup"><span data-stu-id="8c882-302">If you haven't already deployed AD FS on-premises, consider these benefits of deploying this workload to Azure:</span></span>
  
- <span data-ttu-id="8c882-303">Автономная проверка подлинности в облачных службах (без зависимостей от локальной среды).</span><span class="sxs-lookup"><span data-stu-id="8c882-303">Provides autonomy for authentication to cloud services (no on-premises dependencies)</span></span>
    
- <span data-ttu-id="8c882-304">Меньшее количество серверов и средств в локальной среде.</span><span class="sxs-lookup"><span data-stu-id="8c882-304">Reduces servers and tools hosted on-premises</span></span>
    
- <span data-ttu-id="8c882-305">Используется VPN-шлюз типа "сеть-сеть" в отказоустойчивом кластере с двумя узлами для подключения к Azure (новый).</span><span class="sxs-lookup"><span data-stu-id="8c882-305">Uses a site-to-site VPN gateway on a two-node failover cluster to connect to Azure (new)</span></span>
    
- <span data-ttu-id="8c882-306">Используется ACL, чтобы прокси-серверы приложений могли напрямую взаимодействовать только с AD FS, а не с контроллерами доменов или другими серверами.</span><span class="sxs-lookup"><span data-stu-id="8c882-306">Uses ACLs to ensure that Web Application Proxy servers can only communicate with AD FS, not domain controllers or other servers directly</span></span>
    
![Развертывание инфраструктуры федеративной проверки подлинности в Azure](images/4e023dd4-b9fb-403a-a8eb-069b56d7a65e.png)
  
 <span data-ttu-id="8c882-308">**Рисунок 9. Развертывание инфраструктуры федеративной проверки подлинности в Azure**</span><span class="sxs-lookup"><span data-stu-id="8c882-308">**Figure 9: Deploying your federated authentication infrastructure in Azure**</span></span>
  
<span data-ttu-id="8c882-p129">На рис. 9 показан набор локальных контроллеров доменов, которые реплицируют сведения из AD DS, с набором контроллеров доменов в виртуальной сети Azure. Средство Azure AD Connect. выполняющееся на сервере в виртуальной сети Azure, отправляет локальным контроллерам доменов запросы на изменения, а затем отправляет эти изменения в Azure AD. Входящие запросы проверки подлинности в Azure AD из SaaS-служб Майкрософт, приложений Azure PaaS и других облачных приложений отправляются во внешнюю подсистему балансировки нагрузки, которая направляет запрос набору серверов прокси-служб веб-приложений. Серверы прокси-служб веб-приложений отправляют запрос внешней подсистеме балансировки нагрузки, которая перенаправляет запрос набору серверов AD FS. Затем серверы AD FS перенаправляют запрос на контроллер домена, чтобы проверить учетные данные отправки.</span><span class="sxs-lookup"><span data-stu-id="8c882-p129">Figure 9 shows a set of on-premises domain controllers replicating AD DS information with a set of domain controllers in an Azure virtual network. The Azure AD Connect tool running on a server in the Azure virtual network queries the local domain controllers for changes and then sends those changes to Azure AD. Incoming authentication requests to Azure AD from Microsoft SaaS services, Azure PaaS applications, and other cloud applications are forwarded to an external load balancer, which forwards the request to a set of Web Application Proxy servers. The Web Application Proxy servers forward the request to an internal load balancer, which forwards the request to a set of AD FS servers. The AD FS servers then forward the request to a domain controller to validate the send credentials.</span></span>
  
 <span data-ttu-id="8c882-314">Это решение работает:</span><span class="sxs-lookup"><span data-stu-id="8c882-314">This solution works with:</span></span>
  
- <span data-ttu-id="8c882-315">с приложениями, требующими Kerberos;</span><span class="sxs-lookup"><span data-stu-id="8c882-315">Applications that require Kerberos</span></span>
    
- <span data-ttu-id="8c882-316">со всеми SaaS-службами Майкрософт;</span><span class="sxs-lookup"><span data-stu-id="8c882-316">All of Microsoft's SaaS services</span></span>
    
- <span data-ttu-id="8c882-317">с приложениями в Azure, имеющими доступ к Интернету;</span><span class="sxs-lookup"><span data-stu-id="8c882-317">Applications in Azure that are Internet-facing</span></span>
    
- <span data-ttu-id="8c882-318">с приложениями в Azure IaaS или PaaS, которым требуется проверка подлинности с набором учетных записей в доменных службах Active Directory организации.</span><span class="sxs-lookup"><span data-stu-id="8c882-318">Applications in Azure IaaS or PaaS that require authentication with the set of accounts in your organization's AD DS</span></span>
    
<span data-ttu-id="8c882-319">Дополнительные сведения см. в статье [Интеграция локальных удостоверений с Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524307).</span><span class="sxs-lookup"><span data-stu-id="8c882-319">For more information, see [Integrating your on-premises identities with Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524307).</span></span>
  
### <a name="standalone-ad-ds-environment-in-an-azure-virtual-network"></a><span data-ttu-id="8c882-320">Автономная среда AD DS в виртуальной сети Azure</span><span class="sxs-lookup"><span data-stu-id="8c882-320">Standalone AD DS environment in an Azure virtual network</span></span>

<span data-ttu-id="8c882-p130">Облачное приложение не всегда необходимо интегрировать с локальной средой. Например, автономный домен AD DS в виртуальной сети Azure поддерживает общедоступные приложения, например сайты Интернета.</span><span class="sxs-lookup"><span data-stu-id="8c882-p130">You don't always need to integrate a cloud application with your on-premises environment. For example, a standalone AD DS domain in an Azure virtual network supports applications that are public-facing, such as Internet sites.</span></span>
  
![Отдельная среда доменных служб Active Directory для серверного приложения](images/98c7349f-535d-4c9b-8de4-e580f6d573d4.png)
  
 <span data-ttu-id="8c882-324">**Рисунок 10. Отдельная среда доменных служб Active Directory для серверного приложения**</span><span class="sxs-lookup"><span data-stu-id="8c882-324">**Figure 10: A standalone AD DS environment for a server-based application**</span></span>
  
<span data-ttu-id="8c882-p131">На рис. 10 показана виртуальная сеть Azure, которая содержит серверы AD DS, а также предоставляет службы AD DS и DNS, с набором серверов, на которых размещается приложение. Это решение работает:</span><span class="sxs-lookup"><span data-stu-id="8c882-p131">Figure 10 shows an Azure virtual network hosting a set of AD DS servers, providing both AD DS and DNS services, with a set of servers that host an application. This solution works with:</span></span>
  
- <span data-ttu-id="8c882-327">с веб-сайтами и приложениями Интернета;</span><span class="sxs-lookup"><span data-stu-id="8c882-327">Internet-facing web sites and applications</span></span>
    
- <span data-ttu-id="8c882-328">с приложениями, требующими проверку подлинности NTLM или Kerberos;</span><span class="sxs-lookup"><span data-stu-id="8c882-328">Applications that require NTLM or Kerberos authentication</span></span>
    
- <span data-ttu-id="8c882-329">с приложениями на серверах под управлением Windows, требующих AD DS.</span><span class="sxs-lookup"><span data-stu-id="8c882-329">Applications running on Windows-based servers that require AD DS</span></span>
    
<span data-ttu-id="8c882-330">Дополнительные сведения см. в статье [Интеграция локальных удостоверений с Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524307).</span><span class="sxs-lookup"><span data-stu-id="8c882-330">For more information, see [Integrating your on-premises identities with Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524307).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="8c882-331">См. также</span><span class="sxs-lookup"><span data-stu-id="8c882-331">See Also</span></span>

[<span data-ttu-id="8c882-332">Ресурсы для администраторов, посвященные архитектуре Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="8c882-332">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="8c882-333">Стратегия Enterprise Cloud корпорации Майкрософт: ресурсы для лиц, принимающих решения в области ИТ</span><span class="sxs-lookup"><span data-stu-id="8c882-333">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



