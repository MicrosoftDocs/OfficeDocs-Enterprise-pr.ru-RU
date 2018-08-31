---
title: Задержка при загрузке изображений и JavaScript-файлов в SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 12/29/2016
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 74d327e5-755f-4135-b9a5-7b79578c1bf9
description: В этой статье описывается, как можно уменьшить время загрузки для страниц SharePoint Online с помощью JavaScript задержку загрузка изображений, а также путем ожидания загрузить JavaScript Неосновные до после загрузки страницы.
ms.openlocfilehash: b8b052d85c99e51dff4b0fc747b3b52c17de8d8b
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542541"
---
# <a name="delay-loading-images-and-javascript-in-sharepoint-online"></a><span data-ttu-id="9538e-103">Задержка при загрузке изображений и JavaScript-файлов в SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="9538e-103">Delay loading images and JavaScript in SharePoint Online</span></span>

<span data-ttu-id="9538e-104">В этой статье описывается, как можно уменьшить время загрузки для страниц SharePoint Online с помощью JavaScript задержку загрузка изображений, а также путем ожидания загрузить JavaScript Неосновные до после загрузки страницы.</span><span class="sxs-lookup"><span data-stu-id="9538e-104">This article describes how you can decrease the load time for SharePoint Online pages by using JavaScript to delay loading images and also by waiting to load non-essential JavaScript until after the page loads.</span></span> 
  
<span data-ttu-id="9538e-p101">Изображения могут негативно повлиять на скорость загрузки страницы на SharePoint Online. По умолчанию большинство современных интернет-браузеров при загрузке HTML-страницы предварительно запрашивают изображения. Это может привести к тому, что страница будет загружаться очень медленно, если изображения не видны на экране до тех пор, пока пользователь не прокрутит страницу вниз. Изображения могут блокировать загрузку видимых частей страницы в браузере. Для обхода этой проблемы можно использовать JavaScript, чтобы пропустить первоочередную загрузку изображений. Кроме того, загрузка несущественных JavaScript также может увеличить время загрузки страниц SharePoint. В данной статье описаны некоторые методы, позволяющие улучшить время загрузки в SharePoint Online с помощью JavaScript.</span><span class="sxs-lookup"><span data-stu-id="9538e-p101">Images can negatively affect page load speeds on SharePoint Online. By default, most modern Internet browsers pre-fetch images when loading an HTML page. This can cause the page to be unnecessarily slow to load if the images are not visible on the screen until the user scrolls down. The images can block the browser from loading the visible part of the page. To work around this problem, you can use JavaScript to skip loading the images first. Also, loading non-essential JavaScript can slow down load times on your SharePoint pages too. This topic describes some methods you can use to improve page load times with JavaScript in SharePoint Online.</span></span> 
  
## <a name="improve-page-load-times-by-delaying-image-loading-in-sharepoint-online-pages-by-using-javascript"></a><span data-ttu-id="9538e-112">Улучшение времени загрузки за счет задержки загрузки изображений на страницах SharePoint Online с помощью JavaScript</span><span class="sxs-lookup"><span data-stu-id="9538e-112">Improve page load times by delaying image loading in SharePoint Online pages by using JavaScript</span></span>

<span data-ttu-id="9538e-p102">Чтобы запретить веб-браузера из предварительно выборку изображений можно использовать JavaScript. Это ускоряет общую визуализацию документа. Для этого удалите значение атрибута src из \<img\> тега и укажите путь к файлу в атрибуте данных таких как: данные src. Например:</span><span class="sxs-lookup"><span data-stu-id="9538e-p102">You can use JavaScript to prevent a web browser from pre-fetching images. This speeds up overall document rendering. To do this you remove the value of the src attribute from the \<img\> tag and replace it with the path to a file in a data attribute such as: data-src. For example:</span></span>
  
```
<img src="" data-src="/sites/NavigationBySearch/_catalogs/masterpage/media/microsoft-white-8.jpg" />
```

<span data-ttu-id="9538e-p103">С помощью этого метода, браузер не сразу же загрузки изображений. Если изображение уже в окне просмотра JavaScript сообщает о том, браузер для получения URL-адрес из атрибута данных и вставьте его в качестве значения для атрибута src. Изображение загружает только прокрутке пользователем и переходит в представление.</span><span class="sxs-lookup"><span data-stu-id="9538e-p103">By using this method, the browser doesn't download the images immediately. If the image is already in the viewport, JavaScript tells the browser to retrieve the URL from the data attribute and insert it as the value for the src attribute. The image only loads as the user scrolls and it comes into view.</span></span>
  
<span data-ttu-id="9538e-119">Чтобы сделать все это произойдет, вам потребуются использование JavaScript.</span><span class="sxs-lookup"><span data-stu-id="9538e-119">To make all of this happen, you'll need to use JavaScript.</span></span>
  
<span data-ttu-id="9538e-120">В текстовом файле определите функцию **isElementInViewport()**, которая проверяет, относится ли элемент к видимой для пользователя части браузера.</span><span class="sxs-lookup"><span data-stu-id="9538e-120">In a text file, define the **isElementInViewport()** function to check whether or not an element is in the part of the browser that is visible to the user.</span></span> 
  
```
function isElementInViewport(el) {
  if (!el)
    return false;
  var rect = el.getBoundingClientRect();
  return (
    rect.top >= 0 &amp;&amp;
    rect.left >= 0 &amp;&amp;
    rect.bottom <= (window.innerHeight || document.documentElement.clientHeight) &amp;&amp;
    rect.right <= (window.innerWidth || document.documentElement.clientWidth) 
  );
}

```

<span data-ttu-id="9538e-p104">Далее используйте **isElementInViewport()** в функции **loadItemsInView()**. Функция **loadItemsInView()** будет загружать все изображения, которые имеют значение для атрибута data-src, если они являются видимой для пользователя частью браузера. Добавьте в текстовый файл следующую функцию:</span><span class="sxs-lookup"><span data-stu-id="9538e-p104">Next, use **isElementInViewport()** in the **loadItemsInView()** function. The **loadItemsInView()** function will load all images that have a value for the data-src attribute if they are in the part of the browser that is visible to the user. Add the following function to the text file:</span></span> 
  
```
function loadItemsInView() {
  //Select elements by the row id.
  $("#row [data-src]").each(function () {
      var isVisible = isElementInViewport(this);
      if (isVisible) {
          if ($(this).attr("src") == undefined) {
              $(this).attr("src", $(this).data("src"));
          }
      }
  });
}
```

<span data-ttu-id="9538e-p105">Вызовите функцию **loadItemsInView()** из **window.onscroll()**, как это показано в следующем примере. Благодаря этому любые изображения, которые находятся в окне просмотра, загружаются по мере необходимости, а не заранее. Добавьте в текстовый файл следующий код:</span><span class="sxs-lookup"><span data-stu-id="9538e-p105">Finally, call **loadItemsInView()** from within **window.onscroll()** as shown in the following example. This ensures that any images that are in the viewport are loaded as the user needs them, but not before. Add the following to the text file:</span></span> 
  
```
//Example of calling loadItemsInView() from within window.onscroll()
$(window).on("scroll", function () {
    loadItemsInView();
});

```

<span data-ttu-id="9538e-p106">Для SharePoint Online, необходимо подключить следующая функция событие scroll #s4 workspace \<div\> тег. Это события окна переопределяются Луна ленты остается подключенным к верхней части страницы.</span><span class="sxs-lookup"><span data-stu-id="9538e-p106">For SharePoint Online, you need to attach the following function to the scroll event on the #s4-workspace \<div\> tag. This is because the window events are overridden in order to ensure the ribbon remains attached to the top of the page.</span></span>
  
```
//Keep the ribbon at the top of the page
$('#s4-workspace').on("scroll", function () {
    loadItemsInView();
});
```

<span data-ttu-id="9538e-129">Сохраните текстовый файл в виде JavaScript-файла с расширением JS, например delayLoadImages.js.</span><span class="sxs-lookup"><span data-stu-id="9538e-129">Save the text file as a JavaScript file with the extension .js, for example delayLoadImages.js.</span></span>
  
<span data-ttu-id="9538e-p107">После завершения написания delayLoadImages.js можно добавить содержимое файла в главную страницу в SharePoint Online. Это делается путем добавления ссылки на сценарий верхнего колонтитула в главную страницу. После загрузки его в главную страницу, JavaScript будет применяться к все страницы на сайте SharePoint Online, которые используют главную страницу макета. Кроме того Если планируется использовать только на одной странице веб-узла, используйте редактор сценариев веб-части для внедрения JavaScript в страницу. Для получения дополнительных сведений см.</span><span class="sxs-lookup"><span data-stu-id="9538e-p107">Once you've finished writing delayLoadImages.js, you can add the contents of the file to a master page in SharePoint Online. You do this by adding a script link to the header in the master page. Once it's in a master page, the JavaScript will be applied to all pages in your SharePoint Online site that use that master page layout. Alternatively, if you intend to only use this on one page of your site, use the script editor Web Part to embed the JavaScript into the page. See these topics for more information:</span></span>
  
- [<span data-ttu-id="9538e-135">Как: применение главной страницы сайта в SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="9538e-135">How to: Apply a master page to a site in SharePoint 2013</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=525627)
    
- [<span data-ttu-id="9538e-136">Как: создать макет страницы в SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="9538e-136">How to: Create a page layout in SharePoint 2013</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=525628)
    
 <span data-ttu-id="9538e-137">**Пример: ссылка на JavaScript-файл delayLoadImages.js из эталонной страницы в SharePoint Online**</span><span class="sxs-lookup"><span data-stu-id="9538e-137">**Example: Referencing the JavaScript delayLoadImages.js file from a master page in SharePoint Online**</span></span>
  
<span data-ttu-id="9538e-p108">Чтобы этот метод заработал, вам также необходимо упомянуть jQuery на эталонной странице. В следующем примере вы можете видеть в загрузке начальной страницы только одно изображение, однако на этой странице их несколько.</span><span class="sxs-lookup"><span data-stu-id="9538e-p108">In order for this to work, you also need to reference jQuery in the master page. In the following example, you can see in the initial page load that there is only one image loaded but there are several more on the page.</span></span>
  
![Снимок экрана: одно изображение загружено на странице](media/3d177ddb-67e5-43a7-b327-c9f9566ca937.png)
  
<span data-ttu-id="9538e-141">На следующем снимке экрана показаны оставшиеся изображения, которые скачиваются после того, как попадают в область просмотра.</span><span class="sxs-lookup"><span data-stu-id="9538e-141">The following screen shot shows the rest of the images that are downloaded after they scroll into view.</span></span>
  
![Снимок экрана: несколько изображений загружено на странице](media/95eb2b14-f6a1-4eac-a5cb-96097e49514c.png)
  
<span data-ttu-id="9538e-p109">Задержка загрузки изображений с использованием JavaScript может быть эффективным способом увеличения производительности. Однако, если этот способ применяется на общедоступном веб-сайте, то поисковые системы не могут выполнить обход изображений таким же образом, как это выполняется при стандартно сформированном изображении. Это может повлиять на ранжирование в поисковых системах, так как пока страница не загрузится, метаданных самого изображения там нет. Программы-обходчики поисковых систем считывают только HTML, поэтому они не увидят изображения в виде контента страницы. Изображения являются одним из факторов, используемых при ранжировании страниц в результатах поиска. Один из способов обойти данную проблему — это использовать вводный текст для изображений.</span><span class="sxs-lookup"><span data-stu-id="9538e-p109">Delaying image loading by using JavaScript can be an effective technique in increasing performance; however, if the technique is applied on a public website then search engines are not able to crawl the images in the same way they would crawl a regularly formed image. This can affect rankings on search engines because metadata on the image itself is not really there until the page loads. Search engine crawlers only read the HTML and therefore will not see the images as content on the page. Images are one of the factors used to rank pages in search results. One way to work around this is to use introductory text for your images.</span></span>
  
## <a name="github-code-sample-injecting-javascript-to-improve-performance"></a><span data-ttu-id="9538e-148">Пример кода GitHub: Добавление кода JavaScript для повышения производительности</span><span class="sxs-lookup"><span data-stu-id="9538e-148">GitHub code sample: Injecting JavaScript to improve performance</span></span>

<span data-ttu-id="9538e-149">Не пропустите статья и пример кода на [JavaScript ввод данных](https://go.microsoft.com/fwlink/p/?LinkId=524759) на репозиториев.</span><span class="sxs-lookup"><span data-stu-id="9538e-149">Don't miss the article and code sample on [JavaScript injection](https://go.microsoft.com/fwlink/p/?LinkId=524759) provided on GitHub.</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="9538e-150">См. также</span><span class="sxs-lookup"><span data-stu-id="9538e-150">See also</span></span>

[<span data-ttu-id="9538e-151">Поддерживаемые браузеры в Office 2013 и Office 365 профессиональный плюс</span><span class="sxs-lookup"><span data-stu-id="9538e-151">Supported browsers in Office 2013 and Office 365 ProPlus</span></span>](https://support.office.com/article/57342811-0dc4-4316-b773-20082ced8a82)
  
[<span data-ttu-id="9538e-152">Как: применение главной страницы сайта в SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="9538e-152">How to: Apply a master page to a site in SharePoint 2013</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=525627)
  
[<span data-ttu-id="9538e-153">Как: создать макет страницы в SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="9538e-153">How to: Create a page layout in SharePoint 2013</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=525628)

