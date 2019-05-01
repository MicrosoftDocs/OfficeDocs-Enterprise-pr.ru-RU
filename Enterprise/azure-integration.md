---
title: Интеграция Azure с Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-identity-device-management
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: a5efce5d-9c9c-4190-b61b-fd273c1d425f
description: Ваша подписка на Office 365 включает в себя подписку на Azure AD. Интегрируйте Office 365 с Azure AD, если вы хотите выполнить синхронизацию паролей или единый вход с локальной средой.
ms.openlocfilehash: 0ad1c064d2ffe29f0f06e1368cd728d8b3bd630b
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/30/2019
ms.locfileid: "33490145"
---
# <a name="azure-integration-with-office-365"></a>Интеграция Azure с Office 365

Office 365 использует Azure Active Directory (Azure AD) для управления удостоверениями пользователей в фоновом режиме. Ваша подписка на Office 365 включает бесплатную подписку на Azure AD, поэтому вы можете интегрировать Office 365 с Azure AD, если вы хотите синхронизировать пароли или настроить единый вход в локальной среде. Кроме того, вы можете приобрести дополнительные функции, чтобы лучше управлять учетными записями.
  
Azure также предоставляет другие функциональные возможности, такие как Управление интегрированными приложениями, которые можно использовать для расширения и настройки подписок на Office 365.
  
Вы можете использовать рекомендации по развертыванию Azure AD для руководства по установке и настройке:
 - [Советник по подключению Azure AD](https://aka.ms/aadconnectpwsync)
 - [Помощник по развертыванию AD FS](https://aka.ms/adfsguidance)
 - [Мастер развертывания службы управления правами Azure](https://aka.ms/azuremsguidance)
 - [Руководство по установке Azure AD Premium](https://aka.ms/aadpguidance)
  
## <a name="azure-ad-editions-and-office-365-identity-management"></a>Выпуски Azure AD и управление удостоверениями Office 365

Если у вас есть платная подписка на Office 365, вы также можете получить бесплатную подписку на Azure AD. Вы можете использовать Azure AD для создания учетных записей пользователей и групп и управления ими. Чтобы активировать эту подписку, необходимо выполнить одноразовую регистрацию. После этого вы сможете получить доступ к Azure AD на портале администрирования Office 365. Инструкции можно найти [в статье регистрация бесплатной подписки на Azure AD](https://go.microsoft.com/fwlink/p/?LinkId=617127). 
  
> [!TIP]
> Следуйте инструкциям, приведенным выше, чтобы зарегистрировать бесплатную подписку на Azure AD, которая входит в состав подписки на Office 365. Не переходите непосредственно к azure.microsoft.com, чтобы зарегистрироваться или получить пробную или платную подписку на Microsoft Azure, отделенную от бесплатной для Office 365. 
  
С помощью бесплатной подписки вы можете синхронизироваться с локальными каталогами, настроить единый вход и синхронизировать с множеством программ в качестве приложений служб, таких как Salesforce, DropBox и многие другие.
  
Если вы хотите улучшить функции AD DS, двунаправленную синхронизацию и другие возможности управления, вы можете обновить бесплатную подписку на платную подписку. Дополнительные сведения см. в статье [Azure Active Directory Editions](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-whatis).
  
Дополнительные сведения о Office 365 и Azure AD см. в статье Общие сведения об [удостоверенИи office 365 и Azure Active Directory](https://support.office.com/article/06a189e7-5ec6-4af2-94bf-a22ea225a7a9).
  
## <a name="extend-the-capabilities-of-your-office-365-tenant"></a>Расширьте возможности клиента Office 365

|**Функция**|**Описание**|
|:-----|:-----|
|Интегрированные приложения  <br/> |Вы можете предоставить доступ к данным Office 365 для отдельных приложений, таких как почта, календари, контакты, пользователи, группы, файлы и папки. Вы также можете авторизовать эти приложения на глобальном уровне администратора и сделать их доступными для всей компании, зарегистрировав приложения в Azure AD. Дополнительные сведения см. [интегрированНые приложения и Azure AD для администраторов Office 365](https://support.office.com/article/cb2250e3-451e-416f-bf4e-363549652c2a).  <br/> В этой статье вы также найдете [коллекцию приложений Azure AD и единый вход](https://go.microsoft.com/fwlink/p/?LinkId=698604).  <br/> |
|PowerApps  <br/> | Приложения Power Apps ориентированы на приложения для мобильных устройств, которые могут подключаться к существующим источникам данных, таким как списки SharePoint и другие приложения для передачи данных. [В статье Создание поверапп для списка на странице SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) и [PowerApps](https://powerapps.microsoft.com/) для получения дополнительных сведений.  <br/> |
   
Другие ресурсы, посвященные Microsoft Cloud и Office 365, можно найти в следующих ресурсах:
  
- [Облачное удостоверение Майкрософт для корпоративных архитекторов](https://go.microsoft.com/fwlink/p/?LinkId=524586)
    
- [Развертывание службы синхронизации каталогов Office 365 (DirSync) в Microsoft Azure](https://go.microsoft.com/fwlink/p/?LinkId=517887)
    

Узнайте больше об [интегрированНых приложениях и Azure AD для администраторов Office 365](integrated-apps-and-azure-ads.md) и [коллекции приложений Azure AD и единого входа](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-single-sign-on).

### <a name="power-apps"></a>Power Apps
Приложения Power Apps ориентированы на приложения для мобильных устройств, которые могут подключаться к существующим источникам данных, таким как списки SharePoint и другие приложения для передачи данных. [В статье Создание поверапп для списка на странице SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) и [PowerApps](https://powerapps.microsoft.com/) для получения дополнительных сведений.