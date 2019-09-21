---
title: Пределы ресурсов для Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
description: Сводка. сведения об ограничении ресурсов для различных приложений в Office 365.
ms.openlocfilehash: ece25deece5a0f2eec7ab0295a2af68f47e1c50c
ms.sourcegitcommit: 55a046bdf49bf7c62ab74da73be1fd1cf6f0ad86
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/20/2019
ms.locfileid: "37067757"
---
# <a name="resource-limits"></a>Ограничения ресурсов

Ограничения ресурсов применяются с помощью квот (ограничений) и регулирования. Azure Active Directory и отдельные службы Office 365 используют оба. При добавлении новых возможностей предельные значения задаются для конкретных служб и изменяются с течением времени. Сведения о текущих пределах для различных служб представлены в следующих разделах:
- [Ограничения и ограничения для службы Azure Active Directory](https://msdn.microsoft.com/en-us/library/azure/dn764971.aspx)
- [Ограничения Exchange Online](https://technet.microsoft.com/en-us/library/exchange-online-limits.aspx)
- [Ограничения Exchange Online Protection](https://technet.microsoft.com/en-us/library/exchange-online-protection-limits.aspx)
- [Границы и ограничения программного обеспечения SharePoint Online](https://support.office.com/article/SharePoint-Online-software-boundaries-and-limits-8F34FF47-B749-408B-ABC0-B605E1F6D498)
- [Пределы Skype для бизнеса](https://technet.microsoft.com/en-us/library/skype-for-business-online-limits.aspx)
- [API REST для REST и пределы скорости](https://developer.yammer.com/docs/rest-api-rate-limits)
- [Предельные значения для размера файлов в Sway](https://support.office.com/article/File-size-limits-in-Sway-4db21bc6-b42b-499f-9272-66e089db109f)

В дополнение к этим ограничениям в Azure Active Directory и Office 365 используются несколько механизмов регулирования. Регулирование в службе особенно важно, так как сетевые ресурсы в центрах обработки данных корпорации Майкрософт оптимизированы для широкого набора клиентов, использующих эти службы. Механизмы регулирования включают:
- Функция регулирования на уровне пользователей Azure Active Directory и Office 365, которая ограничивает количество транзакций или одновременных вызовов (в соответствии со сценарием или кодом), которые могут выполняться одним пользователем.
- Политика регулирования PowerShell по умолчанию назначается каждому клиенту при создании клиента. Эти параметры влияют на другие элементы, например максимальное количество одновременных сеансов PowerShell, которые могут быть открыты одним администратором.
- У каждого клиента Exchange Online есть политика веб-служб Exchange по умолчанию (EWS), которая настроена на выполнение клиентских операций EWS, и регулирование, которое применяется ко всем клиентам Outlook.
