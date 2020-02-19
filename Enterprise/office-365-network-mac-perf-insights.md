---
title: Подробные сведения о производительности сети Office 365 (Предварительная версия)
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
description: Подробные сведения о производительности сети Office 365 (Предварительная версия)
ms.openlocfilehash: 2e57ffabec5b2172cb36f10135406ddda95bc1c5
ms.sourcegitcommit: e2f7bb4ccd4c74902235f680104ca6b56c051587
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/19/2020
ms.locfileid: "42106426"
---
# <a name="office-365-network-performance-insights-preview"></a><span data-ttu-id="71a7d-103">Подробные сведения о производительности сети Office 365 (Предварительная версия)</span><span class="sxs-lookup"><span data-stu-id="71a7d-103">Office 365 network performance insights (preview)</span></span>

<span data-ttu-id="71a7d-104">На страницах "производительность сети центра администрирования Microsoft 365" показаны сведения о сети Office 365, которые могут помочь при проектировании периметров сети для офисов.</span><span class="sxs-lookup"><span data-stu-id="71a7d-104">The Microsoft 365 Admin Center network performance pages show Office 365 network insights which can help in designing network perimeters for your office locations.</span></span> <span data-ttu-id="71a7d-105">Существует пять сведений о сети, которые могут отображаться для каждого местоположения Office.</span><span class="sxs-lookup"><span data-stu-id="71a7d-105">There are five specific network insights that may be shown for each office location.</span></span>

>[!IMPORTANT]
><span data-ttu-id="71a7d-106">Рекомендации по производительности сети, оценки и оценки в центре администрирования Microsoft 365 в настоящее время находятся в состоянии предварительной версии и доступны только для клиентов Office 365, зарегистрированных в программе предварительного просмотра компонентов.</span><span class="sxs-lookup"><span data-stu-id="71a7d-106">Network performance recommendations, insights and assessments in the Microsoft 365 Admin Center is currently in preview status, and is only available for Office 365 tenants that have been enrolled in the feature preview program.</span></span>

## <a name="backhauled-network-egress"></a><span data-ttu-id="71a7d-107">Выход сети с обратной допускной подсистемой</span><span class="sxs-lookup"><span data-stu-id="71a7d-107">Backhauled network egress</span></span>

<span data-ttu-id="71a7d-108">Расстояние от расположения пользователя до выхода в сеть превышает 500 миль (800 километров), и это повлияет на производительность.</span><span class="sxs-lookup"><span data-stu-id="71a7d-108">The distance from the user location to the network egress is greater than 500 miles (800 kilometers) and this is expected to be impacting performance.</span></span> <span data-ttu-id="71a7d-109">Рекомендуется локальный выход ближе к пользователю.</span><span class="sxs-lookup"><span data-stu-id="71a7d-109">Local egress closer to the user is recommended.</span></span>

<span data-ttu-id="71a7d-110">Это указывает, что расстояние между расположением офиса и выходом сети превышает 500 миль.</span><span class="sxs-lookup"><span data-stu-id="71a7d-110">This identifies that the distance between the office location and the network egress is more than 500 miles.</span></span> <span data-ttu-id="71a7d-111">Расположение офиса идентифицируется с помощью непонятного места на клиентском компьютере, а расположение выходного трафика определяется с помощью обратного IP-адреса в базы данных расположения.</span><span class="sxs-lookup"><span data-stu-id="71a7d-111">The office location is identified by an obfuscated client machine location and the network egress location is identified by using reverse IP Address to location databases.</span></span> <span data-ttu-id="71a7d-112">Если служба расположения Windows отключена на компьютерах, расположение Office может быть неточным.</span><span class="sxs-lookup"><span data-stu-id="71a7d-112">The office location may be inaccurate if Windows Location Services is disabled on machines.</span></span> <span data-ttu-id="71a7d-113">Расположение выхода из сети может быть неточным, если информация о базе данных обратного IP-адреса неточна.</span><span class="sxs-lookup"><span data-stu-id="71a7d-113">The network egress location may be inaccurate if the reverse IP Address database information is inaccurate.</span></span>

<span data-ttu-id="71a7d-114">Подробные сведения об этом соотношении включают расположение Office, расположение сети и расстояние между ними.</span><span class="sxs-lookup"><span data-stu-id="71a7d-114">Details for this insight include the office location, the network egress location, and the distance between them.</span></span>

<span data-ttu-id="71a7d-115">Для этого мы рекомендуем использовать сетевые выходы ближе к расположению Office, чтобы обеспечить оптимальное направление подключения к сети корпорации Майкрософт в Интернете и на переднюю дверцу службы Office 365.</span><span class="sxs-lookup"><span data-stu-id="71a7d-115">For this insight we would recommend network egress closer to the office location so that connectivity can route optimally to Microsoft's network on the Internet and onto Office 365 service front doors.</span></span> <span data-ttu-id="71a7d-116">Если вы развернете доступ к сетевым выходным пользователям для пользователей, вы также можете улучшить производительность в будущем, так как корпорация Майкрософт развертывает в будущем как сетевые точки присутствия, так и передние двери обслуживания Office 365.</span><span class="sxs-lookup"><span data-stu-id="71a7d-116">Having close network egress to users office locations also allows for improved performance in the future as Microsoft expands both network points of presence and Office 365 service front doors in the future.</span></span>

<span data-ttu-id="71a7d-117">Это сокращение является сокращенным в некоторых сводных представлениях.</span><span class="sxs-lookup"><span data-stu-id="71a7d-117">This insight is abbreviated as "Egress" in some summary views.</span></span>

## <a name="better-performance-detected-for-customers-near-you"></a><span data-ttu-id="71a7d-118">Более высокая производительность обнаружено соседних клиентов</span><span class="sxs-lookup"><span data-stu-id="71a7d-118">Better performance detected for customers near you</span></span>

<span data-ttu-id="71a7d-119">Так как большое количество клиентов в вашей области Metro имеет лучшую производительность, чем у пользователей в вашей организации в этом расположении.</span><span class="sxs-lookup"><span data-stu-id="71a7d-119">Since a significant number of customers in your metro area have better performance than users in your organization at this office location.</span></span>

<span data-ttu-id="71a7d-120">Эта область ведет к суммарному снижению производительности пользователей Office 365, которые находятся в том же городе, что и этот офис.</span><span class="sxs-lookup"><span data-stu-id="71a7d-120">This looks at the aggregate performance of Office 365 customers in the same city as this office location.</span></span>

![Относительная производительность сети](Media/m365-mac-perf/m365-mac-perf-relative-perf.png)

<span data-ttu-id="71a7d-122">Мы вычисляем процент клиентов Office 365 в одном городе в более эффективных сегментах производительности.</span><span class="sxs-lookup"><span data-stu-id="71a7d-122">We calculate the percentage of Office 365 customers in the same city in better performance buckets.</span></span> <span data-ttu-id="71a7d-123">Если это число превышает 10%, мы покажем, как показать информацию в сети.</span><span class="sxs-lookup"><span data-stu-id="71a7d-123">If this number if 10% of more then we show the network insight.</span></span>

<span data-ttu-id="71a7d-124">В некоторых сводных представлениях это аббревиатура "Peers".</span><span class="sxs-lookup"><span data-stu-id="71a7d-124">This insight is abbreviated as "Peers" in some summary views.</span></span>

## <a name="use-of-a-non-optimal-exchange-online-service-front-door"></a><span data-ttu-id="71a7d-125">Использование неоптимальной передней дверцы службы Exchange Online</span><span class="sxs-lookup"><span data-stu-id="71a7d-125">Use of a non-optimal Exchange Online service front door</span></span>

<span data-ttu-id="71a7d-126">Пользователь не подключается к оптимальной передней дверце службы Office 365, что повлияет на производительность.</span><span class="sxs-lookup"><span data-stu-id="71a7d-126">The user is not connecting to an optimal Office 365 service front door and this is expected to be impacting performance.</span></span>

<span data-ttu-id="71a7d-127">Мы перечислим передние двери служб Exchange Online, которые подходят для использования из города местонахождения Office с хорошей производительностью.</span><span class="sxs-lookup"><span data-stu-id="71a7d-127">We list Exchange Online service front doors which are suitable for use from the office location city with good performance.</span></span> <span data-ttu-id="71a7d-128">Если в текущем тесте показывается использование передней дверцы службы Exchange Online, которой нет в этом списке, мы вызываем эту рекомендацию.</span><span class="sxs-lookup"><span data-stu-id="71a7d-128">If the current test shows use of an Exchange Online service front door not on this list, then we call out this recommendation.</span></span>

<span data-ttu-id="71a7d-129">Использование неоптимальной передней дверцы службы Exchange Online может быть вызвано обратной связи в сети перед выходом в корпоративную сеть, в этом случае мы рекомендуем использовать локальную и прямую сеть.</span><span class="sxs-lookup"><span data-stu-id="71a7d-129">Use of a non-optimal Exchange Online service front door could be caused by network backhaul before the corporate network egress in which case we recommend local and direct network egress.</span></span> <span data-ttu-id="71a7d-130">Кроме того, это может быть вызвано использованием удаленного сервера рекурсивного разрешения DNS, в результате чего мы рекомендуем выравнивать рекурсивный сервер сопоставителя DNS с выходом в сеть.</span><span class="sxs-lookup"><span data-stu-id="71a7d-130">It could also be caused by use of a remote DNS Recursive Resolver server in which case we recommend aligning the DNS Recursive Resolver server with the network egress.</span></span>

<span data-ttu-id="71a7d-131">Эта аналитика сокращена в виде "маршрутизации" в некоторых сводных представлениях.</span><span class="sxs-lookup"><span data-stu-id="71a7d-131">This insight is abbreviated as "Routing" in some summary views.</span></span>

## <a name="use-of-non-optimal-sharepoint-online-service-front-door"></a><span data-ttu-id="71a7d-132">Использование неоптимальной передней дверцы службы SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="71a7d-132">Use of non-optimal SharePoint Online service front door</span></span>

<span data-ttu-id="71a7d-133">Пользователь не подключается к ближайшей передней дверце службы SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="71a7d-133">The user is not connecting to the closest SharePoint Online service front door.</span></span> <span data-ttu-id="71a7d-134">Предполагается, что это повлияет на производительность.</span><span class="sxs-lookup"><span data-stu-id="71a7d-134">This is expected to be impacting performance.</span></span>

<span data-ttu-id="71a7d-135">Мы идентифицируем переднюю дверцу службы SharePoint Online, к которой подключается тестовый клиент.</span><span class="sxs-lookup"><span data-stu-id="71a7d-135">We identify the SharePoint Online service front door that the test client is connecting to.</span></span> <span data-ttu-id="71a7d-136">Затем в городе местонахождения Office мы сравниваемся с ожидаемой внешней дверце службы SharePoint Online для этого города.</span><span class="sxs-lookup"><span data-stu-id="71a7d-136">Then for the office location city we compare that to the expected SharePoint Online service front door for that city.</span></span> <span data-ttu-id="71a7d-137">Если это не так, мы будем использовать эту рекомендацию.</span><span class="sxs-lookup"><span data-stu-id="71a7d-137">If it doesn't match, then we make this recommendation.</span></span>

<span data-ttu-id="71a7d-138">Это сокращение сокращается как "АФД" в некоторых сводных представлениях.</span><span class="sxs-lookup"><span data-stu-id="71a7d-138">This insight is abbreviated as "Afd" in some summary views.</span></span>

## <a name="low-download-speed-from-sharepoint-front-door"></a><span data-ttu-id="71a7d-139">Минимальная скорость скачивания из передней дверцы SharePoint</span><span class="sxs-lookup"><span data-stu-id="71a7d-139">Low download speed from SharePoint front door</span></span>

<span data-ttu-id="71a7d-140">Обнаружена подходящие скорости скачивания сети, которые влияют на то, сколько времени занимает загрузка документов из OneDrive для бизнеса.</span><span class="sxs-lookup"><span data-stu-id="71a7d-140">Sub optimal network download speed detected which impacts how long it takes to load documents from OneDrive for Business.</span></span>

<span data-ttu-id="71a7d-141">Скорость скачивания, которую пользователь может получить из SharePoint Online и фронтальных дверей службы OneDrive для бизнеса, измеряется в мегабайтах в секунду (Мбит/с).</span><span class="sxs-lookup"><span data-stu-id="71a7d-141">The download speed that a user can get from SharePoint Online and OneDrive for Business service front doors is measured in megabytes per second (MBps).</span></span> <span data-ttu-id="71a7d-142">Если это значение меньше 1 Мбит/с, мы предоставляем эту информацию.</span><span class="sxs-lookup"><span data-stu-id="71a7d-142">If this value is less than 1 MBps then we provide this insight.</span></span>

<span data-ttu-id="71a7d-143">Для повышения скорости загрузки может потребоваться увеличить пропускную способность пользователя.</span><span class="sxs-lookup"><span data-stu-id="71a7d-143">To improve download speed that a user can get bandwidth may need to be increased.</span></span> <span data-ttu-id="71a7d-144">Кроме того, может возникнуть перегрузка сети между пользовательскими машинами в расположении Office и внешней дверце службы SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="71a7d-144">Alternatively, there may be network congestion between user machines at the office location and the SharePoint Online service front door.</span></span> <span data-ttu-id="71a7d-145">Иногда это называется перегруженной потерей и позволяет ограничить скорость загрузки, доступную пользователям даже при наличии достаточной пропускной способности.</span><span class="sxs-lookup"><span data-stu-id="71a7d-145">This is sometimes called congestive loss and it restricts the download speed available to users even if sufficient bandwidth is available.</span></span>

<span data-ttu-id="71a7d-146">Это сокращение сокращается до "пропускная способность" в некоторых сводных представлениях.</span><span class="sxs-lookup"><span data-stu-id="71a7d-146">This insight is abbreviated as "Throughput" in some summary views.</span></span>

## <a name="related-topics"></a><span data-ttu-id="71a7d-147">Связанные статьи</span><span class="sxs-lookup"><span data-stu-id="71a7d-147">Related topics</span></span>

[<span data-ttu-id="71a7d-148">Рекомендации по повышению производительности сети в центре администрирования Microsoft 365 (Предварительная версия)</span><span class="sxs-lookup"><span data-stu-id="71a7d-148">Network performance recommendations in the Microsoft 365 Admin Center (preview)</span></span>](office-365-network-mac-perf-overview.md)

[<span data-ttu-id="71a7d-149">Оценка сети Office 365 (Предварительная версия)</span><span class="sxs-lookup"><span data-stu-id="71a7d-149">Office 365 network assessment (preview)</span></span>](office-365-network-mac-perf-score.md)

[<span data-ttu-id="71a7d-150">Средство входящей миграции в сети Office 365 в центре администрирования M365 (Предварительная версия)</span><span class="sxs-lookup"><span data-stu-id="71a7d-150">Office 365 Network Onboarding Tool in the M365 Admin Center (preview)</span></span>](office-365-network-mac-perf-onboarding-tool.md)
