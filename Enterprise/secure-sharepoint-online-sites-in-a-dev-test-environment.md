---
title: "Защита сайтов SharePoint Online в среде разработки и тестирования"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.custom:
- DecEntMigration
- Strat_O365_Enterprise
ms.assetid: 06af70f3-e7dc-4ee2-a385-fb4d61a5e93b
description: 'Summary: Create public, private, sensitive, and highly confidential SharePoint Online team sites in a dev/test environment.'
ms.openlocfilehash: 17abee7a293996194a097693607b4b4d9c117046
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2017
---
# <a name="secure-sharepoint-online-sites-in-a-devtest-environment"></a>Защита сайтов SharePoint Online в среде разработки и тестирования

 **Summary:** Create public, private, sensitive, and highly confidential SharePoint Online team sites in a dev/test environment.
  
This article provides step-by-step instructions to create a dev/test environment that includes the four different types of SharePoint Online team sites for the [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md) solution.
  
![Все четыре сайта группы в безопасной среде разработки и тестирования SharePoint Online.](images/b0fea489-359c-4c85-a0ad-e4efb4a1e47f.png)
  
Use this dev/test environment to experiment with the information protection behaviors and fine-tune settings for your specific needs before deploying SharePoint Online team sites in production.
  
## <a name="phase-1-create-your-devtest-environment"></a>Этап 1. Создание среды разработки и тестирования

In this phase, you obtain trial subscriptions for Office 365 and Enterprise Mobility + Security for a fictional organization.
  
First, follow the instructions in **Phase 2** of the [Office 365 dev/test environment](office-365-dev-test-environment.md).
  
Затем оформите пробную подписку на EMS и добавьте ее к той же организации, что и пробную подписку на Office 365.
  
1. If needed, sign in to the Office 365 portal with the credentials of the global administrator account of your trial subscription. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Click the **Admin** tile.
    
3. On the **Office Admin center** tab in your browser, in the left navigation, click **Billing > Purchase services**.
    
4. On the **Purchase services** page, find the **Enterprise Mobility + Security E5** item. Hover your mouse pointer over it and click **Start free trial**.
    
5. On the **Confirm your order** page, click **Try now**.
    
6. On the **Order receipt** page, click **Continue**.
    
Затем включите лицензию на Enterprise Mobility + Security E5 для учетной записи глобального администратора.
  
1. On the **Office 365 Admin center** tab in your browser, in the left navigation, click **Users > Active users**.
    
2. Click your global administrator account, and then click **Edit** for **Product licenses**.
    
3. On the **Product licenses** pane, turn the product license for **Enterprise Mobility + Security E5** to **On**, click **Save,** and then click **Close** twice.
    
## <a name="phase-2-create-and-configure-your-azure-active-directory-ad-groups-and-users"></a>Phase 2: Create and configure your Azure Active Directory (AD) groups and users

In this phase, you create and configure the Azure AD groups and users for your fictional organization.
  
First, create a set of groups for a typical organization with the Azure portal.
  
1. Create a separate tab in your browser, and then go to the Azure portal at [https://portal.azure.com](https://portal.azure.com). If needed, sign in with the credentials of the global administrator account for your Office 365 E5 trial subscription.
    
2. In the Azure portal, click **Azure Active Directory > Users and groups > All groups**.
    
3. On the **All groups** blade, click **+ New group**.
    
4. On the **Group** blade:
    
  - Type **C-Suite** in **Name**.
    
  - Select **Assigned** in **Membership**.
    
  - Click **Yes** for **Enable Office features**.
    
5. Click **Create**, and then close the **Group** blade.
    
6. Repeat steps 3-5 for the following group names:
    
  - ИТ-персонал
    
  - Исследовательский персонал
    
  - Обычный персонал
    
  - Сотрудники отдела маркетинга
    
  - Сотрудники отдела продаж
    
7. Keep the Azure portal tab in your browser open.
    
Затем настройте автоматическое лицензирование, чтобы членам групп автоматически назначались лицензии для подписок на Office 365 и EMS.
  
1. In the Azure portal, click **Azure Active Directory > Licenses > All products**.
    
2. In the list, select **Enterprise Mobility + Security E5** and **Office 365 Enterprise E5**, and then click **Assign**.
    
3. In the **Assign license** blade, click **Users and groups**.
    
4. В списке выберите следующие группы:
    
  - Топ-менеджмент
    
  - ИТ-персонал
    
  - Исследовательский персонал
    
  - Обычный персонал
    
  - Сотрудники отдела маркетинга
    
  - Сотрудники отдела продаж
    
5. Click **Select**, and then click **Assign**.
    
6. Закройте вкладку портала Azure в браузере.
    
Next, you [Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218).
  
Fill in your organization name, your location, and a common password, and then run these commands from the PowerShell command prompt or Integrated Script Environment (ISE) to create user accounts and add them to their groups:
  
```
$orgName="<organization name, such as contoso for the contoso.onmicrosoft.com trial subscription domain name>"
$location="<the ISO ALPHA2 country code, such as US for the United States>"
$commonPassword="<common password for all the new accounts>"

$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password=$commonPassword

$groupName="C-Suite"
$userNames=@("CEO","CFO","CIO") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="IT staff"
$userNames=@("ITAdmin1","ITAdmin2") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="Research staff"
$userNames=@("Researcher1") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="Regular staff"
$userNames=@("Regular1", "Regular2") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="Marketing staff"
$userNames=@("Marketing1", "Marketing2") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="Sales staff"
$userNames=@("SalesPerson1") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
```

> [!NOTE]
> Общий пароль используется для автоматизации и упрощения настройки среды разработки и тестирования. Не рекомендуется для рабочих подписок. 
  
Выполните указанные ниже действия, чтобы убедиться, что лицензирование на основе групп работает должным образом.
  
1. From the **Microsoft Office Home** tab of your browser, click the **Admin** tile.
    
2. From the new **Office Admin center** tab of your browser, click **Users**.
    
3. In the list of users, click **CEO**.
    
4. In the pane that lists the properties of the **CEO** user account, verify that it has been assigned the **Enterprise Mobility + Security E5** and **Office 365 Enterprise E5** licenses (in **Product licenses**).
    
## <a name="phase-3-create-office-365-labels"></a>Phase 3: Create Office 365 labels

На этом этапе мы создадим метки разных уровней защиты для папок документов на сайтах групп SharePoint Online.
  
1. If needed, use a private instance of your Internet browser and sign in to the Office 365 portal with the global administrator account of your Office 365 E5 trial subscription. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. From the **Microsoft Office Home** tab, click the **Admin** tile.
    
3. From the new **Office Admin center** tab of your browser, click **Admin centers > Security &amp; Compliance**.
    
4. From the new **Home - Security &amp; Compliance** tab of your browser, click **Classifications > Labels**.
    
5. From the **Home > Labels** pane, click **Create a label**.
    
6. On the **Name your label** pane, type **Internal Public**, and then click **Next**.
    
7. On the **Label settings** pane, click **Next**.
    
8. On the **Review your settings** pane, click **Create this label**, and then click **Close**.
    
9. Повторите действия 5–8 для следующих меток:
    
  - Частный
    
  - Конфиденциальный
    
  - Строго конфиденциальный
    
10. From the **Home > Labels** pane, click **Publish labels**.
    
11. On the **Choose labels to publish** pane, click **Choose labels to publish**.
    
12. On the **Choose labels** pane, click **Add** and select all four labels.
    
13. Click **Done**.
    
14. On the **Choose labels to publish** pane, click **Next**.
    
15. On the **Choose locations** pane, click **Next**.
    
16. On the **Name your policy** pane, type **Example organization** in **Name**, and then click **Next**.
    
17. On the **Review your settings** pane, click **Publish labels**, and then click **Close**.
    
## <a name="phase-4-create-your-sharepoint-online-team-sites"></a>Phase 4: Create your SharePoint Online team sites

In this phase, you create and configure the four types of SharePoint Online team sites for your example organization.
  
### <a name="organization-wide-team-site"></a>Сайт группы для всей организации

Чтобы создать базовый общедоступный сайт группы SharePoint Online, выполните указанные ниже действия.
  
1. If needed, use a browser on your local computer and sign in to the Office 365 portal using your global administrator account. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. In the list of tiles, click **SharePoint**.
    
3. On the new **SharePoint** tab in your browser, click **+ Create site**.
    
4. On the **Create a site** page, click **Team site**.
    
5. In **Site name**, type **Organization wide**. 
    
6. In **Team site description**, type **SharePoint site for the entire organization**.
    
7. In **Privacy settings**, select **Public - anyone in the organization can access this site**, and then click **Next**.
    
8. On the **Who do you want to add?** pane, click **Finish**.
    
Next, configure the documents folder of the Organization wide team site for the Internal Public label.
  
1. In the **Organization wide-Home** tab of your browser, click **Documents**.
    
2. Click the settings icon, and then click **Library settings**.
    
3. Under **Permissions and Management**, click **Apply label to items in this library**.
    
4. In **Settings-Apply Label**, select **Internal Public**, and then click **Save**.
    
Ниже показана итоговая конфигурация.
  
![Защита базового уровня для общедоступного сайта группы SharePoint Online, используемого во всей организации.](images/25c86847-a38d-49ad-bb5f-c7c04206b6dc.png)
  
### <a name="project-1-team-site"></a>Сайт группы "Проект 1"

Чтобы создать базовый частный сайт группы SharePoint Online для проекта в организации, выполните указанные ниже действия.
  
1. If needed, use a browser on your local computer and sign in to the Office 365 portal using your global administrator account. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. In the list of tiles, click **SharePoint**.
    
3. На новой вкладке **SharePoint** в браузере нажмите кнопку **+ Создание сайта**.
    
4. On the **Create a site** page, click **Team site**.
    
5. В поле **имя узла**введите **1 для Project**. 
    
6. В **поле Описание сайта группы** укажите **сайт SharePoint для проекта 1**.
    
7. В **Параметры конфиденциальности**, выберите **частный — только для членов можно получить доступ к этот сайт**и нажмите кнопку **Далее**.
    
8. On the **Who do you want to add?** pane, click **Finish**.
    
Затем настройте папку документов на сайте группы "Проект 1" на использование метки "Частный".
  
1. In the **Project 1-Home** tab of your browser, click **Documents**.
    
2. Щелкните значок параметры и нажмите кнопку **Параметры библиотеки**.
    
3. Under **Permissions and Management**, click **Apply label to items in this library**.
    
4. В поле **Применить параметры метки**выберите **частный**и нажмите кнопку **Сохранить**.
    
Ниже показана итоговая конфигурация.
  
![Защита базового уровня для закрытого сайта группы SharePoint Online, названного Project1.](images/ecd96376-b5dc-4042-9cbd-b3765507ace7.png)
  
### <a name="marketing-campaigns-team-site"></a>Сайт группы маркетинговых кампаний

Чтобы создать изолированный сайт группы SharePoint Online на конфиденциальном уровне для ресурсов маркетинговых кампаний, выполните указанные ниже действия.
  
1. Using a browser on your local computer, sign in to the Office 365 portal using your global administrator account. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. In the list of tiles, click **SharePoint**.
    
3. На новой вкладке **SharePoint** в браузере нажмите кнопку **+ Создание сайта**.
    
4. На странице **создания сайта** щелкните **сайт группы**.
    
5. In **Team site name**, type **Marketing campaigns**.
    
6. В поле **Описание сайта группы**укажите **сайт SharePoint для маркетинговых кампаний ресурсы (с учетом)**.
    
7.  In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.
    
8. На **пользователей, которые вы хотите добавить?** области, нажмите кнопку **Готово**.
    
9. На вкладке **маркетинговые кампании** в браузере, в панели инструментов щелкните значок параметры и нажмите кнопку **разрешения для сайта**.
    
10. В области **разрешения для сайта** выберите **Параметры дополнительные разрешения**.
    
11. На новой вкладке **разрешения** в браузере нажмите кнопку **Параметры запроса доступа**.
    
12. В диалоговом окне **Параметры запроса доступа** снимите флажки **Разрешить членам для совместного использования сайтов и отдельных файлов и папок** и **Разрешить участникам приглашать других людей для группы участников сайта** введите **ITAdmin1 @**\<вашей Название организации >**. onmicrosoft.com** в **отправлять все запросы на доступ**и нажмите кнопку **ОК**.
    
13. **Маркетинговые кампании элементы** выберите в списке.
    
14. На странице " **пользователи и группы** " нажмите кнопку **Создать**.
    
15. In the **Share** dialog box, type **Marketing staff**, select it, and then click **Share**.
    
16. Повторите шаги 14 и 15 для учетной записи пользователя **Researcher1** .
    
17. Нажмите кнопку "Назад" в браузере.
    
18. **Маркетинговые кампании владельцев** выберите в списке.
    
19. На странице " **пользователи и группы** " нажмите кнопку **Создать**.
    
20. В диалоговом окне **общий доступ** введите **ИТ-специалистов**, выберите его и нажмите кнопку **общий доступ**.
    
21. Нажмите кнопку "Назад" в браузере.
    
22. Закройте вкладку **людей и групп** в браузере, перейдите на вкладку **маркетинговых кампаний домашней** в браузере, а затем закройте в области **разрешения для сайта** .
    
Ниже представлены результаты настройки разрешений.
  
- SharePoint **Маркетинговые кампании — члены** группы содержит только группе **маркетинговые кампании** (содержащий учетная запись глобального администратора), группа **сотрудников отдела маркетинга** , (который содержит Marketing1 и Marketing2 пользователя учетные записи), а **Researcher1** учетная запись пользователя.
    
- **Маркетинговые кампании владельцев** SharePoint группа содержит только группы **ИТ-специалистов** (который содержит только ITAdmin1 и ITAdmin2 учетные записи пользователей).
    
- Группы SharePoint **Маркетинговые кампании посетители** не содержит групп или учетных записей пользователей.
    
- Члены не могут изменять разрешения на уровне сайта (это может быть выполнено только члены группы **Маркетинговые кампании владельцев** ).
    
- У других учетных записей нет доступа к сайту и его ресурсам, но они могут запрашивать доступ к сайту. При этом в почтовый ящик пользователя "ИТ-администратор1" отправляется электронное сообщение.
    
Теперь настройте папку документов на сайте группы "Маркетинговые кампании" на использование метки "Конфиденциальный".
  
1. На вкладке **маркетинговых кампаний домашней** браузера щелкните **документы**.
    
2. Щелкните значок параметры и нажмите кнопку **Параметры библиотеки**.
    
3. В разделе **разрешения и управление**щелкните **метки применить к элементам в этой библиотеке**.
    
4. В поле **Применить параметры метки**выберите **конфиденциальных**и нажмите кнопку **Сохранить**.
    
Затем настройте политику защиты от потери данных (DLP), которая сообщает пользователям, когда они пытаются поделиться документом, хранящемся на сайте группы SharePoint Online с меткой "Конфиденциальный" (таким является и сайт "Маркетинговые кампании"), с пользователями за пределами организации.
  
1. На вкладке **Microsoft Office для дома** в браузере выберите **безопасности &amp; соответствия** заголовков.
    
2. В новом **безопасности &amp; соответствия** в браузере, щелкните **защиту от потери данных > политики**.
    
3. На левой панели **защиту от потери данных** нажмите кнопку **+ Создать политику**.
    
4. В **Начать с шаблоном или создайте пользовательскую политику** области, выберите **настраиваемые**и нажмите кнопку **Далее**.
    
5. В области **Имя политики** введите **конфиденциальных метки SharePoint Online веб-сайтов групп** в поле **имя**и нажмите кнопку **Далее**.
    
6. На левой панели **Выберите расположение** нажмите кнопку **выбрать определенные расположения**и нажмите кнопку **Далее**.
    
7. В списке расположений отключить расположения **учетных записей OneDrive** и **электронной почты Exchange** и нажмите кнопку **Далее**.
    
8. В области **Настройка типов конфиденциальные сведения, которые необходимо защитить** нажмите кнопку **Изменить**.
    
9. На левой панели **выберите типы содержимого для защиты** нажмите кнопку **Добавить** , в раскрывающемся списке и нажмите кнопку **метки**.
    
10. В области **метки** нажмите кнопку **+ Добавить**, выберите **конфиденциальных** метку, нажмите кнопку **Добавить**и нажмите кнопку **Готово**.
    
11. На левой панели **выберите типы содержимого для защиты** нажмите кнопку **Сохранить**.
    
12. В области **Настройка типов конфиденциальные сведения, которые необходимо защитить** нажмите кнопку **Далее**.
    
13. В **необходимые действия, если мы обнаруживать конфиденциальные сведения?** области, нажмите кнопку **Настройка подсказки и адрес электронной почты**.
    
14. В области **Настройка подсказок политики и уведомления по электронной почте** нажмите кнопку **Настройка текст подсказки политики**.
    
15. В текстовом поле введите или вставьте в следующем примере:
    
  - Чтобы предоставить доступ пользователю за пределами организации, скачайте файл и откройте его. Выберите пункты "Файл > Защитить документ > Зашифровать паролем", а затем укажите надежный пароль. Отправьте пароль в отдельном сообщении или с помощью других средств связи.
    
16. Нажмите кнопку **ОК**.
    
17. В **необходимые действия, если мы обнаруживать конфиденциальные сведения?** области, снимите флажок **Блокировать людей из общего доступа и ограничить доступ к общее содержимое** и нажмите кнопку **Далее**.
    
18. В **хотите ли вы включить действия политики или тестирования сначала?** области, нажмите кнопку **Да, включить немедленно**и нажмите кнопку **Далее**.
    
19. В области **Проверьте параметры** нажмите кнопку **Создать**и затем нажмите кнопку **Закрыть**.
    
Ниже показана итоговая конфигурация.
  
![Защита уровня конфиденциальности для изолированного сайта группы SharePoint Online, названного "Маркетинговые кампании".](images/33992bd5-96ee-4bfb-9ecf-c8a6736dd100.png)
  
### <a name="company-strategy-team-site"></a>Сайт стратегической группы кампании

Для создания изолированного SharePoint Online сайт группы на уровне конфиденциальными для стратегического компании ресурсов главного Руководители организации, выполните следующее:
  
1. При необходимости, используйте браузер на локальном компьютере и войдите в портал Office 365 с помощью учетной записи глобального администратора. Дополнительные сведения см [Where для входа в Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. В списке заголовков щелкните **SharePoint**.
    
3. На новой вкладке **SharePoint** в браузере нажмите кнопку **+ Создание сайта**.
    
4. На странице **создания сайта** щелкните **сайт группы**.
    
5. В поле **имя сайта группы**введите **стратегии компании**.
    
6. В поле **Описание сайта группы**укажите **сайт SharePoint для стратегии компании (конфиденциальными)**.
    
7.  В **Параметры конфиденциальности**, выберите **частный — только для членов можно получить доступ к этот сайт**и нажмите кнопку **Далее**.
    
8. На **пользователей, которые вы хотите добавить?** области, нажмите кнопку **Готово**.
    
9. На вкладке **стратегии компании** в браузере, в панели инструментов щелкните значок параметры и нажмите кнопку **разрешения для сайта**.
    
10. В области **разрешения для сайта** выберите **Параметры дополнительные разрешения**.
    
11. На новой вкладке **разрешения** в браузере нажмите кнопку **Параметры запроса доступа**.
    
12. В диалоговом окне **Параметры запроса доступа** снимите флажок **Разрешить участникам совместного использования сайтов и отдельных файлов и папок** и **Разрешить участникам приглашать других людей для группы участников сайта** (, чтобы все три флажка), а затем нажмите кнопку ** Кнопки ОК**.
    
13. Выберите **стратегии компании элементы** в списке.
    
14. На странице " **пользователи и группы** " нажмите кнопку **Создать**.
    
15. В диалоговом окне **общий доступ** введите **C Suite**, выберите его и нажмите кнопку **совместный доступ**.
    
16. В списке выберите **стратегии компании владельцев** .
    
17. На странице " **пользователи и группы** " нажмите кнопку **Создать**.
    
18. В диалоговом окне **общий доступ** введите **ИТ-специалистов**, выберите его и нажмите кнопку **общий доступ**.
    
19. Нажмите кнопку "Назад" в браузере.
    
20. Закройте вкладку **людей и групп** в браузере, перейдите на вкладку **Главная страница компании стратегии** в браузере, а затем закройте в области **разрешения для сайта** .
    
Ниже представлены результаты настройки разрешений.
  
- **Стратегия компании — члены** группы SharePoint содержит только группы **C Suite** (который содержит только CEO, финансового Директора и директор по информационным Технологиям учетные записи пользователей) и **стратегии компании** (который содержит только учетная запись пользователя глобального администратора).
    
- **Стратегия компании - владельцев** группы SharePoint содержит только группы **ИТ-специалистов** (который содержит только ITAdmin1 и ITAdmin2 учетные записи пользователей).
    
- **Стратегия компании - посетители** группы SharePoint не содержит групп или учетных записей пользователей.
    
- Члены не могут изменять разрешения на уровне сайта (это может быть выполнено только члены группы **Владельцами стратегии компании** ).
    
- Другие учетные записи пользователей не удается доступ к узлу или его ресурсов или запросить доступ к сайту. Глобальный администратор или членом группы **Стратегии компании - владельцев** , необходимо выполнить дополнительные разрешения для сайта.
    
Затем настройте папку документов на сайте стратегической группы компании на использование метки "Строго конфиденциально".
  
1. На вкладке **Главная страница компании стратегии** браузера щелкните **документы**.
    
2. Щелкните значок параметры и нажмите кнопку **Параметры библиотеки**.
    
3. В разделе **разрешения и управление**щелкните **метки применить к элементам в этой библиотеке**.
    
4. В поле **Применить параметры метки**выберите **Конфиденциальными**и нажмите кнопку **Сохранить**.
    
Настройте политику предотвращения потери данных, которое пользователи блоки при их совместное использование документов на сайте группы SharePoint Online с конфиденциальными метки, который включает сайта стратегии компании, за пределами организации.
  
1. В случае необходимости, используйте браузер на локальном компьютере и войдите в портал Office 365 с использованием учетной записи, имеющей роли безопасности администратора или администратора компании. Дополнительные сведения см [Where для входа в Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. На вкладке **Microsoft Office для дома** в браузере выберите **безопасности &amp; соответствия** заголовков.
    
3. В новом **безопасности &amp; соответствия** в браузере, щелкните **защиту от потери данных > политики**.
    
4. На левой панели **защиту от потери данных** нажмите кнопку **+ Создать политику**.
    
5. В **Начать с шаблоном или создайте пользовательскую политику** области, выберите **настраиваемые**и нажмите кнопку **Далее**.
    
6. В области **Имя политики** введите **конфиденциальными метки SharePoint Online веб-сайтов групп** в поле **имя**и нажмите кнопку **Далее**.
    
7. На левой панели **Выберите расположение** нажмите кнопку **выбрать определенные расположения**и нажмите кнопку **Далее**.
    
8. В списке расположений отключить расположения **учетных записей OneDrive** и **электронной почты Exchange** и нажмите кнопку **Далее**.
    
9. В области **Настройка типов конфиденциальные сведения, которые необходимо защитить** нажмите кнопку **Изменить**.
    
10. На левой панели **выберите типы содержимого для защиты** нажмите кнопку **Добавить** , в раскрывающемся списке и нажмите кнопку **метки**.
    
11. На левой панели **метки** нажмите кнопку **+ Добавить**, выберите метку **Конфиденциальными** , нажмите кнопку **Добавить**и нажмите кнопку **Готово**.
    
12. На левой панели **выберите типы содержимого для защиты** нажмите кнопку **Сохранить**.
    
13. В области **Настройка типов конфиденциальные сведения, которые необходимо защитить** нажмите кнопку **Далее**.
    
14. В **необходимые действия, если мы обнаруживать конфиденциальные сведения?** области, нажмите кнопку **Настройка подсказки и адрес электронной почты**.
    
15. В области **Настройка подсказок политики и уведомления по электронной почте** нажмите кнопку **Настройка текст подсказки политики**.
    
16. В текстовом поле введите или вставьте в следующем примере:
    
  - Чтобы предоставить доступ пользователю за пределами организации, скачайте файл и откройте его. Выберите пункты "Файл > Защитить документ > Зашифровать паролем", а затем укажите надежный пароль. Отправьте пароль в отдельном сообщении или с помощью других средств связи.
    
17. Нажмите кнопку **ОК**.
    
18. В **необходимые действия, если мы обнаруживать конфиденциальные сведения?** области, выберите **Требовать деловое обоснование для переопределения**и нажмите кнопку **Далее**.
    
19. В **хотите ли вы включить действия политики или тестирования сначала?** области, нажмите кнопку **Да, включить немедленно**и нажмите кнопку **Далее**.
    
20. В области **Проверьте параметры** нажмите кнопку **Создать**и затем нажмите кнопку **Закрыть**.
    
Затем следуйте инструкциям в [Активировать Azure службы управления правами с помощью центра администрирования Office 365](https://docs.microsoft.com/information-protection/deploy-use/activate-office365).
  
Далее настройте защита информации Azure с новой областью видимости политики и вложенных метку для защиты и разрешения с помощью следующих действий:
  
1. Войдите на портал Office 365, используя учетную запись с ролью администратора компании или администратора безопасности. Справочные сведения см. в статье [Вход в Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Перейдите на портал Azure ([https://portal.azure.com](https://portal.azure.com)), открыв отдельную вкладку браузера.
    
3. Если вы настраиваете Azure Information Protection впервые, ознакомьтесь с этими [инструкциями](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).
    
4. На панели списка выберите **Дополнительные службы**, введите **Информация**, а затем выберите **Azure Information Protection**.
    
5. В колонке **Azure Information Protection**, щелкните последовательно элементы **Политики в области > + Добавить политику**.
    
6. В **имени политики** и **метки для документов на сайте рабочей группы стратегии компании** в **поле Описание**введите **CompanyStrategy** .
    
7. Нажмите кнопку **выбрать, какие пользователи или группы получить эту политику > пользователей и групп**, а затем выберите **Набор C**.
    
8. Щелкните элементы **Выбрать > ОК**.
    
9. Для метки **Строго конфиденциально** щелкните последовательно многоточие (…) и элемент **Добавить подчин. метку**.
    
10. Введите имя подчиненной метки в поле **Имя** и описание метки в поле **Описание**.
    
11. В разделе **Задайте разрешения для документов и электронных писем, имеющих эту метку** нажмите кнопку **Защитить**.
    
12. В разделе **Защита** выберите элемент **Azure (облачный ключ)**.
    
13. В колонке **Защита**, в разделе **Параметры защиты**, нажмите **+ Добавить разрешения**.
    
14. Перейдите к колонке **Добавление разрешений** и выберите **+ Обзор каталога** в разделе **Укажите пользователей и группы**.
    
15. В области **AAD пользователей и групп** выберите **Набор C**и нажмите кнопку **выбрать**.
    
16. В разделе **Выбор разрешений из шаблона** снимите флажки **Печать**, **Копирование и извлечение контента** и **Переадресация**.
    
17. Дважды нажмите кнопку **ОК**.
    
18. В колонке **Подчиненная метка** нажмите кнопку **Сохранить**.
    
19. Закройте колонку новой политики области.
    
20. На blade **Защита информации Azure - областью видимости политик** нажмите кнопку **Опубликовать**и нажмите кнопку **Да**.
    
Чтобы защитить документ с Azure защита информации и этой новой метки, необходимо [установить клиент защита информации Azure](https://docs.microsoft.com/information-protection/rms-client/install-client-app) на тестовом компьютере, установка Office с портала Office 365 и войдите в из Microsoft Word с использованием учетной записи в ** C-Suite** группы пробной подписки.
  
Ниже показана итоговая конфигурация.
  
![Защита уровня строгой конфиденциальности для изолированного сайта группы SharePoint Online, названного "Стратегия компании".](images/c22695f9-50a1-4abf-a0dd-344b0c92cf94.png)
  
Теперь все готово для создания документов на эти четыре сайтах и тестирования доступа к ним с помощью различных учетных записей пользователей в пробной подписки.
  
Вот общей конфигурации для четырех SharePoint Online сайтов групп.
  
![Все четыре сайта группы в безопасной среде разработки и тестирования SharePoint Online.](images/b0fea489-359c-4c85-a0ad-e4efb4a1e47f.png)
  
## <a name="next-step"></a>Следующее действие

Если все готово для производственного развертывания безопасных сайтами SharePoint Online, видеть [безопасной SharePoint Online сайтами и файлами](secure-sharepoint-online-sites-and-files.md) подробные сведения и ссылки на статьи о развертывании пошаговые.
  
## <a name="see-also"></a>See Also

[Безопасность сайтов и файлов SharePoint Online](secure-sharepoint-online-sites-and-files.md)
  
[Решения для обеспечения безопасности](security-solutions.md)
  
[Освоение облака и гибридные решения](cloud-adoption-and-hybrid-solutions.md)
  
[Руководство по безопасности (Майкрософт) для политических кампаний, некоммерческих и других динамических организаций](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)




