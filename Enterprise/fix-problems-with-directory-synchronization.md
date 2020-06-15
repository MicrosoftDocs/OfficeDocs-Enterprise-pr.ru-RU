---
title: Устранение проблем с синхронизацией службы каталогов для Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
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
ms.openlocfilehash: cb2ec57331d227f0965095ee0782f13af935d569
ms.sourcegitcommit: d2a3d6eeeaa07510ee94c2bc675284d893221a95
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/12/2020
ms.locfileid: "44711912"
---
# <a name="fixing-problems-with-directory-synchronization-for-microsoft-365"></a><span data-ttu-id="f17c0-103">Устранение проблем с синхронизацией службы каталогов для Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="f17c0-103">Fixing problems with directory synchronization for Microsoft 365</span></span>

<span data-ttu-id="f17c0-104">С помощью синхронизации службы каталогов можно продолжать локально управлять пользователями и группами и синхронизировать добавления, удаления и изменения с облаком.</span><span class="sxs-lookup"><span data-stu-id="f17c0-104">With directory synchronization, you can continue to manage users and groups on-premises and synchronize additions, deletions, and changes to the cloud.</span></span> <span data-ttu-id="f17c0-105">Тем не менее ее настройка немного сложна и иногда бывает трудно определить причину проблемы.</span><span class="sxs-lookup"><span data-stu-id="f17c0-105">But setup is a little complicated and it can sometimes be difficult to identify the source of problems.</span></span> <span data-ttu-id="f17c0-106">Мы предлагаем ресурсы, которые помогут вам выявить потенциальные проблемы и устранить их.</span><span class="sxs-lookup"><span data-stu-id="f17c0-106">We have resources to help you identify potential issues and fix them.</span></span>
  
## <a name="how-do-i-know-if-something-is-wrong"></a><span data-ttu-id="f17c0-107">Как узнать, что что-то пошло не так?</span><span class="sxs-lookup"><span data-stu-id="f17c0-107">How do I know if something is wrong?</span></span>

<span data-ttu-id="f17c0-108">Первое указание на то, что что-то пошло не так, когда плитка состояния DirSync в центре администрирования Майкрософт 365 указывает на наличие проблемы.</span><span class="sxs-lookup"><span data-stu-id="f17c0-108">The first indication that something is wrong is when the DirSync Status tile in the Microsoft 365 admin center indicates there is a problem.</span></span>
  
<span data-ttu-id="f17c0-109">Кроме того, вы получите почту из Microsoft 365, которая указывает, что клиент обнаружил ошибки синхронизации службы каталогов, в альтернативную электронную почту и электронную почту администратора.</span><span class="sxs-lookup"><span data-stu-id="f17c0-109">You will also receive a mail (to the alternate email and to your admin email) from Microsoft 365 that indicates your tenant has encountered directory synchronization errors.</span></span> <span data-ttu-id="f17c0-110">Подробные сведения см. [в статье определение ошибок синхронизации каталогов в Microsoft 365](identify-directory-synchronization-errors.md).</span><span class="sxs-lookup"><span data-stu-id="f17c0-110">For details see [Identify directory synchronization errors in Microsoft 365](identify-directory-synchronization-errors.md).</span></span>
  
## <a name="how-do-i-get-azure-active-directory-connect-tool"></a><span data-ttu-id="f17c0-111">Как получить средство Azure Active Directory Connect?</span><span class="sxs-lookup"><span data-stu-id="f17c0-111">How do I get Azure Active Directory Connect tool?</span></span>

<span data-ttu-id="f17c0-112">В [центре администрирования Microsoft 365](https://admin.microsoft.com)перейдите к разделу **Пользователи** \> **Активные пользователи**.</span><span class="sxs-lookup"><span data-stu-id="f17c0-112">In the [Microsoft 365 admin center](https://admin.microsoft.com), navigate to **Users** \> **Active users**.</span></span> <span data-ttu-id="f17c0-113">Щелкните меню **больше** (три точки) и выберите пункт **Синхронизация службы каталогов**.</span><span class="sxs-lookup"><span data-stu-id="f17c0-113">Click the **More** menu (three dots) and select **Directory synchronization**.</span></span> 
  
<span data-ttu-id="f17c0-114">Следуйте [инструкциям в мастере](set-up-directory-synchronization.md), чтобы скачать Azure AD Connect.</span><span class="sxs-lookup"><span data-stu-id="f17c0-114">Follow the [instructions in the wizard](set-up-directory-synchronization.md) to download Azure AD Connect.</span></span> 
  
<span data-ttu-id="f17c0-115">Если вы по-прежнему используете Azure Active Directory Sync (DirSync), ознакомьтесь с [сообщениями об ошибках мастера установки и настройки средства синхронизации Azure Active Directory в Microsoft 365](https://go.microsoft.com/fwlink/p/?LinkId=396717) для получения сведений о требованиях к системе для установки DirSync, необходимых разрешений и устранении распространенных ошибок.</span><span class="sxs-lookup"><span data-stu-id="f17c0-115">If you are still using Azure Active Directory Sync (DirSync), take a look at [How to troubleshoot Azure Active Directory Sync Tool installation and Configuration Wizard error messages in Microsoft 365](https://go.microsoft.com/fwlink/p/?LinkId=396717) for information about the system requirements to install dirsync, the permissions you need, and how to troubleshoot common errors.</span></span> 
  
<span data-ttu-id="f17c0-116">Чтобы перейти от средства синхронизации Azure Active Directory к Azure AD Connect, см. [инструкции по обновлению](https://go.microsoft.com/fwlink/p/?LinkId=733240).</span><span class="sxs-lookup"><span data-stu-id="f17c0-116">To update from Azure Active Directory Sync to Azure AD Connect, see [the upgrade instructions](https://go.microsoft.com/fwlink/p/?LinkId=733240).</span></span>
  
## <a name="resolving-common-causes-of-problems-with-directory-synchronization-in-microsoft-365"></a><span data-ttu-id="f17c0-117">Устранение распространенных причин проблем с синхронизацией службы каталогов в Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="f17c0-117">Resolving common causes of problems with directory synchronization in Microsoft 365</span></span>

### <a name="synchronized-objects-arent-appearing-or-updating-online-or-im-getting-synchronization-error-reports-from-the-service"></a><span data-ttu-id="f17c0-118">**Синхронизированные объекты не отображаются или не обновляются в режиме онлайн. Или служба возвращает отчеты об ошибках синхронизации.**</span><span class="sxs-lookup"><span data-stu-id="f17c0-118">**Synchronized objects aren't appearing or updating online, or I'm getting synchronization error reports from the Service.**</span></span>

- [<span data-ttu-id="f17c0-119">Синхронизация удостоверений и устойчивость повторяющихся атрибутов</span><span class="sxs-lookup"><span data-stu-id="f17c0-119">Identity synchronization and duplicate attribute resiliency</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency)

### <a name="i-have-an-alert-in-the-admin-center-or-am-receiving-automated-emails-that-there-hasnt-been-a-recent-synchronization-event"></a><span data-ttu-id="f17c0-120">**Я получаю оповещение в Центре администрирования. Или на мой электронный адрес приходят автоматические сообщения о том, что в последнее время синхронизация не выполнялась**</span><span class="sxs-lookup"><span data-stu-id="f17c0-120">**I have an alert in the admin center, or am receiving automated emails that there hasn't been a recent synchronization event**</span></span>
- [<span data-ttu-id="f17c0-121">Устранение неполадок подключения с помощью Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="f17c0-121">Troubleshoot connectivity issues with Azure AD Connect</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/tshoot-connect-connectivity)
- [<span data-ttu-id="f17c0-122">Azure AD Connect: учетные записи и разрешения</span><span class="sxs-lookup"><span data-stu-id="f17c0-122">Azure AD Connect Accounts and permissions</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=820598)
- [<span data-ttu-id="f17c0-123">Синхронизация Azure AD Connect: управление учетной записью службы Azure AD</span><span class="sxs-lookup"><span data-stu-id="f17c0-123">Azure AD Connect sync: How to manage the Azure AD service account</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-azureadaccount)
- [<span data-ttu-id="f17c0-124">Синхронизация каталогов с Azure Active Directory остановлена или более суток не зарегистрировано попыток синхронизации</span><span class="sxs-lookup"><span data-stu-id="f17c0-124">Directory synchronization to Azure Active Directory stops or you're warned that sync hasn't registered in more than a day</span></span>](https://support.microsoft.com/help/2882421/directory-synchronization-to-azure-active-directory-stops-or-you-re-warned-that-sync-hasn-t-registered-in-more-than-a-day)

### <a name="password-hashes-arent-synchronizing-or-im-seeing-an-alert-in-the-admin-center-that-there-hasnt-been-a-recent-password-hash-synchronization"></a><span data-ttu-id="f17c0-125">**Не синхронизируются пароли. Или в Центре администрирования Office 365 появляется оповещение о том, что в последнее время синхронизация паролей не выполнялась**</span><span class="sxs-lookup"><span data-stu-id="f17c0-125">**Password hashes aren't synchronizing, or I'm seeing an alert in the admin center that there hasn't been a recent password hash synchronization**</span></span>
- [<span data-ttu-id="f17c0-126">Реализация синхронизации хэшированных паролей в службе синхронизации Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="f17c0-126">Implementing password hash synchronization with Azure AD Connect sync</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization)

### <a name="im-seeing-an-alert-that-object-quota-exceeded"></a><span data-ttu-id="f17c0-127">**Появляется оповещение о том, что превышена квота на объекты.**</span><span class="sxs-lookup"><span data-stu-id="f17c0-127">**I'm seeing an alert that Object quota exceeded**</span></span>
- <span data-ttu-id="f17c0-128">Для защиты службы используется встроенная квота на объекты.</span><span class="sxs-lookup"><span data-stu-id="f17c0-128">We have a built-in object quota to help protect the service.</span></span> <span data-ttu-id="f17c0-129">Если в вашем каталоге слишком много объектов, которые необходимо синхронизировать с Microsoft 365, вам потребуется [обратиться в службу поддержки продуктов для бизнеса](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) , чтобы увеличить квоту.</span><span class="sxs-lookup"><span data-stu-id="f17c0-129">If you have too many objects in your directory that need to sync to Microsoft 365, you'll have to [Contact support for business products](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) to increase your quota.</span></span>

### <a name="i-need-to-know-which-attributes-are-synchronized"></a><span data-ttu-id="f17c0-130">**Мне нужно знать, какие атрибуты синхронизируются**</span><span class="sxs-lookup"><span data-stu-id="f17c0-130">**I need to know which attributes are synchronized**</span></span>
- <span data-ttu-id="f17c0-131">Список всех атрибутов, которые синхронизируются между локальной средой и облаком, можно найти [здесь](https://go.microsoft.com/fwlink/p/?LinkId=396719).</span><span class="sxs-lookup"><span data-stu-id="f17c0-131">You can find a list of all the attributes that are synced between on-premises and the cloud [right here](https://go.microsoft.com/fwlink/p/?LinkId=396719).</span></span>

### <a name="i-cant-manage-or-remove-objects-that-were-synchronized-to-the-cloud"></a><span data-ttu-id="f17c0-132">**Не удается управлять объектами, синхронизированными с облаком, и удалять их**</span><span class="sxs-lookup"><span data-stu-id="f17c0-132">**I can't manage or remove objects that were synchronized to the cloud**</span></span>
- <span data-ttu-id="f17c0-133">Вы готовы управлять объектами только в облаке?</span><span class="sxs-lookup"><span data-stu-id="f17c0-133">Are you ready to manage objects in the cloud only?</span></span> <span data-ttu-id="f17c0-134">Или вы удалили объект локально, но он все еще существует в облаке?</span><span class="sxs-lookup"><span data-stu-id="f17c0-134">Or is there an object that was deleted on-premises, but is stuck in the cloud?</span></span> <span data-ttu-id="f17c0-135">Ознакомьтесь с этой статьей [Устранение ошибок синхронизации во время синхронизации](https://go.microsoft.com/fwlink/p/?linkid=842044) и [справочной статьей](https://go.microsoft.com/fwlink/p/?LinkId=396720), чтобы получить инструкции по устранению этих проблем.</span><span class="sxs-lookup"><span data-stu-id="f17c0-135">Take a look at this [Troubleshooting Errors during synchronization](https://go.microsoft.com/fwlink/p/?linkid=842044) and [support article](https://go.microsoft.com/fwlink/p/?LinkId=396720) for guidance on how to resolve these issues.</span></span>

### <a name="i-got-an-error-message-that-my-company-has-exceeded-the-number-of-objects-that-can-be-synchronized"></a><span data-ttu-id="f17c0-136">**Появляется сообщение об ошибке, в котором говорится, что в компании превышено количество объектов, которые можно синхронизировать.**</span><span class="sxs-lookup"><span data-stu-id="f17c0-136">**I got an error message that my company has exceeded the number of objects that can be synchronized**</span></span>
- <span data-ttu-id="f17c0-137">Подробнее об этой проблеме вы можете узнать [здесь](https://go.microsoft.com/fwlink/p/?LinkId=396721).</span><span class="sxs-lookup"><span data-stu-id="f17c0-137">You can read more about this issue [here](https://go.microsoft.com/fwlink/p/?LinkId=396721).</span></span>
   
## <a name="other-resources"></a><span data-ttu-id="f17c0-138">Другие ресурсы</span><span class="sxs-lookup"><span data-stu-id="f17c0-138">Other resources</span></span>

- [<span data-ttu-id="f17c0-139">Сценарий для устранения повторяющихся имен участников-пользователей</span><span class="sxs-lookup"><span data-stu-id="f17c0-139">Script to fix duplicate user principal names</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396725)
    
- [<span data-ttu-id="f17c0-140">Сведения о подготовке немаршрутизируемого домена (например, .local) для синхронизации службы каталогов</span><span class="sxs-lookup"><span data-stu-id="f17c0-140">How to prepare a non-routable domain (such as .local domain) for directory synchronization</span></span>](prepare-a-non-routable-domain-for-directory-synchronization.md)
    
- [<span data-ttu-id="f17c0-141">Сценарий для подсчета общего числа синхронизированных объектов</span><span class="sxs-lookup"><span data-stu-id="f17c0-141">Script to count total synchronized objects</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396726)
    
- [<span data-ttu-id="f17c0-142">Устранение неполадок AD FS 2.0</span><span class="sxs-lookup"><span data-stu-id="f17c0-142">Troubleshoot AD FS 2.0</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396727)
    
- [<span data-ttu-id="f17c0-143">Использование PowerShell для исправления пустых атрибутов DisplayName для групп, поддерживающих почту</span><span class="sxs-lookup"><span data-stu-id="f17c0-143">Use PowerShell to fix empty DisplayName attributes for mail-enabled groups</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396728)
    
- [<span data-ttu-id="f17c0-144">Использование PowerShell для устранения повторяющихся имен участников-пользователей</span><span class="sxs-lookup"><span data-stu-id="f17c0-144">Use PowerShell to fix duplicate UPN</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396730)
    
- [<span data-ttu-id="f17c0-145">Использование PowerShell для устранения повторяющихся адресов электронной почты</span><span class="sxs-lookup"><span data-stu-id="f17c0-145">Use PowerShell to fix duplicate email addresses</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396731)
    
## <a name="diagnostic-tools"></a><span data-ttu-id="f17c0-146">Средства диагностики</span><span class="sxs-lookup"><span data-stu-id="f17c0-146">Diagnostic tools</span></span>

<span data-ttu-id="f17c0-147">[Средство IDFix](prepare-directory-attributes-for-synch-with-idfix.md) используется для выполнения обнаружения и исправления объектов Identity и их атрибутов в локальной среде Active Directory при подготовке к миграции в Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="f17c0-147">[IDFix tool](prepare-directory-attributes-for-synch-with-idfix.md) is used to perform discovery and remediation of identity objects and their attributes in an on-premises Active Directory environment in preparation for migration to Microsoft 365.</span></span> <span data-ttu-id="f17c0-148">IDFix предназначен для администраторов Active Directory, ответственных за синхронизацию каталогов со службой Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="f17c0-148">IDFix is intended for the Active Directory administrators responsible for directory synchronization with the Microsoft 365 service.</span></span> 

<span data-ttu-id="f17c0-149">[Скачайте средство IDFix](https://go.microsoft.com/fwlink/p/?LinkId=396718) из Центра загрузки Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="f17c0-149">[Download the IDFix tool](https://go.microsoft.com/fwlink/p/?LinkId=396718) from the Microsoft download center.</span></span>