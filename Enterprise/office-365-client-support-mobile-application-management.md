---
title: Поддержка клиентских приложений Office 365 — управление мобильными приложениями
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: Office 365 Administration
localization_priority: Normal
ms.collection:
- Strat_O365_Enterprise
- M365-subscription-management
search.appverid:
- MET150
description: Общие сведения о поддержке клиентских приложений Office 365 для управления мобильными приложениями
ms.openlocfilehash: b75b992bf45ff1a899e71a9f6b7903e3f78a34d4
ms.sourcegitcommit: 80bc767a9c88a259facb3894b9a168c85d35eb70
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "31517553"
---
# <a name="office-365-client-app-support---mobile-application-management"></a><span data-ttu-id="0d7a0-103">Поддержка клиентских приложений Office 365 — управление мобильными приложениями</span><span class="sxs-lookup"><span data-stu-id="0d7a0-103">Office 365 Client App Support - Mobile Application Management</span></span>

<span data-ttu-id="0d7a0-104">Используя набор функций управления Intune, управление мобильными приложениями (MAM) позволяет публиковать, отправлять, настраивать, защищать и обновлять мобильные приложения для пользователей.</span><span class="sxs-lookup"><span data-stu-id="0d7a0-104">Leveraging the suite of Intune management features, mobile application management (MAM) lets you publish, push, configure, secure, monitor, and update mobile apps for your users.</span></span> <span data-ttu-id="0d7a0-105">MAM может защищать данные Организации в приложении для всех устройств независимо от того, зарегистрирована ли она в Intune или нет.</span><span class="sxs-lookup"><span data-stu-id="0d7a0-105">MAM can protect an organization's data within an application for all devices, whether enrolled in Intune or not.</span></span>

<span data-ttu-id="0d7a0-106">Узнайте больше об [управлении мобильными приложениями](https://docs.microsoft.com/intune/mam-faq) и в [MAM с несколькими удостоверениями](https://docs.microsoft.com/intune/app-protection-policy).</span><span class="sxs-lookup"><span data-stu-id="0d7a0-106">Learn more about [mobile application management](https://docs.microsoft.com/intune/mam-faq) and [multi-identity MAM](https://docs.microsoft.com/intune/app-protection-policy).</span></span>

## <a name="supported-platforms"></a><span data-ttu-id="0d7a0-107">Поддерживаемые платформы</span><span class="sxs-lookup"><span data-stu-id="0d7a0-107">Supported platforms</span></span>

 - <span data-ttu-id="0d7a0-108">Android</span><span class="sxs-lookup"><span data-stu-id="0d7a0-108">Android</span></span>
 - <span data-ttu-id="0d7a0-109">iOS<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="0d7a0-109">iOS<sup>1</sup></span></span>

<span data-ttu-id="0d7a0-110">Дополнительные сведения о поддержке платформ в Office 365 приведены в статье [требования к системе для office 365](https://products.office.com/office-system-requirements).</span><span class="sxs-lookup"><span data-stu-id="0d7a0-110">For more information about platform support in Office 365, see [System requirements for Office 365](https://products.office.com/office-system-requirements).</span></span>

## <a name="supported-clients"></a><span data-ttu-id="0d7a0-111">Поддерживаемые клиенты</span><span class="sxs-lookup"><span data-stu-id="0d7a0-111">Supported clients</span></span>

<span data-ttu-id="0d7a0-112">Последние версии следующих клиентов поддерживают управление мобильными приложениями:</span><span class="sxs-lookup"><span data-stu-id="0d7a0-112">The latest versions of the following clients support mobile application management:</span></span>

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Значок Dynamics 365](media/o365-dynamics365-64x64.png) <br> [<span data-ttu-id="0d7a0-114">Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="0d7a0-114">Dynamics 365</span></span>](https://dynamics.microsoft.com) | ![Значок поГраничного сервера](media/o365-edge-64x64.png) <br> [<span data-ttu-id="0d7a0-116">Кромки</span><span class="sxs-lookup"><span data-stu-id="0d7a0-116">Edge</span></span>](https://www.microsoft.com/windows/microsoft-edge) | ![Значок Excel](media/o365-excel-64x64.png) <br> [<span data-ttu-id="0d7a0-118">Excel</span><span class="sxs-lookup"><span data-stu-id="0d7a0-118">Excel</span></span>](https://products.office.com/excel) | ![Значок "Flow"](media/o365-flow-64x64.png) <br> [<span data-ttu-id="0d7a0-120">Flow</span><span class="sxs-lookup"><span data-stu-id="0d7a0-120">Flow</span></span>](https://flow.microsoft.com) | ![Значок Kaizala](media/o365-kaizala-64x64.png) <br> [<span data-ttu-id="0d7a0-122">Kaizala</span><span class="sxs-lookup"><span data-stu-id="0d7a0-122">Kaizala</span></span>](https://products.office.com/en/business/microsoft-kaizala) 
| ![Значок OneDrive для бизнеса](media/o365-OneDrive-64x64.png) <br> [<span data-ttu-id="0d7a0-124">OneDrive</span><span class="sxs-lookup"><span data-stu-id="0d7a0-124">OneDrive</span></span>](https://products.office.com/onedrive-for-business/online-cloud-storage) | ![Значок OneNote](media/o365-OneNote-64x64.png) <br> [<span data-ttu-id="0d7a0-126">OneNote</span><span class="sxs-lookup"><span data-stu-id="0d7a0-126">OneNote</span></span>](https://products.office.com/onenote) | ![Значок Outlook](media/o365-outlook-64x64.png) <br> [<span data-ttu-id="0d7a0-128">Outlook</span><span class="sxs-lookup"><span data-stu-id="0d7a0-128">Outlook</span></span>](https://products.office.com/outlook) | ![Значок планировщика](media/o365-planner-64x64.png) <br> [<span data-ttu-id="0d7a0-130">Планировщик</span><span class="sxs-lookup"><span data-stu-id="0d7a0-130">Planner</span></span>](https://products.office.com/business/task-management-software) | ![Значок PowerApps](media/o365-powerapps-64x64.png) <br> [<span data-ttu-id="0d7a0-132">PowerApps</span><span class="sxs-lookup"><span data-stu-id="0d7a0-132">PowerApps</span></span> ](https://powerapps.microsoft.com) 
| ![Значок PowerBI](media/o365-powerbi-64x64.png) <br> [<span data-ttu-id="0d7a0-134">Power BI</span><span class="sxs-lookup"><span data-stu-id="0d7a0-134">Power BI</span></span>](https://powerbi.microsoft.com) | ![Значок PowerPoint](media/o365-powerpoint-64x64.png) <br> [<span data-ttu-id="0d7a0-136">PowerPoint</span><span class="sxs-lookup"><span data-stu-id="0d7a0-136">PowerPoint</span></span>](https://products.office.com/powerpoint) | ![Значок SharePoint](media/o365-sharepoint-64x64.png) <br> [<span data-ttu-id="0d7a0-138">SharePoint</span><span class="sxs-lookup"><span data-stu-id="0d7a0-138">Sharepoint</span></span>](https://products.office.com/sharepoint) | ![Значок Skype для бизнеса](media/o365-skypeforbusiness-64x64.png) <br> [<span data-ttu-id="0d7a0-140">Skype для <br> бизнеса</span><span class="sxs-lookup"><span data-stu-id="0d7a0-140">Skype for <br> Business</span></span>](https://www.skype.com/business/) | ![Значок StaffHub](media/o365-staffhub-64x64.png) <br> [<span data-ttu-id="0d7a0-142">StaffHub</span><span class="sxs-lookup"><span data-stu-id="0d7a0-142">StaffHub</span></span>](https://products.office.com/microsoft-staffhub/staff-scheduling-software) 
| ![Значок потока](media/o365-stream-64x64.png) <br> [<span data-ttu-id="0d7a0-144">Поток</span><span class="sxs-lookup"><span data-stu-id="0d7a0-144">Stream</span></span>](https://stream.microsoft.com) | ![Значок Sway](media/o365-sway-64x64.png) <br> [<span data-ttu-id="0d7a0-146">Sway<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="0d7a0-146">Sway<sup>1</sup></span></span>](https://sway.com) | ![Значок рабочих групп](media/o365-teams-64x64.png) <br> [<span data-ttu-id="0d7a0-148">Teams</span><span class="sxs-lookup"><span data-stu-id="0d7a0-148">Teams</span></span>](https://products.office.com/microsoft-teams/group-chat-software) | ![Значок дел](media/o365-todo-64x64.png) <br> [<span data-ttu-id="0d7a0-150">To-Do</span><span class="sxs-lookup"><span data-stu-id="0d7a0-150">To-Do</span></span>](https://todo.microsoft.com) | ![Значок Visio](media/o365-visio-64x64.png) <br> [<span data-ttu-id="0d7a0-152">Visio</span><span class="sxs-lookup"><span data-stu-id="0d7a0-152">Visio</span></span>](https://products.office.com/visio/flowchart-software) 
| ![Значок Word](media/o365-word-64x64.png) <br> [<span data-ttu-id="0d7a0-154">Word</span><span class="sxs-lookup"><span data-stu-id="0d7a0-154">Word</span></span>](https://products.office.com/word) | ![Значок Yammer](media/o365-yammer-64x64.png) <br> [<span data-ttu-id="0d7a0-156">Yammer</span><span class="sxs-lookup"><span data-stu-id="0d7a0-156">Yammer</span></span>](https://products.office.com/yammer/yammer-overview)

> [!NOTE]
> <span data-ttu-id="0d7a0-157"><sup></sup> в ближайшее время вы сможете в скором времени включить поддержку Sway для iOS.</span><span class="sxs-lookup"><span data-stu-id="0d7a0-157"><sup>1</sup> Support for Sway on iOS coming soon.</span></span>