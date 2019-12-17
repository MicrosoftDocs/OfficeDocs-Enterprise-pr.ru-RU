---
title: Подготовка домена, не поддерживающего маршрутизацию, для синхронизации службы каталогов
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
f1_keywords:
- O365E_SetupDirSyncLocalDir
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: e7968303-c234-46c4-b8b0-b5c93c6d57a7
description: Сведения о том, что делать, если у вас нет домена раутале, связанного с локальными пользователями, прежде чем выполнять синхронизацию с Office 365.
ms.openlocfilehash: 013d29acdd3761793a93dab1eb8583324ba08591
ms.sourcegitcommit: 3539ec707f984de6f3b874744ff8b6832fbd665e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/17/2019
ms.locfileid: "40072421"
---
# <a name="prepare-a-non-routable-domain-for-directory-synchronization"></a><span data-ttu-id="7f57c-103">Подготовка домена, не поддерживающего маршрутизацию, для синхронизации службы каталогов</span><span class="sxs-lookup"><span data-stu-id="7f57c-103">Prepare a non-routable domain for directory synchronization</span></span>
<span data-ttu-id="7f57c-104">При синхронизации локального каталога с Office 365 необходимо иметь проверенный домен в Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="7f57c-104">When you synchronize your on-premises directory with Office 365 you have to have a verified domain in Azure Active Directory.</span></span> <span data-ttu-id="7f57c-105">Синхронизируются только имена участников-пользователей (UPN), связанные с локальным доменом.</span><span class="sxs-lookup"><span data-stu-id="7f57c-105">Only the User Principal Names (UPN) that are associated with the on-premises domain are synchronized.</span></span> <span data-ttu-id="7f57c-106">Тем не менее, любой UPN, который содержит домен без поддержки маршрутизации, например Local (например, billa@contoso. local), будет синхронизирован с доменом onmicrosoft.com (например, billa@contoso.onmicrosoft.com).</span><span class="sxs-lookup"><span data-stu-id="7f57c-106">However, any UPN that contains an non-routable domain, for example .local (like billa@contoso.local), will be synchronized to an .onmicrosoft.com domain (like billa@contoso.onmicrosoft.com).</span></span> 

<span data-ttu-id="7f57c-107">Если в настоящее время для учетных записей пользователей в Active Directory используется локальный домен, рекомендуется изменить их на использование проверенного домена (например, billa@contoso.com), чтобы обеспечить правильную синхронизацию с доменом Office 365.</span><span class="sxs-lookup"><span data-stu-id="7f57c-107">If you currently use a .local domain for your user accounts in Active Directory it's recommended that you change them to use a verified domain (like billa@contoso.com) in order to properly sync with your Office 365 domain.</span></span>
  
## <a name="what-if-i-only-have-a-local-on-premises-domain"></a><span data-ttu-id="7f57c-108">Что делать, если у меня есть только локальный домен.</span><span class="sxs-lookup"><span data-stu-id="7f57c-108">What if I only have a .local on-premises domain?</span></span>

<span data-ttu-id="7f57c-109">Самое последнее средство, которое можно использовать для синхронизации Active Directory с Azure Active Directory, называется Azure AD Connect.</span><span class="sxs-lookup"><span data-stu-id="7f57c-109">The most recent tool you can use for synchronizing your Active Directory to Azure Active Directory is named Azure AD Connect.</span></span> <span data-ttu-id="7f57c-110">Дополнительные сведения см. в статье [Интеграция локальных удостоверений с Azure Active Directory](https://docs.microsoft.com/azure/architecture/reference-architectures/identity/azure-ad).</span><span class="sxs-lookup"><span data-stu-id="7f57c-110">For more information, see [Integrating your on-premises identities with Azure Active Directory](https://docs.microsoft.com/azure/architecture/reference-architectures/identity/azure-ad).</span></span>
  
<span data-ttu-id="7f57c-111">Azure AD Connect синхронизирует UPN и пароль пользователей, чтобы пользователи могли входить в систему с теми же учетными данными, которые они используют в локальной среде.</span><span class="sxs-lookup"><span data-stu-id="7f57c-111">Azure AD Connect synchronizes your users' UPN and password so that users can sign in with the same credentials they use on-premises.</span></span> <span data-ttu-id="7f57c-112">Однако Azure AD Connect синхронизирует только пользователей с доменами, которые проверяются в Office 365.</span><span class="sxs-lookup"><span data-stu-id="7f57c-112">However, Azure AD Connect only synchronizes users to domains that are verified by Office 365.</span></span> <span data-ttu-id="7f57c-113">Это означает, что домен также проверяется с помощью Azure Active Directory, так как удостоверения Office 365 управляются Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="7f57c-113">This means that the domain also is verified by Azure Active Directory because Office 365 identities are managed by Azure Active Directory.</span></span> <span data-ttu-id="7f57c-114">Другими словами, домен должен быть допустимым Интернет-доменом (например,. com,. org, .NET,. US и т. д.).</span><span class="sxs-lookup"><span data-stu-id="7f57c-114">In other words, the domain has to be a valid Internet domain (for example, .com, .org, .net, .us, etc.).</span></span> <span data-ttu-id="7f57c-115">Если во внутренней Active Directory используется только домен, не поддерживающий маршрутизацию (например, Local), это может привести к тому, что проверенный домен, установленный в Office 365.</span><span class="sxs-lookup"><span data-stu-id="7f57c-115">If your internal Active Directory only uses a non-routable domain (for example, .local), this can't possibly match the verified domain you have on Office 365.</span></span> <span data-ttu-id="7f57c-116">Эту проблему можно устранить, либо изменив основной домен в локальной службе Active Directory, либо добавив один или несколько суффиксов имени участника-пользователя.</span><span class="sxs-lookup"><span data-stu-id="7f57c-116">You can fix this issue by either changing your primary domain in your on premises Active Directory, or by adding one or more UPN suffixes.</span></span>
  
### <a name="change-your-primary-domain"></a><span data-ttu-id="7f57c-117">**Изменение основного домена**</span><span class="sxs-lookup"><span data-stu-id="7f57c-117">**Change your primary domain**</span></span>

<span data-ttu-id="7f57c-118">Замените основной домен на домен, проверенный в Office 365, например contoso.com.</span><span class="sxs-lookup"><span data-stu-id="7f57c-118">Change your primary domain to a domain you have verified in Office 365, for example, contoso.com.</span></span> <span data-ttu-id="7f57c-119">После этого все пользователи с доменом contoso. local обновляются до contoso.com.</span><span class="sxs-lookup"><span data-stu-id="7f57c-119">Every user that has the domain contoso.local is then updated to contoso.com.</span></span> <span data-ttu-id="7f57c-120">Инструкции [о том, как работает переименование домена](https://go.microsoft.com/fwlink/p/?LinkId=624174).</span><span class="sxs-lookup"><span data-stu-id="7f57c-120">For instructions, see [How Domain Rename Works](https://go.microsoft.com/fwlink/p/?LinkId=624174).</span></span> <span data-ttu-id="7f57c-121">Тем не менее, это очень сложный процесс, и более простое решение описано в следующем разделе.</span><span class="sxs-lookup"><span data-stu-id="7f57c-121">This is a very involved process, however, and an easier solution is described in the following section.</span></span>
  
### <a name="add-upn-suffixes-and-update-your-users-to-them"></a><span data-ttu-id="7f57c-122">**Добавление суффиксов UPN и обновление пользователей**</span><span class="sxs-lookup"><span data-stu-id="7f57c-122">**Add UPN suffixes and update your users to them**</span></span>

<span data-ttu-id="7f57c-123">Проблему можно устранить, зарегистрировав новые суффиксы UPN или суффиксы в Active Directory в соответствии с доменом (или доменам), проверенным в Office 365.</span><span class="sxs-lookup"><span data-stu-id="7f57c-123">You can solve the .local problem by registering new UPN suffix or suffixes in Active Directory to match the domain (or domains) you verified in Office 365.</span></span> <span data-ttu-id="7f57c-124">После регистрации нового суффикса вы обновите имя пользователя UPN, чтобы заменить. local на новое доменное имя например, чтобы учетная запись пользователя выглядела как billa@contoso.com.</span><span class="sxs-lookup"><span data-stu-id="7f57c-124">After you register the new suffix, you update the user UPNs to replace the .local with the new domain name for example so that a user account looks like billa@contoso.com.</span></span>
  
<span data-ttu-id="7f57c-125">После обновления UPN для использования проверенного домена можно приступать к синхронизации локальной службы Active Directory с Office 365.</span><span class="sxs-lookup"><span data-stu-id="7f57c-125">After you have updated the UPNs to use the verified domain,you are ready to synchronize your on-premises Active Directory with Office 365.</span></span>
  
 <span data-ttu-id="7f57c-126">**Шаг 1: Добавление нового суффикса имени участника-пользователя**</span><span class="sxs-lookup"><span data-stu-id="7f57c-126">**Step 1: Add the new UPN suffix**</span></span>
  
1. <span data-ttu-id="7f57c-127">На сервере, на котором работает доменные службы Active Directory (AD DS), в диспетчере серверов выберите **инструменты** \> **Active Directory — домены и доверие**.</span><span class="sxs-lookup"><span data-stu-id="7f57c-127">On the server that Active Directory Domain Services (AD DS) runs on, in the Server Manager choose **Tools** \> **Active Directory Domains and Trusts**.</span></span>
    
    <span data-ttu-id="7f57c-128">**Если у вас нет Windows Server 2012**</span><span class="sxs-lookup"><span data-stu-id="7f57c-128">**Or, if you don't have Windows Server 2012**</span></span>
    
    <span data-ttu-id="7f57c-129">Нажмите клавиши **Windows + R** , чтобы открыть диалоговое окно **Run** , а затем введите в поле Domain. msc, а затем нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="7f57c-129">Press **Windows key + R** to open the **Run** dialog, and then type in Domain.msc, and then choose **OK**.</span></span>
    
    ![Выберите пункт Active Directory — домены и доверие.](media/46b6e007-9741-44af-8517-6f682e0ac974.png)
  
2. <span data-ttu-id="7f57c-131">В окне " **Active Directory — домены и доверие** " щелкните правой кнопкой мыши **Active Directory — домены и доверие**, а затем выберите пункт **Свойства**.</span><span class="sxs-lookup"><span data-stu-id="7f57c-131">On the **Active Directory Domains and Trusts** window, right-click **Active Directory Domains and Trusts**, and then choose **Properties**.</span></span>
    
    ![Щелкните правой кнопкой мыши "домены и доверие" ActiveDirectory и выберите пункт "Свойства".](media/39d20812-ffb5-4ba9-8d7b-477377ac360d.png)
  
3. <span data-ttu-id="7f57c-133">На вкладке **UPN-суффиксы** в поле **Дополнительные UPN-суффиксы** введите новые суффиксы UPN или суффиксы, а затем нажмите кнопку **Add** \> **Apply**(Добавить).</span><span class="sxs-lookup"><span data-stu-id="7f57c-133">On the **UPN Suffixes** tab, in the **Alternative UPN Suffixes** box, type your new UPN suffix or suffixes, and then choose **Add** \> **Apply**.</span></span>
    
    ![Добавление нового суффикса имени участника-пользователя](media/a4aaf919-7adf-469a-b93f-83ef284c0915.PNG)
  
    <span data-ttu-id="7f57c-135">Завершив добавление суффиксов, нажмите кнопку **ОК** .</span><span class="sxs-lookup"><span data-stu-id="7f57c-135">Choose **OK** when you're done adding suffixes.</span></span> 
    
 <span data-ttu-id="7f57c-136">**Шаг 2: изменение суффикса имени участника-пользователя для существующих пользователей**</span><span class="sxs-lookup"><span data-stu-id="7f57c-136">**Step 2: Change the UPN suffix for existing users**</span></span>
  
1. <span data-ttu-id="7f57c-137">На сервере, на котором работает доменные службы Active Directory (AD DS), в окне Диспетчер серверов выберите **инструменты** \> **Active Directory пользователи и компьютеры Active**Directory.</span><span class="sxs-lookup"><span data-stu-id="7f57c-137">On the server that Active Directory Domain Services (AD DS) runs on, in the Server Manager choose **Tools** \> **Active Directory Active Directory Users and Computers**.</span></span>
    
    <span data-ttu-id="7f57c-138">**Если у вас нет Windows Server 2012**</span><span class="sxs-lookup"><span data-stu-id="7f57c-138">**Or, if you don't have Windows Server 2012**</span></span>
    
    <span data-ttu-id="7f57c-139">Нажмите клавиши **Windows + R** , чтобы открыть диалоговое окно **Run** , а затем введите в DSA. msc, а затем нажмите кнопку **ОК** .</span><span class="sxs-lookup"><span data-stu-id="7f57c-139">Press **Windows key + R** to open the **Run** dialog, and then type in Dsa.msc, and then click **OK**</span></span>
    
2. <span data-ttu-id="7f57c-140">Выберите пользователя, щелкните его правой кнопкой мыши и выберите пункт **Свойства**.</span><span class="sxs-lookup"><span data-stu-id="7f57c-140">Select a user, right-click, and then choose **Properties**.</span></span>
    
3. <span data-ttu-id="7f57c-141">На вкладке **учетная запись** в раскрывающемся списке суффикс UPN выберите новый суффикс UPN и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="7f57c-141">On the **Account** tab, in the UPN suffix drop-down list, choose the new UPN suffix, and then choose **OK**.</span></span>
    
    ![Добавление нового суффикса имени участника-пользователя для пользователя](media/54876751-49f0-48cc-b864-2623c4835563.png)
  
4. <span data-ttu-id="7f57c-143">Выполните указанные ниже действия для каждого пользователя.</span><span class="sxs-lookup"><span data-stu-id="7f57c-143">Complete these steps for every user.</span></span>
    
   
### <a name="you-can-also-use-windows-powershell-to-change-the-upn-suffix-for-all-users"></a><span data-ttu-id="7f57c-144">**Вы также можете использовать Windows PowerShell для изменения суффикса имени участника-пользователя для всех пользователей**</span><span class="sxs-lookup"><span data-stu-id="7f57c-144">**You can also use Windows PowerShell to change the UPN suffix for all users**</span></span>

<span data-ttu-id="7f57c-145">Если у вас много пользователей для обновления, проще использовать Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7f57c-145">If you have a lot of users to update, it is easier to use Windows PowerShell.</span></span> <span data-ttu-id="7f57c-146">В следующем примере командлеты [Get – ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624312) и [Set – ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624313) используются для изменения всех суффиксов contoso. local на contoso.com.</span><span class="sxs-lookup"><span data-stu-id="7f57c-146">The following example uses the cmdlets [Get-ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624312) and [Set-ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624313) to change all contoso.local suffixes to contoso.com.</span></span> 

<span data-ttu-id="7f57c-147">Выполните следующие команды Windows PowerShell, чтобы обновить все локальные суффиксы contoso. contoso.com:</span><span class="sxs-lookup"><span data-stu-id="7f57c-147">Run the following Windows PowerShell commands to update all contoso.local suffixes to contoso.com:</span></span>
    
  ```powershell
  $LocalUsers = Get-ADUser -Filter {UserPrincipalName -like '*contoso.local'} -Properties userPrincipalName -ResultSetSize $null
  $LocalUsers | foreach {$newUpn = $_.UserPrincipalName.Replace("contoso.local","contoso.com"); $_ | Set-ADUser -UserPrincipalName $newUpn}
  ```

<span data-ttu-id="7f57c-148">Чтобы узнать больше об использовании Windows PowerShell в Active Directory, обратитесь к разделу [Windows PowerShell Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=624314) .</span><span class="sxs-lookup"><span data-stu-id="7f57c-148">See [Active Directory Windows PowerShell module](https://go.microsoft.com/fwlink/p/?LinkId=624314) to learn more about using Windows PowerShell in Active Directory.</span></span> 

