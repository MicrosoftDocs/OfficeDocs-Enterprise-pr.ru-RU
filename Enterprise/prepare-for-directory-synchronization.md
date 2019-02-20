---
title: Подготовка к подготовке пользователей с помощью синхронизации службы каталогов в Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: article
f1_keywords:
- O365p_AddUsersWithDirSync
- O365M_AddUsersWithDirSync
- O365E_HRCSetupAADConnectAboutLM617031
- O365E_AddUsersWithDirSync
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOP150
- MOE150
- MBS150
ms.assetid: 01920974-9e6f-4331-a370-13aea4e82b3e
description: В этой статье описано, как подготовить пользователей к работе с Office 365, используя синхронизацию службы каталогов и долгосрочные преимущества использования этого метода.
ms.openlocfilehash: af402950b3681285898d0d87b897d363a693bf98
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085108"
---
# <a name="prepare-to-provision-users-through-directory-synchronization-to-office-365"></a><span data-ttu-id="d32cb-103">Подготовка к подготовке пользователей с помощью синхронизации службы каталогов в Office 365</span><span class="sxs-lookup"><span data-stu-id="d32cb-103">Prepare to provision users through directory synchronization to Office 365</span></span>

<span data-ttu-id="d32cb-p101">Подготовка пользователей с синхронизацией службы каталогов требует больше планирования и подготовки, чем простое управление рабочей или учебной учетной записью непосредственно в Office 365. Для проверки правильности синхронизации локальной службы Active Directory с Azure Active Directory необходимо выполнить дополнительные задачи планирования и подготовки. К вашей организации добавлены следующие преимущества:</span><span class="sxs-lookup"><span data-stu-id="d32cb-p101">Provisioning users with directory synchronization requires more planning and preparation than simply managing your work or school account directly in Office 365. The additional planning and preparation tasks are required to ensure that your on-premises Active Directory synchronizes properly to Azure Active Directory. The added benefits to your organization include:</span></span>
  
- <span data-ttu-id="d32cb-107">Уменьшение количества программ администрирования в организации</span><span class="sxs-lookup"><span data-stu-id="d32cb-107">Reducing the administrative programs in your organization</span></span>
- <span data-ttu-id="d32cb-108">НеОбязательное включение сценария единого входа</span><span class="sxs-lookup"><span data-stu-id="d32cb-108">Optionally enabling single sign-on scenario</span></span>
- <span data-ttu-id="d32cb-109">Автоматическое изменение учетной записи в Office 365</span><span class="sxs-lookup"><span data-stu-id="d32cb-109">Automating account changes in Office 365</span></span>
    
<span data-ttu-id="d32cb-110">Более подробную информацию о преимуществах синхронизации службы каталогов можно узнать в статье [схема синхронизации службы каталогов]( https://go.microsoft.com/fwlink/p/?LinkId=525398) и [сведения об удостоверении Office 365 и Azure Active Directory](about-office-365-identity.md).</span><span class="sxs-lookup"><span data-stu-id="d32cb-110">For more information about the advantages of using directory synchronization, see [Directory synchronization roadmap]( https://go.microsoft.com/fwlink/p/?LinkId=525398) and [Understanding Office 365 Identity and Azure Active Directory](about-office-365-identity.md).</span></span>
  
<span data-ttu-id="d32cb-111">Чтобы определить, какой сценарий лучше всего подходит для вашей организации, изучите [Сравнение средств интеграции каталогов](https://go.microsoft.com/fwlink/p/?LinkId=525320).</span><span class="sxs-lookup"><span data-stu-id="d32cb-111">To determine which scenario is the best for your organization, review the [directory integration tools comparison](https://go.microsoft.com/fwlink/p/?LinkId=525320).</span></span>
  
## <a name="directory-cleanup-tasks"></a><span data-ttu-id="d32cb-112">Задачи очистки каталога</span><span class="sxs-lookup"><span data-stu-id="d32cb-112">Directory cleanup tasks</span></span>

<span data-ttu-id="d32cb-113">Перед началом синхронизации каталога необходимо очистить каталог.</span><span class="sxs-lookup"><span data-stu-id="d32cb-113">Before you begin synchronizing your directory, you need to clean up your directory.</span></span>
  
<span data-ttu-id="d32cb-114">Просмотрите также [атрибуты, синхронизированные с Azure Active Directory по Azure AD Connect](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-sync-attributes-synchronized).</span><span class="sxs-lookup"><span data-stu-id="d32cb-114">Review also the [attributes synchronized to Azure Active Directory by Azure AD Connect](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-sync-attributes-synchronized).</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="d32cb-p102">Если вы не выполняете очистку каталога перед синхронизацией, в процессе развертывания может быть значительно отрицательное значение. Может потребоваться несколько дней или даже недель, чтобы пройти цикл синхронизации службы каталогов, выявить ошибки и повторную синхронизацию.</span><span class="sxs-lookup"><span data-stu-id="d32cb-p102">If you don't perform directory cleanup before you synchronize, there can be a significant negative effect on the deployment process. It might take days, or even weeks, to go through the cycle of directory synchronization, identifying errors, and re-synchronization.</span></span> 
  
<span data-ttu-id="d32cb-117">В локальном каталоге выполните следующие задачи очистки:</span><span class="sxs-lookup"><span data-stu-id="d32cb-117">In your on-premises directory, complete the following clean-up tasks:</span></span>
  
1. <span data-ttu-id="d32cb-118">Убедитесь, что у каждого пользователя, который будет использовать службы Office 365, есть действительный и уникальный адрес электронной почты в атрибуте **proxyAddresses**.</span><span class="sxs-lookup"><span data-stu-id="d32cb-118">Ensure that each user who will be assigned Office 365 service offerings has a valid and unique email address in the **proxyAddresses** attribute.</span></span> 
    
2. <span data-ttu-id="d32cb-119">Удалите все повторяющиеся значения в атрибуте **proxyAddresses**.</span><span class="sxs-lookup"><span data-stu-id="d32cb-119">Remove any duplicate values in the **proxyAddresses** attribute.</span></span> 
    
3.  <span data-ttu-id="d32cb-p103">Если это возможно, убедитесь, что каждый пользователь, которому будут назначены службы Office 365, имеет допустимое и уникальное значение атрибута **userPrincipalName** в объекте **пользователя** пользователя. Для достижения наилучших результатов синхронизации убедитесь, что локальное имя участника-пользователя Active Directory соответствует имени участника-пользователя в облаке. Если у пользователя нет значения атрибута **userPrincipalName** , то объект **пользователя** должен содержать допустимое и уникальное значение для атрибута **SamAccountName** . Удалите все повторяющиеся значения в атрибуте **userPrincipalName** .</span><span class="sxs-lookup"><span data-stu-id="d32cb-p103">If possible, ensure that each user who will be assigned Office 365 service offerings has a valid and unique value for the **userPrincipalName** attribute in the user's **user** object. For best synchronization experience, ensure that the on-premises Active Directory UPN matches the cloud UPN. If a user does not have a value for the **userPrincipalName** attribute, then the **user** object must contain a valid and unique value for the **sAMAccountName** attribute. Remove any duplicate values in the **userPrincipalName** attribute.</span></span> 
    
4. <span data-ttu-id="d32cb-124">Для оптимального применения глобального списка адресов (GAL) проверьте правильность информации в следующих атрибутах:</span><span class="sxs-lookup"><span data-stu-id="d32cb-124">For optimal use of the global address list (GAL), be sure the information in the following attributes is correct:</span></span>
    
  - <span data-ttu-id="d32cb-125">givenName </span><span class="sxs-lookup"><span data-stu-id="d32cb-125">givenName</span></span>
  - <span data-ttu-id="d32cb-126">surname</span><span class="sxs-lookup"><span data-stu-id="d32cb-126">surname</span></span>
  - <span data-ttu-id="d32cb-127">displayName</span><span class="sxs-lookup"><span data-stu-id="d32cb-127">displayName</span></span>
  - <span data-ttu-id="d32cb-128">Должность</span><span class="sxs-lookup"><span data-stu-id="d32cb-128">Job Title</span></span>
  - <span data-ttu-id="d32cb-129">Отдел</span><span class="sxs-lookup"><span data-stu-id="d32cb-129">Department</span></span>
  - <span data-ttu-id="d32cb-130">Кабинет</span><span class="sxs-lookup"><span data-stu-id="d32cb-130">Office</span></span>
  - <span data-ttu-id="d32cb-131">Рабочий телефон</span><span class="sxs-lookup"><span data-stu-id="d32cb-131">Office Phone</span></span>
  - <span data-ttu-id="d32cb-132">Мобильный телефон</span><span class="sxs-lookup"><span data-stu-id="d32cb-132">Mobile Phone</span></span>
  - <span data-ttu-id="d32cb-133">Номер факса</span><span class="sxs-lookup"><span data-stu-id="d32cb-133">Fax Number</span></span>
  - <span data-ttu-id="d32cb-134">Улица, дом</span><span class="sxs-lookup"><span data-stu-id="d32cb-134">Street Address</span></span>
  - <span data-ttu-id="d32cb-135">Город</span><span class="sxs-lookup"><span data-stu-id="d32cb-135">City</span></span>
  - <span data-ttu-id="d32cb-136">Область или район</span><span class="sxs-lookup"><span data-stu-id="d32cb-136">State or Province</span></span>
  - <span data-ttu-id="d32cb-137">Почтовый индекс</span><span class="sxs-lookup"><span data-stu-id="d32cb-137">Zip or Postal Code</span></span>
  - <span data-ttu-id="d32cb-138">Страна или регион</span><span class="sxs-lookup"><span data-stu-id="d32cb-138">Country or Region</span></span>
    
## <a name="directory-object-and-attribute-preparation"></a><span data-ttu-id="d32cb-139">Подготовка объектов и атрибутов каталога</span><span class="sxs-lookup"><span data-stu-id="d32cb-139">Directory object and attribute preparation</span></span>

<span data-ttu-id="d32cb-p104">Для успешной синхронизации каталогов между локальным каталогом и Office 365 необходимо, чтобы атрибуты локального каталога были правильно подготовлены. Например, необходимо убедиться, что определенные символы не используются в определенных атрибутах, которые синхронизируются с средой Office 365. НеПредусмотренные символы не приводят к сбою синхронизации службы каталогов, но могут возвращать предупреждение. НеДопустимые символы приведут к сбою синхронизации службы каталогов.</span><span class="sxs-lookup"><span data-stu-id="d32cb-p104">Successful directory synchronization between your on-premises directory and Office 365 requires that your on-premises directory attributes are properly prepared. For example, you need to ensure that specific characters aren't used in certain attributes that are synchronized with the Office 365 environment. Unexpected characters do not cause directory synchronization to fail but might return a warning. Invalid characters will cause directory synchronization to fail.</span></span>
  
<span data-ttu-id="d32cb-p105">Синхронизация службы каталогов также завершится с ошибками, если некоторые пользователи Active Directory имеют один или несколько повторяющихся атрибутов. Каждый пользователь должен иметь уникальные атрибуты.</span><span class="sxs-lookup"><span data-stu-id="d32cb-p105">Directory synchronization will also fail if some of your Active Directory users have one or more duplicate attributes. Each user must have unique attributes.</span></span>
  
<span data-ttu-id="d32cb-146">Ниже перечислены атрибуты, которые необходимо подготовить.</span><span class="sxs-lookup"><span data-stu-id="d32cb-146">The attributes that you need to prepare are listed here:</span></span>
  
 <span data-ttu-id="d32cb-147">**Примечание:** Кроме того, вы можете использовать [средство IdFix](install-and-run-idfix.md) , чтобы сделать этот процесс намного проще.</span><span class="sxs-lookup"><span data-stu-id="d32cb-147">**NOTE:** You can also use the [IdFix tool](install-and-run-idfix.md) to make this process a lot easier.</span></span> 
  
- <span data-ttu-id="d32cb-148">**displayName**</span><span class="sxs-lookup"><span data-stu-id="d32cb-148">**displayName**</span></span>
    
  - <span data-ttu-id="d32cb-149">Если в объекте пользователя существует атрибут, он будет синхронизирован с Office 365.</span><span class="sxs-lookup"><span data-stu-id="d32cb-149">If the attribute exists in the user object, it will be synchronized with Office 365.</span></span>
  - <span data-ttu-id="d32cb-p106">Если этот атрибут существует в объекте пользователя, для него должно быть предусмотрено значение. То есть атрибут не должен быть пустым.</span><span class="sxs-lookup"><span data-stu-id="d32cb-p106">If this attribute exists in the user object, there must be a value for it. That is, the attribute must not be blank.</span></span>
  - <span data-ttu-id="d32cb-152">Максимальное число символов: 256</span><span class="sxs-lookup"><span data-stu-id="d32cb-152">Maximum number of characters: 256</span></span>
    
- <span data-ttu-id="d32cb-153">\*\*givenName \*\*</span><span class="sxs-lookup"><span data-stu-id="d32cb-153">**givenName**</span></span>
    
  - <span data-ttu-id="d32cb-154">Если атрибут существует в объекте пользователя, он будет синхронизирован с Office 365, но он не требуется и не используется в Office 365.</span><span class="sxs-lookup"><span data-stu-id="d32cb-154">If the attribute exists in the user object, it will be synchronized with Office 365, but Office 365 does not require or use it.</span></span>
  - <span data-ttu-id="d32cb-155">Максимальное число символов: 64</span><span class="sxs-lookup"><span data-stu-id="d32cb-155">Maximum number of characters: 64</span></span>
    
- <span data-ttu-id="d32cb-156">**mail**</span><span class="sxs-lookup"><span data-stu-id="d32cb-156">**mail**</span></span>
    
  - <span data-ttu-id="d32cb-157">Значение атрибута должно быть уникальным в пределах каталога.</span><span class="sxs-lookup"><span data-stu-id="d32cb-157">The attribute value must be unique within the directory.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="d32cb-p107">Если имеются повторяющиеся значения, первый пользователь со значением синхронизируется. Последующие пользователи не будут отображаться в Office 365. Необходимо изменить значение в Office 365 или изменить оба значения в локальном каталоге, чтобы оба пользователя отображались в Office 365.</span><span class="sxs-lookup"><span data-stu-id="d32cb-p107">If there are duplicate values, the first user with the value is synchronized. Subsequent users will not appear in Office 365. You must modify either the value in Office 365, or modify both of the values in the on-premises directory in order for both users to appear in Office 365.</span></span> 
  
- <span data-ttu-id="d32cb-161">**mailNickname** (псевдоним Exchange)</span><span class="sxs-lookup"><span data-stu-id="d32cb-161">**mailNickname** (Exchange alias)</span></span> 
    
  - <span data-ttu-id="d32cb-162">Значение атрибута не может начинаться с точки (.).</span><span class="sxs-lookup"><span data-stu-id="d32cb-162">The attribute value cannot begin with a period (.).</span></span>
  - <span data-ttu-id="d32cb-163">Значение атрибута должно быть уникальным в пределах каталога.</span><span class="sxs-lookup"><span data-stu-id="d32cb-163">The attribute value must be unique within the directory.</span></span>
    
- <span data-ttu-id="d32cb-164">\*\*proxyAddresses \*\*</span><span class="sxs-lookup"><span data-stu-id="d32cb-164">**proxyAddresses**</span></span>
    
  - <span data-ttu-id="d32cb-165">Атрибут с несколькими значениями</span><span class="sxs-lookup"><span data-stu-id="d32cb-165">Multiple-value attribute</span></span>
  - <span data-ttu-id="d32cb-166">Максимальное количество символов для одного значения: 256</span><span class="sxs-lookup"><span data-stu-id="d32cb-166">Maximum number of characters per value: 256</span></span>
  - <span data-ttu-id="d32cb-167">Значение атрибута не должно содержать пробел.</span><span class="sxs-lookup"><span data-stu-id="d32cb-167">The attribute value must not contain a space.</span></span>
  - <span data-ttu-id="d32cb-168">Значение атрибута должно быть уникальным в пределах каталога.</span><span class="sxs-lookup"><span data-stu-id="d32cb-168">The attribute value must be unique within the directory.</span></span>
  - <span data-ttu-id="d32cb-169">НеДопустимые \< \> символы: (); , [ ] "</span><span class="sxs-lookup"><span data-stu-id="d32cb-169">Invalid characters: \< \> ( ) ; , [ ] "</span></span>
    
    <span data-ttu-id="d32cb-170">Обратите внимание, что недопустимые символы применяются к символам, которые следует за разделителем типов и ":", так как SMTP:User@contso.com разрешен, а SMTP:user:M@contoso.com — нет.</span><span class="sxs-lookup"><span data-stu-id="d32cb-170">Note that the invalid characters apply to the characters following the type delimiter and ":", such that SMTP:User@contso.com is allowed, but SMTP:user:M@contoso.com is not.</span></span>
    
    > [!IMPORTANT]
    > <span data-ttu-id="d32cb-p108">Все SMTP-адреса должны соответствовать стандартам обмена сообщениями электронной почты. Если имеются повторяющиеся или нежелательные адреса, ознакомьтесь с разделом справки [Удаление повторяющихся и нежелательных прокси-адресов в Exchange](https://go.microsoft.com/fwlink/?LinkId=293860).</span><span class="sxs-lookup"><span data-stu-id="d32cb-p108">All Simple Mail Transport Protocol (SMTP) addresses should comply with email messaging standards. If duplicate or unwanted addresses exist, see the Help topic [Removing duplicate and unwanted proxy addresses in Exchange](https://go.microsoft.com/fwlink/?LinkId=293860).</span></span> 
  
- <span data-ttu-id="d32cb-173">**sAMAccountName**</span><span class="sxs-lookup"><span data-stu-id="d32cb-173">**sAMAccountName**</span></span>
    
  - <span data-ttu-id="d32cb-174">Максимальное количество символов: 20</span><span class="sxs-lookup"><span data-stu-id="d32cb-174">Maximum number of characters: 20</span></span>
  - <span data-ttu-id="d32cb-175">Значение атрибута должно быть уникальным в пределах каталога.</span><span class="sxs-lookup"><span data-stu-id="d32cb-175">The attribute value must be unique within the directory.</span></span>
  - <span data-ttu-id="d32cb-p109">НеДопустимые символы: [\ "|, \< \> /: + =;? \* ]</span><span class="sxs-lookup"><span data-stu-id="d32cb-p109">Invalid characters: [ \ " | , / : \< \> + = ; ? \* ]</span></span>
  - <span data-ttu-id="d32cb-178">Если пользователь имеет недопустимый атрибут **sAMAccountName**, но имеет допустимый атрибут **userPrincipalName**, учетная запись пользователя создается в Office 365.</span><span class="sxs-lookup"><span data-stu-id="d32cb-178">If a user has an invalid **sAMAccountName** attribute but has a valid **userPrincipalName** attribute, the user account is created in Office 365.</span></span> 
  - <span data-ttu-id="d32cb-179">Если и **SamAccountName** , и **userPrincipalName** являются недопустимыми, необходимо обновить атрибут, расположенный в локальной службе Active Directory **userPrincipalName** .</span><span class="sxs-lookup"><span data-stu-id="d32cb-179">If both **sAMAccountName** and **userPrincipalName** are invalid, the on-premises Active Directory **userPrincipalName** attribute must be updated.</span></span> 
    
- <span data-ttu-id="d32cb-180">**sn** (фамилия)</span><span class="sxs-lookup"><span data-stu-id="d32cb-180">**sn** (surname)</span></span> 
    
  - <span data-ttu-id="d32cb-181">Если атрибут существует в объекте пользователя, он будет синхронизирован с Office 365, но он не требуется и не используется в Office 365.</span><span class="sxs-lookup"><span data-stu-id="d32cb-181">If the attribute exists in the user object, it will be synchronized with Office 365, but Office 365 does not require or use it.</span></span>
    
- <span data-ttu-id="d32cb-182">**targetAddress**</span><span class="sxs-lookup"><span data-stu-id="d32cb-182">**targetAddress**</span></span>
    
    <span data-ttu-id="d32cb-p110">Необходимо, чтобы атрибут **targetAddress** (например, SMTP:Tom@contoso.com), заполненный для пользователя, отображался в глобальном списке адресов Office 365. В сценариях миграции сторонней системы обмена сообщениями для локального каталога потребуется расширение схемы Office 365. Расширение схемы Office 365 также будет добавлять другие атрибуты для управления объектами Office 365, заполненными с помощью средства синхронизации каталогов из локального каталога. Например, вы добавите атрибут **msExchHideFromAddressLists** для управления скрытыми почтовыми ящиками или группами рассылки.</span><span class="sxs-lookup"><span data-stu-id="d32cb-p110">It's required that the **targetAddress** attribute (for example, SMTP:tom@contoso.com) that's populated for the user must appear in the Office 365 GAL. In third-party messaging migration scenarios, this would require the Office 365 schema extension for the on-premises directory. The Office 365 schema extension would also add other useful attributes to manage Office 365 objects that are populated by using a directory synchronization tool from on-premises directory. For example, the **msExchHideFromAddressLists** attribute to manage hidden mailboxes or distribution groups would be added.</span></span> 
   
  - <span data-ttu-id="d32cb-187">Максимальное число символов: 256</span><span class="sxs-lookup"><span data-stu-id="d32cb-187">Maximum number of characters: 256</span></span>
  - <span data-ttu-id="d32cb-188">Значение атрибута не должно содержать пробел.</span><span class="sxs-lookup"><span data-stu-id="d32cb-188">The attribute value must not contain a space.</span></span>
  - <span data-ttu-id="d32cb-189">Значение атрибута должно быть уникальным в пределах каталога.</span><span class="sxs-lookup"><span data-stu-id="d32cb-189">The attribute value must be unique within the directory.</span></span>
  - <span data-ttu-id="d32cb-190">НеДопустимые символы \< \> : \ (); , [ ] "</span><span class="sxs-lookup"><span data-stu-id="d32cb-190">Invalid characters: \ \< \> ( ) ; , [ ] "</span></span>
  - <span data-ttu-id="d32cb-191">Все SMTP-адреса должны соответствовать стандартам обмена сообщениями электронной почты.</span><span class="sxs-lookup"><span data-stu-id="d32cb-191">All Simple Mail Transport Protocol (SMTP) addresses should comply with email messaging standards.</span></span>
    
- <span data-ttu-id="d32cb-192">**userPrincipalName**</span><span class="sxs-lookup"><span data-stu-id="d32cb-192">**userPrincipalName**</span></span>
    
  - <span data-ttu-id="d32cb-p111">Атрибут **userPrincipalName** должен быть в формате для входа в Интернет, где за именем пользователя следуют знак "@" и доменное имя: например, user@contoso.com. Все SMTP-адреса должны соответствовать стандартам обмена сообщениями электронной почты.</span><span class="sxs-lookup"><span data-stu-id="d32cb-p111">The **userPrincipalName** attribute must be in the Internet-style sign-in format where the user name is followed by the at sign (@) and a domain name: for example, user@contoso.com. All Simple Mail Transport Protocol (SMTP) addresses should comply with email messaging standards.</span></span>
  - <span data-ttu-id="d32cb-p112">Максимальное количество символов для атрибута **userPrincipalName**: 113. Перед знаком (@) и после него допускается определенное количество символов, а именно:</span><span class="sxs-lookup"><span data-stu-id="d32cb-p112">The maximum number of characters for the **userPrincipalName** attribute is 113. A specific number of characters are permitted before and after the at sign (@), as follows:</span></span> 
  - <span data-ttu-id="d32cb-197">Максимальное количество символов для имени пользователя, которое находится перед знаком (@): 64</span><span class="sxs-lookup"><span data-stu-id="d32cb-197">Maximum number of characters for the user name that is in front of the at sign (@): 64</span></span>
  - <span data-ttu-id="d32cb-198">Максимальное количество символов для имени домена, которое находится после знака (@): 48</span><span class="sxs-lookup"><span data-stu-id="d32cb-198">Maximum number of characters for the domain name following the at sign (@): 48</span></span>
  - <span data-ttu-id="d32cb-p113">НеДопустимые символы: &amp; \* \% +/=? { } | \< \> ( ) ; : , [ ] "</span><span class="sxs-lookup"><span data-stu-id="d32cb-p113">Invalid characters: \ % &amp; \* + / = ? { } | \< \> ( ) ; : , [ ] "</span></span>
  - <span data-ttu-id="d32cb-201">Умлаут также является недопустимым символом.</span><span class="sxs-lookup"><span data-stu-id="d32cb-201">An umlaut is also an invalid character.</span></span>
  - <span data-ttu-id="d32cb-202">В каждом значении **userPrincipalName** необходимо указать символ @.</span><span class="sxs-lookup"><span data-stu-id="d32cb-202">The @ character is required in each **userPrincipalName** value.</span></span> 
  - <span data-ttu-id="d32cb-203">Символ "@" не может быть первым символом в каждом значении **userPrincipalName**.</span><span class="sxs-lookup"><span data-stu-id="d32cb-203">The @ character cannot be the first character in each **userPrincipalName** value.</span></span> 
  - <span data-ttu-id="d32cb-204">Имя пользователя не может заканчиваться точкой (.), амперсандом (&amp;), пробелом или знаком "@".</span><span class="sxs-lookup"><span data-stu-id="d32cb-204">The user name cannot end with a period (.), an ampersand (&amp;), a space, or an at sign (@).</span></span>
  - <span data-ttu-id="d32cb-205">Имя пользователя не может содержать пробелы.</span><span class="sxs-lookup"><span data-stu-id="d32cb-205">The user name cannot contain any spaces.</span></span>
  - <span data-ttu-id="d32cb-206">Необходимо использовать маршрутизируемые домены; Например, нельзя использовать локальные или внутренние домены.</span><span class="sxs-lookup"><span data-stu-id="d32cb-206">Routable domains must be used; for example, local or internal domains cannot be used.</span></span>
  - <span data-ttu-id="d32cb-207">Символы кодировки Юникод преобразуются в символы подчеркивания.</span><span class="sxs-lookup"><span data-stu-id="d32cb-207">Unicode is converted to underscore characters.</span></span>
  - <span data-ttu-id="d32cb-208">**userPrincipalName** не может содержать дублирующиеся значения в каталоге.</span><span class="sxs-lookup"><span data-stu-id="d32cb-208">**userPrincipalName** cannot contain any duplicate values in the directory.</span></span> 
    
## <a name="prepare-the-userprincipalname-attribute"></a><span data-ttu-id="d32cb-209">Подготовка атрибута userPrincipalName</span><span class="sxs-lookup"><span data-stu-id="d32cb-209">Prepare the userPrincipalName attribute</span></span>

<span data-ttu-id="d32cb-p114">Служба Active Directory позволяет конечным пользователям в Организации входить в каталог с помощью **SamAccountName** или **userPrincipalName**. Аналогичным образом пользователи могут войти в Office 365 с помощью имени участника-пользователя (UPN) своей рабочей или учебной учетной записи. Синхронизация службы каталогов пытается создать новых пользователей в Azure Active Directory с использованием того же имени участника-пользователя, что и в локальном каталоге. ИМЯ участника-пользователя отформатировано как адрес электронной почты.</span><span class="sxs-lookup"><span data-stu-id="d32cb-p114">Active Directory is designed to allow the end users in your organization to sign in to your directory by using either **sAMAccountName** or **userPrincipalName**. Similarly, end users can sign in to Office 365 by using the user principal name (UPN) of their work or school account. Directory synchronization attempts to create new users in Azure Active Directory by using the same UPN that's in your on-premises directory. The UPN is formatted like an email address.</span></span> 

<span data-ttu-id="d32cb-p115">В Office 365 UPN является атрибутом по умолчанию, который используется для создания адреса электронной почты. Вы можете легко получить **userPrincipalName** (в локальной среде и в Azure Active Directory), а основной адрес электронной почты в **proxyAddresses** задан с разными значениями. Если заданы разные значения, могут быть неудобства для администраторов и конечных пользователей.</span><span class="sxs-lookup"><span data-stu-id="d32cb-p115">In Office 365, the UPN is the default attribute that's used to generate the email address. It's easy to get **userPrincipalName** (on-premises and in Azure Active Directory) and the primary email address in **proxyAddresses** set to different values. When they are set to different values, there can be confusion for administrators and end users.</span></span> 
  
<span data-ttu-id="d32cb-p116">Лучше всего выравнивать эти атрибуты, чтобы избежать путаницы. Чтобы удовлетворить требования единого входа с помощью служб федерации Active Directory (AD FS) 2,0, необходимо убедиться, что имена участников-пользователей в Azure Active Directory и в локальной службе Active Directory совпадают и используют допустимое пространство имен доменов.</span><span class="sxs-lookup"><span data-stu-id="d32cb-p116">It's best to align these attributes to reduce confusion. To meet the requirements of single sign-on with Active Directory Federation Services (AD FS) 2.0, you need to ensure that the UPNs in Azure Active Directory and your on-premises Active Directory match and are using a valid domain namespace.</span></span>
  
## <a name="add-an-alternative-upn-suffix-to-ad-ds"></a><span data-ttu-id="d32cb-219">Добавление альтернативного суффикса имени участника-пользователя в доменные службы Active Directory</span><span class="sxs-lookup"><span data-stu-id="d32cb-219">Add an alternative UPN suffix to AD DS</span></span>

<span data-ttu-id="d32cb-p117">Может потребоваться добавить альтернативный суффикс имени участника-пользователя для связи учетных данных организации пользователя с средой Office 365. Суффикс UPN — это часть имени участника-пользователя справа от знака @. Имена участников, используемые для единого входа, могут содержать буквы, цифры, точки, тире и символы подчеркивания, но не другие типы символов.</span><span class="sxs-lookup"><span data-stu-id="d32cb-p117">You may need to add an alternative UPN suffix to associate the user's corporate credentials with the Office 365 environment. A UPN suffix is the part of a UPN to the right of the @ character. UPNs that are used for single sign-on can contain letters, numbers, periods, dashes, and underscores, but no other types of characters.</span></span>
  
<span data-ttu-id="d32cb-223">Дополнительные сведения о том, как добавить альтернативный суффикс UPN в Active Directory, можно найти в статье [Подготовка к синхронизации службы каталогов]( https://go.microsoft.com/fwlink/p/?LinkId=525430).</span><span class="sxs-lookup"><span data-stu-id="d32cb-223">For more information on how to add an alternative UPN suffix to Active Directory, see [Prepare for directory synchronization]( https://go.microsoft.com/fwlink/p/?LinkId=525430).</span></span>
  
## <a name="match-the-on-premises-upn-with-the-office-365-upn"></a><span data-ttu-id="d32cb-224">Сравнение локального имени участника-пользователя с именем участника-пользователя Office 365</span><span class="sxs-lookup"><span data-stu-id="d32cb-224">Match the on-premises UPN with the Office 365 UPN</span></span>

<span data-ttu-id="d32cb-p118">Если вы уже настроили синхронизацию службы каталогов, имя участника-пользователя для Office 365 может отличаться от локального имени участника-пользователя, определенного в локальной службе каталогов. Это может произойти, если пользователю была назначена лицензия, прежде чем домен был проверен. Чтобы устранить эту проблему, используйте [PowerShell для исправления повторяющегося имени участника](https://go.microsoft.com/fwlink/p/?LinkId=396730) -пользователя и обновления имени участника-пользователя Office 365, чтобы убедиться, что имя участника-пользователя Office совпадает с корпоративным именем пользователя и доменом. Если вы обновляете имя участника-пользователя в локальной службе каталогов и хотите, чтобы он выполнял синхронизацию с удостоверением Azure Active Directory, необходимо удалить лицензию пользователя в Office 365 перед внесением изменений в локальную систему.</span><span class="sxs-lookup"><span data-stu-id="d32cb-p118">If you've already set up directory synchronization, the user's UPN for Office 365 may not match the user's on-premises UPN that's defined in your on-premises directory service. This can occur when a user was assigned a license before the domain was verified. To fix this, use [PowerShell to fix duplicate UPN](https://go.microsoft.com/fwlink/p/?LinkId=396730) to update the user's UPN to ensure that the Office 365 UPN matches the corporate user name and domain. If you are updating the UPN in the on-premises directory service and would like it to synchronize with the Azure Active Directory identity, you need to remove the user's license in Office 365 prior to making the changes on-premises.</span></span> 
  
<span data-ttu-id="d32cb-229">Сведения [о подготовке домена без поддержки маршрутизации (например, локального домена) для синхронизации службы каталогов](prepare-a-non-routable-domain-for-directory-synchronization.md).</span><span class="sxs-lookup"><span data-stu-id="d32cb-229">See also [How to prepare a non-routable domain (such as .local domain) for directory synchronization](prepare-a-non-routable-domain-for-directory-synchronization.md).</span></span>
  
## <a name="directory-integration-tools"></a><span data-ttu-id="d32cb-230">Средства интеграции каталогов</span><span class="sxs-lookup"><span data-stu-id="d32cb-230">Directory integration tools</span></span>

<span data-ttu-id="d32cb-p119">Синхронизация службы каталогов — это синхронизация объектов каталогов (пользователей, групп и контактов) из локальной среды Active Directory в инфраструктуру каталогов Office 365, Azure Active Directory. Список доступных инструментов и их функциональных возможностей можно найти в разделе [средства интеграции каталогов](https://go.microsoft.com/fwlink/p/?LinkID=510956) . Рекомендуемое средство — [Microsoft Azure Active Directory Connect](https://go.microsoft.com/fwlink/p/?LinkID=510956). Для получения дополнительных сведений об Azure Active Directory Connect, ознакомьтесь со статьей [интеграция локальных удостоверений с Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=527969).</span><span class="sxs-lookup"><span data-stu-id="d32cb-p119">Directory synchronization is the synchronization of directory objects (users, groups, and contacts) from your on-premises Active Directory environment to the Office 365 directory infrastructure, Azure Active Directory. See [Directory Integration Tools](https://go.microsoft.com/fwlink/p/?LinkID=510956) for a list of the available tools and their functionality. The recommended tool is [Microsoft Azure Active Directory Connect](https://go.microsoft.com/fwlink/p/?LinkID=510956). For more information about Azure Active Directory Connect, see [Integrating your on-premises identities with Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=527969).</span></span>
  
<span data-ttu-id="d32cb-p120">Когда учетные записи пользователей в первый раз синхронизируются с каталогом Office 365, они помечаются как неактивированные. Они не могут отправлять и получать сообщения электронной почты и не потребляют лицензии на подписку. Когда вы будете готовы назначить подписки на Office 365 определенным пользователям, необходимо выбрать и активировать их, наЗначая [пользователям лицензии на office 365 для бизнеса](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc).</span><span class="sxs-lookup"><span data-stu-id="d32cb-p120">When user accounts are synchronized with the Office 365 directory for the first time, they are marked as not activated. They cannot send or receive email, and they don't consume subscription licenses. When you're ready to assign Office 365 subscriptions to specific users, you must select and activate them by [Assign licenses to users in Office 365 for business](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc).</span></span>
  
<span data-ttu-id="d32cb-p121">Вы также можете назначить лицензии с помощью [PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=613097) . Узнайте, [как использовать PowerShell для автоматического назначения лицензий пользователям Office 365](https://go.microsoft.com/fwlink/p?LinkID=329805) для автоматизированного решения.</span><span class="sxs-lookup"><span data-stu-id="d32cb-p121">You can also use [PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=613097) to assign licenses. See [How to Use PowerShell to Automatically Assign Licenses to Your Office 365 Users](https://go.microsoft.com/fwlink/p?LinkID=329805) for an automated solution.</span></span>