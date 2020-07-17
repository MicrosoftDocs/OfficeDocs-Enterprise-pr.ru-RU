---
title: Получение отчетных данных пользовательских клиентов с помощью Windows PowerShell для партнеров службы разрешений делегированного доступа (DAP)
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: 893e5275-30b3-433f-8ecd-644f78f513e2
description: Сводка. Узнайте, как использовать удаленный сеанс Windows PowerShell для Microsoft Exchange Online, чтобы получать отчеты от отдельных пользовательских клиентов.
ms.openlocfilehash: d4b8d931b6b8ea8c7b8467dd70326e1b0fbfc3d5
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998628"
---
# <a name="retrieve-customer-tenant-reporting-data-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a><span data-ttu-id="ecab3-103">Получение отчетных данных пользовательских клиентов с помощью Windows PowerShell для партнеров службы разрешений делегированного доступа (DAP)</span><span class="sxs-lookup"><span data-stu-id="ecab3-103">Retrieve customer tenant reporting data with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>

<span data-ttu-id="ecab3-104">Используйте удаленную оболочку Windows PowerShell для Microsoft Exchange Online, чтобы получать отчеты от отдельных клиентских клиентов.</span><span class="sxs-lookup"><span data-stu-id="ecab3-104">Use remote Windows PowerShell for Microsoft Exchange Online to retrieve reports from individual customer tenants.</span></span>
  
<span data-ttu-id="ecab3-p101">Партнеры по синдикации и поставщики облачных решений (CSP) может получать доступ к данным, составляющим отчеты пользовательских клиентов, непосредственно через удаленный сеанс Windows PowerShell для Exchange Online PowerShell. Это позволяет партнерам собирать и сохранять данные отчетов, а затем выполнять с ними другие операции. После открытия удаленного подключения получение данных отчетов о пользовательском клиенте идентично запуску любого командлета для пользовательского клиента.</span><span class="sxs-lookup"><span data-stu-id="ecab3-p101">Syndication and Cloud Solution Provider (CSP) partners can access the data that makes up customer tenant reports directly via remoteWindows PowerShell for Exchange Online PowerShell. This lets partners collect and save the reporting data and then perform other operations on it. After you open a remote connection, retrieving reporting data about a customer tenancy is identical to running any cmdlet against a customer tenancy.</span></span>
  
<span data-ttu-id="ecab3-p102">В этой статье мы воспользуемся удаленным сеансом Windows PowerShell для Exchange Online, чтобы подключиться к одному пользовательскому клиенту и получить отчет. По умолчанию Windows PowerShell не поддерживает сбор отчетных данных из нескольких пользовательских клиентов. Отчеты, полученные с помощью этой процедуре, предназначены только для  _DelegatedOrg_, к которой выполняется подключение.</span><span class="sxs-lookup"><span data-stu-id="ecab3-p102">In this article, you use remoteWindows PowerShell for Exchange Online to connect to a single customer tenancy and retrieve a report. By default, Windows PowerShell does not support aggregating reporting data from multiple customer tenancies. The reports you retrieve with this procedure are only for the  _DelegatedOrg_ that you connect to.</span></span>
  
 
## <a name="before-you-begin"></a><span data-ttu-id="ecab3-111">До начала работы</span><span class="sxs-lookup"><span data-stu-id="ecab3-111">Before you begin</span></span>

- <span data-ttu-id="ecab3-p103">Для подключения к клиенту Exchange Online необходимо использовать удаленный сеанс Windows PowerShell. Указания см. в статье [Подключение к клиентам Exchange Online с помощью удаленного сеанса Windows PowerShell для партнеров службы разрешений делегированного доступа (DAP)](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)</span><span class="sxs-lookup"><span data-stu-id="ecab3-p103">You need to connect to your Exchange Online tenant by using remote Windows PowerShell. For instructions, see [Connect to Exchange Online tenants with remote Windows PowerShell for Delegated Access Permissions (DAP) partners](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)</span></span>
    
## <a name="run-the-get-stalemailboxreport-sample"></a><span data-ttu-id="ecab3-114">Запуск примера Get-StaleMailboxReport</span><span class="sxs-lookup"><span data-stu-id="ecab3-114">Run the Get-StaleMailboxReport sample</span></span>

<span data-ttu-id="ecab3-115">Открыв удаленный сеанс с Exchange Online, выполните эту команду, чтобы получить **Get-StaleMailboxReport** для диапазона дат с 25.03.2015 по 31.03.2015.</span><span class="sxs-lookup"><span data-stu-id="ecab3-115">After you have opened a remote session to Exchange Online, run this command to retrieve the **Get-StaleMailboxReport** for the date range 03/25/2015 through 03/31/2015.</span></span>
  
```
Get-StaleMailboxReport -StartDate 03/25/2015 -EndDate 03/31/2015
```

<span data-ttu-id="ecab3-p104">Вам доступно много других командлетов для создания отчетов в Exchange Online, Lync Online и SharePoint Online, а также для трассировки сообщений. Дополнительные сведения о доступных командлетах создания отчетов и веб-службе отчетов Office 365 см. в статьях из следующего раздела.</span><span class="sxs-lookup"><span data-stu-id="ecab3-p104">There are many other reporting cmdlets available for Exchange Online, Lync Online, and SharePoint Online as well as others for message tracing that you can use. To find out more about the available reporting cmdlets and the Office 365 Reporting web service, see the topics in the following section.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="ecab3-118">См. также</span><span class="sxs-lookup"><span data-stu-id="ecab3-118">See also</span></span>

#### 

[<span data-ttu-id="ecab3-119">Веб-служба отчетов Office 365</span><span class="sxs-lookup"><span data-stu-id="ecab3-119">Office 365 Reporting web service</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532777)
  
[<span data-ttu-id="ecab3-120">Командлеты отчетов в Exchange Online</span><span class="sxs-lookup"><span data-stu-id="ecab3-120">Reporting cmdlets in Exchange Online</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=526430)
  
[<span data-ttu-id="ecab3-121">Справка для партнеров</span><span class="sxs-lookup"><span data-stu-id="ecab3-121">Help for partners</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=533477)

