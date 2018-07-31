---
title: Azure интеграции с Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 12/29/2016
ms.audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MOE150
- MED150
- BCS160
ms.assetid: a5efce5d-9c9c-4190-b61b-fd273c1d425f
description: Подписки Office 365 включает в себя подписка на Azure AD. Интеграция Office 365 с Azure AD, если необходимо использовать синхронизацию паролей или единого входа с локальной среды.
ms.openlocfilehash: abeda5eb915ac4ff9e395ab3b28f1e0cb7a68163
ms.sourcegitcommit: 92d16c0926e4be3fd493fe9b4eb317fb54996bca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/31/2018
ms.locfileid: "21550083"
---
# <a name="azure-integration-with-office-365"></a><span data-ttu-id="3ba75-104">Azure интеграции с Office 365</span><span class="sxs-lookup"><span data-stu-id="3ba75-104">Azure integration with Office 365</span></span>

<span data-ttu-id="3ba75-p102">Office 365 с помощью Azure Active Directory (Azure AD) управлять удостоверениями пользователей в фоновом режиме. Подписки Office 365 включает в себя бесплатная подписка на Azure AD, чтобы Office 365 можно интегрировать с Azure AD, если вы хотите синхронизации паролей или настроить единый вход с локальной среды. Также можно приобрести дополнительные возможности лучше управлять учетные записи.</span><span class="sxs-lookup"><span data-stu-id="3ba75-p102">Office 365 uses Azure Active Directory (Azure AD)to manage user identities behind the scenes. Your Office 365 subscription includes a free subscription to Azure AD so that you can integrate Office 365 with Azure AD if you want to sync passwords or set up single sign-on with your on-premises environment. You can also buy advanced features to better manage your accounts.</span></span>
  
<span data-ttu-id="3ba75-108">Azure также предоставляет другие функциональные возможности, как управление интегрированной приложений, которые можно использовать для расширения и настройки подписки Office 365.</span><span class="sxs-lookup"><span data-stu-id="3ba75-108">Azure also offers other functionality, like managing integrated apps, that you can use to extend and customize your Office 365 subscriptions.</span></span>
  
<span data-ttu-id="3ba75-109">Вы также можете использовать консультантов по Azure AD: [ядра СУБД Azure AD подключение](https://aka.ms/aadconnectpwsync), [Помощник по развертыванию AD FS](https://aka.ms/adfsguidance), [Мастер развертывании службы управления правами Azure](https://aka.ms/azuremsguidance)и [руководство по настройке Azure AD Premium](https://aka.ms/aadpguidance).</span><span class="sxs-lookup"><span data-stu-id="3ba75-109">You can also use the Azure AD advisors: the [Azure AD Connect advisor](https://aka.ms/aadconnectpwsync), the [AD FS deployment advisor](https://aka.ms/adfsguidance), the [Azure RMS Deploymnet Wizard](https://aka.ms/azuremsguidance), and the [Azure AD Premium setup guide](https://aka.ms/aadpguidance).</span></span>
  
## <a name="azure-ad-editions-and-office-365-identity-management"></a><span data-ttu-id="3ba75-110">Выпуски Azure AD и управления удостоверениями Office 365</span><span class="sxs-lookup"><span data-stu-id="3ba75-110">Azure AD editions and Office 365 identity management</span></span>

<span data-ttu-id="3ba75-p103">При наличии платной подписки на Office 365 также имеется бесплатная подписка на Azure AD. Создание и управление ими пользователи и группы можно использовать Azure AD. Чтобы активировать эту подписку, необходимо выполнить разовое регистрации. После этого можно получить доступ к Azure AD через портал администрирования Office 365. Сведения содержатся в разделе [Регистрация вашей бесплатные подписки Azure AD](https://go.microsoft.com/fwlink/p/?LinkId=617127).</span><span class="sxs-lookup"><span data-stu-id="3ba75-p103">If you have a paid subscription to Office 365, you also have a free subscription to Azure AD. You can use Azure AD to create and manage user and group accounts. To activate this subscription you have to complete a one-time registration. Afterward, you can access Azure AD from your Office 365 admin portal. For instructions, see [register your free Azure AD subscription](https://go.microsoft.com/fwlink/p/?LinkId=617127).</span></span> 
  
> [!TIP]
> <span data-ttu-id="3ba75-p104">Следуйте инструкциям выше подписку register бесплатную Azure AD, которое поставляется с подписки на Office 365. Не перейдите непосредственно к Azure.Microsoft.com зарегистрироваться или получите с пробной версии или платной подписки на Microsoft Azure, отдельно от вашей бесплатную одно для Office 365.</span><span class="sxs-lookup"><span data-stu-id="3ba75-p104">Follow the instructions above to register the free Azure AD subscription that comes with your subscription to Office 365. Don't go directly to Azure.Microsoft.com to sign up or you'll end up with a trial or paid subscription to Microsoft Azure that is separate from your free one for Office 365.</span></span> 
  
<span data-ttu-id="3ba75-118">Бесплатные подписки можно синхронизировать с локально размещенные каталоги, настройки единого входа и синхронизация с много программное обеспечение как приложений-служб, таких как Salesforce, общего банка данных и многое другое.</span><span class="sxs-lookup"><span data-stu-id="3ba75-118">With the free subscription you can synchronize with on-premises directories, set up single sign-on, and synchronize with many software as service applications, such as Salesforce, DropBox and many more.</span></span>
  
<span data-ttu-id="3ba75-p105">Если необходимо, расширенные возможности Доменные службы Active Directory, двунаправленную синхронизацию и других возможностей управления, бесплатные подписки можно обновить до premium платной подписки. Для получения дополнительных сведений см [выпуски Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524280).</span><span class="sxs-lookup"><span data-stu-id="3ba75-p105">If you want enhanced AD DS functionality, bi-directional synchronization, and other management capabilities, you can upgrade your free subscription to a paid premium subscription. For details see [Azure Active Directory editions](https://go.microsoft.com/fwlink/p/?LinkId=524280).</span></span>
  
<span data-ttu-id="3ba75-121">Дополнительные сведения об Office 365 и Azure AD содержатся в разделе [Общие сведения об Office 365 удостоверения и Azure Active Directory](https://support.office.com/article/06a189e7-5ec6-4af2-94bf-a22ea225a7a9).</span><span class="sxs-lookup"><span data-stu-id="3ba75-121">For more information about Office 365 and Azure AD, see [Understanding Office 365 Identity and Azure Active Directory](https://support.office.com/article/06a189e7-5ec6-4af2-94bf-a22ea225a7a9).</span></span>
  
## <a name="extend-the-capabilities-of-your-office-365-tenant"></a><span data-ttu-id="3ba75-122">Расширение возможностей клиента Office 365</span><span class="sxs-lookup"><span data-stu-id="3ba75-122">Extend the capabilities of your Office 365 tenant</span></span>

|<span data-ttu-id="3ba75-123">**Функция**</span><span class="sxs-lookup"><span data-stu-id="3ba75-123">**Feature**</span></span>|<span data-ttu-id="3ba75-124">**Описание**</span><span class="sxs-lookup"><span data-stu-id="3ba75-124">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="3ba75-125">Интегрированные приложения</span><span class="sxs-lookup"><span data-stu-id="3ba75-125">Integrated apps</span></span>  <br/> |<span data-ttu-id="3ba75-p106">Можно предоставить отдельных приложений доступ к данным Office 365, как почты, календари, контакты, пользователи, группы, файлы и папки. Можно также авторизации этих приложений на уровне глобального администратора и сделать их доступными для всей компании по регистрации приложений в Azure AD. Для получения дополнительных сведений см [интегрированной приложений и Azure AD для Office 365 для администраторов](https://support.office.com/article/cb2250e3-451e-416f-bf4e-363549652c2a).</span><span class="sxs-lookup"><span data-stu-id="3ba75-p106">You can grant individual apps access to your Office 365 data, like mail, calendars, contacts, users, groups, files, and folders. You can also authorize these apps at global admin level and make them available to your entire company by registering the apps in Azure AD. For details see [Integrated Apps and Azure AD for Office 365 administrators](https://support.office.com/article/cb2250e3-451e-416f-bf4e-363549652c2a).  </span></span><br/> <span data-ttu-id="3ba75-129">См. также [коллекции приложения Azure AD и single sign on](https://go.microsoft.com/fwlink/p/?LinkId=698604).</span><span class="sxs-lookup"><span data-stu-id="3ba75-129">See also [Azure AD application gallery and single-sign-on](https://go.microsoft.com/fwlink/p/?LinkId=698604).</span></span>  <br/> |
|<span data-ttu-id="3ba75-130">PowerApps</span><span class="sxs-lookup"><span data-stu-id="3ba75-130">PowerApps</span></span>  <br/> | <span data-ttu-id="3ba75-p107">Power приложений, целенаправленных приложения для мобильных устройств, которые могут подключаться к существующих данных источников, например списки SharePoint и другие данные приложения. Для получения дополнительных сведений см [Создать PowerApp для списка в SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) и [PowerApps страницы](https://powerapps.microsoft.com/) .</span><span class="sxs-lookup"><span data-stu-id="3ba75-p107">Power apps are focused apps for mobile devices that can connect to your existing data sources like SharePoint lists, and other data apps. See [Create a PowerApp for a list in SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) and [PowerApps page](https://powerapps.microsoft.com/) for details.  </span></span><br/> |
   
<span data-ttu-id="3ba75-133">Другие ресурсы, посвященные Microsoft Cloud и Office 365 см.</span><span class="sxs-lookup"><span data-stu-id="3ba75-133">For other resources about the Microsoft Cloud and Office 365, see these resources:</span></span>
  
- [<span data-ttu-id="3ba75-134">Идентификация в облаке Майкрософт для корпоративных архитекторов</span><span class="sxs-lookup"><span data-stu-id="3ba75-134">Microsoft Cloud Identity for Enterprise Architects</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=828642)
    
- [<span data-ttu-id="3ba75-135">Развертывание службы синхронизации каталогов Office 365 (DirSync) в Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="3ba75-135">Deploy Office 365 Directory Synchronization (DirSync) in Microsoft Azure</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=517887)
    

