---
title: План для Microsoft 365 Multi-Geo
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: ''
ms.collection:
- Strat_SP_gtc
- SPO_Content
localization_priority: Priority
description: Сведения о Microsoft 365 Multi-Geo, о принципе такой поддержки и о географических расположениях, доступных для хранения данных.
ms.openlocfilehash: 8f06c43b9a622e06959ab12fa0e055c8653ca61c
ms.sourcegitcommit: c6a2256f746f55d1cfb739649ffeee1f2f2152aa
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/07/2020
ms.locfileid: "45052462"
---
# <a name="plan-for-microsoft-365-multi-geo"></a>План для Microsoft 365 Multi-Geo

Настоящее руководство предназначено для администраторов транснациональных компаний (MNC), которые готовятся к использованию клиента Microsoft 365 в дополнительных географических расположениях и при этом должны соблюдать требования к месту расположения данных.

В конфигурации с поддержкой нескольких регионов клиент Microsoft 365 включает центральное расположение и одно или несколько вспомогательных расположений. Это один клиент, который охватывает несколько географических расположений. Управление сведениями о клиенте, в том числе географическими расположениями, выполняется в Azure Active Directory (Azure AD).

Ниже приведены некоторые ключевые термины, связанные с поддержкой нескольких регионов, которые помогут вам понять базовые концепции конфигурации.

-   **Клиент** — представление организации в Microsoft 365, которое имеет, как правило, один или несколько связанных с ним доменов (например, https://contoso.sharepoint.com). 

-   **Географические расположения** — регионы, доступные для размещения данных в клиенте Microsoft 365.

-   **Вспомогательные расположения** — дополнительные географические расположения, настроенные для размещения данных в клиенте Microsoft 365. Клиенты с поддержкой нескольких регионов охватывают более одного географического расположения (например, Северную Америку и Европу).

-   **Предпочтительное расположение данных (PDL)**  — географическое расположение, в котором хранятся данные OneDrive и Exchange отдельного пользователя. В качестве PDL администратор может указать любое из настроенных для клиента географических расположений. Обратите внимание, что в случае изменения PDL для пользователя, у которого уже есть сайт OneDrive, данные OneDrive не переместятся в новое географическое расположение автоматически. Дополнительные сведения см. в статье [Перемещение библиотеки OneDrive в другое географическое расположение](move-onedrive-between-geo-locations.md). При наличии почтового ящика Exchange он автоматически перемещается в новое предпочтительное расположение данных.

Чтобы включить поддержку нескольких регионов, выполните четыре основных шага:

1.  Совместно с группой специалистов, занимающихся учетными записями, добавьте план обслуживания _с поддержкой нескольких регионов в Microsoft 365_.

2.  Выберите необходимые периферийные расположения и добавьте их для клиента.

3.  Задайте в качестве нужного периферийного расположения PDL пользователя. Новый сайт OneDrive или почтовый ящик Exchange для пользователя будет подготовлен к работе с учетом PDL.

4.  При необходимости перенесите существующие сайты OneDrive пользователя из центрального расположения в предпочтительное расположение данных. (Почтовые ящики Exchange переносятся автоматически при настройке PDL пользователя.)

Все упомянутые шаги подробно описаны в статье [Настройка Microsoft 365 Multi-Geo](multi-geo-tenant-configuration.md).

> [!IMPORTANT]
> Обратите внимание, что Microsoft 365 Multi-Geo не предназначен для повышения производительности. Он предназначена для соблюдения требований к месту расположения данных. Сведения о повышении производительности для Microsoft 365 см. в статье [Планирование сети и настройка производительности для Microsoft 365](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848). Вы также можете связаться с группой поддержки.

Вы можете настроить любое из следующих расположений как периферийное расположение для размещения сайтов OneDrive и SharePoint, а также почтовых ящиков Exchange. Планируя поддержку нескольких регионов, составьте список расположений, которые нужно добавить в клиент Microsoft 365. Рекомендуется начать с одного или двух периферийных расположений и постепенно добавлять новые по мере необходимости.

[!INCLUDE [Microsoft 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

When you configure multi-geo, consider taking the opportunity to consolidate your on-premises infrastructure while migrating to Microsoft 365. For example, if you have on-premises farms in Singapore and Malaysia, then you can consolidate them to the APC satellite location, provided data residency requirements allow you to do so.

## <a name="best-practices"></a>Рекомендации

Рекомендуется создать тестового пользователя в Microsoft 365 для выполнения первоначального тестирования. Далее приведены некоторые шаги, касающиеся тестирования и проверки с вовлечением этого пользователя. Выполнив их, вы сможете начать подключение пользователей к Microsoft 365 Multi-Geo.

Завершив тестирование с вовлечением тестового пользователя, выберите пилотную группу (например, группу ИТ-специалистов), которая первой воспользуется OneDrive и Exchange в новом географическом расположении. В эту группу добавьте пользователей, у которых еще нет OneDrive. Рекомендуется вначале добавлять не более пяти человек, а затем постепенно расширять группу методом пакетного развертывания.

Each user should have a *preferred data location* (PDL) set so that Microsoft 365 can determine in which geo location to provision their OneDrive. The user's preferred data location must match one of your chosen satellite locations or your central location. While the PDL field is not mandatory, we recommend that a PDL be set for all users. Workloads of a user without a PDL will be provisioned in the central location.

Create a list of your users, and include their user principal name (UPN) and the location code for the appropriate preferred data location. Include your test user and your initial pilot group to start with. You'll need this list for the configuration procedures.

Если выполняется синхронизация пользователей из локальной системы Active Directory в Azure Active Directory, нужно установить предпочтительное расположение данных в качестве атрибута Active Directory и синхронизировать его с помощью Azure Active Directory Connect. Напрямую настроить PDL для синхронизируемых пользователей с помощью Azure AD PowerShell невозможно. Шаги по настройке PDL в Active Directory и синхронизации рассматриваются в статье [Синхронизация Azure Active Directory Connect: настройка предпочтительного расположения данных для ресурсов Microsoft 365](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).

The administration of a multi-geo tenant can differ from a non-multi-geo tenant, as many of the SharePoint and OneDrive settings and services are multi-geo aware. We recommend that you review [Administering a multi-geo environment](administering-a-multi-geo-environment.md) before you proceed with your configuration.

Прочтите статью [Взаимодействие с пользователем в среде с поддержкой нескольких регионов](multi-geo-user-experience.md).

Сведения о работе с Teams в клиентах Microsoft 365 Multi-Geo см. в статье [Взаимодействие с Teams в клиентах Microsoft 365 OneDrive и SharePoint Online с поддержкой нескольких регионов](https://docs.microsoft.com/microsoftteams/teams-experience-o365odb-spo-multi-geo).

Чтобы начать настройку Microsoft 365 Multi-Geo, ознакомьтесь со статьей [Настройка Microsoft 365 Multi-Geo](multi-geo-tenant-configuration.md).

После настройки не забудьте [перенести библиотеки OneDrive пользователей](move-onedrive-between-geo-locations.md), если это необходимо для работы пользователей в предпочтительных расположениях данных.
