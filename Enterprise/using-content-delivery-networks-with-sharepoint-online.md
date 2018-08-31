---
title: Использование сети доставки содержимого с помощью SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 5/8/2017
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
ms.assetid: 9a64268c-0b74-4eaa-b971-fb6380b1b165
description: 'Сводка: В этой статье описываются контента сети доставки (CDN) и как их использовать для повышения производительности SharePoint Online.'
ms.openlocfilehash: 63062c08d0c22518eb36ea0a6faa97106fd394b4
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542416"
---
# <a name="using-content-delivery-networks-with-sharepoint-online"></a><span data-ttu-id="8439b-103">Использование сети доставки содержимого с помощью SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="8439b-103">Using content delivery networks with SharePoint Online</span></span>

 <span data-ttu-id="8439b-104">**Сводка:** В этой статье описываются контента сети доставки (CDN) и как их использовать для повышения производительности SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="8439b-104">**Summary:** This article describes Content Delivery Networks (CDNs) and how you can use them to increase SharePoint Online performance.</span></span> 
  
<span data-ttu-id="8439b-p101">В современных web разработки сообщества существует множество общих библиотек (таких как JavaScript и CSS-файлы), которые могут включать в решении SharePoint. Многие из них, размещенных Майкрософт на их CDN ASP. Это означает, что можно ссылки этих библиотек из этих распределенных серверов и разрешить internet встроенных DNS маршрутизации систем для поиска ближайших сервера пользователю. В этой статье примерах, как разницу между загрузка популярных библиотеку jQuery из SharePoint Online серверный или ASP CDN весьма значительным. Пользователь также уже может быть версии CDN, кэшируются на локальном компьютере, чтобы они не нужно загрузить файл. Это может быть важно, если у вас есть пользователи, распределенных по всему миру и далеко из центра обработки данных, на котором размещается сайт SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="8439b-p101">In today's web development communities, there are many common libraries (such as JavaScript and CSS files) that you may include in your SharePoint solution. Many of these are hosted by Microsoft on their ASP CDN. This means you can reference these libraries from these distributed servers and allow the internet's built-in DNS routing systems to find the closest server to your user. The examples in this article demonstrate how the time difference between downloading the popular library jQuery from the SharePoint Online server versus the ASP CDN is quite significant. The user also may already have the CDN version cached on the local computer so that they do not have to download the file. This can be important if you have users distributed all over the world and far away from the datacenter that hosts your SharePoint Online site.</span></span>
  
<span data-ttu-id="8439b-p102">При создании страниц для SharePoint Online задержка может зависеть от физического расстояния между пользователями и местоположением экземпляра SharePoint Online. Это особенно важно для организаций с наличием сети представительств во всех регионах мира, где сайт может размещаться на одном континенте, а пользователи, находящиеся на другом конце мира, пользуются его содержимым. Сети CDN помогают смягчить эту ситуацию, разместив некоторые популярные веб-активы в различных местах ближе к пользователю.</span><span class="sxs-lookup"><span data-stu-id="8439b-p102">When creating pages for SharePoint Online, latency can be affected by the physical distance between your users and the location of the SharePoint Online instance. This is particularly important for organizations that have a global presence where a site may be hosted on one continent while users on the other side of the world are accessing its content. CDNs help mitigate this situation by hosting certain popular web assets in different locations closer to the end users.</span></span>
  
<span data-ttu-id="8439b-p103">Так как CDN является всемирной сетью сервером, на которых размещаются одинаковые файлы, URL-адреса эти файлов, хранящиеся в сетях CDN, интерпретируются клиентской машиной таким образом, что файл обслуживается сервером, находящимся ближе всех к пользователю. Это значительно сокращает задержки, вызванные круговыми путями.</span><span class="sxs-lookup"><span data-stu-id="8439b-p103">Since a CDN is a worldwide network of servers that host the same files, Internet URLs for files stored on the CDNs are interpreted by the client machine so that the server that is closest to the user serves the file. Doing this significantly reduces delays caused by network round trips.</span></span>
  
## <a name="the-challenge-of-hosting-sharepoint-online-sites-for-a-global-audience"></a><span data-ttu-id="8439b-116">Задача размещения сайтов SharePoint для глобальной аудитории</span><span class="sxs-lookup"><span data-stu-id="8439b-116">The challenge of hosting SharePoint Online sites for a global audience</span></span>

<span data-ttu-id="8439b-p104">Сайты SharePoint Online размещаются в центрах данных относительно расположения (указанного пользователем), выбранного вами при входе с помощью Office 365. Например, если ваш сайт находится на сервере в Соединенных Штатах, а ваши пользователи обращаются к нему из Восточной Азии, проблемы с задержкой могут возникнуть из-за расстояния, которое данные должны пройти по оптоволоконному кабелю.</span><span class="sxs-lookup"><span data-stu-id="8439b-p104">SharePoint Online sites are hosted at datacenters relative to the location (specified by the user) selected when you signed up with Office 365. For example, if your site is on servers in the United States and you have users accessing the site from East Asia, latency issues might arise due to the distance the data has to travel over fiber optic cable.</span></span>
  
<span data-ttu-id="8439b-p105">Многие статические файлы, используемые с помощью пользовательского интерфейса SharePoint по умолчанию уже размещена в корпорации Майкрософт по всему миру сети CDN. Это улучшит производительность по времени. Тем не менее, если вы используете любой популярных ресурсов JavaScript и CSS (например; JQuery, Modernizr, начальной или ASP.NET Ajax) время загрузки этих файлов можно улучшить с помощью свободным CDN.</span><span class="sxs-lookup"><span data-stu-id="8439b-p105">Many static files used by the default SharePoint user interface are already hosted on Microsoft's worldwide network of CDNs. This will improve performance over time. However, if you use any popular JavaScript and CSS assets (for example; JQuery, Modernizr, Bootstrap, or ASP.NET Ajax) you can improve the loading times of these files by using freely available CDNs.</span></span>
  
## <a name="advantages-of-using-cdns-to-improve-download-speed"></a><span data-ttu-id="8439b-122">Преимущества использования сетей CDN для повышения скорости загрузки</span><span class="sxs-lookup"><span data-stu-id="8439b-122">Advantages of using CDNs to improve download speed</span></span>

<span data-ttu-id="8439b-p106">Использование CDN может увеличить время загрузки страницы при ряду причин. Одной из причин — это что расстояние между CDN и пользователь может быть меньше, чем расстояние для экземпляра SharePoint Online. Эти сети сильно распределенного и также учитывает имеют очень высокая доступность и значения времени ответа. Другой причиной является, если вы используете библиотеки популярные CSS-файлы, вместе с CDN пользователь уже может быть библиотеке кэширования и они даже не придется загрузить на всех.</span><span class="sxs-lookup"><span data-stu-id="8439b-p106">Using CDNs can improve page load times for a variety of reasons. One reason is that the distance between the CDN and the user may be shorter than the distance to the SharePoint Online instance. These networks are highly distributed and are also designed to have very high availability and response times. Another reason is that if you are using a popular library of CSS files, in conjunction with a CDN, the user may already have the library cached and they won't even need to download it at all.</span></span>
  
<span data-ttu-id="8439b-p107">На следующих снимках экрана показаны преимущества использования CDN. Эти снимки экрана, на вкладке **сети** возможности инструментов разработчика Internet Explorer 11. Эти снимках экрана задержка на популярные библиотеку jQuery. Для вызова этого экрана в Internet Explorer, нажмите клавишу **F12** и перейдите на вкладку **сети** , которая отображаемый со значком Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="8439b-p107">The following screen shots illustrate the advantages of using CDNs. These screen shots are from the **Network** tab in the Internet Explorer 11 developer tools. These screen shots show the latency on the popular library jQuery. To bring up this screen, in Internet Explorer, press **F12** and select the **Network** tab which is symbolized with a Wi-Fi icon.</span></span> 
  
![Снимок экрана: вкладка "Сеть", отобразившаяся после нажатия клавиши F12](media/930541fd-af9b-434a-ae18-7bda867be128.png)
  
<span data-ttu-id="8439b-p108">В этом снимке экрана показана библиотека, было выгрузить в коллекции главных страниц на самом сайте SharePoint Online. Время, затраченное на передачу в библиотеке — 1.51 секунд.</span><span class="sxs-lookup"><span data-stu-id="8439b-p108">This screen shot shows the library uploaded to the master page gallery on the SharePoint Online site itself. The time it took to upload the library is 1.51 seconds.</span></span>
  
![Снимок экрана: время загрузки 1,51 с](media/64225c79-fa53-480f-81cd-0d351674320e.png)
  
<span data-ttu-id="8439b-p109">На второй снимке экрана показан тот же файл, предоставляемых корпорации Майкрософт CDN. Данный момент задержка составляет около 496 миллисекундах. Это большой улучшения, показывает, что вся секунды — это shaved общее время для загрузки содержимого страницы.</span><span class="sxs-lookup"><span data-stu-id="8439b-p109">The second screen shot shows the same file delivered by Microsoft's CDN. This time the latency is around 496 milliseconds. This is a large improvement and shows that a whole second is shaved off the total time to download the page content.</span></span>
  
![Снимок экрана: время загрузки 469 мс](media/6a553cc3-25a0-42c1-aae7-4aebbc2eb4c3.png)
  
## <a name="using-cdns-with-sharepoint-server-2013"></a><span data-ttu-id="8439b-139">Использование CDN с SharePoint Server 2013</span><span class="sxs-lookup"><span data-stu-id="8439b-139">Using CDNs with SharePoint Server 2013</span></span>

<span data-ttu-id="8439b-p110">Только с помощью CDN смысл в SharePoint Online контекста и следует избегать с SharePoint Server 2013. Это не все преимущества вокруг географическое положение удержание значение true, если сервер не расположен в локальной или географически закрыть в любом случае. Кроме того Если сетевое подключение на серверах, где размещена, сайта могут использоваться без подключения к Интернету и таким образом, не удается извлечь файлы CDN. В противном случае следует использовать CDN, если один существует и с достаточно постоянным для библиотеки и файлы, необходимые для веб-узла.</span><span class="sxs-lookup"><span data-stu-id="8439b-p110">Using CDNs only makes sense in a SharePoint Online context and should be avoided with SharePoint Server 2013. This is because all of the advantages around geographic location do not hold true if the server is located on-premises or geographically close anyway. Additionally, if there is a network connection to the servers where it's hosted, then the site may be used without an Internet connection and therefore cannot retrieve the CDN files. Otherwise, you should use a CDN if there is one available and stable for the library and files you need for your site.</span></span>
  
## <a name="popular-cdns-and-how-to-use-them"></a><span data-ttu-id="8439b-144">Популярные CDN и их использование</span><span class="sxs-lookup"><span data-stu-id="8439b-144">Popular CDNs and how to use them</span></span>

<span data-ttu-id="8439b-145">Ajax CDN корпорации Майкрософт предлагает наиболее популярные библиотек, включая jQuery (и все его библиотек), ASP.NET Ajax, загрузки, Knockout.js и многое другое.</span><span class="sxs-lookup"><span data-stu-id="8439b-145">Microsoft's Ajax CDN offers most of the popular libraries including jQuery (and all of its other libraries), ASP.NET Ajax, Bootstrap, Knockout.js, and many more.</span></span>
  
<span data-ttu-id="8439b-p111">Чтобы включить эти скрипты в свой проект, просто замените любые ссылки на эти публично доступные библиотеки с помощью ссылок на адрес CDN вместо того, чтобы включать их в сам проект. Например, для ссылки на jQuery используйте следующий код:</span><span class="sxs-lookup"><span data-stu-id="8439b-p111">To include these scripts in your project, simply replace any references to these publicly available libraries with references to the CDN address instead of including it in your project itself. For example, use the following code to link to jQuery:</span></span>
  
```
<script src=http://ajax.aspnetcdn.com/ajax/jquery-2.1.1.js> </script>
```

<span data-ttu-id="8439b-148">Дополнительные сведения о CDN можно [сети доставки содержимого](content-delivery-networks.md).</span><span class="sxs-lookup"><span data-stu-id="8439b-148">For more information about CDNs, see [Content delivery networks](content-delivery-networks.md).</span></span>
  
## <a name="more-topics-about-using-cdns-with-sharepoint"></a><span data-ttu-id="8439b-149">Дополнительные разделы, посвященные использованию CDN с SharePoint</span><span class="sxs-lookup"><span data-stu-id="8439b-149">More topics about using CDNs with SharePoint</span></span>

[<span data-ttu-id="8439b-150">Размещение клиентских веб-части из сети CDN Office 365</span><span class="sxs-lookup"><span data-stu-id="8439b-150">Hosting client-side web part from Office 365 CDN</span></span>](https://dev.office.com/sharepoint/docs/spfx/web-parts/get-started/hosting-webpart-from-office-365-cdn)
  

