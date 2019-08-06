---
title: Загрузка и запуск средства IdFix для Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: get-started-article
f1_keywords:
- O365E_HRCSetupAADConnectIDFixLM617036
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
ms.assetid: f4bd2439-3e41-4169-99f6-3fabdfa326ac
description: Сведения о том, как скачать и запустить средство Office 365 IdFix для очистки доменных служб Active Directory (AD DS) перед их синхронизацией с Office 365.
ms.openlocfilehash: 4a402cf245ebd20fbc5846908d521469ebfb90c1
ms.sourcegitcommit: 10ae1163f8443c53f19dfad6b7c2b2bb952bf759
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/28/2019
ms.locfileid: "34490760"
---
# <a name="download-and-run-the-office-365-idfix-tool"></a><span data-ttu-id="287f4-103">Загрузка и запуск средства IdFix для Office 365</span><span class="sxs-lookup"><span data-stu-id="287f4-103">Download and run the Office 365 IdFix tool</span></span>


<span data-ttu-id="287f4-104">IdFix определяет ошибки, такие как дублирование и форматирование в домене доменных служб Active Directory (AD DS) перед синхронизацией с Office 365.</span><span class="sxs-lookup"><span data-stu-id="287f4-104">IdFix identifies errors such as duplicates and formatting problems in your Active Directory Domain Services (AD DS) domain before you synchronize to Office 365.</span></span> 
  
<span data-ttu-id="287f4-105">Для успешного выполнения этой задачи вы должны быть готовы к работе с объектами пользователей, групп и контактов в доменных СЛУЖБах Active Directory.</span><span class="sxs-lookup"><span data-stu-id="287f4-105">To finish this task successfully, you should be comfortable working with user, group, and contact objects in AD DS.</span></span>
  
<span data-ttu-id="287f4-106">Если вы не можете выполнить эту задачу, можно выполнить несколько других действий.</span><span class="sxs-lookup"><span data-stu-id="287f4-106">If you can't complete this task, there are a couple of other things you can do.</span></span> <span data-ttu-id="287f4-107">Эти методы могут быть проще, но они также могут занимать больше или иметь другие недостатки.</span><span class="sxs-lookup"><span data-stu-id="287f4-107">These methods might be easier, but they might also take longer or have other drawbacks.</span></span> <span data-ttu-id="287f4-108">Они указаны ниже.</span><span class="sxs-lookup"><span data-stu-id="287f4-108">They are:</span></span>
  
- <span data-ttu-id="287f4-109">**Запуск синхронизации службы каталогов без запуска IdFix**</span><span class="sxs-lookup"><span data-stu-id="287f4-109">**Run directory synchronization without running IdFix**</span></span> 

  <span data-ttu-id="287f4-110">Вы можете синхронизировать каталог без использования средства IdFix, но мы не рекомендуем использовать его.</span><span class="sxs-lookup"><span data-stu-id="287f4-110">You can synchronize your directory without using the IdFix tool, but we don't recommend it.</span></span> <span data-ttu-id="287f4-111">Устранение ошибок до синхронизации занимает меньше времени и часто приводит к более гладкому переходу в облако.</span><span class="sxs-lookup"><span data-stu-id="287f4-111">Fixing errors before you synchronize takes less time and often provides a smoother transition to the cloud.</span></span> 

- <span data-ttu-id="287f4-112">**Прием на работу консультанта**</span><span class="sxs-lookup"><span data-stu-id="287f4-112">**Hire a consultant**</span></span> 

  <span data-ttu-id="287f4-113">С помощью экспертной справки пользователи могут быстро и эффективно работать со службой каталогов.</span><span class="sxs-lookup"><span data-stu-id="287f4-113">Getting expert help can get your users up and running quickly and your directory synchronized.</span></span> 
    
## <a name="what-you-need-to-run-idfix"></a><span data-ttu-id="287f4-114">Что нужно для запуска IdFix</span><span class="sxs-lookup"><span data-stu-id="287f4-114">What you need to run IdFix</span></span>

<span data-ttu-id="287f4-115">Самый простой способ получить IdFix и выполнить его загрузку на компьютер, присоединенный к домену доменных служб Active Directory.</span><span class="sxs-lookup"><span data-stu-id="287f4-115">The easiest way to get IdFix up and running is to download it onto a computer that is joined to your AD DS domain.</span></span> <span data-ttu-id="287f4-116">Его можно запустить на контроллере домена, если это необходимо, но это необязательно.</span><span class="sxs-lookup"><span data-stu-id="287f4-116">You can run it on the domain controller if you want, but it's not necessary.</span></span>
  
### <a name="idfix-hardware-requirements"></a><span data-ttu-id="287f4-117">Требования к оборудованию IdFix</span><span class="sxs-lookup"><span data-stu-id="287f4-117">IdFix hardware requirements</span></span>

<span data-ttu-id="287f4-118">Компьютер, на котором необходимо скачать IdFix, должен соответствовать следующим минимальным требованиям к оборудованию:</span><span class="sxs-lookup"><span data-stu-id="287f4-118">The computer where you download IdFix needs to meet these minimum hardware requirements:</span></span>
  
- <span data-ttu-id="287f4-119">4 ГБ ОЗУ</span><span class="sxs-lookup"><span data-stu-id="287f4-119">4 GB RAM</span></span>
- <span data-ttu-id="287f4-120">2 ГБ свободного места на жестком диске</span><span class="sxs-lookup"><span data-stu-id="287f4-120">2 GB of hard disk space</span></span>
   
### <a name="idfix-software-requirements"></a><span data-ttu-id="287f4-121">Требования к программному обеспечению IdFix</span><span class="sxs-lookup"><span data-stu-id="287f4-121">IdFix software requirements</span></span>

<span data-ttu-id="287f4-122">Компьютер, на котором необходимо скачать IdFix, необходимо присоединить к тому же домену доменных служб Active Directory, с которого вы хотите синхронизировать пользователей с Office 365.</span><span class="sxs-lookup"><span data-stu-id="287f4-122">The computer where you download IdFix needs to be joined to the same AD DS domain from which you want to synchronize users to Office 365.</span></span> 

<span data-ttu-id="287f4-123">На компьютере также должен быть установлен .NET Framework 4,0.</span><span class="sxs-lookup"><span data-stu-id="287f4-123">The computer also needs to have .NET Framework 4.0 installed.</span></span> <span data-ttu-id="287f4-124">Если вы используете Windows Server 2008 или более поздней версии, то, возможно, уже установлена платформа .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="287f4-124">If you are running Windows Server 2008 or later, the .NET Framework is probably already installed.</span></span> <span data-ttu-id="287f4-125">В противном случае вы можете [скачать .net 4,0 из центра загрузки](https://go.microsoft.com/fwlink/p/?LinkId=400475) или с помощью центра обновления Windows.</span><span class="sxs-lookup"><span data-stu-id="287f4-125">If not, you can [download .NET 4.0 from the download center](https://go.microsoft.com/fwlink/p/?LinkId=400475) or with Windows Update.</span></span> 
  
### <a name="idfix-permissions-requirements"></a><span data-ttu-id="287f4-126">Требования к разрешениям IdFix</span><span class="sxs-lookup"><span data-stu-id="287f4-126">IdFix permissions requirements</span></span>

<span data-ttu-id="287f4-127">Учетная запись пользователя, используемая для запуска IdFix, должна иметь доступ на чтение и запись к домену доменных служб Active Directory.</span><span class="sxs-lookup"><span data-stu-id="287f4-127">The user account that you use to run IdFix must have read and write access to the AD DS domain.</span></span>
  
<span data-ttu-id="287f4-128">Если вы не уверены, что ваша учетная запись пользователя соответствует этим требованиям, и вы не знаете, как проверить, вы по-прежнему можете скачать и запустить IdFix.</span><span class="sxs-lookup"><span data-stu-id="287f4-128">If you aren't sure if your user account meets these requirements, and you're not sure how to check, you can still download and run IdFix.</span></span> <span data-ttu-id="287f4-129">Если у вашей учетной записи пользователя нет разрешений, IdFix просто выводит сообщение об ошибке при попытке запустить ее.</span><span class="sxs-lookup"><span data-stu-id="287f4-129">If your user account doesn't have the right permissions, IdFix will simply display an error when you try to run it.</span></span>
  
## <a name="download-and-extract-idfix"></a><span data-ttu-id="287f4-130">Скачайте и извлеките IdFix</span><span class="sxs-lookup"><span data-stu-id="287f4-130">Download and extract IdFix</span></span>

<span data-ttu-id="287f4-131">Выполните указанные ниже действия.</span><span class="sxs-lookup"><span data-stu-id="287f4-131">Follow these instructions.</span></span> 
  
1. <span data-ttu-id="287f4-132">Войдите на компьютер, на котором необходимо запустить средство IdFix.</span><span class="sxs-lookup"><span data-stu-id="287f4-132">Sign in to the computer where you want to run the IdFix tool.</span></span>
    
2. <span data-ttu-id="287f4-133">Перейдите на сайт центра загрузки Майкрософт для [средства устранения ошибок IdFix DirSync](https://go.microsoft.com/fwlink/?linkid=867219).</span><span class="sxs-lookup"><span data-stu-id="287f4-133">Go to the Microsoft download site for the [IdFix DirSync Error Remediation Tool](https://go.microsoft.com/fwlink/?linkid=867219).</span></span>
    
3. <span data-ttu-id="287f4-134">Скачайте и откройте Zip-файл.</span><span class="sxs-lookup"><span data-stu-id="287f4-134">Download and open the zip file.</span></span>
    
3. <span data-ttu-id="287f4-135">В окне **IdFix** выберите **извлечь**, а затем **извлечь все**.</span><span class="sxs-lookup"><span data-stu-id="287f4-135">In the **IdFix** window, choose **Extract**, and then **Extract all**.</span></span> <span data-ttu-id="287f4-136">По умолчанию IdFix извлекается в `C:\Users\<your user name>\Documents\IdFix`.</span><span class="sxs-lookup"><span data-stu-id="287f4-136">By default, IdFix is extracted to `C:\Users\<your user name>\Documents\IdFix`.</span></span> 
    
6. <span data-ttu-id="287f4-137">Выберите **извлечь**.</span><span class="sxs-lookup"><span data-stu-id="287f4-137">Choose **Extract**.</span></span>

<span data-ttu-id="287f4-138">Эти инструкции выполнялись с помощью Internet Explorer на сервере под управлением Windows Server 2016.</span><span class="sxs-lookup"><span data-stu-id="287f4-138">These instructions were done with Internet Explorer on a server running Windows Server 2016.</span></span> <span data-ttu-id="287f4-139">Если вы используете другую версию Windows или другой браузер, ваши действия могут различаться.</span><span class="sxs-lookup"><span data-stu-id="287f4-139">If you're using a different version of Windows or a different browser, your steps might vary.</span></span>
    
## <a name="run-the-idfix-tool"></a><span data-ttu-id="287f4-140">Запуск средства IdFix</span><span class="sxs-lookup"><span data-stu-id="287f4-140">Run the IdFix tool</span></span>

<span data-ttu-id="287f4-141">После загрузки и извлечения IdFix запустите его, чтобы найти проблемы в домене доменных служб Active Directory.</span><span class="sxs-lookup"><span data-stu-id="287f4-141">After you download and extract IdFix, run it to search for problems in your AD DS domain.</span></span>
  
1. <span data-ttu-id="287f4-142">Используя учетную запись с правами на чтение и запись для домена доменных служб Active Directory, войдите на компьютер, на котором вы скачали IdFix.</span><span class="sxs-lookup"><span data-stu-id="287f4-142">Using an account that has read/write access to your AD DS domain, sign in to the computer where you downloaded IdFix.</span></span>
    
2. <span data-ttu-id="287f4-143">В проводнике перейдите в папку, в которую вы извлекли файл IdFix.</span><span class="sxs-lookup"><span data-stu-id="287f4-143">In File Explorer, go to the location where you extracted IdFix.</span></span> <span data-ttu-id="287f4-144">Если во время извлечения выбрана папка по умолчанию, `C:\Users\<your user name>\Documents\IdFix`перейдите на страницу.</span><span class="sxs-lookup"><span data-stu-id="287f4-144">If you chose the default folder during extraction, go to `C:\Users\<your user name>\Documents\IdFix`.</span></span> 
    
3. <span data-ttu-id="287f4-145">Дважды щелкните **IdFix. exe**.</span><span class="sxs-lookup"><span data-stu-id="287f4-145">Double-click **IdFix.exe**.</span></span> 
  
4. <span data-ttu-id="287f4-146">По умолчанию IdFix использует набор правил для нескольких клиентов для проверки записей в каталоге.</span><span class="sxs-lookup"><span data-stu-id="287f4-146">By default, IdFix uses the Multi-Tenant rule set to test the entries in your directory.</span></span> <span data-ttu-id="287f4-147">Это правильный набор правил для большинства клиентов Office 365.</span><span class="sxs-lookup"><span data-stu-id="287f4-147">This is the right rule set for most Office 365 customers.</span></span> <span data-ttu-id="287f4-148">Тем не менее, если вы используете выделенный или международный трафик Office 365 (ITAR)), можно настроить IdFix для использования выделенного набора правил.</span><span class="sxs-lookup"><span data-stu-id="287f4-148">However, if you are an Office 365 Dedicated or International Traffic in Arms Regulations (ITAR)) customer, you can configure IdFix to use the Dedicated rule set instead.</span></span> <span data-ttu-id="287f4-149">Если вы не знаете, какой тип клиента вы знаете, вы можете спокойно пропустить этот шаг.</span><span class="sxs-lookup"><span data-stu-id="287f4-149">If you aren't sure what type of customer you are, you can safely skip this step.</span></span> <span data-ttu-id="287f4-150">Чтобы задать для правила значение выделенный, щелкните значок шестеренки в строке меню, а затем выберите **выделенный**.</span><span class="sxs-lookup"><span data-stu-id="287f4-150">To set the rule set to Dedicated, click the gear icon in the menu bar, and then choose **Dedicated**.</span></span>
    
5. <span data-ttu-id="287f4-151">Нажмите кнопку **запрос**.</span><span class="sxs-lookup"><span data-stu-id="287f4-151">Choose **Query**.</span></span>
    
    ![Выберите запрос в IdFix.](media/a07a7aa7-d0ac-4817-8757-946019813a57.JPG)
  
6. <span data-ttu-id="287f4-153">По умолчанию IdFix выполняет поиск ошибок во всем каталоге.</span><span class="sxs-lookup"><span data-stu-id="287f4-153">By default, IdFix searches the entire directory for errors.</span></span>
    
    <span data-ttu-id="287f4-154">В зависимости от размера каталога выполнение запроса может занять некоторое время.</span><span class="sxs-lookup"><span data-stu-id="287f4-154">Depending on the size of your directory, running the query can take a while.</span></span> <span data-ttu-id="287f4-155">Вы можете наблюдать за ходом выполнения в нижней части главного окна средства.</span><span class="sxs-lookup"><span data-stu-id="287f4-155">You can watch the progress at the bottom of the tool's main window.</span></span> <span data-ttu-id="287f4-156">Если вы нажимаете кнопку **Отмена**, вам потребуется перезапустить его с самого начала.</span><span class="sxs-lookup"><span data-stu-id="287f4-156">If you click **Cancel**, you'll need to restart from the beginning.</span></span>
  
7. <span data-ttu-id="287f4-157">После завершения запроса IdFix можно выполнить синхронизацию каталога, если ошибок нет.</span><span class="sxs-lookup"><span data-stu-id="287f4-157">After IdFix completes the query, you can synchronize your directory if there are no errors.</span></span> <span data-ttu-id="287f4-158">Если в каталоге есть ошибки, рекомендуется исправить их перед синхронизацией.</span><span class="sxs-lookup"><span data-stu-id="287f4-158">If there are errors in your directory, it is recommended that you fix them before you synchronize.</span></span> <span data-ttu-id="287f4-159">Более подробную информацию можно узнать [в статье Подготовка атрибутов каталога для синхронизации с Office 365](prepare-directory-attributes-for-synch-with-idfix.md) .</span><span class="sxs-lookup"><span data-stu-id="287f4-159">See [prepare directory attributes for synchronization with Office 365](prepare-directory-attributes-for-synch-with-idfix.md) for more information.</span></span>
    
    <span data-ttu-id="287f4-160">Пока не обязательно исправлять ошибки перед синхронизацией, настоятельно рекомендуется по крайней мере проверить все ошибки, возвращенные в IdFix.</span><span class="sxs-lookup"><span data-stu-id="287f4-160">While it is not mandatory to fix the errors before you synchronize, we strongly recommend that you at least review all the errors returned by IdFix.</span></span>
    
    <span data-ttu-id="287f4-161">Каждая ошибка отображается в отдельной строке в главном окне средства.</span><span class="sxs-lookup"><span data-stu-id="287f4-161">Each error is displayed in a separate row in the tool's main window .</span></span> 
    
8. <span data-ttu-id="287f4-162">Если вы согласны с предложенным изменением в столбце " **Обновление** ", в столбце **действие** выберите действия, которые необходимо IdFix для реализации изменения, а затем нажмите кнопку **Применить**.</span><span class="sxs-lookup"><span data-stu-id="287f4-162">If you agree with the suggested change in the **UPDATE** column, in the **ACTION** column select what you want IdFix to do to implement the change and then click **Apply**.</span></span> <span data-ttu-id="287f4-163">При нажатии кнопки **Применить**средство вносит изменения в каталог.</span><span class="sxs-lookup"><span data-stu-id="287f4-163">When you click **Apply**, the tool makes the changes in the directory.</span></span>
    
    <span data-ttu-id="287f4-164">После каждого обновления нет необходимости нажимать кнопку **Применить** .</span><span class="sxs-lookup"><span data-stu-id="287f4-164">You don't have to click **Apply** after each update.</span></span> <span data-ttu-id="287f4-165">Вместо этого можно устранить несколько ошибок, прежде чем нажать кнопку **Применить** и IdFix будет изменять их все одновременно.</span><span class="sxs-lookup"><span data-stu-id="287f4-165">Instead, you can fix several errors before you click **Apply** and IdFix will change them all at the same time.</span></span> <span data-ttu-id="287f4-166">Можно отсортировать ошибки по типу ошибки, щелкнув **Ошибка** в верхней части столбца со списком типов ошибок.</span><span class="sxs-lookup"><span data-stu-id="287f4-166">You can sort the errors by error type by clicking **ERROR** at the top of the column that lists the error types.</span></span> 
    
    <span data-ttu-id="287f4-167">Одной из стратегий является устранение всех ошибок того же типа; Например, сначала исправьте все дубликаты, а затем примените их.</span><span class="sxs-lookup"><span data-stu-id="287f4-167">One strategy is to fix all the errors of the same type; for example, fix all the duplicates first, and apply them.</span></span> <span data-ttu-id="287f4-168">Затем исправьте ошибки форматов символов и т. д.</span><span class="sxs-lookup"><span data-stu-id="287f4-168">Next, fix the character format errors, and so on.</span></span> <span data-ttu-id="287f4-169">Каждый раз при применении изменений средство IdFix создает отдельный файл журнала, который можно использовать для отмены изменений в случае ошибки.</span><span class="sxs-lookup"><span data-stu-id="287f4-169">Each time you apply the changes, the IdFix tool creates a separate log file that you can use to undo your changes in case you make a mistake.</span></span> <span data-ttu-id="287f4-170">[Журнал транзакций](idfix-transaction-log.md) хранится в папке, в которую вы извлекли IdFix, _C:\Users\<имя пользователя> \документс\идфикс_ по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="287f4-170">The [transaction log](idfix-transaction-log.md) is stored in the folder where you extracted IdFix, which is _C:\Users\<your user name>\Documents\IdFix_ by default.</span></span> 
    
    ![Ошибки устранение в IdFix.](media/5f051070-652c-4be7-98bf-312295e32371.png)
  
9. <span data-ttu-id="287f4-172">После внесения всех изменений в каталог запустите IdFix еще раз, чтобы убедиться в том, что внесенные вами исправления не познакомятся с новыми ошибками.</span><span class="sxs-lookup"><span data-stu-id="287f4-172">After all of your changes are made to the directory, run IdFix again to ensure that the fixes you made didn't introduce new errors.</span></span> <span data-ttu-id="287f4-173">Эти действия можно повторять столько раз, сколько необходимо.</span><span class="sxs-lookup"><span data-stu-id="287f4-173">You can repeat these steps as many times as you need to.</span></span> <span data-ttu-id="287f4-174">Перед синхронизацией рекомендуется пройти процесс несколько раз.</span><span class="sxs-lookup"><span data-stu-id="287f4-174">It's a good idea to go through the process a few times before you synchronize.</span></span>
    
## <a name="additional-resources-on-idfix"></a><span data-ttu-id="287f4-175">Дополнительные материалы по IdFix</span><span class="sxs-lookup"><span data-stu-id="287f4-175">Additional resources on IdFix</span></span> 

- [<span data-ttu-id="287f4-176">Исключаемые и поддерживаемые объекты и атрибуты IdFix</span><span class="sxs-lookup"><span data-stu-id="287f4-176">IdFix excluded and supported objects and attributes</span></span>](idfix-excluded-and-supported-objects-and-attributes.md)  
- [<span data-ttu-id="287f4-177">Журнал транзакций Office 365 IdFix</span><span class="sxs-lookup"><span data-stu-id="287f4-177">Office 365 IdFix transaction log</span></span>](idfix-transaction-log.md)
    
## <a name="video-training"></a><span data-ttu-id="287f4-178">Обучающие видео</span><span class="sxs-lookup"><span data-stu-id="287f4-178">Video training</span></span>

<span data-ttu-id="287f4-179">Дополнительные сведения можно найти в разделе [Установка и использование средства IdFix](https://support.office.com/article/install-and-use-the-idfix-tool-4d81d73c-f172-4fd5-8542-f601c0c96aa9?ui=en-US&rs=en-US&ad=US), предоставленного программой LinkedIn Learning.</span><span class="sxs-lookup"><span data-stu-id="287f4-179">For more information, see the lesson [Install and use the IdFix tool](https://support.office.com/article/install-and-use-the-idfix-tool-4d81d73c-f172-4fd5-8542-f601c0c96aa9?ui=en-US&rs=en-US&ad=US), brought to you by LinkedIn Learning.</span></span>
  

