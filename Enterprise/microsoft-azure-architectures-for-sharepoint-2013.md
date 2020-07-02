---
title: Архитектуры Microsoft Azure для SharePoint 2013
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Ent_Architecture
ms.assetid: 98fc1006-9399-4ff0-a216-c7c05820d822
description: 'Summary: SharePoint 2013 solutions can be hosted in Microsoft Azure virtual machines. Learn which type of solutions are a good fit and how to set up Microsoft Azure to host one.'
ms.openlocfilehash: fee388f56faf2b30534d9a56926d9d62a176df19
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "44997901"
---
# <a name="microsoft-azure-architectures-for-sharepoint-2013"></a>Архитектуры Microsoft Azure для SharePoint 2013

Среда Azure отлично подходит для размещения решений SharePoint Server 2013. В большинстве случаев рекомендуется использовать Microsoft 365, но ферма SharePoint Server, размещенная в Azure, может быть хорошим вариантом для определенных решений. В этой статье описано, как спроектировать решения SharePoint для обеспечения совместимости с платформой Azure. В качестве примеров используются два следующих решения:
  
- [Аварийное восстановление SharePoint Server 2013 в Microsoft Azure](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md)
    
- [Веб-сайты в Microsoft Azure с использованием SharePoint Server 2013](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md)
    
## <a name="recommended-sharepoint-solutions-for-azure-infrastructure-services"></a>Рекомендуемые решения SharePoint для служб инфраструктуры Azure

Azure infrastructure services is a compelling option for hosting SharePoint solutions. Some solutions are a better fit for this platform than others. The following table shows recommended solutions.
  
|**Решение**|**Преимущества работы с Azure**|
|:-----|:-----|
|Среды разработки и тестирования  <br/> |Создавать такие среды и управлять ими легко.  <br/> |
|Аварийное восстановление локальных ферм SharePoint в Azure  <br/> |**Размещенный вспомогательный центр обработки данных** Используйте Azure, чтобы не вкладывать средства во вспомогательный центр обработки данных в другом регионе. <br/> **Lower-cost disaster-recovery environments** Maintain and pay for fewer resources than an on-premises disaster recovery environment. The number of resources depends on the disaster recovery environment you choose: cold standby, warm standby, or hot standby. <br/> **More elastic platform** In the event of a disaster, easily scale-out your recovery SharePoint farm to meet load requirements. Scale in when you no longer need the resources. <br/> См. статью [Аварийное восстановление SharePoint Server 2013 в Microsoft Azure](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md).  <br/> |
|Веб-сайты, использующие функции и масштабируемые, не поддерживаемые в Microsoft 365  <br/> |**Правильные приоритеты** Сосредоточьтесь на создании отличного сайта, а не инфраструктуры. <br/> **Take advantage of elasticity in Azure** Size the farm for the demand by adding new servers, and pay only for resources you need. Dynamic machine allocation is not supported (auto scale). <br/> **Использование службы Azure Active Directory (AD)** Воспользуйтесь преимуществами Azure AD для учетных записей клиентов. <br/> **Добавление функций SharePoint, недоступных в Microsoft 365** Добавьте глубокую отчетность и Web Analytics. <br/> См. статью [Веб-сайты в Microsoft Azure с использованием SharePoint Server 2013](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md).  <br/> |
|Фермы приложений для поддержки Microsoft 365 или локальных сред  <br/> |**Создание, тестирование и размещение приложений** в Azure для поддержки как локальных, так и облачных сред. <br/> **Разместите эту роль** в Azure, не покупая новое оборудование для локальных сред. <br/> |
   
Для решений интрасети и совместной работы рассмотрите следующие факторы.
  
- Определите, соответствует ли Microsoft 365 требованиям бизнес-требований или является частью решения. Microsoft 365 предоставляет богатый набор функций, которые всегда актуальны.
    
- Если Microsoft 365 не отвечает всем бизнес-требованиям, рекомендуем использовать стандартную реализацию SharePoint 2013 в локальной среде консультационных служб Майкрософт (MCS). Поддерживать стандартную архитектуру может быть дешевле и проще, чем персонализированное решение. 
    
- Если стандартная реализация не соответствует вашим бизнес-требованиям, рекомендуется персонализированное локальное решение.
    
- If using a cloud platform is important for your business requirements, consider a standard or customized implementation of SharePoint 2013 hosted in Azure infrastructure services. SharePoint solutions are much easier to support in Azure than other non-native Microsoft public cloud platforms.
    
## <a name="before-you-design-the-azure-environment"></a>Перед разработкой среды Azure

While this article uses example SharePoint topologies, you can use these design concepts with any SharePoint farm topology. Before you design the Azure environment, use the following topology, architecture, capacity, and performance guidance to design the SharePoint farm:
  
- [Архитектура SharePoint 2013 для ИТ-специалистов](https://technet.microsoft.com/sharepoint/fp123594.aspx)
    
- [Plan for performance and capacity management in SharePoint Server 2013](https://technet.microsoft.com/library/8dd52916-f77d-4444-b593-1f7d6f330e5f.aspx)
    
## <a name="determine-the-active-directory-domain-type"></a>Определение типа домена Active Directory

Each SharePoint Server farm relies on Active Directory to provide administrative accounts for farm setup. At this time, there are two options for SharePoint solutions in Azure. These are described in the following table.
  
|**Вариант**|**Описание**|
|:-----|:-----|
|Выделенный домен  <br/> |You can deploy a dedicated and isolated Active Directory domain to Azure to support your SharePoint farm. This is a good choice for public-facing Internet sites.  <br/> |
|Расширение локального домена через подключение между организациями  <br/> |When you extend the on-premises domain through a cross-premises connection, users access the SharePoint farm via your intranet as if it were hosted on-premises. You can take advantage of your on-premises Active Directory and DNS implementation.  <br/> Для создания среды аварийного восстановления в Azure необходимо соединение между организациями, чтобы обрабатывать отказы локальной фермы.  <br/> |
   
This article includes design concepts for extending the on-premises domain through a cross-premises connection. If your solution uses a dedicated domain, you don't need a cross-premises connection.
  
## <a name="design-the-virtual-network"></a>Разработка виртуальной сети

First you need a virtual network in Azure, which includes subnets on which you will place your virtual machines. The virtual network needs a private IP address space, portions of which you assign to the subnets.
  
Если вы расширяете локальную сеть в Azure через подключение между организациями (требуется для среды аварийного восстановления), необходимо выбрать пространство частных адресов, которое еще не используется в сети организации и может включать локальную среду и другие виртуальные сети Azure. 
  
**Рисунок 1. Локальная среда с виртуальной сетью в Azure**

![Microsoft Azure virtual network design for a SharePoint solution. One subnet for the Azure gateway. One subnet for the virtual machines.](media/OPrrasconWA-AZarch.png)
  
На этой схеме:
  
- A virtual network in Azure is illustrated side-by-side to the on-premises environment. The two environments are not yet connected by a cross-premises connection, which can be a site-to-site VPN connection or ExpressRoute.
    
- At this point, the virtual network just includes the subnets and no other architectural elements. One subnet will host the Azure gateway and other subnets host the tiers of the SharePoint farm, with an additional one for Active Directory and DNS.
    
## <a name="add-cross-premises-connectivity"></a>Добавление подключения между организациями

The next deployment step is to create the cross-premises connection (if this applies to your solution). For cross-premises connections, a Azure gateway resides in a separate gateway subnet, which you must create and assign an address space. 
  
При планировании подключения между организациями необходимо определить и создать шлюз Azure и подключение к локальному устройству шлюза.
  
**Рисунок 2. Использование шлюза Azure и локального устройства шлюза для установки подключения типа "сеть-сеть" между локальной средой и Azure**

![Локальная среда подключена к виртуальной сети Azure с помощью VPN-подключения типа "сеть-сеть" или подключения ExpressRoute](media/AZarch-VPNgtwyconnct.png)
  
На этой схеме:
  
- В отличие от предыдущей схемы, здесь добавлено подключение между локальной средой и виртуальной сетью Azure (VPN-подключение типа "сеть-сеть" или подключение ExpressRoute).
    
- Шлюз Azure находится в подсети шлюза.
    
- Локальная среда включает устройство шлюза, например маршрутизатор или VPN-сервер.
    
Дополнительные сведения о планировании и создании распределенной виртуальной сети см. в статье [Подключение локальной сети к виртуальной сети Microsoft Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).
  
## <a name="add-active-directory-domain-services-ad-ds-and-dns"></a>Добавление доменных служб Active Directory (AD DS) и DNS

Для аварийного восстановления в Azure доменные службы AD на сервере Windows и DNS развертываются в гибридном сценарии, где AD на сервере Windows развертывается как в локальной среде, так и на виртуальных машинах Azure.
  
**Рисунок 3. Гибридная конфигурация домена Active Directory**

![Две виртуальные машины, развернутые в виртуальной сети Azure и подсети фермы SharePoint — это реплики контроллеров домена и DNS-серверы](media/AZarch-HyADdomainConfig.png)
  
This diagram builds on the previous diagrams by adding two virtual machines to a Windows Server AD and DNS subnet. These virtual machines are replica domain controllers and DNS servers. They are an extension of the on-premises Windows Server AD environment. 
  
The following table provides configuration recommendations for these virtual machines in Azure. Use these as a starting point for designing your own environment—even for a dedicated domain where your Azure environment doesn't communicate with your on-premises environment.
  
|**Элемент**|**Конфигурация**|
|:-----|:-----|
|Размер виртуальных машин в Azure  <br/> |Размер A1 или A2 стандартного уровня  <br/> |
|Операционная система  <br/> |Windows Server 2012 R2  <br/> |
|Роль Active Directory  <br/> |AD DS domain controller designated as a global catalog server. This configuration reduces egress traffic across the cross-premises connection.  <br/> В среде с несколькими доменами и высокими темпами роста (такие среды встречаются редко) настройте локальные контроллеры домена так, чтобы они не синхронизировались с серверами глобального каталога в Azure, что позволяет снизить трафик репликации.  <br/> |
|Роль DNS  <br/> |Установка и настройка службы DNS-серверов на контроллерах доменов.  <br/> |
|Диски с данными  <br/> |Place the Active Directory database, logs, and SYSVOL on additional Azure data disks. Do not place these on the operating system disk or the temporary disks provided by Azure.  <br/> |
|IP-адреса  <br/> |Используйте статические IP-адреса и настройте виртуальную сеть, чтобы назначить эти адреса виртуальным машинам в виртуальной сети после того, как будут настроены контроллеры доменов.  <br/> |
   
> [!IMPORTANT]
> Before you deploy Active Directory in Azure, read [Guidelines for Deploying Windows Server Active Directory on Azure Virtual Machines](https://go.microsoft.com/fwlink/p/?linkid=392681). These help you determine if a different architecture or different configuration settings are needed for your solution. 
  
## <a name="add-the-sharepoint-farm"></a>Добавление фермы SharePoint

Разместите виртуальные машины фермы SharePoint по уровням соответствующей подсети.
  
**Рисунок 4. Размещение виртуальных машин SharePoint**

![Серверы баз данных и роли сервера SharePoint добавлены в виртуальную сеть Azure в подсети фермы SharePoint](media/AZarch-SPVMsinCloudSer.png)
  
В отличие от предыдущих схем, на этой схеме на соответствующие уровни добавлены роли серверов фермы SharePoint.
  
- Две виртуальные машины баз данных, на которых запущен SQL Server, образуют уровень баз данных.
    
- Две виртуальные машины, на которых запущен SharePoint Server 2013, на каждый из следующих уровней: серверы переднего плана, серверы распределенного кэша и тыловые серверы.
    
## <a name="design-and-fine-tune-server-roles-for-availability-sets-and-fault-domains"></a>Разработка и точная настройка ролей серверов для групп доступности и доменов сбоя

A fault domain is a grouping of hardware in which role instances run. Virtual machines within the same fault domain can be updated by the Azure infrastructure at the same time. Or, they can fail at the same time because they share the same rack. To avoid the risk of having two virtual machines on the same fault domain, you can configure your virtual machines as an availability set, which ensures that each virtual machine is in a different fault domain. If three virtual machines are configured as an availability set, Azure guarantees that no more than two of the virtual machines are located in the same fault domain.
  
When you design the Azure architecture for a SharePoint farm, configure identical server roles to be part of an availability set. This ensures that your virtual machines are spread across multiple fault domains.
  
**Рисунок 5. Использование групп доступности Azure для обеспечения высокой доступности уровней фермы SharePoint**

![Конфигурация групп доступности в инфраструктуре Azure для решения SharePoint 2013](media/AZenv-WinAzureAvailSetsHA.png)
  
This diagram calls out the configuration of availability sets within the Azure infrastructure. Each of the following roles share a separate availability set:
  
- Active Directory и DNS
    
- База данных
    
- Тыловой сервер
    
- Сервер распределенного кэша
    
- Интерфейсный сервер
    
The SharePoint farm might need to be fine tuned in the Azure platform. To ensure high availability of all components, ensure that the server roles are all configured identically.
  
Here is an example that shows a standard Internet Sites architecture that meets specific capacity and performance goals. This example is featured in the following architecture model: [Internet Sites Search Architectures for SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=261519).
  
**Рисунок 6. Пример планирования емкости и производительности в трехуровневой ферме**

![Стандартная архитектура SharePoint 2013 Internet Sites с распределением компонентов, которое соответствует определенным требованиям к мощности и производительности](media/AZarch-CapPerfexmpArch.png)
  
На этой схеме:
  
- Представлена трехуровневая ферма: веб-серверы, серверы приложений и серверы баз данных;
    
- Три веб-сервера настроены одинаково с несколькими компонентами.
    
- Два сервера баз данных настроены одинаково.
    
- The three application servers are not configured identically. These server roles require fine tuning for availability sets in Azure.
    
Рассмотрим уровень серверов приложений подробнее.
  
**Рисунок 7. Уровень серверов приложений перед точной настройкой**

![Пример уровня серверов приложений SharePoint Server 2013 перед настройкой для групп доступности Microsoft Azure](media/AZarch-AppServtierBefore.png)
  
На этой схеме:
  
- уровень приложений включает три сервера;
    
- первый сервер включает четыре компонента;
    
- второй сервер включает три компонента;
    
- третий сервер включает два компонента.
    
You determine the number of components by the performance and capacity targets for the farm. To adapt this architecture for Azure, we'll replicate the four components across all three servers. This increases the number of components beyond what is necessary for performance and capacity. The tradeoff is that this design ensures high availability of all four components in the Azure platform when these three virtual machines are assigned to an availability set.
  
**Рисунок 8. Уровень серверов приложений после точной настройки**

![Пример уровня серверов приложений SharePoint Server 2013 после настройки для групп доступности Microsoft Azure](media/AZarch-AppServtierAfter.png)
  
На этой схеме показаны все три сервера приложений, настроенных одинаково с одними и теми же четырьмя компонентами.
  
После того как мы добавили к уровням фермы SharePoint группы доступности, этап реализации завершен.
  
**Рисунок 9. Готовая ферма SharePoint в службах инфраструктуры Azure**

![Пример фермы SharePoint 2013 в службах инфраструктуры Azure с виртуальной сетью, подключением между организациями, подсетями, виртуальными машинами и группами доступности](media/7256292f-bf11-485b-8917-41ba206153ee.png)
  
На этой схеме показана ферма SharePoint, реализованная в службах инфраструктуры Azure: группы доступности обеспечивают домены сбоя для серверов на каждом уровне.
  
## <a name="see-also"></a>См. также

[Освоение облака и гибридные решения](cloud-adoption-and-hybrid-solutions.yml)
  
[Веб-сайты в Microsoft Azure с использованием SharePoint Server 2013](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md)
  
[Аварийное восстановление SharePoint Server 2013 в Microsoft Azure](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md)


