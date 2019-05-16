---
title: Мониторинг подключения к Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 7/6/2017
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 53cdb60c-a6b2-4848-b3ff-e7b75dc3fd1f
description: После развертывания Office 365 вы можете поддерживать подключение к службам Office 365 с помощью описанных ниже средств и методик. Для этого желательно разобраться в официальных рекомендациях по поддержанию работоспособности и непрерывной работы служб, а также использованию Office 365 в медленных сетях. Полезно также задействовать приложение для администраторов Office 365 и добавить в закладки справку для администраторов по Office 365 для бизнеса.
ms.openlocfilehash: ce307e01a3d7da4a24a06e58d293b9598c684d8f
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070055"
---
# <a name="monitor-office-365-connectivity"></a><span data-ttu-id="d731e-105">Мониторинг подключения к Office 365</span><span class="sxs-lookup"><span data-stu-id="d731e-105">Monitor Office 365 connectivity</span></span>

<span data-ttu-id="d731e-p102">После развертывания Office 365 вы можете поддерживать подключение к службам Office 365 с помощью описанных ниже средств и методик. Для этого желательно разобраться в официальных рекомендациях по поддержанию [работоспособности и непрерывной работы служб](https://technet.microsoft.com/library/office-365-service-health.aspx), а также [использованию Office 365 в медленных сетях](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166). Полезно также задействовать [приложение для администраторов Office 365](https://blogs.office.com/2015/03/13/administer-on-the-go-with-the-updated-office-365-admin-app/) и добавить в закладки [справку для администраторов по Office 365 для бизнеса](https://support.office.com/article/17d3ff3f-3601-466e-b5a1-482b31cfb791).</span><span class="sxs-lookup"><span data-stu-id="d731e-p102">Once you've deployed Office 365, you can maintain Office 365 connectivity using some of the tools and techniques below. You'll want to understand the official [Service Health and Continuity](https://technet.microsoft.com/library/office-365-service-health.aspx) guidelines as well as our [Best practices for using Office 365 on a slow network](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166). You'll also want to grab the [Office 365 admin app](https://blogs.office.com/2015/03/13/administer-on-the-go-with-the-updated-office-365-admin-app/) and bookmark our [Office 365 for business - Admin Help](https://support.office.com/article/17d3ff3f-3601-466e-b5a1-482b31cfb791).</span></span>
  
## <a name="monitoring-office-365-connectivity"></a><span data-ttu-id="d731e-109">Мониторинг подключения к Office 365</span><span class="sxs-lookup"><span data-stu-id="d731e-109">Monitoring Office 365 Connectivity</span></span>

|||
|:-----|:-----|
|<span data-ttu-id="d731e-110">**Получение уведомлений о новых конечных точках Office 365**</span><span class="sxs-lookup"><span data-stu-id="d731e-110">**Getting notified of new Office 365 endpoints**</span></span> <br/> |<span data-ttu-id="d731e-p103">Если вы [управляете конечными точками Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a) и хотите получать уведомления при публикации новых конечных точек, вы можете подписаться на наш RSS-канал с помощью любого средства чтения RSS. Кроме того, можно [подписаться через Outlook](https://go.microsoft.com/fwlink/p/?LinkId=532416) или [настроить получение обновлений RSS-канала по электронной почте](https://go.microsoft.com/fwlink/p/?LinkId=532417).  </span><span class="sxs-lookup"><span data-stu-id="d731e-p103">If you're [Managing Office 365 endpoints](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a), you'll want to receive notifications when we publish new endpoints, you can subscribe to our RSS feed using your favorite RSS reader. Here is how to [subscribe via Outlook](https://go.microsoft.com/fwlink/p/?LinkId=532416) or you can [have the RSS feed updates emailed to you](https://go.microsoft.com/fwlink/p/?LinkId=532417).  </span></span><br/> |
|<span data-ttu-id="d731e-113">**Использование System Center для наблюдения за Office 365**</span><span class="sxs-lookup"><span data-stu-id="d731e-113">**Use System Center to Monitor Office 365**</span></span> <br/> |<span data-ttu-id="d731e-p104">Если вы используете Microsoft System Center, вы можете скачать [пакет управления System Center для Office 365](https://www.microsoft.com/download/details.aspx?id=43708), чтобы сразу начать мониторинг Office 365. Подробные инструкции см. в руководстве по работе с пакетом управления или в записи блога [Мониторинг Office 365 с помощью System Centre Operations Manager](https://blogs.msdn.com/b/mvpawardprogram/archive/2015/07/08/office365-monitoring-using-system-centre-operations-manager.aspx)</span><span class="sxs-lookup"><span data-stu-id="d731e-p104">If you're using Microsoft System Center, you can download the [System Center Management Pack for Office 365](https://www.microsoft.com/download/details.aspx?id=43708) to begin monitoring Office 365 today. For more detailed guidance, please see the management pack operations guide or this blog post [Office365 Monitoring using System Centre Operations Manager](https://blogs.msdn.com/b/mvpawardprogram/archive/2015/07/08/office365-monitoring-using-system-centre-operations-manager.aspx)</span></span> <br/> |
|<span data-ttu-id="d731e-116">**Наблюдение за работоспособностью Azure ExpressRoute**</span><span class="sxs-lookup"><span data-stu-id="d731e-116">**Monitoring the health of Azure ExpressRoute**</span></span> <br/> |<span data-ttu-id="d731e-117">Если вы подключаетесь к Office 365 с помощью Azure ExpressRoute для Office 365, рекомендуется использовать как панель мониторинга работоспособности Office 365, так и Azure для [экономии времени по устранению неполадок с помощью службы "Работоспособность ресурсов Azure"](https://azure.microsoft.com/blog/reduce-troubleshooting-time-with-azure-resource-health/)</span><span class="sxs-lookup"><span data-stu-id="d731e-117">If you are connecting to Office 365 using Azure ExpressRoute for Office 365, you'll want to ensure that you're using both the Office 365 Service Health Dashboard as well as the Azure [Reducing troubleshooting time with Azure Resource health](https://azure.microsoft.com/blog/reduce-troubleshooting-time-with-azure-resource-health/)</span></span> <br/> |
|<span data-ttu-id="d731e-118">**Использование Azure AD Connect Health с AD FS**</span><span class="sxs-lookup"><span data-stu-id="d731e-118">**Using Azure AD Connect Health with AD FS**</span></span> <br/> |<span data-ttu-id="d731e-119">Если вы используете AD FS для единого входа в Office 365, рекомендуем вам начать [использовать службу Azure AD Connect Health для мониторинга своей инфраструктуры AD FS](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect-health-adfs/).</span><span class="sxs-lookup"><span data-stu-id="d731e-119">If you're using AD FS for Single Sign-On with Office 365, you'll want to begin [using Azure AD Connect Health to monitor your AD FS infrastructure](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect-health-adfs/).</span></span>  <br/> |
|<span data-ttu-id="d731e-120">**Программный мониторинг Office 365**</span><span class="sxs-lookup"><span data-stu-id="d731e-120">**Programmatically monitor Office 365**</span></span> <br/> |<span data-ttu-id="d731e-121">См. наше руководство по [API управления Office 365](https://docs.microsoft.com/office/office-365-management-api/office-365-management-apis-overview).</span><span class="sxs-lookup"><span data-stu-id="d731e-121">Refer to our guidance on the [Office 365 Management API](https://docs.microsoft.com/office/office-365-management-api/office-365-management-apis-overview).</span></span>  <br/> |

<span data-ttu-id="d731e-122">Вы можете быстро вернуться сюда с помощью этой короткой ссылки: [hhttps://aka.ms/monitorconnectivity365](https://aka.ms/monitorconnectivity365)</span><span class="sxs-lookup"><span data-stu-id="d731e-122">Here's a short link you can use to come back: [hhttps://aka.ms/monitorconnectivity365](https://aka.ms/monitorconnectivity365)</span></span>
  
## <a name="see-also"></a><span data-ttu-id="d731e-123">См. также</span><span class="sxs-lookup"><span data-stu-id="d731e-123">See also</span></span>

[<span data-ttu-id="d731e-124">Настройка служб и приложений Office 365 корпоративный</span><span class="sxs-lookup"><span data-stu-id="d731e-124">Configure Office 365 Enterprise services and applications</span></span>](configure-services-and-applications.md)
  
[<span data-ttu-id="d731e-125">Подготовка организации к миграции на Office 365 корпоративный</span><span class="sxs-lookup"><span data-stu-id="d731e-125">Get your organization ready for Office 365 Enterprise</span></span>](get-your-organization-ready-for-office-365.md)
  
[<span data-ttu-id="d731e-126">Планирование сети и настройка производительности для Office 365</span><span class="sxs-lookup"><span data-stu-id="d731e-126">Network planning and performance tuning for Office 365</span></span>](network-planning-and-performance.md)
  
[<span data-ttu-id="d731e-127">Интеграция Office 365 с локальными средами</span><span class="sxs-lookup"><span data-stu-id="d731e-127">Office 365 integration with on-premises environments</span></span>](office-365-integration.md)
  
[<span data-ttu-id="d731e-128">Управление конечными точками Office 365</span><span class="sxs-lookup"><span data-stu-id="d731e-128">Managing Office 365 endpoints</span></span>](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
