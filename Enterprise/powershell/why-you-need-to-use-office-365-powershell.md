---
title: Причины использования Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/13/2019
audience: ITPro
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Ent_Office_Other
ms.assetid: b3209b1a-40c7-4ede-8e78-8a88bb2adc8a
description: 'Сводка: в этой статье рассказывается, почему необходимо использовать PowerShell в Office 365 для управления Office 365:: в ряде случаев это может быть более эффективно, а в других  вызвано необходимостью.'
ms.openlocfilehash: f7854888db563b932567200db0d24708d59f9969
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/07/2020
ms.locfileid: "41841256"
---
# <a name="why-you-need-to-use-office-365-powershell"></a><span data-ttu-id="bc12b-103">Причины использования Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="bc12b-103">Why you need to use Office 365 PowerShell</span></span>

<span data-ttu-id="bc12b-104">С помощью центра администрирования Microsoft 365 можно не только управлять учетными записями пользователей и лицензиями Office 365, но и управлять такими службами Office 365, как Exchange Online, Teams и SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="bc12b-104">With the Microsoft 365 admin center, you can not only manage your Office 365 user accounts and licenses, but you can also manage your Office 365 services such as Exchange Online, Teams, and SharePoint Online.</span></span> <span data-ttu-id="bc12b-105">Тем не менее, вы также можете управлять этими элементами с помощью команд PowerShell для Office 365, используя преимущества командной строки и язык сценариев для ускорения, автоматизации и дополнительной возможности.</span><span class="sxs-lookup"><span data-stu-id="bc12b-105">However, you can also manage these elements with Office 365 PowerShell commands, taking advantage of a command-line and scripting language environment for speed, automation, and additional capability.</span></span>
  
<span data-ttu-id="bc12b-106">В этой статье мы расскажем, как использовать PowerShell Office 365 для управления Office 365:</span><span class="sxs-lookup"><span data-stu-id="bc12b-106">In this article, we'll show you these ways in which you can use Office 365 PowerShell to manage Office 365:</span></span>
  
- <span data-ttu-id="bc12b-107">Показать дополнительные сведения, которые не отображаются в центре администрирования Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="bc12b-107">Reveal additional information that you cannot see with the Microsoft 365 admin center</span></span>
    
- <span data-ttu-id="bc12b-108">Настройка компонентов и параметров, доступных только с помощью PowerShell для Office 365</span><span class="sxs-lookup"><span data-stu-id="bc12b-108">Configure features and settings only possible with Office 365 PowerShell</span></span>
    
- <span data-ttu-id="bc12b-109">Выполнение массовых операций</span><span class="sxs-lookup"><span data-stu-id="bc12b-109">Perform bulk operations</span></span>
    
- <span data-ttu-id="bc12b-110">Фильтрация данных</span><span class="sxs-lookup"><span data-stu-id="bc12b-110">Filtering data</span></span>
    
- <span data-ttu-id="bc12b-111">Печать или сохранение данных</span><span class="sxs-lookup"><span data-stu-id="bc12b-111">Print or save data</span></span>
    
- <span data-ttu-id="bc12b-112">Управление между службами</span><span class="sxs-lookup"><span data-stu-id="bc12b-112">Manage across services</span></span>
    
<span data-ttu-id="bc12b-p102">Приступая к чтению статьи, необходимо понимать, что PowerShell в Office 365 — это набор модулей для Windows PowerShell, среды командной строки для служб и платформ Windows. Эта среда создает язык командной строки, который можно расширить с помощью дополнительных модулей и который позволяет выполнять как простые, так и сложные команды и скрипты. Например, после установки модулей PowerShell в Office 365 и подключения подписки на Office 365 вы можете выполнить следующую команду, чтобы получить список всех почтовых ящиков пользователей для Microsoft Exchange Online:</span><span class="sxs-lookup"><span data-stu-id="bc12b-p102">Before you begin, understand that Office 365 PowerShell is a set of modules for Windows PowerShell, a command-line environment for Windows-based services and platforms. This environment creates a command shell language that can be extended with additional modules and provides a way to execute simple or complex commands or scripts. For example, after you install the Office 365 PowerShell modules and connect to your Office 365 subscription, you can run this command to list all of the user mailboxes for Microsoft Exchange Online:</span></span>
  
```powershell
Get-Mailbox
```

<span data-ttu-id="bc12b-116">Вы также можете легко выполнить список почтовых ящиков с помощью центра администрирования Microsoft 365, но подсчитать количество элементов во всех списках всех сайтов для всех веб-приложений нелегко.</span><span class="sxs-lookup"><span data-stu-id="bc12b-116">Getting the list of mailboxes can also be easily done using the Microsoft 365 admin center, but counting the number of items in all of the lists for all of the sites for all of your web apps cannot be easily done.</span></span>
  
<span data-ttu-id="bc12b-117">Обратите внимание на то, что Office 365 PowerShell предназначен для расширения возможностей управления Office 365, а не для замены центра администрирования Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="bc12b-117">Please note that Office 365 PowerShell is designed to augment and enhance your ability to manage Office 365, not to replace the Microsoft 365 admin center.</span></span> <span data-ttu-id="bc12b-118">Как администратор Office 365:, вы должны владеть по крайней мере основами работы с Office 365: PowerShell, так как некоторые процедуры настройки можно выполнить только с помощью команд PowerShell в Office 365.</span><span class="sxs-lookup"><span data-stu-id="bc12b-118">As an Office 365 administrator, you must become at least comfortable with using Office 365 PowerShell because there are some configuration procedures that can only be done with Office 365 PowerShell commands.</span></span> <span data-ttu-id="bc12b-119">В таких случаях вы должны уметь:</span><span class="sxs-lookup"><span data-stu-id="bc12b-119">In these cases, you will be required to understand how to:</span></span>
  
- <span data-ttu-id="bc12b-120">устанавливать модули PowerShell в Office 365 (выполняется только один раз для компьютера администратора);</span><span class="sxs-lookup"><span data-stu-id="bc12b-120">Install the Office 365 PowerShell modules (done only once for each administrator computer).</span></span>
    
- <span data-ttu-id="bc12b-121">подключаться к своей подписке Office 365: (выполняется один раз для каждого сеанса PowerShell);</span><span class="sxs-lookup"><span data-stu-id="bc12b-121">Connect to your Office 365 subscription (done once for each PowerShell session).</span></span>
    
- <span data-ttu-id="bc12b-122">собирать информацию для выполнения необходимых команд PowerShell в Office 365;</span><span class="sxs-lookup"><span data-stu-id="bc12b-122">Gather the information needed to run the required Office 365 PowerShell commands.</span></span>
    
- <span data-ttu-id="bc12b-123">успешно выполнять команды PowerShell в Office 365.</span><span class="sxs-lookup"><span data-stu-id="bc12b-123">Run the Office 365 PowerShell commands successfully.</span></span>
    
<span data-ttu-id="bc12b-p104">Овладев этими основными навыками, вам не обязательно отображать список пользователей почтовых ящиков с помощью команды **Get-Mailbox** или учиться создавать команду, подобную предыдущей, для подсчета всех элементов во всех списках для всех сайтов всех веб-приложений. Корпорация Майкрософт и сообщество администраторов Office 365: могут помочь вам в этом при необходимости.</span><span class="sxs-lookup"><span data-stu-id="bc12b-p104">After learning these basic skills, you are not required to list your mailbox users with **Get-Mailbox** command, nor are you required to understand how to create a new command like the previous one to count all the items in all the lists for all of the sites for all of your web apps. Microsoft and the community of Office 365 administrators can help you with that as needed.</span></span>
  
## <a name="office-365-powershell-can-reveal-additional-information-that-you-cannot-see-with-the-microsoft-365-admin-center"></a><span data-ttu-id="bc12b-126">Office 365 PowerShell может открыть дополнительные сведения, которые не отображаются в центре администрирования Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="bc12b-126">Office 365 PowerShell can reveal additional information that you cannot see with the Microsoft 365 admin center</span></span>

<span data-ttu-id="bc12b-127">В центре администрирования Microsoft 365 отображается большое количество полезной информации, но это не означает, что на ней отображаются все возможные сведения, которые хранятся в Office 365 для пользователей, лицензий, почтовых ящиков и сайтов.</span><span class="sxs-lookup"><span data-stu-id="bc12b-127">The Microsoft 365 admin center displays a lot of useful information, but that doesn't mean that it displays all the possible information that Office 365 stores on users, licenses, mailboxes, and sites.</span></span> <span data-ttu-id="bc12b-128">Ниже приведен пример для **пользователей и групп** в центре администрирования Microsoft 365:</span><span class="sxs-lookup"><span data-stu-id="bc12b-128">Here is an example for **users and groups** in the Microsoft 365 admin center:</span></span>
  
![Пример отображения пользователей и групп в центре администрирования Microsoft 365.](media/o365-powershell-users-and-groups.png)
  
<span data-ttu-id="bc12b-130">Для многих целей отображаются сведения, которые необходимо знать.</span><span class="sxs-lookup"><span data-stu-id="bc12b-130">For many purposes, this displays the information you need to know.</span></span> <span data-ttu-id="bc12b-131">Однако бывают случаи, когда вам требуется больше времени.</span><span class="sxs-lookup"><span data-stu-id="bc12b-131">However, there are times when you need more.</span></span> <span data-ttu-id="bc12b-132">Например, лицензирование Office 365 (и возможности Office 365, доступные пользователю) зависят от географического расположения этого пользователя.</span><span class="sxs-lookup"><span data-stu-id="bc12b-132">For example, Office 365 licensing (and the Office 365 features available to a user) depend in part on that user's geographic location.</span></span> <span data-ttu-id="bc12b-133">Политики и функции, которые вы можете расширить для пользователя, который живет в США, могут отличаться от политик и функций, которые можно расширить для пользователя, который живет в Индии или в Бельгии.</span><span class="sxs-lookup"><span data-stu-id="bc12b-133">The policies and features you can extend to a user who lives in the United States might not be the same as the policies and features you can extend to a user who lives in India or in Belgium.</span></span> <span data-ttu-id="bc12b-134">С помощью центра администрирования Microsoft 365 вы можете определить географическое расположение пользователя, выполнив указанные ниже действия.</span><span class="sxs-lookup"><span data-stu-id="bc12b-134">You can use the Microsoft 365 admin center to determine a user's geographic location with these steps:</span></span>
  
1. <span data-ttu-id="bc12b-135">Дважды щелкните **отображаемое имя** пользователя.</span><span class="sxs-lookup"><span data-stu-id="bc12b-135">Double-click the user's **Display Name**.</span></span>
    
2. <span data-ttu-id="bc12b-136">На панели отображения свойств пользователя щелкните **сведения**.</span><span class="sxs-lookup"><span data-stu-id="bc12b-136">In the user properties display pane, click **details**.</span></span>
    
3. <span data-ttu-id="bc12b-137">В окне сведений щелкните **дополнительные сведения**.</span><span class="sxs-lookup"><span data-stu-id="bc12b-137">In the details display, click **additional details**.</span></span>
    
4. <span data-ttu-id="bc12b-138">Прокрутите окно вниз до заголовка **Страна или регион**.</span><span class="sxs-lookup"><span data-stu-id="bc12b-138">Scroll down until you see the heading **Country or region**:</span></span>
    
     ![Пример сведений о регионе для пользователя в центре администрирования Microsoft 365.](media/o365-powershell-usage-location.png)
  
5. <span data-ttu-id="bc12b-140">Запишите отображаемое имя и местонахождение пользователя на лист бумаги или скопируйте и вставьте их в Блокнот.</span><span class="sxs-lookup"><span data-stu-id="bc12b-140">Write the user's display name and location on a piece of paper, or copy and paste it into Notepad.</span></span> 
    
<span data-ttu-id="bc12b-p107">Эту процедуру необходимо повторить для каждого пользователя. Если пользователей очень много, эта задача может показаться утомительной. В PowerShell в Office 365 вы можете отобразить эти сведения обо всех пользователях с помощью следующей команды:</span><span class="sxs-lookup"><span data-stu-id="bc12b-p107">You must repeat this procedure for each user. For many users, this can be a tedious task. With Office 365 PowerShell, you can display this information for all of your users with the following command:</span></span>
  
```powershell
Get-MsolUser | Select DisplayName, UsageLocation
```


>[!Note]
><span data-ttu-id="bc12b-144">В PowerShell Core не поддерживается модуль Microsoft Azure Active Directory для Windows PowerShell и командлеты с компонентом **Msol** в имени.</span><span class="sxs-lookup"><span data-stu-id="bc12b-144">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="bc12b-145">Чтобы использовать эти командлеты, необходимо запустить их из Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bc12b-145">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="bc12b-146">Ниже приведен пример отображения.</span><span class="sxs-lookup"><span data-stu-id="bc12b-146">Here is an example of the display:</span></span>
  
```powershell
DisplayName                               UsageLocation
-----------                               -------------
Bonnie Kearney                            GB
Fabrice Canel                             BR
Brian Johnson (TAILSPIN)                  US
Anne Wallace                              US
Alex Darrow                               US
David Longmuir                            BR
```

> [!TIP]
>  <span data-ttu-id="bc12b-147">Эта команда PowerShell возвращает список всех пользователей в текущей подписке Office 365 (**Get-MsolUser**), но отображает только имя и местонахождение каждого пользователя (**Select DisplayName, UsageLocation**).</span><span class="sxs-lookup"><span data-stu-id="bc12b-147">The interpretation of this Office 365 PowerShell command is: Get all of the users in the current Office 365 subscription ( **Get-MsolUser** ), but only display the name and location for each user ( **Select DisplayName, UsageLocation** ).</span></span>
  
<span data-ttu-id="bc12b-p109">Так как PowerShell в Office 365 поддерживает язык командной оболочки, вы можете выполнять дополнительные действия над информацией, полученной с помощью команды **Get-MSolUser**. Например, вы можете отсортировать пользователей по их расположениям и объединить в группы пользователей из Бразилии, США, и т. д. Это можно сделать с помощью указанной ниже команды.</span><span class="sxs-lookup"><span data-stu-id="bc12b-p109">Because Office 365 PowerShell supports a command shell language, you can further manipulate the information obtained from the **Get-MSolUser** command. For example, maybe you'd like to sort these users by their location, grouping all the Brazilian users together, all the United States users together, etc. Here is the command:</span></span>
  
```powershell
Get-MsolUser | Select DisplayName, UsageLocation | Sort UsageLocation, DisplayName
```

<span data-ttu-id="bc12b-150">Ниже приведен пример отображения.</span><span class="sxs-lookup"><span data-stu-id="bc12b-150">Here is an example of the display:</span></span>
  
```powershell
DisplayName                                 UsageLocation
-----------                                 -------------
David Longmuir                              BR
Fabrice Canel                               BR
Bonnie Kearney                              GB
Alex Darrow                                 US
Anne Wallace                                US
Brian Johnson (TAILSPIN)                    US
```

> [!TIP]
>  <span data-ttu-id="bc12b-151">Эта команда PowerShell возвращает список всех пользователей в текущей подписке Office 365, но отображает только имя и местонахождение каждого пользователя. Список сортируется сначала по местонахождению, а затем по имени (**Sort UsageLocation, DisplayName**).</span><span class="sxs-lookup"><span data-stu-id="bc12b-151">The interpretation of this Office 365 PowerShell command is: Get all of the users in the current Office 365 subscription, but only display the name and location for each user and sort them first by their location, and then their names ( **Sort UsageLocation, DisplayName** ).</span></span>
  
<span data-ttu-id="bc12b-p110">Можно также использовать дополнительные фильтры. Например, если нужно просмотреть сведения о пользователях, находящихся в Бразилии, используйте следующую команду:</span><span class="sxs-lookup"><span data-stu-id="bc12b-p110">You can also employ additional filtering. For example, if you only want to see information about users based in Brazil, use this command:</span></span>
  
```powershell
Get-MsolUser | Where {$_.UsageLocation -eq "BR"} | Select DisplayName, UsageLocation 
```

<span data-ttu-id="bc12b-154">Ниже приведен пример отображения.</span><span class="sxs-lookup"><span data-stu-id="bc12b-154">Here is an example of the display:</span></span>
  
```powershell
DisplayName                                           UsageLocation
-----------                                           -------------
David Longmuir                                        BR
Fabrice Canel                                         BR
```

> [!TIP]
>  <span data-ttu-id="bc12b-155">Эта команда PowerShell возвращает список всех пользователей в текущей подписке Office 365, которые находятся в Бразилии (**Where {$\_.UsageLocation -eq "BR"}**), а затем отображает имя и местонахождение каждого пользователя.</span><span class="sxs-lookup"><span data-stu-id="bc12b-155">The interpretation of this Office 365 PowerShell command is: Get all of the users in the current Office 365 subscription whose location is Brazil ( **Where {$\_.UsageLocation -eq "BR"}** ), then display the name and location for each user.</span></span>
  
 <span data-ttu-id="bc12b-156">**Небольшое примечание относительно более крупных доменов**</span><span class="sxs-lookup"><span data-stu-id="bc12b-156">**A Quick Note Regarding Larger Domains**</span></span>
  
<span data-ttu-id="bc12b-p111">Если у вас очень большой домен, включающий десятки тысяч пользователей, то использование некоторых сценариев, описанных в этой статье, может привести к так называемому "регулированию". Это будет означать, что вы одновременно выполняете слишком большое количество задач, для чего недостаточно мощности компьютера и пропускной способности сети. Поэтому крупным организациям может понадобиться разбить некоторые из этих команд PowerShell в Office 365 на две команды. Например, указанная ниже команда возвращает все учетные записи пользователей и отображает для каждой из них имя и расположение.</span><span class="sxs-lookup"><span data-stu-id="bc12b-p111">If you have a very large domain with tens of thousands of users, trying some of the examples we show in this article could lead to "throttling." That means that, based on things like computing power and available network bandwidth, you're trying to do a little too much at one time. Because of that, larger organizations might want to split some of these Office 365 PowerShell commands into two commands. For example, this one command returns all the user accounts and shows the name and location for each:</span></span>
  
```powershell
Get-MsolUser | Select DisplayName, UsageLocation
```

<span data-ttu-id="bc12b-p112">Она отлично подходит для небольших доменов. Тем не менее крупной организации может понадобиться разделить ее на две команды: одна команда будет использоваться для сохранения сведений об учетных записях пользователей в переменной, а другая  для отображения необходимой информации. Вот пример:</span><span class="sxs-lookup"><span data-stu-id="bc12b-p112">That works great for smaller domains. In a large organization, however, you might need to split that into two commands: one command to store the user account information in a variable and another command to display the needed information. Here is an example:</span></span>
  
```powershell
$x = Get-MsolUser
$x | Select DisplayName, UsageLocation
```

<span data-ttu-id="bc12b-164">Этот набор команд PowerShell для Office 365 интерпретируется так:</span><span class="sxs-lookup"><span data-stu-id="bc12b-164">The interpretation of this set of Office 365 PowerShell commands is:</span></span>
- <span data-ttu-id="bc12b-165">Возвращается список всех пользователей в текущей подписке Office 365, после чего сведения сохраняются в переменной $x (**$x = Get-MsolUser**).</span><span class="sxs-lookup"><span data-stu-id="bc12b-165">Get all of the users in the current Office 365 subscription and store the information in a variable named $x ( **$x = Get-MsolUser** ).</span></span>
- <span data-ttu-id="bc12b-166">Отображается содержимое переменной $x, которое включает в себя только имя и местонахождение каждого пользователя (**$x | Select DisplayName, UsageLocation**).</span><span class="sxs-lookup"><span data-stu-id="bc12b-166">Display the contents of the variable $x, but only include the name and location for each user ( **$x | Select DisplayName, UsageLocation** ).</span></span>
  
## <a name="office-365-has-features-that-you-can-only-configure-with-office-365-powershell"></a><span data-ttu-id="bc12b-167">Некоторые компоненты Office 365 можно настроить только с помощью PowerShell</span><span class="sxs-lookup"><span data-stu-id="bc12b-167">Office 365 has features that you can only configure with Office 365 PowerShell</span></span>

<span data-ttu-id="bc12b-168">Центр администрирования Microsoft 365 предназначен для обеспечения доступа к наиболее распространенным или осмысленным задачам администрирования, которые применяются к большинству пользователей.</span><span class="sxs-lookup"><span data-stu-id="bc12b-168">The Microsoft 365 admin center is intended to provide access to the most common or meaningful administrative tasks that apply to most people.</span></span> <span data-ttu-id="bc12b-169">Другими словами, центр администрирования Microsoft 365 был разработан таким образом, что стандартный администратор может использовать это средство для выполнения самых распространенных задач управления.</span><span class="sxs-lookup"><span data-stu-id="bc12b-169">In other words, the Microsoft 365 admin center was designed so that the typical administrator could use the tool to carry out the most common management tasks.</span></span> <span data-ttu-id="bc12b-170">Это определение означает, что существует несколько задач, которые невозможно выполнить с помощью центра администрирования Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="bc12b-170">By this definition, that means that there are some tasks that can't be completed by using the Microsoft 365 admin center.</span></span>
  
<span data-ttu-id="bc12b-171">Например, в Центр администрирования Skype для бизнеса Online используется несколько параметров для создания настраиваемых приглашений на собрания:</span><span class="sxs-lookup"><span data-stu-id="bc12b-171">For example, the Skype for Business Online Admin center provides a few options for creating custom meeting invitations:</span></span>
  
![Пример отображения настраиваемых приглашений на собрание в Центре администрирования Skype для бизнеса Online.](media/o365-powershell-meeting-invitation.png)
  
<span data-ttu-id="bc12b-p114">С помощью указанных ниже параметров приглашения на собрания можно сделать более персонализированными и профессиональными. Тем не менее, настройки собраний позволяют сделать больше, чем просто создать пользовательские приглашения. Например, по умолчанию собрания позволяют:</span><span class="sxs-lookup"><span data-stu-id="bc12b-p114">With these settings, you can add a touch of personalization and professionalism to meeting invitations. However, there's more to meeting configuration settings than simply creating custom meeting invitations. For example, by default, meetings allow:</span></span>
  
- <span data-ttu-id="bc12b-176">анонимным пользователям автоматически присоединяться к каждому собранию;</span><span class="sxs-lookup"><span data-stu-id="bc12b-176">Anonymous users to gain automatic entrance to each meeting.</span></span>
    
- <span data-ttu-id="bc12b-177">участникам записывать собрание;</span><span class="sxs-lookup"><span data-stu-id="bc12b-177">Attendees to record the meeting.</span></span>
    
- <span data-ttu-id="bc12b-178">обозначать всех пользователей из вашей организации докладчиками при их присоединении к собранию.</span><span class="sxs-lookup"><span data-stu-id="bc12b-178">All users from your organization to be designated as presenters when they join the meeting.</span></span>
    
<span data-ttu-id="bc12b-p115">Эти параметры недоступны в Центре администрирования Skype для бизнеса Online. Но ими можно управлять с помощью PowerShell в Office 365. Указанная ниже команда отключает эти три параметра.</span><span class="sxs-lookup"><span data-stu-id="bc12b-p115">These settings are not available from the Skype for Business Online Admin center. However, you can control them from Office 365 PowerShell. Here is a command that disables these three settings:</span></span>
  
```powershell
Set-CsMeetingConfiguration -AdmitAnonymousUsersByDefault $False -AllowConferenceRecording $False -DesignateAsPresenter "None"
```

> [!NOTE]
> <span data-ttu-id="bc12b-182">Для использования этой команды необходимо установить [модуль PowerShell для Skype для бизнеса Online](https://www.microsoft.com/download/details.aspx?id=39366).</span><span class="sxs-lookup"><span data-stu-id="bc12b-182">This command requires that you install the [Skype for Business Online PowerShell Module ](https://www.microsoft.com/download/details.aspx?id=39366).</span></span> 
  
> [!TIP]
>  <span data-ttu-id="bc12b-183">Эта команда PowerShell для Office 365 отключает разрешение для анонимных пользователям автоматически присоединяться к новым собраниям Skype для бизнеса Online (**Set-CsMeetingConfiguration**, **-AdmitAnonymousUsersByDefault $False**), отключает для участников возможность записывать эти собрания (**-AllowConferenceRecording $False**) и отменяет для всех пользователей в организации статус выступающего (**-DesignateAsPresenter "None"**).</span><span class="sxs-lookup"><span data-stu-id="bc12b-183">The interpretation of this Office 365 PowerShell command is: For the settings for new Skype for Business Online meetings ( **Set-CsMeetingConfiguration** ), disable allowing anonymous users to gain automatic entrance to meetings ( **-AdmitAnonymousUsersByDefault $False** ), disable the ability for attendees to record meetings ( **-AllowConferenceRecording $False** ), and do not designate all users from your organization as presenters ( **-DesignateAsPresenter "None"** ).</span></span>
  
<span data-ttu-id="bc12b-184">Если вы передумали и хотите восстановить эти настройки по умолчанию (т. е. включить их все), выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="bc12b-184">If you change your mind and want to restore these default settings (all of them enabled), run this command:</span></span>
  
```powershell
Set-CsMeetingConfiguration -AdmitAnonymousUsersByDefault $True -AllowConferenceRecording $True -DesignateAsPresenter "Company"
```

<span data-ttu-id="bc12b-p116">Это только один пример. Существуют и другие, поэтому вы как администратор Office 365: должны уметь без труда использовать команды PowerShell в Office 365.</span><span class="sxs-lookup"><span data-stu-id="bc12b-p116">This is just one example. There are others, which is why you, as an Office 365 administrator, need to be comfortable with running Office 365 PowerShell commands.</span></span>
  
## <a name="office-365-powershell-is-great-at-carrying-out-bulk-operations"></a><span data-ttu-id="bc12b-187">PowerShell Office 365 идеально подходит для массовых операций</span><span class="sxs-lookup"><span data-stu-id="bc12b-187">Office 365 PowerShell is great at carrying out bulk operations</span></span>

<span data-ttu-id="bc12b-188">Историческось, что визуальные интерфейсы, такие как центр администрирования Microsoft 365, наиболее полезны, если вы выполняете одну операцию.</span><span class="sxs-lookup"><span data-stu-id="bc12b-188">Historically, visual interfaces like the Microsoft 365 admin center are most valuable when you have a single operation to perform.</span></span> <span data-ttu-id="bc12b-189">Например, если необходимо отключить одну учетную запись пользователя, вы можете использовать центр администрирования Microsoft 365 для быстрого обнаружения и снятия флажка.</span><span class="sxs-lookup"><span data-stu-id="bc12b-189">For example, if you need to disable one user account, you can use the Microsoft 365 admin center to quickly locate and clear a checkbox.</span></span> <span data-ttu-id="bc12b-190">Обычно это проще, чем выполнить аналогичную операцию в PowerShell в Office 365.</span><span class="sxs-lookup"><span data-stu-id="bc12b-190">This can be simpler than performing a similar operation in Office 365 PowerShell.</span></span>
  
<span data-ttu-id="bc12b-191">Но если вам нужно изменить множество вещей или некоторые из выбранных элементов в большом наборе других элементов, центр администрирования Microsoft 365 может оказаться неоптимальным.</span><span class="sxs-lookup"><span data-stu-id="bc12b-191">But if you have to change many things or some selected things within a large set of other things, the Microsoft 365 admin center might not be the best use of your time.</span></span> <span data-ttu-id="bc12b-192">Например, если необходимо изменить префикс для тысяч телефонных номеров или удалить определенного пользователя, Ken Myer со всех сайтов SharePoint Online, как это сделать в центре администрирования Microsoft 365?</span><span class="sxs-lookup"><span data-stu-id="bc12b-192">For example, if you had to change the prefix on thousands of phone numbers or you needed to remove a specific user, Ken Myer, from all of your SharePoint Online sites, how would you do that in the Microsoft 365 admin center?</span></span>
  
<span data-ttu-id="bc12b-193">Допустим, в последнем примере у вас есть несколько сотен сайтов SharePoint Online и вы даже не знаете, на каком из них зарегистрирован пользователь Ken Meyer.</span><span class="sxs-lookup"><span data-stu-id="bc12b-193">For the latter example, you have several hundred SharePoint Online sites and you don't know even know which ones of which Ken Meyer is a member.</span></span> <span data-ttu-id="bc12b-194">Это означает, что вам потребуется начать с центра администрирования Microsoft 365, а затем выполнить эту процедуру для каждого сайта:</span><span class="sxs-lookup"><span data-stu-id="bc12b-194">That means you'll have to start at the Microsoft 365 admin center and then perform this procedure for each site:</span></span>
  
1. <span data-ttu-id="bc12b-195">Щелкнуть **URL-адрес** сайта.</span><span class="sxs-lookup"><span data-stu-id="bc12b-195">Click the **URL** of the site.</span></span>
    
2. <span data-ttu-id="bc12b-196">В поле **свойств семейства веб-сайтов** щелкнуть ссылку **Адрес веб-сайта**, чтобы открыть сайт.</span><span class="sxs-lookup"><span data-stu-id="bc12b-196">In the **site collection properties** box, click the **Web Site Address** link to open the site.</span></span>
    
3. <span data-ttu-id="bc12b-197">На сайте нажать кнопку **Общий доступ**.</span><span class="sxs-lookup"><span data-stu-id="bc12b-197">On the site, click **Share**.</span></span>
    
4. <span data-ttu-id="bc12b-198">В диалоговом окне **Общий доступ** щелкнуть ссылку, чтобы показать всех пользователей с разрешениями для сайта:</span><span class="sxs-lookup"><span data-stu-id="bc12b-198">In the **Share** dialog box click the link that shows you all the users who have permissions to the site:</span></span>
    
     ![Пример просмотра участников сайта SharePoint Online в Центре администрирования SharePoint Online](media/o365-powershell-view-permissions.png)
  
5. <span data-ttu-id="bc12b-200">В диалоговом окне **Общий доступ предоставлен** нажать кнопку **Дополнительно**.</span><span class="sxs-lookup"><span data-stu-id="bc12b-200">In the **Shared With** dialog box, click **Advanced**.</span></span>
    
6. <span data-ttu-id="bc12b-201">Прокрутить список пользователей, найти и выбрать Кена Майера (если у него есть разрешения для сайта) и нажать кнопку **Удалить разрешения пользователя**.</span><span class="sxs-lookup"><span data-stu-id="bc12b-201">Scroll down the list of users, find and select Ken Myer (assuming he has permissions to the site), and then click **Remove User Permissions**.</span></span>
    
<span data-ttu-id="bc12b-202">Для нескольких сотен сайтов это может занять очень много времени.</span><span class="sxs-lookup"><span data-stu-id="bc12b-202">This can take a long time for several hundred sites.</span></span>
  
<span data-ttu-id="bc12b-203">Но есть и другой вариант: удалить пользователя Ken Myer со всех сайтов с помощью указанной ниже команды PowerShell в Office 365.</span><span class="sxs-lookup"><span data-stu-id="bc12b-203">The alternative is to use Office 365 PowerShell and the following command to remove Ken Myer from all of your sites:</span></span>
  
```powershell
Get-SPOSite | ForEach {Remove-SPOUser -Site $_.Url -LoginName "kenmyer@litwareinc.com"}
```

> [!NOTE]
> <span data-ttu-id="bc12b-204">Для этой команды необходимо установить [модуль PowerShell для SharePoint Online](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span><span class="sxs-lookup"><span data-stu-id="bc12b-204">This command requires that you install the [SharePoint Online PowerShell module](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span></span> 
  
> [!TIP]
>  <span data-ttu-id="bc12b-205">Эта команда PowerShell возвращает список всех сайтов SharePoint в текущей подписке Office 365 (**Get-SPOSite**) и удаляет пользователя Ken Meyer из списка зарегистрированных пользователей каждого сайта (**ForEach {Remove-SPOUser -Site $\_.Url -LoginName "kenmyer@litwareinc.com"}**).</span><span class="sxs-lookup"><span data-stu-id="bc12b-205">The interpretation of this Office 365 PowerShell command is:  Get all of the SharePoint sites in the current Office 365 subscription ( **Get-SPOSite** ) and for each site, remove Ken Meyer from the list of users who can access it ( **ForEach {Remove-SPOUser -Site $\_.Url -LoginName "kenmyer@litwareinc.com"}** ).</span></span>
  
<span data-ttu-id="bc12b-206">Так как мы указываем Office 365: удалить пользователя Ken Meyer с каждого сайта, включая те, к которым у него нет доступа, эта команда будет показывать ошибки для таких сайтов.</span><span class="sxs-lookup"><span data-stu-id="bc12b-206">Because we are telling Office 365 to remove Ken Meyer from every site, including those in which he does not have access, the display of this command will show errors for those sites in which he does not currently have access.</span></span> <span data-ttu-id="bc12b-207">В этой команде можно использовать дополнительное условие, чтобы пользователь Ken Meyer был удален только с тех сайтов, в списке учетных записей которых он содержится, но чтобы указанные ошибки не влияли на сами сайты.</span><span class="sxs-lookup"><span data-stu-id="bc12b-207">We can use an additional condition on this command to remove Key Meyer only from the sites that have him in their login list, but the listed errors cause no harm to the sites themselves.</span></span> <span data-ttu-id="bc12b-208">Выполнение этой команды может занять несколько минут, а не часов работы с сотнями сайтов в центре администрирования Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="bc12b-208">This command might take a few minutes to run against hundreds of sites, rather than hours of working through the Microsoft 365 admin center.</span></span>
  
<span data-ttu-id="bc12b-p121">Вот еще один пример массовой операции. Чтобы добавить пользователя Бонни Керни (Bonnie Kearney) — нового администратора SharePoint — на все сайты в организации, используйте следующую команду:</span><span class="sxs-lookup"><span data-stu-id="bc12b-p121">Here is another bulk operation example. Use this command to add Bonnie Kearney, a new SharePoint administrator, to all of the sites in the organization:</span></span>
  
```powershell
Get-SPOSite | ForEach {Add-SPOUser -Site $_.Url -LoginName "bkearney@litwareinc.com" -Group "Members"}
```

> [!TIP]
>  <span data-ttu-id="bc12b-211">Эта команда PowerShell возвращает список всех сайтов SharePoint в текущей подписке Office 365, а затем добавляет имя Bonnie Kearney в группу участников каждого сайта, чтобы разрешить этому пользователю соответствующий доступ (**ForEach {Add-SPOUser -Site $\_.Url -LoginName "bkearney@litwareinc.com" -Group "Members"}**).</span><span class="sxs-lookup"><span data-stu-id="bc12b-211">The interpretation of this Office 365 PowerShell command is:  Get all of the SharePoint sites in the current Office 365 subscription and for each site, allow Bonnie Kearney access by adding her login name to the Members group of the site ( **ForEach {Add-SPOUser -Site $\_.Url -LoginName "bkearney@litwareinc.com" -Group "Members"}** ).</span></span>
  
## <a name="office-365-powershell-is-great-at-filtering-data"></a><span data-ttu-id="bc12b-212">PowerShell для Office 365 позволяет фильтровать данные</span><span class="sxs-lookup"><span data-stu-id="bc12b-212">Office 365 PowerShell is great at filtering data</span></span>

<span data-ttu-id="bc12b-213">Центр администрирования Microsoft 365 предоставляет несколько различных способов фильтрации данных, чтобы быстро и легко находить целевое подмножество данных.</span><span class="sxs-lookup"><span data-stu-id="bc12b-213">The Microsoft 365 admin center provides several different ways to filter your data to quickly and easily locate a targeted subset of information.</span></span> <span data-ttu-id="bc12b-214">Например, Exchange упрощает фильтрацию практически любого свойства почтового ящика пользователя.</span><span class="sxs-lookup"><span data-stu-id="bc12b-214">For example, Exchange makes it easy to filter on practically any property of a user mailbox.</span></span> <span data-ttu-id="bc12b-215">Например, ниже приведен список почтовых ящиков всех пользователей, проживающих в городе Блумингтон:</span><span class="sxs-lookup"><span data-stu-id="bc12b-215">For example, here is the list of mailboxes for all the users who live in the city of Bloomington:</span></span>
  
![Пример расширенного поиска в центре администрирования Microsoft 365 для списка почтовых ящиков всех пользователей, проживающих в городе Блумингтон.](media/o365-powershell-advanced-search.png)
  
<span data-ttu-id="bc12b-p123">Кроме того, Центр администрирования Exchange позволяет сочетать различные условия фильтра. Например, можно найти почтовые ящики всех пользователей, проживающих в г. Блумингтон и работающих в отделе финансов.</span><span class="sxs-lookup"><span data-stu-id="bc12b-p123">The Exchange Admin center also lets you combine filter criteria. For example, you can find the mailboxes for all the people who live in Bloomington and who work in the Finance department.</span></span> 
  
<span data-ttu-id="bc12b-p124">Но возможности фильтрации в Центре администрирования Exchange ограничены. Например, вам может понадобиться найти почтовые ящики пользователей, проживающих в городах Блумингтон (Bloomington) или Сан-Диего (San Diego), или почтовые ящики всех пользователей, которые не проживают в городе Блумингтон.</span><span class="sxs-lookup"><span data-stu-id="bc12b-p124">However, there are limitations to what you can do in the Exchange Admin center. For example, maybe you'd like to find the mailboxes of people who live in Bloomington or San Diego, or the mailboxes for all the people who don't live in Bloomington.</span></span> 
  
<span data-ttu-id="bc12b-221">PowerShell в Office 365 позволяет получить список почтовых ящиков всех пользователей, проживающих в городах Блумингтон или Сан-Диего, с помощью указанной ниже команды.</span><span class="sxs-lookup"><span data-stu-id="bc12b-221">With Office 365 PowerShell, you can get a list of mailboxes for all the people who live in the cities of Bloomington or San Diego with this command:</span></span>
  
```powershell
Get-User | Where {$_.RecipientTypeDetails -eq "UserMailbox" -and ($_.City -eq "San Diego" -or $_.City -eq "Bloomington")} | Select DisplayName, City
```

<span data-ttu-id="bc12b-222">Ниже приведен пример отображения.</span><span class="sxs-lookup"><span data-stu-id="bc12b-222">Here is an example of the display:</span></span>
  
```powershell
DisplayName                              City
-----------                              ----
Alex Darrow                              San Diego
Bonnie Kearney                           San Diego
Julian Isla                              Bloomington
Rob Young                                Bloomington
```

> [!TIP]
>  <span data-ttu-id="bc12b-223">Эта команда PowerShell возвращает список всех пользователей в текущей подписке Office 365, имеющих почтовый ящик в городах Блумингтон или Сан-Диего (**Where {$\_.RecipientTypeDetails -eq "UserMailbox" -and ($\_.City -eq "San Diego" -or $\_.City -eq "Bloomington")}**), а затем отображает имя и город каждого из этих пользователей (**Select DisplayName, City**).</span><span class="sxs-lookup"><span data-stu-id="bc12b-223">The interpretation of this Office 365 PowerShell command is: Get all of the users in the current Office 365 subscription who have a mailbox in the cities of either San Diego or Bloomington ( **Where {$\_.RecipientTypeDetails -eq "UserMailbox" -and ($\_.City -eq "San Diego" -or $\_.City -eq "Bloomington")}** ), then display the name and city for each ( **Select DisplayName, City** ).</span></span>
  
<span data-ttu-id="bc12b-224">Чтобы отобразить список всех почтовых ящиков пользователей, проживающих в любом месте за исключением г. Блумингтон, используйте такую команду:</span><span class="sxs-lookup"><span data-stu-id="bc12b-224">To list all the mailboxes for people who live anywhere except Bloomington, here is the command:</span></span>
  
```powershell
Get-User | Where {$_.RecipientTypeDetails -eq "UserMailbox" -and $_.City -ne "Bloomington"} | Select DisplayName, City
```

<span data-ttu-id="bc12b-225">Ниже приведен пример отображения.</span><span class="sxs-lookup"><span data-stu-id="bc12b-225">Here is an example of the display:</span></span>
  
```powershell
DisplayName                               City
-----------                               ----
MOD Administrator                         Redmond
Alex Darrow                               San Diego
Allie Bellew                              Bellevue
Anne Wallace                              Louisville
Aziz Hassouneh                            Cairo
Belinda Newman                            Charlotte
Bonnie Kearney                            San Diego
David Longmuir                            Waukesha
Denis Dehenne                             Birmingham
Garret Vargas                             Seattle
Garth Fort                                Tulsa
Janet Schorr                              Bellevue
```

> [!TIP]
>  <span data-ttu-id="bc12b-226">Эта команда PowerShell возвращает список всех пользователей в текущей подписке Office 365, почтовый ящик которых расположен не в г. Блумингтон ( **Where {$\_.RecipientTypeDetails -eq "UserMailbox" -and $\_.City -ne "Bloomington"}** ), а затем отображает имя и город каждого из этих пользователей.</span><span class="sxs-lookup"><span data-stu-id="bc12b-226">The interpretation of this Office 365 PowerShell command is: Get all of the users in the current Office 365 subscription who have a mailbox not located in the city of Bloomington ( **Where {$\_.RecipientTypeDetails -eq "UserMailbox" -and $\_.City -ne "Bloomington"}** ), then display the name and city for each.</span></span>
  
<span data-ttu-id="bc12b-p125">Кроме того, в фильтрах PowerShell в Office 365 можно использовать подстановочные знаки для поиска соответствия с частью имени. Предположим, вы ищете учетную запись пользователя, но помните только, что его фамилия или Андерсон, или Хендерсон, или, может быть, Йоргенсон.</span><span class="sxs-lookup"><span data-stu-id="bc12b-p125">You can also use wildcard characters in your Office 365 PowerShell filters to match part of a name. For example, suppose you're looking for a user account, and all you can remember is that their last name was Anderson, or maybe Henderson, or maybe it was Jorgenson.</span></span>
  
<span data-ttu-id="bc12b-229">Вы можете проследить этого пользователя в центре администрирования Microsoft 365 с помощью средства поиска и выполнить три различных поиска:</span><span class="sxs-lookup"><span data-stu-id="bc12b-229">You could track down that user in the Microsoft 365 admin center by using the search tool and carrying out three different searches:</span></span>
  
- <span data-ttu-id="bc12b-230">*Андерсон*  ;</span><span class="sxs-lookup"><span data-stu-id="bc12b-230">One for  *Anderson*</span></span> 
    
- <span data-ttu-id="bc12b-231">*Хендерсон*  ;</span><span class="sxs-lookup"><span data-stu-id="bc12b-231">One for  *Henderson*</span></span> 
    
- <span data-ttu-id="bc12b-232">*Йоргенсон*  .</span><span class="sxs-lookup"><span data-stu-id="bc12b-232">One for  *Jorgenson*</span></span> 
    
<span data-ttu-id="bc12b-p126">Так как все три фамилии заканчиваются на "-сон", в PowerShell в Office 365 можно использовать команду для отображения всех пользователей, фамилия которых имеет такое окончание. Вот как это делается:</span><span class="sxs-lookup"><span data-stu-id="bc12b-p126">Because all three of these names end in "son", you can tell Office 365 PowerShell to display all the users whose name ends in "son". Here is the command:</span></span>
  
```powershell
Get-User -Filter '{LastName -like "*son"}'
```

> [!TIP]
>  <span data-ttu-id="bc12b-p127">Эта команда PowerShell для Office 365 возвращает список всех пользователей в текущей подписке Office 365, при этом используется фильтр, отображающий только пользователей, чьи фамилии заканчиваются на "son" (**-Filter '{LastName -like "\*son"}'**). Символ \* означает любой набор знаков, в этом случае букв в фамилии пользователя.</span><span class="sxs-lookup"><span data-stu-id="bc12b-p127">The interpretation of this Office 365 PowerShell command is: Get all of the users in the current Office 365 subscription, but use a filter that only lists the users whose last names end in "son" ( **-Filter '{LastName -like "\*son"}'** ). The \* stands for any set of characters, which are letters in the case of the user's last name.</span></span>
  
## <a name="office-365-powershell-makes-it-easy-to-print-or-save-data"></a><span data-ttu-id="bc12b-237">PowerShell для Office 365 упрощает печать и сохранение данных</span><span class="sxs-lookup"><span data-stu-id="bc12b-237">Office 365 PowerShell makes it easy to print or save data</span></span>

<span data-ttu-id="bc12b-238">Центр администрирования Microsoft 365 позволяет просматривать списки данных.</span><span class="sxs-lookup"><span data-stu-id="bc12b-238">The Microsoft 365 admin center lets you view lists of data.</span></span> <span data-ttu-id="bc12b-239">Ниже приведен пример, где в Центре администрирования Skype для бизнеса Online отображается список пользователей, для которых включено приложение Skype для бизнеса Online:</span><span class="sxs-lookup"><span data-stu-id="bc12b-239">Here is an example of the Skype for Business Online Admin center displaying a list of users who have been enabled for Skype for Business Online:</span></span>
  
![Пример Центра администрирования Skype для бизнеса Online со списком пользователей, для которых включен Skype для бизнеса Online.](media/o365-powershell-lync-users.png)
  
<span data-ttu-id="bc12b-241">Чтобы сохранить эти данные в файл, необходимо их скопировать и вставить в документ или лист Excel.</span><span class="sxs-lookup"><span data-stu-id="bc12b-241">To save that information to a file, you must copy and paste it into a document or Excel.</span></span> <span data-ttu-id="bc12b-242">В любом случае может потребоваться дополнительное форматирование копии.</span><span class="sxs-lookup"><span data-stu-id="bc12b-242">In either case, the copy might require additional formatting.</span></span> <span data-ttu-id="bc12b-243">Кроме того, центр администрирования Microsoft 365 не предоставляет возможности непосредственного вывода списка.</span><span class="sxs-lookup"><span data-stu-id="bc12b-243">Additionally, the Microsoft 365 admin center does not provide a way to directly print the displayed list.</span></span>
  
<span data-ttu-id="bc12b-p130">К счастью, с помощью PowerShell в Office 365 можно не только отобразить список, но и сохранить его в файл, который легко импортировать в Excel. Ниже приведен пример команды, позволяющей сохранить пользовательские данные Skype для бизнеса Online в файл с разделителями-запятыми (CSV-файл), который легко импортировать в виде таблицы в лист Excel.</span><span class="sxs-lookup"><span data-stu-id="bc12b-p130">Fortunately, you can use Office 365 PowerShell to not only display the list, but save it to a file that can be easily imported into Excel. Here is an example command to save Skype for Business Online user data to a comma-separated values (CSV) file, a file that can be easily imported as a table in an Excel worksheet:</span></span>
  
```powershell
Get-CsOnlineUser | Select DisplayName, UserPrincipalName, UsageLocation | Export-Csv -Path "C:\Logs\SfBUsers.csv" -NoTypeInformation
```

<span data-ttu-id="bc12b-246">Ниже приведен пример отображения.</span><span class="sxs-lookup"><span data-stu-id="bc12b-246">Here is an example of the display:</span></span>
  
![Пример таблицы с данными пользователей Skype для бизнеса, импортированной на лист Excel и сохраненной в формате файла данных с разделителями-запятыми (CSV).](media/o365-powershell-data-in-excel.png)
  
> [!TIP]
>  <span data-ttu-id="bc12b-248">Эта команда PowerShell для Office 365 возвращает список всех пользователей Skype для бизнеса Online в текущей подписке Office 365 (**Get-CsOnlineUser**), но отображает только имя, имя участника (UPN) и местонахождение пользователей (**Select DisplayName, UserPrincipalName, UsageLocation**), после чего сохраняет эту информацию в CSV-файле C:\\Logs\\SfBUsers.csv (**Export-Csv -Path "C:\\Logs\\SfBUsers.csv" -NoTypeInformation**).</span><span class="sxs-lookup"><span data-stu-id="bc12b-248">The interpretation of this Office 365 PowerShell command is: Get all of the Skype for Business Online users in the current Office 365 subscription ( **Get-CsOnlineUser** ), obtain only the user name, UPN, and location ( **Select DisplayName, UserPrincipalName, UsageLocation** ), and then save that information in CSV file named C:\\Logs\\SfBUsers.csv ( **Export-Csv -Path "C:\\Logs\\SfBUsers.csv" -NoTypeInformation** ).</span></span>
  
<span data-ttu-id="bc12b-p131">PowerShell также позволяет сохранить этот список в виде XML-файла или HTML-страницы. Кроме того, с помощью дополнительных команд PowerShell вы можете сохранить данные непосредственно в файл Excel, используя необходимое форматирование.</span><span class="sxs-lookup"><span data-stu-id="bc12b-p131">You can also use options to save this list as an XML file or as an HTML page. In fact, with additional PowerShell commands, you could save it directly as an Excel file, with any custom formatting you desire.</span></span> 
  
<span data-ttu-id="bc12b-p132">Список, возвращенный командой PowerShell в Office 365, можно также отправить непосредственно на принтер, используемый по умолчанию в Windows. Вот пример необходимой команды:</span><span class="sxs-lookup"><span data-stu-id="bc12b-p132">You can also send the output of an Office 365 PowerShell command that displays a list directly to the default printer in Windows. Here is an example command:</span></span>
  
```powershell
Get-CsOnlineUser | Select DisplayName, UserPrincipalName, UsageLocation | Out-Printer
```

<span data-ttu-id="bc12b-253">Ниже показано, как будет выглядеть напечатанный документ.</span><span class="sxs-lookup"><span data-stu-id="bc12b-253">Here's what your printed document will look like:</span></span>
  
![Пример документа, напечатанного напрямую на стандартном принтере в Windows в результате выполнения команды PowerShell для Office 365.](media/o365-powershell-printed-data.png)
  
> [!TIP]
>  <span data-ttu-id="bc12b-255">Эта команда PowerShell возвращает список всех пользователей Skype для бизнеса Online в текущей подписке Office 365, но отображает только имя, имя участника (UPN) и расположение пользователей, после чего отправляет эту информацию на стандартный принтер Windows (**Out-Printer**).</span><span class="sxs-lookup"><span data-stu-id="bc12b-255">The interpretation of this Office 365 PowerShell command is:  Get all of the Skype for Business Online users in the current Office 365 subscription, obtain only the user name, UPN, and location, and then send that information to the default Windows printer ( **Out-Printer** ).</span></span>
  
<span data-ttu-id="bc12b-256">Распечатанный документ имеет то же простое форматирование, что и сведения, отображаемые в окне командной строки PowerShell для Office 365. Чтобы получить рабочую печатную копию, просто добавьте **| Out-Printer** в конец команды PowerShell для Office 365, которую вы создали, чтобы отобразить нужные данные.</span><span class="sxs-lookup"><span data-stu-id="bc12b-256">The printed document has the same simple formatting as the display within the Office 365 PowerShell command window, but once you have created an Office 365 PowerShell command to list what you need, you just add **| Out-Printer** to the end of the command to get a hard copy to work from.</span></span>
  
## <a name="office-365-powershell-lets-you-manage-across-server-products"></a><span data-ttu-id="bc12b-257">PowerShell для Office 365 позволяет управлять различными серверными продуктами</span><span class="sxs-lookup"><span data-stu-id="bc12b-257">Office 365 PowerShell lets you manage across server products</span></span>

<span data-ttu-id="bc12b-p133">Различные компоненты, составляющие Office 365:, предназначены для совместной работы. Предположим, вы добавляете нового пользователя в Office 365: и при этом указываете такие сведения, как его отдел и номер телефона. Эти сведения в дальнейшем будут доступны при получении доступа к данным пользователя с помощью любого из серверных продуктов Office 365:. Skype для бизнеса Online, Exchange или SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="bc12b-p133">The different components that make up Office 365 are designed to work together. For example, suppose you add a new user to Office 365 and, when you do, you specify such information as the user's department and phone number. That information will then be available if you access the user's information using any of the Office 365 server products: Skype for Business Online, Exchange, or SharePoint Online.</span></span>
  
<span data-ttu-id="bc12b-p134">Это общие сведения, распространяющиеся на набор продуктов. Сведения о конкретных продуктах, например информация о почтовом ящике Exchange пользователя, обычно недоступны во всех продуктах набора. Например, если вы хотите знать, включен ли почтовый ящик пользователя, то эти сведения доступны только в Центре администрирования Exchange.</span><span class="sxs-lookup"><span data-stu-id="bc12b-p134">But that's for common information that spans the suite of products. Product-specific information-for example, information about a user's Exchange mailbox-is typically not available across the suite. For example, if you want to know if a user's mailbox is enabled or not, that information is available only in the Exchange Admin center.</span></span> 
  
<span data-ttu-id="bc12b-264">Предположим, вы хотите создать отчет со следующим сведениями обо всех пользователях:</span><span class="sxs-lookup"><span data-stu-id="bc12b-264">Suppose you'd like to make a report that shows the following information for all your users:</span></span>
  
- <span data-ttu-id="bc12b-265">краткое имя пользователя;</span><span class="sxs-lookup"><span data-stu-id="bc12b-265">The user's display name</span></span>
    
- <span data-ttu-id="bc12b-266">наличие у пользователя лицензии на Office 365:;</span><span class="sxs-lookup"><span data-stu-id="bc12b-266">Whether the user is licensed for Office 365</span></span>
    
- <span data-ttu-id="bc12b-267">включен ли почтовый ящик Exchange пользователя;</span><span class="sxs-lookup"><span data-stu-id="bc12b-267">Whether the user's Exchange mailbox has been enabled</span></span>
    
- <span data-ttu-id="bc12b-268">включено ли для пользователя приложение Skype для бизнеса Online.</span><span class="sxs-lookup"><span data-stu-id="bc12b-268">Whether the user is enabled for Skype for Business Online</span></span>
    
<span data-ttu-id="bc12b-269">В настоящее время вы не можете использовать центр администрирования Microsoft 365 для простого создания такого отчета.</span><span class="sxs-lookup"><span data-stu-id="bc12b-269">You currently cannot use the Microsoft 365 admin center to easily produce such a report.</span></span> <span data-ttu-id="bc12b-270">Вместо этого необходимо создать отдельный документ для хранения информации, например листа Excel, и получить все имена пользователей и сведения о лицензировании из центра администрирования Microsoft 365, получить сведения о почтовом ящике из центра администрирования Exchange, получить Skype для Сведения о бизнес-сети из центра администрирования Skype для бизнеса Online, а затем выполните разбор и объединение этих сведений.</span><span class="sxs-lookup"><span data-stu-id="bc12b-270">Instead, you'll have to create a separate document to store the information, like an Excel worksheet, and get all the user names and licensing information from the Microsoft 365 admin center, get mailbox information from the Exchange Admin center, get Skype for Business Online information from the Skype for Business Online Admin center, and then collate and combine that information.</span></span>
  
<span data-ttu-id="bc12b-271">Вместо этого можно запустить сценарий PowerShell в Office 365, который составит для вас этот отчет.</span><span class="sxs-lookup"><span data-stu-id="bc12b-271">The alternative is to use an Office 365 PowerShell script to compile that report for you.</span></span>
  
<span data-ttu-id="bc12b-p136">Следующий пример сценария сложнее приведенных выше команд. Но он показывает преимущества PowerShell в Office 365 при создании представления данных, которое очень сложно получить другим способом. Вот сценарий, с помощью которого можно составить и отобразить необходимый список:</span><span class="sxs-lookup"><span data-stu-id="bc12b-p136">The following example script is more complicated than the commands you have seen so far in this article. But, it shows the potential of using Office 365 PowerShell to create views of information that are very difficult to do otherwise. Here is the script that can compile and display the needed list:</span></span>
  
```powershell
$x = Get-MsolUser

foreach ($i in $x)
    {
      $y = Get-Mailbox -Identity $i.UserPrincipalName
      $i | Add-Member -MemberType NoteProperty -Name IsMailboxEnabled -Value $y.IsMailboxEnabled

      $y = Get-CsOnlineUser -Identity $i.UserPrincipalName
      $i | Add-Member -MemberType NoteProperty -Name EnabledForSfB -Value $y.Enabled
    }

$x | Select DisplayName, IsLicensed, IsMailboxEnabled, EnabledforSfB
```

<span data-ttu-id="bc12b-275">Ниже приведен пример отображения.</span><span class="sxs-lookup"><span data-stu-id="bc12b-275">Here is an example of the display:</span></span>
  
```powershell
DisplayName             IsLicensed   IsMailboxEnabled   EnabledForSfB
-----------             ----------   ----------------   --------------
Bonnie Kearney          True         True               True
Fabrice Canel           True         True               True
Brian Johnson           False        True               False
Anne Wallace            True         True               True
Alex Darrow             True         True               True
David Longmuir          True         True               True
Katy Jordan             False        True               False
Molly Dempsey           False        True               False
```

<span data-ttu-id="bc12b-276">Этот сценарий PowerShell для Office 365 интерпретируется так:</span><span class="sxs-lookup"><span data-stu-id="bc12b-276">The interpretation of this Office 365 PowerShell script is:</span></span>  
- <span data-ttu-id="bc12b-277">Возвращается список всех пользователей в текущей подписке Office 365, после чего сведения сохраняются в переменной $x (**$x = Get-MsolUser**).</span><span class="sxs-lookup"><span data-stu-id="bc12b-277">Get all of the users in the current Office 365 subscription and store the information in a variable named $x ( **$x = Get-MsolUser** ).</span></span>
- <span data-ttu-id="bc12b-278">Запускается цикл для всех пользователей в переменной $x (**foreach ($i in $x)**).</span><span class="sxs-lookup"><span data-stu-id="bc12b-278">Start a loop that runs over all the users in the variable named $x ( **foreach ($i in $x)** ).</span></span>  
- <span data-ttu-id="bc12b-279">Определяется переменная $y, в которой сохраняются сведения о почтовом ящике пользователя (**$y = Get-Mailbox -Identity $i.UserPrincipalName**).</span><span class="sxs-lookup"><span data-stu-id="bc12b-279">Define a variable named $y and store the user's mailbox information in it ( **$y = Get-Mailbox -Identity $i.UserPrincipalName** ).</span></span>
- <span data-ttu-id="bc12b-280">К сведениям о пользователе добавляется новое свойство IsMailBoxEnabled, которое задается как значение свойства IsMailBoxEnabled почтового ящика пользователя (**$i | Add-Member -MemberType NoteProperty -Name IsMailboxEnabled -Value $y.IsMailboxEnabled**).</span><span class="sxs-lookup"><span data-stu-id="bc12b-280">Add a new property to the user information named IsMailBoxEnabled and set it to the value of the IsMailBoxEnabled property of the user's mailbox ( **$i | Add-Member -MemberType NoteProperty -Name IsMailboxEnabled -Value $y.IsMailboxEnabled** ).</span></span>
- <span data-ttu-id="bc12b-281">Определяется переменная $y, в которой сохраняются данные Skype для бизнеса Online пользователя (**$y = Get-CsOnlineUser -Identity $i.UserPrincipalName**).</span><span class="sxs-lookup"><span data-stu-id="bc12b-281">Define a variable named $y and store the user's Skype for Business Online information in it ( **$y = Get-CsOnlineUser -Identity $i.UserPrincipalName** ).</span></span>
- <span data-ttu-id="bc12b-282">К сведениям о пользователе добавляется новое свойство EnabledForSfB, которое задается как значение свойства Enabled для данных Skype для бизнеса Online пользователя (**$i | Add-Member -MemberType NoteProperty -Name EnabledForSfB -Value $y.Enabled**).</span><span class="sxs-lookup"><span data-stu-id="bc12b-282">Add a new property to the user information named EnabledForSfB and set it to the value of the Enabled property of the user's Skype for Business Online information ( **$i | Add-Member -MemberType NoteProperty -Name EnabledForSfB -Value $y.Enabled** ).</span></span>
- <span data-ttu-id="bc12b-283">Отображается список пользователей, в котором указаны только их имена, наличие лицензии и два новых свойства, которые указывают, включен ли почтовый ящик пользователей и могут ли они использовать Skype для бизнеса Online (**$x | Select DisplayName, IsLicensed, IsMailboxEnabled, EnabledforSfB**).</span><span class="sxs-lookup"><span data-stu-id="bc12b-283">Display the list of users, but include only their name, whether they are licensed, and the two new properties that indicate whether their mailbox is enabled and whether they are enabled for Skype for Business Online ( **$x | Select DisplayName, IsLicensed, IsMailboxEnabled, EnabledforSfB** ).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="bc12b-284">См. также</span><span class="sxs-lookup"><span data-stu-id="bc12b-284">See also</span></span>

[<span data-ttu-id="bc12b-285">Начало работы с PowerShell для Office 365</span><span class="sxs-lookup"><span data-stu-id="bc12b-285">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
  
[<span data-ttu-id="bc12b-286">Управление учетными записями пользователей, лицензиями и группами с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="bc12b-286">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="bc12b-287">Использование Windows PowerShell для создания отчетов в Office 365</span><span class="sxs-lookup"><span data-stu-id="bc12b-287">Use Windows PowerShell to create reports in Office 365</span></span>](use-windows-powershell-to-create-reports-in-office-365.md)

