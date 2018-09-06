---
title: Ответы на общие вопросы о перемещении данных
ms.author: deniseb
author: denisebmsft
manager: laurawi
ms.date: 09/05/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 1f01bc6f-5d37-4d14-bdd3-9d94a1e23e14
description: Здесь приведены ответы на некоторые общие вопросы о перемещении основных данных для нового географически центра обработки данных.
ms.openlocfilehash: fe2399afa81a189416c41e3acba67e53eb99c674
ms.sourcegitcommit: 75ad9af1fa8adc73611fc6140546222b001861d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/06/2018
ms.locfileid: "23839597"
---
# <a name="data-move-general-faq"></a><span data-ttu-id="0e8e9-103">Ответы на общие вопросы о перемещении данных</span><span class="sxs-lookup"><span data-stu-id="0e8e9-103">Data move general FAQ</span></span>

<span data-ttu-id="0e8e9-104">Здесь приведены ответы на некоторые общие вопросы о перемещении основных данных для нового географически центра обработки данных.</span><span class="sxs-lookup"><span data-stu-id="0e8e9-104">Here are answers to general questions about moving core data to a new datacenter geo.</span></span>
  
 <span data-ttu-id="0e8e9-105">**В. как убедиться, что данные клиента safe во время перемещения и что я не будут работать в нем?**</span><span class="sxs-lookup"><span data-stu-id="0e8e9-105">**Q. How do you make sure my customer data is safe during the move and that I won't experience downtime?**</span></span>
  
<span data-ttu-id="0e8e9-p101">Перемещение данных A. — это операция серверной службы, оказывая минимальное влияние на конечных пользователей. Функции, которые могут повлиять на работу, перечислены в [во время и после перемещения данных](during-and-after-your-data-move.md). Использования [Microsoft Online Services службы уровень соглашение](https://go.microsoft.com/fwlink/p/?LinkId=523897) для обеспечения доступности, но это не требуется для подготовки к или мониторинг во время перемещения.</span><span class="sxs-lookup"><span data-stu-id="0e8e9-p101">A. Data moves are a back-end service operation with minimal impact to end-users. Features that can be impacted are listed in [During and after your data move](during-and-after-your-data-move.md). We adhere to the [Microsoft Online Services Service Level Agreement (SLA)](https://go.microsoft.com/fwlink/p/?LinkId=523897) for availability so there is nothing that customers need to prepare for or to monitor during the move.</span></span> 
  
<span data-ttu-id="0e8e9-p102">Всех служб Office 365 запустите те же версии в центрах обработки данных, чтобы можно быть уверенным, согласованные функциональных возможностей. Службы полностью поддерживается в процессе.</span><span class="sxs-lookup"><span data-stu-id="0e8e9-p102">All Office 365 services run the same versions in the datacenters, so you can be assured of consistent functionality. Your service is fully supported throughout the process.</span></span>
  
 <span data-ttu-id="0e8e9-112">**В. что такое влияние на наличие различных служб, расположенных в различных geos?**</span><span class="sxs-lookup"><span data-stu-id="0e8e9-112">**Q. What is the impact of having different services located in different geos?**</span></span>
  
<span data-ttu-id="0e8e9-p103">А. для некоторых существующие клиенты и клиенты сбой процесса перемещения некоторые из служб Office 365 может находиться в разных geos. Запуск наших услуг независимо друг от друга и нет без влияния на пользователей, если это так.</span><span class="sxs-lookup"><span data-stu-id="0e8e9-p103">A. For some existing customers and customers in the middle of the move process, some of the Office 365 services may be located in different geos. Our services run independently of each other and there is no user impact if this is the case.</span></span>
  
 <span data-ttu-id="0e8e9-116">**В. повлияют новых клиентов Office 365 ли автоматически подготавливаться в новый geos центра обработки данных?**</span><span class="sxs-lookup"><span data-stu-id="0e8e9-116">**Q. Will new Office 365 customers be automatically provisioned in the new datacenter geos?**</span></span>
  
<span data-ttu-id="0e8e9-p104">А. После нового географически центра обработки данных доступен, новый Office 365 для предприятий, которым выберите страны право на новый geo в качестве своей страны во время регистрации будут иметь свои основных данных, размещенных в географически нового центра обработки данных.</span><span class="sxs-lookup"><span data-stu-id="0e8e9-p104">A. Yes. Once a new datacenter geo is available, new Office 365 for business customers who select a country eligible for the new geo as their country during sign-up will have their core data hosted in the new datacenter geo.</span></span>
  
 <span data-ttu-id="0e8e9-120">**Вопрос. где мои данные расположены?**</span><span class="sxs-lookup"><span data-stu-id="0e8e9-120">**Q. Where is my data is located?**</span></span>
  
<span data-ttu-id="0e8e9-p105">Мы публикация расположение geos центра обработки данных, центров обработки данных и расположение данных клиента на [сопоставляет интерактивных Office 365 центра обработки данных ](https://o365datacentermap.azurewebsites.net). По состоянию на 1 августа можно проверить расположение данных о клиентах статических через раздел расположение данных в разделе профиль организации в центре администрирования Office 365.</span><span class="sxs-lookup"><span data-stu-id="0e8e9-p105">We publish the location of datacenter geos, datacenters, and location of customer data on the [ Office 365 interactive datacenter maps ](https://o365datacentermap.azurewebsites.net). As of August 1, you will be able to verify the location of your customer data at rest via the Data Location section under your Organization Profile in the Office 365 Admin Center.</span></span>
  
 <span data-ttu-id="0e8e9-123">**Вопрос. существующие клиенты Office 365 перемещается в новый geos центра обработки данных?**</span><span class="sxs-lookup"><span data-stu-id="0e8e9-123">**Q. Will existing Office 365 customers be moved to the new datacenter geos?**</span></span>
  
<span data-ttu-id="0e8e9-p106">Office 365 подходящими а. пользователи могут запросить у своих основных данных перемещено в новый geos. Клиентам будет необходимо отправить запрос в срок для их географически для участия.</span><span class="sxs-lookup"><span data-stu-id="0e8e9-p106">A. Eligible Office 365 customers can request to have their core data moved to the new geos. Customers will need to submit a request before the deadline for their geo in order to participate.</span></span> 
  
 <span data-ttu-id="0e8e9-127">**В.: какие пользователи могут запрашивать перемещения?**</span><span class="sxs-lookup"><span data-stu-id="0e8e9-127">**Q. What customers are eligible to request a move?**</span></span>
  
<span data-ttu-id="0e8e9-p107">Выбранные страны право на новый географически центра обработки данных A. существующих Office 365 коммерческих клиентов будет запрашивать перемещения.</span><span class="sxs-lookup"><span data-stu-id="0e8e9-p107">A. Existing Office 365 commercial customers who selected a country eligible for the new datacenter geo will be able to request a move.</span></span> 
  
 <span data-ttu-id="0e8e9-130">**Вопрос. когда я будет запрашивать перемещения?**</span><span class="sxs-lookup"><span data-stu-id="0e8e9-130">**Q. When will I be able to request a move?**</span></span>
  
<span data-ttu-id="0e8e9-p108">A. на странице [запрос на перемещение данных](request-your-data-move.md) рассылаются период запроса.</span><span class="sxs-lookup"><span data-stu-id="0e8e9-p108">A. The request period will be announced on the [How to request your data move](request-your-data-move.md) page.</span></span> 
  
 <span data-ttu-id="0e8e9-133">**В. как можно запросить перемещаемых?**</span><span class="sxs-lookup"><span data-stu-id="0e8e9-133">**Q. How can I request to be moved?**</span></span>
  
<span data-ttu-id="0e8e9-p109">A. подходящими клиенты будут видеть страницы в их [Портал администрирования Office 365](https://portal.office.com/). Можно найти [по запросу перемещения данных](request-your-data-move.md) для получения инструкций по запросу перемещения.</span><span class="sxs-lookup"><span data-stu-id="0e8e9-p109">A. Eligible customers will see a page in their [Office 365 Admin Portal](https://portal.office.com/). Please see [How to request your data move](request-your-data-move.md) for instructions on how to request a move.</span></span> 
  
 <span data-ttu-id="0e8e9-137">**В. можно изменить мой выбор после выполнения запроса перемещения?**</span><span class="sxs-lookup"><span data-stu-id="0e8e9-137">**Q. Can I change my selection after requesting a move?**</span></span>
  
<span data-ttu-id="0e8e9-p110">A. она не поддерживается для нас для снятия процесс после отправки запроса.</span><span class="sxs-lookup"><span data-stu-id="0e8e9-p110">A. It is not possible for us to remove you from the process after you submit your request.</span></span>
  
 <span data-ttu-id="0e8e9-140">**В. что произойдет, если я не запрашивать move в срок?**</span><span class="sxs-lookup"><span data-stu-id="0e8e9-140">**Q. What happens if I do not request a move before the deadline?**</span></span>
  
<span data-ttu-id="0e8e9-p111">Ответ: мы не могут принимать запросы на перемещаемых после срока в каждом географически.</span><span class="sxs-lookup"><span data-stu-id="0e8e9-p111">A. We are unable to accept requests to be moved after the deadline in each geo.</span></span>
  
 <span data-ttu-id="0e8e9-143">**В. что делать, если хотите переместить данные, чтобы получить производительность сети?**</span><span class="sxs-lookup"><span data-stu-id="0e8e9-143">**Q. What if I want to move my data in order to get better network performance?**</span></span>
  
<span data-ttu-id="0e8e9-p112">Закрыть для Office 365 центра обработки данных, не является гарантией для лучшей производительности сети. Существует множество факторов и компонентов, которые влиять на производительность сети между конечных пользователей и службу Office 365. Дополнительные сведения об этом и настройка производительности в разделе [Планирование сети и настройка производительности для Office 365](network-planning-and-performance.md).</span><span class="sxs-lookup"><span data-stu-id="0e8e9-p112">Being close to an Office 365 datacenter is not a guarantee for a better networking performance. There are many factors and components that impact the network performance between the end user and the Office 365 service. For more information about this and performance tuning see [Network planning and performance tuning for Office 365](network-planning-and-performance.md).</span></span>
  
 <span data-ttu-id="0e8e9-147">**Вопрос. все службы переместить свои данные на тот же день?**</span><span class="sxs-lookup"><span data-stu-id="0e8e9-147">**Q. Do all the services move their data on the same day?**</span></span>
  
<span data-ttu-id="0e8e9-p113">A. служб не перемещаются данные в то же время. Каждая служба будет перемещать независимо друг от друга и скорее всего будут перемещаться данные в разное время.</span><span class="sxs-lookup"><span data-stu-id="0e8e9-p113">A. The services do not move their data at the same time. Each service will move independently and will likely move their data at different times.</span></span>
  
 <span data-ttu-id="0e8e9-151">**В. можно указать при требуется для перемещения личных данных?**</span><span class="sxs-lookup"><span data-stu-id="0e8e9-151">**Q. Can I choose when I want my data to be moved?**</span></span>
  
<span data-ttu-id="0e8e9-p114">A. пользователи не смогут даты, они не может отложить такого перехода, и мы не могут совместно использовать определенную дату или временной интервал для перемещений.</span><span class="sxs-lookup"><span data-stu-id="0e8e9-p114">A. Customers are not able to select a specific date, they cannot delay their move, and we cannot share a specific date or timeframe for the moves.</span></span>
  
 <span data-ttu-id="0e8e9-154">**В. можно обмениваться при Мои данные будут быть перемещены?**</span><span class="sxs-lookup"><span data-stu-id="0e8e9-154">**Q. Can you share when my data will be be moved?**</span></span>
  
<span data-ttu-id="0e8e9-p115">Перемещение данных A. — это операция серверной с минимальное влияние для конечных пользователей. Сложность, точности и масштаба, в которой необходимо выполнить перемещение данных в среде глобальной клапан и автоматической запретить "мне нравится" общий доступ к после перемещения данных ожидается в для вашего клиента или одним клиентом. Пользователи будут получать одно подтверждение в центр сообщений каждого участника службы после завершения перемещения его данных.</span><span class="sxs-lookup"><span data-stu-id="0e8e9-p115">A. Data moves are a back-end operation with minimal impact to end-users. The complexity, precision and scale at which we need to perform data moves within a globally operated and automated environment prohibit us from sharing when a data move is expected to complete for your tenant or any other single tenant. Customers will receive one confirmation in Message Center per participating service when its data move has completed.</span></span> 
  
 <span data-ttu-id="0e8e9-159">**В. что произойдет, если пользователям доступа к службам, при перемещении данных?**</span><span class="sxs-lookup"><span data-stu-id="0e8e9-159">**Q. What happens if users access services while the data is being moved?**</span></span>
  
<span data-ttu-id="0e8e9-p116">А. в разделе [во время и после перемещения данных](during-and-after-your-data-move.md) полный список компонентов, которые могут быть ограничены во время части перемещения данных для каждой службы.</span><span class="sxs-lookup"><span data-stu-id="0e8e9-p116">A. See [During and after your data move](during-and-after-your-data-move.md) for a complete list of features that may be limited during portions of the data move for each service.</span></span> 
  
 <span data-ttu-id="0e8e9-162">**В. как знаете, что ли перемещение?**</span><span class="sxs-lookup"><span data-stu-id="0e8e9-162">**Q. How do I know the move is complete?**</span></span>
  
<span data-ttu-id="0e8e9-p117">А. Просмотр центра Office 365 сообщение для подтверждения, что перемещение данных каждой службы завершен. При перемещении данных каждой службы, мы буду размещать уведомление о так вы получите три уведомления завершения: одному для каждого Exchange Online, SharePoint Online и Скайп для бизнеса в Интернет.</span><span class="sxs-lookup"><span data-stu-id="0e8e9-p117">A. Watch the Office 365 message center for confirmation that the move of each service's data is complete. When each service's data is moved, we'll post a completion notice so you'll get three completion notices: one each for Exchange Online, SharePoint Online, and Skype for Business Online.</span></span>
  
<span data-ttu-id="0e8e9-166">Если найденные проблемы отображаются после перемещения, обратитесь в службу [Поддержки Office 365](https://go.microsoft.com/fwlink/p/?LinkID=522459) для получения справки.</span><span class="sxs-lookup"><span data-stu-id="0e8e9-166">If you see any issues after the move, contact [Office 365 Support](https://go.microsoft.com/fwlink/p/?LinkID=522459) to get assistance.</span></span> 
  
 <span data-ttu-id="0e8e9-167">**В.: какие данные Office 365 хранится в новый geos центра обработки данных?**</span><span class="sxs-lookup"><span data-stu-id="0e8e9-167">**Q. What data for Office 365 is stored in the new datacenter geos?**</span></span>
  
<span data-ttu-id="0e8e9-p118">А. Если подготавливает клиента его клиента в одном из новых geos центра обработки данных, корпорация Майкрософт сохраняет следующие данные клиента статических в географически:</span><span class="sxs-lookup"><span data-stu-id="0e8e9-p118">A. If a customer provisions its tenant in one of the new datacenter geos, Microsoft stores the following customer data at rest within the geo:</span></span>
  
- <span data-ttu-id="0e8e9-170">Exchange Online содержимого почтового ящика (тела сообщения электронной почты, элементы календаря и содержимого вложений электронной почты)</span><span class="sxs-lookup"><span data-stu-id="0e8e9-170">Exchange Online mailbox content (e-mail body, calendar entries, and the content of email attachments)</span></span>
    
- <span data-ttu-id="0e8e9-171">SharePoint Online контента сайта и файлы, хранящиеся в пределах этого сайта, включая контент Project Online и доступа к сети.</span><span class="sxs-lookup"><span data-stu-id="0e8e9-171">SharePoint Online site content and the files stored within that site, including Project Online and Access Online content.</span></span>
    
<span data-ttu-id="0e8e9-172">Кроме того эти данные не реплицируются за пределы географически.</span><span class="sxs-lookup"><span data-stu-id="0e8e9-172">In addition, this data is not replicated outside of the geo.</span></span>
  
 <span data-ttu-id="0e8e9-173">**Вопрос. я на клиента Office 365 в одном из новых geos центра обработки данных, но подписанные я выбран другой стране. Как можно ли переместить новые географически центра обработки данных?**</span><span class="sxs-lookup"><span data-stu-id="0e8e9-173">**Q. I am an Office 365 customer in one of the new datacenter geos, but when I signed up, I selected a different country. How can I be moved to the new datacenter geo?**</span></span>
  
<span data-ttu-id="0e8e9-p119">А. к сожалению не является возможность изменения страны, связанные с вашего клиента. Вместо этого необходимо создать новый клиент Office 365 с новой подписки и вручную переместите пользователей и данных в новый клиент.</span><span class="sxs-lookup"><span data-stu-id="0e8e9-p119">A. Unfortunately, it is not possible to change the country associated with your tenant. Instead, you need to create a new Office 365 tenant with a new subscription and manually move your users and data to the new tenant.</span></span>
  
 <span data-ttu-id="0e8e9-177">**Повлияют ли все изменения на мой Билл?**</span><span class="sxs-lookup"><span data-stu-id="0e8e9-177">**Q. Will there be any changes on my bill?**</span></span>
  
<span data-ttu-id="0e8e9-p120">А. в большинстве случаев нет изменений, которые клиенты в будут видеть на их выставления счетов оператора.</span><span class="sxs-lookup"><span data-stu-id="0e8e9-p120">A. In most cases there are no changes that customers in will see on their billing statement.</span></span>
  
<span data-ttu-id="0e8e9-p121">Корпорация Майкрософт издержки всех Австралии клиентов Office 365 дополнительного равно Австралии GST для служб Office 365 и выпустит tax счетов. Это изменение будет возникать Австралии GST с поставщиками на Налогооблагаемый питания товаров отмеченными и предложенные в Австралии служб.</span><span class="sxs-lookup"><span data-stu-id="0e8e9-p121">Microsoft will charge all Australian customers of Office 365 an additional amount equal to the Australian GST for Office 365 services and will issue tax invoices. This change will occur because Australian GST is payable on taxable supplies of goods and services provided and offered in Australia.</span></span>
  
 <span data-ttu-id="0e8e9-182">**В. что произойдет, если мы находящихся миграция данных электронной почты в Office 365 во время перемещения Exchange Online?**</span><span class="sxs-lookup"><span data-stu-id="0e8e9-182">**Q. What happens if we are in process of email data migration to Office 365 during the Exchange Online move?**</span></span>
  
<span data-ttu-id="0e8e9-p122">А. при миграции электронной почты находятся в процессе выполнения, отдельных почтовых ящиков, которые переносятся в настоящее время будет отменена во время перемещения клиента завершает и после загрузки клиента в центрах обработки данных конечного автоматически перезапустит миграции этих почтовых ящиков.</span><span class="sxs-lookup"><span data-stu-id="0e8e9-p122">A. If email migrations are in progress, any individual mailboxes that are currently being migrated will be canceled while the tenant move finalizes, and migration of those mailboxes will automatically restart once the tenant is in the target datacenters.</span></span>
  
 <span data-ttu-id="0e8e9-185">**Вопрос. после данных при перемещении из предыдущей географически центра обработки данных, он удаляется из этих центров обработки данных?**</span><span class="sxs-lookup"><span data-stu-id="0e8e9-185">**Q. After data is moved out of the previous datacenter geo, is it removed from those datacenters?**</span></span>
  
<span data-ttu-id="0e8e9-p123">О. Да, после определенного периода времени, будут очищены старые данные.</span><span class="sxs-lookup"><span data-stu-id="0e8e9-p123">A. Yes, the old data will be purged after a period of time.</span></span>
  
 <span data-ttu-id="0e8e9-188">**В. можно Пилотное некоторых пользователей?**</span><span class="sxs-lookup"><span data-stu-id="0e8e9-188">**Q. Can I pilot some users?**</span></span>
  
<span data-ttu-id="0e8e9-p124">А. при перемещении клиента Office 365 для нового географически центра обработки данных, все пользователи перемещаются за один раз. Можно создать отдельные пробной версии клиента можно проверить возможность подключения, но нельзя сочетать пробной версии клиента никаких уведомлений с помощью существующего клиента.</span><span class="sxs-lookup"><span data-stu-id="0e8e9-p124">A. When your Office 365 tenant is moved to a new datacenter geo, all users are moved at once. You can create a separate trial tenant to test connectivity, but the trial tenant can't be combined in any way with your existing tenant.</span></span>
  
 <span data-ttu-id="0e8e9-192">**Вопрос. как получу о перемещение и пользователей, которые в моей организации будет получать уведомления?**</span><span class="sxs-lookup"><span data-stu-id="0e8e9-192">**Q. How will I be notified about the move and who at my company will be notified?**</span></span>
  
<span data-ttu-id="0e8e9-p125">А. Мы будем использовать центр сообщений Office 365, которая доступна всем пользователям с правами администратора в Office 365.</span><span class="sxs-lookup"><span data-stu-id="0e8e9-p125">A. We'll use the Office 365 message center, which is visible to anyone with any admin permissions in Office 365.</span></span>
  
 <span data-ttu-id="0e8e9-195">**Вопрос. я не хочу ожидать в Майкрософт для переноса данных. Можно ли только что создать новый клиент и перемещение проблемы?**</span><span class="sxs-lookup"><span data-stu-id="0e8e9-195">**Q. I don't want to wait for Microsoft to move my data. Can I just create a new tenant and move myself?**</span></span>
  
<span data-ttu-id="0e8e9-p126">A. Да, но процесс не будет максимально эффективным, как если бы корпорация Майкрософт перенос данных.</span><span class="sxs-lookup"><span data-stu-id="0e8e9-p126">A. Yes, however the process will not be as seamless as if Microsoft were to perform the data move.</span></span>
  
<span data-ttu-id="0e8e9-p127">При создании нового клиента после нового географически центра обработки данных доступен новый клиент будет размещаться в новый географически. Этот новый клиент отделена от предыдущего клиента и может быть отвечает за перемещение всех почтовых ящиков пользователей, контента веб-сайта, имена доменов и другие данные. Обратите внимание, что нельзя переместить имя клиента от одного клиента в другой. Мы рекомендуем дождитесь программы move, предоставляемым корпорацией Майкрософт, которые мы будем взяла на себя перемещение всех параметров, данных и подписок для пользователей.</span><span class="sxs-lookup"><span data-stu-id="0e8e9-p127">If you create a new tenant after the new datacenter geo is available, the new tenant will be hosted in the new geo. This new tenant is completely separate from your previous tenant and you would be responsible for moving all user mailboxes, site content, domain names, and any other data. Note that you can't move the tenant name from one tenant to another. We recommend that you wait for the move program provided by Microsoft as we'll take care of moving all settings, data, and subscriptions for your users.</span></span>
  
 <span data-ttu-id="0e8e9-202">**Вопрос. я не готово для перемещения, можно ли подбор конкретных move date?**</span><span class="sxs-lookup"><span data-stu-id="0e8e9-202">**Q. I'm not ready to be moved, can I pick a specific move date?**</span></span>
  
<span data-ttu-id="0e8e9-p128">A. она не позволяет изменить, когда данные клиента каждой службы будут перемещены. Перемещение данных — это операция серверной с минимальное влияние для конечных пользователей.</span><span class="sxs-lookup"><span data-stu-id="0e8e9-p128">A. It is not possible for you to change when each service's customer data will be moved. Data moves are a back-end operation with minimal impact to end-users.</span></span>
  
 <span data-ttu-id="0e8e9-206">**В. в моей данные клиента уже была перемещена в новый географически центра обработки данных. Можно переместить назад?**</span><span class="sxs-lookup"><span data-stu-id="0e8e9-206">**Q. My customer data has already been moved to a new datacenter geo. Can I move back?**</span></span>
  
<span data-ttu-id="0e8e9-p129">А. это невозможно. Пользователи, которые были перемещены в новый географически центров обработки данных, нельзя перемещать обратно. Как клиента в любой географически смогут работать же качества службы, производительности и безопасности элементов управления, как это делалось ранее.</span><span class="sxs-lookup"><span data-stu-id="0e8e9-p129">A. This is not possible. Customers who have been moved to new geo datacenters cannot be moved back. As a customer in any geo, you will experience the same quality of service, performance, and security controls as you did before.</span></span>
  
 <span data-ttu-id="0e8e9-211">**Вопрос. новый geos центра обработки данных используйте те же версии служб Office 365 как текущий geos центра обработки данных?**</span><span class="sxs-lookup"><span data-stu-id="0e8e9-211">**Q. Do the new datacenter geos use the same versions of Office 365 services as the current datacenter geos?**</span></span>
  
<span data-ttu-id="0e8e9-p130">А.</span><span class="sxs-lookup"><span data-stu-id="0e8e9-p130">A. Yes.</span></span>
  
 <span data-ttu-id="0e8e9-214">**Вопрос. клиентов будет Office 365, размещенные в новый центров обработки данных доступен для пользователей за пределами страны?**</span><span class="sxs-lookup"><span data-stu-id="0e8e9-214">**Q. Will Office 365 tenants hosted in the new datacenters be available to users outside of the country?**</span></span>
  
<span data-ttu-id="0e8e9-p131">А. Корпорация Майкрософт поддерживает большие глобальная сеть с общей подключения к Интернету в более чем 50 расположений в 23 странах мира с авторами соглашения с более 1 500 поставщиков услуг Интернета (поставщики). Пользователи смогут получить доступ к центров обработки данных из любого места в Интернете.</span><span class="sxs-lookup"><span data-stu-id="0e8e9-p131">A. Yes. Microsoft maintains a large global network with public Internet connections in more than 50 locations in 23 countries around the world with peering agreements with more than 1,500 Internet Service Providers (ISPs). Users will be able to access the datacenters from wherever they are on the Internet.</span></span>
  
## <a name="related-topics"></a><span data-ttu-id="0e8e9-219">Смежные темы</span><span class="sxs-lookup"><span data-stu-id="0e8e9-219">Related topics</span></span>

[<span data-ttu-id="0e8e9-220">Перемещение основных данных в новый Office 365 geos центра обработки данных</span><span class="sxs-lookup"><span data-stu-id="0e8e9-220">Moving core data to new Office 365 datacenter geos</span></span>](moving-data-to-new-datacenter-geos.md)

[<span data-ttu-id="0e8e9-221">Как запросить перемещение данных</span><span class="sxs-lookup"><span data-stu-id="0e8e9-221">How to request your data move</span></span>](request-your-data-move.md)

[<span data-ttu-id="0e8e9-222">Новые geos центра обработки данных для Microsoft Dynamics CRM Online</span><span class="sxs-lookup"><span data-stu-id="0e8e9-222">New datacenter geos for Microsoft Dynamics CRM Online</span></span>](https://go.microsoft.com/fwlink/p/?Linkid=615924)
  
[<span data-ttu-id="0e8e9-223">Служб Azure по регионам</span><span class="sxs-lookup"><span data-stu-id="0e8e9-223">Azure services by region</span></span>](https://azure.microsoft.com/en-us/regions/)
