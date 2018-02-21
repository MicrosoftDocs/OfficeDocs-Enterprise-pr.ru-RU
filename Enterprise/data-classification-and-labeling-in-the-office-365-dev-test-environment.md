---
title: "Классификация и маркировка данных в среде разработки и тестирования Office 365"
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
ms.assetid: 919b8fc7-b0bc-46db-91f5-37342564e01b
description: "Сводка: Настройка и демонстрация классификации данных и маркировки с помощью клиента защиты информации Azure (AIP) в среде разработки и тестирования Office 365."
ms.openlocfilehash: 7243acecca0dd4c39ff6ef2aecd25091f25f2f53
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2018
---
# <a name="data-classification-and-labeling-in-the-office-365-devtest-environment"></a><span data-ttu-id="80453-103">Классификация и маркировка данных в среде разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="80453-103">Data classification and labeling in the Office 365 dev/test environment</span></span>

 <span data-ttu-id="80453-104">**Сводка:** Настройка и демонстрация классификации данных и маркировки с помощью клиента защиты информации Azure (AIP) в среде разработки и тестирования Office 365.</span><span class="sxs-lookup"><span data-stu-id="80453-104">**Summary:** Configure and demonstrate data classification and labeling using the Azure Information Protection (AIP) client in your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="80453-p101">Защита информации Azure клиента можно классифицировать документа перед загрузкой с папкой SharePoint Online в Office 365. Согласно инструкциям в этой статье установить клиент Azure защита информации и демонстрации классификации данных. Дополнительные сведения содержатся в разделе [Защита информации Azure](https://www.microsoft.com/cloud-platform/azure-information-protection).</span><span class="sxs-lookup"><span data-stu-id="80453-p101">The Azure Information Protection client allows you to classify a document before you upload it to a SharePoint Online folder in Office 365. With the instructions in this article, you install the Azure Information Protection client and demonstrate data classification. For more information, see [Azure Information Protection](https://www.microsoft.com/cloud-platform/azure-information-protection).</span></span>
  
> [!TIP]
> <span data-ttu-id="80453-108">Щелкните [здесь](http://aka.ms/catlgstack), чтобы просмотреть схему всех статей, относящихся к руководствам по лаборатории тестирования Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="80453-108">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-office-365-devtest-environment"></a><span data-ttu-id="80453-109">Этап 1. Создание среды разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="80453-109">Phase 1: Build out your Office 365 dev/test environment</span></span>

<span data-ttu-id="80453-110">Следуйте инструкциям, представленным в [Office 365 dev/тестовой среды](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="80453-110">Follow the instructions in [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
## <a name="phase-2-add-the-azure-information-protection-trial-subscription"></a><span data-ttu-id="80453-111">Этап 2. Добавление пробной подписки Azure Information Protection</span><span class="sxs-lookup"><span data-stu-id="80453-111">Phase 2: Add the Azure Information Protection trial subscription</span></span>

<span data-ttu-id="80453-p102">На этом этапе добавить защита информации Azure в среду Office 365 dev/test и активировать его учетные записи пользователей. Если вы настроили [Office 365 и Командной разработки и тестовой среде](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx), пропустите этот этап. Enterprise мобильности Suite пробной подписки включает в себя защита информации Azure лицензий.</span><span class="sxs-lookup"><span data-stu-id="80453-p102">In this phase, you add Azure Information Protection to your Office 365 dev/test environment and enable it for your user accounts. If you have configured the [Office 365 and EMS dev/test environment](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx), skip this phase. The Enterprise Mobility Suite trial subscription includes Azure Information Protection licenses.</span></span>
  
<span data-ttu-id="80453-115">Сначала оформите пробную подписку на Azure Information Protection.</span><span class="sxs-lookup"><span data-stu-id="80453-115">First, sign up for an Azure Information Protection trial subscription.</span></span>
  
### <a name="sign-up-for-an-azure-information-protection-trial-subscription"></a><span data-ttu-id="80453-116">Оформление пробной подписки на Azure Information Protection</span><span class="sxs-lookup"><span data-stu-id="80453-116">Sign up for an Azure Information Protection trial subscription</span></span>

1. <span data-ttu-id="80453-117">В Internet Explorer или в браузере перейдите на [http://portal.office.com](http://portal.office.com) и вход с помощью учетной записи глобального администратора Office 365.</span><span class="sxs-lookup"><span data-stu-id="80453-117">In Internet Explorer or your browser, go to [http://portal.office.com](http://portal.office.com) and sign in with your Office 365 global administrator account.</span></span>
    
2. <span data-ttu-id="80453-118">На вкладке **Microsoft Office для дома** щелкните плитку **администрирования** .</span><span class="sxs-lookup"><span data-stu-id="80453-118">On the **Microsoft Office Home** tab, click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="80453-119">На вкладке администрирования Office 365 на панели навигации слева щелкните **выставления счетов > службы приобретения**.</span><span class="sxs-lookup"><span data-stu-id="80453-119">On the Office 365 Admin tab, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="80453-p103">На странице " **службы приобретения** " Поиск элемента **Azure сведения о защите Premium P2** . Наведите указатель мыши на его и нажмите кнопку **Пуск бесплатную пробную версию**.</span><span class="sxs-lookup"><span data-stu-id="80453-p103">On the **Purchase services** page, find the **Azure Information Protection Premium P2** item. Hover your mouse over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="80453-122">На странице **Подтверждение заказа** щелкните **Попробовать сейчас**.</span><span class="sxs-lookup"><span data-stu-id="80453-122">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="80453-123">На странице **Получение заказа** нажмите кнопку **Продолжить**.</span><span class="sxs-lookup"><span data-stu-id="80453-123">On the **Order receipt** page, click **Continue**.</span></span>
    
<span data-ttu-id="80453-124">После этого включите лицензию Azure Information Protection для всех учетных записей пользователей.</span><span class="sxs-lookup"><span data-stu-id="80453-124">Next, you enable the Azure Information Protection license for all user accounts.</span></span>
  
1. <span data-ttu-id="80453-125">На вкладке Центр администрирования Office 365 щелкните **Пользователи**.</span><span class="sxs-lookup"><span data-stu-id="80453-125">On the Office 365 admin center tab, click **Users**.</span></span>
    
2.  <span data-ttu-id="80453-126">В списке учетных записей пользователей выберите учетную запись глобального администратора и нажмите кнопку **Изменить** для **лицензий на продукт**.</span><span class="sxs-lookup"><span data-stu-id="80453-126">In the list of user accounts, select your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="80453-127">Включить лицензии для **Azure сведения о защите Premium P2** для **на**, нажмите кнопку **Сохранить** и дважды нажмите кнопку **Закрыть** .</span><span class="sxs-lookup"><span data-stu-id="80453-127">Turn the product license for **Azure Information Protection Premium P2** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
4. <span data-ttu-id="80453-128">Повторите шаги 2 и 3 для других учетных записей пользователей (с первой по пятую).</span><span class="sxs-lookup"><span data-stu-id="80453-128">Repeat steps 2 and 3 for your other user accounts (User 1 through User 5).</span></span>
    
<span data-ttu-id="80453-129">Теперь ваша среда разработки и тестирования Office 365 содержит:</span><span class="sxs-lookup"><span data-stu-id="80453-129">Your Office 365 dev/test environment now has:</span></span>
  
- <span data-ttu-id="80453-130">Пробные подписки на Office 365 E5 корпоративный и Azure Information Protection.</span><span class="sxs-lookup"><span data-stu-id="80453-130">Office 365 E5 Enterprise and Azure Information Protection trial subscriptions.</span></span>
    
- <span data-ttu-id="80453-131">Все учетные записи, которые могут использовать Office 365 E5 корпоративный и Azure Information Protection.</span><span class="sxs-lookup"><span data-stu-id="80453-131">All of your user accounts enabled to use both Office 365 E5 Enterprise and Azure Information Protection.</span></span>
    
## <a name="phase-3-demonstrate-data-classification"></a><span data-ttu-id="80453-132">Этап 3. Демонстрация классификации данных</span><span class="sxs-lookup"><span data-stu-id="80453-132">Phase 3: Demonstrate data classification</span></span>

<span data-ttu-id="80453-133">На этом этапе вы демонстрируете, как классифицировать данные с помощью клиента Azure Information Protection и политики Azure Information Protection по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="80453-133">In this phase, you demonstrate data classification using the Azure Information Protection client and the default Azure Information Protection policy.</span></span>
  
<span data-ttu-id="80453-134">Если вы используете условную корпоративную среду разработки и тестирования Office 365, сначала необходимо установить Office 2016 на компьютере CLIENT1.</span><span class="sxs-lookup"><span data-stu-id="80453-134">If you are using the simulated enterprise Office 365 dev/test environment, you must first install Office 2016 on CLIENT1.</span></span>
  
1. <span data-ttu-id="80453-135">Используйте браузер и перейдите к [Azure портала](http://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="80453-135">Use your browser and go to the [Azure portal](http://portal.azure.com).</span></span>
    
2. <span data-ttu-id="80453-136">Нажмите кнопку **группы ресурсов >** [имя группы ресурсов] **> CLIENT1 > подключить**.</span><span class="sxs-lookup"><span data-stu-id="80453-136">Click **Resource Groups >** [your resource group name] **> CLIENT1 > Connect**.</span></span>
    
3. <span data-ttu-id="80453-137">Из CLIENT1 запустите Internet Explorer, перейдите на портале Office по [http://portal.office.com](http://portal.office.com)и затем выполните вход с User5 имя учетной записи и пароль.</span><span class="sxs-lookup"><span data-stu-id="80453-137">From CLIENT1, run Internet Explorer, go to the Office portal at [http://portal.office.com](http://portal.office.com), and then sign in with the User5 account name and password.</span></span>
    
4. <span data-ttu-id="80453-138">На вкладке **Microsoft Office для дома** щелкните **установить 2016 Office**.</span><span class="sxs-lookup"><span data-stu-id="80453-138">On the **Microsoft Office Home** tab, click **Install Office 2016**.</span></span>
    
5. <span data-ttu-id="80453-p104">Запустите файл для загрузки при появлении запроса и нажмите кнопку **Да** при появлении запроса контроля учетных записей пользователей. Дождитесь Office для установки. Закончив настройку, дважды нажмите кнопку **Закрыть** .</span><span class="sxs-lookup"><span data-stu-id="80453-p104">Run the download when prompted and click **Yes** when prompted by User Account Control. Wait for Office to install. When complete, click **Close** twice.</span></span>
    
<span data-ttu-id="80453-142">После этого установите клиент Azure Information Protection.</span><span class="sxs-lookup"><span data-stu-id="80453-142">Next, you install the Azure Information Protection client.</span></span>
  
1. <span data-ttu-id="80453-143">В браузере или Internet Explorer перейдите на [страницу загрузки Microsoft Azure Information Protection](https://www.microsoft.com/download/details.aspx?id=53018).</span><span class="sxs-lookup"><span data-stu-id="80453-143">In your browser or Internet Explorer, go to the [Microsoft Azure Information Protection download page](https://www.microsoft.com/download/details.aspx?id=53018).</span></span>
    
  - <span data-ttu-id="80453-144">Если вы используете облегченную версию среды разработки и тестирования Office 365, воспользуйтесь браузером на локальном компьютере.</span><span class="sxs-lookup"><span data-stu-id="80453-144">If you are using the lightweight version of the Office 365 dev/test environment, use the browser on your local computer.</span></span>
    
  - <span data-ttu-id="80453-145">Если вы используете условную корпоративную среду разработки и тестирования Office 365, запустите Internet Explorer на компьютере CLIENT1.</span><span class="sxs-lookup"><span data-stu-id="80453-145">If you are using the simulated enterprise Office 365 dev/test environment, run Internet Explorer from CLIENT1.</span></span>
    
2. <span data-ttu-id="80453-146">На странице загрузки **Microsoft Azure Information Protection** нажмите кнопку **загрузить**, нажмите кнопку **AzInfoProtection.exe**и нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="80453-146">On the **Microsoft Azure Information Protection** download page, click **Download**, click **AzInfoProtection.exe**, and then click **Next**.</span></span>
    
3. <span data-ttu-id="80453-147">При появлении соответствующего запроса запустите AzInfoProtection.exe.</span><span class="sxs-lookup"><span data-stu-id="80453-147">When prompted, run AzInfoProtection.exe.</span></span>
    
4. <span data-ttu-id="80453-148">В поле Клиент **Установка Azure защита информации** нажмите кнопку **принимаю**и нажмите кнопку **Да** при появлении запроса контроля учетных записей пользователей.</span><span class="sxs-lookup"><span data-stu-id="80453-148">In the **Install the Azure Information Protection** client box, click **I agree**, and then click **Yes** when prompted by User Account Control.</span></span>
    
5. <span data-ttu-id="80453-149">В диалоговом окне **успешного завершения** нажмите кнопку **Close.**</span><span class="sxs-lookup"><span data-stu-id="80453-149">In the **Completed successfully** box, click **Close.**</span></span>
    
<span data-ttu-id="80453-150">Теперь продемонстрируйте классификацию документов.</span><span class="sxs-lookup"><span data-stu-id="80453-150">Next, you demonstrate document classification.</span></span>
  
1. <span data-ttu-id="80453-151">Щелкните значок **Word** на панели задач.</span><span class="sxs-lookup"><span data-stu-id="80453-151">Click the **Word** icon in the taskbar.</span></span>
    
2. <span data-ttu-id="80453-152">После отображения соответствующего запроса войдите в систему, используя данные учетной записи User5.</span><span class="sxs-lookup"><span data-stu-id="80453-152">When prompted, sign in with the User5 account name and password.</span></span>
    
3. <span data-ttu-id="80453-153">Если вы только что установлены 2016 Office на компьютере CLIENT1 в **первых действий первого** нажмите кнопку **принять**.</span><span class="sxs-lookup"><span data-stu-id="80453-153">If you just installed Office 2016 on CLIENT1, in the **First things first** box, click **Accept**.</span></span>
    
4. <span data-ttu-id="80453-154">Выберите **новый документ**.</span><span class="sxs-lookup"><span data-stu-id="80453-154">Click **Blank document**.</span></span> 
    
    <span data-ttu-id="80453-155">Обратите внимание, в разделе **Защита** на ленте на вкладке **Главная** и строку классификации документов.</span><span class="sxs-lookup"><span data-stu-id="80453-155">Note the **Protection** section of the ribbon on the **Home** tab and the row of document classifications.</span></span>
    
5. <span data-ttu-id="80453-156">Введите текст в новый документ.</span><span class="sxs-lookup"><span data-stu-id="80453-156">In the blank document, type some text.</span></span>
    
6. <span data-ttu-id="80453-157">Нажмите кнопку **Файл > Сохранить**, введите имя **BeforeAIP**и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="80453-157">Click **File > Save**, type the name **BeforeAIP**, and then click **OK**.</span></span> 
    
7. <span data-ttu-id="80453-158">В строке классов документов щелкните стрелку вниз для **секрета**и нажмите кнопку **Все компании**.</span><span class="sxs-lookup"><span data-stu-id="80453-158">In the row of document classes, click the down arrow for **Secret**, and then click **All Company**.</span></span>
    
8. <span data-ttu-id="80453-159">Нажмите кнопку **Файл > Сохранить как**, введите имя **AfterAIP**и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="80453-159">Click **File > Save As**, type the name **AfterAIP**, and then click **OK**.</span></span>
    
9. <span data-ttu-id="80453-160">Нажмите кнопку **Проводник** в панели задач, а затем откройте папку « **документы** ».</span><span class="sxs-lookup"><span data-stu-id="80453-160">Click **File Explorer** in the taskbar, and then open the **Documents** folder.</span></span>
    
    <span data-ttu-id="80453-p105">Обратите внимание, различных размеров **BeforeAIP** и **AfterAIP** документы. Документ AfterAIP больше, так как он содержит сведения о классификации.</span><span class="sxs-lookup"><span data-stu-id="80453-p105">Note the different file sizes of the **BeforeAIP** and **AfterAIP** documents. The AfterAIP document is larger because it contains the classification information.</span></span>
    
<span data-ttu-id="80453-163">Теперь необходимо разрешить всем пользователям доступ к поддержке семейства веб-сайтов.</span><span class="sxs-lookup"><span data-stu-id="80453-163">Next, you allow everyone to access the Support site collection.</span></span>
  
1. <span data-ttu-id="80453-164">На вкладке **Microsoft Office для дома** выберите **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="80453-164">On the **Microsoft Office Home** tab, click **SharePoint**.</span></span>
    
2. <span data-ttu-id="80453-165">На вкладке **SharePoint** выберите **Поддержка семейства веб-сайтов**.</span><span class="sxs-lookup"><span data-stu-id="80453-165">From the **SharePoint** tab, click **Support site collection**.</span></span>
    
3. <span data-ttu-id="80453-166">В правом верхнем углу щелкните значок **Параметры** и выберите **общий доступ**.</span><span class="sxs-lookup"><span data-stu-id="80453-166">In the upper right, click the **Settings** icon, and then click **Shared with**.</span></span>
    
4. <span data-ttu-id="80453-167">В поле **общий доступ «Поддержка семейства веб-сайтов»**нажмите кнопку **Дополнительно**.</span><span class="sxs-lookup"><span data-stu-id="80453-167">In **Share 'Support site collection'**, click **Advanced**.</span></span>
    
5. <span data-ttu-id="80453-168">В списке групп SharePoint выберите **семейство сайтов поддержки участников**.</span><span class="sxs-lookup"><span data-stu-id="80453-168">In the list of SharePoint groups, click **Support site collection Members**.</span></span>
    
6. <span data-ttu-id="80453-169">На странице **Пользователи и группы** нажмите кнопку **Создать**.</span><span class="sxs-lookup"><span data-stu-id="80453-169">On the **People and Groups** page, click **New**.</span></span>
    
7. <span data-ttu-id="80453-170">В **папке «Поддержка семейства веб-сайтов»**, введите **все**, щелкните **все, кроме внешних пользователей**и нажмите кнопку **совместный доступ.**</span><span class="sxs-lookup"><span data-stu-id="80453-170">In **Share 'Support site collection'**, type **Everyone**, click **Everyone except external users**, and then click **Share.**</span></span>
    
8. <span data-ttu-id="80453-171">Закройте вкладку **пользователи и группы** .</span><span class="sxs-lookup"><span data-stu-id="80453-171">Close the **People and Groups** tab.</span></span>
    
<span data-ttu-id="80453-172">Теперь войдите в систему под учетной записью User5 и отправьте защищенный с помощью AIP документ в папку "Документы" поддержки семейства веб-сайтов.</span><span class="sxs-lookup"><span data-stu-id="80453-172">Next, you sign in with your User5 account and upload the AIP-protected document to the Documents folder of the Support site collection.</span></span>
  
1. <span data-ttu-id="80453-173">На вкладке **Microsoft Office для дома** , в правом верхнем углу щелкните значок пользователя и нажмите кнопку **Выход**.</span><span class="sxs-lookup"><span data-stu-id="80453-173">On the **Microsoft Office Home** tab, in the upper right, click the user icon, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="80453-174">Перейдите к [http://portal.office.com](http://portal.office.com).</span><span class="sxs-lookup"><span data-stu-id="80453-174">Go to [http://portal.office.com](http://portal.office.com).</span></span>
    
3. <span data-ttu-id="80453-175">На ** вход Office 365 ** щелкните имя учетной записи User5 и вход.</span><span class="sxs-lookup"><span data-stu-id="80453-175">On the ** Office 365 sign in** page, click the User5 account name and sign in.</span></span>
    
4. <span data-ttu-id="80453-176">На вкладке **Microsoft Office для дома** щелкните **SharePoint > поддержки семейства веб-сайтов**.</span><span class="sxs-lookup"><span data-stu-id="80453-176">On the **Microsoft Office Home** tab, click **SharePoint > Support site collection**.</span></span>
    
5. <span data-ttu-id="80453-177">Щелкните **документы**, нажмите кнопку **Отправить**, щелкните **AfterAIP** документ и нажмите кнопку **Открыть**.</span><span class="sxs-lookup"><span data-stu-id="80453-177">Click **Documents**, click **Upload**, click the **AfterAIP** document, and then click **Open**.</span></span>
    
    <span data-ttu-id="80453-178">Файл ПослеAIP.docx отобразится в папке "Документы" поддержки семейства веб-сайтов.</span><span class="sxs-lookup"><span data-stu-id="80453-178">You should see AfterAIP.docx in the Documents folder on the Support site collection.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="80453-179">См. также</span><span class="sxs-lookup"><span data-stu-id="80453-179">See Also</span></span>

[<span data-ttu-id="80453-180">Руководства по лаборатории тестирования для принятия облачных решений</span><span class="sxs-lookup"><span data-stu-id="80453-180">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)

[<span data-ttu-id="80453-181">Office 365 и Командной разработки и тестовой среде</span><span class="sxs-lookup"><span data-stu-id="80453-181">Office 365 and EMS dev/test environment</span></span>](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx)
  
[<span data-ttu-id="80453-182">Azure Information Protection</span><span class="sxs-lookup"><span data-stu-id="80453-182">Azure Information Protection</span></span>](https://www.microsoft.com/cloud-platform/azure-information-protection)


