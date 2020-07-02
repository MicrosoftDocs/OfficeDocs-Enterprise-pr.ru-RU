---
title: Устранение проблем с синхронизацией службы каталогов для Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MBS150
ms.assetid: 79c43023-5a47-45ae-8068-d8a26eee6bc2
description: В этой статье описаны распространенные причины проблем с синхронизацией службы каталогов в Office 365, а также несколько способов их решения.
ms.openlocfilehash: d9e390a7230499f724ebbdae592264a850dd9418
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998037"
---
# <a name="fixing-problems-with-directory-synchronization-for-microsoft-365"></a>Устранение проблем с синхронизацией службы каталогов для Microsoft 365

С помощью синхронизации службы каталогов можно продолжать локально управлять пользователями и группами и синхронизировать добавления, удаления и изменения с облаком. Тем не менее ее настройка немного сложна и иногда бывает трудно определить причину проблемы. Мы предлагаем ресурсы, которые помогут вам выявить потенциальные проблемы и устранить их.
  
## <a name="how-do-i-know-if-something-is-wrong"></a>Как узнать, что что-то пошло не так?

Первое указание на то, что что-то пошло не так, когда плитка состояния DirSync в центре администрирования Майкрософт 365 указывает на наличие проблемы.
  
Кроме того, вы получите почту из Microsoft 365, которая указывает, что клиент обнаружил ошибки синхронизации службы каталогов, в альтернативную электронную почту и электронную почту администратора. Подробные сведения см. [в статье определение ошибок синхронизации каталогов в Microsoft 365](identify-directory-synchronization-errors.md).
  
## <a name="how-do-i-get-azure-active-directory-connect-tool"></a>Как получить средство Azure Active Directory Connect?

В [центре администрирования Microsoft 365](https://admin.microsoft.com)перейдите к разделу **Пользователи** \> **Активные пользователи**. Щелкните меню **больше** (три точки) и выберите пункт **Синхронизация службы каталогов**. 
  
Следуйте [инструкциям в мастере](set-up-directory-synchronization.md), чтобы скачать Azure AD Connect. 
  
Если вы по-прежнему используете синхронизацию Azure Active Directory (DirSync), ознакомьтесь с [сообщениями об ошибках мастера установки и настройки средства синхронизации Azure Active Directory в Microsoft 365](https://go.microsoft.com/fwlink/p/?LinkId=396717) для получения сведений о требованиях к системе для установки DirSync, необходимых разрешений и устранении распространенных ошибок. 
  
Чтобы выполнить обновление из Azure AD Sync в Azure AD Connect, ознакомьтесь [с инструкциями по обновлению](https://go.microsoft.com/fwlink/p/?LinkId=733240).
  
## <a name="resolving-common-causes-of-problems-with-directory-synchronization-in-microsoft-365"></a>Устранение распространенных причин проблем с синхронизацией службы каталогов в Microsoft 365

### <a name="synchronized-objects-arent-appearing-or-updating-online-or-im-getting-synchronization-error-reports-from-the-service"></a>**Синхронизированные объекты не отображаются или не обновляются в режиме онлайн. Или служба возвращает отчеты об ошибках синхронизации.**

- [Синхронизация удостоверений и устойчивость повторяющихся атрибутов](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency)

### <a name="i-have-an-alert-in-the-admin-center-or-am-receiving-automated-emails-that-there-hasnt-been-a-recent-synchronization-event"></a>**Я получаю оповещение в Центре администрирования. Или на мой электронный адрес приходят автоматические сообщения о том, что в последнее время синхронизация не выполнялась**
- [Устранение неполадок подключения с помощью Azure AD Connect](https://docs.microsoft.com/azure/active-directory/hybrid/tshoot-connect-connectivity)
- [Azure AD Connect: учетные записи и разрешения](https://go.microsoft.com/fwlink/p/?LinkId=820598)
- [Синхронизация Azure AD Connect: управление учетной записью службы Azure AD](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-azureadaccount)
- [Синхронизация каталогов с Azure Active Directory остановлена или более суток не зарегистрировано попыток синхронизации](https://support.microsoft.com/help/2882421/directory-synchronization-to-azure-active-directory-stops-or-you-re-warned-that-sync-hasn-t-registered-in-more-than-a-day)

### <a name="password-hashes-arent-synchronizing-or-im-seeing-an-alert-in-the-admin-center-that-there-hasnt-been-a-recent-password-hash-synchronization"></a>**Не синхронизируются пароли. Или в Центре администрирования Office 365 появляется оповещение о том, что в последнее время синхронизация паролей не выполнялась**
- [Реализация синхронизации хэшированных паролей в службе синхронизации Azure AD Connect](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization)

### <a name="im-seeing-an-alert-that-object-quota-exceeded"></a>**Появляется оповещение о том, что превышена квота на объекты.**
- Для защиты службы используется встроенная квота на объекты. Если в вашем каталоге слишком много объектов, которые необходимо синхронизировать с Microsoft 365, вам потребуется [обратиться в службу поддержки продуктов для бизнеса](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) , чтобы увеличить квоту.

### <a name="i-need-to-know-which-attributes-are-synchronized"></a>**Мне нужно знать, какие атрибуты синхронизируются**
- Список всех атрибутов, которые синхронизируются между локальной средой и облаком, можно найти [здесь](https://go.microsoft.com/fwlink/p/?LinkId=396719).

### <a name="i-cant-manage-or-remove-objects-that-were-synchronized-to-the-cloud"></a>**Не удается управлять объектами, синхронизированными с облаком, и удалять их**
- Вы готовы управлять объектами только в облаке? Или вы удалили объект локально, но он все еще существует в облаке? Ознакомьтесь с этой статьей [Устранение ошибок синхронизации во время синхронизации](https://go.microsoft.com/fwlink/p/?linkid=842044) и [справочной статьей](https://go.microsoft.com/fwlink/p/?LinkId=396720), чтобы получить инструкции по устранению этих проблем.

### <a name="i-got-an-error-message-that-my-company-has-exceeded-the-number-of-objects-that-can-be-synchronized"></a>**Появляется сообщение об ошибке, в котором говорится, что в компании превышено количество объектов, которые можно синхронизировать.**
- Подробнее об этой проблеме вы можете узнать [здесь](https://go.microsoft.com/fwlink/p/?LinkId=396721).
   
## <a name="other-resources"></a>Другие ресурсы

- [Сценарий для устранения повторяющихся имен участников-пользователей](https://go.microsoft.com/fwlink/p/?LinkId=396725)
    
- [Сведения о подготовке немаршрутизируемого домена (например, .local) для синхронизации службы каталогов](prepare-a-non-routable-domain-for-directory-synchronization.md)
    
- [Сценарий для подсчета общего числа синхронизированных объектов](https://go.microsoft.com/fwlink/p/?LinkId=396726)
    
- [Устранение неполадок AD FS 2.0](https://go.microsoft.com/fwlink/p/?LinkId=396727)
    
- [Использование PowerShell для исправления пустых атрибутов DisplayName для групп, поддерживающих почту](https://go.microsoft.com/fwlink/p/?LinkId=396728)
    
- [Использование PowerShell для устранения повторяющихся имен участников-пользователей](https://go.microsoft.com/fwlink/p/?LinkId=396730)
    
- [Использование PowerShell для устранения повторяющихся адресов электронной почты](https://go.microsoft.com/fwlink/p/?LinkId=396731)
    
## <a name="diagnostic-tools"></a>Средства диагностики

[Средство IDFix](prepare-directory-attributes-for-synch-with-idfix.md) используется для выполнения обнаружения и исправления объектов Identity и их атрибутов в локальной среде Active Directory при подготовке к миграции в Microsoft 365. IDFix предназначен для администраторов Active Directory, ответственных за синхронизацию каталогов со службой Microsoft 365. 

[Скачайте средство IDFix](https://go.microsoft.com/fwlink/p/?LinkId=396718) из Центра загрузки Майкрософт.