---
title: Интеграция с Microsoft Azure с помощью Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/09/2019
audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-identity-device-management
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: a5efce5d-9c9c-4190-b61b-fd273c1d425f
description: Подписка на Microsoft 365 включает в себя подписку на Azure AD. Интегрируйте Microsoft 365 с Azure AD, если вы хотите выполнить синхронизацию паролей или единый вход с локальной средой.
ms.openlocfilehash: 40426c20f12cf17955457c38d809926550efa188
ms.sourcegitcommit: 4c519f054216c05c42acba5ac460fb9a821d6436
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "44774844"
---
# <a name="azure-integration-with-microsoft-365"></a><span data-ttu-id="a9af9-104">Интеграция с Microsoft Azure с помощью Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="a9af9-104">Azure integration with Microsoft 365</span></span>

<span data-ttu-id="a9af9-105">*Эта статья относится как к Microsoft 365 Enterprise, так и к Office 365 корпоративный.*</span><span class="sxs-lookup"><span data-stu-id="a9af9-105">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="a9af9-106">Microsoft 365 использует Azure Active Directory (Azure AD) для управления удостоверениями пользователей в фоновом режиме.</span><span class="sxs-lookup"><span data-stu-id="a9af9-106">Microsoft 365 uses Azure Active Directory (Azure AD) to manage user identities behind the scenes.</span></span> <span data-ttu-id="a9af9-107">Подписка на Microsoft 365 включает бесплатную подписку на Azure AD, чтобы вы могли интегрировать Microsoft 365 с Azure AD, если вы хотите синхронизировать пароли или настроить единый вход в локальной среде.</span><span class="sxs-lookup"><span data-stu-id="a9af9-107">Your Microsoft 365 subscription includes a free subscription to Azure AD so that you can integrate Microsoft 365 with Azure AD if you want to sync passwords or set up single sign-on with your on-premises environment.</span></span> <span data-ttu-id="a9af9-108">Кроме того, вы можете приобрести дополнительные функции, чтобы лучше управлять учетными записями.</span><span class="sxs-lookup"><span data-stu-id="a9af9-108">You can also buy advanced features to better manage your accounts.</span></span>
  
<span data-ttu-id="a9af9-109">Azure также предоставляет другие функциональные возможности, такие как Управление интегрированными приложениями, которые можно использовать для расширения и настройки подписок Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="a9af9-109">Azure also offers other functionality, like managing integrated apps, that you can use to extend and customize your Microsoft 365 subscriptions.</span></span>
  
<span data-ttu-id="a9af9-110">Вы можете использовать рекомендации по развертыванию Azure AD для пошаговой установки и настройки (необходимо войти в Microsoft 365):</span><span class="sxs-lookup"><span data-stu-id="a9af9-110">You can use the Azure AD deployment advisors for a guided setup and configuration experience (you must be signed in to Microsoft 365):</span></span>

 - [<span data-ttu-id="a9af9-111">Советник по подключению Azure AD</span><span class="sxs-lookup"><span data-stu-id="a9af9-111">Azure AD Connect advisor</span></span>](https://aka.ms/aadconnectpwsync)
 - [<span data-ttu-id="a9af9-112">Помощник по развертыванию AD FS</span><span class="sxs-lookup"><span data-stu-id="a9af9-112">AD FS deployment advisor</span></span>](https://aka.ms/adfsguidance)
 - [<span data-ttu-id="a9af9-113">Руководство по установке Azure AD Premium</span><span class="sxs-lookup"><span data-stu-id="a9af9-113">Azure AD Premium setup guide</span></span>](https://aka.ms/aadpguidance)
  
## <a name="azure-ad-editions-and-microsoft-365-identity-management"></a><span data-ttu-id="a9af9-114">Выпуски Azure AD и Microsoft 365 Identity Management</span><span class="sxs-lookup"><span data-stu-id="a9af9-114">Azure AD editions and Microsoft 365 identity management</span></span>

<span data-ttu-id="a9af9-115">Если у вас есть платная подписка на Microsoft 365, у вас также есть бесплатная подписка на Azure AD.</span><span class="sxs-lookup"><span data-stu-id="a9af9-115">If you have a paid subscription to Microsoft 365, you also have a free subscription to Azure AD.</span></span> <span data-ttu-id="a9af9-116">Вы можете использовать Azure AD для создания учетных записей пользователей и групп и управления ими.</span><span class="sxs-lookup"><span data-stu-id="a9af9-116">You can use Azure AD to create and manage user and group accounts.</span></span> <span data-ttu-id="a9af9-117">Чтобы активировать эту подписку, необходимо выполнить одноразовую регистрацию.</span><span class="sxs-lookup"><span data-stu-id="a9af9-117">To activate this subscription you have to complete a one-time registration.</span></span> <span data-ttu-id="a9af9-118">После этого вы сможете получить доступ к Azure AD из центра администрирования Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="a9af9-118">Afterward, you can access Azure AD from your Microsoft 365 admin center.</span></span> 

<span data-ttu-id="a9af9-119">Инструкции см. [в разделе Использование бесплатной подписки на Azure AD](https://go.microsoft.com/fwlink/p/?LinkId=617127).</span><span class="sxs-lookup"><span data-stu-id="a9af9-119">For instructions, see [use your free Azure AD subscription](https://go.microsoft.com/fwlink/p/?LinkId=617127).</span></span> <span data-ttu-id="a9af9-120">Следуйте инструкциям по регистрации бесплатной подписки на Azure AD, которая входит в состав подписки на Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="a9af9-120">Follow the instructions to register the free Azure AD subscription that comes with your subscription to Microsoft 365.</span></span> <span data-ttu-id="a9af9-121">Не переходите непосредственно к azure.microsoft.com, чтобы зарегистрироваться или получить пробную или платную подписку на Microsoft Azure, отделенную от бесплатной версии для Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="a9af9-121">Don't go directly to azure.microsoft.com to sign up or you'll end up with a trial or paid subscription to Microsoft Azure that is separate from your free one for Microsoft 365.</span></span> 
  
<span data-ttu-id="a9af9-122">С помощью бесплатной подписки вы можете синхронизироваться с локальными каталогами, настроить единый вход и синхронизировать с множеством программ в качестве приложений служб, таких как Salesforce, DropBox и многие другие.</span><span class="sxs-lookup"><span data-stu-id="a9af9-122">With the free subscription you can synchronize with on-premises directories, set up single sign-on, and synchronize with many software as service applications, such as Salesforce, DropBox and many more.</span></span>
  
<span data-ttu-id="a9af9-123">Если вам нужны расширенные функции доменных служб Active Directory (AD DS), двунаправленной синхронизации и другие возможности управления, вы можете обновить бесплатную подписку до платной подписки.</span><span class="sxs-lookup"><span data-stu-id="a9af9-123">If you want enhanced Active Directory Domain Services (AD DS) functionality, bi-directional synchronization, and other management capabilities, you can upgrade your free subscription to a paid premium subscription.</span></span> <span data-ttu-id="a9af9-124">Дополнительные сведения см. в статье [Azure Active Directory Editions](https://azure.microsoft.com/pricing/details/active-directory/).</span><span class="sxs-lookup"><span data-stu-id="a9af9-124">For details see [Azure Active Directory editions](https://azure.microsoft.com/pricing/details/active-directory/).</span></span>
  
<span data-ttu-id="a9af9-125">Для получения дополнительных сведений о Microsoft 365 и Azure AD, ознакомьтесь со статьей [сведения об удостоверении microsoft 365 и Azure Active Directory](about-office-365-identity.md).</span><span class="sxs-lookup"><span data-stu-id="a9af9-125">For more information about Microsoft 365 and Azure AD, see [Understanding Microsoft 365 Identity and Azure Active Directory](about-office-365-identity.md).</span></span>
  
## <a name="extend-the-capabilities-of-your-microsoft-365-tenant"></a><span data-ttu-id="a9af9-126">Расширьте возможности клиента Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="a9af9-126">Extend the capabilities of your Microsoft 365 tenant</span></span>

|<span data-ttu-id="a9af9-127">**Функция**</span><span class="sxs-lookup"><span data-stu-id="a9af9-127">**Feature**</span></span>|<span data-ttu-id="a9af9-128">**Описание**</span><span class="sxs-lookup"><span data-stu-id="a9af9-128">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="a9af9-129">Интегрированные приложения</span><span class="sxs-lookup"><span data-stu-id="a9af9-129">Integrated apps</span></span>  <br/> |<span data-ttu-id="a9af9-130">Вы можете предоставить отдельным приложениям доступ к данным Microsoft 365, например к почте, календарям, контактам, пользователям, группам, файлам и папкам.</span><span class="sxs-lookup"><span data-stu-id="a9af9-130">You can grant individual apps access to your Microsoft 365 data, like mail, calendars, contacts, users, groups, files, and folders.</span></span> <span data-ttu-id="a9af9-131">Вы также можете авторизовать эти приложения на глобальном уровне администратора и сделать их доступными для всей компании, зарегистрировав приложения в Azure AD.</span><span class="sxs-lookup"><span data-stu-id="a9af9-131">You can also authorize these apps at global admin level and make them available to your entire company by registering the apps in Azure AD.</span></span> <span data-ttu-id="a9af9-132">Дополнительные сведения см. [интегрированные приложения и Azure AD для администраторов Microsoft 365](https://support.office.com/article/cb2250e3-451e-416f-bf4e-363549652c2a).</span><span class="sxs-lookup"><span data-stu-id="a9af9-132">For details see [Integrated Apps and Azure AD for Microsoft 365 administrators](https://support.office.com/article/cb2250e3-451e-416f-bf4e-363549652c2a).</span></span>  <br/> <span data-ttu-id="a9af9-133">Кроме того, вы можете просматривать [единый вход в приложения](https://go.microsoft.com/fwlink/p/?LinkId=698604).</span><span class="sxs-lookup"><span data-stu-id="a9af9-133">Also see [single sign-on to applications](https://go.microsoft.com/fwlink/p/?LinkId=698604).</span></span>  <br/> |
|<span data-ttu-id="a9af9-134">PowerApps</span><span class="sxs-lookup"><span data-stu-id="a9af9-134">PowerApps</span></span>  <br/> | <span data-ttu-id="a9af9-135">Приложения Power Apps ориентированы на приложения для мобильных устройств, которые могут подключаться к существующим источникам данных, таким как списки SharePoint и другие приложения для передачи данных.</span><span class="sxs-lookup"><span data-stu-id="a9af9-135">Power apps are focused apps for mobile devices that can connect to your existing data sources like SharePoint lists, and other data apps.</span></span> <span data-ttu-id="a9af9-136">[В статье Создание поверапп для списка на странице SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) и [PowerApps](https://powerapps.microsoft.com/) для получения дополнительных сведений.</span><span class="sxs-lookup"><span data-stu-id="a9af9-136">See [Create a PowerApp for a list in SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) and [PowerApps page](https://powerapps.microsoft.com/) for details.</span></span>  <br/> |
   
<span data-ttu-id="a9af9-137">Узнайте больше об [интегрированных приложениях и Azure AD для администраторов Microsoft 365](integrated-apps-and-azure-ads.md) , а [коллекции приложений Azure AD и единого входа](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-single-sign-on).</span><span class="sxs-lookup"><span data-stu-id="a9af9-137">Learn more at [Integrated Apps and Azure AD for Microsoft 365 administrators](integrated-apps-and-azure-ads.md) and [Azure AD application gallery and single-sign-on](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-single-sign-on).</span></span>

## <a name="see-also"></a><span data-ttu-id="a9af9-138">См. также</span><span class="sxs-lookup"><span data-stu-id="a9af9-138">See also</span></span>

[<span data-ttu-id="a9af9-139">Обзор Microsoft 365 корпоративный</span><span class="sxs-lookup"><span data-stu-id="a9af9-139">Microsoft 365 Enterprise overview</span></span>](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)
