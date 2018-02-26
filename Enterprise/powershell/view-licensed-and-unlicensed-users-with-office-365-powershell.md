---
title: "Отображение списков пользователей с лицензиями и пользователей без лицензий с помощью Office 365 PowerShell"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- O365ITProTrain
- Ent_Office_Other
- PowerShell
ms.assetid: e4ee53ed-ed36-4993-89f4-5bec11031435
description: "В этой статье рассказывается, как использовать PowerShell в Office 365 для просмотра учетных записей пользователей с лицензиями и пользователей без лицензий."
ms.openlocfilehash: b26c98c1c294e2f1369d4368d0b1415702580a83
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2018
---
# <a name="view-licensed-and-unlicensed-users-with-office-365-powershell"></a><span data-ttu-id="c14c7-103">Отображение списков пользователей с лицензиями и пользователей без лицензий с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="c14c7-103">View licensed and unlicensed users with Office 365 PowerShell</span></span>

<span data-ttu-id="c14c7-104">**Сводка.** Узнайте, как просмотреть учетные записи пользователей Office 365 с лицензиями и без них, используя PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c14c7-104">**Summary:** Explains how to use Office 365 PowerShell to view licensed and unlicensed user accounts.</span></span>
  
<span data-ttu-id="c14c7-p101">Учетным записям пользователей в вашей организации Office 365: могут быть назначены все лицензии или часть лицензий (или вообще ни одной доступной лицензии) из планов лицензирования, имеющихся в организации. С помощью PowerShell в Office 365 вы можете быстро найти пользователей в организации, у которых есть лицензии, и пользователей, у которых их нет.</span><span class="sxs-lookup"><span data-stu-id="c14c7-p101">User accounts in your Office 365 organization may have some, all, or none of the available licenses assigned to them from the licensing plans that are available in your organization. You can use Office 365 PowerShell to quickly find the licensed and unlicensed users in your organization.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="c14c7-107">Перед началом работы</span><span class="sxs-lookup"><span data-stu-id="c14c7-107">Before you begin</span></span>

- <span data-ttu-id="c14c7-p102">Для процедур, описанных в этой статье, требуется подключение к PowerShell в Office 365. Указания см. в статье [Подключение к Office 365 PowerShell](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="c14c7-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="c14c7-110">Если использовать командлет **Get-MsolUser** без параметра _-All_, возвращаются только первые 500 учетных записей.</span><span class="sxs-lookup"><span data-stu-id="c14c7-110">If you use the **Get-MsolUser** cmdlet without using the _-All_ parameter, only the first 500 accounts are returned.</span></span>
    
## <a name="the-short-version-instructions-without-explanations"></a><span data-ttu-id="c14c7-111">Краткая версия (инструкции без пояснений)</span><span class="sxs-lookup"><span data-stu-id="c14c7-111">The short version (instructions without explanations)</span></span>

<span data-ttu-id="c14c7-p103">В этом разделе процедуры представлены без лишних слов и объяснений. Если у вас возникнут вопросы или вам потребуются дополнительные сведения, вы можете прочитать остальные разделы статьи.</span><span class="sxs-lookup"><span data-stu-id="c14c7-p103">This section presents the procedures without fanfare or superfluous explanation. If you have questions or want more information, you can read rest of the topic.</span></span>
  
<span data-ttu-id="c14c7-114">Чтобы отобразить список всех учетных записей пользователей в организации и сведения об их состояниях лицензирования, в PowerShell в Office 365 выполните указанную ниже команду.</span><span class="sxs-lookup"><span data-stu-id="c14c7-114">To view the list of all user accounts and their licensing status in your organization, run the following command in Office 365 PowerShell:</span></span>
  
```
Get-MsolUser -All
```

<span data-ttu-id="c14c7-115">Чтобы отобразить список всех учетных записей пользователей без лицензий в вашей организации, выполните указанную ниже команду.</span><span class="sxs-lookup"><span data-stu-id="c14c7-115">To view the list of all unlicensed user accounts in your organization, run the following command:</span></span>
  
```
Get-MsolUser -All -UnlicensedUsersOnly
```

<span data-ttu-id="c14c7-116">Чтобы отобразить список всех учетных записей пользователей с лицензиями в вашей организации, выполните указанную ниже команду.</span><span class="sxs-lookup"><span data-stu-id="c14c7-116">To view the list of all licensed user accounts in your organization, run the following command:</span></span>
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true}
```

## <a name="the-long-version-instructions-with-detailed-explanations"></a><span data-ttu-id="c14c7-117">Подробная версия (инструкции с подробными пояснениями)</span><span class="sxs-lookup"><span data-stu-id="c14c7-117">The long version (instructions with detailed explanations)</span></span>

<span data-ttu-id="c14c7-p104">Между учетными записями пользователей Office 365 и лицензиями Office 365 не обязательно наличие точного соответствия. У некоторых пользователей может не быть лицензии, а некоторые лицензии могут быть никому не назначены. (У одного пользователя может быть *несколько* лицензий.) При создании учетной записи пользователя Office 365 ([дополнительная информация](http://technet.microsoft.com/library/0ab9fcac-e5ea-4b5b-b72c-8c92c55565ac.aspx)) необязательно назначать ему лицензию: у нового пользователя будет действительная учетная запись, но он не сможет войти в Office 365. При попытке входа он увидит примерно следующее:</span><span class="sxs-lookup"><span data-stu-id="c14c7-p104">Office 365 user accounts and Office 365 licenses don't need to have a one-to-one correspondence: it's possible to have Office 365 users who do not have an Office 365 license, and it's possible to have Office 365 licenses that haven't been assigned to a user. (In fact, a single user account can even have  *multiple*  Office 365 licenses.) When you create a new Office 365 user account (see the article [License Office 365 users with Windows PowerShell](http://technet.microsoft.com/library/0ab9fcac-e5ea-4b5b-b72c-8c92c55565ac.aspx) for more information) you don't have to assign that user a license: the new user will have a valid account, but he or she won't be able to sign in to Office 365. If they try to sign in, they'll see something similar to this:</span></span>
  
![Пользователь без действительной лицензии Office 365.](images/o365_powershell_no_license.png)
  
<span data-ttu-id="c14c7-p105">Аналогично, пользователь может уйти во внеплановый отпуск, например творческий или декретный. В таком случае вы можете удалить лицензию этого пользователя, оставив учетную запись нетронутой (то есть оставив "как есть" все значения ее свойств, такие как адрес, номер телефона и т. д.). Благодаря этому вы можете назначить эту лицензию другому пользователю (например, временному сотруднику, занявшему должность пользователя, который ушел в отпуск). Когда пользователь вернется на работу, вы можете выдать ему новую лицензию, чтобы тот смог сразу вернуться к выполнению своих задач.</span><span class="sxs-lookup"><span data-stu-id="c14c7-p105">Likewise, you might have a user who will be taking some extended time off, perhaps for a sabbatical or for maternity/paternity leave. In a case like that, you could remove the user's license but leave the user account intact (that is, leave all its property values, such as address and phone number, as-is). By doing that, you can assign their license to someone else (like, say, a temporary worker filling in for the person on leave). When the user returns to work you can issue them a new license and they'll be able to resume working as if they'd never been gone.</span></span>
  
<span data-ttu-id="c14c7-p106">Таким образом, у вас действительно могут быть пользователи с учетными записями без лицензий или наоборот.</span><span class="sxs-lookup"><span data-stu-id="c14c7-p106">Which simply means that, yes, you can have users who have accounts but who don't have licenses. Or vice-versa.</span></span>
  
<span data-ttu-id="c14c7-p107">В статье [Просмотр лицензий и служб с помощью PowerShell в Office 365](view-licenses-and-services-with-office-365-powershell.md) описано, как определить количество приобретенных вашей организацией лицензий Office 365: и сколько из них назначены пользователям. Это важные сведения. Не менее важно знать, каким пользователям назначены лицензии, а каким  нет. Об этом также говорится в этой статье.</span><span class="sxs-lookup"><span data-stu-id="c14c7-p107">The article [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md) explains how you can determine the number of Office 365 licenses your organization has purchased as well as how many of those licenses have been assigned to users. That's important information. Equally important, however is knowing which of your users have been assigned these licenses and which ones haven't. And this article will tell you how to do just that.</span></span>
  
<span data-ttu-id="c14c7-p108">Как вам, вероятно, известно, командлет **Get-MsolUser** возвращает сведения обо всех учетных записях пользователей Office 365:. Необходимо быстро получить сведения обо всех пользователях Office 365:? В PowerShell в Office 365 выполните указанную ниже команду.</span><span class="sxs-lookup"><span data-stu-id="c14c7-p108">As you probably know, the **Get-MsolUser** cmdlet returns information about all your Office 365 user accounts. Need some quick info about all your Office 365 users? Then run this command in Office 365 PowerShell:</span></span>
  
```
Get-MsolUser
```

<span data-ttu-id="c14c7-135">В свою очередь командлет Get-MsolUser возвращает приведенные ниже данные.</span><span class="sxs-lookup"><span data-stu-id="c14c7-135">In turn, Get-MsolUser returns data similar to this:</span></span>
  
```
UserPrincipalName           DisplayName                     isLicensed
-----------------           -----------                     ----------
ZrinkaM@litwareinc.com      Zrinka Makovac                  True
BelindaN@litwareinc.com     Belinda Newman                  False
BonnieK@litwareinc.com      Bonnie Kearney                  True
FabriceC@litwareinc.com     Fabrice Canel                   True
AnneW@litwareinc.com        Anne Wallace                    True
AlexD@litwareinc.com        Alex Darrow                     True
```

<span data-ttu-id="c14c7-p109">Как видите, одно из возвращенных значений свойств предназначено для свойства **isLicensed**. Если свойство **isLicensed** имеет значение `False`, то это означает, что у пользователя нет лицензии на Office 365:. Другими словами, вы могли бы просто прокрутить список пользователей и выбрать пользователей, для которых свойство **isLicensed** имеет значение `False`.</span><span class="sxs-lookup"><span data-stu-id="c14c7-p109">As you can see, one of the property values returned is for the **isLicensed** property. If **isLicensed** is equal to `False` that means that the user doesn't have a license for Office 365. In other words, and if you wanted to, you could simply scroll through your list of users and pick out the ones where the **isLicensed** property is set to `False`.</span></span>
  
<span data-ttu-id="c14c7-p110">В любом случае, прокрутить список и выбрать нелицензированных пользователей можно, если имеется относительно небольшое количество пользователей. Однако при наличии большого числа пользователей это очень трудоемкая задача. (Кроме того, в зависимости от настроек Windows PowerShell выполнение этой задачи может оказаться невозможным, поскольку в Windows PowerShell существует ограничение относительно количества строк вывода, которые можно одновременно отобразить.)</span><span class="sxs-lookup"><span data-stu-id="c14c7-p110">At any rate, scrolling through a list of users trying to pick out the unlicensed users works as long as you have a relatively small number of users. If you have a large number of users, however, scrolling through that list will be, at best, extremely tedious. (And, depending on how Windows PowerShell has been configured, perhaps downright impossible. That's because there's a limit to the number of lines of output that can be displayed in the Windows PowerShell console at any one time.)</span></span>
  
<span data-ttu-id="c14c7-143">Поэтому намного лучший способ отобразить нелицензированных пользователей — выполнить такую команду:</span><span class="sxs-lookup"><span data-stu-id="c14c7-143">With that in mind, a much better way to list your unlicensed users is to run this command instead:</span></span>
  
```
Get-MsolUser -UnlicensedUsersOnly
```

<span data-ttu-id="c14c7-p111">Эта команда возвращает только пользователей, у которых нет лицензии на Office 365:. Другими словами:</span><span class="sxs-lookup"><span data-stu-id="c14c7-p111">That command returns only those users who don't have a license for Office 365. In other words:</span></span>
  
```
UserPrincipalName           DisplayName                     isLicensed
-----------------           -----------                     ----------
BelindaN@litwareinc.com     Belinda Newman                  False
```

<span data-ttu-id="c14c7-p112">Как вы видите, имеется один пользователь без лицензии. А что, если нам нужен список только  *лицензированных*  пользователей? Это немного сложнее:</span><span class="sxs-lookup"><span data-stu-id="c14c7-p112">As you can see we have one unlicensed user. And what is we only wanted a list of the  *licensed*  users? That's a tiny bit more complicated, but only the tiniest bit:</span></span>
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true}
```

<span data-ttu-id="c14c7-149">Эта команда ищет все учетные записи пользователей, для которых значение свойства **isLicensed** равно `True`, и возвращает примерно следующую информацию:</span><span class="sxs-lookup"><span data-stu-id="c14c7-149">That command, which looks for all the user accounts where the **isLicensed** property is equal to `True`, returns information similar to this:</span></span>
  
```
UserPrincipalName           DisplayName                     isLicensed
-----------------           -----------                     ----------
ZrinkaM@litwareinc.com      Zrinka Makovac                  True
BonnieK@litwareinc.com      Bonnie Kearney                  True
FabriceC@litwareinc.com     Fabrice Canel                   True
AnneW@litwareinc.com        Anne Wallace                    True
AlexD@litwareinc.com        Alex Darrow                     True
```

<span data-ttu-id="c14c7-p113">Как видите, сведения о пользователе Belinda Newman не возвращаются. Почему? Очень просто: для учетной записи этого пользователя значение свойства **isLicensed** не равно `True`.</span><span class="sxs-lookup"><span data-stu-id="c14c7-p113">As you can see, information is not returned for Belinda Newman. Why not? You got it: because the **isLicensed** property for Belinda's account is not set to `True`.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="c14c7-153">См. также</span><span class="sxs-lookup"><span data-stu-id="c14c7-153">See also</span></span>
<span data-ttu-id="c14c7-154"><a name="SeeAlso"> </a></span><span class="sxs-lookup"><span data-stu-id="c14c7-154"><a name="SeeAlso"> </a></span></span>

<span data-ttu-id="c14c7-155">Дополнительные сведения о командлетах, использованных в этих процедурах, см. в указанных ниже статьях.</span><span class="sxs-lookup"><span data-stu-id="c14c7-155">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="c14c7-156">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="c14c7-156">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691547)
    
- [<span data-ttu-id="c14c7-157">Where-Object</span><span class="sxs-lookup"><span data-stu-id="c14c7-157">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

