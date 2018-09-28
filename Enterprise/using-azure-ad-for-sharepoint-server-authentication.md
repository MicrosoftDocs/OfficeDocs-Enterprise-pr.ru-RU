---
title: Использование Azure AD для проверки подлинности на сервере SharePoint Server
ms.author: tracyp
author: MSFTTracyP
ms.reviewer: kirke, josephd, kirks
manager: laurawi
ms.audience: ITPro
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
description: 'Сводка: Узнайте, как для обхода служба контроля доступа Azure и использовании SAML 1.1 для проверки подлинности пользователей SharePoint Server с помощью Azure Active Directory.'
ms.openlocfilehash: 5c95501d73c59a4af89147d3eec6c5d4e206d067
ms.sourcegitcommit: 82219b5f8038ae066405dfb7933c40bd1f598bd0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/14/2018
ms.locfileid: "23975227"
---
# <a name="using-azure-ad-for-sharepoint-server-authentication"></a>Использование Azure AD для проверки подлинности на сервере SharePoint Server

 **Сводка:** Узнайте, как выполнить проверку подлинности пользователей SharePoint Server 2016 с Azure Active Directory. 

<blockquote>
<p>В этом статье содержатся ссылки на примеры кода для взаимодействия с Azure Active Directory графике. Вы можете загрузить примеры кода [ниже](https://github.com/kaevans/spsaml11/tree/master/scripts).</p>
</blockquote>

SharePoint Server 2016 предоставляет возможность проверки подлинности пользователей с помощью проверки подлинности на основе утверждений, что упрощает для управления пользователями, они проходят проверку подлинности с помощью различных поставщиков удостоверений, которые вы доверяете, но кто управляет. К примеру вместо управления проверки подлинности пользователей с помощью доменных служб Active Directory (AD DS), позволит пользователям проходить проверку подлинности с помощью Azure Active Directory (Azure AD). Это позволяет проверки подлинности пользователей только в облаке с суффиксом onmicrosoft.com в свои имя пользователя, пользователи синхронизируются с локального каталога и гостевых пользователей из других каталогов на участие. Он также позволяет воспользоваться преимуществами Azure AD компонентов, таких как многофакторная проверка подлинности и расширенные возможности работы с отчетами.

> [!IMPORTANT]
> Решения, описанного в данной статье также можно использовать вместе с SharePoint Server 2013; Однако имейте в виду, что SharePoint Server 2013 приближается к завершению основной поддержки. Для получения дополнительных сведений см [ [Microsoft жизненный цикл обновления продукта обслуживания для политики](https://technet.microsoft.com/library/684173bb-e90a-4eb7-b268-b8d7458bc802(v=office.16).aspx)и SharePoint 2013](https://support.microsoft.com/en-us/lifecycle/search?alpha=SharePoint%20Server%202013) .

В этой статье объясняется, как использовать Azure AD для проверки подлинности пользователей, а не на локальную Доменные службы Active Directory. В этой конфигурации Azure AD становится доверенного поставщика удостоверений для SharePoint Server 2016. В этой конфигурации добавляется метод проверки подлинности пользователя, которая не связана с проверки подлинности Доменные службы Active Directory, используемых самой установки SharePoint Server 2016. Чтобы извлечь пользу из этой статьи, необходимо ознакомиться с WS-Federation. Дополнительные сведения содержатся в разделе [Общие сведения о WS-Federation](https://go.microsoft.com/fwlink/p/?linkid=188052).

![С помощью Azure AD для проверки подлинности SharePoint](media/SAML11/fig1-architecture.png)

Ранее эта конфигурация потребовалось бы службы федерации например Azure доступа Control Service (ACS) в облаке или в среде, в котором размещается служб федерации Active Directory (AD FS) для преобразования маркеры SAML 2.0 для SAML 1.1. Это преобразование больше не требуется как Azure AD теперь включает выдающего маркеры SAML 1.1. На приведенной выше схеме показано принципы работы проверки подлинности для пользователей SharePoint 2016 в этой конфигурации демонстрирует, что оно больше не является обязательным требованием для посредника для выполнения этого преобразования.

> [!NOTE]
> Эта конфигурация работает ли размещается в виртуальных машин Azure или локальной фермы SharePoint. Не требуется открыть порты брандмауэра Дополнительные отличный от обеспечение пользователей можно получить доступ к Azure Active Directory в браузере.

Сведения о специальных возможностей SharePoint 2016 содержатся [Требования к специальным возможностям в SharePoint Server 2016](https://go.microsoft.com/fwlink/p/?LinkId=393123).

## <a name="configuration-overview"></a>Общие сведения о конфигурации

Выполните следующие действия для настройки среды для использования в качестве поставщика удостоверений SharePoint Server 2016 Azure AD.

1. Создать новый каталог Azure AD или использовать существующий каталог.
2. Убедитесь, что зоны для веб-приложения, которое требуется защитить с помощью Azure AD настроен для использования протокола SSL.
3. Создание нового приложения предприятия в Azure AD.
4. Настройка нового доверенного поставщика удостоверений в SharePoint Server 2016.
5. Установка разрешений для веб-приложения.
6. Добавление политики выдача маркеров SAML 1.1 в Azure AD.
7. Проверьте нового поставщика.

В следующих разделах описано для выполнения этих задач.

## <a name="step-1-create-a-new-azure-ad-directory-or-use-your-existing-directory"></a>Шаг 1: Создание нового каталога Azure AD или использовать существующий каталог

На портале Azure ([https://portal.azure.com](https://portal.azure.com)), создайте новый каталог. Укажите название организации, исходное имя домена и страну или регион.

![Создание каталога](media/SAML11/fig2-createdirectory.png) 

 При наличии каталогов, такой как для Microsoft Office 365 или подписки Microsoft Azure, вместо этого можно использовать этот каталог. Необходимо иметь разрешения для регистрации приложений в каталоге.

## <a name="step-2-ensure-the-zone-for-the-web-application-that-you-want-to-secure-with-azure-ad-is-configured-to-use-ssl"></a>Шаг 2: Убедитесь, что зоны для веб-приложения, которое требуется защитить с помощью Azure AD настроен для использования протокола SSL

Эта статья была написана использование архитектуры ссылку в [запустите высокой доступности фермы SharePoint Server 2016 в Azure](https://docs.microsoft.com/en-us/azure/architecture/reference-architectures/sharepoint). Сопутствующая сценарии со статьей, используемые для развертывания решения, описанного в [данной статье](https://docs.microsoft.com/en-us/azure/architecture/reference-architectures/sharepoint) Создание сайта, который не используется протокол SSL.  

При использовании SAML необходимо настроить приложение для использования протокола SSL. Если веб-приложения SharePoint не настроен для использования протокола SSL, выполните следующие действия для создания самозаверяющего сертификата для настройки веб-приложения для SSL. Эта конфигурация предназначен только для лабораторной среды и не предназначен для рабочей среды. Рабочие среды следует использовать подписанный сертификат.

1. Перейдите в **Центр администрирования** > **Управление приложениями** > **Управление веб-приложениями**и выберите веб-приложение, которое должно быть расширены для использования протокола SSL. Выберите веб-приложение и нажмите кнопку **ленты расширить** . Расширение веб-приложения, чтобы использовать же URL-адрес, но использование SSL с порт 443.<br/>![Расширение веб-приложения на другой сайт служб IIS](media/SAML11/fig3-extendwebapptoiis.png)<br/>
2. В Диспетчер IIS дважды щелкните **Сертификаты сервера**.
3. В области **Действия** нажмите **Создать самозаверяющий сертификат**. Введите понятное имя сертификата в поле Понятное имя сертификата и нажмите кнопку **ОК**.
4. В диалоговом окне **Изменение привязки сайта** убедитесь, что имя узла — это понятное имя, как показано на следующем рисунке.<br/>![Изменение привязки сайта в IIS](media/SAML11/fig4-editsitebinding.png)<br/>

Каждый из интерфейсных веб-серверах в ферме SharePoint требуется Настройка сертификата для привязки сайта в IIS.


## <a name="step-3-create-a-new-enterprise-application-in-azure-ad"></a>Шаг 3: Создание нового корпоративного приложения в Azure AD

1. На портале Azure ([https://portal.azure.com](https://portal.azure.com)), откройте каталог Azure AD. Нажмите кнопку **Корпоративные приложения**, а затем нажмите кнопку **новое приложение**. Выберите **приложение, не коллекции**. Укажите имя, например *SAML интеграции с SharePoint* и нажмите кнопку **Добавить**.<br/>![Добавление нового приложения не галереи](media/SAML11/fig5-addnongalleryapp.png)<br/>
2. Щелкните ссылку единого входа на левой панели навигации для настройки приложения. Измените раскрывающийся список **Режим единого входа** **на основе SAML-входа** для отображения свойства конфигурации SAML для приложения. Настройка со следующими свойствами:<br/>
    - Идентификатор:`urn:sharepoint:portal.contoso.local`
    - URL-адрес для ответа:`https://portal.contoso.local/_trust/default.aspx`
    - Вход в систему URL-адрес.`https://portal.contoso.local/_trust/default.aspx`
    - Идентификатор пользователя:`user.userprincipalname`<br/>
    - Примечание: Не забудьте изменить URL-адреса, заменив *portal.contoso.local* URL-адрес сайта SharePoint, которые необходимо защитить.<br/>
3. Настройка таблицы (как в таблице 1), который включает в себя следующие строки:<br/> 
    - Realm
    - Полный путь к файлу сертификата для подписи SAML
    - SAML единого входа URL-адрес службы (Замените */saml2* */wsfed*)
    - Идентификатор объекта приложения. <br/>
Скопируйте значение *идентификатора* в *области* свойства в таблицу (видеть в таблице 1 ниже.)
4. Сохраните изменения.
5. Щелкните ссылку **настроить (app name)** для доступа к странице настройки единого входа.<br/>![Настройка единого входа на страницу](media/SAML11/fig7-configssopage.png)<br/> 
    -  Щелкните ссылку **SAML сертификат для подписи - необработанные** для загрузки сертификата для подписи SAML как файл с расширением CER-файл. Скопируйте и вставьте полный путь к файлу загруженного в таблицу.
    - Скопируйте и вставьте ссылку SAML единого входа URL-адрес службы в вашей, заменив */saml2* часть URL-адрес */wsfed*.<br/>
6.  Перейдите в области **свойств** для приложения. Скопируйте и вставьте значение идентификатора объекта в таблице, настроенных в шаге 3.<br/>![Область свойств для приложения](media/SAML11/fig8-propertiespane.png)<br/>
7. С помощью значений, сохраненных, убедитесь, что таблицы, настроенных в шаге 3 имеет следующий вид: 1 в таблице ниже.


| В таблице 1: Записываемые значения  |  |
|---------|---------|
|Realm | `urn:sharepoint:portal.contoso.local` |
|Полный путь к файлу сертификата для подписи SAML | `C:/temp/SharePoint SAML Integration.cer`  |
|URL-адрес службы единого входа SAML (заменить /saml2 /wsfed) | `https://login.microsoftonline.com/b1726649-b616-460d-8d20-defab80d476c/wsfed` |
|Идентификатор объекта приложения | `a812f48b-d1e4-4c8e-93be-e4808c8ca3ac` |

> [!IMPORTANT]
> Замените значение */saml2* в URL-адрес */wsfed*. Конечная точка */saml2* будет обрабатываться маркеры SAML 2.0. Конечная точка */wsfed* включает маркеры SAML 1.1 обработки и является обязательным для федерации SharePoint 2016 SAML.

## <a name="step-4-configure-a-new-trusted-identity-provider-in-sharepoint-server-2016"></a>Шаг 4: Настройка нового доверенного поставщика удостоверений в SharePoint Server 2016

Войдите на сервер SharePoint Server 2016 и откройте командную консоль SharePoint 2016. Введите значения $realm, $wsfedurl и $filepath в таблице 1 и выполните следующие команды для настройки нового доверенного поставщика удостоверений.

> [!TIP]
> Хотите узнать больше о работе PowerShell или работе с помощью PowerShell, в статье [SharePoint PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/overview?view=sharepoint-ps). 

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

Затем выполните следующие действия для включения доверенного поставщика удостоверений для вашего приложения.
1. В центре администрирования перейдите на **Управление веб-приложения** и выберите веб-приложение, предназначенное для безопасного с Azure AD. 
2. На ленте щелкните **Поставщики проверки подлинности** и выберите зону, которая будет использоваться.
3. Выберите **доверенный поставщик удостоверений** и выберите определение поставщика, который вы только что зарегистрированные с именем *AzureAD*.  
4. На странице параметров URL-адрес страницы входа выберите **Custom входа в страницу** и укажите значение «/_trust/». 
5. Нажмите кнопку **ОК**.

![Настройка поставщика проверки подлинности](media/SAML11/fig10-configauthprovider.png)

> [!IMPORTANT]
> Важно, необходимо выполнить все действия, включая установку настраиваемых входа на странице «/_trust/», как показано. Конфигурации не будет работать корректно, если выполнены все шаги.

## <a name="step-5-set-the-permissions"></a>Шаг 5: Задайте разрешения

Пользователи, которым будет войти в Azure AD и получить доступ к SharePoint необходимо предоставить доступ к приложению. 

1. На портале Azure откройте каталог Azure AD. Нажмите кнопку **Корпоративные приложения**, а затем выберите **все приложения**. Выберите приложение, которое вы создали ранее (SAML интеграции с SharePoint).
2. Щелкните **пользователи и группы**. 
3. Нажмите кнопку **Добавить пользователя** для добавления пользователя или группы пользователей, которые будут иметь разрешения на вход в SharePoint с помощью Azure AD.
4. Выберите пользователя или группы, а затем нажмите кнопку **назначить**.
 
Пользователь имеет разрешение в Azure AD, но также необходимо предоставить разрешение в SharePoint. Чтобы задать разрешения для доступа к веб-приложение, выполните следующие действия.

1. Откройте Центр администрирования и выберите **Управление приложениями**.
2. На странице **Управление приложениями** в разделе **Веб-приложения** выберите команду **Управление веб-приложениями**.
3. Щелкните соответствующее веб-приложение, а затем выберите пункт **Политика пользователей**.
4. В политике для веб-приложения нажмите кнопку **Добавить пользователей**.<br/>![Поиск пользователя с их имя утверждения](media/SAML11/fig11-searchbynameclaim.png)<br/>
5. В диалоговом окне **Добавление пользователей** щелкните соответствующие зоны в разделе **Зоны**, а затем нажмите кнопку **Далее**.
6. В диалоговом окне **Политика для веб-приложения** в разделе **Выбор пользователей** щелкните значок **Обзор** .
7. В текстовом поле **поиска** введите имя входа для пользователя в каталоге и нажмите кнопку **Найти**. <br/>Пример: *demouser@blueskyabove.onmicrosoft.com*.
8. Под заголовком AzureAD в представлении списка выберите свойство имя и нажмите кнопку **Добавить,** а затем нажмите **кнопку ОК** , чтобы закрыть диалоговое окно.
9. В разделе разрешения выберите **Полный доступ**.<br/>![Предоставление полного доступа к пользователя утверждений](media/SAML11/fig12-grantfullcontrol.png)<br/>
10. Нажмите **Готово**, а затем  **ОК**.

## <a name="step-6-add-a-saml-11-token-issuance-policy-in-azure-ad"></a>Шаг 6: Добавление политики выдача маркеров SAML 1.1 в Azure AD

При создании приложения Azure AD на портале, по умолчанию с помощью SAML 2.0. SharePoint Server 2016 необходимо использовать формат маркеров SAML 1.1. Приведенный ниже сценарий будет удалить политику SAML 2.0 по умолчанию и добавьте новую политику маркеры SAML 1.1 проблему. 

> Этот код требует загрузки сопутствующий [примеры, показывающие взаимодействия с Azure Active Directory графике](https://github.com/kaevans/spsaml11/tree/master/scripts). Если сценарии загрузить ZIP-файл из репозиториев рабочий стол Windows, убедитесь в том разблокировать `MSGraphTokenLifetimePolicy.psm1` файл сценария модуля и `Initialize.ps1` файл сценария (щелкните правой кнопкой мыши свойства, нажмите кнопку разблокировать, нажмите кнопку ОК). ![Разблокировка загружаемых файлов](media/SAML11/fig17-unblock.png)

После загрузки пример сценария создать новый сценарий PowerShell, путем добавления следующего кода, заменив заполнитель путь к файлу загруженного `Initialize.ps1` на локальном компьютере. Замените заполнитель идентификатор объекта приложения идентификатор объекта приложения, который был введен в таблице 1. После создания выполните сценарий PowerShell. 

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
> Не подписи скриптов PowerShell и может потребоваться задать политику выполнения. Дополнительные сведения о политиках выполнения видеть [О политиках выполнения](http://go.microsoft.com/fwlink/?LinkID=135170). Кроме того необходимо открыть окно командной строки с повышенными привилегиями, для успешного выполнения команд, содержащихся в примеры сценариев.

Эти команды PowerShell пример приведены примеры того, как для выполнения запросов к API графике. Для получения дополнительных сведений о маркеров политики выдачи с Azure AD видеть [Справочник по API график для операций в политике](https://msdn.microsoft.com/en-us/library/azure/ad/graph/api/policy-operations#create-a-policy).

## <a name="step-7-verify-the-new-provider"></a>Шаг 7: Проверка нового поставщика

Откройте браузер на URL-адрес веб-приложения, настроенного на предыдущих шагах. Вы будете перенаправлены для входа в Azure AD.

![Вход в Azure AD, настроенных для федерации](media/SAML11/fig13-examplesignin.png)

Запрос следует ли выполнять выход.

![Будьте в курсе выполнен вход?](media/SAML11/fig14-staysignedin.png)

И, наконец можно доступ к сайту, войти в систему под учетной записью пользователя от клиента Azure Active Directory.

![Пользователь вошел в SharePoint](media/SAML11/fig15-signedinsharepoint.png)

## <a name="managing-certificates"></a>Управление сертификатами
Важно понимать, что имеет дату окончания срока действия сертификата для подписи, который был настроен для доверенного поставщика удостоверений в приведенном выше шаге 4 и должны обновляться. В статье [Управление сертификатами для федеративного единого входа в Azure Active Directory](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-sso-certs) для получения сведений на Продление сертификата. После обновления сертификата в Azure AD загрузить локальный файл и используйте приведенный ниже сценарий для настройки доверенного поставщика удостоверений с обновленного сертификата для подписи. 

```
$filepath="<Full path to renewed SAML signing certificate file>"
$cert= New-Object System.Security.Cryptography.X509Certificates.X509Certificate2($filePath)
New-SPTrustedRootAuthority -Name "AzureAD" -Certificate $cert
Get-SPTrustedIdentityTokenIssuer "AzureAD" | Set-SPTrustedIdentityTokenIssuer -ImportTrustCertificate $cert
```
## <a name="configuring-one-trusted-identity-provider-for-multiple-web-applications"></a>Настройка одного доверенного поставщика удостоверений для нескольких веб-приложений
Конфигурация работает для одного веб-приложения, но требуется дополнительная настройка, если вы намерены использовать же доверенного поставщика удостоверений для нескольких веб-приложений. Например, предположим, мы расширенного веб-приложение для использования URL-адрес `https://portal.contoso.local` и теперь требуется проверка подлинности пользователей для `https://sales.contoso.local` также. Для этого необходимо обновить поставщика удостоверений для поддерживать параметра WReply и обновления регистрации приложения в Azure AD для добавления URL-адрес ответа.

1. На портале Azure откройте каталог Azure AD. Щелкните **Регистрация приложения**, а затем щелкните **Просмотр всех приложений**. Выберите приложение, которое вы создали ранее (SAML интеграции с SharePoint).
2. Нажмите кнопку **Параметры**.
3. В blade параметры щелкните **URL-адреса ответа**. 
4. Добавьте URL-адрес для дополнительных веб-приложения с помощью `/_trust/default.aspx` добавляется в конец URL-адреса (например, `https://sales.contoso.local/_trust/default.aspx`) и нажмите кнопку **Сохранить**. 
5. На сервере SharePoint откройте **Командную консоль SharePoint 2016** и выполните следующие команды, используя имя надежный поставщик маркеров удостоверений, который использовался ранее.

```
$t = Get-SPTrustedIdentityTokenIssuer "AzureAD"
$t.UseWReplyParameter=$true
$t.Update()
```
6. В центре администрирования перейдите на веб-приложения и включить существующий доверенного поставщика удостоверений. Не забудьте также настроить URL-адрес страницы входа в качестве настраиваемая страница входа `/_trust/`.
7. В центре администрирования щелкните веб-приложение и выберите **Политика пользователя**. Добавление пользователя с соответствующими разрешениями, как было показано ранее в этой статье.

## <a name="fixing-people-picker"></a>Исправление "Выбор людей"
Пользователи могут теперь войдите в 2016 SharePoint с помощью удостоверения от Azure AD, но по-прежнему существуют возможности для улучшения взаимодействия с пользователем. Например поиск пользователя представляет нескольких результатов поиска в средстве выбора людей. Нет результатов поиска для каждого из типов 3 утверждения, которые были созданы в сопоставлении утверждений. Чтобы выбрать пользователя, с помощью средства выбора людей, необходимо точно введите свои имя пользователя и выберите **имя** утверждения результатов.

![Результаты поиска утверждений](media/SAML11/fig16-claimssearchresults.png)

Проверка на значения, которые вы поиска, что может привести к орфографические ошибки не или утверждений пользователи случайно Выбор неправильный тип для назначения, такие как **Фамилия** утверждения. Это может запретить пользователям успешно доступ к ресурсам.

Чтобы упростить этот сценарий, является открытым кодом решения вызывается [AzureCP](https://yvand.github.io/AzureCP/) , который предоставляет пользовательского поставщика утверждений для SharePoint 2016. Он будет использоваться на графике Azure AD для решения, что пользователи вводят и выполнить проверку. Дополнительные [AzureCP](https://yvand.github.io/AzureCP/). 

## <a name="additional-resources"></a>Дополнительные ресурсы

[Общие сведения о WS-Federation](https://go.microsoft.com/fwlink/p/?linkid=188052)
  
[Освоение облака и гибридные решения](cloud-adoption-and-hybrid-solutions.md)
  
## <a name="join-the-discussion"></a>Присоединяйтесь к обсуждению

|**Свяжитесь с нами**|**Описание**|
|:-----|:-----|
|**Какое вам решение необходимо?** <br/> |Мы создаем контент для решений, которые охватывают несколько продуктов и служб Майкрософт. Сообщите нам, что вы думаете о наших межсерверных решениях, или укажите интересующие вас решения, написав по адресу [MODAcontent@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20).<br/> |
|**Присоединяйтесь к обсуждению решений** <br/> |Если вам интересны облачные решения, присоединяйтесь к теме Cloud Adoption Advisory Board (CAAB) и общайтесь с разработчиками контента Майкрософт, специалистами отрасли и клиентами со всего мира. Чтобы присоединиться, добавьте себя в качестве участника [темы CAAB (Cloud Adoption Advisory Board)](https://aka.ms/caab) на сайте Microsoft Tech Community и отправьте нам письмо на адрес [CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!). Просматривать материалы в [блоге CAAB](https://blogs.technet.com/b/solutions_advisory_board/) могут все пользователи. Однако только участники CAAB получают приглашения на закрытые вебинары, на которых мы рассказываем о новых облачных решениях и ресурсах по их внедрению.<br/> |
|**Скачать изображения, которые вы видите здесь** <br/> |Если вам нужна редактируемая копия иллюстративного материала из этой статьи, мы с радостью вам ее отправим. Напишите нам, указав URL-адрес и название материала, по адресу [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20).<br/> |
   

