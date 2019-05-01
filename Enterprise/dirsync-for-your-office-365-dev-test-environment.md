---
title: Синхронизация каталогов для среды разработки и тестирования Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/18/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: e6b27e25-74ae-4b54-9421-c8e911aef543
description: Сводка. Настройте синхронизацию каталогов для среды разработки и тестирования Office 365.
ms.openlocfilehash: 74457cca2d199fe7bfa8839908b0f6a413890f8a
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487333"
---
# <a name="directory-synchronization-for-your-office-365-devtest-environment"></a><span data-ttu-id="988b7-103">Синхронизация каталогов для среды разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="988b7-103">Directory synchronization for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="988b7-104">**Сводка.** Настройте синхронизацию каталогов для среды разработки и тестирования Office 365.</span><span class="sxs-lookup"><span data-stu-id="988b7-104">**Summary:** Configure directory synchronization for your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="988b7-p101">Во многих организациях используют Azure AD Connect и синхронизацию каталогов, чтобы синхронизировать набор учетных записей в локальном лесу доменных служб Active Directory (AD DS) с учетными записями в Office 365. В этой статье описано, как добавить синхронизацию каталогов с синхронизацией хэша паролей в среду тестирования и разработки Office 365, в результате чего получается следующая конфигурация.</span><span class="sxs-lookup"><span data-stu-id="988b7-p101">Many organizations use Azure AD Connect and directory synchronization to synchronize the set of accounts in their on-premises Active Directory Domain Services (AD DS) forest to the set of accounts in Office 365. This article describes how you can add directory synchronization with password hash synchronization to the Office 365 dev/test environment, resulting in the following configuration.</span></span>
  
![Среда разработки и тестирования Office 365 с синхронизацией каталогов](media/be5b37b0-f832-4878-b153-436c31546e21.png)
  
<span data-ttu-id="988b7-108">Конфигурация состоит из следующих компонентов:</span><span class="sxs-lookup"><span data-stu-id="988b7-108">This configuration consists of:</span></span> 
  
- <span data-ttu-id="988b7-109">Пробная подписка Office 365 E5, которая действительна в течение 30 дней с момента создания.</span><span class="sxs-lookup"><span data-stu-id="988b7-109">An Office 365 E5 Trial Subscription, which expires 30 days from when you create it.</span></span>
- <span data-ttu-id="988b7-p102">Упрощенная интрасеть организации, подключенная к Интернету и состоящая из трех виртуальных машин в подсети виртуальной сети Azure (DC1, APP1 и CLIENT1). Azure AD Connect работает на компьютере APP1 для синхронизации домена AD DS с Office 365.</span><span class="sxs-lookup"><span data-stu-id="988b7-p102">A simplified organization intranet connected to the Internet, consisting of three virtual machines on a subnet of an Azure virtual network (DC1, APP1, and CLIENT1). Azure AD Connect runs on APP1 to synchronize the AD DS domain to Office 365.</span></span>
    
<span data-ttu-id="988b7-112">Процесс настройки этой среды разработки и тестирования состоит из двух указанных ниже основных этапов.</span><span class="sxs-lookup"><span data-stu-id="988b7-112">There are two phases to setting up this dev/test environment:</span></span>
  
1. <span data-ttu-id="988b7-113">Создание среды разработки и тестирования Office 365 (виртуальных машин DC1, APP1 и CLIENT1 в виртуальной сети Azure с пробной подпиской Office 365 E5).</span><span class="sxs-lookup"><span data-stu-id="988b7-113">Create the Office 365 dev/test environment (the DC1, APP1, and CLIENT1 virtual machines in an Azure virtual network with an Office 365 E5 trial subscription).</span></span>
2. <span data-ttu-id="988b7-114">Установка и настройка Azure AD Connect на виртуальной машине APP1.</span><span class="sxs-lookup"><span data-stu-id="988b7-114">Install and configure Azure AD Connect on APP1.</span></span>
    
> [!TIP]
> <span data-ttu-id="988b7-115">Щелкните [здесь](http://aka.ms/catlgstack), чтобы просмотреть схему всех статей, относящихся к руководствам по лаборатории тестирования в Office 365.</span><span class="sxs-lookup"><span data-stu-id="988b7-115">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the Office 365 Test Lab Guide stack.</span></span>
  
## <a name="phase-1-create-an-office-365-devtest-environment"></a><span data-ttu-id="988b7-116">Этап 1. Создание среды разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="988b7-116">Phase 1: Create an Office 365 dev/test environment</span></span>

<span data-ttu-id="988b7-p103">Следуйте инструкциям, приведенным на этапах 1, 2 и 3 статьи [Среда разработки и тестирования Office 365](office-365-dev-test-environment.md). Ниже показана итоговая конфигурация.</span><span class="sxs-lookup"><span data-stu-id="988b7-p103">Follow the instructions in phases 1, 2, and 3 of the [Office 365 dev/test environment](office-365-dev-test-environment.md) article. Here is the resulting configuration.</span></span>
  
![Среда разработки и тестирования Office 365](media/48fb91aa-09b0-4020-a496-a8253920c45d.png)
  
<span data-ttu-id="988b7-120">Конфигурация состоит из следующих компонентов:</span><span class="sxs-lookup"><span data-stu-id="988b7-120">This configuration consists of:</span></span> 
  
- <span data-ttu-id="988b7-121">Пробная подписка на Office 365 E5.</span><span class="sxs-lookup"><span data-stu-id="988b7-121">An Office 365 E5 Trial Subscription.</span></span>
- <span data-ttu-id="988b7-122">Упрощенная интрасеть организации, подключенная к Интернету и состоящая из виртуальных машин DC1, APP1 и CLIENT1 в подсети, входящей в виртуальную сеть Azure.</span><span class="sxs-lookup"><span data-stu-id="988b7-122">A simplified organization intranet connected to the Internet, consisting of the DC1, APP1, and CLIENT1 virtual machines on a subnet of an Azure virtual network.</span></span>
    
## <a name="phase-2-install-azure-ad-connect-on-app1"></a><span data-ttu-id="988b7-123">Этап 2. Установка Azure AD Connect на компьютере APP1</span><span class="sxs-lookup"><span data-stu-id="988b7-123">Phase 2: Install Azure AD Connect on APP1</span></span>

<span data-ttu-id="988b7-p104">После установки и настройки Azure AD Connect синхронизирует набор учетных записей на домене AD DS CORP с учетными записями в пробной подписке Office 365. Описанная ниже процедура поможет вам установить средство Azure AD Connect на компьютере APP1 и проверить, что оно работает.</span><span class="sxs-lookup"><span data-stu-id="988b7-p104">Once installed and configured, Azure AD Connect synchronizes the set of accounts in the CORP AD DS domain with the set of accounts in your Office 365 trial subscription. The following procedure steps you through installing Azure AD Connect on APP1 and checking that it works.</span></span>
  
### <a name="install-and-configure-azure-ad-connect-on-app1"></a><span data-ttu-id="988b7-126">Установка и настройка Azure AD Connect на APP1</span><span class="sxs-lookup"><span data-stu-id="988b7-126">Install and configure Azure AD Connect on APP1</span></span>

1. <span data-ttu-id="988b7-127">Откройте [портал Azure](https://portal.azure.com) и подключитесь к виртуальной машине APP1, используя учетную запись CORP\\User1.</span><span class="sxs-lookup"><span data-stu-id="988b7-127">From the [Azure portal](https://portal.azure.com), connect to APP1 with the CORP\\User1 account.</span></span>
    
2. <span data-ttu-id="988b7-128">На виртуальной машине APP1 откройте командную строку Windows PowerShell с правами администратора и выполните следующие команды:</span><span class="sxs-lookup"><span data-stu-id="988b7-128">From APP1, open an administrator-level Windows PowerShell command prompt, and then run these commands:</span></span>
    
  ```
  Set-ItemProperty -Path "HKLM:\SOFTWARE\Microsoft\Active Setup\Installed Components\{A509B1A7-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
Set-ItemProperty -Path "HKLM:\SOFTWARE\Microsoft\Active Setup\Installed Components\{A509B1A8-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
Stop-Process -Name Explorer -Force

  ```

3. <span data-ttu-id="988b7-129">На панели задач выберите **Internet Explorer** и перейдите по адресу [https://aka.ms/aadconnect](https://aka.ms/aadconnect).</span><span class="sxs-lookup"><span data-stu-id="988b7-129">From the task bar, click **Internet Explorer** and go to [https://aka.ms/aadconnect](https://aka.ms/aadconnect).</span></span>
    
4. <span data-ttu-id="988b7-130">На странице Microsoft Azure Active Directory Connect нажмите **Скачать**, а затем **Запустить**.</span><span class="sxs-lookup"><span data-stu-id="988b7-130">On the Microsoft Azure Active Directory Connect page, click **Download**, and then click **Run**.</span></span>
    
5. <span data-ttu-id="988b7-131">На странице **Добро пожаловать в Azure AD Connect** установите флажок **Принимаю** и нажмите кнопку **Продолжить**.</span><span class="sxs-lookup"><span data-stu-id="988b7-131">On the **Welcome to Azure AD Connect** page, click **I agree**, and then click **Continue**.</span></span>
    
6. <span data-ttu-id="988b7-132">На странице **Стандартные параметры** выберите **Использовать стандартные параметры**.</span><span class="sxs-lookup"><span data-stu-id="988b7-132">On the **Express Settings** page, click **Use express settings**.</span></span>
    
7. <span data-ttu-id="988b7-133">На странице **Подключение к Azure AD** введите имя своей учетной записи глобального администратора в поле **Имя пользователя**, введите пароль в поле **Пароль** и нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="988b7-133">On the **Connect to Azure AD** page, type your global administrator account name in **Username,** type its password in **Password**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="988b7-134">На странице **Подключение к AD DS** введите **CORP\\User1** в поле **Имя пользователя** и пароль в поле **Пароль**, а затем нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="988b7-134">On the **Connect to AD DS** page, type **CORP\\User1** in **Username,** type its password in **Password**, and then click **Next**.</span></span>
    
9. <span data-ttu-id="988b7-135">На странице **Настройка входа в Azure AD** нажмите **Продолжить без проверенных доменов**, а затем нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="988b7-135">On the **Azure AD sign-in configuration** page, click **Continue without any verified domains**, and then click **Next**.</span></span>
    
10. <span data-ttu-id="988b7-136">На странице **Готово к настройке** нажмите **Установить**.</span><span class="sxs-lookup"><span data-stu-id="988b7-136">On the **Ready to configure** page, click **Install**.</span></span>
    
11. <span data-ttu-id="988b7-137">На странице **Настройка завершена** нажмите **Выход**.</span><span class="sxs-lookup"><span data-stu-id="988b7-137">On the **Configuration complete** page, click **Exit**.</span></span>
    
12. <span data-ttu-id="988b7-138">В Internet Explorer перейдите в Центр администрирования Microsoft 365 ([https://admin.microsoft.com](https://admin.microsoft.com)) и войдите на странице пробной подписки на Office 365, используя учетную запись глобального администратора.</span><span class="sxs-lookup"><span data-stu-id="988b7-138">In Internet Explorer, go to the Microsoft 365 admin center ([https://admin.microsoft.com](https://admin.microsoft.com)) and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
13. <span data-ttu-id="988b7-139">На главной странице портала нажмите **Администрирование**.</span><span class="sxs-lookup"><span data-stu-id="988b7-139">From the main portal page, click **Admin**.</span></span>
    
14. <span data-ttu-id="988b7-140">На панели навигации слева выберите **Пользователи > Активные пользователи**.</span><span class="sxs-lookup"><span data-stu-id="988b7-140">In the left navigation, click **Users > Active users**.</span></span>
    
    <span data-ttu-id="988b7-p105">Обратите внимание на учетную запись **User1**. Эта учетная запись из домена AD DS CORP является доказательством, что синхронизация каталогов сработала.</span><span class="sxs-lookup"><span data-stu-id="988b7-p105">Note the account named **User1**. This account is from the CORP AD DS domain and is proof that directory synchronization has worked.</span></span>
    
15. <span data-ttu-id="988b7-p106">Выберите учетную запись **User1**. Нажмите кнопку **Изменить** для лицензий на продукты.</span><span class="sxs-lookup"><span data-stu-id="988b7-p106">Click the **User1** account. For product licenses, click **Edit**.</span></span>
    
16. <span data-ttu-id="988b7-p107">На панели **Лицензии на продукты** выберите страну и переведите переключатель **Office 365 корпоративный E5** в положение **Вкл.** Нажмите **Сохранить** в нижней части страницы, а затем **Закрыть**.</span><span class="sxs-lookup"><span data-stu-id="988b7-p107">In **Product licenses**, select your country, and then click the **Off** control for **Office 365 Enterprise E5** (switching it to **On**). Click **Save** at the bottom of the page, and then click **Close**.</span></span>
    
<span data-ttu-id="988b7-147">Ниже показана итоговая конфигурация.</span><span class="sxs-lookup"><span data-stu-id="988b7-147">This is the resulting configuration.</span></span>
  
![Среда разработки и тестирования Office 365 с синхронизацией каталогов](media/be5b37b0-f832-4878-b153-436c31546e21.png)
  
<span data-ttu-id="988b7-149">Конфигурация состоит из следующих компонентов:</span><span class="sxs-lookup"><span data-stu-id="988b7-149">This configuration consists of:</span></span> 
  
- <span data-ttu-id="988b7-150">Пробная подписка на Office 365 E5.</span><span class="sxs-lookup"><span data-stu-id="988b7-150">An Office 365 E5 Trial Subscription.</span></span>
- <span data-ttu-id="988b7-p108">Упрощенная интрасеть организации, подключенная к Интернету и состоящая из виртуальных машин DC1, APP1 и CLIENT1 в подсети, входящей в виртуальную сеть Azure. Azure AD Connect работает на компьютере APP1 для синхронизации домена AD DS CORP с Office 365 каждые 30 минут.</span><span class="sxs-lookup"><span data-stu-id="988b7-p108">A simplified organization intranet connected to the Internet, consisting of the DC1, APP1, and CLIENT1 virtual machines on a subnet of an Azure virtual network. Azure AD Connect runs on APP1 to synchronize the CORP AD DS domain to Office 365 every 30 minutes.</span></span>
    
## <a name="next-step"></a><span data-ttu-id="988b7-153">Следующий этап</span><span class="sxs-lookup"><span data-stu-id="988b7-153">Next Step</span></span>

<span data-ttu-id="988b7-154">Когда вы будете готовы развернуть синхронизацию каталогов для своей организации, обратитесь к статье [Развертывание службы синхронизации каталогов Office 365 в Microsoft Azure](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md).</span><span class="sxs-lookup"><span data-stu-id="988b7-154">When you are ready to deploy directory synchronization for your organization, see [Deploy Office 365 Directory Synchronization in Microsoft Azure](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="988b7-155">См. также</span><span class="sxs-lookup"><span data-stu-id="988b7-155">See Also</span></span>

[<span data-ttu-id="988b7-156">Руководства по созданию сред разработки и тестирования облачных решений</span><span class="sxs-lookup"><span data-stu-id="988b7-156">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)

[<span data-ttu-id="988b7-157">Базовая конфигурация среды разработки и тестирования</span><span class="sxs-lookup"><span data-stu-id="988b7-157">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)

[<span data-ttu-id="988b7-158">Среда разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="988b7-158">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)

[<span data-ttu-id="988b7-159">Cloud App Security для среды разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="988b7-159">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)

[<span data-ttu-id="988b7-160">Advanced Threat Protection в среде разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="988b7-160">Advanced Threat Protection for your Office 365 dev/test environment</span></span>](advanced-threat-protection-for-your-office-365-dev-test-environment.md)

[<span data-ttu-id="988b7-161">Освоение облака и гибридные решения</span><span class="sxs-lookup"><span data-stu-id="988b7-161">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)




