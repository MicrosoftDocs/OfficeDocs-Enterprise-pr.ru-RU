---
title: Гибридная идентификация и синхронизация каталогов для Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: conceptual
ms.date: 05/20/2019
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MOE150
- MET150
ms.assetid: d3577c90-dda5-45ca-afb0-370d2889b10f
description: Описывается синхронизация каталогов с Office 365, очистка доменных служб Active Directory и средство Azure Active Directory Connect.
ms.openlocfilehash: 5b91ebfae2250d44c34aed45c00ac09e98b21909
ms.sourcegitcommit: f316aef1c122f8eb25c43a56bc894c4aa61c8e0c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2019
ms.locfileid: "38747089"
---
# <a name="hybrid-identity-and-directory-synchronization-for-office-365"></a><span data-ttu-id="0d4a2-103">Гибридная идентификация и синхронизация каталогов для Office 365</span><span class="sxs-lookup"><span data-stu-id="0d4a2-103">Hybrid identity and directory synchronization for Office 365</span></span>

<span data-ttu-id="0d4a2-104">*Эта статья относится как к Office 365 Enterprise, так и к Microsoft 365 корпоративный.*</span><span class="sxs-lookup"><span data-stu-id="0d4a2-104">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="0d4a2-105">В зависимости от потребностей бизнеса и технических требований, наиболее распространенным выбором для корпоративных клиентов, использующих Office 365, является гибридная модель идентификации и синхронизация службы каталогов.</span><span class="sxs-lookup"><span data-stu-id="0d4a2-105">Depending on business needs and technical requirements, the hybrid identity model and directory synchronization is the most common choice for enterprise customers who are adopting Office 365.</span></span> <span data-ttu-id="0d4a2-106">Синхронизация службы каталогов позволяет управлять удостоверениями в доменных службах Active Directory (AD DS), а все обновления учетных записей пользователей, групп и контактов синхронизируются с клиентом Azure Active Directory (Azure AD) вашей подписки на Office 365.</span><span class="sxs-lookup"><span data-stu-id="0d4a2-106">Directory synchronization allows you to manage identities in your Active Directory Domain Services (AD DS) and all updates to user accounts, groups, and contacts are synchronized to the Azure Active Directory (Azure AD) tenant of your Office 365 subscription.</span></span>

>[!Note]
><span data-ttu-id="0d4a2-107">Когда учетные записи пользователей AD DS синхронизируются впервые, им не назначается автоматическая лицензия на Office 365 и не удается получить доступ к службам Office 365, таким как электронная почта.</span><span class="sxs-lookup"><span data-stu-id="0d4a2-107">When AD DS user accounts are synchronized for the first time, they are not automatically assigned an Office 365 license and cannot access Office 365 services, such as email.</span></span> <span data-ttu-id="0d4a2-108">Необходимо назначить лицензии для этих учетных записей по отдельности или динамически с помощью членства в группе.</span><span class="sxs-lookup"><span data-stu-id="0d4a2-108">You must assign a license to these user accounts, either individually or dynamically through group membership.</span></span>
>

## <a name="authentication-for-hybrid-identity"></a><span data-ttu-id="0d4a2-109">Проверка подлинности для гибридного удостоверения</span><span class="sxs-lookup"><span data-stu-id="0d4a2-109">Authentication for hybrid identity</span></span>

<span data-ttu-id="0d4a2-110">При использовании модели гибридной идентификации существует два типа проверки подлинности:</span><span class="sxs-lookup"><span data-stu-id="0d4a2-110">There are two types of authentication when using the hybrid identity model:</span></span>

- <span data-ttu-id="0d4a2-111">Управляемая проверка подлинности.</span><span class="sxs-lookup"><span data-stu-id="0d4a2-111">Managed authentication</span></span>

  <span data-ttu-id="0d4a2-112">Azure AD обрабатывает процесс проверки подлинности с помощью локально сохраненной хешированной версии пароля или отправляет учетные данные в локальный агент программного обеспечения, чтобы пройти проверку подлинности в локальных доменных службах Active Directory.</span><span class="sxs-lookup"><span data-stu-id="0d4a2-112">Azure AD handles the authentication process by using a locally stored hashed version of the password or sends the credentials to an on-premises software agent to be authenticated by the on-premises AD DS.</span></span>

- <span data-ttu-id="0d4a2-113">Федеративная проверка подлинности</span><span class="sxs-lookup"><span data-stu-id="0d4a2-113">Federated authentication</span></span>

  <span data-ttu-id="0d4a2-114">Azure AD перенаправляет клиентский компьютер, запрашивающий проверку подлинности, установить контакт с другим поставщиком удостоверений.</span><span class="sxs-lookup"><span data-stu-id="0d4a2-114">Azure AD redirects the client computer requesting authentication to contact another identity provider.</span></span>

### <a name="managed-authentication"></a><span data-ttu-id="0d4a2-115">Управляемая проверка подлинности.</span><span class="sxs-lookup"><span data-stu-id="0d4a2-115">Managed authentication</span></span>

<span data-ttu-id="0d4a2-116">Существует два типа управляемой проверки подлинности:</span><span class="sxs-lookup"><span data-stu-id="0d4a2-116">There are two types of managed authentication:</span></span>

- <span data-ttu-id="0d4a2-117">Синхронизация хэша паролей (PHS)</span><span class="sxs-lookup"><span data-stu-id="0d4a2-117">Password hash synchronization (PHS)</span></span>

  <span data-ttu-id="0d4a2-118">Проверка подлинности выполняется с помощью Azure AD.</span><span class="sxs-lookup"><span data-stu-id="0d4a2-118">Azure AD performs the authentication itself.</span></span>

- <span data-ttu-id="0d4a2-119">Сквозная проверка подлинности (PTA)</span><span class="sxs-lookup"><span data-stu-id="0d4a2-119">Pass-through authentication (PTA)</span></span>

  <span data-ttu-id="0d4a2-120">Проверка подлинности выполняется с помощью доменных служб Aсtive Directory в Azure AD.</span><span class="sxs-lookup"><span data-stu-id="0d4a2-120">Azure AD has AD DS perform the authentication.</span></span>


#### <a name="password-hash-synchronization"></a><span data-ttu-id="0d4a2-121">Синхронизация хэшей паролей</span><span class="sxs-lookup"><span data-stu-id="0d4a2-121">Password hash synchronization</span></span>

<span data-ttu-id="0d4a2-122">С помощью синхронизации хэша паролей (ФС) вы синхронизируете учетные записи пользователей доменных служб Active Directory с Office 365 и управляете локальными пользователями.</span><span class="sxs-lookup"><span data-stu-id="0d4a2-122">With password hash synchronization (PHS), you synchronize your AD DS user accounts with Office 365 and manage your users on-premises.</span></span> <span data-ttu-id="0d4a2-123">Хэши паролей пользователей синхронизируются из доменных служб Active Directory в Azure AD, чтобы пользователи могли использовать один и тот же пароль в локальной среде и в облаке.</span><span class="sxs-lookup"><span data-stu-id="0d4a2-123">Hashes of user passwords are synchronized from your AD DS to Azure AD so that the users have the same password on-premises and in the cloud.</span></span> <span data-ttu-id="0d4a2-124">Это самый простой способ включить проверку подлинности для удостоверений AD DS в Azure AD.</span><span class="sxs-lookup"><span data-stu-id="0d4a2-124">This is the simplest way to enable authentication for AD DS identities in Azure AD.</span></span> 

![](./media/plan-for-directory-synchronization/phs-authentication.png)

<span data-ttu-id="0d4a2-125">Когда пароли изменяются или сбрасываются локально, новые хэши паролей синхронизируются с Azure AD, чтобы пользователи всегда могли использовать одинаковые пароли для облачных ресурсов и локальных ресурсов.</span><span class="sxs-lookup"><span data-stu-id="0d4a2-125">When passwords are changed or reset on-premises, the new password hashes are synchronized to Azure AD so that your users can always use the same password for cloud resources and on-premises resources.</span></span> <span data-ttu-id="0d4a2-126">Пароли пользователей никогда не отправляются в Azure AD или хранятся в службе Azure AD в виде простого текста.</span><span class="sxs-lookup"><span data-stu-id="0d4a2-126">The user passwords are never sent to Azure AD or stored in Azure AD in clear text.</span></span> <span data-ttu-id="0d4a2-127">Некоторые расширенные функции Azure AD, такие как защита идентификации, требуют ФС независимо от выбранного метода проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="0d4a2-127">Some premium features of Azure AD, such as Identity Protection, require PHS regardless of which authentication method is selected.</span></span>
  
<span data-ttu-id="0d4a2-128">Чтобы узнать больше, ознакомьтесь со статьей [Выбор ФС](https://docs.microsoft.com/azure/security/azure-ad-choose-authn) .</span><span class="sxs-lookup"><span data-stu-id="0d4a2-128">See [choosing PHS](https://docs.microsoft.com/azure/security/azure-ad-choose-authn) to learn more.</span></span>
  
#### <a name="pass-through-authentication"></a><span data-ttu-id="0d4a2-129">Сквозная проверка подлинности</span><span class="sxs-lookup"><span data-stu-id="0d4a2-129">Pass-through authentication</span></span>

<span data-ttu-id="0d4a2-130">Сквозная проверка подлинности (ПТА) предоставляет простую проверку паролей для служб проверки подлинности Azure AD с помощью программного агента, работающего на одном или нескольких локальных серверах, для проверки пользователей непосредственно в доменных СЛУЖБах Active Directory.</span><span class="sxs-lookup"><span data-stu-id="0d4a2-130">Pass-through authentication (PTA) provides a simple password validation for Azure AD authentication services using a software agent running on one or more on-premises servers to validate the users directly with your AD DS.</span></span> <span data-ttu-id="0d4a2-131">При сквозной проверке подлинности (ПТА) вы синхронизируете учетные записи пользователей AD DS с Office 365 и управляете локальными пользователями.</span><span class="sxs-lookup"><span data-stu-id="0d4a2-131">With pass-through authentication (PTA), you synchronize AD DS user accounts with Office 365 and manage your users on-premises.</span></span> 

![](./media/plan-for-directory-synchronization/pta-authentication.png)

<span data-ttu-id="0d4a2-132">ПТА позволяет пользователям входить как в локальные, так и в Office 365 ресурсы и приложения, используя их локальную учетную запись и пароль.</span><span class="sxs-lookup"><span data-stu-id="0d4a2-132">PTA allows your users to sign in to both on-premises and Office 365 resources and applications using their on-premises account and password.</span></span> <span data-ttu-id="0d4a2-133">Эта конфигурация проверяет пароли пользователей непосредственно для локальных доменных служб Active Directory без сохранения хеш-кодов паролей в Azure AD.</span><span class="sxs-lookup"><span data-stu-id="0d4a2-133">This configuration validates users passwords directly against your on-premises AD DS without storing password hashes in Azure AD.</span></span> 

<span data-ttu-id="0d4a2-134">ПТА также используется в организациях с требованиями к безопасности для немедленного применения локальных состояний учетных записей пользователей, политик паролей и часов входа.</span><span class="sxs-lookup"><span data-stu-id="0d4a2-134">PTA is also for organizations with a security requirement to immediately enforce on-premises user account states, password policies, and logon hours.</span></span> 
  
<span data-ttu-id="0d4a2-135">Чтобы узнать больше, ознакомьтесь со статьей [Выбор ПТА](https://docs.microsoft.com/azure/security/azure-ad-choose-authn) .</span><span class="sxs-lookup"><span data-stu-id="0d4a2-135">See [choosing PTA](https://docs.microsoft.com/azure/security/azure-ad-choose-authn) to learn more.</span></span>
  
### <a name="federated-authentication"></a><span data-ttu-id="0d4a2-136">Федеративная проверка подлинности</span><span class="sxs-lookup"><span data-stu-id="0d4a2-136">Federated authentication</span></span>

<span data-ttu-id="0d4a2-137">Федеративная проверка подлинности в основном используется для крупных организаций с более сложными требованиями к проверке подлинности.</span><span class="sxs-lookup"><span data-stu-id="0d4a2-137">Federated authentication is primarily for large enterprise organizations with more complex authentication requirements.</span></span> <span data-ttu-id="0d4a2-138">Удостоверения доменных служб Active Directory синхронизируются с Office 365, и учетные записи пользователей управляются локально.</span><span class="sxs-lookup"><span data-stu-id="0d4a2-138">AD DS identities are synchronized with Office 365 and users accounts are managed on-premises.</span></span> <span data-ttu-id="0d4a2-139">При использовании федеративной проверки подлинности пользователи имеют один и тот же пароль в локальной среде и в облаке, и им не нужно повторно выполнять вход для использования Office 365.</span><span class="sxs-lookup"><span data-stu-id="0d4a2-139">With federated authentication, users have the same password on-premises and in the cloud and they do not have to sign in again to use Office 365.</span></span> 

<span data-ttu-id="0d4a2-140">Федеративная проверка подлинности может поддерживать дополнительные требования к проверке подлинности, такие как проверка подлинности на основе смарт-карт или третья многофакторная проверка подлинности и обычно требуется при отсутствии требования к проверке подлинности для организаций изначально поддержка Azure AD.</span><span class="sxs-lookup"><span data-stu-id="0d4a2-140">Federated authentication can support additional authentication requirements, such as smartcard-based authentication or a third-party multi-factor authentication and is typically required when organizations have an authentication requirement not natively supported by Azure AD.</span></span>
 
<span data-ttu-id="0d4a2-141">Чтобы узнать больше, ознакомьтесь со статьей [Выбор федеративной проверки подлинности](https://docs.microsoft.com/azure/security/azure-ad-choose-authn) .</span><span class="sxs-lookup"><span data-stu-id="0d4a2-141">See [choosing federated authentication](https://docs.microsoft.com/azure/security/azure-ad-choose-authn) to learn more.</span></span>
  
#### <a name="third-party-authentication-and-identity-providers"></a><span data-ttu-id="0d4a2-142">Сторонние поставщики проверки подлинности и идентификации</span><span class="sxs-lookup"><span data-stu-id="0d4a2-142">Third-party authentication and identity providers</span></span>

<span data-ttu-id="0d4a2-143">Локальные объекты каталогов могут синхронизироваться с Office 365 и доступом к облачным ресурсам в основном управляются сторонним поставщиком удостоверений (IdP).</span><span class="sxs-lookup"><span data-stu-id="0d4a2-143">On-premises directory objects may be synchronized to Office 365 and cloud resource access is primarily managed by a third-party identity provider (IdP).</span></span> <span data-ttu-id="0d4a2-144">Если в вашей организации используется стороннее решение Федерации, вы можете настроить вход с этим решением для Office 365, предоставили, что стороннее решение совместимо с Azure AD.</span><span class="sxs-lookup"><span data-stu-id="0d4a2-144">If your organization uses a third-party federation solution, you can configure sign-on with that solution for Office 365 provided that the third-party federation solution is compatible with Azure AD.</span></span>
  
<span data-ttu-id="0d4a2-145">Для получения дополнительных сведений см. [Совместимость Федерации Azure AD](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-federation-compatibility) .</span><span class="sxs-lookup"><span data-stu-id="0d4a2-145">See [Azure AD federation compatibility](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-federation-compatibility) to learn more.</span></span>
  
## <a name="ad-ds-cleanup"></a><span data-ttu-id="0d4a2-146">Очистка AD DS</span><span class="sxs-lookup"><span data-stu-id="0d4a2-146">AD DS Cleanup</span></span>

<span data-ttu-id="0d4a2-147">Для обеспечения беспрепятственного перехода в Office 365 с помощью синхронизации необходимо подготовить лес доменных служб Active Directory, прежде чем приступать к развертыванию синхронизации каталогов Office 365.</span><span class="sxs-lookup"><span data-stu-id="0d4a2-147">To help ensure a seamless transition to Office 365 by using synchronization, you must prepare your AD DS forest before you begin your Office 365 directory synchronization deployment.</span></span>
  
<span data-ttu-id="0d4a2-148">Если вы [настроили синхронизацию службы каталогов в Office 365](set-up-directory-synchronization.md), выполните одно из указанных ниже действий для [загрузки и запуска средства IdFix](install-and-run-idfix.md).</span><span class="sxs-lookup"><span data-stu-id="0d4a2-148">When you [set up directory synchronization in Office 365](set-up-directory-synchronization.md), one of the steps is to [download and run the IdFix tool](install-and-run-idfix.md).</span></span> <span data-ttu-id="0d4a2-149">Средство IdFix можно использовать для [очистки каталогов](prepare-directory-attributes-for-synch-with-idfix.md).</span><span class="sxs-lookup"><span data-stu-id="0d4a2-149">You can use the IdFix tool to help with [directory cleanup](prepare-directory-attributes-for-synch-with-idfix.md).</span></span>
  
<span data-ttu-id="0d4a2-150">Очистка каталогов должна сосредоточиться на следующих задачах:</span><span class="sxs-lookup"><span data-stu-id="0d4a2-150">Your directory cleanup should focus on the following tasks:</span></span>

- <span data-ttu-id="0d4a2-151">Удалите повторяющиеся атрибуты **proxyAddress** и **userPrincipalName** .</span><span class="sxs-lookup"><span data-stu-id="0d4a2-151">Remove duplicate **proxyAddress** and **userPrincipalName** attributes.</span></span>
- <span data-ttu-id="0d4a2-152">Обновление пустых и недопустимых атрибутов **userPrincipalName** с допустимыми атрибутами **userPrincipalName** .</span><span class="sxs-lookup"><span data-stu-id="0d4a2-152">Update blank and invalid **userPrincipalName** attributes with valid **userPrincipalName** attributes.</span></span>
- <span data-ttu-id="0d4a2-153">Удалите недопустимые и сомнительные символы в атрибутах **givenName**, фамилия ( **SN** ), **SamAccountName**, **DisplayName**, **mail**, **proxyAddresses**, **mailNickname**и **userPrincipalName** .</span><span class="sxs-lookup"><span data-stu-id="0d4a2-153">Remove invalid and questionable characters in the **givenName**, surname ( **sn** ), **sAMAccountName**, **displayName**, **mail**, **proxyAddresses**, **mailNickname**, and **userPrincipalName** attributes.</span></span> <span data-ttu-id="0d4a2-154">Подробнее о подготовке атрибутов можно узнать [в разделе List of Attributes, которые синхронизируются средством синхронизации Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=396719).</span><span class="sxs-lookup"><span data-stu-id="0d4a2-154">For details about preparing attributes, see [List of attributes that are synced by the Azure Active Directory Sync Tool](https://go.microsoft.com/fwlink/p/?LinkId=396719).</span></span>

    > [!NOTE]
    > <span data-ttu-id="0d4a2-155">Это те же атрибуты, которые синхронизируются с помощью Azure AD Connect.</span><span class="sxs-lookup"><span data-stu-id="0d4a2-155">These are the same attributes that Azure AD Connect synchronizes.</span></span> 
  
## <a name="multi-forest-deployment-considerations"></a><span data-ttu-id="0d4a2-156">Рекомендации по развертыванию нескольких лесов</span><span class="sxs-lookup"><span data-stu-id="0d4a2-156">Multi-forest deployment considerations</span></span>

<span data-ttu-id="0d4a2-157">Для параметров нескольких лесов и единого входа используйте [выборочную установку Azure AD Connect](https://go.microsoft.com/fwlink/p/?LinkId=698430).</span><span class="sxs-lookup"><span data-stu-id="0d4a2-157">For multiple forests and SSO options, use [Custom Installation of Azure AD Connect](https://go.microsoft.com/fwlink/p/?LinkId=698430).</span></span>
  
<span data-ttu-id="0d4a2-158">Если в организации используется несколько лесов для проверки подлинности (лесов входа), настоятельно рекомендуется выполнить следующие действия:</span><span class="sxs-lookup"><span data-stu-id="0d4a2-158">If your organization has multiple forests for authentication (logon forests), we highly recommend the following:</span></span>
  
- <span data-ttu-id="0d4a2-159">**Рассмотрите вопрос консолидации лесов.**</span><span class="sxs-lookup"><span data-stu-id="0d4a2-159">**Consider consolidating your forests.**</span></span> <span data-ttu-id="0d4a2-160">В общем случае для поддержки нескольких лесов требуется дополнительная нагрузка.</span><span class="sxs-lookup"><span data-stu-id="0d4a2-160">In general, there's more overhead required to maintain multiple forests.</span></span> <span data-ttu-id="0d4a2-161">Если в Организации не предусмотрены ограничения безопасности, которые определяют потребность в отдельных лесах, рекомендуется упростить локальную среду.</span><span class="sxs-lookup"><span data-stu-id="0d4a2-161">Unless your organization has security constraints that dictate the need for separate forests, consider simplifying your on-premises environment.</span></span>
- <span data-ttu-id="0d4a2-162">**Используйте только в основном лесе входа в систему.**</span><span class="sxs-lookup"><span data-stu-id="0d4a2-162">**Use only in your primary logon forest.**</span></span> <span data-ttu-id="0d4a2-163">Рассмотрите вопрос о развертывании Office 365 только в основном лесе входа в систему для первоначального развертывания Office 365.</span><span class="sxs-lookup"><span data-stu-id="0d4a2-163">Consider deploying Office 365 only in your primary logon forest for your initial rollout of Office 365.</span></span> 

<span data-ttu-id="0d4a2-164">Если вы не можете консолидировать развертывание AD DS с несколькими лесами или используете другие службы каталогов для управления удостоверениями, их можно синхронизировать с помощью корпорации Майкрософт или партнера.</span><span class="sxs-lookup"><span data-stu-id="0d4a2-164">If you can't consolidate your multi-forest AD DS deployment or are using other directory services to manage identities, you may be able to synchronize these with the help of Microsoft or a partner.</span></span>
  
<span data-ttu-id="0d4a2-165">Более подробную информацию можно узнать [в статье Синхронизация каталогов с несколькими лесами с помощью сценария единого входа](https://go.microsoft.com/fwlink/p/?LinkId=525321) .</span><span class="sxs-lookup"><span data-stu-id="0d4a2-165">See [Multi-forest Directory Sync with Single Sign-On Scenario](https://go.microsoft.com/fwlink/p/?LinkId=525321) for more information.</span></span>
  
## <a name="features-that-are-dependent-on-directory-synchronization"></a><span data-ttu-id="0d4a2-166">Компоненты, зависящие от синхронизации службы каталогов</span><span class="sxs-lookup"><span data-stu-id="0d4a2-166">Features that are dependent on directory synchronization</span></span>
  
<span data-ttu-id="0d4a2-167">Синхронизация службы каталогов необходима для следующих функций и функций:</span><span class="sxs-lookup"><span data-stu-id="0d4a2-167">Directory synchronization is required for the following features and functionality:</span></span>
  
- <span data-ttu-id="0d4a2-168">Единый вход в Azure AD (SSO)</span><span class="sxs-lookup"><span data-stu-id="0d4a2-168">Azure AD Seamless Single Sign-On (SSO)</span></span>
- <span data-ttu-id="0d4a2-169">Сосуществование Skype</span><span class="sxs-lookup"><span data-stu-id="0d4a2-169">Skype coexistence</span></span>
- <span data-ttu-id="0d4a2-170">Гибридное развертывание Exchange, в том числе:</span><span class="sxs-lookup"><span data-stu-id="0d4a2-170">Exchange hybrid deployment, including:</span></span>
  - <span data-ttu-id="0d4a2-171">Полный общий глобальный список адресов (GAL) между локальной средой Exchange и Office 365.</span><span class="sxs-lookup"><span data-stu-id="0d4a2-171">Fully shared global address list (GAL) between your on-premises Exchange environment and Office 365.</span></span>
  - <span data-ttu-id="0d4a2-172">синхронизацию данных глобального списка адресов из разных почтовых систем;</span><span class="sxs-lookup"><span data-stu-id="0d4a2-172">Synchronizing GAL information from different mail systems.</span></span>
  - <span data-ttu-id="0d4a2-173">Возможность добавлять и удалять пользователей из служб Office 365.</span><span class="sxs-lookup"><span data-stu-id="0d4a2-173">The ability to add users to and remove users from Office 365 service offerings.</span></span> <span data-ttu-id="0d4a2-174">Для этого требуются следующие компоненты:</span><span class="sxs-lookup"><span data-stu-id="0d4a2-174">This requires the following:</span></span>
  - <span data-ttu-id="0d4a2-175">Двухсторонняя синхронизация должна быть настроена во время настройки синхронизации службы каталогов.</span><span class="sxs-lookup"><span data-stu-id="0d4a2-175">Two-way synchronization must be configured during directory synchronization setup.</span></span> <span data-ttu-id="0d4a2-176">По умолчанию средства синхронизации службы каталогов записывают данные каталога только в облако.</span><span class="sxs-lookup"><span data-stu-id="0d4a2-176">By default, directory synchronization tools write directory information only to the cloud.</span></span> <span data-ttu-id="0d4a2-177">При настройке двусторонней синхронизации необходимо включить функцию обратной записи, чтобы в облако копировалось ограниченное количество атрибутов объектов, а затем они были записаны в локальные доменные службы Active Directory.</span><span class="sxs-lookup"><span data-stu-id="0d4a2-177">When you configure two-way synchronization, you enable write-back functionality so that a limited number of object attributes are copied from the cloud, and then written them back to your local AD DS.</span></span> <span data-ttu-id="0d4a2-178">Обратная запись также называется гибридным режимом Exchange.</span><span class="sxs-lookup"><span data-stu-id="0d4a2-178">Write-back is also referred to as Exchange hybrid mode.</span></span> 
  - <span data-ttu-id="0d4a2-179">Локальное гибридное развертывание Exchange</span><span class="sxs-lookup"><span data-stu-id="0d4a2-179">An on-premises Exchange hybrid deployment</span></span>
  - <span data-ttu-id="0d4a2-180">Возможность перемещать некоторые почтовые ящики пользователей в Office 365, сохраняя другие локальные почтовые ящики пользователей.</span><span class="sxs-lookup"><span data-stu-id="0d4a2-180">The ability to move some user mailboxes to Office 365 while keeping other user mailboxes on-premises.</span></span>
  - <span data-ttu-id="0d4a2-181">Надежные отправители и заблокированные отправители реплицируются в Office 365.</span><span class="sxs-lookup"><span data-stu-id="0d4a2-181">Safe senders and blocked senders on-premises are replicated to Office 365.</span></span>
  - <span data-ttu-id="0d4a2-182">базовое делегирование и функциональную возможность отправки электронной почты от имени кого-либо.</span><span class="sxs-lookup"><span data-stu-id="0d4a2-182">Basic delegation and send-on-behalf-of email functionality.</span></span>
  - <span data-ttu-id="0d4a2-183">У вас есть интегрированная локальная смарт-карта или решение с многофакторной проверкой подлинности.</span><span class="sxs-lookup"><span data-stu-id="0d4a2-183">You have an integrated on-premises smart card or multi-factor authentication solution.</span></span>
- <span data-ttu-id="0d4a2-184">Синхронизация фотографий, эскизов, Конференц-залов и групп безопасности</span><span class="sxs-lookup"><span data-stu-id="0d4a2-184">Synchronization of photos, thumbnails, conference rooms, and security groups</span></span>

## <a name="next-step"></a><span data-ttu-id="0d4a2-185">Следующий шаг</span><span class="sxs-lookup"><span data-stu-id="0d4a2-185">Next step</span></span>

<span data-ttu-id="0d4a2-186">Когда вы будете готовы развернуть гибридную идентификацию, ознакомьтесь со статьей [Подготовка к подготовке пользователей](prepare-for-directory-synchronization.md).</span><span class="sxs-lookup"><span data-stu-id="0d4a2-186">When you are ready to deploy hybrid identity, see [prepare to provision users](prepare-for-directory-synchronization.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="0d4a2-187">См. также</span><span class="sxs-lookup"><span data-stu-id="0d4a2-187">See also</span></span>

[<span data-ttu-id="0d4a2-188">Обзор Microsoft 365 корпоративный</span><span class="sxs-lookup"><span data-stu-id="0d4a2-188">Microsoft 365 Enterprise overview</span></span>](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)

