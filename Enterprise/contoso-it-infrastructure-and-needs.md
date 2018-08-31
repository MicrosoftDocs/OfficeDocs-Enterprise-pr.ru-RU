---
title: ИТ-инфраструктура и потребности корпорации Contoso
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 5d6a58b8-bec3-4629-9737-8733c7b7ec92
description: Сводка. Сведения о базовой локальной ИТ-инфраструктуре Contoso и о том, как можно удовлетворить бизнес-потребности с помощью облачных решений Майкрософт.
ms.openlocfilehash: e500aa1f3105c1e605d0d3c1d5f66651acb82b34
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915734"
---
# <a name="contosos-it-infrastructure-and-needs"></a><span data-ttu-id="db8ed-103">ИТ-инфраструктура и потребности корпорации Contoso</span><span class="sxs-lookup"><span data-stu-id="db8ed-103">Contoso's IT infrastructure and needs</span></span>

 <span data-ttu-id="db8ed-104">**Сводка.** Сведения о базовой локальной ИТ-инфраструктуре Contoso и о том, как можно удовлетворить бизнес-потребности с помощью облачных решений Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="db8ed-104">**Summary:** Understand the basic structure of Contoso's on-premises IT infrastructure and how its business needs can be met by Microsoft's cloud offerings.</span></span>
  
<span data-ttu-id="db8ed-105">Компания Contoso как раз переходит с централизованной локальной ИТ-инфраструктуры на гибридную, включающую приложения и личные рабочие нагрузки в облаке, а также гибридные сценарии.</span><span class="sxs-lookup"><span data-stu-id="db8ed-105">Contoso is in the process of transitioning from an on-premises, centralized IT infrastructure to a cloud-inclusive one that incorporates cloud-based personal productivity workloads, applications, and hybrid scenarios.</span></span>
  
## <a name="contosos-existing-it-infrastructure"></a><span data-ttu-id="db8ed-106">Существующая ИТ-инфраструктура Contoso</span><span class="sxs-lookup"><span data-stu-id="db8ed-106">Contoso's existing IT infrastructure</span></span>

<span data-ttu-id="db8ed-107">Компания Contoso использует по большей части централизованную локальную ИТ-инфраструктуру с центрами обработки данных приложений, находящимися в главном офисе в Париже.</span><span class="sxs-lookup"><span data-stu-id="db8ed-107">Contoso uses a mostly centralized on-premises IT infrastructure, with application datacenters in the Paris headquarters.</span></span>
  
<span data-ttu-id="db8ed-108">**Рис. 1. Существующая ИТ-инфраструктура Contoso**</span><span class="sxs-lookup"><span data-stu-id="db8ed-108">**Figure 1: Contoso's existing IT infrastructure**</span></span>

![Существующая ИТ-инфраструктура Contoso](media/Contoso-Poster/Existing-IT.png)
  
<span data-ttu-id="db8ed-110">На рисунке 1 показан главный офис с центрами обработки данных приложений, сетью периметра и Интернетом.</span><span class="sxs-lookup"><span data-stu-id="db8ed-110">Figure 1 shows a headquarters office with application datacenters, a DMZ, and the Internet.</span></span>
  
<span data-ttu-id="db8ed-111">В сети периметра Contoso различные группы серверов обеспечивают такие возможности:</span><span class="sxs-lookup"><span data-stu-id="db8ed-111">In Contoso's DMZ, different sets of servers provide:</span></span>
  
- <span data-ttu-id="db8ed-112">удаленный доступ к интрасети Contoso и веб-прокси для сотрудников в главном офисе в Париже;</span><span class="sxs-lookup"><span data-stu-id="db8ed-112">Remote access to the Contoso intranet and web proxying for workers in the Paris headquarters.</span></span>
    
- <span data-ttu-id="db8ed-113">размещение общедоступного веб-сайта Contoso, на котором клиенты могут заказать продукты, компоненты и принадлежности;</span><span class="sxs-lookup"><span data-stu-id="db8ed-113">Hosting for the Contoso public web site, from which customers can order products, parts, or supplies.</span></span>
    
- <span data-ttu-id="db8ed-114">размещение партнерской экстрасети Contoso для связи и совместной работы партнеров.</span><span class="sxs-lookup"><span data-stu-id="db8ed-114">Hosting for the Contoso partner extranet for partner communication and collaboration.</span></span>
    
## <a name="contosos-business-needs"></a><span data-ttu-id="db8ed-115">Бизнес-задачи компании Contoso</span><span class="sxs-lookup"><span data-stu-id="db8ed-115">Contoso's business needs</span></span>

<span data-ttu-id="db8ed-116">Бизнес-потребности Contoso приведены ниже в порядке приоритета.</span><span class="sxs-lookup"><span data-stu-id="db8ed-116">Here are Contoso's business needs in priority order:</span></span>
  
1. <span data-ttu-id="db8ed-117">Соблюдение региональных нормативных требований</span><span class="sxs-lookup"><span data-stu-id="db8ed-117">Adhere to regional regulatory requirements</span></span>
    
    <span data-ttu-id="db8ed-118">Чтобы избежать штрафов и поддержать хорошие отношения с местными органами власти, компании Contoso необходимо обеспечить соответствие нормативным требованиям в отношении хранения и шифрования данных.</span><span class="sxs-lookup"><span data-stu-id="db8ed-118">To prevent fines and maintain good relations with local governments, Contoso must ensure compliance with data storage and encryption regulations.</span></span>
    
2. <span data-ttu-id="db8ed-119">Улучшение управления связью с поставщиками и партнерами</span><span class="sxs-lookup"><span data-stu-id="db8ed-119">Improve vendor and partner management</span></span>
    
    <span data-ttu-id="db8ed-p101">Партнерская экстрасеть устаревает, ее обслуживание дорого обходится. Компания Contoso решила заменить ее на облачное решение, в котором используется федеративная проверка подлинности.</span><span class="sxs-lookup"><span data-stu-id="db8ed-p101">The partner extranet is aging and expensive to maintain. Contoso wants to replace it with a cloud-based solution that uses federated authentication.</span></span>
    
3. <span data-ttu-id="db8ed-122">Улучшение производительности мобильных сотрудников, управления устройствами и возможностей доступа</span><span class="sxs-lookup"><span data-stu-id="db8ed-122">Improve mobile workforce productivity, device management, and access</span></span>
    
    <span data-ttu-id="db8ed-123">Количество мобильных сотрудников компании Contoso увеличивается, поэтому ей требуется решение по управлению устройствами, чтобы улучшить защиту интеллектуальной собственности и доступ к ресурсам.</span><span class="sxs-lookup"><span data-stu-id="db8ed-123">Contoso's mobile-only workforce is expanding and needs device management to ensure intellectual property protection and more efficient access to resources.</span></span>
    
4. <span data-ttu-id="db8ed-124">Уменьшение инфраструктуры удаленного доступа</span><span class="sxs-lookup"><span data-stu-id="db8ed-124">Reduce remote access infrastructure</span></span>
    
    <span data-ttu-id="db8ed-125">Перемещение ресурсов, часто используемых удаленными сотрудниками, в облако позволит компании Contoso сэкономить деньги, уменьшив затраты на обслуживание и поддержку решения для удаленного доступа к ним.</span><span class="sxs-lookup"><span data-stu-id="db8ed-125">By moving resources commonly accessed by remote workers to the cloud, Contoso will save money by reducing maintenance and support costs for their remote access solution.</span></span>
    
5. <span data-ttu-id="db8ed-126">Уменьшение масштабов локальных центров обработки данных</span><span class="sxs-lookup"><span data-stu-id="db8ed-126">Scale down on-premises datacenters</span></span>
    
    <span data-ttu-id="db8ed-127">Центры обработки данных Contoso содержат сотни серверов, некоторые из которых выполняют устаревшие функции или функции архивирования, что отвлекает ИТ-специалистов от рабочих нагрузок, представляющих высокую ценность для бизнеса.</span><span class="sxs-lookup"><span data-stu-id="db8ed-127">The Contoso datacenters contain hundreds of servers, some of which are running legacy or archival functions that distract IT staff from maintaining high business value workloads.</span></span>
    
6. <span data-ttu-id="db8ed-128">Увеличение масштаба вычислительных ресурсов и ресурсов хранилища на конец квартала</span><span class="sxs-lookup"><span data-stu-id="db8ed-128">Scale-up computing and storage resources for end-of-quarter processing</span></span>
    
    <span data-ttu-id="db8ed-129">Обработка данных, связанных с финансовым учетом, составлением прогнозов и управлением запасами, на конец квартала требует краткосрочного увеличения количества серверов и объема хранилища.</span><span class="sxs-lookup"><span data-stu-id="db8ed-129">End-of-quarter financial accounting and projection processing along with inventory management requires short-term increases in servers and storage.</span></span>
    
## <a name="mapping-contosos-business-needs-to-microsofts-cloud-offerings"></a><span data-ttu-id="db8ed-130">Сопоставление бизнес-задач Contoso с облачными решениями Майкрософт</span><span class="sxs-lookup"><span data-stu-id="db8ed-130">Mapping Contoso's business needs to Microsoft's cloud offerings</span></span>

<span data-ttu-id="db8ed-131">Проанализировав облачные предложения Майкрософт, ИТ-отдел Contoso составил приведенную ниже схему.</span><span class="sxs-lookup"><span data-stu-id="db8ed-131">Based on an analysis of Microsoft's cloud offerings, Contoso's IT department determined the following mapping:</span></span>
  
|<span data-ttu-id="db8ed-132">**Программное обеспечение как услуга (SaaS)**</span><span class="sxs-lookup"><span data-stu-id="db8ed-132">**Software as a Service (SaaS)**</span></span>|<span data-ttu-id="db8ed-133">**Платформа как услуга (Azure PaaS )**</span><span class="sxs-lookup"><span data-stu-id="db8ed-133">**Platform as a Service (Azure PaaS )**</span></span>|<span data-ttu-id="db8ed-134">**Инфраструктура как услуга (Azure IaaS )**</span><span class="sxs-lookup"><span data-stu-id="db8ed-134">**Infrastructure as a Service (Azure IaaS )**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="db8ed-135">**Office 365.** Основные приложения для повышения производительности отдельных пользователей и групп в облаке.</span><span class="sxs-lookup"><span data-stu-id="db8ed-135">**Office 365:** Primary personal and group productivity applications in the cloud.</span></span> <br/> <span data-ttu-id="db8ed-136">Бизнес-потребности: 1, 3, 5.</span><span class="sxs-lookup"><span data-stu-id="db8ed-136">Business needs: 1 3 5</span></span>  <br/> |<span data-ttu-id="db8ed-137">Размещение документов о продажах и поддержке, а также информационных систем, для которых используются облачные приложения.</span><span class="sxs-lookup"><span data-stu-id="db8ed-137">Host sales and support documents and information systems using cloud-based apps.</span></span>  <br/> <span data-ttu-id="db8ed-138">Бизнес-потребность: 3.</span><span class="sxs-lookup"><span data-stu-id="db8ed-138">Business need: 3</span></span>  <br/> |<span data-ttu-id="db8ed-139">Перемещение устаревших систем и систем архивирования на облачные серверы.</span><span class="sxs-lookup"><span data-stu-id="db8ed-139">Move archival and legacy systems to cloud-based servers.</span></span>  <br/> <span data-ttu-id="db8ed-140">Бизнес-потребность: 5.</span><span class="sxs-lookup"><span data-stu-id="db8ed-140">Business need: 5</span></span>  <br/> |
|<span data-ttu-id="db8ed-p102">**Dynamics 365.** Использование облачного решения для управления связью с пользователями и поставщиками. Удаление партнерской экстрасети в сети периметра.</span><span class="sxs-lookup"><span data-stu-id="db8ed-p102">**Dynamics 365:** Use cloud-based customer and vendor management. Remove partner extranet in the DMZ. </span></span><br/> <span data-ttu-id="db8ed-143">Бизнес-потребность: 2.</span><span class="sxs-lookup"><span data-stu-id="db8ed-143">Business need: 2</span></span>  <br/> |<span data-ttu-id="db8ed-144">Размещение мобильных приложений в облаке, а не в центре обработки данных в Париже.</span><span class="sxs-lookup"><span data-stu-id="db8ed-144">Mobile applications are cloud-based, rather than Paris datacenter-based.</span></span>  <br/> <span data-ttu-id="db8ed-145">Бизнес-потребности: 3, 4.</span><span class="sxs-lookup"><span data-stu-id="db8ed-145">Business needs: 3 4</span></span>  <br/> |<span data-ttu-id="db8ed-146">Перенос редко используемых приложений и данных из локальных центров обработки данных.</span><span class="sxs-lookup"><span data-stu-id="db8ed-146">Migrate low-use apps and data out of on-premises datacenters.</span></span>  <br/> <span data-ttu-id="db8ed-147">Бизнес-потребность: 5.</span><span class="sxs-lookup"><span data-stu-id="db8ed-147">Business need: 5</span></span>  <br/> |
|<span data-ttu-id="db8ed-148">**Intune/EMS.** Управление устройствами с iOS и Android.</span><span class="sxs-lookup"><span data-stu-id="db8ed-148">**Intune/EMS:** Manage iOS and Android devices.</span></span> <br/> <span data-ttu-id="db8ed-149">Бизнес-потребность: 3.</span><span class="sxs-lookup"><span data-stu-id="db8ed-149">Business need: 3</span></span>  <br/> ||<span data-ttu-id="db8ed-150">Временное добавление серверов и хранилища для обработки данных на конец квартала.</span><span class="sxs-lookup"><span data-stu-id="db8ed-150">Add temporary servers and storage for end-of-quarter processing needs.</span></span>  <br/> <span data-ttu-id="db8ed-151">Бизнес-потребность: 6.</span><span class="sxs-lookup"><span data-stu-id="db8ed-151">Business need: 6</span></span>  <br/> |
   
## <a name="see-also"></a><span data-ttu-id="db8ed-152">See Also</span><span class="sxs-lookup"><span data-stu-id="db8ed-152">See Also</span></span>

[<span data-ttu-id="db8ed-153">Contoso в Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="db8ed-153">Contoso in the Microsoft Cloud</span></span>](contoso-in-the-microsoft-cloud.md)
  
[<span data-ttu-id="db8ed-154">Ресурсы для администраторов, посвященные архитектуре Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="db8ed-154">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="db8ed-155">Стратегия Enterprise Cloud корпорации Майкрософт: ресурсы для лиц, принимающих решения в области ИТ</span><span class="sxs-lookup"><span data-stu-id="db8ed-155">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)


