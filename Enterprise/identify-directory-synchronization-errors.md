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
ms.openlocfilehash: 57ca9ce125679931adcca93621474cec9ee9b82f
ms.sourcegitcommit: 3349fdaff646f5f7d92c22565402dfc22c12d2ed
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/22/2020
ms.locfileid: "44842093"
---
# <a name="view-directory-synchronization-errors-in-microsoft-365"></a><span data-ttu-id="82915-103">Просмотр ошибок синхронизации каталогов в Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="82915-103">View directory synchronization errors in Microsoft 365</span></span>

<span data-ttu-id="82915-104">Вы можете просматривать ошибки синхронизации каталогов в центре администрирования Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="82915-104">You can view directory synchronization errors in the Microsoft 365 admin center.</span></span> <span data-ttu-id="82915-105">Отображаются только ошибки объекта пользователя.</span><span class="sxs-lookup"><span data-stu-id="82915-105">Only the User object errors are displayed.</span></span> <span data-ttu-id="82915-106">Чтобы просмотреть ошибки с помощью PowerShell, ознакомьтесь со статьей [Определение объектов с помощью дирсинкпровисионинжеррорс](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency).</span><span class="sxs-lookup"><span data-stu-id="82915-106">To view errors with PowerShell, see [Identify objects with DirSyncProvisioningErrors](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency).</span></span>

## <a name="view-directory-synchronization-errors-in-the-microsoft-365-admin-center"></a><span data-ttu-id="82915-107">Просмотр ошибок синхронизации каталогов в центре администрирования Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="82915-107">View directory synchronization errors in the Microsoft 365 admin center</span></span>

<span data-ttu-id="82915-108">Чтобы просмотреть ошибки в центре администрирования Microsoft 365, выполните указанные ниже действия.</span><span class="sxs-lookup"><span data-stu-id="82915-108">To view any errors in the Microsoft 365 admin center:</span></span>
  
1. <span data-ttu-id="82915-109">Войдите в [центр администрирования Microsoft 365](https://admin.microsoft.com) , используя учетную запись глобального администратора.</span><span class="sxs-lookup"><span data-stu-id="82915-109">Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com) with a global administrator account.</span></span> 
    
2. <span data-ttu-id="82915-110">На **домашней** странице вы увидите карточку **Управление пользователями** .</span><span class="sxs-lookup"><span data-stu-id="82915-110">On the **Home** page, you'll see the **User management** card.</span></span> 
    
    ![Карточка управления пользователями в центре администрирования Microsoft 365](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
3. <span data-ttu-id="82915-112">На карточке выберите **ошибки синхронизации** в **Azure AD Connect** , чтобы просмотреть ошибки на странице " **ошибки синхронизации каталогов** ".</span><span class="sxs-lookup"><span data-stu-id="82915-112">On the card, choose **Sync errors** under **Azure AD Connect** to see the errors on the **Directory sync errors** page.</span></span>   
    
    ![Пример страницы ошибок синхронизации каталогов](media/882094a3-80d3-4aae-b90b-78b27047974c.png)

4. <span data-ttu-id="82915-114">Выберите любую ошибку, чтобы отобразить область сведений со сведениями об ошибке, и советы по ее устранению.</span><span class="sxs-lookup"><span data-stu-id="82915-114">Choose any of the errors to display the details pane with information about the error and tips on how to fix it.</span></span>

   ![Пример сведений об ошибке синхронизации каталогов](media/a6e302d4-6be7-4e3a-b4b5-81c5a2c02952.png)
  
<span data-ttu-id="82915-116">После просмотра ознакомьтесь с разрешениями [проблем с синхронизацией каталогов для Microsoft 365](fix-problems-with-directory-synchronization.md) , чтобы устранить обнаруженные проблемы.</span><span class="sxs-lookup"><span data-stu-id="82915-116">After viewing, see [fixing problems with directory synchronization for Microsoft 365](fix-problems-with-directory-synchronization.md) to correct any identified issues.</span></span>

