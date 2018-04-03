---
title: Управление несколькими географически среды
ms.author: tlarsen
author: tklarsen
manager: arnek
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: Сведения о настройке поиска в среде с несколькими географически.
ms.openlocfilehash: 0c5c8eaa981c31151c70507da54587a7269f98f5
ms.sourcegitcommit: 3f3d2de6c0c5225156cfba01bc980994cd9ae848
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/03/2018
---
# <a name="configure-search-for-onedrive-for-business-multi-geo"></a><span data-ttu-id="35397-103">Настройка поиска для OneDrive для бизнеса Multi географически</span><span class="sxs-lookup"><span data-stu-id="35397-103">Configure Search for OneDrive for Business Multi-Geo</span></span>

<span data-ttu-id="35397-104">В среде с несколькими географически SharePoint Online (SPO) может иметь одну клиента Office 365 организации, но хранить их содержимого SharePoint в нескольких географических местах - одного центрального местоположения и один или несколько вспомогательные географического расположения.</span><span class="sxs-lookup"><span data-stu-id="35397-104">In a Multi-Geo SharePoint Online (SPO) environment, an organization can have one Office 365 tenant, but store their SharePoint content in multiple geographical locations - one central location and one or more satellite geo locations.</span></span>

<span data-ttu-id="35397-p101">Каждый свое географическое местоположение имеет свой собственный центр поиска и индекс поиска. При выполнении пользователем поиска, запрос fanned в работе для всех индексов и объединяются возвращаемых результатов.</span><span class="sxs-lookup"><span data-stu-id="35397-p101">Each geographical location has its own search index and Search Center. When a user searches, the query is fanned out to all the indexes, and the returned results are merged.</span></span>

<span data-ttu-id="35397-p102">К примеру пользователей в одном месте географически можно найти контент, который хранится в другом месте географически, и для контента на сайте SharePoint, в которую различных географического расположения. Если у пользователя есть доступ к этому содержимому, поиска будет показывать результат.</span><span class="sxs-lookup"><span data-stu-id="35397-p102">For example, a user in one geo location can search for content stored in another geo location, or for content on a SharePoint site that’s restricted to a different geo location. If the user has access to this content, search will show the result.</span></span>

## <a name="which-search-clients-work-in-a-multi-geo-environment"></a><span data-ttu-id="35397-109">В среде с несколькими географически которого поиск работы клиентов?</span><span class="sxs-lookup"><span data-stu-id="35397-109">Which search clients work in a Multi-Geo environment?</span></span>

<span data-ttu-id="35397-110">Эти клиенты могут возвращать результаты из всех расположений географически:</span><span class="sxs-lookup"><span data-stu-id="35397-110">These clients can return results from all geo locations:</span></span>

-   <span data-ttu-id="35397-111">OneDrive для бизнеса</span><span class="sxs-lookup"><span data-stu-id="35397-111">OneDrive for Business</span></span>

-   <span data-ttu-id="35397-112">Delve</span><span class="sxs-lookup"><span data-stu-id="35397-112">Delve</span></span>

-   <span data-ttu-id="35397-113">Домашняя страница SharePoint</span><span class="sxs-lookup"><span data-stu-id="35397-113">The SharePoint home page</span></span>

-   <span data-ttu-id="35397-114">Центр поиска</span><span class="sxs-lookup"><span data-stu-id="35397-114">The Search Center</span></span>

-   <span data-ttu-id="35397-115">Настраиваемые приложения поиска, использующие API поиска SharePoint</span><span class="sxs-lookup"><span data-stu-id="35397-115">Custom search applications that use the SharePoint Search API</span></span>

### <a name="onedrive-for-business"></a><span data-ttu-id="35397-116">OneDrive для бизнеса</span><span class="sxs-lookup"><span data-stu-id="35397-116">OneDrive for Business</span></span>

<span data-ttu-id="35397-117">Настройка среды ферма с несколькими географически сразу же пользователей, в которых поиск в OneDrive получать результаты из всех расположений географически.</span><span class="sxs-lookup"><span data-stu-id="35397-117">As soon as the Multi-Geo environment has been set up, users that search in OneDrive get results from all geo locations.</span></span>

### <a name="delve"></a><span data-ttu-id="35397-118">Delve</span><span class="sxs-lookup"><span data-stu-id="35397-118">Delve</span></span>

<span data-ttu-id="35397-119">Настройка среды ферма с несколькими географически сразу же пользователей, в которых поиск в Delve получать результаты из всех расположений географически.</span><span class="sxs-lookup"><span data-stu-id="35397-119">As soon as the Multi-Geo environment has been set up, users that search in Delve get results from all geo locations.</span></span>

<span data-ttu-id="35397-p103">Веб-канал Delve и Карточка профиля отображаются только предварительный просмотр файлов, которые хранятся в **центральном** расположении. Для файлов, которые хранятся в вспомогательных географического расположения вместо этого отображается значок для типа файла.</span><span class="sxs-lookup"><span data-stu-id="35397-p103">The Delve feed and the profile card only show previews of files that are stored in the **central** location. For files that are stored in satellite geo locations, the icon for the file type is shown instead.</span></span>

### <a name="the-sharepoint-home-page"></a><span data-ttu-id="35397-122">Домашняя страница SharePoint</span><span class="sxs-lookup"><span data-stu-id="35397-122">The SharePoint home page</span></span>

<span data-ttu-id="35397-p104">Как настроить среду несколькими географически пользователи увидят новости, последние и число сайтов из нескольких расположений географически на своей домашней странице SharePoint. При использовании поля поиска на домашней странице SharePoint, они только получать результаты из индекса поиска находится в расположения географически SPHome.</span><span class="sxs-lookup"><span data-stu-id="35397-p104">As soon as the Multi-Geo environment has been set up, users will see news, recent and followed sites from multiple geo locations on their SharePoint home page. If they use search box on the SharePoint home page, they only get results from the geo location SPHome search index is located in.</span></span>

### <a name="the-search-center"></a><span data-ttu-id="35397-125">Центр поиска</span><span class="sxs-lookup"><span data-stu-id="35397-125">The Search Center</span></span>

<span data-ttu-id="35397-p105">После Multi-географически среды был настроен, каждого центра поиска по-прежнему производится только Показать результаты из географического расположения. Администраторы должны [Изменить параметры каждого центра поиска](#_Set_up_a_1) для получения результатов из всех расположений географически. После этого пользователи, в которых поиск в центре поиска получать результаты из всех расположений географически.</span><span class="sxs-lookup"><span data-stu-id="35397-p105">After the Multi-Geo environment has been set up, each Search Center continues to only show results from their own geo location. Admins must [change the settings of each Search Center](#_Set_up_a_1) to get results from all geo locations. Afterwards, users that search in the Search Center get results from all geo locations.</span></span>

### <a name="custom-search-applications"></a><span data-ttu-id="35397-129">Настраиваемые приложения поиска</span><span class="sxs-lookup"><span data-stu-id="35397-129">Custom search applications</span></span>

<span data-ttu-id="35397-p106">Как обычно настраиваемые приложения поиска взаимодействовать с индексы поиска с помощью существующих API REST поиска SharePoint. Для получения результатов из всех или некоторых географического расположения, приложение должно [вызов API и включения новых параметров запроса несколькими географически](#_Get_custom_search) в запросе. Это запускает вентилятора из него запросов на все географического расположения.</span><span class="sxs-lookup"><span data-stu-id="35397-p106">As usual, custom search applications interact with the search indexes by using the existing SharePoint Search REST APIs. To get results from all, or some geo locations, the application must [call the API and include the new Multi-Geo query parameters](#_Get_custom_search) in the request. This triggers a fan out of the query to all geo locations.</span></span>

### <a name="whats-different-about-search-in-a-multi-geo-environment"></a><span data-ttu-id="35397-133">Каковы отличия, о поиске в среде с несколькими географически?</span><span class="sxs-lookup"><span data-stu-id="35397-133">What’s different about search in a Multi-Geo environment?</span></span>

<span data-ttu-id="35397-134">Некоторые функции поиска, которые могут быть знакомы, работают по-разному в среде с несколькими географически.</span><span class="sxs-lookup"><span data-stu-id="35397-134">Some search features you might be familiar with, work differently in a Multi-Geo environment.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="35397-135"><strong>Компонент</strong></span><span class="sxs-lookup"><span data-stu-id="35397-135"><strong>Feature</strong></span></span></th>
<th align="left"><span data-ttu-id="35397-136"><strong>Как это работает</strong></span><span class="sxs-lookup"><span data-stu-id="35397-136"><strong>How does it work</strong></span></span></th>
<th align="left"><span data-ttu-id="35397-137"><strong>Обходной путь</strong></span><span class="sxs-lookup"><span data-stu-id="35397-137"><strong>Workaround</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="35397-138">Результатов повышенного уровня</span><span class="sxs-lookup"><span data-stu-id="35397-138">Promoted results</span></span></td>
<td align="left"><span data-ttu-id="35397-p107">Можно создать правила запросов с повышенным уровнем результаты на различных уровнях: для всей клиента, для семейства веб-сайтов или для сайта. В среде с несколькими географически определите результатов повышенного уровня на уровне <strong>клиента</strong> , чтобы повысить уровень результатов в центрах поиска во <strong>всех</strong> расположениях географически. Вы <strong>только</strong> продвигать результаты в центре поиска, который находится в папке географически семейства веб-сайтов или сайта, определите результаты на уровне <strong>семейства веб-сайтов</strong> или <strong>сайта</strong> .</span><span class="sxs-lookup"><span data-stu-id="35397-p107">You can create query rules with promoted results at different levels: for the whole tenant, for a site collection, or for a site. In a Multi-Geo environment, define promoted results at the <strong>tenant</strong> level if you want to promote the results to the Search Centers in <strong>all</strong> geo locations. If you <strong>only</strong> want to promote results in the Search Center that’s in the geo location of the site collection or site, define the results at the <strong>site collection</strong> or <strong>site</strong> level.</span></span></td>
<td align="left"><span data-ttu-id="35397-142">Если не требуется различных результатов повышенного уровня одного географического расположения, например различные правила поездок, мы рекомендуем определение результатов на уровне клиента повышенного уровня.</span><span class="sxs-lookup"><span data-stu-id="35397-142">If you don’t need different promoted results per geo location, for example different rules for traveling, we recommend defining promoted results at the tenant level.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="35397-143">Уточнения поиска</span><span class="sxs-lookup"><span data-stu-id="35397-143">Search refiners</span></span></td>
<td align="left"><span data-ttu-id="35397-p108">Поиск возвращает уточнений из всех расположений географически клиента и затем объединяет их. Объединение — это все возможное, что означает, что счетчиков может быть точных 100%. Для большинства сценариев на основе механизмов поиска это является достаточно.</span><span class="sxs-lookup"><span data-stu-id="35397-p108">Search returns refiners from all the geo locations of a tenant and then aggregates them. The aggregation is a best effort, meaning that the refiner counts might not be 100% accurate. For most search-driven scenarios, this accuracy is sufficient.</span></span></td>
<td align="left"><span data-ttu-id="35397-147">Для приложения на основе поиска, зависящих от полнота уточнения запросов для каждого географического расположения независимо друг от друга без использования несколькими географически развертывания.</span><span class="sxs-lookup"><span data-stu-id="35397-147">For search-driven applications that depend on refiner completeness, query each geo location independently without using Multi-Geo fan-out.</span></span></td>
</tr>
<tr class="odd">
<td align="left"></td>
<td align="left"><span data-ttu-id="35397-148">Ферма с несколькими географически поиска не поддерживает динамические сегментация для числовых уточнений.</span><span class="sxs-lookup"><span data-stu-id="35397-148">Multi-Geo search doesn’t support dynamic bucketing for numerical refiners.</span></span></td>
<td align="left"><span data-ttu-id="35397-149">Используйте <a href="https://docs.microsoft.com/en-us/sharepoint/dev/general-development/query-refinement-in-sharepoint">параметр «Discretize»</a> для числовых уточнений.</span><span class="sxs-lookup"><span data-stu-id="35397-149">Use the <a href="https://docs.microsoft.com/en-us/sharepoint/dev/general-development/query-refinement-in-sharepoint">“Discretize” parameter</a> for numerical refiners.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="35397-150">Идентификаторы документов</span><span class="sxs-lookup"><span data-stu-id="35397-150">Document IDs</span></span></td>
<td align="left"><span data-ttu-id="35397-151">При разработке приложения на основе механизмов поиска, которое зависит от идентификаторами документов, обратите внимание на то, что идентификаторы документов в среде с несколькими географически не уникальный в географически подразделениях, они являются уникальными для географического расположения.</span><span class="sxs-lookup"><span data-stu-id="35397-151">If you’re developing a search-driven application that depends on document IDs, note that document IDs in a Multi-Geo environment aren’t unique across geo locations, they are unique per geo location.</span></span></td>
<td align="left"><span data-ttu-id="35397-p109">Мы добавили столбец, который идентифицирует географического расположения. Используйте этот столбец для обеспечения уникальности. Этот столбец является с именем «GeoLocationSource».</span><span class="sxs-lookup"><span data-stu-id="35397-p109">We’ve added a column that identifies the geo location. Use this column to achieve uniqueness. This column is named “GeoLocationSource”.</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="35397-155">Число результатов</span><span class="sxs-lookup"><span data-stu-id="35397-155">Number of results</span></span></td>
<td align="left"><span data-ttu-id="35397-156">Страницы результатов поиска отображает объединенный результаты из географического расположения, но невозможно страницы за пределы 500 результатов.</span><span class="sxs-lookup"><span data-stu-id="35397-156">The search results page shows combined results from the geo locations, but it’s not possible to page beyond 500 results.</span></span></td>
<td align="left"></td>
</tr>
</tbody>
</table>

### <a name="whats-not-supported-for-search-in-a-multi-geo-environment"></a><span data-ttu-id="35397-157">Что не поддерживается для поиска в среде с несколькими географически?</span><span class="sxs-lookup"><span data-stu-id="35397-157">What’s not supported for search in a Multi-Geo environment?</span></span>

<span data-ttu-id="35397-158">Некоторые функции поиска, которые могут быть знакомы, не поддерживаются в среде с несколькими географически.</span><span class="sxs-lookup"><span data-stu-id="35397-158">Some of the search features you might be familiar with, aren’t supported in a Multi-Geo environment.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="35397-159"><strong>Функция поиска</strong></span><span class="sxs-lookup"><span data-stu-id="35397-159"><strong>Search feature</strong></span></span></th>
<th align="left"><span data-ttu-id="35397-160"><strong>Примечание</strong></span><span class="sxs-lookup"><span data-stu-id="35397-160"><strong>Note</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="35397-161">Проверка подлинности только для приложений</span><span class="sxs-lookup"><span data-stu-id="35397-161">App-only authentication</span></span></td>
<td align="left"><span data-ttu-id="35397-162">Только проверка подлинности (привилегированный доступ из служб) не поддерживается в географически несколькими поиска.</span><span class="sxs-lookup"><span data-stu-id="35397-162">App-only authentication (privileged access from services) isn’t supported in Multi-Geo search.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="35397-163">Гости</span><span class="sxs-lookup"><span data-stu-id="35397-163">Guest users</span></span></td>
<td align="left"><span data-ttu-id="35397-164">Гости получить только результаты из географического расположения, они поиска из.</span><span class="sxs-lookup"><span data-stu-id="35397-164">Guest users only get results from the geo location that they’re searching from.</span></span></td>
</tr>
</tbody>
</table>

### <a name="how-does-search-work-in-a-multi-geo-environment"></a><span data-ttu-id="35397-165">Как работает поиска работает в среде с несколькими географически?</span><span class="sxs-lookup"><span data-stu-id="35397-165">How does search work in a Multi-Geo environment?</span></span>

<span data-ttu-id="35397-166">**Все** клиенты поиска использовать существующие интерфейсы API REST поиска SharePoint для взаимодействия с индексы поиска.</span><span class="sxs-lookup"><span data-stu-id="35397-166">**All** the search clients use the existing SharePoint Search REST APIs to interact with the search indexes.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><p><img src="media/configure-search-for-multi-geo_image1.png" /></p>
<p><span data-ttu-id="35397-167">На рисунке 1: Поиска в рамках клиента с тремя географического расположения</span><span class="sxs-lookup"><span data-stu-id="35397-167">Figure 1: Searching across a tenant with three geo locations</span></span></p></th>
<th align="left"><p><span data-ttu-id="35397-168">Поиск клиент вызывает конечная точка REST поиска с помощью свойства запроса EnableMultiGeoSearch = true.</span><span class="sxs-lookup"><span data-stu-id="35397-168">Search client calls the Search REST endpoint with the query property EnableMultiGeoSearch= true.</span></span></p>
<p><span data-ttu-id="35397-169">Запрос отправляется все географического расположения в клиентов.</span><span class="sxs-lookup"><span data-stu-id="35397-169">The query is sent to all geo locations in the tenant.</span></span></p>
<p><span data-ttu-id="35397-170">Результаты поиска из каждого географического расположения объединенных и ранжирования.</span><span class="sxs-lookup"><span data-stu-id="35397-170">Search results from each geo location are merged and ranked.</span></span></p>
<p><span data-ttu-id="35397-171">Клиент получает результаты объединенных поиска.</span><span class="sxs-lookup"><span data-stu-id="35397-171">Client gets unified search results.</span></span></p></th>
</tr>
</thead>
<tbody>
</tbody>
</table><span data-ttu-id="35397-p110">

<span id="_Set_up_a" class="anchor"><span id="_Ref501388384" class="anchor"></span></span>Ферма с несколькими географически поиска работает путем вызова каждой конечной точке поиска в каждом geos. Запросы на удаленных переход выполняются параллельно, но для объединения происходить мы дождитесь самые медленные ветвь отвечать перед мы можем слияния. Это означает несколькими географически добавьте дополнительные задержки для результатов поиска.  <span id="_Set_up_a_1" class="anchor"><span id="_Ref505252370" class="anchor"></span></span> 
### Получить центра поиска, чтобы показать результаты из всех расположений географически</span><span class="sxs-lookup"><span data-stu-id="35397-p110">

<span id="_Set_up_a" class="anchor"><span id="_Ref501388384" class="anchor"></span></span>Multi-Geo Search works by calling each search endpoint in each geos. The requests to remote goes are performed in parallel, but to merging to happen, we wait for the slowest leg to reply before we can do the merging. This implies multi-geo add additional latency to the search experience.  <span id="_Set_up_a_1" class="anchor"><span id="_Ref505252370" class="anchor"></span></span>
### Get a Search Center to show results from all geo locations</span></span>

<span data-ttu-id="35397-176">Каждого центра поиска имеет несколько вертикали и должны настроить по вертикали каждого по отдельности.</span><span class="sxs-lookup"><span data-stu-id="35397-176">Each Search Center has several verticals and you have to set up each vertical individually.</span></span>

1.  <span data-ttu-id="35397-177">Убедитесь, что выполняются эти действия с использованием учетной записи, которая имеет разрешение на изменение страницы результатов поиска и веб-части результатов поиска.</span><span class="sxs-lookup"><span data-stu-id="35397-177">Ensure that you perform these steps with an account that has permission to edit the search results page and the Search Result Web Part.</span></span>

2.  <span data-ttu-id="35397-178">Перейдите на страницу результатов поиска (просматривать страницы результатов поиска [списка](https://support.office.com/article/174d36e0-2f85-461a-ad9a-8b3f434a4213) )</span><span class="sxs-lookup"><span data-stu-id="35397-178">Navigate to the search results page (see the [list](https://support.office.com/article/174d36e0-2f85-461a-ad9a-8b3f434a4213) of search results pages)</span></span>

3.  <span data-ttu-id="35397-179">Выберите вертикальная для установки, щелкните значок шестеренки **Параметры** в верхнем правом углу окна и выберите команду **Изменить страницу**.</span><span class="sxs-lookup"><span data-stu-id="35397-179">Select the vertical to set up, click **Settings** gear icon in the upper, right corner, and then click **Edit Page**.</span></span>

> ![](media/configure-search-for-multi-geo_image2.png)
>
> <span data-ttu-id="35397-180">Откроется страница результатов поиска в режиме редактирования.</span><span class="sxs-lookup"><span data-stu-id="35397-180">The search results page opens in Edit mode.</span></span>

1.  <span data-ttu-id="35397-181">В веб-части результатов поиска наведите указатель на верхний правый угол веб-части щелкните стрелку и выберите в меню команду **Изменить веб-часть** .</span><span class="sxs-lookup"><span data-stu-id="35397-181">In the Search Results Web Part, move the pointer to the upper, right corner of the Web Part, click the arrow, and then click **Edit Web Part** on the menu.</span></span> ![](media/configure-search-for-multi-geo_image3.png)

> <span data-ttu-id="35397-182">Откроется панель инструмента веб-части результатов поиска в разделе ленты в верхней правой части страницы.</span><span class="sxs-lookup"><span data-stu-id="35397-182">The Search Results Web Part tool pane opens under the ribbon in the top right of the page.</span></span>

1.  <span data-ttu-id="35397-183">В области инструментов веб-части в разделе **Параметры** в области **результатов задают параметры**выберите **Показать несколькими географически результатов** для получения веб-части результатов поиска для отображения результатов из всех расположений географически.</span><span class="sxs-lookup"><span data-stu-id="35397-183">In the Web Part tool pane, in the **Settings** section, under **Results control settings**, select **Show Multi-Geo results** to get the Search Results Web Part to show results from all geo locations.</span></span>

2.  <span data-ttu-id="35397-184">Нажмите **кнопку ОК** , чтобы сохранить изменения и закрыть панель инструментов веб-части.</span><span class="sxs-lookup"><span data-stu-id="35397-184">Click **OK** to save your change and close the Web Part tool pane.</span></span>

3.  <span data-ttu-id="35397-185">Проверка изменений для веб-части результатов поиска, щелкнув **Возврат** на вкладке Страница главного меню.</span><span class="sxs-lookup"><span data-stu-id="35397-185">Check your changes to the Search Results Web Part by clicking **Check-In** on the Page tab of the main menu.</span></span>

4.  <span data-ttu-id="35397-186">Публикация изменений с помощью ссылки, содержащиеся в примечание в верхней части страницы.</span><span class="sxs-lookup"><span data-stu-id="35397-186">Publish the changes by using the link provided in the note at the top of the page.</span></span>

<span id="_Get_custom_search" class="anchor"><span id="_Ref501388387" class="anchor"></span></span>
### <a name="get-custom-search-applications-to-show-results-from-all-or-some-geo-locations"></a><span data-ttu-id="35397-187">Получение настраиваемые приложения поиска для отображения результатов из всех или некоторых географического расположения</span><span class="sxs-lookup"><span data-stu-id="35397-187">Get custom search applications to show results from all or some geo locations</span></span>

<span data-ttu-id="35397-p111">Настраиваемые приложения поиска получать результаты из всех или некоторых, географического расположения, путем указания параметров запроса с запросом на API REST поиска SharePoint. В зависимости от параметров запроса запрос fanned все географического расположения или некоторые географического расположения. Например если вам требуется только для запроса подмножество географически местоположения, чтобы найти информацию, можно управлять веером только такие. Если запрос пройдет успешно, API REST поиска SharePoint возвращает данные ответа.</span><span class="sxs-lookup"><span data-stu-id="35397-p111">Custom search applications get results from all, or some, geo locations by specifying query parameters with the request to the SharePoint Search REST API. Depending on the query parameters, the query is fanned out to all geo locations, or to some geo locations. For example, if you only need to query a subset of geo locations to find relevant information, you can control the fan out to only these. If the request succeeds, the SharePoint Search REST API returns response data.</span></span>

### <a name="query-parameters"></a><span data-ttu-id="35397-192">Параметры запроса</span><span class="sxs-lookup"><span data-stu-id="35397-192">Query parameters</span></span>

<span data-ttu-id="35397-p112">**EnableMultiGeoSearch** — это логическое значение, указывает ли запрос должен fanned в работе с индексами другие расположения географически несколькими географически клиента. Значение **true,** чтобы проходят запросов; **значение false,** чтобы не проходят запроса. Значение по умолчанию — **false**. Если этот параметр не указан, запрос — это **не** fanned в работе других географического расположения. При использовании параметра в среде, где не несколькими географически параметр игнорируется.</span><span class="sxs-lookup"><span data-stu-id="35397-p112">**EnableMultiGeoSearch** - This is a Boolean value that specifies whether the query shall be fanned out to the indexes of other geo locations of the Multi-Geo tenant. Set it to **true** to fan out the query; **false** to not fan out the query. The default value is **false**. If you don’t include this parameter, the query is **not** fanned out to other geo locations. If you use the parameter in an environment that isn’t Multi-Geo, the parameter is ignored.</span></span>

<span data-ttu-id="35397-p113">**Типа клиента** — это строка. Введите имя уникальное клиента для каждого приложения поиска. Если этот параметр не указан, запрос — это **не** fanned в работе других географического расположения.</span><span class="sxs-lookup"><span data-stu-id="35397-p113">**ClientType** - This is a string. Enter a unique client name for each search application. If you don’t include this parameter, the query is **not** fanned out to other geo locations.</span></span>

<span data-ttu-id="35397-p114">**MultiGeoSearchConfiguration** — это необязательный список из которых географически расположений в различных-географически клиентов для проходят запрос к при **EnableMultiGeoSearch** имеет **значение true**. Если не включить этот параметр, или оставьте его пустым, запрос fanned в работе для всех географического расположения. Для каждого географического расположения введите указанные ниже представлен в формате JSON.</span><span class="sxs-lookup"><span data-stu-id="35397-p114">**MultiGeoSearchConfiguration** - This is an optional list of which geo locations in the Multi-Geo tenant to fan the query out to when **EnableMultiGeoSearch** is **true**. If you don’t include this parameter, or leave it blank, the query is fanned out to all geo locations. For each geo location, enter the following items, in JSON format:</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="35397-204">Элемент</span><span class="sxs-lookup"><span data-stu-id="35397-204">Item</span></span></th>
<th align="left"><span data-ttu-id="35397-205">Описание</span><span class="sxs-lookup"><span data-stu-id="35397-205">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="35397-206">DataLocation</span><span class="sxs-lookup"><span data-stu-id="35397-206">DataLocation</span></span></td>
<td align="left"><span data-ttu-id="35397-207">Расположение географически, например им.</span><span class="sxs-lookup"><span data-stu-id="35397-207">The geo location, for example NAM.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="35397-208">Конечная точка</span><span class="sxs-lookup"><span data-stu-id="35397-208">EndPoint</span></span></td>
<td align="left"><span data-ttu-id="35397-209">Конечная точка следует подключиться, напримерhttps://contoso.sharepoint.com</span><span class="sxs-lookup"><span data-stu-id="35397-209">The endpoint to connect to, for example https://contoso.sharepoint.com</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="35397-210">SourceId</span><span class="sxs-lookup"><span data-stu-id="35397-210">SourceId</span></span></td>
<td align="left"><span data-ttu-id="35397-211">Идентификатор GUID источника результатов, например B81EAB55-3140-4312-B0F4-9459D1B4FFEE.</span><span class="sxs-lookup"><span data-stu-id="35397-211">The GUID of the result source, for example B81EAB55-3140-4312-B0F4-9459D1B4FFEE.</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="35397-p115">Если опустить DataLocation или конечную точку или дублируются DataLocation, не удается выполнить запрос. [Вы можете получать сведения о конечной точки клиента географического расположения с помощью Microsoft Graph](https://docs.microsoft.com/en-us/sharepoint/dev/solution-guidance/multigeo-discovery).</span><span class="sxs-lookup"><span data-stu-id="35397-p115">If you omit DataLocation or EndPoint, or if a DataLocation is duplicated, the request fails. [You can get information about the endpoint of a tenant's geo locations by using Microsoft Graph](https://docs.microsoft.com/en-us/sharepoint/dev/solution-guidance/multigeo-discovery).</span></span>

### <a name="response-data"></a><span data-ttu-id="35397-214">Данные ответа</span><span class="sxs-lookup"><span data-stu-id="35397-214">Response data</span></span>

<span data-ttu-id="35397-p116">**MultiGeoSearchStatus** — это свойство, которое возвращает API поиска SharePoint в ответ на запрос. Значение свойства — это строка и дает следующие сведения о результатах, возвращаемых API поиска SharePoint:</span><span class="sxs-lookup"><span data-stu-id="35397-p116">**MultiGeoSearchStatus** – This is a property that the SharePoint Search API returns in response to a request. The value of the property is a string and gives the following information about the results that the SharePoint Search API returns:</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="35397-217">Значение</span><span class="sxs-lookup"><span data-stu-id="35397-217">Value</span></span></th>
<th align="left"><span data-ttu-id="35397-218">Описание</span><span class="sxs-lookup"><span data-stu-id="35397-218">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="35397-219">Полный доступ</span><span class="sxs-lookup"><span data-stu-id="35397-219">Full</span></span></td>
<td align="left"><span data-ttu-id="35397-220">Полный результаты из <strong>всех</strong> расположений географически.</span><span class="sxs-lookup"><span data-stu-id="35397-220">Full results from <strong>all</strong> the geo locations.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="35397-221">Частично</span><span class="sxs-lookup"><span data-stu-id="35397-221">Partial</span></span></td>
<td align="left"><span data-ttu-id="35397-p117">Частичный результаты из одного или нескольких географического расположения. Результаты не завершены из-за временные ошибки.</span><span class="sxs-lookup"><span data-stu-id="35397-p117">Partial results from one or more geo locations. The results are incomplete due to a transient error.</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="35397-224">Нет</span><span class="sxs-lookup"><span data-stu-id="35397-224">None</span></span></td>
<td align="left"><span data-ttu-id="35397-225">Запрос не несколькими географически запроса и не было fanned в работе на других географического расположения.</span><span class="sxs-lookup"><span data-stu-id="35397-225">The query was not a Multi-Geo query and was not fanned out to the other geo locations.</span></span></td>
</tr>
</tbody>
</table>

### <a name="query-using-the-rest-service"></a><span data-ttu-id="35397-226">Запрос с использованием службы REST</span><span class="sxs-lookup"><span data-stu-id="35397-226">Query using the REST service</span></span>

<span data-ttu-id="35397-p118">Запрос GET позволяет определить параметры запроса в URL-адрес. С помощью запроса POST передайте параметров запроса в тексте запроса в формате JavaScript Object Notation (JSON).</span><span class="sxs-lookup"><span data-stu-id="35397-p118">With a GET request, you specify the query parameters in the URL. With a POST request, you pass the query parameters in the body in JavaScript Object Notation (JSON) format.</span></span>

#### <a name="request-headers"></a><span data-ttu-id="35397-229">Заголовки запросов</span><span class="sxs-lookup"><span data-stu-id="35397-229">Request headers</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="35397-230">Имя</span><span class="sxs-lookup"><span data-stu-id="35397-230">Name</span></span></th>
<th align="left"><span data-ttu-id="35397-231">Значение</span><span class="sxs-lookup"><span data-stu-id="35397-231">Value</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="35397-232">Content-Type</span><span class="sxs-lookup"><span data-stu-id="35397-232">Content-Type</span></span></td>
<td align="left"><span data-ttu-id="35397-233">приложение/json; odata = verbose</span><span class="sxs-lookup"><span data-stu-id="35397-233">application/json;odata=verbose</span></span></td>
</tr>
</tbody>
</table>

#### <a name="sample-get-request-thats-fanned-out-to-all-geo-locations"></a><span data-ttu-id="35397-234">Пример запроса GET, fanned в работе, чтобы **все** географического расположения</span><span class="sxs-lookup"><span data-stu-id="35397-234">Sample GET request that’s fanned out to **all** geo locations</span></span>

<span data-ttu-id="35397-235">https:// \<клиента\>/\_api/search/query?querytext = «sharepoint» & свойства = «EnableMultiGeoSearch:true» & типа клиента = "Мои\_клиента\_идентификатор"</span><span class="sxs-lookup"><span data-stu-id="35397-235">https:// \<tenant\>/\_api/search/query?querytext='sharepoint'&Properties='EnableMultiGeoSearch:true'&ClientType='my\_client\_id'</span></span>

#### <a name="sample-get-request-to-fan-out-to-some-geo-locations"></a><span data-ttu-id="35397-236">Пример запроса GET для проходят **некоторые** географического расположения</span><span class="sxs-lookup"><span data-stu-id="35397-236">Sample GET request to fan out to **some** geo locations</span></span>

<span data-ttu-id="35397-237">https:// <tenant>/_api/search/query?querytext = «узел» & типа клиента = «my_client_id» & Свойства = "EnableMultiGeoSearch:true, MultiGeoSearchConfiguration: [{DataLocation\:«Им»\,конечная точка\:«https\: contosoNAM.sharepoint.com»\,SourceId\:«B81EAB55-3140-4312-B0F4-9459D1B4FFEE»}\,{DataLocation\:«Может»\,конечная точка\:«https\://contosoCAN.sharepoint-df.com»}] "</span><span class="sxs-lookup"><span data-stu-id="35397-237">https:// <tenant>/_api/search/query?querytext='site'&ClientType='my_client_id'&Properties='EnableMultiGeoSearch:true, MultiGeoSearchConfiguration:[{DataLocation\:"NAM"\,Endpoint\:"https\://contosoNAM.sharepoint.com"\,SourceId\:"B81EAB55-3140-4312-B0F4-9459D1B4FFEE"}\,{DataLocation\:"CAN"\,Endpoint\:"https\://contosoCAN.sharepoint-df.com"}]'</span></span>

#### <a name="sample-post-request-thats-fanned-out-to-all-geo-locations"></a><span data-ttu-id="35397-238">Пример запроса POST, fanned в работе, чтобы **все** географического расположения</span><span class="sxs-lookup"><span data-stu-id="35397-238">Sample POST request that’s fanned out to **all** geo locations</span></span>

    {
        "request": {
            "__metadata": {
            "type": "Microsoft.Office.Server.Search.REST.SearchRequest"
        },
        "Querytext": "sharepoint",
        "Properties": {
            "results": [
                {
                    "Name": "EnableMultiGeoSearch",
                    "Value": {
                        "QueryPropertyValueTypeIndex": 3,
                        "BoolVal": true
                    }
                }
            ]
        },
        "ClientType": "my_client_id"
        }
    }


#### <a name="sample-post-request-thats-fanned-out-to-some-geo-locations"></a><span data-ttu-id="35397-239">Пример запроса POST, fanned в работе для **некоторых** географического расположения</span><span class="sxs-lookup"><span data-stu-id="35397-239">Sample POST request that’s fanned out to **some** geo locations</span></span>


    {
        "request": {
            "Querytext": "SharePoint",
            "ClientType": "my_client_id",
            "Properties": {
                "results": [
                    {
                        "Name": "EnableMultiGeoSearch",
                        "Value": {
                            "QueryPropertyValueTypeIndex": 3,
                            "BoolVal": true
                        }
                    },
                    {
                        "Name": "MultiGeoSearchConfiguration",
                        "Value": {
                        "StrVal": "[{\"DataLocation\":\"NAM\",\"Endpoint\":\"https://contoso.sharepoint.com\",\"SourceId\":\"B81EAB55-3140-4312-B0F4-9459D1B4FFEE\"},{\"DataLocation\":\"CAN\",\"Endpoint\":\"https://contosoCAN.sharepoint.com\"}]",
                            "QueryPropertyValueTypeIndex": 1
                        }
                    }
                ]
            }
        }
    }

### <a name="query-using-csom"></a><span data-ttu-id="35397-240">Запрос с использованием CSOM</span><span class="sxs-lookup"><span data-stu-id="35397-240">Query using CSOM</span></span>

<span data-ttu-id="35397-241">Ниже приведен пример запроса CSOM, fanned в работе, чтобы **все** географического расположения:</span><span class="sxs-lookup"><span data-stu-id="35397-241">Here’s a sample CSOM query that’s fanned out to **all** geo locations:</span></span>

    var keywordQuery = new KeywordQuery(ctx);
    keywordQuery.QueryText = query.SearchQueryText;
    keywordQuery.ClientType = <enter a string here>;
    keywordQuery["EnableMultiGeoSearch"] = true;