---
title: "Разработка изолированного сайта группы SharePoint Online"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Top
ms.custom:
- DecEntMigration
- Ent_Solutions
ms.assetid: 775a4e9e-3135-4a48-b32f-bbdd9f2bd0aa
description: "Сводка: Шаг через процесс разработки изолированного SharePoint Online веб-сайтов групп."
ms.openlocfilehash: 343872ef7a41b40a87454da27ddccc4530ffe2eb
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2017
---
# <a name="design-an-isolated-sharepoint-online-team-site"></a><span data-ttu-id="37b56-103">Разработка изолированного сайта группы SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="37b56-103">Design an isolated SharePoint Online team site</span></span>

 <span data-ttu-id="37b56-104">**Сводка:** Описывается пошаговый процесс разработки изолированного SharePoint Online веб-сайтов групп.</span><span class="sxs-lookup"><span data-stu-id="37b56-104">**Summary:** Step through the design process for isolated SharePoint Online team sites.</span></span>
  
<span data-ttu-id="37b56-105">В этой статье описаны основные проектные решения, которые необходимо принять перед созданием изолированного сайта группы SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="37b56-105">This article takes you through the key design decisions you must make before creating an isolated SharePoint Online team site.</span></span>
  
## <a name="phase-1-determine-your-sharepoint-groups-and-permission-levels"></a><span data-ttu-id="37b56-106">Этап 1. Определение групп SharePoint и уровней разрешений</span><span class="sxs-lookup"><span data-stu-id="37b56-106">Phase 1: Determine your SharePoint groups and permission levels</span></span>

<span data-ttu-id="37b56-107">Каждый сайт группы SharePoint Online по умолчанию создается со следующими группами SharePoint:</span><span class="sxs-lookup"><span data-stu-id="37b56-107">Every SharePoint Online team site by default is created with the following SharePoint groups:</span></span>
  
- <span data-ttu-id="37b56-108">\<Имя сайта > члены</span><span class="sxs-lookup"><span data-stu-id="37b56-108">\<site name> Members</span></span>
    
- <span data-ttu-id="37b56-109">\<Имя сайта > посетители</span><span class="sxs-lookup"><span data-stu-id="37b56-109">\<site name> Visitors</span></span>
    
- <span data-ttu-id="37b56-110">\<Имя сайта > владельцев</span><span class="sxs-lookup"><span data-stu-id="37b56-110">\<site name> Owners</span></span>
    
<span data-ttu-id="37b56-111">Эти группы не связаны с группами Office 365 и Azure Active Directory (AD) и позволяют назначать разрешения для ресурсов сайта.</span><span class="sxs-lookup"><span data-stu-id="37b56-111">These groups are separate from Office 365 and Azure Active Directory (AD) groups and are the basis for assigning permissions for the resources of the site.</span></span>
  
<span data-ttu-id="37b56-p101">Набор разрешений, определяющий возможности члена группы SharePoint на сайте, — это уровень разрешений. По умолчанию для сайта группы SharePoint Online доступно три уровня разрешений: "Изменение", "Чтение" и "Полный доступ". В приведенной ниже таблице показаны группы SharePoint и назначенные им по умолчанию уровни разрешений.</span><span class="sxs-lookup"><span data-stu-id="37b56-p101">The set of specific permissions that determines what a member of a SharePoint group can do in a site is a permission level. There are three permission levels by default for a SharePoint Online team site: Edit, Read, and Full control. The following table shows the default correlation of SharePoint groups and assigned permission levels:</span></span>
  
|<span data-ttu-id="37b56-115">**Группа SharePoint**</span><span class="sxs-lookup"><span data-stu-id="37b56-115">**SharePoint group**</span></span>|<span data-ttu-id="37b56-116">**Уровень разрешений**</span><span class="sxs-lookup"><span data-stu-id="37b56-116">**Permission level**</span></span>|
|:-----|:-----|
|<span data-ttu-id="37b56-117">\<Имя сайта > члены</span><span class="sxs-lookup"><span data-stu-id="37b56-117">\<site name> Members</span></span>  <br/> |<span data-ttu-id="37b56-118">Изменение</span><span class="sxs-lookup"><span data-stu-id="37b56-118">Edit</span></span>  <br/> |
|<span data-ttu-id="37b56-119">\<Имя сайта > посетители</span><span class="sxs-lookup"><span data-stu-id="37b56-119">\<site name> Visitors</span></span>  <br/> |<span data-ttu-id="37b56-120">Чтение</span><span class="sxs-lookup"><span data-stu-id="37b56-120">Read</span></span>  <br/> |
|<span data-ttu-id="37b56-121">\<Имя сайта > владельцев</span><span class="sxs-lookup"><span data-stu-id="37b56-121">\<site name> Owners</span></span>  <br/> |<span data-ttu-id="37b56-122">Полный контроль</span><span class="sxs-lookup"><span data-stu-id="37b56-122">Full control</span></span>  <br/> |
   
 <span data-ttu-id="37b56-p102">**Рекомендация:** Можно создать дополнительные группы SharePoint и уровни разрешений. Тем не менее рекомендуется использовать группы SharePoint по умолчанию и уровни разрешений для изолированного сайта SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="37b56-p102">**Best practice:** You can create additional SharePoint groups and permission levels. However, we recommend using the default SharePoint groups and permission levels for your isolated SharePoint Online site.</span></span>
  
<span data-ttu-id="37b56-125">Ниже перечислены группы SharePoint по умолчанию и уровни разрешений.</span><span class="sxs-lookup"><span data-stu-id="37b56-125">Here are the default SharePoint groups and permission levels.</span></span>
  
![Заданные по умолчанию группы SharePoint и уровни разрешений для сайта SharePoint Online.](images/3f892ab4-6479-42f0-a505-1ba0ef94b9c6.png)
  
## <a name="phase-2-assign-permissions-to-users-with-access-groups"></a><span data-ttu-id="37b56-127">Этап 2. Назначение разрешений пользователям с помощью групп доступа</span><span class="sxs-lookup"><span data-stu-id="37b56-127">Phase 2: Assign permissions to users with access groups</span></span>

<span data-ttu-id="37b56-p103">Вы можете назначить разрешения пользователям, добавив либо их учетные записи, либо группы Office 365 или Azure AD, в которых они состоят, в группы SharePoint. После добавления учетным записям пользователей Office 365 назначается уровень разрешений, связанный с группой SharePoint. Это происходит либо непосредственно, либо благодаря членству в группе Office 365 или Azure AD.</span><span class="sxs-lookup"><span data-stu-id="37b56-p103">You can assign permissions to users by adding their user account, or an Office 365 or Azure AD group of which the user account is a member, to the SharePoint groups. Once added, the Office 365 user accounts, either directly or indirectly via membership in an Office 365 or Azure AD group, are assigned the permission level associated with the SharePoint group.</span></span>
  
<span data-ttu-id="37b56-130">Предоставление разрешений на примере групп SharePoint по умолчанию:</span><span class="sxs-lookup"><span data-stu-id="37b56-130">Using the default SharePoint groups as an example:</span></span>
  
- <span data-ttu-id="37b56-131">Члены ** \<имя сайта > члены** группы SharePoint, которые могут включать учетные записи пользователей и группы, назначенных **Изменение** уровня разрешений</span><span class="sxs-lookup"><span data-stu-id="37b56-131">Members of the **\<site name> Members** SharePoint group, which can include both user accounts and groups, are assigned the **Edit** permission level</span></span>
    
- <span data-ttu-id="37b56-132">Члены ** \<имя сайта > посетители** группы SharePoint, которые могут включать учетные записи пользователей и группы, назначенных уровень разрешений **Чтение**</span><span class="sxs-lookup"><span data-stu-id="37b56-132">Members of the **\<site name> Visitors** SharePoint group, which can include both user accounts and groups, are assigned the **Read** permission level</span></span>
    
- <span data-ttu-id="37b56-133">Члены ** \<имя сайта > владельцев** группы SharePoint, которые могут включать учетные записи пользователей и группы, назначенных уровнем разрешений **Полный доступ**</span><span class="sxs-lookup"><span data-stu-id="37b56-133">Members of the **\<site name> Owners** SharePoint group, which can include both user accounts and groups, are assigned the **Full control** permission level</span></span>
    
 <span data-ttu-id="37b56-p104">**Рекомендация:** Несмотря на то, что могут управлять разрешениями с помощью учетных записей отдельных пользователей, мы рекомендуем использовать один группы Azure AD, называется группу доступа вместо этого. Это упрощает управление разрешениями с помощью членство в группе доступ, а не управление пользователем учетных записей для каждой группы SharePoint.</span><span class="sxs-lookup"><span data-stu-id="37b56-p104">**Best practice:** Although you can manage permissions through individual user accounts, we recommend that you use a single Azure AD group, known as an access group, instead. This simplifies the management of permissions through membership in the access group, rather than managing the list of user accounts for each SharePoint group.</span></span>
  
<span data-ttu-id="37b56-p105">Группы Azure AD для Office 365, отличаются от группы Office 365. Azure AD группы отображаются в центре администрирования Office с равным **безопасности** , их **Тип** и не имеет адрес электронной почты. В можно управлять группами Azure AD:</span><span class="sxs-lookup"><span data-stu-id="37b56-p105">Azure AD groups for Office 365 are different than Office 365 groups. Azure AD groups appear in the Office Admin center with their **Type** set to **Security** and do not have an email address. Azure AD groups can be managed within:</span></span>
  
- <span data-ttu-id="37b56-139">Windows Server Active Directory (AD).</span><span class="sxs-lookup"><span data-stu-id="37b56-139">Windows Server Active Directory (AD)</span></span>
    
    <span data-ttu-id="37b56-p106">Это группы, которые были созданы в вашей локальной инфраструктуре Windows Server AD и синхронизируются с подписки Office 365. В центре администрирования Office эти группы имеют **состояние** **Synched с active directory**.</span><span class="sxs-lookup"><span data-stu-id="37b56-p106">These are groups that have been created in your on-premises Windows Server AD infrastructure and synchronized to your Office 365 subscription. In the Office Admin center, these groups have a **Status** of **Synched with active directory**.</span></span>
    
- <span data-ttu-id="37b56-142">Office 365</span><span class="sxs-lookup"><span data-stu-id="37b56-142">Office 365</span></span>
    
    <span data-ttu-id="37b56-p107">Это группы, которые были созданы с помощью центра администрирования Office, Azure портала либо Microsoft PowerShell. В центре администрирования Office эти группы имеют **состояние** из **облака**.</span><span class="sxs-lookup"><span data-stu-id="37b56-p107">These are groups that have been created using either the Office Admin center, the Azure portal, or Microsoft PowerShell. In the Office Admin center, these groups have a **Status** of **Cloud**.</span></span>
    
 <span data-ttu-id="37b56-145">**Рекомендация:** Если вы используете Windows Server AD для локальной и синхронизация с подписки Office 365, выполните на управление пользователями и группами с помощью Windows Server AD.</span><span class="sxs-lookup"><span data-stu-id="37b56-145">**Best practice:** If you are using Windows Server AD on-premises and synchronizing with your Office 365 subscription, perform your user and group management with Windows Server AD.</span></span>
  
<span data-ttu-id="37b56-146">Рекомендуемая структура изолированных сайтов групп SharePoint Online указана ниже.</span><span class="sxs-lookup"><span data-stu-id="37b56-146">For isolated SharePoint Online team sites, the recommended group structure looks like this:</span></span>
  
|<span data-ttu-id="37b56-147">**Группа SharePoint**</span><span class="sxs-lookup"><span data-stu-id="37b56-147">**SharePoint group**</span></span>|<span data-ttu-id="37b56-148">**Группа доступа Microsoft Azure на основе AD**</span><span class="sxs-lookup"><span data-stu-id="37b56-148">**Azure AD-based access group**</span></span>|<span data-ttu-id="37b56-149">**Уровень разрешений**</span><span class="sxs-lookup"><span data-stu-id="37b56-149">**Permission level**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="37b56-150">\<Имя сайта > члены</span><span class="sxs-lookup"><span data-stu-id="37b56-150">\<site name> Members</span></span>  <br/> |<span data-ttu-id="37b56-151">\<Имя сайта > члены</span><span class="sxs-lookup"><span data-stu-id="37b56-151">\<site name> Members</span></span>  <br/> |<span data-ttu-id="37b56-152">Изменение</span><span class="sxs-lookup"><span data-stu-id="37b56-152">Edit</span></span>  <br/> |
|<span data-ttu-id="37b56-153">\<Имя сайта > посетители</span><span class="sxs-lookup"><span data-stu-id="37b56-153">\<site name> Visitors</span></span>  <br/> |<span data-ttu-id="37b56-154">\<Имя сайта > средства просмотра</span><span class="sxs-lookup"><span data-stu-id="37b56-154">\<site name> Viewers</span></span>  <br/> |<span data-ttu-id="37b56-155">Чтение</span><span class="sxs-lookup"><span data-stu-id="37b56-155">Read</span></span>  <br/> |
|<span data-ttu-id="37b56-156">\<Имя сайта > владельцев</span><span class="sxs-lookup"><span data-stu-id="37b56-156">\<site name> Owners</span></span>  <br/> |<span data-ttu-id="37b56-157">\<Имя сайта > "Администраторы"</span><span class="sxs-lookup"><span data-stu-id="37b56-157">\<site name> Admins</span></span>  <br/> |<span data-ttu-id="37b56-158">Полный контроль</span><span class="sxs-lookup"><span data-stu-id="37b56-158">Full control</span></span>  <br/> |
   
 <span data-ttu-id="37b56-p108">**Рекомендация:** Несмотря на то, что Office 365 и Azure AD группы можно использовать в качестве членов групп SharePoint, мы рекомендуем использовать групп Azure AD. Azure AD групп, управляемых с помощью Windows Server AD или Office 365, предоставить большую гибкость использовать вложенные группы для назначения разрешений.</span><span class="sxs-lookup"><span data-stu-id="37b56-p108">**Best practice:** Although you can use either Office 365 or Azure AD groups as members of SharePoint groups, we recommend that you use Azure AD groups. Azure AD groups, managed either through Windows Server AD or Office 365, give you more flexibility to use nested groups to assign permissions.</span></span>
  
<span data-ttu-id="37b56-161">Здесь — это группы SharePoint настроен для использования доступа Microsoft Azure на основе AD групп по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="37b56-161">Here are the default SharePoint groups configured to use Azure AD-based access groups.</span></span>
  
![Использование групп доступа как членов групп стандартного сайта SharePoint Online.](images/50a76328-ae69-483e-9029-ac4e7357b5ef.png)
  
<span data-ttu-id="37b56-163">При создании трех групп доступа учитывайте следующее:</span><span class="sxs-lookup"><span data-stu-id="37b56-163">When designing the three access groups, keep the following in mind:</span></span>
  
- <span data-ttu-id="37b56-164">Должен быть только некоторые элементы в ** \<имя сайта > "Администраторы"** группу доступа, соответствующий небольшое число администраторов SharePoint Online, которые управление сайта группы.</span><span class="sxs-lookup"><span data-stu-id="37b56-164">There should be only a few members in the **\<site name> Admins** access group, corresponding to a small number of SharePoint Online administrators who are managing the team site.</span></span>
    
- <span data-ttu-id="37b56-p109">Большинство участников сайта, в ** \<имя сайта > члены** или ** \<имя сайта > средства просмотра** доступ к группам. Так как веб-элементы в ** \<имя сайта > члены** группу доступа могут получать удаление или изменение ресурсы на сайте, рекомендуется рассмотреть его членства. При работе в сомнительных, добавьте элемент сайта для ** \<имя сайта > средства просмотра** группу доступа.</span><span class="sxs-lookup"><span data-stu-id="37b56-p109">Most of your site members are in the **\<site name> Members** or **\<site name> Viewers** access groups. Because site members in the **\<site name> Members** access group have the ability to delete or modify resources in the site, carefully consider its membership. When in doubt, add the site member to the **\<site name> Viewers** access group.</span></span>
    
<span data-ttu-id="37b56-168">Ниже приведен пример группы SharePoint и групп доступа для изолированного использования сайта с именем ProjectX.</span><span class="sxs-lookup"><span data-stu-id="37b56-168">Here is an example of the SharePoint groups and access groups for an isolated site named ProjectX.</span></span>
  
![Пример использования групп доступа для сайта SharePoint Online, названного ProjectX.](images/13afe542-9ffd-4671-9f48-210a0e2a502a.png)
  
## <a name="phase-3-use-nested-azure-ad-groups"></a><span data-ttu-id="37b56-170">Этап 3: Использование вложенных групп Azure AD</span><span class="sxs-lookup"><span data-stu-id="37b56-170">Phase 3: Use nested Azure AD groups</span></span>

<span data-ttu-id="37b56-p110">Для проекта, ограничен небольшого числа людей один уровень доступа Microsoft Azure на основе AD группы, добавленные в группы SharePoint сайта подходит для большинства вариантов. Тем не менее, если у вас есть много людей и тем пользователям, которые уже члены установлены Azure AD групп можно проще назначить разрешения SharePoint с помощью вложенные группы или группы, которые содержат другие группы в качестве членов.</span><span class="sxs-lookup"><span data-stu-id="37b56-p110">For a project confined to a small number of people, a single level of Azure AD-based access groups added to the SharePoint groups of the site will fit most scenarios. However, if you have a large number of people and those people are already members of established Azure AD groups, you can more easily assign SharePoint permissions by using nested groups, or groups that contain other groups as members.</span></span>
  
<span data-ttu-id="37b56-p111">Например, вы хотите создать изолированный сайт группы SharePoint Online для совместной работы руководителей отделов продаж, маркетинга, поддержки, а также инженерно-технического и юридического отделов, и у этих отделов уже есть группы руководителей. Вместо того чтобы создавать группу для новых участников сайта и добавлять в нее все учетные записи руководителей, добавьте существующие группы руководителей каждого отдела в новую группу.</span><span class="sxs-lookup"><span data-stu-id="37b56-p111">For example, you want to create an isolated SharePoint online team site for collaboration among the executives of the sales, marketing, engineering, legal, and support departments and those departments already their own groups with executive user account membership. Rather than creating a new group for the new site members and placing all the individual executive user accounts in it, put the existing executive groups for each department in the new group.</span></span>
  
 <span data-ttu-id="37b56-p112"> Если у вас одна подписка на Office 365 на несколько организаций, одним уровнем членства в группе для изолированного сайта может быть трудно управлять из-за большого количества учетных записей пользователей. В этом случае можно использовать вложенные группы Azure AD для каждой организации, которые содержат группы в своей организации для управления разрешениями.</span><span class="sxs-lookup"><span data-stu-id="37b56-p112">If you are sharing an Office 365 subscription between multiple organizations, a single level of group membership for an isolated site for an organization might become difficult to manage due to the sheer number of user accounts. In this case, you can use nested Azure AD groups for each organization that contain the groups within their organizations to manage the permissions.</span></span>
  
<span data-ttu-id="37b56-177">Чтобы использовать вложенные группы Azure AD:</span><span class="sxs-lookup"><span data-stu-id="37b56-177">To use nested Azure AD groups:</span></span>
  
1. <span data-ttu-id="37b56-178">Определите или создайте группы Azure AD, которые будут содержать учетные записи пользователей, и добавьте соответствующие учетные записи пользователей в качестве членов.</span><span class="sxs-lookup"><span data-stu-id="37b56-178">Identify or create the Azure AD groups that will contain user accounts and add the appropriate user accounts as members.</span></span>
    
2. <span data-ttu-id="37b56-179">Создайте общую группу доступа на основе Azure AD, которая будет содержать другие группы Azure AD, и добавьте эти группы в качестве членов.</span><span class="sxs-lookup"><span data-stu-id="37b56-179">Create the container Azure AD-based access group that will contain the other Azure AD groups and add those groups as members.</span></span>
    
3.  <span data-ttu-id="37b56-180"> Чтобы предоставить общей группе доступа нужный уровень доступа, укажите группу SharePoint и соответствующий уровень разрешений.</span><span class="sxs-lookup"><span data-stu-id="37b56-180">For the appropriate level of access for the container access group, identify the SharePoint group and corresponding permission level.</span></span>
    
> [!NOTE]
> <span data-ttu-id="37b56-181">Вложенные группы Office 365 не поддерживаются.</span><span class="sxs-lookup"><span data-stu-id="37b56-181">You cannot use nested Office 365 groups.</span></span> 
  
<span data-ttu-id="37b56-182">Ниже приведен пример вложенных Azure AD группами для доступа к группе элементов ProjectX.</span><span class="sxs-lookup"><span data-stu-id="37b56-182">Here is an example of nested Azure AD groups for the ProjectX member access group.</span></span>
  
![Использование вложенных групп доступа на примере группы доступа членов для сайта ProjectX.](images/2abca710-bf9e-4ce8-9bcd-a8e128264fb1.png)
  
<span data-ttu-id="37b56-184">Так как все учетные записи пользователей в справочных материалов, проектирование и проекта влечет за собой группы должны быть участниками сайта, проще добавить их Azure AD группы в группу доступа ProjectX члены.</span><span class="sxs-lookup"><span data-stu-id="37b56-184">Because all of the user accounts in the Research, Engineering, and Project leads teams are intended to be site members, it is easier to add their Azure AD groups to the ProjectX Members access group.</span></span>
  
## <a name="next-step"></a><span data-ttu-id="37b56-185">Следующее действие</span><span class="sxs-lookup"><span data-stu-id="37b56-185">Next step</span></span>

<span data-ttu-id="37b56-186">Если вы готовы для создания и настройки изолированной сайта в рабочей среде, видеть [Развертывание изолированного SharePoint Online сайт группы](deploy-an-isolated-sharepoint-online-team-site.md).</span><span class="sxs-lookup"><span data-stu-id="37b56-186">When you are ready to create and configure an isolated site in production, see [Deploy an isolated SharePoint Online team site](deploy-an-isolated-sharepoint-online-team-site.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="37b56-187">See Also</span><span class="sxs-lookup"><span data-stu-id="37b56-187">See Also</span></span>

[<span data-ttu-id="37b56-188">Изолированные сайты групп SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="37b56-188">Isolated SharePoint Online team sites</span></span>](isolated-sharepoint-online-team-sites.md)
  
[<span data-ttu-id="37b56-189">Управление изолированным сайтом группы SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="37b56-189">Manage an isolated SharePoint Online team site</span></span>](manage-an-isolated-sharepoint-online-team-site.md)
  
[<span data-ttu-id="37b56-190">Решения для обеспечения безопасности</span><span class="sxs-lookup"><span data-stu-id="37b56-190">Security solutions</span></span>](security-solutions.md)

[<span data-ttu-id="37b56-191">Развертывание изолированного сайта группы SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="37b56-191">Deploy an isolated SharePoint Online team site</span></span>](deploy-an-isolated-sharepoint-online-team-site.md)



