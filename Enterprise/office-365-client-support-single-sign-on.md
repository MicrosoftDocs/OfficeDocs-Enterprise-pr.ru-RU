---
title: Поддержка клиентских приложений Office 365 — единый вход
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
description: Поддержка единого входа в клиентские приложения Office 365.
ms.openlocfilehash: e8f3aab27d898ebbc564a1815320bce72a151d35
ms.sourcegitcommit: b1a32e8df403143fb34eaddf116aed3595228c8c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/09/2019
ms.locfileid: "36817255"
---
# <a name="office-365-client-app-support--single-sign-on"></a>Поддержка клиентских приложений Office 365 — единый вход

Единый вход (SSO) обеспечивает безопасность и удобство при входе пользователей в приложения в Azure Active Directory (Azure AD). При использовании единого входа пользователи могут войти в систему с одной учетной записью, чтобы получить доступ к устройствам, связанным с доменом, ресурсам компании, программному обеспечению и веб-приложениям.

Дополнительные сведения об использовании [единого входа](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-single-sign-on).

## <a name="supported-platforms"></a>Поддерживаемые платформы

 - Windows 10 Desktop<sup>2</sup>
 - Windows 10 современные приложения<sup>4</sup>
 - Веб-браузеры
 - Android<sup>3</sup>
 - iOS<sup>1</sup>
 - macOS

Дополнительные сведения о поддержке платформ в Office 365 приведены в статье [требования к системе для office 365](https://products.office.com/office-system-requirements).

## <a name="supported-clients"></a>Поддерживаемые клиенты

Последние версии следующих клиентов поддерживают единый вход:

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Значок доступа](media/o365-access-64x64.png) <br> [Доступ](https://products.office.com/access) | ![Значок портала компании](media/o365-microsoft-64x64.png) <br> [Корпоративный <br> портал<sup>3</sup>](https://docs.microsoft.com/intune-user-help/sign-in-to-the-company-portal) | ![Значок delve](media/o365-delve-64x64.png) <br> [Delve](https://products.office.com/business/intelligent-search) | ![Значок пограничного сервера](media/o365-edge-64x64.png) <br> [Кромки](https://www.microsoft.com/windows/microsoft-edge) | ![Значок Excel](media/o365-excel-64x64.png) <br> [Excel](https://products.office.com/excel) 
| ![Значок "Flow"](media/o365-flow-64x64.png) <br> [Flow](https://flow.microsoft.com) | ![Значок Kaizala](media/o365-kaizala-64x64.png) <br> [Kaizala<sup>1</sup>](https://products.office.com/en/business/microsoft-kaizala) | ![Значок Office.com](media/o365-office-64x64.png) <br> [Office.com](https://www.office.com/) | ![Значок лупы](media/o365-lens-64x64.png) <br> [Office Lens<sup>4</sup>](https://www.microsoft.com/p/office-lens/9wzdncrfj3t8?activetab=pivot%3Aoverviewtab) | ![Значок OneDrive для бизнеса](media/o365-OneDrive-64x64.png) <br> [OneDrive](https://products.office.com/onedrive-for-business/online-cloud-storage) 
| ![Значок OneNote](media/o365-OneNote-64x64.png) <br> [OneNote<sup>2</sup>](https://products.office.com/onenote) | ![Значок Outlook](media/o365-outlook-64x64.png) <br> [Outlook](https://products.office.com/outlook) | ![Значок планировщика](media/o365-planner-64x64.png) <br> [Planner](https://products.office.com/business/task-management-software) | ![Значок PowerBI](media/o365-powerbi-64x64.png) <br> [Power BI<sup>2</sup>](https://powerbi.microsoft.com)| ![Значок PowerPoint](media/o365-powerpoint-64x64.png) <br> [PowerPoint](https://products.office.com/powerpoint) 
| ![Значок проекта](media/o365-project-64x64.png) <br> [Project](https://products.office.com/project) | ![Значок Publisher](media/o365-publisher-64x64.png) <br> [Publisher](https://products.office.com/publisher) | ![Значок SharePoint](media/o365-sharepoint-64x64.png) <br> [SharePoint](https://products.office.com/sharepoint) | ![Значок Skype для бизнеса](media/o365-skypeforbusiness-64x64.png) <br> [Skype для <br> бизнеса](https://www.skype.com/business/) | ![Значок клейких заметок](media/o365-stickynotes-64x64.png) <br> [Клейкие заметки](https://www.microsoft.com/p/microsoft-sticky-notes/9nblggh4qghw) 
| ![Значок Sway](media/o365-sway-64x64.png) <br> [Sway](https://sway.com) | ![Значок рабочих групп](media/o365-teams-64x64.png) <br> [Teams<sup>2</sup>](https://products.office.com/microsoft-teams/group-chat-software) | ![Значок "to do"](media/o365-todo-64x64.png) <br> [Действие](https://todo.microsoft.com) | ![Значок Visio](media/o365-visio-64x64.png) <br> [Visio](https://products.office.com/visio/flowchart-software) | ![Значок доски](media/o365-whiteboard-64x64.png) <br> [Доска<sup>3</sup>](https://whiteboard.microsoft.com/) 
| ![Значок Word](media/o365-word-64x64.png) <br> [Word](https://products.office.com/word) | ![Значок Yammer](media/o365-yammer-64x64.png) <br> [Yammer<sup>2</sup>](https://products.office.com/yammer/yammer-overview) |

## <a name="supported-powershell-modules"></a>Поддерживаемые модули PowerShell

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Значок Azure](media/o365-azure-64x64.png) <br> [Azure AD <br> PowerShell](https://docs.microsoft.com/powershell/azure/active-directory/overview?view=azureadps-2.0) | ![Значок Exchange](media/o365-exchange-64x64.png) <br> [Exchange Online <br> PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell?view=exchange-ps) | ![Значок SharePoint](media/o365-sharepoint-64x64.png) <br> [PowerShell в <br> SharePoint Online](https://docs.microsoft.com/sharepoint/manage-team-and-communication-sites-in-powershell)

> [!NOTE]
> <sup>1</sup> в ближайшее время доступна поддержка Kaizala в iOS. <br>
> <sup>2</sup> поддержка OneNote, PowerBI, Teams и Yammer на рабочем столе Windows 10 доступна в ближайшее время. <br>
> <sup>3</sup> поддержка доски в Android скоро доступна. <br>
> <sup>4</sup> поддержка Office Lens на современных приложениях с Windows 10 доступна в ближайшее время. <br>
