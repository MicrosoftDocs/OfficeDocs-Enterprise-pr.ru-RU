---
title: Среда разработки и тестирования изолированного сайта группы SharePoint Online
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
ms.assetid: d1795031-beef-49ea-a6fc-5da5450d320d
description: Сводка. Настройте сайт группы SharePoint Online, изолированный от остальной организации, в среде Office 365 для разработки и тестирования.
ms.openlocfilehash: d2a75f3a3a410116c454892c9ecf3747fb3da53d
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915054"
---
# <a name="isolated-sharepoint-online-team-site-devtest-environment"></a>Среда разработки и тестирования изолированного сайта группы SharePoint Online

 **Сводка.** Настройте сайт группы SharePoint Online, изолированный от остальной организации, в среде Office 365 для разработки и тестирования.
  
SharePoint Online сайтов группы в Office 365, расположения для совместной работы, с помощью библиотеки общих документов, записной книжки OneNote и другие службы. Во многих случаях требуется широкий доступ и совместная работа между организаций или отделов. Тем не менее в некоторых случаях вы хотите жестко контролировать доступ и разрешения для сотрудничества между небольшой группы пользователей.
  
Доступ к SharePoint Online сайты рабочих групп и что могут делать пользователи управляет групп и уровней разрешений SharePoint. По умолчанию сайты SharePoint Online имеют три уровня доступа:
  
- **Участники** могут просматривать, создавать и изменять ресурсы на сайте.
    
- **Владельцы** могут полностью контролировать сайт, в том числе изменять разрешения.
    
- **Посетители** могут просматривать ресурсы на сайте.
    
В этом статье действия по конфигурации изолированного SharePoint Online сайт группы для проекта секретный справочные материалы с именем ProjectX. Требования к access являются:
  
- Только участники проекта могут получить доступ к сайту и его содержимому (документам, записной книжке OneNote, страницам), уровни разрешений SharePoint на просмотр и редактирование определяются членством в группе.
    
- Только создатель сайта и члены группы администраторов сайта могут выполнять администрирование сайта, в том числе изменять разрешения на уровне сайта.
    
Настройка изолированного сайта группы SharePoint Online в среде Office 365 для разработки и тестирования выполняется в три этапа:
  
1. Создание среды разработки и тестирования Office 365.
    
2. Создание пользователей и групп для ProjectX.
    
3. Создание сайта группы SharePoint Online для ProjectX и его изоляция.
    
> [!TIP]
> Щелкните [здесь](http://aka.ms/catlgstack), чтобы просмотреть схему всех статей, относящихся к руководствам по лаборатории тестирования Microsoft Cloud.
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a>Этап 1. Создание среды разработки и тестирования Office 365 — упрощенной или для имитированных предприятий

Если необходимо создать узел изолированного группы разработчиков SharePoint Online в облегченный путь с минимальным требованиям, следуйте инструкциям в этапы 2 и 3 [Office 365 dev/тестовой среды](office-365-dev-test-environment.md).
  
Если вы хотите создать узел изолированного группы разработчиков SharePoint Online в конфигурации имитации enterprise, следуйте инструкциям в [DirSync для вашей среды разработки или тестирования Office 365](dirsync-for-your-office-365-dev-test-environment.md).
  
> [!NOTE]
> Для создания изолированного сайта SharePoint Online не требуется имитированная среда разработки и тестирования предприятия, которая включает имитированную интрасеть, подключенную к Интернету, и синхронизацию каталогов для леса Windows Server AD. Она указана здесь, чтобы вы могли протестировать изолированный сайт SharePoint Online и поэкспериментировать с ним в среде, которая представляет типичную среду для организаций. 
  
## <a name="phase-2-create-user-accounts-and-access-groups"></a>Этап 2: Создание учетных записей пользователей и доступ к группам

Используйте инструкции из статьи [подключение к Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx) подключиться к своей подписке журнала Office 365, используя свою учетную запись глобального администратора из:
  
- компьютера (для упрощенной среды разработки и тестирования Office 365);
    
- виртуальной машины CLIENT1 (для среды Office 365 для разработки и тестирования смоделированного предприятия).
    
Чтобы создать новые группы доступа для ProjectX SharePoint Online сайт группы, выполните эти команды в командной строке Windows Azure модуль Active Directory для Windows PowerShell.
  
```
$groupName="ProjectX-Members"
$groupDesc="People allowed to collaborate for ProjectX."
New-MsolGroup -DisplayName $groupName -Description $groupDesc
$groupName="ProjectX-Admins"
$groupDesc="People allowed to administer SharePoint for ProjectX."
New-MsolGroup -DisplayName $groupName -Description $groupDesc
$groupName="ProjectX-Viewers"
$groupDesc="People allowed to view the SharePoint resources for ProjectX."
New-MsolGroup -DisplayName $groupName -Description $groupDesc
```

> [!TIP]
> Щелкните [здесь](https://gallery.technet.microsoft.com/PowerShell-commands-for-an-b2608df1) для текстового файла, который содержит все команды PowerShell в данной статье.
  
Введите название организации (например, contosotoycompany) и двузначный код страны, а затем выполните следующие команды в командной строке модуля Windows Azure Active Directory для Windows PowerShell:
  
```
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$licAssignment= $orgName + ":ENTERPRISEPREMIUM"
$userName= "designer@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "Lead Designer" -FirstName Lead -LastName Designer -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment -ForceChangePassword $false
```

Запишите в надежном месте пароль, созданный командой **New-MsolUser** для учетной записи ведущего дизайнера.
  
Выполните следующие команды в командной строке модуля Windows Azure Active Directory для Windows PowerShell:
  
```
$userName= "researcher@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "Lead Researcher" -FirstName Lead -LastName Researcher -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment -ForceChangePassword $false
```

Запишите в надежном месте пароль, созданный командой **New-MsolUser** для учетной записи ведущего научного сотрудника.
  
Выполните следующие команды в командной строке модуля Windows Azure Active Directory для Windows PowerShell:
  
```
$userName= "devvp@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "Development VP" -FirstName Development -LastName VP -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment -ForceChangePassword $false
```

Запишите в надежном месте пароль, созданный командой **New-MsolUser** для учетной записи вице-президента по развитию.
  
Затем для добавления новых учетных записей для новых групп доступа, выполните следующие команды PowerShell в командной строке Windows Azure модуль Active Directory для Windows PowerShell:
  
```
$grpName="ProjectX-Members"
$userUPN="designer@" + $orgName + ".onmicrosoft.com"
Add-MsolGroupMember -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $grpName }).ObjectID -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupMemberType "User"
$userUPN="researcher@" + $orgName + ".onmicrosoft.com"
Add-MsolGroupMember -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $grpName }).ObjectID -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupMemberType "User"
$grpName="ProjectX-Admins"
Add-MsolGroupMember -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $grpName }).ObjectID -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userCredential.UserName }).ObjectID -GroupMemberType "User"
$grpName="ProjectX-Viewers"
$userUPN="devvp@" + $orgName + ".onmicrosoft.com"
Add-MsolGroupMember -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $grpName }).ObjectID -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupMemberType "User"
```

Результаты:
  
- Группа доступа членов ProjectX содержит привести Designer и привести исследователя учетных записей пользователей
    
- Группа администраторов ProjectX доступа содержит учетной записи глобального администратора для пробной подписки
    
- Группа доступа средства просмотра ProjectX содержит учетная запись вице-президент по разработке
    
На рисунке 1 показано доступа групп и их участия.
  
**Рис. 1**

![Группы Office 365 и их участники для изолированного сайта группы SharePoint Online](media/5b7373b9-2a80-4880-afe5-63ffb17237e6.png)
  
## <a name="phase-3-create-a-new-projectx-sharepoint-online-team-site-and-isolate-it"></a>Этап 3. Создание сайта группы SharePoint Online для ProjectX и его изоляция

Чтобы создать сайт группы SharePoint Online для ProjectX, выполните перечисленные ниже действия.
  
1. С помощью браузера на одного локального компьютера (lightweight конфигурация) или на компьютере CLIENT1 (конфигурация имитации корпоративной) вход на портал Office 365 ([https://portal.office.com](https://portal.office.com)) с помощью учетной записи глобального администратора.
    
2. В списке плиток выберите **SharePoint**.
    
3. На новой вкладке SharePoint в браузере щелкните **+ Создать сайт**.
    
4. В поле **имя сайта группы**введите **ProjectX**. В **Параметры конфиденциальности**, выберите **частный — только для членов можно получить доступ к этот сайт**.
    
5. В поле **Описание сайта группы** введите **Сайт SharePoint для ProjectX** и нажмите кнопку **Далее**.
    
6. На, **который вы хотите добавить**? области, нажмите кнопку **Готово**.
    
7. В новой вкладке **Главная, ProjectX** в браузере, на панели инструментов, щелкните значок параметров и выберите **Разрешения для сайта**.
    
8. В области **Разрешения для сайта** щелкните **Параметры дополнительных разрешений**.
    
9. В новой вкладке **Разрешения: Project X** в браузере нажмите **Параметры запросов на доступ**.
    
10. В диалоговом окне **Параметры запросов на доступ** снимите флажки **Разрешить участникам совместный доступ к этому сайту, а также отдельным файлам и папкам** и **Разрешить запросы на доступ** (все три флажка должны быть сняты) и нажмите кнопку **ОК**.
    
11. Выберите **ProjectX — участники** в списке.
    
12. На странице **Пользователи и группы** нажмите кнопку **Создать**.
    
13. В диалоговом окне **Общий доступ** введите **ProjectX-Members**, выберите группу и нажмите **Поделиться**.
    
14. Нажмите кнопку "Назад" в браузере.
    
15. Выберите **ProjectX — владельцы** в списке.
    
16. На странице **Пользователи и группы** нажмите кнопку **Создать**.
    
17. В диалоговом окне **Общий доступ** введите **ProjectX-Admins**, выберите группу и нажмите **Поделиться**.
    
18. Нажмите кнопку "Назад" в браузере.
    
19. Выберите **ProjectX — посетители** в списке.
    
20. На странице **Пользователи и группы** нажмите кнопку **Создать**.
    
21. В диалоговом окне **Общий доступ** введите **ProjectX-Viewers**, выберите группу и нажмите **Поделиться**.
    
22. Закройте вкладку **Пользователи и группы** в браузере, перейдите на вкладку **Главная, ProjectX** в браузере и закройте область **Разрешения для сайта**.

    
Ниже приведены результаты настройки разрешений.
  
- Группой SharePoint членов ProjectX содержит только группы доступа членов ProjectX (который содержит только привести Designer и привести исследователя учетные записи пользователей) и ProjectX (который содержит только учетная запись пользователя глобального администратора).
    
- Группы владельцев SharePoint ProjectX содержит только ProjectX-доступа к группе "Администраторы" (который содержит только учетная запись пользователя глобального администратора).
    
- Используется группой SharePoint посетителей ProjectX содержит только группу доступа средства просмотра ProjectX (который содержит только учетная запись пользователя вице-президент по разработке).
    
- Участники не могут изменять разрешения на уровне сайта (это могут делать только члены группы ProjectX-Admins).
    
- Другие учетные записи пользователей не могут получить доступ к сайту и его ресурсам и запросить доступ к нему.
    
На рисунке 2 показаны группы SharePoint и их участники.
  
**Рис. 2**

![Группы SharePoint Online и их участники для изолированного сайта группы SharePoint Online](media/595abff4-64f9-49de-a37a-c70c6856936b.png)
  
Теперь давайте демонстрации access с помощью учетной записи пользователя привести конструктора:
  
1. Закройте вкладку **Главная, ProjectX** в браузере и перейдите на вкладку **Домашняя страница Microsoft Office**.
    
2. Щелкните имя глобального администратора и нажмите **Выйти**.
    
3. Войдите в портал Office 365 ([https://portal.office.com](https://portal.office.com)) с помощью конструктора привести имя учетной записи и пароль.
    
4. В списке плиток выберите **SharePoint**.
    
5. На новой вкладке **SharePoint** в браузере в поле «Поиск» введите **ProjectX** активировать поиска и выберите пункт сайт группы **ProjectX** . Вы должны увидеть новую вкладку в браузере для сайта группы ProjectX.
    
6. Щелкните значок параметров. Обратите внимание, что параметр **Разрешения для сайта** отсутствует, так как только члены группы ProjectX-Admins могут изменять разрешения для сайта.
    
7. Откройте приложение "Блокнот" или другой текстовый редактор.
    
8. Скопируйте URL-адрес сайта группы ProjectX и вставьте его в новой строке в приложении "Блокнот" или другом текстовом редакторе.
    
9. На новой вкладке **Главная, ProjectX** в браузере нажмите **Документы**.
    
10. Скопируйте URL-адрес папки документов ProjectX и вставьте его в новой строке в Блокноте или другом текстовом редакторе.
    
11. В новой вкладке **ProjectX — Документы** в браузере нажмите **Создать > Документ Word**.
    
12. Введите текст на странице **Word Online**, дождитесь состояния **Сохранено**, нажмите кнопку "Назад" в браузере и обновите страницу. В папке **Документы** появится новый файл **Документ.docx**.
    
13. Нажмите кнопку с многоточием для документа **Document.docx** и нажмите кнопку **получить ссылку**.
    
14. Скопируйте URL-адрес в диалоговом окне **общий доступ «Document.docx»** и вставьте его на новую строку в блокноте или текстовый редактор, а затем закройте диалоговое окно **«Document.docx» общий доступ** .
    
15. Закройте вкладки **ProjectX — Документы** и **SharePoint** в браузере и перейдите на вкладку **Домашняя страница Microsoft Office**.
    
16. Щелкните имя **ведущего дизайнера** и нажмите **Выйти**.

    
Теперь давайте демонстрации access с помощью учетной записи пользователя вице-президент по разработке:
  
1. Войдите в портал Office 365 ([https://portal.office.com](https://portal.office.com)) с помощью вице-президент по разработке имя учетной записи и пароль.
    
2. В списке плиток выберите **SharePoint**.
    
3. На новой вкладке **SharePoint** в браузере в поле «Поиск» введите **ProjectX** активировать поиска и выберите пункт сайт группы **ProjectX** . Вы должны увидеть новую вкладку в браузере для сайта группы ProjectX.
    
4. Нажмите **Документы** и выберите файл **Документ.docx**.
    
5. Во вкладке **Документ.docx** в браузере попробуйте изменить текст. Вы увидите сообщение о том, что **этот документ доступен только для чтения**, так как у учетной записи вице-президента по развитию есть только разрешения на просмотр сайта.
    
6. Закройте вкладки **Документ.docx**, **ProjectX — Документы** и **SharePoint** в браузере.
    
7. Перейдите на вкладку **Домашняя страница Microsoft Office**, щелкните имя **вице-президента по развитию** и нажмите **Выйти**.

    
Теперь давайте Демонстрация доступ с помощью учетной записи пользователя, которая не имеет разрешений:
  
1. Войдите в портал Office 365 ([https://portal.office.com](https://portal.office.com)) с помощью 3 пользователя имя учетной записи и пароль.
    
2. В списке плиток выберите **SharePoint**.
    
3. 	В новой вкладке **SharePoint** введите **ProjectX** в поле поиска и активируйте поиск. Вы увидите сообщение **Нет результатов, соответствующих вашим условиям поиска**.
    
4. Скопируйте URL-адрес сайта ProjectX из открытого Блокнота или другого текстового редактора в адресную строку браузера и нажмите клавишу **Ввод**. Вы увидите страницу **Доступ запрещен**.
    
5. Скопируйте URL-адрес папки документов ProjectX из Блокнота или другого текстового редактора в адресную строку браузера и нажмите клавишу **Ввод**. Вы увидите страницу **Доступ запрещен**.
    
6. Скопируйте URL-адрес файла Документ.docx из Блокнота или другого текстового редактора в адресную строку браузера и нажмите клавишу **Ввод**. Вы увидите страницу **Доступ запрещен**.
    
7. Закройте вкладку **SharePoint** в браузере, перейдите на вкладку **Домашняя страница Microsoft Office**, щелкните имя **пользователя 3** и нажмите **Выйти**.

    
Изолированный сайта SharePoint Online готов к дополнительные экспериментов.
  
## <a name="next-step"></a>Следующий шаг

Когда вы будете готовы выполнить развертывание изолированного сайта группы SharePoint Online в рабочей среде, просмотрите подробные инструкции из статьи [Разработка изолированного сайта группы SharePoint Online](design-an-isolated-sharepoint-online-team-site.md).
  
## <a name="see-also"></a>См. также

[Изолированные сайты групп SharePoint Online](isolated-sharepoint-online-team-sites.md)
  
[Руководства по созданию сред разработки и тестирования облачных решений](cloud-adoption-test-lab-guides-tlgs.md)
  
[Базовая конфигурация среды разработки и тестирования](base-configuration-dev-test-environment.md)
  
[Среда разработки и тестирования Office 365](office-365-dev-test-environment.md)
  
[Освоение облака и гибридные решения](cloud-adoption-and-hybrid-solutions.md)




