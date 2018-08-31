---
title: Устранение проблем с синхронизацией каталогов для Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MBS150
ms.assetid: 79c43023-5a47-45ae-8068-d8a26eee6bc2
description: Описываются распространенные причины проблем с синхронизацией каталогов в Office 365 и предоставляет несколько методов для устранения неполадок и устраните их.
ms.openlocfilehash: ad3b6e27439354a2ede9b1a4b100e0f9e06148d3
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542376"
---
# <a name="fixing-problems-with-directory-synchronization-for-office-365"></a>Устранение проблем с синхронизацией каталогов для Office 365

С помощью синхронизации службы каталогов можно продолжить Управление пользователями и группами в локальной и синхронизация добавления, удаления и изменения в облако. Программа установки немного сложнее, но в некоторых случаях может быть трудно определить источник проблемы. У нас есть ресурсы, которые помогут вам определить потенциальные проблемы и их устранения.
  
## <a name="how-do-i-know-if-something-is-wrong"></a>Как узнать, что-то неверно?

Первым признаком того, что дает сбой при Плитка DirSync состояния в центре администрирования Office 365 указывает, что проблемы:
  
![Состояние DirSync плиток в предварительной версии центра администрирования](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
Также вы получите почты (альтернативного электронной почты и электронной почты администратора) с Office 365, который указывает, что клиент обнаружил ошибок синхронизации службы каталогов. Для получения дополнительных сведений см [Определение ошибок синхронизации службы каталогов в Office 365](identify-directory-synchronization-errors.md).
  
## <a name="how-do-i-get-azure-active-directory-connect-tool"></a>Как получить средство подключения Azure Active Directory?

В центре администрирования Office 365 перейдите к разделу ** пользователей ** \> **Активные пользователи**. Щелкните **Дополнительные** меню и выберите **синхронизации службы каталогов**. 
  
![Выберите в меню Дополнительные синхронизации службы каталогов](media/dc6669e5-c01b-471e-9cdf-04f5d44e1c4b.png)
  
В старой центра администрирования Office 365 перейдите к **пользователям** \> **Активных пользователей**и выберите **Настройка** синхронизации **Active Directory**. 
  
![Щелкните настроить синхронизации Active Directory](media/bd95492b-d65e-4072-a6ee-e562f5f566c3.png)
  
Следуйте [инструкциям мастера](set-up-directory-synchronization.md) , чтобы загрузить подключить Azure AD. 
  
Если вы используете по-прежнему синхронизации Azure Active Directory (DirSync), посмотрите на [Устранение неполадок при установке средства синхронизации Azure Active Directory и мастер настройки сообщений об ошибках в Office 365](https://go.microsoft.com/fwlink/p/?LinkId=396717) для получения сведений о требованиях к системе для установки DirSync, разрешения, необходимые и способы устранения наиболее распространенных ошибок. 
  
Для обновления от синхронизации Azure Active Directory подключение Azure AD, видеть [инструкциями по обновлению](https://go.microsoft.com/fwlink/p/?LinkId=733240).
  
## <a name="resolving-common-causes-of-problems-with-directory-synchronization-in-office-365"></a>Устранение распространенных причин проблем с синхронизацией каталогов в Office 365

### <a name="synchronized-objects-arent-appearing-or-updating-online-or-im-getting-synchronization-error-reports-from-the-service"></a>**Объекты не отображаются или обновление online или отчеты об ошибках синхронизации получены от службы.**

- [Устойчивость атрибут синхронизации и повторяющихся удостоверений](https://go.microsoft.com/fwlink/p/?LinkID=798300)

### <a name="i-have-an-alert-in-the-office-365-admin-center-or-am-receiving-automated-emails-that-there-hasnt-been-a-recent-synchronization-event"></a>**Я иметь оповещения в центре администрирования Office 365 или выводится сообщение, что не был недавнее событие синхронизации автоматическая отправка сообщения электронной почты**
- [Устранения неполадок подключения к с Azure AD подключение](https://go.microsoft.com/fwlink/p/?LinkId=820597)
- [Azure учетные записи подключения AD и разрешения](https://go.microsoft.com/fwlink/p/?LinkId=820598)
- [Azure AD подключение синхронизации: управление учетной записи службы Azure AD](https://go.microsoft.com/fwlink/p/?LinkId=820599)
- [Синхронизации службы каталогов останавливает Azure Active Directory или в случае предупреждение о том, что синхронизация не зарегистрировано в более одного дня](https://support.microsoft.com/help/2882421/directory-synchronization-to-azure-active-directory-stops-or-you-re-warned-that-sync-hasn-t-registered-in-more-than-a-day)

### <a name="password-hashes-arent-synchronizing-or-im-seeing-an-alert-in-the-office-365-admin-center-that-there-hasnt-been-a-recent-password-hash-synchronization"></a>**Не синхронизация хэши паролей или я вижу оповещения в центре администрирования Office 365, что не был последние хэш-функции синхронизации паролей**
- [Реализация хэш-функции синхронизации паролей с помощью Azure AD подключение синхронизации](https://go.microsoft.com/fwlink/p/?LinkId=820600)

### <a name="im-seeing-an-alert-that-object-quota-exceeded"></a>**Я вижу оповещение о превышении квот объектов**
- У нас есть квоты встроенный объект для защиты службы. При наличии слишком большого числа объектов в каталоге, которые необходимо синхронизировать с Office 365, потребуется увеличить квоту на почтовый [контакт поддержки продуктов бизнес](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) .

### <a name="i-need-to-know-which-attributes-are-synchronized"></a>**Необходимо определить, какие атрибуты синхронизируются**
- Список всех атрибутов, которые синхронизируются между локальной и облачных [право здесь](https://go.microsoft.com/fwlink/p/?LinkId=396719)можно найти.

### <a name="i-cant-manage-or-remove-objects-that-were-synchronized-to-the-cloud"></a>**Не удается управлять или удалить объекты, которые были синхронизированы с облаком**
- Все готово для управления объектами в облаке только? Или, существует ли объект, который был удаленных локальные, но обращается в облаке? Рассмотрим этот [Устранение ошибок во время синхронизации](https://go.microsoft.com/fwlink/p/?linkid=842044) и [поддержки статьи](https://go.microsoft.com/fwlink/p/?LinkId=396720) для инструкции о том, как решить эти проблемы.

### <a name="i-got-an-error-message-that-my-company-has-exceeded-the-number-of-objects-that-can-be-synchronized"></a>**Появляется сообщение о том, что в компании превышено максимальное количество объектов, которые можно синхронизировать**
- Можно прочитать подробнее об этой проблеме [здесь](https://go.microsoft.com/fwlink/p/?LinkId=396721).
   
## <a name="other-resources"></a>Другие ресурсы

- [Сценарий для исправления дублированных основные имена](https://go.microsoft.com/fwlink/p/?LinkId=396725)
    
- [Подготовка к синхронизации службы каталогов без поддержки маршрутизации домена (например, .local домена)](prepare-a-non-routable-domain-for-directory-synchronization.md)
    
- [Сценарий для подсчета всего синхронизированных объектов](https://go.microsoft.com/fwlink/p/?LinkId=396726)
    
- [Устранение неполадок AD FS 2.0 (en)](https://go.microsoft.com/fwlink/p/?LinkId=396727)
    
- [Использование PowerShell для исправления пустых атрибутов DisplayName для групп с включенной поддержкой почты](https://go.microsoft.com/fwlink/p/?LinkId=396728)
    
- [Использование PowerShell для исправления дублированных имени участника-пользователя](https://go.microsoft.com/fwlink/p/?LinkId=396730)
    
- [Использование PowerShell для исправления адреса повторяющихся электронной почты](https://go.microsoft.com/fwlink/p/?LinkId=396731)
    
## <a name="diagnostic-tools"></a>Средства диагностики

[Инструмент IDFix](prepare-directory-attributes-for-synch-with-idfix.md) используется для выполнения средства обнаружения и исправлению удостоверения объектов и их атрибутов в локальной среде Active Directory при подготовке к миграции в Office 365. IDFix предназначена для администраторов Active Directory, ответственный за DirSync со службой Office 365. 

[Загрузите средство IDFix](https://go.microsoft.com/fwlink/p/?LinkId=396718) из центра загрузки Майкрософт.