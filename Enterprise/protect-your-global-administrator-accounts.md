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
description: Защита глобального администратора доступ к подписки Office 365 с помощью следующих трех действий.
ms.openlocfilehash: 41168643fb8867017865860624c8b436460fa0b8
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2019
ms.locfileid: "25897522"
---
# <a name="protect-your-office-365-global-administrator-accounts"></a><span data-ttu-id="8e420-103">Защита учетных записей глобального администратора Office 365</span><span class="sxs-lookup"><span data-stu-id="8e420-103">Protect your Office 365 global administrator accounts</span></span>

 <span data-ttu-id="8e420-104">**Сводка:** Защита от атак на основании компромиссов учетной записи глобального администратора подписки Office 365.</span><span class="sxs-lookup"><span data-stu-id="8e420-104">**Summary:** Protect your Office 365 subscription from attacks based on the compromise of a global administrator account.</span></span> 
  
<span data-ttu-id="8e420-p101">Нарушение безопасности с последующим подписку на Office 365, включая сбор информации и фишинга, обычно выполняется по снижения учетные данные учетной записи глобального администратора Office 365. Безопасность в облаке представляет отношение доверия между вами и корпорацией Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="8e420-p101">Security breaches of an Office 365 subscription, including information harvesting and phishing attacks, are typically done by compromising the credentials of an Office 365 global administrator account. Security in the cloud is a partnership between you and Microsoft:</span></span>
  
- <span data-ttu-id="8e420-p102">Облачные службы Майкрософт создаются на основе доверия и безопасности. Корпорация Майкрософт предоставляет элементы управления безопасности и возможностей по защите данных и приложений.</span><span class="sxs-lookup"><span data-stu-id="8e420-p102">Microsoft cloud services are built on a foundation of trust and security. Microsoft provides you security controls and capabilities to help you protect your data and applications.</span></span>
    
- <span data-ttu-id="8e420-109">Владельцем данных и удостоверения и ответственность за защита их безопасности локальным ресурсам и безопасность облака компонентах, от которых можно управлять.</span><span class="sxs-lookup"><span data-stu-id="8e420-109">You own your data and identities and the responsibility for protecting them, the security of your on-premises resources, and the security of cloud components you control.</span></span>
    
<span data-ttu-id="8e420-p103">Корпорация Майкрософт предоставляет возможности, которые помогут защитить организацию, но они действуют только в том случае, если они используются. Если вы не используете их, могут быть уязвимы к атакам. Чтобы защитить учетные записи глобального администратора, корпорация Майкрософт считает здесь призванные помочь вам с подробные инструкции по:</span><span class="sxs-lookup"><span data-stu-id="8e420-p103">Microsoft provides capabilities to help protect your organization, but they are effective only if you use them. If you do not use them, you may be vulnerable to attack. To protect your global administrator accounts, Microsoft is here to help you with detailed instructions to:</span></span>
  
1. <span data-ttu-id="8e420-113">Создание выделенных учетных записей глобального администратора Office 365 и использовать их только при необходимости.</span><span class="sxs-lookup"><span data-stu-id="8e420-113">Create dedicated Office 365 global administrator accounts and use them only when necessary.</span></span>
    
2. <span data-ttu-id="8e420-114">Настройка многофакторной проверки подлинности для выделенных учетных записей глобального администратора Office 365 и использование высший уровень дополнительного проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="8e420-114">Configure multi-factor authentication for your dedicated Office 365 global administrator accounts and use the strongest form of secondary authentication.</span></span>
    
3. <span data-ttu-id="8e420-115">Включение и настройка безопасности Office 365 облаке приложения для наблюдения за активности подозрительные глобального администратора учетной записи.</span><span class="sxs-lookup"><span data-stu-id="8e420-115">Enable and configure Office 365 Cloud App Security to monitor for suspicious global administrator account activity.</span></span>
    
> [!NOTE]
> <span data-ttu-id="8e420-116">Несмотря на то, что в этой статье, ориентированный на учетные записи глобального администратора, также необходимо учитывать ли дополнительные учетные записи с более общие разрешения на доступ к данным в подписке, таких как eDiscovery администратора или безопасности или соответствия защиты учетных записей администраторов, так же, как следует.</span><span class="sxs-lookup"><span data-stu-id="8e420-116">Although this article is focused on global administrator accounts, you should also consider whether additional accounts with wide-ranging permissions to access the data in your subscription, such as eDiscovery administrator or security or compliance administrator accounts, should be protected in the same way.</span></span> 
  
## <a name="step-1-create-dedicated-office-365-global-administrator-accounts-and-use-them-only-when-necessary"></a><span data-ttu-id="8e420-p104">Шаг 1. Создание выделенных учетных записей глобального администратора Office 365 и использовать их только при необходимости</span><span class="sxs-lookup"><span data-stu-id="8e420-p104">Step 1. Create dedicated Office 365 global administrator accounts and use them only when necessary</span></span>

<span data-ttu-id="8e420-p105">Существует относительно небольшим числом задач администрирования, таких как назначение ролей для учетных записей пользователей, которые требуются права глобального администратора. Таким образом вместо использования повседневных учетные записи, которым назначена роль глобального администратора, выполните следующие действия:</span><span class="sxs-lookup"><span data-stu-id="8e420-p105">There are relatively few administrative tasks, such as assigning roles to user accounts, that require global administrator privileges. Therefore, instead of using everyday user accounts that have been assigned the global admin role, do these steps:</span></span>
  
1. <span data-ttu-id="8e420-p106">Определение набора учетных записей пользователей, которым был назначен в роль глобального администратора. Это можно сделать с помощью этой команды в командной строке Microsoft Azure модуль Active Directory для Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="8e420-p106">Determine the set of user accounts that have been assigned the global admin role. You can do this with this command at the Microsoft Azure Active Directory Module for Windows PowerShell command prompt:</span></span>
    
  ```
  Get-MsolRoleMember -RoleObjectId (Get-MsolRole -RoleName "Company Administrator").ObjectId
  ```

2. <span data-ttu-id="8e420-123">Войдите в подписки Office 365 с помощью учетной записи пользователя, которому назначена роль глобального администратора.</span><span class="sxs-lookup"><span data-stu-id="8e420-123">Sign into your Office 365 subscription with a user account that has been assigned the global admin role.</span></span>
    
3. <span data-ttu-id="8e420-p107">Создайте по крайней мере один и более чем на пять выделенных учетных записей пользователей глобального администратора. **Использование надежных паролей по крайней мере 12 символов длинное** Для получения дополнительных сведений см. [Создание надежных паролей](https://support.microsoft.com/help/4026406/microsoft-account-create-a-strong-password) . Храните пароли для новых учетных записей в надежном месте.</span><span class="sxs-lookup"><span data-stu-id="8e420-p107">Create at least one and up to a maximum of five dedicated global administrator user accounts. **Use strong passwords at least 12 characters long.** See [Create a strong password](https://support.microsoft.com/help/4026406/microsoft-account-create-a-strong-password) for more information. Store the passwords for the new accounts in a secure location.</span></span> 
    
4. <span data-ttu-id="8e420-128">Назначение роли глобального администратора для каждого из учетных записей пользователей новые выделенного глобального администратора.</span><span class="sxs-lookup"><span data-stu-id="8e420-128">Assign the global admin role to each of the new dedicated global administrator user accounts.</span></span>
    
5. <span data-ttu-id="8e420-129">Выход из Office 365.</span><span class="sxs-lookup"><span data-stu-id="8e420-129">Sign out of Office 365.</span></span>
    
6. <span data-ttu-id="8e420-130">Вход с помощью одного из новых учетных записей пользователей выделенного глобального администратора.</span><span class="sxs-lookup"><span data-stu-id="8e420-130">Sign in with one of the new dedicated global administrator user accounts.</span></span>
    
7. <span data-ttu-id="8e420-131">Для каждой существующей учетной записи пользователя, который был назначен роль глобального администратора в шаге 1:</span><span class="sxs-lookup"><span data-stu-id="8e420-131">For each existing user account that had been assigned the global admin role from step 1:</span></span>
    
  - <span data-ttu-id="8e420-132">Удалите роль глобального администратора.</span><span class="sxs-lookup"><span data-stu-id="8e420-132">Remove the global admin role.</span></span>
    
  - <span data-ttu-id="8e420-p108">Назначение роли администратора для учетной записи, которая подходит для работы этого пользователя и ответственности. Дополнительные сведения о различных ролях администратора в Office 365 можно [роли администраторов об Office 365](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d).</span><span class="sxs-lookup"><span data-stu-id="8e420-p108">Assign admin roles to the account that are appropriate to that user's job function and responsibility. For more information about various admin roles in Office 365, see [About Office 365 admin roles](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d).</span></span>
    
8. <span data-ttu-id="8e420-135">Выход из Office 365.</span><span class="sxs-lookup"><span data-stu-id="8e420-135">Sign out of Office 365.</span></span>
    
<span data-ttu-id="8e420-136">Должно быть:</span><span class="sxs-lookup"><span data-stu-id="8e420-136">The result should be:</span></span>
  
- <span data-ttu-id="8e420-p109">Только учетные записи пользователей в своей подписке, на которых роль глобального администратора — новый набор учетных записей выделенного глобального администратора. Чтобы проверьте это с помощью следующей команды PowerShell:</span><span class="sxs-lookup"><span data-stu-id="8e420-p109">The only user accounts in your subscription that have the global admin role are the new set of dedicated global administrator accounts. Verify this with the following PowerShell command:</span></span>
    
  ```
  Get-MsolRoleMember -RoleObjectId (Get-MsolRole -RoleName "Company Administrator").ObjectId
  ```

- <span data-ttu-id="8e420-139">Всем остальным повседневным учетным записям пользователей, которые управляют вашей подпиской, назначены роли администраторов, соответствующие должностным обязанностям этих пользователей.</span><span class="sxs-lookup"><span data-stu-id="8e420-139">All other everyday user accounts that manage your subscription have admin roles assigned that are associated with their job responsibilities.</span></span>
    
<span data-ttu-id="8e420-p110">Из и далее в данный момент входе с учетными записями выделенного глобального администратора только для задач, которые требуются права глобального администратора. Назначение других ролей администрирования для учетных записей пользователей должна выполняться другим администрирования Office 365.</span><span class="sxs-lookup"><span data-stu-id="8e420-p110">From this moment onward, you sign in with the dedicated global administrator accounts only for tasks that require global administrator privileges. All other Office 365 administration must be done by assigning other administration roles to user accounts.</span></span>
  
> [!NOTE]
> <span data-ttu-id="8e420-p111">Да, для этого необходимо дополнительные действия по выход как учетная запись пользователя повседневных и выполнить вход с учетной записью выделенного глобального администратора. Однако это действие необходимо выполнить иногда для операций глобального администратора. Обратите внимание на следующее восстановление подписки Office 365 после сбоя учетной записи глобального администратора, необходимо выполнить больше действий.</span><span class="sxs-lookup"><span data-stu-id="8e420-p111">Yes, this requires additional steps to sign out as your everyday user account and sign in with a dedicated global administrator account. But this only needs to be done occasionally for global administrator operations. Consider that recovering your Office 365 subscription after a global administrator account breach requires a lot more steps.</span></span> 
  
## <a name="step-2-configure-multi-factor-authentication-for-your-dedicated-office-365-global-administrator-accounts-and-use-the-strongest-form-of-secondary-authentication"></a><span data-ttu-id="8e420-p112">Шаг 2. Настройка многофакторной проверки подлинности для выделенных учетных записей глобального администратора Office 365 и использование высший уровень дополнительного проверки подлинности</span><span class="sxs-lookup"><span data-stu-id="8e420-p112">Step 2. Configure multi-factor authentication for your dedicated Office 365 global administrator accounts and use the strongest form of secondary authentication</span></span>

<span data-ttu-id="8e420-p113">Многофакторная проверка подлинности (многофакторной проверкой Подлинности) для учетные записи глобального администратора требует дополнительной информации за пределы имя учетной записи и пароль. Office 365 поддерживает следующие методы проверки:</span><span class="sxs-lookup"><span data-stu-id="8e420-p113">Multi-factor authentication (MFA) for your global administrator accounts requires additional information beyond the account name and password. Office 365 supports these verification methods:</span></span>
  
- <span data-ttu-id="8e420-149">телефонный звонок;</span><span class="sxs-lookup"><span data-stu-id="8e420-149">A phone call</span></span>
    
- <span data-ttu-id="8e420-150">код доступа, сформированный случайным образом;</span><span class="sxs-lookup"><span data-stu-id="8e420-150">A randomly generated pass code</span></span>
    
- <span data-ttu-id="8e420-151">смарт-карта (виртуальная или физическая);</span><span class="sxs-lookup"><span data-stu-id="8e420-151">A smart card (virtual or physical)</span></span>
    
- <span data-ttu-id="8e420-152">биометрическое устройство.</span><span class="sxs-lookup"><span data-stu-id="8e420-152">A biometric device</span></span>
    
<span data-ttu-id="8e420-153">Если вы являетесь малого бизнеса, с помощью учетных записей пользователей, хранятся только в облаке (модель облачных удостоверений), выполните следующие действия для настройки многофакторной проверкой Подлинности с помощью телефонного звонка или код проверки текста сообщения, отправленным на смарт-телефон.</span><span class="sxs-lookup"><span data-stu-id="8e420-153">If you are a small business that is using user accounts stored only in the cloud (the cloud identity model), use these steps to configure MFA using a phone call or a text message verification code sent to a smart phone:</span></span>
  
1. <span data-ttu-id="8e420-154">[Включение многофакторной проверкой Подлинности](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6).</span><span class="sxs-lookup"><span data-stu-id="8e420-154">[Enable MFA](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6).</span></span>
    
2. <span data-ttu-id="8e420-155">[Настройка проверки шаг 2 для Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) для настройки каждого выделенных учетной записи глобального администратора для текстовых сообщений или телефонный звонок как метода проверки.</span><span class="sxs-lookup"><span data-stu-id="8e420-155">[Set up 2-step verification for Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) to configure each dedicated global administrator account for phone call or text message as the verification method.</span></span> 
    
<span data-ttu-id="8e420-p114">Если вы являетесь организации среднего размера, которую используют модель identity гибридных Office 365, у вас есть дополнительные параметры проверки. Если имеется инфраструктура безопасности уже на месте для более надежная метод дополнительного проверки подлинности, выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="8e420-p114">If you are a larger organization that is using an Office 365 hybrid identity model, you have more verification options. If you have the security infrastructure already in place for a stronger secondary authentication method, use these steps:</span></span>
  
1. <span data-ttu-id="8e420-158">[Включение многофакторной проверкой Подлинности](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6).</span><span class="sxs-lookup"><span data-stu-id="8e420-158">[Enable MFA](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6).</span></span>
    
2. <span data-ttu-id="8e420-159">[Настройка проверки шаг 2 для Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) для настройки каждого выделенной учетной записи глобального администратора для метода соответствующие проверки.</span><span class="sxs-lookup"><span data-stu-id="8e420-159">[Set up 2-step verification for Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) to configure each dedicated global administrator account for the appropriate verification method.</span></span> 
    
<span data-ttu-id="8e420-p115">Если инфраструктуры безопасности для нужного более надежная метода проверки нет на месте и времени для Office 365 многофакторной проверкой Подлинности, настоятельно рекомендуется настроить учетные записи выделенного глобального администратора с многофакторной проверкой Подлинности с помощью телефонного звонка или текстовое сообщение код подтверждения, отправленным на смарт-телефон для учетные записи глобального администратора в качестве меры безопасности промежуточный режим работы. Не оставляйте учетные записи выделенного глобального администратора без дополнительных защищены с многофакторной проверкой Подлинности.</span><span class="sxs-lookup"><span data-stu-id="8e420-p115">If the security infrastructure for the desired stronger verification method is not in place and functioning for Office 365 MFA, we strongly recommend that you configure dedicated global administrator accounts with MFA using a phone call or a text message verification code sent to a smart phone for your global administrator accounts as an interim security measure. Do not leave your dedicated global administrator accounts without the additional protection provided by MFA.</span></span>
  
<span data-ttu-id="8e420-162">Дополнительные сведения см. в статье [Планирование многофакторной проверки подлинности для развертываний Office 365](https://support.office.com/article/043807b2-21db-4d5c-b430-c8a6dee0e6ba).</span><span class="sxs-lookup"><span data-stu-id="8e420-162">For more information, see [Plan for multi-factor authentication for Office 365 Deployments](https://support.office.com/article/043807b2-21db-4d5c-b430-c8a6dee0e6ba).</span></span>
  
<span data-ttu-id="8e420-163">[Чтобы подключиться к службам Office 365 с многофакторной проверкой Подлинности и PowerShell, см.](https://blogs.technet.microsoft.com/solutions_advisory_board/2017/04/27/connect-to-office-365-services-with-multifactor-authentication-mfa-and-powershell/)</span><span class="sxs-lookup"><span data-stu-id="8e420-163">To connect to Office 365 services with MFA and PowerShell, see [this article](https://blogs.technet.microsoft.com/solutions_advisory_board/2017/04/27/connect-to-office-365-services-with-multifactor-authentication-mfa-and-powershell/).</span></span>
  
## <a name="step-3-monitor-for-suspicious-global-administrator-account-activity"></a><span data-ttu-id="8e420-p116">Шаг 3. Монитор для учетной записи действия подозрительные глобального администратора</span><span class="sxs-lookup"><span data-stu-id="8e420-p116">Step 3. Monitor for suspicious global administrator account activity</span></span>

<span data-ttu-id="8e420-p117">Безопасности приложения Office 365 облако позволяет создавать политики для уведомления о подозрительных поведение в подписке. Безопасность в облаке приложения встроен в Office 365 E5, но также доступен в качестве отдельной службы. К примеру при отсутствии Office 365 E5 вы можете приобрести индивидуальных лицензий облачных приложений безопасности для учетных записей пользователей, которым назначен глобального администратора, администратора безопасности и соответствия ролей администратора.</span><span class="sxs-lookup"><span data-stu-id="8e420-p117">Office 365 Cloud App Security lets you create policies to notify you of suspicious behavior in your subscription. Cloud App Security is built into Office 365 E5, but is also available as a separate service. For example, if you do not have Office 365 E5, you can purchase individual Cloud App Security licenses for the user accounts that are assigned the global administrator, security administrator, and compliance administrator roles.</span></span>
  
<span data-ttu-id="8e420-169">При наличии безопасности приложения облака в подписки Office 365, выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="8e420-169">If you have Cloud App Security in your Office 365 subscription, use these steps:</span></span>
  
1. <span data-ttu-id="8e420-170">Войдите в портал Office 365 с учетной записью, назначенной роли безопасности администратора или администратора соответствия требованиям.</span><span class="sxs-lookup"><span data-stu-id="8e420-170">Sign into the Office 365 portal with an account that is assigned the Security Administrator or Compliance Administrator role.</span></span>
    
2. <span data-ttu-id="8e420-171">[Включение безопасности приложения Office 365 облака](https://support.office.com/article/ba919c73-d021-404d-9850-eec57e78678c).</span><span class="sxs-lookup"><span data-stu-id="8e420-171">[Turn on Office 365 Cloud App Security](https://support.office.com/article/ba919c73-d021-404d-9850-eec57e78678c).</span></span>
    
3. <span data-ttu-id="8e420-172">Просмотр [политик обнаружения неполадок в облаке приложения Office 365 безопасности](https://support.office.com/article/88935b4e-dcb1-47f1-8aca-1bf8fb069db6) уведомлений по электронной почте из непредвиденных шаблонов привилегированной административных действий.</span><span class="sxs-lookup"><span data-stu-id="8e420-172">Review your [Anomaly detection policies in Office 365 Cloud App Security](https://support.office.com/article/88935b4e-dcb1-47f1-8aca-1bf8fb069db6) to notify you by email of anomalous patterns of privileged administrative activity.</span></span> 
    
<span data-ttu-id="8e420-173">Чтобы добавить учетную запись пользователя для роли администраторов безопасности, [подключение к Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx#step3) с учетной записью выделенного глобального администратора и многофакторной проверкой Подлинности, заполните поля в имя участника-пользователя учетной записи пользователя и затем выполните следующие команды:</span><span class="sxs-lookup"><span data-stu-id="8e420-173">To add a user account to the Security Administrator role, [connect to Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx#step3) with a dedicated global administrator account and MFA, fill in the user principal name of the user account, and then run these commands:</span></span> 
  
```
$upn="<User principal name of the account>"
Add-MsolRoleMember -RoleMemberEmailAddress $upn -RoleName "Security Administrator"
```

<span data-ttu-id="8e420-174">Чтобы добавить учетную запись пользователя к роли администратора соответствия требованиям, заполните поля в имя участника-пользователя учетной записи пользователя и затем выполните следующие команды:</span><span class="sxs-lookup"><span data-stu-id="8e420-174">To add a user account to the Compliance Administrator role, fill in the user principal name of the user account, and then run these commands:</span></span>
  
```
$upn="<User principal name of the account>"
Add-MsolRoleMember -RoleMemberEmailAddress  $upn -RoleName "Compliance Administrator"
```

## <a name="additional-protections-for-enterprise-organizations"></a><span data-ttu-id="8e420-175">Дополнительные средства защиты для предприятий</span><span class="sxs-lookup"><span data-stu-id="8e420-175">Additional protections for enterprise organizations</span></span>

<span data-ttu-id="8e420-176">Шаги 1-3, чтобы убедиться, что учетная запись глобального администратора и конфигурацию, можно выполнить с помощью его с помощью эти дополнительные методы, которые безопасности.</span><span class="sxs-lookup"><span data-stu-id="8e420-176">After steps 1-3, use these additional methods to ensure that your global administrator account, and the configuration that you perform using it, are as secure as possible.</span></span>
  
### <a name="privileged-access-workstation-paw"></a><span data-ttu-id="8e420-177">Рабочая станция привилегированный доступ (ЛАПЕ)</span><span class="sxs-lookup"><span data-stu-id="8e420-177">Privileged Access Workstation (PAW)</span></span>

<span data-ttu-id="8e420-p118">Чтобы обеспечить максимальную безопасность выполнения задач с высоким уровнем привилегий, используйте ЛАПЕ. ЛАПЕ — это выделенный компьютер, который используется только для задач, конфиденциальные данные, такие как настройки Office 365, которому требуется учетная запись глобального администратора. Поскольку этот компьютер не используется для работы в Интернете или по электронной почте ежедневно, его лучше защищены от Интернет-атак и угроз.</span><span class="sxs-lookup"><span data-stu-id="8e420-p118">To ensure that the execution of highly privileged tasks is as secure as possible, use a PAW. A PAW is a dedicated computer that is only used for sensitive configuration tasks, such as Office 365 configuration that requires a global administrator account. Because this computer is not used daily for Internet browsing or email, it is better protected from Internet attacks and threats.</span></span>
  
<span data-ttu-id="8e420-181">За инструкциями по настройке ЛАПЕ [http://aka.ms/cyberpaw](http://aka.ms/cyberpaw).</span><span class="sxs-lookup"><span data-stu-id="8e420-181">For instructions on how to set up a PAW, see [http://aka.ms/cyberpaw](http://aka.ms/cyberpaw).</span></span>
  
### <a name="azure-ad-privileged-identity-management-pim"></a><span data-ttu-id="8e420-182">Управление удостоверениями Azure AD привилегиями (PIM)</span><span class="sxs-lookup"><span data-stu-id="8e420-182">Azure AD Privileged Identity Management (PIM)</span></span>

<span data-ttu-id="8e420-183">Вместо того, учетные записи глобального администратора без возможности восстановления назначить роль глобального администратора, можно использовать Azure AD PIM для включения по запросу, в время назначения роли глобального администратора, при необходимости.</span><span class="sxs-lookup"><span data-stu-id="8e420-183">Rather than having your global administrator accounts be permanently assigned the global administrator role, you can use Azure AD PIM to enable on-demand, just-in-time assignment of the global administrator role when it is needed.</span></span>
  
<span data-ttu-id="8e420-p119">Вместо глобального администратора учетных записей выполняется безвозвратная администратора они становятся подходящими администраторов. Роль глобального администратора неактивна пока кто-то должен. Завершите процесс активации, чтобы добавить роль глобального администратора учетной записи глобального администратора для предварительно определенный период времени. По истечении времени PIM Удаляет роль глобального администратора от учетной записи глобального администратора.</span><span class="sxs-lookup"><span data-stu-id="8e420-p119">Instead of your global administrator accounts being a permanent admin, they become eligible administrators. The global administrator role is inactive until someone needs it. You then complete an activation process to add the global administrator role to the global administrator account for a predetermined amount of time. When the time expires, PIM removes the global administrator role from the global administrator account.</span></span>
  
<span data-ttu-id="8e420-188">С помощью PIM и этот процесс значительно сокращает время, учетные записи глобального администратора уязвимы для атак и использования пользователями.</span><span class="sxs-lookup"><span data-stu-id="8e420-188">Using PIM and this process significantly reduces the amount of time that your global administrator accounts are vulnerable to attack and use by malicious users.</span></span>
  
<span data-ttu-id="8e420-189">Дополнительные сведения можно [настроить Azure AD привилегированной управления удостоверениями](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure).</span><span class="sxs-lookup"><span data-stu-id="8e420-189">For more information, see [Configure Azure AD Privileged Identity Management](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure).</span></span>
  
> [!NOTE]
> <span data-ttu-id="8e420-190">PIM доступна с Azure Active Directory Premium P2, который входит в состав корпоративной мобильности + E5 безопасности (Командной), или вы можете приобрести индивидуальных лицензий для учетные записи глобального администратора.</span><span class="sxs-lookup"><span data-stu-id="8e420-190">PIM is available with Azure Active Directory Premium P2, which is included with Enterprise Mobility + Security (EMS) E5, or you can purchase individual licenses for your global administrator accounts.</span></span> 
  
### <a name="security-information-and-event-management-siem-software-for-office-365-logging"></a><span data-ttu-id="8e420-191">Сведения и события управления (SIEM) программное обеспечение безопасности для входа в Office 365</span><span class="sxs-lookup"><span data-stu-id="8e420-191">Security information and event management (SIEM) software for Office 365 logging</span></span>

<span data-ttu-id="8e420-p120">Программное обеспечение SIEM размещать на сервере выполняет анализ в реальном времени оповещение системы безопасности и события, созданные приложениями и сетевого оборудования. Чтобы разрешить SIEM сервера для включения оповещение системы безопасности Office 365 и события в анализа и создания отчетов, интегрируйте их в SIEM в системе:</span><span class="sxs-lookup"><span data-stu-id="8e420-p120">SIEM software run on a server performs real-time analysis of security alerts and events created by applications and network hardware. To allow your SIEM server to include Office 365 security alerts and events in its analysis and reporting functions, integrate these in your SIEM system:</span></span>
  
- <span data-ttu-id="8e420-194">Azure AD</span><span class="sxs-lookup"><span data-stu-id="8e420-194">Azure AD</span></span>
    
    <span data-ttu-id="8e420-195">Для получения дополнительных сведений см.: [Журналы интеграция с Azure ресурсы в вашей системы SIEM](https://docs.microsoft.com/azure/security/security-azure-log-integration-overview).</span><span class="sxs-lookup"><span data-stu-id="8e420-195">For more information, see [Integrate logs from Azure resources into your SIEM systems](https://docs.microsoft.com/azure/security/security-azure-log-integration-overview).</span></span>
    
- <span data-ttu-id="8e420-196">Office 365 Cloud App Security</span><span class="sxs-lookup"><span data-stu-id="8e420-196">Office 365 Cloud App Security</span></span>
    
    <span data-ttu-id="8e420-197">Дополнительные сведения можно [интегрировать SIEM сервера с помощью приложения облаке Безопасность в Office 365](https://support.office.com/article/dd6d2417-49c4-4de6-9294-67fdabbf8532).</span><span class="sxs-lookup"><span data-stu-id="8e420-197">For more information, see [Integrate your SIEM server with Office 365 Cloud App Security](https://support.office.com/article/dd6d2417-49c4-4de6-9294-67fdabbf8532).</span></span>
    
## <a name="next-step"></a><span data-ttu-id="8e420-198">Следующее действие</span><span class="sxs-lookup"><span data-stu-id="8e420-198">Next step</span></span>

<span data-ttu-id="8e420-199">Просмотрите [рекомендации по обеспечению безопасности для Office 365](https://support.office.com/article/9295e396-e53d-49b9-ae9b-0b5828cdedc3).</span><span class="sxs-lookup"><span data-stu-id="8e420-199">See [Security best practices for Office 365](https://support.office.com/article/9295e396-e53d-49b9-ae9b-0b5828cdedc3).</span></span>
  

