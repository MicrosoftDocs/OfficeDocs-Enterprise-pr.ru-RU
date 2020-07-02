---
title: Руководство по лаборатории тестирования Настройка интегрированной лаборатории тестирования Exchange, Lync и SharePoint
ms.author: jhendr
author: JoanneHendrickson
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 48e16935-3429-456a-8fe6-50afa257924c
f1.keywords:
- NOCSH
description: Сводка. Узнайте, как создать интегрированную лабораторию тестирования, содержащую сервер под управлением Exchange Server 2013, сервер, на котором работает Lync Server 2013, и сервер, на котором работает SharePoint Server 2013.
ms.openlocfilehash: bfb2e1be3b9bb401514e736d38a6f1a2944940f0
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "44996523"
---
# <a name="test-lab-guide-configure-an-integrated-exchange-lync-and-sharepoint-test-lab"></a><span data-ttu-id="e1786-103">Руководство по лаборатории тестирования. Настройка интегрированной лаборатории тестирования Exchange, Lync и SharePoint</span><span class="sxs-lookup"><span data-stu-id="e1786-103">Test Lab Guide: Configure an integrated Exchange, Lync, and SharePoint test lab</span></span>

 <span data-ttu-id="e1786-104">Узнайте, как создать интегрированную лабораторию тестирования, которая содержит серверы Exchange Server 2013, Lync Server 2013 и SharePoint Server 2013.</span><span class="sxs-lookup"><span data-stu-id="e1786-104">Learn how to create an integrated test lab that contains a server that runs Exchange Server 2013, a server that runs Lync Server 2013, and a server that runs SharePoint Server 2013.</span></span>
 
<span data-ttu-id="e1786-105">**Посмотрите видеообзор руководства по созданию интегрированной лаборатории тестирования Exchange, Lync и SharePoint**</span><span class="sxs-lookup"><span data-stu-id="e1786-105">**Watch the integrated Exchange, Lync, and SharePoint test lab guide overview video**</span></span>

> [!VIDEO https://videoplayercdn.osi.office.net/hub/?csid=ux-cms-en-us-msoffice&uuid=8d1f00cc-b8b1-4394-9367-0cc9765e380a&AutoPlayVideo=false]
 
<span data-ttu-id="e1786-106">Тестовая лаборатория, полученная из этой конфигурации, которая включает межсерверную проверку подлинности между всеми тремя типами серверов, может использоваться для создания и демонстрации сценариев с несколькими продуктами и решений, использующих сервер под управлением Exchange Server 2013, сервер, на котором работает Lync Server 2013, и сервер, на котором работает SharePoint Server 2013.</span><span class="sxs-lookup"><span data-stu-id="e1786-106">The test lab that results from this configuration, which includes server-to-server authentication between all three types of servers, can be used to build out and demonstrate multi-product scenarios and solutions that use a server that runs Exchange Server 2013, a server that runs Lync Server 2013, and a server that runs SharePoint Server 2013.</span></span>
  
<span data-ttu-id="e1786-107">В этом документе представлены инструкции для:</span><span class="sxs-lookup"><span data-stu-id="e1786-107">This document contains instructions for:</span></span>
  
1. <span data-ttu-id="e1786-108">Настройка лаборатории тестирования базовой конфигурации Windows Server 2012.</span><span class="sxs-lookup"><span data-stu-id="e1786-108">Configuring the Windows Server 2012 Base Configuration test lab.</span></span>
    
2. <span data-ttu-id="e1786-109">Установка и настройка нового сервера SQL1.</span><span class="sxs-lookup"><span data-stu-id="e1786-109">Installing and configuring a new server named SQL1.</span></span>
    
3. <span data-ttu-id="e1786-110">Установка SQL Server 2012 на сервере SQL1.</span><span class="sxs-lookup"><span data-stu-id="e1786-110">Installing SQL Server 2012 on the SQL1 server.</span></span>
    
4. <span data-ttu-id="e1786-111">Установка и настройка нового клиентского компьютера с именем CLIENT2.</span><span class="sxs-lookup"><span data-stu-id="e1786-111">Installing and configuring a new client computer named CLIENT2.</span></span>
    
5. <span data-ttu-id="e1786-112">Установка и настройка Exchange Server 2013 на EX1.</span><span class="sxs-lookup"><span data-stu-id="e1786-112">Installing and configuring Exchange Server 2013 on EX1.</span></span>
    
6. <span data-ttu-id="e1786-113">Установка и настройка нового сервера с именем LYNC1.</span><span class="sxs-lookup"><span data-stu-id="e1786-113">Installing and configuring a new server named LYNC1.</span></span>
    
7. <span data-ttu-id="e1786-114">Установка Lync Server 2013 Standard Edition на LYNC1.</span><span class="sxs-lookup"><span data-stu-id="e1786-114">Installing Lync Server 2013 Standard Edition on LYNC1.</span></span>
    
8. <span data-ttu-id="e1786-115">Установка SharePoint Server 2013 в пакет обновления 1 (SP1).</span><span class="sxs-lookup"><span data-stu-id="e1786-115">Installing SharePoint Server 2013 on SP1.</span></span>
    
9. <span data-ttu-id="e1786-116">Настройка интеграции между серверами EX1, LYNC1 и SP1.</span><span class="sxs-lookup"><span data-stu-id="e1786-116">Configuring integration between EX1, LYNC1, and SP1.</span></span>
    
<span data-ttu-id="e1786-117">Сведения о настройке этой лаборатории тестирования в Hyper-V можно найти в статье [Размещение интегрированной лаборатории тестирования Exchange, Lync и SharePoint с помощью Windows Server 2012 Hyper-V](https://social.technet.microsoft.com/wiki/contents/articles/18483.hosting-the-integrated-exchange-lync-and-sharepoint-test-lab-with-windows-server-2012-hyper-v.aspx).</span><span class="sxs-lookup"><span data-stu-id="e1786-117">For information about how to configure this test lab in Hyper-V, see [Hosting the integrated Exchange, Lync, and SharePoint test lab with Windows Server 2012 Hyper-V](https://social.technet.microsoft.com/wiki/contents/articles/18483.hosting-the-integrated-exchange-lync-and-sharepoint-test-lab-with-windows-server-2012-hyper-v.aspx).</span></span>
  
## <a name="download-the-test-lab-guide"></a><span data-ttu-id="e1786-118">Скачайте это руководство</span><span class="sxs-lookup"><span data-stu-id="e1786-118">Download the test lab guide</span></span>

<span data-ttu-id="e1786-119">[Руководство по лаборатории тестирования: Настройка интегрированной лаборатории тестирования Exchange, Lync и SharePoint](https://go.microsoft.com/fwlink/p/?LinkId=313670) (https://go.microsoft.com/fwlink/p/?LinkId=313670)</span><span class="sxs-lookup"><span data-stu-id="e1786-119">[Test Lab Guide: Configure an Integrated Exchange, Lync, and SharePoint Test Lab](https://go.microsoft.com/fwlink/p/?LinkId=313670) (https://go.microsoft.com/fwlink/p/?LinkId=313670)</span></span>
  
## <a name="see-also"></a><span data-ttu-id="e1786-120">См. также</span><span class="sxs-lookup"><span data-stu-id="e1786-120">See Also</span></span>

[<span data-ttu-id="e1786-121">Руководства по лаборатории тестирования</span><span class="sxs-lookup"><span data-stu-id="e1786-121">Test Lab Guides</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=202817)




