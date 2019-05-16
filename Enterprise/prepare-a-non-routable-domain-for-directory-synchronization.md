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
ms.openlocfilehash: 15ab67212ec1ea6ca7665bb5a4b0748f7d85adb5
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "34071085"
---
# <a name="prepare-a-non-routable-domain-for-directory-synchronization"></a>Подготовка домена, не поддерживающего маршрутизацию, для синхронизации службы каталогов
При синхронизации локального каталога с Office 365 необходимо иметь проверенный домен в Azure Active Directory. Синхронизируются только имена участников-пользователей (UPN), связанные с локальным доменом. Тем не менее, любой UPN, который содержит домен без маршрутизации, например, Local (например, Билла @ contoso. local), будет синхронизирован с доменом onmicrosoft.com (например, billa@contoso.onmicrosoft.com). 

Если в настоящее время для учетных записей пользователей в Active Directory используется локальный домен, рекомендуется изменить их на использование проверенного домена (например, billa@contoso.com), чтобы обеспечить правильную синхронизацию с доменом Office 365.
  
## <a name="what-if-i-only-have-a-local-on-premises-domain"></a>Что делать, если у меня есть только локальный домен.

Самое последнее средство, которое можно использовать для синхронизации Active Directory с Azure Active Directory, называется Azure AD Connect. Дополнительные сведения см. в статье [Интеграция локальных удостоверений с Azure Active Directory](https://docs.microsoft.com/azure/architecture/reference-architectures/identity/azure-ad).
  
Azure AD Connect синхронизирует UPN и пароль пользователей, чтобы пользователи могли входить в систему с теми же учетными данными, которые они используют в локальной среде. Однако Azure AD Connect синхронизирует только пользователей с доменами, которые проверяются в Office 365. Это означает, что домен также проверяется с помощью Azure Active Directory, так как удостоверения Office 365 управляются Azure Active Directory. Другими словами, домен должен быть допустимым Интернет-доменом (например,. com,. org, .NET,. US и т. д.). Если во внутренней Active Directory используется только домен, не поддерживающий маршрутизацию (например, Local), это может привести к тому, что проверенный домен, установленный в Office 365. Эту проблему можно устранить, либо изменив основной домен в локальной службе Active Directory, либо добавив один или несколько суффиксов имени участника-пользователя.
  
### <a name="change-your-primary-domain"></a>**Изменение основного домена**

Замените основной домен на домен, проверенный в Office 365, например contoso.com. После этого все пользователи с доменом contoso. local обновляются до contoso.com. Инструкции [о том, как работает переименование домена](https://go.microsoft.com/fwlink/p/?LinkId=624174). Это очень сложный процесс, но проще всего [Добавить суффиксы UPN и обновить пользователей на них](prepare-a-non-routable-domain-for-directory-synchronization.md#bk_register), как показано в следующем разделе.
  
### <a name="add-upn-suffixes-and-update-your-users-to-them"></a>**Добавление суффиксов UPN и обновление пользователей**

Проблему можно устранить, зарегистрировав новые суффиксы UPN или суффиксы в Active Directory в соответствии с доменом (или доменам), проверенным в Office 365. После регистрации нового суффикса вы обновите имя пользователя UPN, чтобы заменить. local на новое доменное имя например, чтобы учетная запись пользователя выглядела как billa@contoso.com.
  
После обновления UPN для использования проверенного домена можно приступать к синхронизации локальной службы Active Directory с Office 365.
  
 **Шаг 1: Добавление нового суффикса имени участника-пользователя**
  
1. На сервере, на котором работает доменные службы Active Directory (AD DS), в диспетчере серверов выберите **инструменты** \> **Active Directory — домены и доверие**.
    
    **Если у вас нет Windows Server 2012**
    
    Нажмите клавиши **Windows + R** , чтобы открыть диалоговое окно **Run** , а затем введите в поле Domain. msc, а затем нажмите кнопку **ОК**.
    
    ![Выберите пункт Active Directory — домены и доверие.](media/46b6e007-9741-44af-8517-6f682e0ac974.png)
  
2. В окне " **Active Directory — домены и доверие** " щелкните правой кнопкой мыши **Active Directory — домены и доверие**, а затем выберите пункт **Свойства**.
    
    ![Щелкните правой кнопкой мыши "домены и доверие" ActiveDirectory и выберите пункт "Свойства".](media/39d20812-ffb5-4ba9-8d7b-477377ac360d.png)
  
3. На вкладке **UPN** -суффиксы в поле **Дополнительные UPN** -суффиксы введите новые суффиксы UPN или суффиксы, а затем нажмите кнопку **Add** \> **Apply**(Добавить).
    
    ![Добавление нового суффикса имени участника-пользователя](media/a4aaf919-7adf-469a-b93f-83ef284c0915.PNG)
  
    Завершив добавление суффиксов, нажмите кнопку **ОК** . 
    
 **Шаг 2: изменение суффикса имени участника-пользователя для существующих пользователей**
  
1. На сервере, на котором работает доменные службы Active Directory (AD DS), в окне Диспетчер серверов выберите **инструменты** \> **Active Directory пользователи и компьютеры Active**Directory.
    
    **Если у вас нет Windows Server 2012**
    
    Нажмите клавиши **Windows + R** , чтобы открыть диалоговое окно **Run** , а затем введите в DSA. msc, а затем нажмите кнопку **ОК** .
    
2. Выберите пользователя, щелкните его правой кнопкой мыши и выберите пункт **Свойства**.
    
3. На вкладке **учетная запись** в раскрывающемся списке суффикс UPN выберите новый суффикс UPN и нажмите кнопку **ОК**.
    
    ![Добавление нового суффикса имени участника-пользователя для пользователя](media/54876751-49f0-48cc-b864-2623c4835563.png)
  
4. Выполните указанные ниже действия для каждого пользователя.
    
    Кроме того, можно выполнить массовое обновление суффиксов имени участника-пользователя [, но вы также можете использовать Windows PowerShell для изменения суффикса имени участника-пользователя для всех пользователей](prepare-a-non-routable-domain-for-directory-synchronization.md#BK_Posh).
    
### <a name="you-can-also-use-windows-powershell-to-change-the-upn-suffix-for-all-users"></a>**Вы также можете использовать Windows PowerShell для изменения суффикса имени участника-пользователя для всех пользователей**

Если у вас много пользователей для обновления, проще использовать Windows PowerShell. В следующем примере командлеты [Get – ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624312) и [Set – ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624313) используются для изменения всех суффиксов contoso. local на contoso.com. 

Выполните следующие команды Windows PowerShell, чтобы обновить все локальные суффиксы contoso. contoso.com:
    
  ```
  $LocalUsers = Get-ADUser -Filter {UserPrincipalName -like '*contoso.local'} -Properties userPrincipalName -ResultSetSize $null
  ```

  ```
  $LocalUsers | foreach {$newUpn = $_.UserPrincipalName.Replace("contoso.local","contoso.com"); $_ | Set-ADUser -UserPrincipalName $newUpn}
  ```
Чтобы узнать больше об использовании Windows PowerShell в Active Directory, обратитесь к разделу [Windows PowerShell Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=624314) . 

