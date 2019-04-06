---
title: Настройка синхронизации каталогов для Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED15
- MBS150
- BCS160
ms.assetid: 1b3b5318-6977-42ed-b5c7-96fa74b08846
description: Узнайте, как настроить синхронизацию каталогов между Office 365 и локальной службой Active Directory.
ms.openlocfilehash: 6d635dbcacb5a1c6c6c9c202f2ece4fac35558a4
ms.sourcegitcommit: 29f937b7430c708c9dbec23bdc4089e86c37c225
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2019
ms.locfileid: "31001752"
---
# <a name="set-up-directory-synchronization-for-office-365"></a>Настройка синхронизации каталогов для Office 365

В Office 365 для управления пользователями используется облачная служба управления удостоверениями Azure Active Directory. Вы также можете интегрировать локальную службу Active Directory с Azure AD, синхронизируя локальную среду с Office 365. После настройки синхронизации можно использовать проверку подлинности пользователей в Azure AD или в локальном каталоге.
  
## <a name="office-365-directory-synchronization"></a>Синхронизация каталогов Office 365

Вы можете использовать синхронизированное удостоверение или федеративный идентификатор между локальной организацией и Office 365. С помощью синхронизированного удостоверения вы управляете локальными пользователями и проходят проверку подлинности с помощью Azure AD, когда они используют один и тот же пароль в облаке в локальной среде. Это наиболее распространенный сценарий синхронизации каталогов. Сквозная проверка подлинности или федеративного удостоверения позволяет управлять локальными пользователями и проходить их проверку подлинности в локальном каталоге. Для федеративного удостоверения требуется дополнительная настройка, и пользователи могут выполнять только один вход. Для получения дополнительных сведений ознакомьтесь со сведениями [об удостоверенИи Office 365 и Azure Active Directory](about-office-365-identity.md).
  
## <a name="want-to-upgrade-from-windows-azure-active-directory-sync-dirsync-to-azure-active-directory-connect"></a>Хотите обновить синхронизацию с Windows Azure Active Directory (DirSync) до Azure Active Directory Connect?

Если вы используете DirSync и хотите выполнить обновление, перейдите к [Azure.com](https://azure.com) для [получения инструкций](https://go.microsoft.com/fwlink/p/?LinkId=733240)по обновлению.
  
## <a name="prerequisites-for-azure-ad-connect"></a>Необходимые условия для Azure AD Connect

Вы получаете бесплатную подписку на Azure AD с вашей подпиской на Office 365. Когда вы настраиваете синхронизацию службы каталогов, вы сможете установить Azure Active Directory Connect на одном из локальных серверов.
  
Для Office 365 вам потребуется выполнить следующие действия:
  
- Проверка локального домена (процедура поможет вам выполнить указанные ниже действия).
- [Назначьте роли администратора в office 365 для бизнес](https://support.office.com/article/EAC4D046-1AFD-4F1A-85FC-8219C79E1504) -разрешений для клиента Office 365 и локального каталога Active Directory.

Для локального сервера, на котором вы устанавливаете Azure AD Connect, вам потребуется следующее программное обеспечение:
  
|**Серверная операционная система**|**другое программное обеспечение. **|
|:-----|:-----|
|**Windows Server 2012 R2** | -PowerShell устанавливается по умолчанию, никакие действия не требуются.  <br> – NET 4.5.1 и более поздние версии предлагаются через обновление Windows. Убедитесь, что установлены последние обновления для Windows Server на панели управления. |
|**Windows server 2008 R2 с пакетом обновления 1 (SP1)** или **Windows Server 2012** | — Последняя версия PowerShell доступна в Windows Management Framework 4,0. Выполните поиск в [центре загрузки Майкрософт](https://go.microsoft.com/fwlink/p/?LinkId=717996).  <br> .NET 4.5.1 и более поздние версии доступны в [центре загрузки Майкрософт](https://go.microsoft.com/fwlink/p/?LinkId=717996). |
|**Windows Server 2008** | -Последняя поддерживаемая версия PowerShell доступна в Windows Management Framework 3,0, которая доступна в [центре загрузки Майкрософт](https://go.microsoft.com/fwlink/p/?LinkId=717996).  <br> .NET 4.5.1 и более поздние версии доступны в [центре загрузки Майкрософт](https://go.microsoft.com/fwlink/p/?LinkId=717996). |

> [!NOTE]
> Если вы используете Azure Active Directory DirSync, максимальное число членов группы рассылки, которые можно синхронизировать из локального каталога Active Directory с Azure Active Directory, — 15 000. Для Azure AD Connect это число равно 50 000.
  
Чтобы тщательно проанализировать требования к оборудованию, программному обеспечению, учетным записям и разрешениям, требования к сертификатам SSL и ограничению объектов для Azure AD Connect, прочитайте [необходимые компоненты для Azure Active Directory Connect](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-prerequisites).
  
Вы также можете ознакомиться с журналом выпусков для [версии](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-version-history) Azure AD Connect, чтобы узнать, какие из них включены и исправлены в каждом выпуске.

## <a name="to-set-up-directory-synchronization"></a>Настройка синхронизации службы каталогов

1. войдите в [центр администрирования Microsoft 365](https://admin.microsoft.com) и выберите **пользователи** \> **активные пользователи** на левой панели навигации.
2. В центре администрирования на странице **Активные пользователи** выберите пункт **больше** \> **синхронизации службы каталогов**.

    ![В меню Дополнительно выберите пункт Синхронизация службы каталогов.](media/dc6669e5-c01b-471e-9cdf-04f5d44e1c4b.png)
  
3. На странице " **Подготовка Active Directory** " выберите ссылку **скачать средство Microsoft Azure Active Directory Connect** , чтобы приступить к работе. Дополнительные сведения о процессе установки Azure Active Directory Connect можно найти в статье [план установки Azure AD Connect и Azure AD Connect Health](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-roadmap).

## <a name="assign-licenses-to-synchronized-users"></a>Назначение лицензий синхронизированным пользователям

После синхронизации пользователей с Office 365 они будут созданы, но вам нужно назначить им лицензии, чтобы они могли использовать функции Office 365, такие как почта. Инструкции приведены в статье [Назначение лицензий пользователям в Office 365 для бизнеса](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc).

## <a name="finish-setting-up-domains"></a>Завершение настройки доменов

Выполните действия, описанные в статье [CREATE DNS Records for Office 365, когда вы управляете записями DNS](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23) для завершения настройки доменов.