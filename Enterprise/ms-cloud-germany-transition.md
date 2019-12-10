---
title: Миграция с Microsoft Cloud для Германии (Microsoft Cloud Deutschland) в службы Office 365 в новых регионах центров обработки данных в Германии
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/09/2019
audience: ITPro
ms.topic: hub-page
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: 706d5449-45e5-4b0c-a012-ab60501899ad
description: 'Сводка: понимание миграции с Microsoft Cloud для Германии (Microsoft Cloud Deutschland) в службы Office 365 в новых регионах центров обработки данных в Германии'
ms.openlocfilehash: 5b339ab36ad613078bbfcd705f42ceb3703585e9
ms.sourcegitcommit: b5992f367ccae97a8ea538738fe36d3d703cd6e7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/10/2019
ms.locfileid: "39920285"
---
# <a name="migration-from-microsoft-cloud-germany-microsoft-cloud-deutschland-to-office-365-services-in-the-new-german-datacenter-regions"></a>Миграция с Microsoft Cloud для Германии (Microsoft Cloud Deutschland) в службы Office 365 в новых регионах центров обработки данных в Германии


>[!Note]
>Эта статья относится только к разрешенным клиентам Microsoft Cloud для Германии/Deutschland.
>

## <a name="cloud-service-offerings-in-germany"></a>Предложения облачных служб в Германии

В августе 2018 г. мы объявили о своем намерении поставить полноценную платформу Microsoft Cloud (Azure, Office 365, Dynamics 365 и Power Platform) из новых облачных регионов в Германии, чтобы лучше обеспечить цифровые преобразования наших клиентов. В августе 2019 г. мы объявили о том, что находимся в процессе открытия новых облачных регионов в Германии. Мы объявили о доступности Azure в августе, а Office 365 стал доступен в декабре.  В первом квартале 2020 предполагается, что Dynamics 365 и Power Platform также станут доступными.  

Новые регионы предназначены для удовлетворения растущих потребностей немецких клиентов благодаря большей гибкости, новейшим интеллектуальным облачным сервисам, а также полному подключению к нашей глобальной облачной сети и хранению данных клиентов в пределах Германии.

## <a name="moving-to-the-new-german-regions"></a>Переход на новые регионы в Германии

Существующие клиенты Microsoft Cloud для Германии (Microsoft Cloud Deutschland) теперь могут начать миграцию своих клиентов Office 365, Dynamics 365 Customer Engagement и Power Platform BI.  Первым шагом является [согласие на миграцию под руководством корпорации Майкрософт](https://aka.ms/office365germanymoveoptin) в наши новые регионы центров обработки данных в Германии.

Для организаций, давших согласие на программу под руководством корпорации Майкрософт, предполагается, что миграция будет выполняться в 2020 году. В результате миграции основные данные клиента и подписки перемещаются в новые регионы в Германии. 

Обратите внимание на то, что после завершения миграции подписки цены будут снижаться в соответствии с ценами на общедоступное облако. Прямые клиенты увидят, что новая подписка будет продлена на новый срок в 12 месяцев, а дата завершения миграции будет вашей новой ежегодной датой продления. Указанные ниже службы будут перенесены в рамках программы под руководством корпорации Майкрософт:

- Azure Active Directory
- Exchange Online
- Exchange Online Protection
- SharePoint Online
- OneDrive для бизнеса
- Skype для бизнеса Online

  В рамках перехода с Microsoft Cloud для Германии на регион в Германии существующие пользователи Skype для бизнеса Online перейдут в Microsoft Teams. Дополнительные сведения см. в статье [https://aka.ms/SkypeToTeams-Home](https://aka.ms/SkypeToTeams-Home).

- Группы Office 365
- Dynamics 365 / Power Platform

  Предварительные требования и влияние миграции на эти службы описаны в статье [Dynamics 365 Customer engagement](https://aka.ms/D365ceOptIn).

## <a name="how-to-prepare-for-migration-to-office-365-services-in-the-new-german-datacenter-regions"></a>Как подготовиться к миграции на службы Office 365 в новых регионах центров обработки данных в Германии

Сначала необходимо сообщить корпорации Майкрософт о своем решении, чтобы у нас было ваше согласие на миграцию вашей подписки и данных из Microsoft Cloud для Германии / Deutschland в службы Office 365 в новых регионах центров обработки данных в Германии.  Инструкции приведены в статье [Процедура согласия](ms-cloud-germany-migration-opt-in.md).

- Всем мигрирующим пользователям необходимо проверить подключение к [URL-адресам и IP-адресам Office 365](urls-and-ip-address-ranges.md), которые включают в себя новые регионы центров обработки данных в Германии.
- Ознакомьтесь с описанием службы платформы Office 365, чтобы понять, какие функции и службы станут доступны вашей организации после завершения миграции в регион в Германии. 
- Во время миграции будут переходить платные подписки.

Миграции клиента выполняются в виде серверных операций обслуживания, для которых требуется минимальное взаимодействие с клиентом.  В процессе миграции в Центре сообщений будет отображаться информация о любых дополнительные задачах, выполняемых клиентом, и об общем состоянии миграции.  Примером задач могут быть управляемые клиентом обновления DNS или реконфигурация гибридной настройки для гибридных клиентов Exchange.

## <a name="customer-experience-during-the-migration-to-office-365-services-in-the-new-german-datacenter-regions"></a>Взаимодействие с клиентами в процессе миграции на службы Office 365 в новых регионах центров обработки данных в Германии

Миграции клиента выполняются в виде серверных операций обслуживания с минимальным взаимодействием с конечными клиентами или действиями, требуемыми администраторами.  Однако для каждой рабочей нагрузки следует учитывать ряд моментов.  

### <a name="azure-active-directory"></a>Azure Active Directory

Подписки на Office/Dynamics (на основе Microsoft Cloud для Германии) переносятся в регион в Германии с перемещением Azure Active Directory (Azure AD). Затем организация обновляется в соответствии с новыми глобальными подписками на службы. В ходе короткого процесса переноса подписки изменения в подписке будут заблокированы.

### <a name="exchange-online"></a>Exchange Online

Клиенты Exchange Online Hybrid должны повторно запустить мастер настройки гибридной конфигурации, чтобы обновить локальную конфигурацию Microsoft Cloud для Германии до перехода, и повторно выполнить мастер настройки гибридной конфигурации (HCW) после очистки в соответствии с глобальной службой. Для клиентов, использующих личные домены, могут потребоваться дополнительные обновления DNS.

Почтовые ящики переносятся в виде серверного процесса; пользователи в вашей организации могут находиться в Microsoft Cloud для Германии или в регионе в Германии во время перехода и быть частью одной организации Exchange (GAL)

### <a name="exchange-online-protection"></a>Exchange Online Protection

Серверные функции Exchange Online Protection скопированы в новый регион в Германии

### <a name="sharepoint-online"></a>SharePoint Online

После завершения миграции SharePoint Online в регион в Германии будут перестроены только индексы данных. Функции, зависящие от индексов поиска, могут быть затронуты в процессе переиндексации.

Существующие URL-адреса sharepoint.de сохраняются для перешедших организаций.

### <a name="onedrive-for-business"></a>OneDrive для бизнеса

После завершения миграции OneDrive для бизнеса в регион в Германии будут перестроены только индексы данных. Функции, зависящие от индексов поиска, могут быть затронуты в процессе переиндексации.

### <a name="skype-for-business-online"></a>Skype для бизнеса Online

Существующие клиенты Skype для бизнеса Online будут переходить в Microsoft Teams. Дополнительные сведения см. в статье [https://aka.ms/SkypeToTeams-Home](https://aka.ms/SkypeToTeams-Home).


## <a name="key-differences-between-microsoft-cloud-germany-microsoft-cloud-deutschland-and-office-365-services-in-the-new-german-datacenter-regions"></a>Основные различия между Microsoft Cloud для Германии (Microsoft Cloud Deutschland) и служб Office 365 в новых регионах центров обработки данных в Германии


|| Microsoft Cloud для Германии (Microsoft Cloud Deutschland) | Службы Office 365 в новых регионах центров обработки данных в Германии |
|:-------|:-----|:-----|
| Службы Microsoft 365, доступные для подписки только на один клиент Office 365 | 15 служб (см. раздел REF) | 29 служб (см. раздел REF) |
| Новые функции | Новые функции недоступны. | Новые функции будут доступны в рамках глобальных служб Office 365. |
| Доверенное лицо для данных | Да | Нет |
| Взаимодействие между клиентами и глобальными клиентами Office 365 | Нет | Да |
| Размещение данных клиента | Данные клиента будут храниться только в центрах обработки данных в Германии. | Корпорация Майкрософт будет хранить указанные ниже данные клиентов только в Германии: содержимое почтовых ящиков Exchange Online (тело сообщения электронной почты, элементы календаря и содержимое вложений в сообщения электронной почты), содержимое сайта SharePoint Online и файлы, хранящиеся на этом сайте, файлы, отправленные в OneDrive для бизнеса. |
| Применимые условия использования | [Условия предоставления услуг в Интернете](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=46) с [дополнением](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=64) | [Условия использования веб-служб](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=46) |
||||

## <a name="frequently-asked-questions"></a>Вопросы и ответы

### <a name="is-migration-required"></a>Требуется ли миграция?

Корпорация Майкрософт предлагает миграцию клиентов Office 365 из Microsoft Cloud для Германии в службы Office 365 в новых регионах центров обработки данных в Германии без дополнительной оплаты.  Хотя мы настоятельно рекомендуем вам зарегистрироваться для миграции в новые регионы центров обработки данных в Германии, однако мы продолжим предоставлять необходимые обновления безопасности для региона Microsoft Cloud для Германии.  

Службы Office 365 в новых регионах центров обработки данных в Германии имеют дополнительные преимущества:

- Предложение конкурентоспособной рыночной цены для [Azure](https://azure.microsoft.com/pricing/calculator/), [Office 365](https://www.microsoft.com/microsoft-365/business/compare-more-office-365-for-business-plans), [Dynamics 365 Customer Engagement](https://dynamics.microsoft.com/pricing/) и [Power BI](https://powerbi.microsoft.com/pricing/). 
- Они подключены к глобальной сети Майкрософт, предлагают сотни периферийных сетевых сайтов, расположений пиринга и точек выхода, чтобы обеспечить надежную работу пользователей в любой точке мира. 
- Помогают вам соответствовать местным требованиям о размещении данных в пределах Германии. 
- Вы получаете полнофункциональное глобальное облачное решение, в том числе новейшие версии наших служб и новых возможностей, включая Microsoft Teams и Office 365. Сравните продукты по регионам для [Azure](https://azure.microsoft.com/global-infrastructure/services/?products=all&regions=germany-non-regional,germany-central,germany-north,germany-northeast,germany-west-central), [Office 365](https://products.office.com/ru-RU/where-is-your-data-located)и [Dynamics 365](https://docs.microsoft.com/dynamics365/get-started/availability).
- Предлагают полный набор функций, обеспечение безопасности корпоративного уровня и широкие возможности, которые помогают клиентам удовлетворить нормативные требования. 
- Доступны через существующие контракты веб-служб.

#### <a name="what-is-the-service-availability"></a>Какова доступность у службы?

Службы Microsoft 365, доступные для подписки только с одним клиентом Office 365

Для Microsoft Cloud для Германии (Microsoft Cloud Deutschland) мы предлагаем следующие службы. Мы не добавляем новые службы в это облачное предложение.

1. Exchange Online
2. Защищенное хранилище для пользователей (Exchange Online)
3. Группы (современные группы)
4. Профиль Delve
5. Exchange Online Protection
6. Расширенная защита от угроз (ATP)
7. Advanced eDiscovery
8. Расширенное управление данными
9. SharePoint Online
10. Защищенное хранилище для пользователей (SharePoint Online)
11. OneDrive для бизнеса
12. Skype для бизнеса
13. Word Online, Excel Online, PowerPoint, OneNote, Visio Online
14. Office 365 профессиональный плюс
15. Outlook Mobile

Для служб Office 365 в новых регионах центров обработки данных в Германии мы предлагаем следующие службы. Мы постоянно добавляем новые службы в это облачное предложение.

1. Exchange Online
2. Защищенное хранилище для пользователей (Exchange Online)
3. Группы (современные группы)
4. Профиль Delve
5. MyAnalytics
6. Рабочая аналитика
7. Exchange Online Protection
8. Расширенная защита от угроз (ATP)
9. Advanced eDiscovery
10. Расширенное управление безопасностью
11. Управление правами на доступ к данным
12. Расширенное управление данными
13. SharePoint Online
14. Защищенное хранилище для пользователей (SharePoint Online)
15. OneDrive для бизнеса
16. Microsoft Stream
17. Skype для бизнеса (переход на Microsoft Teams)
18. Облачная УАТС
19. Конференц-связь через ТСОП
20. Вызовы ТСОП
21. Microsoft Teams
22. Отчеты администратора / Отчеты об использовании
23. Word Online, Excel Online, PowerPoint, OneNote, Visio Online
24. 24. Планировщик
25. Sway
26. Office 365 профессиональный плюс
27. Outlook Mobile
28. EMS E3 (Azure Active Directory Premium P1 + Intune + Служба управления правами)
29. Yammer Online

### <a name="when-will-migration-happen"></a>Когда произойдет миграция?

- Azure 

 Вы можете начать [миграцию](https://docs.microsoft.com/azure/germany/germany-migration-main) своих ресурсов Azure в другой регион уже сегодня. При наличии Azure с Office 365, Dynamics 365 и/или Power BI выполните указанные ниже действия.

- Office 365

  [Согласие](https://aka.ms/office365germanymoveoptin) на миграцию под руководством корпорации Майкрософт сегодня. Когда вы будете готовы начать миграцию, то в центре администрирования Microsoft 365 мы проинформируем вас с помощью [Центра сообщений](https://docs.microsoft.com/office365/admin/manage/message-center?view=o365-worldwide).

- Dynamics 365 и Power BI

  Присоединяйтесь к миграции под руководством корпорации Майкрософт для [Dynamics 365](https://aka.ms/D365ceOptIn) и [Power BI сегодня](https://aka.ms/pbioptin). Когда вы будете готовы начать миграцию, то в центре администрирования Microsoft 365 мы проинформируем вас с помощью [Центра сообщений](https://docs.microsoft.com/office365/admin/manage/message-center?view=o365-worldwide).

### <a name="will-the-price-change-for-the-office-services-that-i-use"></a>Будут ли изменяться цены для используемых мною служб Office?

Да, цены в глобальном облаке Майкрософт (в том числе в новых регионах центров обработки данных), как правило, меньше.

### <a name="how-do-i-get-help-from-microsoft-to-migrate-to-a-new-region-or-answer-support-questions"></a>Как получить помощь от корпорации Майкрософт, чтобы перейти на новый регион или ответить на вопросы о поддержке?

При наличии вопросов вы можете связаться с нами, выполнив указанные ниже действия, или через нашего партнера.

- В Azure можно отправлять [новые запросы в службу поддержки](https://portal.microsoftazure.de/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/newsupportrequest) на портале Azure.
- В Office 365 вы можете отправлять вопросы с помощью опции "Нужна помощь?". ссылка [Центра администрирования Microsoft 365](https://portal.office.de/).
- Для клиентов Dynamics 365 Customer Engagement и Power BI, у которых также есть Office 365, вы можете отправлять вопросы с помощью опции "Нужна помощь?". ссылка [Центра администрирования Microsoft 365](https://portal.office.de/). Варианты поддержки клиентов Dynamics 365 Customer Engagement доступны [здесь](https://docs.microsoft.com/dynamics365/get-started/support/). Варианты поддержки клиентов Power BI доступны [здесь](https://powerbi.microsoft.com/support/).

## <a name="more-information"></a>Дополнительные сведения

- Помощь по миграции Microsoft Cloud Deutschland в [https://aka.ms/germanymigrateassist](https://aka.ms/germanymigrateassist)
- Как принять участие в миграции на [https://aka.ms/office365germanymoveoptin](https://aka.ms/office365germanymoveoptin)
- Миграция Dynamics 365 на [https://aka.ms/D365ceOptIn](https://aka.ms/D365ceOptIn)
- Миграция Power BI на [https://aka.ms/pbioptin](https://aka.ms/pbioptin)
- URL-адреса и диапазоны IP-адресов для Office 365 на [https://aka.ms/o365endpoints](https://aka.ms/o365endpoints)
- Мастер гибридной конфигурации Office 365 на [https://aka.ms/HybridWizard](https://aka.ms/HybridWizard)
