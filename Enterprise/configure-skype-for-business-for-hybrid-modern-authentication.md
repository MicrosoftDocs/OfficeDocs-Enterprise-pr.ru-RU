---
title: Как настроить локальное развертывание Skype для бизнеса для использования гибридной современной проверки подлинности
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/3/2019
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 522d5cec-4e1b-4cc3-937f-293570717bc6
ms.collection:
- M365-security-compliance
f1.keywords:
- NOCSH
description: Современная проверка подлинности — это способ управления удостоверениями, обеспечивающий более надежную проверку подлинности и авторизацию пользователей, доступный для локального сервера Skype для бизнеса Server и для локального сервера Exchange Server, а также для гибридной среды Skype для бизнеса.
ms.openlocfilehash: de5063da9eed03e2cd455b79b3a2d1c2f671ad1e
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/07/2020
ms.locfileid: "41840726"
---
# <a name="how-to-configure-skype-for-business-on-premises-to-use-hybrid-modern-authentication"></a><span data-ttu-id="29258-103">Как настроить локальное развертывание Skype для бизнеса для использования гибридной современной проверки подлинности</span><span class="sxs-lookup"><span data-stu-id="29258-103">How to configure Skype for Business on-premises to use Hybrid Modern Authentication</span></span>

<span data-ttu-id="29258-104">*Эта статья относится к Office 365 корпоративный и Microsoft 365 корпоративный.*</span><span class="sxs-lookup"><span data-stu-id="29258-104">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="29258-105">Современная проверка подлинности — это способ управления удостоверениями, обеспечивающий более надежную проверку подлинности и авторизацию пользователей, доступный для локального сервера Skype для бизнеса Server и для локального сервера Exchange Server, а также для гибридной среды Skype для бизнеса.</span><span class="sxs-lookup"><span data-stu-id="29258-105">Modern Authentication, is a method of identity management that offers more secure user authentication and authorization, is available for Skype for Business server on-premises and Exchange server on-premises, as well as split-domain Skype for Business hybrids.</span></span>
  
 <span data-ttu-id="29258-106">**Важно!** Хотите узнать больше о современной проверке подлинности (MA) и зачем использовать ее в вашей компании или Организации?</span><span class="sxs-lookup"><span data-stu-id="29258-106">**Important** Would you like to know more about Modern Authentication (MA) and why you might prefer to use it in your company or organization?</span></span> <span data-ttu-id="29258-107">Просмотрите [этот документ](hybrid-modern-auth-overview.md) , чтобы получить обзор.</span><span class="sxs-lookup"><span data-stu-id="29258-107">Check [this document](hybrid-modern-auth-overview.md) for an overview.</span></span> <span data-ttu-id="29258-108">Если вам нужно знать, какие топологии Skype для бизнеса поддерживаются в MA, это задокументировано здесь!</span><span class="sxs-lookup"><span data-stu-id="29258-108">If you need to know what Skype for Business topologies are supported with MA, that's documented here!</span></span>
  
 <span data-ttu-id="29258-109">**Прежде чем начать**, я вызываю:</span><span class="sxs-lookup"><span data-stu-id="29258-109">**Before we begin**, I call:</span></span>
  
- <span data-ttu-id="29258-110">Современная Проверка \> подлинности MA</span><span class="sxs-lookup"><span data-stu-id="29258-110">Modern Authentication \> MA</span></span>

- <span data-ttu-id="29258-111">Гибридная современная \> проверка подлинности HMA</span><span class="sxs-lookup"><span data-stu-id="29258-111">Hybrid Modern Authentication \> HMA</span></span>

- <span data-ttu-id="29258-112">Локальная \> служба Exchange (Дов)</span><span class="sxs-lookup"><span data-stu-id="29258-112">Exchange on-premises \> EXCH</span></span>

- <span data-ttu-id="29258-113">Exchange Online \> EXO</span><span class="sxs-lookup"><span data-stu-id="29258-113">Exchange Online \> EXO</span></span>

- <span data-ttu-id="29258-114">Локальная \> среда Skype для бизнеса SFB</span><span class="sxs-lookup"><span data-stu-id="29258-114">Skype for Business on-premises \> SFB</span></span>

- <span data-ttu-id="29258-115">и Skype для бизнеса Online \> SFBO</span><span class="sxs-lookup"><span data-stu-id="29258-115">and Skype for Business Online \> SFBO</span></span>

<span data-ttu-id="29258-116">Кроме того, если рисунок в этой статье содержит затененный или затененный объект, значит элемент, отображаемый серым цветом, **не** включается в конфигурацию, характерную для MA.</span><span class="sxs-lookup"><span data-stu-id="29258-116">Also, if a graphic in this article has an object that's greyed-out or dimmed that means the element shown in gray **is not** included in MA-specific configuration.</span></span>
  
## <a name="read-the-summary"></a><span data-ttu-id="29258-117">Просмотр сводки</span><span class="sxs-lookup"><span data-stu-id="29258-117">Read the summary</span></span>

<span data-ttu-id="29258-118">Эта сводка разделяет процесс на действия, которые в противном случае будут потеряны во время выполнения, и хорошо подходит для отслеживания того, где находится процесс.</span><span class="sxs-lookup"><span data-stu-id="29258-118">This summary breaks down the process into steps that might otherwise get lost during the execution, and is good for an overall checklist to keep track of where you are in the process.</span></span>
  
1. <span data-ttu-id="29258-119">Для начала убедитесь, что все необходимые компоненты соблюдены.</span><span class="sxs-lookup"><span data-stu-id="29258-119">First, make sure you meet all the prerequisites.</span></span>

1. <span data-ttu-id="29258-120">Так как многие **Предварительные требования** распространены как для Skype для бизнеса, так и для Exchange, [Ознакомьтесь со статьей обзорного контрольного списка требований](hybrid-modern-auth-overview.md).</span><span class="sxs-lookup"><span data-stu-id="29258-120">Since many **prerequisites** are common for both Skype for Business and Exchange, [see the overview article for your pre-req checklist](hybrid-modern-auth-overview.md).</span></span> <span data-ttu-id="29258-121">Выполните это действие, *прежде чем* приступать к каким – либо действиям, описанным в этой статье.</span><span class="sxs-lookup"><span data-stu-id="29258-121">Do this  *before*  you begin any of the steps in this article.</span></span>

1. <span data-ttu-id="29258-122">Соберите сведения, относящиеся к сегменту HMA, которые понадобятся в файле, или OneNote.</span><span class="sxs-lookup"><span data-stu-id="29258-122">Collect the HMA-specific info you'll need in a file, or OneNote.</span></span>

1. <span data-ttu-id="29258-123">Включите современная проверка подлинности для EXO (если она еще не включена).</span><span class="sxs-lookup"><span data-stu-id="29258-123">Turn ON Modern Authentication for EXO (if it is not already turned on).</span></span>

1. <span data-ttu-id="29258-124">Включите современная проверка подлинности для SFBO (если она еще не включена).</span><span class="sxs-lookup"><span data-stu-id="29258-124">Turn ON Modern Authentication for SFBO (if it is not already turned on).</span></span>

1. <span data-ttu-id="29258-125">Включение гибридной современной проверки подлинности для локального сервера Exchange.</span><span class="sxs-lookup"><span data-stu-id="29258-125">Turn ON Hybrid Modern Authentication for Exchange on-premises.</span></span>

1. <span data-ttu-id="29258-126">Включение гибридной современной проверки подлинности в локальной среде Skype для бизнеса.</span><span class="sxs-lookup"><span data-stu-id="29258-126">Turn ON Hybrid Modern Authentication for Skype for Business on-premises.</span></span>

<span data-ttu-id="29258-127">Эти действия включают MA для SFB, SFBO, курс и EXO-, то есть все продукты, которые могут участвовать в конфигурации HMA для SFB и SFBO (включая зависимости от валюты по курсу/EXO).</span><span class="sxs-lookup"><span data-stu-id="29258-127">These steps turn on MA for SFB, SFBO, EXCH, and EXO - that is, all the products that can participate in a HMA configuration of SFB and SFBO (including dependencies on EXCH/EXO).</span></span> <span data-ttu-id="29258-128">Другими словами, если ваши пользователи размещены в почтовых ящиках, созданных в любой части гибридной среды (EXO + SFBO, EXO + SFB, дов + SFBO или дов + SFB), ваш готовый продукт будет выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="29258-128">In other words, if your users are homed in/have mailboxes created in any part of the Hybrid (EXO + SFBO, EXO + SFB, EXCH + SFBO, or EXCH + SFB), your finished product will look like this:</span></span>
  
![Смешанная 6 топология HMA в Skype для бизнеса имеет все четыре возможных расположения.](media/ab89cdf2-160b-49ac-9b71-0160800acfc8.png)
  
<span data-ttu-id="29258-130">Как видно из четырех различных мест для включения MA!</span><span class="sxs-lookup"><span data-stu-id="29258-130">As you can see there are four different places to turn on MA!</span></span> <span data-ttu-id="29258-131">Для лучшего взаимодействия с пользователем рекомендуется включить мА во всех четырех местах.</span><span class="sxs-lookup"><span data-stu-id="29258-131">For the best user experience we recommend you turn on MA in all four of these locations.</span></span> <span data-ttu-id="29258-132">Если вы не можете включить MA во всех этих расположениях, настройте действия так, чтобы включить MA только в тех местах, которые необходимы для вашей среды.</span><span class="sxs-lookup"><span data-stu-id="29258-132">If you can't turn MA on in all these locations, adjust the steps so that you turn on MA only in the locations that are necessary for your environment.</span></span>
  
<span data-ttu-id="29258-133">В [разделе Поддержка для Skype для бизнеса с MA](https://technet.microsoft.com/library/mt803262.aspx) для поддерживаемых топологий.</span><span class="sxs-lookup"><span data-stu-id="29258-133">See the [Supportability topic for Skype for Business with MA](https://technet.microsoft.com/library/mt803262.aspx) for supported topologies.</span></span>
  
 <span data-ttu-id="29258-134">**Важно!** Прежде чем приступать к работе, убедитесь, что выполнены все необходимые условия.</span><span class="sxs-lookup"><span data-stu-id="29258-134">**Important** Double-check that you've met all the prerequisites before you begin.</span></span> <span data-ttu-id="29258-135">Эти сведения можно найти [здесь](hybrid-modern-auth-overview.md).</span><span class="sxs-lookup"><span data-stu-id="29258-135">You'll find that information [here](hybrid-modern-auth-overview.md).</span></span>
  
## <a name="collect-all-hma-specific-info-youll-need"></a><span data-ttu-id="29258-136">Сбор сведений, относящихся к сегменту HMA, которые вам понадобятся</span><span class="sxs-lookup"><span data-stu-id="29258-136">Collect all HMA-specific info you'll need</span></span>

<span data-ttu-id="29258-137">После повторной проверки соответствия [требованиям для использования](hybrid-modern-auth-overview.md) современной проверки подлинности (см. примечание выше) необходимо создать файл для хранения сведений, необходимых для настройки HMA в шагах.</span><span class="sxs-lookup"><span data-stu-id="29258-137">After you've double-checked that you meet the [prerequisites](hybrid-modern-auth-overview.md) to use Modern Authentication (see the note above), you should create a file to hold the info you'll need for configuring HMA in the steps ahead.</span></span> <span data-ttu-id="29258-138">Примеры, используемые в этой статье:</span><span class="sxs-lookup"><span data-stu-id="29258-138">Examples used in this article:</span></span>
  
- <span data-ttu-id="29258-139">**Домен SIP/SMTP**</span><span class="sxs-lookup"><span data-stu-id="29258-139">**SIP/SMTP domain**</span></span>

  - <span data-ttu-id="29258-140">Пример.</span><span class="sxs-lookup"><span data-stu-id="29258-140">Ex.</span></span> <span data-ttu-id="29258-141">contoso.com (является федеративным с Office 365)</span><span class="sxs-lookup"><span data-stu-id="29258-141">contoso.com (is federated with Office 365)</span></span>

- <span data-ttu-id="29258-142">**Идентификатор клиента**</span><span class="sxs-lookup"><span data-stu-id="29258-142">**Tenant ID**</span></span>

  - <span data-ttu-id="29258-143">GUID, представляющий клиента Office 365 (с учетной записью contoso.onmicrosoft.com).</span><span class="sxs-lookup"><span data-stu-id="29258-143">The GUID that represents your Office 365 tenant (at the login of contoso.onmicrosoft.com).</span></span>

- <span data-ttu-id="29258-144">**URL-адреса веб-службы SFB 2015 CU5**</span><span class="sxs-lookup"><span data-stu-id="29258-144">**SFB 2015 CU5 Web Service URLs**</span></span>

<span data-ttu-id="29258-145">Для всех развернутых пулов SfB 2015 потребуется внутренний и внешний URL-адрес веб-службы.</span><span class="sxs-lookup"><span data-stu-id="29258-145">You will need internal and external web service URL's for all SfB 2015 pools deployed.</span></span> <span data-ttu-id="29258-146">Чтобы получить эти сведения, выполните следующую команду в командной консоли Skype для бизнеса:</span><span class="sxs-lookup"><span data-stu-id="29258-146">To obtain these, run the following from Skype for Business Management Shell:</span></span>
  
```powershell
Get-CsService -WebServer | Select-Object PoolFqdn, InternalFqdn, ExternalFqdn | FL
```

- <span data-ttu-id="29258-147">Пример.</span><span class="sxs-lookup"><span data-stu-id="29258-147">Ex.</span></span> <span data-ttu-id="29258-148">Образомhttps://lyncwebint01.contoso.com</span><span class="sxs-lookup"><span data-stu-id="29258-148">Internal: https://lyncwebint01.contoso.com</span></span>

- <span data-ttu-id="29258-149">Пример.</span><span class="sxs-lookup"><span data-stu-id="29258-149">Ex.</span></span> <span data-ttu-id="29258-150">Внешнихhttps://lyncwebext01.contoso.com</span><span class="sxs-lookup"><span data-stu-id="29258-150">External: https://lyncwebext01.contoso.com</span></span>

<span data-ttu-id="29258-151">Если используется сервер Standard Edition, внутренний URL-адрес будет пустым.</span><span class="sxs-lookup"><span data-stu-id="29258-151">If you are using a Standard Edition server, the internal URL will be blank.</span></span> <span data-ttu-id="29258-152">В этом случае используйте полное доменное имя пула для внутреннего URL-адреса.</span><span class="sxs-lookup"><span data-stu-id="29258-152">In this case, use the pool fqdn for the internal URL.</span></span>
  
## <a name="turn-on-modern-authentication-for-exo"></a><span data-ttu-id="29258-153">Включение современной проверки подлинности для EXO</span><span class="sxs-lookup"><span data-stu-id="29258-153">Turn on Modern Authentication for EXO</span></span>

<span data-ttu-id="29258-154">Следуйте инструкциям в статье [Exchange Online: как включить клиент для современной проверки подлинности.](https://social.technet.microsoft.com/wiki/contents/articles/32711.exchange-online-how-to-enable-your-tenant-for-modern-authentication.aspx)</span><span class="sxs-lookup"><span data-stu-id="29258-154">Follow the instructions here: [Exchange Online: How to enable your tenant for modern authentication.](https://social.technet.microsoft.com/wiki/contents/articles/32711.exchange-online-how-to-enable-your-tenant-for-modern-authentication.aspx)</span></span>
  
## <a name="turn-on-modern-authentication-for-sfbo"></a><span data-ttu-id="29258-155">Включение современной проверки подлинности для SFBO</span><span class="sxs-lookup"><span data-stu-id="29258-155">Turn on Modern Authentication for SFBO</span></span>

<span data-ttu-id="29258-156">Следуйте инструкциям здесь: [Skype для бизнеса Online: Включите клиент для современной проверки подлинности](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx).</span><span class="sxs-lookup"><span data-stu-id="29258-156">Follow the instructions here: [Skype for Business Online: Enable your tenant for modern authentication](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx).</span></span>
  
## <a name="turn-on-hybrid-modern-authentication-for-exchange-on-premises"></a><span data-ttu-id="29258-157">Включение гибридной современной проверки подлинности для локального сервера Exchange</span><span class="sxs-lookup"><span data-stu-id="29258-157">Turn on Hybrid Modern Authentication for Exchange on-premises</span></span>

<span data-ttu-id="29258-158">Следуйте инструкциям ниже: [Настройка локального сервера Exchange Server для использования гибридной современной проверки подлинности](configure-exchange-server-for-hybrid-modern-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="29258-158">Follow the instructions here: [How to configure Exchange Server on-premises to use Hybrid Modern Authentication](configure-exchange-server-for-hybrid-modern-authentication.md).</span></span>
  
## <a name="turn-on-hybrid-modern-authentication-for-skype-for-business-on-premises"></a><span data-ttu-id="29258-159">Включение гибридной современной проверки подлинности в локальной среде Skype для бизнеса</span><span class="sxs-lookup"><span data-stu-id="29258-159">Turn on Hybrid Modern Authentication for Skype for Business on-premises</span></span>

### <a name="add-on-premises-web-service-urls-as-spns-in-azure-ad"></a><span data-ttu-id="29258-160">Добавление локальных URL-адресов веб-служб в Azure AD в качестве SPN</span><span class="sxs-lookup"><span data-stu-id="29258-160">Add on-premises web service URLs as SPNs in Azure AD</span></span>

<span data-ttu-id="29258-161">Теперь вам потребуется выполнить команды, чтобы добавить URL-адреса (собранные ранее) в качестве субъектов-служб в SFBO.</span><span class="sxs-lookup"><span data-stu-id="29258-161">Now you'll need to run commands to add the URLs (collected earlier) as Service Principals in SFBO.</span></span>
  
 <span data-ttu-id="29258-162">**Note (Примечание** ) Имена участников службы (SPN) идентифицируют веб-службы и связывают их с участником безопасности (например, именем или группой учетных записей), чтобы служба могла работать от имени авторизованного пользователя.</span><span class="sxs-lookup"><span data-stu-id="29258-162">**Note** Service principal names (SPNs) identify web services and associate them with a security principal (such as an account name or group) so that the service can act on the behalf of an authorized user.</span></span> <span data-ttu-id="29258-163">Клиенты, выполняющие проверку подлинности на сервере, используют сведения, которые хранятся в именах участников-служб.</span><span class="sxs-lookup"><span data-stu-id="29258-163">Clients authenticating to a server make use of information that's contained in SPNs.</span></span>
  
1. <span data-ttu-id="29258-164">Для начала подключитесь к AAD с помощью [приведенных ниже инструкций](https://docs.microsoft.com/powershell/azure/active-directory/overview?view=azureadps-1.0).</span><span class="sxs-lookup"><span data-stu-id="29258-164">First, connect to AAD with [these instructions](https://docs.microsoft.com/powershell/azure/active-directory/overview?view=azureadps-1.0).</span></span>

2. <span data-ttu-id="29258-165">Выполните эту команду в локальной среде, чтобы получить список URL-адресов веб-службы SFB.</span><span class="sxs-lookup"><span data-stu-id="29258-165">Run this command, on-premises, to get a list of SFB web service URLs.</span></span>

   <span data-ttu-id="29258-166">Обратите внимание, что AppPrincipalId `00000004`начинается с.</span><span class="sxs-lookup"><span data-stu-id="29258-166">Note that the AppPrincipalId begins with `00000004`.</span></span> <span data-ttu-id="29258-167">Это соответствует Skype для бизнеса Online.</span><span class="sxs-lookup"><span data-stu-id="29258-167">This corresponds to Skype for Business Online.</span></span>

   <span data-ttu-id="29258-168">Запишите (и снимок экрана для последующего сравнения) выходные данные этой команды, которые будут включать URL-адрес SE и WS, но в основном состоят из имен участников `00000004-0000-0ff1-ce00-000000000000/`-служб, начинающихся с.</span><span class="sxs-lookup"><span data-stu-id="29258-168">Take note of (and screenshot for later comparison) the output of this command, which will include an SE and WS URL, but mostly consist of SPNs that begin with `00000004-0000-0ff1-ce00-000000000000/`.</span></span>

```powershell
Get-MsolServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 | Select -ExpandProperty ServicePrincipalNames
```

3. <span data-ttu-id="29258-169">Если внутренние **или** внешние URL-адреса SFB из локальной сети отсутствуют (например, и https://lyncwebint01.contoso.com https://lyncwebext01.contoso.com) нам потребуется добавить эти записи в этот список).</span><span class="sxs-lookup"><span data-stu-id="29258-169">If the internal **or** external SFB URLs from on-premises are missing (for example, https://lyncwebint01.contoso.com and https://lyncwebext01.contoso.com) we will need to add those specific records to this list.</span></span>

    <span data-ttu-id="29258-170">Обязательно замените *Пример URL-адресов* , приведенный ниже, на фактические URL-адреса в разделе Add Commands!</span><span class="sxs-lookup"><span data-stu-id="29258-170">Be sure to replace  *the example URLs*  , below, with your actual URLs in the Add commands!</span></span>
  
```powershell
$x= Get-MsolServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000
$x.ServicePrincipalnames.Add("https://lyncwebint01.contoso.com/")
$x.ServicePrincipalnames.Add("https://lyncwebext01.contoso.com/")
Set-MSOLServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $x.ServicePrincipalNames
```
  
4. <span data-ttu-id="29258-171">Проверьте, были ли добавлены новые записи, выполнив команду **Get – MsolServicePrincipal** повторно с шага 2 и просмотрев результаты.</span><span class="sxs-lookup"><span data-stu-id="29258-171">Verify your new records were added by running the **Get-MsolServicePrincipal** command from step 2 again, and looking through the output.</span></span> <span data-ttu-id="29258-172">Сравнение списка и снимка экрана перед новым списком имен участников-служб (вы также можете создать список снимков экрана для записи).</span><span class="sxs-lookup"><span data-stu-id="29258-172">Compare the list / screenshot from before to the new list of SPNs (you may also screenshot the new list for your records).</span></span> <span data-ttu-id="29258-173">В случае успеха в списке отобразятся два новых URL-адреса.</span><span class="sxs-lookup"><span data-stu-id="29258-173">If you were successful, you will see the two new URLs in the list.</span></span> <span data-ttu-id="29258-174">В нашем примере список SPN теперь включает определенные URL-адреса https://lyncwebint01.contoso.com и. https://lyncwebext01.contoso.com/</span><span class="sxs-lookup"><span data-stu-id="29258-174">Going by our example, the list of SPNs will now include the specific URLs https://lyncwebint01.contoso.com and https://lyncwebext01.contoso.com/.</span></span>

### <a name="create-the-evosts-auth-server-object"></a><span data-ttu-id="29258-175">Создание объекта сервера проверки подлинности Евостс</span><span class="sxs-lookup"><span data-stu-id="29258-175">Create the EvoSTS Auth Server Object</span></span>

<span data-ttu-id="29258-176">Выполните следующую команду в командной консоли Skype для бизнеса.</span><span class="sxs-lookup"><span data-stu-id="29258-176">Run the following command in the Skype for Business Management Shell.</span></span>
  
```powershell
New-CsOAuthServer -Identity evoSTS -MetadataURL https://login.windows.net/common/FederationMetadata/2007-06/FederationMetadata.xml -AcceptSecurityIdentifierInformation $true -Type AzureAD
```

### <a name="enable-hybrid-modern-authentication"></a><span data-ttu-id="29258-177">Включение гибридной современной проверки подлинности</span><span class="sxs-lookup"><span data-stu-id="29258-177">Enable Hybrid Modern Authentication</span></span>

<span data-ttu-id="29258-178">Это шаг, который фактически включает мА.</span><span class="sxs-lookup"><span data-stu-id="29258-178">This is the step that actually turns MA on.</span></span> <span data-ttu-id="29258-179">Все предыдущие действия можно выполнить заранее, не изменяя поток проверки подлинности клиента.</span><span class="sxs-lookup"><span data-stu-id="29258-179">All the previous steps can be run ahead of time without changing the client authentication flow.</span></span> <span data-ttu-id="29258-180">Когда вы будете готовы изменить поток проверки подлинности, выполните эту команду в командной консоли Skype для бизнеса.</span><span class="sxs-lookup"><span data-stu-id="29258-180">When you are ready to change the authentication flow, run this command in the Skype for Business Management Shell.</span></span>

```powershell
Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity evoSTS
```

## <a name="verify"></a><span data-ttu-id="29258-181">Читаем</span><span class="sxs-lookup"><span data-stu-id="29258-181">Verify</span></span>

<span data-ttu-id="29258-182">После включения HMA для следующего входа клиента будет использоваться новый процесс проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="29258-182">Once you enable HMA, a client's next login will use the new auth flow.</span></span> <span data-ttu-id="29258-183">Обратите внимание, что просто включение HMA не вызывает повторную проверку подлинности для любого клиента.</span><span class="sxs-lookup"><span data-stu-id="29258-183">Note that just turning on HMA won't trigger a re-authentication for any client.</span></span> <span data-ttu-id="29258-184">Клиенты повторно проходят проверку подлинности на основе времени существования маркеров и/или сертификатов проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="29258-184">The clients re-authenticate based on the lifetime of the auth tokens and/or certs they have.</span></span>
  
<span data-ttu-id="29258-185">Чтобы проверить, работает ли сегмент HMA после включения, выйдите из тестового клиента Windows SFB и убедитесь, что выбран пункт "удалить мои учетные данные".</span><span class="sxs-lookup"><span data-stu-id="29258-185">To test that HMA is working after you've enabled it, sign out of a test SFB Windows client and be sure to click 'delete my credentials'.</span></span> <span data-ttu-id="29258-186">Выполните вход еще раз.</span><span class="sxs-lookup"><span data-stu-id="29258-186">Sign in again.</span></span> <span data-ttu-id="29258-187">Теперь клиент должен использовать современный процесс проверки подлинности, а ваш вход в систему будет включать в себя приглашение на **Office 365** для учетной записи "Рабочий или учебный", которая отображается прямо перед тем, как клиент обращается к серверу и выполняет вход в систему.</span><span class="sxs-lookup"><span data-stu-id="29258-187">The client should now use the Modern Auth flow and your login will now include an **Office 365** prompt for a 'Work or school' account, seen right before the client contacts the server and logs you in.</span></span>
  
<span data-ttu-id="29258-188">Кроме того, вы также можете проверить сведения о конфигурации для клиентов Skype для бизнеса для "центра OAuth".</span><span class="sxs-lookup"><span data-stu-id="29258-188">You should also check the 'Configuration Information' for Skype for Business Clients for an 'OAuth Authority'.</span></span> <span data-ttu-id="29258-189">Для этого на клиентском компьютере, удерживая клавишу CTRL, щелкните правой кнопкой мыши значок Skype для бизнеса в панели уведомлений Windows.</span><span class="sxs-lookup"><span data-stu-id="29258-189">To do this on your client computer, hold down the CTRL key at the same time you right-click the Skype for Business Icon in the Windows Notification tray.</span></span> <span data-ttu-id="29258-190">В появившемся меню выберите пункт **сведения о конфигурации** .</span><span class="sxs-lookup"><span data-stu-id="29258-190">Click **Configuration Information** in the menu that appears.</span></span> <span data-ttu-id="29258-191">В окне сведения о настройке Skype для бизнеса, которое будет отображаться на рабочем столе, найдите следующее:</span><span class="sxs-lookup"><span data-stu-id="29258-191">In the 'Skype for Business Configuration Information' window that will appear on the desktop, look for the following:</span></span>
  
![Сведения о конфигурации клиента Skype для бизнеса с современной проверкой подлинности показывает URL-адрес центра OAUTH и https://login.windows.net/common/oauth2/authorizeцентра OAuth EWS.](media/4e54edf5-c8f8-4e7f-b032-5d413b0232de.png)
  
<span data-ttu-id="29258-193">Кроме того, следует удерживать нажатой клавишу CTRL, щелкнув значок клиента Outlook (также в области уведомлений Windows), и выберите пункт "состояние подключения".</span><span class="sxs-lookup"><span data-stu-id="29258-193">You should also hold down the CTRL key at the same time you right click the icon for the Outlook client (also in the Windows Notifications tray) and click 'Connection Status'.</span></span> <span data-ttu-id="29258-194">Найдите SMTP-адрес клиента с типом определения "Bearer\*", который представляет токен носителя, используемый в OAuth.</span><span class="sxs-lookup"><span data-stu-id="29258-194">Look for the client's SMTP address against an AuthN type of 'Bearer\*', which represents the bearer token used in OAuth.</span></span>
  
## <a name="related-articles"></a><span data-ttu-id="29258-195">Статьи по теме</span><span class="sxs-lookup"><span data-stu-id="29258-195">Related articles</span></span>

<span data-ttu-id="29258-196">[Выполните обратное соединение с обзором современной проверки подлинности](hybrid-modern-auth-overview.md).</span><span class="sxs-lookup"><span data-stu-id="29258-196">[Link back to the Modern Authentication overview](hybrid-modern-auth-overview.md).</span></span>
  
<span data-ttu-id="29258-197">Вам нужно знать, как использовать современные проверки подлинности (ADAL) для клиентов Skype для бизнеса?</span><span class="sxs-lookup"><span data-stu-id="29258-197">Do you need to know how to use Modern Authentication (ADAL) for your Skype for Business clients?</span></span> <span data-ttu-id="29258-198">Мы познакомились с [этой](https://technet.microsoft.com/library/mt710548.aspx)статьей.</span><span class="sxs-lookup"><span data-stu-id="29258-198">We've got steps [here](https://technet.microsoft.com/library/mt710548.aspx).</span></span>
