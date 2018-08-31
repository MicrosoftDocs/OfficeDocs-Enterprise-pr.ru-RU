---
title: Как настроить локальное развертывание Skype для бизнеса для использования гибридной современной проверки подлинности
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 6/4/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 522d5cec-4e1b-4cc3-937f-293570717bc6
description: Проверка подлинности для современных способ управления удостоверениями, которое предлагает более безопасной проверки подлинности пользователя и авторизации, доступных для Скайп для Business server локальной и Exchange server в локальной, а также Скайп разделенного домена для бизнеса гибридные устройства.
ms.openlocfilehash: 48ce10022e384ec88b88c0e8ec038bf201adc707
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542655"
---
# <a name="how-to-configure-skype-for-business-on-premises-to-use-hybrid-modern-authentication"></a><span data-ttu-id="c29d8-103">Как настроить локальное развертывание Skype для бизнеса для использования гибридной современной проверки подлинности</span><span class="sxs-lookup"><span data-stu-id="c29d8-103">How to configure Skype for Business on-premises to use Hybrid Modern Authentication</span></span>

<span data-ttu-id="c29d8-104">Проверка подлинности для современных способ управления удостоверениями, которое предлагает более безопасной проверки подлинности пользователя и авторизации, доступных для Скайп для Business server локальной и Exchange server в локальной, а также Скайп разделенного домена для бизнеса гибридные устройства.</span><span class="sxs-lookup"><span data-stu-id="c29d8-104">Modern Authentication, is a method of identity management that offers more secure user authentication and authorization, is available for Skype for Business server on-premises and Exchange server on-premises, as well as split-domain Skype for Business hybrids.</span></span>
  
 <span data-ttu-id="c29d8-p101">**Важные** Вы хотите узнать больше о современных проверки подлинности (агент Управления) и почему вы предпочитаете использовать в вашей организации? Поиск [в этом документе](hybrid-modern-auth-overview.md) Обзор. Если необходимо знать, какие Скайп Business топологии поддерживаемые с помощью агента Управления, здесь описаны!</span><span class="sxs-lookup"><span data-stu-id="c29d8-p101">**Important** Would you like to know more about Modern Authentication (MA) and why you might prefer to use it in your company or organization? Check [this document](hybrid-modern-auth-overview.md) for an overview. If you need to know what Skype for Business topologies are supported with MA, that's documented here!</span></span> 
  
 <span data-ttu-id="c29d8-108">**Прежде чем начать**, ли вызов:</span><span class="sxs-lookup"><span data-stu-id="c29d8-108">**Before we begin**, I call:</span></span> 
  
- <span data-ttu-id="c29d8-109">Современный проверки подлинности \> агента Управления</span><span class="sxs-lookup"><span data-stu-id="c29d8-109">Modern Authentication \> MA</span></span>
    
- <span data-ttu-id="c29d8-110">Современный проверки подлинности гибридной \> НЕГО</span><span class="sxs-lookup"><span data-stu-id="c29d8-110">Hybrid Modern Authentication \> HMA</span></span>
    
- <span data-ttu-id="c29d8-111">Exchange в локальной \> EXCH</span><span class="sxs-lookup"><span data-stu-id="c29d8-111">Exchange on-premises \> EXCH</span></span>
    
- <span data-ttu-id="c29d8-112">Exchange Online \> EXO</span><span class="sxs-lookup"><span data-stu-id="c29d8-112">Exchange Online \> EXO</span></span>
    
- <span data-ttu-id="c29d8-113">Скайп для бизнеса в локальной \> SFB</span><span class="sxs-lookup"><span data-stu-id="c29d8-113">Skype for Business on-premises \> SFB</span></span>
    
- <span data-ttu-id="c29d8-114">и Скайп для бизнеса в Интернете \> SFBO</span><span class="sxs-lookup"><span data-stu-id="c29d8-114">and Skype for Business Online \> SFBO</span></span>
    
<span data-ttu-id="c29d8-115">Кроме того \* Если графического элемента в данной статье есть объект, который «серым» или «недоступен», который означает, что элемент, приведенные в серую **не** включены в конфигурации агента Управления.</span><span class="sxs-lookup"><span data-stu-id="c29d8-115">Also,  \*if a graphic in this article has an object that's 'grayed-out' or 'dimmed' that means the element shown in gray **is not** included in MA-specific configuration.</span></span> * 
  
## <a name="read-the-summary"></a><span data-ttu-id="c29d8-116">Ознакомьтесь с краткими сведениями</span><span class="sxs-lookup"><span data-stu-id="c29d8-116">Read the summary</span></span>

<span data-ttu-id="c29d8-117">В этом Сводка сводится процесс в действия, которые в противном случае — получить потеряны во время выполнения и хорошо подходит для общего контрольный список для записи сведений о где находятся в процессе.</span><span class="sxs-lookup"><span data-stu-id="c29d8-117">This summary boils the process into steps that might otherwise get lost during the execution, and is good for an overall check-list to keep track of where you are in the process.</span></span>
  
1. <span data-ttu-id="c29d8-118">Во-первых убедитесь, что соблюдены все необходимые компоненты.</span><span class="sxs-lookup"><span data-stu-id="c29d8-118">First, make sure you meet all the prerequisites.</span></span>
    
1. <span data-ttu-id="c29d8-p102">С момента множество **необходимых компонентов** являются общими для обоих Скайп для бизнеса и Exchange, [в статье Обзор контрольному списку версии, предшествующей требования](hybrid-modern-auth-overview.md). Сделать этот *перед* началом работы какие-либо действия, описанные в этой статье.</span><span class="sxs-lookup"><span data-stu-id="c29d8-p102">Since many **prerequisites** are common for both Skype for Business and Exchange, [see the overview article for your pre-req checklist](hybrid-modern-auth-overview.md). Do this  *before*  you begin any of the steps in this article.</span></span> 
    
2. <span data-ttu-id="c29d8-121">Сбор информации зависящие от НЕГО вам в виде файла или OneNote.</span><span class="sxs-lookup"><span data-stu-id="c29d8-121">Collect the HMA-specific info you'll need in a file, or OneNote.</span></span>
    
3. <span data-ttu-id="c29d8-122">Turn ON современных проверки подлинности для EXO (если он еще не включен).</span><span class="sxs-lookup"><span data-stu-id="c29d8-122">Turn ON Modern Authentication for EXO (if it is not already turned on).</span></span>
    
4. <span data-ttu-id="c29d8-123">Turn ON современных проверки подлинности для SFBO (если он еще не включен).</span><span class="sxs-lookup"><span data-stu-id="c29d8-123">Turn ON Modern Authentication for SFBO (if it is not already turned on).</span></span>
    
5. <span data-ttu-id="c29d8-124">Включение гибридного современных проверки подлинности для локальную систему Exchange.</span><span class="sxs-lookup"><span data-stu-id="c29d8-124">Turn ON Hybrid Modern Authentication for Exchange on-premises.</span></span>
    
6. <span data-ttu-id="c29d8-125">Включение гибридного современных проверки подлинности для Скайп для бизнеса в локальной.</span><span class="sxs-lookup"><span data-stu-id="c29d8-125">Turn ON Hybrid Modern Authentication for Skype for Business on-premises.</span></span>
    
<span data-ttu-id="c29d8-p103">Обратите внимание, что эти шаги включить агент Управления для SFB, SFBO, EXCH и EXO — то есть, все продукты, которые могут принимать участие в НЕГО конфигурации SFB и SFBO (включая зависимости с EXCH/EXO). Другими словами Если пользователи размещены в аудио- и почтовые ящики были созданы в любой части гибридного (EXO + SFBO, EXO + SFB, EXCH + SFBO, или EXCH + SFB), по завершении работы продукта будет выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="c29d8-p103">Note These steps turn on MA for SFB, SFBO, EXCH, and EXO -- that is, all the products that can participate in a HMA configuration of SFB and SFBO (including dependencies on EXCH/EXO). In other words, if your users are homed in/have mailboxes created in any part of the Hybrid (EXO + SFBO, EXO + SFB, EXCH + SFBO, or EXCH + SFB), your finished product will look like this:</span></span>
  
![Смешанные Скайп 6 для НЕГО топологии business дает агент Управления всех четырех возможных расположений.](media/ab89cdf2-160b-49ac-9b71-0160800acfc8.png)
  
<span data-ttu-id="c29d8-p104">Как вы видите, что существует четыре различных местах, чтобы включить агент Управления! Для обеспечения наилучшего взаимодействия пользователей мы рекомендуем включить агент Управления в все четыре местоположениях. Если агент Управления нельзя включить в этих расположениях, скорректировать действия, чтобы включить агент Управления только в расположениях, которые необходимы для вашей среды.</span><span class="sxs-lookup"><span data-stu-id="c29d8-p104">As you can see there are four different places to turn on MA! For the best user experience we recommend you turn on MA in all four of these locations. If you can't turn MA on in all these locations, adjust the steps so that you turn on MA only in the locations that are necessary for your environment.</span></span>
  
<span data-ttu-id="c29d8-132">Перейдите в [раздел технической поддержке для Скайп для бизнеса с помощью агента Управления](https://technet.microsoft.com/en-us/library/mt803262.aspx) для поддерживаемых топологий.</span><span class="sxs-lookup"><span data-stu-id="c29d8-132">See the [Supportability topic for Skype for Business with MA](https://technet.microsoft.com/en-us/library/mt803262.aspx) for supported topologies.</span></span> 
  
 <span data-ttu-id="c29d8-p105">**Важные** Проверьте, что вы выполнили все все необходимые компоненты, прежде чем приступить к работе. Эти сведения можно найти [здесь](hybrid-modern-auth-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c29d8-p105">**Important** Double-check that you've met all the prerequisites before you begin. You'll find that information [here](hybrid-modern-auth-overview.md).</span></span>
  
## <a name="collect-all-hma-specific-info-youll-need"></a><span data-ttu-id="c29d8-135">Соберите все зависящие от НЕГО сведения, необходимые</span><span class="sxs-lookup"><span data-stu-id="c29d8-135">Collect all HMA-specific info you'll need</span></span>

<span data-ttu-id="c29d8-p106">После вы уверены, необходимо выполнить [Предварительные требования](hybrid-modern-auth-overview.md) для использования современных проверки подлинности (см. Примечание выше), необходимо создать файл для хранения сведения, необходимые для настройки НЕГО в действия издержек. Примеры, используемые в этой статье:</span><span class="sxs-lookup"><span data-stu-id="c29d8-p106">After you've double-checked that you meet the [prerequisites](hybrid-modern-auth-overview.md) to use Modern Authentication (see the note above), you should create a file to hold the info you'll need for configuring HMA in the steps ahead. Examples used in this article:</span></span> 
  
- <span data-ttu-id="c29d8-138">**Домен SIP/SMTP**</span><span class="sxs-lookup"><span data-stu-id="c29d8-138">**SIP/SMTP domain**</span></span>
    
  - <span data-ttu-id="c29d8-p107">Например contoso.com (федеративные с Office 365)</span><span class="sxs-lookup"><span data-stu-id="c29d8-p107">Ex. contoso.com (is federated with Office 365)</span></span>
    
- <span data-ttu-id="c29d8-141">**ИД клиента**</span><span class="sxs-lookup"><span data-stu-id="c29d8-141">**Tenant ID**</span></span>
    
  - <span data-ttu-id="c29d8-142">Идентификатор GUID, представляющий клиента Office 365 (на входа contoso.onmicrosoft.com).</span><span class="sxs-lookup"><span data-stu-id="c29d8-142">The GUID that represents your Office 365 tenant (at the login of contoso.onmicrosoft.com).</span></span>
    
- <span data-ttu-id="c29d8-143">**URL-адреса SFB 2015 накопительным пакетом обновления 5 Web служб**</span><span class="sxs-lookup"><span data-stu-id="c29d8-143">**SFB 2015 CU5 Web Service URLs**</span></span>
    
<span data-ttu-id="c29d8-p108">Внутренние и внешние веб-службы URL потребуется для всех пулов SfB 2015 развернут. Для получения этих, выполните следующую из Скайп оболочки управления бизнеса:</span><span class="sxs-lookup"><span data-stu-id="c29d8-p108">You will need internal and external web service URL's for all SfB 2015 pools deployed. To obtain these, run the following from Skype for Business Management Shell:</span></span>
  
<span data-ttu-id="c29d8-146">Командлет Get-CsService - WebServer | ExternalFqdn PoolFqdn Select-Object, InternalFqdn, | FL</span><span class="sxs-lookup"><span data-stu-id="c29d8-146">Get-CsService -WebServer | Select-Object PoolFqdn, InternalFqdn, ExternalFqdn | FL</span></span>
  
- <span data-ttu-id="c29d8-p109">Например внутреннего:https://lyncwebint01.contoso.com</span><span class="sxs-lookup"><span data-stu-id="c29d8-p109">Ex. Internal: https://lyncwebint01.contoso.com</span></span>
    
- <span data-ttu-id="c29d8-p110">Внешние например:https://lyncwebext01.contoso.com</span><span class="sxs-lookup"><span data-stu-id="c29d8-p110">Ex. External: https://lyncwebext01.contoso.com</span></span>
    
<span data-ttu-id="c29d8-p111">При использовании стандартного выпуска сервера внутренний URL-адрес будет пустым. В этом случае используйте полное доменное имя пула для внутреннего URL-адреса.</span><span class="sxs-lookup"><span data-stu-id="c29d8-p111">If you are using a Standard Edition server, the internal URL will be blank. In this case, use the pool fqdn for the internal URL.</span></span>
  
## <a name="turn-on-modern-authentication-for-exo"></a><span data-ttu-id="c29d8-153">Включение современных проверки подлинности для EXO</span><span class="sxs-lookup"><span data-stu-id="c29d8-153">Turn on Modern Authentication for EXO</span></span>

<span data-ttu-id="c29d8-154">Следуйте инструкциям,: [Exchange Online: Включение вашего клиента для проверки подлинности на современном.](https://social.technet.microsoft.com/wiki/contents/articles/32711.exchange-online-how-to-enable-your-tenant-for-modern-authentication.aspx)</span><span class="sxs-lookup"><span data-stu-id="c29d8-154">Follow the instructions here: [Exchange Online: How to enable your tenant for modern authentication.](https://social.technet.microsoft.com/wiki/contents/articles/32711.exchange-online-how-to-enable-your-tenant-for-modern-authentication.aspx)</span></span>
  
## <a name="turn-on-modern-authentication-for-sfbo"></a><span data-ttu-id="c29d8-155">Включение современных проверки подлинности для SFBO</span><span class="sxs-lookup"><span data-stu-id="c29d8-155">Turn on Modern Authentication for SFBO</span></span>

<span data-ttu-id="c29d8-156">Следуйте инструкциям,: [Скайп для бизнеса Online: Включение вашего клиента для проверки подлинности на современном](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx).</span><span class="sxs-lookup"><span data-stu-id="c29d8-156">Follow the instructions here: [Skype for Business Online: Enable your tenant for modern authentication](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx).</span></span>
  
## <a name="turn-on-hybrid-modern-authentication-for-exchange-on-premises"></a><span data-ttu-id="c29d8-157">Включение гибридного современных проверки подлинности для локальную систему Exchange</span><span class="sxs-lookup"><span data-stu-id="c29d8-157">Turn on Hybrid Modern Authentication for Exchange on-premises</span></span>

<span data-ttu-id="c29d8-158">Следуйте инструкциям,: [Настройка Exchange Server в локальной для использования проверки подлинности современных гибридного](configure-exchange-server-for-hybrid-modern-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="c29d8-158">Follow the instructions here: [How to configure Exchange Server on-premises to use Hybrid Modern Authentication](configure-exchange-server-for-hybrid-modern-authentication.md).</span></span>
  
## <a name="turn-on-hybrid-modern-authentication-for-skype-for-business-on-premises"></a><span data-ttu-id="c29d8-159">Включение гибридного современных проверки подлинности для Скайп для бизнеса в локальной</span><span class="sxs-lookup"><span data-stu-id="c29d8-159">Turn on Hybrid Modern Authentication for Skype for Business on-premises</span></span>

### <a name="add-on-premises-web-service-urls-as-spns-in-azure-ad"></a><span data-ttu-id="c29d8-160">Добавление локального веб-службы URL-адреса как имена участников-служб в Azure AD</span><span class="sxs-lookup"><span data-stu-id="c29d8-160">Add on-premises web service URLs as SPNs in Azure AD</span></span>

<span data-ttu-id="c29d8-161">Теперь необходимо запустить команды, чтобы добавить URL-адреса (собирать более ранних версий) в качестве субъектов-служб в SFBO.</span><span class="sxs-lookup"><span data-stu-id="c29d8-161">Now you'll need to run commands to add the URLs (collected earlier) as Service Principals in SFBO.</span></span>
  
 <span data-ttu-id="c29d8-p112">**Примечание** Имена участников служб (SPN) определение веб-служб и свяжите их с участника безопасности (например, имя учетной записи или группы), чтобы служба могут действовать от имени этого авторизованный пользователь. Клиенты, проверка подлинности на сервере использовать сведения на содержащихся в имена участников-служб.</span><span class="sxs-lookup"><span data-stu-id="c29d8-p112">**Note** Service principal names (SPNs) identify web services and associate them with a security principal (such as an account name or group) so that the service can act on the behalf of an authorized user. Clients authenticating to a server make use of information that's contained in SPNs.</span></span> 
  
1. <span data-ttu-id="c29d8-164">Во-первых подключение к AAD с [этим инструкциям](https://docs.microsoft.com/en-us/powershell/azure/active-directory/install-adv2?view=azureadps-2.0).</span><span class="sxs-lookup"><span data-stu-id="c29d8-164">First, connect to AAD with [these instructions](https://docs.microsoft.com/en-us/powershell/azure/active-directory/install-adv2?view=azureadps-2.0).</span></span>
    
2. <span data-ttu-id="c29d8-165">Выполните эту команду, локальная, чтобы получить список URL-адреса служб web SFB.</span><span class="sxs-lookup"><span data-stu-id="c29d8-165">Run this command, on-premises, to get a list of SFB web service URLs.</span></span>
    
  - <span data-ttu-id="c29d8-166">Get-MsolServicePrincipal - AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 | Выберите ServicePrincipalNames - ExpandProperty</span><span class="sxs-lookup"><span data-stu-id="c29d8-166">Get-MsolServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 | Select -ExpandProperty ServicePrincipalNames</span></span>
    
    <span data-ttu-id="c29d8-p113">Обратите внимание на то, что AppPrincipalId начинается с "00000004". Это соответствует Скайп для бизнеса в Интернет.</span><span class="sxs-lookup"><span data-stu-id="c29d8-p113">Notice that the AppPrincipalId begins with '00000004'. This corresponds to Skype for Business Online.</span></span>
    
    <span data-ttu-id="c29d8-169">Принимать сообщения с (и снимок экрана для дальнейшего сравнения) выходные данные этой команды, которая включают в себя SE и WS URL-адрес, но в основном состоят из имен участников-служб, начинающихся с 00000004-0000-0ff1-ce00-000000000000 /.</span><span class="sxs-lookup"><span data-stu-id="c29d8-169">Take note of (and screenshot for later comparison) the output of this command, which will include an SE and WS URL, but mostly consist of SPNs that begin with 00000004-0000-0ff1-ce00-000000000000/.</span></span>
    
3. <span data-ttu-id="c29d8-170">Если внутренний **или** внешний URL-адресов SFB из локальной отсутствуют (например, https://lyncwebint01.contoso.com и https://lyncwebext01.contoso.com) будет необходимо добавить записи, определенные в этот список.</span><span class="sxs-lookup"><span data-stu-id="c29d8-170">If the internal **or** external SFB URLs from on-premises are missing (for example, https://lyncwebint01.contoso.com and https://lyncwebext01.contoso.com) we will need to add those specific records to this list.</span></span> 
    
    <span data-ttu-id="c29d8-171">Убедитесь, что замените *Примеры URL-адресов* , ниже, фактический URL-адресов в списке добавить команды!</span><span class="sxs-lookup"><span data-stu-id="c29d8-171">Be sure to replace  *the example URLs*  , below, with your actual URLs in the Add commands!</span></span> 
    
  - <span data-ttu-id="c29d8-172">$x = get-MsolServicePrincipal - AppPrincipalId 00000004-0000-0ff1-ce00-000000000000</span><span class="sxs-lookup"><span data-stu-id="c29d8-172">$x= Get-MsolServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000</span></span>
    
  - <span data-ttu-id="c29d8-173">$x.ServicePrincipalnames.Add (" *https://lyncwebint01.contoso.com/* ")</span><span class="sxs-lookup"><span data-stu-id="c29d8-173">$x.ServicePrincipalnames.Add(" *https://lyncwebint01.contoso.com/*  ")</span></span> 
    
  - <span data-ttu-id="c29d8-174">$x.ServicePrincipalnames.Add (" *https://lyncwebext01.contoso.com/* ")</span><span class="sxs-lookup"><span data-stu-id="c29d8-174">$x.ServicePrincipalnames.Add(" *https://lyncwebext01.contoso.com/*  ")</span></span> 
    
  - <span data-ttu-id="c29d8-175">SET-MSOLServicePrincipal - AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 - ServicePrincipalNames $x.ServicePrincipalNames</span><span class="sxs-lookup"><span data-stu-id="c29d8-175">Set-MSOLServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $x.ServicePrincipalNames</span></span>
    
4. <span data-ttu-id="c29d8-p114">Убедитесь, что были добавлены новые записи, выполнив команду Get-MsolServicePrincipal на шаге 2 еще раз и просмотр выходных данных. Сравните список / снимок экрана с перед новый список имен участников-служб (можно также снимок экрана нового списка для записи). Если вы было выполнено успешно, вы увидите две новые URL-адресов в списке. Переход в нашем примере список имен участников-служб будут включать конкретные URL-адреса https://lyncweb01.contoso.com и https://autodiscover.contoso.com.</span><span class="sxs-lookup"><span data-stu-id="c29d8-p114">Verify your new records were added by running the Get-MsolServicePrincipal command from step 2 again, and looking through the output. Compare the list / screenshot from before to the new list of SPNs (you may also screenshot the new list for your records). If you were successful, you will see the two new URLs in the list. Going by our example, the list of SPNs will now include the specific URLs https://lyncweb01.contoso.com and https://autodiscover.contoso.com.</span></span>
    
### <a name="create-the-evosts-auth-server-object"></a><span data-ttu-id="c29d8-180">Создание объекта EvoSTS проверкой подлинности на основе сервера</span><span class="sxs-lookup"><span data-stu-id="c29d8-180">Create the EvoSTS Auth Server Object</span></span>

<span data-ttu-id="c29d8-181">Выполните следующую команду в Скайп оболочки управления бизнеса.</span><span class="sxs-lookup"><span data-stu-id="c29d8-181">Run the following command in the Skype for Business Management Shell.</span></span>
  
- <span data-ttu-id="c29d8-182">Командлет New-CsOAuthServer-Identity evoSTS - MetadataURL https://login.windows.net/common/FederationMetadata/2007-06/FederationMetadata.xml - AcceptSecurityIdentifierInformation $true-AzureAD тип</span><span class="sxs-lookup"><span data-stu-id="c29d8-182">New-CsOAuthServer -Identity evoSTS -MetadataURL https://login.windows.net/common/FederationMetadata/2007-06/FederationMetadata.xml -AcceptSecurityIdentifierInformation $true -Type AzureAD</span></span>
    
### <a name="enable-hybrid-modern-authentication"></a><span data-ttu-id="c29d8-183">Включить проверку подлинности на современном гибридного</span><span class="sxs-lookup"><span data-stu-id="c29d8-183">Enable Hybrid Modern Authentication</span></span>

<span data-ttu-id="c29d8-p115">Это шаг, который фактически включается агент Управления. Все предыдущие действия может выполняться заранее без изменения поток проверки подлинности клиента. Когда вы готовы для изменения поток проверки подлинности, выполните эту команду в Скайп оболочки управления бизнеса.</span><span class="sxs-lookup"><span data-stu-id="c29d8-p115">This is the step that actually turns MA on. All the previous steps can be run ahead of time without changing the client authentication flow. When you are ready to change the authentication flow, run this command in the Skype for Business Management Shell.</span></span> 
  
- <span data-ttu-id="c29d8-187">SET-CsOAuthConfiguration - ClientAuthorizationOAuthServerIdentity evoSTS</span><span class="sxs-lookup"><span data-stu-id="c29d8-187">Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity evoSTS</span></span>
    
## <a name="verify"></a><span data-ttu-id="c29d8-188">"Проверить"</span><span class="sxs-lookup"><span data-stu-id="c29d8-188">Verify</span></span>

<span data-ttu-id="c29d8-p116">После включения НЕГО клиента следующем входе в систему будет использовать новый поток проверки подлинности. Обратите внимание на то, что только что включение НЕГО не запустит повторная проверка подлинности для любого клиента. Клиенты повторно пройти проверку подлинности на основе времени жизни проверкой подлинности на основе маркеров и/или сертификаты у них.</span><span class="sxs-lookup"><span data-stu-id="c29d8-p116">Once you enable HMA, a client's next login will use the new auth flow. Note that just turning on HMA won't trigger a re-authentication for any client. The clients re-authenticate based on the lifetime of the auth tokens and/or certs they have.</span></span>
  
<span data-ttu-id="c29d8-p117">Для проверки работы НЕГО после его включения, выход из тестового клиента SFB Windows и нажмите кнопку «удалить учетные данные». Снова выполните вход. Клиент должен использовать теперь поток проверкой подлинности на основе современных и имя входа теперь будет включать строки **Office 365** для «рабочий или школа» учетная запись, видимых непосредственно перед клиент связывается с сервером и вход в.</span><span class="sxs-lookup"><span data-stu-id="c29d8-p117">To test that HMA is working after you've enabled it, sign out of a test SFB Windows client and be sure to click 'delete my credentials'. Sign in again. The client should now use the Modern Auth flow and your login will now include an **Office 365** prompt for a 'Work or school' account, seen right before the client contacts the server and logs you in.</span></span> 
  
<span data-ttu-id="c29d8-p118">Также следует проверить «Сведения о конфигурации» для Скайп пользователей для «OAuth сертификации». Для этого на клиентском компьютере, в то же время, щелкнуть правой кнопкой мыши Скайп для бизнеса значок в области уведомлений Windows удерживайте нажатой клавишу CTRL. Нажмите кнопку сведения о конфигурации в появившемся меню. В окне «Скайп для настройки бизнес-информация», которое будет отображаться на рабочем столе Найдите следующее:</span><span class="sxs-lookup"><span data-stu-id="c29d8-p118">You should also check the 'Configuration Information' for Skype for Business Clients for an 'OAuth Authority'. To do this on your client computer, hold down the CTRL key at the same time you right-click the Skype for Business Icon in the Windows Notification tray. Click Configuration Information in the menu that appears. In the 'Skype for Business Configuration Information' window that will appear on the desktop, look for the following:</span></span>
  
![Сведения о Скайп конфигурации для бизнеса клиента с помощью проверки подлинности на современном показаны Lync и веб-служб Exchange OAUTH сертификации URL-адрес https://login.windows.net/common/oauth2/authorize.](media/4e54edf5-c8f8-4e7f-b032-5d413b0232de.png)
  
<span data-ttu-id="c29d8-p119">Также следует удерживайте нажатой клавишу CTRL, в то же время, щелкните значок правой кнопкой мыши для клиентов Outlook (а также в области уведомлений Windows) и нажмите кнопку «Состояние подключения». Найдите SMTP-адрес клиента от определения типа "носителя\*", который представляет маркер носителя, используемый в OAuth.</span><span class="sxs-lookup"><span data-stu-id="c29d8-p119">You should also hold down the CTRL key at the same time you right click the icon for the Outlook client (also in the Windows Notifications tray) and click 'Connection Status'. Look for the client's SMTP address against an Authn type of 'Bearer\*', which represents the bearer token used in OAuth.</span></span>
  
## <a name="related-articles"></a><span data-ttu-id="c29d8-202">Статьи по теме</span><span class="sxs-lookup"><span data-stu-id="c29d8-202">Related articles</span></span>

<span data-ttu-id="c29d8-203">[Ссылку на обзор современного проверки подлинности](hybrid-modern-auth-overview.md) .</span><span class="sxs-lookup"><span data-stu-id="c29d8-203">[Link back to the Modern Authentication overview](hybrid-modern-auth-overview.md) .</span></span> 
  
<span data-ttu-id="c29d8-p120">Необходимо знать, как использовать современных проверки подлинности (ADAL) для вашей Скайп пользователей? У нас есть действия [здесь](https://technet.microsoft.com/en-us/library/mt710548.aspx).</span><span class="sxs-lookup"><span data-stu-id="c29d8-p120">Do you need to know how to use Modern Authentication (ADAL) for your Skype for Business clients? We've got steps [here](https://technet.microsoft.com/en-us/library/mt710548.aspx).</span></span>
  
<span data-ttu-id="c29d8-p121">Следует прочитать следующие действия, отображенные для Exchange Server, в локальной, выполнение не SFB? Здесь вы найдете эти действия.</span><span class="sxs-lookup"><span data-stu-id="c29d8-p121">Would you like to read these steps as they appear for Exchange Server, on-premises, running without SFB? Those steps are available here.</span></span>
  

