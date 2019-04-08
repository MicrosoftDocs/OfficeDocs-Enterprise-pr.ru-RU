---
title: Развертывание службы синхронизации каталогов Office 365 в Microsoft Azure
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/05/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_Solutions
ms.assetid: b8464818-4325-4a56-b022-5af1dad2aa8b
description: Сводка. Развертывание средства Azure AD Connect на виртуальной машине в Azure для синхронизации учетных записей между локальным каталогом и клиентом Azure AD, связанным с подпиской на Office 365.
ms.openlocfilehash: 02706235d2de816ff5dd4ceeced8b7158ab7c2ce
ms.sourcegitcommit: 201d3338d8bbc6da9389e62e2add8a17384fab4d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2019
ms.locfileid: "31038063"
---
# <a name="deploy-office-365-directory-synchronization-in-microsoft-azure"></a><span data-ttu-id="5faa5-103">Развертывание службы синхронизации каталогов Office 365 в Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="5faa5-103">Deploy Office 365 Directory Synchronization in Microsoft Azure</span></span>

 <span data-ttu-id="5faa5-104">**Сводка.** Развертывание средства Azure AD Connect на виртуальной машине в службах инфраструктуры Azure для синхронизации учетных записей между локальным каталогом и клиентом Azure AD, связанным с подпиской на Office 365.</span><span class="sxs-lookup"><span data-stu-id="5faa5-104">**Summary:** Deploy Azure AD Connect on a virtual machine in Azure infrastructure services to synchronize accounts between your on-premises directory and the Azure AD tenant of your Office 365 subscription.</span></span>
  
<span data-ttu-id="5faa5-p101">Средство Azure Active Directory Connect (предыдущие названия: средство синхронизации каталогов и средство DirSync.exe) — это приложение, которое устанавливается на сервере, входящем в домен, для синхронизации пользователей локальных доменных служб Active Directory (AD DS) с клиентом Azure AD, связанным с подпиской на Office 365. Office 365 использует службу каталогов Azure Active Directory (Azure AD). Подписка на Office 365 включает клиент Azure AD. Его также можно использовать для управления удостоверениями организации в других облачных рабочих нагрузках, в том числе других приложениях SaaS и приложениях в Azure.</span><span class="sxs-lookup"><span data-stu-id="5faa5-p101">Azure Active Directory (AD) Connect (formerly known as the Directory Synchronization tool, Directory Sync tool, or the DirSync.exe tool) is an application that you install on a domain-joined server to synchronize your on-premises Windows Server Active Directory (AD) users to the Azure AD tenant of your Office 365 subscription. Office 365 uses Azure Active Directory (Azure AD) for its directory service. Your Office 365 subscription includes an Azure AD tenant. This tenant can also be used for management of your organization's identities with other cloud workloads, including other SaaS applications and apps in Azure.</span></span>

<span data-ttu-id="5faa5-109">Вы можете установить средство Azure AD Connect как на локальном сервере, так и на виртуальной машине в Azure. Последний вариант установки возможен по причинам, указанным ниже:</span><span class="sxs-lookup"><span data-stu-id="5faa5-109">You can install Azure AD Connect on a on-premises server, but you can also install it on a virtual machine in Azure for these reasons:</span></span>
  
- <span data-ttu-id="5faa5-110">Вы можете быстрее подготовить и настроить облачные службы, чтобы сделать их доступными для пользователей.</span><span class="sxs-lookup"><span data-stu-id="5faa5-110">You can provision and configure cloud-based servers faster, making the services available to your users sooner.</span></span>
- <span data-ttu-id="5faa5-111">Azure обеспечивает высокую доступность сайтов и требует меньше усилий.</span><span class="sxs-lookup"><span data-stu-id="5faa5-111">Azure offers better site availability with less effort.</span></span>
- <span data-ttu-id="5faa5-112">Вы можете сократить количество локальных серверов в своей организации.</span><span class="sxs-lookup"><span data-stu-id="5faa5-112">You can reduce the number of on-premises servers in your organization.</span></span>

<span data-ttu-id="5faa5-p102">Для этого решения требуется соединение между локальной сетью и виртуальной сетью Azure. Дополнительные сведения см. в статье [Подключение локальной сети к виртуальной сети Microsoft Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span><span class="sxs-lookup"><span data-stu-id="5faa5-p102">This solution requires connectivity between your on-premises network and your Azure virtual network. For more information, see [Connect an on-premises network to a Microsoft Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span></span> 
  
> [!NOTE]
> <span data-ttu-id="5faa5-p103">В этой статье описывается синхронизация одного домена в одном лесу. Средство Azure AD Connect синхронизирует все домены AD DS в лесу Active Directory с Office 365. Если вам нужно синхронизировать несколько лесов Active Directory с Office 365, см. [сценарий синхронизации каталогов с единым входом при наличии нескольких лесов](https://go.microsoft.com/fwlink/p/?LinkId=393091).</span><span class="sxs-lookup"><span data-stu-id="5faa5-p103">This article describes synchronization of a single domain in a single forest. Azure AD Connect synchronizes all Windows Server AD domains in your Active Directory forest with Office 365. If you have multiple Active Directory forests to synchronize with Office 365, see [Multi-forest Directory Sync with Single Sign-On Scenario](https://go.microsoft.com/fwlink/p/?LinkId=393091).</span></span> 
  
## <a name="overview-of-deploying-office-365-directory-synchronization-in-azure"></a><span data-ttu-id="5faa5-118">Общие сведения о развертывании синхронизации каталогов Office 365 в Azure</span><span class="sxs-lookup"><span data-stu-id="5faa5-118">Overview of deploying Office 365 directory synchronization in Azure</span></span>

<span data-ttu-id="5faa5-119">На представленной ниже схеме показано средство Azure AD Connect, запущенное на виртуальной машине в Azure (сервер синхронизации каталогов), которое синхронизирует локальный лес AD DS с подпиской на Office 365.</span><span class="sxs-lookup"><span data-stu-id="5faa5-119">The following diagram shows Azure AD Connect running on a virtual machine in Azure (the directory sync server) that synchronizes an on-premises Windows Server AD forest to an Office 365 subscription.</span></span>
  
![Средство Azure AD Connect на виртуальной машине в Azure синхронизирует локальные учетные записи с клиентом Azure AD для Office 365](media/CP-DirSyncOverview.png)
  
<span data-ttu-id="5faa5-p104">На этой схеме показаны две сети, соединенные VPN-подключением типа "сеть-сеть" или подключением ExpressRoute. В локальной сети размещаются контроллеры доменов AD DS, а в виртуальной сети Azure — сервер синхронизации каталогов, виртуальная машина, на которой запущено [средство Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594). Из сервера синхронизации каталогов исходит два основных потока трафика:</span><span class="sxs-lookup"><span data-stu-id="5faa5-p104">In the diagram, there are two networks connected by a site-to-site VPN or ExpressRoute connection. There is an on-premises network where Windows Server AD domain controllers are located, and there is an Azure virtual network with a directory sync server, which is a virtual machine running [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594). There are two main traffic flows originating from the directory sync server:</span></span>
  
-  <span data-ttu-id="5faa5-124">Средство Azure AD Connect отправляет контроллеру домена в локальной сети запросы на изменение учетных записей и паролей.</span><span class="sxs-lookup"><span data-stu-id="5faa5-124">Azure AD Connect queries a domain controller on the on-premises network for changes to accounts and passwords.</span></span>
-  <span data-ttu-id="5faa5-p105">Средство Azure AD Connect отправляет изменения учетных записей и паролей экземпляру Azure AD подписки на Office 365. Так как сервер синхронизации каталогов является расширением локальной сети, эти изменения отправляются через прокси-сервер локальной сети.</span><span class="sxs-lookup"><span data-stu-id="5faa5-p105">Azure AD Connect sends the changes to accounts and passwords to the Azure AD instance of your Office 365 subscription. Because the directory sync server is in an extended portion of your on-premises network, these changes are sent through the on-premises network's proxy server.</span></span>
    
> [!NOTE]
> <span data-ttu-id="5faa5-p106">В этом решении описывается синхронизация одного домена Active Directory в одном лесу. Средство синхронизации Azure AD Connect синхронизирует все домены Active Directory в лесу Active Directory с Office 365. Если вам нужно синхронизировать несколько лесов Active Directory с Office 365, см. [сценарий синхронизации каталогов с единым входом при наличии нескольких лесов](https://go.microsoft.com/fwlink/p/?LinkId=393091).</span><span class="sxs-lookup"><span data-stu-id="5faa5-p106">This solution describes synchronization of a single Active Directory domain, in a single Active Directory forest. Azure AD Connect synchronizes all Active Directory domains in your Active Directory forest with Office 365. If you have multiple Active Directory forests to synchronize with Office 365, see [Multi-forest Directory Sync with Single Sign-On Scenario](https://go.microsoft.com/fwlink/p/?LinkId=393091).</span></span> 
  
<span data-ttu-id="5faa5-130">Развертывание этого решения делится на два основных этапа:</span><span class="sxs-lookup"><span data-stu-id="5faa5-130">There are two major steps when you deploy this solution:</span></span>
  
1. <span data-ttu-id="5faa5-p107">Создание виртуальной сети Azure и настройка VPN-подключения типа "сеть-сеть" к локальной сети. Дополнительные сведения см. в статье [Подключение локальной сети к виртуальной сети Microsoft Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span><span class="sxs-lookup"><span data-stu-id="5faa5-p107">Create an Azure virtual network and establish a site-to-site VPN connection to your on-premises network. For more information, see [Connect an on-premises network to a Microsoft Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span></span>
    
2. <span data-ttu-id="5faa5-p108">Установка [средства Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594) на присоединенной к домену виртуальной машине в Azure и синхронизация локального леса AD DS с Office 365. Этот процесс включает следующие этапы:</span><span class="sxs-lookup"><span data-stu-id="5faa5-p108">Install [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594) on a domain-joined virtual machine in Azure, and then synchronize the on-premises Windows Server AD to Office 365. This involves:</span></span>
    
    <span data-ttu-id="5faa5-135">Создание виртуальной машины Azure для запуска Azure AD Connect.</span><span class="sxs-lookup"><span data-stu-id="5faa5-135">Creating an Azure Virtual Machine to run Azure AD Connect.</span></span>
    
    <span data-ttu-id="5faa5-136">Установка и настройка [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594).</span><span class="sxs-lookup"><span data-stu-id="5faa5-136">Installing and configuring [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594).</span></span>
    
    <span data-ttu-id="5faa5-p109">Для настройки средства Azure AD Connect требуются учетные данные (имя пользователя и пароль) администратора Azure AD и администратора предприятия AD DS. Средство Azure AD Connect запускается мгновенно и регулярно для синхронизации локального леса AD DS с Office 365.</span><span class="sxs-lookup"><span data-stu-id="5faa5-p109">Configuring Azure AD Connect requires the credentials (user name and password) of an Azure AD administrator account and a Windows Server AD enterprise administrator account. Azure AD Connect runs immediately and on an ongoing basis to synchronize the on-premises Windows Server AD forest to Office 365.</span></span>
    
<span data-ttu-id="5faa5-139">Прежде чем развертывать это решение в эксплуатационной среде, можно воспользоваться инструкциями в статье [Синхронизация каталогов для среды разработки и тестирования Office 365](dirsync-for-your-office-365-dev-test-environment.md), чтобы установить эту конфигурацию для демонстраций или экспериментов.</span><span class="sxs-lookup"><span data-stu-id="5faa5-139">Before you deploy this solution in production, you can use the instructions in [Directory synchronization for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md) to set this configuration up as a proof of concept, for demonstrations, or for experimentation.</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="5faa5-140">После настройки средство Azure AD Connect не сохраняет учетные данные администратора предприятия AD DS.</span><span class="sxs-lookup"><span data-stu-id="5faa5-140">When Azure AD Connect configuration completes, it does not save the Windows Server AD enterprise administrator account credentials.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="5faa5-p110">Это решение описывает синхронизацию одного леса AD DS с Office 365. Топология, описываемая в этой статье, предоставляет только один из способов реализации решения. Топология вашей организации может отличаться в связи с уникальными требованиями к сети и ее безопасности.</span><span class="sxs-lookup"><span data-stu-id="5faa5-p110">This solution describes synchronizing a single Windows Server AD forest to Office 365. The topology discussed in this article represents only one way to implement this solution. Your organization's topology might differ based on your unique network requirements and security considerations.</span></span> 
  
## <a name="plan-for-hosting-a-directory-sync-server-for-office-365-in-azure"></a><span data-ttu-id="5faa5-144">Планирование размещения сервера синхронизации каталогов для Office 365 в Azure</span><span class="sxs-lookup"><span data-stu-id="5faa5-144">Plan for hosting a directory sync server for Office 365 in Azure</span></span>
<span data-ttu-id="5faa5-145"><a name="PlanningVirtual"> </a></span><span class="sxs-lookup"><span data-stu-id="5faa5-145"><a name="PlanningVirtual"> </a></span></span>

### <a name="prerequisites"></a><span data-ttu-id="5faa5-146">Требования</span><span class="sxs-lookup"><span data-stu-id="5faa5-146">Prerequisites</span></span>

<span data-ttu-id="5faa5-147">Прежде чем приступать к работе, изучите требования для развертывания этого решения:</span><span class="sxs-lookup"><span data-stu-id="5faa5-147">Before you begin, review the following prerequisites for this solution:</span></span>
  
- <span data-ttu-id="5faa5-148">Изучите соответствующие материалы по планированию в разделе [Планирование виртуальной сети Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#plan-your-azure-virtual-network).</span><span class="sxs-lookup"><span data-stu-id="5faa5-148">Review the related planning content in [Plan your Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#plan-your-azure-virtual-network).</span></span>
    
- <span data-ttu-id="5faa5-149">Убедитесь, что ваша организация отвечает всем [требованиям](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#prerequisites) для настройки виртуальной сети Azure.</span><span class="sxs-lookup"><span data-stu-id="5faa5-149">Ensure that you meet all [Prerequisites](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#prerequisites) for configuring the Azure virtual network.</span></span>
    
- <span data-ttu-id="5faa5-p111">Приготовьте подписку на Office 365, которая включает функцию интеграции с Active Directory. Сведения о подписках на Office 365 см. на [этой странице](https://products.office.com/compare-all-microsoft-office-products?tab=2).</span><span class="sxs-lookup"><span data-stu-id="5faa5-p111">Have an Office 365 subscription that includes the Active Directory integration feature. For information about Office 365 subscriptions, go to the [Office 365 subscription page](https://products.office.com/compare-all-microsoft-office-products?tab=2).</span></span>
    
- <span data-ttu-id="5faa5-152">Подготовьте одну виртуальную машину Azure, на которой запущено средство Azure AD Connect, для синхронизации локального леса AD DS с Office 365.</span><span class="sxs-lookup"><span data-stu-id="5faa5-152">Provision one Azure Virtual Machine that runs Azure AD Connect to synchronize your on-premises Windows Server AD forest with Office 365.</span></span>
    
    <span data-ttu-id="5faa5-153">У вас должны быть учетные данные (имена и пароли) администратора предприятия AD DS и администратора Azure AD.</span><span class="sxs-lookup"><span data-stu-id="5faa5-153">You must have the credentials (names and passwords) for a Windows Server AD enterprise administrator account and an Azure AD Administrator account.</span></span>
    
### <a name="solution-architecture-design-assumptions"></a><span data-ttu-id="5faa5-154">Допущения по архитектуре решения</span><span class="sxs-lookup"><span data-stu-id="5faa5-154">Solution architecture design assumptions</span></span>

<span data-ttu-id="5faa5-155">Ниже приведены принятые проектные решения.</span><span class="sxs-lookup"><span data-stu-id="5faa5-155">The following list describes the design choices made for this solution.</span></span>
  
- <span data-ttu-id="5faa5-p112">Это решение использует одну виртуальную сеть Azure с VPN-подключением типа "сеть-сеть". В виртуальной сети Azure размещается одна подсеть с одним сервером синхронизации каталогов, на котором запущено средство Azure AD Connect.</span><span class="sxs-lookup"><span data-stu-id="5faa5-p112">This solution uses a single Azure virtual network with a site-to-site VPN connection. The Azure virtual network hosts a single subnet that has one server, the directory sync server that is running Azure AD Connect.</span></span> 
    
- <span data-ttu-id="5faa5-158">В локальной сети размещены контроллер домена и DNS-серверы.</span><span class="sxs-lookup"><span data-stu-id="5faa5-158">On the on-premises network, a domain controller and DNS servers exist.</span></span>
    
- <span data-ttu-id="5faa5-p113">Вместо единого входа средство Azure AD Connect выполняет синхронизацию хэша паролей. Вам не требуется развертывать инфраструктуру служб федерации Active Directory (AD FS). Дополнительные сведения о синхронизации хэша паролей и едином входе см. в статье [Выбор правильного метода аутентификации для гибридного решения для идентификации Azure Active Directory](http://aka.ms/auth-options).</span><span class="sxs-lookup"><span data-stu-id="5faa5-p113">Azure AD Connect performs password hash synchronization instead of single sign-on. You do not have to deploy an Active Directory Federation Services (AD FS) infrastructure. To learn more about password hash synchronization and single sign-on options, see [Choosing the right authentication method for your Azure Active Directory hybrid identity solution](http://aka.ms/auth-options).</span></span>
    
<span data-ttu-id="5faa5-p114">При развертывании этого решения в своей среде вы можете рассмотреть дополнительные варианты структуры. К ним относятся следующие:</span><span class="sxs-lookup"><span data-stu-id="5faa5-p114">There are additional design choices that you might consider when you deploy this solution in your environment. These include the following:</span></span>
  
- <span data-ttu-id="5faa5-164">Если в виртуальной сети Azure уже есть DNS-серверы, определите, должен ли сервер синхронизации каталогов использовать их вместо DNS-серверов в локальной сети.</span><span class="sxs-lookup"><span data-stu-id="5faa5-164">If there are existing DNS servers in an existing Azure virtual network, determine whether you want your directory sync server to use them for name resolution instead of DNS servers on the on-premises network.</span></span>
    
- <span data-ttu-id="5faa5-p115">Если в существующей виртуальной сети Azure есть контроллеры доменов, решите, будет ли настройка сайтов и служб Active Directory более подходящим вариантом для вашей организации. Вместо контроллеров доменов локальной сети сервер синхронизации каталогов может отправлять запросы контроллерам доменов в виртуальной сети Azure для поиска изменений в учетных записях и паролях.</span><span class="sxs-lookup"><span data-stu-id="5faa5-p115">If there are domain controllers in an existing Azure virtual network, determine whether configuring Active Directory Sites and Services may be a better option for you. The directory sync server can query the domain controllers in the Azure virtual network for changes in accounts and passwords instead of domain controllers on the on-premises network.</span></span>
    
## <a name="deployment-roadmap"></a><span data-ttu-id="5faa5-167">План развертывания</span><span class="sxs-lookup"><span data-stu-id="5faa5-167">Deployment roadmap</span></span>

<span data-ttu-id="5faa5-168">Развертывание Azure AD Connect на виртуальной машине в Azure состоит из трех этапов:</span><span class="sxs-lookup"><span data-stu-id="5faa5-168">Deploying Azure AD Connect on a virtual machine in Azure consists of three phases:</span></span>
  
- <span data-ttu-id="5faa5-169">Этап 1. Создание и настройка виртуальной сети Azure</span><span class="sxs-lookup"><span data-stu-id="5faa5-169">Phase 1: Create and configure the Azure virtual network</span></span>
    
- <span data-ttu-id="5faa5-170">Этап 2. Создание и настройка виртуальной машины Azure</span><span class="sxs-lookup"><span data-stu-id="5faa5-170">Phase 2: Create and configure the Azure virtual machine</span></span>
    
- <span data-ttu-id="5faa5-171">Этап 3. Установка и настройка Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="5faa5-171">Phase 3: Install and configure Azure AD Connect</span></span>
    
<span data-ttu-id="5faa5-172">После развертывания также необходимо назначить расположения и лицензии для новых учетных записей пользователей в Office 365.</span><span class="sxs-lookup"><span data-stu-id="5faa5-172">After deployment, you must also assign locations and licenses for the new user accounts in Office 365.</span></span>

<!--  
> [!TIP]
> The [Directory Synchronization Server in Azure Deployment Kit](https://gallery.technet.microsoft.com/DirSync-Server-in-Azure-32cb2ded) has all of the Azure PowerShell blocks to build out this solution, the diagrams in Microsoft PowerPoint and Visio format, and a Microsoft Excel configuration workbook that generates Azure PowerShell command blocks customized for your settings.
-->
  
### <a name="phase-1-create-and-configure-the-azure-virtual-network"></a><span data-ttu-id="5faa5-173">Этап 1. Создание и настройка виртуальной сети Azure</span><span class="sxs-lookup"><span data-stu-id="5faa5-173">Phase 1: Create and configure the Azure virtual network</span></span>

<span data-ttu-id="5faa5-174">Чтобы создать и настроить виртуальную сеть Azure, выполните [Этап 1. Подготовка локальной сети](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#phase-1-prepare-your-on-premises-network) и [Этап 2. Создание виртуальной сети в Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#phase-2-create-the-cross-premises-virtual-network-in-azure) из схемы развертывания [Подключение локальной сети к виртуальной сети Microsoft Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span><span class="sxs-lookup"><span data-stu-id="5faa5-174">To create and configure the Azure virtual network, complete [Phase 1: Prepare your on-premises network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#phase-1-prepare-your-on-premises-network) and [Phase 2: Create the cross-premises virtual network in Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#phase-2-create-the-cross-premises-virtual-network-in-azure) in the deployment roadmap of [Connect an on-premises network to a Microsoft Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span></span>
  
<span data-ttu-id="5faa5-175">Ниже показана итоговая конфигурация.</span><span class="sxs-lookup"><span data-stu-id="5faa5-175">This is your resulting configuration.</span></span>
  
![Этап 1. Развертывание сервера синхронизации каталогов для Office 365 в Azure](media/aab6a9a4-eb78-4d85-9b96-711e6de420d7.png)
  
<span data-ttu-id="5faa5-177">На этом рисунке показана локальная сеть, подключенная к виртуальной сети Azure через подключение VPN типа "сеть-сеть" или ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="5faa5-177">This figure shows an on-premises network connected to an Azure virtual network through a site-to-site VPN or ExpressRoute connection.</span></span>
  
### <a name="phase-2-create-and-configure-the-azure-virtual-machine"></a><span data-ttu-id="5faa5-178">Этап 2. Создание и настройка виртуальной машины Azure</span><span class="sxs-lookup"><span data-stu-id="5faa5-178">Phase 2: Create and configure the Azure virtual machine</span></span>

<span data-ttu-id="5faa5-p116">Создайте виртуальную машину в Azure, следуя инструкциям в статье [Создание первой виртуальной машины Windows на портале Azure](https://go.microsoft.com/fwlink/p/?LinkId=393098). Используйте следующие параметры:</span><span class="sxs-lookup"><span data-stu-id="5faa5-p116">Create the virtual machine in Azure using the instructions [Create your first Windows virtual machine in the Azure portal](https://go.microsoft.com/fwlink/p/?LinkId=393098). Use the following settings:</span></span>
  
- <span data-ttu-id="5faa5-p117">В области **Основные** выберите ту же подписку, расположение и группу ресурсов, что и в виртуальной сети. Запишите имя пользователя и пароль в надежном месте. Они потребуются позже для подключения к виртуальной машине.</span><span class="sxs-lookup"><span data-stu-id="5faa5-p117">On the **Basics** pane, select the same subscription, location, and resource group as your virtual network. Record the user name and password in a secure location. You will need these later to connect to the virtual machine.</span></span>
    
- <span data-ttu-id="5faa5-184">В области **Выберите размер** выберите размер **Стандартный A2**.</span><span class="sxs-lookup"><span data-stu-id="5faa5-184">On the **Choose a size** pane, choose the **A2 Standard** size.</span></span>
    
- <span data-ttu-id="5faa5-p118">В области **Параметры** в разделе **Хранилище** выберите тип хранилища **Стандартный**. В разделе **Сеть** выберите имя виртуальной сети и подсеть для размещения сервера синхронизации каталогов (не GatewaySubnet). Для всех остальных параметров оставьте значения по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="5faa5-p118">On the **Settings** pane, in the **Storage** section, select the **Standard** storage type. In the **Network** section, select the name of your virtual network and the subnet for hosting the directory sync server (not the GatewaySubnet). Leave all other settings at their default values.</span></span>
    
<span data-ttu-id="5faa5-188">Проверьте внутренний DNS, чтобы убедиться, что сервер синхронизации каталогов правильно использует DNS и для виртуальной машины добавлена запись адреса (A) с ее IP-адресом.</span><span class="sxs-lookup"><span data-stu-id="5faa5-188">Verify that your directory sync server is using DNS correctly by checking your internal DNS to make sure that an Address (A) record was added for the virtual machine with its IP address.</span></span> 
  
<span data-ttu-id="5faa5-p119">Воспользуйтесь инструкциями в разделе [Подключение к виртуальной машине и вход](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-hero-tutorial?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json#connect-to-the-virtual-machine-and-sign-on), чтобы подключиться к серверу синхронизации каталогов через подключение к удаленному рабочему столу. После входа присоедините виртуальную машину к локальному домену AD DS.</span><span class="sxs-lookup"><span data-stu-id="5faa5-p119">Use the instructions in [Connect to the virtual machine and sign on](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-hero-tutorial?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json#connect-to-the-virtual-machine-and-sign-on) to connect to the directory sync server with a Remote Desktop Connection. After signing in, join the virtual machine to the on-premises Windows Server AD domain.</span></span>
  
<span data-ttu-id="5faa5-p120">Чтобы предоставить средству Azure AD Connect доступ к ресурсам Интернета, необходимо настроить сервер синхронизации каталогов на использование прокси-сервера локальной сети. Обратитесь к администратору сети за дополнительными инструкциями по настройке.</span><span class="sxs-lookup"><span data-stu-id="5faa5-p120">For Azure AD Connect to gain access to Internet resources, you must configure the directory sync server to use the on-premises network's proxy server. You should contact your network administrator for any additional configuration steps to perform.</span></span>
  
<span data-ttu-id="5faa5-193">Ниже показана итоговая конфигурация.</span><span class="sxs-lookup"><span data-stu-id="5faa5-193">This is your resulting configuration.</span></span>
  
![Этап 2. Развертывание сервера синхронизации каталогов для Office 365 в Azure](media/9d8c9349-a207-4828-9b2b-826fe9c06af3.png)
  
<span data-ttu-id="5faa5-195">На этом рисунке показана виртуальная машина сервера синхронизации каталогов в виртуальной сети Azure.</span><span class="sxs-lookup"><span data-stu-id="5faa5-195">This figure shows the directory sync server virtual machine in the cross-premises Azure virtual network.</span></span>
  
### <a name="phase-3-install-and-configure-azure-ad-connect"></a><span data-ttu-id="5faa5-196">Этап 3. Установка и настройка Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="5faa5-196">Phase 3: Install and configure Azure AD Connect</span></span>

<span data-ttu-id="5faa5-197">Выполните следующие действия:</span><span class="sxs-lookup"><span data-stu-id="5faa5-197">Complete the following procedure:</span></span>
  
1. <span data-ttu-id="5faa5-p121">Подключитесь к серверу синхронизации каталогов в режиме удаленного рабочего стола, используя учетную запись домена AD DS с правами локального администратора. См. статью [Подключение к виртуальной машине и вход](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-hero-tutorial?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json#connect-to-the-virtual-machine-and-sign-on).</span><span class="sxs-lookup"><span data-stu-id="5faa5-p121">Connect to the directory sync server using a Remote Desktop Connection with a Windows Server AD domain account that has local administrator privileges. See [Connect to the virtual machine and sign on](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-hero-tutorial?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json#connect-to-the-virtual-machine-and-sign-on).</span></span>
    
2. <span data-ttu-id="5faa5-200">На сервере синхронизации каталогов откройте статью [Настройка синхронизации каталогов для Office 365](set-up-directory-synchronization.md) и следуйте инструкциям для синхронизации каталогов с синхронизацией хэша паролей.</span><span class="sxs-lookup"><span data-stu-id="5faa5-200">From the directory sync server, open the [Set up directory synchronization for Office 365](set-up-directory-synchronization.md) article and follow the directions for directory synchronization with password hash synchronization.</span></span>
    
> [!CAUTION]
> <span data-ttu-id="5faa5-p122">Программа установки создает учетную запись **AAD_xxxxxxxxxxxx** в подразделении "Локальные пользователи". Не перемещайте и не удаляйте эту учетную запись, иначе синхронизация будет невозможна.</span><span class="sxs-lookup"><span data-stu-id="5faa5-p122">Setup creates the **AAD_xxxxxxxxxxxx** account in the Local Users organizational unit (OU). Do not move or remove this account or synchronization will fail.</span></span>
  
<span data-ttu-id="5faa5-203">Ниже показана итоговая конфигурация.</span><span class="sxs-lookup"><span data-stu-id="5faa5-203">This is your resulting configuration.</span></span>
  
![Этап 3. Развертывание сервера синхронизации каталогов для Office 365 в Azure](media/3f692b62-b77c-4877-abee-83c7edffa922.png)
  
<span data-ttu-id="5faa5-205">На этом рисунке показан сервер синхронизации каталогов со средством Azure AD Connect в виртуальной сети Azure.</span><span class="sxs-lookup"><span data-stu-id="5faa5-205">This figure shows the directory sync server with Azure AD Connect in the cross-premises Azure virtual network.</span></span>
  
### <a name="assign-locations-and-licenses-to-users-in-office-365"></a><span data-ttu-id="5faa5-206">Назначение расположений и лицензий пользователям в Office 365</span><span class="sxs-lookup"><span data-stu-id="5faa5-206">Assign locations and licenses to users in Office 365</span></span>

<span data-ttu-id="5faa5-p123">Средство Azure AD Connect добавляет учетные записи из локального леса AD DS в подписку на Office 365, но чтобы пользователи могли входить в Office 365 и использовать службы, необходимо настроить расположение и лицензии. Чтобы добавить расположение и активировать лицензии для соответствующих учетных записей пользователей, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="5faa5-p123">Azure AD Connect adds accounts to your Office 365 subscription from the on-premises Windows Server AD, but in order for users to sign in to Office 365 and use its services, the accounts must be configured with a location and licenses. Use these steps to add the location and activate licenses for the appropriate user accounts:</span></span>
  
1. <span data-ttu-id="5faa5-209">Выполните вход на [странице портала Office 365](https://www.office.com) и нажмите плитку **Администрирование**.</span><span class="sxs-lookup"><span data-stu-id="5faa5-209">Sign in to the [Office 365 portal page](https://www.office.com), and then click **Admin**.</span></span>
    
2. <span data-ttu-id="5faa5-210">На панели навигации слева выберите **Пользователи > Активные пользователи**.</span><span class="sxs-lookup"><span data-stu-id="5faa5-210">In the left navigation, click **Users > Active users**.</span></span>
    
3. <span data-ttu-id="5faa5-211">В списке учетных записей пользователей установите флажок рядом с нужным пользователем.</span><span class="sxs-lookup"><span data-stu-id="5faa5-211">In the list of user accounts, select the check box next to the user you want to activate.</span></span>
    
4. <span data-ttu-id="5faa5-212">На странице пользователя выберите **Изменить** для пункта **Лицензии на продукты**.</span><span class="sxs-lookup"><span data-stu-id="5faa5-212">On the page for the user, click **Edit** for **Product licenses**.</span></span>
    
5. <span data-ttu-id="5faa5-213">На странице **Лицензии на продукты** выберите расположение пользователя и включите для него соответствующие лицензии.</span><span class="sxs-lookup"><span data-stu-id="5faa5-213">On the **Product licenses** page, select a location for the user for **Location**, and then enable the appropriate licenses for the user.</span></span>
    
6. <span data-ttu-id="5faa5-214">По завершении нажмите кнопку **Сохранить**, а затем кнопку **Закрыть** дважды.</span><span class="sxs-lookup"><span data-stu-id="5faa5-214">When complete, click **Save**, and then click **Close** twice.</span></span>
    
7. <span data-ttu-id="5faa5-215">Вернитесь к шагу 3, чтобы повторить эти действия для других пользователей.</span><span class="sxs-lookup"><span data-stu-id="5faa5-215">Go back to step 3 for additional users.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="5faa5-216">См. также</span><span class="sxs-lookup"><span data-stu-id="5faa5-216">See also</span></span>

[<span data-ttu-id="5faa5-217">Освоение облака и гибридные решения</span><span class="sxs-lookup"><span data-stu-id="5faa5-217">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
  
[<span data-ttu-id="5faa5-218">Подключение локальной сети к виртуальной сети Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="5faa5-218">Connect an on-premises network to a Microsoft Azure virtual network</span></span>](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)

[<span data-ttu-id="5faa5-219">Скачать Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="5faa5-219">Download Azure AD Connect</span></span>](https://www.microsoft.com/download/details.aspx?id=47594)
  
[<span data-ttu-id="5faa5-220">Настройка синхронизации каталогов для Office 365</span><span class="sxs-lookup"><span data-stu-id="5faa5-220">Set up directory synchronization for Office 365</span></span>](set-up-directory-synchronization.md)
  
<!--
[Directory Synchronization server in Azure Deployment Kit](https://gallery.technet.microsoft.com/DirSync-Server-in-Azure-32cb2ded)
-->


