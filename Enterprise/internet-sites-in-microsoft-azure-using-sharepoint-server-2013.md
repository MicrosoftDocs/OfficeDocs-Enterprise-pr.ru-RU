---
title: Веб-сайты в Microsoft Azure с использованием SharePoint Server 2013
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 0d93ff4a-8fbd-42b8-9227-d817dba0046d
description: Сводка. Веб-сайты, использующие SharePoint Server 2013, размещаются в службах инфраструктуры Azure. В этой статье приводятся ресурсы по проектированию и реализации этого решения.
ms.openlocfilehash: 26578133709959964e2f8ab1d01b562a526febcb
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487913"
---
# <a name="internet-sites-in-microsoft-azure-using-sharepoint-server-2013"></a><span data-ttu-id="a3430-104">Веб-сайты в Microsoft Azure, использующие SharePoint Server 2013</span><span class="sxs-lookup"><span data-stu-id="a3430-104">Internet Sites in Microsoft Azure using SharePoint Server 2013</span></span>

 <span data-ttu-id="a3430-p102">**Сводка.** Веб-сайты, использующие SharePoint Server 2013, размещаются в службах инфраструктуры Azure. В этой статье приводятся ресурсы по проектированию и реализации этого решения.</span><span class="sxs-lookup"><span data-stu-id="a3430-p102">**Summary:** Internet sites that use SharePoint Server 2013 benefit by being hosted in Azure Infrastructure Services. This article provides resources for designing and implementing this solution.</span></span>
  
## <a name="using-azure-infrastructure-services-for-internet-sites"></a><span data-ttu-id="a3430-107">Использование служб инфраструктуры Azure для веб-сайтов</span><span class="sxs-lookup"><span data-stu-id="a3430-107">Using Azure Infrastructure Services for Internet sites</span></span>

<span data-ttu-id="a3430-p103">Microsoft Azure предусматривает возможность размещения веб-сайтов на основе SharePoint Server 2013. Преимущества:</span><span class="sxs-lookup"><span data-stu-id="a3430-p103">Microsoft Azure provides a compelling option for hosting Internet sites based on SharePoint Server 2013. Advantages include the following:</span></span>
  
- <span data-ttu-id="a3430-110">фокус на разработке хорошего сайта, а не создании инфраструктуры;</span><span class="sxs-lookup"><span data-stu-id="a3430-110">Focus on developing a great site instead of building infrastructure.</span></span>
    
- <span data-ttu-id="a3430-111">гибкость масштабирования решения в соответствии с потребностями;</span><span class="sxs-lookup"><span data-stu-id="a3430-111">Flexibility to scale your solution based on demand by scaling out and in.</span></span>
    
- <span data-ttu-id="a3430-112">оплату только за нужные и используемые ресурсы;</span><span class="sxs-lookup"><span data-stu-id="a3430-112">Pay only for the resources that you need and use.</span></span>
    
- <span data-ttu-id="a3430-113">преимущества Azure Active Directory для учетных записей клиентов;</span><span class="sxs-lookup"><span data-stu-id="a3430-113">Take advantage of Azure Active Directory for customer accounts.</span></span>
    
- <span data-ttu-id="a3430-114">добавление функций, не доступных в Office 365 на данный момент, например подробных отчетов и аналитики.</span><span class="sxs-lookup"><span data-stu-id="a3430-114">Add features that are not currently available in Office 365, such as deep reporting and analytics.</span></span>
    
## <a name="resources"></a><span data-ttu-id="a3430-115">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="a3430-115">Resources</span></span>

<span data-ttu-id="a3430-116">В приведенных ниже технических иллюстрациях и статьях представлены сведения о разработке и реализации веб-сайтов на платформе Azure с помощью SharePoint Server 2013.</span><span class="sxs-lookup"><span data-stu-id="a3430-116">The following technical illustrations and articles provide information about how to design and implement Internet sites in Azure by using SharePoint Server 2013.</span></span>
  
|<span data-ttu-id="a3430-117">**Ресурс**</span><span class="sxs-lookup"><span data-stu-id="a3430-117">**Resource**</span></span>|<span data-ttu-id="a3430-118">**Дополнительные сведения**</span><span class="sxs-lookup"><span data-stu-id="a3430-118">**More information**</span></span>|
|:-----|:-----|
|<span data-ttu-id="a3430-119">Веб-сайты **SharePoint Server 2013 в Azure**</span><span class="sxs-lookup"><span data-stu-id="a3430-119">**SharePoint Server 2013 Internet sites in Azure**</span></span> <br/> <span data-ttu-id="a3430-120">[![Изображение сайтов Интернета в Azure, использующих SharePoint](media/MS-AZ-SPInternetSites.jpg)          ](https://go.microsoft.com/fwlink/p/?LinkId=392552)</span><span class="sxs-lookup"><span data-stu-id="a3430-120">[![Image of Internet sites in Azure using SharePoint](media/MS-AZ-SPInternetSites.jpg)          ](https://go.microsoft.com/fwlink/p/?LinkId=392552)</span></span> <br/> <span data-ttu-id="a3430-121">[](https://go.microsoft.com/fwlink/p/?LinkId=392552)\| PDF [           ](https://go.microsoft.com/fwlink/p/?LinkId=392551) [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392551)  </span><span class="sxs-lookup"><span data-stu-id="a3430-121">[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392552)  \| [          ](https://go.microsoft.com/fwlink/p/?LinkId=392551)[Visio](https://go.microsoft.com/fwlink/p/?LinkId=392551)</span></span> <br/> |<span data-ttu-id="a3430-122">В этой модели показаны основные задачи проектирования и рекомендуемые варианты архитектуры для веб-сайтов в Azure.</span><span class="sxs-lookup"><span data-stu-id="a3430-122">This architecture model outlines key design activities and recommended architecture choices for Internet sites in Azure.</span></span>  <br/> |
|<span data-ttu-id="a3430-123">**Пример проектирования: веб-сайты в Azure для SharePoint Server 2013**</span><span class="sxs-lookup"><span data-stu-id="a3430-123">**Design sample: Internet Sites in Azure for SharePoint Server 2013**</span></span> <br/> <span data-ttu-id="a3430-124">[![Пример проектирования: веб-сайты в Microsoft Azure для SharePoint 2013](media/MS-AZ-InternetSitesDesignSample.jpg)          ](https://go.microsoft.com/fwlink/p/?LinkId=392549)</span><span class="sxs-lookup"><span data-stu-id="a3430-124">[![Image of the Design sample: Internet sites in Microsoft Azure for SharePoint 2013](media/MS-AZ-InternetSitesDesignSample.jpg)          ](https://go.microsoft.com/fwlink/p/?LinkId=392549)</span></span> <br/> <span data-ttu-id="a3430-125">[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392549)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392548)</span><span class="sxs-lookup"><span data-stu-id="a3430-125">[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392549)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392548)</span></span> <br/> |<span data-ttu-id="a3430-126">Используйте этот пример в качестве отправной точки для создания своей архитектуры.</span><span class="sxs-lookup"><span data-stu-id="a3430-126">Use this design sample as a starting point for your own architecture.</span></span>  <br/> |
|<span data-ttu-id="a3430-127">**[Архитектуры Microsoft Azure для SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md)**</span><span class="sxs-lookup"><span data-stu-id="a3430-127">**[Microsoft Azure Architectures for SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md)**</span></span> <br/> |<span data-ttu-id="a3430-128">В этой статье описано проектирование архитектур Azure для размещения решений SharePoint.</span><span class="sxs-lookup"><span data-stu-id="a3430-128">This article describes how to design Azure architectures to host SharePoint solutions.</span></span>  <br/> |

   
<span data-ttu-id="a3430-129">**Присоединяйтесь к обсуждению**</span><span class="sxs-lookup"><span data-stu-id="a3430-129">**Join the discussion**</span></span>

|<span data-ttu-id="a3430-130">**Свяжитесь с нами**</span><span class="sxs-lookup"><span data-stu-id="a3430-130">**Contact us**</span></span>|<span data-ttu-id="a3430-131">**Описание**</span><span class="sxs-lookup"><span data-stu-id="a3430-131">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="a3430-132">**Какое вам решение необходимо?**</span><span class="sxs-lookup"><span data-stu-id="a3430-132">**What cloud adoption content do you need?**</span></span> <br/> |<span data-ttu-id="a3430-p104">Мы создаем контент для решений, которые охватывают несколько продуктов и служб Майкрософт. Сообщите нам, что вы думаете о наших межсерверных решениях, или укажите интересующие вас решения, написав по адресу [MODAcontent@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20).</span><span class="sxs-lookup"><span data-stu-id="a3430-p104">We are creating content for cloud adoption that spans multiple Microsoft cloud platforms and services. Let us know what you think about our cloud adoption content, or ask for specific content by sending email to [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20).  </span></span><br/> |
|<span data-ttu-id="a3430-135">**Присоединяйтесь к обсуждению решений**</span><span class="sxs-lookup"><span data-stu-id="a3430-135">**Join the cloud adoption discussion**</span></span> <br/> |<span data-ttu-id="a3430-p105">If you are passionate about cloud-based solutions, consider joining the Cloud Adoption Advisory Board (CAAB) to connect with a larger, vibrant community of Microsoft content developers, industry professionals, and customers from around the globe. To join, add yourself as a member of the [CAAB (Cloud Adoption Advisory Board) space](https://aka.ms/caab) of the Microsoft Tech Community and send us a quick email at[CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!). Anyone can read community-related content on the [CAAB blog](https://blogs.technet.com/b/solutions_advisory_board/). However, CAAB members get invitations to private webinars that describe new cloud adoption resources and solutions.  </span><span class="sxs-lookup"><span data-stu-id="a3430-p105">If you are passionate about cloud-based solutions, consider joining the Cloud Adoption Advisory Board (CAAB) to connect with a larger, vibrant community of Microsoft content developers, industry professionals, and customers from around the globe. To join, add yourself as a member of the [CAAB (Cloud Adoption Advisory Board) space](https://aka.ms/caab) of the Microsoft Tech Community and send us a quick email at[CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!). Anyone can read community-related content on the [CAAB blog](https://blogs.technet.com/b/solutions_advisory_board/). However, CAAB members get invitations to private webinars that describe new cloud adoption resources and solutions.  </span></span><br/> |
|<span data-ttu-id="a3430-140">**Получите изображения, которые вы здесь видите**</span><span class="sxs-lookup"><span data-stu-id="a3430-140">**Get the art you see here**</span></span> <br/> |<span data-ttu-id="a3430-p106">Если вам нужна редактируемая копия иллюстративного материала из этой статьи, мы с радостью вам ее отправим. Напишите нам, указав URL-адрес и название материала, по адресу [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20).</span><span class="sxs-lookup"><span data-stu-id="a3430-p106">If you want an editable copy of the art you see in this article, we'll be glad to send it to you. Email your request, including the URL and title of the art, to [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20).  </span></span><br/> |
   
## <a name="see-also"></a><span data-ttu-id="a3430-143">См. также</span><span class="sxs-lookup"><span data-stu-id="a3430-143">See Also</span></span>

[<span data-ttu-id="a3430-144">Освоение облака и гибридные решения</span><span class="sxs-lookup"><span data-stu-id="a3430-144">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)



