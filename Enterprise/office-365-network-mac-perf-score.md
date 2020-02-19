---
title: Оценка сети Office 365 (Предварительная версия)
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 02/04/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
description: Оценка сети Office 365 (Предварительная версия)
ms.openlocfilehash: f919eeb2771095502865b4a5079b91eb8d7efe36
ms.sourcegitcommit: e2f7bb4ccd4c74902235f680104ca6b56c051587
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/19/2020
ms.locfileid: "42106419"
---
# <a name="office-365-network-assessment-preview"></a><span data-ttu-id="98c35-103">Оценка сети Office 365 (Предварительная версия)</span><span class="sxs-lookup"><span data-stu-id="98c35-103">Office 365 network assessment (preview)</span></span>

<span data-ttu-id="98c35-104">Оценка сети Office 365 означает относительный опыт работы пользователей от подключения к сети клиента.</span><span class="sxs-lookup"><span data-stu-id="98c35-104">The Office 365 network assessment indicates the relative user experience impact from customer network connectivity.</span></span> <span data-ttu-id="98c35-105">Влияние какого-либо сетевого подключения Майкрософт из этой группы исключается, чтобы клиенты могли оптимизировать сетевые структуры, для которых они отвечают.</span><span class="sxs-lookup"><span data-stu-id="98c35-105">The impact of any Microsoft owned network connectivity is excluded from this to enable customers to optimize network designs for which they are responsible.</span></span>

<span data-ttu-id="98c35-106">Он рассчитывается на основе измерений, которые влияют на взаимодействие с пользователем в ключевых рабочих нагрузках Office 365 и отображается в процентах с диапазоном от 0 до 100.</span><span class="sxs-lookup"><span data-stu-id="98c35-106">It is calculated from measurements that impact user experience in key Office 365 workloads and shown as a percentage with a range of 0 to 100.</span></span>

<span data-ttu-id="98c35-107">При очень низком показателе сети предполагается, что клиенты Office 365 будут иметь серьезные проблемы с подключением или оставшееся время отклика пользователей.</span><span class="sxs-lookup"><span data-stu-id="98c35-107">A very low network score suggests that Office 365 clients will have significant problems connecting or remaining user responsive.</span></span> <span data-ttu-id="98c35-108">Показатель 80% означает сетевое подключение, в котором не ожидается получение жалоб пользователя на пользовательский интерфейс Office 365 из-за производительности сети.</span><span class="sxs-lookup"><span data-stu-id="98c35-108">A score of 80% represents network connectivity where you should not expect to receive user complaints about your Office 365 user experience due to your network performance.</span></span> <span data-ttu-id="98c35-109">По мере внесения улучшения сетевого подключения этот показатель увеличится и будет работать с пользователем.</span><span class="sxs-lookup"><span data-stu-id="98c35-109">As network connectivity improvements are made, this score will increase along with user experience.</span></span>

>[!IMPORTANT]
><span data-ttu-id="98c35-110">Рекомендации по производительности сети, оценки и оценки в центре администрирования Microsoft 365 в настоящее время находятся в состоянии предварительной версии и доступны только для клиентов Office 365, зарегистрированных в программе предварительного просмотра компонентов.</span><span class="sxs-lookup"><span data-stu-id="98c35-110">Network performance recommendations, insights and assessments in the Microsoft 365 Admin Center is currently in preview status, and is only available for Office 365 tenants that have been enrolled in the feature preview program.</span></span>

## <a name="exchange-online"></a><span data-ttu-id="98c35-111">Exchange Online</span><span class="sxs-lookup"><span data-stu-id="98c35-111">Exchange Online</span></span>

<span data-ttu-id="98c35-112">Для Exchange Online измеряется задержка TCP от клиентского компьютера до сервера переднего плана Exchange.</span><span class="sxs-lookup"><span data-stu-id="98c35-112">For Exchange Online the TCP latency from the client machine to the Exchange front end server is measured.</span></span> <span data-ttu-id="98c35-113">Это может повлиять на расстояние, на которое сеть перемещается по локальной сети и глобальной сети клиентов.</span><span class="sxs-lookup"><span data-stu-id="98c35-113">This can be impacted by the distance the network travels over the customers LAN and WAN.</span></span> <span data-ttu-id="98c35-114">Кроме того, они могут быть затронуты сетевыми промежуточными устройствами или службами, которые отменяют подключение или вызывают повторную отправку пакетов.</span><span class="sxs-lookup"><span data-stu-id="98c35-114">It can also be impacted by network intermediary devices or services which delay the connectivity or cause packets to be resent.</span></span>

## <a name="sharepoint-online"></a><span data-ttu-id="98c35-115">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="98c35-115">SharePoint Online</span></span>

<span data-ttu-id="98c35-116">Для SharePoint Online скорость скачивания, доступная пользователям для доступа к документу, измеряется.</span><span class="sxs-lookup"><span data-stu-id="98c35-116">For SharePoint Online the download speed available for a user to access a document is measured.</span></span> <span data-ttu-id="98c35-117">Это может повлиять на пропускную способность, доступную для сетевых цепей между клиентским компьютером и сетью корпорации Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="98c35-117">This can be impacted by the bandwidth available on network circuits between the client machine and Microsoft’s network.</span></span> <span data-ttu-id="98c35-118">Кроме того, это часто влияет на перегрузку сети, которая существует в узких местах в сложных сетевых устройствах или в областях с плохим покрытием.</span><span class="sxs-lookup"><span data-stu-id="98c35-118">It is also often impacted by network congestion that exists in bottlenecks in complex network devices or in poor coverage Wi-Fi areas.</span></span>

## <a name="microsoft-teams"></a><span data-ttu-id="98c35-119">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="98c35-119">Microsoft Teams</span></span>

<span data-ttu-id="98c35-120">Для Microsoft Teams качество сети измеряется как задержка UDP, колебание UDP и потеря пакетов UDP.</span><span class="sxs-lookup"><span data-stu-id="98c35-120">For Microsoft Teams the Network quality is measured as UDP latency, UDP jitter, and UDP packet loss.</span></span> <span data-ttu-id="98c35-121">UDP используется для подключения аудио-и видеоконференций для Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="98c35-121">UDP is used for call and conferencing audio and video media connectivity for Microsoft Teams.</span></span> <span data-ttu-id="98c35-122">Это может затронуть те же факторы, что и для задержки и скорости скачивания в дополнение к разрывам подключений в сетевой поддержке UDP, так как протокол UDP настроен отдельно для более общего протокола TCP.</span><span class="sxs-lookup"><span data-stu-id="98c35-122">This can be impacted by the same factors as for latency and download speed in addition to connectivity gaps in a network’s UDP support since UDP is configured separately to the more common TCP protocol.</span></span>

## <a name="tenant-network-score-and-office-location-network-score"></a><span data-ttu-id="98c35-123">Оценка сети клиента и оценка сети расположения Office</span><span class="sxs-lookup"><span data-stu-id="98c35-123">Tenant network score and office location network score</span></span>

<span data-ttu-id="98c35-124">Оценка сети измеряет структуру периметра сети офиса в сети корпорации Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="98c35-124">A network score measures the design of the network perimeter of an office location to Microsoft’s network.</span></span> <span data-ttu-id="98c35-125">Улучшения периметра сети лучше всего подходят для каждого офиса или в том случае, если сетевое подключение объединено, могут возникать улучшения, влияющие на несколько расположений.</span><span class="sxs-lookup"><span data-stu-id="98c35-125">Improvements to the network perimeter is best done at each office location, or where network connectivity is aggregated there may be improvements that impact multiple locations.</span></span>
<span data-ttu-id="98c35-126">Мы отображаем оценку сети для всего клиента Office 365 на странице "Обзор сетевой производительности" и определенных оценок сети для каждого обнаруженного расположения Office на странице сводки этого расположения.</span><span class="sxs-lookup"><span data-stu-id="98c35-126">We show a network score for the whole Office 365 tenant on the network performance overview page and a specific network score for each detected office location on that location’s summary page.</span></span>

## <a name="network-score-panel"></a><span data-ttu-id="98c35-127">Панель оценки сети</span><span class="sxs-lookup"><span data-stu-id="98c35-127">Network score panel</span></span>

<span data-ttu-id="98c35-128">Каждая сеть указывает, отображается ли панель с подробными сведениями о рейтинге для клиента или отдельного расположения Office.</span><span class="sxs-lookup"><span data-stu-id="98c35-128">Each network score whether for the tenant or for a specific office location shows a panel with details about the score.</span></span> <span data-ttu-id="98c35-129">На этой панели отображается линейчатая диаграмма оценки как в процентах, так и в качестве общего количества баллов для каждой рабочей нагрузки компонентов, включая рабочие нагрузки, в которых были получены данные измерения.</span><span class="sxs-lookup"><span data-stu-id="98c35-129">This panel shows a bar chart of the score both as a percentage and as the total points for each component workload including only workloads where measurement data was received.</span></span> <span data-ttu-id="98c35-130">Для оценки сети расположения Office мы также можем показать тест, который является медианы всех клиентов Office 365, которые сообщают данные в том же городе, что и ваше расположение в офисе.</span><span class="sxs-lookup"><span data-stu-id="98c35-130">For an office location network score we also show a benchmark which is the median of all Office 365 clients that reported data in the same City as your office location.</span></span>

<span data-ttu-id="98c35-131">При разбивке оценки на панели отображается показатель для каждой рабочей нагрузки компонентов.</span><span class="sxs-lookup"><span data-stu-id="98c35-131">The score breakdown in the panel shows the score for each of the component workloads.</span></span>

<span data-ttu-id="98c35-132">Журнал показателей показывает прошедшие 30 дней оценки и тестирования.</span><span class="sxs-lookup"><span data-stu-id="98c35-132">The score history shows the past 30 days of the score and the benchmark.</span></span>

## <a name="related-topics"></a><span data-ttu-id="98c35-133">Связанные статьи</span><span class="sxs-lookup"><span data-stu-id="98c35-133">Related topics</span></span>

[<span data-ttu-id="98c35-134">Рекомендации по повышению производительности сети в центре администрирования Microsoft 365 (Предварительная версия)</span><span class="sxs-lookup"><span data-stu-id="98c35-134">Network performance recommendations in the Microsoft 365 Admin Center (preview)</span></span>](office-365-network-mac-perf-overview.md)

[<span data-ttu-id="98c35-135">Подробные сведения о производительности сети Office 365 (Предварительная версия)</span><span class="sxs-lookup"><span data-stu-id="98c35-135">Office 365 network performance insights (preview)</span></span>](office-365-network-mac-perf-insights.md)

[<span data-ttu-id="98c35-136">Средство входящей миграции в сети Office 365 в центре администрирования M365 (Предварительная версия)</span><span class="sxs-lookup"><span data-stu-id="98c35-136">Office 365 Network Onboarding Tool in the M365 Admin Center (preview)</span></span>](office-365-network-mac-perf-onboarding-tool.md)
