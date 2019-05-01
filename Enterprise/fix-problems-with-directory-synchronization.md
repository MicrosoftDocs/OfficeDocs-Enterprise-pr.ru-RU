---
title: Устранение проблем с синхронизацией службы каталогов для Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MBS150
ms.assetid: 79c43023-5a47-45ae-8068-d8a26eee6bc2
description: В этой статье описываются распространенные причины проблем с синхронизацией службы каталогов в Office 365, а также способы их устранения.
ms.openlocfilehash: a5c4b58dd856158b00605f39d8a66b48488086b2
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487473"
---
# <a name="fixing-problems-with-directory-synchronization-for-office-365"></a>Устранение проблем с синхронизацией службы каталогов для Office 365

С помощью синхронизации службы каталогов можно продолжать управлять локальными пользователями и группами и синхронизировать добавления, удаления и изменения в облаке. Однако программа установки немного сложна, и иногда может быть трудно определить источник проблем. У нас есть ресурсы, которые помогут вам определить потенциальные проблемы и устранить их.
  
## <a name="how-do-i-know-if-something-is-wrong"></a>Как узнать, что что-то не так?

Первое указание на то, что что-то пошло не так, когда плитка состояния DirSync в центре администрирования Майкрософт 365 указывает на наличие проблем:
  
![Плитка состояния DirSync в предварительной версии центра администрирования](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
Кроме того, вы получите почту из Office 365, которая указывает на то, что клиент обнаружил ошибки синхронизации службы каталогов, в альтернативную электронную почту и электронную почту администратора. Подробные сведения см. [в статье определение ошибок синхронизации каталогов в Office 365](identify-directory-synchronization-errors.md).
  
## <a name="how-do-i-get-azure-active-directory-connect-tool"></a>Как получить средство Azure Active Directory Connect?

в [центре администрирования Microsoft 365](https://admin.microsoft.com)перейдите к разделу * * пользователи * * \> **активные пользователи**. Откройте меню **Дополнительно** и выберите пункт **Синхронизация службы каталогов**. 
  
![В меню Дополнительно выберите пункт Синхронизация службы каталогов.](media/dc6669e5-c01b-471e-9cdf-04f5d44e1c4b.png)
  
Следуйте [инструкциям мастера](set-up-directory-synchronization.md) , чтобы скачать Azure AD Connect. 
  
Если вы по-прежнему используете Azure Active Directory Sync (DirSync), ознакомьтесь с [сообщениями об ошибках мастера установки и настройки средства синхронизации Azure Active Directory в Office 365](https://go.microsoft.com/fwlink/p/?LinkId=396717) для получения сведений о требованиях к системе для установки DirSync, необходимые разрешения и устранение распространенных ошибок. 
  
Чтобы обновить синхронизацию Azure Active Directory с помощью Azure AD Connect, ознакомьтесь [с инструкциями по обновлению](https://go.microsoft.com/fwlink/p/?LinkId=733240).
  
## <a name="resolving-common-causes-of-problems-with-directory-synchronization-in-office-365"></a>Устранение распространенных причин проблем с синхронизацией службы каталогов в Office 365

### <a name="synchronized-objects-arent-appearing-or-updating-online-or-im-getting-synchronization-error-reports-from-the-service"></a>**Синхронизированные объекты не отображаются или не обновляются в Интернете, или я получаю отчеты об ошибках синхронизации от службы.**

- [Устойчивость к синхронизации удостоверений и дублирование атрибутов](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency)

### <a name="i-have-an-alert-in-the-admin-center-or-am-receiving-automated-emails-that-there-hasnt-been-a-recent-synchronization-event"></a>**У меня есть оповещение в центре администрирования или приходят автоматические сообщения о том, что последнее событие синхронизации еще не выполнялось**
- [Устранение проблем с подключением к Azure AD Connect](https://docs.microsoft.com/azure/active-directory/hybrid/tshoot-connect-connectivity)
- [Учетные записи и разрешения для Azure AD Connect](https://go.microsoft.com/fwlink/p/?LinkId=820598)
- [Синхронизация Azure AD Connect: Управление учетной записью службы Azure AD](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-azureadaccount)
- [Синхронизация службы каталогов с Azure Active Directory закончится, или вы будете предупреждать о том, что синхронизация не была зарегистрирована более суток](https://support.microsoft.com/help/2882421/directory-synchronization-to-azure-active-directory-stops-or-you-re-warned-that-sync-hasn-t-registered-in-more-than-a-day)

### <a name="password-hashes-arent-synchronizing-or-im-seeing-an-alert-in-the-admin-center-that-there-hasnt-been-a-recent-password-hash-synchronization"></a>**Хэши паролей не синхронизируются, или я вижу оповещение в центре администрирования, что еще не выполнялась Последняя синхронизация хэша паролей**
- [Реализация синхронизации хэша паролей с синхронизацией Azure AD Connect](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization)

### <a name="im-seeing-an-alert-that-object-quota-exceeded"></a>**Я вижу предупреждение о превышении квоты объекта**
- У нас есть встроенная квота объекта, помогающая защитить службу. Если в вашем каталоге слишком много объектов, которые необходимо синхронизировать с Office 365, вам потребуется [обратиться в службу поддержки продуктов для бизнеса](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) , чтобы увеличить квоту.

### <a name="i-need-to-know-which-attributes-are-synchronized"></a>**Мне нужно знать, какие атрибуты синхронизированы**
- Вы можете найти список всех атрибутов, которые синхронизируются между локальной средой и облаком [непосредственно](https://go.microsoft.com/fwlink/p/?LinkId=396719).

### <a name="i-cant-manage-or-remove-objects-that-were-synchronized-to-the-cloud"></a>**Не удается управлять или удалять объекты, синхронизированные с облаком**
- Вы готовы управлять объектами только в облаке? Есть ли в облаке объект, который был удален локально, но в облаке он застрял? Ознакомьтесь с этой статьей [об устраненИи неполадок во время синхронизации](https://go.microsoft.com/fwlink/p/?linkid=842044) и [поддержки](https://go.microsoft.com/fwlink/p/?LinkId=396720) , чтобы получить рекомендации по устранению этих проблем.

### <a name="i-got-an-error-message-that-my-company-has-exceeded-the-number-of-objects-that-can-be-synchronized"></a>**Получено сообщение об ошибке, когда в компании превышено количество объектов, которые можно синхронизировать**
- Подробнее об этой статье можно узнать [здесь](https://go.microsoft.com/fwlink/p/?LinkId=396721).
   
## <a name="other-resources"></a>Другие ресурсы

- [Сценарий для устранения повторяющихся имен участников-пользователей](https://go.microsoft.com/fwlink/p/?LinkId=396725)
    
- [Подготовка домена, не поддерживающего маршрутизацию (например, локального домена), для синхронизации службы каталогов](prepare-a-non-routable-domain-for-directory-synchronization.md)
    
- [Скрипт для подсчета итоговых синхронизированных объектов](https://go.microsoft.com/fwlink/p/?LinkId=396726)
    
- [Устранение неполадок AD FS 2,0](https://go.microsoft.com/fwlink/p/?LinkId=396727)
    
- [Использование PowerShell для исправления пустых атрибутов DisplayName для групп с включенной поддержкой почты](https://go.microsoft.com/fwlink/p/?LinkId=396728)
    
- [Использование PowerShell для исправления повторяющегося имени участника-пользователя](https://go.microsoft.com/fwlink/p/?LinkId=396730)
    
- [Использование PowerShell для исправления дублирующихся адресов электронной почты](https://go.microsoft.com/fwlink/p/?LinkId=396731)
    
## <a name="diagnostic-tools"></a>Средства диагностики

[Средство IDFix](prepare-directory-attributes-for-synch-with-idfix.md) используется для выполнения обнаружения и исправления объектов Identity и их атрибутов в локальной среде Active Directory при подготовке к миграции в Office 365. IDFix предназначен для администраторов Active Directory, ответственных за DirSync, с помощью службы Office 365. 

[Скачайте средство IDFix](https://go.microsoft.com/fwlink/p/?LinkId=396718) из центра загрузки Майкрософт.