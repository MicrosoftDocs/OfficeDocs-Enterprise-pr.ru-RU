---
title: Интеграция Azure с Office 365
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
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085478"
---
# <a name="azure-integration-with-office-365"></a><span data-ttu-id="1e0da-104">Интеграция Azure с Office 365</span><span class="sxs-lookup"><span data-stu-id="1e0da-104">Azure integration with Office 365</span></span>

<span data-ttu-id="1e0da-p102">Office 365 использует Azure Active Directory (Azure AD) для управления удостоверениями пользователей в фоновом режиме. Ваша подписка на Office 365 включает бесплатную подписку на Azure AD, поэтому вы можете интегрировать Office 365 с Azure AD, если вы хотите синхронизировать пароли или настроить единый вход в локальной среде. Кроме того, вы можете приобрести дополнительные функции, чтобы лучше управлять учетными записями.</span><span class="sxs-lookup"><span data-stu-id="1e0da-p102">Office 365 uses Azure Active Directory (Azure AD) to manage user identities behind the scenes. Your Office 365 subscription includes a free subscription to Azure AD so that you can integrate Office 365 with Azure AD if you want to sync passwords or set up single sign-on with your on-premises environment. You can also buy advanced features to better manage your accounts.</span></span>
  
<span data-ttu-id="1e0da-108">Azure также предоставляет другие функциональные возможности, такие как Управление интегрированными приложениями, которые можно использовать для расширения и настройки подписок на Office 365.</span><span class="sxs-lookup"><span data-stu-id="1e0da-108">Azure also offers other functionality, like managing integrated apps, that you can use to extend and customize your Office 365 subscriptions.</span></span>
  
<span data-ttu-id="1e0da-109">Вы можете использовать рекомендации по развертыванию Azure AD для руководства по установке и настройке:</span><span class="sxs-lookup"><span data-stu-id="1e0da-109">You can use the Azure AD deployment advisors for a guided setup and configuration experience:</span></span>
 - [<span data-ttu-id="1e0da-110">Советник по подключению Azure AD</span><span class="sxs-lookup"><span data-stu-id="1e0da-110">Azure AD Connect advisor</span></span>](https://aka.ms/aadconnectpwsync)
 - [<span data-ttu-id="1e0da-111">Помощник по развертыванию AD FS</span><span class="sxs-lookup"><span data-stu-id="1e0da-111">AD FS deployment advisor</span></span>](https://aka.ms/adfsguidance)
 - [<span data-ttu-id="1e0da-112">Мастер развертывания службы управления правами Azure</span><span class="sxs-lookup"><span data-stu-id="1e0da-112">Azure RMS Deployment Wizard</span></span>](https://aka.ms/azuremsguidance)
 - [<span data-ttu-id="1e0da-113">Руководство по установке Azure AD Premium</span><span class="sxs-lookup"><span data-stu-id="1e0da-113">Azure AD Premium setup guide</span></span>](https://aka.ms/aadpguidance)
  
## <a name="azure-ad-editions-and-office-365-identity-management"></a><span data-ttu-id="1e0da-114">Выпуски Azure AD и управление удостоверениями Office 365</span><span class="sxs-lookup"><span data-stu-id="1e0da-114">Azure AD editions and Office 365 identity management</span></span>

<span data-ttu-id="1e0da-p103">Если у вас есть платная подписка на Office 365, вы также можете получить бесплатную подписку на Azure AD. Вы можете использовать Azure AD для создания учетных записей пользователей и групп и управления ими. Чтобы активировать эту подписку, необходимо выполнить одноразовую регистрацию. После этого вы сможете получить доступ к Azure AD на портале администрирования Office 365. Инструкции можно найти [в статье регистрация бесплатной подписки на Azure AD](https://go.microsoft.com/fwlink/p/?LinkId=617127).</span><span class="sxs-lookup"><span data-stu-id="1e0da-p103">If you have a paid subscription to Office 365, you also have a free subscription to Azure AD. You can use Azure AD to create and manage user and group accounts. To activate this subscription you have to complete a one-time registration. Afterward, you can access Azure AD from your Office 365 admin portal. For instructions, see [register your free Azure AD subscription](https://go.microsoft.com/fwlink/p/?LinkId=617127).</span></span> 
  
> [!TIP]
> <span data-ttu-id="1e0da-p104">Следуйте инструкциям, приведенным выше, чтобы зарегистрировать бесплатную подписку на Azure AD, которая входит в состав подписки на Office 365. Не переходите непосредственно к azure.microsoft.com, чтобы зарегистрироваться или получить пробную или платную подписку на Microsoft Azure, отделенную от бесплатной для Office 365.</span><span class="sxs-lookup"><span data-stu-id="1e0da-p104">Follow the instructions above to register the free Azure AD subscription that comes with your subscription to Office 365. Don't go directly to azure.microsoft.com to sign up or you'll end up with a trial or paid subscription to Microsoft Azure that is separate from your free one for Office 365.</span></span> 
  
<span data-ttu-id="1e0da-122">С помощью бесплатной подписки вы можете синхронизироваться с локальными каталогами, настроить единый вход и синхронизировать с множеством программ в качестве приложений служб, таких как Salesforce, DropBox и многие другие.</span><span class="sxs-lookup"><span data-stu-id="1e0da-122">With the free subscription you can synchronize with on-premises directories, set up single sign-on, and synchronize with many software as service applications, such as Salesforce, DropBox and many more.</span></span>
  
<span data-ttu-id="1e0da-p105">Если вы хотите улучшить функции AD DS, двунаправленную синхронизацию и другие возможности управления, вы можете обновить бесплатную подписку на платную подписку. Дополнительные сведения см. в статье [Azure Active Directory Editions](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-whatis).</span><span class="sxs-lookup"><span data-stu-id="1e0da-p105">If you want enhanced AD DS functionality, bi-directional synchronization, and other management capabilities, you can upgrade your free subscription to a paid premium subscription. For details see [Azure Active Directory editions](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-whatis).</span></span>
  
<span data-ttu-id="1e0da-125">Дополнительные сведения о Office 365 и Azure AD см. в статье Общие сведения об [удостоверенИи office 365 и Azure Active Directory](https://support.office.com/article/06a189e7-5ec6-4af2-94bf-a22ea225a7a9).</span><span class="sxs-lookup"><span data-stu-id="1e0da-125">For more information about Office 365 and Azure AD, see [Understanding Office 365 Identity and Azure Active Directory](https://support.office.com/article/06a189e7-5ec6-4af2-94bf-a22ea225a7a9).</span></span>
  
## <a name="extend-the-capabilities-of-your-office-365-tenant"></a><span data-ttu-id="1e0da-126">Расширьте возможности клиента Office 365</span><span class="sxs-lookup"><span data-stu-id="1e0da-126">Extend the capabilities of your Office 365 tenant</span></span>

|<span data-ttu-id="1e0da-127">**Функция**</span><span class="sxs-lookup"><span data-stu-id="1e0da-127">**Feature**</span></span>|<span data-ttu-id="1e0da-128">**Описание**</span><span class="sxs-lookup"><span data-stu-id="1e0da-128">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="1e0da-129">Интегрированные приложения</span><span class="sxs-lookup"><span data-stu-id="1e0da-129">Integrated apps</span></span>  <br/> |<span data-ttu-id="1e0da-p106">Вы можете предоставить доступ к данным Office 365 для отдельных приложений, таких как почта, календари, контакты, пользователи, группы, файлы и папки. Вы также можете авторизовать эти приложения на глобальном уровне администратора и сделать их доступными для всей компании, зарегистрировав приложения в Azure AD. Дополнительные сведения см. [интегрированНые приложения и Azure AD для администраторов Office 365](https://support.office.com/article/cb2250e3-451e-416f-bf4e-363549652c2a).</span><span class="sxs-lookup"><span data-stu-id="1e0da-p106">You can grant individual apps access to your Office 365 data, like mail, calendars, contacts, users, groups, files, and folders. You can also authorize these apps at global admin level and make them available to your entire company by registering the apps in Azure AD. For details see [Integrated Apps and Azure AD for Office 365 administrators](https://support.office.com/article/cb2250e3-451e-416f-bf4e-363549652c2a).  </span></span><br/> <span data-ttu-id="1e0da-133">В этой статье вы также найдете [коллекцию приложений Azure AD и единый вход](https://go.microsoft.com/fwlink/p/?LinkId=698604).</span><span class="sxs-lookup"><span data-stu-id="1e0da-133">See also [Azure AD application gallery and single-sign-on](https://go.microsoft.com/fwlink/p/?LinkId=698604).</span></span>  <br/> |
|<span data-ttu-id="1e0da-134">PowerApps</span><span class="sxs-lookup"><span data-stu-id="1e0da-134">PowerApps</span></span>  <br/> | <span data-ttu-id="1e0da-p107">Приложения Power Apps ориентированы на приложения для мобильных устройств, которые могут подключаться к существующим источникам данных, таким как списки SharePoint и другие приложения для передачи данных. [В статье Создание поверапп для списка на странице SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) и [PowerApps](https://powerapps.microsoft.com/) для получения дополнительных сведений.</span><span class="sxs-lookup"><span data-stu-id="1e0da-p107">Power apps are focused apps for mobile devices that can connect to your existing data sources like SharePoint lists, and other data apps. See [Create a PowerApp for a list in SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) and [PowerApps page](https://powerapps.microsoft.com/) for details.  </span></span><br/> |
   
<span data-ttu-id="1e0da-137">Другие ресурсы, посвященные Microsoft Cloud и Office 365, можно найти в следующих ресурсах:</span><span class="sxs-lookup"><span data-stu-id="1e0da-137">For other resources about the Microsoft Cloud and Office 365, see these resources:</span></span>
  
- [<span data-ttu-id="1e0da-138">Идентификация в облаке Майкрософт для корпоративных архитекторов</span><span class="sxs-lookup"><span data-stu-id="1e0da-138">Microsoft Cloud Identity for Enterprise Architects</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524586)
    
- [<span data-ttu-id="1e0da-139">Развертывание службы синхронизации каталогов Office 365 (DirSync) в Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="1e0da-139">Deploy Office 365 Directory Synchronization (DirSync) in Microsoft Azure</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=517887)
    

<span data-ttu-id="1e0da-140">Узнайте больше об [интегрированНых приложениях и Azure AD для администраторов Office 365](integrated-apps-and-azure-ads.md) и [коллекции приложений Azure AD и единого входа](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-single-sign-on).</span><span class="sxs-lookup"><span data-stu-id="1e0da-140">Learn more at [Integrated Apps and Azure AD for Office 365 administrators](integrated-apps-and-azure-ads.md) and [Azure AD application gallery and single-sign-on](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-single-sign-on).</span></span>

### <a name="power-apps"></a><span data-ttu-id="1e0da-141">Power Apps</span><span class="sxs-lookup"><span data-stu-id="1e0da-141">Power Apps</span></span>
<span data-ttu-id="1e0da-p108">Приложения Power Apps ориентированы на приложения для мобильных устройств, которые могут подключаться к существующим источникам данных, таким как списки SharePoint и другие приложения для передачи данных. [В статье Создание поверапп для списка на странице SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) и [PowerApps](https://powerapps.microsoft.com/) для получения дополнительных сведений.</span><span class="sxs-lookup"><span data-stu-id="1e0da-p108">Power apps are focused apps for mobile devices that can connect to your existing data sources like SharePoint lists, and other data apps. See [Create a PowerApp for a list in SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) and [PowerApps page](https://powerapps.microsoft.com/) for details.</span></span>