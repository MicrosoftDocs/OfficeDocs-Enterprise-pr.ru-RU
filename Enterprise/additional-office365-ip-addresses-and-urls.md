---
title: Дополнительные IP-адреса и URL-адреса Office 365, не включенные в веб-службы
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 8/22/2018
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- MOM160
- BCS160
ms.assetid: ''
description: Сводка. В новых веб-службах конечных точек отсутствует небольшое количество конечных точек для определенных сценариев.
hideEdit: true
ms.openlocfilehash: b40fb1a40d2a815bfc6e02fa11204d10dde2af73
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "22600513"
---
# <a name="additional-office-365-ip-addresses-and-urls-not-included-in-the-web-services"></a>Дополнительные IP-адреса и URL-адреса Office 365, не включенные в веб-службы

Некоторые конечные точки сети были опубликованы ранее и не были включены в веб-службы. Область действия веб-служб — конечные точки сети, необходимые для подключения конечных пользователей Office 365 к корпоративной сети периметра. В настоящее время к ней не относится следующее:

1. Возможные сетевые подключения из центра обработки данных Майкрософт к сети клиента (входящий гибридный сетевой трафик сервера)
2. Сетевое подключение от серверов клиентской сети к корпоративному периметру (исходящий серверный сетевой трафик)
3. Редкие сценарии с требованиями к сетевому подключению от пользователя
4. Требование подключения для разрешения DNS (не представлено ниже)
5. Надежные сайты Internet Explorer или Microsoft Edge

Эти параметры (кроме DNS) являются необязательными для большинства клиентов, за исключением особого описанного сценария.

|||||
|:-----|:-----|:-----|:-----|
| **Строка** | **Цель** | **Назначение** | **Тип** |
| 1  | [Служба импорта](https://support.office.com/article/use-network-upload-to-import-your-organization-pst-files-to-office-365-103f940c-0468-4e1a-b527-cc8ad13a5ea6) для приема PST- и других файлов | Дополнительные требования см. в статье [Служба импорта](https://support.office.com/article/use-network-upload-to-import-your-organization-pst-files-to-office-365-103f940c-0468-4e1a-b527-cc8ad13a5ea6). | Редкий сценарий исходящего трафика |
| 2  | [Помощник по поддержке и восстановлению для Microsoft Office 365](https://diagnostics.office.com/#/) — проверка учетных данных пользователя для единого входа. Источник:<br> ```o365diagnosticsbasic-eus.cloudapp.net (104.211.54.99)``` <br> ```o365diagnosticworker-eus.cloudapp.net (104.211.54.134)```  | Локальная служба маркеров безопасности | Входящий серверный трафик |
| 3  | Azure AD Connect (с возможностью единого входа) — WinRM и удаленная оболочка PowerShell | Клиентская среда службы маркеров безопасности (сервер AD FS и прокси-сервер AD FS) \| TCP-порты 80 и 443 | Входящий серверный трафик |
| 4  | Служба маркеров безопасности, например прокси-серверы AD FS (только для федеративных клиентов) | Служба маркеров безопасности клиента (например, прокси-сервер AD FS) \| TCP-порты 443 или 49443 с клиентским TLS | Входящий серверный трафик |
| 5  | [Интеграция единой службы обмена сообщениями Exchange Online с SBC](https://technet.microsoft.com/library/jj673565.aspx) | Двунаправленный обмен между локальным пограничным контроллером сеансов и *. um.outlook.com | Только исходящий серверный трафик |
| 6  | Функции сосуществования для[гибридного развертывания Exchange](https://docs.microsoft.com/exchange/exchange-deployment-assistant), например обмен сведениями о доступности. | Локальный сервер Exchange клиента | Входящий серверный трафик |
| 7  | Проверка подлинности прокси-сервера для [гибридного развертывания Exchange](https://docs.microsoft.com/exchange/exchange-deployment-assistant) | Локальная служба маркеров безопасности клиента | Входящий серверный трафик |
| 8  | Используется для настройки [гибридного развертывания Exchange](https://docs.microsoft.com/exchange/exchange-deployment-assistant) с помощью мастера гибридной конфигурации Exchange. <br> Примечание. Эти конечные точки необходимы только для настройки гибридного развертывания Exchange  | ```domains.live.com``` на TCP-портах 80 и 443. Требуется только для мастера гибридной конфигурации Exchange 2010 с пакетом обновления 3 (SP3). | Только исходящий серверный трафик |
| 9  | **Проверка подлинности и удостоверения полных доменных имен** <br> Для функционирования полное доменное имя ```secure.aadcdn.microsoftonline-p.com``` должно находиться в зоне надежных сайтов Internet Explorer (IE) или Microsoft Edge. |  | Надежные сайты |
| 10  |  **Полные доменные имена Microsoft Teams** <br> Если вы используете Internet Explorer или Microsoft Edge, вам нужно разрешить основные и сторонние файлы cookie, а также добавить полные доменные имена Teams в список надежных сайтов (в дополнение к полным доменным именам для всего набора, CDN и телеметрии, перечисленным выше). Дополнительные сведения см. в статье [Известные проблемы Microsoft Teams](https://docs.microsoft.com/microsoftteams/known-issues). |  | Надежные сайты |
| 11  |  **Полные доменные имена SharePoint Online и OneDrive для бизнеса** <br> Для функционирования все полные доменные имена ". sharepoint.com", имеющие в имени "\<клиент>", должны находиться в зоне надежных сайтов IE или Microsoft Edge вашего клиента. Эти конечные точки необходимо добавить в дополнение к полным доменным именам для всего набора, CDN и телеметрии, перечисленным выше. |  | Надежные сайты |
| 12  | **Yammer**  <br> Приложение Yammer доступно только в браузере и требует, чтобы авторизованный пользователь проходил через прокси-сервер. Для функционирования все полные доменные имена приложения Yammer должны находиться в зоне надежных сайтов IE или Microsoft Edge вашего клиента. |  | Надежные сайты |

## <a name="related-topics"></a>Статьи по теме

[Управление конечными точками Office 365](managing-office-365-endpoints.md)
  
[Устранение неполадок с подключением к Office 365](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d.aspx)
  
[Подключение клиентских компьютеров](https://support.office.com/article/client-connectivity-4232abcf-4ae5-43aa-bfa1-9a078a99c78b)
  
[Сети доставки содержимого](https://support.office.com/article/content-delivery-networks-0140f704-6614-49bb-aa6c-89b75dcd7f1f)
  
[Диапазоны IP-адресов центра обработки данных Microsoft Azure](https://www.microsoft.com/download/details.aspx?id=41653)
  
[Пространство публичных IP-адресов корпорации Майкрософт](https://www.microsoft.com/download/details.aspx?id=53602)

