---
title: Advanced eDiscovery для среды разработки и тестирования Office 365
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
ms.assetid: d4c49a6f-abfd-4d68-b353-259b4eefb033
description: Сводка. Настройка и демонстрация Office 365 Advanced eDiscovery с образцами данных в среде разработки и тестирования Office 365.
ms.openlocfilehash: 6c52c7c7fdc31616e58f186484d2d8c4506b7ea6
ms.sourcegitcommit: 4ef8e113fa20b539de1087422455fc26ff123d55
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "30573823"
---
# <a name="advanced-ediscovery-for-your-office-365-devtest-environment"></a><span data-ttu-id="2b2ab-103">Advanced eDiscovery для среды разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="2b2ab-103">Advanced eDiscovery for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="2b2ab-104">**Сводка.** Настройка и демонстрация Office 365 Advanced eDiscovery с образцами данных в среде разработки и тестирования Office 365.</span><span class="sxs-lookup"><span data-stu-id="2b2ab-104">**Summary:** Configure and demonstrate Office 365 Advanced eDiscovery with sample data in your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="2b2ab-105">Office 365 Advanced eDiscovery позволяет быстро находить и анализировать релевантную информацию по данным, хранящимся в Office 365, включая электронную почту и документы.</span><span class="sxs-lookup"><span data-stu-id="2b2ab-105">Office 365 Advanced eDiscovery lets you quickly find and analyze relevant information across the data that is stored in Office 365, including email and documents.</span></span> <span data-ttu-id="2b2ab-106">Это поможет вам сэкономить огромное количество времени и сократить расходы, особенно во время судебных разбирательств.</span><span class="sxs-lookup"><span data-stu-id="2b2ab-106">This can save enormous amounts of time and expense, especially in litigation situations.</span></span> <span data-ttu-id="2b2ab-107">Дополнительные сведения см. в статье [Office 365 Advanced eDiscovery](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4).</span><span class="sxs-lookup"><span data-stu-id="2b2ab-107">For more information, see [Office 365 Advanced eDiscovery](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4).</span></span>
  
<span data-ttu-id="2b2ab-108">Выполнив действия, описанные в этой статье, вы создадите небольшой набор данных для урегулирования вымышленных разногласий по контракту и проанализируете его с помощью Advanced eDiscovery.</span><span class="sxs-lookup"><span data-stu-id="2b2ab-108">With the instructions in this article, you create a small set of data for a fictional contract dispute and analyze it with Advanced eDiscovery.</span></span>
  
> [!TIP]
> <span data-ttu-id="2b2ab-109">Щелкните [здесь](http://aka.ms/catlgstack), чтобы просмотреть схему всех статей, относящихся к руководствам по лаборатории тестирования в One Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="2b2ab-109">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-create-your-office-365-devtest-environment"></a><span data-ttu-id="2b2ab-110">Этап 1. Создание среды разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="2b2ab-110">Phase 1: Create your Office 365 dev/test environment</span></span>

<span data-ttu-id="2b2ab-111">Если вы просто хотите протестировать расширенные функции обнаружения электронных данных в упрощенном способе с минимальными требованиями, следуйте инструкциям в статье 2 и 3 этапа [разработки и тестирования Office 365 для среды разработки и тестирования](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="2b2ab-111">If you just want to test Advanced eDiscovery in a lightweight way with the minimum requirements, follow the instructions in Phase 2 and Phase 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="2b2ab-112">Если вы хотите протестировать расширенные функции обнаружения электронных данных на имитации предприятия, следуйте инструкциям в статье [DirSync для среды разработки и тестирования Office 365](dirsync-for-your-office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="2b2ab-112">If you want to test Advanced eDiscovery in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="2b2ab-113">Чтобы тестировать Advanced eDiscovery, не требуется среда для имитированного предприятия, предусматривающая подключение имитированной интрасети к Интернету и синхронизацию каталогов для леса Windows Server AD.</span><span class="sxs-lookup"><span data-stu-id="2b2ab-113">Testing Advanced eDiscovery does not require the simulated enterprise environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest.</span></span> <span data-ttu-id="2b2ab-114">Он предоставляется в качестве варианта, чтобы можно было выполнять тестирование и эксперименты в среде, представляющей типичную организацию.</span><span class="sxs-lookup"><span data-stu-id="2b2ab-114">It is provided here as an option so that you can perform testing and experimentation in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-create-example-data-for-advanced-ediscovery"></a><span data-ttu-id="2b2ab-115">Этап 2. Создание образца данных для Advanced eDiscovery</span><span class="sxs-lookup"><span data-stu-id="2b2ab-115">Phase 2: Create example data for Advanced eDiscovery</span></span>

<span data-ttu-id="2b2ab-116">В этой процедуре мы создадим электронные сообщения, которые затем будут анализироваться в рамках дела Advanced eDiscovery.</span><span class="sxs-lookup"><span data-stu-id="2b2ab-116">In this procedure, you create email messages that will you later analyze in an Advanced eDiscovery case.</span></span>
  
1. <span data-ttu-id="2b2ab-117">Откройте Internet Explorer и войдите [https://outlook.com](https://outlook.com) в учетную запись Outlook, созданную на этапе 2[среды разработки и тестирования Office 365](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="2b2ab-117">Open Internet Explorer and sign in at [https://outlook.com](https://outlook.com) to the Outlook account you created in Phase 2 of[Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
    
  - <span data-ttu-id="2b2ab-118">Если вы используете упрощенную среду разработки и тестирования, запустите частный сеанс Internet Explorer и войдите с локального компьютера.</span><span class="sxs-lookup"><span data-stu-id="2b2ab-118">If you are using the lightweight dev/test environment, open a private session of Internet Explorer and sign in from your local computer.</span></span>
    
  - <span data-ttu-id="2b2ab-119">Если вы используете имитируемую среду разработки и тестирования предприятия, используйте портал Azure ([https://portal.azure.com](https://portal.azure.com)), чтобы подключиться к ВИРТУАЛЬНОЙ машине CLIENT1, а затем выполните вход с компьютера CLIENT1.</span><span class="sxs-lookup"><span data-stu-id="2b2ab-119">If you are using the simulated enterprise dev/test environment, use the Azure portal ([https://portal.azure.com](https://portal.azure.com)) to connect to the CLIENT1 virtual machine, and then sign in from CLIENT1.</span></span>
    
2. <span data-ttu-id="2b2ab-120">На вкладке **Почта Outlook** нажмите кнопку **Создать**.</span><span class="sxs-lookup"><span data-stu-id="2b2ab-120">On the **Outlook Mail** tab, click **New**.</span></span>
    
3. <span data-ttu-id="2b2ab-121">В поле **Кому**введите электронный адрес учетной записи User6 пробной подписки ( **User6 @.**<organization name></span><span class="sxs-lookup"><span data-stu-id="2b2ab-121">In **To**, type the email address of the User6 account of your trial subscription ( **user6@.**<organization name></span></span> <span data-ttu-id="2b2ab-122">**. onmicrosoft.com**).</span><span class="sxs-lookup"><span data-stu-id="2b2ab-122">**.onmicrosoft.com**).</span></span>
    
4. <span data-ttu-id="2b2ab-123">В поле темы введите **Тестовое сообщение 1**.</span><span class="sxs-lookup"><span data-stu-id="2b2ab-123">For the subject, type **Test email 1**.</span></span>
    
5. <span data-ttu-id="2b2ab-124">В тексте введите **Черновик контракта Tailspin**, а затем нажмите кнопку **Отправить**.</span><span class="sxs-lookup"><span data-stu-id="2b2ab-124">In the body, type **Tailspin contract draft**, and then click **Send**.</span></span>
    
6. <span data-ttu-id="2b2ab-125">На вкладке **Почта Outlook** нажмите кнопку **Создать**.</span><span class="sxs-lookup"><span data-stu-id="2b2ab-125">On the **Outlook Mail** tab, click **New**.</span></span>
    
7. <span data-ttu-id="2b2ab-126">В поле **Кому** введите электронный адрес учетной записи User6 в пробной подписке.</span><span class="sxs-lookup"><span data-stu-id="2b2ab-126">In **To**, type the email address of the User6 account of your trial subscription.</span></span>
    
8. <span data-ttu-id="2b2ab-127">В поле темы введите **Тестовое сообщение 2**.</span><span class="sxs-lookup"><span data-stu-id="2b2ab-127">For the subject, type **Test email 2**.</span></span>
    
9. <span data-ttu-id="2b2ab-128">В тексте введите **Обеденное собрание Tailspin**, а затем нажмите кнопку **Отправить**.</span><span class="sxs-lookup"><span data-stu-id="2b2ab-128">In the body, type **Tailspin lunch meeting**, and then click **Send**.</span></span>
    
10. <span data-ttu-id="2b2ab-129">На вкладке **Почта Outlook** нажмите кнопку **Создать**.</span><span class="sxs-lookup"><span data-stu-id="2b2ab-129">On the **Outlook Mail** tab, click **New**.</span></span>
    
11. <span data-ttu-id="2b2ab-130">В поле **Кому** введите электронный адрес учетной записи User6 в пробной подписке.</span><span class="sxs-lookup"><span data-stu-id="2b2ab-130">In **To**, type the email address of the User6 account of your trial subscription.</span></span>
    
12. <span data-ttu-id="2b2ab-131">В поле темы введите **Тестовое сообщение 3**.</span><span class="sxs-lookup"><span data-stu-id="2b2ab-131">For the subject, type **Test email 3**.</span></span>
    
13. <span data-ttu-id="2b2ab-132">В тексте введите **Разногласия по контракту Tailspin**, а затем нажмите кнопку **Отправить**.</span><span class="sxs-lookup"><span data-stu-id="2b2ab-132">In the body, type **Tailspin contract disagreement**, and then click **Send**.</span></span>
    
14. <span data-ttu-id="2b2ab-133">Нажмите значок пользователя в правом верхнем углу страницы, а затем выберите **Выйти**.</span><span class="sxs-lookup"><span data-stu-id="2b2ab-133">Click the user icon in the upper right corner, and then click **Sign out**.</span></span>
    
15. <span data-ttu-id="2b2ab-134">Откройте новую вкладку и войдите на портал Office 365 ([https://www.office.com](https://www.office.com)), указав имя и пароль учетНой записи User6 пробной подписки.</span><span class="sxs-lookup"><span data-stu-id="2b2ab-134">Open a new tab and sign in to the Office 365 portal ([https://www.office.com](https://www.office.com)) with the account name and password of the User6 account of your trial subscription.</span></span>
    
16. <span data-ttu-id="2b2ab-135">На вкладке **портала Office 365** выберите элемент **Почта**.</span><span class="sxs-lookup"><span data-stu-id="2b2ab-135">On the **Office 365 portal** tab, click **Mail**.</span></span>
    
17. <span data-ttu-id="2b2ab-136">На вкладке **почта — User6 — Outlook** убедитесь, что в User6 получены все три сообщения электронной почты из учетной записи электронной почты Outlook.</span><span class="sxs-lookup"><span data-stu-id="2b2ab-136">On the **Mail - User6 - Outlook** tab, check that User6 received all three emails from the Outlook email account.</span></span>
    
18. <span data-ttu-id="2b2ab-137">Переключитесь на **вкладку портала Office 365** для пользователя User6.</span><span class="sxs-lookup"><span data-stu-id="2b2ab-137">Switch back to the **Office 365 portal tab** for User6.</span></span>
    
19. <span data-ttu-id="2b2ab-138">Нажмите значок пользователя в правом верхнем углу страницы, а затем нажмите **Выйти**.</span><span class="sxs-lookup"><span data-stu-id="2b2ab-138">Click the user icon in the upper right corner, and then click **Sign out.**</span></span>
    
<span data-ttu-id="2b2ab-139">В этой процедуре мы создадим два документа Word, которые затем будут анализироваться в рамках дела Advanced eDiscovery.</span><span class="sxs-lookup"><span data-stu-id="2b2ab-139">In this procedure, you create two Word documents that will you will later analyze in an Advanced eDiscovery case.</span></span>
  
1. <span data-ttu-id="2b2ab-140">На странице **Office** нажмите кнопку **Войти** и войдите с помощью учетных данных глобального администратора.</span><span class="sxs-lookup"><span data-stu-id="2b2ab-140">On the **Office** page, click **Sign in,** sign in with the credentials of your global administrator account.</span></span>
    
2. <span data-ttu-id="2b2ab-141">на новой вкладке получите доступ к URL-адресу рабочего сайта SharePoint: **https://** <fictional organization name> **. sharepoint.com/sites/production**</span><span class="sxs-lookup"><span data-stu-id="2b2ab-141">On a new tab, access the URL of your Production SharePoint site: **https://**<fictional organization name> **.sharepoint.com/sites/production**</span></span>
    
3. <span data-ttu-id="2b2ab-142">На вкладке **Семейство рабочих веб-сайтов** найдите раздел **Документы** и выберите элементы **Создать > Документ Word**.</span><span class="sxs-lookup"><span data-stu-id="2b2ab-142">On the **Production site collection** tab, under **Documents**, click **New > Word Document**.</span></span>
    
4. <span data-ttu-id="2b2ab-143">На странице **Word Online** введите **Черновик контракта Tailspin**, подождите, пока в заголовке не появится надпись **Сохранено**, а затем закройте вкладку **Word Online**.</span><span class="sxs-lookup"><span data-stu-id="2b2ab-143">On the **Word Online** page, type **Tailspin draft contract**, wait until it displays **Saved** in the title, and then close the **Word Online** page tab.</span></span>
    
5. <span data-ttu-id="2b2ab-144">На вкладке **Семейство рабочих веб-сайтов** найдите раздел **Документы** и выберите элементы **Создать > Документ Word**.</span><span class="sxs-lookup"><span data-stu-id="2b2ab-144">On the **Production site collection** tab, under **Documents**, click **New > Word Document**.</span></span>
    
6. <span data-ttu-id="2b2ab-145">	На вкладке *\*Word Online** введите *\*Примечания к разногласиям по контракту Tailspin*\*, подождите, пока в заголовке не появится надпись *\*Сохранено*\*, а затем закройте вкладку *\*Word Online*\*.</span><span class="sxs-lookup"><span data-stu-id="2b2ab-145">On the **Word Online** tab, type **Tailspin contract dispute notes**, wait until it displays **Saved** in the title, and then close the **Word Online** tab.</span></span>
    
7. <span data-ttu-id="2b2ab-146">В списке документов на вкладке **Семейство рабочих веб-сайтов** должны отобразиться файлы **Документ** и **Документ1**.</span><span class="sxs-lookup"><span data-stu-id="2b2ab-146">On the **Production site collection** tab, you should see **Document** and **Document1** in the list of documents.</span></span>
    
8. <span data-ttu-id="2b2ab-147">Закройте вкладку **Семейство рабочих веб-сайтов**.</span><span class="sxs-lookup"><span data-stu-id="2b2ab-147">Close the **Production site collection** tab.</span></span>
    
## <a name="phase-3-use-advanced-ediscovery-for-a-legal-dispute"></a><span data-ttu-id="2b2ab-148">Этап 3: использование расширенного обнаружения электронных данных для юридического спора</span><span class="sxs-lookup"><span data-stu-id="2b2ab-148">Phase 3: Use Advanced eDiscovery for a legal dispute</span></span>

<span data-ttu-id="2b2ab-149">К сожалению, разногласия по контракту между нашей организацией и компанией Tailspin Toys достигли уровня судебного разбирательства.</span><span class="sxs-lookup"><span data-stu-id="2b2ab-149">Unfortunately, a contract dispute between your organization and Tailspin Toys has reached the point of legal action.</span></span> <span data-ttu-id="2b2ab-150">В этой процедуре показано, как создать и настроить расширенное дело обнаружения электронных данных для поиска и анализа электронной почты и документов, содержащих текст "контракт Tailspin".</span><span class="sxs-lookup"><span data-stu-id="2b2ab-150">In this procedure, you create and configure an Advanced eDiscovery case to search for and analyze email and documents that contain the text "Tailspin contract".</span></span>
  
<span data-ttu-id="2b2ab-151">Порядок использования Advanced eDiscovery:</span><span class="sxs-lookup"><span data-stu-id="2b2ab-151">The process for using Advanced eDiscovery is the following:</span></span>
  
- <span data-ttu-id="2b2ab-152">Создайте Поиск в центре безопасности &amp; и соответствия требованиям, проанализируйте его результаты, а затем подготовьте результаты для расширенного обнаружения электронных данных.</span><span class="sxs-lookup"><span data-stu-id="2b2ab-152">Create a search in the Security &amp; Compliance center, analyze its results, and then prepare the results for Advanced eDiscovery.</span></span>
    
- <span data-ttu-id="2b2ab-153">Создайте и настройте дело в Advanced eDiscovery и проанализируйте результаты поиска.</span><span class="sxs-lookup"><span data-stu-id="2b2ab-153">Create and configure a case in Advanced eDiscovery and analyze the search results.</span></span>
    
<span data-ttu-id="2b2ab-154">В этой процедуре показано, как создать поиск в центре соответствия &amp; требованиям безопасности для "контракт Tailspin", просмотреть результаты, а затем подготовить результаты для расширенного обнаружения электронных данных.</span><span class="sxs-lookup"><span data-stu-id="2b2ab-154">In this procedure, you create a search in the Security &amp; Compliance center for "Tailspin contract", look at the results, and then prepare the results for Advanced eDiscovery.</span></span>
  
1. <span data-ttu-id="2b2ab-155">На вкладке **портала Office 365** выберите элемент **Администрирование**.</span><span class="sxs-lookup"><span data-stu-id="2b2ab-155">From the **Office 365 portal** tab, click **Admin**.</span></span>
    
2. <span data-ttu-id="2b2ab-156">В левой области навигации на вкладке Центра администрирования выберите элементы **Центры управления > Соответствие требованиям**.</span><span class="sxs-lookup"><span data-stu-id="2b2ab-156">In the left navigation of the Admin center tab, click **Admin centers > Compliance**.</span></span>
    
3. <span data-ttu-id="2b2ab-157">На вкладке **соответствие &amp; требованиям безопасности** щелкните элемент **разрешения**.</span><span class="sxs-lookup"><span data-stu-id="2b2ab-157">On the **Security &amp; Compliance** tab, click **Permissions**.</span></span>
    
4. <span data-ttu-id="2b2ab-158">В списке **Разрешения** дважды щелкните **Управление организацией**.</span><span class="sxs-lookup"><span data-stu-id="2b2ab-158">In the **Permissions** list, double-click **Organization Management**.</span></span>
    
5. <span data-ttu-id="2b2ab-159">В окне **Группы ролей** нажмите значок "плюс" в разделе **Члены**.</span><span class="sxs-lookup"><span data-stu-id="2b2ab-159">In the **Role Group** window, under **Members**, click the plus sign.</span></span>
    
6. <span data-ttu-id="2b2ab-160">В окне **Выбор членов** дважды щелкните имя учетной записи администратора, а затем нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="2b2ab-160">In the **Select Members** window, double-click the name of your administrator account, and then click **OK**.</span></span>
    
7. <span data-ttu-id="2b2ab-161">В окне **Группа ролей** нажмите кнопку **Сохранить**.</span><span class="sxs-lookup"><span data-stu-id="2b2ab-161">In the **Role Group** window, click **Save**.</span></span>
    
8. <span data-ttu-id="2b2ab-162">В списке **Разрешения** дважды щелкните элемент **Руководитель службы обнаружения электронных данных**.</span><span class="sxs-lookup"><span data-stu-id="2b2ab-162">In the **Permissions** list, double-click **eDiscovery Manager**.</span></span>
    
9. <span data-ttu-id="2b2ab-163">В окне **Группа ролей** нажмите значок "плюс" в разделе **Администратор, ответственный за обнаружение электронных данных**.</span><span class="sxs-lookup"><span data-stu-id="2b2ab-163">In the **Role Group** window, under **eDiscovery Administrator**, click the plus icon.</span></span>
    
10. <span data-ttu-id="2b2ab-164">В окне **Выбор членов** дважды щелкните имя учетной записи администратора, а затем нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="2b2ab-164">In the **Select Members** window, double-click the name of your administrator account, and then click **OK**.</span></span>
    
11. <span data-ttu-id="2b2ab-165">В окне **Группа ролей** нажмите кнопку **Сохранить**.</span><span class="sxs-lookup"><span data-stu-id="2b2ab-165">In the **Role Group** window, click **Save**.</span></span>
    
12. <span data-ttu-id="2b2ab-166">В левой панели навигации щелкните **Поиск &amp; _гт_ поиск контента**.</span><span class="sxs-lookup"><span data-stu-id="2b2ab-166">In the left navigation, click **Search &amp; Investigation > Content search**.</span></span>
    
13. <span data-ttu-id="2b2ab-167">Нажмите значок "плюс", чтобы добавить операцию поиска.</span><span class="sxs-lookup"><span data-stu-id="2b2ab-167">Click the plus icon to add a search.</span></span>
    
14. <span data-ttu-id="2b2ab-168">В окне **Новый поиск** введите **Поиск контракта Tailspin** в поле **Имя**.</span><span class="sxs-lookup"><span data-stu-id="2b2ab-168">In the **New search** window, type **Tailspin contract search** in **Name**.</span></span>
    
15. <span data-ttu-id="2b2ab-169">В разделе **Где нужно искать?** нажмите **Поиск везде**, выберите **Exchange**, **SharePoint** и **Общие папки**, а затем нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="2b2ab-169">In **Where do you want us to look?**, click **Search everywhere,** select **Exchange**, **SharePoint**, and **Public Folders**, and then click **Next.**</span></span>
    
16. <span data-ttu-id="2b2ab-170">В разделе **Что вы ищете?** введите **Контракт Tailspin**, затем нажмите кнопку **Искать**.</span><span class="sxs-lookup"><span data-stu-id="2b2ab-170">In **What do you want us to look for?**, type **Tailspin contract**, and then click **Search**.</span></span>
    
17. <span data-ttu-id="2b2ab-171">В списке операций поиска выберите имя **Поиск контракта Tailspin**.</span><span class="sxs-lookup"><span data-stu-id="2b2ab-171">In the list of searches, click the **Tailspin contract search** name.</span></span>
    
18. <span data-ttu-id="2b2ab-172">В области **Поиск контракта Tailspin** нажмите **Предварительный просмотр результатов поиска** в разделе **Результаты**.</span><span class="sxs-lookup"><span data-stu-id="2b2ab-172">In the **Tailspin contract search** pane, click **Preview search results** under **Results**.</span></span> <span data-ttu-id="2b2ab-173">Должно отобразиться окно со списком двух документов на рабочем сайте SharePoint ( **Document** and **document1**), а также **тестировать электронную почту 1** и **тестировать сообщения электронной почты 3** в User6.</span><span class="sxs-lookup"><span data-stu-id="2b2ab-173">You should see a window listing the two documents on the Production SharePoint site ( **Document** and **Document1**) and the **Test email 1** and **Test email 3** emails to User6.</span></span> <span data-ttu-id="2b2ab-174">Закройте окно.</span><span class="sxs-lookup"><span data-stu-id="2b2ab-174">Close the window.</span></span>
    
19. <span data-ttu-id="2b2ab-175">В области **Поиск контента**, в разделе **Анализ результатов с помощью Advanced eDiscovery**, нажмите **Предварительный просмотр результатов для анализа**.</span><span class="sxs-lookup"><span data-stu-id="2b2ab-175">In the **Content search** pane, under **Analyze results with Advanced eDiscovery**, click **Preview results for analysis**.</span></span>
    
20. <span data-ttu-id="2b2ab-176">В окне **Подготовка результатов поиска "Поиск контракта Tailspin"** нажмите **Подготовить** и дождитесь завершения операции.</span><span class="sxs-lookup"><span data-stu-id="2b2ab-176">In the **Prepare the search results for Tailspin contract search** window, click **Prepare** and wait for it to complete.</span></span>
    
<span data-ttu-id="2b2ab-177">В этой процедуре мы создадим дело для Advanced eDiscovery и проанализируем результаты поиска контракта Tailspin.</span><span class="sxs-lookup"><span data-stu-id="2b2ab-177">In this procedure, you create a new case for Advanced eDiscovery and analyze the Tailspin contract search results.</span></span>
  
1. <span data-ttu-id="2b2ab-178">В области навигации слева щелкните **Обнаружение электронных** данных в разделе \*\*Поиск &amp; \*\*в расследовании.</span><span class="sxs-lookup"><span data-stu-id="2b2ab-178">In the left navigation, click **eDiscovery** under **Search &amp; Investigation**.</span></span>
    
2. <span data-ttu-id="2b2ab-179">В области **Обнаружение электронных данных** нажмите **Перейти к Advanced eDiscovery**.</span><span class="sxs-lookup"><span data-stu-id="2b2ab-179">In the **eDiscovery** pane, click **Go to Advanced eDiscovery**.</span></span>
    
3. <span data-ttu-id="2b2ab-180">На вкладке **Advanced eDiscovery** нажмите значок "плюс", чтобы добавить дело.</span><span class="sxs-lookup"><span data-stu-id="2b2ab-180">In the **Advanced eDiscovery** tab, click the plus icon to add a new case.</span></span>
    
4. <span data-ttu-id="2b2ab-p106">	В области *\*Добавление дела** введите *\*Разногласия по контракту Tailspin** в поле *\*Имя*\*, а затем нажмите кнопку *\*ОК*\*. Дождитесь создания дела.</span><span class="sxs-lookup"><span data-stu-id="2b2ab-p106">In the **Add case** pane, type **Tailspin contract dispute** in **Name**, and then click **OK**. Wait for the case to be created.</span></span>
    
5. <span data-ttu-id="2b2ab-183">Дважды щелкните дело **Разногласия по контрактам Tailspin** в списке. </span><span class="sxs-lookup"><span data-stu-id="2b2ab-183">Double click the **Tailspin contract dispute** case in the list.</span></span>
    
6. <span data-ttu-id="2b2ab-184">В списке **контейнер** выберите контейнер поиска по **контракту Tailspin** и нажмите кнопку **обработать**.</span><span class="sxs-lookup"><span data-stu-id="2b2ab-184">In the **Container** list, click the **Tailspin contract search** container, and then click **Process**.</span></span> <span data-ttu-id="2b2ab-185">Дождитесь завершения обработки.</span><span class="sxs-lookup"><span data-stu-id="2b2ab-185">Wait for the processing to complete.</span></span>
    
7. <span data-ttu-id="2b2ab-186">Когда в нижней части окна появится надпись **Обработка: завершена**, выберите элемент **Сводка по обработке** в левой области навигации, чтобы открыть сводку.</span><span class="sxs-lookup"><span data-stu-id="2b2ab-186">When **Process: completed** appears at the bottom of the window, click **Process summary** in the left navigation to see a summary.</span></span>
    
8. <span data-ttu-id="2b2ab-187">В верхней области навигации нажмите **Анализировать**.</span><span class="sxs-lookup"><span data-stu-id="2b2ab-187">In the top navigation, click **Analyze**.</span></span>
    
9. <span data-ttu-id="2b2ab-188">На странице **Настройки**, в разделе **Темы**, введите значение **3** в поле **Максимальное количество тем**.</span><span class="sxs-lookup"><span data-stu-id="2b2ab-188">On the **Setup** page, under **Themes**, type **3** in **Max number of themes**.</span></span>
    
10. <span data-ttu-id="2b2ab-189">Нажмите кнопку **Анализировать** и дождитесь завершения анализа.</span><span class="sxs-lookup"><span data-stu-id="2b2ab-189">Click **Analyze** and wait for the analysis to complete.</span></span> <span data-ttu-id="2b2ab-190">Должна появиться серия круговых диаграмм с анализом целевой аудитории, документов, электронных сообщений и вложений.</span><span class="sxs-lookup"><span data-stu-id="2b2ab-190">You should see a series of pie charts with analysis of the target population, documents, emails, and attachments.</span></span> <span data-ttu-id="2b2ab-191">Дополнительную информацию можно узнать в статье [Просмотр результатов анализа](https://support.office.com/article/Viewing-Analyze-results-5974f3c2-89fe-4c5f-ac7b-57f214437f7e).</span><span class="sxs-lookup"><span data-stu-id="2b2ab-191">For more information, see [Viewing Analyze results](https://support.office.com/article/Viewing-Analyze-results-5974f3c2-89fe-4c5f-ac7b-57f214437f7e).</span></span>
    
<span data-ttu-id="2b2ab-192">Теперь вы можете использовать эту среду для создания контента, операций поиска и дел, а также дальнейших экспериментов с Advanced eDiscovery в Office 365.</span><span class="sxs-lookup"><span data-stu-id="2b2ab-192">You can now use this environment to create new content, new searches and cases, and experiment further with Advanced eDiscovery in Office 365.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="2b2ab-193">См. также</span><span class="sxs-lookup"><span data-stu-id="2b2ab-193">See Also</span></span>

[<span data-ttu-id="2b2ab-194">Руководства по лабораториям тестирования (TLG) для принятия облачных решений</span><span class="sxs-lookup"><span data-stu-id="2b2ab-194">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="2b2ab-195">Базовая конфигурация среды разработки и тестирования</span><span class="sxs-lookup"><span data-stu-id="2b2ab-195">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="2b2ab-196">Среда разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="2b2ab-196">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="2b2ab-197">DirSync для среды разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="2b2ab-197">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="2b2ab-198">Cloud App Security для среды разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="2b2ab-198">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="2b2ab-199">Освоение облака и гибридные решения</span><span class="sxs-lookup"><span data-stu-id="2b2ab-199">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="2b2ab-200">Office 365 Advanced eDiscovery</span><span class="sxs-lookup"><span data-stu-id="2b2ab-200">Office 365 Advanced eDiscovery</span></span>](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4)


