---
title: Подписки, лицензии, учетные записи и клиенты для облачных предложений корпорации Майкрософт
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/08/2019
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
ms.openlocfilehash: ad4307b2725fa37f6b28540b92895fc78f097c6c
ms.sourcegitcommit: c112869b3ecc0f574b7054ee1edc8c57132f8237
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2020
ms.locfileid: "44735967"
---
# <a name="subscriptions-licenses-accounts-and-tenants-for-microsofts-cloud-offerings"></a>Подписки, лицензии, учетные записи и клиенты для облачных предложений корпорации Майкрософт

 **Сводка.** Общие сведения о связи между организациями, подписками, лицензиями, учетными записями пользователей и клиентами в облачных предложениях корпорации Майкрософт.
  
Для облачных решений Майкрософт предусмотрена иерархия организаций, подписок, лицензий и учетных записей пользователей. Это обеспечивает согласованное использование удостоверений и выставление счетов.
  
- Microsoft Office 365
- Microsoft Azure
- Microsoft Intune и Enterprise Mobility + Security (EMS)
- Microsoft Dynamics 365

[Microsoft 365](https://docs.microsoft.com/microsoft-365/) объединяет Office 365, EMS и Windows 10 Корпоративная в одну подписку и набор интегрированных служб.

## <a name="elements-of-the-hierarchy"></a>Элементы иерархии

Ниже перечислены элементы иерархии.
  
### <a name="organization"></a>Организация

An organization represents a business entity that is using Microsoft cloud offerings, typically identified by one or more public Domain Name System (DNS) domain names, such as contoso.com. The organization is a container for subscriptions.
  
### <a name="subscriptions"></a>Подписки

Подписка — это соглашение с корпорацией Майкрософт на использование одной или нескольких облачных платформ или служб Майкрософт, за которые взимается плата (по лицензиям отдельных пользователей или по использованию облачных ресурсов). 

- В облачных предложениях корпорации Майкрософт на основе SaaS (Office 365, Intune/EMS и Dynamics 365) оплата взимается за лицензии пользователей. 
- В облачных предложениях корпорации Майкрософт (Azure) на основе PaaS (платформа как услуга) и IaaS (инфраструктура как услуга) оплата взимается за использование облачных ресурсов.
 
You can also use a trial subscription, but the subscription expires after a specific amount of time or consumption charges. You can convert a trial subscription to a paid subscription.
  
У организации может быть несколько подписок на облачные предложения корпорации Майкрософт. На рисунке 1 показана одна организация с несколькими подписками на Office 365 и Azure, подпиской на Intune и подпиской на Dynamics 365.

**Рис. 1. Пример использования нескольких подписок для организации**

![Пример организации с несколькими подписками на облачные предложения корпорации Майкрософт.](media/Subscriptions/Subscriptions-Fig1.png)

  
### <a name="licenses"></a>Лицензии

В случае облачных предложений корпорации Майкрософт на основе SaaS лицензия позволяет определенному пользователю пользоваться услугами облачной службы. В рамках подписки ежемесячно взимается фиксированная плата. Администраторы назначают лицензии отдельным учетным записям пользователей в подписке. Например, на рис. 2 у корпорации Contoso есть подписка на Office 365 корпоративный E5 со 100 лицензиями, что позволяет 100 отдельным пользователям использовать функции и службы Office 365 корпоративный E5.
  
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

For SaaS cloud offerings, the tenant is the regional location that houses the servers providing cloud services. For example, the Contoso Corporation chose the European region to host its Office 365, EMS, and Dynamics 365 tenants for the 15,000 workers in their Paris headquarters.
  
Azure PaaS services and virtual machine-based workloads hosted in Azure IaaS can have tenancy in any Azure datacenter across the world. You specify the Azure datacenter, known as the location, when you create the Azure PaaS app or service or element of an IaaS workload.
  
An Azure AD tenant is a specific instance of Azure AD containing accounts and groups. Paid or trial subscriptions of Office 365, Dynamics 365, or Intune/EMS include a free Azure AD tenant. This Azure AD tenant does not include other Azure services and is not the same as an Azure trial or paid subscription.
  
### <a name="summary-of-the-hierarchy"></a>Сводка по иерархии

Краткая сводка:
  
- У организации может быть несколько подписок
    
  - В одной подписке может быть несколько лицензий
    
  - Лицензии можно назначать отдельным учетным записям
    
  - Учетные записи хранятся в клиенте Azure AD
    
Ниже приведен пример связи между организациями, подписками, лицензиями и учетными записями пользователей.
  
- Организация определяется по имени общедоступного домена.
    
  - Подписка Office 365 корпоративный E3 с лицензиями "на пользователя".
    
    Подписка Office 365 корпоративный E5 с лицензиями "на пользователя".
    
    Подписка на EMS с лицензиями "на пользователя".
    
    Подписка на Dynamics 365 с лицензиями "на пользователя".
    
    Несколько подписок на Azure.
    
  - Учетные записи пользователей организации на общем клиенте Azure AD.
    
Для нескольких подписок на облачные решения Майкрософт может использоваться один клиент Azure AD, выступающий в качестве поставщика удостоверений. Благодаря центральному клиенту Azure AD, содержащему синхронизированные учетные записи из локальной службы AD DS, возможно предоставление удостоверений как услуги (IDaaS) для организации. 
  
**Рис. 4. Синхронизированные локальные учетные записи и IDaaS для организации**

![Идентификация как служба (IDaaS) для организации.](media/Subscriptions/Subscriptions-Fig4.png)
  
Figure 4 shows how a common Azure AD tenant is used by Microsoft's SaaS cloud offerings, Azure PaaS apps, and virtual machines in Azure IaaS that use Azure AD Domain Services. Azure AD Connect synchronizes the on-premises AD DS forest with the Azure AD tenant.
  
## <a name="combining-subscriptions-for-multiple-microsoft-cloud-offerings"></a>Объединение подписок для нескольких облачных предложений корпорации Майкрософт

В приведенной ниже таблице показано, как объединить несколько облачных предложений корпорации Майкрософт на основе имеющейся подписки на облачное предложение одного типа (подписи в первом столбце) и добавленной подписки на другое решение (поперек столбцов).
  
||**Office 365**|**Azure**|**Intune/EMS**|**Dynamics 365**|
|:-----|:-----|:-----|:-----|:-----|
|**Office 365** <br/> |Н/Д  <br/> |Добавьте подписку Azure для организации с помощью портала Azure.  <br/> |Добавьте подписку Intune/EMS для организации в Центре администрирования Microsoft 365.  <br/> |Добавьте подписку на Dynamics 365 для организации в Центре администрирования Microsoft 365.  <br/> |
|**Azure** <br/> |Добавьте подписку на Office 365 для организации.  <br/> |Недоступно  <br/> |Добавьте подписку Intune/EMS для организации.  <br/> |Добавьте подписку Dynamics 365 для организации.  <br/> |
|**Intune/EMS** <br/> |Добавьте подписку на Office 365 для организации.  <br/> |Добавьте подписку Azure для организации с помощью портала Azure.  <br/> |Недоступно  <br/> |Добавьте подписку Dynamics 365 для организации.  <br/> |
|**Dynamics 365** <br/> |Добавьте подписку на Office 365 для организации.  <br/> |Добавьте подписку Azure для организации с помощью портала Azure.  <br/> |Добавьте подписку Intune/EMS для организации.  <br/> |Н/Д  <br/> |
   
Вы можете с легкостью добавить подписки на службы Майкрософт на основе SaaS для организации, используя Центр администрирования.
  
1. Войдите в Центр администрирования Microsoft 365 ([https://admin.microsoft.com](https://admin.microsoft.com)) с помощью учетной записи глобального администратора.
    
2. В левой части главной страницы **Центра администрирования** выберите **Выставление счетов** > **Приобретение служб**.
    
3. На странице **Приобретение служб** купите новые подписки.
    
Центр администрирования назначает организации и клиенту Azure AD, у которых есть подписка на Office 365, новые подписки на облачные решения на основе SaaS.
  
Чтобы добавить подписку Azure с теми же организацией и клиентом Azure AD, что и в подписке на Office 365:
  
1. Войдите на портал Azure ([https://portal.azure.com](https://portal.azure.com)), используя учетную запись глобального администратора Office 365.
    
2. В области навигации слева выберите **Подписки** > **Добавить**.
    
3. На странице **Добавление подписки** выберите предложение, а затем укажите платежную информацию и примите условия лицензионного соглашения.
    
Если вы приобрели подписки на Azure и Office 365 отдельно и хотите получить доступ к клиенту Azure AD в Office 365, воспользуйтесь инструкциями в статье [Добавление существующей подписки на Azure с клиентом Azure Active Directory](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-how-subscriptions-associated-directory).
 
## <a name="see-also"></a>См. также

[Ресурсы, посвященные ИТ-архитектуре Microsoft Cloud](microsoft-cloud-it-architecture-resources.md)
  
[Архитектурные модели для SharePoint, Exchange, Skype для бизнеса и Lync](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[Гибридные решения](hybrid-solutions.md)

## <a name="next-step"></a>Следующий шаг

[Доступ к сетевому подключению Office 365](assessing-network-connectivity.md)
  
