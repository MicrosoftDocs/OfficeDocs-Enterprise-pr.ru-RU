---
title: Как настроить локальное развертывание Exchange Server для использования гибридной современной проверки подлинности
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 11/16/2018
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: cef3044d-d4cb-4586-8e82-ee97bd3b14ad
ms.collection:
- M365-security-compliance
f1.keywords:
- NOCSH
description: Гибридная современная проверка подлинности (HMA) — это способ управления удостоверениями, обеспечивающий более безопасную проверку подлинности и авторизацию пользователей, а также доступный для локальных гибридных развертываний Exchange Server.
ms.openlocfilehash: 6c4b57454b415b3af799d82e1c3655daa1fd5ef8
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/07/2020
ms.locfileid: "41840746"
---
# <a name="how-to-configure-exchange-server-on-premises-to-use-hybrid-modern-authentication"></a><span data-ttu-id="6a540-103">Как настроить локальное развертывание Exchange Server для использования гибридной современной проверки подлинности</span><span class="sxs-lookup"><span data-stu-id="6a540-103">How to configure Exchange Server on-premises to use Hybrid Modern Authentication</span></span>

<span data-ttu-id="6a540-104">*Эта статья относится к Office 365 корпоративный и Microsoft 365 корпоративный.*</span><span class="sxs-lookup"><span data-stu-id="6a540-104">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="6a540-105">Гибридная современная проверка подлинности (HMA) — это способ управления удостоверениями, обеспечивающий более безопасную проверку подлинности и авторизацию пользователей, а также доступный для локальных гибридных развертываний Exchange Server.</span><span class="sxs-lookup"><span data-stu-id="6a540-105">Hybrid Modern Authentication (HMA), is a method of identity management that offers more secure user authentication and authorization, and is available for Exchange server on-premises hybrid deployments.</span></span>
  
## <a name="fyi"></a><span data-ttu-id="6a540-106">СВЕДЕНИЮ</span><span class="sxs-lookup"><span data-stu-id="6a540-106">FYI</span></span>

<span data-ttu-id="6a540-107">Прежде чем начать, я вызываю:</span><span class="sxs-lookup"><span data-stu-id="6a540-107">Before we begin, I call:</span></span>
  
- <span data-ttu-id="6a540-108">Гибридная современная \> проверка подлинности HMA</span><span class="sxs-lookup"><span data-stu-id="6a540-108">Hybrid Modern Authentication \> HMA</span></span>
    
- <span data-ttu-id="6a540-109">Локальная \> служба Exchange (Дов)</span><span class="sxs-lookup"><span data-stu-id="6a540-109">Exchange on-premises \> EXCH</span></span>
    
- <span data-ttu-id="6a540-110">Exchange Online \> EXO</span><span class="sxs-lookup"><span data-stu-id="6a540-110">Exchange Online \> EXO</span></span>
    
<span data-ttu-id="6a540-111">Кроме того, *Если рисунок в этой статье содержит объект с серым или затемненным элементом, то это означает, что элемент, отображаемый серым цветом, не включается в конфигурацию, характерную для HMA* .</span><span class="sxs-lookup"><span data-stu-id="6a540-111">Also,  *if a graphic in this article has an object that's 'grayed-out' or 'dimmed' that means the element shown in gray is not included in HMA-specific configuration*  .</span></span> 
  
## <a name="enabling-hybrid-modern-authentication"></a><span data-ttu-id="6a540-112">Включение гибридной современной проверки подлинности</span><span class="sxs-lookup"><span data-stu-id="6a540-112">Enabling Hybrid Modern Authentication</span></span>

<span data-ttu-id="6a540-113">При повороте HMA на средних отключаются:</span><span class="sxs-lookup"><span data-stu-id="6a540-113">Turning HMA on means:</span></span>
  
1. <span data-ttu-id="6a540-114">Прежде чем приступить к работе, убедитесь, что вы соответствуете пререкс.</span><span class="sxs-lookup"><span data-stu-id="6a540-114">Being sure you meet the prereqs before you begin.</span></span>
    
1. <span data-ttu-id="6a540-115">Так как многие **Предварительные требования** распространены как для Skype для бизнеса, так и для Exchange, [Гибридная современная проверка подлинности и предварительные требования для их использования с локальными серверами Skype для бизнеса и Exchange](hybrid-modern-auth-overview.md).</span><span class="sxs-lookup"><span data-stu-id="6a540-115">Since many **prerequisites** are common for both Skype for Business and Exchange, [Hybrid Modern Authentication overview and prerequisites for using it with on-premises Skype for Business and Exchange servers](hybrid-modern-auth-overview.md).</span></span> <span data-ttu-id="6a540-116">Выполните это действие, прежде чем приступать к каким – либо действиям, описанным в этой статье.</span><span class="sxs-lookup"><span data-stu-id="6a540-116">Do this before you begin any of the steps in this article.</span></span>
    
2. <span data-ttu-id="6a540-117">Добавление локальных URL-адресов веб-служб в Azure AD в качестве имен участников-служб (SPN).</span><span class="sxs-lookup"><span data-stu-id="6a540-117">Adding on-premises web service URLs as Service Principal Names (SPNs) in Azure AD.</span></span>
    
3. <span data-ttu-id="6a540-118">Обеспечение включения всех виртуальных каталогов в верхнюю область памяти</span><span class="sxs-lookup"><span data-stu-id="6a540-118">Ensuring all Virtual Directories are enabled for HMA</span></span>
    
4. <span data-ttu-id="6a540-119">Проверка наличия объекта сервера проверки подлинности Евостс</span><span class="sxs-lookup"><span data-stu-id="6a540-119">Checking for the EvoSTS Auth Server object</span></span>
    
5. <span data-ttu-id="6a540-120">Включение HMA в КУРСах</span><span class="sxs-lookup"><span data-stu-id="6a540-120">Enabling HMA in EXCH.</span></span>
    
 <span data-ttu-id="6a540-121">**Note (Примечание** ) Поддерживает ли ваша версия Office мА?</span><span class="sxs-lookup"><span data-stu-id="6a540-121">**Note** Does your version of Office support MA?</span></span> <span data-ttu-id="6a540-122">Узнайте [, как работает современная проверка подлинности для клиентских приложений office 2013 и office 2016](modern-auth-for-office-2013-and-2016.md).</span><span class="sxs-lookup"><span data-stu-id="6a540-122">See [How modern authentication works for Office 2013 and Office 2016 client apps](modern-auth-for-office-2013-and-2016.md).</span></span>
  
## <a name="make-sure-you-meet-all-the-pre-reqs"></a><span data-ttu-id="6a540-123">Убедитесь, что вы соответствуете предварительным Рекс.</span><span class="sxs-lookup"><span data-stu-id="6a540-123">Make sure you meet all the pre-reqs</span></span>

<span data-ttu-id="6a540-124">Так как многие предварительные требования распространены как для Skype для бизнеса, так и для Exchange, ознакомьтесь с [обзором гибридной современной проверки подлинности и необходимыми требованиями для его использования с локальными серверами Skype для бизнеса и Exchange](hybrid-modern-auth-overview.md).</span><span class="sxs-lookup"><span data-stu-id="6a540-124">Since many prerequisites are common for both Skype for Business and Exchange, review [Hybrid Modern Authentication overview and prerequisites for using it with on-premises Skype for Business and Exchange servers](hybrid-modern-auth-overview.md).</span></span> <span data-ttu-id="6a540-125">Выполните это действие, *прежде чем* приступать к каким – либо действиям, описанным в этой статье.</span><span class="sxs-lookup"><span data-stu-id="6a540-125">Do this  *before*  you begin any of the steps in this article.</span></span> 
  
## <a name="add-on-premises-web-service-urls-as-spns-in-azure-ad"></a><span data-ttu-id="6a540-126">Добавление локальных URL-адресов веб-служб в Azure AD в качестве SPN</span><span class="sxs-lookup"><span data-stu-id="6a540-126">Add on-premises web service URLs as SPNs in Azure AD</span></span>

<span data-ttu-id="6a540-127">Выполните команды, которые назначают URL-адреса локальной веб-службы как SPN Azure AD.</span><span class="sxs-lookup"><span data-stu-id="6a540-127">Run the commands that assign your on-premises web service URLs as Azure AD SPNs.</span></span> <span data-ttu-id="6a540-128">Имена участников-служб используются клиентскими компьютерами и устройствами во время проверки подлинности и авторизации.</span><span class="sxs-lookup"><span data-stu-id="6a540-128">SPNs are used by client machines and devices during authentication and authorization.</span></span> <span data-ttu-id="6a540-129">Все URL-адреса, которые могут использоваться для подключения из локальной системы в Azure Active Directory (AAD), должны быть зарегистрированы в AAD (сюда входят как внутренние, так и внешние пространства имен).</span><span class="sxs-lookup"><span data-stu-id="6a540-129">All the URLs that might be used to connect from on-premises to Azure Active Directory (AAD) must be registered in AAD (this includes both internal and external namespaces).</span></span>
  
<span data-ttu-id="6a540-130">Сначала соберите все URL-адреса, которые необходимо добавить в AAD.</span><span class="sxs-lookup"><span data-stu-id="6a540-130">First, gather all the URLs that you need to add in AAD.</span></span> <span data-ttu-id="6a540-131">Выполните следующие команды в локальной среде:</span><span class="sxs-lookup"><span data-stu-id="6a540-131">Run these commands on-premises:</span></span>
  
```powershell
Get-MapiVirtualDirectory | FL server,*url*
Get-WebServicesVirtualDirectory | FL server,*url*
Get-ActiveSyncVirtualDirectory | FL server,*url*
Get-OABVirtualDirectory | FL server,*url*
```
    
<span data-ttu-id="6a540-132">Убедитесь, что URL-адреса, к которым могут подключаться клиенты, указаны как имена субъектов-служб HTTPS в AAD.</span><span class="sxs-lookup"><span data-stu-id="6a540-132">Ensure the URLs clients may connect to are listed as HTTPS service principal names in AAD.</span></span>
  
1. <span data-ttu-id="6a540-133">Для начала подключитесь к AAD с помощью [приведенных ниже инструкций](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell).</span><span class="sxs-lookup"><span data-stu-id="6a540-133">First, connect to AAD with [these instructions](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell).</span></span> 

 <span data-ttu-id="6a540-134">**Note (Примечание** ) Для использования указанной ниже команды необходимо использовать параметр Connect-MsolService на этой странице.</span><span class="sxs-lookup"><span data-stu-id="6a540-134">**Note** You need to use the Connect-MsolService option from this page to be able to use the command below.</span></span> 
    
2. <span data-ttu-id="6a540-135">Для URL-адресов, относящихся к Exchange, введите следующую команду:</span><span class="sxs-lookup"><span data-stu-id="6a540-135">For your Exchange related URLs, type the following command:</span></span>
    
```powershell
Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 | select -ExpandProperty ServicePrincipalNames
```

<span data-ttu-id="6a540-136">Запишите (и снимок экрана для последующего сравнения) выходные данные этой команды, которые должны содержать URL-адрес https:// *autodiscover.yourdomain.com* и HTTPS:// *mail.yourdomain.com* , но в основном состоит из имен участников-служб, начинающихся с 00000002-0000-0ff1-ce00-000000000000/.</span><span class="sxs-lookup"><span data-stu-id="6a540-136">Take note of (and screenshot for later comparison) the output of this command, which should include an https://  *autodiscover.yourdomain.com*  and https://  *mail.yourdomain.com*  URL, but mostly consist of SPNs that begin with 00000002-0000-0ff1-ce00-000000000000/.</span></span> <span data-ttu-id="6a540-137">Если у вас есть URL-адреса https://из локальной среды, которые отсутствуют, вам потребуется добавить эти записи в этот список.</span><span class="sxs-lookup"><span data-stu-id="6a540-137">If there are https:// URLs from your on-premises that are missing we will need to add those specific records to this list.</span></span> 
  
3. <span data-ttu-id="6a540-138">Если вы не видите внутреннюю и внешнюю записи MAPI/HTTP, EWS, ActiveSync, OAB и автообнаружения в этом списке, их необходимо добавить с помощью приведенной ниже команды (например, URL-адреса`mail.corp.contoso.com`"" и`owa.contoso.com`""), но вы **заменили свои примеры URL-адресов своими собственными** :</span><span class="sxs-lookup"><span data-stu-id="6a540-138">If you don't see your internal and external MAPI/HTTP, EWS, ActiveSync, OAB and Autodiscover records in this list, you must add them using the command below (the example URLs are '`mail.corp.contoso.com`' and '`owa.contoso.com`', but you'd **replace the example URLs with your own** ):</span></span> <br/>
```powershell
$x= Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000   
$x.ServicePrincipalnames.Add("https://mail.corp.contoso.com/")
$x.ServicePrincipalnames.Add("https://owa.contoso.com/")
Set-MSOLServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $x.ServicePrincipalNames
```
 
4. <span data-ttu-id="6a540-139">Проверьте, были ли добавлены новые записи, выполнив команду Get – MsolServicePrincipal повторно с шага 2 и просмотрев результаты.</span><span class="sxs-lookup"><span data-stu-id="6a540-139">Verify your new records were added by running the Get-MsolServicePrincipal command from step 2 again, and looking through the output.</span></span> <span data-ttu-id="6a540-140">Сравнение списка и снимка экрана перед новым списком имен участников-служб (вы также можете создать список снимков экрана для записи).</span><span class="sxs-lookup"><span data-stu-id="6a540-140">Compare the list / screenshot from before to the new list of SPNs (you may also screenshot the new list for your records).</span></span> <span data-ttu-id="6a540-141">В случае успеха в списке отобразятся два новых URL-адреса.</span><span class="sxs-lookup"><span data-stu-id="6a540-141">If you were successful, you will see the two new URLs in the list.</span></span> <span data-ttu-id="6a540-142">В нашем примере список SPN теперь включает определенные URL-адреса `https://mail.corp.contoso.com` и. `https://owa.contoso.com`</span><span class="sxs-lookup"><span data-stu-id="6a540-142">Going by our example, the list of SPNs will now include the specific URLs  `https://mail.corp.contoso.com`  and  `https://owa.contoso.com`.</span></span> 
  
## <a name="verify-virtual-directories-are-properly-configured"></a><span data-ttu-id="6a540-143">Проверка правильности настройки виртуальных каталогов</span><span class="sxs-lookup"><span data-stu-id="6a540-143">Verify Virtual Directories are Properly Configured</span></span>

<span data-ttu-id="6a540-144">Теперь проверьте правильность включения OAuth в Exchange для всех виртуальных каталогов, которые Outlook может использовать, выполнив следующие команды:</span><span class="sxs-lookup"><span data-stu-id="6a540-144">Now verify OAuth is properly enabled in Exchange on all of the Virtual Directories Outlook might use by running the following commands:</span></span>

```powershell
Get-MapiVirtualDirectory | FL server,*url*,*auth* 
Get-WebServicesVirtualDirectory | FL server,*url*,*oauth*
Get-OABVirtualDirectory | FL server,*url*,*oauth*
Get-AutoDiscoverVirtualDirectory | FL server,*oauth*
```

<span data-ttu-id="6a540-145">Проверьте выходные данные, чтобы убедиться в том, что **OAuth** включен для каждого из этих вдирс, он будет выглядеть примерно так, как показано в разделе "OAuth".</span><span class="sxs-lookup"><span data-stu-id="6a540-145">Check the output to make sure **OAuth** is enabled on each of these VDirs, it will look something like this (and the key thing to look at is 'OAuth');</span></span> 

```powershell
Get-MapiVirtualDirectory | fl server,*url*,*auth*
```

```
Server                        : EX1
InternalUrl                   : https://mail.contoso.com/mapi
ExternalUrl                   : https://mail.contoso.com/mapi
IISAuthenticationMethods      : {Ntlm, OAuth, Negotiate}
InternalAuthenticationMethods : {Ntlm, OAuth, Negotiate}
ExternalAuthenticationMethods : {Ntlm, OAuth, Negotiate}
```
  
<span data-ttu-id="6a540-146">Если OAuth отсутствует на каком-либо сервере и в любом из четырех виртуальных каталогов, необходимо добавить его с помощью соответствующих команд, прежде чем продолжить.</span><span class="sxs-lookup"><span data-stu-id="6a540-146">If OAuth is missing from any server and any of the four virtual directories then you need to add it using the relevant commands before proceeding.</span></span>
  
## <a name="confirm-the-evosts-auth-server-object-is-present"></a><span data-ttu-id="6a540-147">Подтвердите, что присутствует объект сервера проверки подлинности Евостс</span><span class="sxs-lookup"><span data-stu-id="6a540-147">Confirm the EvoSTS Auth Server Object is Present</span></span>

<span data-ttu-id="6a540-148">Вернитесь в локальную консоль управления Exchange для последней команды.</span><span class="sxs-lookup"><span data-stu-id="6a540-148">Return to the on-premises Exchange Management Shell for this last command.</span></span> <span data-ttu-id="6a540-149">Теперь вы можете проверить, что в локальной организации есть запись для поставщика проверки подлинности Евостс:</span><span class="sxs-lookup"><span data-stu-id="6a540-149">Now you can validate that your on-premises has an entry for the evoSTS authentication provider:</span></span>
  
```powershell
Get-AuthServer | where {$_.Name -eq "EvoSts"}
```

<span data-ttu-id="6a540-150">В выходных данных должен отображаться AuthServer имени Евостс, а состояние Enabled должно иметь значение true.</span><span class="sxs-lookup"><span data-stu-id="6a540-150">Your output should show an AuthServer of the Name EvoSts and the 'Enabled' state should be True.</span></span> <span data-ttu-id="6a540-151">Если вы не видите это значение, скачайте и запустите последнюю версию мастера гибридной конфигурации.</span><span class="sxs-lookup"><span data-stu-id="6a540-151">If you don't see this, you should download and run the most recent version of the Hybrid Configuration Wizard.</span></span>
  
 <span data-ttu-id="6a540-152">**Важно!** Если вы используете Exchange 2010 в своей среде, то поставщик проверки подлинности Евостс не будет создан.</span><span class="sxs-lookup"><span data-stu-id="6a540-152">**Important** If you're running Exchange 2010 in your environment, the EvoSTS authentication provider won't be created.</span></span> 
  
## <a name="enable-hma"></a><span data-ttu-id="6a540-153">Включение HMA</span><span class="sxs-lookup"><span data-stu-id="6a540-153">Enable HMA</span></span>

<span data-ttu-id="6a540-154">Выполните в командной консоли Exchange следующую команду:</span><span class="sxs-lookup"><span data-stu-id="6a540-154">Run the following command in the Exchange Management Shell, on-premises:</span></span>

```powershell
Set-AuthServer -Identity EvoSTS -IsDefaultAuthorizationEndpoint $true  
Set-OrganizationConfig -OAuth2ClientProfileEnabled $true
```
    
## <a name="verify"></a><span data-ttu-id="6a540-155">Читаем</span><span class="sxs-lookup"><span data-stu-id="6a540-155">Verify</span></span>

<span data-ttu-id="6a540-156">После включения HMA для следующего входа клиента будет использоваться новый процесс проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="6a540-156">Once you enable HMA, a client's next login will use the new auth flow.</span></span> <span data-ttu-id="6a540-157">Обратите внимание, что просто включение HMA не вызывает повторную проверку подлинности для любого клиента.</span><span class="sxs-lookup"><span data-stu-id="6a540-157">Note that just turning on HMA won't trigger a re-authentication for any client.</span></span> <span data-ttu-id="6a540-158">Клиенты повторно проходят проверку подлинности на основе времени существования маркеров и/или сертификатов проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="6a540-158">The clients re-authenticate based on the lifetime of the auth tokens and/or certs they have.</span></span>
  
<span data-ttu-id="6a540-159">Кроме того, следует удерживать нажатой клавишу CTRL, щелкнув значок клиента Outlook (также в области уведомлений Windows), и выберите пункт "состояние подключения".</span><span class="sxs-lookup"><span data-stu-id="6a540-159">You should also hold down the CTRL key at the same time you right click the icon for the Outlook client (also in the Windows Notifications tray) and click 'Connection Status'.</span></span> <span data-ttu-id="6a540-160">Найдите SMTP-адрес клиента для типа "определения" носителя "Bearer\*", который представляет токен носителя, используемый в OAuth.</span><span class="sxs-lookup"><span data-stu-id="6a540-160">Look for the client's SMTP address against an 'Authn' type of 'Bearer\*', which represents the bearer token used in OAuth.</span></span>
  
 <span data-ttu-id="6a540-161">**Note (Примечание** ) Требуется настроить Skype для бизнеса с HMA?</span><span class="sxs-lookup"><span data-stu-id="6a540-161">**Note** Need to configure Skype for Business with HMA?</span></span> <span data-ttu-id="6a540-162">Вам потребуются две статьи: одна, в которой перечислены [Поддерживаемые топологии](https://docs.microsoft.com/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported)и одна, которая показывает, [как выполнить настройку](configure-skype-for-business-for-hybrid-modern-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="6a540-162">You'll need two articles: One that lists [supported topologies](https://docs.microsoft.com/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported), and one that shows you [how to do the configuration](configure-skype-for-business-for-hybrid-modern-authentication.md).</span></span>
 
## <a name="using-hybrid-modern-authentication-with-outlook-for-ios-and-android"></a><span data-ttu-id="6a540-163">Гибридная современная проверка подлинности в случае Outlook для iOS и Android</span><span class="sxs-lookup"><span data-stu-id="6a540-163">Using hybrid Modern Authentication with Outlook for iOS and Android</span></span>

<span data-ttu-id="6a540-164">Если вы являетесь локальным клиентом, использующим Exchange Server по протоколу TCP 443, белом следующие диапазоны IP-адресов: </span><span class="sxs-lookup"><span data-stu-id="6a540-164">If you are an on-premises customer using Exchange server on TCP 443, please whitelist the following IP ranges:  </span></span><BR> ```52.125.128.0/20``` <BR> ```52.127.96.0/23``` <BR> 
  

## <a name="related-topics"></a><span data-ttu-id="6a540-165">Связанные статьи</span><span class="sxs-lookup"><span data-stu-id="6a540-165">Related topics</span></span>

[<span data-ttu-id="6a540-166">Обзор гибридной современной проверки подлинности и предварительные требования для их использования с локальными серверами Skype для бизнеса и Exchange</span><span class="sxs-lookup"><span data-stu-id="6a540-166">Hybrid Modern Authentication overview and prerequisites for using it with on-premises Skype for Business and Exchange servers</span></span>](hybrid-modern-auth-overview.md) 
  
<span data-ttu-id="6a540-167">Включение современной проверки подлинности для пользователей Outlook</span><span class="sxs-lookup"><span data-stu-id="6a540-167">Force Outlook users to Modern Authentication</span></span>  
[<span data-ttu-id="6a540-168">Требования к конфигурации современного режима проверки подлинности для перехода от Office 365 выделенный/ITAR к vNext</span><span class="sxs-lookup"><span data-stu-id="6a540-168">Modern Authentication configuration requirements for transition from Office 365 dedicated/ITAR to vNext</span></span>](modern-authentication-configuration.md)
