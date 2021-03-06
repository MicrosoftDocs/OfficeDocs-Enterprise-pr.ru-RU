---
title: "Облачное удостоверение Майкрософт для корпоративных архитекторов"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 7/19/2017
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Priority
ms.collection:
- Ent_O365
- Ent_O365_Visuals
ms.custom:
- DecEntMigration
- O365ITProTrain
- Strat_O365_Enterprise
- Ent_Architecture
ms.assetid: d27b5085-7325-4ab9-9d9a-438908a65d2c
description: "Сводка. Разработка решения для работы с удостоверениями для облачных служб и платформ Майкрософт."
---

# Облачное удостоверение Майкрософт для корпоративных архитекторов

 **Сводка.** Разработка решения для работы с удостоверениями для облачных служб и платформ Майкрософт.
  
В этой статье представлены сведения для ИТ-архитекторов о создании системы удостоверений для организаций, использующих облачные службы и платформы Майкрософт. Вы также можете просмотреть эту статью в виде 5-страничного плаката и распечатать его в табличном формате (регистр, 11 x 17 или A3).
  
[![Эскиз модели удостоверений для облака Майкрософт](images/ffa145a1-97e6-4c36-b08b-01c4a4ae8b9b.png)
  
](https://www.microsoft.com/download/details.aspx?id=54431)
  
![PDF-файл](images/ITPro_Other_PDFicon.png)[PDF](https://go.microsoft.com/fwlink/p/?LinkId=524586) |![Файл Visio](images/ITPro_Other_VisioIcon.jpg)[Visio](https://download.microsoft.com/download/2/3/8/238228E6-9017-4F6C-BD3C-5559E6708F82/MSFT_cloud_architecture_identity.vsd) |![См. страницу с версиями на дополнительных языках](images/e16c992d-b0f8-48ae-bf44-db7a9fcaab9e.png)[Другие языки](https://www.microsoft.com/download/details.aspx?id=54431)
  
Вы также можете просмотреть все модели в [Ресурсы для администраторов, посвященные архитектуре Microsoft Cloud](microsoft-cloud-it-architecture-resources.md) и документ[Схема корпоративного облака Майкрософт: ресурсы для ИТ-менеджеров](https://aka.ms/cloudarchitecture).
  
> [!NOTE]
> Эта статья основана на версии плаката **Облачное удостоверение Майкрософт для корпоративных архитекторов** за январь 2016 г. Она не содержит изменения из версии за апрель 2016 г.
  
## Разработка удостоверения для облака Майкрософт

Интеграция удостоверений с облаком Майкрософт предоставляет доступ к широкому выбору служб и облачных платформ. Существует два основных сценария:
  
- Вы можете выполнить интеграцию с Microsoft Azure Active Directory (AD). В частности, вам придется синхронизировать локальные учетные записи с Azure AD, поставщиком удостоверений для облака Майкрософт.
    
- Вы можете расширить локальную среду доменных служб Active Directory (AD DS) на виртуальные машины, работающие в службах инфраструктуры Microsoft Azure.
    
![Параметры для разработки облачных удостоверений](images/08277e96-e4d2-43cb-a56f-a11c7647881a.png)
  
 **Рисунок 1. Варианты разработки удостоверений в облаке**
  
На рис. 1 показано, что служба Azure AD является поставщиком удостоверений для служб "программное обеспечение как услуга" (SaaS) от Майкрософт и приложений Azure "платформа как услуга" (PaaS), а бизнес-приложения могут использовать локальные службы AD DS. 
  
### Azure Active Directory

Microsoft Azure AD  это размещаемая в облаке Майкрософт служба удостоверений и управления доступом. Она находится в центре облачных служб и платформ Майкрософт. Интеграция Azure AD предоставляет доступ ко всем SaaS-службам Майкрософт с помощью текущего набора учетных записей и паролей. Такая интеграция также предоставляет облачное удостоверение для приложений Azure PaaS. 
  
> [!NOTE]
> Azure AD не избавляет от необходимости использовать локальные доменные службы Active Directory для предприятий или виртуальных машин под управлением Windows, работающих в Azure "инфраструктура как услуга" (IaaS). 
  
Существует три выпуска Azure AD: бесплатный, базовый и расширенный. 
  
||||
|:-----|:-----|:-----|
|**Бесплатный** <br/> |**Базовый** <br/> |**Расширенный** <br/> |
| Управление учетными записями пользователей <br/>  Синхронизация с локальными каталогами <br/>  Единый вход в Azure, Office 365 и тысячах других популярных приложений SaaS, например Salesforce, Workday, Concur, DocuSign, Google Apps, Box, ServiceNow, Dropbox и многих других <br/> | Включает все возможности бесплатного выпуска, а также: <br/>  Фирменная символика <br/>  Групповой доступ к приложениям <br/>  Самостоятельный сброс пароля <br/>  Корпоративное соглашение об уровне обслуживания 99,9 % <br/> | Включает все функции бесплатного и базового выпусков, а также: <br/>  Самостоятельное управление группами <br/>  Расширенные отчеты и оповещения безопасности <br/>  Многофакторная проверка подлинности <br/>  Сброс пароля с обратной записью в локальные службы AD DS <br/>  Двунаправленная синхронизация с помощью средства Azure AD Connect <br/>  Прокси приложения Azure AD <br/>  Microsoft Forefront Identity Manager (MIM) <br/> |
   
Дополнительные сведения о версиях см. в статье [Выпуски Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524280).
  
### Вариант 1. Интеграция с Azure Active Directory

Большинство организаций синхронизируют стандартный набор объектов и атрибутов со своим клиентом Azure AD. Средство Azure AD Connect синхронизирует учетные записи между локальными службами AD DS и клиентом Azure AD.
  
![Интеграция с Azure AD](images/3ce05e49-2cb6-4cdc-99ab-d96c5bd12fe8.png)
  
 **Рисунок 2. Интеграция с Azure AD**
  
На рис. 2 показано, как средство Azure AD Connect получает изменения AD DS и отправляет их в клиент Azure AD. В этом случае клиент Azure AD является размещаемой в облаке копией важного содержимого локальных каталогов.
  
Во многих организациях AD DS используется в качестве локального поставщика удостоверений. В локальной среде можно использовать поставщик удостоверений другого типа (например, с использованием LDAP) и синхронизировать эти удостоверения с Azure AD.
  
### Вариант 2. Расширение доменных служб Active Directory в Azure

По сравнению с синхронизацией с Azure AD, при расширении AD DS на виртуальные машины в службах инфраструктуры Azure поддерживается другой набор решений и приложений. Вот два из них:
  
- Поддерживаются облачные решения, которым требуется проверка подлинности NTLM или Kerberos, или присоединенные к домену AD DS виртуальные машины.
    
- Дополнительный потенциал интеграции для облачных служб и приложений в облачных службах и платформах Майкрософт.
    
![Расширение доменных служб Active Directory в Azure](images/4675cf17-962c-4840-b1dc-bbd1d8894a27.png)
  
 **Рисунок 3. Расширение доменных служб Active Directory в Azure**
  
На рис. 3 показан контроллер домена AD DS, подключенный к виртуальной сети Azure через локальное VPN-устройство и VPN-шлюз Azure. Виртуальная сеть Azure содержит серверы для бизнес-приложения и собственный набор контроллеров доменов AD DS.
  
### Дополнительные сведения

- [Синхронизация каталога с Office 365  это просто!](https://go.microsoft.com/fwlink/p/?LinkId=524281)
    
- [Инфографика. Управление удостоверениями и доступом в облаке](https://go.microsoft.com/fwlink/p/?LinkId=524282)
    
- [Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524283)
    
## Интеграция локальных учетных записей AD DS с Microsoft Azure AD

После синхронизации локальных учетных записей AD DS с Azure AD пользователи смогут использовать свои локальные учетные записи AD DS для доступа:
  
- ко всем SaaS-службам Майкрософт (Office 365, Microsoft Intune и Dynamics CRM Online);
    
- к приложениям, работающим в Azure PaaS.
    
Два способа настройки этой интеграции:
  
- синхронизация каталогов и паролей;
    
- федерация и единый вход.
    
Начните с простейшего варианта, который соответствует вашим требованиям. При необходимости вы можете переключаться между этими вариантами.
  
> [!NOTE]
> В организациях корпоративного уровня не рекомендуется использовать облачные учетные записи (без интеграции с локальными доменными службами Active Directory). 
  
### синхронизация каталогов и паролей;

Это самый простой вариант, для которого требуется только сервер со средством Azure AD Connect. 
  
![Конфигурация синхронизации каталогов и паролей](images/e7dcfe8f-dab5-461e-89cc-d7a48f58dc0f.png)
  
 **Рисунок 4. Конфигурация синхронизации каталогов и паролей**
  
На рис. 4 показан локальный или частный облачный центр обработки данных с контроллером домена AD DS. Сервер, на котором запущено средство Azure AD Connect, синхронизирует список имен учетных записей с Azure AD.
  
При использовании этого варианта:
  
- Учетные записи пользователей из локальных доменных служб Active Directory (или другого поставщика удостоверений) синхронизируются с клиентом Azure AD. Локальный каталог остается полномочным источником учетных записей, в котором вы управляете всеми их изменениями.
    
- Azure AD выполняет все проверки подлинности для SaaS-служб Майкрософт и приложений Azure PaaS.
    
- Вы также можете настроить синхронизацию для нескольких лесов AD DS.
    
Если используется синхронизация паролей:
  
- При доступе к облачным службам пользователям предлагается ввести тот же пароль, который они используют для локальных ресурсов.
    
- Пароли пользователей никогда не отправляются в Azure AD открытым текстом. Вместо этого используется хэш пароля. Его криптографически невозможно расшифровать или реконструировать, чтобы получить открытый текст пароля. 
    
При многофакторной проверке подлинности (MFA):
  
- Вы можете пользоваться основными функциями MFA, включенными в Office 365.
    
- Разработчики приложений Azure PaaS могут пользоваться преимуществами службы многофакторной проверки подлинности Azure.
    
Синхронизация каталогов не обеспечивает интеграцию с локальными решениями MFA.
  
### федерация и единый вход.

Для этого варианта требуются дополнительные серверы и инфраструктура. 
  
![Сервера, необходимые для федеративной проверки подлинности](images/1e54f0d2-e650-4eb5-957f-4f1d3c44da16.png)
  
 **Рисунок 5. Серверы, необходимые для федеративной проверки подлинности**
  
На рис. 5 показан набор компонентов для федеративной проверки подлинности. Azure AD связывается с прокси-службой веб-приложения, отправляющей запрос проверки подлинности на сервер служб федерации Active Directory (AD FS), который отправляет запрос контроллеру домена AD DS для оценки и ответа. Сервер, на котором запущено средство Azure AD Connect, синхронизирует список имен учетных записей из AD DS с Azure AD.
  
Федерация предоставляет предприятиям следующие дополнительные возможности:
  
- Все запросы проверки подлинности, отправленные в Azure AD, направляются локальному поставщику удостоверений и выполняются в нем через AD FS.
    
- Поддерживаются поставщики удостоверений сторонних поставщиков.
    
- Синхронизация хэша паролей может служить запасным вариантом для федеративного входа (например, в случае сбоя федеративной проверки подлинности).
    
Используйте федерацию, если:
  
- Необходим единый вход. С единым входом пользователям не предлагается вводить учетные данные (имя пользователя и пароль) при доступе к облачной службе.
    
- Службы федерации Active Directory уже развернуты.
    
- Используется сторонний поставщик удостоверений.
    
- Используется Forefront Identity Manager 2010 R2 (не поддерживается синхронизация хэша паролей).
    
- У вас есть локальная встроенная смарт-карта или другое решение MFA.
    
- Требуется аудит входа и/или отключение учетных записей.
    
- Организации требуются ограничения входа клиентов по сетевому расположению или рабочим часам.
    
- Организация должна соответствовать Федеральному стандарту обработки информации (FIPS).
    
Для федеративной проверки подлинности требуется больше инвестиций в локальную инфраструктуру.
  
- Локальные серверы должны быть доступны из Интернета через корпоративный брандмауэр. Корпорация Майкрософт рекомендует использовать серверы прокси-служб веб-приложений, развернутые в сети периметра.
    
- Необходимы оборудование, лицензии и операции для серверов AD FS, прокси-серверов AD FS или серверов прокси-служб веб-приложений, брандмауэров и подсистем балансировки нагрузки. 
    
- Доступность и производительность важны, чтобы пользователи имели доступ к Office 365 и другим облачным приложениям.
    
### Дополнительные сведения

- [Синхронизация каталога с Office 365  это просто!](https://go.microsoft.com/fwlink/p/?LinkId=524281)
    
- [Подготовка пользователей к работе путем синхронизации каталогов с Office 365](https://go.microsoft.com/fwlink/p/?LinkId=524284)
    
- [Многофакторная проверка подлинности для Office 365](https://go.microsoft.com/fwlink/p/?LinkID=392012)
    
- [Многофакторная проверка подлинности Azure](https://go.microsoft.com/fwlink/p/?LinkId=524285)
    
- [TechEd 2014. Интеграция каталогов: создание одного каталога с Active Directory и Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524286)
    
## Расширение доменных служб Active Directory в Azure

Расширение AD DS в Azure  это первый шаг к поддержке бизнес-приложений, выполняющихся на виртуальных машинах в службах инфраструктуры Azure, которые предоставляют:
  
- поддержку облачных решений, которым требуется проверка подлинности NTLM или Kerberos, либо виртуальных машин, присоединенных к домену AD DS;
    
- дополнительный потенциал интеграции для облачных служб и приложений с возможностью добавления в любой момент.
    
![Расширение доменных служб Active Directory в виртуальной сети Azure](images/9fe2e27d-7fc8-441a-a694-1db4b9f6d03f.png)
  
 **Рисунок 6. Расширение доменных служб Active Directory в виртуальной сети Azure**
  
На рис. 6 показан локальный или частный облачный центр обработки данных с доменными службами Active Directory, подключенными к виртуальной сети Azure с подключением ExpressRoute или VPN-подключением типа "сеть-сеть". Виртуальная сеть Azure содержит серверы для бизнес-приложения и собственный набор контроллеров доменов AD DS. Эта конфигурация является гибридным развертыванием AD DS в локальной среде и службах инфраструктуры Azure. Для нее требуется следующее:
  
- виртуальная сеть Azure;
    
- соединение между устройством локальной виртуальной частной сети (VPN) или маршрутизатором и VPN-шлюзом Azure;
    
- часть локального пространства IP-адресов, отведенная под виртуальные машины в виртуальной сети;
    
- развертывание одного или нескольких контроллеров доменов в виртуальной сети, назначенных серверами глобального каталога (это снижает исходящий трафик в VPN-подключении).
    
По сравнению с синхронизацией с Azure AD, эта архитектура удостоверений поддерживает другой набор решений и приложений.
  
### Варианты подключения локальной среды к Azure

Чтобы подключить локальную сеть к виртуальной сети Azure, вы можете использовать:
  
- VPN-подключение типа "сеть-сеть", которое может объединить 1-10 сайтов (включая другие виртуальные сети Azure) в одну виртуальную сеть Azure;
    
- ExpressRoute, частное, защищенное подключение глобальной сети к Azure через партнерскую сеть и поставщика служб центра обработки данных. Подключения ExpressRoute могут обеспечивать повышенную надежность, увеличенную пропускную способность и сокращенное время задержки.
    
### Дополнительные сведения

- [О безопасных распределенных подключениях для виртуальных сетей](https://go.microsoft.com/fwlink/p/?LinkId=524293)
    
- [Технический обзор ExpressRoute](https://go.microsoft.com/fwlink/?LinkID=392081)
    
- [Руководства по развертыванию Windows Server Active Directory на виртуальных машинах Azure](https://go.microsoft.com/fwlink/p/?LinkId=524295)
    
## Интеграция приложений с облачными удостоверениями

Во время проектирования и разработки приложений, работающих в облаке, следует ориентироваться на согласованность пользовательского интерфейса для процесса проверки подлинности, включая набор необходимых учетных данных. Например, при использовании учетных данных Windows в Azure AD или расширенных доменных службах Active Directory, убедитесь, что пользователи могут быстро пройти проверку подлинности и сосредоточиться на своих задачах.
  
![Интеграция приложений с облачными удостоверениями](images/1e6304b0-fa15-4f80-a3b4-7507a28808ae.png)
  
 **Рисунок 7. Интеграция приложений с облачными удостоверениями**
  
На рис. 7 показано три варианта интеграции приложения с облачными удостоверениями.
  
1. Регистрация размещаемых в облаке приложений с Azure AD.
    
    См. статью [Интеграция приложений с Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524303) на портале MSDN. Это позволяет использовать Azure AD для проверки подлинности при доступе к приложению PaaS, а также позволяет пользователям или администраторам предоставлять права доступа к приложению, чтобы другие пользователи могли получать доступ к содержимому от их имени из других облачных служб, например Office 365. Дополнительные сведения и примеры кода можно найти в статье[Сценарии проверки подлинности в Azure AD](https://go.microsoft.com/fwlink/p/?LinkId=524304) на портале MSDN.
    
2. Приложения, которым необходима программная проверку подлинности для доступа к приложению, защищенному с помощью AD DS, AD FS на сервере Windows Server 2012 R2 или Azure AD, могут использовать:
    
  - [Azure AD Graph API](https://go.microsoft.com/fwlink/p/?LinkId=524305);
    
  - [библиотеку проверки подлинности Active Directory (ADAL)](https://go.microsoft.com/fwlink/p/?LinkID=524297).
    
    Azure AD Graph API поддерживает OAuth и OpenID Connect. Этот интерфейс также поддерживает приложения PaaS.
    
3. Настройте локальные приложения или бизнес-приложения, работающие на виртуальных машинах в виртуальной сети Azure, на непосредственное использование проверки подлинности Windows (NTLM или Kerberos). Это обеспечивает максимальное удобство для пользователей и упрощает настройку для разработчиков серверных приложений.
    
### Пример интеграции приложений

Организация создает приложение ASP.NET, которое открывает конечную точку REST, где другие приложения могут получать последние данные о продажах. Доступ к этой конечной точке REST защищен с помощью Azure AD. Приложения должны предоставлять учетные данные, которые может проверить служба Azure AD, прежде чем приложение ASP.NET отправит запрашиваемые данные. Затем другие разработчики в организации могут создавать собственные приложения, использующие данные о продажах из конечной точки REST.
  
Чтобы пройти проверку подлинности в Azure AD и получить данные, ADAL управляет процессом проверки подлинности пользователя и передает маркер доступа приложению, чтобы его можно было использовать для доступа к данным о продажах. ADAL избавляет от большинства сложностей, связанных с получением и анализом маркеров, потоков OAuth и других элементов. ADAL  это еще одна стремительно развивающаяся технология, поэтому разработчикам следует искать последнюю версию на сайте NuGet.
  
## Развертывание компонентов каталога в Azure

Вы можете развертывать компоненты каталогов, например серверы для синхронизации паролей или федеративной проверки подлинности, в виртуальной сети Azure, а не в локальном центре обработки данных. Учитывайте ее преимущества, особенно если вы планируете расширить AD DS в Azure.
  
В виртуальную сеть Azure можно поместить следующие компоненты:
  
- средство Azure AD Connect;
    
- компоненты федеративной проверки подлинности;
    
- автономная среда AD DS.
    
### Средство AD Connect

Средство Azure AD Connect можно разместить в облачной виртуальной сети Azure. Учитывайте следующие преимущества развертывания этой рабочей нагрузки в Azure:
  
- потенциально ускоренная подготовка и сниженная стоимость операций;
    
- повышенная доступность.
    
![Средство AD Connect, работающее в службах инфраструктуры Azure](images/97593481-e06a-4e34-b8b5-cc63acb5f9f1.png)
  
 **Рисунок 8. Средство AD Connect, запущенное в Azure**
  
На рис. 8 показано средство AD Connect, работающее на виртуальной машине в виртуальной сети Azure, которая отправляет запрос изменений учетных записей локальному контроллеру домена AD DS, а затем отправляет эти изменения в Office 365. Это решение работает:
  
- со службами Office 365;
    
- с приложениями Azure PaaS, доступными через Интернет;
    
- с бизнес-приложениями в Azure, доступными из локальных сред через подключение ExpressRoute или VPN-подключение типа "сеть-сеть".
    
Дополнительные сведения см. в статье [Интеграция локальных удостоверений с Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524307).
  
### Инфраструктура федеративной проверки подлинности

Если вы еще не развернули AD FS в локальной среде, учитывайте следующие преимущества развертывания рабочей нагрузки в Azure:
  
- Автономная проверка подлинности в облачных службах (без зависимостей от локальной среды).
    
- Меньшее количество серверов и средств в локальной среде.
    
- Используется VPN-шлюз типа "сеть-сеть" в отказоустойчивом кластере с двумя узлами для подключения к Azure (новый).
    
- Используется ACL, чтобы прокси-серверы приложений могли напрямую взаимодействовать только с AD FS, а не с контроллерами доменов или другими серверами.
    
![Развертывание инфраструктуры федеративной проверки подлинности в Azure](images/4e023dd4-b9fb-403a-a8eb-069b56d7a65e.png)
  
 **Рисунок 9. Развертывание инфраструктуры федеративной проверки подлинности в Azure**
  
На рис. 9 показан набор локальных контроллеров доменов, которые реплицируют сведения из AD DS, с набором контроллеров доменов в виртуальной сети Azure. Средство Azure AD Connect. выполняющееся на сервере в виртуальной сети Azure, отправляет локальным контроллерам доменов запросы на изменения, а затем отправляет эти изменения в Azure AD. Входящие запросы проверки подлинности в Azure AD из SaaS-служб Майкрософт, приложений Azure PaaS и других облачных приложений отправляются во внешнюю подсистему балансировки нагрузки, которая направляет запрос набору серверов прокси-служб веб-приложений. Серверы прокси-служб веб-приложений отправляют запрос внешней подсистеме балансировки нагрузки, которая перенаправляет запрос набору серверов AD FS. Затем серверы AD FS перенаправляют запрос на контроллер домена, чтобы проверить учетные данные отправки.
  
 Это решение работает:
  
- с приложениями, требующими Kerberos;
    
- со всеми SaaS-службами Майкрософт;
    
- с приложениями в Azure, имеющими доступ к Интернету;
    
- с приложениями в Azure IaaS или PaaS, которым требуется проверка подлинности с набором учетных записей в доменных службах Active Directory организации.
    
Дополнительные сведения см. в статье [Интеграция локальных удостоверений с Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524307).
  
### Автономная среда AD DS в виртуальной сети Azure

Облачное приложение не всегда необходимо интегрировать с локальной средой. Например, автономный домен AD DS в виртуальной сети Azure поддерживает общедоступные приложения, например сайты Интернета.
  
![Отдельная среда доменных служб Active Directory для серверного приложения](images/98c7349f-535d-4c9b-8de4-e580f6d573d4.png)
  
 **Рисунок 10. Отдельная среда доменных служб Active Directory для серверного приложения**
  
На рис. 10 показана виртуальная сеть Azure, которая содержит серверы AD DS, а также предоставляет службы AD DS и DNS, с набором серверов, на которых размещается приложение. Это решение работает:
  
- с веб-сайтами и приложениями Интернета;
    
- с приложениями, требующими проверку подлинности NTLM или Kerberos;
    
- с приложениями на серверах под управлением Windows, требующих AD DS.
    
Дополнительные сведения см. в статье [Интеграция локальных удостоверений с Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524307).
  
## See Also

#### 

[Ресурсы для администраторов, посвященные архитектуре Microsoft Cloud](microsoft-cloud-it-architecture-resources.md)
#### 

[Схема корпоративного облака Майкрософт: ресурсы для ИТ-менеджеров](https://sway.com/FJ2xsyWtkJc2taRD)

