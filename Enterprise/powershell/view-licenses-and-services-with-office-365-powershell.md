---
title: Office 365 PowerShell でライセンスとサービスを確認する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/03/2019
audience: Admin
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
ms.openlocfilehash: 8ee2c834063ea80388662c1f36f4524715f98a58
ms.sourcegitcommit: f316aef1c122f8eb25c43a56bc894c4aa61c8e0c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2019
ms.locfileid: "38747456"
---
# <a name="view-licenses-and-services-with-office-365-powershell"></a><span data-ttu-id="ac917-103">Office 365 PowerShell でライセンスとサービスを確認する</span><span class="sxs-lookup"><span data-stu-id="ac917-103">View licenses and services with Office 365 PowerShell</span></span>

<span data-ttu-id="ac917-104">Office 365 サブスクリプションは、すべて以下の要素で構成されます。</span><span class="sxs-lookup"><span data-stu-id="ac917-104">Every Office 365 subscription consists of the following elements:</span></span>

- <span data-ttu-id="ac917-105">**ライセンスプラン**これらは、ライセンスプランまたは Office 365 プランとも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="ac917-105">**Licensing plans** These are also known as license plans or Office 365 plans.</span></span> <span data-ttu-id="ac917-106">ライセンス プランでは、ユーザーが利用可能な Office 365 サービスを定義します。</span><span class="sxs-lookup"><span data-stu-id="ac917-106">Licensing plans define the Office 365 services that are available to users.</span></span> <span data-ttu-id="ac917-107">Office 365 サブスクリプションには、複数のライセンス プランが含まれる場合があります。</span><span class="sxs-lookup"><span data-stu-id="ac917-107">Your Office 365 subscription may contain multiple licensing plans.</span></span> <span data-ttu-id="ac917-108">たとえば、Office 365 Enterprise E3 というライセンス プランがあります。</span><span class="sxs-lookup"><span data-stu-id="ac917-108">An example licensing plan would be Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="ac917-109">**サービス**これらはサービスプランとも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="ac917-109">**Services** These are also known as service plans.</span></span> <span data-ttu-id="ac917-110">サービスとは、各ライセンス プランで利用可能な Office 365 製品および機能のことで、たとえば、Exchange Online や Office Professional Plus があります。</span><span class="sxs-lookup"><span data-stu-id="ac917-110">Services are the Office 365 products, features, and capabilities that are available in each licensing plan, for example, Exchange Online and Office Professional Plus.</span></span> <span data-ttu-id="ac917-111">ユーザーは、さまざまなサービスへのアクセスを許可するさまざまなライセンス プランから割り当てられた複数のライセンスを持つことができます。</span><span class="sxs-lookup"><span data-stu-id="ac917-111">Users can have multiple licenses assigned to them from different licensing plans that grant access to different services.</span></span>
    
- <span data-ttu-id="ac917-p103">**ライセンス** すべてのライセンス プランには、購入した数のライセンスが含まれています。ライセンスをユーザーに割り当てると、ライセンス プランで定義した Office 365 サービスが使えるようになります。それぞれのユーザー アカウントに、少なくとも 1 つのライセンス プランからの 1 つのライセンスが必要です。これにより、ユーザーが Office 365 にログオンして、サービスを利用することができます。</span><span class="sxs-lookup"><span data-stu-id="ac917-p103">**Licenses** Each licensing plan contains the number of licenses that you purchased. You assign licenses to users so they can use the Office 365 services that are defined by the licensing plan. Every user account requires at least one license from one licensing plan so they can log on to Office 365 and use the services.</span></span>
    
<span data-ttu-id="ac917-p104">Office 365 PowerShell を使って、Office 365 組織で利用可能なライセンス プラン、ライセンス、およびサービスに関する詳細を確認することができます。別の Office 365 サブスクリプションで利用可能な製品、機能、サービスについての詳細は、「[Office 365 プランのオプション](https://go.microsoft.com/fwlink/p/?LinkId=691147)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ac917-p104">You can use Office 365 PowerShell to view details about the available licensing plans, licenses, and services in your Office 365 organization. For more information about the products, features, and services that are available in different Office 365 subscriptions, see [Office 365 Plan Options](https://go.microsoft.com/fwlink/p/?LinkId=691147).</span></span>


## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="ac917-117">Graph モジュールの Azure Active Directory PowerShell を使用する</span><span class="sxs-lookup"><span data-stu-id="ac917-117">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="ac917-118">まず、[Office 365 テナントに接続します](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。</span><span class="sxs-lookup"><span data-stu-id="ac917-118">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  
<span data-ttu-id="ac917-119">現在のライセンスプランおよび各プランで使用可能なライセンスに関する概要情報を表示するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="ac917-119">To view summary information about your current licensing plans and the available licenses for each plan, run the following command:</span></span>
  
```powershell
Get-AzureADSubscribedSku | Select -Property Sku*,ConsumedUnits -ExpandProperty PrepaidUnits
```

<span data-ttu-id="ac917-120">結果には次の情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="ac917-120">The results contain the following information:</span></span>
  
- <span data-ttu-id="ac917-121">**Skupartnumber:** 組織の利用可能なライセンスプランを表示します。</span><span class="sxs-lookup"><span data-stu-id="ac917-121">**SkuPartNumber:** Shows the available licensing plans for your organization.</span></span> <span data-ttu-id="ac917-122">たとえば、 `ENTERPRISEPACK`は Office 365 Enterprise E3 のライセンスプラン名です。</span><span class="sxs-lookup"><span data-stu-id="ac917-122">For example, `ENTERPRISEPACK` is the license plan name for Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="ac917-123">**有効:** 特定のライセンスプランで購入したライセンスの数。</span><span class="sxs-lookup"><span data-stu-id="ac917-123">**Enabled:** Number of licenses that you've purchased for a specific licensing plan.</span></span>
    
- <span data-ttu-id="ac917-124">**ConsumedUnits:** 特定のライセンス プランでユーザーに割り当てたライセンスの数。</span><span class="sxs-lookup"><span data-stu-id="ac917-124">**ConsumedUnits:** Number of licenses that you've assigned to users from a specific licensing plan.</span></span>
    
<span data-ttu-id="ac917-125">すべてのライセンスプランで利用可能な Office 365 サービスの詳細を表示するには、最初にライセンスプランの一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="ac917-125">To view details about the Office 365 services that are available in all of your license plans, first display a list of your license plans.</span></span>

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="ac917-126">次に、ライセンスプラン情報を変数に格納します。</span><span class="sxs-lookup"><span data-stu-id="ac917-126">Next, store the license plans information in a variable.</span></span>

```powershell
$licenses = Get-AzureADSubscribedSku
```

<span data-ttu-id="ac917-127">次に、特定のライセンスプランでサービスを表示します。</span><span class="sxs-lookup"><span data-stu-id="ac917-127">Next, display the services in a specific license plan.</span></span>

```powershell
$licenses[<index>].ServicePlans
```

<span data-ttu-id="ac917-128">\<index> は、 `Get-AzureADSubscribedSku | Select SkuPartNumber`コマンドの表示からライセンスプランの行番号を指定する整数値から1を引いた値です。</span><span class="sxs-lookup"><span data-stu-id="ac917-128">\<index> is an integer that specifies the row number of the license plan from the display of the `Get-AzureADSubscribedSku | Select SkuPartNumber` command, minus 1.</span></span>

<span data-ttu-id="ac917-129">たとえば、 `Get-AzureADSubscribedSku | Select SkuPartNumber`コマンドの表示は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="ac917-129">For example, if the display of the `Get-AzureADSubscribedSku | Select SkuPartNumber` command is this:</span></span>

```powershell
SkuPartNumber
-------------
WIN10_VDA_E5
EMSPREMIUM
ENTERPRISEPREMIUM
FLOW_FREE
```

<span data-ttu-id="ac917-130">次に、ENTERPRISEPREMIUM ライセンスプランのサービスを表示するコマンドは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="ac917-130">Then the command to display the services for the ENTERPRISEPREMIUM license plan is this:</span></span>

```powershell
$licenses[2].ServicePlans
```

<span data-ttu-id="ac917-131">ENTERPRISEPREMIUM は3番目の行です。</span><span class="sxs-lookup"><span data-stu-id="ac917-131">ENTERPRISEPREMIUM is the third row.</span></span> <span data-ttu-id="ac917-132">したがって、インデックス値は (3-1) または2です。</span><span class="sxs-lookup"><span data-stu-id="ac917-132">Therefore, the index value is (3 - 1), or 2.</span></span>

<span data-ttu-id="ac917-133">ライセンスプランの完全な一覧 (製品名とも呼ばれます)、含まれるサービスプラン、およびそれに対応するフレンドリ名については、「[ライセンスの製品名とサービスプラン識別子](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ac917-133">For a complete list of license plans (also known as product names), their included service plans, and their corresponding friendly names, see [Product names and service plan identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span></span>

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="ac917-134">Windows PowerShell の Microsoft Azure Active Directory モジュールを使用する</span><span class="sxs-lookup"><span data-stu-id="ac917-134">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="ac917-135">まず、[Office 365 テナントに接続します](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="ac917-135">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

>[!Note]
><span data-ttu-id="ac917-136">このトピックで説明されている手順を自動化する PowerShell スクリプトが利用可能です。</span><span class="sxs-lookup"><span data-stu-id="ac917-136">A PowerShell script is available that automates the procedures described in this topic.</span></span> <span data-ttu-id="ac917-137">具体的には、このスクリプトを使用すると、Sway などの Office 365 組織のサービスを表示したり、無効にしたりできます。</span><span class="sxs-lookup"><span data-stu-id="ac917-137">Specifically, the script lets you view and disable services in your Office 365 organization, including Sway.</span></span> <span data-ttu-id="ac917-138">詳細については、「[Office 365 PowerShell を使った Sway へのアクセスを無効にする](disable-access-to-sway-with-office-365-powershell.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ac917-138">For more information, see [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span></span>
>
    
<span data-ttu-id="ac917-139">現在のライセンスプランおよび各プランで使用可能なライセンスに関する概要情報を表示するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="ac917-139">To view summary information about your current licensing plans and the available licenses for each plan, run the following command:</span></span>
  
```powershell
Get-MsolAccountSku
```

<span data-ttu-id="ac917-140">結果には次の情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="ac917-140">The results contain the following information:</span></span>
  
- <span data-ttu-id="ac917-p108">**AccountSkuId:** 構文 `<CompanyName>:<LicensingPlan>` を使用して、組織で利用可能なライセンス プランを表示します。_<CompanyName>_ は Office 365 に登録するときに指定した値で、組織に対して一意です。_<LicensingPlan>_ の値は、すべてのユーザーに対して同じです。たとえば、値 `litwareinc:ENTERPRISEPACK` では、会社名が `litwareinc`、ライセンス プラン名が `ENTERPRISEPACK` で、これが Office 365 Enterprise E3 のシステム名になります。</span><span class="sxs-lookup"><span data-stu-id="ac917-p108">**AccountSkuId:** Show the available licensing plans for your organization by using the syntax `<CompanyName>:<LicensingPlan>`.  _<CompanyName>_ is the value that you provided when you enrolled in Office 365, and is unique for your organization. The _<LicensingPlan>_ value is the same for everyone. For example, in the value `litwareinc:ENTERPRISEPACK`, the company name is  `litwareinc`, and the licensing plan name  `ENTERPRISEPACK`, which is the system name for Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="ac917-145">**Activeunits:** 特定のライセンスプランで購入したライセンスの数。</span><span class="sxs-lookup"><span data-stu-id="ac917-145">**ActiveUnits:** Number of licenses that you've purchased for a specific licensing plan.</span></span>
    
- <span data-ttu-id="ac917-146">**WarningUnits:** 更新していないライセンス プランのライセンスの数。30 日の猶予期間を過ぎると有効期限切れになります。</span><span class="sxs-lookup"><span data-stu-id="ac917-146">**WarningUnits:** Number of licenses in a licensing plan that you haven't renewed, and that will expire after the 30-day grace period.</span></span>
    
- <span data-ttu-id="ac917-147">**ConsumedUnits:** 特定のライセンス プランでユーザーに割り当てたライセンスの数。</span><span class="sxs-lookup"><span data-stu-id="ac917-147">**ConsumedUnits:** Number of licenses that you've assigned to users from a specific licensing plan.</span></span>
    
<span data-ttu-id="ac917-148">すべてのライセンス プランで利用できる Office 365 サービスの詳細を参照するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="ac917-148">To view details about the Office 365 services that are available in all of your license plans, run the following command:</span></span>
  
```powershell
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

<span data-ttu-id="ac917-149">次の表は、Office 365 のサービス プランと最も一般的なサービスのフレンドリ名を示します。</span><span class="sxs-lookup"><span data-stu-id="ac917-149">The following table shows the Office 365 service plans and their friendly names for the most common services.</span></span> <span data-ttu-id="ac917-150">実際のサービス プランの一覧とは、異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="ac917-150">Your list of service plans might be different.</span></span> 
  
|<span data-ttu-id="ac917-151">**サービス プラン**</span><span class="sxs-lookup"><span data-stu-id="ac917-151">**Service plan**</span></span>|<span data-ttu-id="ac917-152">**説明**</span><span class="sxs-lookup"><span data-stu-id="ac917-152">**Description**</span></span>|
|:-----|:-----|
| `SWAY` <br/> |<span data-ttu-id="ac917-153">Sway</span><span class="sxs-lookup"><span data-stu-id="ac917-153">Sway</span></span>  <br/> |
| `TEAMS1` <br/> |<span data-ttu-id="ac917-154">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="ac917-154">Microsoft Teams</span></span>  <br/> |
| `YAMMER_ENTERPRISE` <br/> |<span data-ttu-id="ac917-155">Yammer</span><span class="sxs-lookup"><span data-stu-id="ac917-155">Yammer</span></span>  <br/> |
| `RMS_S_ENTERPRISE` <br/> |<span data-ttu-id="ac917-156">Azure Rights Management (RMS)</span><span class="sxs-lookup"><span data-stu-id="ac917-156">Azure Rights Management (RMS)</span></span>  <br/> |
| `OFFICESUBSCRIPTION` <br/> |<span data-ttu-id="ac917-157">Office Professional Plus</span><span class="sxs-lookup"><span data-stu-id="ac917-157">Office Professional Plus</span></span>  <br/> |
| `MCOSTANDARD` <br/> |<span data-ttu-id="ac917-158">Skype for Business Online</span><span class="sxs-lookup"><span data-stu-id="ac917-158">Skype for Business Online</span></span>  <br/> |
| `SHAREPOINTWAC` <br/> |<span data-ttu-id="ac917-159">事業所</span><span class="sxs-lookup"><span data-stu-id="ac917-159">Office</span></span>  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |<span data-ttu-id="ac917-160">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="ac917-160">SharePoint Online</span></span>  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |<span data-ttu-id="ac917-161">Exchange Online プラン 2</span><span class="sxs-lookup"><span data-stu-id="ac917-161">Exchange Online Plan 2</span></span>  <br/> |
   
<span data-ttu-id="ac917-162">ライセンスプランの完全な一覧 (製品名とも呼ばれます)、含まれるサービスプラン、およびそれに対応するフレンドリ名については、「[ライセンスの製品名とサービスプラン識別子](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ac917-162">For a complete list of license plans (also known as product names), their included service plans, and their corresponding friendly names, see [Product names and service plan identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span></span>

<span data-ttu-id="ac917-163">特定のライセンス プランで利用可能な Office 365 サービスの詳細を確認するには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="ac917-163">To view details about the Office 365 services that are available in a specific licensing plan, use the following syntax.</span></span>
  
```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "<AccountSkuId>"}).ServiceStatus
```

<span data-ttu-id="ac917-164">この例は、litwareinc: ENTERPRISEPACK (Office 365 Enterprise E3) ライセンスプランで利用可能な Office 365 サービスを示しています。</span><span class="sxs-lookup"><span data-stu-id="ac917-164">This example shows the Office 365 services that are available in the litwareinc:ENTERPRISEPACK (Office 365 Enterprise E3) licensing plan.</span></span>
  
```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "litwareinc:ENTERPRISEPACK"}).ServiceStatus
```


## <a name="new-to-office-365"></a><span data-ttu-id="ac917-165">Office 365 を初めて使用する場合</span><span class="sxs-lookup"><span data-stu-id="ac917-165">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   
## <a name="see-also"></a><span data-ttu-id="ac917-166">関連項目</span><span class="sxs-lookup"><span data-stu-id="ac917-166">See also</span></span>

[<span data-ttu-id="ac917-167">Office 365 PowerShell を使ってユーザー アカウントとライセンスを管理します。</span><span class="sxs-lookup"><span data-stu-id="ac917-167">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="ac917-168">Office 365 PowerShell による Office 365 の管理</span><span class="sxs-lookup"><span data-stu-id="ac917-168">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="ac917-169">Office 365 PowerShell の概要</span><span class="sxs-lookup"><span data-stu-id="ac917-169">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
