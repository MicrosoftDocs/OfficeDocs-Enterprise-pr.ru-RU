---
title: Прямая миграция в Office 365 с помощью PowerShell
ms.author: sirkkuw
author: sirkkuw
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: b468cb4b-a35c-43d3-85bf-65446998af40
description: Сводка. Узнайте, как использовать Windows PowerShell для прямой миграции в Office 365.
ms.openlocfilehash: 669aa3dc728b41bdc2ba8cc467943db5eb2005d9
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "34071205"
---
# <a name="use-powershell-to-perform-a-cutover-migration-to-office-365"></a><span data-ttu-id="0edc2-103">Прямая миграция в Office 365 с помощью PowerShell</span><span class="sxs-lookup"><span data-stu-id="0edc2-103">Use PowerShell to perform a cutover migration to Office 365</span></span>

 <span data-ttu-id="0edc2-104">**Сводка.** Узнайте, как выполнить прямую миграцию в Office 365, используя Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0edc2-104">**Summary:** Learn how to use Windows PowerShell to perform a cutover migration to Office 365.</span></span>
  
<span data-ttu-id="0edc2-p101">Вы можете одновременно перенести содержимое почтовых ящиков пользователей из исходной системы электронной почты в Office 365:, используя прямую миграцию. В этой статье описаны задачи, которые выполняются при прямой миграции электронной почты с помощью Exchange Online PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0edc2-p101">You can migrate the contents of user mailboxes from a source email system to Office 365 all at once by using a cutover migration. This article walks you through the tasks for an email cutover migration by using Exchange Online PowerShell.</span></span> 
  
<span data-ttu-id="0edc2-p102">Процесс миграции в общих чертах рассматривается в статье [Что необходимо знать о прямой миграции электронной почты в Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536688). Ознакомившись с содержимым этой статьи, начните переносить почтовые ящики из одной почтовой системы в другую, руководствуясь приведенными в этой статье сведениями.</span><span class="sxs-lookup"><span data-stu-id="0edc2-p102">By reviewing the topic, [What you need to know about a cutover email migration to Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536688), you can get an overview of the migration process. When you're comfortable with the contents of that article, use this one to begin migrating mailboxes from one email system to another.</span></span>
  
> [!NOTE]
> <span data-ttu-id="0edc2-p103">Для прямой миграции можно также использовать Центр администрирования Exchange. См. статью [Прямая миграция электронной почты в Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536689).</span><span class="sxs-lookup"><span data-stu-id="0edc2-p103">You can also use the Exchange admin center to perform a cutover migration. See [Perform a cutover migration of email to Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536689).</span></span> 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="0edc2-111">Что нужно знать перед началом работы?</span><span class="sxs-lookup"><span data-stu-id="0edc2-111">What do you need to know before you begin?</span></span>

<span data-ttu-id="0edc2-p104">Предполагаемое время выполнения задачи: от 2 до 5 минут для создания пакета миграции. После запуска пакета миграции продолжительность миграции будет зависеть от количества почтовых ящиков в пакете, размера каждого почтового ящика и доступной пропускной способности сети. Подробнее о других факторах, влияющих на продолжительность миграции почтовых ящиков в Office 365:, см. в статье [Производительность миграции](https://go.microsoft.com/fwlink/p/?LinkId=275079)</span><span class="sxs-lookup"><span data-stu-id="0edc2-p104">Estimated time to complete this task: 2-5 minutes to create a migration batch. After the migration batch is started, the duration of the migration will vary based on the number of mailboxes in the batch, the size of each mailbox, and your available network capacity. For information about other factors that affect how long it takes to migrate mailboxes to Office 365, see [Migration Performance](https://go.microsoft.com/fwlink/p/?LinkId=275079).</span></span>
  
<span data-ttu-id="0edc2-p105">Для выполнения этой процедуры (процедур) необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в пункте "Миграция" статьи [Разрешения получателей](https://go.microsoft.com/fwlink/p/?LinkId=534105) в соответствующей таблице.</span><span class="sxs-lookup"><span data-stu-id="0edc2-p105">You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Migration" entry in a table in the [Recipients Permissions](https://go.microsoft.com/fwlink/p/?LinkId=534105) topic.</span></span>
  
<span data-ttu-id="0edc2-p106">Чтобы использовать командлеты Exchange Online PowerShell, вам необходимо войти в систему и импортировать командлеты в локальный сеанс Windows PowerShell. Инструкции см в статье [Подключение к Exchange Online с помощью удаленной оболочки PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534121).</span><span class="sxs-lookup"><span data-stu-id="0edc2-p106">To use the Exchange Online PowerShell cmdlets, you need to sign in and import the cmdlets into your local Windows PowerShell session. See [Connect to Exchange Online using remote PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534121) for instructions.</span></span>
  
<span data-ttu-id="0edc2-119">Полный список команд миграции см. в статье [Командлеты перемещения и миграции](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span><span class="sxs-lookup"><span data-stu-id="0edc2-119">For a full list of migration commands, see [Move and migration cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span></span>
  
## <a name="migration-steps"></a><span data-ttu-id="0edc2-120">Шаги миграции</span><span class="sxs-lookup"><span data-stu-id="0edc2-120">Migration steps</span></span>

### <a name="step-1-prepare-for-a-cutover-migration"></a><span data-ttu-id="0edc2-121">Шаг 1. Подготовка к прямой миграции</span><span class="sxs-lookup"><span data-stu-id="0edc2-121">Step 1: Prepare for a cutover migration</span></span>
<span data-ttu-id="0edc2-122"><a name="BK_Step1"> </a></span><span class="sxs-lookup"><span data-stu-id="0edc2-122"></span></span>

- <span data-ttu-id="0edc2-p107">**Добавьте локальную организацию Exchange в качестве обслуживаемого домена организации Office 365.** Служба миграции использует SMTP-адрес локальных почтовых ящиков для создания идентификатора пользователя Microsoft Online Services и адреса электронной почты для новых почтовых ящиков Office 365:. Выполнить миграцию не удастся, если домен Exchange не является обслуживаемым или основным доменом организации Office 365:. Дополнительные сведения см. в статье[Проверка домена в Office 365](https://go.microsoft.com/fwlink/p/?LinkId=534110).</span><span class="sxs-lookup"><span data-stu-id="0edc2-p107">**Add your on-premises Exchange organization as an accepted domain of your Office 365 organization.** The migration service uses the SMTP address of your on-premises mailboxes to create the Microsoft Online Services user ID and email address for the new Office 365 mailboxes. Migration will fail if your Exchange domain isn't an accepted domain or the primary domain of your Office 365 organization. For more information, see[Verify your domain in Office 365](https://go.microsoft.com/fwlink/p/?LinkId=534110).</span></span>
    
- <span data-ttu-id="0edc2-p108">**Настройте мобильный Outlook на локальном сервере Exchange.** Служба миграции электронной почты использует протокол RPC через HTTP, также называемый мобильный Outlook, для подключения к локальному серверу Exchange Server. Дополнительные сведения о настройке службы мобильный Outlook для Exchange 2010, Exchange 2007 и Exchange 2003 см. в следующих статьях.</span><span class="sxs-lookup"><span data-stu-id="0edc2-p108">**Configure Outlook Anywhere on your on-premises Exchange server.** The email migration service uses RPC over HTTP, or Outlook Anywhere, to connect to your on-premises Exchange server. For information about how to set up Outlook Anywhere for Exchange 2010, Exchange 2007, and Exchange 2003, see the following:</span></span>
    
  - [<span data-ttu-id="0edc2-130">Exchange 2010. Включение мобильного Outlook</span><span class="sxs-lookup"><span data-stu-id="0edc2-130">Exchange 2010: Enable Outlook Anywhere</span></span>](https://go.microsoft.com/fwlink/?LinkID=187249)
    
  - [<span data-ttu-id="0edc2-131">Exchange 2007. Инструкции по включению мобильного Outlook</span><span class="sxs-lookup"><span data-stu-id="0edc2-131">Exchange 2007: How to Enable Outlook Anywhere</span></span>](https://go.microsoft.com/fwlink/?LinkID=167210)
    
  - [<span data-ttu-id="0edc2-132">Exchange 2003. Сценарии развертывания для RPC через HTTP</span><span class="sxs-lookup"><span data-stu-id="0edc2-132">Exchange 2003: Deployment Scenarios for RPC over HTTP</span></span>](https://go.microsoft.com/fwlink/?LinkID=73657)
    
  - [<span data-ttu-id="0edc2-133">Настройка мобильного Outlook в Exchange 2003</span><span class="sxs-lookup"><span data-stu-id="0edc2-133">How to Configure Outlook Anywhere with Exchange 2003</span></span>](https://go.microsoft.com/fwlink/?LinkID=167209)
    
    > [!IMPORTANT]
    > <span data-ttu-id="0edc2-p109">Конфигурацию мобильного Outlook необходимо настроить с использованием сертификата, выпущенного доверенным центром сертификации (ЦС). Настройка с использованием самозаверяющего сертификата невозможна. Дополнительные сведения см. в статье [Инструкции по настройке протокола SSL для мобильного Outlook](https://go.microsoft.com/fwlink/?LinkID=80875).</span><span class="sxs-lookup"><span data-stu-id="0edc2-p109">Your Outlook Anywhere configuration must be configured with a certificate issued by a trusted certification authority (CA). It can't be configured with a self-signed certificate. For more information, see [How to Configure SSL for Outlook Anywhere](https://go.microsoft.com/fwlink/?LinkID=80875).</span></span> 
  
- <span data-ttu-id="0edc2-p110">**Проверьте возможность подключения к организации Exchange с помощью мобильного Outlook.** Проверьте настройки подключения с использованием следующих способов.</span><span class="sxs-lookup"><span data-stu-id="0edc2-p110">**Verify that you can connect to your Exchange organization using Outlook Anywhere.** Try one of these methods to test your connection settings:</span></span>
    
  - <span data-ttu-id="0edc2-139">Подключитесь к локальному почтовому ящику Exchange с помощью Microsoft Outlook из-за пределов корпоративной сети.</span><span class="sxs-lookup"><span data-stu-id="0edc2-139">Use Microsoft Outlook from outside your corporate network to connect to your on-premises Exchange mailbox.</span></span>
    
  - <span data-ttu-id="0edc2-p111">Проверьте настройки подключения с помощью [анализатора удаленного подключения Exchange](https://www.testexchangeconnectivity.com/) корпорации Майкрософт. Используйте средства мобильного Outlook (RPC через HTTP) или проверки автообнаружения Outlook.</span><span class="sxs-lookup"><span data-stu-id="0edc2-p111">Use the Microsoft [Exchange Remote Connectivity Analyzer](https://www.testexchangeconnectivity.com/) to test your connection settings. Use the Outlook Anywhere (RPC over HTTP) or Outlook Autodiscover tests.</span></span>
    
  - <span data-ttu-id="0edc2-142">В Exchange Online PowerShell выполните следующие команды.</span><span class="sxs-lookup"><span data-stu-id="0edc2-142">Run the following commands in Exchange Online PowerShell.</span></span>
    
  ```
  $Credentials = Get-Credential
  ```

  ```
  Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress <email address for on-premises administrator> -Credentials $credentials
  ```

- <span data-ttu-id="0edc2-143">**Назначьте для локальной учетной записи необходимые разрешения на доступ к почтовым ящикам в организации Exchange.**</span><span class="sxs-lookup"><span data-stu-id="0edc2-143">**Assign an on-premises user account the necessary permissions to access mailboxes in your Exchange organization.**</span></span> <span data-ttu-id="0edc2-144">Локальная учетная запись пользователя, которая используется для подключения к локальной организации Exchange (также называемую администратором миграции), должна иметь необходимые разрешения для доступа к локальным почтовым ящикам, которые необходимо перенести в Office 365.</span><span class="sxs-lookup"><span data-stu-id="0edc2-144">The on-premises user account that you use to connect to your on-premises Exchange organization (also called the migration administrator) must have the necessary permissions to access the on-premises mailboxes that you want to migrate to Office 365.</span></span> <span data-ttu-id="0edc2-145">Эта учетная запись пользователя необходима для создания конечной точки миграции в вашей локальной организации.</span><span class="sxs-lookup"><span data-stu-id="0edc2-145">This user account is used to create a migration endpoint to your on-premises organization.</span></span>
    
    <span data-ttu-id="0edc2-p113">В следующем списке перечислены права администратора, необходимые для переноса почтовых ящиков с помощью прямой миграции. У вас есть три варианта.</span><span class="sxs-lookup"><span data-stu-id="0edc2-p113">The following list shows the administrative privileges required to migrate mailboxes using a cutover migration. There are three possible options.</span></span>
    
  - <span data-ttu-id="0edc2-148">Администратор миграции должен быть членом группы **Администраторы домена** в службе каталогов Active Directory локальной организации.</span><span class="sxs-lookup"><span data-stu-id="0edc2-148">The migration administrator must be a member of the **Domain Admins** group in Active Directory in the on-premises organization.</span></span>
    
    <span data-ttu-id="0edc2-149">или</span><span class="sxs-lookup"><span data-stu-id="0edc2-149">Or</span></span>
    
  - <span data-ttu-id="0edc2-150">Администратор миграции должен иметь разрешение **FullAccess** для всех локальных почтовых ящиков.</span><span class="sxs-lookup"><span data-stu-id="0edc2-150">The migration administrator must be assigned the **FullAccess** permission for each on-premises mailbox.</span></span>
    
    <span data-ttu-id="0edc2-151">Или</span><span class="sxs-lookup"><span data-stu-id="0edc2-151">Or</span></span>
    
  - <span data-ttu-id="0edc2-152">Администратор миграции должен иметь разрешение **Получить как** в локальной базе данных, где хранятся почтовые ящики пользователей.</span><span class="sxs-lookup"><span data-stu-id="0edc2-152">The migration administrator must be assigned the **Receive As** permission on the on-premises mailbox database that stores the user mailboxes.</span></span>
    
- <span data-ttu-id="0edc2-p114">**Отключите единую систему обмена сообщениями.** Если для локальных почтовых ящиков включена поддержка единой системы обмена сообщениями, ее необходимо отключить, прежде чем переносить почтовые ящики. После завершения миграции поддержку единой системы обмена сообщениями для этих ящиков можно снова включить.</span><span class="sxs-lookup"><span data-stu-id="0edc2-p114">**Disable Unified Messaging.** If the on-premises mailboxes you're migrating are enabled for Unified Messaging (UM), you have to disable UM on the mailboxes before you migrate them. You can then enable UM on the mailboxes after the migration is complete.</span></span>
    
- <span data-ttu-id="0edc2-p115">**Группы безопасности и делегаты.** Служба миграции электронной почты не может определить, являются ли локальные группы Active Directory группами безопасности, поэтому эта служба не может подготовить к работе перенесенные группы в качестве групп безопасности в Office 365. Если вы хотите иметь группы безопасности в клиенте Office 365, сначала необходимо подготовить к работе пустую группу безопасности, поддерживающую почту, в клиенте Office 365 перед запуском прямой миграции. Кроме того, этот метод миграции обеспечивает перемещение только почтовых ящиков, почтовых пользователей, почтовых контактов и групп, поддерживающих почту. Если любой другой объект Active Directory, например пользователь, не перенесенный в Office 365:, назначается в качестве руководителя или делегата для переносимого объекта, перед миграцией их необходимо удалить из объекта.</span><span class="sxs-lookup"><span data-stu-id="0edc2-p115">**Security Groups and Delegates** The email migration service cannot detect whether on-premises Active Directory groups are security groups or not, so it cannot provision any migrated groups as security groups in Office 365. If you want to have security groups in your Office 365 tenant, you must first provision an empty mail-enabled security group in your Office 365 tenant before starting the cutover migration. Additionally, this migration method only moves mailboxes, mail users, mail contacts, and mail-enabled groups. If any other Active Directory object, such as user that is not migrated to Office 365, is assigned as a manager or delegate to an object being migrated, they must be removed from the object before you migrate.</span></span>
    
### <a name="step-2-create-a-migration-endpoint"></a><span data-ttu-id="0edc2-160">Шаг 2. Создание конечной точки миграции</span><span class="sxs-lookup"><span data-stu-id="0edc2-160">Step 2: Create a migration endpoint</span></span>
<span data-ttu-id="0edc2-161"><a name="BK_Step2"> </a></span><span class="sxs-lookup"><span data-stu-id="0edc2-161"></span></span>

<span data-ttu-id="0edc2-p116">Для успешного переноса электронной почты решение Office 365: должно обмениваться данными с исходной системой электронной почты. Для этого Office 365 использует конечную точку миграции. Чтобы создать конечную точку миграции мобильного Outlook для прямой миграции, сначала [подключитесь к Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121).</span><span class="sxs-lookup"><span data-stu-id="0edc2-p116">To migrate email successfully, Office 365 needs to connect and communicate with the source email system. To do this, Office 365 uses a migration endpoint. To create an Outlook Anywhere migration endpoint for cutover migration, first [connect to Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121).</span></span> 
  
<span data-ttu-id="0edc2-165">Полный список команд миграции см. в статье [Командлеты перемещения и миграции](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span><span class="sxs-lookup"><span data-stu-id="0edc2-165">For a full list of migration commands, see [Move and migration cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span></span>
  
<span data-ttu-id="0edc2-166">В Exchange Online PowerShell выполните следующие команды.</span><span class="sxs-lookup"><span data-stu-id="0edc2-166">Run the following commands in Exchange Online PowerShell:</span></span>
  
```
$Credentials = Get-Credential
```

<span data-ttu-id="0edc2-167">В примере используется командлет [Test-MigrationServerAvailability](https://go.microsoft.com/fwlink/p/?LinkId=534752), который получает и проверяет параметры подключения к локальному серверу Exchange, а затем использует эти параметры для создания конечной точки миграции CutoverEndpoint.</span><span class="sxs-lookup"><span data-stu-id="0edc2-167">The example uses the [Test-MigrationServerAvailability](https://go.microsoft.com/fwlink/p/?LinkId=534752) cmdlet to obtain and test the connection settings to the on-premises Exchange server, and then uses those connection settings to create the migration endpoint called "CutoverEndpoint".</span></span>
  
```
$TSMA = Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress administrator@contoso.com -Credentials $credentials
```

```
New-MigrationEndpoint -ExchangeOutlookAnywhere -Name CutoverEndpoint -ConnectionSettings $TSMA.ConnectionSettings
```

> [!NOTE]
> <span data-ttu-id="0edc2-p117">С помощью командлета **New-MigrationEndpoint** и параметра **-TargetDatabase** можно указать базу данных, которая будет использоваться службой. В противном случае база данных назначается случайным образом на сайте Службы федерации Active Directory (AD FS) 2.0, на котором расположен почтовый ящик управления.</span><span class="sxs-lookup"><span data-stu-id="0edc2-p117">The **New-MigrationEndpoint** cmdlet can be used to specify a database for the service to use by using the **-TargetDatabase** option. Otherwise a database is randomly assigned from the Active Directory Federation Services (AD FS) 2.0 site where the management mailbox is located.</span></span>
  
#### <a name="verify-it-worked"></a><span data-ttu-id="0edc2-170">Проверка работы</span><span class="sxs-lookup"><span data-stu-id="0edc2-170">Verify it worked</span></span>

<span data-ttu-id="0edc2-171">В Exchange Online PowerShell выполните следующую команду, чтобы отобразить сведения о конечной точке миграции CutoverEndpoint.</span><span class="sxs-lookup"><span data-stu-id="0edc2-171">In Exchange Online PowerShell, run the following command to display information about the "CutoverEndpoint" migration endpoint:</span></span>
  
```
Get-MigrationEndpoint CutoverEndpoint | Format-List EndpointType,ExchangeServer,UseAutoDiscover,Max*

```

### <a name="step-3-create-the-cutover-migration-batch"></a><span data-ttu-id="0edc2-172">Шаг 3. Создание пакета прямой миграции</span><span class="sxs-lookup"><span data-stu-id="0edc2-172">Step 3: Create the cutover migration batch</span></span>
<span data-ttu-id="0edc2-173"><a name="BK_Step3"> </a></span><span class="sxs-lookup"><span data-stu-id="0edc2-173"></span></span>

<span data-ttu-id="0edc2-p118">Чтобы создать пакет для прямой миграции, выполните командлет **New-MigrationBatch** в Exchange Online PowerShell. Можно создать пакет миграции и запустить его обработку автоматически, включив параметр _AutoStart_. Кроме того, вы можете создать пакет миграции, а затем вручную запустить его с помощью командлета **Start-MigrationBatch**. В этом примере создается пакет миграции CutoverBatch и используется конечная точка миграции, созданная на предыдущем шаге.</span><span class="sxs-lookup"><span data-stu-id="0edc2-p118">You can use the **New-MigrationBatch** cmdlet in Exchange Online PowerShell to create a migration batch for a cutover migration. You can create a migration batch and start it automatically by including the _AutoStart_ parameter. Alternatively, you can create the migration batch and then manually start it afterwards by using the **Start-MigrationBatch** cmdlet. This example creates a migration batch called "CutoverBatch" and uses the migration endpoint that was created in the previous step.</span></span>
  
```
New-MigrationBatch -Name CutoverBatch -SourceEndpoint CutoverEndpoint -AutoStart
```

<span data-ttu-id="0edc2-p119">В этом примере также создается пакет миграции CutoverBatch и используется конечная точка миграции, созданная на предыдущем шаге. Так как параметр  _AutoStart_ не включен, пакет миграции необходимо запустить вручную на панели мониторинга миграции или с помощью командлета **Start-MigrationBatch**. Как было сказано выше, в одно и то же время может существовать только один пакет прямой миграции.</span><span class="sxs-lookup"><span data-stu-id="0edc2-p119">This example also creates a migration batch called "CutoverBatch" and uses the migration endpoint that was created in the previous step. Because the  _AutoStart_ parameter isn't included, the migration batch has to be manually started on the migration dashboard or by using **Start-MigrationBatch** cmdlet. As previously stated, only one cutover migration batch can exist at a time.</span></span>
  
```
New-MigrationBatch -Name CutoverBatch -SourceEndpoint CutoverEndpoint
```

#### <a name="verify-it-worked"></a><span data-ttu-id="0edc2-181">Проверка работы</span><span class="sxs-lookup"><span data-stu-id="0edc2-181">Verify it worked</span></span>

<span data-ttu-id="0edc2-182">Чтобы убедиться, что вы успешно создали пакет прямой миграции, выполните следующую команду в Exchange Online PowerShell для отображения сведений о новом пакете миграции.</span><span class="sxs-lookup"><span data-stu-id="0edc2-182">To verify that you've successfully created a migration batch for a cutover migration, run the following command in Exchange Online PowerShell to display information about the new migration batch:</span></span>
  
```
Get-MigrationBatch | Format-List
```

### <a name="step-4-start-the-cutover-migration-batch"></a><span data-ttu-id="0edc2-183">Шаг 4. Запуск пакета прямой миграции</span><span class="sxs-lookup"><span data-stu-id="0edc2-183">Step 4: Start the cutover migration batch</span></span>
<span data-ttu-id="0edc2-184"><a name="BK_Step4"> </a></span><span class="sxs-lookup"><span data-stu-id="0edc2-184"></span></span>

<span data-ttu-id="0edc2-p120">Чтобы запустить пакет миграции в Exchange Online PowerShell, выполните следующую команду. Будет создан пакет миграции CutoverBatch.</span><span class="sxs-lookup"><span data-stu-id="0edc2-p120">To start the migration batch in Exchange Online PowerShell, run the following command. This will create a migration batch called "CutoverBatch".</span></span>
  
```
Start-MigrationBatch -Identity CutoverBatch
```

#### <a name="verify-it-worked"></a><span data-ttu-id="0edc2-187">Проверка работы</span><span class="sxs-lookup"><span data-stu-id="0edc2-187">Verify it worked</span></span>

<span data-ttu-id="0edc2-p121">Если пакет миграции успешно запущен, состояние пакета на панели мониторинга миграции изменится на "Синхронизация". Чтобы убедиться, вы успешно запустили пакет миграции с помощью Exchange Online PowerShell, выполните следующую команду.</span><span class="sxs-lookup"><span data-stu-id="0edc2-p121">If a migration batch is successfully started, its status on the migration dashboard is specified as Syncing. To verify that you've successfully started a migration batch using Exchange Online PowerShell, run the following command:</span></span>
  
```
Get-MigrationBatch -Identity CutoverBatch |  Format-List Status
```

### <a name="step-5-route-your-email-to-office-365"></a><span data-ttu-id="0edc2-190">Шаг 5. Маршрутизация электронной почты в Office 365</span><span class="sxs-lookup"><span data-stu-id="0edc2-190">Step 5: Route your email to Office 365</span></span>
<span data-ttu-id="0edc2-191"><a name="BK_Step5"> </a></span><span class="sxs-lookup"><span data-stu-id="0edc2-191"></span></span>

<span data-ttu-id="0edc2-p122">Чтобы выяснить, куда доставлять сообщения электронной почты, системы электронной почты используют DNS-запись, которая называется записью MX. В процессе миграции электронной почты запись MX указывала на вашу исходную систему электронной почты. Теперь, когда перенос электронной почты в Office 365: завершен, запись MX должна указывать на Office 365:. Это обеспечит доставку электронной почты в ваши почтовые ящики Office 365:. Перемещая запись MX, вы также сможете отключить старую систему электронной почты, когда будете готовы сделать это.</span><span class="sxs-lookup"><span data-stu-id="0edc2-p122">Email systems use a DNS record called an MX record to figure out where to deliver emails. During the email migration process, your MX record was pointing to your source email system. Now that the email migration to Office 365 is complete, it's time to point your MX record at Office 365. This helps make sure that email is delivered to your Office 365 mailboxes. By moving the MX record, you can also you turn off your old email system when you're ready.</span></span> 
  
<span data-ttu-id="0edc2-p123">Многим поставщикам DNS следует придерживаться инструкций по [изменению записи MX](https://go.microsoft.com/fwlink/p/?LinkId=279163). Если ваш поставщик DNS не включен в этот список, или если вы хотите получить представление об общих указаниях, см. [статью с общими инструкции в отношении записи MX](https://go.microsoft.com/fwlink/?LinkId=397449).</span><span class="sxs-lookup"><span data-stu-id="0edc2-p123">For many DNS providers, there are specific instructions to [change your MX record](https://go.microsoft.com/fwlink/p/?LinkId=279163). If your DNS provider isn't included, or if you want to get a sense of the general directions, [general MX record instructions ](https://go.microsoft.com/fwlink/?LinkId=397449) are provided as well.</span></span>
  
<span data-ttu-id="0edc2-p124">Системам электронной почты клиентов и партнеров может потребоваться до 72 часов, чтобы распознать измененную запись MX. Подождите по крайней мере 72 часа, прежде чем перейти к следующей задаче: [Шаг 6. Удаление пакета прямой миграции](use-powershell-to-perform-a-cutover-migration-to-office-365.md#Bk_step6).</span><span class="sxs-lookup"><span data-stu-id="0edc2-p124">It can take up to 72 hours for the email systems of your customers and partners to recognize the changed MX record. Wait at least 72 hours before you proceed to the next task: [Step 6: Delete the cutover migration batch](use-powershell-to-perform-a-cutover-migration-to-office-365.md#Bk_step6).</span></span> 
  
### <a name="step-6-delete-the-cutover-migration-batch"></a><span data-ttu-id="0edc2-201">Шаг 6. Удаление пакета прямой миграции</span><span class="sxs-lookup"><span data-stu-id="0edc2-201">Step 6: Delete the cutover migration batch</span></span>
<span data-ttu-id="0edc2-202"><a name="Bk_step6"> </a></span><span class="sxs-lookup"><span data-stu-id="0edc2-202"></span></span>

<span data-ttu-id="0edc2-p125">После того как вы измените запись MX и убедитесь, что вся электронная почта направляется в почтовые ящики Office 365:, уведомите пользователей о том, что их сообщения доставляются в Office 365. Затем можно удалить пакет прямой миграции. Убедитесь в следующем, прежде чем удалить пакет миграции.</span><span class="sxs-lookup"><span data-stu-id="0edc2-p125">After you change the MX record and verify that all email is being routed to Office 365 mailboxes, notify the users that their mail is going to Office 365. After this, you can delete the cutover migration batch. Verify the following before you delete the migration batch.</span></span>
  
- <span data-ttu-id="0edc2-p126">Все пользователи используют почтовые ящики Office 365:. После удаления пакета почта, отправляемая в почтовые ящики на локальном сервере Exchange Server, не копируется в соответствующие почтовые ящики Office 365:.</span><span class="sxs-lookup"><span data-stu-id="0edc2-p126">All users are using Office 365 mailboxes. After the batch is deleted, mail sent to mailboxes on the on-premises Exchange Server isn't copied to the corresponding Office 365 mailboxes.</span></span>
    
- <span data-ttu-id="0edc2-p127">Почтовые ящики Office 365: синхронизированы по крайней мере один раз после того, как почта стала доставляться непосредственно в них. Для этого убедитесь, что значение в поле "Время последней синхронизации" для пакета миграции позже даты и времени, когда почта стала направляться непосредственно в почтовые ящики Office 365:.</span><span class="sxs-lookup"><span data-stu-id="0edc2-p127">Office 365 mailboxes were synchronized at least once after mail began being sent directly to them. To do this, make sure that the value in the Last Synced Time box for the migration batch is more recent than when mail started being routed directly to Office 365 mailboxes.</span></span>
    
<span data-ttu-id="0edc2-210">Чтобы удалить пакет миграции CutoverBatch в Exchange Online PowerShell, выполните следующую команду.</span><span class="sxs-lookup"><span data-stu-id="0edc2-210">To delete the "CutoverBatch" migration batch in Exchange Online PowerShell, run the following command:</span></span>
  
```
Remove-MigrationBatch -Identity CutoverBatch
```

### <a name="section-7-assign-user-licenses"></a><span data-ttu-id="0edc2-211">Шаг 7. Назначение пользователям лицензий</span><span class="sxs-lookup"><span data-stu-id="0edc2-211">Section 7: Assign user licenses</span></span>
<span data-ttu-id="0edc2-212"><a name="BK_Step7"> </a></span><span class="sxs-lookup"><span data-stu-id="0edc2-212"></span></span>

 <span data-ttu-id="0edc2-213">**Активируйте учетные записи пользователей Office 365 для перенесенных учетных записей, назначив им лицензии.**</span><span class="sxs-lookup"><span data-stu-id="0edc2-213">**Activate Office 365 user accounts for the migrated accounts by assigning licenses.**</span></span> <span data-ttu-id="0edc2-214">Если вы не назначите лицензию, почтовый ящик отключается по окончании льготного периода (30 дней).</span><span class="sxs-lookup"><span data-stu-id="0edc2-214">If you don't assign a license, the mailbox is disabled when the grace period ends (30 days).</span></span> <span data-ttu-id="0edc2-215">Чтобы назначить лицензию в центре администрирования Microsoft 365, ознакомьтесь с разназначением[лицензий на Office 365 для бизнеса](https://go.microsoft.com/fwlink/?LinkId=536681).</span><span class="sxs-lookup"><span data-stu-id="0edc2-215">To assign a license in the Microsoft 365 admin center, see[Assign or unassign licenses for Office 365 for business](https://go.microsoft.com/fwlink/?LinkId=536681).</span></span>
  
### <a name="step-8-complete-post-migration-tasks"></a><span data-ttu-id="0edc2-216">Шаг 8. Необходимые действия после миграции</span><span class="sxs-lookup"><span data-stu-id="0edc2-216">Step 8: Complete post-migration tasks</span></span>
<span data-ttu-id="0edc2-217"><a name="BK_Step8"> </a></span><span class="sxs-lookup"><span data-stu-id="0edc2-217"></span></span>

- <span data-ttu-id="0edc2-p129">**Создайте DNS-запись автообнаружения, чтобы пользователи смогли с легкостью получить доступ к своим почтовым ящикам.** После переноса всех локальных почтовых ящиков в Office 365: вы можете настроить DNS-запись автообнаружения для своей организации Office 365:, чтобы пользователи могли с легкостью подключаться к своим новым почтовым ящикам Office 365: с помощью Outlook и мобильных клиентов. В этой новой DNS-записи автообнаружения необходимо использовать то же пространство имен, которое используется для организации Office 365:. Например, если облачное пространство имен  cloud.contoso.com, необходимо создать DNS-запись автообнаружения autodiscover.cloud.contoso.com.</span><span class="sxs-lookup"><span data-stu-id="0edc2-p129">**Create an Autodiscover DNS record so users can easily get to their mailboxes.** After all on-premises mailboxes are migrated to Office 365, you can configure an Autodiscover DNS record for your Office 365 organization to enable users to easily connect to their new Office 365 mailboxes with Outlook and mobile clients. This new Autodiscover DNS record has to use the same namespace that you're using for your Office 365 organization. For example, if your cloud-based namespace is cloud.contoso.com, the Autodiscover DNS record you need to create is autodiscover.cloud.contoso.com.</span></span>
    
    <span data-ttu-id="0edc2-222">Если Exchange Server останется, убедитесь, что после миграции запись CNAME службы доменных имен (DNS) для автообнаружения указывает на Office 365 на внутренних и внешних DNS-серверах, чтобы клиент Outlook мог подключиться к правильному почтовому ящику.</span><span class="sxs-lookup"><span data-stu-id="0edc2-222">If you keep your Exchange Server, you should also make sure that Autodiscover DNS CNAME record has to point to Office 365 in both internal and external DNS after the migration so that the Outlook client will to connect to the correct mailbox.</span></span>
    
    > [!NOTE]
    >  <span data-ttu-id="0edc2-223">В Exchange 2007, Exchange 2010 и Exchange 2013 для параметра  `Set-ClientAccessServer AutodiscoverInternalConnectionURI` необходимо задать значение `Null`.</span><span class="sxs-lookup"><span data-stu-id="0edc2-223">In Exchange 2007, Exchange 2010, and Exchange 2013 you should also set `Set-ClientAccessServer AutodiscoverInternalConnectionURI` to `Null`.</span></span> 
  
    <span data-ttu-id="0edc2-p130">В Office 365: запись CNAME служит для реализации службы автообнаружения для клиентов Outlook и мобильных клиентов. Необходимо, чтобы запись CNAME для автообнаружения содержала следующие сведения.</span><span class="sxs-lookup"><span data-stu-id="0edc2-p130">Office 365 uses a CNAME record to implement the Autodiscover service for Outlook and mobile clients. The Autodiscover CNAME record must contain the following information:</span></span>
    
  - <span data-ttu-id="0edc2-226">**Псевдоним:** autodiscover</span><span class="sxs-lookup"><span data-stu-id="0edc2-226">**Alias:** autodiscover</span></span>
    
  - <span data-ttu-id="0edc2-227">**Целевой объект:** autodiscover.outlook.com</span><span class="sxs-lookup"><span data-stu-id="0edc2-227">**Target:** autodiscover.outlook.com</span></span>
    
    <span data-ttu-id="0edc2-228">Дополнительные сведения см. в статье [Создание DNS-записей для Office 365 при управлении DNS-записями](https://go.microsoft.com/fwlink/p/?LinkId=535028).</span><span class="sxs-lookup"><span data-stu-id="0edc2-228">For more information, see [Create DNS records for Office 365 when you manage your DNS records](https://go.microsoft.com/fwlink/p/?LinkId=535028).</span></span>
    
- <span data-ttu-id="0edc2-p131">**Выполните списание локальных серверов Exchange.** Как только вы убедитесь, что вся электронная почта направляется непосредственно в почтовые ящики Office 365:, поэтому вам больше не нужно поддерживать свою локальную организацию электронной почты, либо если вы не планируете внедрять решение единого входа, вы можете удалить Exchange с серверов, а также удалить свою локальную организацию Exchange.</span><span class="sxs-lookup"><span data-stu-id="0edc2-p131">**Decommission on-premises Exchange servers.** After you've verified that all email is being routed directly to the Office 365 mailboxes, and you no longer need to maintain your on-premises email organization or don't plan on implementing a single sign-on (SSO) solution, you can uninstall Exchange from your servers and remove your on-premises Exchange organization.</span></span>
    
    <span data-ttu-id="0edc2-231">Дополнительные сведения см. в следующих статьях:</span><span class="sxs-lookup"><span data-stu-id="0edc2-231">For more information, see the following:</span></span>
    
  - [<span data-ttu-id="0edc2-232">Изменение или удаление Exchange 2010</span><span class="sxs-lookup"><span data-stu-id="0edc2-232">Modify or Remove Exchange 2010</span></span>](https://go.microsoft.com/fwlink/?LinkId=217936)
    
  - [<span data-ttu-id="0edc2-233">Удаление организации Exchange 2007</span><span class="sxs-lookup"><span data-stu-id="0edc2-233">How to Remove an Exchange 2007 Organization</span></span>](https://go.microsoft.com/fwlink/?LinkID=100485)
    
  - [<span data-ttu-id="0edc2-234">Удаление сервера Exchange Server 2003</span><span class="sxs-lookup"><span data-stu-id="0edc2-234">How to Uninstall Exchange Server 2003</span></span>](https://go.microsoft.com/fwlink/?LinkID=56561)
    

