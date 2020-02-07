---
title: Административные элементы управления доступом в Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
f1.keywords:
- NOCSH
ms.collection:
- Strat_O365_IP
- M365-security-compliance
description: Сводка. Обзор элементов управления административным доступом и категоризации данных в Office 365.
ms.openlocfilehash: f902b123b26f2c71cb6597f66fc47142e2f2b44c
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844540"
---
# <a name="administrative-access-controls-in-office-365"></a><span data-ttu-id="dcedd-103">Административные элементы управления доступом в Office 365</span><span class="sxs-lookup"><span data-stu-id="dcedd-103">Administrative Access Controls in Office 365</span></span> 

<span data-ttu-id="dcedd-104">Корпорация Майкрософт в значительной степени вкладывает системы и элементы управления, автоматизирующие большинство операций Office 365, в то же время ограничивая доступ к контенту клиентов корпорацией Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="dcedd-104">Microsoft has invested heavily in systems and controls that automate most Office 365 operations while intentionally limiting access to customer content by Microsoft.</span></span> <span data-ttu-id="dcedd-105">Люди управляют службой, и программное обеспечение работает со службой.</span><span class="sxs-lookup"><span data-stu-id="dcedd-105">Humans govern the service, and software operates the service.</span></span> <span data-ttu-id="dcedd-106">Это позволяет Майкрософт управлять масштабом Office 365 и управлять рисками внутренних угроз для контента клиента.</span><span class="sxs-lookup"><span data-stu-id="dcedd-106">This enables Microsoft to manage Office 365 at scale and manage the risks of internal threats to customer content.</span></span>

<span data-ttu-id="dcedd-107">По умолчанию у инженеров корпорации Майкрософт нет ни прав администратора, ни доступа к контенту пользователя в Office 365.</span><span class="sxs-lookup"><span data-stu-id="dcedd-107">By default, Microsoft engineers have zero standing administrative privileges and zero standing access to customer content in Office 365.</span></span> <span data-ttu-id="dcedd-108">У инженера Майкрософт может быть ограниченный, проверенный и защищенный доступ к контенту клиента в течение ограниченного периода времени.</span><span class="sxs-lookup"><span data-stu-id="dcedd-108">A Microsoft engineer can have limited, audited, and secured access to a customer's content for a limited amount of time.</span></span> <span data-ttu-id="dcedd-109">Доступ предоставляется только при необходимости для операций службы и только при утверждении участником высшего управления Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="dcedd-109">Access is only when necessary for service operations and only when approved by a member of Microsoft senior management.</span></span> <span data-ttu-id="dcedd-110">Для клиентов, исходящих через защищенное хранилище, клиент предоставляет утверждение на доступ к контенту, размещенному в Office 365.</span><span class="sxs-lookup"><span data-stu-id="dcedd-110">For Customer Lockbox licensed customers, the customer provides access approval to their content hosted on Office 365.</span></span>

<span data-ttu-id="dcedd-111">Майкрософт предоставляет веб-службы, используя несколько форм облачной доставки:</span><span class="sxs-lookup"><span data-stu-id="dcedd-111">Microsoft provides online services using multiple forms of cloud delivery:</span></span>

- <span data-ttu-id="dcedd-112">**Общедоступные облака:** Включает многоклиентские версии Office 365, Azure и другие службы, размещенные в Северной Америке, Южной Америке, Европе, Азии, Австралии и т. д.</span><span class="sxs-lookup"><span data-stu-id="dcedd-112">**Public Clouds:** Includes multi-tenant versions of Office 365, Azure, and other services hosted in North America, South America, Europe, Asia, Australia, etc.</span></span>
- <span data-ttu-id="dcedd-113">**Местные облака:** Включает все публичном и сторонние облака за пределами США (за исключением упомянутых выше), таких как Office 365 в Китае (под управлением 21Vianet) и Office 365 в Германии (под управлением корпорации Майкрософт, но в модели, в которой доверенный для немецкого приложения для работы с данными, Deutsche Telekom, контролирует и отслеживает доступ Майкрософт к данным и системам, содержащим данные клиента).</span><span class="sxs-lookup"><span data-stu-id="dcedd-113">**National Clouds:** Includes all sovereign and third party-operated clouds outside of the United States (except ones noted previously), such as Office 365 in China (operated by 21Vianet), and Office 365 in Germany (operated by Microsoft, but under a model in which a German data trustee, Deutsche Telekom, controls and monitors Microsoft's access to Customer Data and systems that contain Customer Data).</span></span>
- <span data-ttu-id="dcedd-114">**Государственные облака:** Включает в себя Office 365 и службы Azure, которые доступны клиентам правительства США.</span><span class="sxs-lookup"><span data-stu-id="dcedd-114">**Government Clouds:** Includes Office 365 and Azure services that are available to United States government customers.</span></span>

<span data-ttu-id="dcedd-115">В целях данной статьи службы Office 365 включают:</span><span class="sxs-lookup"><span data-stu-id="dcedd-115">For purposes of this article, Office 365 services include:</span></span>

- [<span data-ttu-id="dcedd-116">Exchange Online</span><span class="sxs-lookup"><span data-stu-id="dcedd-116">Exchange Online</span></span>](https://docs.microsoft.com/Exchange/exchange-online)
- [<span data-ttu-id="dcedd-117">Exchange Online Protection</span><span class="sxs-lookup"><span data-stu-id="dcedd-117">Exchange Online Protection</span></span>](https://docs.microsoft.com/Office365/SecurityCompliance/eop/exchange-online-protection-overview)
- [<span data-ttu-id="dcedd-118">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="dcedd-118">SharePoint Online</span></span>](https://docs.microsoft.com/sharepoint/sharepoint-online)
- [<span data-ttu-id="dcedd-119">OneDrive для бизнеса</span><span class="sxs-lookup"><span data-stu-id="dcedd-119">OneDrive for Business</span></span>](https://docs.microsoft.com/OneDrive/onedrive)
- [<span data-ttu-id="dcedd-120">Skype для бизнеса</span><span class="sxs-lookup"><span data-stu-id="dcedd-120">Skype for Business</span></span>](https://docs.microsoft.com/SkypeForBusiness/skype-for-business-online)
- [<span data-ttu-id="dcedd-121">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="dcedd-121">Microsoft Teams</span></span>](https://docs.microsoft.com/MicrosoftTeams/Teams-overview)
- [<span data-ttu-id="dcedd-122">Yammer</span><span class="sxs-lookup"><span data-stu-id="dcedd-122">Yammer</span></span>](https://docs.microsoft.com/yammer/yammer-landing-page)

## <a name="office-365-access-controls"></a><span data-ttu-id="dcedd-123">Элементы управления доступом Office 365</span><span class="sxs-lookup"><span data-stu-id="dcedd-123">Office 365 Access Controls</span></span>

<span data-ttu-id="dcedd-124">Для целей управления доступом Майкрософт классифицирует данные Office 365 как данные клиента или другие типы данных.</span><span class="sxs-lookup"><span data-stu-id="dcedd-124">For access control purposes, Microsoft categorizes Office 365 data as Customer data or other types of data.</span></span>

### <a name="customer-data"></a><span data-ttu-id="dcedd-125">Данные клиента</span><span class="sxs-lookup"><span data-stu-id="dcedd-125">Customer data</span></span>

<span data-ttu-id="dcedd-126">Данные клиентов — это все данные, предоставляемые или от имени клиента при использовании служб Office 365.</span><span class="sxs-lookup"><span data-stu-id="dcedd-126">Customer data is all data provided by or on behalf of a customer when using Office 365 services.</span></span> <span data-ttu-id="dcedd-127">Это содержимое клиента напрямую создается или отправляется пользователям Office 365, в том числе:</span><span class="sxs-lookup"><span data-stu-id="dcedd-127">This is customer content directly created or uploaded by Office 365 users, including:</span></span>

- <span data-ttu-id="dcedd-128">Сообщения электронной почты</span><span class="sxs-lookup"><span data-stu-id="dcedd-128">Emails</span></span>
- <span data-ttu-id="dcedd-129">Контент SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="dcedd-129">SharePoint Online content</span></span>
- <span data-ttu-id="dcedd-130">Мгновенные сообщения</span><span class="sxs-lookup"><span data-stu-id="dcedd-130">Instant messages</span></span>
- <span data-ttu-id="dcedd-131">Элементы календаря</span><span class="sxs-lookup"><span data-stu-id="dcedd-131">Calendar items</span></span>
- <span data-ttu-id="dcedd-132">Документы</span><span class="sxs-lookup"><span data-stu-id="dcedd-132">Documents</span></span>
- <span data-ttu-id="dcedd-133">Контакты</span><span class="sxs-lookup"><span data-stu-id="dcedd-133">Contacts</span></span>
- <span data-ttu-id="dcedd-134">Сведения, идентифицируемые конечными пользователями (ЕУИИ) (данные, которые являются уникальными для пользователя или связаны с отдельными пользователями, но не включают контент клиентов).</span><span class="sxs-lookup"><span data-stu-id="dcedd-134">End-user identifiable information (EUII) (data that is unique to a user or that is linkable to an individual user but does not include customer content).</span></span>

### <a name="other-types-of-data"></a><span data-ttu-id="dcedd-135">Другие типы данных</span><span class="sxs-lookup"><span data-stu-id="dcedd-135">Other types of data</span></span>

<span data-ttu-id="dcedd-136">К другим типам данных относятся:</span><span class="sxs-lookup"><span data-stu-id="dcedd-136">Other types of data include:</span></span>

- <span data-ttu-id="dcedd-137">**Данные учетной записи:** Включает административные данные (сведения, предоставленные администраторами при регистрации или приобретении услуг), а также данные платежа (сведения о платежных инструментах, например сведения о кредитных картах).</span><span class="sxs-lookup"><span data-stu-id="dcedd-137">**Account data:** Includes administrative data (information provided by administrators when they sign-up or purchase services), and payment data (information about payment instruments, such as credit card details).</span></span>
- <span data-ttu-id="dcedd-138">**Организация, идентифицирующая информацию:** Содержит данные, используемые для идентификации клиента, данных об использовании и невозможности связи с отдельным пользователем или для включения в контент клиента.</span><span class="sxs-lookup"><span data-stu-id="dcedd-138">**Organizationally identifiable information:** Includes data used to identify a tenant, usage data, and not linkable to an individual user or included in customer content.</span></span>
- <span data-ttu-id="dcedd-139">**Системные метаданные:** Включает журналы служб, содержащие параметры конфигурации, состояние системы, IP-адреса Майкрософт и технические сведения о подписках и клиентах.</span><span class="sxs-lookup"><span data-stu-id="dcedd-139">**System metadata:** Includes service logs that contain configuration settings, system status, Microsoft IP addresses, and technical information about subscriptions and tenants.</span></span>

<span data-ttu-id="dcedd-140">Корпорация Майкрософт установила механизмы управления доступом, чтобы никто не получил Неутвержденный доступ к данным клиента или данным управления доступом.</span><span class="sxs-lookup"><span data-stu-id="dcedd-140">Microsoft has established access control mechanisms to ensure that no one has unapproved access to Customer Data or access control data.</span></span> <span data-ttu-id="dcedd-141">Данные управления доступом управляют доступом к другим типам данных или функциям в среде, включая доступ к контенту клиента или ЕУИИ, пароли Майкрософт, сертификаты безопасности и другие данные, связанные с проверкой подлинности.</span><span class="sxs-lookup"><span data-stu-id="dcedd-141">Access control data manages access to other types of data or functions within the environment, including access to customer content or EUII, Microsoft passwords, security certificates, and other authentication-related data.</span></span> <span data-ttu-id="dcedd-142">Механизмы управления доступом также позволяют защититься от неодобренного физического, логического или удаленного доступа к рабочей среде Office 365.</span><span class="sxs-lookup"><span data-stu-id="dcedd-142">Access control mechanisms also guard against unapproved physical, logical, or remote access to the Office 365 production environment.</span></span>

<span data-ttu-id="dcedd-143">Существует три категории элементов управления доступом, используемых Microsoft для работы с Office 365:</span><span class="sxs-lookup"><span data-stu-id="dcedd-143">There are three categories of access controls used by Microsoft for operating Office 365:</span></span>

- <span data-ttu-id="dcedd-144">Элементы управления изоляцией</span><span class="sxs-lookup"><span data-stu-id="dcedd-144">Isolation Controls</span></span>
- <span data-ttu-id="dcedd-145">Элементы управления персоналом</span><span class="sxs-lookup"><span data-stu-id="dcedd-145">Personnel Controls</span></span>
- <span data-ttu-id="dcedd-146">Технологические элементы</span><span class="sxs-lookup"><span data-stu-id="dcedd-146">Technology Controls</span></span>

<span data-ttu-id="dcedd-147">В сочетании эти элементы управления помогают предотвратить и обнаруживать вредоносные действия в Office 365.</span><span class="sxs-lookup"><span data-stu-id="dcedd-147">When combined, these controls help prevent and detect malicious actions in Office 365.</span></span> <span data-ttu-id="dcedd-148">В дополнение к элементам управления изоляция, персоналу и технологиям, используемым корпорацией Майкрософт, существует четвертая категория элементов управления:, реализуемых клиентами.</span><span class="sxs-lookup"><span data-stu-id="dcedd-148">In addition to the isolation, personnel, and technology controls used by Microsoft, there is a fourth category of controls: those implemented by customers.</span></span>

<span data-ttu-id="dcedd-149">Office 365 позволяет управлять данными так же, как и управляемые данные в локальных средах.</span><span class="sxs-lookup"><span data-stu-id="dcedd-149">Office 365 allows you to manage data the same way data is managed in on-premises environments.</span></span> <span data-ttu-id="dcedd-150">Пользователь, который записывает организацию для Office 365, автоматически становится глобальным администратором.</span><span class="sxs-lookup"><span data-stu-id="dcedd-150">The person who signs up an organization for Office 365 automatically becomes a global administrator.</span></span> <span data-ttu-id="dcedd-151">Глобальный администратор имеет доступ ко всем функциям в порталах управления и может выполнять следующие действия:</span><span class="sxs-lookup"><span data-stu-id="dcedd-151">The global admin has access to all features in Management Portals and can:</span></span>

- <span data-ttu-id="dcedd-152">Создание или изменение пользователей</span><span class="sxs-lookup"><span data-stu-id="dcedd-152">Create or edit users</span></span>
- <span data-ttu-id="dcedd-153">Назначение ролей администратора другим пользователям</span><span class="sxs-lookup"><span data-stu-id="dcedd-153">Assign admin roles to others</span></span>
- <span data-ttu-id="dcedd-154">Сброс паролей пользователей</span><span class="sxs-lookup"><span data-stu-id="dcedd-154">Reset user passwords</span></span>
- <span data-ttu-id="dcedd-155">Управление пользовательскими лицензиями</span><span class="sxs-lookup"><span data-stu-id="dcedd-155">Manage user licenses</span></span>
- <span data-ttu-id="dcedd-156">Управление доменами</span><span class="sxs-lookup"><span data-stu-id="dcedd-156">Manage domains</span></span>
- <span data-ttu-id="dcedd-157">Утверждение запросов на защищенный клиент</span><span class="sxs-lookup"><span data-stu-id="dcedd-157">Approve Customer Lockbox requests</span></span>

<span data-ttu-id="dcedd-158">Рекомендуется настроить по крайней мере две учетных записи администратора.</span><span class="sxs-lookup"><span data-stu-id="dcedd-158">We recommend that each organization configure at least two admin accounts.</span></span> <span data-ttu-id="dcedd-159">Для крупных организаций рекомендуется использовать специализированные учетные записи администраторов, которые выполняют различные функции.</span><span class="sxs-lookup"><span data-stu-id="dcedd-159">For large enterprise organizations, we recommend specialized admin accounts that serve different functions.</span></span>

<span data-ttu-id="dcedd-160">Сведения о назначении ролей и разрешений администратора приведены [в статье назначение ролей администратора в office 365](https://support.office.com/article/Assigning-admin-roles-in-Office-365-eac4d046-1afd-4f1a-85fc-8219c79e1504) и [о ролях администратора Office 365](https://support.office.com/article/Permissions-in-Office-365-DA585EEA-F576-4F55-A1E0-87090B6AAA9D).</span><span class="sxs-lookup"><span data-stu-id="dcedd-160">For information about assigning admin roles and permissions, see [Assigning admin roles in Office 365](https://support.office.com/article/Assigning-admin-roles-in-Office-365-eac4d046-1afd-4f1a-85fc-8219c79e1504) and [About Office 365 admin roles](https://support.office.com/article/Permissions-in-Office-365-DA585EEA-F576-4F55-A1E0-87090B6AAA9D).</span></span>

## <a name="related-links"></a><span data-ttu-id="dcedd-161">Дополнительные ссылки</span><span class="sxs-lookup"><span data-stu-id="dcedd-161">Related Links</span></span>

- [<span data-ttu-id="dcedd-162">Элементы управления изоляцией</span><span class="sxs-lookup"><span data-stu-id="dcedd-162">Isolation Controls</span></span>](office-365-isolation-controls.md)
- [<span data-ttu-id="dcedd-163">Элементы управления персоналом</span><span class="sxs-lookup"><span data-stu-id="dcedd-163">Personnel Controls</span></span>](office-365-personnel-controls.md)
- [<span data-ttu-id="dcedd-164">Технологические элементы</span><span class="sxs-lookup"><span data-stu-id="dcedd-164">Technology Controls</span></span>](office-365-technology-controls.md)
- [<span data-ttu-id="dcedd-165">Элементы управления доступом к мониторингу и аудиту</span><span class="sxs-lookup"><span data-stu-id="dcedd-165">Monitoring and Auditing Access Controls</span></span>](office-365-monitoring-and-auditing-access-controls.md)
- [<span data-ttu-id="dcedd-166">Элементы управления доступом к Yammer корпоративный</span><span class="sxs-lookup"><span data-stu-id="dcedd-166">Yammer Enterprise Access Controls</span></span>](office-365-yammer-enterprise-access-controls.md)