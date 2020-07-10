---
title: Конечные точки DoD Office 365 для государственных учреждений (США)
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
search.appverid:
- OGA150
- OGC150
- OGD150
- MOE150
ms.assetid: 5d7dce60-4892-4b58-b45e-ee42fe8a907f
f1.keywords:
- NOCSH
description: Сводка. для Office 365 требуется подключение к Интернету. Конечные точки, расположенные ниже, должны быть достижимыми для клиентов, использующих только планы DoD Office 365 США.
hideEdit: true
ms.openlocfilehash: 824998ea1bcb89a151e9d249d9155bf5e9d785dc
ms.sourcegitcommit: 338e3bcf0a62842fbbb17145b67a4a93f3b90aac
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/09/2020
ms.locfileid: "45091196"
---
# <a name="office-365-us-government-dod-endpoints"></a>Конечные точки DoD Office 365 для государственных учреждений (США)

*Область применения: Office 365 Admin*

 Для Office 365 требуется подключение к Интернету. Конечные точки, расположенные ниже, должны быть достижимыми для клиентов, использующих только планы DoD Office 365 США.
  
> [!NOTE]
> Microsoft has released a REST-based web service for the IP address and FQDN entries on this page. This new service will help you configure and update network perimeter devices such as firewalls and proxy servers. You can download the list of endpoints, the current version of the list, or specific changes. This service replaces the XML document linked from this page, which was deprecated on October 2, 2018. To try out this new service, go to [Web service](office-365-ip-web-service.md).
  
 **Конечные точки Office 365:**[ по всему миру (включая GCC)](urls-and-ip-address-ranges.md) | [Office 365, предоставляемый 21 Vianet](urls-and-ip-address-ranges-21vianet.md)  | [Office 365 Germany](office-365-germany-endpoints.md) | *Office 365 для DoD государственных организаций США* | [Office 365 для GCC High государственных организаций США](office-365-u-s-government-gcc-high-endpoints.md) |
  
|||
|:-----|:-----|
|**Последнее обновление:** 07/09/2020 — ![ ](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [Подписка на журнал изменений](https://endpoints.office.com/version/USGOVDoD?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) RSS <br/> |**Download:** полный список в [формате JSON](https://endpoints.office.com/endpoints/USGOVDoD?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) <br/> |

 Начните с [управления конечными точками Office 365](managing-office-365-endpoints.md) , чтобы узнать, какие рекомендации по управлению сетевым подключением с помощью этих данных. Данные конечных точек обновляются в начале каждого месяца с новыми IP-адресами и URL-адресами, опубликованными в течение 30 дней до момента активации. Это позволяет пользователям, у которых еще не было автоматизированное обновление, завершить свои процессы, прежде чем потребуется новое подключение. Конечные точки также могут быть обновлены в течение месяца при необходимости обращения к укрупнению поддержки, происшествиям безопасности или другим немедленным рабочим требованиям. Данные, показанные на этой странице, созданы на основе веб-служб REST. Если вы используете сценарий или сетевое устройство для доступа к этим данным, перейдите непосредственно к [веб-службе](office-365-ip-web-service.md) .

Ниже приведены требования к данным конечной точки для подключения компьютера пользователя к Office 365. Он не включает сетевые подключения от корпорации Майкрософт к клиентской сети, иногда называемые гибридными или входящими сетевыми подключениями. Дополнительные сведения приведены в статье [дополнительные конечные точки, не включенные в веб-службу](additional-office365-ip-addresses-and-urls.md). 

The endpoints are grouped into four service areas. The first three service areas can be independently selected for connectivity. The fourth service area is a common dependency (called Microsoft 365 Common and Office) and must always have network connectivity.

Показанные столбцы с данными:

- **ID**: The ID number of the row, also known as an endpoint set. This ID is the same as is returned by the web service for the endpoint set.

- **Category**: Shows whether the endpoint set is categorized as “Optimize”, “Allow”, or “Default”. You can read about these categories and guidance for management of them at [https://aka.ms/pnc](https://aka.ms/pnc). This column also lists which endpoint sets are required to have network connectivity. For endpoint sets which are not required to have network connectivity, we provide notes in this field to indicate what functionality would be missing if the endpoint set is blocked. If you are excluding an entire service area, the endpoint sets listed as required do not require connectivity.

- **ER**: **Да** , если набор конечных точек поддерживается через Azure ExpressRoute с префиксами маршрутизации Office 365. Сообщество BGP, содержащее префиксы маршрутов, которые отображаются в списке, соответствует области службы. Если параметр ER имеет значение " **нет**", это означает, что для этого набора конечных точек не поддерживается ExpressRoute. Однако он не должен предполагать, что для набора конечных точек не было объявлено ни одного маршрута, где ER — **No**. Если вы планируете использовать Azure AD Connect, ознакомьтесь с [разделом специальные факторы](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-instances#microsoft-azure-government) , чтобы убедиться, что у вас есть соответствующая конфигурация Azure AD Connect.

- **Addresses**: Lists the FQDNs or wildcard domain names and IP Address ranges for the endpoint set. Note that an IP Address range is in CIDR format and may include many individual IP Addresses in the specified network.
 
- **Ports**: Lists the TCP or UDP ports that are combined with the Addresses to form the network endpoint. You may notice some duplication in IP Address ranges where there are different ports listed.
 
[!INCLUDE [Office 365 U.S. Government DoD endpoints](./includes/office-365-u.s.-government-dod-endpoints.md)]
  
Примечания для таблицы.

- Центр безопасности и соответствия требованиям (SCC) предоставляет поддержку Azure ExpressRoute для Office 365. Это относится ко многим функциям, предоставляемым в SCC, например отчетам, аудиту, расширенному обнаружению электронных данных, единой системе защиты от потери данных и управлению данными. Два отдельных компонента: экспорт PST-файлов и обнаружение электронных данных, в настоящее время не поддерживаются Azure ExpressRoute с фильтрами маршрутов Office 365, вызванных зависимостью от их зависимости в хранилище больших двоичных объектов Azure. Чтобы использовать эти функции, вам потребуется отдельное подключение к хранилищу больших двоичных объектов Azure, используя любые поддерживаемые варианты подключения Azure, которые включают подключение к Интернету или Azure ExpressRoute с помощью фильтров маршрутизации Azure public. Для обоих этих функций необходимо оценить установленное подключение. Группа Office 365 Information Protection осведомлена об этом ограничении и активно работает над обеспечением поддержки Azure ExpressRoute для Office 365 в соответствии с фильтрами маршрутов Office 365 для обоих этих функций.

- Существуют дополнительные необязательные конечные точки для приложений Microsoft 365 для предприятий, которые не указаны в списке и не требуются пользователям для запуска приложений Microsoft 365 для корпоративных приложений и редактирования документов. Дополнительные конечные точки размещаются в центрах обработки данных Майкрософт и не обрабатывают, не передают и не хранят данные о клиентах. Мы рекомендуем пользователям подключаться к этим конечным точкам по умолчанию на периметр выхода в Интернет.
