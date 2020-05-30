---
title: Управление Skype для бизнеса Online с помощью Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/28/2018
audience: ITPro
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: 054c16e6-9fd1-4e85-a0e6-81788b8410ea
description: 'Сводка: в этой статье рассказывается, как использовать PowerShell в Office 365 для управления параметрами политик, индивидуальных политик для пользователей и собраний в Skype для бизнеса Online.'
ms.openlocfilehash: f1a5df3802d43755e81465743b81c5fbb9fff7e0
ms.sourcegitcommit: 6c7cc6aca8713e280ae6ff51226dde9db4497401
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2020
ms.locfileid: "44415941"
---
# <a name="manage-skype-for-business-online-with-office-365-powershell"></a><span data-ttu-id="85418-103">Управление Skype для бизнеса Online с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="85418-103">Manage Skype for Business Online with Office 365 PowerShell</span></span>

<span data-ttu-id="85418-104">Одной из основных задач администратора Skype для бизнеса Online является Управление политиками.</span><span class="sxs-lookup"><span data-stu-id="85418-104">One of the primary tasks of any Skype for Business Online administrator is managing policies.</span></span> <span data-ttu-id="85418-105">Вы можете выполнить некоторые из указанных ниже задач в Центре администрирования Microsoft 365, но остальные задачи гораздо быстрее и проще выполнить с помощью PowerShell в Office 365.</span><span class="sxs-lookup"><span data-stu-id="85418-105">Although you can accomplish some of these tasks in the Microsoft 365 admin center, other tasks are much quicker and easier in Office 365 PowerShell.</span></span> 

## <a name="before-you-start"></a><span data-ttu-id="85418-106">Перед началом работы</span><span class="sxs-lookup"><span data-stu-id="85418-106">Before you start</span></span>

<span data-ttu-id="85418-107">Скачайте и установите [модуль соединителя Skype для бизнеса Online](https://www.microsoft.com/download/details.aspx?id=39366), а затем перезагрузите компьютер.</span><span class="sxs-lookup"><span data-stu-id="85418-107">Download and install the [Skype for Business Online Connector module](https://www.microsoft.com/download/details.aspx?id=39366), and then restart your computer.</span></span>


## <a name="connect-using-a-skype-for-business-online-administrator-account-name-and-password"></a><span data-ttu-id="85418-108">Подключение с помощью имени и пароля учетной записи администратора Skype для бизнеса Online</span><span class="sxs-lookup"><span data-stu-id="85418-108">Connect using a Skype for Business Online administrator account name and password</span></span>

1. <span data-ttu-id="85418-109">Откройте командную строку Windows PowerShell и выполните указанные команды:</span><span class="sxs-lookup"><span data-stu-id="85418-109">Open a Windows PowerShell command prompt and run the following commands:</span></span> 
    
  ```powershell
  Import-Module SkypeOnlineConnector
  $userCredential = Get-Credential
  $sfbSession = New-CsOnlineSession -Credential $userCredential
  Import-PSSession $sfbSession
  ```

2. <span data-ttu-id="85418-110">В диалоговом окне **запрос учетных данных Windows PowerShell** введите имя и пароль учетной записи администратора Skype для бизнеса Online, а затем нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="85418-110">In the **Windows PowerShell Credential Request** dialog box, type your Skype for Business Online administrator account name and password, and then click **OK**.</span></span>


## <a name="connect-using-a-skype-for-business-online-administrator-account-with-multi-factor-authentication"></a><span data-ttu-id="85418-111">Подключение с помощью учетной записи администратора Skype для бизнеса Online с многофакторной проверкой подлинности</span><span class="sxs-lookup"><span data-stu-id="85418-111">Connect using a Skype for Business Online administrator account with multi-factor authentication</span></span>

1. <span data-ttu-id="85418-112">Откройте командную строку Windows PowerShell и выполните указанные команды:</span><span class="sxs-lookup"><span data-stu-id="85418-112">Open a Windows PowerShell command prompt and run the following commands:</span></span>

  ```powershell
  Import-Module SkypeOnlineConnector
  $sfbSession = New-CsOnlineSession
  Import-PSSession $sfbSession
  ```

2. <span data-ttu-id="85418-113">Когда появится команда **New-CsOnlineSession** , введите имя учетной записи администратора Skype для бизнеса Online.</span><span class="sxs-lookup"><span data-stu-id="85418-113">When prompted by the **New-CsOnlineSession** command, enter your Skype for Business Online administrator account name.</span></span>

3. <span data-ttu-id="85418-114">В диалоговом окне **Вход в учетную запись** введите пароль администратора Skype для бизнеса Online и нажмите кнопку **войти**.</span><span class="sxs-lookup"><span data-stu-id="85418-114">In the **Sign in to your account** dialog box, type your Skype for Business Online administrator password, and then click **Sign in**.</span></span>

4. <span data-ttu-id="85418-115">Следуйте инструкциям в диалоговом окне **Вход в учетную запись** , чтобы предоставить дополнительные сведения о проверке подлинности, например код подтверждения, и нажмите кнопку **проверить**.</span><span class="sxs-lookup"><span data-stu-id="85418-115">Follow the instructions in the **Sign in to your account** dialog box to provide additional authentication information, such as a verification code, and then click **Verify**.</span></span>

<span data-ttu-id="85418-116">Дополнительную информацию см. в следующих статьях:</span><span class="sxs-lookup"><span data-stu-id="85418-116">For more information, see the following topics:</span></span>
  
- [<span data-ttu-id="85418-117">Управление политиками Skype для бизнеса Online с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="85418-117">Manage Skype for Business Online policies with Office 365 PowerShell</span></span>](manage-skype-for-business-online-policies-with-office-365-powershell.md)
    
- [<span data-ttu-id="85418-118">Назначение индивидуальных политик для Skype для бизнеса Online с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="85418-118">Assign per-user Skype for Business Online policies with Office 365 PowerShell</span></span>](assign-per-user-skype-for-business-online-policies-with-office-365-powershell.md)
    
## <a name="see-also"></a><span data-ttu-id="85418-119">См. также</span><span class="sxs-lookup"><span data-stu-id="85418-119">See also</span></span>

[<span data-ttu-id="85418-120">Управление Office 365 с помощью PowerShell Office 365</span><span class="sxs-lookup"><span data-stu-id="85418-120">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="85418-121">Начало работы с Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="85418-121">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

[<span data-ttu-id="85418-122">Справочные материалы по командлетам PowerShell в Skype для бизнеса</span><span class="sxs-lookup"><span data-stu-id="85418-122">Skype for Business PowerShell cmdlet references</span></span>](https://docs.microsoft.com/powershell/module/skype/?view=skype-ps)

