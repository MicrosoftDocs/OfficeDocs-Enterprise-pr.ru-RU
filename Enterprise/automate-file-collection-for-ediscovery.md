---
title: Автоматизация сбора файлов для обнаружения электронных данных
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom: ''
ms.assetid: 8d751419-d81b-4eb7-a2e5-8b03ccbf670c
search.appverid:
- MET150
description: Сводка. Узнайте, как автоматизировать сбор файлов с компьютеров пользователей для обнаружения электронных данных.
ms.openlocfilehash: 83bd55ff786803cfcb3eec9430d72de30179d000
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "44997980"
---
# <a name="automate-file-collection-for-ediscovery"></a><span data-ttu-id="bb6e2-103">Автоматизация сбора файлов для обнаружения электронных данных</span><span class="sxs-lookup"><span data-stu-id="bb6e2-103">Automate file collection for eDiscovery</span></span>

<span data-ttu-id="bb6e2-p101">Ни одна компания не застрахована от судебных исков. Несмотря на то что юридические отделы стараются снизить этот риск, судебные разбирательства  неизбежная реальность бизнеса. Когда против компании начинается судебное разбирательство, она обязана предоставить суду и адвокату противной стороны все необходимые документы.</span><span class="sxs-lookup"><span data-stu-id="bb6e2-p101">All companies face the potential of lawsuits or other types of legal action. While legal departments work to reduce that exposure, litigation is a fact of business life. When a company faces legal action, they are required, through the process of legal discovery, to provide all relevant documentary materials to the court and to opposing counsel.</span></span> 
  
<span data-ttu-id="bb6e2-p102">Обнаружение электронных данных  это процесс, который компании используют для инвентаризации, поиска, идентификации, сохранения, фильтрации и предоставления необходимых электронных документов. В SharePoint 2013, Exchange Server 2013, Lync Server 2013, SharePoint Online и Exchange Online можно хранить большое количество документов. В зависимости от версии эти продукты могут поддерживать eDiscovery и хранение на месте (Lync через Exchange Server), что позволяет юридическим отделам легко индексировать, идентифицировать, хранить и фильтровать материалы по тому или иному делу.</span><span class="sxs-lookup"><span data-stu-id="bb6e2-p102">eDiscovery is the process by which companies inventory, search, identify, preserve, filter, and make available the relevant documentary materials that exist in electronic form. SharePoint 2013, Exchange Server 2013, Lync Server 2013, SharePoint Online, and Exchange Online can hold large amounts of documentary content. Depending on the version, these products may support eDiscovery and in place holds (Lync via Exchange Server), making it easier for the legal teams to index, identify, hold, and filter the most relevant content for a given case.</span></span>
  
<span data-ttu-id="bb6e2-p103">Многие документы хранятся на локальных компьютерах пользователей (хранителей), а не в одной папке. В этом случае поиск данных в SharePoint 2013 практически невозможен. Следовательно, их невозможно включить в eDiscovery. В этом решении показано, как использовать сценарии входа, System Center Orchestrator 2012 R2 и Windows PowerShell, чтобы автоматизировать идентификацию и сбор документов с компьютеров пользователей в Exchange Server.</span><span class="sxs-lookup"><span data-stu-id="bb6e2-p103">Many documents are stored on users' (Custodians) local computers, not in a centralized location. This makes it essentially impossible for SharePoint 2013 to search, and if it can't be searched, it can't be included in eDiscovery. This solution shows you how to use logon scripts, System Center Orchestrator 2012 R2 and Windows PowerShell for Exchange Server to automate the identification and collection of documentary materials from users' computers.</span></span>
  
## <a name="what-this-solution-does"></a><span data-ttu-id="bb6e2-113">Принцип работы решения</span><span class="sxs-lookup"><span data-stu-id="bb6e2-113">What this solution does</span></span>

<span data-ttu-id="bb6e2-p104">В этом решении используются глобальная группа безопасности, групповая политика и сценарий Windows PowerShell для поиска содержимого и PST-файлов Outlook на локальных компьютерах пользователей, их инвентаризации и сбора в скрытую общую папку. Оттуда PST-файлы можно импортировать в Exchange Server 2013 или Exchange Online. После этого все файлы перемещаются с помощью модуля Runbook System Center Orchestrator 2012 R2 в другую общую папку в Microsoft Azure для долгосрочного хранения и индексации с помощью SharePoint 2013. Затем вы можете использовать центры eDiscovery в локальном развертывании SharePoint 2013 или SharePoint Online, как при обычном поиске eDiscovery.</span><span class="sxs-lookup"><span data-stu-id="bb6e2-p104">This solution uses a global security group, Group Policy, and a Windows PowerShell script to locate, inventory, and collect content and Outlook personal store (PST) files from users local computers to a hidden file share. From there, the PST files can be imported into either Exchange Server 2013 or Exchange Online. All files are then moved using a System Center Orchestrator 2012 R2 runbook to another file share in Microsoft Azure for long-term storage and indexing by SharePoint 2013. You then use eDiscovery centers in your on-premises SharePoint 2013 deployment or in SharePoint Online as you regularly would to perform eDiscovery.</span></span> 
  
> [!IMPORTANT]
> <span data-ttu-id="bb6e2-p105">В этом решении файлы копируются с компьютеров хранителей в одну общую папку с помощью операции Robocopy. Операция Robocopy не копирует открытые или заблокированные файлы, поэтому все открытые файлы, в том числе PST-файлы, не будут собраны. Их потребуется собрать вручную. В этом решении не создается список файлов, которые не удалось скопировать, с полными путями к каждому файлу.</span><span class="sxs-lookup"><span data-stu-id="bb6e2-p105">This solution uses robocopy to copy files from custodian's computers to a centralized file share. Because robocopy does not copy files that are open or locked, any files, including PST files, that the custodian has open will not be collected. You will have to collect them manually. This solution does provide you with a list that explicitly identifies the files it cannot copy and the full path to each file.</span></span> 
  
<span data-ttu-id="bb6e2-122">На следующей схеме подробно рассмотрены все этапы и элементы решения.</span><span class="sxs-lookup"><span data-stu-id="bb6e2-122">The following diagram walks you through all the steps and elements of the solution.</span></span>
  
![Обзор решения для автоматического сбора файлов](media/dbb447b5-c74c-4956-986c-10a1d047ac99.png)
  
|<span data-ttu-id="bb6e2-124">\*\*\*\*Условные обозначения\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="bb6e2-124">\*\*\*\*Legend\*\*\*\*</span></span>||
|:-----|:-----|
|![выноска пурпурного цвета 1](media/000026a3-2bf0-4678-b468-ccb5f81da6f1.png)|<span data-ttu-id="bb6e2-126">Создайте объект групповой политики (GPO) и свяжите его со сценарием входа для сбора данных.</span><span class="sxs-lookup"><span data-stu-id="bb6e2-126">Create a Group Policy object (GPO), and associate it with the collection logon script.</span></span>  <br/> |
|![выноска пурпурного цвета 2](media/a31b11e2-3597-42a4-933e-b6af11ed6ef1.png)| <span data-ttu-id="bb6e2-128">Настройте фильтр безопасности GPO, чтобы применять объект групповой политики только к группе Custodians.</span><span class="sxs-lookup"><span data-stu-id="bb6e2-128">Configure the GPO security filter to apply the GPO only to the Custodians group.</span></span> <br/> |
|![выноска пурпурного цвета 3](media/3ced060c-daec-460d-a9b5-260a3dfcae36.png)|<span data-ttu-id="bb6e2-130">Хранитель входит в систему, после чего запускается GPO, вызывая сценарий входа для сбора данных.</span><span class="sxs-lookup"><span data-stu-id="bb6e2-130">A Custodian logs on and the GPO runs, calling the collection logon script.</span></span>  <br/> |
|![выноска пурпурного цвета 4](media/6f269d84-2559-49e3-b18e-af6ac94d0419.png)|<span data-ttu-id="bb6e2-132">Сценарий входа для сбора данных проводит инвентаризацию всех локально подключенных дисков на компьютере хранителя, ищет нужные файлы и записывает их расположение.</span><span class="sxs-lookup"><span data-stu-id="bb6e2-132">The collection logon script inventories all locally attached drives on the Custodians computer, searching for the files you want, and recording their location.</span></span>  <br/> |
|![выноска пурпурного цвета 5](media/4bf8898c-44ad-4524-b983-70175804eb85.png)|<span data-ttu-id="bb6e2-134">Сценарий входа для сбора данных копирует файлы, инвентаризация которых проведена, в скрытый файловый ресурс на промежуточном сервере.</span><span class="sxs-lookup"><span data-stu-id="bb6e2-134">The collection logon script copies the inventoried files to a hidden file share on the staging server.</span></span>  <br/> |
|![выноска пурпурного цвета 6](media/99589726-0c7e-406b-a276-44301a135768.png)| <span data-ttu-id="bb6e2-136">(Вариант А) Вручную запустите сценарий импорта PST-файлов, чтобы импортировать собранные PST-файлы в Exchange Server 2013.</span><span class="sxs-lookup"><span data-stu-id="bb6e2-136">(Option A) Manually run the PST import script to import the collected PST files into Exchange Server 2013.</span></span> <br/> |
|![выноска пурпурного цвета 7](media/ff15e89c-d2fd-4614-9838-5e18287d578b.png)|<span data-ttu-id="bb6e2-138">(Вариант б) С помощью средства и процесса импорта Microsoft 365 импортируйте собранные PST-файлы в Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="bb6e2-138">(Option B) Using the Microsoft 365 Import tool and process, import the collected PST files into Exchange Online.</span></span>  <br/> |
|![выноска пурпурного цвета 8](media/aaf3bd3d-9508-4aaf-a3af-44ba501da63a.png)|<span data-ttu-id="bb6e2-140">Переместите все собранные файлы в общую папку Azure для долгосрочного хранения с помощью модуля Runbook MoveToColdStorageSystem Center Orchestrator 2012 R2.</span><span class="sxs-lookup"><span data-stu-id="bb6e2-140">Move all collected files to an Azure file share for long term storage with the MoveToColdStorage System Center Orchestrator 2012 R2 runbook.</span></span> <br/> |
|![выноска пурпурного цвета 9](media/b354642e-445e-4723-a84a-b41f7ac6e774.png)|<span data-ttu-id="bb6e2-142">Индексируйте файлы в файловом ресурсе "холодного" хранилища с помощью SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="bb6e2-142">Index the files in the cold storage file share with SharePoint 2013.</span></span>  <br/> |
|![выноска пурпурного цвета 10](media/cebf7de5-7525-413b-9e52-638a4f8b2f74.png)|<span data-ttu-id="bb6e2-144">Выполните eDiscovery для контента в "холодном" хранилище и на локальном сервере Exchange Server 2013.</span><span class="sxs-lookup"><span data-stu-id="bb6e2-144">Perform eDiscovery on content in cold storage and in the on-premises Exchange Server 2013.</span></span>  <br/> |
|![выноска пурпурного цвета 11](media/e59ab403-2f19-497a-92a5-549846dded66.png)|<span data-ttu-id="bb6e2-146">Выполните обнаружение электронных данных для содержимого в Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="bb6e2-146">Perform eDiscovery on content in Microsoft 365.</span></span>  <br/> |
   
## <a name="prerequisites"></a><span data-ttu-id="bb6e2-147">Предварительные условия</span><span class="sxs-lookup"><span data-stu-id="bb6e2-147">Prerequisites</span></span>

<span data-ttu-id="bb6e2-p106">Для настройки этого решения требуется ряд элементов, большинство из которых должны быть установлены и настроены, если вы планируете использовать eDiscovery. Мы предоставим вам ссылки на элементы, которые отсутствуют или требуют специальной настройки, чтобы вы смогли создать базовую конфигурацию. Базовая конфигурация должна быть готова до настройки самого решения.</span><span class="sxs-lookup"><span data-stu-id="bb6e2-p106">The configuration of this solution requires many elements, most of which you likely have in place and configured if you're thinking about eDiscovery. For the elements that you may not have or ones that require a specific configuration, we'll provide you with the links you need build out your base configuration. You must have the base configuration in place before you configure the solution itself.</span></span>
  
### <a name="base-configuration"></a><span data-ttu-id="bb6e2-151">Базовая настройка</span><span class="sxs-lookup"><span data-stu-id="bb6e2-151">Base configuration</span></span>

|<span data-ttu-id="bb6e2-152">**Элемент**</span><span class="sxs-lookup"><span data-stu-id="bb6e2-152">**Element**</span></span>|<span data-ttu-id="bb6e2-153">**Ссылка**</span><span class="sxs-lookup"><span data-stu-id="bb6e2-153">**Link**</span></span>|
|:-----|:-----|
|<span data-ttu-id="bb6e2-154">Домен Доменные службы Active Directory</span><span class="sxs-lookup"><span data-stu-id="bb6e2-154">Active Directory Domain Services (AD DS) domain</span></span>  <br/> ||
|<span data-ttu-id="bb6e2-155">Подключение к Интернету из локальной сети</span><span class="sxs-lookup"><span data-stu-id="bb6e2-155">Internet connectivity from your on-premises network</span></span>  <br/> ||
|<span data-ttu-id="bb6e2-156">SQL Server 2012 для поддержки SharePoint 2013 и System Center Orchestrator 2012 R2</span><span class="sxs-lookup"><span data-stu-id="bb6e2-156">SQL Server 2012 to support SharePoint 2013 and System Center Orchestrator 2012 R2</span></span>  <br/> |[<span data-ttu-id="bb6e2-157">Развертывание System Center Orchestrator 2012</span><span class="sxs-lookup"><span data-stu-id="bb6e2-157">Deploying System Center Orchestrator - 2012</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=613503) <br/> |
| <span data-ttu-id="bb6e2-158">SharePoint 2013 в локальной среде или на основе Azure для eDiscovery (необходимо для варианта А)</span><span class="sxs-lookup"><span data-stu-id="bb6e2-158">On-premises or Azure based SharePoint 2013 for eDiscovery (required for Option A)</span></span> <br/> ||
|<span data-ttu-id="bb6e2-159">Локальный серверный файловый ресурс для промежуточного хранения</span><span class="sxs-lookup"><span data-stu-id="bb6e2-159">On-premises file share server for staging</span></span>  <br/> ||
|<span data-ttu-id="bb6e2-160">Локальный Exchange Server 2013 для импорта PST-файлов при использовании варианта А</span><span class="sxs-lookup"><span data-stu-id="bb6e2-160">On-premises Exchange Server 2013 for Option A PST import</span></span>  <br/> |<span data-ttu-id="bb6e2-161">Накопительный пакет обновления 5 (15.913.22) доступен на [этой странице](https://go.microsoft.com/fwlink/p/?LinkId=613426).</span><span class="sxs-lookup"><span data-stu-id="bb6e2-161">CU5 (15.913.22) is available at [CU5](https://go.microsoft.com/fwlink/p/?LinkId=613426).</span></span>  <br/> |
|<span data-ttu-id="bb6e2-162">System Center Orchestrator 2012 R2</span><span class="sxs-lookup"><span data-stu-id="bb6e2-162">System Center Orchestrator 2012 R2</span></span>  <br/> |[<span data-ttu-id="bb6e2-163">Развертывание System Center Orchestrator 2012</span><span class="sxs-lookup"><span data-stu-id="bb6e2-163">Deploying System Center Orchestrator - 2012</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=613503) <br/> |
|<span data-ttu-id="bb6e2-164">Microsoft 365 E3 с Exchange Online и SharePoint Online (необходимо для варианта б)</span><span class="sxs-lookup"><span data-stu-id="bb6e2-164">Microsoft 365 E3 with Exchange Online and SharePoint Online (required for Option B)</span></span>  <br/> |<span data-ttu-id="bb6e2-165">Чтобы зарегистрировать подписку на Microsoft 365 E3, ознакомьтесь с [подпиской microsoft 365 E3](https://www.microsoft.com/microsoft-365/enterprise-e3-business-software?activetab=pivot%3aoverviewtab).</span><span class="sxs-lookup"><span data-stu-id="bb6e2-165">To sign up for a Microsoft 365 E3 subscription, see [Microsoft 365 E3 subscription](https://www.microsoft.com/microsoft-365/enterprise-e3-business-software?activetab=pivot%3aoverviewtab).</span></span>  <br/> |
|<span data-ttu-id="bb6e2-166">Подписка на Azure с виртуальной машиной</span><span class="sxs-lookup"><span data-stu-id="bb6e2-166">Azure subscription with a virtual machine</span></span>  <br/> |<span data-ttu-id="bb6e2-167">Сведения о подписке на Azure см. на странице [подписки на Microsoft Azure](https://go.microsoft.com/fwlink/p/?LinkId=512010).</span><span class="sxs-lookup"><span data-stu-id="bb6e2-167">To sign up for a Azure, see [Subscribe to Windows Azure](https://go.microsoft.com/fwlink/p/?LinkId=512010)</span></span> <br/> |
|<span data-ttu-id="bb6e2-168">VPN-подключение между локальной сетью и подпиской Azure</span><span class="sxs-lookup"><span data-stu-id="bb6e2-168">A VPN connection between your on-premises network and your Azure subscription</span></span>  <br/> |<span data-ttu-id="bb6e2-169">Сведения о настройке туннеля VPN между службой Azure, предоставляемой по подписке, и локальной сетью см. в статье [Подключение локальной сети к виртуальной сети Microsoft Azure](https://go.microsoft.com/fwlink/p/?LinkId=613507).</span><span class="sxs-lookup"><span data-stu-id="bb6e2-169">To set up a VPN tunnel between your Azure subscription and your on-premises network, see [Connect an on-premises network to a Microsoft Azure virtual network](https://go.microsoft.com/fwlink/p/?LinkId=613507).</span></span>  <br/> |
|<span data-ttu-id="bb6e2-170">SharePoint 2013eDiscovery, настроенное на поиск в SharePoint и Exchange Server 2013, а также (необязательно) Lync Server 2013</span><span class="sxs-lookup"><span data-stu-id="bb6e2-170">SharePoint 2013 eDiscovery configured to search across SharePoint and Exchange Server 2013 and optionally Lync Server 2013</span></span>  <br/> |<span data-ttu-id="bb6e2-171">Сведения о том, как настроить обнаружение электронных данных таким образом, см. в статье [Настройка обнаружения электронных данных в SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=613508) и[руководстве по настройке обнаружения электронных данных для лаборатории тестирования общих папок Exchange, Lync, SharePoint и Windows](https://go.microsoft.com/fwlink/p/?LinkId=393130).  </span><span class="sxs-lookup"><span data-stu-id="bb6e2-171">To configure eDiscovery in this fashion, see [Configure eDiscovery in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=613508) and[Test Lab Guide: Configure eDiscovery for an Exchange, Lync, SharePoint and Windows File Shares Test Lab](https://go.microsoft.com/fwlink/p/?LinkId=393130).</span></span>  <br/> |
|<span data-ttu-id="bb6e2-172">Обнаружение электронных данных в Microsoft 365 для SharePoint Online и Exchange Online</span><span class="sxs-lookup"><span data-stu-id="bb6e2-172">eDiscovery in Microsoft 365 for SharePoint Online and Exchange Online</span></span>  <br/> |<span data-ttu-id="bb6e2-173">Чтобы настроить обнаружение электронных данных в Microsoft 365, ознакомьтесь со статьей [Настройка центра обнаружения электронных данных в SharePoint Online](https://go.microsoft.com/fwlink/p/?LinkId=613628).</span><span class="sxs-lookup"><span data-stu-id="bb6e2-173">To configure eDiscovery in Microsoft 365, see [Set up an eDiscovery Center in SharePoint Online](https://go.microsoft.com/fwlink/p/?LinkId=613628).</span></span>  <br/> |
   
## <a name="configure-the-environment"></a><span data-ttu-id="bb6e2-174">Настройка среды</span><span class="sxs-lookup"><span data-stu-id="bb6e2-174">Configure the environment</span></span>

<span data-ttu-id="bb6e2-175">Теперь, когда базовая конфигурация готова, вы можете перейти к настройке самого решения.</span><span class="sxs-lookup"><span data-stu-id="bb6e2-175">Now that you have the base configuration in place, you can move ahead to configuring the solution itself.</span></span> 
  
### <a name="staging-file-share"></a><span data-ttu-id="bb6e2-176">Подготовка общей папки для промежуточного хранения</span><span class="sxs-lookup"><span data-stu-id="bb6e2-176">Staging file share</span></span>

1. <span data-ttu-id="bb6e2-177">Создайте на локальном домене глобальную группу безопасности Custodians.</span><span class="sxs-lookup"><span data-stu-id="bb6e2-177">In the on-premises domain, create a global security group named Custodians.</span></span>
    
2. <span data-ttu-id="bb6e2-p107">Создайте скрытую общую папку для файлов, собираемых с компьютеров хранителей. Она должна находиться на локальном сервере. Например, на сервере Staging создайте общую папку Cases$. Символ **$** необходим для того, чтобы сделать эту папку скрытой.</span><span class="sxs-lookup"><span data-stu-id="bb6e2-p107">Create a hidden file share for the files that are collected from Custodians computers. This should be on an on-premises server. For example, on a server called Staging, create a file share called Cases$. The **$** is required to make this a hidden share.</span></span>
    
3. <span data-ttu-id="bb6e2-182">Задайте следующие разрешения для общей папки:</span><span class="sxs-lookup"><span data-stu-id="bb6e2-182">Set the following share permissions:</span></span>
    
  - <span data-ttu-id="bb6e2-183">Хранители: "Изменение", "Чтение"</span><span class="sxs-lookup"><span data-stu-id="bb6e2-183">Custodians: Change, Read</span></span>
    
  - <span data-ttu-id="bb6e2-184">Администраторы: полный доступ</span><span class="sxs-lookup"><span data-stu-id="bb6e2-184">Administrators: Full Control</span></span>
    
  - <span data-ttu-id="bb6e2-185">Доверенная подсистема Exchange: "Изменение", "Чтение"</span><span class="sxs-lookup"><span data-stu-id="bb6e2-185">Exchange Trusted Subsystem: Change, Read</span></span>
    
4. <span data-ttu-id="bb6e2-p108">Откройте вкладку **Безопасность**, добавьте группу Custodians и нажмите кнопку **Дополнительно**. Для группы Custodians задайте следующие разрешения:</span><span class="sxs-lookup"><span data-stu-id="bb6e2-p108">Open the **Security** tab, add the Custodians group, and click **Advanced**. Set the following permissions for the Custodians group:</span></span>
    
  - <span data-ttu-id="bb6e2-188">**Тип: Deny**</span><span class="sxs-lookup"><span data-stu-id="bb6e2-188">**Type: Deny**</span></span>
    
  - <span data-ttu-id="bb6e2-189">**Применимо к: "Для этой папки, ее подпапок и файлов"**</span><span class="sxs-lookup"><span data-stu-id="bb6e2-189">**Applies to: This folder, subfolders and files**</span></span>
    
5. <span data-ttu-id="bb6e2-190">Нажмите **Дополнительные разрешения** и выберите следующее:</span><span class="sxs-lookup"><span data-stu-id="bb6e2-190">Click **Advanced Permissions** and select the following:</span></span>
    
  - <span data-ttu-id="bb6e2-191">**Чтение атрибутов**;</span><span class="sxs-lookup"><span data-stu-id="bb6e2-191">**Read attributes**</span></span>
    
  - <span data-ttu-id="bb6e2-192">**Чтение дополнительных атрибутов**;</span><span class="sxs-lookup"><span data-stu-id="bb6e2-192">**Read extended attributes**</span></span>
    
  - <span data-ttu-id="bb6e2-193">**Чтение разрешений**.</span><span class="sxs-lookup"><span data-stu-id="bb6e2-193">**Read permissions**</span></span>
    
6. <span data-ttu-id="bb6e2-194">Проверьте доступ к общей папке Cases$. Для этого сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="bb6e2-194">Test access to the Cases$ file share by doing the following:</span></span>
    
1. <span data-ttu-id="bb6e2-195">Добавьте пользователя в группу Custodians.</span><span class="sxs-lookup"><span data-stu-id="bb6e2-195">Add a user to the Custodians group.</span></span>
    
2. <span data-ttu-id="bb6e2-196">Поместите файл в папку Cases$.</span><span class="sxs-lookup"><span data-stu-id="bb6e2-196">Place a file in the Cases$ folder.</span></span>
    
3. <span data-ttu-id="bb6e2-p109">От имени пользователя перейдите к промежуточному серверу, например к общей папке \\\\Staging, чтобы проверить, какие папки доступны. Папки **Cases$** не должно быть в списке.</span><span class="sxs-lookup"><span data-stu-id="bb6e2-p109">As the user, browse to the staging server, for example browse to the \\\\Staging share to see what shares are available. You shouldn't see the **Cases$** share listed.</span></span>
    
4. <span data-ttu-id="bb6e2-p110">Вручную введите полный путь к общей папке Cases$ в проводнике. Должна открыться общая папка Cases$.</span><span class="sxs-lookup"><span data-stu-id="bb6e2-p110">Manually type the full path to the Cases$ share into Explorer. This should open the Cases$ share.</span></span>
    
5. <span data-ttu-id="bb6e2-p111">Попробуйте открыть файл, который вы ранее разместили в общей папке. Должна возникнуть ошибка.</span><span class="sxs-lookup"><span data-stu-id="bb6e2-p111">Try to open the file you previously placed in the share. This should fail.</span></span>
    
### <a name="logon-script"></a><span data-ttu-id="bb6e2-203">Сценарий входа</span><span class="sxs-lookup"><span data-stu-id="bb6e2-203">Logon script</span></span>

1. <span data-ttu-id="bb6e2-204">Скопируйте и вставьте этот сценарий Windows PowerShell в Блокнот:</span><span class="sxs-lookup"><span data-stu-id="bb6e2-204">Copy and paste this Windows PowerShell script into Notepad:</span></span>
    
  ```
  # Automated file collection script
# Substantial error processing should be added for robust execution and troubleshooting opportunities
# All commented out write-hosts are for debugging only and are commented out for regular execution

# Functions 

Function CreateCaseFolder() {

#Check to see if case folder already exists
$CaseFolderCheck = Test-Path $CaseLocation

try {

    if (!$CaseFolderCheck) {
    # Case folder doesn't exist.  Create the case folder and the log file location
    # Write-Host -ForegroundColor Cyan "Creating Case Folder $CaseLocation"
    New-Item "$CaseLocation" -ItemType Directory -Force -ErrorAction SilentlyContinue
    # Write-Host -ForegroundColor Cyan "Creating Case Log Folder $CaseLogLocation"
    New-Item "$CaseLogLocation" -ItemType Directory -Force -ErrorAction SilentlyContinue
    # Write-Host -ForegroundColor Cyan "Creating Case PST folder $CasePSTLocation"
    New-Item "$CasePSTLocation" -ItemType Directory -Force -ErrorAction SilentlyContinue

    }
    else {

    # do nothing since the target case folder already exists

    }
}
catch [System.Exception] {

    # To do..
    # to log to an exception or log file
    
    }
}

Function CopyFileToCaseFolder($SourcePath, $TargetPath, $FileName) {
    
    # Check to see if the file already exists
    $TargetFileCheck = Test-Path $TargetPath\$FileName

try {

    if (!$TargetFileCheck) {
    # Copy the file to the case folder
    Write-Host $SourcePath $TargetPath $FileName
    robocopy "$SourcePath" "$TargetPath" "$FileName" /COPY:DATSO /TEE /LOG+:$LoggingFile /R:10 /W:10 | Out-Null

    }
    else {

    # do nothing since file is already in the target case folder

    }
}
catch [System.Exception] {

    # To do..
    # to log to an exception or log file
    
    }
}

# Global variable initializations

# Error log
$Loggederrors=@()

# The array to contain the file types we collect
$FileTypes = @("*.doc","*.docx","*.pst","*.txt")

# We'll set the case number to be a combination of the date and user name
# For example, a case for John Doe on Dec 14, 2014 at 2:38pm would be:
# 201412141438_jdoe
$CaseNo = get-date -Format yyyyMMddHHmm
$CaseNo = $CaseNo + "_" + [Environment]::UserName

# Target location to copy case files
$CaseRootLocation = "\\staging\Cases$" 

# File copy location, log file location, PST file location and temporary log file location
$CaseLocation = $CaseRootLocation + "\" + $CaseNo
$CaseLogLocation = $CaseRootLocation + "\" + $CaseNo + "\_Log"
$CasePSTLocation = $CaseRootLocation + "\" + $CaseNo + "\_PSTs"
$TemporaryLogLocation = [Environment]::getfolderpath('ApplicationData') + "\" + $CaseNo

# Inventory of local drives
$LocalDrives = Get-PSDrive -PSProvider FileSystem -Scope Global

$LoggingFile = "$CaseLogLocation\FileCopyErrors.log"

# Main script

# Create the case folder if it doesn't already exist
CreateCaseFolder

# Create the list of files to be copied
# First create the temporary directory in the AppData\Roaming folder
New-Item "$TemporaryLogLocation" -ItemType Directory -Force -ErrorAction SilentlyContinue
$LocalDrives | foreach {

    # Write-Host -ForeGroundColor Cyan "Collecting Files for Drive: " $_
    Get-ChildItem -Path $_.Root -Recurse -Include $FileTypes -ErrorAction SilentlyContinue -ErrorVariable +Loggederrors | Export-Clixml $TemporaryLogLocation\$_.xml -Force
    # Needs try catch and logged collection error file
}

# Now let's read each file and copy any files we need to the case folder
# We will also copy these XMLs to the case log files folder as we go along
# We only want to process XML files, just in case something else got in there as the script ran
$CaseDriveFiles = Get-ChildItem $TemporaryLogLocation -Filter '*.xml'
$CaseDriveFiles | foreach {
    # Copy the XML file to the case log location
    CopyFileToCaseFolder $_.Directory.FullName $CaseLogLocation $_.Name
    $DriveFile = $_.FullName
    # Write-Host -ForegroundColor Cyan "Copying Files specified in the XML file: $DriveFile"
    $CurrentDriveFile = Import-Clixml $DriveFile
    $CurrentDriveFile | foreach {
        # write-host $_.FullName
        # if it's a PST, add to the PSTs folder. otherwise add it to case folder
        if ($_.Extension -match '.PST')
        {
            CopyFileToCaseFolder $_.Directory.FullName $CasePSTLocation $_.Name
            write-host "this is a PST"
        }
        else
        {
            CopyFileToCaseFolder $_.Directory.FullName $CaseLocation $_.Name
        }
    }
}

# Now delete the temporary log file
Remove-Item $TemporaryLogLocation -Recurse 

Write-Host -ForegroundColor Cyan "Finished."

  ```

2. <span data-ttu-id="bb6e2-205">Сохраните приведенный выше сценарий как CollectionScript.ps1 в легкодоступном расположении, например C:\\AFCScripts.</span><span class="sxs-lookup"><span data-stu-id="bb6e2-205">Save the above script as CollectionScript.ps1 in a location that's easy for you to find, for example, C:\\AFCScripts.</span></span>
    
3. <span data-ttu-id="bb6e2-p112">Используя функцию Блокнота "Перейти", при необходимости внесите следующие изменения:</span><span class="sxs-lookup"><span data-stu-id="bb6e2-p112">Use the Go To feature in Notepad. Make the following changes, as needed:</span></span>
    
|<span data-ttu-id="bb6e2-208">**Номер строки**</span><span class="sxs-lookup"><span data-stu-id="bb6e2-208">**Line #**</span></span>|<span data-ttu-id="bb6e2-209">**Необходимые изменения**</span><span class="sxs-lookup"><span data-stu-id="bb6e2-209">**What you need to change**</span></span>|<span data-ttu-id="bb6e2-210">**Обязательно?**</span><span class="sxs-lookup"><span data-stu-id="bb6e2-210">**Required/optional**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="bb6e2-211">71</span><span class="sxs-lookup"><span data-stu-id="bb6e2-211">71</span></span>  <br/> |<span data-ttu-id="bb6e2-p113">Переменная **$FileTypes**. Включите расширения всех типов файлов, подлежащих инвентаризации и сбору в переменной массива с использованием сценария.</span><span class="sxs-lookup"><span data-stu-id="bb6e2-p113">**$FileTypes** variable. Include all the file type extensions that you want the script to inventory and collect in the array variable. </span></span><br/> |<span data-ttu-id="bb6e2-214">Необязательна</span><span class="sxs-lookup"><span data-stu-id="bb6e2-214">Optional</span></span>  <br/> |
|<span data-ttu-id="bb6e2-215">76 и 77</span><span class="sxs-lookup"><span data-stu-id="bb6e2-215">76 and 77</span></span>  <br/> |<span data-ttu-id="bb6e2-p114">Измените способ сборки переменной **$CaseNo** в соответствии со своими потребностями. Сценарий записывает текущую дату и время, а также добавляет к переменной имя пользователя.</span><span class="sxs-lookup"><span data-stu-id="bb6e2-p114">Change the way the **$CaseNo** variable is built to suit your needs. The script captures the current date and time and appends the user name to it. </span></span><br/> |<span data-ttu-id="bb6e2-218">Необязательно</span><span class="sxs-lookup"><span data-stu-id="bb6e2-218">Optional</span></span>  <br/> |
|<span data-ttu-id="bb6e2-219">80</span><span class="sxs-lookup"><span data-stu-id="bb6e2-219">80</span></span>  <br/> |<span data-ttu-id="bb6e2-220">Переменную **$CaseRootLocation** необходимо настроить для общей папки коллекции промежуточных серверов, например **\\\\Staging\\Cases$**.</span><span class="sxs-lookup"><span data-stu-id="bb6e2-220">**$CaseRootLocation** variable needs to be set to your staging servers collection file share, for example **\\\\Staging\\Cases$**.</span></span> <br/> |<span data-ttu-id="bb6e2-221">Обязательный</span><span class="sxs-lookup"><span data-stu-id="bb6e2-221">Required</span></span>  <br/> |
   
4. <span data-ttu-id="bb6e2-222">Поместите файл CollectionScript.ps1 в общую папку Netlogon на контроллере домена. </span><span class="sxs-lookup"><span data-stu-id="bb6e2-222">Place the CollectionScript.ps1 file in the Netlogon file share on a domain controller.</span></span> 
    
### <a name="configure-gpo-for-the-logon-script-and-custodians-group"></a><span data-ttu-id="bb6e2-223">Настройте GPO для сценария входа и группы Custodians</span><span class="sxs-lookup"><span data-stu-id="bb6e2-223">Configure GPO for the logon script and Custodians Group</span></span>

1. <span data-ttu-id="bb6e2-224">Настройте сценарий входа для группы Custodians, следуя инструкциям из раздела "Как назначить сценарии входа пользователей" статьи [Использование сценариев запуска, завершения работы, входа и выхода в групповой политике](https://go.microsoft.com/fwlink/p/?LinkId=614844).</span><span class="sxs-lookup"><span data-stu-id="bb6e2-224">Configure a logon script for the Custodians group by following the "How to assign user logon scripts" section in the topic, [Using Startup, Shutdown, Logon, and Logoff Scripts in Group Policy](https://go.microsoft.com/fwlink/p/?LinkId=614844).</span></span>
    
2. <span data-ttu-id="bb6e2-225">Удалите пользователей, прошедших проверку подлинности, из раздела **Фильтры безопасности** и добавьте группу Custodians.</span><span class="sxs-lookup"><span data-stu-id="bb6e2-225">Remove authenticated users from **Security Filtering**, and add the Custodians group.</span></span>
    
### <a name="pst-import-option-a-script-for-exchange-server-2013"></a><span data-ttu-id="bb6e2-226">Вариант А импорта PST-файлов, сценарий для Exchange Server 2013</span><span class="sxs-lookup"><span data-stu-id="bb6e2-226">PST import Option A, script for Exchange Server 2013</span></span>

1.  <span data-ttu-id="bb6e2-227">Скопируйте и вставьте следующий сценарий Windows PowerShell в Блокнот:</span><span class="sxs-lookup"><span data-stu-id="bb6e2-227">Copy and paste the following Windows PowerShell script into Notepad:</span></span>
    
  ```
  # Script to import all PSTs in a given folder to a target mailbox
#
# This is for on-prem Exchange only
# Input parameters
# When you run the script, you call it with two parameters, PST source path and target mailbox alias
# For example:  .\PSTImport.ps1 \\FileShare\PSTFiles jdoe

param ([String]$SourcePath,[String]$MailboxAlias)

# Folder identifier is the string we want to show in the mailbox that we import the PSTs to

$FolderIdentifier = "zzImportedPSTs_"

# Connect to Exchange remote powershell using the connection Uri below
# This would be the format https://<exchange server FQDN>/Powershell

$ConnectionUri = 'https://h10-exch/PowerShell'
$RemoteEx2013Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri $ConnectionUri -Authentication Kerberos
Import-PSSession $RemoteEx2013Session

# Get all the files in the source path

$AllFiles = Get-ChildItem $SourcePath -Recurse

# Go through each file and if it's a PST launch a mailbox import request for it

$AllFiles | ForEach-Object {
    If ($_.Extension -eq ".pst") {
        $ImportName = $MailboxAlias + "_" + $_.Name
        $FolderName = $FolderIdentifier + $_.Name
        New-MailboxImportRequest -Name $ImportName -Mailbox $MailboxAlias -FilePath $_.FullName -TargetRootFolder $FolderName
    }
}
  ```

2. <span data-ttu-id="bb6e2-p115">Сохраните сценарий как PSTImportScript.ps1 в расположении, которое вы сможете легко найти. Например, для удобства создайте папку \\\\Staging\\AFCScripts на своем промежуточном сервере и сохраните сценарий в ней.</span><span class="sxs-lookup"><span data-stu-id="bb6e2-p115">Save the script as PSTImportScript.ps1 in a location that's easy for you to find. For example and ease of use, create a folder on your staging server called \\\\Staging\\AFCScripts, and save it there.</span></span>
    
3. <span data-ttu-id="bb6e2-230">Используя функцию Блокнота "Перейти", при необходимости внесите следующие изменения:</span><span class="sxs-lookup"><span data-stu-id="bb6e2-230">Use the Go To feature in Notepad, and make the following changes, as needed:</span></span>
    
|<span data-ttu-id="bb6e2-231">**Номер строки**</span><span class="sxs-lookup"><span data-stu-id="bb6e2-231">**Line #**</span></span>|<span data-ttu-id="bb6e2-232">**Необходимые изменения**</span><span class="sxs-lookup"><span data-stu-id="bb6e2-232">**What you need to change**</span></span>|<span data-ttu-id="bb6e2-233">**Обязательно?**</span><span class="sxs-lookup"><span data-stu-id="bb6e2-233">**Required/optional**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="bb6e2-234">12 </span><span class="sxs-lookup"><span data-stu-id="bb6e2-234">12</span></span>  <br/> |<span data-ttu-id="bb6e2-p116">**$FolderIdentifier** помечает папки почтовых ящиков, в которые импортируются PST-файлы. При необходимости измените их.</span><span class="sxs-lookup"><span data-stu-id="bb6e2-p116">**$FolderIdentifier** tags the mailbox folders that PSTs are imported into. Change this if necessary. </span></span><br/> |<span data-ttu-id="bb6e2-237">Необязательный</span><span class="sxs-lookup"><span data-stu-id="bb6e2-237">Optional</span></span>  <br/> |
|<span data-ttu-id="bb6e2-238">17 </span><span class="sxs-lookup"><span data-stu-id="bb6e2-238">17</span></span>  <br/> |<span data-ttu-id="bb6e2-239">**$ConnectionUri** необходимо настроить на отдельном сервере.</span><span class="sxs-lookup"><span data-stu-id="bb6e2-239">**$ConnectionUri** needs to be set to your own server.</span></span> <br/> <span data-ttu-id="bb6e2-p117">> [!IMPORTANT]> Убедитесь, что **$ConnectionUri** указывает на расположение с префиксом http://, а не https://. Префикс https:// не будет работать.</span><span class="sxs-lookup"><span data-stu-id="bb6e2-p117">> [!IMPORTANT]> Make sure your **$ConnectionUri** points to a http location, not https. It won't work with https:.</span></span>          |<span data-ttu-id="bb6e2-242">Обязательно</span><span class="sxs-lookup"><span data-stu-id="bb6e2-242">Required</span></span>  <br/> |
   
4. <span data-ttu-id="bb6e2-243">Убедитесь, что у учетной записи "Доверенная подсистема Exchange" есть разрешения на чтение, запись и выполнение в общей папке \\\\Staging\\Cases$.</span><span class="sxs-lookup"><span data-stu-id="bb6e2-243">Verify that the Exchange Trusted Subsystem account has Read, Write, and Execute permissions to the \\\\Staging\\Cases$ share.</span></span>
    
5. <span data-ttu-id="bb6e2-244">У сценария импорта PST-файлов есть два обязательных входных параметра:</span><span class="sxs-lookup"><span data-stu-id="bb6e2-244">The PST import script requires the following two input parameters:</span></span>
    
  - <span data-ttu-id="bb6e2-245">**$SourcePath**  расположение импортируемых PST-файлов, например \\\\Staging\\Cases$.</span><span class="sxs-lookup"><span data-stu-id="bb6e2-245">**$SourcePath** The location of the PST files to be imported, for example \\\\Staging\\Cases$.</span></span>
    
  - <span data-ttu-id="bb6e2-246">**$MailboxAlias**  псевдоним целевого почтового ящика, в который будут импортированы элементы электронной почты.</span><span class="sxs-lookup"><span data-stu-id="bb6e2-246">**$MailboxAlias** The alias of the target mailbox that will receive the imported email items.</span></span>
    
6. <span data-ttu-id="bb6e2-247">Например, если вы хотите импортировать все PST-файлы из пути \\Staging\Cases$ в почтовый ящик с псевдонимом eDiscoveryMailbox, запустите следующий сценарий: `\\staging\AFCscripts\PSTImportScript.ps1 \\Staging\cases$ eDiscoveryMailbox`.</span><span class="sxs-lookup"><span data-stu-id="bb6e2-247">For example, if you want to import all the PST files from the path \\Staging\Cases$ into a mailbox with the alias eDiscoveryMailbox, you would run the script like this `\\staging\AFCscripts\PSTImportScript.ps1 \\Staging\cases$ eDiscoveryMailbox`.</span></span>
    
### <a name="pst-import-option-b-for-exchange-online"></a><span data-ttu-id="bb6e2-248">Вариант Б импорта PST-файлов для Exchange Online</span><span class="sxs-lookup"><span data-stu-id="bb6e2-248">PST Import Option B, for Exchange Online</span></span>

-  <span data-ttu-id="bb6e2-p118">Создайте структуру почтовых ящиков для размещения импортированных PST-файлов. Дополнительные сведения о том, как создать почтовый ящик пользователя в Exchange Online, см. в статье [Создание почтовых ящиков пользователей в Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=615118).</span><span class="sxs-lookup"><span data-stu-id="bb6e2-p118">Create the mailbox structure to place the imported PST files into. For more information on how to create a user mailbox in Exchange Online, see[Create User Mailboxes in Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=615118).</span></span>
    
### <a name="cold-storage"></a><span data-ttu-id="bb6e2-251">Автономное неструктурированное защищенное хранилище</span><span class="sxs-lookup"><span data-stu-id="bb6e2-251">Cold storage</span></span>

1. <span data-ttu-id="bb6e2-252">Создайте общую папку в виртуальной машине Azure, в которую будут помещены все собранные файлы, например \\\\AZFile1\\ContentColdStorage.</span><span class="sxs-lookup"><span data-stu-id="bb6e2-252">Create a file share on the Azure Virtual Machine, where all the collected files will be placed, for example, \\\\AZFile1\\ContentColdStorage.</span></span>
    
2. <span data-ttu-id="bb6e2-p119">Предоставьте стандартной учетной записи для доступа к контенту разрешения по крайней мере на чтение содержимого общей папки, а также всех вложенных папок и файлов. Дополнительные сведения о настройке службы поиска SharePoint 2013 см. в статье [Создание и настройка приложения-службы поиска в SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=614940).</span><span class="sxs-lookup"><span data-stu-id="bb6e2-p119">Grant the default content access account at least Read permissions to the share and all subfolders and files. For more information about configuring SharePoint 2013 Search, see [Create and configure a Search service application in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=614940).</span></span>
    
3. <span data-ttu-id="bb6e2-255">Если планируется импортировать PST-файлы из общей папки \\\\AZFile1\\ContentColdStorage, предоставьте группе "Доверенная подсистема Exchange" разрешения на чтение, запись и выполнение в этой папке.</span><span class="sxs-lookup"><span data-stu-id="bb6e2-255">If you anticipate importing PST files from \\\\AZFile1\\ContentColdStorage, grant the Exchange Trusted Subsystem Read, Write, and Execute permissions to the share.</span></span>
    
### <a name="orchestrator"></a><span data-ttu-id="bb6e2-256">Orchestrator</span><span class="sxs-lookup"><span data-stu-id="bb6e2-256">Orchestrator</span></span>

1. <span data-ttu-id="bb6e2-257">Скачайте [MoveToColdStorage Runbook](https://go.microsoft.com/fwlink/?LinkId=616095) в Центре загрузки Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="bb6e2-257">Download the[ MoveToColdStorage runbook](https://go.microsoft.com/fwlink/?LinkId=616095) from the Microsoft Download Center.</span></span>
    
2. <span data-ttu-id="bb6e2-p120">Откройте **Runbook Designer** и в области **Подключения** выберите папку, в которую нужно импортировать модуль Runbook. В меню **Действия** выберите пункт **Импортировать**. Откроется диалоговое окно **Импорт**.</span><span class="sxs-lookup"><span data-stu-id="bb6e2-p120">Open the **Runbook Designer**, in the **Connections** pane, click the folder that you want to import the runbook into. Click the **Actions** menu, and the click **Import**. The **Import** dialog box appears.</span></span>
    
3. <span data-ttu-id="bb6e2-261">В поле **Расположение файла** введите путь и имя файла модуля Runbook, который вы хотите импортировать, или щелкните многоточие ( **...**), чтобы найти необходимый файл.</span><span class="sxs-lookup"><span data-stu-id="bb6e2-261">In the **File Location** box, type the path and file name of the runbook you want to import, or click the ellipsis ( **...**) to browse to the file you want to import.</span></span> 
    
4. <span data-ttu-id="bb6e2-p121">Последовательно выберите пункты **Импорт модулей Runbook** и **Импорт данных, зашифрованных в Orchestrator**. Очистите значения в полях **Счетчики**, **Расписания**, **Переменные**, **Группы компьютеров**, **Импортировать глобальные конфигурации** и **Перезаписать существующие глобальные конфигурации**.</span><span class="sxs-lookup"><span data-stu-id="bb6e2-p121">Select **Import runbooks** and **Import Orchestrator encrypted data**. Clear **Counters**, **Schedules**, **Variables**, **Computer Groups**, **Import global configurations**, and **Overwrite existing global configurations**.</span></span>
    
5. <span data-ttu-id="bb6e2-264">Нажмите кнопку **Готово**.</span><span class="sxs-lookup"><span data-stu-id="bb6e2-264">Click **Finish**.</span></span>
    
6. <span data-ttu-id="bb6e2-265">Внесите в модуль Runbook **MoveFilesToColdStorage** следующие изменения.</span><span class="sxs-lookup"><span data-stu-id="bb6e2-265">Edit the **MoveFilesToColdStorage** runbook as follows:</span></span>
    
1. <span data-ttu-id="bb6e2-p122">Действие **Перемещение файла**: задайте в качестве значения параметра **Исходный файл** общую папку для сбора данных, например \\\\Staging\\cases$. Задайте в качестве значения параметра **Конечная папка** общую папку в защищенном хранилище в Azure, например \\\\AZFile1\\ContentColdStorage. Выберите пункт **Создать файл с уникальным именем**.</span><span class="sxs-lookup"><span data-stu-id="bb6e2-p122">**Move File** activity - set the **Source File** path to the collection file share, for example \\\\Staging\\cases$. Set the **Destination Folder** to the cold storage file share in Azure, for example \\\\AZFile1\\ContentColdStorage. Select **Create a file with a unique name**.</span></span>
    
2. <span data-ttu-id="bb6e2-269">Действие **Удаление папки**: задайте в качестве значения параметра **Путь:** общую папку для сбора данных, например \\\\Staging\\cases$\\* и выберите пункт **Удалить все файлы и вложенные папки**.</span><span class="sxs-lookup"><span data-stu-id="bb6e2-269">**Delete Folder** activity - Set the **Path:** to the collection file share, for example \\\\Staging\\cases$\\*, and select **Delete all files and sub-folders**.</span></span> 
    
7. <span data-ttu-id="bb6e2-270">Разверните модуль Runbook **MoveToColdStorage**. Для этого выполните действия, перечисленные в статье[Развертывание модулей Runbook](https://go.microsoft.com/fwlink/p/?LinkId=615120).</span><span class="sxs-lookup"><span data-stu-id="bb6e2-270">Deploy the **MoveToColdStorage** runbook using the procedures in[Deploying Runbooks](https://go.microsoft.com/fwlink/p/?LinkId=615120).</span></span>
    
### <a name="sharepoint-on-premises-search-for-cold-storage"></a><span data-ttu-id="bb6e2-271">Локальный поиск защищенного хранилища в SharePoint</span><span class="sxs-lookup"><span data-stu-id="bb6e2-271">SharePoint on-premises search for cold storage</span></span>

1. <span data-ttu-id="bb6e2-p123">Создайте новый источник контента на своей ферме SharePoint 2013 для общей папки в автономном неструктурированном защищенном хранилище Azure, например \\\\AZFile1\\ContentColdStorage. Дополнительные сведения об управлении источниками контента см. в статье [Добавление, изменение и удаление источника контента в SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615004).</span><span class="sxs-lookup"><span data-stu-id="bb6e2-p123">Create an new content source in your SharePoint 2013 farm for the cold storage share in Azure, for example \\\\AZFile1\\ContentColdStorage. For more information about managing content sources, see [Add, edit, or delete a content source in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615004)</span></span>
    
2. <span data-ttu-id="bb6e2-p124">Запустите полный обход контента. Дополнительные сведения см. в статье [Запуск, приостановка, возобновление и остановка обхода контента в SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615005).</span><span class="sxs-lookup"><span data-stu-id="bb6e2-p124">Start a full crawl. For more information see, [Start, pause, resume, or stop a crawl in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615005).</span></span>
    
## <a name="using-the-solution"></a><span data-ttu-id="bb6e2-276">Использование решения</span><span class="sxs-lookup"><span data-stu-id="bb6e2-276">Using the solution</span></span>

<span data-ttu-id="bb6e2-p125">Это решение используется в пять основных этапов, если PST-файлы не нужно импортировать как в Exchange Server 2013, так и в Exchange Online. В этом разделе описаны действия для всех этих этапов. При работе с решением вашими основными задачами будут следующие:</span><span class="sxs-lookup"><span data-stu-id="bb6e2-p125">There are five major steps in using this solution, assuming you don't want to import the PST files into both Exchange Server 2013 and Exchange Online. This section provides you with the procedures for all of them. Your primary interaction with the solution will be in doing the following:</span></span>
  
1. <span data-ttu-id="bb6e2-280">Управление членством в группе Custodians.</span><span class="sxs-lookup"><span data-stu-id="bb6e2-280">Manage user membership in the Custodians group.</span></span>
    
2. <span data-ttu-id="bb6e2-p126">Ошибки</span><span class="sxs-lookup"><span data-stu-id="bb6e2-p126">Review the log files generated by the logon script. The FileCopyErrors.log lists all the files that were not successfully copied. You need to decide what you want to do with them</span></span>
    
3. <span data-ttu-id="bb6e2-284">Управление процессом импорта PST-файлов.</span><span class="sxs-lookup"><span data-stu-id="bb6e2-284">Managing the PST import process.</span></span>
    
4. <span data-ttu-id="bb6e2-285">Перемещение файлов коллекции в защищенное хранилище.</span><span class="sxs-lookup"><span data-stu-id="bb6e2-285">Moving the collection files to cold storage.</span></span>
    
<span data-ttu-id="bb6e2-286">Все остальные действия не относятся к этому решению.</span><span class="sxs-lookup"><span data-stu-id="bb6e2-286">All the other steps are not specific to this solution.</span></span> <span data-ttu-id="bb6e2-287">Это стандартные административные задачи, выполняемые в SharePoint 2013, Microsoft 365 и Azure.</span><span class="sxs-lookup"><span data-stu-id="bb6e2-287">They are standard administrative tasks that you perform in SharePoint 2013, Microsoft 365, and Azure.</span></span> <span data-ttu-id="bb6e2-288">В этом решении есть элементы, которые не предоставляют никаких рекомендаций, необходимых для работы, в зависимости от потребностей компании, например:</span><span class="sxs-lookup"><span data-stu-id="bb6e2-288">There are items that this solution does not provide any guidance that you will need to work out based on your company's needs, such as:</span></span>
  
1. <span data-ttu-id="bb6e2-289">Отслеживание дел eDiscovery и связанных с ними хранителей.</span><span class="sxs-lookup"><span data-stu-id="bb6e2-289">Tracking your eDiscovery cases, and which Custodians are associated with which case.</span></span>
    
2. <span data-ttu-id="bb6e2-290">Отслеживание связей наборов коллекций файлов и дел eDiscovery.</span><span class="sxs-lookup"><span data-stu-id="bb6e2-290">Tracking which sets of file collections are associate with which eDiscovery case.</span></span>
    
3. <span data-ttu-id="bb6e2-291">Согласование времени выполнения этапов импорта и перемещения в защищенное хранилище.</span><span class="sxs-lookup"><span data-stu-id="bb6e2-291">Coordinating the timing of the Import and move to cold storage steps.</span></span>
    
4. <span data-ttu-id="bb6e2-292">Управление размером файлов, используемых в службе Azure.</span><span class="sxs-lookup"><span data-stu-id="bb6e2-292">Managing the file space used in Azure.</span></span>
    
5. <span data-ttu-id="bb6e2-293">Управление почтовыми ящиками, в которые импортируются PST-файлы.</span><span class="sxs-lookup"><span data-stu-id="bb6e2-293">Managing the mailboxes that PSTs are imported into.</span></span>
    
6. <span data-ttu-id="bb6e2-294">Резервное копирование и восстановление всех локальных данных.</span><span class="sxs-lookup"><span data-stu-id="bb6e2-294">Backup and restoration of all on-premises data.</span></span>
    
### <a name="custodian-management"></a><span data-ttu-id="bb6e2-295">Управление хранителями</span><span class="sxs-lookup"><span data-stu-id="bb6e2-295">Custodian management</span></span>

- <span data-ttu-id="bb6e2-p128">Чтобы начать процесс автоматического сбора файлов для отдельных пользователей, добавьте их в группу Custodians. При следующем входе пользователя в систему будет выполняться сценарий входа, назначенный группе Custodians с помощью групповой политики.</span><span class="sxs-lookup"><span data-stu-id="bb6e2-p128">To start the automated file collection process for an individual user, add them to the Custodians group. The next time that the user logs on, the logon script assigned to the Custodians group through Group Policy will run.</span></span> 
    
### <a name="monitor-collected-files-and-review-log-files"></a><span data-ttu-id="bb6e2-298">Отслеживание сбора файлов и просмотр файлов журнала</span><span class="sxs-lookup"><span data-stu-id="bb6e2-298">Monitor collected files and review log files</span></span>

1. <span data-ttu-id="bb6e2-p129">Откройте общую папку для сбора данных, например \\\\Staging\\cases$\\*, и найдите в ней папку пользователя. Имя папки будет иметь следующий формат:  *ггггММддЧЧмм_ИмяПользователя*  .</span><span class="sxs-lookup"><span data-stu-id="bb6e2-p129">Watch the collection file share, for example \\\\Staging\\cases$\\*, for the collection folder from the user. The name of the folder will be formatted like this:  *yyyyMMddHHmm_UserName*  .</span></span>
    
2. <span data-ttu-id="bb6e2-p130">По завершении сбора данных откройте эту папку и перейдите в папку _Log. В папке _Log вы обнаружите следующее:</span><span class="sxs-lookup"><span data-stu-id="bb6e2-p130">When the collection is completed, open the collection folder, and browse to the _Log folder. In the _Log folder, you will see the following:</span></span>
    
  - <span data-ttu-id="bb6e2-p131">Один XML-файл для каждого локального диска на компьютере пользователя, например **A.xml**, **C.xml**. Эти файлы содержат инвентаризированные диски, на основе которых они получили свои имена. Файлы используются для операции Robocopy.</span><span class="sxs-lookup"><span data-stu-id="bb6e2-p131">One XML file for every local drive on the user's computer, for example **A.xml**, **C.xml**. These files contain the inventory drives that they are named after, and they are used for the robocopy operation.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="bb6e2-p132">Сценарий сбора данных только создаст запись в файле инвентаризации для типов файлов, определенных в самом сценарии. Он не будет создавать запись инвентаризации для каждого файла на компьютере пользователя.</span><span class="sxs-lookup"><span data-stu-id="bb6e2-p132">The collection script will only create an entry in the inventory file for the file types that you defined in the script itself. It will not create an inventory entry for every file on the user's computer.</span></span> 
  
  - <span data-ttu-id="bb6e2-p133">Один файл журнала с именем FileCopyErrors.log для каждого цикла сбора данных. Этот файл содержит список файлов, которые операции Robocopy не удалось скопировать в общую папку для сбора данных, например \\\\Staging\\cases$\\*. Вам потребуется просмотреть этот список и решить, какие действия предпринять в отношении пропущенных файлов. Как правило, вам нужно будет собрать их вручную (если они необходимы) или исключить их из операции сбора данных, если вы решите, что эти файлы вам не нужны.</span><span class="sxs-lookup"><span data-stu-id="bb6e2-p133">One log file named FileCopyErrors.log for each collection run. This file contains a listing of the files that robocopy could not copy to the file collection share, for example, \\\\Staging\\cases$\\*. You will need to review this and decide what actions to take for these missed files. Usually, you either need to collect them manually if you want them, or you may decide that they are not required and can therefore be omitted from the collection.</span></span>
    
### <a name="pst-import-option-a-for-exchange-server-2013"></a><span data-ttu-id="bb6e2-311">Вариант А импорта PST-файлов для Exchange Server 2013</span><span class="sxs-lookup"><span data-stu-id="bb6e2-311">PST import option A for Exchange Server 2013</span></span>

1. <span data-ttu-id="bb6e2-p134">Войдите на сервер, на котором размещена общая папка для сбора данных, например **сервер для промежуточного хранения**, и откройте Windows PowerShell. Дополнительные сведения о запуске Windows PowerShell см. в статье[Запуск Windows PowerShell в Windows Server](https://go.microsoft.com/fwlink/p/?LinkId=615115).</span><span class="sxs-lookup"><span data-stu-id="bb6e2-p134">Log on to the server that hosts the collection file share, for example **Staging**, and open Windows PowerShell. For more information about starting Windows PowerShell, see[Starting Windows PowerShell on Windows Server](https://go.microsoft.com/fwlink/p/?LinkId=615115).</span></span>
    
2. <span data-ttu-id="bb6e2-p135">Установите отсутствие ограничений для политики выполнения. Введите  `Set-ExecutionPolicy Unrestricted -Scope Process` в Windows PowerShell и нажмите клавишу ВВОД.</span><span class="sxs-lookup"><span data-stu-id="bb6e2-p135">Set the Execution policy to Unrestricted . Type  `Set-ExecutionPolicy Unrestricted -Scope Process` into Windows PowerShell, and press Enter.</span></span>
    
3. <span data-ttu-id="bb6e2-p136">Запустите файл PSTImportScript.ps1, указав параметры **$SourcePath** и **$MailboxAlias**. Дополнительные сведения о запуске сценариев Windows PowerShell см. в статье[Поддержка скриптов](https://go.microsoft.com/fwlink/p/?LinkID=615117).</span><span class="sxs-lookup"><span data-stu-id="bb6e2-p136">Run the PSTImportScript.ps1 file, and provide the **$SourcePath** and **$MailboxAlias** parameters. For more information about running Windows PowerShell scripts, see[Running Scripts](https://go.microsoft.com/fwlink/p/?LinkID=615117).</span></span>
    
4. <span data-ttu-id="bb6e2-318">Проверьте выходные данные на наличие ошибок.</span><span class="sxs-lookup"><span data-stu-id="bb6e2-318">Review the output for errors.</span></span>
    
5. <span data-ttu-id="bb6e2-p137">Прежде чем импортировать PST-файл с таким же именем в тот же почтовый ящик, необходимо удалить запрос на импорт почтового ящика. Для этого выполните следующую команду:  `Get-MailboxImportRequest | Remove-MailboxImportRequest`. Вам будет предложено удалить каждый запрос из очереди по отдельности. Выполните необходимые действия.</span><span class="sxs-lookup"><span data-stu-id="bb6e2-p137">Before you attempt to import an identically named PST file into the same mailbox, you have to remove the mailbox import request. Run the following command to do that:  `Get-MailboxImportRequest | Remove-MailboxImportRequest`. You will be prompted to remove each individual request from the queue. Respond as needed.</span></span>
    
### <a name="pst-import-option-b-for-exchange-online"></a><span data-ttu-id="bb6e2-323">Вариант Б импорта PST-файлов для Exchange Online</span><span class="sxs-lookup"><span data-stu-id="bb6e2-323">PST import option B, for Exchange Online</span></span>

- <span data-ttu-id="bb6e2-324">Чтобы поместить собранные PST-файлы в Exchange Online, выполните процедуры, приведенные в файлах импорта, в Microsoft 365 с помощью [сетевой отправки](https://docs.microsoft.com/microsoft-365/compliance/use-network-upload-to-import-pst-files).</span><span class="sxs-lookup"><span data-stu-id="bb6e2-324">To place the collected PST files into Exchange Online, follow the procedures in the Import files into Microsoft 365 through [network upload](https://docs.microsoft.com/microsoft-365/compliance/use-network-upload-to-import-pst-files).</span></span>
    
### <a name="move-to-cold-storage"></a><span data-ttu-id="bb6e2-325">Перемещение в защищенное хранилище</span><span class="sxs-lookup"><span data-stu-id="bb6e2-325">Move to cold storage</span></span>

1. <span data-ttu-id="bb6e2-326">Запустите Runbook **MoveToColdStorage** , используя процедуры в [запущенных модулях Runbook](https://go.microsoft.com/fwlink/p/?LinkId=615123).</span><span class="sxs-lookup"><span data-stu-id="bb6e2-326">Run the **MoveToColdStorage** runbook using the procedures in [Running Runbooks](https://go.microsoft.com/fwlink/p/?LinkId=615123).</span></span>
    
2. <span data-ttu-id="bb6e2-p138">Просмотрите общую папку Azure, используемую для долгосрочного хранения, например \\\\AZFile1\\ContentColdStorage, а также локальную общую папку для сбора данных, например \\\\Staging\\cases$. Файлы и папки должны появиться в общей папке в защищенном хранилище и исчезнуть из общей папки для сбора данных.</span><span class="sxs-lookup"><span data-stu-id="bb6e2-p138">Watch the Azure file share you are using for long term storage, for example \\\\AZFile1\\ContentColdStorage and the on-premises collection file share, for example \\\\Staging\\cases$. You should see the files and folders appear in the cold storage file share and disappear from the collection file share.</span></span>
    
### <a name="ediscovery"></a><span data-ttu-id="bb6e2-329">Обнаружение электронных данных</span><span class="sxs-lookup"><span data-stu-id="bb6e2-329">eDiscovery</span></span>

1. <span data-ttu-id="bb6e2-p139">Разрешите полный обход контента для общей папки в автономном неструктурированном защищенном хранилище, чтобы запускать его по расписанию, либо инициируйте обход контента. Дополнительные сведения о запуске полного или добавочного обхода контента см. в статье [Запуск, приостановка, возобновление и остановка обхода контента в SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615005).</span><span class="sxs-lookup"><span data-stu-id="bb6e2-p139">Either allow the full crawl of the cold storage file share to run as schedules, or initiate a crawl. For more information on starting full or incremental crawls, see [Start, pause, resume, or stop a crawl in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615005).</span></span>
    
2. <span data-ttu-id="bb6e2-332">Создайте обращение к функции "eDiscovery" в SharePoint 2013, если вы использовали вариант А для импорта PST-файлов, или обращение к функции "eDiscovery" в SharePoint Online, если использовался вариант Б.</span><span class="sxs-lookup"><span data-stu-id="bb6e2-332">Create an eDiscovery case in SharePoint 2013 if you used option A for a PST file import or create an eDiscovery case in SharePoint Online if you used option B.</span></span>
    

