---
title: Журнал транзакций Office 365 IdFix
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: reference
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
ms.assetid: d58b7d45-7947-4193-9456-82ba76f42d89
description: В этом разделе приводится пример и описывается соглашение об именовании и уровень журнала по умолчанию для журнала транзакций Office 365 IdFix.
ms.openlocfilehash: 0c6f2dd64cb406681c0a98099b2a42887ee79c25
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067265"
---
# <a name="office-365-idfix-transaction-log"></a>Журнал транзакций Office 365 IdFix

В этом разделе приводится пример и описывается соглашение об именовании и уровень журнала по умолчанию для журнала транзакций Office 365 IdFix.
  
## <a name="idfix-transaction-log-location"></a>Расположение журнала транзакций IdFix

Средство Office 365 IdFix создает новый журнал транзакций при каждом нажатии кнопки **Применить** в IdFix и применении изменений к лесу Active Directory. Журнал транзакций сохраняется в той же папке, где установлен IdFix. По умолчанию эта папка является К:\деплоймент Тулс\идфикс. В имени файла журнала транзакций используется формат даты и времени, например verbose 6-1-2018 6-17-22 PM указывает файл, который был создан 1 июня 2018 по 6:17:22 PM. Verbose указывает уровень ведения журнала. 
  
## <a name="idfix-transaction-log-logging-level"></a>Уровень ведения журнала транзакций IdFix

Слово Verbose в имени файла журнала транзакций указывает уровень ведения журнала в файле. Verbose означает, что максимальный объем информации записывается в журнал. Это уровень ведения журнала по умолчанию. В настоящее время невозможно изменить уровень ведения журнала.
  
## <a name="idfix-transaction-log-format"></a>Формат журнала транзакций IdFix

IdFix записывает результаты каждого действия **обновления** в журнал транзакций, как показано в следующем примере:
  
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