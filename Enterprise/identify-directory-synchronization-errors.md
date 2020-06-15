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
# <a name="view-directory-synchronization-errors-in-microsoft-365"></a><span data-ttu-id="0f09a-103">Просмотр ошибок синхронизации каталогов в Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="0f09a-103">View directory synchronization errors in Microsoft 365</span></span>

<span data-ttu-id="0f09a-104">Вы можете просматривать ошибки синхронизации каталогов в [центре администрирования Microsoft 365](https://admin.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="0f09a-104">You can view directory synchronization errors in the [Microsoft 365 admin center](https://admin.microsoft.com).</span></span> <span data-ttu-id="0f09a-105">Отображаются только ошибки объекта пользователя.</span><span class="sxs-lookup"><span data-stu-id="0f09a-105">Only the User object errors are displayed.</span></span> <span data-ttu-id="0f09a-106">Просмотреть ошибки с помощью PowerShell можно в разделе [Identify Objects with дирсинкпровисионинжеррорс](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency).</span><span class="sxs-lookup"><span data-stu-id="0f09a-106">To view errors by using PowerShell, see [Identify objects with DirSyncProvisioningErrors](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency).</span></span>

<span data-ttu-id="0f09a-107">После просмотра ознакомьтесь с разрешениями [проблем с синхронизацией каталогов для Microsoft 365](fix-problems-with-directory-synchronization.md) , чтобы устранить обнаруженные проблемы.</span><span class="sxs-lookup"><span data-stu-id="0f09a-107">After viewing, see [fixing problems with directory synchronization for Microsoft 365](fix-problems-with-directory-synchronization.md) to correct any identified issues.</span></span>
  
## <a name="view-directory-synchronization-errors-in-the-admin-center"></a><span data-ttu-id="0f09a-108">Просмотр ошибок синхронизации каталогов в центре администрирования</span><span class="sxs-lookup"><span data-stu-id="0f09a-108">View directory synchronization errors in the admin center</span></span>

<span data-ttu-id="0f09a-109">Чтобы просмотреть ошибки в центре администрирования, выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="0f09a-109">To view any errors in the admin center:</span></span>
  
1. <span data-ttu-id="0f09a-110">Войдите в Microsoft 365, используя свою рабочую или учебную учетную запись.</span><span class="sxs-lookup"><span data-stu-id="0f09a-110">Sign in to Microsoft 365 with your work or school account.</span></span> 
    
2. <span data-ttu-id="0f09a-111">Перейдите к разделу [о центре администрирования](https://support.office.com/article/758befc4-0888-4009-9f14-0d147402fd23).</span><span class="sxs-lookup"><span data-stu-id="0f09a-111">Go to the [About the admin center](https://support.office.com/article/758befc4-0888-4009-9f14-0d147402fd23).</span></span>
    
3. <span data-ttu-id="0f09a-112">На **домашней** странице вы увидите плитку **состояния DirSync** .</span><span class="sxs-lookup"><span data-stu-id="0f09a-112">On the **Home** page you will see the **DirSync Status** tile.</span></span> 
    
    ![Плитка "Состояние DirSync" в предварительной версии центра администрирования](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
4. <span data-ttu-id="0f09a-114">На плитке выберите **состояние DirSync** , чтобы перейти на страницу **состояния синхронизации каталогов** .</span><span class="sxs-lookup"><span data-stu-id="0f09a-114">On the tile, choose **DirSync Status** to go to the **Directory Sync Status** page.</span></span> 
    
    <span data-ttu-id="0f09a-115">В нижней части страницы можно увидеть, есть ли ошибки DirSync.</span><span class="sxs-lookup"><span data-stu-id="0f09a-115">On the bottom of the page you can see if there are DirSync errors.</span></span>
    
    ![На странице состояния синхронизации каталогов можно увидеть, есть ли ошибки в объектах DirSync.](media/882094a3-80d3-4aae-b90b-78b27047974c.png)
  
    <span data-ttu-id="0f09a-117">Нажмите **мы обнаружили ошибки объекта DirSync** , чтобы перейти к подробному представлению ошибок синхронизации службы каталогов.</span><span class="sxs-lookup"><span data-stu-id="0f09a-117">Choose **We found DirSync object errors** to go to a detailed view of the directory synchronization errors.</span></span> 
    
    > [!NOTE]
    > <span data-ttu-id="0f09a-118">Вы также можете перейти на страницу **ошибки DirSync** , если вы выберете **ошибки объекта DirSync** в плитке **состояния DirSync** .</span><span class="sxs-lookup"><span data-stu-id="0f09a-118">You can also go to the **DirSync errors** page if you choose **We found DirSync object errors** on the **DirSync status** tile.</span></span> 
  
![Страница "ошибки DirSync"](media/a6e302d4-6be7-4e3a-b4b5-81c5a2c02952.png)
  
5. <span data-ttu-id="0f09a-120">На странице " **ошибки DirSync** " выберите любую из указанных ошибок, чтобы отобразить область сведений о сообщении об ошибке, и советы по ее устранению.</span><span class="sxs-lookup"><span data-stu-id="0f09a-120">On the **DirSync errors** page, choose any of the errors listed to display the details pane with information about the error and tips on how to fix it.</span></span> 
