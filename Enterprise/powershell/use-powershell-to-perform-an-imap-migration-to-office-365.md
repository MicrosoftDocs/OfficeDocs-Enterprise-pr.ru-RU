---
title: "Использование PowerShell для миграции IMAP в Office 365"
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
ms.assetid: c28de4a5-1e8e-4491-9421-af066cde7cdd
description: "Сводка. Узнайте, как использовать Windows PowerShell для миграции IMAP в Office 365."
ms.openlocfilehash: 2c4d54f02a885e7ee5e18bed715c30e9090610df
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/11/2018
---
# <a name="use-powershell-to-perform-an-imap-migration-to-office-365"></a><span data-ttu-id="b59c1-103">Использование PowerShell для миграции IMAP в Office 365</span><span class="sxs-lookup"><span data-stu-id="b59c1-103">Use PowerShell to perform an IMAP migration to Office 365</span></span>

 <span data-ttu-id="b59c1-104">**Сводка.** Узнайте, как выполнить IMAP-миграцию в Office 365, используя Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b59c1-104">**Summary:** Learn how to use Windows PowerShell to perform an IMAP migration to Office 365.</span></span>
  
<span data-ttu-id="b59c1-p101">В процессе развертывания Office 365:, вы можете перенести содержимое почтовых ящиков пользователей из службы электронной почты IMAP в Office 365:. В этой статье описаны задачи, которые выполняются при миграции электронной почты IMAP с помощью Exchange Online PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b59c1-p101">As part of the process of deploying Office 365, you can choose to migrate the contents of user mailboxes from an Internet Mail Access Protocol (IMAP) email service to Office 365. This article walks you through the tasks for an email IMAP migration by using Exchange Online PowerShell.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="b59c1-p102">Для миграции IMAP можно также использовать Центр администрирования Exchange. См. статью [Перенос почтовых ящиков IMAP в Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536685).</span><span class="sxs-lookup"><span data-stu-id="b59c1-p102">You can also use the Exchange admin center to perform an IMAP migration. See [Migrate your IMAP mailboxes to Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536685).</span></span> 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="b59c1-109">Что нужно знать перед началом работы?</span><span class="sxs-lookup"><span data-stu-id="b59c1-109">What do you need to know before you begin?</span></span>

<span data-ttu-id="b59c1-p103">Предполагаемое время выполнения задачи: от 2 до 5 минут для создания пакета миграции. После запуска пакета миграции продолжительность миграции будет зависеть от количества почтовых ящиков в пакете, размера каждого почтового ящика и доступной пропускной способности сети. Подробнее о других факторах, влияющих на продолжительность миграции почтовых ящиков в Office 365:, см. в статье [Производительность миграции](https://go.microsoft.com/fwlink/p/?LinkId=275079)</span><span class="sxs-lookup"><span data-stu-id="b59c1-p103">Estimated time to complete this task: 2-5 minutes to create a migration batch. After the migration batch is started, the duration of the migration will vary based on the number of mailboxes in the batch, the size of each mailbox, and your available network capacity. For information about other factors that affect how long it takes to migrate mailboxes to Office 365, see [Migration Performance](https://go.microsoft.com/fwlink/p/?LinkId=275079).</span></span>
  
<span data-ttu-id="b59c1-p104">Для выполнения этой процедуры (процедур) необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в пункте "Миграция" статьи [Разрешения получателей](https://go.microsoft.com/fwlink/p/?LinkId=534105) в соответствующей таблице.</span><span class="sxs-lookup"><span data-stu-id="b59c1-p104">You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Migration" entry in a table in the [Recipients Permissions](https://go.microsoft.com/fwlink/p/?LinkId=534105) topic.</span></span>
  
<span data-ttu-id="b59c1-p105">Чтобы использовать командлеты Exchange Online PowerShell, вам необходимо войти в систему и импортировать командлеты в локальный сеанс Windows PowerShell. Инструкции см в статье [Подключение к Exchange Online с помощью удаленной оболочки PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534121).</span><span class="sxs-lookup"><span data-stu-id="b59c1-p105">To use the Exchange Online PowerShell cmdlets, you need to sign in and import the cmdlets into your local Windows PowerShell session. See [Connect to Exchange Online using remote PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534121) for instructions.</span></span>
  
<span data-ttu-id="b59c1-117">Полный список команд миграции см. в статье [Командлеты перемещения и миграции](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span><span class="sxs-lookup"><span data-stu-id="b59c1-117">For a full list of migration commands, see [Move and migration cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span></span>
  
<span data-ttu-id="b59c1-118">К миграции IMAP применяются следующие ограничения.</span><span class="sxs-lookup"><span data-stu-id="b59c1-118">The following restrictions apply to IMAP migrations:</span></span>
  
- <span data-ttu-id="b59c1-p106">Можно перемещать только элементы из папки "Входящие" и других папок почты. Миграция контактов, элементов календаря и задач невозможна.</span><span class="sxs-lookup"><span data-stu-id="b59c1-p106">Only items in a user's inbox or other mail folders can be migrated. You can't migrate contacts, calendar items, or tasks.</span></span>
    
- <span data-ttu-id="b59c1-121">Из почтового ящика пользователя можно перенести не более 500 000 элементов.</span><span class="sxs-lookup"><span data-stu-id="b59c1-121">A maximum of 500,000 items can be migrated from a user's mailbox.</span></span>
    
- <span data-ttu-id="b59c1-122">Максимальный размер сообщения, которое можно перенести, равен 35 МБ.</span><span class="sxs-lookup"><span data-stu-id="b59c1-122">The maximum message size that can be migrated is 35 MB.</span></span>
    
## <a name="migration-steps"></a><span data-ttu-id="b59c1-123">Шаги миграции</span><span class="sxs-lookup"><span data-stu-id="b59c1-123">Migration steps</span></span>

### <a name="step-1-prepare-for-an-imap-migration"></a><span data-ttu-id="b59c1-124">Шаг 1. Подготовка к миграции IMAP</span><span class="sxs-lookup"><span data-stu-id="b59c1-124">Step 1: Prepare for an IMAP migration</span></span>
<span data-ttu-id="b59c1-125"><a name="BK_Step1"> </a></span><span class="sxs-lookup"><span data-stu-id="b59c1-125"><a name="BK_Step1"> </a></span></span>

- <span data-ttu-id="b59c1-p107">**Если у организации IMAP есть домен, добавьте его в качестве обслуживаемого домена организации Office 365.** Если вы хотите использовать имеющийся домен для своих почтовых ящиков Office 365:, сначала его необходимо добавить в Office 365: в качестве обслуживаемого домена. После добавления вы можете создать пользователей в Office 365:. Дополнительные сведения см. в статье[Проверка домена в Office 365](https://go.microsoft.com/fwlink/p/?LinkId=534110).</span><span class="sxs-lookup"><span data-stu-id="b59c1-p107">**If you have a domain for you IMAP organization, add it as an accepted domain of your Office 365 organization.** If you want to use the same domain you already own for your Office 365 mailboxes, you first have to add it as an accepted domain to Office 365. After you have added it, you can create your users in Office 365. For more information, see[Verify your domain in Office 365](https://go.microsoft.com/fwlink/p/?LinkId=534110).</span></span>
    
- <span data-ttu-id="b59c1-p108">**Добавьте всех пользователей в Office 365:, чтобы у каждого из них был почтовый ящик Office 365:.** Инструкции см. в статье[Добавление пользователей в Office 365 для бизнеса](https://go.microsoft.com/fwlink/p/?LinkId=535065).</span><span class="sxs-lookup"><span data-stu-id="b59c1-p108">**Add each user to Office 365 so that they have an Office 365 mailbox.** For instructions, see[Add users to Office 365 for business](https://go.microsoft.com/fwlink/p/?LinkId=535065).</span></span>
    
- <span data-ttu-id="b59c1-p109">**Получите полное доменное имя (FQDN) сервера IMAP**. Необходимо указать полное доменное имя (FQDN) (которое также называется полным именем компьютера) сервера IMAP, из которого будут переноситься данные почтовых ящиков при создании конечной точки миграции IMAP. С помощью клиента IMAP или команды PING убедитесь, что это имя можно использовать для подключения к серверу IMAP через Интернет.</span><span class="sxs-lookup"><span data-stu-id="b59c1-p109">**Obtain the FQDN of the IMAP server**. You need to provide the fully qualified domain name (FQDN) (also called the full computer name) of the IMAP server that you will migrate mailbox data from when you create an IMAP migration endpoint. Use an IMAP client or the PING command to verify that you can use the FQDN to communicate with the IMAP server over the Internet.</span></span>
    
- <span data-ttu-id="b59c1-p110">**Настройте брандмауэр, разрешив подключения IMAP**. Может потребоваться открыть порты в брандмауэре организации, в которой размещен сервер IMAP, чтобы сетевой трафик, исходящий из центра обработки данных корпорации Майкрософт во время миграции, смог поступать в организацию, в которой размещен сервер IMAP. Список IP-адресов, используемых центрами обработки данных корпорации Майкрософт, см. в статье [URL-адреса и диапазоны IP-адресов Office 365](https://go.microsoft.com/fwlink/p/?LinkId=535066).</span><span class="sxs-lookup"><span data-stu-id="b59c1-p110">**Configure the firewall to allow IMAP connections**. You might have to open ports in the firewall of the organization that hosts the IMAP server so network traffic originating from the Microsoft datacenter during the migration is allowed to enter the organization that hosts the IMAP server. For a list of IP addresses used by Microsoft datacenters, see [Exchange Online URLs and IP Address Ranges](https://go.microsoft.com/fwlink/p/?LinkId=535066).</span></span>
    
- <span data-ttu-id="b59c1-p111">**Предоставьте учетной записи администратора разрешения на доступа к почтовым ящикам в организации IMAP**. Если в CSV-файле используются учетные данные администратора, применяемая учетная запись должна иметь необходимые разрешения на доступ к локальным почтовым ящикам. Разрешения, необходимые для доступа к почтовым ящикам пользователей, определяются конкретным сервером IMAP.</span><span class="sxs-lookup"><span data-stu-id="b59c1-p111">**Assign the administrator account permissions to access mailboxes in your IMAP organization**. If you use administrator credentials in the CSV file, the account that you use must have the necessary permissions to access the on-premises mailboxes. The permissions required to access user mailboxes is determined by the particular IMAP server.</span></span> 
    
- <span data-ttu-id="b59c1-p112">**Чтобы использовать командлеты Exchange Online PowerShell**, вам необходимо войти в систему и импортировать командлеты в локальный сеанс Windows PowerShell. Инструкции см в статье [Подключение к Exchange Online с помощью удаленной оболочки PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534121).</span><span class="sxs-lookup"><span data-stu-id="b59c1-p112">**To use the Exchange Online PowerShell cmdlets**, you need to sign in and import the cmdlets into your local Windows PowerShell session. See [Connect to Exchange Online using remote PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534121) for instructions.</span></span>
    
    <span data-ttu-id="b59c1-143">Полный список команд миграции см. в статье [Командлеты перемещения и миграции](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span><span class="sxs-lookup"><span data-stu-id="b59c1-143">For a full list of migration commands, see [Move and migration cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span></span>
    
- <span data-ttu-id="b59c1-p113">**Убедитесь, что вы можете подключиться к серверу IMAP**. Выполните следующую команду в Exchange Online PowerShell, чтобы проверить параметры подключения к серверу IMAP.</span><span class="sxs-lookup"><span data-stu-id="b59c1-p113">**Verify that you can connect to your IMAP server**. Run the following command in Exchange Online PowerShell to test the connection settings to your IMAP server.</span></span>
    
  ```
  Test-MigrationServerAvailability -IMAP -RemoteServer <FQDN of IMAP server> -Port <143 or 993> -Security <None, Ssl, or Tls>
  ```

    <span data-ttu-id="b59c1-146">Для параметра **Port** обычно устанавливается значение 143 для незашифрованных или TLS-соединений и значение 993 для SSL-соединений.</span><span class="sxs-lookup"><span data-stu-id="b59c1-146">For the value of the **Port** parameter, it's typical to use 143 for unencrypted or Transport Layer Security (TLS) connections and to use 993 for SSL connections.</span></span>
    
### <a name="step-2-create-a-csv-file-for-an-imap-migration-batch"></a><span data-ttu-id="b59c1-147">Шаг 2. Создание CSV-файла для пакета миграции IMAP.</span><span class="sxs-lookup"><span data-stu-id="b59c1-147">Step 2: Create a CSV file for an IMAP migration batch</span></span>
<span data-ttu-id="b59c1-148"><a name="BK_Step2"> </a></span><span class="sxs-lookup"><span data-stu-id="b59c1-148"><a name="BK_Step2"> </a></span></span>

<span data-ttu-id="b59c1-p114">Определите группу пользователей, миграцию чьих почтовых ящиков следует выполнить с помощью пакета миграции IMAP. Каждая строка в CSV-файле содержит сведения, необходимые для подключения к почтовому ящику в системе обмена сообщениями IMAP.</span><span class="sxs-lookup"><span data-stu-id="b59c1-p114">Identify the group of users whose mailboxes you want to migrate in an IMAP migration batch. Each row in the CSV file contains information necessary to connect to a mailbox in the IMAP messaging system.</span></span>
  
<span data-ttu-id="b59c1-151">Ниже приведены обязательные атрибуты для каждого пользователя.</span><span class="sxs-lookup"><span data-stu-id="b59c1-151">Here are the required attributes for each user:</span></span> 
  
- <span data-ttu-id="b59c1-152">**EmailAddress**. Задает идентификатор пользователя для его почтового ящика Office 365:.</span><span class="sxs-lookup"><span data-stu-id="b59c1-152">**EmailAddress** specifies the user ID for the user's Office 365 mailbox.</span></span>
    
- <span data-ttu-id="b59c1-153">**UserName**. Задает для учетной записи имя для входа, при помощи которого будет выполняться доступ к почтовому ящику на сервере IMAP.</span><span class="sxs-lookup"><span data-stu-id="b59c1-153">**UserName** specifies the logon name for the account to use to access the mailbox on the IMAP server.</span></span>
    
- <span data-ttu-id="b59c1-154">**Password**. Задает пароль для учетной записи в столбце **UserName**.</span><span class="sxs-lookup"><span data-stu-id="b59c1-154">**Password** specifies the password for the account in the **UserName** column.</span></span>
    
<span data-ttu-id="b59c1-p115">Ниже приведен пример формата CSV-файла. В этом примере выполняется миграция трех почтовых ящиков.</span><span class="sxs-lookup"><span data-stu-id="b59c1-p115">Here's an example of the format for the CSV file. In this example, three mailboxes are migrated:</span></span>
  
```
EmailAddress,UserName,Password
terrya@contoso.edu,terry.adams,1091990
annb@contoso.edu,ann.beebe,2111991
paulc@contoso.edu,paul.cannon,3281986
```

<span data-ttu-id="b59c1-157">В качестве значения атрибута **UserName** кроме имени пользователя можно использовать данные учетной записи, для которой назначены необходимые разрешения на доступ к почтовым ящикам на сервере IMAP. Ниже перечислены несколько специальных форматов, используемых для некоторых серверов IMAP.</span><span class="sxs-lookup"><span data-stu-id="b59c1-157">For the **UserName** attribute, in addition to the user name, you can use the credentials of an account that has been assigned the necessary permissions to access mailboxes on the IMAP server, the following are some of the specific formats used for some of the IMAP servers:</span></span>
  
 <span data-ttu-id="b59c1-158">**Microsoft Exchange**</span><span class="sxs-lookup"><span data-stu-id="b59c1-158">**Microsoft Exchange:**</span></span>
  
<span data-ttu-id="b59c1-p116">При переносе электронной почты с реализации IMAP в Microsoft Exchange для атрибута **UserName** в CSV-файле используется формат **домен/имя_администратора/имя_пользователя**. Предположим, выполняется перенос электронной почты Exchange для учетных записей Terry Adams, Ann Beebe и Chris Cannon. Имеется учетная запись администратора почты с именем пользователя **mailadmin** и паролем **P@ssw0rd**. Вот как будет выглядеть CSV-файл.</span><span class="sxs-lookup"><span data-stu-id="b59c1-p116">If you're migrating email from the IMAP implementation for Microsoft Exchange, use the format **Domain/Admin_UserName/User_UserName** for the **UserName** attribute in the CSV file. Let's say you're migrating email from Exchange for Terry Adams, Ann Beebe, and Paul Cannon. You have a mail administrator account, where the user name is **mailadmin** and the password is **P@ssw0rd**. Here's what your CSV file would look like:</span></span>
  
```
EmailAddress,UserName,Password
terrya@contoso.edu,contoso-students/mailadmin/terry.adams,P@ssw0rd
annb@contoso.edu,contoso-students/mailadmin/ann.beebe,P@ssw0rd
paulc@contoso.edu,contoso-students/mailadmin/paul.cannon,P@ssw0rd
```

 <span data-ttu-id="b59c1-163">**Dovecot**</span><span class="sxs-lookup"><span data-stu-id="b59c1-163">**Dovecot:**</span></span>
  
<span data-ttu-id="b59c1-p117">На серверах IMAP, поддерживающих протокол SASL, например Dovecot, используется формат **имя_пользователя*имя_администратора**, где звездочка ( * ) является настраиваемым знаком разделения. Допустим, переносится почта тех же пользователей с сервера IMAP Dovecot с использованием учетных данных администратора **mailadmin** и **P@ssw0rd**. Вот как будет выглядеть CSV-файл.</span><span class="sxs-lookup"><span data-stu-id="b59c1-p117">For IMAP servers that support Simple Authentication and Security Layer (SASL), such as a Dovecot IMAP server, use the format **User_UserName*Admin_UserName**, where the asterisk ( * ) is a configurable separator character. Let's say you're migrating those same users' email from a Dovecot IMAP server using the administrator credentials **mailadmin** and **P@ssw0rd**. Here's what your CSV file would look like:</span></span>
  
```
EmailAddress,UserName,Password
terrya@contoso.edu,terry.adams*mailadmin,P@ssw0rd
annb@contoso.edu,ann.beebe*mailadmin,P@ssw0rd
paulc@contoso.edu,paul.cannon*mailadmin,P@ssw0rd
```

 <span data-ttu-id="b59c1-167">**Mirapoint**</span><span class="sxs-lookup"><span data-stu-id="b59c1-167">**Mirapoint:**</span></span>
  
<span data-ttu-id="b59c1-p118">При переносе почты с сервера Mirapoint Message Server для учетных данных администратора используется формат **#пользователь@домен#имя_администратора#**. Для переноса электронной почты с Mirapoint с использованием учетных данных администратора **mailadmin** и **P@ssw0rd** CSV-файл должен выглядеть следующим образом.</span><span class="sxs-lookup"><span data-stu-id="b59c1-p118">If you're migrating email from Mirapoint Message Server, use the format **#user@domain#Admin_UserName#** for the administrator credentials. To migrate email from Mirapoint using the administrator credentials **mailadmin** and **P@ssw0rd**, your CSV file would look like this:</span></span>
  
```
EmailAddress,UserName,Password
terrya@contoso.edu,#terry.adams@contoso-students.edu#mailadmin#,P@ssw0rd
annb@contoso.edu,#ann.beebe@contoso-students.edu#mailadmin#,P@ssw0rd
paulc@contoso.edu,#paul.cannon@contoso-students.edu#mailadmin#,P@ssw0rd
```

 <span data-ttu-id="b59c1-170">**Courier-IMAP**</span><span class="sxs-lookup"><span data-stu-id="b59c1-170">**Courier IMAP:**</span></span>
  
<span data-ttu-id="b59c1-p119">Некоторые исходные системы электронной почты, такие как Courier IMAP, не поддерживают использование учетных данных администратора почтовых ящиков для переноса почтовых ящиков в Office 365:. В таком случае исходную систему электронной почты необходимо настроить на использование виртуальных общих папок. С помощью виртуальных общих папок вы можете использовать учетные данные администратора почтовых ящиков для доступа к почтовым ящикам пользователей в исходной системе электронной почты. Дополнительные сведения о настройке виртуальных общих папок для Courier IMAP см. в статье [Общие папки](https://go.microsoft.com/fwlink/p/?LinkId=398870).</span><span class="sxs-lookup"><span data-stu-id="b59c1-p119">Some source email systems, such as Courier IMAP, don't support using mailbox admin credentials to migrate mailboxes to Office 365. Instead, you can set up your source email system to use virtual shared folders. By using virtual shared folders, you can use the mailbox admin credentials to access user mailboxes on the source email system. For more information about how to configure virtual shared folders for Courier IMAP, see [Shared Folders](https://go.microsoft.com/fwlink/p/?LinkId=398870).</span></span>
  
<span data-ttu-id="b59c1-p120">Чтобы перенести почтовые ящики после настройки виртуальных общих папок в исходной системе электронной почты, в файл миграции необходимо включить необязательный атрибут **UserRoot**. Этот атрибут определяет расположение каждого пользовательского почтового ящика в структуре виртуальных общих папок в исходной системе электронной почты. Например, путь к почтовому ящику пользователя Terry  /users/terry.adams.</span><span class="sxs-lookup"><span data-stu-id="b59c1-p120">To migrate mailboxes after you set up virtual shared folders on your source email system, you have to include the optional attribute **UserRoot** in the migration file. This attribute specifies the location of each user's mailbox in the virtual shared folder structure on the source email system. For example, the path to Terry's mailbox is /users/terry.adams.</span></span>
  
<span data-ttu-id="b59c1-178">Ниже приведен пример CSV-файла, содержащего атрибут **UserRoot**.</span><span class="sxs-lookup"><span data-stu-id="b59c1-178">Here's an example of a CSV file that contains the **UserRoot** attribute:</span></span>
  
```
EmailAddress,UserName,Password,UserRoot
terrya@contoso.edu,mailadmin,P@ssw0rd,/users/terry.adams
annb@contoso.edu,mailadmin,P@ssw0rd,/users/ann.beebe
paulc@contoso.edu,mailadmin,P@ssw0rd,/users/paul.cannon
```

### <a name="step-3-create-an-imap-migration-endpoint"></a><span data-ttu-id="b59c1-179">Шаг 3. Создание конечной точки миграции IMAP</span><span class="sxs-lookup"><span data-stu-id="b59c1-179">Step 3: Create an IMAP migration endpoint</span></span>
<span data-ttu-id="b59c1-180"><a name="BK_Step3"> </a></span><span class="sxs-lookup"><span data-stu-id="b59c1-180"><a name="BK_Step3"> </a></span></span>

<span data-ttu-id="b59c1-p121">Для успешного переноса электронной почты решение Office 365: должно обмениваться данными с исходной системой электронной почты. Для этого в Office 365: используется конечная точка миграции. Конечная точка миграции также определяет количество почтовых ящиков для одновременной миграции и для одновременной синхронизации в процессе добавочной синхронизации, которая осуществляется один раз каждые 24 часа. Чтобы создать конечную точку миграции IMAP, сначала [подключитесь к Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121).</span><span class="sxs-lookup"><span data-stu-id="b59c1-p121">To migrate email successfully, Office 365 needs to connect to and communicate with the source email system. To do this, Office 365 uses a migration endpoint. The migration endpoint also defines the number of mailboxes to migrate simultaneously and the number of mailboxes to synchronize simultaneously during incremental synchronization, which occurs once every 24 hours. To create a migration end point for IMAP migration, first [connect to Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121).</span></span> 
  
<span data-ttu-id="b59c1-185">Полный список команд миграции см. в статье [Командлеты перемещения и миграции](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span><span class="sxs-lookup"><span data-stu-id="b59c1-185">For a full list of migration commands, see [Move and migration cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span></span>
  
<span data-ttu-id="b59c1-186">Чтобы создать конечную точку миграции IMAP с именем IMAPEndpoint в Exchange Online PowerShell, выполните следующую команду.</span><span class="sxs-lookup"><span data-stu-id="b59c1-186">To create the IMAP migration endpoint called "IMAPEndpoint" in Exchange Online PowerShell, run the following command:</span></span>
  
```
New-MigrationEndpoint -IMAP -Name IMAPEndpoint -RemoteServer imap.contoso.com -Port 993 -Security Ssl

```

<span data-ttu-id="b59c1-p122">Вы также можете добавить параметры, чтобы указать одновременно выполняемые миграции (в том числе добавочные) и используемый порт. Следующая команда Exchange Online PowerShell создает конечную точку миграции IMAP с именем IMAPEndpoint, которая поддерживает 50 одновременных миграций и до 25 одновременных добавочных синхронизаций. В этом примере конечная точка также настраивается на использование порта 143 для шифрования TLS.</span><span class="sxs-lookup"><span data-stu-id="b59c1-p122">You can also add parameters to specify concurrent migrations, concurrent incremental migrations, and the port to use. The following Exchange Online PowerShell command creates an IMAP migration endpoint called "IMAPEndpoint" that supports 50 concurrent migrations and up to 25 concurrent incremental synchronizations. It also configures the endpoint to use port 143 for TLS encryption.</span></span>
  
```
New-MigrationEndpoint -IMAP -Name IMAPEndpoint -RemoteServer imap.contoso.com -Port 143 -Security Tls -MaxConcurrentMigrations
50 -MaxConcurrentIncrementalSyncs 25
```

<span data-ttu-id="b59c1-190">Дополнительные сведения о командлете **New-MigrationEndpoint** см. в статье[New-MigrationEndpoint](https://go.microsoft.com/fwlink/p/?LinkId=536437).</span><span class="sxs-lookup"><span data-stu-id="b59c1-190">For more information about the **New-MigrationEndpoint** cmdlet, see[New-MigrationEndpoint](https://go.microsoft.com/fwlink/p/?LinkId=536437).</span></span>
  
#### <a name="verify-it-worked"></a><span data-ttu-id="b59c1-191">Проверка работы</span><span class="sxs-lookup"><span data-stu-id="b59c1-191">Verify it worked</span></span>

<span data-ttu-id="b59c1-192">Выполните следующую команду в Exchange Online PowerShell, чтобы отобразить сведения о конечной точке миграции IMAPEndpoint.</span><span class="sxs-lookup"><span data-stu-id="b59c1-192">Run the following command in Exchange Online PowerShell to display information about the "IMAPEndpoint":</span></span>
  
```
Get-MigrationEndpoint IMAPEndpoint | Format-List EndpointType,RemoteServer,Port,Security,Max*
```

### <a name="step-4-create-and-start-an-imap-migration-batch"></a><span data-ttu-id="b59c1-193">Шаг 4. Создание и запуск пакета миграции IMAP</span><span class="sxs-lookup"><span data-stu-id="b59c1-193">Step 4: Create and start an IMAP migration batch</span></span>
<span data-ttu-id="b59c1-194"><a name="BK_Step4"> </a></span><span class="sxs-lookup"><span data-stu-id="b59c1-194"><a name="BK_Step4"> </a></span></span>

<span data-ttu-id="b59c1-p123">Для создания пакета миграции IMAP можно использовать командлет [New-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536439). Можно создать пакет миграции и запустить его обработку автоматически, включив параметр  _AutoStart_. Кроме того, вы можете создать пакет миграции и запустить его с помощью командлета [Start-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536440).</span><span class="sxs-lookup"><span data-stu-id="b59c1-p123">You can use the [New-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536439) cmdlet to create a migration batch for an IMAP migration. You can create a migration batch and start it automatically by including the _AutoStart_ parameter. Alternatively, you can create the migration batch and then start it afterwards by using the[Start-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536440) cmdlet.</span></span>
  
<span data-ttu-id="b59c1-198">Следующая команда Exchange Online PowerShell автоматически запустит пакет миграции IMAPBatch1 с использованием конечной точки IMAP с именем IMAPEndpoint.</span><span class="sxs-lookup"><span data-stu-id="b59c1-198">The following Exchange Online PowerShell command will automatically start the migration batch called "IMAPBatch1" using the IMAP endpoint called "IMAPEndpoint":</span></span>
  
```
New-MigrationBatch -Name IMAPBatch1 -SourceEndpoint IMAPEndpoint -CSVData ([System.IO.File]::ReadAllBytes("C:\\Users\\Administrator\\Desktop\\IMAPmigration_1.csv")) -AutoStart
```

#### <a name="verify-it-worked"></a><span data-ttu-id="b59c1-199">Проверка работы</span><span class="sxs-lookup"><span data-stu-id="b59c1-199">Verify it worked</span></span>

<span data-ttu-id="b59c1-200">Выполните командлет [Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441), чтобы отобразить сведения о пакете миграции IMAPBatch1.</span><span class="sxs-lookup"><span data-stu-id="b59c1-200">Run the [Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441) cmdlet to display information about the "IMAPBatch1":</span></span>
  
```
Get-MigrationBatch -Identity IMAPBatch1 | Format-List
```

<span data-ttu-id="b59c1-201">Вы также можете убедиться, что пакет запущен, выполнив следующую команду.</span><span class="sxs-lookup"><span data-stu-id="b59c1-201">You can also verify that the batch has started by running the following command:</span></span>
  
```
Get-MigrationBatch -Identity IMAPBatch1 | Format-List Status
```

### <a name="step-5-route-your-email-to-office-365"></a><span data-ttu-id="b59c1-202">Шаг 5. Маршрутизация электронной почты в Office 365</span><span class="sxs-lookup"><span data-stu-id="b59c1-202">Step 5: Route your email to Office 365</span></span>
<span data-ttu-id="b59c1-203"><a name="BK_Step5"> </a></span><span class="sxs-lookup"><span data-stu-id="b59c1-203"><a name="BK_Step5"> </a></span></span>

<span data-ttu-id="b59c1-p124">Чтобы выяснить, куда доставлять сообщения электронной почты, системы электронной почты используют DNS-запись, которая называется записью MX. В процессе миграции электронной почты запись MX указывала на вашу исходную систему электронной почты. Теперь, когда перенос электронной почты в Office 365: завершен, запись MX должна указывать на Office 365:. Это обеспечит доставку электронной почты в ваши почтовые ящики Office 365:. Перемещая запись MX, вы также сможете отключить старую систему электронной почты, когда будете готовы сделать это.</span><span class="sxs-lookup"><span data-stu-id="b59c1-p124">Email systems use a DNS record called an MX record to figure out where to deliver emails. During the email migration process, your MX record was pointing to your source email system. Now that the email migration to Office 365 is complete, it's time to point your MX record at Office 365. This helps make sure that email is delivered to your Office 365 mailboxes. By moving the MX record, you can also turn off your old email system when you're ready.</span></span> 
  
<span data-ttu-id="b59c1-p125">Многим поставщикам DNS следует придерживаться инструкций по [изменению записи MX](https://go.microsoft.com/fwlink/p/?LinkId=279163). Если ваш поставщик DNS не включен в этот список, или если вы хотите получить представление об общих указаниях, см. [статью с общими инструкции в отношении записи MX](https://go.microsoft.com/fwlink/?LinkId=397449).</span><span class="sxs-lookup"><span data-stu-id="b59c1-p125">For many DNS providers, there are specific instructions to [change your MX record](https://go.microsoft.com/fwlink/p/?LinkId=279163). If your DNS provider isn't included, or if you want to get a sense of the general directions, [general MX record instructions ](https://go.microsoft.com/fwlink/?LinkId=397449) are provided as well.</span></span>
  
<span data-ttu-id="b59c1-p126">Системам электронной почты клиентов и партнеров может потребоваться до 72 часов, чтобы распознать измененную запись MX. Подождите по крайней мере 72 часа, прежде чем перейти к следующей задаче: Шаг 6. Удаление пакета миграции IMAP.</span><span class="sxs-lookup"><span data-stu-id="b59c1-p126">It can take up to 72 hours for the email systems of your customers and partners to recognize the changed MX record. Wait at least 72 hours before you proceed to the next task: Step 6: Delete IMAP migration batch.</span></span> 
  
### <a name="step-6-delete-imap-migration-batch"></a><span data-ttu-id="b59c1-213">Шаг 6. Удаление пакета миграции IMAP</span><span class="sxs-lookup"><span data-stu-id="b59c1-213">Step 6: Delete IMAP migration batch</span></span>
<span data-ttu-id="b59c1-214"><a name="BK_Step6"> </a></span><span class="sxs-lookup"><span data-stu-id="b59c1-214"><a name="BK_Step6"> </a></span></span>

<span data-ttu-id="b59c1-p127">После того как вы измените запись MX и убедитесь, что вся электронная почта направляется в почтовые ящики Office 365:, уведомите пользователей о том, что их сообщения доставляются в Office 365. Затем можно удалить пакет миграции IMAP. Убедитесь в следующем, прежде чем удалить пакет миграции.</span><span class="sxs-lookup"><span data-stu-id="b59c1-p127">After you change the MX record and verify that all email is being routed to Office 365 mailboxes, notify the users that their mail is going to Office 365. After this, you can delete the IMAP migration batch. Verify the following before you delete the migration batch.</span></span>
  
- <span data-ttu-id="b59c1-p128">Все пользователи используют почтовые ящики Office 365:. После удаления пакета почта, отправляемая в почтовые ящики на локальном сервере Exchange Server, не копируется в соответствующие почтовые ящики Office 365:.</span><span class="sxs-lookup"><span data-stu-id="b59c1-p128">All users are using Office 365 mailboxes. After the batch is deleted, mail sent to mailboxes on the on-premises Exchange Server isn't copied to the corresponding Office 365 mailboxes.</span></span>
    
- <span data-ttu-id="b59c1-p129">Почтовые ящики Office 365: синхронизированы по крайней мере один раз после того, как почта стала доставляться непосредственно в них. Для этого убедитесь, что значение в поле "Время последней синхронизации" для пакета миграции позже даты и времени, когда почта стала направляться непосредственно в почтовые ящики Office 365:.</span><span class="sxs-lookup"><span data-stu-id="b59c1-p129">Office 365 mailboxes were synchronized at least once after mail began being sent directly to them. To do this, make sure that the value in the Last Synced Time box for the migration batch is more recent than when mail started being routed directly to Office 365 mailboxes.</span></span>
    
<span data-ttu-id="b59c1-222">Чтобы удалить пакет миграции IMAPBatch1 в Exchange Online PowerShell, выполните следующую команду.</span><span class="sxs-lookup"><span data-stu-id="b59c1-222">To delete the "IMAPBatch1" migration batch from Exchange Online PowerShell, run the following command:</span></span>
  
```
Remove-MigrationBatch -Identity IMAPBatch1
```

<span data-ttu-id="b59c1-223">Дополнительные сведения о командлете **Remove-MigrationBatch** см. в статье[Remove-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536481).</span><span class="sxs-lookup"><span data-stu-id="b59c1-223">For more information about the **Remove-MigrationBatch** cmdlet, see[Remove-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536481).</span></span>
  
#### <a name="verify-it-worked"></a><span data-ttu-id="b59c1-224">Проверка работы</span><span class="sxs-lookup"><span data-stu-id="b59c1-224">Verify it worked</span></span>

<span data-ttu-id="b59c1-225">Выполните следующую команду в Exchange Online PowerShell, чтобы отобразить сведения о пакете миграции IMAPBatch1.</span><span class="sxs-lookup"><span data-stu-id="b59c1-225">Run the following command in Exchange Online PowerShell to display information about the "IMAPBatch1":</span></span>
  
```
Get-MigrationBatch IMAPBatch1"
```

<span data-ttu-id="b59c1-226">Команда либо вернет пакет миграции с состоянием **Удаление**, либо вернет ошибку (не удалось найти пакет миграции), что подтверждает удаление пакета миграции.</span><span class="sxs-lookup"><span data-stu-id="b59c1-226">The command will return either the migration batch with a status of **Removing**, or it will return an error stating that migration batch couldn't be found, verifying that the batch was deleted.</span></span>
  
<span data-ttu-id="b59c1-227">Дополнительные сведения о командлете **Get-MigrationBatch** см. в статье[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441).</span><span class="sxs-lookup"><span data-stu-id="b59c1-227">For more information about the **Get-MigrationBatch** cmdlet, see[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="b59c1-228">См. также</span><span class="sxs-lookup"><span data-stu-id="b59c1-228">See also</span></span>

#### 

[<span data-ttu-id="b59c1-229">Средство устранения неполадок миграции IMAP</span><span class="sxs-lookup"><span data-stu-id="b59c1-229">IMAP Migration Troubleshooter</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536482)

