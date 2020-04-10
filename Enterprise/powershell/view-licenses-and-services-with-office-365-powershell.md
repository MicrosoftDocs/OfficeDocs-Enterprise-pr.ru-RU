---
title: Просмотр лицензий и служб с помощью PowerShell в Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/16/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Ent_Office_Other
- O365ITProTrain
- LIL_Placement
- PowerShell
ms.assetid: bb5260a9-a6a3-4f34-b19a-06c6699f6723
description: В этой статье рассказывается, как использовать PowerShell для Office 365 для просмотра сведений о планах лицензирования, службах и лицензиях, доступных в организации Office 365.
ms.openlocfilehash: 83c42fdaafcee94f86bd86253f13c64725b047c2
ms.sourcegitcommit: 3aa6c61242c5691e3180a474ad059bd84c86dc9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/09/2020
ms.locfileid: "43206602"
---
# <a name="view-licenses-and-services-with-office-365-powershell"></a><span data-ttu-id="90b14-103">Просмотр лицензий и служб с помощью PowerShell в Office 365</span><span class="sxs-lookup"><span data-stu-id="90b14-103">View licenses and services with Office 365 PowerShell</span></span>

<span data-ttu-id="90b14-104">Каждая подписка на Office 365 состоит из следующих элементов:</span><span class="sxs-lookup"><span data-stu-id="90b14-104">Every Office 365 subscription consists of the following elements:</span></span>

- <span data-ttu-id="90b14-105">**Планы лицензирования** Они также называются планами лицензирования или планами Office 365.</span><span class="sxs-lookup"><span data-stu-id="90b14-105">**Licensing plans** These are also known as license plans or Office 365 plans.</span></span> <span data-ttu-id="90b14-106">Планы лицензирования определяют службы Office 365, доступные пользователям.</span><span class="sxs-lookup"><span data-stu-id="90b14-106">Licensing plans define the Office 365 services that are available to users.</span></span> <span data-ttu-id="90b14-107">Ваша подписка на Office 365 может содержать несколько планов лицензирования.</span><span class="sxs-lookup"><span data-stu-id="90b14-107">Your Office 365 subscription may contain multiple licensing plans.</span></span> <span data-ttu-id="90b14-108">Примером может служить план лицензирования Office 365 корпоративный E3.</span><span class="sxs-lookup"><span data-stu-id="90b14-108">An example licensing plan would be Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="90b14-109">**Службы** Они также называются планами обслуживания.</span><span class="sxs-lookup"><span data-stu-id="90b14-109">**Services** These are also known as service plans.</span></span> <span data-ttu-id="90b14-110">Службы — это продукты, функции и возможности Office 365, доступные в каждом плане лицензирования, например Exchange Online и Office 365 профессиональный плюс.</span><span class="sxs-lookup"><span data-stu-id="90b14-110">Services are the Office 365 products, features, and capabilities that are available in each licensing plan, for example, Exchange Online and Office 365 ProPlus.</span></span> <span data-ttu-id="90b14-111">Пользователям могут быть назначены несколько лицензий из разных планов лицензирования, которые предоставляют доступ к разным службам.</span><span class="sxs-lookup"><span data-stu-id="90b14-111">Users can have multiple licenses assigned to them from different licensing plans that grant access to different services.</span></span>
    
- <span data-ttu-id="90b14-112">**Licenses (лицензии** ) Каждый план лицензирования содержит количество приобретенных лицензий.</span><span class="sxs-lookup"><span data-stu-id="90b14-112">**Licenses** Each licensing plan contains the number of licenses that you purchased.</span></span> <span data-ttu-id="90b14-113">Вы назначаете пользователям лицензии, чтобы они могли использовать службы Office 365, определенные планом лицензирования.</span><span class="sxs-lookup"><span data-stu-id="90b14-113">You assign licenses to users so they can use the Office 365 services that are defined by the licensing plan.</span></span> <span data-ttu-id="90b14-114">Каждая учетная запись пользователя должна иметь по крайней мере одну лицензию из одного плана лицензирования, чтобы пользователи могли входить в Office 365 и использовать службы.</span><span class="sxs-lookup"><span data-stu-id="90b14-114">Every user account requires at least one license from one licensing plan so they can log on to Office 365 and use the services.</span></span>
    
<span data-ttu-id="90b14-115">Вы можете использовать Office 365 PowerShell для просмотра сведений о доступных планах лицензирования, лицензиях и службах в организации Office 365.</span><span class="sxs-lookup"><span data-stu-id="90b14-115">You can use Office 365 PowerShell to view details about the available licensing plans, licenses, and services in your Office 365 organization.</span></span> <span data-ttu-id="90b14-116">Дополнительные сведения о продуктах, возможностях и службах, доступных в различных подписках на Office 365, можно найти в статье [варианты плана office 365](https://go.microsoft.com/fwlink/p/?LinkId=691147).</span><span class="sxs-lookup"><span data-stu-id="90b14-116">For more information about the products, features, and services that are available in different Office 365 subscriptions, see [Office 365 Plan Options](https://go.microsoft.com/fwlink/p/?LinkId=691147).</span></span>


## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="90b14-117">Использование модуля PowerShell Azure Active Directory для Graph</span><span class="sxs-lookup"><span data-stu-id="90b14-117">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="90b14-118">Сначала [подключитесь к своему клиенту Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="90b14-118">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  
<span data-ttu-id="90b14-119">Чтобы просмотреть сводную информацию о текущих планах лицензирования и доступных лицензиях для каждого плана, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="90b14-119">To view summary information about your current licensing plans and the available licenses for each plan, run this command:</span></span>
  
```powershell
Get-AzureADSubscribedSku | Select -Property Sku*,ConsumedUnits -ExpandProperty PrepaidUnits
```

<span data-ttu-id="90b14-120">Результаты содержат:</span><span class="sxs-lookup"><span data-stu-id="90b14-120">The results contain:</span></span>
  
- <span data-ttu-id="90b14-121">**Скупартнумбер:** Показывает доступные планы лицензирования для вашей организации.</span><span class="sxs-lookup"><span data-stu-id="90b14-121">**SkuPartNumber:** Shows the available licensing plans for your organization.</span></span> <span data-ttu-id="90b14-122">Например, `ENTERPRISEPACK` это название плана лицензирования для Office 365 корпоративный E3.</span><span class="sxs-lookup"><span data-stu-id="90b14-122">For example, `ENTERPRISEPACK` is the license plan name for Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="90b14-123">**Включено:** Количество лицензий, приобретенных для определенного плана лицензирования.</span><span class="sxs-lookup"><span data-stu-id="90b14-123">**Enabled:** Number of licenses that you've purchased for a specific licensing plan.</span></span>
    
- <span data-ttu-id="90b14-124">**ConsumedUnits:** Количество лицензий, назначенных пользователям из определенного плана лицензирования.</span><span class="sxs-lookup"><span data-stu-id="90b14-124">**ConsumedUnits:** Number of licenses that you've assigned to users from a specific licensing plan.</span></span>
    
<span data-ttu-id="90b14-125">Чтобы просмотреть сведения о службах Office 365, доступных во всех планах лицензирования, сначала необходимо отобразить список планов лицензирования.</span><span class="sxs-lookup"><span data-stu-id="90b14-125">To view details about the Office 365 services that are available in all of your license plans, first display a list of your license plans.</span></span>

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="90b14-126">Затем сохраните сведения о планах лицензии в переменной.</span><span class="sxs-lookup"><span data-stu-id="90b14-126">Next, store the license plans information in a variable.</span></span>

```powershell
$licenses = Get-AzureADSubscribedSku
```

<span data-ttu-id="90b14-127">Затем отобразите службы в определенном плане лицензирования.</span><span class="sxs-lookup"><span data-stu-id="90b14-127">Next, display the services in a specific license plan.</span></span>

```powershell
$licenses[<index>].ServicePlans
```

<span data-ttu-id="90b14-128">\<Индекс> — это целое число, задающее номер строки плана лицензирования из отображения `Get-AzureADSubscribedSku | Select SkuPartNumber` команды минус 1.</span><span class="sxs-lookup"><span data-stu-id="90b14-128">\<index> is an integer that specifies the row number of the license plan from the display of the `Get-AzureADSubscribedSku | Select SkuPartNumber` command, minus 1.</span></span>

<span data-ttu-id="90b14-129">Например, если `Get-AzureADSubscribedSku | Select SkuPartNumber` команда имеет следующий вид:</span><span class="sxs-lookup"><span data-stu-id="90b14-129">For example, if the display of the `Get-AzureADSubscribedSku | Select SkuPartNumber` command is this:</span></span>

```powershell
SkuPartNumber
-------------
WIN10_VDA_E5
EMSPREMIUM
ENTERPRISEPREMIUM
FLOW_FREE
```

<span data-ttu-id="90b14-130">Затем команда отображает службы для плана лицензирования ЕНТЕРПРИСЕПРЕМИУМ следующим образом:</span><span class="sxs-lookup"><span data-stu-id="90b14-130">Then the command to display the services for the ENTERPRISEPREMIUM license plan is this:</span></span>

```powershell
$licenses[2].ServicePlans
```

<span data-ttu-id="90b14-131">ЕНТЕРПРИСЕПРЕМИУМ — третья строка.</span><span class="sxs-lookup"><span data-stu-id="90b14-131">ENTERPRISEPREMIUM is the third row.</span></span> <span data-ttu-id="90b14-132">Таким образом, значение индекса — (3-1) или 2.</span><span class="sxs-lookup"><span data-stu-id="90b14-132">Therefore, the index value is (3 - 1), or 2.</span></span>

<span data-ttu-id="90b14-133">Полный список планов лицензирования (называемых также названиями продуктов), включенных планов обслуживания и соответствующих понятных имен можно узнать в статье [наименования и идентификаторы планов обслуживания для лицензирования](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span><span class="sxs-lookup"><span data-stu-id="90b14-133">For a complete list of license plans (also known as product names), their included service plans, and their corresponding friendly names, see [Product names and service plan identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span></span>

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="90b14-134">Использование модуля Microsoft Azure Active Directory для Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="90b14-134">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="90b14-135">Сначала [подключитесь к своему клиенту Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="90b14-135">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

>[!Note]
><span data-ttu-id="90b14-136">Кроме того, вы можете воспользоваться сценарием PowerShell, который автоматизирует выполнение процедур, описанных в этой статье.</span><span class="sxs-lookup"><span data-stu-id="90b14-136">A PowerShell script is available that automates the procedures described in this topic.</span></span> <span data-ttu-id="90b14-137">В частности, скрипт позволяет просматривать и отключать службы в организации Office 365, в том числе Sway.</span><span class="sxs-lookup"><span data-stu-id="90b14-137">Specifically, the script lets you view and disable services in your Office 365 organization, including Sway.</span></span> <span data-ttu-id="90b14-138">Дополнительные сведения см. в статье [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="90b14-138">For more information, see [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span></span>
>
    
<span data-ttu-id="90b14-139">Чтобы просмотреть сводную информацию о текущих планах лицензирования и доступных лицензиях для каждого плана, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="90b14-139">To view summary information about your current licensing plans and the available licenses for each plan, run the following command:</span></span>
  
```powershell
Get-MsolAccountSku
```

>[!Note]
><span data-ttu-id="90b14-140">В PowerShell Core не поддерживается модуль Microsoft Azure Active Directory для Windows PowerShell и командлеты с компонентом **Msol** в имени.</span><span class="sxs-lookup"><span data-stu-id="90b14-140">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="90b14-141">Чтобы использовать эти командлеты, необходимо запустить их из Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="90b14-141">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="90b14-142">Результаты содержат сведения, указанные ниже.</span><span class="sxs-lookup"><span data-stu-id="90b14-142">The results contain the following information:</span></span>
  
- <span data-ttu-id="90b14-143">**AccountSkuId:** Отображение доступных планов лицензирования для Организации с помощью синтаксиса `<CompanyName>:<LicensingPlan>`.</span><span class="sxs-lookup"><span data-stu-id="90b14-143">**AccountSkuId:** Show the available licensing plans for your organization by using the syntax `<CompanyName>:<LicensingPlan>`.</span></span>  <span data-ttu-id="90b14-144">CompanyName>— это значение, которое вы задаете при регистрации в Office 365 и является уникальным для вашей организации. _ \<_</span><span class="sxs-lookup"><span data-stu-id="90b14-144">_\<CompanyName>_ is the value that you provided when you enrolled in Office 365, and is unique for your organization.</span></span> <span data-ttu-id="90b14-145">Значение _ \<>лиценсингплан_ одинаково для всех.</span><span class="sxs-lookup"><span data-stu-id="90b14-145">The _\<LicensingPlan>_ value is the same for everyone.</span></span> <span data-ttu-id="90b14-146">Например, в значении `litwareinc:ENTERPRISEPACK`название `litwareinc`компании и название `ENTERPRISEPACK`плана лицензирования, которое является системным именем для Office 365 корпоративный E3.</span><span class="sxs-lookup"><span data-stu-id="90b14-146">For example, in the value `litwareinc:ENTERPRISEPACK`, the company name is  `litwareinc`, and the licensing plan name  `ENTERPRISEPACK`, which is the system name for Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="90b14-147">**ActiveUnits:** Количество лицензий, приобретенных для определенного плана лицензирования.</span><span class="sxs-lookup"><span data-stu-id="90b14-147">**ActiveUnits:** Number of licenses that you've purchased for a specific licensing plan.</span></span>
    
- <span data-ttu-id="90b14-148">**WarningUnits:** Количество лицензий в плане лицензирования, которые вы еще не обновили, и срок действия которых истекает через 30 дней.</span><span class="sxs-lookup"><span data-stu-id="90b14-148">**WarningUnits:** Number of licenses in a licensing plan that you haven't renewed, and that will expire after the 30-day grace period.</span></span>
    
- <span data-ttu-id="90b14-149">**ConsumedUnits:** Количество лицензий, назначенных пользователям из определенного плана лицензирования.</span><span class="sxs-lookup"><span data-stu-id="90b14-149">**ConsumedUnits:** Number of licenses that you've assigned to users from a specific licensing plan.</span></span>
    
<span data-ttu-id="90b14-150">Чтобы просмотреть сведения о службах Office 365, доступных во всех планах лицензирования, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="90b14-150">To view details about the Office 365 services that are available in all of your license plans, run the following command:</span></span>
  
```powershell
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

<span data-ttu-id="90b14-151">В следующей таблице показаны планы обслуживания Office 365 и их понятные имена для наиболее распространенных служб.</span><span class="sxs-lookup"><span data-stu-id="90b14-151">The following table shows the Office 365 service plans and their friendly names for the most common services.</span></span> <span data-ttu-id="90b14-152">Ваш список планов обслуживания может отличаться.</span><span class="sxs-lookup"><span data-stu-id="90b14-152">Your list of service plans might be different.</span></span> 
  
|<span data-ttu-id="90b14-153">**План обслуживания**</span><span class="sxs-lookup"><span data-stu-id="90b14-153">**Service plan**</span></span>|<span data-ttu-id="90b14-154">**Описание**</span><span class="sxs-lookup"><span data-stu-id="90b14-154">**Description**</span></span>|
|:-----|:-----|
| `SWAY` <br/> |<span data-ttu-id="90b14-155">Sway</span><span class="sxs-lookup"><span data-stu-id="90b14-155">Sway</span></span>  <br/> |
| `TEAMS1` <br/> |<span data-ttu-id="90b14-156">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="90b14-156">Microsoft Teams</span></span>  <br/> |
| `YAMMER_ENTERPRISE` <br/> |<span data-ttu-id="90b14-157">Yammer</span><span class="sxs-lookup"><span data-stu-id="90b14-157">Yammer</span></span>  <br/> |
| `RMS_S_ENTERPRISE` <br/> |<span data-ttu-id="90b14-158">Azure Rights Management (RMS)</span><span class="sxs-lookup"><span data-stu-id="90b14-158">Azure Rights Management (RMS)</span></span>  <br/> |
| `OFFICESUBSCRIPTION` <br/> |<span data-ttu-id="90b14-159">Office 365 профессиональный плюс</span><span class="sxs-lookup"><span data-stu-id="90b14-159">Office 365 ProPlus</span></span>  <br/> |
| `MCOSTANDARD` <br/> |<span data-ttu-id="90b14-160">Skype для бизнеса Online</span><span class="sxs-lookup"><span data-stu-id="90b14-160">Skype for Business Online</span></span>  <br/> |
| `SHAREPOINTWAC` <br/> |<span data-ttu-id="90b14-161">Office</span><span class="sxs-lookup"><span data-stu-id="90b14-161">Office</span></span>  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |<span data-ttu-id="90b14-162">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="90b14-162">SharePoint Online</span></span>  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |<span data-ttu-id="90b14-163">Exchange Online (план 2)</span><span class="sxs-lookup"><span data-stu-id="90b14-163">Exchange Online Plan 2</span></span>  <br/> |
   
<span data-ttu-id="90b14-164">Полный список планов лицензирования (называемых также названиями продуктов), включенных планов обслуживания и соответствующих понятных имен можно узнать в статье [наименования и идентификаторы планов обслуживания для лицензирования](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span><span class="sxs-lookup"><span data-stu-id="90b14-164">For a complete list of license plans (also known as product names), their included service plans, and their corresponding friendly names, see [Product names and service plan identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span></span>

<span data-ttu-id="90b14-165">Чтобы просмотреть сведения о службах Office 365, доступных в определенном плане лицензирования, используйте следующий синтаксис.</span><span class="sxs-lookup"><span data-stu-id="90b14-165">To view details about the Office 365 services that are available in a specific licensing plan, use the following syntax.</span></span>
  
```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "<AccountSkuId>"}).ServiceStatus
```

<span data-ttu-id="90b14-166">В этом примере показаны службы Office 365, доступные в плане лицензирования litwareinc: ENTERPRISEPACK (Office 365 корпоративный E3).</span><span class="sxs-lookup"><span data-stu-id="90b14-166">This example shows the Office 365 services that are available in the litwareinc:ENTERPRISEPACK (Office 365 Enterprise E3) licensing plan.</span></span>
  
```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "litwareinc:ENTERPRISEPACK"}).ServiceStatus
```

## <a name="see-also"></a><span data-ttu-id="90b14-167">См. также</span><span class="sxs-lookup"><span data-stu-id="90b14-167">See also</span></span>

[<span data-ttu-id="90b14-168">Управление учетными записями пользователей, лицензиями и группами с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="90b14-168">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="90b14-169">Управление Office 365 с помощью PowerShell Office 365</span><span class="sxs-lookup"><span data-stu-id="90b14-169">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="90b14-170">Начало работы с Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="90b14-170">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
