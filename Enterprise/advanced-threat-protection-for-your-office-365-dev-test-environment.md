---
title: "Advanced Threat Protection в среде разработки и тестирования Office 365"
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
ms.assetid: 51019757-20ac-498c-b51e-cae6d41a8c08
description: "Сводка: Настройка и демонстрация защиту от угроз для Office 365 расширенного в среде разработки и тестирования Office 365."
ms.openlocfilehash: 6266960287d06ffafdf7ed1f6690396fd4cda9d5
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2018
---
# <a name="advanced-threat-protection-for-your-office-365-devtest-environment"></a><span data-ttu-id="98282-103">Advanced Threat Protection в среде разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="98282-103">Advanced Threat Protection for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="98282-104">**Сводка:** Настройка и демонстрация защиту от угроз для Office 365 расширенного в среде разработки и тестирования Office 365.</span><span class="sxs-lookup"><span data-stu-id="98282-104">**Summary:** Configure and demonstrate Office 365 Advanced Threat Protection in your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="98282-p101">Office 365 расширенного угроз защиты анализа — это компонент из Exchange Online Protection (EOP), которая позволяет сохранить вредоносных программ из него электронной почты. С помощью анализа, Создание политик в центре администрирования Exchange (EAC) или безопасность &amp; центре соответствия требованиям, помочь обеспечить пользователям доступ к только ссылки или вложения в сообщениях, которые считаются не вредоносных. Для получения дополнительных сведений см [расширенной защитой для вложений надежных и безопасных ссылок](https://technet.microsoft.com/library/mt148491%28v=exchg.150%29.aspx).</span><span class="sxs-lookup"><span data-stu-id="98282-p101">Office 365 Advanced Threat Protection (ATP) is a feature of Exchange Online Protection (EOP) that helps keep malware out of your email. With ATP, you create policies in the Exchange admin center (EAC) or the Security &amp; Compliance center that help ensure your users access only links or attachments in emails that are identified as not malicious. For more information, see [Advanced threat protection for safe attachments and safe links](https://technet.microsoft.com/library/mt148491%28v=exchg.150%29.aspx).</span></span>
  
<span data-ttu-id="98282-108">С помощью инструкций в этой статье вы можете настроить и протестировать ATP в пробной подписке на Office 365. </span><span class="sxs-lookup"><span data-stu-id="98282-108">With the instructions in this article, you configure and test ATP in your Office 365 trial subscription.</span></span>
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a><span data-ttu-id="98282-109">Этап 1. Создание среды разработки и тестирования Office 365 — упрощенной или для имитированных предприятий</span><span class="sxs-lookup"><span data-stu-id="98282-109">Phase 1: Build out your lightweight or simulated enterprise Office 365 dev/test environment</span></span>

<span data-ttu-id="98282-110">Если необходимо проверить ATP в облегченный путь с минимальным требованиям, следуйте инструкциям в этапы 2 и 3 [Office 365 dev/тестовой среды](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="98282-110">If you just want to test ATP in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="98282-111">Если вы хотите проверить ATP в имитации enterprise, следуйте инструкциям в [DirSync для вашей среды разработки или тестирования Office 365](dirsync-for-your-office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="98282-111">If you want to test ATP in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="98282-p102">Чтобы можно было протестировать ATP, не требуется среда разработки и тестирования для имитированного предприятия, предусматривающая подключение имитированной интрасети к Интернету и синхронизацию каталогов для леса Windows Server AD. Она указана здесь лишь для того, чтобы вы могли протестировать ATP и поэкспериментировать с этим компонентом в типичной для организаций среде.</span><span class="sxs-lookup"><span data-stu-id="98282-p102">Testing ATP does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest. It is provided here as an option so that you can test ATP and experiment with it in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-demonstrate-the-default-email-delivery-behavior-of-office-365"></a><span data-ttu-id="98282-114">Этап 2: Демонстрация поведения доставки электронной почты по умолчанию для Office 365</span><span class="sxs-lookup"><span data-stu-id="98282-114">Phase 2: Demonstrate the default email delivery behavior of Office 365</span></span>

<span data-ttu-id="98282-115">Этот этап посвящен демонстрации того, что до настройки политик ATP потенциально вредоносные электронные сообщения доставляются в почтовые ящики Office 365 без экранирования и устранения рисков.</span><span class="sxs-lookup"><span data-stu-id="98282-115">In this phase, you demonstrate that before configuring ATP policies, potentially malicious email gets delivered to Office 365 mailboxes without screening or mitigation.</span></span>
  
1. <span data-ttu-id="98282-116">Откройте Internet Explorer и войдите в учетную запись Outlook, созданной на этапе 2 [Office 365 dev/тестовой среды](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="98282-116">Open Internet Explorer and sign in to the Outlook account you created in Phase 2 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
    
  - <span data-ttu-id="98282-117">Если вы используете упрощенную среду разработки и тестирования Office 365, запустите частный сеанс Internet Explorer и войдите с локального компьютера.</span><span class="sxs-lookup"><span data-stu-id="98282-117">If you are using the lightweight Office 365 dev/test environment, open a private session of Internet Explorer and sign in from your local computer.</span></span>
    
  - <span data-ttu-id="98282-118">Если вы используете среду разработки и тестирования Office 365 для имитированного предприятия, войдите на [портал Azure](https://portal.azure.com), чтобы подключиться к виртуальной машине CLIENT1, а затем выполните вход с этой виртуальной машины.</span><span class="sxs-lookup"><span data-stu-id="98282-118">If you are using the simulated enterprise Office 365 dev/test environment, use the [Azure portal](https://portal.azure.com) to connect to the CLIENT1 virtual machine, and then sign in from CLIENT1.</span></span>
    
2. <span data-ttu-id="98282-119">Запустите "Блокнот" и введите какой-нибудь текст.</span><span class="sxs-lookup"><span data-stu-id="98282-119">Run Notepad and enter some text.</span></span>
    
3. <span data-ttu-id="98282-120">Сохраните файл в папку «документы» как **getKeys.js**.</span><span class="sxs-lookup"><span data-stu-id="98282-120">Save the file to the Documents folder as **getKeys.js**.</span></span>
    
4. <span data-ttu-id="98282-121">В Internet Explorer откройте вкладку почты Outlook и нажмите кнопку **Создать**.</span><span class="sxs-lookup"><span data-stu-id="98282-121">From the Outlook Mail tab of Internet Explorer, click **New**.</span></span>
    
5. <span data-ttu-id="98282-122">В **в**введите адрес электронной почты от имени глобального администратора Office 365 пробной подписки.</span><span class="sxs-lookup"><span data-stu-id="98282-122">In **To**, type the email address of the Office 365 global administrator name of your trial subscription.</span></span>
    
6. <span data-ttu-id="98282-123">Для темы введите **новый ключ**.</span><span class="sxs-lookup"><span data-stu-id="98282-123">For the subject, type **Your new keys**.</span></span>
    
7. <span data-ttu-id="98282-124">В тексте запроса введите **здесь — это файл**.</span><span class="sxs-lookup"><span data-stu-id="98282-124">In the body, type **Here is the file**.</span></span>
    
8. <span data-ttu-id="98282-125">Нажмите кнопку **присоединить**, дважды щелкните значок **getKeys.js** в папку «документы», нажмите кнопку **Присоединить как копии**и нажмите кнопку **Отправить**.</span><span class="sxs-lookup"><span data-stu-id="98282-125">Click **Attach**, double-click **getKeys.js** in the Documents folder, click **Attach as a copy**, and then click **Send**.</span></span>
    
9. <span data-ttu-id="98282-126">Нажмите кнопку **Создать**.</span><span class="sxs-lookup"><span data-stu-id="98282-126">Click **New**.</span></span>
    
10. <span data-ttu-id="98282-127">В **в**введите адрес электронной почты от имени глобального администратора Office 365 пробной подписки.</span><span class="sxs-lookup"><span data-stu-id="98282-127">In **To**, type the email address of the Office 365 global administrator name of your trial subscription.</span></span>
    
11. <span data-ttu-id="98282-128">Для темы введите **New путешествий веб-сайта**.</span><span class="sxs-lookup"><span data-stu-id="98282-128">For the subject, type **New travel web site**.</span></span>
    
12. <span data-ttu-id="98282-129">В тексте запроса введите **кто-то пересылку мне этого сайта**.</span><span class="sxs-lookup"><span data-stu-id="98282-129">In the body, type **Someone forwarded me this site**.</span></span>
    
13. <span data-ttu-id="98282-130">В тексте запроса выберите текст **этого сайта** и щелкните значок гиперссылки на панели инструментов.</span><span class="sxs-lookup"><span data-stu-id="98282-130">In the body, select the **this site** text and click the hyperlink icon in the toolbar.</span></span>
    
14. <span data-ttu-id="98282-131">В **URL-адрес**введите **http://www.spamlink.contoso.com/**и нажмите **кнопку ОК,**нажмите кнопку **Отправить**.</span><span class="sxs-lookup"><span data-stu-id="98282-131">In **URL**, type **http://www.spamlink.contoso.com/**, click **OK**, and then click **Send**.</span></span>
    
15. <span data-ttu-id="98282-132">Открыть отдельный экземпляр Internet Explorer в частный режим просмотра, перейдите к порталу Office 365 ([https://portal.office.com](https://portal.office.com)) и войдите в пробной подписки Office 365 с учетной записью глобального администратора.</span><span class="sxs-lookup"><span data-stu-id="98282-132">Open a separate instance of Internet Explorer in private browsing mode, go to the Office 365 portal ([https://portal.office.com](https://portal.office.com)), and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
16. <span data-ttu-id="98282-133">На основной странице портала щелкните плитку приложения и нажмите кнопку **почты**.</span><span class="sxs-lookup"><span data-stu-id="98282-133">From the main portal page, click the apps tile, and then click **Mail**.</span></span>
    
17. <span data-ttu-id="98282-134">В папке "Входящие" щелкните сообщение с темой **новые ключи**.</span><span class="sxs-lookup"><span data-stu-id="98282-134">In the Inbox, click the message with the subject **Your new keys**.</span></span>
    
18. <span data-ttu-id="98282-p103">В папку нежелательной почты щелкните сообщение с темой **New путешествий веб-сайта**. В сообщении щелкните ссылку **этого сайта** . Вы должны увидеть «Oops! Страница Internet Explorer не удается найти spamlink.contoso.com.». Это правильный результат, так как в этом расположении нет веб-страницы.</span><span class="sxs-lookup"><span data-stu-id="98282-p103">In the Junk Mail folder, click the message with the subject **New travel web site**. Within the message, click the **this site** link. You should see a "Oops! Internet Explorer could not find spamlink.contoso.com." page. This is the correct result because there is no web page at that location.</span></span>
    
<span data-ttu-id="98282-p104">Обратите внимание на то, что оба эти потенциально вредоносных сообщения были успешно доставлено. **Новые ключи** сообщение электронной почты может содержать невыявленное вредоносных программ и разрешено пользователю щелкните потенциально вредоносных ссылку в сообщение электронной почты **New путешествий веб-сайта** .</span><span class="sxs-lookup"><span data-stu-id="98282-p104">Notice that both of these potentially malicious emails were delivered successfully. The **Your new keys** email could contain undetected malware and the user was allowed to click the potentially malicious link in the **New travel web site** email.</span></span>
  
## <a name="phase-3-configure-safe-attachment-and-safe-links-policies-for-atp"></a><span data-ttu-id="98282-143">Этап 3. Настройка политик безопасных вложений и безопасных ссылок для ATP</span><span class="sxs-lookup"><span data-stu-id="98282-143">Phase 3: Configure safe attachment and safe links policies for ATP</span></span>

<span data-ttu-id="98282-144">На этом этапе нужно создать и настроить политику безопасных вложений, предотвращающую доставку писем с потенциально вредоносными вложениями, и политику безопасных ссылок, не допускающую перехода пользователей по потенциально небезопасным URL-адресам.</span><span class="sxs-lookup"><span data-stu-id="98282-144">In this phase, you create and configure a safe attachment policy to prevent email with potentially malicious attachments from being delivered and a safe links policy to keep users from traveling to potentially unsafe URLs.</span></span>
  
1. <span data-ttu-id="98282-145">На вкладке **Microsoft Office для дома** Internet Explorer щелкните плитку **администрирования** .</span><span class="sxs-lookup"><span data-stu-id="98282-145">On the **Microsoft Office Home** tab of Internet Explorer, click the **Admin** tile.</span></span>
    
2. <span data-ttu-id="98282-146">На панели навигации слева щелкните **центра администрирования**, а затем **Exchange**.</span><span class="sxs-lookup"><span data-stu-id="98282-146">In the left navigation, click **Admin centers**, and then **Exchange**.</span></span>
    
3. <span data-ttu-id="98282-147">В левой панели навигации на вкладку Центр администрирования Exchange щелкните **Дополнительно угрозы**.</span><span class="sxs-lookup"><span data-stu-id="98282-147">In the left navigation of the Exchange admin center tab, click **advanced threats**.</span></span>
    
4. <span data-ttu-id="98282-148">Перейдите на вкладку **безопасные вложения** и затем щелкните значок "плюс".</span><span class="sxs-lookup"><span data-stu-id="98282-148">Click the **safe attachments** tab, and then click the plus sign.</span></span>
    
5. <span data-ttu-id="98282-149">В окне **Создание политики безопасные вложения** в поле **имя**введите **Безопасные вложения политики - блока**.</span><span class="sxs-lookup"><span data-stu-id="98282-149">In the **new safe attachments policy** window, in **Name**, type **Safe Attachment Policy - Block**.</span></span>
    
6. <span data-ttu-id="98282-150">Для **ответа безопасные вложения неизвестные вредоносные программы**выберите вариант **Блокировать**.</span><span class="sxs-lookup"><span data-stu-id="98282-150">For **Safe attachments unknown malware response**, click **Block**.</span></span>
    
7. <span data-ttu-id="98282-151">Для **перенаправления вложений на обнаружение**нажмите кнопку **Включить перенаправления** и введите адрес электронной почты учетной записи глобального администратора Office 365.</span><span class="sxs-lookup"><span data-stu-id="98282-151">For **Redirect attachment on detection**, click **Enable redirect** and type the email address of your Office 365 global administrator account.</span></span>
    
8. <span data-ttu-id="98282-p105">Для **применения к**щелкните стрелку вниз и нажмите кнопку **получателей домен — это**. В окне щелкните имя вашей организации (например, contoso.onmicrosoft.com) и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="98282-p105">For **Applied to**, click the down arrow, and then click **The recipient domain is**. In the window, click your organization name (such as contoso.onmicrosoft.com), and then click **OK**.</span></span>
    
9. <span data-ttu-id="98282-p106">Нажмите кнопку **Сохранить**. После обновления должны появиться новый и включить **Безопасные вложения политики - блока**.</span><span class="sxs-lookup"><span data-stu-id="98282-p106">Click **Save**. After the update, you should see the new and enabled **Safe Attachment Policy - Block**.</span></span>
    
10. <span data-ttu-id="98282-156">Перейдите на вкладку **безопасных ссылки** и нажмите кнопку «плюс».</span><span class="sxs-lookup"><span data-stu-id="98282-156">Click the **safe links** tab, and then click the plus sign.</span></span>
    
11. <span data-ttu-id="98282-157">В окне **новой политики безопасных ссылки** в поле **имя**введите **Безопасных ссылку политики**.</span><span class="sxs-lookup"><span data-stu-id="98282-157">In the **new safe links policy** window, in **Name**, type **Safe Link Policy**.</span></span>
    
12. <span data-ttu-id="98282-158">**Выберите действие для Неизвестный потенциально вредоносных URL-адресов в сообщениях**щелкните **на**и выберите **не разрешать пользователям перейдите по исходный URL-адрес**.</span><span class="sxs-lookup"><span data-stu-id="98282-158">For **Select the action for unknown potentially malicious URLs in messages**, click **On**, and then select **Do not allow users to click through to original URL**.</span></span>
    
13. <span data-ttu-id="98282-p107">Для **применения к**щелкните стрелку вниз и нажмите кнопку **получателей домен — это**. В окне щелкните имя вашей организации (например, contoso.onmicrosoft.com) и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="98282-p107">For **Applied to**, click the down arrow, and then click **The recipient domain is**. In the window, click your organization name (such as contoso.onmicrosoft.com), and then click **OK**.</span></span>
    
14. <span data-ttu-id="98282-p108">Нажмите кнопку **Сохранить**. Должны появиться новый и включить **Безопасный ссылку политики**.</span><span class="sxs-lookup"><span data-stu-id="98282-p108">Click **Save**. You should see the new and enabled **Safe Link Policy**.</span></span>
    
## <a name="phase-4-show-atp-in-action"></a><span data-ttu-id="98282-163">Этап 4. Демонстрация ATP в действии</span><span class="sxs-lookup"><span data-stu-id="98282-163">Phase 4: Show ATP in action</span></span>

<span data-ttu-id="98282-164">Этот этап посвящен демонстрации того, как ATP обращается с потенциально вредоносными электронными сообщениями.</span><span class="sxs-lookup"><span data-stu-id="98282-164">In this phase, you demonstrate how ATP deals with potentially malicious email.</span></span>
  
1. <span data-ttu-id="98282-165">Из экземпляра Internet Explorer, который использовался для отправки электронной почты на этапе 2, на панели навигации слева щелкните **Отправленные.**</span><span class="sxs-lookup"><span data-stu-id="98282-165">From the instance of Internet Explorer that you used to send the email in Phase 2, in the left navigation, click **Sent Items.**</span></span>
    
2. <span data-ttu-id="98282-166">Нажмите кнопку под названием **новые ключи**сообщение электронной почты, щелкните значок со стрелкой вниз и нажмите кнопку **переадресации**.</span><span class="sxs-lookup"><span data-stu-id="98282-166">Click the email titled **Your new keys**, click the down arrow icon, and then click **Forward**.</span></span>
    
3. <span data-ttu-id="98282-167">Для нового сообщения, **Чтобы**введите адрес электронной почты от имени глобального администратора Office 365 пробной подписки и нажмите кнопку **Отправить**.</span><span class="sxs-lookup"><span data-stu-id="98282-167">For the new message, in **To**, type the email address of the Office 365 global administrator name of your trial subscription, and then click **Send**.</span></span>
    
4. <span data-ttu-id="98282-168">Щелкните сообщение электронной почты, под названием **New путешествий веб-сайта**, щелкните значок со стрелкой вниз, нажмите кнопку **Ответить всем**и нажмите кнопку **Отправить**.</span><span class="sxs-lookup"><span data-stu-id="98282-168">Click the email titled **New travel web site**, click the down arrow icon, click **Reply all**, and then click **Send**.</span></span>
    
5. <span data-ttu-id="98282-p109">Из экземпляра Internet Explorer, который используется для настройки политик ATP на этапе 3 перейдите на вкладку Центр администрирования Exchange, щелкните плитку приложения и нажмите кнопку **почты**. Вы должны увидеть две новые сообщения электронной почты в папке "Входящие":</span><span class="sxs-lookup"><span data-stu-id="98282-p109">From the instance of Internet Explorer that you used to configure ATP policies in Phase 3, click the Exchange admin center tab, click the apps tile, and then click **Mail**. You should see two new email messages in the Inbox:</span></span>
    
  - <span data-ttu-id="98282-171">Один под названием **встроенного по: новые ключи**</span><span class="sxs-lookup"><span data-stu-id="98282-171">One titled **Fw: Your new keys**</span></span>
    
  - <span data-ttu-id="98282-172">Один под названием **встроенного по: новый веб-сайт travel**</span><span class="sxs-lookup"><span data-stu-id="98282-172">One titled **Fw: New travel web site**</span></span>
    
6. <span data-ttu-id="98282-p110">Откройте сообщение электронной почты, под названием **встроенного по: новый веб-сайт travel** и перейдите по ссылке **этого сайта** . Вы должны увидеть на странице «веб-сайту классифицируется как вредоносный.». Этот пример демонстрирует, что ATP предотвращения доступ к потенциально вредоносных веб-сайта.</span><span class="sxs-lookup"><span data-stu-id="98282-p110">Open the email message titled **Fw: New travel web site** and click the **this site** link. You should see a "This website has been classified as malicious." page. This demonstrates that ATP is preventing you from accessing the potentially malicious web site.</span></span>
    
7. <span data-ttu-id="98282-177">На вкладке Центр администрирования Exchange Internet Explorer, в левой панели навигации щелкните **поток обработки почты**.</span><span class="sxs-lookup"><span data-stu-id="98282-177">In the Exchange admin center tab of Internet Explorer, in the left navigation, click **mail flow**.</span></span>
    
8. <span data-ttu-id="98282-178">Перейдите на вкладку **Трассировка сообщений** и нажмите кнопку **Поиск**.</span><span class="sxs-lookup"><span data-stu-id="98282-178">Click the **message trace** tab, and then click **search**.</span></span>
    
9. <span data-ttu-id="98282-p111">В окне **Результатов трассировки** дважды щелкните сообщение с темой **новые ключи**. Это сообщение было успешно доставлено в папке "Входящие". Закройте это окно.</span><span class="sxs-lookup"><span data-stu-id="98282-p111">In the **Message Trace Results** window, double-click the message with the subject **Your new keys**. This message was successfully delivered to the Inbox. Close this window.</span></span>
    
10. <span data-ttu-id="98282-p112">Дважды щелкните сообщение с темой **New путешествий веб-сайта**. Это сообщение было успешно доставлено в папке "Входящие". Закройте это окно.</span><span class="sxs-lookup"><span data-stu-id="98282-p112">Double-click the message with the subject **New travel web site**. This message was successfully delivered to the Inbox. Close this window.</span></span>
    
11. <span data-ttu-id="98282-p113">Дважды щелкните сообщение с темой **встроенного по: новые ключи**. Обратите внимание на то, как обрабатываются анализа и затем доставлено в папке "Входящие" это сообщение. Закройте это окно.</span><span class="sxs-lookup"><span data-stu-id="98282-p113">Double-click the message with the subject **Fw: Your new keys**. Note how this message was processed by ATP and then delivered to the Inbox. Close this window.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="98282-p114">Назначение политики безопасные вложения, было начать сканирование вложений для вредоносного кода. Вложение getKeys.js было разрешено, так как он не оказался вредоносных. Это действие показывает, что ATP выполнить сканирование вложения.</span><span class="sxs-lookup"><span data-stu-id="98282-p114">The purpose of the safe attachments policy was to begin scanning attachments for malicious code. The getKeys.js attachment was allowed because it was not determined to be malicious. This step shows that ATP did perform a scan of the attachment.</span></span> 
  
12. <span data-ttu-id="98282-p115">Дважды щелкните сообщение с темой **встроенного по: новый веб-сайт travel**. Обратите внимание на то, что это сообщение было успешно доставлено в папке "Входящие".</span><span class="sxs-lookup"><span data-stu-id="98282-p115">Double-click the message with the subject **Fw: New travel web site**. Note that this message was successfully delivered to the Inbox.</span></span>
    
<span data-ttu-id="98282-193">Теперь с помощью этой среды можно создавать новые политики и экспериментировать с ATP.</span><span class="sxs-lookup"><span data-stu-id="98282-193">You can now use this environment to create new policies and experiment with ATP.</span></span>
  
> [!TIP]
> <span data-ttu-id="98282-194">Щелкните [здесь](http://aka.ms/catlgstack), чтобы просмотреть схему всех статей, относящихся к руководствам по лаборатории тестирования Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="98282-194">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="98282-195">См. также</span><span class="sxs-lookup"><span data-stu-id="98282-195">See Also</span></span>

[<span data-ttu-id="98282-196">Руководства по лаборатории тестирования для принятия облачных решений</span><span class="sxs-lookup"><span data-stu-id="98282-196">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="98282-197">Базовая конфигурация среды разработки и тестирования</span><span class="sxs-lookup"><span data-stu-id="98282-197">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="98282-198">Среда разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="98282-198">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="98282-199">DirSync для среды разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="98282-199">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="98282-200">Облако безопасности приложения для Office 365 dev/тестовой среды</span><span class="sxs-lookup"><span data-stu-id="98282-200">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="98282-201">Освоение облака и гибридные решения</span><span class="sxs-lookup"><span data-stu-id="98282-201">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md) 

[<span data-ttu-id="98282-202">Расширенной защитой для вложений надежных и безопасных ссылок</span><span class="sxs-lookup"><span data-stu-id="98282-202">Advanced threat protection for safe attachments and safe links</span></span>](https://support.office.com/article/Office-365-Advanced-Threat-Protection-E100FE7C-F2A1-4B7D-9E08-622330B83653)


