---
title: Подготовка к синхронизации каталогов в Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/25/2019
audience: Admin
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
ms.openlocfilehash: adae292f4dc8ef0402c3bd51391d020af0c28649
ms.sourcegitcommit: a73518764b97948219e378d7014ada5654146be4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/25/2019
ms.locfileid: "39250515"
---
# <a name="prepare-for-directory-synchronization-to-office-365"></a><span data-ttu-id="05cc0-103">Подготовка к синхронизации каталогов в Office 365</span><span class="sxs-lookup"><span data-stu-id="05cc0-103">Prepare for directory synchronization to Office 365</span></span>

<span data-ttu-id="05cc0-104">Преимущества для гибридных удостоверений и синхронизации каталогов в Организации включают:</span><span class="sxs-lookup"><span data-stu-id="05cc0-104">The benefits to hybrid identity and directory synchronization your organization include:</span></span>
  
- <span data-ttu-id="05cc0-105">Сокращение количества программ администрирования в Организации</span><span class="sxs-lookup"><span data-stu-id="05cc0-105">Reducing the administrative programs in your organization</span></span>
- <span data-ttu-id="05cc0-106">Необязательное включение сценария единого входа</span><span class="sxs-lookup"><span data-stu-id="05cc0-106">Optionally enabling single sign-on scenario</span></span>
- <span data-ttu-id="05cc0-107">Автоматизация изменений учетных записей в Office 365</span><span class="sxs-lookup"><span data-stu-id="05cc0-107">Automating account changes in Office 365</span></span>
    
<span data-ttu-id="05cc0-108">Более подробную информацию о преимуществах синхронизации службы каталогов можно узнать в статье [схема синхронизации каталогов]( https://go.microsoft.com/fwlink/p/?LinkId=525398) и [гибридное удостоверение для Office 365](plan-for-directory-synchronization.md).</span><span class="sxs-lookup"><span data-stu-id="05cc0-108">For more information about the advantages of using directory synchronization, see [Directory synchronization roadmap]( https://go.microsoft.com/fwlink/p/?LinkId=525398) and [Hybrid identity for Office 365](plan-for-directory-synchronization.md).</span></span>

<span data-ttu-id="05cc0-109">Однако для синхронизации каталогов требуется планирование и подготовка к синхронизации доменных служб Active Directory (AD DS) с клиентом Azure Active Directory (Azure AD) для подписки на Office 365 с минимальными ошибками.</span><span class="sxs-lookup"><span data-stu-id="05cc0-109">However, directory synchronization requires planning and preparation to ensure that your Active Directory Domain Services (AD DS) synchronizes to the Azure Active Directory (Azure AD) tenant of your Office 365 subscription with a minimum of errors.</span></span> 

<span data-ttu-id="05cc0-110">Чтобы получить наилучшие результаты, выполните указанные ниже действия.</span><span class="sxs-lookup"><span data-stu-id="05cc0-110">Follow these steps in order for the best results.</span></span>
  
## <a name="1-directory-cleanup-tasks"></a><span data-ttu-id="05cc0-111">1. задачи очистки каталога</span><span class="sxs-lookup"><span data-stu-id="05cc0-111">1. Directory cleanup tasks</span></span>

<span data-ttu-id="05cc0-112">Перед синхронизацией доменных служб Active Directory с клиентом Azure AD необходимо очистить службу AD DS.</span><span class="sxs-lookup"><span data-stu-id="05cc0-112">Before you synchronize your AD DS to your Azure AD tenant, you need to clean up your AD DS.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="05cc0-113">Если вы не выполняете очистку доменных служб Active Directory перед синхронизацией, это может значительно негативно сказаться на процессе развертывания.</span><span class="sxs-lookup"><span data-stu-id="05cc0-113">If you don't perform AD DS cleanup before you synchronize, there can be a significant negative effect on the deployment process.</span></span> <span data-ttu-id="05cc0-114">Может потребоваться несколько дней или даже недель, чтобы пройти цикл синхронизации службы каталогов, выявить ошибки и повторную синхронизацию.</span><span class="sxs-lookup"><span data-stu-id="05cc0-114">It might take days, or even weeks, to go through the cycle of directory synchronization, identifying errors, and re-synchronization.</span></span> 
  
<span data-ttu-id="05cc0-115">В доменных службах Active Directory выполните следующие задачи очистки для каждой учетной записи пользователя, которой будет назначена лицензия на Office 365:</span><span class="sxs-lookup"><span data-stu-id="05cc0-115">In your AD DS, complete the following clean-up tasks for each user account that will be assigned an Office 365 license:</span></span>
  
1. <span data-ttu-id="05cc0-116">Убедитесь, что в атрибуте **proxyAddresses** допустимый и уникальный адрес электронной почты.</span><span class="sxs-lookup"><span data-stu-id="05cc0-116">Ensure a valid and unique email address in the **proxyAddresses** attribute.</span></span> 

  >[!Note]
  ><span data-ttu-id="05cc0-117">Символ тильды (~) в адресах электронной почты будет игнорироваться.</span><span class="sxs-lookup"><span data-stu-id="05cc0-117">A tilde (~) character in email addresses will be ignored.</span></span> <span data-ttu-id="05cc0-118">Это может приводить к ложным ошибкам синхронизации каталогов при дублировании proxyAddresses.</span><span class="sxs-lookup"><span data-stu-id="05cc0-118">This can lead to false-positive directory synchronization errors about duplicate proxyAddresses.</span></span>
    
2. <span data-ttu-id="05cc0-119">Удалите все повторяющиеся значения в атрибуте **proxyAddresses** .</span><span class="sxs-lookup"><span data-stu-id="05cc0-119">Remove any duplicate values in the **proxyAddresses** attribute.</span></span> 
    
3.  <span data-ttu-id="05cc0-120">Если это возможно, убедитесь, что допустимое и уникальное значение атрибута **userPrincipalName** в объекте **пользователя** пользователя.</span><span class="sxs-lookup"><span data-stu-id="05cc0-120">If possible, ensure a valid and unique value for the **userPrincipalName** attribute in the user's **user** object.</span></span> <span data-ttu-id="05cc0-121">Для достижения наилучшего качества синхронизации убедитесь, что имя участника-службы доменных служб Active Directory соответствует имени участника-пользователя Azure AD.</span><span class="sxs-lookup"><span data-stu-id="05cc0-121">For the best synchronization experience, ensure that the AD DS UPN matches the Azure AD UPN.</span></span> <span data-ttu-id="05cc0-122">Если у пользователя нет значения атрибута **userPrincipalName** , то объект **пользователя** должен содержать допустимое и уникальное значение для атрибута **SamAccountName** .</span><span class="sxs-lookup"><span data-stu-id="05cc0-122">If a user does not have a value for the **userPrincipalName** attribute, then the **user** object must contain a valid and unique value for the **sAMAccountName** attribute.</span></span> <span data-ttu-id="05cc0-123">Удалите все повторяющиеся значения в атрибуте **userPrincipalName** .</span><span class="sxs-lookup"><span data-stu-id="05cc0-123">Remove any duplicate values in the **userPrincipalName** attribute.</span></span> 
    
4. <span data-ttu-id="05cc0-124">Для оптимального использования глобального списка адресов (GAL) необходимо убедиться в правильности сведений в следующих атрибутах учетной записи пользователя доменных служб Active Directory:</span><span class="sxs-lookup"><span data-stu-id="05cc0-124">For optimal use of the global address list (GAL), ensure the information in the following attributes of the AD DS user account is correct:</span></span>
    
  - <span data-ttu-id="05cc0-125">givenName;</span><span class="sxs-lookup"><span data-stu-id="05cc0-125">givenName</span></span>
  - <span data-ttu-id="05cc0-126">surname</span><span class="sxs-lookup"><span data-stu-id="05cc0-126">surname</span></span>
  - <span data-ttu-id="05cc0-127">displayName</span><span class="sxs-lookup"><span data-stu-id="05cc0-127">displayName</span></span>
  - <span data-ttu-id="05cc0-128">должность;</span><span class="sxs-lookup"><span data-stu-id="05cc0-128">Job Title</span></span>
  - <span data-ttu-id="05cc0-129">Отдел</span><span class="sxs-lookup"><span data-stu-id="05cc0-129">Department</span></span>
  - <span data-ttu-id="05cc0-130">Кабинет</span><span class="sxs-lookup"><span data-stu-id="05cc0-130">Office</span></span>
  - <span data-ttu-id="05cc0-131">рабочий телефон;</span><span class="sxs-lookup"><span data-stu-id="05cc0-131">Office Phone</span></span>
  - <span data-ttu-id="05cc0-132">мобильный телефон;</span><span class="sxs-lookup"><span data-stu-id="05cc0-132">Mobile Phone</span></span>
  - <span data-ttu-id="05cc0-133">номер факса;</span><span class="sxs-lookup"><span data-stu-id="05cc0-133">Fax Number</span></span>
  - <span data-ttu-id="05cc0-134">адрес;</span><span class="sxs-lookup"><span data-stu-id="05cc0-134">Street Address</span></span>
  - <span data-ttu-id="05cc0-135">Город</span><span class="sxs-lookup"><span data-stu-id="05cc0-135">City</span></span>
  - <span data-ttu-id="05cc0-136">регион или область;</span><span class="sxs-lookup"><span data-stu-id="05cc0-136">State or Province</span></span>
  - <span data-ttu-id="05cc0-137">почтовый индекс;</span><span class="sxs-lookup"><span data-stu-id="05cc0-137">Zip or Postal Code</span></span>
  - <span data-ttu-id="05cc0-138">страна или регион.</span><span class="sxs-lookup"><span data-stu-id="05cc0-138">Country or Region</span></span>
    
## <a name="2-directory-object-and-attribute-preparation"></a><span data-ttu-id="05cc0-139">2. Подготовка объекта каталога и атрибута</span><span class="sxs-lookup"><span data-stu-id="05cc0-139">2. Directory object and attribute preparation</span></span>

<span data-ttu-id="05cc0-140">Для успешной синхронизации каталогов между доменными службами Active Directory и Office 365 необходимо, чтобы атрибуты доменных служб Active Directory были правильно подготовлены.</span><span class="sxs-lookup"><span data-stu-id="05cc0-140">Successful directory synchronization between your AD DS and Office 365 requires that your AD DS attributes are properly prepared.</span></span> <span data-ttu-id="05cc0-141">Например, необходимо убедиться, что определенные символы не используются в определенных атрибутах, которые синхронизируются с средой Office 365.</span><span class="sxs-lookup"><span data-stu-id="05cc0-141">For example, you need to ensure that specific characters aren't used in certain attributes that are synchronized with the Office 365 environment.</span></span> <span data-ttu-id="05cc0-142">Непредусмотренные символы не приводят к сбою синхронизации службы каталогов, но могут возвращать предупреждение.</span><span class="sxs-lookup"><span data-stu-id="05cc0-142">Unexpected characters do not cause directory synchronization to fail but might return a warning.</span></span> <span data-ttu-id="05cc0-143">Недопустимые символы приведут к сбою синхронизации службы каталогов.</span><span class="sxs-lookup"><span data-stu-id="05cc0-143">Invalid characters will cause directory synchronization to fail.</span></span>
  
<span data-ttu-id="05cc0-144">Синхронизация службы каталогов также завершится с ошибками, если некоторые пользователи доменных служб Active Directory имеют один или несколько повторяющихся атрибутов.</span><span class="sxs-lookup"><span data-stu-id="05cc0-144">Directory synchronization will also fail if some of your AD DS users have one or more duplicate attributes.</span></span> <span data-ttu-id="05cc0-145">Каждый пользователь должен иметь уникальные атрибуты.</span><span class="sxs-lookup"><span data-stu-id="05cc0-145">Each user must have unique attributes.</span></span>
  
<span data-ttu-id="05cc0-146">Ниже перечислены атрибуты, которые необходимо подготовить.</span><span class="sxs-lookup"><span data-stu-id="05cc0-146">The attributes that you need to prepare are listed here:</span></span>
  
- <span data-ttu-id="05cc0-147">**displayName**</span><span class="sxs-lookup"><span data-stu-id="05cc0-147">**displayName**</span></span>
    
  - <span data-ttu-id="05cc0-148">Если атрибут существует в объекте пользователя, он будет синхронизирован с Office 365.</span><span class="sxs-lookup"><span data-stu-id="05cc0-148">If the attribute exists in the user object, it will be synchronized with Office 365.</span></span>
  - <span data-ttu-id="05cc0-149">Если этот атрибут существует в объекте пользователя, для него должно быть задано значение.</span><span class="sxs-lookup"><span data-stu-id="05cc0-149">If this attribute exists in the user object, there must be a value for it.</span></span> <span data-ttu-id="05cc0-150">То есть атрибут не должен быть пустым.</span><span class="sxs-lookup"><span data-stu-id="05cc0-150">That is, the attribute must not be blank.</span></span>
  - <span data-ttu-id="05cc0-151">Максимальное число символов: 256</span><span class="sxs-lookup"><span data-stu-id="05cc0-151">Maximum number of characters: 256</span></span>
    
- <span data-ttu-id="05cc0-152">**givenName;**</span><span class="sxs-lookup"><span data-stu-id="05cc0-152">**givenName**</span></span>
    
  - <span data-ttu-id="05cc0-153">Если атрибут существует в объекте пользователя, он будет синхронизирован с Office 365, но Office 365 не требует и не использует его.</span><span class="sxs-lookup"><span data-stu-id="05cc0-153">If the attribute exists in the user object, it will be synchronized with Office 365, but Office 365 does not require or use it.</span></span>
  - <span data-ttu-id="05cc0-154">Максимальное число символов: 64</span><span class="sxs-lookup"><span data-stu-id="05cc0-154">Maximum number of characters: 64</span></span>
    
- <span data-ttu-id="05cc0-155">**mail**</span><span class="sxs-lookup"><span data-stu-id="05cc0-155">**mail**</span></span>
    
  - <span data-ttu-id="05cc0-156">Значение атрибута должно быть уникальным в пределах каталога.</span><span class="sxs-lookup"><span data-stu-id="05cc0-156">The attribute value must be unique within the directory.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="05cc0-157">Если имеются повторяющиеся значения, первый пользователь со значением синхронизируется.</span><span class="sxs-lookup"><span data-stu-id="05cc0-157">If there are duplicate values, the first user with the value is synchronized.</span></span> <span data-ttu-id="05cc0-158">Последующие пользователи не будут отображаться в Office 365.</span><span class="sxs-lookup"><span data-stu-id="05cc0-158">Subsequent users will not appear in Office 365.</span></span> <span data-ttu-id="05cc0-159">Необходимо изменить значение в Office 365 или изменить оба значения в доменных СЛУЖБах Active Directory, чтобы оба пользователя отображались в Office 365.</span><span class="sxs-lookup"><span data-stu-id="05cc0-159">You must modify either the value in Office 365 or modify both of the values in AD DS in order for both users to appear in Office 365.</span></span> 
  
- <span data-ttu-id="05cc0-160">**mailNickname** (псевдоним Exchange)</span><span class="sxs-lookup"><span data-stu-id="05cc0-160">**mailNickname** (Exchange alias)</span></span> 
    
  - <span data-ttu-id="05cc0-161">Значение атрибута не может начинаться с точки (.).</span><span class="sxs-lookup"><span data-stu-id="05cc0-161">The attribute value cannot begin with a period (.).</span></span>
  - <span data-ttu-id="05cc0-162">Значение атрибута должно быть уникальным в пределах каталога.</span><span class="sxs-lookup"><span data-stu-id="05cc0-162">The attribute value must be unique within the directory.</span></span>
  
    > [!NOTE]
    > <span data-ttu-id="05cc0-163">Символ подчеркивания ("_") в синхронизированном имени указывает на то, что исходное значение этого атрибута содержит недопустимые символы.</span><span class="sxs-lookup"><span data-stu-id="05cc0-163">Underscores ("_") in the synchronized name indicates that the original value of this attribute contains invalid characters.</span></span> <span data-ttu-id="05cc0-164">Исходное значение может содержать буквы, цифры, а также символы!, #, $,%, &, ', \*, +,-,/, =,?, ^, _, ', {, |,} и ~.</span><span class="sxs-lookup"><span data-stu-id="05cc0-164">The original value can contain letters, numbers, and the characters !, #, $, %, &, ', \*, +, -, /, =, ?, ^, _, \`, {, |, } and ~.</span></span> <span data-ttu-id="05cc0-165">Дополнительные сведения об этом атрибуте приведены в разделе [атрибут псевдонима Exchange](https://docs.microsoft.com/powershell/module/exchange/mailboxes/set-mailbox?view=exchange-ps).</span><span class="sxs-lookup"><span data-stu-id="05cc0-165">For more information on this attribute, see [Exchange alias attribute](https://docs.microsoft.com/powershell/module/exchange/mailboxes/set-mailbox?view=exchange-ps).</span></span>
    >
      
- <span data-ttu-id="05cc0-166">**proxyAddresses**</span><span class="sxs-lookup"><span data-stu-id="05cc0-166">**proxyAddresses**</span></span>
    
  - <span data-ttu-id="05cc0-167">Атрибут с несколькими значениями</span><span class="sxs-lookup"><span data-stu-id="05cc0-167">Multiple-value attribute</span></span>
  - <span data-ttu-id="05cc0-168">Максимальное число символов на значение: 256</span><span class="sxs-lookup"><span data-stu-id="05cc0-168">Maximum number of characters per value: 256</span></span>
  - <span data-ttu-id="05cc0-169">Значение атрибута не должно содержать пробел.</span><span class="sxs-lookup"><span data-stu-id="05cc0-169">The attribute value must not contain a space.</span></span>
  - <span data-ttu-id="05cc0-170">Значение атрибута должно быть уникальным в пределах каталога.</span><span class="sxs-lookup"><span data-stu-id="05cc0-170">The attribute value must be unique within the directory.</span></span>
  - <span data-ttu-id="05cc0-171">Недопустимые \< \> символы: (); , [ ] " '</span><span class="sxs-lookup"><span data-stu-id="05cc0-171">Invalid characters: \< \> ( ) ; , [ ] " '</span></span>
    
    <span data-ttu-id="05cc0-172">Обратите внимание, что недопустимые символы применяются к символам, которые следует за разделителем типов и ":", так как SMTP:User@contso.com разрешен, а SMTP:user:M@contoso.com — нет.</span><span class="sxs-lookup"><span data-stu-id="05cc0-172">Note that the invalid characters apply to the characters following the type delimiter and ":", such that SMTP:User@contso.com is allowed, but SMTP:user:M@contoso.com is not.</span></span>
    
    > [!IMPORTANT]
    > <span data-ttu-id="05cc0-173">Все SMTP-адреса должны соответствовать стандартам обмена сообщениями электронной почты.</span><span class="sxs-lookup"><span data-stu-id="05cc0-173">All Simple Mail Transport Protocol (SMTP) addresses should comply with email messaging standards.</span></span> <span data-ttu-id="05cc0-174">Если имеются повторяющиеся или нежелательные адреса, ознакомьтесь с разделом справки [Удаление повторяющихся и нежелательных прокси-адресов в Exchange](https://go.microsoft.com/fwlink/?LinkId=293860).</span><span class="sxs-lookup"><span data-stu-id="05cc0-174">If duplicate or unwanted addresses exist, see the Help topic [Removing duplicate and unwanted proxy addresses in Exchange](https://go.microsoft.com/fwlink/?LinkId=293860).</span></span> 
  
- <span data-ttu-id="05cc0-175">**sAMAccountName**</span><span class="sxs-lookup"><span data-stu-id="05cc0-175">**sAMAccountName**</span></span>
    
  - <span data-ttu-id="05cc0-176">Максимальное число символов: 20</span><span class="sxs-lookup"><span data-stu-id="05cc0-176">Maximum number of characters: 20</span></span>
  - <span data-ttu-id="05cc0-177">Значение атрибута должно быть уникальным в пределах каталога.</span><span class="sxs-lookup"><span data-stu-id="05cc0-177">The attribute value must be unique within the directory.</span></span>
  - <span data-ttu-id="05cc0-178">Недопустимые символы: [\ "|, \< \> /: + =;?</span><span class="sxs-lookup"><span data-stu-id="05cc0-178">Invalid characters: [ \ " | , / : \< \> + = ; ?</span></span> <span data-ttu-id="05cc0-179">\* ']</span><span class="sxs-lookup"><span data-stu-id="05cc0-179"></span></span>
  - <span data-ttu-id="05cc0-180">Если пользователь имеет недопустимый атрибут **SamAccountName** , но имеет допустимый атрибут **userPrincipalName** , учетная запись пользователя создается в Office 365.</span><span class="sxs-lookup"><span data-stu-id="05cc0-180">If a user has an invalid **sAMAccountName** attribute but has a valid **userPrincipalName** attribute, the user account is created in Office 365.</span></span> 
  - <span data-ttu-id="05cc0-181">Если и **SamAccountName** , и **userPrincipalName** являются недопустимыми, необходимо обновить атрибут **userPrincipalName** доменных служб Active Directory.</span><span class="sxs-lookup"><span data-stu-id="05cc0-181">If both **sAMAccountName** and **userPrincipalName** are invalid, the AD DS **userPrincipalName** attribute must be updated.</span></span> 
    
- <span data-ttu-id="05cc0-182">**СН** (фамилия)</span><span class="sxs-lookup"><span data-stu-id="05cc0-182">**sn** (surname)</span></span> 
    
  - <span data-ttu-id="05cc0-183">Если атрибут существует в объекте пользователя, он будет синхронизирован с Office 365, но Office 365 не требует и не использует его.</span><span class="sxs-lookup"><span data-stu-id="05cc0-183">If the attribute exists in the user object, it will be synchronized with Office 365, but Office 365 does not require or use it.</span></span>
    
- <span data-ttu-id="05cc0-184">**targetAddress**</span><span class="sxs-lookup"><span data-stu-id="05cc0-184">**targetAddress**</span></span>
    
    <span data-ttu-id="05cc0-185">Необходимо, чтобы атрибут **targetAddress** (например, SMTP:Tom@contoso.com), заполненный для пользователя, отображался в глобальном списке адресов Office 365.</span><span class="sxs-lookup"><span data-stu-id="05cc0-185">It's required that the **targetAddress** attribute (for example, SMTP:tom@contoso.com) that's populated for the user must appear in the Office 365 GAL.</span></span> <span data-ttu-id="05cc0-186">В сценариях миграции сторонних производителей потребуется расширение схемы Office 365 для AD DS.</span><span class="sxs-lookup"><span data-stu-id="05cc0-186">In third-party messaging migration scenarios, this would require the Office 365 schema extension for the AD DS.</span></span> <span data-ttu-id="05cc0-187">Расширение схемы Office 365 также будет добавлять другие атрибуты для управления объектами Office 365, заполненными с помощью средства синхронизации каталогов из доменных служб Active Directory.</span><span class="sxs-lookup"><span data-stu-id="05cc0-187">The Office 365 schema extension would also add other useful attributes to manage Office 365 objects that are populated by using a directory synchronization tool from AD DS.</span></span> <span data-ttu-id="05cc0-188">Например, вы добавите атрибут **msExchHideFromAddressLists** для управления скрытыми почтовыми ящиками или группами рассылки.</span><span class="sxs-lookup"><span data-stu-id="05cc0-188">For example, the **msExchHideFromAddressLists** attribute to manage hidden mailboxes or distribution groups would be added.</span></span> 
   
  - <span data-ttu-id="05cc0-189">Максимальное число символов: 256</span><span class="sxs-lookup"><span data-stu-id="05cc0-189">Maximum number of characters: 256</span></span>
  - <span data-ttu-id="05cc0-190">Значение атрибута не должно содержать пробел.</span><span class="sxs-lookup"><span data-stu-id="05cc0-190">The attribute value must not contain a space.</span></span>
  - <span data-ttu-id="05cc0-191">Значение атрибута должно быть уникальным в пределах каталога.</span><span class="sxs-lookup"><span data-stu-id="05cc0-191">The attribute value must be unique within the directory.</span></span>
  - <span data-ttu-id="05cc0-192">Недопустимые символы \< \> : \ (); , [ ] "</span><span class="sxs-lookup"><span data-stu-id="05cc0-192">Invalid characters: \ \< \> ( ) ; , [ ] "</span></span>
  - <span data-ttu-id="05cc0-193">Все SMTP-адреса должны соответствовать стандартам обмена сообщениями электронной почты.</span><span class="sxs-lookup"><span data-stu-id="05cc0-193">All Simple Mail Transport Protocol (SMTP) addresses should comply with email messaging standards.</span></span>
    
- <span data-ttu-id="05cc0-194">**userPrincipalName**</span><span class="sxs-lookup"><span data-stu-id="05cc0-194">**userPrincipalName**</span></span>
    
  - <span data-ttu-id="05cc0-195">Атрибут **userPrincipalName** должен быть в формате для входа в Интернет, где за именем пользователя следуют знак "@" и доменное имя: например, user@contoso.com.</span><span class="sxs-lookup"><span data-stu-id="05cc0-195">The **userPrincipalName** attribute must be in the Internet-style sign-in format where the user name is followed by the at sign (@) and a domain name: for example, user@contoso.com.</span></span> <span data-ttu-id="05cc0-196">Все SMTP-адреса должны соответствовать стандартам обмена сообщениями электронной почты.</span><span class="sxs-lookup"><span data-stu-id="05cc0-196">All Simple Mail Transport Protocol (SMTP) addresses should comply with email messaging standards.</span></span>
  - <span data-ttu-id="05cc0-197">Максимальное число символов для атрибута **userPrincipalName** — 113.</span><span class="sxs-lookup"><span data-stu-id="05cc0-197">The maximum number of characters for the **userPrincipalName** attribute is 113.</span></span> <span data-ttu-id="05cc0-198">Определенное количество символов допускаются до и после знака "@" (@), как показано ниже.</span><span class="sxs-lookup"><span data-stu-id="05cc0-198">A specific number of characters are permitted before and after the at sign (@), as follows:</span></span> 
  - <span data-ttu-id="05cc0-199">Максимальное число символов для имени пользователя, которое находится перед знаком (@): 64</span><span class="sxs-lookup"><span data-stu-id="05cc0-199">Maximum number of characters for the username that is in front of the at sign (@): 64</span></span>
  - <span data-ttu-id="05cc0-200">Максимальное число символов для доменного имени после знака "@": 48</span><span class="sxs-lookup"><span data-stu-id="05cc0-200">Maximum number of characters for the domain name following the at sign (@): 48</span></span>
  - <span data-ttu-id="05cc0-201">Недопустимые символы: &amp; \* \% +/=?</span><span class="sxs-lookup"><span data-stu-id="05cc0-201">Invalid characters: \ % &amp; \* + / = ?</span></span> <span data-ttu-id="05cc0-202">{ } | \< \> ( ) ; : , [ ] " '</span><span class="sxs-lookup"><span data-stu-id="05cc0-202"></span></span>
  - <span data-ttu-id="05cc0-203">Умлаут также является недопустимым символом.</span><span class="sxs-lookup"><span data-stu-id="05cc0-203">An umlaut is also an invalid character.</span></span>
  - <span data-ttu-id="05cc0-204">В каждом значении **userPrincipalName** необходимо указать символ @.</span><span class="sxs-lookup"><span data-stu-id="05cc0-204">The @ character is required in each **userPrincipalName** value.</span></span> 
  - <span data-ttu-id="05cc0-205">Символ "@" не может быть первым символом в каждом значении **userPrincipalName**.</span><span class="sxs-lookup"><span data-stu-id="05cc0-205">The @ character cannot be the first character in each **userPrincipalName** value.</span></span> 
  - <span data-ttu-id="05cc0-206">Имя пользователя не может заканчиваться точкой (.), амперсандом (&amp;), пробелом или знаком @.</span><span class="sxs-lookup"><span data-stu-id="05cc0-206">The username cannot end with a period (.), an ampersand (&amp;), a space, or an at sign (@).</span></span>
  - <span data-ttu-id="05cc0-207">Имя пользователя не может содержать пробелы.</span><span class="sxs-lookup"><span data-stu-id="05cc0-207">The username cannot contain any spaces.</span></span>
  - <span data-ttu-id="05cc0-208">Необходимо использовать маршрутизируемые домены; Например, нельзя использовать локальные или внутренние домены.</span><span class="sxs-lookup"><span data-stu-id="05cc0-208">Routable domains must be used; for example, local or internal domains cannot be used.</span></span>
  - <span data-ttu-id="05cc0-209">Символы кодировки Юникод преобразуются в символы подчеркивания.</span><span class="sxs-lookup"><span data-stu-id="05cc0-209">Unicode is converted to underscore characters.</span></span>
  - <span data-ttu-id="05cc0-210">**userPrincipalName** не может содержать дублирующиеся значения в каталоге.</span><span class="sxs-lookup"><span data-stu-id="05cc0-210">**userPrincipalName** cannot contain any duplicate values in the directory.</span></span> 

<span data-ttu-id="05cc0-211">Чтобы определить ошибки в атрибутах доменных служб Active Directory, ознакомьтесь со статьей [Подготовка атрибутов каталогов с помощью средства IdFix](prepare-directory-attributes-for-synch-with-idfix.md) , чтобы использовать средство IdFix.</span><span class="sxs-lookup"><span data-stu-id="05cc0-211">See [Prepare directory attributes with the IdFix tool](prepare-directory-attributes-for-synch-with-idfix.md) to use the IdFIx tool to identify errors in the attributes of your AD DS.</span></span>
    
## <a name="3-prepare-the-userprincipalname-attribute"></a><span data-ttu-id="05cc0-212">3. Подготовка атрибута userPrincipalName</span><span class="sxs-lookup"><span data-stu-id="05cc0-212">3. Prepare the userPrincipalName attribute</span></span>

<span data-ttu-id="05cc0-213">Служба Active Directory позволяет конечным пользователям в Организации входить в каталог с помощью **SamAccountName** или **userPrincipalName**.</span><span class="sxs-lookup"><span data-stu-id="05cc0-213">Active Directory is designed to allow the end users in your organization to sign in to your directory by using either **sAMAccountName** or **userPrincipalName**.</span></span> <span data-ttu-id="05cc0-214">Аналогичным образом пользователи могут войти в Office 365 с помощью имени участника-пользователя (UPN) своей рабочей или учебной учетной записи.</span><span class="sxs-lookup"><span data-stu-id="05cc0-214">Similarly, end users can sign in to Office 365 by using the user principal name (UPN) of their work or school account.</span></span> <span data-ttu-id="05cc0-215">Синхронизация службы каталогов пытается создать новых пользователей в Azure Active Directory с использованием того же имени участника-пользователя, что и в доменных СЛУЖБах Active Directory.</span><span class="sxs-lookup"><span data-stu-id="05cc0-215">Directory synchronization attempts to create new users in Azure Active Directory by using the same UPN that's in your AD DS.</span></span> <span data-ttu-id="05cc0-216">Имя участника-пользователя отформатировано как адрес электронной почты.</span><span class="sxs-lookup"><span data-stu-id="05cc0-216">The UPN is formatted like an email address.</span></span> 

<span data-ttu-id="05cc0-217">В Office 365 UPN является атрибутом по умолчанию, который используется для создания адреса электронной почты.</span><span class="sxs-lookup"><span data-stu-id="05cc0-217">In Office 365, the UPN is the default attribute that's used to generate the email address.</span></span> <span data-ttu-id="05cc0-218">Вы можете легко получить **userPrincipalName** (в AD DS и в Azure AD), а основной адрес электронной почты в **proxyAddresses** задан с разными значениями.</span><span class="sxs-lookup"><span data-stu-id="05cc0-218">It's easy to get **userPrincipalName** (in AD DS and in Azure AD) and the primary email address in **proxyAddresses** set to different values.</span></span> <span data-ttu-id="05cc0-219">Если заданы разные значения, могут быть неудобства для администраторов и конечных пользователей.</span><span class="sxs-lookup"><span data-stu-id="05cc0-219">When they are set to different values, there can be confusion for administrators and end users.</span></span> 
  
<span data-ttu-id="05cc0-220">Лучше всего выравнивать эти атрибуты, чтобы избежать путаницы.</span><span class="sxs-lookup"><span data-stu-id="05cc0-220">It's best to align these attributes to reduce confusion.</span></span> <span data-ttu-id="05cc0-221">Чтобы удовлетворить требования единого входа с помощью служб федерации Active Directory (AD FS) 2,0, необходимо убедиться, что имена участников-пользователей в Azure Active Directory и доменные службы Active Directory совпадают и используют допустимое пространство имен доменов.</span><span class="sxs-lookup"><span data-stu-id="05cc0-221">To meet the requirements of single sign-on with Active Directory Federation Services (AD FS) 2.0, you need to ensure that the UPNs in Azure Active Directory and your AD DS match and are using a valid domain namespace.</span></span>
  
## <a name="4-add-an-alternative-upn-suffix-to-ad-ds"></a><span data-ttu-id="05cc0-222">4. Добавление альтернативного суффикса UPN в доменные службы Active Directory</span><span class="sxs-lookup"><span data-stu-id="05cc0-222">4. Add an alternative UPN suffix to AD DS</span></span>

<span data-ttu-id="05cc0-223">Может потребоваться добавить альтернативный суффикс имени участника-пользователя для связи учетных данных организации пользователя с средой Office 365.</span><span class="sxs-lookup"><span data-stu-id="05cc0-223">You may need to add an alternative UPN suffix to associate the user's corporate credentials with the Office 365 environment.</span></span> <span data-ttu-id="05cc0-224">Суффикс UPN — это часть имени участника-пользователя, расположенная справа от символа @.</span><span class="sxs-lookup"><span data-stu-id="05cc0-224">A UPN suffix is the part of a UPN to the right of the @ character.</span></span> <span data-ttu-id="05cc0-225">UPN-имена, которые используются для единого входа, могут содержать буквы, цифры, точки, дефисы и подчеркивания, другие символы запрещены.</span><span class="sxs-lookup"><span data-stu-id="05cc0-225">UPNs that are used for single sign-on can contain letters, numbers, periods, dashes, and underscores, but no other types of characters.</span></span>
  
<span data-ttu-id="05cc0-226">Дополнительные сведения о том, как добавить альтернативный суффикс UPN в Active Directory, можно найти в статье [Подготовка к синхронизации службы каталогов]( https://go.microsoft.com/fwlink/p/?LinkId=525430).</span><span class="sxs-lookup"><span data-stu-id="05cc0-226">For more information on how to add an alternative UPN suffix to Active Directory, see [Prepare for directory synchronization]( https://go.microsoft.com/fwlink/p/?LinkId=525430).</span></span>
  
## <a name="5-match-the-ad-ds-upn-with-the-office-365-upn"></a><span data-ttu-id="05cc0-227">5. Сопоставьте имя участника-службы доменных служб Active Directory с именем участника-пользователя Office 365.</span><span class="sxs-lookup"><span data-stu-id="05cc0-227">5. Match the AD DS UPN with the Office 365 UPN</span></span>

<span data-ttu-id="05cc0-228">Если вы уже настроили синхронизацию службы каталогов, имя участника-пользователя для Office 365 может отличаться от имени участника-пользователя доменных служб Active Directory AD, которое определено в доменных службах Active Directory.</span><span class="sxs-lookup"><span data-stu-id="05cc0-228">If you've already set up directory synchronization, the user's UPN for Office 365 may not match the user's AD DS UPN that's defined in your AD DS.</span></span> <span data-ttu-id="05cc0-229">Это может произойти, если пользователю была назначена лицензия до проверки домена.</span><span class="sxs-lookup"><span data-stu-id="05cc0-229">This can occur when a user was assigned a license before the domain was verified.</span></span> <span data-ttu-id="05cc0-230">Чтобы устранить эту проблему, используйте [PowerShell для исправления повторяющегося имени участника](https://go.microsoft.com/fwlink/p/?LinkId=396730) -пользователя и обновления имени участника-пользователя Office 365, чтобы убедиться, что имя участника-пользователя Office совпадает с корпоративным именем пользователя и доменом.</span><span class="sxs-lookup"><span data-stu-id="05cc0-230">To fix this, use [PowerShell to fix duplicate UPN](https://go.microsoft.com/fwlink/p/?LinkId=396730) to update the user's UPN to ensure that the Office 365 UPN matches the corporate user name and domain.</span></span> <span data-ttu-id="05cc0-231">Если вы обновляете имя участника-пользователя в доменных СЛУЖБах Active Directory и хотите, чтобы он выполнял синхронизацию с удостоверением Azure Active Directory, необходимо удалить лицензию пользователя в Office 365 перед внесением изменений в AD DS.</span><span class="sxs-lookup"><span data-stu-id="05cc0-231">If you are updating the UPN in the AD DS and would like it to synchronize with the Azure Active Directory identity, you need to remove the user's license in Office 365 prior to making the changes in AD DS.</span></span> 
  
<span data-ttu-id="05cc0-232">Кроме того, Узнайте [, как подготовить домен, не поддерживающий маршрутизацию (например, локальный домен), для синхронизации службы каталогов](prepare-a-non-routable-domain-for-directory-synchronization.md).</span><span class="sxs-lookup"><span data-stu-id="05cc0-232">Also see [How to prepare a non-routable domain (such as .local domain) for directory synchronization](prepare-a-non-routable-domain-for-directory-synchronization.md).</span></span>


## <a name="next-steps"></a><span data-ttu-id="05cc0-233">Дальнейшие действия</span><span class="sxs-lookup"><span data-stu-id="05cc0-233">Next steps</span></span>

<span data-ttu-id="05cc0-234">Сведения о [подготовке атрибутов каталогов с помощью средства IdFix](prepare-directory-attributes-for-synch-with-idfix.md) помогут исправить ошибки в атрибутах доменных служб Active Directory до синхронизации службы каталогов.</span><span class="sxs-lookup"><span data-stu-id="05cc0-234">See [Prepare directory attributes with the IdFix tool](prepare-directory-attributes-for-synch-with-idfix.md) to help you correct errors in the attributes of your AD DS prior to directory synchronization.</span></span>

<span data-ttu-id="05cc0-235">Если были исправлены все ошибки атрибутов, обнаруженные с помощью средства IdFix, и выполнить действия с 1 по 5, ознакомьтесь с разделом [Настройка синхронизации службы каталогов](set-up-directory-synchronization.md).</span><span class="sxs-lookup"><span data-stu-id="05cc0-235">If you have corrected all the attribute errors identified with the IdFix tool and have done steps 1 through 5 above, see [Set up directory synchronization](set-up-directory-synchronization.md).</span></span>
