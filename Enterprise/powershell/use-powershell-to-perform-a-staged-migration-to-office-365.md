---
title: Выполнение поэтапной миграции в Microsoft 365 с помощью PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: a20f9dbd-6102-4ffa-b72c-ff813e700930
description: 'Сводка: в этой статье рассказывается, как использовать Windows PowerShell для поэтапной миграции в Microsoft 365.'
ms.openlocfilehash: bc21ec403b0c6daa3fe2411f8f4fea790dd5e71c
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/22/2020
ms.locfileid: "45229795"
---
# <a name="use-powershell-to-perform-a-staged-migration-to-microsoft-365"></a><span data-ttu-id="c6657-103">Выполнение поэтапной миграции в Microsoft 365 с помощью PowerShell</span><span class="sxs-lookup"><span data-stu-id="c6657-103">Use PowerShell to perform a staged migration to Microsoft 365</span></span>

<span data-ttu-id="c6657-104">*Эта статья относится как к Microsoft 365 Enterprise, так и к Office 365 корпоративный.*</span><span class="sxs-lookup"><span data-stu-id="c6657-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="c6657-105">Вы можете перенести содержимое почтовых ящиков пользователей из исходной системы электронной почты в Microsoft 365 со временем с помощью поэтапной миграции.</span><span class="sxs-lookup"><span data-stu-id="c6657-105">You can migrate the contents of user mailboxes from a source email system to Microsoft 365 over time using a staged migration.</span></span>
  
<span data-ttu-id="c6657-p101">В этой статье рассказывается о задачах, связанных с поэтапной миграцией электронной почты с помощью Exchange Online PowerShell. В теме, [что необходимо знать о поэтапной миграции электронной почты](https://go.microsoft.com/fwlink/p/?LinkId=536487), вы можете получить обзор процесса миграции. Когда вы знакомы с содержимым этой статьи, используйте эту ссылку, чтобы начать перенос почтовых ящиков из одной почтовой системы в другую.</span><span class="sxs-lookup"><span data-stu-id="c6657-p101">This article walks you through the tasks involved with for a staged email migration using Exchange Online PowerShell. The topic, [What you need to know about a staged email migration](https://go.microsoft.com/fwlink/p/?LinkId=536487), gives you an overview of the migration process. When you're comfortable with the contents of that article, use this one to begin migrating mailboxes from one email system to another.</span></span>
  
> [!NOTE]
> <span data-ttu-id="c6657-p102">Вы также можете выполнить поэтапную миграцию с помощью центра администрирования Exchange. [Выполните поэтапную миграцию электронной почты в Microsoft 365](https://go.microsoft.com/fwlink/p/?LinkId=536687).</span><span class="sxs-lookup"><span data-stu-id="c6657-p102">You can also use the Exchange admin center to perform staged migration. See [Perform a staged migration of email to Microsoft 365](https://go.microsoft.com/fwlink/p/?LinkId=536687).</span></span> 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="c6657-111">Что нужно знать перед началом работы?</span><span class="sxs-lookup"><span data-stu-id="c6657-111">What do you need to know before you begin?</span></span>

<span data-ttu-id="c6657-p103">Предполагаемое время выполнения задачи: 2-5 минут для создания пакета миграции. После запуска пакета миграции длительность переноса зависит от количества почтовых ящиков в пакете, размера каждого почтового ящика и доступной емкости сети. Сведения о других факторах, влияющих на время переноса почтовых ящиков в Microsoft 365, можно найти в разделе [производительность миграции](https://go.microsoft.com/fwlink/p/?LinkId=275079).</span><span class="sxs-lookup"><span data-stu-id="c6657-p103">Estimated time to complete this task: 2-5 minutes to create a migration batch. After the migration batch is started, the duration of the migration will vary based on the number of mailboxes in the batch, the size of each mailbox, and your available network capacity. For information about other factors that affect how long it takes to migrate mailboxes to Microsoft 365, see [Migration Performance](https://go.microsoft.com/fwlink/p/?LinkId=275079).</span></span>
  
<span data-ttu-id="c6657-p104">Для выполнения этой процедуры (процедур) необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в пункте "Миграция" статьи [Разрешения получателей](https://go.microsoft.com/fwlink/p/?LinkId=534105).</span><span class="sxs-lookup"><span data-stu-id="c6657-p104">You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Migration" entry in the [Recipients Permissions](https://go.microsoft.com/fwlink/p/?LinkId=534105) topic.</span></span>
  
<span data-ttu-id="c6657-p105">Чтобы использовать командлеты Exchange Online PowerShell, вам необходимо войти в систему и импортировать командлеты в локальный сеанс Windows PowerShell. Инструкции см в статье [Подключение к Exchange Online с помощью удаленной оболочки PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534121).</span><span class="sxs-lookup"><span data-stu-id="c6657-p105">To use the Exchange Online PowerShell cmdlets, you need to sign in and import the cmdlets into your local Windows PowerShell session. See [Connect to Exchange Online using remote PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534121) for instructions.</span></span>
  
<span data-ttu-id="c6657-119">Полный список команд миграции см. в статье [Командлеты перемещения и миграции](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span><span class="sxs-lookup"><span data-stu-id="c6657-119">For a full list of migration commands, see [Move and migration cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span></span>
  
## <a name="migration-steps"></a><span data-ttu-id="c6657-120">Шаги миграции</span><span class="sxs-lookup"><span data-stu-id="c6657-120">Migration steps</span></span>

### <a name="step-1-prepare-for-a-staged-migration"></a><span data-ttu-id="c6657-121">Шаг 1. Подготовка к поэтапной миграции</span><span class="sxs-lookup"><span data-stu-id="c6657-121">Step 1: Prepare for a staged migration</span></span>

<span data-ttu-id="c6657-122">Прежде чем переносить почтовые ящики в Microsoft 365 с помощью поэтапной миграции, в среду Exchange необходимо внести несколько изменений.</span><span class="sxs-lookup"><span data-stu-id="c6657-122">Before you migrate mailboxes to Microsoft 365 by using a staged migration, there are a few changes you must make to your Exchange environment.</span></span>
  
 <span data-ttu-id="c6657-p106">**Настройте Мобильный Outlook на локальном сервере Exchange Server**. Служба миграции электронной почты использует компонент Мобильный Outlook (также известный как RPC через HTTP) для подключения к локальному серверу Exchange Server. Сведения о настройке Мобильный Outlook для Exchange Server 2007 и Exchange 2003 см. в следующих статьях.</span><span class="sxs-lookup"><span data-stu-id="c6657-p106">**Configure Outlook Anywhere on your on-premises Exchange Server** The email migration service uses Outlook Anywhere (also known as RPC over HTTP), to connect to your on-premises Exchange Server. For information about how to set up Outlook Anywhere for Exchange Server 2007, and Exchange 2003, see the following:</span></span>
  
- [<span data-ttu-id="c6657-125">Exchange 2007. Инструкции по включению мобильного Outlook</span><span class="sxs-lookup"><span data-stu-id="c6657-125">Exchange 2007: How to Enable Outlook Anywhere</span></span>](https://go.microsoft.com/fwlink/?LinkID=167210)
    
- [<span data-ttu-id="c6657-126">Настройка мобильного Outlook в Exchange 2003</span><span class="sxs-lookup"><span data-stu-id="c6657-126">How to configure Outlook Anywhere with Exchange 2003</span></span>](https://go.microsoft.com/fwlink/?LinkID=167209)
    
> [!IMPORTANT]
> <span data-ttu-id="c6657-p107">В вашей конфигурации Мобильный Outlook необходимо использовать сертификат, выданный доверенным центром сертификации (ЦС). Мобильный Outlook невозможно настроить с помощью самозаверяющего сертификата. Дополнительные сведения см. в статье [Инструкции по настройке протокола SSL для мобильного Outlook](https://go.microsoft.com/fwlink/?LinkID=80875).</span><span class="sxs-lookup"><span data-stu-id="c6657-p107">You must use a certificate issued by a trusted certification authority (CA) with your Outlook Anywhere configuration. Outlook Anywhere can't be configured with a self-signed certificate. For more information, see [How to configure SSL for Outlook Anywhere](https://go.microsoft.com/fwlink/?LinkID=80875).</span></span> 
  
 <span data-ttu-id="c6657-130">**Необязательно. Убедитесь, что вы можете подключиться к своей организации Exchange с помощью Мобильный Outlook**. Для проверки параметров подключения воспользуйтесь одним из следующих методов.</span><span class="sxs-lookup"><span data-stu-id="c6657-130">**Optional: Verify that you can connect to your Exchange organization using Outlook Anywhere** Try one of the following methods to test your connection settings.</span></span>
  
- <span data-ttu-id="c6657-131">Используйте Outlook из-за пределов вашей корпоративной сети, чтобы подключиться к своему локальному почтовому ящику Exchange.</span><span class="sxs-lookup"><span data-stu-id="c6657-131">Use Outlook from outside your corporate network to connect to your on-premises Exchange mailbox.</span></span>
    
- <span data-ttu-id="c6657-p108">Проверьте параметры подключения с помощью [анализатора удаленных подключений (Майкрософт](https://https://testconnectivity.microsoft.com/) ). Используйте тесты мобильного Outlook (RPC через HTTP) или тесты автообнаружения Outlook.</span><span class="sxs-lookup"><span data-stu-id="c6657-p108">Use the [Microsoft Remote Connectivity Analyzer](https://https://testconnectivity.microsoft.com/) to test your connection settings. Use the Outlook Anywhere (RPC over HTTP) or Outlook Autodiscover tests.</span></span>
    
- <span data-ttu-id="c6657-134">В Exchange Online PowerShell выполните следующие команды.</span><span class="sxs-lookup"><span data-stu-id="c6657-134">Run the following commands in Exchange Online PowerShell:</span></span>
    
  ```powershell
  $Credentials = Get-Credential
  ```

  ```powershell
  Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress <email address for on-premises administrator> -Credentials $credentials
  ```

 <span data-ttu-id="c6657-p109">**Настройка разрешений** Локальная учетная запись пользователя, которая используется для подключения к локальной организации Exchange (также называемую администратором миграции), должна иметь необходимые разрешения для доступа к локальным почтовым ящикам, которые необходимо перенести в Microsoft 365. Эта учетная запись пользователя используется при подключении к почтовой системе путем создания конечной точки миграции позже в этой процедуре ([Шаг 3: создание конечной точки миграции](use-powershell-to-perform-a-staged-migration-to-office-365.md#BK_Endpoint) ).</span><span class="sxs-lookup"><span data-stu-id="c6657-p109">**Set permissions** The on-premises user account that you use to connect to your on-premises Exchange organization (also called the migration administrator) must have the necessary permissions to access the on-premises mailboxes that you want to migrate to Microsoft 365. This user account is used when you connect to your email system by creating a migration endpoint later in this procedure ([Step 3: Create a migration endpoint](use-powershell-to-perform-a-staged-migration-to-office-365.md#BK_Endpoint) ).</span></span>
  
<span data-ttu-id="c6657-137">Для переноса почтовых ящиков администратор должен иметь один из следующих наборов разрешений.</span><span class="sxs-lookup"><span data-stu-id="c6657-137">To migrate the mailboxes, the admin must have one of the following permission sets:</span></span>
  
- <span data-ttu-id="c6657-138">Он должен входить в группу **администраторов домена** в доменной службе Active Directory локальной организации.</span><span class="sxs-lookup"><span data-stu-id="c6657-138">Be a member of the **Domain Admins** group in Active Directory in the on-premises organization.</span></span>
    
    <span data-ttu-id="c6657-139"> или </span><span class="sxs-lookup"><span data-stu-id="c6657-139">or</span></span>
    
- <span data-ttu-id="c6657-140">Он должен получить разрешение на уровне **FullAccess** для каждого локального почтового ящика и разрешение **WriteProperty** на изменение свойства **TargetAddress** в локальных учетных записях пользователей.</span><span class="sxs-lookup"><span data-stu-id="c6657-140">Be assigned the **FullAccess** permission for each on-premises mailbox and the **WriteProperty** permission to modify the **TargetAddress** property on the on-premises user accounts.</span></span>
    
    <span data-ttu-id="c6657-141"> или </span><span class="sxs-lookup"><span data-stu-id="c6657-141">or</span></span>
    
- <span data-ttu-id="c6657-142">Он должен получить разрешение **Получать как** для базы данных локальных почтовых ящиков, в которой хранятся почтовые ящики пользователей, и разрешение **WriteProperty** на изменение свойства **TargetAddress** в локальных учетных записях пользователей.</span><span class="sxs-lookup"><span data-stu-id="c6657-142">Be assigned the **Receive As** permission on the on-premises mailbox database that stores user mailboxes and the **WriteProperty** permission to modify the **TargetAddress** property on the on-premises user accounts.</span></span>
    
<span data-ttu-id="c6657-143">Инструкции по настройке этих разрешений приведены в разделе [Назначение разрешений для переноса почтовых ящиков в Microsoft 365](https://go.microsoft.com/fwlink/?LinkId=521656).</span><span class="sxs-lookup"><span data-stu-id="c6657-143">For instructions about how to set these permissions, see [Assign permissions to migrate mailboxes to Microsoft 365](https://go.microsoft.com/fwlink/?LinkId=521656).</span></span>
  
 <span data-ttu-id="c6657-p110">**Отключите единую систему обмена сообщениями.** Если единая система обмена сообщениями включена для переносимых локальных почтовых ящиков, отключите ее перед миграцией. Включите эту систему по завершении миграции. Практические инструкции см. в статье[Выключение единой системы обмена сообщениями для пользователя](https://go.microsoft.com/fwlink/?LinkId=521891).</span><span class="sxs-lookup"><span data-stu-id="c6657-p110">**Disable Unified Messaging (UM)** If UM is turned on for the on-premises mailboxes you're migrating, turn off UM before migration. Turn on UM for the mailboxes after migration is complete. For how-to steps, see[disable unified messaging](https://go.microsoft.com/fwlink/?LinkId=521891).</span></span>
  
 <span data-ttu-id="c6657-p111">**Используйте синхронизацию службы каталогов для создания новых пользователей в Microsoft 365.** Синхронизация службы каталогов используется для создания всех локальных пользователей в организации Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="c6657-p111">**Use directory synchronization to create new users in Microsoft 365.** You use directory synchronization to create all the on-premises users in your Microsoft 365 organization.</span></span>
  
<span data-ttu-id="c6657-p112">После создания пользователей им необходимо предоставить лицензии. У вас есть 30 дней на то, чтобы добавить лицензии после создания пользователей. Инструкции по добавлению лицензий см. в разделе [Шаг 8. Необходимые действия после миграции](use-powershell-to-perform-a-staged-migration-to-office-365.md#BK_Postmigration).</span><span class="sxs-lookup"><span data-stu-id="c6657-p112">You need to license the users after they're created. You have 30 days to add licenses after the users are created. For steps to add licenses, see [Step 8: Complete post-migration tasks](use-powershell-to-perform-a-staged-migration-to-office-365.md#BK_Postmigration).</span></span>
  
 <span data-ttu-id="c6657-p113">Для синхронизации и создания локальных пользователей в Microsoft 365 вы можете использовать средство синхронизации Microsoft Azure Active Directory (Azure AD) или службы синхронизации Microsoft Azure AD. После переноса почтовых ящиков в Microsoft 365 вы можете управлять учетными записями пользователей в локальной организации и синхронизировать их с вашей организацией Microsoft 365. Более подробную информацию вы найдете в статье[Интеграция каталогов](https://go.microsoft.com/fwlink/?LinkId=521788) .</span><span class="sxs-lookup"><span data-stu-id="c6657-p113">You can use either the Microsoft Azure Active Directory (Azure AD) Synchronization Tool or the Microsoft Azure AD Sync Services  to synchronize and create your on-premises users in Microsoft 365. After mailboxes are migrated to Microsoft 365, you manage user accounts in your on-premises organization, and they're synchronized with your Microsoft 365 organization. For more information, see[Directory Integration](https://go.microsoft.com/fwlink/?LinkId=521788) .</span></span>
  
### <a name="step-2-create-a-csv-file-for-a-staged-migration-batch"></a><span data-ttu-id="c6657-155">Шаг 2. Создание CSV-файла для пакета поэтапной миграции</span><span class="sxs-lookup"><span data-stu-id="c6657-155">Step 2: Create a CSV file for a staged migration batch</span></span>

<span data-ttu-id="c6657-p114">После определения пользователей, чьи локальные почтовые ящики необходимо перенести в Microsoft 365, создайте пакет миграции с помощью CSV-файла с разделителями-запятыми (CSV). Каждая строка в CSV-файле, используемая Microsoft 365 для запуска миграции, содержит сведения о локальном почтовом ящике.</span><span class="sxs-lookup"><span data-stu-id="c6657-p114">After you identify the users whose on-premises mailboxes you want to migrate to Microsoft 365, you use a comma separated value (CSV ) file to create a migration batch. Each row in the CSV file—used by Microsoft 365 to run the migration—contains information about an on-premises mailbox.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="c6657-p115">Количество почтовых ящиков, которые можно перенести в Microsoft 365 с помощью поэтапной миграции, не ограничено. CSV-файл для пакета миграции может содержать не более 2 000 строк. Чтобы перенести более 2 000 почтовых ящиков, создайте дополнительные CSV-файлы и используйте каждый файл для создания нового пакета миграции.</span><span class="sxs-lookup"><span data-stu-id="c6657-p115">There isn't a limit for the number of mailboxes that you can migrate to Microsoft 365 using a staged migration. The CSV file for a migration batch can contain a maximum of 2,000 rows. To migrate more than 2,000 mailboxes, create additional CSV files and use each file to create a new migration batch.</span></span> 
  
 <span data-ttu-id="c6657-161">**Поддерживаемые атрибуты**</span><span class="sxs-lookup"><span data-stu-id="c6657-161">**Supported attributes**</span></span>
  
<span data-ttu-id="c6657-p116">CSV-файл для поэтапной миграции поддерживает три атрибута, которые описаны ниже. Каждая строка в CSV-файле соответствует почтовому ящику и должна содержать значение каждого из этих атрибутов.</span><span class="sxs-lookup"><span data-stu-id="c6657-p116">The CSV file for a staged migration supports the following three attributes. Each row in the CSV file corresponds to a mailbox and must contain a value for each of these attributes.</span></span>
  
|<span data-ttu-id="c6657-164">**Атрибут**</span><span class="sxs-lookup"><span data-stu-id="c6657-164">**Attribute**</span></span>|<span data-ttu-id="c6657-165">**Описание**</span><span class="sxs-lookup"><span data-stu-id="c6657-165">**Description**</span></span>|<span data-ttu-id="c6657-166">**Обязательный?**</span><span class="sxs-lookup"><span data-stu-id="c6657-166">**Required?**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="c6657-167">EmailAddress</span><span class="sxs-lookup"><span data-stu-id="c6657-167">EmailAddress</span></span>  <br/> |<span data-ttu-id="c6657-168">Задает основной SMTP-адрес электронной почты, например pilarp@contoso.com, для локальных почтовых ящиков.</span><span class="sxs-lookup"><span data-stu-id="c6657-168">Specifies the primary SMTP email address, for example, pilarp@contoso.com, for on-premises mailboxes.</span></span>  <br/> <span data-ttu-id="c6657-p117">Используйте основной SMTP-адрес для локальных почтовых ящиков, а не идентификаторов пользователей из Microsoft 365. Например, если локальный домен называется contoso.com, но домен электронной почты Microsoft 365 называется service.contoso.com, для адресов электронной почты в CSV-файле следует использовать доменное имя contoso.com.</span><span class="sxs-lookup"><span data-stu-id="c6657-p117">Use the primary SMTP address for on-premises mailboxes and not user IDs from the Microsoft 365. For example, if the on-premises domain is named contoso.com but the Microsoft 365 email domain is named service.contoso.com, you would use the contoso.com domain name for email addresses in the CSV file.</span></span>  <br/> |<span data-ttu-id="c6657-171">Обязательный</span><span class="sxs-lookup"><span data-stu-id="c6657-171">Required</span></span>  <br/> |
|<span data-ttu-id="c6657-172">Password</span><span class="sxs-lookup"><span data-stu-id="c6657-172">Password</span></span>  <br/> |<span data-ttu-id="c6657-p118">Пароль, заданный для нового почтового ящика Microsoft 365. Все ограничения паролей, применяемые к организации Microsoft 365, также применяются к паролям, включенным в CSV-файл.</span><span class="sxs-lookup"><span data-stu-id="c6657-p118">The password to be set for the new Microsoft 365 mailbox. Any password restrictions that are applied to your Microsoft 365 organization also apply to the passwords included in the CSV file.</span></span>  <br/> |<span data-ttu-id="c6657-175">Необязательный</span><span class="sxs-lookup"><span data-stu-id="c6657-175">Optional</span></span>  <br/> |
|<span data-ttu-id="c6657-176">ForceChangePassword</span><span class="sxs-lookup"><span data-stu-id="c6657-176">ForceChangePassword</span></span>  <br/> |<span data-ttu-id="c6657-p119">Указывает, должен ли пользователь изменить пароль при первом входе в новый почтовый ящик Microsoft 365. Используйте значение **true** или **false** для этого параметра.</span><span class="sxs-lookup"><span data-stu-id="c6657-p119">Specifies whether a user must change the password the first time they sign in to their new Microsoft 365 mailbox. Use **True** or **False** for the value of this parameter. </span></span><br/> <span data-ttu-id="c6657-179">> [!NOTE]> Если вы внедрили решение единого входа путем развертывания служб федерации Active Directory (AD FS) в локальной организации, для атрибута **ForceChangePassword** необходимо задать значение **False**.</span><span class="sxs-lookup"><span data-stu-id="c6657-179">> [!NOTE]> If you've implemented a single sign-on (SSO) solution by deploying Active Directory Federation Services (AD FS) or greater in your on-premises organization, you must use **False** for the value of the **ForceChangePassword** attribute.</span></span>          |<span data-ttu-id="c6657-180">Необязательный</span><span class="sxs-lookup"><span data-stu-id="c6657-180">Optional</span></span>  <br/> |
   
 <span data-ttu-id="c6657-181">**Формат CSV-файла**</span><span class="sxs-lookup"><span data-stu-id="c6657-181">**CSV file format**</span></span>
  
<span data-ttu-id="c6657-p120">Ниже приведен пример формата CSV-файла. В этом примере три локальных почтовых ящика переносятся в Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="c6657-p120">Here's an example of the format for the CSV file. In this example, three on-premises mailboxes are migrated to Microsoft 365.</span></span>
  
<span data-ttu-id="c6657-p121">В первой строке (строке заголовков CSV-файла) содержатся имена атрибутов или полей, значения которых находятся в последующих строках. Имя каждого атрибута отделяется запятой.</span><span class="sxs-lookup"><span data-stu-id="c6657-p121">The first row, or header row, of the CSV file lists the names of the attributes, or fields, specified in the rows that follow. Each attribute name is separated by a comma.</span></span>
  
```powershell
EmailAddress,Password,ForceChangePassword 
pilarp@contoso.com,Pa$$w0rd,False 
tobyn@contoso.com,Pa$$w0rd,False 
briant@contoso.com,Pa$$w0rd,False 
```

<span data-ttu-id="c6657-p122">Каждая строка под строкой заголовков представляет одного пользователя и содержит данные, используемые для переноса почтового ящика этого пользователя. Значения атрибутов в каждой строке должны следовать в том же порядке, что и имена атрибутов в строке заголовков.</span><span class="sxs-lookup"><span data-stu-id="c6657-p122">Each row under the header row represents one user and supplies the information that will be used to migrate the user's mailbox. The attribute values in each row must be in the same order as the attribute names in the header row.</span></span> 
  
<span data-ttu-id="c6657-p123">Создать CSV-файл можно с помощью любого текстового редактора или соответствующего приложения, например Excel. Сохраните файл как CSV- или TXT-файл.</span><span class="sxs-lookup"><span data-stu-id="c6657-p123">Use any text editor, or an application like Excel , to create the CSV file. Save the file as a .csv or .txt file.</span></span>
  
> [!NOTE]
> <span data-ttu-id="c6657-p124">Если CSV-файл содержит знаки, не входящие в ASCII, или специальные символы, сохраните его в кодировке UTF-8 или другой кодировке Юникода. В зависимости от приложения сохранить CSV-файл в кодировке UTF-8 или другой кодировке Юникода может оказаться проще, если язык системы соответствует языку, используемому в CSV-файле.</span><span class="sxs-lookup"><span data-stu-id="c6657-p124">If the CSV file contains non-ASCII or special characters, save the CSV file with UTF-8 or other Unicode encoding. Depending on the application, saving the CSV file with UTF-8 or other Unicode encoding can be easier when the system locale of the computer matches the language used in the CSV file.</span></span> 
  
### <a name="step-3-create-a-migration-endpoint"></a><span data-ttu-id="c6657-192">Шаг 3. Создание конечной точки миграции</span><span class="sxs-lookup"><span data-stu-id="c6657-192">Step 3: Create a migration endpoint</span></span>
<span data-ttu-id="c6657-193"><a name="BK_Endpoint"> </a></span><span class="sxs-lookup"><span data-stu-id="c6657-193"><a name="BK_Endpoint"> </a></span></span>

<span data-ttu-id="c6657-p125">Для успешной миграции электронной почты в Microsoft 365 необходимо подключиться к исходной почтовой системе и связаться с ней. Для этого в Microsoft 365 используется конечная точка миграции. Чтобы создать конечную точку миграции мобильного Outlook с помощью PowerShell для поэтапной миграции, сначала [подключитесь к Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121).</span><span class="sxs-lookup"><span data-stu-id="c6657-p125">To migrate email successfully, Microsoft 365 needs to connect and communicate with the source email system. To do this, Microsoft 365 uses a migration endpoint. To create an Outlook Anywhere migration endpoint by using PowerShell, for staged migration, first [connect to Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121).</span></span> 
  
<span data-ttu-id="c6657-197">Полный список команд миграции см. в статье [Командлеты перемещения и миграции](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span><span class="sxs-lookup"><span data-stu-id="c6657-197">For a full list of migration commands, see [Move and migration cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span></span>
  
<span data-ttu-id="c6657-198">Чтобы создать конечную точку миграции мобильного Outlook с именем StagedEndpoint в Exchange Online PowerShell, выполните следующие команды.</span><span class="sxs-lookup"><span data-stu-id="c6657-198">To create an Outlook Anywhere migration endpoint called "StagedEndpoint" in Exchange Online PowerShell, run the following commands:</span></span>
  
```powershell
$Credentials = Get-Credential
```

```powershell
New-MigrationEndpoint -ExchangeOutlookAnywhere -Name StagedEndpoint -Autodiscover -EmailAddress administrator@contoso.com -Credentials $Credentials
```

<span data-ttu-id="c6657-199">Дополнительные сведения о командлете **New-MigrationEndpoint** см. в статье[New-MigrationEndpoint](https://go.microsoft.com/fwlink/p/?LinkId=536437).</span><span class="sxs-lookup"><span data-stu-id="c6657-199">For more information about the **New-MigrationEndpoint** cmdlet, see[New-MigrationEndpoint](https://go.microsoft.com/fwlink/p/?LinkId=536437).</span></span>
  
> [!NOTE]
> <span data-ttu-id="c6657-p126">С помощью командлета **New-MigrationEndpoint** и параметра **-TargetDatabase** можно указать базу данных, которая будет использоваться службой. В противном случае база данных назначается случайным образом на сайте Службы федерации Active Directory (AD FS) 2.0, на котором расположен почтовый ящик управления.</span><span class="sxs-lookup"><span data-stu-id="c6657-p126">The **New-MigrationEndpoint** cmdlet can be used to specify a database for the service to use by using the **-TargetDatabase** option. Otherwise a database is randomly assigned from the Active Directory Federation Services (AD FS) 2.0 site where the management mailbox is located.</span></span>
  
#### <a name="verify-it-worked"></a><span data-ttu-id="c6657-202">Проверка работы</span><span class="sxs-lookup"><span data-stu-id="c6657-202">Verify it worked</span></span>

<span data-ttu-id="c6657-203">В Exchange Online PowerShell выполните следующую команду, чтобы отобразить сведения о конечной точке миграции StagedEndpoint.</span><span class="sxs-lookup"><span data-stu-id="c6657-203">In Exchange Online PowerShell, run the following command to display information about the "StagedEndpoint" migration endpoint:</span></span>
  
```powershell
Get-MigrationEndpoint StagedEndpoint | Format-List EndpointType,ExchangeServer,UseAutoDiscover,Max*
```

### <a name="step-4-create-and-start-a-stage-migration-batch"></a><span data-ttu-id="c6657-204">Шаг 4. Создание и запуск пакета поэтапной миграции</span><span class="sxs-lookup"><span data-stu-id="c6657-204">Step 4: Create and start a stage migration batch</span></span>
<span data-ttu-id="c6657-205"><a name="BK_Endpoint"> </a></span><span class="sxs-lookup"><span data-stu-id="c6657-205"><a name="BK_Endpoint"> </a></span></span>

<span data-ttu-id="c6657-p127">Чтобы создать пакет для прямой миграции, выполните командлет **New-MigrationBatch** в Exchange Online PowerShell. Можно создать пакет миграции и запустить его обработку автоматически, включив параметр _AutoStart_. Кроме того, вы можете создать пакет миграции, а затем вручную запустить его с помощью командлета **Start-MigrationBatch**. В этом примере создается пакет миграции StagedBatch1 и используется конечная точка миграции, созданная на предыдущем шаге.</span><span class="sxs-lookup"><span data-stu-id="c6657-p127">You can use the **New-MigrationBatch** cmdlet in Exchange Online PowerShell to create a migration batch for a cutover migration. You can create a migration batch and start it automatically by including the _AutoStart_ parameter. Alternatively, you can create the migration batch and then manually start it afterwards by using the **Start-MigrationBatch** cmdlet. This example creates a migration batch called "StagedBatch1" and uses the migration endpoint that was created in the previous step.</span></span>
  
```powershell
New-MigrationBatch -Name StagedBatch1 -SourceEndpoint StagedEndpoint -AutoStart
```

<span data-ttu-id="c6657-p128">В этом примере также создается пакет миграции StagedBatch1 и используется конечная точка миграции, созданная на предыдущем шаге. Так как параметр  _AutoStart_ не включен, пакет миграции необходимо запустить вручную на панели мониторинга миграции или с помощью командлета **Start-MigrationBatch**. Как было сказано выше, в одно и то же время может существовать только один пакет прямой миграции.</span><span class="sxs-lookup"><span data-stu-id="c6657-p128">This example also creates a migration batch called "StagedBatch1" and uses the migration endpoint that was created in the previous step. Because the  _AutoStart_ parameter isn't included, the migration batch has to be manually started on the migration dashboard or by using **Start-MigrationBatch** cmdlet. As previously stated, only one cutover migration batch can exist at a time.</span></span>
  
```powershell
New-MigrationBatch -Name StagedBatch1 -SourceEndpoint StagedEndpoint
```

#### <a name="verify-it-worked"></a><span data-ttu-id="c6657-213">Проверка работы</span><span class="sxs-lookup"><span data-stu-id="c6657-213">Verify it worked</span></span>

<span data-ttu-id="c6657-214">Выполните следующую команду в Exchange Online PowerShell, чтобы отобразить сведения о пакете миграции StagedBatch1.</span><span class="sxs-lookup"><span data-stu-id="c6657-214">Run the following command in Exchange Online PowerShell to display information about the "StagedBatch1":</span></span>
  
```powershell
Get-MigrationBatch -Identity StagedBatch1 | Format-List
```

<span data-ttu-id="c6657-215">Вы также можете убедиться, что пакет запущен, выполнив следующую команду.</span><span class="sxs-lookup"><span data-stu-id="c6657-215">You can also verify that the batch has started by running the following command:</span></span>
  
```powershell
Get-MigrationBatch -Identity StagedBatch1 | Format-List Status
```

<span data-ttu-id="c6657-216">Дополнительные сведения о командлете **Get-MigrationBatch** см. в статье[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441).</span><span class="sxs-lookup"><span data-stu-id="c6657-216">For more information about the **Get-MigrationBatch** cmdlet, see[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441).</span></span>
  
### <a name="step-5-convert-on-premises-mailboxes-to-mail-enabled-users"></a><span data-ttu-id="c6657-217">Шаг 5. Преобразование локальных почтовых ящиков в учетные записи пользователей, поддерживающих почту</span><span class="sxs-lookup"><span data-stu-id="c6657-217">Step 5: Convert on-premises mailboxes to mail-enabled users</span></span>
<span data-ttu-id="c6657-218"><a name="BK_Endpoint"> </a></span><span class="sxs-lookup"><span data-stu-id="c6657-218"><a name="BK_Endpoint"> </a></span></span>

<span data-ttu-id="c6657-p129">После успешного переноса пакета почтовых ящиков необходим какой – то способ, чтобы пользователи могли получить доступ к своей почте. Пользователь, чей почтовый ящик был перенесен, теперь имеет локальный почтовый ящик и один из них в Microsoft 365. Пользователи с почтовым ящиком в Microsoft 365 прекратят получать новую почту в своем локальном почтовом ящике.</span><span class="sxs-lookup"><span data-stu-id="c6657-p129">After you have successfully migrated a batch of mailboxes, you need some way to let users get to their mail. A user whose mailbox has been migrated now has both a mailbox on-premises and one in Microsoft 365. Users who have a mailbox in Microsoft 365 will stop receiving new mail in their on-premises mailbox.</span></span> 
  
<span data-ttu-id="c6657-p130">Так как вы не выполнили миграцию, вы пока не готовы перенаправлены к Microsoft 365 для всех пользователей. Так что же делать для тех, у кого есть оба? Вы можете изменить локальные почтовые ящики, которые вы уже выполнили миграцию, на пользователей с включенной поддержкой почты. При переходе с почтового ящика на пользователя с включенной поддержкой почты можно направить пользователя в электронную почту в Microsoft 365 вместо того, чтобы перейти к локальному почтовому ящику.</span><span class="sxs-lookup"><span data-stu-id="c6657-p130">Because you are not done with your migrations, you are not yet ready to direct all users to Microsoft 365 for their email. So what do you do for those people who have both? What you can do is change the on-premises mailboxes that you've already migrated to mail-enabled users. When you change from a mailbox to a mail-enabled user, you can direct the user to Microsoft 365 for their email instead of going to their on-premises mailbox.</span></span> 
  
<span data-ttu-id="c6657-p131">Еще одна важная причина преобразования локальных почтовых ящиков в пользователей с включенной поддержкой почты — хранение адресов прокси-серверов из почтовых ящиков Microsoft 365 путем копирования прокси-адресов в пользователей с включенной поддержкой почты. Это позволяет управлять облачными пользователями из локальной организации с помощью Active Directory. Кроме того, если вы решили списать локальную организацию Exchange Server после переноса всех почтовых ящиков в Microsoft 365, прокси-адреса, скопированные в пользователей с включенной поддержкой почты, останутся в локальной службе Active Directory.</span><span class="sxs-lookup"><span data-stu-id="c6657-p131">Another important reason to convert on-premises mailboxes to mail-enabled users is to retain proxy addresses from the Microsoft 365 mailboxes by copying proxy addresses to the mail-enabled users. This lets you manage cloud-based users from your on-premises organization by using Active Directory. Also, if you decide to decommission your on-premises Exchange Server organization after all mailboxes are migrated to Microsoft 365, the proxy addresses you've copied to the mail-enabled users will remain in your on-premises Active Directory.</span></span>
    
### <a name="step-6-delete-a-staged-migration-batch"></a><span data-ttu-id="c6657-229">Шаг 6. Удаление пакета поэтапной миграции</span><span class="sxs-lookup"><span data-stu-id="c6657-229">Step 6: Delete a staged migration batch</span></span>
<span data-ttu-id="c6657-230"><a name="BK_Endpoint"> </a></span><span class="sxs-lookup"><span data-stu-id="c6657-230"><a name="BK_Endpoint"> </a></span></span>

 <span data-ttu-id="c6657-231">После успешного переноса всех почтовых ящиков из пакета миграции и преобразования локальных почтовых ящиков из пакета в учетные записи пользователей, поддерживающих почту, пакет поэтапной миграции можно удалить.</span><span class="sxs-lookup"><span data-stu-id="c6657-231">After all mailboxes in a migration batch have been successfully migrated, and you've converted the on-premises mailboxes in the batch to mail-enabled users, you're ready to delete a staged migration batch.</span></span> <span data-ttu-id="c6657-232">Обязательно убедитесь, что почта перенаправляется в почтовые ящики Microsoft 365 в пакете миграции.</span><span class="sxs-lookup"><span data-stu-id="c6657-232">Be sure to verify that mail is being forwarded to the Microsoft 365 mailboxes in the migration batch.</span></span> <span data-ttu-id="c6657-233">При удалении пакета поэтапной миграции служба миграции удаляет все записи, связанные с пакетом, а также сам пакет.</span><span class="sxs-lookup"><span data-stu-id="c6657-233">When you delete a staged migration batch, the migration service cleans up any records related to the migration batch and deletes the migration batch.</span></span>
  
<span data-ttu-id="c6657-234">Чтобы удалить пакет миграции StagedBatch1 в Exchange Online PowerShell, выполните следующую команду.</span><span class="sxs-lookup"><span data-stu-id="c6657-234">To delete the "StagedBatch1" migration batch in Exchange Online PowerShell, run the following command.</span></span>
  
```powershell
Remove-MigrationBatch -Identity StagedBatch1
```

<span data-ttu-id="c6657-235">Дополнительные сведения о командлете **Remove-MigrationBatch** см. в статье[Remove-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536481).</span><span class="sxs-lookup"><span data-stu-id="c6657-235">For more information about the **Remove-MigrationBatch** cmdlet, see[Remove-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536481).</span></span>
  
#### <a name="verify-it-worked"></a><span data-ttu-id="c6657-236">Проверка работы</span><span class="sxs-lookup"><span data-stu-id="c6657-236">Verify it worked</span></span>

<span data-ttu-id="c6657-237">Выполните следующую команду в Exchange Online PowerShell, чтобы отобразить сведения о пакете миграции IMAPBatch1.</span><span class="sxs-lookup"><span data-stu-id="c6657-237">Run the following command in Exchange Online PowerShell to display information about the "IMAPBatch1":</span></span>
  
```powershell
Get-MigrationBatch StagedBatch1
```

<span data-ttu-id="c6657-238">Команда либо вернет пакет миграции с состоянием **Удаление**, либо вернет ошибку (не удалось найти пакет миграции), что подтверждает удаление пакета миграции.</span><span class="sxs-lookup"><span data-stu-id="c6657-238">The command will return either the migration batch with a status of **Removing**, or it will return an error stating that migration batch couldn't be found, verifying that the batch was deleted.</span></span>
  
<span data-ttu-id="c6657-239">Дополнительные сведения о командлете **Get-MigrationBatch** см. в статье[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441).</span><span class="sxs-lookup"><span data-stu-id="c6657-239">For more information about the **Get-MigrationBatch** cmdlet, see[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441).</span></span>
  
### <a name="step7-assign-licenses-to-microsoft-365-users"></a><span data-ttu-id="c6657-240">Step7: Назначение лицензий пользователям Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="c6657-240">Step7: Assign licenses to Microsoft 365 users</span></span>
<span data-ttu-id="c6657-241"><a name="BK_Endpoint"> </a></span><span class="sxs-lookup"><span data-stu-id="c6657-241"><a name="BK_Endpoint"> </a></span></span>

<span data-ttu-id="c6657-242">Активируйте учетные записи пользователей Microsoft 365 для мигрировавших учетных записей, назначая лицензии.</span><span class="sxs-lookup"><span data-stu-id="c6657-242">Activate Microsoft 365 user accounts for the migrated accounts by assigning licenses.</span></span> <span data-ttu-id="c6657-243">Если не назначить лицензию, почтовый ящик отключится по окончании льготного периода (30 дней).</span><span class="sxs-lookup"><span data-stu-id="c6657-243">If you don't assign a license, the mailbox is disabled when the grace period (30 days) ends.</span></span> <span data-ttu-id="c6657-244">Чтобы назначить лицензию в центре администрирования Microsoft 365, ознакомьтесь со статьей [назначение и отмена назначения лицензий](https://docs.microsoft.com/microsoft-365/admin/manage/assign-licenses-to-users).</span><span class="sxs-lookup"><span data-stu-id="c6657-244">To assign a license in the Microsoft 365 admin center, see [Assign or unassign licenses](https://docs.microsoft.com/microsoft-365/admin/manage/assign-licenses-to-users).</span></span>
  
### <a name="step-8-complete-post-migration-tasks"></a><span data-ttu-id="c6657-245">Шаг 8. Необходимые действия после миграции</span><span class="sxs-lookup"><span data-stu-id="c6657-245">Step 8: Complete post-migration tasks</span></span>
<span data-ttu-id="c6657-246"><a name="BK_Postmigration"> </a></span><span class="sxs-lookup"><span data-stu-id="c6657-246"><a name="BK_Postmigration"> </a></span></span>

- <span data-ttu-id="c6657-247">**Создайте DNS-запись автообнаружения, чтобы пользователи смогли с легкостью получить доступ к своим почтовым ящикам.**</span><span class="sxs-lookup"><span data-stu-id="c6657-247">**Create an Autodiscover DNS record so users can easily get to their mailboxes.**</span></span> <span data-ttu-id="c6657-248">После переноса всех локальных почтовых ящиков в Microsoft 365 вы можете настроить запись DNS службы автообнаружения для организации Microsoft 365, чтобы пользователи могли легко подключаться к новым почтовым ящикам Microsoft 365 с Outlook и мобильными клиентами.</span><span class="sxs-lookup"><span data-stu-id="c6657-248">After all on-premises mailboxes are migrated to Microsoft 365, you can configure an Autodiscover DNS record for your Microsoft 365 organization to enable users to easily connect to their new Microsoft 365 mailboxes with Outlook and mobile clients.</span></span> <span data-ttu-id="c6657-249">Эта новая запись DNS автообнаружения должна использовать то же пространство имен, которое вы используете для вашей организации Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="c6657-249">This new Autodiscover DNS record has to use the same namespace that you're using for your Microsoft 365 organization.</span></span> <span data-ttu-id="c6657-250">Например, если пространство имен облачной службы имеет значение cloud.contoso.com, необходимо создать запись DNS автообнаружения autodiscover.cloud.contoso.com.</span><span class="sxs-lookup"><span data-stu-id="c6657-250">For example, if your cloud-based namespace is cloud.contoso.com, the Autodiscover DNS record you need to create is autodiscover.cloud.contoso.com.</span></span>
    
    <span data-ttu-id="c6657-251">В Microsoft 365 для реализации службы автообнаружения для клиентов Outlook и мобильных устройств используется запись CNAME.</span><span class="sxs-lookup"><span data-stu-id="c6657-251">Microsoft 365 uses a CNAME record to implement the Autodiscover service for Outlook and mobile clients.</span></span> <span data-ttu-id="c6657-252">Запись CNAME автообнаружения должна содержать следующие сведения:</span><span class="sxs-lookup"><span data-stu-id="c6657-252">The Autodiscover CNAME record must contain the following information:</span></span>
    
  - <span data-ttu-id="c6657-253">**Псевдоним:** autodiscover</span><span class="sxs-lookup"><span data-stu-id="c6657-253">**Alias:** autodiscover</span></span>
    
  - <span data-ttu-id="c6657-254">**Целевой объект:** autodiscover.outlook.com</span><span class="sxs-lookup"><span data-stu-id="c6657-254">**Target:** autodiscover.outlook.com</span></span>
    
    <span data-ttu-id="c6657-255">Дополнительные сведения см. [в статье Добавление DNS-записей для подключения к домену](https://go.microsoft.com/fwlink/p/?LinkId=535028).</span><span class="sxs-lookup"><span data-stu-id="c6657-255">For more information, see [Add DNS records to connect your domain](https://go.microsoft.com/fwlink/p/?LinkId=535028).</span></span>
    
- <span data-ttu-id="c6657-256">**Спишите локальные сервера Exchange.**</span><span class="sxs-lookup"><span data-stu-id="c6657-256">**Decommission on-premises Exchange servers.**</span></span> <span data-ttu-id="c6657-257">После проверки того, что вся электронная почта направляется непосредственно в почтовые ящики Microsoft 365, и вам больше не нужна поддержка локальной организации электронной почты или не планируется внедрять решение единого входа, вы можете удалить Exchange с серверов и удалить локальную организацию Exchange.</span><span class="sxs-lookup"><span data-stu-id="c6657-257">After you've verified that all email is being routed directly to the Microsoft 365 mailboxes, and you no longer need to maintain your on-premises email organization or don't plan on implementing an SSO solution, you can uninstall Exchange from your servers and remove your on-premises Exchange organization.</span></span>
    
    <span data-ttu-id="c6657-258">Дополнительные сведения см. в следующих статьях:</span><span class="sxs-lookup"><span data-stu-id="c6657-258">For more information, see the following:</span></span>
    
  - [<span data-ttu-id="c6657-259">Изменение или удаление Exchange 2010</span><span class="sxs-lookup"><span data-stu-id="c6657-259">Modify or Remove Exchange 2010</span></span>](https://go.microsoft.com/fwlink/?LinkId=217936)
    
  - [<span data-ttu-id="c6657-260">Удаление организации Exchange 2007</span><span class="sxs-lookup"><span data-stu-id="c6657-260">How to Remove an Exchange 2007 Organization</span></span>](https://go.microsoft.com/fwlink/?LinkID=100485)
    
  - [<span data-ttu-id="c6657-261">Удаление сервера Exchange Server 2003</span><span class="sxs-lookup"><span data-stu-id="c6657-261">How to Uninstall Exchange Server 2003</span></span>](https://go.microsoft.com/fwlink/?LinkID=56561)
    

