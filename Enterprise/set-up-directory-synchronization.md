---
title: Настройка синхронизации каталогов для Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
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
ms.openlocfilehash: 5f6e5be2a2137ee183a7d592d9a3e6b086e5be9a
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085268"
---
# <a name="set-up-directory-synchronization-for-office-365"></a><span data-ttu-id="b0765-103">Настройка синхронизации каталогов для Office 365</span><span class="sxs-lookup"><span data-stu-id="b0765-103">Set up directory synchronization for Office 365</span></span>

<span data-ttu-id="b0765-p101">В Office 365 для управления пользователями используется облачная служба управления удостоверениями Azure Active Directory. Вы также можете интегрировать локальную службу Active Directory с Azure AD, синхронизируя локальную среду с Office 365. После настройки синхронизации можно использовать проверку подлинности пользователей в Azure AD или в локальном каталоге.</span><span class="sxs-lookup"><span data-stu-id="b0765-p101">Office 365 uses the cloud-based user identity management service Azure Active Directory to manage users. You can also integrate your on-premises Active Directory with Azure AD by synchronizing your on-premises environment with Office 365. Once you set up synchronization you can decide to have their user authentication take place within Azure AD or within your on-premises directory.</span></span>
  
## <a name="office-365-directory-synchronization"></a><span data-ttu-id="b0765-107">Синхронизация каталогов Office 365</span><span class="sxs-lookup"><span data-stu-id="b0765-107">Office 365 directory synchronization</span></span>

<span data-ttu-id="b0765-p102">Вы можете использовать синхронизированное удостоверение или федеративный идентификатор между локальной организацией и Office 365. С помощью синхронизированного удостоверения вы управляете локальными пользователями и проходят проверку подлинности с помощью Azure AD, когда они используют один и тот же пароль в облаке в локальной среде. Это наиболее распространенный сценарий синхронизации каталогов. Сквозная проверка подлинности или федеративного удостоверения позволяет управлять локальными пользователями и проходить их проверку подлинности в локальном каталоге. Для федеративного удостоверения требуется дополнительная настройка, и пользователи могут выполнять только один вход. Для получения дополнительных сведений ознакомьтесь со сведениями [об удостоверенИи Office 365 и Azure Active Directory](about-office-365-identity.md).</span><span class="sxs-lookup"><span data-stu-id="b0765-p102">You can either use synchronized identity or federated identity between your on-premises organization and Office 365. With synchronized identity, you manage your users on-premises, and they are authenticated by Azure AD when they use the same password in the cloud as on-premises. This is the most common directory synchronization scenario. Pass-through authentication or Federated identity, allows you to manage your users on-premises and they are authenticated by your on-premises directory. Federated identity requires additional configuration and enables your users to only sign in once. For details, read [Understanding Office 365 Identity and Azure Active Directory](about-office-365-identity.md).</span></span>
  
## <a name="want-to-upgrade-from-windows-azure-active-directory-sync-dirsync-to-azure-active-directory-connect"></a><span data-ttu-id="b0765-114">Хотите обновить синхронизацию с Windows Azure Active Directory (DirSync) до Azure Active Directory Connect?</span><span class="sxs-lookup"><span data-stu-id="b0765-114">Want to upgrade from Windows Azure Active Directory sync (DirSync) to Azure Active Directory Connect?</span></span>

<span data-ttu-id="b0765-115">Если вы используете DirSync и хотите выполнить обновление, перейдите к [Azure.com](https://azure.com) для [получения инструкций](https://go.microsoft.com/fwlink/p/?LinkId=733240)по обновлению.</span><span class="sxs-lookup"><span data-stu-id="b0765-115">If you are currently using DirSync and want to upgrade, head over to [azure.com](https://azure.com) for [upgrade instructions](https://go.microsoft.com/fwlink/p/?LinkId=733240).</span></span>
  
## <a name="prerequisites-for-azure-ad-connect"></a><span data-ttu-id="b0765-116">Необходимые условия для Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="b0765-116">Prerequisites for Azure AD Connect</span></span>

<span data-ttu-id="b0765-p103">Вы получаете бесплатную подписку на Azure AD с вашей подпиской на Office 365. Когда вы настраиваете синхронизацию службы каталогов, вы сможете установить Azure Active Directory Connect на одном из локальных серверов.</span><span class="sxs-lookup"><span data-stu-id="b0765-p103">You get a free subscription to Azure AD with your Office 365 subscription. When you set up directory synchronization, you will install Azure Active Directory Connect on one of your on-premises servers.</span></span>
  
<span data-ttu-id="b0765-119">Для Office 365 вам потребуется выполнить следующие действия:</span><span class="sxs-lookup"><span data-stu-id="b0765-119">For Office 365 you will need to:</span></span>
  
- <span data-ttu-id="b0765-120">Проверка локального домена (процедура поможет вам выполнить указанные ниже действия).</span><span class="sxs-lookup"><span data-stu-id="b0765-120">Verify your on-premises domain (the procedure will guide you through this).</span></span>
- <span data-ttu-id="b0765-121">[Назначьте роли администратора в office 365 для бизнес](https://support.office.com/article/EAC4D046-1AFD-4F1A-85FC-8219C79E1504) -разрешений для клиента Office 365 и локального каталога Active Directory.</span><span class="sxs-lookup"><span data-stu-id="b0765-121">Have [Assign admin roles in Office 365 for business](https://support.office.com/article/EAC4D046-1AFD-4F1A-85FC-8219C79E1504) permissions for your Office 365 tenant and on-premises Active Directory.</span></span>

<span data-ttu-id="b0765-122">Для локального сервера, на котором вы устанавливаете Azure AD Connect, вам потребуется следующее программное обеспечение:</span><span class="sxs-lookup"><span data-stu-id="b0765-122">For your on-premises server on which you install Azure AD Connect you will need the following software:</span></span>
  
|<span data-ttu-id="b0765-123">**Серверная операционная система**</span><span class="sxs-lookup"><span data-stu-id="b0765-123">**Server OS**</span></span>|<span data-ttu-id="b0765-124">\*\*другое программное обеспечение. \*\*</span><span class="sxs-lookup"><span data-stu-id="b0765-124">**Other software**</span></span>|
|:-----|:-----|
|<span data-ttu-id="b0765-125">**Windows Server 2012 R2**</span><span class="sxs-lookup"><span data-stu-id="b0765-125">**Windows Server 2012 R2**</span></span> | <span data-ttu-id="b0765-126">-PowerShell устанавливается по умолчанию, никакие действия не требуются.</span><span class="sxs-lookup"><span data-stu-id="b0765-126">- PowerShell is installed by default, no action is required.</span></span>  <br> <span data-ttu-id="b0765-p104">– NET 4.5.1 и более поздние версии предлагаются через обновление Windows. Убедитесь, что установлены последние обновления для Windows Server на панели управления.</span><span class="sxs-lookup"><span data-stu-id="b0765-p104">- Net 4.5.1 and later releases are offered through Windows Update. Make sure you have installed the latest updates to Windows Server in the Control Panel.</span></span> |
|<span data-ttu-id="b0765-129">**Windows server 2008 R2 с пакетом обновления 1 (SP1)** или **Windows Server 2012**</span><span class="sxs-lookup"><span data-stu-id="b0765-129">**Windows Server 2008 R2 with Service Pack 1 (SP1)** or **Windows Server 2012**</span></span> | <span data-ttu-id="b0765-p105">— Последняя версия PowerShell доступна в Windows Management Framework 4,0. Выполните поиск в [центре загрузки Майкрософт](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span><span class="sxs-lookup"><span data-stu-id="b0765-p105">- The latest version of PowerShell is available in Windows Management Framework 4.0. Search for it on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).  </span></span><br> <span data-ttu-id="b0765-132">.NET 4.5.1 и более поздние версии доступны в [центре загрузки Майкрософт](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span><span class="sxs-lookup"><span data-stu-id="b0765-132">- .Net 4.5.1 and later releases are available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span> |
|<span data-ttu-id="b0765-133">**Windows Server 2008**</span><span class="sxs-lookup"><span data-stu-id="b0765-133">**Windows Server 2008**</span></span> | <span data-ttu-id="b0765-134">-Последняя поддерживаемая версия PowerShell доступна в Windows Management Framework 3,0, которая доступна в [центре загрузки Майкрософт](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span><span class="sxs-lookup"><span data-stu-id="b0765-134">- The latest supported version of PowerShell is available in Windows Management Framework 3.0, available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span>  <br> <span data-ttu-id="b0765-135">.NET 4.5.1 и более поздние версии доступны в [центре загрузки Майкрософт](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span><span class="sxs-lookup"><span data-stu-id="b0765-135">- .Net 4.5.1 and later releases are available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span> |

> [!NOTE]
> <span data-ttu-id="b0765-p106">Если вы используете Azure Active Directory DirSync, максимальное число членов группы рассылки, которые можно синхронизировать из локального каталога Active Directory с Azure Active Directory, — 15 000. Для Azure AD Connect это число равно 50 000.</span><span class="sxs-lookup"><span data-stu-id="b0765-p106">If you're using Azure Active Directory DirSync, the maximum number of distribution group members that you can synchronize from your on-premises Active Directory to Azure Active Directory is 15,000. For Azure AD Connect, that number is 50,000.</span></span> 
  
<span data-ttu-id="b0765-138">Чтобы тщательно проанализировать требования к оборудованию, программному обеспечению, учетным записям и разрешениям, требования к сертификатам SSL и ограничению объектов для Azure AD Connect, прочитайте [необходимые компоненты для Azure Active Directory Connect](https://go.microsoft.com/fwlink/p/?LinkId=716896).</span><span class="sxs-lookup"><span data-stu-id="b0765-138">To more carefully review hardware, software, account and permissions requirements, SSL certificate requirements, and object limits for Azure AD Connect, read [Prerequisites for Azure Active Directory Connect](https://go.microsoft.com/fwlink/p/?LinkId=716896).</span></span>
  
<span data-ttu-id="b0765-139">Вы также можете ознакомиться с журналом выпусков для [версии](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-version-history) Azure AD Connect, чтобы узнать, какие из них включены и исправлены в каждом выпуске.</span><span class="sxs-lookup"><span data-stu-id="b0765-139">You can also review the Azure AD Connect [version release history](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-version-history) to see what is included and fixed in each release.</span></span>

## <a name="to-set-up-directory-synchronization"></a><span data-ttu-id="b0765-140">Настройка синхронизации службы каталогов</span><span class="sxs-lookup"><span data-stu-id="b0765-140">To set up directory synchronization</span></span>

1. <span data-ttu-id="b0765-141">войдите в центр администрирования Office 365 и выберите **пользователи** \> **активные пользователи** на левой панели навигации.</span><span class="sxs-lookup"><span data-stu-id="b0765-141">Sign in to the Office 365 admin center and choose **Users** \> **Active Users** on the left navigation.</span></span>
2. <span data-ttu-id="b0765-142">в центре администрирования Office 365 на странице **активные пользователи** выберите пункт **больше** \> **синхронизации службы каталогов**.</span><span class="sxs-lookup"><span data-stu-id="b0765-142">In the Office 365 admin center, on the **Active users** page, choose **More** \> **Directory synchronization**.</span></span>

    ![В меню Дополнительно выберите пункт Синхронизация службы каталогов.](media/dc6669e5-c01b-471e-9cdf-04f5d44e1c4b.png)
  
3. <span data-ttu-id="b0765-p107">На странице " **Подготовка Active Directory** " выберите ссылку **скачать средство Microsoft Azure Active Directory Connect** , чтобы приступить к работе. Дополнительные сведения о процессе установки Azure Active Directory Connect можно найти в статье [план установки Azure AD Connect и Azure AD Connect Health](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-roadmap).</span><span class="sxs-lookup"><span data-stu-id="b0765-p107">On the **Active Directory preparation** page, select the **Download Microsoft Azure Active Directory Connect tool** link to get started. For more information about the Azure Active Directory Connect installation process, see [Azure AD Connect and Azure AD Connect Health installation roadmap](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-roadmap).</span></span>

## <a name="assign-licenses-to-synchronized-users"></a><span data-ttu-id="b0765-146">Назначение лицензий синхронизированным пользователям</span><span class="sxs-lookup"><span data-stu-id="b0765-146">Assign licenses to synchronized users</span></span>

<span data-ttu-id="b0765-p108">После синхронизации пользователей с Office 365 они будут созданы, но вам нужно назначить им лицензии, чтобы они могли использовать функции Office 365, такие как почта. Инструкции приведены в статье [Назначение лицензий пользователям в Office 365 для бизнеса](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc).</span><span class="sxs-lookup"><span data-stu-id="b0765-p108">After you have synchronized your users to Office 365, they are created but you need to assign licenses to them so they can use Office 365 features, such as mail. For instructions, see [Assign licenses to users in Office 365 for business](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc).</span></span>

## <a name="finish-setting-up-domains"></a><span data-ttu-id="b0765-149">Завершение настройки доменов</span><span class="sxs-lookup"><span data-stu-id="b0765-149">Finish setting up domains</span></span>

<span data-ttu-id="b0765-150">Выполните действия, описанные в статье [CREATE DNS Records for Office 365, когда вы управляете записями DNS](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23) для завершения настройки доменов.</span><span class="sxs-lookup"><span data-stu-id="b0765-150">Follow the steps in [Create DNS records for Office 365 when you manage your DNS records](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23) to finish setting up your domains.</span></span>