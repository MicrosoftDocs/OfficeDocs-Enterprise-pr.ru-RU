---
title: Взаимодействие между клиентами Office 365
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 6/28/2018
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
search.appverid:
- MET150
- MOE150
ms.assetid: eb45fd8b-1d5d-4b0c-9c5a-479dbb176e7d
description: Узнайте, как совместной работы Office 365 работает между клиентами и организациями.
ms.openlocfilehash: 932c837f9dc09dd0469a17ad4e6a05f09966d29c
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542369"
---
# <a name="office-365-inter-tenant-collaboration"></a>Взаимодействие между клиентами Office 365

В этой статье описываются несколько способов совместной работы между двумя клиентов Office 365. Предназначена для администраторов Office 365.
  
Предположим, что организациями, Fabrikam и Contoso, имеющих Office 365 для бизнеса клиента, и они хотят работать вместе с несколькими проектами; Некоторые из которых работают в течение ограниченного времени и некоторые из них текущего. Как Fabrikam и Contoso включить людей и групп для совместной работы более эффективно их различных клиентов Office 365 в безопасном режиме? Office 365, вместе с Azure Active Directory B2B совместной работы, предоставляет несколько вариантов. В этой статье описываются несколько ключевых сценариев, которые могут быть полезны Fabrikam и Contoso.
  
Включить параметры совместной работы между клиентом Office 365 с помощью центрального расположения для файлов и беседы, общий доступ к календарям, обмена мгновенными Сообщениями, аудио и видео на звонки для обмена данными и обеспечение безопасности доступа к ресурсам и приложениям. Используйте следующую таблицу для выбора решения и Дополнительные сведения.
  
## <a name="exchange-online-collaboration-options"></a>Exchange Online параметры совместной работы

|**Цель общего доступа**|**Функции администрирования**|**Инструкции**|
|:-----|:-----|:-----|
|Совместное использование календарей с другой организацией Office 365  <br/> |Администраторы могут настроить различные уровни доступа к календарю в Exchange Online, чтобы разрешить следующие преимущества для совместной работы с другой предприятиями и пользователи могут совместно использовать расписания (сведения о доступности) с другими пользователями  <br/> |[Поиск в Exchange Online](https://technet.microsoft.com/en-us/library/jj916670%28v=exchg.150%29.aspx) <br/> [Связи организации в Exchange Online](https://technet.microsoft.com/en-us/library/jj916658%28v=exchg.150%29.aspx) <br/> [Создание связи организации в Exchange Online](https://technet.microsoft.com/en-us/library/jj916671%28v=exchg.150%29.aspx) <br/> [Изменение и связи организации в Exchange Online](https://technet.microsoft.com/en-us/library/jj916659%28v=exchg.150%29.aspx) <br/> [Удаление связи организации в Exchange Online](https://technet.microsoft.com/en-us/library/jj916657%28v=exchg.150%29.aspx) <br/> [Совместное использование календарей с внешними пользователями](https://support.office.com/article/fb00dd4e-2d5f-4e8d-8ff4-94b2cf002bdd) <br/> |
|Контролировать, как пользователи совместно использовать их календарей с людьми за пределами вашей организации  <br/> |Администраторы применения политик общего доступа к почтовым ящикам пользователей для пользователей, которые можно использовать совместно с и уровень доступа, предоставленный  <br/> |[Совместное использование политик в Exchange Online](https://technet.microsoft.com/en-us/library/jj916673%28v=exchg.150%29.aspx) <br/> [Создание политики общего доступа в Exchange Online](https://technet.microsoft.com/en-us/library/jj916676%28v=exchg.150%29.aspx) <br/> [Применение политики общего доступа к почтовым ящикам в Exchange Online](https://technet.microsoft.com/en-us/library/jj916672%28v=exchg.150%29.aspx) <br/> [Изменение, отключение или удаление политики общего доступа в Exchange Online](https://technet.microsoft.com/en-us/library/jj916674%28v=exchg.150%29.aspx) <br/> |
|Настройка каналов защиты электронной почты и управления потоком почты партнерские организации  <br/> |Администраторы создание соединителей для защиты обмена почты с партнерской организации или поставщика услуг. Соединители принудительное применение шифрования через протокол TLS (TLS) и создания ограничения на имена доменов и партнеры отправки электронной почты из диапазонов IP-адресов.  <br/> |[Использование протокола TLS службой Exchange Online для защиты электронной почты в Office 365](https://technet.microsoft.com/en-us/library/mt163898.aspx) <br/> [Configure mail flow using connectors in Office 365](https://technet.microsoft.com/en-us/library/ms.exch.eac.connectorselection%28v=exchg.150%29.aspx) <br/> [Удаленные домены в Exchange Online](https://technet.microsoft.com/en-us/library/jj966211%28v=exchg.150%29.aspx) <br/> [Настроить соединитель для защиты потока электронной почты с партнерской организации](https://technet.microsoft.com/en-us/library/dn751021%28v=exchg.150%29.aspx) <br/> [Рекомендации по потоку обработки почты для Exchange Online и Office 365 (обзор)](https://technet.microsoft.com/en-us/library/0e6cd9d5-ad3e-418a-8ea9-3bf33332c491%28v=exchg.150%29) <br/> |
   
## <a name="sharepoint-online-and-onedrive-for-business-collaboration-options"></a>SharePoint Online и OneDrive для бизнеса параметры совместной работы

|**Общий доступ к цели**|**Функции администрирования**|**Инструкции**|
|:-----|:-----|:-----|
|Совместное использование сайтов и документов с внешними пользователями  <br/> |Администраторы настраивают общего доступа в клиента или уровне семейства сайтов для учетной записи Майкрософт прошедшим проверку подлинности, рабочий или школа учетная запись прошедшего проверку подлинности или гостя учетные записи  <br/> |
  [Управление внешним доступом для среды SharePoint Online](https://support.office.com/en-US/article/Manage-external-sharing-for-your-SharePoint-Online-environment-C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85?ui=en-US&amp;rs=en-US&amp;ad=US) <br/> [Ограниченное доменов, совместное использование в Office 365 SharePoint Online и OneDrive для бизнеса](https://support.office.com/en-US/article/Restricted-Domains-Sharing-in-Office-365-SharePoint-Online-and-OneDrive-for-Business-5d7589cd-0997-4a00-a2ba-2320ec49c4e9) <br/> [Использовать SharePoint Online в качестве внешнего решения бизнес business (B2B)](https://support.office.com/article/7b087413-165a-4e94-8871-4393e0b9c037) <br/> |
|Отслеживание и управление внешний общий доступ для конечных пользователей  <br/> |Настройка сайта и общий доступ к документам и внедрить уведомления для отслеживания общего доступа к OneDrive для бизнеса файл владельцев и SharePoint Online конечных пользователей  <br/> |[Настройка уведомлений для внешних общего доступа к службе OneDrive для бизнеса](https://support.office.com/en-US/article/Configure-notifications-for-external-sharing-for-OneDrive-for-Business-b640c693-f170-4227-b8c1-b0a7e0fa876b) <br/> [Общий доступ к файлам и папкам SharePoint в Office 365](https://support.office.com/article/1fe37332-0f9a-4719-970e-d2578da4941c) <br/> |
   
## <a name="skype-for-business-collaboration-options"></a>Скайп для доступа к параметрам совместной работы бизнеса

|**Цель общего доступа**|**Функции администрирования**|**Инструкции**|
|:-----|:-----|:-----|
|Скайп для бизнеса в Интернет - обмена мгновенными Сообщениями, звонки и сведений о присутствии с другими Скайп для бизнес-пользователи  <br/> |Администраторы могут включить их Скайп Business Online пользователям для обмена мгновенными Сообщениями, совершать звонки аудио и видео и просматривать сведения о присутствии с пользователями в другом клиента Office 365.  <br/> |[Разрешить пользователям контактов внешних Скайп для бизнес-пользователи](https://support.office.com/article/b414873a-0059-4cd5-aea1-e5d0857dbc94) <br/> |
|Скайп для бизнеса в Интернет - обмена мгновенными Сообщениями, звонки и сведений о присутствии с пользователями Скайп (получатель)  <br/> |Администраторы могут включить их Скайп Business Online пользователям для обмена мгновенными Сообщениями, совершать звонки и просматривать сведения о присутствии с пользователями Скайп (получатель).  <br/> |[Сообщите Скайп для бизнес-пользователям добавлять контакты Скайп](https://support.office.com/article/08666236-1894-42ae-8846-e49232bbc460) <br/> |
   
## <a name="azure-ad-b2b-collaboration-options"></a>Параметры Azure AD B2B совместной работы

|**Цель общего доступа**|**Функции администрирования**|**Инструкции**|
|:-----|:-----|:-----|
|Azure AD B2B совместная работа — общий доступ к путем добавления внешних пользователей в группу в каталоге организации контента  <br/> |Глобальный администратор для одного клиента Office 365 можно приглашать людей в другой клиента Office 365 их каталогу Добавление этих внешних пользователей в группу и предоставление доступа к контенту, например сайтов SharePoint и библиотеки для группы.  <br/> |[Что такое Предварительный просмотр Azure AD B2B совместной работы?](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-b2b-what-is-azure-ad-b2b) <br/> [Azure AD B2B: Новые обновления упростить между предприятиями исключения](https://blogs.technet.microsoft.com/enterprisemobility/2017/02/01/azure-ad-b2b-new-updates-make-cross-business-collab-easy/) <br/> [Внешний общий доступ к Office 365 и Azure Active Directory B2B совместной работы](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-b2b-o365-external-user) <br/> [Совместная работа Azure Active Directory B2B API и параметры настройки](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-b2b-api) <br/> [Azure AD и Показать удостоверения: совместная работа Azure AD B2B (Business для бизнеса](https://channel9.msdn.com/Series/Azure-AD-Identity/AzureADB2B) <br/> |
   
## <a name="office-365-collaboration-options"></a>Параметры совместной работы Office 365

|**Цель общего доступа**|**Функции администрирования**|**Инструкции**|
|:-----|:-----|:-----|
|Office 365 групп — электронной почты, календарь, OneNote и общие файлы в централизованный доступ  <br/> |Группы поддерживаются в Business Essentials, бизнеса расширенный, образовательных учреждений и планы Enterprise E1, E3 и E5. Пользователи в один клиента Office 365 можно создать группу и пригласить участников в другой клиента Office 365 как гости. Также применяется к Dynamics CRM.  <br/> |[Сведения о группах Office 365](https://support.office.com/article/b565caa1-5c40-40ef-9915-60fdb2d97fa2) <br/> [Гостевая доступа в Office 365 групп](https://support.office.com/article/bfc7a840-868f-4fd6-a390-f347bf51aff6) <br/> [Развертывание Office 365 групп](https://technet.microsoft.com/en-us/library/dn896591.aspx) <br/> |
   
## <a name="yammer-collaboration-options"></a>Параметры совместной работы в сети Yammer

|**Цель общего доступа**|**Функции администрирования**|**Инструкции**|
|:-----|:-----|:-----|
|Yammer — совместной работы через социальных среднего предприятия  <br/> |Если возможность создания внешних групп отключен администратором Yammer, пользователи могут создавать внешние групп для совместной работы в сети Yammer через бесед, возможность like и следуйте публикации, общий доступ к файлам и общаться по сети.  <br/> |[Создание и управление внешним группами в Yammer](https://support.office.com/article/9ccd15ce-0efc-4dc1-81bc-4a424ab6f92a) <br/> |
   
## <a name="teams-collaboration-options"></a>Параметры совместной работы групп

|**Цель общего доступа**|**Функции администрирования**|**Инструкции**|
|:-----|:-----|:-----|
|Совместная работа в рабочих группах с пользователями, внешними по отношению к организации  <br/> |Глобальный администратор для приглашения клиента Office 365 должен включить внешней совместной работы в группах. Глобальный администраторов и группы владельцев теперь можно приглашать любой пользователь с адресом электронной почты для совместной работы в группах.  <br/> Администраторы могут также управление и изменение Гости уже присутствует в своих клиентов.  <br/> |[Авторизация доступа](https://docs.microsoft.com/en-us/microsoftteams/teams-dependencies) <br/> [Включение и отключение доступа в группах](https://docs.microsoft.com/en-us/microsoftteams/set-up-guests) <br/> [Использование PowerShell для контроля доступа](https://docs.microsoft.com/en-us/microsoftteams/guest-access-powershell) <br/> [Контрольный список доступа гостя](https://docs.microsoft.com/en-us/microsoftteams/guest-access-checklist) <br/> [Просмотр гостевых пользователей](https://docs.microsoft.com/en-us/microsoftteams/view-guests) <br/> [Изменение сведений о пользователе гостя](https://docs.microsoft.com/en-us/microsoftteams/edit-guests-information) <br/> |
|Группа владельцев можно пригласить и управлять ими как гости совместной работы в рамках соответствующих групп на необходимые.  <br/> |Владельцы группы имеют дополнительные элементы управления на компьютерах с гостевым можно выполнить в соответствующих групп на необходимые.  <br/> |[Добавление Гости](https://support.office.com/en-us/article/teams-and-channels-df38ae23-8f85-46d3-b071-cb11b9de5499?ui=en-US&amp;rs=en-US&amp;ad=US#bkmk_addingguests&amp;ID0EAABAAA=Add_guests) <br/> [Добавить гостя группы.](https://docs.microsoft.com/en-us/microsoftteams/add-guests) <br/> [Управление доступом гостевой в группах](https://docs.microsoft.com/en-us/microsoftteams/manage-guests) <br/> [Определение пользователей, группы или в канале](https://support.office.com/en-us/article/see-who-s-on-a-team-or-in-a-channel-5c6be9be-9c45-4a0f-a1a0-f332b23cb6b7?ui=en-US&amp;rs=en-US&amp;ad=US) <br/> |
|Гости из других клиентов можно просмотреть содержимое в группах и совместно работать с другими участниками  <br/> |Нет.  <br/> |[Интерфейс доступа гостя](https://docs.microsoft.com/en-us/microsoftteams/guest-experience) <br/> |
   
## <a name="points-to-be-aware-of-about-office-365-inter-tenant-collaboration"></a>Моменты, которые необходимо учитывать о совместной работы между клиентом Office 365

### <a name="sharing-of-user-accounts-licenses-subscriptions-and-storage"></a>Совместное использование учетных записей пользователей, лицензий, подписки и хранилища

Каждая организация поддерживает собственный учетные записи пользователей, удостоверения, группы безопасности, подписок, лицензий и хранилища. Используется функции совместной работы в Office 365 вместе с общего доступа, политики и параметры безопасности для предоставления доступа к необходимой информации без снижения управления активами компании.
  
- **Учетных записей пользователей:** Учетные записи не могут быть общими и учетных записей не может повторяться между клиентами или разделов в локальной службы Active Directory. 
    
- **Лицензий &amp; подписки:** В Office 365, лицензируемые из планы лицензирования (также называемое номера SKU или Office 365 планы) предоставить пользователям доступ к службам Office 365, определенных для этих планов. 
    
- **Хранения:** В планах Office 365 связанные с программным обеспечением, в SharePoint Online можно управлять отдельно с ограничения хранилища почтовых ящиков. Ограничения для хранилища почтовых ящиков настроить и управлять с помощью Exchange Online. В обоих случаях хранения не может использоваться на нескольких клиентов. 
    
### <a name="can-we-share-domain-namespaces-across-office-365-tenants"></a>Задать мы совместное использование пространства имен домена клиентов Office 365?

Нет. Запоминающиеся домены, например, fabrikam.com или tailspintoys.com, можно только связанные и использовать с одного клиента во время. Каждый клиент должен иметь собственное пространство имен; Имя участника-пользователя, SMTP и SIP пространства имен не могут совместно использоваться клиентов.
  
### <a name="what-about-hybrid-components-and-office-365-inter-tenant-collaboration"></a>Как насчет гибридных компонентов и совместной работы между клиентом Office 365?

Локальный гибридный компоненты, такие как Exchange в организации и Azure AD "Подключение" невозможно разделить нескольких клиентов.
  

