---
title: Интеграция с Exchange Online для среды разработки и тестирования Office 365 и Dynamics 365
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
ms.custom: Ent_TLGs
ms.assetid: 499c5823-427a-4ba2-8fc1-9553bc2ff2d3
description: Сводка. Воспользуйтесь этим руководством, чтобы включить интеграцию Dynamics 365 для Exchange Online в пробной подписке Office 365.
ms.openlocfilehash: be79f58f448799bba9c4a9ee51350f198d721e0d
ms.sourcegitcommit: 4ef8e113fa20b539de1087422455fc26ff123d55
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "30574023"
---
# <a name="exchange-online-integration-for-your-office-365-and-dynamics-365-devtest-environment"></a><span data-ttu-id="81112-103">Интеграция с Exchange Online для среды разработки и тестирования Office 365 и Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="81112-103">Exchange Online integration for your Office 365 and Dynamics 365 dev/test environment</span></span>

 <span data-ttu-id="81112-104">**Сводка.** Воспользуйтесь этим руководством, чтобы включить интеграцию Dynamics 365 для Exchange Online в пробной подписке Office 365.</span><span class="sxs-lookup"><span data-stu-id="81112-104">**Summary:** Use this Test Lab Guide to enable Dynamics 365 integration for Exchange Online in your Office 365 trial subscription.</span></span>
  
<span data-ttu-id="81112-p101">Microsoft Dynamics 365 позволяет хранить всю переписку с клиентами в одном месте, чтобы каждый, у кого есть необходимые разрешения, мог ее просмотреть. Например, просмотреть всю электронную почту, связанную с определенным контактом, учетной записью, возможной сделкой или обращением.</span><span class="sxs-lookup"><span data-stu-id="81112-p101">A valuable use of Microsoft Dynamics 365 is to store all customer communications in one place, so anyone with the appropriate permissions can see all relevant customer records. For example, view all email associated with a particular contact, account, opportunity, or case.</span></span>
  
<span data-ttu-id="81112-p102">Чтобы хранить электронную почту и другие сообщения в Dynamics 365, вам необходимо синхронизировать свою систему электронной почты с Dynamics 365. Предпочтительным методом является синхронизация на стороне сервера.</span><span class="sxs-lookup"><span data-stu-id="81112-p102">To store email and other messaging records in Dynamics 365, you need to synchronize your email system with Dynamics 365. Server-side synchronization is the method of choice for email synchronization.</span></span>
  
<span data-ttu-id="81112-109">Воспользуйтесь этим руководством, чтобы настроить и продемонстрировать, как Exchange Online и клиент Outlook Online могут использовать информацию, хранящуюся в Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="81112-109">Use this Test Lab Guide to configure and demonstrate how Exchange Online and the Outlook Online client can leverage the information stored in Dynamics 365.</span></span> 
  
## <a name="phase-1-build-out-the-office-365-and-dynamics-365-devtest-environment"></a><span data-ttu-id="81112-110">Этап 1. Создание среды разработки и тестирования Office 365 и Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="81112-110">Phase 1: Build out the Office 365 and Dynamics 365 dev/test environment</span></span>

<span data-ttu-id="81112-111">Воспользуйтесь инструкциями в [Среда разработки и тестирования для Office 365 и Dynamics 365](office-365-and-dynamics-365-dev-test-environment.md), чтобы создать упрощенную или условную корпоративную среду разработки и тестирования Office 365 и Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="81112-111">Use the instructions in [Office 365 and Dynamics 365 dev/test environment](office-365-and-dynamics-365-dev-test-environment.md) to create either a lightweight or simulated enterprise version of an Office 365 and Dynamics 365 dev/test environment.</span></span>
  
> [!NOTE]
> <span data-ttu-id="81112-p103">Для настройки, описанной в этой статье, не требуется условная корпоративная среда разработки и тестирования, которая включает условную интрасеть, подключенную к Интернету, и синхронизацию каталогов для леса Windows Server Active Directory (AD). Она представлена здесь лишь для того, чтобы вы могли поэкспериментировать с Office 365 и Dynamics 365 в типичной среде организации.</span><span class="sxs-lookup"><span data-stu-id="81112-p103">The configuration in this article does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server Active Directory (AD) forest. It is provided here as an option so that you can experiment with Office 365 and Dynamics 365 in an environment that represents a typical organization</span></span> 
  
## <a name="phase-2-configure-and-demonstrate-dynamics-365-integration-in-exchange-online"></a><span data-ttu-id="81112-114">Этап 2. Настройка и демонстрация интеграции с Dynamics 365 в Exchange Online</span><span class="sxs-lookup"><span data-stu-id="81112-114">Phase 2: Configure and demonstrate Dynamics 365 integration in Exchange Online</span></span>

<span data-ttu-id="81112-115">Выполните следующие действия, чтобы настроить почтовый ящик глобального администратора для интеграции Dynamics 365 и Exchange Online:</span><span class="sxs-lookup"><span data-stu-id="81112-115">Use these steps to configure the global administrator's mailbox for Dynamics 365 and Exchange Online integration:</span></span>
  
1. <span data-ttu-id="81112-116">С помощью личного сеанса работы с браузером перейдите к [http://admin.microsoft.com](http://admin.microsoft.com) учетной записи глобального администратора Office 365 и войдите в нее.</span><span class="sxs-lookup"><span data-stu-id="81112-116">Using a private session of your browser, go to [http://admin.microsoft.com](http://admin.microsoft.com) and sign in using your Office 365 global administrator account.</span></span>
    
2. <span data-ttu-id="81112-117">На **домашней странице Microsoft Office** щелкните плитку **Почта**.</span><span class="sxs-lookup"><span data-stu-id="81112-117">On the **Microsoft Office Home** page, click the **Mail** tile.</span></span>
    
3. <span data-ttu-id="81112-118">На вкладке Новая **почта** в браузере нажмите кнопку **создать** и обратите внимание на то, что нижний угол области под полем для ввода сообщения имеет значок для шаблонов "Мои шаблоны".</span><span class="sxs-lookup"><span data-stu-id="81112-118">On the new **Mail** tab in your browser, click **New** and notice how the bottom corner of the pane below the box for typing a message has an icon for My Templates.</span></span>
    
     ![Пустое новое сообщение электронной почты без интеграции с Dynamics 365.](media/879b54fd-a68f-4581-9f89-d5050df6f4de.png)
  
4. <span data-ttu-id="81112-120">Нажмите **Отменить** и оставьте вкладку **Почта** открытой.</span><span class="sxs-lookup"><span data-stu-id="81112-120">Click **Discard** and leave the **Mail** tab open.</span></span>
    
5. <span data-ttu-id="81112-121">Перейдите на вкладку **Домашняя страница Microsoft Office** и щелкните плитку **Администратор**.</span><span class="sxs-lookup"><span data-stu-id="81112-121">Click the **Microsoft Office Home** tab in your browser, and then click the **Admin** tile.</span></span>
    
6. <span data-ttu-id="81112-122">На вкладке **Office Admin center**, в области навигации слева, выберите **Центры администрирования > Dynamics 365**.</span><span class="sxs-lookup"><span data-stu-id="81112-122">In the left navigation of the **Office Admin center** tab, click **Admin centers > Dynamics 365**.</span></span>
    
7. <span data-ttu-id="81112-123">На новой вкладке **Dynamics 365**, в списке экземпляров Dynamics 365, нажмите **Открыть**.</span><span class="sxs-lookup"><span data-stu-id="81112-123">On the new **Dynamics 365** tab in your browser, in the list of Dynamics 365 instances, click **Open**.</span></span>
    
8. <span data-ttu-id="81112-124">На новой вкладке **Администрирование**, на панели навигации, щелкните стрелку вниз рядом с кнопкой **Параметры** и выберите **Настройка электронной почты** в разделе **Система**.</span><span class="sxs-lookup"><span data-stu-id="81112-124">On the new **Administration** tab in your browser, on the navigation bar, click the down arrow next to **Settings**, and then click **Email Configuration** under **System**.</span></span>
    
9.  <span data-ttu-id="81112-125">На странице **Настройка электронной почты** выберите **Настройки конфигурации электронной почты**.</span><span class="sxs-lookup"><span data-stu-id="81112-125">On the **Email Configuration** page, click **Email Configuration Settings**.</span></span>
    
10. <span data-ttu-id="81112-126">На вкладке **Электронная почта** диалогового окна **Системные параметры** измените метод синхронизации **Встречи, контакты и задачи** на **Синхронизация на стороне сервера** и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="81112-126">In the **Email** tab on the **System Settings** dialog box, change **Appointments, Contacts, and Tasks** to **Server-Side Synchronization**, and then click **OK**.</span></span>
    
11. <span data-ttu-id="81112-127">На странице **Настройка электронной почты** нажмите **Почтовые ящики**.</span><span class="sxs-lookup"><span data-stu-id="81112-127">On the **Email Configuration** page, click **Mailboxes**.</span></span>
    
12. <span data-ttu-id="81112-128">Поставьте флажок возле имени глобального администратора Office 365, нажмите **Применить настройки электронной почты по умолчанию** на панели инструментов и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="81112-128">Select the Office 365 global administrator name in the left check mark column, click **Apply Default Email Settings** in the tool bar, and then click **OK**.</span></span>
    
13. <span data-ttu-id="81112-129">Нажмите **Утвердить адрес электронной почты** на панели инструментов и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="81112-129">Click **Approve Email** in the tool bar, and then click **OK**.</span></span>
    
14. <span data-ttu-id="81112-130">Поставьте флажок возле имени глобального администратора Office 365, нажмите **Проверить и включить почтовые ящики** на панели инструментов и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="81112-130">Select the Office 365 global administrator name in the left check mark column, click **Test &amp; Enable Mailboxes** in the tool bar, and then click **OK**.</span></span>
    
15. <span data-ttu-id="81112-131">Откройте вкладку **Почта** и убедитесь, что глобальный администратор получил тестовое сообщение.</span><span class="sxs-lookup"><span data-stu-id="81112-131">Click the open **Mail** tab and confirm that the global administrator received a test message.</span></span>
    
16. <span data-ttu-id="81112-p104">Вернитесь на вкладку **Почтовые ящики Мои активные почтовые ящики** и обновите страницу. В столбцах **Состояние входящих сообщений электронной почты** и **Состояние исходящих сообщений электронной почты** должно быть указано **Успех** для имени учетной записи глобального администратора. Обратите внимание, что выполнение обоих тестов может занять до 15 минут.</span><span class="sxs-lookup"><span data-stu-id="81112-p104">Return to the **Mailboxes My Active Mailboxes** tab in your browser and refresh the page. The **Incoming Email Status** and **Outgoing Email Status** columns should be set to **Success** for the global administrator account name. Note that it can take up to 15 minutes to complete both tests.</span></span>
    
<span data-ttu-id="81112-135">Выполните следующие действия, чтобы установить приложение Dynamics 365 для Outlook и продемонстрировать функции Dynamics 365 в почтовом ящике глобального администратора:</span><span class="sxs-lookup"><span data-stu-id="81112-135">Use these steps to install the Dynamics 365 App for Outlook and demonstrate Dynamics 365 features within the global administrator's mailbox:</span></span>
  
1. <span data-ttu-id="81112-136">На вкладке **Почтовые ящики Мои активные почтовые ящики** щелкните стрелку вниз рядом с кнопкой **Параметры** и выберите **Приложение Dynamics 365 для Outlook** в разделе **Система**.</span><span class="sxs-lookup"><span data-stu-id="81112-136">On the **Mailboxes My Active Mailboxes** tab in your browser, click the down arrow next to **Settings**, and then click **Dynamics 365 App for Outlook** under **System**.</span></span>
    
2. <span data-ttu-id="81112-p105">На странице **Приступая к работе с приложением Microsoft Dynamics 365 для Outlook** выберите имя глобального администратора и нажмите **Добавить приложение в Outlook**. Значение в столбце **Состояние** изменится на **В ожидании**.</span><span class="sxs-lookup"><span data-stu-id="81112-p105">On the **Getting Started with Microsoft Dynamics 365 App for Outlook** page, click the global administrator name, and then click **Add App to Outlook**. The **Status** column changes to **Pending**.</span></span>
    
3. <span data-ttu-id="81112-p106">Обновляйте страницу, пока состояние не изменится на **Добавлено в Outlook**. Обратите внимание, что выполнение этой настройки может занять до 15 минут.</span><span class="sxs-lookup"><span data-stu-id="81112-p106">Refresh the page until the status changes to **Added to Outlook**. Note that it can take up to 15 minutes to complete this configuration.</span></span>
    
4. <span data-ttu-id="81112-141">Перейдите на вкладку **Почта** и закройте ее.</span><span class="sxs-lookup"><span data-stu-id="81112-141">Click on the **Mail** tab in your browser and then close it.</span></span>
    
5. <span data-ttu-id="81112-142">Откройте вкладку **Домашняя страница Microsoft Office** и щелкните плитку **Почта**.</span><span class="sxs-lookup"><span data-stu-id="81112-142">Click the **Microsoft Office Home** tab in your browser, and then click the **Mail** tile.</span></span>
    
6. <span data-ttu-id="81112-143">На новой вкладке **Почта** нажмите **Создать**.</span><span class="sxs-lookup"><span data-stu-id="81112-143">On the new **Mail** tab in your browser, click **New**.</span></span> <span data-ttu-id="81112-144">Обратите внимание, что в нижнем углу области под полем для ввода сообщения теперь есть значок Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="81112-144">Notice that the bottom corner of the pane below the box for typing a message now has an icon for Dynamics 365.</span></span>
    
     ![Пустое новое сообщение с интеграцией с Dynamics 365; отображается новый значок.](media/ecb822e1-45fe-4481-99a1-294317d1d2de.png)
  
7. <span data-ttu-id="81112-p108">Щелкните значок Dynamics 365. Вы увидите панель **Dynamics 365**, на которой сможете отслеживать это сообщение, а также просматривать шаблоны, литературу и статьи.</span><span class="sxs-lookup"><span data-stu-id="81112-p108">Click the Dynamics 365 icon. You should see a **Dynamics 365** pane, from which you can track this email or access templates, sales literature, or articles.</span></span>
    
8. <span data-ttu-id="81112-p109">В поле **Кому** сообщения электронной почты введите **alex.y.wu@outlook.com** и нажмите **Повторить** на панели **Dynamics 365**. Вы увидите раздел **Получатели** на панели **Dynamics 365** с информацией о контакте Alex Wu из приложения "Продажи", в которое в рамках пробной подписки были добавлены демонстрационные данные.</span><span class="sxs-lookup"><span data-stu-id="81112-p109">In the **To** field of the email message, type **alex.y.wu@outlook.com**, and then click **Retry** in the **Dynamics 365** pane. You should see a **Recipients** section in the **Dynamics 365** pane with information on Alex Wu, a contact from the sales application that was provided with the sample data for your trial subscription.</span></span>
    
     ![Область сведений для контакта по продажам, сохраненного в Dynamics 365.](media/a010fa5f-3f1b-47d4-ab5e-d00d85a24a3f.png)
  
9. <span data-ttu-id="81112-151">Нажмите **Отменить**.</span><span class="sxs-lookup"><span data-stu-id="81112-151">Click **Discard**.</span></span>

> [!TIP]
> <span data-ttu-id="81112-152">Щелкните [здесь](http://aka.ms/catlgstack), чтобы просмотреть схему всех статей, относящихся к руководствам по лаборатории тестирования Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="81112-152">Click [here](http://aka.ms/catlgstack) for a visual map to all of the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="81112-153">См. также</span><span class="sxs-lookup"><span data-stu-id="81112-153">See Also</span></span>

[<span data-ttu-id="81112-154">Среда разработки и тестирования для Office 365 и Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="81112-154">Office 365 and Dynamics 365 dev/test environment</span></span>](office-365-and-dynamics-365-dev-test-environment.md)
  
[<span data-ttu-id="81112-155">Руководства по лаборатории тестирования для принятия облачных решений</span><span class="sxs-lookup"><span data-stu-id="81112-155">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="81112-156">Базовая конфигурация среды разработки и тестирования</span><span class="sxs-lookup"><span data-stu-id="81112-156">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="81112-157">Среда разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="81112-157">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="81112-158">DirSync для среды разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="81112-158">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)

[<span data-ttu-id="81112-159">Управление подпиской для Dynamics 365 (сетевая версия)</span><span class="sxs-lookup"><span data-stu-id="81112-159">Subscription Management for Dynamics 365 (online)</span></span>](https://technet.microsoft.com/library/jj679903.aspx)
  
[<span data-ttu-id="81112-160">Администрирование Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="81112-160">Administering Dynamics 365</span></span>](https://technet.microsoft.com/library/dn531101.aspx)


