---
title: Office 365 PowerShell でライセンスとサービスを確認する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/03/2019
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
ms.openlocfilehash: bce181445523a2f043caa932f3d4e0ddd81d89cc
ms.sourcegitcommit: 6826e0ea4a777f7d98500209a9d3bc75e89f8d15
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/30/2019
ms.locfileid: "29651211"
---
# <a name="view-licenses-and-services-with-office-365-powershell"></a><span data-ttu-id="ae9ee-103">Office 365 PowerShell でライセンスとサービスを確認する</span><span class="sxs-lookup"><span data-stu-id="ae9ee-103">View licenses and services with Office 365 PowerShell</span></span>

<span data-ttu-id="ae9ee-104">**概要:** Office 365 PowerShell を使ってライセンス プラン、サービス、Office 365 組織で利用可能なライセンスについての情報を確認する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ae9ee-104">**Summary:** Explains how to use Office 365 PowerShell to view information about the licensing plans, services, and licenses that are available in your Office 365 organization.</span></span>
  
<span data-ttu-id="ae9ee-105">Office 365 サブスクリプションは、すべて以下の要素で構成されます。</span><span class="sxs-lookup"><span data-stu-id="ae9ee-105">Every Office 365 subscription consists of the following elements:</span></span>

- <span data-ttu-id="ae9ee-p101">**ライセンス プラン**これらは、Office 365 のプランやライセンスの計画とも呼ばれます。ライセンス プランでは、ユーザーに利用可能な Office 365 サービスを定義します。Office 365 サブスクリプションにはライセンスの複数の計画が含まれます。例のライセンスについては、Office 365 エンタープライズ E3 になります。</span><span class="sxs-lookup"><span data-stu-id="ae9ee-p101">**Licensing plans** These are also known as license plans or Office 365 plans. Licensing plans define the Office 365 services that are available to users. Your Office 365 subscription may contain multiple licensing plans. An example licensing plan would be Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="ae9ee-p102">**サービス**これらは、サービス プランとも呼ばれます。サービスは、Office 365 の製品、機能、および使用可能な機能で、各ライセンス プランなどの Exchange Online と Office Professional Plus です。ユーザーには、複数のライセンスが割り当てられているさまざまなサービスへのアクセスを許可するさまざまなライセンス プランからことができます。</span><span class="sxs-lookup"><span data-stu-id="ae9ee-p102">**Services** These are also known as service plans. Services are the Office 365 products, features, and capabilities that are available in each licensing plan, for example, Exchange Online and Office Professional Plus. Users can have multiple licenses assigned to them from different licensing plans that grant access to different services.</span></span>
    
- <span data-ttu-id="ae9ee-p103">**ライセンス** すべてのライセンス プランには、購入した数のライセンスが含まれています。ライセンスをユーザーに割り当てると、ライセンス プランで定義した Office 365 サービスが使えるようになります。それぞれのユーザー アカウントに、少なくとも 1 つのライセンス プランからの 1 つのライセンスが必要です。これにより、ユーザーが Office 365 にログオンして、サービスを利用することができます。</span><span class="sxs-lookup"><span data-stu-id="ae9ee-p103">**Licenses** Each licensing plan contains the number of licenses that you purchased. You assign licenses to users so they can use the Office 365 services that are defined by the licensing plan. Every user account requires at least one license from one licensing plan so they can log on to Office 365 and use the services.</span></span>
    
<span data-ttu-id="ae9ee-p104">Office 365 PowerShell を使って、Office 365 組織で利用可能なライセンス プラン、ライセンス、およびサービスに関する詳細を確認することができます。別の Office 365 サブスクリプションで利用可能な製品、機能、サービスについての詳細は、「[Office 365 プランのオプション](https://go.microsoft.com/fwlink/p/?LinkId=691147)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ae9ee-p104">You can use Office 365 PowerShell to view details about the available licensing plans, licenses, and services in your Office 365 organization. For more information about the products, features, and services that are available in different Office 365 subscriptions, see [Office 365 Plan Options](https://go.microsoft.com/fwlink/p/?LinkId=691147).</span></span>


## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="ae9ee-118">Graph モジュールの Azure Active Directory PowerShell を使用する</span><span class="sxs-lookup"><span data-stu-id="ae9ee-118">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="ae9ee-119">まず、[Office 365 テナントに接続します](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。</span><span class="sxs-lookup"><span data-stu-id="ae9ee-119">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  
<span data-ttu-id="ae9ee-120">現在ライセンス計画と各プランの利用可能なライセンスについての概要情報を表示するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="ae9ee-120">To view summary information about your current licensing plans and the available licenses for each plan, run the following command:</span></span>
  
```
Get-AzureADSubscribedSku | Select -Property Sku*,ConsumedUnits -ExpandProperty PrepaidUnits
```

<span data-ttu-id="ae9ee-121">結果には次の情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="ae9ee-121">The results contain the following information:</span></span>
  
- <span data-ttu-id="ae9ee-p105">**SkuPartNumber:** 組織の利用可能なライセンス プランを示しています。たとえば、`ENTERPRISEPACK`は、Office 365 エンタープライズ E3 のライセンスの計画の名前。</span><span class="sxs-lookup"><span data-stu-id="ae9ee-p105">**SkuPartNumber:** Shows the available licensing plans for your organization. For example, `ENTERPRISEPACK` is the license plan name for Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="ae9ee-124">**を有効にします**。特定のライセンスについては購入したライセンスの数です。</span><span class="sxs-lookup"><span data-stu-id="ae9ee-124">**Enabled:** Number of licenses that you've purchased for a specific licensing plan.</span></span>
    
- <span data-ttu-id="ae9ee-125">**ConsumedUnits:** 特定のライセンス プランでユーザーに割り当てたライセンスの数。</span><span class="sxs-lookup"><span data-stu-id="ae9ee-125">**ConsumedUnits:** Number of licenses that you've assigned to users from a specific licensing plan.</span></span>
    
<span data-ttu-id="ae9ee-126">すべてのライセンス プランで利用できる Office 365 のサービスに関する詳細を表示するには、まず、ライセンス プランの一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="ae9ee-126">To view details about the Office 365 services that are available in all of your license plans, first display a list of your license plans.</span></span>

````
Get-AzureADSubscribedSku | Select SkuPartNumber
````

<span data-ttu-id="ae9ee-127">次に、ライセンス プランの情報を変数に格納します。</span><span class="sxs-lookup"><span data-stu-id="ae9ee-127">Next, store the license plans information in a variable.</span></span>

````
$licenses = Get-AzureADSubscribedSku
````

<span data-ttu-id="ae9ee-128">次に、特定のライセンス プランでサービスを表示します。</span><span class="sxs-lookup"><span data-stu-id="ae9ee-128">Next, display the services in a specific license plan.</span></span>

````
$licenses[<index>].ServicePlans
````

<span data-ttu-id="ae9ee-129">\<ライセンス プランの表示の行番号を指定する整数は、index>、 `Get-AzureADSubscribedSku | Select SkuPartNumber` -1 のコマンドです。</span><span class="sxs-lookup"><span data-stu-id="ae9ee-129">\<index> is an integer that specifies the row number of the license plan from the display of the `Get-AzureADSubscribedSku | Select SkuPartNumber` command, minus 1.</span></span>

<span data-ttu-id="ae9ee-130">などの場合の表示、`Get-AzureADSubscribedSku | Select SkuPartNumber`は、コマンド。</span><span class="sxs-lookup"><span data-stu-id="ae9ee-130">For example, if the display of the `Get-AzureADSubscribedSku | Select SkuPartNumber` command is this:</span></span>

````
SkuPartNumber
-------------
WIN10_VDA_E5
EMSPREMIUM
ENTERPRISEPREMIUM
FLOW_FREE
````

<span data-ttu-id="ae9ee-131">ENTERPRISEPREMIUM ライセンス プランのサービスを表示するコマンドは、これです。</span><span class="sxs-lookup"><span data-stu-id="ae9ee-131">Then the command to display the services for the ENTERPRISEPREMIUM license plan is this:</span></span>

````
$licenses[2].ServicePlans
````

<span data-ttu-id="ae9ee-p106">ENTERPRISEPREMIUM は、3 番目の行です。したがって、インデックス値は (3-1) または 2 です。</span><span class="sxs-lookup"><span data-stu-id="ae9ee-p106">ENTERPRISEPREMIUM is the third row. Therefore, the index value is (3 - 1), or 2.</span></span>

<span data-ttu-id="ae9ee-134">ライセンス プラン (製品の名前とも呼ばれます) が含まれているサービス プラン、および対応するフレンドリ名の一覧については、[製品の名前とライセンスのサービス プランの識別子](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ae9ee-134">For a complete list of license plans (also known as product names), their included service plans, and their corresponding friendly names, see [Product names and service plan identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span></span>

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="ae9ee-135">Windows PowerShell の Microsoft Azure Active Directory モジュールを使用する</span><span class="sxs-lookup"><span data-stu-id="ae9ee-135">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="ae9ee-136">まず、[Office 365 テナントに接続します](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="ae9ee-136">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

>[!Note]
><span data-ttu-id="ae9ee-p107">PowerShell スクリプトが利用可能なこのトピックで説明する手順を自動化します。具体的には、スクリプトでは、表示し、影響を与えるを含む、Office 365 の組織でサービスを無効にすることができます。詳細については、 [Office 365 の PowerShell で影響を与えるへのアクセスを無効にする](disable-access-to-sway-with-office-365-powershell.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ae9ee-p107">A PowerShell script is available that automates the procedures described in this topic. Specifically, the script lets you view and disable services in your Office 365 organization, including Sway. For more information, see [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span></span>
>
    
<span data-ttu-id="ae9ee-140">現在ライセンス計画と各プランの利用可能なライセンスについての概要情報を表示するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="ae9ee-140">To view summary information about your current licensing plans and the available licenses for each plan, run the following command:</span></span>
  
```
Get-MsolAccountSku
```

<span data-ttu-id="ae9ee-141">結果には次の情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="ae9ee-141">The results contain the following information:</span></span>
  
- <span data-ttu-id="ae9ee-p108">**AccountSkuId:** 構文 `<CompanyName>:<LicensingPlan>` を使用して、組織で利用可能なライセンス プランを表示します。_<CompanyName>_ は Office 365 に登録するときに指定した値で、組織に対して一意です。_<LicensingPlan>_ の値は、すべてのユーザーに対して同じです。たとえば、値 `litwareinc:ENTERPRISEPACK` では、会社名が `litwareinc`、ライセンス プラン名が `ENTERPRISEPACK` で、これが Office 365 Enterprise E3 のシステム名になります。</span><span class="sxs-lookup"><span data-stu-id="ae9ee-p108">**AccountSkuId:** Show the available licensing plans for your organization by using the syntax `<CompanyName>:<LicensingPlan>`.  _<CompanyName>_ is the value that you provided when you enrolled in Office 365, and is unique for your organization. The _<LicensingPlan>_ value is the same for everyone. For example, in the value `litwareinc:ENTERPRISEPACK`, the company name is  `litwareinc`, and the licensing plan name  `ENTERPRISEPACK`, which is the system name for Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="ae9ee-146">**ActiveUnits:** 特定のライセンスについては購入したライセンスの数です。</span><span class="sxs-lookup"><span data-stu-id="ae9ee-146">**ActiveUnits:** Number of licenses that you've purchased for a specific licensing plan.</span></span>
    
- <span data-ttu-id="ae9ee-147">**WarningUnits:** 更新していないライセンス プランのライセンスの数。30 日の猶予期間を過ぎると有効期限切れになります。</span><span class="sxs-lookup"><span data-stu-id="ae9ee-147">**WarningUnits:** Number of licenses in a licensing plan that you haven't renewed, and that will expire after the 30-day grace period.</span></span>
    
- <span data-ttu-id="ae9ee-148">**ConsumedUnits:** 特定のライセンス プランでユーザーに割り当てたライセンスの数。</span><span class="sxs-lookup"><span data-stu-id="ae9ee-148">**ConsumedUnits:** Number of licenses that you've assigned to users from a specific licensing plan.</span></span>
    
<span data-ttu-id="ae9ee-149">すべてのライセンス プランで利用できる Office 365 サービスの詳細を参照するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="ae9ee-149">To view details about the Office 365 services that are available in all of your license plans, run the following command:</span></span>
  
```
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

<span data-ttu-id="ae9ee-p109">次の表は、Office 365 のサービス プランと、最も一般的なサービスのフレンドリ名を示します。サービス プランの一覧は、異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="ae9ee-p109">The following table shows the Office 365 service plans and their friendly names for the most common services. Your list of service plans might be different.</span></span> 
  
|<span data-ttu-id="ae9ee-152">**サービス プラン**</span><span class="sxs-lookup"><span data-stu-id="ae9ee-152">**Service plan**</span></span>|<span data-ttu-id="ae9ee-153">**説明**</span><span class="sxs-lookup"><span data-stu-id="ae9ee-153">**Description**</span></span>|
|:-----|:-----|
| `SWAY` <br/> |<span data-ttu-id="ae9ee-154">Sway</span><span class="sxs-lookup"><span data-stu-id="ae9ee-154">Sway</span></span>  <br/> |
| `TEAMS1` <br/> |<span data-ttu-id="ae9ee-155">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="ae9ee-155">Microsoft Teams</span></span>  <br/> |
| `YAMMER_ENTERPRISE` <br/> |<span data-ttu-id="ae9ee-156">Yammer</span><span class="sxs-lookup"><span data-stu-id="ae9ee-156">Yammer</span></span>  <br/> |
| `RMS_S_ENTERPRISE` <br/> |<span data-ttu-id="ae9ee-157">Azure Rights Management (RMS)</span><span class="sxs-lookup"><span data-stu-id="ae9ee-157">Azure Rights Management (RMS)</span></span>  <br/> |
| `OFFICESUBSCRIPTION` <br/> |<span data-ttu-id="ae9ee-158">Office Professional Plus</span><span class="sxs-lookup"><span data-stu-id="ae9ee-158">Office Professional Plus</span></span>  <br/> |
| `MCOSTANDARD` <br/> |<span data-ttu-id="ae9ee-159">Skype for Business Online</span><span class="sxs-lookup"><span data-stu-id="ae9ee-159">Skype for Business Online</span></span>  <br/> |
| `SHAREPOINTWAC` <br/> |<span data-ttu-id="ae9ee-160">Office Online</span><span class="sxs-lookup"><span data-stu-id="ae9ee-160">Office Online</span></span>  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |<span data-ttu-id="ae9ee-161">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="ae9ee-161">SharePoint Online</span></span>  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |<span data-ttu-id="ae9ee-162">Exchange Online プラン 2</span><span class="sxs-lookup"><span data-stu-id="ae9ee-162">Exchange Online Plan 2</span></span>  <br/> |
   
<span data-ttu-id="ae9ee-163">ライセンス プラン (製品の名前とも呼ばれます) が含まれているサービス プラン、および対応するフレンドリ名の一覧については、[製品の名前とライセンスのサービス プランの識別子](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ae9ee-163">For a complete list of license plans (also known as product names), their included service plans, and their corresponding friendly names, see [Product names and service plan identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span></span>

<span data-ttu-id="ae9ee-164">特定のライセンス プランで利用可能な Office 365 サービスの詳細を確認するには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="ae9ee-164">To view details about the Office 365 services that are available in a specific licensing plan, use the following syntax.</span></span>
  
```
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "<AccountSkuId>"}).ServiceStatus
```

<span data-ttu-id="ae9ee-165">この例では、litwareinc:ENTERPRISEPACK (Office 365 エンタープライズ E3) ライセンス プランで利用可能な Office 365 サービスを使用します。</span><span class="sxs-lookup"><span data-stu-id="ae9ee-165">This example shows the Office 365 services that are available in the litwareinc:ENTERPRISEPACK (Office 365 Enterprise E3) licensing plan.</span></span>
  
```
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "litwareinc:ENTERPRISEPACK"}).ServiceStatus
```


## <a name="new-to-office-365"></a><span data-ttu-id="ae9ee-166">Office 365 を初めて使用する場合</span><span class="sxs-lookup"><span data-stu-id="ae9ee-166">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   
## <a name="see-also"></a><span data-ttu-id="ae9ee-167">関連項目</span><span class="sxs-lookup"><span data-stu-id="ae9ee-167">See also</span></span>


[<span data-ttu-id="ae9ee-168">Office 365 PowerShell を使ってユーザー アカウントとライセンスを管理します。</span><span class="sxs-lookup"><span data-stu-id="ae9ee-168">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="ae9ee-169">Office 365 PowerShell による Office 365 の管理</span><span class="sxs-lookup"><span data-stu-id="ae9ee-169">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="ae9ee-170">Office 365 PowerShell の概要</span><span class="sxs-lookup"><span data-stu-id="ae9ee-170">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
