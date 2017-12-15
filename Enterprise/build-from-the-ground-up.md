---
title: "Создание с чистого листа"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Top
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: 84348d0c-d9d1-4a98-9b99-8433f9b70e45
description: "Сводка: Получите подробные сведения об набор облачных хранилища стандартные блоки, которые можно использовать для создания службы хранилища или решения."
ms.openlocfilehash: 18aa8cb7fa0dda05302a88487dcc69bdbcb174d5
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2017
---
# <a name="build-from-the-ground-up"></a><span data-ttu-id="2efdf-103">Создание с чистого листа</span><span class="sxs-lookup"><span data-stu-id="2efdf-103">Build from the ground up</span></span>

 <span data-ttu-id="2efdf-104">**Сводка:** Получите подробные сведения об набор облачных хранилища стандартные блоки, которые можно использовать для создания службы хранилища или решения.</span><span class="sxs-lookup"><span data-stu-id="2efdf-104">**Summary:** Get the details on the set of cloud storage building blocks that you can use to create your own storage service or solution.</span></span>
  
<span data-ttu-id="2efdf-105">Что можно или нужно в случае, если вы создаете решения для хранения с чистого листа:</span><span class="sxs-lookup"><span data-stu-id="2efdf-105">"Build from the ground up" storage solutions:</span></span>
  
- <span data-ttu-id="2efdf-106">Позволяют создавать свои собственные решения хранения с нуля.</span><span class="sxs-lookup"><span data-stu-id="2efdf-106">Allow you to create your own storage solution from scratch.</span></span> 
    
- <span data-ttu-id="2efdf-107">Требуется программирование с использованием API-интерфейсы REST.</span><span class="sxs-lookup"><span data-stu-id="2efdf-107">Requires programming using the REST APIs.</span></span>
    
- <span data-ttu-id="2efdf-108">Предоставьте максимум в настройке и гибкости.</span><span class="sxs-lookup"><span data-stu-id="2efdf-108">Provide the ultimate in customization and flexibility.</span></span>
    
<span data-ttu-id="2efdf-109">В следующих разделах подробно описан каждый из вариантов решений для хранения, созданных с чистого листа.</span><span class="sxs-lookup"><span data-stu-id="2efdf-109">The following sections describe the details of each "Build from the ground up" storage option.</span></span>
  
## <a name="azure-storage-files"></a><span data-ttu-id="2efdf-110">Служба хранилища Azure (файлы)</span><span class="sxs-lookup"><span data-stu-id="2efdf-110">Azure Storage (files)</span></span>

### <a name="features"></a><span data-ttu-id="2efdf-111">Возможности</span><span class="sxs-lookup"><span data-stu-id="2efdf-111">Features</span></span>

- <span data-ttu-id="2efdf-112">Более простое перемещение приложений прежних версий в облако.</span><span class="sxs-lookup"><span data-stu-id="2efdf-112">Makes it easier to move legacy applications to the cloud</span></span>
    
- <span data-ttu-id="2efdf-113">Хранилище BLOB-объектов, предпочтительное для новых приложений.</span><span class="sxs-lookup"><span data-stu-id="2efdf-113">Blob storage preferred for new applications</span></span>
    
- <span data-ttu-id="2efdf-114">Возможность подключения из виртуальной машины Azure.</span><span class="sxs-lookup"><span data-stu-id="2efdf-114">Can mount from an Azure virtual machine</span></span>
    
- <span data-ttu-id="2efdf-115">Возможность подключения локальной среды с помощью SMB 3.0.</span><span class="sxs-lookup"><span data-stu-id="2efdf-115">Can mount on-premises with SMB 3.0</span></span>
    
- <span data-ttu-id="2efdf-116">Работает с ОС Linux и Windows.</span><span class="sxs-lookup"><span data-stu-id="2efdf-116">Works with Linux and Windows</span></span>
    
- <span data-ttu-id="2efdf-117">Не поддерживает проверку подлинности на основе AD Azure или списки управления доступом (ключи хранилища Azure учетной записи проверки подлинности и авторизованные доступ к общей папке)</span><span class="sxs-lookup"><span data-stu-id="2efdf-117">Doesn't support Azure AD-based authentication or ACLs (Azure Storage account keys provide authentication and authorized access to the file share)</span></span>
    
### <a name="common-uses"></a><span data-ttu-id="2efdf-118">Стандартные варианты использования</span><span class="sxs-lookup"><span data-stu-id="2efdf-118">Common uses</span></span>

- <span data-ttu-id="2efdf-119">Перенос приложений прежних версий, зависящих от файловых ресурсов, в облако.</span><span class="sxs-lookup"><span data-stu-id="2efdf-119">Migrating legacy applications to the cloud that rely on file shares</span></span>
    
- <span data-ttu-id="2efdf-120">Совместное использование средств разработки и тестирования.</span><span class="sxs-lookup"><span data-stu-id="2efdf-120">Share development and testing tools</span></span>
    
- <span data-ttu-id="2efdf-121">Распределенные приложения могут сохранять журналы, диагностические данные и аварийные дампы.</span><span class="sxs-lookup"><span data-stu-id="2efdf-121">Distributed apps can store logs, diagnostic data, and crash dumps</span></span>
    
### <a name="key-storage-scenarios"></a><span data-ttu-id="2efdf-122">Основные сценарии использования хранилища</span><span class="sxs-lookup"><span data-stu-id="2efdf-122">Key storage scenarios</span></span>

- <span data-ttu-id="2efdf-123">Резервное копирование файлов</span><span class="sxs-lookup"><span data-stu-id="2efdf-123">Backup files</span></span>
    
### <a name="resources"></a><span data-ttu-id="2efdf-124">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="2efdf-124">Resources</span></span>

<span data-ttu-id="2efdf-125">Дополнительные сведения вы найдете [здесь](https://msdn.microsoft.com/library/azure/dn166972.aspx).</span><span class="sxs-lookup"><span data-stu-id="2efdf-125">For additional information, click [here](https://msdn.microsoft.com/library/azure/dn166972.aspx).</span></span>
  
<span data-ttu-id="2efdf-126">Сведения о ценах см. [здесь](http://azure.microsoft.com/pricing/details/storage/).</span><span class="sxs-lookup"><span data-stu-id="2efdf-126">For cost information, click [here](http://azure.microsoft.com/pricing/details/storage/).</span></span>
  
## <a name="azure-storage-blobs"></a><span data-ttu-id="2efdf-127">Служба хранилища Azure (большие двоичные объекты)</span><span class="sxs-lookup"><span data-stu-id="2efdf-127">Azure Storage (blobs)</span></span>

### <a name="features"></a><span data-ttu-id="2efdf-128">Возможности</span><span class="sxs-lookup"><span data-stu-id="2efdf-128">Features</span></span>

- <span data-ttu-id="2efdf-129">Каждой учетной записи хранения может содержать до 500 ТБ (одна подписка может иметь несколько учетных записей хранилища)</span><span class="sxs-lookup"><span data-stu-id="2efdf-129">Each storage account can hold up to 500 TB (one subscription can have multiple storage accounts)</span></span>
    
- <span data-ttu-id="2efdf-130">Учетные записи хранения упорядочены в контейнеры, которые можно защитить и которые могут содержать большие двоичные объекты.</span><span class="sxs-lookup"><span data-stu-id="2efdf-130">Storage accounts are organized into containers, which can have security applied to them and can contain blobs</span></span>
    
- <span data-ttu-id="2efdf-131">Блочные BLOB-объекты оптимизированы для потоковой передачи и хранения облачных объектов размером до 200 ГБ.</span><span class="sxs-lookup"><span data-stu-id="2efdf-131">Block blobs are optimized for streaming and storing cloud objects, up to 200 GB in size</span></span>
    
- <span data-ttu-id="2efdf-132">Страничные BLOB-объекты оптимизированы для представления дисков PaaS и операций произвольной записи и могут иметь размер до 1 ТБ.</span><span class="sxs-lookup"><span data-stu-id="2efdf-132">Page blobs are optimized for representing PaaS disks and supporting random writes, up to 1 TB in size</span></span>
    
- <span data-ttu-id="2efdf-133">Большие двоичные объекты добавления оптимизированы для операций добавления и могут иметь размер до 195 ГБ.</span><span class="sxs-lookup"><span data-stu-id="2efdf-133">Append blobs are optimized for append operations, up to 195 GB</span></span>
    
- <span data-ttu-id="2efdf-134">Хранилище класса Premium имеет более высокие показатели количества операций ввода-вывода в секунду из-за использования SSD.</span><span class="sxs-lookup"><span data-stu-id="2efdf-134">Premium Storage provides faster IOPS through SSD storage</span></span>
    
### <a name="common-uses"></a><span data-ttu-id="2efdf-135">Стандартные варианты использования</span><span class="sxs-lookup"><span data-stu-id="2efdf-135">Common uses</span></span>

- <span data-ttu-id="2efdf-136">Резервные копии файлов, компьютеров, баз данных и устройств изображения и текст для веб-приложений</span><span class="sxs-lookup"><span data-stu-id="2efdf-136">Backups of files, computers, databases, and devices Images and text for web applications</span></span>
    
- <span data-ttu-id="2efdf-137">Данные конфигурации для облачных приложений.</span><span class="sxs-lookup"><span data-stu-id="2efdf-137">Configuration data for cloud applications</span></span>
    
- <span data-ttu-id="2efdf-138">Большие данные, например журналы и другие большие наборы данных.</span><span class="sxs-lookup"><span data-stu-id="2efdf-138">Big data, such as logs and other large datasets</span></span>
    
- <span data-ttu-id="2efdf-139">Azure использует хранилище BLOB-объектов для собственных служб, например HDInsight и дисков виртуальных машин.</span><span class="sxs-lookup"><span data-stu-id="2efdf-139">Azure uses blob storage for its own services, such as HDInsight and virtual machine disks</span></span>
    
### <a name="key-storage-scenarios"></a><span data-ttu-id="2efdf-140">Основные сценарии использования хранилища</span><span class="sxs-lookup"><span data-stu-id="2efdf-140">Key storage scenarios</span></span>

- <span data-ttu-id="2efdf-141">Управление данными.</span><span class="sxs-lookup"><span data-stu-id="2efdf-141">Manage data</span></span>
    
### <a name="resources"></a><span data-ttu-id="2efdf-142">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="2efdf-142">Resources</span></span>

<span data-ttu-id="2efdf-143">Дополнительные сведения вы найдете [здесь](https://msdn.microsoft.com/library/azure/dd179376.aspx).</span><span class="sxs-lookup"><span data-stu-id="2efdf-143">For additional information, click [here](https://msdn.microsoft.com/library/azure/dd179376.aspx).</span></span>
  
<span data-ttu-id="2efdf-144">Сведения о ценах см. [здесь](http://azure.microsoft.com/pricing/details/storage/).</span><span class="sxs-lookup"><span data-stu-id="2efdf-144">For cost information, click [here](http://azure.microsoft.com/pricing/details/storage/).</span></span>
  
## <a name="azure-storage-queues"></a><span data-ttu-id="2efdf-145">Служба хранилища Azure (очереди)</span><span class="sxs-lookup"><span data-stu-id="2efdf-145">Azure Storage (queues)</span></span>

### <a name="features"></a><span data-ttu-id="2efdf-146">Возможности</span><span class="sxs-lookup"><span data-stu-id="2efdf-146">Features</span></span>

- <span data-ttu-id="2efdf-147">Учетная запись хранения может содержать любое количество очередей.</span><span class="sxs-lookup"><span data-stu-id="2efdf-147">Storage account can contain any number of queues</span></span>
    
- <span data-ttu-id="2efdf-148">Очередь может содержать любое количество сообщений (пока учетная запись хранения не будет заполнена).</span><span class="sxs-lookup"><span data-stu-id="2efdf-148">Queue can contain any number of messages (until the storage account is full)</span></span>
    
- <span data-ttu-id="2efdf-149">Если сообщения в очереди не извлечены или не удалены приложением, они будут автоматически удалены по истечении семи дней.</span><span class="sxs-lookup"><span data-stu-id="2efdf-149">Queue messages are automatically deleted after seven days if not retrieved and deleted by an application</span></span>
    
- <span data-ttu-id="2efdf-150">Сообщения могут иметь размер до 64 КБ.</span><span class="sxs-lookup"><span data-stu-id="2efdf-150">Messages may be up to 64 KB in size</span></span>
    
- <span data-ttu-id="2efdf-151">Защита на уровне учетной записи хранения.</span><span class="sxs-lookup"><span data-stu-id="2efdf-151">Secured at storage account level</span></span>
    
- <span data-ttu-id="2efdf-152">Очереди предназначены для передачи управляющих сообщений, а не необработанных данных.</span><span class="sxs-lookup"><span data-stu-id="2efdf-152">Queues are intended to pass control messages, not raw data</span></span>
    
### <a name="common-uses"></a><span data-ttu-id="2efdf-153">Стандартные варианты использования</span><span class="sxs-lookup"><span data-stu-id="2efdf-153">Common uses</span></span>

- <span data-ttu-id="2efdf-154">Подготовка невыполненной работы для асинхронной обработки.</span><span class="sxs-lookup"><span data-stu-id="2efdf-154">Create a backlog of work to process asynchronously</span></span>
    
- <span data-ttu-id="2efdf-155">Обработка сообщений в журналах.</span><span class="sxs-lookup"><span data-stu-id="2efdf-155">Processing log messages</span></span>
    
- <span data-ttu-id="2efdf-156">Разъединение приложений.</span><span class="sxs-lookup"><span data-stu-id="2efdf-156">Decouple applications</span></span>
    
### <a name="key-storage-scenarios"></a><span data-ttu-id="2efdf-157">Основные сценарии использования хранилища</span><span class="sxs-lookup"><span data-stu-id="2efdf-157">Key storage scenarios</span></span>

- <span data-ttu-id="2efdf-158">Распределение событий.</span><span class="sxs-lookup"><span data-stu-id="2efdf-158">Distribute events</span></span>
    
### <a name="resources"></a><span data-ttu-id="2efdf-159">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="2efdf-159">Resources</span></span>

<span data-ttu-id="2efdf-160">Дополнительные сведения вы найдете [здесь](https://msdn.microsoft.com/library/azure/dd179353.aspx).</span><span class="sxs-lookup"><span data-stu-id="2efdf-160">For additional information, click [here](https://msdn.microsoft.com/library/azure/dd179353.aspx).</span></span>
  
<span data-ttu-id="2efdf-161">Сведения о ценах см. [здесь](http://azure.microsoft.com/pricing/details/storage/).</span><span class="sxs-lookup"><span data-stu-id="2efdf-161">For cost information, click [here](http://azure.microsoft.com/pricing/details/storage/).</span></span>
  
## <a name="azure-storage-tables"></a><span data-ttu-id="2efdf-162">Служба хранилища Azure (таблицы)</span><span class="sxs-lookup"><span data-stu-id="2efdf-162">Azure Storage (tables)</span></span>

### <a name="features"></a><span data-ttu-id="2efdf-163">Возможности</span><span class="sxs-lookup"><span data-stu-id="2efdf-163">Features</span></span>

- <span data-ttu-id="2efdf-164">Решение лучше всего подходит для частично структурированных наборов данных.</span><span class="sxs-lookup"><span data-stu-id="2efdf-164">Best for semi-structured datasets</span></span>
    
- <span data-ttu-id="2efdf-165">Обычно требует более низких затрат по сравнению с традиционными SQL.</span><span class="sxs-lookup"><span data-stu-id="2efdf-165">Typically lower cost than traditional SQL</span></span>
    
- <span data-ttu-id="2efdf-166">Очень быстрый интерфейс, если запрос для ключа медленно, если запрос для значения</span><span class="sxs-lookup"><span data-stu-id="2efdf-166">Very fast if querying for key, slow if querying for value</span></span>
    
- <span data-ttu-id="2efdf-167">Широкие возможности масштабирования; любое количество таблиц вплоть до максимального объема дискового пространства учетной записи хранения.</span><span class="sxs-lookup"><span data-stu-id="2efdf-167">Massively scalable; any amount of tables up to the limits of the storage account</span></span>
    
- <span data-ttu-id="2efdf-168">Доступ через REST API, ограниченный протокол oData, .NET.</span><span class="sxs-lookup"><span data-stu-id="2efdf-168">Accessible through REST API, limited oData protocol, .NET</span></span>
    
- <span data-ttu-id="2efdf-169">Значения должны быть сериализованы.</span><span class="sxs-lookup"><span data-stu-id="2efdf-169">Values must be serialized</span></span>
    
### <a name="common-uses"></a><span data-ttu-id="2efdf-170">Стандартные варианты использования</span><span class="sxs-lookup"><span data-stu-id="2efdf-170">Common uses</span></span>

- <span data-ttu-id="2efdf-171">Данные пользователей для веб-приложений.</span><span class="sxs-lookup"><span data-stu-id="2efdf-171">User data for web applications</span></span>
    
- <span data-ttu-id="2efdf-172">Адресные книги.</span><span class="sxs-lookup"><span data-stu-id="2efdf-172">Address books</span></span>
    
- <span data-ttu-id="2efdf-173">Сведения об устройствах.</span><span class="sxs-lookup"><span data-stu-id="2efdf-173">Device information</span></span>
    
### <a name="key-storage-scenarios"></a><span data-ttu-id="2efdf-174">Основные сценарии использования хранилища</span><span class="sxs-lookup"><span data-stu-id="2efdf-174">Key storage scenarios</span></span>

- <span data-ttu-id="2efdf-175">Управление данными.</span><span class="sxs-lookup"><span data-stu-id="2efdf-175">Manage data</span></span>
    
### <a name="resources"></a><span data-ttu-id="2efdf-176">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="2efdf-176">Resources</span></span>

<span data-ttu-id="2efdf-177">Дополнительные сведения вы найдете [здесь](https://msdn.microsoft.com/library/azure/dd179463.aspx).</span><span class="sxs-lookup"><span data-stu-id="2efdf-177">For additional information, click [here](https://msdn.microsoft.com/library/azure/dd179463.aspx).</span></span>
  
<span data-ttu-id="2efdf-178">Сведения о ценах см. [здесь](http://azure.microsoft.com/pricing/details/storage/).</span><span class="sxs-lookup"><span data-stu-id="2efdf-178">For cost information, click [here](http://azure.microsoft.com/pricing/details/storage/).</span></span>
  
## <a name="microsoft-azure-storage-recommendations"></a><span data-ttu-id="2efdf-179">Рекомендации по службе хранилища Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="2efdf-179">Microsoft Azure Storage recommendations</span></span>

<span data-ttu-id="2efdf-180">Когда вы создаете свое специальное решение для хранения с использованием службы хранилища Azure, помните об этом:</span><span class="sxs-lookup"><span data-stu-id="2efdf-180">When designing your custom storage solution with Azure Storage, keep the following in mind:</span></span>
  
- <span data-ttu-id="2efdf-181">Для увеличения масштабируемости, дискового пространства (более 100 ТБ) или пропускной способности (более 5000 операций в секунду) используйте несколько учетных записей хранения.</span><span class="sxs-lookup"><span data-stu-id="2efdf-181">Leverage multiple storage accounts for greater scalability, either for increased size (> 100 TB) or for more throughput (> 5,000 operations per second).</span></span>
    
- <span data-ttu-id="2efdf-182">Запланируйте возможность добавления дополнительных учетных записей хранения путем изменения конфигурации, а не кода.</span><span class="sxs-lookup"><span data-stu-id="2efdf-182">Design the ability for adding additional storage accounts as a configuration change, not as a code change.</span></span>
    
- <span data-ttu-id="2efdf-183">Тщательно выберите функции секционирования для хранилища таблиц, чтобы достичь необходимого уровня производительности при вставке данных и обработке запросов.</span><span class="sxs-lookup"><span data-stu-id="2efdf-183">Carefully select partitioning functions for table storage to enable the desired scale in terms of insert and query performance.</span></span>
    
- <span data-ttu-id="2efdf-184">Выбирайте короткие имена столбцов для свойств таблиц, так как метаданные (имена свойств) хранятся в самих таблицах (имена столбцов включаются в данные строк, размер которых не должен превышать 1 МБ).</span><span class="sxs-lookup"><span data-stu-id="2efdf-184">Choose short column names for table properties as the metadata (property names) are stored in-band (the column names also count towards the maximum row size of 1 MB).</span></span>
    
- <span data-ttu-id="2efdf-185">По возможности используйте пакетные операции в хранилище.</span><span class="sxs-lookup"><span data-stu-id="2efdf-185">When possible, batch operations into storage.</span></span>
    
- <span data-ttu-id="2efdf-186">Выполняйте агрессивное кэширование информации, содержащейся в базе данных конфигурации, добавляя ее в распределенный кэш.</span><span class="sxs-lookup"><span data-stu-id="2efdf-186">Aggressively cache information in the configuration database into a distributed cache.</span></span>
    
- <span data-ttu-id="2efdf-187">Если производительность или надежность приложения зависит от доступности определенного сегмента данных в кэше, ваше приложение должно отклонять входящие запросы до тех пор, пока кэш не будет повторно заполнен.</span><span class="sxs-lookup"><span data-stu-id="2efdf-187">If application performance or reliability is dependent on having a certain segment of data available in the cache, your application should refuse incoming requests until the cache has been pre-populated.</span></span>
    
- <span data-ttu-id="2efdf-188">Сегментируйте данные по вертикали (по таблицам) либо по горизонтали (разбивайте таблицы на несколько сегментов), чтобы распределить нагрузку в нескольких базах данных.</span><span class="sxs-lookup"><span data-stu-id="2efdf-188">Partition the data in either vertically (by table) or horizontally (segment table across multiple shards) to spread the load across multiple databases.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="2efdf-189">See Also</span><span class="sxs-lookup"><span data-stu-id="2efdf-189">See Also</span></span>

[<span data-ttu-id="2efdf-190">Облачные хранилища Майкрософт для корпоративных архитекторов</span><span class="sxs-lookup"><span data-stu-id="2efdf-190">Microsoft Cloud Storage for Enterprise Architects</span></span>](microsoft-cloud-storage-for-enterprise-architects.md)
  
[<span data-ttu-id="2efdf-191">Ресурсы для администраторов, посвященные архитектуре Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="2efdf-191">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="2efdf-192">Стратегия Enterprise Cloud корпорации Майкрософт: ресурсы для лиц, принимающих решения в области ИТ</span><span class="sxs-lookup"><span data-stu-id="2efdf-192">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



