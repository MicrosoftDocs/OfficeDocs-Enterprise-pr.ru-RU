---
title: Подписки, лицензии, учетные записи и клиенты для облачных предложений корпорации Майкрософт
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 06/25/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Ent_Architecture
ms.assetid: c720cffc-f9b5-4f43-9100-422f86a1027c
description: Сводка. Общие сведения о связи между организациями, подписками, лицензиями, учетными записями пользователей и клиентами в облачных предложениях корпорации Майкрософт.
ms.openlocfilehash: 52857196f53a44196c96f60bd70564f5e3221b80
ms.sourcegitcommit: 0f7607b5e88b78ae250900ce7ce1b019cd245aa1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/26/2020
ms.locfileid: "44906292"
---
# <a name="subscriptions-licenses-accounts-and-tenants-for-microsofts-cloud-offerings"></a>Подписки, лицензии, учетные записи и клиенты для облачных предложений корпорации Майкрософт

Для облачных решений Майкрософт предусмотрена иерархия организаций, подписок, лицензий и учетных записей пользователей. Это обеспечивает согласованное использование удостоверений и выставление счетов.
  
- Microsoft 365 и Microsoft Office 365
- Microsoft Azure
- Microsoft Dynamics 365

## <a name="elements-of-the-hierarchy"></a>Элементы иерархии

Ниже перечислены элементы иерархии.
  
### <a name="organization"></a>Организация

An organization represents a business entity that is using Microsoft cloud offerings, typically identified by one or more public Domain Name System (DNS) domain names, such as contoso.com. The organization is a container for subscriptions.
  
### <a name="subscriptions"></a>Подписки

Подписка — это соглашение с корпорацией Майкрософт на использование одной или нескольких облачных платформ или служб Майкрософт, за которые взимается плата (по лицензиям отдельных пользователей или по использованию облачных ресурсов). 

- Корпорация Майкрософт (Microsoft 365 и Dynamics 365) — это облачные решения Майкрософт (Microsoft и Dynamics), которые оплачиваются за лицензии на пользователя. 
- В облачных предложениях корпорации Майкрософт (Azure) на основе PaaS (платформа как услуга) и IaaS (инфраструктура как услуга) оплата взимается за использование облачных ресурсов.
 
You can also use a trial subscription, but the subscription expires after a specific amount of time or consumption charges. You can convert a trial subscription to a paid subscription.
  
У организации может быть несколько подписок на облачные предложения корпорации Майкрософт. На рисунке 1 показана одна организация с несколькими подписками на Microsoft 365, подпиской Dynamics 365 и несколькими подписками Azure.

**Рис. 1. Пример использования нескольких подписок для организации**

![Пример организации с несколькими подписками на облачные предложения корпорации Майкрософт.](media/Subscriptions/Subscriptions-Fig1.png)
  
### <a name="licenses"></a>Лицензии

В случае облачных предложений корпорации Майкрософт на основе SaaS лицензия позволяет определенному пользователю пользоваться услугами облачной службы. В рамках подписки ежемесячно взимается фиксированная плата. Администраторы назначают лицензии отдельным учетным записям пользователей в подписке. В примере на рисунке 2 Корпорация Contoso имеет подписку Microsoft 365, в которой есть лицензии на 100, которые позволяют до 100 отдельных учетных записей пользователей использовать функции и службы Microsoft 365.
  
**Рис. 2. Лицензии в рамках подписок на основе SaaS для организации**

![Пример нескольких лицензий в подписках на облачные предложения корпорации Майкрософт на основе SaaS.](media/Subscriptions/Subscriptions-Fig2.png)
  
В случае облачных служб на основе Azure PaaS стоимость лицензий на программное обеспечение включается в цену службы.
  
For Azure IaaS-based virtual machines, additional licenses to use the software or application installed on a virtual machine image might be required. Some virtual machine images have licensed versions of software installed and the cost is included in the per-minute rate for the server. Examples are the virtual machine images for SQL Server 2014 and SQL Server 2016. 
  
Some virtual machine images have trial versions of applications installed and need additional software application licenses for use beyond the trial period. For example, the SharePoint Server 2016 Trial virtual machine image includes a trial version of SharePoint Server 2016 pre-installed. To continue using SharePoint Server 2016 after the trial expiration date, you must purchase a SharePoint Server 2016 license and client licenses from Microsoft. These charges are separate from the Azure subscription and the per-minute rate to run the virtual machine still applies.
  
### <a name="user-accounts"></a>Учетные записи пользователей

Учетные записи для всех облачных предложений корпорации Майкрософт хранятся в клиенте Azure Active Directory (Azure AD), содержащем учетные записи и группы пользователей. Клиент Azure AD можно синхронизировать с имеющимися учетными записями доменных служб Active Directory (AD DS) с помощью Azure AD Connect, серверной службы Windows. Это называется синхронизацией службы каталогов.
  
На рис. 3 показан пример нескольких подписок организации, использующих общий клиент Azure AD с учетными записями организации.
  
**Рис. 3. Несколько подписок организации, использующих один клиент Azure AD**

![Пример организации с несколькими подписками, использующими один и тот же клиент Azure AD.](media/Subscriptions/Subscriptions-Fig3.png)
  
### <a name="tenants"></a>Клиенты

В случае облачных предложений на основе SaaS клиент — это регион, в котором располагаются серверы, предоставляющие облачные службы. Например, Корпорация Contoso выбрала Европейский регион для размещения клиентов Microsoft 365, EMS и Dynamics 365 для сотрудников 15 000 в штаб-квартирах Париж.
  
Azure PaaS services and virtual machine-based workloads hosted in Azure IaaS can have tenancy in any Azure datacenter across the world. You specify the Azure datacenter, known as the location, when you create the Azure PaaS app or service or element of an IaaS workload.
  
Клиент Azure AD — это определенный экземпляр Azure AD, содержащий учетные записи и группы. Платные или пробные подписки Microsoft 365 или Dynamics 365 включают бесплатный клиент Azure AD. Этот клиент Azure AD не включает службы Azure и не предоставляется с пробной или платной подпиской Azure.
  
### <a name="summary-of-the-hierarchy"></a>Сводка по иерархии

Краткая сводка:
  
- У организации может быть несколько подписок
    
  - В одной подписке может быть несколько лицензий
    
  - Лицензии можно назначать отдельным учетным записям
    
  - Учетные записи хранятся в клиенте Azure AD
    
Ниже приведен пример связи между организациями, подписками, лицензиями и учетными записями пользователей.
  
- Организация определяется по имени общедоступного домена.
    
  - Подписка на Microsoft 365 E3 с пользовательскими лицензиями.
    
    Подписка на Microsoft 365 с пользовательским лицензиями.
    
    Подписка на Dynamics 365 с лицензиями "на пользователя".
    
    Несколько подписок на Azure.
    
  - Учетные записи пользователей организации на общем клиенте Azure AD.
    
Для нескольких подписок на облачные решения Майкрософт может использоваться один клиент Azure AD, выступающий в качестве поставщика удостоверений. Благодаря центральному клиенту Azure AD, содержащему синхронизированные учетные записи из локальной службы AD DS, возможно предоставление удостоверений как услуги (IDaaS) для организации. 
  
**Рис. 4. Синхронизированные локальные учетные записи и IDaaS для организации**

![Идентификация как служба (IDaaS) для организации.](media/Subscriptions/Subscriptions-Fig4.png)
  
Figure 4 shows how a common Azure AD tenant is used by Microsoft's SaaS cloud offerings, Azure PaaS apps, and virtual machines in Azure IaaS that use Azure AD Domain Services. Azure AD Connect synchronizes the on-premises AD DS forest with the Azure AD tenant.
  
## <a name="combining-subscriptions-for-multiple-microsoft-cloud-offerings"></a>Объединение подписок для нескольких облачных предложений корпорации Майкрософт

В приведенной ниже таблице показано, как объединить несколько облачных предложений корпорации Майкрософт на основе имеющейся подписки на облачное предложение одного типа (подписи в первом столбце) и добавленной подписки на другое решение (поперек столбцов).
  
||**Microsoft 365**|**Azure**|**Dynamics 365**|
|:-----|:-----|:-----|:-----|:-----|
|**Microsoft 365** <br/> |NA  <br/> |Добавьте подписку Azure для организации с помощью портала Azure.  <br/> |Добавьте подписку на Dynamics 365 для организации в Центре администрирования Microsoft 365.  <br/> |
|**Azure** <br/> |Вы добавляете в организацию подписку на Microsoft 365.  <br/> |Н/Д  <br/> |Добавьте подписку Dynamics 365 для организации.  <br/> |
|**Dynamics 365** <br/> |Вы добавляете в организацию подписку на Microsoft 365.  <br/> |Добавьте подписку Azure для организации с помощью портала Azure.  <br/> |Н/Д  <br/> |
   
Вы можете с легкостью добавить подписки на службы Майкрософт на основе SaaS для организации, используя Центр администрирования.
  
1. Войдите в Центр администрирования Microsoft 365 ([https://admin.microsoft.com](https://admin.microsoft.com)) с помощью учетной записи глобального администратора.
    
2. В левой части главной страницы **Центра администрирования** выберите **Выставление счетов** > **Приобретение служб**.
    
3. На странице **Приобретение служб** купите новые подписки.
    
Центр администрирования назначает организацию и клиент Azure AD для подписки на Microsoft 365 новым подпискам на облачные решения на основе SaaS.
  
Чтобы добавить подписку Azure с той же организацией и клиентом Azure AD, что и ваша подписка на Microsoft 365:
  
1. Войдите на портал Azure ( [https://portal.azure.com](https://portal.azure.com) ) с помощью учетной записи глобального администратора Microsoft 365.
    
2. В области навигации слева выберите **Подписки** > **Добавить**.
    
3. На странице **Добавление подписки** выберите предложение, а затем укажите платежную информацию и примите условия лицензионного соглашения.
    
Если вы приобрели подписки Azure и Microsoft 365 отдельно и хотите получить доступ к клиенту Microsoft 365 Azure AD из вашей подписки на Azure, ознакомьтесь с инструкциями в статье [Добавление существующей подписки Azure в клиент Azure Active Directory](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-how-subscriptions-associated-directory).
 
## <a name="see-also"></a>См. также

[Ресурсы, посвященные ИТ-архитектуре Microsoft Cloud](microsoft-cloud-it-architecture-resources.md)
  
[Архитектурные модели для SharePoint, Exchange, Skype для бизнеса и Lync](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[Гибридные решения](hybrid-solutions.md)

## <a name="next-step"></a>Следующий шаг

[Оценка сетевого подключения Microsoft 365](assessing-network-connectivity.md)
  
