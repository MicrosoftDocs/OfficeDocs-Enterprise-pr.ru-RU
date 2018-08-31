---
title: Диагностика проблем производительности в SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 2/23/2018
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 3c364f9e-b9f6-4da4-a792-c8e8c8cd2e86
description: В этой статье показано, как можно диагностировать распространенные проблемы, связанные с сайта SharePoint Online с помощью средств разработчика Internet Explorer.
ms.openlocfilehash: 89d4544bfabf6424b5f401bad7d63bd7fa41b5ca
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542460"
---
# <a name="diagnosing-performance-issues-with-sharepoint-online"></a><span data-ttu-id="3d67f-103">Диагностика проблем производительности в SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="3d67f-103">Diagnosing performance issues with SharePoint Online</span></span>

<span data-ttu-id="3d67f-104">В этой статье показано, как можно диагностировать распространенные проблемы, связанные с сайта SharePoint Online с помощью средств разработчика Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="3d67f-104">This article shows you how you can diagnose common issues with your SharePoint Online site using Internet Explorer developer tools.</span></span>
  
<span data-ttu-id="3d67f-105">Существует три различных способа определить, что настройки на странице сайта SharePoint Online вызывают проблемы производительности:</span><span class="sxs-lookup"><span data-stu-id="3d67f-105">There are three different ways that you can identify that a page on a SharePoint Online site has a performance problem with the customizations.</span></span>
  
- <span data-ttu-id="3d67f-106">сетевой мониторинг с помощью панели инструментов F12;</span><span class="sxs-lookup"><span data-stu-id="3d67f-106">The F12 tool bar network monitor</span></span>
    
- <span data-ttu-id="3d67f-107">сравнение с ненастроенным стандартным сайтом;</span><span class="sxs-lookup"><span data-stu-id="3d67f-107">Comparison to a non-customized baseline</span></span>
    
- <span data-ttu-id="3d67f-108">метрики заголовков ответа SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="3d67f-108">SharePoint Online response header metrics</span></span>
    
<span data-ttu-id="3d67f-p101">В этом разделе описывается, как использовать каждый из этих методов для диагностики проблем производительности. Как только поняли причины проблемы, можно работать над решения с помощью статьи о повышении производительности SharePoint, который можно найти на http://aka.ms/tune.</span><span class="sxs-lookup"><span data-stu-id="3d67f-p101">This topic describes how to use each of these methods to diagnose performance issues. Once you've figured out the cause of the problem, you can work toward a solution using the articles about improving SharePoint performance that you can find on http://aka.ms/tune.</span></span>
  
## <a name="using-the-f12-tool-bar-to-diagnose-performance-in-sharepoint-online"></a><span data-ttu-id="3d67f-111">Использование панели инструментов F12 для диагностики производительности в SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="3d67f-111">Using the F12 tool bar to diagnose performance in SharePoint Online</span></span>
<span data-ttu-id="3d67f-112"><a name="F12ToolInfo"> </a></span><span class="sxs-lookup"><span data-stu-id="3d67f-112"></span></span>

<span data-ttu-id="3d67f-p102">В этой статье мы используем Internet Explorer 11. Версии средства для разработчика F12 на других браузерах имеют похожий функционал, хотя могут выглядеть несколько иначе. Более подробную информацию о средствах для разработчика F12 можно узнать в статьях:</span><span class="sxs-lookup"><span data-stu-id="3d67f-p102">In this article we use Internet Explorer 11. Versions of the F12 developer tools on other browsers have similar features though they may look slightly different. For information on the F12 developer tools, see:</span></span>
  
- [<span data-ttu-id="3d67f-116">Новые возможности средства F12</span><span class="sxs-lookup"><span data-stu-id="3d67f-116">What's new in F12 Tools</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=522545)
    
- [<span data-ttu-id="3d67f-117">С помощью средства разработчика F12</span><span class="sxs-lookup"><span data-stu-id="3d67f-117">Using the F12 developer tools</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=522546)
    
<span data-ttu-id="3d67f-118">Для вызова средств разработчика нажмите клавишу **F12**, а затем щелкните значок Wi-Fi: 
</span><span class="sxs-lookup"><span data-stu-id="3d67f-118">To bring up the developer tools press **F12** and then click the Wi-Fi icon:</span></span> 
  
![Снимок экрана со значком Wi-Fi для средств разработчика (F12)](media/27acacbb-5688-459a-aa2f-5c8c5f17b76e.png)
  
<span data-ttu-id="3d67f-p103">На вкладке **Сеть** нажмите зеленую кнопку воспроизведения, чтобы загрузить страницу. Средство вернет все файлы, которые запросил браузер, чтобы получить нужную вам страницу. Один такой список изображен на следующем снимке экрана.</span><span class="sxs-lookup"><span data-stu-id="3d67f-p103">On the **Network** tab, press the green play button to load a page. The tool returns all of the files that the browser requests in order to get the page you asked for. The following screen shot shows one such list.</span></span> 
  
![Снимок экрана со списком возвращенных файлов, которые браузер запрашивает для отображения страницы.](media/247a9422-76da-4b0c-bed3-ce77b05e4560.png)
  
<span data-ttu-id="3d67f-124">Кроме того, с правой стороны вы можете видеть время загрузки файлов, как показано на данном снимке экрана.</span><span class="sxs-lookup"><span data-stu-id="3d67f-124">You can also see the download times of the files on the right side as shown in this screen shot.</span></span>
  
![Схема, показывающая время, которое требуется для загрузки запрошенных из SharePoint страниц](media/d71ad1fa-9018-4fae-82eb-c1838e7db0ff.png)
  
<span data-ttu-id="3d67f-p104">Это даст вам наглядное представление о времени загрузки файла. Зеленая линия показывает, когда страница готова для обработки браузером. Таким способом можно быстро просмотреть различные файлы, которые могут быть причиной медленной загрузки страницы на сайте.

</span><span class="sxs-lookup"><span data-stu-id="3d67f-p104">This gives you a visual representation of how long the file took to load. The green line represents when the page is ready to be rendered by the browser. This can give you a quick view of the different files that might be causing slow page loads on your site.</span></span>
  
## <a name="setting-up-a-non-customized-baseline-for-sharepoint-online"></a><span data-ttu-id="3d67f-129">Настройка базовой без дополнительной настройки для SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="3d67f-129">Setting up a non-customized baseline for SharePoint Online</span></span>
<span data-ttu-id="3d67f-130"><a name="F12ToolInfo"> </a></span><span class="sxs-lookup"><span data-stu-id="3d67f-130"></span></span>

<span data-ttu-id="3d67f-p105">Настройка семейства сайтов полностью-установленными в SharePoint Online — лучший способ определения слабые места производительности веб-узла. Таким образом можно сравнить различных аспектов сайта с максимально без настройки на странице. OneDrive для бизнеса домашней страницы является хорошим примером отдельное семейство сайтов, вероятнее всего, не имеют все настройки.</span><span class="sxs-lookup"><span data-stu-id="3d67f-p105">The best way to determine your site's performance weak points is to set up a completely out-of-the-box site collection in SharePoint Online. This way you can compare all the various aspects of your site with what you would get with no customization on the page. The OneDrive for Business home page is a good example of a separate site collection that is unlikely to have any customizations.</span></span>
  
## <a name="viewing-sharepoint-response-header-information"></a><span data-ttu-id="3d67f-134">Просмотр информации заголовков ответа SharePoint</span><span class="sxs-lookup"><span data-stu-id="3d67f-134">Viewing SharePoint response header information</span></span>
<span data-ttu-id="3d67f-135"><a name="F12ToolInfo"> </a></span><span class="sxs-lookup"><span data-stu-id="3d67f-135"></span></span>

<span data-ttu-id="3d67f-p106">В SharePoint Online и SharePoint Server 2013 вы можете получить доступ к информации, которая отправляется обратно браузеру в заголовке ответа для каждого файла. Два наиболее полезных значения для диагностики ошибок производительности — это SPRequestDuration и X-SharePointHealthScore.</span><span class="sxs-lookup"><span data-stu-id="3d67f-p106">In SharePoint Online and SharePoint Server 2013 you can access the information that is sent back to the browser in the response header for each file. The two most useful values for diagnosing performance issues are SPRequestDuration and X-SharePointHealthScore:</span></span>
  
- <span data-ttu-id="3d67f-138">**SPRequestDuration**</span><span class="sxs-lookup"><span data-stu-id="3d67f-138">**SPRequestDuration**</span></span>
    
    <span data-ttu-id="3d67f-p107">Это количество времени, затраченного на обработку запроса на сервере. Оно поможет выявить слишком тяжелый и ресурсоемкий запрос. Это лучший способ оценить нагрузку на сервер при обработке данной страницы.</span><span class="sxs-lookup"><span data-stu-id="3d67f-p107">This is the amount of time that the request took on the server to be processed. This can help determine if the request is very heavy and resource intensive. This is the best insight you have into how much work the server is doing to serve the page.</span></span>
    
- <span data-ttu-id="3d67f-142">**X-SharePointHealthScore**</span><span class="sxs-lookup"><span data-stu-id="3d67f-142">**X-SharePointHealthScore**</span></span>
    
    <span data-ttu-id="3d67f-p108">Это указывает на использование сервера или ЦП, на котором выполняется экземпляр SharePoint. Это число в диапазоне от 0 до 10, где 0 указывает на сервере простоя и 10 указывает сервер, очень занят. HealthScore, которая постоянно 9 или 10 могут указывать на проблему производительности системы с сервером. Любое другое число указывает, что сервер работает в ожидаемый диапазон.</span><span class="sxs-lookup"><span data-stu-id="3d67f-p108">This indicates the utilization of the server, or CPU, on which your SharePoint instance runs. This number ranges from 0 to 10 where 0 indicates the server is idle and 10 indicates the server is very busy. A HealthScore that is consistently 9 or 10 might indicate an ongoing performance issue with the server. Any other number indicates that server is operating within the expected range.</span></span>
    
 <span data-ttu-id="3d67f-147">**Чтобы просмотреть информацию заголовков ответа SharePoint:**</span><span class="sxs-lookup"><span data-stu-id="3d67f-147">**To view SharePoint response header information**</span></span>
  
1. <span data-ttu-id="3d67f-p109">Убедитесь, что установлены средства F12. Дополнительные сведения о загрузке и установке этих средств [новые возможности средства F12](https://go.microsoft.com/fwlink/p/?LinkId=522545)см.</span><span class="sxs-lookup"><span data-stu-id="3d67f-p109">Ensure that you have the F12 tools installed. For more information on downloading and installing these tools, see [What's new in F12 tools](https://go.microsoft.com/fwlink/p/?LinkId=522545).</span></span>
    
2. <span data-ttu-id="3d67f-150">В средствах F12 на вкладке **Сеть** нажмите зеленую кнопку воспроизведения, чтобы загрузить страницу.</span><span class="sxs-lookup"><span data-stu-id="3d67f-150">In the F12 tools, on the **Network** tab, press the green play button to load a page.</span></span> 
    
3. <span data-ttu-id="3d67f-151">Щелкните один из файлов .aspx, возвращенных средством, и затем нажмите пункт **СВЕДЕНИЯ**.</span><span class="sxs-lookup"><span data-stu-id="3d67f-151">Click one of the .aspx files returned by the tool and then click **DETAILS**.</span></span> 
    
    ![Показывает сведения заголовка ответа](media/1f8a044a-caf8-4613-be2b-7e064141ac8a.png)
  
4. <span data-ttu-id="3d67f-153">Щелкните пункт **Заголовки ответов**.</span><span class="sxs-lookup"><span data-stu-id="3d67f-153">Click **Response headers**.</span></span> 
    
    ![Схема, показывающая URL-адрес заголовка ответа](media/efc7076e-447e-447e-882a-ae3aa721e2c3.png)
  
## <a name="whats-causing-performance-issues-in-sharepoint-online"></a><span data-ttu-id="3d67f-155">Каковы причины ошибок производительности в SharePoint Online?</span><span class="sxs-lookup"><span data-stu-id="3d67f-155">What's causing performance issues in SharePoint Online?</span></span>
<span data-ttu-id="3d67f-156"><a name="F12ToolInfo"> </a></span><span class="sxs-lookup"><span data-stu-id="3d67f-156"></span></span>

<span data-ttu-id="3d67f-p110">Статья [Параметры навигации по SharePoint Online](navigation-options-for-sharepoint-online.md) показан пример с использованием значения SPRequestDuration для определения, что все сложнее структуры навигации причиной страницы, чтобы уйти много времени для обработки на сервере. Используя значение для базового узла (без параметров), можно определить, если любого указанного файла занимает много времени на загрузку. Пример [параметров навигации для SharePoint Online](navigation-options-for-sharepoint-online.md) — это основной ASPX-файл. Этот файл содержит большую часть кода ASP.NET, на котором выполняется для вашей загрузки страницы. В зависимости от шаблона сайта, которые можно использовать это может быть start.aspx, home.aspx, default.aspx или другое имя при настройке домашней страницы. Если этот номер значительно больше, чем базовое сайта, является означает, что есть что-то сложных переходом на страницу, которая вызывает проблемы с производительностью.</span><span class="sxs-lookup"><span data-stu-id="3d67f-p110">The article [Navigation options for SharePoint Online](navigation-options-for-sharepoint-online.md) shows an example of using the SPRequestDuration value to determine that the complicated structural navigation was causing the page to take a long time to process on the server. By taking a value for a baseline site (without customization), it is possible to determine if any given file is taking a long time to load. The example used in [Navigation options for SharePoint Online](navigation-options-for-sharepoint-online.md) is the main .aspx file. That file contains most of the ASP.NET code that runs for your page load. Depending on the site template you use, this could be start.aspx, home.aspx, default.aspx, or another name if you customize the home page. If this number is considerably higher than your baseline site, then it's a good indication that there is something complex going on in your page that is causing performance issues.</span></span> 
  
<span data-ttu-id="3d67f-p111">После того как вы определили на своем сайте конкретную ошибку, рекомендуем выяснить причины низкой производительности, например настройки страницы, а затем одну за другой добавлять их обратно на сайт. После того как вы удалили такое количество настроек, что страница работает хорошо, вы можете одну за другой добавлять специфические настройки обратно.</span><span class="sxs-lookup"><span data-stu-id="3d67f-p111">Once you have identified that an issue specific to your site, the recommended way to figure out what is causing poor performance is to eliminate all of the possible causes, like page customizations, and then add them back to the site one by one. Once you have removed enough customizations that the page is performing well, you can then add back specific customizations one by one.</span></span>
  
<span data-ttu-id="3d67f-p112">Например, если у вас очень сложная навигация, попытайтесь ее изменить так, чтобы не отображались дочерние сайты, затем запустите средства разработчика, чтобы увидеть есть ли изменения. Или если большой объем контента сворачивается, попробуйте удалить свертки со страницы и посмотрите, появились ли улучшения. Если вы устраните все возможные причины и будете добавлять их по отдельности, вы сможете легко определить, какие функции доставляют самые большие проблемы, а затем начать работать над их решением. 
</span><span class="sxs-lookup"><span data-stu-id="3d67f-p112">For example, if you have a very complex navigation try changing the navigation to not show sub-sites then check the developer tools to see if this makes a difference. Or if you have a large amount of content roll-ups try removing them from your page and see if this improves things. If you eliminate all of the possible causes and add them back in one at a time, you can easily identify which features are the biggest problem and then work towards a solution.</span></span>
  

