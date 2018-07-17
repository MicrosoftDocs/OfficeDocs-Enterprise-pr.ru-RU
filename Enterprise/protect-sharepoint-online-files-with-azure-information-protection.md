---
title: Защита файлов SharePoint Online с помощью Azure Information Protection
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_Solutions
ms.assetid: 5b9c8e41-25d2-436d-89bb-9aecb9ec2b80
description: Сводка. Защита файлов на строго конфиденциальном сайте группы SharePoint Online с помощью службы Azure Information Protection.
ms.openlocfilehash: 2c4776f5795a5a0b07be0f04b4872abadb4d31ca
ms.sourcegitcommit: b39b8ae3b4268d6475b54e2fdb62982b2c7d9943
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/12/2018
ms.locfileid: "20319290"
---
# <a name="protect-sharepoint-online-files-with-azure-information-protection"></a><span data-ttu-id="5b130-103">Защита файлов SharePoint Online с помощью Azure Information Protection</span><span class="sxs-lookup"><span data-stu-id="5b130-103">Protect SharePoint Online files with Azure Information Protection</span></span>

 <span data-ttu-id="5b130-104">**Сводка.** Защита файлов на строго конфиденциальном сайте группы SharePoint Online с помощью службы Azure Information Protection.</span><span class="sxs-lookup"><span data-stu-id="5b130-104">**Summary:** Apply Azure Information Protection to protect files in a highly confidential SharePoint Online team site.</span></span>
  
<span data-ttu-id="5b130-p101">В этой статье показано, как настроить Azure Information Protection, чтобы обеспечить шифрование и применение разрешений для файлов. Эти файлы можно добавлять в библиотеку SharePoint, настроенную на строго конфиденциальный уровень защиты. Или можно открыть файл непосредственно на сайте и использовать клиент Azure Information Protection, чтобы добавить шифрование. Даже при скачивании с сайта файл будет по-прежнему защищен благодаря шифрованию и указанным разрешениям.</span><span class="sxs-lookup"><span data-stu-id="5b130-p101">Use the steps in this article to configure Azure Information Protection to provide encryption and permissions for files. These files can be added to a SharePoint library configured for highly confidential protection. Or, you can open a file directly from the site and use the Azure Information Protection client to add encryption. The encryption and permissions protection travels with a file even when it is downloaded from the site.</span></span> 

<span data-ttu-id="5b130-p102">Эти действия являются частью более крупного решения по настройке строго конфиденциальной защиты для сайтов SharePoint и файлов на этих сайтах. Дополнительные сведения см. в статье [Безопасность сайтов и файлов SharePoint Online](secure-sharepoint-online-sites-and-files.md).</span><span class="sxs-lookup"><span data-stu-id="5b130-p102">These steps are part of a larger solution for configuring highly confidential protection for SharePoint sites and the files within these sites. For more information, see [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md).</span></span> 

<span data-ttu-id="5b130-111">Использование Azure Information Protection для файлов в SharePoint Online не рекомендуется для всех клиентов, но допустимо для клиентов, которым требуется этот уровень защиты для подмножества файлов.</span><span class="sxs-lookup"><span data-stu-id="5b130-111">Using Azure Information Protection for files in SharePoint Online is not recommended for all customers, but is an option for customers who need this level of protection for a subset of files.</span></span>

<span data-ttu-id="5b130-112">Некоторые важные замечания об этом решении:</span><span class="sxs-lookup"><span data-stu-id="5b130-112">Some important notes about this solution:</span></span>
- <span data-ttu-id="5b130-p103">Когда шифрование Azure Information Protection применяется к файлам в Office 365, служба не может обрабатывать содержимое этих файлов. Совместное редактирование, обнаружение электронных данных, поиск, Delve и другие функции совместной работы неактивны. Политики защиты от потери данных могут работать только с метаданными (включая метки Office 365), но не с содержимым этих файлов (например, номерами кредитных карт в файлах).</span><span class="sxs-lookup"><span data-stu-id="5b130-p103">When Azure Information Protection encryption is applied to files stored in Office 365, the service cannot process the contents of these files. Co-authoring, eDiscovery, search, Delve, and other collaborative features do not work. Data Loss Prevention (DLP) policies can only work with the metadata (including Office 365 labels) but not the contents of these files (such as credit card numbers within files).</span></span>
- <span data-ttu-id="5b130-p104">Для этого решения требуется, чтобы пользователь выбрал метку, которая применяет защиту от Azure Information Protection. Если вам требуется автоматическое шифрование, а также возможность индексировать и проверять файлы в SharePoint, рекомендуется использовать управление правами на доступ к данным (IRM) в SharePoint Online. При настройке библиотеки SharePoint для IRM, файлы автоматически шифруются, если они скачиваются для редактирования. Управление правами на доступ к данным SharePoint включает в себя ограничения, которые могут повлиять на ваше решение. Дополнительные сведения см. в статье [Настройка управления правами на доступ к данным (IRM) в центре администрирования SharePoint](https://support.office.com/ru-RU/article/Set-up-Information-Rights-Management-IRM-in-SharePoint-admin-center-239CE6EB-4E81-42DB-BF86-A01362FED65C).</span><span class="sxs-lookup"><span data-stu-id="5b130-p104">This solution requires a user to select a label that applies the protection from Azure Information Protection. If you require automatic encryption and the ability for SharePoint to index and inspect the files, consider using Information Rights Management (IRM) in SharePoint Online. When you configure a SharePoint library for IRM, files are automatically encrypted when they are downloaded for editing.  SharePoint IRM includes limitations that might influence your decision. For more information, see [Set up Information Rights Management (IRM) in SharePoint admin center](https://support.office.com/ru-RU/article/Set-up-Information-Rights-Management-IRM-in-SharePoint-admin-center-239CE6EB-4E81-42DB-BF86-A01362FED65C).</span></span>

##<a name="admin-setup"></a><span data-ttu-id="5b130-121">Настройка администратора</span><span class="sxs-lookup"><span data-stu-id="5b130-121">Admin setup</span></span>
<span data-ttu-id="5b130-122">Сперва выполните для настройки подписки на Office 365 действия, описанные в статье [Как активировать Azure RMS в Центре администрирования Office 365](https://docs.microsoft.com/information-protection/deploy-use/activate-office365).</span><span class="sxs-lookup"><span data-stu-id="5b130-122">First, use the instructions in [Activate Azure RMS with the Office 365 admin center](https://docs.microsoft.com/information-protection/deploy-use/activate-office365) for your Office 365 subscription.</span></span>
  
<span data-ttu-id="5b130-123">Теперь настройте Azure Information Protection, добавив новую политику области и подчиненную метку для разрешений на доступ к строго конфиденциальному сайту группы SharePoint Online и его защиты.</span><span class="sxs-lookup"><span data-stu-id="5b130-123">Next, configure Azure Information Protection with a new scoped policy and sub-label for protection and permissions of your highly confidential SharePoint Online team site.</span></span>
  
1. <span data-ttu-id="5b130-p105">Войдите на портал Office 365, используя учетную запись с ролью администратора компании или администратора безопасности. Справочные сведения см. в статье [Вход в Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="5b130-p105">Sign in to the Office 365 portal with an account that has the Security Administrator or Company Administrator role. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="5b130-126">Перейдите на портал Azure ([https://portal.azure.com](https://portal.azure.com)), открыв отдельную вкладку браузера.</span><span class="sxs-lookup"><span data-stu-id="5b130-126">In a separate tab of your browser, go to the Azure portal ([https://portal.azure.com](https://portal.azure.com)).</span></span>
    
3. <span data-ttu-id="5b130-127">Если вы настраиваете Azure Information Protection впервые, ознакомьтесь с этими [инструкциями](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).</span><span class="sxs-lookup"><span data-stu-id="5b130-127">If this is the first time you are configuring Azure Information Protection, see these [instructions](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).</span></span>
    
4. <span data-ttu-id="5b130-128">На панели списка выберите **Все службы**, введите **information**, а затем выберите **Azure Information Protection**.</span><span class="sxs-lookup"><span data-stu-id="5b130-128">In the list pane, click **All services**, type **information**, and then click **Azure Information Protection**.</span></span>
    
5. <span data-ttu-id="5b130-129">В колонке **Azure Information Protection**, щелкните последовательно элементы **Политики в области > + Добавить политику**.</span><span class="sxs-lookup"><span data-stu-id="5b130-129">On the **Azure Information protection** blade, , click **Scoped policies > + Add a new policy**.</span></span>
    
6. <span data-ttu-id="5b130-130">Введите имя новой политики в поле **Имя политики** и описание в поле **Описание**.</span><span class="sxs-lookup"><span data-stu-id="5b130-130">Type a name for the new policy in **Policy name** and a description in **Description**.</span></span>
    
7. <span data-ttu-id="5b130-131">Щелкните элементы **Выберите, к каким пользователям или группам будет применяться эта политика > Группы и пользователи**, а затем выберите группу доступа для участников строго конфиденциального сайта группы SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="5b130-131">Click **Select which users or groups get this policy > User/Groups**, and then select the site members access group for your highly sensitive SharePoint Online team site.</span></span> 
    
8. <span data-ttu-id="5b130-132">Щелкните элементы **Выбрать > ОК**.</span><span class="sxs-lookup"><span data-stu-id="5b130-132">Click **Select > OK**.</span></span>
    
9. <span data-ttu-id="5b130-133">Для метки **Строго конфиденциально** щелкните последовательно многоточие (…) и элемент **Добавить подчин. метку**.</span><span class="sxs-lookup"><span data-stu-id="5b130-133">For the **Highly Confidential** label, click the ellipses (…), and then click **Add a sub-label**.</span></span>
    
10. <span data-ttu-id="5b130-134">Введите имя подчиненной метки в поле **Имя** и описание метки в поле **Описание**.</span><span class="sxs-lookup"><span data-stu-id="5b130-134">Type a name for the sub-label in **Name** and a description of the label in **Description**.</span></span>
    
11. <span data-ttu-id="5b130-135">В разделе **Задайте разрешения для документов и электронных писем, имеющих эту метку** нажмите кнопку **Защитить**.</span><span class="sxs-lookup"><span data-stu-id="5b130-135">In **Set permissions for documents and emails containing this label**, click **Protect**.</span></span>
    
12. <span data-ttu-id="5b130-136">В разделе **Защита** выберите элемент **Azure (облачный ключ)**.</span><span class="sxs-lookup"><span data-stu-id="5b130-136">In the **Protection** section, click **Azure (cloud key)**.</span></span>
    
13. <span data-ttu-id="5b130-137">В колонке **Защита** в разделе **Параметры защиты** нажмите кнопку **+ Добавить разрешения**.</span><span class="sxs-lookup"><span data-stu-id="5b130-137">On the **Protection** blade, under **Protection settings**, click **+ Add permissions**.</span></span>
    
14. <span data-ttu-id="5b130-138">Перейдите к колонке **Добавление разрешений** и выберите **+ Обзор каталога** в разделе **Укажите пользователей и группы**.</span><span class="sxs-lookup"><span data-stu-id="5b130-138">On the **Add permissions** blade, under **Specify users and groups**, click **+ Browse directory**.</span></span>
    
15. <span data-ttu-id="5b130-139">В области **Пользователи и группы AAD** выберите группу доступа для членов строго конфиденциального сайта группы SharePoint Online, а затем нажмите **Выбрать**.</span><span class="sxs-lookup"><span data-stu-id="5b130-139">On the **AAD Users and Groups** pane, select the site members access group for your highly sensitive SharePoint Online team site, and then click **Select**.</span></span>
    
16. <span data-ttu-id="5b130-140">В разделе **Выбор разрешений из шаблона** снимите флажки **Печать**, **Копирование и извлечение контента** и **Переадресация**.</span><span class="sxs-lookup"><span data-stu-id="5b130-140">Under **Choose permissions from the preset**, clear the **Print**, **Copy and extract content**, and **Forward** check boxes.</span></span>
    
17. <span data-ttu-id="5b130-141">Дважды нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="5b130-141">Click **OK** twice.</span></span>
    
18. <span data-ttu-id="5b130-142">В колонке **Подчиненная метка** нажмите кнопку **Сохранить**.</span><span class="sxs-lookup"><span data-stu-id="5b130-142">On the **Sub-label** blade, click **Save**.</span></span>
    
19. <span data-ttu-id="5b130-143">Закройте колонку новой политики области.</span><span class="sxs-lookup"><span data-stu-id="5b130-143">Close the new scoped policy blade.</span></span>
    
20. <span data-ttu-id="5b130-144">В колонке **Azure Information Protection – политики в области** нажмите кнопку **Опубликовать**.</span><span class="sxs-lookup"><span data-stu-id="5b130-144">On the **Azure Information protection - Scoped policies** blade, click **Publish**.</span></span>
    
 
##<a name="client-setup"></a><span data-ttu-id="5b130-145">Настройка клиента</span><span class="sxs-lookup"><span data-stu-id="5b130-145">Client setup</span></span>
<span data-ttu-id="5b130-146">Теперь вы можете создавать документы и защищать их с помощью службы Azure Information Protection и новой метки.</span><span class="sxs-lookup"><span data-stu-id="5b130-146">You are now ready to begin creating documents and protecting them with Azure Information Protection and your new label.</span></span>
  
<span data-ttu-id="5b130-p106">Необходимо [установить клиент Azure Information Protection](https://docs.microsoft.com/information-protection/rms-client/install-client-app) на мобильном устройстве или компьютере под управлением Windows. Вы можете воспользоваться скриптом и автоматизировать установку. Кроме того, пользователи могут установить клиент вручную. Просмотрите указанные ниже ресурсы.</span><span class="sxs-lookup"><span data-stu-id="5b130-p106">You must [install the Azure Information Protection client](https://docs.microsoft.com/information-protection/rms-client/install-client-app) on your device or Windows-based computer. You can script and automate the installation, or users can install the client manually. See the following resources:</span></span>
  
- [<span data-ttu-id="5b130-150">Клиентская часть Azure Information Protection</span><span class="sxs-lookup"><span data-stu-id="5b130-150">The client side of Azure Information Protection</span></span>](https://docs.microsoft.com/information-protection/rms-client/use-client)
    
- [<span data-ttu-id="5b130-151">Установка клиента Azure Information Protection</span><span class="sxs-lookup"><span data-stu-id="5b130-151">Installing the Azure Information Protection client</span></span>](https://docs.microsoft.com/information-protection/rms-client/client-admin-guide)
    
- [<span data-ttu-id="5b130-152">Страница скачивания для установки вручную</span><span class="sxs-lookup"><span data-stu-id="5b130-152">Download page for manual installation</span></span>](https://www.microsoft.com/download/details.aspx?id=53018)
    
<span data-ttu-id="5b130-p107">После установки пользователи выполняют запуск и вход из приложения Office (например, Microsoft Word) с указанием своей учетной записи Office 365. С помощью новой панели **Information Protection** пользователи могут выбрать новую метку. Убедитесь, что они знают, какую метку использовать для сайта группы SharePoint Online, чтобы защитить свои строго конфиденциальные файлы.</span><span class="sxs-lookup"><span data-stu-id="5b130-p107">Once installed, your users run and then sign-in from an Office application (such as Microsoft Word) with their Office 365 account. A new **Information Protection** bar allows users to select the new label. Make sure that your users know the SharePoint Online team site and which label to use, to protect their highly confidential files.</span></span>
  
> [!NOTE]
> <span data-ttu-id="5b130-156">Если у вас несколько строго конфиденциальных сайтов группы SharePoint Online, необходимо создать несколько политик области Azure Information Protection с подчиненными метками, используя указанные выше параметры. При этом нужно настроить разрешения для каждой подчиненной метки, заданные группе доступа для участников определенного сайта группы SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="5b130-156">If you have multiple highly sensitive SharePoint Online team sites, you should create multiple Azure Information Protection scoped policies with sub-labels with the above settings, with the permissions for each sub-label set to the site members access group of a specific SharePoint Online team site.</span></span> 
  
##<a name="adding-permissions-for-external-users"></a><span data-ttu-id="5b130-157">Добавление разрешений для внешних пользователей</span><span class="sxs-lookup"><span data-stu-id="5b130-157">Adding permissions for external users</span></span>
<span data-ttu-id="5b130-p108">Предоставить внешним пользователям доступ к файлам, защищенным с помощью Azure Information Protection, можно двумя способами. В обоих случаях внешним пользователям необходима учетная запись Azure AD. Если внешние пользователи не состоят в организации, использующей Azure AD, они могут получить личную учетную запись Azure AD на странице регистрации: [https://aka.ms/aip-signup](https://aka.ms/aip-signup).</span><span class="sxs-lookup"><span data-stu-id="5b130-p108">There are two ways you can grant external users access to files protected with Azure Information Protection. In both these cases, external users must have an Azure AD account. If external users aren't members of an organization that uses Azure AD, they can obtain an Azure AD account as an individual by using this sign-up page: [https://aka.ms/aip-signup](https://aka.ms/aip-signup).</span></span>

 - <span data-ttu-id="5b130-p109">Добавление внешних пользователей в группу Azure AD, используемую для настройки защиты метки. Для начала потребуется добавить в каталог учетную запись B2B-пользователя. Может потребоваться несколько часов, чтобы [служба управления правами Azure кэшировала данные о членстве в группах](https://docs.microsoft.com/ru-RU/azure/information-protection/plan-design/prepare#group-membership-caching-by-azure-information-protection).</span><span class="sxs-lookup"><span data-stu-id="5b130-p109">Add external users to an Azure AD group that is used to configure protection for a label. You’ll need to first add the account as a B2B user in your directory. It can take a couple of hours for group membership caching by Azure Rights Management. With this method, permissions are granted to all existing files protected with the label (even files protected before a user is added to the Azure AD group).</span></span>  
 - <span data-ttu-id="5b130-p110">Непосредственное добавление внешних пользователей в защиту метки. Вы можете добавить всех пользователей из организации (например, Fabrikam.com), группу Azure AD (например, финансовый отдел в организации) или пользователя. Например, вы можете добавить внешнюю команду контролеров для защиты метки.</span><span class="sxs-lookup"><span data-stu-id="5b130-p110">Add external users directly to the label protection. You can add all users from an organization (e.g. Fabrikam.com), an Azure AD group (such as a finance group within an organization), or an individual user. For example, you can add an external team of regulators to the protection for a label. With this method, permissions are granted only to files protected with the label after the external entity is added to the protection.</span></span>

## <a name="see-also"></a><span data-ttu-id="5b130-167">См. также</span><span class="sxs-lookup"><span data-stu-id="5b130-167">See Also</span></span>

[<span data-ttu-id="5b130-168">Безопасность сайтов и файлов SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="5b130-168">Secure SharePoint Online sites and files</span></span>](secure-sharepoint-online-sites-and-files.md)
  
[<span data-ttu-id="5b130-169">Защита сайтов SharePoint Online в среде разработки и тестирования</span><span class="sxs-lookup"><span data-stu-id="5b130-169">Secure SharePoint Online sites in a dev/test environment</span></span>](secure-sharepoint-online-sites-in-a-dev-test-environment.md)
  
[<span data-ttu-id="5b130-170">Руководство по безопасности (Майкрософт) для политических кампаний, некоммерческих и других динамических организаций</span><span class="sxs-lookup"><span data-stu-id="5b130-170">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[<span data-ttu-id="5b130-171">Освоение облака и гибридные решения</span><span class="sxs-lookup"><span data-stu-id="5b130-171">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)




