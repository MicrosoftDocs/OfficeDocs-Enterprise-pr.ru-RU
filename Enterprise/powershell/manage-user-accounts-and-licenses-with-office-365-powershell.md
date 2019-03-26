---
title: Управление учетными записями и лицензиями пользователей с помощью Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: 26b9ff81-93b0-4251-beaf-3c9f1d7c80c8
description: 'Сводка: в этой статье рассказывается о том, как управлять учетными записями и лицензиями пользователей с помощью PowerShell в Office 365.'
ms.openlocfilehash: 604f0e6926936473f4b8e13546cdf0d7d839c667
ms.sourcegitcommit: 4ef8e113fa20b539de1087422455fc26ff123d55
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "30573893"
---
# <a name="manage-user-accounts-and-licenses-with-office-365-powershell"></a><span data-ttu-id="0da66-103">Управление учетными записями и лицензиями пользователей с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="0da66-103">Manage user accounts and licenses with Office 365 PowerShell</span></span>

 <span data-ttu-id="0da66-104">**Сводка.** Узнайте, как управлять учетными записями и лицензиями пользователей с помощью PowerShell для Office 365.</span><span class="sxs-lookup"><span data-stu-id="0da66-104">**Summary:** Learn how to manage user accounts and licenses with Office 365 PowerShell.</span></span>
  
<span data-ttu-id="0da66-105">Одна из основных задач любого администратора Office 365 — управление учетными записями и лицензиями пользователей.</span><span class="sxs-lookup"><span data-stu-id="0da66-105">One of the primary tasks of any O365_W14_2nd administrator is managing user accounts and licenses.</span></span> <span data-ttu-id="0da66-106">Вы можете выполнить некоторые из указанных ниже задач в Центре администрирования Microsoft 365, но остальные задачи гораздо быстрее и проще выполнить с помощью PowerShell в Office 365.</span><span class="sxs-lookup"><span data-stu-id="0da66-106">One of the primary tasks of any Office 365 administrator is managing user accounts and licenses. Although you can accomplish some of these tasks in the Office 365 admin center, other tasks are much quicker and easier with Office 365 PowerShell. For more information, see the following topics:</span></span> <span data-ttu-id="0da66-107">Дополнительную информацию см. в следующих статьях:</span><span class="sxs-lookup"><span data-stu-id="0da66-107">For more information, see the following topics:</span></span>
  
- [<span data-ttu-id="0da66-108">Просмотр лицензий и служб с помощью PowerShell в Office 365</span><span class="sxs-lookup"><span data-stu-id="0da66-108">View licenses and services with Office 365 PowerShell</span></span>](view-licenses-and-services-with-office-365-powershell.md)
    
- [<span data-ttu-id="0da66-109">Отображение списков пользователей с лицензиями и пользователей без лицензий с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="0da66-109">View licensed and unlicensed users with Office 365 PowerShell</span></span>](view-licensed-and-unlicensed-users-with-office-365-powershell.md)
    
- [<span data-ttu-id="0da66-110">Назначение лицензий для учетных записей пользователей с помощью PowerShell в Office 365</span><span class="sxs-lookup"><span data-stu-id="0da66-110">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="0da66-111">Просмотр сведений о лицензии и службе учетной записи с помощью PowerShell в Office 365</span><span class="sxs-lookup"><span data-stu-id="0da66-111">View account license and service details with Office 365 PowerShell</span></span>](view-account-license-and-service-details-with-office-365-powershell.md)
    
- [<span data-ttu-id="0da66-112">Назначение ролей учетным записям пользователей с помощью PowerShell для Office 365</span><span class="sxs-lookup"><span data-stu-id="0da66-112">Assign roles to user accounts with Office 365 PowerShell</span></span>](assign-roles-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="0da66-113">Отключение доступа к службам с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="0da66-113">Disable access to services with Office 365 PowerShell</span></span>](disable-access-to-services-with-office-365-powershell.md)
    
- [<span data-ttu-id="0da66-114">Использование PowerShell в Office 365 для удаления лицензий из учетных записей пользователей</span><span class="sxs-lookup"><span data-stu-id="0da66-114">Remove licenses from user accounts with Office 365 PowerShell</span></span>](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="0da66-115">Блокировка учетных записей пользователей с помощью PowerShell в Office 365</span><span class="sxs-lookup"><span data-stu-id="0da66-115">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="0da66-116">Удаление и восстановление учетных записей пользователей с помощью PowerShell в Office 365</span><span class="sxs-lookup"><span data-stu-id="0da66-116">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="0da66-117">Создание учетных записей пользователей с помощью PowerShell в Office 365</span><span class="sxs-lookup"><span data-stu-id="0da66-117">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="0da66-118">Просмотр учетных записей пользователей с помощью PowerShell для Office 365</span><span class="sxs-lookup"><span data-stu-id="0da66-118">View user accounts with Office 365 PowerShell</span></span>](view-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="0da66-119">Настройка параметров учетной записи пользователя с помощью PowerShell для Office 365</span><span class="sxs-lookup"><span data-stu-id="0da66-119">Configure user account properties with Office 365 PowerShell</span></span>](configure-user-account-properties-with-office-365-powershell.md)
    

