---
title: Параметры навигации для SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/27/2018
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: adb92b80-b342-4ecb-99a1-da2a2b4782eb
description: В этой статье описывается, как для улучшения время загрузки страницы для SharePoint Online с использованием управляемой навигации и Навигация на основе поиска в классическом публикации.
ms.openlocfilehash: 6b2ee613d0cc6a6df92eb9b53374087a0ac2e5b7
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542572"
---
# <a name="navigation-options-for-sharepoint-online"></a>Параметры навигации для SharePoint Online

В этой статье описывается, как для улучшения время загрузки страницы для SharePoint Online с использованием управляемой навигации и Навигация на основе поиска в классическом публикации.
  
SharePoint Online с поддержкой классический публикацией имеет две области переходов; Глобальных и текущих переходов.
  
Глобальной навигации — меню верхней панели навигации, когда текущая структура навигации равно со стороны или навигации влево и вправо в контексте зависящие от языка конфигурации и использовать главную страницу.
  
Навигации может отрицательно сказаться производительности для всей портала часто настроены для использования в масштабе портала и таковым является важным элементом любого сайта SharePoint.
  
Структуры навигации не параметр рекомендуемые навигации в SharePoint Online, как он был разработан для On-premise топология с фильтрация по ролям безопасности и вызывает чрезмерной звонки и влияет на производительность при использовании этой структуры.
  
Об изменении структуры вследствие внедрения сайтов SharePoint современных где современных имеет иерархии упрощенный плоская сайта. Это упрощенный навигации с иерархией упрощенный, который не актуальна проблем производительности, связанных с навигации.
  
Существует два варианта ожидания введите переходов в SharePoint, а также третий, настраиваемые подход на основе поиска. Кроме того четвертый и довольно популярные вариант является для создания настраиваемого поставщика навигации. Руководство по поставщика навигации Custom просмотрите [решения навигации для порталов SharePoint Online](https://docs.microsoft.com/en-us/sharepoint/dev/solution-guidance/portal-navigation) . 
  
Каждый параметр имеет свои преимущества и недостатки, как описано в следующей таблице.
  
|**Структурная навигация**|**Управляемая навигация**|**Навигация на основе поиска**||**Поставщик пользовательских переходов**|
|:-----|:-----|:-----|:-----|:-----|
| Преимущества:  <br/>  простота настройки;  <br/>  фильтрация по ролям безопасности;  <br/>  автоматическое обновление при добавлении сайтов.  <br/> | Преимущества:  <br/>  простота поддержки;  <br/>  Рекомендуется использовать параметр  <br/> | Преимущества:  <br/>  фильтрация по ролям безопасности;  <br/>  автоматическое обновление при добавлении сайтов;  <br/>  короткое время загрузки и локальное кэширование структуры навигации.  <br/> || Плюсы:  <br/>    <br/>  Широкий выбор аудио- и параметры недоступны  <br/>  Быстрое загрузки при кэшировании используется правильно  <br/> |
| Недостатки:  <br/> **Не рекомендуется** <br/> **Воздействия на производительность** <br/> | Недостатки:  <br/>  отсутствие автоматического обновления для отражения структуры сайта.  <br/>  Воздействия на производительность при включении фильтрации по ролям безопасности  <br/> | Недостатки:  <br/>  нет возможности простого упорядочивания сайтов;  <br/>  требуется настройка эталонной страницы (необходимы технические навыки).  <br/> || Недостатки:  <br/>  Является обязательным, разработки пользовательских решений  <br/>  Внешний источник данных аудио- и необходимости кэша хранятся например Azure  <br/> |
   
Наиболее подходящий вариант для веб-узла будет зависят от требований к сайта и технические возможности. Если готовы, с помощью настраиваемой главной страницы и имеет некоторые возможности в организации, чтобы сохранить изменения, которые могут возникнуть в главную страницу по умолчанию для SharePoint Online, параметр на основе механизмов поиска будут создавать максимальное удобство работы пользователей. Если вы хотите простой промежуточный вариант между ожидания введите структуры навигации и поиска, управляемая Навигация является очень хорошим выбором. Параметр управляемой навигации могут поддерживать через конфигурации, не связанных файлов настройки кода, и это значительно быстрее, чем ожидания введите структуры навигации.
  
Упрощение Общая структура классический портала так же, как современная сортировка, помогает общую производительность и масштаб также. Что означает, что вместо одного семейства веб-сайтов с помощью нескольких сотен и тысяч узлов (дочерние сайты), лучший подход заключается в большое количество семейств с лишь несколько дочерних сайтов (дочерние сайты).
  
Это обеспечивает дополнительные параметры масштабирования в службе, позволяет избежать помещения все содержимое в один большой базы данных и в конечном счете обеспечивает большую свободу действий для навигации и важнее безопасности.
  
## <a name="using-structural-navigation-in-sharepoint-online"></a>Использование структурной навигации в SharePoint Online

Эта функция ожидания введите навигации, используемый по умолчанию и — это самый простой решения, но таким образом имеет компромиссов дорогостоящих производительности. Не требует настройки и не технической пользователя можно также легко добавить элементы, скрыть элементы и управления панели навигации на странице параметры. Это также тем не менее значение true для управляемой навигации, поэтому рекомендуется использовать управляемой навигации в качестве которых может также быть легко управляемых, а также управление.
  
### <a name="turning-on-structural-navigation-in-sharepoint-online"></a>Переход на структурную навигацию в SharePoint Online

В качестве демонстрации как производительности в решении стандартных SharePoint Online с помощью структуры навигации и отображать дочерние сайты вариант включен. Ниже снимок экрана, параметры, находящиеся на странице " **Параметры сайта** " \> **навигации**.
  
![Снимок экрана: дочерние сайты](media/5b6a8841-34ed-4f61-b6d3-9d3e78d393e7.png)
  
### <a name="analyzing-structural-navigation-performance-in-sharepoint-online"></a>Анализ производительности структурной навигации в SharePoint Online

Чтобы проанализировать производительность страницы SharePoint, используйте вкладку **Сеть** средств разработчика (F12) в Internet Explorer. 
  
![Снимок экрана: вкладка "Сеть", отображенная после вызова средств разработчика (F12)](media/e2aed8af-0843-487a-8b68-4f5260a2685e.png)
  
На вкладке **Сеть** выберите загруженную страницу .aspx, а затем — вкладку **Сведения**. 
  
![Снимок экрана: вкладка "Сведения"](media/ad85cefb-7bc5-4932-b29c-25f61b4ceeb2.png)
  
Щелкните пункт **Заголовки ответов**.
  
![Снимок экрана: вкладка "Сведения"](media/c47770ac-5b2b-4941-9830-c57565dec4cc.png)
  
SharePoint возвращает некоторую полезную диагностическую информацию в своих заголовках ответов. Одно из наиболее полезных — значение **SPRequestDuration**, обозначающее время обработки запроса на сервере в миллисекундах. 
  
В следующем рисунке **показано дочерних сайтов** не установлен для структуры навигации. Это значит, что существует только связь семейства сайтов в глобальной навигации. 
  
![Снимок экрана: время загрузки как время ответа на запрос](media/3422b2e8-15ec-4bb9-ba86-0965b6b49b01.png)
  
Клавиша **SPRequestDuration** имеет значение 245 (в миллисекундах). Представляет время, затраченное на возврата запроса. Поскольку существует только один элемент навигации на сайте, это хороший тестирования производительности для SharePoint Online выполнение без толстые навигации. На следующем снимке экрана показано, как добавлять в дочерних сайтов влияет этот ключ. 
  
![Снимок экрана: длительность обработки запроса составляет 2502 мс](media/618ee4e9-2ffa-4a22-b638-fa77b72292b8.png)
  
Добавление дочерних сайтов существенно увеличивает время возврата запроса страницы.
  
Преимущества использования регулярного структурированная навигация — можно легко организовать порядке, скрыть сайты, добавление страниц, результатом будет обрезать безопасности, что вы не отклоняться от поддерживаемых главных страниц, используемых в SharePoint Online.
  
## <a name="using-managed-navigation-and-managed-metadata-in-sharepoint-online"></a>Использование управляемой навигации и управляемых метаданных в SharePoint Online

Управляемая навигация — другой готовый параметр, который вы можете использовать для воссоздания функциональности, которая аналогична структурной навигации.
  
Преимущества использования управляемых метаданных, что является значительно быстрее для извлечения данных, а не с помощью содержимого по запросу для создания структуры переходов сайта. Хотя это и что намного быстрее нет возможности безопасности обрезки результатов так если у пользователя нет доступа на данном сайте, ссылки по-прежнему будут отображаться, но приведет к сообщение об ошибке.
  
 **Как реализовать управляемую навигацию и результаты**
  
Существует несколько статей на сайте TechNet о сведения о управляемой навигации, например, в разделе [Обзор управляемой навигации в SharePoint Server 2013](https://go.microsoft.com/fwlink/?LinkId=708689).
  
Для реализации управляемой навигации вы должны иметь права администратора банка терминов. С помощью настройки терминов с URL-адресами, которые соответствуют структуре семейства сайта, управляемую навигацию можно использовать для замены структурной навигации. Например:
  
![Снимок экрана: пример Subsite1](media/4155b4da-ccff-4e2a-92de-7803ac62982b.png)
  
Следующий пример демонстрирует производительность сложной навигации с использованием управляемой навигации.
  
![Снимок экрана: пример SPRequestDuration](media/72257528-0ec6-48b0-85a5-efeb7432db5b.png)
  
Использование управляемой навигации последовательно повышает производительность по сравнению со структурной навигацией с содержимым по запросу.
  
## <a name="using-search-driven-client-side-scripting"></a>Использование скриптов с навигацией на основе поиска на стороне клиента

С помощью поиска вы можете выгодно использовать индексы, которые создаются в фоне, используя непрерывный обход контента. Это значит, что громоздких запросов содержимого нет. Результаты поиска извлекаются из индекса поиска, а результаты отфильтровываются по ролям безопасности. Этот подход быстрее, чем использование обычных запросов на содержимое. Использование поиска для структурной навигации позволит значительно повысить скорость загрузки страниц, особенно если на вашем сайте сложная структура. Основное преимущество этого вида навигации над управляемой состоит в том, что вы выигрываете от фильтрации по ролям безопасности.
  
Этот подход включает в себя создание эталонной страницы и замену коробочного кода навигации пользовательским HTML-кодом. Следуйте этой процедуре, чтобы заменить код навигации в файле seattle.html.
  
В этом примере будет откройте файл seattle.html и замените весь элемент **id = «DeltaTopNavigation»** с помощью пользовательского кода HTML. 
  
 **Пример: Чтобы заменить коробочный код навигации на эталонной странице:**
  
1. Перейдите на страницу **Параметры сайта**. 
    
2. Откройте коллекцию эталонных страниц, выбрав пункт **Эталонные страницы**.
    
3. Отсюда вы можете перейти через библиотеку и скачать файл **seattle.master**.
    
4. Измените код с помощью текстового редактора и удалите фрагмент кода, представленный на следующем снимке экрана.
    
    ![Снимок экрана: удаление кода DeltaTopNavigation](media/70db2cd2-660d-4e0d-9d5c-a5df331c73b4.png)
  
5. Удаление кода между \<SharePoint:AjaxDelta id = «DeltaTopNavigation»\> и \<\SharePoint:AjaxDelta\> теги и замените его на следующий фрагмент:
    
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

6. Замените URL-адрес в загрузке тега привязки в начале со ссылкой на изображение загрузки в семействе веб-сайтов "изображение". После внесения изменений, переименуйте файл и отправить его в коллекции главных страниц. Создает новый файл .master.
    
7. В этом HTML — это базовая разметка, которая будет устанавливаться результаты поиска, возвращаемые из кода JavaScript. Нужно изменить следующий код, чтобы изменить значение для `var root = "site collection URL"` как показано в следующем фрагменте: 
    
  ```
  var root = "https://spperformance.sharepoint.com/sites/NavigationBySearch";
  ```

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
  var query = baseUrl + "'contentClass=\"STS_Web\"+path:" + root + "'&amp;trimduplicates=false&amp;rowlimit=300";
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
              if (cachedNodes &amp;&amp; timeStamp) {
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
              if (elem.children &amp;&amp; elem.children.length > 0) {
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
  
  ```

     $("li.level1").mouseover (функция {) 
  
положение var = $(this).position();
  
$(это).find("ul.level2").css ({ширины: 100, слева: position.left + 10, наиболее распространенные: 50});
    
     }) 
  
.mouseout (функция {)
  
$(это).find("ul.level2").css ({левой:-99999 верхней: 0});
  
});
  
$("li.level2").mouseover (функция {)
  
положение var = $(this).position();
  
Console.log(JSON.stringify(Position));
  
$(это).find("ul.level3").css ({ширины: 100, слева: position.left + 95, наиболее распространенные: position.top});
    
     }) 
  
.mouseout (функция {)
  
$(это).find("ul.level3").css ({левой:-99999 верхней: 0});
  
});
    
    } _spBodyOnLoadFunctionNames.push("InitCustomNav");
    
    To summarize the code shown above in the jQuery **[$(document).ready]** function there is a **[viewModel]** object created and then the **[loadNavigationNodes()]** function on that object is called. This function either loads the previously built navigation hierarchy stored in the HTML5 local storage of the client browser or it calls the function **[queryRemoteInterface()]**. 
    
    **[QueryRemoteInterface()]** builds a request using the **[getRequest()]** function with the query parameter defined earlier in the script and then returns data from the server. This data is essentially an array of all the sites in the site collection represented as data transfer objects with various properties. This data is then parsed into the previously defined **[SPO.Models.NavigationNode]** objects which use Knockout.js to create observable properties for use by data binding the values into the HTML that we defined earlier. The objects are then put into a results array. This array is parsed into JSON using Knockout and stored in the local browser storage for improved performance on future page loads. 
    
8. Затем результаты присваиваются массив **[self.nodes]** и иерархия создается из объектов, с помощью linq.js присвоение массива **[self.heirarchy]** выходные данные. Этот массив — это объект, связанный с HTML-код. Для этого в функции **[toggleView()]** , передав собственный объект в функцию **[ko.applyBinding()]** . Затем в результате массив иерархии привязаны к следующий HTML-код: 
    
  ```
  <div data-bind="foreach: hierarchy" class="noindex ms-core-listMenu-horizontalBox">
  ```

    И, наконец обработчики событий для **[mouseenter]** и **[mouseexit]** добавляются навигации верхнего уровня для обработки раскрывающихся меню дочернего сайта которого выполняется в функции **[addEventsToElements()]** . 
    
    В приведенном ниже снимке экрана можно увидеть результаты панели навигации:
    
    ![Снимок экрана с результатами навигации](media/020d34d2-942a-431b-9b26-6d2c8a6fde30.png)
  
    В нашем примере сложной навигации загрузка новой страницы без локального кэширования показывает, что время обработки на сервере было удалено при тестовой структурной навигации, чтобы получить такой же результат, как при управляемой навигации.
    
    ![Снимок экрана: SPRequestDuration 301](media/307d7caf-e83a-40d9-a551-91d842521d03.png)
  
    Одно из главных преимуществ такого подхода — то, что при использовании локального хранилища HTML5 данные навигации хранятся локально для пользователя на случай загрузки этой страницы в будущем.
    
Мы получаем значительные улучшения производительности от использования поискового API для структурной навигации. Однако для реализации и настройки этого функционала необходимы некоторые технические возможности. В этом примере реализации сайты упорядочены так же, как и в готовой структурной навигации, — в алфавитном порядке. Если вы хотите отойти от этого порядка, то сложность разработки и сопровождения возрастет. Кроме того, этот подход требует отказа от поддерживаемых эталонных страниц. Если пользовательские эталонные страницы не поддерживаются, то ваш сайт перестанет получать обновления и улучшения, которые Майкрософт разрабатывает для эталонных страниц.
  
Этот код имеет следующие зависимости:
  
- jQuery-[http://jquery.com/](http://jquery.com/)
    
- KnockoutJS-[http://knockoutjs.com/](http://knockoutjs.com/)
    
- LINQ.js - [http://linqjs.codeplex.com/](http://linqjs.codeplex.com/), или [github.com/neuecc/linq.js](https://github.com/neuecc/linq.js/)
    
Текущая версия LinqJS не содержит метод ByHierarchy, используемый в предыдущем примере кода и нарушит работу кода навигации. Чтобы устранить эту проблему, добавьте следующий метод в файл Linq.js перед строкой «Flatten: работать ()».
  
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


