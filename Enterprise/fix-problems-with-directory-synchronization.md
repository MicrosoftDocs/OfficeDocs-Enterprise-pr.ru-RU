---
title: Устранение проблем с синхронизацией каталогов для Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MBS150
ms.assetid: 79c43023-5a47-45ae-8068-d8a26eee6bc2
description: Описываются распространенные причины проблем с синхронизацией каталогов в Office 365 и предоставляет несколько методов для устранения неполадок и устраните их.
ms.openlocfilehash: a1ccf7aa8c6d450cdd3d658ef0bc8d9ed6d25753
ms.sourcegitcommit: 6a4611bb474c783efd361890fe6f41c26c5aeeb3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/04/2018
ms.locfileid: "25405132"
---
# <a name="fixing-problems-with-directory-synchronization-for-office-365"></a><span data-ttu-id="e01fc-103">Устранение проблем с синхронизацией каталогов для Office 365</span><span class="sxs-lookup"><span data-stu-id="e01fc-103">Fixing problems with directory synchronization for Office 365</span></span>

<span data-ttu-id="e01fc-p101">С помощью синхронизации службы каталогов можно продолжить Управление пользователями и группами в локальной и синхронизация добавления, удаления и изменения в облако. Программа установки немного сложнее, но в некоторых случаях может быть трудно определить источник проблемы. У нас есть ресурсы, которые помогут вам определить потенциальные проблемы и их устранения.</span><span class="sxs-lookup"><span data-stu-id="e01fc-p101">With directory synchronization, you can continue to manage users and groups on-premises and synchronize additions, deletions, and changes to the cloud. But setup is a little complicated and it can sometimes be difficult to identify the source of problems. We have resources to help you identify potential issues and fix them.</span></span>
  
## <a name="how-do-i-know-if-something-is-wrong"></a><span data-ttu-id="e01fc-107">Как узнать, что-то неверно?</span><span class="sxs-lookup"><span data-stu-id="e01fc-107">How do I know if something is wrong?</span></span>

<span data-ttu-id="e01fc-108">Первым признаком того, что дает сбой при Плитка DirSync состояния в центре администрирования Office 365 указывает, что проблемы:</span><span class="sxs-lookup"><span data-stu-id="e01fc-108">The first indication that something is wrong is when the DirSync Status tile in the Office 365 admin center indicates there is a problem:</span></span>
  
![Состояние DirSync плиток в предварительной версии центра администрирования](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
<span data-ttu-id="e01fc-p102">Также вы получите почты (альтернативного электронной почты и электронной почты администратора) с Office 365, который указывает, что клиент обнаружил ошибок синхронизации службы каталогов. Для получения дополнительных сведений см [Определение ошибок синхронизации службы каталогов в Office 365](identify-directory-synchronization-errors.md).</span><span class="sxs-lookup"><span data-stu-id="e01fc-p102">You will also receive a mail (to the alternate email and to your admin email) from Office 365 that indicates your tenant has encountered directory synchronization errors. For details see [Identify directory synchronization errors in Office 365](identify-directory-synchronization-errors.md).</span></span>
  
## <a name="how-do-i-get-azure-active-directory-connect-tool"></a><span data-ttu-id="e01fc-112">Как получить средство подключения Azure Active Directory?</span><span class="sxs-lookup"><span data-stu-id="e01fc-112">How do I get Azure Active Directory Connect tool?</span></span>

<span data-ttu-id="e01fc-p103">В центре администрирования Office 365 перейдите к разделу \*\* пользователей \*\* \> **Активные пользователи**. Щелкните **Дополнительные** меню и выберите **синхронизации службы каталогов**.</span><span class="sxs-lookup"><span data-stu-id="e01fc-p103">In the Office 365 admin center, navigate to \*\* Users \*\* \> **Active users**. Click the **More** menu and select **Directory synchronization**.</span></span> 
  
![Выберите в меню Дополнительные синхронизации службы каталогов](media/dc6669e5-c01b-471e-9cdf-04f5d44e1c4b.png)
  
<span data-ttu-id="e01fc-116">В старой центра администрирования Office 365 перейдите к **пользователям** \> **Активных пользователей**и выберите **Настройка** синхронизации **Active Directory**.</span><span class="sxs-lookup"><span data-stu-id="e01fc-116">In the old Office 365 admin center, navigate to **USERS** \> **Active Users**, and select **Set up** next to **Active Directory synchronization**.</span></span> 
  
![Щелкните настроить синхронизации Active Directory](media/bd95492b-d65e-4072-a6ee-e562f5f566c3.png)
  
<span data-ttu-id="e01fc-118">Следуйте [инструкциям мастера](set-up-directory-synchronization.md) , чтобы загрузить подключить Azure AD.</span><span class="sxs-lookup"><span data-stu-id="e01fc-118">Follow the [instructions in the wizard](set-up-directory-synchronization.md) to download Azure AD Connect.</span></span> 
  
<span data-ttu-id="e01fc-119">Если вы используете по-прежнему синхронизации Azure Active Directory (DirSync), посмотрите на [Устранение неполадок при установке средства синхронизации Azure Active Directory и мастер настройки сообщений об ошибках в Office 365](https://go.microsoft.com/fwlink/p/?LinkId=396717) для получения сведений о требованиях к системе для установки DirSync, разрешения, необходимые и способы устранения наиболее распространенных ошибок.</span><span class="sxs-lookup"><span data-stu-id="e01fc-119">If you are still using Azure Active Directory Sync (DirSync), take a look at [How to troubleshoot Azure Active Directory Sync Tool installation and Configuration Wizard error messages in Office 365](https://go.microsoft.com/fwlink/p/?LinkId=396717) for information about the system requirements to install dirsync, the permissions you need, and how to troubleshoot common errors.</span></span> 
  
<span data-ttu-id="e01fc-120">Для обновления от синхронизации Azure Active Directory подключение Azure AD, видеть [инструкциями по обновлению](https://go.microsoft.com/fwlink/p/?LinkId=733240).</span><span class="sxs-lookup"><span data-stu-id="e01fc-120">To update from Azure Active Directory Sync to Azure AD Connect, see [the upgrade instructions](https://go.microsoft.com/fwlink/p/?LinkId=733240).</span></span>
  
## <a name="resolving-common-causes-of-problems-with-directory-synchronization-in-office-365"></a><span data-ttu-id="e01fc-121">Устранение распространенных причин проблем с синхронизацией каталогов в Office 365</span><span class="sxs-lookup"><span data-stu-id="e01fc-121">Resolving common causes of problems with directory synchronization in Office 365</span></span>

### <a name="synchronized-objects-arent-appearing-or-updating-online-or-im-getting-synchronization-error-reports-from-the-service"></a><span data-ttu-id="e01fc-122">**Объекты не отображаются или обновление online или отчеты об ошибках синхронизации получены от службы.**</span><span class="sxs-lookup"><span data-stu-id="e01fc-122">**Synchronized objects aren't appearing or updating online, or I'm getting synchronization error reports from the Service.**</span></span>

- [<span data-ttu-id="e01fc-123">Устойчивость атрибут синхронизации и повторяющихся удостоверений</span><span class="sxs-lookup"><span data-stu-id="e01fc-123">Identity synchronization and duplicate attribute resiliency</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=798300)

### <a name="i-have-an-alert-in-the-office-365-admin-center-or-am-receiving-automated-emails-that-there-hasnt-been-a-recent-synchronization-event"></a><span data-ttu-id="e01fc-124">**Я иметь оповещения в центре администрирования Office 365 или выводится сообщение, что не был недавнее событие синхронизации автоматическая отправка сообщения электронной почты**</span><span class="sxs-lookup"><span data-stu-id="e01fc-124">**I have an alert in the Office 365 admin center, or am receiving automated emails that there hasn't been a recent synchronization event**</span></span>
- [<span data-ttu-id="e01fc-125">Устранения неполадок подключения к с Azure AD подключение</span><span class="sxs-lookup"><span data-stu-id="e01fc-125">Troubleshoot connectivity issues with Azure AD Connect</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=820597)
- [<span data-ttu-id="e01fc-126">Azure учетные записи подключения AD и разрешения</span><span class="sxs-lookup"><span data-stu-id="e01fc-126">Azure AD Connect Accounts and permissions</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=820598)
- [<span data-ttu-id="e01fc-127">Azure AD подключение синхронизации: управление учетной записи службы Azure AD</span><span class="sxs-lookup"><span data-stu-id="e01fc-127">Azure AD Connect sync: How to manage the Azure AD service account</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=820599)
- [<span data-ttu-id="e01fc-128">Синхронизации службы каталогов останавливает Azure Active Directory или в случае предупреждение о том, что синхронизация не зарегистрировано в более одного дня</span><span class="sxs-lookup"><span data-stu-id="e01fc-128">Directory synchronization to Azure Active Directory stops or you're warned that sync hasn't registered in more than a day</span></span>](https://support.microsoft.com/help/2882421/directory-synchronization-to-azure-active-directory-stops-or-you-re-warned-that-sync-hasn-t-registered-in-more-than-a-day)

### <a name="password-hashes-arent-synchronizing-or-im-seeing-an-alert-in-the-office-365-admin-center-that-there-hasnt-been-a-recent-password-hash-synchronization"></a><span data-ttu-id="e01fc-129">**Не синхронизация хэши паролей или я вижу оповещения в центре администрирования Office 365, что не был последние хэш-функции синхронизации паролей**</span><span class="sxs-lookup"><span data-stu-id="e01fc-129">**Password hashes aren't synchronizing, or I'm seeing an alert in the Office 365 admin center that there hasn't been a recent password hash synchronization**</span></span>
- [<span data-ttu-id="e01fc-130">Реализация хэш-функции синхронизации паролей с помощью Azure AD подключение синхронизации</span><span class="sxs-lookup"><span data-stu-id="e01fc-130">Implementing password hash synchronization with Azure AD Connect sync</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization)

### <a name="im-seeing-an-alert-that-object-quota-exceeded"></a><span data-ttu-id="e01fc-131">**Я вижу оповещение о превышении квот объектов**</span><span class="sxs-lookup"><span data-stu-id="e01fc-131">**I'm seeing an alert that Object quota exceeded**</span></span>
- <span data-ttu-id="e01fc-p104">У нас есть квоты встроенный объект для защиты службы. При наличии слишком большого числа объектов в каталоге, которые необходимо синхронизировать с Office 365, потребуется увеличить квоту на почтовый [контакт поддержки продуктов бизнес](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) .</span><span class="sxs-lookup"><span data-stu-id="e01fc-p104">We have a built-in object quota to help protect the service. If you have too many objects in your directory that need to sync to Office 365, you'll have to [Contact support for business products](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) to increase your quota.</span></span>

### <a name="i-need-to-know-which-attributes-are-synchronized"></a><span data-ttu-id="e01fc-134">**Необходимо определить, какие атрибуты синхронизируются**</span><span class="sxs-lookup"><span data-stu-id="e01fc-134">**I need to know which attributes are synchronized**</span></span>
- <span data-ttu-id="e01fc-135">Список всех атрибутов, которые синхронизируются между локальной и облачных [право здесь](https://go.microsoft.com/fwlink/p/?LinkId=396719)можно найти.</span><span class="sxs-lookup"><span data-stu-id="e01fc-135">You can find a list of all the attributes that are synced between on-premises and the cloud [right here](https://go.microsoft.com/fwlink/p/?LinkId=396719).</span></span>

### <a name="i-cant-manage-or-remove-objects-that-were-synchronized-to-the-cloud"></a><span data-ttu-id="e01fc-136">**Не удается управлять или удалить объекты, которые были синхронизированы с облаком**</span><span class="sxs-lookup"><span data-stu-id="e01fc-136">**I can't manage or remove objects that were synchronized to the cloud**</span></span>
- <span data-ttu-id="e01fc-p105">Все готово для управления объектами в облаке только? Или, существует ли объект, который был удаленных локальные, но обращается в облаке? Рассмотрим этот [Устранение ошибок во время синхронизации](https://go.microsoft.com/fwlink/p/?linkid=842044) и [поддержки статьи](https://go.microsoft.com/fwlink/p/?LinkId=396720) для инструкции о том, как решить эти проблемы.</span><span class="sxs-lookup"><span data-stu-id="e01fc-p105">Are you ready to manage objects in the cloud only? Or is there an object that was deleted on-premises, but is stuck in the cloud? Take a look at this [Troubleshooting Errors during synchronization](https://go.microsoft.com/fwlink/p/?linkid=842044) and [support article](https://go.microsoft.com/fwlink/p/?LinkId=396720) for guidance on how to resolve these issues.</span></span>

### <a name="i-got-an-error-message-that-my-company-has-exceeded-the-number-of-objects-that-can-be-synchronized"></a><span data-ttu-id="e01fc-140">**Появляется сообщение о том, что в компании превышено максимальное количество объектов, которые можно синхронизировать**</span><span class="sxs-lookup"><span data-stu-id="e01fc-140">**I got an error message that my company has exceeded the number of objects that can be synchronized**</span></span>
- <span data-ttu-id="e01fc-141">Можно прочитать подробнее об этой проблеме [здесь](https://go.microsoft.com/fwlink/p/?LinkId=396721).</span><span class="sxs-lookup"><span data-stu-id="e01fc-141">You can read more about this issue [here](https://go.microsoft.com/fwlink/p/?LinkId=396721).</span></span>
   
## <a name="other-resources"></a><span data-ttu-id="e01fc-142">Другие ресурсы</span><span class="sxs-lookup"><span data-stu-id="e01fc-142">Other resources</span></span>

- [<span data-ttu-id="e01fc-143">Сценарий для исправления дублированных основные имена</span><span class="sxs-lookup"><span data-stu-id="e01fc-143">Script to fix duplicate user principal names</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396725)
    
- [<span data-ttu-id="e01fc-144">Подготовка к синхронизации службы каталогов без поддержки маршрутизации домена (например, .local домена)</span><span class="sxs-lookup"><span data-stu-id="e01fc-144">How to prepare a non-routable domain (such as .local domain) for directory synchronization</span></span>](prepare-a-non-routable-domain-for-directory-synchronization.md)
    
- [<span data-ttu-id="e01fc-145">Сценарий для подсчета всего синхронизированных объектов</span><span class="sxs-lookup"><span data-stu-id="e01fc-145">Script to count total synchronized objects</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396726)
    
- [<span data-ttu-id="e01fc-146">Устранение неполадок AD FS 2.0 (en)</span><span class="sxs-lookup"><span data-stu-id="e01fc-146">Troubleshoot AD FS 2.0</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396727)
    
- [<span data-ttu-id="e01fc-147">Использование PowerShell для исправления пустых атрибутов DisplayName для групп с включенной поддержкой почты</span><span class="sxs-lookup"><span data-stu-id="e01fc-147">Use PowerShell to fix empty DisplayName attributes for mail-enabled groups</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396728)
    
- [<span data-ttu-id="e01fc-148">Использование PowerShell для исправления дублированных имени участника-пользователя</span><span class="sxs-lookup"><span data-stu-id="e01fc-148">Use PowerShell to fix duplicate UPN</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396730)
    
- [<span data-ttu-id="e01fc-149">Использование PowerShell для исправления адреса повторяющихся электронной почты</span><span class="sxs-lookup"><span data-stu-id="e01fc-149">Use PowerShell to fix duplicate email addresses</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396731)
    
## <a name="diagnostic-tools"></a><span data-ttu-id="e01fc-150">Средства диагностики</span><span class="sxs-lookup"><span data-stu-id="e01fc-150">Diagnostic tools</span></span>

<span data-ttu-id="e01fc-p106">[Инструмент IDFix](prepare-directory-attributes-for-synch-with-idfix.md) используется для выполнения средства обнаружения и исправлению удостоверения объектов и их атрибутов в локальной среде Active Directory при подготовке к миграции в Office 365. IDFix предназначена для администраторов Active Directory, ответственный за DirSync со службой Office 365.</span><span class="sxs-lookup"><span data-stu-id="e01fc-p106">[IDFix tool](prepare-directory-attributes-for-synch-with-idfix.md) is used to perform discovery and remediation of identity objects and their attributes in an on-premises Active Directory environment in preparation for migration to Office 365. IDFix is intended for the Active Directory administrators responsible for DirSync with the Office 365 service.</span></span> 

<span data-ttu-id="e01fc-153">[Загрузите средство IDFix](https://go.microsoft.com/fwlink/p/?LinkId=396718) из центра загрузки Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="e01fc-153">[Download the IDFix tool](https://go.microsoft.com/fwlink/p/?LinkId=396718) from the Microsoft download center.</span></span>