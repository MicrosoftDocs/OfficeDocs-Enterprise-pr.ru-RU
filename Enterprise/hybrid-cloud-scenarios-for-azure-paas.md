---
title: "Сценарии гибридного облака для Azure PaaS"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/1/2016
ms.audience: ITPro
ms.topic: overview
ms.prod: office-online-server
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Visuals
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: 5f4f5d0d-4638-48e8-a517-bd804856b617
description: "Сводка. Сведения о гибридной архитектуре и сценариях для облачных предложений на основе Microsoft PaaS в Azure."
---

# Сценарии гибридного облака для Azure PaaS

 **Сводка.** Сведения о гибридной архитектуре и сценариях для облачных предложений на основе Microsoft PaaS в Azure.
  
Объедините локальные данные или вычислительные ресурсы с новыми либо преобразованными приложениями, работающими в Azure PaaS. Это позволит воспользоваться преимуществами производительности, надежности и масштабирования облачных решений, а также улучшить поддержку пользователей мобильных приложений. 
  
## Архитектура гибридного сценария Azure PaaS

На рисунке 1 показана архитектура гибридных сценариев на основе Microsoft PaaS в Azure.
  
**Рис. 1. Гибридные сценарии на основе Microsoft PaaS в Azure**

![Гибридные сценарии на основе Microsoft PaaS в Azure](images/b003b15c-db66-4a3f-8cd9-3ab2e01601fe.png)
  
Для каждого слоя архитектуры:
  
- Приложения и сценарии
    
    Гибридное приложение PaaS выполняется в Azure и использует локальные вычислительные ресурсы или ресурсы хранилища.
    
- Удостоверение
    
    Включает синхронизацию службы каталогов или федерацию со сторонним поставщиком удостоверений.
    
- Сеть
    
    Состоит из имеющегося интернет-канала или подключения ExpressRoute с открытым пирингом к Azure PaaS. Приложению Azure PaaS необходимо предоставить доступ к локальным вычислительным ресурсам или ресурсам хранилища.
    
- Локальная среда
    
    Состоит из инфраструктуры удостоверений и безопасности, а также имеющихся бизнес-приложений или серверов баз данных, к которым приложение Azure PaaS может получить безопасный доступ.
    
## Гибридное приложение Azure PaaS

На рисунке 2 показана конфигурация гибридного приложения, выполняемого в Azure.
  
**Рис. 2. Гибридное приложение на основе Azure PaaS**

![Гибридное приложение на основе Azure PaaS](images/7d945c8e-346b-4610-8a02-dbaa9396e1f7.png)
  
На рисунке 2 показана локальная сеть, в которой на серверах размещаются хранилище или приложения, а также зона DMZ, содержащая прокси-сервер. Локальная сеть подключена к службам Azure PaaS через интернет-канал или с помощью подключения ExpressRoute.
  
Организации могут предоставить гибридному приложению Azure PaaS доступ к своим вычислительным ресурсам или ресурсам хранилища следующими способами:
  
- разместив ресурсы на серверах в DMZ;
    
- разместив обратный прокси-сервер в DMZ, что обеспечивает входящим запросам на основе HTTPS, прошедшим проверку подлинности, доступ к локальному ресурсу.
    
Приложение Azure может использовать учетные данные:
  
- из службы Azure AD, которую можно синхронизировать с локальным поставщиком удостоверений, например Windows Server AD; 
    
- от стороннего поставщика удостоверений.
    
### Пример гибридного приложения Azure PaaS

На рисунке 3 показан пример гибридного приложения, выполняемого в Azure.
  
**Рис. 3. Пример гибридного приложения на основе Azure PaaS**

![Пример гибридного приложения на основе Azure PaaS](images/63051bbc-918b-4ae9-aa87-a43668a0067b.png)
  
На рисунке 3 показана локальная сеть, в которой размещается бизнес-приложение. В Azure PaaS находится настраиваемое мобильное приложение. Подключенный к Интернету смартфон получает доступ к настраиваемому мобильному приложению в Azure, которое отправляет запросы данных локальному бизнес-приложению.
  
В этом примере гибридное приложение Azure PaaS представляет собой настраиваемое мобильное приложение, которое предоставляет обновленные контактные данные сотрудников. Сквозной гибридный сценарий включает:
  
- приложение для смартфона, для запуска которого требуются проверенные локальные учетные данные;
    
- настраиваемое мобильное приложение, выполняемое в Azure PaaS, которое запрашивает сведения о конкретных сотрудниках на основе запросов, полученных от приложения для смартфона пользователя;
    
- обратный прокси-сервер в DMZ, который проверяет настраиваемое мобильное приложение и пересылает запрос;
    
- ферму серверов бизнес-приложений, которая обслуживает запрос контактных данных при наличии соответствующих разрешений в учетной записи пользователя.
    
Так как локальный поставщик удостоверений синхронизирован с Azure AD, настраиваемое мобильное приложение и бизнес-приложение могут проверить имя учетной записи пользователя, отправившего запрос.
  
## База данных Stretch в SQL Server 2016

База данных Stretch  это функция SQL Server 2016, которая позволяет прозрачно и безопасно переместить редко используемые данные, например данные о закрытой компании в большой таблице со сведениями о заказах клиентов, в базу данных Stretch в SQL Azure.
  
При использовании функции Stretch содержимое экземпляра SQL Server, база данных или даже одна таблица являются сочетанием локальных данных на сервере SQL Server 2016 и удаленных данных в Azure. SQL Server 2016 автоматически перемещает в Azure данные, которые поддерживают функцию Stretch.
  
На рисунке 4 показана база данных Stretch в SQL Server 2016.
  
**Рис. 4. База данных Stretch в SQL Server 2016**

![База данных Stretch с SQL Server 2016](images/bab0812e-eef0-4667-9939-cd398d33a196.png)
  
На рисунке 4 показана локальная сеть, в которой размещен сервер SQL Server 2016 с небольшой локальной базой данных. В Azure PaaS размещен экземпляр растянутой базы данных Stretch сервера SQL Azure. Запросы T-SQL, отправляемые от локальных пользователей на локальный сервер SQL, безопасно перенаправляются в базу данных Stretch SQL Azure, которая возвращает результаты запросов пользователям.
  
 Запросы пользователей, которые содержат архивные данные, прозрачно перенаправляются в базу данных Stretch в SQL Azure. Несмотря на то что таблица растягивается, запросы не нужно записывать повторно.
  
База данных Stretch представляет собой экономически эффективное решение для долгосрочного хранения архивных данных и прозрачного доступа к ним. Кроме того, она позволяет решить проблемы производительности и доступности, возникающие при значительном увеличении таблиц.
  
Дополнительные сведения см. в статье [База данных Stretch](https://msdn.microsoft.com/ru-ru/library/dn935011.aspx).
  
## See Also

#### 

[Гибридное облако Майкрософт для корпоративных архитекторов](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[Ресурсы для администраторов, посвященные архитектуре Microsoft Cloud](microsoft-cloud-it-architecture-resources.md)
#### 

[Стратегия Enterprise Cloud корпорации Майкрософт: ресурсы для лиц, принимающих решения в области ИТ](https://sway.com/FJ2xsyWtkJc2taRD)

