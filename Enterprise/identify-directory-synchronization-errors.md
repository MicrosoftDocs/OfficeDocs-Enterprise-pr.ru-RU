---
title: Просмотр ошибок синхронизации каталогов в Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
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
ms.openlocfilehash: b1cda68590131967ea2fe91506c8e71769f4c32b
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067525"
---
# <a name="view-directory-synchronization-errors-in-office-365"></a><span data-ttu-id="cdfcd-103">Просмотр ошибок синхронизации каталогов в Office 365</span><span class="sxs-lookup"><span data-stu-id="cdfcd-103">View directory synchronization errors in Office 365</span></span>

<span data-ttu-id="cdfcd-104">Вы можете просматривать ошибки синхронизации каталогов в [центре администрирования Microsoft 365](https://admin.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="cdfcd-104">You can view directory synchronization errors in the [Microsoft 365 admin center](https://admin.microsoft.com).</span></span> <span data-ttu-id="cdfcd-105">Отображаются только ошибки объекта пользователя.</span><span class="sxs-lookup"><span data-stu-id="cdfcd-105">Only the User object errors are displayed.</span></span> <span data-ttu-id="cdfcd-106">Просмотреть ошибки с помощью PowerShell можно в разделе [Identify Objects with дирсинкпровисионинжеррорс](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency).</span><span class="sxs-lookup"><span data-stu-id="cdfcd-106">To view errors by using PowerShell, see [Identify objects with DirSyncProvisioningErrors](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency).</span></span>

<span data-ttu-id="cdfcd-107">После просмотра ознакомьтесь с разрешениями [проблем с синхронизацией каталогов для Office 365](fix-problems-with-directory-synchronization.md) , чтобы устранить обнаруженные проблемы.</span><span class="sxs-lookup"><span data-stu-id="cdfcd-107">After viewing, see [fixing problems with directory synchronization for Office 365](fix-problems-with-directory-synchronization.md) to correct any identified issues.</span></span>
  
## <a name="view-directory-synchronization-errors-in-the-admin-center"></a><span data-ttu-id="cdfcd-108">Просмотр ошибок синхронизации каталогов в центре администрирования</span><span class="sxs-lookup"><span data-stu-id="cdfcd-108">View directory synchronization errors in the admin center</span></span>

<span data-ttu-id="cdfcd-109">Чтобы просмотреть ошибки в центре администрирования, выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="cdfcd-109">To view any errors in the admin center:</span></span>
  
1. <span data-ttu-id="cdfcd-110">Войдите в Office 365 с рабочей или учебной учетной записью.</span><span class="sxs-lookup"><span data-stu-id="cdfcd-110">Sign in to Office 365 with your work or school account.</span></span> 
    
2. <span data-ttu-id="cdfcd-111">Перейдите к разделу [о центре администрирования](https://support.office.com/article/758befc4-0888-4009-9f14-0d147402fd23).</span><span class="sxs-lookup"><span data-stu-id="cdfcd-111">Go to the [About the admin center](https://support.office.com/article/758befc4-0888-4009-9f14-0d147402fd23).</span></span>
    
3. <span data-ttu-id="cdfcd-112">На **домашней** странице вы увидите плитку **состояния DirSync** .</span><span class="sxs-lookup"><span data-stu-id="cdfcd-112">On the **Home** page you will see the **DirSync Status** tile.</span></span> 
    
    ![Плитка состояния DirSync в предварительной версии центра администрирования](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
4. <span data-ttu-id="cdfcd-114">На плитке выберите **состояние DirSync** , чтобы перейти на страницу **состояния синхронизации каталогов** .</span><span class="sxs-lookup"><span data-stu-id="cdfcd-114">On the tile, choose **DirSync Status** to go to the **Directory Sync Status** page.</span></span> 
    
    <span data-ttu-id="cdfcd-115">В нижней части страницы можно увидеть, есть ли ошибки DirSync.</span><span class="sxs-lookup"><span data-stu-id="cdfcd-115">On the bottom of the page you can see if there are DirSync errors.</span></span>
    
    ![На странице состояния синхронизации каталогов можно увидеть, есть ли ошибки в объектах DirSync.](media/882094a3-80d3-4aae-b90b-78b27047974c.png)
  
    <span data-ttu-id="cdfcd-117">Нажмите **мы обнаружили ошибки объекта DirSync** , чтобы перейти к подробному представлению ошибок синхронизации службы каталогов.</span><span class="sxs-lookup"><span data-stu-id="cdfcd-117">Choose **We found DirSync object errors** to go to a detailed view of the directory synchronization errors.</span></span> 
    
    > [!NOTE]
    > <span data-ttu-id="cdfcd-118">Вы также можете перейти на страницу **ошибки DirSync** , если вы выберете **ошибки объекта DirSync** в плитке **состояния DirSync** .</span><span class="sxs-lookup"><span data-stu-id="cdfcd-118">You can also go to the **DirSync errors** page if you choose **We found DirSync object errors** on the **DirSync status** tile.</span></span> 
  
![Страница "ошибки DirSync"](media/a6e302d4-6be7-4e3a-b4b5-81c5a2c02952.png)
  
5. <span data-ttu-id="cdfcd-120">На странице " **ошибки DirSync** " выберите любую из указанных ошибок, чтобы отобразить область сведений о сообщении об ошибке, и советы по ее устранению.</span><span class="sxs-lookup"><span data-stu-id="cdfcd-120">On the **DirSync errors** page, choose any of the errors listed to display the details pane with information about the error and tips on how to fix it.</span></span> 
