---
title: Записи DNS для Office 365 GCC High
ms.author: dzazzo
author: dzazzo
manager: dzazzo
ms.date: 05/19/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- OGA150
- OGC150
- OGD150
- MOE150
ms.assetid: ''
description: 'Сводка: записи DNS для Office 365 GCC High'
hideEdit: true
ms.openlocfilehash: 9bcaa71ab965f01481887d50a3e6ddbbbe3fadee
ms.sourcegitcommit: 576c3dbdef535f952a861197dea5348908da9504
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/09/2020
ms.locfileid: "44339806"
---
# <a name="dns-records-for-office-365-gcc-high"></a><span data-ttu-id="45301-103">Записи DNS для Office 365 GCC High</span><span class="sxs-lookup"><span data-stu-id="45301-103">DNS records for Office 365 GCC High</span></span>

<span data-ttu-id="45301-104">*Эта статья относится к пакету Office 365 GCC High и Microsoft 365 GCC High*</span><span class="sxs-lookup"><span data-stu-id="45301-104">*This article applies to Office 365 GCC High and Microsoft 365 GCC High*</span></span>

<span data-ttu-id="45301-105">В процессе входящей миграции в Office 365 GCC High необходимо добавить домены SMTP и SIP в клиент Интернет-служб.</span><span class="sxs-lookup"><span data-stu-id="45301-105">As part of onboarding to Office 365 GCC High, you will need to add your SMTP and SIP domains to your Online Services tenant.</span></span>  <span data-ttu-id="45301-106">Это можно сделать с помощью командлета New – Мсолдомаин в Azure AD PowerShell или на [портале для государственных учреждений Azure](https://portal.azure.us) , чтобы начать процесс добавления домена и подтверждения владения.</span><span class="sxs-lookup"><span data-stu-id="45301-106">You’ll do this using the New-MsolDomain cmdlet in Azure AD PowerShell or use the [Azure Government Portal](https://portal.azure.us) to start the process of adding the domain and proving ownership.</span></span>

<span data-ttu-id="45301-107">После добавления доменов к клиенту и проверки подлинности добавьте соответствующие записи DNS для служб ниже, следуя приведенным ниже рекомендациям.</span><span class="sxs-lookup"><span data-stu-id="45301-107">Once you have your domains added to your tenant and validated, use the following guidance to add the appropriate DNS records for the services below.</span></span>  <span data-ttu-id="45301-108">Возможно, вам потребуется изменить приведенную ниже таблицу в соответствии с потребностями Организации относительно входящих записей MX и всех имеющихся записей автообнаружения Exchange.</span><span class="sxs-lookup"><span data-stu-id="45301-108">You may need to modify the below table to fit your organization’s needs with respect to the inbound MX record(s) and any existing Exchange Autodiscover record(s) you have in place.</span></span>  <span data-ttu-id="45301-109">Мы настоятельно рекомендуем координировать эти записи DNS с помощью команды обмена сообщениями, чтобы избежать каких-либо непростостей или неправильной доставки электронной почты.</span><span class="sxs-lookup"><span data-stu-id="45301-109">We strongly recommend coordinating these DNS records with your messaging team to avoid any outages or mis-delivery of email.</span></span>

## <a name="exchange-online"></a><span data-ttu-id="45301-110">Exchange Online</span><span class="sxs-lookup"><span data-stu-id="45301-110">Exchange Online</span></span>

| <span data-ttu-id="45301-111">Type (Тип)</span><span class="sxs-lookup"><span data-stu-id="45301-111">Type</span></span> | <span data-ttu-id="45301-112">Priority (Приоритет)</span><span class="sxs-lookup"><span data-stu-id="45301-112">Priority</span></span> | <span data-ttu-id="45301-113">Имя узла</span><span class="sxs-lookup"><span data-stu-id="45301-113">Host name</span></span> | <span data-ttu-id="45301-114">Указывает на адрес или значение</span><span class="sxs-lookup"><span data-stu-id="45301-114">Points to address or value</span></span> | <span data-ttu-id="45301-115">TTL</span><span class="sxs-lookup"><span data-stu-id="45301-115">TTL</span></span> |
| --- | --- | --- | --- | --- |
| <span data-ttu-id="45301-116">MX</span><span class="sxs-lookup"><span data-stu-id="45301-116">MX</span></span> | <span data-ttu-id="45301-117">нуль</span><span class="sxs-lookup"><span data-stu-id="45301-117">0</span></span> | @ | <span data-ttu-id="45301-118">*клиент*. mail.Protection.Office365.US (Дополнительные сведения см. ниже)</span><span class="sxs-lookup"><span data-stu-id="45301-118">*tenant*.mail.protection.office365.us (see below for additional details)</span></span> | <span data-ttu-id="45301-119">1 Hour</span><span class="sxs-lookup"><span data-stu-id="45301-119">1 Hour</span></span> |
| <span data-ttu-id="45301-120">TXT</span><span class="sxs-lookup"><span data-stu-id="45301-120">TXT</span></span> | - | @ | <span data-ttu-id="45301-121">v = spf1 включение:SPF. Protection. Office365. US — ALL</span><span class="sxs-lookup"><span data-stu-id="45301-121">v=spf1 include:spf.protection.office365.us -all</span></span> | <span data-ttu-id="45301-122">1 Hour</span><span class="sxs-lookup"><span data-stu-id="45301-122">1 Hour</span></span> |
| <span data-ttu-id="45301-123">CNAME</span><span class="sxs-lookup"><span data-stu-id="45301-123">CNAME</span></span> | - | <span data-ttu-id="45301-124">autodiscover</span><span class="sxs-lookup"><span data-stu-id="45301-124">autodiscover</span></span> | <span data-ttu-id="45301-125">autodiscover.office365.us</span><span class="sxs-lookup"><span data-stu-id="45301-125">autodiscover.office365.us</span></span> | <span data-ttu-id="45301-126">1 Hour</span><span class="sxs-lookup"><span data-stu-id="45301-126">1 Hour</span></span> |

### <a name="exchange-autodiscover-record"></a><span data-ttu-id="45301-127">Запись автообнаружения Exchange</span><span class="sxs-lookup"><span data-stu-id="45301-127">Exchange Autodiscover record</span></span>

<span data-ttu-id="45301-128">При наличии локального сервера Exchange Server мы рекомендуем оставить существующую запись на месте во время миграции в Exchange Online и обновить эту запись после завершения миграции.</span><span class="sxs-lookup"><span data-stu-id="45301-128">If you have Exchange Server on-premises, we recommend leaving your existing record in place while you migrate to Exchange Online, and update that record once you have completed your migration.</span></span> 

### <a name="exchange-online-mx-record"></a><span data-ttu-id="45301-129">Запись MX Exchange Online</span><span class="sxs-lookup"><span data-stu-id="45301-129">Exchange Online MX Record</span></span>

<span data-ttu-id="45301-130">Значение записи MX для обслуживаемых доменов соответствует стандартному формату, как указано выше: *клиент*. mail.Protection.Office365.US, заменяя *клиент* первой частью имени клиента по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="45301-130">The MX record value for your accepted domains follows a standard format as noted above: *tenant*.mail.protection.office365.us, replacing *tenant* with the first part of your default tenant name.</span></span>

<span data-ttu-id="45301-131">Например, если имя клиента — contoso.onmicrosoft.us, вы бы использовали **contoso.mail.Protection.Office365.US** в качестве значения для записи MX.</span><span class="sxs-lookup"><span data-stu-id="45301-131">For example, if your tenant name is contoso.onmicrosoft.us, you’d use **contoso.mail.protection.office365.us** as the value for your MX record.</span></span>

## <a name="skype-for-business-online"></a><span data-ttu-id="45301-132">Skype для бизнеса Online</span><span class="sxs-lookup"><span data-stu-id="45301-132">Skype for Business Online</span></span>

### <a name="cname-records"></a><span data-ttu-id="45301-133">Записи CNAME</span><span class="sxs-lookup"><span data-stu-id="45301-133">CNAME records</span></span>

| <span data-ttu-id="45301-134">Тип</span><span class="sxs-lookup"><span data-stu-id="45301-134">Type</span></span> | <span data-ttu-id="45301-135">Имя узла</span><span class="sxs-lookup"><span data-stu-id="45301-135">Host name</span></span> | <span data-ttu-id="45301-136">Указывает на адрес или значение</span><span class="sxs-lookup"><span data-stu-id="45301-136">Points to address or value</span></span> | <span data-ttu-id="45301-137">TTL</span><span class="sxs-lookup"><span data-stu-id="45301-137">TTL</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="45301-138">CNAME</span><span class="sxs-lookup"><span data-stu-id="45301-138">CNAME</span></span> | <span data-ttu-id="45301-139">sip</span><span class="sxs-lookup"><span data-stu-id="45301-139">sip</span></span> | <span data-ttu-id="45301-140">sipdir.online.gov.skypeforbusiness.us</span><span class="sxs-lookup"><span data-stu-id="45301-140">sipdir.online.gov.skypeforbusiness.us</span></span> | <span data-ttu-id="45301-141">1 Hour</span><span class="sxs-lookup"><span data-stu-id="45301-141">1 Hour</span></span> |
| <span data-ttu-id="45301-142">CNAME</span><span class="sxs-lookup"><span data-stu-id="45301-142">CNAME</span></span> | <span data-ttu-id="45301-143">lyncdiscover</span><span class="sxs-lookup"><span data-stu-id="45301-143">lyncdiscover</span></span> | <span data-ttu-id="45301-144">webdir.online.gov.skypeforbusiness.us</span><span class="sxs-lookup"><span data-stu-id="45301-144">webdir.online.gov.skypeforbusiness.us</span></span> | <span data-ttu-id="45301-145">1 Hour</span><span class="sxs-lookup"><span data-stu-id="45301-145">1 Hour</span></span> |

### <a name="srv-records"></a><span data-ttu-id="45301-146">Записи SRV</span><span class="sxs-lookup"><span data-stu-id="45301-146">SRV records</span></span>

| <span data-ttu-id="45301-147">Тип</span><span class="sxs-lookup"><span data-stu-id="45301-147">Type</span></span> | <span data-ttu-id="45301-148">Служба</span><span class="sxs-lookup"><span data-stu-id="45301-148">Service</span></span> | <span data-ttu-id="45301-149">Протокол</span><span class="sxs-lookup"><span data-stu-id="45301-149">Protocol</span></span> | <span data-ttu-id="45301-150">Порт</span><span class="sxs-lookup"><span data-stu-id="45301-150">Port</span></span> | <span data-ttu-id="45301-151">Насыщенность</span><span class="sxs-lookup"><span data-stu-id="45301-151">Weight</span></span> | <span data-ttu-id="45301-152">Priority</span><span class="sxs-lookup"><span data-stu-id="45301-152">Priority</span></span> | <span data-ttu-id="45301-153">Имя</span><span class="sxs-lookup"><span data-stu-id="45301-153">Name</span></span> | <span data-ttu-id="45301-154">Target</span><span class="sxs-lookup"><span data-stu-id="45301-154">Target</span></span> | <span data-ttu-id="45301-155">TTL</span><span class="sxs-lookup"><span data-stu-id="45301-155">TTL</span></span> |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| <span data-ttu-id="45301-156">SRV</span><span class="sxs-lookup"><span data-stu-id="45301-156">SRV</span></span> | <span data-ttu-id="45301-157">\_sip</span><span class="sxs-lookup"><span data-stu-id="45301-157">\_sip</span></span> | <span data-ttu-id="45301-158">\_аутентифицирован</span><span class="sxs-lookup"><span data-stu-id="45301-158">\_tls</span></span> | <span data-ttu-id="45301-159">443</span><span class="sxs-lookup"><span data-stu-id="45301-159">443</span></span> | <span data-ttu-id="45301-160">1 </span><span class="sxs-lookup"><span data-stu-id="45301-160">1</span></span> | <span data-ttu-id="45301-161">100</span><span class="sxs-lookup"><span data-stu-id="45301-161">100</span></span> | @ | <span data-ttu-id="45301-162">sipdir.online.gov.skypeforbusiness.us</span><span class="sxs-lookup"><span data-stu-id="45301-162">sipdir.online.gov.skypeforbusiness.us</span></span> | <span data-ttu-id="45301-163">1 час</span><span class="sxs-lookup"><span data-stu-id="45301-163">1 Hour</span></span> |
| <span data-ttu-id="45301-164">SRV</span><span class="sxs-lookup"><span data-stu-id="45301-164">SRV</span></span> | <span data-ttu-id="45301-165">\_сипфедератионтлс</span><span class="sxs-lookup"><span data-stu-id="45301-165">\_sipfederationtls</span></span> | <span data-ttu-id="45301-166">\_семейства</span><span class="sxs-lookup"><span data-stu-id="45301-166">\_tcp</span></span> | <span data-ttu-id="45301-167">5061</span><span class="sxs-lookup"><span data-stu-id="45301-167">5061</span></span> | <span data-ttu-id="45301-168">1 </span><span class="sxs-lookup"><span data-stu-id="45301-168">1</span></span> | <span data-ttu-id="45301-169">100</span><span class="sxs-lookup"><span data-stu-id="45301-169">100</span></span> | @ | <span data-ttu-id="45301-170">sipfed.online.gov.skypeforbusiness.us</span><span class="sxs-lookup"><span data-stu-id="45301-170">sipfed.online.gov.skypeforbusiness.us</span></span> | <span data-ttu-id="45301-171">1 Hour</span><span class="sxs-lookup"><span data-stu-id="45301-171">1 Hour</span></span> |

## <a name="additional-dns-records"></a><span data-ttu-id="45301-172">Дополнительные записи DNS</span><span class="sxs-lookup"><span data-stu-id="45301-172">Additional DNS records</span></span>

> [!IMPORTANT]
> <span data-ttu-id="45301-173">Если у вас есть запись CNAME *msoID* в зоне DNS, в настоящее время необходимо **Удалить** эту запись из DNS.</span><span class="sxs-lookup"><span data-stu-id="45301-173">If you have an existing *msoid* CNAME record in your DNS zone, you must **remove** the record from DNS at this time.</span></span>  <span data-ttu-id="45301-174">Запись msoID несовместима с Microsoft 365 Enterprise Apps *(прежнее название — Office 365 профессиональный плюс)* и не позволит выполнить активацию.</span><span class="sxs-lookup"><span data-stu-id="45301-174">The msoid record is incompatible with Microsoft 365 Enterprise Apps *(formerly Office 365 ProPlus)* and will prevent activation from succeeding.</span></span>
