---
title: Администрирование почтовых ящиков Exchange Online в среде с поддержкой нескольких регионов
ms.reviewer: adwood
ms.author: chrisda
author: chrisda
manager: serdars
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: ''
localization_priority: Priority
description: Узнайте, как управлять параметрами поддержки нескольких регионов в Exchange Online с помощью Microsoft PowerShell.
ms.openlocfilehash: 4074748a9fdd567e37159198524acb3979291ef5
ms.sourcegitcommit: 265cc03b600e9015a44c60c3f8bb9075b1c20888
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2020
ms.locfileid: "41974001"
---
# <a name="administering-exchange-online-mailboxes-in-a-multi-geo-environment"></a><span data-ttu-id="798c7-103">Администрирование почтовых ящиков Exchange Online в среде с поддержкой нескольких регионов</span><span class="sxs-lookup"><span data-stu-id="798c7-103">Administering Exchange Online mailboxes in a multi-geo environment</span></span>

<span data-ttu-id="798c7-104">Для просмотра и настройки свойств нескольких регионов в среде Office 365 требуется удаленная оболочка PowerShell.</span><span class="sxs-lookup"><span data-stu-id="798c7-104">Remote PowerShell is required to view and configure multi geo properties in your Office 365 environment.</span></span> <span data-ttu-id="798c7-105">Сведения о подключении к Exchange Online PowerShell см. в статье [Подключение к Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).</span><span class="sxs-lookup"><span data-stu-id="798c7-105">To connect to Exchange Online PowerShell, see [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).</span></span>

<span data-ttu-id="798c7-106">Вам потребуется [модуль Microsoft Azure Active Directory PowerShell](https://social.technet.microsoft.com/wiki/contents/articles/28552.microsoft-azure-active-directory-powershell-module-version-release-history.aspx) версии 1.1.166.0 или более поздней в версии 1.x, чтобы просматривать свойство **PreferredDataLocation** пользовательских объектов.</span><span class="sxs-lookup"><span data-stu-id="798c7-106">You need the [Microsoft Azure Active Directory PowerShell Module](https://social.technet.microsoft.com/wiki/contents/articles/28552.microsoft-azure-active-directory-powershell-module-version-release-history.aspx) v1.1.166.0 or later in v1.x to see the **PreferredDataLocation** property on user objects.</span></span> <span data-ttu-id="798c7-107">Для пользовательских объектов, синхронизированных с помощью AAD Connect с AAD, нельзя изменить значение **PreferredDataLocation** непосредственно через AAD PowerShell.</span><span class="sxs-lookup"><span data-stu-id="798c7-107">User objects synchronized via AAD Connect into AAD cannot have their **PreferredDataLocation** value directly modified via AAD PowerShell.</span></span> <span data-ttu-id="798c7-108">Через AAD PowerShell можно изменять объекты облачных пользователей.</span><span class="sxs-lookup"><span data-stu-id="798c7-108">Cloud-only user objects can be modified via AAD PowerShell.</span></span> <span data-ttu-id="798c7-109">Сведения о подключении к Azure AD PowerShell см. в статье [Подключение к Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell).</span><span class="sxs-lookup"><span data-stu-id="798c7-109">To connect to Azure AD PowerShell, see [Connect to Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell).</span></span>

## <a name="connect-directly-to-a-geo-location-using-exchange-online-powershell"></a><span data-ttu-id="798c7-110">Прямое подключение к географическому расположению с помощью Exchange Online PowerShell</span><span class="sxs-lookup"><span data-stu-id="798c7-110">Connect directly to a geo location using Exchange Online PowerShell</span></span>

<span data-ttu-id="798c7-111">Обычно Exchange Online PowerShell подключается к центральному географическому расположению.</span><span class="sxs-lookup"><span data-stu-id="798c7-111">Typically, Exchange Online PowerShell will connect to the central geo location.</span></span> <span data-ttu-id="798c7-112">Но вы также можете подключиться непосредственно к периферийному географическому расположению.</span><span class="sxs-lookup"><span data-stu-id="798c7-112">But, you can also connect directly to satellite geo locations.</span></span> <span data-ttu-id="798c7-113">В связи с повышением производительности рекомендуется подключаться непосредственно к периферийному географическому расположению, если вы управляете пользователями только в этом расположении.</span><span class="sxs-lookup"><span data-stu-id="798c7-113">Because of performance improvements, we recommend connecting directly to the satellite geo location when you only manage users in that location.</span></span>

<span data-ttu-id="798c7-114">При подключении к определенным географическим расположениям параметр *ConnectionUri* отличается от указанного в инструкциях для обычного подключения.</span><span class="sxs-lookup"><span data-stu-id="798c7-114">To connect to a specific geo location, the *ConnectionUri* parameter is different than the regular connection instructions.</span></span> <span data-ttu-id="798c7-115">Остальные команды и значения совпадают.</span><span class="sxs-lookup"><span data-stu-id="798c7-115">The rest of the commands and values are the same.</span></span> <span data-ttu-id="798c7-116">Ниже описана последовательность действий.</span><span class="sxs-lookup"><span data-stu-id="798c7-116">The steps are:</span></span>

1. <span data-ttu-id="798c7-117">На локальном компьютере откройте Windows PowerShell и запустите следующую команду:</span><span class="sxs-lookup"><span data-stu-id="798c7-117">On your local computer, open Windows PowerShell and run the following command:</span></span>

   ```powershell
   $UserCredential = Get-Credential
   ```

   <span data-ttu-id="798c7-118">В диалоговом окне **Запрос учетных данных Windows PowerShell** введите свою рабочую или учебную учетную запись и пароль, а затем нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="798c7-118">In the **Windows PowerShell Credential Request** dialog box, type your work or school account and password, and then click **OK**.</span></span>

2. <span data-ttu-id="798c7-119">Замените `<emailaddress>` адресом электронной почты **любого** почтового ящика в целевом географическом расположении и выполните указанную ниже команду.</span><span class="sxs-lookup"><span data-stu-id="798c7-119">Replace `<emailaddress>` with the email address of **any** mailbox in the target geo location and run the following command.</span></span> <span data-ttu-id="798c7-120">Ваши разрешения для почтового ящика и связи с учетными данными из шага 1 не оказывают влияния; адрес электронной почты просто сообщает Exchange Online место подключения.</span><span class="sxs-lookup"><span data-stu-id="798c7-120">Your permissions on the mailbox and the relationship to your credentials in Step 1 are not a factor; the email address simply tells Exchange Online where to connect.</span></span>
  
   ```powershell
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=<emailaddress> -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```

   <span data-ttu-id="798c7-121">Например, если olga@contoso.onmicrosoft.com — это адрес электронной почты действительного почтового ящика в географическом расположении, к которому нужно подключиться, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="798c7-121">For example, if olga@contoso.onmicrosoft.com is the email address of a valid mailbox in the geo location where you want to connect, run the following command:</span></span>

   ```powershell
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=olga@contoso.onmicrosoft.com -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```

3. <span data-ttu-id="798c7-122">Выполните следующую команду.</span><span class="sxs-lookup"><span data-stu-id="798c7-122">Run the following command:</span></span>

    ```powershell
    Import-PSSession $Session
    ```

## <a name="view-the-available-geo-locations-that-are-configured-in-your-exchange-online-organization"></a><span data-ttu-id="798c7-123">Просмотр доступных географических расположений, настроенных в организации Exchange Online</span><span class="sxs-lookup"><span data-stu-id="798c7-123">View the available geo locations that are configured in your Exchange Online organization</span></span>

<span data-ttu-id="798c7-124">Чтобы просмотреть список настроенных географических расположений в Office 365 с поддержкой нескольких регионов, выполните следующую команду в Exchange Online PowerShell:</span><span class="sxs-lookup"><span data-stu-id="798c7-124">To see the list of configured geo locations in Office 365 Multi-Geo, run the following command in Exchange Online PowerShell:</span></span>

```powershell
Get-OrganizationConfig | Select -ExpandProperty AllowedMailboxRegions | Format-Table
```

## <a name="view-the-central-geo-location-for-your-exchange-online-organization"></a><span data-ttu-id="798c7-125">Просмотр центрального географического расположения для организации Exchange Online</span><span class="sxs-lookup"><span data-stu-id="798c7-125">View the central geo location for your Exchange Online organization</span></span>

<span data-ttu-id="798c7-126">Чтобы просмотреть центральное географическое расположение клиента, выполните следующую команду в Exchange Online PowerShell:</span><span class="sxs-lookup"><span data-stu-id="798c7-126">To view your tenant's central geo location, run the following command in Exchange Online PowerShell:</span></span>

```powershell
Get-OrganizationConfig | Select DefaultMailboxRegion
```

## <a name="find-the-geo-location-of-a-mailbox"></a><span data-ttu-id="798c7-127">Поиск географического расположения почтового ящика</span><span class="sxs-lookup"><span data-stu-id="798c7-127">Find the geo location of a mailbox</span></span>

<span data-ttu-id="798c7-128">Командлет **Get-Mailbox** в Exchange Online PowerShell отображает следующие свойства, связанные с поддержкой нескольких регионов, для почтовых ящиков:</span><span class="sxs-lookup"><span data-stu-id="798c7-128">The **Get-Mailbox** cmdlet in Exchange Online PowerShell displays the following multi-geo related properties on mailboxes:</span></span>

- <span data-ttu-id="798c7-129">**Database**. Первые 3 буквы имени базы данных соответствуют коду региона, указывающему текущее расположение почтового ящика.</span><span class="sxs-lookup"><span data-stu-id="798c7-129">**Database**: The first 3 letters of the database name correspond to the geo code, which tells you where the mailbox is currently located.</span></span> <span data-ttu-id="798c7-130">Для сетевых архивных почтовых ящиков следует использовать свойство **ArchiveDatabase**.</span><span class="sxs-lookup"><span data-stu-id="798c7-130">For Online Archive Mailboxes the **ArchiveDatabase** property should be used.</span></span>

- <span data-ttu-id="798c7-131">**MailboxRegion**. Указывает код географического расположения, установленный администратором (синхронизируется из параметра **PreferredDataLocation** в Azure AD).</span><span class="sxs-lookup"><span data-stu-id="798c7-131">**MailboxRegion**: Specifies the geo location code that was set by the admin (synchronized from **PreferredDataLocation** in Azure AD).</span></span>

- <span data-ttu-id="798c7-132">**MailboxRegionLastUpdateTime**. Указывает время последнего обновления MailboxRegion (автоматического или ручного).</span><span class="sxs-lookup"><span data-stu-id="798c7-132">**MailboxRegionLastUpdateTime**: Indicates when MailboxRegion was last updated (either automatically or manually).</span></span>

<span data-ttu-id="798c7-133">Чтобы просмотреть эти свойства для почтового ящика, используйте следующий синтаксис:</span><span class="sxs-lookup"><span data-stu-id="798c7-133">To see these properties for a mailbox, use the following syntax:</span></span>

```powershell
Get-Mailbox -Identity <MailboxIdentity> | Format-List Database,MailboxRegion*
```

<span data-ttu-id="798c7-134">Например, чтобы просмотреть сведения о географическом расположении для почтового ящика chris@contoso.onmicrosoft.com, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="798c7-134">For example, to see the geo location information for the mailbox chris@contoso.onmicrosoft.com, run the following command:</span></span>

```powershell
Get-Mailbox -Identity chris@contoso.onmicrosoft.com | Format-List Database, MailboxRegion*
```

<span data-ttu-id="798c7-135">Выходные данные команды выглядят так:</span><span class="sxs-lookup"><span data-stu-id="798c7-135">The output of the command looks like this:</span></span>

```powershell
Database                    : EURPR03DG077-db007
MailboxRegion               : EUR
MailboxRegionLastUpdateTime : 2/6/2018 8:21:01 PM
```

> <span data-ttu-id="798c7-136">**Примечание.** Если код географического расположения в имени базы данных не соответствует значению **MailboxRegion**, почтовый ящик автоматически помещается в очередь перемещения и переносится в географическое расположение, указанное значением **MailboxRegion** (Exchange Online ищет несоответствия между этими значениями свойств).</span><span class="sxs-lookup"><span data-stu-id="798c7-136">**Note:** If the geo location code in the database name doesn't match **MailboxRegion** value, the mailbox will be automatically be put into a relocation queue and moved to the geo location specified by the **MailboxRegion** value (Exchange Online looks for a mismatch between these property values).</span></span>

## <a name="move-an-existing-cloud-only-mailbox-to-a-specific-geo-location"></a><span data-ttu-id="798c7-137">Перемещение существующего облачного почтового ящика в определенное географическое расположение</span><span class="sxs-lookup"><span data-stu-id="798c7-137">Move an existing cloud-only mailbox to a specific geo location</span></span>

<span data-ttu-id="798c7-138">Облачный пользователь — это пользователь, не синхронизированный с клиентом посредством AAD Connect.</span><span class="sxs-lookup"><span data-stu-id="798c7-138">A cloud-only user is a user not synchronized to the tenant via AAD Connect.</span></span> <span data-ttu-id="798c7-139">Этот пользователь был создан непосредственно в Azure AD.</span><span class="sxs-lookup"><span data-stu-id="798c7-139">This user was created directly in Azure AD.</span></span> <span data-ttu-id="798c7-140">Используйте командлеты **Get-MsolUser** и **Set-MsolUser** модуля Azure AD для Windows PowerShell, чтобы просмотреть или указать географическое расположение для хранения почтового ящика облачного пользователя.</span><span class="sxs-lookup"><span data-stu-id="798c7-140">Use the **Get-MsolUser** and **Set-MsolUser** cmdlets in the Azure AD Module for Windows PowerShell to view or specify the geo location where a cloud-only user's mailbox will be stored.</span></span>

<span data-ttu-id="798c7-141">Чтобы просмотреть значение **PreferredDataLocation** для пользователя, используйте следующий синтаксис в Azure AD PowerShell:</span><span class="sxs-lookup"><span data-stu-id="798c7-141">To view the **PreferredDataLocation** value for a user, use this syntax in Azure AD PowerShell:</span></span>

```powershell
Get-MsolUser -UserPrincipalName <UserPrincipalName> | Format-List UserPrincipalName,PreferredDataLocation
```

<span data-ttu-id="798c7-142">Например, чтобы посмотреть значение **PreferredDataLocation** для пользователя michelle@contoso.onmicrosoft.com, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="798c7-142">For example, to see the **PreferredDataLocation** value for the user michelle@contoso.onmicrosoft.com, run the following command:</span></span>

```powershell
Get-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com | Format-List
```

<span data-ttu-id="798c7-143">Чтобы изменить значение **PreferredDataLocation** для объекта облачного пользователя, используйте следующий синтаксис в Azure AD PowerShell:</span><span class="sxs-lookup"><span data-stu-id="798c7-143">To modify the **PreferredDataLocation** value for a cloud-only user object, use the following syntax in Azure AD PowerShell:</span></span>

```powershell
Set-MsolUser -UserPrincipalName <UserPrincipalName> -PreferredDataLocation <GeoLocationCode>
```

<span data-ttu-id="798c7-144">Например, чтобы присвоить значению **PreferredDataLocation** регион Европейского Союза (EUR) для пользователя michelle@contoso.onmicrosoft.com, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="798c7-144">For example, to set the **PreferredDataLocation** value to the European Union (EUR) geo for the user michelle@contoso.onmicrosoft.com, run the following command:</span></span>

```powershell
Set-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com -PreferredDataLocation EUR
```

<span data-ttu-id="798c7-145">**Примечания**:</span><span class="sxs-lookup"><span data-stu-id="798c7-145">**Notes**:</span></span>

- <span data-ttu-id="798c7-146">Как указано выше, нельзя использовать эту процедуру для объектов синхронизированных пользователей из локальной службы Active Directory.</span><span class="sxs-lookup"><span data-stu-id="798c7-146">As mentioned previously you cannot use this procedure for synchronized user objects from on-premises Active Directory.</span></span> <span data-ttu-id="798c7-147">Нужно изменить значение **PreferredDataLocation** в Active Directory и синхронизировать его с помощью AAD Connect.</span><span class="sxs-lookup"><span data-stu-id="798c7-147">You need to change the **PreferredDataLocation** value in Active Directory and synchronize it using AAD Connect.</span></span> <span data-ttu-id="798c7-148">Дополнительные сведения см. в статье [Синхронизация Azure Active Directory Connect. Настройка предпочтительного расположения данных для ресурсов Office 365](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span><span class="sxs-lookup"><span data-stu-id="798c7-148">For more information, see [Azure Active Directory Connect sync: Configure preferred data location for Office 365 resources](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span></span>

- <span data-ttu-id="798c7-149">Продолжительность перемещения почтового ящика в новое географическое расположение зависит от нескольких факторов:</span><span class="sxs-lookup"><span data-stu-id="798c7-149">How long it takes to relocate a mailbox to a new geo location depends on several factors:</span></span>

  - <span data-ttu-id="798c7-150">Размер и тип почтового ящика.</span><span class="sxs-lookup"><span data-stu-id="798c7-150">The size and type of mailbox.</span></span>

  - <span data-ttu-id="798c7-151">Число перемещаемых почтовых ящиков.</span><span class="sxs-lookup"><span data-stu-id="798c7-151">The number of mailboxes being moved.</span></span>

  - <span data-ttu-id="798c7-152">Доступность ресурсов перемещения.</span><span class="sxs-lookup"><span data-stu-id="798c7-152">The availability of move resources.</span></span>

### <a name="move-disabled-mailboxes-that-are-on-litigation-hold"></a><span data-ttu-id="798c7-153">Перемещение отключенных почтовых ящиков, находящихся на судебном удержании</span><span class="sxs-lookup"><span data-stu-id="798c7-153">Move disabled mailboxes that are on Litigation Hold</span></span>

<span data-ttu-id="798c7-154">Отключенные почтовые ящики на судебном удержании, сохраненные для целей обнаружения электронных данных, невозможно переместить путем изменения их значения **PreferredDataLocation** в отключенном состоянии.</span><span class="sxs-lookup"><span data-stu-id="798c7-154">Disabled mailboxes on Litigation Hold that are preserved for eDiscovery purposes cannot be moved by changing their **PreferredDataLocation** value in their disabled state.</span></span> <span data-ttu-id="798c7-155">Чтобы переместить отключенный почтовый ящик на судебном удержании:</span><span class="sxs-lookup"><span data-stu-id="798c7-155">To move a disabled mailbox on litigation hold:</span></span>

1. <span data-ttu-id="798c7-156">Временно назначьте лицензию для почтового ящика.</span><span class="sxs-lookup"><span data-stu-id="798c7-156">Temporarily assign a license to the mailbox.</span></span>

2. <span data-ttu-id="798c7-157">Измените значение **PreferredDataLocation**.</span><span class="sxs-lookup"><span data-stu-id="798c7-157">Change the **PreferredDataLocation**.</span></span>

3. <span data-ttu-id="798c7-158">Удалите лицензию из почтового ящика после его перемещения в выбранное географическое расположение, чтобы вернуть его в отключенное состояние.</span><span class="sxs-lookup"><span data-stu-id="798c7-158">Remove the license from the mailbox after it has been moved to the selected geo location to put it back into the disabled state.</span></span>

## <a name="create-new-cloud-mailboxes-in-a-specific-geo-location"></a><span data-ttu-id="798c7-159">Создание новых облачных почтовых ящиков в определенном географическом расположении</span><span class="sxs-lookup"><span data-stu-id="798c7-159">Create new cloud mailboxes in a specific geo location</span></span>

<span data-ttu-id="798c7-160">Чтобы создать почтовый ящик в определенном географическом расположении, нужно выполнить одно из следующих действий:</span><span class="sxs-lookup"><span data-stu-id="798c7-160">To create a new mailbox in a specific geo location, you need to do either of these steps:</span></span>

- <span data-ttu-id="798c7-161">Настройте значение **PreferredDataLocation**, как описано в предыдущем разделе, *перед* созданием почтового ящика в Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="798c7-161">Configure the **PreferredDataLocation** value as described in the previous section *before* the mailbox is created in Exchange Online.</span></span> <span data-ttu-id="798c7-162">Например, настройте значение **PreferredDataLocation** для пользователя перед назначением лицензии.</span><span class="sxs-lookup"><span data-stu-id="798c7-162">For example, configure the **PreferredDataLocation** value on a user before assigning a license.</span></span>

- <span data-ttu-id="798c7-163">Назначьте лицензию одновременно с настройкой значения **PreferredDataLocation**.</span><span class="sxs-lookup"><span data-stu-id="798c7-163">Assign a license at the same time you set the **PreferredDataLocation** value.</span></span>

<span data-ttu-id="798c7-164">Чтобы создать облачного лицензированного пользователя (не синхронизированного с помощью AAD Connect) в определенном географическом расположении, используйте следующий синтаксис в Azure AD PowerShell:</span><span class="sxs-lookup"><span data-stu-id="798c7-164">To create a new cloud-only licensed user (not AAD Connect synchronized) in a specific geo location, use the following syntax in Azure AD PowerShell:</span></span>

```powershell
New-MsolUser -UserPrincipalName <UserPrincipalName> -DisplayName "<Display Name>" [-FirstName <FirstName>] [-LastName <LastName>] [-Password <Password>] [-LicenseAssignment <AccountSkuId>] -PreferredDataLocation <GeoLocationCode>
```

<span data-ttu-id="798c7-165">В этом примере создается новая учетная запись пользователя Elizabeth Brunner со следующими значениями:</span><span class="sxs-lookup"><span data-stu-id="798c7-165">This example create a new user account for Elizabeth Brunner with the following values:</span></span>

- <span data-ttu-id="798c7-166">Имя участника-пользователя: ebrunner@contoso.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="798c7-166">User principal name: ebrunner@contoso.onmicrosoft.com</span></span>

- <span data-ttu-id="798c7-167">Имя: Elizabeth</span><span class="sxs-lookup"><span data-stu-id="798c7-167">First name: Elizabeth</span></span>

- <span data-ttu-id="798c7-168">Фамилия: Brunner</span><span class="sxs-lookup"><span data-stu-id="798c7-168">Last name: Brunner</span></span>

- <span data-ttu-id="798c7-169">Отображаемое имя: Elizabeth Brunner</span><span class="sxs-lookup"><span data-stu-id="798c7-169">Display name: Elizabeth Brunner</span></span>

- <span data-ttu-id="798c7-170">Пароль: создается случайным образом и отображается в результатах команды (так как не используется параметр *Password*)</span><span class="sxs-lookup"><span data-stu-id="798c7-170">Password: randomly-generated and shown in the results of the command (because we're not using the *Password* parameter)</span></span>

- <span data-ttu-id="798c7-171">Лицензия: `contoso:ENTERPRISEPREMIUM` (E5)</span><span class="sxs-lookup"><span data-stu-id="798c7-171">License: `contoso:ENTERPRISEPREMIUM` (E5)</span></span>

- <span data-ttu-id="798c7-172">Расположение: Австралия (AUS)</span><span class="sxs-lookup"><span data-stu-id="798c7-172">Location: Australia (AUS)</span></span>

```powershell
New-MsolUser -UserPrincipalName ebrunner@contoso.onmicrosoft.com -DisplayName "Elizabeth Brunner" -FirstName Elizabeth -LastName Brunner -LicenseAssignment contoso:ENTERPRISEPREMIUM -PreferredDataLocation AUS
```

<span data-ttu-id="798c7-173">Дополнительные сведения о создании учетных записей пользователей и поиске значений LicenseAssignment в Azure AD PowerShell см. в статьях [Создание учетных записей пользователей с помощью PowerShell в Office 365](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell) и [Просмотр лицензий и служб с помощью PowerShell в Office 365](https://docs.microsoft.com/office365/enterprise/powershell/view-licenses-and-services-with-office-365-powershell).</span><span class="sxs-lookup"><span data-stu-id="798c7-173">For more information about creating new user accounts and finding LicenseAssignment values in Azure AD PowerShell, see [Create user accounts with Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell) and [View licenses and services with Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/view-licenses-and-services-with-office-365-powershell).</span></span>

> [!NOTE]
> <span data-ttu-id="798c7-174">Если вы используете Exchange Online PowerShell, чтобы включить почтовый ящик, и вам нужно создать почтовый ящик непосредственно в географическом расположении, указанном в параметре **PreferredDataLocation**, необходимо использовать командлет Exchange Online, например, **Enable-Mailbox** или **New-Mailbox**, прямо в облачной службе.</span><span class="sxs-lookup"><span data-stu-id="798c7-174">If you are using Exchange Online PowerShell to enable a mailbox and need the mailbox to be created directly in the geo location that's specified in **PreferredDataLocation**, you need to use an Exchange Online cmdlet such as **Enable-Mailbox** or **New-Mailbox** directly against the cloud service.</span></span> <span data-ttu-id="798c7-175">Если вы используете командлет **Enable-RemoteMailbox** в локальной среде Exchange PowerShell, почтовый ящик будет создан в центральном географическом расположении.</span><span class="sxs-lookup"><span data-stu-id="798c7-175">If you use the **Enable-RemoteMailbox** cmdlet in on-premises Exchange PowerShell, the mailbox will be created in the central geo location.</span></span>

## <a name="onboard-existing-on-premises-mailboxes-in-a-specific-geo-location"></a><span data-ttu-id="798c7-176">Перенос существующих локальных почтовых ящиков в определенное географическое расположение</span><span class="sxs-lookup"><span data-stu-id="798c7-176">Onboard existing on-premises mailboxes in a specific geo location</span></span>

<span data-ttu-id="798c7-177">Можно использовать стандартные средства и процедуры переноса для перемещения почтового ящика из локальной организации Exchange в Exchange Online, включая [информационную панель миграции в Центре администрирования Exchange](https://support.office.com/article/d164b35c-f624-4f83-ac58-b7cae96ab331) и командлет [New-MigrationBatch](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-migrationbatch) в Exchange Online PowerShell.</span><span class="sxs-lookup"><span data-stu-id="798c7-177">You can use the standard onboarding tools and processes to migrate a mailbox from an on-premises Exchange organization to Exchange Online, including the [Migration dashboard in the EAC](https://support.office.com/article/d164b35c-f624-4f83-ac58-b7cae96ab331), and the [New-MigrationBatch](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-migrationbatch) cmdlet in Exchange Online PowerShell.</span></span>

<span data-ttu-id="798c7-178">Сначала нужно подтвердить, что объект пользователя существует для каждого переносимого почтового ящика, и проверить правильность значения **PreferredDataLocation**, настроенного в Azure AD.</span><span class="sxs-lookup"><span data-stu-id="798c7-178">The first step is to verify a user object exists for each mailbox to be onboarded, and verify the correct **PreferredDataLocation** value is configured in Azure AD.</span></span> <span data-ttu-id="798c7-179">Средства переноса учитывают значение **PreferredDataLocation** и переносят почтовые ящики непосредственно в указанное географическое расположение.</span><span class="sxs-lookup"><span data-stu-id="798c7-179">The onboarding tools will respect the **PreferredDataLocation** value and will migrate the mailboxes directly to the specified geo location.</span></span>

<span data-ttu-id="798c7-180">Или можно использовать указанные ниже действия для переноса почтовых ящиков непосредственно в определенное географическое расположение с помощью командлета [New-MoveRequest](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-moverequest) в Exchange Online PowerShell.</span><span class="sxs-lookup"><span data-stu-id="798c7-180">Or, you can use the following steps to onboard mailboxes directly in a specific geo location using the [New-MoveRequest](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-moverequest) cmdlet in Exchange Online PowerShell.</span></span>

1. <span data-ttu-id="798c7-181">Убедитесь в наличии объекта пользователя для каждого переносимого почтового ящика и в установке нужного значения **PreferredDataLocation** в Azure AD.</span><span class="sxs-lookup"><span data-stu-id="798c7-181">Verify the user object exists for each mailbox to be onboarded and that **PreferredDataLocation** is set to the desired value in Azure AD.</span></span> <span data-ttu-id="798c7-182">Значение **PreferredDataLocation** синхронизируется с атрибутом **MailboxRegion** соответствующего объекта пользователя почты в Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="798c7-182">The value of **PreferredDataLocation** will be synchronized to the **MailboxRegion** attribute of the corresponding mail user object in Exchange Online.</span></span>

2. <span data-ttu-id="798c7-183">Напрямую подключитесь к определенному периферийному географическому расположению, следуя инструкциям по подключению, указанным выше в этой статье.</span><span class="sxs-lookup"><span data-stu-id="798c7-183">Connect directly to the specific satellite geo location using the connection instructions from earlier in this topic.</span></span>

3. <span data-ttu-id="798c7-184">В Exchange Online PowerShell сохраните учетные данные локального администратора, использующиеся для выполнения переноса почтового ящика, в переменной, выполнив следующую команду:</span><span class="sxs-lookup"><span data-stu-id="798c7-184">In Exchange Online PowerShell, store the on-premises administrator credentials that's used to perform a mailbox migration in a variable by running the following command:</span></span>

   ```powershell
   $RC = Get-Credential
   ```

4. <span data-ttu-id="798c7-185">В Exchange Online PowerShell, создайте новый командлет **New-MoveRequest**, как в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="798c7-185">In Exchange Online PowerShell, create a new **New-MoveRequest** similar to the following example:</span></span>

   ```powershell
   New-MoveRequest -Remote -RemoteHostName mail.contoso.com -RemoteCredential $RC -Identity user@contoso.com -TargetDeliveryDomain <YourAppropriateDomain>
   ```

5. <span data-ttu-id="798c7-186">Повторите шаг 4 для каждого почтового ящика, требующего переноса из локальной среды Exchange в периферийное географическое расположение, к которому вы в настоящее время подключены.</span><span class="sxs-lookup"><span data-stu-id="798c7-186">Repeat step #4 for every mailbox you need to migrate from on-premises Exchange to the satellite geo location you are currently connected to.</span></span>

6. <span data-ttu-id="798c7-187">Если нужно перенести дополнительные почтовые ящики в другое периферийное географическое расположение, повторите шаги 2–4 для каждого определенного периферийного расположения.</span><span class="sxs-lookup"><span data-stu-id="798c7-187">If you need to migrate additional mailboxes to different satellite geo locations, repeat steps 2 through 4 for each specific location.</span></span>

## <a name="multi-geo-reporting"></a><span data-ttu-id="798c7-188">Отчеты об использовании нескольких регионов</span><span class="sxs-lookup"><span data-stu-id="798c7-188">Multi-geo reporting</span></span>

<span data-ttu-id="798c7-189">**Отчеты об использовании нескольких регионов** в Центре администрирования Microsoft 365 отображают число пользователей по географическим расположениям.</span><span class="sxs-lookup"><span data-stu-id="798c7-189">**Multi-Geo Usage Reports** in the Microsoft 365 admin center displays the user count by geo location.</span></span> <span data-ttu-id="798c7-190">Отчет отображает распределение пользователей в текущем месяце и представляет ретроспективные данные за последние 6 месяцев.</span><span class="sxs-lookup"><span data-stu-id="798c7-190">The report displays user distribution for the current month and provides historical data for the past 6 months.</span></span>

## <a name="see-also"></a><span data-ttu-id="798c7-191">См. также</span><span class="sxs-lookup"><span data-stu-id="798c7-191">See also</span></span>

[<span data-ttu-id="798c7-192">Управление Office 365 и Exchange Online с помощью Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="798c7-192">Managing Office 365 and Exchange Online with Windows PowerShell</span></span>](https://support.office.com//article/06a743bb-ceb6-49a9-a61d-db4ffdf54fa6)
