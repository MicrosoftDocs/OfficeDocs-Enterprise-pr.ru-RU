---
title: Минификация и объединение в SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 3/1/2017
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 87a52468-994e-43a2-b155-7229ed659291
description: В этой статье описывается, как использовать иными и объединения методики с помощью Web Essentials сократить число HTTP-запросов и сократить время, необходимое для загрузки страниц в SharePoint Online.
ms.openlocfilehash: edc959e881b0f22b72fba64969e5984f30bce696
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542291"
---
# <a name="minification-and-bundling-in-sharepoint-online"></a><span data-ttu-id="f771c-103">Минификация и объединение в SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="f771c-103">Minification and bundling in SharePoint Online</span></span>

<span data-ttu-id="f771c-104">В этой статье описывается, как использовать иными и объединения методики с помощью Web Essentials сократить число HTTP-запросов и сократить время, необходимое для загрузки страниц в SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="f771c-104">This article describes how to use minification and bundling techniques with Web Essentials to reduce the number of HTTP requests and to reduce the time it takes to load pages in SharePoint Online.</span></span>
  
<span data-ttu-id="f771c-p101">Когда вы настраиваете свой веб-сайт, вы можете прийти к добавлению большого количества дополнительных файлов на сервер для поддержки этой настройки. Добавление дополнительных CSS- и JavaScript-файлов, изображений увеличивает количество HTTP-запросов на сервер, что в свою очередь увеличивает время, необходимое для отображения веб-страницы. Чтобы несколько файлов одного типа скачивались быстрее, их можно объединить.</span><span class="sxs-lookup"><span data-stu-id="f771c-p101">When you customize your website you can end up adding a large number of extra files to the server to support the customization. Adding extra JavaScript, CSS, and images increases the number of HTTP requests to the server which in turn increases the time it takes to display a web page. If you have multiple files of the same type, you can bundle these files to make downloading these files faster.</span></span>
  
<span data-ttu-id="f771c-108">Для JavaScript и CSS-файлов можно также использовать подход, называется иными, где уменьшить размер файлов путем удаления пробелов и других знаков, которых нет необходимости.</span><span class="sxs-lookup"><span data-stu-id="f771c-108">For JavaScript and CSS files, you can also use an approach called minification, where you reduce the total size of files by removing whitespace and other characters that aren't necessary.</span></span>
  
## <a name="minification-and-bundling-javascript-and-css-files-with-web-essentials"></a><span data-ttu-id="f771c-109">Минификация и объединение CSS- и JavaScript-файлов с помощью Web Essentials</span><span class="sxs-lookup"><span data-stu-id="f771c-109">Minification and bundling JavaScript and CSS files with Web Essentials</span></span>

<span data-ttu-id="f771c-110">Для объединения CSS- и JavaScript-файлов можно использовать программное обеспечение сторонних производителей, например Web Essentials.</span><span class="sxs-lookup"><span data-stu-id="f771c-110">You can use third-party software such as Web Essentials to bundle CSS and JavaScript files.</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="f771c-p102">Основы Web является сторонних производителей, открытая, на основе сообщества project. Программное обеспечение — это расширение для Visual Studio 2012 и Visual Studio 2013 и не поддерживается корпорацией Майкрософт. Чтобы загрузить Web Essentials, посетите веб-сайте по [http://vswebessentials.com/download](https://go.microsoft.com/fwlink/p/?LinkId=525629).</span><span class="sxs-lookup"><span data-stu-id="f771c-p102">Web Essentials is a third-party, open-source, community-based project. The software is an extension to Visual Studio 2012 and Visual Studio 2013 and is not supported by Microsoft. To download Web Essentials, visit the website at [http://vswebessentials.com/download](https://go.microsoft.com/fwlink/p/?LinkId=525629).</span></span> 
  
<span data-ttu-id="f771c-114">В Web Essentials доступны два формата для объединения:</span><span class="sxs-lookup"><span data-stu-id="f771c-114">Web Essentials offers two forms of bundling:</span></span>
  
- <span data-ttu-id="f771c-115">BUNDLE — для файлов CSS и JavaScript;</span><span class="sxs-lookup"><span data-stu-id="f771c-115">.bundle: for CSS and JavaScript files</span></span>
    
- <span data-ttu-id="f771c-116">SPRITE — для изображений (доступно только в Visual Studio 2013).</span><span class="sxs-lookup"><span data-stu-id="f771c-116">.sprite: for images (only available in Visual Studio 2013)</span></span>
    
<span data-ttu-id="f771c-117">Вы можете использовать Web Essentials, если у вас есть функция с несколькими фирменными элементами, на которые ссылается пользовательская эталонная страница, например:</span><span class="sxs-lookup"><span data-stu-id="f771c-117">You can use Web Essentials if you have an existing feature with some branding elements that are referenced inside a custom master page, such as:</span></span>
  
![Снимок экрана: элемент фирменной символики на настраиваемой эталонной странице](media/3a6eba36-973d-482b-8556-a9394b8ba19f.png)
  
 <span data-ttu-id="f771c-119">**Для создания пакета TE000127218 и CSS в Web Essentials**</span><span class="sxs-lookup"><span data-stu-id="f771c-119">**To create a TE000127218 and CSS bundle in Web Essentials**</span></span>
  
1. <span data-ttu-id="f771c-120">В обозревателе решений в Visual Studio выберите файлы, которые нужно объединить.</span><span class="sxs-lookup"><span data-stu-id="f771c-120">In Visual Studio, in Solution Explorer, select the files that you want to include in the bundle.</span></span>
    
2. <span data-ttu-id="f771c-p103">Щелкните правой кнопкой мыши выбранных файлов, а затем выберите **Web Essentials** \> **файл пакета создания JavaScript** в контекстном меню. Например:</span><span class="sxs-lookup"><span data-stu-id="f771c-p103">Right-click the selected files and then select **Web Essentials** \> **Create JavaScript bundle file** from the context menu. For example:</span></span> 
    
    ![Снимок экрана: параметры меню Web Essentials](media/41aac84c-4538-4f78-b454-46e651f868a3.png)
  
## <a name="viewing-the-results-of-bundling-javascript-and-css-files"></a><span data-ttu-id="f771c-124">Просмотр результатов объединения CSS- и JavaScript-файлов</span><span class="sxs-lookup"><span data-stu-id="f771c-124">Viewing the results of bundling JavaScript and CSS files</span></span>

<span data-ttu-id="f771c-125">Когда вы объединяете CSS- и JavaScript-файлы, Web Essentials создает XML-файл, называемый файлом инструкций. Он идентифицирует CSS- и JavaScript-файлы, а также некоторую другую информацию:</span><span class="sxs-lookup"><span data-stu-id="f771c-125">When you create a JavaScript and CSS bundle, Web Essentials creates an XML file called a recipe file that identifies the JavaScript and CSS files as well as some other configuration information:</span></span> 
  
![Снимок экрана: файл инструкций JavaScript и CSS](media/7ba891f8-52d8-467b-a0f6-b062dd1137a4.png)
  
<span data-ttu-id="f771c-p104">Кроме того, если в инструкции объединения значение флага минификации установлено как "true", то эти файлы будут уменьшены в размере и объединены. Это значит, что будут созданы новые, минифицированные версии JavaScript-файлов, на которые может ссылаться эталонная страница.</span><span class="sxs-lookup"><span data-stu-id="f771c-p104">In addition, if the minify flag is set to true in the bundling recipe the files are reduced in size as well as bundled together. This means that new, minified versions of the JavaScript files were created that you can reference in your master page.</span></span>
  
![Снимок экрана: флаг минификации со значением true](media/50523af2-6412-4117-ac3d-5bd26f6d562e.png)
  
<span data-ttu-id="f771c-130">Когда вы загружаете страницу со своего веб-сайта, вы можете использовать средства разработчика в своем веб-браузере, например Internet Explorer 11, чтобы увидеть количество запросов, отправленных на сервер, и время загрузки каждого файла.</span><span class="sxs-lookup"><span data-stu-id="f771c-130">When you load a page from your web site, you can use the developer tools from your web browser, such as Internet Explorer 11, to see the number of requests sent to the server and how long each file took to load.</span></span>
  
<span data-ttu-id="f771c-131">На рисунке ниже представлен результат загрузки CSS- и JavaScript-файлов до минификации.</span><span class="sxs-lookup"><span data-stu-id="f771c-131">The following figure is the result of loading the JavaScript and CSS files before minification.</span></span>
  
![Снимок экрана: скачивание 80 элементов](media/e2df3912-1923-46e6-8cf2-3015a31554e1.png)
  
<span data-ttu-id="f771c-133">После объединения CSS- и JavaScript-файлов количество запросов сократилось до 74, а время загрузки файла только немного увеличилось по сравнению с загрузкой исходных файлов по отдельности:</span><span class="sxs-lookup"><span data-stu-id="f771c-133">After bundling the CSS and JavaScript files together, the number of requests dropped to 74 and each file took only slightly longer than the original files to download individually:</span></span>
  
![Снимок экрана: скачивание 74 элементов](media/686c4387-70e8-4a74-9d45-059f33a91184.png)
  
<span data-ttu-id="f771c-135">После объединения JavaScript-файлы значительно уменьшились в размере (с 815 КБ до 365 КБ):</span><span class="sxs-lookup"><span data-stu-id="f771c-135">After bundling, the JavaScript bundle file is reduced significantly from 815KB to 365KB:</span></span>
  
![Снимок экрана: сокращение размера скачиваемых элементов](media/5e7dbd98-faff-4f68-b320-108fb252e395.png)
  
## <a name="bundling-images-by-creating-an-image-sprite"></a><span data-ttu-id="f771c-137">Объединение изображений путем создания спрайта изображений</span><span class="sxs-lookup"><span data-stu-id="f771c-137">Bundling images by creating an image sprite</span></span>

<span data-ttu-id="f771c-p105">Как и как объединяют файлы JavaScript и CSS, можно объединить множество небольших значки и другие общие изображения в увеличенного sprite и затем Показать отдельных изображений с помощью CSS. Вместо загрузки каждого отдельного изображения, веб-браузер пользователя загружает таблицы sprite один раз и кэширует его на локальном компьютере. Это повышает производительность загрузки страницы, снижают вниз на количество обращений к веб-сервера и файлы для загрузки.</span><span class="sxs-lookup"><span data-stu-id="f771c-p105">Similar to how you bundle JavaScript and CSS files, you can combine many small icons and other common images into a larger sprite sheet and then use CSS to reveal the individual images. Instead of downloading each individual image, the user's web browser downloads the sprite sheet once and then caches it on the local computer. This improves page load performance by cutting down on the number of downloads and round trips to the web server.</span></span>
  
 <span data-ttu-id="f771c-141">**Создание спрайта изображений в Web Essentials**</span><span class="sxs-lookup"><span data-stu-id="f771c-141">**To create an image sprite in Web Essentials**</span></span>
  
1. <span data-ttu-id="f771c-142">В обозревателе решений в Visual Studio выберите файлы, которые нужно объединить.</span><span class="sxs-lookup"><span data-stu-id="f771c-142">In Visual Studio, in Solution Explorer, select the files that you want to include in the bundle.</span></span>
    
2. <span data-ttu-id="f771c-p106">Щелкните правой кнопкой мыши выбранных файлов, а затем выберите **Web Essentials** \> **Создать изображение sprite** в контекстном меню. Например:</span><span class="sxs-lookup"><span data-stu-id="f771c-p106">Right-click the selected files and then select **Web Essentials** \> **Create image sprite** from the context menu. For example:</span></span> 
    
    ![Снимок экрана: как создать спрайт изображения](media/de0fe741-4ef7-4e3b-bafa-ef9f4822dac6.png)
  
3. <span data-ttu-id="f771c-p107">Выберите расположение для сохранения файла спрайта. SPRITE-файл — это XML-файл, описывающий настройки и файлы в спрайте. На следующих рисунках в качестве примера показаны файл спрайта в формате PNG и соответствующий ему XML-файл с расширением SPRITE.</span><span class="sxs-lookup"><span data-stu-id="f771c-p107">Choose a location to save the sprite file. The .sprite file is an XML file that describes the settings and files in the sprite. The following figures show an example of a sprite PNG file and its corresponding .sprite XML file.</span></span>
    
    ![Снимок экрана: файл спрайта](media/0876bb2a-d1b9-4169-8e95-9c290d628d90.png)
  
    ![Снимок экрана: XML-файл спрайта](media/d1f94776-280d-4d56-abb5-384f145d9989.png)
  

