---
title: Развертывание Office 365 корпоративный для организации
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- M365-subscription-management
ms.custom: Adm_O365
ms.assetid: ee73dafb-be54-492e-bcfd-0fbfb5f65e94
description: С помощью описанных здесь действий вы сможете развернуть Office 365, подключить Active Directory, выполнить перенос данных, а также помочь пользователям организации приступить к работе с последней версией Office 2016.
ms.openlocfilehash: 76421a7870358e48798f21866d69672509084c6a
ms.sourcegitcommit: fd137a68c516379a9f09e06987e8d45d92de7ed6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/27/2019
ms.locfileid: "30303603"
---
# <a name="deploy-office-365-enterprise-for-your-organization"></a><span data-ttu-id="96c96-103">Развертывание Office 365 корпоративный для организации</span><span class="sxs-lookup"><span data-stu-id="96c96-103">Deploy Office 365 Enterprise for your organization</span></span>
<span data-ttu-id="96c96-p101">Готовы развернуть и интегрировать Office 365 корпоративный в свою локальную инфраструктуру? С помощью описанных здесь действий вы сможете подключить свой каталог, выполнить перенос данных, а также помочь пользователям организации приступить к работе с последней версией Office 2016.</span><span class="sxs-lookup"><span data-stu-id="96c96-p101">Ready to deploy and integrate Office 365 Enterprise with your on-premises infrastructure? These overview steps are designed to help you connect your directory, migrate your data, and help the people in your organization begin using the latest version of Office 2016.</span></span>
  
<span data-ttu-id="96c96-106">Эти инструкции предназначены для коммерческих и [некоммерческих](https://go.microsoft.com/fwlink/?LinkId=627221) организаций, которым требуется выполнить индивидуальное развертывание Office 365 корпоративный.</span><span class="sxs-lookup"><span data-stu-id="96c96-106">These steps are for businesses and [nonprofits](https://go.microsoft.com/fwlink/?LinkId=627221) that want to start with a custom deployment of Office 365 Enterprise.</span></span> 
  
<span data-ttu-id="96c96-p102">У вас не Office 365 корпоративный? См. инструкции для предприятий малого бизнеса в статье [Настройка Office 365 для бизнеса](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa).</span><span class="sxs-lookup"><span data-stu-id="96c96-p102">Don't have Office 365 Enterprise? See [Set up Office 365 for business](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa) for instructions for small businesses.</span></span> 
  
## <a name="guided-enterprise-office-365-setup-process-with-fasttrack"></a><span data-ttu-id="96c96-109">Процесс настройки Office 365 в организации под руководством службы FastTrack</span><span class="sxs-lookup"><span data-stu-id="96c96-109">Guided enterprise Office 365 setup process with FastTrack</span></span>
<span data-ttu-id="96c96-p103">Оптимальный способ развертывания Office 365 — служба **[FastTrack](https://docs.microsoft.com/fasttrack)**. Программа FastTrack помогает выбрать одну из самых распространенных конфигураций развертывания, а также найти ответы на возникающие вопросы. Если вы хотите выполнить развертывание самостоятельно или под руководством партнера, см. наши статьи [Руководство по настройке Office 365](https://support.office.com/article/Set-up-Office-365-for-business-6a3a29a0-e616-4713-99d1-15eda62d04fa), [Мастера настройки Office 365](https://aka.ms/o365fasttrack) или [найдите соответствующего партнера](https://partnercenter.microsoft.com/ru-RU/pcv/search).</span><span class="sxs-lookup"><span data-stu-id="96c96-p103">Office 365 **[FastTrack](https://docs.microsoft.com/fasttrack)** is the best method for deploying Office 365. FastTrack guides you through the most common deployment configurations and can answer questions along the way. If you want to self-help or guidance from a partner, use our [Office 365 setup guide](https://support.office.com/article/Set-up-Office-365-for-business-6a3a29a0-e616-4713-99d1-15eda62d04fa), our [Office 365 setup wizards](https://aka.ms/o365fasttrack), or [find a qualified partner](https://partnercenter.microsoft.com/ru-RU/pcv/search).</span></span>

## <a name="self-deployment-of-office-365"></a><span data-ttu-id="96c96-113">Самостоятельное развертывание Office 365</span><span class="sxs-lookup"><span data-stu-id="96c96-113">Self-deployment of Office 365</span></span>
<span data-ttu-id="96c96-114">Если вы хотите самостоятельно развернуть Office 365, воспользуйтесь приведенными ниже инструкциями по развертыванию.</span><span class="sxs-lookup"><span data-stu-id="96c96-114">If you want to deploy Office 365 on your own, the following deployment steps are here to help.</span></span>

1. <span data-ttu-id="96c96-p104">**[Подготовка к миграции на Office 365](get-your-organization-ready-for-office-365.md)**. Эти инструменты и ресурсы помогут вам подготовить сеть, каталог и пользователей к использованию Office 365.</span><span class="sxs-lookup"><span data-stu-id="96c96-p104">**[Get ready for Office 365](get-your-organization-ready-for-office-365.md)**. These tools and resources will help you get your network, directory, and end users ready for Office 365.</span></span>

2. <span data-ttu-id="96c96-p105">**[Вход и добавление своих доменов в Office 365](https://portal.office.com/Domains/AddDomainWizard.aspx?Scenario=AdvancedSetup)**. Войдите на портал и добавьте один или несколько доменов в подписку на Office 365 без добавления пользователей и переноса электронной почты. Если вы хотите сразу задать необходимые параметры для всех пользователей и служб, следуйте нашим [инструкциям по базовой настройке](https://support.office.com/article/Set-up-Office-365-for-business-6a3a29a0-e616-4713-99d1-15eda62d04fa).</span><span class="sxs-lookup"><span data-stu-id="96c96-p105">**[Sign in and add your internet domain(s) to Office 365](https://portal.office.com/Domains/AddDomainWizard.aspx?Scenario=AdvancedSetup)**. Sign into the portal and add one or more domains to your Office 365 subscription without adding users or migrating email. If you want to configure all your users and services at the same time, follow our [basic set up instructions](https://support.office.com/article/Set-up-Office-365-for-business-6a3a29a0-e616-4713-99d1-15eda62d04fa).</span></span>

>[!IMPORTANT] 
><span data-ttu-id="96c96-120">Инструкции по базовой настройке не актуальны, если вы хотите синхронизировать пользователей из локального каталога или задействовать службу единого входа.</span><span class="sxs-lookup"><span data-stu-id="96c96-120">The basic set up instructions won't work if you want to synchronize your users from an on-premises directory or utilize Single Sign-On.</span></span>

3. <span data-ttu-id="96c96-p106">**[Подключение каталога к Office 365](https://support.office.com/article/Understanding-Office-365-Identity-and-Azure-Active-Directory-06a189e7-5ec6-4af2-94bf-a22ea225a7a9)**. Руководство по синхронизации удостоверений и параметрам настройки единого входа. Используйте [помощник по AAD Connect](https://aka.ms/aadconnectpwsync) и [руководство по настройке Azure AD Premium](https://aka.ms/aadpguidance) для получения индивидуальных рекомендаций по настройке.</span><span class="sxs-lookup"><span data-stu-id="96c96-p106">**[Connect your directory to Office 365](https://support.office.com/article/Understanding-Office-365-Identity-and-Azure-Active-Directory-06a189e7-5ec6-4af2-94bf-a22ea225a7a9)**. Guide to the identity synchronization and/or single sign-on configuration options. Use the [AAD Connect advisor](https://aka.ms/aadconnectpwsync) and the [Azure AD Premium setup guide](https://aka.ms/aadpguidance) to get customized set up guidance.</span></span>
4. <span data-ttu-id="96c96-p107">**[Настройка служб и приложений Office 365](configure-services-and-applications.md)**. На этом этапе выполняется настройка электронной почты, общего доступа к файлам, системы обмена мгновенными сообщениями, а также других служб и приложений Office 365.</span><span class="sxs-lookup"><span data-stu-id="96c96-p107">**[Configure Office 365 services and applications](configure-services-and-applications.md)**. Start here to configure email, file sharing, instant messaging, or any of the other Office 365 services and applications.</span></span>
5. <span data-ttu-id="96c96-p108">**[Перенос данных в Office 365](migrate-data-to-office-365.md)**. После настройки служб можно начать перенос данных.</span><span class="sxs-lookup"><span data-stu-id="96c96-p108">**[Migrate data to Office 365](migrate-data-to-office-365.md)**. Once the services are configured, you can start migrating data.</span></span>
6. <span data-ttu-id="96c96-p109">**[Перевод пользователей на Office 365](https://support.office.com/article/Get-started-with-Office-365-for-business-d6466f0d-5d13-464a-adcb-00906ae87029)**. Помогите пользователям из своей организации приступить к уверенной работе с Office 365 с помощью этих ресурсов.</span><span class="sxs-lookup"><span data-stu-id="96c96-p109">**[Get people using Office 365](https://support.office.com/article/Get-started-with-Office-365-for-business-d6466f0d-5d13-464a-adcb-00906ae87029)**. Help people in your organization build confidence using Office 365 with these resources.</span></span>