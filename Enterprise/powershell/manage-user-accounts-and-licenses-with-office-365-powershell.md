---
title: Управление учетными записями пользователей, лицензиями и группами Microsoft 365 с помощью PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: ITPro
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: 26b9ff81-93b0-4251-beaf-3c9f1d7c80c8
description: Сводка. сведения о том, как управлять учетными записями пользователей, лицензиями и группами Microsoft 365 с помощью PowerShell.
ms.openlocfilehash: 26da0d13ecc9c14be4abe059943bd91d88126f1e
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230415"
---
# <a name="manage-microsoft-365-user-accounts-licenses-and-groups-with-powershell"></a><span data-ttu-id="eb54f-103">Управление учетными записями пользователей, лицензиями и группами Microsoft 365 с помощью PowerShell</span><span class="sxs-lookup"><span data-stu-id="eb54f-103">Manage Microsoft 365 user accounts, licenses, and groups with PowerShell</span></span>

<span data-ttu-id="eb54f-104">*Эта статья относится как к Microsoft 365 Enterprise, так и к Office 365 корпоративный.*</span><span class="sxs-lookup"><span data-stu-id="eb54f-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="eb54f-105">Одной из основных задач администратора Microsoft 365 является управление учетными записями пользователей, лицензиями и группами.</span><span class="sxs-lookup"><span data-stu-id="eb54f-105">One of the primary tasks of any Microsoft 365 administrator is managing user accounts, licenses, and groups.</span></span> <span data-ttu-id="eb54f-106">Несмотря на то, что вы можете выполнить большинство аспектов этих задач в центре администрирования Microsoft 365, другие задачи выполняются значительно быстрее и проще с помощью PowerShell.</span><span class="sxs-lookup"><span data-stu-id="eb54f-106">Although you can accomplish most aspects of these tasks in the Microsoft 365 admin center, other tasks are much quicker and easier with PowerShell.</span></span> 

<span data-ttu-id="eb54f-107">Более подробную информацию можно узнать в следующих статьях.</span><span class="sxs-lookup"><span data-stu-id="eb54f-107">For more information, see these topics.</span></span>

## <a name="user-accounts"></a><span data-ttu-id="eb54f-108">Учетные записи пользователей</span><span class="sxs-lookup"><span data-stu-id="eb54f-108">User accounts</span></span>

- [<span data-ttu-id="eb54f-109">Создание учетных записей пользователей</span><span class="sxs-lookup"><span data-stu-id="eb54f-109">Create user accounts</span></span>](create-user-accounts-with-office-365-powershell.md)
- [<span data-ttu-id="eb54f-110">Просмотр учетных записей пользователей</span><span class="sxs-lookup"><span data-stu-id="eb54f-110">View user accounts</span></span>](view-user-accounts-with-office-365-powershell.md)
- [<span data-ttu-id="eb54f-111">Настройка свойств учетной записи пользователя</span><span class="sxs-lookup"><span data-stu-id="eb54f-111">Configure user account properties</span></span>](configure-user-account-properties-with-office-365-powershell.md)
- [<span data-ttu-id="eb54f-112">Назначение ролей учетным записям пользователей</span><span class="sxs-lookup"><span data-stu-id="eb54f-112">Assign roles to user accounts</span></span>](assign-roles-to-user-accounts-with-office-365-powershell.md)
- [<span data-ttu-id="eb54f-113">Удаление и восстановление учетных записей пользователей</span><span class="sxs-lookup"><span data-stu-id="eb54f-113">Delete and restore user accounts</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
- [<span data-ttu-id="eb54f-114">Блокировка учетных записей пользователей</span><span class="sxs-lookup"><span data-stu-id="eb54f-114">Block user accounts</span></span>](block-user-accounts-with-office-365-powershell.md)

## <a name="licenses-and-services"></a><span data-ttu-id="eb54f-115">Лицензии и службы</span><span class="sxs-lookup"><span data-stu-id="eb54f-115">Licenses and services</span></span>
- [<span data-ttu-id="eb54f-116">Просмотр лицензий и служб</span><span class="sxs-lookup"><span data-stu-id="eb54f-116">View licenses and services</span></span>](view-licenses-and-services-with-office-365-powershell.md)
- [<span data-ttu-id="eb54f-117">Просмотр лицензированных и нелицензированных пользователей</span><span class="sxs-lookup"><span data-stu-id="eb54f-117">View licensed and unlicensed users</span></span>](view-licensed-and-unlicensed-users-with-office-365-powershell.md)
- [<span data-ttu-id="eb54f-118">Назначение лицензий учетным записям пользователей</span><span class="sxs-lookup"><span data-stu-id="eb54f-118">Assign licenses to user accounts</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
- [<span data-ttu-id="eb54f-119">Просмотр сведений о лицензии и службе учетной записи</span><span class="sxs-lookup"><span data-stu-id="eb54f-119">View account license and service details</span></span>](view-account-license-and-service-details-with-office-365-powershell.md)
- [<span data-ttu-id="eb54f-120">Отключение доступа к службам</span><span class="sxs-lookup"><span data-stu-id="eb54f-120">Disable access to services</span></span>](disable-access-to-services-with-office-365-powershell.md)
  - [<span data-ttu-id="eb54f-121">Отключение доступа к Sway</span><span class="sxs-lookup"><span data-stu-id="eb54f-121">Disable access to Sway</span></span>](disable-access-to-sway-with-office-365-powershell.md)
  - [<span data-ttu-id="eb54f-122">Отключение доступа к службам во время назначения лицензий</span><span class="sxs-lookup"><span data-stu-id="eb54f-122">Disable access to services while assigning user licenses</span></span>](disable-access-to-services-while-assigning-user-licenses.md)
- [<span data-ttu-id="eb54f-123">Удаление лицензий из учетных записей пользователей</span><span class="sxs-lookup"><span data-stu-id="eb54f-123">Remove licenses from user accounts</span></span>](remove-licenses-from-user-accounts-with-office-365-powershell.md)

## <a name="groups"></a><span data-ttu-id="eb54f-124">Группы</span><span class="sxs-lookup"><span data-stu-id="eb54f-124">Groups</span></span>
- [<span data-ttu-id="eb54f-125">Управление участием в группах</span><span class="sxs-lookup"><span data-stu-id="eb54f-125">Maintain group membership</span></span>](maintain-group-membership-with-office-365-powershell.md)
- [<span data-ttu-id="eb54f-126">Управление группами Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="eb54f-126">Manage Microsoft 365 groups</span></span>](manage-office-365-groups-with-powershell.md)

