---
title: Поддержка протокола IPv6 в службах Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 10/10/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: c08786fb-298e-437c-8222-dab7625fc815
description: 'Сводка: Описание поддержки IPv6 в компонентах Microsoft Office 365 и в предложениях Office 365 для государственных учреждений.'
ms.openlocfilehash: ed06f1eac3c6a3d631445db1d623bd25c62a309c
ms.sourcegitcommit: ae7f2087d51698d3c5ef371888278544a7046205
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/10/2018
ms.locfileid: "25493834"
---
# <a name="ipv6-support-in-office-365-services"></a><span data-ttu-id="137da-103">Поддержка протокола IPv6 в службах Office 365</span><span class="sxs-lookup"><span data-stu-id="137da-103">IPv6 support in Office 365 services</span></span>

 <span data-ttu-id="137da-104">**Сводка**: Описание поддержки IPv6 в компонентах Microsoft Office 365 и в предложениях Office 365 для государственных учреждений.</span><span class="sxs-lookup"><span data-stu-id="137da-104">**Summary**: Describes IPv6 support in Microsoft Office 365 components and in Office 365 government offerings.</span></span>
  
<span data-ttu-id="137da-p101">Office 365 поддерживает IPv6 и IPv4; Однако не все возможности Office 365 полностью включен с IPv6. Это означает, что необходимо использовать IPv4 и IPv6 для подключения к Office 365. Если используется фильтрация исходящего трафика в Office 365, полный список адресов IPv6, поддерживаемых приложением Office 365 можно найти в статье [Office 365 URL-адреса и диапазоны IP-адресов](https://go.microsoft.com/fwlink/?LinkId=293744). После настройки сети и могут адреса IPv6, можно загрузить [план тестирования Office 365 IPv6](https://go.microsoft.com/fwlink/?LinkId=293447) из центра загрузки Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="137da-p101">Office 365 supports both IPv6 and IPv4; however, not all Office 365 features are fully enabled with IPv6. This means that you must use both IPv4 and IPv6 to connect to Office 365. If you are filtering your outbound traffic to Office 365, the full list of IPv6 addresses that are supported by Office 365 can be found in the article [Office 365 URLs and IP address ranges](https://go.microsoft.com/fwlink/?LinkId=293744). After your network is configured and the appropriate IPv6 addresses are allowed, you can download the [Office 365 IPv6 test plan](https://go.microsoft.com/fwlink/?LinkId=293447) from the Microsoft Download Center.</span></span>
  
||
|:-----|
| <span data-ttu-id="137da-109">В этой статье является частью [сети планирование и настройка производительности для Office 365](https://aka.ms/tune).</span><span class="sxs-lookup"><span data-stu-id="137da-109">This article is part of [Network planning and performance tuning for Office 365](https://aka.ms/tune).</span></span>|

## <a name="ipv6-support-in-office-365-subscription-service"></a><span data-ttu-id="137da-110">Поддержка протокола IPv6 в службе подписки Office 365</span><span class="sxs-lookup"><span data-stu-id="137da-110">IPv6 support in Office 365 subscription service</span></span>

### <a name="exchange-online-and-ipv6"></a><span data-ttu-id="137da-111">Exchange Online и IPv6</span><span class="sxs-lookup"><span data-stu-id="137da-111">Exchange Online and IPv6</span></span>

<span data-ttu-id="137da-p102">Если программа, используемая для подключения к Exchange Online поддерживает IPv6, она будет использовать IPv6 на проводной и беспроводной сети по умолчанию. Если вы хотите управлять коммуникаций в Exchange Online, используйте диапазоны IP-адресов в [Office 365 URL-адреса и диапазоны IP-адресов](https://go.microsoft.com/fwlink/?LinkId=293744).</span><span class="sxs-lookup"><span data-stu-id="137da-p102">If the program that you use to connect to Exchange Online supports IPv6, it will use IPv6 by default on both wired and wireless networks. If you want to control communications to Exchange Online, use the IP address ranges in [Office 365 URLs and IP address ranges](https://go.microsoft.com/fwlink/?LinkId=293744).</span></span>
  
### <a name="sharepoint-online-and-ipv6"></a><span data-ttu-id="137da-114">SharePoint Online и IPv6</span><span class="sxs-lookup"><span data-stu-id="137da-114">SharePoint Online and IPv6</span></span>

 <span data-ttu-id="137da-115">**Office 365 для государственных организаций G1/G3/G4/K1** Если программа, используемая для подключения к SharePoint Online поддерживает IPv6, она будет использовать IPv6 по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="137da-115">**Office 365 Government G1/G3/G4/K1** If the program that you use to connect to SharePoint Online supports IPv6, it will attempt to use IPv6 by default.</span></span>
  
 <span data-ttu-id="137da-p103">**Общедоступное облако несколькими клиентами** Microsoft SharePoint Online IPv6 позволяет по вашему запросу. Необходимо указать, что CIDR собой IP-адресов для инфраструктуры DNS. Имейте в виду, что эта инфраструктура DNS не может совместно с другими организациями для IPv6, чтобы включить для клиента. После включения IPv6, если программа, используемая для подключения к SharePoint Online поддерживает IPv6, по умолчанию используется IPv6.</span><span class="sxs-lookup"><span data-stu-id="137da-p103">**Public multi-tenant cloud** Microsoft enables SharePoint Online IPv6 at your request. You need to provide the CIDR notated IP addresses for your organization's DNS infrastructure. Keep in mind that this DNS infrastructure can't be shared by other organizations for IPv6 to be enabled for your tenant. After IPv6 is enabled, if the program that you use to connect to SharePoint Online supports IPv6, it uses IPv6 by default.</span></span>
  
<span data-ttu-id="137da-p104">Если программа, используемая для подключения к SharePoint Online поддерживает IPv6, она будет использовать IPv6 на проводной и беспроводной сети по умолчанию. Если вы хотите управлять объявлений в SharePoint Online, используйте диапазоны IP-адресов в [Office 365 URL-адреса и диапазоны IP-адресов](https://go.microsoft.com/fwlink/?LinkId=293744).</span><span class="sxs-lookup"><span data-stu-id="137da-p104">If the program that you use to connect to SharePoint Online supports IPv6, it will use IPv6 by default on both wired and wireless networks. If you want to control communications to SharePoint Online, use the IP address ranges in [Office 365 URLs and IP address ranges](https://go.microsoft.com/fwlink/?LinkId=293744).</span></span>
  
 <span data-ttu-id="137da-122">**Office 365 для государственных организаций G1/G3/G4/K1** Если программа, используемая для подключения к SharePoint Online поддерживает IPv6, она будет использовать IPv6 по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="137da-122">**Office 365 Government G1/G3/G4/K1** If the program that you use to connect to SharePoint Online supports IPv6, it will attempt to use IPv6 by default.</span></span>
  
### <a name="skype-for-business-and-ipv6"></a><span data-ttu-id="137da-123">Скайп для бизнеса, так и IPv6</span><span class="sxs-lookup"><span data-stu-id="137da-123">Skype for Business and IPv6</span></span>

<span data-ttu-id="137da-p105">Корпорация Майкрософт будет включить IPv6 на Скайп для бизнеса по вашему запросу общедоступное облако несколькими клиентами и в Office 365 для государственных организаций G1/G3/G4/K1 подписок. После включения, если программа, используемая для подключения к Скайп для бизнеса поддерживает IPv6, он будет использовать IPv6 по умолчанию. Если вы хотите управлять объявлений в Скайп для бизнеса, используйте диапазоны IP-адресов в [Office 365 URL-адреса и диапазоны IP-адресов](https://go.microsoft.com/fwlink/?LinkId=293744).</span><span class="sxs-lookup"><span data-stu-id="137da-p105">Microsoft will enable IPv6 for Skype for Business at your request in the public multi-tenant cloud and in Office 365 Government G1/G3/G4/K1 subscriptions. After it's enabled, if the program that you use to connect to Skype for Business supports IPv6, it will use IPv6 by default. If you want to control communications to Skype for Business, use the IP address ranges in [Office 365 URLs and IP address ranges](https://go.microsoft.com/fwlink/?LinkId=293744).</span></span>
  
<span data-ttu-id="137da-127">Имейте в виду, IPv6 доступна не во всех регионах и корпорация Майкрософт не удается включить его для вашего клиента в данный момент.</span><span class="sxs-lookup"><span data-stu-id="137da-127">Please be aware IPv6 is not available in all regions and Microsoft may not be able to activate it for your Tenant at this time.</span></span>
  
### <a name="exchange-online-protection-and-ipv6"></a><span data-ttu-id="137da-128">Exchange Online Protection и IPv6</span><span class="sxs-lookup"><span data-stu-id="137da-128">Exchange Online Protection and IPv6</span></span>

<span data-ttu-id="137da-p106">Exchange Online Protection (EOP) поддерживает IPv6, если передача происходит через транспортный протокол безопасности. Для диапазона EOP используйте [Office 365 URL-адреса и диапазоны IP-адресов](https://go.microsoft.com/fwlink/?LinkId=293744).</span><span class="sxs-lookup"><span data-stu-id="137da-p106">Exchange Online Protection (EOP) supports IPv6 if the transmission occurs over Transport Layer Security Protocol. For the EOP range, use [Office 365 URLs and IP address ranges](https://go.microsoft.com/fwlink/?LinkId=293744).</span></span>
  
### <a name="ipv6-support-for-office-365-government-offerings"></a><span data-ttu-id="137da-131">Поддержка IPv6 в предложениях Office 365 для государственных организаций</span><span class="sxs-lookup"><span data-stu-id="137da-131">IPv6 support for Office 365 government offerings</span></span>

<span data-ttu-id="137da-p107">Поддержка протокола IPv6 Office 365 для государственных организаций и услуги соответствует Управление организацией и меморандум бюджета (OMB) для главного руководителей информационных отделов отделы руководителю и органов (en), а также Федеральное государственных внедрения из протокол Интернета версии 6 (IPv6 ) меморандум. [Microsoft Office 365 для государственных учреждений](https://go.microsoft.com/fwlink/p/?LinkId=325414) — это служба несколькими клиентами, в которой хранятся "мне НРАВИТСЯ" государственных данных в облаке раздельные сообщества. Как и другие услуги Office 365 его предоставляет службы повышения производительности и совместной работы, включая Exchange Online Скайп для бизнеса, SharePoint Online и Office профессиональный плюс. Услуги государственных организаций Microsoft Office 365 применяются только для 2013 и более поздних версий. Дополнительные сведения о предложениях Office 365 государственных учреждений можно [объявление о Office 365 для государственных организаций: "мне Нравится" облако сообщества госучреждений](https://go.microsoft.com/fwlink/p/?LinkId=325414). Международный трафика в руки нормы (соответствующих международным правилам ТОРГОВЛИ) — это набор законодательства США, которые управляют экспорта и импорта связанных с защитой статей и службы на [Список Munitions США (USML)](https://go.microsoft.com/fwlink/p/?LinkId=325415). Microsoft Office 365 для предприятий предоставляет выделенного услуги размещения для повышения производительности решения Майкрософт, которые поддерживают безопасности, конфиденциальности и обеспечение соответствия законодательным нормам требования для НАС федеральных органов, требующие Федеральное информационной безопасности Управление (FISMA) сертификации и коммерческие сущности может быть соответствующих международным правилам ТОРГОВЛИ.</span><span class="sxs-lookup"><span data-stu-id="137da-p107">Office 365 IPv6 support for government offerings conforms to the Office of Management and Budget (OMB) Memorandum for Chief Information Officers of Executive Departments and Agencies, as well as the Federal Government Adoption of Internet Protocol Version 6 (IPv6) memorandum. [Microsoft Office 365 for Government](https://go.microsoft.com/fwlink/p/?LinkId=325414) is a multi-tenant service that stores US government data in a segregated community cloud. Like other Office 365 offerings, it provides productivity and collaboration services, including Exchange Online, Skype for Business, SharePoint Online, and Office Professional Plus. The Microsoft Office 365 government offerings apply only for 2013 and later. For more information about the Office 365 government offerings, see [Announcing Office 365 for Government: A US Government Community Cloud](https://go.microsoft.com/fwlink/p/?LinkId=325414). International Traffic in Arms Regulations (ITAR) is a set of US government regulations that control the export and import of defense-related articles and services on the [United States Munitions List (USML)](https://go.microsoft.com/fwlink/p/?LinkId=325415). Microsoft Office 365 for Enterprises provides dedicated hosting services for Microsoft productivity solutions that support the security, privacy, and regulatory compliance requirements for US federal agencies requiring Federal Information Security Management (FISMA) certification and commercial entities subject to ITAR.</span></span>
  
## <a name="things-to-consider-when-using-ipv6-and-office-365"></a><span data-ttu-id="137da-139">Что следует учесть при использовании IPv6 с Office 365</span><span class="sxs-lookup"><span data-stu-id="137da-139">Things to consider when using IPv6 and Office 365</span></span>

<span data-ttu-id="137da-p108">Мы рекомендуем не отключайте IPv6. Дополнительные сведения можно [IPv6 для Microsoft Windows: вопросы и ответы](https://go.microsoft.com/fwlink/p/?LinkId=325418). Чтобы определить, какие версии IP-адресов, используемых в сети, необходимо учитывайте следующее:</span><span class="sxs-lookup"><span data-stu-id="137da-p108">We recommend that you do not disable IPv6. For more information, see [IPv6 for Microsoft Windows: Frequently Asked Questions](https://go.microsoft.com/fwlink/p/?LinkId=325418). To determine what IP versions are being used on your network, consider the following:</span></span>
  
- <span data-ttu-id="137da-143">Если отображаемое команды IPConfig в командной строке, содержит строку «IPv6-адрес» или «Временный IPv6-адрес», у вас есть IPv6 в вашей среде.</span><span class="sxs-lookup"><span data-stu-id="137da-143">If the display of the IPConfig command at the command prompt contains rows named "IPv6 Address" or "Temporary IPv6 Address," you have IPv6 in your environment.</span></span>

- <span data-ttu-id="137da-144">Если все адреса IPv6 начинаются с «fe80» и соответствуют строкам с названием «Локальный IPv6-адрес», в вашей среде не нужно IPv6.</span><span class="sxs-lookup"><span data-stu-id="137da-144">If all the IPv6 addresses begin with "fe80" and correspond to rows named "Link-Local IPv6 Address," you don't have IPv6 in your environment.</span></span>

<span data-ttu-id="137da-145">К сети могут применяться следующие условия:</span><span class="sxs-lookup"><span data-stu-id="137da-145">These considerations might apply to your network:</span></span>
  
- <span data-ttu-id="137da-p109">Бесплатная служба подписки не поддерживает оплату покупок кредитной картой через IPv6. Это условие не относится к облаку сообщества госучреждений, так как госучреждения имеют лицензию по Соглашению Enterprise.</span><span class="sxs-lookup"><span data-stu-id="137da-p109">The public subscription service does not support purchase by credit card over IPv6. This does not apply to the Government Community Cloud (GCC) because governments have Enterprise Agreement (EA) licensing.</span></span>

- <span data-ttu-id="137da-148">IPv6 не поддерживает некоторые сценарии службы управления правами.</span><span class="sxs-lookup"><span data-stu-id="137da-148">IPv6 does not support some Rights Management Services (RMS) scenarios.</span></span>

- <span data-ttu-id="137da-149">IPv6 не поддерживает BlackBerry® Enterprise Server (BES), так как BlackBerry не поддерживает IPv6.</span><span class="sxs-lookup"><span data-stu-id="137da-149">IPv6 does not support BlackBerry® Enterprise Server (BES) because BlackBerry doesn't support IPv6.</span></span>

- <span data-ttu-id="137da-p110">При использовании служб федерации Active Directory (AD FS) с помощью Office 365 рекламу сетевую конечную точку службы федерации Active Directory в Office 365 с помощью IPv6 не поддерживается. Не следует включать записи AAAA в соответствующие записи AD FS при использовании Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="137da-p110">If you use Active Directory Federation Services (AD FS) with Office 365, advertising your AD FS network endpoint to Office 365 using IPv6 is not supported. You should not include AAAA records in the AD FS DNS entry when using Exchange Online.</span></span> 

<span data-ttu-id="137da-152">Вы можете быстро вернуться сюда с помощью этой короткой ссылки: [https://aka.ms/o365ip6](https://aka.ms/o365ip6)</span><span class="sxs-lookup"><span data-stu-id="137da-152">Here's a short link you can use to come back: [https://aka.ms/o365ip6](https://aka.ms/o365ip6)</span></span>
  
## <a name="see-also"></a><span data-ttu-id="137da-153">См. также</span><span class="sxs-lookup"><span data-stu-id="137da-153">See also</span></span>

[<span data-ttu-id="137da-154">Документ положение технологии корпорации Майкрософт</span><span class="sxs-lookup"><span data-stu-id="137da-154">Microsoft Technology Position Paper</span></span>](https://go.microsoft.com/fwlink/p/?linkid=525743)
  
[<span data-ttu-id="137da-155">Протокол TCP/IP v4 и v6</span><span class="sxs-lookup"><span data-stu-id="137da-155">TCP/IP v4 and v6</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=211898)
  
[<span data-ttu-id="137da-156">Руководство по освоению IPv6</span><span class="sxs-lookup"><span data-stu-id="137da-156">IPv6 Survival Guide</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=237480)
