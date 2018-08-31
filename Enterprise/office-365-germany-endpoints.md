---
title: Конечные точки Office 365 Germany
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 8/13/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365_Setup
search.appverid: MOE150
ms.assetid: 8a113a50-0071-4155-bb8e-eba5a8dbd4c8
description: Если ваша организация использует Office 365 и ограничивает компьютеры в сети с подключением к Интернету, Далее вы найдете конечных точек (полные доменные имена, порты, URL-адреса и IPv4 и IPv6 диапазонов адресов), который следует включить в вашей исходящих разрешить списков, чтобы обеспечить вашей компьютеры можно успешно использовать Office 365.
hideEdit: true
ms.openlocfilehash: fa5133391a24a3b9bb82a9dc5065e4dd10bb5bfe
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542298"
---
# <a name="office-365-germany-endpoints"></a><span data-ttu-id="1cde6-103">Конечные точки Office 365 Germany</span><span class="sxs-lookup"><span data-stu-id="1cde6-103">Office 365 Germany endpoints</span></span>

 <span data-ttu-id="1cde6-104">*Применимо к: Администратор Office 365*</span><span class="sxs-lookup"><span data-stu-id="1cde6-104">*Applies To: Office 365 Admin*</span></span>

<span data-ttu-id="1cde6-p101">**Сводка:** Office 365 необходимо подключение к Интернету. Конечные точки ниже, должен быть доступен для клиентов, использующих только планы **Office 365 Германия** .</span><span class="sxs-lookup"><span data-stu-id="1cde6-p101">**Summary:** Office 365 requires connectivity to the Internet. The endpoints below should be reachable for customers using **Office 365 Germany** plans only.</span></span>
  
> [!NOTE]
> <span data-ttu-id="1cde6-p102">Корпорация Майкрософт разрабатывает на основе REST веб-службы для IP-адрес и полное доменное имя записи на этой странице. Эта новая служба помогут настроить и обновления устройств сети периметра брандмауэров и прокси-серверов. Вы можете загрузить список конечных точек, текущую версию списка или определенные изменения. Эта служба заменит XML-документа, RSS-канал и IP-адрес и полное доменное имя записи на этой странице. Чтобы ознакомиться с этой новой службы, перейдите на [веб-службы](managing-office-365-endpoints.md#webservice).</span><span class="sxs-lookup"><span data-stu-id="1cde6-p102">Microsoft is developing a REST-based web service for the IP address and FQDN entries on this page. This new service will help you configure and update network perimeter devices such as firewalls and proxy servers. You can download the list of endpoints, the current version of the list, or specific changes. This service will eventually replace the XML document, RSS feed, and the IP address and FQDN entries on this page. To try out this new service, go to [Web service](managing-office-365-endpoints.md#webservice).</span></span> 
  
 <span data-ttu-id="1cde6-112">**Конечных точках office 365:** [Worldwide (включая GCC)](urls-and-ip-address-ranges.md)   |  [Office 365 обслуживается 21 Vianet](urls-and-ip-address-ranges-21vianet.md)  | *Office 365 Германия* | [Министерства обороны США государственных организаций США Office 365](office-365-u-s-government-dod-endpoints.md) | [Office 365 США государственных GCC высокой](office-365-u-s-government-gcc-high-endpoints.md)  |</span><span class="sxs-lookup"><span data-stu-id="1cde6-112">**Office 365 endpoints:** [Worldwide (including GCC)](urls-and-ip-address-ranges.md)  | [Office 365 operated by 21 Vianet](urls-and-ip-address-ranges-21vianet.md)  | *Office 365 Germany* | [Office 365 U.S. Government DoD](office-365-u-s-government-dod-endpoints.md) | [Office 365 U.S. Government GCC High](office-365-u-s-government-gcc-high-endpoints.md)  |</span></span>
  
|||
|:-----|:-----|
|<span data-ttu-id="1cde6-113">**Последнее обновление:** 7/2/2018 - ![RSS-канал](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [список изменений в конечных точках Office 365 Германия](office-365-germany-endpoints-change-log.md)</span><span class="sxs-lookup"><span data-stu-id="1cde6-113">**Last updated:** 7/2/2018 - ![RSS](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [List of changes to the Office 365 Germany endpoints](office-365-germany-endpoints-change-log.md)</span></span>||

<span data-ttu-id="1cde6-p103">Начать с [конечными точками управления Office 365](managing-office-365-endpoints.md) понять рекомендаций по управлению подключение к сети с помощью этих данных. Конечные точки данных обновляется в начале каждый месяц с новой IP-адресов и URL-адреса опубликовано 30 дней до активности. Это позволяет для пользователей, которые еще не автоматические обновления для выполнения своих процессов до нового подключения является обязательным. Конечные точки также могут быть обновлены в течение месяца, если, необходимые для поддержки эскалации адрес, угрозы безопасности и других интерпретации эксплуатационных требований. Всегда можно найти в [список изменений в конечных точках Office 365 Германия](office-365-germany-endpoints-change-log.md).</span><span class="sxs-lookup"><span data-stu-id="1cde6-p103">Start with [Managing Office 365 endpoints](managing-office-365-endpoints.md) to understand our recommendations for managing network connectivity using this data. Endpoints data is updated at the beginning of each month with new IP Addresses and URLs published 30 days in advance of being active. This allows for customers who do not yet have automated updates to complete their processes before new connectivity is required. Endpoints may also be updated during the month if needed to address support escalations, security incidents, or other immediate operational requirements. You can always refer to the [list of changes to the Office 365 Germany endpoints](office-365-germany-endpoints-change-log.md).</span></span>

<span data-ttu-id="1cde6-p104">Данные, отображаемые на этой странице ниже создается на основе REST веб-службы. При использовании сценария или сетевых устройств для доступа к этим данным, то должны перейти к [веб-службы](managing-office-365-endpoints.md#webservice) непосредственно.</span><span class="sxs-lookup"><span data-stu-id="1cde6-p104">The data shown on this page below is all generated from the REST-based web services. If you are using a script or a network device to access this data, you should go to the [Web service](managing-office-365-endpoints.md#webservice) directly.</span></span>

<span data-ttu-id="1cde6-p105">Конечная точка данных ниже приведены требования к для связи с компьютера пользователя в Office 365. Он не включает сетевых подключений от корпорации Майкрософт в сеть клиента, иногда называемое гибридного или входящие сетевые подключения.</span><span class="sxs-lookup"><span data-stu-id="1cde6-p105">Endpoint data below lists requirements for connectivity from a user’s machine to Office 365. It does not include network connections from Microsoft into a customer network, sometimes called hybrid or inbound network connections.</span></span>

<span data-ttu-id="1cde6-p106">Конечные точки, сгруппированы в четыре области службы. Первый областях три службы можно выбирать для подключения к независимо друг от друга. Четвертая область службы распространенных зависимость (называемые Microsoft 365 общие и Office Online) и всегда должен иметь подключение к сети.</span><span class="sxs-lookup"><span data-stu-id="1cde6-p106">The endpoints are grouped into four service areas. The first three service areas can be independently selected for connectivity. The fourth service area is a common dependency (called Microsoft 365 Common and Office Online) and must always have network connectivity.</span></span>

<span data-ttu-id="1cde6-126">Столбцы данных показано являются:</span><span class="sxs-lookup"><span data-stu-id="1cde6-126">Data columns shown are:</span></span>

- <span data-ttu-id="1cde6-p107">**ID**: идентификатор число строк, также известные как набор конечной точки. Этот идентификатор — так же, как возвращается веб-службой для набора конечных точек.</span><span class="sxs-lookup"><span data-stu-id="1cde6-p107">**ID**: The ID number of the row, also known as an endpoint set. This ID is the same as is returned by the web service for the endpoint set.</span></span>

- <span data-ttu-id="1cde6-p108">**Категории**: показывает, относится ли набор конечной точки к категории «Оптимизировать», «Разрешить» или «По умолчанию». Сведения о следующих категорий и рекомендации по управлению их на [http://aka.ms/pnc](http://aka.ms/pnc). Этот столбец также список, который устанавливает конечной точки должны иметь подключение к сети. Для наборов конечной точки, которые не должны иметь подключение к сети предоставляемая нами заметки в этом поле, чтобы указать, какие функциональные возможности будут отсутствовать, если заблокировано set конечной точки. Если указаны без области всей службы, наборы конечной точки, указано, что требуется не требуют подключения.</span><span class="sxs-lookup"><span data-stu-id="1cde6-p108">**Category**: Shows whether the endpoint set is categorized as “Optimize”, “Allow”, or “Default”. You can read about these categories and guidance for management of them at [http://aka.ms/pnc](http://aka.ms/pnc). This column also lists which endpoint sets are required to have network connectivity. For endpoint sets which are not required to have network connectivity, we provide notes in this field to indicate what functionality would be missing if the endpoint set is blocked. If you are excluding an entire service area, the endpoint sets listed as required do not require connectivity.</span></span>

- <span data-ttu-id="1cde6-p109">**Аварийного восстановления**: это **Да** , если набор конечной точки поддерживается по Azure ExpressRoute с префиксами маршрута Office 365. Сообщество протокола BGP, включающий префиксы маршрут показано коммерческим области службы из списка. При аварийного восстановления — **Нет**, это означает, что ExpressRoute не поддерживается для этого набора конечных точек. Тем не менее следует не считать, что маршруты объявления для набора конечных точек, где аварийного восстановления — **Нет**.</span><span class="sxs-lookup"><span data-stu-id="1cde6-p109">**ER**: This is **Yes** if the endpoint set is supported over Azure ExpressRoute with Office 365 route prefixes. The BGP community that includes the route prefixes shown aligns with the service area listed. When ER is **No**, this means that ExpressRoute is not supported for this endpoint set. However, it should not be assumed that no routes are advertised for an endpoint set where ER is **No**.</span></span>

- <span data-ttu-id="1cde6-p110">**Адреса**: список полных доменных имен или подстановочные знаки доменных имен и диапазоны IP-адрес для набора конечных точек. Обратите внимание на то, что диапазон IP-адрес в формате CIDR и может содержать множество отдельных IP-адресов в указанную сеть.</span><span class="sxs-lookup"><span data-stu-id="1cde6-p110">**Addresses**: Lists the FQDNs or wildcard domain names and IP Address ranges for the endpoint set. Note that an IP Address range is in CIDR format and may include many individual IP Addresses in the specified network.</span></span>
 
- <span data-ttu-id="1cde6-p111">**Порты**: перечислены порты TCP или UDP, которые в сочетании с адреса конечной точки сети. Можно заметить некоторые дублирование диапазонов IP-адрес, где существуют разные порты из списка.</span><span class="sxs-lookup"><span data-stu-id="1cde6-p111">**Ports**: Lists the TCP or UDP ports that are combined with the Addresses to form the network endpoint. You may notice some duplication in IP Address ranges where there are different ports listed.</span></span>

[!INCLUDE [Office 365 Germany endpoints](./includes/office-365-germany-endpoints.md)]

 

