---
title: Office 365 PowerShell でライセンスとサービスを確認する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/17/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- O365ITProTrain
- LIL_Placement
- PowerShell
ms.assetid: bb5260a9-a6a3-4f34-b19a-06c6699f6723
description: Office 365 PowerShell を使ってライセンス プラン、サービス、Office 365 組織で利用可能なライセンスについての情報を確認する方法について説明します。
ms.openlocfilehash: 21dda5bfc1bf1fa975b4a94879435c1842c383ec
ms.sourcegitcommit: 8cacedcba4627042d4bd17f1a94fddcfd87f77b2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2018
ms.locfileid: "25601631"
---
# <a name="view-licenses-and-services-with-office-365-powershell"></a><span data-ttu-id="d9882-103">Office 365 PowerShell でライセンスとサービスを確認する</span><span class="sxs-lookup"><span data-stu-id="d9882-103">View licenses and services with Office 365 PowerShell</span></span>

<span data-ttu-id="d9882-104">**概要:** Office 365 PowerShell を使ってライセンス プラン、サービス、Office 365 組織で利用可能なライセンスについての情報を確認する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d9882-104">**Summary:** Explains how to use Office 365 PowerShell to view information about the licensing plans, services, and licenses that are available in your Office 365 organization.</span></span>
  
<span data-ttu-id="d9882-105">Office 365 サブスクリプションは、すべて以下の要素で構成されます。</span><span class="sxs-lookup"><span data-stu-id="d9882-105">Every Office 365 subscription consists of the following elements:</span></span>

- <span data-ttu-id="d9882-p101">**ライセンス プラン**ライセンス プランまたは Office 365 プランとも呼ばれます。ライセンス プランでは、ユーザーが利用可能な Office 365 サービスを定義します。Office 365 サブスクリプションには、複数のライセンス プランが含まれる場合があります。たとえば、Office 365 Enterprise E3 というライセンス プランがあります。</span><span class="sxs-lookup"><span data-stu-id="d9882-p101">**Licensing plans** These are also known aslicense plans or Office 365 plans. Licensing plans define the Office 365 services that are available to users. Your Office 365 subscription may contain multiple licensing plans. An example licensing plan would be Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="d9882-p102">**サービス**サービス プランとも呼ばれます。サービスとは、各ライセンス プランで利用可能な Office 365 製品および機能のことで、たとえば、Exchange Online や Office Professional Plus があります。ユーザーは、さまざまなサービスへのアクセスを許可するさまざまなライセンス プランから割り当てられた複数のライセンスを持つことができます。</span><span class="sxs-lookup"><span data-stu-id="d9882-p102">**Services** These are also known asservice plans. Services are the Office 365 products, features, and capabilities that are available in each licensing plan, for example, Exchange Online and Office Professional Plus. Users can have multiple licenses assigned to them from different licensing plans that grant access to different services.</span></span>
    
- <span data-ttu-id="d9882-p103">**ライセンス** すべてのライセンス プランには、購入した数のライセンスが含まれています。ライセンスをユーザーに割り当てると、ライセンス プランで定義した Office 365 サービスが使えるようになります。それぞれのユーザー アカウントに、少なくとも 1 つのライセンス プランからの 1 つのライセンスが必要です。これにより、ユーザーが Office 365 にログオンして、サービスを利用することができます。</span><span class="sxs-lookup"><span data-stu-id="d9882-p103">**Licenses** Each licensing plan contains the number of licenses that you purchased. You assign licenses to users so they can use the Office 365 services that are defined by the licensing plan. Every user account requires at least one license from one licensing plan so they can log on to Office 365 and use the services.</span></span>
    
<span data-ttu-id="d9882-p104">Office 365 PowerShell を使って、Office 365 組織で利用可能なライセンス プラン、ライセンス、およびサービスに関する詳細を確認することができます。別の Office 365 サブスクリプションで利用可能な製品、機能、サービスについての詳細は、「[Office 365 プランのオプション](https://go.microsoft.com/fwlink/p/?LinkId=691147)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d9882-p104">You can use Office 365 PowerShell to view details about the available licensing plans, licenses, and services in your Office 365 organization. For more information about the products, features, and services that are available in different Office 365 subscriptions, see [Office 365 Plan Options](https://go.microsoft.com/fwlink/p/?LinkId=691147).</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="d9882-118">はじめに</span><span class="sxs-lookup"><span data-stu-id="d9882-118">Before you begin</span></span>

- <span data-ttu-id="d9882-p105">このトピックの手順では、Office 365 PowerShell に接続する必要があります。手順については、「[Office 365 PowerShell への接続](connect-to-office-365-powershell.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d9882-p105">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="d9882-p106">このトピックで説明されている手順を自動化する PowerShell スクリプトが利用可能です。具体的に言うと、このスクリプトにより、Office 365 組織のサービス (Sway を含む) を表示し、無効化できます。詳細については、「[Office 365 PowerShell を使った Sway へのアクセスを無効にする](disable-access-to-sway-with-office-365-powershell.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="d9882-p106">A PowerShell script is available that automates the procedures described in this topic. Specifically, the script allows you to view and disable services in your Office 365 organization, including Sway. For more information, see [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span></span>
    
## <a name="view-information-about-licensing-plans-and-the-available-licenses"></a><span data-ttu-id="d9882-124">ライセンス プランと利用可能なライセンスに関する情報を確認する</span><span class="sxs-lookup"><span data-stu-id="d9882-124">View information about licensing plans and the available licenses</span></span>

<span data-ttu-id="d9882-125">現在のライセンス プランおよび各プランで利用可能なライセンスについての概要を確認するには、Office 365 PowerShell で以下のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="d9882-125">To view summary information about your current licensing plans and the available licenses for each plan, run the following command in Office 365 PowerShell:</span></span>
  
```
Get-MsolAccountSku
```

<span data-ttu-id="d9882-126">結果には次の情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="d9882-126">The results contain the following information:</span></span>
  
- <span data-ttu-id="d9882-p107">**AccountSkuId:** 構文 `<CompanyName>:<LicensingPlan>` を使用して、組織で利用可能なライセンス プランを表示します。_<CompanyName>_ は Office 365 に登録するときに指定した値で、組織に対して一意です。_<LicensingPlan>_ の値は、すべてのユーザーに対して同じです。たとえば、値 `litwareinc:ENTERPRISEPACK` では、会社名が `litwareinc`、ライセンス プラン名が `ENTERPRISEPACK` で、これが Office 365 Enterprise E3 のシステム名になります。</span><span class="sxs-lookup"><span data-stu-id="d9882-p107">**AccountSkuId:** Show the available licensing plans for your organization by using the syntax `<CompanyName>:<LicensingPlan>`.  _<CompanyName>_ is the value that you provided when you enrolled in Office 365, and is unique for your organization. The _<LicensingPlan>_ value is the same for everyone. For example, in the value `litwareinc:ENTERPRISEPACK`, the company name is  `litwareinc`, and the licensing plan name  `ENTERPRISEPACK`, which is the system name for Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="d9882-131">**ActiveUnits** 特定のライセンス プランで購入したライセンスの数。</span><span class="sxs-lookup"><span data-stu-id="d9882-131">**ActiveUnits:** Number of licenses that you've purchases for a specific licensing plan.</span></span>
    
- <span data-ttu-id="d9882-132">**WarningUnits:** 更新していないライセンス プランのライセンスの数。30 日の猶予期間を過ぎると有効期限切れになります。</span><span class="sxs-lookup"><span data-stu-id="d9882-132">**WarningUnits:** Number of licenses in a licensing plan that you haven't renewed, and that will expire after the 30-day grace period.</span></span>
    
- <span data-ttu-id="d9882-133">**ConsumedUnits:** 特定のライセンス プランでユーザーに割り当てたライセンスの数。</span><span class="sxs-lookup"><span data-stu-id="d9882-133">**ConsumedUnits:** Number of licenses that you've assigned to users from a specific licensing plan.</span></span>
    
<span data-ttu-id="d9882-134">すべてのライセンス プランで利用できる Office 365 サービスの詳細を参照するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="d9882-134">To view details about the Office 365 services that are available in all of your license plans, run the following command:</span></span>
  
```
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

<span data-ttu-id="d9882-p108">次の表は、Office 365 のサービス プランと、最も一般的なサービスのフレンドリ名を示します。サービス プランの一覧は、異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="d9882-p108">The following table shows the Office 365 service plans and their friendly names for the most common services. Your list of service plans might be different.</span></span> 
  
|<span data-ttu-id="d9882-137">**サービス プラン**</span><span class="sxs-lookup"><span data-stu-id="d9882-137">**Service plan**</span></span>|<span data-ttu-id="d9882-138">**説明**</span><span class="sxs-lookup"><span data-stu-id="d9882-138">**Description**</span></span>|
|:-----|:-----|
| `SWAY` <br/> |<span data-ttu-id="d9882-139">Sway</span><span class="sxs-lookup"><span data-stu-id="d9882-139">Sway</span></span>  <br/> |
| `TEAMS1` <br/> |<span data-ttu-id="d9882-140">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="d9882-140">Microsoft Teams</span></span>  <br/> |
| `YAMMER_ENTERPRISE` <br/> |<span data-ttu-id="d9882-141">Yammer</span><span class="sxs-lookup"><span data-stu-id="d9882-141">Yammer</span></span>  <br/> |
| `RMS_S_ENTERPRISE` <br/> |<span data-ttu-id="d9882-142">Azure Rights Management (RMS)</span><span class="sxs-lookup"><span data-stu-id="d9882-142">Azure Rights Management (RMS)</span></span>  <br/> |
| `OFFICESUBSCRIPTION` <br/> |<span data-ttu-id="d9882-143">Office Professional Plus</span><span class="sxs-lookup"><span data-stu-id="d9882-143">Office Professional Plus</span></span>  <br/> |
| `MCOSTANDARD` <br/> |<span data-ttu-id="d9882-144">Skype for Business Online</span><span class="sxs-lookup"><span data-stu-id="d9882-144">Skype for Business Online</span></span>  <br/> |
| `SHAREPOINTWAC` <br/> |<span data-ttu-id="d9882-145">Office Online</span><span class="sxs-lookup"><span data-stu-id="d9882-145">Office Online</span></span>  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |<span data-ttu-id="d9882-146">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="d9882-146">SharePoint Online</span></span>  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |<span data-ttu-id="d9882-147">Exchange Online プラン 2</span><span class="sxs-lookup"><span data-stu-id="d9882-147">Exchange Online Plan 2</span></span>  <br/> |
   
<span data-ttu-id="d9882-148">ライセンス プラン (製品の名前とも呼ばれます) が含まれているサービス プラン、および対応するフレンドリ名の一覧については、[製品の名前とライセンスのサービス プランの識別子](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d9882-148">For a complete list of license plans (also known as product names), their included service plans, and their corresponding friendly names, see [Product names and service plan identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span></span>

<span data-ttu-id="d9882-149">特定のライセンス プランで利用可能な Office 365 サービスの詳細を確認するには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="d9882-149">To view details about the Office 365 services that are available in a specific licensing plan, use the following syntax.</span></span>
  
```
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "<AccountSkuId>"}).ServiceStatus
```

<span data-ttu-id="d9882-150">この例では、litwareinc:ENTERPRISEPACK (Office 365 エンタープライズ E3) ライセンス プランで利用可能な Office 365 サービスを使用します。</span><span class="sxs-lookup"><span data-stu-id="d9882-150">This example shows the Office 365 services that are available in the litwareinc:ENTERPRISEPACK (Office 365 Enterprise E3) licensing plan.</span></span>
  
```
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "litwareinc:ENTERPRISEPACK"}).ServiceStatus
```

## <a name="new-to-office-365"></a><span data-ttu-id="d9882-151">Office 365 を初めて使用する場合</span><span class="sxs-lookup"><span data-stu-id="d9882-151">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   
## <a name="see-also"></a><span data-ttu-id="d9882-152">関連項目</span><span class="sxs-lookup"><span data-stu-id="d9882-152">See also</span></span>

- [<span data-ttu-id="d9882-153">ライセンスのあるユーザーとライセンスのないユーザーを Office 365 PowerShell で表示する</span><span class="sxs-lookup"><span data-stu-id="d9882-153">View licensed and unlicensed users with Office 365 PowerShell</span></span>](view-licensed-and-unlicensed-users-with-office-365-powershell.md)
- [<span data-ttu-id="d9882-154">Office 365 PowerShell を使用してアカウントのライセンスとサービスの詳細を表示する</span><span class="sxs-lookup"><span data-stu-id="d9882-154">View account license and service details with Office 365 PowerShell</span></span>](view-account-license-and-service-details-with-office-365-powershell.md)
- [<span data-ttu-id="d9882-155">Get-MsolAccountSku</span><span class="sxs-lookup"><span data-stu-id="d9882-155">Get-MsolAccountSku</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691549)

