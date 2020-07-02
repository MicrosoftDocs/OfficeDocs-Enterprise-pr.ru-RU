---
title: Добавление домена к аренде клиента с помощью Windows PowerShell для партнеров службы разрешений делегированного доступа (DAP)
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- M365-subscription-management
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: f49b4d24-9aa0-48a6-95dd-6bae9cf53d2c
description: 'Сводка: используйте Windows PowerShell для Microsoft 365, чтобы добавить альтернативное доменное имя к существующему клиенту клиента.'
ms.openlocfilehash: 6ba706c1fc0b2e2b43687ac582a40f36a2a3387c
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "44997365"
---
# <a name="add-a-domain-to-a-client-tenancy-with-windows-powershell-for-delegated-access-permission-dap-partners"></a>Добавление домена к аренде клиента с помощью Windows PowerShell для партнеров службы разрешений делегированного доступа (DAP)

Вы можете создавать и связывать новые домены с клиентской учетной записью с помощью Windows PowerShell для Microsoft 365 быстрее, чем при использовании центра администрирования Microsoft 365.
  
Партнеры по делегированным правам доступа (DAP)  партнеры по синдикации и поставщики облачных решений (CSP). Они часто бывают поставщиками сети или телекоммуникационных услуг в других компаниях. Они объединяют подписки на Microsoft 365 на свои услуги своим клиентам. Когда вы продаете подписку на Microsoft 365, им автоматически предоставляются разрешения на администрирование от имени пользователя (АОБО), чтобы они могли администрировать и предоставлять отчеты для клиентов клиенты.
## <a name="what-do-you-need-to-know-before-you-begin"></a>Что нужно знать перед началом работы?

The procedures in this topic require you to connect to Windows PowerShell for Office 365. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).
  
Вам также необходимы учетные данные администратора для клиента партнера.
  
Кроме того, понадобятся указанные ниже сведения.
  
- Необходимо полное доменное имя (FQDN), которое  требуется вашему клиенту.
    
- Вам необходим идентификатор **TenantId** пользователя.
    
- The FQDN must be registered with an Internet domain name service (DNS) registrar, such as GoDaddy. For more information on how to publically register a domain name, see [How to buy a domain name](https://go.microsoft.com/fwlink/p/?LinkId=532541).
    
- Вам необходимо знать, как добавить запись типа TXT в зарегистрированную зону DNS для своего регистратора DNS. Дополнительные сведения о том, как добавить запись TXT, можно узнать [в статье Добавление записей DNS для подключения к домену](https://go.microsoft.com/fwlink/p/?LinkId=532542). Если эти действия вам не помогут, потребуется найти инструкции, касающиеся вашего регистратора DNS.
    
## <a name="create-domains"></a>Создание доменов

 Your customers will likely ask you to create additional domains to associate with their tenancy because they don't want the default <domain>.onmicrosoft.com domain to be the primary one that represents their corporate identities to the world. This procedure walks you through creating a new domain associated with your customer's tenancy.
  
> [!NOTE]
> Для выполнения некоторых из этих операций учетная запись администратора партнера, с помощью которой вы входите в систему, должна быть настроена на **полный** доступ к параметру **назначить административный доступ к компаниям, которые вы поддерживаете** , в сведениях о учетной записи администратора в центре администрирования Microsoft 365. Дополнительные сведения об управлении ролями администраторов партнеров приведены в статье [партнеры: предлагается делегированное администрирование](https://go.microsoft.com/fwlink/p/?LinkId=532435). 
  
### <a name="create-the-domain-in-azure-active-directory"></a>Создание домена в Azure Active Directory

Эта команда создает домен в Azure Active Directory, но не связывает его с публично зарегистрированным доменом. Это поступает, когда вы подтверждаете, что вы являетесь владельцем общедоступного домена Microsoft 365 для предприятий.
  
```
New-MsolDomain -TenantId <customer TenantId> -Name <FQDN of new domain>
```

>[!Note]
>В PowerShell Core не поддерживается модуль Microsoft Azure Active Directory для Windows PowerShell и командлеты с компонентом **Msol** в имени. Чтобы использовать эти командлеты, необходимо запустить их из Windows PowerShell.
>

### <a name="get-the-data-for-the-dns-txt-verification-record"></a>Получение данных для записи TXT проверки DNS

 Microsoft 365 создаст определенные данные, которые необходимо разместить в записи проверки DNS TXT. Чтобы получить эти данные, выполните указанную ниже команду.
  
```
Get-MsolDomainVerificationDNS -TenantId <customer TenantId> -DomainName <FQDN of new domain> -Mode DnsTxtRecord
```

Выходные данные будут иметь следующий вид:
  
 `Label: domainname.com`
  
 `Text: MS=ms########`
  
 `Ttl: 3600`
  
> [!NOTE]
> Этот текст потребуется для создания записи TXT в публично зарегистрированной зоне DNS. Обязательно скопируйте и сохраните его. 
  
### <a name="add-a-txt-record-to-the-publically-registered-dns-zone"></a>Добавление записи TXT в публично зарегистрированную зону DNS

Прежде чем Microsoft 365 начнет принимать трафик, направленный на общедоступный доменное имя, необходимо доказать, что у вас есть права администратора домена. Для этого нужно создать для домена запись типа TXT. Такая запись не выполняет никаких действий в домене, и ее можно удалить, когда ваше владение доменом будет подтверждено. Чтобы создать записи TXT, выполните действия, описанные в разделе [Add DNS Records to Connect Domain](https://go.microsoft.com/fwlink/p/?LinkId=532542). Если эти действия вам не помогут, потребуется найти процедуры для своего регистратора DNS.
  
Confirm the successful creation of the TXT record via nslookup. Follow this syntax.
  
```
nslookup -type=TXT <FQDN of registered domain>
```

Выходные данные будут иметь следующий вид:
  
 `Non-authoritative answer:`
  
 `FQDN of the registered domain`
  
 `text=MS=ms########`
  
### <a name="validate-domain-ownership-in-microsoft-365"></a>Проверка владения доменом в Microsoft 365

На последнем этапе вы проверите до Microsoft 365, что вы владеете общедоступным зарегистрированным доменом. После выполнения этого действия Microsoft 365 начнет принимать трафик, направленный на новое доменное имя. Чтобы завершить процесс создания и регистрации домена, выполните следующую команду. 
  
```
Confirm-MsolDomain -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

Эта команда не возвращает выходных данных, поэтому для проверки выполните следующую команду.
  
```
Get-MsolDomain -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

Выходные данные имеют следующий вид:
  
||||
|:-----|:-----|:-----|
| `Name` <br/> | `Status` <br/> | `Authentication` <br/> |
| `FQDN of new domain` <br/> | `Verified` <br/> | `Managed` <br/> |
   
## <a name="see-also"></a>См. также

#### 

[Справка для партнеров](https://go.microsoft.com/fwlink/p/?LinkID=533477)

