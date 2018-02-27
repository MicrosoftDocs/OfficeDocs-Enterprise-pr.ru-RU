---
title: "Защита файлов SharePoint Online с помощью Azure Information Protection"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365, Strat_O365_Enterprise
ms.custom: Strat_O365_Enterprise, Ent_Solutions
ms.assetid: 5b9c8e41-25d2-436d-89bb-9aecb9ec2b80
description: "Сводка. Защита файлов на строго конфиденциальном сайте группы SharePoint Online с помощью службы Azure Information Protection."
ms.openlocfilehash: f1a063f07b6e7488cf7512472631d0d2cae09733
ms.sourcegitcommit: c16db80a2be81db876566c578bb04f3747dbd50c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/13/2018
---
# <a name="protect-sharepoint-online-files-with-azure-information-protection"></a><span data-ttu-id="90224-103">Защита файлов SharePoint Online с помощью Azure Information Protection</span><span class="sxs-lookup"><span data-stu-id="90224-103">Protect SharePoint Online files with Azure Information Protection</span></span>

 <span data-ttu-id="90224-104">**Сводка.** Защита файлов на строго конфиденциальном сайте группы SharePoint Online с помощью службы Azure Information Protection.</span><span class="sxs-lookup"><span data-stu-id="90224-104">**Summary:** Apply Azure Information Protection to protect files in a highly confidential SharePoint Online team site.</span></span>
  
<span data-ttu-id="90224-p101">В этой статье описано, как настроить Azure Information Protection для применения шифрования и разрешений к файлам на строго конфиденциальном сайте группы SharePoint Online. Даже при скачивании с сайта файл будет по-прежнему защищен благодаря шифрованию и указанным разрешениям. Дополнительные сведения о строго конфиденциальных сайтах групп SharePoint Online см. в статье [Безопасность сайтов и файлов SharePoint Online](secure-sharepoint-online-sites-and-files.md).</span><span class="sxs-lookup"><span data-stu-id="90224-p101">Use the steps in this article to configure Azure Information Protection to provide encryption and permissions for files in a highly confidential SharePoint Online team site. The encryption and permissions protection travels with a file even when it is downloaded from the site. For more information about highly confidential SharePoint Online team sites, see [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="90224-p102">Office 365 не может обрабатывать файлы, к которым применено шифрование Azure Information Protection. Совместное редактирование, обнаружение электронных данных, поиск, Delve и другие функции совместной работы неактивны. Политики защиты от потери данных могут работать только с метаданными (включая метки Office 365), но не с содержимым этих файлов (например, номерами кредитных карт в файлах).</span><span class="sxs-lookup"><span data-stu-id="90224-p102">When Azure Information Protection encryption is applied to files stored in Office 365, the service cannot process the contents of these files. Co-authoring, eDiscovery, search, Delve, and other collaborative features do not work. Data Loss Prevention (DLP) policies can only work with the metadata (including Office 365 labels) but not the contents of these files (such as credit card numbers within files).</span></span> 
  
<span data-ttu-id="90224-111">Для начала выполните действия, описанные в статье [Как активировать службу Azure Rights Management из Центра администрирования Office 365](https://docs.microsoft.com/information-protection/deploy-use/activate-office365), со своей подпиской на Office 365.</span><span class="sxs-lookup"><span data-stu-id="90224-111">First, use the instructions in [Activate Azure RMS with the Office 365 admin center](https://docs.microsoft.com/information-protection/deploy-use/activate-office365) for your Office 365 subscription.</span></span>
  
<span data-ttu-id="90224-112">Теперь настройте Azure Information Protection, добавив новую политику области и подчиненную метку для разрешений на доступ к строго конфиденциальному сайту группы SharePoint Online и его защиты.</span><span class="sxs-lookup"><span data-stu-id="90224-112">Next, configure Azure Information Protection with a new scoped policy and sub-label for protection and permissions of your highly confidential SharePoint Online team site.</span></span>
  
1. <span data-ttu-id="90224-p103">Войдите на портал Office 365, используя учетную запись с ролью администратора компании или администратора безопасности. Дополнительные сведения см. в статье [Вход в Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="90224-p103">Sign in to the Office 365 portal with an account that has the Security Administrator or Company Administrator role. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="90224-115">Перейдите на портал Azure ([https://portal.azure.com](https://portal.azure.com)), открыв отдельную вкладку браузера.</span><span class="sxs-lookup"><span data-stu-id="90224-115">In a separate tab of your browser, go to the Azure portal ([https://portal.azure.com](https://portal.azure.com)).</span></span>
    
3. <span data-ttu-id="90224-116">Если вы настраиваете Azure Information Protection впервые, ознакомьтесь с этими [инструкциями](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).</span><span class="sxs-lookup"><span data-stu-id="90224-116">If this is the first time you are configuring Azure Information Protection, see these [instructions](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).</span></span>
    
4. <span data-ttu-id="90224-117">На панели списка выберите **Дополнительные службы**, введите **Информация**, а затем выберите **Azure Information Protection**.</span><span class="sxs-lookup"><span data-stu-id="90224-117">In the list pane, click **More services**, type **information**, and then click **Azure Information Protection**.</span></span>
    
5. <span data-ttu-id="90224-118">В колонке **Azure Information Protection**, щелкните последовательно элементы **Политики в области > + Добавить политику**.</span><span class="sxs-lookup"><span data-stu-id="90224-118">On the **Azure Information protection** blade, , click **Scoped policies > + Add a new policy**.</span></span>
    
6. <span data-ttu-id="90224-119">Введите имя новой политики в поле **Имя политики** и описание в поле **Описание**.</span><span class="sxs-lookup"><span data-stu-id="90224-119">Type a name for the new policy in **Policy name** and a description in **Description**.</span></span>
    
7. <span data-ttu-id="90224-120">Щелкните элементы **Выберите, к каким пользователям или группам будет применяться эта политика > Группы и пользователи**, а затем выберите группу доступа для участников строго конфиденциального сайта группы SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="90224-120">Click **Select which users or groups get this policy > User/Groups**, and then select the site members access group for your highly sensitive SharePoint Online team site.</span></span> 
    
8. <span data-ttu-id="90224-121">Щелкните элементы **Выбрать > ОК**.</span><span class="sxs-lookup"><span data-stu-id="90224-121">Click **Select > OK**.</span></span>
    
9. <span data-ttu-id="90224-122">Для метки **Строго конфиденциально** щелкните последовательно многоточие (…) и элемент **Добавить подчин. метку**.</span><span class="sxs-lookup"><span data-stu-id="90224-122">For the **Highly Confidential** label, click the ellipses (…), and then click **Add a sub-label**.</span></span>
    
10. <span data-ttu-id="90224-123">Введите имя подчиненной метки в поле **Имя** и описание метки в поле **Описание**.</span><span class="sxs-lookup"><span data-stu-id="90224-123">Type a name for the sub-label in **Name** and a description of the label in **Description**.</span></span>
    
11. <span data-ttu-id="90224-124">В разделе **Задайте разрешения для документов и электронных писем, имеющих эту метку** нажмите кнопку **Защитить**.</span><span class="sxs-lookup"><span data-stu-id="90224-124">In **Set permissions for documents and emails containing this label**, click **Protect**.</span></span>
    
12. <span data-ttu-id="90224-125">В разделе **Защита** выберите элемент **Azure (облачный ключ)**.</span><span class="sxs-lookup"><span data-stu-id="90224-125">In the **Protection** section, click **Azure (cloud key)**.</span></span>
    
13. <span data-ttu-id="90224-126">В колонке **Защита** в разделе **Параметры защиты** нажмите кнопку **+ Добавить разрешения**.</span><span class="sxs-lookup"><span data-stu-id="90224-126">On the **Protection** blade, under **Protection settings**, click **+ Add permissions**.</span></span>
    
14. <span data-ttu-id="90224-127">Перейдите к колонке **Добавление разрешений** и выберите **+ Обзор каталога** в разделе **Укажите пользователей и группы**.</span><span class="sxs-lookup"><span data-stu-id="90224-127">On the **Add permissions** blade, under **Specify users and groups**, click **+ Browse directory**.</span></span>
    
15. <span data-ttu-id="90224-128">В области **Пользователи и группы AAD** выберите группу доступа для членов строго конфиденциального сайта группы SharePoint Online, а затем нажмите **Выбрать**.</span><span class="sxs-lookup"><span data-stu-id="90224-128">On the **AAD Users and Groups** pane, select the site members access group for your highly sensitive SharePoint Online team site, and then click **Select**.</span></span>
    
16. <span data-ttu-id="90224-129">В разделе **Выбор разрешений из шаблона** снимите флажки **Печать**, **Копирование и извлечение контента** и **Переадресация**.</span><span class="sxs-lookup"><span data-stu-id="90224-129">Under **Choose permissions from the preset**, clear the **Print**, **Copy and extract content**, and **Forward** check boxes.</span></span>
    
17. <span data-ttu-id="90224-130">Дважды нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="90224-130">Click **OK** twice.</span></span>
    
18. <span data-ttu-id="90224-131">В колонке **Подчиненная метка** нажмите кнопку **Сохранить**.</span><span class="sxs-lookup"><span data-stu-id="90224-131">On the **Sub-label** blade, click **Save**.</span></span>
    
19. <span data-ttu-id="90224-132">Закройте колонку новой политики области.</span><span class="sxs-lookup"><span data-stu-id="90224-132">Close the new scoped policy blade.</span></span>
    
20. <span data-ttu-id="90224-133">В колонке **Azure Information Protection  политики в области** нажмите кнопку **Опубликовать**.</span><span class="sxs-lookup"><span data-stu-id="90224-133">On the **Azure Information protection - Scoped policies** blade, click **Publish**.</span></span>
    
<span data-ttu-id="90224-134">Ниже показана полученная в результате конфигурация строго конфиденциального сайта группы SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="90224-134">This is your resulting configuration for your highly confidential SharePoint Online team site.</span></span>
  
![Метка Azure Information Protection для изолированного сайта группы SharePoint Online.](images/8cc92aa4-e7bc-4c2f-a4a4-3b034b21aebf.png)
  
<span data-ttu-id="90224-136">Теперь вы можете создавать документы и защищать их с помощью службы Azure Information Protection и новой метки.</span><span class="sxs-lookup"><span data-stu-id="90224-136">You are now ready to begin creating documents and protecting them with Azure Information Protection and your new label.</span></span>
  
<span data-ttu-id="90224-p104">Вам нужно [установить клиент Azure Information Protection](https://docs.microsoft.com/information-protection/rms-client/install-client-app) на мобильном устройстве или компьютере под управлением Windows. Вы можете воспользоваться скриптом и автоматизировать установку. Кроме того, пользователи могут установить клиент вручную. Ознакомьтесь с приведенными ниже материалами.</span><span class="sxs-lookup"><span data-stu-id="90224-p104">You must [install the Azure Information Protection client](https://docs.microsoft.com/information-protection/rms-client/install-client-app) on your device or Windows-based computer. You can script and automate the installation, or users can install the client manually. See the following resources:</span></span>
  
- [<span data-ttu-id="90224-140">Клиентская часть Azure Information Protection</span><span class="sxs-lookup"><span data-stu-id="90224-140">The client side of Azure Information Protection</span></span>](https://docs.microsoft.com/information-protection/rms-client/use-client)
    
- [<span data-ttu-id="90224-141">Установка клиента Azure Information Protection</span><span class="sxs-lookup"><span data-stu-id="90224-141">Installing the Azure Information Protection client</span></span>](https://docs.microsoft.com/information-protection/rms-client/client-admin-guide)
    
- [<span data-ttu-id="90224-142">Страница скачивания для установки вручную</span><span class="sxs-lookup"><span data-stu-id="90224-142">Download page for manual installation</span></span>](https://www.microsoft.com/download/details.aspx?id=53018)
    
<span data-ttu-id="90224-p105">После установки пользователи запускают приложение Office (например, Microsoft Word) и входят с помощью своей учетной записи Office 365. Затем они могут выбрать метку в новой панели **Information Protection**. Убедитесь, что они знают, какую метку использовать для сайта группы SharePoint Online, чтобы защитить свои строго конфиденциальные файлы.</span><span class="sxs-lookup"><span data-stu-id="90224-p105">Once installed, your users run and then sign-in from an Office application (such as Microsoft Word) with their Office 365 account. A new **Information Protection** bar allows users to select the new label. Make sure that your users know the SharePoint Online team site and which label to use, to protect their highly confidential files.</span></span>
  
> [!NOTE]
> <span data-ttu-id="90224-146">Если у вас несколько строго конфиденциальных сайтов группы SharePoint Online, необходимо создать несколько политик Azure Information Protection с подчиненными метками, используя указанные выше параметры. При этом нужно настроить разрешения для каждой подчиненной метки, заданные группе доступа для участников определенного сайта группы SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="90224-146">If you have multiple highly sensitive SharePoint Online team sites, you should create multiple Azure Information Protection scoped policies with sub-labels with the above settings, with the permissions for each sub-label set to the site members access group of a specific SharePoint Online team site.</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="90224-147">См. также</span><span class="sxs-lookup"><span data-stu-id="90224-147">See Also</span></span>

[<span data-ttu-id="90224-148">Безопасность сайтов и файлов SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="90224-148">Secure SharePoint Online sites and files</span></span>](secure-sharepoint-online-sites-and-files.md)
  
[<span data-ttu-id="90224-149">Защита сайтов SharePoint Online в среде разработки и тестирования</span><span class="sxs-lookup"><span data-stu-id="90224-149">Secure SharePoint Online sites in a dev/test environment</span></span>](secure-sharepoint-online-sites-in-a-dev-test-environment.md)
  
[<span data-ttu-id="90224-150">Руководство по безопасности (Майкрософт) для политических кампаний, некоммерческих и других динамических организаций</span><span class="sxs-lookup"><span data-stu-id="90224-150">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[<span data-ttu-id="90224-151">Освоение облака и гибридные решения</span><span class="sxs-lookup"><span data-stu-id="90224-151">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)




