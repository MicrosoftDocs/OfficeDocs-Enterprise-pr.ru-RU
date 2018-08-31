---
title: Просмотр состояния синхронизации каталогов в Office 365
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
ms.assetid: 18be3b98-34ae-47be-9337-ab6c3fb372ac
description: Узнайте, как отключить синхронизацию службы каталогов. Можно также просмотреть его состояние.
ms.openlocfilehash: c843fa4d71976cbdd0d6d3d10720e2845b26796c
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542613"
---
# <a name="view-directory-synchronization-status-in-office-365"></a><span data-ttu-id="dda0a-104">Просмотр состояния синхронизации каталогов в Office 365</span><span class="sxs-lookup"><span data-stu-id="dda0a-104">View directory synchronization status in Office 365</span></span>
<span data-ttu-id="dda0a-105">Если локальной Active Directory с Azure AD интегрировали путем синхронизации локальной среды с Office 365, вы также можете проверить состояние вашей синхронизации.</span><span class="sxs-lookup"><span data-stu-id="dda0a-105">If you have integrated your on-premises Active Directory with Azure AD by synchronizing your on-premises environment with Office 365, you can also check the status of your synchronization.</span></span>
  
## <a name="view-directory-synchronization-status"></a><span data-ttu-id="dda0a-106">Просмотр состояния синхронизации каталогов</span><span class="sxs-lookup"><span data-stu-id="dda0a-106">View directory synchronization status</span></span>
- <span data-ttu-id="dda0a-107">Войдите Центр администрирования Office 365 и выберите **Состояние DirSync** на домашней странице.</span><span class="sxs-lookup"><span data-stu-id="dda0a-107">Sign in to the Office 365 admin center and choose **DirSync Status** on the home page.</span></span> 
- <span data-ttu-id="dda0a-p102">Кроме того, можно перейти к **пользователям** \> **активных пользователей**и на странице **активных пользователей** выберите **Дополнительные** \> **синхронизации службы каталогов**. В области **Синхронизации службы каталогов** выберите команду **перейдите на страницу управления DirSync**.</span><span class="sxs-lookup"><span data-stu-id="dda0a-p102">Alternately, you can go to **Users** \> **Active users**, and on the **Active users** page, choose **More** \> **Directory synchronization**. On the **Directory Synchronization** pane, choose **Go to DirSync management**.</span></span>
    
## <a name="information-on-the-manage-directory-synchronization-page"></a><span data-ttu-id="dda0a-110">Сведения на странице "Управление синхронизации каталогов"</span><span class="sxs-lookup"><span data-stu-id="dda0a-110">Information on the Manage directory synchronization page</span></span>

<span data-ttu-id="dda0a-111">В следующей таблице перечислены функции, которые вы можете получать сведения о на странице.</span><span class="sxs-lookup"><span data-stu-id="dda0a-111">The following table lists the features you can get information about on the page.</span></span>
  
<span data-ttu-id="dda0a-p103">Если проблема связана с вашей синхронизации службы каталогов, на этой странице также перечислены ошибки. Дополнительные сведения о различных ошибках, которые могут возникнуть в разделе [Определение ошибок синхронизации службы каталогов в Office 365](identify-directory-synchronization-errors.md).</span><span class="sxs-lookup"><span data-stu-id="dda0a-p103">If there is a problem with your directory synchronization, the errors are listed on this page as well. For more information about different errors you might encounter, see [Identify directory synchronization errors in Office 365](identify-directory-synchronization-errors.md).</span></span>
  
|<span data-ttu-id="dda0a-114">**Элемент**</span><span class="sxs-lookup"><span data-stu-id="dda0a-114">**Item**</span></span>|<span data-ttu-id="dda0a-115">**Что такое для**</span><span class="sxs-lookup"><span data-stu-id="dda0a-115">**What it's for**</span></span>|
|:-----|:-----|
|<span data-ttu-id="dda0a-116">**Проверить доменов**</span><span class="sxs-lookup"><span data-stu-id="dda0a-116">**Domains verified**</span></span> | <span data-ttu-id="dda0a-117">Количество доменов в клиент Office 365, что проверки вы владеете.</span><span class="sxs-lookup"><span data-stu-id="dda0a-117">Number of domains in your Office 365 tenant that you have verified you own.</span></span> |
|<span data-ttu-id="dda0a-118">**Домены не проверено**</span><span class="sxs-lookup"><span data-stu-id="dda0a-118">**Domains not verified**</span></span> | <span data-ttu-id="dda0a-119">Домены добавлен, но не проверены.</span><span class="sxs-lookup"><span data-stu-id="dda0a-119">Domains you have added, but not verified.</span></span> |
|<span data-ttu-id="dda0a-120">**Синхронизация каталогов включена**</span><span class="sxs-lookup"><span data-stu-id="dda0a-120">**Directory sync enabled**</span></span> |<span data-ttu-id="dda0a-p104">Значение true или False. Указывает, включена ли синхронизация каталогов.</span><span class="sxs-lookup"><span data-stu-id="dda0a-p104">True or False. Specifies whether you have enabled directory sync.</span></span> |
|<span data-ttu-id="dda0a-123">**Новейшие синхронизации каталогов**</span><span class="sxs-lookup"><span data-stu-id="dda0a-123">**Latest directory sync**</span></span> | <span data-ttu-id="dda0a-p105">Время последнего запуска синхронизации каталогов. Будет отображаться предупреждения и ссылка средства устранения неполадок при последней синхронизации был более чем на три дня назад.</span><span class="sxs-lookup"><span data-stu-id="dda0a-p105">Last time directory sync ran. Will display a warning and a link to a troubleshooting tool if the last sync was more than three days ago.</span></span> |
|<span data-ttu-id="dda0a-126">**Включить синхронизацию паролей**</span><span class="sxs-lookup"><span data-stu-id="dda0a-126">**Password sync enabled**</span></span> | <span data-ttu-id="dda0a-p106">Значение true или False. Указывает, будет ли у вас есть хэш-функции синхронизации паролей между наших локальной и клиента Office 365.</span><span class="sxs-lookup"><span data-stu-id="dda0a-p106">True or False. Specifies whether you have password hash sync between our on-premises and your Office 365 tenant.</span></span> |
|<span data-ttu-id="dda0a-129">**Последняя синхронизация паролей**</span><span class="sxs-lookup"><span data-stu-id="dda0a-129">**Last Password Sync**</span></span> | <span data-ttu-id="dda0a-p107">Время последнего запуска хэш-функции синхронизации паролей. Будет отображаться предупреждения и ссылка средства устранения неполадок при последней синхронизации был более чем на три дня назад.</span><span class="sxs-lookup"><span data-stu-id="dda0a-p107">Last time password hash sync ran. Will display a warning and a link to a troubleshooting tool if the last sync was more than three days ago.</span></span> |
|<span data-ttu-id="dda0a-132">**Версия клиента синхронизации каталогов**</span><span class="sxs-lookup"><span data-stu-id="dda0a-132">**Directory sync client version**</span></span> | <span data-ttu-id="dda0a-133">Содержит ссылки загрузки выпуска новой версии подключить Azure AD.</span><span class="sxs-lookup"><span data-stu-id="dda0a-133">Contains a download link if a new version of Azure AD Connect has been released.</span></span> |
|<span data-ttu-id="dda0a-134">**Инструмент IDFix**</span><span class="sxs-lookup"><span data-stu-id="dda0a-134">**IDFix Tool**</span></span> | <span data-ttu-id="dda0a-135">Ссылка для загрузки для [IDFix](install-and-run-idfix.md), средства, которые можно использовать для проверки локального Active Directory.</span><span class="sxs-lookup"><span data-stu-id="dda0a-135">Download link to [IDFix](install-and-run-idfix.md), a tool you can use to check you local Active Directory.</span></span> |
|<span data-ttu-id="dda0a-136">**Учетная запись службы синхронизации каталогов**</span><span class="sxs-lookup"><span data-stu-id="dda0a-136">**Directory sync service account**</span></span> | <span data-ttu-id="dda0a-137">Отображает имя учетной записи службы синхронизации каталогов Office 365.</span><span class="sxs-lookup"><span data-stu-id="dda0a-137">Displays the name of you Office 365 directory sync service account.</span></span> |