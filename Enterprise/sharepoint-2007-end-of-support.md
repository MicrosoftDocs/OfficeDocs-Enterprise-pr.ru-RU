---
title: План действий после прекращения поддержки SharePoint Server 2007;
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 1/31/2018
ms.audience: ITPro
ms.topic: conceptual
f1_keywords:
- vsemail
- MS_WSS_DirectoryManagement
- MS_WSS_ConfigEmail
- globalemailconfig
- configssc
- AppDefToBDC
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
search.appverid:
- MET150
- OFU120
- SPS150
- OSU140
- WSU120
- OSR120
- SPO160
- PJW120
- SPB160
- OSI150
- OSI160
- BSA160
- OSU160
ms.assetid: ba124775-d5c0-4d68-b88d-8458ad4c3717
description: На 10 октября 2017 поддержка закончилась для SharePoint Server 2007. В этой статье, чтобы узнать о варианты обновления, устранение неполадок, советы и рекомендации, требования к системе, шагов для обновления и получение справки партнеров Майкрософт.
ms.openlocfilehash: b548e7623a72d57793c18409a80506bb832df858
ms.sourcegitcommit: a9c84d02e94c99ff6b1099b4a9ae695be08210e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/25/2018
ms.locfileid: "21169801"
---
# <a name="sharepoint-server-2007-end-of-support-roadmap"></a>План действий после прекращения поддержки SharePoint Server 2007;

На **10 октября 2017**Microsoft Office SharePoint Server 2007 достигнут конец поддержки. Если вы еще не начали миграции из SharePoint Server 2007 в Office 365 или более поздней версии SharePoint Server в локальной, пришло время для начала планирования. В этой статье приведены сведения о ресурсы, которые помогут пользователям перенос данных в SharePoint Online или обновления SharePoint Server на локальную. 
  
## <a name="what-does-end-of-support-mean"></a>Окончание поддержки среднее какие работает?

SharePoint Server, как и практически во всех продуктов Майкрософт, имеет жизненный цикл поддержки, во время которого корпорация Майкрософт предоставляет новые функции, исправления ошибок, исправления безопасности и т. д. Обычно этот жизненный цикл продолжается десять лет с момента первоначального выпуска продукта и конечных этот жизненный цикл называется окончание поддержки продукта. В конце поддержки Корпорация Майкрософт больше не предоставляет:
  
- Технической поддержки для решения проблем, которые могут возникнуть;
    
- Исправления ошибок, проблем, обнаруженных и, которое может повлиять на надежность и удобство использования сервера;
    
- Исправления безопасности для уязвимостей, обнаруженных и, которое может сделать сервер подвержена нарушения безопасности; и 
    
- Обновления для часового пояса.
    
Тем не менее фермы SharePoint Server 2007 по-прежнему будут действующие после 10 октября 2017, без дальнейших обновлений, исправления, или исправления будет был включен для продукта (включая исправления исправления) и службы поддержки Майкрософт будет полностью изменились борьбе поддержки более поздних версий продукта. Так как установки будет больше не поддерживаются или исправления, как конец поддержки подходов следует обновить продукт, или перенос важных данных.
  
> [!TIP]
> Если вы еще не планируется для обновления или переноса, вы можете найти: [варианты перехода SharePoint 2007, которые необходимо учитывать](sharepoint-2007-migration-options.md), некоторые примеры того, где начинать. Можно также выполнить поиск для [Партнеров Майкрософт](https://go.microsoft.com/fwlink/?linkid=841249) , которые смогут помочь с обновления и миграции в Office 365 (или оба). 
  
Дополнительные сведения о достигает окончание поддержки серверов выпуска 2007 системы Office в разделе [Планирование обновления для серверов выпуска 2007 системы Office](https://support.office.com/article/4e5eab5f-05db-4627-9e17-421a6bf89606.aspx).
  
## <a name="what-are-my-options"></a>Что такое параметры?

Первый этап должен быть [узел жизненный цикл продукта](https://go.microsoft.com/fwlink/?linkid=843148). При наличии продуктом Microsoft локальной, который срокам, необходимо проверить наличие его поддержки Дата окончания таким образом, год или это out - или до тех пор, пока вашей миграции обычно требуются - можно запланировать обновление или перенос. При выборе к следующему шагу, полезно думаете, что может быть достаточно, лучше и рекомендации в отношении возможности продукта. Ниже приведен пример:
  
|**Хороший**|**Лучше**|**Лучший**|
|:-----|:-----|:-----|
|SharePoint Server 2010  <br/> |SharePoint Server 2013  <br/> |SharePoint Online  <br/> |
||Гибридная среда SharePoint  <br/> |SharePoint Server 2016  <br/> |
|||Гибридная среда SharePoint  <br/> |
   
При выборе параметров в нижней части (достаточно) масштаба помните, что необходимо начать планирование обновления очень вскоре после миграции из SharePoint Server 2007 завершена. (окончание поддержки для SharePoint Server 2007 — 10 октября 2017. Следует иметь в виду, что эти даты могут быть изменены и проверьте [жизненный цикл продукта сайта](https://support.microsoft.com/en-us/lifecycle)).
  
## <a name="where-can-i-go-next"></a>Где можно перейти далее?

SharePoint Server может быть установлено локально на собственных серверах, или можно использовать SharePoint Online, которая является сетевая служба, входящий в состав Microsoft Office 365. Вы можете:
  
- Миграция в SharePoint Online
    
- Обновления SharePoint Server в локальной
    
- Выполнить оба указанных
    
- Реализация решения [гибридной среды SharePoint](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx) 
    
Следует помнить о скрытых расходы, связанные с обслуживание фермы серверов, начиная, обслуживание или миграция настроек и обновление оборудования, от которого зависит SharePoint Server. Необходимости в локальной ферме SharePoint Server — это результативным, если это необходимо; в противном случае при запуске фермы для устаревших серверов SharePoint, без толстые настройки можно воспользоваться преимуществом планируется переход к SharePoint Online.
  
> [!IMPORTANT]
> Существует другая возможность редко используемые контента в SharePoint 2007. Некоторые администраторы SharePoint следующим шагом нужно [Создать подписку на Office 365](https://go.microsoft.com/fwlink/?linkid=843152), настройте совершенно новый сайт SharePoint Online и без ошибок, cut вне SharePoint 2007, с удалением только самые важные документы на новые веб-сайты SharePoint Online. Нет может извлекаются данные из сайта SharePoint 2007 в архивы. Предоставление выполняемом на работу пользователей с данными SharePoint 2007 установки. Может быть creative способа решения этой проблемы. 
  
|**SharePoint Online (SPO)**|**SharePoint Server в локальной**|
|:-----|:-----|
|Высокая стоимость времени (план / выполнения и проверки)  <br/> |Высокая стоимость времени (план / выполнения и проверки)  <br/> |
|Снижение затрат в средств (нет покупки оборудования)  <br/> |Выше затрат в средств (оборудование + разработчики и "Администраторы")  <br/> |
|Одноразовый стоимость миграции  <br/> |Стоимость единовременного повторяющихся в будущем миграции  <br/> |
|Низкая совокупная стоимость владения / обслуживания  <br/> |Высокая совокупной стоимости владения и обслуживание  <br/> |
   
При миграции на Office 365 одноразовый move имеет весом стоимость авансовые, а вы организации данных и решить, какой вступило в облако и что следует оставить. Тем не менее будет с этого момента автоматического обновления, больше не требуется управление обновлениями аппаратного и программного обеспечения и повышения времени фермы будут использовать Microsoft соглашения об уровне обслуживания ([SLA](https://go.microsoft.com/fwlink/?linkid=843153)).
  
### <a name="migrate-to-sharepoint-online"></a>Миграция в SharePoint Online

Убедитесь в том, что SharePoint Online включает все функциональные возможности, описанные в разделе Описание связанных служб. Вот ссылки на все описания служб Office 365.
  
[Описание службы Office 365](https://go.microsoft.com/fwlink/?linkid=272060)
  
Нет возможности прямая миграция из SharePoint 2007 в SharePoint Online; Перейти к SharePoint Online будет выполняться вручную. При обновлении до SharePoint Server 2013 или SharePoint Server 2016 перемещения может потребоваться перенос с помощью API переноса SharePoint (данные в OneDrive для бизнеса, например).
  
|**Online Pro**|**Что такое Online**|
|:-----|:-----|
|Корпорация Майкрософт предоставляет SPO оборудование и все администрирования оборудования.  <br/> |Доступные функции могут отличаться между SharePoint Server в локальной и SPO.  <br/> |
|Глобальный администратор подписки и может назначение администраторов для сайтов SPO.  <br/> |Некоторые действия, доступные для администратора фермы в SharePoint Server в локальной не существует (или не нужны) включены в роль администратора SharePoint в Office 365.  <br/> |
|Microsoft область применения исправлений, исправления и обновления базового аппаратного и программного обеспечения.  <br/> |Поскольку нет доступа к базовым файловой системы в службе, некоторые настройки ограничены.  <br/> |
|Корпорация Майкрософт публикует [Соглашений об уровне обслуживания](https://go.microsoft.com/fwlink/?linkid=843153) и перемещает быстро завершать уровня службы.  <br/> |Резервное копирование, восстановление и другие варианты восстановления автоматического службы в SharePoint Online — резервные копии будут перезаписаны не используется.  <br/> |
|Тестирование безопасности и настройки производительности сервера выполняются на постоянной основе в службе Microsoft.  <br/> |Изменения в пользовательском интерфейсе и других SharePoint функции должны быть установлены службы и может потребоваться включаются или выключаются.  <br/> |
|Office 365 с использованием многих отраслевых стандартов: [Соответствие требованиям Office 365](https://go.microsoft.com/fwlink/?linkid=843165).  <br/> |[Она](https://go.microsoft.com/fwlink/?linkid=518597) обращайтесь к миграции ограничена.  <br/> Большая часть обновления будет выполняться вручную или с помощью API переноса SPO представлена в [SharePoint Online и материалов по миграции OneDrive](https://go.microsoft.com/fwlink/?linkid=843184).  <br/> |
|Сотрудники службы поддержки Майкрософт, ни сотрудников в центре данных не ограничен административного доступа к своей подписке.  <br/> |Может существовать дополнительные расходы, если инфраструктуры оборудование должно быть обновлены для поддержки новой версии SharePoint или дополнительной ферме не требуется для обновления.  <br/> |
|Партнеры по может быть полезна в разовое задание из перенос данных в SharePoint Online.  <br/> ||
|Через службу, что означает наличие на то, что может отказаться от функций, не true окончание поддержки Online продукты будут обновлены автоматически.  <br/> ||
   
Если вы решили создать новый сайт Office 365 и будет вручную перенести данные его, необходимые, вы откроете право параметры Office 365:
  
[Параметры планов Office 365](https://go.microsoft.com/fwlink/?linkid=843151)
  
### <a name="upgrade-sharepoint-server-on-premises"></a>Обновления SharePoint Server в локальной

С исторической точки зрения нет возможности пропустить версий в обновления SharePoint, по крайней мере, по состоянию на выпуск SharePoint Server 2016. Это означает, что обновления перейдите последовательно:
  
|||
|:-----|:-----|
||SharePoint 2007 | SharePoint Server 2010 | SharePoint Server 2013 | SharePoint Server 2016 |
   
Необходимо получить весь путь из SharePoint 2007 для SharePoint Server 2016 будет означать значительные инвестиции времени и включает расходы обновленных оборудования (Помните, что серверы SQL Server также должны быть обновлены), программное обеспечение и администрирования. Настройки потребуется обновить или недействительным в соответствии с требованиями надежности компонента.
  
> [!NOTE]
> Существует возможность обслуживания окончания срока поддержки фермы SharePoint 2007, для установки фермы SharePoint Server 2016 на новом оборудовании (то есть отдельных ферм запустите рядом друг с другом) и затем планирование и выполнение ручного переноса содержимого (для загрузки и повторно передачи контента, для пример). Необходимо учитывать некоторые проблемы перемещения вручную (такие как перемещение документов, заменив последнего изменения учетной записи с псевдонимом учетной записи, выполнив перемещения вручную), а также работ, которые необходимо выполнить заранее (например, повторного создания сайтов, дочерних сайтов, разрешения и списка структуры). Опять же это время необходимо рассмотреть какие данные, можно переместить в хранилище, или больше не требуется, действие, которое может уменьшить влияние миграции.
  
В любом случае очистите вашей среды перед обновлением. Убедиться в существующей ферме функционирует перед выполнением обновления и (проверить) до его ликвидации! 
  
Не забудьте просмотрите **поддерживаемых и неподдерживаемых путей обновления**: 
  
- 
  [SharePoint Server 2007](https://go.microsoft.com/fwlink/?linkid=843156)
    
- [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843156).
    
- [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843157)
    
При наличии **настроек**, важно иметь план обновления для каждого шага в пути миграции: 
  
- [SharePoint 2007](https://go.microsoft.com/fwlink/?linkid=843158)
    
- [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843160).
    
- [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843162)
    
|**Локальные Pro**|**Что такое локальные**|
|:-----|:-----|
|Разрешения на полный доступ все аспекты фермы SharePoint из серверного оборудования копирования.  <br/> |Все разрывов и исправления оплачиваются вашей компании (могли взаимодействовать платной технической поддержки Майкрософт Если продукт не в конце поддержка):  <br/> |
|Полный набор компонентов SharePoint Server в локальной с параметром для подключения локальной фермы в SharePoint Online подписку через гибридные.  <br/> |Обновления, исправления, исправления безопасности и все обслуживание SharePoint Server управляемых локальной.  <br/> |
|Полный доступ для настройки на более высокой версии.  <br/> |[Соответствие требованиям стандартов, поддерживаемых Office 365](https://go.microsoft.com/fwlink/?linkid=843165) должен быть настроен вручную в локальной.  <br/> |
|Тестирование безопасности и настройки производительности сервера, выполняемые на локально (используется в разделе элемент управления).  <br/> |Office 365 может доступность компонентов в SharePoint Online, не будет взаимодействовать с SharePoint Server в локальной  <br/> |
|Партнеры могут помочь с переносом данных до следующей версии SharePoint Server (и за ее пределами).  <br/> |На сайтах SharePoint Server не будет автоматически использовать сертификаты [SSL/TLS](https://go.microsoft.com/fwlink/?linkid=843167) , как видно в SharePoint Online.  <br/> |
|Разрешения на полный доступ соглашения о наименовании, резервного копирования и восстановления и другие параметры восстановления в SharePoint Server в локальной.  <br/> |SharePoint Server в локальной конфиденциальной жизненным циклом продукта.  <br/> |
   
### <a name="upgrade-resources"></a>Обновление ресурсы

Следует знать, что выполняются требования к оборудованию и программному обеспечению, а затем выполните поддерживаемых методов обновления.
  
- **Требования к оборудованию и программному обеспечению для**: 
    
    [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843204) | [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843204) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843206) | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843207)
    
- **Программные ограничения и лимиты для**: 
    
    [SharePoint Server 2007](https://go.microsoft.com/fwlink/?linkid=843245) | [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843247) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843248) | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843249)
    
- **Обзор процесса обновления для**: 
    
    [SharePoint Server 2007](https://go.microsoft.com/fwlink/?linkid=843250) | [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843251) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843252) | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843359)
    
### <a name="create-a-sharepoint-hybrid-solution-between-sharepoint-online-and-on-premises"></a>Создание гибридное решение SharePoint между SharePoint Online и локальной

Если вы ответили свой особый миграции где-нибудь между self-control, предлагаемых локальной и снижение стоимости владения, предоставляемых SharePoint Online, можно подключить SharePoint Server 2013 или 2016 ферм в SharePoint Online через гибридные устройства. [Сведения о гибридных решениях SharePoint](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx)
  
Если вы решили, что гибридные фермы серверов SharePoint выиграют бизнеса, ознакомьтесь с существующей типы гибридного и как настроить соединение между локальной фермы SharePoint и подписки Office 365.
  
Позволяет видеть, как это работает — путем создания [Office 365 dev/тестовой среды](https://go.microsoft.com/fwlink/?linkid=843152). После того как у вас есть пробную версию или приобрести подписки Office 365, вы будете работу по созданию семейств веб-сайтов, веб-сайтов и библиотек документов в SharePoint Online, к которому можно перенести данные (либо вручную, с помощью API-интерфейса миграции или — если нужно перенести Мои Контента сайта в OneDrive для бизнеса - в мастере гибридной).
  
> [!NOTE]
> Помните, что фермы SharePoint 2007 нужно обновить, локальная, SharePoint Server 2013 или SharePoint Server 2016 для использования параметра гибридного 
  
## <a name="related-topics"></a>Статьи по теме

[Устранение ошибок и возобновление обновления (Office SharePoint Server 2007)](https://go.microsoft.com/fwlink/?linkid=843192)
  
[Устранение неполадок при обновлении (SharePoint Server 2010)](https://go.microsoft.com/fwlink/?linkid=843194)
  
[Устранение неполадок при обновлении баз данных в SharePoint 2013](https://go.microsoft.com/fwlink/?linkid=843195)
  
[Поиск для партнеров Майкрософт при обновлении](https://go.microsoft.com/fwlink/?linkid=841249)
  
[Ресурсы, которые помогут вам обновление с Office 2007 серверов и клиентов](upgrade-from-office-2007-servers-and-products.md)
  
