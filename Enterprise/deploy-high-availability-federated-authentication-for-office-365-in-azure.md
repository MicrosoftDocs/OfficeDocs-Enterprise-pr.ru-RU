---
title: Развертывание в Azure федеративной проверки подлинности для обеспечения высокой доступности в случае использования Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/06/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_Solutions
ms.assetid: 34b1ab9c-814c-434d-8fd0-e5a82cd9bff6
description: Сводка. Настройка федеративной проверки подлинности с высоким уровнем доступности для подписки на Office 365 в Microsoft Azure.
ms.openlocfilehash: 3767eed81b46448aab6c0439bc4ba6403ad8d01a
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="deploy-high-availability-federated-authentication-for-office-365-in-azure"></a><span data-ttu-id="ab4c9-103">Развертывание в Azure федеративной проверки подлинности для обеспечения высокой доступности в случае использования Office 365</span><span class="sxs-lookup"><span data-stu-id="ab4c9-103">Deploy high availability federated authentication for Office 365 in Azure</span></span>

 <span data-ttu-id="ab4c9-104">**Сводка.** Настройка федеративной проверки подлинности с высоким уровнем доступности для подписки на Office 365 в Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="ab4c9-104">**Summary:** Configure high availability federated authentication for your Office 365 subscription in Microsoft Azure.</span></span>
  
<span data-ttu-id="ab4c9-105">Эта статья содержит ссылки на пошаговые инструкции по развертыванию федеративной проверки подлинности с высоким уровнем доступности для Microsoft Office 365 в службах инфраструктуры Azure со следующими виртуальными машинами:</span><span class="sxs-lookup"><span data-stu-id="ab4c9-105">This article contains links to the step-by-step instructions for deploying high availability federated authentication for Microsoft Office 365 in Azure infrastructure services with these virtual machines:</span></span>
  
- <span data-ttu-id="ab4c9-106">два прокси-сервера веб-приложений;</span><span class="sxs-lookup"><span data-stu-id="ab4c9-106">Two web application proxy servers</span></span>
    
- <span data-ttu-id="ab4c9-107">два сервера служб федерации Active Directory (AD FS);</span><span class="sxs-lookup"><span data-stu-id="ab4c9-107">Two Active Directory Federation Services (AD FS) servers</span></span>
    
- <span data-ttu-id="ab4c9-108">две реплики контроллеров домена;</span><span class="sxs-lookup"><span data-stu-id="ab4c9-108">Two replica domain controllers</span></span>
    
- <span data-ttu-id="ab4c9-109">один сервер DirSync, на котором запущено средство Azure AD Connect.</span><span class="sxs-lookup"><span data-stu-id="ab4c9-109">One directory synchronization (DirSync) server running Azure AD Connect</span></span>
    
<span data-ttu-id="ab4c9-110">Ниже приводится конфигурация с именами-заполнителями для каждого сервера.</span><span class="sxs-lookup"><span data-stu-id="ab4c9-110">Here is the configuration, with placeholder names for each server.</span></span>
  
<span data-ttu-id="ab4c9-111">**Инфраструктура федеративной проверки подлинности с высоким уровнем доступности для Office 365 в Azure**</span><span class="sxs-lookup"><span data-stu-id="ab4c9-111">**A high availability federated authentication for Office 365 infrastructure in Azure**</span></span>

![Окончательная конфигурация инфраструктуры для федеративной проверки подлинности Office 365 с высоким уровнем доступности в Azure](images/c5da470a-f2aa-489a-a050-df09b4d641df.png)
  
<span data-ttu-id="ab4c9-113">Все виртуальные машины находятся в единой виртуальной сети Azure из распределенного развертывания.</span><span class="sxs-lookup"><span data-stu-id="ab4c9-113">All of the virtual machines are in a single cross-premises Azure virtual network (VNet).</span></span> 
  
> [!NOTE]
> <span data-ttu-id="ab4c9-p101">Федеративная проверка подлинности для отдельных пользователей не зависит от локальных ресурсов. Но если распределенное подключение станет недоступным, контроллеры домена в виртуальной сети не получат тех обновлений для учетных записей пользователей и для групп, которые появились в локальной службе AD на сервере Windows Server. Чтобы этого не произошло, настройте высокую доступность для распределенного подключения. Дополнительные сведения см. в статье [Настройка высокодоступных подключений: распределенных и между виртуальными сетями](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-highlyavailable).</span><span class="sxs-lookup"><span data-stu-id="ab4c9-p101">Federated authentication of individual users does not rely on any on-premises resources. However, if the cross-premises connection becomes unavailable, the domain controllers in the VNet will not receive updates to user accounts and groups made in the on-premises Windows Server AD. To ensure this does not happen, you can configure high availability for your cross-premises connection. For more information, see [Highly Available Cross-Premises and VNet-to-VNet Connectivity](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-highlyavailable)</span></span>
  
<span data-ttu-id="ab4c9-118">Каждая пара виртуальных машин для определенной роли находится в отдельной подсети или группе доступности.</span><span class="sxs-lookup"><span data-stu-id="ab4c9-118">Each pair of virtual machines for a specific role is in its own subnet and availability set.</span></span>
  
> [!NOTE]
> <span data-ttu-id="ab4c9-p102">Поскольку эта виртуальная сеть соединена с локальной, в конфигурацию не входят виртуальные машины jumpbox и виртуальные машины наблюдения в подсети управления. Дополнительные сведения см. в статье [Запуск виртуальных машин Windows в n-уровневой архитектуре](https://docs.microsoft.com/azure/guidance/guidance-compute-n-tier-vm).</span><span class="sxs-lookup"><span data-stu-id="ab4c9-p102">Because this VNet is connected to the on-premises network, this configuration does not include jumpbox or monitoring virtual machines on a management subnet. For more information, see [Running Windows VMs for an N-tier architecture](https://docs.microsoft.com/azure/guidance/guidance-compute-n-tier-vm).</span></span> 
  
<span data-ttu-id="ab4c9-p103">Такая конфигурация обеспечивает федеративную проверку подлинности для всех пользователей Office 365, при которой они смогут применять для входа учетные данные Active Directory в Windows Server, а не учетную запись Office 365. Инфраструктура федеративной проверки подлинности включает группу избыточных серверов, которые проще развертывать в службах инфраструктуры Azure, чем в локальной сети периметра.</span><span class="sxs-lookup"><span data-stu-id="ab4c9-p103">The result of this configuration is that you will have federated authentication for all of your Office 365 users, in which they can use their Windows Server Active Directory credentials to sign in rather than their Office 365 account. The federated authentication infrastructure uses a redundant set of servers that are more easily deployed in Azure infrastructure services, rather than in your on-premises edge network.</span></span>
  
## <a name="bill-of-materials"></a><span data-ttu-id="ab4c9-123">Перечень компонентов</span><span class="sxs-lookup"><span data-stu-id="ab4c9-123">Bill of materials</span></span>

<span data-ttu-id="ab4c9-124">Для этой базовой конфигурации требуется следующий набор служб Azure и компонентов:</span><span class="sxs-lookup"><span data-stu-id="ab4c9-124">This baseline configuration requires the following set of Azure services and components:</span></span>
  
- <span data-ttu-id="ab4c9-125">семь виртуальных машин;</span><span class="sxs-lookup"><span data-stu-id="ab4c9-125">Seven virtual machines</span></span>
    
- <span data-ttu-id="ab4c9-126">одна нелокальная виртуальная сеть с четырьмя подсетями;</span><span class="sxs-lookup"><span data-stu-id="ab4c9-126">One cross-premises virtual network with four subnets</span></span>
    
- <span data-ttu-id="ab4c9-127">четыре группы ресурсов;</span><span class="sxs-lookup"><span data-stu-id="ab4c9-127">Four resource groups</span></span>
    
- <span data-ttu-id="ab4c9-128">три группы доступности;</span><span class="sxs-lookup"><span data-stu-id="ab4c9-128">Three availability sets</span></span>
    
- <span data-ttu-id="ab4c9-129">одна подписка Azure.</span><span class="sxs-lookup"><span data-stu-id="ab4c9-129">One Azure subscription</span></span>
    
<span data-ttu-id="ab4c9-130">Ниже приводится список виртуальных машин, необходимых для данной конфигурации, а также их размеры по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="ab4c9-130">Here are the virtual machines and their default sizes for this configuration.</span></span>
  
|<span data-ttu-id="ab4c9-131">**Элемент**</span><span class="sxs-lookup"><span data-stu-id="ab4c9-131">**Item**</span></span>|<span data-ttu-id="ab4c9-132">**Описание виртуальной машины**</span><span class="sxs-lookup"><span data-stu-id="ab4c9-132">**Virtual machine description**</span></span>|<span data-ttu-id="ab4c9-133">**Изображение коллекции Azure**</span><span class="sxs-lookup"><span data-stu-id="ab4c9-133">**Azure gallery image**</span></span>|<span data-ttu-id="ab4c9-134">**Размер по умолчанию**</span><span class="sxs-lookup"><span data-stu-id="ab4c9-134">**Default size**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="ab4c9-135">1.</span><span class="sxs-lookup"><span data-stu-id="ab4c9-135">1.</span></span>  <br/> |<span data-ttu-id="ab4c9-136">Первый контроллер домена</span><span class="sxs-lookup"><span data-stu-id="ab4c9-136">First domain controller</span></span>  <br/> |<span data-ttu-id="ab4c9-137">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="ab4c9-137">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="ab4c9-138">D2</span><span class="sxs-lookup"><span data-stu-id="ab4c9-138">D2</span></span>  <br/> |
|<span data-ttu-id="ab4c9-139">2.</span><span class="sxs-lookup"><span data-stu-id="ab4c9-139">2.</span></span>  <br/> |<span data-ttu-id="ab4c9-140">Второй контроллер домена</span><span class="sxs-lookup"><span data-stu-id="ab4c9-140">Second domain controller</span></span>  <br/> |<span data-ttu-id="ab4c9-141">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="ab4c9-141">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="ab4c9-142">D2</span><span class="sxs-lookup"><span data-stu-id="ab4c9-142">D2</span></span>  <br/> |
|<span data-ttu-id="ab4c9-143">3.</span><span class="sxs-lookup"><span data-stu-id="ab4c9-143">3.</span></span>  <br/> |<span data-ttu-id="ab4c9-144">Сервер Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="ab4c9-144">Azure AD Connect server</span></span>  <br/> |<span data-ttu-id="ab4c9-145">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="ab4c9-145">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="ab4c9-146">D2</span><span class="sxs-lookup"><span data-stu-id="ab4c9-146">D2</span></span>  <br/> |
|<span data-ttu-id="ab4c9-147">4.</span><span class="sxs-lookup"><span data-stu-id="ab4c9-147">4.</span></span>  <br/> |<span data-ttu-id="ab4c9-148">Первый сервер AD FS</span><span class="sxs-lookup"><span data-stu-id="ab4c9-148">First AD FS server</span></span>  <br/> |<span data-ttu-id="ab4c9-149">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="ab4c9-149">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="ab4c9-150">D2</span><span class="sxs-lookup"><span data-stu-id="ab4c9-150">D2</span></span>  <br/> |
|<span data-ttu-id="ab4c9-151">5.</span><span class="sxs-lookup"><span data-stu-id="ab4c9-151">5.</span></span>  <br/> |<span data-ttu-id="ab4c9-152">Второй сервер AD FS</span><span class="sxs-lookup"><span data-stu-id="ab4c9-152">Second AD FS server</span></span>  <br/> |<span data-ttu-id="ab4c9-153">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="ab4c9-153">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="ab4c9-154">D2</span><span class="sxs-lookup"><span data-stu-id="ab4c9-154">D2</span></span>  <br/> |
|<span data-ttu-id="ab4c9-155">6.</span><span class="sxs-lookup"><span data-stu-id="ab4c9-155">6.</span></span>  <br/> |<span data-ttu-id="ab4c9-156">Первый прокси-сервер веб-приложений</span><span class="sxs-lookup"><span data-stu-id="ab4c9-156">First web application proxy server</span></span>  <br/> |<span data-ttu-id="ab4c9-157">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="ab4c9-157">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="ab4c9-158">D2</span><span class="sxs-lookup"><span data-stu-id="ab4c9-158">D2</span></span>  <br/> |
|<span data-ttu-id="ab4c9-159">7.</span><span class="sxs-lookup"><span data-stu-id="ab4c9-159">7.</span></span>  <br/> |<span data-ttu-id="ab4c9-160">Второй прокси-сервер веб-приложений</span><span class="sxs-lookup"><span data-stu-id="ab4c9-160">Second web application proxy server</span></span>  <br/> |<span data-ttu-id="ab4c9-161">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="ab4c9-161">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="ab4c9-162">D2</span><span class="sxs-lookup"><span data-stu-id="ab4c9-162">D2</span></span>  <br/> |
   
<span data-ttu-id="ab4c9-163">Рассчитать примерные затраты на эту конфигурацию можно с помощью [калькулятора цен Azure](https://azure.microsoft.com/pricing/calculator/).</span><span class="sxs-lookup"><span data-stu-id="ab4c9-163">To compute the estimated costs for this configuration, see the [Azure pricing calculator](https://azure.microsoft.com/pricing/calculator/)</span></span>
  
## <a name="phases-of-deployment"></a><span data-ttu-id="ab4c9-164">Этапы развертывания</span><span class="sxs-lookup"><span data-stu-id="ab4c9-164">Phases of deployment</span></span>

<span data-ttu-id="ab4c9-165">Эта рабочая нагрузка развертывается на следующих этапах:</span><span class="sxs-lookup"><span data-stu-id="ab4c9-165">You deploy this workload in the following phases:</span></span>
  
- <span data-ttu-id="ab4c9-p104">[Федеративная проверка подлинности для обеспечения высокой доступности
Этап 1. Настройка Azure](high-availability-federated-authentication-phase-1-configure-azure.md). Создайте группы ресурсов, учетные записи хранения, группы доступности и нелокальную виртуальную сеть.</span><span class="sxs-lookup"><span data-stu-id="ab4c9-p104">[High availability federated authentication Phase 1: Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md). Create resource groups, storage accounts, availability sets, and a cross-premises virtual network.</span></span>
    
- <span data-ttu-id="ab4c9-p105">[Федеративная проверка подлинности для обеспечения высокой доступности
Этап 2. Настройка контроллеров домена](high-availability-federated-authentication-phase-2-configure-domain-controllers.md). Создайте и настройте реплики контроллеров домена Windows Server Active Directory (AD) и сервера DirSync.</span><span class="sxs-lookup"><span data-stu-id="ab4c9-p105">[High availability federated authentication Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md). Create and configure replica Windows Server Active Directory (AD) domain controllers and the DirSync server.</span></span>
    
- <span data-ttu-id="ab4c9-p106">[Федеративная проверка подлинности для обеспечения высокой доступности
Этап 3. Настройка серверов AD FS](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md). Создайте и настройте два сервера AD FS.</span><span class="sxs-lookup"><span data-stu-id="ab4c9-p106">[High availability federated authentication Phase 3: Configure AD FS servers](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md). Create and configure the two AD FS servers.</span></span>
    
- <span data-ttu-id="ab4c9-p107">[Федеративная проверка подлинности для обеспечения высокой доступности
Этап 4. Настройка прокси веб-приложений](high-availability-federated-authentication-phase-4-configure-web-application-pro.md). Создайте и настройте два прокси-сервера веб-приложений.</span><span class="sxs-lookup"><span data-stu-id="ab4c9-p107">[High availability federated authentication Phase 4: Configure web application proxies](high-availability-federated-authentication-phase-4-configure-web-application-pro.md). Create and configure the two web application proxy servers.</span></span>
    
- <span data-ttu-id="ab4c9-p108">[Федеративная проверка подлинности для обеспечения высокой доступности
Этап 5. Настройка федеративной проверки подлинности для Office 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md). Настройте федеративную проверку подлинности для подписки на Office 365.</span><span class="sxs-lookup"><span data-stu-id="ab4c9-p108">[High availability federated authentication Phase 5: Configure federated authentication for Office 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md). Configure federated authentication for your Office 365 subscription.</span></span>
    
<span data-ttu-id="ab4c9-p109">Эти статьи содержат поэтапное руководство по созданию функциональной федеративной проверки подлинности с высоким уровнем доступности для Office 365 в службах инфраструктуры Azure для предопределенной архитектуры. Учитывайте следующее:</span><span class="sxs-lookup"><span data-stu-id="ab4c9-p109">These articles provide a prescriptive, phase-by-phase guide for a predefined architecture to create a functional, high availability federated authentication for Office 365 in Azure infrastructure services. Keep the following in mind:</span></span>
  
- <span data-ttu-id="ab4c9-178">Если у вас уже есть опыт развертывания AD FS, можете скорректировать инструкции на этапах 3 и 4 и создать группу серверов для своих нужд.</span><span class="sxs-lookup"><span data-stu-id="ab4c9-178">If you are an experienced AD FS implementer, feel free to adapt the instructions in phases 3 and 4 and build the set of servers that best suits your needs.</span></span>
    
- <span data-ttu-id="ab4c9-179">Если у вас уже есть гибридное облачное развертывание Azure с нелокальной виртуальной сетью, можете скорректировать или пропустить инструкции на этапах 1 и 2 и разместить серверы AD FS и прокси-серверы веб-приложений в соответствующих подсетях.</span><span class="sxs-lookup"><span data-stu-id="ab4c9-179">If you already have an existing Azure hybrid cloud deployment with an existing cross-premises virtual network, feel free to adapt or skip the instructions in phases 1 and 2 and place the AD FS and web application proxy servers on the appropriate subnets.</span></span>
    
<span data-ttu-id="ab4c9-180">Для создания среды разработки и тестирования или экспериментальной версии этой конфигурации ознакомьтесь со статьей [Федеративное удостоверение для среды разработки и тестирования Office 365](federated-identity-for-your-office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="ab4c9-180">To build a dev/test environment or a proof-of-concept of this configuration, see [Federated identity for your Office 365 dev/test environment](federated-identity-for-your-office-365-dev-test-environment.md).</span></span>
  
## <a name="next-step"></a><span data-ttu-id="ab4c9-181">Следующее действие</span><span class="sxs-lookup"><span data-stu-id="ab4c9-181">Next step</span></span>

<span data-ttu-id="ab4c9-182">Начните настройку этой рабочей нагрузки с ознакомления со статьей [Этап 1. Федеративная проверка подлинности для обеспечения высокой доступности: настройка Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span><span class="sxs-lookup"><span data-stu-id="ab4c9-182">Start the configuration of this workload with [High availability federated authentication Phase 1: Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span></span> 
  
> [!TIP]
> <span data-ttu-id="ab4c9-183">Чтобы быстрее выполнить развертывание федеративной проверки подлинности с высоким уровнем доступности для Office 365 в Azure, воспользуйтесь [этим комплектом средств](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664).</span><span class="sxs-lookup"><span data-stu-id="ab4c9-183">For a set of files to more quickly deploy your high availability federated authentication for Office 365 in Azure, see the [Federated Authentication for Office 365 in Azure Deployment Kit](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664).</span></span> 
 

