---
title: Модели удостоверений Office 365 и Azure Active Directory
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.date: 05/20/2019
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
ms.openlocfilehash: f6e871f03fb99feea05293c425406b6be7dfedd5
ms.sourcegitcommit: f316aef1c122f8eb25c43a56bc894c4aa61c8e0c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2019
ms.locfileid: "38745672"
---
# <a name="office-365-identity-models-and-azure-active-directory"></a><span data-ttu-id="1b995-103">Модели удостоверений Office 365 и Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="1b995-103">Office 365 identity models and Azure Active Directory</span></span>

<span data-ttu-id="1b995-104">*Эта статья относится как к Office 365 Enterprise, так и к Microsoft 365 корпоративный.*</span><span class="sxs-lookup"><span data-stu-id="1b995-104">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="1b995-105">Office 365 использует Azure Active Directory (Azure AD), службу удостоверений и удостоверений пользователей на основе облачной службы проверки подлинности, включенную в вашу подписку на Office 365, для управления удостоверениями и проверкой подлинности для Office 365.</span><span class="sxs-lookup"><span data-stu-id="1b995-105">Office 365 uses Azure Active Directory (Azure AD), a cloud-based user identity and authentication service that is included with your Office 365 subscription, to manage identities and authentication for Office 365.</span></span> <span data-ttu-id="1b995-106">Правильная настройка инфраструктуры удостоверений крайне важна для управления доступом пользователей и разрешений Office 365 для Организации.</span><span class="sxs-lookup"><span data-stu-id="1b995-106">Getting your identity infrastructure configured correctly is vital to managing Office 365 user access and permissions for your organization.</span></span>

<span data-ttu-id="1b995-107">Прежде чем начать, просмотрите этот видеоролик, чтобы получить обзор моделей удостоверений и проверки подлинности для Office 365 и Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="1b995-107">Before you begin, watch this video for an overview of identity models and authentication for both Office 365 and Microsoft 365.</span></span>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE2Pjwu]

<span data-ttu-id="1b995-108">Первым вариантом планирования является модель удостоверений Office 365.</span><span class="sxs-lookup"><span data-stu-id="1b995-108">Your first planning choice is the Office 365 identity model.</span></span>

## <a name="office-365-identity-models"></a><span data-ttu-id="1b995-109">Модели удостоверений Office 365</span><span class="sxs-lookup"><span data-stu-id="1b995-109">Office 365 identity models</span></span>

<span data-ttu-id="1b995-110">Чтобы спланировать учетные записи пользователей, сначала необходимо ознакомиться с двумя моделями идентификации в Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="1b995-110">To plan for user accounts, you first need to understand the two identity models in Microsoft 365.</span></span> <span data-ttu-id="1b995-111">Вы можете поддерживать удостоверения вашей организации только в облаке, а также поддерживать локальные удостоверения доменных служб Active Directory (AD DS) и использовать их для проверки подлинности при доступе пользователей к Microsoft 365 Cloud Services.</span><span class="sxs-lookup"><span data-stu-id="1b995-111">You can maintain your organization's identities only in the cloud, or you can maintain your on-premises Active Directory Domain Services (AD DS) identities and use them for authentication when users access Microsoft 365 cloud services.</span></span>  

<span data-ttu-id="1b995-112">Ниже приведены два типа удостоверений, а также их наилучшее соответствие и преимущества.</span><span class="sxs-lookup"><span data-stu-id="1b995-112">Here are the two types of identity and their best fit and benefits.</span></span>

|||
|:-------|:-----|:-----|
|  | <span data-ttu-id="1b995-113">**Удостоверение только для облака**</span><span class="sxs-lookup"><span data-stu-id="1b995-113">**Cloud-only identity**</span></span> | <span data-ttu-id="1b995-114">**Гибридное удостоверение**</span><span class="sxs-lookup"><span data-stu-id="1b995-114">**Hybrid identity**</span></span> |
| <span data-ttu-id="1b995-115">**Определение**</span><span class="sxs-lookup"><span data-stu-id="1b995-115">**Definition**</span></span> | <span data-ttu-id="1b995-116">Учетная запись пользователя существует только в клиенте Azure Active Directory (Azure AD) для вашей подписки на Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="1b995-116">User account only exists in the Azure Active Directory (Azure AD) tenant for your Microsoft 365 subscription.</span></span> | <span data-ttu-id="1b995-117">Учетная запись пользователя существует в доменных службах Active Directory, а также копия в клиенте Azure AD для вашей подписки на Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="1b995-117">User account exists in AD DS and a copy is also in the Azure AD tenant for your Microsoft 365 subscription.</span></span> <span data-ttu-id="1b995-118">Учетная запись пользователя в Azure AD также может включать хешированную версию пароля учетной записи пользователя.</span><span class="sxs-lookup"><span data-stu-id="1b995-118">The user account in Azure AD might also include a hashed version of the user account password.</span></span> |
| <span data-ttu-id="1b995-119">**Проверка подлинности учетных данных пользователей в Microsoft 365**</span><span class="sxs-lookup"><span data-stu-id="1b995-119">**How Microsoft 365 authenticates user credentials**</span></span> | <span data-ttu-id="1b995-120">Клиент Azure AD для вашей подписки на Microsoft 365 выполняет проверку подлинности с учетной записью удостоверения в облаке.</span><span class="sxs-lookup"><span data-stu-id="1b995-120">The Azure AD tenant for your Microsoft 365 subscription performs the authentication with the cloud identity account.</span></span> | <span data-ttu-id="1b995-121">Клиент Azure AD для вашей подписки на Microsoft 365 обрабатывает процесс проверки подлинности или перенаправляет пользователя другому поставщику удостоверений.</span><span class="sxs-lookup"><span data-stu-id="1b995-121">The Azure AD tenant for your Microsoft 365 subscription either handles the authentication process or redirects the user to another identity provider.</span></span> |
| <span data-ttu-id="1b995-122">**Оптимально для**.</span><span class="sxs-lookup"><span data-stu-id="1b995-122">**Best for**</span></span> | <span data-ttu-id="1b995-123">Организации, которые не имеют локальных доменных служб Active Directory или не нуждаются в них.</span><span class="sxs-lookup"><span data-stu-id="1b995-123">Organizations that do not have or need an on-premises AD DS.</span></span> | <span data-ttu-id="1b995-124">Организации, использующие AD DS или другого поставщика удостоверений.</span><span class="sxs-lookup"><span data-stu-id="1b995-124">Organizations using AD DS or another identity provider.</span></span> |
| <span data-ttu-id="1b995-125">**Наибольшая выгода**</span><span class="sxs-lookup"><span data-stu-id="1b995-125">**Greatest benefit**</span></span> | <span data-ttu-id="1b995-126">Простота использования.</span><span class="sxs-lookup"><span data-stu-id="1b995-126">Simple to use.</span></span> <span data-ttu-id="1b995-127">Не требуются дополнительные средства каталогов или серверы.</span><span class="sxs-lookup"><span data-stu-id="1b995-127">No extra directory tools or servers required.</span></span> | <span data-ttu-id="1b995-128">Пользователи могут использовать одни и те же учетные данные при доступе к локальным или облачным ресурсам.</span><span class="sxs-lookup"><span data-stu-id="1b995-128">Users can use the same credentials when accessing on-premises or cloud-based resources.</span></span> |
||||

## <a name="cloud-only-identity"></a><span data-ttu-id="1b995-129">Удостоверение только для облака</span><span class="sxs-lookup"><span data-stu-id="1b995-129">Cloud-only identity</span></span>

<span data-ttu-id="1b995-130">Для удостоверения с единственным облаком используются учетные записи пользователей, существующие только в Azure AD.</span><span class="sxs-lookup"><span data-stu-id="1b995-130">A cloud-only identity uses user accounts that exist only in Azure AD.</span></span> <span data-ttu-id="1b995-131">Облачное удостоверение обычно используется малыми организациями, не имеющими локальных серверов, или не использующими AD DS для управления локальными удостоверениями.</span><span class="sxs-lookup"><span data-stu-id="1b995-131">Cloud identity is typically used by small organizations that do not have on-premises servers or do not use AD DS to manage local identities.</span></span> 

<span data-ttu-id="1b995-132">Ниже приведены основные компоненты удостоверения "только облако".</span><span class="sxs-lookup"><span data-stu-id="1b995-132">Here are the basic components of cloud-only identity.</span></span>
 
![](./media/about-office-365-identity/cloud-only-identity.png)

<span data-ttu-id="1b995-133">Как локальные, так и удаленные пользователи используют свои учетные записи пользователей и пароли Azure AD для доступа к облачным службам Office 365.</span><span class="sxs-lookup"><span data-stu-id="1b995-133">Both on-premises and remote (online) users use their Azure AD user accounts and passwords to access Office 365 cloud services.</span></span> <span data-ttu-id="1b995-134">Azure AD выполняет проверку подлинности учетных данных пользователя на основе сохраненных учетных записей пользователей и паролей.</span><span class="sxs-lookup"><span data-stu-id="1b995-134">Azure AD authenticates user credentials based on its stored user accounts and passwords.</span></span>

### <a name="administration"></a><span data-ttu-id="1b995-135">Администрирование</span><span class="sxs-lookup"><span data-stu-id="1b995-135">Administration</span></span>
<span data-ttu-id="1b995-136">Так как учетные записи пользователей хранятся только в Azure AD, управление облачными удостоверениями осуществляется с помощью таких средств, как [центр администрирования Microsoft 365](https://admin.microsoft.com) и Windows PowerShell, с помощью модуля PowerShell Azure Active Directory PowerShell для Graph.</span><span class="sxs-lookup"><span data-stu-id="1b995-136">Because user accounts are only stored in Azure AD, you manage cloud identities with tools such as the [Microsoft 365 admin center](https://admin.microsoft.com) and Windows PowerShell with the Azure Active Directory PowerShell for Graph module.</span></span> 

## <a name="hybrid-identity"></a><span data-ttu-id="1b995-137">Гибридная идентификация</span><span class="sxs-lookup"><span data-stu-id="1b995-137">Hybrid identity</span></span>

<span data-ttu-id="1b995-138">Гибридное удостоверение использует учетные записи, созданные в локальных доменных службах Active Directory и имеющие копию в клиенте Azure AD подписки на Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="1b995-138">Hybrid identity uses accounts that originate in an on-premises AD DS and have a copy in the Azure AD tenant of a Microsoft 365 subscription.</span></span> <span data-ttu-id="1b995-139">Однако большинство изменений переходят только один из них.</span><span class="sxs-lookup"><span data-stu-id="1b995-139">However, most changes only flow one way.</span></span> <span data-ttu-id="1b995-140">Изменения, вносимые в учетные записи пользователей доменных служб Active Directory, синхронизируются с их копией в Azure AD.</span><span class="sxs-lookup"><span data-stu-id="1b995-140">Changes that you make to AD DS user accounts are synchronized to their copy in Azure AD.</span></span> <span data-ttu-id="1b995-141">Но изменения, внесенные в облачные учетные записи в Azure AD, такие как новые учетные записи пользователей, не синхронизируются с AD DS.</span><span class="sxs-lookup"><span data-stu-id="1b995-141">But changes made to cloud-based accounts in Azure AD, such as new user accounts, are not synchronized with AD DS.</span></span>

<span data-ttu-id="1b995-142">Azure AD Connect обеспечивает текущую синхронизацию учетных записей.</span><span class="sxs-lookup"><span data-stu-id="1b995-142">Azure AD Connect provides the ongoing account synchronization.</span></span> <span data-ttu-id="1b995-143">Он выполняется на локальном сервере, проверяет изменения в доменных СЛУЖБах Active Directory и пересылает эти изменения в Azure AD.</span><span class="sxs-lookup"><span data-stu-id="1b995-143">It runs on an on-premises server, checks for changes in the AD DS, and forwards those changes to Azure AD.</span></span> <span data-ttu-id="1b995-144">Azure AD Connect предоставляет возможность фильтрации синхронизируемых учетных записей и синхронизации хешированной версии паролей пользователей, называемой синхронизацией хеша паролей (ФС).</span><span class="sxs-lookup"><span data-stu-id="1b995-144">Azure AD Connect provides the ability to filter which accounts are synchronized and whether to synchronize a hashed version of user passwords, known as password hash synchronization (PHS).</span></span>

<span data-ttu-id="1b995-145">При внедрении гибридного удостоверения для сведений об учетной записи в локальной службе AD DS используется достоверный источник.</span><span class="sxs-lookup"><span data-stu-id="1b995-145">When you implement hybrid identity, your on-premises AD DS is the authoritative source for account information.</span></span> <span data-ttu-id="1b995-146">Это означает, что вы выполняете задачи по администрированию преимущественно в локальной среде, которые затем синхронизируются с Azure AD.</span><span class="sxs-lookup"><span data-stu-id="1b995-146">This means that you perform administration tasks mostly on-premises, which are then synchronized to Azure AD.</span></span> 

<span data-ttu-id="1b995-147">Ниже приведены компоненты гибридного удостоверения.</span><span class="sxs-lookup"><span data-stu-id="1b995-147">Here are the components of hybrid identity.</span></span>

![](./media/about-office-365-identity/hybrid-identity.png)

<span data-ttu-id="1b995-148">У клиента Azure AD есть копия учетных записей доменных служб Active Directory.</span><span class="sxs-lookup"><span data-stu-id="1b995-148">The Azure AD tenant has a copy of the AD DS accounts.</span></span> <span data-ttu-id="1b995-149">В этой конфигурации как локальные, так и удаленные пользователи, обращающиеся к Microsoft 365 Cloud Services, проходят проверку подлинности в Azure AD.</span><span class="sxs-lookup"><span data-stu-id="1b995-149">In this configuration, both on-premises and remote users accessing Microsoft 365 cloud services authenticate against Azure AD.</span></span>

>[!Note]
><span data-ttu-id="1b995-150">Всегда необходимо использовать Azure AD Connect для синхронизации учетных записей пользователей с гибридным удостоверением.</span><span class="sxs-lookup"><span data-stu-id="1b995-150">You always need to use Azure AD Connect to synchronize user accounts for hybrid identity.</span></span> <span data-ttu-id="1b995-151">Учетные записи синхронизированных пользователей в Azure AD необходимы для выполнения задач по управлению назначением лицензий и групп, а также для настройки разрешений и других административных задач, включающих учетные записи пользователей.</span><span class="sxs-lookup"><span data-stu-id="1b995-151">You need the synchronized user accounts in Azure AD to perform license assignment and group management, configure permissions, and other administrative tasks that involve user accounts.</span></span>
>

### <a name="administration"></a><span data-ttu-id="1b995-152">Администрирование</span><span class="sxs-lookup"><span data-stu-id="1b995-152">Administration</span></span>

<span data-ttu-id="1b995-153">Так как первоначальные и полномочные учетные записи пользователей хранятся в локальной службе AD DS, вы управляете удостоверениями с теми же инструментами, что и AD DS, например с помощью средства "пользователи и компьютеры Active Directory".</span><span class="sxs-lookup"><span data-stu-id="1b995-153">Because the original and authoritative user accounts are stored in the on-premises AD DS, you manage your identities with the same tools as AD DS, such as the Active Directory Users and Computers tool.</span></span> 

<span data-ttu-id="1b995-154">Вы не используете центр администрирования Microsoft 365 или Windows PowerShell для управления синхронизированными учетными записями пользователей в Azure AD.</span><span class="sxs-lookup"><span data-stu-id="1b995-154">You don’t use the Microsoft 365 admin center or Windows PowerShell to manage synchronized user accounts in Azure AD.</span></span>

## <a name="next-step"></a><span data-ttu-id="1b995-155">Следующий шаг</span><span class="sxs-lookup"><span data-stu-id="1b995-155">Next step</span></span>

<span data-ttu-id="1b995-156">Если требуется только Облачная модель удостоверений, ознакомьтесь со статьями " [облачные удостоверения](cloud-only-identities.md)".</span><span class="sxs-lookup"><span data-stu-id="1b995-156">If you need the cloud-only identity model, see [Cloud-only identities](cloud-only-identities.md).</span></span>

<span data-ttu-id="1b995-157">Если вам нужна Гибридная модель идентификации, ознакомьтесь со статьей [Синхронизация службы каталогов](plan-for-directory-synchronization.md).</span><span class="sxs-lookup"><span data-stu-id="1b995-157">If you need the hybrid identity model, see [directory synchronization](plan-for-directory-synchronization.md).</span></span>
  

## <a name="video-training"></a><span data-ttu-id="1b995-158">Обучающее видео</span><span class="sxs-lookup"><span data-stu-id="1b995-158">Video training</span></span>

<span data-ttu-id="1b995-159">В видеокурсе [Office 365: Управление удостоверениями с помощью Azure AD Connect](https://support.office.com/article/90991a1d-c0ab-479a-b413-35c9706f6fed.aspx), предоставленных в LinkedIn Learning.</span><span class="sxs-lookup"><span data-stu-id="1b995-159">See the video course [Office 365: Manage Identities Using Azure AD Connect](https://support.office.com/article/90991a1d-c0ab-479a-b413-35c9706f6fed.aspx), brought to you by LinkedIn Learning.</span></span>

## <a name="see-also"></a><span data-ttu-id="1b995-160">См. также</span><span class="sxs-lookup"><span data-stu-id="1b995-160">See also</span></span>

[<span data-ttu-id="1b995-161">Обзор Microsoft 365 корпоративный</span><span class="sxs-lookup"><span data-stu-id="1b995-161">Microsoft 365 Enterprise overview</span></span>](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)
