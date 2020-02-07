---
title: Управление учетными записями и лицензиями пользователей с помощью Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/06/2019
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
description: Сводка. Узнайте, как управлять учетными записями пользователей, лицензиями и группами с помощью Office 365 PowerShell.
ms.openlocfilehash: e43272196556bcfb09fb7a41a5b2cd40e2056928
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/07/2020
ms.locfileid: "41841316"
---
# <a name="manage-user-accounts-licenses-and-groups-with-office-365-powershell"></a><span data-ttu-id="cbd9d-103">Управление учетными записями пользователей, лицензиями и группами с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="cbd9d-103">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>

<span data-ttu-id="cbd9d-104">Одной из основных задач администратора Office 365 является управление учетными записями пользователей, лицензиями и группами.</span><span class="sxs-lookup"><span data-stu-id="cbd9d-104">One of the primary tasks of any Office 365 administrator is managing user accounts, licenses, and group.</span></span> <span data-ttu-id="cbd9d-105">Несмотря на то, что вы можете выполнить большинство аспектов этих задач в центре администрирования Microsoft 365, другие задачи выполняются значительно быстрее и проще с помощью PowerShell для Office 365.</span><span class="sxs-lookup"><span data-stu-id="cbd9d-105">Although you can accomplish most aspects of these tasks in the Microsoft 365 admin center, other tasks are much quicker and easier with Office 365 PowerShell.</span></span> 

<span data-ttu-id="cbd9d-106">Более подробную информацию можно узнать в следующих статьях.</span><span class="sxs-lookup"><span data-stu-id="cbd9d-106">For more information, see these topics.</span></span>

## <a name="user-accounts"></a><span data-ttu-id="cbd9d-107">Учетные записи пользователей</span><span class="sxs-lookup"><span data-stu-id="cbd9d-107">User accounts</span></span>

- [<span data-ttu-id="cbd9d-108">Создание учетных записей пользователей</span><span class="sxs-lookup"><span data-stu-id="cbd9d-108">Create user accounts</span></span>](create-user-accounts-with-office-365-powershell.md)
- [<span data-ttu-id="cbd9d-109">Просмотр учетных записей пользователей</span><span class="sxs-lookup"><span data-stu-id="cbd9d-109">View user accounts</span></span>](view-user-accounts-with-office-365-powershell.md)
- [<span data-ttu-id="cbd9d-110">Настройка свойств учетной записи пользователя</span><span class="sxs-lookup"><span data-stu-id="cbd9d-110">Configure user account properties</span></span>](configure-user-account-properties-with-office-365-powershell.md)
- [<span data-ttu-id="cbd9d-111">Назначение ролей учетным записям пользователей</span><span class="sxs-lookup"><span data-stu-id="cbd9d-111">Assign roles to user accounts</span></span>](assign-roles-to-user-accounts-with-office-365-powershell.md)
- [<span data-ttu-id="cbd9d-112">Удаление и восстановление учетных записей пользователей</span><span class="sxs-lookup"><span data-stu-id="cbd9d-112">Delete and restore user accounts</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
- [<span data-ttu-id="cbd9d-113">Блокировка учетных записей пользователей</span><span class="sxs-lookup"><span data-stu-id="cbd9d-113">Block user accounts</span></span>](block-user-accounts-with-office-365-powershell.md)

## <a name="licenses-and-services"></a><span data-ttu-id="cbd9d-114">Лицензии и службы</span><span class="sxs-lookup"><span data-stu-id="cbd9d-114">Licenses and services</span></span>
- [<span data-ttu-id="cbd9d-115">Просмотр лицензий и служб</span><span class="sxs-lookup"><span data-stu-id="cbd9d-115">View licenses and services</span></span>](view-licenses-and-services-with-office-365-powershell.md)
- [<span data-ttu-id="cbd9d-116">Просмотр лицензированных и нелицензированных пользователей</span><span class="sxs-lookup"><span data-stu-id="cbd9d-116">View licensed and unlicensed users</span></span>](view-licensed-and-unlicensed-users-with-office-365-powershell.md)
- [<span data-ttu-id="cbd9d-117">Назначение лицензий учетным записям пользователей</span><span class="sxs-lookup"><span data-stu-id="cbd9d-117">Assign licenses to user accounts</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
- [<span data-ttu-id="cbd9d-118">Просмотр сведений о лицензии и службе учетной записи</span><span class="sxs-lookup"><span data-stu-id="cbd9d-118">View account license and service details</span></span>](view-account-license-and-service-details-with-office-365-powershell.md)
- [<span data-ttu-id="cbd9d-119">Отключение доступа к службам</span><span class="sxs-lookup"><span data-stu-id="cbd9d-119">Disable access to services</span></span>](disable-access-to-services-with-office-365-powershell.md)
  - [<span data-ttu-id="cbd9d-120">Отключение доступа к Sway</span><span class="sxs-lookup"><span data-stu-id="cbd9d-120">Disable access to Sway</span></span>](disable-access-to-sway-with-office-365-powershell.md)
  - [<span data-ttu-id="cbd9d-121">Отключение доступа к службам во время назначения лицензий</span><span class="sxs-lookup"><span data-stu-id="cbd9d-121">Disable access to services while assigning user licenses</span></span>](disable-access-to-services-while-assigning-user-licenses.md)
- [<span data-ttu-id="cbd9d-122">Удаление лицензий из учетных записей пользователей</span><span class="sxs-lookup"><span data-stu-id="cbd9d-122">Remove licenses from user accounts</span></span>](remove-licenses-from-user-accounts-with-office-365-powershell.md)

## <a name="groups"></a><span data-ttu-id="cbd9d-123">Группы</span><span class="sxs-lookup"><span data-stu-id="cbd9d-123">Groups</span></span>
- [<span data-ttu-id="cbd9d-124">Управление участием в группах</span><span class="sxs-lookup"><span data-stu-id="cbd9d-124">Maintain group membership</span></span>](maintain-group-membership-with-office-365-powershell.md)
- [<span data-ttu-id="cbd9d-125">Управление группами Office 365</span><span class="sxs-lookup"><span data-stu-id="cbd9d-125">Manage Office 365 groups</span></span>](manage-office-365-groups-with-powershell.md)

