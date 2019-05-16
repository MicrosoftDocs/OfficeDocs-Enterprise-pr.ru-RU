---
title: Гибридные облачные сценарии для Azure PaaS
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/30/2018
audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 5f4f5d0d-4638-48e8-a517-bd804856b617
description: Сводка. Сведения о гибридной архитектуре и сценариях для облачных предложений на основе Microsoft PaaS в Azure.
ms.openlocfilehash: fcc335d0e53463dea4e7ac73c3885b39734db38e
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067535"
---
# <a name="hybrid-cloud-scenarios-for-azure-paas"></a><span data-ttu-id="19803-103">Сценарии гибридного облака для Azure PaaS</span><span class="sxs-lookup"><span data-stu-id="19803-103">Hybrid cloud scenarios for Azure PaaS</span></span>

 <span data-ttu-id="19803-104">**Сводка.** Сведения о гибридной архитектуре и сценариях для облачных предложений на основе Microsoft PaaS в Azure.</span><span class="sxs-lookup"><span data-stu-id="19803-104">**Summary:** Understand the hybrid architecture and scenarios for Microsoft's Platform as a Service (PaaS)-based cloud offerings in Azure.</span></span>
  
<span data-ttu-id="19803-105">Объедините локальные данные или вычислительные ресурсы с новыми либо преобразованными приложениями, работающими в Azure PaaS. Это позволит воспользоваться преимуществами производительности, надежности и масштабирования облачных решений, а также улучшить поддержку пользователей мобильных приложений.</span><span class="sxs-lookup"><span data-stu-id="19803-105">Combine on-premises data or computing resources with new or converted applications running in Azure PaaS, which can take advantage of cloud performance, reliability, and scale and provide better support for mobile users.</span></span> 
  
## <a name="azure-paas-hybrid-scenario-architecture"></a><span data-ttu-id="19803-106">Архитектура гибридного сценария Azure PaaS</span><span class="sxs-lookup"><span data-stu-id="19803-106">Azure PaaS hybrid scenario architecture</span></span>

<span data-ttu-id="19803-107">На рисунке 1 показана архитектура гибридных сценариев на основе Microsoft PaaS в Azure.</span><span class="sxs-lookup"><span data-stu-id="19803-107">Figure 1 shows the architecture of Microsoft PaaS-based hybrid scenarios in Azure.</span></span>
  
<span data-ttu-id="19803-108">**Рис. 1. Гибридные сценарии на основе Microsoft PaaS в Azure**</span><span class="sxs-lookup"><span data-stu-id="19803-108">**Figure 1: Microsoft PaaS-based hybrid scenarios in Azure**</span></span>

![Гибридные сценарии на основе Microsoft PaaS в Azure](media/Hybrid-Poster/Hybrid-Cloud-Stack-PaaS.png)
  
<span data-ttu-id="19803-110">Для каждого слоя архитектуры:</span><span class="sxs-lookup"><span data-stu-id="19803-110">For each layer of the architecture:</span></span>
  
- <span data-ttu-id="19803-111">Приложения и сценарии</span><span class="sxs-lookup"><span data-stu-id="19803-111">Apps and scenarios</span></span>
    
    <span data-ttu-id="19803-112">Гибридное приложение PaaS выполняется в Azure и использует локальные вычислительные ресурсы или ресурсы хранилища.</span><span class="sxs-lookup"><span data-stu-id="19803-112">A hybrid PaaS application runs in Azure and uses on-premises compute or storage resources.</span></span>
    
- <span data-ttu-id="19803-113">Удостоверение</span><span class="sxs-lookup"><span data-stu-id="19803-113">Identity</span></span>
    
    <span data-ttu-id="19803-114">Включает синхронизацию службы каталогов или федерацию со сторонним поставщиком удостоверений.</span><span class="sxs-lookup"><span data-stu-id="19803-114">Consists of either directory synchronization or federation with a third-party identity provider.</span></span>
    
- <span data-ttu-id="19803-115">Сеть</span><span class="sxs-lookup"><span data-stu-id="19803-115">Network</span></span>
    
    <span data-ttu-id="19803-p101">Состоит из имеющегося интернет-канала или подключения ExpressRoute с открытым пирингом к Azure PaaS. Приложению Azure PaaS необходимо предоставить доступ к локальным вычислительным ресурсам или ресурсам хранилища.</span><span class="sxs-lookup"><span data-stu-id="19803-p101">Consists of either your existing Internet pipe or an ExpressRoute connection with public peering to Azure PaaS. You must include a way for the Azure PaaS application to access the on-premises compute or storage resource.</span></span>
    
- <span data-ttu-id="19803-118">Локальная среда</span><span class="sxs-lookup"><span data-stu-id="19803-118">On-premises</span></span>
    
    <span data-ttu-id="19803-119">Состоит из инфраструктуры удостоверений и безопасности, а также имеющихся бизнес-приложений или серверов баз данных, к которым приложение Azure PaaS может получить безопасный доступ.</span><span class="sxs-lookup"><span data-stu-id="19803-119">Consists of identity and security infrastructure and existing line of business (LOB) applications or database servers, which an Azure PaaS application can securely access.</span></span>
    
## <a name="azure-paas-hybrid-application"></a><span data-ttu-id="19803-120">Гибридное приложение Azure PaaS</span><span class="sxs-lookup"><span data-stu-id="19803-120">Azure PaaS hybrid application</span></span>

<span data-ttu-id="19803-121">На рисунке 2 показана конфигурация гибридного приложения, выполняемого в Azure.</span><span class="sxs-lookup"><span data-stu-id="19803-121">Figure 2 shows the configuration of a hybrid application running in Azure.</span></span>
  
<span data-ttu-id="19803-122">**Рис. 2. Гибридное приложение на основе Azure PaaS**</span><span class="sxs-lookup"><span data-stu-id="19803-122">**Figure 2: Azure PaaS-based hybrid application**</span></span>

![Гибридное приложение на основе Azure PaaS](media/Hybrid-Poster/Hybrid-Cloud-Stack-PaaS-Apps.png)
  
<span data-ttu-id="19803-p102">На рисунке 2 показана локальная сеть, в которой на серверах размещаются хранилище или приложения, а также зона DMZ, содержащая прокси-сервер. Локальная сеть подключена к службам Azure PaaS через интернет-канал или с помощью подключения ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="19803-p102">In Figure 2, an on-premises network hosts storage or apps on servers and a DMZ containing a proxy server. It is connected to Azure PaaS services either over the Internet or with an ExpressRoute connection.</span></span>
  
<span data-ttu-id="19803-126">Организации могут предоставить гибридному приложению Azure PaaS доступ к своим вычислительным ресурсам или ресурсам хранилища следующими способами:</span><span class="sxs-lookup"><span data-stu-id="19803-126">An organization can make its compute or storage resources available to the Azure PaaS hybrid application by:</span></span>
  
- <span data-ttu-id="19803-127">разместив ресурсы на серверах в DMZ;</span><span class="sxs-lookup"><span data-stu-id="19803-127">Hosting the resource on servers in the DMZ.</span></span>
    
- <span data-ttu-id="19803-128">разместив обратный прокси-сервер в DMZ, что обеспечивает входящим запросам на основе HTTPS, прошедшим проверку подлинности, доступ к локальному ресурсу.</span><span class="sxs-lookup"><span data-stu-id="19803-128">Hosting a reverse proxy server in the DMZ, which allows authenticated, inbound, HTTPS-based requests to the resource that is located on-premises.</span></span>
    
<span data-ttu-id="19803-129">Приложение Azure может использовать учетные данные:</span><span class="sxs-lookup"><span data-stu-id="19803-129">The Azure app can use credentials from:</span></span>
  
- <span data-ttu-id="19803-130">Azure AD, которую можно синхронизировать с локальным поставщиком удостоверений, например доменными службами Active Directory (AD DS).</span><span class="sxs-lookup"><span data-stu-id="19803-130">Azure AD, which can be synchronized with your on-premises identity provider, such as Active Directory Domain Services (AD DS).</span></span>
    
- <span data-ttu-id="19803-131">от стороннего поставщика удостоверений.</span><span class="sxs-lookup"><span data-stu-id="19803-131">A third-party identity provider.</span></span>
    
### <a name="example-azure-paas-hybrid-application"></a><span data-ttu-id="19803-132">Пример гибридного приложения Azure PaaS</span><span class="sxs-lookup"><span data-stu-id="19803-132">Example Azure PaaS hybrid application</span></span>

<span data-ttu-id="19803-133">На рисунке 3 показан пример гибридного приложения, выполняемого в Azure.</span><span class="sxs-lookup"><span data-stu-id="19803-133">Figure 3 shows an example hybrid application running in Azure.</span></span>
  
<span data-ttu-id="19803-134">**Рис. 3. Пример гибридного приложения на основе Azure PaaS**</span><span class="sxs-lookup"><span data-stu-id="19803-134">**Figure 3: An example Azure PaaS-based hybrid application**</span></span>

![Пример гибридного приложения на основе Azure PaaS](media/Hybrid-Poster/Hybrid-Cloud-Stack-PaaS-Apps-Ex.png)
  
<span data-ttu-id="19803-p103">На рисунке 3 показана локальная сеть, в которой размещается бизнес-приложение. В Azure PaaS находится настраиваемое мобильное приложение. Подключенный к Интернету смартфон получает доступ к настраиваемому мобильному приложению в Azure, которое отправляет запросы данных локальному бизнес-приложению.</span><span class="sxs-lookup"><span data-stu-id="19803-p103">In Figure 3, an on-premises network hosts an LOB app. Azure PaaS hosts a custom mobile app. A smartphone on the Internet accesses the custom mobile app in Azure, which sends data requests to the on-premises LOB app.</span></span>
  
<span data-ttu-id="19803-p104">В этом примере гибридное приложение Azure PaaS представляет собой настраиваемое мобильное приложение, которое предоставляет обновленные контактные данные сотрудников. Сквозной гибридный сценарий включает:</span><span class="sxs-lookup"><span data-stu-id="19803-p104">This example Azure PaaS hybrid application is a custom mobile app that provides up-to-date contact information on employees. The end-to-end hybrid scenario consists of:</span></span>
  
- <span data-ttu-id="19803-141">приложение для смартфона, для запуска которого требуются проверенные локальные учетные данные;</span><span class="sxs-lookup"><span data-stu-id="19803-141">A smartphone app that requires validated, on-premises credentials to run.</span></span>
    
- <span data-ttu-id="19803-142">настраиваемое мобильное приложение, выполняемое в Azure PaaS, которое запрашивает сведения о конкретных сотрудниках на основе запросов, полученных от приложения для смартфона пользователя;</span><span class="sxs-lookup"><span data-stu-id="19803-142">A custom mobile app running in Azure PaaS, which requests information about specific employees based on queries from a user's smartphone app.</span></span>
    
- <span data-ttu-id="19803-143">обратный прокси-сервер в DMZ, который проверяет настраиваемое мобильное приложение и пересылает запрос;</span><span class="sxs-lookup"><span data-stu-id="19803-143">A reverse proxy server in the DMZ that validates the custom mobile app and forwards the request.</span></span>
    
- <span data-ttu-id="19803-144">ферму серверов бизнес-приложений, которая обслуживает запрос контактных данных при наличии соответствующих разрешений в учетной записи пользователя.</span><span class="sxs-lookup"><span data-stu-id="19803-144">An LOB application server farm that services the contact request, subject to the permissions of the user's account.</span></span>
    
<span data-ttu-id="19803-145">Так как локальный поставщик удостоверений синхронизирован с Azure AD, настраиваемое мобильное приложение и бизнес-приложение могут проверить имя учетной записи пользователя, отправившего запрос.</span><span class="sxs-lookup"><span data-stu-id="19803-145">Because the on-premises identity provider has been synchronized with Azure AD, both the custom mobile app and the LOB app can validate the requesting user's account name.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="19803-146">См. также</span><span class="sxs-lookup"><span data-stu-id="19803-146">See Also</span></span>

[<span data-ttu-id="19803-147">Гибридное облако Майкрософт для корпоративных архитекторов</span><span class="sxs-lookup"><span data-stu-id="19803-147">Microsoft Hybrid Cloud for Enterprise Architects</span></span>](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[<span data-ttu-id="19803-148">Ресурсы для администраторов, посвященные архитектуре Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="19803-148">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

