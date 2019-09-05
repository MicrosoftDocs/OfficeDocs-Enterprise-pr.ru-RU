---
title: Как настроить локальное развертывание Skype для бизнеса для использования гибридной современной проверки подлинности
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/4/2018
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 522d5cec-4e1b-4cc3-937f-293570717bc6
ms.collection:
- M365-security-compliance
description: Современная проверка подлинности — это способ управления удостоверениями, обеспечивающий более надежную проверку подлинности и авторизацию пользователей, доступный для локального сервера Skype для бизнеса Server и для локального сервера Exchange Server, а также для гибридной среды Skype для бизнеса.
ms.openlocfilehash: 4a49885fc6276f180872facb777bfe5a5adb61ee
ms.sourcegitcommit: f9b5e029ed427b7c15cbfb6231a9259b34c9436f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/05/2019
ms.locfileid: "36759687"
---
# <a name="how-to-configure-skype-for-business-on-premises-to-use-hybrid-modern-authentication"></a><span data-ttu-id="fa25a-103">Как настроить локальное развертывание Skype для бизнеса для использования гибридной современной проверки подлинности</span><span class="sxs-lookup"><span data-stu-id="fa25a-103">How to configure Skype for Business on-premises to use Hybrid Modern Authentication</span></span>

<span data-ttu-id="fa25a-104">Современная проверка подлинности — это способ управления удостоверениями, обеспечивающий более надежную проверку подлинности и авторизацию пользователей, доступный для локального сервера Skype для бизнеса Server и для локального сервера Exchange Server, а также для гибридной среды Skype для бизнеса.</span><span class="sxs-lookup"><span data-stu-id="fa25a-104">Modern Authentication, is a method of identity management that offers more secure user authentication and authorization, is available for Skype for Business server on-premises and Exchange server on-premises, as well as split-domain Skype for Business hybrids.</span></span>
  
 <span data-ttu-id="fa25a-105">**Важно!** Хотите узнать больше о современной проверке подлинности (MA) и зачем использовать ее в вашей компании или Организации?</span><span class="sxs-lookup"><span data-stu-id="fa25a-105">**Important** Would you like to know more about Modern Authentication (MA) and why you might prefer to use it in your company or organization?</span></span> <span data-ttu-id="fa25a-106">Просмотрите [этот документ](hybrid-modern-auth-overview.md) , чтобы получить обзор.</span><span class="sxs-lookup"><span data-stu-id="fa25a-106">Check [this document](hybrid-modern-auth-overview.md) for an overview.</span></span> <span data-ttu-id="fa25a-107">Если вам нужно знать, какие топологии Skype для бизнеса поддерживаются в MA, это задокументировано здесь!</span><span class="sxs-lookup"><span data-stu-id="fa25a-107">If you need to know what Skype for Business topologies are supported with MA, that's documented here!</span></span> 
  
 <span data-ttu-id="fa25a-108">**Прежде чем начать**, я вызываю:</span><span class="sxs-lookup"><span data-stu-id="fa25a-108">**Before we begin**, I call:</span></span> 
  
- <span data-ttu-id="fa25a-109">Современная Проверка \> подлинности MA</span><span class="sxs-lookup"><span data-stu-id="fa25a-109">Modern Authentication \> MA</span></span>
    
- <span data-ttu-id="fa25a-110">Гибридная современная \> проверка подлинности HMA</span><span class="sxs-lookup"><span data-stu-id="fa25a-110">Hybrid Modern Authentication \> HMA</span></span>
    
- <span data-ttu-id="fa25a-111">Локальная \> служба Exchange (Дов)</span><span class="sxs-lookup"><span data-stu-id="fa25a-111">Exchange on-premises \> EXCH</span></span>
    
- <span data-ttu-id="fa25a-112">Exchange Online \> EXO</span><span class="sxs-lookup"><span data-stu-id="fa25a-112">Exchange Online \> EXO</span></span>
    
- <span data-ttu-id="fa25a-113">Локальная \> среда Skype для бизнеса SFB</span><span class="sxs-lookup"><span data-stu-id="fa25a-113">Skype for Business on-premises \> SFB</span></span>
    
- <span data-ttu-id="fa25a-114">и Skype для бизнеса Online \> SFBO</span><span class="sxs-lookup"><span data-stu-id="fa25a-114">and Skype for Business Online \> SFBO</span></span>
    
<span data-ttu-id="fa25a-115">Кроме того, \* если рисунок в этой статье содержит объект с серым или затемненным элементом, то это означает, что элемент, отображаемый серым цветом, **не** включен в конфигурацию, характерную для MA.</span><span class="sxs-lookup"><span data-stu-id="fa25a-115">Also,  \*if a graphic in this article has an object that's 'grayed-out' or 'dimmed' that means the element shown in gray **is not** included in MA-specific configuration.</span></span> * 
  
## <a name="read-the-summary"></a><span data-ttu-id="fa25a-116">Просмотр сводки</span><span class="sxs-lookup"><span data-stu-id="fa25a-116">Read the summary</span></span>

<span data-ttu-id="fa25a-117">Эта сводка состоит в том, чтобы выполнить действия, которые в противном случае могут быть потеряны во время выполнения, а также для отслеживания того, где находится процесс.</span><span class="sxs-lookup"><span data-stu-id="fa25a-117">This summary boils the process into steps that might otherwise get lost during the execution, and is good for an overall check-list to keep track of where you are in the process.</span></span>
  
1. <span data-ttu-id="fa25a-118">Для начала убедитесь, что все необходимые компоненты соблюдены.</span><span class="sxs-lookup"><span data-stu-id="fa25a-118">First, make sure you meet all the prerequisites.</span></span>
    
1. <span data-ttu-id="fa25a-119">Так как многие **Предварительные требования** распространены как для Skype для бизнеса, так и для Exchange, [Ознакомьтесь со статьей обзорного контрольного списка требований](hybrid-modern-auth-overview.md).</span><span class="sxs-lookup"><span data-stu-id="fa25a-119">Since many **prerequisites** are common for both Skype for Business and Exchange, [see the overview article for your pre-req checklist](hybrid-modern-auth-overview.md).</span></span> <span data-ttu-id="fa25a-120">Выполните это действие, *прежде чем* приступать к каким – либо действиям, описанным в этой статье.</span><span class="sxs-lookup"><span data-stu-id="fa25a-120">Do this  *before*  you begin any of the steps in this article.</span></span> 
    
2. <span data-ttu-id="fa25a-121">Соберите сведения, относящиеся к сегменту HMA, которые понадобятся в файле, или OneNote.</span><span class="sxs-lookup"><span data-stu-id="fa25a-121">Collect the HMA-specific info you'll need in a file, or OneNote.</span></span>
    
3. <span data-ttu-id="fa25a-122">Включите современная проверка подлинности для EXO (если она еще не включена).</span><span class="sxs-lookup"><span data-stu-id="fa25a-122">Turn ON Modern Authentication for EXO (if it is not already turned on).</span></span>
    
4. <span data-ttu-id="fa25a-123">Включите современная проверка подлинности для SFBO (если она еще не включена).</span><span class="sxs-lookup"><span data-stu-id="fa25a-123">Turn ON Modern Authentication for SFBO (if it is not already turned on).</span></span>
    
5. <span data-ttu-id="fa25a-124">Включение гибридной современной проверки подлинности для локального сервера Exchange.</span><span class="sxs-lookup"><span data-stu-id="fa25a-124">Turn ON Hybrid Modern Authentication for Exchange on-premises.</span></span>
    
6. <span data-ttu-id="fa25a-125">Включение гибридной современной проверки подлинности в локальной среде Skype для бизнеса.</span><span class="sxs-lookup"><span data-stu-id="fa25a-125">Turn ON Hybrid Modern Authentication for Skype for Business on-premises.</span></span>
    
<span data-ttu-id="fa25a-126">Обратите внимание на то, что эти действия включают MA для SFB, SFBO, курс и EXO--, то есть, все продукты, которые могут участвовать в конфигурации HMA для SFB и SFBO (включая зависимости от КОНВЕРТАЦИи/EXO).</span><span class="sxs-lookup"><span data-stu-id="fa25a-126">Note These steps turn on MA for SFB, SFBO, EXCH, and EXO -- that is, all the products that can participate in a HMA configuration of SFB and SFBO (including dependencies on EXCH/EXO).</span></span> <span data-ttu-id="fa25a-127">Другими словами, если ваши пользователи размещены в почтовых ящиках, созданных в любой части гибридной среды (EXO + SFBO, EXO + SFB, дов + SFBO или дов + SFB), ваш готовый продукт будет выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="fa25a-127">In other words, if your users are homed in/have mailboxes created in any part of the Hybrid (EXO + SFBO, EXO + SFB, EXCH + SFBO, or EXCH + SFB), your finished product will look like this:</span></span>
  
![Смешанная 6 топология HMA в Skype для бизнеса имеет все четыре возможных расположения.](media/ab89cdf2-160b-49ac-9b71-0160800acfc8.png)
  
<span data-ttu-id="fa25a-129">Как видно из четырех различных мест для включения MA!</span><span class="sxs-lookup"><span data-stu-id="fa25a-129">As you can see there are four different places to turn on MA!</span></span> <span data-ttu-id="fa25a-130">Для лучшего взаимодействия с пользователем рекомендуется включить мА во всех четырех местах.</span><span class="sxs-lookup"><span data-stu-id="fa25a-130">For the best user experience we recommend you turn on MA in all four of these locations.</span></span> <span data-ttu-id="fa25a-131">Если вы не можете включить MA во всех этих расположениях, настройте действия так, чтобы включить MA только в тех местах, которые необходимы для вашей среды.</span><span class="sxs-lookup"><span data-stu-id="fa25a-131">If you can't turn MA on in all these locations, adjust the steps so that you turn on MA only in the locations that are necessary for your environment.</span></span>
  
<span data-ttu-id="fa25a-132">В [разделе Поддержка для Skype для бизнеса с MA](https://technet.microsoft.com/en-us/library/mt803262.aspx) для поддерживаемых топологий.</span><span class="sxs-lookup"><span data-stu-id="fa25a-132">See the [Supportability topic for Skype for Business with MA](https://technet.microsoft.com/en-us/library/mt803262.aspx) for supported topologies.</span></span> 
  
 <span data-ttu-id="fa25a-133">**Важно!** Прежде чем приступать к работе, убедитесь, что выполнены все необходимые условия.</span><span class="sxs-lookup"><span data-stu-id="fa25a-133">**Important** Double-check that you've met all the prerequisites before you begin.</span></span> <span data-ttu-id="fa25a-134">Эти сведения можно найти [здесь](hybrid-modern-auth-overview.md).</span><span class="sxs-lookup"><span data-stu-id="fa25a-134">You'll find that information [here](hybrid-modern-auth-overview.md).</span></span>
  
## <a name="collect-all-hma-specific-info-youll-need"></a><span data-ttu-id="fa25a-135">Сбор сведений, относящихся к сегменту HMA, которые вам понадобятся</span><span class="sxs-lookup"><span data-stu-id="fa25a-135">Collect all HMA-specific info you'll need</span></span>

<span data-ttu-id="fa25a-136">После повторной проверки соответствия [требованиям для использования](hybrid-modern-auth-overview.md) современной проверки подлинности (см. примечание выше) необходимо создать файл для хранения сведений, необходимых для настройки HMA в шагах.</span><span class="sxs-lookup"><span data-stu-id="fa25a-136">After you've double-checked that you meet the [prerequisites](hybrid-modern-auth-overview.md) to use Modern Authentication (see the note above), you should create a file to hold the info you'll need for configuring HMA in the steps ahead.</span></span> <span data-ttu-id="fa25a-137">Примеры, используемые в этой статье:</span><span class="sxs-lookup"><span data-stu-id="fa25a-137">Examples used in this article:</span></span> 
  
- <span data-ttu-id="fa25a-138">**Домен SIP/SMTP**</span><span class="sxs-lookup"><span data-stu-id="fa25a-138">**SIP/SMTP domain**</span></span>
    
  - <span data-ttu-id="fa25a-139">Пример.</span><span class="sxs-lookup"><span data-stu-id="fa25a-139">Ex.</span></span> <span data-ttu-id="fa25a-140">contoso.com (является федеративным с Office 365)</span><span class="sxs-lookup"><span data-stu-id="fa25a-140">contoso.com (is federated with Office 365)</span></span>
    
- <span data-ttu-id="fa25a-141">**Идентификатор клиента**</span><span class="sxs-lookup"><span data-stu-id="fa25a-141">**Tenant ID**</span></span>
    
  - <span data-ttu-id="fa25a-142">GUID, представляющий клиента Office 365 (с учетной записью contoso.onmicrosoft.com).</span><span class="sxs-lookup"><span data-stu-id="fa25a-142">The GUID that represents your Office 365 tenant (at the login of contoso.onmicrosoft.com).</span></span>
    
- <span data-ttu-id="fa25a-143">**URL-адреса веб-службы SFB 2015 CU5**</span><span class="sxs-lookup"><span data-stu-id="fa25a-143">**SFB 2015 CU5 Web Service URLs**</span></span>
    
<span data-ttu-id="fa25a-144">Для всех развернутых пулов SfB 2015 потребуется внутренний и внешний URL-адрес веб-службы.</span><span class="sxs-lookup"><span data-stu-id="fa25a-144">You will need internal and external web service URL's for all SfB 2015 pools deployed.</span></span> <span data-ttu-id="fa25a-145">Чтобы получить эти сведения, выполните следующую команду в командной консоли Skype для бизнеса:</span><span class="sxs-lookup"><span data-stu-id="fa25a-145">To obtain these, run the following from Skype for Business Management Shell:</span></span>
  
```
Get-CsService -WebServer | Select-Object PoolFqdn, InternalFqdn, ExternalFqdn | FL
```

- <span data-ttu-id="fa25a-146">Пример.</span><span class="sxs-lookup"><span data-stu-id="fa25a-146">Ex.</span></span> <span data-ttu-id="fa25a-147">Образомhttps://lyncwebint01.contoso.com</span><span class="sxs-lookup"><span data-stu-id="fa25a-147">Internal: https://lyncwebint01.contoso.com</span></span>
    
- <span data-ttu-id="fa25a-148">Пример.</span><span class="sxs-lookup"><span data-stu-id="fa25a-148">Ex.</span></span> <span data-ttu-id="fa25a-149">Внешнихhttps://lyncwebext01.contoso.com</span><span class="sxs-lookup"><span data-stu-id="fa25a-149">External: https://lyncwebext01.contoso.com</span></span>
    
<span data-ttu-id="fa25a-150">Если используется сервер Standard Edition, внутренний URL-адрес будет пустым.</span><span class="sxs-lookup"><span data-stu-id="fa25a-150">If you are using a Standard Edition server, the internal URL will be blank.</span></span> <span data-ttu-id="fa25a-151">В этом случае используйте полное доменное имя пула для внутреннего URL-адреса.</span><span class="sxs-lookup"><span data-stu-id="fa25a-151">In this case, use the pool fqdn for the internal URL.</span></span>
  
## <a name="turn-on-modern-authentication-for-exo"></a><span data-ttu-id="fa25a-152">Включение современной проверки подлинности для EXO</span><span class="sxs-lookup"><span data-stu-id="fa25a-152">Turn on Modern Authentication for EXO</span></span>

<span data-ttu-id="fa25a-153">Следуйте инструкциям в статье [Exchange Online: как включить клиент для современной проверки подлинности.](https://social.technet.microsoft.com/wiki/contents/articles/32711.exchange-online-how-to-enable-your-tenant-for-modern-authentication.aspx)</span><span class="sxs-lookup"><span data-stu-id="fa25a-153">Follow the instructions here: [Exchange Online: How to enable your tenant for modern authentication.](https://social.technet.microsoft.com/wiki/contents/articles/32711.exchange-online-how-to-enable-your-tenant-for-modern-authentication.aspx)</span></span>
  
## <a name="turn-on-modern-authentication-for-sfbo"></a><span data-ttu-id="fa25a-154">Включение современной проверки подлинности для SFBO</span><span class="sxs-lookup"><span data-stu-id="fa25a-154">Turn on Modern Authentication for SFBO</span></span>

<span data-ttu-id="fa25a-155">Следуйте инструкциям здесь: [Skype для бизнеса Online: Включите клиент для современной проверки подлинности](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx).</span><span class="sxs-lookup"><span data-stu-id="fa25a-155">Follow the instructions here: [Skype for Business Online: Enable your tenant for modern authentication](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx).</span></span>
  
## <a name="turn-on-hybrid-modern-authentication-for-exchange-on-premises"></a><span data-ttu-id="fa25a-156">Включение гибридной современной проверки подлинности для локального сервера Exchange</span><span class="sxs-lookup"><span data-stu-id="fa25a-156">Turn on Hybrid Modern Authentication for Exchange on-premises</span></span>

<span data-ttu-id="fa25a-157">Следуйте инструкциям ниже: [Настройка локального сервера Exchange Server для использования гибридной современной проверки подлинности](configure-exchange-server-for-hybrid-modern-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="fa25a-157">Follow the instructions here: [How to configure Exchange Server on-premises to use Hybrid Modern Authentication](configure-exchange-server-for-hybrid-modern-authentication.md).</span></span>
  
## <a name="turn-on-hybrid-modern-authentication-for-skype-for-business-on-premises"></a><span data-ttu-id="fa25a-158">Включение гибридной современной проверки подлинности в локальной среде Skype для бизнеса</span><span class="sxs-lookup"><span data-stu-id="fa25a-158">Turn on Hybrid Modern Authentication for Skype for Business on-premises</span></span>

### <a name="add-on-premises-web-service-urls-as-spns-in-azure-ad"></a><span data-ttu-id="fa25a-159">Добавление локальных URL-адресов веб-служб в Azure AD в качестве SPN</span><span class="sxs-lookup"><span data-stu-id="fa25a-159">Add on-premises web service URLs as SPNs in Azure AD</span></span>

<span data-ttu-id="fa25a-160">Теперь вам потребуется выполнить команды, чтобы добавить URL-адреса (собранные ранее) в качестве субъектов-служб в SFBO.</span><span class="sxs-lookup"><span data-stu-id="fa25a-160">Now you'll need to run commands to add the URLs (collected earlier) as Service Principals in SFBO.</span></span>
  
 <span data-ttu-id="fa25a-161">**Note (Примечание** ) Имена участников службы (SPN) идентифицируют веб-службы и связывают их с участником безопасности (например, именем или группой учетных записей), чтобы служба могла работать от имени авторизованного пользователя.</span><span class="sxs-lookup"><span data-stu-id="fa25a-161">**Note** Service principal names (SPNs) identify web services and associate them with a security principal (such as an account name or group) so that the service can act on the behalf of an authorized user.</span></span> <span data-ttu-id="fa25a-162">Клиенты, выполняющие проверку подлинности на сервере, используют сведения, которые хранятся в именах участников-служб.</span><span class="sxs-lookup"><span data-stu-id="fa25a-162">Clients authenticating to a server make use of information that's contained in SPNs.</span></span> 
  
1. <span data-ttu-id="fa25a-163">Для начала подключитесь к AAD с помощью [приведенных ниже инструкций](https://docs.microsoft.com/en-us/powershell/azure/active-directory/overview?view=azureadps-1.0).</span><span class="sxs-lookup"><span data-stu-id="fa25a-163">First, connect to AAD with [these instructions](https://docs.microsoft.com/en-us/powershell/azure/active-directory/overview?view=azureadps-1.0).</span></span>
    
2. <span data-ttu-id="fa25a-164">Выполните эту команду в локальной среде, чтобы получить список URL-адресов веб-службы SFB.</span><span class="sxs-lookup"><span data-stu-id="fa25a-164">Run this command, on-premises, to get a list of SFB web service URLs.</span></span>

   <span data-ttu-id="fa25a-165">Обратите внимание, что AppPrincipalId `00000004`начинается с.</span><span class="sxs-lookup"><span data-stu-id="fa25a-165">Note that the AppPrincipalId begins with `00000004`.</span></span> <span data-ttu-id="fa25a-166">Это соответствует Skype для бизнеса Online.</span><span class="sxs-lookup"><span data-stu-id="fa25a-166">This corresponds to Skype for Business Online.</span></span>
    
   <span data-ttu-id="fa25a-167">Запишите (и снимок экрана для последующего сравнения) выходные данные этой команды, которые будут включать URL-адрес SE и WS, но в основном состоят из имен участников `00000004-0000-0ff1-ce00-000000000000/`-служб, начинающихся с.</span><span class="sxs-lookup"><span data-stu-id="fa25a-167">Take note of (and screenshot for later comparison) the output of this command, which will include an SE and WS URL, but mostly consist of SPNs that begin with `00000004-0000-0ff1-ce00-000000000000/`.</span></span>
    
```
Get-MsolServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 | Select -ExpandProperty ServicePrincipalNames
```
    
3. <span data-ttu-id="fa25a-168">Если внутренние **или** внешние URL-адреса SFB из локальной сети отсутствуют (например, и https://lyncwebint01.contoso.com https://lyncwebext01.contoso.com) нам потребуется добавить эти записи в этот список).</span><span class="sxs-lookup"><span data-stu-id="fa25a-168">If the internal **or** external SFB URLs from on-premises are missing (for example, https://lyncwebint01.contoso.com and https://lyncwebext01.contoso.com) we will need to add those specific records to this list.</span></span> 
    
    <span data-ttu-id="fa25a-169">Обязательно замените *Пример URL-адресов* , приведенный ниже, на фактические URL-адреса в разделе Add Commands!</span><span class="sxs-lookup"><span data-stu-id="fa25a-169">Be sure to replace  *the example URLs*  , below, with your actual URLs in the Add commands!</span></span> 
  
```  
$x= Get-MsolServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000
$x.ServicePrincipalnames.Add("https://lyncwebint01.contoso.com/")
$x.ServicePrincipalnames.Add("https://lyncwebext01.contoso.com/")
Set-MSOLServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $x.ServicePrincipalNames
```
  
4. <span data-ttu-id="fa25a-170">Проверьте, были ли добавлены новые записи, выполнив команду Get – MsolServicePrincipal повторно с шага 2 и просмотрев результаты.</span><span class="sxs-lookup"><span data-stu-id="fa25a-170">Verify your new records were added by running the Get-MsolServicePrincipal command from step 2 again, and looking through the output.</span></span> <span data-ttu-id="fa25a-171">Сравнение списка и снимка экрана перед новым списком имен участников-служб (вы также можете создать список снимков экрана для записи).</span><span class="sxs-lookup"><span data-stu-id="fa25a-171">Compare the list / screenshot from before to the new list of SPNs (you may also screenshot the new list for your records).</span></span> <span data-ttu-id="fa25a-172">В случае успеха в списке отобразятся два новых URL-адреса.</span><span class="sxs-lookup"><span data-stu-id="fa25a-172">If you were successful, you will see the two new URLs in the list.</span></span> <span data-ttu-id="fa25a-173">В нашем примере список SPN теперь включает определенные URL-адреса https://lyncwebint01.contoso.com и. https://lyncwebext01.contoso.com/</span><span class="sxs-lookup"><span data-stu-id="fa25a-173">Going by our example, the list of SPNs will now include the specific URLs https://lyncwebint01.contoso.com and https://lyncwebext01.contoso.com/.</span></span>
    
### <a name="create-the-evosts-auth-server-object"></a><span data-ttu-id="fa25a-174">Создание объекта сервера проверки подлинности Евостс</span><span class="sxs-lookup"><span data-stu-id="fa25a-174">Create the EvoSTS Auth Server Object</span></span>

<span data-ttu-id="fa25a-175">Выполните следующую команду в командной консоли Skype для бизнеса.</span><span class="sxs-lookup"><span data-stu-id="fa25a-175">Run the following command in the Skype for Business Management Shell.</span></span>
  
```
New-CsOAuthServer -Identity evoSTS -MetadataURL https://login.windows.net/common/FederationMetadata/2007-06/FederationMetadata.xml -AcceptSecurityIdentifierInformation $true -Type AzureAD
```
    
### <a name="enable-hybrid-modern-authentication"></a><span data-ttu-id="fa25a-176">Включение гибридной современной проверки подлинности</span><span class="sxs-lookup"><span data-stu-id="fa25a-176">Enable Hybrid Modern Authentication</span></span>

<span data-ttu-id="fa25a-177">Это шаг, который фактически включает мА.</span><span class="sxs-lookup"><span data-stu-id="fa25a-177">This is the step that actually turns MA on.</span></span> <span data-ttu-id="fa25a-178">Все предыдущие действия можно выполнить заранее, не изменяя поток проверки подлинности клиента.</span><span class="sxs-lookup"><span data-stu-id="fa25a-178">All the previous steps can be run ahead of time without changing the client authentication flow.</span></span> <span data-ttu-id="fa25a-179">Когда вы будете готовы изменить поток проверки подлинности, выполните эту команду в командной консоли Skype для бизнеса.</span><span class="sxs-lookup"><span data-stu-id="fa25a-179">When you are ready to change the authentication flow, run this command in the Skype for Business Management Shell.</span></span> 
  
```
Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity evoSTS
```
    
## <a name="verify"></a><span data-ttu-id="fa25a-180">Читаем</span><span class="sxs-lookup"><span data-stu-id="fa25a-180">Verify</span></span>

<span data-ttu-id="fa25a-181">После включения HMA для следующего входа клиента будет использоваться новый процесс проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="fa25a-181">Once you enable HMA, a client's next login will use the new auth flow.</span></span> <span data-ttu-id="fa25a-182">Обратите внимание, что просто включение HMA не вызывает повторную проверку подлинности для любого клиента.</span><span class="sxs-lookup"><span data-stu-id="fa25a-182">Note that just turning on HMA won't trigger a re-authentication for any client.</span></span> <span data-ttu-id="fa25a-183">Клиенты повторно проходят проверку подлинности на основе времени существования маркеров и/или сертификатов проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="fa25a-183">The clients re-authenticate based on the lifetime of the auth tokens and/or certs they have.</span></span>
  
<span data-ttu-id="fa25a-184">Чтобы проверить, работает ли сегмент HMA после включения, выйдите из тестового клиента Windows SFB и убедитесь, что выбран пункт "удалить мои учетные данные".</span><span class="sxs-lookup"><span data-stu-id="fa25a-184">To test that HMA is working after you've enabled it, sign out of a test SFB Windows client and be sure to click 'delete my credentials'.</span></span> <span data-ttu-id="fa25a-185">Выполните вход еще раз.</span><span class="sxs-lookup"><span data-stu-id="fa25a-185">Sign in again.</span></span> <span data-ttu-id="fa25a-186">Теперь клиент должен использовать современный процесс проверки подлинности, а ваш вход в систему будет включать в себя приглашение на **Office 365** для учетной записи "Рабочий или учебный", которая отображается прямо перед тем, как клиент обращается к серверу и выполняет вход в систему.</span><span class="sxs-lookup"><span data-stu-id="fa25a-186">The client should now use the Modern Auth flow and your login will now include an **Office 365** prompt for a 'Work or school' account, seen right before the client contacts the server and logs you in.</span></span> 
  
<span data-ttu-id="fa25a-187">Кроме того, вы также можете проверить сведения о конфигурации для клиентов Skype для бизнеса для "центра OAuth".</span><span class="sxs-lookup"><span data-stu-id="fa25a-187">You should also check the 'Configuration Information' for Skype for Business Clients for an 'OAuth Authority'.</span></span> <span data-ttu-id="fa25a-188">Для этого на клиентском компьютере, удерживая клавишу CTRL, щелкните правой кнопкой мыши значок Skype для бизнеса в панели уведомлений Windows.</span><span class="sxs-lookup"><span data-stu-id="fa25a-188">To do this on your client computer, hold down the CTRL key at the same time you right-click the Skype for Business Icon in the Windows Notification tray.</span></span> <span data-ttu-id="fa25a-189">В появившемся меню выберите пункт сведения о конфигурации.</span><span class="sxs-lookup"><span data-stu-id="fa25a-189">Click Configuration Information in the menu that appears.</span></span> <span data-ttu-id="fa25a-190">В окне сведения о настройке Skype для бизнеса, которое будет отображаться на рабочем столе, найдите следующее:</span><span class="sxs-lookup"><span data-stu-id="fa25a-190">In the 'Skype for Business Configuration Information' window that will appear on the desktop, look for the following:</span></span>
  
![Сведения о конфигурации клиента Skype для бизнеса с современной проверкой подлинности показывает URL-адрес центра OAUTH и https://login.windows.net/common/oauth2/authorizeцентра OAuth EWS.](media/4e54edf5-c8f8-4e7f-b032-5d413b0232de.png)
  
<span data-ttu-id="fa25a-192">Кроме того, следует удерживать нажатой клавишу CTRL, щелкнув значок клиента Outlook (также в области уведомлений Windows), и выберите пункт "состояние подключения".</span><span class="sxs-lookup"><span data-stu-id="fa25a-192">You should also hold down the CTRL key at the same time you right click the icon for the Outlook client (also in the Windows Notifications tray) and click 'Connection Status'.</span></span> <span data-ttu-id="fa25a-193">Найдите SMTP-адрес клиента с типом определения "Bearer\*", который представляет токен носителя, используемый в OAuth.</span><span class="sxs-lookup"><span data-stu-id="fa25a-193">Look for the client's SMTP address against an Authn type of 'Bearer\*', which represents the bearer token used in OAuth.</span></span>
  
## <a name="related-articles"></a><span data-ttu-id="fa25a-194">Статьи по теме</span><span class="sxs-lookup"><span data-stu-id="fa25a-194">Related articles</span></span>

<span data-ttu-id="fa25a-195">[Выполните обратное соединение с обзором современной проверки подлинности](hybrid-modern-auth-overview.md) .</span><span class="sxs-lookup"><span data-stu-id="fa25a-195">[Link back to the Modern Authentication overview](hybrid-modern-auth-overview.md) .</span></span> 
  
<span data-ttu-id="fa25a-196">Вам нужно знать, как использовать современные проверки подлинности (ADAL) для клиентов Skype для бизнеса?</span><span class="sxs-lookup"><span data-stu-id="fa25a-196">Do you need to know how to use Modern Authentication (ADAL) for your Skype for Business clients?</span></span> <span data-ttu-id="fa25a-197">Мы познакомились с [этой](https://technet.microsoft.com/en-us/library/mt710548.aspx)статьей.</span><span class="sxs-lookup"><span data-stu-id="fa25a-197">We've got steps [here](https://technet.microsoft.com/en-us/library/mt710548.aspx).</span></span>
  
<span data-ttu-id="fa25a-198">Вы хотите прочитать эти действия, так как они отображаются для Exchange Server, локальной сети и работают без SFB?</span><span class="sxs-lookup"><span data-stu-id="fa25a-198">Would you like to read these steps as they appear for Exchange Server, on-premises, running without SFB?</span></span> <span data-ttu-id="fa25a-199">Эти действия доступны здесь.</span><span class="sxs-lookup"><span data-stu-id="fa25a-199">Those steps are available here.</span></span>
  

