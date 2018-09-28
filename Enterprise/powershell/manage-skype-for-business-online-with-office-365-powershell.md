---
title: Управление Skype для бизнеса Online с помощью Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 09/13/2018
ms.audience: ITPro
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: 054c16e6-9fd1-4e85-a0e6-81788b8410ea
description: 'Сводка: в этой статье рассказывается, как использовать PowerShell в Office 365 для управления параметрами политик, индивидуальных политик для пользователей и собраний в Skype для бизнеса Online.'
ms.openlocfilehash: a91803316972337aa31e2b979f841ac1cfbe8566
ms.sourcegitcommit: 053db5479f93478a65d4c36ffe44c6a7bcb60e3c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/13/2018
ms.locfileid: "23965196"
---
# <a name="manage-skype-for-business-online-with-office-365-powershell"></a><span data-ttu-id="be548-103">Управление Skype для бизнеса Online с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="be548-103">Manage Skype for Business Online with Office 365 PowerShell</span></span>

 <span data-ttu-id="be548-104">**Сводка.** Управляйте политиками и настройками собраний Skype для бизнеса Online, используя PowerShell для Office 365.</span><span class="sxs-lookup"><span data-stu-id="be548-104">**Summary:** Use Office 365 PowerShell to manage Skype for Business Online policies, per-user policies, and meeting settings.</span></span>
  
<span data-ttu-id="be548-p101">Один из основных задач любой Скайп для бизнеса в Интернет администратор Управление политиками. Несмотря на то, что можно выполнить некоторые из этих задач в центре администрирования Office 365, другие задачи, намного быстрее и проще в Office 365 PowerShell.</span><span class="sxs-lookup"><span data-stu-id="be548-p101">One of the primary tasks of any Skype for Business Online administrator is managing policies. Although you can accomplish some of these tasks in the Office 365 Admin center, other tasks are much quicker and easier in Office 365 PowerShell.</span></span> 

## <a name="before-you-start"></a><span data-ttu-id="be548-107">Перед началом работы</span><span class="sxs-lookup"><span data-stu-id="be548-107">Before you start</span></span>

<span data-ttu-id="be548-108">Загрузить и установить [Скайп для модуля Business Online Connector](https://www.microsoft.com/en-us/download/details.aspx?id=39366)и при появлении соответствующего запроса перезагрузите компьютер.</span><span class="sxs-lookup"><span data-stu-id="be548-108">Download and install the [Skype for Business Online Connector module](https://www.microsoft.com/en-us/download/details.aspx?id=39366), and then restart your computer if prompted.</span></span>


## <a name="connect-using-a-skype-for-business-online-administrator-account-name-and-password"></a><span data-ttu-id="be548-109">Подключение через Скайп Business Online имя учетной записи администратора и пароля</span><span class="sxs-lookup"><span data-stu-id="be548-109">Connect using a Skype for Business Online administrator account name and password</span></span>

1. <span data-ttu-id="be548-110">Откройте командную строку Windows PowerShell и выполните указанные команды:</span><span class="sxs-lookup"><span data-stu-id="be548-110">Open a Windows PowerShell command prompt and run the following commands:</span></span> 
    
  ```
  Import-Module SkypeOnlineConnector
  $userCredential = Get-Credential
  $sfbSession = New-CsOnlineSession -Credential $userCredential
  Import-PSSession $sfbSession
  ```

2. <span data-ttu-id="be548-111">В диалоговом окне **Запрос учетных данных Windows PowerShell** введите вашей Скайп для бизнеса в Интернет имя учетной записи администратора и пароль и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="be548-111">In the **Windows PowerShell Credential Request** dialog box, type your Skype for Business Online administrator account name and password, and then click **OK**.</span></span>


## <a name="connect-using-a-skype-for-business-online-administrator-account-with-multifactor-authentication"></a><span data-ttu-id="be548-112">Подключение через Скайп для бизнеса в Интернет учетной записи администратора с многофакторной проверкой подлинности</span><span class="sxs-lookup"><span data-stu-id="be548-112">Connect using a Skype for Business Online administrator account with multifactor authentication</span></span>

1. <span data-ttu-id="be548-113">Откройте командную строку Windows PowerShell и выполните указанные команды:</span><span class="sxs-lookup"><span data-stu-id="be548-113">Open a Windows PowerShell command prompt and run the following commands:</span></span>

  ```
  Import-Module SkypeOnlineConnector
  $sfbSession = New-CsOnlineSession
  Import-PSSession $sfbSession
  ```

2. <span data-ttu-id="be548-114">При появлении запроса с помощью команды **New-CsOnlineSession** введите вашей Скайп для бизнеса в Интернет имя учетной записи администратора.</span><span class="sxs-lookup"><span data-stu-id="be548-114">When prompted by the **New-CsOnlineSession** command, enter your Skype for Business Online administrator account name.</span></span>

3. <span data-ttu-id="be548-115">В диалоговом окне **входа в свою учетную запись** введите ваше Скайп для бизнеса в Интернет пароль администратора и нажмите кнопку **Вход**.</span><span class="sxs-lookup"><span data-stu-id="be548-115">In the **Sign in to your account** dialog box, type your Skype for Business Online administrator password, and then click **Sign in**.</span></span>

4. <span data-ttu-id="be548-116">Следуйте инструкциям в диалоговом окне **входа в учетную запись** для обеспечения проверки подлинности на дополнительные сведения, такие как код подтверждения и нажмите кнопку **Проверить**.</span><span class="sxs-lookup"><span data-stu-id="be548-116">Follow the instructions in the **Sign in to your account** dialog box to provide additional authentication information, such as a verification code, and then click **Verify**.</span></span>

<span data-ttu-id="be548-117">Дополнительные сведения приведены в следующих разделах:</span><span class="sxs-lookup"><span data-stu-id="be548-117">For more information, see the following topics:</span></span>
  
- [<span data-ttu-id="be548-118">Управление политиками Skype для бизнеса Online с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="be548-118">Manage Skype for Business Online policies with Office 365 PowerShell</span></span>](manage-skype-for-business-online-policies-with-office-365-powershell.md)
    
- [<span data-ttu-id="be548-119">Назначение индивидуальных политик для Skype для бизнеса Online с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="be548-119">Assign per-user Skype for Business Online policies with Office 365 PowerShell</span></span>](assign-per-user-skype-for-business-online-policies-with-office-365-powershell.md)
    
## <a name="see-also"></a><span data-ttu-id="be548-120">См. также</span><span class="sxs-lookup"><span data-stu-id="be548-120">See also</span></span>

[<span data-ttu-id="be548-121">Управление Office 365 с помощью PowerShell Office 365</span><span class="sxs-lookup"><span data-stu-id="be548-121">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="be548-122">Начало работы с Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="be548-122">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

[<span data-ttu-id="be548-123">Скайп для ссылок на командлета PowerShell бизнеса</span><span class="sxs-lookup"><span data-stu-id="be548-123">Skype for Business PowerShell cmdlet references</span></span>](https://docs.microsoft.com/powershell/module/skype/?view=skype-ps)

