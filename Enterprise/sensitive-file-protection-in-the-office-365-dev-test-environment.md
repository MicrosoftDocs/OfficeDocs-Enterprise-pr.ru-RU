---
title: "Защита конфиденциальных файлов в среде разработки и тестирования Office 365"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Top
ms.custom:
- DecEntMigration
- jan17entnews
- TLG
- Ent_TLGs
ms.assetid: 27ecff45-06a6-4629-bc45-9dab4eef3a21
description: "Сводка: Настройка и демонстрация Office 365 Information Rights Management защите конфиденциальных файлов, даже если они учтены неверный семейства сайтов SharePoint Online."
ms.openlocfilehash: a6547cf4327980e3909323d5bda4455dfffd37f4
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2017
---
# <a name="sensitive-file-protection-in-the-office-365-devtest-environment"></a>Защита конфиденциальных файлов в среде разработки и тестирования Office 365

 **Сводка:** Настройка и демонстрация Office 365 Information Rights Management защите конфиденциальных файлов, даже если они учтены неверный семейства сайтов SharePoint Online.
  
Управление правами на доступ к данным (IRM) в Office 365 — это набор функций для защиты документов, скачиваемых из списков и библиотек SharePoint Online. Скачиваемые файлы зашифрованы и содержат те же разрешения на открытие, копирование, сохранение и печать, которые настроены в библиотеке SharePoint Online, в которой они хранились.
  
В этой статье описано, как включить и протестировать IRM в Office 365 для файлов, содержащих потенциально конфиденциальную информацию, в пробной подписке на Office 365.
  
> [!TIP]
> Щелкните [здесь](http://aka.ms/catlgstack), чтобы просмотреть схему всех статей, относящихся к руководствам по лаборатории тестирования Microsoft Cloud.
  
## <a name="phase-1-build-out-your-office-365-devtest-environment"></a>Этап 1. Создание среды разработки и тестирования Office 365

Если необходимо проверить защита конфиденциальных файлов в облегченный путь с минимальным требованиям, следуйте инструкциям в этапы 2 и 3 [Office 365 dev/тестовой среды](office-365-dev-test-environment.md).
  
Если вы хотите проверить защита конфиденциальных файлов в имитации enterprise, следуйте инструкциям в [DirSync для вашей среды разработки или тестирования Office 365](dirsync-for-your-office-365-dev-test-environment.md).
  
> [!NOTE]
> Для тестирования не требуется условная корпоративная среда разработки и тестирования, которая включает условную интрасеть, подключенную к Интернету, и синхронизацию каталогов для леса Windows Server AD. Она показана здесь лишь для того, чтобы вы могли протестировать защиту конфиденциальных файлов и поэкспериментировать с этим компонентом в типичной для организаций среде. 
  
## <a name="phase-2-demonstrate-how-documents-from-permissions-protected-sites-can-be-leaked"></a>Этап 2. Демонстрация утечки документов с сайтов, защищенных системой прав доступа

На этом этапе демонстрируется, что пользователь может скачать документ с сайта, защищенного системой прав доступа, а затем отправить его на незащищенный сайт.
  
Для начала создайте три новых учетных записи пользователя для руководителей и назначьте им лицензии Office 365 E5.
  
Используйте инструкции из статьи Установка PowerShell модули (при необходимости) и подключиться к новой подписки Office 365 через [подключение к Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx) :
  
- компьютера (для упрощенной среды разработки и тестирования Office 365);
    
- виртуальной машины CLIENT1 (для среды Office 365 для разработки и тестирования смоделированного предприятия).
    
В диалоговом окне **Запрос учетных данных Windows PowerShell** введите имя глобального администратора Office 365 (пример: jdoe@contosotoycompany.onmicrosoft.com) и пароль для пробной подписки Office 365.
  
Введите название организации (например, contosotoycompany) и двузначный код страны, а затем выполните следующие команды в командной строке модуля Windows Azure Active Directory для Windows PowerShell:
  
```
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$licAssignment= $orgName + ":ENTERPRISEPREMIUM"
$userName= "ceo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "CEO" -FirstName "Chief" -LastName "Executive Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

Отображение команду **New-MsolUser** Обратите внимание, созданный пароль для учетной записи генеральный Директор и запишите его в надежном месте.
  
Выполните следующие команды в командной строке модуля Windows Azure Active Directory для Windows PowerShell:
  
```
$userName= "cfo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "CFO" -FirstName "Chief" -LastName "Financial Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

Отображение команду **New-MsolUser** Обратите внимание, созданный пароль для учетной записи финансового Директора и запишите его в надежном месте.
  
Выполните следующие команды в командной строке модуля Windows Azure Active Directory для Windows PowerShell:
  
```
$userName= "coo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "COO" -FirstName "Chief" -LastName "Operations Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

Отображение команду **New-MsolUser** Обратите внимание, созданный пароль для учетной записи работе исполнительного Директора и запишите его в надежном месте.
  
Теперь создайте закрытую группу "Руководители" и добавьте в нее новые учетные записи.
  
1. В браузере перейдите на портале Office по [http://portal.office.com](http://portal.office.com) и войдите пробной подписки Office 365 с учетной записью глобального администратора.
    
  - Если вы используете упрощенную среду разработки и тестирования Office 365, запустите частный сеанс Internet Explorer или вашего браузера и войдите с локального компьютера.
    
  - Если вы используете условную корпоративную среду разработки и тестирования Office 365, подключитесь к виртуальной машине CLIENT1 с помощью портала Azure, а затем войдите с этой виртуальной машины.
    
2. На вкладке **Microsoft Office для дома** щелкните **администрирования > группы > группы**и нажмите кнопку **Добавить группу**.
    
3. В диалоговом окне **Добавить группу**выберите **группу, Office 365** для типа группы, введите в поле **имя** и **Идентификатор группы**, **руководителями** выберите **частный** для **обеспечения конфиденциальности**и нажмите кнопку **Выберите владельца**.
    
4. Выберите имя учетной записи глобального администратора из списка.
    
5. Нажмите кнопку **Добавить**и нажмите кнопку **Закрыть**.
    
6. В списке группы выберите **руководителей**.
    
7. Нажмите кнопку **изменить для членов**.
    
8. Нажмите кнопку **Добавить элементы**. В списке элементов выберите следующие учетные записи пользователей:
    
  - генеральный директор;
    
  - финансовый директор;
    
  - главный операционный директор.
    
9. Нажмите кнопку **Сохранить**и нажмите кнопку **Закрыть**.
    
10. Закройте вкладку **Центр администрирования Office** .
    
Теперь создайте семейство веб-сайтов "Руководители" и предоставьте к нему доступ только участникам этой группы.
  
1. На вкладке **Microsoft Office для дома** щелкните плитку **администрирования** .
    
2. На вкладке **центра администрирования Office** щелкните **центры администрирования > SharePoint**.
    
3. На вкладке **Центр администрирования SharePoint** щелкните **Создать > закрытый семейства**.
    
4. В области семейства сайтов введите **руководителей** в поле **Название**руководителей в поле URL-адреса укажите имя учетной записи глобального администратора в **администратора**и нажмите кнопку **ОК**.
    
5. Подождите, пока создания нового семейства сайтов. Закончив настройку, скопируйте URL-адрес нового семейства сайтов для руководителей и вставьте его в новую вкладку браузера.
    
6. В правом верхнем углу **руководители** семейства веб-сайтов щелкните значок параметры и выберите **общий доступ**.
    
7. В **папке «Руководители»**нажмите кнопку **Дополнительно**.
    
8. В список групп SharePoint щелкните **Элементы руководителей**.
    
9. На странице " **пользователи и группы** " нажмите кнопку **Создать**.
    
10. В поле **общий доступ «Руководители»**введите **руководители**, щелкните группу, **руководители** и нажмите кнопку **совместный доступ**.
    
11. Закройте вкладку **пользователи и группы** .
    
Теперь предоставьте всем пользователям доступ к семейству веб-сайтов "Продажи".
  
1. Откройте вкладку **Центр администрирования SharePoint** и скопируйте URL-адрес семейства сайтов, продажи и вставьте его в новую вкладку браузера...
    
2. В правом верхнем углу щелкните значок параметры и выберите **общий доступ**.
    
3. В поле **общий доступ «Продажи семейства веб-сайтов»**нажмите кнопку **Дополнительно**.
    
4. В списке групп SharePoint нажмите кнопку **члены семейства веб-сайтов продаж**.
    
5. На странице " **пользователи и группы** " нажмите кнопку **Создать**.
    
6. В **папке «Продажи семейства веб-сайтов»**введите **все**, щелкните **все, кроме внешних пользователей**и нажмите кнопку **общий доступ**.
    
7. Закройте вкладки **продаж семейства сайтов** и **SharePoint** .
    
Затем войдите в учетную запись руководителя и создайте документ в семействе веб-сайтов "Руководители".
  
1. На вкладке **Microsoft Office для дома** щелкните значок пользователя в правом верхнем углу и выберите команду **Выход**.
    
2. Перейдите к [http://portal.office.com](http://portal.office.com).
    
3. На странице **входа Office 365** выберите **использовать другую учетную запись**.
    
4. Введите имя **CEO** учетной записи и пароль и нажмите кнопку **Вход**.
    
5. На новой вкладке браузера введите URL-адрес семейства веб-сайтов руководителей ( **https://**\<название организации >**.sharepoint.com/sites/executives**).
    
6. Щелкните **документы**, нажмите кнопку **Создать** и выберите **Документ Word**.
    
7. Щелкните в строке заголовка и введите **SensitiveData BeforeIRM**.
    
8. Щелкните в теле документа и введите **минут из последних доска собрания**и нажмите кнопку **руководителей**.
    
     Вы должны увидеть **SensitiveData BeforeIRM.docx** в папку « **документы** ».
    
Теперь скачайте локальную копию документа SensitiveData-BeforeIRM.docx и случайно опубликуйте ее в семействе веб-сайтов "Продажи".
  
1. На локальном компьютере, создать новую папку (например, C:\\руководствам\\SensitiveDataTestFiles).
    
2. На вкладке **документы** в браузере выберите **SensitiveData BeforeIRM.docx** документ, нажмите кнопку с многоточием и нажмите кнопку **загрузить**.
    
3. Хранение документов **SensitiveData BeforeIRM.docx** в папке, созданной на шаге 1.
    
4. На новой вкладке браузера введите URL-адрес семейства веб-сайтов продаж ( **https://**\<название организации >**.sharepoint.com/sites/sales**).
    
5. Щелкните папку « **документы** » из **семейства сайтов продаж**.
    
6. Нажмите кнопку **Отправить**и затем укажите **SensitiveData BeforeIRM.docx** документа в папке, созданной на шаге 1 и нажмите кнопку **ОК**.
    
7. Убедитесь, что документ **SensitiveData BeforeIRM.docx** в папку « **документы** ».
    
8. Закройте вкладки **продажи** и **SharePoint** .
    
После этого войдите в учетную запись User5 и откройте документ SensitiveData-BeforeIRM.docx в семействе веб-сайтов "Продажи".
  
1. На вкладке **Microsoft Office для дома** щелкните значок пользователя в правом верхнем углу и выберите команду **Выход**.
    
2. Перейдите к [http://portal.office.com](http://portal.office.com).
    
3. На странице **входа Office 365** выберите **использовать другую учетную запись**.
    
4. Введите имя учетной записи User5 и пароль и нажмите кнопку **Вход**.
    
5. На новой вкладке браузера введите URL-адрес семейства веб-сайтов продаж.
    
6. В папке **документы** **продажи семейство сайтов**нажмите кнопку **SensitiveData BeforeIRM.docx** документа.
    
    Появится его содержимое.
    
7. Закройте вкладки **документов** и **продажи семейства сайтов** .
    
Случайно опубликовав документ SensitiveData-BeforeIRM.docx в семействе веб-сайтов "Продажи", генеральный директор обошел систему прав доступа семейства веб-сайтов "Руководители".
  
Чтобы подготовить Office 365 к этапам 3 и 4, включите IRM для SharePoint Online.
  
1. На вкладке **Microsoft Office для дома** щелкните значок пользователя в правом верхнем углу и выберите команду **Выход**.
    
2. Перейдите к [http://portal.office.com](http://portal.office.com).
    
3. На странице **входа Office 365** щелкните имя учетной записи глобального администратора, введите пароль и затем нажмите кнопку **Вход**.
    
4. На вкладке **Microsoft Office для дома** щелкните **администрирования > центры администрирования > SharePoint**.
    
5. На вкладке **Центр администрирования SharePoint** щелкните **Параметры**.
    
6. На странице " **Параметры** " в разделе **Управление правами на доступ к данным (IRM)** выберите **с помощью службы IRM, указанного в конфигурации**и выберите пункт **Обновить параметры IRM**.
    
7. Закройте вкладку **Центр администрирования SharePoint** .
    
## <a name="phase-3-use-sharepoint-information-rights-management-with-an-office-365-private-group"></a>Этап 3. Использование управления правами на доступ к данным SharePoint с закрытой группой Office 365

На этом этапе используется управление правами на доступ к данным SharePoint с закрытой группой Office 365, чтобы защитить документ с конфиденциальной информацией, даже если он опубликован на сайте с открытым доступом.
  
Для начала включите и настройте IRM для библиотеки документов семейства веб-сайтов "Руководители".  
  
1. На новой вкладке браузера введите URL-адрес для руководителей семейства веб-сайтов.
    
2. Щелкните **документы**.
    
3. В правом верхнем углу щелкните значок параметры и нажмите кнопку **Параметры библиотеки**.
    
4. На странице " **Параметры** " в разделе **разрешения и управление**, щелкните **Управление правами на доступ**.
    
5. На странице **Параметры управления правами сведениями** :
    
  - Выберите **ограничить разрешения для документов этой библиотеки при загрузке**.
    
  - Для **создания название политики разрешений**введите **руководителей**.
    
  - В поле **Добавить описание политики разрешений**, введите **IRM для руководителей**.
    
6. Щелкните **Показать параметры**.
    
7. В разделе **Задайте дополнительные параметры библиотеки IRM**выберите **не разрешать пользователям загружать документы, которые не поддерживают IRM**.
    
8. В разделе **права доступа Configure документа**выберите **Разрешить средства просмотра для печати** и **Разрешить средства просмотра для записи копии загруженного документа**.
    
9. В разделе **Настройка защиты группы и интервал учетные данные**выберите **Разрешить группы защиты** и **Группа по умолчанию**, введите **руководителей**.
    
10. Нажмите кнопку **ОК**.
    
Затем отправьте новый документ в папку документов "Руководители" от имени генерального директора, скачайте его и ошибочно отправьте в папку документов "Продажи".
  
1. Откройте локальный папка для хранения документов **SensitiveData BeforeIRM.docx** .
    
2. Щелкните правой кнопкой мыши **SensitiveData BeforeIRM.docx**и выберите команду **Копировать**.
    
3. Щелкните правой кнопкой мыши папку и выберите команду **Вставить**.
    
4. Измените имя нового файла **SensitiveData-BeforeIRM - Copy.docx** на **SensitiveData AfterIRM.docx**.
    
5. В браузере откройте вкладку **Microsoft Office для дома** и щелкните значок пользователя в правом верхнем углу и нажмите кнопку **Выход**.
    
6. Перейдите к [http://portal.office.com](http://portal.office.com).
    
7. На странице **входа Office 365 в** щелкните имя учетной записи CEO, введите пароль и затем нажмите кнопку **Вход**.
    
8. На новой вкладке браузера введите URL-адрес для руководителей семейства веб-сайтов.
    
9. На странице " **документы** " нажмите кнопку **Отправить**, укажите **SensitiveData AfterIRM.docx** документа в локальную папку и нажмите кнопку **Открыть**.
    
10. Выберите новый документ **SensitiveData AfterIRM.docx** на странице " **документы** ", нажмите кнопку с многоточием (...) в строке меню и нажмите кнопку **загрузить**.
    
11. При появлении соответствующего запроса сохраните документ **SensitiveData AfterIRM.docx** в локальной папке, перезаписью исходной версии.
    
12. Закройте вкладку страницы **документов** .
    
13. На новой вкладке браузера введите URL-адрес семейства веб-сайтов продаж.
    
14. Щелкните **документы**.
    
15. На странице " **документы** " нажмите кнопку **Отправить**, укажите **SensitiveData AfterIRM.docx** документа в локальную папку и нажмите кнопку **Открыть**.
    
16. Закройте вкладки **продаж семейства сайтов** и **SharePoint** .
    
Далее будет действовать как обычный пользователь, вы попытаетесь обратиться к **SensitiveData AfterIRM.docx** документа в папке документов продажи.
  
1. В браузере откройте вкладку **Microsoft Office для дома** и щелкните значок пользователя в правом верхнем углу и нажмите кнопку **Выход**.
    
2. Перейдите к [http://portal.office.com](http://portal.office.com).
    
3. На странице **входа Office 365** щелкните имя учетной записи User5, введите пароль и затем нажмите кнопку **Вход**.
    
4. На новой вкладке браузера введите URL-адрес семейства веб-сайтов продаж.
    
5. Щелкните **документы**.
    
6. На странице " **документы** " открываете документ **SensitiveData AfterIRM.docx** .
    
    Появится сообщение "К сожалению, Word Online не может открыть этот документ, так как он защищен службой управления правами на доступ к данным (IRM)."  
    
7. Нажмите кнопку **"Изменить" в Word**. Приглашение, чтобы открыть файл. Нажмите кнопку **Да**.
    
8. Вам будет предложено входа введите имя учетной записи для учетной записи User5, а затем нажмите кнопку **Далее**.
    
9. Будет предложено ввести пароль. Введите пароль для учетной записи User5 и нажмите кнопку **Вход**. 
    
    Появится такое сообщение: "Ваши учетные данные не позволяют вам открыть этот документ."
    
10. Нажмите кнопку **Нет**.
    
Другой способ просмотра защиту IRM — просматривать файлы в локальной папке. **SensitiveData AfterIRM.docx** должно быть значительно больше **SensitiveData BeforeIRM.docx** файла. Файл **SensitiveData AfterIRM.docx** зашифрован и добавил данные защиту IRM к нему.
  
## <a name="see-also"></a>See Also

[Руководства по лаборатории тестирования для принятия облачных решений](cloud-adoption-test-lab-guides-tlgs.md)
  
[Базовая конфигурация среды разработки и тестирования](base-configuration-dev-test-environment.md)
  
[Среда разработки и тестирования Office 365](office-365-dev-test-environment.md)
  
[Освоение облака и гибридные решения](cloud-adoption-and-hybrid-solutions.md)

