---
title: Управление Skype для бизнеса Online с помощью PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: 054c16e6-9fd1-4e85-a0e6-81788b8410ea
description: 'Сводка: использование PowerShell для Microsoft 365 для управления политиками Skype для бизнеса Online, политиками для отдельных пользователей и параметрами собраний.'
ms.openlocfilehash: 0701fdb8a0a1f588e1c113ad7050ed516638aebc
ms.sourcegitcommit: d9abb99b336170f07b8f3f6d00fac19ad2159d3a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/28/2020
ms.locfileid: "46502614"
---
# <a name="manage-skype-for-business-online-with-powershell"></a><span data-ttu-id="f20b8-103">Управление Skype для бизнеса Online с помощью PowerShell</span><span class="sxs-lookup"><span data-stu-id="f20b8-103">Manage Skype for Business Online with PowerShell</span></span>

<span data-ttu-id="f20b8-104">*Эта статья относится к Microsoft 365 корпоративный и Office 365 корпоративный.*</span><span class="sxs-lookup"><span data-stu-id="f20b8-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="f20b8-105">Одной из основных задач администратора Skype для бизнеса Online является Управление политиками.</span><span class="sxs-lookup"><span data-stu-id="f20b8-105">One of the primary tasks of any Skype for Business Online administrator is managing policies.</span></span> <span data-ttu-id="f20b8-106">Несмотря на то, что вы можете выполнить некоторые из этих задач в центре администрирования Microsoft 365, другие задачи выполняются значительно быстрее и проще в PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f20b8-106">Although you can accomplish some of these tasks in the Microsoft 365 admin center, other tasks are much quicker and easier in PowerShell.</span></span> 

## <a name="before-you-start"></a><span data-ttu-id="f20b8-107">Перед началом работы</span><span class="sxs-lookup"><span data-stu-id="f20b8-107">Before you start</span></span>

<span data-ttu-id="f20b8-108">Скачайте и установите [модуль соединителя Skype для бизнеса Online](https://www.microsoft.com/download/details.aspx?id=39366), а затем перезагрузите компьютер.</span><span class="sxs-lookup"><span data-stu-id="f20b8-108">Download and install the [Skype for Business Online Connector module](https://www.microsoft.com/download/details.aspx?id=39366), and then restart your computer.</span></span>


## <a name="connect-using-a-skype-for-business-online-administrator-account-name-and-password"></a><span data-ttu-id="f20b8-109">Подключение с помощью имени и пароля учетной записи администратора Skype для бизнеса Online</span><span class="sxs-lookup"><span data-stu-id="f20b8-109">Connect using a Skype for Business Online administrator account name and password</span></span>

1. <span data-ttu-id="f20b8-110">Откройте командную строку Windows PowerShell и выполните указанные команды:</span><span class="sxs-lookup"><span data-stu-id="f20b8-110">Open a Windows PowerShell command prompt and run the following commands:</span></span> 
    
   ```powershell
   Import-Module SkypeOnlineConnector
   $userCredential = Get-Credential
   $sfbSession = New-CsOnlineSession -Credential $userCredential
   Import-PSSession $sfbSession
   ```

2. <span data-ttu-id="f20b8-111">В диалоговом окне **запрос учетных данных Windows PowerShell** введите имя и пароль учетной записи администратора Skype для бизнеса Online, а затем нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="f20b8-111">In the **Windows PowerShell Credential Request** dialog box, type your Skype for Business Online administrator account name and password, and then click **OK**.</span></span>


## <a name="connect-using-a-skype-for-business-online-administrator-account-with-multi-factor-authentication"></a><span data-ttu-id="f20b8-112">Подключение с помощью учетной записи администратора Skype для бизнеса Online с многофакторной проверкой подлинности</span><span class="sxs-lookup"><span data-stu-id="f20b8-112">Connect using a Skype for Business Online administrator account with multi-factor authentication</span></span>

1. <span data-ttu-id="f20b8-113">Откройте командную строку Windows PowerShell и выполните указанные команды:</span><span class="sxs-lookup"><span data-stu-id="f20b8-113">Open a Windows PowerShell command prompt and run the following commands:</span></span>

   ```powershell
   Import-Module SkypeOnlineConnector
   $sfbSession = New-CsOnlineSession
   Import-PSSession $sfbSession
   ```

2. <span data-ttu-id="f20b8-114">Когда появится команда **New-CsOnlineSession** , введите имя учетной записи администратора Skype для бизнеса Online.</span><span class="sxs-lookup"><span data-stu-id="f20b8-114">When prompted by the **New-CsOnlineSession** command, enter your Skype for Business Online administrator account name.</span></span>

3. <span data-ttu-id="f20b8-115">В диалоговом окне **Вход в учетную запись** введите пароль администратора Skype для бизнеса Online и нажмите кнопку **войти**.</span><span class="sxs-lookup"><span data-stu-id="f20b8-115">In the **Sign in to your account** dialog box, type your Skype for Business Online administrator password, and then click **Sign in**.</span></span>

4. <span data-ttu-id="f20b8-116">Следуйте инструкциям в диалоговом окне **Вход в учетную запись** , чтобы предоставить дополнительные сведения о проверке подлинности, например код подтверждения, и нажмите кнопку **проверить**.</span><span class="sxs-lookup"><span data-stu-id="f20b8-116">Follow the instructions in the **Sign in to your account** dialog box to provide additional authentication information, such as a verification code, and then click **Verify**.</span></span>

<span data-ttu-id="f20b8-117">Дополнительную информацию см. в следующих статьях:</span><span class="sxs-lookup"><span data-stu-id="f20b8-117">For more information, see the following topics:</span></span>
  
- [<span data-ttu-id="f20b8-118">Управление политиками Skype для бизнеса Online с помощью PowerShell</span><span class="sxs-lookup"><span data-stu-id="f20b8-118">Manage Skype for Business Online policies with PowerShell</span></span>](manage-skype-for-business-online-policies-with-office-365-powershell.md)
    
- [<span data-ttu-id="f20b8-119">Назначение политик Skype для бизнеса Online для отдельных пользователей с помощью PowerShell</span><span class="sxs-lookup"><span data-stu-id="f20b8-119">Assign per-user Skype for Business Online policies with PowerShell</span></span>](assign-per-user-skype-for-business-online-policies-with-office-365-powershell.md)
    
## <a name="see-also"></a><span data-ttu-id="f20b8-120">См. также</span><span class="sxs-lookup"><span data-stu-id="f20b8-120">See also</span></span>

[<span data-ttu-id="f20b8-121">Управление Microsoft 365 с помощью PowerShell</span><span class="sxs-lookup"><span data-stu-id="f20b8-121">Manage Microsoft 365 with PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="f20b8-122">Начало работы с PowerShell для Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="f20b8-122">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-office-365-powershell.md)

[<span data-ttu-id="f20b8-123">Справочные материалы по командлетам PowerShell в Skype для бизнеса</span><span class="sxs-lookup"><span data-stu-id="f20b8-123">Skype for Business PowerShell cmdlet references</span></span>](https://docs.microsoft.com/powershell/module/skype/?view=skype-ps)

