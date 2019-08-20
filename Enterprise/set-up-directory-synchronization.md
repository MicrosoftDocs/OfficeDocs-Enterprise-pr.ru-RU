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
description: Узнайте, как настроить синхронизацию каталогов между Office 365 и локальной службой Active Directory.
ms.openlocfilehash: 1798c54854bc5ecc82481aaabca3690e7212e135
ms.sourcegitcommit: 36e760407a1f4b18bc108134628ed9a8d3e35a8a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/17/2019
ms.locfileid: "34162482"
---
# <a name="set-up-directory-synchronization-for-office-365"></a>Настройка синхронизации службы каталогов для Office 365

В Office 365 используется клиент Azure Active Directory (Azure AD) для хранения удостоверений и управления ими для проверки подлинности и разрешений на доступ к облачным ресурсам. 

Если у вас есть локальные доменные службы Active Directory, вы можете синхронизировать учетные записи пользователей, группы и контакты доменных служб Active Directory с клиентом Azure AD для вашей подписки на Office 365. Это гибридное удостоверение для Office 365. Ниже перечислены его компоненты.

![](./media/about-office-365-identity/hybrid-identity.png)

Azure AD Connect запускается на локальном сервере и синхронизирует ваши доменные службы Active Directory с клиентом Azure AD. Одновременно с синхронизацией каталогов вы можете также задать приведенные ниже параметры проверки подлинности.

- Синхронизация хэша паролей (PHS)

  Проверка подлинности выполняется с помощью Azure AD.

- Сквозная проверка подлинности (PTA)

  Проверка подлинности выполняется с помощью доменных служб Aсtive Directory в Azure AD.

- Федеративная проверка подлинности

  Azure AD перенаправляет клиентский компьютер, запрашивающий проверку подлинности, установить контакт с другим поставщиком удостоверений.

Дополнительные сведения см. в статье [Гибридные удостоверения](plan-for-directory-synchronization.md).
  
## <a name="1-review-prerequisites-for-azure-ad-connect"></a>1. Необходимые условия для Azure AD Connect

Вы получаете бесплатную подписку на Azure AD вместе со своей подпиской на Office 365. При настройке синхронизации каталогов вы устанавливаете Azure AD Connect на одном из локальных серверов.
  
Для Office 365 вам потребуется
  
- Проверка локального домена. Мастер Azure AD Connect направляет этот процесс.
- Получение имен пользователей и паролей для учетных записей администратора клиента Office 365 и доменных служб Active Directory.

Для локального сервера, на котором выполняется установка Azure AD Connect, вам потребуется
  
|**Серверная ОС**|**Другое ПО**|
|:-----|:-----|
|Windows Server 2012 R2 и более поздних версий | - PowerShell устанавливается по умолчанию; никаких действий не требуется.  <br> - Net 4.5.1 и более поздние выпуски можно получить через Центр обновления Windows. На панели управления убедитесь в том, что установлены последние обновления для Windows Server. |
|Windows Server 2008 R2 с пакетом обновления 1 (SP1)** или Windows Server 2012 | - Последняя версия PowerShell доступна в составе платформы Windows Management Framework 4.0. Найти ее можно в [Центре загрузки Майкрософт](https://go.microsoft.com/fwlink/p/?LinkId=717996).  <br> - .Net 4.5.1 и более поздние выпуски доступны в [Центре загрузки Майкрософт](https://go.microsoft.com/fwlink/p/?LinkId=717996). |
|Windows Server 2008 | Последняя поддерживаемая версия PowerShell доступна в составе платформы Windows Management Framework 3.0, которую можно найти в [Центре загрузки Майкрософт](https://go.microsoft.com/fwlink/p/?LinkId=717996).  <br> - .Net 4.5.1 и более поздние выпуски доступны в [Центре загрузки Майкрософт](https://go.microsoft.com/fwlink/p/?LinkId=717996). |

Более подробно ознакомиться с требованиями к оборудованию, программному обеспечению, учетным записям, разрешениям и SSL-сертификатам, а также с ограничениями на объекты для Azure AD Connect можно в статье [Необходимые условия для Azure AD Connect](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-prerequisites).
  
Вы также можете ознакомиться с [журналом выпуска версий](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-version-history) Azure AD Connect, чтобы выяснить, что добавилось или было исправлено в каждой версии.

## <a name="2-install-azure-ad-connect-and-configure-directory-synchronization"></a>2. Установка Azure AD Connect и настройка синхронизации каталогов.

Перед началом вам необходимо иметь

- Имя пользователя и пароль глобального администратора Office 365.
- Имя пользователя и пароль администратора доменных служб Active Directory
- Метод проверки подлинности (синхронизация хэша паролей, сквозная или федеративная)
- Либо [Простой единый вход Azure AD](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-sso) по вашему желанию.

Выполните приведенные ниже действия.

1. Войдите в [Центр администрирования Microsoft 365](https://admin.microsoft.com) https://admin.microsoft.com)и в области навигации слева выберите пункты **Пользователи** \> ** > Активные пользователи**.
2. В предварительной версии Центра администрирования на странице **Активные пользователи** выберите **Еще** > \>**Синхронизация службы каталогов**.

    ![В меню "Еще" выберите элемент "Синхронизация службы каталогов"](media/dc6669e5-c01b-471e-9cdf-04f5d44e1c4b.png)
  
3. На странице **Подготовка Active Directory** щелкните ссылку **Скачать средство Microsoft Azure Active Directory Connect**, чтобы начать работу. 
4. Выполните действия в статье [План установки Azure AD Connect и Azure AD Connect Health](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-roadmap).

## <a name="3-finish-setting-up-domains"></a>3. Завершение настройки доменов

Инструкции по завершению настройки доменов см. в статье [Создание записей DNS для Office 365 при самостоятельном управлении записями DNS](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23).

## <a name="next-step"></a>Следующий этап

[Назначение лицензий учетным записям пользователей](assign-licenses-to-user-accounts.md).
