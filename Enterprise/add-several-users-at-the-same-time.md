---
title: Добавление в Office 365 сразу нескольких пользователей — справка для администраторов
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
ms.date: 6/29/2018
ms.audience: Admin
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
description: 'Узнайте, как добавить несколько пользователей в Office 365 для бизнеса из списка в электронной таблице или других CSV файла в формате. Видео на сайте YouTube, объясняется, как добавить учетные записи в Office 365. В конце этого процесса каждого пользователя с использованием учетной записи будут иметь почтовый ящик Office 365. '
ms.openlocfilehash: 1f91821ee552b59201ca01bdbce7edc0406929d6
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542353"
---
# <a name="add-several-users-at-the-same-time-to-office-365---admin-help"></a><span data-ttu-id="8d1a2-105">Добавление в Office 365 сразу нескольких пользователей — справка для администраторов</span><span class="sxs-lookup"><span data-stu-id="8d1a2-105">Add several users at the same time to Office 365 - Admin Help</span></span>

<span data-ttu-id="8d1a2-p102">Каждый пользователь в группе должен учетной записи пользователя перед их может выполнять вход и доступ к службам Office 365, например электронной почты и Office. Если у вас есть много людей, можно добавить свои учетные записи и одновременное из таблицы Excel или других файл, сохраненный в формате CSV. [Не знаете, какой формат CSV?](add-several-users-at-the-same-time.md#__toc316652088)</span><span class="sxs-lookup"><span data-stu-id="8d1a2-p102">Each person on your team needs a user account before they can sign in and access Office 365 services, such as email and Office. If you have a lot of people, you can add their accounts all at once from an Excel spreadsheet or other file saved in CSV format. [Not sure what CSV format is?](add-several-users-at-the-same-time.md#__toc316652088)</span></span>
  
## <a name="add-multiple-users-to-office-365-in-the-office-365-admin-center"></a><span data-ttu-id="8d1a2-109">Добавление нескольких пользователей в Office 365 в центре администрирования Office 365</span><span class="sxs-lookup"><span data-stu-id="8d1a2-109">Add multiple users to Office 365 in the Office 365 admin center</span></span>

1. <span data-ttu-id="8d1a2-110">Войдите в Office 365 с помощью рабочей или учебной учетной записи.</span><span class="sxs-lookup"><span data-stu-id="8d1a2-110">Sign in to Office 365 with your work or school account.</span></span> 
    
2. <span data-ttu-id="8d1a2-111">В центре администрирования Office 365 выберите **пользователей** \> **Активные пользователи**.</span><span class="sxs-lookup"><span data-stu-id="8d1a2-111">In the Office 365 admin center, choose **Users** \> **Active users**.</span></span>
    
    ![В центре администрирования выберите пользователи и затем активных пользователей](media/12086d98-a8b4-4c48-89cf-b78ad8058ff1.png)
  
3. <span data-ttu-id="8d1a2-113">В **более** раскрывающегося списка выберите **Импорт нескольких пользователей**.</span><span class="sxs-lookup"><span data-stu-id="8d1a2-113">In the **More** drop-down, choose **Import multiple users**.</span></span>
    
4. <span data-ttu-id="8d1a2-114">На панели **импорта нескольких пользователей** при необходимости можно загрузить пример CSV-файла или без заполнения образца данных.</span><span class="sxs-lookup"><span data-stu-id="8d1a2-114">On the **Import multiple users** panel, you can optionally download a sample CSV file with or without sample data filled in.</span></span> 
    
    ![В более раскрывающегося списка, выберите Импорт нескольким пользователям](media/77df8a4a-fd00-4fbe-bf1c-d234fc1d5e93.png)
  
    <span data-ttu-id="8d1a2-116">Электронной таблицы должна включать **точное же заголовки столбцов** как пример одно (имя пользователя, имя, и т.д...). При использовании шаблона, откройте его в средстве редактирования текста, например Блокнот и учитывайте покидать сам по себе он все данные в строке 1 и только ввод данных в строках 2 и ниже.</span><span class="sxs-lookup"><span data-stu-id="8d1a2-116">Your spreadsheet needs to include the **exact same column headings** as the sample one (User Name, First Name, etc...). If you use the template, open it in a text editing tool, like Notepad, and consider leaving all the data in row 1 alone, and only entering data in rows 2 and below.</span></span> 
    
    <span data-ttu-id="8d1a2-117">Электронная таблица также должна включать значения для имени пользователя (например, bob@contoso.com) и отображаемое имя (например, Владимир Егоров) для каждого пользователя.</span><span class="sxs-lookup"><span data-stu-id="8d1a2-117">Your spreadsheet also needs to include values for the user name (like bob@contoso.com) and a display name (like Bob Kelly) for each user.</span></span> 
    
  ```
  User Name,First Name,Last Name,Display Name,Job Title,Department,Office Number,Office Phone,Mobile Phone,Fax,Address,City,State or Province,ZIP or Postal Code,Country or Region
  chris@contoso.com,Chris,Green,Chris Green,IT Manager,Information Technology,123451,123-555-1211,123-555-6641,123-555-9821,1 Microsoft way,Redmond,Wa,98052,United States
  ben@contoso.com,Ben,Andrews,Ben Andrews,IT Manager,Information Technology,123452,123-555-1212,123-555-6642,123-555-9822,1 Microsoft way,Redmond,Wa,98052,United States
  david@contoso.com,David,Longmuir,David Longmuir,IT Manager,Information Technology,123453,123-555-1213,123-555-6643,123-555-9823,1 Microsoft way,Redmond,Wa,98052,United States
  cynthia@contoso.com,Cynthia,Carey,Cynthia Carey,IT Manager,Information Technology,123454,123-555-1214,123-555-6644,123-555-9824,1 Microsoft way,Redmond,Wa,98052,United States
  melissa@contoso.com,Melissa,MacBeth,Melissa MacBeth,IT Manager,Information Technology,123455,123-555-1215,123-555-6645,123-555-9825,1 Microsoft way,Redmond,Wa,98052,United States
  
  ```

5. <span data-ttu-id="8d1a2-118">Введите в поле путь к файлу или нажмите кнопку **Обзор** , перейдите к месту расположения файла CSV и нажмите кнопку **Проверить**.</span><span class="sxs-lookup"><span data-stu-id="8d1a2-118">Enter a file path into the box, or choose **Browse** to browse to the CSV file location, then choose **Verify**.</span></span>
    
    ![Проверить CSV-файла](media/a43d49db-b2ab-4200-8ddf-0bc846ac6fe5.png)
  
    <span data-ttu-id="8d1a2-p103">При возникновении проблем с файлом, проблема отображается на панели. Кроме того, можно загрузить файл журнала.</span><span class="sxs-lookup"><span data-stu-id="8d1a2-p103">If there are problems with the file, the problem is displayed in the panel. You can also download a log file.</span></span>
    
6. <span data-ttu-id="8d1a2-122">В диалоговом окне **Параметры пользователя** можно установить состояние входа и выбрать лицензии на продукт, который будет назначен всем пользователям.</span><span class="sxs-lookup"><span data-stu-id="8d1a2-122">On the **Set user options** dialog you can set the sign-in status and choose the product license that will be assigned to all users.</span></span> 
    
7. <span data-ttu-id="8d1a2-123">В диалоговом окне **Просмотр результатов** можно отправить результаты в себя или другим пользователям (паролей будет находиться в обычный текст) и могут видеть, сколько пользователей были созданы, и если вам потребуется приобрести дополнительные лицензии для назначения новых пользователей.</span><span class="sxs-lookup"><span data-stu-id="8d1a2-123">On the **View your result** dialog you can choose to send the results to either yourself or other users (passwords will be in plain text) and you can see how many users were created, and if you need to purchase more licenses to assign to some of the new users.</span></span> 
    
## <a name="watch-the-video"></a><span data-ttu-id="8d1a2-124">Просмотр видео</span><span class="sxs-lookup"><span data-stu-id="8d1a2-124">Watch the video</span></span>
<span data-ttu-id="8d1a2-125"><a name="bk_preview"> </a></span><span class="sxs-lookup"><span data-stu-id="8d1a2-125"></span></span>

 <span data-ttu-id="8d1a2-126">Посмотрите короткий видеоролик, в котором показано, как выполнить массовое Добавление пользователей.</span><span class="sxs-lookup"><span data-stu-id="8d1a2-126">Watch a short video that shows you how to bulk add users.</span></span> 
  
> [!VIDEO https://www.microsoft.com/videoplayer/embed/f4e7f161-8ae6-4264-a429-9297b539a8de?autoplay=false]
  
## <a name="next-steps"></a><span data-ttu-id="8d1a2-127">Дальнейшие действия</span><span class="sxs-lookup"><span data-stu-id="8d1a2-127">Next steps</span></span>
<span data-ttu-id="8d1a2-128"><a name="bk_preview"> </a></span><span class="sxs-lookup"><span data-stu-id="8d1a2-128"></span></span>

- <span data-ttu-id="8d1a2-p104">Теперь, когда эти пользователи имеют учетные записи, они должны [загрузить и установить или повторно установить Office 365 или 2016 Office на ПК или Mac](https://support.office.com/article/4414eaaf-0478-48be-9c42-23adc4716658). Каждому сотруднику группы можно установить Office 365 на до 5 компьютеров или компьютеров Макинтош.</span><span class="sxs-lookup"><span data-stu-id="8d1a2-p104">Now that these people have accounts, they need to [Download and install or reinstall Office 365 or Office 2016 on a PC or Mac](https://support.office.com/article/4414eaaf-0478-48be-9c42-23adc4716658). Each person on your team can install Office 365 on up to 5 PCs or Macs.</span></span> 
    
- <span data-ttu-id="8d1a2-p105">Человек, можно также [Настройка приложений Office и адрес электронной почты на мобильном устройстве](https://support.office.com/article/7dabb6cb-0046-40b6-81fe-767e0b1f014f) на планшетах до 5 и 5 телефоны, например, iPhone, iPad и Android телефоны и планшетные ПК. Таким образом, они могут изменять файлы Office в любом месте.</span><span class="sxs-lookup"><span data-stu-id="8d1a2-p105">Each person can also [Set up Office apps and email on a mobile device](https://support.office.com/article/7dabb6cb-0046-40b6-81fe-767e0b1f014f) on up to 5 tablets and 5 phones, such as iPhones, iPads, and Android phones and tablets. This way they can edit Office files from anywhere.</span></span> 
    
    <span data-ttu-id="8d1a2-133">В разделе [Настройка Office 365 для бизнеса](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa) начала до конца списка этапов настройки.</span><span class="sxs-lookup"><span data-stu-id="8d1a2-133">See [Set up Office 365 for business](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa) for an end-to-end list of the setup steps.</span></span> 
    
## <a name="more-information-about-how-to-add-users-to-office-365"></a><span data-ttu-id="8d1a2-134">Дополнительные сведения о том, как добавить пользователей в Office 365</span><span class="sxs-lookup"><span data-stu-id="8d1a2-134">More information about how to add users to Office 365</span></span>
<span data-ttu-id="8d1a2-135"><a name="bk_preview"> </a></span><span class="sxs-lookup"><span data-stu-id="8d1a2-135"></span></span>

### <a name="not-sure-what-csv-format-is"></a><span data-ttu-id="8d1a2-136">Не знаете, какой формат CSV?</span><span class="sxs-lookup"><span data-stu-id="8d1a2-136">Not sure what CSV format is?</span></span>
<span data-ttu-id="8d1a2-137"><a name="__toc316652088"> </a></span><span class="sxs-lookup"><span data-stu-id="8d1a2-137"></span></span>

<span data-ttu-id="8d1a2-p106">В CSV-файл представляет собой файл с разделителями-запятыми значения. Можно создавать и редактировать файла следующим образом с помощью любого текстового редактора или программы электронной таблицы, например Microsoft Excel.</span><span class="sxs-lookup"><span data-stu-id="8d1a2-p106">A CSV file is a file with comma separated values. You can create or edit a file like this with any text editor or spreadsheet program, such as Excel.</span></span>
  
<span data-ttu-id="8d1a2-p107">[Этот пример электронной таблицы](https://www.microsoft.com/en-us/download/details.aspx?id=45485) можно загрузить в качестве отправной точки. Имейте в виду, что Office 365 требует заголовков столбцов в первой строке так не их замены на другой.</span><span class="sxs-lookup"><span data-stu-id="8d1a2-p107">You can download [this sample spreadsheet](https://www.microsoft.com/en-us/download/details.aspx?id=45485) as a starting point. Remember that Office 365 requires column headings in the first row so don't replace them with something else.</span></span> 
  
<span data-ttu-id="8d1a2-142">Сохраните файл под новым именем и укажите формат CSV.</span><span class="sxs-lookup"><span data-stu-id="8d1a2-142">Save the file with a new name, and specify CSV format.</span></span>
  
![Изображение сохранение файла в Excel в формате CSV](media/35a86ebe-63ab-4b4d-9a92-e177de33ebae.png)
  
<span data-ttu-id="8d1a2-p108">При сохранении файла может появиться запрос, что некоторые функции, содержащиеся в книге, будут потеряны при сохранении файла в формате CSV. Это нормально. Нажмите кнопку **Да,** чтобы продолжить.</span><span class="sxs-lookup"><span data-stu-id="8d1a2-p108">When you save the file, you'll probably get a prompt that some features in your workbook will be lost if you save the file in CSV format. This is okay. Click **Yes** to continue.</span></span> 
  
![Изображение приглашения может получить из Excel предложение сделать сохраните файл как формат CSV](media/51032a81-690c-45ef-bfc5-09ea7f790e98.png)
  
### <a name="tips-for-formatting-your-spreadsheet"></a><span data-ttu-id="8d1a2-148">Советы по форматированию электронной таблицы</span><span class="sxs-lookup"><span data-stu-id="8d1a2-148">Tips for formatting your spreadsheet</span></span>
<span data-ttu-id="8d1a2-149"><a name="__toc314595848"> </a></span><span class="sxs-lookup"><span data-stu-id="8d1a2-149"></span></span>

- <span data-ttu-id="8d1a2-p109">**Требуются же заголовки столбцов, как и в электронную таблицу?** Да. Пример электронной таблицы содержит заголовки столбцов в первой строке. Заголовки являются обязательными. Для каждого пользователя, которые необходимо добавить в Office 365 создайте строку под заголовком. Если добавление, изменение или удаление всех заголовков столбцов, Office 365 не могут для создания пользователей из файла.</span><span class="sxs-lookup"><span data-stu-id="8d1a2-p109">**Do I need the same column headings as in the sample spreadsheet?** Yes. The sample spreadsheet contains column headings in the first row. These headings are required. For each user you want to add to Office 365, create a row under the heading. If you add, change, or delete any of the column headings, Office 365 might not be able to create users from the information in the file.</span></span> 
    
- <span data-ttu-id="8d1a2-p110">**Что делать, если я не все сведения, необходимые для каждого пользователя?** Имя пользователя и отображаемое имя являются обязательными и не удается добавить нового пользователя без эти сведения. У вас нет некоторые другие сведения, такие как службы факсов, можно использовать пробел, а также их запятыми для указания, что поля должен быть пустым.</span><span class="sxs-lookup"><span data-stu-id="8d1a2-p110">**What if I don't have all the information required for each user?** The user name and display name are required, and you cannot add a new user without this information. If you don't have some of the other information, such as the fax, you can use a space plus a comma to indicate that the field should remain blank.</span></span> 
    
- <span data-ttu-id="8d1a2-p111">** Как или мелких можно электронной таблицы Электронной таблицы должны иметь по крайней мере двух строк. Один — для заголовков столбцов (метки столбца данных пользователя), а другая — для пользователя. Не может содержать более 251 строк. Если требуется импортировать более чем 250 пользователей, можно создать более одного листа.</span><span class="sxs-lookup"><span data-stu-id="8d1a2-p111">** How small or large can the spreadsheet be? ** The spreadsheet must have at least two rows. One is for the column headings (the user data column label) and one for the user. You cannot have more than 251 rows. If you need to import more than 250 users, you can create more than one spreadsheet.</span></span> 
    
- <span data-ttu-id="8d1a2-p112">** Какие языки можно использовать? ** При создании электронной таблице заголовки столбцов данных пользователя можно ввести в любой язык или символов, но нельзя изменять порядок метки, как показано в примере. Затем можно сделать записи в поля, с помощью любого языка или символов и сохраните файл в формате Юникод или UTF-8.</span><span class="sxs-lookup"><span data-stu-id="8d1a2-p112">** What languages can I use? ** When you create your spreadsheet, you can enter user data column labels in any language or characters, but you must not change the order of the labels, as shown in the sample. You can then make entries into the fields, using any language or characters, and save your file in a Unicode or UTF-8 format.</span></span> 
    
- <span data-ttu-id="8d1a2-p113">**Что делать, если добавляемых пользователей из разных стран или регионов?** Создайте отдельные электронную таблицу для каждой области. Вам потребуется пошаговое выполнение большую мастера добавления пользователей какие каждого листа, давая в одном месте всем пользователям, включенным в файле, с которыми работает пользователь.</span><span class="sxs-lookup"><span data-stu-id="8d1a2-p113">**What if I'm adding users from different countries or regions?** Create a separate spreadsheet for each area. You'll need to step through the Bulk add users wizard which each spreadsheet, giving a single location of all users included in the file that you're working with.</span></span> 
    
- <span data-ttu-id="8d1a2-p114">**Существует ограничение на число знаков, я могу использовать?** Следующей таблице показаны метки столбец данных пользователей и максимальное количество символов для каждого из них в электронную таблицу.</span><span class="sxs-lookup"><span data-stu-id="8d1a2-p114">**Is there a limit to the number of characters I can use?** The following table shows the user data column labels and the maximum character length for each in the sample spreadsheet.</span></span> 
    
|<span data-ttu-id="8d1a2-172">**Названия столбцов данных пользователя**</span><span class="sxs-lookup"><span data-stu-id="8d1a2-172">**User data column label**</span></span>|<span data-ttu-id="8d1a2-173">**Максимальное количество символов**</span><span class="sxs-lookup"><span data-stu-id="8d1a2-173">**Maximum character length**</span></span>|
|:-----|:-----|
|<span data-ttu-id="8d1a2-174">Имя пользователя (требуется)</span><span class="sxs-lookup"><span data-stu-id="8d1a2-174">User Name (Required)</span></span>  <br/> |<span data-ttu-id="8d1a2-p115">включая 79 знака (@), в формате name@domain. \<расширение\>. Псевдоним пользователя не может превышать 30 символов, а имя домена не должна превышать 48 символов.</span><span class="sxs-lookup"><span data-stu-id="8d1a2-p115">79 including the at sign (@), in the format name@domain.\<extension\>. The user's alias cannot exceed 30 characters, and the domain name cannot exceed 48 characters.</span></span>  <br/> |
|<span data-ttu-id="8d1a2-177">имя;</span><span class="sxs-lookup"><span data-stu-id="8d1a2-177">First Name</span></span>  <br/> |<span data-ttu-id="8d1a2-178">64</span><span class="sxs-lookup"><span data-stu-id="8d1a2-178">64</span></span>  <br/> |
|<span data-ttu-id="8d1a2-179">фамилия;</span><span class="sxs-lookup"><span data-stu-id="8d1a2-179">Last Name</span></span>  <br/> |<span data-ttu-id="8d1a2-180">64</span><span class="sxs-lookup"><span data-stu-id="8d1a2-180">64</span></span>  <br/> |
|<span data-ttu-id="8d1a2-181">Отображаемое имя (обязательный)</span><span class="sxs-lookup"><span data-stu-id="8d1a2-181">Display Name (required)</span></span>  <br/> |<span data-ttu-id="8d1a2-182">256</span><span class="sxs-lookup"><span data-stu-id="8d1a2-182">256</span></span>  <br/> |
|<span data-ttu-id="8d1a2-183">Должность</span><span class="sxs-lookup"><span data-stu-id="8d1a2-183">Job Title</span></span>  <br/> |<span data-ttu-id="8d1a2-184">64</span><span class="sxs-lookup"><span data-stu-id="8d1a2-184">64</span></span>  <br/> |
|<span data-ttu-id="8d1a2-185">Отдел</span><span class="sxs-lookup"><span data-stu-id="8d1a2-185">Department</span></span>  <br/> |<span data-ttu-id="8d1a2-186">64</span><span class="sxs-lookup"><span data-stu-id="8d1a2-186">64</span></span>  <br/> |
|<span data-ttu-id="8d1a2-187">Адрес офиса</span><span class="sxs-lookup"><span data-stu-id="8d1a2-187">Office Number</span></span>  <br/> |<span data-ttu-id="8d1a2-188">128</span><span class="sxs-lookup"><span data-stu-id="8d1a2-188">128</span></span>  <br/> |
|<span data-ttu-id="8d1a2-189">Рабочий телефон</span><span class="sxs-lookup"><span data-stu-id="8d1a2-189">Office Phone</span></span>  <br/> |<span data-ttu-id="8d1a2-190">64</span><span class="sxs-lookup"><span data-stu-id="8d1a2-190">64</span></span>  <br/> |
|<span data-ttu-id="8d1a2-191">Мобильный телефон</span><span class="sxs-lookup"><span data-stu-id="8d1a2-191">Mobile Phone</span></span>  <br/> |<span data-ttu-id="8d1a2-192">64</span><span class="sxs-lookup"><span data-stu-id="8d1a2-192">64</span></span>  <br/> |
|<span data-ttu-id="8d1a2-193">Факс</span><span class="sxs-lookup"><span data-stu-id="8d1a2-193">Fax</span></span>  <br/> |<span data-ttu-id="8d1a2-194">64</span><span class="sxs-lookup"><span data-stu-id="8d1a2-194">64</span></span>  <br/> |
|<span data-ttu-id="8d1a2-195">Адрес</span><span class="sxs-lookup"><span data-stu-id="8d1a2-195">Address</span></span>  <br/> |<span data-ttu-id="8d1a2-196">1023</span><span class="sxs-lookup"><span data-stu-id="8d1a2-196">1023</span></span>  <br/> |
|<span data-ttu-id="8d1a2-197">Город</span><span class="sxs-lookup"><span data-stu-id="8d1a2-197">City</span></span>  <br/> |<span data-ttu-id="8d1a2-198">128</span><span class="sxs-lookup"><span data-stu-id="8d1a2-198">128</span></span>  <br/> |
|<span data-ttu-id="8d1a2-199">область или район.</span><span class="sxs-lookup"><span data-stu-id="8d1a2-199">State or Province</span></span>  <br/> |<span data-ttu-id="8d1a2-200">128</span><span class="sxs-lookup"><span data-stu-id="8d1a2-200">128</span></span>  <br/> |
|<span data-ttu-id="8d1a2-201">Почтовый индекс</span><span class="sxs-lookup"><span data-stu-id="8d1a2-201">ZIP or Postal Code</span></span>  <br/> |<span data-ttu-id="8d1a2-202">40</span><span class="sxs-lookup"><span data-stu-id="8d1a2-202">40</span></span>  <br/> |
|<span data-ttu-id="8d1a2-203">Страна или регион</span><span class="sxs-lookup"><span data-stu-id="8d1a2-203">Country or Region</span></span>  <br/> |<span data-ttu-id="8d1a2-204">128</span><span class="sxs-lookup"><span data-stu-id="8d1a2-204">128</span></span>  <br/> |
   
### <a name="still-having-problems-when-adding-users-to-office-365"></a><span data-ttu-id="8d1a2-205">Все еще возникают проблемы при добавлении пользователей в Office 365?</span><span class="sxs-lookup"><span data-stu-id="8d1a2-205">Still having problems when adding users to Office 365?</span></span>

- <span data-ttu-id="8d1a2-p116">**Еще раз проверьте правильный формат электронной таблицы.** Установите флажок заголовки столбцов, чтобы убедиться в том, что они соответствуют заголовки в файле примера. Убедитесь, что в случае следующие правила для количеству символов и каждого поля, разделенных запятыми.</span><span class="sxs-lookup"><span data-stu-id="8d1a2-p116">**Double-check that the spreadsheet is formatted correctly.** Check the column headings to make sure they match the headings in the sample file. Make sure you're following the rules for character lengths and that each field is separated by a comma.</span></span> 
    
- <span data-ttu-id="8d1a2-p117">** Если новых пользователей в Office 365 не отображается сразу, подождите несколько минут. ** Может потребоваться немного во время для изменения перейти на всех служб в Office 365.</span><span class="sxs-lookup"><span data-stu-id="8d1a2-p117">** If you don't see the new users in Office 365 right away, wait a few minutes. ** It can take a little while for changes to go across all the services in Office 365.</span></span> 
    
## <a name="add-multiple-users-to-office-365-in-the-old-office-365-admin-center"></a><span data-ttu-id="8d1a2-211">Добавление нескольких пользователей в Office 365 в старой центра администрирования Office 365</span><span class="sxs-lookup"><span data-stu-id="8d1a2-211">Add multiple users to Office 365 in the old Office 365 admin center</span></span>

1. <span data-ttu-id="8d1a2-212">Загрузите [Этот пример электронной таблицы](https://www.microsoft.com/en-us/download/details.aspx?id=45485) и откройте его в Excel.</span><span class="sxs-lookup"><span data-stu-id="8d1a2-212">Download [this sample spreadsheet](https://www.microsoft.com/en-us/download/details.aspx?id=45485) and open it in Excel.</span></span> 
    
    <span data-ttu-id="8d1a2-213">Электронной таблицы должна включать **точное же заголовки столбцов** как пример одно (имя пользователя, имя, и т.д...). При использовании шаблона, учитывайте покидать сам по себе он все данные в строке 1 и только ввод данных в строках 2 и ниже.</span><span class="sxs-lookup"><span data-stu-id="8d1a2-213">Your spreadsheet needs to include the **exact same column headings** as the sample one (User Name, First Name, etc...). If you use the template, consider leaving all the data in row 1 alone, and only entering data in rows 2 and below.</span></span> 
    
    <span data-ttu-id="8d1a2-p118">Электронная таблица также должна включать значения для имени пользователя (например, bob@contoso.com) и отображаемое имя (например, Владимир Егоров) для каждого пользователя. В остальных полях оставьте пустой, введите пробел, а также их запятыми в поле как показано на следующем рисунке.</span><span class="sxs-lookup"><span data-stu-id="8d1a2-p118">Your spreadsheet also needs to include values for the user name (like bob@contoso.com) and a display name (like Bob Kelly) for each user. To leave other fields blank, enter a space plus a comma in the field as shown in the following figure.</span></span> 
    
    ![Пример файла РЕЗЮМЕ, имеющей указан пустые строки](media/9c596ba1-1053-4687-a46c-c9359e9818c9.png)
  
    <span data-ttu-id="8d1a2-p119">Если у пользователей, работающих в разных странах, необходимо создать один электронных таблиц для пользователей в каждой страны. Например один электронной таблицы, который содержит список всех сотрудников в США и другую со списком всех сотрудников в Японии. Это так, как доступность служб Office 365 зависит от региона.</span><span class="sxs-lookup"><span data-stu-id="8d1a2-p119">If you have people working in different countries, you'll need to create one spreadsheet for users in each country. For example, one spreadsheet that lists everyone who works in the US, and another that lists everyone who works in Japan. This is because the availability of Office 365 services varies by region.</span></span> 
    
    <span data-ttu-id="8d1a2-p120">**Совет:** Перед добавлением количество пользователей в Office 365 может потребоваться практического занятия пример электронной таблицы. Например изменить пример электронной таблицы с данными для нескольких пользователей, сказать 5 или 10 и сохраните файл под новым именем. Работать с помощью шагов, описанных в этой процедуре, проверьте результаты, удалите новые учетные записи и начать заново. Таким образом, можно прием начало все права, данные для вашей ситуации. Прочитайте [Советы по форматированию электронной таблицы](add-several-users-at-the-same-time.md#__toc314595848).</span><span class="sxs-lookup"><span data-stu-id="8d1a2-p120">**Tip:** Before you add many users to Office 365, you might want to practice with the sample spreadsheet. For example, edit the sample spreadsheet with data for a few of your users, say 5 or 10, and save the file with a new name. Run through steps described in this procedure, check the results, and then delete the new accounts and start over again. This way you can practice getting all of the data right for your situation. Also check out [Tips for formatting your spreadsheet](add-several-users-at-the-same-time.md#__toc314595848).</span></span>
    
2. <span data-ttu-id="8d1a2-225">Войдите в Office 365 с помощью рабочей или учебной учетной записи.</span><span class="sxs-lookup"><span data-stu-id="8d1a2-225">Sign in to Office 365 with your work or school account.</span></span> 
    
3. <span data-ttu-id="8d1a2-226">Перейдите в Центр администрирования Office 365.</span><span class="sxs-lookup"><span data-stu-id="8d1a2-226">Go to the Office 365 admin center.</span></span>
    
4. <span data-ttu-id="8d1a2-p121">Для других служб Office 365 они должны быть назначены лицензии. Прежде чем продолжить, необходимо проверить, что имеется достаточно лицензий для всех, перечисленных в электронной таблице. Выберите **выставления счетов** \> **подписок** для просмотра, если у вас есть достаточно. Если вам потребуется приобрести дополнительные лицензии, выберите ** изменить количество лицензий **. Или можно запустить мастер и назначьте лицензии у, а затем позднее приобрести дополнительные лицензии и перезапустите мастер.</span><span class="sxs-lookup"><span data-stu-id="8d1a2-p121">For people to use Office 365 services, they need to be assigned a license. Before continuing, you might want to check that you have enough licenses for everyone listed in your spreadsheet. Choose **Billing** \> **Subscriptions** to see if you have enough. If you need to buy more licenses, choose ** Change license quantity **. Or, you can run the wizard and assign the licenses you have, then buy more licenses later and rerun the wizard.</span></span> 
    
5. <span data-ttu-id="8d1a2-p122">Теперь перейдите к большую мастера добавления пользователей: выберите **пользователей,** \> **Активные пользователи**. Выберите ![значок для добавления нескольких пользователей в Office 365](media/3481ffea-d552-4a7f-9a3b-014504e69746.png) как показано на следующем рисунке.</span><span class="sxs-lookup"><span data-stu-id="8d1a2-p122">Now go to the Bulk add users wizard: choose **Users** \> **Active Users**. Choose ![The icon for adding many users to Office 365](media/3481ffea-d552-4a7f-9a3b-014504e69746.png) as shown in the following figure.</span></span> 
    
    ![Изображение пользователей в разделе центра администрирования Office 365](media/2cd5ff86-9c0b-438e-9bb9-13b12a2675de.png)
  
    <span data-ttu-id="8d1a2-235">Массовое добавление пользователей wizard, которая предоставляется пошаговый Добавление группы пользователей в Office 365.</span><span class="sxs-lookup"><span data-stu-id="8d1a2-235">The Bulk add users wizard appears and steps you through adding a group of users to Office 365.</span></span> 
    
6. <span data-ttu-id="8d1a2-236">В шаге 1 — выберите CSV-файл, укажите свои собственные электронной таблицы, как показано на следующем рисунке.</span><span class="sxs-lookup"><span data-stu-id="8d1a2-236">In Step 1 - Select a CSV file, specify your own spreadsheet as shown in the following figure.</span></span>
    
    ![Шаг 1 из большую мастера добавления пользователей - выбрать CSV-файла](media/aeb837ed-1f86-427d-b038-c643c383829c.png)
  
7. <span data-ttu-id="8d1a2-238">На шаге 2 - проверку, мастера вы найдете ли правильный формат содержимого в электронной таблице.</span><span class="sxs-lookup"><span data-stu-id="8d1a2-238">In Step 2 - Verification, the wizard tells you whether the content in the spreadsheet is formatted correctly.</span></span>
    
    ![Шаг 2 из большую мастера добавления пользователей — проверки](media/3fd3cd2c-44d4-4593-b02c-b87c176affb3.png)
  
8. <span data-ttu-id="8d1a2-p123">На шаге 3 - параметры, выберите параметр **разрешено** , чтобы пользователи, указанные в электронной таблице будет иметь возможность использовать Office 365. Также выберите страны, в которой эти сотрудники будут использовать Office 365. Помните, если некоторые пользователи в вашей организации будет использовать Office 365 в другой стране, создайте отдельные электронной таблицы с их имена и выполнить массовое мастера добавления пользователей еще раз, чтобы добавить их.</span><span class="sxs-lookup"><span data-stu-id="8d1a2-p123">In Step 3 - Settings, choose **Allowed** so that the people listed in your spreadsheet will be able to use Office 365. Also choose the country in which these people will use Office 365. Remember if some people in your organization are going to use Office 365 in a different country, create a separate spreadsheet with their names and run the Bulk add users wizard again to add them.</span></span> 
    
    ![Шаг 3 большую мастера добавления пользователей - параметры](media/ff12ad34-5d8b-4e89-a02f-d827a94095b3.png)
  
9. <span data-ttu-id="8d1a2-244">Странице назначение лицензий сообщает о том, сколько лицензий, доступны.</span><span class="sxs-lookup"><span data-stu-id="8d1a2-244">The assign licenses page tells you how many licenses are available.</span></span> 
    
    ![Шаг 4 мастера Массовое добавление пользователей - лицензий](media/161ea34c-c67e-43be-962f-029f5426ff1b.png)
  
    <span data-ttu-id="8d1a2-p124">Вы можете **приобрести дополнительные лицензии**, но не будет большую мастера добавления пользователей и перейдите к **выставления счетов** в центре администрирования Office 365. После приобретения дополнительные лицензии, необходимо хранить Подождите несколько минут, порядок обработки и нажмите Пуск большую мастера добавления пользователей с самого начала.</span><span class="sxs-lookup"><span data-stu-id="8d1a2-p124">You can choose **Buy more licenses**, but you'll leave the Bulk add users wizard and go to **Billing** in the Office 365 admin center. After buying more licenses, you'll have to wait a few minutes for the order to be processed and then start the Bulk add users wizard from the beginning.</span></span> 
    
    <span data-ttu-id="8d1a2-248">Если не приобрести дополнительные лицензии, учетные записи не будут созданы для всех, перечисленных в электронной таблице.</span><span class="sxs-lookup"><span data-stu-id="8d1a2-248">If you don't buy more licenses, accounts won't be created for everyone listed in your spreadsheet.</span></span> 
    
    <span data-ttu-id="8d1a2-249">В этом примере не приобрести дополнительные лицензии и продолжите большую мастера добавления пользователей.</span><span class="sxs-lookup"><span data-stu-id="8d1a2-249">In this example, we don't buy any more licenses and continue with the Bulk add users wizard.</span></span>
    
10. <span data-ttu-id="8d1a2-250">На шаге 5 - отправки результатов, введите адреса электронной почты пользователей, которым необходимо получить сообщение электронной почты, в котором приведены *все* имена пользователей Office 365 и временные пароли для пользователей в электронной таблице.</span><span class="sxs-lookup"><span data-stu-id="8d1a2-250">In Step 5 - Send Results, type the email addresses of the people who you want to get an email that lists  *all*  of the Office 365 user names and temporary passwords for the people in the spreadsheet.</span></span> 
    
    ![Шаг 5 большую мастера добавления пользователей - Отправка результатов](media/5beeb825-4ba7-4ae0-bfb5-a1f8a785ebdb.png)
  
    <span data-ttu-id="8d1a2-p125">Следующие сообщение электронной почты отправляется все адреса электронной почты, указанный в шаге 5 - Отправка результатов. Это сообщение указывает учетные записи, которые были созданы. Обратите внимание на то, что учетные записи не были созданы для некоторых пользователей, так как не найден достаточное количество лицензий.</span><span class="sxs-lookup"><span data-stu-id="8d1a2-p125">The following email is sent to all the email addresses you specified in Step 5 - Send results. This email indicates which accounts were created. Notice that accounts weren't created for some people because there weren't enough licenses.</span></span> 
    
    ![Образец сообщения с помощью учетных данных пользователя](media/0a40c612-2078-4b5b-813e-f99bc53635a6.png)
  
    <span data-ttu-id="8d1a2-p126">Вы можете приобрести дополнительные лицензии более поздней версии и повторно запустить Массовое добавление мастера пользователей с одной электронной таблицы. Мастер пропускает пользователи, которые уже имеют учетные записи; в отчете о результатах, появится сообщение «имя пользователя», чтобы указать, кто-то еще сведениями об учетной записи.</span><span class="sxs-lookup"><span data-stu-id="8d1a2-p126">You can buy more licenses later and rerun the Bulk add users wizard with the same spreadsheet. The wizard skips over the users that already have accounts; on the results report, it will say "duplicate user name" to indicate someone with that information already has an account.</span></span>
    
11. <span data-ttu-id="8d1a2-258">Последней странице массовое добавить мастер пользователи приведены имена пользователей и временные пароли, как показано на следующем рисунке.</span><span class="sxs-lookup"><span data-stu-id="8d1a2-258">The final page in the Bulk add users wizard lists the user names and temporary passwords, as shown in the following figure.</span></span>
    
    ![Шаг 6 большую мастера добавления пользователей - Отправка результатов](media/0cd43832-071b-4b33-b57a-5d07959985ad.png)
  
12. <span data-ttu-id="8d1a2-p127">После добавления пользователей в Office 365, необходимо сообщить им о своих сведений об учетной записи Office 365. Используйте обычный процесс для общения новых паролей.</span><span class="sxs-lookup"><span data-stu-id="8d1a2-p127">After you've added users to Office 365, you need to tell them about their Office 365 account information. Use your normal process for communicating new passwords.</span></span>
    

