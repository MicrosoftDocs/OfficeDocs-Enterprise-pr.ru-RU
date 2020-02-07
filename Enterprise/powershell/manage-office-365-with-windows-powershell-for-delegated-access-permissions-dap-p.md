---
title: Управление Office 365 с помощью Windows PowerShell для партнеров службы разрешений делегированного доступа (DAP)
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-subscription-management
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: be497751-596f-431d-b256-0a89d36a47ce
description: Сводка. Партнеры по синдикации и поставщики облачных решений (CSP) может использовать Windows PowerShell для управления пользовательскими клиентами Office 365.
ms.openlocfilehash: 5e3fb67cad453593119347e2de07222f35d03f56
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844210"
---
# <a name="manage-office-365-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a><span data-ttu-id="bfa39-103">Управление Office 365 с помощью Windows PowerShell для партнеров службы разрешений делегированного доступа (DAP)</span><span class="sxs-lookup"><span data-stu-id="bfa39-103">Manage Office 365 with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>

 <span data-ttu-id="bfa39-104">**Сводка.** Партнеры по синдикации и поставщики облачных решений (CSP) могут управлять клиентами Office 365, используя Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bfa39-104">**Summary:** Syndication and Cloud Solution Provider (CSP) partners can use Windows PowerShell to manage Office 365 customer tenants.</span></span>
  
<span data-ttu-id="bfa39-105">Партнеры по делегированным правам доступа (DAP)  партнеры по синдикации и поставщики облачных решений (CSP).</span><span class="sxs-lookup"><span data-stu-id="bfa39-105">Delegated Access Permission (DAP) partners are Syndication and Cloud Solution Providers (CSP) Partners.</span></span> <span data-ttu-id="bfa39-106">Они часто бывают поставщиками сети или телекоммуникационных услуг в других компаниях.</span><span class="sxs-lookup"><span data-stu-id="bfa39-106">They are frequently network or telecom providers to other companies.</span></span> <span data-ttu-id="bfa39-107">Они внесли подписки на Office 365 в пакет своих услуг.</span><span class="sxs-lookup"><span data-stu-id="bfa39-107">They bundle Office 365 subscriptions into their service offerings to their customers.</span></span> <span data-ttu-id="bfa39-108">Продавая подписки на Office 365, они автоматически получают разрешения на администрирование от чьего-либо имени (AOBO) для области клиентов пользователя, что позволяет им администрировать эти области и создавать отчеты.</span><span class="sxs-lookup"><span data-stu-id="bfa39-108">When they sell an Office 365 subscription, they are automatically granted Administer On Behalf Of (AOBO) permissions to the customer tenancies so they can administer and report on the customer tenancies.</span></span> <span data-ttu-id="bfa39-109">В центре администрирования Майкрософт 365 это сложно и много времени.</span><span class="sxs-lookup"><span data-stu-id="bfa39-109">At best, this is difficult and time consuming to do in the Microsoft 365 admin center.</span></span> <span data-ttu-id="bfa39-110">Намного проще выполнять такие административные задачи, как вывод списка всех идентификаторов **TenantIds** пользователей и их доменов или идентификацию всех пользователей в аренде и назначенных им лицензий, с помощью Windows PowerShell для Office 365.</span><span class="sxs-lookup"><span data-stu-id="bfa39-110">It is much easier to do administrative tasks like listing all the customer **TenantIds** and their domains or identifying all users in a customer tenancy and what licenses they are assigned by using Windows PowerShell for Office 365.</span></span> <span data-ttu-id="bfa39-111">В некоторых случаях эти задачи администрирования возможно выполнять только в Windows PowerShell для Office 365.</span><span class="sxs-lookup"><span data-stu-id="bfa39-111">In some cases, it is possible to do these administrative tasks only in Windows PowerShell for Office 365.</span></span> <span data-ttu-id="bfa39-112">Ниже приведены примеры сценариев, которые партнеры служб синдикации и CSP чаще всего используют для администрирования своих клиентов:</span><span class="sxs-lookup"><span data-stu-id="bfa39-112">Here are samples of scenarios that Syndication and CSP partners most frequently use to administer their customer tenancies:</span></span>
  
## 

- [<span data-ttu-id="bfa39-113">Управление клиентами Office 365 с помощью Windows PowerShell для партнеров службы разрешений делегированного доступа (DAP)</span><span class="sxs-lookup"><span data-stu-id="bfa39-113">Manage Office 365 tenants with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>](manage-office-365-tenants-with-windows-powershell-for-delegated-access-permissio.md)
    
- [<span data-ttu-id="bfa39-114">Добавление домена к аренде клиента с помощью Windows PowerShell для партнеров службы разрешений делегированного доступа (DAP)</span><span class="sxs-lookup"><span data-stu-id="bfa39-114">Add a domain to a client tenancy with Windows PowerShell for Delegated Access Permission (DAP) partners</span></span>](add-a-domain-to-a-client-tenancy-with-windows-powershell-for-delegated-access-pe.md)
    
- [<span data-ttu-id="bfa39-115">Подключение к клиентам Exchange Online с помощью удаленного сеанса Windows PowerShell для партнеров службы разрешений делегированного доступа (DAP)</span><span class="sxs-lookup"><span data-stu-id="bfa39-115">Connect to Exchange Online tenants with remote Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)
    
- [<span data-ttu-id="bfa39-116">Получение отчетных данных пользовательских клиентов с помощью Windows PowerShell для партнеров службы разрешений делегированного доступа (DAP)</span><span class="sxs-lookup"><span data-stu-id="bfa39-116">Retrieve customer tenant reporting data with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>](retrieve-customer-tenant-reporting-data-with-windows-powershell-for-delegated-ac.md)
    

    

