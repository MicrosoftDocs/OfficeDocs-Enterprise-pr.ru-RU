---
title: Поддержка клиентских приложений Office 365 — проверка подлинности на основе сертификатов
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
f1.keywords:
- NOCSH
description: Поддержка клиентских приложений Office 365 для проверки подлинности на основе сертификатов.
ms.openlocfilehash: 70ce690cc19e6db575f654daa1fe7d59c89e158c
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/07/2020
ms.locfileid: "41849082"
---
# <a name="office-365-client-app-support--certificate-based-authentication"></a>Поддержка клиентских приложений Office 365 — проверка подлинности на основе сертификатов

*Эта статья относится к Office 365 корпоративный и Microsoft 365 корпоративный.*

Проверка подлинности на основе сертификатов позволяет выполнять проверку подлинности в Azure Active Directory с помощью сертификата клиента на устройствах под управлением Windows, Android или iOS. Настройка этой функции исключает необходимость ввода имени пользователя и пароля в определенные приложения электронной почты и приложения Microsoft Office на мобильном устройстве.

Узнайте больше о [проверке подлинности на основе сертификатов](https://docs.microsoft.com/azure/active-directory/authentication/active-directory-certificate-based-authentication-get-started).

## <a name="supported-platforms"></a>Поддерживаемые платформы

 - Windows 10 Desktop<sup>2</sup>
 - Современные приложения Windows 10
 - Веб-браузеры<sup>3</sup>
 - Android<sup>4</sup>
 - iOS
 - macOS<sup>1</sup> <sup>2</sup>

Дополнительные сведения о поддержке платформ в Office 365 приведены в статье [требования к системе для office 365](https://products.office.com/office-system-requirements).

## <a name="supported-clients"></a>Поддерживаемые клиенты

Последние версии следующих клиентов поддерживают проверку подлинности на основе сертификатов:

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Значок Access](media/o365-access-64x64.png) <br> [Access](https://products.office.com/access) | ![Значок Azure](media/o365-azure-64x64.png) <br> [Портал Azure <br> AD](https://azure.microsoft.com/features/azure-portal/) | ![Значок портала компании](media/o365-microsoft-64x64.png) <br> [Корпоративный <br> портал](https://docs.microsoft.com/intune-user-help/sign-in-to-the-company-portal) | ![Значок delve](media/o365-delve-64x64.png) <br> [Delve](https://products.office.com/business/intelligent-search) | ![Значок Dynamics 365](media/o365-dynamics365-64x64.png) <br> [Dynamics 365](https://dynamics.microsoft.com) 
| ![Значок пограничного сервера](media/o365-edge-64x64.png) <br> [Microsoft Edge](https://www.microsoft.com/windows/microsoft-edge) | ![Значок Excel](media/o365-excel-64x64.png) <br> [Excel](https://products.office.com/excel) | ![Значок Flow](media/o365-flow-64x64.png) <br> [Flow](https://flow.microsoft.com) | ![Значок Forms](media/o365-forms-64x64.png) <br> [Forms](https://flow.microsoft.com/connectors/shared_microsoftforms/microsoft-forms/) | ![Значок Kaizala](media/o365-kaizala-64x64.png) <br> [Kaizala](https://products.office.com/en/business/microsoft-kaizala) 
| ![Значок Office.com](media/o365-office-64x64.png) <br> [Office.com](https://www.office.com/) | ![Значок администратора Office 365](media/o365-o365admin-64x64.png) <br> [Администратор Office <br> 365](https://products.office.com/business/manage-office-365-admin-app) | ![Значок лупы](media/o365-lens-64x64.png) <br> [Office Lens](https://www.microsoft.com/p/office-lens/9wzdncrfj3t8?activetab=pivot%3Aoverviewtab) | ![Значок OneDrive для бизнеса](media/o365-OneDrive-64x64.png) <br> [OneDrive<sup>1</sup>](https://products.office.com/onedrive-for-business/online-cloud-storage) |  ![Значок OneNote](media/o365-OneNote-64x64.png) <br> [OneNote](https://products.office.com/onenote) 
| ![Значок Outlook](media/o365-outlook-64x64.png) <br> [Outlook](https://products.office.com/outlook) | ![Значок Планировщика](media/o365-planner-64x64.png) <br> [Планировщик](https://products.office.com/business/task-management-software) | ![Значок PowerApps](media/o365-powerapps-64x64.png) <br> [PowerApps<sup>3</sup>](https://powerapps.microsoft.com) | ![Значок PowerBI](media/o365-powerbi-64x64.png) <br> [Power BI](https://powerbi.microsoft.com)| ![Значок PowerPoint](media/o365-powerpoint-64x64.png) <br> [PowerPoint](https://products.office.com/powerpoint) 
| ![Значок Project](media/o365-project-64x64.png) <br> [Project](https://products.office.com/project) | ![Значок Publisher](media/o365-publisher-64x64.png) <br> [Publisher](https://products.office.com/publisher) | ![Значок SharePoint](media/o365-sharepoint-64x64.png) <br> [SharePoint](https://products.office.com/sharepoint) | ![Значок Skype для бизнеса](media/o365-skypeforbusiness-64x64.png) <br> [Skype для <br> бизнеса](https://www.skype.com/business/) | ![Значок клейких заметок](media/o365-stickynotes-64x64.png) <br> [Клейкие заметки](https://www.microsoft.com/p/microsoft-sticky-notes/9nblggh4qghw) 
| ![Значок Stream](media/o365-stream-64x64.png) <br> [Stream](https://stream.microsoft.com) | ![Значок Sway](media/o365-sway-64x64.png) <br> [Sway](https://sway.com) | ![Значок Teams](media/o365-teams-64x64.png) <br> [Teams<sup>2</sup>](https://products.office.com/microsoft-teams/group-chat-software) | ![Значок "to do"](media/o365-todo-64x64.png) <br> [To-Do](https://todo.microsoft.com) | ![Значок Visio](media/o365-visio-64x64.png) <br> [Visio](https://products.office.com/visio/flowchart-software) 
| ![Значок Доски](media/o365-whiteboard-64x64.png) <br> [Доска<sup>3</sup>,<sup>4</sup>](https://whiteboard.microsoft.com/) | ![Значок Word](media/o365-word-64x64.png) <br> [Word](https://products.office.com/word) | ![Значок Yammer](media/o365-yammer-64x64.png) <br> [Yammer<sup>2</sup>](https://products.office.com/yammer/yammer-overview) |

## <a name="supported-powershell-modules"></a>Поддерживаемые модули PowerShell

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Значок Azure](media/o365-azure-64x64.png) <br> [Azure AD <br> PowerShell](https://docs.microsoft.com/powershell/azure/active-directory/overview?view=azureadps-2.0) | ![Значок Exchange](media/o365-exchange-64x64.png) <br> [Exchange Online <br> PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell?view=exchange-ps) | ![Значок SharePoint](media/o365-sharepoint-64x64.png) <br> [PowerShell в <br> SharePoint Online](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)

> [!NOTE]
> <sup>1</sup> поддержка OneDrive в macOS доступна в ближайшее время. <br>
> <sup>2</sup> поддержка Yammer на настольных компьютерах с Windows и macOS доступна в ближайшее время. В ближайшее время доступна поддержка Teams на рабочем столе Windows.<br>
> <sup>3</sup> поддержка PowerApps и доска в веб-приложениях скоро доступна. <br>
> <sup>4</sup> в скором времени доступна поддержка доски на Android.

## <a name="see-also"></a>См. также

[Обзор Microsoft 365 корпоративный](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)
