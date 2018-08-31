---
title: Установка и запуск инструмента Office 365 IdFix
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: get-started-article
f1_keywords:
- O365E_HRCSetupAADConnectIDFixLM617036
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
ms.assetid: f4bd2439-3e41-4169-99f6-3fabdfa326ac
description: Как установить и запустить средство Office 365 IdFix для очистки active directory перед выполнением синхронизации в Office 365.
ms.openlocfilehash: 642273c0171603d627a19273a78fe66662f4caaf
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542325"
---
# <a name="install-and-run-the-office-365-idfix-tool"></a><span data-ttu-id="10120-103">Установка и запуск инструмента Office 365 IdFix</span><span class="sxs-lookup"><span data-stu-id="10120-103">Install and run the Office 365 IdFix tool</span></span>

<span data-ttu-id="10120-104">IdFix определяет ошибки, такие как дубликаты и форматирования проблем в каталоге перед синхронизацией в Office 365.</span><span class="sxs-lookup"><span data-stu-id="10120-104">IdFix identifies errors such as duplicates and formatting problems in your directory before you synchronize to Office 365.</span></span> 
  
<span data-ttu-id="10120-105">Для успешного выполнения задачи необходимо умение свободно работать с пользователей, группы и контактных объектов в Active Directory.</span><span class="sxs-lookup"><span data-stu-id="10120-105">To finish this task successfully, you should be comfortable working with user, group, and contact objects in Active Directory.</span></span>
  
<span data-ttu-id="10120-p101">Если не удается выполнить эту задачу, есть несколько вещей, которые можно выполнить. Эти методы могут быть проще, но они также могут занимать значительно больше времени или у других недостатков. Они являются:</span><span class="sxs-lookup"><span data-stu-id="10120-p101">If you can't complete this task, there are a couple of other things you can do. These methods might be easier, but they might also take longer or have other drawbacks. They are:</span></span>
  
- <span data-ttu-id="10120-p102">**Выполнить синхронизацию каталогов без запуска IdFix.** Можно синхронизировать каталоге без запуска инструмента IdFix, но не рекомендуется. Устранение ошибок, перед выполнением синхронизации требуется меньше времени и часто содержит плавный переход в облако.</span><span class="sxs-lookup"><span data-stu-id="10120-p102">**Run directory synchronization without running IdFix.** You can synchronize your directory without running the IdFix tool, but we don't recommend it. Fixing errors before you synchronize takes less time and often provides a smoother transition to the cloud.</span></span> 
- <span data-ttu-id="10120-p103">**Наем консультанта.** Помощь эксперта позволит быстро обучить пользователей и синхронизировать ваш каталог.</span><span class="sxs-lookup"><span data-stu-id="10120-p103">**Hire a consultant.** Getting expert help can get your users up and running quickly and your directory synchronized.</span></span> 
    
## <a name="what-you-need-to-run-idfix"></a><span data-ttu-id="10120-114">Что необходимо для запуска IdFix</span><span class="sxs-lookup"><span data-stu-id="10120-114">What you need to run IdFix</span></span>

<span data-ttu-id="10120-p104">Простой способ получить IdFix регистрация и работает — это для установки на компьютер, присоединенный к домену. Если требуется, но нет необходимости можно запустить его на контроллере домена.</span><span class="sxs-lookup"><span data-stu-id="10120-p104">The easiest way to get IdFix up and running is to install it on a computer that is joined to your domain. You can run it on the domain controller if you want to, but it's not necessary.</span></span>
  
### <a name="idfix-hardware-requirements"></a><span data-ttu-id="10120-117">Требования IdFix к оборудованию</span><span class="sxs-lookup"><span data-stu-id="10120-117">IdFix hardware requirements</span></span>

<span data-ttu-id="10120-118">Компьютер, на котором установлен IdFix, должен соответствовать следующим требованиям к оборудованию:</span><span class="sxs-lookup"><span data-stu-id="10120-118">The computer where you install IdFix needs to meet these hardware requirements:</span></span>
  
- <span data-ttu-id="10120-119">4 ГБ ОЗУ (минимум).</span><span class="sxs-lookup"><span data-stu-id="10120-119">4 GB RAM (minimum)</span></span>
- <span data-ttu-id="10120-120">2 ГБ места на жестком диске (минимум).</span><span class="sxs-lookup"><span data-stu-id="10120-120">2 GB of hard disk space (minimum)</span></span>
    
### <a name="idfix-software-requirements"></a><span data-ttu-id="10120-121">Требования IdFix к программному обеспечению</span><span class="sxs-lookup"><span data-stu-id="10120-121">IdFix software requirements</span></span>

<span data-ttu-id="10120-p105">Компьютер, где устанавливается необходимо IdFix должен быть присоединен к тому же домену Active Directory, из которого нужно синхронизировать пользователей с Office 365. Компьютер должен быть установлен .NET Framework 4.0.</span><span class="sxs-lookup"><span data-stu-id="10120-p105">The computer where you install IdFix needs to needs to be joined to the same Active Directory domain from which you want to synchronize users to Office 365. The computer also needs to have .NET Framework 4.0 installed.</span></span> 
  
<span data-ttu-id="10120-p106">При запуске Windows Server 2008 или Windows Server 2012 .NET Framework, возможно, уже установлен. Если нет, вы можете [загрузить .NET 4.0 из центра загрузки](https://go.microsoft.com/fwlink/p/?LinkId=400475) или с помощью центра обновления Windows.</span><span class="sxs-lookup"><span data-stu-id="10120-p106">If you are running Windows Server 2008 or Windows Server 2012, then .NET Framework is probably already installed. If not, you can [download .NET 4.0 from the download center](https://go.microsoft.com/fwlink/p/?LinkId=400475) or by using Windows Update.</span></span> 
  
### <a name="idfix-permissions-requirements"></a><span data-ttu-id="10120-126">Требования к разрешениям IdFix</span><span class="sxs-lookup"><span data-stu-id="10120-126">IdFix permissions requirements</span></span>

<span data-ttu-id="10120-127">Учетная запись пользователя, используемая для запуска IdFix, требует права на чтение и запись в этом каталоге.</span><span class="sxs-lookup"><span data-stu-id="10120-127">The user account that you use to run IdFix needs to have read/write access to the directory.</span></span>
  
<span data-ttu-id="10120-p107">Если вы не уверены в том случае, если учетная запись пользователя соответствует этим требованиям, и вы не знаете, как проверить, по-прежнему можно установить и запустить IdFix все равно. Если учетная запись пользователя не имеет соответствующих разрешений, IdFix просто выводится сообщение об ошибке при попытке запустить его.</span><span class="sxs-lookup"><span data-stu-id="10120-p107">If you aren't sure if your user account meets these requirements, and you're not sure how to check, you can still install and run IdFix anyway. If your user account doesn't have the right permissions, IdFix will simply display an error when you try to run it.</span></span>
  
## <a name="install-idfix"></a><span data-ttu-id="10120-130">Установка IdFix</span><span class="sxs-lookup"><span data-stu-id="10120-130">Install IdFix</span></span>

<span data-ttu-id="10120-131">Чтобы установить IdFix, загрузите и распакуйте **IdFix.exe**, как это описано далее:</span><span class="sxs-lookup"><span data-stu-id="10120-131">To install IdFix, you download and unzip **IdFix.exe** as described in these steps:</span></span> 
  
1. <span data-ttu-id="10120-132">Войдите на компьютер, где вы хотите установить инструмент IdFix.</span><span class="sxs-lookup"><span data-stu-id="10120-132">Log on to the computer where you want to install the IdFix tool.</span></span>
    
2. <span data-ttu-id="10120-133">Перейдите на сайт загрузок Майкрософт со [Средством исправления ошибок IdFix DirSync](https://go.microsoft.com/fwlink/?linkid=867219).</span><span class="sxs-lookup"><span data-stu-id="10120-133">Go to the Microsoft download site for the [IdFix DirSync Error Remediation Tool](https://go.microsoft.com/fwlink/?linkid=867219).</span></span>
    
3. <span data-ttu-id="10120-134">Выберите пункт **Загрузить**.</span><span class="sxs-lookup"><span data-stu-id="10120-134">Choose **Download**.</span></span>
    
4. <span data-ttu-id="10120-135">После появления запроса выберите пункт **выполнить**.</span><span class="sxs-lookup"><span data-stu-id="10120-135">When prompted, choose **Run**.</span></span>
    
5. <span data-ttu-id="10120-p108">В диалоговом окне **Самораспаковывающийся пакет WinZip** в текстовом поле **Unzip папку** введите или выберите расположение, где необходимо установить инструмент IdFix. По умолчанию IdFix установлен в C:\Deployment средства\.</span><span class="sxs-lookup"><span data-stu-id="10120-p108">On the **WinZip Self-Extractor** dialog box, in the **Unzip to folder** text box, type or browse to the location where you want to install the IdFix tool. By default, IdFix is installed into C:\Deployment Tools\.</span></span> 
    
6. <span data-ttu-id="10120-138">Нажмите кнопку **Unzip**.</span><span class="sxs-lookup"><span data-stu-id="10120-138">Choose **Unzip**.</span></span>
    
## <a name="run-the-idfix-tool"></a><span data-ttu-id="10120-139">Запуск IdFix</span><span class="sxs-lookup"><span data-stu-id="10120-139">Run the IdFix tool</span></span>

<span data-ttu-id="10120-140">После установки IdFix запустите инструмент для поиска проблем в каталоге:</span><span class="sxs-lookup"><span data-stu-id="10120-140">After you install IdFix, run the tool to search for problems in your directory:</span></span>
  
1. <span data-ttu-id="10120-141">С помощью учетной записи, имеющей право чтения и записи в этой папке, войдите на компьютер, на котором установлен IdFix.</span><span class="sxs-lookup"><span data-stu-id="10120-141">Using an account that has read/write access to the directory, log on to the computer where you installed IdFix.</span></span>
    
2. <span data-ttu-id="10120-p109">В проводнике перейдите в местоположение, где установлен IdFix. Если во время установки была выбрана папка по умолчанию, перейдите в C:\Deployment Tools\IdFix.</span><span class="sxs-lookup"><span data-stu-id="10120-p109">In File Explorer, go to the location where you installed IdFix. If you chose the default folder during installation, go to C:\Deployment Tools\IdFix.</span></span>
    
3. <span data-ttu-id="10120-144">Дважды щелкните файл **IdFix.exe**.</span><span class="sxs-lookup"><span data-stu-id="10120-144">Double-click **IdFix.exe**.</span></span> 
    
    ![Выберите файл IdFix.exe.](media/a9387bbc-991f-41c2-a500-45e3ce574285.JPG)
  
4. <span data-ttu-id="10120-p110">По умолчанию IdFix использует правила несколькими клиентами, задайте для тестирования операций в каталоге. Это вправо набора правил для большинства клиентов Office 365. Тем не менее при наличии в Office 365 выделенных или соответствующих международным правилам ТОРГОВЛИ (International трафик в руки нормы) клиента, можно настроить IdFix для использования выделенного вместо этого набора правил. Если вы не уверены, какой тип клиента, вы являетесь, этот шаг можно пропустить безопасно. Чтобы задать правила, задайте значение выделенными, щелкните значок шестеренки в строке меню, затем выберите **выделенными**.</span><span class="sxs-lookup"><span data-stu-id="10120-p110">By default, IdFix uses the Multi-Tenant rule set to test the entries in your directory. This is the right rule set for most Office 365 customers. However, if you are an Office 365 Dedicated or ITAR (International Traffic in Arms Regulations) customer, you can configure IdFix to use the Dedicated rule set instead. If you aren't sure what type of customer you are, you can safely skip this step. To set the rule set to Dedicated, click the gear icon in the menu bar and then choose **Dedicated**.</span></span>
    
5. <span data-ttu-id="10120-151">Выберите пункт **запрос**.</span><span class="sxs-lookup"><span data-stu-id="10120-151">Choose **Query**.</span></span>
    
    ![Выбор запроса в IdFix.](media/a07a7aa7-d0ac-4817-8757-946019813a57.JPG)
  
6. <span data-ttu-id="10120-153">По умолчанию IdFix выполняет поиск ошибок по всему каталогу.</span><span class="sxs-lookup"><span data-stu-id="10120-153">By default, IdFix searches the entire directory for errors.</span></span>
    
    <span data-ttu-id="10120-p111">В зависимости от размера каталога выполнение запроса может занять некоторое время. Можно отслеживать ход выполнения в нижней части главного окна программы. Если нажать кнопку **Отмена**, то необходимо для перезапуска с самого начала.</span><span class="sxs-lookup"><span data-stu-id="10120-p111">Depending on the size of your directory, running the query can take a while. You can watch the progress at the bottom of the tool's main window. If you click **Cancel**, you'll need to restart from the beginning.</span></span>
    
    ![Количество запросов и ошибок IdFix.](media/da0198a0-7d4d-4afe-a256-e82f1330ada5.JPG)
  
7. <span data-ttu-id="10120-p112">После выполнения запроса, а также если в каталоге не обнаружено никаких ошибок, вы можете пройти дальше и синхронизировать свой каталог. Если в каталоге есть ошибки, рекомендуется исправить их до синхронизации. Для получения дополнительной информации о типах ошибок, а также рекомендаций по наилучшему способу их устранения, пройдите по ссылкам, приведенным в конце этой статьи.</span><span class="sxs-lookup"><span data-stu-id="10120-p112">After IdFix completes the query, and if there are no errors in your directory, you can go ahead and synchronize your directory. If there are errors in your directory, it is recommended that you fix them before you synchronize. If you want more specific information about types of errors and recommendations about the best way to fix each of them, see the links at the end of this topic.</span></span> 
    
    <span data-ttu-id="10120-161">Несмотря на то что исправлять ошибки, обнаруженные IdFix, необязательно, мы настоятельно рекомендуем хотя бы просмотреть их.</span><span class="sxs-lookup"><span data-stu-id="10120-161">While it is not mandatory to fix the errors before you synchronize, we strongly recommend that you at least review all the errors returned by IdFix.</span></span>
    
    <span data-ttu-id="10120-162">Каждая ошибка отображается в отдельной строке в главном окне программы.</span><span class="sxs-lookup"><span data-stu-id="10120-162">Each error is displayed in a separate row in the tool's main window .</span></span> 
    
8. <span data-ttu-id="10120-p113">Если вы согласны с изменением, предложенным в столбце **UPDATE**, выберите необходимое действие в столбце **ACTION** и нажмите кнопку **Apply** (Применить). При нажатии кнопки **Apply** (Применить) средство внесет изменения в каталог.</span><span class="sxs-lookup"><span data-stu-id="10120-p113">If you agree with the suggested change in the **UPDATE** column, in the **ACTION** column select what you want IdFix to do to implement the change and then click **Apply**. When you click **Apply**, the tool makes the changes in the directory.</span></span>
    
    <span data-ttu-id="10120-p114">Нажмите кнопку **Применить,** после каждого обновления не нужно. Вместо этого можно устранить несколько ошибок перед нажмите кнопку **Применить** и IdFix изменить их все в то же время. Можно сортировать ошибки, тип ошибки, нажав кнопку **ошибки** в верхней части столбца, где перечислены типы ошибок.</span><span class="sxs-lookup"><span data-stu-id="10120-p114">You don't have to click **Apply** after each update. Instead, you can fix several errors before you click **Apply** and IdFix will change them all at the same time. You can sort the errors by error type by clicking **ERROR** at the top of the column that lists the error types.</span></span> 
    
    <span data-ttu-id="10120-p115">Первый способ — исправить все ошибки того же типа; Например сначала исправить все дубликаты и применить их. Рассмотрим процедуру исправить ошибки формата символов и так далее. Каждый раз, применить изменения, инструмента IdFix создает отдельный файл журнала, которые можно использовать для отмены изменений в случае, если в случае ошибки. [Журнал транзакций](idfix-transaction-log.md) хранится в к папке, где установлен IdFix в.  _C:\Deployment Tools\IdFix_ по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="10120-p115">One strategy is to fix all the errors of the same type; for example, fix all the duplicates first, and apply them. Next, fix the character format errors, and so on. Each time you apply the changes, the IdFix tool creates a separate log file that you can use to undo your changes in case you make a mistake. The [transaction log](idfix-transaction-log.md) is stored in the folder that you installed IdFix in.  _C:\Deployment Tools\IdFix_ by default.</span></span> 
    
    ![Устранение ошибок в IdFix.](media/5f051070-652c-4be7-98bf-312295e32371.png)
  
9. <span data-ttu-id="10120-p116">Когда все изменения вносятся в каталог запуска IdFix еще раз, чтобы убедиться, что исправления, внесенные вами не вызовет новых ошибок. Можно повторить эти действия столько раз, сколько требуется. Рекомендуется пройти через процесс несколько раз, перед выполнением синхронизации.</span><span class="sxs-lookup"><span data-stu-id="10120-p116">After all of your changes are made to the directory, run IdFix again to ensure that the fixes you made didn't introduce new errors. You can repeat these steps as many times as you need to. It's a good idea to go through the process a few times before you synchronize.</span></span>
    
## <a name="i-want-to-refine-my-search-or-dig-deeper-into-the-errors-what-else-can-i-do-with-idfix"></a><span data-ttu-id="10120-177">Что еще можно сделать с IdFix, чтобы уточнить поиск или узнать подробнее об ошибках?</span><span class="sxs-lookup"><span data-stu-id="10120-177">I want to refine my search or dig deeper into the errors, what else can I do with IdFix?</span></span>

<span data-ttu-id="10120-178">Более подробную информацию можно найти в следующих разделах:</span><span class="sxs-lookup"><span data-stu-id="10120-178">More in-depth information is available from these topics:</span></span>
  
- <span data-ttu-id="10120-p117">[Подготовка атрибутов каталога для синхронизации с Office 365 с помощью инструмента IdFix](prepare-directory-attributes-for-synch-with-idfix.md) . После установки средства перехода в данном разделе приведены подробные инструкции по запуску средства, распространенные ошибки, которые указываются, предлагаемые исправления, примеры и практические советы по что делать, если у вас есть большое количество ошибок.</span><span class="sxs-lookup"><span data-stu-id="10120-p117">[Prepare directory attributes for synchronization with Office 365 by using the IdFix tool](prepare-directory-attributes-for-synch-with-idfix.md) . After you have installed the tool, jump to this topic for more detailed instructions about running the tool, common errors you will encounter, suggested fixes, examples, and best practices for what to do when you have a large number of errors.</span></span> 
- [<span data-ttu-id="10120-181">Справка: исключаемые и поддерживаемые объекты и атрибуты IdFix</span><span class="sxs-lookup"><span data-stu-id="10120-181">Reference: IdFix excluded and supported objects and attributes</span></span>](idfix-excluded-and-supported-objects-and-attributes.md)  
- [<span data-ttu-id="10120-182">Ссылка: журнал транзакций Office 365 IdFix</span><span class="sxs-lookup"><span data-stu-id="10120-182">Reference: Office 365 IdFix transaction log</span></span>](idfix-transaction-log.md)
    
## <a name="video-training"></a><span data-ttu-id="10120-183">Учебные</span><span class="sxs-lookup"><span data-stu-id="10120-183">Video training</span></span>

<span data-ttu-id="10120-184">Для получения дополнительных сведений см. [Установка и использование инструмента IDFix](https://support.office.com/article/4d81d73c-f172-4fd5-8542-f601c0c96aa9.aspx), с LinkedIn обучения.</span><span class="sxs-lookup"><span data-stu-id="10120-184">For more information, see the lesson [Install and use the IDFix tool](https://support.office.com/article/4d81d73c-f172-4fd5-8542-f601c0c96aa9.aspx), brought to you by LinkedIn Learning.</span></span>
  

