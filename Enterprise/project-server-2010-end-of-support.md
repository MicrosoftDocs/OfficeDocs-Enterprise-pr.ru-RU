---
title: План конечной поддержки Project Server 2010
ms.author: efrene
author: efrene
manager: pamg
ms.date: 06/03/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: IT_ProjectAdmin
search.appverid:
- MET150
- ZPJ120
- PJU120
- PJW120
description: Прекращение поддержки для Project Server 2010 завершается 13 октября 2020 г. Используйте эту статью в качестве руководства по обновлению до Project Online или более новой версии Project Server в локальной среде.
ms.openlocfilehash: 86ab1534058d49094327c326d8367a08c14d725b
ms.sourcegitcommit: c763b0f28e1ce498aef5d5deb3b6324288da85ea
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/21/2019
ms.locfileid: "35128706"
---
# <a name="project-server-2010-end-of-support-roadmap"></a>План поддержки Project Server 2010.

Project Server 2010 дойдет до конца поддержки **13 октября 2020 г**. Если в настоящее время используется Project Server 2010, обратите внимание на то, что следующие связанные продукты имеют следующие даты:
  
|**Product**|**Дата окончания поддержки**|
|:-----|:-----|
|Project Portfolio Server 2010  <br/> |13 октября 2020 г.  <br/> |
|Project 2010 Стандартный  <br/> |13 октября 2020 г.  <br/> |
|Project 2010 профессиональный  <br/> |13 октября 2020 г.  <br/> |
   
Дополнительные сведения о серверах Office 2010, достигнутых в конце поддержки, можно найти [в статье обновление с серверов и клиентских продуктов office 2010](https://docs.microsoft.com/office365/enterprise/plan-upgrade-previous-versions-office).
  
## <a name="what-does-end-of-support-mean"></a>Что означает окончание поддержки?

Project Server, как и почти все продукты Майкрософт, имеет жизненный цикл поддержки, в котором мы предоставляем новые функции, исправления ошибок и обновления для системы безопасности. Этот жизненный цикл обычно продолжается в течение 10 лет с даты первоначального выпуска продукта, а окончание этого жизненного цикла называется окончанием поддержки продукта. Когда Project Server 2010 достиг конца поддержки 13 октября 2020, корпорация Майкрософт больше не будет предоставлять:
  
- Техническая поддержка проблем, которые могут возникнуть.
    
- Исправление ошибок для обнаруженных проблем, которые могут повлиять на стабильность и удобство использования сервера.
    
- Исправления для системы безопасности уязвимостей, которые могут привести к уязвимости сервера при нарушении безопасности.
    
- Обновления часового пояса.
    
Установка Project Server 2010 продолжит работу после этой даты. Однако из-за перечисленных выше изменений настоятельно рекомендуется выполнить миграцию из Project Server 2010 как можно скорее.
  
## <a name="what-are-my-options"></a>Что такое параметры?

Если вы используете Project Server 2010, необходимо ознакомиться с параметрами миграции, которые перечислены ниже.
  
- Миграция в Project Online
    
- Переход на более новую локальную версию Project Server (желательно Project Server 2019).
    
|**Зачем нужна миграция в Project Online?**|**Зачем переходить на Project Server 2019?**|
|:-----|:-----|
| У меня есть мобильные или удаленные пользователи.  <br/>  Затраты на миграцию локальных серверов значительно важнее (оборудование, программное обеспечение, часы и усилия для реализации и т. д.).  <br/>  После миграции затраты на поддержание среды очень важны (например, автоматическое обновление, гарантированное время работы и т. д.).  <br/> | Бизнес-правила ограничивают меня рабочими моими предприятиями в облаке.  <br/>  Мне нужно управлять обновлениями в моей среде.  <br/> |
   
> [!NOTE]
> Для получения дополнительных сведений о возможностях перехода с серверов Office 2010, ознакомьтесь со статьей [ресурсы, которые помогут вам выполнить обновление серверов и клиентов office 2010](https://docs.microsoft.com/office365/enterprise/upgrade-from-office-2010-servers-and-products). Обратите внимание, что Project Server не поддерживает гибридную конфигурацию, так как Project Server и Project Online не могут совместно использовать один пул ресурсов. 
  
## <a name="important-considerations-you-need-to-make-when-planning-to-migrate-from-project-server-2010"></a>Важные замечания, которые необходимо принять во время планирования миграции из Project Server 2010

При планировании миграции из Project Server 2010 необходимо учитывать следующие рекомендации.
  
- **Получение помощи от поставщика решений Майкрософт** — обновление с Project Server 2010 может быть сложной задачей и требует значительных усилий по подготовке и планированию. Это может быть особенно сложным, если вы не использовались для настройки и первоначально настроили Project Server 2010. К счастью, у вас есть поставщики решений Майкрософт, которые могут сделать это, если вы планируете переход на Project Server 2019 или Project Online. Вы можете найти поставщика решений Майкрософт, который поможет вам выполнить миграцию в [центре поставщиков решений Майкрософт](https://go.microsoft.com/fwlink/p/?linkid=841249). 
    
- **Запланируйте настройки** , имейте в виду, что многие настройки, работающие в среде project Server 2010, могут не работать при переходе на project Server 2019 или Project Online. В архитектуре Project Server существуют существенные различия между версиями, а также операционные системы, серверы баз данных и клиентские веб-браузеры, которые поддерживают работу с более новой версией. Составьте план, чтобы проверить или перестроить настройки по мере необходимости в новой среде. При планировании обновления также будет полезно проверить, действительно ли требуется определенная настройка при переходе вперед. [Создайте план для текущих настроек во время обновления до SharePoint 2013]( https://docs.microsoft.com/SharePoint/upgrade-and-update/create-a-plan-for-current-customizations-during-upgrade-to-sharepoint-2013) содержит общие сведения об оценке и планировании текущих настроек при обновлении. 
    
- При планировании, выполнении и тестировании обновления **время и терпение** занимают много времени и сил, особенно при обновлении до Project Server 2019. Например, при переносе из Project Server 2010 в Project Server 2019 необходимо выполнить миграцию из Project Server 2010 в Project Server 2013, а затем проверить данные, а затем выполнить те же действия при переходе к каждой последующей версии (в Project Сервер 2016 и затем в Project Server 2019). Вы можете узнать у поставщика решений Майкрософт, что нужно сравнить предполагаемые затраты с оценками того, сколько времени потребуется для их выполнения, а также в каких затратах. 
    
## <a name="migrate-to-project-online"></a>Миграция в Project Online

Если вы решили выполнить миграцию из Project Server 2010 в Project Online, можно выполнить следующие действия, чтобы вручную перенести данные плана проекта:
  
1. Сохраните планы проекта из Project Server 2010. Формат MPP.
    
2. Используя Project профессиональный 2016, Project профессиональный 2019 или клиент Project Online для настольных ПК, откройте каждый MPP-файл, а затем сохраните и опубликуйте его в Project Online.
    
Вы можете вручную создать конфигурацию PWA в Project Online (например, создать все необходимые настраиваемые поля или корпоративные календари). Кроме того, вы можете помочь поставщикам решений Майкрософт.
  
Основные ресурсы:
  
|**Ресурс**|**Описание**|
|:-----|:-----|
|[Приступая к работе с Project Online](https://support.office.com/article/e3e5f64f-ada5-4f9d-a578-130b2d4e5f11) <br/> |Настройка и использование Project Online.  <br/> |
|[Описание службы Project Online](https://go.microsoft.com/fwlink/p/?linkid=829088) <br/> |Сведения о различных доступных планах Project Online.  <br/> |
   
## <a name="migrate-to-a-newer-on-premises-version-of-project-server"></a>Переход на новую локальную версию Project Server

Несмотря на то, что вы уверены, что вы можете добиться наилучшего качества и удобства работы пользователей, переполнив их в Project Online, мы также понимаем, что в некоторых организациях необходимо хранить данные проекта в локальной среде. Если вы решили хранить данные проекта локально, вы можете перенести среду Project Server 2010 в Project Server 2013, Project Server 2016 или Project Server 2019.
  
Рекомендуется выполнить миграцию в Project Server 2019, если вы не можете выполнить миграцию в Project Online. Project Server 2019 включает в себя большинство основных функций и улучшений, включенных в предыдущие выпуски Project Server, и наиболее полно соответствует интерфейсу, доступному в Project Online (хотя некоторые функции доступны только в Project Online).
  
После завершения каждой миграции необходимо проверить данные, чтобы убедиться, что они успешно перенесены.
  
> [!NOTE]
> Если вы планируете переход на Project Server 2013 только в том случае, если вы ограничены локальным решением, то важно отметить, что осталось только еще несколько лет поддержки. Дата окончания поддержки Project Server 2013 с пакетом обновления 2 (SP2) — 10/13/2023. Для получения дополнительных сведений о конце дат поддержки обратитесь к разделу [Политика жизненного цикла продуктов Майкрософт](https://go.microsoft.com/fwlink/p/?linkid=842066). 
  
### <a name="how-do-i-migrate-to-project-server-2019"></a>Как перейти к Project Server 2019?

Различия в архитектуре Project Server 2010 и Project Server 2019 запрещают прямой путь миграции. Это означает, что после обновления до Project Server 2019 вам потребуется перенести данные Project Server 2010 в следующую последующую версию Project Server.
  
Чтобы обновить Project Server 2010 до Project Server 2019, выполните следующие действия:
  
1. Переход на Project Server 2013.
    
2. Миграция из Project обслуживает 2013 в Project Server 2016.
    
3. Миграция из Project Server 2016 в Project Server 2019.
    
После завершения каждой миграции необходимо проверить данные, чтобы убедиться, что они успешно перенесены.
  
    
### <a name="step-1-migrate-to-project-server-2013"></a>Шаг 1: миграция на Project Server 2013

Первым этапом переноса данных Project Server 2010 в Project Server 2019 является предварительная миграция в Project Server 2013. 
  
Полное представление о том, что необходимо сделать для обновления Project Server 2010 до Project Server 2013, приведено в статье [Upgrade to Project server 2013](https://go.microsoft.com/fwlink/p/?linkid=841822). 
  
Основные ресурсы:
  
|||
|:-----|:-----|
|[Обзор этапов обновления до Project Server 2013](https://go.microsoft.com/fwlink/p/?linkid=841822) <br/> |Получите высокоуровневое представление о том, что нужно сделать для обновления с Project Server 2010 до Project Server 2013.  <br/> |
|[Планирование обновления до Project Server 2013](https://go.microsoft.com/fwlink/p/?linkid=841823) <br/> |Изучите рекомендации по планированию, которые необходимо выполнить при обновлении Project Server 2010 до Project Server 2013, включая требования к системе.  <br/> |
   
[Что нового в Project Server 2013 Upgrade](https://go.microsoft.com/fwlink/p/?linkid=841824) сообщает о важных изменениях для обновления этой версии, что наиболее заметно: 
  
- Обновление на месте до Project Server 2013 отсутствует. Метод с присоединением базы данных — единственный поддерживаемый метод обновления с Project Server 2010 до Project Server 2013.
    
- Процесс обновления не только преобразует данные Project Server 2010 в формат Project Server 2013, но также объединяет четыре базы данных Project Server 2010 в одну базу данных Project Web App.
    
- SharePoint Server 2013 и Project Server 2013 изменились на проверку подлинности на основе утверждений из предыдущей версии. При использовании классической проверки подлинности необходимо принять во внимание рекомендации по обновлению. Дополнительные сведения см. в статье [Migrate from classic-mode to claims-based authentication in SharePoint 2013]( https://docs.microsoft.com/sharepoint/upgrade-and-update/migrate-from-classic-mode-to-claims-based-authentication-in-sharepoint-2013).
    
Основные ресурсы:
  
- [Общие сведения о процессе обновления до Project Server 2013](https://go.microsoft.com/fwlink/p/?linkid=841274)
    
- [Обновление баз данных и семейств сайтов Project Web App (Project Server 2013)](https://go.microsoft.com/fwlink/p/?linkid=841272)
    
- [Схема процесса обновления Microsoft Project Server](https://go.microsoft.com/fwlink/p/?linkid=841270)
    
- [Отличная консолидация баз данных, Project Server 2010 – 2013 миграция на 8 простых действий](https://go.microsoft.com/fwlink/p/?linkid=841271)
    
### <a name="step-2-migrate-to-project-server-2016"></a>Шаг 2: миграция на Project Server 2016

После перехода на Project Server 2013 и проверки того, что данные успешно перенесены, следующим шагом является перенос данных в Project Server 2016.
  
Полное представление о том, что необходимо сделать для обновления Project Server 2013 до Project Server 2016, приведено в статье [Upgrade to Project server 2016](https://docs.microsoft.com/en-us/Project/upgrade-to-project-server-2016).
  
Основные ресурсы:
  
|||
|:-----|:-----|
|[Обзор процесса обновления до Project Server 2016](https://docs.microsoft.com/Project/overview-of-the-project-server-2016-upgrade-process) <br/> |Получите высокоуровневое представление о том, что нужно сделать для обновления с Project Server 2013 до Project Server 2016.  <br/> |
|[Планирование обновления до Project Server 2016](https://docs.microsoft.com/Project/plan-for-upgrade-to-project-server-2016) <br/> |Изучите рекомендации по планированию, которые необходимо выполнить при обновлении Project Server 2013 до Project Server 2016.  <br/> |
   
Что нужно [знать о Project Server 2016 Upgrade](https://docs.microsoft.com/project/plan-for-upgrade-to-project-server-2016#thingknow) содержит некоторые важные изменения для обновления до этой версии, в том числе: 
  
- При создании среды Project Server 2016, в которую будут перенесены данные Project Server 2013, обратите внимание на то, что установочные файлы Project Server 2016 включены в SharePoint Server 2016. Дополнительные сведения см. в статье [deploy Project Server 2016](https://go.microsoft.com/fwlink/p/?linkid=841829).
    
- Планы ресурсов являются устаревшими в Project Server 2016. Планы ресурсов Project Server 2013 будут перенесены в задействование ресурсов в Project Server 2016 и Project Online. Для получения дополнительных сведений см. [Обзор: задействование ресурсов](https://support.office.com/article/73eefb5a-81fe-42bf-980e-9532b1bdc870) . 
    
### <a name="step-3-migrate-to-project-server-2019"></a>Шаг 3: миграция на Project Server 2019

После перехода на Project Server 2016 и проверки того, что данные успешно перенесены, следующим шагом является перенос данных в Project Server 2019.
  
Полное представление о том, что необходимо сделать для обновления Project Server 2016 до Project Server 2019, приведено в статье [Upgrade to Project server 2019](https://docs.microsoft.com/en-us/Project/upgrade-to-project-server-2016).
  
Основные ресурсы:
  
|||
|:-----|:-----|
|[Обзор процесса обновления Project Server 2019](https://docs.microsoft.com/project/overview-of-the-project-server-2019-upgrade-process) <br/> |Получите высокоуровневое представление о том, что нужно сделать для обновления с Project Server 2013 до Project Server 2016.  <br/> |
|[Планирование обновления до Project Server 2019](https://docs.microsoft.com/project/plan-for-upgrade-to-project-server-2019) <br/> |Изучите рекомендации по планированию, которые необходимо выполнить при обновлении Project Server 2016 до Project Server 2019.  <br/> |
   
Что нужно [знать о Project Server 2019 Upgrade](https://go.microsoft.com/fwlink/p/?linkid=841827) содержит некоторые важные изменения для обновления до этой версии, в том числе: 
  
- В процессе обновления данные из базы данных Project Server 2016 будут перенесены в базу данных контента SharePoint Server 2019.  Project Server 2019 больше не будет создавать собственную базу данных Project Server в ферме SharePoint Server.

- После обновления следует учитывать несколько изменений в Project Web App.  Описание этих возможностей приведено в статье [новые возможности Project Server 2019](https://docs.microsoft.com/en-us/project/what-s-new-for-it-pros-in-project-server-2019#PWAChanges).

  
Другие ресурсы:
  
- [Описания служб Project Online](https://go.microsoft.com/fwlink/p/?linkid=841280): сведения о функциях управления портфелем, включенных в project Server 2016 и Project Online Premium.
    
- [Руководство по миграции Microsoft Office Project Portfolio Server 2010](https://go.microsoft.com/fwlink/p/?linkid=841279)
    
## <a name="related-topics"></a>Статьи по теме

[Обновление с SharePoint 2010](upgrade-from-sharepoint-2010.md)
  
[Обновление серверов и клиентов Office 2010](upgrade-from-office-2010-servers-and-products.md)
  

