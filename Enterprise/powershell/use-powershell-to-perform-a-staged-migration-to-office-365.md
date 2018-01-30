---
title: "Поэтапная миграция в Office 365 с помощью PowerShell"
ms.author: sirkkuw
author: sirkkuw
manager: scotv
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: 
ms.assetid: a20f9dbd-6102-4ffa-b72c-ff813e700930
description: "Сводка. Узнайте, как использовать Windows PowerShell для поэтапной миграции в Office 365."
ms.openlocfilehash: 5143b039937389d965386de0e09f4f59db071c86
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/11/2018
---
# <a name="use-powershell-to-perform-a-staged-migration-to-office-365"></a>Поэтапная миграция в Office 365 с помощью PowerShell

 **Сводка.** Узнайте, как выполнить поэтапную миграцию в Office 365, используя Windows PowerShell.
  
С помощью поэтапной миграции вы со временем можете перенести содержимое почтовых ящиков пользователей из исходной системы электронной почты в Office 365:.
  
В этой статье описываются задачи, связанные с поэтапной миграцией электронной почты с помощью Exchange Online PowerShell. Статья [Что необходимо знать о поэтапной миграции электронной почты в Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536487) представляет из себя обзор процесса миграции. Ознакомившись с содержимым этой статьи, начните переносить почтовые ящики из одной почтовой системы в другую, руководствуясь приведенными в этой статье сведениями.
  
> [!NOTE]
> Для поэтапной миграции можно также использовать Центр администрирования Exchange. См. статью [Поэтапная миграция электронной почты в Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536687). 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a>Что нужно знать перед началом работы?

Предполагаемое время выполнения задачи: от 2 до 5 минут для создания пакета миграции. После запуска пакета миграции продолжительность миграции будет зависеть от количества почтовых ящиков в пакете, размера каждого почтового ящика и доступной пропускной способности сети. Подробнее о других факторах, влияющих на продолжительность миграции почтовых ящиков в Office 365:, см. в статье [Производительность миграции](https://go.microsoft.com/fwlink/p/?LinkId=275079)
  
Для выполнения этой процедуры (процедур) необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в пункте "Миграция" статьи [Разрешения получателей](https://go.microsoft.com/fwlink/p/?LinkId=534105).
  
Чтобы использовать командлеты Exchange Online PowerShell, вам необходимо войти в систему и импортировать командлеты в локальный сеанс Windows PowerShell. Инструкции см в статье [Подключение к Exchange Online с помощью удаленной оболочки PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534121).
  
Полный список команд миграции см. в статье [Командлеты перемещения и миграции](https://go.microsoft.com/fwlink/p/?LinkId=534750).
  
## <a name="migration-steps"></a>Шаги миграции

### <a name="step-1-prepare-for-a-staged-migration"></a>Шаг 1. Подготовка к поэтапной миграции

Прежде чем переносить почтовые ящики в Office 365: с помощью поэтапной миграции, в среду Exchange необходимо внести несколько изменений.
  
 **Настройте Мобильный Outlook на локальном сервере Exchange Server**. Служба миграции электронной почты использует компонент Мобильный Outlook (также известный как RPC через HTTP) для подключения к локальному серверу Exchange Server. Сведения о настройке Мобильный Outlook для Exchange Server 2007 и Exchange 2003 см. в следующих статьях.
  
- [Exchange 2007. Инструкции по включению мобильного Outlook](https://go.microsoft.com/fwlink/?LinkID=167210)
    
- [Настройка мобильного Outlook в Exchange 2003](https://go.microsoft.com/fwlink/?LinkID=167209)
    
> [!IMPORTANT]
> В вашей конфигурации Мобильный Outlook необходимо использовать сертификат, выданный доверенным центром сертификации (ЦС). Мобильный Outlook невозможно настроить с помощью самозаверяющего сертификата. Дополнительные сведения см. в статье [Инструкции по настройке протокола SSL для мобильного Outlook](https://go.microsoft.com/fwlink/?LinkID=80875). 
  
 **Необязательно. Убедитесь, что вы можете подключиться к своей организации Exchange с помощью Мобильный Outlook**. Для проверки параметров подключения воспользуйтесь одним из следующих методов.
  
- Используйте Outlook из-за пределов вашей корпоративной сети, чтобы подключиться к своему локальному почтовому ящику Exchange.
    
- Проверьте параметры подключения с помощью [анализатора удаленного подключения Microsoft Exchange]((https://www.testexchangeconnectivity.com/)). Используйте Мобильный Outlook (RPC через HTTP) или проверки автообнаружения Outlook.
    
- В Exchange Online PowerShell выполните следующие команды.
    
  ```
  $Credentials = Get-Credential
  ```

  ```
  Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress <email address for on-premises administrator> -Credentials $credentials
  ```

 **Настройте разрешения.** Локальная учетная запись пользователя, используемая для подключения к локальной организации Exchange (также называемая "администратором миграции"), должна иметь необходимые разрешения на доступ к локальным почтовым ящикам, которые необходимо перенести в Office 365:. Эта учетная запись пользователя используется при подключении к системе электронной почты путем создания конечной точки миграции позже в рамках этой процедуры ([Шаг 3. Создание конечной точки миграции](use-powershell-to-perform-a-staged-migration-to-office-365.md#BK_Endpoint)).
  
Для переноса почтовых ящиков администратор должен иметь один из следующих наборов разрешений.
  
- Он должен входить в группу **администраторов домена** в доменной службе Active Directory локальной организации.
    
     или 
    
- Он должен получить разрешение на уровне **FullAccess** для каждого локального почтового ящика и разрешение **WriteProperty** на изменение свойства **TargetAddress** в локальных учетных записях пользователей.
    
     или 
    
- Он должен получить разрешение **Получать как** для базы данных локальных почтовых ящиков, в которой хранятся почтовые ящики пользователей, и разрешение **WriteProperty** на изменение свойства **TargetAddress** в локальных учетных записях пользователей.
    
Инструкции по настройке этих разрешений см. в статье [Назначение разрешений на перенос почтовых ящиков в Office 365](https://go.microsoft.com/fwlink/?LinkId=521656).
  
 **Отключите единую систему обмена сообщениями.** Если единая система обмена сообщениями включена для переносимых локальных почтовых ящиков, отключите ее перед миграцией. Включите эту систему по завершении миграции. Практические инструкции см. в статье[Выключение единой системы обмена сообщениями для пользователя](https://go.microsoft.com/fwlink/?LinkId=521891).
  
 **Создайте пользователей в Office 365 с помощью синхронизации службы каталогов.** Синхронизация службы каталогов используется для создания всех локальных пользователей в организации Office 365:.
  
После создания пользователей им необходимо предоставить лицензии. У вас есть 30 дней на то, чтобы добавить лицензии после создания пользователей. Инструкции по добавлению лицензий см. в разделе [Шаг 8. Необходимые действия после миграции](use-powershell-to-perform-a-staged-migration-to-office-365.md#BK_Postmigration).
  
 Для синхронизации и создания локальных пользователей в Office 365: вы можете использовать средство синхронизации Microsoft Azure Active Directory или службы синхронизации Microsoft Azure Active Directory Sync Services (AAD Sync). После переноса почтовых ящиков в Office 365: вы сможете управлять учетными записями пользователей в своей локальной организации, синхронизируя их со своей организацией Office 365:. Дополнительные сведения см. в статье [Интеграция служб каталогов](https://go.microsoft.com/fwlink/?LinkId=521788).
  
### <a name="step-2-create-a-csv-file-for-a-staged-migration-batch"></a>Шаг 2. Создание CSV-файла для пакета поэтапной миграции

После определения пользователей, локальные почтовые ящики которых необходимо перенести в Office 365:, используйте файл данных с разделителями-запятыми (CSV-файл) для создания пакета миграции. Каждая строка в CSV-файле, используемом Office 365: для запуска миграции, содержит сведения о локальном почтовом ящике. 
  
> [!NOTE]
> Ограничений по количеству почтовых ящиков, которые можно перенести в Office 365: с использованием поэтапной миграции Exchange, не существует. Тем не менее CSV-файл для пакета миграции может содержать не более 2000 строк. Чтобы перенести более 2000 почтовых ящиков, создайте дополнительные CSV-файлы и используйте каждый из них для создания соответствующего пакета миграции. 
  
 **Поддерживаемые атрибуты**
  
CSV-файл для поэтапной миграции поддерживает три атрибута, которые описаны ниже. Каждая строка в CSV-файле соответствует почтовому ящику и должна содержать значение каждого из этих атрибутов.
  
|**Атрибут**|**Описание**|**Обязательный?**|
|:-----|:-----|:-----|
|EmailAddress  <br/> |Задает основной SMTP-адрес электронной почты, например pilarp@contoso.com, для локальных почтовых ящиков.  <br/> Используйте для локальных почтовых ящиков основной SMTP-адрес, а не идентификаторы пользователей из Office 365:. Например, если локальный домен называется contoso.com, а домен электронной почты Office 365:  service.contoso.com, для адресов электронной почты в CSV-файле необходимо использовать доменное имя contoso.com.  <br/> |Обязательный  <br/> |
|Password  <br/> |Пароль, задаваемый для нового почтового ящика Office 365:. Любые ограничения относительно пароля, которые используются в организации Office 365:, также применяются к паролям из CSV-файла.  <br/> |Необязательный  <br/> |
|ForceChangePassword  <br/> |Указывает необходимость изменения пароля при первом входе пользователя в свой новый почтовый ящик Office 365:. Задайте для этого параметра значение **True** или **False**. <br/> > [!NOTE]> Если вы внедрили решение единого входа путем развертывания служб федерации Active Directory (AD FS) в локальной организации, для атрибута **ForceChangePassword** необходимо задать значение **False**.          |Необязательный  <br/> |
   
 **Формат CSV-файла**
  
Ниже приведен пример формата CSV-файла. В этом примере выполняется миграция в Office 365: трех локальных почтовых ящиков.
  
В первой строке (строке заголовков CSV-файла) содержатся имена атрибутов или полей, значения которых находятся в последующих строках. Имя каждого атрибута отделяется запятой.
  
```
EmailAddress,Password,ForceChangePassword 
pilarp@contoso.com,Pa$$w0rd,False 
tobyn@contoso.com,Pa$$w0rd,False 
briant@contoso.com,Pa$$w0rd,False 
```

Каждая строка под строкой заголовков представляет одного пользователя и содержит данные, используемые для переноса почтового ящика этого пользователя. Значения атрибутов в каждой строке должны следовать в том же порядке, что и имена атрибутов в строке заголовков. 
  
Создать CSV-файл можно с помощью любого текстового редактора или соответствующего приложения, например Excel. Сохраните файл как CSV- или TXT-файл.
  
> [!NOTE]
> Если CSV-файл содержит знаки, не входящие в ASCII, или специальные символы, сохраните его в кодировке UTF-8 или другой кодировке Юникода. В зависимости от приложения сохранить CSV-файл в кодировке UTF-8 или другой кодировке Юникода может оказаться проще, если язык системы соответствует языку, используемому в CSV-файле. 
  
### <a name="step-3-create-a-migration-endpoint"></a>Шаг 3. Создание конечной точки миграции
<a name="BK_Endpoint"> </a>

Для успешного переноса электронной почты решение Office 365: должно обмениваться данными с исходной системой электронной почты. Для этого Office 365 использует конечную точку миграции. Чтобы создать конечную точку миграции мобильного Outlook с помощью PowerShell для поэтапной миграции, сначала [подключитесь к Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121). 
  
Полный список команд миграции см. в статье [Командлеты перемещения и миграции](https://go.microsoft.com/fwlink/p/?LinkId=534750).
  
Чтобы создать конечную точку миграции мобильного Outlook с именем StagedEndpoint в Exchange Online PowerShell, выполните следующие команды.
  
```
$Credentials = Get-Credential
```

```
New-MigrationEndpoint -ExchangeOutlookAnywhere -Name StagedEndpoint -Autodiscover -EmailAddress administrator@contoso.com -Credentials $Credentials
```

Дополнительные сведения о командлете **New-MigrationEndpoint** см. в статье[New-MigrationEndpoint](https://go.microsoft.com/fwlink/p/?LinkId=536437).
  
> [!NOTE]
> С помощью командлета **New-MigrationEndpoint** и параметра **-TargetDatabase** можно указать базу данных, которая будет использоваться службой. В противном случае база данных назначается случайным образом на сайте Службы федерации Active Directory (AD FS) 2.0, на котором расположен почтовый ящик управления.
  
#### <a name="verify-it-worked"></a>Проверка работы

В Exchange Online PowerShell выполните следующую команду, чтобы отобразить сведения о конечной точке миграции StagedEndpoint.
  
```
Get-MigrationEndpoint StagedEndpoint | Format-List EndpointType,ExchangeServer,UseAutoDiscover,Max*
```

### <a name="step-4-create-and-start-a-stage-migration-batch"></a>Шаг 4. Создание и запуск пакета поэтапной миграции
<a name="BK_Endpoint"> </a>

Чтобы создать пакет для прямой миграции, выполните командлет **New-MigrationBatch** в Exchange Online PowerShell. Можно создать пакет миграции и запустить его обработку автоматически, включив параметр _AutoStart_. Кроме того, вы можете создать пакет миграции, а затем вручную запустить его с помощью командлета **Start-MigrationBatch**. В этом примере создается пакет миграции StagedBatch1 и используется конечная точка миграции, созданная на предыдущем шаге.
  
```
New-MigrationBatch -Name StagedBatch1 -SourceEndpoint StagedEndpoint -AutoStart
```

В этом примере также создается пакет миграции StagedBatch1 и используется конечная точка миграции, созданная на предыдущем шаге. Так как параметр  _AutoStart_ не включен, пакет миграции необходимо запустить вручную на панели мониторинга миграции или с помощью командлета **Start-MigrationBatch**. Как было сказано выше, в одно и то же время может существовать только один пакет прямой миграции.
  
```
New-MigrationBatch -Name StagedBatch1 -SourceEndpoint StagedEndpoint
```

#### <a name="verify-it-worked"></a>Проверка работы

Выполните следующую команду в Exchange Online PowerShell, чтобы отобразить сведения о пакете миграции StagedBatch1.
  
```
Get-MigrationBatch -Identity StagedBatch1 | Format-List
```

Вы также можете убедиться, что пакет запущен, выполнив следующую команду.
  
```
Get-MigrationBatch -Identity StagedBatch1 | Format-List Status
```

Дополнительные сведения о командлете **Get-MigrationBatch** см. в статье[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441).
  
### <a name="step-5-convert-on-premises-mailboxes-to-mail-enabled-users"></a>Шаг 5. Преобразование локальных почтовых ящиков в учетные записи пользователей, поддерживающих почту
<a name="BK_Endpoint"> </a>

После успешной миграции пакета почтовых ящиков необходимо обеспечить получение почты пользователями. У пользователя, почтовый ящик которого перенесен, теперь есть два почтовых ящика: локальный и почтовый ящик Office 365:. Пользователи, у которых есть почтовый ящик в Office 365:, перестанут получать новые сообщения в свои локальные почтовые ящики. 
  
Так как миграция не завершена, вы пока не можете направлять всех пользователей к Office 365: для получения электронной почты. Так что необходимо сделать для пользователей, у которых есть оба почтовых ящика? Нужно изменить локальные почтовые ящики, которые уже перенесены для пользователей, поддерживающих почту. При переходе из почтового ящика к пользователю, поддерживающему почту, посоветуйте ему перейти в Office 365:, а не к своему локальному почтовому ящику, чтобы получить электронную почту. 
  
Еще одна важная причина, по которой локальные почтовые ящики следует преобразовать в учетные записи пользователей, поддерживающих почту,  необходимость сохранить прокси-адреса из почтовых ящиков Office 365: посредством их копирования в учетную запись пользователей, поддерживающих почту. Это позволит управлять облачными пользователями из локальной организации с помощью службы Active Directory. Кроме того, если после переноса всех почтовых ящиков в Office 365: вы решите списать свою локальную организацию Exchange Server, прокси-адреса, скопированные в учетные записи пользователей, поддерживающих почту, останутся в локальной службе Active Directory.
  
Чтобы получить дополнительные сведения и скачать сценарии, которые можно использовать для преобразования почтовых ящиков в учетные записи пользователей, поддерживающих почту, см. следующие статьи.
  
- [Преобразование почтовых ящиков Exchange 2007 в учетные записи пользователей, поддерживающих почту](https://go.microsoft.com/fwlink/p/?LinkId=233648)
    
- [Преобразование почтовых ящиков Exchange 2003 в учетные записи пользователей, поддерживающих почту](https://go.microsoft.com/fwlink/p/?LinkId=233647)
    
### <a name="step-6-delete-a-staged-migration-batch"></a>Шаг 6. Удаление пакета поэтапной миграции
<a name="BK_Endpoint"> </a>

 После успешного переноса всех почтовых ящиков из пакета миграции и преобразования локальных почтовых ящиков из пакета в учетные записи пользователей, поддерживающих почту, пакет поэтапной миграции можно удалить. Убедитесь, что почта пересылается в почтовые ящики Office 365: из пакета миграции. При удалении пакета поэтапной миграции служба миграции удаляет все записи, связанные с пакетом, а также сам пакет.
  
Чтобы удалить пакет миграции StagedBatch1 в Exchange Online PowerShell, выполните следующую команду.
  
```
Remove-MigrationBatch -Identity StagedBatch1
```

Дополнительные сведения о командлете **Remove-MigrationBatch** см. в статье[Remove-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536481).
  
#### <a name="verify-it-worked"></a>Проверка работы

Выполните следующую команду в Exchange Online PowerShell, чтобы отобразить сведения о пакете миграции IMAPBatch1.
  
```
Get-MigrationBatch StagedBatch1
```

Команда либо вернет пакет миграции с состоянием **Удаление**, либо вернет ошибку (не удалось найти пакет миграции), что подтверждает удаление пакета миграции.
  
Дополнительные сведения о командлете **Get-MigrationBatch** см. в статье[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441).
  
### <a name="step7-assign-licenses-to-office-365-users"></a>Шаг 7. Назначение лицензий пользователям Office 365
<a name="BK_Endpoint"> </a>

Активируйте учетные записи пользователей Office 365 для перенесенных учетных записей, назначив им лицензии. Если не назначить лицензию, почтовый ящик будет отключен по истечении льготного периода (30 дней). Сведения о назначении лицензии в Центре администрирования Центр администрирования Office 365 см. в статье [Назначение и отмена лицензий для Office 365 бизнес](https://go.microsoft.com/fwlink/?LinkId=536681).
  
### <a name="step-8-complete-post-migration-tasks"></a>Шаг 8. Необходимые действия после миграции
<a name="BK_Postmigration"> </a>

- **Создайте DNS-запись автообнаружения, чтобы пользователи смогли с легкостью получить доступ к своим почтовым ящикам.** После переноса всех локальных почтовых ящиков в Office 365: вы можете настроить DNS-запись автообнаружения для своей организации Office 365:, чтобы пользователи могли с легкостью подключаться к своим новым почтовым ящикам Office 365: с помощью Outlook и мобильных клиентов. В этой новой DNS-записи автообнаружения необходимо использовать то же пространство имен, которое используется для организации Office 365:. Например, если облачное пространство имен  cloud.contoso.com, необходимо создать DNS-запись автообнаружения autodiscover.cloud.contoso.com.
    
    В Office 365: запись CNAME служит для реализации службы автообнаружения для клиентов Outlook и мобильных клиентов. Необходимо, чтобы запись CNAME для автообнаружения содержала следующие сведения.
    
  - **Псевдоним:** autodiscover
    
  - **Целевой объект:** autodiscover.outlook.com
    
    Дополнительные сведения см. в статье [Создание DNS-записей для Office 365 при управлении DNS-записями](https://go.microsoft.com/fwlink/p/?LinkId=535028).
    
- **Выполните списание локальных серверов Exchange.** Как только вы убедитесь, что вся электронная почта направляется непосредственно в почтовые ящики Office 365:, поэтому вам больше не нужно поддерживать свою локальную организацию электронной почты, либо если вы не планируете внедрять решение единого входа, вы можете удалить Exchange с серверов, а также удалить свою локальную организацию Exchange.
    
    Дополнительные сведения см. в следующих статьях:
    
  - [Изменение или удаление Exchange 2010](https://go.microsoft.com/fwlink/?LinkId=217936)
    
  - [Удаление организации Exchange 2007](https://go.microsoft.com/fwlink/?LinkID=100485)
    
  - [Удаление сервера Exchange Server 2003](https://go.microsoft.com/fwlink/?LinkID=56561)
    
