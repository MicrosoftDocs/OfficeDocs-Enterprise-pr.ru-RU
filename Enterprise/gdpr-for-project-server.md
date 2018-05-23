---
title: GDPR для Project Server
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
description: Узнайте, как обеспечивать соблюдение требований GDPR в локальном развертывании Project Server.
ms.openlocfilehash: 6a630dc4cef2c4117e0ba25497f898d0b8da221b
ms.sourcegitcommit: aabd369fc8b397f9e738374d42d8afd18b96d469
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/17/2018
---
# <a name="gdpr-for-project-server"></a><span data-ttu-id="540ee-103">GDPR для Project Server</span><span class="sxs-lookup"><span data-stu-id="540ee-103">Plan for Project Server</span></span>

<span data-ttu-id="540ee-p101">Project Server использует специальные скрипты для экспорта и редактирования данных пользователя в Project Web App. Ниже описывается базовый процесс.</span><span class="sxs-lookup"><span data-stu-id="540ee-p101">Project Server uses custom scripts to export and redact user data in Project Web App. The basic process is:</span></span>

1.  <span data-ttu-id="540ee-106">Найдите сайты Project Web App в ферме.</span><span class="sxs-lookup"><span data-stu-id="540ee-106">Find the Project Web App sites in your farm.</span></span>

2.  <span data-ttu-id="540ee-107">Найдите на каждом сайте проекты, содержащие данные пользователя.</span><span class="sxs-lookup"><span data-stu-id="540ee-107">Find the projects in each site that contain the user.</span></span>

3.  <span data-ttu-id="540ee-108">Экспортируйте и просмотрите нужные типы данных.</span><span class="sxs-lookup"><span data-stu-id="540ee-108">Export and review the types of data that you want to review.</span></span>

4.  <span data-ttu-id="540ee-109">Отредактируйте данные надлежащим образом.</span><span class="sxs-lookup"><span data-stu-id="540ee-109">Redact data as needed.</span></span>

<span data-ttu-id="540ee-110">Эти действия подробно рассматриваются в следующих статьях:</span><span class="sxs-lookup"><span data-stu-id="540ee-110">These three scenarios are covered in detail in the following articles:</span></span>

- [<span data-ttu-id="540ee-111">Экспорт данных пользователя из Project Server</span><span class="sxs-lookup"><span data-stu-id="540ee-111">Export user data from Project Server</span></span>](/Project/export-user-data-from-project-server?toc=/Office365/Enterprise/toc.json)

- [<span data-ttu-id="540ee-112">Удаление данных пользователя из Project Server</span><span class="sxs-lookup"><span data-stu-id="540ee-112">Delete user data from Project Server</span></span>](/Project/delete-user-data-from-project-server?toc=/Office365/Enterprise/toc.json)


<span data-ttu-id="540ee-113">Обратите внимание, что Project Server основан на SharePoint Server и регистрирует события в журналах ULS SharePoint и базе данных использования.</span><span class="sxs-lookup"><span data-stu-id="540ee-113">Note that Project Server is built on top of SharePoint Server and logs events to the SharePoint ULS logs and Usage database.</span></span>
