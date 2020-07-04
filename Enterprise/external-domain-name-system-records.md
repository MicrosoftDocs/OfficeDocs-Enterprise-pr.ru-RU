---
title: Внешние записи DNS для Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 10/21/2019
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: c0531a6f-9e25-4f2d-ad0e-a70bfef09ac0
description: Сводка. Список записей DNS для планирования развертывания Office 365.
ms.openlocfilehash: d0804cec4ce2c15345a9c4ddc83525d1961f8db4
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "44996543"
---
# <a name="external-domain-name-system-records-for-office-365"></a>Внешние записи DNS для Office 365

|||
|:-----|:-----|
|![Домен](media/e05b1c78-1df0-4200-ba40-6e26b7ead68f.png)|**Want to see a customized list of DNS records for your Office 365 organization?** You can [find the info you need to create Office 365 DNS records](https://support.office.microsoft.com/article/Gather-the-information-you-need-to-create-Office-365-DNS-records-77f90d4a-dc7f-4f09-8972-c1b03ea85a67) for your domain in Office 365.  <br/> **Need step-by-step help to add these records at your domain's DNS host, such as GoDaddy or eNom?** [Find links to step-by-step instructions for many popular DNS hosts](https://go.microsoft.com/fwlink/?LinkId=286745). <br/>  **Sticking around to use the reference list for your own custom deployment?** The below list should be used as a reference for your custom Office 365 deployment. You will need to select which records apply to your organization and fill in the appropriate values. <br/> **Возврат к статье** [Планирование сети и настройка производительности для Office 365](https://aka.ms/tune).  <br/> |

Often the SPF and MX records are the hardest to figure out. We've updated our SPF records guidance at the end of this article. The important thing to remember is that _you can only have a single SPF record for your domain_. You can have multiple MX records; however, that can cause problems for mail delivery. Having a single MX record that directs email to one mail system removes many potential problems.
  
The sections below are organized by service in Office 365. To see a customized list of the Office 365 DNS records for your domain, sign in to Office 365 and [Gather the information you need to create Office 365 DNS records](https://support.office.com/article/77f90d4a-dc7f-4f09-8972-c1b03ea85a67).
  
## <a name="external-dns-records-required-for-office-365-core-services"></a>Внешние записи DNS, необходимые для Office 365 (основные службы)
<a name="BKMK_ReqdCore"> </a>

Every Office 365 customer needs to add two records to their external DNS. The first CNAME record ensures that Office 365 can direct workstations to authenticate with the appropriate identity platform. The second required record is to prove you own your domain name.
  
||||
|:-----|:-----|:-----|
|**Запись DNS** <br/> |**Назначение** <br/> |**Значение для использования** <br/> |
|**CNAME** <br/> **(Пакет)** <br/> |Used by Office 365 to direct authentication to the correct identity platform. [More information](https://go.microsoft.com/fwlink/p/?LinkId=322005) <br/> **Примечание.** Эта запись CNAME применяется только к службе Office 365, предоставляемой компанией 21Vianet.   |**Псевдоним:** msoid  <br/> **Целевое значение:** clientconfig.partner.microsoftonline-p.net.cn  <br/> |
|**TXT** <br/> **(Проверка домена)** <br/> |Used by Office 365 to verify only that you own your domain. It doesn't affect anything else.  <br/> |**Узел:** @ (или доменное имя для некоторых поставщиков услуг размещения DNS)  <br/> **Значение TXT:** _текстовая строка, предоставленная_ Office 365  <br/> **Мастер настройки домена** Office 365 предоставляет значения, которые можно использовать для создания этой записи.  <br/> |


## <a name="external-dns-records-required-for-email-in-office-365-exchange-online"></a>Внешние записи DNS, необходимые для электронной почты в Office 365 (Exchange Online)
<a name="BKMK_ReqdCore"> </a>

Email in Office 365 requires several different records. The three primary records that all customers should use are the Autodiscover, MX, and SPF records.
  
- **Запись автообнаружения** позволяет клиентским компьютерам автоматически находить Exchange и настраивать клиент соответствующим образом.

- **The MX record** tells other mail systems where to send email for your domain. **Note:** When you change your email to Office 365, by updating your domain's MX record, ALL email sent to that domain will start coming to Office 365.  
Вы хотите перенести в Office 365 лишь несколько адресов? Воспользуйтесь [пилотным развертыванием Office 365 с несколькими адресами электронной почты в личном домене](https://support.office.com/article/39cee536-6a03-40cf-b9c1-f301bb6001d7).

- **Запись типа TXT для SPF** используется принимающими почтовыми системами для проверки отправляющих серверов. Это помогает предотвратить такие проблемы, как спуфинг и фишинг электронной почты. Сведения о создании подобных записей см. в разделе [Внешние записи DNS, необходимые для SPF](external-domain-name-system-records.md#BKMK_SPFrecords) в этой статье.

Для пользователей электронной почты, использующих федерацию Exchange, в нижней части таблицы приведены необходимые дополнительные записи CNAME и TXT.
  
||||
|:-----|:-----|:-----|
|**Запись DNS** <br/> |**Назначение** <br/> |**Значение для использования** <br/> |
|**CNAME** <br/> **(Exchange Online)** <br/> |Helps Outlook clients to easily connect to the Exchange Online service by using the Autodiscover service. Autodiscover automatically finds the correct Exchange Server host and configures Outlook for users.  <br/> |**Псевдоним:** autodiscover  <br/> **Целевое значение:** autodiscover.outlook.com  <br/> |
|**MX** <br/> **(Exchange Online)** <br/> |Отправляет входящую почту для домена в службу Exchange Online в Office 365.  <br/> [!NOTE] Как только сообщения электронной почты начнут поступать в Exchange Online, следует удалить записи MX, указывающие на старую систему.   |**Домен:** например, contoso.com  <br/> **Целевой сервер электронной почты:** \<MX token\> . mail.protection.outlook.com  <br/> **Предпочтение/приоритет:** ниже, чем у всех остальных записей MX (это гарантирует доставку почты в Exchange Online) — например, 1 или "низкий"  <br/>  Чтобы найти свой \<MX token\> , выполните указанные ниже действия.  <br/>  Войдите в Office 365 и перейдите в раздел администратора Office 365 \> "Домены".  <br/>  В столбце действий для вашего домена выберите "Исправить ошибки".  <br/>  В разделе записей MX выберите пункт "Что необходимо исправить?"  <br/>  Следуйте указаниям на этой странице, чтобы обновить запись MX.  <br/> [Что такое приоритет записей MX?](https://go.microsoft.com/fwlink/p/?LinkId=396471) <br/> |
|**SPF (TXT)** <br/> **(Exchange Online)**  <br/> |Helps to prevent other people from using your domain to send spam or other malicious email. Sender policy framework (SPF) records work by identifying the servers that are authorized to send email from your domain.  <br/> |[Внешние записи DNS, необходимые для SPF](external-domain-name-system-records.md#BKMK_SPFrecords) <br/> |
|**TXT** <br/> **(федерация Exchange)** <br/> |Применяется для федерации Exchange для гибридного развертывания.  <br/> |**Запись TXT 1:** например, contoso.com и специально созданный связанный хэш-текст для подтверждения права собственности на домен (например, Y96nu89138789315669824)  <br/> **Запись TXT 2:** например, exchangedelegation.contoso.com и специально созданный связанный хэш-текст для подтверждения права собственности на домен (например, Y3259071352452626169)  <br/> |
|**CNAME** <br/> **(федерация Exchange)** <br/> |Helps Outlook clients to easily connect to the Exchange Online service by using the Autodiscover service when your company is using Exchange federation. Autodiscover automatically finds the correct Exchange Server host and configures Outlook for your users.  <br/> |**Псевдоним:** например, Autodiscover.service.contoso.com  <br/> **Целевое значение:** autodiscover.outlook.com  <br/> |


## <a name="external-dns-records-required-for-skype-for-business-online"></a>Внешние записи DNS, необходимые для Skype для бизнеса Online
<a name="BKMK_ReqdCore"> </a>

Чтобы правильно настроить сеть с использованием [URL-адресов и диапазонов IP-адресов Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2#BKMK_LYO) необходимо выполнить определенные действия.

> [!NOTE]
> Эти записи DNS применяются и для Teams, в частности, в случае с гибридным сценарием Teams и Skype для бизнеса Online, когда могут возникать определенные проблемы федерации.
  
||||
|:-----|:-----|:-----|
|**Запись DNS** <br/> |**Назначение** <br/> |**Значение для использования** <br/> |
|**SRV** <br/> **(Skype для бизнеса Online)** <br/> |Allows your Office 365 domain to share instant messaging (IM) features with external clients by enabling SIP federation. Read more about [Office 365 URLs and IP address ranges](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2#BKMK_LYO).  <br/> |**Служба:** sipfederationtls  <br/> **Протокол:** TCP  <br/> **Приоритет:** 100  <br/> **Вес:** 1  <br/> **Порт:** 5061  <br/> **Целевое значение:** sipfed.online.lync.com  <br/> **Примечание.** Если брандмауэр или прокси-сервер блокирует поиск SRV на внешнем DNS, эту запись необходимо также добавить во внутреннюю запись DNS.   |
|**SRV** <br/> **(Skype для бизнеса Online)** <br/> |Используется Skype для бизнеса для координации потока сведений между клиентами Lync.  <br/> |**Служба:** sip  <br/> **Протокол:** TLS  <br/> **Приоритет:** 100  <br/> **Вес:** 1  <br/> **Порт:** 443  <br/> **Целевое значение:** sipdir.online.lync.com  <br/> |
|**CNAME** <br/> **(Skype для бизнеса Online)** <br/> |Используется клиентом Lync для помощи в поиске службы Skype для бизнеса Online и входа.  <br/> |**Псевдоним:** sip  <br/> **Целевое значение:** sipdir.online.lync.com  <br/> Дополнительные сведения см. в статье [URL-адреса и диапазоны IP-адресов Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2#BKMK_LYO).  <br/> |
|**CNAME** <br/> **(Skype для бизнеса Online)** <br/> |Используется мобильным клиентом Lync для помощи в поиске службы Skype для бизнеса Online и входа.  <br/> |**Псевдоним:** lyncdiscover  <br/> **Целевое значение:** webdir.online.lync.com  <br/> |

## <a name="external-dns-records-required-for-office-365-single-sign-on"></a>Внешние записи DNS, необходимые для единого входа Office 365
<a name="BKMK_ReqdCore"> </a>

||||
|:-----|:-----|:-----|
|**Запись DNS** <br/> |**Назначение** <br/> |**Значение для использования** <br/> |
|**Узел (A)** <br/> |Used for single sign-on (SSO). It provides the endpoint for your off-premises users (and on-premises users, if you like) to connect to your Active Directory Federation Services (AD FS) federation server proxies or load-balanced virtual IP (VIP).  <br/> |**Целевое значение:** например, sts.contoso.com  <br/> |

## <a name="external-dns-records-required-for-spf"></a>Внешние записи DNS, необходимые для SPF
<a name="BKMK_SPFrecords"> </a>

> [!IMPORTANT]
> SPF is designed to help prevent spoofing, but there are spoofing techniques that SPF cannot protect against. In order to protect against these, once you have set up SPF, you should also configure DKIM and DMARC for Office 365. To get started, see [Use DKIM to validate outbound email sent from your domain in Office 365](https://technet.microsoft.com/library/mt695945%28v=exchg.150%29.aspx). Next, see [Use DMARC to validate email in Office 365](https://technet.microsoft.com/library/mt734386%28v=exchg.150%29.aspx).
  
SPF records are TXT records that help to prevent other people from using your domain to send spam or other malicious email. Sender policy framework (SPF) records work by identifying the servers that are authorized to send email from your domain.
  
You can only have one SPF record (that is, a TXT record that defines SPF) for your domain. That single record can have a few different inclusions but the total DNS lookups that result can't be more than 10 (this helps prevent denial of service attacks). See the table and other examples below to help you create or update the right SPF record values for your environment.
  
### <a name="structure-of-an-spf-record"></a>Структура записи SPF

All SPF records contain three parts: the declaration that it is an SPF record, the domains, and IP addresses that should be sending email, and an enforcement rule. You need all three in a valid SPF record. Here's an example of a common SPF record for Office 365 when you use only Exchange Online email:
  
``` dns
TXT Name @
Values: v=spf1 include:spf.protection.outlook.com -all
```

Система электронной почты, получающая сообщение из вашего домена, выполняет поиск записи SPF. Если для отправки письма использовался почтовый сервер Office 365, сообщение будет получено. Если же письмо отправлено с помощью вашей старой почтовой системы или нежелательной системы из Интернета, проверка SPF может завершиться ошибкой и сообщение не будет доставлено. Проверки наподобие этой помогают предотвратить спуфинг и фишинговые сообщения.
  
### <a name="choose-the-spf-record-structure-you-need"></a>Выбор необходимой структуры записи SPF

В случаях, когда в Office 365 используется не только электронная почта Exchange Online (например, также используется почта, поступающая из SharePoint Online), вы можете определить, что нужно включить в значение записи, с помощью приведенной ниже таблицы.
  
> [!NOTE]
> If you have a complicated scenario that includes, for example, edge email servers for managing email traffic across your firewall, you'll have a more detailed SPF record to set up. Learn how: [Set up SPF records in Office 365 to help prevent spoofing](https://go.microsoft.com/fwlink/?LinkId=787656). You can also learn much more about how SPF works with Office 365 by reading [How Office 365 uses Sender Policy Framework (SPF) to help prevent spoofing](https://go.microsoft.com/fwlink/?LinkId=787065).
  
|||||
|:-----|:-----|:-----|:-----|
||Используемая система  <br/> |Назначение  <br/> |Добавьте эти включения  <br/> |
|1   <br/> |Все почтовые системы (обязательно)  <br/> |Все записи SPF начинаются с этого значения  <br/> |v=spf1  <br/> |
|2   <br/> |Exchange Online (распространено)  <br/> |Используйте только с Exchange Online  <br/> |include:spf.protection.outlook.com  <br/> |
|3   <br/> |Сторонняя почтовая система (менее распространено)  <br/> ||include:\<email system like mail.contoso.com\>  <br/> |
|4   <br/> |Локальная почтовая система (менее распространено)  <br/> |Применяйте, если вы используете службу Exchange Online Protection или Exchange Online вместе с другой почтовой системой  <br/> |ip4:\<0.0.0.0\>  <br/> ip6:\< : : \>  <br/> include:\<mail.contoso.com\>  <br/> В угловых скобках (\<\>) следует указать другие почтовые системы, которые будут использоваться для отправки почты для вашего домена.  <br/> |
|5   <br/> |Все почтовые системы (обязательно)  <br/> ||-all  <br/> |

### <a name="example-adding-to-an-existing-spf-record"></a>Пример. Добавление значений в существующую запись SPF
<a name="bkmk_addtospf"> </a>

If you already have an SPF record, you'll need to add or update values for Office 365. For example, say your existing SPF record for contoso.com is this:
  
``` dns
TXT Name @
Values: v=spf1 ip4:60.200.100.30 include:smtp.adatum.com -all
```

Теперь вы обновляете запись SPF для Office 365. Вы измените текущую запись, чтобы у вас была запись SPF, включающая необходимые значения. Для Office 365 "spf.protection.outlook.com".
  
Правильный вариант:
  
``` dns
TXT Name @
Values: v=spf1 ip4:60.200.100.30 include:spf.protection.outlook.com include:smtp.adatum.com -all
```

Неправильный вариант:
  
``` dns
Record 1:
TXT Name @
Values: v=spf1 ip4:60.200.100.30 include:smtp.adatum.com -all
Record 2:
Values: v=spf1 include:spf.protection.outlook.com -all
```

### <a name="more-examples-of-common-spf-values"></a>Другие примеры распространенных значений SPF
<a name="bkmk_addtospf"> </a>

Если вы используете полный набор Office 365 и используете MailChimp для отправки маркетинговых сообщений электронной почты от вашего имени, запись SPF в contoso.com может выглядеть следующим образом, в которой используются строки 1, 3 и 5 из таблицы выше. Помните, что требуются строки 1 и 5.
  
``` dns
TXT Name @
Values: v=spf1 include:spf.protection.outlook.com include:servers.mcsv.net -all
```

Если вы используете гибридную конфигурацию Exchange, в которой сообщения электронной почты отправляются из Office 365 и вашей локальной почтовой системы, ваша запись SPF на contoso.com может выглядеть следующим образом:
  
``` dns
TXT Name @
Values: v=spf1 include:spf.protection.outlook.com include:mail.contoso.com -all
```

These are some common examples that can help you adapt your existing SPF record when you add your domain to Office 365 for email. If you have a complicated scenario that includes, for example, edge email servers for managing email traffic across your firewall, you'll have a more detailed SPF record to set up. Learn how: [Set up SPF records in Office 365 to help prevent spoofing](https://go.microsoft.com/fwlink/?LinkId=787656).
  
Вы можете быстро вернуться сюда с помощью этой короткой ссылки: [https://aka.ms/o365edns](https://aka.ms/o365edns)
