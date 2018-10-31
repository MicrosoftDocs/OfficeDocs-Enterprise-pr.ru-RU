---
title: Ферма с несколькими географически возможности в Exchange Online
ms.author: chrisda
author: chrisda
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Normal
ms.assetid: ''
description: Разверните узел состояние присутствия Office 365 для нескольких географических регионов с несколькими географически возможности в Exchange Online.
ms.openlocfilehash: 5f34a2da47b9767aa9dfe22c6be7237951128960
ms.sourcegitcommit: a3e2b2e58c328238c15d3f9daf042ea3de9d66be
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/30/2018
ms.locfileid: "25849925"
---
# <a name="multi-geo-capabilities-in-exchange-online"></a>Ферма с несколькими географически возможности в Exchange Online

Одним клиентом охватывать разных географических местоположениях предоставляют возможности несколькими Geo в Office 365. При включении географически ферма с несколькими клиентами можно выбрать расположение содержимого почтового ящика, Exchange Online (статических данных) на уровне пользователя.

Расположение начальной клиента (называется центрального расположения) определяется на основании адрес для выставления счетов. При включении несколькими географически почтовые ящики можно поместить в расположениях Дополнительные сопутствующие по:

- Создание нового почтового ящика Exchange Online напрямую в расположение вспомогательных.

- Перемещение существующего почтового ящика Exchange Online в расположение вспомогательных.

- Адаптация новых сотрудников почтовых ящиков из локальной организации Exchange непосредственно в расположение вспомогательных.

В следующих расположениях географически доступны для использования в конфигурации с несколькими географически:

- Азиатско-Тихоокеанский регион

- Австралия

- Канада

- Европейский Союз

- Франция

- Индия (в настоящее время доступны только для клиентов с адреса для выставления счета в Индии)

- Япония

- Республика Корея

- Соединенное Королевство

- США

## <a name="prerequisite-configuration"></a>Предварительные настройки
Прежде чем начать, используя возможности несколькими географически в Exchange Online, корпорации Майкрософт необходимо настроить клиент Exchange Online для поддержки различных географически. Этот процесс однократного конфигурации запускается после определения порядка что Office 365 Multi-географически и лицензий, которые отображаются в вашего клиента. Этот процесс однократного конфигурации обычно занимает меньше, чем 30 дней. Чтобы порядок Office 365 Multi-географически, обратитесь к представителю Майкрософт. Дополнительные сведения можно https://aka.ms/Multi-Geo.

Вы будете получать уведомления в [Центр сообщений Office 365](https://support.office.com/article/Message-center-in-Office-365-38FB3333-BFCC-4340-A37B-DEDA509C2093) после завершения настройки. Конфигурация будет запущен автоматически после лицензии несколькими географически отображаются в вашего клиента.

## <a name="mailbox-placement-and-moves"></a>Расположение почтового ящика и перемещений
После завершения действия по настройке необходимого несколькими географически Microsoft Exchange Online будет поддерживать атрибут **PreferredDataLocation** для объектов-пользователей в Azure AD.

Exchange Online синхронизирует свойство **PreferredDataLocation** из Azure AD в свойство **MailboxRegion** в службе каталогов Exchange Online. Значение **MailboxRegion** определяет географически, где будет помещен почтовых ящиков пользователей и все связанные архивные почтовые ящики. Настройка основного почтового ящика и архивирование почтовых ящиков пользователей могут располагаться в разных географического расположения невозможна. Только один географического расположения можно настроить для каждого объекта-пользователя.

- При настройке **PreferredDataLocation** на пользователя с помощью существующего почтового ящика почтового ящика будут помещены в очередь перемещения и автоматически перемещены указанного географического расположения. 

- Когда **PreferredDataLocation** настроен на пользователя, не существующего почтового ящика, почтовый ящик будет выполнена подготовка в указанного географического расположения. 

- Если **PreferredDataLocation** не указан на пользователя, почтовый ящик будет назначено центрального расположения.

- Если код **PreferredDataLocation** неверен (например тип NAN вместо им), почтовый ящик будет помещен в центральном расположении.

**Примечание**: несколькими географически возможности и Скайп для бизнеса на региональном уровнях размещенных собрания по сети обоих используйте свойство **PreferredDataLocation** на объектов-пользователей для обнаружения служб. Если вы настраиваете **PreferredDataLocation** значения для объектов-пользователей на региональном уровнях размещенной собраний, почтовых ящиков для тех пользователей, автоматически перемещается в указанного географического расположения после включения несколькими географически на клиента Office 365.

## <a name="feature-limitations-for-multi-geo-in-exchange-online"></a>Ограничения для нескольких Geo в Exchange Online
1. Ферма с несколькими географически возможности поддержки только почтовые ящики пользователей, почтовые ящики ресурса (почтовые ящики оборудования и помещений) и общие почтовые ящики. Общедоступные папки почтовых ящиков и групп Office 365, остаются в центральном расположении.
 
2. Безопасность и соответствие требованиям функции (например, аудит и обнаружения электронных данных), доступные в центре администрирования Exchange (EAC) не доступны в географически нескольких организаций. Вместо этого необходимо использовать для настройки функций безопасности и соответствия требованиям в [Office 365 безопасности & центре соответствия требованиям](https://support.office.com/article/7e696a40-b86b-4a20-afcc-559218b7b1b8) .

3. Outlook для Mac пользователей могут возникнуть кратковременной потере доступа к их папки серверный архив при перемещении их почтовых ящиков в новое расположение географически. Это условие возникает, когда основной пользователя и архивные почтовые ящики находятся в разных географического расположения, так как перемещение почтовых ящиков между географически может завершиться в разное время.

4. Пользователи не могут совместно использовать *папки почтовых ящиков* в подразделениях geo в Outlook в Интернете (ранее известных как Outlook Web App или OWA). Например пользователя в Европейском союзе нельзя использовать Outlook в Интернете для открытия общей папки в почтовом ящике, расположенного в США. Тем не менее Outlook на веб-пользователей можно открыть *другой почтовый ящик* в разных Geos с помощью отдельном окне браузера, как описано в [Открытие почтового ящика другого пользователя в отдельном окне браузера в Outlook Web App](https://support.office.com/article/A909AD30-E413-40B5-A487-0EA70B763081#__toc372210362).

    **Примечание**: географически нескольких почтовых ящиков общий доступ к папке, поддерживаемых в Outlook в Windows.

## <a name="administration"></a>Администрирование 
Для просмотра и настройки несколькими географически свойств в среде Office 365 требуется удаленной оболочки PowerShell. Сведения о различных моделей PowerShell, используемые для администрирования Office 365 содержатся в разделе [Управление Office 365 и Exchange Online с помощью Windows PowerShell](https://support.office.com//article/06a743bb-ceb6-49a9-a61d-db4ffdf54fa6).

- Необходимо v1.1.166.0 [PowerShell модуле Microsoft Azure Active Directory](https://social.technet.microsoft.com/wiki/contents/articles/28552.microsoft-azure-active-directory-powershell-module-version-release-history.aspx) или более поздней версии в v1.x, чтобы просмотреть свойство **PreferredDataLocation** на объектов-пользователей. Синхронизация через подключение AAD в AAD объектов-пользователей не могут иметь напрямую изменить с помощью AAD PowerShell их **PreferredDataLocation** значение. С помощью AAD PowerShell может быть изменено объектов-пользователей только в облаке. Чтобы подключиться к Windows Azure AD PowerShell, обратитесь к разделу [подключение к Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell). 

- Чтобы подключиться к Exchange Online PowerShell, обратитесь к разделу [подключение к Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell). 

### <a name="connect-directly-to-a-specific-geo-using-exchange-online-powershell"></a>Прямой звонок на конкретных географически с помощью Exchange Online PowerShell
Как правило Exchange Online PowerShell будут подключаться к географически расположение по умолчанию. Однако можно также подключиться непосредственно к географически нестандартные расположения. Из-за повышение производительности мы рекомендуем путем прямого подключения расположение географически не по умолчанию при только управление пользователями в данном месте географически.

Для подключения к определенным Geo параметра *ConnectionUri* отличается от инструкции регулярных подключения. Остальные команды и значения, совпадают. Порядок действий:

1. На локальном компьютере откройте Windows PowerShell и выполните следующую команду:
    
    ```
    $UserCredential = Get-Credential
    ```
   В диалоговом окне **Запрос учетных данных Windows PowerShell** введите рабочий или школа учетной записи и пароль и нажмите кнопку **ОК**.
    
2. Замените `<emailaddress>` с адресом электронной почты из **любой** почтовых ящиков в целевом расположении географически и выполните следующую команду. Разрешения для почтового ящика и связь с свои учетные данные на шаге 1 не учитываются; адрес электронной почты просто сообщает Exchange Online where для подключения.
  
   ```
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=<emailaddress> -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```

   Например если olga@contoso.onmicrosoft.com является адресом электронной почты допустимый почтовый ящик в географически, чтобы подключиться, выполните следующую команду:

   ```
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=olga@contoso.onmicrosoft.com -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```
3. Выполните следующую команду:
    
    ```
    Import-PSSession $Session
    ```

### <a name="azure-ad-connect-version-requirements"></a>Требования относительно версий Azure AD подключение
Подключение AAD версии 1.1.524.0 или более поздняя версия является единственным поддерживаемым способом для установки свойства **PreferredDataLocation** объектов-пользователей, которые синхронизируются из локального Active Directory. Синхронизация через подключение AAD в AAD объектов-пользователей не могут иметь напрямую изменить с помощью AAD PowerShell их **PreferredDataLocation** значение. С помощью AAD PowerShell может быть изменено объектов-пользователей только в облаке. Подробные сведения содержатся в разделе [Azure Active Directory подключение синхронизации: Настройка предпочитаемого данных расположения для ресурсов Office 365](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).

### <a name="geo-codes"></a>Коды географически
Для указания Geo в свойстве **PreferredDataLocation** используйте трех букв. В следующей таблице перечислены коды для доступных Geos:

|Географическое |Код |
|---------|---------|
|Азиатско-Тихоокеанский регион |APC |
|Австралия |AUS |
|Канада |CAN |
|Европейский Союз |EUR |
|Франция |FRA|
|Индия |IND |
|Япония |JPN |
|Республика Корея |KOR |
|Соединенное Королевство |GBR |
|США |NAM |

**Примечание**: свойства **PreferredDataLocation** и **MailboxRegion** являются строками с без проверки ошибок. Если ввести недопустимое значение (например, NAN) почтовый ящик будет помещен в географически по умолчанию.

### <a name="view-the-available-geos-that-are-configured-in-your-exchange-online-organization"></a>Просмотр доступных Geos, настроенных в организации Exchange Online
Чтобы просмотреть список настроенных Geos в организации Exchange Online, выполните следующую команду в Exchange Online PowerShell:

```
Get-OrganizationConfig | Select -ExpandProperty AllowedMailboxRegions | Format-Table
```

Выходные данные команды выглядят так:

```
APC
AUS
CAN
EUR
FRA
GBR
JPN
KOR
NAM
```

### <a name="view-the-default-geo-for-your-exchange-online-organization"></a>Представление по умолчанию географически для организации Exchange Online
Чтобы просмотреть географически по умолчанию из организации Exchange Online, выполните следующую команду в Exchange Online PowerShell:

```
Get-OrganizationConfig | Select DefaultMailboxRegion
```

Выходные данные команды выглядят так:

```
DefaultMailboxRegion
--------------------
NAM
```


### <a name="find-the-geo-location-of-a-mailbox"></a>Поиск расположения географически почтового ящика
Командлет **Get-Mailbox** в Exchange Online PowerShell отображает следующие multi географически связанных свойств почтовых ящиков:

- **Базы данных**: сначала 3 букв имя базы данных соответствующие код географически, который сообщает о том, где в настоящее время находится почтовый ящик. Свойство должно использоваться для почтовых ящиков Online архив **ArchiveDatabase** .

- **MailboxRegion**: Определяет код географически расположение, которое было задано администратором (синхронизируются из **PreferredDataLocation** в Azure AD).

- **MailboxRegionLastUpdateTime**: Указывает, когда MailboxRegion последнего обновления (автоматически или вручную).

Чтобы увидеть эти свойства почтового ящика, используйте следующий синтаксис:

```
Get-Mailbox -Identity <MailboxIdentity> | Format-List Database,MailboxRegion*
```

Например для просмотра сведений географически для chris@contoso.onmicrosoft.com почтовых ящиков, выполните следующую команду:

```
Get-Mailbox -Identity chris@contoso.onmicrosoft.com | Format-List Database, MailboxRegion*
```

Выходные данные команды выглядят так:

```
Database                    : EURPR03DG077-db007 
MailboxRegion               : EUR 
MailboxRegionLastUpdateTime : 2/6/2018 8:21:01 PM 
```

> **Примечание:** Если код geo в имя базы данных не соответствует **MailboxRegion** значение, почтовый ящик будет автоматически быть помещены в очередь перемещения и переместить в географически место, указанное значение **MailboxRegion** (Exchange Online выполняет поиск Несоответствие между значениями свойств).

### <a name="move-an-existing-cloud-only-mailbox-to-a-specific-geo"></a>Перемещение к определенным Geo существующего почтового ящика только в облаке
Только в облаке пользователь — это пользователь не представлением для клиента с помощью AAD подключение. Этот пользователь был создан непосредственно в Azure AD. Используйте командлеты **Get-MsolUser** и **Set-MsolUser** в модуля Azure AD для Windows PowerShell, чтобы просмотреть или задать географически, где будет храниться только в облаке почтового ящика пользователя.

Чтобы просмотреть значение **PreferredDataLocation** для пользователя, используйте следующий синтаксис в Windows Azure AD PowerShell:

```
Get-MsolUser -UserPrincipalName <UserPrincipalName> | Format-List UserPrincipalName,PreferredDataLocation
```

Например чтобы просмотреть значение **PreferredDataLocation** для michelle@contoso.onmicrosoft.com пользователя, выполните следующую команду:

```
Get-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com | Format-List
```

Выходные данные команды выглядят так:

```
UserPrincipalName     : michelle@contoso.onmicrosoft.com
PreferredDataLocation : EUR
```

Чтобы изменить значение **PreferredDataLocation** для объекта пользователя только в облаке, используйте следующий синтаксис в Windows Azure AD PowerShell:

``` 
Set-MsolUser -UserPrincipalName <UserPrincipalName> -PreferredDataLocation <GeoCode>
```

Например чтобы задать значение **PreferredDataLocation** географически Европейский союз (ЕВРО) для michelle@contoso.onmicrosoft.com пользователя, выполните следующую команду:

``` 
Set-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com -PreferredDataLocation EUR
```

**Примечания.**

- Как упоминалось ранее нельзя использовать эту процедуру для объектов-синхронизированных пользователей из локального Active Directory. Необходимо изменить значение **PreferredDataLocation** , с помощью AAD подключение. Дополнительные сведения можно [Azure Active Directory подключение синхронизации: Настройка предпочитаемого данных расположения для ресурсов Office 365](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation). 

- Сколько времени занимает о перемещении mailboxfrom его текущего geo в новом расположении желаемую географически зависит от нескольких факторов:
 
  - Размер и тип почтового ящика.
 
  - Количество происходит перемещение почтовых ящиков.
 
  - Доступность ресурсов перемещения.

#### <a name="move-disabled-mailboxes-that-are-on-litigation-hold"></a>Перемещение почтовых ящиков на хранение для судебного разбирательства этот параметр отключен
Этот параметр отключен почтовых ящиков на хранение для судебного разбирательства, сохраняются для обнаружения электронных данных, которые целей, нельзя перемещать, изменяя их значение **PreferredDataLocation** в отключенном состоянии. Чтобы переместить отключенного почтового ящика на хранение для судебного разбирательства:

1. Временно назначьте почтовому ящику лицензию.

2. Измените **PreferredDataLocation**.

3. Удалите лицензии из почтового ящика после его были перемещены для выбранного географического расположения верните его в отключенном состоянии.

### <a name="create-new-cloud-mailboxes-in-a-specific-geo"></a>Создание новых облачных почтовых ящиков в конкретных географически 
Чтобы создать новый почтовый ящик в конкретных географического расположения, необходимо выполнить одно из следующих действий:

- Настройте значение **PreferredDataLocation** , как описано в предыдущем разделе *перед* создания почтового ящика в Exchange Online. К примеру настройте значение **PreferredDataLocation** пользователя перед назначение лицензии. 

- Назначение лицензии в то же время, задайте значение **PreferredDataLocation** .

Для создания нового только в облаке лицензированных пользователей (не AAD подключение синхронизации) в определенных географически, используйте следующий синтаксис в Windows Azure AD PowerShell:

```
New-MsolUser -UserPrincipalName <UserPrincipalName> -DisplayName "<Display Name>" [-FirstName <FirstName>] [-LastName <LastName>] [-Password <Password>] [-LicenseAssignment <AccountSkuId>] -PreferredDataLocation <GeoCode> 
```
В этом примере Создание учетной записи пользователя для Brunner Александру со следующими значениями:

- Имя участника-пользователя: ebrunner@contoso.onmicrosoft.com

- Имя: Александру

- Фамилия: Brunner

- Отображаемое имя Brunner Александру

- Пароль: случайным образом полученное и отображаются в результатах команды (так как не используется параметр *Password* )

- Лицензия: contoso:ENTERPRISEPREMIUM (E5)

- Расположение: Австралия (Стандартное)

```
New-MsolUser -UserPrincipalName ebrunner@contoso.onmicrosoft.com -DisplayName "Elizabeth Brunner" -FirstName Elizabeth -LastName Brunner -LicenseAssignment contoso:ENTERPRISEPREMIUM -PreferredDataLocation AUS
```

Дополнительные сведения о создании новых учетных записей пользователей и поиск значения LicenseAssignment в Windows Azure AD PowerShell можно [Создать учетные записи пользователей с Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell) и [Просмотр лицензий и службы с помощью Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/view-licenses-and-services-with-office-365-powershell).

> **Примечание:** Если вы используете Exchange Online PowerShell для включения почтового ящика и необходимости почтового ящика будет создан непосредственно в географически, который указан в **PreferredDataLocation**, необходимо использовать Exchange Online командлета, такие как **Enable-Mailbox** или **New-Mailbox **непосредственно к облачной службе. При использовании командлета **Enable-RemoteMailbox** в локальной Exchange, почтовый ящик будет создан в географически по умолчанию.

### <a name="onboard-existing-on-premises-mailboxes-in-a-specific-geo"></a>Встроенный существующих локальных почтовых ящиков в конкретных географически
Можно использовать стандартный входящая средства и процедуры для переноса почтовых ящиков из локальной организации Exchange в Exchange Online, включая панели [мониторинга миграции в центре администрирования Exchange](https://support.office.com/article/d164b35c-f624-4f83-ac58-b7cae96ab331)и командлет [New-MigrationBatch](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-migrationbatch) в Exchange Online PowerShell.

Первым этапом является убедитесь, что существует объект пользователя для каждого почтового ящика быть onboarded и убедитесь, что правильное значение **PreferredDataLocation** , используемых в Azure AD. Средства адаптация новых сотрудников будут использовать значение **PreferredDataLocation** и будет перенос почтовых ящиков непосредственно в указанный географически.

Или можно использовать следующие шаги для встроенных почтовых ящиков непосредственно в конкретных географического расположения, с помощью командлета [New-MoveRequest](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-moverequest) в Exchange Online PowerShell.

1. Убедитесь, что существует объект пользователя для каждого почтового ящика onboarded и **PreferredDataLocation** имеет значение необходимого значения в Azure AD. Значение **PreferredDataLocation** синхронизируются с атрибутом **MailboxRegion** соответствующего объекта пользователя почты в Exchange Online.

2. Напрямую подключаться к определенным вспомогательных географически, с помощью инструкций по подключению из данного раздела.

3. В Exchange Online PowerShell хранение учетных данных администратора в локальной, которые используются для выполнения миграции почтовых ящиков в переменную, выполнив следующую команду:

    ```
    $RC = Get-Credential
    ```

4. В Exchange Online PowerShell создайте новый **New-MoveRequest** аналогичные следующим образом: 

    ```
    New-MoveRequest -Remote -RemoteHostName mail.contoso.com -RemoteCredential $RC -Identity user@contoso.com -TargetDeliveryDomain <YourAppropriateDomain>
    ```

5. Повторите шаг #4 для всех почтовых ящиков, необходимые для переноса из локального сервера Exchange в расположение вспомогательных в настоящее время связаны с.

6. Если необходимо перенести дополнительные почтовые ящики в различных вспомогательных расположение, повторите шаги с 2 по 4 для каждого конкретного вспомогательных расположения.

### <a name="multi-geo-reporting"></a>Ферма с несколькими географически отчетов
**Отчеты об использовании несколькими Geo** в центре администрирования Office 365 отображает число пользователей, географического расположения. Отчет отображает рассылки пользователя для текущего месяца и предоставляет статистические данные за последние 6 месяцев.
