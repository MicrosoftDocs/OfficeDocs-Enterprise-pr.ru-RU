---
title: Безопасность в корпорации Contoso
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 8f6f9894-5394-4110-8b0a-b8765028c10b
description: 'Сводка: Сведения о как Contoso сопоставлены своих требований к безопасности функции в облаке и услуги корпорации Майкрософт и определить пути в облако проверки готовности к безопасности.'
ms.openlocfilehash: 722c01995c95c36b9975b0682858c38063f79d2c
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/21/2018
ms.locfileid: "22914834"
---
# <a name="security-for-the-contoso-corporation"></a><span data-ttu-id="de5b5-103">Безопасность в корпорации Contoso</span><span class="sxs-lookup"><span data-stu-id="de5b5-103">Security for the Contoso Corporation</span></span>

 <span data-ttu-id="de5b5-104">**Сводка:** Понимаете, как Contoso сопоставлен функции в облаке и услуги корпорации Майкрософт своих требований к безопасности и определить пути в облако проверки готовности к безопасности.</span><span class="sxs-lookup"><span data-stu-id="de5b5-104">**Summary:** Understand how Contoso mapped their security requirements to features in Microsoft's cloud offerings and determined a path to cloud security readiness.</span></span>
  
<span data-ttu-id="de5b5-p101">Contoso — серьезные об их сведения о безопасности и защиты. При переводе их ИТ-инфраструктуру для облачных включительно один, они выполняет проверку того, что их требования к безопасности в локальной поддерживались и реализации в облаке и услуги корпорации Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="de5b5-p101">Contoso is serious about their information security and protection. When transitioning their IT infrastructure to a cloud-inclusive one, they made sure that their on-premises security requirements were supported and implemented in Microsoft's cloud offerings.</span></span>
  
## <a name="contosos-security-requirements-in-the-cloud"></a><span data-ttu-id="de5b5-107">Требования к безопасности Contoso в облаке</span><span class="sxs-lookup"><span data-stu-id="de5b5-107">Contoso's security requirements in the cloud</span></span>

<span data-ttu-id="de5b5-108">Требования компании Contoso к безопасности в облаке:</span><span class="sxs-lookup"><span data-stu-id="de5b5-108">Here are Contoso's security requirements for the cloud:</span></span>
  
- <span data-ttu-id="de5b5-109">Строгая проверка подлинности при доступе к облачным ресурсам.</span><span class="sxs-lookup"><span data-stu-id="de5b5-109">Strong authentication to cloud resources</span></span>
    
    <span data-ttu-id="de5b5-110">При доступе к облачным ресурсам требуется проверка подлинности, причем (по возможности) многофакторная.</span><span class="sxs-lookup"><span data-stu-id="de5b5-110">Cloud resource access must be authenticated and, where possible, leverage multi-factor authentication.</span></span>
    
- <span data-ttu-id="de5b5-111">Шифрование интернет-трафика.</span><span class="sxs-lookup"><span data-stu-id="de5b5-111">Encryption for traffic across the Internet</span></span>
    
    <span data-ttu-id="de5b5-p102">Никакие данные не должны передаваться через Интернет в виде обычного текста. Всегда должны использоваться подключения HTTPS, IPsec или другие комплексные решения для шифрования данных.</span><span class="sxs-lookup"><span data-stu-id="de5b5-p102">No data sent across the Internet is in plain text form. Always use HTTPS connections, IPsec, or other end-to-end data encryption methods.</span></span>
    
- <span data-ttu-id="de5b5-114">Шифрование неактивных данных в облаке.</span><span class="sxs-lookup"><span data-stu-id="de5b5-114">Encryption for data at rest in the cloud</span></span>
    
    <span data-ttu-id="de5b5-115">Все данные, хранящиеся на дисках или в другом месте в облаке, должны быть зашифрованы.</span><span class="sxs-lookup"><span data-stu-id="de5b5-115">All data stored on disks or elsewhere in the cloud must be in an encrypted form.</span></span>
    
- <span data-ttu-id="de5b5-116">ACL для минимальных прав доступа.</span><span class="sxs-lookup"><span data-stu-id="de5b5-116">ACLs for least privilege access</span></span>
    
    <span data-ttu-id="de5b5-117">Разрешения на доступ учетных записей к ресурсам в облаке и на действия с этими ресурсами должны соответствовать рекомендациям относительно минимальных прав доступа.</span><span class="sxs-lookup"><span data-stu-id="de5b5-117">Account permissions to access resources in the cloud and what they are allowed to do must follow least-privilege guidelines.</span></span>
    
## <a name="contosos-data-sensitivity-classification"></a><span data-ttu-id="de5b5-118">Уровень конфиденциальности сообщения классификации данных Contoso</span><span class="sxs-lookup"><span data-stu-id="de5b5-118">Contoso's data sensitivity classification</span></span>

<span data-ttu-id="de5b5-119">Использование данных в корпорации Майкрософт [Toolkit классификации данных](https://msdn.microsoft.com/library/hh204743.aspx), Contoso провел анализ данных и определить следующие уровни.</span><span class="sxs-lookup"><span data-stu-id="de5b5-119">Using the information in Microsoft's [Data Classification Toolkit](https://msdn.microsoft.com/library/hh204743.aspx), Contoso performed an analysis of their data and determined the following levels.</span></span>
  
|<span data-ttu-id="de5b5-120">**Уровень 1. Низкая ценность для бизнеса**</span><span class="sxs-lookup"><span data-stu-id="de5b5-120">**Level 1: Low business value**</span></span>|<span data-ttu-id="de5b5-121">**Уровень 2. Средняя ценность для бизнеса**</span><span class="sxs-lookup"><span data-stu-id="de5b5-121">**Level 2: Medium business value**</span></span>|<span data-ttu-id="de5b5-122">**Уровень 3. Высокая ценность для бизнеса**</span><span class="sxs-lookup"><span data-stu-id="de5b5-122">**Level 3: High business value**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="de5b5-123">Данные шифруются и доступны только пользователям, прошедшим проверку подлинности.

</span><span class="sxs-lookup"><span data-stu-id="de5b5-123">Data is encrypted and available only to authenticated users</span></span>  <br/> <span data-ttu-id="de5b5-p103">Предоставляется для всех данных, хранящихся локально и в облачном хранилище, а также рабочих нагрузок, таких как в Office 365. Данные шифруются при хранении в службе и при перемещении между службой и клиентским устройством.</span><span class="sxs-lookup"><span data-stu-id="de5b5-p103">Provided for all data stored on premises and in cloud-based storage and workloads, such as Office 365. Data is encrypted while it resides in the service and in transit between the service and client devices.</span></span>  <br/> <span data-ttu-id="de5b5-126">Примеры данных уровня 1 — это обычный обмен деловой информацией (электронная почта) и файлы для администраторов, а также специалистов по продажам и поддержке.</span><span class="sxs-lookup"><span data-stu-id="de5b5-126">Examples of Level 1 data are normal business communications (email) and files for administrative, sales, and support workers.</span></span>  <br/> |<span data-ttu-id="de5b5-127">Уровень 1, а также строгая проверка подлинности и защита от потери данных.
</span><span class="sxs-lookup"><span data-stu-id="de5b5-127">Level 1 plus strong authentication and data loss protection</span></span>  <br/> <span data-ttu-id="de5b5-p104">Строгая проверка подлинности включает многофакторную проверку подлинности с проверкой при помощи SMS. Защита от потери данных гарантирует, что конфиденциальные и критически важные данные не попадут за пределы локальной сети.
</span><span class="sxs-lookup"><span data-stu-id="de5b5-p104">Strong authentication includes multi-factor authentication with SMS validation. Data loss prevention ensures that sensitive or critical information does not travel outside the on-premises network.</span></span>  <br/> <span data-ttu-id="de5b5-130">Примеры данных уровня 2 — финансовые и юридические сведения, а также данные об исследованиях и разработке новых продуктов.</span><span class="sxs-lookup"><span data-stu-id="de5b5-130">Examples of Level 2 data are financial and legal information and research and development data for new products.</span></span>  <br/> |<span data-ttu-id="de5b5-131">Уровень 2, а также самые высокие уровни шифрования, проверки подлинности и аудита.
</span><span class="sxs-lookup"><span data-stu-id="de5b5-131">Level 2 plus the highest levels of encryption, authentication, and auditing</span></span>  <br/> <span data-ttu-id="de5b5-132">Самые высокие уровни шифрования хранящихся данных и данных в облаке, которые соответствуют региональным нормативам, в сочетании с многофакторной проверкой подлинности с использованием смарт-карт, детального аудита и оповещений.
</span><span class="sxs-lookup"><span data-stu-id="de5b5-132">The highest levels of encryption for data at rest and in the cloud, compliant with regional regulations, combined with multi-factor authentication with smart cards and granular auditing and alerting.</span></span>  <br/> <span data-ttu-id="de5b5-133">Примеры данных уровня 3 — личные сведения клиентов и партнеров, а также технические характеристики продуктов и защищаемые методы производства.</span><span class="sxs-lookup"><span data-stu-id="de5b5-133">Examples of Level 3 data are customer and partner personally identifiable information and product engineering specifications and proprietary manufacturing techniques.</span></span>  <br/> |
   
## <a name="mapping-microsoft-cloud-offerings-and-features-to-contosos-data-levels"></a><span data-ttu-id="de5b5-134">Сопоставление облака Microsoft и функции уровней данных Contoso</span><span class="sxs-lookup"><span data-stu-id="de5b5-134">Mapping Microsoft cloud offerings and features to Contoso's data levels</span></span>

<span data-ttu-id="de5b5-135">В приведенной ниже таблице показано сопоставление уровней данных Contoso с функциями облачных решений Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="de5b5-135">The following table shows the mapping of Contoso's data levels to features in Microsoft's cloud offerings:</span></span>
  
||<span data-ttu-id="de5b5-136">**SaaS**</span><span class="sxs-lookup"><span data-stu-id="de5b5-136">**SaaS**</span></span>|<span data-ttu-id="de5b5-137">**Azure PaaS**</span><span class="sxs-lookup"><span data-stu-id="de5b5-137">**Azure PaaS**</span></span>|<span data-ttu-id="de5b5-138">**Azure IaaS**</span><span class="sxs-lookup"><span data-stu-id="de5b5-138">**Azure IaaS**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="de5b5-139">Уровень 1. Низкая ценность для бизнеса</span><span class="sxs-lookup"><span data-stu-id="de5b5-139">Level 1: Low business value</span></span>  <br/> | <span data-ttu-id="de5b5-140">Протокол HTTPS для всех подключений
</span><span class="sxs-lookup"><span data-stu-id="de5b5-140">HTTPS for all connections</span></span> <br/>  <span data-ttu-id="de5b5-141">Шифрование статических данных</span><span class="sxs-lookup"><span data-stu-id="de5b5-141">Encryption at rest</span></span> <br/> | <span data-ttu-id="de5b5-142">Поддержка только HTTPS-подключений
</span><span class="sxs-lookup"><span data-stu-id="de5b5-142">Support only HTTPS connections</span></span> <br/>  <span data-ttu-id="de5b5-143">Шифрование файлов, хранящихся в Azure</span><span class="sxs-lookup"><span data-stu-id="de5b5-143">Encrypt files stored in Azure</span></span> <br/> | <span data-ttu-id="de5b5-144">Требуется протокол HTTPS или IPsec для доступа к серверу
</span><span class="sxs-lookup"><span data-stu-id="de5b5-144">Require HTTPS or IPsec for server access</span></span> <br/>  <span data-ttu-id="de5b5-145">Шифрование диска Azure</span><span class="sxs-lookup"><span data-stu-id="de5b5-145">Azure disk encryption</span></span> <br/> |
|<span data-ttu-id="de5b5-146">Уровень 2. Средняя ценность для бизнеса</span><span class="sxs-lookup"><span data-stu-id="de5b5-146">Level 2: Medium business value</span></span>  <br/> | <span data-ttu-id="de5b5-147">Многофакторная идентификация Azure AD с использованием SMS-сообщений</span><span class="sxs-lookup"><span data-stu-id="de5b5-147">Azure AD multi-factor authentication (MFA) with SMS</span></span> <br/> | <span data-ttu-id="de5b5-148">Использование хранилища ключей Azure для ключей шифрования
</span><span class="sxs-lookup"><span data-stu-id="de5b5-148">Use Azure Key Vault for encryption keys</span></span> <br/>  <span data-ttu-id="de5b5-149">MFA Azure AD с использованием SMS-сообщений</span><span class="sxs-lookup"><span data-stu-id="de5b5-149">Azure AD MFA with SMS</span></span> <br/> | <span data-ttu-id="de5b5-150">MFA с использованием SMS-сообщений</span><span class="sxs-lookup"><span data-stu-id="de5b5-150">MFA with SMS</span></span> <br/> |
|<span data-ttu-id="de5b5-151">Уровень 3. Высокая ценность для бизнеса</span><span class="sxs-lookup"><span data-stu-id="de5b5-151">Level 3: High business value</span></span>  <br/> | <span data-ttu-id="de5b5-152">Azure RMS</span><span class="sxs-lookup"><span data-stu-id="de5b5-152">Azure Rights Management System (RMS)</span></span> <br/>  <span data-ttu-id="de5b5-153">MFA Azure AD с использованием смарт-карт</span><span class="sxs-lookup"><span data-stu-id="de5b5-153">Azure AD MFA with smart cards</span></span> <br/>  <span data-ttu-id="de5b5-154">Условный доступ к Intune</span><span class="sxs-lookup"><span data-stu-id="de5b5-154">Intune conditional access</span></span> <br/> | <span data-ttu-id="de5b5-155">Azure RMS;</span><span class="sxs-lookup"><span data-stu-id="de5b5-155">Azure RMS</span></span> <br/>  <span data-ttu-id="de5b5-156">MFA Azure AD с использованием смарт-карт</span><span class="sxs-lookup"><span data-stu-id="de5b5-156">Azure AD MFA with smart cards</span></span> <br/> | <span data-ttu-id="de5b5-157">MFA с использованием смарт-карт</span><span class="sxs-lookup"><span data-stu-id="de5b5-157">MFA with smart cards</span></span> <br/> |
   
## <a name="contosos-information-policies"></a><span data-ttu-id="de5b5-158">Сведения о политиках Contoso</span><span class="sxs-lookup"><span data-stu-id="de5b5-158">Contoso's information policies</span></span>

<span data-ttu-id="de5b5-159">В приведенной ниже таблице указаны информационные политики Contoso.</span><span class="sxs-lookup"><span data-stu-id="de5b5-159">The following table lists Contoso's information policies.</span></span>
  
||<span data-ttu-id="de5b5-160">**Access**</span><span class="sxs-lookup"><span data-stu-id="de5b5-160">**Access**</span></span>|<span data-ttu-id="de5b5-161">**Хранение данных**</span><span class="sxs-lookup"><span data-stu-id="de5b5-161">**Data retention**</span></span>|<span data-ttu-id="de5b5-162">**Защита информации**</span><span class="sxs-lookup"><span data-stu-id="de5b5-162">**Information protection**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="de5b5-163">Уровень 1. Низкая ценность для бизнеса</span><span class="sxs-lookup"><span data-stu-id="de5b5-163">Level 1: Low business value</span></span>  <br/> | <span data-ttu-id="de5b5-164">Предоставление доступа всем пользователям</span><span class="sxs-lookup"><span data-stu-id="de5b5-164">Allow access to all</span></span> <br/> |<span data-ttu-id="de5b5-165">6 месяцев</span><span class="sxs-lookup"><span data-stu-id="de5b5-165">6 months</span></span>  <br/> |<span data-ttu-id="de5b5-166">Применение шифрования</span><span class="sxs-lookup"><span data-stu-id="de5b5-166">Use encryption</span></span>  <br/> |
|<span data-ttu-id="de5b5-167">Уровень 2. Средняя ценность для бизнеса</span><span class="sxs-lookup"><span data-stu-id="de5b5-167">Level 2: Medium business value</span></span>  <br/> | <span data-ttu-id="de5b5-168">Предоставление доступа сотрудникам, субподрядчикам и партнерам компании Contoso
</span><span class="sxs-lookup"><span data-stu-id="de5b5-168">Allow access to Contoso employees, subcontractors, and partners</span></span> <br/>  <span data-ttu-id="de5b5-169">Использование MFA, TLS и MAM</span><span class="sxs-lookup"><span data-stu-id="de5b5-169">Use MFA, TLS, and MAM</span></span> <br/> |<span data-ttu-id="de5b5-170">2 года</span><span class="sxs-lookup"><span data-stu-id="de5b5-170">2 years</span></span>  <br/> |<span data-ttu-id="de5b5-171">Использование хэш-значений для обеспечения целостности данных</span><span class="sxs-lookup"><span data-stu-id="de5b5-171">Use hash values for data integrity</span></span>  <br/> |
|<span data-ttu-id="de5b5-172">Уровень 3. Высокая ценность для бизнеса</span><span class="sxs-lookup"><span data-stu-id="de5b5-172">Level 3: High business value</span></span>  <br/> | <span data-ttu-id="de5b5-173">Предоставление доступа руководителям и ведущим сотрудникам инженерного и производственного отделов
</span><span class="sxs-lookup"><span data-stu-id="de5b5-173">Allow access to executives and leads in engineering and manufacturing</span></span> <br/>  <span data-ttu-id="de5b5-174">RMS только с управляемыми сетевыми устройствами</span><span class="sxs-lookup"><span data-stu-id="de5b5-174">RMS with managed network devices only</span></span> <br/> |<span data-ttu-id="de5b5-175">7 лет</span><span class="sxs-lookup"><span data-stu-id="de5b5-175">7 years</span></span>  <br/> |<span data-ttu-id="de5b5-176">Использование цифровых подписей для обеспечения неотрекаемости</span><span class="sxs-lookup"><span data-stu-id="de5b5-176">Use digital signatures for non-repudiation</span></span>  <br/> |
   
## <a name="contosos-path-to-cloud-security-readiness"></a><span data-ttu-id="de5b5-177">Contoso путь для проверки готовности к безопасности облако</span><span class="sxs-lookup"><span data-stu-id="de5b5-177">Contoso's path to cloud security readiness</span></span>

<span data-ttu-id="de5b5-178">Подготовка инфраструктуры безопасности Contoso для работы с Microsoft Cloud включает в себя следующие этапы:</span><span class="sxs-lookup"><span data-stu-id="de5b5-178">Contoso used the following steps to ready their security for the Microsoft cloud:</span></span>
  
1. <span data-ttu-id="de5b5-179">Оптимизация учетных записей администраторов для облака.
</span><span class="sxs-lookup"><span data-stu-id="de5b5-179">Optimize administrator accounts for the cloud</span></span>
    
    <span data-ttu-id="de5b5-180">Компания Contoso провела обширную проверку существующих учетных записей администраторов Windows Server AD и настроила ряд учетных записей администраторов и групп в облаке.</span><span class="sxs-lookup"><span data-stu-id="de5b5-180">Contoso did an extensive review of the existing Windows Server AD administrator accounts and set up a series of cloud administrator accounts and groups.</span></span>
    
2. <span data-ttu-id="de5b5-181">Классификация данных с разделением их на три уровня.
</span><span class="sxs-lookup"><span data-stu-id="de5b5-181">Perform data classification analysis into three levels</span></span>
    
    <span data-ttu-id="de5b5-182">Contoso выполнена тщательной проверки и определить три уровня, который был использован для определения облаке Майкрософт предлагает возможности для защиты данных наиболее ценных Contoso.</span><span class="sxs-lookup"><span data-stu-id="de5b5-182">Contoso performed a careful review and determined the three levels, which was used to determine the Microsoft cloud offering features to protect Contoso's most valuable data.</span></span>
    
3. <span data-ttu-id="de5b5-183">Определение политик защиты информации, политик доступа к ней и ее хранения согласно уровням данных.
</span><span class="sxs-lookup"><span data-stu-id="de5b5-183">Determine access, retention, and information protection policies for data levels</span></span>
    
    <span data-ttu-id="de5b5-184">Учитывая уровни данных, компания Contoso определила подробные требования, которые будут применяться для будущих рабочих ИТ-нагрузок, перемещаемых в облако.</span><span class="sxs-lookup"><span data-stu-id="de5b5-184">Based on the data levels, Contoso determined detailed requirements, which will be used to qualify future IT workloads being moved to the cloud.</span></span>
    
## <a name="contosos-use-of-office-365-security-best-practices"></a><span data-ttu-id="de5b5-185">Использование Contoso рекомендации по обеспечению безопасности Office 365</span><span class="sxs-lookup"><span data-stu-id="de5b5-185">Contoso's use of Office 365 security best practices</span></span>

<span data-ttu-id="de5b5-186">В соответствии с Office 365 рекомендации по обеспечению безопасности администраторов и ИТ-подразделения организации Contoso развернули следующее:</span><span class="sxs-lookup"><span data-stu-id="de5b5-186">In accordance with Office 365 security best practices, Contoso's security administrators and IT department have deployed the following:</span></span>
  
- <span data-ttu-id="de5b5-187">**Выделенные учетные записи глобального администратора с очень надежных паролей**</span><span class="sxs-lookup"><span data-stu-id="de5b5-187">**Dedicated global administrator accounts with very strong passwords**</span></span>
    
    <span data-ttu-id="de5b5-p105">Не назначить роль глобального администратора повседневных учетных записей, Contoso имеет создать три, выделенные учетные записи глобального администратора с очень надежных паролей. Вход с учетной записью глобального администратора выполняется только для определенных административных задач и паролей только известно, назначенного персонала. Администраторы безопасности организации Contoso назначены роли администраторов учетных записей, которые подходят для работы этого лица ИТ и ответственности.</span><span class="sxs-lookup"><span data-stu-id="de5b5-p105">Rather than assign the global admin role to everyday user accounts, Contoso has create three, dedicated global administrator accounts with very strong passwords. Signing in with a global administrator account is only done for specific administrative tasks and the passwords are only known to designated staff. Contoso's security administrators have assigned admin roles to accounts that are appropriate to that IT person's job function and responsibility.</span></span>
    
    <span data-ttu-id="de5b5-191">Дополнительные сведения см в [роли администраторов об Office 365](https://support.office.com/article/About-Office-365-admin-roles-da585eea-f576-4f55-a1e0-87090b6aaa9d).</span><span class="sxs-lookup"><span data-stu-id="de5b5-191">For more information, see [About Office 365 admin roles](https://support.office.com/article/About-Office-365-admin-roles-da585eea-f576-4f55-a1e0-87090b6aaa9d).</span></span>
    
- <span data-ttu-id="de5b5-192">**Многофакторная проверка подлинности (многофакторной проверкой Подлинности) для важные учетные записи**</span><span class="sxs-lookup"><span data-stu-id="de5b5-192">**Multi-factor authentication (MFA) for important user accounts**</span></span>
    
    <span data-ttu-id="de5b5-p106">Многофакторной проверкой Подлинности добавляет дополнительный уровень защиты, процесс входа, требуя от пользователей для подтверждения на телефонный звонок, текстовое сообщение или уведомление приложения на своем телефоне смарт-после правильно ввода пароля. С многофакторной проверкой Подлинности учетными записями пользователей Office 365, защищены от несанкционированного входа в систему даже в том случае, если раскрыты пароля учетной записи.</span><span class="sxs-lookup"><span data-stu-id="de5b5-p106">MFA adds an additional layer of protection to the sign-in process by requiring users to acknowledge a phone call, text message, or an app notification on their smart phone after correctly entering their password. With MFA, Office 365 user accounts are protected against unauthorized sign-in even if an account password is compromised.</span></span>
    
  - <span data-ttu-id="de5b5-195">Для защиты от компрометации подписки на Office 365 Contoso включить многофакторной проверкой Подлинности на все три учетные записи глобального администратора.</span><span class="sxs-lookup"><span data-stu-id="de5b5-195">To protect against a compromise of the Office 365 subscription, Contoso enabled MFA on all three global administrator accounts.</span></span>
    
  - <span data-ttu-id="de5b5-196">Для защиты от фишинга, в которых он снижает учетные данные доверенные лица в организации и отправляет сообщение о нежелательном сообщения электронной почты, Contoso включен многофакторной проверкой Подлинности на все учетные записи пользователей для руководителей, включая исполнительный персонала.</span><span class="sxs-lookup"><span data-stu-id="de5b5-196">To protect against phishing attacks, in which an attacker compromises the credentials of a trusted person in the organization and sends malicious emails, Contoso enabled MFA on all user accounts for managers, including the executive staff.</span></span>
    
    <span data-ttu-id="de5b5-197">Дополнительные сведения можно [спланировать многофакторной проверки подлинности для развертываний Office 365](https://support.office.com/article/Plan-for-multifactor-authentication-for-Office-365-Deployments-043807b2-21db-4d5c-b430-c8a6dee0e6ba)</span><span class="sxs-lookup"><span data-stu-id="de5b5-197">For more information, see [Plan for multi-factor authentication for Office 365 Deployments](https://support.office.com/article/Plan-for-multifactor-authentication-for-Office-365-Deployments-043807b2-21db-4d5c-b430-c8a6dee0e6ba)</span></span>
    
- <span data-ttu-id="de5b5-198">**Управление повышенной безопасности (ASM)**</span><span class="sxs-lookup"><span data-stu-id="de5b5-198">**Advanced Security Management (ASM)**</span></span>
    
    <span data-ttu-id="de5b5-p107">ASM использует настроенные политики для наблюдения за непредвиденных активности. Настройка оповещений с помощью ASM, чтобы ИТ-администраторы будут уведомлены об активности пользователей необычных или рискующий, такие как загрузка больших объемов данных, администраторов безопасности Contoso несколькими сбой попыток входа или войти в систему с неизвестными или опасные IP-адресов</span><span class="sxs-lookup"><span data-stu-id="de5b5-p107">ASM uses configured policies to monitor for anomalous activity. Contoso security administrators set up alerts with ASM so that IT administrators are notified of unusual or risky user activity, such as downloading large amounts of data, multiple failed sign-in attempts, or sign-ins from unknown or dangerous IP addresses</span></span>
    
    <span data-ttu-id="de5b5-201">Для получения дополнительных сведений см [Overview of расширенного управления безопасностью в Office 365 ](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475).</span><span class="sxs-lookup"><span data-stu-id="de5b5-201">For more information, see [Overview of Advanced Security Management in Office 365 ](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475).</span></span>
    
- <span data-ttu-id="de5b5-202">**Ведение журнала аудита потока защиты электронной почты и почтовых ящиков**</span><span class="sxs-lookup"><span data-stu-id="de5b5-202">**Secure email flow and mailbox audit logging**</span></span>
    
    <span data-ttu-id="de5b5-p108">Для защиты от неизвестного вредоносных программ, вирусов и вредоносного URL-адреса, передаваемых через по электронной почте специалистов по безопасности Contoso используется Exchange Online Protection и расширенный угроз защиты анализа. Contoso имеет также включено ведения журнала аудита для определения, который был выполнен вход в почтовые ящики пользователей, отправленные сообщения и других действий, выполняемых с владельца почтового ящика, делегированный пользователь или администратор.</span><span class="sxs-lookup"><span data-stu-id="de5b5-p108">Contoso security specialists are using Exchange Online Protection and Advanced Threat Protection (ATP) to protect against unknown malware, viruses, and malicious URLs transmitted through emails. Contoso has also enabled mailbox audit logging to determine who has logged into user mailboxes, sent messages, and other activities performed by the mailbox owner, a delegated user, or an administrator.</span></span>
    
    <span data-ttu-id="de5b5-205">Дополнительные сведения см. в следующих разделах:</span><span class="sxs-lookup"><span data-stu-id="de5b5-205">For more information, see:</span></span> 
    
  - [<span data-ttu-id="de5b5-206">Защита от спама в Office 365</span><span class="sxs-lookup"><span data-stu-id="de5b5-206">Office 365 Email Anti-Spam Protection</span></span>](https://support.office.com/article/Office-365-Email-AntiSpam-Protection-6a601501-a6a8-4559-b2e7-56b59c96a586)
    
  - [<span data-ttu-id="de5b5-207">Дополнительная защита от угроз для безопасных вложений и ссылок</span><span class="sxs-lookup"><span data-stu-id="de5b5-207">Advanced threat protection for safe attachments and safe links</span></span>](https://technet.microsoft.com/library/mt148491.aspx)
    
  - [<span data-ttu-id="de5b5-208">Включение аудита почтовых ящиков в Office 365</span><span class="sxs-lookup"><span data-stu-id="de5b5-208">Enable mailbox auditing in Office 365</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=626109)
    
- <span data-ttu-id="de5b5-209">**Защита от потери данных (DLP)**</span><span class="sxs-lookup"><span data-stu-id="de5b5-209">**Data Loss Prevention (DLP)**</span></span>
    
    <span data-ttu-id="de5b5-210">Contoso определяемую конфиденциальные данные и настройки политики защиты от потери данных для Exchange Online, SharePoint Online и OneDrive для предотвращения пользователи случайно или специально общего доступа к данным.</span><span class="sxs-lookup"><span data-stu-id="de5b5-210">Contoso has identified its sensitive data and configured DLP policies for Exchange Online, SharePoint Online, and OneDrive to help prevent users from accidentally or intentionally sharing the data.</span></span> 
    
    <span data-ttu-id="de5b5-211">Подробнее см. в статье [Обзор политик защиты от потери данных](https://support.office.com/article/Overview-of-data-loss-prevention-policies-1966b2a7-d1e2-4d92-ab61-42efbb137f5e).</span><span class="sxs-lookup"><span data-stu-id="de5b5-211">For more information, see [Overview of data loss prevention policies](https://support.office.com/article/Overview-of-data-loss-prevention-policies-1966b2a7-d1e2-4d92-ab61-42efbb137f5e).</span></span>
    
## <a name="see-also"></a><span data-ttu-id="de5b5-212">See Also</span><span class="sxs-lookup"><span data-stu-id="de5b5-212">See Also</span></span>

[<span data-ttu-id="de5b5-213">Contoso в Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="de5b5-213">Contoso in the Microsoft Cloud</span></span>](contoso-in-the-microsoft-cloud.md)
  
[<span data-ttu-id="de5b5-214">Ресурсы для администраторов, посвященные архитектуре Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="de5b5-214">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="de5b5-215">Стратегия Enterprise Cloud корпорации Майкрософт: ресурсы для лиц, принимающих решения в области ИТ</span><span class="sxs-lookup"><span data-stu-id="de5b5-215">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)
  
[<span data-ttu-id="de5b5-216">Рекомендации по обеспечению безопасности в Office 365</span><span class="sxs-lookup"><span data-stu-id="de5b5-216">Security best practices for Office 365</span></span>](https://support.office.com/article/Security-best-practices-for-Office-365-9295e396-e53d-49b9-ae9b-0b5828cdedc3)




