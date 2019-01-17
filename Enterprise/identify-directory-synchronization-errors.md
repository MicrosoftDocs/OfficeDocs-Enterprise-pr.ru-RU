---
title: Просмотр ошибок синхронизации службы каталогов в Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- GPA150
ms.assetid: b4fc07a5-97ea-4ca6-9692-108acab74067
description: Узнайте, как для просмотра ошибок синхронизации службы каталогов в центре администрирования Office 365.
ms.openlocfilehash: 8beeeebbb24936abd7c93f4c04c0fa4e27c85c12
ms.sourcegitcommit: c5ee713709d76f519cb77de0e12c435d8409f571
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/17/2019
ms.locfileid: "28327341"
---
# <a name="view-directory-synchronization-errors-in-office-365"></a>Просмотр ошибок синхронизации службы каталогов в Office 365

В центре администрирования Office 365 можно просмотреть ошибок синхронизации службы каталогов. Отображаются только ошибки объекта пользователя. Просмотр ошибок с помощью PowerShell, просмотрите [Определение объектов с DirSyncProvisioningErrors](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency).

После просмотра, в разделе [Устранение проблем с синхронизацией каталогов для Office 365](fix-problems-with-directory-synchronization.md) для исправления найденных проблем.
  
## <a name="view-directory-synchronization-errors-in-the-admin-center"></a>Просмотр ошибок синхронизации службы каталогов в центре администрирования

Чтобы просмотреть все ошибки в центре администрирования:
  
1. Войдите в Office 365 с помощью своей рабочей или учебной учетной записи. 
    
2. Перейдите в [Центр администрирования об Office 365](https://support.office.com/article/758befc4-0888-4009-9f14-0d147402fd23).
    
3. На **домашней** странице отображается Плитка **Состояние DirSync** . 
    
    ![Состояние DirSync плиток в предварительной версии центра администрирования](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
4. В разделе Выбор перейдите на страницу **Состояния синхронизации каталогов** в **Состоянии DirSync** . 
    
    В нижней части страницы можно видеть, если имеется DirSync ошибки.
    
    ![На странице состояния синхронизации каталогов можно увидеть при наличии ошибок объект DirSync](media/882094a3-80d3-4aae-b90b-78b27047974c.png)
  
    Выберите, **мы обнаружили ошибки объекта DirSync** переход на подробное представление ошибок синхронизации службы каталогов. 
    
    > [!NOTE]
    > Также можно перейти к странице **DirSync ошибки** , если **мы обнаружили ошибки объекта DirSync** выберите в разделе **состояние DirSync** . 
  
![Страница ошибок DirSync](media/a6e302d4-6be7-4e3a-b4b5-81c5a2c02952.png)
  
5. На странице **ошибок DirSync** выберите любой из списка для отображения области сведений со сведениями об ошибке и советы по исправлению ошибок. 
