---
title: Развертывание Office 365 синхронизации службы каталогов в Microsoft Azure
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/04/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_Solutions
ms.assetid: b8464818-4325-4a56-b022-5af1dad2aa8b
description: 'Сводка: Развертывание Azure AD подключение на виртуальной машине в среде Azure для синхронизации учетных записей между локального каталога и клиента Azure AD подписки Office 365.'
ms.openlocfilehash: af0c837ead0ddfce31d7f3635f3283f118d26dca
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="deploy-office-365-directory-synchronization-in-microsoft-azure"></a><span data-ttu-id="25da5-103">Развертывание Office 365 синхронизации службы каталогов в Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="25da5-103">Deploy Office 365 Directory Synchronization in Microsoft Azure</span></span>

 <span data-ttu-id="25da5-104">**Сводка:** Развертывание Azure AD подключение на виртуальной машине в среде Azure для синхронизации учетных записей между локального каталога и клиента Azure AD подписки Office 365.</span><span class="sxs-lookup"><span data-stu-id="25da5-104">**Summary:** Deploy Azure AD Connect on a virtual machine in Azure to synchronize accounts between your on-premises directory and the Azure AD tenant of your Office 365 subscription.</span></span>
  
<span data-ttu-id="25da5-p101">Azure Active Directory (AD) подключение (ранее известных как средство синхронизации службы каталогов, средство синхронизации каталогов или средство DirSync.exe) — это на сервере, присоединенный к домену для установки приложения на стороне сервера для синхронизации локальной Windows Server Active Directory — пользователи к клиенту Azure Active Directory подписки Office 365. Подключение Azure AD можно установить на локальный сервер, но можно также установить его на виртуальную машину в Azure по следующим причинам:</span><span class="sxs-lookup"><span data-stu-id="25da5-p101">Azure Active Directory (AD) Connect (formerly known as the Directory Synchronization tool, Directory Sync tool, or the DirSync.exe tool) is a server-based application that you install on a domain-joined server to synchronize your on-premises Windows Server Active Directory users to the Azure Active Directory tenant of your Office 365 subscription. You can install Azure AD Connect on a on-premises server, but you can also install it on a virtual machine in Azure for the following reasons:</span></span>
  
- <span data-ttu-id="25da5-107">Вы можете быстрее подготовить и настроить облачные службы, чтобы сделать их доступными для пользователей.</span><span class="sxs-lookup"><span data-stu-id="25da5-107">You can provision and configure cloud-based servers faster, making the services available to your users sooner.</span></span>
    
- <span data-ttu-id="25da5-108">Azure предлагает обеспечения большей доступности сайта меньше усилий.</span><span class="sxs-lookup"><span data-stu-id="25da5-108">Azure offers better site availability with less effort.</span></span>
    
- <span data-ttu-id="25da5-109">Вы можете сократить количество локальных серверов в своей организации.</span><span class="sxs-lookup"><span data-stu-id="25da5-109">You can reduce the number of on-premises servers in your organization.</span></span>
    
> [!IMPORTANT]
> <span data-ttu-id="25da5-p102">В этом решении необходимо подключение между локальной сетью и виртуальные сети Azure. Дополнительные сведения можно [Подключить локальной сети для Microsoft Azure виртуальной сети](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span><span class="sxs-lookup"><span data-stu-id="25da5-p102">This solution requires connectivity between your on-premises network and your Azure Virtual Network. For more information, see [Connect an on-premises network to a Microsoft Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span></span> 
  
> [!IMPORTANT]
> <span data-ttu-id="25da5-p103">В этой статье описываются синхронизации из одного домена в одном лесу. Подключение Azure AD синхронизирует все Windows Server AD доменов в лесу Active Directory с Office 365. При наличии нескольких лесах Active Directory для синхронизации с Office 365, видеть [Нескольких лесов синхронизации каталога с помощью сценария единого входа](https://go.microsoft.com/fwlink/p/?LinkId=393091).</span><span class="sxs-lookup"><span data-stu-id="25da5-p103">This article describes synchronization of a single domain in a single forest. Azure AD Connect synchronizes all Windows Server AD domains in your Active Directory forest with Office 365. If you have multiple Active Directory forests to synchronize with Office 365, see [Multi-forest Directory Sync with Single Sign-On Scenario](https://go.microsoft.com/fwlink/p/?LinkId=393091).</span></span> 
  
> [!NOTE]
> <span data-ttu-id="25da5-p104">Office 365 с помощью Azure Active Directory (Azure AD) для его службы каталогов. Подписки Office 365 включает в себя клиента Azure AD. В этом клиента можно также для управления удостоверениями вашей организации с помощью других облачных рабочих нагрузок, включая других SaaS приложений и приложений в Azure.</span><span class="sxs-lookup"><span data-stu-id="25da5-p104">Office 365 uses Azure Active Directory (Azure AD) for its directory service. Your Office 365 subscription includes an Azure AD tenant. This tenant can also be used for management of your organization's identities with other cloud workloads, including other SaaS applications and apps in Azure.</span></span> 
  
## <a name="overview-of-deploying-office-365-directory-synchronization-in-azure"></a><span data-ttu-id="25da5-118">Общие сведения о развертывании синхронизации каталогов Office 365 в Azure</span><span class="sxs-lookup"><span data-stu-id="25da5-118">Overview of deploying Office 365 directory synchronization in Azure</span></span>
<span data-ttu-id="25da5-119"><a name="Overview"> </a></span><span class="sxs-lookup"><span data-stu-id="25da5-119"></span></span>

<span data-ttu-id="25da5-120">На следующей схеме показана Azure AD подключение, запущенные на виртуальную машину в Azure (сервер синхронизации каталогов), которая синхронизирует локального леса Windows Server AD собой 365 подписку.</span><span class="sxs-lookup"><span data-stu-id="25da5-120">The following diagram shows Azure AD Connect running on a virtual machine in Azure (the directory sync server) that synchronizes an on-premises Windows Server AD forest to anOffice 365 subscription.</span></span>
  
![Средство Azure AD Connect на виртуальной машине в Azure синхронизирует локальные учетные записи с клиентом Azure AD для Office 365](images/CP_DirSyncOverview.png)
  
<span data-ttu-id="25da5-p105">На схеме существует две сети, веб сайт VPN или ExpressRoute соединение. Существует в локальной сети, где расположены контроллеров домена Windows Server AD, и имеется виртуальная сеть Azure с сервер синхронизации каталогов, который является виртуальной машины под управлением [Подключить Azure AD](https://www.microsoft.com/download/details.aspx?id=47594). Существует два основных трафика потоки, поступающих от сервера синхронизации каталогов.</span><span class="sxs-lookup"><span data-stu-id="25da5-p105">In the diagram, there are two networks connected by a site-to-site VPN or ExpressRoute connection. There is an on-premises network where Windows Server AD domain controllers are located, and there is an Azure virtual network with a directory sync server, which is a virtual machine running [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594). There are two main traffic flows originating from the directory sync server:</span></span>
  
-  <span data-ttu-id="25da5-125"> Средство Azure AD Connect отправляет контроллеру домена в локальной сети запросы на изменение учетных записей и паролей.</span><span class="sxs-lookup"><span data-stu-id="25da5-125">Azure AD Connect queries a domain controller on the on-premises network for changes to accounts and passwords.</span></span>
    
-  <span data-ttu-id="25da5-p106">Подключение Azure AD отправляет изменения учетных записей и пароли в Azure AD экземпляр подписки Office 365. Поскольку сервер синхронизации каталогов в расширенной части в локальной сети, эти изменения, передаются через прокси-сервер в локальной сети.</span><span class="sxs-lookup"><span data-stu-id="25da5-p106">Azure AD Connect sends the changes to accounts and passwords to the Azure AD instance of your Office 365 subscription. Because the directory sync server is in an extended portion of your on-premises network, these changes are sent through the on-premises network's proxy server.</span></span>
    
> [!NOTE]
> <span data-ttu-id="25da5-p107">В этом решении описание синхронизации одного домена Active Directory, в одном лесу Active Directory. Подключение Azure AD синхронизирует все домены Active Directory в лес Active Directory с Office 365. При наличии нескольких лесах Active Directory для синхронизации с Office 365, видеть [Нескольких лесов синхронизации каталога с помощью сценария единого входа](https://go.microsoft.com/fwlink/p/?LinkId=393091).</span><span class="sxs-lookup"><span data-stu-id="25da5-p107">This solution describes synchronization of a single Active Directory domain, in a single Active Directory forest. Azure AD Connect synchronizes all Active Directory domains in your Active Directory forest with Office 365. If you have multiple Active Directory forests to synchronize with Office 365, see [Multi-forest Directory Sync with Single Sign-On Scenario](https://go.microsoft.com/fwlink/p/?LinkId=393091).</span></span> 
  
<span data-ttu-id="25da5-p108">В обоих случаях трафика с Azure AD подключение, работающим на виртуальная машина Azure будет переведен на шлюз виртуальной сети в Azure, который затем перенаправляет трафик через подключение через VPN или ExpressRoute веб сайта на устройство шлюза VPN на в локальной сети. Инфраструктуры маршрутизации в локальной сети нажмите перенаправляет трафик в место назначения, такие как контроллер домена или прокси-сервера.</span><span class="sxs-lookup"><span data-stu-id="25da5-p108">In both cases, the traffic originated by Azure AD Connect running on the Azure virtual machine is forwarded to a gateway on the virtual network in Azure, which then forwards the traffic across the site-to-site VPN or ExpressRoute connection to the VPN gateway device on the on-premises network. The routing infrastructure of the on-premises network then forwards the traffic to its destination, such as a domain controller or a proxy server.</span></span>
  
<span data-ttu-id="25da5-133">Развертывание этого решения делится на два основных этапа:</span><span class="sxs-lookup"><span data-stu-id="25da5-133">There are two major steps when you deploy this solution:</span></span>
  
1. <span data-ttu-id="25da5-p109">Создайте Azure виртуальной сети и веб сайта VPN-подключение к локальной сети. Дополнительные сведения можно [Подключить локальной сети для Microsoft Azure виртуальной сети](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span><span class="sxs-lookup"><span data-stu-id="25da5-p109">Create an Azure virtual network and establish a site-to-site VPN connection to your on-premises network. For more information, see [Connect an on-premises network to a Microsoft Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span></span>
    
2. <span data-ttu-id="25da5-p110">Установка [Azure AD подключение](https://www.microsoft.com/download/details.aspx?id=47594) на присоединенный к домену виртуальной машины в Azure, а затем синхронизировать Windows Server AD локальной в Office 365. Это включает в себя:</span><span class="sxs-lookup"><span data-stu-id="25da5-p110">Install [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594) on a domain-joined virtual machine in Azure, and then synchronize the on-premises Windows Server AD to Office 365. This involves:</span></span>
    
    <span data-ttu-id="25da5-138">Создание виртуальной машины Azure для запуска подключить Azure AD.</span><span class="sxs-lookup"><span data-stu-id="25da5-138">Creating an Azure Virtual Machine to run Azure AD Connect.</span></span>
    
    <span data-ttu-id="25da5-139">Установка и настройка [Подключить Azure AD](https://www.microsoft.com/download/details.aspx?id=47594).</span><span class="sxs-lookup"><span data-stu-id="25da5-139">Installing and configuring [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594).</span></span>
    
    <span data-ttu-id="25da5-p111">Настройка Azure AD подключения требуются учетные данные (имя пользователя и пароль) учетной записи администратора Azure AD и учетная запись администратора предприятия Windows Server AD. Подключение Azure AD выполняется немедленно и постоянно синхронизировать локального леса Windows Server AD в Office 365.</span><span class="sxs-lookup"><span data-stu-id="25da5-p111">Configuring Azure AD Connect requires the credentials (user name and password) of an Azure AD administrator account and a Windows Server AD enterprise administrator account. Azure AD Connect runs immediately and on an ongoing basis to synchronize the on-premises Windows Server AD forest to Office 365.</span></span>
    
<span data-ttu-id="25da5-142">Перед развертыванием этого решения в рабочей среде, используйте инструкции в [синхронизации службы каталогов для Office 365 dev/тестовой среды](dirsync-for-your-office-365-dev-test-environment.md) для настройки этой конфигурации как пробная версия, для демонстрации или для экспериментов.</span><span class="sxs-lookup"><span data-stu-id="25da5-142">Before you deploy this solution in production, use the instructions in [Directory synchronization for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md) to set this configuration up as a proof of concept, for demonstrations, or for experimentation.</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="25da5-143">После настройки средство Azure AD Connect не сохраняет учетные данные администратора предприятия Windows Server AD.</span><span class="sxs-lookup"><span data-stu-id="25da5-143">When Azure AD Connect configuration completes, it does not save the Windows Server AD enterprise administrator account credentials.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="25da5-p112">В этом решении описывается синхронизация одного леса Windows Server AD в Office 365. Топологии, описанные в этой статье представляет только один из способов внедрения такого решения. Топология организации могут различаться в зависимости от уникальные требования и рекомендации по безопасности.</span><span class="sxs-lookup"><span data-stu-id="25da5-p112">This solution describes synchronizing a single Windows Server AD forest to Office 365. The topology discussed in this article represents only one way to implement this solution. Your organization's topology might differ based on your unique network requirements and security considerations.</span></span> 
  
## <a name="plan-for-hosting-a-directory-sync-server-for-office-365-in-azure"></a><span data-ttu-id="25da5-147">Планирование размещения сервер синхронизации каталогов для Office 365 в Azure</span><span class="sxs-lookup"><span data-stu-id="25da5-147">Plan for hosting a directory sync server for Office 365 in Azure</span></span>
<span data-ttu-id="25da5-148"><a name="PlanningVirtual"> </a></span><span class="sxs-lookup"><span data-stu-id="25da5-148"></span></span>

### <a name="prerequisites"></a><span data-ttu-id="25da5-149">Необходимые условия</span><span class="sxs-lookup"><span data-stu-id="25da5-149">Prerequisites</span></span>

<span data-ttu-id="25da5-150">Прежде чем приступать к работе, изучите необходимые условия для этого решения.</span><span class="sxs-lookup"><span data-stu-id="25da5-150">Before you begin, review the following prerequisites for this solution:</span></span>
  
- <span data-ttu-id="25da5-151">Просмотрите соответствующий контент планирования в [Планирование Azure виртуальной сети](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#PlanningVirtual).</span><span class="sxs-lookup"><span data-stu-id="25da5-151">Review the related planning content in [Plan your Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#PlanningVirtual).</span></span>
    
- <span data-ttu-id="25da5-152">Убедитесь, что соблюдены все [необходимые компоненты](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#Prerequisites) для настройки виртуальная сеть Azure.</span><span class="sxs-lookup"><span data-stu-id="25da5-152">Ensure that you meet all [prerequisites](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#Prerequisites) for configuring the Azure virtual network.</span></span>
    
- <span data-ttu-id="25da5-p113">У подписки Office 365, которая включает в себя средство интеграции Active Directory. Сведения о подписках Office 365 перейдите на [страницу подписки Office 365](https://go.microsoft.com/fwlink/p/?LinkId=394278).</span><span class="sxs-lookup"><span data-stu-id="25da5-p113">Have an Office 365 subscription that includes the Active Directory integration feature. For information about Office 365 subscriptions, go to the [Office 365 subscription page](https://go.microsoft.com/fwlink/p/?LinkId=394278).</span></span>
    
- <span data-ttu-id="25da5-155">Подготовка одной виртуальной машины Azure, на котором выполняется Azure AD подключение для синхронизации локального леса Windows Server AD с Office 365.</span><span class="sxs-lookup"><span data-stu-id="25da5-155">Provision one Azure Virtual Machine that runs Azure AD Connect to synchronize your on-premises Windows Server AD forest with Office 365.</span></span>
    
    <span data-ttu-id="25da5-156">Необходимо иметь учетные данные (имена и пароли) для учетной записи администратора предприятия Windows Server AD и учетной записи администратора Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="25da5-156">You must have the credentials (names and passwords) for a Windows Server AD enterprise administrator account and an Azure Active Directory Administrator account.</span></span>
    
### <a name="solution-architecture-design-assumptions"></a><span data-ttu-id="25da5-157">Допущения по архитектуре решения</span><span class="sxs-lookup"><span data-stu-id="25da5-157">Solution architecture design assumptions</span></span>

<span data-ttu-id="25da5-158">Ниже приведены принятые проектные решения.</span><span class="sxs-lookup"><span data-stu-id="25da5-158">The following list describes the design choices made for this solution.</span></span>
  
- <span data-ttu-id="25da5-p114">Это решение использует один виртуальная сеть Azure с VPN-подключения веб сайта. Виртуальная сеть Azure служит для размещения одной подсети, которая содержит один сервер, сервер синхронизации каталогов, на котором выполняется подключение Azure AD.</span><span class="sxs-lookup"><span data-stu-id="25da5-p114">This solution uses a single Azure virtual network with a site-to-site VPN connection. The Azure virtual network hosts a single subnet that contains one server, the directory sync server that is running Azure AD Connect.</span></span> 
    
- <span data-ttu-id="25da5-161">В локальной сети размещены контроллер домена и DNS-серверы.</span><span class="sxs-lookup"><span data-stu-id="25da5-161">On the on-premises network, a domain controller and DNS servers exist.</span></span>
    
- <span data-ttu-id="25da5-p115">Подключение Azure AD выполняет хэш-функции синхронизации паролей вместо единого входа. Необходимо развернуть инфраструктуру служб федерации Active Directory (AD FS). Чтобы узнать больше о хэш-функции синхронизации паролей и параметры единого входа, обратитесь к разделу [определить, какие сценарии интеграции каталогов для использования](https://go.microsoft.com/fwlink/p/?LinkId=393094).</span><span class="sxs-lookup"><span data-stu-id="25da5-p115">Azure AD Connect performs password hash synchronization instead of single sign-on. You do not have to deploy an Active Directory Federation Services (AD FS) infrastructure. To learn more about password hash synchronization and single sign-on options, see [Determine which directory integration scenario to use](https://go.microsoft.com/fwlink/p/?LinkId=393094).</span></span>
    
<span data-ttu-id="25da5-p116">При развертывании этого решения в своей среде вы можете рассмотреть дополнительные варианты структуры. К ним относятся следующие:</span><span class="sxs-lookup"><span data-stu-id="25da5-p116">There are additional design choices that you might consider when you deploy this solution in your environment. These include the following:</span></span>
  
- <span data-ttu-id="25da5-167">Если существуют DNS-серверов в существующие Azure виртуальной сети, определяет, следует ли сервер синхронизации каталогов к их использования для разрешения имен, а не DNS-серверов в локальной сети.</span><span class="sxs-lookup"><span data-stu-id="25da5-167">If there are existing DNS servers in an existing Azure virtual network, determine whether you want your directory sync server to use them for name resolution instead of DNS servers on the on-premises network.</span></span>
    
- <span data-ttu-id="25da5-p117">Если в Azure виртуальной сети, контроллеры домена, определить, является ли Настройка Active Directory — сайты и службы может быть лучшим вариантом. Сервер синхронизации каталогов можно запросить контроллеры доменов в виртуальная сеть Azure для изменения в учетные записи и пароли, а не контроллеров домена в локальной сети.</span><span class="sxs-lookup"><span data-stu-id="25da5-p117">If there are domain controllers in an existing Azure virtual network, determine whether configuring Active Directory Sites and Services may be a better option for you. The directory sync server can query the domain controllers in the Azure virtual network for changes in accounts and passwords instead of domain controllers on the on-premises network.</span></span>
    
## <a name="deployment-roadmap"></a><span data-ttu-id="25da5-170">План развертывания</span><span class="sxs-lookup"><span data-stu-id="25da5-170">Deployment roadmap</span></span>
<span data-ttu-id="25da5-171"><a name="DeploymentRoadmap"> </a></span><span class="sxs-lookup"><span data-stu-id="25da5-171"></span></span>

<span data-ttu-id="25da5-172">Развертывание Azure AD подключение на виртуальную машину в Azure состоит из трех этапов:</span><span class="sxs-lookup"><span data-stu-id="25da5-172">Deploying Azure AD Connect on a virtual machine in Azure consists of three phases:</span></span>
  
- <span data-ttu-id="25da5-173">Этап 1. Создание и настройка виртуальной сети Azure</span><span class="sxs-lookup"><span data-stu-id="25da5-173">Phase 1: Create and configure the Azure virtual network</span></span>
    
- <span data-ttu-id="25da5-174">Этап 2. Создание и настройка виртуальной машины Azure</span><span class="sxs-lookup"><span data-stu-id="25da5-174">Phase 2: Create and configure the Azure virtual machine</span></span>
    
- <span data-ttu-id="25da5-175">Этап 3. Установка и настройка Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="25da5-175">Phase 3: Install and configure Azure AD Connect</span></span>
    
<span data-ttu-id="25da5-176">После развертывания также необходимо назначить расположения и лицензии для новых учетных записей пользователей в Office 365.</span><span class="sxs-lookup"><span data-stu-id="25da5-176">After deployment, you must also assign locations and licenses for the new user accounts in Office 365.</span></span>
  
> [!TIP]
> <span data-ttu-id="25da5-177">[Сервер синхронизации каталогов в Azure Deployment Kit](https://gallery.technet.microsoft.com/DirSync-Server-in-Azure-32cb2ded) содержит все блоки Azure PowerShell для создания этого решения, схемы в формат Microsoft PowerPoint и Visio и конфигурации книги Microsoft Excel, которое создает Azure блоки команды PowerShell, настроенный для настройки.</span><span class="sxs-lookup"><span data-stu-id="25da5-177">The [Directory Synchronization Server in Azure Deployment Kit](https://gallery.technet.microsoft.com/DirSync-Server-in-Azure-32cb2ded) contains all of the Azure PowerShell blocks to build out this solution, the diagrams in Microsoft PowerPoint and Visio format, and a Microsoft Excel configuration workbook that generates Azure PowerShell command blocks customized for your settings.</span></span>
  
### <a name="phase-1-create-and-configure-the-azure-virtual-network"></a><span data-ttu-id="25da5-178">Этап 1. Создание и настройка виртуальной сети Azure</span><span class="sxs-lookup"><span data-stu-id="25da5-178">Phase 1: Create and configure the Azure virtual network</span></span>

<span data-ttu-id="25da5-179">Для создания и настройки виртуальная сеть Azure, выполните [Этап 1: Подготовка локальной сетью](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#Phase1) и [Этап 2: Создание виртуальной сети между организациями в Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#Phase2) в развертывании схема [подключения локальной сети к Виртуальная сеть Microsoft Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span><span class="sxs-lookup"><span data-stu-id="25da5-179">To create and configure the Azure virtual network, complete [Phase 1: Prepare your on-premises network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#Phase1) and [Phase 2: Create the cross-premises virtual network in Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#Phase2) in the deployment roadmap of [Connect an on-premises network to a Microsoft Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span></span>
  
<span data-ttu-id="25da5-180">Ниже показана итоговая конфигурация.</span><span class="sxs-lookup"><span data-stu-id="25da5-180">This is your resulting configuration.</span></span>
  
![Этап 1 сервер синхронизации каталогов для Office 365, размещенных в Azure](images/aab6a9a4-eb78-4d85-9b96-711e6de420d7.png)
  
<span data-ttu-id="25da5-182">На этом рисунке показана локальная сеть, подключенная к виртуальной сети Azure через подключение VPN типа "сеть-сеть" или ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="25da5-182">This figure shows an on-premises network connected to an Azure virtual network through a site-to-site VPN or ExpressRoute connection.</span></span>
  
### <a name="phase-2-create-and-configure-the-azure-virtual-machine"></a><span data-ttu-id="25da5-183">Этап 2. Создание и настройка виртуальной машины Azure</span><span class="sxs-lookup"><span data-stu-id="25da5-183">Phase 2: Create and configure the Azure virtual machine</span></span>

<span data-ttu-id="25da5-p118">Создайте виртуальную машину в Azure с использованием инструкций [создать первый виртуальной машины для Windows Azure портала](https://go.microsoft.com/fwlink/p/?LinkId=393098). Используйте следующие параметры:</span><span class="sxs-lookup"><span data-stu-id="25da5-p118">Create the virtual machine in Azure using the instructions [Create your first Windows virtual machine in the Azure portal](https://go.microsoft.com/fwlink/p/?LinkId=393098). Use the following settings:</span></span>
  
- <span data-ttu-id="25da5-p119">В области **основы** выберите ту же группу подписки, расположение и ресурсов как виртуальной сети. Запишите имя пользователя и пароль в надежном месте. Они потребуются позднее, чтобы подключиться к виртуальной машине.</span><span class="sxs-lookup"><span data-stu-id="25da5-p119">On the **Basics** pane, select the same subscription, location, and resource group as your virtual network. Record the user name and password in a secure location. You will need these later to connect to the virtual machine.</span></span>
    
- <span data-ttu-id="25da5-189">В области **выберите размер** выберите команду **A2 стандартный** размер.</span><span class="sxs-lookup"><span data-stu-id="25da5-189">On the **Choose a size** pane, choose the **A2 Standard** size.</span></span>
    
- <span data-ttu-id="25da5-p120">В области **Параметры** в разделе **хранения** выберите **стандартный** тип хранилища. В разделе **сети** выберите имя виртуальной сети и подсети для размещения сервера синхронизации каталогов (не GatewaySubnet). Всех остальных параметров оставьте значения по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="25da5-p120">On the **Settings** pane, in the **Storage** section, select the **Standard** storage type. In the **Network** section, select the name of your virtual network and the subnet for hosting the directory sync server (not the GatewaySubnet). Leave all other settings at their default values.</span></span>
    
<span data-ttu-id="25da5-193">Убедитесь, что сервер синхронизации каталогов использует DNS правильно, проверьте внутренней DNS для убедитесь в том, что запись адреса (A) была добавлена для виртуальной машины с IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="25da5-193">Verify that your directory sync server is using DNS correctly by checking your internal DNS to make sure that an Address (A) record was added for the virtual machine with its IP address.</span></span> 
  
<span data-ttu-id="25da5-p121">Используйте инструкции из статьи [подключение к виртуальной машине и входа на](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-hero-tutorial?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json#connect-to-the-virtual-machine-and-sign-on) подключение к серверу синхронизации каталогов с помощью подключения к удаленному рабочему столу. После входа в присоединиться к виртуальной машины Windows Server AD в локальный домен.</span><span class="sxs-lookup"><span data-stu-id="25da5-p121">Use the instructions in [Connect to the virtual machine and sign on](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-hero-tutorial?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json#connect-to-the-virtual-machine-and-sign-on) to connect to the directory sync server with a Remote Desktop Connection. After signing in, join the virtual machine to the on-premises Windows Server AD domain.</span></span>
  
<span data-ttu-id="25da5-p122">Для подключения Azure AD для получения доступа к ресурсам Интернета необходимо настроить сервер синхронизации каталогов для использования прокси-сервера в локальной сети. Следует обратитесь к администратору сети для дополнительных действий по настройке для выполнения.</span><span class="sxs-lookup"><span data-stu-id="25da5-p122">For Azure AD Connect to gain access to Internet resources, you must configure the directory sync server to use the on-premises network's proxy server. You should contact your network administrator for any additional configuration steps to perform.</span></span>
  
<span data-ttu-id="25da5-198">Ниже показана итоговая конфигурация.</span><span class="sxs-lookup"><span data-stu-id="25da5-198">This is your resulting configuration.</span></span>
  
![Этап 2 сервер синхронизации каталогов для Office 365, размещенных в Azure](images/9d8c9349-a207-4828-9b2b-826fe9c06af3.png)
  
<span data-ttu-id="25da5-200">На этом рисунке показана виртуальной машины сервер синхронизации каталогов в нескольких организациях виртуальная сеть Azure.</span><span class="sxs-lookup"><span data-stu-id="25da5-200">This figure shows the directory sync server virtual machine in the cross-premises Azure virtual network.</span></span>
  
### <a name="phase-3-install-and-configure-azure-ad-connect"></a><span data-ttu-id="25da5-201">Этап 3. Установка и настройка Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="25da5-201">Phase 3: Install and configure Azure AD Connect</span></span>

<span data-ttu-id="25da5-202">Выполните следующие действия:</span><span class="sxs-lookup"><span data-stu-id="25da5-202">Complete the following procedure:</span></span>
  
1. <span data-ttu-id="25da5-p123">Подключение к серверу синхронизации каталогов с помощью подключения к удаленному рабочему столу с учетной записью домена Windows Server AD с правами локального администратора. В разделе [подключение к виртуальной машине и входа в систему](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-hero-tutorial?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json#connect-to-the-virtual-machine-and-sign-on).</span><span class="sxs-lookup"><span data-stu-id="25da5-p123">Connect to the directory sync server using a Remote Desktop Connection with a Windows Server AD domain account that has local administrator privileges. See [Connect to the virtual machine and sign on](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-hero-tutorial?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json#connect-to-the-virtual-machine-and-sign-on).</span></span>
    
2. <span data-ttu-id="25da5-205">Сервер синхронизации каталогов откройте в статье [Настройка синхронизации службы каталогов в Office 365](https://support.office.com/article/Set-up-directory-synchronization-in-Office-365-1b3b5318-6977-42ed-b5c7-96fa74b08846) и следуйте инструкциям для синхронизации службы каталогов с помощью хэш-функции синхронизации паролей.</span><span class="sxs-lookup"><span data-stu-id="25da5-205">From the directory sync server, open the [Set up directory synchronization in Office 365](https://support.office.com/article/Set-up-directory-synchronization-in-Office-365-1b3b5318-6977-42ed-b5c7-96fa74b08846) article and follow the directions for directory synchronization with password hash synchronization.</span></span>
    
> [!CAUTION]
> <span data-ttu-id="25da5-p124">Программа установки создает учетную запись **AAD_xxxxxxxxxxxx** в локальные пользователи подразделение (OU). Не перемещать и удалить эту учетную запись или синхронизации завершится с ошибкой.</span><span class="sxs-lookup"><span data-stu-id="25da5-p124">Setup creates the **AAD_xxxxxxxxxxxx** account in the Local Users organizational unit (OU). Do not move or remove this account or synchronization will fail.</span></span>
  
<span data-ttu-id="25da5-208">Ниже показана итоговая конфигурация.</span><span class="sxs-lookup"><span data-stu-id="25da5-208">This is your resulting configuration.</span></span>
  
![Этап 3 сервера синхронизации каталогов для Office 365, размещенных в Azure](images/3f692b62-b77c-4877-abee-83c7edffa922.png)
  
<span data-ttu-id="25da5-210">На этом рисунке показана сервер синхронизации каталогов с Azure AD подключение в нескольких организациях виртуальная сеть Azure.</span><span class="sxs-lookup"><span data-stu-id="25da5-210">This figure shows the directory sync server with Azure AD Connect in the cross-premises Azure virtual network.</span></span>
  
### <a name="assign-locations-and-licenses-to-users-in-office-365"></a><span data-ttu-id="25da5-211">Назначение расположений и лицензий пользователям в Office 365</span><span class="sxs-lookup"><span data-stu-id="25da5-211">Assign locations and licenses to users in Office 365</span></span>

<span data-ttu-id="25da5-p125">Средство Azure AD Connect добавляет учетные записи из локального леса Windows Server AD в подписку на Office 365, но чтобы пользователи могли входить в Office 365 и использовать службы, необходимо настроить расположение и лицензии. Чтобы добавить расположение и активировать лицензии для соответствующих учетных записей пользователей, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="25da5-p125">Azure AD Connect adds accounts to your Office 365 subscription from the on-premises Windows Server AD, but in order for users to sign in to Office 365 and use its services, the accounts must configured with a location and licenses. Use these steps to add the location and activate licenses for the appropriate user accounts:</span></span>
  
1. <span data-ttu-id="25da5-214">Вход на [странице портала Office 365](https://portal.office.com)и нажмите кнопку **администрирования**.</span><span class="sxs-lookup"><span data-stu-id="25da5-214">Sign in to the [Office 365 portal page](https://portal.office.com), and then click **Admin**.</span></span>
    
2. <span data-ttu-id="25da5-215">На панели навигации слева выберите элементы **Пользователи > Активные пользователи**.</span><span class="sxs-lookup"><span data-stu-id="25da5-215">In the left navigation, click **Users > Active users**.</span></span>
    
3. <span data-ttu-id="25da5-216">В списке учетных записей пользователей установите флажок рядом с нужным пользователем.</span><span class="sxs-lookup"><span data-stu-id="25da5-216">In the list of user accounts, select the check box next to the user you want to activate.</span></span>
    
4. <span data-ttu-id="25da5-217">На странице для пользователя нажмите кнопку **Изменить** для **лицензий на продукт**.</span><span class="sxs-lookup"><span data-stu-id="25da5-217">On the page for the user, click **Edit** for **Product licenses**.</span></span>
    
5. <span data-ttu-id="25da5-218">На странице " **число лицензий на продукт** " выберите расположение для пользователя для **расположения**и включите соответствующие лицензии для пользователя.</span><span class="sxs-lookup"><span data-stu-id="25da5-218">On the **Product licences** page, select a location for the user for **Location**, and then enable the appropriate licences for the user.</span></span>
    
6. <span data-ttu-id="25da5-219">Закончив настройку, нажмите кнопку **Сохранить**и дважды нажмите кнопку **Закрыть** .</span><span class="sxs-lookup"><span data-stu-id="25da5-219">When complete, click **Save**, and then click **Close** twice.</span></span>
    
7. <span data-ttu-id="25da5-220">Вернитесь к шагу 3, чтобы повторить эти действия для других пользователей.</span><span class="sxs-lookup"><span data-stu-id="25da5-220">Go back to step 3 for additional users.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="25da5-221">См. также</span><span class="sxs-lookup"><span data-stu-id="25da5-221">See Also</span></span>

<span data-ttu-id="25da5-222"><a name="DeploymentRoadmap"> </a></span><span class="sxs-lookup"><span data-stu-id="25da5-222"></span></span>

[<span data-ttu-id="25da5-223">Освоение облака и гибридные решения</span><span class="sxs-lookup"><span data-stu-id="25da5-223">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
  
[<span data-ttu-id="25da5-224">Подключение локальной сети к виртуальной сети Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="25da5-224">Connect an on-premises network to a Microsoft Azure virtual network</span></span>](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)

[<span data-ttu-id="25da5-225">Подключение загрузки Azure AD</span><span class="sxs-lookup"><span data-stu-id="25da5-225">Download Azure AD Connect</span></span>](https://www.microsoft.com/download/details.aspx?id=47594)
  
[<span data-ttu-id="25da5-226">Настройка синхронизации службы каталогов в Office 365</span><span class="sxs-lookup"><span data-stu-id="25da5-226">Set up directory synchronization in Office 365</span></span>](https://support.office.com/article/Set-up-directory-synchronization-in-Office-365-1b3b5318-6977-42ed-b5c7-96fa74b08846)
  
[<span data-ttu-id="25da5-227">Сервер синхронизации каталогов в Azure Deployment Kit</span><span class="sxs-lookup"><span data-stu-id="25da5-227">Directory Synchronization server in Azure Deployment Kit</span></span>](https://gallery.technet.microsoft.com/DirSync-Server-in-Azure-32cb2ded)



