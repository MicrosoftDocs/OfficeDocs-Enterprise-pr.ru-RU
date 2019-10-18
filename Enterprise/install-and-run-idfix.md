---
title: Скачивание и запуск инструмента Office 365 IdFix
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
description: В статье описывается как скачать и запустить инструмент Office 365 IdFix, чтобы очистить доменные службы Active Directory (AD DS) перед их синхронизацией с Office 365.
ms.openlocfilehash: 4a402cf245ebd20fbc5846908d521469ebfb90c1
ms.sourcegitcommit: 10ae1163f8443c53f19dfad6b7c2b2bb952bf759
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/28/2019
ms.locfileid: "34490760"
---
# <a name="download-and-run-the-office-365-idfix-tool"></a><span data-ttu-id="ce3bb-103">Скачивание и запуск инструмента Office 365 IdFix</span><span class="sxs-lookup"><span data-stu-id="ce3bb-103">Install and run the Office 365 IdFix tool</span></span>


<span data-ttu-id="ce3bb-104">IdFix определяет в домене AD DS (доменные службы Active Directory) ошибки, например повторения или ошибки форматирования, перед выполнением синхронизации с Office 365.</span><span class="sxs-lookup"><span data-stu-id="ce3bb-104">IdFix identifies errors such as duplicates and formatting problems in your Active Directory Domain Services (AD DS) domain before you synchronize to Office 365.</span></span> 
  
<span data-ttu-id="ce3bb-105">Для успешного завершения этой задачи требуются навыки работы с объектами пользователей, групп и контактов в AD DS.</span><span class="sxs-lookup"><span data-stu-id="ce3bb-105">To finish this task successfully, you should be comfortable working with user, group, and contact objects in AD DS.</span></span>
  
<span data-ttu-id="ce3bb-106">Если вы не можете выполнить эту задачу, существует еще несколько способов.</span><span class="sxs-lookup"><span data-stu-id="ce3bb-106">If you can't complete this task, there are a couple of other things you can do.</span></span> <span data-ttu-id="ce3bb-107">Они могут быть проще, но при этом могут занимать больше времени или иметь другие недостатки.</span><span class="sxs-lookup"><span data-stu-id="ce3bb-107">These methods might be easier, but they might also take longer or have other drawbacks.</span></span> <span data-ttu-id="ce3bb-108">Они указаны ниже.</span><span class="sxs-lookup"><span data-stu-id="ce3bb-108">They are:</span></span>
  
- <span data-ttu-id="ce3bb-109">**Запуск синхронизации каталога без запуска IdFix**</span><span class="sxs-lookup"><span data-stu-id="ce3bb-109">**Run directory synchronization without running IdFix**</span></span> 

  <span data-ttu-id="ce3bb-110">Вы можете синхронизировать свой каталог, не используя инструмент IdFix, однако мы не рекомендуем этого делать.</span><span class="sxs-lookup"><span data-stu-id="ce3bb-110">You can synchronize your directory without using the IdFix tool, but we don't recommend it.</span></span> <span data-ttu-id="ce3bb-111">Исправление ошибок перед синхронизацией требует меньше времени и часто обеспечивает более плавный переход к облаку.</span><span class="sxs-lookup"><span data-stu-id="ce3bb-111">Fixing errors before you synchronize takes less time and often provides a smoother transition to the cloud.</span></span> 

- <span data-ttu-id="ce3bb-112">**Использование услуг консультанта**</span><span class="sxs-lookup"><span data-stu-id="ce3bb-112">**Hire a consultant**</span></span> 

  <span data-ttu-id="ce3bb-113">Благодаря помощи экспертов можно быстро подготовить пользователей к работе и синхронизировать каталог.</span><span class="sxs-lookup"><span data-stu-id="ce3bb-113">Getting expert help can get your users up and running quickly and your directory synchronized.</span></span> 
    
## <a name="what-you-need-to-run-idfix"></a><span data-ttu-id="ce3bb-114">Что необходимо для запуска IdFix</span><span class="sxs-lookup"><span data-stu-id="ce3bb-114">What you need to run IdFix</span></span>

<span data-ttu-id="ce3bb-115">Самый простой способ запустить IdFix — скачать его на компьютер, подключенный к вашему домену AD DS.</span><span class="sxs-lookup"><span data-stu-id="ce3bb-115">The easiest way to get IdFix up and running is to download it onto a computer that is joined to your AD DS domain.</span></span> <span data-ttu-id="ce3bb-116">При желании вы можете запустить его на контроллере домена, но это необязательно.</span><span class="sxs-lookup"><span data-stu-id="ce3bb-116">You can run it on the domain controller if you want, but it's not necessary.</span></span>
  
### <a name="idfix-hardware-requirements"></a><span data-ttu-id="ce3bb-117">Требования IdFix к оборудованию</span><span class="sxs-lookup"><span data-stu-id="ce3bb-117">IdFix hardware requirements</span></span>

<span data-ttu-id="ce3bb-118">Компьютер, на который скачивается IdFix, должен соответствовать следующим минимальным требованиям к оборудованию:</span><span class="sxs-lookup"><span data-stu-id="ce3bb-118">The computer where you download IdFix needs to meet these minimum hardware requirements:</span></span>
  
- <span data-ttu-id="ce3bb-119">4 ГБ ОЗУ</span><span class="sxs-lookup"><span data-stu-id="ce3bb-119">4 GB RAM</span></span>
- <span data-ttu-id="ce3bb-120">2 ГБ места на жестком диске</span><span class="sxs-lookup"><span data-stu-id="ce3bb-120">At least 11 GB of hard disk space.</span></span>
   
### <a name="idfix-software-requirements"></a><span data-ttu-id="ce3bb-121">Требования IdFix к программному обеспечению</span><span class="sxs-lookup"><span data-stu-id="ce3bb-121">IdFix software requirements</span></span>

<span data-ttu-id="ce3bb-122">Компьютер, на который скачивается IdFix, должен быть присоединен к домену AD DS, пользователей из которого вы хотите синхронизировать с Office 365.</span><span class="sxs-lookup"><span data-stu-id="ce3bb-122">The computer where you download IdFix needs to be joined to the same AD DS domain from which you want to synchronize users to Office 365.</span></span> 

<span data-ttu-id="ce3bb-123">Кроме того, на компьютере должна быть установлена платформа .NET Framework 4.0.</span><span class="sxs-lookup"><span data-stu-id="ce3bb-123">The computer also needs to have .NET Framework 4.0 installed.</span></span> <span data-ttu-id="ce3bb-124">Если вы работаете под управлением Windows Server 2008, вероятно, что платформа .NET Framework уже установлена.</span><span class="sxs-lookup"><span data-stu-id="ce3bb-124">If you are running Windows Server 2008 or later, the .NET Framework is probably already installed.</span></span> <span data-ttu-id="ce3bb-125">Если нет, вы можете [скачать ее из Центра загрузки](https://go.microsoft.com/fwlink/p/?LinkId=400475) или с помощью Центра обновления Windows.</span><span class="sxs-lookup"><span data-stu-id="ce3bb-125">If not, you can [download .NET 4.0 from the download center](https://go.microsoft.com/fwlink/p/?LinkId=400475) or with Windows Update.</span></span> 
  
### <a name="idfix-permissions-requirements"></a><span data-ttu-id="ce3bb-126">Требования к разрешениям IdFix</span><span class="sxs-lookup"><span data-stu-id="ce3bb-126">IdFix permissions requirements</span></span>

<span data-ttu-id="ce3bb-127">Учетная запись пользователя, применяемая для запуска IdFix, должна иметь права на чтение и запись в домене AD DS.</span><span class="sxs-lookup"><span data-stu-id="ce3bb-127">The user account that you use to run IdFix must have read and write access to the AD DS domain.</span></span>
  
<span data-ttu-id="ce3bb-128">Если вы не уверены, что ваша учетная запись пользователя удовлетворяет данным требованиям, и не знаете как это проверить, вы все равно можете скачать и запустить IdFix.</span><span class="sxs-lookup"><span data-stu-id="ce3bb-128">If you aren't sure if your user account meets these requirements, and you're not sure how to check, you can still download and run IdFix.</span></span> <span data-ttu-id="ce3bb-129">Если ваша учетная запись пользователя не имеет соответствующих разрешений, при попытке запуска IdFix отобразится сообщение об ошибке.</span><span class="sxs-lookup"><span data-stu-id="ce3bb-129">If your user account doesn't have the right permissions, IdFix will simply display an error when you try to run it.</span></span>
  
## <a name="download-and-extract-idfix"></a><span data-ttu-id="ce3bb-130">Скачивание и извлечение IdFix</span><span class="sxs-lookup"><span data-stu-id="ce3bb-130">Download and extract IdFix</span></span>

<span data-ttu-id="ce3bb-131">Следуйте данным инструкциям.</span><span class="sxs-lookup"><span data-stu-id="ce3bb-131">Follow these instructions.</span></span> 
  
1. <span data-ttu-id="ce3bb-132">Войдите на компьютер, где нужно запустить инструмент IdFix.</span><span class="sxs-lookup"><span data-stu-id="ce3bb-132">Sign in to the computer where you want to run the IdFix tool.</span></span>
    
2. <span data-ttu-id="ce3bb-133">Перейдите на страницу Центра загрузки Майкрософт для [средства исправления ошибок синхронизации каталога IdFix](https://go.microsoft.com/fwlink/?linkid=867219).</span><span class="sxs-lookup"><span data-stu-id="ce3bb-133">Go to the Microsoft download site for the [IdFix DirSync Error Remediation Tool](https://go.microsoft.com/fwlink/?linkid=867219).</span></span>
    
3. <span data-ttu-id="ce3bb-134">Скачайте и откройте ZIP-файл.</span><span class="sxs-lookup"><span data-stu-id="ce3bb-134">Download and open the zip file.</span></span>
    
3. <span data-ttu-id="ce3bb-135">В папке **IdFix** выберите команду **Извлечь**, а затем — **Извлечь все**.</span><span class="sxs-lookup"><span data-stu-id="ce3bb-135">In the **IdFix** window, choose **Extract**, and then **Extract all**.</span></span> <span data-ttu-id="ce3bb-136">По умолчанию IdFix извлекается в папку `C:\Users\<your user name>\Documents\IdFix`.</span><span class="sxs-lookup"><span data-stu-id="ce3bb-136">By default, IdFix is extracted to `C:\Users\<your user name>\Documents\IdFix`.</span></span> 
    
6. <span data-ttu-id="ce3bb-137">Нажмите **Извлечь**.</span><span class="sxs-lookup"><span data-stu-id="ce3bb-137">Choose **Extract**.</span></span>

<span data-ttu-id="ce3bb-138">Эти действия были выполнены в Internet Explorer на сервере под управлением Windows Server 2016.</span><span class="sxs-lookup"><span data-stu-id="ce3bb-138">These instructions were done with Internet Explorer on a server running Windows Server 2016.</span></span> <span data-ttu-id="ce3bb-139">Если вы используете другую версию Windows или другой браузер, ваши действия могут отличаться.</span><span class="sxs-lookup"><span data-stu-id="ce3bb-139">If you're using a different version of Windows or a different browser, your steps might vary.</span></span>
    
## <a name="run-the-idfix-tool"></a><span data-ttu-id="ce3bb-140">Запуск IdFix</span><span class="sxs-lookup"><span data-stu-id="ce3bb-140">Run the tool.</span></span>

<span data-ttu-id="ce3bb-141">После скачивания и извлечения IdFix запустите его для поиска проблем в домене AD DS.</span><span class="sxs-lookup"><span data-stu-id="ce3bb-141">After you download and extract IdFix, run it to search for problems in your AD DS domain.</span></span>
  
1. <span data-ttu-id="ce3bb-142">С помощью учетной записи, имеющей право чтения и записи в домене AD DS, войдите на компьютер, куда скачан IdFix.</span><span class="sxs-lookup"><span data-stu-id="ce3bb-142">Using an account that has read/write access to your AD DS domain, sign in to the computer where you downloaded IdFix.</span></span>
    
2. <span data-ttu-id="ce3bb-143">В проводнике перейдите в папку, куда извлечен IdFix.</span><span class="sxs-lookup"><span data-stu-id="ce3bb-143">In File Explorer, go to the location where you extracted IdFix.</span></span> <span data-ttu-id="ce3bb-144">Если во время установки была выбрана папка по умолчанию, перейдите в `C:\Users\<your user name>\Documents\IdFix`.</span><span class="sxs-lookup"><span data-stu-id="ce3bb-144">If you chose the default folder during extraction, go to `C:\Users\<your user name>\Documents\IdFix`.</span></span> 
    
3. <span data-ttu-id="ce3bb-145">Дважды щелкните **IdFix.exe**.</span><span class="sxs-lookup"><span data-stu-id="ce3bb-145">Double-click **IdFix.exe**.</span></span> 
  
4. <span data-ttu-id="ce3bb-146">По умолчанию для тестирования записей в каталоге IdFix использует многопользовательский набор правил.</span><span class="sxs-lookup"><span data-stu-id="ce3bb-146">By default, IdFix uses the Multi-Tenant rule set to test the entries in your directory.</span></span> <span data-ttu-id="ce3bb-147">Он подходит для большинства клиентов Office 365.</span><span class="sxs-lookup"><span data-stu-id="ce3bb-147">This is the right rule set for most Office 365 customers.</span></span> <span data-ttu-id="ce3bb-148">Но если вы являетесь пользователем выделенной службы Office 365 или пользователем ITAR (подчиняющимся Правилам международной торговли оружием), вы можете настроить IdFix для использования набора правил "Выделенный".</span><span class="sxs-lookup"><span data-stu-id="ce3bb-148">However, if you are an Office 365 Dedicated or International Traffic in Arms Regulations (ITAR)) customer, you can configure IdFix to use the Dedicated rule set instead.</span></span> <span data-ttu-id="ce3bb-149">Если вы не знаете, к какому типу пользователей относитесь, пропустите этот шаг.</span><span class="sxs-lookup"><span data-stu-id="ce3bb-149">If you aren’t sure what type of customer you are, you can safely disregard this note.</span></span> <span data-ttu-id="ce3bb-150">Чтобы изменить набор правил на "Выделенный", щелкните значок шестеренки в строке меню и выберите **Выделенный**.</span><span class="sxs-lookup"><span data-stu-id="ce3bb-150">To set the rule set to Dedicated, click the gear icon in the menu bar, and then choose **Dedicated**.</span></span>
    
5. <span data-ttu-id="ce3bb-151">Выберите **Запрос**.</span><span class="sxs-lookup"><span data-stu-id="ce3bb-151">Choose **Query**.</span></span>
    
    ![Выбор запросов в IdFix.](media/a07a7aa7-d0ac-4817-8757-946019813a57.JPG)
  
6. <span data-ttu-id="ce3bb-153">По умолчанию IdFix выполняет поиск ошибок по всему каталогу.</span><span class="sxs-lookup"><span data-stu-id="ce3bb-153">By default, IdFix searches the entire directory for errors.</span></span>
    
    <span data-ttu-id="ce3bb-154">В зависимости от размера каталога выполнение запроса может занять некоторое время.</span><span class="sxs-lookup"><span data-stu-id="ce3bb-154">Depending on the size of your directory, running the query can take a while.</span></span> <span data-ttu-id="ce3bb-155">Отслеживать ход выполнения можно в нижней части главного окна программы.</span><span class="sxs-lookup"><span data-stu-id="ce3bb-155">You can watch the progress at the bottom of the tool's main window.</span></span> <span data-ttu-id="ce3bb-156">Если вы нажмете кнопку **Отмена**, потребуется начать все с начала.</span><span class="sxs-lookup"><span data-stu-id="ce3bb-156">If you click **Cancel**, you'll need to restart from the beginning.</span></span>
  
7. <span data-ttu-id="ce3bb-157">После выполнения запроса, вы можете синхронизировать свой каталог, если не обнаружено никаких ошибок.</span><span class="sxs-lookup"><span data-stu-id="ce3bb-157">After IdFix completes the query, you can synchronize your directory if there are no errors.</span></span> <span data-ttu-id="ce3bb-158">Если в каталоге есть ошибки, рекомендуется исправить их до синхронизации.</span><span class="sxs-lookup"><span data-stu-id="ce3bb-158">If there are errors in your directory, it is recommended that you fix them before you synchronize.</span></span> <span data-ttu-id="ce3bb-159">Дополнительные сведения см. в статье [Подготовка атрибутов каталога к синхронизации с Office 365](prepare-directory-attributes-for-synch-with-idfix.md).</span><span class="sxs-lookup"><span data-stu-id="ce3bb-159">See [prepare directory attributes for synchronization with Office 365](prepare-directory-attributes-for-synch-with-idfix.md) for more information.</span></span>
    
    <span data-ttu-id="ce3bb-160">Хотя исправлять ошибки перед синхронизацией необязательно, мы настоятельно рекомендуем по крайней мере просмотреть все ошибки, обнаруженные IdFix.</span><span class="sxs-lookup"><span data-stu-id="ce3bb-160">While it is not mandatory to fix the errors before you synchronize, we strongly recommend that you at least review all the errors returned by IdFix.</span></span>
    
    <span data-ttu-id="ce3bb-161">Каждая ошибка отображается в отдельной строке в главном окне инструмента.</span><span class="sxs-lookup"><span data-stu-id="ce3bb-161">Each error is displayed in a separate row in the tool's main window .</span></span> 
    
8. <span data-ttu-id="ce3bb-162">Если вы согласны с изменениями, предлагаемыми в столбце **ОБНОВЛЕНИЕ**, в столбце **ДЕЙСТВИЕ** выберите, что средство IdFix должно сделать для их применения, и нажмите кнопку **Применить**.</span><span class="sxs-lookup"><span data-stu-id="ce3bb-162">If you agree with the suggested change in the **UPDATE** column, in the **ACTION** column select what you want IdFix to do to implement the change and then click **Apply**.</span></span> <span data-ttu-id="ce3bb-163">При нажатии кнопки **Применить** инструмент вносит изменения в каталог.</span><span class="sxs-lookup"><span data-stu-id="ce3bb-163">When you click **Apply**, the tool makes the changes in the directory.</span></span>
    
    <span data-ttu-id="ce3bb-164">Не нужно нажимать кнопку **Применить** после каждого обновления.</span><span class="sxs-lookup"><span data-stu-id="ce3bb-164">You don't have to click **Apply** after each update.</span></span> <span data-ttu-id="ce3bb-165">Вы можете исправить несколько ошибок, а потом нажать кнопку **Применить**, чтобы IdFix изменил их все за один раз.</span><span class="sxs-lookup"><span data-stu-id="ce3bb-165">Instead, you can fix several errors before you click **Apply** and IdFix will change them all at the same time.</span></span> <span data-ttu-id="ce3bb-166">Вы можете сортировать ошибки по типу, щелкая **ОШИБКА** в верхней части столбца, в котором перечислены типы ошибок.</span><span class="sxs-lookup"><span data-stu-id="ce3bb-166">You can sort the errors by error type by clicking **ERROR** at the top of the column that lists the error types.</span></span> 
    
    <span data-ttu-id="ce3bb-167">Первый способ — исправить все ошибки одного типа. Например, сначала исправить все повторяющиеся записи и применить их.</span><span class="sxs-lookup"><span data-stu-id="ce3bb-167">One strategy is to fix all the errors of the same type; for example, fix all the duplicates first, and apply them.</span></span> <span data-ttu-id="ce3bb-168">После этого можно исправить ошибки форматирования символов и так далее.</span><span class="sxs-lookup"><span data-stu-id="ce3bb-168">Next, fix the character format errors, and so on.</span></span> <span data-ttu-id="ce3bb-169">Каждый раз после применения изменений IdFix создает отдельный файл журнала, который можно использовать для отмены изменений в случае ошибки.</span><span class="sxs-lookup"><span data-stu-id="ce3bb-169">Each time you apply the changes, the IdFix tool creates a separate log file that you can use to undo your changes in case you make a mistake.</span></span> <span data-ttu-id="ce3bb-170">[Журнал транзакций](idfix-transaction-log.md) хранится в папке, в которую извлечен IdFix (по умолчанию это _C:\Users\<ваше имя пользователя>\Documents\IdFix_).</span><span class="sxs-lookup"><span data-stu-id="ce3bb-170">The [transaction log](idfix-transaction-log.md) is stored in the folder where you extracted IdFix, which is _C:\Users\<your user name>\Documents\IdFix_ by default.</span></span> 
    
    ![Исправление ошибок в IdFix.](media/5f051070-652c-4be7-98bf-312295e32371.png)
  
9. <span data-ttu-id="ce3bb-172">После внесения в каталог всех изменений запустите IdFix еще раз, чтобы убедиться, что эти исправления не приводят к появлению новых ошибок.</span><span class="sxs-lookup"><span data-stu-id="ce3bb-172">After all of your changes are made to the directory, run IdFix again to ensure that the fixes you made didn't introduce new errors.</span></span> <span data-ttu-id="ce3bb-173">Можно повторять эти действия столько раз, сколько необходимо.</span><span class="sxs-lookup"><span data-stu-id="ce3bb-173">You can repeat these steps for as many sites as you want to join to the hub.</span></span> <span data-ttu-id="ce3bb-174">Рекомендуется выполнить этот процесс перед синхронизацией несколько раз.</span><span class="sxs-lookup"><span data-stu-id="ce3bb-174">It's a good idea to go through the process a few times before you synchronize.</span></span>
    
## <a name="additional-resources-on-idfix"></a><span data-ttu-id="ce3bb-175">Дополнительные ресурсы по IdFix</span><span class="sxs-lookup"><span data-stu-id="ce3bb-175">Additional resources on IdFix</span></span> 

- [<span data-ttu-id="ce3bb-176">Исключаемые и поддерживаемые объекты и атрибуты IdFix</span><span class="sxs-lookup"><span data-stu-id="ce3bb-176">IdFix excluded and supported objects and attributes</span></span>](idfix-excluded-and-supported-objects-and-attributes.md)  
- [<span data-ttu-id="ce3bb-177">Журнал транзакций Office 365 IdFix</span><span class="sxs-lookup"><span data-stu-id="ce3bb-177">Reference: Office 365 IdFix transaction log</span></span>](idfix-transaction-log.md)
    
## <a name="video-training"></a><span data-ttu-id="ce3bb-178">Обучающее видео</span><span class="sxs-lookup"><span data-stu-id="ce3bb-178">Video training</span></span>

<span data-ttu-id="ce3bb-179">Дополнительные сведения см. в статье [Установка и использование инструмента IdFix](https://support.office.com/article/install-and-use-the-idfix-tool-4d81d73c-f172-4fd5-8542-f601c0c96aa9?ui=en-US&rs=en-US&ad=US). Обучающее видео предоставлено платформой LinkedIn Learning.</span><span class="sxs-lookup"><span data-stu-id="ce3bb-179">For more information, see the lesson [Install and use the IdFix tool](https://support.office.com/article/install-and-use-the-idfix-tool-4d81d73c-f172-4fd5-8542-f601c0c96aa9?ui=en-US&rs=en-US&ad=US), brought to you by LinkedIn Learning.</span></span>
  

