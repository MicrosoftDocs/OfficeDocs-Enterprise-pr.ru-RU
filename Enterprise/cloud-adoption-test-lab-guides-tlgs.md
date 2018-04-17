---
title: Руководства по лаборатории тестирования для облачных решений
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: hub-page
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: 706d5449-45e5-4b0c-a012-ab60501899ad
description: Сводка. Воспользуйтесь этими руководствами по лаборатории тестирования для облачных решений, чтобы настроить среды демонстрации, экспериментирования, разработки и тестирования для продуктов Office 365, Enterprise Mobility + Security (EMS), Dynamics 365 и Office Server.
ms.openlocfilehash: 1597bcefbcfa578e74d96676b3ea446c72a080bc
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="cloud-adoption-test-lab-guides-tlgs"></a>Руководства по лаборатории тестирования для облачных решений

 **Сводка.** Воспользуйтесь этими руководствами по лаборатории тестирования для облачных решений, чтобы настроить среды демонстрации, экспериментирования, разработки и тестирования для продуктов Office 365, Enterprise Mobility + Security (EMS), Dynamics 365 и Office Server.
  
Руководства по лаборатории тестирования содержат краткие сведения о продуктах Майкрософт. Они отлично подходят для ситуаций, в которых нужно оценить технологию или конфигурацию, прежде чем решать, подходит ли она вам, или прежде чем развертывать ее для пользователей. Такой интерактивный подход помогает ознакомиться с требованиями для развертывания нового продукта или решения и позволяет лучше спланировать его размещение в производственной среде.
  
Кроме того, эти руководства помогают создавать типичные среды для разработки и тестирования приложений.
  
![Руководства по лаборатории тестирования в Microsoft Cloud](images/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
Прежде чем приступить к освоению, ознакомьтесь с дополнительными ресурсами:
  
- Посмотрите сеанс в Microsoft Virtual Academy [Освоение Microsoft Cloud с руководствами по лаборатории тестирования для облачных решений](https://mva.microsoft.com/en-US/training-courses/experience-the-microsoft-cloud-with-cloud-adoption-test-lab-guides-17960?l=LXNRdhSLE_1000115881 ) (всего 22 минуты).
    
- Щелкните [здесь](http://aka.ms/catlgstack), чтобы просмотреть схему всех статей, относящихся к руководствам по лаборатории тестирования в One Microsoft Cloud.
    
## <a name="office-365-devtest-environment"></a>Среда разработки и тестирования Office 365
<a name="O365"> </a>

Следующие статьи помогут вам создать среду разработки и тестирования Office 365:
  
- [Базовая конфигурация среды разработки и тестирования](base-configuration-dev-test-environment.md)
    
    Создание упрощенной интрасети, выполняющейся в службах инфраструктуры Microsoft Azure. Это действие не является обязательным для создания имитации конфигурации предприятия.
    
- [Среда разработки и тестирования Office 365](office-365-dev-test-environment.md)
    
    Подписка на бесплатную пробную версию Office 365 корпоративный Е5, которую можно оформить со своего компьютера или через упрощенную интрасеть в службах инфраструктуры Azure.
    
- [DirSync для среды разработки и тестирования Office 365](dirsync-for-your-office-365-dev-test-environment.md)
    
    Установка и настройка Azure AD Connect для синхронизации каталогов с синхронизацией паролей. Это действие не является обязательным для создания имитации конфигурации предприятия.
    
Следующие статьи можно использовать для демонстрации компонентов корпоративного выпуска Office 365 в среде разработки и тестирования Office 365:
  
- [Многофакторная проверка подлинности для среды разработки и тестирования Office 365](multi-factor-authentication-for-your-office-365-dev-test-environment.md)
    
    Настройте и протестируйте дополнительную проверку подлинности, отправив текстовое сообщение на свой смартфон для учетной записи, указанной при подписке на Office 365.
    
- [Федеративное удостоверение для среды разработки и тестирования Office 365](federated-identity-for-your-office-365-dev-test-environment.md)
    
    Настройка и демонстрация федеративной проверки подлинности для учетных записей, настроенных в домене Windows Server Active Directory.
    
- [Cloud App Security для среды разработки и тестирования Office 365](cloud-app-security-for-your-office-365-dev-test-environment.md)
    
    Настройка и демонстрация компонента Office 365 Cloud App Security, с помощью которого можно создавать политики, отслеживающие подозрительные действия в вашей подписке на Office 365 и сообщающие вам о них.
    
- [Advanced Threat Protection в среде разработки и тестирования Office 365](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
    
    Настройка и демонстрация Advanced Threat Protection — компонента Exchange Online Protection (EOP), позволяющего оградить электронную почту от вредоносных программ.
    
- [Advanced eDiscovery для среды разработки и тестирования Office 365](advanced-ediscovery-for-your-office-365-dev-test-environment.md)
    
    Добавление данных для примера и демонстрация функции Advanced eDiscovery, позволяющей быстро находить и анализировать данные, хранящиеся в Office 365, в том числе электронные сообщения и документы.
    
- [Защита конфиденциальных файлов в среде разработки и тестирования Office 365](sensitive-file-protection-in-the-office-365-dev-test-environment.md)
    
    Демонстрация того, как с помощью управления правами на доступ к данным Office 365 можно защитить конфиденциальные документы, даже если их случайно поместили не в ту папку.
    
- [Классификация и маркировка данных в среде разработки и тестирования Office 365](data-classification-and-labeling-in-the-office-365-dev-test-environment.md)
    
    Демонстрация порядка использования клиента Azure Information Protection (AIP) для классификации документов с использованием различных уровней защиты.
    
- [Среда разработки и тестирования изолированного сайта группы SharePoint Online](isolated-sharepoint-online-team-site-dev-test-environment.md)
    
    Демонстрация процесса создания сайта группы SharePoint Online, функционирующего изолированно от всей организации с целью защиты ресурсов с высоким или средним уровнем конфиденциальности.
    
## <a name="the-microsoft-365-enterprise-devtest-environment"></a>Среда разработки и тестирования Microsoft 365 корпоративный
<a name="O365"> </a>

Следующие статьи можно использовать для создания среды разработки и тестирования для сценариев [Microsoft 365 корпоративный](https://docs.microsoft.com/microsoft-365-enterprise/):
  
- [Среда разработки и тестирования Microsoft 365 корпоративный](the-microsoft-365-enterprise-dev-test-environment.md)
    
    Создание начальной среды, которая включает в себя Office 365 E5, EMS E5 и компьютер на базе ОС Windows 10 Корпоративная.
    
- [Политики MAM для вашей среды разработки и тестирования Microsoft 365 корпоративный](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
    
    Создание групп пользователей и политик управления мобильными приложениями (MAM) для устройств iOS и Android.
    
- [Регистрация устройств на базе ОС iOS и Android в среде разработки и тестирования Microsoft 365 корпоративный](enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-dev-test-environ.md)
    
    Регистрация устройств с ОС iOS или Android и удаленное управление ими.
    
## <a name="office-365-and-dynamics-365-devtest-environment"></a>Среда разработки и тестирования для Office 365 и Dynamics 365
<a name="O365_D365"> </a>

В следующих статьях описано, как добавить пробную подписку на Dynamics 365 и протестировать интегрированные компоненты и сценарии Office 365 и Dynamics 365:
  
- [Среда разработки и тестирования для Office 365 и Dynamics 365](office-365-and-dynamics-365-dev-test-environment.md)
    
    Добавьте пробную подписку на Dynamics 365, а также лицензии и разрешения на Dynamics 365 для учетных записей пользователей.
    
- [Интеграция с Exchange Online для среды разработки и тестирования Office 365 и Dynamics 365](exchange-online-integration-for-your-office-365-and-dynamics-365-dev-test-enviro.md)
    
    Настройка и демонстрация совместной работы Office 365 и Dynamics 365 в почтовых ящиках Exchange Online.
    
## <a name="the-one-microsoft-cloud-devtest-environment"></a>Среда разработки и тестирования One Microsoft Cloud
<a name="O365_D365"> </a>

Создание среды разработки и тестирования, включающей все облачные решения корпорации Майкрософт: Office 365, Azure, EMS и Dynamics 365. Для ознакомления с пошаговыми инструкциями см. статью [Среда разработки и тестирования One Microsoft Cloud](the-one-microsoft-cloud-dev-test-environment.md).
  
## <a name="simulated-cross-premises-devtest-environments"></a>Имитация распределенной среды разработки и тестирования
<a name="O365_D365"> </a>

Сведения о том, как создать распределенную среду разработки и тестирования, включающую виртуальную сеть Azure и имитацию локальной сети, вы найдете в таких статьях:
  
- [Имитация распределенной виртуальной сети в Azure](simulated-cross-premises-virtual-network-in-azure.md)
    
    Создание имитации интрасети, подключенной к виртуальной сети Azure в гибридной облачной конфигурации.
    
- [Интрасеть SharePoint Server 2016 в среде разработки и тестирования Azure](https://technet.microsoft.com/library/mt806351%28v=office.16%29.aspx)
    
    Создание односерверной фермы SharePoint Server 2016 в виртуальной сети Azure и проверка возможности подключения и администрирования в имитации локальной сети.
    
## <a name="additional-cloud-based-devtest-environments"></a>Дополнительные облачные среды разработки и тестирования
<a name="ADD_TLGs"> </a>

В службы инфраструктуры Azure можно также добавить следующие облачные среды разработки и тестирования:
  
- [Среда разработки и тестирования SharePoint Server 2016 в Azure](https://technet.microsoft.com/library/mt723354.aspx)
    
    Создание односерверной фермы SharePoint Server 2016 в службах инфраструктуры Azure.
    
- [Среда разработки и тестирования Exchange 2016 в Azure](https://technet.microsoft.com/library/mt733070%28v=exchg.160%29.aspx)
    
    Создание одного сервера Exchange 2016 в службах инфраструктуры Azure.
    
- [Среда разработки и тестирования SharePoint Server 2013 в Azure](http://technet.microsoft.com/library/165de4d5-8fe6-4fbb-a15b-39a8b0a0eb23.aspx)
    
    Создание ферм SharePoint Server 2013 (базовых и с высоким уровнем доступности) в службах инфраструктуры Azure.
    
**Присоединяйтесь к обсуждению**

|**Свяжитесь с нами**|**Описание**|
|:-----|:-----|
|**Какое вам решение необходимо?** <br/> |Мы создаем контент для решений, которые охватывают несколько продуктов и служб Майкрософт. Сообщите нам, что вы думаете о наших межсерверных решениях, или укажите интересующие вас решения, написав по адресу [MODAcontent@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20).<br/> |
|**Присоединяйтесь к обсуждению решений** <br/> |Если вам интересны облачные решения, присоединяйтесь к теме Cloud Adoption Advisory Board (CAAB) и общайтесь с разработчиками контента Майкрософт, специалистами отрасли и клиентами со всего мира. Чтобы присоединиться, добавьте себя в качестве участника [темы CAAB (Cloud Adoption Advisory Board)](https://aka.ms/caab) на сайте Microsoft Tech Community и отправьте нам письмо на адрес [CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!). Просматривать материалы в [блоге CAAB](https://blogs.technet.com/b/solutions_advisory_board/) могут все пользователи. Однако только участники CAAB получают приглашения на закрытые вебинары, на которых мы рассказываем о новых облачных решениях и ресурсах по их внедрению.<br/> |
|**Скачать изображения, которые вы видите здесь** <br/> |Если вам нужна редактируемая копия иллюстративного материала из этой статьи, мы с радостью вам ее отправим. Напишите нам, указав URL-адрес и название материала, по адресу [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20).<br/> |
   
## <a name="see-also"></a>См. также

<a name="ADD_TLGs"> </a>

[Освоение облака и гибридные решения](cloud-adoption-and-hybrid-solutions.md)
  
[Ресурсы для администраторов, посвященные архитектуре Microsoft Cloud](microsoft-cloud-it-architecture-resources.md)
  
[Архитектурные модели для SharePoint, Exchange, Skype для бизнеса и Lync](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[Гибридные решения](hybrid-solutions.md)


