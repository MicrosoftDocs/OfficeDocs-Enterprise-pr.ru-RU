---
title: Использование Azure AD для проверки подлинности на сервере SharePoint Server
ms.author: tracyp
author: MSFTTracyP
ms.reviewer: kirke, josephd, kirks
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Ent_O365_Hybrid
ms.custom: Ent_Solutions
ms.assetid: ''
description: Сводка. Узнайте, как обходить службу контроля доступа Azure и использовать SAML 1,1 для проверки подлинности пользователей SharePoint Server с помощью Azure Active Directory.
ms.openlocfilehash: c2c9f33aa5e095a8b7fdde08e80cb1a61e88f3eb
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070795"
---
# <a name="using-azure-ad-for-sharepoint-server-authentication"></a>Использование Azure AD для проверки подлинности на сервере SharePoint Server

 **Сводка:** Узнайте, как проверить подлинность пользователей SharePoint Server 2016 с помощью Azure Active Directory. 

<blockquote>
<p>В этой статье приводятся примеры кода для взаимодействия с диаграммой Azure Active Directory. Вы можете скачать примеры кода [здесь](https://github.com/kaevans/spsaml11/tree/master/scripts).</p>
</blockquote>

SharePoint Server 2016 обеспечивает возможность проверки подлинности пользователей с помощью проверки подлинности на основе утверждений, что упрощает управление пользователями с помощью проверки подлинности с другими поставщиками удостоверений, которым вы доверяете, но кто-то еще управляет им. Например, вместо управления проверкой подлинности пользователей с помощью доменных служб Active Directory (AD DS) можно разрешить пользователям выполнять проверку подлинности с помощью Azure Active Directory (Azure AD). Это позволяет выполнять проверку подлинности для пользователей в облаке с помощью суффикса onmicrosoft.com в имени пользователя, синхронизировать пользователей с локальным каталогом и приглашать гостевых пользователей из других каталогов. Кроме того, вы можете использовать преимущества функций Azure AD, таких как многофакторная проверка подлинности и расширенные возможности создания отчетов.

> [!IMPORTANT]
> Решение, описанное в этой статье, также можно использовать с SharePoint Server 2013. Однако имейте в виду, что SharePoint Server 2013 приближается к концу основной поддержки. Дополнительные сведения см в разделе [Политика жизненного цикла Майкрософт](https://support.microsoft.com/en-us/lifecycle/search?alpha=SharePoint%20Server%202013) и [Обновленная политика обслуживания продукта для SharePoint 2013](https://technet.microsoft.com/library/684173bb-e90a-4eb7-b268-b8d7458bc802(v=office.16).aspx).

В этой статье объясняется, как можно использовать Azure AD вместо локальных ДОМЕНных служб Active Directory для проверки подлинности пользователей. В этой конфигурации Azure AD становится доверенным поставщиком удостоверений для SharePoint Server 2016. Эта конфигурация добавляет метод проверки подлинности пользователя, который отличается от проверки подлинности доменных служб Active Directory, используемой установкой SharePoint Server 2016. Эта статья будет вам полезна, если вы знакомы с WS-Federation. Дополнительные сведения см. [](https://go.microsoft.com/fwlink/p/?linkid=188052) Подробные сведения о интеграции SharePoint в локальной среде с Azure Active Directory можно найти в выделенном [руководстве](https://docs.microsoft.com/azure/active-directory/saas-apps/sharepoint-on-premises-tutorial).

![Использование Azure AD для проверки подлинности SharePoint](media/SAML11/fig1-architecture.png)

Ранее эта конфигурация требовала бы, что служба Федерации, например служба контроля доступа Azure (ACS) в облаке или среде, в которой размещаются службы федерации Active Directory (AD FS), преобразует маркеры из SAML 2,0 в SAML 1,1. Это преобразование больше не нужно, так как Azure AD теперь позволяет выдавать маркеры SAML 1,1. На схеме выше показано, как работает проверка подлинности для пользователей SharePoint 2016 в этой конфигурации, что показывает, что больше не требуется для промежуточных посредников выполнять это преобразование.

> [!NOTE]
> Эта конфигурация работает независимо от того, размещается ли ферма SharePoint в виртуальных машинах Azure или локальной среде. Для этого не требуется открывать дополнительные порты брандмауэра, кроме проверки того, что пользователи могут получать доступ к Azure Active Directory из своего браузера.

Сведения о специальных возможностях SharePoint 2016 приведены [в статье рекомендации по специальным возможностям в SharePoint Server 2016](https://go.microsoft.com/fwlink/p/?LinkId=393123).

## <a name="configuration-overview"></a>Общие сведения о конфигурации

Выполните следующие общие действия, чтобы настроить среду для использования Azure AD в качестве поставщика удостоверений SharePoint Server 2016.

1. Создайте новый каталог Azure AD или используйте существующий каталог.
2. Убедитесь, что зона для веб-приложения, которую требуется защитить с помощью Azure AD, настроена на использование SSL.
3. Создайте новое корпоративное приложение в Azure AD.
4. Настройте новый доверенный поставщик удостоверений в SharePoint Server 2016.
5. Задайте разрешения для веб-приложения.
6. Добавьте политику выдачи маркеров SAML 1,1 в Azure AD.
7. Проверьте нового поставщика.

В следующих разделах описано, как выполнить эти задачи.

## <a name="step-1-create-a-new-azure-ad-directory-or-use-your-existing-directory"></a>Шаг 1: создание нового каталога Azure AD или использование существующего каталога

На портале Azure ([https://portal.azure.com](https://portal.azure.com)) создайте новый каталог. Укажите название организации, имя исходного домена, страну или регион.

![Создание каталога](media/SAML11/fig2-createdirectory.png) 

 Если у вас уже есть каталог, например, который используется для Microsoft Office 365 или вашей подписки Microsoft Azure, вы можете использовать эту папку. Необходимо иметь разрешения на регистрацию приложений в каталоге.

## <a name="step-2-ensure-the-zone-for-the-web-application-that-you-want-to-secure-with-azure-ad-is-configured-to-use-ssl"></a>Шаг 2: Убедитесь, что зона для веб-приложения, которую требуется защитить с помощью Azure AD, настроена на использование SSL

Эта статья была написана с помощью эталонной архитектуры в статье [Запуск фермы SharePoint Server 2016 с высоким уровнем доступности в Azure](https://docs.microsoft.com/en-us/azure/architecture/reference-architectures/sharepoint). Прилагаемые к статье скрипты, используемые для развертывания решения, описанные в [этой статье](https://docs.microsoft.com/en-us/azure/architecture/reference-architectures/sharepoint) , создают сайт, который не использует SSL.  

Для использования функции SAML необходимо, чтобы приложение было настроено для использования протокола SSL. Если ваше веб-приложение SharePoint не настроено для использования SSL, выполните следующие действия, чтобы создать новый самозаверяющий сертификат для настройки веб-приложения для SSL. Эта конфигурация предназначена только для лабораторной среды и не предназначена для рабочей среды. В рабочих средах должен использоваться подписанный сертификат.

1. Перейдите в раздел**Управление** > приложениями **центра администрирования** > **Управление веб-приложениями**и выберите веб-приложение, которое необходимо расширить для использования протокола SSL. Выберите веб-приложение и нажмите кнопку " **расширить ленту** ". Расширьте веб-приложение, используя тот же URL-адрес, но с помощью SSL с портом 443.<br/>![Расширение веб-приложения для другого сайта IIS](media/SAML11/fig3-extendwebapptoiis.png)<br/>
2. В Диспетчер IIS дважды щелкните **Сертификаты сервера**.
3. В области **Действия** нажмите **Создать самозаверяющий сертификат**. Введите понятное имя сертификата в поле Понятное имя сертификата и нажмите кнопку **ОК**.
4. В диалоговом окне **изменение привязки сайта** убедитесь, что имя узла совпадает с понятным именем, как показано на следующем рисунке.<br/>![Изменение привязки сайта в СЛУЖБах IIS](media/SAML11/fig4-editsitebinding.png)<br/>

Для каждого из серверов веб-интерфейсов в ферме SharePoint потребуется настроить сертификат для привязки сайта в СЛУЖБах IIS.


## <a name="step-3-create-a-new-enterprise-application-in-azure-ad"></a>Шаг 3: создание нового корпоративного приложения в Azure AD

1. На портале Azure ([https://portal.azure.com](https://portal.azure.com)) откройте каталог Azure AD. Выберите пункт **корпоративные приложения**и нажмите кнопку **создать приложение**. Выберите **приложение, не являющееся галереей**. Введите имя, например интеграция с помощью *SAML для SharePoint* , и нажмите кнопку **Добавить**.<br/>![Добавление нового приложения, не относящегося к коллекции](media/SAML11/fig5-addnongalleryapp.png)<br/>
2. Щелкните ссылку единый вход в области навигации, чтобы настроить приложение. В раскрывающемся списке **режим единого входа измените режим единого входа** на **Вход на основе SAML** , чтобы открыть свойства конфигурации SAML для приложения. Настройте со следующими свойствами:<br/>
    - Идентификацион`urn:sharepoint:portal.contoso.local`
    - URL-адрес ответа:`https://portal.contoso.local/_trust/default.aspx`
    - URL-адрес для входа:`https://portal.contoso.local/_trust/default.aspx`
    - Идентификатор пользователя:`user.userprincipalname`<br/>
    - Note: не забудьте изменить URL-адреса, заменив URL-адрес сайта *Portal. contoso. local* URL-адресом сайта SharePoint, который требуется защитить.<br/>
3. Настройте таблицу (аналогичную таблице 1 ниже), которая включает следующие строки:<br/> 
    - Realm
    - Полный путь к файлу сертификата подписывания SAML
    - URL-адрес службы единого входа SAML (замена */SAML2* на */всфед*)
    - Идентификатор объекта Application. <br/>
Скопируйте значение *идентификатора* в свойство *realm* в таблицу (см. Таблица 1 ниже).
4. Сохраните изменения.
5. Щелкните ссылку **Настройка (имя приложения)** , чтобы открыть страницу "Настройка входа".<br/>![Настройка страницы единого входа](media/SAML11/fig7-configssopage.png)<br/> 
    -  Щелкните ссылку " **подписанный сертификат SAML-RAW** ", чтобы скачать сертификат подписи SAML в виде файла с расширением CER. Скопируйте и вставьте полный путь к загруженному файлу в таблицу.
    - Скопируйте и вставьте ссылку на URL-адрес службы единого входа SAML, заменив часть */SAML2* URL-адреса на */всфед*.<br/>
6.  Перейдите в область **свойств** приложения. Скопируйте и вставьте значение идентификатора объекта в таблицу, настроенную на шаге 3.<br/>![Область свойств для приложения](media/SAML11/fig8-propertiespane.png)<br/>
7. Используя записанные значения, убедитесь, что таблица, настроенная на шаге 3, похожа на таблицу 1 ниже.


| Таблица 1: зафиксированные значения  |  |
|---------|---------|
|Realm | `urn:sharepoint:portal.contoso.local` |
|Полный путь к файлу сертификата подписывания SAML | `C:/temp/SharePoint SAML Integration.cer`  |
|URL-адрес службы единого входа SAML (замените/SAML2 на/всфед) | `https://login.microsoftonline.com/b1726649-b616-460d-8d20-defab80d476c/wsfed` |
|Идентификатор объекта Application | `a812f48b-d1e4-4c8e-93be-e4808c8ca3ac` |

> [!IMPORTANT]
> Замените значение */SAML2* в URL-адресе на */всфед*. Конечная точка */SAML2* будет ОБРАБАТЫВАТЬ маркеры SAML 2,0. Конечная точка */всфед* разрешает обработку маркеров SAML 1,1 и является обязательной для Федерации SAML для SharePoint 2016.

## <a name="step-4-configure-a-new-trusted-identity-provider-in-sharepoint-server-2016"></a>Шаг 4: Настройка нового доверенного поставщика удостоверений в SharePoint Server 2016

Войдите на сервер SharePoint Server 2016 и откройте командную консоль SharePoint 2016. Введите значения $realm, $wsfedurl и $filepath из таблицы 1 и выполните указанные ниже команды, чтобы настроить новый доверенный поставщик удостоверений.

> [!TIP]
> Если вы не знакомы с использованием PowerShell или хотите узнать больше о том, как работает PowerShell, обратитесь к разделу [SharePoint PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/overview?view=sharepoint-ps). 

```
$realm = "<Realm from Table 1>"
$wsfedurl="<SAML single sign-on service URL from Table 1>"
$filepath="<Full path to SAML signing certificate file from Table 1>"
$cert = New-Object System.Security.Cryptography.X509Certificates.X509Certificate2($filepath)
New-SPTrustedRootAuthority -Name "AzureAD" -Certificate $cert
$map = New-SPClaimTypeMapping -IncomingClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" -IncomingClaimTypeDisplayName "name" -LocalClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/upn"
$map2 = New-SPClaimTypeMapping -IncomingClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/givenname" -IncomingClaimTypeDisplayName "GivenName" -SameAsIncoming
$map3 = New-SPClaimTypeMapping -IncomingClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/surname" -IncomingClaimTypeDisplayName "SurName" -SameAsIncoming
$ap = New-SPTrustedIdentityTokenIssuer -Name "AzureAD" -Description "SharePoint secured by Azure AD" -realm $realm -ImportTrustCertificate $cert -ClaimsMappings $map,$map2,$map3 -SignInUrl $wsfedurl -IdentifierClaim "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name"
```

После этого выполните указанные ниже действия, чтобы включить доверенный поставщик удостоверений для вашего приложения.
1. В центре администрирования перейдите в раздел **Управление веб-приложением** и выберите веб-приложение, которое необходимо защитить с помощью Azure AD. 
2. На ленте щелкните **поставщики проверки** подлинности и выберите зону, которую вы хотите использовать.
3. Выберите **доверенный поставщик удостоверений** и выберите только что зарегистрированный поставщик с именем *AzureAD*.  
4. В параметре URL-адрес страницы входа выберите пункт **Настраиваемая страница входа** и укажите значение "/_труст/". 
5. Нажмите кнопку **ОК**.

![Настройка поставщика проверки подлинности](media/SAML11/fig10-configauthprovider.png)

> [!IMPORTANT]
> Важно выполнить все действия, в том числе настроить настраиваемую страницу входа в "/_труст/", как показано ниже. Конфигурация не будет работать должным образом, если не выполнены все действия.

## <a name="step-5-set-the-permissions"></a>Шаг 5: Установка разрешений

Пользователям, которые будут входить в систему Azure AD и получать доступ к SharePoint, должен быть назначен доступ к приложению. 

1. На портале Azure откройте каталог Azure AD. Щелкните **корпоративные приложения**, а затем выберите **все приложения**. Выберите приложение, созданное ранее (интеграция с помощью SAML для SharePoint).
2. Щелкните **Пользователи и группы**. 
3. Нажмите кнопку **Добавить пользователя** , чтобы добавить пользователя или группу, которые будут иметь разрешения на вход в SharePoint с помощью Azure AD.
4. Выберите пользователя или группу, а затем нажмите кнопку **назначить**.
 
Пользователю предоставлено разрешение в Azure AD, но ему также должно быть предоставлено разрешение в SharePoint. Выполните указанные ниже действия, чтобы задать разрешения доступа к веб-приложению.

1. Откройте Центр администрирования и выберите **Управление приложениями**.
2. На странице **Управление приложениями** в разделе **Веб-приложения** выберите команду **Управление веб-приложениями**.
3. Щелкните соответствующее веб-приложение, а затем выберите пункт **Политика пользователей**.
4. В окне Политика для веб-приложения нажмите кнопку **Добавить пользователей**.<br/>![Поиск пользователя по утверждению его имени](media/SAML11/fig11-searchbynameclaim.png)<br/>
5. В диалоговом окне **Добавление пользователей** щелкните соответствующие зоны в разделе **Зоны**, а затем нажмите кнопку **Далее**.
6. В диалоговом окне " **Политика для веб-приложения** " в разделе **Выбор пользователей** щелкните значок **Обзор** .
7. В текстовом поле **найти** введите имя пользователя для входа в ваш каталог и нажмите кнопку **Поиск**. <br/>Пример: *demouser@blueskyabove.onmicrosoft.com*.
8. Под заголовком AzureAD в представлении списка выберите свойство имя и нажмите кнопку **Добавить** , а затем нажмите кнопку **ОК** , чтобы закрыть диалоговое окно.
9. В окне Разрешения нажмите кнопку **полный**доступ.<br/>![Предоставление пользователю утверждений полного доступа](media/SAML11/fig12-grantfullcontrol.png)<br/>
10. Нажмите **Готово**, а затем  **ОК**.

## <a name="step-6-add-a-saml-11-token-issuance-policy-in-azure-ad"></a>Шаг 6: Добавление политики выдачи маркеров SAML 1,1 в Azure AD

При создании приложения Azure AD на портале по умолчанию используется SAML 2,0. Для SharePoint Server 2016 требуется формат маркеров SAML 1,1. Следующий сценарий удалит политику SAML 2,0 по умолчанию и добавит новую политику для выпусков маркеров SAML 1,1. 

> Этот код требует загрузки прилагаемых [примеров, демонстрирующих взаимодействие с диаграммой Azure Active Directory](https://github.com/kaevans/spsaml11/tree/master/scripts). Если вы скачиваете скрипты в виде ZIP-файла из GitHub на Рабочий стол Windows, не забудьте `MSGraphTokenLifetimePolicy.psm1` разблокировать файл модуля скрипта `Initialize.ps1` и файл сценария (щелкните правой кнопкой мыши свойства, выберите Разблокировать, нажмите кнопку ОК). 
![Разблокировка скачанных файлов](media/SAML11/fig17-unblock.png)

После скачивания примера сценария создайте новый скрипт PowerShell с помощью следующего кода, заменив заполнитель на путь к файлу, скачанному `Initialize.ps1` на локальном компьютере. Замените заполнитель идентификатора объекта приложения ИДЕНТИФИКАТОРом объекта Application, который вы ввели в таблице 1. После создания выполните сценарий PowerShell. 

```
function AssignSaml11PolicyToAppPrincipal
{
    Param(
        [Parameter(Mandatory=$true)]
        [string]$pathToInitializeScriptFile, 
        [Parameter(Mandatory=$true)]
        [string]$appObjectid
    )

    $folder = Split-Path $pathToInitializeScriptFile
    Push-Location $folder

    #Loads the dependent ADAL module used to acquire tokens
    Import-Module $pathToInitializeScriptFile 

    #Gets the existing token issuance policy
    $existingTokenIssuancePolicy = Get-PoliciesAssignedToServicePrincipal -servicePrincipalId $appObjectid | ?{$_.type -EQ "TokenIssuancePolicy"} 
    Write-Host "The following TokenIssuancePolicy policies are assigned to the service principal." -ForegroundColor Green
    Write-Host $existingTokenIssuancePolicy -ForegroundColor White
    $policyId = $existingTokenIssuancePolicy.objectId

    #Removes existing token issuance policy
    Write-Host "Only a single policy can be assigned to the service principal. Removing the existing policy with ID $policyId" -ForegroundColor Green
    Remove-PolicyFromServicePrincipal -policyId $policyId -servicePrincipalId $appObjectid

    #Creates a new token issuance policy and assigns to the service principal
    Write-Host "Adding the new SAML 1.1 TokenIssuancePolicy" -ForegroundColor Green
    $policy = Add-TokenIssuancePolicy -DisplayName SPSAML11 -SigningAlgorithm "http://www.w3.org/2001/04/xmldsig-more#rsa-sha256" -TokenResponseSigningPolicy TokenOnly -SamlTokenVersion "1.1"
    Write-Host "Assigning the new SAML 1.1 TokenIssuancePolicy $policy.objectId to the service principal $appObjectid" -ForegroundColor Green
    Set-PolicyToServicePrincipal -policyId $policy.objectId -servicePrincipalId $appObjectid
    Pop-Location
}

#Only edit the following two variables
$pathToInitializeScriptFile = "<file path of Initialize.ps1>"
$appObjectid = "<Application Object ID from Table 1>"

AssignSaml11PolicyToAppPrincipal $pathToInitializeScriptFile $appObjectid
```
> [!IMPORTANT]
> Сценарии PowerShell не подписаны, и вам может быть предложено задать политику выполнения. Более подробную информацию о политиках выполнения можно узнать в статье [о политиках выполнения](http://go.microsoft.com/fwlink/?LinkID=135170). Кроме того, может потребоваться открыть командную строку с повышенными привилегиями, чтобы успешно выполнить команды, хранящиеся в примерах сценариев.

В этих примерах команд PowerShell представлены примеры выполнения запросов к API Graph. Для получения дополнительных сведений о политиках выдачи маркеров в Azure AD, ознакомьтесь со статьей [Справочник по API Graph для работы с политикой](https://msdn.microsoft.com/en-us/library/azure/ad/graph/api/policy-operations#create-a-policy).

## <a name="step-7-verify-the-new-provider"></a>Шаг 7: проверка нового поставщика

Откройте браузер URL-адрес веб-приложения, настроенного в предыдущих шагах. Вы перенаправлены на команду "войти в Azure AD".

![Вход в Azure AD, настроенный для Федерации](media/SAML11/fig13-examplesignin.png)

Вам будет предложено подтвердить вход в систему.

![Оставайтесь в курсе входа?](media/SAML11/fig14-staysignedin.png)

Наконец, вы можете получить доступ к сайту, вошедшего в систему от имени пользователя, из клиента Azure Active Directory.

![Пользователь выполнил вход в SharePoint](media/SAML11/fig15-signedinsharepoint.png)

## <a name="managing-certificates"></a>Управление сертификатами
Важно понимать, что сертификат подписи, настроенный для доверенного поставщика удостоверений на шаге 4 выше, имеет дату окончания срока действия и должен быть обновлен. Сведения об обновлении сертификатов можно найти [в статье Управление сертификатами для федеративного единого входа в Azure Active Directory](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-sso-certs) . После продления сертификата в Azure AD Скачайте в локальный файл и используйте следующий сценарий для настройки доверенного поставщика удостоверений с обновленным сертификатом подписи. 

```
$filepath="<Full path to renewed SAML signing certificate file>"
$cert= New-Object System.Security.Cryptography.X509Certificates.X509Certificate2($filePath)
New-SPTrustedRootAuthority -Name "AzureAD" -Certificate $cert
Get-SPTrustedIdentityTokenIssuer "AzureAD" | Set-SPTrustedIdentityTokenIssuer -ImportTrustCertificate $cert
```
## <a name="configuring-one-trusted-identity-provider-for-multiple-web-applications"></a>Настройка одного доверенного поставщика удостоверений для нескольких веб-приложений
Конфигурация работает для одного веб-приложения, но требует дополнительной настройки, если вы планируете использовать один и тот же доверенный поставщик удостоверений для нескольких веб-приложений. Например, предположим, что веб-приложение было расширено для использования URL `https://portal.contoso.local` -адреса, и теперь вы хотите проверить `https://sales.contoso.local` подлинность пользователей. Для этого необходимо обновить поставщик удостоверений, чтобы он использовал параметр WReply и обновлял регистрацию приложения в Azure AD, чтобы добавить URL-адрес ответа.

1. На портале Azure откройте каталог Azure AD. Щелкните **Регистрация приложений**, а затем щелкните **Просмотр всех приложений**. Выберите приложение, созданное ранее (интеграция с помощью SAML для SharePoint).
2. Нажмите кнопку **Параметры**.
3. В колонке параметры щелкните **URL-адреса для ответа**. 
4. Добавьте URL-адрес дополнительного веб-приложения с `/_trust/default.aspx` добавлением к URL-адресу ( `https://sales.contoso.local/_trust/default.aspx`например,), а затем нажмите кнопку **сохранить**. 
5. На сервере SharePoint откройте **командную консоль sharepoint 2016** и выполните следующие команды, используя имя доверенного поставщика маркеров удостоверений, который вы использовали ранее.

```
$t = Get-SPTrustedIdentityTokenIssuer "AzureAD"
$t.UseWReplyParameter=$true
$t.Update()
```
6. В центре администрирования перейдите в веб-приложение и включите существующего доверенного поставщика удостоверений. Не забудьте также настроить URL-адрес страницы входа как настраиваемую страницу `/_trust/`входа.
7. В центре администрирования щелкните веб-приложение и выберите **Политика пользователя**. Добавьте пользователя с соответствующими разрешениями, как показано выше в этой статье.

## <a name="fixing-people-picker"></a>Устранение неполадок средства выбора людей
Теперь пользователи могут войти в SharePoint 2016 с помощью удостоверений из Azure AD, но по-прежнему существуют возможности улучшения взаимодействия с пользователем. Например, Поиск пользователя представляет несколько результатов поиска в средстве выбора людей. Существует результат поиска для каждого из трех типов утверждений, созданных в сопоставлении утверждений. Чтобы выбрать пользователя с помощью средства выбора людей, необходимо ввести имя пользователя в точности и выбрать результат утверждения **имени** .

![Результаты поиска утверждений](media/SAML11/fig16-claimssearchresults.png)

Поиск по искомым значениям не выполняется, что может повлечь за собой неправильное написание или неправильное выбор неправильного типа утверждений **** , например утверждений о фамилии. Это может препятствовать успешному доступу к ресурсам для пользователей.

Чтобы помочь этому сценарию, существует решение с открытым кодом, именуемое [азурекп](https://yvand.github.io/AzureCP/) , которое предоставляет пользовательский поставщик утверждений для SharePoint 2016. Он будет использовать Azure AD Graph, чтобы разрешить пользователям ввод и выполнение проверки. Узнайте больше по адресу [азурекп](https://yvand.github.io/AzureCP/). 

## <a name="additional-resources"></a>Дополнительные ресурсы

[Общие сведения о WS-Federation](https://go.microsoft.com/fwlink/p/?linkid=188052)
  
[Освоение облака и гибридные решения](cloud-adoption-and-hybrid-solutions.md)
  
## <a name="join-the-discussion"></a>Присоединяйтесь к обсуждению

|**Свяжитесь с нами**|**Описание**|
|:-----|:-----|
|**Какое вам решение необходимо?** <br/> |Мы создаем контент для решений, которые охватывают несколько продуктов и служб Майкрософт. Сообщите нам, что вы думаете о наших межсерверных решениях, или укажите интересующие вас решения, написав по адресу [MODAcontent@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20).<br/> |
|**Присоединяйтесь к обсуждению решений** <br/> |Если вам интересны облачные решения, присоединяйтесь к теме Cloud Adoption Advisory Board (CAAB) и общайтесь с разработчиками контента Майкрософт, специалистами отрасли и клиентами со всего мира. Чтобы присоединиться, добавьте себя в качестве участника [темы CAAB (Cloud Adoption Advisory Board)](https://aka.ms/caab) на сайте Microsoft Tech Community и отправьте нам письмо на адрес [CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!). Просматривать материалы в [блоге CAAB](https://blogs.technet.com/b/solutions_advisory_board/) могут все пользователи. Однако только участники CAAB получают приглашения на закрытые вебинары, на которых мы рассказываем о новых облачных решениях и ресурсах по их внедрению.<br/> |
|**Скачать изображения, которые вы видите здесь** <br/> |Если вам нужна редактируемая копия иллюстративного материала из этой статьи, мы с радостью вам ее отправим. Напишите нам, указав URL-адрес и название материала, по адресу [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20).<br/> |
   

