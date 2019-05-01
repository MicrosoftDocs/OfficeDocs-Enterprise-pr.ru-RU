---
title: Добавление домена к аренде клиента с помощью Windows PowerShell для партнеров службы разрешений делегированного доступа (DAP)
ms.author: chrfox
author: chrfox
manager: laurawi
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-subscription-management
ms.custom: ''
ms.assetid: f49b4d24-9aa0-48a6-95dd-6bae9cf53d2c
description: Сводка. Узнайте, как использовать Windows PowerShell для Office 365, чтобы добавить альтернативное доменное имя к существующему пользовательскому клиенту.
ms.openlocfilehash: 85cddd28b72a3b03e9157a28c3fd1dc101a167e0
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/30/2019
ms.locfileid: "33492073"
---
# <a name="add-a-domain-to-a-client-tenancy-with-windows-powershell-for-delegated-access-permission-dap-partners"></a><span data-ttu-id="eb6f6-103">Добавление домена к аренде клиента с помощью Windows PowerShell для партнеров службы разрешений делегированного доступа (DAP)</span><span class="sxs-lookup"><span data-stu-id="eb6f6-103">Add a domain to a client tenancy with Windows PowerShell for Delegated Access Permission (DAP) partners</span></span>

 <span data-ttu-id="eb6f6-104">**Сводка.** Добавьте альтернативное доменное имя к существующему клиенту, используя Windows PowerShell для Office 365.</span><span class="sxs-lookup"><span data-stu-id="eb6f6-104">**Summary:** Use Windows PowerShell for Office 365 to add an alternate domain name to an existing customer tenant.</span></span>
  
<span data-ttu-id="eb6f6-105">Вы можете создавать и связывать новые домены со своим пользовательским клиентом с помощью Windows PowerShell для Office 365 быстрее, чем с помощью Центра администрирования Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="eb6f6-105">You can create and associate new domains with your customer's tenancy with Windows PowerShell for Office 365 faster than using the Microsoft 365 admin center.</span></span>
  
<span data-ttu-id="eb6f6-106">Партнеры по делегированным правам доступа (DAP)  партнеры по синдикации и поставщики облачных решений (CSP).</span><span class="sxs-lookup"><span data-stu-id="eb6f6-106">Delegated Access Permission (DAP) partners are Syndication and Cloud Solution Providers (CSP) Partners.</span></span> <span data-ttu-id="eb6f6-107">Они часто бывают поставщиками сети или телекоммуникационных услуг в других компаниях.</span><span class="sxs-lookup"><span data-stu-id="eb6f6-107">They are frequently network or telecom providers to other companies.</span></span> <span data-ttu-id="eb6f6-108">Они внесли подписки на Office 365 в пакет своих услуг.</span><span class="sxs-lookup"><span data-stu-id="eb6f6-108">They bundle Office 365 subscriptions into their service offerings to their customers.</span></span> <span data-ttu-id="eb6f6-109">Продавая подписки на Office 365, они автоматически получают разрешения на администрирование от чьего-либо имени (AOBO) для области клиентов пользователя, что позволяет им администрировать эти области и создавать отчеты.</span><span class="sxs-lookup"><span data-stu-id="eb6f6-109">When they sell an Office 365 subscription, they are automatically granted Administer On Behalf Of (AOBO) permissions to the customer tenancies so they can administer and report on the customer tenancies.</span></span>
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="eb6f6-110">Что нужно знать перед началом работы?</span><span class="sxs-lookup"><span data-stu-id="eb6f6-110">What do you need to know before you begin?</span></span>

<span data-ttu-id="eb6f6-111">UNRESOLVED_TOKEN_VAL(GENL_O365_PowerShell_BeforeYouBegin)</span><span class="sxs-lookup"><span data-stu-id="eb6f6-111">UNRESOLVED_TOKEN_VAL(GENL_O365_PowerShell_BeforeYouBegin)</span></span>
  
<span data-ttu-id="eb6f6-112">Кроме того, понадобятся указанные ниже сведения.</span><span class="sxs-lookup"><span data-stu-id="eb6f6-112">You also need the following information:</span></span>
  
- <span data-ttu-id="eb6f6-113">Необходимо полное доменное имя (FQDN), которое  требуется вашему клиенту.</span><span class="sxs-lookup"><span data-stu-id="eb6f6-113">You need the fully qualified domain name (FQDN) that your customer wants.</span></span>
    
- <span data-ttu-id="eb6f6-114">Вам необходим идентификатор **TenantId** пользователя.</span><span class="sxs-lookup"><span data-stu-id="eb6f6-114">You need the customer's **TenantId**.</span></span>
    
- <span data-ttu-id="eb6f6-p102">Полное доменное имя должно быть зарегистрировано у регистратора служб доменных имен Интернета (DNS), например GoDaddy. Дополнительные сведения о том, как публично зарегистрировать доменное имя, см. в статье [Приобретение доменного имени](https://go.microsoft.com/fwlink/p/?LinkId=532541).</span><span class="sxs-lookup"><span data-stu-id="eb6f6-p102">The FQDN must be registered with an Internet domain name service (DNS) registrar, such as GoDaddy. For more information on how to publically register a domain name, see [How to buy a domain name](https://go.microsoft.com/fwlink/p/?LinkId=532541).</span></span>
    
- <span data-ttu-id="eb6f6-p103">Вам необходимо знать, как добавить запись типа TXT в зарегистрированную зону DNS для своего регистратора DNS. Дополнительные сведения о добавлении записи типа TXT см. в статье [Создание записи DNS для Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532542). Если эти действия вам не помогут, потребуется найти инструкции, касающиеся вашего регистратора DNS.</span><span class="sxs-lookup"><span data-stu-id="eb6f6-p103">You need to know how to add a TXT record to the registered DNS zone for your DNS registrar. For more information on how to add a TXT record, see [Create DNS records at any DNS hosting provider for Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532542). If those procedures don't work for you, you will need to find the procedures for your DNS registrar.</span></span>
    
## <a name="create-domains"></a><span data-ttu-id="eb6f6-120">Создание доменов</span><span class="sxs-lookup"><span data-stu-id="eb6f6-120">Create domains</span></span>

 <span data-ttu-id="eb6f6-p104">Ваши клиенты, скорее всего, попросят вас создать дополнительные домены, чтобы связать их с со своим клиентом, поскольку они не хотят, чтобы стандартный домен<домен>.onmicrosoft.comбыл основным, который представляет лицо их организации всему миру. Это руководство поможет вам создать новый домен, связанный с пользовательским клиентом.</span><span class="sxs-lookup"><span data-stu-id="eb6f6-p104">Your customers will likely ask you to create additional domains to associate with their tenancy because they don't want the default <domain>.onmicrosoft.com domain to be the primary one that represents their corporate identities to the world. This procedure walks you through creating a new domain associated with your customer's tenancy.</span></span>
  
> [!NOTE]
> <span data-ttu-id="eb6f6-p105">Чтобы можно было выполнить некоторые из этих операций, партнерской учетной записи администратора, которая используется для входа, нужно задать значение **Полное администрирование** для параметра **Назначение прав администратора на компании, которым предоставляется поддержка**. Этот параметр отображается в разделе информации об учетной записи администратора в Центре администрирования Office 365. Дополнительные сведения об управлении партнерскими ролями администратора см. в статье [Партнеры: предложение услуг делегированного администрирования](https://go.microsoft.com/fwlink/p/?LinkId=532435).</span><span class="sxs-lookup"><span data-stu-id="eb6f6-p105">To perform some of these operations, the partner administrator account you sign in with must be set to **Full administration** for the **Assign administrative access to companies you support** setting found in the details of the admin account in the Office 365 admin center. For more information on managing partner administrator roles, see[Partners: Offer delegated administration](https://go.microsoft.com/fwlink/p/?LinkId=532435).</span></span> 
  
### <a name="create-the-domain-in-azure-active-directory"></a><span data-ttu-id="eb6f6-125">Создание домена в Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="eb6f6-125">Create the domain in Azure Active Directory</span></span>

<span data-ttu-id="eb6f6-126">Эта команда создает домен в Azure Active Directory, но не связывает его с публично зарегистрированным доменом.</span><span class="sxs-lookup"><span data-stu-id="eb6f6-126">This command creates the domain in Azure Active Directory but does not associate it with the publicly registered domain.</span></span> <span data-ttu-id="eb6f6-127">Это происходит после того, как вы докажете службе Microsoft Office 365 для предприятий, что вам принадлежит публично зарегистрированный домен.</span><span class="sxs-lookup"><span data-stu-id="eb6f6-127">That comes when you prove that you own the publicly registered domain to Microsoft Office 365 for enterprises.</span></span>
  
```
New-MsolDomain -TenantId <customer TenantId> -Name <FQDN of new domain>
```

### <a name="get-the-data-for-the-dns-txt-verification-record"></a><span data-ttu-id="eb6f6-128">Получение данных для записи TXT проверки DNS</span><span class="sxs-lookup"><span data-stu-id="eb6f6-128">Get the data for the DNS TXT verification record</span></span>

 <span data-ttu-id="eb6f6-p107">Office 365 создаст необходимые вам данные, которые нужно поместить в запись типа TXT для проверки DNS. Чтобы получить эти данные, выполните указанную ниже команду.</span><span class="sxs-lookup"><span data-stu-id="eb6f6-p107">Office 365 will generate the specific data that you need to place into the DNS TXT verification record. To get the data, run this command.</span></span>
  
```
Get-MsolDomainVerificationDNS -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

<span data-ttu-id="eb6f6-131">Выходные данные будут иметь следующий вид:</span><span class="sxs-lookup"><span data-stu-id="eb6f6-131">This will give you output like:</span></span>
  
 `Label: domainname.com`
  
 `Text: MS=ms########`
  
 `Ttl: 3600`
  
> [!NOTE]
> <span data-ttu-id="eb6f6-132">Этот текст потребуется для создания записи TXT в публично зарегистрированной зоне DNS.</span><span class="sxs-lookup"><span data-stu-id="eb6f6-132">You will need this text to create the TXT record in the publicly registered DNS zone.</span></span> <span data-ttu-id="eb6f6-133">Обязательно скопируйте и сохраните его.</span><span class="sxs-lookup"><span data-stu-id="eb6f6-133">Be sure to copy and save it.</span></span> 
  
### <a name="add-a-txt-record-to-the-publically-registered-dns-zone"></a><span data-ttu-id="eb6f6-134">Добавление записи TXT в публично зарегистрированную зону DNS</span><span class="sxs-lookup"><span data-stu-id="eb6f6-134">Add a TXT record to the publically registered DNS zone</span></span>

<span data-ttu-id="eb6f6-135">Прежде чем Office 365 начнет принимать трафик, направленный на публично зарегистрированное доменное имя, потребуется доказать, что этот домен принадлежит вам и у вас есть соответствующие разрешения администратора.</span><span class="sxs-lookup"><span data-stu-id="eb6f6-135">Before Office 365 will start accepting traffic that is directed to the publicly registered domain name, you must prove that you own and have administrator permissions to the domain.</span></span> <span data-ttu-id="eb6f6-136">Для этого нужно создать для домена запись типа TXT.</span><span class="sxs-lookup"><span data-stu-id="eb6f6-136">You prove you own the domain by creating a TXT record in the domain.</span></span> <span data-ttu-id="eb6f6-137">Такая запись не выполняет никаких действий в домене, и ее можно удалить, когда ваше владение доменом будет подтверждено.</span><span class="sxs-lookup"><span data-stu-id="eb6f6-137">A TXT record doesn't do anything in your domain, and it can be deleted after your ownership of the domain is established.</span></span> <span data-ttu-id="eb6f6-138">Чтобы создать запись типа TXT, следуйте указаниям в статье [Создание записи DNS для Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532542).</span><span class="sxs-lookup"><span data-stu-id="eb6f6-138">To create the TXT records, follow the procedures at [Create DNS records at any DNS hosting provider for Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532542).</span></span> <span data-ttu-id="eb6f6-139">Если эти действия вам не помогут, потребуется найти процедуры для своего регистратора DNS.</span><span class="sxs-lookup"><span data-stu-id="eb6f6-139">If those procedures don't work for you , you need to find the procedures for your DNS registrar.</span></span>
  
<span data-ttu-id="eb6f6-p110">Убедитесь, что запись TXT создана успешно, с помощью команды nslookup. Используйте следующий синтаксис.</span><span class="sxs-lookup"><span data-stu-id="eb6f6-p110">Confirm the successful creation of the TXT record via nslookup. Follow this syntax.</span></span>
  
```
nslookup -type=TXT <FQDN of registered domain>
```

<span data-ttu-id="eb6f6-142">Выходные данные будут иметь следующий вид:</span><span class="sxs-lookup"><span data-stu-id="eb6f6-142">This will give you output like:</span></span>
  
 `Non-authoritative answer:`
  
 `FQDN of the registered domain`
  
 `text=MS=ms########`
  
### <a name="validate-domain-ownership-in-office-365"></a><span data-ttu-id="eb6f6-143">Проверка владения доменом в Office 365</span><span class="sxs-lookup"><span data-stu-id="eb6f6-143">Validate domain ownership in Office 365</span></span>

<span data-ttu-id="eb6f6-p111">Напоследок необходимо доказать службе Office 365, что вам принадлежит публично зарегистрированный домен. После этого Office 365 начнет принимать трафик, направленный на новое доменное имя. Чтобы завершить процесс создания и регистрации домена, выполните следующую команду.</span><span class="sxs-lookup"><span data-stu-id="eb6f6-p111">In this last step, you validate to Office 365 that you own the publically registered domain. After this step, Office 365 will begin accepting traffic routed to the new domain name. To complete the domain creation and registration process, run this command.</span></span> 
  
```
Confirm-MsolDomain -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

<span data-ttu-id="eb6f6-147">Эта команда не возвращает выходных данных, поэтому для проверки выполните следующую команду.</span><span class="sxs-lookup"><span data-stu-id="eb6f6-147">This command won't return any output, so to confirm that this worked, run this command.</span></span>
  
```
Get-MsolDomain -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

<span data-ttu-id="eb6f6-148">Выходные данные имеют следующий вид:</span><span class="sxs-lookup"><span data-stu-id="eb6f6-148">This will return something like this</span></span>
  
||||
|:-----|:-----|:-----|
| `Name` <br/> | `Status` <br/> | `Authentication` <br/> |
| `FQDN of new domain` <br/> | `Verified` <br/> | `Managed` <br/> |
   
## <a name="see-also"></a><span data-ttu-id="eb6f6-149">См. также</span><span class="sxs-lookup"><span data-stu-id="eb6f6-149">See also</span></span>

#### 

[<span data-ttu-id="eb6f6-150">Справка для партнеров</span><span class="sxs-lookup"><span data-stu-id="eb6f6-150">Help for partners</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=533477)

