---
title: Аварийное восстановление SharePoint Server 2013 в Microsoft Azure
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 04/17/2018
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Ent_Deployment
ms.assetid: e9d14cb2-ff28-4a18-a444-cebf891880ea
description: 'Summary: Using Azure, you can create a disaster-recovery environment for your on-premises SharePoint farm. This article describes how to design and implement this solution.'
ms.openlocfilehash: 101d87b1a25d2b3ac8a7ae29832e52c805ecdc4c
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998171"
---
# <a name="sharepoint-server-2013-disaster-recovery-in-microsoft-azure"></a>Аварийное восстановление SharePoint Server 2013 в Microsoft Azure

 С помощью Azure вы можете создать среду аварийного восстановления для локальной фермы SharePoint. В этой статье описываются разработка и реализация этого решения.

 **Смотрите видео с обзором аварийного восстановления в SharePoint Server 2013**
> [!VIDEO https://www.microsoft.com/videoplayer/embed/1b73ec8f-29bd-44eb-aa3a-f7932784bfd9?autoplay=false]
  
 When disaster strikes your SharePoint on-premises environment, your top priority is to get the system running again quickly. Disaster recovery with SharePoint is quicker and easier when you have a backup environment already running in Microsoft Azure. This video explains the main concepts of a SharePoint warm failover environment and complements the full details available in this article.
  
Используйте эту статью вместе со следующей моделью решения: **Аварийное восстановление SharePoint в Microsoft Azure**.
  
[![Процесс аварийного восстановления SharePoint в Azure](media/SP-DR-Azure.png)](https://go.microsoft.com/fwlink/p/?LinkId=392555)
  
 [PDF](https://go.microsoft.com/fwlink/p/?LinkId=392555) |  [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392554)
  
## <a name="use-azure-infrastructure-services-for-disaster-recovery"></a>Использование служб инфраструктуры Azure для аварийного восстановления

Many organizations do not have a disaster recovery environment for SharePoint, which can be expensive to build and maintain on-premises. Azure Infrastructure Services provides compelling options for disaster recovery environments that are more flexible and less expensive than the on-premises alternatives.
  
Используя Службы инфраструктуры Azure, вы получаете следующие преимущества:
  
- **Fewer costly resources** Maintain and pay for fewer resources than on-premises disaster recovery environments. The number of resources depends on which disaster-recovery environment you choose: cold standby, warm standby, or hot standby.
    
- **Better resource flexibility** In the event of a disaster, easily scale out your recovery SharePoint farm to meet load requirements. Scale in when you no longer need the resources.
    
- **Меньшая зависимость от центров обработки данных** Используйте Службы инфраструктуры Azure, чтобы не вкладывать средства во вспомогательный центр обработки данных в другом регионе.
    
There are less-complex options for organizations just getting started with disaster recovery and advanced options for organizations with high-resilience requirements. The definitions for cold, warm, and hot standby environments are a little different when the environment is hosted on a cloud platform. The following table describes these environments for building a SharePoint recovery farm in Azure.
  
**Таблица. Среды восстановления**

|**Тип среды восстановления**|**Описание**|
|:-----|:-----|
|Горячая замена  <br/> |Полноразмерная ферма подготавливается, обновляется и работает в ждущем режиме.  <br/> |
|Горячее резервирование  <br/> |Создается ферма, а также работают и обновляются виртуальные машины.  <br/> Восстановление включает присоединение баз данных контента, подготовку приложений-служб и обход контента.  <br/> Эта ферма может быть уменьшенной версией рабочей фермы и расширяться для обслуживания всех пользователей.  <br/> |
|Холодное резервирование  <br/> |Ферма создается в полном масштабе, но виртуальные машины останавливаются.  <br/> Обслуживание среды включает запуск виртуальных машин по мере необходимости, а также исправление, обновление и проверку среды.  <br/> Полный запуск среды в случае сбоя.  <br/> |
   
It's important to evaluate your organization's Recovery Time Objectives (RTOs) and Recovery Point Objectives (RPOs). These requirements determine which environment is the most appropriate investment for your organization.
  
The guidance in this article describes how to implement a warm standby environment. You can also adapt it to a cold standby environment, although you need to follow additional procedures to support this kind of environment. This article does not describe how to implement a hot standby environment.
  
Дополнительные сведения о решениях аварийного восстановления см. в статьях [High availability and disaster recovery concepts in SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkID=393114) и [Choose a disaster recovery strategy for SharePoint 2013](https://go.microsoft.com/fwlink/p/?linkid=203228).
  
## <a name="solution-description"></a>Описание решения

Для решения аварийного восстановления с горячим резервированием необходимы следующие компоненты среды:
  
- локальная рабочая ферма SharePoint;
    
- среда восстановления SharePoint в Azure;
    
- VPN-подключение типа "сеть-сеть" между двумя средами.
    
На следующем рисунке показаны эти три элемента.
  
**Рисунок. Элементы решения горячего резервирования в Azure**

![Элементы решения "горячего" резервирования SharePoint в Azure](media/AZarch-AZWarmStndby.png)
  
Доставка журналов SQL Server с репликацией распределенной файловой системы (DFSR) используется для копирования резервных копий баз данных и журналов транзакций в ферму восстановления в Azure: 
  
- DFSR transfers logs from the production environment to the recovery environment. In a WAN scenario, DFSR is more efficient than shipping the logs directly to the secondary server in Azure.
    
- Журналы воспроизводятся на сервере SQL Server в среде восстановления Azure.
    
- Базы данных контента SharePoint с доставкой журналов присоединяются к среде только после восстановления.
    
Чтобы восстановить ферму, выполните следующие действия.
  
1. Остановите доставку журналов.
    
2. Остановите прием трафика основной фермы.
    
3. Воспроизведите журналы транзакций.
    
4. Присоедините базу данных контента к ферме.
    
5. Восстановите приложения-службы из служб реплицированных баз данных.
    
6. Измените записи системы доменных имен (DNS), чтобы они указывали на ферму восстановления.
    
7. Запустите полный обход.
    
We recommend that you rehearse these steps regularly and document them to help ensure that your live recovery runs smoothly. Attaching content databases and restoring service applications can take some time and typically involves some manual configuration.
  
После восстановления это решение предоставляет элементы, перечисленные в следующей таблице.
  
**Таблица. Цели восстановления решения**

|**Элемент**|**Описание**|
|:-----|:-----|
|Сайты и контент  <br/> |Сайты и контент доступны в среде восстановления.  <br/> |
|Новый экземпляр поиска  <br/> |In this warm standby solution, search is not restored from search databases. Search components in the recovery farm are configured as similarly as possible to the production farm. After the sites and content are restored, a full crawl is started to rebuild the search index. You do not need to wait for the crawl to complete to make the sites and content available.  <br/> |
|Службы  <br/> | Services that store data in databases are restored from the log-shipped databases. Services that do not store data in databases are simply started. <br/>  Not all services with databases need to be restored. The following services do not need to be restored from databases and can simply be started after failover: <br/>  Приложение-служба сбора данных об использовании и работоспособности <br/>  Служба состояний <br/>  Служба автоматизации Word <br/>  Любая другая служба, которая не использует базу данных <br/> |
   
You can work with Microsoft Consulting Services (MCS) or a partner to address more-complex recovery objectives. These are summarized in the following table.
  
**Таблица. Другие задачи, которые могут выполнить MCS или партнеры**

|**Элемент**|**Описание**|
|:-----|:-----|
|Синхронизация решений пользовательской фермы  <br/> |Ideally, the recovery farm configuration is identical to the production farm. You can work with a consultant or partner to evaluate whether custom farm solutions are replicated and whether the process is in place for keeping the two environments synchronized.  <br/> |
|Подключения к локальным источникам данных  <br/> |Реплицировать подключения к серверным системам данных, например резервным контроллерам доменов (BDC) и источникам контента поиска, может быть нецелесообразно.  <br/> |
|Сценарии восстановления поиска  <br/> |Because enterprise search deployments tend to be fairly unique and complex, restoring search from databases requires a greater investment. You can work with a consultant or partner to identify and implement search restore scenarios that your organization might require.  <br/> |
   
В этой статье предполагается, что локальная ферма уже разработана и развернута.
  
## <a name="detailed-architecture"></a>Подробная архитектура

В идеальном случае конфигурация фермы восстановления в Azure идентична конфигурации локальной рабочей фермы, включая:
  
- одинаковое представление ролей серверов;
    
- одинаковую конфигурацию настроек;
    
- одинаковую конфигурацию компонентов поиска.
    
The environment in Azure can be a smaller version of the production farm. If you plan to scale out the recovery farm after failover, it's important that each type of server role be initially represented.
  
Some configurations might not be practical to replicate in the failover environment. Be sure to test the failover procedures and environment to help ensure that the failover farm provides the expected service level.
  
This solution doesn't prescribe a specific topology for a SharePoint farm. The focus of this solution is to use Azure for the failover farm and to implement log shipping and DFSR between the two environments.
  
### <a name="warm-standby-environments"></a>Среды горячего резервирования

In a warm standby environment, all virtual machines in the Azure environment are running. The environment is ready for a failover exercise or event.
  
На следующем рисунке показано решение аварийного восстановления из локальной фермы SharePoint в ферму Azure, которая настроена как среда горячего резервирования.
  
**Рисунок. Топология и основные элементы рабочей фермы и фермы восстановления с горячим резервированием**

![Топология фермы SharePoint и фермы восстановления с "горячим" резервированием](media/AZarch-AZWarmStndby.png)
  
На этой схеме:
  
- показаны две среды: локальная ферма SharePoint и ферма горячего резервирования в Azure;
    
- Каждая среда содержит общий файловый ресурс.
    
- Each farm includes four tiers. To achieve high availability, each tier includes two servers or virtual machines that are configured identically for a specific role, such as front-end services, distributed cache, back-end services, and databases. It isn't important in this illustration to call out specific components. The two farms are configured identically.
    
- The fourth tier is the database tier. Log shipping is used to copy logs from the secondary database server in the on-premises environment to the file share in the same environment.
    
- DFSR копирует файлы из общего файлового ресурса локальной среды на общий файловый ресурс среды Azure;
    
- доставка журналов воспроизводит журналы из общего файлового ресурса в среде Azure для основной реплики в группе доступности SQL Server AlwaysOn в среде восстановления.
    
### <a name="cold-standby-environments"></a>Среды холодного резервирования

In a cold standby environment, most of the SharePoint farm virtual machines can be shut down. (We recommend occasionally starting the virtual machines, such as every two weeks or once a month, so that each virtual machine can sync with the domain.) The following virtual machines in the Azure recovery environment must remain running to help ensure continuous operations of log shipping and DFSR:
  
- Общий файловый ресурс
    
- Основной сервер баз данных
    
- Как минимум одна виртуальная машина, на которой запущены доменные службы Windows Server Active Directory и DNS
    
The following figure shows an Azure failover environment in which the file share virtual machine and the primary SharePoint database virtual machine are running. All other SharePoint virtual machines are stopped. The virtual machine that is running Windows Server Active Directory and DNS is not shown.
  
**Рисунок. Виртуальные машины, запущенные в ферме восстановления с холодным резервированием**

![Элементы решения холодного резервирования SharePoint в Azure](media/AZarch-AZColdStndby.png)
  
После отработки отказа в среде с холодным резервированием запускаются все виртуальные машины и должен быть настроен метод обеспечения высокой доступности серверов баз данных, например группы доступности SQL Server AlwaysOn.
  
Если реализовано несколько групп хранения (базы данных распределены между несколькими группами высокой доступности SQL Server), должна быть запущена основная база данных для каждой группы хранения, чтобы получить журналы, связанные с соответствующей группой хранения.
  
### <a name="skills-and-experience"></a>Знания и опыт

Multiple technologies are used in this disaster recovery solution. To help ensure that these technologies interact as expected, each component in the on-premises and Azure environment must be installed and configured correctly. We recommend that the person or team who sets up this solution have a strong working knowledge of and hands-on skills with the technologies described in the following articles:
  
- [Службы репликации распределенной файловой системы (DFS)](https://go.microsoft.com/fwlink/p/?LinkId=392698)
    
- [Отказоустойчивая кластеризация Windows Server (WSFC) с SQL Server](https://go.microsoft.com/fwlink/p/?LinkId=392701)
    
- [Группы доступности AlwaysOn (SQL Server)](https://go.microsoft.com/fwlink/p/?LinkId=392725)
    
- [Резервное копирование и восстановление баз данных SQL Server](https://go.microsoft.com/fwlink/p/?LinkId=392728)
    
- [Установка SharePoint Server 2013 и развертывание в ферме](https://go.microsoft.com/fwlink/p/?LinkId=393119)
    
- [Microsoft Azure](https://go.microsoft.com/fwlink/p/?LinkId=392729)
    
Finally, we recommend scripting skills that you can use to automate tasks associated with these technologies. It's possible to use the available user interfaces to complete all the tasks described in this solution. However, a manual approach can be time consuming and error prone and delivers inconsistent results.
  
In addition to Windows PowerShell, there are also Windows PowerShell libraries for SQL Server, SharePoint Server, and Azure. Don't forget T-SQL, which can also help reduce the time to configure and maintain your disaster-recovery environment.
  
## <a name="disaster-recovery-roadmap"></a>Схема аварийного восстановления

![Визуальное представление схемы аварийного восстановления SharePoint.](media/Azure-DRroadmap.png)
  
Эта схема подразумевает, что рабочая ферма SharePoint Server 2013 уже развернута.
  
**Таблица. Схема аварийного восстановления**

|**Этап**|**Описание**|
|:-----|:-----|
|Этап 1  <br/> |Разработка среды аварийного восстановления.  <br/> |
|Этап 2  <br/> |Создание виртуальной сети Azure и VPN-подключения.  <br/> |
|Этап 3  <br/> |Развертывание Windows Active Directory и служб доменных имен в виртуальной сети Azure.  <br/> |
|Этап 4  <br/> |Развертывание фермы восстановления SharePoint в Azure.  <br/> |
|Этап 5  <br/> |Настройка DFSR между фермами.  <br/> |
|Этап 6  <br/> |Настройка доставки журналов в ферму восстановления.  <br/> |
|Этап 7  <br/> | Validate failover and recovery solutions. This includes the following procedures and technologies: <br/>  остановка доставки журналов; <br/>  восстановление резервных копий; <br/>  обход контента; <br/>  восстановление служб; <br/>  управление записями DNS. <br/> |
   
## <a name="phase-1-design-the-disaster-recovery-environment"></a>Этап 1. Разработка среды аварийного восстановления

Следуйте указаниям из статьи [Microsoft Azure Architectures for SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md), чтобы разработать среду аварийного восстановления, включая ферму восстановления SharePoint. Вы можете использовать графические элементы [решения аварийного восстановления SharePoint в файле Azure](https://go.microsoft.com/fwlink/p/?LinkId=392554) Visio, чтобы начать процесс создания проекта. Рекомендуем полностью разработать среду, прежде чем приступать к работе в среде Azure.
  
Выполнив указания по разработке виртуальной сети, VPN-подключения, Active Directory и фермы SharePoint, приведенные в статье [Архитектуры Microsoft Azure для SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md), также необходимо добавить роль файлового ресурса в среду Azure.
  
To support log shipping in a disaster-recovery solution, a file share virtual machine is added to the subnet where the database roles reside. The file share also serves as the third node of a Node Majority for the SQL Server AlwaysOn availability group. This is the recommended configuration for a standard SharePoint farm that uses SQL Server AlwaysOn availability groups. 
  
> [!NOTE]
> It is important to review the prerequisites for a database to participate in a SQL Server AlwaysOn availability group. For more information, see [Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups](https://go.microsoft.com/fwlink/p/?LinkId=510870). 
  
**Рисунок. Расположение файлового сервера, используемого решением для аварийного восстановления**

![Отображает общую папку виртуальной машины, добавленную в облачную службу, которая содержит роли сервера базы данных SharePoint.](media/AZenv-FSforDFSRandWSFC.png)
  
In this diagram, a file share virtual machine is added to the same subnet in Azure that contains the database server roles. Do not add the file share virtual machine to an availability set with other server roles, such as the SQL Server roles.
  
If you are concerned about the high availability of the logs, consider taking a different approach by using [SQL Server backup and restore with Azure Blob Storage Service](https://go.microsoft.com/fwlink/p/?LinkId=393113). This is a new feature in Azure that saves logs directly to a blob storage URL. This solution does not include guidance about using this feature.
  
When you design the recovery farm, keep in mind that a successful disaster recovery environment accurately reflects the production farm that you want to recover. The size of the recovery farm is not the most important thing in the recovery farm's design, deployment, and testing. Farm scale varies from organization to organization based on business requirements. It might be possible to use a scaled-down farm for a short outage or until performance and capacity demands require you to scale the farm.
  
Configure the recovery farm as identically as possible to the production farm so that it meets your service level agreement (SLA) requirements and provides the functionality that you need to support your business. When you design the disaster recovery environment, also look at your change management process for your production environment. We recommend that you extend the change management process to the recovery environment by updating the recovery environment at the same interval as the production environment. As part of the change management process, we recommend maintaining a detailed inventory of your farm configuration, applications, and users. 
  
## <a name="phase-2-create-the-azure-virtual-network-and-vpn-connection"></a>Этап 2. Создание виртуальной сети Azure и VPN-подключения

[Connect an on-premises network to a Microsoft Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md) shows you how to plan and deploy the virtual network in Azure and how to create the VPN connection. Follow the guidance in the topic to complete the following procedures:
  
- Планирование пространства частных IP-адресов Виртуальная сеть.
    
- Планирование изменений инфраструктуры маршрутизации для Виртуальная сеть.
    
- Планирование правил брандмауэра для входящего и исходящего трафика на локальном устройстве VPN.
    
- Создание распределенной виртуальной сети в Azure.
    
- Настройка маршрутизации между локальной сетью и Виртуальная сеть.
    
## <a name="phase-3-deploy-active-directory-and-domain-name-services-to-the-azure-virtual-network"></a>Этап 3. Развертывание Active Directory и служб доменных имен в виртуальной сети Azure

Этот этап включает развертывание Windows Server Active Directory и DNS в Виртуальная сеть в гибридном сценарии, как описано в статье [Архитектуры Microsoft Azure для SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md) и показано на следующем рисунке:
  
**Рисунок. Гибридная конфигурация домена Active Directory**

![Две виртуальные машины, развернутые в виртуальной сети Azure, и подсеть фермы SharePoint — это реплики контроллеров домена и DNS-серверы.](media/AZarch-HyADdomainConfig.png)
  
In the illustration, two virtual machines are deployed to the same subnet. These virtual machines are each hosting two roles: Active Directory and DNS.
  
Before deploying Active Directory in Azure, read [Guidelines for Deploying Windows Server Active Directory on Azure Virtual Machines](https://go.microsoft.com/fwlink/p/?linkid=392681). These guidelines help you determine whether you need a different architecture or different configuration settings for your solution.
  
Подробные указания по настройке контроллера домена в Azure см. в статье [Установка реплики контроллера домена Active Directory в виртуальных сетях Azure](https://go.microsoft.com/fwlink/p/?LinkId=392687).
  
Before this phase, you didn't deploy virtual machines to the Virtual Network. The virtual machines for hosting Active Directory and DNS are likely not the largest virtual machines you need for the solution. Before you deploy these virtual machines, first create the largest virtual machine that you plan to use in your Virtual Network. This helps ensure that your solution lands on a tag in Azure that allows the largest size you need. You do not need to configure this virtual machine at this time. Simply create it, and set it aside. If you do not do this, you might run into a limitation when you try to create larger virtual machines later, which was an issue at the time this article was written. 
  
## <a name="phase-4-deploy-the-sharepoint-recovery-farm-in-azure"></a>Этап 4. Развертывание фермы восстановления SharePoint в Azure

Deploy the SharePoint farm in your Virtual Network according to your design plans. It might be helpful to review [Planning for SharePoint 2013 on Azure Infrastructure Services](https://go.microsoft.com/fwlink/p/?LinkId=400984) before you deploy SharePoint roles in Azure.
  
Ниже приводятся рекомендации, которые помогли нам при создании нашей экспериментальной среды:
  
- Создавайте виртуальные машины с помощью портала Azure или PowerShell.
    
- Azure and Hyper-V do not support dynamic memory. Be sure this is factored into your performance and capacity plans.
    
- Restart virtual machines through the Azure interface, not from the virtual machine logon itself. Using the Azure interface works better and is more predictable.
    
- If you want to shut down a virtual machine to save costs, use the Azure interface. If you shut down from the virtual machine logon, charges continue to accrue.
    
- Используйте соглашение об именовании для виртуальных машин.
    
- Обращайте внимание на расположение центра обработки, в котором развертываются виртуальные машины.
    
- Функция автоматического масштабирования в Azure не поддерживается для ролей SharePoint.
    
- Не настраивайте элементы фермы, которые будут восстановлены, например семейства веб-сайтов. 
    
## <a name="phase-5-set-up-dfsr-between-the-farms"></a>Этап 5. Настройка DFSR между фермами

To set up file replication by using DFSR, use the DNS Management snap-in. However, before the DFSR setup, log on to your on-premises file server and Azure file server and enable the service in Windows.
  
На панели мониторинга диспетчера серверов выполните следующие действия.
  
- Настройте локальный сервер.
    
- Запустите **мастер добавления ролей и компонентов**.
    
- Откройте узел **Файловые службы и службы хранилища**.
    
- Выберите пункты **Пространства имен DFS** и **Репликация DFS**.
    
- Нажмите кнопку **Далее**, чтобы завершить работу мастера.
    
В приведенной ниже таблице представлены ссылки на справочные статьи и сообщения блогов, посвященные DFSR.
  
**Таблица. Справочные статьи, посвященные DFSR**

|**Название**|**Описание**|
|:-----|:-----|
|[Репликация](https://go.microsoft.com/fwlink/p/?LinkId=392732) <br/> |Статья по управлению DFS на сайте TechNet, включающая ссылки для репликации  <br/> |
|[Практические советы по репликации DFS](https://go.microsoft.com/fwlink/p/?LinkId=392737) <br/> |Вики-сайт со ссылками на сведения о DFS  <br/> |
|[Репликация DFS. Вопросы и ответы](https://go.microsoft.com/fwlink/p/?LinkId=392738) <br/> |Статья о репликации DFS на сайте TechNet  <br/> |
|[Блог Хосе Баррето (Jose Barreto)](https://go.microsoft.com/fwlink/p/?LinkId=392739) <br/> |Блог главного руководителя проекта из группы файловых серверов Майкрософт  <br/> |
|[Блог группы Майкрософт, ответственной за хранение](https://go.microsoft.com/fwlink/p/?LinkId=392740) <br/> |Блог, посвященный файловым службам и функциям хранения в Windows Server  <br/> |
   
## <a name="phase-6-set-up-log-shipping-to-the-recovery-farm"></a>Этап 6. Настройка доставки журналов в ферму восстановления

Log shipping is the critical component for setting up disaster recovery in this environment. You can use log shipping to automatically send transaction log files for databases from a primary database server instance to a secondary database server instance. To set up log shipping, see [Configure log shipping in SharePoint 2013](https://docs.microsoft.com/sharepoint/administration/configure-log-shipping). 
  
> [!IMPORTANT]
> Log shipping support in SharePoint Server is limited to certain databases. For more information, see [Supported high availability and disaster recovery options for SharePoint databases (SharePoint 2013)](https://go.microsoft.com/fwlink/p/?LinkId=393121). 
  
## <a name="phase-7-validate-failover-and-recovery"></a>Этап 7. Проверка отработки отказа и восстановления

The goal of this final phase is to verify that the disaster recovery solution works as planned. To do this, create a failover event that shuts down the production farm and starts up the recovery farm as a replacement. You can start a failover scenario manually or by using scripts.
  
The first step is to stop incoming user requests for farm services or content. You can do this by disabling DNS entries or by shutting down the front-end web servers. After the farm is "down," you can fail over to the recovery farm.
  
### <a name="stop-log-shipping"></a>Остановка доставки журналов

You must stop log shipping before farm recovery. Stop log shipping on the secondary server in Azure first, and then stop it on the primary server on-premises. Use the following script to stop log shipping on the secondary server first and then on the primary server. The database names in the script might be different, depending on your environment.
  
```
-- This script removes log shipping from the server.
-- Commands must be executed on the secondary server first and then on the primary server.

SET NOCOUNT ON
DECLARE  @PriDB nvarchar(max)
,@SecDB nvarchar(250)
,@PriSrv nvarchar(250)
,@SecSrv nvarchar(250)

Set @PriDB= ''
SET @PriDB = UPPER(@PriDB)
SET @PriDB = REPLACE(@PriDB, ' ', '')
SET @PriDB = '''' + REPLACE(@PriDB, ',', ''', ''') + ''''

Set @SecDB = @PriDB

Exec ( 'Select  ''exec master..sp_delete_log_shipping_secondary_database '' + '''''''' + prm.primary_database +  ''''''''   
from msdb.dbo.log_shipping_monitor_primary prm INNER JOIN msdb.dbo.log_shipping_primary_secondaries sec  ON  prm.primary_database=sec.secondary_database
where prm.primary_database in ( ' + @PriDB + ' )')

Exec ( 'Select  ''exec master..sp_delete_log_shipping_primary_secondary '' + '''''''' + prm.Primary_Database + '''''', '''''' + sec.Secondary_Server + '''''', '''''' + sec.Secondary_database + ''''''''   
from msdb.dbo.log_shipping_monitor_primary prm INNER JOIN msdb.dbo.log_shipping_primary_secondaries sec  ON  prm.primary_database=sec.secondary_database
where prm.primary_database in ( ' + @PriDB + ' )')

Exec ( 'Select  ''exec master..sp_delete_log_shipping_primary_database '' + '''''''' + prm.primary_database +  ''''''''   
from msdb.dbo.log_shipping_monitor_primary prm INNER JOIN msdb.dbo.log_shipping_primary_secondaries sec  ON  prm.primary_database=sec.secondary_database
where prm.primary_database in ( ' + @PriDB + ' )')

Exec ( 'Select  ''exec master..sp_delete_log_shipping_secondary_primary '' + '''''''' + prm.primary_server + '''''', '''''' + prm.primary_database +  ''''''''   
from msdb.dbo.log_shipping_monitor_primary prm INNER JOIN msdb.dbo.log_shipping_primary_secondaries sec  ON  prm.primary_database=sec.secondary_database
where prm.primary_database in ( ' + @PriDB + ' )')

```

### <a name="restore-the-backups"></a>Восстановление резервных копий

Backups must be restored in the order in which they were created. Before you can restore a particular transaction log backup, you must first restore the following previous backups without rolling back uncommitted transactions (that is, by using  `WITH NORECOVERY`):
  
- The full database backup and the last differential backup - Restore these backups, if any exist, taken before the particular transaction log backup. Before the most recent full or differential database backup was created, the database was using the full recovery model or bulk-logged recovery model.
    
- All transaction log backups - Restore any transaction log backups taken after the full database backup or the differential backup (if you restore one) and before the particular transaction log backup. Log backups must be applied in the sequence in which they were created, without any gaps in the log chain.
    
To recover the content database on the secondary server so that the sites render, remove all database connections before recovery. To restore the database, run the following SQL statement.
  
```
restore database WSS_Content with recovery

```

> [!IMPORTANT]
> When you use T-SQL explicitly, specify either **WITH NORECOVERY** or **WITH RECOVERY** in every RESTORE statement to eliminate ambiguity—this is very important when writing scripts. After the full and differential backups are restored, the transaction logs can be restored in SQL Server Management Studio. Also, because log shipping is already stopped, the content database is in a standby state, so you must change the state to full access.
  
In SQL Server Management Studio, right-click the **WSS_Content** database, point to **Tasks** > **Restore**, and then click **Transaction Log** (if you have not restored the full backup, this is not available). For more information, see[Restore a Transaction Log Backup (SQL Server)](https://go.microsoft.com/fwlink/p/?LinkId=392778).
  
### <a name="crawl-the-content-source"></a>Обход источника контента

You must start a full crawl for each content source to restore the Search Service. Note that you lose some analytics information from the on-premises farm, such as search recommendations. Before you start the full crawls, use the Windows PowerShell cmdlet **Restore-SPEnterpriseSearchServiceApplication** and specify the log-shipped and replicated Search Administration database, **Search_Service__DB_<GUID>**. This cmdlet gives the search configuration, schema, managed properties, rules, and sources and creates a default set of the other components.
  
Чтобы запустить полный обход, выполните следующие действия.
  
1. В Центр администрирования SharePoint 2013 откройте раздел **Управление приложениями** > **Приложения-службы** > **Управление приложениями-службами**, а затем щелкните приложение-службу поиска, обход которого нужно выполнить.
    
2. На странице **Администрирование поиска** нажмите **Источники контента**, наведите указатель на нужный источник контента, щелкните стрелку и нажмите **Начать полный обход**.
    
### <a name="recover-farm-services"></a>Восстановление служб фермы

В приведенной ниже таблице показано, как восстановить службы, в которых есть базы данных с доставкой журналов, службы, где есть базы данных, но не рекомендуется восстановление с доставкой журналов, и службы, в которых нет баз данных.
  
> [!IMPORTANT]
> При восстановлении локальной базы данных SharePoint в среде Azure не восстанавливаются службы SharePoint, которые еще не установлены в Azure вручную. 
  
**Таблица. Справка по базам данных приложений-служб**

|**Восстановление этих служб из баз данных с доставкой журналов**|**В этих службах есть базы данных, но их рекомендуется запускать без восстановления баз данных**|**Эти службы не хранят данные в базах данных. Запускайте их после отработки отказа**|
|:-----|:-----|:-----|
| Служба машинного перевода <br/>  Служба управляемых метаданных <br/>  Служба Secure Store <br/>  User Profile. (Only the Profile and Social Tagging databases are supported. The Synchronization database is not supported.) <br/>  Служба параметров подписки Microsoft SharePoint Foundation <br/> | Приложение-служба сбора данных об использовании и работоспособности <br/>  Служба состояний <br/>  Служба автоматизации Word <br/> | Службы Excel <br/>  PerformancePoint Services <br/>  Служба преобразования PowerPoint <br/>  Служба графики Visio <br/>  Служба управления работой <br/> |
   
На следующем примере показано, как восстановить службу управляемых метаданных из базы данных.
  
This uses the existing Managed_Metadata_DB database. This database is log shipped, but there is no active service application on the secondary farm, so it needs to be connected after the service application is in place.
  
Для начала используйте команду  `New-SPMetadataServiceApplication` и укажите параметр `DatabaseName` с именем восстановленной базы данных.
  
Затем настройте новое приложение-службу управляемых метаданных на вспомогательном сервере, указав следующие параметры:
  
- Имя: служба управляемых метаданных
    
- Сервер базы данных: имя базы данных из доставленного журнала транзакций
    
- Имя базы данных:Managed_Metadata_DB
    
- Пул приложений: приложения-службы SharePoint 
    
### <a name="manage-dns-records"></a>Управление записями DNS

Необходимо вручную создать записи DNS, указывающие на ферму SharePoint.
  
In most cases where you have multiple front-end web servers, it makes sense to take advantage of the Network Load Balancing feature in Windows Server 2012 or a hardware load balancer to distribute requests among the web-front-end servers in your farm. Network load balancing can also help reduce risk by distributing requests to the other servers if one of your web-front-end servers fails. 
  
Typically, when you set up network load balancing, your cluster is assigned a single IP address. You then create a DNS host record in the DNS provider for your network that points to the cluster. (For this project, we put a DNS server in Azure for resiliency in case of an on-premises datacenter failure.) For instance, you can create a DNS record, in DNS Manager in Active Directory, for example, called  `https://sharepoint.contoso.com`, that points to the IP address for your load-balanced cluster.
  
Для внешнего доступа к ферме SharePoint можно создать запись узла на внешнем DNS-сервере с тем же URL-адресом, который клиенты используют в вашей интрасети (например, `https://sharepoint.contoso.com` ), который указывает на внешний IP-адрес в брандмауэре. (При использовании этого примера лучше всего настроить разделенный DNS, чтобы внутренний DNS-сервер был полномочным для `contoso.com` маршрутизации и направляет запросы непосредственно в кластер фермы SharePoint вместо маршрутизации DNS-запросов на внешний DNS-сервер.) Затем можно сопоставить внешний IP-адрес с внутренним IP-адресом локального кластера, чтобы клиенты могли найти нужные вам ресурсы.
  
После этого может возникнуть один из описанных ниже сценариев аварийного восстановления.
  
 **Example scenario: The on-premises SharePoint farm is unavailable because of hardware failure in the on-premises SharePoint farm.** In this case, after you have completed the steps for failover to the Azure SharePoint farm, you can configure network load balancing on the recovery SharePoint farm's web-front-end servers, the same way you did with the on-premises farm. You can then redirect the host record in your internal DNS provider to point to the recovery farm's cluster IP address. Note that it can take some time before cached DNS records on clients are refreshed and point to the recovery farm.
  
 **Example scenario: The on-premises datacenter is lost completely.** This scenario might occur due to a natural disaster, such as a fire or flood. In this case, for an enterprise, you would likely have a secondary datacenter hosted in another region as well as your Azure subnet that has its own directory services and DNS. As in the previous disaster scenario, you can redirect your internal and external DNS records to point to the Azure SharePoint farm. Again, take note that DNS-record propagation can take some time.
  
Если вы используете семейства сайтов с именем на основе узла, как рекомендуется в [архитектуре и развертывании семейства сайтов с именем на основе узла (SharePoint 2013)](https://docs.microsoft.com/SharePoint/administration/host-named-site-collection-architecture-and-deployment), у вас может быть несколько семейств сайтов, размещенных в одном веб-приложении в ферме SharePoint, с УНИКАЛЬНЫМи DNS-именами (например, `https://sales.contoso.com` и `https://marketing.contoso.com` ). В этом случае вы можете создать для каждого семейства веб-сайтов записи DNS, указывающие на IP-адрес кластера. Когда запросы достигают интерфейсных веб-серверов SharePoint, эти серверы обрабатывают маршрутизацию запросов в соответствующие семейства веб-сайтов.
  
## <a name="microsoft-proof-of-concept-environment"></a>Экспериментальная среда Майкрософт

We designed and tested a proof-of-concept environment for this solution. The design goal for our test environment was to deploy and recover a SharePoint farm that we might find in a customer environment. We made several assumptions, but we knew that the farm needed to provide all of the out-of-the-box functionality without any customizations. The topology was designed for high availability by using best practice guidance from the field and product group.
  
В следующей таблице описываются виртуальные машины Hyper-V, созданные и настроенные для локальной тестовой среды.
  
**Таблица. Виртуальные машины для локального тестирования**

|**Имя сервера**|**Роль**|**Конфигурация**|
|:-----|:-----|:-----|
|DC1  <br/> |Контроллер домена с Active Directory.  <br/> |Два процессора  <br/> От 512 МБ до 4 ГБ ОЗУ  <br/> 1 жесткий диск объемом 127 ГБ  <br/> |
|RRAS  <br/> |Сервер, на котором настроена роль службы маршрутизации и удаленного доступа (RRAS).  <br/> |Два процессора  <br/> 2-8 ГБ ОЗУ  <br/> 1 жесткий диск объемом 127 ГБ  <br/> |
|FS1  <br/> |Файловый сервер с общими папками для резервных копий и конечной точкой для DFSR.  <br/> |Четыре процессора  <br/> 2-12 ГБ ОЗУ  <br/> 1 жесткий диск объемом 127 ГБ  <br/> 1 жесткий диск объемом 1 ТБ (SAN)  <br/> 1 жесткий диск объемом 750 ГБ  <br/> |
|SP-WFE1, SP-WFE2  <br/> |Интерфейсные веб-серверы.  <br/> |Четыре процессора  <br/> 16 ГБ ОЗУ  <br/> |
|SP-APP1, SP-APP2, SP-APP3  <br/> |Серверы приложений  <br/> |Четыре процессора  <br/> 2-16 ГБ ОЗУ  <br/> |
|SP-SQL-HA1, SP-SQL-HA2  <br/> |Database servers, configured with SQL Server 2012 AlwaysOn availability groups to provide high availability. This configuration uses SP-SQL-HA1 and SP-SQL-HA2 as the primary and secondary replicas.  <br/> |Четыре процессора  <br/> 2-16 ГБ ОЗУ  <br/> |
   
В следующей таблице описываются конфигурации дисков для виртуальных машин Hyper-V, которые мы создали и настроили для серверов приложений и интерфейсных веб-серверов в локальной тестовой среде.
  
**Таблица. Требования к дискам виртуальных машин для серверов приложений и интерфейсных веб-серверов в локальной тестовой среде**

|**Буква диска**|**Размер**|**Имя каталога**|**Путь**|
|:-----|:-----|:-----|:-----|
|C  <br/> |80  <br/> |Системный диск  <br/> |<DriveLetter>:\\Program Files\\Microsoft SQL Server\\  <br/> |
|E  <br/> |80  <br/> |Диск журналов (40 ГБ)  <br/> |<DriveLetter>:\\Program Files\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\DATA  <br/> |
|F  <br/> |80  <br/> |Диск файла подкачки (36 ГБ)  <br/> |<DriveLetter>:\\Program Files\\Microsoft SQL Server\\MSSQL\\DATA  <br/> |
   
The following table describes drive configurations for the Hyper-V virtual machines created and configured to serve as the on-premises database servers. On the **Database Engine Configuration** page, access the **Data Directories** tab to set and confirm the settings shown in the following table.
  
**Таблица. Требования к диска виртуальных машин для сервера базы данных в локальной тестовой среде**

|**Буква диска**|**Размер**|**Имя каталога**|**Путь**|
|:-----|:-----|:-----|:-----|
|C  <br/> |80  <br/> |Корневой каталог данных  <br/> |<DriveLetter>:\\Program Files\\Microsoft SQL Server\\  <br/> |
|E  <br/> |500  <br/> |Каталог базы данных пользователей  <br/> |<DriveLetter>:\\Program Files\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\DATA  <br/> |
|F  <br/> |500  <br/> |Каталог журнала базы данных пользователей  <br/> |<DriveLetter>:\\Program Files\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\DATA  <br/> |
|Г  <br/> |500  <br/> |Временный каталог БД  <br/> |<DriveLetter>:\\Program Files\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\DATA  <br/> |
|H  <br/> |500  <br/> |Временный каталог журнала БД  <br/> |<DriveLetter>:\\Program Files\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\DATA  <br/> |
   
### <a name="setting-up-the-test-environment"></a>Настройка тестовой среды

During the different deployment phases, the test team typically worked on the on-premises architecture first and then on the corresponding Azure environment. This reflects the general real-world cases where in-house production farms are already running. What is even more important is that you should know the current production workload, capacity, and typical performance. In addition to building a disaster recovery model that can meet business requirements, you should size the recovery farm servers to deliver a minimum level of service. In a cold or warm standby environment, a recovery farm is typically smaller than a production farm. After the recovery farm is stable and in production, the farm can be scaled up and out to meet workload requirements.
  
Развертывание нашей тестовой среды выполнялось в три этапа:
  
- Настройка гибридной инфраструктуры
    
- Подготовка серверов
    
- Развертывание ферм SharePoint
    
#### <a name="set-up-the-hybrid-infrastructure"></a>Настройка гибридной инфраструктуры

This phase involved setting up a domain environment for the on-premises farm and for the recovery farm in Azure. In addition to the normal tasks associated with configuring Active Directory, the test team implemented a routing solution and a VPN connection between the two environments.
  
#### <a name="provision-the-servers"></a>Подготовка серверов

In addition to the farm servers, it was necessary to provision servers for the domain controllers and configure a server to handle RRAS as well as the site-to-site VPN. Two file servers were provisioned for the DFSR service, and several client computers were provisioned for testers.
  
#### <a name="deploy-the-sharepoint-farms"></a>Развертывание ферм SharePoint

The SharePoint farms were deployed in two stages in order to simplify environment stabilization and troubleshooting, if required. During the first stage, each farm was deployed on the minimum number of servers for each tier of the topology to support the required functionality.
  
We created the database servers with SQL Server installed before creating the SharePoint 2013 servers. Because this was a new deployment, we created the availability groups before deploying SharePoint. We created three groups based on MCS best practice guidance. 
  
> [!NOTE]
> Create placeholder databases so that you can create availability groups before the SharePoint installation. For more information, see [Configure SQL Server 2012 AlwaysOn Availability Groups for SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=517626)
  
Мы создали ферму и объединили дополнительные серверы в следующем порядке:
  
- Подготовка серверов SP-SQL-HA1 и SP-SQL-HA2.
    
- Настройка AlwaysOn и создание трех групп доступности для фермы. 
    
- Подготовка сервера SP-APP1 для размещения Центра администрирования.
    
- Подготовка серверов SP-WFE1 и SP-WFE2 для размещения распределенного кэша. 
    
Мы использовали параметр _скипрегистерасдистрибутедкачехост_ при выполнении **psconfig.exe** в командной строке. Дополнительные сведения см. [в статье Plan for Feeds and Distributed Cache Service in SharePoint Server 2013](https://docs.microsoft.com/sharepoint/administration/plan-for-feeds-and-the-distributed-cache-service). 
  
В среде восстановления мы повторили следующие этапы:
  
- Подготовка серверов AZ-SQL-HA1 и AZ-SQL-HA2.
    
- Настройка AlwaysOn и создание трех групп доступности для фермы.
    
- Подготовка сервера AZ-APP1 для размещения Центра администрирования.
    
- Подготовка серверов AZ-WFE1 и AZ-WFE2 для размещения распределенного кэша.
    
After we configured the distributed cache and added test users and test content, we started stage two of the deployment. This required scaling out the tiers and configuring the farm servers to support the high-availability topology described in the farm architecture.
  
В следующей таблице описываются виртуальные машины, подсети и группы доступности, настроенные для фермы восстановления.
  
**Таблица. Инфраструктура фермы восстановления**

|**Имя сервера**|**Роль**|**Конфигурация**|**Подсеть**|**Группа доступности**|
|:-----|:-----|:-----|:-----|:-----|
|spDRAD  <br/> |Контроллер домена с Active Directory  <br/> |Два процессора  <br/> От 512 МБ до 4 ГБ ОЗУ  <br/> 1 жесткий диск объемом 127 ГБ  <br/> |sp-ADservers  <br/> ||
|AZ-SP-FS  <br/> |Файловый сервер с общими папками для резервных копий и конечной точкой службы DFSR  <br/> | Конфигурация A5: <br/>  Два процессора <br/>  14 ГБ ОЗУ <br/>  1 жесткий диск объемом 127 ГБ <br/>  1 жесткий диск объемом 135 ГБ <br/>  1 жесткий диск объемом 127 ГБ <br/>  1 жесткий диск объемом 150 ГБ <br/> |sp-databaseservers  <br/> |DATA_SET  <br/> |
|AZ-WFE1, AZ -WFE2  <br/> |Интерфейсные веб-серверы  <br/> | Конфигурация A5: <br/>  Два процессора <br/>  14 ГБ ОЗУ <br/>  1 жесткий диск объемом 127 ГБ <br/> |sp-webservers  <br/> |WFE_SET  <br/> |
|AZ -APP1, AZ -APP2, AZ -APP3  <br/> |Серверы приложений  <br/> | Конфигурация A5: <br/>  Два процессора <br/>  14 ГБ ОЗУ <br/>  1 жесткий диск объемом 127 ГБ <br/> |sp-applicationservers  <br/> |APP_SET  <br/> |
|AZ -SQL-HA1, AZ -SQL-HA2  <br/> |Серверы баз данных, основная и вспомогательная реплики для групп доступности AlwaysOn  <br/> | Конфигурация A5: <br/>  Два процессора <br/>  14 ГБ ОЗУ <br/> |sp-databaseservers  <br/> |DATA_SET  <br/> |
   
### <a name="operations"></a>Операции

Когда команда тестирования стабилизировала среды ферм и завершила функциональное тестирование, она приступила к следующим задачам, необходимым для настройки локальной среды восстановления:
  
- Настройка полных и разностных резервных копий.
    
- Настройка DFSR на файловых серверах, которые передают журналы транзакций между средой Azure и локальной средой.
    
- Настройка доставки журналов на основном сервере баз данных.
    
- Stabilize, validate, and troubleshoot log shipping, as required. This included identifying and documenting any behavior that might cause issues, such as network latency, which would cause log shipping or DFSR file synchronization failures.
    
### <a name="databases"></a>Databases

Наши испытания отработки отказа включали следующие базы данных: 
  
- WSS_Content
    
- ManagedMetadata
    
- БД профилей
    
- БД синхронизации
    
- БД социальных функций
    
- Концентратор типов контента (база данных для выделенного концентратора синдикации типов контента)
    
## <a name="troubleshooting-tips"></a>Советы по устранению неполадок

В этом разделе рассматриваются проблемы, с которыми мы столкнулись в ходе тестирования, и их решения. 
  
### <a name="using-the-term-store-management-tool-caused-the-error-the-managed-metadata-store-or-connection-is-currently-not-available"></a>При использовании средства управления банками терминов возникала ошибка "Хранилище управляемых метаданных или подключение в настоящий момент недоступно".

Убедитесь, что у учетной записи пула приложений, используемой веб-приложением, есть разрешение "Доступ на чтение в банк терминов".
  
### <a name="custom-term-sets-are-not-available-in-the-site-collection"></a>Пользовательские банки терминов недоступны в семействе веб-сайтов

Check for a missing service application association between your content site collection and your content type hub. In addition, under the **Managed Metadata - <site collection name> Connection** properties screen, make sure this option is enabled: **This service application is the default storage location for column specific term sets.**
  
### <a name="the-get-adforest-windows-powershell-command-generates-the-error-the-term-get-adforest-is-not-recognized-as-the-name-of-a-cmdlet-function-script-file-or-operable-program"></a>Команда Windows PowerShell Get-ADForest вызывает ошибку "Имя "Get-ADForest" не распознано как имя командлета, функции, файла скрипта или выполняемой программы".

When setting up user profiles, you need the Active Directory forest name. In the Add Roles and Features Wizard, ensure that you have enabled the Active Directory Module for Windows PowerShell (under the **Remote Server Administration Tools>Role Administration Tools>AD DS and AD LDS Tools** section). In addition, run the following commands before using **Get-ADForest** to help ensure that your software dependencies are loaded.
  
```
Import-module servermanager
Import-module activedirectory

```

### <a name="availability-group-creation-fails-at-starting-the-alwayson_health-xevent-session-on-server-name"></a>Ошибка создания группы доступности на этапе запуска сеанса XEvent "AlwaysOn_health" на сервере <имя сервера>

Убедитесь, что оба узла отказоустойчивого кластера находятся в состоянии "Работает", а не "Приостановлен" или "Остановлен". 
  
### <a name="sql-server-log-shipping-job-fails-with-access-denied-error-trying-to-connect-to-the-file-share"></a>Задание доставки журналов SQL Server завершается с ошибкой отказа в доступе при попытке подключиться к общему файловому ресурсу

Убедитесь, что агент SQL Server работает с учетными данными сети, а не учетными данными по умолчанию.
  
### <a name="sql-server-log-shipping-job-indicates-success-but-no-files-are-copied"></a>Задание доставки журналов SQL Server завершается без ошибок, но файлы не копируются

This happens because the default backup preference for an availability group is **Prefer Secondary**. Ensure that you run the log shipping job from the secondary server for the availability group instead of the primary; otherwise, the job will fail silently. 
  
### <a name="managed-metadata-service-or-other-sharepoint-service-fails-to-start-automatically-after-installation"></a>Служба управляемых метаданных (или другая служба SharePoint) не запускается автоматически после установки

Запуск служб может занять несколько минут в зависимости от производительности и текущей нагрузки на сервере SharePoint Server. Нажмите кнопку **Запустить** для службы и дайте ей достаточно времени для запуска, периодически обновляя экран "Службы на сервере" и проверяя ее состояние. Если служба останется остановленной, включите сбор данных диагностики SharePoint, снова попробуйте запустить службу и проверьте журнал на предмет ошибок. Дополнительные сведения см в статье [Настройка сбора данных диагностики в SharePoint 2013](https://docs.microsoft.com/sharepoint/administration/configure-diagnostic-logging)
  
### <a name="after-changing-dns-to-the-azure-failover-environment-client-browsers-continue-to-use-the-old-ip-address-for-the-sharepoint-site"></a>После настройки DNS для среды отработки отказа Azure браузеры клиентов продолжают использовать старый IP-адрес сайта SharePoint

Your DNS change might not be visible to all clients immediately. On a test client, perform the following command from an elevated command prompt and attempt to access the site again.
  
```
Ipconfig /flushdns
```

## <a name="additional-resources"></a>Дополнительные ресурсы

[Поддерживаемые варианты обеспечения высокой доступности и аварийного восстановления для баз данных SharePoint](https://docs.microsoft.com/sharepoint/administration/supported-high-availability-and-disaster-recovery-options-for-sharepoint-databas)
  
[Настройка групп обеспечения доступности SQL Server 2012 AlwaysOn для SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=393122)
  
## <a name="see-also"></a>См. также

[Освоение облака и гибридные решения](cloud-adoption-and-hybrid-solutions.yml)



