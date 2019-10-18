---
title: Устранение проблем с синхронизацией службы каталогов для Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MBS150
ms.assetid: 79c43023-5a47-45ae-8068-d8a26eee6bc2
description: В этой статье описаны распространенные причины проблем с синхронизацией службы каталогов в Office 365, а также несколько способов их решения.
ms.openlocfilehash: 3a1cf63122be84dc3e1c60e84a9a3a488f81bc0f
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067675"
---
# <a name="fixing-problems-with-directory-synchronization-for-office-365"></a><span data-ttu-id="61bf0-103">Устранение проблем с синхронизацией службы каталогов для Office 365</span><span class="sxs-lookup"><span data-stu-id="61bf0-103">Fixing problems with directory synchronization for Office 365</span></span>

<span data-ttu-id="61bf0-104">С помощью синхронизации службы каталогов можно продолжать локально управлять пользователями и группами и синхронизировать добавления, удаления и изменения с облаком.</span><span class="sxs-lookup"><span data-stu-id="61bf0-104">With directory synchronization, you can continue to manage users and groups on-premises and synchronize additions, deletions, and changes to the cloud.</span></span> <span data-ttu-id="61bf0-105">Тем не менее ее настройка немного сложна и иногда бывает трудно определить причину проблемы.</span><span class="sxs-lookup"><span data-stu-id="61bf0-105">But setup is a little complicated and it can sometimes be difficult to identify the source of problems.</span></span> <span data-ttu-id="61bf0-106">Мы предлагаем ресурсы, которые помогут вам выявить потенциальные проблемы и устранить их.</span><span class="sxs-lookup"><span data-stu-id="61bf0-106">We have resources to help you identify potential issues and fix them.</span></span>
  
## <a name="how-do-i-know-if-something-is-wrong"></a><span data-ttu-id="61bf0-107">Как узнать, что что-то пошло не так?</span><span class="sxs-lookup"><span data-stu-id="61bf0-107">How do I know if something is wrong?</span></span>

<span data-ttu-id="61bf0-108">Первым сигналом о наличии проблемы служит вот такое сообщение, появляющееся на плитке "Состояние DirSync" в Центре администрирования Microsoft 365:</span><span class="sxs-lookup"><span data-stu-id="61bf0-108">The first indication that something is wrong is when the DirSync Status tile in the Microsoft 365 admin center indicates there is a problem:</span></span>
  
![Плитка "Состояние DirSync" в предварительной версии центра администрирования](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
<span data-ttu-id="61bf0-110">Вы также получите от Office 365 почтовое сообщение (на адрес электронной почты администратора и запасной адрес) о том, что в вашем клиенте обнаружены ошибки синхронизации службы каталогов.</span><span class="sxs-lookup"><span data-stu-id="61bf0-110">You will also receive a mail (to the alternate email and to your admin email) from Office 365 that indicates your tenant has encountered directory synchronization errors.</span></span> <span data-ttu-id="61bf0-111">Подробные сведения см. в статье [Определение ошибок синхронизации службы каталогов в Office 365](identify-directory-synchronization-errors.md).</span><span class="sxs-lookup"><span data-stu-id="61bf0-111">[Identify directory synchronization errors in Office 365](identify-directory-synchronization-errors.md)</span></span>
  
## <a name="how-do-i-get-azure-active-directory-connect-tool"></a><span data-ttu-id="61bf0-112">Как получить средство Azure Active Directory Connect?</span><span class="sxs-lookup"><span data-stu-id="61bf0-112">How do I get Azure Active Directory Connect tool?</span></span>

<span data-ttu-id="61bf0-113">В [Центре администрирования Microsoft 365](https://admin.microsoft.com) перейдите к разделу \*\* Пользователи \*\* \> **Активные пользователи**.</span><span class="sxs-lookup"><span data-stu-id="61bf0-113">In the [Microsoft 365 admin center](https://admin.microsoft.com), navigate to \*\* Users \*\* \> **Active users**.</span></span> <span data-ttu-id="61bf0-114">В меню **Дополнительно** выберите элемент **Синхронизация службы каталогов**.</span><span class="sxs-lookup"><span data-stu-id="61bf0-114">Click the **More** menu and select **Directory synchronization**.</span></span> 
  
![В меню "Дополнительно" выберите элемент "Синхронизация службы каталогов"](media/dc6669e5-c01b-471e-9cdf-04f5d44e1c4b.png)
  
<span data-ttu-id="61bf0-116">Следуйте [инструкциям в мастере](set-up-directory-synchronization.md), чтобы скачать Azure AD Connect.</span><span class="sxs-lookup"><span data-stu-id="61bf0-116">Follow the [instructions in the wizard](set-up-directory-synchronization.md) to download Azure AD Connect.</span></span> 
  
<span data-ttu-id="61bf0-117">Если вы все еще используете средство синхронизации Azure Active Directory (DirSync), ознакомьтесь со статьей [Устранение ошибок установки инструмента для синхронизации Azure Active Directory и мастера настройки в Office 365](https://go.microsoft.com/fwlink/p/?LinkId=396717), чтобы узнать о требованиях к системе для установки средства, необходимых разрешениях и устранении распространенных ошибок.</span><span class="sxs-lookup"><span data-stu-id="61bf0-117">If you are still using Azure Active Directory Sync (DirSync), take a look at [How to troubleshoot Azure Active Directory Sync Tool installation and Configuration Wizard error messages in Office 365](https://go.microsoft.com/fwlink/p/?LinkId=396717) for information about the system requirements to install dirsync, the permissions you need, and how to troubleshoot common errors.</span></span> 
  
<span data-ttu-id="61bf0-118">Чтобы перейти от средства синхронизации Azure Active Directory к Azure AD Connect, см. [инструкции по обновлению](https://go.microsoft.com/fwlink/p/?LinkId=733240).</span><span class="sxs-lookup"><span data-stu-id="61bf0-118">To update from Azure Active Directory Sync to Azure AD Connect, see [the upgrade instructions](https://go.microsoft.com/fwlink/p/?LinkId=733240).</span></span>
  
## <a name="resolving-common-causes-of-problems-with-directory-synchronization-in-office-365"></a><span data-ttu-id="61bf0-119">Устранение распространенных причин проблем с синхронизаций службы каталогов в Office 365</span><span class="sxs-lookup"><span data-stu-id="61bf0-119">Resolving common causes of problems with directory synchronization in Office 365</span></span>

### <a name="synchronized-objects-arent-appearing-or-updating-online-or-im-getting-synchronization-error-reports-from-the-service"></a><span data-ttu-id="61bf0-120">**Синхронизированные объекты не отображаются или не обновляются в режиме онлайн. Или служба возвращает отчеты об ошибках синхронизации.**</span><span class="sxs-lookup"><span data-stu-id="61bf0-120">**Synchronized objects aren't appearing or updating online, or I'm getting synchronization error reports from the Service.**</span></span>

- [<span data-ttu-id="61bf0-121">Синхронизация удостоверений и устойчивость повторяющихся атрибутов</span><span class="sxs-lookup"><span data-stu-id="61bf0-121">Identity synchronization and duplicate attribute resiliency</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency)

### <a name="i-have-an-alert-in-the-admin-center-or-am-receiving-automated-emails-that-there-hasnt-been-a-recent-synchronization-event"></a><span data-ttu-id="61bf0-122">**Я получаю оповещение в Центре администрирования. Или на мой электронный адрес приходят автоматические сообщения о том, что в последнее время синхронизация не выполнялась**</span><span class="sxs-lookup"><span data-stu-id="61bf0-122">**I have an alert in the admin center, or am receiving automated emails that there hasn't been a recent synchronization event**</span></span>
- [<span data-ttu-id="61bf0-123">Устранение неполадок подключения с помощью Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="61bf0-123">Troubleshoot connectivity issues with Azure AD Connect</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/tshoot-connect-connectivity)
- [<span data-ttu-id="61bf0-124">Azure AD Connect: учетные записи и разрешения</span><span class="sxs-lookup"><span data-stu-id="61bf0-124">Azure AD Connect Accounts and permissions</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=820598)
- [<span data-ttu-id="61bf0-125">Синхронизация Azure AD Connect: управление учетной записью службы Azure AD</span><span class="sxs-lookup"><span data-stu-id="61bf0-125">Azure AD Connect sync: How to manage the Azure AD service account</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-azureadaccount)
- [<span data-ttu-id="61bf0-126">Синхронизация каталогов с Azure Active Directory остановлена или более суток не зарегистрировано попыток синхронизации</span><span class="sxs-lookup"><span data-stu-id="61bf0-126">Directory synchronization to Azure Active Directory stops or you're warned that sync hasn't registered in more than a day</span></span>](https://support.microsoft.com/help/2882421/directory-synchronization-to-azure-active-directory-stops-or-you-re-warned-that-sync-hasn-t-registered-in-more-than-a-day)

### <a name="password-hashes-arent-synchronizing-or-im-seeing-an-alert-in-the-admin-center-that-there-hasnt-been-a-recent-password-hash-synchronization"></a><span data-ttu-id="61bf0-127">**Не синхронизируются пароли. Или в Центре администрирования Office 365 появляется оповещение о том, что в последнее время синхронизация паролей не выполнялась**</span><span class="sxs-lookup"><span data-stu-id="61bf0-127">**Password hashes aren't synchronizing, or I'm seeing an alert in the admin center that there hasn't been a recent password hash synchronization**</span></span>
- <span data-ttu-id="61bf0-128">[Реализация синхронизации хэшированных паролей в службе синхронизации Azure AD Connect](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization)</span><span class="sxs-lookup"><span data-stu-id="61bf0-128">For more information, see [Implement password hash synchronization with Azure AD Connect sync](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization).</span></span>

### <a name="im-seeing-an-alert-that-object-quota-exceeded"></a><span data-ttu-id="61bf0-129">**Появляется оповещение о том, что превышена квота на объекты.**</span><span class="sxs-lookup"><span data-stu-id="61bf0-129">**I'm seeing an alert that Object quota exceeded**</span></span>
- <span data-ttu-id="61bf0-130">Для защиты службы используется встроенная квота на объекты.</span><span class="sxs-lookup"><span data-stu-id="61bf0-130">We have a built-in object quota to help protect the service.</span></span> <span data-ttu-id="61bf0-131">Если в каталоге слишком много объектов, которые нужно синхронизировать с Office 365, [обратитесь в службу поддержки продуктов для бизнеса](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) с просьбой увеличить квоту.</span><span class="sxs-lookup"><span data-stu-id="61bf0-131">If you have too many objects in your directory that need to sync to Office 365, you'll have to [Contact support for business products](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) to increase your quota.</span></span>

### <a name="i-need-to-know-which-attributes-are-synchronized"></a><span data-ttu-id="61bf0-132">**Мне нужно знать, какие атрибуты синхронизируются**</span><span class="sxs-lookup"><span data-stu-id="61bf0-132">**I need to know which attributes are synchronized**</span></span>
- <span data-ttu-id="61bf0-133">Список всех атрибутов, которые синхронизируются между локальной средой и облаком, можно найти [здесь](https://go.microsoft.com/fwlink/p/?LinkId=396719).</span><span class="sxs-lookup"><span data-stu-id="61bf0-133">You can find a list of all the attributes that are synced between on-premises and the cloud [right here](https://go.microsoft.com/fwlink/p/?LinkId=396719).</span></span>

### <a name="i-cant-manage-or-remove-objects-that-were-synchronized-to-the-cloud"></a><span data-ttu-id="61bf0-134">**Не удается управлять объектами, синхронизированными с облаком, и удалять их**</span><span class="sxs-lookup"><span data-stu-id="61bf0-134">**I can't manage or remove objects that were synchronized to the cloud**</span></span>
- <span data-ttu-id="61bf0-135">Вы готовы управлять объектами только в облаке?</span><span class="sxs-lookup"><span data-stu-id="61bf0-135">Are you ready to manage objects in the cloud only?</span></span> <span data-ttu-id="61bf0-136">Или вы удалили объект локально, но он все еще существует в облаке?</span><span class="sxs-lookup"><span data-stu-id="61bf0-136">Or is there an object that was deleted on-premises, but is stuck in the cloud?</span></span> <span data-ttu-id="61bf0-137">Ознакомьтесь с этой статьей [Устранение ошибок синхронизации во время синхронизации](https://go.microsoft.com/fwlink/p/?linkid=842044) и [справочной статьей](https://go.microsoft.com/fwlink/p/?LinkId=396720), чтобы получить инструкции по устранению этих проблем.</span><span class="sxs-lookup"><span data-stu-id="61bf0-137">Take a look at this [Troubleshooting Errors during synchronization](https://go.microsoft.com/fwlink/p/?linkid=842044) and [support article](https://go.microsoft.com/fwlink/p/?LinkId=396720) for guidance on how to resolve these issues.</span></span>

### <a name="i-got-an-error-message-that-my-company-has-exceeded-the-number-of-objects-that-can-be-synchronized"></a><span data-ttu-id="61bf0-138">**Появляется сообщение об ошибке, в котором говорится, что в компании превышено количество объектов, которые можно синхронизировать.**</span><span class="sxs-lookup"><span data-stu-id="61bf0-138">**I got an error message that my company has exceeded the number of objects that can be synchronized**</span></span>
- <span data-ttu-id="61bf0-139">Подробнее об этой проблеме вы можете узнать [здесь](https://go.microsoft.com/fwlink/p/?LinkId=396721).</span><span class="sxs-lookup"><span data-stu-id="61bf0-139">You can read more about this issue [here](https://go.microsoft.com/fwlink/p/?LinkId=396721).</span></span>
   
## <a name="other-resources"></a><span data-ttu-id="61bf0-140">Другие ресурсы</span><span class="sxs-lookup"><span data-stu-id="61bf0-140">Other resources</span></span>

- [<span data-ttu-id="61bf0-141">Сценарий для устранения повторяющихся имен участников-пользователей</span><span class="sxs-lookup"><span data-stu-id="61bf0-141">Script to fix duplicate user principal names</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396725)
    
- [<span data-ttu-id="61bf0-142">Сведения о подготовке немаршрутизируемого домена (например, .local) для синхронизации службы каталогов</span><span class="sxs-lookup"><span data-stu-id="61bf0-142">How to prepare a non-routable domain for directory synchronization</span></span>](prepare-a-non-routable-domain-for-directory-synchronization.md)
    
- [<span data-ttu-id="61bf0-143">Сценарий для подсчета общего числа синхронизированных объектов</span><span class="sxs-lookup"><span data-stu-id="61bf0-143">Script to count total synchronized objects</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396726)
    
- [<span data-ttu-id="61bf0-144">Устранение неполадок AD FS 2.0</span><span class="sxs-lookup"><span data-stu-id="61bf0-144">AD FS 2.0</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396727)
    
- [<span data-ttu-id="61bf0-145">Использование PowerShell для исправления пустых атрибутов DisplayName для групп, поддерживающих почту</span><span class="sxs-lookup"><span data-stu-id="61bf0-145">Use PowerShell to fix empty DisplayName attributes for mail-enabled groups</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396728)
    
- [<span data-ttu-id="61bf0-146">Использование PowerShell для устранения повторяющихся имен участников-пользователей</span><span class="sxs-lookup"><span data-stu-id="61bf0-146">Use PowerShell to fix duplicate UPN</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396730)
    
- [<span data-ttu-id="61bf0-147">Использование PowerShell для устранения повторяющихся адресов электронной почты</span><span class="sxs-lookup"><span data-stu-id="61bf0-147">Use PowerShell to fix duplicate email addresses</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396731)
    
## <a name="diagnostic-tools"></a><span data-ttu-id="61bf0-148">Средства диагностики</span><span class="sxs-lookup"><span data-stu-id="61bf0-148">Diagnostic tools</span></span>

<span data-ttu-id="61bf0-149">Средство [IDFix](prepare-directory-attributes-for-synch-with-idfix.md) используется для обнаружения и исправления объектов удостоверений и их атрибутов в локальной среде Active Directory при подготовке к переходу на Office 365.</span><span class="sxs-lookup"><span data-stu-id="61bf0-149">The  IDFix Tool http://go.microsoft.com/fwlink/?LinkID=286107  is used to perform discovery and remediation of identity objects and their attributes in an on-premises Active Directory environment in preparation for migration to Office 365.</span></span> <span data-ttu-id="61bf0-150">Средство IDFix предназначено для администраторов Active Directory, отвечающих за синхронизацию службы каталогов со службой Office 365.</span><span class="sxs-lookup"><span data-stu-id="61bf0-150">IdFix is intended for the Active Directory administrators responsible for DirSync with the Office 365 service.</span></span> 

<span data-ttu-id="61bf0-151">[Скачайте средство IDFix](https://go.microsoft.com/fwlink/p/?LinkId=396718) из Центра загрузки Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="61bf0-151">[Download the IDFix tool](https://go.microsoft.com/fwlink/p/?LinkId=396718) from the Microsoft download center.</span></span>