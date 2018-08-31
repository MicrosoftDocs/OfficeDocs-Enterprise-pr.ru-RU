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
ms.assetid: cc453ae5-fa9b-4836-b0ce-c7e824b1e36d
description: Содержит атрибуты, исключаемые и поддерживаемые инструмент IdFix.
ms.openlocfilehash: de8d57bb8ad9a3097ec9da3ff2a485095a140a42
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542454"
---
# <a name="idfix-excluded-and-supported-objects-and-attributes"></a>Исключаемые и поддерживаемые объекты и атрибуты IdFix
Существует два набора правил, поддерживаемых IdFix, — многопользовательский и выделенный/ITAR. В настоящее время эти два набора правил исключают из поиска одинаковые объекты, атрибуты и значения атрибутов. Это может измениться в последующих выпусках.
  
## <a name="multi-tenant-and-dedicated-error-exclusions-used-by-idfix"></a>Многопользовательские и выделенные ошибочные исключения, используемые IdFix
В этом разделе перечислены объекты, атрибуты и значения, которые IdFix исключает из поиск каталога. Символ звездочки (\*) — это подстановочный знак, который может быть заменен других знаков.
  
### <a name="objects-attributes-and-values-excluded-during-an-idfix-search"></a>Объекты, атрибуты и значения, исключаемые во время поиска по IdFix

|**Исключения**|**Пример**|
|:-----|:-----|
|Уязвимой\* |Администратор |
|CAS_ {\*  |CAS_{fe35fc98e69e4d08} |
|DiscoverySearchMailbox\*  |DiscoverySearchMailbox  |
|FederatedEmail\* |FederatedEmail. *Идентификатор GUID* |
|Гостевая\* ||
|HTTPConnector\*  |HTTPConnector* |
|KRBTGT\* |MS-доменных служб Active Directory KrbTgt ссылки |
|IUSR_\* |IUSR_ *machinename* |
|IWAM\*  |IWAM_ *machinename* |
|msol\* |MSOL_AD_SYNC |
|Support_\* ||
|SystemMailbox\* |Systemmailbox { *GUID* }|
|WWIOadmini\*  ||
|\*$ ||
|Различающееся_имя содержит «\0ACNF:»|«\0ACNF: *идентификатор GUID* " |
|Объект содержит атрибут IsCriticalSystemObject |В разделе [атрибут isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169). |
   
## <a name="multi-tenant-and-dedicated-objects-and-attributes-checked-by-idfix"></a>Многопользовательские и выделенные объекты и атрибуты, проверяемые IdFix
Атрибуты, которые проверяются на наличие ошибок с IdFix, описаны в разделе «каталог подготовки объектов и атрибутов» в [Подготовка атрибутов каталога для синхронизации с Office 365 с помощью инструмента IdFix](prepare-directory-attributes-for-synch-with-idfix.md).
  

