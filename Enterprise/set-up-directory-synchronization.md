---
title: Настройка синхронизации службы каталогов для Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/03/2019
audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
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
description: Узнайте, как настроить синхронизацию каталогов между Office 365 и локальной службой Active Directory.
ms.openlocfilehash: d549d2b56ef1d642e5dfc16b747e6eb909dd7337
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844050"
---
# <a name="set-up-directory-synchronization-for-office-365"></a><span data-ttu-id="17beb-103">Настройка синхронизации службы каталогов для Office 365</span><span class="sxs-lookup"><span data-stu-id="17beb-103">Set up directory synchronization for Office 365</span></span>

<span data-ttu-id="17beb-104">*Эта статья относится к Office 365 корпоративный и Microsoft 365 корпоративный.*</span><span class="sxs-lookup"><span data-stu-id="17beb-104">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="17beb-105">В Office 365 используется клиент Azure Active Directory (Azure AD) для хранения удостоверений и управления ими для проверки подлинности и разрешений на доступ к облачным ресурсам.</span><span class="sxs-lookup"><span data-stu-id="17beb-105">Office 365 uses an Azure Active Directory (Azure AD) tenant to store and manage identities for authentication and permissions to access cloud-based resources.</span></span> 

<span data-ttu-id="17beb-106">Если у вас есть локальные доменные службы Active Directory, вы можете синхронизировать учетные записи пользователей, группы и контакты доменных служб Active Directory с клиентом Azure AD для вашей подписки на Office 365.</span><span class="sxs-lookup"><span data-stu-id="17beb-106">If you have an on-premises Active Directory Domain Services (AD DS), you can synchronize your AD DS user accounts, groups, and contacts with the Azure AD tenant of your Office 365 subscription.</span></span> <span data-ttu-id="17beb-107">Это гибридное удостоверение для Office 365.</span><span class="sxs-lookup"><span data-stu-id="17beb-107">This is hybrid identity for Office 365.</span></span> <span data-ttu-id="17beb-108">Ниже перечислены его компоненты.</span><span class="sxs-lookup"><span data-stu-id="17beb-108">Here are its components.</span></span>

![Компоненты синхронизации каталогов для Office 365](./media/about-office-365-identity/hybrid-identity.png)

<span data-ttu-id="17beb-110">Azure AD Connect запускается на локальном сервере и синхронизирует ваши доменные службы Active Directory с клиентом Azure AD.</span><span class="sxs-lookup"><span data-stu-id="17beb-110">Azure AD Connect runs on an on-premises server and synchronizes your AD DS with the Azure AD tenant.</span></span> <span data-ttu-id="17beb-111">Одновременно с синхронизацией каталогов вы можете также задать приведенные ниже параметры проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="17beb-111">Along with directory synchronization, you can also specify these authentication options:</span></span>

- <span data-ttu-id="17beb-112">Синхронизация хэша паролей (PHS)</span><span class="sxs-lookup"><span data-stu-id="17beb-112">Password hash synchronization (PHS)</span></span>

  <span data-ttu-id="17beb-113">Проверка подлинности выполняется с помощью Azure AD.</span><span class="sxs-lookup"><span data-stu-id="17beb-113">Azure AD performs the authentication itself.</span></span>

- <span data-ttu-id="17beb-114">Сквозная проверка подлинности (PTA)</span><span class="sxs-lookup"><span data-stu-id="17beb-114">Pass-through authentication (PTA)</span></span>

  <span data-ttu-id="17beb-115">Проверка подлинности выполняется с помощью доменных служб Aсtive Directory в Azure AD.</span><span class="sxs-lookup"><span data-stu-id="17beb-115">Azure AD has AD DS perform the authentication.</span></span>

- <span data-ttu-id="17beb-116">Федеративная проверка подлинности</span><span class="sxs-lookup"><span data-stu-id="17beb-116">Federated authentication</span></span>

  <span data-ttu-id="17beb-117">Azure AD перенаправляет клиентский компьютер, запрашивающий проверку подлинности, установить контакт с другим поставщиком удостоверений.</span><span class="sxs-lookup"><span data-stu-id="17beb-117">Azure AD redirects the client computer requesting authentication to contact another identity provider.</span></span>

<span data-ttu-id="17beb-118">Дополнительные сведения см. в статье [Гибридные удостоверения](plan-for-directory-synchronization.md).</span><span class="sxs-lookup"><span data-stu-id="17beb-118">See [Hybrid identities](plan-for-directory-synchronization.md) for more information.</span></span>
  
## <a name="1-review-prerequisites-for-azure-ad-connect"></a><span data-ttu-id="17beb-119">1. Необходимые условия для Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="17beb-119">1. Review prerequisites for Azure AD Connect</span></span>

<span data-ttu-id="17beb-120">Вы получаете бесплатную подписку на Azure AD вместе со своей подпиской на Office 365.</span><span class="sxs-lookup"><span data-stu-id="17beb-120">You get a free Azure AD subscription with your Office 365 subscription.</span></span> <span data-ttu-id="17beb-121">При настройке синхронизации каталогов вы устанавливаете Azure AD Connect на одном из локальных серверов.</span><span class="sxs-lookup"><span data-stu-id="17beb-121">When you set up directory synchronization, you will install Azure AD Connect on one of your on-premises servers.</span></span>
  
<span data-ttu-id="17beb-122">Для Office 365 вам потребуется</span><span class="sxs-lookup"><span data-stu-id="17beb-122">For Office 365 you'll need to:</span></span>
  
- <span data-ttu-id="17beb-123">Проверка локального домена.</span><span class="sxs-lookup"><span data-stu-id="17beb-123">Verify your on-premises domain.</span></span> <span data-ttu-id="17beb-124">Мастер Azure AD Connect направляет этот процесс.</span><span class="sxs-lookup"><span data-stu-id="17beb-124">The Azure AD Connect wizard guides you through this.</span></span>
- <span data-ttu-id="17beb-125">Получение имен пользователей и паролей для учетных записей администратора клиента Office 365 и доменных служб Active Directory.</span><span class="sxs-lookup"><span data-stu-id="17beb-125">Obtain the user names and passwords for the admin accounts of your Office 365 tenant and AD DS.</span></span>

<span data-ttu-id="17beb-126">Для локального сервера, на котором выполняется установка Azure AD Connect, вам потребуется</span><span class="sxs-lookup"><span data-stu-id="17beb-126">For your on-premises server on which you install Azure AD Connect, you'll need:</span></span>
  
|<span data-ttu-id="17beb-127">**Серверная ОС**</span><span class="sxs-lookup"><span data-stu-id="17beb-127">**Server OS**</span></span>|<span data-ttu-id="17beb-128">**Другое ПО**</span><span class="sxs-lookup"><span data-stu-id="17beb-128">**Other software**</span></span>|
|:-----|:-----|
|<span data-ttu-id="17beb-129">Windows Server 2012 R2 и более поздних версий</span><span class="sxs-lookup"><span data-stu-id="17beb-129">Windows Server 2012 R2 and later</span></span> | <span data-ttu-id="17beb-130">- PowerShell устанавливается по умолчанию; никаких действий не требуется.</span><span class="sxs-lookup"><span data-stu-id="17beb-130">- PowerShell is installed by default, no action is required.</span></span>  <br> <span data-ttu-id="17beb-131">- Net 4.5.1 и более поздние выпуски можно получить через Центр обновления Windows.</span><span class="sxs-lookup"><span data-stu-id="17beb-131">- Net 4.5.1 and later releases are offered through Windows Update.</span></span> <span data-ttu-id="17beb-132">На панели управления убедитесь в том, что установлены последние обновления для Windows Server.</span><span class="sxs-lookup"><span data-stu-id="17beb-132">Make sure you have installed the latest updates to Windows Server in the Control Panel.</span></span> |
|<span data-ttu-id="17beb-133">Windows Server 2008 R2 с пакетом обновления 1 (SP1)\*\* или Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="17beb-133">Windows Server 2008 R2 with Service Pack 1 (SP1)\*\* or Windows Server 2012</span></span> | <span data-ttu-id="17beb-134">- Последняя версия PowerShell доступна в составе платформы Windows Management Framework 4.0.</span><span class="sxs-lookup"><span data-stu-id="17beb-134">- The latest version of PowerShell is available in Windows Management Framework 4.0.</span></span> <span data-ttu-id="17beb-135">Найти ее можно в [Центре загрузки Майкрософт](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span><span class="sxs-lookup"><span data-stu-id="17beb-135">Search for it on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span>  <br> <span data-ttu-id="17beb-136">- .Net 4.5.1 и более поздние выпуски доступны в [Центре загрузки Майкрософт](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span><span class="sxs-lookup"><span data-stu-id="17beb-136">- .Net 4.5.1 and later releases are available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span> |
|<span data-ttu-id="17beb-137">Windows Server 2008</span><span class="sxs-lookup"><span data-stu-id="17beb-137">Windows Server 2008</span></span> | <span data-ttu-id="17beb-138">Последняя поддерживаемая версия PowerShell доступна в составе платформы Windows Management Framework 3.0, которую можно найти в [Центре загрузки Майкрософт](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span><span class="sxs-lookup"><span data-stu-id="17beb-138">- The latest supported version of PowerShell is available in Windows Management Framework 3.0, available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span>  <br> <span data-ttu-id="17beb-139">- .Net 4.5.1 и более поздние выпуски доступны в [Центре загрузки Майкрософт](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span><span class="sxs-lookup"><span data-stu-id="17beb-139">- .Net 4.5.1 and later releases are available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span> |

<span data-ttu-id="17beb-140">Более подробно ознакомиться с требованиями к оборудованию, программному обеспечению, учетным записям, разрешениям и SSL-сертификатам, а также с ограничениями на объекты для Azure AD Connect можно в статье [Необходимые условия для Azure AD Connect](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-prerequisites).</span><span class="sxs-lookup"><span data-stu-id="17beb-140">See [Prerequisites for Azure Active Directory Connect](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-prerequisites) for the details of hardware, software, account and permissions requirements, SSL certificate requirements, and object limits for Azure AD Connect.</span></span>
  
<span data-ttu-id="17beb-141">Вы также можете ознакомиться с [журналом выпуска версий](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-version-history) Azure AD Connect, чтобы выяснить, что добавилось или было исправлено в каждой версии.</span><span class="sxs-lookup"><span data-stu-id="17beb-141">You can also review the Azure AD Connect [version release history](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-version-history) to see what is included and fixed in each release.</span></span>

## <a name="2-install-azure-ad-connect-and-configure-directory-synchronization"></a><span data-ttu-id="17beb-142">2. Установка Azure AD Connect и настройка синхронизации каталогов.</span><span class="sxs-lookup"><span data-stu-id="17beb-142">2. Install Azure AD Connect and configure directory synchronization</span></span>

<span data-ttu-id="17beb-143">Перед началом вам необходимо иметь</span><span class="sxs-lookup"><span data-stu-id="17beb-143">Before you begin, make sure you have:</span></span>

- <span data-ttu-id="17beb-144">Имя пользователя и пароль глобального администратора Office 365.</span><span class="sxs-lookup"><span data-stu-id="17beb-144">The user name and password of an Office 365 global admin</span></span>
- <span data-ttu-id="17beb-145">Имя пользователя и пароль администратора доменных служб Active Directory</span><span class="sxs-lookup"><span data-stu-id="17beb-145">The user name and password of an AD DS domain administrator</span></span>
- <span data-ttu-id="17beb-146">Метод проверки подлинности (синхронизация хэша паролей, сквозная или федеративная)</span><span class="sxs-lookup"><span data-stu-id="17beb-146">Which authentication method (PHS, PTA, federated)</span></span>
- <span data-ttu-id="17beb-147">Либо [Простой единый вход Azure AD](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-sso) по вашему желанию.</span><span class="sxs-lookup"><span data-stu-id="17beb-147">Whether you want to use [Azure AD Seamless Single Sign-on (SSO)](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-sso)</span></span>

<span data-ttu-id="17beb-148">Выполните приведенные ниже действия.</span><span class="sxs-lookup"><span data-stu-id="17beb-148">Follow these steps:</span></span>

1. <span data-ttu-id="17beb-149">Войдите в [Центр администрирования Microsoft 365](https://admin.microsoft.com) https://admin.microsoft.com)и в области навигации слева выберите пункты **Пользователи** \> ** > Активные пользователи**.</span><span class="sxs-lookup"><span data-stu-id="17beb-149">Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com) (https://admin.microsoft.com) and choose **Users** \> **Active Users** on the left navigation.</span></span>
2. <span data-ttu-id="17beb-150">На странице **Активные пользователи** выберите пункт **больше** (три точки) \> **синхронизации каталогов**.</span><span class="sxs-lookup"><span data-stu-id="17beb-150">On the **Active users** page, choose **More** (three dots) \> **Directory synchronization**.</span></span>
  
3. <span data-ttu-id="17beb-151">На странице " **Подготовка Azure Active Directory** " щелкните ссылку **Перейти в центр загрузки, чтобы получить ссылку на средство Azure AD Connect** , чтобы приступить к работе.</span><span class="sxs-lookup"><span data-stu-id="17beb-151">On the **Azure Active Directory preparation** page, select the **Go to the Download center to get the Azure AD Connect tool** link to get started.</span></span> 
4. <span data-ttu-id="17beb-152">Выполните действия в статье [План установки Azure AD Connect и Azure AD Connect Health](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-roadmap).</span><span class="sxs-lookup"><span data-stu-id="17beb-152">Follow the steps in [Azure AD Connect and Azure AD Connect Health installation roadmap](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-roadmap).</span></span>

## <a name="3-finish-setting-up-domains"></a><span data-ttu-id="17beb-153">3. Завершение настройки доменов</span><span class="sxs-lookup"><span data-stu-id="17beb-153">3. Finish setting up domains</span></span>

<span data-ttu-id="17beb-154">Инструкции по завершению настройки доменов см. в статье [Создание записей DNS для Office 365 при самостоятельном управлении записями DNS](https://docs.microsoft.com/office365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider).</span><span class="sxs-lookup"><span data-stu-id="17beb-154">Follow the steps in [Create DNS records for Office 365 when you manage your DNS records](https://docs.microsoft.com/office365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider) to finish setting up your domains.</span></span>

## <a name="next-step"></a><span data-ttu-id="17beb-155">Следующий этап</span><span class="sxs-lookup"><span data-stu-id="17beb-155">Next step</span></span>

[<span data-ttu-id="17beb-156">Назначение лицензий учетным записям пользователей</span><span class="sxs-lookup"><span data-stu-id="17beb-156">Assign licenses to user accounts</span></span>](assign-licenses-to-user-accounts.md)
