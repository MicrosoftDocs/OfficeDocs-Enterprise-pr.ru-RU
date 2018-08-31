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
ms.openlocfilehash: 9834b102365f11623a1decc00460f85f36552ccb
ms.sourcegitcommit: d88307a32fd3439a09a87b260e0c0cf9074ebeb0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/16/2018
ms.locfileid: "22914784"
---
# <a name="multi-geo-capabilities-in-exchange-online"></a><span data-ttu-id="9eaa0-103">Ферма с несколькими географически возможности в Exchange Online</span><span class="sxs-lookup"><span data-stu-id="9eaa0-103">Multi-Geo Capabilities in Exchange Online</span></span>

<span data-ttu-id="9eaa0-p101">Одним клиентом охватывать разных географических местоположениях (Geos) предоставляют возможности несколькими Geo в Office 365. При включении географически ферма с несколькими клиентами можно выбрать расположение содержимого почтового ящика, Exchange Online (статических данных) на уровне пользователя.</span><span class="sxs-lookup"><span data-stu-id="9eaa0-p101">Multi-Geo Capabilities in Office 365 enable a single tenant to span multiple geographic locations (Geos). When Multi-Geo is enabled, customers can select the location of Exchange Online mailbox content (data at rest) on a per-user basis.</span></span>

<span data-ttu-id="9eaa0-p102">Расположение начальной клиента (называется «default» или «централизованно») определяет, какие на основании адрес для выставления счетов. При включении несколькими географически почтовые ящики можно поместить в расположениях Дополнительные «сопутствующие» по:</span><span class="sxs-lookup"><span data-stu-id="9eaa0-p102">Your initial tenant location (referred to as your "default" or "central" location) is determined based on your billing address. When Multi-Geo is enabled, you can place mailboxes in additional "satellite" locations by:</span></span>

- <span data-ttu-id="9eaa0-108">Создание нового почтового ящика Exchange Online напрямую в вспомогательной.</span><span class="sxs-lookup"><span data-stu-id="9eaa0-108">Creating a new Exchange Online mailbox directly in a satellite.</span></span>

- <span data-ttu-id="9eaa0-109">Перемещение существующего почтового ящика Exchange Online в вспомогательной.</span><span class="sxs-lookup"><span data-stu-id="9eaa0-109">Moving an existing Exchange Online mailbox into a satellite.</span></span>

- <span data-ttu-id="9eaa0-110">Адаптация новых сотрудников почтовых ящиков из локальной организации Exchange непосредственно в вспомогательной.</span><span class="sxs-lookup"><span data-stu-id="9eaa0-110">Onboarding a mailbox from an on-premises Exchange organization directly into a satellite.</span></span>

<span data-ttu-id="9eaa0-111">Для использования в конфигурации с несколькими географически доступны следующие Geos:</span><span class="sxs-lookup"><span data-stu-id="9eaa0-111">The following Geos are available for use in a Multi-Geo configuration:</span></span>

- <span data-ttu-id="9eaa0-112">Азиатско-Тихоокеанский регион</span><span class="sxs-lookup"><span data-stu-id="9eaa0-112">Asia Pacific</span></span>

- <span data-ttu-id="9eaa0-113">Австралия</span><span class="sxs-lookup"><span data-stu-id="9eaa0-113">Australia</span></span>

- <span data-ttu-id="9eaa0-114">Канада</span><span class="sxs-lookup"><span data-stu-id="9eaa0-114">Canada</span></span>

- <span data-ttu-id="9eaa0-115">Европейский Союз</span><span class="sxs-lookup"><span data-stu-id="9eaa0-115">European Union</span></span>

- <span data-ttu-id="9eaa0-116">Франция</span><span class="sxs-lookup"><span data-stu-id="9eaa0-116">France</span></span>

- <span data-ttu-id="9eaa0-117">Индия (в настоящее время доступны только для клиентов с адреса для выставления счета в Индии)</span><span class="sxs-lookup"><span data-stu-id="9eaa0-117">India (currently only available to customers with billing addresses in India)</span></span>

- <span data-ttu-id="9eaa0-118">Япония</span><span class="sxs-lookup"><span data-stu-id="9eaa0-118">Japan</span></span>

- <span data-ttu-id="9eaa0-119">Республика Корея</span><span class="sxs-lookup"><span data-stu-id="9eaa0-119">Korea</span></span>

- <span data-ttu-id="9eaa0-120">Соединенное Королевство</span><span class="sxs-lookup"><span data-stu-id="9eaa0-120">United Kingdom</span></span>

- <span data-ttu-id="9eaa0-121">США</span><span class="sxs-lookup"><span data-stu-id="9eaa0-121">United States</span></span>

## <a name="prerequisite-configuration"></a><span data-ttu-id="9eaa0-122">Предварительные настройки</span><span class="sxs-lookup"><span data-stu-id="9eaa0-122">Prerequisite configuration</span></span>
<span data-ttu-id="9eaa0-p103">Прежде чем начать, используя возможности несколькими географически в Exchange Online, корпорации Майкрософт необходимо настроить клиент Exchange Online для поддержки различных географически. Этот процесс однократного конфигурации запускается после упорядочивании несколькими географически и лицензий, которые отображаются в наших клиентов. Этот процесс однократного конфигурации обычно занимает меньше, чем 30 дней.</span><span class="sxs-lookup"><span data-stu-id="9eaa0-p103">Before you can start using Multi-Geo capabilities in Exchange Online, Microsoft needs to configure your Exchange Online tenant for Multi-Geo support. This one-time configuration process is triggered after you order Multi-Geo and the licenses show up in our tenant. This one-time configuration process should typically take less than 30 days to complete.</span></span>

<span data-ttu-id="9eaa0-p104">Вы будете получать уведомления в [Центр сообщений Office 365](https://support.office.com/article/Message-center-in-Office-365-38FB3333-BFCC-4340-A37B-DEDA509C2093) после завершения настройки. Конфигурация будет запущен автоматически после лицензии несколькими географически отображаются в вашего клиента.</span><span class="sxs-lookup"><span data-stu-id="9eaa0-p104">You'll receive notifications in the [Office 365 message center](https://support.office.com/article/Message-center-in-Office-365-38FB3333-BFCC-4340-A37B-DEDA509C2093) when your configuration has completed. Configuration is automatically triggered once your Multi-Geo licenses show up in your tenant.</span></span>

## <a name="mailbox-placement-and-moves"></a><span data-ttu-id="9eaa0-128">Расположение почтового ящика и перемещений</span><span class="sxs-lookup"><span data-stu-id="9eaa0-128">Mailbox placement and moves</span></span>
<span data-ttu-id="9eaa0-129">По завершении предварительные действия конфигурации несколькими географически Microsoft Exchange Online будет поддерживать атрибут **PreferredDataLocation** для объектов-пользователей в Azure AD.</span><span class="sxs-lookup"><span data-stu-id="9eaa0-129">After Microsoft completes the prerequisite Multi-Geo configuration steps, Exchange Online will honor the **PreferredDataLocation** attribute on user objects in Azure AD.</span></span>

<span data-ttu-id="9eaa0-p105">Exchange Online синхронизирует свойство **PreferredDataLocation** из Azure AD в свойство **MailboxRegion** в службе каталогов Exchange Online. Значение **MailboxRegion** определяет географически, где будет помещен почтовых ящиков пользователей и все связанные архивные почтовые ящики. Настройка основного почтового ящика и архивирование почтовых ящиков пользователей могут располагаться в разных Geos невозможна. Только один географически можно настроить для каждого объекта-пользователя.</span><span class="sxs-lookup"><span data-stu-id="9eaa0-p105">Exchange Online synchronizes the **PreferredDataLocation** property from Azure AD into the **MailboxRegion** property in the Exchange Online directory service. The value of **MailboxRegion** determines the Geo where user mailboxes and any associated archive mailboxes will be placed. It is not possible to configure a user's primary mailbox and archive mailboxes to reside in different Geos. Only one Geo may be configured per user object.</span></span>

- <span data-ttu-id="9eaa0-134">При настройке **PreferredDataLocation** на пользователя с помощью существующего почтового ящика почтового ящика будут помещены в очередь перемещения и автоматическое перемещение в указанном географически.</span><span class="sxs-lookup"><span data-stu-id="9eaa0-134">When **PreferredDataLocation** is configured on a user with an existing mailbox, the mailbox will be put into a relocation queue and automatically moved to the specified Geo.</span></span> 

- <span data-ttu-id="9eaa0-135">Когда **PreferredDataLocation** настроен на пользователя, не существующего почтового ящика, почтовый ящик будет выполнена подготовка в указанном географически.</span><span class="sxs-lookup"><span data-stu-id="9eaa0-135">When **PreferredDataLocation** is configured on a user without an existing mailbox, the mailbox will be provisioned into the specified Geo.</span></span> 

- <span data-ttu-id="9eaa0-136">При **PreferredDataLocation** не указан на пользователя, почтовый ящик будет помещен в географически по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="9eaa0-136">When **PreferredDataLocation** is not specified on a user, the mailbox will be placed in the default Geo.</span></span>

- <span data-ttu-id="9eaa0-137">Если код **PreferredDataLocation** неверен (например тип NAN вместо им), почтовый ящик будет помещен в географически по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="9eaa0-137">If the **PreferredDataLocation** code is incorrect (e.g. a type of NAN instead of NAM), the mailbox will be placed in the default Geo.</span></span>

<span data-ttu-id="9eaa0-p106">**Примечание**: несколькими географически возможности и Скайп для бизнеса на региональном уровнях размещенных собрания по сети обоих используйте свойство **PreferredDataLocation** на объектов-пользователей для обнаружения служб. Если вы настраиваете **PreferredDataLocation** значения для объектов-пользователей на региональном уровнях размещенной собраний, почтовых ящиков для этих пользователей автоматически перемещается в указанный географически после включения несколькими географически на клиента Office 365.</span><span class="sxs-lookup"><span data-stu-id="9eaa0-p106">**Note**: Multi-Geo capabilities and Skype for Business Online regionally hosted meetings both use the **PreferredDataLocation** property on user objects to locate services. If you configure **PreferredDataLocation** values on user objects for regionally hosted meetings, the mailbox for those users will be automatically moved to the specified Geo after Multi-Geo is enabled on the Office 365 tenant.</span></span>

## <a name="feature-limitations-for-multi-geo-in-exchange-online"></a><span data-ttu-id="9eaa0-140">Ограничения для нескольких Geo в Exchange Online</span><span class="sxs-lookup"><span data-stu-id="9eaa0-140">Feature limitations for Multi-Geo in Exchange Online</span></span>
1. <span data-ttu-id="9eaa0-p107">Ферма с несколькими географически возможности поддержки только почтовые ящики пользователей, почтовые ящики ресурса (почтовые ящики оборудования и помещений) и общие почтовые ящики. Общедоступные папки почтовых ящиков и групп Office 365 оставаться в географически Домашняя страница клиента.</span><span class="sxs-lookup"><span data-stu-id="9eaa0-p107">Only user mailboxes, resource mailboxes (room and equipment mailboxes), and shared mailboxes support Multi-Geo features. Public Folder Mailboxes and Office 365 Groups remain in the customer's home Geo.</span></span>
 
2. <span data-ttu-id="9eaa0-p108">Безопасность и соответствие требованиям функции (например, аудит и обнаружения электронных данных), доступные в центре администрирования Exchange (EAC) не доступны в географически нескольких организаций. Вместо этого необходимо использовать для настройки функций безопасности и соответствия требованиям в [Office 365 безопасности & центре соответствия требованиям](https://support.office.com/article/7e696a40-b86b-4a20-afcc-559218b7b1b8) .</span><span class="sxs-lookup"><span data-stu-id="9eaa0-p108">Security and compliance features (for example, auditing and eDiscovery) that are available in the Exchange admin center (EAC) aren't available in Multi-Geo organizations. Instead, you need to use the [Office 365 Security & Compliance Center](https://support.office.com/article/7e696a40-b86b-4a20-afcc-559218b7b1b8) to configure security and compliance features.</span></span>

3. <span data-ttu-id="9eaa0-p109">Outlook для Mac пользователей могут возникнуть кратковременной потере доступа к их папки серверный архив при перемещении их почтовых ящиков для новых географически. Это условие возникает, когда пользователя основной и архивные почтовые ящики находятся в разных Geos, так как перемещение почтовых ящиков между географически может завершиться в разное время.</span><span class="sxs-lookup"><span data-stu-id="9eaa0-p109">Outlook for Mac users may experience a temporary loss of access to their Online Archive folder while you move their mailbox to a new Geo. This condition occurs when the user's the primary and archive mailboxes are in different Geos, because cross-Geo mailbox moves may complete at different times.</span></span>

4. <span data-ttu-id="9eaa0-p110">Пользователи не могут совместно использоваться Geos в Outlook в Интернете (ранее известных как Outlook Web App или OWA) *папки почтовых ящиков* . Например пользователя в Европейском союзе нельзя использовать Outlook в Интернете для открытия общей папки в почтовом ящике, расположенного в США. Тем не менее Outlook на веб-пользователей можно открыть *другой почтовый ящик* в разных Geos с помощью отдельном окне браузера, как описано в [Открытие почтового ящика другого пользователя в отдельном окне браузера в Outlook Web App](https://support.office.com/article/A909AD30-E413-40B5-A487-0EA70B763081#__toc372210362).</span><span class="sxs-lookup"><span data-stu-id="9eaa0-p110">Users can't share *mailbox folders* across Geos in Outlook on the web (formerly known as Outlook Web App or OWA). For example, a user in the European Union can't use Outlook on the web to open a shared folder in a mailbox that's located in the United States. However, Outlook on the Web users can open *other mailboxes* in different Geos by using a separate browser window as described in [Open another person’s mailbox in a separate browser window in Outlook Web App](https://support.office.com/article/A909AD30-E413-40B5-A487-0EA70B763081#__toc372210362).</span></span>

    <span data-ttu-id="9eaa0-150">**Примечание**: географически нескольких почтовых ящиков общий доступ к папке, поддерживаемых в Outlook в Windows.</span><span class="sxs-lookup"><span data-stu-id="9eaa0-150">**Note**: Cross-Geo mailbox folder sharing is supported in Outlook on Windows.</span></span>

## <a name="administration"></a><span data-ttu-id="9eaa0-151">Администрирование</span><span class="sxs-lookup"><span data-stu-id="9eaa0-151">Administration</span></span> 
<span data-ttu-id="9eaa0-p111">Для просмотра и настройки свойства, связанные с Geo в вашей среде Office 365 требуется удаленной оболочки PowerShell. Сведения о различных моделей PowerShell, используемые для администрирования Office 365 содержатся в разделе [Управление Office 365 и Exchange Online с помощью Windows PowerShell](https://support.office.com//article/06a743bb-ceb6-49a9-a61d-db4ffdf54fa6).</span><span class="sxs-lookup"><span data-stu-id="9eaa0-p111">Remote PowerShell is required to view and configure Geo-related properties in your Office 365 environment. For information on various PowerShell modules used to administer Office 365, see [Managing Office 365 and Exchange Online with Windows PowerShell](https://support.office.com//article/06a743bb-ceb6-49a9-a61d-db4ffdf54fa6).</span></span>

- <span data-ttu-id="9eaa0-p112">Необходимо v1.1.166.0 [PowerShell модуле Microsoft Azure Active Directory](https://social.technet.microsoft.com/wiki/contents/articles/28552.microsoft-azure-active-directory-powershell-module-version-release-history.aspx) или более поздней версии в v1.x, чтобы просмотреть свойство **PreferredDataLocation** на объектов-пользователей. Синхронизация через подключение AAD в AAD объектов-пользователей не могут иметь напрямую изменить с помощью AAD PowerShell их **PreferredDataLocation** значение. С помощью AAD PowerShell может быть изменено объектов-пользователей только в облаке. Чтобы подключиться к Windows Azure AD PowerShell, обратитесь к разделу [подключение к Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell).</span><span class="sxs-lookup"><span data-stu-id="9eaa0-p112">You need the [Microsoft Azure Active Directory PowerShell Module](https://social.technet.microsoft.com/wiki/contents/articles/28552.microsoft-azure-active-directory-powershell-module-version-release-history.aspx) v1.1.166.0 or later in v1.x to see the **PreferredDataLocation** property on user objects. User objects synchronized via AAD Connect into AAD cannot have their **PreferredDataLocation** value directly modified via AAD PowerShell. Cloud-only user objects can be modified via AAD PowerShell. To connect to Azure AD PowerShell, see [Connect to Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell).</span></span> 

- <span data-ttu-id="9eaa0-158">Чтобы подключиться к Exchange Online PowerShell, обратитесь к разделу [подключение к Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).</span><span class="sxs-lookup"><span data-stu-id="9eaa0-158">To connect to Exchange Online PowerShell, see [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).</span></span> 

### <a name="connect-directly-to-a-specific-geo-using-exchange-online-powershell"></a><span data-ttu-id="9eaa0-159">Прямой звонок на конкретных географически с помощью Exchange Online PowerShell</span><span class="sxs-lookup"><span data-stu-id="9eaa0-159">Connect directly to a specific Geo using Exchange Online PowerShell</span></span>
<span data-ttu-id="9eaa0-p113">Как правило Exchange Online PowerShell будут подключаться к географически по умолчанию. Однако можно также подключиться напрямую к Geos не по умолчанию. Из-за повышение производительности мы рекомендуем путем прямого подключения географически не по умолчанию при только управление пользователями в этой географически.</span><span class="sxs-lookup"><span data-stu-id="9eaa0-p113">Typically, Exchange Online PowerShell will connect to the default Geo. But, you can also connect directly to non-default Geos. Because of performance improvements, we recommend connecting directly to the non-default Geo when you only manage users in that Geo.</span></span>

<span data-ttu-id="9eaa0-p114">Для подключения к определенным Geo параметра *ConnectionUri* отличается от инструкции регулярных подключения. Остальные команды и значения, совпадают. Порядок действий:</span><span class="sxs-lookup"><span data-stu-id="9eaa0-p114">To connect to a specific Geo, the *ConnectionUri* parameter is different than the regular connection instructions. The rest of the commands and values are the same. The steps are:</span></span>

1. <span data-ttu-id="9eaa0-166">На локальном компьютере откройте Windows PowerShell и выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="9eaa0-166">On your local computer, open Windows PowerShell and run the following command:</span></span>
    
    ```
    $UserCredential = Get-Credential
    ```
   <span data-ttu-id="9eaa0-167">В диалоговом окне **Запрос учетных данных Windows PowerShell** введите рабочий или школа учетной записи и пароль и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="9eaa0-167">In the **Windows PowerShell Credential Request** dialog box, type your work or school account and password, and then click **OK**.</span></span>
    
2. <span data-ttu-id="9eaa0-p115">Замените `<emailaddress>` с адресом электронной почты из **любой** почтовых ящиков в целевом географически и выполните следующую команду. Разрешения для почтового ящика и связь с свои учетные данные на шаге 1 не учитываются; адрес электронной почты просто сообщает Exchange Online where для подключения.</span><span class="sxs-lookup"><span data-stu-id="9eaa0-p115">Replace `<emailaddress>` with the email address of **any** mailbox in the target Geo and run the following command. Your permissions on the mailbox and the relationship to your credentials in Step 1 are not a factor; the email address simply tells Exchange Online where to connect.</span></span>
  
   ```
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=<emailaddress> -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```

   <span data-ttu-id="9eaa0-170">Например если olga@contoso.onmicrosoft.com является адресом электронной почты допустимый почтовый ящик в географически, чтобы подключиться, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="9eaa0-170">For example, if olga@contoso.onmicrosoft.com is the email address of a valid mailbox in the Geo you want to connect, run the following command:</span></span>

   ```
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=olga@contoso.onmicrosoft.com -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```
3. <span data-ttu-id="9eaa0-171">Выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="9eaa0-171">Run the following command:</span></span>
    
    ```
    Import-PSSession $Session
    ```

### <a name="azure-ad-connect-version-requirements"></a><span data-ttu-id="9eaa0-172">Требования относительно версий Azure AD подключение</span><span class="sxs-lookup"><span data-stu-id="9eaa0-172">Azure AD Connect version requirements</span></span>
<span data-ttu-id="9eaa0-p116">Подключение AAD версии 1.1.524.0 или более поздняя версия является единственным поддерживаемым способом для установки свойства **PreferredDataLocation** объектов-пользователей, которые синхронизируются из локального Active Directory. Синхронизация через подключение AAD в AAD объектов-пользователей не могут иметь напрямую изменить с помощью AAD PowerShell их **PreferredDataLocation** значение. С помощью AAD PowerShell может быть изменено объектов-пользователей только в облаке. Подробные сведения содержатся в разделе [Azure Active Directory подключение синхронизации: Настройка предпочитаемого данных расположения для ресурсов Office 365](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span><span class="sxs-lookup"><span data-stu-id="9eaa0-p116">AAD Connect version 1.1.524.0 or later is the only supported method for setting the **PreferredDataLocation** property on user objects that are synchronized from on-premises Active Directory. User objects synchronized via AAD Connect into AAD cannot have their **PreferredDataLocation** value directly modified via AAD PowerShell. Cloud-only user objects can be modified via AAD PowerShell. For detailed instructions, see [Azure Active Directory Connect sync: Configure preferred data location for Office 365 resources](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span></span>

### <a name="geo-codes"></a><span data-ttu-id="9eaa0-177">Коды географически</span><span class="sxs-lookup"><span data-stu-id="9eaa0-177">Geo Codes</span></span>
<span data-ttu-id="9eaa0-p117">Для указания Geo в свойстве **PreferredDataLocation** используйте трех букв. В следующей таблице перечислены коды для доступных Geos:</span><span class="sxs-lookup"><span data-stu-id="9eaa0-p117">You use three-letter codes to specify the Geo in the **PreferredDataLocation** property. The following table lists the codes for the available Geos:</span></span>

|<span data-ttu-id="9eaa0-180">Географическое</span><span class="sxs-lookup"><span data-stu-id="9eaa0-180">Geo</span></span> |<span data-ttu-id="9eaa0-181">Код</span><span class="sxs-lookup"><span data-stu-id="9eaa0-181">Code</span></span> |
|---------|---------|
|<span data-ttu-id="9eaa0-182">Азиатско-Тихоокеанский регион</span><span class="sxs-lookup"><span data-stu-id="9eaa0-182">Asia/Pacific</span></span> |<span data-ttu-id="9eaa0-183">APC</span><span class="sxs-lookup"><span data-stu-id="9eaa0-183">APC</span></span> |
|<span data-ttu-id="9eaa0-184">Австралия</span><span class="sxs-lookup"><span data-stu-id="9eaa0-184">Australia</span></span> |<span data-ttu-id="9eaa0-185">AUS</span><span class="sxs-lookup"><span data-stu-id="9eaa0-185">AUS</span></span> |
|<span data-ttu-id="9eaa0-186">Канада</span><span class="sxs-lookup"><span data-stu-id="9eaa0-186">Canada</span></span> |<span data-ttu-id="9eaa0-187">CAN</span><span class="sxs-lookup"><span data-stu-id="9eaa0-187">CAN</span></span> |
|<span data-ttu-id="9eaa0-188">Европейский Союз</span><span class="sxs-lookup"><span data-stu-id="9eaa0-188">European Union</span></span> |<span data-ttu-id="9eaa0-189">EUR</span><span class="sxs-lookup"><span data-stu-id="9eaa0-189">EUR</span></span> |
|<span data-ttu-id="9eaa0-190">Франция</span><span class="sxs-lookup"><span data-stu-id="9eaa0-190">France</span></span> |<span data-ttu-id="9eaa0-191">FRA</span><span class="sxs-lookup"><span data-stu-id="9eaa0-191">FRA</span></span>|
|<span data-ttu-id="9eaa0-192">Индия</span><span class="sxs-lookup"><span data-stu-id="9eaa0-192">India</span></span> |<span data-ttu-id="9eaa0-193">IND</span><span class="sxs-lookup"><span data-stu-id="9eaa0-193">IND</span></span> |
|<span data-ttu-id="9eaa0-194">Япония</span><span class="sxs-lookup"><span data-stu-id="9eaa0-194">Japan</span></span> |<span data-ttu-id="9eaa0-195">JPN</span><span class="sxs-lookup"><span data-stu-id="9eaa0-195">JPN</span></span> |
|<span data-ttu-id="9eaa0-196">Республика Корея</span><span class="sxs-lookup"><span data-stu-id="9eaa0-196">Korea</span></span> |<span data-ttu-id="9eaa0-197">KOR</span><span class="sxs-lookup"><span data-stu-id="9eaa0-197">KOR</span></span> |
|<span data-ttu-id="9eaa0-198">Соединенное Королевство</span><span class="sxs-lookup"><span data-stu-id="9eaa0-198">United Kingdom</span></span> |<span data-ttu-id="9eaa0-199">GBR</span><span class="sxs-lookup"><span data-stu-id="9eaa0-199">GBR</span></span> |
|<span data-ttu-id="9eaa0-200">США</span><span class="sxs-lookup"><span data-stu-id="9eaa0-200">United States</span></span> |<span data-ttu-id="9eaa0-201">NAM</span><span class="sxs-lookup"><span data-stu-id="9eaa0-201">NAM</span></span> |

<span data-ttu-id="9eaa0-p118">**Примечание**: свойства **PreferredDataLocation** и **MailboxRegion** являются строками с без проверки ошибок. Если ввести недопустимое значение (например, NAN) почтовый ящик будет помещен в географически по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="9eaa0-p118">**Note**: The **PreferredDataLocation** and **MailboxRegion** properties are strings with no error checking. If you enter an invalid value (for example, NAN) the mailbox will be placed in the default Geo.</span></span>

### <a name="view-the-available-geos-that-are-configured-in-your-exchange-online-organization"></a><span data-ttu-id="9eaa0-204">Просмотр доступных Geos, настроенных в организации Exchange Online</span><span class="sxs-lookup"><span data-stu-id="9eaa0-204">View the available Geos that are configured in your Exchange Online organization</span></span>
<span data-ttu-id="9eaa0-205">Чтобы просмотреть список настроенных Geos в организации Exchange Online, выполните следующую команду в Exchange Online PowerShell:</span><span class="sxs-lookup"><span data-stu-id="9eaa0-205">To see the list of configured Geos in your Exchange Online organization, run the following command in Exchange Online PowerShell:</span></span>

```
Get-OrganizationConfig | Select -ExpandProperty AllowedMailboxRegions | Format-Table
```

<span data-ttu-id="9eaa0-206">Выходные данные команды выглядят следующим образом:</span><span class="sxs-lookup"><span data-stu-id="9eaa0-206">The output of the command looks like this:</span></span>

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

### <a name="view-the-default-geo-for-your-exchange-online-organization"></a><span data-ttu-id="9eaa0-207">Представление по умолчанию географически для организации Exchange Online</span><span class="sxs-lookup"><span data-stu-id="9eaa0-207">View the default Geo for your Exchange Online organization</span></span>
<span data-ttu-id="9eaa0-208">Чтобы просмотреть географически по умолчанию из организации Exchange Online, выполните следующую команду в Exchange Online PowerShell:</span><span class="sxs-lookup"><span data-stu-id="9eaa0-208">To view the default geo of your Exchange Online organization, run the following command in Exchange Online PowerShell:</span></span>

```
Get-OrganizationConfig | Select DefaultMailboxRegion
```

<span data-ttu-id="9eaa0-209">Выходные данные команды выглядят следующим образом:</span><span class="sxs-lookup"><span data-stu-id="9eaa0-209">The output of the command looks like this:</span></span>

```
DefaultMailboxRegion
--------------------
NAM
```


### <a name="find-the-geo-location-of-a-mailbox"></a><span data-ttu-id="9eaa0-210">Поиск расположения географически почтового ящика</span><span class="sxs-lookup"><span data-stu-id="9eaa0-210">Find the Geo location of a mailbox</span></span>
<span data-ttu-id="9eaa0-211">Командлет **Get-Mailbox** в Exchange Online PowerShell отображает следующие свойства, связанные с географически для почтовых ящиков:</span><span class="sxs-lookup"><span data-stu-id="9eaa0-211">The **Get-Mailbox** cmdlet in Exchange Online PowerShell displays the following Geo-related properties on mailboxes:</span></span>

- <span data-ttu-id="9eaa0-p119">**Базы данных**: сначала 3 букв имя базы данных соответствующие код географически, который сообщает о том, где в настоящее время находится почтовый ящик. Свойство должно использоваться для почтовых ящиков Online архив **ArchiveDatabase** .</span><span class="sxs-lookup"><span data-stu-id="9eaa0-p119">**Database**: The first 3 letters of the database name correspond to the Geo code, which tells you where the mailbox is currently located. For Online Archive Mailboxes the **ArchiveDatabase** property should be used.</span></span>

- <span data-ttu-id="9eaa0-214">**MailboxRegion**: Определяет код географически, которое было задано администратором (синхронизируются из **PreferredDataLocation** в Azure AD).</span><span class="sxs-lookup"><span data-stu-id="9eaa0-214">**MailboxRegion**: Specifies the Geo code that was set by the admin (synchronized from **PreferredDataLocation** in Azure AD).</span></span>

- <span data-ttu-id="9eaa0-215">**MailboxRegionLastUpdateTime**: Указывает, когда MailboxRegion последнего обновления (автоматически или вручную).</span><span class="sxs-lookup"><span data-stu-id="9eaa0-215">**MailboxRegionLastUpdateTime**: Indicates when MailboxRegion was last updated (either automatically or manually).</span></span>

<span data-ttu-id="9eaa0-216">Чтобы увидеть эти свойства почтового ящика, используйте следующий синтаксис:</span><span class="sxs-lookup"><span data-stu-id="9eaa0-216">To see these properties for a mailbox, use the following syntax:</span></span>

```
Get-Mailbox -Identity <MailboxIdentity> | Format-List Database,MailboxRegion*
```

<span data-ttu-id="9eaa0-217">Например для просмотра сведений географически для chris@contoso.onmicrosoft.com почтовых ящиков, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="9eaa0-217">For example, to see the Geo information for the mailbox chris@contoso.onmicrosoft.com, run the following command:</span></span>

```
Get-Mailbox -Identity chris@contoso.onmicrosoft.com | Format-List Database, MailboxRegion*
```

<span data-ttu-id="9eaa0-218">Выходные данные команды выглядят следующим образом:</span><span class="sxs-lookup"><span data-stu-id="9eaa0-218">The output of the command looks like this:</span></span>

```
Database                    : EURPR03DG077-db007 
MailboxRegion               : EUR 
MailboxRegionLastUpdateTime : 2/6/2018 8:21:01 PM 
```

> <span data-ttu-id="9eaa0-219">**Примечание:** Если код Geo в поле имя базы данных не соответствует значение **MailboxRegion** , почтовый ящик будет автоматически быть помещены в очередь перемещения и перемещено в географически, указанное значение **MailboxRegion** (Exchange Online ищет несоответствие между этими значения свойств).</span><span class="sxs-lookup"><span data-stu-id="9eaa0-219">**Note:** If the Geo code in the database name doesn't match **MailboxRegion** value, the mailbox will be automatically be put into a relocation queue and moved to the Geo specified by the **MailboxRegion** value (Exchange Online looks for a mismatch between these property values).</span></span>

### <a name="move-an-existing-cloud-only-mailbox-to-a-specific-geo"></a><span data-ttu-id="9eaa0-220">Перемещение к определенным Geo существующего почтового ящика только в облаке</span><span class="sxs-lookup"><span data-stu-id="9eaa0-220">Move an existing cloud-only mailbox to a specific Geo</span></span>
<span data-ttu-id="9eaa0-p120">Только в облаке пользователь — это пользователь не представлением для клиента с помощью AAD подключение. Этот пользователь был создан непосредственно в Azure AD. Используйте командлеты **Get-MsolUser** и **Set-MsolUser** в модуля Azure AD для Windows PowerShell, чтобы просмотреть или задать географически, где будет храниться только в облаке почтового ящика пользователя.</span><span class="sxs-lookup"><span data-stu-id="9eaa0-p120">A cloud-only user is a user not syncrhonized to the tenant via AAD Connect. This user was created directly in Azure AD. Use the **Get-MsolUser** and **Set-MsolUser** cmdlets in the Azure AD Module for Windows PowerShell to view or specify the Geo where a cloud-only user's mailbox will be stored.</span></span>

<span data-ttu-id="9eaa0-224">Чтобы просмотреть значение **PreferredDataLocation** для пользователя, используйте следующий синтаксис в Windows Azure AD PowerShell:</span><span class="sxs-lookup"><span data-stu-id="9eaa0-224">To view the **PreferredDataLocation** value for a user, use this syntax in Azure AD PowerShell:</span></span>

```
Get-MsolUser -UserPrincipalName <UserPrincipalName> | Format-List UserPrincipalName,PreferredDataLocation
```

<span data-ttu-id="9eaa0-225">Например чтобы просмотреть значение **PreferredDataLocation** для michelle@contoso.onmicrosoft.com пользователя, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="9eaa0-225">For example, to see the **PreferredDataLocation** value for the user michelle@contoso.onmicrosoft.com, run the following command:</span></span>

```
Get-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com | Format-List
```

<span data-ttu-id="9eaa0-226">Выходные данные команды выглядят следующим образом:</span><span class="sxs-lookup"><span data-stu-id="9eaa0-226">The output of the command looks like this:</span></span>

```
UserPrincipalName     : michelle@contoso.onmicrosoft.com
PreferredDataLocation : EUR
```

<span data-ttu-id="9eaa0-227">Чтобы изменить значение **PreferredDataLocation** для объекта пользователя только в облаке, используйте следующий синтаксис в Windows Azure AD PowerShell:</span><span class="sxs-lookup"><span data-stu-id="9eaa0-227">To modify the **PreferredDataLocation** value for a cloud-only user object, use the following syntax in Azure AD PowerShell:</span></span>

``` 
Set-MsolUser -UserPrincipalName <UserPrincipalName> -PreferredDataLocation <GeoCode>
```

<span data-ttu-id="9eaa0-228">Например чтобы задать значение **PreferredDataLocation** географически Европейский союз (ЕВРО) для michelle@contoso.onmicrosoft.com пользователя, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="9eaa0-228">For example, to set the **PreferredDataLocation** value to the European Union (EUR) geo for the user michelle@contoso.onmicrosoft.com, run the following command:</span></span>

``` 
Set-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com -PreferredDataLocation EUR
```

<span data-ttu-id="9eaa0-229">**Примечания.**</span><span class="sxs-lookup"><span data-stu-id="9eaa0-229">**Notes**:</span></span>

- <span data-ttu-id="9eaa0-p121">Как упоминалось ранее нельзя использовать эту процедуру для объектов-синхронизированных пользователей из локального Active Directory. Необходимо изменить значение **PreferredDataLocation** , с помощью AAD подключение. Дополнительные сведения можно [Azure Active Directory подключение синхронизации: Настройка предпочитаемого данных расположения для ресурсов Office 365](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span><span class="sxs-lookup"><span data-stu-id="9eaa0-p121">As mentioned previously you cannot use this procedure for synchronized user objects from on-premises Active Directory. You need to change the **PreferredDataLocation** value using AAD Connect. For more information, see [Azure Active Directory Connect sync: Configure preferred data location for Office 365 resources](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span></span> 

- <span data-ttu-id="9eaa0-233">Сколько времени занимает о перемещении mailboxfrom его текущего географически для нового желаемую географически зависит от нескольких факторов:</span><span class="sxs-lookup"><span data-stu-id="9eaa0-233">How long it takes to relocate a mailboxfrom its current geo to the new desired geo depends on several factors:</span></span>
 
  - <span data-ttu-id="9eaa0-234">Размер и тип почтового ящика.</span><span class="sxs-lookup"><span data-stu-id="9eaa0-234">The size and type of mailbox.</span></span>
 
  - <span data-ttu-id="9eaa0-235">Количество происходит перемещение почтовых ящиков.</span><span class="sxs-lookup"><span data-stu-id="9eaa0-235">The number of mailboxes being moved.</span></span>
 
  - <span data-ttu-id="9eaa0-236">Доступность ресурсов перемещения.</span><span class="sxs-lookup"><span data-stu-id="9eaa0-236">The availability of move resources.</span></span>

#### <a name="move-disabled-mailboxes-that-are-on-litigation-hold"></a><span data-ttu-id="9eaa0-237">Перемещение почтовых ящиков на хранение для судебного разбирательства этот параметр отключен</span><span class="sxs-lookup"><span data-stu-id="9eaa0-237">Move disabled mailboxes that are on Litigation Hold</span></span>
<span data-ttu-id="9eaa0-p122">Этот параметр отключен почтовых ящиков на хранение для судебного разбирательства, сохраняются для обнаружения электронных данных, которые целей, нельзя перемещать, изменяя их значение **PreferredDataLocation** в отключенном состоянии. Чтобы переместить отключенного почтового ящика на хранение для судебного разбирательства:</span><span class="sxs-lookup"><span data-stu-id="9eaa0-p122">Disabled mailboxes on Litigation Hold that are preserved for eDiscovery purposes cannot be moved by changing their **PreferredDataLocation** value in their disabled state. To move a disabled mailbox on litigation hold:</span></span>

1. <span data-ttu-id="9eaa0-240">Временно назначьте почтовому ящику лицензию.</span><span class="sxs-lookup"><span data-stu-id="9eaa0-240">Temporarily assign a license to the mailbox.</span></span>

2. <span data-ttu-id="9eaa0-241">Измените **PreferredDataLocation**.</span><span class="sxs-lookup"><span data-stu-id="9eaa0-241">Change the **PreferredDataLocation**.</span></span>

3. <span data-ttu-id="9eaa0-242">Удалите лицензии из почтового ящика после его были перемещены для выбранного географически верните его в отключенном состоянии.</span><span class="sxs-lookup"><span data-stu-id="9eaa0-242">Remove the license from the mailbox after it has been moved to the selected Geo to put it back into the disabled state.</span></span>

### <a name="create-new-cloud-mailboxes-in-a-specific-geo"></a><span data-ttu-id="9eaa0-243">Создание новых облачных почтовых ящиков в конкретных географически</span><span class="sxs-lookup"><span data-stu-id="9eaa0-243">Create new cloud mailboxes in a specific Geo</span></span> 
<span data-ttu-id="9eaa0-244">Чтобы создать новый почтовый ящик в конкретных географически, необходимо выполнить одно из следующих действий:</span><span class="sxs-lookup"><span data-stu-id="9eaa0-244">To create a new mailbox in a specific Geo, you need to do either of these steps:</span></span>

- <span data-ttu-id="9eaa0-p123">Настройте значение **PreferredDataLocation** , как описано в предыдущем разделе *перед* создания почтового ящика в Exchange Online. К примеру настройте значение **PreferredDataLocation** пользователя перед назначение лицензии.</span><span class="sxs-lookup"><span data-stu-id="9eaa0-p123">Configure the **PreferredDataLocation** value as described in the previous section *before* the mailbox is created in Exchange Online. For example, configure the **PreferredDataLocation** value on a user before assigning a license.</span></span> 

- <span data-ttu-id="9eaa0-247">Назначение лицензии в то же время, задайте значение **PreferredDataLocation** .</span><span class="sxs-lookup"><span data-stu-id="9eaa0-247">Assign a license at the same time you set the **PreferredDataLocation** value.</span></span>

<span data-ttu-id="9eaa0-248">Для создания нового только в облаке лицензированных пользователей (не AAD подключение синхронизации) в определенных географически, используйте следующий синтаксис в Windows Azure AD PowerShell:</span><span class="sxs-lookup"><span data-stu-id="9eaa0-248">To create a new cloud-only licensed user (not AAD Connect synchronized) in a specific Geo, use the following syntax in Azure AD PowerShell:</span></span>

```
New-MsolUser -UserPrincipalName <UserPrincipalName> -DisplayName "<Display Name>" [-FirstName <FirstName>] [-LastName <LastName>] [-Password <Password>] [-LicenseAssignment <AccountSkuId>] -PreferredDataLocation <GeoCode> 
```
<span data-ttu-id="9eaa0-249">В этом примере Создание учетной записи пользователя для Brunner Александру со следующими значениями:</span><span class="sxs-lookup"><span data-stu-id="9eaa0-249">This example create a new user account for Elizabeth Brunner with the following values:</span></span>

- <span data-ttu-id="9eaa0-250">Имя участника-пользователя: ebrunner@contoso.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="9eaa0-250">User principal name: ebrunner@contoso.onmicrosoft.com</span></span>

- <span data-ttu-id="9eaa0-251">Имя: Александру</span><span class="sxs-lookup"><span data-stu-id="9eaa0-251">First name: Elizabeth</span></span>

- <span data-ttu-id="9eaa0-252">Фамилия: Brunner</span><span class="sxs-lookup"><span data-stu-id="9eaa0-252">Last name: Brunner</span></span>

- <span data-ttu-id="9eaa0-253">Отображаемое имя Brunner Александру</span><span class="sxs-lookup"><span data-stu-id="9eaa0-253">Display name Elizabeth Brunner</span></span>

- <span data-ttu-id="9eaa0-254">Пароль: случайным образом полученное и отображаются в результатах команды (так как не используется параметр *Password* )</span><span class="sxs-lookup"><span data-stu-id="9eaa0-254">Password: randomly-generated and shown in the results of the command (because we're not using the *Password* parameter)</span></span>

- <span data-ttu-id="9eaa0-255">Лицензия: contoso:ENTERPRISEPREMIUM (E5)</span><span class="sxs-lookup"><span data-stu-id="9eaa0-255">License: contoso:ENTERPRISEPREMIUM (E5)</span></span>

- <span data-ttu-id="9eaa0-256">Расположение: Австралия (Стандартное)</span><span class="sxs-lookup"><span data-stu-id="9eaa0-256">Location: Australia (AUS)</span></span>

```
New-MsolUser -UserPrincipalName ebrunner@contoso.onmicrosoft.com -DisplayName "Elizabeth Brunner" -FirstName Elizabeth -LastName Brunner -LicenseAssignment contoso:ENTERPRISEPREMIUM -PreferredDataLocation AUS
```

<span data-ttu-id="9eaa0-257">Дополнительные сведения о создании новых учетных записей пользователей и поиск значения LicenseAssignment в Windows Azure AD PowerShell можно [Создать учетные записи пользователей с Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell) и [Просмотр лицензий и службы с помощью Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/view-licenses-and-services-with-office-365-powershell).</span><span class="sxs-lookup"><span data-stu-id="9eaa0-257">For more information about creating new user accounts and finding LicenseAssignment values in Azure AD PowerShell, see [Create user accounts with Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell) and [View licenses and services with Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/view-licenses-and-services-with-office-365-powershell).</span></span>

> <span data-ttu-id="9eaa0-p124">**Примечание:** Если вы используете Exchange Online PowerShell для включения почтового ящика и необходимости почтового ящика будет создан непосредственно в географически, который указан в **PreferredDataLocation**, необходимо использовать Exchange Online командлета, такие как **Enable-Mailbox** или **New-Mailbox **непосредственно к облачной службе. При использовании командлета **Enable-RemoteMailbox** в локальной Exchange, почтовый ящик будет создан в географически по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="9eaa0-p124">**Note:** If you are using Exchange Online PowerShell to enable a mailbox and need the mailbox to be created directly in the Geo that's specified in **PreferredDataLocation**, you need to use an Exchange Online cmdlet such as **Enable-Mailbox** or **New-Mailbox** directly against the cloud service. If you use the **Enable-RemoteMailbox** on-premises Exchange cmdlet, the mailbox will be created in the default Geo.</span></span>

### <a name="onboard-existing-on-premises-mailboxes-in-a-specific-geo"></a><span data-ttu-id="9eaa0-260">Встроенный существующих локальных почтовых ящиков в конкретных географически</span><span class="sxs-lookup"><span data-stu-id="9eaa0-260">Onboard existing on-premises mailboxes in a specific Geo</span></span>
<span data-ttu-id="9eaa0-261">Можно использовать стандартный входящая средства и процедуры для переноса почтовых ящиков из локальной организации Exchange в Exchange Online, включая панели [мониторинга миграции в центре администрирования Exchange](https://support.office.com/article/d164b35c-f624-4f83-ac58-b7cae96ab331)и командлет [New-MigrationBatch](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-migrationbatch) в Exchange Online PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9eaa0-261">You can use the standard onboarding tools and processes to migrate a mailbox from an on-premises Exchange organization to Exchange Online, including the [Migration dashboard in the EAC](https://support.office.com/article/d164b35c-f624-4f83-ac58-b7cae96ab331), and the [New-MigrationBatch](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-migrationbatch) cmdlet in Exchange Online PowerShell.</span></span>

<span data-ttu-id="9eaa0-p125">Первым этапом является убедитесь, что существует объект пользователя для каждого почтового ящика быть onboarded и убедитесь, что правильное значение **PreferredDataLocation** , используемых в Azure AD. Средства адаптация новых сотрудников будут использовать значение **PreferredDataLocation** и будет перенос почтовых ящиков непосредственно в указанный географически.</span><span class="sxs-lookup"><span data-stu-id="9eaa0-p125">The first step is to verify a user object exists for each mailbox to be onboarded, and verify the correct **PreferredDataLocation** value is configured in Azure AD. The onboarding tools will respect the **PreferredDataLocation** value and will migrate the mailboxes directly to the specified Geo.</span></span>

<span data-ttu-id="9eaa0-264">Или можно использовать следующие шаги для встроенных почтовых ящиков непосредственно в конкретных географически с помощью командлета [New-MoveRequest](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-moverequest) в Exchange Online PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9eaa0-264">Or, you can use the following steps to onboard mailboxes directly in a specific Geo using the [New-MoveRequest](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-moverequest) cmdlet in Exchange Online PowerShell.</span></span>

1. <span data-ttu-id="9eaa0-p126">Убедитесь, что существует объект пользователя для каждого почтового ящика onboarded и **PreferredDataLocation** имеет значение необходимого значения в Azure AD. Значение **PreferredDataLocation** синхронизируются с атрибутом **MailboxRegion** соответствующего объекта пользователя почты в Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="9eaa0-p126">Verify the user object exists for each mailbox to be onboarded and that **PreferredDataLocation** is set to the desired value in Azure AD. The value of **PreferredDataLocation** will be synchronized to the **MailboxRegion** attribute of the corresponding mail user object in Exchange Online.</span></span>

2. <span data-ttu-id="9eaa0-267">Напрямую подключаться к определенным вспомогательных географически, с помощью инструкций по подключению из данного раздела.</span><span class="sxs-lookup"><span data-stu-id="9eaa0-267">Connect directly to the specific satellite Geo using the connection instructions from earlier in this topic.</span></span>

3. <span data-ttu-id="9eaa0-268">В Exchange Online PowerShell хранение учетных данных администратора в локальной, которые используются для выполнения миграции почтовых ящиков в переменную, выполнив следующую команду:</span><span class="sxs-lookup"><span data-stu-id="9eaa0-268">In Exchange Online PowerShell, store the on-premises administrator credentials that's used to perform a mailbox migration in a variable by running the following command:</span></span>

    ```
    $RC = Get-Credential
    ```

4. <span data-ttu-id="9eaa0-269">В Exchange Online PowerShell создайте новый **New-MoveRequest** аналогичные следующим образом:</span><span class="sxs-lookup"><span data-stu-id="9eaa0-269">In Exchange Online PowerShell, create a new **New-MoveRequest** similar to the following example:</span></span> 

    ```
    New-MoveRequest -Remote -RemoteHostName mail.contoso.com -RemoteCredential $RC -Identity user@contoso.com -TargetDeliveryDomain <YourAppropriateDomain>
    ```

5. <span data-ttu-id="9eaa0-270">Повторите шаг #4 для каждого почтового ящика, необходимые для переноса из локальной Exchange вспомогательной подключены к географически.</span><span class="sxs-lookup"><span data-stu-id="9eaa0-270">Repeat step #4 for every mailbox you need to migrate from on-premises Exchange to the satellite Geo you are currently connected to.</span></span>

6. <span data-ttu-id="9eaa0-271">Если необходимо перенести дополнительные почтовые ящики различных вспомогательной географически, повторите шаги с 2 по 4 для каждого конкретного вспомогательных географически.</span><span class="sxs-lookup"><span data-stu-id="9eaa0-271">If you need to migrate additional mailboxes to a different satellite Geo, repeat steps 2 through 4 for each specific satellite Geo.</span></span>

### <a name="multi-geo-reporting"></a><span data-ttu-id="9eaa0-272">Ферма с несколькими географически отчетов</span><span class="sxs-lookup"><span data-stu-id="9eaa0-272">Multi-Geo Reporting</span></span>
<span data-ttu-id="9eaa0-p127">**Отчеты об использовании несколькими Geo** в центре администрирования Office 365 отображает число пользователей, географически. Отчет отображает рассылки пользователя для текущего месяца и предоставляет статистические данные за последние 6 месяцев.</span><span class="sxs-lookup"><span data-stu-id="9eaa0-p127">**Multi-Geo Usage Reports** in the Office 365 admin center displays the user count by Geo. The report displays user distribution for the current month and provides historical data for the past 6 months.</span></span>
