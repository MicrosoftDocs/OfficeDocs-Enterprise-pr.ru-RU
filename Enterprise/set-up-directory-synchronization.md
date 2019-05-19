---
title: Настройка синхронизации службы каталогов для Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
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
ms.openlocfilehash: 1798c54854bc5ecc82481aaabca3690e7212e135
ms.sourcegitcommit: 36e760407a1f4b18bc108134628ed9a8d3e35a8a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/17/2019
ms.locfileid: "34162482"
---
# <a name="set-up-directory-synchronization-for-office-365"></a>Настройка синхронизации службы каталогов для Office 365

Office 365 использует клиент Azure Active Directory (Azure AD) для хранения удостоверений для проверки подлинности и разрешений на доступ к облачным ресурсам и управления ими. 

Если у вас есть локальные доменные службы Active Directory (AD DS), вы можете синхронизировать учетные записи пользователей доменных служб Active Directory, группы и контакты с клиентом Azure AD вашей подписки на Office 365. Это гибридное удостоверение для Office 365. Вот ее компоненты.

![](./media/about-office-365-identity/hybrid-identity.png)

Azure AD Connect работает на локальном сервере и синхронизирует доменные службы Active Directory с клиентом Azure AD. Помимо синхронизации службы каталогов, можно также указать следующие параметры проверки подлинности.

- Синхронизация хэша паролей (ФС)

  Azure AD выполняет проверку подлинности.

- Сквозная проверка подлинности (PTA)

  В Azure AD доменные службы Active Directory выполняют проверку подлинности.

- Федеративная проверка подлинности

  Azure AD перенаправляет клиентский компьютер, запрашивающий проверку подлинности, для связи с другим поставщиком удостоверений.

Более подробную информацию можно узнать в статье [гибридные удостоверения](plan-for-directory-synchronization.md) .
  
## <a name="1-review-prerequisites-for-azure-ad-connect"></a>1. Ознакомьтесь с требованиями для Azure AD Connect.

Вы получаете бесплатную подписку на Azure AD с подпиской на Office 365. Когда вы настраиваете синхронизацию службы каталогов, вы сможете установить Azure AD Connect на одном из локальных серверов.
  
Для Office 365 вам потребуется:
  
- Проверка локального домена. Мастер Azure AD Connect поможет вам выполнить следующие шаги.
- Получите имена пользователей и пароли для учетных записей администраторов клиента Office 365 и AD DS.

Для локального сервера, на котором вы устанавливаете Azure AD Connect, вам потребуются следующие компоненты:
  
|**Серверная операционная система**|**другое программное обеспечение. **|
|:-----|:-----|
|Windows Server 2012 R2 и более поздние версии | -PowerShell устанавливается по умолчанию, никакие действия не требуются.  <br> – NET 4.5.1 и более поздние версии предлагаются через обновление Windows. Убедитесь, что установлены последние обновления для Windows Server на панели управления. |
|Windows Server 2008 R2 с пакетом обновления 1 (SP1) * * или Windows Server 2012 | — Последняя версия PowerShell доступна в Windows Management Framework 4,0. Выполните поиск в [центре загрузки Майкрософт](https://go.microsoft.com/fwlink/p/?LinkId=717996).  <br> .NET 4.5.1 и более поздние версии доступны в [центре загрузки Майкрософт](https://go.microsoft.com/fwlink/p/?LinkId=717996). |
|Windows Server 2008 | -Последняя поддерживаемая версия PowerShell доступна в Windows Management Framework 3,0, которая доступна в [центре загрузки Майкрософт](https://go.microsoft.com/fwlink/p/?LinkId=717996).  <br> .NET 4.5.1 и более поздние версии доступны в [центре загрузки Майкрософт](https://go.microsoft.com/fwlink/p/?LinkId=717996). |

Ознакомьтесь с требованиями [для Azure Active Directory Connect](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-prerequisites) для получения сведений о требованиях к оборудованию, программному обеспечению, учетным записям и разрешениям, ТРЕБОВАНИЯх SSL-сертификатов и ограничению объектов для Azure AD Connect.
  
Вы также можете ознакомиться с журналом выпусков для [версии](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-version-history) Azure AD Connect, чтобы узнать, какие из них включены и исправлены в каждом выпуске.

## <a name="2-install-azure-ad-connect-and-configure-directory-synchronization"></a>2. Установка Azure AD Connect и Настройка синхронизации службы каталогов

Прежде чем приступать к работе, убедитесь в том, что у вас есть:

- Имя пользователя и пароль глобального администратора Office 365
- Имя пользователя и пароль администратора домена доменных служб Active Directory
- Какой метод проверки подлинности (ФС, ПТА, федеративный)
- Необходимость использования [единого входа Azure AD с единым входом (SSO)](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-sso)

Выполните следующие действия:

1. Войдите в [центр администрирования Microsoft 365](https://admin.microsoft.com) (https://admin.microsoft.com) и выберите **Пользователи** \> **Активные пользователи** на левой панели навигации).
2. В центре администрирования на странице **Активные пользователи** выберите пункт **больше** \> **синхронизации службы каталогов**.

    ![В меню Дополнительно выберите пункт Синхронизация службы каталогов.](media/dc6669e5-c01b-471e-9cdf-04f5d44e1c4b.png)
  
3. На странице " **Подготовка Active Directory** " выберите ссылку **скачать средство Microsoft Azure Active Directory Connect** , чтобы приступить к работе. 
4. Выполните действия, описанные в статье [план установки работоспособности Azure AD Connect и Azure AD Connect](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-roadmap).

## <a name="3-finish-setting-up-domains"></a>3. Завершение настройки доменов

Выполните действия, описанные в статье [CREATE DNS Records for Office 365, когда вы управляете записями DNS](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23) для завершения настройки доменов.

## <a name="next-step"></a>Следующий шаг

[Назначение лицензий учетным записям пользователей](assign-licenses-to-user-accounts.md).
