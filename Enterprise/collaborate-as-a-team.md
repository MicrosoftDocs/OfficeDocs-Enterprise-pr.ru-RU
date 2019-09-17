---
title: Совместная работа с гостями в команде
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: sharepoint-online
localization_priority: Normal
description: Узнайте, как совместно работать с гостями в Teams.
ms.openlocfilehash: 9a169e33a9cbd8f079966443bd3d830aa79f4971
ms.sourcegitcommit: 3bba97053caf5f9cff0ef3205afb7869535f38bd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/16/2019
ms.locfileid: "36992418"
---
# <a name="collaborate-with-guests-in-a-team"></a><span data-ttu-id="5a4d5-103">Совместная работа с гостями в команде</span><span class="sxs-lookup"><span data-stu-id="5a4d5-103">Collaborate with guests in a team</span></span>

<span data-ttu-id="5a4d5-104">Если вам требуется совместно работать с гостями в документах, задачах и беседах, рекомендуется использовать Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="5a4d5-104">If you need to collaborate with guests across documents, tasks, and conversations, we recommend using Microsoft Teams.</span></span> <span data-ttu-id="5a4d5-105">Teams предоставляет все функции совместной работы, доступные в Office и SharePoint с сохраняемым чат и настраиваемым и расширяемым набором средств совместной работы в едином пользовательском интерфейсе.</span><span class="sxs-lookup"><span data-stu-id="5a4d5-105">Teams provides all of the collaboration features available in Office and SharePoint with persistent chat and a customizable and extensible set of collaboration tools in a unified user experience.</span></span>

<span data-ttu-id="5a4d5-106">В этой статье мы рассмотрим действия по настройке Microsoft 365, необходимые для настройки группы для совместной работы с гостями.</span><span class="sxs-lookup"><span data-stu-id="5a4d5-106">In this article, we'll walk through the Microsoft 365 configuration steps necessary to set up a team for collaboration with guests.</span></span>

## <a name="azure-organizational-relationships-settings"></a><span data-ttu-id="5a4d5-107">Параметры связей в Организации Azure</span><span class="sxs-lookup"><span data-stu-id="5a4d5-107">Azure Organizational relationships settings</span></span>

<span data-ttu-id="5a4d5-108">Общий доступ в Microsoft 365 регулируется на самом высоком уровне параметрами организационных отношений в Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="5a4d5-108">Sharing in Microsoft 365 is governed at its highest level by the organizational relationships settings in Azure Active Directory.</span></span> <span data-ttu-id="5a4d5-109">Если общий доступ к гостям отключен или ограничен в Azure AD, все параметры общего доступа, настроенные в Microsoft 365, будут переопределены.</span><span class="sxs-lookup"><span data-stu-id="5a4d5-109">If guest sharing is disabled or restricted in Azure AD, this will override any sharing settings that you configure in Microsoft 365.</span></span>

<span data-ttu-id="5a4d5-110">Проверьте параметры организационных отношений, чтобы предотвратить блокировку общего доступа с гостями.</span><span class="sxs-lookup"><span data-stu-id="5a4d5-110">Check the organizational relationships settings to ensure that sharing with guests is not blocked.</span></span>

![Снимок экрана: страница параметров организационных отношений для Azure Active Directory](media/azure-ad-organizational-relationships-settings.png)

<span data-ttu-id="5a4d5-112">Настройка параметров организационных отношений</span><span class="sxs-lookup"><span data-stu-id="5a4d5-112">To set organizational relationship settings</span></span>

1. <span data-ttu-id="5a4d5-113">Выполните вход в Microsoft Azure по [https://portal.azure.com](https://portal.azure.com)адресу.</span><span class="sxs-lookup"><span data-stu-id="5a4d5-113">Log in to Microsoft Azure at [https://portal.azure.com](https://portal.azure.com).</span></span>
2. <span data-ttu-id="5a4d5-114">В области навигации слева выберите **Azure Active Directory**.</span><span class="sxs-lookup"><span data-stu-id="5a4d5-114">In the left navigation, click **Azure Active Directory**.</span></span>
3. <span data-ttu-id="5a4d5-115">В области **Обзор** щелкните **организационные связи**.</span><span class="sxs-lookup"><span data-stu-id="5a4d5-115">In the **Overview** pane, click **Organizational relationships**.</span></span>
4. <span data-ttu-id="5a4d5-116">В области **организационные связи** щелкните **Параметры**.</span><span class="sxs-lookup"><span data-stu-id="5a4d5-116">In the **Organizational relationships** pane, click **Settings**.</span></span>
5. <span data-ttu-id="5a4d5-117">Убедитесь, что у **администраторов и пользователей в роли гостя может быть приглашение** , а **Участники** — значение **Да**.</span><span class="sxs-lookup"><span data-stu-id="5a4d5-117">Ensure that **Admins and users in the guest inviter role can invite** and **Members can invite** are both set to **Yes**.</span></span>
6. <span data-ttu-id="5a4d5-118">Если вы внесли изменения, нажмите кнопку **сохранить**.</span><span class="sxs-lookup"><span data-stu-id="5a4d5-118">If you made changes, click **Save**.</span></span>

<span data-ttu-id="5a4d5-119">Обратите внимание на параметры в разделе **ограничения совместной работы** .</span><span class="sxs-lookup"><span data-stu-id="5a4d5-119">Note the settings in the **Collaboration restrictions** section.</span></span> <span data-ttu-id="5a4d5-120">Убедитесь, что домены гостей, с которыми вы хотите работать совместно, не заблокированы.</span><span class="sxs-lookup"><span data-stu-id="5a4d5-120">Make sure that the domains of the guests that you want to collaborate with aren't blocked.</span></span>

## <a name="teams-guest-access-settings"></a><span data-ttu-id="5a4d5-121">Параметры гостевого доступа Teams</span><span class="sxs-lookup"><span data-stu-id="5a4d5-121">Teams guest access settings</span></span>

<span data-ttu-id="5a4d5-122">У Teams есть главный переключатель включения/выключения для гостевого доступа, а также различные параметры, позволяющие контролировать, какие гости могут выполнять в команде.</span><span class="sxs-lookup"><span data-stu-id="5a4d5-122">Teams has a master on/off switch for guest access and a variety of settings available to control what guests can do in a team.</span></span> <span data-ttu-id="5a4d5-123">Главный коммутатор, **разрешающий гостевой доступ в Teams** , должен быть **включен** для работы в Teams.</span><span class="sxs-lookup"><span data-stu-id="5a4d5-123">The master switch, **Allow guest access in Teams** must be **On** for guest access to work in Teams.</span></span>

<span data-ttu-id="5a4d5-124">Убедитесь, что гостевой доступ включен в Teams, и внесите любую корректировку параметров гостя в соответствии с бизнес-потребностями.</span><span class="sxs-lookup"><span data-stu-id="5a4d5-124">Check to ensure that guest access is enabled in Teams and make any adjustment to the guest settings based on your business needs.</span></span> <span data-ttu-id="5a4d5-125">Помните, что эти параметры влияют на все команды.</span><span class="sxs-lookup"><span data-stu-id="5a4d5-125">Keep in mind that these settings affect all teams.</span></span>

![Снимок экрана: переключатель гостевого доступа в Teams](media/teams-guest-access-toggle-on.png)

<span data-ttu-id="5a4d5-127">Настройка параметров гостевого доступа для Teams</span><span class="sxs-lookup"><span data-stu-id="5a4d5-127">To set Teams guest access settings</span></span>

1. <span data-ttu-id="5a4d5-128">Войдите в центр администрирования Microsoft 365 по адресу [https://admin.microsoft.com](https://admin.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="5a4d5-128">Log in to the Microsoft 365 admin center at [https://admin.microsoft.com](https://admin.microsoft.com).</span></span>
2. <span data-ttu-id="5a4d5-129">В области навигации слева щелкните **Показать все**.</span><span class="sxs-lookup"><span data-stu-id="5a4d5-129">In the left navigation, click **Show all**.</span></span>
3. <span data-ttu-id="5a4d5-130">В разделе **центры администрирования**щелкните **Teams**.</span><span class="sxs-lookup"><span data-stu-id="5a4d5-130">Under **Admin centers**, click **Teams**.</span></span>
4. <span data-ttu-id="5a4d5-131">В центре администрирования Teams в области навигации слева разверните раздел **Параметры на уровне Организации** и выберите **гостевой доступ**.</span><span class="sxs-lookup"><span data-stu-id="5a4d5-131">In the Teams admin center, in the left navigation, expand **Org-wide settings** and click **Guest access**.</span></span>
5. <span data-ttu-id="5a4d5-132">Убедитесь, что для параметра **Разрешить гостевой доступ в Teams** задано значение **включено**.</span><span class="sxs-lookup"><span data-stu-id="5a4d5-132">Ensure that **Allow guest access in Teams** is set to **On**.</span></span>
6. <span data-ttu-id="5a4d5-133">Внесите необходимые изменения в дополнительные параметры гостей, а затем нажмите кнопку **сохранить**.</span><span class="sxs-lookup"><span data-stu-id="5a4d5-133">Make any desired changes to the additional guest settings, and then click **Save**.</span></span>

> [!NOTE]
> <span data-ttu-id="5a4d5-134">После включения гостевой настройки Teams может потребоваться до двадцати четырех часов.</span><span class="sxs-lookup"><span data-stu-id="5a4d5-134">It may take up to twenty-four hours for the Teams guest setting to become active after you turn it on.</span></span>

## <a name="office-365-groups-guest-settings"></a><span data-ttu-id="5a4d5-135">Параметры гостей для групп Office 365</span><span class="sxs-lookup"><span data-stu-id="5a4d5-135">Office 365 Groups guest settings</span></span>

<span data-ttu-id="5a4d5-136">Teams использует группы Office 365 для членства в группах.</span><span class="sxs-lookup"><span data-stu-id="5a4d5-136">Teams uses Office 365 Groups for team membership.</span></span> <span data-ttu-id="5a4d5-137">Для работы гостевых Teams в Teams необходимо включить параметры гостевых групп Office 365.</span><span class="sxs-lookup"><span data-stu-id="5a4d5-137">The Office 365 Groups guest settings must be turned on in order for guest access in Teams to work.</span></span>

![Снимок экрана: параметры гостя группы Office 365 в центре администрирования Microsoft 365](media/office-365-groups-guest-settings.png)

<span data-ttu-id="5a4d5-139">Настройка параметров гостя для групп Office 365</span><span class="sxs-lookup"><span data-stu-id="5a4d5-139">To set Office 365 Groups guest settings</span></span>

1. <span data-ttu-id="5a4d5-140">В центре администрирования Microsoft 365 в левой панели навигации разверните узел **Параметры**.</span><span class="sxs-lookup"><span data-stu-id="5a4d5-140">In the Microsoft 365 admin center, in the left navigation, expand **Settings**.</span></span>
2. <span data-ttu-id="5a4d5-141">Щелкните **службы & надстройки**.</span><span class="sxs-lookup"><span data-stu-id="5a4d5-141">Click **Services & add-ins**.</span></span>
3. <span data-ttu-id="5a4d5-142">В списке выберите пункт **группы Office 365**.</span><span class="sxs-lookup"><span data-stu-id="5a4d5-142">In the list, click **Office 365 Groups**.</span></span>
4. <span data-ttu-id="5a4d5-143">Убедитесь, что установлены флажки для членов группы, не входящих в **вашу организацию** , и **разрешите владельцам групп добавлять людей за пределом Организации в группы** .</span><span class="sxs-lookup"><span data-stu-id="5a4d5-143">Ensure that the **Let group members outside your organization access group content** and **Let group owners add people outside your organization to groups** check boxes are both checked.</span></span>
5. <span data-ttu-id="5a4d5-144">Если вы внесли изменения, нажмите кнопку **сохранить изменения**.</span><span class="sxs-lookup"><span data-stu-id="5a4d5-144">If you made changes, click **Save changes**.</span></span>


## <a name="sharepoint-organization-level-sharing-settings"></a><span data-ttu-id="5a4d5-145">Параметры общего доступа на уровне Организации SharePoint</span><span class="sxs-lookup"><span data-stu-id="5a4d5-145">SharePoint organization level sharing settings</span></span>

<span data-ttu-id="5a4d5-146">Чтобы гости могли иметь доступ к файлам в Teams, параметры общего доступа на уровне Организации SharePoint должны разрешить совместное использование с гостями.</span><span class="sxs-lookup"><span data-stu-id="5a4d5-146">In order for guests to have access to files in Teams, the SharePoint organization-level sharing settings must allow for sharing with guests.</span></span>

<span data-ttu-id="5a4d5-147">Параметры на уровне Организации определяют, какие параметры доступны для отдельных сайтов, включая сайты, связанные с Teams.</span><span class="sxs-lookup"><span data-stu-id="5a4d5-147">The organization-level settings determine what settings are available for individual sites, including sites associated with teams.</span></span> <span data-ttu-id="5a4d5-148">Параметры сайта не могут быть более разрешительнои, чем параметры на уровне Организации.</span><span class="sxs-lookup"><span data-stu-id="5a4d5-148">Site settings cannot be more permissive than the organization-level settings.</span></span>

<span data-ttu-id="5a4d5-149">Если вы хотите разрешить общий доступ к файлам и папкам анонимных пользователей, выберите пункт **все**.</span><span class="sxs-lookup"><span data-stu-id="5a4d5-149">If you want to allow file and folder sharing with anonymous users, choose **Anyone**.</span></span> <span data-ttu-id="5a4d5-150">Если необходимо обеспечить проверку подлинности для всех гостей, выберите **новые и существующие гости**.</span><span class="sxs-lookup"><span data-stu-id="5a4d5-150">If you want to ensure that all guests have to authenticate, choose **New and existing guests**.</span></span> <span data-ttu-id="5a4d5-151">Выберите наиболее разрешительное значение, которое потребуется всем сайтам в вашей организации.</span><span class="sxs-lookup"><span data-stu-id="5a4d5-151">Choose the most permissive setting that will be needed by any site in your organization.</span></span>

![Снимок экрана: параметры общего доступа на уровне Организации SharePoint](media/sharepoint-organization-external-sharing-controls.png)


<span data-ttu-id="5a4d5-153">Настройка параметров общего доступа на уровне Организации SharePoint</span><span class="sxs-lookup"><span data-stu-id="5a4d5-153">To set SharePoint organization level sharing settings</span></span>

1. <span data-ttu-id="5a4d5-154">В центре администрирования Microsoft 365 в области навигации слева в разделе **центры администрирования**щелкните **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="5a4d5-154">In the Microsoft 365 admin center, in the left navigation, under **Admin centers**, click **SharePoint**.</span></span>
2. <span data-ttu-id="5a4d5-155">В центре администрирования SharePoint в области навигации слева щелкните **общий доступ**.</span><span class="sxs-lookup"><span data-stu-id="5a4d5-155">In the SharePoint admin center, in the left navigation, click **Sharing**.</span></span>
3. <span data-ttu-id="5a4d5-156">Убедитесь, что для внешнего общего доступа для SharePoint задано значение " **любой пользователь** " или " **новые и существующие гости**".</span><span class="sxs-lookup"><span data-stu-id="5a4d5-156">Ensure that external sharing for SharePoint is set to **Anyone** or **New and existing guests**.</span></span>
4. <span data-ttu-id="5a4d5-157">Если вы внесли изменения, нажмите кнопку **сохранить**.</span><span class="sxs-lookup"><span data-stu-id="5a4d5-157">If you made changes, click **Save**.</span></span>


## <a name="sharepoint-organization-level-default-link-settings"></a><span data-ttu-id="5a4d5-158">Параметры ссылок по умолчанию на уровне Организации SharePoint</span><span class="sxs-lookup"><span data-stu-id="5a4d5-158">SharePoint organization level default link settings</span></span>

<span data-ttu-id="5a4d5-159">Параметры ссылки по умолчанию для файлов и папок определяют, какой вариант ссылки отображается для пользователя по умолчанию при предоставлении общего доступа к файлу или папке.</span><span class="sxs-lookup"><span data-stu-id="5a4d5-159">The default file and folder link settings determine which link option is shown to the user by default when they share a file or folder.</span></span> <span data-ttu-id="5a4d5-160">При необходимости пользователи могут изменить тип ссылки на один из других вариантов, прежде чем предоставлять общий доступ.</span><span class="sxs-lookup"><span data-stu-id="5a4d5-160">Users can change the link type to one of the other options before sharing if desired.</span></span>

<span data-ttu-id="5a4d5-161">Помните, что этот параметр влияет на все команды и сайты SharePoint в Организации.</span><span class="sxs-lookup"><span data-stu-id="5a4d5-161">Keep in mind that this setting affects all teams and SharePoint sites in your organization.</span></span>

<span data-ttu-id="5a4d5-162">Выберите тип ссылки, выбранной по умолчанию, когда пользователи совместно используют файлы и папки:</span><span class="sxs-lookup"><span data-stu-id="5a4d5-162">Choose the type of link that's selected by default when users share files and folders:</span></span>

- <span data-ttu-id="5a4d5-163">Если вы ожидаете совместное использование большого числа файлов и папок анонимными пользователями, выберите этот параметр для **ссылки** .</span><span class="sxs-lookup"><span data-stu-id="5a4d5-163">**Anyone with the link** - Choose this option if you expect to share a lot of files and folders with anonymous users.</span></span> <span data-ttu-id="5a4d5-164">Если вы хотите разрешить ссылки для *всех пользователей* , но беспокоитесь о случайном анонимном доступе, примите во внимание один из других параметров, используемый по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="5a4d5-164">If you want to allow *Anyone* links but are concerned about accidental anonymous sharing, consider one of the other options as the default.</span></span> <span data-ttu-id="5a4d5-165">Этот тип ссылки доступен только в том случае, если вы включили **общий доступ** .</span><span class="sxs-lookup"><span data-stu-id="5a4d5-165">This link type is only available if you've enabled **Anyone** sharing.</span></span>
- <span data-ttu-id="5a4d5-166">**Только люди из вашей организации** — выберите этот вариант, если вы хотите, чтобы большая часть общего доступа к файлам и папкам была доступна пользователям в вашей организации.</span><span class="sxs-lookup"><span data-stu-id="5a4d5-166">**Only people in your organization** - Choose this option if you expect most file and folder sharing to be with people inside your organization.</span></span>
- <span data-ttu-id="5a4d5-167">\*\*\*\* Если вы собираетесь делать большой объем общего доступа к файлам и папкам для гостей, используйте этот вариант.</span><span class="sxs-lookup"><span data-stu-id="5a4d5-167">**Specific people** - Consider this option if you expect to do a lot of file and folder sharing with guests.</span></span> <span data-ttu-id="5a4d5-168">Этот тип ссылки работает с гостями и требует проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="5a4d5-168">This type of link works with guests and requires them to authenticate.</span></span>
 
![Снимок экрана: параметры общего доступа к файлам и папкам на уровне Организации SharePoint](media/sharepoint-organization-files-folders-sharing-settings.png)


<span data-ttu-id="5a4d5-170">Настройка параметров по умолчанию для ссылок на уровень организации SharePoint</span><span class="sxs-lookup"><span data-stu-id="5a4d5-170">To set the SharePoint organization level default link settings</span></span>

1. <span data-ttu-id="5a4d5-171">Перейдите на страницу "общий доступ" в центре администрирования SharePoint.</span><span class="sxs-lookup"><span data-stu-id="5a4d5-171">Navigate to the Sharing page in the SharePoint admin center.</span></span>
2. <span data-ttu-id="5a4d5-172">В разделе **ссылки на файлы и папки**выберите ссылку для совместного доступа по умолчанию, которую нужно использовать.</span><span class="sxs-lookup"><span data-stu-id="5a4d5-172">Under **File and folder links**, select the default sharing link that you want to use.</span></span>
3. <span data-ttu-id="5a4d5-173">Если вы внесли изменения, нажмите кнопку **сохранить**.</span><span class="sxs-lookup"><span data-stu-id="5a4d5-173">If you made changes, click **Save**.</span></span>

## <a name="create-a-team"></a><span data-ttu-id="5a4d5-174">Создание команды</span><span class="sxs-lookup"><span data-stu-id="5a4d5-174">Create a team</span></span>

<span data-ttu-id="5a4d5-175">Следующий шаг — создание команды, которую планируется использовать для совместной работы с гостями.</span><span class="sxs-lookup"><span data-stu-id="5a4d5-175">The next step is to create the team that you plan to use for collaborating with guests.</span></span>

<span data-ttu-id="5a4d5-176">Создание команды</span><span class="sxs-lookup"><span data-stu-id="5a4d5-176">To create a team</span></span>
1. <span data-ttu-id="5a4d5-177">В Teams на вкладке **группы** выберите команду **присоединиться или создайте** команду в нижней части левой области.</span><span class="sxs-lookup"><span data-stu-id="5a4d5-177">In Teams, on the **Teams** tab, click **Join or create a team** at the bottom of the left pane.</span></span>
2. <span data-ttu-id="5a4d5-178">Нажмите **создать группу**.</span><span class="sxs-lookup"><span data-stu-id="5a4d5-178">Click **Create a team**.</span></span>
3. <span data-ttu-id="5a4d5-179">Нажмите **"создать группу"**.</span><span class="sxs-lookup"><span data-stu-id="5a4d5-179">Click **Build a team from scratch**.</span></span>
4. <span data-ttu-id="5a4d5-180">Выберите **частный** или **общедоступный**.</span><span class="sxs-lookup"><span data-stu-id="5a4d5-180">Choose **Private** or **Public**.</span></span>
5. <span data-ttu-id="5a4d5-181">Введите имя и описание команды, а затем нажмите кнопку **создать**.</span><span class="sxs-lookup"><span data-stu-id="5a4d5-181">Type a name and description for the team, and then click **Create**.</span></span>
6. <span data-ttu-id="5a4d5-182">Нажмите кнопку **пропустить**.</span><span class="sxs-lookup"><span data-stu-id="5a4d5-182">Click **Skip**.</span></span>

<span data-ttu-id="5a4d5-183">Мы будем приглашать пользователей позже.</span><span class="sxs-lookup"><span data-stu-id="5a4d5-183">We'll invite users later.</span></span> <span data-ttu-id="5a4d5-184">Затем важно проверить параметры общего доступа на уровне сайта для сайта SharePoint, связанного с командой.</span><span class="sxs-lookup"><span data-stu-id="5a4d5-184">Next, it's important to check the site-level sharing settings for the SharePoint site that is associated with the team.</span></span>

## <a name="sharepoint-site-level-sharing-settings"></a><span data-ttu-id="5a4d5-185">Параметры общего доступа на уровне сайта SharePoint</span><span class="sxs-lookup"><span data-stu-id="5a4d5-185">SharePoint site level sharing settings</span></span>

<span data-ttu-id="5a4d5-186">Проверьте параметры общего доступа на уровне сайта, чтобы убедиться, что они допускают тип доступа, который вы хотите использовать для этой команды.</span><span class="sxs-lookup"><span data-stu-id="5a4d5-186">Check the site-level sharing settings to make sure that they allow the type of access that you want for this team.</span></span> <span data-ttu-id="5a4d5-187">Например, если вы настроили параметры на уровне Организации для всех **пользователей**, но хотите, чтобы все гости подлинны для этой команды, убедитесь, что для параметров общего доступа на уровне сайта задано значение " **новые и существующие гости**".</span><span class="sxs-lookup"><span data-stu-id="5a4d5-187">For example, if you set the organization-level settings to **Anyone**, but you want all guests to authenticate for this team, then make sure the site-level sharing settings are set to **New and existing guests**.</span></span>

![Снимок экрана: параметры внешнего общего доступа к сайту SharePoint](media/sharepoint-site-external-sharing-settings.png)


<span data-ttu-id="5a4d5-189">Установка параметров общего доступа на уровне сайта</span><span class="sxs-lookup"><span data-stu-id="5a4d5-189">To set site-level sharing settings</span></span>
1. <span data-ttu-id="5a4d5-190">В центре администрирования SharePoint в области навигации слева разверните узел **сайты** и выберите пункт **активные сайты**.</span><span class="sxs-lookup"><span data-stu-id="5a4d5-190">In the SharePoint admin center, in the left navigation, expand **Sites** and click **Active sites**.</span></span>
2. <span data-ttu-id="5a4d5-191">Выберите сайт только что созданной команды.</span><span class="sxs-lookup"><span data-stu-id="5a4d5-191">Select the site for the team that you just created.</span></span>
3. <span data-ttu-id="5a4d5-192">На ленте щелкните **общий доступ**.</span><span class="sxs-lookup"><span data-stu-id="5a4d5-192">In the ribbon, click **Sharing**.</span></span>
4. <span data-ttu-id="5a4d5-193">Убедитесь, что для общего доступа задано значение " **любой пользователь** " или " **новые и существующие гости**".</span><span class="sxs-lookup"><span data-stu-id="5a4d5-193">Ensure that sharing is set to **Anyone** or **New and existing guests**.</span></span>
5. <span data-ttu-id="5a4d5-194">Если вы внесли изменения, нажмите кнопку **сохранить**.</span><span class="sxs-lookup"><span data-stu-id="5a4d5-194">If you made changes, click **Save**.</span></span>

## <a name="invite-users"></a><span data-ttu-id="5a4d5-195">Приглашение пользователей</span><span class="sxs-lookup"><span data-stu-id="5a4d5-195">Invite users</span></span>

<span data-ttu-id="5a4d5-196">Параметры общего доступа к гостевой сети настроены, поэтому вы можете добавить в команду внутренних пользователей и гостей.</span><span class="sxs-lookup"><span data-stu-id="5a4d5-196">Guest sharing settings are now configured, so you can start adding internal users and guests to your team.</span></span> 

<span data-ttu-id="5a4d5-197">Приглашение внутренних пользователей в команду</span><span class="sxs-lookup"><span data-stu-id="5a4d5-197">To invite internal users to a team</span></span>
1. <span data-ttu-id="5a4d5-198">В группе выберите **Дополнительные параметры** (**\*\***), а затем нажмите кнопку **Добавить участника**.</span><span class="sxs-lookup"><span data-stu-id="5a4d5-198">In the team, click **More options** (**\*\*\***), and then click **Add member**.</span></span>
2. <span data-ttu-id="5a4d5-199">Введите имя человека, которого хотите пригласить.</span><span class="sxs-lookup"><span data-stu-id="5a4d5-199">Type the name of the person who you want to invite.</span></span>
3. <span data-ttu-id="5a4d5-200">Нажмите **Добавить**, а затем **Закрыть**.</span><span class="sxs-lookup"><span data-stu-id="5a4d5-200">Click **Add**, and then click **Close**.</span></span>

<span data-ttu-id="5a4d5-201">Приглашение гостей в команду</span><span class="sxs-lookup"><span data-stu-id="5a4d5-201">To invite guests to a team</span></span>
1. <span data-ttu-id="5a4d5-202">В группе выберите **Дополнительные параметры** (**\*\***), а затем нажмите кнопку **Добавить участника**.</span><span class="sxs-lookup"><span data-stu-id="5a4d5-202">In the team, click **More options** (**\*\*\***), and then click **Add member**.</span></span>
2. <span data-ttu-id="5a4d5-203">Введите адрес электронной почты гостя, которого вы хотите пригласить.</span><span class="sxs-lookup"><span data-stu-id="5a4d5-203">Type the email address of the guest who you want to invite.</span></span>
3. <span data-ttu-id="5a4d5-204">Щелкните ссылку **изменить сведения о гостевой**системе.</span><span class="sxs-lookup"><span data-stu-id="5a4d5-204">Click **Edit guest information**.</span></span>
4. <span data-ttu-id="5a4d5-205">Введите полное имя гостя и щелкните галочку.</span><span class="sxs-lookup"><span data-stu-id="5a4d5-205">Type the guest's full name and click the check mark.</span></span>
5. <span data-ttu-id="5a4d5-206">Нажмите **Добавить**, а затем **Закрыть**.</span><span class="sxs-lookup"><span data-stu-id="5a4d5-206">Click **Add**, and then click **Close**.</span></span>

## <a name="see-also"></a><span data-ttu-id="5a4d5-207">См. также</span><span class="sxs-lookup"><span data-stu-id="5a4d5-207">See Also</span></span>

