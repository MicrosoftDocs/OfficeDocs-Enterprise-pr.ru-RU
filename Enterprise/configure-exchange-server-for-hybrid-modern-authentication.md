---
title: Как настроить локальное развертывание Exchange Server для использования гибридной современной проверки подлинности
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 09/28/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: cef3044d-d4cb-4586-8e82-ee97bd3b14ad
description: Гибридные современных проверки подлинности (НЕГО) — это метод управления удостоверениями, который обеспечивает более безопасной проверки подлинности пользователя и авторизации и доступна для гибридного развертывания Exchange server в локальной.
ms.openlocfilehash: 4267eaff8dfce71461f230310141a98be8a39e80
ms.sourcegitcommit: 9f921c0cae9a5dd4e66ec1a1261cb88284984a91
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/28/2018
ms.locfileid: "25347609"
---
# <a name="how-to-configure-exchange-server-on-premises-to-use-hybrid-modern-authentication"></a>Как настроить локальное развертывание Exchange Server для использования гибридной современной проверки подлинности

Гибридные современных проверки подлинности (НЕГО) — это метод управления удостоверениями, который обеспечивает более безопасной проверки подлинности пользователя и авторизации и доступна для гибридного развертывания Exchange server в локальной.
  
## <a name="fyi"></a>FYI

Прежде чем начать, ли вызов:
  
- Современный проверки подлинности гибридной \> НЕГО
    
- Exchange в локальной \> EXCH
    
- Exchange Online \> EXO
    
Кроме того, *Если графического элемента в этой статье есть объект, который «серым» или «неактивен», что означает, что элемент, приведенные в серый цвет не входит в НЕГО конфигурации* . 
  
## <a name="enabling-hybrid-modern-authentication"></a>Включение проверки подлинности гибридной современных

Для включения НЕГО означает, что:
  
1. Необходимо выполнить проверка готовности, прежде чем приступить к работе.
    
1. С момента множество **необходимых компонентов** являются общими для обоих Скайп для бизнеса и Exchange, [Обзор проверки подлинности гибридной современных и необходимые условия для использования с локальной Скайп для серверов Exchange и бизнес](hybrid-modern-auth-overview.md). Это необходимо сделать, прежде чем начать, какие-либо действия, описанные в этой статье.
    
2. Добавление локального URL-адреса служб web как имена участников-служб (SPN) в Azure AD.
    
3. Проверка всех виртуальных каталогов, включены для НЕГО
    
4. Проверка для объекта EvoSTS проверкой подлинности на основе сервера
    
5. Включение НЕГО в курс
    
 **Примечание** Поддерживает ли агент Управления вашей версии Office? В разделе [того, как современные выполняется проверка подлинности для Office 2013 и Office 2016 клиентских приложений](modern-auth-for-office-2013-and-2016.md).
  
## <a name="make-sure-you-meet-all-the-pre-reqs"></a>Убедитесь, что выполнены все предварительные условия

Поскольку множество необходимых компонентов являются общими для обоих Скайп для бизнеса и Exchange, просмотрите [Обзор проверки подлинности гибридной современных и необходимые условия для использования с Скайп локальных серверов Exchange и бизнес](hybrid-modern-auth-overview.md). Сделать этот *перед* началом работы какие-либо действия, описанные в этой статье. 
  
## <a name="add-on-premises-web-service-urls-as-spns-in-azure-ad"></a>Добавление локального веб-службы URL-адреса как имена участников-служб в Azure AD

Запуск команды, которые присвоить локального веб-службы URL-адреса, как имена участников-служб Azure AD. имена участников-служб используются с клиентских компьютеров и устройств во время проверки подлинности и авторизации. Все URL-адреса, которые могут использоваться для подключения через локальную для Azure Active Directory (AAD) должны быть зарегистрированы в AAD (включая внутренних и внешних пространств имен).
  
Во-первых необходимо Соберите все URL-адреса, которые необходимо добавить в AAD. Выполните следующие команды в локальной:
  
```powershell
Get-MapiVirtualDirectory | FL server,*url*
Get-WebServicesVirtualDirectory | FL server,*url*
Get-ActiveSyncVirtualDirectory | FL server,*url*
Get-OABVirtualDirectory | FL server,*url*
```
    
Проверьте URL-адреса, клиенты могут подключаться к присутствовала HTTPS имена участников-служб в AAD.
  
1. Во-первых подключение к AAD с [этим инструкциям](https://docs.microsoft.com/en-us/office365/enterprise/powershell/connect-to-office-365-powershell).
    
2. Для обмена связанные URL-адреса, введите следующую команду:
    
```powershell
Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 | select -ExpandProperty ServicePrincipalNames
```

Принимать сообщения с (и снимок экрана для дальнейшего сравнения) выходные данные этой команды, которая должна включать https:// *autodiscover.yourdomain.com* и URL-адрес https:// *mail.yourdomain.com* , но большей части состоят из имен участников-служб, начинающихся с 00000002-0000-0ff1-ce00-000000000000 /. При наличии https:// URL-адресов из своей локальной, которые не указаны необходимо добавить записи, определенные в этот список. 
  
3. Если своих внутренних и внешних MAPI/HTTP, веб-служб Exchange, ActiveSync, автономной адресной книги и автоматического обнаружения записей в этом списке не отображается, необходимо добавить их с помощью приведенной ниже команды (примере используются URL-адреса "`mail.corp.contoso.com`«и»`owa.contoso.com`", но было **Заменить примеры URL-адресов с помощью собственного** ) : <br/>
```powershell
$x= Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000   
$x.ServicePrincipalnames.Add("https://mail.corp.contoso.com/")
$x.ServicePrincipalnames.Add("https://owa.contoso.com/")
$x.ServicePrincipalnames.Add("https://eas.contoso.com/")
Set-MSOLServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $x.ServicePrincipalNames
```
 
4. Убедитесь, что были добавлены новые записи, выполнив команду Get-MsolServicePrincipal на шаге 2 еще раз и просмотр выходных данных. Сравните список / снимок экрана с перед новый список имен участников-служб (можно также снимок экрана нового списка для записи). Если вы было выполнено успешно, вы увидите две новые URL-адресов в списке. Переход в нашем примере список имен участников-служб будут включать конкретные URL-адреса `https://mail.corp.contoso.com` и `https://owa.contoso.com`. 
  
## <a name="verify-virtual-directories-are-properly-configured"></a>Убедитесь, что правильно настроить виртуальные каталоги

Теперь проверьте OAuth должным образом включены в Exchange на всех виртуальных каталогов Outlook может использовать, выполнив следующие команды:

```powershell
Get-MapiVirtualDirectory | FL server,*url*,*auth* 
Get-WebServicesVirtualDirectory | FL server,*url*,*oauth*
Get-OABVirtualDirectory | FL server,*url*,*oauth*
Get-AutoDiscoverVirtualDirectory | FL server,*oauth*
```

Проверка выходные данные в убедитесь в том, **OAuth** включен на каждом из этих VDirs, он будет выглядеть примерно следующим образом (и всего рассмотрение является «OAuth»); 

```powershell
Get-MapiVirtualDirectory | fl server,*url*,*auth*
```

```
Server                        : EX1
InternalUrl                   : https://mail.contoso.com/mapi
ExternalUrl                   : https://mail.contoso.com/mapi
IISAuthenticationMethods      : {Ntlm, OAuth, Negotiate}
InternalAuthenticationMethods : {Ntlm, OAuth, Negotiate}
ExternalAuthenticationMethods : {Ntlm, OAuth, Negotiate}
```
  
Если отсутствует OAuth с любого сервера и любой из четырех виртуальных каталогов необходимо добавить его с помощью нужных команд перед тем как перейти.
  
## <a name="confirm-the-evosts-auth-server-object-is-present"></a>Убедитесь, что отображается объект EvoSTS проверкой подлинности на основе сервера

Вернуться к локальной Командная консоль Exchange для этой команды последнего. Теперь можно проверить, что локальную имеется запись evoSTS поставщика проверки подлинности:
  
```powershell
Get-AuthServer | where {$_.Name -eq "EvoSts"}
```

Выходные данные должны быть показаны AuthServer EvoSts имя и состояние «Включено» должно быть значение True. Если это не отображается, следует Загрузите и запустите последнюю версию мастера гибридной конфигурации.
  
 **Важные** Если вы используете Exchange 2010 в вашей среде, не создается поставщик проверки подлинности EvoSTS. 
  
## <a name="enable-hma"></a>Включите в НЕГО

Выполните следующую команду в командной консоли Exchange, в локальной:

```powershell
Set-AuthServer -Identity EvoSTS -IsDefaultAuthorizationEndpoint $true  
Set-OrganizationConfig -OAuth2ClientProfileEnabled $true
```
    
## <a name="verify"></a>"Проверить"

После включения НЕГО клиента следующем входе в систему будет использовать новый поток проверки подлинности. Обратите внимание на то, что только что включение НЕГО не запустит повторная проверка подлинности для любого клиента. Клиенты повторно пройти проверку подлинности на основе времени жизни проверкой подлинности на основе маркеров и/или сертификаты у них.
  
Также следует удерживайте нажатой клавишу CTRL, в то же время, щелкните значок правой кнопкой мыши для клиентов Outlook (а также в области уведомлений Windows) и нажмите кнопку «Состояние подключения». Найдите SMTP-адрес клиента с типом «Определения» "носителя\*", который представляет маркер носителя, используемый в OAuth.
  
 **Примечание** Необходимо настроить Скайп для бизнеса с НЕГО? Вам потребуются две статьи:, в котором приведены [Поддерживаемые топологии](https://technet.microsoft.com/en-us/library/mt803262.aspx)и показано, [как для выполнения конфигурации](configure-skype-for-business-for-hybrid-modern-authentication.md).
  

## <a name="related-topics"></a>Смежные темы

[Обзор проверки подлинности на современном гибридной среды и необходимые условия для использования его с Скайп локальных серверов Exchange и бизнес-](hybrid-modern-auth-overview.md) 
  

