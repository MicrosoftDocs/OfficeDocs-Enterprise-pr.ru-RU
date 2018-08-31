---
title: Поддержка приложения клиента Office 365 — условного доступа
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 7/17/2018
audience: ITPro
ms.topic: article
ms.service: Office 365 Administration
localization_priority: None
search.appverid:
- MET150
ms.collection: Strat_O365_Enterprise
description: Понять поддержки приложения клиента Office 365 условного доступа
ms.openlocfilehash: 215b97daf532e22eb37618d66779378e37accb31
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915304"
---
# <a name="office-365-client-app-support---conditional-access"></a>Поддержка приложения клиента Office 365 — условного доступа

В современных рабочей области доступ можно ресурсы организации с помощью различных устройств и приложений практически в любом месте. В результате только что внимание пользователей на доступ к ресурсу уже не достаточно. Также должны поддерживать вашей организации, как и где ресурса осуществляется в инфраструктуре управления доступа. С Azure AD устройства, расположение и многофакторной проверки подлинности на основе условного доступа можно выполнение этих новых требований. Условное доступа — это возможность Azure Active Directory, которая позволяет обеспечить элементов управления на доступ к приложениям в вашей среде все на основе определенных условий и управлять из центрального расположения. 

Дополнительные сведения о [на устройство](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-policy-connected-applications), [на основе расположения](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-locations)и условного доступ на [основе многофакторной проверкой Подлинности](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-conditions#users-and-groups) .

## <a name="supported-platforms"></a>Поддерживаемые платформы

 - Рабочий стол Windows 10
 - Современные приложения для Windows 10
 - Веб-браузер
 - Android
 - операций ввода-вывода
 - macOS<sup>1</sup>

## <a name="supported-clients"></a>Поддерживаемые клиенты

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Углубимся значок](media/o365-delve-64x64.png) <br> [Delve;](https://products.office.com/business/intelligent-search) | ![Значок Excel](media/o365-excel-64x64.png) <br> [Excel](https://products.office.com/excel) | ![Значок потока](media/o365-flow-64x64.png) <br> [Flow](https://flow.microsoft.com) | ![Значок формы](media/o365-forms-64x64.png) <br> [Forms](https://flow.microsoft.com/connectors/shared_microsoftforms/microsoft-forms/) | ![Значок Kaizala](media/o365-kaizala-64x64.png) <br> [Kaizala](https://products.office.com/en/business/microsoft-kaizala) 
| ![Значок администратора Office 365](media/o365-o365admin-64x64.png) <br> [Office 365 <br> администрирования](https://products.office.com/business/manage-office-365-admin-app) | ![OneDrive для бизнеса значок](media/o365-OneDrive-64x64.png) <br> [OneDrive](https://products.office.com/onedrive-for-business/online-cloud-storage) | ![Значок OneNote](media/o365-OneNote-64x64.png) <br> [OneNote](https://products.office.com/onenote) | ![Значок Outlook](media/o365-outlook-64x64.png) <br> [Outlook](https://products.office.com/outlook) | ![Значок "Планировщик работы"](media/o365-planner-64x64.png) <br> [Планировщик](https://products.office.com/business/task-management-software) 
| ![Значок PowerBI](media/o365-powerbi-64x64.png) <br> [Power BI](https://powerbi.microsoft.com) | ![Значок PowerPoint](media/o365-powerpoint-64x64.png) <br> [PowerPoint](https://products.office.com/powerpoint) | ![Значок проекта](media/o365-project-64x64.png) <br> [Project](https://products.office.com/project) | ![Значок SharePoint](media/o365-sharepoint-64x64.png) <br> [SharePoint<sup>1</sup>](https://products.office.com/sharepoint) | ![Скайп для значка бизнеса](media/o365-skypeforbusiness-64x64.png) <br> [Скайп для <br> бизнеса](https://www.skype.com/business/) 
| ![Значок StaffHub](media/o365-staffhub-64x64.png) <br> [StaffHub](https://products.office.com/microsoft-staffhub/staff-scheduling-software) | ![Значок потока](media/o365-stream-64x64.png) <br> [Поток](https://stream.microsoft.com) | ![Значок sway](media/o365-sway-64x64.png) <br> [Sway](https://sway.com) | ![Значок группы](media/o365-teams-64x64.png) <br> [Teams](https://products.office.com/microsoft-teams/group-chat-software) | ![Значок "задачи"](media/o365-todo-64x64.png) <br> [To-Do](https://todo.microsoft.com) 
| ![Значок Visio](media/o365-visio-64x64.png) <br> [Visio](https://products.office.com/visio/flowchart-software) | ![Значок Word](media/o365-word-64x64.png) <br> [Word](https://products.office.com/word) | ![Значок сети Yammer](media/o365-yammer-64x64.png) <br> [Yammer](https://products.office.com/yammer/yammer-overview)

> [!NOTE]
> <sup>1</sup> поддерживают приложения для SharePoint на macOS готовится к выпуску.