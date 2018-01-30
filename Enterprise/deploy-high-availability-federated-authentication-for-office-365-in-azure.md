---
title: "Развертывание в Azure федеративной проверки подлинности для обеспечения высокой доступности в случае использования Office 365"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Strat_O365_Enterprise
- Ent_Solutions
ms.assetid: 34b1ab9c-814c-434d-8fd0-e5a82cd9bff6
description: "Сводка. Настройка федеративной проверки подлинности с высоким уровнем доступности для подписки на Office 365 в Microsoft Azure."
ms.openlocfilehash: 111e52531e45e54b8ce53c3f530e9c9d273f24fc
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/11/2018
---
# <a name="deploy-high-availability-federated-authentication-for-office-365-in-azure"></a>Развертывание в Azure федеративной проверки подлинности для обеспечения высокой доступности в случае использования Office 365

 **Сводка.** Настройка федеративной проверки подлинности с высоким уровнем доступности для подписки на Office 365 в Microsoft Azure.
  
Эта статья содержит ссылки на пошаговые инструкции по развертыванию федеративной проверки подлинности с высоким уровнем доступности для Microsoft Office 365 в службах инфраструктуры Azure со следующими виртуальными машинами:
  
- два прокси-сервера веб-приложений;
    
- два сервера служб федерации Active Directory (AD FS);
    
- две реплики контроллеров домена;
    
- один сервер DirSync, на котором запущено средство Azure AD Connect.
    
Ниже приводится конфигурация с именами-заполнителями для каждого сервера.
  
**Инфраструктура федеративной проверки подлинности с высоким уровнем доступности для Office 365 в Azure**

![Окончательная конфигурация инфраструктуры для федеративной проверки подлинности Office 365 с высоким уровнем доступности в Azure](images/c5da470a-f2aa-489a-a050-df09b4d641df.png)
  
Все виртуальные машины находятся в единой виртуальной сети Azure из распределенного развертывания. 
  
> [!NOTE]
> Федеративная проверка подлинности для отдельных пользователей не зависит от локальных ресурсов. Но если распределенное подключение станет недоступным, контроллеры домена в виртуальной сети не получат тех обновлений для учетных записей пользователей и для групп, которые появились в локальной службе AD на сервере Windows Server. Чтобы этого не произошло, настройте высокую доступность для распределенного подключения. Дополнительные сведения см. в статье [Настройка высокодоступных подключений: распределенных и между виртуальными сетями]((https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-highlyavailable)).
  
Каждая пара виртуальных машин для определенной роли находится в отдельной подсети или группе доступности.
  
> [!NOTE]
> Поскольку эта виртуальная сеть соединена с локальной, в конфигурацию не входят виртуальные машины jumpbox и виртуальные машины наблюдения в подсети управления. Дополнительные сведения см. в статье [Запуск виртуальных машин Windows в n-уровневой архитектуре]((https://docs.microsoft.com/azure/guidance/guidance-compute-n-tier-vm)). 
  
Такая конфигурация обеспечивает федеративную проверку подлинности для всех пользователей Office 365, при которой они смогут применять для входа учетные данные Active Directory в Windows Server, а не учетную запись Office 365. Инфраструктура федеративной проверки подлинности включает группу избыточных серверов, которые проще развертывать в службах инфраструктуры Azure, чем в локальной сети периметра.
  
## <a name="bill-of-materials"></a>Перечень компонентов

Для этой базовой конфигурации требуется следующий набор служб Azure и компонентов:
  
- семь виртуальных машин;
    
- одна нелокальная виртуальная сеть с четырьмя подсетями;
    
- четыре группы ресурсов;
    
- три группы доступности;
    
- одна подписка Azure.
    
Ниже приводится список виртуальных машин, необходимых для данной конфигурации, а также их размеры по умолчанию.
  
|**Элемент**|**Описание виртуальной машины**|**Изображение коллекции Azure**|**Размер по умолчанию**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |Первый контроллер домена  <br/> |Windows Server 2016 Datacenter  <br/> |D2  <br/> |
|2.  <br/> |Второй контроллер домена  <br/> |Windows Server 2016 Datacenter  <br/> |D2  <br/> |
|3.  <br/> |Сервер Azure AD Connect  <br/> |Windows Server 2016 Datacenter  <br/> |D2  <br/> |
|4.  <br/> |Первый сервер AD FS  <br/> |Windows Server 2016 Datacenter  <br/> |D2  <br/> |
|5.  <br/> |Второй сервер AD FS  <br/> |Windows Server 2016 Datacenter  <br/> |D2  <br/> |
|6.  <br/> |Первый прокси-сервер веб-приложений  <br/> |Windows Server 2016 Datacenter  <br/> |D2  <br/> |
|7.  <br/> |Второй прокси-сервер веб-приложений  <br/> |Windows Server 2016 Datacenter  <br/> |D2  <br/> |
   
Рассчитать примерные затраты на эту конфигурацию можно с помощью [калькулятора цен Azure]((https://azure.microsoft.com/pricing/calculator/)).
  
## <a name="phases-of-deployment"></a>Этапы развертывания

Эта рабочая нагрузка развертывается на следующих этапах:
  
<<<<<<< HEAD
- [Федеративная проверка подлинности для обеспечения высокой доступности
Этап 1. Настройка Azure](high-availability-federated-authentication-phase-1-configure-azure.md). Создайте группы ресурсов, учетные записи хранения, группы доступности и нелокальную виртуальную сеть.
    
- [Федеративная проверка подлинности для обеспечения высокой доступности
Этап 2. Настройка контроллеров домена](high-availability-federated-authentication-phase-2-configure-domain-controllers.md). Создайте и настройте реплики контроллеров домена Windows Server Active Directory (AD) и сервера DirSync.
    
- [Федеративная проверка подлинности для обеспечения высокой доступности
Этап 3. Настройка серверов AD FS](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md). Создайте и настройте два сервера AD FS.
    
- [Федеративная проверка подлинности для обеспечения высокой доступности
Этап 4. Настройка прокси веб-приложений](high-availability-federated-authentication-phase-4-configure-web-application-pro.md). Создайте и настройте два прокси-сервера веб-приложений.
    
- [Федеративная проверка подлинности для обеспечения высокой доступности
Этап 5. Настройка федеративной проверки подлинности для Office 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md). Настройте федеративную проверку подлинности для подписки на Office 365.
- [Федеративная проверка подлинности для обеспечения высокой доступности
Этап 1. Настройка Azure](high-availability-federated-authentication-phase-1-configure-azure.md). Создайте группы ресурсов, учетные записи хранения, группы доступности и нелокальную виртуальную сеть.
    
- [Федеративная проверка подлинности для обеспечения высокой доступности
Этап 2. Настройка контроллеров домена](high-availability-federated-authentication-phase-2-configure-domain-controllers.md). Создайте и настройте реплики контроллеров домена Windows Server Active Directory (AD) и сервер DirSync.
    
- [Федеративная проверка подлинности для обеспечения высокой доступности
Этап 3. Настройка серверов AD FS](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md). Создайте и настройте два сервера AD FS.
    
- [Федеративная проверка подлинности для обеспечения высокой доступности
Этап 4. Настройка прокси веб-приложений](high-availability-federated-authentication-phase-4-configure-web-application-pro.md). Создайте и настройте два прокси-сервера веб-приложений.
    
- [Федеративная проверка подлинности для обеспечения высокой доступности
Этап 5. Настройка федеративной проверки подлинности для Office 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md). Настройте федеративную проверку подлинности для подписки на Office 365.
>>>>>>> образец
    
Эти статьи содержат поэтапное руководство по созданию функциональной федеративной проверки подлинности с высоким уровнем доступности для Office 365 в службах инфраструктуры Azure для предопределенной архитектуры. Учитывайте следующее:
  
- Если у вас уже есть опыт развертывания AD FS, можете скорректировать инструкции на этапах 3 и 4 и создать группу серверов для своих нужд.
    
- Если у вас уже есть гибридное облачное развертывание Azure с нелокальной виртуальной сетью, можете скорректировать или пропустить инструкции на этапах 1 и 2 и разместить серверы AD FS и прокси-серверы веб-приложений в соответствующих подсетях.
    
Для создания среды разработки и тестирования или экспериментальной версии этой конфигурации ознакомьтесь со статьей [Федеративное удостоверение для среды разработки и тестирования Office 365](federated-identity-for-your-office-365-dev-test-environment.md).
  
## <a name="next-step"></a>Следующее действие

Начните настройку этой рабочей нагрузки с ознакомления со статьей [Этап 1. Федеративная проверка подлинности для обеспечения высокой доступности: настройка Azure](high-availability-federated-authentication-phase-1-configure-azure.md). 
  
> [!TIP]
> Чтобы быстрее выполнить развертывание федеративной проверки подлинности с высоким уровнем доступности для Office 365 в Azure, воспользуйтесь [этим комплектом средств]((https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664)). 
  
## <a name="see-also"></a>См. также

[Федеративное удостоверение для среды разработки и тестирования Office 365](federated-identity-for-your-office-365-dev-test-environment.md)
  
[Освоение облака и гибридные решения](cloud-adoption-and-hybrid-solutions.md)

[Федеративные удостоверения для Office 365](https://support.office.com/article/Understanding-Office-365-identity-and-Azure-Active-Directory-06a189e7-5ec6-4af2-94bf-a22ea225a7a9#bk_federated)

