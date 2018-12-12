---
title: Получение отчетных данных пользовательских клиентов с помощью Windows PowerShell для партнеров службы разрешений делегированного доступа (DAP)
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: 893e5275-30b3-433f-8ecd-644f78f513e2
description: Сводка. Узнайте, как использовать удаленный сеанс Windows PowerShell для Microsoft Exchange Online, чтобы получать отчеты от отдельных пользовательских клиентов.
ms.openlocfilehash: d764f34b89ee55fd7015f01c0c48446fc73a6ac0
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/11/2018
ms.locfileid: "17114668"
---
# <a name="retrieve-customer-tenant-reporting-data-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a><span data-ttu-id="ed090-103">Получение отчетных данных пользовательских клиентов с помощью Windows PowerShell для партнеров службы разрешений делегированного доступа (DAP)</span><span class="sxs-lookup"><span data-stu-id="ed090-103">Retrieve customer tenant reporting data with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>

 <span data-ttu-id="ed090-104">**Сводка.** Получайте отчеты от отдельных клиентов, используя удаленный сеанс Windows PowerShell для Microsoft Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="ed090-104">**Summary:** Use remoteWindows PowerShell for Microsoft Exchange Online to retrieve reports from individual customer tenants.</span></span>
  
<span data-ttu-id="ed090-p101">Партнеры по синдикации и поставщики облачных решений (CSP) может получать доступ к данным, составляющим отчеты пользовательских клиентов, непосредственно через удаленный сеанс Windows PowerShell для Exchange Online PowerShell. Это позволяет партнерам собирать и сохранять данные отчетов, а затем выполнять с ними другие операции. После открытия удаленного подключения получение данных отчетов о пользовательском клиенте идентично запуску любого командлета для пользовательского клиента.</span><span class="sxs-lookup"><span data-stu-id="ed090-p101">Syndication and Cloud Solution Provider (CSP) partners can access the data that makes up customer tenant reports directly via remoteWindows PowerShell for Exchange Online PowerShell. This lets partners collect and save the reporting data and then perform other operations on it. After you open a remote connection, retrieving reporting data about a customer tenancy is identical to running any cmdlet against a customer tenancy.</span></span>
  
<span data-ttu-id="ed090-p102">В этой статье мы воспользуемся удаленным сеансом Windows PowerShell для Exchange Online, чтобы подключиться к одному пользовательскому клиенту и получить отчет. По умолчанию Windows PowerShell не поддерживает сбор отчетных данных из нескольких пользовательских клиентов. Отчеты, полученные с помощью этой процедуре, предназначены только для  _DelegatedOrg_, к которой выполняется подключение.</span><span class="sxs-lookup"><span data-stu-id="ed090-p102">In this article, you use remoteWindows PowerShell for Exchange Online to connect to a single customer tenancy and retrieve a report. By default, Windows PowerShell does not support aggregating reporting data from multiple customer tenancies. The reports you retrieve with this procedure are only for the  _DelegatedOrg_ that you connect to.</span></span>
  
<span data-ttu-id="ed090-111">Если вам нужно получить один отчет для всех пользовательских клиентов, вы можете найти соответствующий пример сценария в статье [Сбор отчетных данных о пользователях с помощью Windows PowerShell для партнеров службы разрешений делегированного доступа (DAP)](aggregate-customer-reporting-data-via-windows-powershell-for-delegated-access-pe.md).</span><span class="sxs-lookup"><span data-stu-id="ed090-111">If you want to retrieve a single report for all your customer tenancies, a sample script to do this can be found in [Aggregate customer reporting data via Windows PowerShell for Delegated Access Permission (DAP) partners](aggregate-customer-reporting-data-via-windows-powershell-for-delegated-access-pe.md) .</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="ed090-112">Перед началом работы</span><span class="sxs-lookup"><span data-stu-id="ed090-112">Before you begin</span></span>

- <span data-ttu-id="ed090-p103">Для подключения к клиенту Exchange Online необходимо использовать удаленный сеанс Windows PowerShell. Указания см. в статье [Подключение к клиентам Exchange Online с помощью удаленного сеанса Windows PowerShell для партнеров службы разрешений делегированного доступа (DAP)](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)</span><span class="sxs-lookup"><span data-stu-id="ed090-p103">You need to connect to your Exchange Online tenant by using remote Windows PowerShell. For instructions, see [Connect to Exchange Online tenants with remote Windows PowerShell for Delegated Access Permissions (DAP) partners](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)</span></span>
    
## <a name="run-the-get-stalemailboxreport-sample"></a><span data-ttu-id="ed090-115">Запуск примера Get-StaleMailboxReport</span><span class="sxs-lookup"><span data-stu-id="ed090-115">Run the Get-StaleMailboxReport sample</span></span>

<span data-ttu-id="ed090-116">Открыв удаленный сеанс с Exchange Online, выполните эту команду, чтобы получить **Get-StaleMailboxReport** для диапазона дат с 25.03.2015 по 31.03.2015.</span><span class="sxs-lookup"><span data-stu-id="ed090-116">After you have opened a remote session to Exchange Online, run this command to retrieve the **Get-StaleMailboxReport** for the date range 03/25/2015 through 03/31/2015.</span></span>
  
```
Get-StaleMailboxReport -StartDate 03/25/2015 -EndDate 03/31/2015
```

<span data-ttu-id="ed090-p104">Вам доступно много других командлетов для создания отчетов в Exchange Online, Lync Online и SharePoint Online, а также для трассировки сообщений. Дополнительные сведения о доступных командлетах создания отчетов и веб-службе отчетов Office 365 см. в статьях из следующего раздела.</span><span class="sxs-lookup"><span data-stu-id="ed090-p104">There are many other reporting cmdlets available for Exchange Online, Lync Online, and SharePoint Online as well as others for message tracing that you can use. To find out more about the available reporting cmdlets and the Office 365 Reporting web service, see the topics in the following section.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="ed090-119">См. также</span><span class="sxs-lookup"><span data-stu-id="ed090-119">See also</span></span>

#### 

[<span data-ttu-id="ed090-120">Веб-служба отчетов Office 365</span><span class="sxs-lookup"><span data-stu-id="ed090-120">Office 365 Reporting web service</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532777)
  
[<span data-ttu-id="ed090-121">Командлеты отчетов в Exchange Online</span><span class="sxs-lookup"><span data-stu-id="ed090-121">Reporting cmdlets in Exchange Online</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=526430)
  
[<span data-ttu-id="ed090-122">Справка для партнеров</span><span class="sxs-lookup"><span data-stu-id="ed090-122">Help for partners</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=533477)

