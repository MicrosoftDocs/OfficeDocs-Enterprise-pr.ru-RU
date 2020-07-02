---
title: Удаление данных Office 365 в Skype для бизнеса
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
f1.keywords:
- NOCSH
description: Пояснения об удалении данных в Skype для бизнеса.
ms.openlocfilehash: 7c94c5d1ddfb5a8056e139d664627dd1e7bed0de
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "44997799"
---
# <a name="skype-for-business-data-deletion-in-office-365"></a><span data-ttu-id="35dd5-103">Удаление данных в Skype для бизнеса в Office 365</span><span class="sxs-lookup"><span data-stu-id="35dd5-103">Skype for Business Data Deletion in Office 365</span></span>

<span data-ttu-id="35dd5-104">Skype for Business provides archiving of peer-to-peer instant messages, multiparty instant messages, and content upload activities in meetings.</span><span class="sxs-lookup"><span data-stu-id="35dd5-104">Skype for Business provides archiving of peer-to-peer instant messages, multiparty instant messages, and content upload activities in meetings.</span></span> <span data-ttu-id="35dd5-105">The archiving capability requires Exchange and is controlled by the user's Exchange mailbox In-Place Hold attribute, which archives both email and Skype for Business contents.</span><span class="sxs-lookup"><span data-stu-id="35dd5-105">The archiving capability requires Exchange and is controlled by the user's Exchange mailbox In-Place Hold attribute, which archives both email and Skype for Business contents.</span></span>

<span data-ttu-id="35dd5-106">All archiving in Skype for Business is considered "user-level archiving" because you enable or disable it for one or more specific users or groups of users by creating, configuring, and applying a user-level archiving policy for those users.</span><span class="sxs-lookup"><span data-stu-id="35dd5-106">All archiving in Skype for Business is considered "user-level archiving" because you enable or disable it for one or more specific users or groups of users by creating, configuring, and applying a user-level archiving policy for those users.</span></span> <span data-ttu-id="35dd5-107">There is no direct control of archiving settings from within the Skype for Business admin center.</span><span class="sxs-lookup"><span data-stu-id="35dd5-107">There is no direct control of archiving settings from within the Skype for Business admin center.</span></span>

<span data-ttu-id="35dd5-108">Следующие типы контента не архивируются в Skype для бизнеса:</span><span class="sxs-lookup"><span data-stu-id="35dd5-108">The following types of content are not archived in Skype for Business:</span></span>

- <span data-ttu-id="35dd5-109">одноранговые передачи файлов;</span><span class="sxs-lookup"><span data-stu-id="35dd5-109">Peer-to-peer file transfers</span></span>
- <span data-ttu-id="35dd5-110">аудио- и видеоданные для однорангового обмена мгновенными сообщениями и конференций;</span><span class="sxs-lookup"><span data-stu-id="35dd5-110">Audio/video for peer-to-peer instant messages and conferences</span></span>
- <span data-ttu-id="35dd5-111">данные совместного использования приложений для одноранговых мгновенных сообщений и конференций</span><span class="sxs-lookup"><span data-stu-id="35dd5-111">Application sharing for peer-to-peer instant messages and conferences</span></span>
- <span data-ttu-id="35dd5-112">Примечания конференц-связи</span><span class="sxs-lookup"><span data-stu-id="35dd5-112">Conferencing annotations</span></span> 

## <a name="meeting-content-retention"></a><span data-ttu-id="35dd5-113">Хранение содержимого собрания</span><span class="sxs-lookup"><span data-stu-id="35dd5-113">Meeting Content Retention</span></span>

<span data-ttu-id="35dd5-114">Клиенты, использующие Skype для бизнеса, могут отправлять контент на собрание Skype для бизнеса как вложения, такие как презентации PowerPoint, файлы OneNote и другие файлы.</span><span class="sxs-lookup"><span data-stu-id="35dd5-114">Customers using Skype for Business can upload content to a Skype for Business meeting as attachments, such as PowerPoint presentations, OneNote files, and other files.</span></span> <span data-ttu-id="35dd5-115">Срок хранения содержимого, отправленного для собрания:</span><span class="sxs-lookup"><span data-stu-id="35dd5-115">The retention period for content that has been uploaded to a meeting is as follows:</span></span>

- <span data-ttu-id="35dd5-116">**Однократная встреча** — контент сохраняется в течение 15 дней, начиная с последнего пользователя, когда он покидает собрание.</span><span class="sxs-lookup"><span data-stu-id="35dd5-116">**One-time meeting** - Content is retained for 15 days starting from when the last person leaves the meeting.</span></span>
- <span data-ttu-id="35dd5-117">**Повторяющееся собрание** — контент сохраняется в течение 15 дней после последнего сеанса собрания.</span><span class="sxs-lookup"><span data-stu-id="35dd5-117">**Recurring meeting** - Content is retained for 15 days after the last person leaves the last session of the meeting.</span></span> <span data-ttu-id="35dd5-118">Если в течение 15 дней к этому сеансу собрания присоединяется какой-либо человек, таймер срока хранения сбрасывается.</span><span class="sxs-lookup"><span data-stu-id="35dd5-118">The retention timer resets if someone joins the same meeting session within 15 days.</span></span> <span data-ttu-id="35dd5-119">Например, предположим, что собрание Skype для бизнеса запланировано еженедельно в течение одного года, а файл отправляется на собрание во время первого экземпляра.</span><span class="sxs-lookup"><span data-stu-id="35dd5-119">For example, assume a Skype for Business meeting is scheduled to occur on a weekly basis for one year, and a file is uploaded to the meeting during the first instance.</span></span> <span data-ttu-id="35dd5-120">Если по крайней мере один пользователь присоединяется к сеансу собраний каждую неделю, файл сохраняется в Skype для бизнеса Online Servers в течение всего года плюс 15 дней после последнего пользователя, который покидает Последнее собрание ряда.</span><span class="sxs-lookup"><span data-stu-id="35dd5-120">If at least one person joins the meeting session every week, the file is retained in Skype for Business Online servers for the entire year plus 15 days after the last person leaves the last meeting of the series.</span></span>
- <span data-ttu-id="35dd5-121">Провести **собрание** : контент сохраняется в течение 8 часов после окончания собрания.</span><span class="sxs-lookup"><span data-stu-id="35dd5-121">**Meet Now meeting** - Content is retained for 8 hours after the meeting end time.</span></span>

> [!NOTE]
> <span data-ttu-id="35dd5-122">Если пользователь не лицензируется или отключен (например, если для **msRTCSIP-userenabled** задано значение *false*), а затем он повторно лицензирован или повторно включен, контент собраний не сохраняется.</span><span class="sxs-lookup"><span data-stu-id="35dd5-122">If a user is unlicensed or disabled (e.g., if **msRTCSIP-userenabled** is set to *False*), and is then re-licensed or reenabled, meeting content is not retained.</span></span>

## <a name="meeting-expiration"></a><span data-ttu-id="35dd5-123">Окончание срока действия собрания</span><span class="sxs-lookup"><span data-stu-id="35dd5-123">Meeting Expiration</span></span>

<span data-ttu-id="35dd5-124">Пользователи могут получить доступ к определенному собранию после его завершения в следующие сроки:</span><span class="sxs-lookup"><span data-stu-id="35dd5-124">Users can access a specific meeting after the meeting has ended, subject to the following expiration time periods:</span></span>

- <span data-ttu-id="35dd5-125">**Разовое собрание** — срок действия собрания истечет через 14 дней после окончания запланированного времени окончания собрания.</span><span class="sxs-lookup"><span data-stu-id="35dd5-125">**One-time meeting** - Meeting expires 14 days after the scheduled meeting end time.</span></span>
- <span data-ttu-id="35dd5-126">**Повторяющееся собрание с датой окончания** — срок действия собрания истечет через 14 дней после запланированного времени окончания последнего экземпляра собрания.</span><span class="sxs-lookup"><span data-stu-id="35dd5-126">**Recurring meeting with end date** - Meeting expires 14 days after the scheduled end time of the last meeting occurrence.</span></span>
- <span data-ttu-id="35dd5-127">Начать **собрание** : срок действия собрания истечет через 8 часов.</span><span class="sxs-lookup"><span data-stu-id="35dd5-127">**Meet Now meeting** - Meeting expires after 8 hours.</span></span>

## <a name="whiteboard-collaboration"></a><span data-ttu-id="35dd5-128">Совместная работа с доской</span><span class="sxs-lookup"><span data-stu-id="35dd5-128">Whiteboard Collaboration</span></span>

<span data-ttu-id="35dd5-129">Заметки, сделанные на досках, будут видны всем участникам.</span><span class="sxs-lookup"><span data-stu-id="35dd5-129">Annotations made on whiteboards will be seen by all participants.</span></span> <span data-ttu-id="35dd5-130">Когда вы сохраняете доску, доска и все заметки будут храниться на сервере Skype для бизнеса, и они будут храниться на сервере в соответствии с политиками срока действия контента для собраний, установленными администратором.</span><span class="sxs-lookup"><span data-stu-id="35dd5-130">When saving a whiteboard, the whiteboard and all annotations will be stored on a Skype for Business server, and it will be retained on the server according to meeting content expiration policies set by the administrator.</span></span>

## <a name="audio-test-service"></a><span data-ttu-id="35dd5-131">Служба проверки звука</span><span class="sxs-lookup"><span data-stu-id="35dd5-131">Audio Test Service</span></span>

<span data-ttu-id="35dd5-132">В процессе проверки звука записывается краткое (приблизительно в 5 секундах) пример голосовых вызовов.</span><span class="sxs-lookup"><span data-stu-id="35dd5-132">A short (approximately 5 seconds) sample of your voice is recorded during the Audio Test Service call.</span></span> <span data-ttu-id="35dd5-133">Образец голосовой связи используется для проверки и/или проверки качества звука звонка Skype для бизнеса на основе качества записи.</span><span class="sxs-lookup"><span data-stu-id="35dd5-133">The voice sample is used by you to check and/or verify the sound quality of your Skype for Business call based on the quality of the recording.</span></span> <span data-ttu-id="35dd5-134">При завершении вызова службы проверки звука образец голосовой связи удаляется.</span><span class="sxs-lookup"><span data-stu-id="35dd5-134">When the Audio Test Service call ends, the voice sample is deleted.</span></span>

## <a name="persistent-group-chat"></a><span data-ttu-id="35dd5-135">Сохраняемый групповой чат</span><span class="sxs-lookup"><span data-stu-id="35dd5-135">Persistent Group Chat</span></span>

<span data-ttu-id="35dd5-136">Persistent Group Chat хранит содержимое бесед из группового чата.</span><span class="sxs-lookup"><span data-stu-id="35dd5-136">Persistent Group Chat stores the content of group chat conversations.</span></span> <span data-ttu-id="35dd5-137">Если этот параметр включен, администратор может управлять сроком хранения данных, на сервере, на котором хранятся эти сведения, если журнал группового чата архивируется для соответствия или других целей, а также для управления и изменения любых свойств комнаты.</span><span class="sxs-lookup"><span data-stu-id="35dd5-137">If enabled, the administrator can control the retention period, the server on which this information is stored, if Group Chat history is archived for compliance or other purposes, and manage/modify any properties on a room.</span></span> <span data-ttu-id="35dd5-138">Пользователи с разными ролями имеют разный доступ к постоянным данным, как показано ниже.</span><span class="sxs-lookup"><span data-stu-id="35dd5-138">Users with different roles have different access to the persisted data, as follows:</span></span>

- <span data-ttu-id="35dd5-139">Администраторы могут удалять старые материалы (например, содержимое, опубликованное до определенной даты) из любой комнаты чата, чтобы размер базы данных значительно увеличиваться.</span><span class="sxs-lookup"><span data-stu-id="35dd5-139">Administrators can delete older content (for example, content posted before a certain date) from any chat room to keep the size of the database from growing greatly.</span></span> <span data-ttu-id="35dd5-140">Либо они могут удалять или заменять сообщения, которые считаются недопустимыми для конкретной комнаты чата (или считаются неуместными).</span><span class="sxs-lookup"><span data-stu-id="35dd5-140">Or, they can remove or replace messages considered inappropriate for a given chat room (or considered unsuitable).</span></span>
- <span data-ttu-id="35dd5-141">Конечные пользователи, включая авторов сообщений, не могут удалять контент из комнаты чата.</span><span class="sxs-lookup"><span data-stu-id="35dd5-141">End-users, including message authors, cannot delete content from any chat room.</span></span>
- <span data-ttu-id="35dd5-142">Менеджеры комнаты чата могут отключать комнаты, но не могут удалять комнаты.</span><span class="sxs-lookup"><span data-stu-id="35dd5-142">Chat room managers can disable rooms but cannot delete rooms.</span></span> <span data-ttu-id="35dd5-143">Только администраторы могут удалять комнату чата после ее создания.</span><span class="sxs-lookup"><span data-stu-id="35dd5-143">Only administrators can delete a chat room after it is created.</span></span>