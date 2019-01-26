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
search.appverid:
- MET150
- MOE150
- MED15
- MBS150
- BCS160
ms.assetid: 1b3b5318-6977-42ed-b5c7-96fa74b08846
description: Узнайте, как Настройка синхронизации службы каталогов в Office 365 и локальной Active Directory.
ms.openlocfilehash: f2cd29e7a81854bb64f6317aa2b41e674ae22df4
ms.sourcegitcommit: a4546e1f3fe9e8e25a56ed350400d51eb7dd7f83
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "29555445"
---
# <a name="set-up-directory-synchronization-for-office-365"></a>Настройка синхронизации каталогов для Office 365

Office 365 использует службы управления удостоверения пользователя на основе облака Azure Active Directory для управления пользователями. Также можно интегрировать локальной Active Directory с Azure AD, синхронизацию локальной среды с Office 365. После настройки синхронизации можно указать, кто имеет свои происходят в Azure AD или в локальном каталоге проверки подлинности пользователей.
  
## <a name="office-365-directory-synchronization"></a>Синхронизация службы каталогов Office 365

Можно использовать либо синхронизированного identity или федеративных удостоверений между локальной организацией и Office 365. С синхронизированной удостоверения для управления пользователями на локальную и Azure AD, при использовании тот же пароль в облаке как локальный проходят проверку подлинности. Это наиболее распространенные сценарии синхронизации службы каталогов. Сквозной проверки подлинности или федеративных удостоверений позволяет управлять пользователями на локальную и локального каталога проходят проверку подлинности. Федеративное удостоверение требуется дополнительная настройка и позволяет пользователям только входа в один раз. Для получения дополнительных сведений прочитайте [Общие сведения об Office 365 удостоверения и Azure Active Directory](about-office-365-identity.md).
  
## <a name="want-to-upgrade-from-windows-azure-active-directory-sync-dirsync-to-azure-active-directory-connect"></a>Хотите выполнить обновление до синхронизации Windows Azure Active Directory (DirSync) для Azure Active Directory подключения?

Если в настоящее время с помощью DirSync и хотите обновить, не забывайте также через посещать [azure.com](https://azure.com) для [инструкции по обновлению](https://go.microsoft.com/fwlink/p/?LinkId=733240).
  
## <a name="prerequisites-for-azure-ad-connect"></a>Необходимые условия для Azure AD подключения

Получите бесплатную подписка на Azure AD с подписки Office 365. При настройке синхронизации службы каталогов на одном из локальных серверов будет установлено подключение Azure Active Directory.
  
Для Office 365 требуется:
  
- Проверьте локальный домен (процедура поможет это).
- Права на [Назначение ролей администратора в Office 365 для бизнеса](https://support.office.com/article/EAC4D046-1AFD-4F1A-85FC-8219C79E1504) для клиента Office 365 и локальной службы каталогов Active Directory.

Для вашего на локальный сервер, на котором устанавливается подключение Azure AD необходимо следующее программное обеспечение:
  
|**Операционной системы**|**другое программное обеспечение. **|
|:-----|:-----|
|**Windows Server 2012 R2** | -PowerShell устанавливается по умолчанию, никаких действий не требуется.  <br> -Net 4.5.1 и более поздних версий, предлагаемых через Центр обновления Windows. Убедитесь в том, что установлены последние обновления для Windows Server в панели управления. |
|**Windows Server 2008 R2 с пакетом обновления 1 (SP1)** или **Windows Server 2012 г.** | -Последняя версия PowerShell доступна в Windows Management Framework 4.0. Поиск на [Центр загрузки Майкрософт](https://go.microsoft.com/fwlink/p/?LinkId=717996).<br> -.net 4.5.1 и более поздних версий, доступны в [Центре загрузки Майкрософт](https://go.microsoft.com/fwlink/p/?LinkId=717996). |
|**Windows Server 2008** | -Последняя поддерживаемая версия PowerShell доступна в Windows Management Framework 3.0, доступные в [Центре загрузки Майкрософт](https://go.microsoft.com/fwlink/p/?LinkId=717996).  <br> -.net 4.5.1 и более поздних версий, доступны в [Центре загрузки Майкрософт](https://go.microsoft.com/fwlink/p/?LinkId=717996). |

> [!NOTE]
> Если вы используете Azure Active Directory DirSync, максимальное число членов группы рассылки, которые можно синхронизировать из локального Active Directory для Azure Active Directory — 15 000. Для Azure AD "Подключение" Этот номер является 50 000. 
  
Более внимательно изучите оборудование, программное обеспечение, учетной записи и требования к разрешениям, требования к сертификатам SSL и ограничения объекта для Azure AD "Подключение" чтение [Необходимые условия для Azure Active Directory подключение](https://go.microsoft.com/fwlink/p/?LinkId=716896).
  
Также можно обратиться к Azure AD подключить [версии версии обновлений](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-version-history) какой используется включены и фиксированной в каждой версии.

## <a name="to-set-up-directory-synchronization"></a>Настройка синхронизации службы каталогов

1. Войдите Центр администрирования Office 365 и выберите **пользователей,** \> **Активных пользователей** на левой панели навигации.
2. В центре администрирования Office 365 на странице **активных пользователей** выберите **Дополнительные** \> **синхронизации службы каталогов**.

    ![Выберите в меню Дополнительные синхронизации службы каталогов](media/dc6669e5-c01b-471e-9cdf-04f5d44e1c4b.png)
  
3. На странице **подготовки Active Directory** выберите ссылку **загрузить Microsoft Azure Active Directory подключение средство** для начала работы. Дополнительные сведения о процессе установки Azure Active Directory подключение видеть [Azure AD подключение и состояния подключения Azure AD план проведения установки](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-roadmap).

## <a name="assign-licenses-to-synchronized-users"></a>Назначение лицензий пользователям синхронизированного

После синхронизации пользователей с Office 365 их создания, но им необходимо назначить лицензий им, поэтому они могут использовать возможности Office 365, например почты. Сведения содержатся в разделе [Назначение лицензий для пользователей в Office 365 для бизнеса](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc).

## <a name="finish-setting-up-domains"></a>Завершите настройку доменов

Выполните действия, описанные в [статье Создание записей DNS для Office 365 при самостоятельном управлении записями DNS-записей](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23) для завершения установки домены.