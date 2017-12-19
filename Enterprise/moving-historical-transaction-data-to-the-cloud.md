---
title: "Перемещение в облако транзакционных данных за прошлые периоды"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: 3e9c405a-415b-4584-aa7e-f2489299c457
description: "Сводка. Статья о том, как корпорация Contoso внедрила базу данных Stretch на SQL Server, чтобы снизить необходимость в локальных хранилищах данных и сократить ежедневные производственные затраты."
ms.openlocfilehash: f1a44a14da49c394974755f7c557013717c4ccef
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2017
---
# <a name="moving-historical-transaction-data-to-the-cloud"></a><span data-ttu-id="ae979-103">Перемещение в облако транзакционных данных за прошлые периоды</span><span class="sxs-lookup"><span data-stu-id="ae979-103">Moving historical transaction data to the cloud</span></span>

 <span data-ttu-id="ae979-104">**Сводка.** Статья о том, как корпорация Contoso внедрила базу данных Stretch на SQL Server, чтобы снизить необходимость в локальных хранилищах данных и сократить ежедневные производственные затраты.</span><span class="sxs-lookup"><span data-stu-id="ae979-104">**Summary:** How Contoso implemented SQL Server stretch database to reduce its on-premises data storage needs and daily running costs.</span></span>
  
<span data-ttu-id="ae979-p101">Системы хранения данных корпорации Contoso содержат большой объем статистических данных о транзакциях, чтобы обеспечить соблюдение нормативных требований, а также для проведения маркетинговых исследований и бизнес-аналитики тенденций расходования средств. Кроме того, корпорации необходимо восстанавливать архивированные данные с магнитной ленты, а этот процесс занимает много времени. Эксплуатационный срок службы оборудования в корпоративной системе хранения подходил к концу, а замена оборудования предполагала крупные затраты.</span><span class="sxs-lookup"><span data-stu-id="ae979-p101">Contoso's enterprise storage system stores a large amount of historical transaction data for adherence with regulatory requirements and for marketing research and BI analysis of spending trends. Contoso also needs to restore archived data from magnetic tape, a time-intensive process. The hardware in Contoso's enterprise storage system was nearing its end of life and replacing it would be very expensive.</span></span> 
  
<span data-ttu-id="ae979-p102">В рамках сокращения локальных центров обработки корпорация Contoso выбрала обновление до SQL Server 2016 по причине гибридной функции базы данных Stretch и ее полной интеграции с Azure. База данных Stretch позволяет корпорации перемещать "холодные" данные в таблицах из локального хранилища в облачное, освобождая место на локальном диске и сокращая расходы на обслуживание. И "горячие", и "холодные" данные находятся в одних и тех же таблицах и всегда доступны для приложений и их пользователей, а также для обслуживания, например резервного копирования и восстановления. На рис. 1 показана база данных Stretch.</span><span class="sxs-lookup"><span data-stu-id="ae979-p102">As part of its business need to scale down its on-premises datacenters, Contoso chose to upgrade to SQL Server 2016 because of the Stretch Database hybrid feature and its seamless integration with Azure. Stretch Database allows Contoso to move the cold data in its tables from on-premises to cloud storage, freeing up local disk space and reducing maintenance. Both hot and cold data are in the same tables and are always available to applications and their users and for maintenance, such as backups and restores. Figure 1 shows Stretch Database.</span></span>
  
<span data-ttu-id="ae979-112">**Рис. 1. База данных Stretch в SQL Server**</span><span class="sxs-lookup"><span data-stu-id="ae979-112">**Figure 1: SQL Server Stretch Database**</span></span>

![База данных SQL Server Stretch как гибридное решение для хранения данных](images/Contoso_Poster/StretchDB01.png)
  
<span data-ttu-id="ae979-114">На рис. 1 показано, как клиент SQL отправляет запросы T-SQL на сервер, на котором развернут сервер SQL Server 2016, перенаправляющий их в базу данных SQL Stretch Azure в Azure PaaS.</span><span class="sxs-lookup"><span data-stu-id="ae979-114">Figure 1 shows how a SQL client sends T-SQL queries to a server running SQL Server 2016, which forwards them to an Azure SQL Stretch Database in Azure PaaS.</span></span>
  
<span data-ttu-id="ae979-115">Дополнительные сведения см. в статье [База данных Stretch](https://msdn.microsoft.com/library/dn935011.aspx).</span><span class="sxs-lookup"><span data-stu-id="ae979-115">For more information, see [Stretch Database](https://msdn.microsoft.com/library/dn935011.aspx).</span></span>
  
<span data-ttu-id="ae979-116">Для перемещения статистических данных в облако корпорация Contoso использовала следующие шаги:</span><span class="sxs-lookup"><span data-stu-id="ae979-116">Contoso used these steps to move their historical data to the cloud:</span></span>
  
1. <span data-ttu-id="ae979-117">Анализ базы данных.</span><span class="sxs-lookup"><span data-stu-id="ae979-117">Analyze databases</span></span>
    
    <span data-ttu-id="ae979-p103">Был выполнен анализ таблиц в базах данных, которые они намереваются переместить в облако, и исправлены все ошибки. Новый помощник по базам данных Stretch предоставил полный обзор того, что они могут ожидать от всех функций SQL Server 2016, включая таблицы с "холодными" данными, которые могут быть перенесены.</span><span class="sxs-lookup"><span data-stu-id="ae979-p103">Performed an analysis of the tables in the databases that they intended to move to the cloud and fixed any issues. The new Stretch Database Advisor gave them a full overview of what they can expect from all features in SQL Server 2016, including which tables have cold data that could be stretched.</span></span>
    
2. <span data-ttu-id="ae979-120">Обновление</span><span class="sxs-lookup"><span data-stu-id="ae979-120">Upgrade</span></span>
    
    <span data-ttu-id="ae979-121">Существующие серверы SQL в центре обработки данных в парижском главном офисе были обновлены до SQL Server 2016.</span><span class="sxs-lookup"><span data-stu-id="ae979-121">Updated existing SQL servers in the Paris headquarters datacenter to SQL Server 2016.</span></span>
    
3. <span data-ttu-id="ae979-122">Перенос "холодных" данных в облако.</span><span class="sxs-lookup"><span data-stu-id="ae979-122">Migrate cold data to the cloud</span></span>
    
    <span data-ttu-id="ae979-p104">С помощью SQL Management Studio они определили базы данных и таблицы для переноса на экземпляры базы данных Stretch в Azure. Постепенно в фоновом режиме сервер SQL Server 2016 перенес статистические данные в базы данных Stretch в Azure.</span><span class="sxs-lookup"><span data-stu-id="ae979-p104">Using SQL Management Studio, they identified the databases to stretch and the tables to migrate to instances of Stretch Database in Azure. Over time and in the background, SQL Server 2016 moved the historical data to stretch databases in Azure.</span></span>
    
<span data-ttu-id="ae979-125">Вот итоговая конфигурация для одного сервера SQL Server 2016 в парижском главном офисе.</span><span class="sxs-lookup"><span data-stu-id="ae979-125">Here is the resulting configuration for one server running SQL Server 2016 in the Paris headquarters.</span></span>
  
<span data-ttu-id="ae979-126">**Рис. 2. Использование базы данных Stretch для сервера в центре обработки данных корпорации Contoso**</span><span class="sxs-lookup"><span data-stu-id="ae979-126">**Figure 2: Using Stretch Database for a server in Contoso's datacenter**</span></span>

![Настройка Базы данных SQL Server Stretch, выполняемая Contoso для одного компьютера с SQL Server](images/Contoso_Poster/StretchDB02.png)

  
<span data-ttu-id="ae979-128">На рис. 2 показано, как пользовательские запросы к серверу приложений в центре обработки данных Contoso превращаются в SQL-запросы, которые передаются в базу данных SQL Stretch Azure в Azure PaaS.</span><span class="sxs-lookup"><span data-stu-id="ae979-128">Figure 2 shows how user queries to an application server in Contoso's datacenter become SQL queries that are passed to an Azure SQL Stretch Database in Azure PaaS.</span></span>
  
<span data-ttu-id="ae979-p105">Пользователи обращаются к данным через существующие приложения и посредством запросов. Политики доступа остаются прежними. В будущем создание резервных копий на ленточных носителях не требуется. Техническая поддержка заключается в резервном копировании и восстановлении "горячих" данных.</span><span class="sxs-lookup"><span data-stu-id="ae979-p105">Users access the data through existing apps and queries. Access policies remain the same. Moving forward, there is no need for tape backups. Maintenance consists of backing up and restoring hot data.</span></span>
  
<span data-ttu-id="ae979-133">После внедрения базы данных Stretch в корпорации Contoso:</span><span class="sxs-lookup"><span data-stu-id="ae979-133">After implementing Stretch Database, Contoso:</span></span>
  
- <span data-ttu-id="ae979-134">На 85 % снизилась необходимость в локальных хранилищах данных.</span><span class="sxs-lookup"><span data-stu-id="ae979-134">Reduced its on-premises data storage needs by 85%.</span></span>
    
- <span data-ttu-id="ae979-135">Исчезла необходимость обновления корпоративной системы хранения и зависимость от магнитных ленточных архивов.</span><span class="sxs-lookup"><span data-stu-id="ae979-135">Made the update of the enterprise storage system and reliance on magnetic tape archives unnecessary.</span></span>
    
- <span data-ttu-id="ae979-136">Значительно снизились ежедневные производственные затраты.</span><span class="sxs-lookup"><span data-stu-id="ae979-136">Reduced its daily running costs significantly.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="ae979-137">См. также</span><span class="sxs-lookup"><span data-stu-id="ae979-137">See Also</span></span>

[<span data-ttu-id="ae979-138">Корпоративные сценарии для корпорации Contoso</span><span class="sxs-lookup"><span data-stu-id="ae979-138">Enterprise scenarios for the Contoso Corporation</span></span>](enterprise-scenarios-for-the-contoso-corporation.md)
  
[<span data-ttu-id="ae979-139">Contoso в Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="ae979-139">Contoso in the Microsoft Cloud</span></span>](contoso-in-the-microsoft-cloud.md)
  
[<span data-ttu-id="ae979-140">Ресурсы для администраторов, посвященные архитектуре Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="ae979-140">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="ae979-141">База данных Stretch</span><span class="sxs-lookup"><span data-stu-id="ae979-141">Stretch Database</span></span>](https://msdn.microsoft.com/library/dn935011.aspx)
  
[<span data-ttu-id="ae979-142">Стратегия Enterprise Cloud корпорации Майкрософт: ресурсы для лиц, принимающих решения в области ИТ</span><span class="sxs-lookup"><span data-stu-id="ae979-142">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)




