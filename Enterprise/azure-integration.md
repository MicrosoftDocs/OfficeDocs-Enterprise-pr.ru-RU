---
title: Интеграция Azure с Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: a5efce5d-9c9c-4190-b61b-fd273c1d425f
description: Подписки Office 365 включает в себя подписка на Azure AD. Интеграция Office 365 с Azure AD, если необходимо использовать синхронизацию паролей или единого входа с локальной среды.
ms.openlocfilehash: 276243b953d18953ef3ea8f1189d1af8292dca6a
ms.sourcegitcommit: b1cd20300a616ebef2f00668f42ba14e8aa5fcab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/30/2018
ms.locfileid: "23531842"
---
# <a name="azure-integration-with-office-365"></a>Интеграция Azure с Office 365

Office 365 с помощью Azure Active Directory (Azure AD) управлять удостоверениями пользователей в фоновом режиме. Подписки Office 365 включает в себя бесплатная подписка на Azure AD, чтобы Office 365 можно интегрировать с Azure AD, если вы хотите синхронизации паролей или настроить единый вход с локальной среды. Также можно приобрести дополнительные возможности лучше управлять учетные записи.
  
Azure также предоставляет другие функциональные возможности, как управление интегрированной приложений, которые можно использовать для расширения и настройки подписки Office 365.
  
Можно использовать консультантов по развертыванию Azure AD для под руководством инструктора программой установки и настройки:
 - [Помощник по Azure AD подключение](https://aka.ms/aadconnectpwsync)
 - [Помощник по развертыванию AD FS](https://aka.ms/adfsguidance)
 - [Мастер развертывания службы управления правами Azure](https://aka.ms/azuremsguidance)
 - [Руководство по настройке Azure AD премиум](https://aka.ms/aadpguidance)
  
## <a name="azure-ad-editions-and-office-365-identity-management"></a>Выпуски Azure AD и управления удостоверениями Office 365

При наличии платной подписки на Office 365 также имеется бесплатная подписка на Azure AD. Создание и управление ими пользователи и группы можно использовать Azure AD. Чтобы активировать эту подписку, необходимо выполнить разовое регистрации. После этого можно получить доступ к Azure AD через портал администрирования Office 365. Сведения содержатся в разделе [Регистрация вашей бесплатные подписки Azure AD](https://go.microsoft.com/fwlink/p/?LinkId=617127). 
  
> [!TIP]
> Следуйте инструкциям выше подписку register бесплатную Azure AD, которое поставляется с подписки на Office 365. Не перейдите непосредственно к azure.microsoft.com зарегистрироваться или получите с пробной версии или платной подписки на Microsoft Azure, отдельно от вашей бесплатную одно для Office 365. 
  
Бесплатные подписки можно синхронизировать с локально размещенные каталоги, настройки единого входа и синхронизация с много программное обеспечение как приложений-служб, таких как Salesforce, общего банка данных и многое другое.
  
Если необходимо, расширенные возможности Доменные службы Active Directory, двунаправленную синхронизацию и других возможностей управления, бесплатные подписки можно обновить до premium платной подписки. Для получения дополнительных сведений см [выпуски Azure Active Directory](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-whatis).
  
Дополнительные сведения об Office 365 и Azure AD содержатся в разделе [Общие сведения об Office 365 удостоверения и Azure Active Directory](https://support.office.com/article/06a189e7-5ec6-4af2-94bf-a22ea225a7a9).
  
## <a name="extend-the-capabilities-of-your-office-365-tenant"></a>Расширение возможностей клиента Office 365

|**Функция**|**Описание**|
|:-----|:-----|
|Интегрированные приложения  <br/> |Можно предоставить отдельных приложений доступ к данным Office 365, как почты, календари, контакты, пользователи, группы, файлы и папки. Можно также авторизации этих приложений на уровне глобального администратора и сделать их доступными для всей компании по регистрации приложений в Azure AD. Для получения дополнительных сведений см [интегрированной приложений и Azure AD для Office 365 для администраторов](https://support.office.com/article/cb2250e3-451e-416f-bf4e-363549652c2a).<br/> См. также [коллекции приложения Azure AD и single sign on](https://go.microsoft.com/fwlink/p/?LinkId=698604).  <br/> |
|PowerApps  <br/> | Power приложений, целенаправленных приложения для мобильных устройств, которые могут подключаться к существующих данных источников, например списки SharePoint и другие данные приложения. Для получения дополнительных сведений см [Создать PowerApp для списка в SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) и [PowerApps страницы](https://powerapps.microsoft.com/) .<br/> |
   
Другие ресурсы, посвященные Microsoft Cloud и Office 365 см.
  
- [Идентификация в облаке Майкрософт для корпоративных архитекторов](https://go.microsoft.com/fwlink/p/?LinkId=828642)
    
- [Развертывание службы синхронизации каталогов Office 365 (DirSync) в Microsoft Azure](https://go.microsoft.com/fwlink/p/?LinkId=517887)
    

Дополнительные сведения по [интегрированной приложений и Azure AD для Office 365 для администраторов](integrated-apps-and-azure-ads.md) и [коллекции приложения Azure AD и single sign on](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-single-sign-on).

### <a name="power-apps"></a>Power приложений
Power приложений, целенаправленных приложения для мобильных устройств, которые могут подключаться к существующих данных источников, например списки SharePoint и другие данные приложения. Для получения дополнительных сведений см [Создать PowerApp для списка в SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) и [PowerApps страницы](https://powerapps.microsoft.com/) .