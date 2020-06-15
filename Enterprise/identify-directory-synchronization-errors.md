---
title: Просмотр ошибок синхронизации каталогов в Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- GPA150
ms.assetid: b4fc07a5-97ea-4ca6-9692-108acab74067
description: Сведения о том, как просматривать ошибки синхронизации каталогов в центре администрирования Microsoft 365.
ms.openlocfilehash: d10abc29a08da4352d4c0779698e2062175008b4
ms.sourcegitcommit: d2a3d6eeeaa07510ee94c2bc675284d893221a95
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/12/2020
ms.locfileid: "44711649"
---
# <a name="view-directory-synchronization-errors-in-microsoft-365"></a>Просмотр ошибок синхронизации каталогов в Microsoft 365

Вы можете просматривать ошибки синхронизации каталогов в [центре администрирования Microsoft 365](https://admin.microsoft.com). Отображаются только ошибки объекта пользователя. Просмотреть ошибки с помощью PowerShell можно в разделе [Identify Objects with дирсинкпровисионинжеррорс](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency).

После просмотра ознакомьтесь с разрешениями [проблем с синхронизацией каталогов для Microsoft 365](fix-problems-with-directory-synchronization.md) , чтобы устранить обнаруженные проблемы.
  
## <a name="view-directory-synchronization-errors-in-the-admin-center"></a>Просмотр ошибок синхронизации каталогов в центре администрирования

Чтобы просмотреть ошибки в центре администрирования, выполните следующие действия.
  
1. Войдите в Microsoft 365, используя свою рабочую или учебную учетную запись. 
    
2. Перейдите к разделу [о центре администрирования](https://support.office.com/article/758befc4-0888-4009-9f14-0d147402fd23).
    
3. На **домашней** странице вы увидите плитку **состояния DirSync** . 
    
    ![Плитка "Состояние DirSync" в предварительной версии центра администрирования](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
4. На плитке выберите **состояние DirSync** , чтобы перейти на страницу **состояния синхронизации каталогов** . 
    
    В нижней части страницы можно увидеть, есть ли ошибки DirSync.
    
    ![На странице состояния синхронизации каталогов можно увидеть, есть ли ошибки в объектах DirSync.](media/882094a3-80d3-4aae-b90b-78b27047974c.png)
  
    Нажмите **мы обнаружили ошибки объекта DirSync** , чтобы перейти к подробному представлению ошибок синхронизации службы каталогов. 
    
    > [!NOTE]
    > Вы также можете перейти на страницу **ошибки DirSync** , если вы выберете **ошибки объекта DirSync** в плитке **состояния DirSync** . 
  
![Страница "ошибки DirSync"](media/a6e302d4-6be7-4e3a-b4b5-81c5a2c02952.png)
  
5. На странице " **ошибки DirSync** " выберите любую из указанных ошибок, чтобы отобразить область сведений о сообщении об ошибке, и советы по ее устранению. 
