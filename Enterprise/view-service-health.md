---
title: Проверка работоспособности службы Office 365
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
ms.openlocfilehash: f4bdc0f4b6faa7a3ae86580596e28e6391167340
ms.sourcegitcommit: 09985cb7894725289ef1fc8ddd90b569c285c09e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2018
ms.locfileid: "24976569"
---
# <a name="how-to-check-office-365-service-health"></a><span data-ttu-id="e2271-103">Проверка работоспособности службы Office 365</span><span class="sxs-lookup"><span data-stu-id="e2271-103">How to check Office 365 service health</span></span>

<span data-ttu-id="e2271-p101">Работоспособность Office 365, Yammer, Microsoft Dynamics CRM и облачных служб Microsoft Intune можно просмотреть на странице Office 365 **работоспособность службы** в центре администрирования. Если возникают проблемы с облачной службы, можно проверить работоспособность службы для определения, является ли это известная проблема с разрешением в процессе выполнения перед обращения в службу поддержки или тратить время устранения неполадок.</span><span class="sxs-lookup"><span data-stu-id="e2271-p101">You can view the health of Office 365, Yammer, Microsoft Dynamics CRM, and Microsoft Intune cloud services on the Office 365 **Service health** page in the admin center. If you are experiencing problems with a cloud service, you can check the service health to determine whether this is a known issue with a resolution in progress before you call support or spend time troubleshooting.</span></span> 
  
### <a name="how-to-check-service-health"></a><span data-ttu-id="e2271-106">Как проверить работоспособность службы</span><span class="sxs-lookup"><span data-stu-id="e2271-106">How to check service health</span></span>

1. <span data-ttu-id="e2271-107">Последовательно выберите пункты [https://portal.office.com/adminportal/home](https://portal.office.com/adminportal/home#/homepage) и входа в систему с учетной записью администратора.</span><span class="sxs-lookup"><span data-stu-id="e2271-107">Go to [https://portal.office.com/adminportal/home](https://portal.office.com/adminportal/home#/homepage) and sign in with an admin account.</span></span> 
    
    > [!NOTE]
    > <span data-ttu-id="e2271-p102">Людей, назначенных глобального администратора или роли администратора службы можно просмотреть работоспособность службы. Чтобы разрешить Exchange, SharePoint и Скайп для бизнеса "Администраторы" для просмотра работоспособности службы, их необходимо также назначить роль администратора службы.</span><span class="sxs-lookup"><span data-stu-id="e2271-p102">People who are assigned the global admin or service administrator role can view service health. To allow Exchange, SharePoint, and Skype for Business admins to view service health, they must also be assigned the Service admin role.</span></span> 
  
2. <span data-ttu-id="e2271-p103">Чтобы открыть работоспособность службы в центре администрирования, перейдите к **работоспособности** > **работоспособность службы**или нажмите кнопку **карты работоспособности службы** **Домашняя страница панели мониторинга**. Панель мониторинга карточки указывает, является ли проблема активной службы и ссылки на страницы работоспособности подробные службы.</span><span class="sxs-lookup"><span data-stu-id="e2271-p103">To open service health, in the admin center, go to **Health** > **Service health**, or click the **Service health card** on the **Home dashboard**. The dashboard card indicates whether there is an active service issue and links to the detailed service health page.</span></span>
    
    ![Карту панели мониторинга работоспособности службы](media/8ae3de43-7bd5-4ee9-90ed-8b5ba5f9b474.png)
  
3. <span data-ttu-id="e2271-113">Состояние работоспособности каждого облачная служба отображается в виде таблицы со значком для указания возможных состояний.</span><span class="sxs-lookup"><span data-stu-id="e2271-113">The health state of each cloud service is shown in a table format with an icon to indicate possible states.</span></span>
    
> [!TIP]
> <span data-ttu-id="e2271-114">Можно также использовать [приложение администрирования Office 365](https://go.microsoft.com/fwlink/p/?linkid=627216) на мобильном устройстве для просмотра работоспособности службы, которая — это отличный способ оставаться на связи с push-уведомлений.</span><span class="sxs-lookup"><span data-stu-id="e2271-114">You can also use the [Office 365 Admin app](https://go.microsoft.com/fwlink/p/?linkid=627216) on your mobile device to view Service health, which is a great way to stay current with push notifications.</span></span> 
  
### <a name="view-details-of-posted-service-health"></a><span data-ttu-id="e2271-115">Просмотр сведений о работоспособности сервисного</span><span class="sxs-lookup"><span data-stu-id="e2271-115">View details of posted service health</span></span>

<span data-ttu-id="e2271-p104">В представлении по умолчанию отображаются все службы и их текущее состояние работоспособности. Для фильтрации представления для служб, в настоящее время освоение происшествие выберите **Происшествия** из окна с затененными слева. **Рекомендации по** выбору будут отображаться только службы, которые в настоящий момент назначены учтена выпуска рекомендаций. Из представления **всех служб** щелкнув отображаемой службы состояний откроется представление сводки рекомендации или происшествия.</span><span class="sxs-lookup"><span data-stu-id="e2271-p104">In the default view, all services and their current health state are displayed. To filter your view to services currently experiencing an incident, select **Incidents** from the shaded bar on the left. Selecting **Advisories** will show only services that currently have an advisory posted. From the **All services** view, clicking the displayed service state will open a summary view of the advisory or incident.</span></span> 
  
![Просмотр текущего проблемы в работоспособность службы](media/f829a3af-1aca-4dc2-97eb-15d805349b24.png)
  
<span data-ttu-id="e2271-121">Рекомендации или происшествия сводки представлены следующие сведения:</span><span class="sxs-lookup"><span data-stu-id="e2271-121">The advisory or incident summary provides the following information:</span></span> 
  
![Снимок экрана меток полей в службу поддержки](media/0dd6065c-1381-4a5c-8ca0-854c3e043a5c.png)
  
1. <span data-ttu-id="e2271-123">Проблема идентификатор и Сводка инструкции о проблеме.</span><span class="sxs-lookup"><span data-stu-id="e2271-123">An issue identifier and summary statement of the problem.</span></span>
    
2. <span data-ttu-id="e2271-p105">Текущее состояние. В разделе определения состояния в этой статье описание каждого возможных состояния.</span><span class="sxs-lookup"><span data-stu-id="e2271-p105">The current status. See status definitions in this article for an explanation of each potential status.</span></span>
    
3. <span data-ttu-id="e2271-126">Описание влияния пользователи этой проблемы.</span><span class="sxs-lookup"><span data-stu-id="e2271-126">A description of how this issue can affect users.</span></span>
    
4. <span data-ttu-id="e2271-p106">Время запуска проблему и время последнего обновленного сообщение работоспособности службы. На протяжении проблему мы публиковать часто используемые сообщения сообщить о ходе выполнения, мы создаем в применение решения.</span><span class="sxs-lookup"><span data-stu-id="e2271-p106">The time that the issue was started and the last time that the service health message was updated. Throughout the duration of an issue we post frequent messages to let you know the progress that we're making in applying a solution.</span></span>
    
5. <span data-ttu-id="e2271-129">Выберите ссылку **Показать подробности** для получения дополнительных сведений о проблеме, включая журнал все сообщения, размещенные при работе на решения.</span><span class="sxs-lookup"><span data-stu-id="e2271-129">Select the **Show details** link to see more details about the issue, including the history of all messages posted while we work on a solution.</span></span> 
    
### <a name="translate-service-health-details"></a><span data-ttu-id="e2271-130">Сведения о работоспособности службы перевода</span><span class="sxs-lookup"><span data-stu-id="e2271-130">Translate service health details</span></span>

<span data-ttu-id="e2271-p107">Так как пояснения работоспособности службы публикуются в режиме реального времени, они не переносятся автоматически свой язык и сведения о службе событий доступны только на английском языке. Чтобы перевести объяснением, выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="e2271-p107">Because service health explanations are posted in real-time, they are not automatically translated to your language and the details of a service event are in English only. To translate the explanation, follow these steps:</span></span>
  
1. <span data-ttu-id="e2271-133">Перейдите на [(en)](https://www.bing.com/translator/).</span><span class="sxs-lookup"><span data-stu-id="e2271-133">Go to [Translator](https://www.bing.com/translator/).</span></span>
    
2. <span data-ttu-id="e2271-p108">На странице **работоспособность службы** выберите происшествие или рекомендации. В разделе **Показать подробности**скопируйте текст о проблеме.</span><span class="sxs-lookup"><span data-stu-id="e2271-p108">On the **Service health** page, select an incident or advisory. Under **Show details**, copy the text about the issue.</span></span>
    
3. <span data-ttu-id="e2271-136">В (en) вставьте текст и выберите команду **перевести**.</span><span class="sxs-lookup"><span data-stu-id="e2271-136">In Translator, paste the text and choose **Translate**.</span></span>
    
### <a name="definitions"></a><span data-ttu-id="e2271-137">Определения</span><span class="sxs-lookup"><span data-stu-id="e2271-137">Definitions</span></span>

<span data-ttu-id="e2271-p109">Большая часть служб время будет отображаться в работоспособном без подробных сведений. Если служба не удается, проблему помечаются как рекомендации или происшествие и отображает текущее состояние.</span><span class="sxs-lookup"><span data-stu-id="e2271-p109">Most of the time services will appear as healthy with no further information. When a service is having a problem, the issue is identified as either an advisory or an incident and shows a current status.</span></span>
  
> [!TIP]
> <span data-ttu-id="e2271-p110">Запланированного обслуживания, события не отображаемых в работоспособности службы. Всегда остается в актуальном состоянии с **Центр сообщений**можно отслеживать события запланированного технического обслуживания. Фильтровать сообщения, классифицированные как планирование изменений можно найти сведения при изменении должно произойти, влияние и подготовке к его. Для получения дополнительных сведений в разделе [Центр сообщений в Office 365](https://support.office.com/article/38fb3333-bfcc-4340-a37b-deda509c2093) .</span><span class="sxs-lookup"><span data-stu-id="e2271-p110">Planned maintenance events aren't shown in service health. You can track planned maintenance events by staying up to date with the **Message center**. Filter to messages categorized as Plan for change to find out when the change is going to happen, its effect, and how to prepare for it. See [Message center in Office 365](https://support.office.com/article/38fb3333-bfcc-4340-a37b-deda509c2093) for more details.</span></span> 
  
### <a name="incidents-and-advisories"></a><span data-ttu-id="e2271-144">Происшествия и рекомендации</span><span class="sxs-lookup"><span data-stu-id="e2271-144">Incidents and advisories</span></span>

|||
|:-----|:-----|
|![Значок сведений для рекомендации](media/a7f5fd21-c760-4948-9bc1-50f7c8070e28.png)|<span data-ttu-id="e2271-p111">Если службы показано выпуска рекомендаций, корпорации Майкрософт известно проблема, влияет на несколько пользователей, но по-прежнему доступна служба. В статье часто есть обходной путь к проблеме, и проблема может быть временная или ограничен воздействия области и пользователя.</span><span class="sxs-lookup"><span data-stu-id="e2271-p111">If a service has an advisory shown, we are aware of a problem that is affecting some users, but the service is still available. In an advisory, there is often a workaround to the problem and the problem may be intermittent or is limited in scope and user impact.</span></span>  <br/> |
|![Значок восклицательный знак для происшествия](media/a636db57-6083-44dc-bbd5-556850804f17.png)|<span data-ttu-id="e2271-p112">Если службы происшествие active показано, критические проблемы и основные функции службы или служба недоступна. Например иногда пользователи не могут отправлять и получать электронную почту или не удается входа происшествия будут иметь заметно влияние на пользователей. Если в процессе выполнения происшествие, предоставляются обновления, касающиеся исследования, по смягчению и подтверждения решение в панель мониторинга работоспособности службы.</span><span class="sxs-lookup"><span data-stu-id="e2271-p112">If a service has an active incident shown, it's a critical issue and the service or a major function of the service is unavailable. For example, users may be unable to send and receive email or unable to sign-in. Incidents will have noticeable impact to users. When there is an incident in progress, we will provide updates regarding the investigation, mitigation efforts, and confirmation of resolution in the Service health dashboard.</span></span>  <br/> |
   
### <a name="status-definitions"></a><span data-ttu-id="e2271-153">Определения состояния</span><span class="sxs-lookup"><span data-stu-id="e2271-153">Status definitions</span></span>

|<span data-ttu-id="e2271-154">**Состояние**</span><span class="sxs-lookup"><span data-stu-id="e2271-154">**Status**</span></span>|<span data-ttu-id="e2271-155">**Определение**</span><span class="sxs-lookup"><span data-stu-id="e2271-155">**Definition**</span></span>|
|:-----|:-----|
|<span data-ttu-id="e2271-156">**Исследование**</span><span class="sxs-lookup"><span data-stu-id="e2271-156">**Investigating**</span></span> | <span data-ttu-id="e2271-157">Мы полностью осведомлены о потенциальных проблем и сборе Дополнительные сведения о происходящем и пределы воздействия.</span><span class="sxs-lookup"><span data-stu-id="e2271-157">We're aware of a potential issue and are gathering more information about what's going on and the scope of impact.</span></span> |
|<span data-ttu-id="e2271-158">**Ухудшение работы службы**</span><span class="sxs-lookup"><span data-stu-id="e2271-158">**Service degradation**</span></span> | <span data-ttu-id="e2271-p113">Мы подтверждает, что существует проблема, которая может повлиять на использование службы или компонента. Пользователь видит это состояние, если служба выполняется медленно, чем обычно, существует временная перерывы или если работает компонент, например.</span><span class="sxs-lookup"><span data-stu-id="e2271-p113">We've confirmed that there is an issue that may affect use of a service or feature. You might see this status if a service is performing more slowly than usual, there are intermittent interruptions, or if a feature isn't working, for example.</span></span> |
|<span data-ttu-id="e2271-161">**Прерывания работы службы**</span><span class="sxs-lookup"><span data-stu-id="e2271-161">**Service interruption**</span></span> | <span data-ttu-id="e2271-p114">Если мы определили, что проблема затрагивает пользователям получать доступ к службе, вы увидите это состояние. В этом случае проблемы значительным и может быть воспроизведена постоянно.</span><span class="sxs-lookup"><span data-stu-id="e2271-p114">You'll see this status if we determine that an issue affects the ability for users to access the service. In this case, the issue is significant and can be reproduced consistently.</span></span> |
|<span data-ttu-id="e2271-164">**Восстановление службы**</span><span class="sxs-lookup"><span data-stu-id="e2271-164">**Restoring service**</span></span> | <span data-ttu-id="e2271-165">Обнаружена причины проблемы, мы знаем, какие исправления действия и в перенос службу обратно в работоспособном состоянии.</span><span class="sxs-lookup"><span data-stu-id="e2271-165">The cause of the issue has been identified, we know what corrective action to take, and are in the process of bringing the service back to a healthy state.</span></span> |
|<span data-ttu-id="e2271-166">**Расширенные восстановления**</span><span class="sxs-lookup"><span data-stu-id="e2271-166">**Extended recovery**</span></span> | <span data-ttu-id="e2271-p115">Это состояние указывает, что действия по устранению находится в стадии разработки для восстановления службы для большинства пользователей, но может занять некоторое время, чтобы сделать доступными в затронутых системах. Может также видит это состояние, если внесенные временное исправление для уменьшения воздействия во время ожидания для применения постоянное решение.</span><span class="sxs-lookup"><span data-stu-id="e2271-p115">This status indicates that corrective action is in progress to restore service to most users but will take some time to reach all the affected systems. You might also see this status if we've made a temporary fix to reduce impact while we wait to apply a permanent fix.</span></span> |
|<span data-ttu-id="e2271-169">**Исследование приостановлен**</span><span class="sxs-lookup"><span data-stu-id="e2271-169">**Investigation suspended**</span></span> | <span data-ttu-id="e2271-p116">Если в запросе для получения дополнительных сведений от клиентов, мы будем исследование подробное исследование потенциальные проблемы, вы увидите это состояние. Если необходимо работать, мы позволим вам узнать, какие данные или журналы перспективы.</span><span class="sxs-lookup"><span data-stu-id="e2271-p116">If our detailed investigation of a potential issue results in a request for additional information from customers to allow us to investigate further, you'll see this status. If we need you to act, we'll let you know what data or logs we need.</span></span> |
|<span data-ttu-id="e2271-172">**Служба восстановлена**</span><span class="sxs-lookup"><span data-stu-id="e2271-172">**Service restored**</span></span> | <span data-ttu-id="e2271-p117">Мы подтверждает, что действия по устранению сопоставление ее причину и службы восстановления в работоспособном состоянии. Чтобы узнать, что случилось, просмотрите сведения о проблеме.</span><span class="sxs-lookup"><span data-stu-id="e2271-p117">We've confirmed that corrective action has resolved the underlying problem and the service has been restored to a healthy state. To find out what went wrong, view the issue details.</span></span> |
|<span data-ttu-id="e2271-175">**Разбор отчет о публикации**</span><span class="sxs-lookup"><span data-stu-id="e2271-175">**Post-incident report published**</span></span> | <span data-ttu-id="e2271-176">Мы опубликовали отчет об инциденте Post определенные проблемы, включая сведения о корневом причина и дальнейшие действия, чтобы убедиться, что аналогичные проблема не возникает.</span><span class="sxs-lookup"><span data-stu-id="e2271-176">We’ve published a Post Incident Report for a specific issue that includes root cause information and next steps to ensure a similar issue doesn’t reoccur.</span></span> |
   
## <a name="history"></a><span data-ttu-id="e2271-177">журнале</span><span class="sxs-lookup"><span data-stu-id="e2271-177">History</span></span>

<span data-ttu-id="e2271-p118">Работоспособность службы позволяет просмотрите текущее состояние работоспособности и просмотреть журнал все службы рекомендации и происшествия за последние 30 дней. Чтобы просмотреть последние работоспособности всех служб, выберите команду **просмотреть журнал** на странице **работоспособность службы** .</span><span class="sxs-lookup"><span data-stu-id="e2271-p118">Service health lets you look at current health status and view the history of any service advisories and incidents in the past 30 days. To view the past health of all services, select **View history** on the **Service health** page.</span></span> 
  
![Показывать ссылку для журнала работоспособности](media/12a3e484-1eb4-497f-8cab-8064bccc2ef5.png)
  
<span data-ttu-id="e2271-181">Отображается список всех сообщений работоспособности службы, размещенные в выбранный период времени, как показано ниже:</span><span class="sxs-lookup"><span data-stu-id="e2271-181">A list of all service health messages posted in the selected timeframe is displayed, as shown below:</span></span>
  
![Просмотр журнала работоспособности службы](media/5ed20247-121c-4abe-9fe7-9025e26a2d0e.png)
  
<span data-ttu-id="e2271-p119">Можно просмотреть журнал работоспособности последние 7 дней или последние 30 дней. Выберите любую строку, чтобы просмотреть дополнительные сведения об этой проблеме.</span><span class="sxs-lookup"><span data-stu-id="e2271-p119">You may view the health history for either the last 7 days or last 30 days. Select any row to view more details about that issue.</span></span>
  
<span data-ttu-id="e2271-185">Дополнительные сведения о нашей, направленных на время работы содержатся в разделе [прозрачной операций с Office 365](https://go.microsoft.com/fwlink/?linkid=848695).</span><span class="sxs-lookup"><span data-stu-id="e2271-185">For more information about our commitment to uptime, see [Transparent operations from Office 365](https://go.microsoft.com/fwlink/?linkid=848695).</span></span>
  
## <a name="leave-feedback"></a><span data-ttu-id="e2271-186">Оставьте свои отзывы и предложения</span><span class="sxs-lookup"><span data-stu-id="e2271-186">Leave feedback</span></span>

<span data-ttu-id="e2271-p120">Цель — убедиться, что сведения, которые мы предоставить вам о проблеме, постоянная своевременного, точные и полезные. Чтобы сообщить нам как в нашем, выберите оценку. После предоставленные оценку от 1 до 5 звезд, могут предоставить свои отзывы и предложения на любой подробные сведения. Ваш отзыв будет использоваться для настройки системы работоспособности службы.</span><span class="sxs-lookup"><span data-stu-id="e2271-p120">Our goal is to make sure that the information we provide to you about an ongoing issue is timely, accurate, and useful. To tell us how we're doing, select a star rating. After you give us a score from 1 to 5 stars, you can give feedback on any specific details. We'll use your feedback to fine-tune our service health system.</span></span>
  
![Форма свои отзывы и предложения для проблемы работоспособности службы](media/fd083fdb-fde8-47b4-9136-b90d1d003864.png)
  
## <a name="see-also"></a><span data-ttu-id="e2271-192">См. также</span><span class="sxs-lookup"><span data-stu-id="e2271-192">See also</span></span>

[<span data-ttu-id="e2271-193">Отчеты об активности в центре администрирования Office 365</span><span class="sxs-lookup"><span data-stu-id="e2271-193">Activity Reports in the Office 365 admin center</span></span>](https://support.office.com/article/0d6dfb17-8582-4172-a9a9-aed798150263)

