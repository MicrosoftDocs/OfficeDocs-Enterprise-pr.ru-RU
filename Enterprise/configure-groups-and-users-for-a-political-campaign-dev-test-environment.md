---
title: "Настройка групп и пользователей для среды разработки и тестирования политической кампании"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: None
ms.custom:
- DecEntMigration
- Strat_O365_Enterprise
ms.assetid: 0e22bcf3-bad3-42a4-b44f-276e0cf4790f
description: "Сводка: Создание Office 365 и мобильных устройств предприятия + безопасности (Командной) пробной подписки с пользователями и группами в среде разработки и тестирования политических кампании."
ms.openlocfilehash: 7faf428fc2225d3f31297ba6bf83a10a7682009a
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2017
---
# <a name="configure-groups-and-users-for-a-political-campaign-devtest-environment"></a>Настройка групп и пользователей для среды разработки и тестирования политической кампании

 **Сводка:** Создайте Office 365 и мобильных устройств предприятия + безопасности (Командной) пробной подписки с пользователями и группами в среде разработки и тестирования политических кампании.
  
Для создания среды разработки или тестирования, которая включает в себя упрощенный учетных записей и групп для решения [Майкрософт по обеспечению безопасности политических по сбору средств, некоммерческим организациями и другие гибкой организации](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md) , используйте инструкции в данной статье.
  
## <a name="phase-1-create-your-office-365-devtest-environment"></a>Этап 1. Создание среды разработки и тестирования Office 365

На этом этапе получения пробной подписки для Office 365 E5 и мобильных устройств предприятия + E5 безопасности (Командной) для вымышленной организации, представляющий политических кампании.
  
Во-первых следуйте инструкциям в **Этап 2** в [Office 365 dev/тестовой среды](office-365-dev-test-environment.md).
  
Затем регистрация для пробной подписки Командной E5 и добавить его в той же организации, что пробной подписки Office 365.
  
1. При необходимости, войдите в портал Office 365 с использованием учетных данных учетной записи глобального администратора пробной подписки. Дополнительные сведения см [Where для входа в Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Щелкните плитку **администрирования** .
    
3. На вкладке **центра администрирования Office** в браузере на панели навигации слева щелкните **выставления счетов > службы приобретения**.
    
4. На странице " **службы приобретения** " Поиск элемента **мобильной работы предприятия + E5 безопасности** . Наведите указатель мыши на его и нажмите кнопку **Пуск бесплатную пробную версию**.
    
5. На странице " **Подтверждение заказа** " щелкните **Теперь попробуйте**.
    
6. На странице **получения заказа** нажмите кнопку **Продолжить**.
    
Рассмотрим процедуру включения E5 Командной лицензии для учетной записи глобального администратора.
  
1. На вкладке **Центр администрирования Office 365** в браузере на панели навигации слева щелкните **Пользователи > Активные пользователи**.
    
2. Выберите учетную запись глобального администратора и нажмите кнопку **Изменить** для **лицензий на продукт**.
    
3. В области **лицензий на продукт** включить лицензии для **мобильных устройств предприятия + E5 безопасности** для **на**, нажмите кнопку **Сохранить** и дважды нажмите кнопку **Закрыть** .
    
## <a name="phase-2-create-and-configure-your-azure-active-directory-ad-groups"></a>Этап 2. Создание и настройка групп Azure Active Directory (AD)

На этом этапе создаются и настраиваются группы Azure AD для кампании.
  
Во-первых создайте набор групп для обычной политических кампании с порталом Azure.
  
1. На отдельной вкладке в браузере перейдите на портале Azure по [https://portal.azure.com](https://portal.azure.com). При необходимости вход с помощью учетных данных учетной записи глобального администратора для пробной подписки Office 365 E5.
    
2. На портале Azure щелкните **Azure Active Directory > пользователи и группы > все группы**.
    
3. Выполните следующие действия для каждого имени группы в этом списке:
    
  - Старший и стратегический персонал
    
  - ИТ-персонал
    
  - Специалисты по аналитике
    
  - Основной персонал
    
  - Оперативный персонал
    
  - Выездной персонал
    
1. На blade **все группы** нажмите кнопку **+ новую группу**.
    
2. В поле **имя**введите имя группы в списке.
    
3. Выберите **динамических пользователя** **членства**.
    
4. Для **включения Office компонентов**, нажмите кнопку **Да** .
    
5. Нажмите кнопку **Добавить динамический запрос**.
    
6. В **Добавление пользователей где**, выберите **отдела**.
    
7. В следующем поле выберите **равно**.
    
8. В следующем поле введите имя группы в списке.
    
9. Нажмите кнопку **Добавить запрос**и затем нажмите кнопку **Создать**.
    
10. Выберите **пользователей и групп — все группы**.
    
Далее следует настроить группы, чтобы участники автоматически назначаются лицензии Office 365 E5 и E5 Командной.
  
1. На портале Azure щелкните **Azure Active Directory > лицензий > всех продуктов**.
    
2. В списке выберите **Enterprise мобильности + E5 безопасности** и **Office 365 корпоративный E5**и нажмите кнопку **+ Назначение**.
    
3. В blade **Назначение лицензии** нажмите кнопку **пользователи и группы**.
    
4. В списке выберите следующие группы:
    
  - Специалисты по аналитике
    
  - Выездной персонал
    
  - ИТ-персонал
    
  - Оперативный персонал
    
  - Основной персонал
    
  - Старший и стратегический персонал
    
5. Нажмите кнопку **выбрать**и нажмите кнопку **назначить**.
    
6. Закройте вкладку портала Azure в браузере.
    
## <a name="phase-3-add-your-user-accounts"></a>Этап 3. Добавление учетных записей пользователей

На этом этапе добавляются демонстрационные учетные записи пользователей для политической кампании.
  
Во-первых, можно [подключить с помощью модуля Azure Active Directory версии 2 PowerShell](https://go.microsoft.com/fwlink/?linkid=842218).
  
Затем введите название организации, адрес и общий пароль и выполните эти команды в командной строке PowerShell или интегрированной среде сценариев (ISE):
  
```
$orgName="<organization name, such as contoso for the contoso.onmicrosoft.com trial subscription domain name>"
$location="<the ISO ALPHA2 country code, such as US for the United States>"
$commonPassword="<common password for all the new accounts>"

$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password=$commonPassword

$deptName="Senior and strategic staff"
$userNames=@("Candidate","ChiefOfStaff","Strategic1") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="IT staff"
$userNames=@("ITAdmin1","ITAdmin2") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Analytics staff"
$userNames=@("DataScientist1") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Regular core staff"
$userNames=@("Regular1","Regular2") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Operations staff"
$userNames=@("Operations1") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Field staff"
$userNames=@("FieldConsultant1") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }

```

> [!IMPORTANT]
> Общий пароль используется для автоматизации и удобства настройки в среде разработки или тестирования. Не рекомендуется для производственных подписок. При входе с каждой из этих новых учетных записей пользователя, будет предложено изменить пароль. 
  
Чтобы проверить работу динамического членства в группах и группового лицензирования, сделайте следующее:
  
1. На вкладке **Microsoft Office для дома** браузера щелкните плитку **администрирования** .
    
2. На вкладке **центра администрирования Office** нового обозревателя щелкните **Пользователи**.
    
3. В списке пользователей выберите **кандидата**.
    
4. В области, где перечислены свойства учетной записи пользователя **кандидата** убедитесь, что:
    
  - Это должна быть членом группы **старший и стратегического персонала** (в **группах**).
    
  - Она была назначена лицензий **Enterprise мобильности + E5 безопасности** и **Office 365 корпоративный E5** (в **лицензий продукта**).
    
5. Закройте область учетной записи пользователя **кандидата** .
    
## <a name="record-values-for-future-reference"></a>Запишите значения для дальнейшего использования

Запишите эти значения для работы с пробными подписками Office 365 и EMS для этой среды разработки и тестирования:
  
- Название вашей организации: _______________________________________________  
    
    Например, для доменного имени contoso.onmicrosoft.com название организации — "contoso".
    
- Имя глобального администратора Office 365: ___.onmicrosoft.com
    
    Запишите пароль для этой учетной записи и общие исходный пароль для других учетных записей пользователей в надежном месте.
    
## <a name="next-step"></a>Следующее действие

Создание четырех различных типов SharePoint Online веб-сайтов групп в этой среде разработки и тестирования с [сайтами групп создать в среде разработки и тестирования политических кампании](create-team-sites-in-a-political-campaign-dev-test-environment.md).
  
## <a name="see-also"></a>See Also

[Руководство по безопасности (Майкрософт) для политических кампаний, некоммерческих и других динамических организаций](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[Создание веб-сайтов групп в среде разработки и тестирования политических кампаний (en)](create-team-sites-in-a-political-campaign-dev-test-environment.md)
  
[Руководства по лаборатории тестирования для принятия облачных решений](cloud-adoption-test-lab-guides-tlgs.md)
  
[Освоение облака и гибридные решения](cloud-adoption-and-hybrid-solutions.md)




