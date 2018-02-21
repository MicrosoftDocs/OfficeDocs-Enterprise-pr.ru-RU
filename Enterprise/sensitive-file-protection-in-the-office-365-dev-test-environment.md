---
title: "Защита конфиденциальных файлов в среде разработки и тестирования Office 365"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: 27ecff45-06a6-4629-bc45-9dab4eef3a21
description: "Сводка: Настройка и демонстрация Office 365 Information Rights Management защите конфиденциальных файлов, даже если они учтены неверный семейства сайтов SharePoint Online."
ms.openlocfilehash: 236272a90bb6ff7f310c95f1494b68750e363f40
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2018
---
# <a name="sensitive-file-protection-in-the-office-365-devtest-environment"></a><span data-ttu-id="6561a-103">Защита конфиденциальных файлов в среде разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="6561a-103">Sensitive file protection in the Office 365 dev/test environment</span></span>

 <span data-ttu-id="6561a-104">**Сводка:** Настройка и демонстрация Office 365 Information Rights Management защите конфиденциальных файлов, даже если они учтены неверный семейства сайтов SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="6561a-104">**Summary:** Configure and demonstrate how Office 365 Information Rights Management protects your sensitive files, even when they are posted to the wrong SharePoint Online site collection.</span></span>
  
<span data-ttu-id="6561a-p101">Управление правами на доступ к данным (IRM) в Office 365 — это набор функций для защиты документов, скачиваемых из списков и библиотек SharePoint Online. Скачиваемые файлы зашифрованы и содержат те же разрешения на открытие, копирование, сохранение и печать, которые настроены в библиотеке SharePoint Online, в которой они хранились.</span><span class="sxs-lookup"><span data-stu-id="6561a-p101">Information Rights Management (IRM) in Office 365 is a set of capabilities to protect documents that are downloaded from SharePoint Online libraries and lists. Downloaded files are encrypted and contain the open, copy, save, and print permissions that reflect the SharePoint Online library in which they were stored.</span></span>
  
<span data-ttu-id="6561a-107">В этой статье описано, как включить и протестировать IRM в Office 365 для файлов, содержащих потенциально конфиденциальную информацию, в пробной подписке на Office 365.</span><span class="sxs-lookup"><span data-stu-id="6561a-107">With the instructions in this article, you enable and test IRM in Office 365 for files containing possible sensitive information in your Office 365 trial subscription.</span></span>
  
> [!TIP]
> <span data-ttu-id="6561a-108">Щелкните [здесь](http://aka.ms/catlgstack), чтобы просмотреть схему всех статей, относящихся к руководствам по лаборатории тестирования Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="6561a-108">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-office-365-devtest-environment"></a><span data-ttu-id="6561a-109">Этап 1. Создание среды разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="6561a-109">Phase 1: Build out your Office 365 dev/test environment</span></span>

<span data-ttu-id="6561a-110">Если необходимо проверить защита конфиденциальных файлов в облегченный путь с минимальным требованиям, следуйте инструкциям в этапы 2 и 3 [Office 365 dev/тестовой среды](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="6561a-110">If you just want to test sensitive file protection in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="6561a-111">Если вы хотите проверить защита конфиденциальных файлов в имитации enterprise, следуйте инструкциям в [DirSync для вашей среды разработки или тестирования Office 365](dirsync-for-your-office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="6561a-111">If you want to test sensitive file protection in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="6561a-p102">Для тестирования не требуется условная корпоративная среда разработки и тестирования, которая включает условную интрасеть, подключенную к Интернету, и синхронизацию каталогов для леса Windows Server AD. Она показана здесь лишь для того, чтобы вы могли протестировать защиту конфиденциальных файлов и поэкспериментировать с этим компонентом в типичной для организаций среде.</span><span class="sxs-lookup"><span data-stu-id="6561a-p102">Testing sensitive file protection does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest. It is provided here as an option so that you can test sensitive file protection and experiment with it in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-demonstrate-how-documents-from-permissions-protected-sites-can-be-leaked"></a><span data-ttu-id="6561a-114">Этап 2. Демонстрация утечки документов с сайтов, защищенных системой прав доступа</span><span class="sxs-lookup"><span data-stu-id="6561a-114">Phase 2: Demonstrate how documents from permissions-protected sites can be leaked</span></span>

<span data-ttu-id="6561a-115">На этом этапе демонстрируется, что пользователь может скачать документ с сайта, защищенного системой прав доступа, а затем отправить его на незащищенный сайт.</span><span class="sxs-lookup"><span data-stu-id="6561a-115">In this phase, you demonstrate that someone can download a document from a permissions-protected site and then upload it to a site that has wide-open permissions.</span></span>
  
<span data-ttu-id="6561a-116">Для начала создайте три новых учетных записи пользователя для руководителей и назначьте им лицензии Office 365 E5.</span><span class="sxs-lookup"><span data-stu-id="6561a-116">First, you add three new user accounts that represent executives and assign them Office 365 E5 licenses.</span></span>
  
<span data-ttu-id="6561a-117">Используйте инструкции из статьи Установка PowerShell модули (при необходимости) и подключиться к новой подписки Office 365 через [подключение к Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx) :</span><span class="sxs-lookup"><span data-stu-id="6561a-117">Use the instructions in [Connect to Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx) to install the PowerShell modules (if needed) and connect to your new Office 365 subscription from:</span></span>
  
- <span data-ttu-id="6561a-118">компьютера (для упрощенной среды разработки и тестирования Office 365);</span><span class="sxs-lookup"><span data-stu-id="6561a-118">Your computer (for the lightweight Office 365 dev/test environment).</span></span>
    
- <span data-ttu-id="6561a-119">виртуальной машины CLIENT1 (для среды Office 365 для разработки и тестирования смоделированного предприятия).</span><span class="sxs-lookup"><span data-stu-id="6561a-119">The CLIENT1 virtual machine (for the simulated enterprise Office 365 dev/test environment).</span></span>
    
<span data-ttu-id="6561a-120">В диалоговом окне **Запрос учетных данных Windows PowerShell** введите имя глобального администратора Office 365 (пример: jdoe@contosotoycompany.onmicrosoft.com) и пароль для пробной подписки Office 365.</span><span class="sxs-lookup"><span data-stu-id="6561a-120">In the **Windows PowerShell Credential Request** dialog box, type the Office 365 global administrator name (example: jdoe@contosotoycompany.onmicrosoft.com) and password of your Office 365 trial subscription.</span></span>
  
<span data-ttu-id="6561a-121">Введите название организации (например, contosotoycompany) и двузначный код страны, а затем выполните следующие команды в командной строке модуля Windows Azure Active Directory для Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="6561a-121">Fill in your organization name (example: contosotoycompany) and the two-character country code for your location, and then run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$licAssignment= $orgName + ":ENTERPRISEPREMIUM"
$userName= "ceo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "CEO" -FirstName "Chief" -LastName "Executive Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

<span data-ttu-id="6561a-122">Отображение команду **New-MsolUser** Обратите внимание, созданный пароль для учетной записи генеральный Директор и запишите его в надежном месте.</span><span class="sxs-lookup"><span data-stu-id="6561a-122">From the display of the **New-MsolUser** command, note the generated password for the CEO account and record it in a safe location.</span></span>
  
<span data-ttu-id="6561a-123">Выполните следующие команды в командной строке модуля Windows Azure Active Directory для Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="6561a-123">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "cfo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "CFO" -FirstName "Chief" -LastName "Financial Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

<span data-ttu-id="6561a-124">Отображение команду **New-MsolUser** Обратите внимание, созданный пароль для учетной записи финансового Директора и запишите его в надежном месте.</span><span class="sxs-lookup"><span data-stu-id="6561a-124">From the display of the **New-MsolUser** command, note the generated password for the CFO account and record it in a safe location.</span></span>
  
<span data-ttu-id="6561a-125">Выполните следующие команды в командной строке модуля Windows Azure Active Directory для Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="6561a-125">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "coo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "COO" -FirstName "Chief" -LastName "Operations Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

<span data-ttu-id="6561a-126">Отображение команду **New-MsolUser** Обратите внимание, созданный пароль для учетной записи работе исполнительного Директора и запишите его в надежном месте.</span><span class="sxs-lookup"><span data-stu-id="6561a-126">From the display of the **New-MsolUser** command, note the generated password for the COO account and record it in a safe location.</span></span>
  
<span data-ttu-id="6561a-127">Теперь создайте закрытую группу "Руководители" и добавьте в нее новые учетные записи.</span><span class="sxs-lookup"><span data-stu-id="6561a-127">Next, you create a private Executives group and add the new executive accounts to it.</span></span>
  
1. <span data-ttu-id="6561a-128">В браузере перейдите на портале Office по [http://portal.office.com](http://portal.office.com) и войдите пробной подписки Office 365 с учетной записью глобального администратора.</span><span class="sxs-lookup"><span data-stu-id="6561a-128">In your browser, go to the Office portal at [http://portal.office.com](http://portal.office.com) and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
  - <span data-ttu-id="6561a-129">Если вы используете упрощенную среду разработки и тестирования Office 365, запустите частный сеанс Internet Explorer или вашего браузера и войдите с локального компьютера.</span><span class="sxs-lookup"><span data-stu-id="6561a-129">If you are using the lightweight Office 365 dev/test environment, open a private session of Internet Explorer or your browser and sign in from your local computer.</span></span>
    
  - <span data-ttu-id="6561a-130">Если вы используете условную корпоративную среду разработки и тестирования Office 365, подключитесь к виртуальной машине CLIENT1 с помощью портала Azure, а затем войдите с этой виртуальной машины.</span><span class="sxs-lookup"><span data-stu-id="6561a-130">If you are using the simulated enterprise Office 365 dev/test environment, use the Azure portal to connect to the CLIENT1 virtual machine, and then sign in from CLIENT1.</span></span>
    
2. <span data-ttu-id="6561a-131">На вкладке **Microsoft Office для дома** щелкните **администрирования > группы > группы**и нажмите кнопку **Добавить группу**.</span><span class="sxs-lookup"><span data-stu-id="6561a-131">On the **Microsoft Office Home** tab, click **Admin > Groups > Groups**, and then click **Add a group**.</span></span>
    
3. <span data-ttu-id="6561a-132">В диалоговом окне **Добавить группу**выберите **группу, Office 365** для типа группы, введите в поле **имя** и **Идентификатор группы**, **руководителями** выберите **частный** для **обеспечения конфиденциальности**и нажмите кнопку **Выберите владельца**.</span><span class="sxs-lookup"><span data-stu-id="6561a-132">In **Add a group**, select **Office 365 group** for the group type, type **Executives** in **Name** and **Group Id**, select **Private** for **Privacy**, and then click **Select Owner**.</span></span>
    
4. <span data-ttu-id="6561a-133">Выберите имя учетной записи глобального администратора из списка.</span><span class="sxs-lookup"><span data-stu-id="6561a-133">In the list, click your global administrator account name.</span></span>
    
5. <span data-ttu-id="6561a-134">Нажмите кнопку **Добавить**и нажмите кнопку **Закрыть**.</span><span class="sxs-lookup"><span data-stu-id="6561a-134">Click **Add**, and then click **Close**.</span></span>
    
6. <span data-ttu-id="6561a-135">В списке группы выберите **руководителей**.</span><span class="sxs-lookup"><span data-stu-id="6561a-135">In the groups list, click **Executives**.</span></span>
    
7. <span data-ttu-id="6561a-136">Нажмите кнопку **изменить для членов**.</span><span class="sxs-lookup"><span data-stu-id="6561a-136">Click **Edit for Members**.</span></span>
    
8. <span data-ttu-id="6561a-p103">Нажмите кнопку **Добавить элементы**. В списке элементов выберите следующие учетные записи пользователей:</span><span class="sxs-lookup"><span data-stu-id="6561a-p103">Click **Add members**. In the member list, select the following user accounts:</span></span>
    
  - <span data-ttu-id="6561a-139">генеральный директор;</span><span class="sxs-lookup"><span data-stu-id="6561a-139">Chief Executive Officer</span></span>
    
  - <span data-ttu-id="6561a-140">финансовый директор;</span><span class="sxs-lookup"><span data-stu-id="6561a-140">Chief Financial Officer</span></span>
    
  - <span data-ttu-id="6561a-141">главный операционный директор.</span><span class="sxs-lookup"><span data-stu-id="6561a-141">Chief Operations Officer</span></span>
    
9. <span data-ttu-id="6561a-142">Нажмите кнопку **Сохранить**и нажмите кнопку **Закрыть**.</span><span class="sxs-lookup"><span data-stu-id="6561a-142">Click **Save**, and then click **Close**.</span></span>
    
10. <span data-ttu-id="6561a-143">Закройте вкладку **Центр администрирования Office** .</span><span class="sxs-lookup"><span data-stu-id="6561a-143">Close the **Office Admin center** tab.</span></span>
    
<span data-ttu-id="6561a-144">Теперь создайте семейство веб-сайтов "Руководители" и предоставьте к нему доступ только участникам этой группы.</span><span class="sxs-lookup"><span data-stu-id="6561a-144">Next, you create an Executives site collection and allow just the members of the Executives group to access it.</span></span>
  
1. <span data-ttu-id="6561a-145">На вкладке **Microsoft Office для дома** щелкните плитку **администрирования** .</span><span class="sxs-lookup"><span data-stu-id="6561a-145">On the **Microsoft Office Home** tab, click the **Admin** tile.</span></span>
    
2. <span data-ttu-id="6561a-146">На вкладке **центра администрирования Office** щелкните **центры администрирования > SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="6561a-146">On the **Office Admin center** tab, click **Admin centers > SharePoint**.</span></span>
    
3. <span data-ttu-id="6561a-147">На вкладке **Центр администрирования SharePoint** щелкните **Создать > закрытый семейства**.</span><span class="sxs-lookup"><span data-stu-id="6561a-147">On the **SharePoint admin center** tab, click **New > Private site collection**.</span></span>
    
4. <span data-ttu-id="6561a-148">В области семейства сайтов введите **руководителей** в поле **Название**руководителей в поле URL-адреса укажите имя учетной записи глобального администратора в **администратора**и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="6561a-148">In the new site collection pane, type **Executives** in **Title**, executives in the URL box, specify the name of your global administrator account in **Administrator**, and then click **OK**.</span></span>
    
5. <span data-ttu-id="6561a-p104">Подождите, пока создания нового семейства сайтов. Закончив настройку, скопируйте URL-адрес нового семейства сайтов для руководителей и вставьте его в новую вкладку браузера.</span><span class="sxs-lookup"><span data-stu-id="6561a-p104">Wait until the new site collection has been created. When complete, copy the URL of the new Executives site collection and paste it into a new tab of your browser.</span></span>
    
6. <span data-ttu-id="6561a-151">В правом верхнем углу **руководители** семейства веб-сайтов щелкните значок параметры и выберите **общий доступ**.</span><span class="sxs-lookup"><span data-stu-id="6561a-151">In the upper right of the **Executives** site collection, click the settings icon, and then click **Shared with**.</span></span>
    
7. <span data-ttu-id="6561a-152">В **папке «Руководители»**нажмите кнопку **Дополнительно**.</span><span class="sxs-lookup"><span data-stu-id="6561a-152">In **Share 'Executives'**, click **Advanced**.</span></span>
    
8. <span data-ttu-id="6561a-153">В список групп SharePoint щелкните **Элементы руководителей**.</span><span class="sxs-lookup"><span data-stu-id="6561a-153">In the list of SharePoint groups, click **Executives Members**.</span></span>
    
9. <span data-ttu-id="6561a-154">На странице **Пользователи и группы** нажмите кнопку **Создать**.</span><span class="sxs-lookup"><span data-stu-id="6561a-154">On the **People and Groups** page, click **New**.</span></span>
    
10. <span data-ttu-id="6561a-155">В поле **общий доступ «Руководители»**введите **руководители**, щелкните группу, **руководители** и нажмите кнопку **совместный доступ**.</span><span class="sxs-lookup"><span data-stu-id="6561a-155">In **Share 'Executives'**, type **Executives**, click the **Executives** group, and then click **Share**.</span></span>
    
11. <span data-ttu-id="6561a-156">Закройте вкладку **пользователи и группы** .</span><span class="sxs-lookup"><span data-stu-id="6561a-156">Close the **People and groups** tab.</span></span>
    
<span data-ttu-id="6561a-157">Теперь предоставьте всем пользователям доступ к семейству веб-сайтов "Продажи".</span><span class="sxs-lookup"><span data-stu-id="6561a-157">Next, you allow everyone to access the Sales site collection.</span></span>
  
1. <span data-ttu-id="6561a-158">Откройте вкладку **Центр администрирования SharePoint** и скопируйте URL-адрес семейства сайтов, продажи и вставьте его в новую вкладку браузера...</span><span class="sxs-lookup"><span data-stu-id="6561a-158">From the **SharePoint admin center** tab, copy the URL of the Sales site collection and paste it into a new tab of your browser..</span></span>
    
2. <span data-ttu-id="6561a-159">В правом верхнем углу щелкните значок параметры и выберите **общий доступ**.</span><span class="sxs-lookup"><span data-stu-id="6561a-159">In the upper right, click the settings icon, and then click **Shared with**.</span></span>
    
3. <span data-ttu-id="6561a-160">В поле **общий доступ «Продажи семейства веб-сайтов»**нажмите кнопку **Дополнительно**.</span><span class="sxs-lookup"><span data-stu-id="6561a-160">In **Share 'Sales site collection'**, click **Advanced**.</span></span>
    
4. <span data-ttu-id="6561a-161">В списке групп SharePoint нажмите кнопку **члены семейства веб-сайтов продаж**.</span><span class="sxs-lookup"><span data-stu-id="6561a-161">In the list of SharePoint groups, click **Sales site collection Members**.</span></span>
    
5. <span data-ttu-id="6561a-162">На странице **Пользователи и группы** нажмите кнопку **Создать**.</span><span class="sxs-lookup"><span data-stu-id="6561a-162">On the **People and Groups** page, click **New**.</span></span>
    
6. <span data-ttu-id="6561a-163">В **папке «Продажи семейства веб-сайтов»**введите **все**, щелкните **все, кроме внешних пользователей**и нажмите кнопку **общий доступ**.</span><span class="sxs-lookup"><span data-stu-id="6561a-163">In **Share 'Sales site collection'**, type **Everyone**, click **Everyone except external users**, and then click **Share**.</span></span>
    
7. <span data-ttu-id="6561a-164">Закройте вкладки **продаж семейства сайтов** и **SharePoint** .</span><span class="sxs-lookup"><span data-stu-id="6561a-164">Close the **Sales site collection** and **SharePoint** tabs.</span></span>
    
<span data-ttu-id="6561a-165">Затем войдите в учетную запись руководителя и создайте документ в семействе веб-сайтов "Руководители".</span><span class="sxs-lookup"><span data-stu-id="6561a-165">Next, you sign in with an executive account and create a document in the Executives site collection.</span></span>
  
1. <span data-ttu-id="6561a-166">На вкладке **Microsoft Office для дома** щелкните значок пользователя в правом верхнем углу и выберите команду **Выход**.</span><span class="sxs-lookup"><span data-stu-id="6561a-166">On the **Microsoft Office Home** tab, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="6561a-167">Перейдите к [http://portal.office.com](http://portal.office.com).</span><span class="sxs-lookup"><span data-stu-id="6561a-167">Go to [http://portal.office.com](http://portal.office.com).</span></span>
    
3. <span data-ttu-id="6561a-168">На странице **входа Office 365** выберите **использовать другую учетную запись**.</span><span class="sxs-lookup"><span data-stu-id="6561a-168">On the **Office 365 sign in** page, click **Use another account**.</span></span>
    
4. <span data-ttu-id="6561a-169">Введите имя **CEO** учетной записи и пароль и нажмите кнопку **Вход**.</span><span class="sxs-lookup"><span data-stu-id="6561a-169">Type the **CEO** account name and its password, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="6561a-170">На новой вкладке браузера введите URL-адрес семейства веб-сайтов руководителей ( **https://**\<название организации >**.sharepoint.com/sites/executives**).</span><span class="sxs-lookup"><span data-stu-id="6561a-170">On a new tab of your browser, type the URL to the Executives site collection ( **https://**\<organization name>**.sharepoint.com/sites/executives**).</span></span>
    
6. <span data-ttu-id="6561a-171">Щелкните **документы**, нажмите кнопку **Создать** и выберите **Документ Word**.</span><span class="sxs-lookup"><span data-stu-id="6561a-171">Click **Documents**, click **New,** and then click **Word Document**.</span></span>
    
7. <span data-ttu-id="6561a-172">Щелкните в строке заголовка и введите **SensitiveData BeforeIRM**.</span><span class="sxs-lookup"><span data-stu-id="6561a-172">Click in the title bar and type **SensitiveData-BeforeIRM**.</span></span>
    
8. <span data-ttu-id="6561a-173">Щелкните в теле документа и введите **минут из последних доска собрания**и нажмите кнопку **руководителей**.</span><span class="sxs-lookup"><span data-stu-id="6561a-173">Click in the document body and type **Minutes from the latest board meeting**, and then click **Executives**.</span></span>
    
     <span data-ttu-id="6561a-174">Вы должны увидеть **SensitiveData BeforeIRM.docx** в папку « **документы** ».</span><span class="sxs-lookup"><span data-stu-id="6561a-174">You should see **SensitiveData-BeforeIRM.docx** in the **Documents** folder.</span></span>
    
<span data-ttu-id="6561a-175">Теперь скачайте локальную копию документа SensitiveData-BeforeIRM.docx и случайно опубликуйте ее в семействе веб-сайтов "Продажи".</span><span class="sxs-lookup"><span data-stu-id="6561a-175">Next, you download a local copy of the SensitiveData-BeforeIRM.docx document and then accidentally post it to the Sales site collection.</span></span>
  
1. <span data-ttu-id="6561a-176">На локальном компьютере, создать новую папку (например, C:\\руководствам\\SensitiveDataTestFiles).</span><span class="sxs-lookup"><span data-stu-id="6561a-176">On your local computer, create a new folder (for example, C:\\TLGs\\SensitiveDataTestFiles).</span></span>
    
2. <span data-ttu-id="6561a-177">На вкладке **документы** в браузере выберите **SensitiveData BeforeIRM.docx** документ, нажмите кнопку с многоточием и нажмите кнопку **загрузить**.</span><span class="sxs-lookup"><span data-stu-id="6561a-177">On the **Documents** tab of your browser, select the **SensitiveData-BeforeIRM.docx** document, click the ellipses, and then click **Download**.</span></span>
    
3. <span data-ttu-id="6561a-178">Хранение документов **SensitiveData BeforeIRM.docx** в папке, созданной на шаге 1.</span><span class="sxs-lookup"><span data-stu-id="6561a-178">Store the **SensitiveData-BeforeIRM.docx** document in the folder created in step 1.</span></span>
    
4. <span data-ttu-id="6561a-179">На новой вкладке браузера введите URL-адрес семейства веб-сайтов продаж ( **https://**\<название организации >**.sharepoint.com/sites/sales**).</span><span class="sxs-lookup"><span data-stu-id="6561a-179">On a new tab of your browser, type the URL to the Sales site collection ( **https://**\<organization name>**.sharepoint.com/sites/sales**).</span></span>
    
5. <span data-ttu-id="6561a-180">Щелкните папку « **документы** » из **семейства сайтов продаж**.</span><span class="sxs-lookup"><span data-stu-id="6561a-180">Click the **Documents** folder of the **Sales site collection**.</span></span>
    
6. <span data-ttu-id="6561a-181">Нажмите кнопку **Отправить**и затем укажите **SensitiveData BeforeIRM.docx** документа в папке, созданной на шаге 1 и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="6561a-181">Click **Upload**, and then specify **SensitiveData-BeforeIRM.docx** document in the folder created in step 1, and then click **OK**.</span></span>
    
7. <span data-ttu-id="6561a-182">Убедитесь, что документ **SensitiveData BeforeIRM.docx** в папку « **документы** ».</span><span class="sxs-lookup"><span data-stu-id="6561a-182">Verify that the **SensitiveData-BeforeIRM.docx** document is in the **Documents** folder.</span></span>
    
8. <span data-ttu-id="6561a-183">Закройте вкладки **продажи** и **SharePoint** .</span><span class="sxs-lookup"><span data-stu-id="6561a-183">Close the **Sales** and **SharePoint** tabs.</span></span>
    
<span data-ttu-id="6561a-184">После этого войдите в учетную запись User5 и откройте документ SensitiveData-BeforeIRM.docx в семействе веб-сайтов "Продажи".</span><span class="sxs-lookup"><span data-stu-id="6561a-184">Next, you sign in as User5 and try to open the SensitiveData-BeforeIRM.docx document in the Sales site collection.</span></span>
  
1. <span data-ttu-id="6561a-185">На вкладке **Microsoft Office для дома** щелкните значок пользователя в правом верхнем углу и выберите команду **Выход**.</span><span class="sxs-lookup"><span data-stu-id="6561a-185">On the **Microsoft Office Home** tab, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="6561a-186">Перейдите к [http://portal.office.com](http://portal.office.com).</span><span class="sxs-lookup"><span data-stu-id="6561a-186">Go to [http://portal.office.com](http://portal.office.com).</span></span>
    
3. <span data-ttu-id="6561a-187">На странице **входа Office 365** выберите **использовать другую учетную запись**.</span><span class="sxs-lookup"><span data-stu-id="6561a-187">On the **Office 365 sign in** page, click **Use another account**.</span></span>
    
4. <span data-ttu-id="6561a-188">Введите имя учетной записи User5 и пароль и нажмите кнопку **Вход**.</span><span class="sxs-lookup"><span data-stu-id="6561a-188">Type the User5 account name and its password, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="6561a-189">На новой вкладке браузера введите URL-адрес семейства веб-сайтов продаж.</span><span class="sxs-lookup"><span data-stu-id="6561a-189">On a new tab of your browser, type the URL to the Sales site collection.</span></span>
    
6. <span data-ttu-id="6561a-190">В папке **документы** **продажи семейство сайтов**нажмите кнопку **SensitiveData BeforeIRM.docx** документа.</span><span class="sxs-lookup"><span data-stu-id="6561a-190">In the **Documents** folder of the **Sales site collection**, click the **SensitiveData-BeforeIRM.docx** document.</span></span>
    
    <span data-ttu-id="6561a-191">Появится его содержимое.</span><span class="sxs-lookup"><span data-stu-id="6561a-191">You should see its contents.</span></span>
    
7. <span data-ttu-id="6561a-192">Закройте вкладки **документов** и **продажи семейства сайтов** .</span><span class="sxs-lookup"><span data-stu-id="6561a-192">Close the **Documents** and **Sales site collection** tabs.</span></span>
    
<span data-ttu-id="6561a-193">Случайно опубликовав документ SensitiveData-BeforeIRM.docx в семействе веб-сайтов "Продажи", генеральный директор обошел систему прав доступа семейства веб-сайтов "Руководители".</span><span class="sxs-lookup"><span data-stu-id="6561a-193">By accidentally posting the SensitiveData-BeforeIRM.docx document on the Sales site collection, the CEO bypassed the permissions security of the Executives site collection.</span></span>
  
<span data-ttu-id="6561a-194">Чтобы подготовить Office 365 к этапам 3 и 4, включите IRM для SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="6561a-194">To prepare Office 365 for Phases 3 and 4, enable IRM for SharePoint Online.</span></span>
  
1. <span data-ttu-id="6561a-195">На вкладке **Microsoft Office для дома** щелкните значок пользователя в правом верхнем углу и выберите команду **Выход**.</span><span class="sxs-lookup"><span data-stu-id="6561a-195">On the **Microsoft Office Home** tab, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="6561a-196">Перейдите к [http://portal.office.com](http://portal.office.com).</span><span class="sxs-lookup"><span data-stu-id="6561a-196">Go to [http://portal.office.com](http://portal.office.com).</span></span>
    
3. <span data-ttu-id="6561a-197">На странице **входа Office 365** щелкните имя учетной записи глобального администратора, введите пароль и затем нажмите кнопку **Вход**.</span><span class="sxs-lookup"><span data-stu-id="6561a-197">On the **Office 365 sign in** page, click the global administrator account name, type its password, and then click **Sign in**.</span></span>
    
4. <span data-ttu-id="6561a-198">На вкладке **Microsoft Office для дома** щелкните **администрирования > центры администрирования > SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="6561a-198">On the **Microsoft Office Home** tab, click **Admin > Admin centers > SharePoint**.</span></span>
    
5. <span data-ttu-id="6561a-199">На вкладке **Центр администрирования SharePoint** щелкните **Параметры**.</span><span class="sxs-lookup"><span data-stu-id="6561a-199">On the **SharePoint admin center** tab, click **Settings**.</span></span>
    
6. <span data-ttu-id="6561a-200">На странице " **Параметры** " в разделе **Управление правами на доступ к данным (IRM)** выберите **с помощью службы IRM, указанного в конфигурации**и выберите пункт **Обновить параметры IRM**.</span><span class="sxs-lookup"><span data-stu-id="6561a-200">On the **Settings** page, in the **Information Rights Management (IRM)** section, select **Use the IRM service specified in your configuration**, and then select **Refresh IRM Settings**.</span></span>
    
7. <span data-ttu-id="6561a-201">Закройте вкладку **Центр администрирования SharePoint** .</span><span class="sxs-lookup"><span data-stu-id="6561a-201">Close the **SharePoint admin center** tab.</span></span>
    
## <a name="phase-3-use-sharepoint-information-rights-management-with-an-office-365-private-group"></a><span data-ttu-id="6561a-202">Этап 3. Использование управления правами на доступ к данным SharePoint с закрытой группой Office 365</span><span class="sxs-lookup"><span data-stu-id="6561a-202">Phase 3: Use SharePoint Information Rights Management with an Office 365 private group</span></span>

<span data-ttu-id="6561a-203">На этом этапе используется управление правами на доступ к данным SharePoint с закрытой группой Office 365, чтобы защитить документ с конфиденциальной информацией, даже если он опубликован на сайте с открытым доступом.</span><span class="sxs-lookup"><span data-stu-id="6561a-203">In this phase, you use SharePoint Information Rights Management with an Office 365 private group to protect access to a document with sensitive information, even when it is posted on a site with open permissions.</span></span>
  
<span data-ttu-id="6561a-204">Для начала включите и настройте IRM для библиотеки документов семейства веб-сайтов "Руководители". </span><span class="sxs-lookup"><span data-stu-id="6561a-204">First, you enable and configure IRM for the documents library of the Executives site collection.</span></span> 
  
1. <span data-ttu-id="6561a-205">На новой вкладке браузера введите URL-адрес для руководителей семейства веб-сайтов.</span><span class="sxs-lookup"><span data-stu-id="6561a-205">On a new tab of your browser, type the URL to the Executives site collection.</span></span>
    
2. <span data-ttu-id="6561a-206">Щелкните **документы**.</span><span class="sxs-lookup"><span data-stu-id="6561a-206">Click **Documents**.</span></span>
    
3. <span data-ttu-id="6561a-207">В правом верхнем углу щелкните значок параметры и нажмите кнопку **Параметры библиотеки**.</span><span class="sxs-lookup"><span data-stu-id="6561a-207">In the upper-right, click the settings icon, and then click **Library settings**.</span></span>
    
4. <span data-ttu-id="6561a-208">На странице " **Параметры** " в разделе **разрешения и управление**, щелкните **Управление правами на доступ**.</span><span class="sxs-lookup"><span data-stu-id="6561a-208">On the **Settings** page, under **Permissions and Management**, click **Information Rights Management**.</span></span>
    
5. <span data-ttu-id="6561a-209">На странице **Параметры управления правами сведениями** :</span><span class="sxs-lookup"><span data-stu-id="6561a-209">On the **Information Rights Management Settings** page:</span></span>
    
  - <span data-ttu-id="6561a-210">Выберите **ограничить разрешения для документов этой библиотеки при загрузке**.</span><span class="sxs-lookup"><span data-stu-id="6561a-210">Select **Restrict permission to documents in this library on download**.</span></span>
    
  - <span data-ttu-id="6561a-211">Для **создания название политики разрешений**введите **руководителей**.</span><span class="sxs-lookup"><span data-stu-id="6561a-211">For **Create a permission policy title**, type **Executives**.</span></span>
    
  - <span data-ttu-id="6561a-212">В поле **Добавить описание политики разрешений**, введите **IRM для руководителей**.</span><span class="sxs-lookup"><span data-stu-id="6561a-212">For **Add a permission policy description**, type **IRM for executives**.</span></span>
    
6. <span data-ttu-id="6561a-213">Щелкните **Показать параметры**.</span><span class="sxs-lookup"><span data-stu-id="6561a-213">Click **Show Options**.</span></span>
    
7. <span data-ttu-id="6561a-214">В разделе **Задайте дополнительные параметры библиотеки IRM**выберите **не разрешать пользователям загружать документы, которые не поддерживают IRM**.</span><span class="sxs-lookup"><span data-stu-id="6561a-214">Under **Set additional IRM library settings**, select **Do not allow users to upload documents that do not support IRM**.</span></span>
    
8. <span data-ttu-id="6561a-215">В разделе **права доступа Configure документа**выберите **Разрешить средства просмотра для печати** и **Разрешить средства просмотра для записи копии загруженного документа**.</span><span class="sxs-lookup"><span data-stu-id="6561a-215">Under **Configure document access rights**, select **Allow viewers to print** and **Allow viewers to write on a copy of the downloaded document**.</span></span>
    
9. <span data-ttu-id="6561a-216">В разделе **Настройка защиты группы и интервал учетные данные**выберите **Разрешить группы защиты** и **Группа по умолчанию**, введите **руководителей**.</span><span class="sxs-lookup"><span data-stu-id="6561a-216">Under **Set group protection and credentials interval**, select **Allow group protection** and for **Default group**, type **Executives**.</span></span>
    
10. <span data-ttu-id="6561a-217">Нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="6561a-217">Click **OK**.</span></span>
    
<span data-ttu-id="6561a-218">Затем отправьте новый документ в папку документов "Руководители" от имени генерального директора, скачайте его и ошибочно отправьте в папку документов "Продажи".</span><span class="sxs-lookup"><span data-stu-id="6561a-218">Next, acting as the CEO, you upload a new document to the Executives document folder, download it, then accidentally upload it to the Sales document folder.</span></span>
  
1. <span data-ttu-id="6561a-219">Откройте локальный папка для хранения документов **SensitiveData BeforeIRM.docx** .</span><span class="sxs-lookup"><span data-stu-id="6561a-219">Open the local folder where you stored the **SensitiveData-BeforeIRM.docx** document.</span></span>
    
2. <span data-ttu-id="6561a-220">Щелкните правой кнопкой мыши **SensitiveData BeforeIRM.docx**и выберите команду **Копировать**.</span><span class="sxs-lookup"><span data-stu-id="6561a-220">Right-click **SensitiveData-BeforeIRM.docx**, and then click **Copy**.</span></span>
    
3. <span data-ttu-id="6561a-221">Щелкните правой кнопкой мыши папку и выберите команду **Вставить**.</span><span class="sxs-lookup"><span data-stu-id="6561a-221">Right-click within the folder, and then click **Paste**.</span></span>
    
4. <span data-ttu-id="6561a-222">Измените имя нового файла **SensitiveData-BeforeIRM - Copy.docx** на **SensitiveData AfterIRM.docx**.</span><span class="sxs-lookup"><span data-stu-id="6561a-222">Rename the new **SensitiveData-BeforeIRM - Copy.docx** file to **SensitiveData-AfterIRM.docx**.</span></span>
    
5. <span data-ttu-id="6561a-223">В браузере откройте вкладку **Microsoft Office для дома** и щелкните значок пользователя в правом верхнем углу и нажмите кнопку **Выход**.</span><span class="sxs-lookup"><span data-stu-id="6561a-223">From the **Microsoft Office Home** tab in your browser, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
6. <span data-ttu-id="6561a-224">Перейдите к [http://portal.office.com](http://portal.office.com).</span><span class="sxs-lookup"><span data-stu-id="6561a-224">Go to [http://portal.office.com](http://portal.office.com).</span></span>
    
7. <span data-ttu-id="6561a-225">На странице **входа Office 365 в** щелкните имя учетной записи CEO, введите пароль и затем нажмите кнопку **Вход**.</span><span class="sxs-lookup"><span data-stu-id="6561a-225">On the **Office 365 sign in** page, click the CEO account name, type its password, and then click **Sign in**.</span></span>
    
8. <span data-ttu-id="6561a-226">На новой вкладке браузера введите URL-адрес для руководителей семейства веб-сайтов.</span><span class="sxs-lookup"><span data-stu-id="6561a-226">On a new tab of your browser, type the URL to the Executives site collection.</span></span>
    
9. <span data-ttu-id="6561a-227">На странице " **документы** " нажмите кнопку **Отправить**, укажите **SensitiveData AfterIRM.docx** документа в локальную папку и нажмите кнопку **Открыть**.</span><span class="sxs-lookup"><span data-stu-id="6561a-227">On the **Documents** page, click **Upload**, specify the **SensitiveData-AfterIRM.docx** document in your local folder, and then click **Open**.</span></span>
    
10. <span data-ttu-id="6561a-228">Выберите новый документ **SensitiveData AfterIRM.docx** на странице " **документы** ", нажмите кнопку с многоточием (...) в строке меню и нажмите кнопку **загрузить**.</span><span class="sxs-lookup"><span data-stu-id="6561a-228">Select the new **SensitiveData-AfterIRM.docx** document in the **Documents** page, click the ellipsis (…) in the menu bar, and then click **Download**.</span></span>
    
11. <span data-ttu-id="6561a-229">При появлении соответствующего запроса сохраните документ **SensitiveData AfterIRM.docx** в локальной папке, перезаписью исходной версии.</span><span class="sxs-lookup"><span data-stu-id="6561a-229">When prompted, save the **SensitiveData-AfterIRM.docx** document in your local folder, overwriting the original version.</span></span>
    
12. <span data-ttu-id="6561a-230">Закройте вкладку страницы **документов** .</span><span class="sxs-lookup"><span data-stu-id="6561a-230">Close the tab for the **Documents** page.</span></span>
    
13. <span data-ttu-id="6561a-231">На новой вкладке браузера введите URL-адрес семейства веб-сайтов продаж.</span><span class="sxs-lookup"><span data-stu-id="6561a-231">On a new tab of your browser, type the URL to the Sales site collection.</span></span>
    
14. <span data-ttu-id="6561a-232">Щелкните **документы**.</span><span class="sxs-lookup"><span data-stu-id="6561a-232">Click **Documents**.</span></span>
    
15. <span data-ttu-id="6561a-233">На странице " **документы** " нажмите кнопку **Отправить**, укажите **SensitiveData AfterIRM.docx** документа в локальную папку и нажмите кнопку **Открыть**.</span><span class="sxs-lookup"><span data-stu-id="6561a-233">On the **Documents** page, click **Upload**, specify the **SensitiveData-AfterIRM.docx** document in your local folder, and then click **Open**.</span></span>
    
16. <span data-ttu-id="6561a-234">Закройте вкладки **продаж семейства сайтов** и **SharePoint** .</span><span class="sxs-lookup"><span data-stu-id="6561a-234">Close the **Sales site collection** and **SharePoint** tabs.</span></span>
    
<span data-ttu-id="6561a-235">Далее будет действовать как обычный пользователь, вы попытаетесь обратиться к **SensitiveData AfterIRM.docx** документа в папке документов продажи.</span><span class="sxs-lookup"><span data-stu-id="6561a-235">Next, acting as a normal user, you try to access the **SensitiveData-AfterIRM.docx** document in the Sales document folder.</span></span>
  
1. <span data-ttu-id="6561a-236">В браузере откройте вкладку **Microsoft Office для дома** и щелкните значок пользователя в правом верхнем углу и нажмите кнопку **Выход**.</span><span class="sxs-lookup"><span data-stu-id="6561a-236">From the **Microsoft Office Home** tab in your browser, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="6561a-237">Перейдите к [http://portal.office.com](http://portal.office.com).</span><span class="sxs-lookup"><span data-stu-id="6561a-237">Go to [http://portal.office.com](http://portal.office.com).</span></span>
    
3. <span data-ttu-id="6561a-238">На странице **входа Office 365** щелкните имя учетной записи User5, введите пароль и затем нажмите кнопку **Вход**.</span><span class="sxs-lookup"><span data-stu-id="6561a-238">On the **Office 365 sign in** page, click the User5 account name, type its password, and then click **Sign in**.</span></span>
    
4. <span data-ttu-id="6561a-239">На новой вкладке браузера введите URL-адрес семейства веб-сайтов продаж.</span><span class="sxs-lookup"><span data-stu-id="6561a-239">On a new tab of your browser, type the URL to the Sales site collection.</span></span>
    
5. <span data-ttu-id="6561a-240">Щелкните **документы**.</span><span class="sxs-lookup"><span data-stu-id="6561a-240">Click **Documents**.</span></span>
    
6. <span data-ttu-id="6561a-241">На странице " **документы** " открываете документ **SensitiveData AfterIRM.docx** .</span><span class="sxs-lookup"><span data-stu-id="6561a-241">On the **Documents** page, open the **SensitiveData-AfterIRM.docx** document.</span></span>
    
    <span data-ttu-id="6561a-242">Появится сообщение "К сожалению, Word Online не может открыть этот документ, так как он защищен службой управления правами на доступ к данным (IRM)." </span><span class="sxs-lookup"><span data-stu-id="6561a-242">You should see a message that states "Sorry, Word Online can't open this document because it's protected by Information Rights Management (IRM)."</span></span> 
    
7. <span data-ttu-id="6561a-p105">Нажмите кнопку **"Изменить" в Word**. Приглашение, чтобы открыть файл. Нажмите кнопку **Да**.</span><span class="sxs-lookup"><span data-stu-id="6561a-p105">Click **Edit in Word**. You are prompted if you want to open the file. Click **Yes**.</span></span>
    
8. <span data-ttu-id="6561a-p106">Вам будет предложено входа введите имя учетной записи для учетной записи User5, а затем нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="6561a-p106">You are prompted to sign-in. Type the account name of the User5 account, and then click **Next**.</span></span>
    
9. <span data-ttu-id="6561a-p107">Будет предложено ввести пароль. Введите пароль для учетной записи User5 и нажмите кнопку **Вход**.</span><span class="sxs-lookup"><span data-stu-id="6561a-p107">You are prompted to provide the password. Type the password for the User5 account and then click **Sign in**.</span></span> 
    
    <span data-ttu-id="6561a-250">Появится такое сообщение: "Ваши учетные данные не позволяют вам открыть этот документ."</span><span class="sxs-lookup"><span data-stu-id="6561a-250">You should see the a message that states: "You do not have the credentials that allow you to open this document."</span></span>
    
10. <span data-ttu-id="6561a-251">Нажмите кнопку **Нет**.</span><span class="sxs-lookup"><span data-stu-id="6561a-251">Click **No**.</span></span>
    
<span data-ttu-id="6561a-p108">Другой способ просмотра защиту IRM — просматривать файлы в локальной папке. **SensitiveData AfterIRM.docx** должно быть значительно больше **SensitiveData BeforeIRM.docx** файла. Файл **SensitiveData AfterIRM.docx** зашифрован и добавил данные защиту IRM к нему.</span><span class="sxs-lookup"><span data-stu-id="6561a-p108">Another way to see the IRM protection is to look at the files in your local folder. The **SensitiveData-AfterIRM.docx** should be much larger than the **SensitiveData-BeforeIRM.docx** file. The **SensitiveData-AfterIRM.docx** file is encrypted and has the IRM protection information added to it.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="6561a-255">См. также</span><span class="sxs-lookup"><span data-stu-id="6561a-255">See Also</span></span>

[<span data-ttu-id="6561a-256">Руководства по лаборатории тестирования для принятия облачных решений</span><span class="sxs-lookup"><span data-stu-id="6561a-256">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="6561a-257">Базовая конфигурация среды разработки и тестирования</span><span class="sxs-lookup"><span data-stu-id="6561a-257">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="6561a-258">Среда разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="6561a-258">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="6561a-259">Освоение облака и гибридные решения</span><span class="sxs-lookup"><span data-stu-id="6561a-259">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)


