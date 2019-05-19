---
title: Назначение лицензий на Office 365 для учетных записей пользователей
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
f1_keywords:
- O365p_AddUsersWithDirSync
- O365M_AddUsersWithDirSync
- O365E_HRCSetupAADConnectAboutLM617031
- O365E_AddUsersWithDirSync
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOP150
- MOE150
- MBS150
ms.assetid: 01920974-9e6f-4331-a370-13aea4e82b3e
description: В этой статье описано, как назначать лицензии на Office 365 для учетных записей пользователей по отдельности или в зависимости от принадлежности к группе.
ms.openlocfilehash: 0f258ef9240239ebdfa695e8c5b214484cfb4db1
ms.sourcegitcommit: 36e760407a1f4b18bc108134628ed9a8d3e35a8a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/17/2019
ms.locfileid: "34164604"
---
# <a name="assign-office-365-licenses-to-user-accounts"></a>Назначение лицензий на Office 365 для учетных записей пользователей

Для модели удостоверений, которая используется только в облаке, вы можете назначить лицензии Office 365 для учетных записей пользователей при их создании, в зависимости от того, как они создаются.

Для модели гибридной идентификации при первой синхронизации учетных записей пользователей доменных служб Active Directory (AD DS) им не назначается автоматическая лицензия на Office 365.

В любом случае необходимо назначить лицензии учетным записям пользователей, чтобы пользователи могли получать доступ к службам Office 365, таким как электронная почта и Microsoft Teams.

Вы можете назначать лицензии учетным записям пользователей по отдельности или автоматически с помощью членства в группе.

Чтобы назначить лицензии Office 365 отдельным учетным записям пользователей, можно использовать:

- [Центр администрирования Microsoft 365](https://docs.microsoft.com/office365/admin/subscriptions-and-billing/assign-licenses-to-users)
- [Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/assign-licenses-to-user-accounts-with-office-365-powershell)

Для автоматического назначения лицензий просмотрите раздел [Лицензирование на основе групп в Azure AD](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-licensing-whatis-azure-portal).

## <a name="next-steps"></a>Дальнейшие действия

С полным набором учетных записей пользователей, которым были назначены лицензии, вы можете:

- [Развертывание клиентского программного обеспечения, например Office 365 профессиональный плюс](https://docs.microsoft.com/DeployOffice/deployment-guide-for-office-365-proplus)
- [Настройка управления мобильными устройствами](https://support.office.com/article/set-up-mobile-device-management-mdm-in-office-365-dd892318-bc44-4eb1-af00-9db5430be3cd)
- [Настройка служб и приложений](configure-services-and-applications.md)
