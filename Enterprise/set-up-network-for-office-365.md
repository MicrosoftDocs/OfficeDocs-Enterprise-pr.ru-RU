---
title: Настройка сети для Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/19/2019
audience: ITPro
ms.topic: hub-page
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: ''
description: Сводка. Статьи с общими сведениями об организации сети для Office 365.
ms.openlocfilehash: 725c2470644206045a40816fad3643b83d6c8ea6
ms.sourcegitcommit: f316aef1c122f8eb25c43a56bc894c4aa61c8e0c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2019
ms.locfileid: "38747418"
---
# <a name="set-up-your-network-for-office-365"></a>Настройка сети для Office 365

*Эта статья относится к Office 365 корпоративный и Microsoft 365 корпоративный.*

Важной частью миграции на Office 365 является обеспечение настройки сети и подключений к Интернету для оптимизации доступа. Настройка локальной сети для доступа к глобально распределенным облачным предложениям программного обеспечения как услуги (SaaS) отличается от традиционной сети, оптимизированной для трафика к локальным центрам обработки данных и центрального подключения к Интернету. 

С помощью этих статей можно ознакомиться с основными различиями пограничных устройств, клиентских компьютеров и локальной сети, а также изменять их для обеспечения оптимальной производительности для локальных пользователей.

## <a name="how-office-365-networking-works"></a>Как выполняется организация сети Office 365

В указанных ниже статьях рассматриваются возможности подключения для Office 365.

- [Обзор возможности сетевого подключения к Office 365](office-365-networking-overview.md)
- [Принципы сетевого подключения к Office 365](office-365-network-connectivity-principles.md)
- [Оценка сетевого подключения к Office 365](assessing-network-connectivity.md)

Советы по повышению производительности см. в статье [Планирование сети и настройка производительности для Office 365](network-planning-and-performance.md).

## <a name="support-office-365-networking-as-a-network-equipment-vendor"></a>Поддержка организации сети Office 365 поставщиком сетевого оборудования

Если вы являетесь поставщиком сетевого оборудования, присоединяйтесь к [партнерской программе Office 365 для поставщиков сетевых устройств и служб](office-365-networking-partner-program.md). Зарегистрируйтесь в программе, чтобы встроить принципы сетевого подключения к Office 365 в свои продукты и решения. 

## <a name="office-365-endpoints"></a>Конечные точки Office 365

Конечные точки — это набор конечных IP-адресов, доменных имен DNS и URL-адресов для трафика Office 365 в Интернете. 

Чтобы повысить производительность облачных служб Office 365, некоторым конечным точкам требуется специальная обработка клиентскими браузерами и устройствами в сети периметра. К этим устройствам относятся брандмауэры, устройства расшифровки и анализа SSL-трафика, устройства анализа пакетов и системы защиты от потери данных.

Подробные сведения см. в статье [Управление конечными точками Office 365](managing-office-365-endpoints.md).

В настоящее время существует пять разных облаков Office 365. Эта таблица позволяет перейти к списку конечных точек для каждого из них.

|||
|:-------|:-----|
| [Глобальные конечные точки](urls-and-ip-address-ranges.md) | Конечные точки для подписок на Office 365 во всем мире, которые включают облако сообщества государственных организаций США (GCC). |
| [Конечные точки U.S. Government DoD](office-365-u-s-government-dod-endpoints.md) | Конечные точки для подписок Министерства обороны США (DoD). |
| [Конечные точки U.S. Government GCC High](office-365-u-s-government-gcc-high-endpoints.md) | Конечные точки для подписок GCC High государственных организаций США. |
| [Конечные точки Office 365 под управлением 21Vianet](urls-and-ip-address-ranges-21vianet.md) | Конечные точки для Office 365 под управлением компании 21Vianet, соответствующие требованиям для Office 365 в Китае. |
| [Конечные точки Office 365 Germany](office-365-germany-endpoints.md) | Конечные точки отдельного облака в Европе для наиболее регулируемых клиентов в Германии, Европейском Союзе (ЕС) и Европейской ассоциации свободной торговли (ЕАСТ). |
|||

Чтобы автоматизировать получение актуального списка конечных точек для облачной службы Office 365, см. статью [Веб-служба IP-адресов и URL-адресов в Office 365](office-365-ip-web-service.md).

Сведения о дополнительных конечных точках см. в этих статьях:

- [Дополнительные конечные точки, отсутствующие в веб-службе](additional-office365-ip-addresses-and-urls.md)
- [Сетевые запросы в Office 2016 для Mac](network-requests-in-office-2016-for-mac.md)


## <a name="additional-topics-for-office-365-networking"></a>Дополнительные разделы об организации сети Office 365

Специальные разделы, касающиеся организации сети Office 365, см. в указанных ниже статьях.

- [Сети доставки содержимого](content-delivery-networks.md)
- [Поддержка IPv6 в службах Office 365](ipv6-support.md)
- [Поддержка NAT в Office 365](nat-support-with-office-365.md)

## <a name="expressroute-for-office-365"></a>ExpressRoute для Office 365

Сведения об использовании ExpressRoute для трафика Office 365 см. в указанных ниже статьях.

- [Azure ExpressRoute для Office 365](azure-expressroute.md)
- [Реализация ExpressRoute для Office 365](implementing-expressroute.md)
- [Планирование сети при использовании ExpressRoute для Office 365](network-planning-with-expressroute.md)
- [Маршрутизация с использованием ExpressRoute для Office 365](routing-with-expressroute.md)
