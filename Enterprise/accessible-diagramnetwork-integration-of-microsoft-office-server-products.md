---
title: "Доступная схема — сетевая интеграция серверных продуктов Microsoft Office"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 89f564eb-95c3-4077-bb92-75bf71b51270
description: "Данная статья представляет собой текстовую версию схемы \"Сетевая интеграция серверных продуктов Microsoft Office\"."
ms.openlocfilehash: 2ced3ae648d07ae00c66b8ede8562df66826e4a9
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2017
---
# <a name="accessible-diagram---network-integration-of-microsoft-office-server-products"></a>Доступная схема — сетевая интеграция серверных продуктов Microsoft Office

**Сводка:** Эта статья является доступным текстовая версия схемы с именем сети интеграции из продуктов Microsoft Office Server.
  
На этом плакате приводятся общие иллюстрация сетевая среда, которая включает в себя Lync Server 2013, SharePoint 2013 и Exchange Server 2013. Демонстрация следующих сетевых элементов, которые являются общими для всех таких продуктов: внутренний и удаленного доступа, проверки подлинности, клиентского трафика и трафик через общедоступные устройства. 
  
## <a name="high-level-concepts-for-lync-exchange-sharepoint-server-and-office-web-apps"></a>Общие понятия для Lync, Exchange, SharePoint Server и Office Web Apps

### <a name="about-the-design"></a>Сведения о структуре

#### <a name="streamlined-network-design"></a>Упрощенная структура сети

Эта топология показана сети локальное развертывание SharePoint 2013, Exchange Server 2013 и Lync Server 2013. Также демонстрируется использование облачной службе Microsoft, Exchange Online Protection, которая обеспечивает защиту от нежелательной почты и вредоносных программ для входящего трафика Simple Mail Transfer Protocol (SMTP) из Интернета. 
  
Эта структура сети упрощена до такой степени, что в ней используется минимальный набор сетевых функций. В ней не учитываются дополнительные функции безопасности и инфраструктуры, которые могут потребоваться некоторым организациям.   
  
На этой схеме:  
  
- представлен пример топологии сети, иллюстрирующий прохождение входящего и исходящего трафика через маршрутизатор шлюза и балансировку нагрузки для трафика сеанса клиента (внешнего и внутреннего) к серверам SharePoint, Exchange и Lync соответствующего уровня;   
    
- показано использование необязательных серверов удаленного доступа, например стороннего VPN-шлюза или сервера DirectAccess, для обеспечения безопасной связи с разъездными или удаленными сотрудниками;  
    
- представлены подробные сведения о потоке трафика SharePoint, Exchange и Lync от клиента к серверам платформы всех уровней;  
    
- определены типы подключений для удаленного или внутреннего доступа на основе клиентов (например, для партнеров или сотрудников) и используемые методы проверки подлинности;  
    
- Устранение платформы SharePoint, Exchange и Lync с необходимые роли сервера, идентифицирующий переднего плана, приложения, базы данных и других уровнях. 
    
Архитектура, используемая здесь для SharePoint, Lync и Exchange, не является предпочитаемым способом реализации этих платформ. Она приведена исключительно в качестве примера, так как топологии зависят от уникальных требований к сети и соображений безопасности.  
  
#### <a name="gateway-router"></a>Маршрутизатор шлюза

В этой топологии маршрутизатор шлюза находится на краю сети и выполняет маршрутизацию всего входящего и исходящего трафика в интрасеть и из нее. Кроме того, могут использоваться другие компоненты, заполняющие разрыв между показанными маршрутизатором шлюза и подсистемой балансировки нагрузки, например несколько уровней брандмауэров. Эта топология — всего лишь один из способов развертывания вашей сети. В этой конфигурации шлюз настроен с использованием списков управления доступом, чтобы разрешать только определенный входящий и исходящий IP-трафик в интерфейсах маршрутизатора. Кроме того, можно применить списки управления доступом, средства расширенной проверки или функцию преобразования сетевых адресов к другим устройствам, например брандмауэрам, во всей вашей сети.  
  
#### <a name="load-balancer-and-reverse-proxy-devices"></a>Устройства подсистемы балансировки нагрузки и обратного прокси-сервера

Решения балансировки нагрузки оборудования или программного обеспечения можно использовать для перенаправления потока данных для сегментов, включая SharePoint интерфейсных веб-серверов и серверов клиентского доступа Exchange (классов). В некоторых случаях является оптимальным на использование подсистему балансировки нагрузки на основе оборудования уровня 7 сохраняемость требований к, как его можно лучше выполнять с помощью информации в запросе, такие как файлы cookie или заголовки. Тем не менее факторов, таких как затраты и увеличивает и рабочей нагрузки из такого решения может быть нежелательно для конкретных потребностей. Помните о следующих балансировки нагрузки между SharePoint, Exchange и Lync. 
  
- SharePoint — для SharePoint 2013 Включение сходства для интерфейсных веб-серверов не нужно. Как правило это будет использоваться для создания решения о сеансах и избежать нескольких запросов проверки подлинности клиентов на каждом интерфейсном веб-сервере. Новые службы распределенного кэша в SharePoint 2013 хранит и распределяет маркеры входа в систему на веб-серверах в ферме SharePoint. 
    
- Exchange - в Exchange 2013, роль сервера клиентского доступа позволяет использовать Балансировка нагрузки на уровне 4, распределения запросов на транспортном уровне. Это может существенно сократить использование балансировки нагрузки и рабочей нагрузки. 
    
- Lync - Балансировка нагрузки на доменных имен (DNS) рекомендуется для трафика Session Initiation Protocol (SIP) для пулов Lync. Аппаратная Балансировка (аппаратного балансировщика Нагрузки) нагрузки является обязательным для трафика Lync Web (HTTPS). 
    
### <a name="remote-access-options"></a>Средства удаленного доступа

Существует несколько способов публикации ресурсов интрасети в Интернете для партнеров или предоставления безопасного удаленного доступа для выездных или удаленных сотрудников. Это, например, обратные прокси-серверы, технология DirectAccess и сторонние VPN-шлюзы. Рассматриваемые далее решения для удаленного доступа предоставляют соответствующие возможности для серверов SharePoint, Lync и Exchange, а также для любого их сочетания в локальном развертывании. Тем не менее некоторые способы удаленного доступа могут не работать с определенными решениями.   
  
Обратный прокси-сервер — обратный прокси-сервер поддерживает шифрование трафика, например Secure Sockets Layer (SSL) и с ним, которые могут публиковать приложения интрасети и веб-ресурсы для прошедших проверку пользователей и партнеров в Интернете. Например, Microsoft Forefront Unified Access Gateway (UAG). Многие аппаратных балансировщиков нагрузки также поддерживает функции обратного прокси-сервера. Тем не менее будут по-прежнему действительный сценарии использования отдельных решения на основе потребности и требования, такие как изоляции трафика, разделение ответственности безопасности и оптимизации производительности. 
  
Преимущества и соображения, связанные с использованием обратных прокси-серверов.  
  
- Обратные прокси-серверы обеспечивают защищенный доступ с проверкой подлинности для партнеров или пользователей, использующих ресурсы интрасети. При этом между клиентом и обратным прокси-сервером используется SSL (TCP-порт 443).  
    
- Для Exchange преимущество использования обратного прокси-сервера, например Forefront UAG, состоит в возможности предварительной проверки подлинности перед получением доступа к серверу клиентского доступа Exchange. Чтобы войти во внутреннюю сеть, пользователи с удаленным доступом, использующие опубликованные приложения, например Outlook Web Access, могут проходить проверку подлинности с помощью основного метода, а также с помощью методов NTLM или Kerberos.  
    
- Для Exchange и SharePoint такие решения, как Forefront UAG, могут завершать SSL-подключения и уменьшать нагрузку на сервер ресурсов в интрасети. При этом они обеспечивают единую точку управления сертификатами.  
    
- Для Lync Web (HTTPS) трафик проходит через обратный прокси-сервер (TCP 443) связь с клиентами. Прокси-серверы обратного прокси-сервера HTTPS подключения к Lync веб-служб, сервер клиентского доступа Exchange и Office Web Apps. Lync Server 2013 не поддерживает UAG. 
    
DirectAccess - технология удаленного доступа, которая использует безопасности протокола IP (IPsec) для проверки подлинности и шифрования трафика между сервером и клиентом DirectAccess. DirectAccess предоставляет одновременный доступ к ресурсам Интернета и интрасети для перемещения и удаленных сотрудников без необходимости установки подключения. 
  
Ниже приведены соображения касательно DirectAccess, на которые необходимо обратить внимание.  
  
- Для обмена данными между клиентом и сервером DirectAccess используется защищенный трафик IPsec (протоколы 50 и 51, а также UDP 500).  
    
- DirectAccess для Windows Server 2012 и Windows 8 не требует развертывания инфраструктуры открытых ключей для проверки подлинности сервера и клиента.  
    
- Мы не рекомендуем с помощью DirectAccess с Lync Server 2013 из-за проблем задержка аудио- и видеоконференций, связанных с IPsec шифрования и расшифровки. 
    
    Шлюз VPN - типичного VPN шлюзы предоставляют подключения удаленного доступа, в которой клиентский компьютер удаленного доступа логически отображаться на интрасети через подключение к Туннелированные и инициированных пользователем. Можно использовать единую удаленного доступа в Windows Server 2012 или несколько решений сторонних производителей для обеспечения безопасный доступ к интрасети для мобильных или удаленных сотрудников. VPN не рекомендуется для Lync. Трафик Lync следует использовать пограничных серверов и разделение туннелирование. 
    
### <a name="domain-name-system-dns-considerations"></a>Соображения касательно DNS

Вам потребуется спланировать набор записей DNS, который позволит пользователям в Интернете и в интрасети сопоставлять DNS-имена с соответствующими IP-адресами.  
  
- Для партнеров, получающих доступ через Интернет, и выездных и удаленных сотрудников записи DNS, зарегистрированные с помощью DNS-серверов в Интернете, обеспечивают сопоставление с набором общедоступных IP-адресов, соответствующих маршрутизатору шлюза, пограничному серверу Lync, набору виртуальных IP-адресов в подсистеме балансировки нагрузки и DirectAccess или VPN-шлюзу.  
    
- Для пользователей, получающих доступ из интрасети, записи DNS, зарегистрированные с помощью DNS-серверов в интрасети, обеспечивают сопоставление с набором виртуальных IP-адресов в подсистеме балансировки нагрузки для доступа к ресурсам SharePoint, Lync и Exchange.  
    
- Клиенты DirectAccess используют DNS-серверы интрасети для имен, входящих в пространство имен DNS интрасети, и DNS-серверы в Интернете — для всех остальных имен. Чтобы упростить эксплуатацию DirectAccess, рассмотрим использование разделенной реализации DNS, в которой для имен в интрасети и в Интернете применяются различные пространства имен DNS. Например, можно использовать имя contoso.com для пространства имен в Интернете и имя corp.contoso.com для пространства имен в интрасети.  
    
- Exchange использует модель разделенной DNS, в которой сопоставленный IP-адрес узла будет различным для трафика из общедоступной сети и трафика в корпоративной сети. Как минимум, вам понадобятся записи DNS для URL-адресов Outlook Web Access, службы автообнаружения и ActiveSync для трафика от клиента и запись MX для входящей почты.  
    
- Если вы используете Exchange Online Protection, то запись MX будет указывать на эту службу, а не на вашу ферму Exchange.  
    
- При использовании Exchange вам потребуется доказательство права собственности на запись TXT в общедоступном DNS и код организации федерации для настройки федеративного общего доступа.  
    
- Можно настроить VPN-клиенты удаленного доступа таким образом, чтобы когда VPN-подключение удаленного доступа активно, они использовали только DNS-серверы в интрасети.  
    
### <a name="diagram-description"></a>Описание схемы

На этой схеме представлен пример топологии сети, иллюстрирующий прохождение входящего и исходящего трафика через маршрутизатор шлюза и балансировку нагрузки для трафика сеанса клиента (внешнего и внутреннего) к серверам SharePoint, Exchange и Lync соответствующего уровня. Описание этой схемы состоит из двух указанных ниже частей.  
  
- Описание компонентов, показанных на схеме  
    
- Описание того, как трафик проходит через различные компоненты к уровням серверов SharePoint, Exchange, Lync и Office Web Apps.  
    
#### <a name="description-of-components-shown-in-the-diagram"></a>Описание компонентов, показанных на схеме 

#### <a name="user-types"></a>Типы пользователей

Существуют четыре указанных ниже типа пользователей. Три из них располагаются за пределами сети и облачных служб, а четвертый — внутри них.  
  
- Компании-партнеры (бизнес-бизнес) — внешние пользователи  
    
- Индивидуальные партнеры (SharePoint) и анонимные пользователи (Lync) — внешние пользователи  
    
- Выездные и удаленные сотрудники — внешние пользователи  
    
- Внутренние сотрудники 
    
#### <a name="cloud-based-email-traffic"></a>Трафик облачной электронной почты

На схеме имеется облачный компонент для SMTP-трафика электронной почты. Это либо узлы электронной почты в Интернете, либо Exchange Online Protection.  
  
#### <a name="authentication-for-external-access"></a>Проверка подлинности для внешнего доступа

Существует определенный набор процедур проверки подлинности для Lync, SharePoint и Exchange для каждого типа пользователей. Они будут описаны более подробно далее в этом документе.  
  
#### <a name="gateway-router-with-acls"></a>Маршрутизатор шлюза со списками управления доступом

Маршрутизатор шлюза находится на границе сети и выполняет маршрутизацию всего входящего и исходящего трафика в интрасеть и из нее.  
  
#### <a name="remote-access-servers-for-lync-and-sharepoint"></a>Серверы удаленного доступа для Lync и SharePoint

Эта топология включает пограничный сервер Lync и VPN-шлюз SharePoint или сервер DirectAccess.  
  
#### <a name="load-balancer-and-reverse-proxy-device"></a>Устройство подсистемы балансировки нагрузки и обратного прокси-сервера

Вы можете использовать как аппаратные, так и программные решения для балансировки нагрузки, чтобы перенаправлять трафик в различные сегменты, включая веб-серверы переднего плана SharePoint и серверы клиентского доступа Exchange. В этой топологии показаны компоненты виртуальных IP-адресов Lync, SharePoint и Exchange в подсистеме балансировки нагрузки.  
  
#### <a name="servers"></a>Серверы

Существует четыре сервера: Lync, SharePoint, Exchange и сервера Office Web Apps. Каждый сервер может иметь три уровня: сервером переднего плана, клиентского доступа уровня, уровня приложений и уровня хранилища и базы данных.
  
#### <a name="front-end-client-access-tier"></a>Уровень переднего плана для клиентского доступа

Компоненты этого уровня имеются на всех четырех серверах.  
  
- Пул Lync (переднего плана). На схеме показаны две базы данных Lync.  
    
- Передний план и распределенный кэш SharePoint. На схеме показаны три базы данных SharePoint.   
    
- Сервер клиентского доступа Exchange. На схеме показаны две базы данных Exchange.  
    
- Сервер Office Web Apps. На схеме показаны две базы данных Office Web Apps.  
    
#### <a name="application-tier"></a>Уровень приложений

Компоненты этого уровня имеются только в сервере SharePoint.  
  
- Поиск (запросы, индексирование, администрирование). На схеме показаны три базы данных SharePoint.  
    
- Пакетная обработка. На схеме показаны три базы данных SharePoint.   
    
#### <a name="databasestorage-tier"></a>Уровень базы данных и хранилища

Компоненты этого уровня имеются на серверах Lync, SharePoint и Exchange.  
  
- База данных Lync (внутренняя). На схеме показаны три базы данных Lync.  
    
- База данных SharePoint. На схеме показаны три базы данных SharePoint.  
    
- Сервер почтовых ящиков Exchange. На схеме показаны два сервера почтовых ящиков Exchange.  
    
Дополнительные сведения о компонентах, установленных на каждой роли сервера SharePoint можно [Оптимизированные топологии для SharePoint 2013](https://aka.ms/Ma5cgk). 
  
#### <a name="description-of-how-traffic-moves-through-the-components-to-the-different-server-tiers"></a>Описание процесса перемещения трафика через компоненты на различные уровни серверов

В этом разделе описано, как запросы пользователей перемещаются в пределах топологии сети.   
  
#### <a name="authentication-and-routing-for-external-access"></a>Проверка подлинности и маршрутизация для внешнего доступа

Существуют три указанных ниже типа клиентов, располагающихся за пределами сети и облачных служб.  
  
- Компании-партнеры (бизнес-бизнес) — внешние пользователи  
    
- Индивидуальные партнеры (SharePoint) и анонимные пользователи (Lync) — внешние пользователи  
    
- Выездные и удаленные сотрудники — внешние пользователи  
    
Процессы проверки подлинности и маршрутизации для каждого типа внешнего пользователя описаны отдельно.  
  
#### <a name="partner-companies-business-to-business-httpspartnerwebcontosocom"></a>Компании-партнеры (бизнес-бизнес) (https://partnerweb.contoso.com)

- Lync: доверие федерации с другими организациями, Skype и возможность подключения к общедоступным службам обмена мгновенными сообщениями c AOL. Трафик федерации Lync проходит через маршрутизатор шлюза на пограничный сервер Lync, потом — на виртуальный IP-адрес Lync (подсистема балансировки нагрузки и обратный прокси-сервер), а затем — на сервер Lync.  
    
- SharePoint: надежный партнер — поставщик удостоверений с проверкой подлинности SAML. Трафик клиента SharePoint проходит через маршрутизатор шлюза на виртуальный IP-адрес SharePoint (подсистема балансировки нагрузки и обратный прокси-сервер), а затем — на сервер SharePoint.  
    
- Exchange: взаимная проверка подлинности TLS для почтового трафика, проверка подлинности SAML для федеративного общего доступа. Трафик клиента Exchange проходит через маршрутизатор шлюза на виртуальный IP-адрес Exchange (подсистема балансировки нагрузки и обратный прокси-сервер), а затем — на сервер Exchange.  
    
- Трафик SMTP проходит через маршрутизатор шлюза и виртуальный IP-адрес Exchange (подсистема балансировки нагрузки и обратный прокси-сервер) на сервер Exchange.  
    
#### <a name="individual-partners-sharepoint-and-anonymous-lync-httpspartnerwebcontosocom-and-httpsmeetcontosocom"></a>Индивидуальные партнеры (SharePoint) и анонимные пользователи (Lync). (https://partnerweb.contoso.com и https://meet.contoso.com.)

- Lync: анонимные пользователи могут только присоединяться к собраниям Lync, организованным сотрудниками. Трафик федерации Lync проходит через маршрутизатор шлюза на пограничный сервер Lync, потом — на виртуальный IP-адрес Lync (подсистема балансировки нагрузки и обратный прокси-сервер), а затем — на сервер Lync.   
    
- SharePoint: надежный партнер-поставщик удостоверений с проверкой подлинности SAML или проверкой подлинности на основе форм. Трафик клиента SharePoint проходит через маршрутизатор шлюза на виртуальный IP-адрес SharePoint (подсистема балансировки нагрузки и обратный прокси-сервер), а затем — на сервер SharePoint.  
    
- Exchange: не применяется. 
    
- Веб-трафик Lync проходит через маршрутизатор шлюза на пограничный сервер Lync, на виртуальный IP-адрес Lync (подсистема балансировки нагрузки и обратный прокси-сервер), потом — на аппаратную подсистему балансировки нагрузки, а затем — на сервер Lync.  
    
#### <a name="roaming-and-remote-employees"></a>Выездные и удаленные сотрудники

1. https://Intranet.contoso.com 
    
2. https://teams.contoso.com 
    
3. https://My.contoso.com
    
4. https://partnerweb.contoso.com 
    
5. https://Mail.contoso.com * 
    
6. https://Dial.contoso.com *
    
7. https://Meet.contoso.com *
    
* URL-адрес Exchange имеет следующие виртуальные каталоги: автообнаружения, ecp, веб-служб Exchange, Microsoft-Server-ActiveSync, автономной адресной книги, owa, PowerShell 
  
- Lync: проверка подлинности TLS-DSK или NTLM. Трафик клиента Lync проходит через маршрутизатор шлюза на пограничный сервер Lync, потом — на виртуальный IP-адрес Lync (подсистема балансировки нагрузки и обратный прокси-сервер), а затем — на сервер Lync.  
    
- SharePoint: доменные службы Active Directory, проверка подлинности на основе форм или проверка подлинности SAML. Трафик клиента SharePoint проходит через VPN-шлюз или сервер DirectAccess на виртуальный IP-адрес SharePoint (подсистема балансировка нагрузки и обратный прокси-сервер), а затем — на сервер SharePoint.  
    
- Exchange: обычная проверка подлинности через SSL (ActiveSync, автообнаружение), проверка подлинности на основе форм (Outlook Web Access). Трафик клиента Exchange проходит через маршрутизатор шлюза на виртуальный IP-адрес Exchange (подсистема балансировки нагрузки и обратный прокси-сервер), а затем — на сервер Exchange.  
    
- Трафик клиента Lync проходит через маршрутизатор шлюза на виртуальный IP-адрес Lync (подсистема балансировки нагрузки и обратный прокси-сервер), потом — на аппаратную подсистему балансировки нагрузки (которая необходима для обработки HTTPS-трафика), а затем — на сервер Lync.  
    
#### <a name="authentication-for-internal-access"></a>Проверка подлинности для внутреннего доступа

#### <a name="internal-employees"></a>Внутренние сотрудники

> https://Intranet.contoso.com 
    
> https://teams.contoso.com 
    
> https://My.contoso.com
    
> https://partnerweb.contoso.com
    
> https://Mail.contoso.com * 
    
> https://Dial.contoso.com 
    
> https://Meet.contoso.com
    
> https://Admin.contoso.com
    
- Lync: проверка подлинности Kerberos, TLS-DSK или NTLM. Трафик клиента Lync проходит на виртуальный IP-адрес Lync (подсистема балансировки нагрузки и обратный прокси-сервер), а затем — на сервер Lync.  
    
- SharePoint: доменные службы Active Directory, проверка подлинности на основе форм или проверка подлинности SAML. Трафик клиента SharePoint проходит на виртуальный IP-адрес SharePoint (подсистема балансировки нагрузки и обратный прокси-сервер), а затем — на сервер SharePoint.  
    
- Exchange: доменные службы Active Directory, проверка подлинности на основе форм. Трафик клиента Exchange проходит на виртуальный IP-адрес Exchange (подсистема балансировки нагрузки и обратный прокси-сервер), а затем — на сервер Exchange.  
    
- Трафик клиента Lync проходит на виртуальный IP-адрес Lync (подсистема балансировки нагрузки и обратный прокси-сервер), потом — на аппаратную подсистему балансировки нагрузки (которая необходима для обработки HTTPS-трафика), а затем — на сервер Lync.  
    
#### <a name="cloud-based-email-traffic"></a>Трафик облачной электронной почты

Компонент на основе облака для электронной почты на основе SMTP-трафика состоит из Интернет-почты узлов или Exchange Online Protection.
  
Эти компоненты перемещают почтовый трафик по сети с помощью SMTP. Трафик проходит через маршрутизатор шлюза на виртуальный IP-адрес Exchange (подсистема балансировки нагрузки и обратный прокси-сервер), а затем — на сервер Exchange.  
  
### <a name="network-traffic-legend"></a>Условные обозначения для сетевого трафика

В поле условных обозначений указаны типы трафика, представленные в графе такими цветными линиями:  
  
- Зеленый строки: Lync SIP трафика 
    
- Синяя: веб-трафик Lync.  
    
- Сиреневая: трафик клиента SharePoint.  
    
- Оранжевая: трафик клиента Exchange.  
    
- Серая: трафик почтового сервера Exchange между локальной средой Exchange и Exchange Online Protection.  
    
Кроме того, в поле условных обозначений описаны различные типы трафика и используемые ими порты.  
  
#### <a name="lync-sip-traffic-and-lync-web-traffic"></a>Трафик SIP для Lync и веб-трафик Lync

Для обмена данными с внешними пользователями пограничный сервер Lync использует указанные ниже порты.   
  
- Трафик служб передачи сигналов и обмена мгновенными сообщениями (SIP и SIMPLE): TCP-порт 443 (открыт для входящего трафика)  
    
- Трафик веб-конференций (PSOM): порт TCP 443 (открыт для входящего трафика)  
    
- Трафик аудио и видео (SRTP): порты TCP 443, UDP 3478 и TCP 50000–59999 (дополнительные). Они открыты для входящего и исходящего трафика  
    
Для обмена данными в пределах федерации пограничный сервер Lync использует указанные ниже порты.   
  
- Порты TCP 5061 (SIP), 5269 (XMPP), 443 и UDP 3478 (SRTP). Они открыты для входящего и исходящего трафика  
    
#### <a name="sharepoint-client-traffic"></a>Трафик клиента SharePoint.

SharePoint может использовать TCP-порт 443 (SSL) для шифрования данных, передаваемых между клиентом и подсистемой балансировки нагрузки. Чтобы можно было получать внешний доступ из Интернета, этот порт должен быть открыт для входящего и исходящего трафика на маршрутизаторе шлюза (или во внешнем брандмауэре).  
  
#### <a name="exchange-client-traffic-and-exchange-mail-server-traffic"></a>Трафик клиента Exchange и почтового сервера Exchange

Для communications server на сервере Exchange используется TCP-порт 25 (SMTP). Большинство клиентского трафика (OWA, ActiveSync, автообнаружение, мобильный Outlook) обрабатывается через порт 443 (HTTPS). Если у вас есть клиентов POP или IMAP, порты 110 (POP3), 995 (зашифрованные POP3), 143 (IMAP4), 993 (зашифрованные IMAP4) и 587 (SMTP) также используются для поддержки этих клиентов. 
  
#### <a name="more-on-lync-network-traffic"></a>Нужны дополнительные сведения о сетевом трафике Lync?

Узнайте, как Lync Server может помочь организации обмена мгновенными сообщениями, веб-конференций, общий доступ к приложениям и голосовой связи. Для получения дополнительных сведений см [Microsoft Lync Server 2013 протокол рабочих нагрузок (en)](https://aka.ms/G5jzjo). 
  
На плакате также имеется QR-код для доступа к этой информации.  
  
