---
title: Управление конечными точками Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 7/18/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365_Setup
search.appverid: MOE150
ms.assetid: 99cab9d4-ef59-4207-9f2b-3728eb46bf9a
description: Некоторые сети предназначены для ограничения доступа к Интернету, чтобы убедиться, что компьютеры в сети, как они могут получить доступ к Office 365, администраторов сети и прокси-сервер должен управлять список полных доменных имен, URL-адреса, а IP-адресов, будут включены в список конечных точках Office 365. Эти потребности для добавления правила прокси-сервера или брандмауэра и PAC файлы для обеспечения сетевых запросов дают возможность связи с Office 365.
ms.openlocfilehash: 42613b45b8395c3f81064bbc2171866bc922a657
ms.sourcegitcommit: ca4d3ec34300d7d39f1a42dc6f29a34915de5c87
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/05/2018
ms.locfileid: "23831924"
---
# <a name="managing-office-365-endpoints"></a>Управление конечными точками Office 365

## <a name="office-365-network-connectivity"></a>Подключение к сети Office 365

 Подключение к Office 365 состоят из большой поток запросов надежной сети, выполняющие лучше всего, когда они состоят через выходной небольшой задержкой, рядом с пользователем. Некоторые подключения к Office 365, могут воспользоваться преимуществами оптимизации подключение. 
  
1. Убедитесь, брандмауэр разрешить списки разрешенных для подключения к конечным точкам Office 365.
    
2. Используйте инфраструктуры прокси-сервера, чтобы разрешить подключение к Интернету для подстановочные знаки и отменить публикацию назначения.
    
3. Ведение конфигурация оптимальную пограничной сети.
    
4. [Убедитесь, что они будут наиболее подключения](https://aka.ms/o365perfprinciples).
    
5. Чтение [Сетевого подключения к Office 365 принципы](office-365-network-connectivity-principles.md) понять принципы подключения для безопасного управления Office 365 трафика и начало обеспечить максимально высокую производительность. 
    
![Подключение к Office 365 через брандмауэров и прокси-серверов.](media/34d402f3-f502-42a0-8156-24a7c4273fa5.png)
  
## <a name="update-your-firewalls-outbound-allow-lists"></a>Обновление брандмауэра исходящих списков

Можно оптимизировать сети, отправив все доверенных Office 365 сетевые запросы непосредственно через брандмауэр, обход всех проверку уровня дополнительных пакетов или обработки. Это уменьшает снижения производительности из задержку и уменьшает требований к мощности демилитаризованной зоны. Выбрать, какие сетевые запросы на доверие проще всего использовать наш готовые файлы PAC на вкладке **прокси-серверы** выше. 
  
Если исходящий трафик блоки вашего брандмауэра, может потребоваться обеспечить соблюдение IP-адресов и полных доменных имен указано, что **требуется** в [XML-файл](https://go.microsoft.com/fwlink/?LinkId=533185) включены в список разрешений. Распознавать все службы требуют использования служб, сторонних производителей. Мы не предоставляют IP-адреса для этих сторонних производителей службы, такие как поставщиков поставщиков сети доставки содержимого, DNS и так далее. Для полной функциональности Office 365 необходимо сделать доступными все назначения по Office 365 запросу независимо от того, объем сведений, мы публикации о назначении. 
  
Множество назначений опубликовано IP-адрес или не представлены в виде домена подстановочные знаки без определенного полного доменного имени, для использования этой функции необходимо иметь возможность устранения сетевые запросы текущий IP-адрес был запрошен и отправки сетевой запрос через Интернет.
  
Автоматизация процесса с помощью брандмауэра, который выполняет синтаксический анализ XML-файла от вашего имени и обновляет правил автоматически на основе служб или компонентов, которые предполагается маршрутизировать непосредственно через брандмауэр. Можно также использовать средство [Диапазон Azure](https://azurerange.azurewebsites.net/) , которая создала сообщества и анализ XML-код для вас с параметры экспорта для конфигурации списка Cisco XE маршрута или списка управления Доступом, обычный текст или CSV. 
  
Больше описание назначения сети доступен на веб- [сайт ссылку](urls-and-ip-address-ranges.md) также в наш [RSS-канал на основе журнала изменений](https://go.microsoft.com/fwlink/p/?linkid=236301) , можно подписаться на изменения. 
  
<a name="pacfiles"> </a>
## <a name="configure-outbound-paths-with-pac-files"></a>Настройка исходящего пути с помощью PAC-файлов

Используйте PAC или WPAD файлов для управления сетевых запросов, которые связаны с Office 365, но не предоставляются IP-адреса. Типичные сетевые запросы, отправляемые через прокси-сервер или периметра устройство требует дополнительных задержки. Во время проверки подлинности прокси-сервера приводит к наибольшим налогах, другие службы, включая репутации подстановки и попытки проверки пакетов может привести к низкого уровня пользовательского интерфейса. Кроме того эти устройства сети периметра должны достаточную емкость для обработки всех запросов сети. Мы рекомендуем обход прокси-сервера или проверка на наличие инфраструктуры для прямой запрос сети Office 365.
  
Используйте один из наших файлов PAC качестве отправной точки для определения какие сетевого трафика будут отправляться на прокси-сервер и которого будут отправляться брандмауэр. Если вы не знакомы с PAC или WPAD файлов, прочитайте этой записи о [файлах развертывание PAC](https://blogs.technet.microsoft.com/undocumentedfeatures/2016/04/06/deploying-the-office-365-proxy-pac-to-manage-your-users/) из одного из наших консультанты Office 365. Вы наверняка хотели бы просмотрите их в качестве отправной точки и изменить в соответствии с вашей средой. 
  
 **Обновлено 7/10/2018 PAC файлов**. 
  
### <a name="1---pac-file-separates-required-internet-fqdns-from-known-office-365-fqdn"></a>#1 - файл PAC: разделяет требуется Internet полные доменные имена из полного доменного ИМЕНИ для известных Office 365.

Первый пример представляет демонстрационный наших рекомендуемый подход к управлению конечных точек через Интернет только. Обходит прокси-сервера для Office 365 назначения, где будет опубликована IP-адрес и отправляет запросы на оставшихся сетевой прокси-сервер.
  
Фрагмент кода:

```javascript
// JavaScript source code
//July 2018 - Updates go live 1st August2018
//This PAC file contains all FQDNs needed for all services and splits the traffic between those which Microsoft can provide IPs for (so can be sent through a managed firewall with conditional access if desired) and those which IPs cannot be provided for, so need to go to an unrestricted proxy or egress. 
//Due to the use of wildcards, some extra logic is provided to send traffic to the proxy before a 'direct' wildcard is hit.
//Includes Core ProPlus URLs but not Office Mobile/IPAD/IOS/ANDROID fqdns from https://support.office.com/en-gb/article/Network-requests-in-Office-365-ProPlus-eb73fcd1-ca88-4d02-a74b-2dd3a9f3364d
//Every Effort is made to ensure 100% accuracy but this PAC should be used as an example and cross-checked with your needs and the Office 365 URL &amp; IP page
//Intended only for Worldwide Office 365 instances, which the vast majority of customers will be using
function FindProxyForURL(url, host)
{
    // Define proxy server
    var proxyserver = "PROXY 10.10.10.10:8080";
    var proxyserver2 = "PROXY 10.10.10.11:8080";
    // Make host lowercase
    var lhost = host.toLowerCase();
    host = lhost;
    //Catch explicit FQDNs which need the proxy but are covered under wildcarded FQDNs which have IPs. This has to be done first before the wildcard is hit
    if ((shExpMatch(host, "quicktips.skypeforbusiness.com"))    
        || (shExpMatch(host, "*.um.outlook.com"))
        || (shExpMatch(host, "r3.res.office365.com"))
        || (shExpMatch(host, "r3.res.outlook.com"))
        || (shExpMatch(host, "r4.res.office365.com"))
        || (shExpMatch(host, "xsi.outlook.com"))
        || (shExpMatch(host, "r1.res.office365.com")))
    {
        return proxyserver;
    }
        //Send FQDNs which Microsoft provide IPs for direct, so they can be sent via a firewall
    else if ((isPlainHostName(host))
    || (shExpMatch(host, "*.aria.microsoft.com"))    
    || (shExpMatch(host, "*.dc.trouter.io"))
    || (shExpMatch(host, "*.lync.com"))
    || (shExpMatch(host, "*.manage.office.com"))
    || (shExpMatch(host, "*.office365.com"))
    || (shExpMatch(host, "*.onenote.com"))
    || (shExpMatch(host, "*.outlook.com"))
    || (shExpMatch(host, "*.outlook.office.com"))
    || (shExpMatch(host, "*.portal.cloudappsecurity.com"))
    || (shExpMatch(host, "*.protection.office.com"))
    || (shExpMatch(host, "*.sharepoint.com"))
    || (shExpMatch(host, "*.skype.com"))
    || (shExpMatch(host, "*.skypeforbusiness.com"))
    || (shExpMatch(host, "*.svc.ms"))
    || (shExpMatch(host, "*.teams.microsoft.com"))
    || (shExpMatch(host, "*.yammer.com"))
    || (shExpMatch(host, "*.yammerusercontent.com"))    
    || (shExpMatch(host, "*broadcast.officeapps.live.com"))
    || (shExpMatch(host, "*excel.officeapps.live.com"))
    || (shExpMatch(host, "*onenote.officeapps.live.com"))
    || (shExpMatch(host, "*powerpoint.officeapps.live.com"))
    || (shExpMatch(host, "*view.officeapps.live.com"))
    || (shExpMatch(host, "*visio.officeapps.live.com"))
    || (shExpMatch(host, "*word-edit.officeapps.live.com"))
    || (shExpMatch(host, "*word-view.officeapps.live.com"))
    || (shExpMatch(host, "admin.microsoft.com"))    
    || (shExpMatch(host, "account.office.net"))
    || (shExpMatch(host, "adminwebservice.microsoftonline.com"))
    || (shExpMatch(host, "agent.office.net"))
    || (shExpMatch(host, "api.login.microsoftonline.com"))
    || (shExpMatch(host, "api.passwordreset.microsoftonline.com"))
    || (shExpMatch(host, "apc.delve.office.com"))
    || (shExpMatch(host, "aus.delve.office.com"))
    || (shExpMatch(host, "autologon.microsoftazuread-sso.com"))  
    || (shExpMatch(host, "becws.microsoftonline.com"))
    || (shExpMatch(host, "browser.pipe.aria.microsoft.com"))  
    || (shExpMatch(host, "can.delve.office.com"))
    || (shExpMatch(host, "ccs.login.microsoftonline.com"))
    || (shExpMatch(host, "ccs-sdf.login.microsoftonline.com"))
    || (shExpMatch(host, "clientconfig.microsoftonline-p.net"))
    || (shExpMatch(host, "clientlog.portal.office.com"))
    || (shExpMatch(host, "companymanager.microsoftonline.com"))
    || (shExpMatch(host, "cus-000.tasks.osi.office.net"))
    || (shExpMatch(host, "delve.office.com"))
    || (shExpMatch(host, "device.login.microsoftonline.com"))    
    || (shExpMatch(host, "ea-000.tasks.osi.office.net"))
    || (shExpMatch(host, "eur.delve.office.com"))
    || (shExpMatch(host, "eus-zzz.tasks.osi.office.net"))
    || (shExpMatch(host, "gbr.delve.office.com"))    
    || (shExpMatch(host, "hip.microsoftonline-p.net"))
    || (shExpMatch(host, "hipservice.microsoftonline.com"))
    || (shExpMatch(host, "home.office.com"))
    || (shExpMatch(host, "ind.delve.office.com"))
    || (shExpMatch(host, "jpn.delve.office.com"))
    || (shExpMatch(host, "kor.delve.office.com"))
    || (shExpMatch(host, "lam.delve.office.com"))
    || (shExpMatch(host, "login.microsoft.com"))
    || (shExpMatch(host, "login.microsoftonline.com"))
    || (shExpMatch(host, "login.microsoftonline-p.com"))
    || (shExpMatch(host, "login.windows.net"))
    || (shExpMatch(host, "logincert.microsoftonline.com"))
    || (shExpMatch(host, "loginex.microsoftonline.com"))
    || (shExpMatch(host, "login-us.microsoftonline.com"))     
    || (shExpMatch(host, "manage.office.com"))
    || (shExpMatch(host, "mobile.pipe.aria.microsoft.com"))
    || (shExpMatch(host, "nam.delve.office.com"))
    || (shExpMatch(host, "neu-000.tasks.osi.office.net"))
    || (shExpMatch(host, "nexus.microsoftonline-p.com"))
    || (shExpMatch(host, "nexus.officeapps.live.com"))
    || (shExpMatch(host, "nexusrules.officeapps.live.com"))
    || (shExpMatch(host, "office.live.com"))
    || (shExpMatch(host, "officeapps.live.com"))
    || (shExpMatch(host, "passwordreset.microsoftonline.com"))
    || (shExpMatch(host, "portal.microsoftonline.com"))
    || (shExpMatch(host, "portal.office.com"))
    || (shExpMatch(host, "protection.office.com"))
    || (shExpMatch(host, "provisioningapi.microsoftonline.com"))
    || (shExpMatch(host, "scsinstrument-ss-us.trafficmanager.net"))   
    || (shExpMatch(host, "scsquery-ss-asia.trafficmanager.net")) 
    || (shExpMatch(host, "scsquery-ss-eu.trafficmanager.net")) 
    || (shExpMatch(host, "scsquery-ss-us.trafficmanager.net"))
    || (shExpMatch(host, "sea-000.tasks.osi.office.net"))    
    || (shExpMatch(host, "stamp2.login.microsoftonline.com"))
    || (shExpMatch(host, "suite.office.net"))    
    || (shExpMatch(host, "tasks.office.com"))
    || (shExpMatch(host, "teams.microsoft.com"))
    || (shExpMatch(host, "testconnectivity.microsoft.com"))
    || (shExpMatch(host, "webshell.suite.office.com"))
    || (shExpMatch(host, "weu-000.tasks.osi.office.net"))
    || (shExpMatch(host, "wus-000.tasks.osi.office.net"))
    || (shExpMatch(host, "www.office.com")))

    {
        return "DIRECT";
    }
    else
        // Send all unknown IP traffic to Proxy for unrestricted access. This section is not necessary if you have a catchall for all other traffic to go to an unfiltered proxy. 
        //However the fqdns required, but for which we dont have IPs for, are listed here incase you need an explicit list.
   if          ((shExpMatch(host, "*.aadrm.com"))
        || (shExpMatch(host, "*.adhybridhealth.azure.com")) 
        || (shExpMatch(host, "*.adl.windows.com"))   
        || (shExpMatch(host, "*.api.microsoftstream.com"))      
        || (shExpMatch(host, "*.assets-yammer.com"))   
        || (shExpMatch(host, "*.azureedge.net"))            
        || (shExpMatch(host, "*.azurerms.com"))
        || (shExpMatch(host, "*.cloudapp.net"))
        || (shExpMatch(host, "*.entrust.net")) 
        || (shExpMatch(host, "*.geotrust.com"))   
        || (shExpMatch(host, "*.helpshift.com"))   
        || (shExpMatch(host, "*.hockeyapp.net"))    
        || (shExpMatch(host, "*.localytics.com"))    
        || (shExpMatch(host, "*.log.optimizely.com"))    
        || (shExpMatch(host, "*.microsoft.com"))
        || (shExpMatch(host, "*.microsoftonline.com"))
        || (shExpMatch(host, "*.microsoftonline-p.com"))
        || (shExpMatch(host, "*.microsoftonline-p.net"))
        || (shExpMatch(host, "*.msecnd.net"))
        || (shExpMatch(host, "*.msedge.net"))      
        || (shExpMatch(host, "*.msocdn.com")) 
        || (shExpMatch(host, "*.mstea.ms"))    
        || (shExpMatch(host, "*.notification.api.microsoftstream.com")) 
        || (shExpMatch(host, "*.o365weve.com"))     
        || (shExpMatch(host, "*.office.com"))   
        || (shExpMatch(host, "*.office.net"))
        || (shExpMatch(host, "*.omniroot.com"))
        || (shExpMatch(host, "*.onmicrosoft.com"))
        || (shExpMatch(host, "*.phonefactor.net"))
        || (shExpMatch(host, "*.public-trust.com"))
        || (shExpMatch(host, "*.search.production.apac.trafficmanager.net"))
        || (shExpMatch(host, "*.search.production.emea.trafficmanager.net"))
        || (shExpMatch(host, "*.search.production.us.trafficmanager.net"))
        || (shExpMatch(host, "*.secure.skypeassets.com"))  
        || (shExpMatch(host, "*.sfbassets.com"))
        || (shExpMatch(host, "*.sharepointonline.com"))
        || (shExpMatch(host, "*.sway.com"))
        || (shExpMatch(host, "*.symcb.com"))
        || (shExpMatch(host, "*.teams.microsoft.com"))  
        || (shExpMatch(host, "*.tenor.com"))  
        || (shExpMatch(host, "*.symcd.com"))     
        || (shExpMatch(host, "*.users.storage.live.com"))
        || (shExpMatch(host, "*.verisign.com"))
        || (shExpMatch(host, "*.verisign.net"))
        || (shExpMatch(host, "*.windows.net"))
        || (shExpMatch(host, "*cdn.onenote.net"))
        || (shExpMatch(host, "account.activedirectory.windowsazure.com"))
        || (shExpMatch(host, "ad.atdmt.com"))
        || (shExpMatch(host, "admin.onedrive.com"))
        || (shExpMatch(host, "ajax.aspnetcdn.com"))
        || (shExpMatch(host, "aka.ms"))
        || (shExpMatch(host, "amp.azure.net"))
        || (shExpMatch(host, "api.microsoftstream.com"))
        || (shExpMatch(host, "apis.live.net"))  
        || (shExpMatch(host, "apps.identrust.com"))  
        || (shExpMatch(host, "assets.onestore.ms"))
        || (shExpMatch(host, "auth.gfx.ms"))
        || (shExpMatch(host, "cacerts.digicert.com"))        
        || (shExpMatch(host, "cdn.odc.officeapps.live.com"))  
        || (shExpMatch(host, "cdn.onenote.net"))
        || (shExpMatch(host, "cdn.optimizely.com")) 
        || (shExpMatch(host, "cert.int-x3.letsencrypt.org"))
        || (shExpMatch(host, "client.hip.live.com"))
        || (shExpMatch(host, "connect.facebook.net"))        
        || (shExpMatch(host, "crl.globalsign.com"))
        || (shExpMatch(host, "crl.globalsign.net"))
        || (shExpMatch(host, "crl.identrust.com"))    
        || (shExpMatch(host, "crl3.digicert.com"))  
        || (shExpMatch(host, "crl4.digicert.com"))
        || (shExpMatch(host, "cus-odc.officeapps.live.com"))              
        || (shExpMatch(host, "cus-roaming.officeapps.live.com"))
        || (shExpMatch(host, "dc.services.visualstudio.com"))
        || (shExpMatch(host, "domains.live.com"))
        || (shExpMatch(host, "ea-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "ea-roaming.officeapps.live.com"))          
        || (shExpMatch(host, "ecn.dev.virtualearth.net "))   
        || (shExpMatch(host, "eus2-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "eus2-roaming.officeapps.live.com"))             
        || (shExpMatch(host, "eus-odc.officeapps.live.com"))         
        || (shExpMatch(host, "eus-www.sway-cdn.com"))
        || (shExpMatch(host, "eus-www.sway-extensions.com"))        
        || (shExpMatch(host, "firstpartyapps.oaspapps.com"))
        || (shExpMatch(host, "g.live.com"))
        || (shExpMatch(host, "groupsapi2-prod.outlookgroups.ms"))  
        || (shExpMatch(host, "groupsapi3-prod.outlookgroups.ms"))  
        || (shExpMatch(host, "groupsapi4-prod.outlookgroups.ms"))  
        || (shExpMatch(host, "groupsapi-prod.outlookgroups.ms"))   
        || (shExpMatch(host, "isrg.trustid.ocsp.identrust.com"))   
        || (shExpMatch(host, "liverdcxstorage.blob.core.windowsazure.com"))
        || (shExpMatch(host, "management.azure.com"))        
        || (shExpMatch(host, "mem.gfx.ms"))
        || (shExpMatch(host, "mrodevicemgr.officeapps.live.com"))      
        || (shExpMatch(host, "ncus-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "ncus-roaming.officeapps.live.com"))                
        || (shExpMatch(host, "neu-000.ocws.officeapps.live.com")) 
        || (shExpMatch(host, "neu-odc.officeapps.live.com"))         
        || (shExpMatch(host, "neu-roaming.officeapps.live.com"))              
        || (shExpMatch(host, "nexus.officeapps.live.com"))
        || (shExpMatch(host, "nexusrules.officeapps.live.com"))
        || (shExpMatch(host, "nps.onyx.azure.net"))
        || (shExpMatch(host, "ocsa.officeapps.live.com"))
        || (shExpMatch(host, "ocsp.digicert.com"))
        || (shExpMatch(host, "ocspx.digicert.com"))
        || (shExpMatch(host, "ocsp.globalsign.com"))
        || (shExpMatch(host, "ocsp.int-x3.letsencrypt.org"))
        || (shExpMatch(host, "ocsp.msocsp.com"))       
        || (shExpMatch(host, "ocsp2.globalsign.com"))
        || (shExpMatch(host, "ocsredir.officeapps.live.com"))
        || (shExpMatch(host, "ocws.officeapps.live.com"))
        || (shExpMatch(host, "odc.officeapps.live.com"))  
        || (shExpMatch(host, "officecdn.microsoft.com.edgekey.net"))            
        || (shExpMatch(host, "officecdn.microsoft.com.edgesuite.net"))              
        || (shExpMatch(host, "ols.officeapps.live.com"))  
        || (shExpMatch(host, "oneclient.sfx.ms"))
        || (shExpMatch(host, "outlook.uservoice.com"))
        || (shExpMatch(host, "platform.linkedin.com"))
        || (shExpMatch(host, "policykeyservice.dc.ad.msft.net"))
        || (shExpMatch(host, "prod.firstpartyapps.oaspapps.com.akadns.net")) 
        || (shExpMatch(host, "r1.res.office365.com"))
        || (shExpMatch(host, "r3.res.office365.com"))
        || (shExpMatch(host, "r4.res.office365.com"))
        || (shExpMatch(host, "s.ytimg.com"))
        || (shExpMatch(host, "scus-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "scus-odc.officeapps.live.com"))         
        || (shExpMatch(host, "scus-roaming.officeapps.live.com"))                 
        || (shExpMatch(host, "sea-odc.officeapps.live.com"))         
        || (shExpMatch(host, "sea-roaming.officeapps.live.com"))              
        || (shExpMatch(host, "secure.globalsign.com"))
        || (shExpMatch(host, "site-cdn.onenote.net"))
        || (shExpMatch(host, "skydrive.wns.windows.com"))
        || (shExpMatch(host, "skypemaprdsitus.trafficmanager.net"))   
        || (shExpMatch(host, "spoprod-a.akamaihd.net"))  
        || (shExpMatch(host, "ssw.live.com"))
        || (shExpMatch(host, "staffhub.ms"))
        || (shExpMatch(host, "staffhub.uservoice.com"))
        || (shExpMatch(host, "storage.live.com"))
        || (shExpMatch(host, "sway.com")) 
        || (shExpMatch(host, "teams.microsoft.com"))              
        || (shExpMatch(host, "telemetry.remoteapp.windowsazure.com"))         
        || (shExpMatch(host, "telemetryservice.firstpartyapps.oaspapps.com"))    
        || (shExpMatch(host, "web.microsoftstream.com"))         
        || (shExpMatch(host, "weu-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "weu-odc.officeapps.live.com"))         
        || (shExpMatch(host, "weu-roaming.officeapps.live.com"))
        || (shExpMatch(host, "wu.client.hip.live.com"))
        || (shExpMatch(host, "wus-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "wus-firstpartyapps.oaspapps.com"))  
        || (shExpMatch(host, "wus-odc.officeapps.live.com"))         
        || (shExpMatch(host, "wus-roaming.officeapps.live.com"))
        || (shExpMatch(host, "wus-www.sway-cdn.com"))
        || (shExpMatch(host, "wus-www.sway-extensions.com"))   
        || (shExpMatch(host, "www.digicert.com"))
        || (shExpMatch(host, "www.google-analytics.com"))
        || (shExpMatch(host, "www.onedrive.com"))
        || (shExpMatch(host, "www.remoteapp.windowsazure.com"))
        || (shExpMatch(host, "www.youtube.com"))
        || (shExpMatch(host, "xsi.outlook.com")))

    {
        return proxyserver;
    }
    //Catchall for all other traffic to another proxy 
else return proxyserver;
}

```

### <a name="2---pac-file-connect-to-office-365-over-the-internet-and-expressroute"></a>#2 - файл PAC: подключение к Office 365 через Интернет и ExpressRoute
<a name="bkmk_inet-aer"> </a>

Во втором примере — это Демонстрация наших рекомендуемый подход для управления подключениями, когда ExpressRoute и Интернет цепи доступны. Отправляет ExpressRoute объявление места назначения цепи ExpressRoute и Интернет только объявленных назначения для прокси-сервера.
  
Фрагмент кода:

```javascript
// JavaScript source code
//July 2018 Update
// Consolidated FQDNs of URLS which are reachable via Microsoft peering over ExpressRoute. All other traffic sent to a proxy in this example. 
//Every Effort is made to ensure 100% accuracy but this PAC should be used as an example and cross-checked with your traffic flow needs and the Office 365 URL &amp; IP page. 
//Intended only for Worldwide Office 365 instances, which the vast majority of customers will be using
//PAC presumes all Office 365 BGP communities/route filters are allowed.
function FindProxyForURL(url, host)
{
    // Define proxy server
    var proxyserver = "PROXY 10.10.10.10:8080";
    // Make host lowercase
    var lhost = host.toLowerCase();
    host = lhost;
    //SUB-FQDNs of ExpressRoutable wildcards which need to be explicitly sent to the proxy at the top of the PAC because they arent ER routable
    if ((shExpMatch(host, "xsi.outlook.com"))
        || (shExpMatch(host, "r3.res.outlook.com"))
        || (shExpMatch(host, "quicktips.skypeforbusiness.com"))
        || (shExpMatch(host, "*.um.outlook.com")))                  
    {
        return proxyserver;
    }
        //EXPRESS ROUTE DIRECT
    else if ((isPlainHostName(host))  
            || (shExpMatch(host, "*.aria.microsoft.com"))             
            || (shExpMatch(host, "*.dc.trouter.io"))
            || (shExpMatch(host, "*.lync.com"))
            || (shExpMatch(host, "*.manage.office.com"))
            || (shExpMatch(host, "*.outlook.com"))
            || (shExpMatch(host, "*.outlook.office.com"))
            || (shExpMatch(host, "*.portal.cloudappsecurity.com"))
            || (shExpMatch(host, "*.protection.office.com"))
            || (shExpMatch(host, "*.protection.outlook.com"))
            || (shExpMatch(host, "*.sharepoint.com")) 
            || (shExpMatch(host, "*.skype.com")) 
            || (shExpMatch(host, "*.skypeforbusiness.com")) 
            || (shExpMatch(host, "*.svc.ms"))   
            || (shExpMatch(host, "*.teams.microsoft.com"))  
            || (shExpMatch(host, "*broadcast.officeapps.live.com"))
            || (shExpMatch(host, "*excel.officeapps.live.com"))
            || (shExpMatch(host, "*onenote.officeapps.live.com"))
            || (shExpMatch(host, "*powerpoint.officeapps.live.com"))
            || (shExpMatch(host, "*view.officeapps.live.com"))                                 
            || (shExpMatch(host, "*visio.officeapps.live.com"))
            || (shExpMatch(host, "*word-edit.officeapps.live.com"))
            || (shExpMatch(host, "*word-view.officeapps.live.com"))
            || (shExpMatch(host, "account.office.net"))
            || (shExpMatch(host, "adminwebservice.microsoftonline.com"))
            || (shExpMatch(host, "agent.office.net"))  
            || (shExpMatch(host, "apc.delve.office.com"))
            || (shExpMatch(host, "api.login.microsoftonline.com"))
            || (shExpMatch(host, "api.passwordreset.microsoftonline.com"))
            || (shExpMatch(host, "aus.delve.office.com"))
            || (shExpMatch(host, "autologon.microsoftazuread-sso.com")) 
            || (shExpMatch(host, "becws.microsoftonline.com"))
            || (shExpMatch(host, "browser.pipe.aria.microsoft.com"))  
            || (shExpMatch(host, "can.delve.office.com")) 
            || (shExpMatch(host, "ccs.login.microsoftonline.com"))  
            || (shExpMatch(host, "ccs-sdf.login.microsoftonline.com"))
            || (shExpMatch(host, "clientconfig.microsoftonline-p.net"))
            || (shExpMatch(host, "companymanager.microsoftonline.com"))
            || (shExpMatch(host, "delve.office.com"))
            || (shExpMatch(host, "device.login.microsoftonline.com"))
            || (shExpMatch(host, "domains.live.com")) 
            || (shExpMatch(host, "eur.delve.office.com"))
            || (shExpMatch(host, "gbr.delve.office.com"))
            || (shExpMatch(host, "hip.microsoftonline-p.net"))
            || (shExpMatch(host, "hipservice.microsoftonline.com"))
            || (shExpMatch(host, "home.office.com"))
            || (shExpMatch(host, "ind.delve.office.com"))
            || (shExpMatch(host, "jpn.delve.office.com"))
            || (shExpMatch(host, "kor.delve.office.com"))
            || (shExpMatch(host, "lam.delve.office.com"))
            || (shExpMatch(host, "login.microsoft.com"))
            || (shExpMatch(host, "login.microsoftonline.com"))
            || (shExpMatch(host, "login.microsoftonline-p.net"))
            || (shExpMatch(host, "login.windows.net"))
            || (shExpMatch(host, "logincert.microsoftonline.com"))
            || (shExpMatch(host, "loginex.microsoftonline.com"))
            || (shExpMatch(host, "login-us.microsoftonline.com"))
            || (shExpMatch(host, "manage.office.com"))
            || (shExpMatch(host, "mobile.pipe.aria.microsoft.com"))
            || (shExpMatch(host, "nam.delve.office.com"))
            || (shExpMatch(host, "nexus.microsoftonline-p.net"))
            || (shExpMatch(host, "office.live.com")) 
            || (shExpMatch(host, "officeapps.live.com")) 
            || (shExpMatch(host, "outlook.office365.com")) 
            || (shExpMatch(host, "passwordreset.microsoftonline.com"))
            || (shExpMatch(host, "portal.office.com"))
            || (shExpMatch(host, "protection.office.com"))
            || (shExpMatch(host, "provisioningapi.microsoftonline.com"))
            || (shExpMatch(host, "scsinstrument-ss-us.trafficmanager.net")) 
            || (shExpMatch(host, "scsquery-ss-asia.trafficmanager.net"))
            || (shExpMatch(host, "scsquery-ss-eu.trafficmanager.net")) 
            || (shExpMatch(host, "scsquery-ss-us.trafficmanager.net"))  
            || (shExpMatch(host, "signup.microsoft.com"))
            || (shExpMatch(host, "smtp.office365.com"))  
            || (shExpMatch(host, "stamp2.login.microsoftonline.com"))
            || (shExpMatch(host, "suite.office.net")) 
            || (shExpMatch(host, "teams.microsoft.com")) 
            || (shExpMatch(host, "webshell.suite.office.com")) 
            || (shExpMatch(host, "www.office.com")))             
       
    {
        return "DIRECT";
    }
        //Catchall for all other traffic to proxy
    else
    {
        return proxyserver;
    }
}

```

### <a name="3---pac-file-manage-all-office-365-destinations-collectively"></a>#3 - файл PAC: управление Собирательно все назначения Office 365
<a name="bkmk_inet-direct"> </a>

Третий пример демонстрирует отправку всех сетевых запросов, связанные с Office 365 в одну целевую. Это обычно используется для обхода все проверки запросов сети Office 365 и предоставляет вам формат, где все опубликованные конечных точек входящих в список в формате PAC для вашего развертывания.
  
Фрагмент кода:

```javascript
// JavaScript source code
//July 2018 Update new URLS go live 1st August 2018 -
//Consolidated FQDNs required to access Office 365 - All services including optional components covered and elements covered under wildcards removed. 
//Some repeated domains have been consoliodated into unpublished wildcards in order to keep the file as small as possible.
//Includes Core ProPlus URLs but not Office Mobile/IPAD/IOS/ANDROID fqdns from https://support.office.com/en-gb/article/Network-requests-in-Office-365-ProPlus-eb73fcd1-ca88-4d02-a74b-2dd3a9f3364d
//Every Effort is made to ensure 100% accuracy but this PAC should be used as an example and cross-checked with your needs and the Office 365 URL &amp; IP page
//Intended only for Worldwide Office 365 instances, which the vast majority of customers will be using
function FindProxyForURL(url, host)
{
    // Define proxy server
    var proxyserver = "PROXY 10.10.10.10:8080";
    // Make host lowercase
    var lhost = host.toLowerCase();
    host = lhost;
   if  ((shExpMatch(host, "*.aadrm.com"))
        || (shExpMatch(host, "*.adhybridhealth.azure.com"))
        || (shExpMatch(host, "*.adl.windows.com"))
        || (shExpMatch(host, "*.api.microsoftstream.com"))  
        || (shExpMatch(host, "*.assets-yammer.com"))
        || (shExpMatch(host, "autologon.microsoftazuread-sso.com"))  
        || (shExpMatch(host, "*.azureedge.net"))   
        || (shExpMatch(host, "*.azurerms.com"))
        || (shExpMatch(host, "*.cloudapp.net")) 
        || (shExpMatch(host, "*.dc.trouter.io"))
        || (shExpMatch(host, "*.entrust.net")) 
        || (shExpMatch(host, "*.geotrust.com"))
        || (shExpMatch(host, "*.helpshift.com"))
        || (shExpMatch(host, "*.hockeyapp.net"))       
        || (shExpMatch(host, "*.localytics.com"))
        || (shExpMatch(host, "*.log.optimizely.com"))     
        || (shExpMatch(host, "*.lync.com"))
        || (shExpMatch(host, "*.microsoft.com"))
        || (shExpMatch(host, "*.microsoftonline.com"))
        || (shExpMatch(host, "*.microsoftonline-p.com"))
        || (shExpMatch(host, "*.microsoftonline-p.net"))
        || (shExpMatch(host, "*.msecnd.net"))
        || (shExpMatch(host, "*.msedge.net"))
        || (shExpMatch(host, "*.msocdn.com"))
        || (shExpMatch(host, "*.mstea.ms"))
        || (shExpMatch(host, "*.o365weve.com"))
        || (shExpMatch(host, "*.office.com"))
        || (shExpMatch(host, "*.office.net"))
        || (shExpMatch(host, "*.office365.com"))
        || (shExpMatch(host, "*.omniroot.com"))
        || (shExpMatch(host, "*.onenote.com"))
        || (shExpMatch(host, "*.onmicrosoft.com"))
        || (shExpMatch(host, "*.outlook.com"))
        || (shExpMatch(host, "*.phonefactor.net")) 
        || (shExpMatch(host, "*.portal.cloudappsecurity.com"))
        || (shExpMatch(host, "*.public-trust.com"))
        || (shExpMatch(host, "*.search.production.apac.trafficmanager.net"))
        || (shExpMatch(host, "*.search.production.emea.trafficmanager.net"))
        || (shExpMatch(host, "*.search.production.us.trafficmanager.net"))
        || (shExpMatch(host, "*.secure.skypeassets.com"))
        || (shExpMatch(host, "*.sfbassets.com"))  
        || (shExpMatch(host, "*.sharepoint.com"))
        || (shExpMatch(host, "*.sharepointonline.com"))
        || (shExpMatch(host, "*.skype.com"))
        || (shExpMatch(host, "*.skypeforbusiness.com"))
        || (shExpMatch(host, "*.svc.ms")) 
        || (shExpMatch(host, "*.sway.com"))
        || (shExpMatch(host, "*.symcb.com"))
        || (shExpMatch(host, "*.symcd.com"))
        || (shExpMatch(host, "*.tenor.com"))
        || (shExpMatch(host, "*.users.storage.live.com"))
        || (shExpMatch(host, "*.verisign.com"))
        || (shExpMatch(host, "*.verisign.net"))
        || (shExpMatch(host, "*.windows.net"))
        || (shExpMatch(host, "*.yammer.com"))
        || (shExpMatch(host, "*.yammerusercontent.com"))         
        || (shExpMatch(host, "*broadcast.officeapps.live.com"))
        || (shExpMatch(host, "*cdn.onenote.net"))
        || (shExpMatch(host, "*excel.officeapps.live.com"))
        || (shExpMatch(host, "*onenote.officeapps.live.com"))
        || (shExpMatch(host, "*powerpoint.officeapps.live.com"))
        || (shExpMatch(host, "*view.officeapps.live.com"))
        || (shExpMatch(host, "*visio.officeapps.live.com"))
        || (shExpMatch(host, "*word-edit.officeapps.live.com"))
        || (shExpMatch(host, "*word-view.officeapps.live.com"))    
        || (shExpMatch(host, "account.activedirectory.windowsazure.com"))
        || (shExpMatch(host, "ad.atdmt.com"))
        || (shExpMatch(host, "admin.onedrive.com"))
        || (shExpMatch(host, "ajax.aspnetcdn.com"))
        || (shExpMatch(host, "aka.ms"))
        || (shExpMatch(host, "amp.azure.net"))
        || (shExpMatch(host, "api.microsoftstream.com"))
        || (shExpMatch(host, "apis.live.net"))
        || (shExpMatch(host, "apps.identrust.com")) 
        || (shExpMatch(host, "assets.onestore.ms"))
        || (shExpMatch(host, "auth.gfx.ms"))
        || (shExpMatch(host, "cacerts.digicert.com"))    
        || (shExpMatch(host, "cdn.odc.officeapps.live.com"))  
        || (shExpMatch(host, "cdn.onenote.net"))
        || (shExpMatch(host, "cdn.optimizely.com"))
        || (shExpMatch(host, "cert.int-x3.letsencrypt.org"))
        || (shExpMatch(host, "client.hip.live.com"))     
        || (shExpMatch(host, "connect.facebook.net"))
        || (shExpMatch(host, "crl.globalsign.com"))
        || (shExpMatch(host, "crl.globalsign.net"))
        || (shExpMatch(host, "crl.identrust.com"))    
        || (shExpMatch(host, "crl3.digicert.com"))  
        || (shExpMatch(host, "crl4.digicert.com"))
        || (shExpMatch(host, "cus-odc.officeapps.live.com"))              
        || (shExpMatch(host, "cus-roaming.officeapps.live.com"))      
        || (shExpMatch(host, "dc.services.visualstudio.com"))
        || (shExpMatch(host, "domains.live.com"))
        || (shExpMatch(host, "ea-000.ocws.officeapps.live.com")) 
        || (shExpMatch(host, "ea-roaming.officeapps.live.com"))           
        || (shExpMatch(host, "ecn.dev.virtualearth.net"))
        || (shExpMatch(host, "eus2-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "eus2-roaming.officeapps.live.com"))              
        || (shExpMatch(host, "eus-odc.officeapps.live.com"))              
        || (shExpMatch(host, "eus-www.sway-cdn.com"))
        || (shExpMatch(host, "eus-www.sway-extensions.com"))
        || (shExpMatch(host, "firstpartyapps.oaspapps.com"))
        || (shExpMatch(host, "g.live.com"))
        || (shExpMatch(host, "groupsapi2-prod.outlookgroups.ms"))  
        || (shExpMatch(host, "groupsapi3-prod.outlookgroups.ms"))  
        || (shExpMatch(host, "groupsapi4-prod.outlookgroups.ms"))  
        || (shExpMatch(host, "groupsapi-prod.outlookgroups.ms"))  
        || (shExpMatch(host, "isrg.trustid.ocsp.identrust.com"))
        || (shExpMatch(host, "liverdcxstorage.blob.core.windowsazure.com"))
        || (shExpMatch(host, "management.azure.com"))
        || (shExpMatch(host, "mem.gfx.ms"))
        || (shExpMatch(host, "mrodevicemgr.officeapps.live.com"))               
        || (shExpMatch(host, "ncus-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "ncus-roaming.officeapps.live.com"))                 
        || (shExpMatch(host, "neu-000.ocws.officeapps.live.com")) 
        || (shExpMatch(host, "neu-odc.officeapps.live.com"))              
        || (shExpMatch(host, "neu-roaming.officeapps.live.com"))              
        || (shExpMatch(host, "nexus.officeapps.live.com"))
        || (shExpMatch(host, "nexusrules.officeapps.live.com"))
        || (shExpMatch(host, "nps.onyx.azure.net"))   
        || (shExpMatch(host, "ocsa.officeapps.live.com"))
        || (shExpMatch(host, "ocsp.digicert.com"))
        || (shExpMatch(host, "ocsp.globalsign.com"))
        || (shExpMatch(host, "ocsp.int-x3.letsencrypt.org"))
        || (shExpMatch(host, "ocsp.msocsp.com"))     
        || (shExpMatch(host, "ocsp2.globalsign.com")) 
        || (shExpMatch(host, "ocspx.digicert.com"))
        || (shExpMatch(host, "ocsredir.officeapps.live.com"))
        || (shExpMatch(host, "ocws.officeapps.live.com"))
        || (shExpMatch(host, "odc.officeapps.live.com"))  
        || (shExpMatch(host, "office.live.com"))
        || (shExpMatch(host, "officeapps.live.com"))
        || (shExpMatch(host, "officecdn.microsoft.com.edgekey.net"))              
        || (shExpMatch(host, "officecdn.microsoft.com.edgesuite.net"))
        || (shExpMatch(host, "ols.officeapps.live.com"))  
        || (shExpMatch(host, "oneclient.sfx.ms"))
        || (shExpMatch(host, "outlook.uservoice.com"))
        || (shExpMatch(host, "platform.linkedin.com"))
        || (shExpMatch(host, "policykeyservice.dc.ad.msft.net"))
        || (shExpMatch(host, "prod.firstpartyapps.oaspapps.com.akadns.net"))
        || (shExpMatch(host, "s.ytimg.com"))
        || (shExpMatch(host, "s0.assets-yammer.com"))  
        || (shExpMatch(host, "scsinstrument-ss-us.trafficmanager.net")) 
        || (shExpMatch(host, "scsquery-ss-asia.trafficmanager.net"))
        || (shExpMatch(host, "scsquery-ss-eu.trafficmanager.net")) 
        || (shExpMatch(host, "scsquery-ss-us.trafficmanager.net")) 
        || (shExpMatch(host, "scus-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "scus-odc.officeapps.live.com"))         
        || (shExpMatch(host, "scus-roaming.officeapps.live.com"))                 
        || (shExpMatch(host, "sea-odc.officeapps.live.com"))              
        || (shExpMatch(host, "sea-roaming.officeapps.live.com"))              
        || (shExpMatch(host, "secure.globalsign.com"))
        || (shExpMatch(host, "site-cdn.onenote.net"))
        || (shExpMatch(host, "skydrive.wns.windows.com"))
        || (shExpMatch(host, "skypemaprdsitus.trafficmanager.net"))
        || (shExpMatch(host, "spoprod-a.akamaihd.net"))
        || (shExpMatch(host, "ssw.live.com"))
        || (shExpMatch(host, "staffhub.ms"))
        || (shExpMatch(host, "staffhub.uservoice.com"))    
        || (shExpMatch(host, "storage.live.com"))
        || (shExpMatch(host, "telemetry.remoteapp.windowsazure.com"))
        || (shExpMatch(host, "telemetryservice.firstpartyapps.oaspapps.com"))
        || (shExpMatch(host, "web.microsoftstream.com"))   
        || (shExpMatch(host, "weu-000.ocws.officeapps.live.com")) 
        || (shExpMatch(host, "weu-odc.officeapps.live.com"))              
        || (shExpMatch(host, "weu-roaming.officeapps.live.com"))              
        || (shExpMatch(host, "wu.client.hip.live.com"))
        || (shExpMatch(host, "wus-000.ocws.officeapps.live.com"))  
        || (shExpMatch(host, "wus-firstpartyapps.oaspapps.com"))  
        || (shExpMatch(host, "wus-odc.officeapps.live.com"))              
        || (shExpMatch(host, "wus-roaming.officeapps.live.com"))              
        || (shExpMatch(host, "wus-www.sway-cdn.com"))
        || (shExpMatch(host, "wus-www.sway-extensions.com"))        
        || (shExpMatch(host, "www.digicert.com"))
        || (shExpMatch(host, "www.google-analytics.com"))
        || (shExpMatch(host, "www.onedrive.com"))
        || (shExpMatch(host, "www.remoteapp.windowsazure.com"))
        || (shExpMatch(host, "www.youtube.com")))
    {
        return proxyserver;
    }
        //Catchall for all other traffic to another proxy
    else return "PROXY 10.10.10.11:8080";
}

```

### <a name="use-custom-scripts-or-manually-create-your-own-pac-files"></a>Использовать пользовательские сценарии или вручную создать PAC файлов
<a name="pacfiles_manual"> </a>

Вот некоторые дополнительные средства сообщества, если вы создали что-то необходимости совместно использовать оставлять Примечание в комментариях. Ни одна из сообщества, инструменты, описанные в этой статье приведены официально поддерживается или поддерживается корпорацией Майкрософт и содержащиеся в этой статье для вашего удобства.
  
- Это средство наиболее старых сообщества созданный для управления процессом, средства, создавать, должна быть членом сообщества Office 365. Здесь приводится ссылка на [загрузку](https://gallery.technet.microsoft.com/Office-365-Proxy-Pac-60fb28f7).
    
- Эксперимент с помощью правил брандмауэра экспортируемый: [API Microsoft Cloud IP-адресов](https://mscloudips.azurewebsites.net/).
    
- Из Praktyk ИТ: [Преобразование RSS-канал](https://gallery.technet.microsoft.com/Convert-the-RSS-channel-5efe18b7) и [преобразования XML](https://gallery.technet.microsoft.com/Convert-the-O365IPAddresses-9890d896).
    
- Из Питер Abele: [Загрузка](https://gallery.technet.microsoft.com/How-to-create-an-up-to-b1fc33f3).
    
- Использование анализа сети для определения, который сети запросами должен обойти инфраструктуры прокси-сервера. Наиболее распространенные полных доменных имен, используемый для обхода прокси-серверы клиента включают следующие из-за объема сетевого трафика отправленных и полученных из этих конечных точек.
    
  ```
  outlook.office365.com
  outlook.office.com
  <tenant-name>.sharepoint.com
  <tenant-name>-my.sharepoint.com
  <tenant-name>-<app>.sharepoint.com
  *.Lync.com
  ```

- Убедитесь, что все сетевые запросы передаются непосредственно в брандмауэре иметь соответствующую запись в брандмауэре разрешить список, чтобы разрешить запрос привлечения.

## <a name="perimeter-network-integration"></a>Интеграция сети периметра
<a name="BKMK_Perimeter"> </a>

Вы знаете корпорации Майкрософт территориально-распределенной сети — это один из наибольшее магистралей в мире?
  
Он имеет значение true, это большой сети это приводит к Office 365 и другие облачным службам работать независимо от того, где в условиях, которые. Сети состоит из высокой пропускной способностью, минимизировать задержки, способный ссылки после сбоя тысячи километров маршрут в конфиденциальном режиме собственные темный оптоволоконной и несколькими терабит подключений между узлами центров обработки данных и пограничного сервера, все, чтобы упростить использование облачным службам.
  
С помощью сети следующим образом, которое устройствах вашей организации, для подключения к сети, как можно скорее. С более чем 2500 авторами связи поставщика услуг Интернета глобально и 70 точек присутствия, начало из локальной сети для нас должны быть полностью. Он не может снизить потратить несколько минут, убедившись, что авторами отношения поставщика услуг Интернета — оптимальный, [Вот несколько примеров](https://blogs.technet.microsoft.com/onthewire/2017/03/22/__) из хороший и не так хорошо авторами наличии номера телефонов для сети. 
  
Можно вручную или автоматически настраивает устройства в сети для оптимальной обработки запросов сети приложения Office 365, в зависимости от используемого оборудования. Какие изменения конфигурации, необходимо сделать для оптимального обработки трафика сети Office 365 будут зависеть от среды. Office 365 сетевых запросов может использовать преимущества конфигурации сети, которые позволяют следующее:
  
- Приоритет над меньше важных сетевого трафика.
    
- Маршрутизация локального исходящего трафика во избежание ретрансляторы медленных глобальной сети ссылок, используя минимизировать задержки доступны в сети Microsoft при. [Здесь приводится подробное обсуждение](https://blogs.technet.microsoft.com/onthewire/2017/05/03/office-365-connectivity-guidance-part-2/) на основании сотрудничества с клиентами. 
    
- С использованием службы DNS рядом с локального исходящего трафика для обеспечения сетевой запрос увольняется из локального исходящего трафика поступает в ближайшее место авторами Microsoft.
    
- Исключения из проверки глубокой сетевых пакетов или других обработки в соответствии с требованиями задержку в масштабе связано со значительными затратами сетевых пакетов.
    
Современный сетевых устройств включают возможности, которые иначе, чем универсальный ненадежные Интернет-трафик управления запросами сети для доверенных приложений, такие как Office 365. С помощью новых альбомная глобальная сеть SD решения такие различие трафика и путь выбора также могут быть выполнены с сведения о изменение состояния сети, например моменту времени доступности, задержка или производительности различных путей подключения к между пользователем и в облаке.
  
Иллюстрация [сети и планирования для Office 365 миграции](network-and-migration-planning.md), [производительность, устранение неполадок план для Office 365](performance-troubleshooting-plan.md)и [Контрольный список планирования развертывания для Office 365](deployment-planning-checklist.md) для Дополнительные рекомендации по планированию реализации конфигурации сети. 
  
### <a name="to-implement-this-scenario"></a>Для реализации этого сценария:

Обратитесь к поставщику сети решения или службы, если они могут использовать URL-адреса Office 365 и определения IP-адресов из XML для облегчения локального (к пользователю), low дополнительную нагрузку сети выходной для трафика Office 365, управлять его приоритета относительно других приложений и настройка сетевой путь для подключения к Office 365 в сети Microsoft в зависимости от того, изменения в сети. Некоторые решения автоматизации определения URL-адреса Office 365 и XMLs IP-адресов в их стеки и загрузки.
  
Всегда убедитесь, что реализованное решение имеет необходимые степень устойчивости, соответствующие географического дублирования сетевой путь для трафика Office 365 и обеспечивает изменения в Office 365 URL-адреса и IP-адреса, становятся публикации.

## <a name="faq"></a>Вопросы и ответы

Администратор часто задаваемые вопросы о подключения:
  
### <a name="how-do-i-submit-a-question"></a>Как отправить вопрос?

Щелкните ссылку внизу для указания, если статья была полезной или нет и отправьте его любые дополнительные вопросы. Мы отслеживать свои отзывы и предложения и обновление с наиболее часто задаваемые вопросы по.
  
### <a name="when-is-the-xml-file-updated"></a>При обновлении XML-файла

При объявили об изменении новые конечные точки, имеется обычно буфера 30 + день перед их эффективны и сетевые запросы почта направляется им. Этот буфер является для обеспечения клиентов и партнеров предоставлена возможность обновлять свои системы. Полное доменное имя и IP-адрес префикс добавления и удаления обрабатываются в XML-файла в то же время, как оповещения, что означает, что новый полное доменное имя будет находиться в XML-файле 30 дней до использования. Поскольку мы прекращения отправки сетевых запросов конечных точек, которые мы удаляется до объявление о их удаления при удалении конечной точки из XML в то же время, как объявление его уже не используется.
  
### <a name="how-can-i-be-notified-of-changes"></a>Как можно ли получать уведомления об изменениях?
<a name="bkmk_changes"> </a>

Конечные точки Office 365 публикуются в конце каждого месяца с уведомление о 30 дней. Иногда изменений внесено не будет более чем один раз в месяц или с более короткий срок, уведомление о периодов. При добавлении конечную точку, дата, перечисленные в [RSS-канал](https://go.microsoft.com/fwlink/p/?linkid=236301) — это дата, после которого будут отправляться сетевых запросов к конечной точке. Если вы не знакомы с RSS-канал, вот как для [подписки с помощью Outlook](https://go.microsoft.com/fwlink/p/?LinkId=532416) , или вы может [иметь RSS-канал, обновления, отправлять вам по электронной почте](https://go.microsoft.com/fwlink/p/?LinkId=532417).
  
### <a name="how-do-i-read-the-rss-change-log"></a>Как читать, RSS-канал журнала изменений?
<a name="bkmk_changes"> </a>

После подписаться на RSS-канал, который может выполнять синтаксический анализ сведения самостоятельно или с использованием скрипта. В следующей таблице описываются формат RSS-канал o облегчают.
  
|**Раздел**|**Часть 1**|**Часть 2**|**Часть 3**|**Часть 4**|**Часть 5**|**Часть 6**|
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
|**Описание** <br/> |Количество  <br/> |Дата, после которого может предполагать сети запросы на отправку в конечную точку.  <br/> |Базовая описание компонента или служба, которая требует конечной точки.  <br/> |Можно ли подключиться к этой конечной точки на канал ExpressRoute в дополнение к Интернету?  <br/> |**Да** — возможность подключения к этой конечной точки в Интернете и ExpressRoute.  <br/> **Нет** — только можно подключить к этой конечной точки в Интернете.  <br/> |Полное доменное имя или IP-адреса диапазона, добавления или удаления назначения.  <br/> |
|**Пример** <br/> |1 /  <br/> |[Эффективных xx/xx/xxx.  <br/> |Обязательный: \<описание\>.  <br/> |ExpressRoute:  <br/> |\<Да/Нет\>.  <br/> |\<Полное доменное имя или IP-адрес\>],  <br/> |

Несколько других замечания, любая операция имеет набору разделителей:
  
- **/**-После count
- **[** - для указания запись для подсчета
- **.** -используется между каждой несовпадающих раздел записи
- **],** -, чтобы указать окончание одной операции
- **].** -Чтобы указать окончание всех записей

### <a name="how-do-i-determine-the-location-of-my-tenant"></a>Как определить расположение личных клиента?

 **Расположение клиента** лучше всего определяется с помощью нашего [сопоставление центра обработки данных](https://o365datacentermap.azurewebsites.net/).
  
### <a name="am-i-peering-appropriately-with-microsoft"></a>У меня авторами надлежащим образом с корпорацией Майкрософт?

 **Расположения Peering** описаны более подробно в [авторами с корпорацией Майкрософт](https://www.microsoft.com/peering).
  
С более чем 2500 авторами связи поставщика услуг Интернета глобально и 70 точек присутствия, начало из локальной сети для нас должны быть полностью. Он не может снизить потратить несколько минут, убедившись, что авторами отношения поставщика услуг Интернета — оптимальный, [Вот несколько примеров](https://blogs.technet.microsoft.com/onthewire/2017/03/22/__) из хороший и не так хорошо авторами наличии номера телефонов для сети. 
  
### <a name="how-do-i-determine-which-ip-addresses-to-accept-over-expressroute"></a>Как определить, какую IP-адресов, чтобы принять через ExpressRoute?

 **Маршруты принятия ExpressRoute** определяются конкретных Office 365 [протокола BGP сообществ](https://support.office.com/article/Using-BGP-communities-in-ExpressRoute-for-Office-365-scenarios-preview-9ac4d7d4-d9f8-40a8-8c78-2a6d7fe96099)и [диапазоны IP-адресов корпорации Майкрософт](https://www.microsoft.com/download/details.aspx?id=53602) .
  
### <a name="how-do-i-determine-which-endpoints-i-need"></a>Как определить, какие конечные точки, требуются?

Мы регулярно добавить новые функции и службы в набор Office 365 расширятся, создавая подключения к альбомная. Если вы подписаны на E3 или E5 SKU, простой способ подумайте, список конечных точек — требуются все из них для получения полной функциональности для набора. Если вы не подписаны на любой из этих продуктов разницы минимальной в зависимости от конечных точек.
  
Чтение [Сетевого подключения к Office 365 принципы](office-365-network-connectivity-principles.md) Чтобы получить дополнительные сведения о категории конечной точки Office 365 и понять принципы подключения для безопасного управления Office 365 трафика и начало обеспечить максимально высокую производительность. 
  
На следующем рисунке видно пример из части таблицы полное доменное имя в разделе Office в Интернете. Строки упорядочены по компонентам и различия в службе подключения к. Первые две строки указывают Office Online полагается на конечных точек помеченные требуется в Office 365 проверки подлинности и удостоверения и портала и общих разделов. Это характерно для службы в Office 365 полагаться на следующих общих служб. Третьей строки указывает на клиентских компьютерах должны быть смогут получать \*. officeapps.live.com для использования Office Online и четвертой строки указывает компьютеров также должны для связи с \*. cdn.office.net для использования Office Online.
  
Несмотря на то, что в строке три и четыре необходимы для использования Office Online, они разделены указывает, что назначения разных:
  
1. \*. officeapps.live.com не представляет CDN, запросы значение для этого пространства имен будет перейти непосредственно в центре обработки данных Майкрософт.
2. \*. officeapps.live.com доступен на ExpressRoute каналов, с помощью Microsoft Peering.
3. IP-адреса, связанные с Office Online и \*. officeapps.live.com можно найти, выполнив эту ссылку.
4. \*. cdn.office.net представляет CDN, размещенного в Akamai, запросы значение для этого пространства имен будут поступать на Akamai центра обработки данных.
5. \*. cdn.office.net недоступен на ExpressRoute каналов.
6. IP-адреса, связанные с Office Online и \*. cdn.office.net недоступны.

![Снимок экрана на странице конечных точек](media/42b487f3-24f3-48fe-9885-f97aae3194f3.png)
  
### <a name="i-see-network-requests-to-ip-addresses-not-on-the-published-list-do-i-need-to-provide-access-to-them"></a>Я вижу сетевых запросов для IP-адресов не на опубликованные списка, необходимо предоставить доступ к ним?
<a name="bkmk_MissingIP"> </a>

Корпорация Майкрософт предоставлять только IP-адресов для серверов Microsoft Office 365, которые следует направлять непосредственно в Интернете или ExpressRoute. Это не полный список всех IP-адресов, которые вы увидите сетевых запросов для. Вы увидите сетевые запросы корпорации Майкрософт и сторонних производителей собственные, отменить публикацию, IP-адресов. Эти IP-адреса динамически создаются или управляемых, чтобы не позволяет своевременно уведомление при изменении ими. Если брандмауэр не может разрешить доступ на основании полные доменные имена для сетевые запросы, используйте файл PAC или WPAD для управления запросами.
  
Отображаются IP-адрес, связанный с Office 365, который вы хотите больше узнать о?
  
1. Установите флажок, если IP-адрес включен в больший диапазон опубликованные с помощью [CIDR калькулятор](http://jodies.de/ipcalc).
2. В разделе Если партнер несет ответственность за IP-адресов с помощью [запросов whois](https://dnsquery.org/). Если он установлен Microsoft владельцем, возможно внутренних партнера.
3. Проверьте сертификат, в браузере подключиться к адрес IP-адресов с помощью *HTTPS://\<IP-адрес\> * , проверьте доменов, перечисленных в сертификате, чтобы понять, какие домены связаны с IP-адрес. Если будет Microsoft, владельцем которого IP-адрес, а не на список Office 365 IP-адресов, значит, вероятно, IP-адрес связан с CDN Майкрософт например *MSOCDN.NET* или другой домен Microsoft без публикуемые сведения IP-адресов. Если в домене в сертификате — это один где мы утверждению IP-адрес, сообщите нам.

### <a name="why-do-i-see-names-such-as-nsatcnet-or-akadnsnet-in-the-microsoft-domain-names"></a>Почему отображаются имена, например nsatc.net или akadns.net в доменных имен Microsoft?
<a name="bkmk_akamai"> </a>

Office 365 и другие службы Microsoft используют несколько служб сторонних производителей, например Akamai и MarkMonitor для улучшения работы в Office 365. Оставьте предоставляет оптимального возможности изменения этих служб в будущем. При этом, мы часто публикация записи CNAME, которая указывает третьей стороне собственные домена, записи или IP-адрес. Домены сторонних производителей могут размещаться контент, такой как CDN, или они могут размещаться службы, такие как служба управления географических трафика. При появлении подключений эти третьим лицам, они в виде перенаправления или ссылок, не начального запроса от клиента. Некоторые клиенты должны убедиться эту форму ссылок и перенаправление разрешено передавать без явного добавления используют длинный список возможных служб сторонних производителей полных доменных имен.
  
Список служб, может быть изменен в любое время. Ниже перечислены некоторые из служб, используемых в настоящее время:
  
[MarkMonitor](https://www.markmonitor.com/) используется при появлении запросов, которые включают * \*. nsatc.net* . Эта служба предоставляет защиты имя домена и мониторинга для защиты от вредоносного поведения.
  
[ExactTarget](https://www.marketingcloud.com/) используется при появлении запросов к * \*. exacttarget.com* . Эта служба предоставляет электронной почты ссылку Управление и мониторинг от вредоносного поведения.
  
При появлении запросы, включающие один из следующих полных доменных имен [Akamai](https://www.akamai.com/) не используется. Данная служба предлагает географически DNS и служб сети доставки содержимого.
  
```
*.akadns.net
*.akam.net
*.akamai.com
*.akamai.net
*.akamaiedge.net
*.akamaihd.net
*.akamaized.net
*.edgekey.net
*.edgesuite.net
```

### <a name="what-are-the-three-types-of-office-365-endpoints"></a>Какие существуют три типа конечных точках Office 365?
<a name="bkmk_akamai"> </a>

- Подключитесь к службам сторонних производителей для получения базовой служб Интернета, например DNS-запросы и получения содержимого CDN. Можно также подключиться к службам сторонних производителей для интеграции, такие как включение видеороликов YouTube записных книжек OneNote.
- Подключитесь к дополнительного служб, размещенных и запустите корпорацией Майкрософт, таких как узлы пограничного сервера, которые позволяют сети запрос на ввод корпорации Майкрософт глобальной сети на ближайших веб-сайта на своем компьютере. Как третьего наибольшего сети как это повышает эффективность подключения. Можно также подключиться к службам Microsoft Azure такими как службы Azure мультимедиа, которые используются по-разному служб Office 365.
- Подключитесь к основным службам Office 365 например сервере почтовых ящиков Exchange Online или Скайп для Business Online server, где находятся уникальное и конфиденциальные данные. Можно подключиться к основным службам Office 365 с полное доменное имя или IP-адрес и использовать internet или ExpressRoute цепей. Только можно подключить к сторонних производителей и дополнительных служб, с помощью полных доменных имен в Интернете цепи.

На следующей схеме показана различия между областями эти службы. На этой диаграмме локальной сети клиента в нижнем левом имеет несколько сетевых устройств для помощи в управлении подключение к сети. Конфигурации следующим образом являются общими для предприятий. Если вашей сети только брандмауэра между клиентскими компьютерами и Интернетом, а также поддерживаются, а вы наверняка хотели бы убедиться, что брандмауэр поддерживает полные доменные имена и подстановочные знаки в список правил allow.
  
Чтение [Сетевого подключения к Office 365 принципы](office-365-network-connectivity-principles.md) Чтобы получить дополнительные сведения о категории конечной точки Office 365 и понять принципы подключения для безопасного управления Office 365 трафика и начало обеспечить максимально высокую производительность. 
  
![Отображает три различных типа конечных точек сети при использовании Office 365](media/6582bcfa-11ba-4ac2-9b69-14bef0437670.png)
  
### <a name="i-cant-or-dont-want-to-use-any-third-party-service"></a>Не удается или не хотите использовать любой службы сторонних производителей
<a name="bkmk_thirdparty"> </a>

Office 365 — это набор служб, созданных в функции через Интернет, надежность и доступность использованием основаны на многих стандартных Интернет-служб, доступных. Например стандартный служб Интернета, например DNS, списки отзыва Сертификатов и CDN должен быть доступен, как они должны быть доступны для использования большинство современных Интернет-служб с помощью Office 365.
  
Помимо этих основных служб Интернета существуют службы сторонних производителей, которые используются только для интеграции функций. Например с помощью Giphy.com внутри групп Майкрософт позволяет пользователям легко включать рисунки в формате GIF внутри групп. Аналогично YouTube и Flickr являются служб сторонних производителей, которые используются для интегрируют видео и изображений в клиентах Office из Интернета. Хотя они необходимы для интеграции, они помечаются как необязательные в статье конечных точках Office 365, это значит, что основные функциональные возможности службы будет продолжать работать, если конечная точка не будет доступен.
  
Если выполняется попытка использовать Office 365 и уже знают, что третья сторона службы недоступны можно [Разрешить все полные доменные имена, помеченные обязательный или необязательный в этой статье через прокси-сервера и брандмауэра](urls-and-ip-address-ranges.md).
  
### <a name="i-cant-or-dont-want-to-use-any-secondary-services"></a>Не удается или не хотите использовать какие-либо дополнительных службы
<a name="bkmk_secondary"> </a>

Дополнительный службы, службы Майкрософт, которые не попадают в элемент управления Office 365. Это пограничной сети, носитель служб Azure и сети доставки содержимого Azure. Они необходимы для использования Office 365 и должен быть доступен.
  
Если выполняется попытка использовать Office 365 и уже знают, что третья сторона службы недоступны можно [Разрешить все полные доменные имена, помеченные обязательный или необязательный в этой статье через прокси-сервера и брандмауэра](urls-and-ip-address-ranges.md).
  
### <a name="how-do-i-block-access-to-microsofts-consumer-services"></a>Как запретить доступ к службам потребителей корпорации Майкрософт
<a name="bkmk_consumer"> </a>

Ограничение доступа к наших услуг потребитель должно выполняться на собственный риск, только надежный способ блокировки потребитель службы для ограничения доступа к *login.live.com* полное доменное имя. В этом поле полное доменное имя используется широкий набор служб, включая не потребитель службы, такие как MSDN, TechNet и другими пользователями. Ограничение доступа к этой полное доменное имя может привести к необходимости также включать исключения для сетевых запросов, связанные с этими службами.
  
Имейте в виду, что блокирующая доступ к службам потребитель Microsoft сам по себе он не предотвратить возможность другого пользователя в сети на exfiltrate сведения, с помощью клиента Office 365 или другие службы.
  
## <a name="related-topics"></a>Статьи по теме

[Office 365 IP-адрес и URL-адрес веб-службы](office-365-ip-web-service.md)

[Диапазоны IP-адресов центра обработки данных Microsoft Azure](https://www.microsoft.com/download/details.aspx?id=41653)
  
[Пространство публичных IP-адресов корпорации Майкрософт](https://www.microsoft.com/download/details.aspx?id=53602)
  
[Требования к инфраструктуре сети для Microsoft Intune](https://docs.microsoft.com/intune/get-started/network-infrastructure-requirements-for-microsoft-intune)
  
[Power BI и ExpressRoute](https://powerbi.microsoft.com/documentation/powerbi-admin-power-bi-expressroute/)
  
[URL-адреса и диапазоны IP-адресов для Office 365](urls-and-ip-address-ranges.md)
  
[Управление подключением ExpressRoute для Office 365](managing-expressroute-for-connectivity.md)
  
[Принципы сетевого подключения к Office 365](office-365-network-connectivity-principles.md)