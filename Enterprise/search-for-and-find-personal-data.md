---
title: "Поиск персональных данных"
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 2/7/2018
ms.audience: ITPro
ms.topic: overview
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.service: o365-solutions
localization_priority: Priority
ms.custom:
- Strat_O365_Enterprise
- GDPR
ms.assetid: 
description: "Узнайте, как находить персональные данные в Office 365."
ms.openlocfilehash: f19aed534fe2bb4154edc31f0d1b0c82afcc1f04
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2018
---
# <a name="search-for-and-find-personal-data"></a><span data-ttu-id="10f40-103">Поиск персональных данных</span><span class="sxs-lookup"><span data-stu-id="10f40-103">Search for and find personal data</span></span>

<span data-ttu-id="10f40-104">Персональные данные в регламенте GDPR имеют очень широкое определение, включая любые сведения, которые касаются идентифицированных или идентифицируемых физических лиц, проживающих в Европейском союзе (ЕС).</span><span class="sxs-lookup"><span data-stu-id="10f40-104">Personal data is defined very broadly under the GDPR as any data that relates to an identified or identifiable natural person that is a resident of the European Union (EU).</span></span>

<span data-ttu-id="10f40-105">Статья 4. Определения</span><span class="sxs-lookup"><span data-stu-id="10f40-105">Article 4 – Definitions</span></span>

> <span data-ttu-id="10f40-106">Под "персональными данными" подразумевается любая информация, связанная с идентифицированным или идентифицируемым физическим лицом ("субъектом данных"). Идентифицируемым физическим лицом считается лицо, которого можно прямо или косвенно определить, в частности с помощью идентификатора, такого как имя, идентификационный номер, данные о местоположении, идентификатор в сети, либо с использованием одного или нескольких факторов, связанных с физическими, физиологическими, генетическими, ментальными, экономическими, культурными или социальными характеристиками этого физического лица.</span><span class="sxs-lookup"><span data-stu-id="10f40-106">‘personal data’ means any information relating to an identified or identifiable natural person (‘data subject’); an identifiable natural person is one who can be identified, directly or indirectly, in particular by reference to an identifier such as a name, an identification number, location data, an online identifier or to one or more factors specific to the physical, physiological, genetic, mental, economic, cultural or social identity of that natural person;</span></span>

<span data-ttu-id="10f40-107">В этой статье показано, как искать персональные данные, которые хранятся в SharePoint Online и OneDrive для бизнеса (в том числе на сайтах для всех групп Office 365 и Microsoft Teams).</span><span class="sxs-lookup"><span data-stu-id="10f40-107">This article demonstrates how to find personal data stored in SharePoint Online and OneDrive for Business (which includes the sites for all Office 365 groups and Microsoft Teams).</span></span>

<span data-ttu-id="10f40-p101">Для поиска персональных данных, на которые распространяется регламент GDPR, используются типы конфиденциальной информации в Office 365. Они определяют, как автоматизированный процесс распознает определенные типы данных, такие как номера медицинской страховки и кредитных карт. Сейчас эти типы невозможно использовать для поиска неактивных данных в почтовых ящиках Exchange. Тем не менее типы конфиденциальной информации можно применять с политиками защиты от потери данных для поиска персональных данных при передаче почты.</span><span class="sxs-lookup"><span data-stu-id="10f40-p101">Finding personal data subject to GDPR relies on using sensitive information types in Office 365. These define how the automated process recognizes specific information types such as health service numbers and credit card numbers. At this time these cannot be used to find data in Exchange mailboxes at rest. However, sensitive information types can be used with data loss prevention policies to find personal data in mail while in transit.</span></span>

<span data-ttu-id="10f40-112">Таким образом, хотя веб-часть "Поиск контента" в настоящее время невозможно использовать для поиска неактивных персональных данных в почтовых ящиках Exchange Online, вы можете применять типы конфиденциальной информации, на которые распространяется регламент GDPR, для поиска и защиты персональных данных во время их отправки по электронной почте.</span><span class="sxs-lookup"><span data-stu-id="10f40-112">So, while you can’t currently use Content Search to find personal data at rest in Exchange Online mailboxes, you can use the sensitive information types you curate for GDPR to find and protect personal information as it is sent through email.</span></span>

## <a name="use-content-search-to-find-personal-data"></a><span data-ttu-id="10f40-113">Поиск персональных данных с помощью веб-части "Поиск контента"</span><span class="sxs-lookup"><span data-stu-id="10f40-113">Use Content Search to find personal data</span></span>

<span data-ttu-id="10f40-p102">Корпорация Майкрософт рекомендует искать персональные данные в Office 365 в три этапа. Инструкции к каждому из этих этапов приведены далее в этой статье.</span><span class="sxs-lookup"><span data-stu-id="10f40-p102">Microsoft recommends a three-stage approach to finding personal data in Office 365. The rest of this topic provides guidance for each of these stages.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="10f40-116"><strong>Шаг</strong></span><span class="sxs-lookup"><span data-stu-id="10f40-116"><strong>Step</strong></span></span></th>
<th align="left"><span data-ttu-id="10f40-117"><strong>Описание</strong></span><span class="sxs-lookup"><span data-stu-id="10f40-117"><strong>Description</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><span data-ttu-id="10f40-118">1. Поиск типов конфиденциальной информации</span><span class="sxs-lookup"><span data-stu-id="10f40-118">1. Search for sensitive information types</span></span></p></td>
<td align="left"><p><span data-ttu-id="10f40-p103">Сначала используйте типы конфиденциальной информации для поиска персональных данных. Для каждого типа конфиденциальной информации создайте запрос веб-части "Поиск контента". Запустите его и проанализируйте результаты.</span><span class="sxs-lookup"><span data-stu-id="10f40-p103">Start by using sensitive information types to find personal data. Create a Content Search query for each sensitive information type. Run the query and analyze the results.</span></span></p>
<span data-ttu-id="10f40-122">При необходимости добавьте в запрос следующие параметры, чтобы сократить количество ложных срабатываний:</span><span class="sxs-lookup"><span data-stu-id="10f40-122">If needed, add parameters to the query to reduce false positives:</span></span> <li><span data-ttu-id="10f40-123">диапазон количества;</span><span class="sxs-lookup"><span data-stu-id="10f40-123">Count range</span></span></li>
    <li><span data-ttu-id="10f40-124">диапазон доверия;</span><span class="sxs-lookup"><span data-stu-id="10f40-124">Confidence range</span></span></li>
    <li><span data-ttu-id="10f40-125">другие свойства или операторы для более сложных запросов.</span><span class="sxs-lookup"><span data-stu-id="10f40-125">Other properties or operators for more complex queries</span></span></li>
<p><span data-ttu-id="10f40-126">При необходимости измените тип конфиденциальной информации, чтобы повысить точность данных для своей организации:</span><span class="sxs-lookup"><span data-stu-id="10f40-126">If necessary, modify a sensitive information type to improve accuracy for your organization:</span></span></p>
<p><li><span data-ttu-id="10f40-127">Настройте уровень вероятности непосредственно в XML.</span><span class="sxs-lookup"><span data-stu-id="10f40-127">Adjust the confidence level directly in the XML.</span></span></li></p>
<p><li><span data-ttu-id="10f40-128">Добавьте ключевые слова.</span><span class="sxs-lookup"><span data-stu-id="10f40-128">Add key words.</span></span></li></p>
<p><li><span data-ttu-id="10f40-129">Настройте требования к расположению слов и знаков для ключевых слов.</span><span class="sxs-lookup"><span data-stu-id="10f40-129">Adjust the proximity requirements for keywords.</span></span></li></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="10f40-130">2. Поиск дополнительных персональных данных в среде с помощью запросов KQL</span><span class="sxs-lookup"><span data-stu-id="10f40-130">2. Use Keyword Query Language (KQL) to find additional personal data in your environment</span></span></p></td>
<td align="left"><p><span data-ttu-id="10f40-131">Чтобы найти данные, не включенные в типы конфиденциальной информации, используйте специальные запросы KQL.</span><span class="sxs-lookup"><span data-stu-id="10f40-131">To find data not included in sensitive information types, use the KQL query language to develop custom queries.</span></span></p>
<p><span data-ttu-id="10f40-132">Проверяйте результаты этих запросов и настраивайте строку запроса KQL, пока не получите ожидаемый результат.</span><span class="sxs-lookup"><span data-stu-id="10f40-132">Test the results of these searches and adjust the KQL query string until you achieve the expected result.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="10f40-133">3. Создание собственных типов конфиденциальной информации с помощью запросов KQL</span><span class="sxs-lookup"><span data-stu-id="10f40-133">3. Create new custom sensitive information types using the KQL queries</span></span></p></td>
<td align="left"><span data-ttu-id="10f40-p104">Оптимизировав запросы KQL для поиска необходимых данных, создайте собственные типы конфиденциальной информации на основе этих запросов. Затем эти типы можно использовать с веб-частью "Поиск контента", в политиках защиты от потери данных и прочих средствах, а также в других запросах KQL.</span><span class="sxs-lookup"><span data-stu-id="10f40-p104">After optimizing KQL queries to find target data, create new custom sensitive information types using these queries. You can then use these custom sensitive information types with Content Search, in DLP policies and other tools, and within other KQL queries.</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="10f40-p105">В ближайшее время вы сможете создавать и изменять типы конфиденциальной информации в новом интерфейсе Центра безопасности и соответствия требованиям. Кроме того, вы сможете просматривать результаты в динамическом режиме и настраивать типы конфиденциальной информации в соответствии со своими потребностями.</span><span class="sxs-lookup"><span data-stu-id="10f40-p105">Coming soon — You'll be able to create and modify sensitive information types in a new user interface in the Security and Compliance Center. You can dynamically see matching results and tune sensitive information types to meet your needs.</span></span>

## <a name="search-for-sensitive-information-types-using-content-search"></a><span data-ttu-id="10f40-138">Поиск типов конфиденциальной информации с помощью веб-части "Поиск контента"</span><span class="sxs-lookup"><span data-stu-id="10f40-138">Search for sensitive information types using Content Search</span></span>

<span data-ttu-id="10f40-p106">Начните поиск персональных данных, используя типы конфиденциальной информации, предусмотренные в Office 365. Они перечислены в разделе "Классификация" в Центре безопасности и соответствия требованиям.</span><span class="sxs-lookup"><span data-stu-id="10f40-p106">Begin searching for personal data by using the sensitive information types that are included with Office 365. These are listed in the Security and Compliance Center under Classification.</span></span>

<span data-ttu-id="10f40-p107">В этой статье приведен список типов конфиденциальной информации, действующих в странах Европейского союза. Используйте их в качестве отправной точки. Скоро в Центре безопасности и соответствия требованиям будут представлены новые типы для соблюдения требований GDPR.</span><span class="sxs-lookup"><span data-stu-id="10f40-p107">This topic includes a list of current sensitive information types that apply to citizens in the European Union. Use these as a starting point. Check Security and Compliance Center frequently for new additions that can help with GDPR compliance.</span></span>

<span data-ttu-id="10f40-144">Кроме того, см. статью, в которой приведен [список типов конфиденциальной информации и описано назначение каждого из них](https://support.office.com/ru-RU/article/What-the-sensitive-information-types-look-for-fd505979-76be-4d9f-b459-abef3fc9e86b).</span><span class="sxs-lookup"><span data-stu-id="10f40-144">Also see this article: [List of sensitive information types and what each one looks for](https://support.office.com/ru-RU/article/What-the-sensitive-information-types-look-for-fd505979-76be-4d9f-b459-abef3fc9e86b).</span></span>

<span data-ttu-id="10f40-p108">Типы конфиденциальной информации определяют автоматические процессы, позволяющие распознавать типы определенных сведений, такие как номера банковских счетов, служб здравоохранения и кредитных карт. Типы конфиденциальной информации также называются условиями. Тип конфиденциальной информации определяется шаблоном, который можно идентифицировать с помощью регулярного выражения или функции. Кроме того, для идентификации типа конфиденциальной информации могут использоваться подкрепляющие доказательства, такие как ключевые слова и контрольные суммы. Кроме того, в процессе оценки используются уровень вероятности, а также расположение слов и знаков.</span><span class="sxs-lookup"><span data-stu-id="10f40-p108">Sensitive information types define how the automated process recognizes specific information types such as bank account numbers, health service numbers, and credit card numbers. Sensitive information types are also referred to as conditions. A sensitive information type is defined by a pattern that can be identified by a regular expression or a function. In addition, corroborative evidence such as keywords and checksums can be used to identify a sensitive information type. Confidence level and proximity are also used in the evaluation process.</span></span>

<span data-ttu-id="10f40-150">Сейчас типы конфиденциальной информации невозможно использовать для поиска неактивных данных в почтовых ящиках.</span><span class="sxs-lookup"><span data-stu-id="10f40-150">At this time sensitive information types cannot be used to find data at rest in mailboxes.</span></span>

### <a name="using-content-search-with-sensitive-information-types"></a><span data-ttu-id="10f40-151">Использование веб-части "Поиск контента" с типами конфиденциальной информации</span><span class="sxs-lookup"><span data-stu-id="10f40-151">Using Content Search with sensitive information types</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="10f40-152"><strong>Шаг</strong></span><span class="sxs-lookup"><span data-stu-id="10f40-152"><strong>Step</strong></span></span></th>
<th align="left"><span data-ttu-id="10f40-153"><strong>Дополнительные сведения</strong></span><span class="sxs-lookup"><span data-stu-id="10f40-153"><strong>More information</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd"><td align="left"><p><span data-ttu-id="10f40-154">Переход в раздел "Поиск контента" в Центре безопасности и соответствия требованиям</span><span class="sxs-lookup"><span data-stu-id="10f40-154">Go to Content Search in the Security and Compliance Center</span></span></p></td>
<td align="left"><p><span data-ttu-id="10f40-155">В расположенной слева области Центра безопасности и соответствия требованиям щелкните **Поиск и исследования** &gt; **Поиск контента**.</span><span class="sxs-lookup"><span data-stu-id="10f40-155">In the left pane of the Security &amp; Compliance Center, click **Search &amp; investigation** &gt; **Content search**.</span></span></p>
<p><span data-ttu-id="10f40-156">См. статью <a href="https://support.office.com/en-us/article/Run-a-Content-Search-in-the-Office-365-Security-Compliance-Center-61852fd9-fe8a-4880-a339-cb19ed3bff4a">Поиск содержимого в Центре безопасности и соответствия требованиям Office 365</a>.</span><span class="sxs-lookup"><span data-stu-id="10f40-156">Run a Content Search in the Office 365 Security & Compliance Center</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="10f40-157">Создание искомого элемента для каждого типа конфиденциальной информации</span><span class="sxs-lookup"><span data-stu-id="10f40-157">Create a new search item for each sensitive information type</span></span></p></td>
<td align="left"><p><span data-ttu-id="10f40-158">Используйте следующий синтаксис:</span><span class="sxs-lookup"><span data-stu-id="10f40-158">Use the following syntax:</span></span></p>
<blockquote>
<p><span data-ttu-id="10f40-159">SensitiveType:"&lt;тип&gt;"</span><span class="sxs-lookup"><span data-stu-id="10f40-159">SensitiveType:”&lt;type&gt;”</span></span></p>
</blockquote>
<p><span data-ttu-id="10f40-160">Пример:</span><span class="sxs-lookup"><span data-stu-id="10f40-160">For example:</span></span></p>
<blockquote>
<p><span data-ttu-id="10f40-161">SensitiveType:&quot;Номер паспорта гражданина Франции&quot;</span><span class="sxs-lookup"><span data-stu-id="10f40-161">France Passport Number</span></span></p>
</blockquote>
<p><span data-ttu-id="10f40-p109">Ограничьте область поиска средой SharePoint (в том числе OneDrive для бизнеса). Убедитесь в точности синтаксиса, а также отсутствии опечаток и лишних пробелов.</span><span class="sxs-lookup"><span data-stu-id="10f40-p109">Scope the search to SharePoint (includes OneDrive for Business). Make sure the syntax is exact and there are no extra spaces or typos.</span></span></p>
<p><span data-ttu-id="10f40-164">См. статью <a href="https://support.office.com/ru-RU/article/Form-a-query-to-find-sensitive-data-stored-on-sites-3019fbc5-7f15-4972-8d0e-dc182dc7f836">Создание запроса для поиска конфиденциальных данных на сайтах</a>.</span><span class="sxs-lookup"><span data-stu-id="10f40-164">Form a query to find sensitive data stored on sites</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="10f40-165">Просмотр результатов каждого запроса</span><span class="sxs-lookup"><span data-stu-id="10f40-165">Review the results for each search</span></span></p></td>
<td align="left"><p><span data-ttu-id="10f40-166">Проверьте запрос на наличие проблем следующего характера, чтобы убедиться в его точности:</span><span class="sxs-lookup"><span data-stu-id="10f40-166">Look for these types of issues to determine if the query accuracy is on target:</span></span></p>
<p><li><span data-ttu-id="10f40-167">большое количество ложных срабатываний;</span><span class="sxs-lookup"><span data-stu-id="10f40-167">Many false positives</span></span></li></p>
<p><li><span data-ttu-id="10f40-168">отсутствие известных экземпляров данных.</span><span class="sxs-lookup"><span data-stu-id="10f40-168">Missing known instances of data</span></span></li></p>
<p><span data-ttu-id="10f40-169">См. статью <a href="https://support.office.com/en-us/article/Export-Content-Search-results-from-the-Office-365-Security-Compliance-Center-ed48d448-3714-4c42-85f5-10f75f6a4278">Экспорт результатов поиска контента из Центра безопасности и соответствия требованиям Office 365</a>.</span><span class="sxs-lookup"><span data-stu-id="10f40-169"> Export Content Search results from the Office 365 Security & Compliance Center  https://go.microsoft.com/fwlink/?linkid=851206 </span></span></p>
<p><span data-ttu-id="10f40-170">Примечание. Если вы используете Mozilla Firefox или Chrome, возможно, вам потребуется сначала скачать отчеты с помощью браузера Internet Explorer или Edge, чтобы установить необходимую надстройку.</span><span class="sxs-lookup"><span data-stu-id="10f40-170">Note: if you’re using Mozilla Firefox or Chrome, you might need to first download reports using Internet Explorer or Edge in order to install the required add-in.</span></span></p></td>
</tr>
</tbody>
</table>

## <a name="sensitive-information-types-for-eu-citizen-data"></a><span data-ttu-id="10f40-171">Типы конфиденциальной информации о гражданах стран ЕС</span><span class="sxs-lookup"><span data-stu-id="10f40-171">Sensitive information types for EU citizen data</span></span>

<span data-ttu-id="10f40-p110">Для начала используйте перечисленные ниже типы конфиденциальной информации. В ближайшее время будет представлен ряд дополнительных типов конфиденциальной информации для персональных данных в странах ЕС.</span><span class="sxs-lookup"><span data-stu-id="10f40-p110">Start with these sensitive information types. Many more sensitive information types are coming soon for personal data in EU countries.</span></span>

> <span data-ttu-id="10f40-174">Внутренний идентификационный номер гражданина Бельгии</span><span class="sxs-lookup"><span data-stu-id="10f40-174">Belgium National Number</span></span>
>
> <span data-ttu-id="10f40-175">Номер кредитной карты</span><span class="sxs-lookup"><span data-stu-id="10f40-175">Credit Card Number</span></span>
>
> <span data-ttu-id="10f40-176">Номер идентификационной карты гражданина Хорватии</span><span class="sxs-lookup"><span data-stu-id="10f40-176">Croatia Identity Card Number</span></span>
>
> <span data-ttu-id="10f40-177">Персональный идентификационный номер (OIB) гражданина Хорватии</span><span class="sxs-lookup"><span data-stu-id="10f40-177">Croatia Personal Identification (OIB) Number</span></span>
>
> <span data-ttu-id="10f40-178">Номер внутренней идентификационной карты гражданина Чехии</span><span class="sxs-lookup"><span data-stu-id="10f40-178">Czech National Identity Card Number</span></span>
>
> <span data-ttu-id="10f40-179">Персональный идентификационный номер гражданина Дании</span><span class="sxs-lookup"><span data-stu-id="10f40-179">Denmark Personal Identification Number</span></span>
>
> <span data-ttu-id="10f40-180">Номер банковской карты для ЕС</span><span class="sxs-lookup"><span data-stu-id="10f40-180">EU Debit Card Number</span></span>
>
> <span data-ttu-id="10f40-181">Национальный идентификационный номер гражданина Финляндии</span><span class="sxs-lookup"><span data-stu-id="10f40-181">Finland National ID</span></span>
>
> <span data-ttu-id="10f40-182">Номер паспорта гражданина Финляндии</span><span class="sxs-lookup"><span data-stu-id="10f40-182">Finland Passport Number</span></span>
>
> <span data-ttu-id="10f40-183">Номер водительского удостоверения для Франции</span><span class="sxs-lookup"><span data-stu-id="10f40-183">France Driver's License Number</span></span>
>
> <span data-ttu-id="10f40-184">Национальная идентификационная карта гражданина Франции (CNI)</span><span class="sxs-lookup"><span data-stu-id="10f40-184">France National ID Card (CNI)</span></span>
>
> <span data-ttu-id="10f40-185">Номер паспорта гражданина Франции</span><span class="sxs-lookup"><span data-stu-id="10f40-185">France Passport Number</span></span>
>
> <span data-ttu-id="10f40-186">Номер социального страхования для Франции (INSEE)</span><span class="sxs-lookup"><span data-stu-id="10f40-186">France Social Security Number (INSEE)</span></span>
>
> <span data-ttu-id="10f40-187">Номер водительского удостоверения для Германии</span><span class="sxs-lookup"><span data-stu-id="10f40-187">German Driver's License Number</span></span>
>
> <span data-ttu-id="10f40-188">Номер идентификационной карты гражданина Германии</span><span class="sxs-lookup"><span data-stu-id="10f40-188">Identity Card Number
</span></span>
>
> <span data-ttu-id="10f40-189">Номер паспорта гражданина Германии</span><span class="sxs-lookup"><span data-stu-id="10f40-189">German Passport Number</span></span>
>
> <span data-ttu-id="10f40-190">Национальная идентификационная карта гражданина Греции</span><span class="sxs-lookup"><span data-stu-id="10f40-190">Greece National ID Card</span></span>
>
> <span data-ttu-id="10f40-191">Международный номер банковского счета (IBAN)</span><span class="sxs-lookup"><span data-stu-id="10f40-191">International Banking Account Number (IBAN)</span></span>
>
> <span data-ttu-id="10f40-192">IP-адрес</span><span class="sxs-lookup"><span data-stu-id="10f40-192">IP Address</span></span>
>
> <span data-ttu-id="10f40-193">Индивидуальный социальный номер (PPS) для Ирландии</span><span class="sxs-lookup"><span data-stu-id="10f40-193">Ireland Personal Public Service (PPS) Number</span></span>
>
> <span data-ttu-id="10f40-194">Номер водительского удостоверения для Италии</span><span class="sxs-lookup"><span data-stu-id="10f40-194">Italy’s Driver’s License Number</span></span>
>
> <span data-ttu-id="10f40-195">Личный номер гражданина (BSN) Нидерландов</span><span class="sxs-lookup"><span data-stu-id="10f40-195">Netherlands Citizen's Service (BSN) Number</span></span>
>
> <span data-ttu-id="10f40-196">Идентификационный номер гражданина Норвегии</span><span class="sxs-lookup"><span data-stu-id="10f40-196">Norway Identity Number</span></span>
>
> <span data-ttu-id="10f40-197">Удостоверение личности гражданина Польши</span><span class="sxs-lookup"><span data-stu-id="10f40-197">Poland Identity Card</span></span>
>
> <span data-ttu-id="10f40-198">Национальный идентификационный номер гражданина Польши (PESEL)</span><span class="sxs-lookup"><span data-stu-id="10f40-198">Poland National ID (PESEL)</span></span>
>
> <span data-ttu-id="10f40-199">Паспорт гражданина Польши</span><span class="sxs-lookup"><span data-stu-id="10f40-199">Poland Passport</span></span>
>
> <span data-ttu-id="10f40-200">Номер карты гражданина Португалии</span><span class="sxs-lookup"><span data-stu-id="10f40-200">Portugal Citizen Card Number</span></span>
>
> <span data-ttu-id="10f40-201">Номер социального страхования Испании (SSN)</span><span class="sxs-lookup"><span data-stu-id="10f40-201">Spain Social Security Number (SSN)</span></span>
>
> <span data-ttu-id="10f40-202">Национальный идентификационный номер гражданина Швеции</span><span class="sxs-lookup"><span data-stu-id="10f40-202">Sweden National ID</span></span>
>
> <span data-ttu-id="10f40-203">Номер паспорта гражданина Швеции</span><span class="sxs-lookup"><span data-stu-id="10f40-203">Sweden Passport Number</span></span>
>
> <span data-ttu-id="10f40-p111">Номер водительского удостоверения для Соединенного Королевства</span><span class="sxs-lookup"><span data-stu-id="10f40-p111">U.K. Driver's License Number</span></span>
>
> <span data-ttu-id="10f40-p112">Регистрационный номер избирателя для Соединенного Королевства</span><span class="sxs-lookup"><span data-stu-id="10f40-p112">U.K. Electoral Roll Number</span></span>
>
> <span data-ttu-id="10f40-p113">Номер национальной службы здравоохранения для Соединенного Королевства</span><span class="sxs-lookup"><span data-stu-id="10f40-p113">U.K. National Health Service Number</span></span>
>
> <span data-ttu-id="10f40-p114">Номер карты национального страхования для Соединенного Королевства (NINO)</span><span class="sxs-lookup"><span data-stu-id="10f40-p114">U.K. National Insurance Number (NINO)</span></span>
>
> <span data-ttu-id="10f40-p115">Номер паспорта гражданина США или Соединенного Королевства</span><span class="sxs-lookup"><span data-stu-id="10f40-p115">U.S. / U.K. Passport Number</span></span>

## <a name="add-parameters-to-a-sensitive-information-type-query-to-hone-the-results"></a><span data-ttu-id="10f40-214">Добавление параметров к запросу типа конфиденциальной информации для уточнения результатов</span><span class="sxs-lookup"><span data-stu-id="10f40-214">Add parameters to a sensitive information type query to hone the results</span></span>

<span data-ttu-id="10f40-215">Вы можете добавить эти параметры к запросу типа конфиденциальной информации:</span><span class="sxs-lookup"><span data-stu-id="10f40-215">You can add these parameters to a sensitive information type query:</span></span>

-   <span data-ttu-id="10f40-216">диапазон количества позволяет определить количество фрагментов конфиденциальной информации, которые должны содержаться в документе, для включения в результаты запроса;</span><span class="sxs-lookup"><span data-stu-id="10f40-216">Count range — define the number of occurrences of sensitive information a document needs to contain before it’s included in the query results.</span></span>

-   <span data-ttu-id="10f40-217">диапазон доверия — это уровень уверенности в том, что обнаруженная конфиденциальная информация действительно соответствует вашему запросу (например, значение 85, что соответствует 85 %).</span><span class="sxs-lookup"><span data-stu-id="10f40-217">Confidence range — the level of confidence that the detected sensitive type is actually a match, such as 85 (85%).</span></span>

<span data-ttu-id="10f40-218">Синтаксис:</span><span class="sxs-lookup"><span data-stu-id="10f40-218">Syntax</span></span>

-   <span data-ttu-id="10f40-219">SensitiveType:"\<тип\>|\<диапазон количества\>|\<диапазон доверия\>"</span><span class="sxs-lookup"><span data-stu-id="10f40-219">SensitiveType:”\<type\>|\<count range\>|\<confidence range\>”</span></span>

<span data-ttu-id="10f40-220">Примеры:</span><span class="sxs-lookup"><span data-stu-id="10f40-220">Examples:</span></span>

-   <span data-ttu-id="10f40-221">SensitiveType:"Номер кредитной карты|5" (возвращаются только документы, содержащие исключительно пять номеров кредитных карт)</span><span class="sxs-lookup"><span data-stu-id="10f40-221">SensitiveType:“Credit Card Number|5” (return only documents that contain exactly five credit card numbers)</span></span>

-   <span data-ttu-id="10f40-p116">SensitiveType:"Номер кредитной карты|\*|85.." (диапазон доверия составляет 85 процентов или выше)</span><span class="sxs-lookup"><span data-stu-id="10f40-p116">SensitiveType:“Credit Card Number|\*|85..” (confidence range is 85 percent or higher)</span></span>

<span data-ttu-id="10f40-224">Примечание. Элемент "SensitiveType" чувствителен к регистру, а остальные компоненты запроса — нет.</span><span class="sxs-lookup"><span data-stu-id="10f40-224">Note: “SensitiveType” is case sensitive, but the rest of the query is not.</span></span>

<span data-ttu-id="10f40-p117">Для уточнения запросов вы также можете использовать свойства и операторы. Дополнительные сведения и примеры см. в статье [Создание запроса для поиска конфиденциальных данных на сайтах](https://support.office.com/ru-RU/article/Form-a-query-to-find-sensitive-data-stored-on-sites-3019fbc5-7f15-4972-8d0e-dc182dc7f836).</span><span class="sxs-lookup"><span data-stu-id="10f40-p117">You can also use properties, and operators to illustrate how you can refine your queries. For more information and examples, see [Form a query to find sensitive data stored on sites](https://support.office.com/ru-RU/article/Form-a-query-to-find-sensitive-data-stored-on-sites-3019fbc5-7f15-4972-8d0e-dc182dc7f836).</span></span>
