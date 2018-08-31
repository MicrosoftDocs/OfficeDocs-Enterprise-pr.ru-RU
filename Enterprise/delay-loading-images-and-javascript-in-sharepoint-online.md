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
# <a name="delay-loading-images-and-javascript-in-sharepoint-online"></a>Задержка при загрузке изображений и JavaScript-файлов в SharePoint Online

В этой статье описывается, как можно уменьшить время загрузки для страниц SharePoint Online с помощью JavaScript задержку загрузка изображений, а также путем ожидания загрузить JavaScript Неосновные до после загрузки страницы. 
  
Изображения могут негативно повлиять на скорость загрузки страницы на SharePoint Online. По умолчанию большинство современных интернет-браузеров при загрузке HTML-страницы предварительно запрашивают изображения. Это может привести к тому, что страница будет загружаться очень медленно, если изображения не видны на экране до тех пор, пока пользователь не прокрутит страницу вниз. Изображения могут блокировать загрузку видимых частей страницы в браузере. Для обхода этой проблемы можно использовать JavaScript, чтобы пропустить первоочередную загрузку изображений. Кроме того, загрузка несущественных JavaScript также может увеличить время загрузки страниц SharePoint. В данной статье описаны некоторые методы, позволяющие улучшить время загрузки в SharePoint Online с помощью JavaScript. 
  
## <a name="improve-page-load-times-by-delaying-image-loading-in-sharepoint-online-pages-by-using-javascript"></a>Улучшение времени загрузки за счет задержки загрузки изображений на страницах SharePoint Online с помощью JavaScript

Чтобы запретить веб-браузера из предварительно выборку изображений можно использовать JavaScript. Это ускоряет общую визуализацию документа. Для этого удалите значение атрибута src из \<img\> тега и укажите путь к файлу в атрибуте данных таких как: данные src. Например:
  
```
<img src="" data-src="/sites/NavigationBySearch/_catalogs/masterpage/media/microsoft-white-8.jpg" />
```

С помощью этого метода, браузер не сразу же загрузки изображений. Если изображение уже в окне просмотра JavaScript сообщает о том, браузер для получения URL-адрес из атрибута данных и вставьте его в качестве значения для атрибута src. Изображение загружает только прокрутке пользователем и переходит в представление.
  
Чтобы сделать все это произойдет, вам потребуются использование JavaScript.
  
В текстовом файле определите функцию **isElementInViewport()**, которая проверяет, относится ли элемент к видимой для пользователя части браузера. 
  
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

Далее используйте **isElementInViewport()** в функции **loadItemsInView()**. Функция **loadItemsInView()** будет загружать все изображения, которые имеют значение для атрибута data-src, если они являются видимой для пользователя частью браузера. Добавьте в текстовый файл следующую функцию: 
  
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

Вызовите функцию **loadItemsInView()** из **window.onscroll()**, как это показано в следующем примере. Благодаря этому любые изображения, которые находятся в окне просмотра, загружаются по мере необходимости, а не заранее. Добавьте в текстовый файл следующий код: 
  
```
//Example of calling loadItemsInView() from within window.onscroll()
$(window).on("scroll", function () {
    loadItemsInView();
});

```

Для SharePoint Online, необходимо подключить следующая функция событие scroll #s4 workspace \<div\> тег. Это события окна переопределяются Луна ленты остается подключенным к верхней части страницы.
  
```
//Keep the ribbon at the top of the page
$('#s4-workspace').on("scroll", function () {
    loadItemsInView();
});
```

Сохраните текстовый файл в виде JavaScript-файла с расширением JS, например delayLoadImages.js.
  
После завершения написания delayLoadImages.js можно добавить содержимое файла в главную страницу в SharePoint Online. Это делается путем добавления ссылки на сценарий верхнего колонтитула в главную страницу. После загрузки его в главную страницу, JavaScript будет применяться к все страницы на сайте SharePoint Online, которые используют главную страницу макета. Кроме того Если планируется использовать только на одной странице веб-узла, используйте редактор сценариев веб-части для внедрения JavaScript в страницу. Для получения дополнительных сведений см.
  
- [Как: применение главной страницы сайта в SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=525627)
    
- [Как: создать макет страницы в SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=525628)
    
 **Пример: ссылка на JavaScript-файл delayLoadImages.js из эталонной страницы в SharePoint Online**
  
Чтобы этот метод заработал, вам также необходимо упомянуть jQuery на эталонной странице. В следующем примере вы можете видеть в загрузке начальной страницы только одно изображение, однако на этой странице их несколько.
  
![Снимок экрана: одно изображение загружено на странице](media/3d177ddb-67e5-43a7-b327-c9f9566ca937.png)
  
На следующем снимке экрана показаны оставшиеся изображения, которые скачиваются после того, как попадают в область просмотра.
  
![Снимок экрана: несколько изображений загружено на странице](media/95eb2b14-f6a1-4eac-a5cb-96097e49514c.png)
  
Задержка загрузки изображений с использованием JavaScript может быть эффективным способом увеличения производительности. Однако, если этот способ применяется на общедоступном веб-сайте, то поисковые системы не могут выполнить обход изображений таким же образом, как это выполняется при стандартно сформированном изображении. Это может повлиять на ранжирование в поисковых системах, так как пока страница не загрузится, метаданных самого изображения там нет. Программы-обходчики поисковых систем считывают только HTML, поэтому они не увидят изображения в виде контента страницы. Изображения являются одним из факторов, используемых при ранжировании страниц в результатах поиска. Один из способов обойти данную проблему — это использовать вводный текст для изображений.
  
## <a name="github-code-sample-injecting-javascript-to-improve-performance"></a>Пример кода GitHub: Добавление кода JavaScript для повышения производительности

Не пропустите статья и пример кода на [JavaScript ввод данных](https://go.microsoft.com/fwlink/p/?LinkId=524759) на репозиториев. 
  
## <a name="see-also"></a>См. также

[Поддерживаемые браузеры в Office 2013 и Office 365 профессиональный плюс](https://support.office.com/article/57342811-0dc4-4316-b773-20082ced8a82)
  
[Как: применение главной страницы сайта в SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=525627)
  
[Как: создать макет страницы в SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=525628)

