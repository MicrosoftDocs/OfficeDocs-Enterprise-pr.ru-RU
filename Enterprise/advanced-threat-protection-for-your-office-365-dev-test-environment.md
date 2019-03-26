---
title: Advanced Threat Protection в среде разработки и тестирования Office 365
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
ms.assetid: 51019757-20ac-498c-b51e-cae6d41a8c08
description: Сводка. Настройка и демонстрация Office 365 Advanced Threat Protection в среде разработки и тестирования Office 365.
ms.openlocfilehash: 9870f666a979d00ce6621e9459a1f9ad236f9799
ms.sourcegitcommit: 4ef8e113fa20b539de1087422455fc26ff123d55
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "30573833"
---
# <a name="advanced-threat-protection-for-your-office-365-devtest-environment"></a><span data-ttu-id="76588-103">Advanced Threat Protection в среде разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="76588-103">Advanced Threat Protection for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="76588-104">**Сводка.** Настройка и демонстрация Office 365 Advanced Threat Protection в среде разработки и тестирования Office 365.</span><span class="sxs-lookup"><span data-stu-id="76588-104">**Summary:** Configure and demonstrate Office 365 Advanced Threat Protection in your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="76588-105">Office 365 Advanced Threat Protection — это компонент Exchange Online Protection (EOP), позволяющий оградить электронную почту от вредоносных программ.</span><span class="sxs-lookup"><span data-stu-id="76588-105">Office 365 Advanced Threat Protection (ATP) is a feature of Exchange Online Protection (EOP) that helps keep malware out of your email.</span></span> <span data-ttu-id="76588-106">С помощью ATP вы создадите политики в центре администрирования Exchange или в центре безопасности &amp; , которые помогают пользователям получать доступ только к ссылкам или вложениям в сообщениях, которые определены как нежелательные.</span><span class="sxs-lookup"><span data-stu-id="76588-106">With ATP, you create policies in the Exchange admin center (EAC) or the Security &amp; Compliance center that help ensure your users access only links or attachments in emails that are identified as not malicious.</span></span> <span data-ttu-id="76588-107">Дополнительные сведения см. в разделе [Advanced threat protection for safe attachments and safe links](https://technet.microsoft.com/library/mt148491%28v=exchg.150%29.aspx).</span><span class="sxs-lookup"><span data-stu-id="76588-107">For more information, see [Advanced threat protection for safe attachments and safe links](https://technet.microsoft.com/library/mt148491%28v=exchg.150%29.aspx).</span></span>
  
<span data-ttu-id="76588-108">С помощью инструкций в этой статье вы можете настроить и протестировать ATP в пробной подписке на Office 365. </span><span class="sxs-lookup"><span data-stu-id="76588-108">With the instructions in this article, you configure and test ATP in your Office 365 trial subscription.</span></span>
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a><span data-ttu-id="76588-109">Этап 1. Создание среды разработки и тестирования Office 365 — упрощенной или для имитированных предприятий</span><span class="sxs-lookup"><span data-stu-id="76588-109">Phase 1: Build out your lightweight or simulated enterprise Office 365 dev/test environment</span></span>

<span data-ttu-id="76588-110">Если вы просто хотите протестировать ATP в упрощенном виде с минимальными требованиями, следуйте инструкциям в статье этапы 2 и 3 из [среды разработки и тестирования Office 365](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="76588-110">If you just want to test ATP in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="76588-111">Если вы хотите протестировать ATP на имитации предприятия, следуйте инструкциям в статье [DirSync для среды разработки и тестирования Office 365](dirsync-for-your-office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="76588-111">If you want to test ATP in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="76588-p102">Чтобы можно было протестировать ATP, не требуется среда разработки и тестирования для имитированного предприятия, предусматривающая подключение имитированной интрасети к Интернету и синхронизацию каталогов для леса Windows Server AD. Она указана здесь лишь для того, чтобы вы могли протестировать ATP и поэкспериментировать с этим компонентом в типичной для организаций среде.</span><span class="sxs-lookup"><span data-stu-id="76588-p102">Testing ATP does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest. It is provided here as an option so that you can test ATP and experiment with it in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-demonstrate-the-default-email-delivery-behavior-of-office-365"></a><span data-ttu-id="76588-114">Этап 2: Демонстрация способа доставки электронной почты по умолчанию в Office 365</span><span class="sxs-lookup"><span data-stu-id="76588-114">Phase 2: Demonstrate the default email delivery behavior of Office 365</span></span>

<span data-ttu-id="76588-115">Этот этап посвящен демонстрации того, что до настройки политик ATP потенциально вредоносные электронные сообщения доставляются в почтовые ящики Office 365 без экранирования и устранения рисков.</span><span class="sxs-lookup"><span data-stu-id="76588-115">In this phase, you demonstrate that before configuring ATP policies, potentially malicious email gets delivered to Office 365 mailboxes without screening or mitigation.</span></span>
  
1. <span data-ttu-id="76588-116">Откройте Internet Explorer и войдите в учетную запись Outlook, созданную на этапе 2 [среды разработки и тестирования Office 365](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="76588-116">Open Internet Explorer and sign in to the Outlook account you created in Phase 2 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
    
  - <span data-ttu-id="76588-117">Если вы используете упрощенную среду разработки и тестирования Office 365, запустите частный сеанс Internet Explorer и войдите с локального компьютера.</span><span class="sxs-lookup"><span data-stu-id="76588-117">If you are using the lightweight Office 365 dev/test environment, open a private session of Internet Explorer and sign in from your local computer.</span></span>
    
  - <span data-ttu-id="76588-118">Если вы используете среду разработки и тестирования Office 365 для имитированного предприятия, войдите на [портал Azure](https://portal.azure.com), чтобы подключиться к виртуальной машине CLIENT1, а затем выполните вход с этой виртуальной машины.</span><span class="sxs-lookup"><span data-stu-id="76588-118">If you are using the simulated enterprise Office 365 dev/test environment, use the [Azure portal](https://portal.azure.com) to connect to the CLIENT1 virtual machine, and then sign in from CLIENT1.</span></span>
    
2. <span data-ttu-id="76588-119">Запустите "Блокнот" и введите какой-нибудь текст.</span><span class="sxs-lookup"><span data-stu-id="76588-119">Run Notepad and enter some text.</span></span>
    
3. <span data-ttu-id="76588-120">Сохраните файл в папку "Документы" под именем **getKeys.js**.</span><span class="sxs-lookup"><span data-stu-id="76588-120">Save the file to the Documents folder as **getKeys.js**.</span></span>
    
4. <span data-ttu-id="76588-121">На вкладке "Почта Outlook" в Internet Explorer нажмите кнопку **Создать**.</span><span class="sxs-lookup"><span data-stu-id="76588-121">From the Outlook Mail tab of Internet Explorer, click **New**.</span></span>
    
5. <span data-ttu-id="76588-122">В поле **Кому** введите электронный адрес глобального администратора для пробной подписки на Office 365.</span><span class="sxs-lookup"><span data-stu-id="76588-122">In **To**, type the email address of the Office 365 global administrator name of your trial subscription.</span></span>
    
6. <span data-ttu-id="76588-123">В поле темы введите **Ваши новые ключи**.</span><span class="sxs-lookup"><span data-stu-id="76588-123">For the subject, type **Your new keys**.</span></span>
    
7. <span data-ttu-id="76588-124">В поле текста введите **Вот файл**.</span><span class="sxs-lookup"><span data-stu-id="76588-124">In the body, type **Here is the file**.</span></span>
    
8. <span data-ttu-id="76588-125">Нажмите кнопку **Вложить**, дважды щелкните **getKeys.js** в папке "Документы" и выберите элемент **Вложить как копию**, после чего нажмите кнопку **Отправить**.</span><span class="sxs-lookup"><span data-stu-id="76588-125">Click **Attach**, double-click **getKeys.js** in the Documents folder, click **Attach as a copy**, and then click **Send**.</span></span>
    
9. <span data-ttu-id="76588-126">Нажмите кнопку **Создать**.</span><span class="sxs-lookup"><span data-stu-id="76588-126">Click **New**.</span></span>
    
10. <span data-ttu-id="76588-127">В поле **Кому** введите электронный адрес глобального администратора для пробной подписки на Office 365.</span><span class="sxs-lookup"><span data-stu-id="76588-127">In **To**, type the email address of the Office 365 global administrator name of your trial subscription.</span></span>
    
11. <span data-ttu-id="76588-128">В поле темы введите **Новый туристический веб-сайт**.</span><span class="sxs-lookup"><span data-stu-id="76588-128">For the subject, type **New travel web site**.</span></span>
    
12. <span data-ttu-id="76588-129">В поле текста введите **Кто-то переслал мне этот сайт**.</span><span class="sxs-lookup"><span data-stu-id="76588-129">In the body, type **Someone forwarded me this site**.</span></span>
    
13. <span data-ttu-id="76588-130">В поле текста выделите текст **этот сайт** и щелкните значок гиперссылки на панели инструментов.</span><span class="sxs-lookup"><span data-stu-id="76588-130">In the body, select the **this site** text and click the hyperlink icon in the toolbar.</span></span>
    
14. <span data-ttu-id="76588-131">В окне **URL-адрес**введите **http://www.spamlink.contoso.com/**, а затем нажмите кнопку **ОК**, а затем нажмите кнопку **Отправить**.</span><span class="sxs-lookup"><span data-stu-id="76588-131">In **URL**, type **http://www.spamlink.contoso.com/**, click **OK**, and then click **Send**.</span></span>
    
15. <span data-ttu-id="76588-132">Откройте отдельный экземпляр Internet Explorer в режиме закрытого просмотра, перейдите в центр администрирования Microsoft 365 ([https://admin.microsoft.com](https://admin.microsoft.com)) и войдите в пробную подписку на Office 365 с помощью учетной записи глобального администратора.</span><span class="sxs-lookup"><span data-stu-id="76588-132">Open a separate instance of Internet Explorer in private browsing mode, go to the Microsoft 365 admin center ([https://admin.microsoft.com](https://admin.microsoft.com)), and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
16. <span data-ttu-id="76588-133">На главной странице портала нажмите плитку приложений и выберите элемент **Почта**.</span><span class="sxs-lookup"><span data-stu-id="76588-133">From the main portal page, click the apps tile, and then click **Mail**.</span></span>
    
17. <span data-ttu-id="76588-134">В папке "Входящие" щелкните сообщение с темой **Ваши новые ключи**.</span><span class="sxs-lookup"><span data-stu-id="76588-134">In the Inbox, click the message with the subject **Your new keys**.</span></span>
    
18. <span data-ttu-id="76588-135">В папке "неЖелательная почта" щелкните сообщение с **веб-сайтом "Создание**темы".</span><span class="sxs-lookup"><span data-stu-id="76588-135">In the Junk Mail folder, click the message with the subject **New travel web site**.</span></span> <span data-ttu-id="76588-136">В сообщении щелкните **эту ссылку сайт** .</span><span class="sxs-lookup"><span data-stu-id="76588-136">Within the message, click the **this site** link.</span></span> <span data-ttu-id="76588-137">Вы должны увидеть "ой!</span><span class="sxs-lookup"><span data-stu-id="76588-137">You should see a "Oops!</span></span> <span data-ttu-id="76588-138">Internet Explorer не удалось найти spamlink.contoso.com ".</span><span class="sxs-lookup"><span data-stu-id="76588-138">Internet Explorer could not find spamlink.contoso.com."</span></span> <span data-ttu-id="76588-139">(Почти готово!).</span><span class="sxs-lookup"><span data-stu-id="76588-139">page.</span></span> <span data-ttu-id="76588-140">Это правильный результат, так как в этом расположении нет веб-страницы.</span><span class="sxs-lookup"><span data-stu-id="76588-140">This is the correct result because there is no web page at that location.</span></span>
    
<span data-ttu-id="76588-p104">Обратите внимание на то, что оба этих потенциально вредоносных электронных сообщения были успешно доставлены. Электронное сообщение с темой **Ваши новые ключи** могло содержать вредоносные программы, а сообщение с темой **Новый туристический веб-сайт** — потенциально вредоносную ссылку, по которой пользователь успешно перешел.</span><span class="sxs-lookup"><span data-stu-id="76588-p104">Notice that both of these potentially malicious emails were delivered successfully. The **Your new keys** email could contain undetected malware and the user was allowed to click the potentially malicious link in the **New travel web site** email.</span></span>
  
## <a name="phase-3-configure-safe-attachment-and-safe-links-policies-for-atp"></a><span data-ttu-id="76588-143">Этап 3. Настройка политик безопасных вложений и безопасных ссылок для ATP</span><span class="sxs-lookup"><span data-stu-id="76588-143">Phase 3: Configure safe attachment and safe links policies for ATP</span></span>

<span data-ttu-id="76588-144">На этом этапе нужно создать и настроить политику безопасных вложений, предотвращающую доставку писем с потенциально вредоносными вложениями, и политику безопасных ссылок, не допускающую перехода пользователей по потенциально небезопасным URL-адресам.</span><span class="sxs-lookup"><span data-stu-id="76588-144">In this phase, you create and configure a safe attachment policy to prevent email with potentially malicious attachments from being delivered and a safe links policy to keep users from traveling to potentially unsafe URLs.</span></span>
  
1. <span data-ttu-id="76588-145">На вкладке **домашнЯя страница Microsoft Office** в Internet Explorer щелкните плитку **Администратор** .</span><span class="sxs-lookup"><span data-stu-id="76588-145">On the **Microsoft Office Home** tab of Internet Explorer, click the **Admin** tile.</span></span>
    
2. <span data-ttu-id="76588-146">В области навигации слева откройте меню **Центры администрирования**, а затем выберите пункт **Exchange**.</span><span class="sxs-lookup"><span data-stu-id="76588-146">In the left navigation, click **Admin centers**, and then **Exchange**.</span></span>
    
3. <span data-ttu-id="76588-147">В Центре администрирования Exchange выберите пункт **Дополнительные риски** в области навигации слева.</span><span class="sxs-lookup"><span data-stu-id="76588-147">In the left navigation of the Exchange admin center tab, click **advanced threats**.</span></span>
    
4. <span data-ttu-id="76588-148">Откройте вкладку **Безопасные вложения** и щелкните знак "плюс".</span><span class="sxs-lookup"><span data-stu-id="76588-148">Click the **safe attachments** tab, and then click the plus sign.</span></span>
    
5. <span data-ttu-id="76588-149">В окне **Создание политики безопасных вложений** в поле **имя**введите **Политика безопасных вложений**.</span><span class="sxs-lookup"><span data-stu-id="76588-149">In the **new safe attachments policy** window, in **Name**, type **Safe Attachment Policy - Block**.</span></span>
    
6. <span data-ttu-id="76588-150">В случае **безопасных вложений неизвестный отклик**нажмите кнопку **блокировать**.</span><span class="sxs-lookup"><span data-stu-id="76588-150">For **Safe attachments unknown malware response**, click **Block**.</span></span>
    
7. <span data-ttu-id="76588-151">Параметру **Перенаправление вложения при его обнаружении** присвойте значение **Включить перенаправление** и введите электронный адрес для учетной записи глобального администратора Office 365.</span><span class="sxs-lookup"><span data-stu-id="76588-151">For **Redirect attachment on detection**, click **Enable redirect** and type the email address of your Office 365 global administrator account.</span></span>
    
8. <span data-ttu-id="76588-152">Щелкните стрелку вниз возле элемента **Применяется к** и выберите пункт **Домен получателя**.</span><span class="sxs-lookup"><span data-stu-id="76588-152">For **Applied to**, click the down arrow, and then click **The recipient domain is**.</span></span> <span data-ttu-id="76588-153">В окне щелкните название организации (например, contoso.onmicrosoft.com), а затем нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="76588-153">In the window, click your organization name (such as contoso.onmicrosoft.com), and then click **OK**.</span></span>
    
9. <span data-ttu-id="76588-154">Нажмите кнопку \*\*Сохранить \*\*.</span><span class="sxs-lookup"><span data-stu-id="76588-154">Click **Save**.</span></span> <span data-ttu-id="76588-155">После обновления вы увидите новый и включенный **блок политики безопасных вложений**.</span><span class="sxs-lookup"><span data-stu-id="76588-155">After the update, you should see the new and enabled **Safe Attachment Policy - Block**.</span></span>
    
10. <span data-ttu-id="76588-156">Откройте вкладку **Безопасные ссылки** и щелкните знак "плюс".</span><span class="sxs-lookup"><span data-stu-id="76588-156">Click the **safe links** tab, and then click the plus sign.</span></span>
    
11. <span data-ttu-id="76588-157">В поле **Имя** окна **Создание политики безопасных ссылок** введите **Политика безопасных ссылок**.</span><span class="sxs-lookup"><span data-stu-id="76588-157">In the **new safe links policy** window, in **Name**, type **Safe Link Policy**.</span></span>
    
12. <span data-ttu-id="76588-158">Нажмите **Вкл.** для параметра **Выберите действие, которое необходимо применять к неизвестным потенциально вредоносным URL-адресам, обнаруживаемым в сообщениях**, а затем выберите **Не разрешать пользователям переходить по исходному URL-адресу**.</span><span class="sxs-lookup"><span data-stu-id="76588-158">For **Select the action for unknown potentially malicious URLs in messages**, click **On**, and then select **Do not allow users to click through to original URL**.</span></span>
    
13. <span data-ttu-id="76588-159">Щелкните стрелку вниз возле элемента **Применяется к** и выберите пункт **Домен получателя**.</span><span class="sxs-lookup"><span data-stu-id="76588-159">For **Applied to**, click the down arrow, and then click **The recipient domain is**.</span></span> <span data-ttu-id="76588-160">В окне щелкните название организации (например, contoso.onmicrosoft.com), а затем нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="76588-160">In the window, click your organization name (such as contoso.onmicrosoft.com), and then click **OK**.</span></span>
    
14. <span data-ttu-id="76588-p108">Нажмите кнопку **Сохранить**. Вы увидите новую включенную политику **Политика безопасных ссылок**.</span><span class="sxs-lookup"><span data-stu-id="76588-p108">Click **Save**. You should see the new and enabled **Safe Link Policy**.</span></span>
    
## <a name="phase-4-show-atp-in-action"></a><span data-ttu-id="76588-163">Этап 4. Демонстрация ATP в действии</span><span class="sxs-lookup"><span data-stu-id="76588-163">Phase 4: Show ATP in action</span></span>

<span data-ttu-id="76588-164">Этот этап посвящен демонстрации того, как ATP обращается с потенциально вредоносными электронными сообщениями.</span><span class="sxs-lookup"><span data-stu-id="76588-164">In this phase, you demonstrate how ATP deals with potentially malicious email.</span></span>
  
1. <span data-ttu-id="76588-165">В экземпляре Internet Explorer, который использовался для отправки электронного сообщения на этапе 2, на панели навигации слева щелкните элемент **Отправленные.**</span><span class="sxs-lookup"><span data-stu-id="76588-165">From the instance of Internet Explorer that you used to send the email in Phase 2, in the left navigation, click **Sent Items.**</span></span>
    
2. <span data-ttu-id="76588-166">Щелкните сообщение электронной почты с названием **новые ключи**, щелкните значок со стрелкой вниз, а затем \*\*\*\* выберите переслать.</span><span class="sxs-lookup"><span data-stu-id="76588-166">Click the email titled **Your new keys**, click the down arrow icon, and then click **Forward**.</span></span>
    
3. <span data-ttu-id="76588-167">В поле **Кому** нового сообщения введите электронный адрес глобального администратора для пробной подписки на Office 365 и нажмите кнопку **Отправить**.</span><span class="sxs-lookup"><span data-stu-id="76588-167">For the new message, in **To**, type the email address of the Office 365 global administrator name of your trial subscription, and then click **Send**.</span></span>
    
4. <span data-ttu-id="76588-168">Щелкните сообщение с названием **создать веб-сайт для командировок**, щелкните значок стрелка вниз, выберите пункт **ответить всем**, а затем нажмите кнопку **Отправить**.</span><span class="sxs-lookup"><span data-stu-id="76588-168">Click the email titled **New travel web site**, click the down arrow icon, click **Reply all**, and then click **Send**.</span></span>
    
5. <span data-ttu-id="76588-p109">Откройте вкладку Центра администрирования Exchange в экземпляре Internet Explorer, который вы использовали для настройки политик ATP на этапе 3. В этой вкладке нажмите плитку приложений и выберите элемент **Почта**. В папке "Входящие" вы увидите два новых электронных сообщения:</span><span class="sxs-lookup"><span data-stu-id="76588-p109">From the instance of Internet Explorer that you used to configure ATP policies in Phase 3, click the Exchange admin center tab, click the apps tile, and then click **Mail**. You should see two new email messages in the Inbox:</span></span>
    
  - <span data-ttu-id="76588-171">с темой **Fw: Ваши новые ключи**;</span><span class="sxs-lookup"><span data-stu-id="76588-171">One titled **Fw: Your new keys**</span></span>
    
  - <span data-ttu-id="76588-172">с темой **Fw: Новый туристический веб-сайт**.</span><span class="sxs-lookup"><span data-stu-id="76588-172">One titled **Fw: New travel web site**</span></span>
    
6. <span data-ttu-id="76588-173">Откройте сообщение электронной почты под названием **"FW: новый веб-сайт для командировок** " и щелкните ссылку на **этот сайт** .</span><span class="sxs-lookup"><span data-stu-id="76588-173">Open the email message titled **Fw: New travel web site** and click the **this site** link.</span></span> <span data-ttu-id="76588-174">Вы должны увидеть "Этот веб-сайт классифицирован как вредоносный".</span><span class="sxs-lookup"><span data-stu-id="76588-174">You should see a "This website has been classified as malicious."</span></span> <span data-ttu-id="76588-175">(Почти готово!).</span><span class="sxs-lookup"><span data-stu-id="76588-175">page.</span></span> <span data-ttu-id="76588-176">Это показывает, что ATP препятствует доступу к потенциально вредоносному веб-сайту.</span><span class="sxs-lookup"><span data-stu-id="76588-176">This demonstrates that ATP is preventing you from accessing the potentially malicious web site.</span></span>
    
7. <span data-ttu-id="76588-177">В Internet Explorer откройте вкладку Центра администрирования Exchange и в области навигации слева выберите пункт **Поток обработки почты**.</span><span class="sxs-lookup"><span data-stu-id="76588-177">In the Exchange admin center tab of Internet Explorer, in the left navigation, click **mail flow**.</span></span>
    
8. <span data-ttu-id="76588-178">Откройте вкладку **Трассировка сообщений** и нажмите кнопку **Поиск**.</span><span class="sxs-lookup"><span data-stu-id="76588-178">Click the **message trace** tab, and then click **search**.</span></span>
    
9. <span data-ttu-id="76588-179">Дважды щелкните сообщение с темой **Ваши новые ключи** в окне **Результаты трассировки сообщений**.</span><span class="sxs-lookup"><span data-stu-id="76588-179">In the **Message Trace Results** window, double-click the message with the subject **Your new keys**.</span></span> <span data-ttu-id="76588-180">Сообщение успешно доставлено в папку "Входящие".</span><span class="sxs-lookup"><span data-stu-id="76588-180">This message was successfully delivered to the Inbox.</span></span> <span data-ttu-id="76588-181">Закройте это окно.</span><span class="sxs-lookup"><span data-stu-id="76588-181">Close this window.</span></span>
    
10. <span data-ttu-id="76588-182">Дважды щелкните сообщение с темой **Новый туристический веб-сайт**.</span><span class="sxs-lookup"><span data-stu-id="76588-182">Double-click the message with the subject **New travel web site**.</span></span> <span data-ttu-id="76588-183">Сообщение успешно доставлено в папку "Входящие".</span><span class="sxs-lookup"><span data-stu-id="76588-183">This message was successfully delivered to the Inbox.</span></span> <span data-ttu-id="76588-184">Закройте это окно.</span><span class="sxs-lookup"><span data-stu-id="76588-184">Close this window.</span></span>
    
11. <span data-ttu-id="76588-185">Дважды щелкните сообщение с темой **Fw: Ваши новые ключи**.</span><span class="sxs-lookup"><span data-stu-id="76588-185">Double-click the message with the subject **Fw: Your new keys**.</span></span> <span data-ttu-id="76588-186">Обратите внимание на то, как это сообщение было обработано ATP и затем доставлено в папку "Входящие".</span><span class="sxs-lookup"><span data-stu-id="76588-186">Note how this message was processed by ATP and then delivered to the Inbox.</span></span> <span data-ttu-id="76588-187">Закройте это окно.</span><span class="sxs-lookup"><span data-stu-id="76588-187">Close this window.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="76588-188">Политика безопасных вложений должна начинать сканирование вложений для вредоносного кода.</span><span class="sxs-lookup"><span data-stu-id="76588-188">The purpose of the safe attachments policy was to begin scanning attachments for malicious code.</span></span> <span data-ttu-id="76588-189">Вложение ключей. js было разрешено, так как оно не было определено как вредоносное.</span><span class="sxs-lookup"><span data-stu-id="76588-189">The getKeys.js attachment was allowed because it was not determined to be malicious.</span></span> <span data-ttu-id="76588-190">На этом этапе показано, что ATP выполнил сканирование вложения.</span><span class="sxs-lookup"><span data-stu-id="76588-190">This step shows that ATP did perform a scan of the attachment.</span></span> 
  
12. <span data-ttu-id="76588-191">Дважды щелкните сообщение с темой **Fw: Новый туристический веб-сайт**.</span><span class="sxs-lookup"><span data-stu-id="76588-191">Double-click the message with the subject **Fw: New travel web site**.</span></span> <span data-ttu-id="76588-192">Обратите внимание, что это сообщение успешно доставлено в папку "Входящие".</span><span class="sxs-lookup"><span data-stu-id="76588-192">Note that this message was successfully delivered to the Inbox.</span></span>
    
<span data-ttu-id="76588-193">Теперь с помощью этой среды можно создавать новые политики и экспериментировать с ATP.</span><span class="sxs-lookup"><span data-stu-id="76588-193">You can now use this environment to create new policies and experiment with ATP.</span></span>
  
> [!TIP]
> <span data-ttu-id="76588-194">Щелкните [здесь](http://aka.ms/catlgstack), чтобы просмотреть схему всех статей, относящихся к руководствам по лаборатории тестирования в One Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="76588-194">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="76588-195">См. также</span><span class="sxs-lookup"><span data-stu-id="76588-195">See Also</span></span>

[<span data-ttu-id="76588-196">Руководства по лабораториям тестирования (TLG) для принятия облачных решений</span><span class="sxs-lookup"><span data-stu-id="76588-196">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="76588-197">Базовая конфигурация среды разработки и тестирования</span><span class="sxs-lookup"><span data-stu-id="76588-197">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="76588-198">Среда разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="76588-198">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="76588-199">DirSync для среды разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="76588-199">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="76588-200">Cloud App Security для среды разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="76588-200">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="76588-201">Освоение облака и гибридные решения</span><span class="sxs-lookup"><span data-stu-id="76588-201">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md) 

[<span data-ttu-id="76588-202">Дополнительная защита от угроз для безопасных вложений и ссылок</span><span class="sxs-lookup"><span data-stu-id="76588-202">Advanced threat protection for safe attachments and safe links</span></span>](https://support.office.com/article/Office-365-Advanced-Threat-Protection-E100FE7C-F2A1-4B7D-9E08-622330B83653)


