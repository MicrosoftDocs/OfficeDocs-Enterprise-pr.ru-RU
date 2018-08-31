---
title: Защита сайтов групп SharePoint Online, содержащих конфиденциальные и строго конфиденциальные ресурсы
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 8c088e88-a9ba-4044-bced-722196f4496d
description: Сводка. Узнайте, как в компании Contoso реализованы защита конфиденциальных данных и строго конфиденциальные сайты групп SharePoint Online, обеспечивающие простую, но безопасную совместную работу руководителей и исследовательских центров.
ms.openlocfilehash: 23511e4156bb04e8bacf970913b00ed36e8ff9c8
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/21/2018
ms.locfileid: "22914864"
---
# <a name="secure-sharepoint-online-team-sites-for-sensitive-and-highly-confidential-assets"></a><span data-ttu-id="8783b-103">Защита сайтов групп SharePoint Online, содержащих конфиденциальные и строго конфиденциальные ресурсы</span><span class="sxs-lookup"><span data-stu-id="8783b-103">Secure SharePoint Online team sites for sensitive and highly confidential assets</span></span>

 <span data-ttu-id="8783b-104">**Сводка.** Узнайте, как в компании Contoso реализованы защита конфиденциальных данных и строго конфиденциальные сайты групп SharePoint Online, обеспечивающие простую, но безопасную совместную работу руководителей и исследовательских центров.</span><span class="sxs-lookup"><span data-stu-id="8783b-104">**Summary:** How Contoso implemented sensitive protection and highly confidential SharePoint Online team sites for easier, yet secure, collaboration for executives and its research centers.</span></span>
  
<span data-ttu-id="8783b-p101">Руководству высшего звена компании Contoso нужно использовать Office 365 и хранить свои файлы в одном расположении для совместной работы независимо от того, где находится тот или иной руководитель. Аналогичным образом, исследовательским отделам компании Contoso (расположенным в Париже, Нью-Йорке, Пекине и Бангалоре) требуется перенести свои локальные цифровые ресурсы в облако для удобства доступа и более открытой совместной работы между группами.</span><span class="sxs-lookup"><span data-stu-id="8783b-p101">The executive leadership of Contoso want to use Office 365 and store their files in a single location for collaboration, regardless of where an executive might be. Similarly, Contoso's research departments—with divisions in Paris, Moscow, New York, Beijing, and Bangalore—would like to transition their on-premises digital assets to the cloud for easier access and more open collaboration across teams.</span></span>
  
<span data-ttu-id="8783b-p102">Однако в обоих случаях доступ к этим ресурсам должен быть предоставлен лишь некоторым людям, которым разрешено просматривать и менять эти ресурсы. При этом текущими разрешениями для сайта должен управлять ИТ-персонал. Кроме того, даже если некоторые ресурсы намеренно или случайно передаются за пределы организации, они должны быть зашифрованы и защищены разрешениями, чтобы пользователи, у которых нет доступа, не могли просматривать и менять содержимое ресурсов.</span><span class="sxs-lookup"><span data-stu-id="8783b-p102">However, in both of these cases, access to these resources must be restricted to the subset of people who are allowed to view or change them, with ongoing permissions for the site administered by IT staff. Additionally, even if some resources are intentionally or unintentionally distributed, they must be encrypted and have permissions to prevent those who do not have access to view or change their contents.</span></span>
  
<span data-ttu-id="8783b-109">Администраторы системы безопасности и SharePoint в ИТ-отделе компании Contoso решили использовать защиту конфиденциальных данных и строго конфиденциальные сайты групп SharePoint Online, как показано на рис. 1.</span><span class="sxs-lookup"><span data-stu-id="8783b-109">Security and SharePoint administrators in Contoso's IT department decided to use sensitive protection and highly-confidential SharePoint Online team sites, as shown in Figure 1.</span></span>
  
<span data-ttu-id="8783b-110">**Рис. 1. Сравнение защиты конфиденциальных данных и строго конфиденциальных сайтов групп SharePoint Online**</span><span class="sxs-lookup"><span data-stu-id="8783b-110">**Figure 1: Comparison of sensitive protection and highly confidential SharePoint Online team sites**</span></span>

![Защита конфиденциальных данных и строго конфиденциальные сайты групп SharePoint Online](media/Contoso-Poster/SP-Solution.png)
  
<span data-ttu-id="8783b-112">Чтобы создать защищенные сайты групп SharePoint Online для руководителей и исследовательских групп, компания Contoso выполнила следующие действия:</span><span class="sxs-lookup"><span data-stu-id="8783b-112">Contoso used these steps to create secure SharePoint Online team sites for their executives and research teams:</span></span>
  
1. <span data-ttu-id="8783b-113">Создание конфиденциального сайта группы **Руководители** в SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="8783b-113">Create an **Executives** sensitive SharePoint Online team site</span></span>
    
    <span data-ttu-id="8783b-114">На новом сайте группы используются существующие группы Azure Active Directory (AD) для руководителей в качестве участников с уровнем разрешений SharePoint "Редактирование", и небольшой набор учетных записей администраторов SharePoint, которые являются владельцами с уровнем разрешением "Полный доступ".</span><span class="sxs-lookup"><span data-stu-id="8783b-114">The new team site uses existing Azure Active Directory (AD) groups for executives as members with the Edit SharePoint permission level and a small set of SharePoint administrator accounts as owners with the Full Control permission level.</span></span>
    
2. <span data-ttu-id="8783b-115">Перенос файлов руководителей</span><span class="sxs-lookup"><span data-stu-id="8783b-115">Migrate executives files</span></span>
    
    <span data-ttu-id="8783b-116">Перемещение существующих файлов и папок руководителей на новый сайт группы "Руководители" в SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="8783b-116">Move existing on-premises executive files and folders to the new Executives SharePoint Online team site.</span></span>
    
3. <span data-ttu-id="8783b-117">Создание строго конфиденциального сайта группы **Исследования** в SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="8783b-117">Create a **Research** highly confidential SharePoint Online team site</span></span>
    
    <span data-ttu-id="8783b-p103">На новом сайте группы используются существующие исследовательские группы Azure AD в качестве участников с уровнем разрешений "Редактирование", и небольшой набор учетных записей администраторов SharePoint, являющихся владельцами с уровнем разрешений "Полный доступ". Метка AIP, назначенная исследовательским файлам, гарантирует, что они зашифрованы и их могут открывать только участники исследовательской группы.</span><span class="sxs-lookup"><span data-stu-id="8783b-p103">The new team site uses existing Azure AD research team groups as members with the Edit permission level and a small set of SharePoint administrator accounts as owners with the Full Control permission level. An AIP label assigned to research files ensures that they are encrypted and only members of a research group can open them.</span></span>
    
4. <span data-ttu-id="8783b-120">Перенос файлов исследований</span><span class="sxs-lookup"><span data-stu-id="8783b-120">Migrate research files</span></span>
    
    <span data-ttu-id="8783b-121">Перемещение существующих локальных файлов и папок исследовательской группы на сайт группы "Исследования" в SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="8783b-121">Move existing research team on-premises files and folders to the new Research SharePoint Online team site.</span></span>
    
<span data-ttu-id="8783b-p104">В результате получается два сайта для совместной работы, доступ к которым строго контролируют система безопасности и администраторы SharePoint. Файлы с меткой AIP "Строго конфиденциальный" всегда шифруются, даже если они распространяются за пределами сайта группы "Исследования". При этом их может открыть только участник исследовательской группы.</span><span class="sxs-lookup"><span data-stu-id="8783b-p104">The result is two collaboration sites whose access is tightly controlled by security and SharePoint administrators. For files with the Highly Confidential AIP label, even if they are distributed outside the Research team site, they are encrypted and can only be opened by a member of a research team.</span></span>
  
<span data-ttu-id="8783b-124">Дополнительные сведения см. в статье [Защита сайтов и файлов SharePoint Online](https://docs.microsoft.com/microsoft-365-enterprise/secure-sharepoint-online-sites-and-files).</span><span class="sxs-lookup"><span data-stu-id="8783b-124">For more information, see [Secure SharePoint Online sites and files](https://docs.microsoft.com/microsoft-365-enterprise/secure-sharepoint-online-sites-and-files).</span></span>
  
 <span data-ttu-id="8783b-125">Сведения о том, как настроить такую защиту для демонстрации, экспериментальной системы либо среды разработки и тестирования, см. в статье [Защита сайтов SharePoint Online в среде разработки и тестирования](https://docs.microsoft.com/microsoft-365-enterprise/secure-sharepoint-online-sites-dev-test).</span><span class="sxs-lookup"><span data-stu-id="8783b-125">To set this up for demonstration, proof-of-concept, or dev/test, see [Secure SharePoint Online sites in a dev/test environment](https://docs.microsoft.com/microsoft-365-enterprise/secure-sharepoint-online-sites-dev-test).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="8783b-126">См. также</span><span class="sxs-lookup"><span data-stu-id="8783b-126">See Also</span></span>

[<span data-ttu-id="8783b-127">Корпоративные сценарии для корпорации Contoso</span><span class="sxs-lookup"><span data-stu-id="8783b-127">Enterprise scenarios for the Contoso Corporation</span></span>](enterprise-scenarios-for-the-contoso-corporation.md)
  
[<span data-ttu-id="8783b-128">Contoso в Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="8783b-128">Contoso in the Microsoft Cloud</span></span>](contoso-in-the-microsoft-cloud.md)
  
[<span data-ttu-id="8783b-129">Ресурсы для администраторов, посвященные архитектуре Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="8783b-129">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="8783b-130">База данных Stretch</span><span class="sxs-lookup"><span data-stu-id="8783b-130">Stretch Database</span></span>](https://msdn.microsoft.com/library/dn935011.aspx)
  
[<span data-ttu-id="8783b-131">Стратегия Enterprise Cloud корпорации Майкрософт: ресурсы для лиц, принимающих решения в области ИТ</span><span class="sxs-lookup"><span data-stu-id="8783b-131">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)




