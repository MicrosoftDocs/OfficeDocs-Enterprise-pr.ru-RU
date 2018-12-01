---
title: Сценарии гибридного облака для Microsoft SaaS (Office 365)
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/30/2018
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: db117e59-389f-46f5-a5df-4eeac0040aa8
description: 'Сводка: Сведения о гибридных архитектуры и сценарии для Майкрософт на основе SaaS в облаке и услуги (Office 365).'
ms.openlocfilehash: 063cbd03a2cc65a6cd278ab2efcea235079f801b
ms.sourcegitcommit: 943d58b89459cd1edfc82e249c141d42dcf69641
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/01/2018
ms.locfileid: "27123416"
---
# <a name="hybrid-cloud-scenarios-for-microsoft-saas-office-365"></a>Гибридные облачные сценарии для SaaS Майкрософт (Office 365)

 **Сводка:** Представление об архитектуре гибридного и сценарии для Майкрософт на основе SaaS в облаке и услуги (Office 365).
  
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
    
  - SharePoint Server 2019 SharePoint Server 2016 и SharePoint Server 2013 в сочетании со службой SharePoint Online (несколько сценариев)
    
    Кроме того, есть следующий перекрестный гибридный сценарий: Exchange Online с локальным приложением Skype для бизнеса Server.
    
- Удостоверение
    
    Может включать синхронизацию службы каталогов с локальным каталогом Windows Server AD. В качестве альтернативы можно настроить федерацию Azure AD со сторонним поставщиком удостоверений.
    
- Сеть
    
    Состоит из имеющегося интернет-канала или подключения ExpressRoute с пирингом Майкрософт для Office 365 или Dynamics 365.
    
- Локальная среда
    
    Может состоять из имеющихся серверов Exchange, SharePoint и Skype для бизнеса, которые необходимо обновить до последних версий. После этого их можно объединить с аналогичными серверами Office 365 для гибридных сценариев.
    
Настройка среды разработки или тестирования Office 365, просмотрите [Руководства по лаборатории тестирования 365 Office](cloud-adoption-test-lab-guides-tlgs.md).
  
## <a name="skype-for-business-hybrid"></a>Скайп для гибридных бизнеса

Скайп для гибридной среды Business позволяет объединять существующей в локальной среде с Скайп для бизнеса в Интернет. Некоторые пользователи, размещенные локально и некоторые пользователи размещаются в Интернете, но пользователи совместно использовать один домен Session Initiation Protocol (SIP), например contoso.com. В этом гибридной конфигурации можно использовать для переноса из локальной в Office 365 со временем в расписании. Скайп для бизнеса можно объединить с [Exchange Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/integration-with-exchange-and-sharepoint).
  
**На рисунке 2: Скайп для бизнеса гибридной конфигурации**

![Скайп для бизнеса гибридной конфигурации](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SfB.png)
  
На рисунке 2 показано Скайп для бизнеса гибридной конфигурации, состоящий из локальной Скайп для бизнеса интерфейсного пула и пограничного сервера связи с Скайп для бизнеса в Интернет в Office 365.
  
Дополнительные сведения см в [планировании гибридного подключения между Скайп Business Server и Скайп для бизнеса в Интернет](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-hybrid-connectivity).
    
## <a name="cloud-pbx-with-skype-for-business-server"></a>Облачная УАТС со Skype для бизнеса Server

Облако УАТС с Скайп для Business Server позволяет перенос существующих Скайп для локального развертывания Business Server к топологии для подключения к общедоступной переключения телефонной сети общего пользования (PSTN) для локальной. 
  
**Рис. 3. Облачная УАТС со Skype для бизнеса Server**

![Облачная УАТС со Skype для бизнеса Server](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SfB-CloudPBX.png)
  
На рисунке 3 показаны облачных УАТС с Скайп для конфигурации Business Server, состоящий из локальной, существующей УАТС или Telco шлюз, Скайп для Business Server и PSTN подключенный к УАТС облаке Майкрософт в Office 365, который включает в себя Скайп для бизнеса Онлайн.
  
Пользователи в организации, расположенные в облаке, могут получать из облака Майкрософт службы УАТС, которые включают в себя передачу сигналов и голосовую почту, но подключение к ТСОП (гудок) осуществляется с помощью корпоративной голосовой связи из локального развертывания Skype для бизнеса Server.
  
Это является хорошим примером гибридной конфигурации, которое позволяет постепенно перенос в облачной службе. Возможности голосовой связи пользователей можно сохранить при начале переместите их Скайп для бизнеса в Интернет. Вы можете переместить пользователей в свои собственные ходом презентации знать, что их функций голосовой связи будет продолжить нет данному которых они размещены. 
  
Дополнительные сведения см в [планировании гибридного подключения между Скайп Business Server и Скайп для бизнеса в Интернет](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-hybrid-connectivity).
  
Если у вас пока не развернуто решение Lync Server или Skype для бизнеса Server, вы можете использовать Cloud Connector Edition для Skype для бизнеса, набор упакованных виртуальных машин, которые реализуют возможность подключения к ТСОП с помощью облачной УАТС.
  
Для получения дополнительных сведений см [Скайп облаке соединитель для выпуска для бизнеса](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-your-phone-system-cloud-pbx-solution/plan-skype-for-business-cloud-connector-edition).

  
## <a name="sharepoint-hybrid"></a>Гибридная среда SharePoint

Гибридная среда SharePoint объединяет SharePoint Online в Office 365 с локальной фермой SharePoint в оптимальном решении с возможностями обоих продуктов.
  
**Рис. 4. Гибридная конфигурация SharePoint**

![Гибридная конфигурация SharePoint](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SP.png)
  
На рисунке 4 показано гибридной конфигурации SharePoint, состоящий из локальной фермы SharePoint, данными с SharePoint Online в Office 365.
  
Гибридные сценарии SharePoint
  
- [Гибридная служба OneDrive для бизнеса](https://docs.microsoft.com/SharePoint/hybrid/configure-hybrid-onedrive-for-businessroadmap)
    
- [Гибридные B2B экстрасети](https://docs.microsoft.com/sharepoint/create-b2b-extranet)
    
- [Гибридный поиск](https://docs.microsoft.com/SharePoint/hybrid/configure-cloud-hybrid-searchroadmap)
    
- [Гибридные профили](https://docs.microsoft.com/SharePoint/hybrid/plan-hybrid-profiles)
    
- [Средство выбора гибридного](https://docs.microsoft.com/SharePoint/hybrid/hybrid-picker-in-the-sharepoint-online-admin-center)
    
    Гибридные сценарии можно легко включить с помощью мастеров, которые автоматически реализуют гибридные конфигурации, доступные в Центре администрирования SharePoint Online в Office 365.
    
- [Расширяемое гибридное средство запуска приложений](https://docs.microsoft.com/SharePoint/hybrid/the-extensible-hybrid-app-launcher)
    
    Позволяет пользователям просматривать и использовать видео Office 365, а также приложения и возможности Delve на страницах их локальной фермы SharePoint.
    
Все эти гибридные сценарии SharePoint, за исключением расширяемого гибридного средства запуска приложений, доступны пользователям SharePoint 2016 и SharePoint 2013.
  
## <a name="exchange-server-2016-hybrid"></a>Гибридный сценарий в Exchange Server 2016

Гибридный сценарий в Exchange Server 2016 позволяет пользователям в сети воспользоваться преимуществами Exchange Online в Office 365, в то время как локальные пользователи смогут и дальше использовать имеющуюся инфраструктуру Exchange Server.  
  
**Рис. 5. Гибридная конфигурация Exchange 2016**

![Гибридная конфигурация Exchange 2016](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-EX.png)
  
На рисунке 5 показана конфигурация гибридного Exchange 2016, состоящий из локальных серверов почтовых ящиков Exchange связи с почтовых ящиков в Office 365 и Exchange Online Protection.
  
Некоторые пользователи применяют локальный сервер электронной почты, а другие — Exchange Online, но все пользователи совместно используют одно пространство адресов электронной почты.  
  
Эта гибридная конфигурация:
  
- использует имеющуюся инфраструктуру Exchange Server при постепенном переносе данных на Exchange Online по расписанию;



    
- позволяет обеспечить поддержку удаленных сайтов без инвестиций в создание инфраструктуры филиалов;
    
- позволяет направить входящую электронную почту через Exchange Online Protection в Office 365;
    
- выполняет задачи транснациональных организаций с дочерними компаниями, которым необходимо локальное размещение данных.
    
Вы также можете интегрировать эту гибридную конфигурацию с другими приложениями Microsoft Office 365, в том числе Skype для бизнеса Online и SharePoint Online.
  
Для получения дополнительных сведений см [Гибридные развертывания Exchange Server](https://docs.microsoft.com/exchange/exchange-hybrid).
  
## <a name="see-also"></a>См. также

[Гибридное облако Майкрософт для корпоративных архитекторов](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[Ресурсы для администраторов, посвященные архитектуре Microsoft Cloud](microsoft-cloud-it-architecture-resources.md)

