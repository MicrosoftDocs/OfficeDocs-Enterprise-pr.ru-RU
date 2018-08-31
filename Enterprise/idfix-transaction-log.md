---
title: Журнал транзакций Office 365 IdFix
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: reference
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
ms.assetid: d58b7d45-7947-4193-9456-82ba76f42d89
description: Пример и описание соглашение об именовании и уровень журнала по умолчанию в журнал транзакций Office 365 IdFix.
ms.openlocfilehash: 016318c7e771ec6c5f90336e11c5dd011144d12e
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542456"
---
# <a name="office-365-idfix-transaction-log"></a>Журнал транзакций Office 365 IdFix

Пример и описание соглашение об именовании и уровень журнала по умолчанию в журнал транзакций Office 365 IdFix.
  
## <a name="idfix-transaction-log-location"></a>Расположение журнала транзакций IdFix

Средство Office 365 IdFix создает новый журнал транзакций каждый раз, нажмите кнопку **Применить** в IdFix и применить изменения к лесу Active Directory. Журнал транзакций сохраняются в ту же папку, где установлен IdFix. По умолчанию эта папка не C:\Deployment Tools\IDFix. Имя файла журнала транзакций используется формат штамп даты и времени, например, Verbose 6-1-2018 6 17 22 PM указывает файл, который был создан на 1 июня 2018 на 6:17:22 PM. подробный уровень ведения журнала. 
  
## <a name="idfix-transaction-log-logging-level"></a>Уровень ведения журнала транзакций IdFix

Слово "verbose" в имени журнала транзакций указывает уровень ведения журнала. В данном случае записывается максимальное количество информации. Данный уровень ведения журнала является уровнем по умолчанию. В текущий момент уровень ведения журнала не изменятся.
  
## <a name="idfix-transaction-log-format"></a>Расположение журнала транзакций IdFix

IdFix записывает результаты каждого действия **UPDATE** в журнал транзакций, как показано в следующем примере:
  
```
5/22/2018 6:36:44 AM Initialized - IdFix version 1.07 - Multi-Tenant
5/22/2018 6:36:47 AM Query AD
5/22/2018 6:36:47 AM FOREST:e2k10.com SERVER:dc1.e2k10.com FILTER:(|(objectCategory=Person)(objectCategory=Group))
5/22/2018 6:36:47 AM Please wait while the LDAP Connection is established.
5/22/2018 6:36:49 AM Query Count: 140  Error Count: 29  Duplicate Check Count: 191
5/22/2018 6:36:49 AM Elapsed Time: AD Query - 00:00:02.3890432
5/22/2018 6:36:49 AM Write split files
5/22/2018 6:36:49 AM Merge split files
5/22/2018 6:36:49 AM Count duplicates
5/22/2018 6:36:49 AM Write filtered duplicate objects
5/22/2018 6:36:49 AM Read filtered duplicate objects
5/22/2018 6:36:49 AM Read error file
5/22/2018 6:36:49 AM Elapsed Time: Duplicate Checks - 00:00:00.0780785
5/22/2018 6:36:49 AM Populating DataGrid
5/22/2018 6:36:50 AM Elapsed Time: Populate DataGridView - 00:00:00.0780785
5/22/2018 6:36:50 AM Query Count: 140  Error Count: 53
5/22/2018 6:37:34 AM Apply Pending
5/22/2018 6:37:34 AM Update: [CN=user000001,OU=e2k10OU1,DC=e2k10,DC=com][user][mailnickname][character][user?^|000001][user000001][EDIT]
5/22/2018 6:37:34 AM Update: [CN=user000008,OU=e2k10OU1,DC=e2k10,DC=com][user][targetAddress][duplicate][smtp:user000008@customer.com][][REMOVE]
5/22/2018 6:37:34 AM COMPLETE
5/22/2018 6:37:40 AM Loading Updates
5/22/2018 6:37:40 AM Action Selection
5/22/2018 6:37:57 AM Apply Pending
5/22/2018 6:37:57 AM Update: [CN=user000001,OU=e2k10OU1,DC=e2k10,DC=com][user][mailnickname][character][user?^|000001][user000001][UNDO]
5/22/2018 6:37:57 AM Update: [CN=user000008,OU=e2k10OU1,DC=e2k10,DC=com][user][targetAddress][duplicate][smtp:user000008@customer.com][][UNDO]
5/22/2018 6:37:57 AM COMPLETE

```