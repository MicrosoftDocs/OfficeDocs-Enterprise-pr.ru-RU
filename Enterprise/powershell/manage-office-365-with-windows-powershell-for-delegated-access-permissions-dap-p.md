---
title: Управление Microsoft 365 с помощью Windows PowerShell для партнеров с правами доступа к данным делегированного доступа
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- M365-subscription-management
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: be497751-596f-431d-b256-0a89d36a47ce
description: Сводка. партнеры по синдикации и поставщикам облачных решений (CSP) могут использовать Windows PowerShell для управления клиентскими клиентами Microsoft 365.
ms.openlocfilehash: 00e60693ad10b705765da9ed57142c893a74b034
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998225"
---
# <a name="manage-microsoft-365-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a><span data-ttu-id="5c8ec-103">Управление Microsoft 365 с помощью Windows PowerShell для партнеров с правами доступа к данным делегированного доступа</span><span class="sxs-lookup"><span data-stu-id="5c8ec-103">Manage Microsoft 365 with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>

<span data-ttu-id="5c8ec-104">Партнеры по делегированным правам доступа (DAP)  партнеры по синдикации и поставщики облачных решений (CSP).</span><span class="sxs-lookup"><span data-stu-id="5c8ec-104">Delegated Access Permission (DAP) partners are Syndication and Cloud Solution Providers (CSP) Partners.</span></span> <span data-ttu-id="5c8ec-105">Они часто бывают поставщиками сети или телекоммуникационных услуг в других компаниях.</span><span class="sxs-lookup"><span data-stu-id="5c8ec-105">They are frequently network or telecom providers to other companies.</span></span> <span data-ttu-id="5c8ec-106">Они объединяют подписки на Microsoft 365 на свои услуги своим клиентам.</span><span class="sxs-lookup"><span data-stu-id="5c8ec-106">They bundle Microsoft 365 subscriptions into their service offerings to their customers.</span></span> <span data-ttu-id="5c8ec-107">Когда вы продаете подписку на Microsoft 365, им автоматически предоставляются разрешения на администрирование от имени пользователя (АОБО), чтобы они могли администрировать и предоставлять отчеты для клиентов клиенты.</span><span class="sxs-lookup"><span data-stu-id="5c8ec-107">When they sell a Microsoft 365 subscription, they are automatically granted Administer On Behalf Of (AOBO) permissions to the customer tenancies so they can administer and report on the customer tenancies.</span></span> <span data-ttu-id="5c8ec-108">В центре администрирования Майкрософт 365 это сложно и много времени.</span><span class="sxs-lookup"><span data-stu-id="5c8ec-108">At best, this is difficult and time consuming to do in the Microsoft 365 admin center.</span></span> <span data-ttu-id="5c8ec-109">Намного проще выполнять такие административные задачи, как вывод списка всех идентификаторов **TenantIds** пользователей и их доменов или идентификацию всех пользователей в аренде и назначенных им лицензий, с помощью Windows PowerShell для Office 365.</span><span class="sxs-lookup"><span data-stu-id="5c8ec-109">It is much easier to do administrative tasks like listing all the customer **TenantIds** and their domains or identifying all users in a customer tenancy and what licenses they are assigned by using Windows PowerShell for Office 365.</span></span> <span data-ttu-id="5c8ec-110">В некоторых случаях эти задачи администрирования возможно выполнять только в Windows PowerShell для Office 365.</span><span class="sxs-lookup"><span data-stu-id="5c8ec-110">In some cases, it is possible to do these administrative tasks only in Windows PowerShell for Office 365.</span></span> <span data-ttu-id="5c8ec-111">Ниже приведены примеры сценариев, которые партнеры служб синдикации и CSP чаще всего используют для администрирования своих клиентов:</span><span class="sxs-lookup"><span data-stu-id="5c8ec-111">Here are samples of scenarios that Syndication and CSP partners most frequently use to administer their customer tenancies:</span></span>
  
## 

- [<span data-ttu-id="5c8ec-112">Управление клиентами Microsoft 365 с помощью Windows PowerShell для партнеров с правами доступа к данным делегированного доступа</span><span class="sxs-lookup"><span data-stu-id="5c8ec-112">Manage Microsoft 365 tenants with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>](manage-office-365-tenants-with-windows-powershell-for-delegated-access-permissio.md)
    
- [<span data-ttu-id="5c8ec-113">Добавление домена к аренде клиента с помощью Windows PowerShell для партнеров службы разрешений делегированного доступа (DAP)</span><span class="sxs-lookup"><span data-stu-id="5c8ec-113">Add a domain to a client tenancy with Windows PowerShell for Delegated Access Permission (DAP) partners</span></span>](add-a-domain-to-a-client-tenancy-with-windows-powershell-for-delegated-access-pe.md)
    
- [<span data-ttu-id="5c8ec-114">Подключение к клиентам Exchange Online с помощью удаленного сеанса Windows PowerShell для партнеров службы разрешений делегированного доступа (DAP)</span><span class="sxs-lookup"><span data-stu-id="5c8ec-114">Connect to Exchange Online tenants with remote Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)
    
- [<span data-ttu-id="5c8ec-115">Получение отчетных данных пользовательских клиентов с помощью Windows PowerShell для партнеров службы разрешений делегированного доступа (DAP)</span><span class="sxs-lookup"><span data-stu-id="5c8ec-115">Retrieve customer tenant reporting data with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>](retrieve-customer-tenant-reporting-data-with-windows-powershell-for-delegated-ac.md)
    

    

