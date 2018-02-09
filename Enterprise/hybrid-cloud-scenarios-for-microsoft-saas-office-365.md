---
title: "Сценарии гибридного облака для Microsoft SaaS (Office 365)"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: db117e59-389f-46f5-a5df-4eeac0040aa8
description: "Сводка: Сведения о гибридных архитектуры и сценарии для Майкрософт на основе SaaS в облаке и услуги (Office 365)."
ms.openlocfilehash: 65b1841a155e286af8862c2fb7c37d0bfb61e1e8
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="hybrid-cloud-scenarios-for-microsoft-saas-office-365"></a>Сценарии гибридного облака для Microsoft SaaS (Office 365)

 **Сводка:** Представление об архитектуре гибридного и сценарии для Майкрософт на основе SaaS в облаке и услуги (Office 365).
  
Объедините локальные развертывания Exchange, SharePoint или Skype для бизнеса с их аналогами в Office 365 в рамках переноса в облако или стратегии долгосрочной интеграции.
  
## <a name="microsoft-saas-hybrid-scenario-architecture"></a>Архитектура гибридного сценария Microsoft SaaS

На рисунке 1 показана архитектура гибридных сценариев на основе Microsoft SaaS для Office 365.
  
**На рисунке 1: Майкрософт на основе SaaS гибридных сценариев для Office 365**

![Гибридные сценарии на основе Microsoft SaaS для Office 365](images/Hybrid_Poster/Hybrid_Cloud_Stack_SaaS.png)
  
Для каждого слоя архитектуры:
  
- Приложения и сценарии
    
    Существуют различные гибридные сценарии на основе SaaS, использующие серверные продукты Office и их аналоги в Office 365:
    
  - Exchange Server в сочетании с Exchange Online (гибридная среда Exchange Server);
    
  - Skype для бизнеса Server в сочетании со Skype для бизнеса Online, а также новые сценарии "Облачная УАТС" и Cloud Connector Edition;
    
  - SharePoint Server 2016 или SharePoint Server 2013 в сочетании с SharePoint Online (несколько сценариев).
    
    Кроме того, есть следующий перекрестный гибридный сценарий: Exchange Online с локальным приложением Skype для бизнеса Server.
    
- Удостоверение
    
    Может включать синхронизацию службы каталогов с локальным каталогом Windows Server AD. В качестве альтернативы можно настроить федерацию Azure AD со сторонним поставщиком удостоверений.
    
- Сеть
    
    Состоит из имеющегося интернет-канала или подключения ExpressRoute с пирингом Майкрософт для Office 365 или Dynamics 365.
    
- Локальная среда
    
    Может состоять из имеющихся серверов Exchange, SharePoint и Skype для бизнеса, которые необходимо обновить до последних версий. После этого их можно объединить с аналогичными серверами Office 365 для гибридных сценариев.
    
Настройка собственных [Office 365 dev/тестовой среды](office-365-dev-test-environment.md).
  
## <a name="skype-for-business-2015-hybrid"></a>Гибридный сценарий в Skype для бизнеса 2015

Скайп для гибридных 2015 Business позволяет объединять существующей в локальной среде с Скайп для бизнеса в Интернет. Некоторые пользователи, размещенные локально и некоторые пользователи размещаются в Интернете, но пользователи совместно использовать один домен Session Initiation Protocol (SIP), например contoso.com. В этом гибридной конфигурации можно использовать для переноса из локальной в Office 365 со временем в расписании. Скайп для бизнеса 2015 можно объединить с Exchange Online.
  
**На рисунке 2: Скайп для бизнеса 2015 гибридной конфигурации**

![Гибридная конфигурация Skype для бизнеса 2015](images/Hybrid_Poster/Hybrid_Cloud_Stack_SaaS_SfB.png)
  
На рисунке 2 показано Скайп для бизнеса 2015 гибридной конфигурации, состоящий из локальной Скайп для бизнеса 2015 интерфейсного пула и пограничного сервера связи с Скайп для бизнеса в Интернет в Office 365.
  
Дополнительные сведения см. в следующих разделах:
  
- [Планирование гибридного подключения между Скайп для Business Server и Скайп для бизнеса в Интернет](https://technet.microsoft.com/library/jj205403.aspx)
    
- [Поддерживаемые гибридные конфигурации для Скайп Business Server 2015](https://technet.microsoft.com/library/jj945633.aspx)
    
- [Скайп для гибридных бизнеса](http://hybrid.office.com/skype-for-business/)
    
## <a name="cloud-pbx-with-skype-for-business-server"></a>Облачная УАТС со Skype для бизнеса Server

Сценарий "Облачная УАТС со Skype для бизнеса Server" позволяет перенести имеющееся локальное развертывание Skype для бизнеса Server на топологию с возможностью подключения к локальной телефонной сети общего пользования (ТСОП).  
  
**На рисунке 3: Cloud УАТС с Скайп для Business Server**

![Облачная УАТС со Skype для бизнеса Server](images/Hybrid_Poster/Hybrid_Cloud_Stack_SaaS_SfB_CloudPBX.png)
  
На рисунке 3 показаны облачных УАТС с Скайп для конфигурации Business Server, состоящий из локальной, существующей УАТС или Telco шлюз, Скайп для Business Server и PSTN подключенный к УАТС облаке Майкрософт в Office 365, который включает в себя Скайп для бизнеса Онлайн.
  
Пользователи в организации, расположенные в облаке, могут получать из облака Майкрософт службы УАТС, которые включают в себя передачу сигналов и голосовую почту, но подключение к ТСОП (гудок) осуществляется с помощью корпоративной голосовой связи из локального развертывания Skype для бизнеса Server.
  
Вот хороший пример гибридной конфигурации, которая позволяет выполнить постепенный перенос в облачную службу. При переносе функций голосовой связи своих пользователей в Skype для бизнеса в Online вы можете сохранить эти функции. Перенос пользователей может выполняться в удобном для вас режиме, при этом вы можете быть уверены в том, что функции голосовой связи будут сохранены независимо от расположения пользователей.  
  
Дополнительные сведения см в [планировании гибридного подключения между Скайп Business Server и Скайп для бизнеса в Интернет или Lync Server 2013](https://technet.microsoft.com/library/jj205403.aspx).
  
Если у вас пока не развернуто решение Lync Server или Skype для бизнеса Server, вы можете использовать Cloud Connector Edition для Skype для бизнеса, набор упакованных виртуальных машин, которые реализуют возможность подключения к ТСОП с помощью облачной УАТС.
  
Для получения дополнительных сведений см [Скайп облаке соединитель для выпуска для бизнеса](https://technet.microsoft.com/library/mt605227.aspx).
  
## <a name="sharepoint-hybrid"></a>Гибридная среда SharePoint

Гибридная среда SharePoint объединяет SharePoint Online в Office 365 с локальной фермой SharePoint в оптимальном решении с возможностями обоих продуктов.
  
**На рисунке 4: Гибридной конфигурации SharePoint**

![Гибридная конфигурация SharePoint](images/Hybrid_Poster/Hybrid_Cloud_Stack_SaaS_SP.png)
  
На рисунке 4 показано гибридной конфигурации SharePoint, состоящий из локальной фермы SharePoint, данными с SharePoint Online в Office 365.
  
Гибридные сценарии SharePoint
  
- [Гибридные OneDrive для бизнеса](https://technet.microsoft.com/library/mt147425%28v=office.16%29.aspx)
    
- [Гибридные веб-сайтов групп](https://technet.microsoft.com/library/mt346110%28v=office.16%29.aspx)
    
- [Гибридные B2B экстрасети](https://support.office.com/article/SharePoint-Business-to-Business-Collaboration-Extranet-for-Partners-with-Office-365-7b087413-165a-4e94-8871-4393e0b9c037)
    
- [Гибридного поиска](https://technet.microsoft.com/library/dn720906%28v=office.16%29.aspx)
    
- [Гибридные профилей](https://support.office.com/article/Plan-hybrid-profiles-96d1eaf0-94eb-40c5-ab76-c82907777db4)
    
- [Средство выбора гибридного](https://support.office.com/article/Hybrid-picker-in-the-SharePoint-Online-admin-center-efce8417-c9bc-4a2c-ac9d-cce6c4e84a9c)
    
    Гибридные сценарии можно легко включить с помощью мастеров, которые автоматически реализуют гибридные конфигурации, доступные в Центре администрирования SharePoint Online в Office 365.
    
- [Расширяемые гибридного запуска приложения](https://support.office.com/article/The-extensible-hybrid-app-launcher-617a7cb5-53da-4128-961a-64a840c0ab91)
    
    Позволяет пользователям просматривать и использовать видео Office 365, а также приложения и возможности Delve на страницах их локальной фермы SharePoint.
    
Все эти гибридные сценарии SharePoint, за исключением расширяемого гибридного средства запуска приложений, доступны пользователям SharePoint 2016 и SharePoint 2013.
  
Для получения дополнительных сведений см [Гибридной среды SharePoint](http://hybrid.office.com/sharepoint/).
  
## <a name="exchange-server-2016-hybrid"></a>Гибридный сценарий в Exchange Server 2016

Гибридный сценарий в Exchange Server 2016 позволяет пользователям в сети воспользоваться преимуществами Exchange Online в Office 365, в то время как локальные пользователи смогут и дальше использовать имеющуюся инфраструктуру Exchange Server.  
  
**На рисунке 5: Exchange 2016 гибридной конфигурации**

![Гибридная конфигурация Exchange 2016](images/Hybrid_Poster/Hybrid_Cloud_Stack_SaaS_EX.png)
  
На рисунке 5 показана конфигурация гибридного Exchange 2016, состоящий из локальных серверов почтовых ящиков Exchange связи с почтовых ящиков в Office 365 и Exchange Online Protection.
  
Некоторые пользователи применяют локальный сервер электронной почты, а другие — Exchange Online, но все пользователи совместно используют одно пространство адресов электронной почты.  
  
Эта гибридная конфигурация:
  
- Использует существующую инфраструктуру Exchange Server при переходе на Exchange Online со временем в расписании.
    
- позволяет обеспечить поддержку удаленных сайтов без инвестиций в создание инфраструктуры филиалов;
    
- позволяет направить входящую электронную почту через Exchange Online Protection в Office 365;
    
- выполняет задачи транснациональных организаций с дочерними компаниями, которым необходимо локальное размещение данных.
    
Вы также можете интегрировать эту гибридную конфигурацию с другими приложениями Microsoft Office 365, в том числе Skype для бизнеса Online и SharePoint Online.
  
Для получения дополнительных сведений см [Гибридные развертывания Exchange Server](https://technet.microsoft.com/library/jj200581%28v=exchg.150%29.aspx) и [Гибридное развертывание Exchange](http://hybrid.office.com/exchange/).
  
## <a name="see-also"></a>См. также

[Гибридное облако Майкрософт для корпоративных архитекторов](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[Ресурсы для администраторов, посвященные архитектуре Microsoft Cloud](microsoft-cloud-it-architecture-resources.md)

[Стратегия Enterprise Cloud корпорации Майкрософт: ресурсы для лиц, принимающих решения в области ИТ](https://sway.com/FJ2xsyWtkJc2taRD)



