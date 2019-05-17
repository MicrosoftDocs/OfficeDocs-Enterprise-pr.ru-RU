---
title: Развертывание Office 365 корпоративный для организации
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- M365-subscription-management
ms.custom: Adm_O365
ms.assetid: ee73dafb-be54-492e-bcfd-0fbfb5f65e94
description: С помощью описанных здесь действий вы сможете развернуть Office 365, подключить Active Directory, выполнить перенос данных, а также помочь пользователям организации приступить к работе с последней версией Office 2016.
ms.openlocfilehash: 2530b170c607f635f6f1baebf1d83fa7745d23a6
ms.sourcegitcommit: 47c6156c0038745103b71f44b2a3b103c62e5d6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/16/2019
ms.locfileid: "34102547"
---
# <a name="deploy-office-365-enterprise-for-your-organization"></a>Развертывание Office 365 корпоративный для организации
Готовы развернуть и интегрировать Office 365 корпоративный в свою локальную инфраструктуру? С помощью описанных здесь действий вы сможете подключить свой каталог, выполнить перенос данных, а также помочь пользователям организации приступить к работе с последней версией Office 2016.
  
Эти инструкции предназначены для коммерческих и [некоммерческих](https://go.microsoft.com/fwlink/?LinkId=627221) организаций, которым требуется выполнить индивидуальное развертывание Office 365 корпоративный. 
  
У вас не Office 365 корпоративный? См. инструкции для предприятий малого бизнеса в статье [Настройка Office 365 для бизнеса](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa). 
  
## <a name="guided-enterprise-office-365-setup-process-with-fasttrack"></a>Процесс настройки Office 365 в организации под руководством службы FastTrack
Оптимальный способ развертывания Office 365 — служба **[FastTrack](https://docs.microsoft.com/fasttrack)**. Программа FastTrack помогает выбрать одну из самых распространенных конфигураций развертывания, а также найти ответы на возникающие вопросы. Если вы хотите выполнить развертывание самостоятельно или под руководством партнера, см. наши статьи [Руководство по настройке Office 365](https://support.office.com/article/Set-up-Office-365-for-business-6a3a29a0-e616-4713-99d1-15eda62d04fa), [Мастера настройки Office 365](https://aka.ms/o365fasttrack) или [найдите соответствующего партнера](https://partnercenter.microsoft.com/en-us/pcv/search).

## <a name="self-deployment-of-office-365"></a>Самостоятельное развертывание Office 365
Если вы хотите самостоятельно развернуть Office 365, воспользуйтесь приведенными ниже инструкциями по развертыванию.

1. **[Подготовка к миграции на Office 365](get-your-organization-ready-for-office-365.md)**. Эти инструменты и ресурсы помогут вам подготовить сеть, каталог и пользователей к использованию Office 365.

2. **Войдите и добавьте Интернет-домены в Office 365**. Войдите в [центр администрирования Microsoft 365](https://portal.microsoft.com), выберите пункт **Настройка доменов _гт_**, а затем нажмите кнопку **создать домен**. Добавьте один или несколько доменов в вашу подписку на Office 365, не добавляя пользователей и не переносят электронную почту. 

>[!IMPORTANT] 
>Инструкции по базовой настройке не актуальны, если вы хотите синхронизировать пользователей из локального каталога или задействовать службу единого входа.

3. **[Подключение каталога к Office 365](about-office-365-identity.md)**. Руководство по синхронизации удостоверений и параметрам настройки единого входа. Используйте [помощник по AAD Connect](https://aka.ms/aadconnectpwsync) и [руководство по настройке Azure AD Premium](https://aka.ms/aadpguidance) для получения индивидуальных рекомендаций по настройке.
4. **[Настройка служб и приложений Office 365](configure-services-and-applications.md)**. На этом этапе выполняется настройка электронной почты, общего доступа к файлам, системы обмена мгновенными сообщениями, а также других служб и приложений Office 365.
5. **[Перенос данных в Office 365](migrate-data-to-office-365.md)**. После настройки служб можно начать перенос данных.
6. **[Перевод пользователей на Office 365](https://support.office.com/article/Get-started-with-Office-365-for-business-d6466f0d-5d13-464a-adcb-00906ae87029)**. Помогите пользователям из своей организации приступить к уверенной работе с Office 365 с помощью этих ресурсов.