---
title: "Удостоверение для корпорации Contoso"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: 78a407e4-2d8b-4561-b308-b22c95f60eeb
description: "Сводка: Узнайте, как Contoso использует IDaaS и предоставляет географически распределенные и избыточных проверки подлинности для пользователей."
ms.openlocfilehash: a0de29ac7e73216e04fe02c680f2557e9f402883
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2017
---
# <a name="identity-for-the-contoso-corporation"></a><span data-ttu-id="b6801-103">Удостоверение для корпорации Contoso</span><span class="sxs-lookup"><span data-stu-id="b6801-103">Identity for the Contoso Corporation</span></span>

 <span data-ttu-id="b6801-104">**Сводка:** Понимаете, как используются преимущества IDaaS и предоставляет географически распределенные Contoso и избыточных проверки подлинности для пользователей.</span><span class="sxs-lookup"><span data-stu-id="b6801-104">**Summary:** Understand how Contoso takes advantage of IDaaS and provides geographically distributed and redundant authentication for its users.</span></span>
  
<span data-ttu-id="b6801-p101">Корпорация Майкрософт предоставляет удостоверение как службы (IDaaS) по его облака. Принятие включительно облачной инфраструктуры, Contoso IDaaS решения необходимо использовать свои поставщика удостоверений в локальной и включить федеративной проверки подлинности с помощью их существующих поставщиков удостоверений надежных, сторонних производителей.</span><span class="sxs-lookup"><span data-stu-id="b6801-p101">Microsoft provides an Identity as a Service (IDaaS) across its cloud offerings. To adopt a cloud-inclusive infrastructure, Contoso's IDaaS solution must leverage their on-premises identity provider and include federated authentication with their existing trusted, third-party identity providers.</span></span>
  
## <a name="contosos-windows-server-ad-forest"></a><span data-ttu-id="b6801-107">Леса Windows Server AD организации Contoso</span><span class="sxs-lookup"><span data-stu-id="b6801-107">Contoso's Windows Server AD forest</span></span>

<span data-ttu-id="b6801-p102">Contoso использует один лес Active Directory Windows Server (AD) для contoso.com с семь доменами, один для каждого регионе. Штаб-квартире, сервер-концентратор региональных офисах и филиалах содержат контроллеров домена для локальной проверки подлинности и авторизации.</span><span class="sxs-lookup"><span data-stu-id="b6801-p102">Contoso uses a single Windows Server Active Directory (AD) forest for contoso.com with seven domains, one for each region of the world. The headquarters, regional hub offices, and satellite offices contain domain controllers for local authentication and authorization.</span></span>
  
<span data-ttu-id="b6801-110">**На рисунке 1: Contoso леса и домены во всем мире**</span><span class="sxs-lookup"><span data-stu-id="b6801-110">**Figure 1: Contoso's forest and domains worldwide**</span></span>

![Лес Windows Server AD и соответствующие домены Contoso, настроенные для разных точек мира](images/Contoso_Poster/Contoso_WW_ID.png)
  
<span data-ttu-id="b6801-112">На рисунке 1 показан лес Contoso с региональными доменами для разных частей света, в которых находятся региональные офисы.</span><span class="sxs-lookup"><span data-stu-id="b6801-112">Figure 1 shows the Contoso forest with regional domains for the different parts of the world that contain regional hubs.</span></span>
  
<span data-ttu-id="b6801-113">Компания Contoso хочет использовать учетные записи и группы в лесу contoso.com для аутентификации и авторизации своих облачных приложений и рабочих нагрузок.</span><span class="sxs-lookup"><span data-stu-id="b6801-113">Contoso wants to use the accounts and groups in the contoso.com forest for authentication and authorization for its cloud-based apps and workloads.</span></span>
  
## <a name="contosos-federated-authentication-infrastructure"></a><span data-ttu-id="b6801-114">Инфраструктура Contoso федеративной проверки подлинности</span><span class="sxs-lookup"><span data-stu-id="b6801-114">Contoso's federated authentication infrastructure</span></span>

<span data-ttu-id="b6801-115">Позволяет Contoso:</span><span class="sxs-lookup"><span data-stu-id="b6801-115">Contoso allows:</span></span>
  
- <span data-ttu-id="b6801-116">клиентам использовать свои учетные записи Майкрософт, Facebook или Google Mail для входа на общедоступный веб-сайт;</span><span class="sxs-lookup"><span data-stu-id="b6801-116">Customers to use their Microsoft, Facebook, or Google Mail accounts to sign in to their public web site.</span></span>
    
- <span data-ttu-id="b6801-117">поставщикам и партнерам использовать свои учетные записи LinkedIn, Salesforce или Google Mail для входа в партнерскую экстрасеть.</span><span class="sxs-lookup"><span data-stu-id="b6801-117">Vendors and partners to use their LinkedIn, Salesforce, or Google Mail accounts to sign in to the partner extranet.</span></span>
    
<span data-ttu-id="b6801-118">**На рисунке 2: Contoso Поддержка федеративного проверки подлинности для клиентов и партнеров**</span><span class="sxs-lookup"><span data-stu-id="b6801-118">**Figure 2: Contoso's support for federated authentication for customers and partners**</span></span>

![Существующая инфраструктура Contoso, обеспечивающая поддержку федеративной аутентификации клиентов и партнеров](images/Contoso_Poster/Federated_ID.png)
  
<span data-ttu-id="b6801-p103">На рисунке 2 показана DMZ Contoso, которая содержит общедоступный веб-сайт, партнерскую экстрасеть и набор серверов AD FS. DMZ подключена к Интернету, в котором находятся клиенты, партнеры и Интернет-службы.</span><span class="sxs-lookup"><span data-stu-id="b6801-p103">Figure 2 shows the Contoso DMZ containing a public web site, a partner extranet, and a set of AD FS servers. The DMZ is connected to the Internet that contains customers and partners and Internet services.</span></span>
  
<span data-ttu-id="b6801-122">Серверы служб федерации Active Directory (AD FS) в DMZ выполняют аутентификацию клиентов на общедоступном веб-сайте и партнеров в партнерской экстрасети.</span><span class="sxs-lookup"><span data-stu-id="b6801-122">Active Directory Federation Services (AD FS) servers in the DMZ authenticate customer credentials for access to the public web site and partner credentials for access to the partner extranet.</span></span>
  
<span data-ttu-id="b6801-p104">Когда Contoso переходит его общедоступного веб-сайта Azure Web App и экстрасети Dynamics 365 партнера, они хотят продолжить использовать эти поставщики удостоверений сторонних производителей для своих клиентов и партнеров. Это будет выполняется путем настройки федерации между клиентами Contoso Azure AD и Поставщики удостоверений сторонних производителей.</span><span class="sxs-lookup"><span data-stu-id="b6801-p104">When Contoso transitions its public web site to an Azure Web App and partner extranet to Dynamics 365, they want to continue to use these third-party identity providers for their customers and partners. This will be accomplished by configuring federation between Contoso Azure AD tenants and these third-party identity providers.</span></span>
  
## <a name="directory-synchronization-for-contosos-windows-server-ad-forest"></a><span data-ttu-id="b6801-125">Синхронизация каталогов для леса Windows Server AD организации Contoso</span><span class="sxs-lookup"><span data-stu-id="b6801-125">Directory synchronization for Contoso's Windows Server AD forest</span></span>

<span data-ttu-id="b6801-p105">Contoso развернут средство Azure AD подключение кластера серверов в его Париж центра обработки данных. Подключение Azure AD синхронизирует изменения на contoso.com леса Windows Server AD с Azure AD клиента, общие для Office 365 организации Contoso, Командной, Dynamics 365 и Azure подписок. Дополнительные сведения о подписках лицензий, учетные записи пользователей и клиентов, посетите [подписок, лицензии и учетные записи для Contoso Corporation](subscriptions-licenses-and-user-accounts-for-the-contoso-corporation.md).</span><span class="sxs-lookup"><span data-stu-id="b6801-p105">Contoso has deployed the Azure AD Connect tool on a cluster of servers in its Paris datacenter. Azure AD Connect synchronizes changes to the contoso.com Windows Server AD forest with the Azure AD tenant shared by Contoso's Office 365, EMS, Dynamics 365, and Azure subscriptions. For more information about subscriptions, licenses, user accounts, and tenants, see [Subscriptions, licenses, and user accounts for the Contoso Corporation](subscriptions-licenses-and-user-accounts-for-the-contoso-corporation.md).</span></span>
  
<span data-ttu-id="b6801-129">**На рисунке 3: Инфраструктура синхронизации каталогов Contoso**</span><span class="sxs-lookup"><span data-stu-id="b6801-129">**Figure 3: Contoso's directory synchronization infrastructure**</span></span>

![Инфраструктура корпорации Contoso для синхронизации службы каталогов ](images/Contoso_Poster/DirSync.png)
  
<span data-ttu-id="b6801-131">На рисунке 3 показан кластер серверов со средством Azure AD Connect, которое синхронизирует лес Windows Server AD компании Contoso с клиентом Azure AD.</span><span class="sxs-lookup"><span data-stu-id="b6801-131">Figure 3 shows a cluster of servers running Azure AD Connect synchronizing the Contoso Windows Server AD forest with the Azure AD tenant.</span></span>
  
<span data-ttu-id="b6801-p106">Contoso настроил федеративной проверки подлинности, которая обеспечивает единый вход для сотрудников организации Contoso. Когда пользователь, который уже вошел в contoso.com леса Windows Server AD обращается к ресурса облаке Майкрософт SaaS или PaaS, будет не запрос пароль.</span><span class="sxs-lookup"><span data-stu-id="b6801-p106">Contoso has configured federated authentication, which provides single sign-on for Contoso's workers. When a user that has already signed in to the contoso.com Windows Server AD forest accesses a Microsoft SaaS or PaaS cloud resource, they will not be prompted for a password.</span></span>
  
## <a name="geographical-distribution-of-contoso-authentication-traffic"></a><span data-ttu-id="b6801-134">Географическое распределение трафика аутентификации Contoso</span><span class="sxs-lookup"><span data-stu-id="b6801-134">Geographical distribution of Contoso authentication traffic</span></span>

<span data-ttu-id="b6801-p107">Чтобы лучше поддерживать его мобильных устройств и удаленных сотрудников, Contoso развернут наборов серверов проверки подлинности в его региональных офисах. Эта инфраструктура распределяет нагрузку и предоставляет избыточности и более высокую производительность при проверке подлинности учетные данные пользователя для доступа к Microsoft облака, использующие общие клиента Azure AD.</span><span class="sxs-lookup"><span data-stu-id="b6801-p107">To better support its mobile and remote workforce, Contoso has deployed sets of authentication servers in its regional offices. This infrastructure distributes the load and provides redundancy and higher performance when authenticating user credentials for access to Microsoft cloud offerings that use the common Azure AD tenant.</span></span>
  
<span data-ttu-id="b6801-137">Чтобы распределить запросы аутентификации, компания Contoso настроила диспетчер трафика Azure с профилем, который использует эффективный метод маршрутизации и направляет запросы на ближайший набор серверов аутентификации. </span><span class="sxs-lookup"><span data-stu-id="b6801-137">To distribute the load of authentication requests, Contoso has configured Azure Traffic Manager with a profile that uses the performance routing method, which refers authenticating clients to the regionally closest set of authentication servers.</span></span> 
  
<span data-ttu-id="b6801-138">**На рисунке 4: Географического трафика проверки подлинности для филиалов**</span><span class="sxs-lookup"><span data-stu-id="b6801-138">**Figure 4: Geographical distribution of authentication traffic for regional offices**</span></span>

![Географическое распределение трафика аутентификации Contoso для региональных офисов](images/Contoso_Poster/Auth_GeoDist.png)
  
<span data-ttu-id="b6801-p108">На рисунке 4 показаны уровни клиентских компьютеров, диспетчер трафика Azure и серверы аутентификации в региональных офисах. Каждый региональные офис использует веб-прокси и серверы AD FS для аутентификации пользователей на контроллерах доменов Windows Server AD.</span><span class="sxs-lookup"><span data-stu-id="b6801-p108">Figure 4 shows the layers of client computers, Azure Traffic Manager, and authentication servers in regional offices. Each regional office uses web proxies and AD FS servers to authenticate user credentials with Windows Server AD domain controllers.</span></span>
  
<span data-ttu-id="b6801-142">Пример аутентификации:</span><span class="sxs-lookup"><span data-stu-id="b6801-142">Authentication process example:</span></span>
  
1. <span data-ttu-id="b6801-143">На клиентском компьютере инициирует взаимодействие с веб-страницы в клиенте Office 365 в Европе (например, sharepoint.contoso.com).</span><span class="sxs-lookup"><span data-stu-id="b6801-143">The client computer initiates communication with a web page in the Office 365 tenancy in Europe (such as sharepoint.contoso.com).</span></span>
    
2. <span data-ttu-id="b6801-p109">Office 365 отправляет запрос на подтверждение подлинности. Запрос содержит URL-адрес для аутентификации.</span><span class="sxs-lookup"><span data-stu-id="b6801-p109">Office 365 sends back a request to send proof of authentication. The request contains the URL to contact for authentication.</span></span>
    
3. <span data-ttu-id="b6801-146">Клиентский компьютер пытается разрешить DNS-имя в URL-адресе для IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="b6801-146">The client computer attempts to resolve the DNS name in the URL to an IP address.</span></span>
    
4. <span data-ttu-id="b6801-147">Диспетчер трафика Azure получает запрос DNS и отправляет клиентскому компьютеру IP-адрес прокси-сервера веб-приложений в региональном офисе, ближайшем к клиентскому компьютеру.</span><span class="sxs-lookup"><span data-stu-id="b6801-147">Azure Traffic Manager receives the DNS query and responds to the client computer with the IP address of a web application proxy server in the regional office that is closest to the client computer.</span></span>
    
5.  <span data-ttu-id="b6801-148">Клиентский компьютер отправляет запрос проверки подлинности сервер прокси-сервера веб-приложений, который отправляет запрос на сервер служб AD FS.</span><span class="sxs-lookup"><span data-stu-id="b6801-148">The client computer sends an authentication request to a web application proxy server, which forwards the request to an AD FS server.</span></span>
    
6. <span data-ttu-id="b6801-149">Сервер AD FS запрашивает учетные данные пользователя с клиентского компьютера.</span><span class="sxs-lookup"><span data-stu-id="b6801-149">The AD FS server requests the user credentials from the client computer.</span></span>
    
7. <span data-ttu-id="b6801-150">Клиентский компьютер отправляет учетные данные пользователя.</span><span class="sxs-lookup"><span data-stu-id="b6801-150">The client computer sends the user credentials without prompting the user.</span></span>
    
8. <span data-ttu-id="b6801-151">Сервер AD FS проверяет учетные данные с помощью контроллера домена Windows Server AD в региональном офисе и возвращает маркер безопасности на клиентский компьютер.</span><span class="sxs-lookup"><span data-stu-id="b6801-151">The AD FS server validates the credentials with a Windows Server AD domain controller in the regional office and returns a security token to the client computer.</span></span>
    
9. <span data-ttu-id="b6801-152">Клиентский компьютер отправляет маркер безопасности в Office 365.</span><span class="sxs-lookup"><span data-stu-id="b6801-152">The client computer sends the security token to Office 365.</span></span>
    
10. <span data-ttu-id="b6801-153">После успешной проверки Office 365 кэширует маркер безопасности и отправляет веб-страницу, запрошенную на шаге 1, на клиентский компьютер.</span><span class="sxs-lookup"><span data-stu-id="b6801-153">After successful validation, Office 365 caches the security token and sends the web page requested in step 1 to the client computer.</span></span>
    
## <a name="redundancy-for-the-headquarters-authentication-infrastructure-in-azure-iaas"></a><span data-ttu-id="b6801-154">Резервная инфраструктура аутентификации в главном офисе в Azure IaaS</span><span class="sxs-lookup"><span data-stu-id="b6801-154">Redundancy for the headquarters authentication infrastructure in Azure IaaS</span></span>

<span data-ttu-id="b6801-155">Для обеспечения избыточности для удаленных и мобильных работников штаб-квартире Париж, содержащий 15 000 сотрудников, Contoso развернут второму набору прокси-серверы приложений и серверы AD FS в Azure IaaS.</span><span class="sxs-lookup"><span data-stu-id="b6801-155">To provide redundancy for the remote and mobile workers of the Paris headquarters that contains 15,000 workers, Contoso has deployed a second set of application proxies and AD FS servers in Azure IaaS.</span></span>
  
<span data-ttu-id="b6801-156">**На рисунке 5: Инфраструктуры избыточные проверки подлинности в Azure IaaS**</span><span class="sxs-lookup"><span data-stu-id="b6801-156">**Figure 5: Redundant authentication infrastructure in Azure IaaS**</span></span>

![Избыточная инфраструктура аутентификации в Azure IaaS для главного офиса в Париже](images/Contoso_Poster/Paris_Auth_Redun.png)
  
<span data-ttu-id="b6801-158">На рисунке 5 показаны веб-прокси и серверы AD FS в DMZ и дополнительные наборы этих компонентов в виртуальной сети Azure.</span><span class="sxs-lookup"><span data-stu-id="b6801-158">Figure 5 shows web proxies and AD FS servers in the DMZ and an additional set of each in a cross-premises Azure virtual network.</span></span>
  
<span data-ttu-id="b6801-p110">Когда основные серверы аутентификации в DMZ главного офиса становятся недоступными, ИТ-специалисты переключают систему на резервный набор, развернутый в Azure IaaS. Последующие запросы аутентификации от компьютеров в парижском офисе используют набор в Azure IaaS, пока проблема не будет устранена.</span><span class="sxs-lookup"><span data-stu-id="b6801-p110">When the primary authentication servers in the headquarters DMZ become unavailable, IT staff switch over to the redundant set deployed in Azure IaaS. Subsequent authentication requests from Paris office computers use the set in Azure IaaS until the availability problem is corrected.</span></span>
  
<span data-ttu-id="b6801-161">Для переключения в двух направлениях компания Contoso обновляет профиль диспетчера трафика Azure для региона "Париж", чтобы использовать другой набор IP-адресов для прокси-серверов веб-приложений:</span><span class="sxs-lookup"><span data-stu-id="b6801-161">To switch over and switch back, Contoso updates the Azure Traffic Manager profile for the Paris region to use a different set of IP addresses for the web application proxies:</span></span>
  
- <span data-ttu-id="b6801-162">Когда серверы проверки подлинности DMZ доступны, используйте IP-адресов серверов в DMZ.</span><span class="sxs-lookup"><span data-stu-id="b6801-162">When the DMZ authentication servers are available, use the IP addresses of the servers in the DMZ.</span></span>
    
- <span data-ttu-id="b6801-163">когда серверы аутентификации DMZ недоступны, используются IP-адреса серверов в Azure IaaS.</span><span class="sxs-lookup"><span data-stu-id="b6801-163">When the DMZ authentication servers are not available, use the IP addresses of the servers in Azure IaaS.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="b6801-164">See Also</span><span class="sxs-lookup"><span data-stu-id="b6801-164">See Also</span></span>

[<span data-ttu-id="b6801-165">Contoso в Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="b6801-165">Contoso in the Microsoft Cloud</span></span>](contoso-in-the-microsoft-cloud.md)
  
[<span data-ttu-id="b6801-166">Ресурсы для администраторов, посвященные архитектуре Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="b6801-166">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="b6801-167">Microsoft Облачное удостоверение для архитекторов предприятия</span><span class="sxs-lookup"><span data-stu-id="b6801-167">Microsoft Cloud Identity for Enterprise Architects</span></span>](http://aka.ms/cloudarchidentity)
  
[<span data-ttu-id="b6801-168">Удостоверение и защита устройств для Office 365</span><span class="sxs-lookup"><span data-stu-id="b6801-168">Identity and Device Protection for Office 365</span></span>](http://aka.ms/o365protect_device)
  
[<span data-ttu-id="b6801-169">Стратегия Enterprise Cloud корпорации Майкрософт: ресурсы для лиц, принимающих решения в области ИТ</span><span class="sxs-lookup"><span data-stu-id="b6801-169">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



