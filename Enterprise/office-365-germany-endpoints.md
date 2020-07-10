---
title: Конечные точки Office 365 Germany
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/09/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom: Adm_O365_Setup
search.appverid: MOE150
ms.assetid: 8a113a50-0071-4155-bb8e-eba5a8dbd4c8
description: Если в вашей организации используется Office 365 и компьютеры сети не подключаются к Интернету, ниже вы найдете конечные точки (FQDN, Ports, URL-адреса, а также диапазоны адресов IPv4 и IPv6), которые следует включить в списки разрешенных исходящих подключений, чтобы убедиться, что компьютеры могут успешно использовать Office 365.
hideEdit: true
ms.openlocfilehash: a0f7f0ac9892363c5f60c509c1e48d7f16f4d96d
ms.sourcegitcommit: 338e3bcf0a62842fbbb17145b67a4a93f3b90aac
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/09/2020
ms.locfileid: "45091156"
---
# <a name="office-365-germany-endpoints"></a>Конечные точки Office 365 Germany

 *Область применения: Office 365 Admin*

Для Office 365 требуется подключение к Интернету. Конечные точки, расположенные ниже, должны быть достижимыми для клиентов, использующих только планы **Office 365 в Германии** .
  
> [!NOTE]
> Microsoft has released a REST-based web service for the IP address and FQDN entries on this page. This new service will help you configure and update network perimeter devices such as firewalls and proxy servers. You can download the list of endpoints, the current version of the list, or specific changes. This service replaces the XML document linked from this page, which was deprecated on October 2, 2018. To try out this new service, go to [Web service](office-365-ip-web-service.md).
 
 **Конечные точки Office 365:**[ по всему миру (включая GCC)](urls-and-ip-address-ranges.md)  | [Office 365, предоставляемый 21 Vianet](urls-and-ip-address-ranges-21vianet.md)  | *Office 365 Germany* | [Office 365 для DoD государственных организаций США](office-365-u-s-government-dod-endpoints.md) | [Office 365 для GCC High государственных организаций США](office-365-u-s-government-gcc-high-endpoints.md)  |
  
|||
|:-----|:-----|
|**Последнее обновление:** 07/09/2020 — ![ ](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [Подписка на журнал изменений](https://endpoints.office.com/version/Germany?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) RSS |**Скачивание:** все обязательные и необязательные назначения в одном списке [в формате JSON](https://endpoints.office.com/endpoints/Germany?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).  <br/> |

Начните с [управления конечными точками Office 365](managing-office-365-endpoints.md) , чтобы узнать, какие рекомендации по управлению сетевым подключением с помощью этих данных. Данные конечных точек обновляются в начале каждого месяца с новыми IP-адресами и URL-адресами, опубликованными в течение 30 дней до момента активации. Это позволяет пользователям, у которых еще не было автоматизированное обновление, завершить свои процессы, прежде чем потребуется новое подключение. Конечные точки также могут быть обновлены в течение месяца при необходимости обращения к укрупнению поддержки, происшествиям безопасности или другим немедленным рабочим требованиям. Вы всегда можете обратиться к [подписке на журнал изменений](https://endpoints.office.com/version/Germany?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).

Данные, показанные на этой странице, созданы на основе веб-служб REST. Если вы используете сценарий или сетевое устройство для доступа к этим данным, перейдите непосредственно к [веб-службе](office-365-ip-web-service.md) .

Endpoint data below lists requirements for connectivity from a user’s machine to Office 365. It does not include network connections from Microsoft into a customer network, sometimes called hybrid or inbound network connections.

The endpoints are grouped into four service areas. The first three service areas can be independently selected for connectivity. The fourth service area is a common dependency (called Microsoft 365 Common and Office) and must always have network connectivity.

Показанные столбцы с данными:

- **ID**: The ID number of the row, also known as an endpoint set. This ID is the same as is returned by the web service for the endpoint set.

- **Category**: Shows whether the endpoint set is categorized as “Optimize”, “Allow”, or “Default”. You can read about these categories and guidance for management of them at [https://aka.ms/pnc](https://aka.ms/pnc). This column also lists which endpoint sets are required to have network connectivity. For endpoint sets which are not required to have network connectivity, we provide notes in this field to indicate what functionality would be missing if the endpoint set is blocked. If you are excluding an entire service area, the endpoint sets listed as required do not require connectivity.

- **ER**: This is **Yes** if the endpoint set is supported over Azure ExpressRoute with Office 365 route prefixes. The BGP community that includes the route prefixes shown aligns with the service area listed. When ER is **No**, this means that ExpressRoute is not supported for this endpoint set. However, it should not be assumed that no routes are advertised for an endpoint set where ER is **No**.

- **Addresses**: Lists the FQDNs or wildcard domain names and IP Address ranges for the endpoint set. Note that an IP Address range is in CIDR format and may include many individual IP Addresses in the specified network.
 
- **Ports**: Lists the TCP or UDP ports that are combined with the Addresses to form the network endpoint. You may notice some duplication in IP Address ranges where there are different ports listed.

[!INCLUDE [Office 365 Germany endpoints](./includes/office-365-germany-endpoints.md)]

 

