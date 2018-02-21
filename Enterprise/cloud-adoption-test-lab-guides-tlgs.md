---
title: "Руководства по лаборатории тестирования для принятия облачных решений"
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
- Strat_O365_Enterprise
- Ent_TLGs
ms.assetid: 706d5449-45e5-4b0c-a012-ab60501899ad
description: "Сводка: Используйте эти облака внедрения тестирование руководства по лаборатории (руководствам) для настройки для демонстрации, проверки концепции или средах разработки и тестирования для Office 365, мобильности Enterprise + безопасности (Командной), Dynamics 365 и продуктов Office Server."
ms.openlocfilehash: 3172b6033fbb7dd79b8eb786d92a4f58886a8fd5
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2018
---
# <a name="cloud-adoption-test-lab-guides-tlgs"></a>Руководства по лаборатории тестирования для принятия облачных решений

 **Сводка:** Настройка демонстрации, проверки концепции или средах разработки и тестирования для Office 365, мобильности Enterprise + безопасности (Командной), Dynamics 365 и продуктов Office Server с помощью этих облачных внедрения тестирование руководства по лаборатории (руководствам).
  
Руководства вы найдете помогают быстро узнать о продуктах Майкрософт. Они отлично подходит для ситуаций, где необходимо оценить технологии или конфигурации, прежде чем оно подходит ли вам или перед при развертывании в работе пользователей. Практический опыт «построения проблемы в работе и работы» помогает понять требования к развертыванию новый продукт или решений, чтобы вы могли лучше запланировать для размещения в рабочей среде.
  
Кроме того, эти руководства помогают создавать типичные среды для разработки и тестирования.
  
![Руководства по лаборатории тестирования в Microsoft Cloud](images/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
Прежде чем углубляться в разделе следующие дополнительные ресурсы:
  
- Просмотр сеанса Microsoft Virtual Academy [взаимодействия Microsoft Cloud с руководствах по лаборатории тестирования внедрения облака](https://mva.microsoft.com/en-US/training-courses/experience-the-microsoft-cloud-with-cloud-adoption-test-lab-guides-17960?l=LXNRdhSLE_1000115881 ) (только 22 минут).
    
- Щелкните [здесь](http://aka.ms/catlgstack), чтобы просмотреть схему всех статей, относящихся к руководствам по лаборатории тестирования Microsoft Cloud.
    
## <a name="office-365-devtest-environment"></a>Среда разработки и тестирования Office 365
<a name="O365"> </a>

Следующие статьи помогут вам создать среду разработки и тестирования Office 365:
  
- [Базовая конфигурация среды разработки и тестирования](base-configuration-dev-test-environment.md)
    
    Создание упрощенной интрасети, выполняющейся в службах инфраструктуры Microsoft Azure. Это действие не является обязательным для создания имитации конфигурации предприятия.
    
- [Среда разработки и тестирования Office 365](office-365-dev-test-environment.md)
    
    Создание подписки пробной версии Office 365 корпоративный E5, что можно сделать с компьютера или из интрасети упрощенный под управлением в службах инфраструктуры.
    
- [DirSync для среды разработки и тестирования Office 365](dirsync-for-your-office-365-dev-test-environment.md)
    
    Установка и настройка Azure AD Connect для синхронизации каталогов с синхронизацией паролей. Это действие не является обязательным для создания имитации конфигурации предприятия.
    
Для среды разработки и тестирования Office 365 используйте эти статьи для демонстрации компонентов корпоративного выпуска Office 365:
  
- [Многофакторная проверка подлинности для среды разработки и тестирования Office 365](multi-factor-authentication-for-your-office-365-dev-test-environment.md)
    
    Настройте и протестируйте дополнительную проверку подлинности, отправив текстовое сообщение на свой смартфон для учетной записи, указанной при подписке на Office 365.
    
- [Федеративное удостоверение для среды разработки и тестирования Office 365](federated-identity-for-your-office-365-dev-test-environment.md)
    
    Настройка и демонстрация федеративной проверки подлинности для учетных записей, настроенных в домене Windows Server Active Directory.
    
- [Облако безопасности приложения для Office 365 dev/тестовой среды](cloud-app-security-for-your-office-365-dev-test-environment.md)
    
    Настройка и демонстрация безопасности облачных приложения Office 365, которая позволяет создавать политики, которые наблюдения за и сообщить о подозрительных действий в подписки Office 365.
    
- [Дополнительные защиту от угроз для вашей среды разработки или тестирования Office 365](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
    
    Настройка и демонстрация Advanced Threat Protection — компонента Exchange Online Protection (EOP), позволяющего оградить электронную почту от вредоносных программ.
    
- [Расширенные eDiscovery для вашей среды разработки или тестирования Office 365](advanced-ediscovery-for-your-office-365-dev-test-environment.md)
    
    Добавление данных для примера и демонстрация функции Advanced eDiscovery, позволяющей быстро находить и анализировать данные, хранящиеся в Office 365, в том числе электронные сообщения и документы.
    
- [Защита конфиденциальных файлов в Office 365 dev/тестовой среде](sensitive-file-protection-in-the-office-365-dev-test-environment.md)
    
    Демонстрация того, как с помощью управления правами на доступ к данным Office 365 можно защитить конфиденциальные документы, даже если их случайно поместили не в ту папку.
    
- [Классификации данных и маркировки в Office 365 dev/тестовой среде](data-classification-and-labeling-in-the-office-365-dev-test-environment.md)
    
    Показано, как клиент защиты информации Azure (AIP) можно использовать для классификации документов с помощью различных уровней безопасности.
    
- [Изолированный SharePoint Online группы сайта dev/тестовой среды](isolated-sharepoint-online-team-site-dev-test-environment.md)
    
    Показано, как создать сайт группы SharePoint Online, изолируется от других отделов организации засекреченные или конфиденциальные сильно ресурсов для.
    
## <a name="the-microsoft-365-enterprise-devtest-environment"></a>Среда разработки и тестирования Microsoft 365 корпоративный
<a name="O365"> </a>

Создайте dev/тестовой среды для сценариев [Microsoft 365 для предприятия](https://docs.microsoft.com/microsoft-365-enterprise/) с в этих статьях:
  
- [Microsoft 365 Enterprise dev/тестовой среды](the-microsoft-365-enterprise-dev-test-environment.md)
    
    Создание начальной среды, включая Office 365 E5, Командной E5 и компьютера под управлением Windows 10 Enterprise.
    
- [MAM политик для вашей среды разработки или тестирования Microsoft 365 для предприятия](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
    
    Создание групп пользователей и политик управления мобильными приложениями (MAM) для устройств iOS и Android.
    
- [Регистрация операций ввода-вывода и Android в среде разработки и тестирования Microsoft Enterprise 365](enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-dev-test-environ.md)
    
    Регистрация устройств с ОС iOS или Android и удаленное управление ими.
    
## <a name="office-365-and-dynamics-365-devtest-environment"></a>Среда разработки и тестирования для Office 365 и Dynamics 365
<a name="O365_D365"> </a>

В следующих статьях описано, как добавить пробную подписку на Dynamics 365 и протестировать интегрированные компоненты и сценарии Office 365 и Dynamics 365:
  
- [Среда разработки и тестирования для Office 365 и Dynamics 365](office-365-and-dynamics-365-dev-test-environment.md)
    
    Добавьте пробную подписку на Dynamics 365, а также лицензии и разрешения на Dynamics 365 для учетных записей пользователей.
    
- [Функция интеграции с Exchange Online для Office 365 и Dynamics 365 dev/тестовой среды](exchange-online-integration-for-your-office-365-and-dynamics-365-dev-test-enviro.md)
    
    Настройка и затем Демонстрация Office 365 Dynamics 365 совместная работа и почтовых ящиков в Exchange Online.
    
## <a name="the-one-microsoft-cloud-devtest-environment"></a>Среда разработки и тестирования One Microsoft Cloud
<a name="O365_D365"> </a>

Создание среды разработки или тестирования, включающий все облака корпорации Майкрософт: Office 365, Azure, Командной и Dynamics 365. Просмотрите [один корпорации Майкрософт облачной dev/тестовой среды](the-one-microsoft-cloud-dev-test-environment.md) для получения пошаговых инструкций.
  
## <a name="simulated-cross-premises-devtest-environments"></a>Имитация гибридной среды разработки и тестирования
<a name="O365_D365"> </a>

Сведения о том, как создать гибридную среду тестирования и разработки, включающую виртуальную сеть Azure и имитацию локальной сети, вы найдете в таких статьях:
  
- [Имитации распределенной виртуальной сети в Azure](simulated-cross-premises-virtual-network-in-azure.md)
    
    Создание имитации интрасети, подключенной к виртуальной сети Azure в гибридной облачной конфигурации.
    
- [SharePoint Server интрасети 2016 в среде Azure разработку и тестирование](https://technet.microsoft.com/library/mt806351%28v=office.16%29.aspx)
    
    Создание односерверной фермы SharePoint Server 2016 в виртуальной сети Azure и проверка возможности подключения и администрирования в имитации локальной сети.
    
## <a name="additional-cloud-based-devtest-environments"></a>Дополнительные облачные среды разработки и тестирования
<a name="ADD_TLGs"> </a>

В службы инфраструктуры Azure можно также добавить следующие облачные среды разработки и тестирования:
  
- [SharePoint Server 2016 dev/тестовой среды в Azure](https://technet.microsoft.com/library/mt723354.aspx)
    
    Создание односерверной фермы SharePoint Server 2016 в службах инфраструктуры Azure.
    
- [Среда разработки и тестирования Exchange 2016 в Azure](https://technet.microsoft.com/library/mt733070%28v=exchg.160%29.aspx)
    
    Создание одного сервера Exchange 2016 в службах инфраструктуры Azure.
    
- [Среды разработки или тестирования SharePoint Server 2013 в Azure](http://technet.microsoft.com/library/165de4d5-8fe6-4fbb-a15b-39a8b0a0eb23.aspx)
    
    Создание ферм SharePoint Server 2013 (базовых и с высоким уровнем доступности) в службах инфраструктуры Azure.
    
**Присоединяйтесь к обсуждению**

|**Свяжитесь с нами**|**Описание**|
|:-----|:-----|
|**Какое вам решение необходимо?** <br/> |Мы создаем контент для решений, которые охватывают несколько продуктов и служб Майкрософт. Сообщите нам, что вы думаете о наших межсерверных решениях, или укажите интересующие вас решения, написав по адресу [MODAcontent@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20).<br/> |
|**Присоединяйтесь к обсуждению решений** <br/> |Если вам интересны облачные решения, присоединяйтесь к теме Cloud Adoption Advisory Board (CAAB) и общайтесь с разработчиками контента Майкрософт, специалистами отрасли и клиентами со всего мира. Чтобы присоединиться, добавьте себя в качестве участника [темы CAAB (Cloud Adoption Advisory Board)](https://aka.ms/caab) на сайте Microsoft Tech Community и отправьте нам письмо на адрес [CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!). Просматривать материалы в [блоге CAAB](https://blogs.technet.com/b/solutions_advisory_board/) могут все пользователи. Однако только участники CAAB получают приглашения на закрытые вебинары, на которых мы рассказываем о новых облачных решениях и ресурсах по их внедрению.<br/> |
|**Получите изображения, которые вы здесь видите** <br/> |Если вам нужна редактируемая копия иллюстративного материала из этой статьи, мы с радостью вам ее отправим. Напишите нам, указав URL-адрес и название материала, по адресу [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20).<br/> |
   
## <a name="see-also"></a>См. также

<a name="ADD_TLGs"> </a>

[Освоение облака и гибридные решения](cloud-adoption-and-hybrid-solutions.md)
  
[Ресурсы для администраторов, посвященные архитектуре Microsoft Cloud](microsoft-cloud-it-architecture-resources.md)
  
[Архитектурные модели для SharePoint, Exchange, Skype для бизнеса и Lync](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[Гибридные решения](hybrid-solutions.md)


