---
title: Планирование для сетевых устройств, подключающихся к службам Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/29/2016
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 073433ca-3511-4db9-b173-7a2edca57691
description: 'Сводка: в этой статье описаны рекомендации по пропускной способности сети, ускорителям глобальной сети и устройствам балансировки нагрузки, которые используются для подключения к Office 365.'
ms.openlocfilehash: c384ba043e64ec83eda74b234937efaf72f29815
ms.sourcegitcommit: ad5bdc53ca67ee6a663c27648511c1ad768a76d4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/28/2018
ms.locfileid: "23223071"
---
# <a name="plan-for-network-devices-that-connect-to-office-365-services"></a>Планирование для сетевых устройств, подключающихся к службам Office 365

 **Сводка**: в этой статье описаны рекомендации по пропускной способности сети, ускорителям глобальной сети и устройствам балансировки нагрузки, которые используются для подключения к Office 365.
  
Некоторые сетевого оборудования могут иметь ограничения на количество одновременных сеансов, которые поддерживаются. Для организаций, более 2 000 пользователей мы рекомендуем, что они отслеживать их сетевых устройств, чтобы убедиться, что они способны дополнительный трафик службы Office 365. Сетевого протокола SNMP (Simple Management) отслеживании программного обеспечения, которые помогут сделать это.

||
|:-----|
| В этой статье является частью [сети планирование и настройка производительности для Office 365](https://aka.ms/tune).|

Локальный исходящий параметры прокси-сервера Интернета также влияет на возможность подключения к службам Office 365 для клиентских приложений. Необходимо также настроить сетевые устройства прокси-сервер для подключений для URL-адреса, Microsoft облачных служб и приложений. Отличается любой организации. Чтобы получить представление для как Microsoft управляют этот процесс и пропускной способности, мы временного [исследований](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365).
  
Следующие Скайп для статьи справки Business получить больше информации о Скайп для параметров бизнеса:
  
- [Устранение неполадок Скайп для бизнеса входа ошибки (для администраторов)](https://go.microsoft.com/fwlink/p/?LinkID=243624)

- [Не удается подключиться к Скайп для бизнеса или некоторые функции не работают, так как локальный брандмауэр блокирует подключение](https://go.microsoft.com/fwlink/p/?LinkID=243625)

> [!NOTE]
> Хотя многие из этих параметров Скайп для конкретного бизнеса, общие рекомендации по настройке сети можно использовать для всех служб Office 365.
  
## <a name="determining-network-capacity"></a>Определение пропускной способности сети

Каждое сетевое устройство, функционирующее при подключении к сети, имеет предельную пропускную способность. К таким устройствам относятся сетевые адаптеры сервера или клиента, маршрутизаторы, коммутаторы, а также концентраторы, которые служат для их соединения. Пропускная способность сети считается достаточной, если устройства сети не перегружаются. Отслеживание сетевой активности имеет большое значение в процессе контроля фактической нагрузки на все сетевые устройства, которая должна быть ниже максимального значения их пропускной способности. Пропускная способность сети влияет на производительность прокси-устройства.
  
В большинстве случаев пропускной способности подключения к Интернету задается ограничение объема трафика. Слабый производительности трафика пиковые часы, вероятно, вызваны чрезмерное использование ссылки на Internet. Это также относится к филиале, где branch office прокси-сервера сервера компьютеры подключены к устройства прокси-сервера в штаб-квартире филиала через медленное подключение Wide сети (WAN).
  
Для тестирования пропускная способность сети, отслеживать активность сети в интерфейсе прокси-сервера. Если это более 75% максимальная пропускная способность для любого сетевого интерфейса, следует увеличить пропускную способность сетевой инфраструктуры, который не отвечает требованиям. Также следует рассмотреть возможность использования дополнительных функций, таких как сжатия HTTP.
  
## <a name="wan-accelerators"></a>Ускорители глобальной сети

Если организация использует глобальной сети (WAN) ускорения прокси-устройства, могут возникнуть проблемы при получении доступа к службам Office 365. Может потребоваться оптимизации сетевого устройства или устройства, чтобы убедиться, что пользователи имеют согласованную работу при доступе к Office 365. Например службам Office 365 шифрования часть содержимого Office 365 и заголовке TCP. Устройства могут быть обрабатывать такого рода трафика.
  
Поддержка заявление о [с помощью глобальной сети контроллер оптимизации или трафика/проверка на наличие устройств с помощью Office 365](https://support.microsoft.com/kb/2690045).
  
## <a name="hardware-and-software-load-balancing-devices"></a>Аппаратные и программные устройства балансировки нагрузки

В организации потребуется использовать устройство балансировки нагрузки или балансировку сетевой нагрузки (HLB или NLB), чтобы распределять запросы серверам AD FS и/или гибридным серверам Exchange. Устройства балансировки нагрузки управляют сетевым трафиком для локальных серверов. Эти серверы имеют решающее значение для обеспечения доступности единого входа и гибридного развертывания Exchange.
  
Мы представляют собой решение балансировки сетевой Нагрузки на основе программного обеспечения, встроенной в Windows Server. Office 365 поддерживает это решение для балансировки нагрузки.
  
## <a name="firewalls-and-proxies"></a>Брандмауэров и прокси-серверов

Для получения дополнительных сведений о настройке брандмауэров и прокси-серверы для подключения к Office 365, [конечные точки управления Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a), [сетевое подключение к Office 365](network-connectivity.md)и [часто задаваемые вопросы о конечных точках Office 365](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d) для получения дополнительных сведений об устройствах и выделения канала.
  
## <a name="see-also"></a>См. также

[Помощники по развертыванию служб Office 365](deployment-advisors-for-office-365.md)