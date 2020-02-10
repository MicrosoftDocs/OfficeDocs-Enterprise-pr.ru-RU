---
title: Настройка обнаружения электронных данных в Office 365 с поддержкой нескольких регионов
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: ''
localization_priority: Priority
ms.collection: Strat_SP_gtc
description: Узнайте, как настроить обнаружение электронных данных в Office 365 с поддержкой нескольких регионов.
ms.openlocfilehash: 01796000353bcc20d9e0ed63be088beeb9b3680e
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844600"
---
# <a name="office-365-multi-geo-ediscovery-configuration"></a><span data-ttu-id="80a4a-103">Настройка обнаружения электронных данных в Office 365 с поддержкой нескольких регионов</span><span class="sxs-lookup"><span data-stu-id="80a4a-103">Office 365 Multi-Geo eDiscovery configuration</span></span>

<span data-ttu-id="80a4a-p101">По умолчанию менеджер по обнаружению электронных данных или администратор в клиенте с поддержкой нескольких регионов сможет обнаруживать электронные данные только в центральном расположении для этого клиента. Чтобы обеспечить поддержку обнаружения электронных данных для периферийных расположений, в PowerShell добавлен новый параметр Region для фильтра соответствия требованиям безопасности.</span><span class="sxs-lookup"><span data-stu-id="80a4a-p101">By default, an eDiscovery Manager or Administrator of a multi-geo tenant will be able to conduct eDiscovery only in the central location of that tenant. To support the ability to conduct eDiscovery for satellite locations, a new Compliance Security Filter parameter called "Region" is available via PowerShell.</span></span>

<span data-ttu-id="80a4a-106">Глобальный администратор Office 365 должен предоставить менеджеру по обнаружению электронных данных право разрешать другим пользователям выполнять обнаружение электронных данных и назначать параметр Region в соответствующем фильтре соответствия требованиям безопасности, чтобы указывать спутниковое расположение в качестве региона для обнаружения электронных данных. В противном случае обнаружение электронных данных не будет выполняться для спутникового расположения.</span><span class="sxs-lookup"><span data-stu-id="80a4a-106">The Office 365 global administrator must assign eDiscovery Manager permissions to allow others to perform eDiscovery and assign a "Region" parameter in their applicable Compliance Security Filter to specify the region for conducting eDiscovery as satellite location, otherwise no eDiscovery will be carried out for the satellite location.</span></span>

<span data-ttu-id="80a4a-p102">Если роль менеджера по обнаружению электронных данных или администратора задана для определенного периферийного расположения, то соответствующий пользователь сможет выполнять операции поиска с обнаружением электронных данных только на сайтах SharePoint и OneDrive, расположенных в этом периферийном расположении. Если менеджер по обнаружению электронных данных попробует выполнить поиск на сайтах SharePoint или OneDrive за пределами указанного периферийного расположения, результаты не будут возвращаться. Кроме того, когда менеджер по обнаружению электронных данных или администратор для периферийного расположения запускает экспорт, данные экспортируются в экземпляр Azure в этом регионе. Это помогает организациям обеспечивать соответствие требованиям, не разрешая экспорт содержимого через контролируемые границы.</span><span class="sxs-lookup"><span data-stu-id="80a4a-p102">When the eDiscovery Manager or Administrator role is set for a particular satellite location, the eDiscovery Manager or Administrator will only be able to perform eDiscovery search actions against the SharePoint sites and OneDrive sites located in that satellite location. If an eDiscovery Manager or Administrator attempts to search SharePoint or OneDrive sites outside the specified satellite location, no results will be returned. Also, when the eDiscovery Manager or Administrator for a satellite location triggers an export, data is exported to the Azure instance of that region. This helps organizations stay in compliance by not allowing content to be exported across controlled borders.</span></span>

> [!NOTE]
> <span data-ttu-id="80a4a-111">Если менеджеру по обнаружению электронных данных требуется искать содержимое в нескольких периферийных расположениях SharePoint, необходимо создать для него еще одну учетную запись, указывающую альтернативное периферийное расположение, где находятся сайты OneDrive или SharePoint.</span><span class="sxs-lookup"><span data-stu-id="80a4a-111">If it's necessary for an eDiscovery Manager to search across multiple SharePoint satellite locations, another user account will need to be created for the eDiscovery Manager which specifies the alternate satellite location where the OneDrive or SharePoint sites are located.</span></span>

[!INCLUDE [Office 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

<span data-ttu-id="80a4a-112">Установка фильтра соответствия требованиям безопасности для региона:</span><span class="sxs-lookup"><span data-stu-id="80a4a-112">To set the Compliance Security Filter for a Region:</span></span>

1. [<span data-ttu-id="80a4a-113">Подключитесь к PowerShell Центра безопасности и соответствия требованиям Office 365.</span><span class="sxs-lookup"><span data-stu-id="80a4a-113">Connect to Office 365 Security & Compliance Center PowerShell</span></span>](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell)

2. <span data-ttu-id="80a4a-114">Используйте следующий синтаксис:</span><span class="sxs-lookup"><span data-stu-id="80a4a-114">Use the following syntax:</span></span>

   ```powershell
   New-ComplianceSecurityFilter -Action All -FilterName <TheNameYouWantToAssign> -Region <RegionValue> -Users <UserPrincipalName>
   ```

   <span data-ttu-id="80a4a-115">Пример:</span><span class="sxs-lookup"><span data-stu-id="80a4a-115">For example:</span></span>

   ```powershell
   New-ComplianceSecurityFilter -Action All -FilterName "NAM eDiscovery Managers" -Region NAM -Users adwood@contoso.onmicrosoft.com
   ```

<span data-ttu-id="80a4a-116">Дополнительные параметры и синтаксис рассматриваются в статье [New-ComplianceSecurityFilter](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance-content-search/new-compliancesecurityfilter).</span><span class="sxs-lookup"><span data-stu-id="80a4a-116">See the [New-ComplianceSecurityFilter](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance-content-search/new-compliancesecurityfilter) article for additional parameters and syntax.</span></span>
