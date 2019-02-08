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
ms.openlocfilehash: c93900e07b8b9adbe0f1120eca77019b9dcc1eda
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2019
ms.locfileid: "25897512"
---
# <a name="advanced-ediscovery-for-your-office-365-devtest-environment"></a><span data-ttu-id="6d9ad-103">Advanced eDiscovery для среды разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="6d9ad-103">Advanced eDiscovery for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="6d9ad-104">**Сводка.** Настройка и демонстрация Office 365 Advanced eDiscovery с образцами данных в среде разработки и тестирования Office 365.</span><span class="sxs-lookup"><span data-stu-id="6d9ad-104">**Summary:** Configure and demonstrate Office 365 Advanced eDiscovery with sample data in your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="6d9ad-p101">Расширенные eDiscovery Office 365 позволяет быстро найти и анализировать информацию по данным, которые хранятся в Office 365, включая электронной почты и документы. Это можно сохранить огромные объемы время и деньги, особенно в ситуациях, судебного разбирательства. Дополнительные сведения см в [Office 365 расширенного обнаружения электронных данных](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4).</span><span class="sxs-lookup"><span data-stu-id="6d9ad-p101">Office 365 Advanced eDiscovery lets you quickly find and analyze relevant information across the data that is stored in Office 365, including email and documents. This can save enormous amounts of time and expense, especially in litigation situations. For more information, see [Office 365 Advanced eDiscovery](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4).</span></span>
  
<span data-ttu-id="6d9ad-108">Выполнив действия, описанные в этой статье, вы создадите небольшой набор данных для урегулирования вымышленных разногласий по контракту и проанализируете его с помощью Advanced eDiscovery.</span><span class="sxs-lookup"><span data-stu-id="6d9ad-108">With the instructions in this article, you create a small set of data for a fictional contract dispute and analyze it with Advanced eDiscovery.</span></span>
  
> [!TIP]
> <span data-ttu-id="6d9ad-109">Щелкните [здесь](http://aka.ms/catlgstack), чтобы просмотреть схему всех статей, относящихся к руководствам по лаборатории тестирования в One Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="6d9ad-109">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-create-your-office-365-devtest-environment"></a><span data-ttu-id="6d9ad-110">Этап 1. Создание среды разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="6d9ad-110">Phase 1: Create your Office 365 dev/test environment</span></span>

<span data-ttu-id="6d9ad-111">Если необходимо проверить расширенной eDiscovery в облегченный путь с минимальным требованиям, следуйте инструкциям в этап 2 и 3 этапа из [Office 365 dev/тестовой среды](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="6d9ad-111">If you just want to test Advanced eDiscovery in a lightweight way with the minimum requirements, follow the instructions in Phase 2 and Phase 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="6d9ad-112">Если вы хотите проверить расширенной eDiscovery в имитации enterprise, следуйте инструкциям в [DirSync для вашей среды разработки или тестирования Office 365](dirsync-for-your-office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="6d9ad-112">If you want to test Advanced eDiscovery in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="6d9ad-p102">Тестирование расширенной обнаружения электронных данных не требуется имитации корпоративной среде, включающая имитации интрасети, подключенных к Интернету и синхронизации каталогов для леса Windows Server AD. Предоставляется здесь как вариант, чтобы тестирования и экспериментов можно выполнить в среде, которая представляет типичное организации.</span><span class="sxs-lookup"><span data-stu-id="6d9ad-p102">Testing Advanced eDiscovery does not require the simulated enterprise environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest. It is provided here as an option so that you can perform testing and experimentation in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-create-example-data-for-advanced-ediscovery"></a><span data-ttu-id="6d9ad-115">Этап 2. Создание образца данных для Advanced eDiscovery</span><span class="sxs-lookup"><span data-stu-id="6d9ad-115">Phase 2: Create example data for Advanced eDiscovery</span></span>

<span data-ttu-id="6d9ad-116">В этой процедуре мы создадим электронные сообщения, которые затем будут анализироваться в рамках дела Advanced eDiscovery.</span><span class="sxs-lookup"><span data-stu-id="6d9ad-116">In this procedure, you create email messages that will you later analyze in an Advanced eDiscovery case.</span></span>
  
1. <span data-ttu-id="6d9ad-117">Откройте Internet Explorer и войдите в систему в [https://outlook.com](https://outlook.com) для учетной записи Outlook, созданной на этапе 2[Office 365 dev/тестовой среды](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="6d9ad-117">Open Internet Explorer and sign in at [https://outlook.com](https://outlook.com) to the Outlook account you created in Phase 2 of[Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
    
  - <span data-ttu-id="6d9ad-118">Если вы используете упрощенную среду разработки и тестирования, запустите частный сеанс Internet Explorer и войдите с локального компьютера.</span><span class="sxs-lookup"><span data-stu-id="6d9ad-118">If you are using the lightweight dev/test environment, open a private session of Internet Explorer and sign in from your local computer.</span></span>
    
  - <span data-ttu-id="6d9ad-119">При использовании среды разработки и тестирования имитации enterprise используйте Azure портала ([https://portal.azure.com](https://portal.azure.com)) для подключения на виртуальную машину CLIENT1 и затем вход из CLIENT1.</span><span class="sxs-lookup"><span data-stu-id="6d9ad-119">If you are using the simulated enterprise dev/test environment, use the Azure portal ([https://portal.azure.com](https://portal.azure.com)) to connect to the CLIENT1 virtual machine, and then sign in from CLIENT1.</span></span>
    
2. <span data-ttu-id="6d9ad-120">На вкладке **Почта Outlook** нажмите кнопку **Создать**.</span><span class="sxs-lookup"><span data-stu-id="6d9ad-120">On the **Outlook Mail** tab, click **New**.</span></span>
    
3. <span data-ttu-id="6d9ad-p103">В поле **для**, введите адрес электронной почты учетной записи User6 пробной подписки ( **user6 @.** <organization name> **. onmicrosoft.com**).</span><span class="sxs-lookup"><span data-stu-id="6d9ad-p103">In **To**, type the email address of the User6 account of your trial subscription ( **user6@.**<organization name> **.onmicrosoft.com**).</span></span>
    
4. <span data-ttu-id="6d9ad-123">В поле темы введите **Тестовое сообщение 1**.</span><span class="sxs-lookup"><span data-stu-id="6d9ad-123">For the subject, type **Test email 1**.</span></span>
    
5. <span data-ttu-id="6d9ad-124">В тексте введите **Черновик контракта Tailspin**, а затем нажмите кнопку **Отправить**.</span><span class="sxs-lookup"><span data-stu-id="6d9ad-124">In the body, type **Tailspin contract draft**, and then click **Send**.</span></span>
    
6. <span data-ttu-id="6d9ad-125">На вкладке **Почта Outlook** нажмите кнопку **Создать**.</span><span class="sxs-lookup"><span data-stu-id="6d9ad-125">On the **Outlook Mail** tab, click **New**.</span></span>
    
7. <span data-ttu-id="6d9ad-126">В поле **Кому** введите электронный адрес учетной записи User6 в пробной подписке.</span><span class="sxs-lookup"><span data-stu-id="6d9ad-126">In **To**, type the email address of the User6 account of your trial subscription.</span></span>
    
8. <span data-ttu-id="6d9ad-127">В поле темы введите **Тестовое сообщение 2**.</span><span class="sxs-lookup"><span data-stu-id="6d9ad-127">For the subject, type **Test email 2**.</span></span>
    
9. <span data-ttu-id="6d9ad-128">В тексте введите **Обеденное собрание Tailspin**, а затем нажмите кнопку **Отправить**.</span><span class="sxs-lookup"><span data-stu-id="6d9ad-128">In the body, type **Tailspin lunch meeting**, and then click **Send**.</span></span>
    
10. <span data-ttu-id="6d9ad-129">На вкладке **Почта Outlook** нажмите кнопку **Создать**.</span><span class="sxs-lookup"><span data-stu-id="6d9ad-129">On the **Outlook Mail** tab, click **New**.</span></span>
    
11. <span data-ttu-id="6d9ad-130">В поле **Кому** введите электронный адрес учетной записи User6 в пробной подписке.</span><span class="sxs-lookup"><span data-stu-id="6d9ad-130">In **To**, type the email address of the User6 account of your trial subscription.</span></span>
    
12. <span data-ttu-id="6d9ad-131">В поле темы введите **Тестовое сообщение 3**.</span><span class="sxs-lookup"><span data-stu-id="6d9ad-131">For the subject, type **Test email 3**.</span></span>
    
13. <span data-ttu-id="6d9ad-132">В тексте введите **Разногласия по контракту Tailspin**, а затем нажмите кнопку **Отправить**.</span><span class="sxs-lookup"><span data-stu-id="6d9ad-132">In the body, type **Tailspin contract disagreement**, and then click **Send**.</span></span>
    
14. <span data-ttu-id="6d9ad-133">Щелкните значок пользователя в правом верхнем углу и выберите команду **Выход**.</span><span class="sxs-lookup"><span data-stu-id="6d9ad-133">Click the user icon in the upper right corner, and then click **Sign out**.</span></span>
    
15. <span data-ttu-id="6d9ad-134">Откройте новую вкладку и войдите в портал Office 365 ([https://portal.office.com](https://portal.office.com)) с именем учетной записи и пароль для учетной записи User6 пробной подписки.</span><span class="sxs-lookup"><span data-stu-id="6d9ad-134">Open a new tab and sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) with the account name and password of the User6 account of your trial subscription.</span></span>
    
16. <span data-ttu-id="6d9ad-135">На вкладке **портала Office 365** выберите элемент **Почта**.</span><span class="sxs-lookup"><span data-stu-id="6d9ad-135">On the **Office 365 portal** tab, click **Mail**.</span></span>
    
17. <span data-ttu-id="6d9ad-136">На вкладке **Outlook почты - User6 -** проверьте, что User6 полученных все три сообщения электронной почты из учетной записи электронной почты Outlook.</span><span class="sxs-lookup"><span data-stu-id="6d9ad-136">On the **Mail - User6 - Outlook** tab, check that User6 received all three emails from the Outlook email account.</span></span>
    
18. <span data-ttu-id="6d9ad-137">Переключитесь на **вкладку портала Office 365** для пользователя User6.</span><span class="sxs-lookup"><span data-stu-id="6d9ad-137">Switch back to the **Office 365 portal tab** for User6.</span></span>
    
19. <span data-ttu-id="6d9ad-138">Нажмите значок пользователя в правом верхнем углу страницы, а затем нажмите **Выйти**.</span><span class="sxs-lookup"><span data-stu-id="6d9ad-138">Click the user icon in the upper right corner, and then click **Sign out.**</span></span>
    
<span data-ttu-id="6d9ad-139">В этой процедуре мы создадим два документа Word, которые затем будут анализироваться в рамках дела Advanced eDiscovery.</span><span class="sxs-lookup"><span data-stu-id="6d9ad-139">In this procedure, you create two Word documents that will you will later analyze in an Advanced eDiscovery case.</span></span>
  
1. <span data-ttu-id="6d9ad-140">На странице **Office** нажмите кнопку **Войти** и войдите с помощью учетных данных глобального администратора.</span><span class="sxs-lookup"><span data-stu-id="6d9ad-140">On the **Office** page, click **Sign in,** sign in with the credentials of your global administrator account.</span></span>
    
2. <span data-ttu-id="6d9ad-141">На новой вкладке, доступ к URL-адрес сайта SharePoint производственной: **https://** <fictional organization name> **.sharepoint.com/sites/production**</span><span class="sxs-lookup"><span data-stu-id="6d9ad-141">On a new tab, access the URL of your Production SharePoint site: **https://**<fictional organization name> **.sharepoint.com/sites/production**</span></span>
    
3. <span data-ttu-id="6d9ad-142">На вкладке **Семейство рабочих веб-сайтов** найдите раздел **Документы** и выберите элементы **Создать > Документ Word**.</span><span class="sxs-lookup"><span data-stu-id="6d9ad-142">On the **Production site collection** tab, under **Documents**, click **New > Word Document**.</span></span>
    
4. <span data-ttu-id="6d9ad-143">На странице **Word Online** введите **Черновик контракта Tailspin**, подождите, пока в заголовке не появится надпись **Сохранено**, а затем закройте вкладку **Word Online**.</span><span class="sxs-lookup"><span data-stu-id="6d9ad-143">On the **Word Online** page, type **Tailspin draft contract**, wait until it displays **Saved** in the title, and then close the **Word Online** page tab.</span></span>
    
5. <span data-ttu-id="6d9ad-144">На вкладке **Семейство рабочих веб-сайтов** найдите раздел **Документы** и выберите элементы **Создать > Документ Word**.</span><span class="sxs-lookup"><span data-stu-id="6d9ad-144">On the **Production site collection** tab, under **Documents**, click **New > Word Document**.</span></span>
    
6. <span data-ttu-id="6d9ad-145">	На вкладке *\*Word Online** введите *\*Примечания к разногласиям по контракту Tailspin*\*, подождите, пока в заголовке не появится надпись *\*Сохранено*\*, а затем закройте вкладку *\*Word Online*\*.</span><span class="sxs-lookup"><span data-stu-id="6d9ad-145">On the **Word Online** tab, type **Tailspin contract dispute notes**, wait until it displays **Saved** in the title, and then close the **Word Online** tab.</span></span>
    
7. <span data-ttu-id="6d9ad-146">В списке документов на вкладке **Семейство рабочих веб-сайтов** должны отобразиться файлы **Документ** и **Документ1**.</span><span class="sxs-lookup"><span data-stu-id="6d9ad-146">On the **Production site collection** tab, you should see **Document** and **Document1** in the list of documents.</span></span>
    
8. <span data-ttu-id="6d9ad-147">Закройте вкладку **Семейство рабочих веб-сайтов**.</span><span class="sxs-lookup"><span data-stu-id="6d9ad-147">Close the **Production site collection** tab.</span></span>
    
## <a name="phase-3-use-advanced-ediscovery-for-a-legal-dispute"></a><span data-ttu-id="6d9ad-148">Этап 3: Использование расширенных обнаружения электронных данных для юридических споров по</span><span class="sxs-lookup"><span data-stu-id="6d9ad-148">Phase 3: Use Advanced eDiscovery for a legal dispute</span></span>

<span data-ttu-id="6d9ad-p104">К сожалению споров по контракт между вашей организацией и Tailspin Toys достиг точки юридических целях. В этой процедуре создайте и настройте вариантом eDiscovery расширенный поиск и анализ электронной почты и документы, содержащие текст «Tailspin контракт».</span><span class="sxs-lookup"><span data-stu-id="6d9ad-p104">Unfortunately, a contract dispute between your organization and Tailspin Toys has reached the point of legal action. In this procedure, you create and configure an Advanced eDiscovery case to search for and analyze email and documents that contain the text "Tailspin contract".</span></span>
  
<span data-ttu-id="6d9ad-151">Порядок использования Advanced eDiscovery:</span><span class="sxs-lookup"><span data-stu-id="6d9ad-151">The process for using Advanced eDiscovery is the following:</span></span>
  
- <span data-ttu-id="6d9ad-152">Создать поиск в системы &amp; центре соответствия требованиям, анализ его результатов, а затем подготовьте результаты расширенной обнаружения электронных данных.</span><span class="sxs-lookup"><span data-stu-id="6d9ad-152">Create a search in the Security &amp; Compliance center, analyze its results, and then prepare the results for Advanced eDiscovery.</span></span>
    
- <span data-ttu-id="6d9ad-153">Создайте и настройте дело в Advanced eDiscovery и проанализируйте результаты поиска.</span><span class="sxs-lookup"><span data-stu-id="6d9ad-153">Create and configure a case in Advanced eDiscovery and analyze the search results.</span></span>
    
<span data-ttu-id="6d9ad-154">В этой процедуре создается поиска в системы &amp; соответствия центра «Tailspin контракт» поиск в окне результатов, а затем подготовьте результаты расширенной обнаружения электронных данных.</span><span class="sxs-lookup"><span data-stu-id="6d9ad-154">In this procedure, you create a search in the Security &amp; Compliance center for "Tailspin contract", look at the results, and then prepare the results for Advanced eDiscovery.</span></span>
  
1. <span data-ttu-id="6d9ad-155">На вкладке **портала Office 365** выберите элемент **Администрирование**.</span><span class="sxs-lookup"><span data-stu-id="6d9ad-155">From the **Office 365 portal** tab, click **Admin**.</span></span>
    
2. <span data-ttu-id="6d9ad-156">В левой области навигации на вкладке Центра администрирования выберите элементы **Центры управления > Соответствие требованиям**.</span><span class="sxs-lookup"><span data-stu-id="6d9ad-156">In the left navigation of the Admin center tab, click **Admin centers > Compliance**.</span></span>
    
3. <span data-ttu-id="6d9ad-157">На **безопасности &amp; соответствия** нажмите кнопку **разрешения**.</span><span class="sxs-lookup"><span data-stu-id="6d9ad-157">On the **Security &amp; Compliance** tab, click **Permissions**.</span></span>
    
4. <span data-ttu-id="6d9ad-158">В списке **Разрешения** дважды щелкните **Управление организацией**.</span><span class="sxs-lookup"><span data-stu-id="6d9ad-158">In the **Permissions** list, double-click **Organization Management**.</span></span>
    
5. <span data-ttu-id="6d9ad-159">В окне **Группы ролей** нажмите значок "плюс" в разделе **Члены**.</span><span class="sxs-lookup"><span data-stu-id="6d9ad-159">In the **Role Group** window, under **Members**, click the plus sign.</span></span>
    
6. <span data-ttu-id="6d9ad-160">В окне **Выбор членов** дважды щелкните имя учетной записи администратора, а затем нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="6d9ad-160">In the **Select Members** window, double-click the name of your administrator account, and then click **OK**.</span></span>
    
7. <span data-ttu-id="6d9ad-161">В окне **Группа ролей** нажмите кнопку **Сохранить**.</span><span class="sxs-lookup"><span data-stu-id="6d9ad-161">In the **Role Group** window, click **Save**.</span></span>
    
8. <span data-ttu-id="6d9ad-162">В списке **Разрешения** дважды щелкните элемент **Руководитель службы обнаружения электронных данных**.</span><span class="sxs-lookup"><span data-stu-id="6d9ad-162">In the **Permissions** list, double-click **eDiscovery Manager**.</span></span>
    
9. <span data-ttu-id="6d9ad-163">В окне **Группа ролей** нажмите значок "плюс" в разделе **Администратор, ответственный за обнаружение электронных данных**.</span><span class="sxs-lookup"><span data-stu-id="6d9ad-163">In the **Role Group** window, under **eDiscovery Administrator**, click the plus icon.</span></span>
    
10. <span data-ttu-id="6d9ad-164">В окне **Выбор членов** дважды щелкните имя учетной записи администратора, а затем нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="6d9ad-164">In the **Select Members** window, double-click the name of your administrator account, and then click **OK**.</span></span>
    
11. <span data-ttu-id="6d9ad-165">В окне **Группа ролей** нажмите кнопку **Сохранить**.</span><span class="sxs-lookup"><span data-stu-id="6d9ad-165">In the **Role Group** window, click **Save**.</span></span>
    
12. <span data-ttu-id="6d9ad-166">На панели навигации слева щелкните **поиска &amp; поиска контента расследования >**.</span><span class="sxs-lookup"><span data-stu-id="6d9ad-166">In the left navigation, click **Search &amp; Investigation > Content search**.</span></span>
    
13. <span data-ttu-id="6d9ad-167">Нажмите значок "плюс", чтобы добавить операцию поиска.</span><span class="sxs-lookup"><span data-stu-id="6d9ad-167">Click the plus icon to add a search.</span></span>
    
14. <span data-ttu-id="6d9ad-168">В окне **Новый поиск** введите **Поиск контракта Tailspin** в поле **Имя**.</span><span class="sxs-lookup"><span data-stu-id="6d9ad-168">In the **New search** window, type **Tailspin contract search** in **Name**.</span></span>
    
15. <span data-ttu-id="6d9ad-169">В разделе **Где нужно искать?** нажмите **Поиск везде**, выберите **Exchange**, **SharePoint** и **Общие папки**, а затем нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="6d9ad-169">In **Where do you want us to look?**, click **Search everywhere,** select **Exchange**, **SharePoint**, and **Public Folders**, and then click **Next.**</span></span>
    
16. <span data-ttu-id="6d9ad-170">В разделе **Что вы ищете?** введите **Контракт Tailspin**, затем нажмите кнопку **Искать**.</span><span class="sxs-lookup"><span data-stu-id="6d9ad-170">In **What do you want us to look for?**, type **Tailspin contract**, and then click **Search**.</span></span>
    
17. <span data-ttu-id="6d9ad-171">В списке операций поиска выберите имя **Поиск контракта Tailspin**.</span><span class="sxs-lookup"><span data-stu-id="6d9ad-171">In the list of searches, click the **Tailspin contract search** name.</span></span>
    
18. <span data-ttu-id="6d9ad-p105">В области **поиска контракт Tailspin** щелкните **Просмотр результатов поиска** в области **результатов**. Вы должны увидеть окна со списком двух документов на сайте SharePoint производственной ( **документов** и **Документ1**) и сообщения **электронной почты Test 1** и **тестирования адрес электронной почты 3** для User6. Закройте окно.</span><span class="sxs-lookup"><span data-stu-id="6d9ad-p105">In the **Tailspin contract search** pane, click **Preview search results** under **Results**. You should see a window listing the two documents on the Production SharePoint site ( **Document** and **Document1**) and the **Test email 1** and **Test email 3** emails to User6. Close the window.</span></span>
    
19. <span data-ttu-id="6d9ad-175">В области **Поиск контента**, в разделе **Анализ результатов с помощью Advanced eDiscovery**, нажмите **Предварительный просмотр результатов для анализа**.</span><span class="sxs-lookup"><span data-stu-id="6d9ad-175">In the **Content search** pane, under **Analyze results with Advanced eDiscovery**, click **Preview results for analysis**.</span></span>
    
20. <span data-ttu-id="6d9ad-176">В окне **Подготовка результатов поиска "Поиск контракта Tailspin"** нажмите **Подготовить** и дождитесь завершения операции.</span><span class="sxs-lookup"><span data-stu-id="6d9ad-176">In the **Prepare the search results for Tailspin contract search** window, click **Prepare** and wait for it to complete.</span></span>
    
<span data-ttu-id="6d9ad-177">В этой процедуре мы создадим дело для Advanced eDiscovery и проанализируем результаты поиска контракта Tailspin.</span><span class="sxs-lookup"><span data-stu-id="6d9ad-177">In this procedure, you create a new case for Advanced eDiscovery and analyze the Tailspin contract search results.</span></span>
  
1. <span data-ttu-id="6d9ad-178">На панели навигации слева щелкните **обнаружения электронных данных** в разделе **поиска &amp; расследования**.</span><span class="sxs-lookup"><span data-stu-id="6d9ad-178">In the left navigation, click **eDiscovery** under **Search &amp; Investigation**.</span></span>
    
2. <span data-ttu-id="6d9ad-179">В области **Обнаружение электронных данных** нажмите **Перейти к Advanced eDiscovery**.</span><span class="sxs-lookup"><span data-stu-id="6d9ad-179">In the **eDiscovery** pane, click **Go to Advanced eDiscovery**.</span></span>
    
3. <span data-ttu-id="6d9ad-180">На вкладке **Advanced eDiscovery** нажмите значок "плюс", чтобы добавить дело.</span><span class="sxs-lookup"><span data-stu-id="6d9ad-180">In the **Advanced eDiscovery** tab, click the plus icon to add a new case.</span></span>
    
4. <span data-ttu-id="6d9ad-p106">	В области *\*Добавление дела** введите *\*Разногласия по контракту Tailspin** в поле *\*Имя*\*, а затем нажмите кнопку *\*ОК*\*. Дождитесь создания дела.</span><span class="sxs-lookup"><span data-stu-id="6d9ad-p106">In the **Add case** pane, type **Tailspin contract dispute** in **Name**, and then click **OK**. Wait for the case to be created.</span></span>
    
5. <span data-ttu-id="6d9ad-183">Дважды щелкните дело **Разногласия по контрактам Tailspin** в списке. </span><span class="sxs-lookup"><span data-stu-id="6d9ad-183">Double click the **Tailspin contract dispute** case in the list.</span></span>
    
6. <span data-ttu-id="6d9ad-p107">В списке **контейнер** щелкните контейнер **Tailspin контракт поиска** и нажмите кнопку **процесс**. Ожидание обработки для выполнения.</span><span class="sxs-lookup"><span data-stu-id="6d9ad-p107">In the **Container** list, click the **Tailspin contract search** container, and then click **Process**. Wait for the processing to complete.</span></span>
    
7. <span data-ttu-id="6d9ad-186">Когда в нижней части окна появится надпись **Обработка: завершена**, выберите элемент **Сводка по обработке** в левой области навигации, чтобы открыть сводку.</span><span class="sxs-lookup"><span data-stu-id="6d9ad-186">When **Process: completed** appears at the bottom of the window, click **Process summary** in the left navigation to see a summary.</span></span>
    
8. <span data-ttu-id="6d9ad-187">В верхней области навигации нажмите **Анализировать**.</span><span class="sxs-lookup"><span data-stu-id="6d9ad-187">In the top navigation, click **Analyze**.</span></span>
    
9. <span data-ttu-id="6d9ad-188">На странице **Настройки**, в разделе **Темы**, введите значение **3** в поле **Максимальное количество тем**.</span><span class="sxs-lookup"><span data-stu-id="6d9ad-188">On the **Setup** page, under **Themes**, type **3** in **Max number of themes**.</span></span>
    
10. <span data-ttu-id="6d9ad-p108">Щелкните **Анализ** и дождитесь выполнения анализа. Вы должны увидеть ряд круговой диаграммы с помощью сведений из целевого заполнения, документы, сообщения электронной почты и вложения. Для получения дополнительных сведений см. [Просмотр анализ результатов](https://support.office.com/article/Viewing-Analyze-results-5974f3c2-89fe-4c5f-ac7b-57f214437f7e).</span><span class="sxs-lookup"><span data-stu-id="6d9ad-p108">Click **Analyze** and wait for the analysis to complete. You should see a series of pie charts with analysis of the target population, documents, emails, and attachments. For more information, see [Viewing Analyze results](https://support.office.com/article/Viewing-Analyze-results-5974f3c2-89fe-4c5f-ac7b-57f214437f7e).</span></span>
    
<span data-ttu-id="6d9ad-192">Теперь вы можете использовать эту среду для создания контента, операций поиска и дел, а также дальнейших экспериментов с Advanced eDiscovery в Office 365.</span><span class="sxs-lookup"><span data-stu-id="6d9ad-192">You can now use this environment to create new content, new searches and cases, and experiment further with Advanced eDiscovery in Office 365.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="6d9ad-193">См. также</span><span class="sxs-lookup"><span data-stu-id="6d9ad-193">See Also</span></span>

[<span data-ttu-id="6d9ad-194">Руководства по созданию сред разработки и тестирования облачных решений</span><span class="sxs-lookup"><span data-stu-id="6d9ad-194">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="6d9ad-195">Базовая конфигурация среды разработки и тестирования</span><span class="sxs-lookup"><span data-stu-id="6d9ad-195">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="6d9ad-196">Среда разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="6d9ad-196">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="6d9ad-197">DirSync для среды разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="6d9ad-197">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="6d9ad-198">Cloud App Security для среды разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="6d9ad-198">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="6d9ad-199">Освоение облака и гибридные решения</span><span class="sxs-lookup"><span data-stu-id="6d9ad-199">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="6d9ad-200">Office 365 Advanced eDiscovery</span><span class="sxs-lookup"><span data-stu-id="6d9ad-200">Office 365 Advanced eDiscovery</span></span>](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4)


