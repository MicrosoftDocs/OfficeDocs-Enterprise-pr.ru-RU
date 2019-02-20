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
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
ms.assetid: 18be3b98-34ae-47be-9337-ab6c3fb372ac
description: Сведения о том, как отключить синхронизацию службы каталогов. Вы также можете просмотреть его состояние.
ms.openlocfilehash: 4803cbadd17dbc1ee23d019f39144ff1ffaefd9a
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085058"
---
# <a name="view-directory-synchronization-status-in-office-365"></a><span data-ttu-id="b5104-104">Просмотр состояния синхронизации каталогов в Office 365</span><span class="sxs-lookup"><span data-stu-id="b5104-104">View directory synchronization status in Office 365</span></span>
<span data-ttu-id="b5104-105">Если вы интегрируете локальную службу Active Directory с помощью Azure AD, синхронизируя локальную среду с Office 365, вы также можете проверить состояние синхронизации.</span><span class="sxs-lookup"><span data-stu-id="b5104-105">If you have integrated your on-premises Active Directory with Azure AD by synchronizing your on-premises environment with Office 365, you can also check the status of your synchronization.</span></span>
  
## <a name="view-directory-synchronization-status"></a><span data-ttu-id="b5104-106">Просмотр состояния синхронизации каталогов</span><span class="sxs-lookup"><span data-stu-id="b5104-106">View directory synchronization status</span></span>
- <span data-ttu-id="b5104-107">Войдите в центр администрирования Office 365 и выберите **состояние DirSync** на домашней странице.</span><span class="sxs-lookup"><span data-stu-id="b5104-107">Sign in to the Office 365 admin center and choose **DirSync Status** on the home page.</span></span> 
- <span data-ttu-id="b5104-p102">Кроме того, можно перейти к разделу **Активные**пользователи **пользователей** \> , а на странице **Активные пользователи** выбрать **больше** \> **синхронизации службы каталогов**. В области **синхронизация каталогов** выберите пункт **Перейти к управлению DirSync**.</span><span class="sxs-lookup"><span data-stu-id="b5104-p102">Alternately, you can go to **Users** \> **Active users**, and on the **Active users** page, choose **More** \> **Directory synchronization**. On the **Directory Synchronization** pane, choose **Go to DirSync management**.</span></span>
    
## <a name="information-on-the-manage-directory-synchronization-page"></a><span data-ttu-id="b5104-110">Сведения на странице "Управление синхронизацией службы каталогов"</span><span class="sxs-lookup"><span data-stu-id="b5104-110">Information on the Manage directory synchronization page</span></span>

<span data-ttu-id="b5104-111">В следующей таблице перечислены функции, которые можно использовать для получения сведений на странице.</span><span class="sxs-lookup"><span data-stu-id="b5104-111">The following table lists the features you can get information about on the page.</span></span>
  
<span data-ttu-id="b5104-p103">При возникновении проблем с синхронизацией службы каталогов на этой странице также отображаются ошибки. Для получения дополнительных сведений о различных ошибках, которые могут возникать, ознакомьтесь [с разделом определение ошибок синхронизации каталогов в Office 365](identify-directory-synchronization-errors.md).</span><span class="sxs-lookup"><span data-stu-id="b5104-p103">If there is a problem with your directory synchronization, the errors are listed on this page as well. For more information about different errors you might encounter, see [Identify directory synchronization errors in Office 365](identify-directory-synchronization-errors.md).</span></span>
  
|<span data-ttu-id="b5104-114">**Элемент**</span><span class="sxs-lookup"><span data-stu-id="b5104-114">**Item**</span></span>|<span data-ttu-id="b5104-115">**Назначение**</span><span class="sxs-lookup"><span data-stu-id="b5104-115">**What it's for**</span></span>|
|:-----|:-----|
|<span data-ttu-id="b5104-116">**Проверенные домены**</span><span class="sxs-lookup"><span data-stu-id="b5104-116">**Domains verified**</span></span> | <span data-ttu-id="b5104-117">Количество доменов в вашем клиенте Office 365, которые вы прошли проверку.</span><span class="sxs-lookup"><span data-stu-id="b5104-117">Number of domains in your Office 365 tenant that you have verified you own.</span></span> |
|<span data-ttu-id="b5104-118">**Домены не проверены**</span><span class="sxs-lookup"><span data-stu-id="b5104-118">**Domains not verified**</span></span> | <span data-ttu-id="b5104-119">Добавленные, но не проверенные домены.</span><span class="sxs-lookup"><span data-stu-id="b5104-119">Domains you have added, but not verified.</span></span> |
|<span data-ttu-id="b5104-120">**Синхронизация каталогов включена**</span><span class="sxs-lookup"><span data-stu-id="b5104-120">**Directory sync enabled**</span></span> |<span data-ttu-id="b5104-p104">True или false. Указывает, включена ли синхронизация каталогов.</span><span class="sxs-lookup"><span data-stu-id="b5104-p104">True or False. Specifies whether you have enabled directory sync.</span></span> |
|<span data-ttu-id="b5104-123">**Последняя синхронизация каталогов**</span><span class="sxs-lookup"><span data-stu-id="b5104-123">**Latest directory sync**</span></span> | <span data-ttu-id="b5104-p105">Время последнего запуска синхронизации каталога. Отображается предупреждение и ссылка на средство устранения неполадок, если последняя синхронизация выполнялась более трех дней назад.</span><span class="sxs-lookup"><span data-stu-id="b5104-p105">Last time directory sync ran. Will display a warning and a link to a troubleshooting tool if the last sync was more than three days ago.</span></span> |
|<span data-ttu-id="b5104-126">**Синхронизация паролей включена**</span><span class="sxs-lookup"><span data-stu-id="b5104-126">**Password sync enabled**</span></span> | <span data-ttu-id="b5104-p106">True или false. Указывает, существует ли синхронизация хэша пароля между локальным клиентом и вашим клиентом Office 365.</span><span class="sxs-lookup"><span data-stu-id="b5104-p106">True or False. Specifies whether you have password hash sync between our on-premises and your Office 365 tenant.</span></span> |
|<span data-ttu-id="b5104-129">**Последняя синхронизация паролей**</span><span class="sxs-lookup"><span data-stu-id="b5104-129">**Last Password Sync**</span></span> | <span data-ttu-id="b5104-p107">Время последней синхронизации хэша пароля. Отображается предупреждение и ссылка на средство устранения неполадок, если последняя синхронизация выполнялась более трех дней назад.</span><span class="sxs-lookup"><span data-stu-id="b5104-p107">Last time password hash sync ran. Will display a warning and a link to a troubleshooting tool if the last sync was more than three days ago.</span></span> |
|<span data-ttu-id="b5104-132">**Версия клиента синхронизации каталогов**</span><span class="sxs-lookup"><span data-stu-id="b5104-132">**Directory sync client version**</span></span> | <span data-ttu-id="b5104-133">Содержит ссылку для скачивания, если была выпущена новая версия Azure AD Connect.</span><span class="sxs-lookup"><span data-stu-id="b5104-133">Contains a download link if a new version of Azure AD Connect has been released.</span></span> |
|<span data-ttu-id="b5104-134">**Средство IDFix**</span><span class="sxs-lookup"><span data-stu-id="b5104-134">**IDFix Tool**</span></span> | <span data-ttu-id="b5104-135">Ссылка для скачивания на [IDFix](install-and-run-idfix.md), средство, с помощью которого можно проверить локальную службу Active Directory.</span><span class="sxs-lookup"><span data-stu-id="b5104-135">Download link to [IDFix](install-and-run-idfix.md), a tool you can use to check you local Active Directory.</span></span> |
|<span data-ttu-id="b5104-136">**Учетная запись службы синхронизации каталогов**</span><span class="sxs-lookup"><span data-stu-id="b5104-136">**Directory sync service account**</span></span> | <span data-ttu-id="b5104-137">Отображает имя учетной записи службы синхронизации каталогов Office 365.</span><span class="sxs-lookup"><span data-stu-id="b5104-137">Displays the name of you Office 365 directory sync service account.</span></span> |