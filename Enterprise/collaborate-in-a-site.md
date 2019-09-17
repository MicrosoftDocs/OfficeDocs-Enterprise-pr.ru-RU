---
title: Совместное сотрудничество с гостями на сайте
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: sharepoint-online
localization_priority: Normal
description: Узнайте, как совместно работать с гостями на сайте SharePoint.
ms.openlocfilehash: 23f55e22d4c85dcd168c403f50b35f574be9ac07
ms.sourcegitcommit: 3bba97053caf5f9cff0ef3205afb7869535f38bd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/16/2019
ms.locfileid: "36992388"
---
# <a name="collaborate-with-guests-in-a-site"></a><span data-ttu-id="e958e-103">Совместное сотрудничество с гостями на сайте</span><span class="sxs-lookup"><span data-stu-id="e958e-103">Collaborate with guests in a site</span></span>

<span data-ttu-id="e958e-104">При необходимости совместной работы с гостями в документах, данных и списках можно использовать сайт SharePoint.</span><span class="sxs-lookup"><span data-stu-id="e958e-104">If you need to collaborate with guests across documents, data, and lists, you can use a SharePoint site.</span></span> <span data-ttu-id="e958e-105">Современные сайты SharePoint подключены к группам Office 365, которые могут управлять членством в сайтах и предоставлять дополнительные инструменты для совместной работы, такие как общий почтовый ящик и календарь.</span><span class="sxs-lookup"><span data-stu-id="e958e-105">Modern SharePoint sites are connected to Office 365 Groups which can manage the site membership and provide additional collaboration tools such as a shared mailbox and calendar.</span></span>

<span data-ttu-id="e958e-106">В этой статье мы рассмотрим действия по настройке Microsoft 365, необходимые для настройки сайта SharePoint для совместной работы с гостями.</span><span class="sxs-lookup"><span data-stu-id="e958e-106">In this article, we'll walk through the Microsoft 365 configuration steps necessary to set up a SharePoint site for collaboration with guests.</span></span>

## <a name="azure-organizational-relationships-settings"></a><span data-ttu-id="e958e-107">Параметры связей в Организации Azure</span><span class="sxs-lookup"><span data-stu-id="e958e-107">Azure Organizational relationships settings</span></span>

<span data-ttu-id="e958e-108">Общий доступ в Microsoft 365 регулируется на самом высоком уровне параметрами организационных отношений в Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="e958e-108">Sharing in Microsoft 365 is governed at its highest level by the organizational relationships settings in Azure Active Directory.</span></span> <span data-ttu-id="e958e-109">Если общий доступ к гостям отключен или ограничен в Azure AD, все параметры общего доступа, настроенные в Microsoft 365, будут переопределены.</span><span class="sxs-lookup"><span data-stu-id="e958e-109">If guest sharing is disabled or restricted in Azure AD, this will override any sharing settings that you configure in Microsoft 365.</span></span>

<span data-ttu-id="e958e-110">Проверьте параметры организационных отношений, чтобы предотвратить блокировку общего доступа с гостями.</span><span class="sxs-lookup"><span data-stu-id="e958e-110">Check the organizational relationships settings to ensure that sharing with guests is not blocked.</span></span>

![Снимок экрана: страница параметров организационных отношений для Azure Active Directory](media/azure-ad-organizational-relationships-settings.png)

<span data-ttu-id="e958e-112">Настройка параметров организационных отношений</span><span class="sxs-lookup"><span data-stu-id="e958e-112">To set organizational relationship settings</span></span>

1. <span data-ttu-id="e958e-113">Выполните вход в Microsoft Azure по [https://portal.azure.com](https://portal.azure.com)адресу.</span><span class="sxs-lookup"><span data-stu-id="e958e-113">Log in to Microsoft Azure at [https://portal.azure.com](https://portal.azure.com).</span></span>
2. <span data-ttu-id="e958e-114">В области навигации слева выберите **Azure Active Directory**.</span><span class="sxs-lookup"><span data-stu-id="e958e-114">In the left navigation, click **Azure Active Directory**.</span></span>
3. <span data-ttu-id="e958e-115">В области **Обзор** щелкните **организационные связи**.</span><span class="sxs-lookup"><span data-stu-id="e958e-115">In the **Overview** pane, click **Organizational relationships**.</span></span>
4. <span data-ttu-id="e958e-116">В области **организационные связи** щелкните **Параметры**.</span><span class="sxs-lookup"><span data-stu-id="e958e-116">In the **Organizational relationships** pane, click **Settings**.</span></span>
5. <span data-ttu-id="e958e-117">Убедитесь, что у **администраторов и пользователей в роли гостя может быть приглашение** , а **Участники** — значение **Да**.</span><span class="sxs-lookup"><span data-stu-id="e958e-117">Ensure that **Admins and users in the guest inviter role can invite** and **Members can invite** are both set to **Yes**.</span></span>
6. <span data-ttu-id="e958e-118">Если вы внесли изменения, нажмите кнопку **сохранить**.</span><span class="sxs-lookup"><span data-stu-id="e958e-118">If you made changes, click **Save**.</span></span>

<span data-ttu-id="e958e-119">Обратите внимание на параметры в разделе **ограничения совместной работы** .</span><span class="sxs-lookup"><span data-stu-id="e958e-119">Note the settings in the **Collaboration restrictions** section.</span></span> <span data-ttu-id="e958e-120">Убедитесь, что домены гостей, с которыми вы хотите работать совместно, не заблокированы.</span><span class="sxs-lookup"><span data-stu-id="e958e-120">Make sure that the domains of the guests that you want to collaborate with aren't blocked.</span></span>

## <a name="office-365-groups-guest-settings"></a><span data-ttu-id="e958e-121">Параметры гостей для групп Office 365</span><span class="sxs-lookup"><span data-stu-id="e958e-121">Office 365 Groups guest settings</span></span>

<span data-ttu-id="e958e-122">Современные сайты SharePoint используют группы Office 365 для управления доступом к сайту.</span><span class="sxs-lookup"><span data-stu-id="e958e-122">Modern SharePoint sites use Office 365 Groups to control site access.</span></span> <span data-ttu-id="e958e-123">Для работы гостевых сайтов SharePoint необходимо включить параметры гостевых групп Office 365.</span><span class="sxs-lookup"><span data-stu-id="e958e-123">The Office 365 Groups guest settings must be turned on in order for guest access in SharePoint sites to work.</span></span>

![Снимок экрана: параметры гостя группы Office 365 в центре администрирования Microsoft 365](media/office-365-groups-guest-settings.png)

<span data-ttu-id="e958e-125">Настройка параметров гостя для групп Office 365</span><span class="sxs-lookup"><span data-stu-id="e958e-125">To set Office 365 Groups guest settings</span></span>

1. <span data-ttu-id="e958e-126">В центре администрирования Microsoft 365 в левой панели навигации разверните узел **Параметры**.</span><span class="sxs-lookup"><span data-stu-id="e958e-126">In the Microsoft 365 admin center, in the left navigation, expand **Settings**.</span></span>
2. <span data-ttu-id="e958e-127">Щелкните **службы & надстройки**.</span><span class="sxs-lookup"><span data-stu-id="e958e-127">Click **Services & add-ins**.</span></span>
3. <span data-ttu-id="e958e-128">В списке выберите пункт **группы Office 365**.</span><span class="sxs-lookup"><span data-stu-id="e958e-128">In the list, click **Office 365 Groups**.</span></span>
4. <span data-ttu-id="e958e-129">Убедитесь, что установлены флажки для членов группы, не входящих в **вашу организацию** , и **разрешите владельцам групп добавлять людей за пределом Организации в группы** .</span><span class="sxs-lookup"><span data-stu-id="e958e-129">Ensure that the **Let group members outside your organization access group content** and **Let group owners add people outside your organization to groups** check boxes are both checked.</span></span>
5. <span data-ttu-id="e958e-130">Если вы внесли изменения, нажмите кнопку **сохранить изменения**.</span><span class="sxs-lookup"><span data-stu-id="e958e-130">If you made changes, click **Save changes**.</span></span>


## <a name="sharepoint-organization-level-sharing-settings"></a><span data-ttu-id="e958e-131">Параметры общего доступа на уровне Организации SharePoint</span><span class="sxs-lookup"><span data-stu-id="e958e-131">SharePoint organization level sharing settings</span></span>

<span data-ttu-id="e958e-132">Чтобы гости могли иметь доступ к сайтам SharePoint, параметры общего доступа на уровне Организации SharePoint должны разрешить совместное использование с гостями.</span><span class="sxs-lookup"><span data-stu-id="e958e-132">In order for guests to have access to SharePoint sites, the SharePoint organization-level sharing settings must allow for sharing with guests.</span></span>

<span data-ttu-id="e958e-133">Параметры на уровне Организации определяют параметры, доступные для отдельных сайтов.</span><span class="sxs-lookup"><span data-stu-id="e958e-133">The organization-level settings determine what settings are available for individual sites.</span></span> <span data-ttu-id="e958e-134">Параметры сайта не могут быть более разрешительнои, чем параметры на уровне Организации.</span><span class="sxs-lookup"><span data-stu-id="e958e-134">Site settings cannot be more permissive than the organization-level settings.</span></span>

<span data-ttu-id="e958e-135">Если вы хотите разрешить общий доступ к файлам и папкам анонимных пользователей, выберите пункт **все**.</span><span class="sxs-lookup"><span data-stu-id="e958e-135">If you want to allow file and folder sharing with anonymous users, choose **Anyone**.</span></span> <span data-ttu-id="e958e-136">Если необходимо обеспечить проверку подлинности для всех гостей, выберите **новые и существующие гости**.</span><span class="sxs-lookup"><span data-stu-id="e958e-136">If you want to ensure that all guests have to authenticate, choose **New and existing guests**.</span></span> <span data-ttu-id="e958e-137">Выберите наиболее разрешительное значение, которое потребуется всем сайтам в вашей организации.</span><span class="sxs-lookup"><span data-stu-id="e958e-137">Choose the most permissive setting that will be needed by any site in your organization.</span></span>

![Снимок экрана: параметры общего доступа на уровне Организации SharePoint](media/sharepoint-organization-external-sharing-controls.png)


<span data-ttu-id="e958e-139">Настройка параметров общего доступа на уровне Организации SharePoint</span><span class="sxs-lookup"><span data-stu-id="e958e-139">To set SharePoint organization level sharing settings</span></span>

1. <span data-ttu-id="e958e-140">В центре администрирования Microsoft 365 в области навигации слева в разделе **центры администрирования**щелкните **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="e958e-140">In the Microsoft 365 admin center, in the left navigation, under **Admin centers**, click **SharePoint**.</span></span>
2. <span data-ttu-id="e958e-141">В центре администрирования SharePoint в области навигации слева щелкните **общий доступ**.</span><span class="sxs-lookup"><span data-stu-id="e958e-141">In the SharePoint admin center, in the left navigation, click **Sharing**.</span></span>
3. <span data-ttu-id="e958e-142">Убедитесь, что для внешнего общего доступа для SharePoint задано значение " **любой пользователь** " или " **новые и существующие гости**".</span><span class="sxs-lookup"><span data-stu-id="e958e-142">Ensure that external sharing for SharePoint is set to **Anyone** or **New and existing guests**.</span></span>
4. <span data-ttu-id="e958e-143">Если вы внесли изменения, нажмите кнопку **сохранить**.</span><span class="sxs-lookup"><span data-stu-id="e958e-143">If you made changes, click **Save**.</span></span>


## <a name="sharepoint-organization-level-default-link-settings"></a><span data-ttu-id="e958e-144">Параметры ссылок по умолчанию на уровне Организации SharePoint</span><span class="sxs-lookup"><span data-stu-id="e958e-144">SharePoint organization level default link settings</span></span>

<span data-ttu-id="e958e-145">Параметры ссылки по умолчанию для файлов и папок определяют, какой вариант ссылки отображается для пользователя по умолчанию при предоставлении общего доступа к файлу или папке.</span><span class="sxs-lookup"><span data-stu-id="e958e-145">The default file and folder link settings determine which link option is shown to the user by default when they share a file or folder.</span></span> <span data-ttu-id="e958e-146">При необходимости пользователи могут изменить тип ссылки на один из других вариантов, прежде чем предоставлять общий доступ.</span><span class="sxs-lookup"><span data-stu-id="e958e-146">Users can change the link type to one of the other options before sharing if desired.</span></span>

<span data-ttu-id="e958e-147">Помните, что этот параметр влияет на все команды и сайты SharePoint в Организации.</span><span class="sxs-lookup"><span data-stu-id="e958e-147">Keep in mind that this setting affects all teams and SharePoint sites in your organization.</span></span>

<span data-ttu-id="e958e-148">Выберите тип ссылки, выбранной по умолчанию, когда пользователи совместно используют файлы и папки:</span><span class="sxs-lookup"><span data-stu-id="e958e-148">Choose the type of link that's selected by default when users share files and folders:</span></span>

- <span data-ttu-id="e958e-149">Если вы ожидаете совместное использование большого числа файлов и папок анонимными пользователями, выберите этот параметр для **ссылки** .</span><span class="sxs-lookup"><span data-stu-id="e958e-149">**Anyone with the link** - Choose this option if you expect to share a lot of files and folders with anonymous users.</span></span> <span data-ttu-id="e958e-150">Если вы хотите разрешить ссылки для *всех пользователей* , но беспокоитесь о случайном анонимном доступе, примите во внимание один из других параметров, используемый по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="e958e-150">If you want to allow *Anyone* links but are concerned about accidental anonymous sharing, consider one of the other options as the default.</span></span> <span data-ttu-id="e958e-151">Этот тип ссылки доступен только в том случае, если вы включили **общий доступ** .</span><span class="sxs-lookup"><span data-stu-id="e958e-151">This link type is only available if you've enabled **Anyone** sharing.</span></span>
- <span data-ttu-id="e958e-152">**Только люди из вашей организации** — выберите этот вариант, если вы хотите, чтобы большая часть общего доступа к файлам и папкам была доступна пользователям в вашей организации.</span><span class="sxs-lookup"><span data-stu-id="e958e-152">**Only people in your organization** - Choose this option if you expect most file and folder sharing to be with people inside your organization.</span></span>
- <span data-ttu-id="e958e-153">\*\*\*\* Если вы собираетесь делать большой объем общего доступа к файлам и папкам для гостей, используйте этот вариант.</span><span class="sxs-lookup"><span data-stu-id="e958e-153">**Specific people** - Consider this option if you expect to do a lot of file and folder sharing with guests.</span></span> <span data-ttu-id="e958e-154">Этот тип ссылки работает с гостями и требует проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="e958e-154">This type of link works with guests and requires them to authenticate.</span></span>
 
![Снимок экрана: параметры общего доступа к файлам и папкам на уровне Организации SharePoint](media/sharepoint-organization-files-folders-sharing-settings.png)


<span data-ttu-id="e958e-156">Настройка параметров по умолчанию для ссылок на уровень организации SharePoint</span><span class="sxs-lookup"><span data-stu-id="e958e-156">To set the SharePoint organization level default link settings</span></span>

1. <span data-ttu-id="e958e-157">Перейдите на страницу "общий доступ" в центре администрирования SharePoint.</span><span class="sxs-lookup"><span data-stu-id="e958e-157">Navigate to the Sharing page in the SharePoint admin center.</span></span>
2. <span data-ttu-id="e958e-158">В разделе **ссылки на файлы и папки**выберите ссылку для совместного доступа по умолчанию, которую нужно использовать.</span><span class="sxs-lookup"><span data-stu-id="e958e-158">Under **File and folder links**, select the default sharing link that you want to use.</span></span>
3. <span data-ttu-id="e958e-159">Если вы внесли изменения, нажмите кнопку **сохранить**.</span><span class="sxs-lookup"><span data-stu-id="e958e-159">If you made changes, click **Save**.</span></span>

## <a name="create-a-site"></a><span data-ttu-id="e958e-160">Создание сайта</span><span class="sxs-lookup"><span data-stu-id="e958e-160">Create a site</span></span>

<span data-ttu-id="e958e-161">Следующий шаг — создание сайта, который планируется использовать для совместной работы с гостями.</span><span class="sxs-lookup"><span data-stu-id="e958e-161">The next step is to create the site that you plan to use for collaborating with guests.</span></span>

<span data-ttu-id="e958e-162">Создание сайта</span><span class="sxs-lookup"><span data-stu-id="e958e-162">To create a site</span></span>
1. <span data-ttu-id="e958e-163">В центре администрирования SharePoint в разделе **сайты**щелкните **активные сайты**.</span><span class="sxs-lookup"><span data-stu-id="e958e-163">In the SharePoint admin center, under **Sites**, click **Active sites**.</span></span>
2. <span data-ttu-id="e958e-164">Щелкните **Создать**.</span><span class="sxs-lookup"><span data-stu-id="e958e-164">Click **Create**.</span></span>
3. <span data-ttu-id="e958e-165">Щелкните **сайт группы**.</span><span class="sxs-lookup"><span data-stu-id="e958e-165">Click **Team site**.</span></span>
4. <span data-ttu-id="e958e-166">Введите имя сайта и введите имя владельца группы (владельца сайта).</span><span class="sxs-lookup"><span data-stu-id="e958e-166">Type a site name and enter a name for the Group owner (site owner).</span></span>
5. <span data-ttu-id="e958e-167">В разделе **Дополнительные параметры**выберите, если вы хотите, чтобы это был общедоступный или частный сайт.</span><span class="sxs-lookup"><span data-stu-id="e958e-167">Under **Advanced settings**, choose if you want this to be a public or private site.</span></span>
6. <span data-ttu-id="e958e-168">Нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="e958e-168">Click **Next**.</span></span>
7. <span data-ttu-id="e958e-169">Нажмите кнопку **Готово**.</span><span class="sxs-lookup"><span data-stu-id="e958e-169">Click **Finish**.</span></span>

<span data-ttu-id="e958e-170">Мы будем приглашать пользователей позже.</span><span class="sxs-lookup"><span data-stu-id="e958e-170">We'll invite users later.</span></span> <span data-ttu-id="e958e-171">После этого важно проверить параметры общего доступа на уровне сайта.</span><span class="sxs-lookup"><span data-stu-id="e958e-171">Next, it's important to check the site-level sharing settings for this site.</span></span>

## <a name="sharepoint-site-level-sharing-settings"></a><span data-ttu-id="e958e-172">Параметры общего доступа на уровне сайта SharePoint</span><span class="sxs-lookup"><span data-stu-id="e958e-172">SharePoint site level sharing settings</span></span>

<span data-ttu-id="e958e-173">Проверьте параметры общего доступа на уровне сайта, чтобы убедиться в том, что они допускают тип доступа, который вы хотите использовать для этого сайта.</span><span class="sxs-lookup"><span data-stu-id="e958e-173">Check the site-level sharing settings to make sure that they allow the type of access that you want for this site.</span></span> <span data-ttu-id="e958e-174">Например, если вы настроили параметры на уровне Организации для всех **пользователей**, но хотите, чтобы все гости прошли проверку подлинности для этого сайта, убедитесь, что для параметров общего доступа на уровне сайта задано значение " **новые и существующие гости**".</span><span class="sxs-lookup"><span data-stu-id="e958e-174">For example, if you set the organization-level settings to **Anyone**, but you want all guests to authenticate for this site, then make sure the site-level sharing settings are set to **New and existing guests**.</span></span>

<span data-ttu-id="e958e-175">Обратите внимание на то, что сайт не может быть\*\*\*\* предоставлен анонимным пользователям, но можно использовать отдельные файлы и папки.</span><span class="sxs-lookup"><span data-stu-id="e958e-175">Note that the site cannot be shared with anonymous users (**Anyone** setting), but individual files and folders can.</span></span>

![Снимок экрана: параметры внешнего общего доступа к сайту SharePoint](media/sharepoint-site-external-sharing-settings.png)

<span data-ttu-id="e958e-177">Установка параметров общего доступа на уровне сайта</span><span class="sxs-lookup"><span data-stu-id="e958e-177">To set site-level sharing settings</span></span>
1. <span data-ttu-id="e958e-178">В центре администрирования SharePoint в области навигации слева разверните узел **сайты** и выберите пункт **активные сайты**.</span><span class="sxs-lookup"><span data-stu-id="e958e-178">In the SharePoint admin center, in the left navigation, expand **Sites** and click **Active sites**.</span></span>
2. <span data-ttu-id="e958e-179">Выберите сайт, который вы только что создали.</span><span class="sxs-lookup"><span data-stu-id="e958e-179">Select the site that you just created.</span></span>
3. <span data-ttu-id="e958e-180">На ленте щелкните **общий доступ**.</span><span class="sxs-lookup"><span data-stu-id="e958e-180">In the ribbon, click **Sharing**.</span></span>
4. <span data-ttu-id="e958e-181">Убедитесь, что для общего доступа задано значение " **любой пользователь** " или " **новые и существующие гости**".</span><span class="sxs-lookup"><span data-stu-id="e958e-181">Ensure that sharing is set to **Anyone** or **New and existing guests**.</span></span>
5. <span data-ttu-id="e958e-182">Если вы внесли изменения, нажмите кнопку **сохранить**.</span><span class="sxs-lookup"><span data-stu-id="e958e-182">If you made changes, click **Save**.</span></span>

## <a name="invite-users"></a><span data-ttu-id="e958e-183">Приглашение пользователей</span><span class="sxs-lookup"><span data-stu-id="e958e-183">Invite users</span></span>

<span data-ttu-id="e958e-184">Параметры общего доступа к гостевой сети настроены, поэтому вы можете добавить внутренних пользователей и гостей на сайт.</span><span class="sxs-lookup"><span data-stu-id="e958e-184">Guest sharing settings are now configured, so you can start adding internal users and guests to your site.</span></span> <span data-ttu-id="e958e-185">Доступ к сайту контролируется с помощью связанной группы Office 365, поэтому мы будем добавлять пользователей.</span><span class="sxs-lookup"><span data-stu-id="e958e-185">Site access is controlled through the associated Office 365 Group, so we'll be adding users there.</span></span>

<span data-ttu-id="e958e-186">Приглашение внутренних пользователей в группу</span><span class="sxs-lookup"><span data-stu-id="e958e-186">To invite internal users to a group</span></span>
1. <span data-ttu-id="e958e-187">Перейдите на сайт, где вы хотите добавить пользователей.</span><span class="sxs-lookup"><span data-stu-id="e958e-187">Navigate to the site where you want to add users.</span></span>
2. <span data-ttu-id="e958e-188">Щелкните **элементы** в правом верхнем углу.</span><span class="sxs-lookup"><span data-stu-id="e958e-188">Click **Members** in the upper right.</span></span>
3. <span data-ttu-id="e958e-189">Нажмите **Добавить участников**.</span><span class="sxs-lookup"><span data-stu-id="e958e-189">Click **Add members**.</span></span>
4. <span data-ttu-id="e958e-190">Введите имена или адреса электронной почты пользователей, которых вы хотите пригласить на сайт, а затем нажмите кнопку **сохранить**.</span><span class="sxs-lookup"><span data-stu-id="e958e-190">Type the names or email addresses of the users that you want to invite to the site, and then click **Save**.</span></span>

<span data-ttu-id="e958e-191">Гостевые пользователи не могут добавляться с сайта.</span><span class="sxs-lookup"><span data-stu-id="e958e-191">Guest users can't be added from the site.</span></span> <span data-ttu-id="e958e-192">Их необходимо добавить с помощью Outlook в Интернете.</span><span class="sxs-lookup"><span data-stu-id="e958e-192">You need to add them using Outlook on the web.</span></span>

<span data-ttu-id="e958e-193">Приглашение гостей на сайт</span><span class="sxs-lookup"><span data-stu-id="e958e-193">To invite guests to a site</span></span>
1. <span data-ttu-id="e958e-194">В Outlook в Интернете в разделе **группы**выберите группу, в которую вы хотите добавить участников.</span><span class="sxs-lookup"><span data-stu-id="e958e-194">In Outlook on the web, under **Groups**, click the group where you want to add members.</span></span>
2. <span data-ttu-id="e958e-195">Откройте карточку контакта группы, а затем в разделе **Дополнительные параметры** (...) нажмите кнопку **Добавить участников**.</span><span class="sxs-lookup"><span data-stu-id="e958e-195">Open the group contact card, and then, under **More options** (...), click **Add members**.</span></span>
3. <span data-ttu-id="e958e-196">Введите адреса электронной почты гостей, которых вы хотите пригласить, и нажмите кнопку **Добавить**.</span><span class="sxs-lookup"><span data-stu-id="e958e-196">Type the email addresses of the guests that you want to invite, and then click **Add**.</span></span>
4. <span data-ttu-id="e958e-197">Нажмите кнопку **Закрыть**.</span><span class="sxs-lookup"><span data-stu-id="e958e-197">Click **Close**.</span></span>

## <a name="see-also"></a><span data-ttu-id="e958e-198">См. также</span><span class="sxs-lookup"><span data-stu-id="e958e-198">See Also</span></span>
