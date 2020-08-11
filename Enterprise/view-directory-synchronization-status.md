---
title: Просмотр состояния синхронизации каталогов в Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
ms.assetid: 18be3b98-34ae-47be-9337-ab6c3fb372ac
description: В этой статье рассказывается о том, как проверить состояние синхронизации службы каталогов в Office 365.
ms.openlocfilehash: 9aaad085854326ebb6542f03256ae851b27f0980
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/10/2020
ms.locfileid: "46605865"
---
# <a name="view-directory-synchronization-status-in-microsoft-365"></a><span data-ttu-id="84868-103">Просмотр состояния синхронизации каталогов в Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="84868-103">View directory synchronization status in Microsoft 365</span></span>

<span data-ttu-id="84868-104">Если вы интегрируете локальную службу Active Directory с помощью Azure AD, синхронизируя локальную среду с Microsoft 365, вы также можете проверить состояние синхронизации.</span><span class="sxs-lookup"><span data-stu-id="84868-104">If you have integrated your on-premises Active Directory with Azure AD by synchronizing your on-premises environment with Microsoft 365, you can also check the status of your synchronization.</span></span>
  
## <a name="view-directory-synchronization-status"></a><span data-ttu-id="84868-105">Просмотр состояния синхронизации каталогов</span><span class="sxs-lookup"><span data-stu-id="84868-105">View directory synchronization status</span></span>

- <span data-ttu-id="84868-106">Войдите в [центр администрирования Microsoft 365](https://admin.microsoft.com) и выберите **состояние DirSync** на домашней странице.</span><span class="sxs-lookup"><span data-stu-id="84868-106">Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com) and choose **DirSync Status** on the home page.</span></span>
- <span data-ttu-id="84868-107">Кроме того, можно перейти к разделу активные пользователи **пользователей** \> **Active users**, а на странице **Активные пользователи** выбрать **больше** \> **синхронизации службы каталогов**.</span><span class="sxs-lookup"><span data-stu-id="84868-107">Alternately, you can go to **Users** \> **Active users**, and on the **Active users** page, choose **More** \> **Directory synchronization**.</span></span> <span data-ttu-id="84868-108">В области **синхронизация каталогов** выберите пункт **Перейти к управлению DirSync**.</span><span class="sxs-lookup"><span data-stu-id="84868-108">On the **Directory Synchronization** pane, choose **Go to DirSync management**.</span></span>

## <a name="information-on-the-manage-directory-synchronization-page"></a><span data-ttu-id="84868-109">Сведения на странице "Управление синхронизацией службы каталогов"</span><span class="sxs-lookup"><span data-stu-id="84868-109">Information on the Manage directory synchronization page</span></span>

<span data-ttu-id="84868-110">В следующей таблице перечислены функции, которые можно использовать для получения сведений на странице.</span><span class="sxs-lookup"><span data-stu-id="84868-110">The following table lists the features you can get information about on the page.</span></span>
  
<span data-ttu-id="84868-111">При возникновении проблем с синхронизацией службы каталогов на этой странице также отображаются ошибки.</span><span class="sxs-lookup"><span data-stu-id="84868-111">If there is a problem with your directory synchronization, the errors are listed on this page as well.</span></span> <span data-ttu-id="84868-112">Для получения дополнительных сведений о различных ошибках, которые могут возникать, ознакомьтесь с разделом [Определение ошибок синхронизации каталогов в Microsoft 365](identify-directory-synchronization-errors.md).</span><span class="sxs-lookup"><span data-stu-id="84868-112">For more information about different errors you might encounter, see [Identify directory synchronization errors in Microsoft 365](identify-directory-synchronization-errors.md).</span></span>
  
|<span data-ttu-id="84868-113">**Элемент**</span><span class="sxs-lookup"><span data-stu-id="84868-113">**Item**</span></span>|<span data-ttu-id="84868-114">**Назначение**</span><span class="sxs-lookup"><span data-stu-id="84868-114">**What it's for**</span></span>|
|:-----|:-----|
|<span data-ttu-id="84868-115">**Проверенные домены**</span><span class="sxs-lookup"><span data-stu-id="84868-115">**Domains verified**</span></span> | <span data-ttu-id="84868-116">Число доменов в вашем клиенте Microsoft 365, которым вы прошли проверку.</span><span class="sxs-lookup"><span data-stu-id="84868-116">Number of domains in your Microsoft 365 tenant that you have verified you own.</span></span> |
|<span data-ttu-id="84868-117">**Домены не проверены**</span><span class="sxs-lookup"><span data-stu-id="84868-117">**Domains not verified**</span></span> | <span data-ttu-id="84868-118">Добавленные, но не проверенные домены.</span><span class="sxs-lookup"><span data-stu-id="84868-118">Domains you have added, but not verified.</span></span> |
|<span data-ttu-id="84868-119">**Синхронизация каталогов включена**</span><span class="sxs-lookup"><span data-stu-id="84868-119">**Directory sync enabled**</span></span> |<span data-ttu-id="84868-120">True или false.</span><span class="sxs-lookup"><span data-stu-id="84868-120">True or False.</span></span> <span data-ttu-id="84868-121">Указывает, включена ли синхронизация каталогов.</span><span class="sxs-lookup"><span data-stu-id="84868-121">Specifies whether you have enabled directory sync.</span></span> |
|<span data-ttu-id="84868-122">**Последняя синхронизация каталогов**</span><span class="sxs-lookup"><span data-stu-id="84868-122">**Latest directory sync**</span></span> | <span data-ttu-id="84868-123">Время последнего запуска синхронизации каталога.</span><span class="sxs-lookup"><span data-stu-id="84868-123">Last time directory sync ran.</span></span> <span data-ttu-id="84868-124">Отображается предупреждение и ссылка на средство устранения неполадок, если последняя синхронизация выполнялась более трех дней назад.</span><span class="sxs-lookup"><span data-stu-id="84868-124">Will display a warning and a link to a troubleshooting tool if the last sync was more than three days ago.</span></span> |
|<span data-ttu-id="84868-125">**Синхронизация паролей включена**</span><span class="sxs-lookup"><span data-stu-id="84868-125">**Password sync enabled**</span></span> | <span data-ttu-id="84868-126">True или false.</span><span class="sxs-lookup"><span data-stu-id="84868-126">True or False.</span></span> <span data-ttu-id="84868-127">Указывает, существует ли синхронизация хэша пароля между локальным и клиентским клиентом Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="84868-127">Specifies whether you have password hash sync between our on-premises and your Microsoft 365 tenant.</span></span> |
|<span data-ttu-id="84868-128">**Последняя синхронизация паролей**</span><span class="sxs-lookup"><span data-stu-id="84868-128">**Last Password Sync**</span></span> | <span data-ttu-id="84868-129">Время последней синхронизации хэша пароля.</span><span class="sxs-lookup"><span data-stu-id="84868-129">Last time password hash sync ran.</span></span> <span data-ttu-id="84868-130">Отображается предупреждение и ссылка на средство устранения неполадок, если последняя синхронизация выполнялась более трех дней назад.</span><span class="sxs-lookup"><span data-stu-id="84868-130">Will display a warning and a link to a troubleshooting tool if the last sync was more than three days ago.</span></span> |
|<span data-ttu-id="84868-131">**Версия клиента синхронизации каталогов**</span><span class="sxs-lookup"><span data-stu-id="84868-131">**Directory sync client version**</span></span> | <span data-ttu-id="84868-132">Содержит ссылку для скачивания, если была выпущена новая версия Azure AD Connect.</span><span class="sxs-lookup"><span data-stu-id="84868-132">Contains a download link if a new version of Azure AD Connect has been released.</span></span> |
|<span data-ttu-id="84868-133">**Учетная запись службы синхронизации каталогов**</span><span class="sxs-lookup"><span data-stu-id="84868-133">**Directory sync service account**</span></span> | <span data-ttu-id="84868-134">Отображает имя учетной записи службы синхронизации каталогов Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="84868-134">Displays the name of your Microsoft 365 directory sync service account.</span></span> |