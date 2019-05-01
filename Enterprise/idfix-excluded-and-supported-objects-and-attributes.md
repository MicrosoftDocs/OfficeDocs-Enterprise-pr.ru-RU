---
title: Исключаемые и поддерживаемые объекты и атрибуты IdFix
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2016
ms.audience: Admin
ms.topic: reference
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
ms.assetid: cc453ae5-fa9b-4836-b0ce-c7e824b1e36d
description: Список атрибутов, исключаемых и поддерживаемых средством IdFix.
ms.openlocfilehash: d6b7aac023e9fe96b8308483322e718937ab1355
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487185"
---
# <a name="idfix-excluded-and-supported-objects-and-attributes"></a>Исключаемые и поддерживаемые объекты и атрибуты IdFix
Существует два набора правил, поддерживаемых IdFix; Поддержка нескольких клиентов и выделенного/ITAR. В настоящее время два набора правил исключают одни и те же объекты, атрибуты и значения атрибутов из поиска. Это может измениться в будущих выпусках.
  
## <a name="multi-tenant-and-dedicated-error-exclusions-used-by-idfix"></a>Несколько клиентов и выделенные исключения ошибок, используемые IdFix
В этом разделе перечислены объекты, атрибуты и значения, которые IdFix исключает из поиска в каталоге. Звездочка (\*) — это подстановочный знак, который можно заменить на другие символы.
  
### <a name="objects-attributes-and-values-excluded-during-an-idfix-search"></a>Объекты, атрибуты и значения, исключенные во время поиска IdFix

|**Исключения**|**Пример**|
|:-----|:-----|
|Админи\* |Администратор |
|КАС_ {\*  |КАС_ {fe35fc98e69e4d08} |
|Дисковерисеарчмаилбокс\*  |Дисковерисеарчмаилбокс  |
|FederatedEmail\* |FederatedEmail. *GUID* |
|Guest\* ||
|Хттпконнектор\*  |Хттпконнектор |
|KRBTGT\* |MS DS: KrbTgt – Link |
|IUSR\* |IUSR_ *имя_компьютера* |
|IWAM\*  |IWAM_ *MachineName* |
|MSOL\* |МСОЛ_АД_СИНК |
|поддержки\* ||
|SystemMailbox\* |SystemMailbox { *GUID* }|
|Ввиоадмини\*  ||
|\*$ ||
|distinguishedName содержит "\0ACNF:"|"\0ACNF: *GUID* " |
|Объект содержит атрибут Искритикалсистемобжект |Ознакомьтесь с [атрибутОм искритикалсистемобжект](https://go.microsoft.com/fwlink/p/?LinkId=401169). |
   
## <a name="multi-tenant-and-dedicated-objects-and-attributes-checked-by-idfix"></a>Поддержка нескольких клиентов и выделенных объектов и атрибутов, проверенных с помощью IdFix
Атрибуты, которые проверяются на наличие ошибок с помощью IdFix, описаны в разделе "объект каталога и подготовка атрибута" в разделе [Подготовка атрибутов каталога для синхронизации с Office 365 с помощью средства IdFix](prepare-directory-attributes-for-synch-with-idfix.md).
  

