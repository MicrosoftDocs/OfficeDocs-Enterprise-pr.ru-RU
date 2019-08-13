---
title: Тестирование Office 365 с помощью руководств по лаборатории тестирования
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 08/12/2019
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
description: Сводка. Воспользуйтесь этими руководствами по лаборатории тестирования, чтобы настроить среды для демонстрации, экспериментальной установки, разработки и тестирования продуктов Office 365.
ms.openlocfilehash: 32675683846789f1e7be0e398e5b140d25d7ba80
ms.sourcegitcommit: d58cdc7b2296df12f7a05d14ba05ab224ffb3e0c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/13/2019
ms.locfileid: "36302741"
---
# <a name="test-office-365-with-test-lab-guides-tlgs"></a>Тестирование Office 365 с помощью руководств по лаборатории тестирования

 **Сводка.** Используйте эту статью, чтобы настроить среды для демонстрации, экспериментальной установки, разработки и тестирования продуктов Office 365.
  
Руководства по лаборатории тестирования содержат краткие сведения о продуктах Майкрософт. Они отлично подходят для ситуаций, в которых нужно оценить технологию или конфигурацию, прежде чем решать, подходит ли она вам, или прежде чем начинать проектировать, планировать и развертывать ее для пользователей. Такой интерактивный подход помогает ознакомиться с требованиями для развертывания нового продукта или решения и позволяет лучше спланировать его размещение в производственной среде.
  
Кроме того, эти руководства помогают создавать типичные среды для разработки и тестирования приложений.
  
![Руководства по лаборатории тестирования в Microsoft Cloud](media/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
## <a name="office-365-devtest-environment"></a>Среда разработки и тестирования Office 365

Следующие статьи помогут вам создать среду разработки и тестирования Office 365:
  
- [Базовая конфигурация среды разработки и тестирования](base-configuration-dev-test-environment.md)
    
    Создание упрощенной интрасети, выполняющейся в службах инфраструктуры Microsoft Azure. Это действие не является обязательным для создания имитации конфигурации предприятия.
    
- [Среда разработки и тестирования Office 365](office-365-dev-test-environment.md)
    
    Подписка на бесплатную пробную версию Office 365 корпоративный Е5, которую можно оформить со своего компьютера или через упрощенную интрасеть в службах инфраструктуры Azure.
    
- [Синхронизация каталогов](dirsync-for-your-office-365-dev-test-environment.md)
    
    Установка и настройка Azure AD Connect для синхронизации каталогов с синхронизацией хэша паролей. Это действие не является обязательным для создания имитации конфигурации предприятия.
    
Следующие статьи можно использовать для демонстрации компонентов корпоративного выпуска Office 365 в среде разработки и тестирования Office 365:
  
- [Многофакторная проверка подлинности](multi-factor-authentication-for-your-office-365-dev-test-environment.md)
    
    Настройте и протестируйте дополнительную проверку подлинности, отправив текстовое сообщение на свой смартфон для учетной записи, указанной при подписке на Office 365.
    
- [Федеративное удостоверение](federated-identity-for-your-office-365-dev-test-environment.md)
    
    Настройка и демонстрация федеративной проверки подлинности для учетных записей, настроенных в доменных службах Active Directory (AD DS).
    
- [Расширенная защита от угроз](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
    
    Настройка и демонстрация Advanced Threat Protection — компонента Exchange Online Protection (EOP), позволяющего оградить электронную почту от вредоносных программ.

## <a name="simulated-cross-premises-devtest-environment"></a>Имитация распределенной среды разработки и тестирования

Создание [имитации интрасети](simulated-cross-premises-virtual-network-in-azure.md), подключенной к виртуальной сети Azure в гибридной облачной конфигурации.
    
## <a name="sharepoint-server-2016-devtest-environment"></a>Среда разработки и тестирования SharePoint Server 2016

Создание [односерверной фермы SharePoint Server 2016](https://docs.microsoft.com/SharePoint/administration/sharepoint-server-2016-dev-test-environment-in-azure) в службах инфраструктуры Azure.

## <a name="microsoft-365-enterprise-devtest-environment"></a>Среда разработки и тестирования Microsoft 365 корпоративный

Создание среды разработки и тестирования для [Microsoft 365 корпоративный](https://docs.microsoft.com/microsoft-365/enterprise/m365-enterprise-test-lab-guides).  
    
## <a name="see-also"></a>См. также

[Освоение облака и гибридные решения](cloud-adoption-and-hybrid-solutions.md)
  
[Ресурсы для администраторов, посвященные архитектуре Microsoft Cloud](microsoft-cloud-it-architecture-resources.md)
  
[Архитектурные модели для SharePoint, Exchange, Skype для бизнеса и Lync](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[Гибридные решения](hybrid-solutions.md)
