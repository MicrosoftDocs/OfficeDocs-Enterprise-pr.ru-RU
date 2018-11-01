---
title: Настройка поиска в OneDrive для бизнеса с поддержкой нескольких регионов
ms.author: tlarsen
author: tklarsen
manager: arnek
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Сведения о настройке поиска в среде с поддержкой нескольких регионов.
ms.openlocfilehash: 5ca2a35385ab2c246b78dc8811e8435bbdec25c7
ms.sourcegitcommit: a3e2b2e58c328238c15d3f9daf042ea3de9d66be
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/30/2018
ms.locfileid: "25849915"
---
# <a name="configure-search-for-onedrive-for-business-multi-geo"></a><span data-ttu-id="ba4c2-103">Настройка поиска в OneDrive для бизнеса с поддержкой нескольких регионов</span><span class="sxs-lookup"><span data-stu-id="ba4c2-103">Configure Search for OneDrive for Business Multi-Geo</span></span>

<span data-ttu-id="ba4c2-104">Используя среду OneDrive для бизнеса с поддержкой нескольких регионов, организация может иметь одного клиента Office 365, но при этом хранить содержимое OneDrive в нескольких географических расположениях — центральном и периферийных.</span><span class="sxs-lookup"><span data-stu-id="ba4c2-104">In a Multi-Geo SharePoint Online (SPO) environment, an organization can have one Office 365 tenant, but store their SharePoint content in multiple geographical locations - one central location and one or more satellite geo locations.</span></span>

<span data-ttu-id="ba4c2-p101">В случае каждого географического расположения предусмотрены отдельные индекс и центр поиска. Когда пользователь пытается что-то найти, запрос развертывается для всех индексов, а возвращенные результаты объединяются.</span><span class="sxs-lookup"><span data-stu-id="ba4c2-p101">Each geographical location has its own search index and Search Center. When a user searches, the query is fanned out to all the indexes, and the returned results are merged.</span></span>

<span data-ttu-id="ba4c2-p102">Например, пользователь, находящийся в одном географическом расположении, может искать контент, хранящийся в другом, а также на сайте SharePoint, доступ к которому ограничен другим географическим расположением. Если у пользователя есть доступ к этому контенту, отобразятся результаты поиска.</span><span class="sxs-lookup"><span data-stu-id="ba4c2-p102">For example, a user in one geo location can search for content stored in another geo location, or for content on a SharePoint site that’s restricted to a different geo location. If the user has access to this content, search will show the result.</span></span>

## <a name="which-search-clients-work-in-a-multi-geo-environment"></a><span data-ttu-id="ba4c2-109">Какие клиенты поиска работают в среде с поддержкой нескольких регионов?</span><span class="sxs-lookup"><span data-stu-id="ba4c2-109">Which search clients work in a Multi-Geo environment?</span></span>

<span data-ttu-id="ba4c2-110">Возвращать результаты поиска из всех географических расположений могут такие клиенты:</span><span class="sxs-lookup"><span data-stu-id="ba4c2-110">These clients can return results from all geo locations:</span></span>

-   <span data-ttu-id="ba4c2-111">OneDrive для бизнеса;</span><span class="sxs-lookup"><span data-stu-id="ba4c2-111">OneDrive for Business</span></span>

-   <span data-ttu-id="ba4c2-112">Delve;</span><span class="sxs-lookup"><span data-stu-id="ba4c2-112">Delve</span></span>

-   <span data-ttu-id="ba4c2-113">домашняя страница SharePoint;</span><span class="sxs-lookup"><span data-stu-id="ba4c2-113">The SharePoint home page</span></span>

-   <span data-ttu-id="ba4c2-114">центр поиска;</span><span class="sxs-lookup"><span data-stu-id="ba4c2-114">The Search Center</span></span>

-   <span data-ttu-id="ba4c2-115">специальные поисковые приложения, которые используют API поиска SharePoint.</span><span class="sxs-lookup"><span data-stu-id="ba4c2-115">Custom search applications that use the SharePoint Search API</span></span>

### <a name="onedrive-for-business"></a><span data-ttu-id="ba4c2-116">OneDrive для бизнеса</span><span class="sxs-lookup"><span data-stu-id="ba4c2-116">OneDrive for Business</span></span>

<span data-ttu-id="ba4c2-117">Как только завершится настройка среды с поддержкой нескольких регионов, пользователи, выполняющие поиск в OneDrive, получат результаты из всех географических расположений.</span><span class="sxs-lookup"><span data-stu-id="ba4c2-117">As soon as the Multi-Geo environment has been set up, users that search in OneDrive get results from all geo locations.</span></span>

### <a name="delve"></a><span data-ttu-id="ba4c2-118">Delve</span><span class="sxs-lookup"><span data-stu-id="ba4c2-118">Delve</span></span>

<span data-ttu-id="ba4c2-119">Как только завершится настройка среды с поддержкой нескольких регионов, пользователи, выполняющие поиск в Delve, получат результаты из всех географических расположений.</span><span class="sxs-lookup"><span data-stu-id="ba4c2-119">As soon as the Multi-Geo environment has been set up, users that search in Delve get results from all geo locations.</span></span>

<span data-ttu-id="ba4c2-p103">Веб-канал Delve и карточка профиля показывают только краткое содержание файлов, которые хранятся в **центральном** расположении. В случае файлов, хранящихся в периферийных расположениях, отображается значок типа файла.</span><span class="sxs-lookup"><span data-stu-id="ba4c2-p103">The Delve feed and the profile card only show previews of files that are stored in the **central** location. For files that are stored in satellite geo locations, the icon for the file type is shown instead.</span></span>

### <a name="the-sharepoint-home-page"></a><span data-ttu-id="ba4c2-122">домашняя страница SharePoint;</span><span class="sxs-lookup"><span data-stu-id="ba4c2-122">The SharePoint home page</span></span>

<span data-ttu-id="ba4c2-p104">Как только завершится настройка среды с поддержкой нескольких регионов, пользователи на своей домашней странице SharePoint увидят новости, недавние и отслеживаемые сайты из нескольких географических расположений. Используя поле поиска на домашней странице SharePoint, пользователи получат объединенные результаты из нескольких географических расположений.</span><span class="sxs-lookup"><span data-stu-id="ba4c2-p104">As soon as the Multi-Geo environment has been set up, users will see news, recent and followed sites from multiple geo locations on their SharePoint home page. If they use the search box on the SharePoint home page, they'll get merged results from multiple geo locations.</span></span>

### <a name="the-search-center"></a><span data-ttu-id="ba4c2-125">центр поиска;</span><span class="sxs-lookup"><span data-stu-id="ba4c2-125">The Search Center</span></span>

<span data-ttu-id="ba4c2-p105">Когда завершится настройка среды с поддержкой нескольких регионов, каждый центр поиска будет по-прежнему отображать только результаты из своего географического расположения. Чтобы можно было получать данные из всех географических расположений, администраторы должны [изменить настройки каждого центра поиска](#_Set_up_a_1). После этого пользователи станут получать результаты из всех географических расположений.</span><span class="sxs-lookup"><span data-stu-id="ba4c2-p105">After the Multi-Geo environment has been set up, each Search Center continues to only show results from their own geo location. Admins must [change the settings of each Search Center](#_Set_up_a_1) to get results from all geo locations. Afterwards, users that search in the Search Center get results from all geo locations.</span></span>

### <a name="custom-search-applications"></a><span data-ttu-id="ba4c2-129">Специальные поисковые приложения</span><span class="sxs-lookup"><span data-stu-id="ba4c2-129">Custom search applications</span></span>

<span data-ttu-id="ba4c2-p106">Как правило, специальные поисковые приложения взаимодействуют с индексами поиска при помощи существующих REST API поиска SharePoint. Для получения результатов из всех или некоторых географических расположений приложение должно [вызвать API и включить в запрос новые параметры поддержки нескольких регионов](#_Get_custom_search). Это действие активирует развертывание запроса для всех геообъектов.</span><span class="sxs-lookup"><span data-stu-id="ba4c2-p106">As usual, custom search applications interact with the search indexes by using the existing SharePoint Search REST APIs. To get results from all, or some geo locations, the application must [call the API and include the new Multi-Geo query parameters](#_Get_custom_search) in the request. This triggers a fan out of the query to all geo locations.</span></span>

## <a name="whats-different-about-search-in-a-multi-geo-environment"></a><span data-ttu-id="ba4c2-133">Чем отличается поиск в среде с поддержкой нескольких регионов?</span><span class="sxs-lookup"><span data-stu-id="ba4c2-133">What’s different about search in a Multi-Geo environment?</span></span>

<span data-ttu-id="ba4c2-134">Некоторые знакомые вам функции поиска работают иначе в среде с поддержкой нескольких регионов.</span><span class="sxs-lookup"><span data-stu-id="ba4c2-134">Some search features you might be familiar with, work differently in a Multi-Geo environment.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="ba4c2-135"><strong>Функция</strong></span><span class="sxs-lookup"><span data-stu-id="ba4c2-135"><strong>Feature</strong></span></span></th>
<th align="left"><span data-ttu-id="ba4c2-136"><strong>Как это работает</strong></span><span class="sxs-lookup"><span data-stu-id="ba4c2-136"><strong>How does it work</strong></span></span></th>
<th align="left"><span data-ttu-id="ba4c2-137"><strong>Решение</strong></span><span class="sxs-lookup"><span data-stu-id="ba4c2-137"><strong>Workaround</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="ba4c2-138">Повышение уровня результатов</span><span class="sxs-lookup"><span data-stu-id="ba4c2-138">Promoted results</span></span></td>
<td align="left"><span data-ttu-id="ba4c2-p107">Вы можете создавать правила запросов с повышением уровня результатов для всего клиента, семейства веб-сайтов или отдельного сайта. Чтобы в среде с поддержкой нескольких регионов повысить уровень результатов для центров поиска <strong>всех</strong> географических расположений, определите такие результаты для <strong>клиента</strong>. Чтобы повысить уровень результатов <strong>только</strong> для центра поиска, находящегося в географическом расположении семейства веб-сайтов или отдельного сайта, определите такие результаты для <strong>семейства веб-сайтов</strong> или <strong>сайта</strong> соответственно.</span><span class="sxs-lookup"><span data-stu-id="ba4c2-p107">You can create query rules with promoted results at different levels: for the whole tenant, for a site collection, or for a site. In a Multi-Geo environment, define promoted results at the <strong>tenant</strong> level if you want to promote the results to the Search Centers in <strong>all</strong> geo locations. If you <strong>only</strong> want to promote results in the Search Center that’s in the geo location of the site collection or site, define the results at the <strong>site collection</strong> or <strong>site</strong> level.</span></span></td>
<td align="left"><span data-ttu-id="ba4c2-142">Если вам не нужны различные результаты с повышенным уровнем для каждого отдельного географического расположения (например, разные правила для перемещения), рекомендуем определять результаты с повышенным уровнем для клиента.</span><span class="sxs-lookup"><span data-stu-id="ba4c2-142">If you don’t need different promoted results per geo location, for example different rules for traveling, we recommend defining promoted results at the tenant level.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ba4c2-143">Уточнения поиска</span><span class="sxs-lookup"><span data-stu-id="ba4c2-143">Search refiners</span></span></td>
<td align="left"><span data-ttu-id="ba4c2-p108">При поиске возвращаются уточнения из всех географических расположений клиента, а затем объединяются. Объединение выполняется максимально правильно, но счетчики уточнений могут не быть точными на 100 %. Для большинства сценариев поиска такой точности вполне достаточно. </span><span class="sxs-lookup"><span data-stu-id="ba4c2-p108">Search returns refiners from all the geo locations of a tenant and then aggregates them. The aggregation is a best effort, meaning that the refiner counts might not be 100% accurate. For most search-driven scenarios, this accuracy is sufficient. </span></span></td>
<td align="left"><span data-ttu-id="ba4c2-147">Поисковые приложения, которые зависят от полноты уточнения, запрашивают каждое географическое расположение отдельно, не используя развертывание с поддержкой нескольких регионов.</span><span class="sxs-lookup"><span data-stu-id="ba4c2-147">For search-driven applications that depend on refiner completeness, query each geo location independently without using Multi-Geo fan-out.</span></span></td>
</tr>
<tr class="odd">
<td align="left"></td>
<td align="left"><span data-ttu-id="ba4c2-148">При поиске в среде с поддержкой нескольких регионов невозможно динамическое группирование числовых уточнений.</span><span class="sxs-lookup"><span data-stu-id="ba4c2-148">Multi-Geo search doesn’t support dynamic bucketing for numerical refiners.</span></span></td>
<td align="left"><span data-ttu-id="ba4c2-149">В случае числовых уточнений задавайте <a href="https://docs.microsoft.com/en-us/sharepoint/dev/general-development/query-refinement-in-sharepoint">параметр discretize</a>.</span><span class="sxs-lookup"><span data-stu-id="ba4c2-149">Use the <a href="https://docs.microsoft.com/en-us/sharepoint/dev/general-development/query-refinement-in-sharepoint">“Discretize” parameter</a> for numerical refiners.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ba4c2-150">Идентификаторы документов</span><span class="sxs-lookup"><span data-stu-id="ba4c2-150">Document IDs</span></span></td>
<td align="left"><span data-ttu-id="ba4c2-151">При разработке поискового приложения, которое зависит от ИД документов, обратите внимание на то, что такие идентификаторы в среде с поддержкой нескольких регионов уникальны только для каждого отдельного географического расположения.</span><span class="sxs-lookup"><span data-stu-id="ba4c2-151">If you’re developing a search-driven application that depends on document IDs, note that document IDs in a Multi-Geo environment aren’t unique across geo locations, they are unique per geo location.</span></span></td>
<td align="left"><span data-ttu-id="ba4c2-p109">Добавлен столбец "GeoLocationSource", который определяет географическое расположение и позволяет добиться уникальности.</span><span class="sxs-lookup"><span data-stu-id="ba4c2-p109">We’ve added a column that identifies the geo location. Use this column to achieve uniqueness. This column is named “GeoLocationSource”.</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="ba4c2-155">Количество результатов</span><span class="sxs-lookup"><span data-stu-id="ba4c2-155">Number of results</span></span></td>
<td align="left"><span data-ttu-id="ba4c2-156">На странице результатов поиска отображаются объединенные данные из географических расположений (не более 500 результатов на одной странице).</span><span class="sxs-lookup"><span data-stu-id="ba4c2-156">The search results page shows combined results from the geo locations, but it’s not possible to page beyond 500 results.</span></span></td>
<td align="left"></td>
</tr>
</tbody>
</table>

## <a name="whats-not-supported-for-search-in-a-multi-geo-environment"></a><span data-ttu-id="ba4c2-157">Что не поддерживается при поиске в среде с поддержкой нескольких регионов?</span><span class="sxs-lookup"><span data-stu-id="ba4c2-157">What’s not supported for search in a Multi-Geo environment?</span></span>

<span data-ttu-id="ba4c2-158">Некоторые знакомые вам функции поиска в среде поддержки нескольких регионов не поддерживаются.</span><span class="sxs-lookup"><span data-stu-id="ba4c2-158">Some of the search features you might be familiar with, aren’t supported in a Multi-Geo environment.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="ba4c2-159"><strong>Функция поиска</strong></span><span class="sxs-lookup"><span data-stu-id="ba4c2-159"><strong>Search feature</strong></span></span></th>
<th align="left"><span data-ttu-id="ba4c2-160"><strong>Примечание</strong></span><span class="sxs-lookup"><span data-stu-id="ba4c2-160"><strong>Note</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="ba4c2-161">Проверка подлинности только для приложений</span><span class="sxs-lookup"><span data-stu-id="ba4c2-161">App-only authentication</span></span></td>
<td align="left"><span data-ttu-id="ba4c2-162">При поиске в среде с поддержкой нескольких регионов невозможна проверка подлинности только для приложений (привилегированный доступ из служб).</span><span class="sxs-lookup"><span data-stu-id="ba4c2-162">App-only authentication (privileged access from services) isn’t supported in Multi-Geo search.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ba4c2-163">Гостевые пользователи</span><span class="sxs-lookup"><span data-stu-id="ba4c2-163">Guest users</span></span></td>
<td align="left"><span data-ttu-id="ba4c2-164">Гостевые пользователи получают результаты только из того географического расположения, из которого они выполняют поиск.</span><span class="sxs-lookup"><span data-stu-id="ba4c2-164">Guest users only get results from the geo location that they’re searching from.</span></span></td>
</tr>
</tbody>
</table>

## <a name="how-does-search-work-in-a-multi-geo-environment"></a><span data-ttu-id="ba4c2-165">Каковые принципы поиска в среде с поддержкой нескольких регионов?</span><span class="sxs-lookup"><span data-stu-id="ba4c2-165">How does search work in a Multi-Geo environment?</span></span>

<span data-ttu-id="ba4c2-166">**Все** клиенты поиска взаимодействуют с индексами поиска, используя существующие REST API поиска SharePoint.</span><span class="sxs-lookup"><span data-stu-id="ba4c2-166">**All** the search clients use the existing SharePoint Search REST APIs to interact with the search indexes.</span></span>

<img src="media/configure-search-for-multi-geo-image1-1.png" />

1. <span data-ttu-id="ba4c2-167">Клиент поиска вызывает конечную точку поиска REST с использованием свойства запроса EnableMultiGeoSearch = true.</span><span class="sxs-lookup"><span data-stu-id="ba4c2-167">A search client calls the Search REST endpoint with the query property EnableMultiGeoSearch= true.</span></span>
2. <span data-ttu-id="ba4c2-168">Запрос отправляется во все геообъекты, предусмотренные для клиента.</span><span class="sxs-lookup"><span data-stu-id="ba4c2-168">The query is sent to all geo locations in the tenant.</span></span>
3. <span data-ttu-id="ba4c2-169">Результаты поиска из каждого географического расположения объединяются и ранжируются.</span><span class="sxs-lookup"><span data-stu-id="ba4c2-169">Search results from each geo location are merged and ranked.</span></span>
4. <span data-ttu-id="ba4c2-170">Клиент получает объединенные результаты поиска.</span><span class="sxs-lookup"><span data-stu-id="ba4c2-170">The client gets unified search results.</span></span>



<span data-ttu-id="ba4c2-p110"><span id="_Set_up_a" class="anchor"><span id="_Ref501388384" class="anchor"></span></span>Обратите внимание на то, что результаты поиска не объединяются до тех пор, пока не будут получены данные из всех географических расположений. Это означает, что поиск в среде с поддержкой нескольких регионов выполняется с большей задержкой, чем поиск в среде с одним геообъектом.</span><span class="sxs-lookup"><span data-stu-id="ba4c2-p110"><span id="_Set_up_a" class="anchor"><span id="_Ref501388384" class="anchor"></span></span>Notice that we don’t merge the search results until we’ve received results from all the geo locations. This means that Multi-Geo searches have additional latency compared to searches in an environment with only one geo location.</span></span>

<span id="_Set_up_a_1" class="anchor"><span id="_Ref505252370" class="anchor"></span></span>
## <a name="get-a-search-center-to-show-results-from-all-geo-locations"></a><span data-ttu-id="ba4c2-173">Настройка отображения в центре поиска результатов из всех географических расположений</span><span class="sxs-lookup"><span data-stu-id="ba4c2-173">Get a Search Center to show results from all geo locations</span></span>

<span data-ttu-id="ba4c2-174">Для каждого центра поиска предусмотрено несколько вертикалей, и каждую из них следует настраивать отдельно.</span><span class="sxs-lookup"><span data-stu-id="ba4c2-174">Each Search Center has several verticals and you have to set up each vertical individually.</span></span>

1.  <span data-ttu-id="ba4c2-175">Убедитесь, что выполняете эти действия в учетной записи, у которой есть разрешение на изменение страницы результатов поиска и веб-части результатов поиска.</span><span class="sxs-lookup"><span data-stu-id="ba4c2-175">Ensure that you perform these steps with an account that has permission to edit the search results page and the Search Result Web Part.</span></span>

2.  <span data-ttu-id="ba4c2-176">Перейдите на страницу результатов поиска (см. [список](https://support.office.com/article/174d36e0-2f85-461a-ad9a-8b3f434a4213) страниц результатов поиска).</span><span class="sxs-lookup"><span data-stu-id="ba4c2-176">Navigate to the search results page (see the [list](https://support.office.com/article/174d36e0-2f85-461a-ad9a-8b3f434a4213) of search results pages)</span></span>

3.  <span data-ttu-id="ba4c2-p111">Выберите вертикаль для настройки. В верхнем правом углу щелкните значок шестеренки **Параметры**, а затем выберите **Изменить страницу**. Откроется страница результатов поиска в режиме редактирования.</span><span class="sxs-lookup"><span data-stu-id="ba4c2-p111">Select the vertical to set up, click **Settings** gear icon in the upper, right corner, and then click **Edit Page**. The search results page opens in Edit mode.</span></span>

     ![](media/configure-search-for-multi-geo-image2.png)
1.  <span data-ttu-id="ba4c2-p112">В веб-части результатов поиска переместите указатель в верхний правый угол, щелкните стрелку, а затем в меню выберите **Изменить веб-часть**. Под лентой в верхней правой части страницы откроется область инструментов веб-части результатов поиска. ![](media/configure-search-for-multi-geo-image3.png)</span><span class="sxs-lookup"><span data-stu-id="ba4c2-p112">In the Search Results Web Part, move the pointer to the upper, right corner of the Web Part, click the arrow, and then click **Edit Web Part** on the menu. The Search Results Web Part tool pane opens under the ribbon in the top right of the page. ![](media/configure-search-for-multi-geo-image3.png)</span></span>

1.  <span data-ttu-id="ba4c2-181">Чтобы в веб-части результатов поиска отображались результаты из всех геообъектов, в области инструментов веб-части выберите **Параметры** > **Параметры управления результатами** > **Отображение результатов с поддержкой нескольких регионов**.</span><span class="sxs-lookup"><span data-stu-id="ba4c2-181">In the Web Part tool pane, in the **Settings** section, under **Results control settings**, select **Show Multi-Geo results** to get the Search Results Web Part to show results from all geo locations.</span></span>

2.  <span data-ttu-id="ba4c2-182">Чтобы сохранить изменения и закрыть область инструментов веб-части, нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="ba4c2-182">Click **OK** to save your change and close the Web Part tool pane.</span></span>

3.  <span data-ttu-id="ba4c2-183">Проверьте изменения, внесенные в веб-часть результатов поиска, выбрав **Возврат** на вкладке "Страница" главного меню.</span><span class="sxs-lookup"><span data-stu-id="ba4c2-183">Check your changes to the Search Results Web Part by clicking **Check-In** on the Page tab of the main menu.</span></span>

4.  <span data-ttu-id="ba4c2-184">Опубликуйте изменения, воспользовавшись ссылкой, предоставленной в примечании вверху страницы.</span><span class="sxs-lookup"><span data-stu-id="ba4c2-184">Publish the changes by using the link provided in the note at the top of the page.</span></span>

<span id="_Get_custom_search" class="anchor"><span id="_Ref501388387" class="anchor"></span></span>
## <a name="get-custom-search-applications-to-show-results-from-all-or-some-geo-locations"></a><span data-ttu-id="ba4c2-185">Настройка отображения в специальных поисковых приложениях результатов из всех или некоторых географических расположений</span><span class="sxs-lookup"><span data-stu-id="ba4c2-185">Get custom search applications to show results from all or some geo locations</span></span>

<span data-ttu-id="ba4c2-p113">Специальные поисковые приложения получают результаты из всех или некоторых географических расположений, указывая параметры запроса для REST API поиска SharePoint. В зависимости от этих параметров запрос развертывается для всех или некоторых геообъектов. Например, если нужно найти релевантные данные, отправив запрос только в подмножество географических расположений, можно выполнить развертывание запроса именно для них. Если запрос будет выполнен успешно, REST API поиска SharePoint возвратит данные отклика.</span><span class="sxs-lookup"><span data-stu-id="ba4c2-p113">Custom search applications get results from all, or some, geo locations by specifying query parameters with the request to the SharePoint Search REST API. Depending on the query parameters, the query is fanned out to all geo locations, or to some geo locations. For example, if you only need to query a subset of geo locations to find relevant information, you can control the fan out to only these. If the request succeeds, the SharePoint Search REST API returns response data.</span></span>

### <a name="query-parameters"></a><span data-ttu-id="ba4c2-190">Параметры запроса</span><span class="sxs-lookup"><span data-stu-id="ba4c2-190">Query parameters</span></span>

<span data-ttu-id="ba4c2-p114">EnableMultiGeoSearch — это логическое значение, определяющее, должен ли запрос развертываться для индексов других геообъектов клиента с несколькими регионами. Чтобы выполнить развертывание запроса, задайте для этого параметра значение **true**. Чтобы не выполнять его, установите значение **false**. По умолчанию задано **false**. Если не указать этот параметр, развертывание запроса **не** будет выполнено для других геообъектов. Если вы используете этот параметр в среде без поддержки нескольких регионов, он будет проигнорирован.</span><span class="sxs-lookup"><span data-stu-id="ba4c2-p114">EnableMultiGeoSearch - This is a Boolean value that specifies whether the query shall be fanned out to the indexes of other geo locations of the Multi-Geo tenant. Set it to **true** to fan out the query; **false** to not fan out the query. The default value is **false**. If you don’t include this parameter, the query is **not** fanned out to other geo locations. If you use the parameter in an environment that isn’t Multi-Geo, the parameter is ignored.</span></span>

<span data-ttu-id="ba4c2-p115">ClientType — строка. Введите для каждого поискового приложения уникальное имя клиента. Если не указать этот параметр, развертывание запроса **не** будет выполнено для других геообъектов.</span><span class="sxs-lookup"><span data-stu-id="ba4c2-p115">ClientType - This is a string. Enter a unique client name for each search application. If you don’t include this parameter, the query is **not** fanned out to other geo locations.</span></span>

<span data-ttu-id="ba4c2-p116">MultiGeoSearchConfiguration — дополнительный список географических расположений клиента с несколькими регионами. Он предназначен для развертывания запроса, когда параметру **EnableMultiGeoSearch** задано значение **true**. Если не указать этот параметр или его значение, развертывание запроса будет выполнено для всех географических расположений. Для каждого географического расположения введите указанные ниже элементы в формате JSON.</span><span class="sxs-lookup"><span data-stu-id="ba4c2-p116">MultiGeoSearchConfiguration - This is an optional list of which geo locations in the Multi-Geo tenant to fan the query out to when **EnableMultiGeoSearch** is **true**. If you don’t include this parameter, or leave it blank, the query is fanned out to all geo locations. For each geo location, enter the following items, in JSON format:</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="ba4c2-202">Item</span><span class="sxs-lookup"><span data-stu-id="ba4c2-202">Item</span></span></th>
<th align="left"><span data-ttu-id="ba4c2-203">Описание</span><span class="sxs-lookup"><span data-stu-id="ba4c2-203">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="ba4c2-204">DataLocation</span><span class="sxs-lookup"><span data-stu-id="ba4c2-204">DataLocation</span></span></td>
<td align="left"><span data-ttu-id="ba4c2-205">Географическое расположение (например, NAM).</span><span class="sxs-lookup"><span data-stu-id="ba4c2-205">The geo location, for example NAM.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ba4c2-206">EndPoint</span><span class="sxs-lookup"><span data-stu-id="ba4c2-206">EndPoint</span></span></td>
<td align="left"><span data-ttu-id="ba4c2-207">Конечная точка для подключения (например, https://contoso.sharepoint.com).</span><span class="sxs-lookup"><span data-stu-id="ba4c2-207">The endpoint to connect to, for example https://contoso.sharepoint.com</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="ba4c2-208">SourceId</span><span class="sxs-lookup"><span data-stu-id="ba4c2-208">SourceId</span></span></td>
<td align="left"><span data-ttu-id="ba4c2-209">GUID источника результатов, например B81EAB55-3140-4312-B0F4-9459D1B4FFEE.</span><span class="sxs-lookup"><span data-stu-id="ba4c2-209">The GUID of the result source, for example B81EAB55-3140-4312-B0F4-9459D1B4FFEE.</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="ba4c2-p117">Если опустить элемент DataLocation или EndPoint, а также если продублировать DataLocation, запрос будет выполнен с ошибкой. [Сведения о конечной точке геообъектов клиента можно получить с помощью Microsoft Graph](https://docs.microsoft.com/ru-RU/sharepoint/dev/solution-guidance/multigeo-discovery).</span><span class="sxs-lookup"><span data-stu-id="ba4c2-p117">If you omit DataLocation or EndPoint, or if a DataLocation is duplicated, the request fails. [You can get information about the endpoint of a tenant's geo locations by using Microsoft Graph](https://docs.microsoft.com/ru-RU/sharepoint/dev/solution-guidance/multigeo-discovery).</span></span>

### <a name="response-data"></a><span data-ttu-id="ba4c2-212">Данные отклика</span><span class="sxs-lookup"><span data-stu-id="ba4c2-212">Response data</span></span>

<span data-ttu-id="ba4c2-p118">MultiGeoSearchStatus — свойство, которое API поиска SharePoint возвращает в отклике на запрос. Значение этого свойства является строкой и предоставляет указанные ниже сведения о результатах, которые возвращает API поиска SharePoint.</span><span class="sxs-lookup"><span data-stu-id="ba4c2-p118">MultiGeoSearchStatus – This is a property that the SharePoint Search API returns in response to a request. The value of the property is a string and gives the following information about the results that the SharePoint Search API returns:</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="ba4c2-215">Значение</span><span class="sxs-lookup"><span data-stu-id="ba4c2-215">Value</span></span></th>
<th align="left"><span data-ttu-id="ba4c2-216">Описание</span><span class="sxs-lookup"><span data-stu-id="ba4c2-216">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="ba4c2-217">Full</span><span class="sxs-lookup"><span data-stu-id="ba4c2-217">Full</span></span></td>
<td align="left"><span data-ttu-id="ba4c2-218">Полные результаты из <strong>всех</strong> географических расположений.</span><span class="sxs-lookup"><span data-stu-id="ba4c2-218">Full results from <strong>all</strong> the geo locations.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ba4c2-219">Partial</span><span class="sxs-lookup"><span data-stu-id="ba4c2-219">Partial</span></span></td>
<td align="left"><span data-ttu-id="ba4c2-p119">Частичные результаты из одного или нескольких географических расположений. Такие результаты являются неполными из-за временной ошибки.</span><span class="sxs-lookup"><span data-stu-id="ba4c2-p119">Partial results from one or more geo locations. The results are incomplete due to a transient error.</span></span></td>
</tr>

</tbody>
</table>

### <a name="query-using-the-rest-service"></a><span data-ttu-id="ba4c2-222">Отправка запросов с помощью службы REST</span><span class="sxs-lookup"><span data-stu-id="ba4c2-222">Query using the REST service</span></span>

<span data-ttu-id="ba4c2-p120">Используя GET-запрос, нужно указать соответствующие параметры в URL-адресе. Параметры POST-запроса передаются в его теле в формате нотации объектов JavaScript (JSON).</span><span class="sxs-lookup"><span data-stu-id="ba4c2-p120">With a GET request, you specify the query parameters in the URL. With a POST request, you pass the query parameters in the body in JavaScript Object Notation (JSON) format.</span></span>


#### <a name="request-headers"></a><span data-ttu-id="ba4c2-225">Заголовки запросов</span><span class="sxs-lookup"><span data-stu-id="ba4c2-225">Request headers</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="ba4c2-226">Имя</span><span class="sxs-lookup"><span data-stu-id="ba4c2-226">Name</span></span></th>
<th align="left"><span data-ttu-id="ba4c2-227">Значение</span><span class="sxs-lookup"><span data-stu-id="ba4c2-227">Value</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="ba4c2-228">Content-Type</span><span class="sxs-lookup"><span data-stu-id="ba4c2-228">Content-Type</span></span></td>
<td align="left"><span data-ttu-id="ba4c2-229">application/json;odata=verbose</span><span class="sxs-lookup"><span data-stu-id="ba4c2-229">application/json;odata=verbose</span></span></td>
</tr>
</tbody>
</table>

#### <a name="sample-get-request-thats-fanned-out-to-all-geo-locations"></a><span data-ttu-id="ba4c2-230">Пример GET-запроса, развертывание которого выполняется для **всех** геообъектов</span><span class="sxs-lookup"><span data-stu-id="ba4c2-230">Sample GET request that’s fanned out to **all** geo locations</span></span>

<span data-ttu-id="ba4c2-231">https:// \<клиент\>/\_api/search/query?querytext='sharepoint'&Properties='EnableMultiGeoSearch:true'&ClientType='ИД\_моего\_клиента'</span><span class="sxs-lookup"><span data-stu-id="ba4c2-231">https:// \<tenant\>/\_api/search/query?querytext='sharepoint'&Properties='EnableMultiGeoSearch:true'&ClientType='my\_client\_id'</span></span>

#### <a name="sample-get-request-to-fan-out-to-some-geo-locations"></a><span data-ttu-id="ba4c2-232">Пример GET-запроса, развертывание которого выполняется для **некоторых** геообъектов</span><span class="sxs-lookup"><span data-stu-id="ba4c2-232">Sample GET request to fan out to **some** geo locations</span></span>

<span data-ttu-id="ba4c2-233">https:// \<tenant\>/\_api/search/query?querytext='site'&ClientType='my_client_id'&Properties='EnableMultiGeoSearch:true, MultiGeoSearchConfiguration:[{DataLocation\\:"NAM"\\,Endpoint\\:"https\\://contosoNAM.sharepoint.com"\\,SourceId\\:"B81EAB55-3140-4312-B0F4-9459D1B4FFEE"}\\,{DataLocation\\:"CAN"\\,Endpoint\\:"https\\://contosoCAN.sharepoint-df.com"}]'</span><span class="sxs-lookup"><span data-stu-id="ba4c2-233">https:// \<tenant\>/\_api/search/query?querytext='site'&ClientType='my_client_id'&Properties='EnableMultiGeoSearch:true, MultiGeoSearchConfiguration:[{DataLocation\\:"NAM"\\,Endpoint\\:"https\\://contosoNAM.sharepoint.com"\\,SourceId\\:"B81EAB55-3140-4312-B0F4-9459D1B4FFEE"}\\,{DataLocation\\:"CAN"\\,Endpoint\\:"https\\://contosoCAN.sharepoint-df.com"}]'</span></span>

> [!NOTE]
> <span data-ttu-id="ba4c2-p121">Перед запятыми и двоеточиями в списке геообъектов для свойства MultiGeoSearchConfiguration используется символ **обратной косой черты**. Это обусловлено тем, что запросы GET используют двоеточия для разделения свойств и запятые для разделения аргументов свойств. Без обратной косой черты в качестве экранирующего символа свойство MultiGeoSearchConfiguration будет распознаваться неправильно.</span><span class="sxs-lookup"><span data-stu-id="ba4c2-p121">Commas and colons in the list of geo-locations for the MultiGeoSearchConfiguration property are preceded by the **backslash** character. This is because GET requests use colons to separate properties and commas to separate arguments of properties. Without the backslash as an escape character, the MultiGeoSearchConfiguration property is interpreted wrongly.</span></span>

#### <a name="sample-post-request-thats-fanned-out-to-all-geo-locations"></a><span data-ttu-id="ba4c2-237">Пример POST-запроса, развертывание которого выполняется для **всех** геообъектов</span><span class="sxs-lookup"><span data-stu-id="ba4c2-237">Sample POST request that’s fanned out to **all** geo locations</span></span>

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


#### <a name="sample-post-request-thats-fanned-out-to-some-geo-locations"></a><span data-ttu-id="ba4c2-238">Пример POST-запроса, развертывание которого выполняется для **некоторых** геообъектов</span><span class="sxs-lookup"><span data-stu-id="ba4c2-238">Sample POST request that’s fanned out to **some** geo locations</span></span>


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

### <a name="query-using-csom"></a><span data-ttu-id="ba4c2-239">Отправка запросов с помощью CSOM</span><span class="sxs-lookup"><span data-stu-id="ba4c2-239">Query using CSOM</span></span>

<span data-ttu-id="ba4c2-240">Пример CSOM-запроса, развертывание которого выполняется для **всех** геообъектов</span><span class="sxs-lookup"><span data-stu-id="ba4c2-240">Here’s a sample CSOM query that’s fanned out to **all** geo locations:</span></span>

    var keywordQuery = new KeywordQuery(ctx);
    keywordQuery.QueryText = query.SearchQueryText;
    keywordQuery.ClientType = <enter a string here>;
    keywordQuery["EnableMultiGeoSearch"] = true;

