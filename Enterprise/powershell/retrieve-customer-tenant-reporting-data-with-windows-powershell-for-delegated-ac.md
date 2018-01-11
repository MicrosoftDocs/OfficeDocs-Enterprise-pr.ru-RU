---
title: "Получение отчетных данных пользовательских клиентов с помощью Windows PowerShell для партнеров службы разрешений делегированного доступа (DAP)"
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: 
ms.assetid: 893e5275-30b3-433f-8ecd-644f78f513e2
description: "Сводка. Узнайте, как использовать удаленный сеанс Windows PowerShell для Microsoft Exchange Online, чтобы получать отчеты от отдельных пользовательских клиентов."
ms.openlocfilehash: d764f34b89ee55fd7015f01c0c48446fc73a6ac0
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/11/2018
---
# <a name="retrieve-customer-tenant-reporting-data-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a>Получение отчетных данных пользовательских клиентов с помощью Windows PowerShell для партнеров службы разрешений делегированного доступа (DAP)

 **Сводка.** Получайте отчеты от отдельных клиентов, используя удаленный сеанс Windows PowerShell для Microsoft Exchange Online.
  
Партнеры по синдикации и поставщики облачных решений (CSP) может получать доступ к данным, составляющим отчеты пользовательских клиентов, непосредственно через удаленный сеанс Windows PowerShell для Exchange Online PowerShell. Это позволяет партнерам собирать и сохранять данные отчетов, а затем выполнять с ними другие операции. После открытия удаленного подключения получение данных отчетов о пользовательском клиенте идентично запуску любого командлета для пользовательского клиента.
  
В этой статье мы воспользуемся удаленным сеансом Windows PowerShell для Exchange Online, чтобы подключиться к одному пользовательскому клиенту и получить отчет. По умолчанию Windows PowerShell не поддерживает сбор отчетных данных из нескольких пользовательских клиентов. Отчеты, полученные с помощью этой процедуре, предназначены только для  _DelegatedOrg_, к которой выполняется подключение.
  
Если вам нужно получить один отчет для всех пользовательских клиентов, вы можете найти соответствующий пример сценария в статье [Сбор отчетных данных о пользователях с помощью Windows PowerShell для партнеров службы разрешений делегированного доступа (DAP)](aggregate-customer-reporting-data-via-windows-powershell-for-delegated-access-pe.md).
  
## <a name="before-you-begin"></a>Перед началом работы

- Для подключения к клиенту Exchange Online необходимо использовать удаленный сеанс Windows PowerShell. Указания см. в статье [Подключение к клиентам Exchange Online с помощью удаленного сеанса Windows PowerShell для партнеров службы разрешений делегированного доступа (DAP)](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)
    
## <a name="run-the-get-stalemailboxreport-sample"></a>Запуск примера Get-StaleMailboxReport

Открыв удаленный сеанс с Exchange Online, выполните эту команду, чтобы получить **Get-StaleMailboxReport** для диапазона дат с 25.03.2015 по 31.03.2015.
  
```
Get-StaleMailboxReport -StartDate 03/25/2015 -EndDate 03/31/2015
```

Вам доступно много других командлетов для создания отчетов в Exchange Online, Lync Online и SharePoint Online, а также для трассировки сообщений. Дополнительные сведения о доступных командлетах создания отчетов и веб-службе отчетов Office 365 см. в статьях из следующего раздела.
  
## <a name="see-also"></a>См. также

#### 

[Веб-служба отчетов Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532777)
  
[Командлеты отчетов в Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=526430)
  
[Справка для партнеров](https://go.microsoft.com/fwlink/p/?LinkID=533477)

