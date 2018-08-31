---
title: Разработка хранилища для Microsoft Cloud
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 7e511118-1b75-413a-b959-ad0d3ffc9516
description: Сводка. Узнайте, зачем вам облачное хранилище, а также ознакомьтесь со списком доступных облачных хранилищ (Майкрософт) и основных сценариев хранения.
ms.openlocfilehash: d96992d63115095dd6a1b7277886d0a4bb2bc02f
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915234"
---
# <a name="designing-storage-for-the-microsoft-cloud"></a><span data-ttu-id="7f446-103">Разработка хранилища для Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="7f446-103">Designing storage for the Microsoft cloud</span></span>

 <span data-ttu-id="7f446-104">**Сводка.** Узнайте, зачем вам облачное хранилище, а также ознакомьтесь со списком доступных облачных хранилищ (Майкрософт) и основных сценариев хранения.</span><span class="sxs-lookup"><span data-stu-id="7f446-104">**Summary:** Understand why you need cloud storage and review the list of Microsoft's cloud storage options and the key storage scenarios.</span></span>
  
<span data-ttu-id="7f446-105">Интеграция хранилища с облачными службами (Майкрософт) предоставляет вам доступ к широкому ассортименту служб и облачных платформ.</span><span class="sxs-lookup"><span data-stu-id="7f446-105">Integrating your storage with Microsoft cloud services gives you access to a broad range of services and cloud platform options.</span></span>
  
## <a name="why-cloud-storage"></a><span data-ttu-id="7f446-106">Зачем использовать облачное хранилище?</span><span class="sxs-lookup"><span data-stu-id="7f446-106">Why cloud storage?</span></span>

<span data-ttu-id="7f446-107">Есть две основные причины для использования облачного хранилища.</span><span class="sxs-lookup"><span data-stu-id="7f446-107">There are two key reasons to use cloud storage.</span></span>
  
1. <span data-ttu-id="7f446-108">Быстрый выход на рынок:</span><span class="sxs-lookup"><span data-stu-id="7f446-108">Speed to market:</span></span>
    
  - <span data-ttu-id="7f446-109">быстродействующая конфигурация, позволяющая обеспечить высокую доступность и аварийное восстановление;</span><span class="sxs-lookup"><span data-stu-id="7f446-109">Faster configuration for high availability and disaster recovery</span></span>
    
  - <span data-ttu-id="7f446-110">не нужно приобретать оборудование для хранилища;</span><span class="sxs-lookup"><span data-stu-id="7f446-110">No storage hardware to purchase</span></span>
    
  - <span data-ttu-id="7f446-111">в облачных предложениях Майкрософт имеются встроенные вспомогательные средства;</span><span class="sxs-lookup"><span data-stu-id="7f446-111">Built-in plumbing provided by Microsoft's cloud offerings</span></span>
    
  - <span data-ttu-id="7f446-112">доступность по всему миру.</span><span class="sxs-lookup"><span data-stu-id="7f446-112">Available from anywhere in the world</span></span>
    
2. <span data-ttu-id="7f446-113">Снижение затрат на обслуживание:</span><span class="sxs-lookup"><span data-stu-id="7f446-113">Lower costs to maintain:</span></span>
    
  - <span data-ttu-id="7f446-114">эластичность, позволяющая масштабировать хранилище согласно вашим потребностям;</span><span class="sxs-lookup"><span data-stu-id="7f446-114">Elasticity to scale up and down your storage demands</span></span>
    
  - <span data-ttu-id="7f446-115">не нужно обслуживать или переносить оборудование хранилища;</span><span class="sxs-lookup"><span data-stu-id="7f446-115">No storage hardware to maintain or migrate</span></span>
    
  - <span data-ttu-id="7f446-116">корпорация Майкрософт предоставляет встроенные средства для обслуживания и повышения качества инфраструктуры;</span><span class="sxs-lookup"><span data-stu-id="7f446-116">Microsoft is your built-in plumber to maintain and improve infrastructure</span></span>
    
  - <span data-ttu-id="7f446-117">лучшая защита хранилища на рынке, которая постоянно совершенствуется.</span><span class="sxs-lookup"><span data-stu-id="7f446-117">Best storage security in the marketplace with ongoing improvements</span></span>
    
## <a name="microsoft-cloud-storage-options"></a><span data-ttu-id="7f446-118">Варианты облачного хранилища (Майкрософт)</span><span class="sxs-lookup"><span data-stu-id="7f446-118">Microsoft cloud storage options</span></span>

<span data-ttu-id="7f446-119">В этом разделе представлен широкий ассортимент облачных хранилищ.</span><span class="sxs-lookup"><span data-stu-id="7f446-119">To help you understand the wide variety of cloud storage options, we use a construction analogy.</span></span>
  
### <a name="move-in-ready"></a><span data-ttu-id="7f446-120">Решения, не требующие сборки</span><span class="sxs-lookup"><span data-stu-id="7f446-120">Move-in ready</span></span>

<span data-ttu-id="7f446-p101">Используйте эти заранее подготовленные пакеты решений, объединенных с существующими службами. Они готовы к работе и практически не требуют настройки.</span><span class="sxs-lookup"><span data-stu-id="7f446-p101">Use these prepackaged solutions that are bundled with existing services. Use immediately and with minimal configuration.</span></span>
  
- <span data-ttu-id="7f446-123">Office 365</span><span class="sxs-lookup"><span data-stu-id="7f446-123">Office 365</span></span>
    
- <span data-ttu-id="7f446-124">Microsoft Intune</span><span class="sxs-lookup"><span data-stu-id="7f446-124">Microsoft Intune</span></span>
    
- <span data-ttu-id="7f446-125">OneDrive для бизнеса</span><span class="sxs-lookup"><span data-stu-id="7f446-125">OneDrive for Business</span></span>
    
- <span data-ttu-id="7f446-126">Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="7f446-126">Dynamics 365</span></span>
    
- <span data-ttu-id="7f446-127">Visual Studio Team Services</span><span class="sxs-lookup"><span data-stu-id="7f446-127">Visual Studio Team Services</span></span>
    
- <span data-ttu-id="7f446-128">Azure Site Recovery</span><span class="sxs-lookup"><span data-stu-id="7f446-128">Azure Site Recovery</span></span>
    
- <span data-ttu-id="7f446-129">Совместный доступ к сайтам Yammer</span><span class="sxs-lookup"><span data-stu-id="7f446-129">Yammer Site Sharing</span></span>
    
- <span data-ttu-id="7f446-130">Azure Backup</span><span class="sxs-lookup"><span data-stu-id="7f446-130">Azure Backup</span></span>
    
<span data-ttu-id="7f446-131">Подробные сведения о каждом из этих вариантов облачного хранилища см. в статье [Решения, не требующие сборки](move-in-ready.md).</span><span class="sxs-lookup"><span data-stu-id="7f446-131">For the details of each of these cloud storage options, see [Move-in ready](move-in-ready.md).</span></span>
  
### <a name="some-assembly-required"></a><span data-ttu-id="7f446-132">Решения, требующие сборки</span><span class="sxs-lookup"><span data-stu-id="7f446-132">Some assembly required</span></span>

<span data-ttu-id="7f446-133">Используйте существующие службы в качестве отправной точки для своего хранилища. Чтобы создать хранилище, вам потребуется выполнить дополнительную настройку или написать код.</span><span class="sxs-lookup"><span data-stu-id="7f446-133">Use these existing services as a starting point for your storage solution with additional configuration or coding for a custom fit.</span></span>
  
- <span data-ttu-id="7f446-134">Сеть доставки содержимого Azure</span><span class="sxs-lookup"><span data-stu-id="7f446-134">Azure Content Delivery Network</span></span>
    
- <span data-ttu-id="7f446-135">Службы мультимедиа Azure</span><span class="sxs-lookup"><span data-stu-id="7f446-135">Azure Media Services</span></span>
    
- <span data-ttu-id="7f446-136">HdInsight</span><span class="sxs-lookup"><span data-stu-id="7f446-136">HdInsight</span></span>
    
- <span data-ttu-id="7f446-137">Кэш Redis для Azure</span><span class="sxs-lookup"><span data-stu-id="7f446-137">Azure Redis Cache</span></span>
    
- <span data-ttu-id="7f446-138">База данных SQL Azure</span><span class="sxs-lookup"><span data-stu-id="7f446-138">Azure SQL Database</span></span>
    
- <span data-ttu-id="7f446-139">SQL Server на виртуальной машине Azure</span><span class="sxs-lookup"><span data-stu-id="7f446-139">SQL Server on an Azure VM</span></span>
    
- <span data-ttu-id="7f446-140">Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="7f446-140">Azure Cosmos DB</span></span>
    
- <span data-ttu-id="7f446-141">StorSimple</span><span class="sxs-lookup"><span data-stu-id="7f446-141">StorSimple</span></span>
    
- <span data-ttu-id="7f446-142">Хранилище данных SQL Azure</span><span class="sxs-lookup"><span data-stu-id="7f446-142">Azure SQL Data Warehouse</span></span>
    
- <span data-ttu-id="7f446-143">Azure Data Lake Store</span><span class="sxs-lookup"><span data-stu-id="7f446-143">Azure Data Lake Store</span></span>
    
<span data-ttu-id="7f446-144">Подробные сведения о каждом из этих вариантов облачного хранилища см. в статье [Решения, требующие сборки](some-assembly-required.md).</span><span class="sxs-lookup"><span data-stu-id="7f446-144">For the details of each of these cloud storage options, see [Some assembly required](some-assembly-required.md).</span></span>
  
### <a name="build-from-the-ground-up"></a><span data-ttu-id="7f446-145">Создание с чистого листа</span><span class="sxs-lookup"><span data-stu-id="7f446-145">Build from the ground up</span></span>

<span data-ttu-id="7f446-146">Используя эти стандартные блоки хранилища и написав необходимый код, вы можете создать собственное хранилище или приложения "с нуля".</span><span class="sxs-lookup"><span data-stu-id="7f446-146">Use these storage building blocks, along with coding, to create your own storage solution or apps from scratch.</span></span>
  
- <span data-ttu-id="7f446-147">Служба хранилища Azure (файлы)</span><span class="sxs-lookup"><span data-stu-id="7f446-147">Azure Storage (files)</span></span>
    
- <span data-ttu-id="7f446-148">Служба хранилища Azure (большие двоичные объекты)</span><span class="sxs-lookup"><span data-stu-id="7f446-148">Azure Storage (blobs)</span></span>
    
- <span data-ttu-id="7f446-149">Служба хранилища Azure (очереди)</span><span class="sxs-lookup"><span data-stu-id="7f446-149">Azure Storage (queues)</span></span>
    
- <span data-ttu-id="7f446-150">Служба хранилища Azure (таблицы)</span><span class="sxs-lookup"><span data-stu-id="7f446-150">Azure Storage (tables)</span></span>
    
<span data-ttu-id="7f446-151">Подробные сведения о каждом из этих вариантов облачного хранилища см. в статье [Создание с чистого листа](build-from-the-ground-up.md).</span><span class="sxs-lookup"><span data-stu-id="7f446-151">For the details of each of these cloud storage options, see [Build from the ground up](build-from-the-ground-up.md).</span></span>
  
## <a name="key-storage-scenarios"></a><span data-ttu-id="7f446-152">Основные сценарии использования хранилища</span><span class="sxs-lookup"><span data-stu-id="7f446-152">Key storage scenarios</span></span>

<span data-ttu-id="7f446-153">Ниже перечислены основные сценарии, в которых требуется облачное хранилище.</span><span class="sxs-lookup"><span data-stu-id="7f446-153">Here are the key scenarios that require cloud-based storage:</span></span>
  
- <span data-ttu-id="7f446-154">Кэширование данных</span><span class="sxs-lookup"><span data-stu-id="7f446-154">Cache data</span></span>
    
    <span data-ttu-id="7f446-155">Чтобы ускорить доступ к часто используемым данным, разместите их в быстродействующем кэше.</span><span class="sxs-lookup"><span data-stu-id="7f446-155">Accelerate access to commonly used data by storing it in a high-speed cache.</span></span>
    
- <span data-ttu-id="7f446-156">Совместная работа с участниками группы</span><span class="sxs-lookup"><span data-stu-id="7f446-156">Collaborate with team members</span></span>
    
    <span data-ttu-id="7f446-157">Вы можете предоставлять разрешения на доступ к данным в облачном хранилище большому количеству пользователей.</span><span class="sxs-lookup"><span data-stu-id="7f446-157">Grant permission to multiple users to allow access to data in cloud storage.</span></span>
    
- <span data-ttu-id="7f446-158">Управление данными</span><span class="sxs-lookup"><span data-stu-id="7f446-158">Manage data</span></span>
    
    <span data-ttu-id="7f446-159">Храните, перемещайте или удаляйте большие объемы внутренних или внешних данных.</span><span class="sxs-lookup"><span data-stu-id="7f446-159">Store, move, or delete internal or external bulk data.</span></span>
    
- <span data-ttu-id="7f446-160">Управление исходным кодом</span><span class="sxs-lookup"><span data-stu-id="7f446-160">Manage source code</span></span>
    
    <span data-ttu-id="7f446-161">Отправляйте файлы кода приложений, ведите совместную работу над ними и запускайте их в облаке.</span><span class="sxs-lookup"><span data-stu-id="7f446-161">Upload, collaborate, and run application code files in the cloud.</span></span>
    
- <span data-ttu-id="7f446-162">Резервное копирование файлов</span><span class="sxs-lookup"><span data-stu-id="7f446-162">Backup files</span></span>
    
    <span data-ttu-id="7f446-163">Храните копии внутренних и внешних данных за пределами своей организации в нескольких облачных расположениях.</span><span class="sxs-lookup"><span data-stu-id="7f446-163">Store copies of internal or external data offsite in multiple cloud locations.</span></span>
    
- <span data-ttu-id="7f446-164">Публикация информации, передаваемой внутри компании</span><span class="sxs-lookup"><span data-stu-id="7f446-164">Publish company communications</span></span>
    
    <span data-ttu-id="7f446-165">Создайте единую точку публикации для внутренних или внешних сообщений.</span><span class="sxs-lookup"><span data-stu-id="7f446-165">Create a single point of publication for internal or external messages.</span></span>
    
- <span data-ttu-id="7f446-166">Распространение миллионов событий</span><span class="sxs-lookup"><span data-stu-id="7f446-166">Distribute millions of events</span></span>
    
    <span data-ttu-id="7f446-167">Создайте хранилище для приема данных телеметрии с веб-сайтов и устройств, а также из приложений.</span><span class="sxs-lookup"><span data-stu-id="7f446-167">Create storage for telemetry ingestion from websites, apps, and devices.</span></span>
    
- <span data-ttu-id="7f446-168">Предоставление видеоматериалов и управление ими</span><span class="sxs-lookup"><span data-stu-id="7f446-168">Manage/serve videos</span></span>
    
    <span data-ttu-id="7f446-169">Храните и показывайте видеоконтент клиентам или пользователям из организации.</span><span class="sxs-lookup"><span data-stu-id="7f446-169">Store and serve video content to customers or organization users.</span></span>
    
## <a name="next-step"></a><span data-ttu-id="7f446-170">Следующее действие</span><span class="sxs-lookup"><span data-stu-id="7f446-170">Next step</span></span>

<span data-ttu-id="7f446-171">Ознакомьтесь со службами облачного хранения [Решения, не требующие сборки](move-in-ready.md).</span><span class="sxs-lookup"><span data-stu-id="7f446-171">Review the [Move-in ready](move-in-ready.md) cloud storage options.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="7f446-172">См. также</span><span class="sxs-lookup"><span data-stu-id="7f446-172">See Also</span></span>

[<span data-ttu-id="7f446-173">Облачные хранилища Майкрософт для корпоративных архитекторов</span><span class="sxs-lookup"><span data-stu-id="7f446-173">Microsoft Cloud Storage for Enterprise Architects</span></span>](microsoft-cloud-storage-for-enterprise-architects.md)
  
[<span data-ttu-id="7f446-174">Ресурсы для администраторов, посвященные архитектуре Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="7f446-174">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="7f446-175">Стратегия Enterprise Cloud корпорации Майкрософт: ресурсы для лиц, принимающих решения в области ИТ</span><span class="sxs-lookup"><span data-stu-id="7f446-175">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)


