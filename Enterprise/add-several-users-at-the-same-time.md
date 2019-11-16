---
title: Добавление сразу нескольких пользователей в службу Office 365 (справка для администраторов)
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
ms.date: 6/29/2018
audience: Admin
ms.topic: article
f1_keywords:
- O365P_AddUsersCSV
- O365M_AddUsersCSV
- O365E_AddUsersCSV
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOP150
- MOE150
- MED150
- GMA150
- MBS150
- GEA150
- BCS160
ms.assetid: 1f5767ed-e717-4f24-969c-6ea9d412ca88
description: 'Узнайте о том, как добавить в Office 365 для бизнеса сразу нескольких пользователей из электронной таблицы или другого CSV-файла. Посмотрите видео на сайте YouTube, в котором показано, как добавлять учетные записи в Office 365. После добавления учетных записей у каждого пользователя появится почтовый ящик Office 365. '
ms.openlocfilehash: a719b2626eada8abe225a6951af4a2d292667856
ms.sourcegitcommit: 8027254ab4b9ed44a5b0c336f714049859f93f3d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/15/2019
ms.locfileid: "38030733"
---
# <a name="add-several-users-at-the-same-time-to-office-365---admin-help"></a><span data-ttu-id="c9ce0-105">Добавление сразу нескольких пользователей в службу Office 365 (справка для администраторов)</span><span class="sxs-lookup"><span data-stu-id="c9ce0-105">Add several users at the same time to Office 365 - Admin Help</span></span>

<span data-ttu-id="c9ce0-p102">Для входа в систему и доступа к службам Office 365, например электронной почте и приложениям Office, сотрудникам вашей организации необходимы учетные записи. Если в вашей организации много пользователей, вы можете добавить учетные записи сразу для всех с помощью таблицы Excel или файла в формате CSV. [Общие сведения о формате CSV](add-several-users-at-the-same-time.md#__toc316652088)</span><span class="sxs-lookup"><span data-stu-id="c9ce0-p102">Each person on your team needs a user account before they can sign in and access Office 365 services, such as email and Office. If you have a lot of people, you can add their accounts all at once from an Excel spreadsheet or other file saved in CSV format. [Not sure what CSV format is?](add-several-users-at-the-same-time.md#__toc316652088)</span></span>
  
## <a name="add-multiple-users-to-office-365-in-the-microsoft-365-admin-center"></a><span data-ttu-id="c9ce0-109">Добавление нескольких пользователей в Office 365, используя Центр администрирования Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="c9ce0-109">Add multiple users to Office 365 in the Microsoft 365 admin center</span></span>

1. <span data-ttu-id="c9ce0-110">Войдите в Office 365 с рабочей или учебной учетной записью.</span><span class="sxs-lookup"><span data-stu-id="c9ce0-110">Sign in to Office 365 with your work or school account.</span></span> 
    
2. <span data-ttu-id="c9ce0-111">В Центре администрирования выберите **Пользователи** \> **Активные пользователи**.</span><span class="sxs-lookup"><span data-stu-id="c9ce0-111">In the admin center, choose **Users** \> **Active users**.</span></span>
    
    ![В Центре администрирования выберите "Пользователи" > "Активные пользователи".](media/12086d98-a8b4-4c48-89cf-b78ad8058ff1.png)
  
    
3. <span data-ttu-id="c9ce0-113">В области **Импорт нескольких пользователей** вы можете скачать шаблон CSV-файла с образцом сведений о пользователях или без него.</span><span class="sxs-lookup"><span data-stu-id="c9ce0-113">On the **Import multiple users** panel, you can optionally download a sample CSV file with or without sample data filled in.</span></span> 
    
    ![В раскрывающемся списке "Еще" выберите "Импорт нескольких пользователей".](media/77df8a4a-fd00-4fbe-bf1c-d234fc1d5e93.png)
  
    <span data-ttu-id="c9ce0-115">В вашей таблице должны быть **точно такие же заголовки столбцов**, как и в шаблоне ("Имя пользователя", "Имя" и т. д.). Если вы используете шаблон, откройте его в текстовом редакторе, например в Блокноте. Данные в первой строке оставьте без изменений. Добавляйте сведения о пользователях начиная со второй строки.</span><span class="sxs-lookup"><span data-stu-id="c9ce0-115">Your spreadsheet needs to include the **exact same column headings** as the sample one (User Name, First Name, etc...). If you use the template, open it in a text editing tool, like Notepad, and consider leaving all the data in row 1 alone, and only entering data in rows 2 and below.</span></span> 
    
    <span data-ttu-id="c9ce0-116">Для каждого человека в таблице также следует указать имя пользователя (например, ivan@contoso.com) и отображаемое имя (например, Иван Воронков).</span><span class="sxs-lookup"><span data-stu-id="c9ce0-116">Your spreadsheet also needs to include values for the user name (like bob@contoso.com) and a display name (like Bob Kelly) for each user.</span></span> 
    
  ```
  User Name,First Name,Last Name,Display Name,Job Title,Department,Office Number,Office Phone,Mobile Phone,Fax,Address,City,State or Province,ZIP or Postal Code,Country or Region
  chris@contoso.com,Chris,Green,Chris Green,IT Manager,Information Technology,123451,123-555-1211,123-555-6641,123-555-9821,1 Microsoft way,Redmond,Wa,98052,United States
  ben@contoso.com,Ben,Andrews,Ben Andrews,IT Manager,Information Technology,123452,123-555-1212,123-555-6642,123-555-9822,1 Microsoft way,Redmond,Wa,98052,United States
  david@contoso.com,David,Longmuir,David Longmuir,IT Manager,Information Technology,123453,123-555-1213,123-555-6643,123-555-9823,1 Microsoft way,Redmond,Wa,98052,United States
  cynthia@contoso.com,Cynthia,Carey,Cynthia Carey,IT Manager,Information Technology,123454,123-555-1214,123-555-6644,123-555-9824,1 Microsoft way,Redmond,Wa,98052,United States
  melissa@contoso.com,Melissa,MacBeth,Melissa MacBeth,IT Manager,Information Technology,123455,123-555-1215,123-555-6645,123-555-9825,1 Microsoft way,Redmond,Wa,98052,United States
  
  ```

4. <span data-ttu-id="c9ce0-117">Укажите путь к CSV-файлу в специальном поле или нажмите кнопку **Обзор** и выберите его, а затем нажмите кнопку **Проверить**.</span><span class="sxs-lookup"><span data-stu-id="c9ce0-117">Enter a file path into the box, or choose **Browse** to browse to the CSV file location, then choose **Verify**.</span></span>
    
    ![Ваш CSV-файл проверен](media/a43d49db-b2ab-4200-8ddf-0bc846ac6fe5.png)
  
    <span data-ttu-id="c9ce0-p103">Если при добавлении файла возникнут проблемы, их причины будут указаны в области импорта. Вы также можете скачать файл журнала.</span><span class="sxs-lookup"><span data-stu-id="c9ce0-p103">If there are problems with the file, the problem is displayed in the panel. You can also download a log file.</span></span>
    
5. <span data-ttu-id="c9ce0-121">В диалоговом окне **Настройка параметров пользователей** вы можете изменить состояние при входе в систему, а также лицензию продукта, которая будет назначена всем пользователям.</span><span class="sxs-lookup"><span data-stu-id="c9ce0-121">On the **Set user options** dialog you can set the sign-in status and choose the product license that will be assigned to all users.</span></span> 
    
6. <span data-ttu-id="c9ce0-122">В диалоговом окне **просмотра результатов** вы можете отправить их себе или другим пользователям (при этом пароли будут указаны в виде обычного текста), проверить число созданных пользователей и при необходимости приобрести лицензии, чтобы назначить их новым пользователям.</span><span class="sxs-lookup"><span data-stu-id="c9ce0-122">On the **View your result** dialog you can choose to send the results to either yourself or other users (passwords will be in plain text) and you can see how many users were created, and if you need to purchase more licenses to assign to some of the new users.</span></span> 
    
## <a name="watch-the-video"></a><span data-ttu-id="c9ce0-123">Смотреть видео</span><span class="sxs-lookup"><span data-stu-id="c9ce0-123">Watch the video</span></span>
<span data-ttu-id="c9ce0-124"><a name="bk_preview"> </a></span><span class="sxs-lookup"><span data-stu-id="c9ce0-124"><a name="bk_preview"> </a></span></span>

 <span data-ttu-id="c9ce0-125">Посмотрите этот короткий видеоролик, в котором показано, как добавить нескольких пользователей.</span><span class="sxs-lookup"><span data-stu-id="c9ce0-125">Watch a short video that shows you how to bulk add users.</span></span> 
  
> [!VIDEO https://www.microsoft.com/videoplayer/embed/f4e7f161-8ae6-4264-a429-9297b539a8de?autoplay=false]
  
## <a name="next-steps"></a><span data-ttu-id="c9ce0-126">Дальнейшие действия</span><span class="sxs-lookup"><span data-stu-id="c9ce0-126">Next steps</span></span>
<span data-ttu-id="c9ce0-127"><a name="bk_preview"> </a></span><span class="sxs-lookup"><span data-stu-id="c9ce0-127"><a name="bk_preview"> </a></span></span>

- <span data-ttu-id="c9ce0-128">После создания учетных записей пользователям понадобится [скачать, установить или переустановить Office 365 или Office 2016 на компьютерах с Windows или Mac OS](https://support.office.com/article/4414eaaf-0478-48be-9c42-23adc4716658).</span><span class="sxs-lookup"><span data-stu-id="c9ce0-128">Now that these people have accounts, they need to [Download and install or reinstall Office 365 or Office 2016 on a PC or Mac](https://support.office.com/article/4414eaaf-0478-48be-9c42-23adc4716658).</span></span> <span data-ttu-id="c9ce0-129">Каждый участник группы может установить Office 365 на пяти компьютерах с Windows или Mac OS.</span><span class="sxs-lookup"><span data-stu-id="c9ce0-129">Each person on your team can install Office 365 on up to 5 PCs or Macs.</span></span> 
    
- <span data-ttu-id="c9ce0-130">Кроме того, каждый пользователь может [настроить приложения Office и электронную почту на мобильных устройствах](https://support.office.com/article/7dabb6cb-0046-40b6-81fe-767e0b1f014f), используя до пяти планшетов и пяти смартфонов, таких как iPhone, iPad и устройства с Android.</span><span class="sxs-lookup"><span data-stu-id="c9ce0-130">Each person can also [Set up Office apps and email on a mobile device](https://support.office.com/article/7dabb6cb-0046-40b6-81fe-767e0b1f014f) on up to 5 tablets and 5 phones, such as iPhones, iPads, and Android phones and tablets.</span></span> <span data-ttu-id="c9ce0-131">Таким образом, они смогут редактировать файлы Office где угодно.</span><span class="sxs-lookup"><span data-stu-id="c9ce0-131">This way they can edit Office files from anywhere.</span></span> 
    
    <span data-ttu-id="c9ce0-132">Подробный список этапов настройки см. в статье [Настройка Office 365 для бизнеса](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa).</span><span class="sxs-lookup"><span data-stu-id="c9ce0-132">See [Set up Office 365 for business](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa) for an end-to-end list of the setup steps.</span></span> 
    
## <a name="more-information-about-how-to-add-users-to-office-365"></a><span data-ttu-id="c9ce0-133">Дополнительные сведения о добавлении пользователей в Office 365</span><span class="sxs-lookup"><span data-stu-id="c9ce0-133">More information about how to add users to Office 365</span></span>
<span data-ttu-id="c9ce0-134"><a name="bk_preview"> </a></span><span class="sxs-lookup"><span data-stu-id="c9ce0-134"><a name="bk_preview"> </a></span></span>

### <a name="not-sure-what-csv-format-is"></a><span data-ttu-id="c9ce0-135">Общие сведения о формате CSV</span><span class="sxs-lookup"><span data-stu-id="c9ce0-135">Not sure what CSV format is?</span></span>
<span data-ttu-id="c9ce0-136"><a name="__toc316652088"> </a></span><span class="sxs-lookup"><span data-stu-id="c9ce0-136"><a name="__toc316652088"> </a></span></span>

<span data-ttu-id="c9ce0-p106">CSV-файл содержит значения, разделенные запятыми. Такие файлы создаются и редактируются с помощью обычного текстового редактора или программы для работы с таблицами, например Excel.</span><span class="sxs-lookup"><span data-stu-id="c9ce0-p106">A CSV file is a file with comma separated values. You can create or edit a file like this with any text editor or spreadsheet program, such as Excel.</span></span>
  
<span data-ttu-id="c9ce0-p107">Для начала вы можете загрузить и использовать [этот пример электронной таблицы](https://www.microsoft.com/download/details.aspx?id=45485). Помните, что для Office 365 в первой строке должны быть заголовки столбцов, поэтому не заменяйте их другими данными.</span><span class="sxs-lookup"><span data-stu-id="c9ce0-p107">You can download [this sample spreadsheet](https://www.microsoft.com/download/details.aspx?id=45485) as a starting point. Remember that Office 365 requires column headings in the first row so don't replace them with something else.</span></span> 
  
<span data-ttu-id="c9ce0-141">Сохраните файл в формате CSV под другим именем.</span><span class="sxs-lookup"><span data-stu-id="c9ce0-141">Save the file with a new name, and specify CSV format.</span></span>
  
![Как сохранить файл в формате CSV в Excel](media/35a86ebe-63ab-4b4d-9a92-e177de33ebae.png)
  
<span data-ttu-id="c9ce0-p108">При сохранении вы, скорее всего, увидите сообщение о том, что в случае сохранения файла в формате CSV некоторые функции в книге будут потеряны. Это нормально. Нажмите кнопку **Да**, чтобы продолжить.</span><span class="sxs-lookup"><span data-stu-id="c9ce0-p108">When you save the file, you'll probably get a prompt that some features in your workbook will be lost if you save the file in CSV format. This is okay. Click **Yes** to continue.</span></span> 
  
![Изображение приглашения от Excel с вопросом о том, хотите ли вы сохранить файл в формате CSV](media/51032a81-690c-45ef-bfc5-09ea7f790e98.png)
  
### <a name="tips-for-formatting-your-spreadsheet"></a><span data-ttu-id="c9ce0-147">Советы по форматированию электронной таблицы</span><span class="sxs-lookup"><span data-stu-id="c9ce0-147">Tips for formatting your spreadsheet</span></span>
<span data-ttu-id="c9ce0-148"><a name="__toc314595848"> </a></span><span class="sxs-lookup"><span data-stu-id="c9ce0-148"><a name="__toc314595848"> </a></span></span>

- <span data-ttu-id="c9ce0-p109">**Обязательно ли использовать такие же заголовки столбцов, как в примере электронной таблицы?** Да. Первая строка в примере таблицы содержит заголовки столбцов. Эти заголовки являются обязательными. Создайте строку под заголовками для каждого пользователя, которого вы хотите добавить в Office 365. Если вы добавите, измените или удалите какие-либо заголовки столбцов, Office 365 не сможет создать пользователей на основе данных из файла.</span><span class="sxs-lookup"><span data-stu-id="c9ce0-p109">**Do I need the same column headings as in the sample spreadsheet?** Yes. The sample spreadsheet contains column headings in the first row. These headings are required. For each user you want to add to Office 365, create a row under the heading. If you add, change, or delete any of the column headings, Office 365 might not be able to create users from the information in the file.</span></span> 
    
- <span data-ttu-id="c9ce0-p110">**Что делать, если сведения о пользователе неполны?** Имя пользователя и отображаемое имя обязательны: не указав их, вы не сможете добавить учетную запись. Если у вас нет других сведений, таких как факс, вы можете ввести вместо них пробел и запятую, чтобы оставить соответствующее поле пустым.</span><span class="sxs-lookup"><span data-stu-id="c9ce0-p110">**What if I don't have all the information required for each user?** The user name and display name are required, and you cannot add a new user without this information. If you don't have some of the other information, such as the fax, you can use a space plus a comma to indicate that the field should remain blank.</span></span> 
    
- <span data-ttu-id="c9ce0-p111">\*\* How small or large can the spreadsheet be? \*\* The spreadsheet must have at least two rows. One is for the column headings (the user data column label) and one for the user. You cannot have more than 251 rows. If you need to import more than 250 users, you can create more than one spreadsheet.</span><span class="sxs-lookup"><span data-stu-id="c9ce0-p111">\*\* How small or large can the spreadsheet be? \*\* The spreadsheet must have at least two rows. One is for the column headings (the user data column label) and one for the user. You cannot have more than 251 rows. If you need to import more than 250 users, you can create more than one spreadsheet.</span></span> 
    
- <span data-ttu-id="c9ce0-p112">\*\* What languages can I use? \*\* When you create your spreadsheet, you can enter user data column labels in any language or characters, but you must not change the order of the labels, as shown in the sample. You can then make entries into the fields, using any language or characters, and save your file in a Unicode or UTF-8 format.</span><span class="sxs-lookup"><span data-stu-id="c9ce0-p112">\*\* What languages can I use? \*\* When you create your spreadsheet, you can enter user data column labels in any language or characters, but you must not change the order of the labels, as shown in the sample. You can then make entries into the fields, using any language or characters, and save your file in a Unicode or UTF-8 format.</span></span> 
    
- <span data-ttu-id="c9ce0-p113">**Как добавить пользователей из разных стран или регионов?** Создайте отдельную таблицу для каждой области. Вам потребуется выполнить мастер массового добавления для каждой таблицы, указав одинаковое расположение для всех пользователей в текущем файле.</span><span class="sxs-lookup"><span data-stu-id="c9ce0-p113">**What if I'm adding users from different countries or regions?** Create a separate spreadsheet for each area. You'll need to step through the Bulk add users wizard which each spreadsheet, giving a single location of all users included in the file that you're working with.</span></span> 
    
- <span data-ttu-id="c9ce0-p114">**Ограничено ли количество символов?** Максимальное количество знаков для значений в столбцах данных пользователя указано в таблице ниже.</span><span class="sxs-lookup"><span data-stu-id="c9ce0-p114">**Is there a limit to the number of characters I can use?** The following table shows the user data column labels and the maximum character length for each in the sample spreadsheet.</span></span> 
    
|<span data-ttu-id="c9ce0-171">**Столбец данных пользователя**</span><span class="sxs-lookup"><span data-stu-id="c9ce0-171">**User data column label**</span></span>|<span data-ttu-id="c9ce0-172">**Максимальная длина в знаках**</span><span class="sxs-lookup"><span data-stu-id="c9ce0-172">**Maximum character length**</span></span>|
|:-----|:-----|
|<span data-ttu-id="c9ce0-173">Имя пользователя (обязательно)</span><span class="sxs-lookup"><span data-stu-id="c9ce0-173">User Name (Required)</span></span>  <br/> |<span data-ttu-id="c9ce0-p115">79, включая знак @, в формате имя@домен.\<расширение\>. Псевдоним пользователя не может содержать больше 30 знаков, а имя домена  больше 48.</span><span class="sxs-lookup"><span data-stu-id="c9ce0-p115">79 including the at sign (@), in the format name@domain.\<extension\>. The user's alias cannot exceed 30 characters, and the domain name cannot exceed 48 characters.</span></span>  <br/> |
|<span data-ttu-id="c9ce0-176">Имя</span><span class="sxs-lookup"><span data-stu-id="c9ce0-176">First Name</span></span>  <br/> |<span data-ttu-id="c9ce0-177">64</span><span class="sxs-lookup"><span data-stu-id="c9ce0-177">64</span></span>  <br/> |
|<span data-ttu-id="c9ce0-178">Фамилия</span><span class="sxs-lookup"><span data-stu-id="c9ce0-178">Last Name</span></span>  <br/> |<span data-ttu-id="c9ce0-179">64</span><span class="sxs-lookup"><span data-stu-id="c9ce0-179">64</span></span>  <br/> |
|<span data-ttu-id="c9ce0-180">Отображаемое имя (обязательно)</span><span class="sxs-lookup"><span data-stu-id="c9ce0-180">Display Name (required)</span></span>  <br/> |<span data-ttu-id="c9ce0-181">256</span><span class="sxs-lookup"><span data-stu-id="c9ce0-181">256</span></span>  <br/> |
|<span data-ttu-id="c9ce0-182">Должность</span><span class="sxs-lookup"><span data-stu-id="c9ce0-182">Job Title</span></span>  <br/> |<span data-ttu-id="c9ce0-183">64</span><span class="sxs-lookup"><span data-stu-id="c9ce0-183">64</span></span>  <br/> |
|<span data-ttu-id="c9ce0-184">Отдел</span><span class="sxs-lookup"><span data-stu-id="c9ce0-184">Department</span></span>  <br/> |<span data-ttu-id="c9ce0-185">64</span><span class="sxs-lookup"><span data-stu-id="c9ce0-185">64</span></span>  <br/> |
|<span data-ttu-id="c9ce0-186">Номер офиса</span><span class="sxs-lookup"><span data-stu-id="c9ce0-186">Office Number</span></span>  <br/> |<span data-ttu-id="c9ce0-187">128</span><span class="sxs-lookup"><span data-stu-id="c9ce0-187">128</span></span>  <br/> |
|<span data-ttu-id="c9ce0-188">Рабочий телефон</span><span class="sxs-lookup"><span data-stu-id="c9ce0-188">Office Phone</span></span>  <br/> |<span data-ttu-id="c9ce0-189">64</span><span class="sxs-lookup"><span data-stu-id="c9ce0-189">64</span></span>  <br/> |
|<span data-ttu-id="c9ce0-190">Мобильный телефон</span><span class="sxs-lookup"><span data-stu-id="c9ce0-190">Mobile Phone</span></span>  <br/> |<span data-ttu-id="c9ce0-191">64</span><span class="sxs-lookup"><span data-stu-id="c9ce0-191">64</span></span>  <br/> |
|<span data-ttu-id="c9ce0-192">Факс</span><span class="sxs-lookup"><span data-stu-id="c9ce0-192">Fax</span></span>  <br/> |<span data-ttu-id="c9ce0-193">64</span><span class="sxs-lookup"><span data-stu-id="c9ce0-193">64</span></span>  <br/> |
|<span data-ttu-id="c9ce0-194">Адрес</span><span class="sxs-lookup"><span data-stu-id="c9ce0-194">Address</span></span>  <br/> |<span data-ttu-id="c9ce0-195">1023</span><span class="sxs-lookup"><span data-stu-id="c9ce0-195">1023</span></span>  <br/> |
|<span data-ttu-id="c9ce0-196">Город</span><span class="sxs-lookup"><span data-stu-id="c9ce0-196">City</span></span>  <br/> |<span data-ttu-id="c9ce0-197">128</span><span class="sxs-lookup"><span data-stu-id="c9ce0-197">128</span></span>  <br/> |
|<span data-ttu-id="c9ce0-198">Область или край</span><span class="sxs-lookup"><span data-stu-id="c9ce0-198">State or Province</span></span>  <br/> |<span data-ttu-id="c9ce0-199">128</span><span class="sxs-lookup"><span data-stu-id="c9ce0-199">128</span></span>  <br/> |
|<span data-ttu-id="c9ce0-200">Почтовый индекс</span><span class="sxs-lookup"><span data-stu-id="c9ce0-200">ZIP or Postal Code</span></span>  <br/> |<span data-ttu-id="c9ce0-201">40</span><span class="sxs-lookup"><span data-stu-id="c9ce0-201">40</span></span>  <br/> |
|<span data-ttu-id="c9ce0-202">Страна</span><span class="sxs-lookup"><span data-stu-id="c9ce0-202">Country or Region</span></span>  <br/> |<span data-ttu-id="c9ce0-203">128</span><span class="sxs-lookup"><span data-stu-id="c9ce0-203">128</span></span>  <br/> |
   
### <a name="still-having-problems-when-adding-users-to-office-365"></a><span data-ttu-id="c9ce0-204">Все еще испытываете проблемы при добавлении пользователей в Office 365?</span><span class="sxs-lookup"><span data-stu-id="c9ce0-204">Still having problems when adding users to Office 365?</span></span>

- <span data-ttu-id="c9ce0-p116">**Убедитесь, что электронная таблица отформатирована правильно.** Проверьте соответствие заголовков столбцов заголовкам в примере файла. Убедитесь, что соблюдены ограничения на длину полей и что все поля разделены запятыми.</span><span class="sxs-lookup"><span data-stu-id="c9ce0-p116">**Double-check that the spreadsheet is formatted correctly.** Check the column headings to make sure they match the headings in the sample file. Make sure you're following the rules for character lengths and that each field is separated by a comma.</span></span> 
    
- <span data-ttu-id="c9ce0-p117">\*\* If you don't see the new users in Office 365 right away, wait a few minutes. \*\* It can take a little while for changes to go across all the services in Office 365.</span><span class="sxs-lookup"><span data-stu-id="c9ce0-p117">\*\* If you don't see the new users in Office 365 right away, wait a few minutes. \*\* It can take a little while for changes to go across all the services in Office 365.</span></span> 
    
## <a name="add-multiple-users-to-office-365-in-the-old-admin-center"></a><span data-ttu-id="c9ce0-210">Добавление нескольких пользователей в Office 365, используя старый Центр администрирования</span><span class="sxs-lookup"><span data-stu-id="c9ce0-210">Add multiple users to Office 365 in the old admin center</span></span>

1. <span data-ttu-id="c9ce0-211">Скачайте [этот пример электронной таблицы](https://www.microsoft.com/download/details.aspx?id=45485) и откройте его в Excel.</span><span class="sxs-lookup"><span data-stu-id="c9ce0-211">Download [this sample spreadsheet](https://www.microsoft.com/download/details.aspx?id=45485) and open it in Excel.</span></span> 
    
    <span data-ttu-id="c9ce0-212">В вашей таблице должны быть **точно такие же заголовки столбцов**, как и в шаблоне ("Имя пользователя", "Имя" и т. д.). Если вы используете шаблон, то данные в первой строке следует оставить без изменений. Добавляйте сведения о пользователях начиная со второй строки.</span><span class="sxs-lookup"><span data-stu-id="c9ce0-212">Your spreadsheet needs to include the **exact same column headings** as the sample one (User Name, First Name, etc...). If you use the template, consider leaving all the data in row 1 alone, and only entering data in rows 2 and below.</span></span> 
    
    <span data-ttu-id="c9ce0-p118">Для каждого человека в таблице также следует указать имя пользователя (например, ivan@contoso.com) и отображаемое имя (например, Иван Воронков). Если вы хотите оставить остальные поля пустыми, введите в каждое из них пробел с запятой, как показано на рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="c9ce0-p118">Your spreadsheet also needs to include values for the user name (like bob@contoso.com) and a display name (like Bob Kelly) for each user. To leave other fields blank, enter a space plus a comma in the field as shown in the following figure.</span></span> 
    
    ![Пример CSV-файла со строками, отмеченными как пустые](media/9c596ba1-1053-4687-a46c-c9359e9818c9.png)
  
    <span data-ttu-id="c9ce0-p119">Если ваши пользователи работают в разных странах/регионах, вам потребуется создать по таблице для каждой страны/региона. Например, в одной таблице должны быть перечислены все сотрудники из США, а в другой  все, кто работает в Японии. Это связано с тем, что доступность служб Office 365 зависит от региона.</span><span class="sxs-lookup"><span data-stu-id="c9ce0-p119">If you have people working in different countries, you'll need to create one spreadsheet for users in each country. For example, one spreadsheet that lists everyone who works in the US, and another that lists everyone who works in Japan. This is because the availability of Office 365 services varies by region.</span></span> 
    
    <span data-ttu-id="c9ce0-p120">**Совет.** Прежде чем добавлять сразу несколько пользователей в Office 365, рекомендуем попрактиковаться с помощью таблицы, приведенной в качестве примера. Добавьте в нее данные 5-10 пользователей и сохраните файл под новым именем. Выполните действия, описанные в этой инструкции, проверьте результат, а затем удалите созданные учетные записи и повторите все сначала. Таким образом вы поймете, какие именно данные вам нужно внести. Помимо этого, ознакомьтесь с разделом [Советы по форматированию электронной таблицы](add-several-users-at-the-same-time.md#__toc314595848).</span><span class="sxs-lookup"><span data-stu-id="c9ce0-p120">**Tip:** Before you add many users to Office 365, you might want to practice with the sample spreadsheet. For example, edit the sample spreadsheet with data for a few of your users, say 5 or 10, and save the file with a new name. Run through steps described in this procedure, check the results, and then delete the new accounts and start over again. This way you can practice getting all of the data right for your situation. Also check out [Tips for formatting your spreadsheet](add-several-users-at-the-same-time.md#__toc314595848).</span></span>
    
2. <span data-ttu-id="c9ce0-224">Войдите в Office 365 с рабочей или учебной учетной записью.</span><span class="sxs-lookup"><span data-stu-id="c9ce0-224">Sign in to Office 365 with your work or school account.</span></span> 
    
3. <span data-ttu-id="c9ce0-225">Перейдите в Центр администрирования.</span><span class="sxs-lookup"><span data-stu-id="c9ce0-225">Go to the admin center.</span></span>
    
4. <span data-ttu-id="c9ce0-p121">Чтобы пользователи могли работать со службами Office 365, им необходимо назначить лицензии. Прежде чем продолжать, проверьте, достаточно ли у вас лицензий для всех пользователей, которых вы добавили в таблицу. Для этого выберите **Выставление счетов** \> **Подписки**.  Если вам нужно приобрести дополнительные лицензии, выберите \*\* Изменить количество лицензий \*\*. Вы также можете запустить мастер и распределить имеющиеся лицензии, затем приобрести дополнительные и снова запустить его.</span><span class="sxs-lookup"><span data-stu-id="c9ce0-p121">For people to use Office 365 services, they need to be assigned a license. Before continuing, you might want to check that you have enough licenses for everyone listed in your spreadsheet. Choose **Billing** \> **Subscriptions** to see if you have enough. If you need to buy more licenses, choose \*\* Change license quantity \*\*. Or, you can run the wizard and assign the licenses you have, then buy more licenses later and rerun the wizard.</span></span> 
    
5. <span data-ttu-id="c9ce0-p122">Теперь откройте мастер массового добавления пользователей (выберите **Пользователи** \> **Активные пользователи**). Выберите ![Значок для добавления группы пользователей в Office 365](media/3481ffea-d552-4a7f-9a3b-014504e69746.png), как показано на приведенном ниже рисунке.</span><span class="sxs-lookup"><span data-stu-id="c9ce0-p122">Now go to the Bulk add users wizard: choose **Users** \> **Active Users**. Choose ![The icon for adding many users to Office 365](media/3481ffea-d552-4a7f-9a3b-014504e69746.png) as shown in the following figure.</span></span> 
    
    ![Изображение раздела "Пользователи" в Центре администрирования](media/2cd5ff86-9c0b-438e-9bb9-13b12a2675de.png)
  
    <span data-ttu-id="c9ce0-234">Откроется мастер массового добавления пользователей с инструкциями по добавлению группы сотрудников в Office 365.</span><span class="sxs-lookup"><span data-stu-id="c9ce0-234">The Bulk add users wizard appears and steps you through adding a group of users to Office 365.</span></span> 
    
6. <span data-ttu-id="c9ce0-235">В действии 1 "Выбор CSV-файла" укажите свою таблицу, как показано на приведенном ниже рисунке.</span><span class="sxs-lookup"><span data-stu-id="c9ce0-235">In Step 1 - Select a CSV file, specify your own spreadsheet as shown in the following figure.</span></span>
    
    ![Мастер массового добавления пользователей. Шаг 1: выбор CSV-файла](media/aeb837ed-1f86-427d-b038-c643c383829c.png)
  
7. <span data-ttu-id="c9ce0-237">В действии 2 "Проверка" мастер сообщает вам, правильно ли отформатировано содержимое таблицы.</span><span class="sxs-lookup"><span data-stu-id="c9ce0-237">In Step 2 - Verification, the wizard tells you whether the content in the spreadsheet is formatted correctly.</span></span>
    
    ![Мастер массового добавления пользователей. Шаг 2: проверка](media/3fd3cd2c-44d4-4593-b02c-b87c176affb3.png)
  
8. <span data-ttu-id="c9ce0-p123">В действии 3 "Параметры" выберите **Разрешено**, чтобы указанные в таблице пользователи могли работать с Office 365. Также выберите страну, в которой эти пользователи будут работать с Office 365. Помните, что если некоторые сотрудники вашей организации будут использовать Office 365 в другой стране, то вам потребуется создать для них отдельную таблицу и еще раз выполнить мастер массового добавления.</span><span class="sxs-lookup"><span data-stu-id="c9ce0-p123">In Step 3 - Settings, choose **Allowed** so that the people listed in your spreadsheet will be able to use Office 365. Also choose the country in which these people will use Office 365. Remember if some people in your organization are going to use Office 365 in a different country, create a separate spreadsheet with their names and run the Bulk add users wizard again to add them.</span></span> 
    
    ![Мастер массового добавления пользователей. Шаг 3: параметры](media/ff12ad34-5d8b-4e89-a02f-d827a94095b3.png)
  
9. <span data-ttu-id="c9ce0-243">На странице назначения лицензий указано количество доступных лицензий.</span><span class="sxs-lookup"><span data-stu-id="c9ce0-243">The assign licenses page tells you how many licenses are available.</span></span> 
    
    ![Мастер массового добавления пользователей. Шаг 4: лицензии](media/161ea34c-c67e-43be-962f-029f5426ff1b.png)
  
    <span data-ttu-id="c9ce0-245">Вы можете выбрать **Приобретение дополнительных лицензий**, но при этом мастер прекратит работу и вы перейдете в раздел **Выставление счетов** Центра администрирования Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="c9ce0-245">You can choose **Buy more licenses**, but you'll leave the Bulk add users wizard and go to **Billing** in the Microsoft 365 admin center.</span></span> <span data-ttu-id="c9ce0-246">После покупки дополнительных лицензий подождите несколько минут, чтобы мы успели обработать ваш заказ, и снова запустите мастер массового добавления пользователей.</span><span class="sxs-lookup"><span data-stu-id="c9ce0-246">After buying more licenses, you'll have to wait a few minutes for the order to be processed and then start the Bulk add users wizard from the beginning.</span></span> 
    
    <span data-ttu-id="c9ce0-247">Без покупки дополнительных лицензий вы не сможете создать учетные записи для всех пользователей, перечисленных в таблице.</span><span class="sxs-lookup"><span data-stu-id="c9ce0-247">If you don't buy more licenses, accounts won't be created for everyone listed in your spreadsheet.</span></span> 
    
    <span data-ttu-id="c9ce0-248">В этом примере мы не приобретаем дополнительные лицензии, а продолжаем работу в мастере массового добавления.</span><span class="sxs-lookup"><span data-stu-id="c9ce0-248">In this example, we don't buy any more licenses and continue with the Bulk add users wizard.</span></span>
    
10. <span data-ttu-id="c9ce0-249">В действии 5 "Отправка результатов" введите адреса электронной почты лиц, которым вы хотите отправить список  *всех*  имен и временных паролей Office 365 пользователей из таблицы.</span><span class="sxs-lookup"><span data-stu-id="c9ce0-249">In Step 5 - Send Results, type the email addresses of the people who you want to get an email that lists  *all*  of the Office 365 user names and temporary passwords for the people in the spreadsheet.</span></span> 
    
    ![Мастер массового добавления пользователей. Шаг 5: отправка результатов](media/5beeb825-4ba7-4ae0-bfb5-a1f8a785ebdb.png)
  
    <span data-ttu-id="c9ce0-p125">Приведенное ниже сообщение электронной почты отправляется по всем адресам, указанным в действии 5 ("Отправка результатов"). Оно содержит сведения о том, какие учетные записи были созданы, а также об ошибках в процессе их добавления. Обратите внимание, что для некоторых пользователей учетные записи не созданы, поскольку им не хватило лицензий.</span><span class="sxs-lookup"><span data-stu-id="c9ce0-p125">The following email is sent to all the email addresses you specified in Step 5 - Send results. This email indicates which accounts were created. Notice that accounts weren't created for some people because there weren't enough licenses.</span></span> 
    
    ![Образец сообщения электронной почты с учетными данными](media/0a40c612-2078-4b5b-813e-f99bc53635a6.png)
  
    <span data-ttu-id="c9ce0-p126">Вы сможете приобрести дополнительные лицензии позже и еще раз запустить мастер массового добавления пользователей с той же таблицей. Мастер пропускает пользователей, у которых уже есть учетные записи. Строка "повторяющееся имя пользователя" в финальном отчете указывает на наличие учетной записи с теми же данными.</span><span class="sxs-lookup"><span data-stu-id="c9ce0-p126">You can buy more licenses later and rerun the Bulk add users wizard with the same spreadsheet. The wizard skips over the users that already have accounts; on the results report, it will say "duplicate user name" to indicate someone with that information already has an account.</span></span>
    
11. <span data-ttu-id="c9ce0-257">На последней странице мастера массового добавления перечислены имена пользователей и временные пароли, как показано на приведенном ниже рисунке.</span><span class="sxs-lookup"><span data-stu-id="c9ce0-257">The final page in the Bulk add users wizard lists the user names and temporary passwords, as shown in the following figure.</span></span>
    
    ![Мастер массового добавления пользователей. Шаг 6: результаты](media/0cd43832-071b-4b33-b57a-5d07959985ad.png)
  
12. <span data-ttu-id="c9ce0-p127">После того как вы добавите лицензии пользователей в Office 365, им нужно предоставить данные их учетных записей Office 365. Для этого следуйте стандартной процедуре передачи паролей.</span><span class="sxs-lookup"><span data-stu-id="c9ce0-p127">After you've added users to Office 365, you need to tell them about their Office 365 account information. Use your normal process for communicating new passwords.</span></span>
    

