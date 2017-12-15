---
title: "Тестирование руководство по лаборатории настройка интегрированной Exchange, Lync и SharePoint тестовой лаборатории"
ms.author: jhendr
author: JoanneHendrickson
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 48e16935-3429-456a-8fe6-50afa257924c
description: "Сводка: Сведения о создании интегрированной тестовой лабораторной среды, которая содержит сервер под управлением Exchange Server 2013, сервер под управлением Lync Server 2013 и сервера под управлением SharePoint Server 2013."
ms.openlocfilehash: 6fc3bc05db0d28bc4de2be77671ccf5e8fc55926
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2017
---
# <a name="test-lab-guide-configure-an-integrated-exchange-lync-and-sharepoint-test-lab"></a><span data-ttu-id="bf950-103">Руководство по лаборатории тестирования. Настройка интегрированной лаборатории тестирования Exchange, Lync и SharePoint</span><span class="sxs-lookup"><span data-stu-id="bf950-103">Test Lab Guide: Configure an integrated Exchange, Lync, and SharePoint test lab</span></span>

 <span data-ttu-id="bf950-104">**Сводка:** Сведения о создании интегрированной тестовой лабораторной среды, которая содержит сервер под управлением Exchange Server 2013, сервер под управлением Lync Server 2013 и сервера под управлением SharePoint Server 2013.</span><span class="sxs-lookup"><span data-stu-id="bf950-104">**Summary:** Learn how to create an integrated test lab that contains a server that runs Exchange Server 2013, a server that runs Lync Server 2013, and a server that runs SharePoint Server 2013.</span></span>
  
<span data-ttu-id="bf950-105">Лаборатории тестирования, результаты из этой конфигурации, которая включает в себя проверки подлинности сервер сервер между все три типа серверов, можно использовать для построения в работе и демонстрации продукта несколькими сценарии и решения, использующие сервер под управлением Exchange Server 2013 сервер под управлением Lync Server 2013 и сервера под управлением SharePoint Server 2013.</span><span class="sxs-lookup"><span data-stu-id="bf950-105">The test lab that results from this configuration, which includes server-to-server authentication between all three types of servers, can be used to build out and demonstrate multi-product scenarios and solutions that use a server that runs Exchange Server 2013, a server that runs Lync Server 2013, and a server that runs SharePoint Server 2013.</span></span>
  
<span data-ttu-id="bf950-106">В этом документе представлены инструкции для выполнения следующих операций:</span><span class="sxs-lookup"><span data-stu-id="bf950-106">This document contains instructions for the following:</span></span>
  
1. <span data-ttu-id="bf950-107">Настройка лаборатории тестирования базовой конфигурации Windows Server 2012.</span><span class="sxs-lookup"><span data-stu-id="bf950-107">Configuring the Windows Server 2012 Base Configuration test lab.</span></span>
    
2. <span data-ttu-id="bf950-108">Установка и настройка нового сервера SQL1.</span><span class="sxs-lookup"><span data-stu-id="bf950-108">Installing and configuring a new server named SQL1.</span></span>
    
3. <span data-ttu-id="bf950-109">Установка SQL Server 2012 на сервере SQL1.</span><span class="sxs-lookup"><span data-stu-id="bf950-109">Installing SQL Server 2012 on the SQL1 server.</span></span>
    
4. <span data-ttu-id="bf950-110">Установка и настройка нового клиентского компьютера с именем CLIENT2.</span><span class="sxs-lookup"><span data-stu-id="bf950-110">Installing and configuring a new client computer named CLIENT2.</span></span>
    
5. <span data-ttu-id="bf950-111">Установка и настройка Exchange Server 2013 на EX1.</span><span class="sxs-lookup"><span data-stu-id="bf950-111">Installing and configuring Exchange Server 2013 on EX1.</span></span>
    
6. <span data-ttu-id="bf950-112">Установка и настройка нового сервера с именем LYNC1.</span><span class="sxs-lookup"><span data-stu-id="bf950-112">Installing and configuring a new server named LYNC1.</span></span>
    
7. <span data-ttu-id="bf950-113">Установка Lync Server 2013 Standard Edition на LYNC1.</span><span class="sxs-lookup"><span data-stu-id="bf950-113">Installing Lync Server 2013 Standard Edition on LYNC1.</span></span>
    
8. <span data-ttu-id="bf950-114">Установка SharePoint Server 2013 с пакетом обновления 1.</span><span class="sxs-lookup"><span data-stu-id="bf950-114">Installing SharePoint Server 2013 on SP1.</span></span>
    
9. <span data-ttu-id="bf950-115">Настройка интеграции между серверами EX1, LYNC1 и SP1.</span><span class="sxs-lookup"><span data-stu-id="bf950-115">Configuring integration between EX1, LYNC1, and SP1.</span></span>
    
<span data-ttu-id="bf950-116">**Просмотрите интегрированной Exchange, Lync и SharePoint Обзорное видео по лаборатории тестирования**</span><span class="sxs-lookup"><span data-stu-id="bf950-116">**Watch the integrated Exchange, Lync, and SharePoint test lab guide overview video**</span></span>

![Значок видео (кнопка воспроизведения)](images/mod_icon_video_M.png)
  
<span data-ttu-id="bf950-118">Сведения о настройке этой лаборатории тестирования в Hyper-V видеть [размещения интегрированной Exchange, SharePoint и Lync, тестовой лаборатории с помощью Windows Server 2012 Hyper-V](https://social.technet.microsoft.com/wiki/contents/articles/18483.hosting-the-integrated-exchange-lync-and-sharepoint-test-lab-with-windows-server-2012-hyper-v.aspx).</span><span class="sxs-lookup"><span data-stu-id="bf950-118">For information about how to configure this test lab in Hyper-V, see [Hosting the integrated Exchange, Lync, and SharePoint test lab with Windows Server 2012 Hyper-V](https://social.technet.microsoft.com/wiki/contents/articles/18483.hosting-the-integrated-exchange-lync-and-sharepoint-test-lab-with-windows-server-2012-hyper-v.aspx).</span></span>
  
## <a name="download-the-test-lab-guide"></a><span data-ttu-id="bf950-119">Скачайте это руководство</span><span class="sxs-lookup"><span data-stu-id="bf950-119">Download the test lab guide</span></span>

<span data-ttu-id="bf950-120">[Руководство по тестовой лаборатории: настройка интегрированной Exchange, Lync и SharePoint тестовой лаборатории](https://go.microsoft.com/fwlink/p/?LinkId=313670) (https://go.microsoft.com/fwlink/p/?LinkId=313670)</span><span class="sxs-lookup"><span data-stu-id="bf950-120">[Test Lab Guide: Configure an Integrated Exchange, Lync, and SharePoint Test Lab](https://go.microsoft.com/fwlink/p/?LinkId=313670) (https://go.microsoft.com/fwlink/p/?LinkId=313670)</span></span>
  
## <a name="see-also"></a><span data-ttu-id="bf950-121">See Also</span><span class="sxs-lookup"><span data-stu-id="bf950-121">See Also</span></span>

[<span data-ttu-id="bf950-122">Руководства по лаборатории тестирования</span><span class="sxs-lookup"><span data-stu-id="bf950-122">Test Lab Guides</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=202817)




