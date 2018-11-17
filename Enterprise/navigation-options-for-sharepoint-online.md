---
title: Параметры навигации для SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: adb92b80-b342-4ecb-99a1-da2a2b4782eb
description: В этой статье описываются сайты параметры навигации с публикации SharePoint включен в SharePoint Online. Выбор и настройка навигации заметно влияет на производительность и масштабируемость сайтов в SharePoint Online.
ms.openlocfilehash: 5a190ca643c20b6644ca1eecdac2a4a2e281a09e
ms.sourcegitcommit: 45633b7034ee98d0cd833db9743f283b638237f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "26547181"
---
# <a name="navigation-options-for-sharepoint-online"></a>Параметры навигации для SharePoint Online

В этой статье описываются сайты параметры навигации с публикации SharePoint включен в SharePoint Online. Выбор и настройка навигации заметно влияет на производительность и масштабируемость сайтов в SharePoint Online.

## <a name="overview"></a>Общие сведения

Конфигурации поставщика навигации можно значительно повысить производительность для всего сайта и тщательного анализа необходимо выполнить, чтобы выбрать поставщика навигации и конфигурации, масштабируется эффективно требования к сайту SharePoint. Существует два поставщиков ожидания введите навигации, а также реализации пользовательских переходов.

Первый вариант [**навигации Managed (метаданные)**](#using-managed-navigation-and-metadata-in-sharepoint-online), рекомендуется и — это один из параметров по умолчанию в SharePoint Online; Тем не менее рекомендуется отключить фильтрацию по ролям безопасности, если не требуется. Фильтрация по ролям безопасности используется в качестве параметров безопасности по умолчанию для данного поставщика навигации; количество сайтов не требуется дополнительная нагрузка безопасности обрезки с момента элементы навигации часто являются согласованными для всех пользователей сайта. Рекомендуемая конфигурация для отключения фильтрации по ролям безопасности данного поставщика навигации не требует перечисление структуры сайта и хорошо масштабируемое с приемлемой производительности.

Второй вариант [**структуры навигации**](#using-structural-navigation-in-sharepoint-online), **это не рекомендуется навигации в SharePoint Online**. В этом поставщика навигации был разработан для локальной топологии с ограниченными поддержки в SharePoint Online. Он обеспечивает некоторые дополнительные набор возможностей и других параметров навигации, эти функции, включая фильтрация по ролям безопасности и перечисление структура сайта, поступающие по цене чрезмерной вызовов и влияние масштабирования и производительности при использовании. Сайты, использующие structed навигации, которые потребляют чрезмерное количество ресурсов могут быть может быть регулирования.

В дополнение к поставщиков навигации ожидания введите многие пользователи реализовано успешно реализации альтернативных пользовательских переходов. Один общий класс реализации пользовательских переходов внедрены шаблоны отобразить клиента разработки, в которых хранятся локального кэша узлов навигации. (См. **[со стороны клиента на основе поиска](#using-search-driven-client-side-scripting)** в этой статье.)

Поставщики навигации существует две основные преимущества: 
- Они обычно работают, так и с отклика страницы макетов.
- Они являются очень масштабируемые и высокой производительностью, так как они могут создавать без затрат на ресурсы (и обновления в фоновом режиме после истечения времени ожидания). 
- Эти поставщиков навигации можно извлечь данные навигации, с помощью различных стратегий, от простого статических конфигураций для различных поставщиков динамических данных. 

Пример поставщика данных является использование **Навигация на основе поиска**, что обеспечивает гибкость для перечисления узлов навигации и обработка эффективно триммер безопасности. 

Возможны другие популярные решения для построения **настраиваемых поставщиков навигации**. Просмотрите [решения навигации для порталов SharePoint Online](https://docs.microsoft.com/sharepoint/dev/solution-guidance/portal-navigation) для получения дополнительных инструкций на создание настраиваемого поставщика навигации.
  
## <a name="pros-and-cons-of-sharepoint-online-navigation-options"></a>Преимущества и недостатки из SharePoint Online параметры навигации

В следующей таблице перечислены преимущества и недостатки каждого варианта. 


|Управляемая навигация  |Структурная навигация  |Навигация на основе поиска  |Поставщик Custom навигации  |
|---------|---------|---------|---------|
|Преимущества:<br/><br/>простота поддержки;<br/>Рекомендуется использовать параметр<br/>     |Преимущества:<br/><br/>простота настройки;<br/>Фильтруются по ролям безопасности<br/>Автоматически меняется по мере добавления содержимого<br/>|Плюсы:<br/><br/>Фильтруются по ролям безопасности<br/>автоматическое обновление при добавлении сайтов;<br/>короткое время загрузки и локальное кэширование структуры навигации.<br/>|Плюсы:<br/><br/>Широкий выбор вариантов<br/>Быстрое загрузки при кэшировании используется правильно<br/>Широкие возможности работы со макет отклика страницы<br/>|
|Недостатки:<br/><br/>отсутствие автоматического обновления для отражения структуры сайта.<br/>Воздействия на производительность при включении фильтрации по ролям безопасности<br/>|Недостатки:<br/><br/>**Не рекомендуется**<br/>**Воздействия на производительность и масштабируемость**<br/>**Может быть регулирования**<br/>|Недостатки:<br/><br/>нет возможности простого упорядочивания сайтов;<br/>требуется настройка эталонной страницы (необходимы технические навыки).<br/>|Недостатки:<br/><br/>Является обязательным, разработки пользовательских решений<br/>Внешний источник данных аудио- и необходимости кэша хранятся например Azure<br/>|

Наиболее подходящий вариант для веб-узла будет зависят от требований к сайта и технические возможности. Если необходимо, чтобы поставщик навигации масштабируемые ожидания введите, управляемой навигации с фильтрация по ролям безопасности этот параметр отключен является очень хорошим выбором. 

Параметр управляемой навигации могут поддерживать через конфигурации, не связанных файлов настройки кода, и это значительно быстрее, чем структуры навигации. Если требуется фильтрация по ролям безопасности и готовы, с помощью настраиваемой главной страницы и имеет некоторые возможности в организации, чтобы сохранить изменения, которые могут возникнуть в главную страницу по умолчанию для SharePoint Online, выберите вариант на основе механизмов поиска может привести к более взаимодействие с пользователем. При наличии более сложные требования поставщика пользовательских переходов может быть правильным выбором. Структуры навигации не рекомендуется.

И, наконец важно Обратите внимание на то, что SharePoint добавление поставщиков дополнительных навигации и функции для современных архитектур сайтов SharePoint, использование более плоская иерархии сайтов и модели и звезда с сайтами SharePoint сервера-концентратора. Это позволяет много сценариев для достигнуть, не требующие использования функции публикации SharePoint, и эти конфигурации навигации оптимизированные для улучшения масштабируемости и задержка в SharePoint Online. Обратите внимание на то, что применение же принцип - упрощение Общая структура сайта публикации SharePoint для структуру, часто помогает с общей производительности и масштабирования также. Это означает, что вместо одного семейства веб-сайтов с помощью сотен сайтов (дочерние сайты), лучше иметь множество семейств веб-сайтов с очень небольшого числа дочерних сайтов (дочерние сайты).


## <a name="using-managed-navigation-and-metadata-in-sharepoint-online"></a>С помощью управляемой навигации и метаданные в SharePoint Online

Управляемая Навигация — еще один параметр out поля, которые можно использовать для повторного создания большую часть функциональных возможностей структуры навигации. Управляемые метаданные можно настроить для фильтрации по ролям безопасности включена или отключена. При использовании фильтрации по ролям безопасности этот параметр отключен управляемой навигации довольно эффективно при загрузке все ссылки для перехода с константу количество вызовов сервера. Включение триммеров безопасности, однако инвертирует некоторые преимущества управляемой навигации и клиенты могут использовать для изучения один из пользовательских переходов решений для обеспечения оптимальной производительности и масштабируемости.

Количество сайтов не требуют фильтрация по ролям безопасности, как структура навигации часто согласованным для всех пользователей сайта. Если этот параметр отключен фильтрация по ролям безопасности и ссылка добавляется навигации, которая не все пользователи имеют доступ к, ссылки по-прежнему будут отображаться, но приведут к отказано в доступе. Нет и риска непреднамеренных доступа к содержимому.

### <a name="how-to-implement-managed-navigation-and-the-results"></a>Как реализовать управляемую навигацию и результаты

Существует несколько статей на Docs.Microsoft.com о сведения о управляемой навигации, например, в разделе [Обзор управляемой навигации в SharePoint Server](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation).

Чтобы реализовать управляемую навигацию, настройке условий с URL-адреса, соответствующие структуры переходов сайта. Даже управляемая Навигация может быть вручную curated для замены структуры навигации во многих случаях. Например:

![SharePoint Online структуры сайта](media/SPONavOptionsListOfSites.png)

Следующий пример демонстрирует производительность сложной навигации с использованием управляемой навигации.

![Производительность сложных навигации, с помощью управляемой навигации](media/SPONavOptionsComplexNavPerf.png)

Использование управляемой навигации постоянно повышает производительность по сравнению с подходом структуры навигации.
  
## <a name="using-structural-navigation-in-sharepoint-online"></a>Использование структурной навигации в SharePoint Online

Эта функция ожидания введите навигации, используемый по умолчанию и — это самый простой решения, но таким образом имеет компромиссов дорогостоящих производительности. Не требует настройки и не технической пользователя можно также легко добавить элементы, скрыть элементы и управления панели навигации на странице параметры. Это также тем не менее значение true для управляемой навигации, поэтому рекомендуется использовать управляемой навигации как, которые могут также быть легко управляемых и также управляются с помощью улучшить производительность.

![Структуры навигации с Показать дочерними сайтами выбранные](media/SPONavOptionsStructuredShowSubsites.png)
  
### <a name="turning-on-structural-navigation-in-sharepoint-online"></a>Переход на структурную навигацию в SharePoint Online

В качестве демонстрации как производительности в решении стандартных SharePoint Online с помощью структуры навигации и отображать дочерние сайты вариант включен. Ниже приведен снимок экрана с параметрами на странице " **Параметры сайта** " \> **навигации**.
  
![Снимок экрана: дочерние сайты](media/5b6a8841-34ed-4f61-b6d3-9d3e78d393e7.png)
  
### <a name="analyzing-structural-navigation-performance-in-sharepoint-online"></a>Анализ производительности структурной навигации в SharePoint Online

Для анализа производительности страниц SharePoint, вкладка **сети** средства разработчика F12 в Internet Explorer. 
  
![Снимок экрана: вкладка "Сеть", отображенная после вызова средств разработчика (F12)](media/SPONavOptionsNetworks.png)
  
1. На вкладке **Сеть** выберите загруженную страницу .aspx, а затем — вкладку **Сведения**.<br/> ![Снимок экрана: вкладка "Сведения"](media/ad85cefb-7bc5-4932-b29c-25f61b4ceeb2.png)<br/>
2. Щелкните пункт **Заголовки ответов**. <br/>![Снимок экрана: вкладка "Сведения"](media/c47770ac-5b2b-4941-9830-c57565dec4cc.png)<br/>SharePoint возвращает некоторые полезные диагностические сведения в заголовке ответа. 
3. Один из самых полезных элементов данных — **SPRequestDuration** , который соответствует значению, в миллисекундах, сколько времени запроса, которое потребовалось для обработки на сервере. На следующем снимке экрана **показано дочерних сайтов** не установлен для структуры навигации. Это значит, что существует только связь семейства сайтов в глобальной навигации.<br/>![Снимок экрана: время загрузки как время ответа на запрос](media/3422b2e8-15ec-4bb9-ba86-0965b6b49b01.png)<br/>
4. Клавиша **SPRequestDuration** имеет значение 245 (в миллисекундах). Представляет время, затраченное на возврата запроса. Поскольку существует только один элемент навигации на сайте, это хороший тестирования производительности для SharePoint Online выполнение без толстые навигации. На следующем снимке экрана показано, как добавлять в дочерних сайтов влияет этот ключ.<br/>![Снимок экрана: длительность обработки запроса составляет 2502 мс](media/618ee4e9-2ffa-4a22-b638-fa77b72292b8.png)<br/>
  
Время, необходимое для возврата запроса страницы для этого сайта относительно простой пример существенно увеличена добавление дочерних сайтов. Иерархии сложных сайтов, включая страницы в области навигации и другие настройки и параметры топологии, можно значительно повысить этой воздействия еще больше.

## <a name="using-search-driven-client-side-scripting"></a>Использование скриптов с навигацией на основе поиска на стороне клиента

С помощью поиска могут использовать индексы, которые создаются в фоновом режиме, используя непрерывного обхода контента. Результаты поиска которые извлекаются из индекса поиска и результаты, обрезать безопасности. Это обычно быстрее, чем поставщиков навигации ожидания введите, когда требуется фильтрация по ролям безопасности. Использование поиска для структуры навигации, особенно в том случае, если у вас есть структуру сложных сайта будет ускорить загрузки времени значительно страницы. Основное преимущество это через управляемой навигации — преимущества фильтрация по ролям безопасности.

Этот подход включает создание настраиваемой главной страницы и заменив навигации ожидания введите код настраиваемого HTML-код. Выполните следующие действия, описанные в следующем примере для замены навигации кода в файле `seattle.html`. В этом примере будет открыт `seattle.html` файл и замените весь элемент `id=”DeltaTopNavigation”` с помощью пользовательского кода HTML.

### <a name="example-replace-the-out-of-the-box-navigation-code-in-a-master-page"></a>Пример: Замена кода ожидания введите переходов на главной странице

1.  Перейдите на страницу Параметры сайта.
2.  Откройте коллекцию эталонных страниц, выбрав пункт **Эталонные страницы**.
3.  Здесь можно перемещаться по библиотеке и загрузите файл `seattle.master`.
4.  Измените код с помощью текстового редактора и удалите фрагмент кода, представленный на следующем снимке экрана.<br/>![Удалите блок кода показано](media/SPONavOptionsDeleteCodeBlock.png)<br/>
5. Удаление кода между `<SharePoint:AjaxDelta id=”DeltaTopNavigation”>` и `<\SharePoint:AjaxDelta>` теги и замените его на следующий фрагмент:<br/>

```
<div id="loading">
  <!--Replace with path to loading image.-->
  <div style="background-image: url(''); height: 22px; width: 22px; ">
  </div>
</div>
<!-- Main Content-->
<div id="navContainer" style="display:none">
    <div data-bind="foreach: hierarchy" class="noindex ms-core-listMenu-horizontalBox">
        <a class="dynamic menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" data-bind="attr: { href: item.Url, title: item.Title }">
            <span class="menu-item-text" data-bind="text: item.Title">
            </span>
        </a>
        <ul id="menu" data-bind="foreach: $data.children" style="padding-left:20px">
            <li class="static dynamic-children level1">
                <a class="static dynamic-children menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" data-bind="attr: { href: item.Url, title: item.Title }">
               
                 <!-- ko if: children.length > 0-->
                    <span aria-haspopup="true" class="additional-background ms-navedit-flyoutArrow dynamic-children">
                        <span class="menu-item-text" data-bind="text: item.Title">
                        </span>
                    </span>
                <!-- /ko -->
                <!-- ko if: children.length == 0-->   
                    <span aria-haspopup="true" class="ms-navedit-flyoutArrow dynamic-children">
                        <span class="menu-item-text" data-bind="text: item.Title">
                        </span>
                    </span>
                <!-- /ko -->   
                </a>
               
                <!-- ko if: children.length > 0-->                                                       
                <ul id="menu"  data-bind="foreach: children;" class="dynamic  level2" >
                    <li class="dynamic level2">
                        <a class="dynamic menu-item ms-core-listMenu-item ms-displayInline  ms-navedit-linkNode" data-bind="attr: { href: item.Url, title: item.Title }">
         
          <!-- ko if: children.length > 0-->
          <span aria-haspopup="true" class="additional-background ms-navedit-flyoutArrow dynamic-children">
           <span class="menu-item-text" data-bind="text: item.Title">
           </span>
          </span>
           <!-- /ko -->
          <!-- ko if: children.length == 0-->
          <span aria-haspopup="true" class="ms-navedit-flyoutArrow dynamic-children">
           <span class="menu-item-text" data-bind="text: item.Title">
           </span>
          </span>                 
          <!-- /ko -->   
                        </a>
          <!-- ko if: children.length > 0-->
         <ul id="menu" data-bind="foreach: children;" class="dynamic level3" >
          <li class="dynamic level3">
           <a class="dynamic menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" data-bind="attr: { href: item.Url, title: item.Title }">
            <span class="menu-item-text" data-bind="text: item.Title">
            </span>
           </a>
          </li>
         </ul>
           <!-- /ko -->
                    </li>
                </ul>
                <!-- /ko -->
            </li>
        </ul>
    </div>
</div>
```
<br/>
6. Замените URL-адрес в загрузке тега привязки в начале со ссылкой на изображение загрузки в семействе веб-сайтов "изображение". После внесения изменений, переименуйте файл и отправить его в коллекции главных страниц. Создает новый файл .master.<br/>
7. В этом HTML — это базовая разметка, которая будет устанавливаться результаты поиска, возвращаемые из кода JavaScript. Необходимо изменить код, чтобы изменить значение для корневого var = «веб-URL-адрес семейства сайтов», как показано в следующем фрагменте:<br/>

```
var root = “https://spperformance.sharepoint.com/sites/NavigationBySearch”;
```
<br/>
8. Результаты присваиваются в массив self.nodes и иерархия создается из объектов, с помощью linq.js присвоение массива self.hierarchy выходные данные. Этот массив — это объект, связанный с HTML-код. Для этого в функции toggleView(), передав собственный объект в функцию ko.applyBinding().<br/>Затем в результате массив иерархии привязаны к следующий HTML-код:<br/>

```
<div data-bind=”foreach: hierarchy” class=”noindex ms-core-listMenu-horizontalBox”>
```

Обработчики событий для `mouseenter` и `mouseexit` добавляются в панели навигации верхнего уровня для обработки раскрывающихся меню дочернего сайта, которых выполняется в `addEventsToElements()` функции.

В нашем примере сложных навигации это пустая страница загрузки без локального кэширования показано сократить время, затрачиваемое на сервере из структуры навигации тестирования производительности для получения следующий результат как подход управляемой навигации.

### <a name="about-the-javascript-file"></a>Описание файла JavaScript...

Полный JavaScript-файл выглядит следующим образом:

```
//Models and Namespaces
var SPOCustom = SPOCustom || {};
SPOCustom.Models = SPOCustom.Models || {}
SPOCustom.Models.NavigationNode = function () {

    this.Url = ko.observable("");
    this.Title = ko.observable("");
    this.Parent = ko.observable("");

};

var root = "https://spperformance.sharepoint.com/sites/NavigationBySearch";
var baseUrl = root + "/_api/search/query?querytext=";
var query = baseUrl + "'contentClass=\"STS_Web\"+path:" + root + "'&trimduplicates=false&rowlimit=300";

var baseRequest = {
    url: "",
    type: ""
};


//Parses a local object from JSON search result.
function getNavigationFromDto(dto) {
    var item = new SPOCustom.Models.NavigationNode();
    if (dto != undefined) {

        var webTemplate = getSearchResultsValue(dto.Cells.results, 'WebTemplate');

        if (webTemplate != "APP") {
            item.Title(getSearchResultsValue(dto.Cells.results, 'Title')); //Key = Title
            item.Url(getSearchResultsValue(dto.Cells.results, 'Path')); //Key = Path
            item.Parent(getSearchResultsValue(dto.Cells.results, 'ParentLink')); //Key = ParentLink
        }

    }
    return item;
}

function getSearchResultsValue(results, key) {

    for (i = 0; i < results.length; i++) {
        if (results[i].Key == key) {
            return results[i].Value;
        }
    }
    return null;
}

//Parse a local object from the serialized cache.
function getNavigationFromCache(dto) {
    var item = new SPOCustom.Models.NavigationNode();

    if (dto != undefined) {

        item.Title(dto.Title);
        item.Url(dto.Url);
        item.Parent(dto.Parent);
    }

    return item;
}

/* create a new OData request for JSON response */
function getRequest(endpoint) {
    var request = baseRequest;
    request.type = "GET";
    request.url = endpoint;
    request.headers = { ACCEPT: "application/json;odata=verbose" };
    return request;
};

/* Navigation Module*/
function NavigationViewModel() {
    "use strict";
    var self = this;
    self.nodes = ko.observableArray([]);
    self.hierarchy = ko.observableArray([]);;
    self.loadNavigatioNodes = function () {
        //Check local storage for cached navigation datasource.
        var fromStorage = localStorage["nodesCache"];
        if (false) {
            var cachedNodes = JSON.parse(localStorage["nodesCache"]);

            if (cachedNodes && timeStamp) {
                //Check for cache expiration. Currently set to 3 hrs.
                var now = new Date();
                var diff = now.getTime() - timeStamp;
                if (Math.round(diff / (1000 * 60 * 60)) < 3) {

                    //return from cache.
                    var cacheResults = [];
                    $.each(cachedNodes, function (i, item) {
                        var nodeitem = getNavigationFromCache(item, true);
                        cacheResults.push(nodeitem);
                    });

                    self.buildHierarchy(cacheResults);
                    self.toggleView();
                    addEventsToElements();
                    return;
                }
            }
        }
        //No cache hit, REST call required.
        self.queryRemoteInterface();
    };

    //Executes a REST call and builds the navigation hierarchy.
    self.queryRemoteInterface = function () {
        var oDataRequest = getRequest(query);
        $.ajax(oDataRequest).done(function (data) {
            var results = [];
            $.each(data.d.query.PrimaryQueryResult.RelevantResults.Table.Rows.results, function (i, item) {

                if (i == 0) {
                    //Add root element.
                    var rootItem = new SPOCustom.Models.NavigationNode();
                    rootItem.Title("Root");
                    rootItem.Url(root);
                    rootItem.Parent(null);
                    results.push(rootItem);
                }
                var navItem = getNavigationFromDto(item);
                results.push(navItem);
            });
            //Add to local cache
            localStorage["nodesCache"] = ko.toJSON(results);

            localStorage["nodesCachedAt"] = new Date().getTime();
            self.nodes(results);
            if (self.nodes().length > 0) {
                var unsortedArray = self.nodes();
                var sortedArray = unsortedArray.sort(self.sortObjectsInArray);

                self.buildHierarchy(sortedArray);
                self.toggleView();
                addEventsToElements();
            }
        }).fail(function () {
            //Handle error here!!
            $("#loading").hide();
            $("#error").show();
        });
    };
    self.toggleView = function () {
        var navContainer = document.getElementById("navContainer");
        ko.applyBindings(self, navContainer);
        $("#loading").hide();
        $("#navContainer").show();

    };
    //Uses linq.js to build the navigation tree.
    self.buildHierarchy = function (enumerable) {
        self.hierarchy(Enumerable.From(enumerable).ByHierarchy(function (d) {
            return d.Parent() == null;
        }, function (parent, child) {
            if (parent.Url() == null || child.Parent() == null)
                return false;
            return parent.Url().toUpperCase() == child.Parent().toUpperCase();
        }).ToArray());

        self.sortChildren(self.hierarchy()[0]);
    };


    self.sortChildren = function (parent) {

        // sjip processing if no children
        if (!parent || !parent.children || parent.children.length === 0) {
            return;
        }

        parent.children = parent.children.sort(self.sortObjectsInArray2);

        for (var i = 0; i < parent.children.length; i++) {
            var elem = parent.children[i];

            if (elem.children && elem.children.length > 0) {
                self.sortChildren(elem);
            }
        }
    };

    // ByHierarchy method breaks the sorting in chrome and firefix 
    // we need to resort  as ascending
    self.sortObjectsInArray2 = function (a, b) {
        if (a.item.Title() > b.item.Title())
            return 1;
        if (a.item.Title() < b.item.Title())
            return -1;
        return 0;
    };


    self.sortObjectsInArray = function (a, b) {
        if (a.Title() > b.Title())
            return -1;
        if (a.Title() < b.Title())
            return 1;
        return 0;
    }
}

//Loads the navigation on load and binds the event handlers for mouse interaction.
function InitCustomNav() {
    var viewModel = new NavigationViewModel();
    viewModel.loadNavigatioNodes();
}

function addEventsToElements() {
    //events.
      $("li.level1").mouseover(function () {
          var position = $(this).position();
          $(this).find("ul.level2").css({ width: 100, left: position.left + 10, top: 50 });
      })
   .mouseout(function () {
     $(this).find("ul.level2").css({  left: -99999, top: 0 });
   
    });
   
     $("li.level2").mouseover(function () {
          var position = $(this).position();
          console.log(JSON.stringify(position));
          $(this).find("ul.level3").css({ width: 100, left: position.left + 95, top:  position.top});
      })
   .mouseout(function () {
     $(this).find("ul.level3").css({  left: -99999, top: 0 });
    });
} _spBodyOnLoadFunctionNames.push("InitCustomNav");

``` 

В целом приведенный выше в `jQuery $(document).ready` функции существует `viewModel object` создан и затем `loadNavigationNodes()` вызове функции для этого объекта. Эта функция загружает либо иерархии построенные навигации, хранящиеся в локальном хранилище HTML5 в клиентском браузере или вызывает функцию `queryRemoteInterface()`.

`QueryRemoteInterface()`выполняет построение запроса с помощью `getRequest()` функция с параметром запроса определенного ранее в сценарии и возвращает данные с сервера. Эти данные — это по сути массив всех сайтов в семействе сайтов, представленные в виде объектов передачи данных с различными свойствами. 

Затем анализируется эти данные в ранее заданных `SPO.Models.NavigationNode` объекты, которые используют `Knockout.js` Создание наблюдаемых свойств, используемых с привязки значения в HTML, которое было определено ранее данных. 

Затем объекты помещаются в массиве результатов. Этот массив синтаксический анализ в JSON, с помощью выход и сохраняются в хранилище локального браузера для улучшения производительности в загрузке будущих страницы.

### <a name="benefits-of-this-approach"></a>Преимущества этого подхода

Одно из основных преимуществ [этого подхода](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page) —, что с помощью локальное хранилище HTML5 панели навигации хранится локально для пользователя при последующем их загрузки страницы. Повышение производительности основных, полученных от с помощью API поиска для структуры навигации; Тем не менее требуемое Техническая возможность выполнения и настроить эту функцию. 

[Пример реализации](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page)сайты упорядочены в так же, как структуры навигации ожидания введите; алфавитном порядке. Если вы хотите отклоняются от этой порядке, было бы более сложный для разработки и обслуживания. Кроме того этот подход требует отклоняются от поддерживаемых главных страниц. Если настраиваемой главной страницы не поддерживаются, веб-узла будет пропуска из внимания обновлений и улучшений, корпорация Майкрософт дает главных страницах.

[Над кода](#about-the-javascript-file) имеет следующие зависимости:

- jQuery-http://jquery.com/
- KnockoutJS-http://knockoutjs.com/
- LINQ.js - http://linqjs.codeplex.com/, или github.com/neuecc/linq.js

Текущая версия LinqJS не содержит метод ByHierarchy, используемый в предыдущем примере кода и нарушит работу кода навигации. Чтобы устранить эту проблему, добавьте следующий метод в файл Linq.js перед строкой `Flatten: function ()`.

```
ByHierarchy: function(firstLevel, connectBy, orderBy, ascending, parent) {
     ascending = ascending == undefined ? true : ascending;
     var orderMethod = ascending == true ? 'OrderBy' : 'OrderByDescending';
     var source = this;
     firstLevel = Utils.CreateLambda(firstLevel);
     connectBy = Utils.CreateLambda(connectBy);
     orderBy = Utils.CreateLambda(orderBy);
    
     //Initiate or increase level
     var level = parent === undefined ? 1 : parent.level + 1;

    return new Enumerable(function() {
         var enumerator;
         var index = 0;

        var createLevel = function() {
                 var obj = {
                     item: enumerator.Current(),
                     level : level
                 };
                 obj.children = Enumerable.From(source).ByHierarchy(firstLevel, connectBy, orderBy, ascending, obj);
                 if (orderBy !== undefined) {
                     obj.children = obj.children[orderMethod](function(d) {
                         return orderBy(d.item); //unwrap the actual item for sort to work
                     });
                 }
                 obj.children = obj.children.ToArray();
                 Enumerable.From(obj.children).ForEach(function(child) {
                     child.getParent = function() {
                         return obj;
                     };
                 });
                 return obj;
             };

        return new IEnumerator(

        function() {
             enumerator = source.GetEnumerator();
         }, function() {
             while (enumerator.MoveNext()) {
                 var returnArr;
                 if (!parent) {
                     if (firstLevel(enumerator.Current(), index++)) {
                         return this.Yield(createLevel());
                     }

                } else {
                     if (connectBy(parent.item, enumerator.Current(), index++)) {
                         return this.Yield(createLevel());
                     }
                 }
             }
             return false;
         }, function() {
             Utils.Dispose(enumerator);
         })
     });
 },

```
  
## <a name="related-topics"></a>Связанные статьи

[Обзор управляемой навигации в SharePoint Server](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation)

