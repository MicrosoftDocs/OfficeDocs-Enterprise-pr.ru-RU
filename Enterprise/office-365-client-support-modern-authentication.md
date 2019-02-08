---
title: Поддержка приложения клиента Office 365 — современных проверки подлинности
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: Office 365 Administration
localization_priority: None
search.appverid:
- MET150
ms.collection: Strat_O365_Enterprise
description: Поддержка клиентского приложения Office 365 для современных проверки подлинности.
ms.openlocfilehash: 18ef5b2219c9527594ae8fcff7e29052671d1431
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2019
ms.locfileid: "29771128"
---
# <a name="office-365-client-app-support---modern-authentication"></a>Поддержка приложения клиента Office 365 — современных проверки подлинности

Функция проверки подлинности на современном корпорации Майкрософт позволяет на основе ADAL библиотеки проверки подлинности Active Directory вход для клиентских приложений Office на различных платформах. Это позволяет входа такие функции многофакторной многофакторной проверки подлинности проверкой (Подлинности), смарт-карты и проверки подлинности на основе сертификатов.

Сведения о [многофакторной проверки подлинности](https://docs.microsoft.com/azure/active-directory/authentication/multi-factor-authentication) и [проверки подлинности на основе сертификатов](https://docs.microsoft.com/azure/active-directory/active-directory-certificate-based-authentication-get-started).

## <a name="supported-platforms"></a>Поддерживаемые платформы

 - Рабочий стол Windows 10
 - Современные приложения для Windows 10
 - Веб-браузер
 - Android
 - операций ввода-вывода
 - macOS

## <a name="supported-clients"></a>Поддерживаемые клиенты

В последних версиях следующие клиенты поддерживают современных проверки подлинности:

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Значок Azure](media/o365-azure-64x64.png) <br> [Azure AD <br> портала](https://azure.microsoft.com/features/azure-portal/) | ![Значок портала компании](media/o365-microsoft-64x64.png) <br> [Компания <br> портала](https://docs.microsoft.com/intune-user-help/sign-in-to-the-company-portal) | ![Углубимся значок](media/o365-delve-64x64.png) <br> [Delve](https://products.office.com/business/intelligent-search) | ![Значок Dynamics 365](media/o365-dynamics365-64x64.png) <br> [Dynamics 365](https://dynamics.microsoft.com) | ![Значок Excel](media/o365-excel-64x64.png) <br> [Excel](https://products.office.com/excel) |
| ![Значок потока](media/o365-flow-64x64.png) <br> [Flow](https://flow.microsoft.com) | ![Значок формы](media/o365-forms-64x64.png) <br> [формы;](https://flow.microsoft.com/connectors/shared_microsoftforms/microsoft-forms/) | ![Значок Kaizala](media/o365-kaizala-64x64.png) <br> [Kaizala](https://products.office.com/en/business/microsoft-kaizala) | ![Значок администратора Office 365](media/o365-o365admin-64x64.png) <br> [Office 365 <br> администрирования](https://products.office.com/business/manage-office-365-admin-app) | ![Значок лупы](media/o365-lens-64x64.png) <br> [Office Lens](https://www.microsoft.com/p/office-lens/9wzdncrfj3t8?activetab=pivot%3Aoverviewtab) | 
| ![OneDrive для бизнеса значок](media/o365-OneDrive-64x64.png) <br> [OneDrive](https://products.office.com/onedrive-for-business/online-cloud-storage) |  ![Значок OneNote](media/o365-OneNote-64x64.png) <br> [OneNote](https://products.office.com/onenote) | ![Значок Outlook](media/o365-outlook-64x64.png) <br> [Outlook](https://products.office.com/outlook) | ![Значок "Планировщик работы"](media/o365-planner-64x64.png) <br> [Planner](https://products.office.com/business/task-management-software) | ![Значок PowerBI](media/o365-powerbi-64x64.png) <br> [Power BI](https://powerbi.microsoft.com)
| ![Значок PowerPoint](media/o365-powerpoint-64x64.png) <br> [PowerPoint](https://products.office.com/powerpoint) | ![Значок проекта](media/o365-project-64x64.png) <br> [Project](https://products.office.com/project) | ![Значок SharePoint](media/o365-sharepoint-64x64.png) <br> [SharePoint](https://products.office.com/sharepoint) | ![Скайп для значка бизнеса](media/o365-skypeforbusiness-64x64.png) <br> [Скайп для <br> бизнеса](https://www.skype.com/business/) | ![Значок StaffHub](media/o365-staffhub-64x64.png) <br> [StaffHub](https://products.office.com/microsoft-staffhub/staff-scheduling-software)
| ![Решения о значок заметки](media/o365-stickynotes-64x64.png) <br> [Записки](https://www.microsoft.com/p/microsoft-sticky-notes/9nblggh4qghw) | ![Значок потока](media/o365-stream-64x64.png) <br> [Stream](https://stream.microsoft.com) | ![Значок sway](media/o365-sway-64x64.png) <br> [Sway](https://sway.com) | ![Значок группы](media/o365-teams-64x64.png) <br> [Teams](https://products.office.com/microsoft-teams/group-chat-software) | ![Значок "задачи"](media/o365-todo-64x64.png) <br> [To-Do](https://todo.microsoft.com)
| ![Значок Visio](media/o365-visio-64x64.png) <br> [Visio](https://products.office.com/visio/flowchart-software) | ![Значок Word](media/o365-word-64x64.png) <br> [Word](https://products.office.com/word) |![Значок сети Yammer](media/o365-yammer-64x64.png) <br> [Yammer](https://products.office.com/yammer/yammer-overview) | ![Значок сети Yammer](media/o365-yammer-64x64.png) <br> [Yammer <br> средство уведомления](https://products.office.com/yammer/yammer-overview) |  |

## <a name="supported-powershell-modules"></a>Поддерживаемые модули PowerShell

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Значок Azure](media/o365-azure-64x64.png) <br> [Azure AD <br> PowerShell](https://docs.microsoft.com/powershell/azure/active-directory/overview?view=azureadps-2.0) | ![Значок Exchange](media/o365-exchange-64x64.png) <br> [Exchange Online <br> PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell?view=exchange-ps) | ![Значок SharePoint](media/o365-sharepoint-64x64.png) <br> [SharePoint Online <br> PowerShell](https://docs.microsoft.com/sharepoint/manage-team-and-communication-sites-in-powershell)