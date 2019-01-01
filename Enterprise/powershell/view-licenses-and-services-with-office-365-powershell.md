---
title: Просмотр лицензий и служб с помощью PowerShell в Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/31/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- O365ITProTrain
- LIL_Placement
- PowerShell
ms.assetid: bb5260a9-a6a3-4f34-b19a-06c6699f6723
description: Объясняет, как использовать Office 365 PowerShell для просмотра сведений о лицензировании планы, служб и лицензий, которые доступны в организации Office 365.
ms.openlocfilehash: dab6b8f1828c6be4d32bb2432437d23328653560
ms.sourcegitcommit: 6dd4ac5808d72406578fcc7be6590dd7a99cebea
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/31/2018
ms.locfileid: "27466878"
---
# <a name="view-licenses-and-services-with-office-365-powershell"></a><span data-ttu-id="8bdc8-103">Просмотр лицензий и служб с помощью PowerShell в Office 365</span><span class="sxs-lookup"><span data-stu-id="8bdc8-103">View licenses and services with Office 365 PowerShell</span></span>

<span data-ttu-id="8bdc8-104">**Сводка:** Объясняет, как использовать Office 365 PowerShell для просмотра сведений о лицензировании планы, служб и лицензий, которые доступны в организации Office 365.</span><span class="sxs-lookup"><span data-stu-id="8bdc8-104">**Summary:** Explains how to use Office 365 PowerShell to view information about the licensing plans, services, and licenses that are available in your Office 365 organization.</span></span>
  
<span data-ttu-id="8bdc8-105">Каждой подписки Office 365 состоит из следующих элементов:</span><span class="sxs-lookup"><span data-stu-id="8bdc8-105">Every Office 365 subscription consists of the following elements:</span></span>

- <span data-ttu-id="8bdc8-p101">**Планы лицензирования** Это также известной как планы лицензии или планов Office 365. Планы лицензирования определяют службы Office 365, которые будут доступны пользователям. Подписки Office 365 может содержать несколько планы лицензирования. Пример плана лицензирования будет Microsoft Office 365 для предприятий E3.</span><span class="sxs-lookup"><span data-stu-id="8bdc8-p101">**Licensing plans** These are also known as license plans or Office 365 plans. Licensing plans define the Office 365 services that are available to users. Your Office 365 subscription may contain multiple licensing plans. An example licensing plan would be Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="8bdc8-p102">**Службы** Это также известной как планов обслуживания. Службы, продуктов Office 365, функций и возможностей, доступных в каждом плане лицензирования, например Exchange Online и Office профессиональный плюс. Пользователи могут иметь несколько лицензий, назначенные им из разных планы лицензирования, предоставление доступа для различных служб.</span><span class="sxs-lookup"><span data-stu-id="8bdc8-p102">**Services** These are also known as service plans. Services are the Office 365 products, features, and capabilities that are available in each licensing plan, for example, Exchange Online and Office Professional Plus. Users can have multiple licenses assigned to them from different licensing plans that grant access to different services.</span></span>
    
- <span data-ttu-id="8bdc8-p103">**Лицензии** Каждый план лицензирования содержит число лицензий, приобретенных. Назначение лицензий пользователям, поэтому они могут использовать службы Office 365, которые определены в плане лицензирования. Каждой учетной записи пользователя требуется по крайней мере один лицензии из одного плана лицензирования, выполните вход в Office 365 и с помощью служб.</span><span class="sxs-lookup"><span data-stu-id="8bdc8-p103">**Licenses** Each licensing plan contains the number of licenses that you purchased. You assign licenses to users so they can use the Office 365 services that are defined by the licensing plan. Every user account requires at least one license from one licensing plan so they can log on to Office 365 and use the services.</span></span>
    
<span data-ttu-id="8bdc8-p104">Office 365 PowerShell можно использовать для просмотра сведений о доступные планы лицензирования, лицензии и службы в организации Office 365. Дополнительные сведения о продуктах, компонентов и служб, доступных в различных подписок на Office 365 можно [Параметры плана Office 365](https://go.microsoft.com/fwlink/p/?LinkId=691147).</span><span class="sxs-lookup"><span data-stu-id="8bdc8-p104">You can use Office 365 PowerShell to view details about the available licensing plans, licenses, and services in your Office 365 organization. For more information about the products, features, and services that are available in different Office 365 subscriptions, see [Office 365 Plan Options](https://go.microsoft.com/fwlink/p/?LinkId=691147).</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="8bdc8-118">Перед началом работы</span><span class="sxs-lookup"><span data-stu-id="8bdc8-118">Before you begin</span></span>

- <span data-ttu-id="8bdc8-p105">Для процедур, описанных в этой статье, требуется подключение к PowerShell в Office 365. Указания см. в статье [Подключение к Office 365 PowerShell](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="8bdc8-p105">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="8bdc8-p106">Сценарий PowerShell, который автоматизирует процедур, описанных в этом разделе. В частности сценарий позволяет просматривать и отключения службы в организации Office 365, включая Sway. Дополнительные сведения можно [отключить доступ к Sway с Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="8bdc8-p106">A PowerShell script is available that automates the procedures described in this topic. Specifically, the script lets you view and disable services in your Office 365 organization, including Sway. For more information, see [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span></span>
    
## <a name="view-information-about-licensing-plans-and-the-available-licenses"></a><span data-ttu-id="8bdc8-124">Просмотр сведений о планах лицензирования и доступных лицензиях</span><span class="sxs-lookup"><span data-stu-id="8bdc8-124">View information about licensing plans and the available licenses</span></span>

<span data-ttu-id="8bdc8-125">Чтобы просмотреть сводную информацию о текущем планы лицензирования и доступных лицензий для каждого плана, выполните следующую команду в Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="8bdc8-125">To view summary information about your current licensing plans and the available licenses for each plan, run the following command in Office 365 PowerShell:</span></span>
  
```
Get-MsolAccountSku
```

<span data-ttu-id="8bdc8-126">Результаты содержат сведения, указанные ниже.</span><span class="sxs-lookup"><span data-stu-id="8bdc8-126">The results contain the following information:</span></span>
  
- <span data-ttu-id="8bdc8-p107">**AccountSkuId:** Показать доступные планы лицензирования для вашей организации, используя синтаксис `<CompanyName>:<LicensingPlan>`.  _<CompanyName>_ — это значение, что и при участвуют в Office 365 и является уникальным для вашей организации. _<LicensingPlan>_ Равны для всех пользователей. Например, в значении `litwareinc:ENTERPRISEPACK`, — это название компании `litwareinc`и имя плана лицензирования `ENTERPRISEPACK`, — имя системы для Office 365 для предприятий E3.</span><span class="sxs-lookup"><span data-stu-id="8bdc8-p107">**AccountSkuId:** Show the available licensing plans for your organization by using the syntax `<CompanyName>:<LicensingPlan>`.  _<CompanyName>_ is the value that you provided when you enrolled in Office 365, and is unique for your organization. The _<LicensingPlan>_ value is the same for everyone. For example, in the value `litwareinc:ENTERPRISEPACK`, the company name is  `litwareinc`, and the licensing plan name  `ENTERPRISEPACK`, which is the system name for Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="8bdc8-131">**ActiveUnits:** Число лицензий, что покупки для конкретного плана лицензирования.</span><span class="sxs-lookup"><span data-stu-id="8bdc8-131">**ActiveUnits:** Number of licenses that you've purchases for a specific licensing plan.</span></span>
    
- <span data-ttu-id="8bdc8-132">**WarningUnits:** Число лицензий в плане лицензирования, который еще не обновленной и, срок действия 30-дневный льготный период.</span><span class="sxs-lookup"><span data-stu-id="8bdc8-132">**WarningUnits:** Number of licenses in a licensing plan that you haven't renewed, and that will expire after the 30-day grace period.</span></span>
    
- <span data-ttu-id="8bdc8-133">**ConsumedUnits:** Число лицензий, которые вы назначили для пользователей с определенным плана лицензирования.</span><span class="sxs-lookup"><span data-stu-id="8bdc8-133">**ConsumedUnits:** Number of licenses that you've assigned to users from a specific licensing plan.</span></span>
    
<span data-ttu-id="8bdc8-134">Чтобы просмотреть подробные сведения о службах Office 365, которые доступны во всех планов лицензии, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="8bdc8-134">To view details about the Office 365 services that are available in all of your license plans, run the following command:</span></span>
  
```
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

<span data-ttu-id="8bdc8-p108">В следующей таблице показаны планов обслуживания Office 365 и их понятные имена для наиболее распространенных служб. Список планов обслуживания может отличаться.</span><span class="sxs-lookup"><span data-stu-id="8bdc8-p108">The following table shows the Office 365 service plans and their friendly names for the most common services. Your list of service plans might be different.</span></span> 
  
|<span data-ttu-id="8bdc8-137">**План обслуживания**</span><span class="sxs-lookup"><span data-stu-id="8bdc8-137">**Service plan**</span></span>|<span data-ttu-id="8bdc8-138">**Описание**</span><span class="sxs-lookup"><span data-stu-id="8bdc8-138">**Description**</span></span>|
|:-----|:-----|
| `SWAY` <br/> |<span data-ttu-id="8bdc8-139">Sway</span><span class="sxs-lookup"><span data-stu-id="8bdc8-139">Sway</span></span>  <br/> |
| `TEAMS1` <br/> |<span data-ttu-id="8bdc8-140">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="8bdc8-140">Microsoft Teams</span></span>  <br/> |
| `YAMMER_ENTERPRISE` <br/> |<span data-ttu-id="8bdc8-141">Yammer</span><span class="sxs-lookup"><span data-stu-id="8bdc8-141">Yammer</span></span>  <br/> |
| `RMS_S_ENTERPRISE` <br/> |<span data-ttu-id="8bdc8-142">Azure Rights Management (RMS)</span><span class="sxs-lookup"><span data-stu-id="8bdc8-142">Azure Rights Management (RMS)</span></span>  <br/> |
| `OFFICESUBSCRIPTION` <br/> |<span data-ttu-id="8bdc8-143">Office профессиональный плюс</span><span class="sxs-lookup"><span data-stu-id="8bdc8-143">Office Professional Plus</span></span>  <br/> |
| `MCOSTANDARD` <br/> |<span data-ttu-id="8bdc8-144">Skype для бизнеса Online</span><span class="sxs-lookup"><span data-stu-id="8bdc8-144">Skype for Business Online</span></span>  <br/> |
| `SHAREPOINTWAC` <br/> |<span data-ttu-id="8bdc8-145">Office Online</span><span class="sxs-lookup"><span data-stu-id="8bdc8-145">Office Online</span></span>  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |<span data-ttu-id="8bdc8-146">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="8bdc8-146">SharePoint Online</span></span>  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |<span data-ttu-id="8bdc8-147">Exchange Online (план 2);</span><span class="sxs-lookup"><span data-stu-id="8bdc8-147">Exchange Online Plan 2</span></span>  <br/> |
   
<span data-ttu-id="8bdc8-148">Полный список планов лицензии (также известной как названия продуктов), планы включены службы и их соответствующих понятные имена в разделе [продукта имена и идентификаторы плана службы для лицензирования](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span><span class="sxs-lookup"><span data-stu-id="8bdc8-148">For a complete list of license plans (also known as product names), their included service plans, and their corresponding friendly names, see [Product names and service plan identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span></span>

<span data-ttu-id="8bdc8-149">Чтобы просмотреть подробные сведения о службах Office 365, доступными в определенных плана лицензирования, используйте следующий синтаксис.</span><span class="sxs-lookup"><span data-stu-id="8bdc8-149">To view details about the Office 365 services that are available in a specific licensing plan, use the following syntax.</span></span>
  
```
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "<AccountSkuId>"}).ServiceStatus
```

<span data-ttu-id="8bdc8-150">В этом примере показано служб Office 365, доступные в плане лицензирования litwareinc: enterprisepack (Office 365 для предприятий E3).</span><span class="sxs-lookup"><span data-stu-id="8bdc8-150">This example shows the Office 365 services that are available in the litwareinc:ENTERPRISEPACK (Office 365 Enterprise E3) licensing plan.</span></span>
  
```
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "litwareinc:ENTERPRISEPACK"}).ServiceStatus
```

## <a name="new-to-office-365"></a><span data-ttu-id="8bdc8-151">Никогда не работали с Office 365?</span><span class="sxs-lookup"><span data-stu-id="8bdc8-151">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   
## <a name="see-also"></a><span data-ttu-id="8bdc8-152">См. также</span><span class="sxs-lookup"><span data-stu-id="8bdc8-152">See also</span></span>

- <span data-ttu-id="8bdc8-153">[Отображение списков пользователей с лицензиями и пользователей без лицензий с помощью Office 365 PowerShell](view-licensed-and-unlicensed-users-with-office-365-powershell.md) .</span><span class="sxs-lookup"><span data-stu-id="8bdc8-153">[View licensed and unlicensed users with Office 365 PowerShell](view-licensed-and-unlicensed-users-with-office-365-powershell.md)</span></span>
- <span data-ttu-id="8bdc8-154">[Просмотр сведений о лицензии и службе учетной записи с помощью PowerShell в Office 365](view-account-license-and-service-details-with-office-365-powershell.md) .</span><span class="sxs-lookup"><span data-stu-id="8bdc8-154">[View account license and service details with Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md)</span></span>
- [<span data-ttu-id="8bdc8-155">Get-MsolAccountSku</span><span class="sxs-lookup"><span data-stu-id="8bdc8-155">Get-MsolAccountSku</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691549)

