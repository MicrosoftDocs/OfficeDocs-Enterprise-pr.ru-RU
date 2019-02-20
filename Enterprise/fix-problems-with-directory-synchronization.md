---
title: Устранение проблем с синхронизацией каталогов для Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
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
description: В этой статье описываются распространенные причины проблем с синхронизацией службы каталогов в Office 365, а также способы их устранения.
ms.openlocfilehash: e83ca495ca96ac41fb2f79775c3d5970a6b538fb
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085398"
---
# <a name="fixing-problems-with-directory-synchronization-for-office-365"></a><span data-ttu-id="be04a-103">Устранение проблем с синхронизацией каталогов для Office 365</span><span class="sxs-lookup"><span data-stu-id="be04a-103">Fixing problems with directory synchronization for Office 365</span></span>

<span data-ttu-id="be04a-p101">С помощью синхронизации службы каталогов можно продолжать управлять локальными пользователями и группами и синхронизировать добавления, удаления и изменения в облаке. Однако программа установки немного сложна, и иногда может быть трудно определить источник проблем. У нас есть ресурсы, которые помогут вам определить потенциальные проблемы и устранить их.</span><span class="sxs-lookup"><span data-stu-id="be04a-p101">With directory synchronization, you can continue to manage users and groups on-premises and synchronize additions, deletions, and changes to the cloud. But setup is a little complicated and it can sometimes be difficult to identify the source of problems. We have resources to help you identify potential issues and fix them.</span></span>
  
## <a name="how-do-i-know-if-something-is-wrong"></a><span data-ttu-id="be04a-107">Как узнать, что что-то не так?</span><span class="sxs-lookup"><span data-stu-id="be04a-107">How do I know if something is wrong?</span></span>

<span data-ttu-id="be04a-108">Первый признак того, что что-то не так, когда плитка состояния DirSync в центре администрирования Office 365 указывает на наличие проблем:</span><span class="sxs-lookup"><span data-stu-id="be04a-108">The first indication that something is wrong is when the DirSync Status tile in the Office 365 admin center indicates there is a problem:</span></span>
  
![Плитка состояния DirSync в предварительной версии центра администрирования](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
<span data-ttu-id="be04a-p102">Кроме того, вы получите почту из Office 365, которая указывает на то, что клиент обнаружил ошибки синхронизации службы каталогов, в альтернативную электронную почту и электронную почту администратора. Подробные сведения см. [в статье определение ошибок синхронизации каталогов в Office 365](identify-directory-synchronization-errors.md).</span><span class="sxs-lookup"><span data-stu-id="be04a-p102">You will also receive a mail (to the alternate email and to your admin email) from Office 365 that indicates your tenant has encountered directory synchronization errors. For details see [Identify directory synchronization errors in Office 365](identify-directory-synchronization-errors.md).</span></span>
  
## <a name="how-do-i-get-azure-active-directory-connect-tool"></a><span data-ttu-id="be04a-112">Как получить средство Azure Active Directory Connect?</span><span class="sxs-lookup"><span data-stu-id="be04a-112">How do I get Azure Active Directory Connect tool?</span></span>

<span data-ttu-id="be04a-p103">в центре администрирования Office 365 перейдите к разделу \* \* пользователи \* \* \> **активные пользователи**. Откройте меню **Дополнительно** и выберите пункт **Синхронизация службы каталогов**.</span><span class="sxs-lookup"><span data-stu-id="be04a-p103">In the Office 365 admin center, navigate to \*\* Users \*\* \> **Active users**. Click the **More** menu and select **Directory synchronization**.</span></span> 
  
![В меню Дополнительно выберите пункт Синхронизация службы каталогов.](media/dc6669e5-c01b-471e-9cdf-04f5d44e1c4b.png)
  
<span data-ttu-id="be04a-116">в старом центре администрирования Office 365 перейдите к разделу \*\*\*\* \> **активные пользователи**пользователей и нажмите кнопку **настройка** рядом с пунктом **синхронизация active Directory**.</span><span class="sxs-lookup"><span data-stu-id="be04a-116">In the old Office 365 admin center, navigate to **USERS** \> **Active Users**, and select **Set up** next to **Active Directory synchronization**.</span></span> 
  
![Нажмите кнопку "Настройка" рядом с элементом "Синхронизация Active Directory"](media/bd95492b-d65e-4072-a6ee-e562f5f566c3.png)
  
<span data-ttu-id="be04a-118">Следуйте [инструкциям мастера](set-up-directory-synchronization.md) , чтобы скачать Azure AD Connect.</span><span class="sxs-lookup"><span data-stu-id="be04a-118">Follow the [instructions in the wizard](set-up-directory-synchronization.md) to download Azure AD Connect.</span></span> 
  
<span data-ttu-id="be04a-119">Если вы по-прежнему используете Azure Active Directory Sync (DirSync), ознакомьтесь с [сообщениями об ошибках мастера установки и настройки средства синхронизации Azure Active Directory в Office 365](https://go.microsoft.com/fwlink/p/?LinkId=396717) для получения сведений о требованиях к системе для установки DirSync, необходимые разрешения и устранение распространенных ошибок.</span><span class="sxs-lookup"><span data-stu-id="be04a-119">If you are still using Azure Active Directory Sync (DirSync), take a look at [How to troubleshoot Azure Active Directory Sync Tool installation and Configuration Wizard error messages in Office 365](https://go.microsoft.com/fwlink/p/?LinkId=396717) for information about the system requirements to install dirsync, the permissions you need, and how to troubleshoot common errors.</span></span> 
  
<span data-ttu-id="be04a-120">Чтобы обновить синхронизацию Azure Active Directory с помощью Azure AD Connect, ознакомьтесь [с инструкциями по обновлению](https://go.microsoft.com/fwlink/p/?LinkId=733240).</span><span class="sxs-lookup"><span data-stu-id="be04a-120">To update from Azure Active Directory Sync to Azure AD Connect, see [the upgrade instructions](https://go.microsoft.com/fwlink/p/?LinkId=733240).</span></span>
  
## <a name="resolving-common-causes-of-problems-with-directory-synchronization-in-office-365"></a><span data-ttu-id="be04a-121">Устранение распространенных причин проблем с синхронизацией службы каталогов в Office 365</span><span class="sxs-lookup"><span data-stu-id="be04a-121">Resolving common causes of problems with directory synchronization in Office 365</span></span>

### <a name="synchronized-objects-arent-appearing-or-updating-online-or-im-getting-synchronization-error-reports-from-the-service"></a><span data-ttu-id="be04a-122">**Синхронизированные объекты не отображаются или не обновляются в Интернете, или я получаю отчеты об ошибках синхронизации от службы.**</span><span class="sxs-lookup"><span data-stu-id="be04a-122">**Synchronized objects aren't appearing or updating online, or I'm getting synchronization error reports from the Service.**</span></span>

- [<span data-ttu-id="be04a-123">Устойчивость к синхронизации удостоверений и дублирование атрибутов</span><span class="sxs-lookup"><span data-stu-id="be04a-123">Identity synchronization and duplicate attribute resiliency</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency)

### <a name="i-have-an-alert-in-the-office-365-admin-center-or-am-receiving-automated-emails-that-there-hasnt-been-a-recent-synchronization-event"></a><span data-ttu-id="be04a-124">**У меня есть оповещение в центре администрирования Office 365 или при получении сообщений электронной почты, которые не были последними событиями синхронизации**</span><span class="sxs-lookup"><span data-stu-id="be04a-124">**I have an alert in the Office 365 admin center, or am receiving automated emails that there hasn't been a recent synchronization event**</span></span>
- [<span data-ttu-id="be04a-125">Устранение проблем с подключением к Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="be04a-125">Troubleshoot connectivity issues with Azure AD Connect</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/tshoot-connect-connectivity)
- [<span data-ttu-id="be04a-126">Учетные записи и разрешения для Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="be04a-126">Azure AD Connect Accounts and permissions</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=820598)
- [<span data-ttu-id="be04a-127">Синхронизация Azure AD Connect: Управление учетной записью службы Azure AD</span><span class="sxs-lookup"><span data-stu-id="be04a-127">Azure AD Connect sync: How to manage the Azure AD service account</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-azureadaccount)
- [<span data-ttu-id="be04a-128">Синхронизация службы каталогов с Azure Active Directory закончится, или вы будете предупреждать о том, что синхронизация не была зарегистрирована более суток</span><span class="sxs-lookup"><span data-stu-id="be04a-128">Directory synchronization to Azure Active Directory stops or you're warned that sync hasn't registered in more than a day</span></span>](https://support.microsoft.com/help/2882421/directory-synchronization-to-azure-active-directory-stops-or-you-re-warned-that-sync-hasn-t-registered-in-more-than-a-day)

### <a name="password-hashes-arent-synchronizing-or-im-seeing-an-alert-in-the-office-365-admin-center-that-there-hasnt-been-a-recent-password-hash-synchronization"></a><span data-ttu-id="be04a-129">**Хеш-коды паролей не синхронизируются, или я вижу оповещение в центре администрирования Office 365, что еще не выполнялась Последняя синхронизация хэша паролей**</span><span class="sxs-lookup"><span data-stu-id="be04a-129">**Password hashes aren't synchronizing, or I'm seeing an alert in the Office 365 admin center that there hasn't been a recent password hash synchronization**</span></span>
- [<span data-ttu-id="be04a-130">Реализация синхронизации хэша паролей с синхронизацией Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="be04a-130">Implementing password hash synchronization with Azure AD Connect sync</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization)

### <a name="im-seeing-an-alert-that-object-quota-exceeded"></a><span data-ttu-id="be04a-131">**Я вижу предупреждение о превышении квоты объекта**</span><span class="sxs-lookup"><span data-stu-id="be04a-131">**I'm seeing an alert that Object quota exceeded**</span></span>
- <span data-ttu-id="be04a-p104">У нас есть встроенная квота объекта, помогающая защитить службу. Если в вашем каталоге слишком много объектов, которые необходимо синхронизировать с Office 365, вам потребуется [обратиться в службу поддержки продуктов для бизнеса](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) , чтобы увеличить квоту.</span><span class="sxs-lookup"><span data-stu-id="be04a-p104">We have a built-in object quota to help protect the service. If you have too many objects in your directory that need to sync to Office 365, you'll have to [Contact support for business products](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) to increase your quota.</span></span>

### <a name="i-need-to-know-which-attributes-are-synchronized"></a><span data-ttu-id="be04a-134">**Необходимо определить, какие атрибуты синхронизируются**</span><span class="sxs-lookup"><span data-stu-id="be04a-134">**I need to know which attributes are synchronized**</span></span>
- <span data-ttu-id="be04a-135">Вы можете найти список всех атрибутов, которые синхронизируются между локальной средой и облаком [непосредственно](https://go.microsoft.com/fwlink/p/?LinkId=396719).</span><span class="sxs-lookup"><span data-stu-id="be04a-135">You can find a list of all the attributes that are synced between on-premises and the cloud [right here](https://go.microsoft.com/fwlink/p/?LinkId=396719).</span></span>

### <a name="i-cant-manage-or-remove-objects-that-were-synchronized-to-the-cloud"></a><span data-ttu-id="be04a-136">**Не удается управлять или удалять объекты, синхронизированные с облаком**</span><span class="sxs-lookup"><span data-stu-id="be04a-136">**I can't manage or remove objects that were synchronized to the cloud**</span></span>
- <span data-ttu-id="be04a-p105">Вы готовы управлять объектами только в облаке? Есть ли в облаке объект, который был удален локально, но в облаке он застрял? Ознакомьтесь с этой статьей [об устраненИи неполадок во время синхронизации](https://go.microsoft.com/fwlink/p/?linkid=842044) и [поддержки](https://go.microsoft.com/fwlink/p/?LinkId=396720) , чтобы получить рекомендации по устранению этих проблем.</span><span class="sxs-lookup"><span data-stu-id="be04a-p105">Are you ready to manage objects in the cloud only? Or is there an object that was deleted on-premises, but is stuck in the cloud? Take a look at this [Troubleshooting Errors during synchronization](https://go.microsoft.com/fwlink/p/?linkid=842044) and [support article](https://go.microsoft.com/fwlink/p/?LinkId=396720) for guidance on how to resolve these issues.</span></span>

### <a name="i-got-an-error-message-that-my-company-has-exceeded-the-number-of-objects-that-can-be-synchronized"></a><span data-ttu-id="be04a-140">**Появляется сообщение о том, что в компании превышено максимальное количество объектов, которые можно синхронизировать**</span><span class="sxs-lookup"><span data-stu-id="be04a-140">**I got an error message that my company has exceeded the number of objects that can be synchronized**</span></span>
- <span data-ttu-id="be04a-141">Подробнее об этой статье можно узнать [здесь](https://go.microsoft.com/fwlink/p/?LinkId=396721).</span><span class="sxs-lookup"><span data-stu-id="be04a-141">You can read more about this issue [here](https://go.microsoft.com/fwlink/p/?LinkId=396721).</span></span>
   
## <a name="other-resources"></a><span data-ttu-id="be04a-142">Другие ресурсы</span><span class="sxs-lookup"><span data-stu-id="be04a-142">Other resources</span></span>

- [<span data-ttu-id="be04a-143">Сценарий для устранения повторяющихся имен участников-пользователей</span><span class="sxs-lookup"><span data-stu-id="be04a-143">Script to fix duplicate user principal names</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396725)
    
- [<span data-ttu-id="be04a-144">Подготовка домена, не поддерживающего маршрутизацию (например, локального домена), для синхронизации службы каталогов</span><span class="sxs-lookup"><span data-stu-id="be04a-144">How to prepare a non-routable domain (such as .local domain) for directory synchronization</span></span>](prepare-a-non-routable-domain-for-directory-synchronization.md)
    
- [<span data-ttu-id="be04a-145">Скрипт для подсчета итоговых синхронизированных объектов</span><span class="sxs-lookup"><span data-stu-id="be04a-145">Script to count total synchronized objects</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396726)
    
- [<span data-ttu-id="be04a-146">Устранение неполадок AD FS 2,0</span><span class="sxs-lookup"><span data-stu-id="be04a-146">Troubleshoot AD FS 2.0</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396727)
    
- [<span data-ttu-id="be04a-147">Использование PowerShell для исправления пустых атрибутов DisplayName для групп с включенной поддержкой почты</span><span class="sxs-lookup"><span data-stu-id="be04a-147">Use PowerShell to fix empty DisplayName attributes for mail-enabled groups</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396728)
    
- [<span data-ttu-id="be04a-148">Использование PowerShell для исправления повторяющегося имени участника-пользователя</span><span class="sxs-lookup"><span data-stu-id="be04a-148">Use PowerShell to fix duplicate UPN</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396730)
    
- [<span data-ttu-id="be04a-149">Использование PowerShell для исправления дублирующихся адресов электронной почты</span><span class="sxs-lookup"><span data-stu-id="be04a-149">Use PowerShell to fix duplicate email addresses</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396731)
    
## <a name="diagnostic-tools"></a><span data-ttu-id="be04a-150">Средства диагностики</span><span class="sxs-lookup"><span data-stu-id="be04a-150">Diagnostic tools</span></span>

<span data-ttu-id="be04a-p106">[Средство IDFix](prepare-directory-attributes-for-synch-with-idfix.md) используется для выполнения обнаружения и исправления объектов Identity и их атрибутов в локальной среде Active Directory при подготовке к миграции в Office 365. IDFix предназначен для администраторов Active Directory, ответственных за DirSync, с помощью службы Office 365.</span><span class="sxs-lookup"><span data-stu-id="be04a-p106">[IDFix tool](prepare-directory-attributes-for-synch-with-idfix.md) is used to perform discovery and remediation of identity objects and their attributes in an on-premises Active Directory environment in preparation for migration to Office 365. IDFix is intended for the Active Directory administrators responsible for DirSync with the Office 365 service.</span></span> 

<span data-ttu-id="be04a-153">[Скачайте средство IDFix](https://go.microsoft.com/fwlink/p/?LinkId=396718) из центра загрузки Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="be04a-153">[Download the IDFix tool](https://go.microsoft.com/fwlink/p/?LinkId=396718) from the Microsoft download center.</span></span>