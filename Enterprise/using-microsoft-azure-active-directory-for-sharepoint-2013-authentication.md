---
title: "Использование службы Microsoft Azure Active Directory для проверки подлинности в SharePoint 2013"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Top
ms.custom:
- DecEntMigration
- Ent_Solutions
ms.assetid: bef810a4-53f6-4962-878e-e20b5019baeb
description: "Сводка. Узнайте, как использовать службу контроля доступа Azure для проверки подлинности пользователей SharePoint Server 2013 в Azure Active Directory."
ms.openlocfilehash: 85db8376aeb06ef6f291b563410c991ea24351d5
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2017
---
# <a name="using-microsoft-azure-active-directory-for-sharepoint-2013-authentication"></a><span data-ttu-id="a6bde-103">Использование службы Microsoft Azure Active Directory для проверки подлинности в SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="a6bde-103">Using Microsoft Azure Active Directory for SharePoint 2013 authentication</span></span>

 <span data-ttu-id="a6bde-104">**Сводка.** Узнайте, как использовать службу контроля доступа Azure для проверки подлинности пользователей SharePoint Server 2013 в Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="a6bde-104">**Summary:** Learn how to use the Azure Access Control Service to authenticate your SharePoint Server 2013 users with Azure Active Directory.</span></span>
  
<span data-ttu-id="a6bde-p101">Управлять пользователями может быть проще, если они будут проходить проверку подлинности у разных поставщиков удостоверений. Подумайте, насколько удобно может быть использовать надежного поставщика удостоверений, которым управляет кто-то другой. Например, вы можете использовать один тип проверки подлинности для пользователей, которые получают доступ к SharePoint Server 2013 в облаке, а другой  для пользователей SharePoint 2013 в локальной среде. Служба контроля доступа Azure делает возможным этот выбор.</span><span class="sxs-lookup"><span data-stu-id="a6bde-p101">It can be easier to manage your users by authenticating them with different identity providers. Consider how convenient it can be to use an identity provider that you trust, but someone else manages. For example, you could have one type of authentication for users who access SharePoint Server 2013 in the cloud and another for SharePoint 2013 users in your on-premises environment. The Azure Access Control Service makes these choices possible.</span></span> 
  
<span data-ttu-id="a6bde-p102">В этой статье описано, как можно использовать службу контроля доступа Azure для проверки подлинности пользователей SharePoint 2013 в службе Azure AD, а не в локальной службе Active Directory. В этой конфигурации Azure AD становится доверенным поставщиком удостоверений для SharePoint 2013. При этом добавляется метод аутентификации пользователей, отличный от проверки подлинности Active Directory, которую использует установленный экземпляр SharePoint 2013. Эта статья будет вам полезна, если вы знакомы с WS-Federation. Дополнительные сведения см. в статье [Общие сведения о WS-Federation](https://go.microsoft.com/fwlink/p/?linkid=188052).</span><span class="sxs-lookup"><span data-stu-id="a6bde-p102">This article explains how you can use the Azure Access Control Service to authenticate your SharePoint 2013 users with Azure AD, instead of your on-premises Active Directory. In this configuration, Azure AD becomes a trusted identity provider for SharePoint 2013. This configuration adds a user authentication method that is separate from Active Directory authentication used by the SharePoint 2013 installation itself. To benefit from this article, you should be familiar with WS-Federation. For more information, see [Understanding WS-Federation](https://go.microsoft.com/fwlink/p/?linkid=188052).</span></span>
  
<span data-ttu-id="a6bde-114">На следующем рисунке показано, как работает проверка подлинности для пользователей SharePoint 2013 в этой конфигурации.</span><span class="sxs-lookup"><span data-stu-id="a6bde-114">The following figure shows how authentication works for SharePoint 2013 users in this configuration.</span></span>
  
![Пользователи, прошедшие проверку подлинности в Azure Active Directory](images/SP_AzureAD.png)
  
<span data-ttu-id="a6bde-116">Пример, используемый в этой статье, предоставил Кирк Эванс (Kirk Evans), архитектор Майкрософт из центра подготовки по Azure.</span><span class="sxs-lookup"><span data-stu-id="a6bde-116">The example used in this article is provided by Kirk Evans, Microsoft Architect for the Azure Center of Excellence.</span></span> 
  
<span data-ttu-id="a6bde-117">Сведения о специальных возможностях SharePoint 2013 см. в статье [Специальные возможности в SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=393123).</span><span class="sxs-lookup"><span data-stu-id="a6bde-117">For information about SharePoint 2013 accessibility, see [Accessibility for SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=393123).</span></span>
  
## <a name="configuration-overview"></a><span data-ttu-id="a6bde-118">Общие сведения о конфигурации</span><span class="sxs-lookup"><span data-stu-id="a6bde-118">Configuration overview</span></span>

<span data-ttu-id="a6bde-119">Выполните приведенные ниже основные действия, чтобы настроить среду для использования Azure AD в качестве поставщика удостоверений SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="a6bde-119">Follow these general steps to set up your environment to use Azure AD as a SharePoint 2013 identity provider.</span></span>
  
1. <span data-ttu-id="a6bde-120">Создайте клиент и пространство имен Azure AD.</span><span class="sxs-lookup"><span data-stu-id="a6bde-120">Create a new Azure AD tenant and namespace.</span></span>
    
2. <span data-ttu-id="a6bde-121">Добавьте поставщика удостоверений WS-Federation.</span><span class="sxs-lookup"><span data-stu-id="a6bde-121">Add a WS-Federation identity provider.</span></span>
    
3. <span data-ttu-id="a6bde-122">Добавьте SharePoint в качестве приложения проверяющей стороны.</span><span class="sxs-lookup"><span data-stu-id="a6bde-122">Add SharePoint as a relying party application.</span></span>
    
4. <span data-ttu-id="a6bde-123">Создайте самозаверяющий SSL-сертификат.</span><span class="sxs-lookup"><span data-stu-id="a6bde-123">Create a self-signed certificate to use for SSL.</span></span>
    
5. <span data-ttu-id="a6bde-124">Создайте группу правил для проверки подлинности на основе утверждений.</span><span class="sxs-lookup"><span data-stu-id="a6bde-124">Create a rule group for claims-based authentication.</span></span>
    
6. <span data-ttu-id="a6bde-125">Настройте сертификат X.509.</span><span class="sxs-lookup"><span data-stu-id="a6bde-125">Configure the X.509 certificate.</span></span>
    
7. <span data-ttu-id="a6bde-126">Создайте сопоставление утверждений.</span><span class="sxs-lookup"><span data-stu-id="a6bde-126">Create a claim mapping.</span></span>
    
8. <span data-ttu-id="a6bde-127">Настройте SharePoint для нового поставщика удостоверений.</span><span class="sxs-lookup"><span data-stu-id="a6bde-127">Configure SharePoint for the new identity provider.</span></span>
    
9. <span data-ttu-id="a6bde-128">Задайте разрешения.</span><span class="sxs-lookup"><span data-stu-id="a6bde-128">Set the permissions.</span></span>
    
10. <span data-ttu-id="a6bde-129">Проверьте нового поставщика.</span><span class="sxs-lookup"><span data-stu-id="a6bde-129">Verify the new provider.</span></span>
    
## <a name="create-azure-ad-tenant-and-namespace"></a><span data-ttu-id="a6bde-130">Создание клиента и пространства имен Azure AD</span><span class="sxs-lookup"><span data-stu-id="a6bde-130">Create Azure AD tenant and namespace</span></span>

<span data-ttu-id="a6bde-p103">Выполните указанные ниже действия, чтобы создать клиент Azure AD и связанное с ним пространство имен. В нашем примере используется пространство имен blueskyabove</span><span class="sxs-lookup"><span data-stu-id="a6bde-p103">Use the following steps to create a new Azure AD tenant and an associated namespace. In this example, we use the namespace "blueskyabove."</span></span> 
  
1. <span data-ttu-id="a6bde-133">На портале управления Azure выберите **Active Directory** и создайте клиент Azure AD.</span><span class="sxs-lookup"><span data-stu-id="a6bde-133">In the Azure Management Portal, click **Active Directory**, and then create a new Azure AD tenant.</span></span>
    
2. <span data-ttu-id="a6bde-134">Нажмите **Пространства имен Access Control** и создайте новое пространство имен.</span><span class="sxs-lookup"><span data-stu-id="a6bde-134">Click **Access Control Namespaces**, and create a new namespace.</span></span> 
    
3. <span data-ttu-id="a6bde-p104">Нажмите кнопку **Управление** в нижней панели. Должен открыться следующий адрес: https://blueskyabove.accesscontrol.windows.net/v2/mgmt/web.</span><span class="sxs-lookup"><span data-stu-id="a6bde-p104">Click **Manage** on the bottom bar. This should open this location, https://blueskyabove.accesscontrol.windows.net/v2/mgmt/web.</span></span>
    
4. <span data-ttu-id="a6bde-p105">Откройте командную консоль Windows PowerShell. Используйте модуль Microsoft Online Services для Windows PowerShell, который необходим, чтобы установить Azure для командлетов Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a6bde-p105">Open Windows PowerShell. Use the Microsoft Online Services Module for Windows PowerShell, which is a prerequisite for installing the Azure for Windows PowerShell cmdlets.</span></span>
    
5. <span data-ttu-id="a6bde-139">В командной строке Windows PowerShell введите команду  `Connect-Msolservice` и свои учетные данные.</span><span class="sxs-lookup"><span data-stu-id="a6bde-139">From the Windows PowerShell command prompt, type the command:  `Connect-Msolservice`, and then type your credentials.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="a6bde-140">Дополнительные сведения об использовании Azure для командлетов Windows PowerShell см. в статье [Управление службой Azure AD с помощью Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=393124).</span><span class="sxs-lookup"><span data-stu-id="a6bde-140">For additional information about how to use Azure for Windows PowerShell cmdlets, see [Manage Azure AD using Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=393124).</span></span> 
  
6. <span data-ttu-id="a6bde-141">В командной строке Windows PowerShell введите следующие команды:</span><span class="sxs-lookup"><span data-stu-id="a6bde-141">From a Windows PowerShell command prompt, type the following commands:</span></span>
    
  ```
  Import-Module MSOnlineExtended -Force
  ```

  ```
  $replyUrl = New-MsolServicePrincipalAddresses -Address "https://blueskyabove.accesscontrol.windows.net/"
  ```

  ```
  New-MsolServicePrincipal -ServicePrincipalNames @("https://blueskyabove.accesscontrol.windows.net/") -DisplayName "BlueSkyAbove ACS Namespace" -Addresses $replyUrl
  ```

    <span data-ttu-id="a6bde-142">На следующем рисунке показан результат вывода команды.</span><span class="sxs-lookup"><span data-stu-id="a6bde-142">The following figure illustrates the output result.</span></span>
    
     ![Создание имен субъектов-служб](images/ServicePrincipalNames.jpg)
  
## <a name="add-a-ws-federation-identity-provider-to-the-namespace"></a><span data-ttu-id="a6bde-144">Добавление поставщика удостоверений WS-Federation к пространству имен</span><span class="sxs-lookup"><span data-stu-id="a6bde-144">Add a WS-Federation identity provider to the namespace</span></span>

<span data-ttu-id="a6bde-145">Выполните указанные ниже действия, чтобы добавить поставщика удостоверений WS-Federation к пространству имен blueskyabove.</span><span class="sxs-lookup"><span data-stu-id="a6bde-145">Use the following steps to add a new WS-Federation identity provider to the blueskyabove namespace.</span></span>
  
1. <span data-ttu-id="a6bde-146">На портале управления Azure перейдите в раздел **Active Directory** > **Пространства имен Access Control Namespaces**, нажмите **Создать новый экземпляр**, а затем нажмите кнопку **Управление**.</span><span class="sxs-lookup"><span data-stu-id="a6bde-146">From the Azure management portal, go to **Active Directory** > **Access Control Namespaces**, click **Create a new instance**, and then click **Manage**.</span></span>
    
2. <span data-ttu-id="a6bde-147">На портале Azure Access Control выберите команды **Поставщики удостоверений** > **Добавить**, как показано на следующем рисунке.</span><span class="sxs-lookup"><span data-stu-id="a6bde-147">From the Azure Access Control portal, click **Identity Providers** > **Add**, as illustrated in the following figure.</span></span>
    
     ![Диалоговое окно "Поставщики удостоверений" в Azure](images/Identity.jpg)
  
3. <span data-ttu-id="a6bde-149">Выберите пункт **Поставщик удостоверений WS-Federation**, как показано на следующем рисунке, а затем нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="a6bde-149">Click **WS-Federation identity provider**, as illustrated in the following figure, and then click **Next**.</span></span>
    
     ![Параметры команды "Добавить поставщика удостоверений" в Azure](images/AddIdentity.jpg)
  
4. <span data-ttu-id="a6bde-p106">Введите отображаемое имя и текст ссылки для входа, а затем нажмите кнопку **Сохранить**. В качестве URL-адреса метаданных WS-Federation введите https://accounts.accesscontrol.windows.net/blueskyabove.onmicrosoft.com/FederationMetadata/2007-06/FederationMetadata.xml. Этот параметр показан на следующем рисунке.</span><span class="sxs-lookup"><span data-stu-id="a6bde-p106">Fill out the display name and logon link text, and then click **Save**. For the WS-Federation metadata URL, type https://accounts.accesscontrol.windows.net/blueskyabove.onmicrosoft.com/FederationMetadata/2007-06/FederationMetadata.xml. The following figure illustrates the setting.</span></span>
    
     ![Поставщик удостоверений федерации](images/FederationIdentity.jpg)
  
## <a name="add-sharepoint-as-a-relying-party-application"></a><span data-ttu-id="a6bde-155">Добавление SharePoint в качестве приложения проверяющей стороны</span><span class="sxs-lookup"><span data-stu-id="a6bde-155">Add SharePoint as a relying party application</span></span>

<span data-ttu-id="a6bde-156">Выполните указанные ниже действия, чтобы добавить SharePoint в качестве приложения проверяющей стороны.</span><span class="sxs-lookup"><span data-stu-id="a6bde-156">Use the following steps to add SharePoint as a relying party application.</span></span>
  
<span data-ttu-id="a6bde-157">Дополнительные сведения о параметрах приложений проверяющей стороны см. в статье [Приложения проверяющей стороны](https://go.microsoft.com/fwlink/p/?LinkId=393125).</span><span class="sxs-lookup"><span data-stu-id="a6bde-157">For additional information about relying party application settings, see [Relying Party Applications](https://go.microsoft.com/fwlink/p/?LinkId=393125).</span></span>
  
1. <span data-ttu-id="a6bde-158">На портале Azure Access Control выберите пункт **Приложения проверяющей стороны** и нажмите кнопку **Добавить**, как показано на следующем рисунке.</span><span class="sxs-lookup"><span data-stu-id="a6bde-158">From the Azure Access Control portal, click **Relying party applications**, and then click **Add**, as illustrated in the following figure.</span></span>
    
     ![Настройки приложения проверяющей стороны](images/RelyingPartyApplications.jpg)
  
## <a name="create-a-self-signed-certificate-to-use-for-ssl"></a><span data-ttu-id="a6bde-160">Создание самозаверяющего сертификата для SSL</span><span class="sxs-lookup"><span data-stu-id="a6bde-160">Create a self-signed certificate to use for SSL</span></span>

<span data-ttu-id="a6bde-161">Выполните указанные ниже действия, чтобы создать самозаверяющий сертификат для безопасного подключения по SSL.</span><span class="sxs-lookup"><span data-stu-id="a6bde-161">Use the following steps to create a new, self-signed certificate to use for secure communications over SSL.</span></span>
  
1. <span data-ttu-id="a6bde-162">Расширьте веб-приложение, чтобы оно использовало тот же URL-адрес, что и PublishingSite, но используйте SSL с портом 443, как показано на следующем рисунке.</span><span class="sxs-lookup"><span data-stu-id="a6bde-162">Extend the web application to use the same URL as PublishingSite, but use SSL with port 443, as illustrated in the following figure.</span></span>
    
     ![Параметры для расширения приложения](images/ExtendWebApp.jpg)
  
2. <span data-ttu-id="a6bde-164">В Диспетчер IIS дважды щелкните **Сертификаты сервера**.</span><span class="sxs-lookup"><span data-stu-id="a6bde-164">In IIS Manager, double-click **Server Certificates**.</span></span>
    
3. <span data-ttu-id="a6bde-p107">В области **Действия** нажмите **Создать самозаверяющий сертификат**. Введите понятное имя сертификата в поле **Понятное имя сертификата** и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="a6bde-p107">In the **Actions** pane, click **Create Self-Signed Certificate**. Type a friendly name for the certificate in the **Specify a friendly name for the certificate** box, and then click **OK**.</span></span>
    
4. <span data-ttu-id="a6bde-167">В диалоговом окне **Изменение привязки сайта** убедитесь, что имя узла совпадает с понятным именем, как показано на следующих рисунках.</span><span class="sxs-lookup"><span data-stu-id="a6bde-167">From the **Edit Site Binding** dialog box, ensure the host name is the same as the friendly name, as illustrated in the following figures.</span></span>
    
     ![Мастер самозаверяющих сертификатов](images/SelfSignedCert.jpg)
  
     ![Имя сервера в диалоговом окне "Изменить привязки"](images/SelfSignedCert1.jpg)
  
5. <span data-ttu-id="a6bde-170">На портале управления Azure щелкните виртуальную машину, которую нужно настроить, и выберите пункт **Конечные точки**.</span><span class="sxs-lookup"><span data-stu-id="a6bde-170">From the Azure management portal, click the virtual machine that you want to configure, and then click **Endpoints**.</span></span>
    
6. <span data-ttu-id="a6bde-171">Нажмите кнопку **Добавить**, а затем  кнопку **-->** ("Далее").</span><span class="sxs-lookup"><span data-stu-id="a6bde-171">Click **Add**, and then click **-->** (for Next).</span></span>
    
7. <span data-ttu-id="a6bde-172">В поле **Имя** введите имя конечной точки.</span><span class="sxs-lookup"><span data-stu-id="a6bde-172">In **Name**, type a name for the endpoint.</span></span>
    
8. <span data-ttu-id="a6bde-p108">В полях **Общий порт** и **Частный порт** введите нужные номера портов и щелкните флажок, чтобы завершить настройку. Эти номера могут отличаться. В этой статье используется порт 443, как показано на следующем рисунке.</span><span class="sxs-lookup"><span data-stu-id="a6bde-p108">In **Public Port** and **Private Port**, type the port numbers that you want to use, and then click the check mark to complete. These numbers can be different. For the purposes of this article, we are using 443, as illustrated in the following figure.</span></span>
    
     ![Настройки конечной точки в Azure](images/AddEndpoint.jpg)
  
    > [!NOTE]
    > <span data-ttu-id="a6bde-177">Дополнительные сведения о добавлении конечной точки к виртуальной машине в Azure см. в статье [Настройка конечных точек виртуальной машины](https://go.microsoft.com/fwlink/p/?LinkId=393126).</span><span class="sxs-lookup"><span data-stu-id="a6bde-177">For additional information about how to add an endpoint to a virtual machine in Azure, see [How to Set Up Endpoints to a Virtual Machine](https://go.microsoft.com/fwlink/p/?LinkId=393126).</span></span> 
  
9. <span data-ttu-id="a6bde-178">На портале служб Access Control добавьте проверяющую сторону, как показано на следующем рисунке.</span><span class="sxs-lookup"><span data-stu-id="a6bde-178">From the Access Control services portal, add a relying party, as illustrated in the following figure.</span></span>
    
     ![Параметры добавления проверяющей стороны в приложении](images/AddRelyingParty.jpg)
  
## <a name="create-a-rule-group-for-claims-based-authentication"></a><span data-ttu-id="a6bde-180">Создание группы правил для проверки подлинности на основе утверждений</span><span class="sxs-lookup"><span data-stu-id="a6bde-180">Create a rule group for claims-based authentication</span></span>

<span data-ttu-id="a6bde-181">Выполните указанные ниже действия, чтобы создать группу правил для проверки подлинности на основе утверждений.</span><span class="sxs-lookup"><span data-stu-id="a6bde-181">Use the following steps to create a new rule group to control claims-based authentication.</span></span>
  
1. <span data-ttu-id="a6bde-182">В левой области выберите **Группы правил** и нажмите кнопку **Добавить**.</span><span class="sxs-lookup"><span data-stu-id="a6bde-182">In the left pane, click **Rule groups**, and then click **Add**.</span></span>
    
2. <span data-ttu-id="a6bde-p109">Введите имя группы правил, нажмите кнопку **Сохранить**, а затем  кнопку **Создать**. В этой статье используется **Default Rule Group for. spvms.cloudapp.net**, как показано на следующем рисунке.</span><span class="sxs-lookup"><span data-stu-id="a6bde-p109">Type a name for the rule group, click **Save**, and then click **Generate**. For the purposes of this article, we are using **Default Rule Group for. spvms.cloudapp.net**, as illustrated in the following figure.</span></span>
    
     ![Параметры группы правил в Azure](images/RuleGroup.jpg)
  
     ![Правила после выбора команды "Создать"](images/GenerateRules.jpg)
  
    > [!NOTE]
    > <span data-ttu-id="a6bde-187">Дополнительные сведения о создании групп правил см. в статье [Группы правил и правила](https://go.microsoft.com/fwlink/p/?LinkId=393128).</span><span class="sxs-lookup"><span data-stu-id="a6bde-187">For additional information about how to create rule groups, see [Rule Groups and Rules](https://go.microsoft.com/fwlink/p/?LinkId=393128).</span></span> 
  
3. <span data-ttu-id="a6bde-p110">Щелкните нужную группу правил, а затем выберите нужное правило утверждений. В этой статье мы добавим в группу правило утверждений, которое передает параметр **name** как **upn**, как показано на следующем рисунке.</span><span class="sxs-lookup"><span data-stu-id="a6bde-p110">Click the rule group that you want to change, and then click the claim rule that you want to change. For the purposes of this article, we add a claim rule to the group to pass **name** as **upn**, as illustrated by the following figure.</span></span>
    
     ![Правила утверждений в службе Azure Access Control](images/ClaimRules.jpg)
  
4. <span data-ttu-id="a6bde-191">Удалите существующее правило утверждений под названием **upn** и оставьте правило **Name Claim to UPN**, как показано на следующем рисунке.</span><span class="sxs-lookup"><span data-stu-id="a6bde-191">Delete the existing claim rule named **upn**, and leave the **Name Claim to UPN** rule, as illustrated by the following figure.</span></span>
    
     ![Параметры правил утверждений в службе Azure Access Control](images/ClaimToUPN.jpg)
  
## <a name="configure-the-x509-certificate"></a><span data-ttu-id="a6bde-193">Настройка сертификата X.509</span><span class="sxs-lookup"><span data-stu-id="a6bde-193">Configure the X.509 certificate</span></span>

<span data-ttu-id="a6bde-194">Выполните указанные ниже действия, чтобы настроить сертификат X.509 для использования подписей маркеров.</span><span class="sxs-lookup"><span data-stu-id="a6bde-194">Use the following steps to configure the X.509 certificate to use for token signing.</span></span>
  
1. <span data-ttu-id="a6bde-195">В области службы контроля доступа в разделе **Разработка** выберите пункт **Интеграция приложений**.</span><span class="sxs-lookup"><span data-stu-id="a6bde-195">In the Access Control Service pane, under **Development**, click **Application integration**.</span></span>
    
2. <span data-ttu-id="a6bde-196">В разделе **Ссылка на конечную точку** найдите файл **Federation.xml**, связанный с клиентом Azure, и скопируйте расположение из адресной строки браузера.</span><span class="sxs-lookup"><span data-stu-id="a6bde-196">In **Endpoint Reference**, locate the **Federation.xml** that is associated with your Azure tenant, and then copy the location in the address bar of a browser.</span></span>
    
3. <span data-ttu-id="a6bde-197">В файле **Federation.xml** найдите раздел **RoleDescriptor** и скопируйте сведения из элемента _<X509Certificate>_, как показано на следующем рисунке.</span><span class="sxs-lookup"><span data-stu-id="a6bde-197">In the **Federation.xml** file, locate the **RoleDescriptor** section, and copy the information from the _<X509Certificate>_ element, as illustrated in the following figure.</span></span>
    
     ![Элемент сертификата X509 в файле Federation.xml](images/X509Cert.jpg)
  
4. <span data-ttu-id="a6bde-199">В корне диска C:\\ создайте папку под названием **Certificates**.</span><span class="sxs-lookup"><span data-stu-id="a6bde-199">From the root of drive C:\\, create a folder named **Certificates**.</span></span>
    
5. <span data-ttu-id="a6bde-200">Сохраните файл сведений X509Certificate в папке C:\\Certificates под именем **AcsTokenSigning.cer**.</span><span class="sxs-lookup"><span data-stu-id="a6bde-200">Save the X509Certificate information to the folder C:\\Certificates with the file name, **AcsTokenSigning.cer**.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="a6bde-201">Имя файла должно иметь расширение CER.</span><span class="sxs-lookup"><span data-stu-id="a6bde-201">The file name must be saved with a .cer extension.</span></span> 
  
     ![Сохранение элемента X509Certificate в файле](images/X509Cert_Save.jpg)
  
## <a name="create-a-claim-mapping-by-using-windows-powershell"></a><span data-ttu-id="a6bde-203">Создание сопоставления утверждений с помощью Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a6bde-203">Create a claim mapping by using Windows PowerShell</span></span>

<span data-ttu-id="a6bde-204">Выполните указанные ниже действия, чтобы создать сопоставление утверждений с помощью Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a6bde-204">Use the following steps to create a claim mapping by using Windows PowerShell.</span></span>
  
<span data-ttu-id="a6bde-205">Убедитесь, что вы являетесь участником следующих групп:</span><span class="sxs-lookup"><span data-stu-id="a6bde-205">Verify that you have the following memberships:</span></span>
  
1. <span data-ttu-id="a6bde-206">Предопределенная роль сервера **securityadmin** для экземпляра SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a6bde-206">**securityadmin** fixed server role on the SQL Server instance.</span></span>
    
2. <span data-ttu-id="a6bde-207">Предопределенная роль сервера **db_owner** на всех обновляемых базах данных.</span><span class="sxs-lookup"><span data-stu-id="a6bde-207">**db_owner** fixed database role on all databases that will be updated.</span></span>
    
3. <span data-ttu-id="a6bde-208">Группа администраторов сервера, на котором выполняются командлеты Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a6bde-208">Administrators group on the server on which you are running the Windows PowerShell cmdlets.</span></span>
    
<span data-ttu-id="a6bde-209">Администратор может использовать командлет **Add-SPShellAdmin** для предоставления разрешений на использование командлетов SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="a6bde-209">An administrator can use the **Add-SPShellAdmin** cmdlet to grant permissions to use SharePoint 2013 cmdlets.</span></span>
  
> [!NOTE]
> <span data-ttu-id="a6bde-p111">Если у вас нет разрешений, запросите их у администратора установки или администратора SQL Server. Дополнительные сведения о разрешениях Windows PowerShell см. в описании командлета [Add-SPShellAdmin](http://technet.microsoft.com/library/2ddfad84-7ca8-409e-878b-d09cb35ed4aa.aspx).</span><span class="sxs-lookup"><span data-stu-id="a6bde-p111">If you do not have permissions, contact your Setup administrator or SQL Server administrator to request permissions. For additional information about Windows PowerShell permissions, see [Add-SPShellAdmin](http://technet.microsoft.com/library/2ddfad84-7ca8-409e-878b-d09cb35ed4aa.aspx).</span></span> 
  
1. <span data-ttu-id="a6bde-212">В меню **Пуск** выберите пункт **Все программы**.</span><span class="sxs-lookup"><span data-stu-id="a6bde-212">From the **Start** menu, click **All Programs**.</span></span>
    
2. <span data-ttu-id="a6bde-213">Выберите **Продукты Microsoft SharePoint 2013**.</span><span class="sxs-lookup"><span data-stu-id="a6bde-213">Click **Microsoft SharePoint 2013 Products**.</span></span>
    
3. <span data-ttu-id="a6bde-214">Щелкните **Командная консоль Командная консоль SharePoint 2013**.</span><span class="sxs-lookup"><span data-stu-id="a6bde-214">Click **SharePoint 2013 Management Shell**.</span></span>
    
4. <span data-ttu-id="a6bde-215">В командной строке Windows PowerShell введите следующие команды, чтобы создать сопоставление утверждений:</span><span class="sxs-lookup"><span data-stu-id="a6bde-215">At the Windows PowerShell command prompt, type the following commands to create a claim mapping:</span></span>
    
  ```
  $cert = New-Object System.Security.Cryptography.X509Certificates.X509Certificate2("c:\\certificates\\AcsTokenSigning.cer")
  ```

  ```
  New-SPTrustedRootAuthority -Name "ACS BlueSkyAbove Token Signing" -Certificate $cert
  ```

  ```
  $map = New-SPClaimTypeMapping -IncomingClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/upn" -IncomingClaimTypeDisplayName "UPN" -SameAsIncoming
  ```

  ```
  $map2 = New-SPClaimTypeMapping -IncomingClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/givenname" -IncomingClaimTypeDisplayName "GivenName" -SameAsIncoming
  ```

  ```
  $map3 = New-SPClaimTypeMapping -IncomingClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/surname" -IncomingClaimTypeDisplayName "SurName" -SameAsIncoming
  ```

  ```
  $realm = "urn:sharepoint:spvms"
  ```

  ```
  $ap = New-SPTrustedIdentityTokenIssuer -Name "ACS Provider" -Description "SharePoint secured by SAML in ACS" -realm $realm -ImportTrustCertificate $cert -ClaimsMappings $map,$map2,$map3 -SignInUrl "https://blueskyabove.accesscontrol.windows.net/v2/wsfederation" -IdentifierClaim "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/upn"
  ```

## <a name="configure-sharepoint-for-the-new-identity-provider"></a><span data-ttu-id="a6bde-216">Настройка SharePoint для нового поставщика удостоверений</span><span class="sxs-lookup"><span data-stu-id="a6bde-216">Configure SharePoint for the new identity provider</span></span>

<span data-ttu-id="a6bde-217">Выполните указанные ниже действия, чтобы настроить свою установку SharePoint для нового поставщика удостоверений Azure AD.</span><span class="sxs-lookup"><span data-stu-id="a6bde-217">Use the following steps to configure your SharePoint installation to the new identity provider for Azure AD.</span></span>
  
1. <span data-ttu-id="a6bde-218">Проверьте, является ли учетная запись пользователя, с помощью которой выполняется данная процедура, участником группы администраторов фермы SharePoint.</span><span class="sxs-lookup"><span data-stu-id="a6bde-218">Verify that the user account that is performing this procedure is a member of the Farm Administrators SharePoint group.</span></span>
    
2. <span data-ttu-id="a6bde-219">На домашней странице центра Центр администрирования нажмите **Управление приложениями**.</span><span class="sxs-lookup"><span data-stu-id="a6bde-219">In Central Administration, on the home page, click **Application Management**.</span></span>
    
3. <span data-ttu-id="a6bde-220">На странице **Управление приложениями** в разделе **Веб-приложения** щелкните **Управление веб-приложениями**.</span><span class="sxs-lookup"><span data-stu-id="a6bde-220">On the **Application Management** page, in the **Web Applications** section, click **Manage web applications**.</span></span>
    
4. <span data-ttu-id="a6bde-221">Щелкните соответствующее веб-приложение.</span><span class="sxs-lookup"><span data-stu-id="a6bde-221">Click the appropriate web application.</span></span>
    
5. <span data-ttu-id="a6bde-222">Нажмите на ленте кнопку **Поставщики проверки подлинности**.</span><span class="sxs-lookup"><span data-stu-id="a6bde-222">From the ribbon, click **Authentication Providers**.</span></span>
    
6. <span data-ttu-id="a6bde-p112">В разделе **Зона** щелкните имя зоны, например **По умолчанию**.</span><span class="sxs-lookup"><span data-stu-id="a6bde-p112">Under **Zone**, click the name of the zone. For example, **Default**.</span></span>
    
7. <span data-ttu-id="a6bde-p113">На странице **Изменение параметров проверки подлинности** в разделе **Типы проверки подлинности на основе утверждений** выберите пункт **Доверенный поставщик удостоверений**, а затем щелкните имя своего поставщика (в этой статье  **ACS Provider** ). Нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="a6bde-p113">On the **Edit Authentication** page, in the **Claims Authentication Types** section, select **Trusted Identity provider**, and then click the name of your provider, which for purposes of this article is **ACS Provider**. Click **OK**.</span></span>
    
8. <span data-ttu-id="a6bde-227">На следующем рисунке показан параметр **Trusted Provider**.</span><span class="sxs-lookup"><span data-stu-id="a6bde-227">The following figure illustrates the **Trusted Provider** setting.</span></span>
    
![Параметр "Надежный поставщик" в веб-приложении](images/AddProvider_Azure.jpg)
  
## <a name="set-the-permissions"></a><span data-ttu-id="a6bde-229">Задание разрешений</span><span class="sxs-lookup"><span data-stu-id="a6bde-229">Set the permissions</span></span>

<span data-ttu-id="a6bde-230">Выполните указанные ниже действия, чтобы задать разрешения доступа к веб-приложению.</span><span class="sxs-lookup"><span data-stu-id="a6bde-230">Use the following steps to set the permissions to access the web application.</span></span>
  
1. <span data-ttu-id="a6bde-231">На главной странице Центр администрирования нажмите **Управление приложениями**.</span><span class="sxs-lookup"><span data-stu-id="a6bde-231">In Central Administration, on the home page, click **Application Management**.</span></span>
    
2. <span data-ttu-id="a6bde-232">На странице **Управление приложениями** в разделе **Веб-приложения** выберите команду **Управление веб-приложениями**.</span><span class="sxs-lookup"><span data-stu-id="a6bde-232">On the **Application Management** page, in the **Web Applications** section, click **Manage web applications**.</span></span>
    
3. <span data-ttu-id="a6bde-233">Щелкните соответствующее веб-приложение, а затем выберите пункт **Политика пользователей**.</span><span class="sxs-lookup"><span data-stu-id="a6bde-233">Click the appropriate web application, and then click **User Policy**.</span></span>
    
4. <span data-ttu-id="a6bde-234">В разделе **Политика для веб-приложения** нажмите кнопку **Добавить пользователей**.</span><span class="sxs-lookup"><span data-stu-id="a6bde-234">In **Policy for Web Application**, click **Add Users**.</span></span>
    
5. <span data-ttu-id="a6bde-235">В диалоговом окне **Добавление пользователей** щелкните соответствующие зоны в разделе **Зоны**, а затем нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="a6bde-235">In the **Add Users** dialog box, click the appropriate zone in **Zones**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="a6bde-236">В диалоговом окне **Добавление пользователей** введитеuser2@blueskyabove.onmicrosoft.com (ACS Provider).</span><span class="sxs-lookup"><span data-stu-id="a6bde-236">In the **Add Users** dialog box, typeuser2@blueskyabove.onmicrosoft.com (ACS Provider).</span></span>
    
7. <span data-ttu-id="a6bde-237">В разделе **Разрешения** выберите **Полный доступ**.</span><span class="sxs-lookup"><span data-stu-id="a6bde-237">In **Permissions**, click **Full Control**.</span></span>
    
8. <span data-ttu-id="a6bde-238">Нажмите **Готово**, а затем  **ОК**.</span><span class="sxs-lookup"><span data-stu-id="a6bde-238">Click **Finish**, and then click **OK**.</span></span>
    
<span data-ttu-id="a6bde-239">На следующем рисунке показан раздел **Добавление пользователей** существующего веб-приложения.</span><span class="sxs-lookup"><span data-stu-id="a6bde-239">The following figure illustrates the **Add Users** section of an existing web application.</span></span>
  
![Добавление пользователей в существующее веб-приложение](images/AddUsers_Azure.jpg)
  
## <a name="verify-the-new-provider"></a><span data-ttu-id="a6bde-241">Проверка нового поставщика</span><span class="sxs-lookup"><span data-stu-id="a6bde-241">Verify the new provider</span></span>

<span data-ttu-id="a6bde-242">Выполните указанные ниже действия, чтобы проверить работу поставщика удостоверений, убедившись, что новый поставщик удостоверений отображается в запросе входа.</span><span class="sxs-lookup"><span data-stu-id="a6bde-242">Use the following steps to verify that the new identity provider is working by ensuring that the new authentication provider appears on the sign-in prompt.</span></span>
  
1. <span data-ttu-id="a6bde-243">Выполните вход с использованием нового поставщика под названием **Blue Sky Above**, как показано на следующем рисунке.</span><span class="sxs-lookup"><span data-stu-id="a6bde-243">Sign in by using the new provider named **Blue Sky Above**, as illustrated in the following figure.</span></span>
    
     ![Диалоговое окно входа с новым надежным поставщиком](images/BlueSkyAbove.jpg)
  
## <a name="additional-resources"></a><span data-ttu-id="a6bde-245">Дополнительные ресурсы</span><span class="sxs-lookup"><span data-stu-id="a6bde-245">Additional resources</span></span>

[<span data-ttu-id="a6bde-246">Общие сведения о WS-Federation</span><span class="sxs-lookup"><span data-stu-id="a6bde-246">Understanding WS-Federation</span></span>](https://go.microsoft.com/fwlink/p/?linkid=188052)
  
[<span data-ttu-id="a6bde-247">Освоение облака и гибридные решения</span><span class="sxs-lookup"><span data-stu-id="a6bde-247">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
  
## <a name="join-the-discussion"></a><span data-ttu-id="a6bde-248">Присоединяйтесь к обсуждению</span><span class="sxs-lookup"><span data-stu-id="a6bde-248">Join the discussion</span></span>

|<span data-ttu-id="a6bde-249">**Свяжитесь с нами**</span><span class="sxs-lookup"><span data-stu-id="a6bde-249">**Contact us**</span></span>|<span data-ttu-id="a6bde-250">**Описание**</span><span class="sxs-lookup"><span data-stu-id="a6bde-250">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="a6bde-251">**Какое вам решение необходимо?**</span><span class="sxs-lookup"><span data-stu-id="a6bde-251">**What cloud adoption content do you need?**</span></span> <br/> |<span data-ttu-id="a6bde-p114">Мы создаем контент для решений, которые охватывают несколько продуктов и служб Майкрософт. Сообщите нам, что вы думаете о наших межсерверных решениях, или укажите интересующие вас решения, написав по адресу [MODAcontent@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20).</span><span class="sxs-lookup"><span data-stu-id="a6bde-p114">We are creating content for cloud adoption that spans multiple Microsoft cloud platforms and services. Let us know what you think about our cloud adoption content, or ask for specific content by sending email to [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20).  </span></span><br/> |
|<span data-ttu-id="a6bde-254">**Присоединяйтесь к обсуждению решений**</span><span class="sxs-lookup"><span data-stu-id="a6bde-254">**Join the cloud adoption discussion**</span></span> <br/> |<span data-ttu-id="a6bde-p115">Если вам интересны облачные решения, присоединяйтесь к теме Cloud Adoption Advisory Board (CAAB) и общайтесь с разработчиками контента Майкрософт, специалистами отрасли и клиентами со всего мира. Чтобы присоединиться, добавьте себя в качестве участника [темы CAAB (Cloud Adoption Advisory Board)](https://aka.ms/caab) на сайте Microsoft Tech Community и отправьте нам письмо на адрес [CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!). Просматривать материалы в [блоге CAAB](https://blogs.technet.com/b/solutions_advisory_board/) могут все пользователи. Однако только участники CAAB получают приглашения на закрытые вебинары, на которых мы рассказываем о новых облачных решениях и ресурсах по их внедрению.</span><span class="sxs-lookup"><span data-stu-id="a6bde-p115">If you are passionate about cloud-based solutions, consider joining the Cloud Adoption Advisory Board (CAAB) to connect with a larger, vibrant community of Microsoft content developers, industry professionals, and customers from around the globe. To join, add yourself as a member of the [CAAB (Cloud Adoption Advisory Board) space](https://aka.ms/caab) of the Microsoft Tech Community and send us a quick email at [CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!). Anyone can read community-related content on the [CAAB blog](https://blogs.technet.com/b/solutions_advisory_board/). However, CAAB members get invitations to private webinars that describe new cloud adoption resources and solutions.  </span></span><br/> |
|<span data-ttu-id="a6bde-258">**Скачать изображения, которые вы видите здесь**</span><span class="sxs-lookup"><span data-stu-id="a6bde-258">**Get the art you see here**</span></span> <br/> |<span data-ttu-id="a6bde-p116">Если вам нужна редактируемая копия иллюстративного материала из этой статьи, мы с радостью вам ее отправим. Напишите нам, указав URL-адрес и название материала, по адресу [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20).</span><span class="sxs-lookup"><span data-stu-id="a6bde-p116">If you want an editable copy of the art you see in the Solutions using Office Servers and the Cloud content, we’ll be glad to send it to you. Email your request, including the URL and title of the art, to  MODAcontent@microsoft.com mailto:modacontent@microsoft.com?subject=[Art%20Request]:%20 .</span></span><br/> |
   

