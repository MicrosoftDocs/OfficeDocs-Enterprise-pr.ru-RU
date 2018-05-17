---
title: Синхронизация каталогов для среды разработки и тестирования Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/04/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: e6b27e25-74ae-4b54-9421-c8e911aef543
description: Сводка. Настройте синхронизацию каталогов для среды разработки и тестирования Office 365.
ms.openlocfilehash: 209b41e4d695a753867d989b8f27b96618a81303
ms.sourcegitcommit: 75842294e1ba7973728e984f5654a85d5d6172cf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2018
---
# <a name="directory-synchronization-for-your-office-365-devtest-environment"></a><span data-ttu-id="8a780-103">Синхронизация каталогов для среды разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="8a780-103">Summary: Configure directory synchronization for your Office 365 dev/test environment.</span></span>

 <span data-ttu-id="8a780-104">**Сводка.** Настройте синхронизацию каталогов для среды разработки и тестирования Office 365.</span><span class="sxs-lookup"><span data-stu-id="8a780-104">**Summary:** Configure directory synchronization for your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="8a780-p101">Во многих организациях используют Azure AD Connect и синхронизацию каталогов, чтобы синхронизировать набор учетных записей в локальном лесу Windows Server Active Directory (AD) с учетными записями в Office 365. В этой статье описано, как добавить синхронизацию каталогов с синхронизацией хэша паролей в среду тестирования и разработки Office 365, в результате чего получается следующая конфигурация.</span><span class="sxs-lookup"><span data-stu-id="8a780-p101">Many organizations use Azure AD Connect and directory synchronization (DirSync) to synchronize the set of accounts in their on-premises Windows Server Active Directory (AD) forest to the set of accounts in Office 365. This article describes how you can add DirSync with password synchronization to the Office 365 dev/test environment, resulting in the following configuration.</span></span>
  
![Среда разработки и тестирования Office 365 с синхронизацией каталогов](images/be5b37b0-f832-4878-b153-436c31546e21.png)
  
<span data-ttu-id="8a780-108">Конфигурация состоит из следующих компонентов:</span><span class="sxs-lookup"><span data-stu-id="8a780-108">This configuration consists of:</span></span> 
  
- <span data-ttu-id="8a780-109">Пробная подписка Office 365 E5, которая действительна в течение 30 дней с момента создания.</span><span class="sxs-lookup"><span data-stu-id="8a780-109">An Office 365 E5 Trial Subscription, which expires 30 days from when you create it.</span></span>
- <span data-ttu-id="8a780-p102">Упрощенная интрасеть организации, подключенная к Интернету и состоящая из трех виртуальных машин в подсети виртуальной сети Azure (DC1, APP1 и CLIENT1). Azure AD Connect работает на компьютере APP1 для синхронизации домена Windows Server AD с Office 365.</span><span class="sxs-lookup"><span data-stu-id="8a780-p102">A simplified organization intranet connected to the Internet, consisting of three virtual machines on a subnet of an Azure virtual network (DC1, APP1, and CLIENT1). Azure AD Connect runs on APP1 to synchronize the Windows Server AD domain to Office 365.</span></span>
    
<span data-ttu-id="8a780-112">Процесс настройки этой среды разработки и тестирования состоит из двух указанных ниже основных этапов.</span><span class="sxs-lookup"><span data-stu-id="8a780-112">There are two phases to setting up this dev/test environment:</span></span>
  
1. <span data-ttu-id="8a780-113">Создание среды разработки и тестирования Office 365 (виртуальных машин DC1, APP1 и CLIENT1 в виртуальной сети Azure с пробной подпиской Office 365 E5).</span><span class="sxs-lookup"><span data-stu-id="8a780-113">Create the Office 365 dev/test environment (the DC1, APP1, and CLIENT1 virtual machines in an Azure virtual network with an Office 365 E5 trial subscription).</span></span>
2. <span data-ttu-id="8a780-114">Установка и настройка Azure AD Connect на виртуальной машине APP1.</span><span class="sxs-lookup"><span data-stu-id="8a780-114">Install and configure Azure AD Connect on APP1.</span></span>
    
> [!TIP]
> <span data-ttu-id="8a780-115">Щелкните [здесь](http://aka.ms/catlgstack), чтобы просмотреть схему всех статей, относящихся к руководствам по лаборатории тестирования в One Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="8a780-115">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-create-an-office-365-devtest-environment"></a><span data-ttu-id="8a780-116">Этап 1. Создание среды разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="8a780-116">Phase 1: Create an Office 365 dev/test environment</span></span>

<span data-ttu-id="8a780-p103">Следуйте инструкциям, приведенным на этапах 1, 2 и 3 статьи [Среда разработки и тестирования Office 365](office-365-dev-test-environment.md). Ниже показана итоговая конфигурация.</span><span class="sxs-lookup"><span data-stu-id="8a780-p103">Follow the instructions in phases 1, 2, and 3 of the Create an Office 365 Dev/Test Environment article. Here is the resulting configuration.</span></span>
  
![Среда разработки и тестирования Office 365](images/48fb91aa-09b0-4020-a496-a8253920c45d.png)
  
<span data-ttu-id="8a780-120">Конфигурация состоит из следующих компонентов:</span><span class="sxs-lookup"><span data-stu-id="8a780-120">This configuration consists of:</span></span> 
  
- <span data-ttu-id="8a780-121">Пробная подписка на Office 365 E5.</span><span class="sxs-lookup"><span data-stu-id="8a780-121">An Office 365 E5 Trial Subscription.</span></span>
- <span data-ttu-id="8a780-122">Упрощенная интрасеть организации, подключенная к Интернету и состоящая из виртуальных машин DC1, APP1 и CLIENT1 в подсети, входящей в виртуальную сеть Azure.</span><span class="sxs-lookup"><span data-stu-id="8a780-122">A simplified organization intranet connected to the Internet, consisting of the DC1, APP1, and CLIENT1 virtual machines on a subnet of an Azure virtual network.</span></span>
    
## <a name="phase-2-install-azure-ad-connect-on-app1"></a><span data-ttu-id="8a780-123">Этап 2. Установка Azure AD Connect на компьютере APP1</span><span class="sxs-lookup"><span data-stu-id="8a780-123">Phase 2: Install Azure AD Connect on APP1</span></span>

<span data-ttu-id="8a780-p104">После установки и настройки Azure AD Connect синхронизирует набор учетных записей на домене Windows Server AD CORP с учетными записями в пробной подписке Office 365. Описанная ниже процедура поможет вам установить средство Azure AD Connect на компьютере APP1 и убедиться, что оно работает.</span><span class="sxs-lookup"><span data-stu-id="8a780-p104">Once installed and configured, Azure AD Connect synchronizes the set of accounts in the CORP Windows Server AD domain with the set of accounts in your Office 365 trial subscription. The following procedure steps you through installing Azure AD Connect on APP1 and verifying that it works.</span></span>
  
### <a name="install-and-configure-azure-ad-connect-on-app1"></a><span data-ttu-id="8a780-126">Установка и настройка Azure AD Connect на виртуальной машине APP1</span><span class="sxs-lookup"><span data-stu-id="8a780-126">Install  and configure Azure AD Connect on APP1</span></span>

1. <span data-ttu-id="8a780-127">Откройте [портал Azure](https://portal.azure.com) и подключитесь к виртуальной машине APP1, используя учетную запись CORP\\User1.</span><span class="sxs-lookup"><span data-stu-id="8a780-127">From the [Azure portalhttps://portal.azure.com](https://portal.azure.com), connect to APP1 with the CORP\User1 account.</span></span>
    
2. <span data-ttu-id="8a780-128">На виртуальной машине APP1 откройте командную строку Windows PowerShell с правами администратора и выполните следующие команды:</span><span class="sxs-lookup"><span data-stu-id="8a780-128">From APP1, open an administrator-level Windows PowerShell command prompt, and then run these commands:</span></span>
    
  ```
  Set-ItemProperty -Path "HKLM:\SOFTWARE\Microsoft\Active Setup\Installed Components\{A509B1A7-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
Set-ItemProperty -Path "HKLM:\SOFTWARE\Microsoft\Active Setup\Installed Components\{A509B1A8-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
Stop-Process -Name Explorer -Force

  ```

3. <span data-ttu-id="8a780-129">На панели задач выберите **Internet Explorer** и перейдите по адресу [https://aka.ms/aadconnect](https://aka.ms/aadconnect).</span><span class="sxs-lookup"><span data-stu-id="8a780-129">From the task bar, click **Internet Explorer** and go to [https://aka.ms/aadconnect](https://aka.ms/aadconnect).</span></span>
    
4. <span data-ttu-id="8a780-130">На странице Microsoft Azure Active Directory Connect нажмите **Скачать**, а затем **Запустить**.</span><span class="sxs-lookup"><span data-stu-id="8a780-130">On the Microsoft Azure Active Directory Connect page, click **Download**, and then click **Run**.</span></span>
    
5. <span data-ttu-id="8a780-131">На странице **Добро пожаловать в Azure AD Connect** установите флажок **Принимаю** и нажмите кнопку **Продолжить**.</span><span class="sxs-lookup"><span data-stu-id="8a780-131">On the **Welcome to Azure AD Connect** page, click **I agree**, and then click **Continue.**</span></span>
    
6. <span data-ttu-id="8a780-132">На странице **Стандартные параметры** выберите **Использовать стандартные параметры**.</span><span class="sxs-lookup"><span data-stu-id="8a780-132">On the **Express Settings** page, click  **Use express settings**.</span></span>
    
7. <span data-ttu-id="8a780-133">На странице **Подключение к Azure AD** введите имя своей учетной записи глобального администратора в поле **Имя пользователя**, введите пароль в поле **Пароль** и нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="8a780-133">On the **Connect to Azure AD** page, type your global administrator account name in **Username,** type its password in **Password**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="8a780-134">На странице **Подключение к AD DS** введите **CORP\\User1** в поле **Имя пользователя** и пароль в поле **Пароль**, а затем нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="8a780-134">On the Connect to AD DS page, type CORP\User1 in Username, type its password in Password, and then click Next.</span></span>
    
9. <span data-ttu-id="8a780-135">На странице **Настройка входа в Azure AD** нажмите **Продолжить без проверенных доменов**, а затем нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="8a780-135">On the **Azure AD sign-in configuration** page, click **Continue without any verified domains**, and then click **Next**.</span></span>
    
10. <span data-ttu-id="8a780-136">На странице **Готово к настройке** нажмите **Установить**.</span><span class="sxs-lookup"><span data-stu-id="8a780-136">On the **Ready to configure** page, click **Install**.</span></span>
    
11. <span data-ttu-id="8a780-137">На странице **Настройка завершена** нажмите **Выход**.</span><span class="sxs-lookup"><span data-stu-id="8a780-137">On the **Configuration complete** page, click **Exit**.</span></span>
    
12. <span data-ttu-id="8a780-138">В Internet Explorer перейдите на портал Office 365 ([https://portal.office.com](https://portal.office.com)) и войдите на странице пробной подписки на Office 365, используя учетную запись глобального администратора.</span><span class="sxs-lookup"><span data-stu-id="8a780-138">Go to the Office 365 portal (https://portal.office.com) and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
13. <span data-ttu-id="8a780-139">На главной странице портала нажмите **Администратор**.</span><span class="sxs-lookup"><span data-stu-id="8a780-139">From the main portal page, click **Admin**.</span></span>
    
14. <span data-ttu-id="8a780-140">На панели навигации слева выберите **Пользователи > Активные пользователи**.</span><span class="sxs-lookup"><span data-stu-id="8a780-140">In the left navigation, click **Users > Active users**.</span></span>
    
    <span data-ttu-id="8a780-p105">Обратите внимание на учетную запись **User1**. Эта учетная запись из домена Windows Server AD CORP и доказывает, что синхронизация каталогов сработала.</span><span class="sxs-lookup"><span data-stu-id="8a780-p105">Note the account named **User1**. This account is from the CORP Windows Server AD domain and is proof that DirSync has worked.</span></span>
    
15. <span data-ttu-id="8a780-p106">Выберите учетную запись **User1**. Нажмите кнопку **Изменить** для лицензий на продукты.</span><span class="sxs-lookup"><span data-stu-id="8a780-p106">Click the **User1** account. For product licenses, click **Edit**.</span></span>
    
16. <span data-ttu-id="8a780-p107">На панели **Лицензии на продукты** выберите страну и переведите переключатель **Office 365 корпоративный E5** в положение **Вкл.** Нажмите **Сохранить** в нижней части страницы, а затем **Закрыть**.</span><span class="sxs-lookup"><span data-stu-id="8a780-p107">In **Product licenses**, select your country, and then click the **Off** control for **Office 365 Enterprise E5** (switching it to **On**). Click **Save** at the bottom of the page, and then click **Close**.</span></span>
    
<span data-ttu-id="8a780-147">Ниже показана итоговая конфигурация.</span><span class="sxs-lookup"><span data-stu-id="8a780-147">This is the resulting configuration.</span></span>
  
![Среда разработки и тестирования Office 365 с синхронизацией каталогов](images/be5b37b0-f832-4878-b153-436c31546e21.png)
  
<span data-ttu-id="8a780-149">Конфигурация состоит из следующих компонентов:</span><span class="sxs-lookup"><span data-stu-id="8a780-149">This configuration consists of:</span></span> 
  
- <span data-ttu-id="8a780-150">Пробная подписка на Office 365 E5.</span><span class="sxs-lookup"><span data-stu-id="8a780-150">An Office 365 E5 Trial Subscription.</span></span>
- <span data-ttu-id="8a780-p108">Упрощенная интрасеть организации, подключенная к Интернету и состоящая из виртуальных машин DC1, APP1 и CLIENT1 в подсети, входящей в виртуальную сеть Azure. Azure AD Connect работает на компьютере APP1 для синхронизации домена Windows Server AD CORP с Office 365 каждые 30 минут.</span><span class="sxs-lookup"><span data-stu-id="8a780-p108">A simplified organization intranet connected to the Internet, consisting of the DC1, APP1, and CLIENT1 virtual machines on a subnet of an Azure virtual network. Azure AD Connect runs on APP1 to synchronize the CORP Windows Server AD domain to Office 365 every 30 minutes.</span></span>
    
## <a name="next-step"></a><span data-ttu-id="8a780-153">Следующий шаг</span><span class="sxs-lookup"><span data-stu-id="8a780-153">Next step</span></span>

<span data-ttu-id="8a780-154">Когда вы будете готовы развернуть синхронизацию каталогов для своей организации, обратитесь к [этой статье](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md).</span><span class="sxs-lookup"><span data-stu-id="8a780-154">When you are ready to deploy directory synchronization for your organization, see [Deploy Office 365 directory synchronization in Microsoft Azure](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8a780-155">См. также</span><span class="sxs-lookup"><span data-stu-id="8a780-155">See Also</span></span>

<span data-ttu-id="8a780-156">[Руководства по лаборатории тестирования для облачных решений](cloud-adoption-test-lab-guides-tlgs.md)
[Базовая среда разработки и тестирования](base-configuration-dev-test-environment.md)
[Среда разработки и тестирования Office 365](office-365-dev-test-environment.md)
[Cloud App Security для среды разработки и тестирования Office 365](cloud-app-security-for-your-office-365-dev-test-environment.md)
[Advanced Threat Protection для среды разработки и тестирования Office 365](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
[Освоение облака и гибридные решения](cloud-adoption-and-hybrid-solutions.md)</span><span class="sxs-lookup"><span data-stu-id="8a780-156">[Cloud adoption Test Lab Guides (TLGs)](cloud-adoption-test-lab-guides-tlgs.md)
[Base Configuration dev/test environment](base-configuration-dev-test-environment.md)
[Office 365 dev/test environment](office-365-dev-test-environment.md)
[Cloud App Security for your Office 365 dev/test environment](cloud-app-security-for-your-office-365-dev-test-environment.md)
[Advanced Threat Protection for your Office 365 dev/test environment](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
[Cloud adoption and hybrid solutions](cloud-adoption-and-hybrid-solutions.md)</span></span>




