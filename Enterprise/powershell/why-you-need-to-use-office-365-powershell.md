---
title: Причины использования Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Office_Other
ms.assetid: b3209b1a-40c7-4ede-8e78-8a88bb2adc8a
description: 'Сводка: в этой статье рассказывается, почему необходимо использовать PowerShell в Office 365 для управления Office 365:: в ряде случаев это может быть более эффективно, а в других  вызвано необходимостью.'
ms.openlocfilehash: d4dec6a62aecf2cfafdaf52f018f34fd2c9a14d4
ms.sourcegitcommit: 62c0630cc0d2611710e73e0592bddfe093e00783
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="why-you-need-to-use-office-365-powershell"></a><span data-ttu-id="405fd-103">Причины использования Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="405fd-103">Why you need to use Office 365 PowerShell</span></span>

 <span data-ttu-id="405fd-104">**Сводка.** Узнайте, зачем использовать PowerShell для Office 365: в ряде случаев это может быть более эффективно, а в других вызвано необходимостью.</span><span class="sxs-lookup"><span data-stu-id="405fd-104">**Summary:** Understand why you must use Office 365 PowerShell to manage Office 365, in some cases more efficiently and in other cases by necessity.</span></span>
  
<span data-ttu-id="405fd-p101">Центр администрирования Office 365 позволяет не только управлять учетными записями и лицензиями пользователей Office 365:, но и серверными продуктами Office 365:: Exchange, Skype для бизнеса Online и SharePoint Online. Кроме того, этими элементами можно также управлять с помощью команд PowerShell в Office 365, используя командную строку и язык сценариев. Это позволит увеличить скорость работы, использовать автоматизацию и получить дополнительные возможности.</span><span class="sxs-lookup"><span data-stu-id="405fd-p101">With the Office 365 admin center, you can not only manage your Office 365 user accounts and licenses, but you can also manage your Office 365 server products: Exchange, Skype for Business Online, and SharePoint Online. However, you can also manage these elements with Office 365 PowerShell commands, taking advantage of a command-line and scripting language environment for speed, automation, and additional capability.</span></span>
  
<span data-ttu-id="405fd-107">В этой статье мы покажем вам эти способы использования PowerShell в Office 365 для управления Office 365:.</span><span class="sxs-lookup"><span data-stu-id="405fd-107">In this article, we'll show you these ways in which you can use Office 365 PowerShell to manage Office 365.</span></span>
  
- <span data-ttu-id="405fd-108">PowerShell в Office 365 может раскрыть дополнительную информацию, которая недоступна в средстве "Центр администрирования Office 365".</span><span class="sxs-lookup"><span data-stu-id="405fd-108">Office 365 PowerShell can reveal additional information that you cannot see with the Office 365 admin center</span></span>
    
- <span data-ttu-id="405fd-109">Некоторые компоненты Office 365 можно настроить только с помощью PowerShell Office 365</span><span class="sxs-lookup"><span data-stu-id="405fd-109">Office 365 has features that you can only configure by using Office 365 PowerShell</span></span>
    
- <span data-ttu-id="405fd-110">PowerShell в Office 365 идеально подходит для выполнения групповых операций.</span><span class="sxs-lookup"><span data-stu-id="405fd-110">Office 365 PowerShell is great at performing bulk operations</span></span>
    
- <span data-ttu-id="405fd-111">Возможности фильтрации данных с помощью PowerShel Office 365</span><span class="sxs-lookup"><span data-stu-id="405fd-111">Office 365 PowerShell is great at filtering data</span></span>
    
- <span data-ttu-id="405fd-112">Упрощение печати или сохранения данных с помощью PowerShell Office 365</span><span class="sxs-lookup"><span data-stu-id="405fd-112">Office 365 PowerShell makes it easy to print or save data</span></span>
    
- <span data-ttu-id="405fd-113">PowerShell для Office 365 позволяет управлять различными серверными продуктами</span><span class="sxs-lookup"><span data-stu-id="405fd-113">Office 365 PowerShell lets you manage across server products</span></span>
    
<span data-ttu-id="405fd-p102">Приступая к чтению статьи, необходимо понимать, что PowerShell в Office 365 — это набор модулей для Windows PowerShell, среды командной строки для служб и платформ Windows. Эта среда создает язык командной строки, который можно расширить с помощью дополнительных модулей и который позволяет выполнять как простые, так и сложные команды и скрипты. Например, после установки модулей PowerShell в Office 365 и подключения подписки на Office 365 вы можете выполнить следующую команду, чтобы получить список всех почтовых ящиков пользователей для Microsoft Exchange Online:</span><span class="sxs-lookup"><span data-stu-id="405fd-p102">Before you begin, understand that Office 365 PowerShell is a set of modules for Windows PowerShell, a command-line environment for Windows-based services and platforms. This environment creates a command shell language that can be extended with additional modules and provides a way to execute simple or complex commands or scripts For example, after you install the Office 365 PowerShell modules and connect to your Office 365 subscription, you can run this command to list all of the user mailboxes for Microsoft Exchange Online:</span></span>
  
```
Get-Mailbox
```

<span data-ttu-id="405fd-117">Кроме того, эта команда позволяет определить количество элементов во всех списках для всех сайтов всех веб-приложений в SharePoint Online:</span><span class="sxs-lookup"><span data-stu-id="405fd-117">You can also run this command to calculate the number of items in all of the lists for all of the sites for all of your web apps in SharePoint Online:</span></span>
  
```
Get-SPOSite -Limit All | Get-SPWeb -Limit All | % {$_.Lists} | ? {$_ -is [Microsoft.SharePoint.SPDocumentLibrary]} | % {$total+= $_.ItemCount}; $total
```

<span data-ttu-id="405fd-118">Центр администрирования Office 365 также позволяет с легкостью отобразить список почтовых ящиков, но подсчитать количество элементов во всех списках для всех сайтов всех веб-приложений будет непросто.</span><span class="sxs-lookup"><span data-stu-id="405fd-118">Getting the list of mailboxes can also be easily done using the Office 365 admin center, but counting the number of items in all of the lists for all of the sites for all of your web apps cannot be easily done.</span></span>
  
<span data-ttu-id="405fd-p103">Помните, что среда PowerShell в Office 365 разработана для того, чтобы расширить и дополнить возможности управления Office 365:, а не заменить Центр администрирования Office 365. Как администратор Office 365:, вы должны владеть по крайней мере основами работы с Office 365: PowerShell, так как некоторые процедуры настройки можно выполнить только с помощью команд PowerShell в Office 365. В таких случаях вы должны уметь:</span><span class="sxs-lookup"><span data-stu-id="405fd-p103">Please note that Office 365 PowerShell is designed to augment and enhance your ability to manage Office 365, not to replace the Office 365 admin center. As an Office 365 administrator, you must become at least comfortable with using Office 365 PowerShell because there are some configuration procedures that can only be done with Office 365 PowerShell commands. In these cases, you will be required to understand how to:</span></span>
  
- <span data-ttu-id="405fd-122">устанавливать модули PowerShell в Office 365 (выполняется только один раз для компьютера администратора);</span><span class="sxs-lookup"><span data-stu-id="405fd-122">Install the Office 365 PowerShell modules (done only once for each administrator computer).</span></span>
    
- <span data-ttu-id="405fd-123">подключаться к своей подписке Office 365: (выполняется один раз для каждого сеанса PowerShell);</span><span class="sxs-lookup"><span data-stu-id="405fd-123">Connect to your Office 365 subscription (done once for each PowerShell session).</span></span>
    
- <span data-ttu-id="405fd-124">собирать информацию для выполнения необходимых команд PowerShell в Office 365;</span><span class="sxs-lookup"><span data-stu-id="405fd-124">Gather the information needed to run the required Office 365 PowerShell commands.</span></span>
    
- <span data-ttu-id="405fd-125">успешно выполнять команды PowerShell в Office 365.</span><span class="sxs-lookup"><span data-stu-id="405fd-125">Run the Office 365 PowerShell commands successfully.</span></span>
    
<span data-ttu-id="405fd-p104">Овладев этими основными навыками, вам не обязательно отображать список пользователей почтовых ящиков с помощью команды **Get-Mailbox** или учиться создавать команду, подобную предыдущей, для подсчета всех элементов во всех списках для всех сайтов всех веб-приложений. Корпорация Майкрософт и сообщество администраторов Office 365: могут помочь вам в этом при необходимости.</span><span class="sxs-lookup"><span data-stu-id="405fd-p104">After learning these basic skills, you are not required to list your mailbox users with **Get-Mailbox** command, nor are you required to understand how to create a new command like the previous one to count all the items in all the lists for all of the sites for all of your web apps. Microsoft and the community of Office 365 administrators can help you with that as needed.</span></span>
  
## <a name="office-365-powershell-can-reveal-additional-information-that-you-cannot-see-with-the-office-365-admin-center"></a><span data-ttu-id="405fd-128">PowerShell позволяет получить дополнительную информацию, которая не отображается в Центре администрирования Office 365</span><span class="sxs-lookup"><span data-stu-id="405fd-128">Office 365 PowerShell can reveal additional information that you cannot see with the Office 365 admin center</span></span>
<span data-ttu-id="405fd-129"><a name="reveal"> </a></span><span class="sxs-lookup"><span data-stu-id="405fd-129"></span></span>

<span data-ttu-id="405fd-p105">Центр администрирования Office 365 включает много полезных сведений, но это не означает, что там отображается вся возможная информация о пользователях, лицензиях, почтовых ящиках и сайтах, имеющаяся в Office 365:. Ниже приведен пример раздела **пользователи и группы** в средстве "Центр администрирования Office 365":</span><span class="sxs-lookup"><span data-stu-id="405fd-p105">The Office 365 admin center displays a lot of useful information, but that doesn't mean that it displays all the possible information that Office 365 stores on users, licenses, mailboxes, and sites. Here is an example for **users and groups** in the Office 365 admin center:</span></span>
  
![Пример отображения пользователей и групп в Центре администрирования Office 365.](images/o365_powershell_users_and_groups.png)
  
<span data-ttu-id="405fd-p106">Здесь отображаются сведения, которых очень часто бывает достаточно. Однако есть случаи, когда нужно знать больше. Например, лицензирование Office 365: (а также доступных пользователю компонентов Office 365:) частично зависит от географического местоположения пользователя: для пользователя, проживающего в США, можно активировать политики и функции, отличные от политик и функций для жителя Индии или Бельгии. Центр администрирования Office 365 позволяет определить географическое расположение пользователя, как описано ниже.</span><span class="sxs-lookup"><span data-stu-id="405fd-p106">For many purposes, this displays the information you need to know. However, there are times when you need more. For example, Office 365 licensing (as well as the Office 365 features available to a user) depend in part on that user's geographic location. The policies and features you can extend to a user who lives in the United States might not be the same as the policies and features you can extend to a user who lives in India or in Belgium. You can use the Office 365 admin center to determine a user's geographic location with these steps:</span></span>
  
1. <span data-ttu-id="405fd-138">Дважды щелкните **отображаемое имя** пользователя.</span><span class="sxs-lookup"><span data-stu-id="405fd-138">Double-click the user's **Display Name**.</span></span>
    
2. <span data-ttu-id="405fd-139">На панели отображения свойств пользователя щелкните **сведения**.</span><span class="sxs-lookup"><span data-stu-id="405fd-139">In the user properties display pane, click **details**.</span></span>
    
3. <span data-ttu-id="405fd-140">В окне сведений щелкните **дополнительные сведения**.</span><span class="sxs-lookup"><span data-stu-id="405fd-140">In the details display, click **additional details**.</span></span>
    
4. <span data-ttu-id="405fd-141">Прокрутите окно вниз до заголовка **Страна или регион**.</span><span class="sxs-lookup"><span data-stu-id="405fd-141">Scroll down until you see the heading **Country or region**:</span></span>
    
     ![Пример сведений о регионе для пользователя в Центре администрирования Office 365.](images/o365_powershell_usage_location.png)
  
5. <span data-ttu-id="405fd-143">Запишите отображаемое имя и местонахождение пользователя на лист бумаги или скопируйте и вставьте их в Блокнот.</span><span class="sxs-lookup"><span data-stu-id="405fd-143">Write the user's display name and location on a piece of paper, or copy and paste it into Notepad.</span></span> 
    
<span data-ttu-id="405fd-p107">Эту процедуру необходимо повторить для каждого пользователя. Если пользователей очень много, эта задача может показаться утомительной. В PowerShell в Office 365 вы можете отобразить эти сведения обо всех пользователях с помощью следующей команды:</span><span class="sxs-lookup"><span data-stu-id="405fd-p107">You must repeat this procedure for each user. For many users, this can be a tedious task. With Office 365 PowerShell, you can display this information for all of your users with the following command:</span></span>
  
```
Get-MsolUser | Select DisplayName, UsageLocation
```

> [!NOTE]
> <span data-ttu-id="405fd-147">Для использования этой команды необходимо установить [модуль Windows Azure Active Directory](https://technet.microsoft.com/ru-RU/library/jj151815.aspx).</span><span class="sxs-lookup"><span data-stu-id="405fd-147">This command requires you to install the [Windows Azure Active Directory module](https://technet.microsoft.com/ru-RU/library/jj151815.aspx).</span></span> 
  
<span data-ttu-id="405fd-148">Ниже приведен пример отображения.</span><span class="sxs-lookup"><span data-stu-id="405fd-148">Here is an example of the display:</span></span>
  
```
DisplayName                               UsageLocation
-----------                               -------------
Zrinka Makovac                            US
Bonnie Kearney                            GB
Fabrice Canel                             BR
Brian Johnson (TAILSPIN)                  US
Anne Wallace                              US
Alex Darrow                               US
David Longmuir                            BR
```

> [!TIP]
>  <span data-ttu-id="405fd-149">Эта команда PowerShell возвращает список всех пользователей в текущей подписке Office 365 (**Get-MsolUser**), но отображает только имя и местонахождение каждого пользователя (**Select DisplayName, UsageLocation**).</span><span class="sxs-lookup"><span data-stu-id="405fd-149">The interpretation of this Office 365 PowerShell command is: Get all of the users in the current Office 365 subscription ( **Get-MsolUser** ), but only display the name and location for each user ( **Select DisplayName, UsageLocation** ).</span></span>
  
<span data-ttu-id="405fd-p108">Так как PowerShell в Office 365 поддерживает язык командной оболочки, вы можете выполнять дополнительные действия над информацией, полученной с помощью команды **Get-MSolUser**. Например, вы можете отсортировать пользователей по их расположениям и объединить в группы пользователей из Бразилии, США, и т. д. Это можно сделать с помощью указанной ниже команды.</span><span class="sxs-lookup"><span data-stu-id="405fd-p108">Because Office 365 PowerShell supports a command shell language, you can further manipulate the information obtained from the **Get-MSolUser** command. For example, maybe you'd like to sort these users by their location, grouping all the Brazilian users together, all the United States users together, etc. Here is the command:</span></span>
  
```
Get-MsolUser | Select DisplayName, UsageLocation | Sort UsageLocation, DisplayName
```

<span data-ttu-id="405fd-152">Ниже приведен пример отображения.</span><span class="sxs-lookup"><span data-stu-id="405fd-152">Here is an example of the display:</span></span>
  
```
DisplayName                                 UsageLocation
-----------                                 -------------
David Longmuir                              BR
Fabrice Canel                               BR
Bonnie Kearney                              GB
Alex Darrow                                 US
Anne Wallace                                US
Brian Johnson (TAILSPIN)                    US
Zrinka Makovac                              US
```

> [!TIP]
>  <span data-ttu-id="405fd-153">Эта команда PowerShell возвращает список всех пользователей в текущей подписке Office 365, но отображает только имя и местонахождение каждого пользователя. Список сортируется сначала по местонахождению, а затем по имени (**Sort UsageLocation, DisplayName**).</span><span class="sxs-lookup"><span data-stu-id="405fd-153">The interpretation of this Office 365 PowerShell command is: Get all of the users in the current Office 365 subscription, but only display the name and location for each user and sort them first by their location, and then their names ( **Sort UsageLocation, DisplayName** ).</span></span>
  
<span data-ttu-id="405fd-p109">Можно также использовать дополнительные фильтры. Например, если нужно просмотреть сведения о пользователях, находящихся в Бразилии, используйте следующую команду:</span><span class="sxs-lookup"><span data-stu-id="405fd-p109">You can also employ additional filtering. For example, if you only want to see information about users based in Brazil, use this command:</span></span>
  
```
Get-MsolUser | Where {$_.UsageLocation -eq "BR"} | Select DisplayName, UsageLocation 
```

<span data-ttu-id="405fd-156">Ниже приведен пример отображения.</span><span class="sxs-lookup"><span data-stu-id="405fd-156">Here is an example of the display:</span></span>
  
```
DisplayName                                           UsageLocation
-----------                                           -------------
David Longmuir                                        BR
Fabrice Canel                                         BR
```

> [!TIP]
>  <span data-ttu-id="405fd-157">Эта команда PowerShell возвращает список всех пользователей в текущей подписке Office 365, которые находятся в Бразилии (**Where {$\_.UsageLocation -eq "BR"}**), а затем отображает имя и местонахождение каждого пользователя.</span><span class="sxs-lookup"><span data-stu-id="405fd-157">The interpretation of this Office 365 PowerShell command is: Get all of the users in the current Office 365 subscription whose location is Brazil ( **Where {$\_.UsageLocation -eq "BR"}** ), then display the name and location for each user.</span></span>
  
 <span data-ttu-id="405fd-158">**Небольшое примечание относительно более крупных доменов**</span><span class="sxs-lookup"><span data-stu-id="405fd-158">**A Quick Note Regarding Larger Domains**</span></span>
  
<span data-ttu-id="405fd-p110">Если у вас очень большой домен, включающий десятки тысяч пользователей, то использование некоторых сценариев, описанных в этой статье, может привести к так называемому "регулированию". Это будет означать, что вы одновременно выполняете слишком большое количество задач, для чего недостаточно мощности компьютера и пропускной способности сети. Поэтому крупным организациям может понадобиться разбить некоторые из этих команд PowerShell в Office 365 на две команды. Например, указанная ниже команда возвращает все учетные записи пользователей и отображает для каждой из них имя и расположение.</span><span class="sxs-lookup"><span data-stu-id="405fd-p110">If you have a very large domain with tens of thousands of users, trying some of the examples we show in this article could lead to "throttling." That means that, based on things like computing power and available network bandwidth, you're trying to do a little too much at one time. Because of that, larger organizations might want to split some of these Office 365 PowerShell commands into two commands. For example, this one command returns all the user accounts and shows the name and location for each:</span></span>
  
```
Get-MsolUser | Select DisplayName, UsageLocation
```

<span data-ttu-id="405fd-p111">Она отлично подходит для небольших доменов. Тем не менее крупной организации может понадобиться разделить ее на две команды: одна команда будет использоваться для сохранения сведений об учетных записях пользователей в переменной, а другая  для отображения необходимой информации. Вот пример:</span><span class="sxs-lookup"><span data-stu-id="405fd-p111">That works great for smaller domains. In a large organization, however, you might need to split that into two commands: one command to store the user account information in a variable and another command to display the needed information. Here is an example:</span></span>
  
```
$x = Get-MsolUser
$x | Select DisplayName, UsageLocation
```


<span data-ttu-id="405fd-166">Этот набор команд PowerShell для Office 365 интерпретируется так:</span><span class="sxs-lookup"><span data-stu-id="405fd-166">The interpretation of this set of Office 365 PowerShell commands is:</span></span>
- <span data-ttu-id="405fd-167">Возвращается список всех пользователей в текущей подписке Office 365, после чего сведения сохраняются в переменной $x (**$x = Get-MsolUser**).</span><span class="sxs-lookup"><span data-stu-id="405fd-167">Get all of the users in the current Office 365 subscription and store the information in a variable named $x ( **$x = Get-MsolUser** ).</span></span>
- <span data-ttu-id="405fd-168">Отображается содержимое переменной $x, которое включает в себя только имя и местонахождение каждого пользователя (**$x | Select DisplayName, UsageLocation**).</span><span class="sxs-lookup"><span data-stu-id="405fd-168">Display the contents of the variable $x, but only include the name and location for each user ( **$x | Select DisplayName, UsageLocation** ).</span></span>
  
## <a name="office-365-has-features-that-you-can-only-configure-with-office-365-powershell"></a><span data-ttu-id="405fd-169">Некоторые компоненты Office 365 можно настроить только с помощью PowerShell</span><span class="sxs-lookup"><span data-stu-id="405fd-169">Office 365 has features that you can only configure with Office 365 PowerShell</span></span>
<span data-ttu-id="405fd-170"><a name="only"> </a></span><span class="sxs-lookup"><span data-stu-id="405fd-170"></span></span>

<span data-ttu-id="405fd-p112">Центр администрирования Office 365 позволяет выполнять самые распространенные и важные задачи администрирования, применимые к большинству пользователей. Другими словами, Центр администрирования Office 365 создан, чтобы типичный администратор с его помощью мог выполнять распространенные задачи управления. Следовательно, Центр администрирования Office 365 не позволяет выполнить некоторые задачи.</span><span class="sxs-lookup"><span data-stu-id="405fd-p112">The Office 365 admin center is intended to provide access to the most common or meaningful administrative tasks that apply to most people. In other words, the Office 365 admin center was designed so that the typical administrator could use the tool to carry out the most common management tasks. By this definition, that means that there are some tasks that can't be completed by using the Office 365 admin center.</span></span>
  
<span data-ttu-id="405fd-174">Например, в Центр администрирования Skype для бизнеса Online используется несколько параметров для создания настраиваемых приглашений на собрания:</span><span class="sxs-lookup"><span data-stu-id="405fd-174">For example, the Skype for Business Online Admin center provides a few options for creating custom meeting invitations:</span></span>
  
![Пример отображения настраиваемых приглашений на собрание в Центре администрирования Skype для бизнеса Online.](images/o365_powershell_meeting_invitation.png)
  
<span data-ttu-id="405fd-p113">С помощью указанных ниже параметров приглашения на собрания можно сделать более персонализированными и профессиональными. Тем не менее, настройки собраний позволяют сделать больше, чем просто создать пользовательские приглашения. Например, по умолчанию собрания позволяют:</span><span class="sxs-lookup"><span data-stu-id="405fd-p113">With these settings, you can add a touch of personalization and professionalism to meeting invitations. However, there's more to meeting configuration settings than simply creating custom meeting invitations. For example, by default, meetings allow:</span></span>
  
- <span data-ttu-id="405fd-179">анонимным пользователям автоматически присоединяться к каждому собранию;</span><span class="sxs-lookup"><span data-stu-id="405fd-179">Anonymous users to gain automatic entrance to each meeting.</span></span>
    
- <span data-ttu-id="405fd-180">участникам записывать собрание;</span><span class="sxs-lookup"><span data-stu-id="405fd-180">Attendees to record the meeting.</span></span>
    
- <span data-ttu-id="405fd-181">обозначать всех пользователей из вашей организации докладчиками при их присоединении к собранию.</span><span class="sxs-lookup"><span data-stu-id="405fd-181">All users from your organization to be designated as presenters when they join the meeting.</span></span>
    
<span data-ttu-id="405fd-p114">Эти параметры недоступны в Центре администрирования Skype для бизнеса Online. Но ими можно управлять с помощью PowerShell в Office 365. Указанная ниже команда отключает эти три параметра.</span><span class="sxs-lookup"><span data-stu-id="405fd-p114">These settings are not available from the Skype for Business Online Admin center. However, you can control them from Office 365 PowerShell. Here is a command that disables these three settings:</span></span>
  
```
Set-CsMeetingConfiguration -AdmitAnonymousUsersByDefault $False -AllowConferenceRecording $False -DesignateAsPresenter "None"
```

> [!NOTE]
> <span data-ttu-id="405fd-185">Для использования этой команды необходимо установить [модуль PowerShell для Skype для бизнеса Online](https://www.microsoft.com/download/details.aspx?id=39366).</span><span class="sxs-lookup"><span data-stu-id="405fd-185">This command requires that you install the [Skype for Business Online PowerShell Module ](https://www.microsoft.com/download/details.aspx?id=39366).</span></span> 
  
> [!TIP]
>  <span data-ttu-id="405fd-186">Эта команда PowerShell для Office 365 отключает разрешение для анонимных пользователям автоматически присоединяться к новым собраниям Skype для бизнеса Online (**Set-CsMeetingConfiguration**, **-AdmitAnonymousUsersByDefault $False**), отключает для участников возможность записывать эти собрания (**-AllowConferenceRecording $False**) и отменяет для всех пользователей в организации статус выступающего (**-DesignateAsPresenter "None"**).</span><span class="sxs-lookup"><span data-stu-id="405fd-186">The interpretation of this Office 365 PowerShell command is: For the settings for new Skype for Business Online meetings ( **Set-CsMeetingConfiguration** ), disable allowing anonymous users to gain automatic entrance to meetings ( **-AdmitAnonymousUsersByDefault $False** ), disable the ability for attendees to record meetings ( **-AllowConferenceRecording $False** ), and do not designate all users from your organization as presenters ( **-DesignateAsPresenter "None"** ).</span></span>
  
<span data-ttu-id="405fd-187">Если вы передумали и хотите восстановить эти настройки по умолчанию (т. е. включить их все), выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="405fd-187">If you change your mind and want to restore these default settings (all of them enabled), run this command:</span></span>
  
```
Set-CsMeetingConfiguration -AdmitAnonymousUsersByDefault $True -AllowConferenceRecording $True -DesignateAsPresenter "Company"
```

<span data-ttu-id="405fd-p115">Это только один пример. Существуют и другие, поэтому вы как администратор Office 365: должны уметь без труда использовать команды PowerShell в Office 365.</span><span class="sxs-lookup"><span data-stu-id="405fd-p115">This is just one example. There are others, which is why you, as an Office 365 administrator, need to be comfortable with running Office 365 PowerShell commands.</span></span>
  
## <a name="office-365-powershell-is-great-at-carrying-out-bulk-operations"></a><span data-ttu-id="405fd-190">PowerShell Office 365 идеально подходит для массовых операций</span><span class="sxs-lookup"><span data-stu-id="405fd-190">Office 365 PowerShell is great at carrying out bulk operations</span></span>
<span data-ttu-id="405fd-191"><a name="bulk"> </a></span><span class="sxs-lookup"><span data-stu-id="405fd-191"></span></span>

<span data-ttu-id="405fd-p116">Исторически сложилось так, что графические пользовательские интерфейсы, например Центр администрирования Office 365, оптимальны при выполнении одной операции. Например, если нужно отключить одну учетную запись пользователя, Центр администрирования Office 365 позволяет быстро найти и снять соответствующий флажок. Обычно это проще, чем выполнить аналогичную операцию в PowerShell в Office 365.</span><span class="sxs-lookup"><span data-stu-id="405fd-p116">Historically, visual interfaces like the Office 365 admin center are most valuable when you have a single operation to perform. For example, if you need to disable one user account, you can use the Office 365 admin center to quickly locate and clear a checkbox. This can be simpler than performing a similar operation in Office 365 PowerShell.</span></span>
  
<span data-ttu-id="405fd-p117">Однако если вам нужно изменить ряд параметров или некоторые параметры внутри большого набора других параметров, Центр администрирования Office 365 может быть не лучшим вариантом с точки зрения экономии времени. Например, если нужно изменить префикс в тысячах номеров телефонов или удалить определенного пользователя, например Кена Майера (Ken Myer), со всех сайтов SharePoint Online, то как это можно сделать в средстве "Центр администрирования Office 365"?</span><span class="sxs-lookup"><span data-stu-id="405fd-p117">But if you have to change many things or some selected things within a large set of other things, the Office 365 admin center might not be the best use of your time. For example, if you had to change the prefix on thousands of phone numbers or you needed to remove a specific user, Ken Myer, from all of your SharePoint Online sites, how would you do that in the Office 365 admin center?</span></span>
  
<span data-ttu-id="405fd-p118">Допустим, в последнем примере у вас есть несколько сотен сайтов SharePoint Online и вы даже не знаете, на каком из них зарегистрирован пользователь Ken Meyer. Это означает, что сначала необходимо войти в Центр администрирования Office 365, а затем выполнить следующую процедуру для каждого сайта:</span><span class="sxs-lookup"><span data-stu-id="405fd-p118">For the latter example, you have several hundred SharePoint Online sites and you don't know even know which ones of which Ken Meyer is a member. That means you'll have to start at the Office 365 admin center and then perform this procedure for each site:</span></span>
  
1. <span data-ttu-id="405fd-199">Щелкнуть **URL-адрес** сайта.</span><span class="sxs-lookup"><span data-stu-id="405fd-199">Click the **URL** of the site.</span></span>
    
2. <span data-ttu-id="405fd-200">В поле **свойств семейства веб-сайтов** щелкнуть ссылку **Адрес веб-сайта**, чтобы открыть сайт.</span><span class="sxs-lookup"><span data-stu-id="405fd-200">In the **site collection properties** box, click the **Web Site Address** link to open the site.</span></span>
    
3. <span data-ttu-id="405fd-201">На сайте нажать кнопку **Общий доступ**.</span><span class="sxs-lookup"><span data-stu-id="405fd-201">On the site, click **Share**.</span></span>
    
4. <span data-ttu-id="405fd-202">В диалоговом окне **Общий доступ** щелкнуть ссылку, чтобы показать всех пользователей с разрешениями для сайта:</span><span class="sxs-lookup"><span data-stu-id="405fd-202">In the **Share** dialog box click the link that shows you all the users who have permissions to the site:</span></span>
    
     ![Пример просмотра участников сайта SharePoint Online в Центре администрирования SharePoint Online](images/o365_powershell_view_permissions.png)
  
5. <span data-ttu-id="405fd-204">В диалоговом окне **Общий доступ предоставлен** нажать кнопку **Дополнительно**.</span><span class="sxs-lookup"><span data-stu-id="405fd-204">In the **Shared With** dialog box, click **Advanced**.</span></span>
    
6. <span data-ttu-id="405fd-205">Прокрутить список пользователей, найти и выбрать Кена Майера (если у него есть разрешения для сайта) и нажать кнопку **Удалить разрешения пользователя**.</span><span class="sxs-lookup"><span data-stu-id="405fd-205">Scroll down the list of users, find and select Ken Myer (assuming he has permissions to the site), and then click **Remove User Permissions**.</span></span>
    
<span data-ttu-id="405fd-206">Для нескольких сотен сайтов это может занять очень много времени.</span><span class="sxs-lookup"><span data-stu-id="405fd-206">This can take a long time for several hundred sites.</span></span>
  
<span data-ttu-id="405fd-207">Но есть и другой вариант: удалить пользователя Ken Myer со всех сайтов с помощью указанной ниже команды PowerShell в Office 365.</span><span class="sxs-lookup"><span data-stu-id="405fd-207">The alternative is to use Office 365 PowerShell and the following command to remove Ken Myer from all of your sites:</span></span>
  
```
Get-SPOSite | ForEach {Remove-SPOUser -Site $_.Url -LoginName "kenmyer@litwareinc.com"}
```

> [!NOTE]
> <span data-ttu-id="405fd-208">Для использования этой команды необходимо [подключиться к PowerShell для SharePoint Online](https://technet.microsoft.com/library/fp161372.aspx).</span><span class="sxs-lookup"><span data-stu-id="405fd-208">This command requires that you install the [Connect to SharePoint Online PowerShell](https://technet.microsoft.com/library/fp161372.aspx).</span></span> 
  
> [!TIP]
>  <span data-ttu-id="405fd-209">Эта команда PowerShell возвращает список всех сайтов SharePoint в текущей подписке Office 365 (**Get-SPOSite**) и удаляет пользователя Ken Meyer из списка зарегистрированных пользователей каждого сайта (**ForEach {Remove-SPOUser -Site $\_.Url -LoginName "kenmyer@litwareinc.com"}**).</span><span class="sxs-lookup"><span data-stu-id="405fd-209">The interpretation of this Office 365 PowerShell command is:  Get all of the SharePoint sites in the current Office 365 subscription ( **Get-SPOSite** ) and for each site, remove Ken Meyer from the list of users who can access it ( **ForEach {Remove-SPOUser -Site $\_.Url -LoginName "kenmyer@litwareinc.com"}** ).</span></span>
  
<span data-ttu-id="405fd-p119">Так как мы указываем Office 365: удалить пользователя Ken Meyer с каждого сайта, включая те, к которым у него нет доступа, эта команда будет показывать ошибки для таких сайтов. В этой команде можно использовать дополнительное условие, чтобы пользователь Ken Meyer был удален только с тех сайтов, в списке учетных записей которых он содержится, но чтобы указанные ошибки не влияли на сами сайты. Чтобы обработать несколько сотен сайтов, команде может потребоваться несколько минут  в отличие от часов работы в средстве "Центр администрирования Office 365".</span><span class="sxs-lookup"><span data-stu-id="405fd-p119">Because we are telling Office 365 to remove Ken Meyer from every site, including those in which he does not have access, the display of this command will show errors for those sites in which he does not currently have access. We can use an additional condition on this command to remove Key Meyer only from the sites that have him in their login list, but the listed errors cause no harm to the sites themselves. This command might take a few minutes to run against hundreds of sites, rather than hours of working through the Office 365 admin center.</span></span>
  
<span data-ttu-id="405fd-p120">Вот еще один пример массовой операции. Чтобы добавить пользователя Бонни Керни (Bonnie Kearney) — нового администратора SharePoint — на все сайты в организации, используйте следующую команду:</span><span class="sxs-lookup"><span data-stu-id="405fd-p120">Here is another bulk operation example. Use this command to add Bonnie Kearney, a new SharePoint administrator, to all of the sites in the organization:</span></span>
  
```
Get-SPOSite | ForEach {Add-SPOUser -Site $_.Url -LoginName "bkearney@litwareinc.com" -Group "Members"}
```

> [!TIP]
>  <span data-ttu-id="405fd-215">Эта команда PowerShell возвращает список всех сайтов SharePoint в текущей подписке Office 365, а затем добавляет имя Bonnie Kearney в группу участников каждого сайта, чтобы разрешить этому пользователю соответствующий доступ (**ForEach {Add-SPOUser -Site $\_.Url -LoginName "bkearney@litwareinc.com" -Group "Members"}**).</span><span class="sxs-lookup"><span data-stu-id="405fd-215">The interpretation of this Office 365 PowerShell command is:  Get all of the SharePoint sites in the current Office 365 subscription and for each site, allow Bonnie Kearney access by adding her login name to the Members group of the site ( **ForEach {Add-SPOUser -Site $\_.Url -LoginName "bkearney@litwareinc.com" -Group "Members"}** ).</span></span>
  
## <a name="office-365-powershell-is-great-at-filtering-data"></a><span data-ttu-id="405fd-216">PowerShell для Office 365 позволяет фильтровать данные</span><span class="sxs-lookup"><span data-stu-id="405fd-216">Office 365 PowerShell is great at filtering data</span></span>
<span data-ttu-id="405fd-217"><a name="filter"> </a></span><span class="sxs-lookup"><span data-stu-id="405fd-217"></span></span>

<span data-ttu-id="405fd-p121">Центр администрирования Office 365 предоставляет несколько различных способов фильтрации данных, т. е. быстрого и легкого поиска целевого подмножества информации. Например, Exchange позволяет с легкостью фильтровать сведения по практически любому свойству почтового ящика пользователя. Например, вот список почтовых ящиков всех пользователей, проживающих в г. Блумингтон (Bloomington):</span><span class="sxs-lookup"><span data-stu-id="405fd-p121">The Office 365 admin center provides several different ways to filter your data to quickly and easily locate a targeted subset of information. For example, Exchange makes it easy to filter on practically any property of a user mailbox. For example, here is the list of mailboxes for all the users who live in the city of Bloomington:</span></span>
  
![Пример расширенного поиска списка почтовых ящиков всех пользователей, проживающих в городе Bloomington, в Центре администрирования Office 365.](images/o365_powershell_advanced_search.png)
  
<span data-ttu-id="405fd-p122">Кроме того, Центр администрирования Exchange позволяет сочетать различные условия фильтра. Например, можно найти почтовые ящики всех пользователей, проживающих в г. Блумингтон и работающих в отделе финансов.</span><span class="sxs-lookup"><span data-stu-id="405fd-p122">The Exchange Admin center also lets you combine filter criteria. For example, you can find the mailboxes for all the people who live in Bloomington and who work in the Finance department.</span></span> 
  
<span data-ttu-id="405fd-p123">Но возможности фильтрации в Центре администрирования Exchange ограничены. Например, вам может понадобиться найти почтовые ящики пользователей, проживающих в городах Блумингтон (Bloomington) или Сан-Диего (San Diego), или почтовые ящики всех пользователей, которые не проживают в городе Блумингтон.</span><span class="sxs-lookup"><span data-stu-id="405fd-p123">However, there are limitations to what you can do in the Exchange Admin center. For example, maybe you'd like to find the mailboxes of people who live in Bloomington or San Diego, or the mailboxes for all the people who don't live in Bloomington.</span></span> 
  
<span data-ttu-id="405fd-226">PowerShell в Office 365 позволяет получить список почтовых ящиков всех пользователей, проживающих в городах Блумингтон или Сан-Диего, с помощью указанной ниже команды.</span><span class="sxs-lookup"><span data-stu-id="405fd-226">With Office 365 PowerShell, you can get a list of mailboxes for all the people who live in the cities of Bloomington or San Diego with this command:</span></span>
  
```
Get-User | Where {$_.RecipientTypeDetails -eq "UserMailbox" -and ($_.City -eq "San Diego" -or $_.City -eq "Bloomington")} | Select DisplayName, City
```

<span data-ttu-id="405fd-227">Ниже приведен пример отображения.</span><span class="sxs-lookup"><span data-stu-id="405fd-227">Here is an example of the display:</span></span>
  
```
DisplayName                              City
-----------                              ----
Alex Darrow                              San Diego
Bonnie Kearney                           San Diego
Julian Isla                              Bloomington
Rob Young                                Bloomington
Zrinka Makovac                           San Diego
```

> [!TIP]
>  <span data-ttu-id="405fd-228">Эта команда PowerShell возвращает список всех пользователей в текущей подписке Office 365, имеющих почтовый ящик в городах Блумингтон или Сан-Диего (**Where {$\_.RecipientTypeDetails -eq "UserMailbox" -and ($\_.City -eq "San Diego" -or $\_.City -eq "Bloomington")}**), а затем отображает имя и город каждого из этих пользователей (**Select DisplayName, City**).</span><span class="sxs-lookup"><span data-stu-id="405fd-228">The interpretation of this Office 365 PowerShell command is: Get all of the users in the current Office 365 subscription who have a mailbox in the cities of either San Diego or Bloomington ( **Where {$\_.RecipientTypeDetails -eq "UserMailbox" -and ($\_.City -eq "San Diego" -or $\_.City -eq "Bloomington")}** ), then display the name and city for each ( **Select DisplayName, City** ).</span></span>
  
<span data-ttu-id="405fd-229">Чтобы отобразить список всех почтовых ящиков пользователей, проживающих в любом месте за исключением г. Блумингтон, используйте такую команду:</span><span class="sxs-lookup"><span data-stu-id="405fd-229">To list all the mailboxes for people who live anywhere except Bloomington, here is the command:</span></span>
  
```
Get-User | Where {$_.RecipientTypeDetails -eq "UserMailbox" -and $_.City -ne "Bloomington"} | Select DisplayName, City
```

<span data-ttu-id="405fd-230">Ниже приведен пример отображения.</span><span class="sxs-lookup"><span data-stu-id="405fd-230">Here is an example of the display:</span></span>
  
```
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
>  <span data-ttu-id="405fd-231">Эта команда PowerShell возвращает список всех пользователей в текущей подписке Office 365, почтовый ящик которых расположен не в г. Блумингтон ( **Where {$\_.RecipientTypeDetails -eq "UserMailbox" -and $\_.City -ne "Bloomington"}** ), а затем отображает имя и город каждого из этих пользователей.</span><span class="sxs-lookup"><span data-stu-id="405fd-231">The interpretation of this Office 365 PowerShell command is: Get all of the users in the current Office 365 subscription who have a mailbox not located in the city of Bloomington ( **Where {$\_.RecipientTypeDetails -eq "UserMailbox" -and $\_.City -ne "Bloomington"}** ), then display the name and city for each.</span></span>
  
<span data-ttu-id="405fd-p124">Кроме того, в фильтрах PowerShell в Office 365 можно использовать подстановочные знаки для поиска соответствия с частью имени. Предположим, вы ищете учетную запись пользователя, но помните только, что его фамилия или Андерсон, или Хендерсон, или, может быть, Йоргенсон.</span><span class="sxs-lookup"><span data-stu-id="405fd-p124">You can also use wildcard characters in your Office 365 PowerShell filters to match part of a name. For example, suppose you're looking for a user account, and all you can remember is that their last name was Anderson, or maybe Henderson, or maybe it was Jorgenson.</span></span>
  
<span data-ttu-id="405fd-234">Центр администрирования Office 365 позволяет найти этого пользователя, используя средство поиска для поиска пользователей с тремя фамилиями:</span><span class="sxs-lookup"><span data-stu-id="405fd-234">You could track down that user in the Office 365 admin center by using the search tool and carrying out three different searches:</span></span>
  
- <span data-ttu-id="405fd-235">*Андерсон*  ;</span><span class="sxs-lookup"><span data-stu-id="405fd-235">One for  *Anderson*</span></span> 
    
- <span data-ttu-id="405fd-236">*Хендерсон*  ;</span><span class="sxs-lookup"><span data-stu-id="405fd-236">One for  *Henderson*</span></span> 
    
- <span data-ttu-id="405fd-237">*Йоргенсон*  .</span><span class="sxs-lookup"><span data-stu-id="405fd-237">One for  *Jorgenson*</span></span> 
    
<span data-ttu-id="405fd-p125">Так как все три фамилии заканчиваются на "-сон", в PowerShell в Office 365 можно использовать команду для отображения всех пользователей, фамилия которых имеет такое окончание. Вот как это делается:</span><span class="sxs-lookup"><span data-stu-id="405fd-p125">Because all three of these names end in "son", you can tell Office 365 PowerShell to display all the users whose name ends in "son". Here is the command:</span></span>
  
```
Get-User -Filter '{LastName -like "*son"}'
```

> [!TIP]
>  <span data-ttu-id="405fd-p126">Эта команда PowerShell для Office 365 возвращает список всех пользователей в текущей подписке Office 365, при этом используется фильтр, отображающий только пользователей, чьи фамилии заканчиваются на "son" (**-Filter '{LastName -like "\*son"}'**). Символ \* означает любой набор знаков, в этом случае букв в фамилии пользователя.</span><span class="sxs-lookup"><span data-stu-id="405fd-p126">The interpretation of this Office 365 PowerShell command is: Get all of the users in the current Office 365 subscription, but use a filter that only lists the users whose last names end in "son" ( **-Filter '{LastName -like "\*son"}'** ). The \* stands for any set of characters, which are letters in the case of the user's last name.</span></span>
  
## <a name="office-365-powershell-makes-it-easy-to-print-or-save-data"></a><span data-ttu-id="405fd-242">PowerShell для Office 365 упрощает печать и сохранение данных</span><span class="sxs-lookup"><span data-stu-id="405fd-242">Office 365 PowerShell makes it easy to print or save data</span></span>
<span data-ttu-id="405fd-243"><a name="printsave"> </a></span><span class="sxs-lookup"><span data-stu-id="405fd-243"></span></span>

<span data-ttu-id="405fd-p127">Центр администрирования Office 365 позволяет просматривать списки данных. Ниже приведен пример, где в Центре администрирования Skype для бизнеса Online отображается список пользователей, для которых включено приложение Skype для бизнеса Online:</span><span class="sxs-lookup"><span data-stu-id="405fd-p127">The Office 365 admin center allows you to view lists of data. Here is an example of the Skype for Business Online Admin center displaying a list of users who have been enabled for Skype for Business Online:</span></span>
  
![Пример Центра администрирования Skype для бизнеса Online со списком пользователей, для которых включен Skype для бизнеса Online.](images/o365_powershell_lync_users.png)
  
<span data-ttu-id="405fd-p128">Чтобы сохранить эти данные в файл, необходимо их скопировать и вставить в документ или лист Excel. В любом случае может потребоваться дополнительное форматирование копии. Кроме того, Центр администрирования Office 365 не позволяет напрямую распечатать отображаемый список.</span><span class="sxs-lookup"><span data-stu-id="405fd-p128">To save that information to a file, you must copy and paste it into a document or Excel. In either case, the copy might require additional formatting. Additionally, the Office 365 admin center does not provide a way to directly print the displayed list.</span></span>
  
<span data-ttu-id="405fd-p129">К счастью, с помощью PowerShell в Office 365 можно не только отобразить список, но и сохранить его в файл, который легко импортировать в Excel. Ниже приведен пример команды, позволяющей сохранить пользовательские данные Skype для бизнеса Online в файл с разделителями-запятыми (CSV-файл), который легко импортировать в виде таблицы в лист Excel.</span><span class="sxs-lookup"><span data-stu-id="405fd-p129">Fortunately, you can use Office 365 PowerShell to not only display the list, but save it to a file that can be easily imported into Excel. Here is an example command to save Skype for Business Online user data to a comma-separated values (CSV) file, a file that can be easily imported as a table in an Excel worksheet:</span></span>
  
```
Get-CsOnlineUser | Select DisplayName, UserPrincipalName, UsageLocation | Export-Csv -Path "C:\\Logs\\SfBUsers.csv" -NoTypeInformation
```

<span data-ttu-id="405fd-252">Ниже приведен пример отображения.</span><span class="sxs-lookup"><span data-stu-id="405fd-252">Here is an example of the display:</span></span>
  
![Пример таблицы с данными пользователей Skype для бизнеса, импортированной на лист Excel и сохраненной в формате файла данных с разделителями-запятыми (CSV).](images/o365_powershell_data_in_excel.png)
  
> [!TIP]
>  <span data-ttu-id="405fd-254">Эта команда PowerShell для Office 365 возвращает список всех пользователей Skype для бизнеса Online в текущей подписке Office 365 (**Get-CsOnlineUser**), но отображает только имя, имя участника (UPN) и местонахождение пользователей (**Select DisplayName, UserPrincipalName, UsageLocation**), после чего сохраняет эту информацию в CSV-файле C:\\Logs\\SfBUsers.csv (**Export-Csv -Path "C:\\Logs\\SfBUsers.csv" -NoTypeInformation**).</span><span class="sxs-lookup"><span data-stu-id="405fd-254">The interpretation of this Office 365 PowerShell command is: Get all of the Skype for Business Online users in the current Office 365 subscription ( **Get-CsOnlineUser** ), obtain only the user name, UPN, and location ( **Select DisplayName, UserPrincipalName, UsageLocation** ), and then save that information in CSV file named C:\\Logs\\SfBUsers.csv ( **Export-Csv -Path "C:\\Logs\\SfBUsers.csv" -NoTypeInformation** ).</span></span>
  
<span data-ttu-id="405fd-p130">PowerShell также позволяет сохранить этот список в виде XML-файла или HTML-страницы. Кроме того, с помощью дополнительных команд PowerShell вы можете сохранить данные непосредственно в файл Excel, используя необходимое форматирование.</span><span class="sxs-lookup"><span data-stu-id="405fd-p130">You can also use options to save this list as an XML file or as an HTML page. In fact, with additional PowerShell commands, you could save it directly as an Excel file, with any custom formatting you desire.</span></span> 
  
<span data-ttu-id="405fd-p131">Список, возвращенный командой PowerShell в Office 365, можно также отправить непосредственно на принтер, используемый по умолчанию в Windows. Вот пример необходимой команды:</span><span class="sxs-lookup"><span data-stu-id="405fd-p131">You can also send the output of an Office 365 PowerShell command that displays a list directly to the default printer in Windows. Here is an example command:</span></span>
  
```
Get-CsOnlineUser | Select DisplayName, UserPrincipalName, UsageLocation | Out-Printer
```

<span data-ttu-id="405fd-259">Ниже показано, как будет выглядеть напечатанный документ.</span><span class="sxs-lookup"><span data-stu-id="405fd-259">Here's what your printed document will look like:</span></span>
  
![Пример документа, напечатанного напрямую на стандартном принтере в Windows в результате выполнения команды PowerShell для Office 365.](images/o365_powershell_printed_data.png)
  
> [!TIP]
>  <span data-ttu-id="405fd-261">Эта команда PowerShell возвращает список всех пользователей Skype для бизнеса Online в текущей подписке Office 365, но отображает только имя, имя участника (UPN) и расположение пользователей, после чего отправляет эту информацию на стандартный принтер Windows (**Out-Printer**).</span><span class="sxs-lookup"><span data-stu-id="405fd-261">The interpretation of this Office 365 PowerShell command is:  Get all of the Skype for Business Online users in the current Office 365 subscription, obtain only the user name, UPN, and location, and then send that information to the default Windows printer ( **Out-Printer** ).</span></span>
  
<span data-ttu-id="405fd-262">Распечатанный документ имеет то же простое форматирование, что и сведения, отображаемые в окне командной строки PowerShell для Office 365. Чтобы получить рабочую печатную копию, просто добавьте **| Out-Printer** в конец команды PowerShell для Office 365, которую вы создали, чтобы отобразить нужные данные.</span><span class="sxs-lookup"><span data-stu-id="405fd-262">The printed document has the same simple formatting as the display within the Office 365 PowerShell command window, but once you have created an Office 365 PowerShell command to list what you need, you just add **| Out-Printer** to the end of the command to get a hard copy to work from.</span></span>
  
## <a name="office-365-powershell-lets-you-manage-across-server-products"></a><span data-ttu-id="405fd-263">PowerShell для Office 365 позволяет управлять различными серверными продуктами</span><span class="sxs-lookup"><span data-stu-id="405fd-263">Office 365 PowerShell lets you manage across server products</span></span>
<span data-ttu-id="405fd-264"><a name="printsave"> </a></span><span class="sxs-lookup"><span data-stu-id="405fd-264"></span></span>

<span data-ttu-id="405fd-p132">Различные компоненты, составляющие Office 365:, предназначены для совместной работы. Предположим, вы добавляете нового пользователя в Office 365: и при этом указываете такие сведения, как его отдел и номер телефона. Эти сведения в дальнейшем будут доступны при получении доступа к данным пользователя с помощью любого из серверных продуктов Office 365:. Skype для бизнеса Online, Exchange или SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="405fd-p132">The different components that make up Office 365 are designed to work together. For example, suppose you add a new user to Office 365 and, when you do, you specify such information as the user's department and phone number. That information will then be available if you access the user's information using any of the Office 365 server products: Skype for Business Online, Exchange, or SharePoint Online.</span></span>
  
<span data-ttu-id="405fd-p133">Это общие сведения, распространяющиеся на набор продуктов. Сведения о конкретных продуктах, например информация о почтовом ящике Exchange пользователя, обычно недоступны во всех продуктах набора. Например, если вы хотите знать, включен ли почтовый ящик пользователя, то эти сведения доступны только в Центре администрирования Exchange.</span><span class="sxs-lookup"><span data-stu-id="405fd-p133">But that's for common information that spans the suite of products. Product-specific information-for example, information about a user's Exchange mailbox-is typically not available across the suite. For example, if you want to know if a user's mailbox is enabled or not, that information is available only in the Exchange Admin center.</span></span> 
  
<span data-ttu-id="405fd-271">Предположим, вы хотите создать отчет со следующим сведениями обо всех пользователях:</span><span class="sxs-lookup"><span data-stu-id="405fd-271">Suppose you'd like to make a report that shows the following information for all your users:</span></span>
  
- <span data-ttu-id="405fd-272">краткое имя пользователя;</span><span class="sxs-lookup"><span data-stu-id="405fd-272">The user's display name</span></span>
    
- <span data-ttu-id="405fd-273">наличие у пользователя лицензии на Office 365:;</span><span class="sxs-lookup"><span data-stu-id="405fd-273">Whether the user is licensed for Office 365</span></span>
    
- <span data-ttu-id="405fd-274">включен ли почтовый ящик Exchange пользователя;</span><span class="sxs-lookup"><span data-stu-id="405fd-274">Whether the user's Exchange mailbox has been enabled</span></span>
    
- <span data-ttu-id="405fd-275">включено ли для пользователя приложение Skype для бизнеса Online.</span><span class="sxs-lookup"><span data-stu-id="405fd-275">Whether the user is enabled for Skype for Business Online</span></span>
    
<span data-ttu-id="405fd-p134">В настоящее время создать такой отчет в средстве "Центр администрирования Office 365" непросто. Для этого вам придется создать отдельный документ для хранения сведений (например, лист Excel), использовать Центр администрирования Office 365, чтобы получить все имена и сведения о лицензировании пользователей, получить сведения о почтовом ящике из Центра администрирования Exchange, данные Skype для бизнеса Online из Центра администрирования Skype для бизнеса Online, а затем разобрать и объединить всю эту информацию.</span><span class="sxs-lookup"><span data-stu-id="405fd-p134">You currently cannot use the Office 365 admin center to easily produce such a report. Instead, you'll have to create a separate document to store the information, like an Excel worksheet, and get all the user names and licensing information from the Office 365 admin center, get mailbox information from the Exchange Admin center, get Skype for Business Online information from the Skype for Business Online Admin center, and then collate and combine that information.</span></span>
  
<span data-ttu-id="405fd-278">Вместо этого можно запустить сценарий PowerShell в Office 365, который составит для вас этот отчет.</span><span class="sxs-lookup"><span data-stu-id="405fd-278">The alternative is to use an Office 365 PowerShell script to compile that report for you.</span></span>
  
<span data-ttu-id="405fd-p135">Следующий пример сценария сложнее приведенных выше команд. Но он показывает преимущества PowerShell в Office 365 при создании представления данных, которое очень сложно получить другим способом. Вот сценарий, с помощью которого можно составить и отобразить необходимый список:</span><span class="sxs-lookup"><span data-stu-id="405fd-p135">The following example script is more complicated than the commands you have seen so far in this article. But, it shows the potential of using Office 365 PowerShell to create views of information that are very difficult to do otherwise. Here is the script that can compile and display the needed list:</span></span>
  
```
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

<span data-ttu-id="405fd-282">Ниже приведен пример отображения.</span><span class="sxs-lookup"><span data-stu-id="405fd-282">Here is an example of the display:</span></span>
  
```
DisplayName             IsLicensed   IsMailboxEnabled   EnabledForSfB
-----------             ----------   ----------------   --------------
Zrinka Makovac          True         True               True
Bonnie Kearney          True         True               True
Fabrice Canel           True         True               True
Brian Johnson           False        True               False
Anne Wallace            True         True               True
Alex Darrow             True         True               True
David Longmuir          True         True               True
Katy Jordan             False        True               False
Molly Dempsey           False        True               False
```

<span data-ttu-id="405fd-283">Этот сценарий PowerShell для Office 365 интерпретируется так:</span><span class="sxs-lookup"><span data-stu-id="405fd-283">The interpretation of this Office 365 PowerShell script is:</span></span>  
- <span data-ttu-id="405fd-284">Возвращается список всех пользователей в текущей подписке Office 365, после чего сведения сохраняются в переменной $x (**$x = Get-MsolUser**).</span><span class="sxs-lookup"><span data-stu-id="405fd-284">Get all of the users in the current Office 365 subscription and store the information in a variable named $x ( **$x = Get-MsolUser** ).</span></span>
- <span data-ttu-id="405fd-285">Запускается цикл для всех пользователей в переменной $x (**foreach ($i in $x)**).</span><span class="sxs-lookup"><span data-stu-id="405fd-285">Start a loop that runs over all the users in the variable named $x ( **foreach ($i in $x)** ).</span></span>  
- <span data-ttu-id="405fd-286">Определяется переменная $y, в которой сохраняются сведения о почтовом ящике пользователя (**$y = Get-Mailbox -Identity $i.UserPrincipalName**).</span><span class="sxs-lookup"><span data-stu-id="405fd-286">Define a variable named $y and store the user's mailbox information in it ( **$y = Get-Mailbox -Identity $i.UserPrincipalName** ).</span></span>
- <span data-ttu-id="405fd-287">К сведениям о пользователе добавляется новое свойство IsMailBoxEnabled, которое задается как значение свойства IsMailBoxEnabled почтового ящика пользователя (**$i | Add-Member -MemberType NoteProperty -Name IsMailboxEnabled -Value $y.IsMailboxEnabled**).</span><span class="sxs-lookup"><span data-stu-id="405fd-287">Add a new property to the user information named IsMailBoxEnabled and set it to the value of the IsMailBoxEnabled property of the user's mailbox ( **$i | Add-Member -MemberType NoteProperty -Name IsMailboxEnabled -Value $y.IsMailboxEnabled** ).</span></span>
- <span data-ttu-id="405fd-288">Определяется переменная $y, в которой сохраняются данные Skype для бизнеса Online пользователя (**$y = Get-CsOnlineUser -Identity $i.UserPrincipalName**).</span><span class="sxs-lookup"><span data-stu-id="405fd-288">Define a variable named $y and store the user's Skype for Business Online information in it ( **$y = Get-CsOnlineUser -Identity $i.UserPrincipalName** ).</span></span>
- <span data-ttu-id="405fd-289">К сведениям о пользователе добавляется новое свойство EnabledForSfB, которое задается как значение свойства Enabled для данных Skype для бизнеса Online пользователя (**$i | Add-Member -MemberType NoteProperty -Name EnabledForSfB -Value $y.Enabled**).</span><span class="sxs-lookup"><span data-stu-id="405fd-289">Add a new property to the user information named EnabledForSfB and set it to the value of the Enabled property of the user's Skype for Business Online information ( **$i | Add-Member -MemberType NoteProperty -Name EnabledForSfB -Value $y.Enabled** ).</span></span>
- <span data-ttu-id="405fd-290">Отображается список пользователей, в котором указаны только их имена, наличие лицензии и два новых свойства, которые указывают, включен ли почтовый ящик пользователей и могут ли они использовать Skype для бизнеса Online (**$x | Select DisplayName, IsLicensed, IsMailboxEnabled, EnabledforSfB**).</span><span class="sxs-lookup"><span data-stu-id="405fd-290">Display the list of users, but include only their name, whether they are licensed, and the two new properties that indicate whether their mailbox is enabled and whether they are enabled for Skype for Business Online ( **$x | Select DisplayName, IsLicensed, IsMailboxEnabled, EnabledforSfB** ).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="405fd-291">См. также</span><span class="sxs-lookup"><span data-stu-id="405fd-291">See also</span></span>


#### 

[<span data-ttu-id="405fd-292">Начало работы с PowerShell для Office 365</span><span class="sxs-lookup"><span data-stu-id="405fd-292">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
  
[<span data-ttu-id="405fd-293">Управление учетными записями и лицензиями пользователей с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="405fd-293">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="405fd-294">Использование Windows PowerShell для создания отчетов в Office 365</span><span class="sxs-lookup"><span data-stu-id="405fd-294">Use Windows PowerShell to create reports in Office 365</span></span>](use-windows-powershell-to-create-reports-in-office-365.md)

