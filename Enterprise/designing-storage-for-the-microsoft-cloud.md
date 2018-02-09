---
title: "Разработка хранилища для Microsoft Cloud"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 7e511118-1b75-413a-b959-ad0d3ffc9516
description: "Сводка. Узнайте, зачем вам облачное хранилище, а также ознакомьтесь со списком доступных облачных хранилищ (Майкрософт) и основных сценариев хранения."
ms.openlocfilehash: ed816743e2d85a622a3fbfbb129bf90a7db93881
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="designing-storage-for-the-microsoft-cloud"></a><span data-ttu-id="26f2b-103">Разработка хранилища для Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="26f2b-103">Designing storage for the Microsoft cloud</span></span>

 <span data-ttu-id="26f2b-104">**Сводка.** Узнайте, зачем вам облачное хранилище, а также ознакомьтесь со списком доступных облачных хранилищ (Майкрософт) и основных сценариев хранения.</span><span class="sxs-lookup"><span data-stu-id="26f2b-104">**Summary:** Understand why you need cloud storage and review the list of Microsoft's cloud storage options and the key storage scenarios.</span></span>
  
<span data-ttu-id="26f2b-105">Интеграция хранилища с облачными службами (Майкрософт) предоставляет вам доступ к широкому ассортименту служб и облачных платформ.</span><span class="sxs-lookup"><span data-stu-id="26f2b-105">Integrating your storage with Microsoft cloud services gives you access to a broad range of services and cloud platform options.</span></span>
  
## <a name="why-cloud-storage"></a><span data-ttu-id="26f2b-106">Зачем использовать облачное хранилище?</span><span class="sxs-lookup"><span data-stu-id="26f2b-106">Why cloud storage?</span></span>

<span data-ttu-id="26f2b-107">Есть две основные причины для использования облачного хранилища.</span><span class="sxs-lookup"><span data-stu-id="26f2b-107">There are two key reasons to use cloud storage.</span></span>
  
1. <span data-ttu-id="26f2b-108">Быстрый выход на рынок:</span><span class="sxs-lookup"><span data-stu-id="26f2b-108">Speed to market:</span></span>
    
  - <span data-ttu-id="26f2b-109">быстродействующая конфигурация, позволяющая обеспечить высокую доступность и аварийное восстановление;</span><span class="sxs-lookup"><span data-stu-id="26f2b-109">Faster configuration for high availability and disaster recovery</span></span>
    
  - <span data-ttu-id="26f2b-110">не нужно приобретать оборудование для хранилища;</span><span class="sxs-lookup"><span data-stu-id="26f2b-110">No storage hardware to purchase</span></span>
    
  - <span data-ttu-id="26f2b-111">в облачных предложениях Майкрософт имеются встроенные вспомогательные средства;</span><span class="sxs-lookup"><span data-stu-id="26f2b-111">Built-in plumbing provided by Microsoft's cloud offerings</span></span>
    
  - <span data-ttu-id="26f2b-112">доступность по всему миру.</span><span class="sxs-lookup"><span data-stu-id="26f2b-112">Available from anywhere in the world</span></span>
    
2. <span data-ttu-id="26f2b-113">Снижение затрат на обслуживание:</span><span class="sxs-lookup"><span data-stu-id="26f2b-113">Lower costs to maintain:</span></span>
    
  - <span data-ttu-id="26f2b-114">эластичность, позволяющая масштабировать хранилище согласно вашим потребностям;</span><span class="sxs-lookup"><span data-stu-id="26f2b-114">Elasticity to scale up and down your storage demands</span></span>
    
  - <span data-ttu-id="26f2b-115">не нужно обслуживать или переносить оборудование хранилища;</span><span class="sxs-lookup"><span data-stu-id="26f2b-115">No storage hardware to maintain or migrate</span></span>
    
  - <span data-ttu-id="26f2b-116">корпорация Майкрософт предоставляет встроенные средства для обслуживания и повышения качества инфраструктуры;</span><span class="sxs-lookup"><span data-stu-id="26f2b-116">Microsoft is your built-in plumber to maintain and improve infrastructure</span></span>
    
  - <span data-ttu-id="26f2b-117">лучшая защита хранилища на рынке, которая постоянно совершенствуется.</span><span class="sxs-lookup"><span data-stu-id="26f2b-117">Best storage security in the marketplace with ongoing improvements</span></span>
    
## <a name="microsoft-cloud-storage-options"></a><span data-ttu-id="26f2b-118">Варианты облачного хранилища (Майкрософт)</span><span class="sxs-lookup"><span data-stu-id="26f2b-118">Microsoft cloud storage options</span></span>

<span data-ttu-id="26f2b-119">В этом разделе представлен широкий ассортимент облачных хранилищ.</span><span class="sxs-lookup"><span data-stu-id="26f2b-119">To help you understand the wide variety of cloud storage options, we use a construction analogy.</span></span>
  
### <a name="move-in-ready"></a><span data-ttu-id="26f2b-120">Решения, не требующие сборки</span><span class="sxs-lookup"><span data-stu-id="26f2b-120">Move-in ready</span></span>

<span data-ttu-id="26f2b-p101">Используйте эти заранее подготовленные пакеты решений, объединенных с существующими службами. Они готовы к работе и практически не требуют настройки.</span><span class="sxs-lookup"><span data-stu-id="26f2b-p101">Use these prepackaged solutions that are bundled with existing services. Use immediately and with minimal configuration.</span></span>
  
- <span data-ttu-id="26f2b-123">Office 365</span><span class="sxs-lookup"><span data-stu-id="26f2b-123">Office 365</span></span>
    
- <span data-ttu-id="26f2b-124">Microsoft Intune</span><span class="sxs-lookup"><span data-stu-id="26f2b-124">Microsoft Intune</span></span>
    
- <span data-ttu-id="26f2b-125">OneDrive для бизнеса</span><span class="sxs-lookup"><span data-stu-id="26f2b-125">OneDrive for Business</span></span>
    
- <span data-ttu-id="26f2b-126">Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="26f2b-126">Dynamics 365</span></span>
    
- <span data-ttu-id="26f2b-127">Visual Studio Team Services</span><span class="sxs-lookup"><span data-stu-id="26f2b-127">Visual Studio Team Services</span></span>
    
- <span data-ttu-id="26f2b-128">Azure Site Recovery</span><span class="sxs-lookup"><span data-stu-id="26f2b-128">Azure Site Recovery</span></span>
    
- <span data-ttu-id="26f2b-129">Совместный доступ к сайтам Yammer</span><span class="sxs-lookup"><span data-stu-id="26f2b-129">Yammer Site Sharing</span></span>
    
- <span data-ttu-id="26f2b-130">Azure Backup</span><span class="sxs-lookup"><span data-stu-id="26f2b-130">Azure Backup</span></span>
    
<span data-ttu-id="26f2b-131">Подробные сведения о каждом из этих вариантов облачного хранилища см. в статье [Решения, не требующие сборки](move-in-ready.md).</span><span class="sxs-lookup"><span data-stu-id="26f2b-131">For the details of each of these cloud storage options, see [Move-in ready](move-in-ready.md).</span></span>
  
### <a name="some-assembly-required"></a><span data-ttu-id="26f2b-132">Решения, требующие сборки</span><span class="sxs-lookup"><span data-stu-id="26f2b-132">Some assembly required</span></span>

<span data-ttu-id="26f2b-133">Используйте существующие службы в качестве отправной точки для своего хранилища. Чтобы создать хранилище, вам потребуется выполнить дополнительную настройку или написать код.</span><span class="sxs-lookup"><span data-stu-id="26f2b-133">Use these existing services as a starting point for your storage solution with additional configuration or coding for a custom fit.</span></span>
  
- <span data-ttu-id="26f2b-134">Сеть доставки содержимого Azure</span><span class="sxs-lookup"><span data-stu-id="26f2b-134">Azure Content Delivery Network</span></span>
    
- <span data-ttu-id="26f2b-135">Службы мультимедиа Azure</span><span class="sxs-lookup"><span data-stu-id="26f2b-135">Azure Media Services</span></span>
    
- <span data-ttu-id="26f2b-136">HdInsight</span><span class="sxs-lookup"><span data-stu-id="26f2b-136">HdInsight</span></span>
    
- <span data-ttu-id="26f2b-137">Кэш Redis для Azure</span><span class="sxs-lookup"><span data-stu-id="26f2b-137">Azure Redis Cache</span></span>
    
- <span data-ttu-id="26f2b-138">База данных SQL Azure</span><span class="sxs-lookup"><span data-stu-id="26f2b-138">Azure SQL Database</span></span>
    
- <span data-ttu-id="26f2b-139">SQL Server на виртуальной машине Azure</span><span class="sxs-lookup"><span data-stu-id="26f2b-139">SQL Server on an Azure VM</span></span>
    
- <span data-ttu-id="26f2b-140">Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="26f2b-140">Azure Cosmos DB</span></span>
    
- <span data-ttu-id="26f2b-141">StorSimple</span><span class="sxs-lookup"><span data-stu-id="26f2b-141">StorSimple</span></span>
    
- <span data-ttu-id="26f2b-142">Хранилище данных SQL Azure</span><span class="sxs-lookup"><span data-stu-id="26f2b-142">Azure SQL Data Warehouse</span></span>
    
- <span data-ttu-id="26f2b-143">Azure Data Lake Store</span><span class="sxs-lookup"><span data-stu-id="26f2b-143">Azure Data Lake Store</span></span>
    
<span data-ttu-id="26f2b-144">Подробные сведения о каждом из этих вариантов облачного хранилища см. в статье [Решения, требующие сборки](some-assembly-required.md).</span><span class="sxs-lookup"><span data-stu-id="26f2b-144">For the details of each of these cloud storage options, see [Some assembly required](some-assembly-required.md).</span></span>
  
### <a name="build-from-the-ground-up"></a><span data-ttu-id="26f2b-145">Создание с чистого листа</span><span class="sxs-lookup"><span data-stu-id="26f2b-145">Build from the ground up</span></span>

<span data-ttu-id="26f2b-146">Используя эти стандартные блоки хранилища и написав необходимый код, вы можете создать собственное хранилище или приложения "с нуля".</span><span class="sxs-lookup"><span data-stu-id="26f2b-146">Use these storage building blocks, along with coding, to create your own storage solution or apps from scratch.</span></span>
  
- <span data-ttu-id="26f2b-147">Служба хранилища Azure (файлы)</span><span class="sxs-lookup"><span data-stu-id="26f2b-147">Azure Storage (files)</span></span>
    
- <span data-ttu-id="26f2b-148">Служба хранилища Azure (большие двоичные объекты)</span><span class="sxs-lookup"><span data-stu-id="26f2b-148">Azure Storage (blobs)</span></span>
    
- <span data-ttu-id="26f2b-149">Служба хранилища Azure (очереди)</span><span class="sxs-lookup"><span data-stu-id="26f2b-149">Azure Storage (queues)</span></span>
    
- <span data-ttu-id="26f2b-150">Служба хранилища Azure (таблицы)</span><span class="sxs-lookup"><span data-stu-id="26f2b-150">Azure Storage (tables)</span></span>
    
<span data-ttu-id="26f2b-151">Подробные сведения о каждом из этих вариантов облачного хранилища см. в статье [Создание с чистого листа](build-from-the-ground-up.md).</span><span class="sxs-lookup"><span data-stu-id="26f2b-151">For the details of each of these cloud storage options, see [Build from the ground up](build-from-the-ground-up.md).</span></span>
  
## <a name="key-storage-scenarios"></a><span data-ttu-id="26f2b-152">Основные сценарии использования хранилища</span><span class="sxs-lookup"><span data-stu-id="26f2b-152">Key storage scenarios</span></span>

<span data-ttu-id="26f2b-153">Ниже перечислены основные сценарии, в которых требуется облачное хранилище.</span><span class="sxs-lookup"><span data-stu-id="26f2b-153">Here are the key scenarios that require cloud-based storage:</span></span>
  
- <span data-ttu-id="26f2b-154">Кэширование данных</span><span class="sxs-lookup"><span data-stu-id="26f2b-154">Cache data</span></span>
    
    <span data-ttu-id="26f2b-155">Чтобы ускорить доступ к часто используемым данным, разместите их в быстродействующем кэше.</span><span class="sxs-lookup"><span data-stu-id="26f2b-155">Accelerate access to commonly used data by storing it in a high-speed cache.</span></span>
    
- <span data-ttu-id="26f2b-156">Совместная работа с участниками группы</span><span class="sxs-lookup"><span data-stu-id="26f2b-156">Collaborate with team members</span></span>
    
    <span data-ttu-id="26f2b-157">Вы можете предоставлять разрешения на доступ к данным в облачном хранилище большому количеству пользователей.</span><span class="sxs-lookup"><span data-stu-id="26f2b-157">Grant permission to multiple users to allow access to data in cloud storage.</span></span>
    
- <span data-ttu-id="26f2b-158">Управление данными</span><span class="sxs-lookup"><span data-stu-id="26f2b-158">Manage data</span></span>
    
    <span data-ttu-id="26f2b-159">Храните, перемещайте или удаляйте большие объемы внутренних или внешних данных.</span><span class="sxs-lookup"><span data-stu-id="26f2b-159">Store, move, or delete internal or external bulk data.</span></span>
    
- <span data-ttu-id="26f2b-160">Управление исходным кодом</span><span class="sxs-lookup"><span data-stu-id="26f2b-160">Manage source code</span></span>
    
    <span data-ttu-id="26f2b-161">Отправляйте файлы кода приложений, ведите совместную работу над ними и запускайте их в облаке.</span><span class="sxs-lookup"><span data-stu-id="26f2b-161">Upload, collaborate, and run application code files in the cloud.</span></span>
    
- <span data-ttu-id="26f2b-162">Резервное копирование файлов</span><span class="sxs-lookup"><span data-stu-id="26f2b-162">Backup files</span></span>
    
    <span data-ttu-id="26f2b-163">Храните копии внутренних и внешних данных за пределами своей организации в нескольких облачных расположениях.</span><span class="sxs-lookup"><span data-stu-id="26f2b-163">Store copies of internal or external data offsite in multiple cloud locations.</span></span>
    
- <span data-ttu-id="26f2b-164">Публикация информации, передаваемой внутри компании</span><span class="sxs-lookup"><span data-stu-id="26f2b-164">Publish company communications</span></span>
    
    <span data-ttu-id="26f2b-165">Создайте единую точку публикации для внутренних или внешних сообщений.</span><span class="sxs-lookup"><span data-stu-id="26f2b-165">Create a single point of publication for internal or external messages.</span></span>
    
- <span data-ttu-id="26f2b-166">Распространение миллионов событий</span><span class="sxs-lookup"><span data-stu-id="26f2b-166">Distribute millions of events</span></span>
    
    <span data-ttu-id="26f2b-167">Создайте хранилище для приема данных телеметрии с веб-сайтов и устройств, а также из приложений.</span><span class="sxs-lookup"><span data-stu-id="26f2b-167">Create storage for telemetry ingestion from websites, apps, and devices.</span></span>
    
- <span data-ttu-id="26f2b-168">Предоставление видеоматериалов и управление ими</span><span class="sxs-lookup"><span data-stu-id="26f2b-168">Manage/serve videos</span></span>
    
    <span data-ttu-id="26f2b-169">Храните и показывайте видеоконтент клиентам или пользователям из организации.</span><span class="sxs-lookup"><span data-stu-id="26f2b-169">Store and serve video content to customers or organization users.</span></span>
    
## <a name="next-step"></a><span data-ttu-id="26f2b-170">Следующее действие</span><span class="sxs-lookup"><span data-stu-id="26f2b-170">Next step</span></span>

<span data-ttu-id="26f2b-171">Ознакомьтесь со службами облачного хранения [Решения, не требующие сборки](move-in-ready.md).</span><span class="sxs-lookup"><span data-stu-id="26f2b-171">Review the [Move-in ready](move-in-ready.md) cloud storage options.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="26f2b-172">См. также</span><span class="sxs-lookup"><span data-stu-id="26f2b-172">See Also</span></span>

[<span data-ttu-id="26f2b-173">Облачные хранилища Майкрософт для корпоративных архитекторов</span><span class="sxs-lookup"><span data-stu-id="26f2b-173">Microsoft Cloud Storage for Enterprise Architects</span></span>](microsoft-cloud-storage-for-enterprise-architects.md)
  
[<span data-ttu-id="26f2b-174">Ресурсы для администраторов, посвященные архитектуре Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="26f2b-174">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="26f2b-175">Стратегия Enterprise Cloud корпорации Майкрософт: ресурсы для лиц, принимающих решения в области ИТ</span><span class="sxs-lookup"><span data-stu-id="26f2b-175">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)


