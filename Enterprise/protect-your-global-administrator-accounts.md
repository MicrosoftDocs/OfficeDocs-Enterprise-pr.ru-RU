---
title: Защита учетных записей глобального администратора Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 4/10/2018
ms.audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Strat_O365_IP
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BCS160
ms.assetid: 6b4ded77-ac8d-42ed-8606-c014fd947560
description: Защитите глобальный администратор доступ к вашей подписке на Office 365, выполнив следующие три действия.
ms.openlocfilehash: 23d47ec1f5fc4126113dd69e1ac6400d003ca41f
ms.sourcegitcommit: 4ef8e113fa20b539de1087422455fc26ff123d55
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "30573923"
---
# <a name="protect-your-office-365-global-administrator-accounts"></a><span data-ttu-id="c397a-103">Защита учетных записей глобального администратора Office 365</span><span class="sxs-lookup"><span data-stu-id="c397a-103">Protect your Office 365 global administrator accounts</span></span>

 <span data-ttu-id="c397a-104">**Сводка:** Защитите свою подписку на Office 365, используя нарушение безопасности учетной записи глобального администратора.</span><span class="sxs-lookup"><span data-stu-id="c397a-104">**Summary:** Protect your Office 365 subscription from attacks based on the compromise of a global administrator account.</span></span> 
  
<span data-ttu-id="c397a-105">Нарушения безопасности подписки на Office 365, включая сбор информации и фишинговые атаки, обычно выполняются путем взлома учетных данных глобального администратора Office 365.</span><span class="sxs-lookup"><span data-stu-id="c397a-105">Security breaches of an Office 365 subscription, including information harvesting and phishing attacks, are typically done by compromising the credentials of an Office 365 global administrator account.</span></span> <span data-ttu-id="c397a-106">Безопасность в облаке — это партнерство между вами и корпорацией Майкрософт:</span><span class="sxs-lookup"><span data-stu-id="c397a-106">Security in the cloud is a partnership between you and Microsoft:</span></span>
  
- <span data-ttu-id="c397a-107">Облачные службы Майкрософт основаны на основах доверия и безопасности.</span><span class="sxs-lookup"><span data-stu-id="c397a-107">Microsoft cloud services are built on a foundation of trust and security.</span></span> <span data-ttu-id="c397a-108">Корпорация Майкрософт предоставляет функции безопасности и функции, помогающие защитить данные и приложения.</span><span class="sxs-lookup"><span data-stu-id="c397a-108">Microsoft provides you security controls and capabilities to help you protect your data and applications.</span></span>
    
- <span data-ttu-id="c397a-109">Вы владеете данными и удостоверениями и ответственностью за их защиту, безопасность локальных ресурсов и защиту облачных компонентов, которыми вы управляете.</span><span class="sxs-lookup"><span data-stu-id="c397a-109">You own your data and identities and the responsibility for protecting them, the security of your on-premises resources, and the security of cloud components you control.</span></span>
    
<span data-ttu-id="c397a-110">Корпорация Майкрософт предоставляет возможности для защиты вашей организации, но они эффективны только в том случае, если вы используете их.</span><span class="sxs-lookup"><span data-stu-id="c397a-110">Microsoft provides capabilities to help protect your organization, but they are effective only if you use them.</span></span> <span data-ttu-id="c397a-111">Если вы не используете их, возможно, она подвержена атакам.</span><span class="sxs-lookup"><span data-stu-id="c397a-111">If you do not use them, you may be vulnerable to attack.</span></span> <span data-ttu-id="c397a-112">Для защиты учетных записей глобального администратора Корпорация Майкрософт может помочь вам получить подробные инструкции:</span><span class="sxs-lookup"><span data-stu-id="c397a-112">To protect your global administrator accounts, Microsoft is here to help you with detailed instructions to:</span></span>
  
1. <span data-ttu-id="c397a-113">Создавайте выделенные учетные записи глобального администратора Office 365 и используйте их только при необходимости.</span><span class="sxs-lookup"><span data-stu-id="c397a-113">Create dedicated Office 365 global administrator accounts and use them only when necessary.</span></span>
    
2. <span data-ttu-id="c397a-114">Настройте многофакторную проверку подлинности для выделенных учетных записей глобального администратора Office 365 и используйте наиболее надежную форму вторичной проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="c397a-114">Configure multi-factor authentication for your dedicated Office 365 global administrator accounts and use the strongest form of secondary authentication.</span></span>
    
3. <span data-ttu-id="c397a-115">Включение и настройка безопасности облачных приложений Office 365 для отслеживания подозрительных действий с учетной записью глобального администратора.</span><span class="sxs-lookup"><span data-stu-id="c397a-115">Enable and configure Office 365 Cloud App Security to monitor for suspicious global administrator account activity.</span></span>
    
> [!NOTE]
> <span data-ttu-id="c397a-116">Несмотря на то, что эта статья ориентирована на учетные записи глобальных администраторов, следует учитывать, что дополнительные учетные записи с широкими разрешениями могут получать доступ к данным в вашей подписке, например администратору обнаружения электронных данных или обеспечению безопасности или соответствия требованиям. учетные записи администраторов должны быть защищены одинаковым образом.</span><span class="sxs-lookup"><span data-stu-id="c397a-116">Although this article is focused on global administrator accounts, you should also consider whether additional accounts with wide-ranging permissions to access the data in your subscription, such as eDiscovery administrator or security or compliance administrator accounts, should be protected in the same way.</span></span> 
  
## <a name="step-1-create-dedicated-office-365-global-administrator-accounts-and-use-them-only-when-necessary"></a><span data-ttu-id="c397a-117">Действие 1.</span><span class="sxs-lookup"><span data-stu-id="c397a-117">Step 1.</span></span> <span data-ttu-id="c397a-118">Создание выделенных учетных записей глобального администратора Office 365 и их использование только при необходимости</span><span class="sxs-lookup"><span data-stu-id="c397a-118">Create dedicated Office 365 global administrator accounts and use them only when necessary</span></span>

<span data-ttu-id="c397a-119">Существует относительно небольшое количество административных задач, таких как назначение ролей учетным записям пользователей, которым требуются права глобального администратора.</span><span class="sxs-lookup"><span data-stu-id="c397a-119">There are relatively few administrative tasks, such as assigning roles to user accounts, that require global administrator privileges.</span></span> <span data-ttu-id="c397a-120">Поэтому вместо использования ежедневных учетных записей пользователей, которым назначена роль глобального администратора, выполните следующие действия:</span><span class="sxs-lookup"><span data-stu-id="c397a-120">Therefore, instead of using everyday user accounts that have been assigned the global admin role, do these steps:</span></span>
  
1. <span data-ttu-id="c397a-121">Определите набор учетных записей пользователей, которым назначена роль глобального администратора.</span><span class="sxs-lookup"><span data-stu-id="c397a-121">Determine the set of user accounts that have been assigned the global admin role.</span></span> <span data-ttu-id="c397a-122">Это можно сделать с помощью этой команды в командной строки Microsoft Azure Active Directory модуля для Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="c397a-122">You can do this with this command at the Microsoft Azure Active Directory Module for Windows PowerShell command prompt:</span></span>
    
  ```
  Get-MsolRoleMember -RoleObjectId (Get-MsolRole -RoleName "Company Administrator").ObjectId
  ```

2. <span data-ttu-id="c397a-123">Войдите в свою подписку на Office 365, используя учетную запись пользователя, которой назначена роль глобального администратора.</span><span class="sxs-lookup"><span data-stu-id="c397a-123">Sign into your Office 365 subscription with a user account that has been assigned the global admin role.</span></span>
    
3. <span data-ttu-id="c397a-124">Создайте по крайней мере одну и более пяти выделенных учетных записей пользователей глобального администратора.</span><span class="sxs-lookup"><span data-stu-id="c397a-124">Create at least one and up to a maximum of five dedicated global administrator user accounts.</span></span> <span data-ttu-id="c397a-125">**Используйте надежные пароли длиной не более 12 символов.**</span><span class="sxs-lookup"><span data-stu-id="c397a-125">**Use strong passwords at least 12 characters long.**</span></span> <span data-ttu-id="c397a-126">Для получения дополнительных сведений ознакомьтесь со статьей [Создание надежного пароля](https://support.microsoft.com/help/4026406/microsoft-account-create-a-strong-password) .</span><span class="sxs-lookup"><span data-stu-id="c397a-126">See [Create a strong password](https://support.microsoft.com/help/4026406/microsoft-account-create-a-strong-password) for more information.</span></span> <span data-ttu-id="c397a-127">Храните пароли для новых учетных записей в надежном месте.</span><span class="sxs-lookup"><span data-stu-id="c397a-127">Store the passwords for the new accounts in a secure location.</span></span> 
    
4. <span data-ttu-id="c397a-128">Назначьте роль глобального администратора каждой новой выделенной учетной записи пользователя глобального администратора.</span><span class="sxs-lookup"><span data-stu-id="c397a-128">Assign the global admin role to each of the new dedicated global administrator user accounts.</span></span>
    
5. <span data-ttu-id="c397a-129">ВыЙдите из Office 365.</span><span class="sxs-lookup"><span data-stu-id="c397a-129">Sign out of Office 365.</span></span>
    
6. <span data-ttu-id="c397a-130">Войдите с помощью одной из новых выделенных учетных записей пользователей глобального администратора.</span><span class="sxs-lookup"><span data-stu-id="c397a-130">Sign in with one of the new dedicated global administrator user accounts.</span></span>
    
7. <span data-ttu-id="c397a-131">Для каждой существующей учетной записи пользователя, которой назначена роль глобального администратора из шага 1:</span><span class="sxs-lookup"><span data-stu-id="c397a-131">For each existing user account that had been assigned the global admin role from step 1:</span></span>
    
  - <span data-ttu-id="c397a-132">Удалите роль глобального администратора.</span><span class="sxs-lookup"><span data-stu-id="c397a-132">Remove the global admin role.</span></span>
    
  - <span data-ttu-id="c397a-133">Назначьте роли администратора учетной записи, которая соответствует должностным обязанностям и должностным обязанностям этого пользователя.</span><span class="sxs-lookup"><span data-stu-id="c397a-133">Assign admin roles to the account that are appropriate to that user's job function and responsibility.</span></span> <span data-ttu-id="c397a-134">Более подробную информацию о различных ролях администратора в Office 365 вы найдете в статье [о ролях администратора office 365](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d).</span><span class="sxs-lookup"><span data-stu-id="c397a-134">For more information about various admin roles in Office 365, see [About Office 365 admin roles](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d).</span></span>
    
8. <span data-ttu-id="c397a-135">ВыЙдите из Office 365.</span><span class="sxs-lookup"><span data-stu-id="c397a-135">Sign out of Office 365.</span></span>
    
<span data-ttu-id="c397a-136">Результат должен быть следующим:</span><span class="sxs-lookup"><span data-stu-id="c397a-136">The result should be:</span></span>
  
- <span data-ttu-id="c397a-137">Единственными учетными записями пользователей в подписке с ролью глобального администратора является новый набор выделенных учетных записей глобального администратора.</span><span class="sxs-lookup"><span data-stu-id="c397a-137">The only user accounts in your subscription that have the global admin role are the new set of dedicated global administrator accounts.</span></span> <span data-ttu-id="c397a-138">Проверьте это с помощью следующей команды PowerShell:</span><span class="sxs-lookup"><span data-stu-id="c397a-138">Verify this with the following PowerShell command:</span></span>
    
  ```
  Get-MsolRoleMember -RoleObjectId (Get-MsolRole -RoleName "Company Administrator").ObjectId
  ```

- <span data-ttu-id="c397a-139">Всем остальным повседневным учетным записям пользователей, которые управляют вашей подпиской, назначены роли администраторов, соответствующие должностным обязанностям этих пользователей.</span><span class="sxs-lookup"><span data-stu-id="c397a-139">All other everyday user accounts that manage your subscription have admin roles assigned that are associated with their job responsibilities.</span></span>
    
<span data-ttu-id="c397a-140">С этого момента вы входите с использованием выделенных учетных записей глобального администратора только для тех задач, для которых требуются права глобального администратора.</span><span class="sxs-lookup"><span data-stu-id="c397a-140">From this moment onward, you sign in with the dedicated global administrator accounts only for tasks that require global administrator privileges.</span></span> <span data-ttu-id="c397a-141">Все остальные административные приложения Office 365 должны быть выполнены путем назначения другим ролям администрирования учетным записям пользователей.</span><span class="sxs-lookup"><span data-stu-id="c397a-141">All other Office 365 administration must be done by assigning other administration roles to user accounts.</span></span>
  
> [!NOTE]
> <span data-ttu-id="c397a-142">Да, это требует дополнительных действий для выхода из учетной записи повседневного пользователя и входа в систему с помощью выделенной учетной записи глобального администратора.</span><span class="sxs-lookup"><span data-stu-id="c397a-142">Yes, this requires additional steps to sign out as your everyday user account and sign in with a dedicated global administrator account.</span></span> <span data-ttu-id="c397a-143">Но это время необходимо выполнять только для операций глобального администратора.</span><span class="sxs-lookup"><span data-stu-id="c397a-143">But this only needs to be done occasionally for global administrator operations.</span></span> <span data-ttu-id="c397a-144">Обратите внимание, что при восстановлении подписки на Office 365 после нарушения безопасности учетной записи глобального администратора требуются дополнительные действия.</span><span class="sxs-lookup"><span data-stu-id="c397a-144">Consider that recovering your Office 365 subscription after a global administrator account breach requires a lot more steps.</span></span> 
  
## <a name="step-2-configure-multi-factor-authentication-for-your-dedicated-office-365-global-administrator-accounts-and-use-the-strongest-form-of-secondary-authentication"></a><span data-ttu-id="c397a-145">Действие 2.</span><span class="sxs-lookup"><span data-stu-id="c397a-145">Step 2.</span></span> <span data-ttu-id="c397a-146">Настройка многофакторной проверки подлинности для выделенных учетных записей глобального администратора Office 365 и использование наиболее надежной формы дополнительной проверки подлинности</span><span class="sxs-lookup"><span data-stu-id="c397a-146">Configure multi-factor authentication for your dedicated Office 365 global administrator accounts and use the strongest form of secondary authentication</span></span>

<span data-ttu-id="c397a-147">Многофакторная проверка подлинности (MFA) для учетных записей глобального администратора требует дополнительной информации за пределами имени учетной записи и пароля.</span><span class="sxs-lookup"><span data-stu-id="c397a-147">Multi-factor authentication (MFA) for your global administrator accounts requires additional information beyond the account name and password.</span></span> <span data-ttu-id="c397a-148">Office 365 поддерживает следующие методы проверки:</span><span class="sxs-lookup"><span data-stu-id="c397a-148">Office 365 supports these verification methods:</span></span>
  
- <span data-ttu-id="c397a-149">телефонный звонок;</span><span class="sxs-lookup"><span data-stu-id="c397a-149">A phone call</span></span>
    
- <span data-ttu-id="c397a-150">код доступа, сформированный случайным образом;</span><span class="sxs-lookup"><span data-stu-id="c397a-150">A randomly generated pass code</span></span>
    
- <span data-ttu-id="c397a-151">смарт-карта (виртуальная или физическая);</span><span class="sxs-lookup"><span data-stu-id="c397a-151">A smart card (virtual or physical)</span></span>
    
- <span data-ttu-id="c397a-152">биометрическое устройство.</span><span class="sxs-lookup"><span data-stu-id="c397a-152">A biometric device</span></span>
    
<span data-ttu-id="c397a-153">Если вы используете небольшие предприятия, которые используют учетные записи пользователей, хранящиеся только в облаке (Облачная модель удостоверений), выполните указанные ниже действия, чтобы настроить MFA с помощью телефонного вызова или кода проверки текстового сообщения, отправляемого на смарт-телефон:</span><span class="sxs-lookup"><span data-stu-id="c397a-153">If you are a small business that is using user accounts stored only in the cloud (the cloud identity model), use these steps to configure MFA using a phone call or a text message verification code sent to a smart phone:</span></span>
  
1. <span data-ttu-id="c397a-154">[Включите MFA](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6).</span><span class="sxs-lookup"><span data-stu-id="c397a-154">[Enable MFA](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6).</span></span>
    
2. <span data-ttu-id="c397a-155">Настройка [2 – шаг проверки для Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) для настройки каждой выделенной учетной записи глобального администратора для телефонного звонка или текстового сообщения в качестве метода проверки.</span><span class="sxs-lookup"><span data-stu-id="c397a-155">[Set up 2-step verification for Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) to configure each dedicated global administrator account for phone call or text message as the verification method.</span></span> 
    
<span data-ttu-id="c397a-156">Если вы используете более крупную организацию, которая использует гибридную модель удостоверений Office 365, вы можете использовать дополнительные параметры проверки.</span><span class="sxs-lookup"><span data-stu-id="c397a-156">If you are a larger organization that is using an Office 365 hybrid identity model, you have more verification options.</span></span> <span data-ttu-id="c397a-157">Если у вас уже есть инфраструктура безопасности для более надежного вторичного метода проверки подлинности, выполните указанные ниже действия.</span><span class="sxs-lookup"><span data-stu-id="c397a-157">If you have the security infrastructure already in place for a stronger secondary authentication method, use these steps:</span></span>
  
1. <span data-ttu-id="c397a-158">[Включите MFA](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6).</span><span class="sxs-lookup"><span data-stu-id="c397a-158">[Enable MFA](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6).</span></span>
    
2. <span data-ttu-id="c397a-159">Настройте [2 этапа проверки для Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) , чтобы настроить каждую выделенную учетную запись глобального администратора для соответствующего метода проверки.</span><span class="sxs-lookup"><span data-stu-id="c397a-159">[Set up 2-step verification for Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) to configure each dedicated global administrator account for the appropriate verification method.</span></span> 
    
<span data-ttu-id="c397a-160">Если инфраструктура безопасности для нужного более надежного метода проверки не на месте и не работает в Office 365 MFA, настоятельно рекомендуется настроить выделенные учетные записи глобального администратора с помощью функции MFA с помощью телефонного вызова или текстового сообщения. код проверки, отправленный на смарт-телефон для учетных записей глобального администратора в качестве промежуточной меры безопасности.</span><span class="sxs-lookup"><span data-stu-id="c397a-160">If the security infrastructure for the desired stronger verification method is not in place and functioning for Office 365 MFA, we strongly recommend that you configure dedicated global administrator accounts with MFA using a phone call or a text message verification code sent to a smart phone for your global administrator accounts as an interim security measure.</span></span> <span data-ttu-id="c397a-161">Не оставляйте выделенных учетных записей глобального администратора без дополнительной защиты, предоставляемой MFA.</span><span class="sxs-lookup"><span data-stu-id="c397a-161">Do not leave your dedicated global administrator accounts without the additional protection provided by MFA.</span></span>
  
<span data-ttu-id="c397a-162">Дополнительные сведения см. в статье [Планирование многофакторной проверки подлинности для развертываний Office 365](https://support.office.com/article/043807b2-21db-4d5c-b430-c8a6dee0e6ba).</span><span class="sxs-lookup"><span data-stu-id="c397a-162">For more information, see [Plan for multi-factor authentication for Office 365 Deployments](https://support.office.com/article/043807b2-21db-4d5c-b430-c8a6dee0e6ba).</span></span>
  
<span data-ttu-id="c397a-163">Чтобы подключиться к службам Office 365 с помощью MFA и PowerShell, ознакомьтесь с [этой статьей](https://blogs.technet.microsoft.com/solutions_advisory_board/2017/04/27/connect-to-office-365-services-with-multifactor-authentication-mfa-and-powershell/).</span><span class="sxs-lookup"><span data-stu-id="c397a-163">To connect to Office 365 services with MFA and PowerShell, see [this article](https://blogs.technet.microsoft.com/solutions_advisory_board/2017/04/27/connect-to-office-365-services-with-multifactor-authentication-mfa-and-powershell/).</span></span>
  
## <a name="step-3-monitor-for-suspicious-global-administrator-account-activity"></a><span data-ttu-id="c397a-164">Действие 3.</span><span class="sxs-lookup"><span data-stu-id="c397a-164">Step 3.</span></span> <span data-ttu-id="c397a-165">Наблюдение за подозрительными действиями с учетной записью глобального администратора</span><span class="sxs-lookup"><span data-stu-id="c397a-165">Monitor for suspicious global administrator account activity</span></span>

<span data-ttu-id="c397a-166">Office 365 Cloud App Security позволяет создавать политики для уведомления о подозрительном поведении подписки.</span><span class="sxs-lookup"><span data-stu-id="c397a-166">Office 365 Cloud App Security lets you create policies to notify you of suspicious behavior in your subscription.</span></span> <span data-ttu-id="c397a-167">Cloud App Security встроено в Office 365, но также доступно как отдельная служба.</span><span class="sxs-lookup"><span data-stu-id="c397a-167">Cloud App Security is built into Office 365 E5, but is also available as a separate service.</span></span> <span data-ttu-id="c397a-168">Например, если у вас нет Office 365, то вы можете приобрести отдельные лицензии Cloud App Security для учетных записей пользователей, которым назначены роли глобального администратора, администратора безопасности и администратора соответствия требованиям.</span><span class="sxs-lookup"><span data-stu-id="c397a-168">For example, if you do not have Office 365 E5, you can purchase individual Cloud App Security licenses for the user accounts that are assigned the global administrator, security administrator, and compliance administrator roles.</span></span>
  
<span data-ttu-id="c397a-169">Если вы используете Cloud App Security в вашей подписке на Office 365, выполните указанные ниже действия.</span><span class="sxs-lookup"><span data-stu-id="c397a-169">If you have Cloud App Security in your Office 365 subscription, use these steps:</span></span>
  
1. <span data-ttu-id="c397a-170">Войдите в центр администрирования Microsoft 365 с помощью учетной записи, которой назначена роль администратора безопасности или администратора соответствия требованиям.</span><span class="sxs-lookup"><span data-stu-id="c397a-170">Sign into the Microsoft 365 admin center with an account that is assigned the Security Administrator or Compliance Administrator role.</span></span>
    
2. <span data-ttu-id="c397a-171">[Включите Cloud App Security для Office 365](https://support.office.com/article/ba919c73-d021-404d-9850-eec57e78678c).</span><span class="sxs-lookup"><span data-stu-id="c397a-171">[Turn on Office 365 Cloud App Security](https://support.office.com/article/ba919c73-d021-404d-9850-eec57e78678c).</span></span>
    
3. <span data-ttu-id="c397a-172">Просмотрите [политики обнаружения аномалий в Office 365 Cloud App Security](https://support.office.com/article/88935b4e-dcb1-47f1-8aca-1bf8fb069db6) , чтобы уведомить вас по электронной почте о неаномальных действиях административного действия.</span><span class="sxs-lookup"><span data-stu-id="c397a-172">Review your [Anomaly detection policies in Office 365 Cloud App Security](https://support.office.com/article/88935b4e-dcb1-47f1-8aca-1bf8fb069db6) to notify you by email of anomalous patterns of privileged administrative activity.</span></span> 
    
<span data-ttu-id="c397a-173">Чтобы добавить учетную запись пользователя в роль администратора безопасности, [подключитесь к Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx#step3) с выделенной учетной записью глобального администратора и MFA, введите имя участника учетной записи пользователя и затем выполните следующие команды:</span><span class="sxs-lookup"><span data-stu-id="c397a-173">To add a user account to the Security Administrator role, [connect to Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx#step3) with a dedicated global administrator account and MFA, fill in the user principal name of the user account, and then run these commands:</span></span> 
  
```
$upn="<User principal name of the account>"
Add-MsolRoleMember -RoleMemberEmailAddress $upn -RoleName "Security Administrator"
```

<span data-ttu-id="c397a-174">Чтобы добавить учетную запись пользователя в роль администратора соответствия требованиям, заполните имя участника учетной записи пользователя, а затем выполните следующие команды:</span><span class="sxs-lookup"><span data-stu-id="c397a-174">To add a user account to the Compliance Administrator role, fill in the user principal name of the user account, and then run these commands:</span></span>
  
```
$upn="<User principal name of the account>"
Add-MsolRoleMember -RoleMemberEmailAddress  $upn -RoleName "Compliance Administrator"
```

## <a name="additional-protections-for-enterprise-organizations"></a><span data-ttu-id="c397a-175">Дополнительные средства защиты для корпоративных организаций</span><span class="sxs-lookup"><span data-stu-id="c397a-175">Additional protections for enterprise organizations</span></span>

<span data-ttu-id="c397a-176">После выполнения шагов 1-3 Используйте следующие дополнительные методы, чтобы убедиться, что ваша учетная запись глобального администратора и конфигурация, с помощью которой выполняется эта учетная запись, защищены как можно более безопасные.</span><span class="sxs-lookup"><span data-stu-id="c397a-176">After steps 1-3, use these additional methods to ensure that your global administrator account, and the configuration that you perform using it, are as secure as possible.</span></span>
  
### <a name="privileged-access-workstation-paw"></a><span data-ttu-id="c397a-177">Рабочая станция привилегированного доступа (PAW)</span><span class="sxs-lookup"><span data-stu-id="c397a-177">Privileged Access Workstation (PAW)</span></span>

<span data-ttu-id="c397a-178">Чтобы гарантировать максимально надежную защиту выполнения задач, используйте PAW.</span><span class="sxs-lookup"><span data-stu-id="c397a-178">To ensure that the execution of highly privileged tasks is as secure as possible, use a PAW.</span></span> <span data-ttu-id="c397a-179">PAW — это выделенный компьютер, который используется только для важных задач настройки, таких как конфигурация Office 365, для которой требуется учетная запись глобального администратора.</span><span class="sxs-lookup"><span data-stu-id="c397a-179">A PAW is a dedicated computer that is only used for sensitive configuration tasks, such as Office 365 configuration that requires a global administrator account.</span></span> <span data-ttu-id="c397a-180">Так как этот компьютер не используется ежедневно для просмотра в Интернете или электронной почты, он лучше защищен от атак из Интернета и угроз.</span><span class="sxs-lookup"><span data-stu-id="c397a-180">Because this computer is not used daily for Internet browsing or email, it is better protected from Internet attacks and threats.</span></span>
  
<span data-ttu-id="c397a-181">Инструкции по настройке PAW приведены в разделе [http://aka.ms/cyberpaw](http://aka.ms/cyberpaw).</span><span class="sxs-lookup"><span data-stu-id="c397a-181">For instructions on how to set up a PAW, see [http://aka.ms/cyberpaw](http://aka.ms/cyberpaw).</span></span>
  
### <a name="azure-ad-privileged-identity-management-pim"></a><span data-ttu-id="c397a-182">Управление удостоверениями в Azure AD (PIM)</span><span class="sxs-lookup"><span data-stu-id="c397a-182">Azure AD Privileged Identity Management (PIM)</span></span>

<span data-ttu-id="c397a-183">Вместо того чтобы учетным записям глобального администратора было окончательно назначена роль глобального администратора, можно использовать службу PIM Azure AD, чтобы включить необязательное назначение роли глобального администратора по требованию, когда это необходимо.</span><span class="sxs-lookup"><span data-stu-id="c397a-183">Rather than having your global administrator accounts be permanently assigned the global administrator role, you can use Azure AD PIM to enable on-demand, just-in-time assignment of the global administrator role when it is needed.</span></span>
  
<span data-ttu-id="c397a-184">Вместо того, чтобы учетные записи глобального администратора были постоянными администраторами, они становятся доступными администраторам.</span><span class="sxs-lookup"><span data-stu-id="c397a-184">Instead of your global administrator accounts being a permanent admin, they become eligible administrators.</span></span> <span data-ttu-id="c397a-185">Роль глобального администратора неактивна, пока она не нужна.</span><span class="sxs-lookup"><span data-stu-id="c397a-185">The global administrator role is inactive until someone needs it.</span></span> <span data-ttu-id="c397a-186">После этого вы можете выполнить процесс активации, чтобы добавить роль глобального администратора в учетную запись глобального администратора на предварительно заданный период времени.</span><span class="sxs-lookup"><span data-stu-id="c397a-186">You then complete an activation process to add the global administrator role to the global administrator account for a predetermined amount of time.</span></span> <span data-ttu-id="c397a-187">По истечении этого действия, PIM Удаляет роль глобального администратора из учетной записи глобального администратора.</span><span class="sxs-lookup"><span data-stu-id="c397a-187">When the time expires, PIM removes the global administrator role from the global administrator account.</span></span>
  
<span data-ttu-id="c397a-188">Использование PIM и этого процесса значительно сокращает время, в течение которого учетные записи глобальных администраторов уязвимы для атак и использования злоумышленниками.</span><span class="sxs-lookup"><span data-stu-id="c397a-188">Using PIM and this process significantly reduces the amount of time that your global administrator accounts are vulnerable to attack and use by malicious users.</span></span>
  
<span data-ttu-id="c397a-189">Дополнительные сведения можно найти в статье [Настройка службы управления удостоверенИями Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure).</span><span class="sxs-lookup"><span data-stu-id="c397a-189">For more information, see [Configure Azure AD Privileged Identity Management](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure).</span></span>
  
> [!NOTE]
> <span data-ttu-id="c397a-190">Служба PIM доступна с помощью Azure Active Directory Premium P2, которая входит в состав Enterprise Mobility + Security (EMS), или вы можете приобрести отдельные лицензии для учетных записей глобального администратора.</span><span class="sxs-lookup"><span data-stu-id="c397a-190">PIM is available with Azure Active Directory Premium P2, which is included with Enterprise Mobility + Security (EMS) E5, or you can purchase individual licenses for your global administrator accounts.</span></span> 
  
### <a name="security-information-and-event-management-siem-software-for-office-365-logging"></a><span data-ttu-id="c397a-191">Сведения о безопасности и программное обеспечение управления событиями (SIEM) для ведения журнала в Office 365</span><span class="sxs-lookup"><span data-stu-id="c397a-191">Security information and event management (SIEM) software for Office 365 logging</span></span>

<span data-ttu-id="c397a-192">Программное обеспечение SIEM, выполняемое на сервере, выполняет анализ оповещений системы безопасности и событий, созданных приложениями и сетевым оборудованием, в режиме реального времени.</span><span class="sxs-lookup"><span data-stu-id="c397a-192">SIEM software run on a server performs real-time analysis of security alerts and events created by applications and network hardware.</span></span> <span data-ttu-id="c397a-193">Чтобы разрешить серверу SIEM включать оповещения и события безопасности Office 365 в функции анализа и создания отчетов, интегрируйте их в систему SIEM:</span><span class="sxs-lookup"><span data-stu-id="c397a-193">To allow your SIEM server to include Office 365 security alerts and events in its analysis and reporting functions, integrate these in your SIEM system:</span></span>
  
- <span data-ttu-id="c397a-194">Azure AD</span><span class="sxs-lookup"><span data-stu-id="c397a-194">Azure AD</span></span>
    
    <span data-ttu-id="c397a-195">Дополнительные сведения см. [в статье интеграция журналов из ресурсов Azure в ваши системы SIEM](https://docs.microsoft.com/azure/security/security-azure-log-integration-overview).</span><span class="sxs-lookup"><span data-stu-id="c397a-195">For more information, see [Integrate logs from Azure resources into your SIEM systems](https://docs.microsoft.com/azure/security/security-azure-log-integration-overview).</span></span>
    
- <span data-ttu-id="c397a-196">Office 365 Cloud App Security</span><span class="sxs-lookup"><span data-stu-id="c397a-196">Office 365 Cloud App Security</span></span>
    
    <span data-ttu-id="c397a-197">Дополнительные сведения см. [в статье интеграция сервера SIEM с Office 365 Cloud App Security](https://support.office.com/article/dd6d2417-49c4-4de6-9294-67fdabbf8532).</span><span class="sxs-lookup"><span data-stu-id="c397a-197">For more information, see [Integrate your SIEM server with Office 365 Cloud App Security](https://support.office.com/article/dd6d2417-49c4-4de6-9294-67fdabbf8532).</span></span>
    
## <a name="next-step"></a><span data-ttu-id="c397a-198">Следующий шаг</span><span class="sxs-lookup"><span data-stu-id="c397a-198">Next step</span></span>

<span data-ttu-id="c397a-199">Рекомендации [по обеспечению безопасности для Office 365](https://support.office.com/article/9295e396-e53d-49b9-ae9b-0b5828cdedc3).</span><span class="sxs-lookup"><span data-stu-id="c397a-199">See [Security best practices for Office 365](https://support.office.com/article/9295e396-e53d-49b9-ae9b-0b5828cdedc3).</span></span>
  

