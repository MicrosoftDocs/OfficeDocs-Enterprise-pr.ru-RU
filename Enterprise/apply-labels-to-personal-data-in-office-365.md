---
title: Применение меток к персональным данным в Office 365
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 2/7/2018
ms.audience: ITPro
ms.topic: overview
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- GDPR
ms.service: o365-solutions
localization_priority: Priority
ms.custom: ''
ms.assetid: ''
search.appverid:
- MET150
description: Узнайте, как использовать метки Office для защиты данных в соответствии с регламентом GDPR.
ms.openlocfilehash: c0058a023b807b81df42274d5e8b9408e37d505d
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/21/2018
ms.locfileid: "22914934"
---
# <a name="apply-labels-to-personal-data-in-office-365"></a><span data-ttu-id="09263-103">Применение меток к персональным данным в Office 365</span><span class="sxs-lookup"><span data-stu-id="09263-103">Apply labels to personal data in Office 365</span></span>

 <span data-ttu-id="09263-p101">Указания в этой статье помогут вам, если вы используете метки Office для защиты данных в соответствии с регламентом GDPR. Сегодня метки можно создавать в Центре безопасности и соответствия требованиям Office 365 и Azure Information Protection. Со временем эти технологии будут объединены в единое решение.</span><span class="sxs-lookup"><span data-stu-id="09263-p101">Use this topic if you are using Office labels as part of your GDPR protection plan. Today labels can be created in the Office 365 Security & Compliance Center and in Azure Information Protection. Over time these technologies will converge into a unified labeling and classification experience and you will be able to achieve even more.</span></span>

<span data-ttu-id="09263-p102">Если вы используете метки для защиты персональных данных в Office 365, корпорация Майкрософт рекомендует начать работу с метками Office. Расширенное управление данными позволяет автоматически применять метки в зависимости от типов конфиденциальной информации или других условий. Метки Office можно использовать с защитой от потери данных. Вы также можете использовать метки с функциями обнаружения электронных данных и поиска контента. В ближайшее время вы сможете использовать метки и типы конфиденциальной информации с Cloud App Security для отслеживания персональных данных, которые хранятся в других приложениях SaaS.</span><span class="sxs-lookup"><span data-stu-id="09263-p102">If you are using labels for protection of personal data in Office 365, Microsoft recommends you start with Office labels. You can use Advanced Data Governance to automatically apply labels based on sensitive information types or other criteria. You can use Office labels with data loss prevention to apply protection. You can also use labels with eDiscovery and Content Search. You’ll soon be able to use both labels and sensitive information types with Cloud App Security to monitor personal data that resides in other SaaS apps.</span></span>

<span data-ttu-id="09263-p103">В настоящее время Azure Information Protection рекомендуется использовать для применения меток к файлам в локальной среде и других облачных службах, а также шифрования файлов Office 365 с помощью Azure Rights Management (Azure RMS), например файлов с коммерческими тайнами.</span><span class="sxs-lookup"><span data-stu-id="09263-p103">Azure Information Protection labels are currently recommended for applying labels to files on premises and in other cloud services and providers. These are also recommended for files in Office 365 that require Azure Rights Management (Azure RMS) encryption for data protection, such as trade secret files.</span></span>

<span data-ttu-id="09263-p104">Сейчас Azure Information Protection не рекомендуется использовать для шифрования файлов Office 365 с данными, на которые распространяется регламент GDPR. Службы Office 365 в настоящее время не могут считывать файлы, зашифрованные с использованием RMS, поэтому не могут находить конфиденциальные данные в этих файлах.</span><span class="sxs-lookup"><span data-stu-id="09263-p104">At this time, using Azure Information Protection to apply Azure RMS encryption is not recommended for files in Office 365 with data that is subject to the GDPR. Office 365 services currently cannot read into RMS-encrypted files. Therefore, the service can’t find sensitive data in these files.</span></span>

<span data-ttu-id="09263-p105">Метки Azure Information Protection можно применять к почте в Exchange Online. Кроме того, их можно использовать при защите от потери данных в Office 365. В ближайшее время ожидается выход единой подсистемы классификации и применения меток, с помощью которой вы сможете использовать одни метки для электронной почты и файлов, в том числе автоматически применять метки и защищать передаваемые сообщения электронной почты.</span><span class="sxs-lookup"><span data-stu-id="09263-p105">Azure Information Protection labels can be applied to mail in Exchange Online and these labels work with Office 365 data loss prevention. Coming soon with the unified classification and labeling engine you will be able to use the same labels for email and files, including automatically labeling and protecting email in transit.</span></span>

![Метки Office 365 и Azure Information Protection](Media/Apply-labels-to-personal-data-in-Office-365-image1.png)

<span data-ttu-id="09263-120">На этом рисунке:</span><span class="sxs-lookup"><span data-stu-id="09263-120">In the illustration:</span></span>

-   <span data-ttu-id="09263-121">Используйте метки Office 365 для персональных данных, строго регулируемых файлов и файлов с коммерческими тайнами в SharePoint Online и OneDrive для бизнеса.</span><span class="sxs-lookup"><span data-stu-id="09263-121">Use Office 365 labels for personal data and for highly regulated & trade secret files in SharePoint Online and OneDrive for Business.</span></span>

-   <span data-ttu-id="09263-122">Используйте метки Azure Information Protection (AIP) для строго регулируемых файлов и файлов с коммерческими тайнами, электронной почты Exchange Online, файлов в других службах SaaS, файлов в локальных центрах данных и других облачных службах.</span><span class="sxs-lookup"><span data-stu-id="09263-122">Use Azure Information Protection (AIP) labels for highly regulated & trade secret files, Exchange Online email, files in other SaaS services, files in on-premises datacenters, and files in other cloud providers.</span></span>

-   <span data-ttu-id="09263-123">Ожидается в ближайшее время: метки обоих типов будут объединены в единое решение.</span><span class="sxs-lookup"><span data-stu-id="09263-123">Coming soon: both types of labels will converge into a unified classification and labeling experience.</span></span>

## <a name="use-office-labels-and-sensitive-information-types-across-microsoft-365-for-information-protection"></a><span data-ttu-id="09263-124">Использование меток Office и типов конфиденциальной информации в Microsoft Office 365 для защиты данных</span><span class="sxs-lookup"><span data-stu-id="09263-124">Use Office labels and sensitive information types across Microsoft 365 for information protection</span></span>

<span data-ttu-id="09263-125">На рисунке ниже показано, как метки и типы конфиденциальной информации Office можно использовать в политиках в отношении меток, политиках защиты от потери данных и политиках Cloud App Security.</span><span class="sxs-lookup"><span data-stu-id="09263-125">The following illustration shows how Office labels and sensitive information types can be used in label policies, data loss prevention policies, and with Cloud App Security policies.</span></span>

![Метки и типы конфиденциальной информации Office](Media/Apply-labels-to-personal-data-in-Office-365-image2.png)

<span data-ttu-id="09263-127">Для работы специальных возможностей примеры на рисунке также приведены в таблице ниже.</span><span class="sxs-lookup"><span data-stu-id="09263-127">For accessibility, the following table provides the same examples in the illustration.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="09263-128"><strong>Элементы классификации</strong></span><span class="sxs-lookup"><span data-stu-id="09263-128"><strong>Classification elements</strong></span></span></th>
<th align="left"><span data-ttu-id="09263-129"><strong>Политики в отношении меток — 2 примера</strong></span><span class="sxs-lookup"><span data-stu-id="09263-129"><strong>Label policies — 2 examples</strong></span></span></th>
<th align="left"><span data-ttu-id="09263-130"><strong>Политики защиты от потери данных — 2 примера</strong></span><span class="sxs-lookup"><span data-stu-id="09263-130"><strong>Data loss prevention policies — 2 examples</strong></span></span></th>
<th align="left"><span data-ttu-id="09263-131"><strong>Политики Cloud App Security для всех приложений SaaS — 1 пример</strong></span><span class="sxs-lookup"><span data-stu-id="09263-131"><strong>Cloud App Security policies for all SaaS apps — 1 example</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="09263-p106">Метки Office. Примеры: "Персональные", "Общедоступные", "Данные клиента", "Данные о персонале" "Конфиденциально", "Строго конфиденциально"</span><span class="sxs-lookup"><span data-stu-id="09263-p106">Office labels. Examples: Personal, Public, Customer data, HR data, Confidential, Highly confidential</span></span></td>
<td align="left"><p><span data-ttu-id="09263-p107">Автоматически применять эту метку...</span><span class="sxs-lookup"><span data-stu-id="09263-p107">Auto apply this label . . .</span></span></p>
<p><span data-ttu-id="09263-137">Данные клиента</span><span class="sxs-lookup"><span data-stu-id="09263-137">Customer data</span></span></p>
<p><span data-ttu-id="09263-p108">...к документам, которые соответствуют этим типам конфиденциальной информации...</span><span class="sxs-lookup"><span data-stu-id="09263-p108">. . . to documents that match these sensitive information types . . .</span></span></p>
<p><span data-ttu-id="09263-144">&lt;список примеров типов конфиденциальной информации&gt;</span><span class="sxs-lookup"><span data-stu-id="09263-144">&lt;list of example sensitive information types&gt;</span></span></p></td>
<td align="left"><p><span data-ttu-id="09263-p109">Применять эту защиту...</span><span class="sxs-lookup"><span data-stu-id="09263-p109">Apply this protection . . .</span></span></p>
<p><span data-ttu-id="09263-148">&lt;определение защиты&gt;</span><span class="sxs-lookup"><span data-stu-id="09263-148">&lt;define protection&gt;</span></span></p>
<p><span data-ttu-id="09263-p110">...к документам с этой меткой...</span><span class="sxs-lookup"><span data-stu-id="09263-p110">. . . to documents with this label . . .</span></span></p>
<p><span data-ttu-id="09263-155">Данные клиента</span><span class="sxs-lookup"><span data-stu-id="09263-155">Customer data</span></span></p></td>
<td align="left"><p><span data-ttu-id="09263-p111">Оповещать, когда к файлам с этими атрибутами...</span><span class="sxs-lookup"><span data-stu-id="09263-p111">Alert when files with these attributes . . .</span></span></p>
<p><span data-ttu-id="09263-159">&lt;предопределенный атрибут PII -или- особое выражение&gt;</span><span class="sxs-lookup"><span data-stu-id="09263-159">&lt;predefined PII attribute -or- custom expression&gt;</span></span></p>
<p><span data-ttu-id="09263-p112">...в любом санкционированном приложении SaaS предоставляется общий доступ за пределами организации</span><span class="sxs-lookup"><span data-stu-id="09263-p112">. . . in any sanctioned SaaS app are shared outside the organization</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="09263-p113">Типы конфиденциальной информации. Примеры: "Внутренний идентификационный номер гражданина Бельгии", "Номер кредитной карты", "Номер идентификационной карты гражданина Хорватии", "Национальный идентификационный номер гражданина Финляндии"</span><span class="sxs-lookup"><span data-stu-id="09263-p113">Sensitive information types. Examples: Belgium National Number, Credit Card Number, Croatia Identity Cart Number, Finland National ID</span></span></td>
<td align="left"><p><span data-ttu-id="09263-p114">Публиковать эти метки для пользователей, чтобы вручную применять...</span><span class="sxs-lookup"><span data-stu-id="09263-p114">Publish these labels for users to manually apply . . .</span></span></p>
<p><span data-ttu-id="09263-169">&lt;выберите метки&gt;</span><span class="sxs-lookup"><span data-stu-id="09263-169">&lt;select labels&gt;</span></span></p>
<p><span data-ttu-id="09263-p115">...к этим расположениям...</span><span class="sxs-lookup"><span data-stu-id="09263-p115">. . . to these locations . . .</span></span></p>
<p><span data-ttu-id="09263-176">&lt;все расположения или выберите расположения&gt;</span><span class="sxs-lookup"><span data-stu-id="09263-176">&lt;all locations or choose specific locations&gt;</span></span></p></td>
<td align="left"><p><span data-ttu-id="09263-p116">Применять эту защиту...</span><span class="sxs-lookup"><span data-stu-id="09263-p116">Apply this protection . . .</span></span></p>
<p><span data-ttu-id="09263-180">&lt;определение защиты&gt;</span><span class="sxs-lookup"><span data-stu-id="09263-180">&lt;define protection&gt;</span></span></p>
<p><span data-ttu-id="09263-p117">...к документам, которые соответствуют этим типам конфиденциальной информации&gt;</span><span class="sxs-lookup"><span data-stu-id="09263-p117">. . . to documents that match these sensitive information types&gt;</span></span></p></td>
<td align="left"><span data-ttu-id="09263-185">Примечание. Атрибуты, которые скоро появятся в Cloud App Security: типы конфиденциальной информации Office 365 и объединенные метки (Office 365 и Azure Information Protection).</span><span class="sxs-lookup"><span data-stu-id="09263-185">Note: Attributes coming soon to Cloud App Security include Office 365 sensitive information types and Unified labels across Office 365 and Azure Information Protection.</span></span></td>
</tr>
</tbody>
</table>

## <a name="prioritize-auto-apply-label-policies"></a><span data-ttu-id="09263-186">Определение приоритетных политик автоматического применения меток</span><span class="sxs-lookup"><span data-stu-id="09263-186">Prioritize auto-apply label policies</span></span>

<span data-ttu-id="09263-p118">Корпорация Майкрософт рекомендует автоматически применять метки к персональным данным, на которые распространяется регламент GDPR, используя типы конфиденциальной информации, подобранные для вашей среды. Важно хорошо правильно разработать и проверить политики автоматического применения меток, чтобы они правильно работали.</span><span class="sxs-lookup"><span data-stu-id="09263-p118">For personal data that is subject to GDPR, Microsoft recommends auto-applying labels by using the sensitive information types you curated for your environment. It is important that auto-apply label policies are well designed and tested to ensure the intended behavior occurs.</span></span>

<span data-ttu-id="09263-p119">На результаты влияет порядок создания политик автоматического применения, а также то, применяют ли эти метки пользователи. Поэтому крайне важно тщательно спланировать выпуск. Вот что нужно знать.</span><span class="sxs-lookup"><span data-stu-id="09263-p119">The order that auto-apply policies are created and whether users are also applying these labels affect the result. So, it is important to carefully plan the roll-out. Here’s what you need to know.</span></span>

### <a name="one-label-at-a-time"></a><span data-ttu-id="09263-191">По одной метке</span><span class="sxs-lookup"><span data-stu-id="09263-191">One label at a time</span></span>

<span data-ttu-id="09263-192">Документу можно назначить только одну метку.</span><span class="sxs-lookup"><span data-stu-id="09263-192">You can only assign one label to a document.</span></span>

### <a name="older-auto-apply-policies-win"></a><span data-ttu-id="09263-193">Установка приоритета для политик автоматического применения более ранних версий</span><span class="sxs-lookup"><span data-stu-id="09263-193">Older auto-apply policies win</span></span>

<span data-ttu-id="09263-p120">Если имеется несколько правил назначения автоматической метки, а содержимое соответствует условиям всех этих правил, будет назначена метка для самого старого правила. По этой причине очень важно тщательно спланировать применение политик в отношении меток, прежде чем их настраивать. Если организации необходимо изменить приоритет политик в отношении меток, их потребуется удалить и заново создать.</span><span class="sxs-lookup"><span data-stu-id="09263-p120">If there are multiple rules that assign an auto-apply label and content meets the conditions of multiple rules, the label for the oldest rule is assigned. For this reason, it is important to plan the label policies carefully before configuring them. If an organization requires a change to the priority of the label policies, they will need to delete and recreate them.</span></span>

### <a name="manual-user-applied-labels-trump-auto-applied-labels"></a><span data-ttu-id="09263-197">Метки, вручную примененные пользователем, имеют приоритет над автоматическими метками</span><span class="sxs-lookup"><span data-stu-id="09263-197">Manual user-applied labels trump auto-applied labels</span></span>

<span data-ttu-id="09263-p121">Метки, вручную примененные пользователем, имеют приоритет над автоматическими метками. Политики автоматического применения не могут заменить метку, которую уже применил пользователь. Пользователи могут заменять автоматические метки.</span><span class="sxs-lookup"><span data-stu-id="09263-p121">Manual user applied labels trump auto-applied labels. Auto-apply policies cannot replace a label that is already applied by a user. Users can replace labels that are auto-applied.</span></span>

### <a name="auto-assigned-labels-can-be-updated"></a><span data-ttu-id="09263-201">Возможность обновления автоматически назначаемых меток</span><span class="sxs-lookup"><span data-stu-id="09263-201">Auto-assigned labels can be updated</span></span>

<span data-ttu-id="09263-202">Автоматически назначаемые метки можно обновлять с помощью новых политик в отношении меток или путем обновления существующих политик.</span><span class="sxs-lookup"><span data-stu-id="09263-202">Auto-assigned labels can be updated by either newer label policies or by updates to existing policies.</span></span>

<span data-ttu-id="09263-203">Убедитесь, что ваш план по внедрению меток предусматривает следующее:</span><span class="sxs-lookup"><span data-stu-id="09263-203">Be sure your plan for implementing labels includes:</span></span>

-   <span data-ttu-id="09263-204">Определение приоритетного порядка создания политик автоматического применения.</span><span class="sxs-lookup"><span data-stu-id="09263-204">Prioritizing the order that auto-apply policies are created.</span></span>

-   <span data-ttu-id="09263-p122">Наличие достаточного времени для автоматического применения меток перед их развертыванием для применения пользователями вручную. Применение меток ко всему содержимому, которое соответствует условиям, может занять до семи дней.</span><span class="sxs-lookup"><span data-stu-id="09263-p122">Allowing enough time for labels to be automatically applied before rolling these out for users to manually apply. It can take up to seven days for the labels to be applied to all content that matches the conditions.</span></span>

### <a name="example-priority-for-creating-the-auto-apply-policies"></a><span data-ttu-id="09263-207">Пример установки приоритета для создания политик автоматического применения</span><span class="sxs-lookup"><span data-stu-id="09263-207">Example priority for creating the auto-apply policies</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="09263-208"><strong>Метки</strong></span><span class="sxs-lookup"><span data-stu-id="09263-208"><strong>Labels</strong></span></span></th>
<th align="left"><span data-ttu-id="09263-209"><strong>Приоритетный порядок создания политик автоматического применения</strong></span><span class="sxs-lookup"><span data-stu-id="09263-209"><strong>Priority order to create auto-apply policies</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="09263-210">Отдел кадров — данные о сотрудниках</span><span class="sxs-lookup"><span data-stu-id="09263-210">Human Resources — Employee Data</span></span></td>
<td align="left"><span data-ttu-id="09263-211">1</span><span class="sxs-lookup"><span data-stu-id="09263-211">1</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="09263-212">Данные клиента</span><span class="sxs-lookup"><span data-stu-id="09263-212">Customer Data</span></span></td>
<td align="left"><span data-ttu-id="09263-213">2</span><span class="sxs-lookup"><span data-stu-id="09263-213">2</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="09263-214">Строго конфиденциально</span><span class="sxs-lookup"><span data-stu-id="09263-214">Highly Confidential</span></span></td>
<td align="left"><span data-ttu-id="09263-215">3</span><span class="sxs-lookup"><span data-stu-id="09263-215">3</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="09263-216">Отдел кадров — данные о зарплате</span><span class="sxs-lookup"><span data-stu-id="09263-216">Human Resources — Salary Data</span></span></td>
<td align="left"><span data-ttu-id="09263-217">4</span><span class="sxs-lookup"><span data-stu-id="09263-217">4</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="09263-218">Конфиденциально</span><span class="sxs-lookup"><span data-stu-id="09263-218">Confidential</span></span></td>
<td align="left"><span data-ttu-id="09263-219">5</span><span class="sxs-lookup"><span data-stu-id="09263-219">5</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="09263-220">Общедоступные</span><span class="sxs-lookup"><span data-stu-id="09263-220">Public</span></span></td>
<td align="left"><span data-ttu-id="09263-221">6</span><span class="sxs-lookup"><span data-stu-id="09263-221">6</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="09263-222">Персональные</span><span class="sxs-lookup"><span data-stu-id="09263-222">Personal</span></span></td>
<td align="left"><span data-ttu-id="09263-223">Без политики автоматического применения</span><span class="sxs-lookup"><span data-stu-id="09263-223">No auto-apply policy</span></span></td>
</tr>
</tbody>
</table>

## <a name="create-labels-and-auto-apply-label-policies"></a><span data-ttu-id="09263-224">Создание меток и политик их автоматического применения</span><span class="sxs-lookup"><span data-stu-id="09263-224">Create labels and auto-apply label policies</span></span>

<span data-ttu-id="09263-225">Метки и политики создаются в Центре безопасности и соответствия требованиям.</span><span class="sxs-lookup"><span data-stu-id="09263-225">Create labels and policies in the Security & Compliance Center.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="09263-226"><strong>Шаг</strong></span><span class="sxs-lookup"><span data-stu-id="09263-226"><strong>Step</strong></span></span></th>
<th align="left"><span data-ttu-id="09263-227"><strong>Описание</strong></span><span class="sxs-lookup"><span data-stu-id="09263-227"><strong>Description</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><span data-ttu-id="09263-228">Предоставление разрешений ответственным за обеспечение соответствия требованиям</span><span class="sxs-lookup"><span data-stu-id="09263-228">Give permissions to members of your compliance team.</span></span></p></td>
<td align="left"><p><span data-ttu-id="09263-p123">Ответственным за обеспечение соответствия требованиям, которые будут создавать метки, необходимы разрешения на использование Центра безопасности и соответствия требованиям. Перейдите в раздел "Разрешения" в Центре безопасности и соответствия требованиям и внесите изменения в список участников группы "Администратор соответствия требованиям".</span><span class="sxs-lookup"><span data-stu-id="09263-p123">Members of your compliance team who will create labels need permissions to use the Security &amp; Compliance Center. Go to Permissions in Security and Compliance Center and modify the members of the Compliance Administrator group.</span></span></p>
<p><span data-ttu-id="09263-231">См. статью <a href="https://support.office.com/en-ie/article/Give-users-access-to-the-Office-365-Security-Compliance-Center-2cfce2c8-20c5-47f9-afc4-24b059c1bd76">Предоставление пользователям доступа к Центру безопасности и соответствия требованиям Office 365</a>.</span><span class="sxs-lookup"><span data-stu-id="09263-231">See <a href="https://support.office.com/en-ie/article/Give-users-access-to-the-Office-365-Security-Compliance-Center-2cfce2c8-20c5-47f9-afc4-24b059c1bd76">Give users access to the Office 365 Security &amp; Compliance Center</a>.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="09263-232">Создание меток Office</span><span class="sxs-lookup"><span data-stu-id="09263-232">Create Office labels.</span></span></p></td>
<td align="left"><span data-ttu-id="09263-233">Перейдите в раздел "Классификации" в Центре безопасности и соответствия требованиям, выберите "Метки" и создайте метки для вашей среды.</span><span class="sxs-lookup"><span data-stu-id="09263-233">Go to Classifications in Security and Compliance Center, choose Labels, and create the labels for your environment.</span></span></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="09263-234">Создание политик автоматического применения меток</span><span class="sxs-lookup"><span data-stu-id="09263-234">Create auto-apply policies for labels.</span></span></p></td>
<td align="left"><span data-ttu-id="09263-p124">Перейдите в раздел "Классификации" в Центре безопасности и соответствия требованиям, выберите пункт "Политики меток" и создайте политики для автоматического применения меток (обязательно в порядке приоритета).</span><span class="sxs-lookup"><span data-stu-id="09263-p124">Go to Classification in Security and Compliance Center, choose Label policies, and create the policies for auto-applying labels. Be sure to create these policies in the prioritized order.</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="09263-237">Ни рисунке ниже показано, как создать автоматическую метку "Данные клиента".</span><span class="sxs-lookup"><span data-stu-id="09263-237">The following illustration shows how to create an auto-apply label for the Customer data label.</span></span>

![Создание и применение метки для данных клиента](Media/Apply-labels-to-personal-data-in-Office-365-image3.png)

<span data-ttu-id="09263-239">На этом рисунке:</span><span class="sxs-lookup"><span data-stu-id="09263-239">In the illustration:</span></span>

-   <span data-ttu-id="09263-240">Создается метка "Данные клиента".</span><span class="sxs-lookup"><span data-stu-id="09263-240">The “Customer data” label is created.</span></span>

-   <span data-ttu-id="09263-241">Перечисляются типы конфиденциальной информации для соблюдения регламента GDPR: "Внутренний идентификационный номер гражданина Бельгии", "Номер кредитной карты", "Номер идентификационной карты гражданина Хорватии", "Национальный идентификационный номер гражданина Финляндии".</span><span class="sxs-lookup"><span data-stu-id="09263-241">The desired sensitive information types for GDPR are listed: Belgium National Number, Credit Card Number, Croatia Identity Card Number, Finland National ID.</span></span>

-   <span data-ttu-id="09263-242">Создается политика автоматического применения, которая назначает метку "Данные клиента" всем файлам, включающим один из типов конфиденциальной информации, добавленных в политику.</span><span class="sxs-lookup"><span data-stu-id="09263-242">Create an auto-apply policy assigns the label “Customer data” to any file that includes one of the sensitive information types that you add to the policy.</span></span>
