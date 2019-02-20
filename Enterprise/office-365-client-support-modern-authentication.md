---
title: Поддержка клиентских приложений Office 365 — современная проверка поДлинности
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: Office 365 Administration
localization_priority: Normal
ms.collection: Strat_O365_Enterprise
search.appverid:
- MET150
description: Поддержка современной проверки подлинности в клиентских приложениях Office 365.
ms.openlocfilehash: 8118ab6c9a7f62f01cede259b5b38c3242106102
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085358"
---
# <a name="office-365-client-app-support---modern-authentication"></a>Поддержка клиентских приложений Office 365 — современная проверка поДлинности

Современная проверка поДлинности Майкрософт включает вход на основе библиотеки проверки поДлинности Active Directory (ADAL) для клиентских приложений Office на разных платформах. Это включает функции входа, такие как многоФакторная проверка поДлинности (MFA), смарт-карта и проверка подлинности на основе сертификатов.

Узнайте больше о [многофакторной проверке](https://docs.microsoft.com/azure/active-directory/authentication/multi-factor-authentication) подлинности и [проверке подлинности на основе сертификатов](https://docs.microsoft.com/azure/active-directory/active-directory-certificate-based-authentication-get-started).

## <a name="supported-platforms"></a>Поддерживаемые платформы

 - Windows 10 для наСтольных ПК
 - Современные приложения Windows 10
 - Веб-браузер
 - Android
 - Модуле
 - macOS

Дополнительные сведения о поддержке платформ в Office 365 приведены в статье [требования к системе для office 365](https://products.office.com/office-system-requirements).

## <a name="supported-clients"></a>Поддерживаемые клиенты

Последние версии следующих клиентов поддерживают современные проверки подлинности:

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Значок Azure](media/o365-azure-64x64.png) <br> [Портал Azure <br> AD](https://azure.microsoft.com/features/azure-portal/) | ![Значок портала компании](media/o365-microsoft-64x64.png) <br> [Корпоративный <br> портал](https://docs.microsoft.com/intune-user-help/sign-in-to-the-company-portal) | ![Значок delve](media/o365-delve-64x64.png) <br> [Delve](https://products.office.com/business/intelligent-search) | ![Значок Dynamics 365](media/o365-dynamics365-64x64.png) <br> [Dynamics 365](https://dynamics.microsoft.com) | ![Значок Excel](media/o365-excel-64x64.png) <br> [Excel](https://products.office.com/excel) |
| ![Значок "Flow"](media/o365-flow-64x64.png) <br> [Flow](https://flow.microsoft.com) | ![Значок форм](media/o365-forms-64x64.png) <br> [формы;](https://flow.microsoft.com/connectors/shared_microsoftforms/microsoft-forms/) | ![Значок Kaizala](media/o365-kaizala-64x64.png) <br> [Kaizala](https://products.office.com/en/business/microsoft-kaizala) | ![Значок администратора Office 365](media/o365-o365admin-64x64.png) <br> [Администратор Office <br> 365](https://products.office.com/business/manage-office-365-admin-app) | ![Значок лупы](media/o365-lens-64x64.png) <br> [Office Lens](https://www.microsoft.com/p/office-lens/9wzdncrfj3t8?activetab=pivot%3Aoverviewtab) | 
| ![Значок OneDrive для бизнеса](media/o365-OneDrive-64x64.png) <br> [OneDrive](https://products.office.com/onedrive-for-business/online-cloud-storage) |  ![Значок OneNote](media/o365-OneNote-64x64.png) <br> [OneNote](https://products.office.com/onenote) | ![Значок Outlook](media/o365-outlook-64x64.png) <br> [Outlook](https://products.office.com/outlook) | ![Значок планировщика](media/o365-planner-64x64.png) <br> [Planner](https://products.office.com/business/task-management-software) | ![Значок PowerBI](media/o365-powerbi-64x64.png) <br> [Power BI](https://powerbi.microsoft.com)
| ![Значок PowerPoint](media/o365-powerpoint-64x64.png) <br> [PowerPoint](https://products.office.com/powerpoint) | ![Значок проекта](media/o365-project-64x64.png) <br> [Project](https://products.office.com/project) | ![Значок SharePoint](media/o365-sharepoint-64x64.png) <br> [SharePoint](https://products.office.com/sharepoint) | ![Значок Skype для бизнеса](media/o365-skypeforbusiness-64x64.png) <br> [Skype для <br> бизнеса](https://www.skype.com/business/) | ![Значок StaffHub](media/o365-staffhub-64x64.png) <br> [StaffHub](https://products.office.com/microsoft-staffhub/staff-scheduling-software)
| ![Значок клейких заМеток](media/o365-stickynotes-64x64.png) <br> [Клейкие заметки](https://www.microsoft.com/p/microsoft-sticky-notes/9nblggh4qghw) | ![Значок потока](media/o365-stream-64x64.png) <br> [Stream](https://stream.microsoft.com) | ![Значок Sway](media/o365-sway-64x64.png) <br> [Sway](https://sway.com) | ![Значок рабочих групп](media/o365-teams-64x64.png) <br> [Teams](https://products.office.com/microsoft-teams/group-chat-software) | ![Значок дел](media/o365-todo-64x64.png) <br> [To-Do](https://todo.microsoft.com)
| ![Значок Visio](media/o365-visio-64x64.png) <br> [Visio](https://products.office.com/visio/flowchart-software) | ![Значок Word](media/o365-word-64x64.png) <br> [Word](https://products.office.com/word) |![Значок Yammer](media/o365-yammer-64x64.png) <br> [Yammer](https://products.office.com/yammer/yammer-overview) | ![Значок Yammer](media/o365-yammer-64x64.png) <br> [Уведомление <br> об Yammer](https://products.office.com/yammer/yammer-overview) |  |

## <a name="supported-powershell-modules"></a>Поддерживаемые модули PowerShell

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Значок Azure](media/o365-azure-64x64.png) <br> [Azure AD <br> PowerShell](https://docs.microsoft.com/powershell/azure/active-directory/overview?view=azureadps-2.0) | ![Значок Exchange](media/o365-exchange-64x64.png) <br> [Exchange Online <br> PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell?view=exchange-ps) | ![Значок SharePoint](media/o365-sharepoint-64x64.png) <br> [PowerShell в <br> SharePoint Online](https://docs.microsoft.com/sharepoint/manage-team-and-communication-sites-in-powershell)