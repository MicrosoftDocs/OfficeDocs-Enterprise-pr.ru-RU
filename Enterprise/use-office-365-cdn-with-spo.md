---
title: Использование сети доставки содержимого Office 365 с помощью SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/29/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
ms.assetid: bebb285f-1d54-4f79-90a5-94985afc6af8
description: Инструкции по использованию Office 365 встроенных сети доставки содержимого (CDN) для ускорения доставки SharePoint Online активов для всех пользователей, независимо от того, где они находятся и как они доступ к содержимому.
ms.openlocfilehash: fd118e8df404961e1c35c6297a788397f810d1a2
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2019
ms.locfileid: "29547117"
---
# <a name="use-the-office-365-content-delivery-network-with-sharepoint-online"></a><span data-ttu-id="228d8-103">Использование сети доставки содержимого Office 365 с помощью SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="228d8-103">Use the Office 365 content delivery network with SharePoint Online</span></span>

<span data-ttu-id="228d8-p101">Вы можете размещать статического активами в Office 365 сети доставки содержимого (CDN) для повышения быстродействия для SharePoint Online страниц. Статические активы, файлов, не очень часто изменяющихся как изображения, видео и звука, таблицы стилей, шрифты и файлов JavaScript. CDN работает как географически распределенные кэширования прокси-сервер, путем кэширования статических активы ближе к браузеры и их разрешения на запрос.</span><span class="sxs-lookup"><span data-stu-id="228d8-p101">You can host static assets in the Office 365 content delivery network (CDN) to provide better performance for your SharePoint Online pages. Static assets are files that don't change very often, like images, video and audio, style sheets, fonts, and JavaScript files. The CDN works as a geographically distributed caching proxy, by caching static assets closer to the browsers requesting them.</span></span> 
  
<span data-ttu-id="228d8-p102">Если вы уже знакомы с то, как работа CDN, необходимо выполнить некоторые действия, чтобы настроить ее. В этом разделе описывается, как. Ознакомьтесь с сведениями о Office 365 CDN, а также для начала размещения статического активов.</span><span class="sxs-lookup"><span data-stu-id="228d8-p102">If you are already familiar with the way that CDNs work, you only need to complete a few steps to set it up. This topic describes how. Read on for information about the Office 365 CDN and how to get started hosting your static assets.</span></span>
  
 <span data-ttu-id="228d8-110">**HEAD обратно [Планирование сети и настройка производительности для Office 365](https://aka.ms/tune).**</span><span class="sxs-lookup"><span data-stu-id="228d8-110">**Head back to [Network planning and performance tuning for Office 365](https://aka.ms/tune).**</span></span>
  
## <a name="office-365-cdn-basics"></a><span data-ttu-id="228d8-111">Основные сведения о CDN Office 365</span><span class="sxs-lookup"><span data-stu-id="228d8-111">Office 365 CDN basics</span></span>

<span data-ttu-id="228d8-p103">Office 365 CDN включены в SharePoint Online подписки. Требуется дополнительная оплата для него не нужно. Office 365 обеспечивает поддержку обоих частный и общий доступ и позволяет для размещения статического активами в несколько расположений или происхождения. Office 365 CDN не совпадает с Azure CDN. Для получения дополнительных сведений о почему следует использовать в сети доставки Содержимого или общие понятия CDN, в статье [сети доставки содержимого](content-delivery-networks.md).</span><span class="sxs-lookup"><span data-stu-id="228d8-p103">The Office 365 CDN is included as part of your SharePoint Online subscription. You don't have to pay extra for it. Office 365 provides support for both private and public access and allows you to host static assets in multiple locations, or origins. The Office 365 CDN is not the same as the Azure CDN. If you need more information about why to use a CDN or about general CDN concepts, see [Content delivery networks](content-delivery-networks.md).</span></span>
  
## <a name="how-the-cdn-grants-access-to-end-users"></a><span data-ttu-id="228d8-117">Способ CDN предоставления доступа конечным пользователям</span><span class="sxs-lookup"><span data-stu-id="228d8-117">How the CDN grants access to end users</span></span>

<span data-ttu-id="228d8-p104">Закрытый статический активами в Office 365 CDN доступа к с маркеры, создаваемая программой SharePoint Online. Пользователей, имеющих разрешения на доступ к папке или библиотеке, обозначенного происхождения будет автоматически предоставлен маркеры. SharePoint Online не поддерживает разрешения на уровне элементов для CDN.</span><span class="sxs-lookup"><span data-stu-id="228d8-p104">Private access to static assets in the Office 365 CDN is granted by tokens generated by SharePoint Online. Users who already have permission to access to the folder or library designated by the origin will automatically be granted tokens. SharePoint Online does not support item-level permissions for the CDN.</span></span>
  
<span data-ttu-id="228d8-121">Например, в файле, расположенном в `https://contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg`, учитывая следующие:</span><span class="sxs-lookup"><span data-stu-id="228d8-121">For example, for a file located at `https://contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg`, given the following:</span></span>
  
- <span data-ttu-id="228d8-122">Пользователь 1 имеет доступ к folder1 и image1.jpg</span><span class="sxs-lookup"><span data-stu-id="228d8-122">User 1 has access to folder1 and to image1.jpg</span></span>
    
- <span data-ttu-id="228d8-123">Пользователь 2 не имеет доступа к folder1</span><span class="sxs-lookup"><span data-stu-id="228d8-123">User 2 does not have access to folder1</span></span>
    
- <span data-ttu-id="228d8-124">Не имеет доступа к folder1 пользователя 3, но предоставлены явные разрешения на доступ к image1.jpg через SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="228d8-124">User 3 does not have access to folder1 but is granted explicit permission to access image1.jpg through SharePoint Online</span></span>
    
- <span data-ttu-id="228d8-125">Пользователь 4 имеет доступ к folder1, но явно запрещен доступ к image1.jpg</span><span class="sxs-lookup"><span data-stu-id="228d8-125">User 4 has access to folder1 but has been explicitly denied access to image1.jpg</span></span>
    
<span data-ttu-id="228d8-126">Затем выполняются следующие:</span><span class="sxs-lookup"><span data-stu-id="228d8-126">Then the following are true:</span></span>
  
- <span data-ttu-id="228d8-127">Пользователь 1 и 4 пользователя смогут получить доступ к image1.jpg через CDN.</span><span class="sxs-lookup"><span data-stu-id="228d8-127">User 1 and User 4 will be able to access image1.jpg through the CDN.</span></span>
    
- <span data-ttu-id="228d8-128">Пользователь 2 и 3 пользователя нельзя будет для доступа к image1.jpg через CDN.</span><span class="sxs-lookup"><span data-stu-id="228d8-128">User 2 and User 3 will not be able to access image1.jpg through the CDN.</span></span>
    
    <span data-ttu-id="228d8-129">Тем не менее 3 пользователя по-прежнему доступны image1.jpg активов непосредственно через SharePoint Online во время 4 пользователя не может получить доступ к активов через SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="228d8-129">However, User 3 can still access the asset image1.jpg directly through SharePoint Online while User 4 cannot access the asset through SharePoint Online.</span></span>
    
## <a name="overview-of-working-with-the-office-365-cdn"></a><span data-ttu-id="228d8-130">Общие сведения о работе с Office 365 CDN</span><span class="sxs-lookup"><span data-stu-id="228d8-130">Overview of working with the Office 365 CDN</span></span>

<span data-ttu-id="228d8-131">Чтобы настроить Office 365 CDN, выполните следующие основные действия:</span><span class="sxs-lookup"><span data-stu-id="228d8-131">To set up the Office 365 CDN, you follow these basic steps:</span></span>
  
- <span data-ttu-id="228d8-132">Планирование развертывания сети CDN:</span><span class="sxs-lookup"><span data-stu-id="228d8-132">Plan for CDN deployment:</span></span>
    
  - <span data-ttu-id="228d8-p105">Определите, какие статического активы будут размещены на Office 365 CDN. Подробные сведения о том, как сделать эти варианты выбора обратитесь к [сети доставки содержимого](content-delivery-networks.md).</span><span class="sxs-lookup"><span data-stu-id="228d8-p105">Determine which static assets you want to host on the Office 365 CDN. For detailed information about how to make these choices, refer to [Content delivery networks](content-delivery-networks.md).</span></span>
    
  - <span data-ttu-id="228d8-p106">[Определите, где будут храниться активов](use-office-365-cdn-with-spo.md#CDNStoreAssets). Это расположение папки или в библиотеке SharePoint и вызывается источник.</span><span class="sxs-lookup"><span data-stu-id="228d8-p106">[Determine where you want to store your assets](use-office-365-cdn-with-spo.md#CDNStoreAssets). This location is a folder or SharePoint library and is called an origin.</span></span>
    
  - <span data-ttu-id="228d8-p107">Определите, сделанных общедоступный или конфиденциальную активов. Выполните этот формат, если вы [Выберите, следует ли каждого origin public или private](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate). Если вы хотите, у вас есть несколько источники, в которых ниже указаны некоторые общедоступные и ниже указаны некоторые закрытый.</span><span class="sxs-lookup"><span data-stu-id="228d8-p107">Determine whether the assets should be made public or kept private. You do this when you [Choose whether each origin should be public or private](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate). If you want, you can have multiple origins in which some are public, and some are private.</span></span>
    
- <span data-ttu-id="228d8-p108">[Задать и настройке Office 365 CDN с помощью консоли SharePoint Online](use-office-365-cdn-with-spo.md#CDNSetupinPShell). После завершения этого шага будет иметь:</span><span class="sxs-lookup"><span data-stu-id="228d8-p108">[Set up and configure the Office 365 CDN by using the SharePoint Online Management Shell](use-office-365-cdn-with-spo.md#CDNSetupinPShell). When you complete this step, you will have:</span></span>
    
  - <span data-ttu-id="228d8-142">Включить CDN для вашей организации.</span><span class="sxs-lookup"><span data-stu-id="228d8-142">Enabled the CDN for your organization.</span></span>
    
  - <span data-ttu-id="228d8-p109">Добавлен вашей происхождения. Определение каждого origin как public или private.</span><span class="sxs-lookup"><span data-stu-id="228d8-p109">Added your origins. You identify each origin as public or private.</span></span>
    
<span data-ttu-id="228d8-145">После завершения установки, [Управление Office 365 CDN](use-office-365-cdn-with-spo.md#CDNManage) со временем с:</span><span class="sxs-lookup"><span data-stu-id="228d8-145">Once you're done with setup, [Manage the Office 365 CDN](use-office-365-cdn-with-spo.md#CDNManage) over time by:</span></span> 
  
- <span data-ttu-id="228d8-146">Добавление, обновление и удаление ресурсов</span><span class="sxs-lookup"><span data-stu-id="228d8-146">Adding, updating, and removing assets</span></span>
    
- <span data-ttu-id="228d8-147">Добавление и удаление происхождения</span><span class="sxs-lookup"><span data-stu-id="228d8-147">Adding and removing origins</span></span>
    
- <span data-ttu-id="228d8-148">Настройка политик CDN</span><span class="sxs-lookup"><span data-stu-id="228d8-148">Configuring CDN policies</span></span>
    
- <span data-ttu-id="228d8-149">В случае необходимости отключение Office 365 CDN</span><span class="sxs-lookup"><span data-stu-id="228d8-149">If necessary, disabling the Office 365 CDN</span></span>
    
## <a name="determine-where-you-want-to-store-your-assets"></a><span data-ttu-id="228d8-150">Определите место хранения активов</span><span class="sxs-lookup"><span data-stu-id="228d8-150">Determine where you want to store your assets</span></span>

<span data-ttu-id="228d8-p110">CDN извлекает активов из вызывать источник расположения. Для Office 365 источник — это библиотека SharePoint или папку, доступную с URL-адреса. При указании происхождения для вашей организации, существует множество способов. К примеру можно указать несколько происхождения или единого происхождения место для размещения всех CDN средств. Вы можете иметь public или private происхождения для вашей организации. Большинство организаций будет выбирать для реализации комбинации двух.</span><span class="sxs-lookup"><span data-stu-id="228d8-p110">The CDN fetches your assets from a location called an origin. For Office 365, an origin is a SharePoint library or folder that is accessible by a URL. You have great flexibility when you specify origins for your organization. For example, you can specify multiple origins, or, a single origin where you want to put all your CDN assets. You can choose to have both public or private origins for your organization. Most organizations will choose to implement a combination of the two.</span></span>
  
<span data-ttu-id="228d8-p111">При указании нескольких сотен происхождения, скорее всего будет отрицательное влияние на время, необходимое для обработки запросов. Мы рекомендуем, что при наличии более около 100 происхождения может потребоваться пересмотреть свою архитектуру.</span><span class="sxs-lookup"><span data-stu-id="228d8-p111">If you define hundreds of origins, it will likely have a negative impact on the time it takes to process requests. We recommend that if you have more than about 100 origins you might want to rethink your architecture.</span></span>
  
## <a name="choose-whether-each-origin-should-be-public-or-private"></a><span data-ttu-id="228d8-159">Выберите, следует ли каждого origin public или private</span><span class="sxs-lookup"><span data-stu-id="228d8-159">Choose whether each origin should be public or private</span></span>

<span data-ttu-id="228d8-p112">При указании источник указывается ли оно должно быть выполнено public или private. Независимо от того, какой вариант выбран Microsoft выполняет сложных задач с администрирования CDN самого. Кроме того решение можно изменить позднее, после настройки CDN и определяемую вашей происхождения.</span><span class="sxs-lookup"><span data-stu-id="228d8-p112">When you identify an origin, you specify whether it should be made public or private. Regardless of which option you choose, Microsoft does all the heavy lifting for you when it comes to administration of the CDN itself. Also, you can change your mind later, after you've set up the CDN and identified your origins.</span></span>
  
<span data-ttu-id="228d8-163">Общие и частные параметры повысить производительность, но каждая имеет уникальный атрибуты и их преимущества.</span><span class="sxs-lookup"><span data-stu-id="228d8-163">Both public and private options provide performance improvements, but each has unique attributes and advantages.</span></span>
  
 <span data-ttu-id="228d8-164">**Атрибуты и размещение активов в общей origin преимущества**</span><span class="sxs-lookup"><span data-stu-id="228d8-164">**Attributes and advantages of hosting assets in a public origin**</span></span>
  
- <span data-ttu-id="228d8-165">Доступные для всех средств, представленных в общедоступных origin доступных анонимным.</span><span class="sxs-lookup"><span data-stu-id="228d8-165">Assets exposed in a public origin are accessible by everyone anonymously.</span></span>
    
    > [!IMPORTANT]
    > <span data-ttu-id="228d8-166">Если в вашей сети CDN определяет общедоступных происхождения, никогда не следует помещать ресурсы, которые считаются зависит от вашей организации в общедоступных происхождения или библиотеке SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="228d8-166">If you identify a public origin in your CDN, you should never place resources that are considered sensitive to your organization in a public origin or SharePoint Online library.</span></span> 
  
- <span data-ttu-id="228d8-167">При удалении основного средства из открытого origin актива может и дальше будут доступны до 30-дневная из кэша; Тем не менее станут недействительными ссылки на средства в CDN в течение 15 минут.</span><span class="sxs-lookup"><span data-stu-id="228d8-167">If you remove an asset from a public origin, the asset may continue to be available for up to 30 days from the cache; however, we will invalidate links to the asset in the CDN within 15 minutes.</span></span>
    
- <span data-ttu-id="228d8-p113">При узел таблицы стилей (CSS-файлы) в общедоступных происхождения, можно использовать относительные пути и URI в коде. Это означает, что можно ссылаться на местоположение фоновые изображения и другие объекты относительно местоположения активов, который делает вызов.</span><span class="sxs-lookup"><span data-stu-id="228d8-p113">When you host style sheets (CSS files) in a public origin, you can use relative paths and URIs within the code. This means that you can reference the location of background images and other objects relative to the location of the asset that's calling it.</span></span>
    
- <span data-ttu-id="228d8-p114">Серьезный можно в коде общедоступных исходный URL-адрес, но это не рекомендуется. Причина этого —, что если доступ к сети CDN, станут недоступны, URL-адрес не будет автоматически разрешить для вашей организации в SharePoint Online и может привести к ссылок и других ошибках.</span><span class="sxs-lookup"><span data-stu-id="228d8-p114">While you can hard code a public origin's URL, doing so is not recommended. The reason for this is that if access to the CDN becomes unavailable, the URL will not automatically resolve to your organization in SharePoint Online and might result in broken links and other errors.</span></span>
    
- <span data-ttu-id="228d8-p115">Типы файлов по умолчанию, которые включены для общедоступных происхождения, .css, .eot, GIF, .ico, JPEG, .jpg, с расширением js, .map, .png, .svg, .ttf и .woff. Можно указать дополнительные типы файлов.</span><span class="sxs-lookup"><span data-stu-id="228d8-p115">The default file types that are included for public origins are .css, .eot, .gif, .ico, .jpeg, .jpg, .js, .map, .png, .svg, .ttf, and .woff. You can specify additional file types.</span></span>
    
- <span data-ttu-id="228d8-p116">Если вы хотите, можно настроить политику, чтобы исключить активы, определенных с сайта классификации строк, которые можно указать. Например можно исключить все ресурсы, которые помечены как «confidential» или «ограниченный», даже если разрешенного типа и находятся в общедоступных origin.</span><span class="sxs-lookup"><span data-stu-id="228d8-p116">If you want, you can configure a policy to exclude assets that have been identified by site classifications that you specify. For example, you can choose to exclude all assets that are marked as "confidential" or "restricted" even if they are an allowed file type and are located in a public origin.</span></span>
    
 <span data-ttu-id="228d8-176">**Атрибуты и их преимущества размещения активами в частной происхождения**</span><span class="sxs-lookup"><span data-stu-id="228d8-176">**Attributes and advantages of hosting assets in a private origin**</span></span>
  
- <span data-ttu-id="228d8-p117">Пользователи могли осуществлять доступ активов с частной происхождения, если они имеют право делать это. Анонимный доступ к этим средствам запрещено.</span><span class="sxs-lookup"><span data-stu-id="228d8-p117">Users can only access the assets from a private origin if they are authorized to do so. Anonymous access to these assets is prevented.</span></span>
    
- <span data-ttu-id="228d8-179">При удалении актива с частной происхождения актива может и дальше стал доступен до часа из кэша; Тем не менее станут недействительными ссылки на средства в CDN в течение 15 минут.</span><span class="sxs-lookup"><span data-stu-id="228d8-179">If you remove an asset from the private origin, the asset may continue to be available for up to an hour from the cache; however, we will invalidate links to the asset in the CDN within 15 minutes.</span></span>
    
- <span data-ttu-id="228d8-p118">Типы файлов по умолчанию, которые включены для частных происхождения, GIF, .ico, JPEG, .jpg, с расширением js и .png. Можно указать дополнительные типы файлов.</span><span class="sxs-lookup"><span data-stu-id="228d8-p118">The default file types that are included for private origins are .gif, .ico, .jpeg, .jpg, .js, and .png. You can specify additional file types.</span></span>
    
- <span data-ttu-id="228d8-182">Так же, как общедоступный происхождения вы можете настроить политику для исключения основных средств, которые определены классификаций сайта, которые задают даже в том случае, если использовать подстановочные знаки для включения всех средств в папке или библиотеке сайта.</span><span class="sxs-lookup"><span data-stu-id="228d8-182">Just like public origins, you can configure a policy to exclude assets that have been identified by site classifications that you specify even if you use wildcards to include all assets within a folder or Site Library.</span></span>
    
## <a name="default-office-365-cdn-origins"></a><span data-ttu-id="228d8-183">По умолчанию происхождения Office 365 CDN</span><span class="sxs-lookup"><span data-stu-id="228d8-183">Default Office 365 CDN origins</span></span>

<span data-ttu-id="228d8-p119">Если не указано иное, Office 365 создает некоторые источники по умолчанию автоматически при включении Office 365 CDN. Если изначально исключить их, можно добавить эти источники после завершения установки.</span><span class="sxs-lookup"><span data-stu-id="228d8-p119">Unless you specify otherwise, Office 365 sets up some default origins for you when you enable the Office 365 CDN. If you initially exclude them, you can add these origins after you complete setup.</span></span>
  
<span data-ttu-id="228d8-186">По умолчанию закрытый происхождение:</span><span class="sxs-lookup"><span data-stu-id="228d8-186">Default private origins:</span></span>
  
- <span data-ttu-id="228d8-187">\*/userphoto.aspx</span><span class="sxs-lookup"><span data-stu-id="228d8-187">\*/userphoto.aspx</span></span>
    
- <span data-ttu-id="228d8-188">\*/siteassets</span><span class="sxs-lookup"><span data-stu-id="228d8-188">\*/siteassets</span></span>
    
<span data-ttu-id="228d8-189">Происхождение общедоступный по умолчанию:</span><span class="sxs-lookup"><span data-stu-id="228d8-189">Default public origins:</span></span>
  
- <span data-ttu-id="228d8-190">\*/MasterPage</span><span class="sxs-lookup"><span data-stu-id="228d8-190">\*/masterpage</span></span>
    
- <span data-ttu-id="228d8-191">\*Style library</span><span class="sxs-lookup"><span data-stu-id="228d8-191">\*/style library</span></span>

> [!NOTE]
> <span data-ttu-id="228d8-p120">Clientsideassets является origin общедоступный по умолчанию, который был добавлен в дек 2017 таким образом, чтобы при наличии общих CDN до этого времени не увидеть запись автоматически добавляется, но если вы создали позже, вы увидите это изменение автоматически. Если нужно выполнить чтение пример использования этого origin CDN, см.: [узел со стороны клиента веб-части из сети CDN Office 365 (часть 4 Hello World)](https://docs.microsoft.com/en-us/sharepoint/dev/spfx/web-parts/get-started/hosting-webpart-from-office-365-cdn)</span><span class="sxs-lookup"><span data-stu-id="228d8-p120">Clientsideassets is a default public origin that was added in Dec of 2017 so that, if you had a public CDN before that time, you wouldn't see the entry automatically added, but if you created afterward, you'd see this change automatically. If you'd like to read an example of using this CDN origin, see: [Host your client-side web part from Office 365 CDN (Hello World part 4)](https://docs.microsoft.com/en-us/sharepoint/dev/spfx/web-parts/get-started/hosting-webpart-from-office-365-cdn)</span></span>
    
## <a name="set-up-and-configure-the-office-365-cdn-by-using-the-sharepoint-online-management-shell"></a><span data-ttu-id="228d8-194">Установка и настройка Office 365 CDN с помощью консоли SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="228d8-194">Set up and configure the Office 365 CDN by using the SharePoint Online Management Shell</span></span>

<span data-ttu-id="228d8-p121">Процедуры, описанные в этом разделе необходимо использовать командную консоль SharePoint Online для подключения к SharePoint Online. Сведения содержатся в разделе [подключение к SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span><span class="sxs-lookup"><span data-stu-id="228d8-p121">The procedures in this topic require you to use the SharePoint Online Management Shell to connect to SharePoint Online. For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span></span>
  
<span data-ttu-id="228d8-197">Выполните следующие действия, чтобы установить и настроить CDN Office 365 для размещения статического активов в SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="228d8-197">Complete these steps to set up and configure the Office 365 CDN to host your static assets in SharePoint Online.</span></span>
  
### <a name="to-enable-your-organization-to-use-the-office-365-cdn"></a><span data-ttu-id="228d8-198">Чтобы включить организации к использованию Office 365 CDN</span><span class="sxs-lookup"><span data-stu-id="228d8-198">To enable your organization to use the Office 365 CDN</span></span>

<span data-ttu-id="228d8-p122">Командлет **Set-SPOTenantCdnEnabled** используется для включения организации к использованию Office 365 CDN. Можно включить организации к использованию общедоступных происхождения, закрытый происхождения или с CDN. Можно также настроить CDN Office 365 прекращение установки по умолчанию происхождения, если вы включили. Всегда можно добавить эти происхождения более поздней версии, как описано в этом разделе.</span><span class="sxs-lookup"><span data-stu-id="228d8-p122">Use the **Set-SPOTenantCdnEnabled** cmdlet to enable your organization to use the Office 365 CDN. You can enable your organization to use either public origins, private origins, or both with the CDN. You can also configure the Office 365 CDN to skip the setup of default origins when you enable it. You can always add these origins later as described in this topic.</span></span> 
  
<span data-ttu-id="228d8-203">В Windows Powershell для SharePoint Online:</span><span class="sxs-lookup"><span data-stu-id="228d8-203">In Windows Powershell for SharePoint Online:</span></span>
  
```
Set-SPOTenantCdnEnabled -CdnType <Public | Private | Both> -Enable $true
```

<span data-ttu-id="228d8-204">Например чтобы включить организации использовать общие и частные происхождения с CDN, введите следующую команду:</span><span class="sxs-lookup"><span data-stu-id="228d8-204">For example, to enable your organization to use both public and private origins with the CDN, type the following command:</span></span>
  
```
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true
```

<span data-ttu-id="228d8-205">Чтобы включить вашей организации использовать общие и частные происхождения с CDN, но пропустить настройку источники по умолчанию, введите следующую команду:</span><span class="sxs-lookup"><span data-stu-id="228d8-205">To enable your organization to use both public and private origins with the CDN but skip setting up the default origins, type the following command:</span></span>
  
```
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true -NoDefaultOrigins
```

<span data-ttu-id="228d8-206">Чтобы включить организации к использованию общедоступных происхождения с CDN, введите следующую команду:</span><span class="sxs-lookup"><span data-stu-id="228d8-206">To enable your organization to use public origins with the CDN, type the following command:</span></span>
  
```
Set-SPOTenantCdnEnabled -CdnType Public -Enable $true
```

<span data-ttu-id="228d8-207">Чтобы включить организации к использованию закрытый происхождения с CDN, введите следующую команду:</span><span class="sxs-lookup"><span data-stu-id="228d8-207">To enable your organization to use private origins with the CDN, type the following command:</span></span>
  
```
Set-SPOTenantCdnEnabled -CdnType Private -Enable $true
```

<span data-ttu-id="228d8-208">Дополнительные сведения о этот командлет [Set-SPOTenantCdnEnabled](https://technet.microsoft.com/en-us/library/mt790765.aspx)см.</span><span class="sxs-lookup"><span data-stu-id="228d8-208">For more information about this cmdlet, see [Set-SPOTenantCdnEnabled](https://technet.microsoft.com/en-us/library/mt790765.aspx).</span></span>
  
### <a name="optional-to-change-the-list-of-file-types-to-include-in-the-office-365-cdn"></a><span data-ttu-id="228d8-209">(Необязательно) Для изменения списка типов файлов, включаемых в Office 365 CDN</span><span class="sxs-lookup"><span data-stu-id="228d8-209">(Optional) To change the list of file types to include in the Office 365 CDN</span></span>
<span data-ttu-id="228d8-210"><a name="Office365CDNforSPOFileType"> </a></span><span class="sxs-lookup"><span data-stu-id="228d8-210"></span></span>

> [!TIP]
> <span data-ttu-id="228d8-p123">При определении типов файлов с помощью командлета **Set-SPOTenantCdnPolicy** , перезаписать в настоящее время определенный список. Если вы хотите добавить дополнительные типы файлов в список, чтобы узнать, какие типы файлов уже разрешенных и включить их в список, а также новых структур сначала используйте командлет.</span><span class="sxs-lookup"><span data-stu-id="228d8-p123">When you define file types by using the **Set-SPOTenantCdnPolicy** cmdlet, you overwrite the currently defined list. If you want to add additional file types to the list, use the cmdlet first to find out what file types are already allowed and include them in the list along with your new ones.</span></span> 
  
<span data-ttu-id="228d8-p124">Командлет **Set-SPOTenantCdnPolicy** для определения статические типы файлов, которые могут размещаться общие и частные источники в сети CDN. По умолчанию общие типы активов разрешены для примера .css, GIF, .jpg и расширением js.</span><span class="sxs-lookup"><span data-stu-id="228d8-p124">Use the **Set-SPOTenantCdnPolicy** cmdlet to define static file types that can be hosted by public and private origins in the CDN. By default, common asset types are allowed, for example .css, .gif, .jpg, and .js.</span></span> 
  
<span data-ttu-id="228d8-215">В Windows PowerShell для SharePoint Online:</span><span class="sxs-lookup"><span data-stu-id="228d8-215">In Windows PowerShell for SharePoint Online:</span></span>
  
```
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType IncludeFileExtensions -PolicyValue "<Comma-separated list of file types >"
```

<span data-ttu-id="228d8-216">Чтобы узнать, какие типы файлов в данный момент разрешено с CDN, выполните командлет **Get-SPOTenantCdnPolicies** :</span><span class="sxs-lookup"><span data-stu-id="228d8-216">To see what file types are currently allowed by the CDN, use the **Get-SPOTenantCdnPolicies** cmdlet:</span></span> 
  
```
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

<span data-ttu-id="228d8-217">Дополнительные сведения об этих командлетах можно [Set SPOTenantCdnPolicy](https://technet.microsoft.com/en-us/library/mt800839.aspx) и [Get-SPOTenantCdnPolicies](https://technet.microsoft.com/en-us/library/mt800838.aspx).</span><span class="sxs-lookup"><span data-stu-id="228d8-217">For more information about these cmdlets, see [Set-SPOTenantCdnPolicy](https://technet.microsoft.com/en-us/library/mt800839.aspx) and [Get-SPOTenantCdnPolicies](https://technet.microsoft.com/en-us/library/mt800838.aspx).</span></span>
  
### <a name="optional-to-change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn"></a><span data-ttu-id="228d8-218">(Необязательно) Чтобы изменить список сайтов классификации строк, которые необходимо исключить из сети CDN Office 365</span><span class="sxs-lookup"><span data-stu-id="228d8-218">(Optional) To change the list of site classifications you want to exclude from the Office 365 CDN</span></span>
<span data-ttu-id="228d8-219"><a name="Office365CDNforSPOSiteClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="228d8-219"></span></span>

> [!TIP]
> <span data-ttu-id="228d8-p125">Когда исключение классификаций сайта с помощью командлета **Set-SPOTenantCdnPolicy** перезаписать в настоящее время определенный список. Если требуется исключить классификаций дополнительных сайта, командлет сначала узнать, какие классификации уже могут быть исключены, а затем добавить их вместе с новых структур.</span><span class="sxs-lookup"><span data-stu-id="228d8-p125">When you exclude site classifications by using the **Set-SPOTenantCdnPolicy** cmdlet, you overwrite the currently defined list. If you want to exclude additional site classifications, use the cmdlet first to find out what classifications are already excluded and then add them along with your new ones.</span></span> 
  
<span data-ttu-id="228d8-p126">Командлет **Set-SPOTenantCdnPolicy** исключать классификаций сайта, которые не требуется сделать доступным через CDN. По умолчанию без классификации сайтов, могут быть исключены.</span><span class="sxs-lookup"><span data-stu-id="228d8-p126">Use the **Set-SPOTenantCdnPolicy** cmdlet to exclude site classifications that you do not want to make available over the CDN. By default, no site classifications are excluded.</span></span> 
  
<span data-ttu-id="228d8-224">В Windows PowerShell для SharePoint Online:</span><span class="sxs-lookup"><span data-stu-id="228d8-224">In Windows PowerShell for SharePoint Online:</span></span>
  
```
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType ExcludeRestrictedSiteClassifications  -PolicyValue "<Comma-separated list of site classifications >"
```

<span data-ttu-id="228d8-225">Чтобы узнать, какие классификации сайта в настоящее время ограничены, выполните командлет **Get-SPOTenantCdnPolicies** :</span><span class="sxs-lookup"><span data-stu-id="228d8-225">To see what site classifications are currently restricted, use the **Get-SPOTenantCdnPolicies** cmdlet:</span></span> 
  
```
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

<span data-ttu-id="228d8-226">Дополнительные сведения об этих командлетах можно [Set SPOTenantCdnPolicy](https://technet.microsoft.com/en-us/library/mt800839.aspx) и [Get-SPOTenantCdnPolicies](https://technet.microsoft.com/en-us/library/mt800838.aspx).</span><span class="sxs-lookup"><span data-stu-id="228d8-226">For more information about these cmdlets, see [Set-SPOTenantCdnPolicy](https://technet.microsoft.com/en-us/library/mt800839.aspx) and [Get-SPOTenantCdnPolicies](https://technet.microsoft.com/en-us/library/mt800838.aspx).</span></span>
  
### <a name="to-add-an-origin-for-your-assets"></a><span data-ttu-id="228d8-227">Чтобы добавить источник средств</span><span class="sxs-lookup"><span data-stu-id="228d8-227">To add an origin for your assets</span></span>
<span data-ttu-id="228d8-228"><a name="Office365CDNforSPOOrigin"> </a></span><span class="sxs-lookup"><span data-stu-id="228d8-228"></span></span>

<span data-ttu-id="228d8-p127">Используйте командлет **Add-SPOTenantCdnOrigin** для определения источник. Вы можете определить нескольких источников. Источником является URL-адрес, указывающий на библиотеку SharePoint или папки, содержащей ресурсы, которые будут размещаться CDN.</span><span class="sxs-lookup"><span data-stu-id="228d8-p127">Use the **Add-SPOTenantCdnOrigin** cmdlet to define an origin. You can define multiple origins. The origin is a URL that points to a SharePoint library or folder that contains the assets that you want to be hosted by the CDN.</span></span> 
  
> [!IMPORTANT]
> <span data-ttu-id="228d8-232">Если в вашей сети CDN определяет общедоступных происхождения, никогда не следует помещать ресурсы, которые считаются зависит от вашей организации в общедоступных происхождения или библиотеку SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="228d8-232">If you identify a public origin in your CDN, you should never place resources that are considered sensitive to your organization in the public origin or SharePoint Online library.</span></span> 
  
```
Add-SPOTenantCdnOrigin -CdnType <Public | Private> -OriginUrl <path >
```

<span data-ttu-id="228d8-p128">Где путь — это путь к папке, содержащей активов. Можно использовать подстановочные знаки в дополнение к относительные пути. Например чтобы включить всех средств в папке макетом для всех сайтов как общедоступный происхождения в рамках CDN, введите следующую команду:</span><span class="sxs-lookup"><span data-stu-id="228d8-p128">Where path is the path to the folder that contains the assets. You can use wildcards in addition to relative paths. For example, to include all of the assets in the masterpages folder for all of your sites as a public origin within the CDN, type the following command:</span></span>
  
```
Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
```

<span data-ttu-id="228d8-236">Дополнительные сведения об этой команды и синтаксис можно [Добавить SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span><span class="sxs-lookup"><span data-stu-id="228d8-236">For more information about this command and its syntax, see [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span></span>
  
<span data-ttu-id="228d8-p129">После выполнения команды, система выполняет синхронизацию конфигурации через Центр обработки данных. Это занимает 15 минут.</span><span class="sxs-lookup"><span data-stu-id="228d8-p129">Once you've run the command, the system synchronizes the configuration across the datacenter. This takes 15 minutes.</span></span>
  
### <a name="example-configure-a-public-origin-for-your-master-pages-and-for-your-style-library-for-sharepoint-online"></a><span data-ttu-id="228d8-239">Пример: Настройка общедоступных происхождения для главных страниц и библиотеки стилей для SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="228d8-239">Example: Configure a public origin for your master pages and for your style library for SharePoint Online</span></span>
<span data-ttu-id="228d8-240"><a name="ExamplePublicOrigin"> </a></span><span class="sxs-lookup"><span data-stu-id="228d8-240"></span></span>

<span data-ttu-id="228d8-p130">Как правило эти источники настраиваются автоматически по умолчанию при включении общедоступных происхождения для Office 365 CDN. Тем не менее если вы хотите включить их вручную, выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="228d8-p130">Normally, these origins are set up for you by default when you enable public origins for the Office 365 CDN. However, if you want to enable them manually, follow these steps.</span></span>
  
- <span data-ttu-id="228d8-243">Используйте командлет **Add-SPOTenantCdnOrigin** определение библиотеку стилей в качестве открытого происхождения в рамках Office 365 CDN.</span><span class="sxs-lookup"><span data-stu-id="228d8-243">Use the **Add-SPOTenantCdnOrigin** cmdlet to define the style library as a public origin within the Office 365 CDN.</span></span> 
    
  ```
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */style%20library
  ```

- <span data-ttu-id="228d8-244">Используйте командлет **Add-SPOTenantCdnOrigin** определение главных страниц в качестве открытого происхождения в рамках Office 365 CDN.</span><span class="sxs-lookup"><span data-stu-id="228d8-244">Use the **Add-SPOTenantCdnOrigin** cmdlet to define the master pages as a public origin within the Office 365 CDN.</span></span> 
    
  ```
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
  ```

- <span data-ttu-id="228d8-245">Дополнительные сведения об этой команды и синтаксис можно [Добавить SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span><span class="sxs-lookup"><span data-stu-id="228d8-245">For more information about this command and its syntax, see [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span></span>
    
    <span data-ttu-id="228d8-p131">После выполнения команды, система выполняет синхронизацию конфигурации через Центр обработки данных. Это занимает 15 минут.</span><span class="sxs-lookup"><span data-stu-id="228d8-p131">Once you've run the command, the system synchronizes the configuration across the datacenter. This takes 15 minutes.</span></span>
    
### <a name="example-configure-a-private-origin-for-your-site-assets-site-pages-and-publishing-images-for-sharepoint-online"></a><span data-ttu-id="228d8-248">Пример: Настройка закрытый происхождения для средств сайтов, страниц сайта и публикации изображений для SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="228d8-248">Example: Configure a private origin for your site assets, site pages, and publishing images for SharePoint Online</span></span>
<span data-ttu-id="228d8-249"><a name="ExamplePrivateOrigin"> </a></span><span class="sxs-lookup"><span data-stu-id="228d8-249"></span></span>

- <span data-ttu-id="228d8-250">Используйте командлет **Add-SPOTenantCdnOrigin** определение папку ресурсов сайта в качестве закрытого происхождения в рамках Office 365 CDN.</span><span class="sxs-lookup"><span data-stu-id="228d8-250">Use the **Add-SPOTenantCdnOrigin** cmdlet to define the site assets folder as a private origin within the Office 365 CDN.</span></span> 
    
  ```
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */siteassets
  ```

- <span data-ttu-id="228d8-251">Используйте командлет **Add-SPOTenantCdnOrigin** определение на папку страницы сайта в качестве закрытого происхождения в рамках Office 365 CDN.</span><span class="sxs-lookup"><span data-stu-id="228d8-251">Use the **Add-SPOTenantCdnOrigin** cmdlet to define the site pages folder as a private origin within the Office 365 CDN.</span></span> 
    
  ```
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */sitepages
  ```

- <span data-ttu-id="228d8-252">Используйте командлет **Add-SPOTenantCdnOrigin** Определение папки публикации изображений в качестве закрытого происхождения в рамках Office 365 CDN.</span><span class="sxs-lookup"><span data-stu-id="228d8-252">Use the **Add-SPOTenantCdnOrigin** cmdlet to define the publishing images folder as a private origin within the Office 365 CDN.</span></span> 
    
  ```
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */publishingimages
  ```

    <span data-ttu-id="228d8-253">Дополнительные сведения об этой команды и синтаксис можно [Добавить SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span><span class="sxs-lookup"><span data-stu-id="228d8-253">For more information about this command and its syntax, see [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span></span>
    
    <span data-ttu-id="228d8-p132">После выполнения команды, система выполняет синхронизацию конфигурации через Центр обработки данных. Это занимает 15 минут.</span><span class="sxs-lookup"><span data-stu-id="228d8-p132">Once you've run the command, the system synchronizes the configuration across the datacenter. This takes 15 minutes.</span></span>
    
### <a name="example-configure-a-private-origin-for-a-site-collection-for-sharepoint-online"></a><span data-ttu-id="228d8-256">Пример: Настройка закрытый происхождения для семейства веб-сайтов для SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="228d8-256">Example: Configure a private origin for a site collection for SharePoint Online</span></span>
<span data-ttu-id="228d8-257"><a name="ExamplePrivateOriginSiteCollection"> </a></span><span class="sxs-lookup"><span data-stu-id="228d8-257"></span></span>

<span data-ttu-id="228d8-p133">Используйте командлет **Add-SPOTenantCdnOrigin** определение семейства веб-сайтов в качестве закрытого происхождения в рамках Office 365 CDN. Например</span><span class="sxs-lookup"><span data-stu-id="228d8-p133">Use the **Add-SPOTenantCdnOrigin** cmdlet to define a site collection as a private origin within the Office 365 CDN. For example,</span></span> 
  
```
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

<span data-ttu-id="228d8-260">Дополнительные сведения об этой команды и синтаксис можно [Добавить SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span><span class="sxs-lookup"><span data-stu-id="228d8-260">For more information about this command and its syntax, see [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span></span>
  
<span data-ttu-id="228d8-p134">После выполнения команды, система выполняет синхронизацию конфигурации через Центр обработки данных. Это занимает 15 минут.</span><span class="sxs-lookup"><span data-stu-id="228d8-p134">Once you've run the command, the system synchronizes the configuration across the datacenter. This takes 15 minutes.</span></span>
  
## <a name="manage-the-office-365-cdn"></a><span data-ttu-id="228d8-263">Управление Office 365 CDN</span><span class="sxs-lookup"><span data-stu-id="228d8-263">Manage the Office 365 CDN</span></span>
<span data-ttu-id="228d8-264"><a name="CDNManage"> </a></span><span class="sxs-lookup"><span data-stu-id="228d8-264"></span></span>

<span data-ttu-id="228d8-265">После настройки CDN можно вносить изменения в конфигурацию, как обновлять содержимое или при изменении потребностей как описано в этом разделе.</span><span class="sxs-lookup"><span data-stu-id="228d8-265">Once you've set up the CDN, you can make changes to your configuration as you update content or as your needs change, as described in this section.</span></span>
  
### <a name="to-add-update-or-remove-assets-from-the-office-365-cdn"></a><span data-ttu-id="228d8-266">Добавление, обновление и удаление ресурсов из сети CDN Office 365</span><span class="sxs-lookup"><span data-stu-id="228d8-266">To add, update, or remove assets from the Office 365 CDN</span></span>
<span data-ttu-id="228d8-267"><a name="Office365CDNforSPOaddremoveasset"> </a></span><span class="sxs-lookup"><span data-stu-id="228d8-267"></span></span>

<span data-ttu-id="228d8-p135">После выполнения программы установки действия, можно добавить новые ресурсы и обновить или удалить существующие ресурсы в любой момент. Только что внесите изменения к средствам в папку или библиотеку SharePoint, которая определена как источник. При добавлении нового средства, он доступен через CDN немедленно. Тем не менее при обновлении активов, необходимое для новой копии для распространения и становятся доступными в CDN до 15 минут.</span><span class="sxs-lookup"><span data-stu-id="228d8-p135">Once you've completed the setup steps, you can add new assets, and update or remove existing assets whenever you want. Just make your changes to the assets in the folder or SharePoint library that you identified as an origin. If you add a new asset, it is available through the CDN immediately. However, if you update the asset, it will take up to 15 minutes for the new copy to propagate and become available in the CDN.</span></span>
  
<span data-ttu-id="228d8-p136">Если вам потребуется получить расположение источника, можно использовать командлет **Get-SPOTenantCdnOrigins** . Сведения о том, как с помощью этого командлета [Get-SPOTenantCdnOrigins](https://technet.microsoft.com/en-us/library/mt790770.aspx)см.</span><span class="sxs-lookup"><span data-stu-id="228d8-p136">If you need to retrieve the location of the origin, you can use the **Get-SPOTenantCdnOrigins** cmdlet. For information on how to use this cmdlet, see [Get-SPOTenantCdnOrigins](https://technet.microsoft.com/en-us/library/mt790770.aspx).</span></span>
  
### <a name="to-remove-an-origin-from-the-office-365-cdn"></a><span data-ttu-id="228d8-274">Чтобы удалить источник из сети CDN Office 365</span><span class="sxs-lookup"><span data-stu-id="228d8-274">To remove an origin from the Office 365 CDN</span></span>
<span data-ttu-id="228d8-275"><a name="Office365CDNforSPORemoveOrigin"> </a></span><span class="sxs-lookup"><span data-stu-id="228d8-275"></span></span>

<span data-ttu-id="228d8-p137">Если требуется, можно удалить доступ к папке или библиотеку SharePoint, которая определена как источник. Чтобы сделать это, используйте командлет **Remove-SPOTenantCdnOrigin** . Сведения о том, как с помощью этого командлета [Remove-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790761.aspx)см.</span><span class="sxs-lookup"><span data-stu-id="228d8-p137">If you need to, you can remove access to a folder or SharePoint library that you identified as an origin. To do this, use the **Remove-SPOTenantCdnOrigin** cmdlet. For information on how to use this cmdlet, see [Remove-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790761.aspx).</span></span>
  
### <a name="to-modify-an-origin-in-the-office-365-cdn"></a><span data-ttu-id="228d8-279">Чтобы изменить источник в Office 365 CDN</span><span class="sxs-lookup"><span data-stu-id="228d8-279">To modify an origin in the Office 365 CDN</span></span>
<span data-ttu-id="228d8-280"><a name="Office365CDNforSPORemoveOrigin"> </a></span><span class="sxs-lookup"><span data-stu-id="228d8-280"></span></span>

<span data-ttu-id="228d8-p138">Невозможно изменить источник, созданные пользователем. Вместо этого удалить источник, а затем добавьте новый. Для получения дополнительных сведений см. [Чтобы удалить источник из сети CDN Office 365](use-office-365-cdn-with-spo.md#Office365CDNforSPORemoveOrigin) и [Добавление origin средств](use-office-365-cdn-with-spo.md#Office365CDNforSPOOrigin).</span><span class="sxs-lookup"><span data-stu-id="228d8-p138">You can't modify an origin you've created. Instead, remove the origin and then add a new one. For more information, see [To remove an origin from the Office 365 CDN](use-office-365-cdn-with-spo.md#Office365CDNforSPORemoveOrigin) and [To add an origin for your assets](use-office-365-cdn-with-spo.md#Office365CDNforSPOOrigin).</span></span>
  
### <a name="to-disable-the-office-365-cdn"></a><span data-ttu-id="228d8-284">Чтобы отключить Office 365 CDN</span><span class="sxs-lookup"><span data-stu-id="228d8-284">To disable the Office 365 CDN</span></span>
<span data-ttu-id="228d8-285"><a name="Office365CDNforSPODisable"> </a></span><span class="sxs-lookup"><span data-stu-id="228d8-285"></span></span>

<span data-ttu-id="228d8-p139">Командлет **Set-SPOTenantCdnEnabled** используется для отключения CDN для вашей организации. При наличии обоих общие и частные источники включена поддержка CDN, необходимо запустить командлет два раза как показано в следующих примерах.</span><span class="sxs-lookup"><span data-stu-id="228d8-p139">Use the **Set-SPOTenantCdnEnabled** cmdlet to disable the CDN for your organization. If you have both the public and private origins enabled for the CDN, you need to run the cmdlet twice as shown in the following examples.</span></span> 
  
<span data-ttu-id="228d8-288">Чтобы отключить использование общих источники в сети CDN, в Windows Powershell для SharePoint Online, введите следующую команду:</span><span class="sxs-lookup"><span data-stu-id="228d8-288">To disable use of public origins in the CDN, in Windows Powershell for SharePoint Online, enter the following command:</span></span>
  
```
Set-SPOTenantCdnEnabled -CdnType Public -Enable $false
```

<span data-ttu-id="228d8-289">Чтобы отключить использование закрытого источники в сети CDN, введите следующую команду:</span><span class="sxs-lookup"><span data-stu-id="228d8-289">To disable use of the private origins in the CDN, enter the following command:</span></span>
  
```
Set-SPOTenantCdnEnabled -CdnType Private -Enable $false
```

<span data-ttu-id="228d8-290">Дополнительные сведения о этот командлет [Set-SPOTenantCdnEnabled](https://technet.microsoft.com/en-us/library/mt790765.aspx)см.</span><span class="sxs-lookup"><span data-stu-id="228d8-290">For more information about this cmdlet, see [Set-SPOTenantCdnEnabled](https://technet.microsoft.com/en-us/library/mt790765.aspx).</span></span>
  
## <a name="troubleshooting-your-office-365-cdn-configuration"></a><span data-ttu-id="228d8-291">Устранение неполадок в Office 365 CDN конфигурации</span><span class="sxs-lookup"><span data-stu-id="228d8-291">Troubleshooting your Office 365 CDN configuration</span></span>
<span data-ttu-id="228d8-292"><a name="CDNManage"> </a></span><span class="sxs-lookup"><span data-stu-id="228d8-292"></span></span>

<span data-ttu-id="228d8-p140">Конечной точки нельзя сразу же доступны для использования, сколько потребуется время регистрации для распространения через CDN. Конфигурация занимает 15 минут.</span><span class="sxs-lookup"><span data-stu-id="228d8-p140">The endpoint will not immediately be available for use, as it takes time for the registration to propagate through the CDN. Configuration takes 15 minutes.</span></span>
  

