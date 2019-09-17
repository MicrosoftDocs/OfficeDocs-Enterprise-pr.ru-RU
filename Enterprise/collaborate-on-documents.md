---
title: Совместное сотрудничество с гостями в документе
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: sharepoint-online
localization_priority: Normal
description: Узнайте, как совместно работать с гостями в документе в SharePoint и OneDrive.
ms.openlocfilehash: c0c74f2457e9b25b37355c58ed18f120261e3364
ms.sourcegitcommit: 3bba97053caf5f9cff0ef3205afb7869535f38bd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/16/2019
ms.locfileid: "36992408"
---
# <a name="collaborate-with-guests-on-a-document"></a><span data-ttu-id="06289-103">Совместное сотрудничество с гостями в документе</span><span class="sxs-lookup"><span data-stu-id="06289-103">Collaborate with guests on a document</span></span>

<span data-ttu-id="06289-104">Если вам требуется совместная работа с гостями в документах в SharePoint или OneDrive, вы можете отправить им ссылку для совместного доступа к документу.</span><span class="sxs-lookup"><span data-stu-id="06289-104">If you need to collaborate with guests on documents in SharePoint or OneDrive, you can send them a sharing link to the document.</span></span> <span data-ttu-id="06289-105">В этой статье мы рассмотрим действия по настройке Microsoft 365, необходимые для настройки ссылок общего доступа для SharePoint и OneDrive.</span><span class="sxs-lookup"><span data-stu-id="06289-105">In this article, we'll walk through the Microsoft 365 configuration steps necessary to set up sharing links for SharePoint and OneDrive.</span></span>

## <a name="azure-organizational-relationships-settings"></a><span data-ttu-id="06289-106">Параметры связей в Организации Azure</span><span class="sxs-lookup"><span data-stu-id="06289-106">Azure Organizational relationships settings</span></span>

<span data-ttu-id="06289-107">Общий доступ в Microsoft 365 регулируется на самом высоком уровне параметрами организационных отношений в Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="06289-107">Sharing in Microsoft 365 is governed at its highest level by the organizational relationships settings in Azure Active Directory.</span></span> <span data-ttu-id="06289-108">Если общий доступ к гостям отключен или ограничен в Azure AD, все параметры общего доступа, настроенные в Microsoft 365, будут переопределены.</span><span class="sxs-lookup"><span data-stu-id="06289-108">If guest sharing is disabled or restricted in Azure AD, this will override any sharing settings that you configure in Microsoft 365.</span></span>

<span data-ttu-id="06289-109">Проверьте параметры организационных отношений, чтобы предотвратить блокировку общего доступа с гостями.</span><span class="sxs-lookup"><span data-stu-id="06289-109">Check the organizational relationships settings to ensure that sharing with guests is not blocked.</span></span>

![Снимок экрана: страница параметров организационных отношений для Azure Active Directory](media/azure-ad-organizational-relationships-settings.png)

<span data-ttu-id="06289-111">Настройка параметров организационных отношений</span><span class="sxs-lookup"><span data-stu-id="06289-111">To set organizational relationship settings</span></span>

1. <span data-ttu-id="06289-112">Выполните вход в Microsoft Azure по [https://portal.azure.com](https://portal.azure.com)адресу.</span><span class="sxs-lookup"><span data-stu-id="06289-112">Log in to Microsoft Azure at [https://portal.azure.com](https://portal.azure.com).</span></span>
2. <span data-ttu-id="06289-113">В области навигации слева выберите **Azure Active Directory**.</span><span class="sxs-lookup"><span data-stu-id="06289-113">In the left navigation, click **Azure Active Directory**.</span></span>
3. <span data-ttu-id="06289-114">В области **Обзор** щелкните **организационные связи**.</span><span class="sxs-lookup"><span data-stu-id="06289-114">In the **Overview** pane, click **Organizational relationships**.</span></span>
4. <span data-ttu-id="06289-115">В области **организационные связи** щелкните **Параметры**.</span><span class="sxs-lookup"><span data-stu-id="06289-115">In the **Organizational relationships** pane, click **Settings**.</span></span>
5. <span data-ttu-id="06289-116">Убедитесь, что у **администраторов и пользователей в роли гостя может быть приглашение** , а **Участники** — значение **Да**.</span><span class="sxs-lookup"><span data-stu-id="06289-116">Ensure that **Admins and users in the guest inviter role can invite** and **Members can invite** are both set to **Yes**.</span></span>
6. <span data-ttu-id="06289-117">Если вы внесли изменения, нажмите кнопку **сохранить**.</span><span class="sxs-lookup"><span data-stu-id="06289-117">If you made changes, click **Save**.</span></span>

<span data-ttu-id="06289-118">Обратите внимание на параметры в разделе **ограничения совместной работы** .</span><span class="sxs-lookup"><span data-stu-id="06289-118">Note the settings in the **Collaboration restrictions** section.</span></span> <span data-ttu-id="06289-119">Убедитесь, что домены гостей, с которыми вы хотите работать совместно, не заблокированы.</span><span class="sxs-lookup"><span data-stu-id="06289-119">Make sure that the domains of the guests that you want to collaborate with aren't blocked.</span></span>

## <a name="sharepoint-organization-level-sharing-settings"></a><span data-ttu-id="06289-120">Параметры общего доступа на уровне Организации SharePoint</span><span class="sxs-lookup"><span data-stu-id="06289-120">SharePoint organization level sharing settings</span></span>

<span data-ttu-id="06289-121">Для того, чтобы гости могли иметь доступ к документу в SharePoint или OneDrive, параметры общего доступа на уровне Организации SharePoint и OneDrive должны разрешить доступ к гостям.</span><span class="sxs-lookup"><span data-stu-id="06289-121">In order for guests to have access to a document in SharePoint or OneDrive, the SharePoint and OneDrive organization-level sharing settings must allow for sharing with guests.</span></span>

<span data-ttu-id="06289-122">Параметры на уровне Организации для SharePoint определяют параметры, доступные для отдельных сайтов SharePoint.</span><span class="sxs-lookup"><span data-stu-id="06289-122">The organization-level settings for SharePoint determine what settings are available for individual SharePoint sites.</span></span> <span data-ttu-id="06289-123">Параметры сайта не могут быть более разрешительнои, чем параметры на уровне Организации.</span><span class="sxs-lookup"><span data-stu-id="06289-123">Site settings cannot be more permissive than the organization-level settings.</span></span> <span data-ttu-id="06289-124">Настройка уровня Организации для OneDrive определяет уровень общего доступа, доступный в библиотеках OneDrive пользователей.</span><span class="sxs-lookup"><span data-stu-id="06289-124">The organization-level setting for OneDrive determines what level of sharing is available in users' OneDrive libraries.</span></span>

<span data-ttu-id="06289-125">Если вы хотите разрешить общий доступ к файлам и папкам для анонимных пользователей Шарепионт и OneDrive, выберите пункт **все**.</span><span class="sxs-lookup"><span data-stu-id="06289-125">For SharePiont and OneDrive, if you want to allow file and folder sharing with anonymous users, choose **Anyone**.</span></span> <span data-ttu-id="06289-126">Если необходимо обеспечить проверку подлинности для всех гостей, выберите **новые и существующие гости**.</span><span class="sxs-lookup"><span data-stu-id="06289-126">If you want to ensure that all guests have to authenticate, choose **New and existing guests**.</span></span> 

<span data-ttu-id="06289-127">В разделе SharePoint выберите параметры с наибольшим количеством разрешений, которые будут необходимы любому сайту в вашей организации.</span><span class="sxs-lookup"><span data-stu-id="06289-127">For SharePoint, choose the most permissive setting that will be needed by any site in your organization.</span></span>

![Снимок экрана: параметры общего доступа на уровне Организации SharePoint](media/sharepoint-organization-external-sharing-controls.png)


<span data-ttu-id="06289-129">Настройка параметров общего доступа на уровне Организации SharePoint</span><span class="sxs-lookup"><span data-stu-id="06289-129">To set SharePoint organization level sharing settings</span></span>

1. <span data-ttu-id="06289-130">В центре администрирования Microsoft 365 в области навигации слева в разделе **центры администрирования**щелкните **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="06289-130">In the Microsoft 365 admin center, in the left navigation, under **Admin centers**, click **SharePoint**.</span></span>
2. <span data-ttu-id="06289-131">В центре администрирования SharePoint в области навигации слева щелкните **общий доступ**.</span><span class="sxs-lookup"><span data-stu-id="06289-131">In the SharePoint admin center, in the left navigation, click **Sharing**.</span></span>
3. <span data-ttu-id="06289-132">Убедитесь, что для внешнего общего доступа для SharePoint или OneDrive задано значение " **любой пользователь** " или " **новые и существующие гости**".</span><span class="sxs-lookup"><span data-stu-id="06289-132">Ensure that external sharing for SharePoint or OneDrive is set to **Anyone** or **New and existing guests**.</span></span> <span data-ttu-id="06289-133">(Обратите внимание, что параметр OneDrive не может быть более разрешающим, чем параметр SharePoint.)</span><span class="sxs-lookup"><span data-stu-id="06289-133">(Note that the OneDrive setting cannot be more permissive than the SharePoint setting.)</span></span>
4. <span data-ttu-id="06289-134">Если вы внесли изменения, нажмите кнопку **сохранить**.</span><span class="sxs-lookup"><span data-stu-id="06289-134">If you made changes, click **Save**.</span></span>

## <a name="sharepoint-organization-level-default-link-settings"></a><span data-ttu-id="06289-135">Параметры ссылок по умолчанию на уровне Организации SharePoint</span><span class="sxs-lookup"><span data-stu-id="06289-135">SharePoint organization level default link settings</span></span>

<span data-ttu-id="06289-136">Параметры ссылки по умолчанию для файлов и папок определяют, какой вариант ссылки отображается для пользователя по умолчанию при предоставлении общего доступа к файлу или папке.</span><span class="sxs-lookup"><span data-stu-id="06289-136">The default file and folder link settings determine which link option is shown to the user by default when they share a file or folder.</span></span> <span data-ttu-id="06289-137">При необходимости пользователи могут изменить тип ссылки на один из других вариантов, прежде чем предоставлять общий доступ.</span><span class="sxs-lookup"><span data-stu-id="06289-137">Users can change the link type to one of the other options before sharing if desired.</span></span>

<span data-ttu-id="06289-138">Имейте в виду, что этот параметр влияет на сайты SharePoint в Организации, а также на OneDrive.</span><span class="sxs-lookup"><span data-stu-id="06289-138">Keep in mind that this setting affects SharePoint sites in your organization, as well as OneDrive.</span></span>

<span data-ttu-id="06289-139">Выберите тип ссылки, выбранной по умолчанию, когда пользователи совместно используют файлы и папки:</span><span class="sxs-lookup"><span data-stu-id="06289-139">Choose the type of link that's selected by default when users share files and folders:</span></span>

- <span data-ttu-id="06289-140">Если вы ожидаете совместное использование большого числа файлов и папок анонимными пользователями, выберите этот параметр для **ссылки** .</span><span class="sxs-lookup"><span data-stu-id="06289-140">**Anyone with the link** - Choose this option if you expect to share a lot of files and folders with anonymous users.</span></span> <span data-ttu-id="06289-141">Если вы хотите разрешить ссылки для *всех пользователей* , но беспокоитесь о случайном анонимном доступе, примите во внимание один из других параметров, используемый по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="06289-141">If you want to allow *Anyone* links but are concerned about accidental anonymous sharing, consider one of the other options as the default.</span></span> <span data-ttu-id="06289-142">Этот тип ссылки доступен только в том случае, если вы включили **общий доступ** .</span><span class="sxs-lookup"><span data-stu-id="06289-142">This link type is only available if you've enabled **Anyone** sharing.</span></span>
- <span data-ttu-id="06289-143">**Только люди из вашей организации** — выберите этот вариант, если вы хотите, чтобы большая часть общего доступа к файлам и папкам была доступна пользователям в вашей организации.</span><span class="sxs-lookup"><span data-stu-id="06289-143">**Only people in your organization** - Choose this option if you expect most file and folder sharing to be with people inside your organization.</span></span>
- <span data-ttu-id="06289-144">\*\*\*\* Если вы собираетесь делать большой объем общего доступа к файлам и папкам для гостей, используйте этот вариант.</span><span class="sxs-lookup"><span data-stu-id="06289-144">**Specific people** - Consider this option if you expect to do a lot of file and folder sharing with guests.</span></span> <span data-ttu-id="06289-145">Этот тип ссылки работает с гостями и требует проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="06289-145">This type of link works with guests and requires them to authenticate.</span></span>
 
![Снимок экрана: параметры общего доступа к файлам и папкам на уровне Организации SharePoint](media/sharepoint-organization-files-folders-sharing-settings.png)


<span data-ttu-id="06289-147">Настройка параметров ссылок по умолчанию на уровне Организации в SharePoint и OneDrive</span><span class="sxs-lookup"><span data-stu-id="06289-147">To set the SharePoint and OneDrive organization level default link settings</span></span>

1. <span data-ttu-id="06289-148">Перейдите на страницу "общий доступ" в центре администрирования SharePoint.</span><span class="sxs-lookup"><span data-stu-id="06289-148">Navigate to the Sharing page in the SharePoint admin center.</span></span>
2. <span data-ttu-id="06289-149">В разделе **ссылки на файлы и папки**выберите ссылку для совместного доступа по умолчанию, которую нужно использовать.</span><span class="sxs-lookup"><span data-stu-id="06289-149">Under **File and folder links**, select the default sharing link that you want to use.</span></span>
3. <span data-ttu-id="06289-150">Если вы внесли изменения, нажмите кнопку **сохранить**.</span><span class="sxs-lookup"><span data-stu-id="06289-150">If you made changes, click **Save**.</span></span>

## <a name="sharepoint-site-level-sharing-settings"></a><span data-ttu-id="06289-151">Параметры общего доступа на уровне сайта SharePoint</span><span class="sxs-lookup"><span data-stu-id="06289-151">SharePoint site level sharing settings</span></span>

<span data-ttu-id="06289-152">При совместном использовании файлов и фодлерс, которые находятся на сайте SharePoint, необходимо также проверить параметры общего доступа на уровне сайта для этого сайта.</span><span class="sxs-lookup"><span data-stu-id="06289-152">If you're sharing files and fodlers that are in a SharePoint site, you also need to check the site-level sharing settings for that site.</span></span>

![Снимок экрана: параметры внешнего общего доступа к сайту SharePoint](media/sharepoint-site-external-sharing-settings.png)

<span data-ttu-id="06289-154">Установка параметров общего доступа на уровне сайта</span><span class="sxs-lookup"><span data-stu-id="06289-154">To set site-level sharing settings</span></span>
1. <span data-ttu-id="06289-155">В центре администрирования SharePoint в области навигации слева разверните узел **сайты** и выберите пункт **активные сайты**.</span><span class="sxs-lookup"><span data-stu-id="06289-155">In the SharePoint admin center, in the left navigation, expand **Sites** and click **Active sites**.</span></span>
2. <span data-ttu-id="06289-156">Выберите сайт, который вы только что создали.</span><span class="sxs-lookup"><span data-stu-id="06289-156">Select the site that you just created.</span></span>
3. <span data-ttu-id="06289-157">На ленте щелкните **общий доступ**.</span><span class="sxs-lookup"><span data-stu-id="06289-157">In the ribbon, click **Sharing**.</span></span>
4. <span data-ttu-id="06289-158">Убедитесь, что для общего доступа задано значение " **любой пользователь** " или " **новые и существующие гости**".</span><span class="sxs-lookup"><span data-stu-id="06289-158">Ensure that sharing is set to **Anyone** or **New and existing guests**.</span></span>
5. <span data-ttu-id="06289-159">Если вы внесли изменения, нажмите кнопку **сохранить**.</span><span class="sxs-lookup"><span data-stu-id="06289-159">If you made changes, click **Save**.</span></span>

## <a name="invite-users"></a><span data-ttu-id="06289-160">Приглашение пользователей</span><span class="sxs-lookup"><span data-stu-id="06289-160">Invite users</span></span>

<span data-ttu-id="06289-161">Параметры общего доступа к гостям настроены, поэтому теперь пользователи могут предоставлять общий доступ к файлам и папкам гостями.</span><span class="sxs-lookup"><span data-stu-id="06289-161">Guest sharing settings are now configured, so users can now share files and folders with guests.</span></span> <span data-ttu-id="06289-162">Для получения дополнительных сведений см. [общий доступ к файлам и папкам OneDrive](https://support.office.com/article/9fcc2f7d-de0c-4cec-93b0-a82024800c07) и [общий доступ к файлам и папкам SharePoint](https://support.office.com/article/1fe37332-0f9a-4719-970e-d2578da4941c) .</span><span class="sxs-lookup"><span data-stu-id="06289-162">See [Share OneDrive files and folders](https://support.office.com/article/9fcc2f7d-de0c-4cec-93b0-a82024800c07) and [Share SharePoint files or folders](https://support.office.com/article/1fe37332-0f9a-4719-970e-d2578da4941c) for more information.</span></span>

## <a name="see-also"></a><span data-ttu-id="06289-163">См. также</span><span class="sxs-lookup"><span data-stu-id="06289-163">See Also</span></span>
