---
title: Восстановление удаленных элементов в почтовом ящике пользователя — справка для администраторов
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: 6/29/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BCS160
ms.assetid: eb15194b-63ec-41b0-8d90-1823d3f558e4
description: 'Эта статья предназначена для администраторов. Пользователя окончательно удалить элементы из их почтовых ящиков Outlook? Пользователь хочет их обратно, но не могут восстанавливать их. Можно восстановить удаленные элементы, если они еще не были удалены окончательно из почтового ящика пользователя. '
ms.openlocfilehash: abfc0a1a35d8e694197e12d05a2206dd4e3eb37a
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542368"
---
# <a name="recover-deleted-items-in-a-user-mailbox---admin-help"></a><span data-ttu-id="897fa-106">Восстановление удаленных элементов в почтовом ящике пользователя — справка для администраторов</span><span class="sxs-lookup"><span data-stu-id="897fa-106">Recover deleted items in a user mailbox - Admin Help</span></span>

<span data-ttu-id="897fa-p102">**Эта статья предназначена для администраторов. Вы пытаетесь восстановить удаленные элементы в собственных почтовых ящиков?** Выполните одно из следующих действий.</span><span class="sxs-lookup"><span data-stu-id="897fa-p102">**This article is for administrators. Are you trying to recover deleted items in your own mailbox?** Try one of the following:</span></span>
- [<span data-ttu-id="897fa-109">Восстановление удаленных элементов в Outlook для Windows</span><span class="sxs-lookup"><span data-stu-id="897fa-109">Recover deleted items in Outlook for Windows</span></span>](https://support.office.com/article/49e81f3c-c8f4-4426-a0b9-c0fd751d48ce)
- [<span data-ttu-id="897fa-110">Восстановление удаленных элементов или электронной почты в Outlook Web App</span><span class="sxs-lookup"><span data-stu-id="897fa-110">Recover deleted items or email in Outlook Web App</span></span>](https://support.office.com/article/c3d8fc15-eeef-4f1c-81df-e27964b7edd4)
- [<span data-ttu-id="897fa-111">Восстановление удаленных сообщений электронной почты в Outlook в Интернете</span><span class="sxs-lookup"><span data-stu-id="897fa-111">Restore deleted email messages in Outlook on the web</span></span>](https://support.office.com/article/a8ca78ac-4721-4066-95dd-571842e9fb11)
- [<span data-ttu-id="897fa-112">Outlook.com</span><span class="sxs-lookup"><span data-stu-id="897fa-112">Outlook.com</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=623435)
   
<span data-ttu-id="897fa-p103">Пользователя окончательно удалить элементы из их почтовых ящиков Outlook? Пользователь хочет их обратно, но не могут восстанавливать их. Можно восстановить удаленные элементы, если они еще не были удалены окончательно из почтового ящика пользователя. Это сделать с помощью средства обнаружения электронных данных на месте в Exchange Online для поиска удаленного электронной почты и другие элементы, например контакты, события календаря и задачи и — в почтовом ящике пользователя. Если поиск удаленных элементов, их можно экспортировать в PST-файл (также называемая файла данных Outlook), который пользователь затем можно использовать для восстановления элементов вернуться к своему почтовому ящику.</span><span class="sxs-lookup"><span data-stu-id="897fa-p103">Did a user permanently delete items from their Outlook mailbox? The user wants them back but can't recover them. You may be able recover the purged items if they haven't been permanently removed from the user's mailbox. You do this by using the In-Place eDiscovery tool in Exchange Online to search for deleted email and other items—and such as contacts, calendar appointments, and tasks—in a user's mailbox. If you find the deleted items, you can export them to a PST file (also called an Outlook Data File), which the user can then use to restore the items back to their mailbox.</span></span>
  
<span data-ttu-id="897fa-p104">Далее приведены шаги для восстановления удаленных элементов в почтовом ящике пользователя. Сколько времени это займет? В первый раз может занимать 20 или 30 минут, чтобы выполнить все действия, в зависимости от того, сколько элементов выполняется восстановление.</span><span class="sxs-lookup"><span data-stu-id="897fa-p104">Here are the steps for recovering deleted items in a user's mailbox. How long will this take? The first time might take 20 or 30 minutes to complete all the steps, depending on how many items you're trying to recover.</span></span>
  
> [!NOTE]
> <span data-ttu-id="897fa-p105">Необходимо быть **администратором Exchange** или **глобального администратора** в Office 365 или быть членом группы ролей управления организацией в Exchange Online для выполнения действия, описанные в этой статье. Дополнительные сведения см в [роли администраторов об Office 365](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d).</span><span class="sxs-lookup"><span data-stu-id="897fa-p105">You have to be an **Exchange administrator** or **Global administrator** in Office 365 or be a member of the Organization Management role group in Exchange Online to perform the steps in this article. For more information, see [About Office 365 admin roles](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d).</span></span> 
  
## <a name="step-1-assign-yourself-ediscovery-permissions"></a><span data-ttu-id="897fa-123">Шаг 1: Присвойте себе разрешения обнаружения электронных данных</span><span class="sxs-lookup"><span data-stu-id="897fa-123">Step 1: Assign yourself eDiscovery permissions</span></span>
<span data-ttu-id="897fa-124"><a name="step1"> </a></span><span class="sxs-lookup"><span data-stu-id="897fa-124"></span></span>

<span data-ttu-id="897fa-p106">Первым этапом является Присвойте себе необходимые разрешения в Exchange Online, можно использовать средство обнаружения электронных данных на месте для поиска почтового ящика пользователя. Имеется только один раз это сделать. Если требуется выполнить поиск другого почтового ящика в будущем, этот шаг можно пропустить.</span><span class="sxs-lookup"><span data-stu-id="897fa-p106">The first step is to assign yourself the necessary permissions in Exchange Online so you can use the In-Place eDiscovery tool to search a user's mailbox. You only have to do this once. If you have to search another mailbox in the future, you can skip this step.</span></span>
  
1. <span data-ttu-id="897fa-128">[Where для входа в Office 365 для бизнеса](https://support.office.com/article/e9eb7d51-5430-4929-91ab-6157c5a050b4) с помощью учетной записи рабочего или школы.</span><span class="sxs-lookup"><span data-stu-id="897fa-128">[Where to sign in to Office 365 for business](https://support.office.com/article/e9eb7d51-5430-4929-91ab-6157c5a050b4) with your work or school account.</span></span> 
    
2. <span data-ttu-id="897fa-129">Выберите значок запуска приложения ![значок запуска приложения в Office 365](media/7502f4ec-3c9a-435d-a7b4-b9cda85189a7.png) в левом верхнем углу и выберите пункты **администратор**.</span><span class="sxs-lookup"><span data-stu-id="897fa-129">Select the app launcher icon ![The app launcher icon in Office 365](media/7502f4ec-3c9a-435d-a7b4-b9cda85189a7.png) in the upper-left and click **Admin**.</span></span>
    
3. <span data-ttu-id="897fa-130">В левой области навигации в центре администрирования Office 365 разверните узел **центра администрирования**и нажмите кнопку **Exchange**.</span><span class="sxs-lookup"><span data-stu-id="897fa-130">In the left navigation in the Office 365 admin center, expand **Admin centers**, and then click **Exchange**.</span></span>
    
    ![Список центра администрирования](media/7d308eb7-ba63-4156-a845-3770facc5de4.PNG)
  
4. <span data-ttu-id="897fa-132">В центре администрирования Exchange выберите **разрешения**и нажмите кнопку **роли администраторов**.</span><span class="sxs-lookup"><span data-stu-id="897fa-132">In the Exchange admin center, click **Permissions**, and then click **Admin roles**.</span></span>
    
5. <span data-ttu-id="897fa-133">В представлении списка выберите **Управление обнаружением**и нажмите кнопку **Изменить**![значок Правка](media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif).</span><span class="sxs-lookup"><span data-stu-id="897fa-133">In the list view, select **Discovery Management**, and then click **Edit**![Edit icon](media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif).</span></span>
    
    ![Добавьте себя в группу ролей "Управление обнаружением" в центре администрирования Exchange](media/e5c98e93-d6a0-40c5-a143-bac956eedaa7.png)
  
6. <span data-ttu-id="897fa-135">В **Группе ролей**, в разделе **члены**, нажмите кнопку **Добавить**![значком Добавить](media/8ee52980-254b-440b-99a2-18d068de62d3.gif).</span><span class="sxs-lookup"><span data-stu-id="897fa-135">In **Role Group**, under **Members**, click **Add**![Add icon](media/8ee52980-254b-440b-99a2-18d068de62d3.gif).</span></span>
    
7. <span data-ttu-id="897fa-136">В списке **Выбрать элементы**выберите список имен, нажмите кнопку **Добавить**и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="897fa-136">In **Select Members**, select yourself from the list of names, click **Add**, and then click **OK**.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="897fa-p107">Также можно добавить группу, что вы являетесь участником, например Управление организацией или TenantAdmins. При добавлении группы, другие участники группы будут назначаться необходимые разрешения для запуска средства обнаружения электронных данных на месте.</span><span class="sxs-lookup"><span data-stu-id="897fa-p107">You can also add a group that you are a member of, such as Organization Management or TenantAdmins. If you add a group, other members of the group will be assigned the necessary permissions to run the In-Place eDiscovery tool.</span></span> 
  
8. <span data-ttu-id="897fa-139">В разделе **Группа ролей** щелкните **Сохранить**.</span><span class="sxs-lookup"><span data-stu-id="897fa-139">In **Role Group**, click **Save**.</span></span>
    
9. <span data-ttu-id="897fa-140">Выход из Office 365.</span><span class="sxs-lookup"><span data-stu-id="897fa-140">Sign out of Office 365.</span></span>
    
    <span data-ttu-id="897fa-141">Необходимо выйти, прежде чем начать следующий шаг, чтобы новые разрешения вступили в силу.</span><span class="sxs-lookup"><span data-stu-id="897fa-141">You have to sign out before you start the next step so the new permissions will take effect.</span></span>
    
> [!CAUTION]
> <span data-ttu-id="897fa-p108">Участники группы ролей управления обнаружения можно обращаться к содержимого конфиденциальные сообщения. Это включает в себя поиск всех почтовых ящиков в организации, предварительный просмотр результатов поиска (и других элементов почтового ящика), копирование результатов в почтовый ящик найденных сообщений и экспорт результатов поиска в PST-файл.</span><span class="sxs-lookup"><span data-stu-id="897fa-p108">Members of the Discovery Management role group can access sensitive message content. This includes searching all mailboxes in your organization, previewing the search results (and other mailbox items), copying the results to a discovery mailbox, and exporting the search results to a PST file.</span></span> 
  
[<span data-ttu-id="897fa-144">Return to top</span><span class="sxs-lookup"><span data-stu-id="897fa-144">Return to top</span></span>](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="step-2-search-the-users-mailbox-for-deleted-items"></a><span data-ttu-id="897fa-145">Шаг 2: Поиск почтового ящика пользователя для удаленных элементов</span><span class="sxs-lookup"><span data-stu-id="897fa-145">Step 2: Search the user's mailbox for deleted items</span></span>
<span data-ttu-id="897fa-146"><a name="step2"> </a></span><span class="sxs-lookup"><span data-stu-id="897fa-146"></span></span>

<span data-ttu-id="897fa-p109">При выполнении поиска методом электронного обнаружения на месте папки восстанавливаемых элементов в почтовом ящике, которые искать автоматически включается в поиск. Папка элементов для восстановления — без возможности восстановления удаленных элементов хранения до их в случае очищены (удалены) из почтового ящика. Таким образом Если элемент не был удален, можно найти с помощью средства обнаружения электронных данных на месте.</span><span class="sxs-lookup"><span data-stu-id="897fa-p109">When you run an In-Place eDiscovery search, the Recoverable Items folder in the mailbox that you search is automatically included in the search. The Recoverable Items folder is where permanently deleted items are stored until they're purged (permanently removed) from the mailbox. So, if an item hasn't been purged, you should be able to find it by using the In-Place eDiscovery tool.</span></span>
  
1. <span data-ttu-id="897fa-150">[Where для входа в Office 365 для бизнеса](https://support.office.com/article/e9eb7d51-5430-4929-91ab-6157c5a050b4) с помощью учетной записи рабочего или школы.</span><span class="sxs-lookup"><span data-stu-id="897fa-150">[Where to sign in to Office 365 for business](https://support.office.com/article/e9eb7d51-5430-4929-91ab-6157c5a050b4) with your work or school account.</span></span> 
    
2. <span data-ttu-id="897fa-151">Выберите значок запуска приложения ![значок запуска приложения в Office 365](media/7502f4ec-3c9a-435d-a7b4-b9cda85189a7.png) в левом верхнем углу и выберите пункты **администратор**.</span><span class="sxs-lookup"><span data-stu-id="897fa-151">Select the app launcher icon ![The app launcher icon in Office 365](media/7502f4ec-3c9a-435d-a7b4-b9cda85189a7.png) in the upper-left and click **Admin**.</span></span>
    
3. <span data-ttu-id="897fa-152">В левой области переходов центра администрирования Office 365 разверните **Admin**и щелкните **Exchange**.</span><span class="sxs-lookup"><span data-stu-id="897fa-152">In the left navigation in the Office 365 admin center, expand **Admin**, and then click **Exchange**.</span></span>
    
4. <span data-ttu-id="897fa-153">В центре администрирования Exchange выберите **Управление соответствием требованиям**, нажмите кнопку **In-Place eDiscovery &amp; хранения**и нажмите кнопку **Создать**![значком Добавить](media/8ee52980-254b-440b-99a2-18d068de62d3.gif).</span><span class="sxs-lookup"><span data-stu-id="897fa-153">In the Exchange admin center, click **Compliance management**, click **In-Place eDiscovery &amp; Hold**, and then click **New**![Add icon](media/8ee52980-254b-440b-99a2-18d068de62d3.gif).</span></span>
    
    ![В центре администрирования Exchange на странице Управление соответствием требованиям щелкните электронного обнаружения на месте и хранение](media/9d9ff0f5-b9be-45b8-8b5e-6037a856b0a8.png)
  
5. <span data-ttu-id="897fa-155">На странице **имя и описание** введите имя для поиска (например, имя пользователя в случае восстановление сообщения электронной почты), описание и нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="897fa-155">On the **Name and description** page, type a name for the search (such as the name of the user you're recovering email for), an optional description, and then click **Next**.</span></span>
    
6. <span data-ttu-id="897fa-156">На странице " **почтовые ящики** " нажмите кнопку **выбрать почтовые ящики для поиска**и нажмите кнопку **Добавить**![значком Добавить](media/8ee52980-254b-440b-99a2-18d068de62d3.gif).</span><span class="sxs-lookup"><span data-stu-id="897fa-156">On the **Mailboxes** page, click **Specify mailboxes to search**, and then click **Add**![Add icon](media/8ee52980-254b-440b-99a2-18d068de62d3.gif).</span></span>
    
    ![Нажмите кнопку выбрать почтовые ящики для поиска для поиска в почтовом ящике особую](media/83879a40-5e5c-49a8-be3b-c0023d197588.png)
  
7. <span data-ttu-id="897fa-158">Найдите и выберите имя пользователя, который восстановление удаленного сообщения электронной почты, нажмите кнопку **Добавить**и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="897fa-158">Find and select the name of the user that you're recovering the deleted email for, click **Add**, and then click **OK**.</span></span>
    
8. <span data-ttu-id="897fa-159">Нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="897fa-159">Click **Next**.</span></span>
    
    <span data-ttu-id="897fa-p110">Откроется страница **поискового запроса** . Здесь указывается, где можно определить условия поиска, которые помогут вам найти отсутствующие элементы в почтовом ящике пользователя.</span><span class="sxs-lookup"><span data-stu-id="897fa-p110">The **Search query** page is displayed. This is where you define the search criteria that will help you find the missing items in user's mailbox.</span></span> 
    
9. <span data-ttu-id="897fa-162">На странице **Поисковый запрос** заполните следующие поля:</span><span class="sxs-lookup"><span data-stu-id="897fa-162">On the **Search query** page, complete the following fields:</span></span> 
    
  - <span data-ttu-id="897fa-p111">**Включить все содержимое** Установите этот флажок, чтобы включить все содержимое в почтовом ящике пользователя в результатах поиска. Если выбран этот параметр, нельзя будет указать дополнительные критерии поиска.</span><span class="sxs-lookup"><span data-stu-id="897fa-p111">**Include all content** Select this option to include all content in the user's mailbox in the search results. If you select this option, you can't specify additional search criteria.</span></span> 
    
  - <span data-ttu-id="897fa-165">**Фильтр на основе критериев** Установите этот флажок, чтобы задать условия поиска, включая ключевые слова, запуск и завершить даты, отправителя и адреса получателей и типов сообщений.</span><span class="sxs-lookup"><span data-stu-id="897fa-165">**Filter based on criteria** Select this option to specify the search criteria, including keywords, start and end dates, sender and recipient addresses, and message types.</span></span> 
    
    ![Построение поиска, на основе критерия, такие как ключевые слова, диапазон дат, получателей и типы сообщений](media/ee47b833-9122-46a0-85e6-fcbe25be0dd5.png)
  
|<span data-ttu-id="897fa-167">**Поле**</span><span class="sxs-lookup"><span data-stu-id="897fa-167">**Field**</span></span>|<span data-ttu-id="897fa-168">**Используйте этот код для...**</span><span class="sxs-lookup"><span data-stu-id="897fa-168">**Use this to...**</span></span>|
|:-----|:-----|
|![Номер один в розовым круг](media/a4da261d-2516-48c5-b58a-9c452b9086b8.png)           <br/> |<span data-ttu-id="897fa-170">Укажите ключевые слова, диапазон дат, получателей и типов сообщений.</span><span class="sxs-lookup"><span data-stu-id="897fa-170">Specify keywords, date range, recipients, and message types.</span></span>  <br/> |
|![Номер два в розовым круг.](media/de3c1ab4-4f01-4026-b1ba-3265bdb32a89.png)           <br/> |<span data-ttu-id="897fa-172">Поиск сообщений с помощью ключевых слов или фраз и использовать логические операторы, такие как **AND** или **OR**.</span><span class="sxs-lookup"><span data-stu-id="897fa-172">Search for messages with keywords or phrases, and use logical operators such as **AND** or **OR**.</span></span>  <br/> |
|![Номер три в розовым круг.](media/60fa378c-6ac1-4cbd-a782-2fa7ca619dc6.png)           <br/> |<span data-ttu-id="897fa-174">Поиск сообщений, отправленных или полученных в диапазон дат.</span><span class="sxs-lookup"><span data-stu-id="897fa-174">Search for messages sent or received within a date range.</span></span>  <br/> |
|![Число 4 в розовым круг.](media/1a0ff2ce-0942-405a-94e3-9bfeb1e5059e.png)           <br/> |<span data-ttu-id="897fa-176">Поиск сообщений, полученных от или отправленных определенным получателям.</span><span class="sxs-lookup"><span data-stu-id="897fa-176">Search for messages received from or sent to specific people.</span></span>  <br/> |
|![Номер пяти розовым кружок.](media/878cc815-0165-49ba-a1ee-9236e5980403.png)           <br/> |<span data-ttu-id="897fa-178">Поиск всех типов сообщений или выберите определенные из них.</span><span class="sxs-lookup"><span data-stu-id="897fa-178">Search for all message types or select specific ones.</span></span>  <br/> |
   
    > [!TIP]
    >  Here's a few tips about how to build a search query to find missing items. Try to get as much information from the user to help you create a search query so you can find what you're looking for. >  If you not sure how to find a missing message, consider using the **Include all content** option. The search results will include all items in the user's Recoverable Items folder, including the hidden folder (called the Purges folder) that contain items that have been purged by the user. Then you can go to Step 3, copy the results to a discovery mailbox, and look at the message in the hidden folder. >  If you know approximately when the missing message was originally sent or received by the user, use the **Specify start date** and **Specify end date** options to provide a date range. This will return all messages sent or received by the user within that date range. Specifying a date range is a really good way to narrow the search results. >  If you know who sent the missing email, use the **From** box to specify this sender. >  If you want to narrow the search results to different types of mailbox items, click **Select message types**, click **Select the message types to search**, and then choose a specific message type to search for. For example, you can search only for calendar items or contacts. Here's a screenshot of the different message types you can search for; the default is to search for all message types. 
  
    Click **Next** when you've completed the **Search query** page. 
    
10. <span data-ttu-id="897fa-p112">На странице " **Параметры хранения на месте** " нажмите кнопку **Готово** , чтобы начать поиск. Для восстановления удаленных сообщений, нет причин для помещения почтового ящика пользователя на удержание.</span><span class="sxs-lookup"><span data-stu-id="897fa-p112">On the **In-Place Hold settings** page, click **Finish** to start the search. To recover deleted email, there's no reason to place the user's mailbox on hold.</span></span> 
    
    <span data-ttu-id="897fa-181">После запуска поиска Exchange будет отображаться оценку общего размера и количества элементов, которые будут возвращены службой поиска, на основе критерия, указанному.</span><span class="sxs-lookup"><span data-stu-id="897fa-181">After you start the search, Exchange will display an estimate of the total size and number of items that will be returned by the search based on the criteria you specified.</span></span>
    
11. <span data-ttu-id="897fa-p113">Выберите только что созданную поиска и нажмите кнопку **Обновить**![обновить](media/165fb3ad-38a8-4dd9-9e76-296aefd96334.png) обновить сведения, отображаемые в области сведений. Состояние **Оценки успешно завершена** указывает, что поиск завершено. Exchange также отображает оценку общее число элементов (и их размер), найти, поиск, основанный на условия поиска, указанного на шаге 9.</span><span class="sxs-lookup"><span data-stu-id="897fa-p113">Select the search you just created and click **Refresh**![refresh](media/165fb3ad-38a8-4dd9-9e76-296aefd96334.png) to update the information displayed in the details pane. The status of **Estimate Succeeded** indicates that the search has finished. Exchange also displays an estimate of the total number of items (and their size) found by the search based on the search criteria you specified in step 9.</span></span> 
    
12. <span data-ttu-id="897fa-p114">В области сведений щелкните **Просмотр результатов поиска** для просмотра элементов, которые были найдены. Это может помочь определить элементы, вы ищете. Если элементы, которые вы пытаетесь восстановить, перейдите к шагу 4, чтобы экспортировать результаты поиска в PST-файл.</span><span class="sxs-lookup"><span data-stu-id="897fa-p114">In the details pane, click **Preview search results** to view the items that were found. This might help you identify the item(s) that you're looking for. If you find the item(s) you're trying to recover, go to step 4 to export the search results to a PST file.</span></span> 
    
    ![Нажмите кнопку Просмотр результатов поиска для просмотра элемента, который вы пытаетесь восстановить](media/a2cea921-dafa-45d6-97d4-ae45a226b8d3.png)
  
13. <span data-ttu-id="897fa-p115">Если найти не удалось, можно просмотреть и изменить критерии поиска, выбрав поиск, нажав кнопку **Изменить**![значок Правка](media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif)и затем выбрав **поисковый запрос**. Изменение условий поиска, а затем повторите поиск.</span><span class="sxs-lookup"><span data-stu-id="897fa-p115">If you don't find what you're looking for, you can revise your search criteria by selecting the search, clicking **Edit**![Edit icon](media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif), and then clicking **Search query**. Change the search criteria and then rerun the search.</span></span>
    
[<span data-ttu-id="897fa-191">Return to top</span><span class="sxs-lookup"><span data-stu-id="897fa-191">Return to top</span></span>](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="optional-step-3-copy-the-search-results-to-a-discovery-mailbox"></a><span data-ttu-id="897fa-192">(Необязательно) Шаг 3: Копирование результатов поиска в почтовый ящик обнаружения</span><span class="sxs-lookup"><span data-stu-id="897fa-192">(Optional) Step 3: Copy the search results to a discovery mailbox</span></span>
<span data-ttu-id="897fa-193"><a name="step3"> </a></span><span class="sxs-lookup"><span data-stu-id="897fa-193"></span></span>

<span data-ttu-id="897fa-p116">Если вы не можете найти элементов Предварительный просмотр результатов поиска или для просмотра элементов, которые находятся в папке элементов для восстановления пользователя, затем можно скопировать результаты поиска специальных почтового ящика (называемые почтового ящика обнаружения) и откройте этот почтовый ящик в Outlook в Интернете t o Просмотр фактических элементов. Основная причина для копирования результатов поиска — для просмотра элементов в папке элементов для восстановления пользователя. Более чем вероятно элемент, который вы пытаетесь восстановить находится во вложенной папке удаляет.</span><span class="sxs-lookup"><span data-stu-id="897fa-p116">If you can't find an items by previewing the search results or if you want to see which items are in the user's Recoverable Items folder, then you can copy the search results to a special mailbox (called a discovery mailbox) and then open that mailbox in Outlook on the web to view the actual items. The best reason to copy the search results is so you can view the items in the user's Recoverable Items folder. More than likely, the item you're trying to recover is located in the Purges subfolder.</span></span> 
  
1. <span data-ttu-id="897fa-197">В центре администрирования Exchange перейдите к **разделу Управление соответствием требованиям** \> **In-Place eDiscovery &amp; хранения**.</span><span class="sxs-lookup"><span data-stu-id="897fa-197">In the Exchange admin center, go to **Compliance management** \> **In-Place eDiscovery &amp; Hold**.</span></span>
    
2. <span data-ttu-id="897fa-198">В списке поиска выберите поиска, созданной на шаге 2.</span><span class="sxs-lookup"><span data-stu-id="897fa-198">In the list of searches, select the search that you created in Step 2.</span></span>
    
3. <span data-ttu-id="897fa-199">Щелкните **Поиск**![поиска](media/c94e8591-7044-4650-a0d1-c57c0633ab4f.png)и нажмите кнопку **Копировать результаты поиска** из раскрывающегося списка.</span><span class="sxs-lookup"><span data-stu-id="897fa-199">Click **Search**![search](media/c94e8591-7044-4650-a0d1-c57c0633ab4f.png), and then click **Copy search results** from the drop-down list.</span></span> 
    
    ![Нажмите кнопку поиска и нажмите кнопку Копировать результаты поиска](media/7888df82-94b4-4e44-8a53-f66854dc7c86.png)
  
4. <span data-ttu-id="897fa-201">На странице **Результатов поиска копии** нажмите кнопку **Обзор**.</span><span class="sxs-lookup"><span data-stu-id="897fa-201">On the **Copy Search Results** page, click **Browse**.</span></span>
    
    ![Оставьте флажки не выбран, если восстановление удаленных элементов](media/37f27999-a5b2-4fed-87e2-bad6dc23cdae.png)
  
5. <span data-ttu-id="897fa-203">В поле **Отображаемое имя**выберите **Почтовый ящик обнаружения поиска**и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="897fa-203">Under **Display Name**, click **Discovery Search Mailbox**, and then click **OK**.</span></span>
    
    ![Копирование результатов поиска для поиска почтового ящика обнаружения по умолчанию](media/36e8ef47-0035-4982-9ed6-426719c5f9ec.png)
  
    > [!NOTE]
    > <span data-ttu-id="897fa-205">Почтовый ящик обнаружения поиска является почтового ящика обнаружения по умолчанию, которая создается автоматически в организации Office 365.</span><span class="sxs-lookup"><span data-stu-id="897fa-205">The Discovery Search Mailbox is a default discovery mailbox that is automatically created in your Office 365 organization.</span></span> 
  
6. <span data-ttu-id="897fa-206">На странице **Результатов поиска копии** щелкните **копии** для начала процесса для копирования результатов поиска в почтовый ящик поиска обнаружения.</span><span class="sxs-lookup"><span data-stu-id="897fa-206">Back on the **Copy Search Results** page, click **Copy** to start the process to copy the search results to the Discovery Search Mailbox.</span></span> 
    
    ![Нажмите кнопку Копировать, чтобы скопировать результаты поиска в почтовый ящик обнаружения поиска](media/71307a9d-f7a1-4e01-ae37-1d49040cc3fd.png)
  
7. <span data-ttu-id="897fa-208">Нажмите кнопку **Обновить**![обновить](media/165fb3ad-38a8-4dd9-9e76-296aefd96334.png) для обновления сведений о ходе выполнения копирования, который отображается в области сведений.</span><span class="sxs-lookup"><span data-stu-id="897fa-208">Click **Refresh**![refresh](media/165fb3ad-38a8-4dd9-9e76-296aefd96334.png) to update the information about the copying status that is displayed in the details pane.</span></span> 
    
8. <span data-ttu-id="897fa-209">По завершении копирования нажмите кнопку **Открыть** , чтобы открыть почтовый ящик обнаружения поиска для просмотра результатов поиска.</span><span class="sxs-lookup"><span data-stu-id="897fa-209">When the copying is complete, click **Open** to open the Discovery Search Mailbox to view the search results.</span></span> 
    
    ![Нажмите кнопку Открыть, чтобы перейти к почтовому ящику поиска обнаружения для просмотра результатов поиска](media/6cc81e0f-ceed-4464-9040-79b6f920de35.png)
  
    <span data-ttu-id="897fa-p117">Результаты поиска, Копировать в почтовый ящик поиска обнаружения, помещаются в папку с тем же именем как поиск обнаружения электронных данных на месте. Нажмите папку для отображения элементов в этой папке.</span><span class="sxs-lookup"><span data-stu-id="897fa-p117">The search results copied to the Discovery Search Mailbox are placed in a folder that has the same name as the In-Place eDiscovery search. You can click a folder to display the items in that folder.</span></span>
    
    ![Результаты поиска в почтовом ящике поиска обнаружения; элементы в папке удаляет можно восстанавливать только с администратором](media/2ef8e5fb-3e63-4f62-938e-307efe9f6998.gif)
  
    <span data-ttu-id="897fa-p118">При выполнении поиска, папки элементов для восстановления также поиск. Это означает, что если элементов в папке элементов для восстановления не отвечает условия поиска, они включаются в результаты поиска. Элементы в папке удалений являются элементы, которые пользователь окончательного удаления (путем удаления элемента из папки «Удаленные» или, выбрав его и нажав клавишу **Shift + Delete**. Пользователя можно использовать средство восстановить удаленные элементы в Outlook или Outlook в Интернете для восстановления элементов в папке удалений. Элементы в папке удаляет: элементы, удаленные пользователя с помощью средства восстановления удаленных элементов или элементов, которые автоматически удалено политикой, применяемые к почтовому ящику. В любом случае только администратор может восстанавливать элементы в папке удаляет.</span><span class="sxs-lookup"><span data-stu-id="897fa-p118">When you run a search, the user's Recoverable Items folder is also searched. That means if items in the Recoverable Items folder meet the search criteria, they are included in the search results. Items in the Deletions folder are items that the user permanently deleted (by deleting an item from the Deleted Items folder or by selecting it and pressing **Shift+Delete**. A user can use the Recover Deleted Items tool in Outlook or Outlook on the web to recover items in the Deletions folder. Items in the Purges folder are items that the user purged by using the Recover Deleted Items tool or items they were automatically purged by a policy applied to the mailbox. In either case, only an admin can recover items in the Purges folder.</span></span> 
    
    > [!TIP]
    > <span data-ttu-id="897fa-p119">Если пользователь не удается найти удаленного элемента с помощью средства восстановления элементов, но этот элемент будет по-прежнему можно восстановить (то есть, что оно не было удалено без возможности восстановления из почтового ящика), он скорее находится в папке удаляет. Таким образом не забудьте удаляет папку для удаленных элементов, которые вы пытаетесь восстановить для пользователя.</span><span class="sxs-lookup"><span data-stu-id="897fa-p119">If a user can't find a deleted item using the Recoverable Items tool, but that item is still recoverable (meaning that it hasn't been permanently removed from the mailbox), it's more than likely located in the Purges folder. So, be sure to look in the Purges folder for the deleted item you're trying to recover for a user.</span></span> 
  
[<span data-ttu-id="897fa-222">Return to top</span><span class="sxs-lookup"><span data-stu-id="897fa-222">Return to top</span></span>](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="step-4-export-the-search-results-to-a-pst-file"></a><span data-ttu-id="897fa-223">Шаг 4: Экспорт результатов поиска в PST-файл</span><span class="sxs-lookup"><span data-stu-id="897fa-223">Step 4: Export the search results to a PST file</span></span>
<span data-ttu-id="897fa-224"><a name="step4"> </a></span><span class="sxs-lookup"><span data-stu-id="897fa-224"></span></span>

<span data-ttu-id="897fa-p120">После найдите элемент, который вы пытаетесь восстановить для пользователя, следующим шагом является экспортировать результаты поиска, выполняемого на шаге 2 PST-файл. Пользователь будет использовать этот PST-файл на следующем этапе для восстановления удаленных элементов в свой почтовый ящик.</span><span class="sxs-lookup"><span data-stu-id="897fa-p120">After you find the item you're trying to recover for a user, the next step is to export the results from the search you ran in Step 2 to a PST file. The user will use this PST file in the next step to restore the deleted item to their mailbox.</span></span>
  
1. <span data-ttu-id="897fa-227">В центре администрирования Exchange перейдите к **разделу Управление соответствием требованиям** \> **In-Place eDiscovery &amp; хранения**.</span><span class="sxs-lookup"><span data-stu-id="897fa-227">In the Exchange admin center, go to **Compliance management** \> **In-Place eDiscovery &amp; Hold**.</span></span>
    
2. <span data-ttu-id="897fa-228">В списке поиска выберите поиска, созданной на шаге 2.</span><span class="sxs-lookup"><span data-stu-id="897fa-228">In the list of searches, select the search that you created in Step 2.</span></span>
    
3. <span data-ttu-id="897fa-229">Нажмите кнопку **Экспорт в PST-файл**.</span><span class="sxs-lookup"><span data-stu-id="897fa-229">Click **Export to a PST file**.</span></span>
    
    ![Нажмите кнопку Экспорт в PST-файл](media/4e59ae17-4541-43f4-a6d1-1f8b9ba9404b.png)
  
4. <span data-ttu-id="897fa-231">Если вам будет предложено установить средство экспорта обнаружения электронных данных, выберите команду **выполнить**.</span><span class="sxs-lookup"><span data-stu-id="897fa-231">If you're prompted to install the eDiscovery Export Tool, click **Run**.</span></span>
    
5. <span data-ttu-id="897fa-232">Возможности обнаружения электронных данных средство экспорта PST-файлов нажмите кнопку **Обзор** , чтобы указать расположение, где нужно загрузить PST-файл.</span><span class="sxs-lookup"><span data-stu-id="897fa-232">In the eDiscovery PST Export Tool, click **Browse** to specify the location where you want to download the PST file.</span></span> 
    
    ![Средство экспорта PST обнаружения электронных данных](media/17274d27-992e-4034-8133-8f793f554e6c.png)
  
    <span data-ttu-id="897fa-234">Параметры для включения дедупликации и включаются элементы, не включаемые можно игнорировать.</span><span class="sxs-lookup"><span data-stu-id="897fa-234">You can ignore the options to enable deduplication and include unsearchable items.</span></span>
    
6. <span data-ttu-id="897fa-235">Нажмите кнопку **запустить** , чтобы загрузить PST-файл на своем компьютере.</span><span class="sxs-lookup"><span data-stu-id="897fa-235">Click **Start** to download the PST file to your computer.</span></span> 
    
    <span data-ttu-id="897fa-p121">**Средство экспорта PST обнаружения электронных данных** сведения о состоянии процесса экспорта. После завершения экспорта можно открыть файл в расположение, где он был загружен.</span><span class="sxs-lookup"><span data-stu-id="897fa-p121">The **eDiscovery PST Export Tool** displays status information about the export process. When the export is complete, you can access the file in the location where it was downloaded.</span></span> 
    
[<span data-ttu-id="897fa-238">Return to top</span><span class="sxs-lookup"><span data-stu-id="897fa-238">Return to top</span></span>](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="step-5-restore-the-recovered-items-to-the-users-mailbox"></a><span data-ttu-id="897fa-239">Шаг 5: Восстановление восстановленные элементы в почтовом ящике пользователя</span><span class="sxs-lookup"><span data-stu-id="897fa-239">Step 5: Restore the recovered items to the user's mailbox</span></span>
<span data-ttu-id="897fa-240"><a name="step5"> </a></span><span class="sxs-lookup"><span data-stu-id="897fa-240"></span></span>

<span data-ttu-id="897fa-p122">Последним шагом является использование PST-файл, который был экспортирован на шаге 4 для восстановления восстановленные элементы в почтовом ящике пользователя. После отправки PST-файл в пользователя в оставшейся части этот шаг выполняется пользователем, чтобы открыть PST-файл и затем переместить восстановленные элементы в другую папку в почтовом ящике. Для получения пошаговых инструкций можно также отправить пользователя ссылки в этом разделе: [открытия и закрытия файлы данных Outlook (PST)](https://support.office.com/article/381b776d-7511-45a0-953a-0935c79d24f2). Или можно отправить ссылку пользователя в представленном ниже разделе [Восстановить удаленные элементы в почтовом ящике с использованием PST-файл](recover-deleted-items-in-a-mailbox.md#restoredeleteditems) с просьбой выполните описанные ниже действия.</span><span class="sxs-lookup"><span data-stu-id="897fa-p122">The final step is to use the PST file that was exported in step 4 to restore the recovered items to the user's mailbox. After you send the PST file to the user, the remainder of this step is performed by the user to open the PST file and then move the recovered items to another folder in their mailbox. For step-by-step instructions, you can also send the user a link to this topic: [Open and close Outlook Data Files (.pst)](https://support.office.com/article/381b776d-7511-45a0-953a-0935c79d24f2). Or you can send the user a link to the [Restore deleted items to a mailbox using a PST file](recover-deleted-items-in-a-mailbox.md#restoredeleteditems) section below and ask them to perform these steps.</span></span> 
  
 <span data-ttu-id="897fa-245">**Отправить PST-файл для пользователя**</span><span class="sxs-lookup"><span data-stu-id="897fa-245">**Send the PST file to the user**</span></span>
  
<span data-ttu-id="897fa-p123">Последний этап, которые необходимо выполнить отправляет PST-файл, который был экспортирован на шаге 4 для пользователя. Для этого несколькими способами:</span><span class="sxs-lookup"><span data-stu-id="897fa-p123">The final step that you need to perform is sending the PST file that was exported in step 4 to the user. There are a few ways to do this:</span></span>
  
- <span data-ttu-id="897fa-p124">PST-файл с подключением к сообщению электронной почты. Если Outlook настроена для блокировки PST-файлов, будут иметь ZIP-файл и вложения в сообщение. Вот как:</span><span class="sxs-lookup"><span data-stu-id="897fa-p124">Attach the PST file to an email message. If Outlook is configured to block PST files, then you will have to zip the file and then attach it to the message. Here's how:</span></span>
    
1. <span data-ttu-id="897fa-251">В проводнике Windows или проводник перейдите к файлу PST-файлов.</span><span class="sxs-lookup"><span data-stu-id="897fa-251">In Windows Explorer or File Explorer, browse to the PST file.</span></span>
    
2. <span data-ttu-id="897fa-p125">Щелкните правой кнопкой мыши файл, а затем выберите **Отправить** \> **сжатый ZIP-папку**. Windows создает новые ZIP-файл и присваивает ему такое же имя, как PST-файл.</span><span class="sxs-lookup"><span data-stu-id="897fa-p125">Right-click the file, and then select **Send to** \> **Compressed (zipped) folder**. Windows creates a new zip file and gives it an identical name as the PST file.</span></span>
    
3. <span data-ttu-id="897fa-254">Присоединение сжатых PST-файл в сообщение электронной почты и отправьте его для пользователя, который затем Распаковка файла, щелкнув его.</span><span class="sxs-lookup"><span data-stu-id="897fa-254">Attach the compressed PST file to an email message and send it to the user, who can then decompress the file just by clicking it.</span></span>
    
- <span data-ttu-id="897fa-255">Скопируйте PST-файл в общей папке, что пользователь может получить доступ к и извлекать его.</span><span class="sxs-lookup"><span data-stu-id="897fa-255">Copy the PST file to a shared folder that the user can access and retrieve it.</span></span>
    
<span data-ttu-id="897fa-256">Действия, описанные в следующем разделе будут выполняться пользователем, для восстановления удаленных элементов в свой почтовый ящик.</span><span class="sxs-lookup"><span data-stu-id="897fa-256">The steps in the next section are performed by the user to restore the deleted items to their mailbox.</span></span>
  
 <span data-ttu-id="897fa-257">**Восстановление удаленных элементов в почтовом ящике с использованием PST-файл**</span><span class="sxs-lookup"><span data-stu-id="897fa-257">**Restore deleted items to a mailbox using a PST file**</span></span>
  
<span data-ttu-id="897fa-p126">Необходимо использовать настольного приложения Outlook для восстановления удаленного элемента с помощью PST-файл. Чтобы открыть в PST-файл нельзя использовать Outlook Web App или Outlook в Интернете.</span><span class="sxs-lookup"><span data-stu-id="897fa-p126">You have to use the Outlook desktop app to restore a deleted item by using a PST file. You can't use Outlook Web App or Outlook on the web to open a PST file.</span></span>
  
1. <span data-ttu-id="897fa-260">В Outlook 2013 или Outlook 2016 перейдите на вкладку **файл** .</span><span class="sxs-lookup"><span data-stu-id="897fa-260">In Outlook 2013 or Outlook 2016, click the **File** tab.</span></span> 
    
2. <span data-ttu-id="897fa-261">Нажмите кнопку **Open &amp; Экспорт**и нажмите кнопку **Открыть файл данных Outlook**.</span><span class="sxs-lookup"><span data-stu-id="897fa-261">Click **Open &amp; Export**, and then click **Open Outlook Data File**.</span></span>
    
3. <span data-ttu-id="897fa-262">Перейдите к папке, в которой вы сохранили файл PST-файлов, отправленных к администратору.</span><span class="sxs-lookup"><span data-stu-id="897fa-262">Browse to the location where you saved the PST file that your administrator sent.</span></span>
    
4. <span data-ttu-id="897fa-263">Выберите PST-файлов и нажмите кнопку **Открыть**.</span><span class="sxs-lookup"><span data-stu-id="897fa-263">Select the PST and then click **Open**.</span></span>
    
    <span data-ttu-id="897fa-264">PST-файл появится в левой навигационной панели в Outlook.</span><span class="sxs-lookup"><span data-stu-id="897fa-264">The PST file appears in the left-nav bar in Outlook.</span></span>
    
    ![PST-файл появится в левой навигационной панели в Outlook](media/c9389392-d08a-4aa7-848c-4986d448b0f2.png)
  
5. <span data-ttu-id="897fa-266">С помощью стрелок разверните PST-файл и папки под ним найдите элемент, который вы хотите восстановить.</span><span class="sxs-lookup"><span data-stu-id="897fa-266">Click the arrows to expand the PST file and the folders under it to locate the item you want to recover.</span></span>
    
    ![Удаляет папку для элемента, который вы хотите восстановить](media/d4e372d9-ac23-4e95-8639-d8da690fefa7.png)
  
    > [!TIP]
    > <span data-ttu-id="897fa-p127">Найдите в папке удаляет элемент, который вы хотите восстановить. Это скрытый папка, которая очищены элементы будут перенесены. Это скорее всего элемента, который является администратором восстановлены в этой папке.</span><span class="sxs-lookup"><span data-stu-id="897fa-p127">Look in the Purges folder for the item you want to recover. This is a hidden folder that purged items are moved to. It's likely the item that your administrator recovered is in this folder.</span></span> 
  
6. <span data-ttu-id="897fa-271">Щелкните правой кнопкой мыши элемент, который необходимо восстановить и выберите команду **переместить** \> **Другие папки**.</span><span class="sxs-lookup"><span data-stu-id="897fa-271">Right-click the item you want to recover and then click **Move** \> **Other Folder**.</span></span>
    
    ![Выберите переместить, а затем выберите другие папки](media/090063df-2aa0-444a-8e47-abd6fe6cf7a8.png)
  
7. <span data-ttu-id="897fa-273">Чтобы переместить элемент в папку "Входящие", нажмите кнопку **"Входящие"** и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="897fa-273">To move the item to your inbox, click **Inbox**, and then click **OK**.</span></span>
    
    <span data-ttu-id="897fa-274">**Совет:** Для восстановления других типов элементов, выполните одно из следующих действий.</span><span class="sxs-lookup"><span data-stu-id="897fa-274">**Tip:** To recover other types of items, do one of the following:</span></span> 
    
  - <span data-ttu-id="897fa-275">Восстановление элемента календаря, щелкните его правой кнопкой мыши и выберите команду **переместить** \> **Другие папки** \> **календаря**.</span><span class="sxs-lookup"><span data-stu-id="897fa-275">To recover a calendar item, right-click it, and then click **Move** \> **Other Folder** \> **Calendar**.</span></span>
    
  - <span data-ttu-id="897fa-276">Чтобы восстановить контакт, щелкните его правой кнопкой мыши и выберите команду **переместить** \> **Другие папки** \> **Контакты**.</span><span class="sxs-lookup"><span data-stu-id="897fa-276">To recover a contact, right-click it, and then click **Move** \> **Other Folder** \> **Contacts**.</span></span>
    
  - <span data-ttu-id="897fa-277">Чтобы восстановить задачи, щелкните его правой кнопкой мыши и выберите команду **переместить** \> **Другие папки** \> **задачи**.</span><span class="sxs-lookup"><span data-stu-id="897fa-277">To recover a task, right-click it, and then click **Move** \> **Other Folder** \> **Tasks**.</span></span>
    
![Выберите папку для перемещения других типов элементов](media/f8290131-43f2-46f1-bc07-228c2d83b96c.png)
  
    Note that calendar items, contacts, and tasks are located directly in the Purges folder, and not in a Calendar, Contacts, or Tasks subfolder. However, you can sort by **Type** to group similar types of items. 
    
8. <span data-ttu-id="897fa-279">После завершения работы восстановление удаленных элементов, щелкните правой кнопкой мыши PST-файл в панели навигации слева и выберите **Закрыть «имя PST-файл»**.</span><span class="sxs-lookup"><span data-stu-id="897fa-279">When you're finished recovering deleted items, right-click the PST file in the left-nav bar and select **Close "name of PST file"**.</span></span>
    
[<span data-ttu-id="897fa-280">К началу страницы</span><span class="sxs-lookup"><span data-stu-id="897fa-280">Return to top</span></span>](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="more-information"></a><span data-ttu-id="897fa-281">Дополнительные сведения</span><span class="sxs-lookup"><span data-stu-id="897fa-281">More information</span></span>
<span data-ttu-id="897fa-282"><a name="moreinfo"> </a></span><span class="sxs-lookup"><span data-stu-id="897fa-282"></span></span>

- <span data-ttu-id="897fa-p128">Возможно, пользователь может восстановить без возможности восстановления удаленных элементов, если еще не истек срок хранения удаленного элемента для элемента. Как администратор, которые могут возникнуть указанного сколько элементов в папке элементов для восстановления доступны для восстановления. Например могут возникнуть политики, в котором удаляются все действия, которое было в папки "Удаленные" пользователя в течение 30 дней и другую политику, которая позволяет пользователям восстановление элементов в папке элементов для восстановления до другого 14 дней. Тем не менее через этот 14 дней, по-прежнему можно восстановить элемента в почтовом ящике пользователя с помощью процедур, описанных в этом разделе.</span><span class="sxs-lookup"><span data-stu-id="897fa-p128">It might be possible for a user to recover a permanently deleted item if the deleted item retention period for the item hasn't expired. As an admin you may have specified how long items in the Recoverable Items folder are available for recovery. For example, there might be a policy that deletes anything that's been in a user's Deleted Items folder for 30 days, and another policy that lets users recover items in the Recoverable Items folder for up to another 14 days. However, after this 14 days, you may still be able to recover an item in a user's mailbox by using the procedures in this topic.</span></span>
    
- <span data-ttu-id="897fa-p129">Пользователей можно восстановить удаленный элемент, если он еще не был удален и еще не истек срок хранения удаленного элемента для этого элемента. Чтобы помочь пользователям восстановление удаленных элементов в почтовом ящике, их наведите указатель на один из следующих разделов:</span><span class="sxs-lookup"><span data-stu-id="897fa-p129">Users can recover a deleted item if it hasn't been purged and if the deleted item retention period for that item hasn't expired. To help users recover deleted items in their mailbox, point them to one of the following topics:</span></span>
    
  - [<span data-ttu-id="897fa-289">Восстановление удаленных элементов в Outlook для Windows</span><span class="sxs-lookup"><span data-stu-id="897fa-289">Recover deleted items in Outlook for Windows</span></span>](https://support.office.com/article/49e81f3c-c8f4-4426-a0b9-c0fd751d48ce)
    
  - [<span data-ttu-id="897fa-290">Восстановление удаленных элементов в Outlook 2010</span><span class="sxs-lookup"><span data-stu-id="897fa-290">Recover deleted items in Outlook 2010</span></span>](https://support.office.com/article/cd9dfe12-8e8c-4a21-bbbf-4bd103a3f1fe)
    
  - [<span data-ttu-id="897fa-291">Восстановление удаленных элементов или электронной почты в Outlook Web App</span><span class="sxs-lookup"><span data-stu-id="897fa-291">Recover deleted items or email in Outlook Web App</span></span>](https://support.office.com/article/c3d8fc15-eeef-4f1c-81df-e27964b7edd4)
    
  - [<span data-ttu-id="897fa-292">Восстановление удаленных сообщений электронной почты в Outlook в Интернете</span><span class="sxs-lookup"><span data-stu-id="897fa-292">Restore deleted email messages in Outlook on the web</span></span>](https://support.office.com/article/a8ca78ac-4721-4066-95dd-571842e9fb11)
    
  - [<span data-ttu-id="897fa-293">Восстановление удаленных контактов в Outlook</span><span class="sxs-lookup"><span data-stu-id="897fa-293">Recover a deleted contact in Outlook</span></span>](https://support.office.com/article/51c83288-6888-4dcd-8c99-4932daabf643)
    
  - [<span data-ttu-id="897fa-294">Восстановление удаленных сообщений электронной почты в Outlook.com</span><span class="sxs-lookup"><span data-stu-id="897fa-294">Restore deleted email messages in Outlook.com</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=623435)
    
[<span data-ttu-id="897fa-295">Return to top</span><span class="sxs-lookup"><span data-stu-id="897fa-295">Return to top</span></span>](recover-deleted-items-in-a-mailbox.md#__top)
  

