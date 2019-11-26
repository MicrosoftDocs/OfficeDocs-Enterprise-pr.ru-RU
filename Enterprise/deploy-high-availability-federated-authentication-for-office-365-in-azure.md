---
title: Развертывание в Azure федеративной проверки подлинности для обеспечения высокой доступности в случае использования Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/25/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150s
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_Solutions
ms.assetid: 34b1ab9c-814c-434d-8fd0-e5a82cd9bff6
description: Сводка. Настройка федеративной проверки подлинности с высоким уровнем доступности для подписки на Office 365 в Microsoft Azure.
ms.openlocfilehash: 0b622c895bcd6b11ee7e096ac1e39f1b6bd2dae2
ms.sourcegitcommit: fbd2f3fb297c508212baed3ee9d1ce51765cc8bb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/25/2019
ms.locfileid: "39254518"
---
# <a name="deploy-high-availability-federated-authentication-for-office-365-in-azure"></a><span data-ttu-id="1a4ee-103">Развертывание в Azure федеративной проверки подлинности для обеспечения высокой доступности в случае использования Office 365</span><span class="sxs-lookup"><span data-stu-id="1a4ee-103">Deploy high availability federated authentication for Office 365 in Azure</span></span>

<span data-ttu-id="1a4ee-104">Эта статья содержит ссылки на пошаговые инструкции по развертыванию федеративной проверки подлинности с высоким уровнем доступности для Microsoft Office 365 в службах инфраструктуры Azure со следующими виртуальными машинами:</span><span class="sxs-lookup"><span data-stu-id="1a4ee-104">This article has links to the step-by-step instructions for deploying high availability federated authentication for Microsoft Office 365 in Azure infrastructure services with these virtual machines:</span></span>
  
- <span data-ttu-id="1a4ee-105">два прокси-сервера веб-приложений;</span><span class="sxs-lookup"><span data-stu-id="1a4ee-105">Two web application proxy servers</span></span>
    
- <span data-ttu-id="1a4ee-106">два сервера служб федерации Active Directory (AD FS);</span><span class="sxs-lookup"><span data-stu-id="1a4ee-106">Two Active Directory Federation Services (AD FS) servers</span></span>
    
- <span data-ttu-id="1a4ee-107">две реплики контроллеров домена;</span><span class="sxs-lookup"><span data-stu-id="1a4ee-107">Two replica domain controllers</span></span>
    
- <span data-ttu-id="1a4ee-108">один сервер синхронизации каталогов, на котором запущено средство Azure AD Connect.</span><span class="sxs-lookup"><span data-stu-id="1a4ee-108">One directory synchronization (DirSync) server running Azure AD Connect</span></span>
    
<span data-ttu-id="1a4ee-109">Ниже приводится конфигурация с именами-заполнителями для каждого сервера.</span><span class="sxs-lookup"><span data-stu-id="1a4ee-109">Here is the configuration, with placeholder names for each server.</span></span>
  
<span data-ttu-id="1a4ee-110">**Инфраструктура федеративной проверки подлинности с высоким уровнем доступности для Office 365 в Azure**</span><span class="sxs-lookup"><span data-stu-id="1a4ee-110">**A high availability federated authentication for Office 365 infrastructure in Azure**</span></span>

![Окончательная конфигурация инфраструктуры для федеративной проверки подлинности Office 365 с высоким уровнем доступности в Azure](media/c5da470a-f2aa-489a-a050-df09b4d641df.png)
  
<span data-ttu-id="1a4ee-112">Все виртуальные машины находятся в единой виртуальной сети Azure из распределенного развертывания.</span><span class="sxs-lookup"><span data-stu-id="1a4ee-112">All of the virtual machines are in a single cross-premises Azure virtual network (VNet).</span></span> 
  
> [!NOTE]
> <span data-ttu-id="1a4ee-p101">Федеративная проверка подлинности для отдельных пользователей не зависит от локальных ресурсов. Но если распределенное подключение станет недоступным, контроллеры домена в виртуальной сети не получат тех обновлений для учетных записей пользователей и для групп, которые появились в локальных доменных службах Active Directory (AD DS). Чтобы этого не произошло, настройте высокую доступность для распределенного подключения. Дополнительные сведения см. в статье [Настройка высокодоступных подключений: распределенных и между виртуальными сетями](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-highlyavailable).</span><span class="sxs-lookup"><span data-stu-id="1a4ee-p101">Federated authentication of individual users does not rely on any on-premises resources. However, if the cross-premises connection becomes unavailable, the domain controllers in the VNet will not receive updates to user accounts and groups made in the on-premises Active Directory Domain Services (AD DS). To ensure this does not happen, you can configure high availability for your cross-premises connection. For more information, see [Highly Available Cross-Premises and VNet-to-VNet Connectivity](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-highlyavailable)</span></span>
  
<span data-ttu-id="1a4ee-117">Каждая пара виртуальных машин для определенной роли находится в отдельной подсети или группе доступности.</span><span class="sxs-lookup"><span data-stu-id="1a4ee-117">Each pair of virtual machines for a specific role is in its own subnet and availability set.</span></span>
  
> [!NOTE]
> <span data-ttu-id="1a4ee-p102">Поскольку эта виртуальная сеть соединена с локальной, в конфигурацию не входят виртуальные машины jumpbox и виртуальные машины наблюдения в подсети управления. Дополнительные сведения см. в статье [Запуск виртуальных машин Windows в n-уровневой архитектуре](https://docs.microsoft.com/azure/guidance/guidance-compute-n-tier-vm).</span><span class="sxs-lookup"><span data-stu-id="1a4ee-p102">Because this VNet is connected to the on-premises network, this configuration does not include jumpbox or monitoring virtual machines on a management subnet. For more information, see [Running Windows VMs for an N-tier architecture](https://docs.microsoft.com/azure/guidance/guidance-compute-n-tier-vm).</span></span> 
  
<span data-ttu-id="1a4ee-120">Такая конфигурация обеспечивает федеративную проверку подлинности для всех пользователей Office 365, при которой они смогут применять для входа учетные данные доменных служб Active Directory, а не учетную запись Office 365.</span><span class="sxs-lookup"><span data-stu-id="1a4ee-120">The result of this configuration is that you will have federated authentication for all of your Office 365 users, in which they can use their Windows Server Active Directory credentials to sign in rather than their Office 365 account.</span></span> <span data-ttu-id="1a4ee-121">Инфраструктура федеративной проверки подлинности включает группу избыточных серверов, которые проще развертывать в службах инфраструктуры Azure, чем в локальной сети периметра.</span><span class="sxs-lookup"><span data-stu-id="1a4ee-121">The federated authentication infrastructure uses a redundant set of servers that are more easily deployed in Azure infrastructure services, rather than in your on-premises edge network.</span></span>
  
## <a name="bill-of-materials"></a><span data-ttu-id="1a4ee-122">Перечень компонентов</span><span class="sxs-lookup"><span data-stu-id="1a4ee-122">Bill of materials</span></span>

<span data-ttu-id="1a4ee-123">Для этой базовой конфигурации требуется следующий набор служб Azure и компонентов:</span><span class="sxs-lookup"><span data-stu-id="1a4ee-123">This baseline configuration requires the following set of Azure services and components:</span></span>
  
- <span data-ttu-id="1a4ee-124">семь виртуальных машин;</span><span class="sxs-lookup"><span data-stu-id="1a4ee-124">Seven virtual machines</span></span>
    
- <span data-ttu-id="1a4ee-125">одна нелокальная виртуальная сеть с четырьмя подсетями;</span><span class="sxs-lookup"><span data-stu-id="1a4ee-125">One cross-premises virtual network with four subnets</span></span>
    
- <span data-ttu-id="1a4ee-126">четыре группы ресурсов;</span><span class="sxs-lookup"><span data-stu-id="1a4ee-126">Four resource groups</span></span>
    
- <span data-ttu-id="1a4ee-127">три группы доступности;</span><span class="sxs-lookup"><span data-stu-id="1a4ee-127">Three availability sets</span></span>
    
- <span data-ttu-id="1a4ee-128">одна подписка Azure.</span><span class="sxs-lookup"><span data-stu-id="1a4ee-128">One Azure subscription</span></span>
    
<span data-ttu-id="1a4ee-129">Ниже приводится список виртуальных машин, необходимых для данной конфигурации, а также их размеры по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="1a4ee-129">Here are the virtual machines and their default sizes for this configuration.</span></span>
  
|<span data-ttu-id="1a4ee-130">**Элемент**</span><span class="sxs-lookup"><span data-stu-id="1a4ee-130">**Item**</span></span>|<span data-ttu-id="1a4ee-131">**Описание виртуальной машины**</span><span class="sxs-lookup"><span data-stu-id="1a4ee-131">**Virtual machine description**</span></span>|<span data-ttu-id="1a4ee-132">**Изображение коллекции Azure**</span><span class="sxs-lookup"><span data-stu-id="1a4ee-132">**Azure gallery image**</span></span>|<span data-ttu-id="1a4ee-133">**Размер по умолчанию**</span><span class="sxs-lookup"><span data-stu-id="1a4ee-133">**Default size**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="1a4ee-134">1.</span><span class="sxs-lookup"><span data-stu-id="1a4ee-134">1.</span></span>  <br/> |<span data-ttu-id="1a4ee-135">Первый контроллер домена</span><span class="sxs-lookup"><span data-stu-id="1a4ee-135">First domain controller</span></span>  <br/> |<span data-ttu-id="1a4ee-136">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="1a4ee-136">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="1a4ee-137">D2</span><span class="sxs-lookup"><span data-stu-id="1a4ee-137">D2</span></span>  <br/> |
|<span data-ttu-id="1a4ee-138">2.</span><span class="sxs-lookup"><span data-stu-id="1a4ee-138">2.</span></span>  <br/> |<span data-ttu-id="1a4ee-139">Второй контроллер домена</span><span class="sxs-lookup"><span data-stu-id="1a4ee-139">Second domain controller</span></span>  <br/> |<span data-ttu-id="1a4ee-140">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="1a4ee-140">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="1a4ee-141">D2</span><span class="sxs-lookup"><span data-stu-id="1a4ee-141">D2</span></span>  <br/> |
|<span data-ttu-id="1a4ee-142">3.</span><span class="sxs-lookup"><span data-stu-id="1a4ee-142">3.</span></span>  <br/> |<span data-ttu-id="1a4ee-143">Сервер Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="1a4ee-143">Azure AD Connect server</span></span>  <br/> |<span data-ttu-id="1a4ee-144">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="1a4ee-144">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="1a4ee-145">D2</span><span class="sxs-lookup"><span data-stu-id="1a4ee-145">D2</span></span>  <br/> |
|<span data-ttu-id="1a4ee-146">4.</span><span class="sxs-lookup"><span data-stu-id="1a4ee-146">4.</span></span>  <br/> |<span data-ttu-id="1a4ee-147">Первый сервер AD FS</span><span class="sxs-lookup"><span data-stu-id="1a4ee-147">First AD FS server</span></span>  <br/> |<span data-ttu-id="1a4ee-148">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="1a4ee-148">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="1a4ee-149">D2</span><span class="sxs-lookup"><span data-stu-id="1a4ee-149">D2</span></span>  <br/> |
|<span data-ttu-id="1a4ee-150">5.</span><span class="sxs-lookup"><span data-stu-id="1a4ee-150">5.</span></span>  <br/> |<span data-ttu-id="1a4ee-151">Второй сервер AD FS</span><span class="sxs-lookup"><span data-stu-id="1a4ee-151">Second AD FS server</span></span>  <br/> |<span data-ttu-id="1a4ee-152">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="1a4ee-152">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="1a4ee-153">D2</span><span class="sxs-lookup"><span data-stu-id="1a4ee-153">D2</span></span>  <br/> |
|<span data-ttu-id="1a4ee-154">6.</span><span class="sxs-lookup"><span data-stu-id="1a4ee-154">6.</span></span>  <br/> |<span data-ttu-id="1a4ee-155">Первый прокси-сервер веб-приложений</span><span class="sxs-lookup"><span data-stu-id="1a4ee-155">First web application proxy server</span></span>  <br/> |<span data-ttu-id="1a4ee-156">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="1a4ee-156">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="1a4ee-157">D2</span><span class="sxs-lookup"><span data-stu-id="1a4ee-157">D2</span></span>  <br/> |
|<span data-ttu-id="1a4ee-158">7.</span><span class="sxs-lookup"><span data-stu-id="1a4ee-158">7.</span></span>  <br/> |<span data-ttu-id="1a4ee-159">Второй прокси-сервер веб-приложений</span><span class="sxs-lookup"><span data-stu-id="1a4ee-159">Second web application proxy server</span></span>  <br/> |<span data-ttu-id="1a4ee-160">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="1a4ee-160">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="1a4ee-161">D2</span><span class="sxs-lookup"><span data-stu-id="1a4ee-161">D2</span></span>  <br/> |
   
<span data-ttu-id="1a4ee-162">Рассчитать примерные затраты на эту конфигурацию можно с помощью [калькулятора цен Azure](https://azure.microsoft.com/pricing/calculator/).</span><span class="sxs-lookup"><span data-stu-id="1a4ee-162">To compute the estimated costs for this configuration, see the [Azure pricing calculator](https://azure.microsoft.com/pricing/calculator/)</span></span>
  
## <a name="phases-of-deployment"></a><span data-ttu-id="1a4ee-163">Этапы развертывания</span><span class="sxs-lookup"><span data-stu-id="1a4ee-163">Phases of deployment</span></span>

<span data-ttu-id="1a4ee-164">Эта рабочая нагрузка развертывается на следующих этапах:</span><span class="sxs-lookup"><span data-stu-id="1a4ee-164">You deploy this workload in the following phases:</span></span>
  
- <span data-ttu-id="1a4ee-p104">[Этап 1: настройка Azure](high-availability-federated-authentication-phase-1-configure-azure.md). Создание групп ресурсов, учетных записей хранения, групп доступности и распределенной виртуальной сети.</span><span class="sxs-lookup"><span data-stu-id="1a4ee-p104">[Phase 1: Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md). Create resource groups, storage accounts, availability sets, and a cross-premises virtual network.</span></span>
    
- <span data-ttu-id="1a4ee-167">[Этап 2. Настройка контроллеров домена](high-availability-federated-authentication-phase-2-configure-domain-controllers.md).</span><span class="sxs-lookup"><span data-stu-id="1a4ee-167">[High availability federated authentication Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md)</span></span> <span data-ttu-id="1a4ee-168">Создание и настройка реплики контроллеров домена AD DS и сервера синхронизации каталогов.</span><span class="sxs-lookup"><span data-stu-id="1a4ee-168">Create and configure replica AD DS domain controllers and the directory synchronization server.</span></span>
    
- <span data-ttu-id="1a4ee-p106">[Этап 3: настройка серверов AD FS](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md). Создание и настройка двух серверов AD FS.</span><span class="sxs-lookup"><span data-stu-id="1a4ee-p106">[Phase 3: Configure AD FS servers](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md). Create and configure the two AD FS servers.</span></span>
    
- <span data-ttu-id="1a4ee-p107">[Этап 4: настройка прокси веб-приложений](high-availability-federated-authentication-phase-4-configure-web-application-pro.md). Создание и настройка двух прокси-серверов веб-приложений.</span><span class="sxs-lookup"><span data-stu-id="1a4ee-p107">[Phase 4: Configure web application proxies](high-availability-federated-authentication-phase-4-configure-web-application-pro.md). Create and configure the two web application proxy servers.</span></span>
    
- <span data-ttu-id="1a4ee-p108">[Этап 5: настройка федеративной проверки подлинности для Office 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md). Настройка федеративной проверки подлинности для подписки на Office 365.</span><span class="sxs-lookup"><span data-stu-id="1a4ee-p108">[Phase 5: Configure federated authentication for Office 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md). Configure federated authentication for your Office 365 subscription.</span></span>
    
<span data-ttu-id="1a4ee-p109">Эти статьи содержат поэтапное руководство по созданию функциональной федеративной проверки подлинности с высоким уровнем доступности для Office 365 в службах инфраструктуры Azure для предопределенной архитектуры. Учитывайте следующее:</span><span class="sxs-lookup"><span data-stu-id="1a4ee-p109">These articles provide a prescriptive, phase-by-phase guide for a predefined architecture to create a functional, high availability federated authentication for Office 365 in Azure infrastructure services. Keep the following in mind:</span></span>
  
- <span data-ttu-id="1a4ee-177">Если у вас уже есть опыт развертывания AD FS, можете скорректировать инструкции на этапах 3 и 4 и создать группу серверов для своих нужд.</span><span class="sxs-lookup"><span data-stu-id="1a4ee-177">If you are an experienced AD FS implementer, feel free to adapt the instructions in phases 3 and 4 and build the set of servers that best suits your needs.</span></span>
    
- <span data-ttu-id="1a4ee-178">Если у вас уже есть гибридное облачное развертывание Azure с нелокальной виртуальной сетью, можете скорректировать или пропустить инструкции на этапах 1 и 2 и разместить серверы AD FS и прокси-серверы веб-приложений в соответствующих подсетях.</span><span class="sxs-lookup"><span data-stu-id="1a4ee-178">If you already have an existing Azure hybrid cloud deployment with an existing cross-premises virtual network, feel free to adapt or skip the instructions in phases 1 and 2 and place the AD FS and web application proxy servers on the appropriate subnets.</span></span>
    
<span data-ttu-id="1a4ee-179">Для создания среды разработки и тестирования или экспериментальной версии этой конфигурации ознакомьтесь со статьей [Федеративное удостоверение для среды разработки и тестирования Office 365](federated-identity-for-your-office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="1a4ee-179">To build a dev/test environment or a proof-of-concept of this configuration, see [Federated identity for your Office 365 dev/test environment](federated-identity-for-your-office-365-dev-test-environment.md).</span></span>
  
## <a name="next-step"></a><span data-ttu-id="1a4ee-180">Следующий шаг</span><span class="sxs-lookup"><span data-stu-id="1a4ee-180">Next step</span></span>

<span data-ttu-id="1a4ee-181">Начните настройку этой рабочей нагрузки с [этапа 1: настройка Azure](high-availability-federated-authentication-phase-1-configure-azure.md). </span><span class="sxs-lookup"><span data-stu-id="1a4ee-181">Start the configuration of this workload with [High availability federated authentication Phase 1: Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span></span> 
  
