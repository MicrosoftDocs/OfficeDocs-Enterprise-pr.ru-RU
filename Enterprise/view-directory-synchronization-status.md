---
title: Просмотр состояния синхронизации каталогов в Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
ms.assetid: 18be3b98-34ae-47be-9337-ab6c3fb372ac
description: Узнайте, как отключить синхронизацию службы каталогов. Можно также просмотреть его состояние.
ms.openlocfilehash: c843fa4d71976cbdd0d6d3d10720e2845b26796c
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542613"
---
# <a name="view-directory-synchronization-status-in-office-365"></a>Просмотр состояния синхронизации каталогов в Office 365
Если локальной Active Directory с Azure AD интегрировали путем синхронизации локальной среды с Office 365, вы также можете проверить состояние вашей синхронизации.
  
## <a name="view-directory-synchronization-status"></a>Просмотр состояния синхронизации каталогов
- Войдите Центр администрирования Office 365 и выберите **Состояние DirSync** на домашней странице. 
- Кроме того, можно перейти к **пользователям** \> **активных пользователей**и на странице **активных пользователей** выберите **Дополнительные** \> **синхронизации службы каталогов**. В области **Синхронизации службы каталогов** выберите команду **перейдите на страницу управления DirSync**.
    
## <a name="information-on-the-manage-directory-synchronization-page"></a>Сведения на странице "Управление синхронизации каталогов"

В следующей таблице перечислены функции, которые вы можете получать сведения о на странице.
  
Если проблема связана с вашей синхронизации службы каталогов, на этой странице также перечислены ошибки. Дополнительные сведения о различных ошибках, которые могут возникнуть в разделе [Определение ошибок синхронизации службы каталогов в Office 365](identify-directory-synchronization-errors.md).
  
|**Элемент**|**Что такое для**|
|:-----|:-----|
|**Проверить доменов** | Количество доменов в клиент Office 365, что проверки вы владеете. |
|**Домены не проверено** | Домены добавлен, но не проверены. |
|**Синхронизация каталогов включена** |Значение true или False. Указывает, включена ли синхронизация каталогов. |
|**Новейшие синхронизации каталогов** | Время последнего запуска синхронизации каталогов. Будет отображаться предупреждения и ссылка средства устранения неполадок при последней синхронизации был более чем на три дня назад. |
|**Включить синхронизацию паролей** | Значение true или False. Указывает, будет ли у вас есть хэш-функции синхронизации паролей между наших локальной и клиента Office 365. |
|**Последняя синхронизация паролей** | Время последнего запуска хэш-функции синхронизации паролей. Будет отображаться предупреждения и ссылка средства устранения неполадок при последней синхронизации был более чем на три дня назад. |
|**Версия клиента синхронизации каталогов** | Содержит ссылки загрузки выпуска новой версии подключить Azure AD. |
|**Инструмент IDFix** | Ссылка для загрузки для [IDFix](install-and-run-idfix.md), средства, которые можно использовать для проверки локального Active Directory. |
|**Учетная запись службы синхронизации каталогов** | Отображает имя учетной записи службы синхронизации каталогов Office 365. |