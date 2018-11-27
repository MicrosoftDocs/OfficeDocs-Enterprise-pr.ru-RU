---
title: Подготовка без поддержки маршрутизации домена для синхронизации службы каталогов
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: article
f1_keywords:
- O365E_SetupDirSyncLocalDir
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: e7968303-c234-46c4-b8b0-b5c93c6d57a7
description: Узнайте, что делать, если у вас не routale домена, связанного с локальными пользователями, перед выполнением синхронизации с Office 365.
ms.openlocfilehash: 9ec96c34e1dc4a6c755ea97fce3f5f2a5ba21bb3
ms.sourcegitcommit: 9c493c4e18e83491d106c5e9bab55d1a89298879
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2018
ms.locfileid: "26674443"
---
# <a name="prepare-a-non-routable-domain-for-directory-synchronization"></a>Подготовка без поддержки маршрутизации домена для синхронизации службы каталогов
При синхронизации локального каталога с Office 365 необходимо иметь подтвержденным доменом в Azure Active Directory. Синхронизированы только участника-пользователя имена (UPN), связанные с локального домена. Тем не менее, будет синхронизирован любое имя участника-пользователя, который содержит без поддержки маршрутизации домена, например .local (например, billa@contoso.local), чтобы. onmicrosoft.com домена (например, billa@contoso.onmicrosoft.com). 

При использовании .local домена для учетных записей пользователей в Active Directory рекомендуется изменять их для использования подтвержденным доменом (например, billa@contoso.com), чтобы должным образом синхронизации с вашего домена Office 365.
  
## <a name="what-if-i-only-have-a-local-on-premises-domain"></a>Что делать, если только у локального домена .local?

Самые последние средство, которое можно использовать для синхронизации Active Directory для Azure Active Directory называется подключить Azure AD. Для получения дополнительных сведений см [Интеграция вашей локальной удостоверения с помощью Azure Active Directory](https://docs.microsoft.com/azure/architecture/reference-architectures/identity/azure-ad).
  
Подключение Azure AD синхронизирует пользователей имени участника-пользователя и пароль, чтобы пользователи могут входить с один набор учетных данных они используют для локальной. Тем не менее Azure AD подключить синхронизирует только пользователям доменов, которые проверяются с Office 365. Это означает, что также проверки домена с Azure Active Directory так как Office 365 удостоверения управляют Azure Active Directory. Другими словами домен должен быть допустимый домен Интернета (например, .com, .org, .net, .us, и т.д.). Если в вашей внутренней Active Directory используется только без поддержки маршрутизации домена (например, .local), это не может совпадать возможно с подтвержденным доменом в Office 365. Эту проблему можно устранить с помощью любого из изменения основного домена в локальный Active Directory или путем добавления одного или нескольких суффиксов UPN.
  
### <a name="change-your-primary-domain"></a>**Изменение основного домена**

Изменение основного домена к домену, в которые проверки в Office 365, например, contoso.com. Каждый пользователь, который имеет contoso.local домена обновляется на contoso.com. Сведения содержатся в разделе [How Domain Rename Works](https://go.microsoft.com/fwlink/p/?LinkId=624174). Это сложный процесс, но и более простое решение — [Добавьте имя участника-пользователя суффиксов и обновите их пользователям](prepare-a-non-routable-domain-for-directory-synchronization.md#bk_register), как показано в следующем разделе.
  
### <a name="add-upn-suffixes-and-update-your-users-to-them"></a>**Добавление суффиксов UPN и обновить пользователей к ним**

Вы можете решить проблему .local путем регистрации нового суффикса имени участника-пользователя или суффиксы в Active Directory в соответствии с домена (или доменов), проверенных в Office 365. После регистрации нового суффикса обновление имен участников-пользователей для замены .local новое доменное имя, например, чтобы учетная запись пользователя выглядит как billa@contoso.com пользователя.
  
После обновления UPN для использования с подтвержденным доменом, вы готовы для синхронизации локальной Active Directory с Office 365.
  
 **Шаг 1: Добавление нового суффикса имени участника-пользователя**
  
1. На сервере, на котором выполняется доменных служб Active Directory (AD DS) на, в диспетчере серверов выберите **средства** \> **Active Directory — домены и доверие**.
    
    **Или, если у вас нет Windows Server 2012**
    
    Нажмите **клавиши Windows + R** , чтобы открыть диалоговое окно **запуска** , а затем введите в Domain.msc и нажмите кнопку **ОК**.
    
    ![Выберите Active Directory — домены и доверие.](media/46b6e007-9741-44af-8517-6f682e0ac974.png)
  
2. В окне **Active Directory — домены и доверие** щелкните правой кнопкой мыши **Active Directory — домены и доверие**и выберите пункт **Свойства**.
    
    ![Щелкните правой кнопкой мыши ActiveDirectory — домены и доверие и выберите команду Свойства](media/39d20812-ffb5-4ba9-8d7b-477377ac360d.png)
  
3. На вкладке **UPN-суффиксы** **UPN-суффиксы альтернатива** введите в поле, нового суффикса имени участника-пользователя или суффиксы и нажмите кнопку **Добавить** \> **Применить**.
    
    ![Добавление нового суффикса имени участника-пользователя](media/a4aaf919-7adf-469a-b93f-83ef284c0915.PNG)
  
    После завершения добавления суффиксов, нажмите кнопку **ОК** . 
    
 **Шаг 2: Изменение суффикса имени участника-пользователя для существующих пользователей**
  
1. На сервере, на котором выполняется доменных служб Active Directory (AD DS) на, в диспетчере серверов выберите **средства** \> **Active Directory Active Directory — пользователи и компьютеры**.
    
    **Или, если у вас нет Windows Server 2012**
    
    Нажмите **клавиши Windows + R** , чтобы открыть диалоговое окно **запуска** , а затем введите в Dsa.msc, а затем нажмите **кнопку ОК**
    
2. Выберите пользователя, щелкните правой кнопкой мыши и выберите пункт **Свойства**.
    
3. На вкладке **учетная запись** в раскрывающемся списке суффикса имени участника-пользователя выберите новый суффикса имени участника-пользователя и нажмите кнопку **ОК**.
    
    ![Добавление нового суффикса имени участника-пользователя для пользователя](media/54876751-49f0-48cc-b864-2623c4835563.png)
  
4. Выполните эти действия для каждого пользователя.
    
    В другом варианте массового обновления суффиксов UPN [также можно использовать Windows PowerShell для изменения суффикса имени участника-пользователя для всех пользователей](prepare-a-non-routable-domain-for-directory-synchronization.md#BK_Posh).
    
### <a name="you-can-also-use-windows-powershell-to-change-the-upn-suffix-for-all-users"></a>**Также можно использовать Windows PowerShell для изменения суффикса имени участника-пользователя для всех пользователей**

Если у вас есть много обновлений, проще использовать Windows PowerShell. В следующем примере используется командлет [Get-ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624312) и [Set-ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624313) для изменения всех суффиксов contoso.local на contoso.com. 

Выполните следующие команды Windows PowerShell для обновления всех суффиксов contoso.local contoso.com.
    
  ```
  $LocalUsers = Get-ADUser -Filter {UserPrincipalName -like '*contoso.local'} -Properties userPrincipalName -ResultSetSize $null
  ```

  ```
  $LocalUsers | foreach {$newUpn = $_.UserPrincipalName.Replace("contoso.local","contoso.com"); $_ | Set-ADUser -UserPrincipalName $newUpn}
  ```
В разделе [модуль Active Directory Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=624314) для получения дополнительных сведений об использовании Windows PowerShell в службе каталогов Active Directory. 

