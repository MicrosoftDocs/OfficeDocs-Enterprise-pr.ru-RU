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
ms.openlocfilehash: 4c2f0baf6d3657e3eb9974ff7d4f8109e52e603b
ms.sourcegitcommit: a9021ba0800ffc0da21cf2c4da67ab1da2d97099
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/05/2020
ms.locfileid: "46571042"
---
# <a name="view-directory-synchronization-status-in-microsoft-365"></a><span data-ttu-id="4cb28-104">Просмотр состояния синхронизации каталогов в Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="4cb28-104">View directory synchronization status in Microsoft 365</span></span>

<span data-ttu-id="4cb28-105">Если вы интегрируете локальную службу Active Directory с помощью Azure AD, синхронизируя локальную среду с Microsoft 365, вы также можете проверить состояние синхронизации.</span><span class="sxs-lookup"><span data-stu-id="4cb28-105">If you have integrated your on-premises Active Directory with Azure AD by synchronizing your on-premises environment with Microsoft 365, you can also check the status of your synchronization.</span></span>
  
## <a name="view-directory-synchronization-status"></a><span data-ttu-id="4cb28-106">Просмотр состояния синхронизации каталогов</span><span class="sxs-lookup"><span data-stu-id="4cb28-106">View directory synchronization status</span></span>

- <span data-ttu-id="4cb28-107">Войдите в [центр администрирования Microsoft 365](https://admin.microsoft.com) и выберите **состояние DirSync** на домашней странице.</span><span class="sxs-lookup"><span data-stu-id="4cb28-107">Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com) and choose **DirSync Status** on the home page.</span></span>
- <span data-ttu-id="4cb28-108">Кроме того, можно перейти к разделу активные пользователи **пользователей** \> **Active users**, а на странице **Активные пользователи** выбрать **больше** \> **синхронизации службы каталогов**.</span><span class="sxs-lookup"><span data-stu-id="4cb28-108">Alternately, you can go to **Users** \> **Active users**, and on the **Active users** page, choose **More** \> **Directory synchronization**.</span></span> <span data-ttu-id="4cb28-109">В области **синхронизация каталогов** выберите пункт **Перейти к управлению DirSync**.</span><span class="sxs-lookup"><span data-stu-id="4cb28-109">On the **Directory Synchronization** pane, choose **Go to DirSync management**.</span></span>

## <a name="information-on-the-manage-directory-synchronization-page"></a><span data-ttu-id="4cb28-110">Сведения на странице "Управление синхронизацией службы каталогов"</span><span class="sxs-lookup"><span data-stu-id="4cb28-110">Information on the Manage directory synchronization page</span></span>

<span data-ttu-id="4cb28-111">В следующей таблице перечислены функции, которые можно использовать для получения сведений на странице.</span><span class="sxs-lookup"><span data-stu-id="4cb28-111">The following table lists the features you can get information about on the page.</span></span>
  
<span data-ttu-id="4cb28-112">При возникновении проблем с синхронизацией службы каталогов на этой странице также отображаются ошибки.</span><span class="sxs-lookup"><span data-stu-id="4cb28-112">If there is a problem with your directory synchronization, the errors are listed on this page as well.</span></span> <span data-ttu-id="4cb28-113">Для получения дополнительных сведений о различных ошибках, которые могут возникать, ознакомьтесь с разделом [Определение ошибок синхронизации каталогов в Microsoft 365](identify-directory-synchronization-errors.md).</span><span class="sxs-lookup"><span data-stu-id="4cb28-113">For more information about different errors you might encounter, see [Identify directory synchronization errors in Microsoft 365](identify-directory-synchronization-errors.md).</span></span>
  
|<span data-ttu-id="4cb28-114">**Элемент**</span><span class="sxs-lookup"><span data-stu-id="4cb28-114">**Item**</span></span>|<span data-ttu-id="4cb28-115">**Назначение**</span><span class="sxs-lookup"><span data-stu-id="4cb28-115">**What it's for**</span></span>|
|:-----|:-----|
|<span data-ttu-id="4cb28-116">**Проверенные домены**</span><span class="sxs-lookup"><span data-stu-id="4cb28-116">**Domains verified**</span></span> | <span data-ttu-id="4cb28-117">Число доменов в вашем клиенте Microsoft 365, которым вы прошли проверку.</span><span class="sxs-lookup"><span data-stu-id="4cb28-117">Number of domains in your Microsoft 365 tenant that you have verified you own.</span></span> |
|<span data-ttu-id="4cb28-118">**Домены не проверены**</span><span class="sxs-lookup"><span data-stu-id="4cb28-118">**Domains not verified**</span></span> | <span data-ttu-id="4cb28-119">Добавленные, но не проверенные домены.</span><span class="sxs-lookup"><span data-stu-id="4cb28-119">Domains you have added, but not verified.</span></span> |
|<span data-ttu-id="4cb28-120">**Синхронизация каталогов включена**</span><span class="sxs-lookup"><span data-stu-id="4cb28-120">**Directory sync enabled**</span></span> |<span data-ttu-id="4cb28-121">True или false.</span><span class="sxs-lookup"><span data-stu-id="4cb28-121">True or False.</span></span> <span data-ttu-id="4cb28-122">Указывает, включена ли синхронизация каталогов.</span><span class="sxs-lookup"><span data-stu-id="4cb28-122">Specifies whether you have enabled directory sync.</span></span> |
|<span data-ttu-id="4cb28-123">**Последняя синхронизация каталогов**</span><span class="sxs-lookup"><span data-stu-id="4cb28-123">**Latest directory sync**</span></span> | <span data-ttu-id="4cb28-124">Время последнего запуска синхронизации каталога.</span><span class="sxs-lookup"><span data-stu-id="4cb28-124">Last time directory sync ran.</span></span> <span data-ttu-id="4cb28-125">Отображается предупреждение и ссылка на средство устранения неполадок, если последняя синхронизация выполнялась более трех дней назад.</span><span class="sxs-lookup"><span data-stu-id="4cb28-125">Will display a warning and a link to a troubleshooting tool if the last sync was more than three days ago.</span></span> |
|<span data-ttu-id="4cb28-126">**Синхронизация паролей включена**</span><span class="sxs-lookup"><span data-stu-id="4cb28-126">**Password sync enabled**</span></span> | <span data-ttu-id="4cb28-127">True или false.</span><span class="sxs-lookup"><span data-stu-id="4cb28-127">True or False.</span></span> <span data-ttu-id="4cb28-128">Указывает, существует ли синхронизация хэша пароля между локальным и клиентским клиентом Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="4cb28-128">Specifies whether you have password hash sync between our on-premises and your Microsoft 365 tenant.</span></span> |
|<span data-ttu-id="4cb28-129">**Последняя синхронизация паролей**</span><span class="sxs-lookup"><span data-stu-id="4cb28-129">**Last Password Sync**</span></span> | <span data-ttu-id="4cb28-130">Время последней синхронизации хэша пароля.</span><span class="sxs-lookup"><span data-stu-id="4cb28-130">Last time password hash sync ran.</span></span> <span data-ttu-id="4cb28-131">Отображается предупреждение и ссылка на средство устранения неполадок, если последняя синхронизация выполнялась более трех дней назад.</span><span class="sxs-lookup"><span data-stu-id="4cb28-131">Will display a warning and a link to a troubleshooting tool if the last sync was more than three days ago.</span></span> |
|<span data-ttu-id="4cb28-132">**Версия клиента синхронизации каталогов**</span><span class="sxs-lookup"><span data-stu-id="4cb28-132">**Directory sync client version**</span></span> | <span data-ttu-id="4cb28-133">Содержит ссылку для скачивания, если была выпущена новая версия Azure AD Connect.</span><span class="sxs-lookup"><span data-stu-id="4cb28-133">Contains a download link if a new version of Azure AD Connect has been released.</span></span> |
|<span data-ttu-id="4cb28-134">**Учетная запись службы синхронизации каталогов**</span><span class="sxs-lookup"><span data-stu-id="4cb28-134">**Directory sync service account**</span></span> | <span data-ttu-id="4cb28-135">Отображает имя учетной записи службы синхронизации каталогов Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="4cb28-135">Displays the name of your Microsoft 365 directory sync service account.</span></span> |