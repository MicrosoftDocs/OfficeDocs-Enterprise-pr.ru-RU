---
title: "Настройка групп и пользователей для среды разработки и тестирования политической кампании"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: None
ms.custom:
- DecEntMigration
- Strat_O365_Enterprise
ms.assetid: 0e22bcf3-bad3-42a4-b44f-276e0cf4790f
description: "Сводка: Создание Office 365 и мобильных устройств предприятия + безопасности (Командной) пробной подписки с пользователями и группами в среде разработки и тестирования политических кампании."
ms.openlocfilehash: 7faf428fc2225d3f31297ba6bf83a10a7682009a
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2017
---
# <a name="configure-groups-and-users-for-a-political-campaign-devtest-environment"></a><span data-ttu-id="878fb-103">Настройка групп и пользователей для среды разработки и тестирования политической кампании</span><span class="sxs-lookup"><span data-stu-id="878fb-103">Configure groups and users for a political campaign dev/test environment</span></span>

 <span data-ttu-id="878fb-104">**Сводка:** Создайте Office 365 и мобильных устройств предприятия + безопасности (Командной) пробной подписки с пользователями и группами в среде разработки и тестирования политических кампании.</span><span class="sxs-lookup"><span data-stu-id="878fb-104">**Summary:** Create Office 365 and Enterprise Mobility + Security (EMS) trial subscriptions with users and groups for a political campaign dev/test environment.</span></span>
  
<span data-ttu-id="878fb-105">Для создания среды разработки или тестирования, которая включает в себя упрощенный учетных записей и групп для решения [Майкрософт по обеспечению безопасности политических по сбору средств, некоммерческим организациями и другие гибкой организации](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md) , используйте инструкции в данной статье.</span><span class="sxs-lookup"><span data-stu-id="878fb-105">Use the instructions in this article to create a dev/test environment that includes simplified user accounts and groups for the [Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md) solution.</span></span>
  
## <a name="phase-1-create-your-office-365-devtest-environment"></a><span data-ttu-id="878fb-106">Этап 1. Создание среды разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="878fb-106">Phase 1: Create your Office 365 dev/test environment</span></span>

<span data-ttu-id="878fb-107">На этом этапе получения пробной подписки для Office 365 E5 и мобильных устройств предприятия + E5 безопасности (Командной) для вымышленной организации, представляющий политических кампании.</span><span class="sxs-lookup"><span data-stu-id="878fb-107">In this phase, you obtain trial subscriptions for Office 365 E5 and Enterprise Mobility + Security (EMS) E5 for a fictional organization that represents a political campaign.</span></span>
  
<span data-ttu-id="878fb-108">Во-первых следуйте инструкциям в **Этап 2** в [Office 365 dev/тестовой среды](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="878fb-108">First, follow the instructions in **Phase 2** of the [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="878fb-109">Затем регистрация для пробной подписки Командной E5 и добавить его в той же организации, что пробной подписки Office 365.</span><span class="sxs-lookup"><span data-stu-id="878fb-109">Next, sign up for the EMS E5 trial subscription and add it to the same organization as your Office 365 trial subscription.</span></span>
  
1. <span data-ttu-id="878fb-p101">При необходимости, войдите в портал Office 365 с использованием учетных данных учетной записи глобального администратора пробной подписки. Дополнительные сведения см [Where для входа в Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="878fb-p101">If needed, sign in to the Office 365 portal with the credentials of the global administrator account of your trial subscription. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="878fb-112">Щелкните плитку **администрирования** .</span><span class="sxs-lookup"><span data-stu-id="878fb-112">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="878fb-113">На вкладке **центра администрирования Office** в браузере на панели навигации слева щелкните **выставления счетов > службы приобретения**.</span><span class="sxs-lookup"><span data-stu-id="878fb-113">On the **Office Admin center** tab in your browser, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="878fb-p102">На странице " **службы приобретения** " Поиск элемента **мобильной работы предприятия + E5 безопасности** . Наведите указатель мыши на его и нажмите кнопку **Пуск бесплатную пробную версию**.</span><span class="sxs-lookup"><span data-stu-id="878fb-p102">On the **Purchase services** page, find the **Enterprise Mobility + Security E5** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="878fb-116">На странице " **Подтверждение заказа** " щелкните **Теперь попробуйте**.</span><span class="sxs-lookup"><span data-stu-id="878fb-116">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="878fb-117">На странице **получения заказа** нажмите кнопку **Продолжить**.</span><span class="sxs-lookup"><span data-stu-id="878fb-117">On the **Order receipt** page, click **Continue**.</span></span>
    
<span data-ttu-id="878fb-118">Рассмотрим процедуру включения E5 Командной лицензии для учетной записи глобального администратора.</span><span class="sxs-lookup"><span data-stu-id="878fb-118">Next, enable the EMS E5 license for your global administrator account.</span></span>
  
1. <span data-ttu-id="878fb-119">На вкладке **Центр администрирования Office 365** в браузере на панели навигации слева щелкните **Пользователи > Активные пользователи**.</span><span class="sxs-lookup"><span data-stu-id="878fb-119">On the **Office 365 Admin center** tab in your browser, in the left navigation, click **Users > Active users**.</span></span>
    
2. <span data-ttu-id="878fb-120">Выберите учетную запись глобального администратора и нажмите кнопку **Изменить** для **лицензий на продукт**.</span><span class="sxs-lookup"><span data-stu-id="878fb-120">Click your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="878fb-121">В области **лицензий на продукт** включить лицензии для **мобильных устройств предприятия + E5 безопасности** для **на**, нажмите кнопку **Сохранить** и дважды нажмите кнопку **Закрыть** .</span><span class="sxs-lookup"><span data-stu-id="878fb-121">On the **Product licenses** pane, turn the product license for **Enterprise Mobility + Security E5** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
## <a name="phase-2-create-and-configure-your-azure-active-directory-ad-groups"></a><span data-ttu-id="878fb-122">Этап 2. Создание и настройка групп Azure Active Directory (AD)</span><span class="sxs-lookup"><span data-stu-id="878fb-122">Phase 2: Create and configure your Azure Active Directory (AD) groups</span></span>

<span data-ttu-id="878fb-123">На этом этапе создаются и настраиваются группы Azure AD для кампании.</span><span class="sxs-lookup"><span data-stu-id="878fb-123">In this phase, you create and configure the Azure AD groups for your campaign.</span></span>
  
<span data-ttu-id="878fb-124">Во-первых создайте набор групп для обычной политических кампании с порталом Azure.</span><span class="sxs-lookup"><span data-stu-id="878fb-124">First, create a set of groups for a typical political campaign with the Azure portal.</span></span>
  
1. <span data-ttu-id="878fb-125">На отдельной вкладке в браузере перейдите на портале Azure по [https://portal.azure.com](https://portal.azure.com). При необходимости вход с помощью учетных данных учетной записи глобального администратора для пробной подписки Office 365 E5.</span><span class="sxs-lookup"><span data-stu-id="878fb-125">On a separate tab in your browser, go to the Azure portal at [https://portal.azure.com](https://portal.azure.com). If needed, sign in with the credentials of the global administrator account for your Office 365 E5 trial subscription.</span></span>
    
2. <span data-ttu-id="878fb-126">На портале Azure щелкните **Azure Active Directory > пользователи и группы > все группы**.</span><span class="sxs-lookup"><span data-stu-id="878fb-126">In the Azure portal, click **Azure Active Directory > Users and groups > All groups**.</span></span>
    
3. <span data-ttu-id="878fb-127">Выполните следующие действия для каждого имени группы в этом списке:</span><span class="sxs-lookup"><span data-stu-id="878fb-127">Do the following steps for each group name in this list:</span></span>
    
  - <span data-ttu-id="878fb-128">Старший и стратегический персонал</span><span class="sxs-lookup"><span data-stu-id="878fb-128">Senior and strategic staff</span></span>
    
  - <span data-ttu-id="878fb-129">ИТ-персонал</span><span class="sxs-lookup"><span data-stu-id="878fb-129">IT staff</span></span>
    
  - <span data-ttu-id="878fb-130">Специалисты по аналитике</span><span class="sxs-lookup"><span data-stu-id="878fb-130">Analytics staff</span></span>
    
  - <span data-ttu-id="878fb-131">Основной персонал</span><span class="sxs-lookup"><span data-stu-id="878fb-131">Regular core staff</span></span>
    
  - <span data-ttu-id="878fb-132">Оперативный персонал</span><span class="sxs-lookup"><span data-stu-id="878fb-132">Operations staff</span></span>
    
  - <span data-ttu-id="878fb-133">Выездной персонал</span><span class="sxs-lookup"><span data-stu-id="878fb-133">Field staff</span></span>
    
1. <span data-ttu-id="878fb-134">На blade **все группы** нажмите кнопку **+ новую группу**.</span><span class="sxs-lookup"><span data-stu-id="878fb-134">On the **All groups** blade, click **+ New group**.</span></span>
    
2. <span data-ttu-id="878fb-135">В поле **имя**введите имя группы в списке.</span><span class="sxs-lookup"><span data-stu-id="878fb-135">Type the group name from the list in **Name**.</span></span>
    
3. <span data-ttu-id="878fb-136">Выберите **динамических пользователя** **членства**.</span><span class="sxs-lookup"><span data-stu-id="878fb-136">Select **Dynamic user** in **Membership**.</span></span>
    
4. <span data-ttu-id="878fb-137">Для **включения Office компонентов**, нажмите кнопку **Да** .</span><span class="sxs-lookup"><span data-stu-id="878fb-137">Click **Yes** for **Enable Office features**.</span></span>
    
5. <span data-ttu-id="878fb-138">Нажмите кнопку **Добавить динамический запрос**.</span><span class="sxs-lookup"><span data-stu-id="878fb-138">Click **Add dynamic query**.</span></span>
    
6. <span data-ttu-id="878fb-139">В **Добавление пользователей где**, выберите **отдела**.</span><span class="sxs-lookup"><span data-stu-id="878fb-139">In **Add users where**, select **department**.</span></span>
    
7. <span data-ttu-id="878fb-140">В следующем поле выберите **равно**.</span><span class="sxs-lookup"><span data-stu-id="878fb-140">In the next field, select **Equals**.</span></span>
    
8. <span data-ttu-id="878fb-141">В следующем поле введите имя группы в списке.</span><span class="sxs-lookup"><span data-stu-id="878fb-141">In the next field, type the group name from the list.</span></span>
    
9. <span data-ttu-id="878fb-142">Нажмите кнопку **Добавить запрос**и затем нажмите кнопку **Создать**.</span><span class="sxs-lookup"><span data-stu-id="878fb-142">Click **Add query**, and then click **Create**.</span></span>
    
10. <span data-ttu-id="878fb-143">Выберите **пользователей и групп — все группы**.</span><span class="sxs-lookup"><span data-stu-id="878fb-143">Click **Users and groups - All groups**.</span></span>
    
<span data-ttu-id="878fb-144">Далее следует настроить группы, чтобы участники автоматически назначаются лицензии Office 365 E5 и E5 Командной.</span><span class="sxs-lookup"><span data-stu-id="878fb-144">Next, you configure the groups so that members are automatically assigned Office 365 E5 and EMS E5 licenses.</span></span>
  
1. <span data-ttu-id="878fb-145">На портале Azure щелкните **Azure Active Directory > лицензий > всех продуктов**.</span><span class="sxs-lookup"><span data-stu-id="878fb-145">In the Azure portal, click **Azure Active Directory > Licenses > All products**.</span></span>
    
2. <span data-ttu-id="878fb-146">В списке выберите **Enterprise мобильности + E5 безопасности** и **Office 365 корпоративный E5**и нажмите кнопку **+ Назначение**.</span><span class="sxs-lookup"><span data-stu-id="878fb-146">In the list, select **Enterprise Mobility + Security E5** and **Office 365 Enterprise E5**, and then click **+ Assign**.</span></span>
    
3. <span data-ttu-id="878fb-147">В blade **Назначение лицензии** нажмите кнопку **пользователи и группы**.</span><span class="sxs-lookup"><span data-stu-id="878fb-147">In the **Assign license** blade, click **Users and groups**.</span></span>
    
4. <span data-ttu-id="878fb-148">В списке выберите следующие группы:</span><span class="sxs-lookup"><span data-stu-id="878fb-148">In the list of groups, select the following:</span></span>
    
  - <span data-ttu-id="878fb-149">Специалисты по аналитике</span><span class="sxs-lookup"><span data-stu-id="878fb-149">Analytics staff</span></span>
    
  - <span data-ttu-id="878fb-150">Выездной персонал</span><span class="sxs-lookup"><span data-stu-id="878fb-150">Field staff</span></span>
    
  - <span data-ttu-id="878fb-151">ИТ-персонал</span><span class="sxs-lookup"><span data-stu-id="878fb-151">IT staff</span></span>
    
  - <span data-ttu-id="878fb-152">Оперативный персонал</span><span class="sxs-lookup"><span data-stu-id="878fb-152">Operations staff</span></span>
    
  - <span data-ttu-id="878fb-153">Основной персонал</span><span class="sxs-lookup"><span data-stu-id="878fb-153">Regular core staff</span></span>
    
  - <span data-ttu-id="878fb-154">Старший и стратегический персонал</span><span class="sxs-lookup"><span data-stu-id="878fb-154">Senior and strategic staff</span></span>
    
5. <span data-ttu-id="878fb-155">Нажмите кнопку **выбрать**и нажмите кнопку **назначить**.</span><span class="sxs-lookup"><span data-stu-id="878fb-155">Click **Select**, and then click **Assign**.</span></span>
    
6. <span data-ttu-id="878fb-156">Закройте вкладку портала Azure в браузере.</span><span class="sxs-lookup"><span data-stu-id="878fb-156">Close the Azure portal tab in your browser.</span></span>
    
## <a name="phase-3-add-your-user-accounts"></a><span data-ttu-id="878fb-157">Этап 3. Добавление учетных записей пользователей</span><span class="sxs-lookup"><span data-stu-id="878fb-157">Phase 3: Add your user accounts</span></span>

<span data-ttu-id="878fb-158">На этом этапе добавляются демонстрационные учетные записи пользователей для политической кампании.</span><span class="sxs-lookup"><span data-stu-id="878fb-158">In this phase, you add the example user accounts for your political campaign.</span></span>
  
<span data-ttu-id="878fb-159">Во-первых, можно [подключить с помощью модуля Azure Active Directory версии 2 PowerShell](https://go.microsoft.com/fwlink/?linkid=842218).</span><span class="sxs-lookup"><span data-stu-id="878fb-159">First, you [Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218).</span></span>
  
<span data-ttu-id="878fb-160">Затем введите название организации, адрес и общий пароль и выполните эти команды в командной строке PowerShell или интегрированной среде сценариев (ISE):</span><span class="sxs-lookup"><span data-stu-id="878fb-160">Next, you fill in your organization name, your location, and a common password, and then run these commands from the PowerShell command prompt or Integrated Script Environment (ISE):</span></span>
  
```
$orgName="<organization name, such as contoso for the contoso.onmicrosoft.com trial subscription domain name>"
$location="<the ISO ALPHA2 country code, such as US for the United States>"
$commonPassword="<common password for all the new accounts>"

$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password=$commonPassword

$deptName="Senior and strategic staff"
$userNames=@("Candidate","ChiefOfStaff","Strategic1") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="IT staff"
$userNames=@("ITAdmin1","ITAdmin2") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Analytics staff"
$userNames=@("DataScientist1") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Regular core staff"
$userNames=@("Regular1","Regular2") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Operations staff"
$userNames=@("Operations1") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Field staff"
$userNames=@("FieldConsultant1") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }

```

> [!IMPORTANT]
> <span data-ttu-id="878fb-p103">Общий пароль используется для автоматизации и удобства настройки в среде разработки или тестирования. Не рекомендуется для производственных подписок. При входе с каждой из этих новых учетных записей пользователя, будет предложено изменить пароль.</span><span class="sxs-lookup"><span data-stu-id="878fb-p103">The use of a common password here is for automation and ease of configuration for a dev/test environment. This is not recommended for production subscriptions. As you sign in with each of these new user accounts, you will be prompted to change the password.</span></span> 
  
<span data-ttu-id="878fb-164">Чтобы проверить работу динамического членства в группах и группового лицензирования, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="878fb-164">Use these steps to verify that dynamic group membership and group-based licensing are working correctly.</span></span>
  
1. <span data-ttu-id="878fb-165">На вкладке **Microsoft Office для дома** браузера щелкните плитку **администрирования** .</span><span class="sxs-lookup"><span data-stu-id="878fb-165">From the **Microsoft Office Home** tab of your browser, click the **Admin** tile.</span></span>
    
2. <span data-ttu-id="878fb-166">На вкладке **центра администрирования Office** нового обозревателя щелкните **Пользователи**.</span><span class="sxs-lookup"><span data-stu-id="878fb-166">From the new **Office Admin center** tab of your browser, click **Users**.</span></span>
    
3. <span data-ttu-id="878fb-167">В списке пользователей выберите **кандидата**.</span><span class="sxs-lookup"><span data-stu-id="878fb-167">In the list of users, click **Candidate**.</span></span>
    
4. <span data-ttu-id="878fb-168">В области, где перечислены свойства учетной записи пользователя **кандидата** убедитесь, что:</span><span class="sxs-lookup"><span data-stu-id="878fb-168">In the pane that lists the properties of the **Candidate** user account, verify that:</span></span>
    
  - <span data-ttu-id="878fb-169">Это должна быть членом группы **старший и стратегического персонала** (в **группах**).</span><span class="sxs-lookup"><span data-stu-id="878fb-169">It is a member of the **Senior and strategic staff** group (in **Group memberships**).</span></span>
    
  - <span data-ttu-id="878fb-170">Она была назначена лицензий **Enterprise мобильности + E5 безопасности** и **Office 365 корпоративный E5** (в **лицензий продукта**).</span><span class="sxs-lookup"><span data-stu-id="878fb-170">It has been assigned the **Enterprise Mobility + Security E5** and **Office 365 Enterprise E5** licenses (in **Product licenses**).</span></span>
    
5. <span data-ttu-id="878fb-171">Закройте область учетной записи пользователя **кандидата** .</span><span class="sxs-lookup"><span data-stu-id="878fb-171">Close the **Candidate** user account pane.</span></span>
    
## <a name="record-values-for-future-reference"></a><span data-ttu-id="878fb-172">Запишите значения для дальнейшего использования</span><span class="sxs-lookup"><span data-stu-id="878fb-172">Record values for future reference</span></span>

<span data-ttu-id="878fb-173">Запишите эти значения для работы с пробными подписками Office 365 и EMS для этой среды разработки и тестирования:</span><span class="sxs-lookup"><span data-stu-id="878fb-173">Record these values for working with the Office 365 and EMS trial subscriptions for this dev/test environment:</span></span>
  
- <span data-ttu-id="878fb-174">Название вашей организации: _______________________________________________ </span><span class="sxs-lookup"><span data-stu-id="878fb-174">Your trial subscription organization name: _______________________________________________</span></span> 
    
    <span data-ttu-id="878fb-175">Например, для доменного имени contoso.onmicrosoft.com название организации — "contoso".</span><span class="sxs-lookup"><span data-stu-id="878fb-175">For example, for the trial subscription domain name of contoso.onmicrosoft.com, the organization name is "contoso".</span></span>
    
- <span data-ttu-id="878fb-176">Имя глобального администратора Office 365: ___.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="878fb-176">The Office 365 global administrator name: ____________________________________.onmicrosoft.com</span></span>
    
    <span data-ttu-id="878fb-177">Запишите пароль для этой учетной записи и общие исходный пароль для других учетных записей пользователей в надежном месте.</span><span class="sxs-lookup"><span data-stu-id="878fb-177">Record the password for this account and the common initial password for the other user accounts in a secure location.</span></span>
    
## <a name="next-step"></a><span data-ttu-id="878fb-178">Следующее действие</span><span class="sxs-lookup"><span data-stu-id="878fb-178">Next step</span></span>

<span data-ttu-id="878fb-179">Создание четырех различных типов SharePoint Online веб-сайтов групп в этой среде разработки и тестирования с [сайтами групп создать в среде разработки и тестирования политических кампании](create-team-sites-in-a-political-campaign-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="878fb-179">Build the four different types of SharePoint Online team sites in this dev/test environment with [Create team sites in a political campaign dev/test environment](create-team-sites-in-a-political-campaign-dev-test-environment.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="878fb-180">See Also</span><span class="sxs-lookup"><span data-stu-id="878fb-180">See Also</span></span>

[<span data-ttu-id="878fb-181">Руководство по безопасности (Майкрософт) для политических кампаний, некоммерческих и других динамических организаций</span><span class="sxs-lookup"><span data-stu-id="878fb-181">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[<span data-ttu-id="878fb-182">Создание веб-сайтов групп в среде разработки и тестирования политических кампаний (en)</span><span class="sxs-lookup"><span data-stu-id="878fb-182">Create team sites in a political campaign dev/test environment</span></span>](create-team-sites-in-a-political-campaign-dev-test-environment.md)
  
[<span data-ttu-id="878fb-183">Руководства по лаборатории тестирования для принятия облачных решений</span><span class="sxs-lookup"><span data-stu-id="878fb-183">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="878fb-184">Освоение облака и гибридные решения</span><span class="sxs-lookup"><span data-stu-id="878fb-184">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)




