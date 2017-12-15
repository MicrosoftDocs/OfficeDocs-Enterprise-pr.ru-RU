---
title: "Руководства по лаборатории тестирования для принятия облачных решений"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: hub-page
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Hybrid
- Ent_O365_Top
ms.custom:
- DecEntMigration
- Strat_O365_Enterprise
- Ent_TLGs
ms.assetid: 706d5449-45e5-4b0c-a012-ab60501899ad
description: "Сводка: Используйте эти облака внедрения тестирование руководства по лаборатории (руководствам) для настройки для демонстрации, проверки концепции или средах разработки и тестирования для Office 365, мобильности Enterprise + безопасности (Командной), Dynamics 365 и продуктов Office Server."
ms.openlocfilehash: 532215a08e28a9d67cd19ef60d60419b06df4957
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2017
---
# <a name="cloud-adoption-test-lab-guides-tlgs"></a><span data-ttu-id="35f57-103">Руководства по лаборатории тестирования для принятия облачных решений</span><span class="sxs-lookup"><span data-stu-id="35f57-103">Cloud adoption Test Lab Guides (TLGs)</span></span>

 <span data-ttu-id="35f57-104">**Сводка:** Настройка демонстрации, проверки концепции или средах разработки и тестирования для Office 365, мобильности Enterprise + безопасности (Командной), Dynamics 365 и продуктов Office Server с помощью этих облачных внедрения тестирование руководства по лаборатории (руководствам).</span><span class="sxs-lookup"><span data-stu-id="35f57-104">**Summary:** Use these cloud adoption Test Lab Guides (TLGs) to set up demonstration, proof of concept, or dev/test environments for Office 365, Enterprise Mobility + Security (EMS), Dynamics 365, and Office Server products.</span></span>
  
<span data-ttu-id="35f57-p101">Руководства вы найдете помогают быстро узнать о продуктах Майкрософт. Они отлично подходит для ситуаций, где необходимо оценить технологии или конфигурации, прежде чем оно подходит ли вам или перед при развертывании в работе пользователей. Практический опыт «построения проблемы в работе и работы» помогает понять требования к развертыванию новый продукт или решений, чтобы вы могли лучше запланировать для размещения в рабочей среде.</span><span class="sxs-lookup"><span data-stu-id="35f57-p101">TLGs help you quickly learn about Microsoft products. They're great for situations where you need to evaluate a technology or configuration before you decide whether it's right for you or before you roll it out to users. The "I built it out myself and it works" hands-on experience helps you understand the deployment requirements of a new product or solution so you can better plan for hosting it in production.</span></span>
  
<span data-ttu-id="35f57-108">Кроме того, эти руководства помогают создавать типичные среды для разработки и тестирования.</span><span class="sxs-lookup"><span data-stu-id="35f57-108">TLGs also create representative environments for development and testing of applications, also known as dev/test environments.</span></span>
  
![Руководства по лаборатории тестирования в Microsoft Cloud](images/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
<span data-ttu-id="35f57-110">Прежде чем углубляться в разделе следующие дополнительные ресурсы:</span><span class="sxs-lookup"><span data-stu-id="35f57-110">See these additional resources before diving in:</span></span>
  
- <span data-ttu-id="35f57-111">Просмотр сеанса Microsoft Virtual Academy [взаимодействия Microsoft Cloud с руководствах по лаборатории тестирования внедрения облака](https://mva.microsoft.com/en-US/training-courses/experience-the-microsoft-cloud-with-cloud-adoption-test-lab-guides-17960?l=LXNRdhSLE_1000115881 ) (только 22 минут).</span><span class="sxs-lookup"><span data-stu-id="35f57-111">View the [Experience the Microsoft Cloud with Cloud Adoption Test Lab Guides](https://mva.microsoft.com/en-US/training-courses/experience-the-microsoft-cloud-with-cloud-adoption-test-lab-guides-17960?l=LXNRdhSLE_1000115881 ) Microsoft Virtual Academy session (only 22 minutes).</span></span>
    
- <span data-ttu-id="35f57-112">Щелкните [здесь](http://aka.ms/catlgstack), чтобы просмотреть схему всех статей, относящихся к руководствам по лаборатории тестирования Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="35f57-112">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
    
## <a name="office-365-devtest-environment"></a><span data-ttu-id="35f57-113">Среда разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="35f57-113">Office 365 dev/test environment</span></span>
<span data-ttu-id="35f57-114"><a name="O365"> </a></span><span class="sxs-lookup"><span data-stu-id="35f57-114"></span></span>

<span data-ttu-id="35f57-115">Следующие статьи помогут вам создать среду разработки и тестирования Office 365:</span><span class="sxs-lookup"><span data-stu-id="35f57-115">Use these articles to build your Office 365 dev/test environment:</span></span>
  
- [<span data-ttu-id="35f57-116">Базовая конфигурация среды разработки и тестирования</span><span class="sxs-lookup"><span data-stu-id="35f57-116">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
    
    <span data-ttu-id="35f57-p102">Создание упрощенной интрасети, выполняющейся в службах инфраструктуры Microsoft Azure. Это действие не является обязательным для создания имитации конфигурации предприятия.</span><span class="sxs-lookup"><span data-stu-id="35f57-p102">Create a simplified intranet running in Microsoft Azure infrastructure services. This is an optional step if you want to build a simulated enterprise configuration.</span></span>
    
- [<span data-ttu-id="35f57-119">Среда разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="35f57-119">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
    
    <span data-ttu-id="35f57-120">Создание подписки пробной версии Office 365 корпоративный E5, что можно сделать с компьютера или из интрасети упрощенный под управлением в службах инфраструктуры.</span><span class="sxs-lookup"><span data-stu-id="35f57-120">Create an Office 365 Enterprise E5 trial subscription, which you can do from your computer or from a simplified intranet running in Azure infrastructure services.</span></span>
    
- [<span data-ttu-id="35f57-121">DirSync для среды разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="35f57-121">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
    
    <span data-ttu-id="35f57-p103">Установка и настройка Azure AD Connect для синхронизации каталогов с синхронизацией паролей. Это действие не является обязательным для создания имитации конфигурации предприятия.</span><span class="sxs-lookup"><span data-stu-id="35f57-p103">Install and configure Azure AD Connect for directory synchronization with password synchronization. This is an optional step if you want to build a simulated enterprise configuration.</span></span>
    
<span data-ttu-id="35f57-124">Для среды разработки и тестирования Office 365 используйте эти статьи для демонстрации компонентов корпоративного выпуска Office 365:</span><span class="sxs-lookup"><span data-stu-id="35f57-124">For your Office 365 dev/test environment, use these articles to demonstrate enterprise features of Office 365:</span></span>
  
- [<span data-ttu-id="35f57-125">Многофакторная проверка подлинности для среды разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="35f57-125">Multi-factor authentication for your Office 365 dev/test environment</span></span>](multi-factor-authentication-for-your-office-365-dev-test-environment.md)
    
    <span data-ttu-id="35f57-126">Настройте и протестируйте дополнительную проверку подлинности, отправив текстовое сообщение на свой смартфон для учетной записи, указанной при подписке на Office 365.</span><span class="sxs-lookup"><span data-stu-id="35f57-126">Configure and test secondary authentication using a text message sent to your smart phone for an account in your Office 365 subscription.</span></span>
    
- [<span data-ttu-id="35f57-127">Федеративное удостоверение для среды разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="35f57-127">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)
    
    <span data-ttu-id="35f57-128">Настройка и демонстрация федеративной проверки подлинности для учетных записей, настроенных в домене Windows Server Active Directory.</span><span class="sxs-lookup"><span data-stu-id="35f57-128">Configure and demonstrate federated authentication with the accounts of a Windows Server Active Directory domain.</span></span>
    
- [<span data-ttu-id="35f57-129">Облако безопасности приложения для Office 365 dev/тестовой среды</span><span class="sxs-lookup"><span data-stu-id="35f57-129">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)
    
    <span data-ttu-id="35f57-130">Настройка и демонстрация безопасности облачных приложения Office 365, которая позволяет создавать политики, которые наблюдения за и сообщить о подозрительных действий в подписки Office 365.</span><span class="sxs-lookup"><span data-stu-id="35f57-130">Configure and demonstrate Office 365 Cloud App Security, which allows you to create policies that monitor for and inform you of suspicious activities in your Office 365 subscription.</span></span>
    
- [<span data-ttu-id="35f57-131">Дополнительные защиту от угроз для вашей среды разработки или тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="35f57-131">Advanced Threat Protection for your Office 365 dev/test environment</span></span>](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
    
    <span data-ttu-id="35f57-132">Настройка и демонстрация Advanced Threat Protection — компонента Exchange Online Protection (EOP), позволяющего оградить электронную почту от вредоносных программ.</span><span class="sxs-lookup"><span data-stu-id="35f57-132">Configure and demonstrate Advanced Threat Protection, which is a feature of Exchange Online Protection (EOP) that helps keep malware out of your email.</span></span>
    
- [<span data-ttu-id="35f57-133">Расширенные eDiscovery для вашей среды разработки или тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="35f57-133">Advanced eDiscovery for your Office 365 dev/test environment</span></span>](advanced-ediscovery-for-your-office-365-dev-test-environment.md)
    
    <span data-ttu-id="35f57-134">Добавление данных для примера и демонстрация функции Advanced eDiscovery, позволяющей быстро находить и анализировать данные, хранящиеся в Office 365, в том числе электронные сообщения и документы.</span><span class="sxs-lookup"><span data-stu-id="35f57-134">Add example data and demonstrate Advanced eDiscovery, which allows you to quickly find and analyze the data that is stored in Office 365, including email and documents.</span></span>
    
- [<span data-ttu-id="35f57-135">Защита конфиденциальных файлов в Office 365 dev/тестовой среде</span><span class="sxs-lookup"><span data-stu-id="35f57-135">Sensitive file protection in the Office 365 dev/test environment</span></span>](sensitive-file-protection-in-the-office-365-dev-test-environment.md)
    
    <span data-ttu-id="35f57-136">Демонстрация того, как с помощью управления правами на доступ к данным Office 365 можно защитить конфиденциальные документы, даже если их случайно поместили не в ту папку.</span><span class="sxs-lookup"><span data-stu-id="35f57-136">Demonstrate how you can use Office 365 Information Rights Management to protect the data in sensitive documents, even when they are accidentally posted in the wrong document folders.</span></span>
    
- [<span data-ttu-id="35f57-137">Классификации данных и маркировки в Office 365 dev/тестовой среде</span><span class="sxs-lookup"><span data-stu-id="35f57-137">Data classification and labeling in the Office 365 dev/test environment</span></span>](data-classification-and-labeling-in-the-office-365-dev-test-environment.md)
    
    <span data-ttu-id="35f57-138">Показано, как клиент защиты информации Azure (AIP) можно использовать для классификации документов с помощью различных уровней безопасности.</span><span class="sxs-lookup"><span data-stu-id="35f57-138">Demonstrate how the Azure Information Protection (AIP) client can be used to classify documents with various levels of security.</span></span>
    
- [<span data-ttu-id="35f57-139">Изолированный SharePoint Online группы сайта dev/тестовой среды</span><span class="sxs-lookup"><span data-stu-id="35f57-139">Isolated SharePoint Online team site dev/test environment</span></span>](isolated-sharepoint-online-team-site-dev-test-environment.md)
    
    <span data-ttu-id="35f57-140">Показано, как создать сайт группы SharePoint Online, изолируется от других отделов организации засекреченные или конфиденциальные сильно ресурсов для.</span><span class="sxs-lookup"><span data-stu-id="35f57-140">Demonstrate how to create a SharePoint Online team site that is isolated from the rest of the organization for sensitive or highly confidential resources.</span></span>
    
## <a name="the-microsoft-365-enterprise-devtest-environment"></a><span data-ttu-id="35f57-141">Среда разработки и тестирования Microsoft 365 корпоративный</span><span class="sxs-lookup"><span data-stu-id="35f57-141">The Microsoft 365 Enterprise dev/test environment</span></span>
<span data-ttu-id="35f57-142"><a name="O365"> </a></span><span class="sxs-lookup"><span data-stu-id="35f57-142"></span></span>

<span data-ttu-id="35f57-143">Создайте dev/тестовой среды для сценариев [Microsoft 365 для предприятия](https://docs.microsoft.com/microsoft-365-enterprise/) с в этих статьях:</span><span class="sxs-lookup"><span data-stu-id="35f57-143">Create a dev/test environment for [Microsoft 365 Enterprise](https://docs.microsoft.com/microsoft-365-enterprise/) scenarios with these articles:</span></span>
  
- [<span data-ttu-id="35f57-144">Microsoft 365 Enterprise dev/тестовой среды</span><span class="sxs-lookup"><span data-stu-id="35f57-144">The Microsoft 365 Enterprise dev/test environment</span></span>](the-microsoft-365-enterprise-dev-test-environment.md)
    
    <span data-ttu-id="35f57-145">Создание начальной среды, включая Office 365 E5, Командной E5 и компьютера под управлением Windows 10 Enterprise.</span><span class="sxs-lookup"><span data-stu-id="35f57-145">Create the initial environment that includes Office 365 E5, EMS E5, and a computer running Windows 10 Enterprise.</span></span>
    
- [<span data-ttu-id="35f57-146">MAM политик для вашей среды разработки или тестирования Microsoft 365 для предприятия</span><span class="sxs-lookup"><span data-stu-id="35f57-146">MAM policies for your Microsoft 365 Enterprise dev/test environment</span></span>](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
    
    <span data-ttu-id="35f57-147">Создание групп пользователей и политик управления мобильными приложениями (MAM) для устройств iOS и Android.</span><span class="sxs-lookup"><span data-stu-id="35f57-147">Create user groups and mobile application management (MAM) policies for ioS and Android devices.</span></span>
    
- [<span data-ttu-id="35f57-148">Регистрация операций ввода-вывода и Android в среде разработки и тестирования Microsoft Enterprise 365</span><span class="sxs-lookup"><span data-stu-id="35f57-148">Enroll iOS and Android devices in your Microsoft Enterprise 365 dev/test environment</span></span>](enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-dev-test-environ.md)
    
    <span data-ttu-id="35f57-149">Регистрация устройств с ОС iOS или Android и удаленное управление ими.</span><span class="sxs-lookup"><span data-stu-id="35f57-149">Enroll iOS or Android devices and manage them remotely.</span></span>
    
## <a name="office-365-and-dynamics-365-devtest-environment"></a><span data-ttu-id="35f57-150">Среда разработки и тестирования для Office 365 и Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="35f57-150">Office 365 and Dynamics 365 dev/test environment</span></span>
<span data-ttu-id="35f57-151"><a name="O365_D365"> </a></span><span class="sxs-lookup"><span data-stu-id="35f57-151"></span></span>

<span data-ttu-id="35f57-152">В следующих статьях описано, как добавить пробную подписку на Dynamics 365 и протестировать интегрированные компоненты и сценарии Office 365 и Dynamics 365:</span><span class="sxs-lookup"><span data-stu-id="35f57-152">Add a Dynamics 365 trial subscription and test Office 365 and Dynamics 365 integrated features and scenarios with these articles:</span></span>
  
- [<span data-ttu-id="35f57-153">Среда разработки и тестирования для Office 365 и Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="35f57-153">Office 365 and Dynamics 365 dev/test environment</span></span>](office-365-and-dynamics-365-dev-test-environment.md)
    
    <span data-ttu-id="35f57-154">Добавьте пробную подписку на Dynamics 365, а также лицензии и разрешения на Dynamics 365 для учетных записей пользователей.</span><span class="sxs-lookup"><span data-stu-id="35f57-154">Add a Dynamics 365 trial subscription and Dynamics 365 licences and permissions to your user accounts.</span></span>
    
- [<span data-ttu-id="35f57-155">Функция интеграции с Exchange Online для Office 365 и Dynamics 365 dev/тестовой среды</span><span class="sxs-lookup"><span data-stu-id="35f57-155">Exchange Online integration for your Office 365 and Dynamics 365 dev/test environment</span></span>](exchange-online-integration-for-your-office-365-and-dynamics-365-dev-test-enviro.md)
    
    <span data-ttu-id="35f57-156">Настройка и затем Демонстрация Office 365 Dynamics 365 совместная работа и почтовых ящиков в Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="35f57-156">Configure and then demonstrate how Office 365 and Dynamics 365 work together in Exchange Online mailboxes.</span></span>
    
## <a name="the-one-microsoft-cloud-devtest-environment"></a><span data-ttu-id="35f57-157">Среда разработки и тестирования One Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="35f57-157">The One Microsoft Cloud dev/test environment</span></span>
<span data-ttu-id="35f57-158"><a name="O365_D365"> </a></span><span class="sxs-lookup"><span data-stu-id="35f57-158"></span></span>

<span data-ttu-id="35f57-p104">Создание среды разработки или тестирования, включающий все облака корпорации Майкрософт: Office 365, Azure, Командной и Dynamics 365. Просмотрите [один корпорации Майкрософт облачной dev/тестовой среды](the-one-microsoft-cloud-dev-test-environment.md) для получения пошаговых инструкций.</span><span class="sxs-lookup"><span data-stu-id="35f57-p104">Create a dev/test environment that includes all of Microsoft's cloud offerings: Office 365, Azure, EMS, and Dynamics 365. See [The One Microsoft Cloud dev/test environment](the-one-microsoft-cloud-dev-test-environment.md) for the step-by-step instructions.</span></span>
  
## <a name="simulated-cross-premises-devtest-environments"></a><span data-ttu-id="35f57-161">Имитация гибридной среды разработки и тестирования</span><span class="sxs-lookup"><span data-stu-id="35f57-161">Simulated cross-premises dev/test environments</span></span>
<span data-ttu-id="35f57-162"><a name="O365_D365"> </a></span><span class="sxs-lookup"><span data-stu-id="35f57-162"></span></span>

<span data-ttu-id="35f57-163">Сведения о том, как создать гибридную среду тестирования и разработки, включающую виртуальную сеть Azure и имитацию локальной сети, вы найдете в таких статьях:</span><span class="sxs-lookup"><span data-stu-id="35f57-163">You can create a cross-premises dev/test environment, which includes an Azure virtual network and a simulated on-premises network, with these articles:</span></span>
  
- [<span data-ttu-id="35f57-164">Имитации распределенной виртуальной сети в Azure</span><span class="sxs-lookup"><span data-stu-id="35f57-164">Simulated cross-premises virtual network in Azure</span></span>](simulated-cross-premises-virtual-network-in-azure.md)
    
    <span data-ttu-id="35f57-165">Создание имитации интрасети, подключенной к виртуальной сети Azure в гибридной облачной конфигурации.</span><span class="sxs-lookup"><span data-stu-id="35f57-165">Create a simulated intranet connected to an Azure virtual network in a hybrid cloud configuration.</span></span>
    
- [<span data-ttu-id="35f57-166">SharePoint Server интрасети 2016 в среде Azure разработку и тестирование</span><span class="sxs-lookup"><span data-stu-id="35f57-166">Intranet SharePoint Server 2016 in Azure dev/test environment</span></span>](https://technet.microsoft.com/library/mt806351%28v=office.16%29.aspx)
    
    <span data-ttu-id="35f57-167">Создание односерверной фермы SharePoint Server 2016 в виртуальной сети Azure и проверка возможности подключения и администрирования в имитации локальной сети.</span><span class="sxs-lookup"><span data-stu-id="35f57-167">Create a single-server SharePoint Server 2016 farm in the Azure virtual network and test connectivity and administration from the simulated on-premises network.</span></span>
    
## <a name="additional-cloud-based-devtest-environments"></a><span data-ttu-id="35f57-168">Дополнительные облачные среды разработки и тестирования</span><span class="sxs-lookup"><span data-stu-id="35f57-168">Additional cloud-based dev/test environments</span></span>
<span data-ttu-id="35f57-169"><a name="ADD_TLGs"> </a></span><span class="sxs-lookup"><span data-stu-id="35f57-169"></span></span>

<span data-ttu-id="35f57-170">В службы инфраструктуры Azure можно также добавить следующие облачные среды разработки и тестирования:</span><span class="sxs-lookup"><span data-stu-id="35f57-170">Here are additional cloud-based dev/test environments that you can create in Azure infrastructure services:</span></span>
  
- [<span data-ttu-id="35f57-171">SharePoint Server 2016 dev/тестовой среды в Azure</span><span class="sxs-lookup"><span data-stu-id="35f57-171">SharePoint Server 2016 dev/test environment in Azure</span></span>](https://technet.microsoft.com/library/mt723354.aspx)
    
    <span data-ttu-id="35f57-172">Создание односерверной фермы SharePoint Server 2016 в службах инфраструктуры Azure.</span><span class="sxs-lookup"><span data-stu-id="35f57-172">Build a single-server SharePoint Server 2016 farm in Azure infrastructure services.</span></span>
    
- [<span data-ttu-id="35f57-173">Среда разработки и тестирования Exchange 2016 в Azure</span><span class="sxs-lookup"><span data-stu-id="35f57-173">Exchange 2016 dev/test environment in Azure</span></span>](https://technet.microsoft.com/library/mt733070%28v=exchg.160%29.aspx)
    
    <span data-ttu-id="35f57-174">Создание одного сервера Exchange 2016 в службах инфраструктуры Azure.</span><span class="sxs-lookup"><span data-stu-id="35f57-174">Build a single Exchange 2016 server in Azure infrastructure services.</span></span>
    
- [<span data-ttu-id="35f57-175">Среды разработки или тестирования SharePoint Server 2013 в Azure</span><span class="sxs-lookup"><span data-stu-id="35f57-175">SharePoint Server 2013 dev/test environments in Azure</span></span>](http://technet.microsoft.com/library/165de4d5-8fe6-4fbb-a15b-39a8b0a0eb23.aspx)
    
    <span data-ttu-id="35f57-176">Создание ферм SharePoint Server 2013 (базовых и с высоким уровнем доступности) в службах инфраструктуры Azure.</span><span class="sxs-lookup"><span data-stu-id="35f57-176">Build basic and high-availability SharePoint Server 2013 farms in Azure infrastructure services.</span></span>
    
<span data-ttu-id="35f57-177">**Присоединяйтесь к обсуждению**</span><span class="sxs-lookup"><span data-stu-id="35f57-177">**Join the discussion**</span></span>

|<span data-ttu-id="35f57-178">**Свяжитесь с нами**</span><span class="sxs-lookup"><span data-stu-id="35f57-178">**Contact us**</span></span>|<span data-ttu-id="35f57-179">**Описание**</span><span class="sxs-lookup"><span data-stu-id="35f57-179">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="35f57-180">**Какое вам решение необходимо?**</span><span class="sxs-lookup"><span data-stu-id="35f57-180">**What cloud adoption content do you need?**</span></span> <br/> |<span data-ttu-id="35f57-p105">Мы создаем контент для решений, которые охватывают несколько продуктов и служб Майкрософт. Сообщите нам, что вы думаете о наших межсерверных решениях, или укажите интересующие вас решения, написав по адресу [MODAcontent@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20).</span><span class="sxs-lookup"><span data-stu-id="35f57-p105">We are creating content for cloud adoption that spans multiple Microsoft cloud platforms and services. Let us know what you think about our cloud adoption content, or ask for specific content by sending email to [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20).  </span></span><br/> |
|<span data-ttu-id="35f57-183">**Присоединяйтесь к обсуждению решений**</span><span class="sxs-lookup"><span data-stu-id="35f57-183">**Join the cloud adoption discussion**</span></span> <br/> |<span data-ttu-id="35f57-p106">Если вы являетесь отношусь решения на основе облака, рассмотрите возможность присоединения облачных внедрения Advisory платы (CAAB) для подключения с более крупный, живые сообщества разработчиков содержимого, ИТ-специалистов и клиентов по всему миру из Microsoft. Чтобы присоединиться к, добавьте себя в качестве члена [пространства CAAB (облако внедрения Advisory Доска)](https://aka.ms/caab) Технический сообщества Microsoft и отправьте быстрого электронной почты в [CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!). Любой пользователь может читать контент, связанный с сообщества [CAAB блога](https://blogs.technet.com/b/solutions_advisory_board/). Тем не менее члены CAAB получать приглашения на закрытый семинары, описывающие внедрения новых облачных ресурсов и решения.</span><span class="sxs-lookup"><span data-stu-id="35f57-p106">If you are passionate about cloud-based solutions, consider joining the Cloud Adoption Advisory Board (CAAB) to connect with a larger, vibrant community of Microsoft content developers, industry professionals, and customers from around the globe. To join, add yourself as a member of the [CAAB (Cloud Adoption Advisory Board) space](https://aka.ms/caab) of the Microsoft Tech Community and send us a quick email at [CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!). Anyone can read community-related content on the [CAAB blog](https://blogs.technet.com/b/solutions_advisory_board/). However, CAAB members get invitations to private webinars that describe new cloud adoption resources and solutions.  </span></span><br/> |
|<span data-ttu-id="35f57-187">**Скачать изображения, которые вы видите здесь**</span><span class="sxs-lookup"><span data-stu-id="35f57-187">**Get the art you see here**</span></span> <br/> |<span data-ttu-id="35f57-p107">Если вы хотите редактирования копию картинка, отображаемые в этой статье, мы будем рады отправить вам. Отправить по электронной почте запроса, включая URL-адреса и заголовка картинка, чтобы [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20).</span><span class="sxs-lookup"><span data-stu-id="35f57-p107">If you want an editable copy of the art you see in this article, we'll be glad to send it to you. Email your request, including the URL and title of the art, to [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20).  </span></span><br/> |
   
## <a name="see-also"></a><span data-ttu-id="35f57-190">See Also</span><span class="sxs-lookup"><span data-stu-id="35f57-190">See Also</span></span>

<span data-ttu-id="35f57-191"><a name="ADD_TLGs"> </a></span><span class="sxs-lookup"><span data-stu-id="35f57-191"></span></span>

[<span data-ttu-id="35f57-192">Освоение облака и гибридные решения</span><span class="sxs-lookup"><span data-stu-id="35f57-192">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
  
[<span data-ttu-id="35f57-193">Ресурсы для администраторов, посвященные архитектуре Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="35f57-193">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)
  
[<span data-ttu-id="35f57-194">Архитектурные модели для SharePoint, Exchange, Skype для бизнеса и Lync</span><span class="sxs-lookup"><span data-stu-id="35f57-194">Architectural models for SharePoint, Exchange, Skype for Business, and Lync</span></span>](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[<span data-ttu-id="35f57-195">Гибридные решения</span><span class="sxs-lookup"><span data-stu-id="35f57-195">Hybrid solutions</span></span>](hybrid-solutions.md)


