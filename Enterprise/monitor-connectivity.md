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
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 53cdb60c-a6b2-4848-b3ff-e7b75dc3fd1f
description: После развертывания Office 365 вы можете поддерживать подключение к службам Office 365 с помощью описанных ниже средств и методик. Для этого желательно разобраться в официальных рекомендациях по поддержанию работоспособности и непрерывной работы служб, а также использованию Office 365 в медленных сетях. Полезно также задействовать приложение для администраторов Office 365 и добавить в закладки справку для администраторов по Office 365 для бизнеса.
ms.openlocfilehash: 5a0a6e217d0f74f6266bffa1bd6037427f14e7bd
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/07/2020
ms.locfileid: "41843710"
---
# <a name="monitor-office-365-connectivity"></a>Мониторинг подключения к Office 365

После развертывания Office 365 вы можете поддерживать подключение к службам Office 365 с помощью описанных ниже средств и методик. Для этого желательно разобраться в официальных рекомендациях по поддержанию [работоспособности и непрерывной работы служб](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/service-health-and-continuity), а также [использованию Office 365 в медленных сетях](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166). Полезно также задействовать [приложение для администраторов Office 365](https://blogs.office.com/2015/03/13/administer-on-the-go-with-the-updated-office-365-admin-app/) и добавить в закладки [справку для администраторов по Office 365 для бизнеса](https://support.office.com/article/17d3ff3f-3601-466e-b5a1-482b31cfb791).
  
## <a name="monitoring-office-365-connectivity"></a>Мониторинг подключения к Office 365

|||
|:-----|:-----|
|**Получение уведомлений о новых конечных точках Office 365** <br/> |Если вы [управляете конечными точками Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a) и хотите получать уведомления при публикации новых конечных точек, вы можете подписаться на наш RSS-канал с помощью любого средства чтения RSS. Кроме того, можно [подписаться через Outlook](https://go.microsoft.com/fwlink/p/?LinkId=532416) или [настроить получение обновлений RSS-канала по электронной почте](https://go.microsoft.com/fwlink/p/?LinkId=532417).  <br/> |
|**Использование System Center для наблюдения за Office 365** <br/> |Если вы используете Microsoft System Center, вы можете скачать [пакет управления System Center для Office 365](https://www.microsoft.com/download/details.aspx?id=43708), чтобы сразу начать мониторинг Office 365. Подробные инструкции см. в руководстве по работе с пакетом управления или в записи блога [Мониторинг Office 365 с помощью System Centre Operations Manager](https://blogs.msdn.com/b/mvpawardprogram/archive/2015/07/08/office365-monitoring-using-system-centre-operations-manager.aspx) <br/> |
|**Наблюдение за работоспособностью Azure ExpressRoute** <br/> |Если вы подключаетесь к Office 365 с помощью Azure ExpressRoute для Office 365, рекомендуется использовать как панель мониторинга работоспособности Office 365, так и Azure для [экономии времени по устранению неполадок с помощью службы "Работоспособность ресурсов Azure"](https://azure.microsoft.com/blog/reduce-troubleshooting-time-with-azure-resource-health/) <br/> |
|**Использование Azure AD Connect Health с AD FS** <br/> |Если вы используете AD FS для единого входа в Office 365, рекомендуем вам начать [использовать службу Azure AD Connect Health для мониторинга своей инфраструктуры AD FS](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect-health-adfs/).  <br/> |
|**Программный мониторинг Office 365** <br/> |См. наше руководство по [API управления Office 365](https://docs.microsoft.com/office/office-365-management-api/office-365-management-apis-overview).  <br/> |

Вы можете быстро вернуться сюда с помощью этой короткой ссылки: [https://aka.ms/monitorconnectivity365](https://aka.ms/monitorconnectivity365)
  
## <a name="see-also"></a>См. также

[Настройка служб и приложений Office 365 корпоративный](configure-services-and-applications.md)
  
[Подготовка организации к миграции на Office 365 корпоративный](get-your-organization-ready-for-office-365.md)
  
[Планирование сети и настройка производительности для Office 365](network-planning-and-performance.md)
  
[Интеграция Office 365 с локальными средами](office-365-integration.md)
  
[Управление конечными точками Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
