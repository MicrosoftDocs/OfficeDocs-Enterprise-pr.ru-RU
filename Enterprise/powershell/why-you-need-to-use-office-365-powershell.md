---
title: Причины использования Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 03/11/2019
audience: ITPro
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Office_Other
ms.assetid: b3209b1a-40c7-4ede-8e78-8a88bb2adc8a
description: 'Сводка: в этой статье рассказывается, почему необходимо использовать PowerShell в Office 365 для управления Office 365:: в ряде случаев это может быть более эффективно, а в других  вызвано необходимостью.'
ms.openlocfilehash: 66782a9165c76c7e1d506e40fa1cacd6db0c6724
ms.sourcegitcommit: f316aef1c122f8eb25c43a56bc894c4aa61c8e0c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2019
ms.locfileid: "38747448"
---
# <a name="why-you-need-to-use-office-365-powershell"></a><span data-ttu-id="71dbc-103">Причины использования Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="71dbc-103">Why you need to use Office 365 PowerShell</span></span>

<span data-ttu-id="71dbc-104">С помощью центра администрирования Microsoft 365 вы можете не только управлять своими учетными записями пользователей и лицензиями Office 365, но также можете управлять серверными продуктами Office 365: Exchange, Skype для бизнеса Online и SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="71dbc-104">With the Microsoft 365 admin center, you can not only manage your Office 365 user accounts and licenses, but you can also manage your Office 365 server products: Exchange, Skype for Business Online, and SharePoint Online.</span></span> <span data-ttu-id="71dbc-105">Тем не менее, вы также можете управлять этими элементами с помощью команд PowerShell для Office 365, используя преимущества командной строки и язык сценариев для ускорения, автоматизации и дополнительной возможности.</span><span class="sxs-lookup"><span data-stu-id="71dbc-105">However, you can also manage these elements with Office 365 PowerShell commands, taking advantage of a command-line and scripting language environment for speed, automation, and additional capability.</span></span>
  
<span data-ttu-id="71dbc-106">В этой статье мы покажем вам эти способы использования PowerShell в Office 365 для управления Office 365:.</span><span class="sxs-lookup"><span data-stu-id="71dbc-106">In this article, we'll show you these ways in which you can use Office 365 PowerShell to manage Office 365.</span></span>
  
- <span data-ttu-id="71dbc-107">Office 365 PowerShell может открыть дополнительные сведения, которые не отображаются в центре администрирования Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="71dbc-107">Office 365 PowerShell can reveal additional information that you cannot see with the Microsoft 365 admin center</span></span>
    
- <span data-ttu-id="71dbc-108">Некоторые компоненты Office 365 можно настроить только с помощью PowerShell Office 365</span><span class="sxs-lookup"><span data-stu-id="71dbc-108">Office 365 has features that you can only configure by using Office 365 PowerShell</span></span>
    
- <span data-ttu-id="71dbc-109">PowerShell в Office 365 идеально подходит для выполнения групповых операций.</span><span class="sxs-lookup"><span data-stu-id="71dbc-109">Office 365 PowerShell is great at performing bulk operations</span></span>
    
- <span data-ttu-id="71dbc-110">Возможности фильтрации данных с помощью PowerShel Office 365</span><span class="sxs-lookup"><span data-stu-id="71dbc-110">Office 365 PowerShell is great at filtering data</span></span>
    
- <span data-ttu-id="71dbc-111">Упрощение печати или сохранения данных с помощью PowerShell Office 365</span><span class="sxs-lookup"><span data-stu-id="71dbc-111">Office 365 PowerShell makes it easy to print or save data</span></span>
    
- <span data-ttu-id="71dbc-112">PowerShell для Office 365 позволяет управлять различными серверными продуктами</span><span class="sxs-lookup"><span data-stu-id="71dbc-112">Office 365 PowerShell lets you manage across server products</span></span>
    
<span data-ttu-id="71dbc-p102">Приступая к чтению статьи, необходимо понимать, что PowerShell в Office 365 — это набор модулей для Windows PowerShell, среды командной строки для служб и платформ Windows. Эта среда создает язык командной строки, который можно расширить с помощью дополнительных модулей и который позволяет выполнять как простые, так и сложные команды и скрипты. Например, после установки модулей PowerShell в Office 365 и подключения подписки на Office 365 вы можете выполнить следующую команду, чтобы получить список всех почтовых ящиков пользователей для Microsoft Exchange Online:</span><span class="sxs-lookup"><span data-stu-id="71dbc-p102">Before you begin, understand that Office 365 PowerShell is a set of modules for Windows PowerShell, a command-line environment for Windows-based services and platforms. This environment creates a command shell language that can be extended with additional modules and provides a way to execute simple or complex commands or scripts. For example, after you install the Office 365 PowerShell modules and connect to your Office 365 subscription, you can run this command to list all of the user mailboxes for Microsoft Exchange Online:</span></span>
  
```powershell
Get-Mailbox
```

<span data-ttu-id="71dbc-116">Вы также можете легко выполнить список почтовых ящиков с помощью центра администрирования Microsoft 365, но подсчитать количество элементов во всех списках всех сайтов для всех веб-приложений нелегко.</span><span class="sxs-lookup"><span data-stu-id="71dbc-116">Getting the list of mailboxes can also be easily done using the Microsoft 365 admin center, but counting the number of items in all of the lists for all of the sites for all of your web apps cannot be easily done.</span></span>
  
<span data-ttu-id="71dbc-117">Обратите внимание на то, что Office 365 PowerShell предназначен для расширения возможностей управления Office 365, а не для замены центра администрирования Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="71dbc-117">Please note that Office 365 PowerShell is designed to augment and enhance your ability to manage Office 365, not to replace the Microsoft 365 admin center.</span></span> <span data-ttu-id="71dbc-118">Как администратор Office 365:, вы должны владеть по крайней мере основами работы с Office 365: PowerShell, так как некоторые процедуры настройки можно выполнить только с помощью команд PowerShell в Office 365.</span><span class="sxs-lookup"><span data-stu-id="71dbc-118">As an Office 365 administrator, you must become at least comfortable with using Office 365 PowerShell because there are some configuration procedures that can only be done with Office 365 PowerShell commands.</span></span> <span data-ttu-id="71dbc-119">В таких случаях вы должны уметь:</span><span class="sxs-lookup"><span data-stu-id="71dbc-119">In these cases, you will be required to understand how to:</span></span>
  
- <span data-ttu-id="71dbc-120">устанавливать модули PowerShell в Office 365 (выполняется только один раз для компьютера администратора);</span><span class="sxs-lookup"><span data-stu-id="71dbc-120">Install the Office 365 PowerShell modules (done only once for each administrator computer).</span></span>
    
- <span data-ttu-id="71dbc-121">подключаться к своей подписке Office 365: (выполняется один раз для каждого сеанса PowerShell);</span><span class="sxs-lookup"><span data-stu-id="71dbc-121">Connect to your Office 365 subscription (done once for each PowerShell session).</span></span>
    
- <span data-ttu-id="71dbc-122">собирать информацию для выполнения необходимых команд PowerShell в Office 365;</span><span class="sxs-lookup"><span data-stu-id="71dbc-122">Gather the information needed to run the required Office 365 PowerShell commands.</span></span>
    
- <span data-ttu-id="71dbc-123">успешно выполнять команды PowerShell в Office 365.</span><span class="sxs-lookup"><span data-stu-id="71dbc-123">Run the Office 365 PowerShell commands successfully.</span></span>
    
<span data-ttu-id="71dbc-p104">Овладев этими основными навыками, вам не обязательно отображать список пользователей почтовых ящиков с помощью команды **Get-Mailbox** или учиться создавать команду, подобную предыдущей, для подсчета всех элементов во всех списках для всех сайтов всех веб-приложений. Корпорация Майкрософт и сообщество администраторов Office 365: могут помочь вам в этом при необходимости.</span><span class="sxs-lookup"><span data-stu-id="71dbc-p104">After learning these basic skills, you are not required to list your mailbox users with **Get-Mailbox** command, nor are you required to understand how to create a new command like the previous one to count all the items in all the lists for all of the sites for all of your web apps. Microsoft and the community of Office 365 administrators can help you with that as needed.</span></span>
  
## <a name="office-365-powershell-can-reveal-additional-information-that-you-cannot-see-with-the-microsoft-365-admin-center"></a><span data-ttu-id="71dbc-126">Office 365 PowerShell может открыть дополнительные сведения, которые не отображаются в центре администрирования Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="71dbc-126">Office 365 PowerShell can reveal additional information that you cannot see with the Microsoft 365 admin center</span></span>

<span data-ttu-id="71dbc-127">В центре администрирования Microsoft 365 отображается большое количество полезной информации, но это не означает, что на ней отображаются все возможные сведения, которые хранятся в Office 365 для пользователей, лицензий, почтовых ящиков и сайтов.</span><span class="sxs-lookup"><span data-stu-id="71dbc-127">The Microsoft 365 admin center displays a lot of useful information, but that doesn't mean that it displays all the possible information that Office 365 stores on users, licenses, mailboxes, and sites.</span></span> <span data-ttu-id="71dbc-128">Ниже приведен пример для **пользователей и групп** в центре администрирования Microsoft 365:</span><span class="sxs-lookup"><span data-stu-id="71dbc-128">Here is an example for **users and groups** in the Microsoft 365 admin center:</span></span>
  
![Пример отображения пользователей и групп в центре администрирования Microsoft 365.](media/o365-powershell-users-and-groups.png)
  
<span data-ttu-id="71dbc-130">Для многих целей отображаются сведения, которые необходимо знать.</span><span class="sxs-lookup"><span data-stu-id="71dbc-130">For many purposes, this displays the information you need to know.</span></span> <span data-ttu-id="71dbc-131">Однако бывают случаи, когда вам требуется больше времени.</span><span class="sxs-lookup"><span data-stu-id="71dbc-131">However, there are times when you need more.</span></span> <span data-ttu-id="71dbc-132">Например, лицензирование Office 365 (и возможности Office 365, доступные пользователю) зависят от географического расположения этого пользователя.</span><span class="sxs-lookup"><span data-stu-id="71dbc-132">For example, Office 365 licensing (and the Office 365 features available to a user) depend in part on that user's geographic location.</span></span> <span data-ttu-id="71dbc-133">Политики и функции, которые вы можете расширить для пользователя, который живет в США, могут отличаться от политик и функций, которые можно расширить для пользователя, который живет в Индии или в Бельгии.</span><span class="sxs-lookup"><span data-stu-id="71dbc-133">The policies and features you can extend to a user who lives in the United States might not be the same as the policies and features you can extend to a user who lives in India or in Belgium.</span></span> <span data-ttu-id="71dbc-134">С помощью центра администрирования Microsoft 365 вы можете определить географическое расположение пользователя, выполнив указанные ниже действия.</span><span class="sxs-lookup"><span data-stu-id="71dbc-134">You can use the Microsoft 365 admin center to determine a user's geographic location with these steps:</span></span>
  
1. <span data-ttu-id="71dbc-135">Дважды щелкните **отображаемое имя** пользователя.</span><span class="sxs-lookup"><span data-stu-id="71dbc-135">Double-click the user's **Display Name**.</span></span>
    
2. <span data-ttu-id="71dbc-136">На панели отображения свойств пользователя щелкните **сведения**.</span><span class="sxs-lookup"><span data-stu-id="71dbc-136">In the user properties display pane, click **details**.</span></span>
    
3. <span data-ttu-id="71dbc-137">В окне сведений щелкните **дополнительные сведения**.</span><span class="sxs-lookup"><span data-stu-id="71dbc-137">In the details display, click **additional details**.</span></span>
    
4. <span data-ttu-id="71dbc-138">Прокрутите окно вниз до заголовка **Страна или регион**.</span><span class="sxs-lookup"><span data-stu-id="71dbc-138">Scroll down until you see the heading **Country or region**:</span></span>
    
     ![Пример сведений о регионе для пользователя в центре администрирования Microsoft 365.](media/o365-powershell-usage-location.png)
  
5. <span data-ttu-id="71dbc-140">Запишите отображаемое имя и местонахождение пользователя на лист бумаги или скопируйте и вставьте их в Блокнот.</span><span class="sxs-lookup"><span data-stu-id="71dbc-140">Write the user's display name and location on a piece of paper, or copy and paste it into Notepad.</span></span> 
    
<span data-ttu-id="71dbc-p107">Эту процедуру необходимо повторить для каждого пользователя. Если пользователей очень много, эта задача может показаться утомительной. В PowerShell в Office 365 вы можете отобразить эти сведения обо всех пользователях с помощью следующей команды:</span><span class="sxs-lookup"><span data-stu-id="71dbc-p107">You must repeat this procedure for each user. For many users, this can be a tedious task. With Office 365 PowerShell, you can display this information for all of your users with the following command:</span></span>
  
```powershell
Get-MsolUser | Select DisplayName, UsageLocation
```

> [!NOTE]
> <span data-ttu-id="71dbc-144">Для использования этой команды необходимо установить [модуль Windows Azure Active Directory](https://docs.microsoft.com/powershell/module/Azuread/?view=azureadps-2.0).</span><span class="sxs-lookup"><span data-stu-id="71dbc-144">This command requires you to install the [Windows Azure Active Directory module](https://docs.microsoft.com/powershell/module/Azuread/?view=azureadps-2.0).</span></span> 
  
<span data-ttu-id="71dbc-145">Ниже приведен пример отображения.</span><span class="sxs-lookup"><span data-stu-id="71dbc-145">Here is an example of the display:</span></span>
  
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
>  <span data-ttu-id="71dbc-146">Эта команда PowerShell возвращает список всех пользователей в текущей подписке Office 365 (**Get-MsolUser**), но отображает только имя и местонахождение каждого пользователя (**Select DisplayName, UsageLocation**).</span><span class="sxs-lookup"><span data-stu-id="71dbc-146">The interpretation of this Office 365 PowerShell command is: Get all of the users in the current Office 365 subscription ( **Get-MsolUser** ), but only display the name and location for each user ( **Select DisplayName, UsageLocation** ).</span></span>
  
<span data-ttu-id="71dbc-p108">Так как PowerShell в Office 365 поддерживает язык командной оболочки, вы можете выполнять дополнительные действия над информацией, полученной с помощью команды **Get-MSolUser**. Например, вы можете отсортировать пользователей по их расположениям и объединить в группы пользователей из Бразилии, США, и т. д. Это можно сделать с помощью указанной ниже команды.</span><span class="sxs-lookup"><span data-stu-id="71dbc-p108">Because Office 365 PowerShell supports a command shell language, you can further manipulate the information obtained from the **Get-MSolUser** command. For example, maybe you'd like to sort these users by their location, grouping all the Brazilian users together, all the United States users together, etc. Here is the command:</span></span>
  
```powershell
Get-MsolUser | Select DisplayName, UsageLocation | Sort UsageLocation, DisplayName
```

<span data-ttu-id="71dbc-149">Ниже приведен пример отображения.</span><span class="sxs-lookup"><span data-stu-id="71dbc-149">Here is an example of the display:</span></span>
  
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
>  <span data-ttu-id="71dbc-150">Эта команда PowerShell возвращает список всех пользователей в текущей подписке Office 365, но отображает только имя и местонахождение каждого пользователя. Список сортируется сначала по местонахождению, а затем по имени (**Sort UsageLocation, DisplayName**).</span><span class="sxs-lookup"><span data-stu-id="71dbc-150">The interpretation of this Office 365 PowerShell command is: Get all of the users in the current Office 365 subscription, but only display the name and location for each user and sort them first by their location, and then their names ( **Sort UsageLocation, DisplayName** ).</span></span>
  
<span data-ttu-id="71dbc-p109">Можно также использовать дополнительные фильтры. Например, если нужно просмотреть сведения о пользователях, находящихся в Бразилии, используйте следующую команду:</span><span class="sxs-lookup"><span data-stu-id="71dbc-p109">You can also employ additional filtering. For example, if you only want to see information about users based in Brazil, use this command:</span></span>
  
```powershell
Get-MsolUser | Where {$_.UsageLocation -eq "BR"} | Select DisplayName, UsageLocation 
```

<span data-ttu-id="71dbc-153">Ниже приведен пример отображения.</span><span class="sxs-lookup"><span data-stu-id="71dbc-153">Here is an example of the display:</span></span>
  
```powershell
DisplayName                                           UsageLocation
-----------                                           -------------
David Longmuir                                        BR
Fabrice Canel                                         BR
```

> [!TIP]
>  <span data-ttu-id="71dbc-154">Эта команда PowerShell возвращает список всех пользователей в текущей подписке Office 365, которые находятся в Бразилии (**Where {$\_.UsageLocation -eq "BR"}**), а затем отображает имя и местонахождение каждого пользователя.</span><span class="sxs-lookup"><span data-stu-id="71dbc-154">The interpretation of this Office 365 PowerShell command is: Get all of the users in the current Office 365 subscription whose location is Brazil ( **Where {$\_.UsageLocation -eq "BR"}** ), then display the name and location for each user.</span></span>
  
 <span data-ttu-id="71dbc-155">**Небольшое примечание относительно более крупных доменов**</span><span class="sxs-lookup"><span data-stu-id="71dbc-155">**A Quick Note Regarding Larger Domains**</span></span>
  
<span data-ttu-id="71dbc-p110">Если у вас очень большой домен, включающий десятки тысяч пользователей, то использование некоторых сценариев, описанных в этой статье, может привести к так называемому "регулированию". Это будет означать, что вы одновременно выполняете слишком большое количество задач, для чего недостаточно мощности компьютера и пропускной способности сети. Поэтому крупным организациям может понадобиться разбить некоторые из этих команд PowerShell в Office 365 на две команды. Например, указанная ниже команда возвращает все учетные записи пользователей и отображает для каждой из них имя и расположение.</span><span class="sxs-lookup"><span data-stu-id="71dbc-p110">If you have a very large domain with tens of thousands of users, trying some of the examples we show in this article could lead to "throttling." That means that, based on things like computing power and available network bandwidth, you're trying to do a little too much at one time. Because of that, larger organizations might want to split some of these Office 365 PowerShell commands into two commands. For example, this one command returns all the user accounts and shows the name and location for each:</span></span>
  
```powershell
Get-MsolUser | Select DisplayName, UsageLocation
```

<span data-ttu-id="71dbc-p111">Она отлично подходит для небольших доменов. Тем не менее крупной организации может понадобиться разделить ее на две команды: одна команда будет использоваться для сохранения сведений об учетных записях пользователей в переменной, а другая  для отображения необходимой информации. Вот пример:</span><span class="sxs-lookup"><span data-stu-id="71dbc-p111">That works great for smaller domains. In a large organization, however, you might need to split that into two commands: one command to store the user account information in a variable and another command to display the needed information. Here is an example:</span></span>
  
```powershell
$x = Get-MsolUser
$x | Select DisplayName, UsageLocation
```


<span data-ttu-id="71dbc-163">Этот набор команд PowerShell для Office 365 интерпретируется так:</span><span class="sxs-lookup"><span data-stu-id="71dbc-163">The interpretation of this set of Office 365 PowerShell commands is:</span></span>
- <span data-ttu-id="71dbc-164">Возвращается список всех пользователей в текущей подписке Office 365, после чего сведения сохраняются в переменной $x (**$x = Get-MsolUser**).</span><span class="sxs-lookup"><span data-stu-id="71dbc-164">Get all of the users in the current Office 365 subscription and store the information in a variable named $x ( **$x = Get-MsolUser** ).</span></span>
- <span data-ttu-id="71dbc-165">Отображается содержимое переменной $x, которое включает в себя только имя и местонахождение каждого пользователя (**$x | Select DisplayName, UsageLocation**).</span><span class="sxs-lookup"><span data-stu-id="71dbc-165">Display the contents of the variable $x, but only include the name and location for each user ( **$x | Select DisplayName, UsageLocation** ).</span></span>
  
## <a name="office-365-has-features-that-you-can-only-configure-with-office-365-powershell"></a><span data-ttu-id="71dbc-166">Некоторые компоненты Office 365 можно настроить только с помощью PowerShell</span><span class="sxs-lookup"><span data-stu-id="71dbc-166">Office 365 has features that you can only configure with Office 365 PowerShell</span></span>

<span data-ttu-id="71dbc-167">Центр администрирования Microsoft 365 предназначен для обеспечения доступа к наиболее распространенным или осмысленным задачам администрирования, которые применяются к большинству пользователей.</span><span class="sxs-lookup"><span data-stu-id="71dbc-167">The Microsoft 365 admin center is intended to provide access to the most common or meaningful administrative tasks that apply to most people.</span></span> <span data-ttu-id="71dbc-168">Другими словами, центр администрирования Microsoft 365 был разработан таким образом, что стандартный администратор может использовать это средство для выполнения самых распространенных задач управления.</span><span class="sxs-lookup"><span data-stu-id="71dbc-168">In other words, the Microsoft 365 admin center was designed so that the typical administrator could use the tool to carry out the most common management tasks.</span></span> <span data-ttu-id="71dbc-169">Это определение означает, что существует несколько задач, которые невозможно выполнить с помощью центра администрирования Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="71dbc-169">By this definition, that means that there are some tasks that can't be completed by using the Microsoft 365 admin center.</span></span>
  
<span data-ttu-id="71dbc-170">Например, в Центр администрирования Skype для бизнеса Online используется несколько параметров для создания настраиваемых приглашений на собрания:</span><span class="sxs-lookup"><span data-stu-id="71dbc-170">For example, the Skype for Business Online Admin center provides a few options for creating custom meeting invitations:</span></span>
  
![Пример отображения настраиваемых приглашений на собрание в Центре администрирования Skype для бизнеса Online.](media/o365-powershell-meeting-invitation.png)
  
<span data-ttu-id="71dbc-p113">С помощью указанных ниже параметров приглашения на собрания можно сделать более персонализированными и профессиональными. Тем не менее, настройки собраний позволяют сделать больше, чем просто создать пользовательские приглашения. Например, по умолчанию собрания позволяют:</span><span class="sxs-lookup"><span data-stu-id="71dbc-p113">With these settings, you can add a touch of personalization and professionalism to meeting invitations. However, there's more to meeting configuration settings than simply creating custom meeting invitations. For example, by default, meetings allow:</span></span>
  
- <span data-ttu-id="71dbc-175">анонимным пользователям автоматически присоединяться к каждому собранию;</span><span class="sxs-lookup"><span data-stu-id="71dbc-175">Anonymous users to gain automatic entrance to each meeting.</span></span>
    
- <span data-ttu-id="71dbc-176">участникам записывать собрание;</span><span class="sxs-lookup"><span data-stu-id="71dbc-176">Attendees to record the meeting.</span></span>
    
- <span data-ttu-id="71dbc-177">обозначать всех пользователей из вашей организации докладчиками при их присоединении к собранию.</span><span class="sxs-lookup"><span data-stu-id="71dbc-177">All users from your organization to be designated as presenters when they join the meeting.</span></span>
    
<span data-ttu-id="71dbc-p114">Эти параметры недоступны в Центре администрирования Skype для бизнеса Online. Но ими можно управлять с помощью PowerShell в Office 365. Указанная ниже команда отключает эти три параметра.</span><span class="sxs-lookup"><span data-stu-id="71dbc-p114">These settings are not available from the Skype for Business Online Admin center. However, you can control them from Office 365 PowerShell. Here is a command that disables these three settings:</span></span>
  
```powershell
Set-CsMeetingConfiguration -AdmitAnonymousUsersByDefault $False -AllowConferenceRecording $False -DesignateAsPresenter "None"
```

> [!NOTE]
> <span data-ttu-id="71dbc-181">Для использования этой команды необходимо установить [модуль PowerShell для Skype для бизнеса Online](https://www.microsoft.com/download/details.aspx?id=39366).</span><span class="sxs-lookup"><span data-stu-id="71dbc-181">This command requires that you install the [Skype for Business Online PowerShell Module ](https://www.microsoft.com/download/details.aspx?id=39366).</span></span> 
  
> [!TIP]
>  <span data-ttu-id="71dbc-182">Эта команда PowerShell для Office 365 отключает разрешение для анонимных пользователям автоматически присоединяться к новым собраниям Skype для бизнеса Online (**Set-CsMeetingConfiguration**, **-AdmitAnonymousUsersByDefault $False**), отключает для участников возможность записывать эти собрания (**-AllowConferenceRecording $False**) и отменяет для всех пользователей в организации статус выступающего (**-DesignateAsPresenter "None"**).</span><span class="sxs-lookup"><span data-stu-id="71dbc-182">The interpretation of this Office 365 PowerShell command is: For the settings for new Skype for Business Online meetings ( **Set-CsMeetingConfiguration** ), disable allowing anonymous users to gain automatic entrance to meetings ( **-AdmitAnonymousUsersByDefault $False** ), disable the ability for attendees to record meetings ( **-AllowConferenceRecording $False** ), and do not designate all users from your organization as presenters ( **-DesignateAsPresenter "None"** ).</span></span>
  
<span data-ttu-id="71dbc-183">Если вы передумали и хотите восстановить эти настройки по умолчанию (т. е. включить их все), выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="71dbc-183">If you change your mind and want to restore these default settings (all of them enabled), run this command:</span></span>
  
```powershell
Set-CsMeetingConfiguration -AdmitAnonymousUsersByDefault $True -AllowConferenceRecording $True -DesignateAsPresenter "Company"
```

<span data-ttu-id="71dbc-p115">Это только один пример. Существуют и другие, поэтому вы как администратор Office 365: должны уметь без труда использовать команды PowerShell в Office 365.</span><span class="sxs-lookup"><span data-stu-id="71dbc-p115">This is just one example. There are others, which is why you, as an Office 365 administrator, need to be comfortable with running Office 365 PowerShell commands.</span></span>
  
## <a name="office-365-powershell-is-great-at-carrying-out-bulk-operations"></a><span data-ttu-id="71dbc-186">PowerShell Office 365 идеально подходит для массовых операций</span><span class="sxs-lookup"><span data-stu-id="71dbc-186">Office 365 PowerShell is great at carrying out bulk operations</span></span>

<span data-ttu-id="71dbc-187">Историческось, что визуальные интерфейсы, такие как центр администрирования Microsoft 365, наиболее полезны, если вы выполняете одну операцию.</span><span class="sxs-lookup"><span data-stu-id="71dbc-187">Historically, visual interfaces like the Microsoft 365 admin center are most valuable when you have a single operation to perform.</span></span> <span data-ttu-id="71dbc-188">Например, если необходимо отключить одну учетную запись пользователя, вы можете использовать центр администрирования Microsoft 365 для быстрого обнаружения и снятия флажка.</span><span class="sxs-lookup"><span data-stu-id="71dbc-188">For example, if you need to disable one user account, you can use the Microsoft 365 admin center to quickly locate and clear a checkbox.</span></span> <span data-ttu-id="71dbc-189">Обычно это проще, чем выполнить аналогичную операцию в PowerShell в Office 365.</span><span class="sxs-lookup"><span data-stu-id="71dbc-189">This can be simpler than performing a similar operation in Office 365 PowerShell.</span></span>
  
<span data-ttu-id="71dbc-190">Но если вам нужно изменить множество вещей или некоторые из выбранных элементов в большом наборе других элементов, центр администрирования Microsoft 365 может оказаться неоптимальным.</span><span class="sxs-lookup"><span data-stu-id="71dbc-190">But if you have to change many things or some selected things within a large set of other things, the Microsoft 365 admin center might not be the best use of your time.</span></span> <span data-ttu-id="71dbc-191">Например, если необходимо изменить префикс для тысяч телефонных номеров или удалить определенного пользователя, Ken Myer со всех сайтов SharePoint Online, как это сделать в центре администрирования Microsoft 365?</span><span class="sxs-lookup"><span data-stu-id="71dbc-191">For example, if you had to change the prefix on thousands of phone numbers or you needed to remove a specific user, Ken Myer, from all of your SharePoint Online sites, how would you do that in the Microsoft 365 admin center?</span></span>
  
<span data-ttu-id="71dbc-192">Допустим, в последнем примере у вас есть несколько сотен сайтов SharePoint Online и вы даже не знаете, на каком из них зарегистрирован пользователь Ken Meyer.</span><span class="sxs-lookup"><span data-stu-id="71dbc-192">For the latter example, you have several hundred SharePoint Online sites and you don't know even know which ones of which Ken Meyer is a member.</span></span> <span data-ttu-id="71dbc-193">Это означает, что вам потребуется начать с центра администрирования Microsoft 365, а затем выполнить эту процедуру для каждого сайта:</span><span class="sxs-lookup"><span data-stu-id="71dbc-193">That means you'll have to start at the Microsoft 365 admin center and then perform this procedure for each site:</span></span>
  
1. <span data-ttu-id="71dbc-194">Щелкнуть **URL-адрес** сайта.</span><span class="sxs-lookup"><span data-stu-id="71dbc-194">Click the **URL** of the site.</span></span>
    
2. <span data-ttu-id="71dbc-195">В поле **свойств семейства веб-сайтов** щелкнуть ссылку **Адрес веб-сайта**, чтобы открыть сайт.</span><span class="sxs-lookup"><span data-stu-id="71dbc-195">In the **site collection properties** box, click the **Web Site Address** link to open the site.</span></span>
    
3. <span data-ttu-id="71dbc-196">На сайте нажать кнопку **Общий доступ**.</span><span class="sxs-lookup"><span data-stu-id="71dbc-196">On the site, click **Share**.</span></span>
    
4. <span data-ttu-id="71dbc-197">В диалоговом окне **Общий доступ** щелкнуть ссылку, чтобы показать всех пользователей с разрешениями для сайта:</span><span class="sxs-lookup"><span data-stu-id="71dbc-197">In the **Share** dialog box click the link that shows you all the users who have permissions to the site:</span></span>
    
     ![Пример просмотра участников сайта SharePoint Online в Центре администрирования SharePoint Online](media/o365-powershell-view-permissions.png)
  
5. <span data-ttu-id="71dbc-199">В диалоговом окне **Общий доступ предоставлен** нажать кнопку **Дополнительно**.</span><span class="sxs-lookup"><span data-stu-id="71dbc-199">In the **Shared With** dialog box, click **Advanced**.</span></span>
    
6. <span data-ttu-id="71dbc-200">Прокрутить список пользователей, найти и выбрать Кена Майера (если у него есть разрешения для сайта) и нажать кнопку **Удалить разрешения пользователя**.</span><span class="sxs-lookup"><span data-stu-id="71dbc-200">Scroll down the list of users, find and select Ken Myer (assuming he has permissions to the site), and then click **Remove User Permissions**.</span></span>
    
<span data-ttu-id="71dbc-201">Для нескольких сотен сайтов это может занять очень много времени.</span><span class="sxs-lookup"><span data-stu-id="71dbc-201">This can take a long time for several hundred sites.</span></span>
  
<span data-ttu-id="71dbc-202">Но есть и другой вариант: удалить пользователя Ken Myer со всех сайтов с помощью указанной ниже команды PowerShell в Office 365.</span><span class="sxs-lookup"><span data-stu-id="71dbc-202">The alternative is to use Office 365 PowerShell and the following command to remove Ken Myer from all of your sites:</span></span>
  
```powershell
Get-SPOSite | ForEach {Remove-SPOUser -Site $_.Url -LoginName "kenmyer@litwareinc.com"}
```

> [!NOTE]
> <span data-ttu-id="71dbc-203">Для использования этой команды необходимо [подключиться к PowerShell для SharePoint Online](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span><span class="sxs-lookup"><span data-stu-id="71dbc-203">This command requires that you install the [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span></span> 
  
> [!TIP]
>  <span data-ttu-id="71dbc-204">Эта команда PowerShell возвращает список всех сайтов SharePoint в текущей подписке Office 365 (**Get-SPOSite**) и удаляет пользователя Ken Meyer из списка зарегистрированных пользователей каждого сайта (**ForEach {Remove-SPOUser -Site $\_.Url -LoginName "kenmyer@litwareinc.com"}**).</span><span class="sxs-lookup"><span data-stu-id="71dbc-204">The interpretation of this Office 365 PowerShell command is:  Get all of the SharePoint sites in the current Office 365 subscription ( **Get-SPOSite** ) and for each site, remove Ken Meyer from the list of users who can access it ( **ForEach {Remove-SPOUser -Site $\_.Url -LoginName "kenmyer@litwareinc.com"}** ).</span></span>
  
<span data-ttu-id="71dbc-205">Так как мы указываем Office 365: удалить пользователя Ken Meyer с каждого сайта, включая те, к которым у него нет доступа, эта команда будет показывать ошибки для таких сайтов.</span><span class="sxs-lookup"><span data-stu-id="71dbc-205">Because we are telling Office 365 to remove Ken Meyer from every site, including those in which he does not have access, the display of this command will show errors for those sites in which he does not currently have access.</span></span> <span data-ttu-id="71dbc-206">В этой команде можно использовать дополнительное условие, чтобы пользователь Ken Meyer был удален только с тех сайтов, в списке учетных записей которых он содержится, но чтобы указанные ошибки не влияли на сами сайты.</span><span class="sxs-lookup"><span data-stu-id="71dbc-206">We can use an additional condition on this command to remove Key Meyer only from the sites that have him in their login list, but the listed errors cause no harm to the sites themselves.</span></span> <span data-ttu-id="71dbc-207">Выполнение этой команды может занять несколько минут, а не часов работы с сотнями сайтов в центре администрирования Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="71dbc-207">This command might take a few minutes to run against hundreds of sites, rather than hours of working through the Microsoft 365 admin center.</span></span>
  
<span data-ttu-id="71dbc-p120">Вот еще один пример массовой операции. Чтобы добавить пользователя Бонни Керни (Bonnie Kearney) — нового администратора SharePoint — на все сайты в организации, используйте следующую команду:</span><span class="sxs-lookup"><span data-stu-id="71dbc-p120">Here is another bulk operation example. Use this command to add Bonnie Kearney, a new SharePoint administrator, to all of the sites in the organization:</span></span>
  
```powershell
Get-SPOSite | ForEach {Add-SPOUser -Site $_.Url -LoginName "bkearney@litwareinc.com" -Group "Members"}
```

> [!TIP]
>  <span data-ttu-id="71dbc-210">Эта команда PowerShell возвращает список всех сайтов SharePoint в текущей подписке Office 365, а затем добавляет имя Bonnie Kearney в группу участников каждого сайта, чтобы разрешить этому пользователю соответствующий доступ (**ForEach {Add-SPOUser -Site $\_.Url -LoginName "bkearney@litwareinc.com" -Group "Members"}**).</span><span class="sxs-lookup"><span data-stu-id="71dbc-210">The interpretation of this Office 365 PowerShell command is:  Get all of the SharePoint sites in the current Office 365 subscription and for each site, allow Bonnie Kearney access by adding her login name to the Members group of the site ( **ForEach {Add-SPOUser -Site $\_.Url -LoginName "bkearney@litwareinc.com" -Group "Members"}** ).</span></span>
  
## <a name="office-365-powershell-is-great-at-filtering-data"></a><span data-ttu-id="71dbc-211">PowerShell для Office 365 позволяет фильтровать данные</span><span class="sxs-lookup"><span data-stu-id="71dbc-211">Office 365 PowerShell is great at filtering data</span></span>

<span data-ttu-id="71dbc-212">Центр администрирования Microsoft 365 предоставляет несколько различных способов фильтрации данных, чтобы быстро и легко находить целевое подмножество данных.</span><span class="sxs-lookup"><span data-stu-id="71dbc-212">The Microsoft 365 admin center provides several different ways to filter your data to quickly and easily locate a targeted subset of information.</span></span> <span data-ttu-id="71dbc-213">Например, Exchange упрощает фильтрацию практически любого свойства почтового ящика пользователя.</span><span class="sxs-lookup"><span data-stu-id="71dbc-213">For example, Exchange makes it easy to filter on practically any property of a user mailbox.</span></span> <span data-ttu-id="71dbc-214">Например, ниже приведен список почтовых ящиков всех пользователей, проживающих в городе Блумингтон:</span><span class="sxs-lookup"><span data-stu-id="71dbc-214">For example, here is the list of mailboxes for all the users who live in the city of Bloomington:</span></span>
  
![Пример расширенного поиска в центре администрирования Microsoft 365 для списка почтовых ящиков всех пользователей, проживающих в городе Блумингтон.](media/o365-powershell-advanced-search.png)
  
<span data-ttu-id="71dbc-p122">Кроме того, Центр администрирования Exchange позволяет сочетать различные условия фильтра. Например, можно найти почтовые ящики всех пользователей, проживающих в г. Блумингтон и работающих в отделе финансов.</span><span class="sxs-lookup"><span data-stu-id="71dbc-p122">The Exchange Admin center also lets you combine filter criteria. For example, you can find the mailboxes for all the people who live in Bloomington and who work in the Finance department.</span></span> 
  
<span data-ttu-id="71dbc-p123">Но возможности фильтрации в Центре администрирования Exchange ограничены. Например, вам может понадобиться найти почтовые ящики пользователей, проживающих в городах Блумингтон (Bloomington) или Сан-Диего (San Diego), или почтовые ящики всех пользователей, которые не проживают в городе Блумингтон.</span><span class="sxs-lookup"><span data-stu-id="71dbc-p123">However, there are limitations to what you can do in the Exchange Admin center. For example, maybe you'd like to find the mailboxes of people who live in Bloomington or San Diego, or the mailboxes for all the people who don't live in Bloomington.</span></span> 
  
<span data-ttu-id="71dbc-220">PowerShell в Office 365 позволяет получить список почтовых ящиков всех пользователей, проживающих в городах Блумингтон или Сан-Диего, с помощью указанной ниже команды.</span><span class="sxs-lookup"><span data-stu-id="71dbc-220">With Office 365 PowerShell, you can get a list of mailboxes for all the people who live in the cities of Bloomington or San Diego with this command:</span></span>
  
```powershell
Get-User | Where {$_.RecipientTypeDetails -eq "UserMailbox" -and ($_.City -eq "San Diego" -or $_.City -eq "Bloomington")} | Select DisplayName, City
```

<span data-ttu-id="71dbc-221">Ниже приведен пример отображения.</span><span class="sxs-lookup"><span data-stu-id="71dbc-221">Here is an example of the display:</span></span>
  
```powershell
DisplayName                              City
-----------                              ----
Alex Darrow                              San Diego
Bonnie Kearney                           San Diego
Julian Isla                              Bloomington
Rob Young                                Bloomington
```

> [!TIP]
>  <span data-ttu-id="71dbc-222">Эта команда PowerShell возвращает список всех пользователей в текущей подписке Office 365, имеющих почтовый ящик в городах Блумингтон или Сан-Диего (**Where {$\_.RecipientTypeDetails -eq "UserMailbox" -and ($\_.City -eq "San Diego" -or $\_.City -eq "Bloomington")}**), а затем отображает имя и город каждого из этих пользователей (**Select DisplayName, City**).</span><span class="sxs-lookup"><span data-stu-id="71dbc-222">The interpretation of this Office 365 PowerShell command is: Get all of the users in the current Office 365 subscription who have a mailbox in the cities of either San Diego or Bloomington ( **Where {$\_.RecipientTypeDetails -eq "UserMailbox" -and ($\_.City -eq "San Diego" -or $\_.City -eq "Bloomington")}** ), then display the name and city for each ( **Select DisplayName, City** ).</span></span>
  
<span data-ttu-id="71dbc-223">Чтобы отобразить список всех почтовых ящиков пользователей, проживающих в любом месте за исключением г. Блумингтон, используйте такую команду:</span><span class="sxs-lookup"><span data-stu-id="71dbc-223">To list all the mailboxes for people who live anywhere except Bloomington, here is the command:</span></span>
  
```powershell
Get-User | Where {$_.RecipientTypeDetails -eq "UserMailbox" -and $_.City -ne "Bloomington"} | Select DisplayName, City
```

<span data-ttu-id="71dbc-224">Ниже приведен пример отображения.</span><span class="sxs-lookup"><span data-stu-id="71dbc-224">Here is an example of the display:</span></span>
  
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
>  <span data-ttu-id="71dbc-225">Эта команда PowerShell возвращает список всех пользователей в текущей подписке Office 365, почтовый ящик которых расположен не в г. Блумингтон ( **Where {$\_.RecipientTypeDetails -eq "UserMailbox" -and $\_.City -ne "Bloomington"}** ), а затем отображает имя и город каждого из этих пользователей.</span><span class="sxs-lookup"><span data-stu-id="71dbc-225">The interpretation of this Office 365 PowerShell command is: Get all of the users in the current Office 365 subscription who have a mailbox not located in the city of Bloomington ( **Where {$\_.RecipientTypeDetails -eq "UserMailbox" -and $\_.City -ne "Bloomington"}** ), then display the name and city for each.</span></span>
  
<span data-ttu-id="71dbc-p124">Кроме того, в фильтрах PowerShell в Office 365 можно использовать подстановочные знаки для поиска соответствия с частью имени. Предположим, вы ищете учетную запись пользователя, но помните только, что его фамилия или Андерсон, или Хендерсон, или, может быть, Йоргенсон.</span><span class="sxs-lookup"><span data-stu-id="71dbc-p124">You can also use wildcard characters in your Office 365 PowerShell filters to match part of a name. For example, suppose you're looking for a user account, and all you can remember is that their last name was Anderson, or maybe Henderson, or maybe it was Jorgenson.</span></span>
  
<span data-ttu-id="71dbc-228">Вы можете проследить этого пользователя в центре администрирования Microsoft 365 с помощью средства поиска и выполнить три различных поиска:</span><span class="sxs-lookup"><span data-stu-id="71dbc-228">You could track down that user in the Microsoft 365 admin center by using the search tool and carrying out three different searches:</span></span>
  
- <span data-ttu-id="71dbc-229">*Андерсон*  ;</span><span class="sxs-lookup"><span data-stu-id="71dbc-229">One for  *Anderson*</span></span> 
    
- <span data-ttu-id="71dbc-230">*Хендерсон*  ;</span><span class="sxs-lookup"><span data-stu-id="71dbc-230">One for  *Henderson*</span></span> 
    
- <span data-ttu-id="71dbc-231">*Йоргенсон*  .</span><span class="sxs-lookup"><span data-stu-id="71dbc-231">One for  *Jorgenson*</span></span> 
    
<span data-ttu-id="71dbc-p125">Так как все три фамилии заканчиваются на "-сон", в PowerShell в Office 365 можно использовать команду для отображения всех пользователей, фамилия которых имеет такое окончание. Вот как это делается:</span><span class="sxs-lookup"><span data-stu-id="71dbc-p125">Because all three of these names end in "son", you can tell Office 365 PowerShell to display all the users whose name ends in "son". Here is the command:</span></span>
  
```powershell
Get-User -Filter '{LastName -like "*son"}'
```

> [!TIP]
>  <span data-ttu-id="71dbc-p126">Эта команда PowerShell для Office 365 возвращает список всех пользователей в текущей подписке Office 365, при этом используется фильтр, отображающий только пользователей, чьи фамилии заканчиваются на "son" (**-Filter '{LastName -like "\*son"}'**). Символ \* означает любой набор знаков, в этом случае букв в фамилии пользователя.</span><span class="sxs-lookup"><span data-stu-id="71dbc-p126">The interpretation of this Office 365 PowerShell command is: Get all of the users in the current Office 365 subscription, but use a filter that only lists the users whose last names end in "son" ( **-Filter '{LastName -like "\*son"}'** ). The \* stands for any set of characters, which are letters in the case of the user's last name.</span></span>
  
## <a name="office-365-powershell-makes-it-easy-to-print-or-save-data"></a><span data-ttu-id="71dbc-236">PowerShell для Office 365 упрощает печать и сохранение данных</span><span class="sxs-lookup"><span data-stu-id="71dbc-236">Office 365 PowerShell makes it easy to print or save data</span></span>

<span data-ttu-id="71dbc-237">Центр администрирования Microsoft 365 позволяет просматривать списки данных.</span><span class="sxs-lookup"><span data-stu-id="71dbc-237">The Microsoft 365 admin center lets you view lists of data.</span></span> <span data-ttu-id="71dbc-238">Ниже приведен пример, где в Центре администрирования Skype для бизнеса Online отображается список пользователей, для которых включено приложение Skype для бизнеса Online:</span><span class="sxs-lookup"><span data-stu-id="71dbc-238">Here is an example of the Skype for Business Online Admin center displaying a list of users who have been enabled for Skype for Business Online:</span></span>
  
![Пример Центра администрирования Skype для бизнеса Online со списком пользователей, для которых включен Skype для бизнеса Online.](media/o365-powershell-lync-users.png)
  
<span data-ttu-id="71dbc-240">Чтобы сохранить эти данные в файл, необходимо их скопировать и вставить в документ или лист Excel.</span><span class="sxs-lookup"><span data-stu-id="71dbc-240">To save that information to a file, you must copy and paste it into a document or Excel.</span></span> <span data-ttu-id="71dbc-241">В любом случае может потребоваться дополнительное форматирование копии.</span><span class="sxs-lookup"><span data-stu-id="71dbc-241">In either case, the copy might require additional formatting.</span></span> <span data-ttu-id="71dbc-242">Кроме того, центр администрирования Microsoft 365 не предоставляет возможности непосредственного вывода списка.</span><span class="sxs-lookup"><span data-stu-id="71dbc-242">Additionally, the Microsoft 365 admin center does not provide a way to directly print the displayed list.</span></span>
  
<span data-ttu-id="71dbc-p129">К счастью, с помощью PowerShell в Office 365 можно не только отобразить список, но и сохранить его в файл, который легко импортировать в Excel. Ниже приведен пример команды, позволяющей сохранить пользовательские данные Skype для бизнеса Online в файл с разделителями-запятыми (CSV-файл), который легко импортировать в виде таблицы в лист Excel.</span><span class="sxs-lookup"><span data-stu-id="71dbc-p129">Fortunately, you can use Office 365 PowerShell to not only display the list, but save it to a file that can be easily imported into Excel. Here is an example command to save Skype for Business Online user data to a comma-separated values (CSV) file, a file that can be easily imported as a table in an Excel worksheet:</span></span>
  
```powershell
Get-CsOnlineUser | Select DisplayName, UserPrincipalName, UsageLocation | Export-Csv -Path "C:\Logs\SfBUsers.csv" -NoTypeInformation
```

<span data-ttu-id="71dbc-245">Ниже приведен пример отображения.</span><span class="sxs-lookup"><span data-stu-id="71dbc-245">Here is an example of the display:</span></span>
  
![Пример таблицы с данными пользователей Skype для бизнеса, импортированной на лист Excel и сохраненной в формате файла данных с разделителями-запятыми (CSV).](media/o365-powershell-data-in-excel.png)
  
> [!TIP]
>  <span data-ttu-id="71dbc-247">Эта команда PowerShell для Office 365 возвращает список всех пользователей Skype для бизнеса Online в текущей подписке Office 365 (**Get-CsOnlineUser**), но отображает только имя, имя участника (UPN) и местонахождение пользователей (**Select DisplayName, UserPrincipalName, UsageLocation**), после чего сохраняет эту информацию в CSV-файле C:\\Logs\\SfBUsers.csv (**Export-Csv -Path "C:\\Logs\\SfBUsers.csv" -NoTypeInformation**).</span><span class="sxs-lookup"><span data-stu-id="71dbc-247">The interpretation of this Office 365 PowerShell command is: Get all of the Skype for Business Online users in the current Office 365 subscription ( **Get-CsOnlineUser** ), obtain only the user name, UPN, and location ( **Select DisplayName, UserPrincipalName, UsageLocation** ), and then save that information in CSV file named C:\\Logs\\SfBUsers.csv ( **Export-Csv -Path "C:\\Logs\\SfBUsers.csv" -NoTypeInformation** ).</span></span>
  
<span data-ttu-id="71dbc-p130">PowerShell также позволяет сохранить этот список в виде XML-файла или HTML-страницы. Кроме того, с помощью дополнительных команд PowerShell вы можете сохранить данные непосредственно в файл Excel, используя необходимое форматирование.</span><span class="sxs-lookup"><span data-stu-id="71dbc-p130">You can also use options to save this list as an XML file or as an HTML page. In fact, with additional PowerShell commands, you could save it directly as an Excel file, with any custom formatting you desire.</span></span> 
  
<span data-ttu-id="71dbc-p131">Список, возвращенный командой PowerShell в Office 365, можно также отправить непосредственно на принтер, используемый по умолчанию в Windows. Вот пример необходимой команды:</span><span class="sxs-lookup"><span data-stu-id="71dbc-p131">You can also send the output of an Office 365 PowerShell command that displays a list directly to the default printer in Windows. Here is an example command:</span></span>
  
```powershell
Get-CsOnlineUser | Select DisplayName, UserPrincipalName, UsageLocation | Out-Printer
```

<span data-ttu-id="71dbc-252">Ниже показано, как будет выглядеть напечатанный документ.</span><span class="sxs-lookup"><span data-stu-id="71dbc-252">Here's what your printed document will look like:</span></span>
  
![Пример документа, напечатанного напрямую на стандартном принтере в Windows в результате выполнения команды PowerShell для Office 365.](media/o365-powershell-printed-data.png)
  
> [!TIP]
>  <span data-ttu-id="71dbc-254">Эта команда PowerShell возвращает список всех пользователей Skype для бизнеса Online в текущей подписке Office 365, но отображает только имя, имя участника (UPN) и расположение пользователей, после чего отправляет эту информацию на стандартный принтер Windows (**Out-Printer**).</span><span class="sxs-lookup"><span data-stu-id="71dbc-254">The interpretation of this Office 365 PowerShell command is:  Get all of the Skype for Business Online users in the current Office 365 subscription, obtain only the user name, UPN, and location, and then send that information to the default Windows printer ( **Out-Printer** ).</span></span>
  
<span data-ttu-id="71dbc-255">Распечатанный документ имеет то же простое форматирование, что и сведения, отображаемые в окне командной строки PowerShell для Office 365. Чтобы получить рабочую печатную копию, просто добавьте **| Out-Printer** в конец команды PowerShell для Office 365, которую вы создали, чтобы отобразить нужные данные.</span><span class="sxs-lookup"><span data-stu-id="71dbc-255">The printed document has the same simple formatting as the display within the Office 365 PowerShell command window, but once you have created an Office 365 PowerShell command to list what you need, you just add **| Out-Printer** to the end of the command to get a hard copy to work from.</span></span>
  
## <a name="office-365-powershell-lets-you-manage-across-server-products"></a><span data-ttu-id="71dbc-256">PowerShell для Office 365 позволяет управлять различными серверными продуктами</span><span class="sxs-lookup"><span data-stu-id="71dbc-256">Office 365 PowerShell lets you manage across server products</span></span>

<span data-ttu-id="71dbc-p132">Различные компоненты, составляющие Office 365:, предназначены для совместной работы. Предположим, вы добавляете нового пользователя в Office 365: и при этом указываете такие сведения, как его отдел и номер телефона. Эти сведения в дальнейшем будут доступны при получении доступа к данным пользователя с помощью любого из серверных продуктов Office 365:. Skype для бизнеса Online, Exchange или SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="71dbc-p132">The different components that make up Office 365 are designed to work together. For example, suppose you add a new user to Office 365 and, when you do, you specify such information as the user's department and phone number. That information will then be available if you access the user's information using any of the Office 365 server products: Skype for Business Online, Exchange, or SharePoint Online.</span></span>
  
<span data-ttu-id="71dbc-p133">Это общие сведения, распространяющиеся на набор продуктов. Сведения о конкретных продуктах, например информация о почтовом ящике Exchange пользователя, обычно недоступны во всех продуктах набора. Например, если вы хотите знать, включен ли почтовый ящик пользователя, то эти сведения доступны только в Центре администрирования Exchange.</span><span class="sxs-lookup"><span data-stu-id="71dbc-p133">But that's for common information that spans the suite of products. Product-specific information-for example, information about a user's Exchange mailbox-is typically not available across the suite. For example, if you want to know if a user's mailbox is enabled or not, that information is available only in the Exchange Admin center.</span></span> 
  
<span data-ttu-id="71dbc-263">Предположим, вы хотите создать отчет со следующим сведениями обо всех пользователях:</span><span class="sxs-lookup"><span data-stu-id="71dbc-263">Suppose you'd like to make a report that shows the following information for all your users:</span></span>
  
- <span data-ttu-id="71dbc-264">краткое имя пользователя;</span><span class="sxs-lookup"><span data-stu-id="71dbc-264">The user's display name</span></span>
    
- <span data-ttu-id="71dbc-265">наличие у пользователя лицензии на Office 365:;</span><span class="sxs-lookup"><span data-stu-id="71dbc-265">Whether the user is licensed for Office 365</span></span>
    
- <span data-ttu-id="71dbc-266">включен ли почтовый ящик Exchange пользователя;</span><span class="sxs-lookup"><span data-stu-id="71dbc-266">Whether the user's Exchange mailbox has been enabled</span></span>
    
- <span data-ttu-id="71dbc-267">включено ли для пользователя приложение Skype для бизнеса Online.</span><span class="sxs-lookup"><span data-stu-id="71dbc-267">Whether the user is enabled for Skype for Business Online</span></span>
    
<span data-ttu-id="71dbc-268">В настоящее время вы не можете использовать центр администрирования Microsoft 365 для простого создания такого отчета.</span><span class="sxs-lookup"><span data-stu-id="71dbc-268">You currently cannot use the Microsoft 365 admin center to easily produce such a report.</span></span> <span data-ttu-id="71dbc-269">Вместо этого необходимо создать отдельный документ для хранения информации, например листа Excel, и получить все имена пользователей и сведения о лицензировании из центра администрирования Microsoft 365, получить сведения о почтовом ящике из центра администрирования Exchange, получить Skype для Сведения о бизнес-сети из центра администрирования Skype для бизнеса Online, а затем выполните разбор и объединение этих сведений.</span><span class="sxs-lookup"><span data-stu-id="71dbc-269">Instead, you'll have to create a separate document to store the information, like an Excel worksheet, and get all the user names and licensing information from the Microsoft 365 admin center, get mailbox information from the Exchange Admin center, get Skype for Business Online information from the Skype for Business Online Admin center, and then collate and combine that information.</span></span>
  
<span data-ttu-id="71dbc-270">Вместо этого можно запустить сценарий PowerShell в Office 365, который составит для вас этот отчет.</span><span class="sxs-lookup"><span data-stu-id="71dbc-270">The alternative is to use an Office 365 PowerShell script to compile that report for you.</span></span>
  
<span data-ttu-id="71dbc-p135">Следующий пример сценария сложнее приведенных выше команд. Но он показывает преимущества PowerShell в Office 365 при создании представления данных, которое очень сложно получить другим способом. Вот сценарий, с помощью которого можно составить и отобразить необходимый список:</span><span class="sxs-lookup"><span data-stu-id="71dbc-p135">The following example script is more complicated than the commands you have seen so far in this article. But, it shows the potential of using Office 365 PowerShell to create views of information that are very difficult to do otherwise. Here is the script that can compile and display the needed list:</span></span>
  
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

<span data-ttu-id="71dbc-274">Ниже приведен пример отображения.</span><span class="sxs-lookup"><span data-stu-id="71dbc-274">Here is an example of the display:</span></span>
  
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

<span data-ttu-id="71dbc-275">Этот сценарий PowerShell для Office 365 интерпретируется так:</span><span class="sxs-lookup"><span data-stu-id="71dbc-275">The interpretation of this Office 365 PowerShell script is:</span></span>  
- <span data-ttu-id="71dbc-276">Возвращается список всех пользователей в текущей подписке Office 365, после чего сведения сохраняются в переменной $x (**$x = Get-MsolUser**).</span><span class="sxs-lookup"><span data-stu-id="71dbc-276">Get all of the users in the current Office 365 subscription and store the information in a variable named $x ( **$x = Get-MsolUser** ).</span></span>
- <span data-ttu-id="71dbc-277">Запускается цикл для всех пользователей в переменной $x (**foreach ($i in $x)**).</span><span class="sxs-lookup"><span data-stu-id="71dbc-277">Start a loop that runs over all the users in the variable named $x ( **foreach ($i in $x)** ).</span></span>  
- <span data-ttu-id="71dbc-278">Определяется переменная $y, в которой сохраняются сведения о почтовом ящике пользователя (**$y = Get-Mailbox -Identity $i.UserPrincipalName**).</span><span class="sxs-lookup"><span data-stu-id="71dbc-278">Define a variable named $y and store the user's mailbox information in it ( **$y = Get-Mailbox -Identity $i.UserPrincipalName** ).</span></span>
- <span data-ttu-id="71dbc-279">К сведениям о пользователе добавляется новое свойство IsMailBoxEnabled, которое задается как значение свойства IsMailBoxEnabled почтового ящика пользователя (**$i | Add-Member -MemberType NoteProperty -Name IsMailboxEnabled -Value $y.IsMailboxEnabled**).</span><span class="sxs-lookup"><span data-stu-id="71dbc-279">Add a new property to the user information named IsMailBoxEnabled and set it to the value of the IsMailBoxEnabled property of the user's mailbox ( **$i | Add-Member -MemberType NoteProperty -Name IsMailboxEnabled -Value $y.IsMailboxEnabled** ).</span></span>
- <span data-ttu-id="71dbc-280">Определяется переменная $y, в которой сохраняются данные Skype для бизнеса Online пользователя (**$y = Get-CsOnlineUser -Identity $i.UserPrincipalName**).</span><span class="sxs-lookup"><span data-stu-id="71dbc-280">Define a variable named $y and store the user's Skype for Business Online information in it ( **$y = Get-CsOnlineUser -Identity $i.UserPrincipalName** ).</span></span>
- <span data-ttu-id="71dbc-281">К сведениям о пользователе добавляется новое свойство EnabledForSfB, которое задается как значение свойства Enabled для данных Skype для бизнеса Online пользователя (**$i | Add-Member -MemberType NoteProperty -Name EnabledForSfB -Value $y.Enabled**).</span><span class="sxs-lookup"><span data-stu-id="71dbc-281">Add a new property to the user information named EnabledForSfB and set it to the value of the Enabled property of the user's Skype for Business Online information ( **$i | Add-Member -MemberType NoteProperty -Name EnabledForSfB -Value $y.Enabled** ).</span></span>
- <span data-ttu-id="71dbc-282">Отображается список пользователей, в котором указаны только их имена, наличие лицензии и два новых свойства, которые указывают, включен ли почтовый ящик пользователей и могут ли они использовать Skype для бизнеса Online (**$x | Select DisplayName, IsLicensed, IsMailboxEnabled, EnabledforSfB**).</span><span class="sxs-lookup"><span data-stu-id="71dbc-282">Display the list of users, but include only their name, whether they are licensed, and the two new properties that indicate whether their mailbox is enabled and whether they are enabled for Skype for Business Online ( **$x | Select DisplayName, IsLicensed, IsMailboxEnabled, EnabledforSfB** ).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="71dbc-283">См. также</span><span class="sxs-lookup"><span data-stu-id="71dbc-283">See also</span></span>

[<span data-ttu-id="71dbc-284">Начало работы с PowerShell для Office 365</span><span class="sxs-lookup"><span data-stu-id="71dbc-284">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
  
[<span data-ttu-id="71dbc-285">Управление учетными записями и лицензиями пользователей с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="71dbc-285">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="71dbc-286">Использование Windows PowerShell для создания отчетов в Office 365</span><span class="sxs-lookup"><span data-stu-id="71dbc-286">Use Windows PowerShell to create reports in Office 365</span></span>](use-windows-powershell-to-create-reports-in-office-365.md)

