---
title: Просмотр ошибок синхронизации службы каталогов в Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
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
ms.openlocfilehash: 62f1135568261eccf0e7e66b78c5aaff966c7281
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542455"
---
# <a name="view-directory-synchronization-errors-in-office-365"></a><span data-ttu-id="9d20a-103">Просмотр ошибок синхронизации службы каталогов в Office 365</span><span class="sxs-lookup"><span data-stu-id="9d20a-103">View directory synchronization errors in Office 365</span></span>

<span data-ttu-id="9d20a-p101">В центре администрирования Office 365 можно просмотреть ошибок синхронизации службы каталогов. Отображаются только ошибки объекта пользователя. Просмотр ошибок с помощью PowerShell, просмотрите [Определение объектов с DirSyncProvisioningErrors](https://go.microsoft.com/fwlink/p/?LinkId=798300).</span><span class="sxs-lookup"><span data-stu-id="9d20a-p101">You can view directory synchronization errors in the Office 365 admin center. Only the User object errors are displayed. To view errors by using PowerShell, see [Identify objects with DirSyncProvisioningErrors](https://go.microsoft.com/fwlink/p/?LinkId=798300).</span></span>

<span data-ttu-id="9d20a-107">После просмотра, в разделе [Устранение проблем с синхронизацией каталогов для Office 365](fix-problems-with-directory-synchronization.md) для исправления найденных проблем.</span><span class="sxs-lookup"><span data-stu-id="9d20a-107">After viewing, see [fixing problems with directory synchronization for Office 365](fix-problems-with-directory-synchronization.md) to correct any identified issues.</span></span>
  
## <a name="view-directory-synchronization-errors-in-the-admin-center"></a><span data-ttu-id="9d20a-108">Просмотр ошибок синхронизации службы каталогов в центре администрирования</span><span class="sxs-lookup"><span data-stu-id="9d20a-108">View directory synchronization errors in the admin center</span></span>

<span data-ttu-id="9d20a-109">Чтобы просмотреть все ошибки в центре администрирования:</span><span class="sxs-lookup"><span data-stu-id="9d20a-109">To view any errors in the admin center:</span></span>
  
1. <span data-ttu-id="9d20a-110">Войдите в Office 365 с помощью рабочей или учебной учетной записи.</span><span class="sxs-lookup"><span data-stu-id="9d20a-110">Sign in to Office 365 with your work or school account.</span></span> 
    
2. <span data-ttu-id="9d20a-111">Перейдите в [Центр администрирования об Office 365](https://support.office.com/article/758befc4-0888-4009-9f14-0d147402fd23).</span><span class="sxs-lookup"><span data-stu-id="9d20a-111">Go to the [About the Office 365 admin center](https://support.office.com/article/758befc4-0888-4009-9f14-0d147402fd23).</span></span>
    
3. <span data-ttu-id="9d20a-112">На **домашней** странице отображается Плитка **Состояние DirSync** .</span><span class="sxs-lookup"><span data-stu-id="9d20a-112">On the **Home** page you will see the **DirSync Status** tile.</span></span> 
    
    ![Состояние DirSync плиток в предварительной версии центра администрирования](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
4. <span data-ttu-id="9d20a-114">В разделе Выбор перейдите на страницу **Состояния синхронизации каталогов** в **Состоянии DirSync** .</span><span class="sxs-lookup"><span data-stu-id="9d20a-114">On the tile, choose **DirSync Status** to go to the **Directory Sync Status** page.</span></span> 
    
    <span data-ttu-id="9d20a-115">В нижней части страницы можно видеть, если имеется DirSync ошибки.</span><span class="sxs-lookup"><span data-stu-id="9d20a-115">On the bottom of the page you can see if there are DirSync errors.</span></span>
    
    ![На странице состояния синхронизации каталогов можно увидеть при наличии ошибок объект DirSync](media/882094a3-80d3-4aae-b90b-78b27047974c.png)
  
    <span data-ttu-id="9d20a-117">Выберите, **мы обнаружили ошибки объекта DirSync** переход на подробное представление ошибок синхронизации службы каталогов.</span><span class="sxs-lookup"><span data-stu-id="9d20a-117">Choose **We found DirSync object errors** to go to a detailed view of the directory synchronization errors.</span></span> 
    
    > [!NOTE]
    > <span data-ttu-id="9d20a-118">Также можно перейти к странице **DirSync ошибки** , если **мы обнаружили ошибки объекта DirSync** выберите в разделе **состояние DirSync** .</span><span class="sxs-lookup"><span data-stu-id="9d20a-118">You can also go to the **DirSync errors** page if you choose **We found DirSync object errors** on the **DirSync status** tile.</span></span> 
  
![Страница ошибок DirSync](media/a6e302d4-6be7-4e3a-b4b5-81c5a2c02952.png)
  
5. <span data-ttu-id="9d20a-120">На странице **ошибок DirSync** выберите любой из списка для отображения области сведений со сведениями об ошибке и советы по исправлению ошибок.</span><span class="sxs-lookup"><span data-stu-id="9d20a-120">On the **DirSync errors** page, choose any of the errors listed to display the details pane with information about the error and tips on how to fix it.</span></span> 
