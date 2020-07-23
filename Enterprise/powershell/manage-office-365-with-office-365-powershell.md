---
title: Управление Microsoft 365 с помощью PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- PowerShell
- O365ITProTrain
- Ent_Office_Other
ms.assetid: 932d57c0-1520-4f0f-8ec9-9966d646480f
description: 'Сводка: в этой статье рассказывается, как использовать PowerShell для управления пользователями и лицензиями Microsoft 365, Skype для бизнеса Online, SharePoint Online, Exchange Online и центром безопасности & соответствия требованиям.'
ms.openlocfilehash: 741ec15a78db9393e11ba6d06720457e20741581
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230515"
---
# <a name="manage-microsoft-365-with-powershell"></a><span data-ttu-id="fb8f3-103">Управление Microsoft 365 с помощью PowerShell</span><span class="sxs-lookup"><span data-stu-id="fb8f3-103">Manage Microsoft 365 with PowerShell</span></span>

<span data-ttu-id="fb8f3-104">*Эта статья относится как к Microsoft 365 Enterprise, так и к Office 365 корпоративный.*</span><span class="sxs-lookup"><span data-stu-id="fb8f3-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="fb8f3-105">PowerShell для Microsoft 365 — это мощное средство управления, которое дополняет центр администрирования Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="fb8f3-105">PowerShell for Microsoft 365 is a powerful management tool that complements the Microsoft 365 admin center.</span></span> <span data-ttu-id="fb8f3-106">Например, вы можете использовать автоматизацию PowerShell для более быстрого управления несколькими учетными записями и лицензиями пользователей и создания отчетов.</span><span class="sxs-lookup"><span data-stu-id="fb8f3-106">For example, you can use PowerShell automation to more quickly manage multiple user accounts and licenses and create reports.</span></span> <span data-ttu-id="fb8f3-107">Узнайте, как использовать PowerShell для пользователей и лицензий Microsoft 365, Skype для бизнеса Online, SharePoint Online, Exchange Online и центра безопасности & соответствия требованиям.</span><span class="sxs-lookup"><span data-stu-id="fb8f3-107">Learn how to use PowerShell for Microsoft 365 users and licenses, Skype for Business Online, SharePoint Online, Exchange Online, and the Security & Compliance Center.</span></span>
  
<span data-ttu-id="fb8f3-108">Выберите необходимый раздел:</span><span class="sxs-lookup"><span data-stu-id="fb8f3-108">Select the topic based on your needs:</span></span>
  
- [<span data-ttu-id="fb8f3-109">Начало работы</span><span class="sxs-lookup"><span data-stu-id="fb8f3-109">Get started</span></span>](getting-started-with-office-365-powershell.md)

    <span data-ttu-id="fb8f3-110">Начните отсюда, если вы не знакомы с PowerShell для Microsoft 365 и хотите установить модули Microsoft 365 и подключиться к своей подписке Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="fb8f3-110">Start here if you are not familiar with PowerShell for Microsoft 365 and want to install the Microsoft 365 modules and connect to your Microsoft 365 subscription.</span></span>

- [<span data-ttu-id="fb8f3-111">Учетные записи пользователей, лицензии и группы</span><span class="sxs-lookup"><span data-stu-id="fb8f3-111">User accounts, licenses, and groups</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)

    <span data-ttu-id="fb8f3-112">Начните отсюда, если вы установили модули Microsoft 365 и хотите узнать больше об использовании команд автоматизации для управления учетными записями пользователей, лицензиями и группами.</span><span class="sxs-lookup"><span data-stu-id="fb8f3-112">Start here if you have installed the Microsoft 365 modules and want to learn more about using automation commands to manage user accounts, licenses, and groups.</span></span>

- [<span data-ttu-id="fb8f3-113">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="fb8f3-113">SharePoint Online</span></span>](https://docs.microsoft.com/office365/enterprise/powershell/manage-sharepoint-online-with-office-365-powershell)

    <span data-ttu-id="fb8f3-114">Начните отсюда, если вы установили модули Microsoft 365 и хотите использовать команды автоматизации для выполнения управления SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="fb8f3-114">Start here if you have installed the Microsoft 365 modules and want to use automation commands to perform management of SharePoint Online.</span></span>

- [<span data-ttu-id="fb8f3-115">Exchange Online PowerShell</span><span class="sxs-lookup"><span data-stu-id="fb8f3-115">Exchange Online PowerShell</span></span>](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell)

    <span data-ttu-id="fb8f3-116">Ознакомьтесь с этой статьей, если вы хотите использовать команды автоматизации для управления Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="fb8f3-116">Start here if you want to use automation commands to manage Exchange Online.</span></span>

- [<span data-ttu-id="fb8f3-117">миграции электронной почты.</span><span class="sxs-lookup"><span data-stu-id="fb8f3-117">Email migration</span></span>](use-powershell-for-email-migration-to-office-365.md)

    <span data-ttu-id="fb8f3-118">Начните отсюда, если вы установили модули PowerShell 365 и хотите перенести электронную почту из существующих систем.</span><span class="sxs-lookup"><span data-stu-id="fb8f3-118">Start here if you have installed the PowerShell 365 modules and want to migrate your email from existing systems.</span></span>

- [<span data-ttu-id="fb8f3-119">Центр безопасности и соответствия требованиям</span><span class="sxs-lookup"><span data-stu-id="fb8f3-119">Security & Compliance Center</span></span>](https://docs.microsoft.com/powershell/exchange/office-365-scc/office-365-scc-powershell)

    <span data-ttu-id="fb8f3-120">Ознакомьтесь с этой статьей, если вы хотите использовать команды автоматизации для управления Центром безопасности и соответствия требованиям.</span><span class="sxs-lookup"><span data-stu-id="fb8f3-120">Start here if you want to use automation commands to manage the Security & Compliance Center.</span></span>

- [<span data-ttu-id="fb8f3-121">Партнеры по Делегированному доступу</span><span class="sxs-lookup"><span data-stu-id="fb8f3-121">Delegated Access Permissions (DAP) partners</span></span>](manage-office-365-with-windows-powershell-for-delegated-access-permissions-dap-p.md)

    <span data-ttu-id="fb8f3-122">Начните отсюда, если вы хотите использовать партнеров для синдикации и поставщиков облачных решений (CSP) для управления вашими клиентами Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="fb8f3-122">Start here if you want to use Syndication and Cloud Solution Provider (CSP) partners to manage your Microsoft 365 customer tenants.</span></span>

- [<span data-ttu-id="fb8f3-123">Skype для бизнеса Online</span><span class="sxs-lookup"><span data-stu-id="fb8f3-123">Skype for Business Online</span></span>](manage-skype-for-business-online-with-office-365-powershell.md)

    <span data-ttu-id="fb8f3-124">Начните отсюда, если вы установили модули PowerShell и хотите выполнить управление Skype для бизнеса Online.</span><span class="sxs-lookup"><span data-stu-id="fb8f3-124">Start here if you have installed the PowerShell modules and want to perform management of Skype for Business Online.</span></span>
