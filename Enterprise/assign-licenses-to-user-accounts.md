---
title: Назначение лицензий на Office 365 для учетных записей пользователей
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
f1_keywords:
- O365p_AddUsersWithDirSync
- O365M_AddUsersWithDirSync
- O365E_HRCSetupAADConnectAboutLM617031
- O365E_AddUsersWithDirSync
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOP150
- MOE150
- MBS150
ms.assetid: 01920974-9e6f-4331-a370-13aea4e82b3e
description: В этой статье описано, как назначать лицензии на Office 365 для учетных записей пользователей по отдельности или в зависимости от принадлежности к группе.
ms.openlocfilehash: 0f258ef9240239ebdfa695e8c5b214484cfb4db1
ms.sourcegitcommit: 36e760407a1f4b18bc108134628ed9a8d3e35a8a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/17/2019
ms.locfileid: "34164604"
---
# <a name="assign-office-365-licenses-to-user-accounts"></a><span data-ttu-id="128fb-103">Назначение лицензий на Office 365 для учетных записей пользователей</span><span class="sxs-lookup"><span data-stu-id="128fb-103">Assign Office 365 licenses to user accounts</span></span>

<span data-ttu-id="128fb-104">Для модели удостоверений, которая используется только в облаке, вы можете назначить лицензии Office 365 для учетных записей пользователей при их создании, в зависимости от того, как они создаются.</span><span class="sxs-lookup"><span data-stu-id="128fb-104">For the cloud-only identity model, you can assign Office 365 licenses to user accounts as they are created, depending on how you create them.</span></span>

<span data-ttu-id="128fb-105">Для модели гибридной идентификации при первой синхронизации учетных записей пользователей доменных служб Active Directory (AD DS) им не назначается автоматическая лицензия на Office 365.</span><span class="sxs-lookup"><span data-stu-id="128fb-105">For the hybrid identity model, when Active Directory Domain Services (AD DS) user accounts are synchronized for the first time, they are not automatically assigned an Office 365 license.</span></span>

<span data-ttu-id="128fb-106">В любом случае необходимо назначить лицензии учетным записям пользователей, чтобы пользователи могли получать доступ к службам Office 365, таким как электронная почта и Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="128fb-106">In either case, you must assign a license to user accounts so your users can access Office 365 services, such as email and Microsoft Teams.</span></span>

<span data-ttu-id="128fb-107">Вы можете назначать лицензии учетным записям пользователей по отдельности или автоматически с помощью членства в группе.</span><span class="sxs-lookup"><span data-stu-id="128fb-107">You can assign licenses to user accounts either individually or automatically through group membership.</span></span>

<span data-ttu-id="128fb-108">Чтобы назначить лицензии Office 365 отдельным учетным записям пользователей, можно использовать:</span><span class="sxs-lookup"><span data-stu-id="128fb-108">To assign Office 365 licenses to individual user accounts, you can use:</span></span>

- [<span data-ttu-id="128fb-109">Центр администрирования Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="128fb-109">The Microsoft 365 admin center</span></span>](https://docs.microsoft.com/office365/admin/subscriptions-and-billing/assign-licenses-to-users)
- [<span data-ttu-id="128fb-110">Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="128fb-110">Office 365 PowerShell</span></span>](https://docs.microsoft.com/office365/enterprise/powershell/assign-licenses-to-user-accounts-with-office-365-powershell)

<span data-ttu-id="128fb-111">Для автоматического назначения лицензий просмотрите раздел [Лицензирование на основе групп в Azure AD](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-licensing-whatis-azure-portal).</span><span class="sxs-lookup"><span data-stu-id="128fb-111">For automatic license assignment, see [group-based licensing in Azure AD](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-licensing-whatis-azure-portal).</span></span>

## <a name="next-steps"></a><span data-ttu-id="128fb-112">Дальнейшие действия</span><span class="sxs-lookup"><span data-stu-id="128fb-112">Next steps</span></span>

<span data-ttu-id="128fb-113">С полным набором учетных записей пользователей, которым были назначены лицензии, вы можете:</span><span class="sxs-lookup"><span data-stu-id="128fb-113">With the full set of user accounts that have been assigned licenses, you are now ready to:</span></span>

- [<span data-ttu-id="128fb-114">Развертывание клиентского программного обеспечения, например Office 365 профессиональный плюс</span><span class="sxs-lookup"><span data-stu-id="128fb-114">Deploy client software, such as Office 365 ProPlus</span></span>](https://docs.microsoft.com/DeployOffice/deployment-guide-for-office-365-proplus)
- [<span data-ttu-id="128fb-115">Настройка управления мобильными устройствами</span><span class="sxs-lookup"><span data-stu-id="128fb-115">Configure mobile device management</span></span>](https://support.office.com/article/set-up-mobile-device-management-mdm-in-office-365-dd892318-bc44-4eb1-af00-9db5430be3cd)
- [<span data-ttu-id="128fb-116">Настройка служб и приложений</span><span class="sxs-lookup"><span data-stu-id="128fb-116">Configure services and applications</span></span>](configure-services-and-applications.md)
