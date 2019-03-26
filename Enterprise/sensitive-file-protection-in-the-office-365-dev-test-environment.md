---
title: Защита конфиденциальных файлов в среде разработки и тестирования Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: 27ecff45-06a6-4629-bc45-9dab4eef3a21
description: Сводка. Настройка и демонстрация защиты Office 365 Information Rights Management защищает конфиденциальные файлы, даже если они публикуются в неправильном семействе веб-сайтов SharePoint Online.
ms.openlocfilehash: 59d4cf56113f8b787f0caeaefddae135ad8e6249
ms.sourcegitcommit: 4ef8e113fa20b539de1087422455fc26ff123d55
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "30574073"
---
# <a name="sensitive-file-protection-in-the-office-365-devtest-environment"></a><span data-ttu-id="0df48-103">Защита конфиденциальных файлов в среде разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="0df48-103">Sensitive file protection in the Office 365 dev/test environment</span></span>

 <span data-ttu-id="0df48-104">**Сводка:** Настройте и продемонстрируйте, как служба управления правами на доступ к данным Office 365 защищает конфиденциальные файлы, даже если они публикуются в неправильном семействе веб-сайтов SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="0df48-104">**Summary:** Configure and demonstrate how Office 365 Information Rights Management protects your sensitive files, even when they are posted to the wrong SharePoint Online site collection.</span></span>
  
<span data-ttu-id="0df48-p101">Управление правами на доступ к данным (IRM) в Office 365 — это набор функций для защиты документов, скачиваемых из списков и библиотек SharePoint Online. Скачиваемые файлы зашифрованы и содержат те же разрешения на открытие, копирование, сохранение и печать, которые настроены в библиотеке SharePoint Online, в которой они хранились.</span><span class="sxs-lookup"><span data-stu-id="0df48-p101">Information Rights Management (IRM) in Office 365 is a set of capabilities to protect documents that are downloaded from SharePoint Online libraries and lists. Downloaded files are encrypted and contain the open, copy, save, and print permissions that reflect the SharePoint Online library in which they were stored.</span></span>
  
<span data-ttu-id="0df48-107">В этой статье описано, как включить и протестировать IRM в Office 365 для файлов, содержащих потенциально конфиденциальную информацию, в пробной подписке на Office 365.</span><span class="sxs-lookup"><span data-stu-id="0df48-107">With the instructions in this article, you enable and test IRM in Office 365 for files containing possible sensitive information in your Office 365 trial subscription.</span></span>
  
> [!TIP]
> <span data-ttu-id="0df48-108">Щелкните [здесь](http://aka.ms/catlgstack), чтобы просмотреть схему всех статей, относящихся к руководствам по лаборатории тестирования в One Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="0df48-108">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-office-365-devtest-environment"></a><span data-ttu-id="0df48-109">Этап 1. Создание среды разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="0df48-109">Phase 1: Build out your Office 365 dev/test environment</span></span>

<span data-ttu-id="0df48-110">Если вам нужно просто протестировать защиту конфиденциальных файлов (в упрощенной форме с минимальными требованиями), следуйте инструкциям в статье [Office 365 dev/test environment](office-365-dev-test-environment.md) (этапы 2 и 3).</span><span class="sxs-lookup"><span data-stu-id="0df48-110">If you just want to test sensitive file protection in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="0df48-111">Если вам нужно протестировать защиту конфиденциальных файлов в условиях смоделированного предприятия, следуйте инструкциям в статье [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="0df48-111">If you want to test sensitive file protection in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="0df48-p102">Для тестирования не требуется условная корпоративная среда разработки и тестирования, которая включает условную интрасеть, подключенную к Интернету, и синхронизацию каталогов для леса Windows Server AD. Она показана здесь лишь для того, чтобы вы могли протестировать защиту конфиденциальных файлов и поэкспериментировать с этим компонентом в типичной для организаций среде.</span><span class="sxs-lookup"><span data-stu-id="0df48-p102">Testing sensitive file protection does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest. It is provided here as an option so that you can test sensitive file protection and experiment with it in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-demonstrate-how-documents-from-permissions-protected-sites-can-be-leaked"></a><span data-ttu-id="0df48-114">Этап 2. Демонстрация утечки документов с сайтов, защищенных системой прав доступа</span><span class="sxs-lookup"><span data-stu-id="0df48-114">Phase 2: Demonstrate how documents from permissions-protected sites can be leaked</span></span>

<span data-ttu-id="0df48-115">На этом этапе демонстрируется, что пользователь может скачать документ с сайта, защищенного системой прав доступа, а затем отправить его на незащищенный сайт.</span><span class="sxs-lookup"><span data-stu-id="0df48-115">In this phase, you demonstrate that someone can download a document from a permissions-protected site and then upload it to a site that has wide-open permissions.</span></span>
  
<span data-ttu-id="0df48-116">Для начала создайте три новых учетных записи пользователя для руководителей и назначьте им лицензии Office 365 E5.</span><span class="sxs-lookup"><span data-stu-id="0df48-116">First, you add three new user accounts that represent executives and assign them Office 365 E5 licenses.</span></span>
  
<span data-ttu-id="0df48-117">Используйте инструкции из статьи [Подключение к Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx) для установки модулей PowerShell (при необходимости) и подключения к новой подписке Office 365 с:</span><span class="sxs-lookup"><span data-stu-id="0df48-117">Use the instructions in [Connect to Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx) to install the PowerShell modules (if needed) and connect to your new Office 365 subscription from:</span></span>
  
- <span data-ttu-id="0df48-118">компьютера (для упрощенной среды разработки и тестирования Office 365);</span><span class="sxs-lookup"><span data-stu-id="0df48-118">Your computer (for the lightweight Office 365 dev/test environment).</span></span>
    
- <span data-ttu-id="0df48-119">виртуальной машины CLIENT1 (для среды Office 365 для разработки и тестирования смоделированного предприятия).</span><span class="sxs-lookup"><span data-stu-id="0df48-119">The CLIENT1 virtual machine (for the simulated enterprise Office 365 dev/test environment).</span></span>
    
<span data-ttu-id="0df48-120">В диалоговом окне **Запрос учетных данных Windows PowerShell** введите имя глобального администратора Office 365 (например, jdoe@contosotoycompany.onmicrosoft.com) и пароль пробной подписки на Office 365.</span><span class="sxs-lookup"><span data-stu-id="0df48-120">In the **Windows PowerShell Credential Request** dialog box, type the Office 365 global administrator name (example: jdoe@contosotoycompany.onmicrosoft.com) and password of your Office 365 trial subscription.</span></span>
  
<span data-ttu-id="0df48-121">Введите название организации (например, contosotoycompany) и двузначный код страны, а затем выполните следующие команды в командной строке модуля Windows Azure Active Directory для Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="0df48-121">Fill in your organization name (example: contosotoycompany) and the two-character country code for your location, and then run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$licAssignment= $orgName + ":ENTERPRISEPREMIUM"
$userName= "ceo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "CEO" -FirstName "Chief" -LastName "Executive Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

<span data-ttu-id="0df48-122">Запишите в надежном месте пароль, созданный командой **New-MsolUser** для учетной записи генерального директора.</span><span class="sxs-lookup"><span data-stu-id="0df48-122">From the display of the **New-MsolUser** command, note the generated password for the CEO account and record it in a safe location.</span></span>
  
<span data-ttu-id="0df48-123">Выполните следующие команды в командной строке модуля Windows Azure Active Directory для Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="0df48-123">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "cfo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "CFO" -FirstName "Chief" -LastName "Financial Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

<span data-ttu-id="0df48-124">Запишите в надежном месте пароль, созданный командой **New-MsolUser** для учетной записи финансового директора.</span><span class="sxs-lookup"><span data-stu-id="0df48-124">From the display of the **New-MsolUser** command, note the generated password for the CFO account and record it in a safe location.</span></span>
  
<span data-ttu-id="0df48-125">Выполните следующие команды в командной строке модуля Windows Azure Active Directory для Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="0df48-125">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "coo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "COO" -FirstName "Chief" -LastName "Operations Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

<span data-ttu-id="0df48-126">Запишите в надежном месте пароль, созданный командой **New-MsolUser** для учетной записи главного операционного директора.</span><span class="sxs-lookup"><span data-stu-id="0df48-126">From the display of the **New-MsolUser** command, note the generated password for the COO account and record it in a safe location.</span></span>
  
<span data-ttu-id="0df48-127">Теперь создайте закрытую группу "Руководители" и добавьте в нее новые учетные записи.</span><span class="sxs-lookup"><span data-stu-id="0df48-127">Next, you create a private Executives group and add the new executive accounts to it.</span></span>
  
1. <span data-ttu-id="0df48-128">В браузере перейдите на портал Office [http://admin.microsoft.com](http://admin.microsoft.com) и войдите в пробную подПиску на Office 365 с помощью учетной записи глобального администратора.</span><span class="sxs-lookup"><span data-stu-id="0df48-128">In your browser, go to the Office portal at [http://admin.microsoft.com](http://admin.microsoft.com) and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
  - <span data-ttu-id="0df48-129">Если вы используете упрощенную среду разработки и тестирования Office 365, запустите частный сеанс Internet Explorer или вашего браузера и войдите с локального компьютера.</span><span class="sxs-lookup"><span data-stu-id="0df48-129">If you are using the lightweight Office 365 dev/test environment, open a private session of Internet Explorer or your browser and sign in from your local computer.</span></span>
    
  - <span data-ttu-id="0df48-130">Если вы используете условную корпоративную среду разработки и тестирования Office 365, подключитесь к виртуальной машине CLIENT1 с помощью портала Azure, а затем войдите с этой виртуальной машины.</span><span class="sxs-lookup"><span data-stu-id="0df48-130">If you are using the simulated enterprise Office 365 dev/test environment, use the Azure portal to connect to the CLIENT1 virtual machine, and then sign in from CLIENT1.</span></span>
    
2. <span data-ttu-id="0df48-131">На главной вкладке **Microsoft Office** нажмите **Администратор > Группы > Группы**, а затем **Добавить группу**.</span><span class="sxs-lookup"><span data-stu-id="0df48-131">On the **Microsoft Office Home** tab, click **Admin > Groups > Groups**, and then click **Add a group**.</span></span>
    
3. <span data-ttu-id="0df48-132">В поле **Добавить группу** выберите тип **Группа Office 365**, введите **Руководители** в поля **Имя** и **Идентификатор группы**, выберите **Закрытая** в поле **Конфиденциальность** и нажмите **Выбрать владельца**.</span><span class="sxs-lookup"><span data-stu-id="0df48-132">In **Add a group**, select **Office 365 group** for the group type, type **Executives** in **Name** and **Group Id**, select **Private** for **Privacy**, and then click **Select Owner**.</span></span>
    
4. <span data-ttu-id="0df48-133">Выберите имя учетной записи глобального администратора из списка.</span><span class="sxs-lookup"><span data-stu-id="0df48-133">In the list, click your global administrator account name.</span></span>
    
5. <span data-ttu-id="0df48-134">Нажмите **Добавить**, а затем **Закрыть**.</span><span class="sxs-lookup"><span data-stu-id="0df48-134">Click **Add**, and then click **Close**.</span></span>
    
6. <span data-ttu-id="0df48-135">В списке групп выберите **Руководители**.</span><span class="sxs-lookup"><span data-stu-id="0df48-135">In the groups list, click **Executives**.</span></span>
    
7. <span data-ttu-id="0df48-136">Нажмите **Участники > Изменить**.</span><span class="sxs-lookup"><span data-stu-id="0df48-136">Click **Edit for Members**.</span></span>
    
8. <span data-ttu-id="0df48-p103">Нажмите **Добавить участников**. В списке участников выберите следующие учетные записи пользователей:</span><span class="sxs-lookup"><span data-stu-id="0df48-p103">Click **Add members**. In the member list, select the following user accounts:</span></span>
    
  - <span data-ttu-id="0df48-139">генеральный директор;</span><span class="sxs-lookup"><span data-stu-id="0df48-139">Chief Executive Officer</span></span>
    
  - <span data-ttu-id="0df48-140">финансовый директор;</span><span class="sxs-lookup"><span data-stu-id="0df48-140">Chief Financial Officer</span></span>
    
  - <span data-ttu-id="0df48-141">главный операционный директор.</span><span class="sxs-lookup"><span data-stu-id="0df48-141">Chief Operations Officer</span></span>
    
9. <span data-ttu-id="0df48-142">Нажмите **Сохранить**, а затем **Закрыть**.</span><span class="sxs-lookup"><span data-stu-id="0df48-142">Click **Save**, and then click **Close**.</span></span>
    
10. <span data-ttu-id="0df48-143">Закройте вкладку **Центр администрирования Office**.</span><span class="sxs-lookup"><span data-stu-id="0df48-143">Close the **Office Admin center** tab.</span></span>
    
<span data-ttu-id="0df48-144">Теперь создайте семейство веб-сайтов "Руководители" и предоставьте к нему доступ только участникам этой группы.</span><span class="sxs-lookup"><span data-stu-id="0df48-144">Next, you create an Executives site collection and allow just the members of the Executives group to access it.</span></span>
  
1. <span data-ttu-id="0df48-145">На главной вкладке **Microsoft Office** щелкните плитку **Администратор**.</span><span class="sxs-lookup"><span data-stu-id="0df48-145">On the **Microsoft Office Home** tab, click the **Admin** tile.</span></span>
    
2. <span data-ttu-id="0df48-146">На вкладке **центр администрирования Office** выберите **центр администрирования _гт_ SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="0df48-146">On the **Office Admin center** tab, click **Admin centers > SharePoint**.</span></span>
    
3. <span data-ttu-id="0df48-147">На вкладке **центр администрирования SharePoint** щелкните **создать частное семейство веб-сайтов _гт_**.</span><span class="sxs-lookup"><span data-stu-id="0df48-147">On the **SharePoint admin center** tab, click **New > Private site collection**.</span></span>
    
4. <span data-ttu-id="0df48-148">В области Создание семейства веб-сайтов введите **руководители** в поле **название**, руководители в поле URL-адрес, укажите имя учетной записи глобального администратора в поле **Администратор**и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="0df48-148">In the new site collection pane, type **Executives** in **Title**, executives in the URL box, specify the name of your global administrator account in **Administrator**, and then click **OK**.</span></span>
    
5. <span data-ttu-id="0df48-149">ДоЖдитесь, пока не будет создано новое семейство веб-сайтов.</span><span class="sxs-lookup"><span data-stu-id="0df48-149">Wait until the new site collection has been created.</span></span> <span data-ttu-id="0df48-150">По завершении скопируйте URL-адрес нового семейства веб-сайтов руководителей и вставьте его в новую вкладку браузера.</span><span class="sxs-lookup"><span data-stu-id="0df48-150">When complete, copy the URL of the new Executives site collection and paste it into a new tab of your browser.</span></span>
    
6. <span data-ttu-id="0df48-151">Щелкните значок параметров в правом верхнем углу семейства веб-сайтов группы **Руководители**, а затем нажмите **Общий доступ**.</span><span class="sxs-lookup"><span data-stu-id="0df48-151">In the upper right of the **Executives** site collection, click the settings icon, and then click **Shared with**.</span></span>
    
7. <span data-ttu-id="0df48-152">В **папке "руководители"** нажмите кнопку **Дополнительно**.</span><span class="sxs-lookup"><span data-stu-id="0df48-152">In **Share 'Executives'**, click **Advanced**.</span></span>
    
8. <span data-ttu-id="0df48-153">В списке групп SharePoint выберите **Участники группы "Руководители"**.</span><span class="sxs-lookup"><span data-stu-id="0df48-153">In the list of SharePoint groups, click **Executives Members**.</span></span>
    
9. <span data-ttu-id="0df48-154">На странице **Пользователи и группы** нажмите кнопку **Создать**.</span><span class="sxs-lookup"><span data-stu-id="0df48-154">On the **People and Groups** page, click **New**.</span></span>
    
10. <span data-ttu-id="0df48-155">В разделе **общий доступ руководителей**введите **руководители**, выберите группу **руководители** , а затем щелкните **общий доступ**.</span><span class="sxs-lookup"><span data-stu-id="0df48-155">In **Share 'Executives'**, type **Executives**, click the **Executives** group, and then click **Share**.</span></span>
    
11. <span data-ttu-id="0df48-156">Закройте вкладку **Пользователи и группы** .</span><span class="sxs-lookup"><span data-stu-id="0df48-156">Close the **People and groups** tab.</span></span>
    
<span data-ttu-id="0df48-157">Теперь предоставьте всем пользователям доступ к семейству веб-сайтов "Продажи".</span><span class="sxs-lookup"><span data-stu-id="0df48-157">Next, you allow everyone to access the Sales site collection.</span></span>
  
1. <span data-ttu-id="0df48-158">На вкладке **центр администрирования SharePoint** СКОПИРУЙТЕ URL-адрес семейства веб-сайтов Sales и вставьте его в новую вкладку браузера...</span><span class="sxs-lookup"><span data-stu-id="0df48-158">From the **SharePoint admin center** tab, copy the URL of the Sales site collection and paste it into a new tab of your browser..</span></span>
    
2. <span data-ttu-id="0df48-159">Щелкните значок параметров в правом верхнем углу страницы, а затем щелкните **Общий доступ**.</span><span class="sxs-lookup"><span data-stu-id="0df48-159">In the upper right, click the settings icon, and then click **Shared with**.</span></span>
    
3. <span data-ttu-id="0df48-160">В окне **общий доступ к семейству веб-сайтов продаж**нажмите **Дополнительно**.</span><span class="sxs-lookup"><span data-stu-id="0df48-160">In **Share 'Sales site collection'**, click **Advanced**.</span></span>
    
4. <span data-ttu-id="0df48-161">В списке групп SharePoint выберите **Семейство веб-сайтов "Продажи" > Участники**.</span><span class="sxs-lookup"><span data-stu-id="0df48-161">In the list of SharePoint groups, click **Sales site collection Members**.</span></span>
    
5. <span data-ttu-id="0df48-162">На странице **Пользователи и группы** нажмите **Создать**.</span><span class="sxs-lookup"><span data-stu-id="0df48-162">On the **People and Groups** page, click **New**.</span></span>
    
6. <span data-ttu-id="0df48-163">В окне **общий доступ к семейству веб-сайтов продаж**введите **все**, щелкните **все, кроме внешних пользователей**, а затем щелкните **общий доступ**.</span><span class="sxs-lookup"><span data-stu-id="0df48-163">In **Share 'Sales site collection'**, type **Everyone**, click **Everyone except external users**, and then click **Share**.</span></span>
    
7. <span data-ttu-id="0df48-164">Закройте вкладки **Семейство веб-сайтов "Продажи"** и **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="0df48-164">Close the **Sales site collection** and **SharePoint** tabs.</span></span>
    
<span data-ttu-id="0df48-165">Затем войдите в учетную запись руководителя и создайте документ в семействе веб-сайтов "Руководители".</span><span class="sxs-lookup"><span data-stu-id="0df48-165">Next, you sign in with an executive account and create a document in the Executives site collection.</span></span>
  
1. <span data-ttu-id="0df48-166">На главной вкладке \*\*Microsoft Office \*\* щелкните значок пользователя в правом верхнем углу и нажмите **Выйти**.</span><span class="sxs-lookup"><span data-stu-id="0df48-166">On the **Microsoft Office Home** tab, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="0df48-167">Перейдите по ссылке [http://admin.microsoft.com](http://admin.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="0df48-167">Go to [http://admin.microsoft.com](http://admin.microsoft.com).</span></span>
    
3. <span data-ttu-id="0df48-168">На странице **входа в Office 365** выберите **Использовать другую учетную запись**.</span><span class="sxs-lookup"><span data-stu-id="0df48-168">On the **Office 365 sign in** page, click **Use another account**.</span></span>
    
4. <span data-ttu-id="0df48-169">Введите данные учетной записи **генерального директора** и нажмите кнопку **Войти**.</span><span class="sxs-lookup"><span data-stu-id="0df48-169">Type the **CEO** account name and its password, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="0df48-170">на новой вкладке браузера введите URL-адрес семейства веб-сайтов руководителей ( **https://**\<organization наме_гт_**. sharepoint.com/sites/executives**).</span><span class="sxs-lookup"><span data-stu-id="0df48-170">On a new tab of your browser, type the URL to the Executives site collection ( **https://**\<organization name>**.sharepoint.com/sites/executives**).</span></span>
    
6. <span data-ttu-id="0df48-171">В меню **документы**выберите пункт **создать,** а затем щелкните **документ Word**.</span><span class="sxs-lookup"><span data-stu-id="0df48-171">Click **Documents**, click **New,** and then click **Word Document**.</span></span>
    
7. <span data-ttu-id="0df48-172">Щелкните строку заголовка и введите **SensitiveData-BeforeIRM**.</span><span class="sxs-lookup"><span data-stu-id="0df48-172">Click in the title bar and type **SensitiveData-BeforeIRM**.</span></span>
    
8. <span data-ttu-id="0df48-173">Щелкните тело документа и введите **Протокол последнего заседания совета директоров** и нажмите **Руководители**.</span><span class="sxs-lookup"><span data-stu-id="0df48-173">Click in the document body and type **Minutes from the latest board meeting**, and then click **Executives**.</span></span>
    
     <span data-ttu-id="0df48-174"> Документ *\*SensitiveData-BeforeIRM.docx** появится в папке *\*Документы*\*.</span><span class="sxs-lookup"><span data-stu-id="0df48-174">You should see **SensitiveData-BeforeIRM.docx** in the **Documents** folder.</span></span>
    
<span data-ttu-id="0df48-175">Теперь скачайте локальную копию документа SensitiveData-BeforeIRM.docx и случайно опубликуйте ее в семействе веб-сайтов "Продажи".</span><span class="sxs-lookup"><span data-stu-id="0df48-175">Next, you download a local copy of the SensitiveData-BeforeIRM.docx document and then accidentally post it to the Sales site collection.</span></span>
  
1. <span data-ttu-id="0df48-176">На локальном компьютере создайте новую папку (например, C:\\руководствах TLG\\сенситиведататестфилес).</span><span class="sxs-lookup"><span data-stu-id="0df48-176">On your local computer, create a new folder (for example, C:\\TLGs\\SensitiveDataTestFiles).</span></span>
    
2. <span data-ttu-id="0df48-177">На вкладке **Документы** браузера выберите документ **SensitiveData-BeforeIRM.docx**, нажмите значок многоточия и выберите **Скачать**.</span><span class="sxs-lookup"><span data-stu-id="0df48-177">On the **Documents** tab of your browser, select the **SensitiveData-BeforeIRM.docx** document, click the ellipses, and then click **Download**.</span></span>
    
3. <span data-ttu-id="0df48-178">Сохраните документ **SensitiveData-BeforeIRM.docx** в папке, созданной на шаге 1.</span><span class="sxs-lookup"><span data-stu-id="0df48-178">Store the **SensitiveData-BeforeIRM.docx** document in the folder created in step 1.</span></span>
    
4. <span data-ttu-id="0df48-179">на новой вкладке браузера введите URL-адрес семейства веб-сайтов продаж ( **https://**\<organization наме_гт_**. sharepoint.com/sites/sales**).</span><span class="sxs-lookup"><span data-stu-id="0df48-179">On a new tab of your browser, type the URL to the Sales site collection ( **https://**\<organization name>**.sharepoint.com/sites/sales**).</span></span>
    
5. <span data-ttu-id="0df48-180">Выберите папку **Документы\*\*\*\*семейства веб-сайтов "Продажи"**.</span><span class="sxs-lookup"><span data-stu-id="0df48-180">Click the **Documents** folder of the **Sales site collection**.</span></span>
    
6. <span data-ttu-id="0df48-181">Нажмите **Отправить**, выберите документ **SensitiveData-BeforeIRM.docx** в папке, созданной на шаге 1, и нажмите **ОК**.</span><span class="sxs-lookup"><span data-stu-id="0df48-181">Click **Upload**, and then specify **SensitiveData-BeforeIRM.docx** document in the folder created in step 1, and then click **OK**.</span></span>
    
7. <span data-ttu-id="0df48-182">Убедитесь, что документ **SensitiveData-BeforeIRM.docx** находится в папке **Документы**.</span><span class="sxs-lookup"><span data-stu-id="0df48-182">Verify that the **SensitiveData-BeforeIRM.docx** document is in the **Documents** folder.</span></span>
    
8. <span data-ttu-id="0df48-183">Закройте вкладки **Продажи** и **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="0df48-183">Close the **Sales** and **SharePoint** tabs.</span></span>
    
<span data-ttu-id="0df48-184">После этого войдите в учетную запись User5 и откройте документ SensitiveData-BeforeIRM.docx в семействе веб-сайтов "Продажи".</span><span class="sxs-lookup"><span data-stu-id="0df48-184">Next, you sign in as User5 and try to open the SensitiveData-BeforeIRM.docx document in the Sales site collection.</span></span>
  
1. <span data-ttu-id="0df48-185">На главной вкладке \*\*Microsoft Office \*\* щелкните значок пользователя в правом верхнем углу и нажмите **Выйти**.</span><span class="sxs-lookup"><span data-stu-id="0df48-185">On the **Microsoft Office Home** tab, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="0df48-186">Перейдите по ссылке [http://admin.microsoft.com](http://admin.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="0df48-186">Go to [http://admin.microsoft.com](http://admin.microsoft.com).</span></span>
    
3. <span data-ttu-id="0df48-187">На странице **входа в Office 365** выберите **Использовать другую учетную запись**.</span><span class="sxs-lookup"><span data-stu-id="0df48-187">On the **Office 365 sign in** page, click **Use another account**.</span></span>
    
4. <span data-ttu-id="0df48-188">Введите данные учетной записи User5 и нажмите **Войти**.</span><span class="sxs-lookup"><span data-stu-id="0df48-188">Type the User5 account name and its password, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="0df48-189">На новой вкладке браузера введите URL-адрес семейства веб-сайтов продаж.</span><span class="sxs-lookup"><span data-stu-id="0df48-189">On a new tab of your browser, type the URL to the Sales site collection.</span></span>
    
6. <span data-ttu-id="0df48-190">Выберите документ **SensitiveData-BeforeIRM.docx** в папке **Документы\*\*\*\*семейства веб-сайтов "Продажи"**. </span><span class="sxs-lookup"><span data-stu-id="0df48-190">In the **Documents** folder of the **Sales site collection**, click the **SensitiveData-BeforeIRM.docx** document.</span></span>
    
    <span data-ttu-id="0df48-191">Появится его содержимое.</span><span class="sxs-lookup"><span data-stu-id="0df48-191">You should see its contents.</span></span>
    
7. <span data-ttu-id="0df48-192">Закройте вкладки **Документы** и **Семейство веб-сайтов "Продажи"**.</span><span class="sxs-lookup"><span data-stu-id="0df48-192">Close the **Documents** and **Sales site collection** tabs.</span></span>
    
<span data-ttu-id="0df48-193">Случайно опубликовав документ SensitiveData-BeforeIRM.docx в семействе веб-сайтов "Продажи", генеральный директор обошел систему прав доступа семейства веб-сайтов "Руководители".</span><span class="sxs-lookup"><span data-stu-id="0df48-193">By accidentally posting the SensitiveData-BeforeIRM.docx document on the Sales site collection, the CEO bypassed the permissions security of the Executives site collection.</span></span>
  
<span data-ttu-id="0df48-194">Чтобы подготовить Office 365 к этапам 3 и 4, включите IRM для SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="0df48-194">To prepare Office 365 for Phases 3 and 4, enable IRM for SharePoint Online.</span></span>
  
1. <span data-ttu-id="0df48-195">На главной вкладке \*\*Microsoft Office \*\* щелкните значок пользователя в правом верхнем углу и нажмите **Выйти**.</span><span class="sxs-lookup"><span data-stu-id="0df48-195">On the **Microsoft Office Home** tab, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="0df48-196">Перейдите по ссылке [http://admin.microsoft.com](http://admin.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="0df48-196">Go to [http://admin.microsoft.com](http://admin.microsoft.com).</span></span>
    
3. <span data-ttu-id="0df48-197">На странице **входа в Office 365** выберите имя учетной записи глобального администратора, введите пароль и нажмите **Войти**.</span><span class="sxs-lookup"><span data-stu-id="0df48-197">On the **Office 365 sign in** page, click the global administrator account name, type its password, and then click **Sign in**.</span></span>
    
4. <span data-ttu-id="0df48-198">На главной вкладке **Microsoft Office** щелкните **Администратор > Центры администрирования > SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="0df48-198">On the **Microsoft Office Home** tab, click **Admin > Admin centers > SharePoint**.</span></span>
    
5. <span data-ttu-id="0df48-199">На вкладке **Центра администрирования SharePoint** щелкните **Параметры**.</span><span class="sxs-lookup"><span data-stu-id="0df48-199">On the **SharePoint admin center** tab, click **Settings**.</span></span>
    
6. <span data-ttu-id="0df48-200">На странице **Параметры** в разделе **Управление правами на доступ к данным (IRM)** выберите **Использовать службу IRM, указанную в вашей конфигурации**, а затем выберите **Обновить параметры IRM**.</span><span class="sxs-lookup"><span data-stu-id="0df48-200">On the **Settings** page, in the **Information Rights Management (IRM)** section, select **Use the IRM service specified in your configuration**, and then select **Refresh IRM Settings**.</span></span>
    
7. <span data-ttu-id="0df48-201">Закройте вкладку **Центр администрирования SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="0df48-201">Close the **SharePoint admin center** tab.</span></span>
    
## <a name="phase-3-use-sharepoint-information-rights-management-with-an-office-365-private-group"></a><span data-ttu-id="0df48-202">Этап 3. Использование управления правами на доступ к данным SharePoint с закрытой группой Office 365</span><span class="sxs-lookup"><span data-stu-id="0df48-202">Phase 3: Use SharePoint Information Rights Management with an Office 365 private group</span></span>

<span data-ttu-id="0df48-203">На этом этапе используется управление правами на доступ к данным SharePoint с закрытой группой Office 365, чтобы защитить документ с конфиденциальной информацией, даже если он опубликован на сайте с открытым доступом.</span><span class="sxs-lookup"><span data-stu-id="0df48-203">In this phase, you use SharePoint Information Rights Management with an Office 365 private group to protect access to a document with sensitive information, even when it is posted on a site with open permissions.</span></span>
  
<span data-ttu-id="0df48-204">Для начала включите и настройте IRM для библиотеки документов семейства веб-сайтов "Руководители". </span><span class="sxs-lookup"><span data-stu-id="0df48-204">First, you enable and configure IRM for the documents library of the Executives site collection.</span></span> 
  
1. <span data-ttu-id="0df48-205">На новой вкладке браузера введите URL-адрес семейства веб-сайтов руководителей.</span><span class="sxs-lookup"><span data-stu-id="0df48-205">On a new tab of your browser, type the URL to the Executives site collection.</span></span>
    
2. <span data-ttu-id="0df48-206">Щелкните **Документы**.</span><span class="sxs-lookup"><span data-stu-id="0df48-206">Click **Documents**.</span></span>
    
3. <span data-ttu-id="0df48-207">Щелкните значок параметров в правом верхнем углу страницы и выберите **Параметры библиотеки**.</span><span class="sxs-lookup"><span data-stu-id="0df48-207">In the upper-right, click the settings icon, and then click **Library settings**.</span></span>
    
4. <span data-ttu-id="0df48-208">На странице **Параметры** в разделе **Разрешения и управление** щелкните **Управление правами на доступ к данным**.</span><span class="sxs-lookup"><span data-stu-id="0df48-208">On the **Settings** page, under **Permissions and Management**, click **Information Rights Management**.</span></span>
    
5. <span data-ttu-id="0df48-209">На странице **Параметры управления правами на доступ к данным**:</span><span class="sxs-lookup"><span data-stu-id="0df48-209">On the **Information Rights Management Settings** page:</span></span>
    
  - <span data-ttu-id="0df48-210">Выберите **Ограничить разрешения для документов этой библиотеки при скачивании**.</span><span class="sxs-lookup"><span data-stu-id="0df48-210">Select **Restrict permission to documents in this library on download**.</span></span>
    
  - <span data-ttu-id="0df48-211">В поле **Название политики разрешений** введите **Руководители**.</span><span class="sxs-lookup"><span data-stu-id="0df48-211">For **Create a permission policy title**, type **Executives**.</span></span>
    
  - <span data-ttu-id="0df48-212">В поле **Описание политики разрешений** введите **IRM для руководителей**.</span><span class="sxs-lookup"><span data-stu-id="0df48-212">For **Add a permission policy description**, type **IRM for executives**.</span></span>
    
6. <span data-ttu-id="0df48-213">Щелкните **Показать параметры**.</span><span class="sxs-lookup"><span data-stu-id="0df48-213">Click **Show Options**.</span></span>
    
7. <span data-ttu-id="0df48-214">В разделе **Установка дополнительных параметров IRM для библиотеки** выберите **Запретить пользователям отправлять документы, не поддерживающие управление правами на доступ к данным**.</span><span class="sxs-lookup"><span data-stu-id="0df48-214">Under **Set additional IRM library settings**, select **Do not allow users to upload documents that do not support IRM**.</span></span>
    
8. <span data-ttu-id="0df48-215">В разделе **Настройка прав доступа к документу** выберите **Разрешить наблюдателям печать** и **Разрешить наблюдателям выполнять запись в копии загруженного документа**.</span><span class="sxs-lookup"><span data-stu-id="0df48-215">Under **Configure document access rights**, select **Allow viewers to print** and **Allow viewers to write on a copy of the downloaded document**.</span></span>
    
9. <span data-ttu-id="0df48-216">В разделе **Настройка защиты группы и интервала для учетных данных** выберите **Разрешить защиту групп**, а в поле **Группа по умолчанию** введите **Руководители**.</span><span class="sxs-lookup"><span data-stu-id="0df48-216">Under **Set group protection and credentials interval**, select **Allow group protection** and for **Default group**, type **Executives**.</span></span>
    
10. <span data-ttu-id="0df48-217">Нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="0df48-217">Click **OK**.</span></span>
    
<span data-ttu-id="0df48-218">Затем отправьте новый документ в папку документов "Руководители" от имени генерального директора, скачайте его и ошибочно отправьте в папку документов "Продажи".</span><span class="sxs-lookup"><span data-stu-id="0df48-218">Next, acting as the CEO, you upload a new document to the Executives document folder, download it, then accidentally upload it to the Sales document folder.</span></span>
  
1. <span data-ttu-id="0df48-219">Откройте локальную папку, в которую вы сохранили документ **SensitiveData-BeforeIRM.docx**.</span><span class="sxs-lookup"><span data-stu-id="0df48-219">Open the local folder where you stored the **SensitiveData-BeforeIRM.docx** document.</span></span>
    
2. <span data-ttu-id="0df48-220">Щелкните правой кнопкой мыши **документ SensitiveData-beforeirm. docx**и выберите команду **Копировать**.</span><span class="sxs-lookup"><span data-stu-id="0df48-220">Right-click **SensitiveData-BeforeIRM.docx**, and then click **Copy**.</span></span>
    
3. <span data-ttu-id="0df48-221">Щелкните правой кнопкой мыши в папке и выберите **Вставить**.</span><span class="sxs-lookup"><span data-stu-id="0df48-221">Right-click within the folder, and then click **Paste**.</span></span>
    
4. <span data-ttu-id="0df48-222">Переименуйте новый файл **сенситиведата. BeforeIRM – Copy. docx** в **документ SensitiveData-afterirm. docx**.</span><span class="sxs-lookup"><span data-stu-id="0df48-222">Rename the new **SensitiveData-BeforeIRM - Copy.docx** file to **SensitiveData-AfterIRM.docx**.</span></span>
    
5. <span data-ttu-id="0df48-223">На главной вкладке \*\*Microsoft Office \*\* в браузере щелкните значок пользователя в правом верхнем углу и нажмите **Выйти**.</span><span class="sxs-lookup"><span data-stu-id="0df48-223">From the **Microsoft Office Home** tab in your browser, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
6. <span data-ttu-id="0df48-224">Перейдите по ссылке [http://admin.microsoft.com](http://admin.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="0df48-224">Go to [http://admin.microsoft.com](http://admin.microsoft.com).</span></span>
    
7. <span data-ttu-id="0df48-225">На странице **входа в Office 365** выберите имя учетной записи генерального директора, введите пароль и нажмите **Войти**.</span><span class="sxs-lookup"><span data-stu-id="0df48-225">On the **Office 365 sign in** page, click the CEO account name, type its password, and then click **Sign in**.</span></span>
    
8. <span data-ttu-id="0df48-226">На новой вкладке браузера введите URL-адрес семейства веб-сайтов руководителей.</span><span class="sxs-lookup"><span data-stu-id="0df48-226">On a new tab of your browser, type the URL to the Executives site collection.</span></span>
    
9. <span data-ttu-id="0df48-227">На странице **Документы** нажмите **Отправить**, выберите в локальной папке документ **SensitiveData-AfterIRM.docx** и нажмите **Открыть**.</span><span class="sxs-lookup"><span data-stu-id="0df48-227">On the **Documents** page, click **Upload**, specify the **SensitiveData-AfterIRM.docx** document in your local folder, and then click **Open**.</span></span>
    
10. <span data-ttu-id="0df48-228">Выберите новый документ **SensitiveData-AfterIRM.docx** на странице **Документы**, щелкните многоточие (…) в строке меню и нажмите **Скачать**.</span><span class="sxs-lookup"><span data-stu-id="0df48-228">Select the new **SensitiveData-AfterIRM.docx** document in the **Documents** page, click the ellipsis (…) in the menu bar, and then click **Download**.</span></span>
    
11. <span data-ttu-id="0df48-229">Сохраните документ **SensitiveData-AfterIRM.docx** в локальной папке, перезаписав его исходную версию.</span><span class="sxs-lookup"><span data-stu-id="0df48-229">When prompted, save the **SensitiveData-AfterIRM.docx** document in your local folder, overwriting the original version.</span></span>
    
12. <span data-ttu-id="0df48-230">Закройте вкладку **Документы**.</span><span class="sxs-lookup"><span data-stu-id="0df48-230">Close the tab for the **Documents** page.</span></span>
    
13. <span data-ttu-id="0df48-231">На новой вкладке браузера введите URL-адрес семейства веб-сайтов продаж.</span><span class="sxs-lookup"><span data-stu-id="0df48-231">On a new tab of your browser, type the URL to the Sales site collection.</span></span>
    
14. <span data-ttu-id="0df48-232">Щелкните **Документы**.</span><span class="sxs-lookup"><span data-stu-id="0df48-232">Click **Documents**.</span></span>
    
15. <span data-ttu-id="0df48-233">На странице **Документы** нажмите **Отправить**, выберите в локальной папке документ **SensitiveData-AfterIRM.docx** и нажмите **Открыть**.</span><span class="sxs-lookup"><span data-stu-id="0df48-233">On the **Documents** page, click **Upload**, specify the **SensitiveData-AfterIRM.docx** document in your local folder, and then click **Open**.</span></span>
    
16. <span data-ttu-id="0df48-234">Закройте вкладки **Семейство веб-сайтов "Продажи"** и **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="0df48-234">Close the **Sales site collection** and **SharePoint** tabs.</span></span>
    
<span data-ttu-id="0df48-235">Затем попробуйте открыть документ **SensitiveData-AfterIRM.docx** в папке документов "Продажи" от имени обычного пользователя.</span><span class="sxs-lookup"><span data-stu-id="0df48-235">Next, acting as a normal user, you try to access the **SensitiveData-AfterIRM.docx** document in the Sales document folder.</span></span>
  
1. <span data-ttu-id="0df48-236">На главной вкладке \*\*Microsoft Office \*\* в браузере щелкните значок пользователя в правом верхнем углу и нажмите **Выйти**.</span><span class="sxs-lookup"><span data-stu-id="0df48-236">From the **Microsoft Office Home** tab in your browser, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="0df48-237">Перейдите по ссылке [http://admin.microsoft.com](http://admin.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="0df48-237">Go to [http://admin.microsoft.com](http://admin.microsoft.com).</span></span>
    
3. <span data-ttu-id="0df48-238">На странице **входа в Office 365** щелкните имя учетной записи User5, введите пароль, а затем нажмите кнопку **войти**.</span><span class="sxs-lookup"><span data-stu-id="0df48-238">On the **Office 365 sign in** page, click the User5 account name, type its password, and then click **Sign in**.</span></span>
    
4. <span data-ttu-id="0df48-239">На новой вкладке браузера введите URL-адрес семейства веб-сайтов продаж.</span><span class="sxs-lookup"><span data-stu-id="0df48-239">On a new tab of your browser, type the URL to the Sales site collection.</span></span>
    
5. <span data-ttu-id="0df48-240">Щелкните **Документы**.</span><span class="sxs-lookup"><span data-stu-id="0df48-240">Click **Documents**.</span></span>
    
6. <span data-ttu-id="0df48-241">На странице **Документы** откройте документ **SensitiveData-AfterIRM.docx**. </span><span class="sxs-lookup"><span data-stu-id="0df48-241">On the **Documents** page, open the **SensitiveData-AfterIRM.docx** document.</span></span>
    
    <span data-ttu-id="0df48-242">Появится сообщение "К сожалению, Word Online не может открыть этот документ, так как он защищен службой управления правами на доступ к данным (IRM)." </span><span class="sxs-lookup"><span data-stu-id="0df48-242">You should see a message that states "Sorry, Word Online can't open this document because it's protected by Information Rights Management (IRM)."</span></span> 
    
7. <span data-ttu-id="0df48-p105">Выберите **Редактировать в Word**. Вам будет предложено открыть файл. Нажмите **Да**.</span><span class="sxs-lookup"><span data-stu-id="0df48-p105">Click **Edit in Word**. You are prompted if you want to open the file. Click **Yes**.</span></span>
    
8. <span data-ttu-id="0df48-p106">Вам будет предложено войти. Введите имя учетной записи User5 и нажмите **Далее**.</span><span class="sxs-lookup"><span data-stu-id="0df48-p106">You are prompted to sign-in. Type the account name of the User5 account, and then click **Next**.</span></span>
    
9. <span data-ttu-id="0df48-p107">Вам будет предложено ввести пароль. Введите пароль учетной записи User5 и нажмите **Войти**. </span><span class="sxs-lookup"><span data-stu-id="0df48-p107">You are prompted to provide the password. Type the password for the User5 account and then click **Sign in**.</span></span> 
    
    <span data-ttu-id="0df48-250">Появится такое сообщение: "Ваши учетные данные не позволяют вам открыть этот документ."</span><span class="sxs-lookup"><span data-stu-id="0df48-250">You should see the a message that states: "You do not have the credentials that allow you to open this document."</span></span>
    
10. <span data-ttu-id="0df48-251">Нажмите **Нет**.</span><span class="sxs-lookup"><span data-stu-id="0df48-251">Click **No**.</span></span>
    
<span data-ttu-id="0df48-p108">Еще один способ проверить защиту IRM — просмотреть файлы в локальной папке. Файл **SensitiveData-AfterIRM.docx** должен быть значительно больше, чем **SensitiveData-BeforeIRM.docx**. Файл **SensitiveData-AfterIRM.docx** зашифрован, и к нему добавлена информация о защите IRM.</span><span class="sxs-lookup"><span data-stu-id="0df48-p108">Another way to see the IRM protection is to look at the files in your local folder. The **SensitiveData-AfterIRM.docx** should be much larger than the **SensitiveData-BeforeIRM.docx** file. The **SensitiveData-AfterIRM.docx** file is encrypted and has the IRM protection information added to it.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="0df48-255">См. также</span><span class="sxs-lookup"><span data-stu-id="0df48-255">See Also</span></span>

[<span data-ttu-id="0df48-256">Руководства по лабораториям тестирования (TLG) для принятия облачных решений</span><span class="sxs-lookup"><span data-stu-id="0df48-256">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="0df48-257">Базовая конфигурация среды разработки и тестирования</span><span class="sxs-lookup"><span data-stu-id="0df48-257">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="0df48-258">Среда разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="0df48-258">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="0df48-259">Освоение облака и гибридные решения</span><span class="sxs-lookup"><span data-stu-id="0df48-259">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)


