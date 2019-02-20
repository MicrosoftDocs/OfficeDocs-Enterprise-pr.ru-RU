---
title: Установка и запуск инструмента Office 365 IdFix
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
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
description: Сведения об установке и запуске средства Office 365 IdFix для очистки Active Directory перед его синхронизацией с Office 365.
ms.openlocfilehash: a35b2a476f2b30eccc955b980eda6315b146af27
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085408"
---
# <a name="install-and-run-the-office-365-idfix-tool"></a><span data-ttu-id="69903-103">Установка и запуск инструмента Office 365 IdFix</span><span class="sxs-lookup"><span data-stu-id="69903-103">Install and run the Office 365 IdFix tool</span></span>

<span data-ttu-id="69903-104">IdFix определяет ошибки, такие как дублирование и форматирование в каталоге, прежде чем выполнять синхронизацию с Office 365.</span><span class="sxs-lookup"><span data-stu-id="69903-104">IdFix identifies errors such as duplicates and formatting problems in your directory before you synchronize to Office 365.</span></span> 
  
<span data-ttu-id="69903-105">Для успешного завершения этой задачи необходимо работать с объектами User, Group и Contact в Active Directory.</span><span class="sxs-lookup"><span data-stu-id="69903-105">To finish this task successfully, you should be comfortable working with user, group, and contact objects in Active Directory.</span></span>
  
<span data-ttu-id="69903-p101">Если вы не можете выполнить эту задачу, можно выполнить несколько других действий. Эти методы могут быть проще, но они также могут занимать больше или иметь другие недостатки. Они:</span><span class="sxs-lookup"><span data-stu-id="69903-p101">If you can't complete this task, there are a couple of other things you can do. These methods might be easier, but they might also take longer or have other drawbacks. They are:</span></span>
  
- <span data-ttu-id="69903-p102">**Запустите синхронизацию службы каталогов, не запуская IdFix.** Вы можете синхронизировать каталог без запуска средства IdFix, но мы не рекомендуем использовать его. Устранение ошибок до синхронизации занимает меньше времени и часто приводит к более гладкому переходу в облако.</span><span class="sxs-lookup"><span data-stu-id="69903-p102">**Run directory synchronization without running IdFix.** You can synchronize your directory without running the IdFix tool, but we don't recommend it. Fixing errors before you synchronize takes less time and often provides a smoother transition to the cloud.</span></span> 
- <span data-ttu-id="69903-p103">**Наем консультанта.** Помощь эксперта позволит быстро обучить пользователей и синхронизировать ваш каталог.</span><span class="sxs-lookup"><span data-stu-id="69903-p103">**Hire a consultant.** Getting expert help can get your users up and running quickly and your directory synchronized.</span></span> 
    
## <a name="what-you-need-to-run-idfix"></a><span data-ttu-id="69903-114">Что необходимо для запуска IdFix</span><span class="sxs-lookup"><span data-stu-id="69903-114">What you need to run IdFix</span></span>

<span data-ttu-id="69903-p104">Самый простой способ заставить IdFix работать и устанавливать его на компьютер, присоединенный к домену. Его можно запустить на контроллере домена, если это необходимо, но это необязательно.</span><span class="sxs-lookup"><span data-stu-id="69903-p104">The easiest way to get IdFix up and running is to install it on a computer that is joined to your domain. You can run it on the domain controller if you want, but it's not necessary.</span></span>
  
### <a name="idfix-hardware-requirements"></a><span data-ttu-id="69903-117">Требования IdFix к оборудованию</span><span class="sxs-lookup"><span data-stu-id="69903-117">IdFix hardware requirements</span></span>

<span data-ttu-id="69903-118">Компьютер, на котором устанавливается IdFix, должен соответствовать следующим минимальным требованиям к оборудованию:</span><span class="sxs-lookup"><span data-stu-id="69903-118">The computer where you install IdFix needs to meet these minimum hardware requirements:</span></span>
  
- <span data-ttu-id="69903-119">4 ГБ ОЗУ</span><span class="sxs-lookup"><span data-stu-id="69903-119">4 GB RAM</span></span>
- <span data-ttu-id="69903-120">2 ГБ свободного места на жестком диске</span><span class="sxs-lookup"><span data-stu-id="69903-120">2 GB of hard disk space</span></span>
    
### <a name="idfix-software-requirements"></a><span data-ttu-id="69903-121">Требования IdFix к программному обеспечению</span><span class="sxs-lookup"><span data-stu-id="69903-121">IdFix software requirements</span></span>

<span data-ttu-id="69903-p105">Компьютер, на котором устанавливается IdFix, должен быть присоединен к тому же домену Active Directory, с которого вы хотите синхронизировать пользователей с Office 365. На компьютере также должен быть установлен .NET Framework 4,0.</span><span class="sxs-lookup"><span data-stu-id="69903-p105">The computer where you install IdFix needs to be joined to the same Active Directory domain from which you want to synchronize users to Office 365. The computer also needs to have .NET Framework 4.0 installed.</span></span> 
  
<span data-ttu-id="69903-p106">Если вы используете Windows Server 2008 или Windows Server 2012, то, вероятно, уже установлена платформа .NET Framework. В противном случае вы можете [скачать .net 4,0 из центра загрузки или с](https://go.microsoft.com/fwlink/p/?LinkId=400475) помощью центра обновления Windows.</span><span class="sxs-lookup"><span data-stu-id="69903-p106">If you are running Windows Server 2008 or Windows Server 2012, then .NET Framework is probably already installed. If not, you can [download .NET 4.0 from the download center](https://go.microsoft.com/fwlink/p/?LinkId=400475) or via Windows Update.</span></span> 
  
### <a name="idfix-permissions-requirements"></a><span data-ttu-id="69903-126">Требования к разрешениям IdFix</span><span class="sxs-lookup"><span data-stu-id="69903-126">IdFix permissions requirements</span></span>

<span data-ttu-id="69903-127">Учетная запись пользователя, используемая для запуска IdFix, требует права на чтение и запись в этом каталоге.</span><span class="sxs-lookup"><span data-stu-id="69903-127">The user account that you use to run IdFix needs to have read/write access to the directory.</span></span>
  
<span data-ttu-id="69903-p107">Если вы не уверены, что ваша учетная запись пользователя соответствует этим требованиям, и вы не знаете, как проверить, можно по-прежнему установить и запустить IdFix. Если у вашей учетной записи пользователя нет разрешений, IdFix просто выводит сообщение об ошибке при попытке запустить ее.</span><span class="sxs-lookup"><span data-stu-id="69903-p107">If you aren't sure if your user account meets these requirements, and you're not sure how to check, you can still install and run IdFix. If your user account doesn't have the right permissions, IdFix will simply display an error when you try to run it.</span></span>
  
## <a name="install-idfix"></a><span data-ttu-id="69903-130">Установка IdFix</span><span class="sxs-lookup"><span data-stu-id="69903-130">Install IdFix</span></span>

<span data-ttu-id="69903-131">Чтобы установить IdFix, скачайте и распакуйте **IdFix. exe**:</span><span class="sxs-lookup"><span data-stu-id="69903-131">To install IdFix, download and unzip **IdFix.exe**:</span></span> 
  
1. <span data-ttu-id="69903-132">Войдите на компьютер, где вы хотите установить инструмент IdFix.</span><span class="sxs-lookup"><span data-stu-id="69903-132">Log on to the computer where you want to install the IdFix tool.</span></span>
    
2. <span data-ttu-id="69903-133">Перейдите на сайт центра загрузки Майкрософт для [средства устранения ошибок IdFix DirSync](https://go.microsoft.com/fwlink/?linkid=867219).</span><span class="sxs-lookup"><span data-stu-id="69903-133">Go to the Microsoft download site for the [IdFix DirSync Error Remediation Tool](https://go.microsoft.com/fwlink/?linkid=867219).</span></span>
    
3. <span data-ttu-id="69903-134">Выберите пункт **Загрузить**.</span><span class="sxs-lookup"><span data-stu-id="69903-134">Choose **Download**.</span></span>
    
4. <span data-ttu-id="69903-135">При появлении соответствующего запроса нажмите кнопку **выполнить**.</span><span class="sxs-lookup"><span data-stu-id="69903-135">When prompted, choose **Run**.</span></span>
    
5. <span data-ttu-id="69903-p108">В диалоговом окне **Самоизвлечение WinZip** в поле **извлечь в папку** введите или выберите расположение, в которое нужно установить средство IdFix. По умолчанию IdFix устанавливается в `C:\Deployment Tools\`.</span><span class="sxs-lookup"><span data-stu-id="69903-p108">On the **WinZip Self-Extractor** dialog box, in the **Unzip to folder** text box, type or browse to the location where you want to install the IdFix tool. By default, IdFix is installed into `C:\Deployment Tools\`.</span></span> 
    
6. <span data-ttu-id="69903-138">Нажмите кнопку **извлечь**.</span><span class="sxs-lookup"><span data-stu-id="69903-138">Choose **Unzip**.</span></span>
    
## <a name="run-the-idfix-tool"></a><span data-ttu-id="69903-139">Запуск IdFix</span><span class="sxs-lookup"><span data-stu-id="69903-139">Run the IdFix tool</span></span>

<span data-ttu-id="69903-140">После установки IdFix запустите инструмент для поиска проблем в каталоге:</span><span class="sxs-lookup"><span data-stu-id="69903-140">After you install IdFix, run the tool to search for problems in your directory:</span></span>
  
1. <span data-ttu-id="69903-141">С помощью учетной записи, имеющей право чтения и записи в этой папке, войдите на компьютер, на котором установлен IdFix.</span><span class="sxs-lookup"><span data-stu-id="69903-141">Using an account that has read/write access to the directory, log on to the computer where you installed IdFix.</span></span>
    
2. <span data-ttu-id="69903-p109">В проводнике перейдите в папку, в которую вы установили IdFix. Если во время установки выбрана папка по умолчанию, `C:\Deployment Tools\IdFix`перейдите на страницу.</span><span class="sxs-lookup"><span data-stu-id="69903-p109">In File Explorer, go to the location where you installed IdFix. If you chose the default folder during installation, go to `C:\Deployment Tools\IdFix`.</span></span>
    
3. <span data-ttu-id="69903-144">Дважды щелкните файл **IdFix.exe**.</span><span class="sxs-lookup"><span data-stu-id="69903-144">Double-click **IdFix.exe**.</span></span> 
    
    ![Выберите файл IdFix. exe.](media/a9387bbc-991f-41c2-a500-45e3ce574285.JPG)
  
4. <span data-ttu-id="69903-p110">По умолчанию IdFix использует набор правил для нескольких клиентов для проверки записей в каталоге. Это правильный набор правил для большинства клиентов Office 365. Тем не менее, если вы настроили Office 365 или ITAR (международный трафик в вооруженных нормах), вы можете настроить IdFix для использования выделенного набора правил. Если вы не знаете, какой тип клиента вы знаете, вы можете спокойно пропустить этот шаг. Чтобы задать для правила значение выделенный, щелкните значок шестеренки в строке меню, а затем выберите **выделенный**.</span><span class="sxs-lookup"><span data-stu-id="69903-p110">By default, IdFix uses the Multi-Tenant rule set to test the entries in your directory. This is the right rule set for most Office 365 customers. However, if you are an Office 365 Dedicated or ITAR (International Traffic in Arms Regulations) customer, you can configure IdFix to use the Dedicated rule set instead. If you aren't sure what type of customer you are, you can safely skip this step. To set the rule set to Dedicated, click the gear icon in the menu bar and then choose **Dedicated**.</span></span>
    
5. <span data-ttu-id="69903-151">Нажмите кнопку **запрос**.</span><span class="sxs-lookup"><span data-stu-id="69903-151">Choose **Query**.</span></span>
    
    ![Выберите запрос в IdFix.](media/a07a7aa7-d0ac-4817-8757-946019813a57.JPG)
  
6. <span data-ttu-id="69903-153">По умолчанию IdFix выполняет поиск ошибок по всему каталогу.</span><span class="sxs-lookup"><span data-stu-id="69903-153">By default, IdFix searches the entire directory for errors.</span></span>
    
    <span data-ttu-id="69903-p111">В зависимости от размера каталога выполнение запроса может занять некоторое время. Вы можете наблюдать за ходом выполнения в нижней части главного окна средства. Если вы нажимаете кнопку **Отмена**, вам потребуется перезапустить его с самого начала.</span><span class="sxs-lookup"><span data-stu-id="69903-p111">Depending on the size of your directory, running the query can take a while. You can watch the progress at the bottom of the tool's main window. If you click **Cancel**, you'll need to restart from the beginning.</span></span>
    
    ![IdFix запрос и число ошибок.](media/da0198a0-7d4d-4afe-a256-e82f1330ada5.JPG)
  
7. <span data-ttu-id="69903-p112">После завершения запроса IdFix можно выполнить синхронизацию каталога в случае отсутствия ошибок. Если в каталоге есть ошибки, рекомендуется исправить их перед синхронизацией. Если вы хотите получить более конкретные сведения о типах ошибок и рекомендаций по их оптимальному способу, ознакомьтесь со ссылками в конце этой статьи.</span><span class="sxs-lookup"><span data-stu-id="69903-p112">After IdFix completes the query, you can go ahead and synchronize your directory if there are no errors. If there are errors in your directory, it is recommended that you fix them before you synchronize. If you want more specific information about types of errors and recommendations about the best way to fix each of them, see the links at the end of this topic.</span></span> 
    
    <span data-ttu-id="69903-161">Несмотря на то что исправлять ошибки, обнаруженные IdFix, необязательно, мы настоятельно рекомендуем хотя бы просмотреть их.</span><span class="sxs-lookup"><span data-stu-id="69903-161">While it is not mandatory to fix the errors before you synchronize, we strongly recommend that you at least review all the errors returned by IdFix.</span></span>
    
    <span data-ttu-id="69903-162">Каждая ошибка отображается в отдельной строке в главном окне средства.</span><span class="sxs-lookup"><span data-stu-id="69903-162">Each error is displayed in a separate row in the tool's main window .</span></span> 
    
8. <span data-ttu-id="69903-p113">Если вы согласны с изменением, предложенным в столбце **UPDATE**, выберите необходимое действие в столбце **ACTION** и нажмите кнопку **Apply** (Применить). При нажатии кнопки **Apply** (Применить) средство внесет изменения в каталог.</span><span class="sxs-lookup"><span data-stu-id="69903-p113">If you agree with the suggested change in the **UPDATE** column, in the **ACTION** column select what you want IdFix to do to implement the change and then click **Apply**. When you click **Apply**, the tool makes the changes in the directory.</span></span>
    
    <span data-ttu-id="69903-p114">После каждого обновления нет необходимости нажимать кнопку **Применить** . Вместо этого можно устранить несколько ошибок, прежде чем нажать кнопку **Применить** и IdFix будет изменять их все одновременно. Можно отсортировать ошибки по типу ошибки, щелкнув **Ошибка** в верхней части столбца со списком типов ошибок.</span><span class="sxs-lookup"><span data-stu-id="69903-p114">You don't have to click **Apply** after each update. Instead, you can fix several errors before you click **Apply** and IdFix will change them all at the same time. You can sort the errors by error type by clicking **ERROR** at the top of the column that lists the error types.</span></span> 
    
    <span data-ttu-id="69903-p115">Одной из стратегий является устранение всех ошибок того же типа; Например, сначала исправьте все дубликаты, а затем примените их. Затем исправьте ошибки форматов символов и т. д. Каждый раз при применении изменений средство IdFix создает отдельный файл журнала, который можно использовать для отмены изменений в случае ошибки. [Журнал транзакций](idfix-transaction-log.md) хранится в папке, в которую вы установили IdFix.  _К:\деплоймент тулс\идфикс_ по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="69903-p115">One strategy is to fix all the errors of the same type; for example, fix all the duplicates first, and apply them. Next, fix the character format errors, and so on. Each time you apply the changes, the IdFix tool creates a separate log file that you can use to undo your changes in case you make a mistake. The [transaction log](idfix-transaction-log.md) is stored in the folder that you installed IdFix in.  _C:\Deployment Tools\IdFix_ by default.</span></span> 
    
    ![Ошибки устранение в IdFix.](media/5f051070-652c-4be7-98bf-312295e32371.png)
  
9. <span data-ttu-id="69903-p116">После внесения всех изменений в каталог запустите IdFix еще раз, чтобы убедиться в том, что внесенные вами исправления не познакомятся с новыми ошибками. Эти действия можно повторять столько раз, сколько необходимо. Перед синхронизацией рекомендуется пройти процесс несколько раз.</span><span class="sxs-lookup"><span data-stu-id="69903-p116">After all of your changes are made to the directory, run IdFix again to ensure that the fixes you made didn't introduce new errors. You can repeat these steps as many times as you need to. It's a good idea to go through the process a few times before you synchronize.</span></span>
    
## <a name="i-want-to-refine-my-search-or-dig-deeper-into-the-errors-what-else-can-i-do-with-idfix"></a><span data-ttu-id="69903-177">Что еще можно сделать с IdFix, чтобы уточнить поиск или узнать подробнее об ошибках?</span><span class="sxs-lookup"><span data-stu-id="69903-177">I want to refine my search or dig deeper into the errors, what else can I do with IdFix?</span></span>

<span data-ttu-id="69903-178">Более подробную информацию можно найти в следующих разделах:</span><span class="sxs-lookup"><span data-stu-id="69903-178">More in-depth information is available from these topics:</span></span>
  
- <span data-ttu-id="69903-p117">[Подготовка атрибутов каталога для синхронизации с Office 365 с помощью средства IdFix](prepare-directory-attributes-for-synch-with-idfix.md) . После установки средства переходите к этому разделу, чтобы получить более подробные инструкции по запуску этого средства, распространенным ошибкам, предлагаемым исправлениям, примерам и рекомендациям по поводу того, что делать при большом количестве ошибок.</span><span class="sxs-lookup"><span data-stu-id="69903-p117">[Prepare directory attributes for synchronization with Office 365 by using the IdFix tool](prepare-directory-attributes-for-synch-with-idfix.md) . After you have installed the tool, jump to this topic for more detailed instructions about running the tool, common errors you will encounter, suggested fixes, examples, and best practices for what to do when you have a large number of errors.</span></span> 
- [<span data-ttu-id="69903-181">Справка: исключаемые и поддерживаемые объекты и атрибуты IdFix</span><span class="sxs-lookup"><span data-stu-id="69903-181">Reference: IdFix excluded and supported objects and attributes</span></span>](idfix-excluded-and-supported-objects-and-attributes.md)  
- [<span data-ttu-id="69903-182">Ссылка: журнал транзакций Office 365 IdFix</span><span class="sxs-lookup"><span data-stu-id="69903-182">Reference: Office 365 IdFix transaction log</span></span>](idfix-transaction-log.md)
    
## <a name="video-training"></a><span data-ttu-id="69903-183">Обучающие видео</span><span class="sxs-lookup"><span data-stu-id="69903-183">Video training</span></span>

<span data-ttu-id="69903-184">Дополнительные сведения можно найти в разделе [Установка и использование средства IDFix](https://support.office.com/article/install-and-use-the-idfix-tool-4d81d73c-f172-4fd5-8542-f601c0c96aa9?ui=en-US&rs=en-US&ad=US), предоставленного программой LinkedIn Learning.</span><span class="sxs-lookup"><span data-stu-id="69903-184">For more information, see the lesson [Install and use the IDFix tool](https://support.office.com/article/install-and-use-the-idfix-tool-4d81d73c-f172-4fd5-8542-f601c0c96aa9?ui=en-US&rs=en-US&ad=US), brought to you by LinkedIn Learning.</span></span>
  

