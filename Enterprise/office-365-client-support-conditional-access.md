---
title: Поддержка клиентских приложений Office 365 — условный доступ
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: Office 365 Administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_Enterprise
- M365-subscription-management
description: Общие сведения о поддержке клиентских приложений Office 365 для условного доступа
ms.openlocfilehash: bed811e16204fd05a83cf2b982a9a825b78b0e10
ms.sourcegitcommit: 27614632a0ceccbd5a4083cefa822187417f02a6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "36672929"
---
# <a name="office-365-client-app-support--conditional-access"></a>Поддержка клиентских приложений Office 365 — условный доступ

На современном рабочем месте пользователи могут получить доступ к ресурсам Организации с помощью различных устройств и приложений из любого места. Таким образом, просто сосредоточиться на том, кто может получить доступ к ресурсу, больше не хватает. Организация также должна поддерживать способ и место доступа к ресурсу в инфраструктуре управления доступом.

С помощью устройства, расположения и условного доступа на основе многофакторной проверки подлинности для Azure AD можно удовлетворить это новое требование. Условный доступ — это возможность Azure Active Directory, которая позволяет принудительно применять элементы управления для доступа к приложениям в вашей среде, в зависимости от конкретных условий и управления ими из центрального расположения.

Узнайте больше о [условном доступе](https://docs.microsoft.com/azure/active-directory/conditional-access/).

## <a name="supported-platforms"></a>Поддерживаемые платформы

 - Windows 10 для настольных ПК
 - Современные приложения Windows 10
 - Веб-браузеры
 - Android<sup>1</sup>
 - iOS
 - macOS<sup>2</sup>

Дополнительные сведения о поддержке платформ в Office 365 приведены в статье [требования к системе для office 365](https://products.office.com/office-system-requirements).

## <a name="supported-clients"></a>Поддерживаемые клиенты

Последние версии следующих клиентов поддерживают условный доступ:

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Значок Azure](media/o365-azure-64x64.png) <br> [Портал Azure <br> AD](https://azure.microsoft.com/features/azure-portal/) | ![Значок доступа](media/o365-access-64x64.png) <br> [Доступ](https://products.office.com/access) | ![Значок портала компании](media/o365-microsoft-64x64.png) <br> [Корпоративный <br> портал](https://docs.microsoft.com/intune-user-help/sign-in-to-the-company-portal)  | ![Значок delve](media/o365-delve-64x64.png) <br> [Delve<sup>1</sup>](https://products.office.com/business/intelligent-search) | ![Значок Dynamics 365](media/o365-dynamics365-64x64.png) <br> [Dynamics 365](https://dynamics.microsoft.com) 
| ![Значок пограничного сервера](media/o365-edge-64x64.png) <br> [Кромки](https://www.microsoft.com/windows/microsoft-edge) | ![Значок Exchange](media/o365-exchange-64x64.png) <br> [Exchange](https://products.office.com/exchange/exchange-online) | ![Значок Excel](media/o365-excel-64x64.png) <br> [Excel](https://products.office.com/excel) | ![Значок "Flow"](media/o365-flow-64x64.png) <br> [Flow](https://flow.microsoft.com) | ![Значок форм](media/o365-forms-64x64.png) <br> [Forms](https://flow.microsoft.com/connectors/shared_microsoftforms/microsoft-forms/) 
| ![Значок Kaizala](media/o365-kaizala-64x64.png) <br> [Kaizala](https://products.office.com/en/business/microsoft-kaizala) | ![Значок Office.com](media/o365-office-64x64.png) <br> [Office.com](https://www.office.com/) | ![Значок лупы](media/o365-lens-64x64.png) <br> [Office Lens](https://www.microsoft.com/p/office-lens/9wzdncrfj3t8?activetab=pivot%3Aoverviewtab) | ![Значок администратора Office 365](media/o365-o365admin-64x64.png) <br> [Администратор Office <br> 365](https://products.office.com/business/manage-office-365-admin-app) | ![Значок OneDrive для бизнеса](media/o365-OneDrive-64x64.png) <br> [OneDrive<sup>2</sup>](https://products.office.com/onedrive-for-business/online-cloud-storage) 
| ![Значок OneNote](media/o365-OneNote-64x64.png) <br> [OneNote](https://products.office.com/onenote) | ![Значок Outlook](media/o365-outlook-64x64.png) <br> [Outlook](https://products.office.com/outlook) | ![Значок планировщика](media/o365-planner-64x64.png) <br> [Planner](https://products.office.com/business/task-management-software) | ![Значок PowerBI](media/o365-powerbi-64x64.png) <br> [Power BI](https://powerbi.microsoft.com) | ![Значок PowerPoint](media/o365-powerpoint-64x64.png) <br> [PowerPoint](https://products.office.com/powerpoint) 
| ![Значок проекта](media/o365-project-64x64.png) <br> [Project](https://products.office.com/project) | ![Значок Publisher](media/o365-publisher-64x64.png) <br> [Publisher](https://products.office.com/publisher) | ![Значок SharePoint](media/o365-sharepoint-64x64.png) <br> [SharePoint](https://products.office.com/sharepoint) | ![Значок Skype для бизнеса](media/o365-skypeforbusiness-64x64.png) <br> [Skype для <br> бизнеса](https://www.skype.com/business/) | ![Значок клейких заметок](media/o365-stickynotes-64x64.png) <br> [Клейкие заметки](https://www.microsoft.com/p/microsoft-sticky-notes/9nblggh4qghw) 
| ![Значок потока](media/o365-stream-64x64.png) <br> [Stream](https://stream.microsoft.com) | ![Значок Sway](media/o365-sway-64x64.png) <br> [Sway](https://sway.com) | ![Значок рабочих групп](media/o365-teams-64x64.png) <br> [Teams](https://products.office.com/microsoft-teams/group-chat-software) | ![Значок дел](media/o365-todo-64x64.png) <br> [To-Do](https://todo.microsoft.com) | ![Значок Visio](media/o365-visio-64x64.png) <br> [Visio](https://products.office.com/visio/flowchart-software) 
| ![Значок Word](media/o365-word-64x64.png) <br> [Word](https://products.office.com/word) | ![Значок Yammer](media/o365-yammer-64x64.png) <br> [Yammer](https://products.office.com/yammer/yammer-overview)

## <a name="supported-powershell-modules"></a>Поддерживаемые модули PowerShell

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Значок Azure](media/o365-azure-64x64.png) <br> [Azure AD <br> PowerShell](https://docs.microsoft.com/powershell/azure/active-directory/overview?view=azureadps-2.0) | ![Значок SharePoint](media/o365-sharepoint-64x64.png) <br> [PowerShell в <br> SharePoint Online](https://docs.microsoft.com/sharepoint/manage-team-and-communication-sites-in-powershell)

> [!NOTE]
> <sup>1</sup> поддержка delve в Android скоро доступна. <br>
> <sup>2</sup> поддержка OneDrive в macOS доступна в ближайшее время.
