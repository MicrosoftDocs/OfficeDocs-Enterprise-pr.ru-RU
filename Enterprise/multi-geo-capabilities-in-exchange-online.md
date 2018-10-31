---
title: Ферма с несколькими географически возможности в Exchange Online
ms.author: chrisda
author: chrisda
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Normal
ms.assetid: ''
description: Разверните узел состояние присутствия Office 365 для нескольких географических регионов с несколькими географически возможности в Exchange Online.
ms.openlocfilehash: 5f34a2da47b9767aa9dfe22c6be7237951128960
ms.sourcegitcommit: a3e2b2e58c328238c15d3f9daf042ea3de9d66be
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/30/2018
ms.locfileid: "25849925"
---
# <a name="multi-geo-capabilities-in-exchange-online"></a><span data-ttu-id="1a0a2-103">Ферма с несколькими географически возможности в Exchange Online</span><span class="sxs-lookup"><span data-stu-id="1a0a2-103">Multi-Geo Capabilities in Exchange Online</span></span>

<span data-ttu-id="1a0a2-p101">Одним клиентом охватывать разных географических местоположениях предоставляют возможности несколькими Geo в Office 365. При включении географически ферма с несколькими клиентами можно выбрать расположение содержимого почтового ящика, Exchange Online (статических данных) на уровне пользователя.</span><span class="sxs-lookup"><span data-stu-id="1a0a2-p101">Multi-Geo Capabilities in Office 365 enable a single tenant to span multiple geographic locations. When multi-geo is enabled, customers can select the location of Exchange Online mailbox content (data at rest) on a per-user basis.</span></span>

<span data-ttu-id="1a0a2-p102">Расположение начальной клиента (называется центрального расположения) определяется на основании адрес для выставления счетов. При включении несколькими географически почтовые ящики можно поместить в расположениях Дополнительные сопутствующие по:</span><span class="sxs-lookup"><span data-stu-id="1a0a2-p102">Your initial tenant location (referred to as the central location) is determined based on your billing address. When multi-geo is enabled, you can place mailboxes in additional satellite locations by:</span></span>

- <span data-ttu-id="1a0a2-108">Создание нового почтового ящика Exchange Online напрямую в расположение вспомогательных.</span><span class="sxs-lookup"><span data-stu-id="1a0a2-108">Creating a new Exchange Online mailbox directly in a satellite location.</span></span>

- <span data-ttu-id="1a0a2-109">Перемещение существующего почтового ящика Exchange Online в расположение вспомогательных.</span><span class="sxs-lookup"><span data-stu-id="1a0a2-109">Moving an existing Exchange Online mailbox into a satellite location.</span></span>

- <span data-ttu-id="1a0a2-110">Адаптация новых сотрудников почтовых ящиков из локальной организации Exchange непосредственно в расположение вспомогательных.</span><span class="sxs-lookup"><span data-stu-id="1a0a2-110">Onboarding a mailbox from an on-premises Exchange organization directly into a satellite location.</span></span>

<span data-ttu-id="1a0a2-111">В следующих расположениях географически доступны для использования в конфигурации с несколькими географически:</span><span class="sxs-lookup"><span data-stu-id="1a0a2-111">The following geo locations are available for use in a Multi-Geo configuration:</span></span>

- <span data-ttu-id="1a0a2-112">Азиатско-Тихоокеанский регион</span><span class="sxs-lookup"><span data-stu-id="1a0a2-112">Asia Pacific</span></span>

- <span data-ttu-id="1a0a2-113">Австралия</span><span class="sxs-lookup"><span data-stu-id="1a0a2-113">Australia</span></span>

- <span data-ttu-id="1a0a2-114">Канада</span><span class="sxs-lookup"><span data-stu-id="1a0a2-114">Canada</span></span>

- <span data-ttu-id="1a0a2-115">Европейский Союз</span><span class="sxs-lookup"><span data-stu-id="1a0a2-115">European Union</span></span>

- <span data-ttu-id="1a0a2-116">Франция</span><span class="sxs-lookup"><span data-stu-id="1a0a2-116">France</span></span>

- <span data-ttu-id="1a0a2-117">Индия (в настоящее время доступны только для клиентов с адреса для выставления счета в Индии)</span><span class="sxs-lookup"><span data-stu-id="1a0a2-117">India (currently only available to customers with billing addresses in India)</span></span>

- <span data-ttu-id="1a0a2-118">Япония</span><span class="sxs-lookup"><span data-stu-id="1a0a2-118">Japan</span></span>

- <span data-ttu-id="1a0a2-119">Республика Корея</span><span class="sxs-lookup"><span data-stu-id="1a0a2-119">Korea</span></span>

- <span data-ttu-id="1a0a2-120">Соединенное Королевство</span><span class="sxs-lookup"><span data-stu-id="1a0a2-120">United Kingdom</span></span>

- <span data-ttu-id="1a0a2-121">США</span><span class="sxs-lookup"><span data-stu-id="1a0a2-121">United States</span></span>

## <a name="prerequisite-configuration"></a><span data-ttu-id="1a0a2-122">Предварительные настройки</span><span class="sxs-lookup"><span data-stu-id="1a0a2-122">Prerequisite configuration</span></span>
<span data-ttu-id="1a0a2-p103">Прежде чем начать, используя возможности несколькими географически в Exchange Online, корпорации Майкрософт необходимо настроить клиент Exchange Online для поддержки различных географически. Этот процесс однократного конфигурации запускается после определения порядка что Office 365 Multi-географически и лицензий, которые отображаются в вашего клиента. Этот процесс однократного конфигурации обычно занимает меньше, чем 30 дней. Чтобы порядок Office 365 Multi-географически, обратитесь к представителю Майкрософт. Дополнительные сведения можно https://aka.ms/Multi-Geo.</span><span class="sxs-lookup"><span data-stu-id="1a0a2-p103">Before you can start using Multi-Geo capabilities in Exchange Online, Microsoft needs to configure your Exchange Online tenant for multi-geo support. This one-time configuration process is triggered after you order Office 365 Multi-Geo and the licenses show up in your tenant. This one-time configuration process should typically take less than 30 days to complete. To order Office 365 Multi-Geo, contact your Microsoft representative. For more information, see https://aka.ms/Multi-Geo.</span></span>

<span data-ttu-id="1a0a2-p104">Вы будете получать уведомления в [Центр сообщений Office 365](https://support.office.com/article/Message-center-in-Office-365-38FB3333-BFCC-4340-A37B-DEDA509C2093) после завершения настройки. Конфигурация будет запущен автоматически после лицензии несколькими географически отображаются в вашего клиента.</span><span class="sxs-lookup"><span data-stu-id="1a0a2-p104">You'll receive notifications in the [Office 365 message center](https://support.office.com/article/Message-center-in-Office-365-38FB3333-BFCC-4340-A37B-DEDA509C2093) when your configuration has completed. Configuration is automatically triggered once your multi-geo licenses show up in your tenant.</span></span>

## <a name="mailbox-placement-and-moves"></a><span data-ttu-id="1a0a2-130">Расположение почтового ящика и перемещений</span><span class="sxs-lookup"><span data-stu-id="1a0a2-130">Mailbox placement and moves</span></span>
<span data-ttu-id="1a0a2-131">После завершения действия по настройке необходимого несколькими географически Microsoft Exchange Online будет поддерживать атрибут **PreferredDataLocation** для объектов-пользователей в Azure AD.</span><span class="sxs-lookup"><span data-stu-id="1a0a2-131">After Microsoft completes the prerequisite multi-geo configuration steps, Exchange Online will honor the **PreferredDataLocation** attribute on user objects in Azure AD.</span></span>

<span data-ttu-id="1a0a2-p105">Exchange Online синхронизирует свойство **PreferredDataLocation** из Azure AD в свойство **MailboxRegion** в службе каталогов Exchange Online. Значение **MailboxRegion** определяет географически, где будет помещен почтовых ящиков пользователей и все связанные архивные почтовые ящики. Настройка основного почтового ящика и архивирование почтовых ящиков пользователей могут располагаться в разных географического расположения невозможна. Только один географического расположения можно настроить для каждого объекта-пользователя.</span><span class="sxs-lookup"><span data-stu-id="1a0a2-p105">Exchange Online synchronizes the **PreferredDataLocation** property from Azure AD into the **MailboxRegion** property in the Exchange Online directory service. The value of **MailboxRegion** determines the Geo where user mailboxes and any associated archive mailboxes will be placed. It is not possible to configure a user's primary mailbox and archive mailboxes to reside in different geo locations. Only one geo location may be configured per user object.</span></span>

- <span data-ttu-id="1a0a2-136">При настройке **PreferredDataLocation** на пользователя с помощью существующего почтового ящика почтового ящика будут помещены в очередь перемещения и автоматически перемещены указанного географического расположения.</span><span class="sxs-lookup"><span data-stu-id="1a0a2-136">When **PreferredDataLocation** is configured on a user with an existing mailbox, the mailbox will be put into a relocation queue and automatically moved to the specified geo location.</span></span> 

- <span data-ttu-id="1a0a2-137">Когда **PreferredDataLocation** настроен на пользователя, не существующего почтового ящика, почтовый ящик будет выполнена подготовка в указанного географического расположения.</span><span class="sxs-lookup"><span data-stu-id="1a0a2-137">When **PreferredDataLocation** is configured on a user without an existing mailbox, the mailbox will be provisioned into the specified geo location.</span></span> 

- <span data-ttu-id="1a0a2-138">Если **PreferredDataLocation** не указан на пользователя, почтовый ящик будет назначено центрального расположения.</span><span class="sxs-lookup"><span data-stu-id="1a0a2-138">When **PreferredDataLocation** is not specified on a user, the mailbox will be placed in the central location.</span></span>

- <span data-ttu-id="1a0a2-139">Если код **PreferredDataLocation** неверен (например тип NAN вместо им), почтовый ящик будет помещен в центральном расположении.</span><span class="sxs-lookup"><span data-stu-id="1a0a2-139">If the **PreferredDataLocation** code is incorrect (e.g. a type of NAN instead of NAM), the mailbox will be placed in the central location.</span></span>

<span data-ttu-id="1a0a2-p106">**Примечание**: несколькими географически возможности и Скайп для бизнеса на региональном уровнях размещенных собрания по сети обоих используйте свойство **PreferredDataLocation** на объектов-пользователей для обнаружения служб. Если вы настраиваете **PreferredDataLocation** значения для объектов-пользователей на региональном уровнях размещенной собраний, почтовых ящиков для тех пользователей, автоматически перемещается в указанного географического расположения после включения несколькими географически на клиента Office 365.</span><span class="sxs-lookup"><span data-stu-id="1a0a2-p106">**Note**: multi-geo capabilities and Skype for Business Online regionally hosted meetings both use the **PreferredDataLocation** property on user objects to locate services. If you configure **PreferredDataLocation** values on user objects for regionally hosted meetings, the mailbox for those users will be automatically moved to the specified geo location after multi-geo is enabled on the Office 365 tenant.</span></span>

## <a name="feature-limitations-for-multi-geo-in-exchange-online"></a><span data-ttu-id="1a0a2-142">Ограничения для нескольких Geo в Exchange Online</span><span class="sxs-lookup"><span data-stu-id="1a0a2-142">Feature limitations for Multi-Geo in Exchange Online</span></span>
1. <span data-ttu-id="1a0a2-p107">Ферма с несколькими географически возможности поддержки только почтовые ящики пользователей, почтовые ящики ресурса (почтовые ящики оборудования и помещений) и общие почтовые ящики. Общедоступные папки почтовых ящиков и групп Office 365, остаются в центральном расположении.</span><span class="sxs-lookup"><span data-stu-id="1a0a2-p107">Only user mailboxes, resource mailboxes (room and equipment mailboxes), and shared mailboxes support multi-geo features. Public Folder Mailboxes and Office 365 Groups remain in the central location.</span></span>
 
2. <span data-ttu-id="1a0a2-p108">Безопасность и соответствие требованиям функции (например, аудит и обнаружения электронных данных), доступные в центре администрирования Exchange (EAC) не доступны в географически нескольких организаций. Вместо этого необходимо использовать для настройки функций безопасности и соответствия требованиям в [Office 365 безопасности & центре соответствия требованиям](https://support.office.com/article/7e696a40-b86b-4a20-afcc-559218b7b1b8) .</span><span class="sxs-lookup"><span data-stu-id="1a0a2-p108">Security and compliance features (for example, auditing and eDiscovery) that are available in the Exchange admin center (EAC) aren't available in multi-geo organizations. Instead, you need to use the [Office 365 Security & Compliance Center](https://support.office.com/article/7e696a40-b86b-4a20-afcc-559218b7b1b8) to configure security and compliance features.</span></span>

3. <span data-ttu-id="1a0a2-p109">Outlook для Mac пользователей могут возникнуть кратковременной потере доступа к их папки серверный архив при перемещении их почтовых ящиков в новое расположение географически. Это условие возникает, когда основной пользователя и архивные почтовые ящики находятся в разных географического расположения, так как перемещение почтовых ящиков между географически может завершиться в разное время.</span><span class="sxs-lookup"><span data-stu-id="1a0a2-p109">Outlook for Mac users may experience a temporary loss of access to their Online Archive folder while you move their mailbox to a new geo location. This condition occurs when the user's the primary and archive mailboxes are in different geo locations, because cross-Geo mailbox moves may complete at different times.</span></span>

4. <span data-ttu-id="1a0a2-p110">Пользователи не могут совместно использовать *папки почтовых ящиков* в подразделениях geo в Outlook в Интернете (ранее известных как Outlook Web App или OWA). Например пользователя в Европейском союзе нельзя использовать Outlook в Интернете для открытия общей папки в почтовом ящике, расположенного в США. Тем не менее Outlook на веб-пользователей можно открыть *другой почтовый ящик* в разных Geos с помощью отдельном окне браузера, как описано в [Открытие почтового ящика другого пользователя в отдельном окне браузера в Outlook Web App](https://support.office.com/article/A909AD30-E413-40B5-A487-0EA70B763081#__toc372210362).</span><span class="sxs-lookup"><span data-stu-id="1a0a2-p110">Users can't share *mailbox folders* across geo locations in Outlook on the web (formerly known as Outlook Web App or OWA). For example, a user in the European Union can't use Outlook on the web to open a shared folder in a mailbox that's located in the United States. However, Outlook on the Web users can open *other mailboxes* in different Geos by using a separate browser window as described in [Open another person’s mailbox in a separate browser window in Outlook Web App](https://support.office.com/article/A909AD30-E413-40B5-A487-0EA70B763081#__toc372210362).</span></span>

    <span data-ttu-id="1a0a2-152">**Примечание**: географически нескольких почтовых ящиков общий доступ к папке, поддерживаемых в Outlook в Windows.</span><span class="sxs-lookup"><span data-stu-id="1a0a2-152">**Note**: Cross-geo mailbox folder sharing is supported in Outlook on Windows.</span></span>

## <a name="administration"></a><span data-ttu-id="1a0a2-153">Администрирование</span><span class="sxs-lookup"><span data-stu-id="1a0a2-153">Administration</span></span> 
<span data-ttu-id="1a0a2-p111">Для просмотра и настройки несколькими географически свойств в среде Office 365 требуется удаленной оболочки PowerShell. Сведения о различных моделей PowerShell, используемые для администрирования Office 365 содержатся в разделе [Управление Office 365 и Exchange Online с помощью Windows PowerShell](https://support.office.com//article/06a743bb-ceb6-49a9-a61d-db4ffdf54fa6).</span><span class="sxs-lookup"><span data-stu-id="1a0a2-p111">Remote PowerShell is required to view and configure multi geo properties in your Office 365 environment. For information on various PowerShell modules used to administer Office 365, see [Managing Office 365 and Exchange Online with Windows PowerShell](https://support.office.com//article/06a743bb-ceb6-49a9-a61d-db4ffdf54fa6).</span></span>

- <span data-ttu-id="1a0a2-p112">Необходимо v1.1.166.0 [PowerShell модуле Microsoft Azure Active Directory](https://social.technet.microsoft.com/wiki/contents/articles/28552.microsoft-azure-active-directory-powershell-module-version-release-history.aspx) или более поздней версии в v1.x, чтобы просмотреть свойство **PreferredDataLocation** на объектов-пользователей. Синхронизация через подключение AAD в AAD объектов-пользователей не могут иметь напрямую изменить с помощью AAD PowerShell их **PreferredDataLocation** значение. С помощью AAD PowerShell может быть изменено объектов-пользователей только в облаке. Чтобы подключиться к Windows Azure AD PowerShell, обратитесь к разделу [подключение к Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell).</span><span class="sxs-lookup"><span data-stu-id="1a0a2-p112">You need the [Microsoft Azure Active Directory PowerShell Module](https://social.technet.microsoft.com/wiki/contents/articles/28552.microsoft-azure-active-directory-powershell-module-version-release-history.aspx) v1.1.166.0 or later in v1.x to see the **PreferredDataLocation** property on user objects. User objects synchronized via AAD Connect into AAD cannot have their **PreferredDataLocation** value directly modified via AAD PowerShell. Cloud-only user objects can be modified via AAD PowerShell. To connect to Azure AD PowerShell, see [Connect to Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell).</span></span> 

- <span data-ttu-id="1a0a2-160">Чтобы подключиться к Exchange Online PowerShell, обратитесь к разделу [подключение к Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).</span><span class="sxs-lookup"><span data-stu-id="1a0a2-160">To connect to Exchange Online PowerShell, see [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).</span></span> 

### <a name="connect-directly-to-a-specific-geo-using-exchange-online-powershell"></a><span data-ttu-id="1a0a2-161">Прямой звонок на конкретных географически с помощью Exchange Online PowerShell</span><span class="sxs-lookup"><span data-stu-id="1a0a2-161">Connect directly to a specific Geo using Exchange Online PowerShell</span></span>
<span data-ttu-id="1a0a2-p113">Как правило Exchange Online PowerShell будут подключаться к географически расположение по умолчанию. Однако можно также подключиться непосредственно к географически нестандартные расположения. Из-за повышение производительности мы рекомендуем путем прямого подключения расположение географически не по умолчанию при только управление пользователями в данном месте географически.</span><span class="sxs-lookup"><span data-stu-id="1a0a2-p113">Typically, Exchange Online PowerShell will connect to the default geo location. But, you can also connect directly to non-default geo locations. Because of performance improvements, we recommend connecting directly to the non-default geo location when you only manage users in that geo location.</span></span>

<span data-ttu-id="1a0a2-p114">Для подключения к определенным Geo параметра *ConnectionUri* отличается от инструкции регулярных подключения. Остальные команды и значения, совпадают. Порядок действий:</span><span class="sxs-lookup"><span data-stu-id="1a0a2-p114">To connect to a specific Geo, the *ConnectionUri* parameter is different than the regular connection instructions. The rest of the commands and values are the same. The steps are:</span></span>

1. <span data-ttu-id="1a0a2-168">На локальном компьютере откройте Windows PowerShell и выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="1a0a2-168">On your local computer, open Windows PowerShell and run the following command:</span></span>
    
    ```
    $UserCredential = Get-Credential
    ```
   <span data-ttu-id="1a0a2-169">В диалоговом окне **Запрос учетных данных Windows PowerShell** введите рабочий или школа учетной записи и пароль и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="1a0a2-169">In the **Windows PowerShell Credential Request** dialog box, type your work or school account and password, and then click **OK**.</span></span>
    
2. <span data-ttu-id="1a0a2-p115">Замените `<emailaddress>` с адресом электронной почты из **любой** почтовых ящиков в целевом расположении географически и выполните следующую команду. Разрешения для почтового ящика и связь с свои учетные данные на шаге 1 не учитываются; адрес электронной почты просто сообщает Exchange Online where для подключения.</span><span class="sxs-lookup"><span data-stu-id="1a0a2-p115">Replace `<emailaddress>` with the email address of **any** mailbox in the target geo location and run the following command. Your permissions on the mailbox and the relationship to your credentials in Step 1 are not a factor; the email address simply tells Exchange Online where to connect.</span></span>
  
   ```
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=<emailaddress> -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```

   <span data-ttu-id="1a0a2-172">Например если olga@contoso.onmicrosoft.com является адресом электронной почты допустимый почтовый ящик в географически, чтобы подключиться, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="1a0a2-172">For example, if olga@contoso.onmicrosoft.com is the email address of a valid mailbox in the Geo you want to connect, run the following command:</span></span>

   ```
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=olga@contoso.onmicrosoft.com -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```
3. <span data-ttu-id="1a0a2-173">Выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="1a0a2-173">Run the following command:</span></span>
    
    ```
    Import-PSSession $Session
    ```

### <a name="azure-ad-connect-version-requirements"></a><span data-ttu-id="1a0a2-174">Требования относительно версий Azure AD подключение</span><span class="sxs-lookup"><span data-stu-id="1a0a2-174">Azure AD Connect version requirements</span></span>
<span data-ttu-id="1a0a2-p116">Подключение AAD версии 1.1.524.0 или более поздняя версия является единственным поддерживаемым способом для установки свойства **PreferredDataLocation** объектов-пользователей, которые синхронизируются из локального Active Directory. Синхронизация через подключение AAD в AAD объектов-пользователей не могут иметь напрямую изменить с помощью AAD PowerShell их **PreferredDataLocation** значение. С помощью AAD PowerShell может быть изменено объектов-пользователей только в облаке. Подробные сведения содержатся в разделе [Azure Active Directory подключение синхронизации: Настройка предпочитаемого данных расположения для ресурсов Office 365](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span><span class="sxs-lookup"><span data-stu-id="1a0a2-p116">AAD Connect version 1.1.524.0 or later is the only supported method for setting the **PreferredDataLocation** property on user objects that are synchronized from on-premises Active Directory. User objects synchronized via AAD Connect into AAD cannot have their **PreferredDataLocation** value directly modified via AAD PowerShell. Cloud-only user objects can be modified via AAD PowerShell. For detailed instructions, see [Azure Active Directory Connect sync: Configure preferred data location for Office 365 resources](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span></span>

### <a name="geo-codes"></a><span data-ttu-id="1a0a2-179">Коды географически</span><span class="sxs-lookup"><span data-stu-id="1a0a2-179">Geo Codes</span></span>
<span data-ttu-id="1a0a2-p117">Для указания Geo в свойстве **PreferredDataLocation** используйте трех букв. В следующей таблице перечислены коды для доступных Geos:</span><span class="sxs-lookup"><span data-stu-id="1a0a2-p117">You use three-letter codes to specify the Geo in the **PreferredDataLocation** property. The following table lists the codes for the available Geos:</span></span>

|<span data-ttu-id="1a0a2-182">Географическое</span><span class="sxs-lookup"><span data-stu-id="1a0a2-182">Geo</span></span> |<span data-ttu-id="1a0a2-183">Код</span><span class="sxs-lookup"><span data-stu-id="1a0a2-183">Code</span></span> |
|---------|---------|
|<span data-ttu-id="1a0a2-184">Азиатско-Тихоокеанский регион</span><span class="sxs-lookup"><span data-stu-id="1a0a2-184">Asia/Pacific</span></span> |<span data-ttu-id="1a0a2-185">APC</span><span class="sxs-lookup"><span data-stu-id="1a0a2-185">APC</span></span> |
|<span data-ttu-id="1a0a2-186">Австралия</span><span class="sxs-lookup"><span data-stu-id="1a0a2-186">Australia</span></span> |<span data-ttu-id="1a0a2-187">AUS</span><span class="sxs-lookup"><span data-stu-id="1a0a2-187">AUS</span></span> |
|<span data-ttu-id="1a0a2-188">Канада</span><span class="sxs-lookup"><span data-stu-id="1a0a2-188">Canada</span></span> |<span data-ttu-id="1a0a2-189">CAN</span><span class="sxs-lookup"><span data-stu-id="1a0a2-189">CAN</span></span> |
|<span data-ttu-id="1a0a2-190">Европейский Союз</span><span class="sxs-lookup"><span data-stu-id="1a0a2-190">European Union</span></span> |<span data-ttu-id="1a0a2-191">EUR</span><span class="sxs-lookup"><span data-stu-id="1a0a2-191">EUR</span></span> |
|<span data-ttu-id="1a0a2-192">Франция</span><span class="sxs-lookup"><span data-stu-id="1a0a2-192">France</span></span> |<span data-ttu-id="1a0a2-193">FRA</span><span class="sxs-lookup"><span data-stu-id="1a0a2-193">FRA</span></span>|
|<span data-ttu-id="1a0a2-194">Индия</span><span class="sxs-lookup"><span data-stu-id="1a0a2-194">India</span></span> |<span data-ttu-id="1a0a2-195">IND</span><span class="sxs-lookup"><span data-stu-id="1a0a2-195">IND</span></span> |
|<span data-ttu-id="1a0a2-196">Япония</span><span class="sxs-lookup"><span data-stu-id="1a0a2-196">Japan</span></span> |<span data-ttu-id="1a0a2-197">JPN</span><span class="sxs-lookup"><span data-stu-id="1a0a2-197">JPN</span></span> |
|<span data-ttu-id="1a0a2-198">Республика Корея</span><span class="sxs-lookup"><span data-stu-id="1a0a2-198">Korea</span></span> |<span data-ttu-id="1a0a2-199">KOR</span><span class="sxs-lookup"><span data-stu-id="1a0a2-199">KOR</span></span> |
|<span data-ttu-id="1a0a2-200">Соединенное Королевство</span><span class="sxs-lookup"><span data-stu-id="1a0a2-200">United Kingdom</span></span> |<span data-ttu-id="1a0a2-201">GBR</span><span class="sxs-lookup"><span data-stu-id="1a0a2-201">GBR</span></span> |
|<span data-ttu-id="1a0a2-202">США</span><span class="sxs-lookup"><span data-stu-id="1a0a2-202">United States</span></span> |<span data-ttu-id="1a0a2-203">NAM</span><span class="sxs-lookup"><span data-stu-id="1a0a2-203">NAM</span></span> |

<span data-ttu-id="1a0a2-p118">**Примечание**: свойства **PreferredDataLocation** и **MailboxRegion** являются строками с без проверки ошибок. Если ввести недопустимое значение (например, NAN) почтовый ящик будет помещен в географически по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="1a0a2-p118">**Note**: The **PreferredDataLocation** and **MailboxRegion** properties are strings with no error checking. If you enter an invalid value (for example, NAN) the mailbox will be placed in the default Geo.</span></span>

### <a name="view-the-available-geos-that-are-configured-in-your-exchange-online-organization"></a><span data-ttu-id="1a0a2-206">Просмотр доступных Geos, настроенных в организации Exchange Online</span><span class="sxs-lookup"><span data-stu-id="1a0a2-206">View the available Geos that are configured in your Exchange Online organization</span></span>
<span data-ttu-id="1a0a2-207">Чтобы просмотреть список настроенных Geos в организации Exchange Online, выполните следующую команду в Exchange Online PowerShell:</span><span class="sxs-lookup"><span data-stu-id="1a0a2-207">To see the list of configured Geos in your Exchange Online organization, run the following command in Exchange Online PowerShell:</span></span>

```
Get-OrganizationConfig | Select -ExpandProperty AllowedMailboxRegions | Format-Table
```

<span data-ttu-id="1a0a2-208">Выходные данные команды выглядят так:</span><span class="sxs-lookup"><span data-stu-id="1a0a2-208">The output of the command looks like this:</span></span>

```
APC
AUS
CAN
EUR
FRA
GBR
JPN
KOR
NAM
```

### <a name="view-the-default-geo-for-your-exchange-online-organization"></a><span data-ttu-id="1a0a2-209">Представление по умолчанию географически для организации Exchange Online</span><span class="sxs-lookup"><span data-stu-id="1a0a2-209">View the default Geo for your Exchange Online organization</span></span>
<span data-ttu-id="1a0a2-210">Чтобы просмотреть географически по умолчанию из организации Exchange Online, выполните следующую команду в Exchange Online PowerShell:</span><span class="sxs-lookup"><span data-stu-id="1a0a2-210">To view the default geo of your Exchange Online organization, run the following command in Exchange Online PowerShell:</span></span>

```
Get-OrganizationConfig | Select DefaultMailboxRegion
```

<span data-ttu-id="1a0a2-211">Выходные данные команды выглядят так:</span><span class="sxs-lookup"><span data-stu-id="1a0a2-211">The output of the command looks like this:</span></span>

```
DefaultMailboxRegion
--------------------
NAM
```


### <a name="find-the-geo-location-of-a-mailbox"></a><span data-ttu-id="1a0a2-212">Поиск расположения географически почтового ящика</span><span class="sxs-lookup"><span data-stu-id="1a0a2-212">Find the Geo location of a mailbox</span></span>
<span data-ttu-id="1a0a2-213">Командлет **Get-Mailbox** в Exchange Online PowerShell отображает следующие multi географически связанных свойств почтовых ящиков:</span><span class="sxs-lookup"><span data-stu-id="1a0a2-213">The **Get-Mailbox** cmdlet in Exchange Online PowerShell displays the following multi-geo related properties on mailboxes:</span></span>

- <span data-ttu-id="1a0a2-p119">**Базы данных**: сначала 3 букв имя базы данных соответствующие код географически, который сообщает о том, где в настоящее время находится почтовый ящик. Свойство должно использоваться для почтовых ящиков Online архив **ArchiveDatabase** .</span><span class="sxs-lookup"><span data-stu-id="1a0a2-p119">**Database**: The first 3 letters of the database name correspond to the Geo code, which tells you where the mailbox is currently located. For Online Archive Mailboxes the **ArchiveDatabase** property should be used.</span></span>

- <span data-ttu-id="1a0a2-216">**MailboxRegion**: Определяет код географически расположение, которое было задано администратором (синхронизируются из **PreferredDataLocation** в Azure AD).</span><span class="sxs-lookup"><span data-stu-id="1a0a2-216">**MailboxRegion**: Specifies the geo location code that was set by the admin (synchronized from **PreferredDataLocation** in Azure AD).</span></span>

- <span data-ttu-id="1a0a2-217">**MailboxRegionLastUpdateTime**: Указывает, когда MailboxRegion последнего обновления (автоматически или вручную).</span><span class="sxs-lookup"><span data-stu-id="1a0a2-217">**MailboxRegionLastUpdateTime**: Indicates when MailboxRegion was last updated (either automatically or manually).</span></span>

<span data-ttu-id="1a0a2-218">Чтобы увидеть эти свойства почтового ящика, используйте следующий синтаксис:</span><span class="sxs-lookup"><span data-stu-id="1a0a2-218">To see these properties for a mailbox, use the following syntax:</span></span>

```
Get-Mailbox -Identity <MailboxIdentity> | Format-List Database,MailboxRegion*
```

<span data-ttu-id="1a0a2-219">Например для просмотра сведений географически для chris@contoso.onmicrosoft.com почтовых ящиков, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="1a0a2-219">For example, to see the Geo information for the mailbox chris@contoso.onmicrosoft.com, run the following command:</span></span>

```
Get-Mailbox -Identity chris@contoso.onmicrosoft.com | Format-List Database, MailboxRegion*
```

<span data-ttu-id="1a0a2-220">Выходные данные команды выглядят так:</span><span class="sxs-lookup"><span data-stu-id="1a0a2-220">The output of the command looks like this:</span></span>

```
Database                    : EURPR03DG077-db007 
MailboxRegion               : EUR 
MailboxRegionLastUpdateTime : 2/6/2018 8:21:01 PM 
```

> <span data-ttu-id="1a0a2-221">**Примечание:** Если код geo в имя базы данных не соответствует **MailboxRegion** значение, почтовый ящик будет автоматически быть помещены в очередь перемещения и переместить в географически место, указанное значение **MailboxRegion** (Exchange Online выполняет поиск Несоответствие между значениями свойств).</span><span class="sxs-lookup"><span data-stu-id="1a0a2-221">**Note:** If the geo location code in the database name doesn't match **MailboxRegion** value, the mailbox will be automatically be put into a relocation queue and moved to the geo location specified by the **MailboxRegion** value (Exchange Online looks for a mismatch between these property values).</span></span>

### <a name="move-an-existing-cloud-only-mailbox-to-a-specific-geo"></a><span data-ttu-id="1a0a2-222">Перемещение к определенным Geo существующего почтового ящика только в облаке</span><span class="sxs-lookup"><span data-stu-id="1a0a2-222">Move an existing cloud-only mailbox to a specific Geo</span></span>
<span data-ttu-id="1a0a2-p120">Только в облаке пользователь — это пользователь не представлением для клиента с помощью AAD подключение. Этот пользователь был создан непосредственно в Azure AD. Используйте командлеты **Get-MsolUser** и **Set-MsolUser** в модуля Azure AD для Windows PowerShell, чтобы просмотреть или задать географически, где будет храниться только в облаке почтового ящика пользователя.</span><span class="sxs-lookup"><span data-stu-id="1a0a2-p120">A cloud-only user is a user not syncrhonized to the tenant via AAD Connect. This user was created directly in Azure AD. Use the **Get-MsolUser** and **Set-MsolUser** cmdlets in the Azure AD Module for Windows PowerShell to view or specify the Geo where a cloud-only user's mailbox will be stored.</span></span>

<span data-ttu-id="1a0a2-226">Чтобы просмотреть значение **PreferredDataLocation** для пользователя, используйте следующий синтаксис в Windows Azure AD PowerShell:</span><span class="sxs-lookup"><span data-stu-id="1a0a2-226">To view the **PreferredDataLocation** value for a user, use this syntax in Azure AD PowerShell:</span></span>

```
Get-MsolUser -UserPrincipalName <UserPrincipalName> | Format-List UserPrincipalName,PreferredDataLocation
```

<span data-ttu-id="1a0a2-227">Например чтобы просмотреть значение **PreferredDataLocation** для michelle@contoso.onmicrosoft.com пользователя, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="1a0a2-227">For example, to see the **PreferredDataLocation** value for the user michelle@contoso.onmicrosoft.com, run the following command:</span></span>

```
Get-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com | Format-List
```

<span data-ttu-id="1a0a2-228">Выходные данные команды выглядят так:</span><span class="sxs-lookup"><span data-stu-id="1a0a2-228">The output of the command looks like this:</span></span>

```
UserPrincipalName     : michelle@contoso.onmicrosoft.com
PreferredDataLocation : EUR
```

<span data-ttu-id="1a0a2-229">Чтобы изменить значение **PreferredDataLocation** для объекта пользователя только в облаке, используйте следующий синтаксис в Windows Azure AD PowerShell:</span><span class="sxs-lookup"><span data-stu-id="1a0a2-229">To modify the **PreferredDataLocation** value for a cloud-only user object, use the following syntax in Azure AD PowerShell:</span></span>

``` 
Set-MsolUser -UserPrincipalName <UserPrincipalName> -PreferredDataLocation <GeoCode>
```

<span data-ttu-id="1a0a2-230">Например чтобы задать значение **PreferredDataLocation** географически Европейский союз (ЕВРО) для michelle@contoso.onmicrosoft.com пользователя, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="1a0a2-230">For example, to set the **PreferredDataLocation** value to the European Union (EUR) geo for the user michelle@contoso.onmicrosoft.com, run the following command:</span></span>

``` 
Set-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com -PreferredDataLocation EUR
```

<span data-ttu-id="1a0a2-231">**Примечания.**</span><span class="sxs-lookup"><span data-stu-id="1a0a2-231">**Notes**:</span></span>

- <span data-ttu-id="1a0a2-p121">Как упоминалось ранее нельзя использовать эту процедуру для объектов-синхронизированных пользователей из локального Active Directory. Необходимо изменить значение **PreferredDataLocation** , с помощью AAD подключение. Дополнительные сведения можно [Azure Active Directory подключение синхронизации: Настройка предпочитаемого данных расположения для ресурсов Office 365](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span><span class="sxs-lookup"><span data-stu-id="1a0a2-p121">As mentioned previously you cannot use this procedure for synchronized user objects from on-premises Active Directory. You need to change the **PreferredDataLocation** value using AAD Connect. For more information, see [Azure Active Directory Connect sync: Configure preferred data location for Office 365 resources](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span></span> 

- <span data-ttu-id="1a0a2-235">Сколько времени занимает о перемещении mailboxfrom его текущего geo в новом расположении желаемую географически зависит от нескольких факторов:</span><span class="sxs-lookup"><span data-stu-id="1a0a2-235">How long it takes to relocate a mailboxfrom its current geo to the new desired geo location depends on several factors:</span></span>
 
  - <span data-ttu-id="1a0a2-236">Размер и тип почтового ящика.</span><span class="sxs-lookup"><span data-stu-id="1a0a2-236">The size and type of mailbox.</span></span>
 
  - <span data-ttu-id="1a0a2-237">Количество происходит перемещение почтовых ящиков.</span><span class="sxs-lookup"><span data-stu-id="1a0a2-237">The number of mailboxes being moved.</span></span>
 
  - <span data-ttu-id="1a0a2-238">Доступность ресурсов перемещения.</span><span class="sxs-lookup"><span data-stu-id="1a0a2-238">The availability of move resources.</span></span>

#### <a name="move-disabled-mailboxes-that-are-on-litigation-hold"></a><span data-ttu-id="1a0a2-239">Перемещение почтовых ящиков на хранение для судебного разбирательства этот параметр отключен</span><span class="sxs-lookup"><span data-stu-id="1a0a2-239">Move disabled mailboxes that are on Litigation Hold</span></span>
<span data-ttu-id="1a0a2-p122">Этот параметр отключен почтовых ящиков на хранение для судебного разбирательства, сохраняются для обнаружения электронных данных, которые целей, нельзя перемещать, изменяя их значение **PreferredDataLocation** в отключенном состоянии. Чтобы переместить отключенного почтового ящика на хранение для судебного разбирательства:</span><span class="sxs-lookup"><span data-stu-id="1a0a2-p122">Disabled mailboxes on Litigation Hold that are preserved for eDiscovery purposes cannot be moved by changing their **PreferredDataLocation** value in their disabled state. To move a disabled mailbox on litigation hold:</span></span>

1. <span data-ttu-id="1a0a2-242">Временно назначьте почтовому ящику лицензию.</span><span class="sxs-lookup"><span data-stu-id="1a0a2-242">Temporarily assign a license to the mailbox.</span></span>

2. <span data-ttu-id="1a0a2-243">Измените **PreferredDataLocation**.</span><span class="sxs-lookup"><span data-stu-id="1a0a2-243">Change the **PreferredDataLocation**.</span></span>

3. <span data-ttu-id="1a0a2-244">Удалите лицензии из почтового ящика после его были перемещены для выбранного географического расположения верните его в отключенном состоянии.</span><span class="sxs-lookup"><span data-stu-id="1a0a2-244">Remove the license from the mailbox after it has been moved to the selected geo location to put it back into the disabled state.</span></span>

### <a name="create-new-cloud-mailboxes-in-a-specific-geo"></a><span data-ttu-id="1a0a2-245">Создание новых облачных почтовых ящиков в конкретных географически</span><span class="sxs-lookup"><span data-stu-id="1a0a2-245">Create new cloud mailboxes in a specific Geo</span></span> 
<span data-ttu-id="1a0a2-246">Чтобы создать новый почтовый ящик в конкретных географического расположения, необходимо выполнить одно из следующих действий:</span><span class="sxs-lookup"><span data-stu-id="1a0a2-246">To create a new mailbox in a specific geo location, you need to do either of these steps:</span></span>

- <span data-ttu-id="1a0a2-p123">Настройте значение **PreferredDataLocation** , как описано в предыдущем разделе *перед* создания почтового ящика в Exchange Online. К примеру настройте значение **PreferredDataLocation** пользователя перед назначение лицензии.</span><span class="sxs-lookup"><span data-stu-id="1a0a2-p123">Configure the **PreferredDataLocation** value as described in the previous section *before* the mailbox is created in Exchange Online. For example, configure the **PreferredDataLocation** value on a user before assigning a license.</span></span> 

- <span data-ttu-id="1a0a2-249">Назначение лицензии в то же время, задайте значение **PreferredDataLocation** .</span><span class="sxs-lookup"><span data-stu-id="1a0a2-249">Assign a license at the same time you set the **PreferredDataLocation** value.</span></span>

<span data-ttu-id="1a0a2-250">Для создания нового только в облаке лицензированных пользователей (не AAD подключение синхронизации) в определенных географически, используйте следующий синтаксис в Windows Azure AD PowerShell:</span><span class="sxs-lookup"><span data-stu-id="1a0a2-250">To create a new cloud-only licensed user (not AAD Connect synchronized) in a specific Geo, use the following syntax in Azure AD PowerShell:</span></span>

```
New-MsolUser -UserPrincipalName <UserPrincipalName> -DisplayName "<Display Name>" [-FirstName <FirstName>] [-LastName <LastName>] [-Password <Password>] [-LicenseAssignment <AccountSkuId>] -PreferredDataLocation <GeoCode> 
```
<span data-ttu-id="1a0a2-251">В этом примере Создание учетной записи пользователя для Brunner Александру со следующими значениями:</span><span class="sxs-lookup"><span data-stu-id="1a0a2-251">This example create a new user account for Elizabeth Brunner with the following values:</span></span>

- <span data-ttu-id="1a0a2-252">Имя участника-пользователя: ebrunner@contoso.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="1a0a2-252">User principal name: ebrunner@contoso.onmicrosoft.com</span></span>

- <span data-ttu-id="1a0a2-253">Имя: Александру</span><span class="sxs-lookup"><span data-stu-id="1a0a2-253">First name: Elizabeth</span></span>

- <span data-ttu-id="1a0a2-254">Фамилия: Brunner</span><span class="sxs-lookup"><span data-stu-id="1a0a2-254">Last name: Brunner</span></span>

- <span data-ttu-id="1a0a2-255">Отображаемое имя Brunner Александру</span><span class="sxs-lookup"><span data-stu-id="1a0a2-255">Display name Elizabeth Brunner</span></span>

- <span data-ttu-id="1a0a2-256">Пароль: случайным образом полученное и отображаются в результатах команды (так как не используется параметр *Password* )</span><span class="sxs-lookup"><span data-stu-id="1a0a2-256">Password: randomly-generated and shown in the results of the command (because we're not using the *Password* parameter)</span></span>

- <span data-ttu-id="1a0a2-257">Лицензия: contoso:ENTERPRISEPREMIUM (E5)</span><span class="sxs-lookup"><span data-stu-id="1a0a2-257">License: contoso:ENTERPRISEPREMIUM (E5)</span></span>

- <span data-ttu-id="1a0a2-258">Расположение: Австралия (Стандартное)</span><span class="sxs-lookup"><span data-stu-id="1a0a2-258">Location: Australia (AUS)</span></span>

```
New-MsolUser -UserPrincipalName ebrunner@contoso.onmicrosoft.com -DisplayName "Elizabeth Brunner" -FirstName Elizabeth -LastName Brunner -LicenseAssignment contoso:ENTERPRISEPREMIUM -PreferredDataLocation AUS
```

<span data-ttu-id="1a0a2-259">Дополнительные сведения о создании новых учетных записей пользователей и поиск значения LicenseAssignment в Windows Azure AD PowerShell можно [Создать учетные записи пользователей с Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell) и [Просмотр лицензий и службы с помощью Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/view-licenses-and-services-with-office-365-powershell).</span><span class="sxs-lookup"><span data-stu-id="1a0a2-259">For more information about creating new user accounts and finding LicenseAssignment values in Azure AD PowerShell, see [Create user accounts with Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell) and [View licenses and services with Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/view-licenses-and-services-with-office-365-powershell).</span></span>

> <span data-ttu-id="1a0a2-p124">**Примечание:** Если вы используете Exchange Online PowerShell для включения почтового ящика и необходимости почтового ящика будет создан непосредственно в географически, который указан в **PreferredDataLocation**, необходимо использовать Exchange Online командлета, такие как **Enable-Mailbox** или \*\*New-Mailbox \*\*непосредственно к облачной службе. При использовании командлета **Enable-RemoteMailbox** в локальной Exchange, почтовый ящик будет создан в географически по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="1a0a2-p124">**Note:** If you are using Exchange Online PowerShell to enable a mailbox and need the mailbox to be created directly in the Geo that's specified in **PreferredDataLocation**, you need to use an Exchange Online cmdlet such as **Enable-Mailbox** or **New-Mailbox** directly against the cloud service. If you use the **Enable-RemoteMailbox** on-premises Exchange cmdlet, the mailbox will be created in the default Geo.</span></span>

### <a name="onboard-existing-on-premises-mailboxes-in-a-specific-geo"></a><span data-ttu-id="1a0a2-262">Встроенный существующих локальных почтовых ящиков в конкретных географически</span><span class="sxs-lookup"><span data-stu-id="1a0a2-262">Onboard existing on-premises mailboxes in a specific Geo</span></span>
<span data-ttu-id="1a0a2-263">Можно использовать стандартный входящая средства и процедуры для переноса почтовых ящиков из локальной организации Exchange в Exchange Online, включая панели [мониторинга миграции в центре администрирования Exchange](https://support.office.com/article/d164b35c-f624-4f83-ac58-b7cae96ab331)и командлет [New-MigrationBatch](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-migrationbatch) в Exchange Online PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1a0a2-263">You can use the standard onboarding tools and processes to migrate a mailbox from an on-premises Exchange organization to Exchange Online, including the [Migration dashboard in the EAC](https://support.office.com/article/d164b35c-f624-4f83-ac58-b7cae96ab331), and the [New-MigrationBatch](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-migrationbatch) cmdlet in Exchange Online PowerShell.</span></span>

<span data-ttu-id="1a0a2-p125">Первым этапом является убедитесь, что существует объект пользователя для каждого почтового ящика быть onboarded и убедитесь, что правильное значение **PreferredDataLocation** , используемых в Azure AD. Средства адаптация новых сотрудников будут использовать значение **PreferredDataLocation** и будет перенос почтовых ящиков непосредственно в указанный географически.</span><span class="sxs-lookup"><span data-stu-id="1a0a2-p125">The first step is to verify a user object exists for each mailbox to be onboarded, and verify the correct **PreferredDataLocation** value is configured in Azure AD. The onboarding tools will respect the **PreferredDataLocation** value and will migrate the mailboxes directly to the specified Geo.</span></span>

<span data-ttu-id="1a0a2-266">Или можно использовать следующие шаги для встроенных почтовых ящиков непосредственно в конкретных географического расположения, с помощью командлета [New-MoveRequest](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-moverequest) в Exchange Online PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1a0a2-266">Or, you can use the following steps to onboard mailboxes directly in a specific geo location using the [New-MoveRequest](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-moverequest) cmdlet in Exchange Online PowerShell.</span></span>

1. <span data-ttu-id="1a0a2-p126">Убедитесь, что существует объект пользователя для каждого почтового ящика onboarded и **PreferredDataLocation** имеет значение необходимого значения в Azure AD. Значение **PreferredDataLocation** синхронизируются с атрибутом **MailboxRegion** соответствующего объекта пользователя почты в Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="1a0a2-p126">Verify the user object exists for each mailbox to be onboarded and that **PreferredDataLocation** is set to the desired value in Azure AD. The value of **PreferredDataLocation** will be synchronized to the **MailboxRegion** attribute of the corresponding mail user object in Exchange Online.</span></span>

2. <span data-ttu-id="1a0a2-269">Напрямую подключаться к определенным вспомогательных географически, с помощью инструкций по подключению из данного раздела.</span><span class="sxs-lookup"><span data-stu-id="1a0a2-269">Connect directly to the specific satellite Geo using the connection instructions from earlier in this topic.</span></span>

3. <span data-ttu-id="1a0a2-270">В Exchange Online PowerShell хранение учетных данных администратора в локальной, которые используются для выполнения миграции почтовых ящиков в переменную, выполнив следующую команду:</span><span class="sxs-lookup"><span data-stu-id="1a0a2-270">In Exchange Online PowerShell, store the on-premises administrator credentials that's used to perform a mailbox migration in a variable by running the following command:</span></span>

    ```
    $RC = Get-Credential
    ```

4. <span data-ttu-id="1a0a2-271">В Exchange Online PowerShell создайте новый **New-MoveRequest** аналогичные следующим образом:</span><span class="sxs-lookup"><span data-stu-id="1a0a2-271">In Exchange Online PowerShell, create a new **New-MoveRequest** similar to the following example:</span></span> 

    ```
    New-MoveRequest -Remote -RemoteHostName mail.contoso.com -RemoteCredential $RC -Identity user@contoso.com -TargetDeliveryDomain <YourAppropriateDomain>
    ```

5. <span data-ttu-id="1a0a2-272">Повторите шаг #4 для всех почтовых ящиков, необходимые для переноса из локального сервера Exchange в расположение вспомогательных в настоящее время связаны с.</span><span class="sxs-lookup"><span data-stu-id="1a0a2-272">Repeat step #4 for every mailbox you need to migrate from on-premises Exchange to the satellite location you are currently connected to.</span></span>

6. <span data-ttu-id="1a0a2-273">Если необходимо перенести дополнительные почтовые ящики в различных вспомогательных расположение, повторите шаги с 2 по 4 для каждого конкретного вспомогательных расположения.</span><span class="sxs-lookup"><span data-stu-id="1a0a2-273">If you need to migrate additional mailboxes to a different satellite location, repeat steps 2 through 4 for each specific satellite location.</span></span>

### <a name="multi-geo-reporting"></a><span data-ttu-id="1a0a2-274">Ферма с несколькими географически отчетов</span><span class="sxs-lookup"><span data-stu-id="1a0a2-274">Multi-Geo Reporting</span></span>
<span data-ttu-id="1a0a2-p127">**Отчеты об использовании несколькими Geo** в центре администрирования Office 365 отображает число пользователей, географического расположения. Отчет отображает рассылки пользователя для текущего месяца и предоставляет статистические данные за последние 6 месяцев.</span><span class="sxs-lookup"><span data-stu-id="1a0a2-p127">**Multi-Geo Usage Reports** in the Office 365 admin center displays the user count by geo location. The report displays user distribution for the current month and provides historical data for the past 6 months.</span></span>
