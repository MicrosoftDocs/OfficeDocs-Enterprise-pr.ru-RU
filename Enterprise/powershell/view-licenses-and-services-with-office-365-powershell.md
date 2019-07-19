---
title: Просмотр лицензий и служб с помощью PowerShell в Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/03/2019
audience: Admin
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
description: В этой статье рассказывается, как использовать PowerShell для Office 365 для просмотра сведений о планах лицензирования, службах и лицензиях, доступных в организации Office 365.
ms.openlocfilehash: 18444f76f312c75bc95645d17c48c996f1a3bfc7
ms.sourcegitcommit: 1c97471f47e1869f6db684f280f9085b7c2ff59f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/18/2019
ms.locfileid: "35782039"
---
# <a name="view-licenses-and-services-with-office-365-powershell"></a><span data-ttu-id="8bd08-103">Просмотр лицензий и служб с помощью PowerShell в Office 365</span><span class="sxs-lookup"><span data-stu-id="8bd08-103">View licenses and services with Office 365 PowerShell</span></span>

<span data-ttu-id="8bd08-104">**Сводка:** В этой статье рассказывается, как использовать PowerShell для Office 365 для просмотра сведений о планах лицензирования, службах и лицензиях, доступных в организации Office 365.</span><span class="sxs-lookup"><span data-stu-id="8bd08-104">**Summary:** Explains how to use Office 365 PowerShell to view information about the licensing plans, services, and licenses that are available in your Office 365 organization.</span></span>
  
<span data-ttu-id="8bd08-105">Каждая подписка на Office 365 состоит из следующих элементов:</span><span class="sxs-lookup"><span data-stu-id="8bd08-105">Every Office 365 subscription consists of the following elements:</span></span>

- <span data-ttu-id="8bd08-106">**Планы лицензирования** Они также называются планами лицензирования или планами Office 365.</span><span class="sxs-lookup"><span data-stu-id="8bd08-106">**Licensing plans** These are also known as license plans or Office 365 plans.</span></span> <span data-ttu-id="8bd08-107">Планы лицензирования определяют службы Office 365, доступные пользователям.</span><span class="sxs-lookup"><span data-stu-id="8bd08-107">Licensing plans define the Office 365 services that are available to users.</span></span> <span data-ttu-id="8bd08-108">Ваша подписка на Office 365 может содержать несколько планов лицензирования.</span><span class="sxs-lookup"><span data-stu-id="8bd08-108">Your Office 365 subscription may contain multiple licensing plans.</span></span> <span data-ttu-id="8bd08-109">Примером может служить план лицензирования Office 365 корпоративный E3.</span><span class="sxs-lookup"><span data-stu-id="8bd08-109">An example licensing plan would be Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="8bd08-110">**Службы** Они также называются планами обслуживания.</span><span class="sxs-lookup"><span data-stu-id="8bd08-110">**Services** These are also known as service plans.</span></span> <span data-ttu-id="8bd08-111">Службы — это продукты, функции и возможности Office 365, доступные в каждом плане лицензирования, например, Exchange Online и Office профессиональный плюс.</span><span class="sxs-lookup"><span data-stu-id="8bd08-111">Services are the Office 365 products, features, and capabilities that are available in each licensing plan, for example, Exchange Online and Office Professional Plus.</span></span> <span data-ttu-id="8bd08-112">Пользователям могут быть назначены несколько лицензий из разных планов лицензирования, которые предоставляют доступ к разным службам.</span><span class="sxs-lookup"><span data-stu-id="8bd08-112">Users can have multiple licenses assigned to them from different licensing plans that grant access to different services.</span></span>
    
- <span data-ttu-id="8bd08-113">**Licenses (лицензии** ) Каждый план лицензирования содержит количество приобретенных лицензий.</span><span class="sxs-lookup"><span data-stu-id="8bd08-113">**Licenses** Each licensing plan contains the number of licenses that you purchased.</span></span> <span data-ttu-id="8bd08-114">Вы назначаете пользователям лицензии, чтобы они могли использовать службы Office 365, определенные планом лицензирования.</span><span class="sxs-lookup"><span data-stu-id="8bd08-114">You assign licenses to users so they can use the Office 365 services that are defined by the licensing plan.</span></span> <span data-ttu-id="8bd08-115">Каждая учетная запись пользователя должна иметь по крайней мере одну лицензию из одного плана лицензирования, чтобы пользователи могли входить в Office 365 и использовать службы.</span><span class="sxs-lookup"><span data-stu-id="8bd08-115">Every user account requires at least one license from one licensing plan so they can log on to Office 365 and use the services.</span></span>
    
<span data-ttu-id="8bd08-116">Вы можете использовать Office 365 PowerShell для просмотра сведений о доступных планах лицензирования, лицензиях и службах в организации Office 365.</span><span class="sxs-lookup"><span data-stu-id="8bd08-116">You can use Office 365 PowerShell to view details about the available licensing plans, licenses, and services in your Office 365 organization.</span></span> <span data-ttu-id="8bd08-117">Дополнительные сведения о продуктах, возможностях и службах, доступных в различных подписках на Office 365, можно найти в статье [варианты плана office 365](https://go.microsoft.com/fwlink/p/?LinkId=691147).</span><span class="sxs-lookup"><span data-stu-id="8bd08-117">For more information about the products, features, and services that are available in different Office 365 subscriptions, see [Office 365 Plan Options](https://go.microsoft.com/fwlink/p/?LinkId=691147).</span></span>


## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="8bd08-118">Использование модуля PowerShell Azure Active Directory для Graph</span><span class="sxs-lookup"><span data-stu-id="8bd08-118">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="8bd08-119">Сначала [подключитесь к своему клиенту Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="8bd08-119">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  
<span data-ttu-id="8bd08-120">Чтобы просмотреть сводную информацию о текущих планах лицензирования и доступных лицензиях для каждого плана, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="8bd08-120">To view summary information about your current licensing plans and the available licenses for each plan, run the following command:</span></span>
  
```
Get-AzureADSubscribedSku | Select -Property Sku*,ConsumedUnits -ExpandProperty PrepaidUnits
```

<span data-ttu-id="8bd08-121">Результаты содержат сведения, указанные ниже.</span><span class="sxs-lookup"><span data-stu-id="8bd08-121">The results contain the following information:</span></span>
  
- <span data-ttu-id="8bd08-122">**Скупартнумбер:** Показывает доступные планы лицензирования для вашей организации.</span><span class="sxs-lookup"><span data-stu-id="8bd08-122">**SkuPartNumber:** Shows the available licensing plans for your organization.</span></span> <span data-ttu-id="8bd08-123">Например, `ENTERPRISEPACK` это название плана лицензирования для Office 365 корпоративный E3.</span><span class="sxs-lookup"><span data-stu-id="8bd08-123">For example, `ENTERPRISEPACK` is the license plan name for Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="8bd08-124">**Включено:** Количество лицензий, приобретенных для определенного плана лицензирования.</span><span class="sxs-lookup"><span data-stu-id="8bd08-124">**Enabled:** Number of licenses that you've purchased for a specific licensing plan.</span></span>
    
- <span data-ttu-id="8bd08-125">**ConsumedUnits:** Количество лицензий, назначенных пользователям из определенного плана лицензирования.</span><span class="sxs-lookup"><span data-stu-id="8bd08-125">**ConsumedUnits:** Number of licenses that you've assigned to users from a specific licensing plan.</span></span>
    
<span data-ttu-id="8bd08-126">Чтобы просмотреть сведения о службах Office 365, доступных во всех планах лицензирования, сначала необходимо отобразить список планов лицензирования.</span><span class="sxs-lookup"><span data-stu-id="8bd08-126">To view details about the Office 365 services that are available in all of your license plans, first display a list of your license plans.</span></span>

````
Get-AzureADSubscribedSku | Select SkuPartNumber
````

<span data-ttu-id="8bd08-127">Затем сохраните сведения о планах лицензии в переменной.</span><span class="sxs-lookup"><span data-stu-id="8bd08-127">Next, store the license plans information in a variable.</span></span>

````
$licenses = Get-AzureADSubscribedSku
````

<span data-ttu-id="8bd08-128">Затем отобразите службы в определенном плане лицензирования.</span><span class="sxs-lookup"><span data-stu-id="8bd08-128">Next, display the services in a specific license plan.</span></span>

````
$licenses[<index>].ServicePlans
````

<span data-ttu-id="8bd08-129">\<Индекс> — это целое число, задающее номер строки плана лицензирования из отображения `Get-AzureADSubscribedSku | Select SkuPartNumber` команды минус 1.</span><span class="sxs-lookup"><span data-stu-id="8bd08-129">\<index> is an integer that specifies the row number of the license plan from the display of the `Get-AzureADSubscribedSku | Select SkuPartNumber` command, minus 1.</span></span>

<span data-ttu-id="8bd08-130">Например, если `Get-AzureADSubscribedSku | Select SkuPartNumber` команда имеет следующий вид:</span><span class="sxs-lookup"><span data-stu-id="8bd08-130">For example, if the display of the `Get-AzureADSubscribedSku | Select SkuPartNumber` command is this:</span></span>

````
SkuPartNumber
-------------
WIN10_VDA_E5
EMSPREMIUM
ENTERPRISEPREMIUM
FLOW_FREE
````

<span data-ttu-id="8bd08-131">Затем команда отображает службы для плана лицензирования ЕНТЕРПРИСЕПРЕМИУМ следующим образом:</span><span class="sxs-lookup"><span data-stu-id="8bd08-131">Then the command to display the services for the ENTERPRISEPREMIUM license plan is this:</span></span>

````
$licenses[2].ServicePlans
````

<span data-ttu-id="8bd08-132">ЕНТЕРПРИСЕПРЕМИУМ — третья строка.</span><span class="sxs-lookup"><span data-stu-id="8bd08-132">ENTERPRISEPREMIUM is the third row.</span></span> <span data-ttu-id="8bd08-133">Таким образом, значение индекса — (3-1) или 2.</span><span class="sxs-lookup"><span data-stu-id="8bd08-133">Therefore, the index value is (3 - 1), or 2.</span></span>

<span data-ttu-id="8bd08-134">Полный список планов лицензирования (называемых также названиями продуктов), включенных планов обслуживания и соответствующих понятных имен можно узнать в статье [наименования и идентификаторы планов обслуживания для лицензирования](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span><span class="sxs-lookup"><span data-stu-id="8bd08-134">For a complete list of license plans (also known as product names), their included service plans, and their corresponding friendly names, see [Product names and service plan identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span></span>

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="8bd08-135">Использование модуля Microsoft Azure Active Directory для Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="8bd08-135">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="8bd08-136">Сначала [подключитесь к своему клиенту Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="8bd08-136">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

>[!Note]
><span data-ttu-id="8bd08-137">Кроме того, вы можете воспользоваться сценарием PowerShell, который автоматизирует выполнение процедур, описанных в этой статье.</span><span class="sxs-lookup"><span data-stu-id="8bd08-137">A PowerShell script is available that automates the procedures described in this topic.</span></span> <span data-ttu-id="8bd08-138">В частности, скрипт позволяет просматривать и отключать службы в организации Office 365, в том числе Sway.</span><span class="sxs-lookup"><span data-stu-id="8bd08-138">Specifically, the script lets you view and disable services in your Office 365 organization, including Sway.</span></span> <span data-ttu-id="8bd08-139">Дополнительные сведения см. в статье [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="8bd08-139">For more information, see [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span></span>
>
    
<span data-ttu-id="8bd08-140">Чтобы просмотреть сводную информацию о текущих планах лицензирования и доступных лицензиях для каждого плана, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="8bd08-140">To view summary information about your current licensing plans and the available licenses for each plan, run the following command:</span></span>
  
```
Get-MsolAccountSku
```

<span data-ttu-id="8bd08-141">Результаты содержат сведения, указанные ниже.</span><span class="sxs-lookup"><span data-stu-id="8bd08-141">The results contain the following information:</span></span>
  
- <span data-ttu-id="8bd08-142">**AccountSkuId:** Отображение доступных планов лицензирования для Организации с помощью синтаксиса `<CompanyName>:<LicensingPlan>`.</span><span class="sxs-lookup"><span data-stu-id="8bd08-142">**AccountSkuId:** Show the available licensing plans for your organization by using the syntax `<CompanyName>:<LicensingPlan>`.</span></span>  <span data-ttu-id="8bd08-143">_<CompanyName>_— Это значение, заданное при регистрации в Office 365, и уникальное для вашей организации.</span><span class="sxs-lookup"><span data-stu-id="8bd08-143">_<CompanyName>_ is the value that you provided when you enrolled in Office 365, and is unique for your organization.</span></span> <span data-ttu-id="8bd08-144">Это _<LicensingPlan>_ значение одинаково для всех.</span><span class="sxs-lookup"><span data-stu-id="8bd08-144">The _<LicensingPlan>_ value is the same for everyone.</span></span> <span data-ttu-id="8bd08-145">Например, в значении `litwareinc:ENTERPRISEPACK`название `litwareinc`компании и название `ENTERPRISEPACK`плана лицензирования, которое является системным именем для Office 365 корпоративный E3.</span><span class="sxs-lookup"><span data-stu-id="8bd08-145">For example, in the value `litwareinc:ENTERPRISEPACK`, the company name is  `litwareinc`, and the licensing plan name  `ENTERPRISEPACK`, which is the system name for Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="8bd08-146">**ActiveUnits:** Количество лицензий, приобретенных для определенного плана лицензирования.</span><span class="sxs-lookup"><span data-stu-id="8bd08-146">**ActiveUnits:** Number of licenses that you've purchased for a specific licensing plan.</span></span>
    
- <span data-ttu-id="8bd08-147">**WarningUnits:** Количество лицензий в плане лицензирования, которые вы еще не обновили, и срок действия которых истекает через 30 дней.</span><span class="sxs-lookup"><span data-stu-id="8bd08-147">**WarningUnits:** Number of licenses in a licensing plan that you haven't renewed, and that will expire after the 30-day grace period.</span></span>
    
- <span data-ttu-id="8bd08-148">**ConsumedUnits:** Количество лицензий, назначенных пользователям из определенного плана лицензирования.</span><span class="sxs-lookup"><span data-stu-id="8bd08-148">**ConsumedUnits:** Number of licenses that you've assigned to users from a specific licensing plan.</span></span>
    
<span data-ttu-id="8bd08-149">Чтобы просмотреть сведения о службах Office 365, доступных во всех планах лицензирования, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="8bd08-149">To view details about the Office 365 services that are available in all of your license plans, run the following command:</span></span>
  
```
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

<span data-ttu-id="8bd08-150">В следующей таблице показаны планы обслуживания Office 365 и их понятные имена для наиболее распространенных служб.</span><span class="sxs-lookup"><span data-stu-id="8bd08-150">The following table shows the Office 365 service plans and their friendly names for the most common services.</span></span> <span data-ttu-id="8bd08-151">Ваш список планов обслуживания может отличаться.</span><span class="sxs-lookup"><span data-stu-id="8bd08-151">Your list of service plans might be different.</span></span> 
  
|<span data-ttu-id="8bd08-152">**План обслуживания**</span><span class="sxs-lookup"><span data-stu-id="8bd08-152">**Service plan**</span></span>|<span data-ttu-id="8bd08-153">**Описание**</span><span class="sxs-lookup"><span data-stu-id="8bd08-153">**Description**</span></span>|
|:-----|:-----|
| `SWAY` <br/> |<span data-ttu-id="8bd08-154">Sway</span><span class="sxs-lookup"><span data-stu-id="8bd08-154">Sway</span></span>  <br/> |
| `TEAMS1` <br/> |<span data-ttu-id="8bd08-155">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="8bd08-155">Microsoft Teams</span></span>  <br/> |
| `YAMMER_ENTERPRISE` <br/> |<span data-ttu-id="8bd08-156">Yammer</span><span class="sxs-lookup"><span data-stu-id="8bd08-156">Yammer</span></span>  <br/> |
| `RMS_S_ENTERPRISE` <br/> |<span data-ttu-id="8bd08-157">Azure Rights Management (RMS)</span><span class="sxs-lookup"><span data-stu-id="8bd08-157">Azure Rights Management (RMS)</span></span>  <br/> |
| `OFFICESUBSCRIPTION` <br/> |<span data-ttu-id="8bd08-158">Office профессиональный плюс</span><span class="sxs-lookup"><span data-stu-id="8bd08-158">Office Professional Plus</span></span>  <br/> |
| `MCOSTANDARD` <br/> |<span data-ttu-id="8bd08-159">Skype для бизнеса Online</span><span class="sxs-lookup"><span data-stu-id="8bd08-159">Skype for Business Online</span></span>  <br/> |
| `SHAREPOINTWAC` <br/> |<span data-ttu-id="8bd08-160">Office</span><span class="sxs-lookup"><span data-stu-id="8bd08-160">Office</span></span>  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |<span data-ttu-id="8bd08-161">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="8bd08-161">SharePoint Online</span></span>  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |<span data-ttu-id="8bd08-162">Exchange Online (план 2)</span><span class="sxs-lookup"><span data-stu-id="8bd08-162">Exchange Online Plan 2</span></span>  <br/> |
   
<span data-ttu-id="8bd08-163">Полный список планов лицензирования (называемых также названиями продуктов), включенных планов обслуживания и соответствующих понятных имен можно узнать в статье [наименования и идентификаторы планов обслуживания для лицензирования](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span><span class="sxs-lookup"><span data-stu-id="8bd08-163">For a complete list of license plans (also known as product names), their included service plans, and their corresponding friendly names, see [Product names and service plan identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span></span>

<span data-ttu-id="8bd08-164">Чтобы просмотреть сведения о службах Office 365, доступных в определенном плане лицензирования, используйте следующий синтаксис.</span><span class="sxs-lookup"><span data-stu-id="8bd08-164">To view details about the Office 365 services that are available in a specific licensing plan, use the following syntax.</span></span>
  
```
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "<AccountSkuId>"}).ServiceStatus
```

<span data-ttu-id="8bd08-165">В этом примере показаны службы Office 365, доступные в плане лицензирования litwareinc: ENTERPRISEPACK (Office 365 корпоративный E3).</span><span class="sxs-lookup"><span data-stu-id="8bd08-165">This example shows the Office 365 services that are available in the litwareinc:ENTERPRISEPACK (Office 365 Enterprise E3) licensing plan.</span></span>
  
```
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "litwareinc:ENTERPRISEPACK"}).ServiceStatus
```


## <a name="new-to-office-365"></a><span data-ttu-id="8bd08-166">Никогда не работали с Office 365?</span><span class="sxs-lookup"><span data-stu-id="8bd08-166">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   
## <a name="see-also"></a><span data-ttu-id="8bd08-167">См. также</span><span class="sxs-lookup"><span data-stu-id="8bd08-167">See also</span></span>


[<span data-ttu-id="8bd08-168">Управление учетными записями и лицензиями пользователей с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="8bd08-168">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="8bd08-169">Управление Office 365 с помощью PowerShell Office 365</span><span class="sxs-lookup"><span data-stu-id="8bd08-169">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="8bd08-170">Начало работы с Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="8bd08-170">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
