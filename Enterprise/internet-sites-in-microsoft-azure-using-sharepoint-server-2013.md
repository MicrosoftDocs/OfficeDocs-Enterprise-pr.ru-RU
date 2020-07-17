---
title: Веб-сайты в Microsoft Azure с использованием SharePoint Server 2013
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Ent_Architecture
ms.assetid: 0d93ff4a-8fbd-42b8-9227-d817dba0046d
description: Сводка. Веб-сайты, использующие SharePoint Server 2013, размещаются в службах инфраструктуры Azure. В этой статье приводятся ресурсы по проектированию и реализации этого решения.
ms.openlocfilehash: fa01df6903a9cbc2ec6163514f27a6bd2fd603aa
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998121"
---
# <a name="internet-sites-in-microsoft-azure-using-sharepoint-server-2013"></a><span data-ttu-id="57210-104">Веб-сайты в Microsoft Azure, использующие SharePoint Server 2013</span><span class="sxs-lookup"><span data-stu-id="57210-104">Internet Sites in Microsoft Azure using SharePoint Server 2013</span></span>

 <span data-ttu-id="57210-105">Веб-сайты, использующие SharePoint Server 2013, размещаются в службах инфраструктуры Azure.</span><span class="sxs-lookup"><span data-stu-id="57210-105">Internet sites that use SharePoint Server 2013 benefit by being hosted in Azure Infrastructure Services.</span></span> <span data-ttu-id="57210-106">В этой статье приводятся ресурсы, посвященные разработке и реализации этого решения.</span><span class="sxs-lookup"><span data-stu-id="57210-106">This article provides resources for designing and implementing this solution.</span></span>
  
## <a name="using-azure-infrastructure-services-for-internet-sites"></a><span data-ttu-id="57210-107">Использование служб инфраструктуры Azure для веб-сайтов</span><span class="sxs-lookup"><span data-stu-id="57210-107">Using Azure Infrastructure Services for Internet sites</span></span>

<span data-ttu-id="57210-p103">Microsoft Azure предусматривает возможность размещения веб-сайтов на основе SharePoint Server 2013. Преимущества:</span><span class="sxs-lookup"><span data-stu-id="57210-p103">Microsoft Azure provides a compelling option for hosting Internet sites based on SharePoint Server 2013. Advantages include the following:</span></span>
  
- <span data-ttu-id="57210-110">фокус на разработке хорошего сайта, а не создании инфраструктуры;</span><span class="sxs-lookup"><span data-stu-id="57210-110">Focus on developing a great site instead of building infrastructure.</span></span>
    
- <span data-ttu-id="57210-111">гибкость масштабирования решения в соответствии с потребностями;</span><span class="sxs-lookup"><span data-stu-id="57210-111">Flexibility to scale your solution based on demand by scaling out and in.</span></span>
    
- <span data-ttu-id="57210-112">оплату только за нужные и используемые ресурсы;</span><span class="sxs-lookup"><span data-stu-id="57210-112">Pay only for the resources that you need and use.</span></span>
    
- <span data-ttu-id="57210-113">преимущества Azure Active Directory для учетных записей клиентов;</span><span class="sxs-lookup"><span data-stu-id="57210-113">Take advantage of Azure Active Directory for customer accounts.</span></span>
    
- <span data-ttu-id="57210-114">Добавьте функции, которые в настоящее время недоступны в Microsoft 365, такие как глубокая отчетность и аналитика.</span><span class="sxs-lookup"><span data-stu-id="57210-114">Add features that are not currently available in Microsoft 365, such as deep reporting and analytics.</span></span>
    
## <a name="resources"></a><span data-ttu-id="57210-115">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="57210-115">Resources</span></span>

<span data-ttu-id="57210-116">В приведенных ниже технических иллюстрациях и статьях представлены сведения о разработке и реализации веб-сайтов на платформе Azure с помощью SharePoint Server 2013.</span><span class="sxs-lookup"><span data-stu-id="57210-116">The following technical illustrations and articles provide information about how to design and implement Internet sites in Azure by using SharePoint Server 2013.</span></span>
  
|<span data-ttu-id="57210-117">**Ресурс**</span><span class="sxs-lookup"><span data-stu-id="57210-117">**Resource**</span></span>|<span data-ttu-id="57210-118">**Дополнительные сведения**</span><span class="sxs-lookup"><span data-stu-id="57210-118">**More information**</span></span>|
|:-----|:-----|
|<span data-ttu-id="57210-119">Веб-сайты **SharePoint Server 2013 в Azure**</span><span class="sxs-lookup"><span data-stu-id="57210-119">**SharePoint Server 2013 Internet sites in Azure**</span></span> <br/> <span data-ttu-id="57210-120">[![Изображение сайтов Интернета в Azure, использующих SharePoint](media/MS-AZ-SPInternetSites.jpg)          ](https://go.microsoft.com/fwlink/p/?LinkId=392552)</span><span class="sxs-lookup"><span data-stu-id="57210-120">[![Image of Internet sites in Azure using SharePoint](media/MS-AZ-SPInternetSites.jpg)          ](https://go.microsoft.com/fwlink/p/?LinkId=392552)</span></span> <br/> <span data-ttu-id="57210-121">[PDF-файл](https://go.microsoft.com/fwlink/p/?LinkId=392552) \| [          ](https://go.microsoft.com/fwlink/p/?LinkId=392551) [Приложение Visio](https://go.microsoft.com/fwlink/p/?LinkId=392551)  </span><span class="sxs-lookup"><span data-stu-id="57210-121">[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392552)  \| [          ](https://go.microsoft.com/fwlink/p/?LinkId=392551)[Visio](https://go.microsoft.com/fwlink/p/?LinkId=392551)</span></span> <br/> |<span data-ttu-id="57210-122">В этой модели показаны основные задачи проектирования и рекомендуемые варианты архитектуры для веб-сайтов в Azure.</span><span class="sxs-lookup"><span data-stu-id="57210-122">This architecture model outlines key design activities and recommended architecture choices for Internet sites in Azure.</span></span>  <br/> |
|<span data-ttu-id="57210-123">**Пример проектирования: веб-сайты в Azure для SharePoint Server 2013**</span><span class="sxs-lookup"><span data-stu-id="57210-123">**Design sample: Internet Sites in Azure for SharePoint Server 2013**</span></span> <br/> <span data-ttu-id="57210-124">[![Пример проектирования: веб-сайты в Microsoft Azure для SharePoint 2013](media/MS-AZ-InternetSitesDesignSample.jpg)          ](https://go.microsoft.com/fwlink/p/?LinkId=392549)</span><span class="sxs-lookup"><span data-stu-id="57210-124">[![Image of the Design sample: Internet sites in Microsoft Azure for SharePoint 2013](media/MS-AZ-InternetSitesDesignSample.jpg)          ](https://go.microsoft.com/fwlink/p/?LinkId=392549)</span></span> <br/> <span data-ttu-id="57210-125">[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392549)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392548)</span><span class="sxs-lookup"><span data-stu-id="57210-125">[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392549)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392548)</span></span> <br/> |<span data-ttu-id="57210-126">Используйте этот пример в качестве отправной точки для создания своей архитектуры.</span><span class="sxs-lookup"><span data-stu-id="57210-126">Use this design sample as a starting point for your own architecture.</span></span>  <br/> |
|<span data-ttu-id="57210-127">**[Архитектуры Microsoft Azure для SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md)**</span><span class="sxs-lookup"><span data-stu-id="57210-127">**[Microsoft Azure Architectures for SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md)**</span></span> <br/> |<span data-ttu-id="57210-128">В этой статье описано проектирование архитектур Azure для размещения решений SharePoint.</span><span class="sxs-lookup"><span data-stu-id="57210-128">This article describes how to design Azure architectures to host SharePoint solutions.</span></span>  <br/> |

## <a name="see-also"></a><span data-ttu-id="57210-129">См. также</span><span class="sxs-lookup"><span data-stu-id="57210-129">See Also</span></span>

[<span data-ttu-id="57210-130">Освоение облака и гибридные решения</span><span class="sxs-lookup"><span data-stu-id="57210-130">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.yml)



