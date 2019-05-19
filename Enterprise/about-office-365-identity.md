---
title: Модели удостоверений Office 365 и Azure Active Directory
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-identity-device-management
- M365-security-compliance
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 06a189e7-5ec6-4af2-94bf-a22ea225a7a9
description: Сведения об управлении удостоверениями пользователей в Office 365.
ms.openlocfilehash: 1d4a2f40ebae9fa87d59ee3f7c9b621b40b03640
ms.sourcegitcommit: 36e760407a1f4b18bc108134628ed9a8d3e35a8a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/17/2019
ms.locfileid: "34162392"
---
# <a name="office-365-identity-models-and-azure-active-directory"></a><span data-ttu-id="afb5e-103">Модели удостоверений Office 365 и Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="afb5e-103">Office 365 identity models and Azure Active Directory</span></span>

<span data-ttu-id="afb5e-104">Office 365 использует Azure Active Directory (Azure AD), службу удостоверений и удостоверений пользователей на основе облачной службы проверки подлинности, включенную в вашу подписку на Office 365, для управления удостоверениями и проверкой подлинности для Office 365.</span><span class="sxs-lookup"><span data-stu-id="afb5e-104">Office 365 uses Azure Active Directory (Azure AD), a cloud-based user identity and authentication service that is included with your Office 365 subscription, to manage identities and authentication for Office 365.</span></span> <span data-ttu-id="afb5e-105">Правильная настройка инфраструктуры удостоверений крайне важна для управления доступом пользователей и разрешений Office 365 для Организации.</span><span class="sxs-lookup"><span data-stu-id="afb5e-105">Getting your identity infrastructure configured correctly is vital to managing Office 365 user access and permissions for your organization.</span></span>

<span data-ttu-id="afb5e-106">Прежде чем начать, просмотрите этот видеоролик, чтобы получить обзор моделей удостоверений и проверки подлинности для Office 365 и Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="afb5e-106">Before you begin, watch this video for an overview of identity models and authentication for both Office 365 and Microsoft 365.</span></span>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE2Pjwu]

<span data-ttu-id="afb5e-107">Первым вариантом планирования является модель удостоверений Office 365.</span><span class="sxs-lookup"><span data-stu-id="afb5e-107">Your first planning choice is the Office 365 identity model.</span></span>

## <a name="office-365-identity-models"></a><span data-ttu-id="afb5e-108">Модели удостоверений Office 365</span><span class="sxs-lookup"><span data-stu-id="afb5e-108">Office 365 identity models</span></span>

<span data-ttu-id="afb5e-109">Чтобы спланировать учетные записи пользователей, сначала необходимо ознакомиться с двумя моделями идентификации в Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="afb5e-109">To plan for user accounts, you first need to understand the two identity models in Microsoft 365.</span></span> <span data-ttu-id="afb5e-110">Вы можете поддерживать удостоверения вашей организации только в облаке, а также поддерживать локальные удостоверения доменных служб Active Directory (AD DS) и использовать их для проверки подлинности при доступе пользователей к Microsoft 365 Cloud Services.</span><span class="sxs-lookup"><span data-stu-id="afb5e-110">You can maintain your organization's identities only in the cloud, or you can maintain your on-premises Active Directory Domain Services (AD DS) identities and use them for authentication when users access Microsoft 365 cloud services.</span></span>  

<span data-ttu-id="afb5e-111">Ниже приведены два типа удостоверений, а также их наилучшее соответствие и преимущества.</span><span class="sxs-lookup"><span data-stu-id="afb5e-111">Here are the two types of identity and their best fit and benefits.</span></span>

|||
|:-------|:-----|:-----|
|  | <span data-ttu-id="afb5e-112">**Удостоверение только для облака**</span><span class="sxs-lookup"><span data-stu-id="afb5e-112">**Cloud-only identity**</span></span> | <span data-ttu-id="afb5e-113">**Гибридное удостоверение**</span><span class="sxs-lookup"><span data-stu-id="afb5e-113">**Hybrid identity**</span></span> |
| <span data-ttu-id="afb5e-114">**Определение**</span><span class="sxs-lookup"><span data-stu-id="afb5e-114">**Definition**</span></span> | <span data-ttu-id="afb5e-115">Учетная запись пользователя существует только в клиенте Azure Active Directory (Azure AD) для вашей подписки на Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="afb5e-115">User account only exists in the Azure Active Directory (Azure AD) tenant for your Microsoft 365 subscription.</span></span> | <span data-ttu-id="afb5e-116">Учетная запись пользователя существует в доменных службах Active Directory, а также копия в клиенте Azure AD для вашей подписки на Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="afb5e-116">User account exists in AD DS and a copy is also in the Azure AD tenant for your Microsoft 365 subscription.</span></span> <span data-ttu-id="afb5e-117">Учетная запись пользователя в Azure AD также может включать хешированную версию пароля учетной записи пользователя.</span><span class="sxs-lookup"><span data-stu-id="afb5e-117">The user account in Azure AD might also include a hashed version of the user account password.</span></span> |
| <span data-ttu-id="afb5e-118">**Проверка подлинности учетных данных пользователей в Microsoft 365**</span><span class="sxs-lookup"><span data-stu-id="afb5e-118">**How Microsoft 365 authenticates user credentials**</span></span> | <span data-ttu-id="afb5e-119">Клиент Azure AD для вашей подписки на Microsoft 365 выполняет проверку подлинности с учетной записью удостоверения в облаке.</span><span class="sxs-lookup"><span data-stu-id="afb5e-119">The Azure AD tenant for your Microsoft 365 subscription performs the authentication with the cloud identity account.</span></span> | <span data-ttu-id="afb5e-120">Клиент Azure AD для вашей подписки на Microsoft 365 обрабатывает процесс проверки подлинности или перенаправляет пользователя другому поставщику удостоверений.</span><span class="sxs-lookup"><span data-stu-id="afb5e-120">The Azure AD tenant for your Microsoft 365 subscription either handles the authentication process or redirects the user to another identity provider.</span></span> |
| <span data-ttu-id="afb5e-121">**Оптимально для**.</span><span class="sxs-lookup"><span data-stu-id="afb5e-121">**Best for**</span></span> | <span data-ttu-id="afb5e-122">Организации, которые не имеют локальных доменных служб Active Directory или не нуждаются в них.</span><span class="sxs-lookup"><span data-stu-id="afb5e-122">Organizations that do not have or need an on-premises AD DS.</span></span> | <span data-ttu-id="afb5e-123">Организации, использующие AD DS или другого поставщика удостоверений.</span><span class="sxs-lookup"><span data-stu-id="afb5e-123">Organizations using AD DS or another identity provider.</span></span> |
| <span data-ttu-id="afb5e-124">**Наибольшая выгода**</span><span class="sxs-lookup"><span data-stu-id="afb5e-124">**Greatest benefit**</span></span> | <span data-ttu-id="afb5e-125">Простота использования.</span><span class="sxs-lookup"><span data-stu-id="afb5e-125">Simple to use.</span></span> <span data-ttu-id="afb5e-126">Не требуются дополнительные средства каталогов или серверы.</span><span class="sxs-lookup"><span data-stu-id="afb5e-126">No extra directory tools or servers required.</span></span> | <span data-ttu-id="afb5e-127">Пользователи могут использовать одни и те же учетные данные при доступе к локальным или облачным ресурсам.</span><span class="sxs-lookup"><span data-stu-id="afb5e-127">Users can use the same credentials when accessing on-premises or cloud-based resources.</span></span> |
||||

## <a name="cloud-only-identity"></a><span data-ttu-id="afb5e-128">Удостоверение только для облака</span><span class="sxs-lookup"><span data-stu-id="afb5e-128">Cloud-only identity</span></span>

<span data-ttu-id="afb5e-129">Для удостоверения с единственным облаком используются учетные записи пользователей, существующие только в Azure AD.</span><span class="sxs-lookup"><span data-stu-id="afb5e-129">A cloud-only identity uses user accounts that exist only in Azure AD.</span></span> <span data-ttu-id="afb5e-130">Облачное удостоверение обычно используется малыми организациями, не имеющими локальных серверов, или не использующими AD DS для управления локальными удостоверениями.</span><span class="sxs-lookup"><span data-stu-id="afb5e-130">Cloud identity is typically used by small organizations that do not have on-premises servers or do not use AD DS to manage local identities.</span></span> 

<span data-ttu-id="afb5e-131">Ниже приведены основные компоненты удостоверения "только облако".</span><span class="sxs-lookup"><span data-stu-id="afb5e-131">Here are the basic components of cloud-only identity.</span></span>
 
![](./media/about-office-365-identity/cloud-only-identity.png)

<span data-ttu-id="afb5e-132">Как локальные, так и удаленные пользователи используют свои учетные записи пользователей и пароли Azure AD для доступа к облачным службам Office 365.</span><span class="sxs-lookup"><span data-stu-id="afb5e-132">Both on-premises and remote (online) users use their Azure AD user accounts and passwords to access Office 365 cloud services.</span></span> <span data-ttu-id="afb5e-133">Azure AD выполняет проверку подлинности учетных данных пользователя на основе сохраненных учетных записей пользователей и паролей.</span><span class="sxs-lookup"><span data-stu-id="afb5e-133">Azure AD authenticates user credentials based on its stored user accounts and passwords.</span></span>

### <a name="administration"></a><span data-ttu-id="afb5e-134">Администрирование</span><span class="sxs-lookup"><span data-stu-id="afb5e-134">Administration</span></span>
<span data-ttu-id="afb5e-135">Так как учетные записи пользователей хранятся только в Azure AD, управление облачными удостоверениями осуществляется с помощью таких средств, как [центр администрирования Microsoft 365](https://admin.microsoft.com) и Windows PowerShell, с помощью модуля PowerShell Azure Active Directory PowerShell для Graph.</span><span class="sxs-lookup"><span data-stu-id="afb5e-135">Because user accounts are only stored in Azure AD, you manage cloud identities with tools such as the [Microsoft 365 admin center](https://admin.microsoft.com) and Windows PowerShell with the Azure Active Directory PowerShell for Graph module.</span></span> 

## <a name="hybrid-identity"></a><span data-ttu-id="afb5e-136">Гибридное удостоверение</span><span class="sxs-lookup"><span data-stu-id="afb5e-136">Hybrid identity</span></span>

<span data-ttu-id="afb5e-137">Гибридное удостоверение использует учетные записи, созданные в локальных доменных службах Active Directory и имеющие копию в клиенте Azure AD подписки на Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="afb5e-137">Hybrid identity uses accounts that originate in an on-premises AD DS and have a copy in the Azure AD tenant of a Microsoft 365 subscription.</span></span> <span data-ttu-id="afb5e-138">Однако большинство изменений переходят только один из них.</span><span class="sxs-lookup"><span data-stu-id="afb5e-138">However, most changes only flow one way.</span></span> <span data-ttu-id="afb5e-139">Изменения, вносимые в учетные записи пользователей доменных служб Active Directory, синхронизируются с их копией в Azure AD.</span><span class="sxs-lookup"><span data-stu-id="afb5e-139">Changes that you make to AD DS user accounts are synchronized to their copy in Azure AD.</span></span> <span data-ttu-id="afb5e-140">Но изменения, внесенные в облачные учетные записи в Azure AD, такие как новые учетные записи пользователей, не синхронизируются с AD DS.</span><span class="sxs-lookup"><span data-stu-id="afb5e-140">But changes made to cloud-based accounts in Azure AD, such as new user accounts, are not synchronized with AD DS.</span></span>

<span data-ttu-id="afb5e-141">Azure AD Connect обеспечивает текущую синхронизацию учетных записей.</span><span class="sxs-lookup"><span data-stu-id="afb5e-141">Azure AD Connect provides the ongoing account synchronization.</span></span> <span data-ttu-id="afb5e-142">Он выполняется на локальном сервере, проверяет изменения в доменных СЛУЖБах Active Directory и пересылает эти изменения в Azure AD.</span><span class="sxs-lookup"><span data-stu-id="afb5e-142">It runs on an on-premises server, checks for changes in the AD DS, and forwards those changes to Azure AD.</span></span> <span data-ttu-id="afb5e-143">Azure AD Connect предоставляет возможность фильтрации синхронизируемых учетных записей и синхронизации хешированной версии паролей пользователей, называемой синхронизацией хеша паролей (ФС).</span><span class="sxs-lookup"><span data-stu-id="afb5e-143">Azure AD Connect provides the ability to filter which accounts are synchronized and whether to synchronize a hashed version of user passwords, known as password hash synchronization (PHS).</span></span>

<span data-ttu-id="afb5e-144">При внедрении гибридного удостоверения для сведений об учетной записи в локальной службе AD DS используется достоверный источник.</span><span class="sxs-lookup"><span data-stu-id="afb5e-144">When you implement hybrid identity, your on-premises AD DS is the authoritative source for account information.</span></span> <span data-ttu-id="afb5e-145">Это означает, что вы выполняете задачи по администрированию преимущественно в локальной среде, которые затем синхронизируются с Azure AD.</span><span class="sxs-lookup"><span data-stu-id="afb5e-145">This means that you perform administration tasks mostly on-premises, which are then synchronized to Azure AD.</span></span> 

<span data-ttu-id="afb5e-146">Ниже приведены компоненты гибридного удостоверения.</span><span class="sxs-lookup"><span data-stu-id="afb5e-146">Here are the components of hybrid identity.</span></span>

![](./media/about-office-365-identity/hybrid-identity.png)

<span data-ttu-id="afb5e-147">У клиента Azure AD есть копия учетных записей доменных служб Active Directory.</span><span class="sxs-lookup"><span data-stu-id="afb5e-147">The Azure AD tenant has a copy of the AD DS accounts.</span></span> <span data-ttu-id="afb5e-148">В этой конфигурации как локальные, так и удаленные пользователи, обращающиеся к Microsoft 365 Cloud Services, проходят проверку подлинности в Azure AD.</span><span class="sxs-lookup"><span data-stu-id="afb5e-148">In this configuration, both on-premises and remote users accessing Microsoft 365 cloud services authenticate against Azure AD.</span></span>

>[!Note]
><span data-ttu-id="afb5e-149">Всегда необходимо использовать Azure AD Connect для синхронизации учетных записей пользователей с гибридным удостоверением.</span><span class="sxs-lookup"><span data-stu-id="afb5e-149">You always need to use Azure AD Connect to synchronize user accounts for hybrid identity.</span></span> <span data-ttu-id="afb5e-150">Учетные записи синхронизированных пользователей в Azure AD необходимы для выполнения задач по управлению назначением лицензий и групп, а также для настройки разрешений и других административных задач, включающих учетные записи пользователей.</span><span class="sxs-lookup"><span data-stu-id="afb5e-150">You need the synchronized user accounts in Azure AD to perform license assignment and group management, configure permissions, and other administrative tasks that involve user accounts.</span></span>
>

### <a name="administration"></a><span data-ttu-id="afb5e-151">Администрирование</span><span class="sxs-lookup"><span data-stu-id="afb5e-151">Administration</span></span>

<span data-ttu-id="afb5e-152">Так как первоначальные и полномочные учетные записи пользователей хранятся в локальной службе AD DS, вы управляете удостоверениями с теми же инструментами, что и AD DS, например с помощью средства "пользователи и компьютеры Active Directory".</span><span class="sxs-lookup"><span data-stu-id="afb5e-152">Because the original and authoritative user accounts are stored in the on-premises AD DS, you manage your identities with the same tools as AD DS, such as the Active Directory Users and Computers tool.</span></span> 

<span data-ttu-id="afb5e-153">Вы не используете центр администрирования Microsoft 365 или Windows PowerShell для управления синхронизированными учетными записями пользователей в Azure AD.</span><span class="sxs-lookup"><span data-stu-id="afb5e-153">You don’t use the Microsoft 365 admin center or Windows PowerShell to manage synchronized user accounts in Azure AD.</span></span>

## <a name="next-step"></a><span data-ttu-id="afb5e-154">Следующий шаг</span><span class="sxs-lookup"><span data-stu-id="afb5e-154">Next step</span></span>

<span data-ttu-id="afb5e-155">Если требуется только Облачная модель удостоверений, ознакомьтесь со статьями " [облачные удостоверения](cloud-only-identities.md)".</span><span class="sxs-lookup"><span data-stu-id="afb5e-155">If you need the cloud-only identity model, see [Cloud-only identities](cloud-only-identities.md).</span></span>

<span data-ttu-id="afb5e-156">Если вам нужна Гибридная модель идентификации, ознакомьтесь со статьей [планирование синхронизированных удостоверений и способов проверки](plan-for-directory-synchronization.md)подлинности.</span><span class="sxs-lookup"><span data-stu-id="afb5e-156">If you need the hybrid identity model, see [planning for your synchronized identities and authentication methods](plan-for-directory-synchronization.md).</span></span>
  

## <a name="video-training"></a><span data-ttu-id="afb5e-157">Обучающие видео</span><span class="sxs-lookup"><span data-stu-id="afb5e-157">Video training</span></span>

<span data-ttu-id="afb5e-158">В видеокурсе [Office 365: Управление удостоверениями с помощью Azure AD Connect](https://support.office.com/article/90991a1d-c0ab-479a-b413-35c9706f6fed.aspx), предоставленных в LinkedIn Learning.</span><span class="sxs-lookup"><span data-stu-id="afb5e-158">See the video course [Office 365: Manage Identities Using Azure AD Connect](https://support.office.com/article/90991a1d-c0ab-479a-b413-35c9706f6fed.aspx), brought to you by LinkedIn Learning.</span></span>
