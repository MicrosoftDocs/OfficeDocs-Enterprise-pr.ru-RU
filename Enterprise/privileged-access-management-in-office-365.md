---
title: Правами доступа к управления в Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 7/13/2018
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Strat_O365_IP
ms.custom: Ent_Solutions
ms.assetid: ''
description: Используйте этот раздел для получения дополнительных сведений о функции управления правами доступа в Office 365
ms.openlocfilehash: b2db3e16e53cca7deb2bf8fbff61b5b981f42fa6
ms.sourcegitcommit: b39b8ae3b4268d6475b54e2fdb62982b2c7d9943
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/12/2018
ms.locfileid: "20319210"
---
# <a name="privileged-access-management-in-office-365"></a><span data-ttu-id="29468-103">Правами доступа к управления в Office 365</span><span class="sxs-lookup"><span data-stu-id="29468-103">Privileged access management in Office 365</span></span>

> [!IMPORTANT]
> <span data-ttu-id="29468-104">В этом разделе описывается развертывание и конфигурация руководство для бета-версия функции в настоящее время доступны только в Office 365 E5 и дополнительные номера SKU соответствия требованиям.</span><span class="sxs-lookup"><span data-stu-id="29468-104">This topic covers deployment and configuration guidance for public beta features only currently available in Office 365 E5 and Advanced Compliance SKUs.</span></span>

<span data-ttu-id="29468-p101">Привилегированный доступ управления позволяет управлять детального доступа задачи правами администратора в Office 365.  Он может помочь защитить организацию от нарушения безопасности, которые могут использовать существующие учетные записи с правами администратора с положение доступа к конфиденциальным данным или доступ к параметрам конфигурации важных. После включения управление правами доступа, пользователям потребуется запросить необходимые права доступа в время для выполнения задач с повышенными полномочиями и привилегированных через рабочего процесса утверждения, который является очень областью действия и временные рамки. Это дает пользователям только что enough права на выполнение с ними без риска доступом важных настройках и конфиденциальных данных. Включение управления правами доступа в Office 365 позволит вашей организации, для работы с нуля привилегиями положение и обеспечивают уровень защиты от уязвимостей, поступающие из-за такой положение административного доступа.</span><span class="sxs-lookup"><span data-stu-id="29468-p101">Privileged access management allows granular access control over privileged admin tasks in Office 365.  It can help protect your organization from breaches that may use existing privileged admin accounts with standing access to sensitive data or access to critical configuration settings. After enabling privileged access management, users will need to request just-in-time access to complete elevated and privileged tasks through an approval workflow that is highly scoped and time-bound. This gives users just-enough-access to perform the task at hand, without risking exposure of sensitive data or critical configuration settings. Enabling privileged access management in Office 365 will enable your organization to operate with zero standing privileges and provide a layer of defense against vulnerabilities arising because of such standing administrative access.</span></span> 

<span data-ttu-id="29468-110">В этом разделе будет поможет вам выполнить включение и настройка управления правами доступа в организации Office 365 и работать как справочное руководство для разрешения на запрос, утверждение и управления компонентом.</span><span class="sxs-lookup"><span data-stu-id="29468-110">This topic will guide you through enabling and configuring privileged access management in your Office 365 organization and serve as a reference guide for requesting, approving, and managing the feature.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="29468-111">Перед началом работы</span><span class="sxs-lookup"><span data-stu-id="29468-111">Before you begin</span></span>

### <a name="limited-functionality"></a><span data-ttu-id="29468-112">Ограниченная функциональность</span><span class="sxs-lookup"><span data-stu-id="29468-112">Limited functionality</span></span>
<span data-ttu-id="29468-p102">Во время общедоступной бета-версии привилегированный доступ функции управления доступны только через [Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell?view=exchange-ps) в Office 365. Правами доступа к освещает Вопросы управления определения задач на уровне командлетов для управления Exchange. В будущих версиях Office 365 привилегированный доступ функции будут доступны через портал администрирования и охватывает другие службы Office 365 рабочих нагрузок.</span><span class="sxs-lookup"><span data-stu-id="29468-p102">During the public beta, privileged access management features are only available through [Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell?view=exchange-ps) in Office 365. Privileged access management covers the task definitions at the level of Exchange management cmdlets. In future Office 365 releases, privileged access features will be available through the admin portal and will cover other Office 365 workloads services.</span></span>

### <a name="connecting-to-exchange-online-powershell"></a><span data-ttu-id="29468-116">Подключение к Exchange Online PowerShell</span><span class="sxs-lookup"><span data-stu-id="29468-116">Connecting to Exchange Online PowerShell</span></span>
<span data-ttu-id="29468-117">Действия по настройке в этот раздел поможет выполнить включение и использование правами доступа в Office 365 с помощью Exchange Online PowerShell.</span><span class="sxs-lookup"><span data-stu-id="29468-117">The configuration steps in this topic will walk you through enabling and using privileged access in Office 365 using Exchange Online PowerShell.</span></span> 

<span data-ttu-id="29468-118">Выполните действия, описанные в [подключение к Exchange Online PowerShell с помощью многофакторной проверки подлинности](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell?view=exchange-ps) для подключения к Exchange Online PowerShell с свои учетные данные Office 365, чтобы включить и настроить правами доступа в организации.</span><span class="sxs-lookup"><span data-stu-id="29468-118">Follow the steps in [Connect to Exchange Online PowerShell using Multi-Factor authentication](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell?view=exchange-ps) to connect to Exchange Online PowerShell with your Office 365 credentials to enable and configure privileged access for your organization.</span></span>

> [!NOTE]
> <span data-ttu-id="29468-p103">Необходимо включить многофакторной проверки подлинности для организации Office 365, выполните действия, чтобы включить привилегированный доступ при подключении к Exchange Online PowerShell. Подключение к многофакторной проверки подлинности создает маркер OAuth, используемый с правами доступа для ваших запросов для подписи.</span><span class="sxs-lookup"><span data-stu-id="29468-p103">You do not need to enable multi-factor authentication for your Office 365 organization to use the steps to enable privileged access while connecting to Exchange Online PowerShell. Connecting with multi-factor authentication creates an OAuth token that is used by privileged access for signing your requests.</span></span>

## <a name="enable-and-configure-privileged-access-management"></a><span data-ttu-id="29468-121">Включение и настройка управления правами доступа</span><span class="sxs-lookup"><span data-stu-id="29468-121">Enable and configure privileged access management</span></span>

### <a name="step-1---create-an-approvers-group"></a><span data-ttu-id="29468-122">Шаг 1 - Создание группы утверждающий</span><span class="sxs-lookup"><span data-stu-id="29468-122">Step 1 - Create an approver's group</span></span>
<span data-ttu-id="29468-p104">Портал администрирования Office 365, выберите **группы** > **Добавить группу**, нажмите Создать группу безопасности включена поддержка почты для доступа по умолчанию привилегированный утверждающих лиц. Закончив настройку, выберите **Добавить** , чтобы создавать и сохранять группы утверждающий.</span><span class="sxs-lookup"><span data-stu-id="29468-p104">From Office 365 Admin Portal, select **Groups** > **Add a group**, then create a mail enabled security group for the default privileged access approvers. When complete, select **Add** to create and save the approver group.</span></span>

![Экран утверждающие привилегированный доступ в портал администрирования Office 365](images/privileged-access-approvers-ui.png)

> [!NOTE] 
> <span data-ttu-id="29468-p105">В настоящее время для утверждения запросов из клиента Office 365 priviledged разрешены только пользователи с правами администратора. В следующих любой пользователь, который является частью в группе утверждающих будет иметь возможность утверждать запросы доступа.</span><span class="sxs-lookup"><span data-stu-id="29468-p105">At this time, only users with administrative access are allowed to approve requests from Office 365 priviledged access. In future any user who is part of the Approvers’ group will be able to approve access requests.</span></span>

### <a name="step-2---enable-privileged-access-in-office-365"></a><span data-ttu-id="29468-128">Шаг 2 - разрешение правами доступа в Office 365</span><span class="sxs-lookup"><span data-stu-id="29468-128">Step 2 - Enable privileged access in Office 365</span></span>
<span data-ttu-id="29468-129">Привилегированный доступ должен явно включены с группой утверждающий по умолчанию, включая набор системных учетных записей, которые необходимо исключить из управления доступом управления правами доступа.</span><span class="sxs-lookup"><span data-stu-id="29468-129">Privileged access needs to be explicitly turned on with the default approver group and including a set of system accounts that you’d want to be excluded from the privileged access management access control.</span></span> 

<span data-ttu-id="29468-130">Выполните следующую команду в Exchange Online PowerShell для включения правами доступа и Назначение группы утверждающий:</span><span class="sxs-lookup"><span data-stu-id="29468-130">Run the following command in Exchange Online PowerShell to enable privileged access and to assign the approver's group:</span></span>
```
Enable-ElevatedAccessControl -AdminGroup '<default approver group>' -SystemAccounts @('<systemAccountUPN1>','<systemAccountUPN2>')
```
<span data-ttu-id="29468-131">Пример.</span><span class="sxs-lookup"><span data-stu-id="29468-131">Example:</span></span>
```
Enable-ElevatedAccessControl -AdminGroup 'pamapprovers@fabrikam.onmicrosoft.com' -SystemAccounts @('sys1@fabrikamorg.onmicrosoft.com', sys2@fabrikamorg.onmicrosoft.com')
```

> [!NOTE]
> <span data-ttu-id="29468-132">Системных учетных записей, что компонент можно сделать доступной для обеспечения определенных automations в вашей организации могут работать без зависимостей привилегированный доступ, однако рекомендуется такое исключения быть исключительных и входящих должен быть одобрен и проверены регулярно.</span><span class="sxs-lookup"><span data-stu-id="29468-132">System accounts feature is made available to ensure certain automations within your organizations can work without dependency on privileged access, however it is recommended that such exclusions be exceptional and those allowed should be approved and audited regularly.</span></span>

### <a name="step-3---create-an-approval-policy"></a><span data-ttu-id="29468-133">Шаг 3 - создать политику утверждения</span><span class="sxs-lookup"><span data-stu-id="29468-133">Step 3 - Create an approval policy</span></span>
<span data-ttu-id="29468-p106">Политику утверждения позволяет определить требования к определенным утверждения, областью действия по отдельным задачам. Параметры типа утверждения, **автоматически** или **вручную**.</span><span class="sxs-lookup"><span data-stu-id="29468-p106">An approval policy allows you to define the specific approval requirements scoped at individual tasks. The approval type options are **Auto** or **Manual**.</span></span> 

<span data-ttu-id="29468-136">Выполните следующую команду в Exchange Online PowerShell, чтобы определить политику утверждения:</span><span class="sxs-lookup"><span data-stu-id="29468-136">Run the following command in Exchange Online PowerShell to define an approval policy:</span></span>
```
New-ElevatedAccessApprovalPolicy -Task 'Exchange\<exchange management cmdlet name>' -ApprovalType <Manual, Auto> -ApproverGroup '<default/custom approver group>'
```
<span data-ttu-id="29468-137">Пример.</span><span class="sxs-lookup"><span data-stu-id="29468-137">Example:</span></span>
```
New-ElevatedAccessApprovalPolicy -Task 'Exchange\New-MoveRequest' -ApprovalType Manual -ApproverGroup 'mbmanagers@fabrikamorg.onmicrosoft.com'
```

## <a name="using-privileged-access-in-your-office-365-organization"></a><span data-ttu-id="29468-138">С помощью привилегированной доступа в организации Office 365</span><span class="sxs-lookup"><span data-stu-id="29468-138">Using privileged access in your Office 365 organization</span></span>

### <a name="requesting-elevation-authorization-to-execute-tasks"></a><span data-ttu-id="29468-139">Разрешения на запрос повышения прав авторизации для выполнения задач</span><span class="sxs-lookup"><span data-stu-id="29468-139">Requesting elevation authorization to execute tasks</span></span>
<span data-ttu-id="29468-p107">Один раз включена, правами доступа требует утверждения для выполнения любой задачи, с которой определена политика связанного утверждения. Пользователи, которым необходимо выполнение задач, включенных в политику утверждения необходимо запросить и получить утверждение доступа для разрешения, необходимые для выполнения задачи.</span><span class="sxs-lookup"><span data-stu-id="29468-p107">Once enabled, privileged access requires approvals for executing any task that has an associated approval policy defined. Users needing to execute tasks included in the an approval policy must request and be granted access approval in order to have permissions necessary to execute the task.</span></span>

<span data-ttu-id="29468-142">Выполните следующую команду в Exchange Online PowerShell для создания и отправки запроса на утверждение утверждающий группе:</span><span class="sxs-lookup"><span data-stu-id="29468-142">Run the following command in Exchange Online PowerShell to create and submit an approval request to the approver's group:</span></span>
```
New-ElevatedAccessRequest -Task 'Exchange\<exchange management cmdlet name>' -Reason '<appropriate reason>' -DurationHours <duration in hours>
```
<span data-ttu-id="29468-143">Пример.</span><span class="sxs-lookup"><span data-stu-id="29468-143">Example:</span></span>
```
New-ElevatedAccessRequest -Task 'Exchange\New-MoveRequest' -Reason 'Attempting to fix the user mailbox error' -DurationHours 4
```
### <a name="view-status-of-elevation-requests"></a><span data-ttu-id="29468-144">Просмотр состояния запросы на повышение прав</span><span class="sxs-lookup"><span data-stu-id="29468-144">View status of elevation requests</span></span>
<span data-ttu-id="29468-145">После создания запроса на утверждение состояние запроса на повышение прав можно просмотреть с помощью связанного с идентификатором запроса.</span><span class="sxs-lookup"><span data-stu-id="29468-145">After an approval request is created, elevation request status can be reviewed using the associated with request ID.</span></span>

<span data-ttu-id="29468-146">Выполните следующую команду в Exchange Online PowerShell для просмотра состояния запросов утверждения для код конкретного запроса:</span><span class="sxs-lookup"><span data-stu-id="29468-146">Run the following command in Exchange Online PowerShell to view a approval request status for a specific request ID:</span></span>
```
Get-ElevatedAccessRequest -Identity <request ID> | select RequestStatus
```
<span data-ttu-id="29468-147">Пример.</span><span class="sxs-lookup"><span data-stu-id="29468-147">Example:</span></span>
```
Get-ElevatedAccessRequest -Identity 28560ed0-419d-4cc3-8f5b-603911cbd450 | select RequestStatus
```

### <a name="approving-an-elevation-authorization-request"></a><span data-ttu-id="29468-148">Утверждение запроса на повышение прав авторизации</span><span class="sxs-lookup"><span data-stu-id="29468-148">Approving an elevation authorization request</span></span>
<span data-ttu-id="29468-149">При создании запроса на утверждение, участники группы соответствующих утверждающий будет получать уведомления по электронной почте и может утвердить запрос, связанный с идентификатором запроса.</span><span class="sxs-lookup"><span data-stu-id="29468-149">When an approval request is created, members of the relevant approver group will receive an email notification and can approve the request associated with the request ID.</span></span> 

<span data-ttu-id="29468-150">Выполните следующую команду в Exchange Online PowerShell, чтобы утвердить запрос повышения авторизации:</span><span class="sxs-lookup"><span data-stu-id="29468-150">Run the following command in Exchange Online PowerShell to approve an elevation authorization request:</span></span>
```
Approve-ElevatedAccessRequest -RequestId <request id> -Comment '<approval comment>'
```
<span data-ttu-id="29468-151">Пример.</span><span class="sxs-lookup"><span data-stu-id="29468-151">Example:</span></span>
```
Approve-ElevatedAccessRequest -RequestId a4bc1bdf-00a1-42b4-be65-b6c63d6be279 -Comment '<approval comment>'
```
### <a name="denying-an-elevation-authorization-request"></a><span data-ttu-id="29468-152">Запрет на запрос повышения авторизации</span><span class="sxs-lookup"><span data-stu-id="29468-152">Denying an elevation authorization request</span></span>
<span data-ttu-id="29468-153">При создании запроса на утверждение, участники группы соответствующих утверждающий может запретить запрос, связанный с идентификатором запроса.</span><span class="sxs-lookup"><span data-stu-id="29468-153">When an approval request is created, members of the relevant approver group can deny the request associated with the request ID.</span></span> 

<span data-ttu-id="29468-154">Выполните следующую команду в Exchange Online PowerShell, чтобы запретить запрос повышения авторизации:</span><span class="sxs-lookup"><span data-stu-id="29468-154">Run the following command in Exchange Online PowerShell to deny an elevation authorization request:</span></span>
```
Deny-ElevatedAccessRequest -RequestId <request id> -Comment '<denial comment>'
```
<span data-ttu-id="29468-155">Пример.</span><span class="sxs-lookup"><span data-stu-id="29468-155">Example:</span></span>
```
Deny-ElevatedAccessRequest -RequestId a4bc1bdf-00a1-42b4-be65-b6c63d6be279 -Comment '<denial comment>'
```

### <a name="running-the-task"></a><span data-ttu-id="29468-156">Выполнение задачи</span><span class="sxs-lookup"><span data-stu-id="29468-156">Running the task</span></span>
<span data-ttu-id="29468-p108">После предоставления утверждения запроса пользователь может выполнять поставленной задачи и привилегированный доступ будет авторизации и выполнения задач от имени пользователя. Утверждение действителен для запрошенного duration (длительность по умолчанию — 4 часа), во время которого инициатор запроса может выполняться поставленной задачи несколько раз. Все выполнений вход и делаются доступными для безопасности и контроля соответствия требованиям.</span><span class="sxs-lookup"><span data-stu-id="29468-p108">After approval is granted, the requesting user can execute the intended task and privileged access will authorize and execute the task on users’ behalf. The approval remains valid for the requested duration (default duration is 4 hours), during which the requester can execute the intended task multiple times. All such executions are logged and made available for security and compliance auditing.</span></span> 

### <a name="disable-privileged-access-in-office-365"></a><span data-ttu-id="29468-160">Отключение правами доступа в Office 365</span><span class="sxs-lookup"><span data-stu-id="29468-160">Disable privileged access in Office 365</span></span>
<span data-ttu-id="29468-p109">При необходимости можно отключить управление правами доступа в Office 365. Отключение привилегиями доступа не удалять любые политики связанного утверждения или утверждающий группы.</span><span class="sxs-lookup"><span data-stu-id="29468-p109">If needed, you can disable privileged access management in Office 365. Disabling privileged access does not delete any associated approval policies or approver groups.</span></span>

<span data-ttu-id="29468-163">Выполните следующую команду в Exchange Online Powershell, чтобы отключить правами доступа:</span><span class="sxs-lookup"><span data-stu-id="29468-163">Run the following command in Exchange Online Powershell to disable privileged access:</span></span>

```
Disable-ElevatedAccessControl
```
## <a name="managed-access-to-microsoft-graph-in-microsoft-azure"></a><span data-ttu-id="29468-164">Управляемый доступ к Microsoft Graph в Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="29468-164">Managed access to Microsoft Graph in Microsoft Azure</span></span>

> [!IMPORTANT]
> <span data-ttu-id="29468-165">В этом разделе описывается развертывание и конфигурация руководство для общедоступных бета-версию Microsoft Graph компонент, в настоящее время доступны только в Office 365 E5 и дополнительные номера SKU соответствия требованиям.</span><span class="sxs-lookup"><span data-stu-id="29468-165">This section covers deployment and configuration guidance for a public beta Microsoft Graph feature only currently available in Office 365 E5 and Advanced Compliance SKUs.</span></span>

<span data-ttu-id="29468-p110">Управляемый доступ к Microsoft Graph в Microsoft Azure — это служба, которая позволяет организациям точный детальный уровень контроля над их данные Office 365. Эта система позволяет разработчикам приложений подделать обмена мнениями с этими данными.</span><span class="sxs-lookup"><span data-stu-id="29468-p110">Managed access to Microsoft Graph in Microsoft Azure is a service that helps organizations exert a granular level of control over their Office 365 data. This system allows application developers to forge insights with that data.</span></span> 

<span data-ttu-id="29468-p111">В этом система использует доступ к Office 365 привилегированный утверждение контроль над их данных с помощью его рабочего процесса утверждения, заданной областью доступа к данным Office 365 с помощью надзор за администрирования. Запросы данных быть, если приложения должны быть установлены и требуют доступа к данным Office 365.</span><span class="sxs-lookup"><span data-stu-id="29468-p111">This system uses Office 365 privileged access to assert control over their data through its approval workflow, allowing scoped access to Office 365 data with admin oversight. Requests for data come in when applications are installed and require access to Office 365 data.</span></span>

### <a name="view-request-details"></a><span data-ttu-id="29468-170">Просмотр сведений о запросе</span><span class="sxs-lookup"><span data-stu-id="29468-170">View request details</span></span>
<span data-ttu-id="29468-171">Просмотр сведений о запросы доступа к данным Office 365.</span><span class="sxs-lookup"><span data-stu-id="29468-171">View details of the access requests for Office 365 data.</span></span>

<span data-ttu-id="29468-172">Выполните следующую команду в Exchange Online Powershell позволяет просматривать запросы данных:</span><span class="sxs-lookup"><span data-stu-id="29468-172">Run the following command in Exchange Online Powershell to view data requests:</span></span>
```
Get-ElevatedAccessRequest | where {$_.RequestedAccess -like '*Data Access Request*'} | select RequestorUPN, Service, RequestedAccess | fl
```
<span data-ttu-id="29468-173">Пример выходных данных:</span><span class="sxs-lookup"><span data-stu-id="29468-173">Example output:</span></span>
```
RequestorUPN    : admin@contoso.com
Service         : Office365
RequestedAccess : Data Access Request
```

### <a name="approve-data-access-requests"></a><span data-ttu-id="29468-174">Утверждение запросов доступа к данным</span><span class="sxs-lookup"><span data-stu-id="29468-174">Approve data access requests</span></span>
<span data-ttu-id="29468-175">Все запросы доступа к данным могут быть утверждены через командлеты утверждения стандартных правами доступа.</span><span class="sxs-lookup"><span data-stu-id="29468-175">All data access requests can be approved through the standard privileged access approval cmdlets.</span></span>

<span data-ttu-id="29468-176">Выполните следующую команду в Exchange Online Powershell для утверждения запросов все данные для конкретных запросившая сторона:</span><span class="sxs-lookup"><span data-stu-id="29468-176">Run the following command in Exchange Online Powershell to approve all data requests for specific requestor:</span></span>

```
Approve-ElevatedAccessRequest -RequestId <request id> -Comment '<approval comment>'
```
<span data-ttu-id="29468-177">Пример.</span><span class="sxs-lookup"><span data-stu-id="29468-177">Example:</span></span>
```
Approve-ElevatedAccessRequest -RequestId a4bc1bdf-00a1-42b4-be65-b6c63d6be279 -Comment '<approval comment>'
```

## <a name="getting-help-and-providing-feedback"></a><span data-ttu-id="29468-178">Получение справки и оставлять отзывы</span><span class="sxs-lookup"><span data-stu-id="29468-178">Getting help and providing feedback</span></span>
<span data-ttu-id="29468-p112">Мы понимаем, что во время общедоступных бета-версию можно часто встречаются периодически ошибки или иметь отзывов и предложений на как можно улучшить управление правами доступа. Мы мнение и рекомендуем вам поделиться с нами:</span><span class="sxs-lookup"><span data-stu-id="29468-p112">We recognize that during the public beta you may come across an occasional bug or have feedback and suggestions on how we can improve privileged access management. We value your feedback and encourage you to share it with us:</span></span>
- <span data-ttu-id="29468-181">Учет ваш отзыв ad предложений в [Группы Yammer предварительной версии Office](https://www.yammer.com/officeenterprisenda/#/threads/inGroup?type=in_group&feedId=14435206).</span><span class="sxs-lookup"><span data-stu-id="29468-181">Post your feedback ad suggestions in the [Office Preview Yammer Group](https://www.yammer.com/officeenterprisenda/#/threads/inGroup?type=in_group&feedId=14435206).</span></span>
- <span data-ttu-id="29468-182">Файл отчеты об ошибках в разделе путь области «Office 365 правами доступа управление» на [VSO предварительной версии Office](https://office-previews.visualstudio.com/previews).</span><span class="sxs-lookup"><span data-stu-id="29468-182">File your bug reports under area path “Office 365 Privileged Access Management” on the [Office Preview VSO](https://office-previews.visualstudio.com/previews).</span></span>

## <a name="frequently-asked-questions"></a><span data-ttu-id="29468-183">Вопросы и ответы</span><span class="sxs-lookup"><span data-stu-id="29468-183">Frequently asked questions</span></span>

### <a name="what-skus-do-i-need-to-use-privileged-access-in-office-365"></a><span data-ttu-id="29468-184">Какие номера SKU необходимо использовать привилегированный доступ в Office 365?</span><span class="sxs-lookup"><span data-stu-id="29468-184">What SKUs do I need to use privileged access in Office 365?</span></span>
<span data-ttu-id="29468-185">Привилегированный доступ управления в Office 365 в данный момент доступна только для клиентов с E5 и дополнительные номера SKU соответствия требованиям.</span><span class="sxs-lookup"><span data-stu-id="29468-185">Privileged access management in Office 365 is currently only available for customers with E5 and Advanced Compliance SKUs.</span></span>

### <a name="when-will-privileged-access-be-available-for-office-365-workloads-beyond-exchange"></a><span data-ttu-id="29468-186">Когда будет доступен для рабочих нагрузок Office 365 за пределы Exchange привилегированный доступ?</span><span class="sxs-lookup"><span data-stu-id="29468-186">When will privileged access be available for Office 365 workloads beyond Exchange?</span></span>
<span data-ttu-id="29468-p113">Мы планирование предлагаемых этой функции в других рабочих нагрузок Office 365 в ближайшее время. Когда мы готовы для совместного использования временной шкалы, оно будет доступно через план Office 365.</span><span class="sxs-lookup"><span data-stu-id="29468-p113">We plan to offer this feature in other Office 365 workloads soon. When we’re ready to share a timeline, it will be available through the Office 365 roadmap.</span></span>

### <a name="how-is-this-different-from-azure-active-directorys-privileged-identity-management"></a><span data-ttu-id="29468-189">Как это отличается от управления удостоверениями привилегированной Azure Active Directory?</span><span class="sxs-lookup"><span data-stu-id="29468-189">How is this different from Azure Active Directory’s Privileged Identity Management?</span></span>
<span data-ttu-id="29468-p114">Привилегиями доступ к управления в Office 365 и [Azure AD привилегированной управления удостоверениями](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure) дополнения друг с другом, предоставляя доступ управления с доступом в времени в различных областях. Они обеспечивают надежный набор элементов управления для защиты данных.</span><span class="sxs-lookup"><span data-stu-id="29468-p114">Privileged access management in Office 365 and [Azure AD Privileged Identity Management](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure) complement each other by providing access control with just-in-time access at different scopes. Together they provide a robust set of controls for protecting your data.</span></span>

<span data-ttu-id="29468-p115">Привилегированный доступ могут быть определены и областью действия на уровне задачи, а Azure AD привилегированной управления удостоверениями применяется на уровне ролей с возможностью выполнение нескольких задач управления в Office 365.  Привилегированной Azure AD, управления удостоверениями в первую очередь можно управлять доступ для роли AD и группы ролей при привилегиями управления доступа в Office 365 применяется на уровне задачи.</span><span class="sxs-lookup"><span data-stu-id="29468-p115">Privileged access management in Office 365 can be defined and scoped at the task level, while Azure AD Privileged Identity Management applies at the role level with the ability to execute multiple tasks.  Azure AD Privileged Identity Management primarily allows managing accesses for AD roles and role groups while privileged access management in Office 365 is applied at the task level.</span></span>

 - <span data-ttu-id="29468-194">**Включение правами доступа к управления в Office 365 во время уже с помощью Azure AD привилегированной управления удостоверениями:** Добавление управление правами доступа в Office 365 может обеспечить еще один детальный уровень защиты и аудита возможности для привилегированный доступ к данным Office 365.</span><span class="sxs-lookup"><span data-stu-id="29468-194">**Enabling privileged access management in Office 365 while already using Azure AD Privileged Identity Management:** Adding privileged access management in Office 365 can provide another granular layer of protection and audit capabilities for privileged access to Office 365 data.</span></span>

- <span data-ttu-id="29468-195">**Включение Azure AD привилегированной управления удостоверениями во время использования уже привилегированный управления доступа в Office 365:**  Добавление Azure AD привилегированной управления удостоверениями в привилегиями управления доступа в Office 365 можно расширить привилегированный доступ к данным за пределами Office 365, определяемое в основном роли или удостоверение пользователя.</span><span class="sxs-lookup"><span data-stu-id="29468-195">**Enabling Azure AD Privileged Identity Management while already using privileged access management in Office 365:**  Adding Azure AD Privileged Identity Management to privileged access management in Office 365 can extend privileged access to data outside of Office 365 that’s primarily defined by a user’s role or identity.</span></span> 

### <a name="do-i-need-to-be-a-global-admin-to-manage-privileged-access-in-office-365"></a><span data-ttu-id="29468-196">Нужно ли быть глобального администратора для управления правами доступа в Office 365?</span><span class="sxs-lookup"><span data-stu-id="29468-196">Do I need to be a Global Admin to manage privileged access in Office 365?</span></span>
<span data-ttu-id="29468-p116">Во время получения ознакомительной версии необходимо привилегии глобального администратора, чтобы иметь возможность управления правами доступа в Office 365. Пользователей, которые включены в группе утверждающих не нужно быть глобального администратора, чтобы проверять и утверждать запросы.</span><span class="sxs-lookup"><span data-stu-id="29468-p116">During the preview you need to have Global Admin privilege to be able to manage privileged access in Office 365. Users who are included in an approvers’ group don't need to be a Global Admin to review and approve requests.</span></span> 

### <a name="how-is-privileged-access-management-in-office-365-related-to-customer-lockbox"></a><span data-ttu-id="29468-199">Как выполняется управление правами доступа в Office 365, связанные с защищенного хранилища клиента?</span><span class="sxs-lookup"><span data-stu-id="29468-199">How is privileged access management in Office 365 related to Customer Lockbox?</span></span>
<span data-ttu-id="29468-p117">[Защищенного хранилища клиента](https://support.office.com/article/Office-365-Customer-Lockbox-Requests-36f9cdd1-e64c-421b-a7e4-4a54d16440a2) позволяет уровень контроля доступа для организаций, для доступа к данным своим поставщиком услуг, например Microsoft. Привилегированный доступ управления в Office 365 позволяет управления детального доступа в рамках организации для всех задач привилегированный Office 365.</span><span class="sxs-lookup"><span data-stu-id="29468-p117">[Customer Lockbox](https://support.office.com/article/Office-365-Customer-Lockbox-Requests-36f9cdd1-e64c-421b-a7e4-4a54d16440a2) allows a level of access control for organizations for access to to data by their service provider, i.e. Microsoft. Privileged access management in Office 365 allows granular access control within an organization for all Office 365 privileged tasks.</span></span>