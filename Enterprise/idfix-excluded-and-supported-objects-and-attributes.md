---
title: Исключаемые и поддерживаемые объекты и атрибуты IdFix
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: reference
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
- MOE150
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
ms.assetid: cc453ae5-fa9b-4836-b0ce-c7e824b1e36d
description: Список атрибутов, исключаемых и поддерживаемых средством IdFix.
ms.openlocfilehash: da9a59d60b1ae2f1f68803e5a10afba16207fc69
ms.sourcegitcommit: d2a3d6eeeaa07510ee94c2bc675284d893221a95
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/12/2020
ms.locfileid: "44711579"
---
# <a name="idfix-excluded-and-supported-objects-and-attributes"></a>Исключаемые и поддерживаемые объекты и атрибуты IdFix

*Эта статья относится как к Microsoft 365 Enterprise, так и к Office 365 корпоративный.*

Существует два набора правил, поддерживаемых IdFix; Поддержка нескольких клиентов и выделенного/ITAR. В настоящее время два набора правил исключают одни и те же объекты, атрибуты и значения атрибутов из поиска. Это может измениться в будущих выпусках.
  
## <a name="multi-tenant-and-dedicated-error-exclusions-used-by-idfix"></a>Несколько клиентов и выделенные исключения ошибок, используемые IdFix
В этом разделе перечислены объекты, атрибуты и значения, которые IdFix исключает из поиска в каталоге. Звездочка ( \* ) — это подстановочный знак, который можно заменить на другие символы.
  
### <a name="objects-attributes-and-values-excluded-during-an-idfix-search"></a>Объекты, атрибуты и значения, исключенные во время поиска IdFix

|**Исключения**|**Пример**|
|:-----|:-----|
|админи\* |Администратор |
|CAS_ {\*  |CAS_ {fe35fc98e69e4d08} |
|дисковерисеарчмаилбокс\*  |дисковерисеарчмаилбокс  |
|FederatedEmail\* |FederatedEmail. *GUID* |
|Guest\* ||
|хттпконнектор\*  |хттпконнектор |
|KRBTGT\* |MS DS: KrbTgt – Link |
|iusr_\* |iusr_ *MachineName* |
|IWAM\*  |IWAM_ *MachineName* |
|MSOL\* |MSOL_AD_SYNC |
|support_\* ||
|SystemMailbox\* |SystemMailbox { *GUID* }|
|ввиоадмини\*  ||
|\*$ ||
|distinguishedName содержит "\0ACNF:"|"\0ACNF: *GUID* " |
|Объект содержит атрибут Искритикалсистемобжект |Ознакомьтесь с [атрибутом искритикалсистемобжект](https://go.microsoft.com/fwlink/p/?LinkId=401169). |
   
## <a name="multi-tenant-and-dedicated-objects-and-attributes-checked-by-idfix"></a>Поддержка нескольких клиентов и выделенных объектов и атрибутов, проверенных с помощью IdFix
Атрибуты, которые проверяются на наличие ошибок с помощью IdFix, описаны в разделе "объект каталога и подготовка атрибута" в разделе [Prepare Attributes for Synchronization for Synchronization with Microsoft 365 с помощью средства IdFix](prepare-directory-attributes-for-synch-with-idfix.md).
  

