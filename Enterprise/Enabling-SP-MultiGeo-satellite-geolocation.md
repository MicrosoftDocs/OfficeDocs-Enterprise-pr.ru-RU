---
title: 'Включение SharePoint c поддержкой нескольких регионов в периферийном расположении '
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Включение SharePoint c поддержкой нескольких регионов в периферийном расположении.
ms.openlocfilehash: 98666f76a5b3ec055a6f26d30f502c3cc6b6d3bb
ms.sourcegitcommit: 0ddd9b0c9c23dc6479dce9f5701b69d533d76127
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/01/2019
ms.locfileid: "31025202"
---
# <a name="enabling-sharepoint-multi-geo-in-your-satellite-geo-location"></a><span data-ttu-id="71baf-103">Включение SharePoint c поддержкой нескольких регионов в периферийном расположении </span><span class="sxs-lookup"><span data-stu-id="71baf-103">Enabling SharePoint Multi-Geo in your satellite geo location</span></span>

<span data-ttu-id="71baf-104">Эта статья предназначена для глобальных администраторов и администраторов SharePoint, создавших периферийное расположение с поддержкой нескольких регионов **до** того, как возможности поддержки нескольких регионов в SharePoint стали общедоступными 27 марта 2019 г., и не включивших SharePoint с поддержкой нескольких регионов в своих периферийных расположениях.</span><span class="sxs-lookup"><span data-stu-id="71baf-104">This article is for Global or SharePoint administrators who have created a Multi-Geo satellite location **before** SharePoint Multi-Geo capabilities became generally available on March 27, 2019, and who have not enabled SharePoint Multi-Geo in their satellite geo location(s).</span></span> 

>[!Note]
><span data-ttu-id="71baf-105">Если новое географическое расположение добавлено **после 27 марта**, вам не потребуется выполнять эти инструкции, так как в новом географическом расположении уже включены функции поддержки нескольких регионов для OneDrive и SharePoint.</span><span class="sxs-lookup"><span data-stu-id="71baf-105">If you have added a new geo location **after March 27th**, you do not need to perform these instructions, as your new geo location will already be enabled for OneDrive and SharePoint Multi-Geo.</span></span>

<span data-ttu-id="71baf-106">Эти инструкции позволят включить SharePoint в периферийном расположении, чтобы ваши пользователи из периферийных расположений могли использовать возможности OneDrive и SharePoint по поддержке нескольких регионов в Office 365.</span><span class="sxs-lookup"><span data-stu-id="71baf-106">These instructions will allow you to enable SharePoint in your satellite location, so your Multi-Geo satellite users can take advantage of both OneDrive and SharePoint Multi-Geo capabilities in O365.</span></span> 

>[!IMPORTANT]
><span data-ttu-id="71baf-107">Обратите внимание, что это одностороннее включение.</span><span class="sxs-lookup"><span data-stu-id="71baf-107">Please note that this is a one way enablement.</span></span> <span data-ttu-id="71baf-108">После настройки режима SPO вы не сможете вернуть свой клиент в режим с поддержкой нескольких регионов только для OneDrive без эскалации запроса в службе поддержки.</span><span class="sxs-lookup"><span data-stu-id="71baf-108">Once you set SPO mode, you will not be able to revert your tenant to OneDrive only Multi-Geo mode without an escalation with support.</span></span> 

## <a name="to-set-a-geo-location-into-spo-mode"></a><span data-ttu-id="71baf-109">Установка режима SPO для географического расположения</span><span class="sxs-lookup"><span data-stu-id="71baf-109">To set a geo location into SPO Mode</span></span>

<span data-ttu-id="71baf-110">Чтобы установить режим SPO для географического расположения, подключитесь к географическому расположению, для которого нужно задать режим SPO:</span><span class="sxs-lookup"><span data-stu-id="71baf-110">To set a geo location into SPO mode, connect to the geo location you want to set in SPO Mode:</span></span>

1.  <span data-ttu-id="71baf-111">Откройте командную консоль SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="71baf-111">Open the SharePoint Online Management Shell.</span></span> 
2.  <span data-ttu-id="71baf-112">Connect-SPOService -URL "https://$tenantGeo-admin.sharepoint.com" -учетные данные $credential</span><span class="sxs-lookup"><span data-stu-id="71baf-112">Connect-SPOService -URL "https://$tenantGeo-admin.sharepoint.com" -Credential $credential</span></span>
3.  <span data-ttu-id="71baf-113">Set-SPOMultiGeoExperience</span><span class="sxs-lookup"><span data-stu-id="71baf-113">Set-SPOMultiGeoExperience</span></span></br></br>
<span data-ttu-id="71baf-114">![Set-SPOMultiGeoExperience](media/Set-SPO-MultiGeo.jpg)</span><span class="sxs-lookup"><span data-stu-id="71baf-114">![Set-SPOMultiGeoExperience](media/Set-SPO-MultiGeo.jpg)</span></span>
4.  <span data-ttu-id="71baf-115">Обычно эта операция занимает около часа, пока выполняются различные резервирования публикаций в службе, а также повторное присвоение метки клиенту.</span><span class="sxs-lookup"><span data-stu-id="71baf-115">This operation usually takes about an hour while we perform various publish backs in the service and re-stamp your tenant.</span></span> <span data-ttu-id="71baf-116">Минимум через 1 час выполните команду Get-SPOMultiGeoExperience.</span><span class="sxs-lookup"><span data-stu-id="71baf-116">After at least 1 hour, please perform a Get-SPOMultiGeoExperience.</span></span>  <span data-ttu-id="71baf-117">В результате будет показано, находится ли это географическое расположение в режиме SPO.</span><span class="sxs-lookup"><span data-stu-id="71baf-117">This will show you whether this geo location is in SPO mode.</span></span></br></br>
<span data-ttu-id="71baf-118">![Set-SPOMultiGeoExperience](media/Get-SPO-MultiGeo.jpg)</span><span class="sxs-lookup"><span data-stu-id="71baf-118">![Set-SPOMultiGeoExperience](media/Get-SPO-MultiGeo.jpg)</span></span>

 
 
 
>[!Note]
><span data-ttu-id="71baf-119">Некоторые кэши в службе обновляются каждые 24 часа, поэтому возможно, что в течение 24 часов периферийное расположение может периодически работать, как будто оно по-прежнему находится в режиме ODB.</span><span class="sxs-lookup"><span data-stu-id="71baf-119">Certain caches in the service update every 24 hours, so it is possible that for a period of up to 24 hours, your satellite geo may intermittently behave as if it was still in ODB mode.</span></span> <span data-ttu-id="71baf-120">Это не приводит к техническим проблемам.</span><span class="sxs-lookup"><span data-stu-id="71baf-120">This does not cause any technical issues.</span></span> 
 
<span data-ttu-id="71baf-121">Дополнительные сведения о SharePoint с поддержкой нескольких регионов см. на странице [aka.ms/sharepointmultigeo](https://docs.microsoft.com/ru-RU/office365/enterprise/multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-office-365)</span><span class="sxs-lookup"><span data-stu-id="71baf-121">For additional information regarding SharePoint Multi-Geo, please refer to [aka.ms/sharepointmultigeo](https://docs.microsoft.com/ru-RU/office365/enterprise/multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-office-365)</span></span>


