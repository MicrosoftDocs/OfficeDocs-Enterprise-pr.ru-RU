---
title: Проверка работоспособности служб Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: article
f1_keywords:
- O365P_ServiceHealthModern
- O365M_ServiceHealthModern
- O365E_ViewStatusServices
- O365E_ServiceHealthModern
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
- IWA160
ms.assetid: 932ad3ad-533c-418a-b938-6e44e8bc33b0
description: Просмотр состояния работоспособности службы Office 365 перед вызовом поддержки ли прерывании активной службы
ms.openlocfilehash: 7e04e1309c990ccced67663576285f7276603ccc
ms.sourcegitcommit: 6826e0ea4a777f7d98500209a9d3bc75e89f8d15
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/30/2019
ms.locfileid: "29651193"
---
# <a name="how-to-check-office-365-service-health"></a><span data-ttu-id="2a9dc-103">Проверка работоспособности служб Office 365</span><span class="sxs-lookup"><span data-stu-id="2a9dc-103">How to check Office 365 service health</span></span>

<span data-ttu-id="2a9dc-p101">Работоспособность Office 365, Yammer, Microsoft Dynamics CRM и облачных служб Microsoft Intune можно просмотреть на странице Office 365 **работоспособность службы** в центре администрирования. Если возникают проблемы с облачной службы, можно проверить работоспособность службы для определения, является ли это известная проблема с разрешением в процессе выполнения перед обращения в службу поддержки или тратить время устранения неполадок.</span><span class="sxs-lookup"><span data-stu-id="2a9dc-p101">You can view the health of Office 365, Yammer, Microsoft Dynamics CRM, and Microsoft Intune cloud services on the Office 365 **Service health** page in the admin center. If you are experiencing problems with a cloud service, you can check the service health to determine whether this is a known issue with a resolution in progress before you call support or spend time troubleshooting.</span></span> 

<span data-ttu-id="2a9dc-106">Если не удается выполнить вход на портал службы, можно использовать [страницу состояния службы](https://status.office365.com) на наличие известных проблем, предотвращая ведения журнала в клиент.</span><span class="sxs-lookup"><span data-stu-id="2a9dc-106">If you are unable to sign in to the service portal, you can use the [service status page](https://status.office365.com) to check for known issues preventing you from logging into your tenant.</span></span>
  
### <a name="how-to-check-service-health"></a><span data-ttu-id="2a9dc-107">Проверка работоспособности службы</span><span class="sxs-lookup"><span data-stu-id="2a9dc-107">How to check service health</span></span>

1. <span data-ttu-id="2a9dc-108">Войдите с учетной записью администратора на портал [https://portal.office.com/adminportal/home](https://portal.office.com/adminportal/home#/homepage).</span><span class="sxs-lookup"><span data-stu-id="2a9dc-108">Go to [https://portal.office.com/adminportal/home](https://portal.office.com/adminportal/home#/homepage) and sign in with an admin account.</span></span> 
    
    > [!NOTE]
    > <span data-ttu-id="2a9dc-p102">Для просмотра сведений о работоспособности требуется роль глобального администратора или администратора службы. Чтобы разрешить администраторам Exchange, SharePoint и Skype для бизнеса просматривать сведения о работоспособности служб, необходимо также назначить им роль администратора служб.</span><span class="sxs-lookup"><span data-stu-id="2a9dc-p102">People who are assigned the global admin or service administrator role can view service health. To allow Exchange, SharePoint, and Skype for Business admins to view service health, they must also be assigned the Service admin role.</span></span>
  
2. <span data-ttu-id="2a9dc-p103">Чтобы открыть работоспособность службы в центре администрирования, перейдите к **работоспособности** > **работоспособность службы**или нажмите кнопку **карты работоспособности службы** **Домашняя страница панели мониторинга**. Панель мониторинга карточки указывает, является ли проблема активной службы и ссылки на страницы работоспособности подробные службы.</span><span class="sxs-lookup"><span data-stu-id="2a9dc-p103">To open service health, in the admin center, go to **Health** > **Service health**, or click the **Service health card** on the **Home dashboard**. The dashboard card indicates whether there is an active service issue and links to the detailed service health page.</span></span>
    
    ![Dashboard card for service health](media/8ae3de43-7bd5-4ee9-90ed-8b5ba5f9b474.png)
  
3. <span data-ttu-id="2a9dc-114">Состояние работоспособности облачных служб представлено с помощью значков в таблице.</span><span class="sxs-lookup"><span data-stu-id="2a9dc-114">The health state of each cloud service is shown in a table format with an icon to indicate possible states.</span></span>
    
> [!TIP]
> <span data-ttu-id="2a9dc-115">Вы также можете просматривать работоспособность службы через приложение [Администратор Office 365](https://go.microsoft.com/fwlink/p/?linkid=627216) и получать push-уведомления на мобильном устройстве.</span><span class="sxs-lookup"><span data-stu-id="2a9dc-115">You can also use the [Office 365 Admin app](https://go.microsoft.com/fwlink/p/?linkid=627216) on your mobile device to view Service health, which is a great way to stay current with push notifications.</span></span> 
  
### <a name="view-details-of-posted-service-health"></a><span data-ttu-id="2a9dc-116">Просмотр опубликованных сведений о работоспособности службы</span><span class="sxs-lookup"><span data-stu-id="2a9dc-116">View details of posted service health</span></span>

<span data-ttu-id="2a9dc-p104">В представлении по умолчанию отображаются все службы и их текущее состояние работоспособности. Для фильтрации представления для служб, в настоящее время освоение происшествие выберите **Происшествия** из окна с затененными слева. **Рекомендации по** выбору будут отображаться только службы, которые в настоящий момент назначены учтена выпуска рекомендаций. Из представления **всех служб** щелкнув отображаемой службы состояний откроется представление сводки рекомендации или происшествия.</span><span class="sxs-lookup"><span data-stu-id="2a9dc-p104">In the default view, all services and their current health state are displayed. To filter your view to services currently experiencing an incident, select **Incidents** from the shaded bar on the left. Selecting **Advisories** will show only services that currently have an advisory posted. From the **All services** view, clicking the displayed service state will open a summary view of the advisory or incident.</span></span> 
  
![View of current issues in service health](media/f829a3af-1aca-4dc2-97eb-15d805349b24.png)
  
<span data-ttu-id="2a9dc-122">В сводку включена следующая информация:</span><span class="sxs-lookup"><span data-stu-id="2a9dc-122">The advisory or incident summary provides the following information:</span></span> 
  
![Снимок экрана меток полей в службу поддержки](media/0dd6065c-1381-4a5c-8ca0-854c3e043a5c.png)
  
1. <span data-ttu-id="2a9dc-124">Идентификатор проблемы и ее краткое описание.</span><span class="sxs-lookup"><span data-stu-id="2a9dc-124">An issue identifier and summary statement of the problem.</span></span>
    
2. <span data-ttu-id="2a9dc-p105">Текущее состояние. Определения состояний вы найдете в этой статье.</span><span class="sxs-lookup"><span data-stu-id="2a9dc-p105">The current status. See status definitions in this article for an explanation of each potential status.</span></span>
    
3. <span data-ttu-id="2a9dc-127">Описание того, как эта проблема может повлиять на пользователей.</span><span class="sxs-lookup"><span data-stu-id="2a9dc-127">A description of how this issue can affect users.</span></span>
    
4. <span data-ttu-id="2a9dc-p106">Время возникновения проблемы и время последнего обновления сообщения о работоспособности службы. Пока проблема не будет устранена, мы публикуем частые сообщения о ходе ее решения.</span><span class="sxs-lookup"><span data-stu-id="2a9dc-p106">The time that the issue was started and the last time that the service health message was updated. Throughout the duration of an issue we post frequent messages to let you know the progress that we're making in applying a solution.</span></span>
    
5. <span data-ttu-id="2a9dc-130">Щелкните ссылку **Показать сведения**, чтобы просмотреть дополнительную информацию о проблеме, включая журнал всех сообщений, опубликованных при работе над ее решением.</span><span class="sxs-lookup"><span data-stu-id="2a9dc-130">Select the **Show details** link to see more details about the issue, including the history of all messages posted while we work on a solution.</span></span> 
    
### <a name="translate-service-health-details"></a><span data-ttu-id="2a9dc-131">Перевод сведений о работоспособности службы</span><span class="sxs-lookup"><span data-stu-id="2a9dc-131">Translate service health details</span></span>

<span data-ttu-id="2a9dc-p107">Так как сведения о работоспособности служб публикуются в режиме реального времени, они предлагаются только на английском языке и не переводятся автоматически. Чтобы перевести объяснения, выполните следующие действия:</span><span class="sxs-lookup"><span data-stu-id="2a9dc-p107">Because service health explanations are posted in real-time, they are not automatically translated to your language and the details of a service event are in English only. To translate the explanation, follow these steps:</span></span>
  
1. <span data-ttu-id="2a9dc-134">Перейдите на сайт [Переводчика](https://www.bing.com/translator/).</span><span class="sxs-lookup"><span data-stu-id="2a9dc-134">Go to [Translator](https://www.bing.com/translator/).</span></span>
    
2. <span data-ttu-id="2a9dc-p108">На странице **Работоспособность службы** выберите инцидент или рекомендацию. В разделе **Показать сведения** скопируйте текст.</span><span class="sxs-lookup"><span data-stu-id="2a9dc-p108">On the **Service health** page, select an incident or advisory. Under **Show details**, copy the text about the issue.</span></span>
    
3. <span data-ttu-id="2a9dc-137">Вставьте текст в Переводчик и нажмите кнопку **Translate** (Перевести).</span><span class="sxs-lookup"><span data-stu-id="2a9dc-137">In Translator, paste the text and choose **Translate**.</span></span>
    
### <a name="definitions"></a><span data-ttu-id="2a9dc-138">Определения</span><span class="sxs-lookup"><span data-stu-id="2a9dc-138">Definitions</span></span>

<span data-ttu-id="2a9dc-p109">Большую часть времени службы будут работоспособны, а дополнительные сведения не будут отображаться. Если в службе возникла проблема, выводится инцидент или рекомендация, а также сведения о текущем состоянии.</span><span class="sxs-lookup"><span data-stu-id="2a9dc-p109">Most of the time services will appear as healthy with no further information. When a service is having a problem, the issue is identified as either an advisory or an incident and shows a current status.</span></span>
  
> [!TIP]
> <span data-ttu-id="2a9dc-p110">На странице "Работоспособность служб" не указываются запланированные мероприятия технического обслуживания. Для их отслеживания предназначен **Центр сообщений**. Отфильтруйте сообщения с категорией Plan for change (Подготовьтесь к изменениям), чтобы узнать, когда должно произойти изменение, на что оно повлияет и как к нему подготовиться. Дополнительные сведения см. в статье [Центр сообщений в Office 365](https://support.office.com/article/38fb3333-bfcc-4340-a37b-deda509c2093).</span><span class="sxs-lookup"><span data-stu-id="2a9dc-p110">Planned maintenance events aren't shown in service health. You can track planned maintenance events by staying up to date with the **Message center**. Filter to messages categorized as Plan for change to find out when the change is going to happen, its effect, and how to prepare for it. See [Message center in Office 365](https://support.office.com/article/38fb3333-bfcc-4340-a37b-deda509c2093) for more details.</span></span> 
  
### <a name="incidents-and-advisories"></a><span data-ttu-id="2a9dc-145">Инциденты и рекомендации</span><span class="sxs-lookup"><span data-stu-id="2a9dc-145">Incidents and advisories</span></span>

|||
|:-----|:-----|
|![Information icon for advisory](media/a7f5fd21-c760-4948-9bc1-50f7c8070e28.png)|<span data-ttu-id="2a9dc-p111">Если для службы выводятся рекомендации, это значит, что нам известно о проблеме, которая касается некоторых пользователей, но служба по-прежнему доступна. В рекомендации часто указывается временное решение проблемы, которая может быть непостоянной или иметь ограниченное воздействие.</span><span class="sxs-lookup"><span data-stu-id="2a9dc-p111">If a service has an advisory shown, we are aware of a problem that is affecting some users, but the service is still available. In an advisory, there is often a workaround to the problem and the problem may be intermittent or is limited in scope and user impact.</span></span>  <br/> |
|![Exclamation point icon for incident](media/a636db57-6083-44dc-bbd5-556850804f17.png)|<span data-ttu-id="2a9dc-p112">Если для службы указан инцидент, это критическая проблема, а служба или ее основные функции недоступны. Например, может не работать отправка и получение электронной почты или вход в службу. Инциденты оказывают заметное влияние на пользователей. При возникновении инцидентов мы будем публиковать на информационной панели новости об их изучении и устранении, а также сообщения о том, что проблема решена.</span><span class="sxs-lookup"><span data-stu-id="2a9dc-p112">If a service has an active incident shown, it's a critical issue and the service or a major function of the service is unavailable. For example, users may be unable to send and receive email or unable to sign-in. Incidents will have noticeable impact to users. When there is an incident in progress, we will provide updates regarding the investigation, mitigation efforts, and confirmation of resolution in the Service health dashboard.</span></span>  <br/> |
   
### <a name="status-definitions"></a><span data-ttu-id="2a9dc-154">Определения состояний</span><span class="sxs-lookup"><span data-stu-id="2a9dc-154">Status definitions</span></span>

|<span data-ttu-id="2a9dc-155">**Состояние**</span><span class="sxs-lookup"><span data-stu-id="2a9dc-155">**Status**</span></span>|<span data-ttu-id="2a9dc-156">**Определение**</span><span class="sxs-lookup"><span data-stu-id="2a9dc-156">**Definition**</span></span>|
|:-----|:-----|
|<span data-ttu-id="2a9dc-157">**Изучение**</span><span class="sxs-lookup"><span data-stu-id="2a9dc-157">**Investigating**</span></span> | <span data-ttu-id="2a9dc-158">Мы знаем о возможной проблеме и собираем дополнительные сведения о ней и ее влиянии.</span><span class="sxs-lookup"><span data-stu-id="2a9dc-158">We're aware of a potential issue and are gathering more information about what's going on and the scope of impact.</span></span> |
|<span data-ttu-id="2a9dc-159">**Производительность службы снижена**</span><span class="sxs-lookup"><span data-stu-id="2a9dc-159">**Service degradation**</span></span> | <span data-ttu-id="2a9dc-p113">Мы подтвердили, что проблема может повлиять на использование служб или функций. Это состояние может отображаться, если служба работает медленнее, чем обычно, периодически возникают прерывания или если недоступна определенная функция.</span><span class="sxs-lookup"><span data-stu-id="2a9dc-p113">We've confirmed that there is an issue that may affect use of a service or feature. You might see this status if a service is performing more slowly than usual, there are intermittent interruptions, or if a feature isn't working, for example.</span></span> |
|<span data-ttu-id="2a9dc-162">**Работа службы прервана**</span><span class="sxs-lookup"><span data-stu-id="2a9dc-162">**Service interruption**</span></span> | <span data-ttu-id="2a9dc-p114">Вы увидите это состояние, если определено, что проблема влияет на доступ к службе. В этом случае проблема является значительной и ее можно воспроизвести.</span><span class="sxs-lookup"><span data-stu-id="2a9dc-p114">You'll see this status if we determine that an issue affects the ability for users to access the service. In this case, the issue is significant and can be reproduced consistently.</span></span> |
|<span data-ttu-id="2a9dc-165">**Восстановление службы**</span><span class="sxs-lookup"><span data-stu-id="2a9dc-165">**Restoring service**</span></span> | <span data-ttu-id="2a9dc-166">Причина проблемы определена, мы знаем, как ее решить, и восстанавливаем службу.</span><span class="sxs-lookup"><span data-stu-id="2a9dc-166">The cause of the issue has been identified, we know what corrective action to take, and are in the process of bringing the service back to a healthy state.</span></span> |
|<span data-ttu-id="2a9dc-167">**Длительное восстановление**</span><span class="sxs-lookup"><span data-stu-id="2a9dc-167">**Extended recovery**</span></span> | <span data-ttu-id="2a9dc-p115">Это состояние указывает на то, что работа над восстановлением службы идет, но пройдет некоторое время, прежде чем она станет доступна для всех затронутых систем. Это состояние также отображается, если мы применили временное исправление, чтобы уменьшить влияние проблемы, пока готовится постоянное исправление.</span><span class="sxs-lookup"><span data-stu-id="2a9dc-p115">This status indicates that corrective action is in progress to restore service to most users but will take some time to reach all the affected systems. You might also see this status if we've made a temporary fix to reduce impact while we wait to apply a permanent fix.</span></span> |
|<span data-ttu-id="2a9dc-170">**Исследование приостановлено**</span><span class="sxs-lookup"><span data-stu-id="2a9dc-170">**Investigation suspended**</span></span> | <span data-ttu-id="2a9dc-p116">Это состояние отображается, если для дальнейшего исследования необходимы дополнительные сведения. В случае если от вас требуются определенные действия, мы дадим вам знать, какие данные или журналы нам нужны.</span><span class="sxs-lookup"><span data-stu-id="2a9dc-p116">If our detailed investigation of a potential issue results in a request for additional information from customers to allow us to investigate further, you'll see this status. If we need you to act, we'll let you know what data or logs we need.</span></span> |
|<span data-ttu-id="2a9dc-173">**Служба восстановлена**</span><span class="sxs-lookup"><span data-stu-id="2a9dc-173">**Service restored**</span></span> | <span data-ttu-id="2a9dc-p117">Мы убедились, что проблема была решена, а работоспособность службы восстановлена. Чтобы узнать, в чем было дело, просмотрите сведения о проблеме.</span><span class="sxs-lookup"><span data-stu-id="2a9dc-p117">We've confirmed that corrective action has resolved the underlying problem and the service has been restored to a healthy state. To find out what went wrong, view the issue details.</span></span> |
|<span data-ttu-id="2a9dc-176">**Разбор отчет о публикации**</span><span class="sxs-lookup"><span data-stu-id="2a9dc-176">**Post-incident report published**</span></span> | <span data-ttu-id="2a9dc-177">Мы опубликовали отчет об инциденте Post определенные проблемы, включая сведения о корневом причина и дальнейшие действия, чтобы убедиться, что аналогичные проблема не возникает.</span><span class="sxs-lookup"><span data-stu-id="2a9dc-177">We’ve published a Post Incident Report for a specific issue that includes root cause information and next steps to ensure a similar issue doesn’t reoccur.</span></span> |
   
## <a name="history"></a><span data-ttu-id="2a9dc-178">журнале</span><span class="sxs-lookup"><span data-stu-id="2a9dc-178">History</span></span>

<span data-ttu-id="2a9dc-p118">Вы можете узнать не только текущее состояние службы, но и просмотреть журнал рекомендаций и инцидентов за последние 30 дней. Для этого щелкните ссылку **Просмотреть журнал** на странице **Работоспособность службы**.</span><span class="sxs-lookup"><span data-stu-id="2a9dc-p118">Service health lets you look at current health status and view the history of any service advisories and incidents in the past 30 days. To view the past health of all services, select **View history** on the **Service health** page.</span></span> 
  
![Show link to health history](media/12a3e484-1eb4-497f-8cab-8064bccc2ef5.png)
  
<span data-ttu-id="2a9dc-182">Появится список всех сообщений о работоспособности службы, опубликованных за выбранный период времени, как показано ниже:</span><span class="sxs-lookup"><span data-stu-id="2a9dc-182">A list of all service health messages posted in the selected timeframe is displayed, as shown below:</span></span>
  
![View service health history](media/5ed20247-121c-4abe-9fe7-9025e26a2d0e.png)
  
<span data-ttu-id="2a9dc-p119">Можно просмотреть журнал работоспособности последние 7 дней или последние 30 дней. Выберите любую строку, чтобы просмотреть дополнительные сведения об этой проблеме.</span><span class="sxs-lookup"><span data-stu-id="2a9dc-p119">You may view the health history for either the last 7 days or last 30 days. Select any row to view more details about that issue.</span></span>
  
<span data-ttu-id="2a9dc-186">Дополнительные сведения о нашей, направленных на время работы содержатся в разделе [прозрачной операций с Office 365](https://go.microsoft.com/fwlink/?linkid=848695).</span><span class="sxs-lookup"><span data-stu-id="2a9dc-186">For more information about our commitment to uptime, see [Transparent operations from Office 365](https://go.microsoft.com/fwlink/?linkid=848695).</span></span>
  
## <a name="leave-feedback"></a><span data-ttu-id="2a9dc-187">Оставьте свой отзыв</span><span class="sxs-lookup"><span data-stu-id="2a9dc-187">Leave feedback</span></span>

<span data-ttu-id="2a9dc-p120">Мы стремимся предоставлять своевременную, точную и полезную информацию о возникающих проблемах. Поставьте нам оценку от 1 до 5, чтобы мы знали, хорошо ли это у нас получается. Кроме того, вы можете изложить свое мнение более подробно. Благодаря вашим отзывам мы совершенствуем сообщения о работоспособности службы.</span><span class="sxs-lookup"><span data-stu-id="2a9dc-p120">Our goal is to make sure that the information we provide to you about an ongoing issue is timely, accurate, and useful. To tell us how we're doing, select a star rating. After you give us a score from 1 to 5 stars, you can give feedback on any specific details. We'll use your feedback to fine-tune our service health system.</span></span>
  
![Feedback form for service health issues](media/fd083fdb-fde8-47b4-9136-b90d1d003864.png)
  
## <a name="see-also"></a><span data-ttu-id="2a9dc-193">См. также</span><span class="sxs-lookup"><span data-stu-id="2a9dc-193">See also</span></span>

[<span data-ttu-id="2a9dc-194">Отчеты об активности в центре администрирования Office 365</span><span class="sxs-lookup"><span data-stu-id="2a9dc-194">Activity Reports in the Office 365 admin center</span></span>](https://support.office.com/article/0d6dfb17-8582-4172-a9a9-aed798150263)

