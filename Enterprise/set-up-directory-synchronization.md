---
title: Настройка синхронизации службы каталогов для Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED15
- MBS150
- BCS160
ms.assetid: 1b3b5318-6977-42ed-b5c7-96fa74b08846
description: Узнайте, как настроить синхронизацию каталогов между Office 365 и локальной службой Active Directory.
ms.openlocfilehash: 1798c54854bc5ecc82481aaabca3690e7212e135
ms.sourcegitcommit: 36e760407a1f4b18bc108134628ed9a8d3e35a8a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/17/2019
ms.locfileid: "34162482"
---
# <a name="set-up-directory-synchronization-for-office-365"></a><span data-ttu-id="60894-103">Настройка синхронизации службы каталогов для Office 365</span><span class="sxs-lookup"><span data-stu-id="60894-103">Set up directory synchronization for Office 365</span></span>

<span data-ttu-id="60894-104">Office 365 использует клиент Azure Active Directory (Azure AD) для хранения удостоверений для проверки подлинности и разрешений на доступ к облачным ресурсам и управления ими.</span><span class="sxs-lookup"><span data-stu-id="60894-104">Office 365 uses an Azure Active Directory (Azure AD) tenant to store and manage identities for authentication and permissions to access cloud-based resources.</span></span> 

<span data-ttu-id="60894-105">Если у вас есть локальные доменные службы Active Directory (AD DS), вы можете синхронизировать учетные записи пользователей доменных служб Active Directory, группы и контакты с клиентом Azure AD вашей подписки на Office 365.</span><span class="sxs-lookup"><span data-stu-id="60894-105">If you have an on-premises Active Directory Domain Services (AD DS), you can synchronize your AD DS user accounts, groups, and contacts with the Azure AD tenant of your Office 365 subscription.</span></span> <span data-ttu-id="60894-106">Это гибридное удостоверение для Office 365.</span><span class="sxs-lookup"><span data-stu-id="60894-106">This is hybrid identity for Office 365.</span></span> <span data-ttu-id="60894-107">Вот ее компоненты.</span><span class="sxs-lookup"><span data-stu-id="60894-107">Here are its components.</span></span>

![](./media/about-office-365-identity/hybrid-identity.png)

<span data-ttu-id="60894-108">Azure AD Connect работает на локальном сервере и синхронизирует доменные службы Active Directory с клиентом Azure AD.</span><span class="sxs-lookup"><span data-stu-id="60894-108">Azure AD Connect runs on an on-premises server and synchronizes your AD DS with the Azure AD tenant.</span></span> <span data-ttu-id="60894-109">Помимо синхронизации службы каталогов, можно также указать следующие параметры проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="60894-109">Along with directory synchronization, you can also specify these authentication options:</span></span>

- <span data-ttu-id="60894-110">Синхронизация хэша паролей (ФС)</span><span class="sxs-lookup"><span data-stu-id="60894-110">Password hash synchronization (PHS)</span></span>

  <span data-ttu-id="60894-111">Azure AD выполняет проверку подлинности.</span><span class="sxs-lookup"><span data-stu-id="60894-111">Azure AD performs the authentication itself.</span></span>

- <span data-ttu-id="60894-112">Сквозная проверка подлинности (PTA)</span><span class="sxs-lookup"><span data-stu-id="60894-112">Pass-through authentication (PTA)</span></span>

  <span data-ttu-id="60894-113">В Azure AD доменные службы Active Directory выполняют проверку подлинности.</span><span class="sxs-lookup"><span data-stu-id="60894-113">Azure AD has AD DS perform the authentication.</span></span>

- <span data-ttu-id="60894-114">Федеративная проверка подлинности</span><span class="sxs-lookup"><span data-stu-id="60894-114">Federated authentication</span></span>

  <span data-ttu-id="60894-115">Azure AD перенаправляет клиентский компьютер, запрашивающий проверку подлинности, для связи с другим поставщиком удостоверений.</span><span class="sxs-lookup"><span data-stu-id="60894-115">Azure AD redirects the client computer requesting authentication to contact another identity provider.</span></span>

<span data-ttu-id="60894-116">Более подробную информацию можно узнать в статье [гибридные удостоверения](plan-for-directory-synchronization.md) .</span><span class="sxs-lookup"><span data-stu-id="60894-116">See [Hybrid identities](plan-for-directory-synchronization.md) for more information.</span></span>
  
## <a name="1-review-prerequisites-for-azure-ad-connect"></a><span data-ttu-id="60894-117">1. Ознакомьтесь с требованиями для Azure AD Connect.</span><span class="sxs-lookup"><span data-stu-id="60894-117">1. Review prerequisites for Azure AD Connect</span></span>

<span data-ttu-id="60894-118">Вы получаете бесплатную подписку на Azure AD с подпиской на Office 365.</span><span class="sxs-lookup"><span data-stu-id="60894-118">You get a free Azure AD subscription with your Office 365 subscription.</span></span> <span data-ttu-id="60894-119">Когда вы настраиваете синхронизацию службы каталогов, вы сможете установить Azure AD Connect на одном из локальных серверов.</span><span class="sxs-lookup"><span data-stu-id="60894-119">When you set up directory synchronization, you will install Azure AD Connect on one of your on-premises servers.</span></span>
  
<span data-ttu-id="60894-120">Для Office 365 вам потребуется:</span><span class="sxs-lookup"><span data-stu-id="60894-120">For Office 365 you'll need to:</span></span>
  
- <span data-ttu-id="60894-121">Проверка локального домена.</span><span class="sxs-lookup"><span data-stu-id="60894-121">Verify your on-premises domain.</span></span> <span data-ttu-id="60894-122">Мастер Azure AD Connect поможет вам выполнить следующие шаги.</span><span class="sxs-lookup"><span data-stu-id="60894-122">The Azure AD Connect wizard guides you through this.</span></span>
- <span data-ttu-id="60894-123">Получите имена пользователей и пароли для учетных записей администраторов клиента Office 365 и AD DS.</span><span class="sxs-lookup"><span data-stu-id="60894-123">Obtain the user names and passwords for the admin accounts of your Office 365 tenant and AD DS.</span></span>

<span data-ttu-id="60894-124">Для локального сервера, на котором вы устанавливаете Azure AD Connect, вам потребуются следующие компоненты:</span><span class="sxs-lookup"><span data-stu-id="60894-124">For your on-premises server on which you install Azure AD Connect, you'll need:</span></span>
  
|<span data-ttu-id="60894-125">**Серверная операционная система**</span><span class="sxs-lookup"><span data-stu-id="60894-125">**Server OS**</span></span>|<span data-ttu-id="60894-126">\*\*другое программное обеспечение. \*\*</span><span class="sxs-lookup"><span data-stu-id="60894-126">**Other software**</span></span>|
|:-----|:-----|
|<span data-ttu-id="60894-127">Windows Server 2012 R2 и более поздние версии</span><span class="sxs-lookup"><span data-stu-id="60894-127">Windows Server 2012 R2 and later</span></span> | <span data-ttu-id="60894-128">-PowerShell устанавливается по умолчанию, никакие действия не требуются.</span><span class="sxs-lookup"><span data-stu-id="60894-128">- PowerShell is installed by default, no action is required.</span></span>  <br> <span data-ttu-id="60894-129">– NET 4.5.1 и более поздние версии предлагаются через обновление Windows.</span><span class="sxs-lookup"><span data-stu-id="60894-129">- Net 4.5.1 and later releases are offered through Windows Update.</span></span> <span data-ttu-id="60894-130">Убедитесь, что установлены последние обновления для Windows Server на панели управления.</span><span class="sxs-lookup"><span data-stu-id="60894-130">Make sure you have installed the latest updates to Windows Server in the Control Panel.</span></span> |
|<span data-ttu-id="60894-131">Windows Server 2008 R2 с пакетом обновления 1 (SP1) \* \* или Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="60894-131">Windows Server 2008 R2 with Service Pack 1 (SP1)\*\* or Windows Server 2012</span></span> | <span data-ttu-id="60894-132">— Последняя версия PowerShell доступна в Windows Management Framework 4,0.</span><span class="sxs-lookup"><span data-stu-id="60894-132">- The latest version of PowerShell is available in Windows Management Framework 4.0.</span></span> <span data-ttu-id="60894-133">Выполните поиск в [центре загрузки Майкрософт](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span><span class="sxs-lookup"><span data-stu-id="60894-133">Search for it on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span>  <br> <span data-ttu-id="60894-134">.NET 4.5.1 и более поздние версии доступны в [центре загрузки Майкрософт](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span><span class="sxs-lookup"><span data-stu-id="60894-134">- .Net 4.5.1 and later releases are available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span> |
|<span data-ttu-id="60894-135">Windows Server 2008</span><span class="sxs-lookup"><span data-stu-id="60894-135">Windows Server 2008</span></span> | <span data-ttu-id="60894-136">-Последняя поддерживаемая версия PowerShell доступна в Windows Management Framework 3,0, которая доступна в [центре загрузки Майкрософт](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span><span class="sxs-lookup"><span data-stu-id="60894-136">- The latest supported version of PowerShell is available in Windows Management Framework 3.0, available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span>  <br> <span data-ttu-id="60894-137">.NET 4.5.1 и более поздние версии доступны в [центре загрузки Майкрософт](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span><span class="sxs-lookup"><span data-stu-id="60894-137">- .Net 4.5.1 and later releases are available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span> |

<span data-ttu-id="60894-138">Ознакомьтесь с требованиями [для Azure Active Directory Connect](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-prerequisites) для получения сведений о требованиях к оборудованию, программному обеспечению, учетным записям и разрешениям, ТРЕБОВАНИЯх SSL-сертификатов и ограничению объектов для Azure AD Connect.</span><span class="sxs-lookup"><span data-stu-id="60894-138">See [Prerequisites for Azure Active Directory Connect](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-prerequisites) for the details of hardware, software, account and permissions requirements, SSL certificate requirements, and object limits for Azure AD Connect.</span></span>
  
<span data-ttu-id="60894-139">Вы также можете ознакомиться с журналом выпусков для [версии](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-version-history) Azure AD Connect, чтобы узнать, какие из них включены и исправлены в каждом выпуске.</span><span class="sxs-lookup"><span data-stu-id="60894-139">You can also review the Azure AD Connect [version release history](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-version-history) to see what is included and fixed in each release.</span></span>

## <a name="2-install-azure-ad-connect-and-configure-directory-synchronization"></a><span data-ttu-id="60894-140">2. Установка Azure AD Connect и Настройка синхронизации службы каталогов</span><span class="sxs-lookup"><span data-stu-id="60894-140">2. Install Azure AD Connect and configure directory synchronization</span></span>

<span data-ttu-id="60894-141">Прежде чем приступать к работе, убедитесь в том, что у вас есть:</span><span class="sxs-lookup"><span data-stu-id="60894-141">Before you begin, make sure you have:</span></span>

- <span data-ttu-id="60894-142">Имя пользователя и пароль глобального администратора Office 365</span><span class="sxs-lookup"><span data-stu-id="60894-142">The user name and password of an Office 365 global admin</span></span>
- <span data-ttu-id="60894-143">Имя пользователя и пароль администратора домена доменных служб Active Directory</span><span class="sxs-lookup"><span data-stu-id="60894-143">The user name and password of an AD DS domain administrator</span></span>
- <span data-ttu-id="60894-144">Какой метод проверки подлинности (ФС, ПТА, федеративный)</span><span class="sxs-lookup"><span data-stu-id="60894-144">Which authentication method (PHS, PTA, federated)</span></span>
- <span data-ttu-id="60894-145">Необходимость использования [единого входа Azure AD с единым входом (SSO)](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-sso)</span><span class="sxs-lookup"><span data-stu-id="60894-145">Whether you want to use [Azure AD Seamless Single Sign-on (SSO)](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-sso)</span></span>

<span data-ttu-id="60894-146">Выполните следующие действия:</span><span class="sxs-lookup"><span data-stu-id="60894-146">Follow these steps:</span></span>

1. <span data-ttu-id="60894-147">Войдите в [центр администрирования Microsoft 365](https://admin.microsoft.com) (https://admin.microsoft.com) и выберите **Пользователи** \> **Активные пользователи** на левой панели навигации).</span><span class="sxs-lookup"><span data-stu-id="60894-147">Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com) (https://admin.microsoft.com) and choose **Users** \> **Active Users** on the left navigation.</span></span>
2. <span data-ttu-id="60894-148">В центре администрирования на странице **Активные пользователи** выберите пункт **больше** \> **синхронизации службы каталогов**.</span><span class="sxs-lookup"><span data-stu-id="60894-148">In the admin center, on the **Active users** page, choose **More** \> **Directory synchronization**.</span></span>

    ![В меню Дополнительно выберите пункт Синхронизация службы каталогов.](media/dc6669e5-c01b-471e-9cdf-04f5d44e1c4b.png)
  
3. <span data-ttu-id="60894-150">На странице " **Подготовка Active Directory** " выберите ссылку **скачать средство Microsoft Azure Active Directory Connect** , чтобы приступить к работе.</span><span class="sxs-lookup"><span data-stu-id="60894-150">On the **Active Directory preparation** page, select the **Download Microsoft Azure Active Directory Connect tool** link to get started.</span></span> 
4. <span data-ttu-id="60894-151">Выполните действия, описанные в статье [план установки работоспособности Azure AD Connect и Azure AD Connect](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-roadmap).</span><span class="sxs-lookup"><span data-stu-id="60894-151">Follow the steps in [Azure AD Connect and Azure AD Connect Health installation roadmap](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-roadmap).</span></span>

## <a name="3-finish-setting-up-domains"></a><span data-ttu-id="60894-152">3. Завершение настройки доменов</span><span class="sxs-lookup"><span data-stu-id="60894-152">3. Finish setting up domains</span></span>

<span data-ttu-id="60894-153">Выполните действия, описанные в статье [CREATE DNS Records for Office 365, когда вы управляете записями DNS](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23) для завершения настройки доменов.</span><span class="sxs-lookup"><span data-stu-id="60894-153">Follow the steps in [Create DNS records for Office 365 when you manage your DNS records](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23) to finish setting up your domains.</span></span>

## <a name="next-step"></a><span data-ttu-id="60894-154">Следующий шаг</span><span class="sxs-lookup"><span data-stu-id="60894-154">Next step</span></span>

<span data-ttu-id="60894-155">[Назначение лицензий учетным записям пользователей](assign-licenses-to-user-accounts.md).</span><span class="sxs-lookup"><span data-stu-id="60894-155">[Assign licenses to user accounts](assign-licenses-to-user-accounts.md).</span></span>
