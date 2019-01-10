---
title: Просмотр лицензий и служб с помощью PowerShell в Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/03/2019
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
ms.openlocfilehash: 8efc123e2820560b4bd8547f4c99bccae242956f
ms.sourcegitcommit: 96313c3c812bae47819f603af995839f4da034c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/09/2019
ms.locfileid: "27786155"
---
# <a name="view-licenses-and-services-with-office-365-powershell"></a><span data-ttu-id="e78f2-103">Просмотр лицензий и служб с помощью PowerShell в Office 365</span><span class="sxs-lookup"><span data-stu-id="e78f2-103">View licenses and services with Office 365 PowerShell</span></span>

<span data-ttu-id="e78f2-104">**Сводка:** Объясняет, как использовать Office 365 PowerShell для просмотра сведений о лицензировании планы, служб и лицензий, которые доступны в организации Office 365.</span><span class="sxs-lookup"><span data-stu-id="e78f2-104">**Summary:** Explains how to use Office 365 PowerShell to view information about the licensing plans, services, and licenses that are available in your Office 365 organization.</span></span>
  
<span data-ttu-id="e78f2-105">Каждой подписки Office 365 состоит из следующих элементов:</span><span class="sxs-lookup"><span data-stu-id="e78f2-105">Every Office 365 subscription consists of the following elements:</span></span>

- <span data-ttu-id="e78f2-p101">**Планы лицензирования** Это также известной как планы лицензии или планов Office 365. Планы лицензирования определяют службы Office 365, которые будут доступны пользователям. Подписки Office 365 может содержать несколько планы лицензирования. Пример плана лицензирования будет Microsoft Office 365 для предприятий E3.</span><span class="sxs-lookup"><span data-stu-id="e78f2-p101">**Licensing plans** These are also known as license plans or Office 365 plans. Licensing plans define the Office 365 services that are available to users. Your Office 365 subscription may contain multiple licensing plans. An example licensing plan would be Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="e78f2-p102">**Службы** Это также известной как планов обслуживания. Службы, продуктов Office 365, функций и возможностей, доступных в каждом плане лицензирования, например Exchange Online и Office профессиональный плюс. Пользователи могут иметь несколько лицензий, назначенные им из разных планы лицензирования, предоставление доступа для различных служб.</span><span class="sxs-lookup"><span data-stu-id="e78f2-p102">**Services** These are also known as service plans. Services are the Office 365 products, features, and capabilities that are available in each licensing plan, for example, Exchange Online and Office Professional Plus. Users can have multiple licenses assigned to them from different licensing plans that grant access to different services.</span></span>
    
- <span data-ttu-id="e78f2-p103">**Лицензии** Каждый план лицензирования содержит число лицензий, приобретенных. Назначение лицензий пользователям, поэтому они могут использовать службы Office 365, которые определены в плане лицензирования. Каждой учетной записи пользователя требуется по крайней мере один лицензии из одного плана лицензирования, выполните вход в Office 365 и с помощью служб.</span><span class="sxs-lookup"><span data-stu-id="e78f2-p103">**Licenses** Each licensing plan contains the number of licenses that you purchased. You assign licenses to users so they can use the Office 365 services that are defined by the licensing plan. Every user account requires at least one license from one licensing plan so they can log on to Office 365 and use the services.</span></span>
    
<span data-ttu-id="e78f2-p104">Office 365 PowerShell можно использовать для просмотра сведений о доступные планы лицензирования, лицензии и службы в организации Office 365. Дополнительные сведения о продуктах, компонентов и служб, доступных в различных подписок на Office 365 можно [Параметры плана Office 365](https://go.microsoft.com/fwlink/p/?LinkId=691147).</span><span class="sxs-lookup"><span data-stu-id="e78f2-p104">You can use Office 365 PowerShell to view details about the available licensing plans, licenses, and services in your Office 365 organization. For more information about the products, features, and services that are available in different Office 365 subscriptions, see [Office 365 Plan Options](https://go.microsoft.com/fwlink/p/?LinkId=691147).</span></span>


## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="e78f2-118">Использование модуля PowerShell Azure Active Directory для Graph</span><span class="sxs-lookup"><span data-stu-id="e78f2-118">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="e78f2-119">Сначала [подключитесь к своему клиенту Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="e78f2-119">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  
<span data-ttu-id="e78f2-120">Чтобы просмотреть сводную информацию о текущем планы лицензирования и доступных лицензий для каждого плана, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="e78f2-120">To view summary information about your current licensing plans and the available licenses for each plan, run the following command:</span></span>
  
```
Get-AzureADSubscribedSku | Select -Property Sku*,ConsumedUnits -ExpandProperty PrepaidUnits
```

<span data-ttu-id="e78f2-121">Результаты содержат сведения, указанные ниже.</span><span class="sxs-lookup"><span data-stu-id="e78f2-121">The results contain the following information:</span></span>
  
- <span data-ttu-id="e78f2-p105">**SkuPartNumber:** Отображает доступные планы лицензирования для вашей организации. Например `ENTERPRISEPACK` — это имя системы для Office 365 для предприятий E3.</span><span class="sxs-lookup"><span data-stu-id="e78f2-p105">**SkuPartNumber:** Shows the available licensing plans for your organization. For example, `ENTERPRISEPACK` is the system name for Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="e78f2-124">**Включено:** Число лицензий, которые вы приобрели для конкретного плана лицензирования.</span><span class="sxs-lookup"><span data-stu-id="e78f2-124">**Enabled:** Number of licenses that you've purchased for a specific licensing plan.</span></span>
    
- <span data-ttu-id="e78f2-125">**ConsumedUnits:** Число лицензий, которые вы назначили для пользователей с определенным плана лицензирования.</span><span class="sxs-lookup"><span data-stu-id="e78f2-125">**ConsumedUnits:** Number of licenses that you've assigned to users from a specific licensing plan.</span></span>
    
<span data-ttu-id="e78f2-126">Чтобы просмотреть подробные сведения о службах Office 365, которые доступны во всех планов лицензии, сначала отобразите список планов лицензии.</span><span class="sxs-lookup"><span data-stu-id="e78f2-126">To view details about the Office 365 services that are available in all of your license plans, first display a list of your license plans.</span></span>

````
Get-AzureADSubscribedSku | Select SkuPartNumber
````

<span data-ttu-id="e78f2-127">Затем сохраните информацию о лицензии планы в переменной.</span><span class="sxs-lookup"><span data-stu-id="e78f2-127">Next, store the license plans information in a variable.</span></span>

````
$licenses = Get-AzureADSubscribedSku
````

<span data-ttu-id="e78f2-128">Затем откройте службы в плане лицензий.</span><span class="sxs-lookup"><span data-stu-id="e78f2-128">Next, display the services in a specific license plan.</span></span>

````
$licenses[<index>].ServicePlans
````

<span data-ttu-id="e78f2-129">\<Индекс > — целое число, указывающее количество план лицензирования из отображения `Get-AzureADSubscribedSku | Select SkuPartNumber` команды минус 1.</span><span class="sxs-lookup"><span data-stu-id="e78f2-129">\<index> is an integer that specifies the row number of the license plan from the display of the `Get-AzureADSubscribedSku | Select SkuPartNumber` command, minus 1.</span></span>

<span data-ttu-id="e78f2-130">Например если на отображение `Get-AzureADSubscribedSku | Select SkuPartNumber` команда будет иметь это:</span><span class="sxs-lookup"><span data-stu-id="e78f2-130">For example, if the display of the `Get-AzureADSubscribedSku | Select SkuPartNumber` command is this:</span></span>

````
SkuPartNumber
-------------
WIN10_VDA_E5
EMSPREMIUM
ENTERPRISEPREMIUM
FLOW_FREE
````

<span data-ttu-id="e78f2-131">Выберите команду, чтобы отобразить служб для план лицензирования ENTERPRISEPREMIUM состоит в следующем.</span><span class="sxs-lookup"><span data-stu-id="e78f2-131">Then the command to display the services for the ENTERPRISEPREMIUM license plan is this:</span></span>

````
$licenses[2].ServicePlans
````

<span data-ttu-id="e78f2-p106">ENTERPRISEPREMIUM является третьей строки. Таким образом, — это значение индекса (3 - 1), или 2.</span><span class="sxs-lookup"><span data-stu-id="e78f2-p106">ENTERPRISEPREMIUM is the third row. Therefore, the index value is (3 - 1), or 2.</span></span>

<span data-ttu-id="e78f2-134">Полный список планов лицензии (также известной как названия продуктов), планы включены службы и их соответствующих понятные имена в разделе [продукта имена и идентификаторы плана службы для лицензирования](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span><span class="sxs-lookup"><span data-stu-id="e78f2-134">For a complete list of license plans (also known as product names), their included service plans, and their corresponding friendly names, see [Product names and service plan identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span></span>

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="e78f2-135">Использование модуля Microsoft Azure Active Directory для Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e78f2-135">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="e78f2-136">Сначала [подключитесь к своему клиенту Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="e78f2-136">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

>[!Note]
><span data-ttu-id="e78f2-p107">Сценарий PowerShell, который автоматизирует процедур, описанных в этом разделе. В частности сценарий позволяет просматривать и отключения службы в организации Office 365, включая Sway. Дополнительные сведения можно [отключить доступ к Sway с Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="e78f2-p107">A PowerShell script is available that automates the procedures described in this topic. Specifically, the script lets you view and disable services in your Office 365 organization, including Sway. For more information, see [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span></span>
>
    
<span data-ttu-id="e78f2-140">Чтобы просмотреть сводную информацию о текущем планы лицензирования и доступных лицензий для каждого плана, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="e78f2-140">To view summary information about your current licensing plans and the available licenses for each plan, run the following command:</span></span>
  
```
Get-MsolAccountSku
```

<span data-ttu-id="e78f2-141">Результаты содержат сведения, указанные ниже.</span><span class="sxs-lookup"><span data-stu-id="e78f2-141">The results contain the following information:</span></span>
  
- <span data-ttu-id="e78f2-p108">**AccountSkuId:** Показать доступные планы лицензирования для вашей организации, используя синтаксис `<CompanyName>:<LicensingPlan>`.  _<CompanyName>_ — это значение, что и при участвуют в Office 365 и является уникальным для вашей организации. _<LicensingPlan>_ Равны для всех пользователей. Например, в значении `litwareinc:ENTERPRISEPACK`, — это название компании `litwareinc`и имя плана лицензирования `ENTERPRISEPACK`, — имя системы для Office 365 для предприятий E3.</span><span class="sxs-lookup"><span data-stu-id="e78f2-p108">**AccountSkuId:** Show the available licensing plans for your organization by using the syntax `<CompanyName>:<LicensingPlan>`.  _<CompanyName>_ is the value that you provided when you enrolled in Office 365, and is unique for your organization. The _<LicensingPlan>_ value is the same for everyone. For example, in the value `litwareinc:ENTERPRISEPACK`, the company name is  `litwareinc`, and the licensing plan name  `ENTERPRISEPACK`, which is the system name for Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="e78f2-146">**ActiveUnits:** Число лицензий, которые вы приобрели для конкретного плана лицензирования.</span><span class="sxs-lookup"><span data-stu-id="e78f2-146">**ActiveUnits:** Number of licenses that you've purchased for a specific licensing plan.</span></span>
    
- <span data-ttu-id="e78f2-147">**WarningUnits:** Число лицензий в плане лицензирования, который еще не обновленной и, срок действия 30-дневный льготный период.</span><span class="sxs-lookup"><span data-stu-id="e78f2-147">**WarningUnits:** Number of licenses in a licensing plan that you haven't renewed, and that will expire after the 30-day grace period.</span></span>
    
- <span data-ttu-id="e78f2-148">**ConsumedUnits:** Число лицензий, которые вы назначили для пользователей с определенным плана лицензирования.</span><span class="sxs-lookup"><span data-stu-id="e78f2-148">**ConsumedUnits:** Number of licenses that you've assigned to users from a specific licensing plan.</span></span>
    
<span data-ttu-id="e78f2-149">Чтобы просмотреть подробные сведения о службах Office 365, которые доступны во всех планов лицензии, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="e78f2-149">To view details about the Office 365 services that are available in all of your license plans, run the following command:</span></span>
  
```
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

<span data-ttu-id="e78f2-p109">В следующей таблице показаны планов обслуживания Office 365 и их понятные имена для наиболее распространенных служб. Список планов обслуживания может отличаться.</span><span class="sxs-lookup"><span data-stu-id="e78f2-p109">The following table shows the Office 365 service plans and their friendly names for the most common services. Your list of service plans might be different.</span></span> 
  
|<span data-ttu-id="e78f2-152">**План обслуживания**</span><span class="sxs-lookup"><span data-stu-id="e78f2-152">**Service plan**</span></span>|<span data-ttu-id="e78f2-153">**Описание**</span><span class="sxs-lookup"><span data-stu-id="e78f2-153">**Description**</span></span>|
|:-----|:-----|
| `SWAY` <br/> |<span data-ttu-id="e78f2-154">Sway</span><span class="sxs-lookup"><span data-stu-id="e78f2-154">Sway</span></span>  <br/> |
| `TEAMS1` <br/> |<span data-ttu-id="e78f2-155">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="e78f2-155">Microsoft Teams</span></span>  <br/> |
| `YAMMER_ENTERPRISE` <br/> |<span data-ttu-id="e78f2-156">Yammer</span><span class="sxs-lookup"><span data-stu-id="e78f2-156">Yammer</span></span>  <br/> |
| `RMS_S_ENTERPRISE` <br/> |<span data-ttu-id="e78f2-157">Azure Rights Management (RMS)</span><span class="sxs-lookup"><span data-stu-id="e78f2-157">Azure Rights Management (RMS)</span></span>  <br/> |
| `OFFICESUBSCRIPTION` <br/> |<span data-ttu-id="e78f2-158">Office профессиональный плюс</span><span class="sxs-lookup"><span data-stu-id="e78f2-158">Office Professional Plus</span></span>  <br/> |
| `MCOSTANDARD` <br/> |<span data-ttu-id="e78f2-159">Skype для бизнеса Online</span><span class="sxs-lookup"><span data-stu-id="e78f2-159">Skype for Business Online</span></span>  <br/> |
| `SHAREPOINTWAC` <br/> |<span data-ttu-id="e78f2-160">Office Online</span><span class="sxs-lookup"><span data-stu-id="e78f2-160">Office Online</span></span>  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |<span data-ttu-id="e78f2-161">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="e78f2-161">SharePoint Online</span></span>  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |<span data-ttu-id="e78f2-162">Exchange Online (план 2)</span><span class="sxs-lookup"><span data-stu-id="e78f2-162">Exchange Online Plan 2</span></span>  <br/> |
   
<span data-ttu-id="e78f2-163">Полный список планов лицензии (также известной как названия продуктов), планы включены службы и их соответствующих понятные имена в разделе [продукта имена и идентификаторы плана службы для лицензирования](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span><span class="sxs-lookup"><span data-stu-id="e78f2-163">For a complete list of license plans (also known as product names), their included service plans, and their corresponding friendly names, see [Product names and service plan identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span></span>

<span data-ttu-id="e78f2-164">Чтобы просмотреть подробные сведения о службах Office 365, доступными в определенных плана лицензирования, используйте следующий синтаксис.</span><span class="sxs-lookup"><span data-stu-id="e78f2-164">To view details about the Office 365 services that are available in a specific licensing plan, use the following syntax.</span></span>
  
```
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "<AccountSkuId>"}).ServiceStatus
```

<span data-ttu-id="e78f2-165">В этом примере показано служб Office 365, доступные в плане лицензирования litwareinc: enterprisepack (Office 365 для предприятий E3).</span><span class="sxs-lookup"><span data-stu-id="e78f2-165">This example shows the Office 365 services that are available in the litwareinc:ENTERPRISEPACK (Office 365 Enterprise E3) licensing plan.</span></span>
  
```
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "litwareinc:ENTERPRISEPACK"}).ServiceStatus
```


## <a name="new-to-office-365"></a><span data-ttu-id="e78f2-166">Никогда не работали с Office 365?</span><span class="sxs-lookup"><span data-stu-id="e78f2-166">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   
## <a name="see-also"></a><span data-ttu-id="e78f2-167">См. также</span><span class="sxs-lookup"><span data-stu-id="e78f2-167">See also</span></span>


[<span data-ttu-id="e78f2-168">Управление учетными записями и лицензиями пользователей с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="e78f2-168">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="e78f2-169">Управление Office 365 с помощью PowerShell Office 365</span><span class="sxs-lookup"><span data-stu-id="e78f2-169">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="e78f2-170">Начало работы с Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="e78f2-170">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
