---
title: Классификация и маркировка данных в среде разработки и тестирования Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: 919b8fc7-b0bc-46db-91f5-37342564e01b
description: Сводка. Настройка и демонстрация классификации и маркировки данных с помощью клиента Azure Information Protection (AIP) в среде разработки и тестирования Office 365.
ms.openlocfilehash: cf369894eb87381e3837a52946a0ba2b9705bf70
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067937"
---
# <a name="data-classification-and-labeling-in-the-office-365-devtest-environment"></a><span data-ttu-id="8bc19-103">Классификация и маркировка данных в среде разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="8bc19-103">Data classification and labeling in the Office 365 dev/test environment</span></span>

 <span data-ttu-id="8bc19-104">**Сводка.** Настройка и демонстрация классификации и маркировки данных с помощью клиента Azure Information Protection (AIP) в среде разработки и тестирования Office 365.</span><span class="sxs-lookup"><span data-stu-id="8bc19-104">**Summary:** Configure and demonstrate data classification and labeling using the Azure Information Protection (AIP) client in your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="8bc19-105">Клиент Azure Information Protection позволяет классифицировать документ перед его отправкой в папку SharePoint Online в Office 365.</span><span class="sxs-lookup"><span data-stu-id="8bc19-105">The Azure Information Protection client lets you classify a document before you upload it to a SharePoint Online folder in Office 365.</span></span> <span data-ttu-id="8bc19-106">С помощью инструкций в этой статье вы можете установить клиент Azure Information Protection и продемонстрировать классификацию данных.</span><span class="sxs-lookup"><span data-stu-id="8bc19-106">With the instructions in this article, you install the Azure Information Protection client and demonstrate data classification.</span></span> <span data-ttu-id="8bc19-107">Для получения дополнительных сведений см [Azure Information Protection](https://www.microsoft.com/cloud-platform/azure-information-protection).</span><span class="sxs-lookup"><span data-stu-id="8bc19-107">For more information, see [Azure Information Protection](https://www.microsoft.com/cloud-platform/azure-information-protection).</span></span>
  
> [!TIP]
> <span data-ttu-id="8bc19-108">Щелкните [здесь](http://aka.ms/catlgstack), чтобы просмотреть схему всех статей, относящихся к руководствам по лаборатории тестирования в Office 365.</span><span class="sxs-lookup"><span data-stu-id="8bc19-108">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the Office 365 Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-office-365-devtest-environment"></a><span data-ttu-id="8bc19-109">Этап 1. Создание среды разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="8bc19-109">Phase 1: Build out your Office 365 dev/test environment</span></span>

<span data-ttu-id="8bc19-110">Следуйте инструкциям в статье [Office 365 dev/test environment](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="8bc19-110">Follow the instructions in [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
## <a name="phase-2-add-the-azure-information-protection-trial-subscription"></a><span data-ttu-id="8bc19-111">Этап 2. Добавление пробной подписки Azure Information Protection</span><span class="sxs-lookup"><span data-stu-id="8bc19-111">Phase 2: Add the Azure Information Protection trial subscription</span></span>

<span data-ttu-id="8bc19-112">На этом этапе вы добавите службу Azure Information Protection в среду разработки и тестирования Office 365 и включите ее для учетных записей пользователей.</span><span class="sxs-lookup"><span data-stu-id="8bc19-112">In this phase, you add Azure Information Protection to your Office 365 dev/test environment and enable it for your user accounts.</span></span> <span data-ttu-id="8bc19-113">Если вы настроили [Office 365 and EMS dev/test environment](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx), пропустите этот этап.</span><span class="sxs-lookup"><span data-stu-id="8bc19-113">If you have configured the [Office 365 and EMS dev/test environment](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx), skip this phase.</span></span> <span data-ttu-id="8bc19-114">Пробная подписка на Enterprise Mobility Suite включает лицензии Azure Information Protection.</span><span class="sxs-lookup"><span data-stu-id="8bc19-114">The Enterprise Mobility Suite trial subscription includes Azure Information Protection licenses.</span></span>
  
<span data-ttu-id="8bc19-115">Сначала оформите пробную подписку на Azure Information Protection.</span><span class="sxs-lookup"><span data-stu-id="8bc19-115">First, sign up for an Azure Information Protection trial subscription.</span></span>
  
### <a name="sign-up-for-an-azure-information-protection-trial-subscription"></a><span data-ttu-id="8bc19-116">Оформление пробной подписки на Azure Information Protection</span><span class="sxs-lookup"><span data-stu-id="8bc19-116">Sign up for an Azure Information Protection trial subscription</span></span>

1. <span data-ttu-id="8bc19-117">В Internet Explorer или в браузере перейдите к [http://admin.microsoft.com](http://admin.microsoft.com) учетной записи глобального администратора Office 365 и войдите в нее.</span><span class="sxs-lookup"><span data-stu-id="8bc19-117">In Internet Explorer or your browser, go to [http://admin.microsoft.com](http://admin.microsoft.com) and sign in with your Office 365 global administrator account.</span></span>
    
2. <span data-ttu-id="8bc19-118">На главной вкладке **Microsoft Office** щелкните плитку **Администратор**.</span><span class="sxs-lookup"><span data-stu-id="8bc19-118">On the **Microsoft Office Home** tab, click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="8bc19-119">На вкладке "Администратор Office 365", в области навигации слева, нажмите **Выставление счетов > Приобретение служб**.</span><span class="sxs-lookup"><span data-stu-id="8bc19-119">On the Office 365 Admin tab, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="8bc19-p103">На странице **Приобретение служб** найдите элемент **Azure Information Protection Premium P2**. Наведите на него указатель мыши и нажмите **Начать использовать**.</span><span class="sxs-lookup"><span data-stu-id="8bc19-p103">On the **Purchase services** page, find the **Azure Information Protection Premium P2** item. Hover your mouse over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="8bc19-122">На странице **Подтверждение заказа** нажмите кнопку **Попробовать**.</span><span class="sxs-lookup"><span data-stu-id="8bc19-122">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="8bc19-123">На странице **Получение заказа** нажмите кнопку **Продолжить**.</span><span class="sxs-lookup"><span data-stu-id="8bc19-123">On the **Order receipt** page, click **Continue**.</span></span>
    
<span data-ttu-id="8bc19-124">После этого включите лицензию Azure Information Protection для всех учетных записей пользователей.</span><span class="sxs-lookup"><span data-stu-id="8bc19-124">Next, you enable the Azure Information Protection license for all user accounts.</span></span>
  
1. <span data-ttu-id="8bc19-125">На вкладке центра администрирования Microsoft 365 щелкните **Пользователи**.</span><span class="sxs-lookup"><span data-stu-id="8bc19-125">On the Microsoft 365 admin center tab, click **Users**.</span></span>
    
2.  <span data-ttu-id="8bc19-126"> В списке учетных записей пользователей выберите свою учетную запись глобального администратора и нажмите *\*Изменить** в поле *\*Лицензии на продукты*\*.</span><span class="sxs-lookup"><span data-stu-id="8bc19-126">In the list of user accounts, select your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="8bc19-127">Включите лицензию на продукт **Azure Information Protection Premium P2** в значение **вкл**., нажмите кнопку **сохранить,** а затем дважды нажмите кнопку **Закрыть** .</span><span class="sxs-lookup"><span data-stu-id="8bc19-127">Turn the product license for **Azure Information Protection Premium P2** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
4. <span data-ttu-id="8bc19-128">Повторите шаги 2 и 3 для других учетных записей пользователей (с первой по пятую).</span><span class="sxs-lookup"><span data-stu-id="8bc19-128">Repeat steps 2 and 3 for your other user accounts (User 1 through User 5).</span></span>
    
<span data-ttu-id="8bc19-129">Теперь ваша среда разработки и тестирования Office 365 содержит:</span><span class="sxs-lookup"><span data-stu-id="8bc19-129">Your Office 365 dev/test environment now has:</span></span>
  
- <span data-ttu-id="8bc19-130">Пробные подписки на Office 365 E5 корпоративный и Azure Information Protection.</span><span class="sxs-lookup"><span data-stu-id="8bc19-130">Office 365 E5 Enterprise and Azure Information Protection trial subscriptions.</span></span>
    
- <span data-ttu-id="8bc19-131">Все учетные записи, которые могут использовать Office 365 E5 корпоративный и Azure Information Protection.</span><span class="sxs-lookup"><span data-stu-id="8bc19-131">All of your user accounts enabled to use both Office 365 E5 Enterprise and Azure Information Protection.</span></span>
    
## <a name="phase-3-demonstrate-data-classification"></a><span data-ttu-id="8bc19-132">Этап 3. Демонстрация классификации данных</span><span class="sxs-lookup"><span data-stu-id="8bc19-132">Phase 3: Demonstrate data classification</span></span>

<span data-ttu-id="8bc19-133">На этом этапе вы демонстрируете, как классифицировать данные с помощью клиента Azure Information Protection и политики Azure Information Protection по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="8bc19-133">In this phase, you demonstrate data classification using the Azure Information Protection client and the default Azure Information Protection policy.</span></span>
  
<span data-ttu-id="8bc19-134">Если вы используете условную корпоративную среду разработки и тестирования Office 365, сначала необходимо установить Office 2016 на компьютере CLIENT1.</span><span class="sxs-lookup"><span data-stu-id="8bc19-134">If you are using the simulated enterprise Office 365 dev/test environment, you must first install Office 2016 on CLIENT1.</span></span>
  
1. <span data-ttu-id="8bc19-135">Используйте браузер и перейдите на [портал Azure](http://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="8bc19-135">Use your browser and go to the [Azure portal](http://portal.azure.com).</span></span>
    
2. <span data-ttu-id="8bc19-136">	Щелкните *\*Группы ресурсов >** [имя вашей группы ресурсов] *\*> CLIENT1 > Подключиться*\*.</span><span class="sxs-lookup"><span data-stu-id="8bc19-136">Click **Resource Groups >** [your resource group name] **> CLIENT1 > Connect**.</span></span>
    
3. <span data-ttu-id="8bc19-137">На компьютере CLIENT1 запустите Internet Explorer, перейдите на портал Office по адресу [http://admin.microsoft.com](http://admin.microsoft.com), а затем войдите в систему, используя имя и пароль учетной записи User5.</span><span class="sxs-lookup"><span data-stu-id="8bc19-137">From CLIENT1, run Internet Explorer, go to the Office portal at [http://admin.microsoft.com](http://admin.microsoft.com), and then sign in with the User5 account name and password.</span></span>
    
4. <span data-ttu-id="8bc19-138">На главной вкладке **Microsoft Office** щелкните **Установить Office 2016**.</span><span class="sxs-lookup"><span data-stu-id="8bc19-138">On the **Microsoft Office Home** tab, click **Install Office 2016**.</span></span>
    
5. <span data-ttu-id="8bc19-p104">	При появлении соответствующего запроса запустите загрузку и нажмите кнопку *\*Да** при отображении запроса контроля учетных записей. Подождите завершения установки Office. После завершения дважды щелкните кнопку *\*Закрыть*\*.</span><span class="sxs-lookup"><span data-stu-id="8bc19-p104">Run the download when prompted and click **Yes** when prompted by User Account Control. Wait for Office to install. When complete, click **Close** twice.</span></span>
    
<span data-ttu-id="8bc19-142">После этого установите клиент Azure Information Protection.</span><span class="sxs-lookup"><span data-stu-id="8bc19-142">Next, you install the Azure Information Protection client.</span></span>
  
1. <span data-ttu-id="8bc19-143">В браузере или Internet Explorer перейдите на [страницу загрузки Microsoft Azure Information Protection](https://www.microsoft.com/download/details.aspx?id=53018).</span><span class="sxs-lookup"><span data-stu-id="8bc19-143">In your browser or Internet Explorer, go to the [Microsoft Azure Information Protection download page](https://www.microsoft.com/download/details.aspx?id=53018).</span></span>
    
  - <span data-ttu-id="8bc19-144">Если вы используете облегченную версию среды разработки и тестирования Office 365, воспользуйтесь браузером на локальном компьютере.</span><span class="sxs-lookup"><span data-stu-id="8bc19-144">If you are using the lightweight version of the Office 365 dev/test environment, use the browser on your local computer.</span></span>
    
  - <span data-ttu-id="8bc19-145">Если вы используете условную корпоративную среду разработки и тестирования Office 365, запустите Internet Explorer на компьютере CLIENT1.</span><span class="sxs-lookup"><span data-stu-id="8bc19-145">If you are using the simulated enterprise Office 365 dev/test environment, run Internet Explorer from CLIENT1.</span></span>
    
2. <span data-ttu-id="8bc19-146">На странице загрузки **Microsoft Azure Information Protection** щелкните **Загрузить**, затем — **AzInfoProtection.exe** и **Далее**.</span><span class="sxs-lookup"><span data-stu-id="8bc19-146">On the **Microsoft Azure Information Protection** download page, click **Download**, click **AzInfoProtection.exe**, and then click **Next**.</span></span>
    
3. <span data-ttu-id="8bc19-147">При появлении соответствующего запроса запустите AzInfoProtection.exe.</span><span class="sxs-lookup"><span data-stu-id="8bc19-147">When prompted, run AzInfoProtection.exe.</span></span>
    
4. <span data-ttu-id="8bc19-148">В диалоговом окне **Установка Azure Information Protection** клиента при отображении соответствующего запроса контроля учетных записей щелкните **Принимаю**, затем — **Да**.</span><span class="sxs-lookup"><span data-stu-id="8bc19-148">In the **Install the Azure Information Protection** client box, click **I agree**, and then click **Yes** when prompted by User Account Control.</span></span>
    
5. <span data-ttu-id="8bc19-149">В диалоговом окне \*\*Успешно завершено \*\* щелкните **Закрыть**.</span><span class="sxs-lookup"><span data-stu-id="8bc19-149">In the **Completed successfully** box, click **Close.**</span></span>
    
<span data-ttu-id="8bc19-150">Теперь продемонстрируйте классификацию документов.</span><span class="sxs-lookup"><span data-stu-id="8bc19-150">Next, you demonstrate document classification.</span></span>
  
1. <span data-ttu-id="8bc19-151">Щелкните значок **Word** на панели задач.</span><span class="sxs-lookup"><span data-stu-id="8bc19-151">Click the **Word** icon in the taskbar.</span></span>
    
2. <span data-ttu-id="8bc19-152">После отображения соответствующего запроса войдите в систему, используя данные учетной записи User5.</span><span class="sxs-lookup"><span data-stu-id="8bc19-152">When prompted, sign in with the User5 account name and password.</span></span>
    
3. <span data-ttu-id="8bc19-153">Если вы только что установили Office 2016 на компьютере CLIENT1, в диалоговом окне **В первую очередь — самое важное** щелкните **Принять**.</span><span class="sxs-lookup"><span data-stu-id="8bc19-153">If you just installed Office 2016 on CLIENT1, in the **First things first** box, click **Accept**.</span></span>
    
4. <span data-ttu-id="8bc19-154">Щелкните **Новый документ**. </span><span class="sxs-lookup"><span data-stu-id="8bc19-154">Click **Blank document**.</span></span> 
    
    <span data-ttu-id="8bc19-155">Обратите внимание на раздел \*\*Защита \*\*, отображаемый в ленте на вкладке **Главная** и строку классификации документа.</span><span class="sxs-lookup"><span data-stu-id="8bc19-155">Note the **Protection** section of the ribbon on the **Home** tab and the row of document classifications.</span></span>
    
5. <span data-ttu-id="8bc19-156">Введите текст в новый документ.</span><span class="sxs-lookup"><span data-stu-id="8bc19-156">In the blank document, type some text.</span></span>
    
6. <span data-ttu-id="8bc19-157">Щелкните **Файл > Сохранить**, введите имя **ДоAIP**, а затем нажмите **OK**. </span><span class="sxs-lookup"><span data-stu-id="8bc19-157">Click **File > Save**, type the name **BeforeAIP**, and then click **OK**.</span></span> 
    
7. <span data-ttu-id="8bc19-158">В строке класса документа щелкните стрелку вниз для класса **Секретный**, а затем выберите пункт **Вся компания**.</span><span class="sxs-lookup"><span data-stu-id="8bc19-158">In the row of document classes, click the down arrow for **Secret**, and then click **All Company**.</span></span>
    
8. <span data-ttu-id="8bc19-159">Щелкните **Файл > Сохранить как**, введите имя **ПослеAIP**, а затем щелкните **OK**.</span><span class="sxs-lookup"><span data-stu-id="8bc19-159">Click **File > Save As**, type the name **AfterAIP**, and then click **OK**.</span></span>
    
9. <span data-ttu-id="8bc19-160">Нажмите кнопку **Проводник** на панели задач, а затем откройте папку **Документы**.</span><span class="sxs-lookup"><span data-stu-id="8bc19-160">Click **File Explorer** in the taskbar, and then open the **Documents** folder.</span></span>
    
    <span data-ttu-id="8bc19-161">Обратите внимание, что файлы **ДоAIP** и **ПослеAIP** имеют разный размер.</span><span class="sxs-lookup"><span data-stu-id="8bc19-161">Note the different file sizes of the **BeforeAIP** and **AfterAIP** documents.</span></span> <span data-ttu-id="8bc19-162">Документ Послеaip больше, так как содержит сведения о классификации.</span><span class="sxs-lookup"><span data-stu-id="8bc19-162">The AfterAIP document is larger because it has the classification information.</span></span>
    
<span data-ttu-id="8bc19-163">Теперь необходимо разрешить всем пользователям доступ к поддержке семейства веб-сайтов.</span><span class="sxs-lookup"><span data-stu-id="8bc19-163">Next, you allow everyone to access the Support site collection.</span></span>
  
1. <span data-ttu-id="8bc19-164">На вкладке **Домашняя страница Microsoft Office** выберите элемент **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="8bc19-164">On the **Microsoft Office Home** tab, click **SharePoint**.</span></span>
    
2. <span data-ttu-id="8bc19-165">На вкладке **SharePoint** щелкните **Поддержка семейства веб-сайтов**.</span><span class="sxs-lookup"><span data-stu-id="8bc19-165">From the **SharePoint** tab, click **Support site collection**.</span></span>
    
3. <span data-ttu-id="8bc19-166">Щелкните значок **Параметры** в верхней правой части страницы, а затем щелкните **Общий доступ**.</span><span class="sxs-lookup"><span data-stu-id="8bc19-166">In the upper right, click the **Settings** icon, and then click **Shared with**.</span></span>
    
4. <span data-ttu-id="8bc19-167">В списке **общий доступ к семейству веб-сайтов поддержки**нажмите **Дополнительно**.</span><span class="sxs-lookup"><span data-stu-id="8bc19-167">In **Share 'Support site collection'**, click **Advanced**.</span></span>
    
5. <span data-ttu-id="8bc19-168">В списке групп SharePoint выберите **Поддержка пользователей семейства веб-сайтов**.</span><span class="sxs-lookup"><span data-stu-id="8bc19-168">In the list of SharePoint groups, click **Support site collection Members**.</span></span>
    
6. <span data-ttu-id="8bc19-169">На странице **Пользователи и группы** нажмите кнопку **Создать**.</span><span class="sxs-lookup"><span data-stu-id="8bc19-169">On the **People and Groups** page, click **New**.</span></span>
    
7. <span data-ttu-id="8bc19-170">В окне **общий доступ к семейству веб-сайтов поддержки**введите **все**, щелкните **все, кроме внешних пользователей**, а затем щелкните **общий доступ.**</span><span class="sxs-lookup"><span data-stu-id="8bc19-170">In **Share 'Support site collection'**, type **Everyone**, click **Everyone except external users**, and then click **Share.**</span></span>
    
8. <span data-ttu-id="8bc19-171">Закройте вкладку **Пользователи и группы**.</span><span class="sxs-lookup"><span data-stu-id="8bc19-171">Close the **People and Groups** tab.</span></span>
    
<span data-ttu-id="8bc19-172">Теперь войдите в систему под учетной записью User5 и отправьте защищенный с помощью AIP документ в папку "Документы" поддержки семейства веб-сайтов.</span><span class="sxs-lookup"><span data-stu-id="8bc19-172">Next, you sign in with your User5 account and upload the AIP-protected document to the Documents folder of the Support site collection.</span></span>
  
1. <span data-ttu-id="8bc19-173">На вкладке **Домашняя страница Microsoft Office** щелкните значок пользователя в верхней правой части, затем нажмите **Выйти**.</span><span class="sxs-lookup"><span data-stu-id="8bc19-173">On the **Microsoft Office Home** tab, in the upper right, click the user icon, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="8bc19-174">Перейдите по ссылке [http://admin.microsoft.com](http://admin.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="8bc19-174">Go to [http://admin.microsoft.com](http://admin.microsoft.com).</span></span>
    
3. <span data-ttu-id="8bc19-175">На странице **входа в Office 365** щелкните имя учетной записи User5 и войдите в систему.</span><span class="sxs-lookup"><span data-stu-id="8bc19-175">On the **Office 365 sign in** page, click the User5 account name and sign in.</span></span>
    
4. <span data-ttu-id="8bc19-176">На главной вкладке **Microsoft Office** щелкните **SharePoint > Поддержка семейства веб-сайтов**.</span><span class="sxs-lookup"><span data-stu-id="8bc19-176">On the **Microsoft Office Home** tab, click **SharePoint > Support site collection**.</span></span>
    
5. <span data-ttu-id="8bc19-177">Щелкните **Документы**, **Отправить**, а затем выберите документ **ПослеAIP** и нажмите **Открыть**.</span><span class="sxs-lookup"><span data-stu-id="8bc19-177">Click **Documents**, click **Upload**, click the **AfterAIP** document, and then click **Open**.</span></span>
    
    <span data-ttu-id="8bc19-178">Файл ПослеAIP.docx отобразится в папке "Документы" поддержки семейства веб-сайтов.</span><span class="sxs-lookup"><span data-stu-id="8bc19-178">You should see AfterAIP.docx in the Documents folder on the Support site collection.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="8bc19-179">См. также</span><span class="sxs-lookup"><span data-stu-id="8bc19-179">See Also</span></span>

[<span data-ttu-id="8bc19-180">Руководства по лаборатории тестирования для облачных решений</span><span class="sxs-lookup"><span data-stu-id="8bc19-180">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)

[<span data-ttu-id="8bc19-181">Среда разработки и тестирования Office 365 и EMS</span><span class="sxs-lookup"><span data-stu-id="8bc19-181">Office 365 and EMS dev/test environment</span></span>](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx)
  
[<span data-ttu-id="8bc19-182">Azure Information Protection</span><span class="sxs-lookup"><span data-stu-id="8bc19-182">Azure Information Protection</span></span>](https://www.microsoft.com/cloud-platform/azure-information-protection)


