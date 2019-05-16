---
title: Сценарии гибридного облака для Microsoft SaaS (Office 365)
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/30/2018
audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: db117e59-389f-46f5-a5df-4eeac0040aa8
description: Сводка. сведения о гибридной архитектуре и сценариях для облачных услуг Майкрософт на основе SaaS (Office 365).
ms.openlocfilehash: 84092fe419ab31fca7763f434e328eb855d46835
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067225"
---
# <a name="hybrid-cloud-scenarios-for-microsoft-saas-office-365"></a>Гибридные облачные сценарии для SaaS Майкрософт (Office 365)

 **Сводка:** Узнайте, как гибридная архитектура и сценарии для облачных услуг Майкрософт на основе SaaS (Office 365).
  
Объедините локальные развертывания Exchange, SharePoint или Skype для бизнеса с их аналогами в Office 365 в рамках переноса в облако или стратегии долгосрочной интеграции.
  
## <a name="microsoft-saas-hybrid-scenario-architecture"></a>Архитектура гибридного сценария Microsoft SaaS

На рисунке 1 показана архитектура гибридных сценариев на основе Microsoft SaaS для Office 365.
  
**Рис. 1. Гибридные сценарии на основе Microsoft SaaS для Office 365**

![Гибридные сценарии на основе Microsoft SaaS для Office 365](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS.png)
  
Для каждого слоя архитектуры:
  
- Приложения и сценарии
    
    Существуют различные гибридные сценарии на основе SaaS, использующие серверные продукты Office и их аналоги в Office 365:
    
  - Exchange Server в сочетании с Exchange Online (гибридная среда Exchange Server);
    
  - Skype для бизнеса Server в сочетании со Skype для бизнеса Online, а также новые сценарии "Облачная УАТС" и Cloud Connector Edition;
    
  - SharePoint Server 2019, SharePoint Server 2016 или SharePoint Server 2013 в сочетании с SharePoint Online (несколько сценариев)
    
    Кроме того, есть следующий перекрестный гибридный сценарий: Exchange Online с локальным приложением Skype для бизнеса Server.
    
- Удостоверение
    
    Может включать синхронизацию службы каталогов с локальными доменными службами Active Directory (AD DS). В качестве альтернативы можно настроить федерацию Azure AD со сторонним поставщиком удостоверений.
    
- Сеть
    
    Состоит из имеющегося интернет-канала или подключения ExpressRoute с пирингом Майкрософт для Office 365 или Dynamics 365.
    
- Локальная среда
    
    Может состоять из имеющихся серверов Exchange, SharePoint и Skype для бизнеса, которые необходимо обновить до последних версий. После этого их можно объединить с аналогичными серверами Office 365 для гибридных сценариев.
    
Настройте собственную среду разработки и тестирования Office 365, ознакомьтесь с [руководством по лаборатории тестирования office 365](cloud-adoption-test-lab-guides-tlgs.md).
  
## <a name="skype-for-business-hybrid"></a>Гибридное развертывание Skype для бизнеса

Гибридная среда Skype для бизнеса позволяет объединить существующее локальное развертывание с Skype для бизнеса Online. Часть пользователей размещена в локальной среде, а другая часть — в Интернете, но все они используют один домен SIP, например contoso.com. Эта гибридная конфигурация позволяет постепенно перенести данные из локальной среды в Office 365 по заданному вами расписанию. Skype для бизнеса также может быть интегрирован с [Exchange Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/integration-with-exchange-and-sharepoint).
  
**Рисунок 2: Гибридная конфигурация Skype для бизнеса**

![Гибридная конфигурация Skype для бизнеса](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SfB.png)
  
На рисунке 2 показана гибридная конфигурация Skype для бизнеса, состоящая из локального интерфейсного пула Skype для бизнеса и пограничного сервера, взаимодействующего со Skype для бизнеса Online в Office 365.
  
Для получения дополнительных сведений ознакомьтесь [со статьей Планирование гибридного подключения между Skype для бизнеса Server и Skype для бизнеса Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-hybrid-connectivity).
    
## <a name="cloud-pbx-with-skype-for-business-server"></a>Облачная УАТС со Skype для бизнеса Server

Облачная УАТС со Skype для бизнеса Server позволяет переходить из существующего локального развертывания Skype для бизнеса Server в топологию с подключением к локальной телефонной сети общего пользования (PSTN). 
  
**Рис. 3. Облачная УАТС со Skype для бизнеса Server**

![Облачная УАТС со Skype для бизнеса Server](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SfB-CloudPBX.png)
  
На рисунке 3 показана облачная УАТС с конфигурацией Skype для бизнеса Server, состоящей из локального существующего шлюза УАТС или Telco, Skype для бизнеса Server и PSTN, подключенного к облачной УАТС Майкрософт в Office 365, которая включает Skype для бизнеса Онлайн.
  
Пользователи в организации, расположенные в облаке, могут получать из облака Майкрософт службы УАТС, которые включают в себя передачу сигналов и голосовую почту, но подключение к ТСОП (гудок) осуществляется с помощью корпоративной голосовой связи из локального развертывания Skype для бизнеса Server.
  
Это отличный пример гибридной конфигурации, который позволяет постепенно переходить на облачную службу. При переносе функций голосовой связи своих пользователей в Skype для бизнеса в Online вы можете сохранить эти функции. Перенос пользователей может выполняться в удобном для вас режиме, при этом вы можете быть уверены в том, что функции голосовой связи будут сохранены независимо от расположения пользователей. 
  
Для получения дополнительных сведений ознакомьтесь [со статьей Планирование гибридного подключения между Skype для бизнеса Server и Skype для бизнеса Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-hybrid-connectivity).
  
Если у вас пока не развернуто решение Lync Server или Skype для бизнеса Server, вы можете использовать Cloud Connector Edition для Skype для бизнеса, набор упакованных виртуальных машин, которые реализуют возможность подключения к ТСОП с помощью облачной УАТС.
  
Более подробную информацию можно найти в статье [Plan for Skype for Business Cloud Connector Edition](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-your-phone-system-cloud-pbx-solution/plan-skype-for-business-cloud-connector-edition).

  
## <a name="sharepoint-hybrid"></a>Гибридная среда SharePoint

Гибридная среда SharePoint объединяет SharePoint Online в Office 365 с локальной фермой SharePoint в оптимальном решении с возможностями обоих продуктов.
  
**Рис. 4. Гибридная конфигурация SharePoint**

![Гибридная конфигурация SharePoint](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SP.png)
  
На рисунке 4 показана гибридная конфигурация SharePoint, состоящая из локальной фермы SharePoint, которая взаимодействует с SharePoint Online в Office 365.
  
Гибридные сценарии SharePoint
  
- [Гибридная служба OneDrive для бизнеса](https://docs.microsoft.com/SharePoint/hybrid/configure-hybrid-onedrive-for-businessroadmap)
    
- [Гибридная сеть B2B](https://docs.microsoft.com/sharepoint/create-b2b-extranet)
    
- [Гибридный поиск](https://docs.microsoft.com/SharePoint/hybrid/configure-cloud-hybrid-searchroadmap)
    
- [Гибридные профили](https://docs.microsoft.com/SharePoint/hybrid/plan-hybrid-profiles)
    
- [Мастер выбора гибридной конфигурации](https://docs.microsoft.com/SharePoint/hybrid/hybrid-picker-in-the-sharepoint-online-admin-center)
    
    Гибридные сценарии можно легко включить с помощью мастеров, которые автоматически реализуют гибридные конфигурации, доступные в Центре администрирования SharePoint Online в Office 365.
    
- [Расширяемое гибридное средство запуска приложений](https://docs.microsoft.com/SharePoint/hybrid/the-extensible-hybrid-app-launcher)
    
    Позволяет пользователям просматривать и использовать видео Office 365, а также приложения и возможности Delve на страницах их локальной фермы SharePoint.
    
Все эти гибридные сценарии SharePoint, за исключением расширяемого гибридного средства запуска приложений, доступны пользователям SharePoint 2016 и SharePoint 2013.
  
## <a name="exchange-server-2016-hybrid"></a>Гибридный сценарий в Exchange Server 2016

Гибридный сценарий в Exchange Server 2016 позволяет пользователям в сети воспользоваться преимуществами Exchange Online в Office 365, в то время как локальные пользователи смогут и дальше использовать имеющуюся инфраструктуру Exchange Server.  
  
**Рис. 5. Гибридная конфигурация Exchange 2016**

![Гибридная конфигурация Exchange 2016](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-EX.png)
  
На рисунке 5 показана гибридная конфигурация Exchange 2016, состоящая из локальных серверов почтовых ящиков Exchange, взаимодействующих с Exchange Online Protection и почтовыми ящиками в Office 365.
  
Некоторые пользователи применяют локальный сервер электронной почты, а другие — Exchange Online, но все пользователи совместно используют одно пространство адресов электронной почты.  
  
Эта гибридная конфигурация:
  
- использует имеющуюся инфраструктуру Exchange Server при постепенном переносе данных на Exchange Online по расписанию;
    
- позволяет обеспечить поддержку удаленных сайтов без инвестиций в создание инфраструктуры филиалов;
    
- позволяет направить входящую электронную почту через Exchange Online Protection в Office 365;
    
- выполняет задачи транснациональных организаций с дочерними компаниями, которым необходимо локальное размещение данных.
    
Вы также можете интегрировать эту гибридную конфигурацию с другими приложениями Microsoft Office 365, в том числе Skype для бизнеса Online и SharePoint Online.
  
Для получения дополнительных сведений обратитесь к разделу [Гибридные развертывания Exchange Server](https://docs.microsoft.com/exchange/exchange-hybrid).
  
## <a name="see-also"></a>См. также

[Гибридное облако Майкрософт для корпоративных архитекторов](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[Ресурсы для администраторов, посвященные архитектуре Microsoft Cloud](microsoft-cloud-it-architecture-resources.md)

