---
title: "Office 365 PowerShell を使用してアカウントのライセンスとサービスの詳細を表示する"
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
- PowerShell
- Ent_Office_Other
- LIL_Placement
ms.assetid: ace07d8a-15ca-4b89-87f0-abbce809b519
description: "Office 365 の PowerShell を使用してユーザーに割り当てられている Office 365 のサービスを確認する方法について説明します。"
ms.openlocfilehash: 69784b43e6e2b24f776d07a937877e5ae0c74888
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2018
---
# <a name="view-account-license-and-service-details-with-office-365-powershell"></a><span data-ttu-id="07bc7-103">Office 365 PowerShell を使用してアカウントのライセンスとサービスの詳細を表示する</span><span class="sxs-lookup"><span data-stu-id="07bc7-103">View account license and service details with Office 365 PowerShell</span></span>

<span data-ttu-id="07bc7-104">**の概要:**Office 365 の PowerShell を使用してユーザーに割り当てられている Office 365 のサービスを確認する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="07bc7-104">**Summary:** Explains how to use Office 365 PowerShell to determine the Office 365 services that have been assigned to users.</span></span>
  
<span data-ttu-id="07bc7-p101">、Office 365 では、計画のライセンスからライセンス (も呼び出された Sku または Office 365 プラン) ユーザーにそれらの計画に定義されている Office 365 サービスへのアクセスを提供します。ただし、[ユーザーはそれらに現在割り当てられているライセンスで使用可能なすべてのサービスへのアクセスをいない可能性があります。ユーザー アカウントのサービスの状態を表示するのには、Office 365 の PowerShell を使用できます。</span><span class="sxs-lookup"><span data-stu-id="07bc7-p101">In Office 365, licenses from licensing plans (also called SKUs or Office 365 plans) give users access to the Office 365 services that are defined for those plans. However, a user might not have access to all the services that are available in a license that's currently assigned to them. You can use Office 365 PowerShell to view the status of services on user accounts.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="07bc7-108">はじめに</span><span class="sxs-lookup"><span data-stu-id="07bc7-108">Before you begin</span></span>
<span data-ttu-id="07bc7-109"><a name="RTT"> </a></span><span class="sxs-lookup"><span data-stu-id="07bc7-109"></span></span>

- <span data-ttu-id="07bc7-p102">このトピックの手順では、Office 365 PowerShell に接続する必要があります。手順については、「[Office 365 PowerShell への接続](connect-to-office-365-powershell.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="07bc7-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="07bc7-112">コマンドを使用して、`Get-MsolAccountSku`と`(Get-MsolAccountSku | where {$_.AccountSkuId -eq '<AccountSkuId>'}).ServiceStatus`、次の情報を検索します。</span><span class="sxs-lookup"><span data-stu-id="07bc7-112">Use the commands  `Get-MsolAccountSku` and `(Get-MsolAccountSku | where {$_.AccountSkuId -eq '<AccountSkuId>'}).ServiceStatus` to find the following information:</span></span>
    
  - <span data-ttu-id="07bc7-113">組織で使用可能なライセンス プラン。</span><span class="sxs-lookup"><span data-stu-id="07bc7-113">The licensing plans that are available in your organization.</span></span>
    
  - <span data-ttu-id="07bc7-114">各ライセンス プランで使用可能なサービス、およびサービスがリストされる順序 (インデックス番号)。</span><span class="sxs-lookup"><span data-stu-id="07bc7-114">The services that are available in each licensing plan, and the order in which they are listed (the index number).</span></span>
    
     <span data-ttu-id="07bc7-115">計画、ライセンス、およびサービスのライセンスの詳細については、[ライセンスを表示し Office 365 の PowerShell を使用してサービス](view-licenses-and-services-with-office-365-powershell.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="07bc7-115">For more information about licensing plans, license, and services, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="07bc7-116">コマンドを使用して`Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses`(インデックス番号) を一覧には、ユーザー、および順に割り当てられているライセンスが見つかりません。</span><span class="sxs-lookup"><span data-stu-id="07bc7-116">Use the command  `Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses` to find the licenses that are assigned to a user, and the order in which they are listed (the index number).</span></span>
    
- <span data-ttu-id="07bc7-117">_All_ パラメーターなしで **Get-MsolUser** コマンドレットを使用する場合、最初の 500 個のアカウントだけが返されます。</span><span class="sxs-lookup"><span data-stu-id="07bc7-117">If you use the **Get-MsolUser** cmdlet without using the _All_ parameter, only the first 500 accounts are returned.</span></span>
    
## <a name="the-short-version-instructions-without-explanations"></a><span data-ttu-id="07bc7-118">簡略版 (説明なしの手順)</span><span class="sxs-lookup"><span data-stu-id="07bc7-118">The short version (instructions without explanations)</span></span>
<span data-ttu-id="07bc7-119"><a name="ShortVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="07bc7-119"></span></span>

<span data-ttu-id="07bc7-120">ユーザーへのアクセス権を持っている Office 365 の PowerShell のすべてのサービスを表示するには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="07bc7-120">To view all the Office 365 PowerShell services that a user has access to, use the following syntax:</span></span>
  
```
(Get-MsolUser -UserPrincipalName <user account UPN>).Licenses[<LicenseIndexNumber>].ServiceStatus
```

<span data-ttu-id="07bc7-p103">この例では、BelindaN@litwareinc.com のユーザーのアクセスを持っているサービスを使用します。自分のアカウントに割り当てられているすべてのライセンスに関連付けられているサービスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="07bc7-p103">This example shows the services to which the user BelindaN@litwareinc.com has access. This shows the services that are associated with all licenses that are assigned to her account.</span></span>
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus
```

<span data-ttu-id="07bc7-123">次の例では、ユーザー BelindaN@litwareinc.com が、アカウントに割り当てられている最初のライセンス (インデックス番号 0) からアクセスできるサービスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="07bc7-123">This example shows the services that user BelindaN@litwareinc.com has access to from the first license that's assigned to her account (the index number is 0).</span></span>
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses[0].ServiceStatus
```

<span data-ttu-id="07bc7-124">特定のサービスが有効、または無効なすべてのライセンス ユーザーを調べるには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="07bc7-124">To find all the licensed users who have been enabled or not enabled for specific services, use the following syntax:</span></span>
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[<LicenseIndexNumber> ].ServiceStatus[<ServiceIndexNumber> ].ProvisioningStatus <-eq | -ne> "Disabled" -and $_.Licenses[<LicenseIndexNumber> ].ServiceStatus[<ServiceIndexNumber> ].ProvisioningStatus <-eq | -ne> "Disabled"...}
```

<span data-ttu-id="07bc7-125">以下の例では、次の情報を使用します。</span><span class="sxs-lookup"><span data-stu-id="07bc7-125">These examples use the following information:</span></span>
  
- <span data-ttu-id="07bc7-126">Office 365 サービスに関心をへのアクセスを提供するライセンスは、(インデックス番号は 0 になります) すべてのユーザーに割り当てられている最初のライセンスです。</span><span class="sxs-lookup"><span data-stu-id="07bc7-126">The license that gives access to the Office 365 services that we're interested in is the first license that's assigned to all users (the index number is 0).</span></span>
    
- <span data-ttu-id="07bc7-p104">関心を Office 365 サービスは、オンライン ビジネスおよび Exchange Online の Skype です。ライセンス プランに関連付けられているライセンス、ビジネス オンラインの Skype は、6 番目の項目に記載されているサービス (インデックス番号が 5)、9 のサービスを Exchange Online には、(インデックス番号は、8) に表示されています。</span><span class="sxs-lookup"><span data-stu-id="07bc7-p104">The Office 365 services that we're interested in are Skype for Business Online and Exchange Online. For the licenses that are associated with the licensing plan, Skype for Business Online is the 6th service listed (the index number is 5), and Exchange Online is the 9th service listed (the index number is 8).</span></span>
    
<span data-ttu-id="07bc7-129">この例が有効になっている Skype のオンライン ビジネスおよび Exchange Online ライセンスを付与されたすべてのユーザーを返します。</span><span class="sxs-lookup"><span data-stu-id="07bc7-129">This example returns all licensed users who are enabled for Skype for Business Online and Exchange Online.</span></span>
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[0].ServiceStatus[5].ProvisioningStatus -ne "Disabled" -and $_.Licenses[0].ServiceStatus[8].ProvisioningStatus -ne "Disabled"}
```

<span data-ttu-id="07bc7-130">この例では、すべてのライセンスを受けたユーザーは有効になっている Skype のビジネス オンラインまたは Exchange Online を返します。</span><span class="sxs-lookup"><span data-stu-id="07bc7-130">This example returns all licensed users who aren't enabled for Skype for Business Online or Exchange Online.</span></span>
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[0].ServiceStatus[5].ProvisioningStatus -eq "Disabled" -and $_.Licenses[0].ServiceStatus[8].ProvisioningStatus -eq "Disabled"}
```

## <a name="the-long-version-instructions-with-detailed-explanations"></a><span data-ttu-id="07bc7-131">詳細版 (詳細な説明付きの手順)</span><span class="sxs-lookup"><span data-stu-id="07bc7-131">The long version (instructions with detailed explanations)</span></span>
<span data-ttu-id="07bc7-132"><a name="LongVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="07bc7-132"></span></span>

### <a name="find-the-office-365-powershell-services-that-a-user-has-access-to"></a><span data-ttu-id="07bc7-133">Office 365 の PowerShell サービスへのアクセスを持つユーザーを見つける</span><span class="sxs-lookup"><span data-stu-id="07bc7-133">Find the Office 365 PowerShell services that a user has access to</span></span>

<span data-ttu-id="07bc7-p105">ユーザーに Office 365 のライセンスが発行されているし、どのユーザーがいないを理解するが明らかに重要です。(詳細については[Office 365 の PowerShell でのライセンスおよびライセンスのないユーザーを表示する](view-licensed-and-unlicensed-users-with-office-365-powershell.md)資料を参照してください)。ただし、Office 365 のライセンスがあるだけはわかります何もそのユーザーが実際に何と Office 365 について。彼または彼女を使用して Exchange Online または Skype オンライン ビジネスのでしょうか。このユーザーが SharePoint のオンラインでアクセスできますか。彼または彼女が、Office Professional Plus へのアクセスですか。ユーザーがこれらのサービスにアクセスする可能性を持っていること、ライセンスのことです。ただし、ユーザーに利用できる機能は、彼または彼女のライセンスを有効になっているサービスに依存します。</span><span class="sxs-lookup"><span data-stu-id="07bc7-p105">It's obviously important for you to know which users have been issued Office 365 licenses and which users haven't. (See the article [View licensed and unlicensed users with Office 365 PowerShell](view-licensed-and-unlicensed-users-with-office-365-powershell.md) for more information). However, simply having an Office 365 license doesn't tell you anything about what that user can actually do with Office 365. Can he or she use Exchange Online or Skype for Business Online? Can this user access SharePoint Online? Does he or she have access to Office Professional Plus? Having a license simply means that the user has the potential to access these services. However, the capabilities available to a user depend on the services that have been enabled on his or her license.</span></span>
  
<span data-ttu-id="07bc7-p106">どのように確認するが Office 365 の機能ユーザーへのアクセス権を持っているでしょうか。このいずれかのようなコマンドを実行する必要があることを実行します。</span><span class="sxs-lookup"><span data-stu-id="07bc7-p106">So how can we determine which Office 365 features a user has access to? To do that we need to run a command similar to this one:</span></span>
  
```
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com | Select-Object -ExpandProperty Licenses | Select-Object -ExpandProperty ServiceStatus
```

<span data-ttu-id="07bc7-144">このコマンドで、BelindaN@litwareinc.com のアカウントに関する情報を取得する**Get MsolUser**コマンドレットを使用している私たち。その情報を取得して、アカウント データを**Select-object**コマンドレットにパイプし、**ライセンス**のプロパティの値を「拡張」を**選択オブジェクト**を確認します。</span><span class="sxs-lookup"><span data-stu-id="07bc7-144">In this command, we're using the **Get-MsolUser** cmdlet to return information about the account BelindaN@litwareinc.com. Once we've returned that information, we then pipe the account data to the **Select-Object** cmdlet and ask **Select-Object** to "expand" the value of the **Licenses** property:</span></span>
  
 `Select-Object -ExpandProperty Licenses`
  
<span data-ttu-id="07bc7-p107">理由で実行するでしょうか。既定では**ライセンス**のプロパティのみがわかりますから Belinda のライセンスが付属していたライセンス パックの名前。</span><span class="sxs-lookup"><span data-stu-id="07bc7-p107">Why do we do that? Well, by default the **Licenses** property only tells us the name of the licensing pack where Belinda's license came from:</span></span>
  
```
Licenses
--------
{litwareinc:ENTERPRISEPACK}
```

<span data-ttu-id="07bc7-147">**ライセンス**プロパティを「拡大」は、少しの詳細については。</span><span class="sxs-lookup"><span data-stu-id="07bc7-147">"Expanding" the **Licenses** property gives us a little more information:</span></span>
  
```
ExtensionData     AccountSku       AccountSkuId ServiceStatus
-------------     ----------       ------------ -------------
System.Runtime... Microsoft.On...  litwarein... {Microsoft.Online.A...
```

<span data-ttu-id="07bc7-148">**サービス ステータス**のプロパティを展開することによって取得できますより多くの情報。</span><span class="sxs-lookup"><span data-stu-id="07bc7-148">And then by expanding the **ServiceStatus** property we can get back even more information:</span></span>
  
|<span data-ttu-id="07bc7-149">****サービス プラン****</span><span class="sxs-lookup"><span data-stu-id="07bc7-149">****Service plan****</span></span>|<span data-ttu-id="07bc7-150">****説明****</span><span class="sxs-lookup"><span data-stu-id="07bc7-150">****Description****</span></span>|
|:-----|:-----|
| `SWAY` <br/> |<span data-ttu-id="07bc7-151">Sway</span><span class="sxs-lookup"><span data-stu-id="07bc7-151">Sway</span></span>  <br/> |
| `TEAMS1` <br/> |<span data-ttu-id="07bc7-152">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="07bc7-152">Microsoft Teams</span></span>  <br/> |
| `YAMMER_ENTERPRISE` <br/> |<span data-ttu-id="07bc7-153">Yammer</span><span class="sxs-lookup"><span data-stu-id="07bc7-153">Yammer</span></span>  <br/> |
| `RMS_S_ENTERPRISE` <br/> |<span data-ttu-id="07bc7-154">Azure Rights Management (RMS)</span><span class="sxs-lookup"><span data-stu-id="07bc7-154">Azure Rights Management (RMS)</span></span>  <br/> |
| `OFFICESUBSCRIPTION` <br/> |<span data-ttu-id="07bc7-155">Office Professional Plus</span><span class="sxs-lookup"><span data-stu-id="07bc7-155">Office Professional Plus</span></span>  <br/> |
| `MCOSTANDARD` <br/> |<span data-ttu-id="07bc7-156">Skype for Business Online</span><span class="sxs-lookup"><span data-stu-id="07bc7-156">Skype for Business Online</span></span>  <br/> |
| `SHAREPOINTWAC` <br/> |<span data-ttu-id="07bc7-157">Office Online</span><span class="sxs-lookup"><span data-stu-id="07bc7-157">Office Online</span></span>  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |<span data-ttu-id="07bc7-158">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="07bc7-158">SharePoint Online</span></span>  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |<span data-ttu-id="07bc7-159">Exchange Online プラン 2</span><span class="sxs-lookup"><span data-stu-id="07bc7-159">Exchange Online Plan 2</span></span>  <br/> |
   
> [!NOTE]
> <span data-ttu-id="07bc7-p108">入力することが多すぎることがあると答えるとしますか。配置するには、ほとんどの Windows PowerShell obtuseness を実行できますこの縮小バージョンのコマンドの代わりに: >`(Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com).Licenses[0].ServiceStatus`</span><span class="sxs-lookup"><span data-stu-id="07bc7-p108">You say that's too much typing? Well, if you can put up with a little Windows PowerShell obtuseness, you can run this condensed version of the command instead: >  `(Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com).Licenses[0].ServiceStatus`</span></span>
  
<span data-ttu-id="07bc7-p109">念のため、「展開」**のライセンス**は**ライセンス**が複数値を持つプロパティであるため: 複数の値を格納できる単一のプロパティです。展開してプロパティの値を単に下にドリル ダウンするときの取得次の値を既定では、表示されていない画面に表示されます。</span><span class="sxs-lookup"><span data-stu-id="07bc7-p109">In case you're wondering, we can "expand" the **Licenses** property because **Licenses** is a multivalued property: it's a single property that can store multiple values. When we expand a property value we simply drill down to get at these additional values that, by default, are not displayed onscreen.</span></span>
  
> [!NOTE]
> <span data-ttu-id="07bc7-p110">どのようにするになっている値は、複数値を持つプロパティであることでしょうか。アウト ボックスが、次のようなコマンドを実行している実行してください: > `Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com | Get-Member`> **get-member**コマンドレットは、オブジェクト自体に関する情報を返しますこの例では、プロパティに関する情報は、ユーザー アカウント オブジェクトを構成する値です。**ライセンス**のプロパティについては、**メンバーの取得**を次のとおりです: > `Licenses Property System.Collections.Generic.List[Microsoft.On...`> プロパティ定義のコレクションのある場合 (この例では、 `System.Collections.Generic.List`) 複数値を持つプロパティを扱うことがわかって、します。</span><span class="sxs-lookup"><span data-stu-id="07bc7-p110">So how are you supposed to know that a value is a multivalued property? Well, to find that out, try running a command similar to this: >  `Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com | Get-Member`> The **Get-member** cmdlet returns information about the object itself; in this case, information about the property values that make up a user account object. Here's what **Get-Member** has to say about the **Licenses** property:>  `Licenses Property System.Collections.Generic.List[Microsoft.On...`> If the property definition says something about collections (in this case,  `System.Collections.Generic.List`) then you know you're dealing with a multivalued property.</span></span> 
  
<span data-ttu-id="07bc7-p111">このすべての意味は何ですか。それに答える、最初にもう 1 つ見てみましょう**Get MsolUser**コマンドレットによって返される情報。</span><span class="sxs-lookup"><span data-stu-id="07bc7-p111">So what does all this mean? To answer that, let's first take another look at the information returned by the **Get-MsolUser** cmdlet:</span></span>
  
```
ServicePlan                       ProvisioningStatus
-----------                       ------------------
SWAY                              Success
INTUNE_O365                       Success
YAMMER_ENTERPRISE                 PendingInput
RMS_S_ENTERPRISE                  Success
OFFICESUBSCRIPTION                Success
MCOSTANDARD                       Success
SHAREPOINTWAC                     Success
SHAREPOINTENTERPRISE              Success
EXCHANGE_S_ENTERPRISE             Success
```

<span data-ttu-id="07bc7-169">見て奇妙という名前のサービス プランが実際に表すかを説明する表にします。</span><span class="sxs-lookup"><span data-stu-id="07bc7-169">And let's also take a look at a table that explains what these oddly-named service plans really represent:</span></span>
  
|<span data-ttu-id="07bc7-170">****サービス プラン****</span><span class="sxs-lookup"><span data-stu-id="07bc7-170">****Service plan****</span></span>|<span data-ttu-id="07bc7-171">****説明****</span><span class="sxs-lookup"><span data-stu-id="07bc7-171">****Description****</span></span>|
|:-----|:-----|
| `SWAY` <br/> |<span data-ttu-id="07bc7-172">Sway</span><span class="sxs-lookup"><span data-stu-id="07bc7-172">Sway</span></span>  <br/> |
| `TEAMS1` <br/> |<span data-ttu-id="07bc7-173">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="07bc7-173">Microsoft Teams</span></span>  <br/> |
| `YAMMER_ENTERPRISE` <br/> |<span data-ttu-id="07bc7-174">Yammer</span><span class="sxs-lookup"><span data-stu-id="07bc7-174">Yammer</span></span>  <br/> |
| `RMS_S_ENTERPRISE` <br/> |<span data-ttu-id="07bc7-175">Azure Rights Management (RMS)</span><span class="sxs-lookup"><span data-stu-id="07bc7-175">Azure Rights Management (RMS)</span></span>  <br/> |
| `OFFICESUBSCRIPTION` <br/> |<span data-ttu-id="07bc7-176">Office Professional Plus</span><span class="sxs-lookup"><span data-stu-id="07bc7-176">Office Professional Plus</span></span>  <br/> |
| `MCOSTANDARD` <br/> |<span data-ttu-id="07bc7-177">Skype for Business Online</span><span class="sxs-lookup"><span data-stu-id="07bc7-177">Skype for Business Online</span></span>  <br/> |
| `SHAREPOINTWAC` <br/> |<span data-ttu-id="07bc7-178">Office Online</span><span class="sxs-lookup"><span data-stu-id="07bc7-178">Office Online</span></span>  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |<span data-ttu-id="07bc7-179">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="07bc7-179">SharePoint Online</span></span>  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |<span data-ttu-id="07bc7-180">Exchange Online プラン 2</span><span class="sxs-lookup"><span data-stu-id="07bc7-180">Exchange Online Plan 2</span></span>  <br/> |
   
<span data-ttu-id="07bc7-p112">おわかりでしょうか。 `MCOSTANDARD`ビジネス オンラインでは、Skype の内部プログラミング名だけでは、中に`OFFICESUSBCRIPTION`は、Office Professional Plus の内部のプログラミング名だけ。世界では、最も直感的なものではありませんが、次の表を手元にする限り、Office 365 サービスを使用する際に多くの問題を必要はありません。</span><span class="sxs-lookup"><span data-stu-id="07bc7-p112">Got all that?  `MCOSTANDARD` is just an internal programming name for Skype for Business Online, while `OFFICESUSBCRIPTION` is just the internal programming name for Office Professional Plus. It's not the most intuitive thing in the world, but as long as you keep this table handy you won't have many problems when it comes to working with Office 365 services.</span></span>
  
<span data-ttu-id="07bc7-p113">待て: はありません。**ProvisioningStatus**設定されている場合、[ライセンスを表示し Office 365 の PowerShell を使用してサービス](view-licenses-and-services-with-office-365-powershell.md)の記事で学んだように`Success`つまり、サービスが完全に有効になっています。などの場合は`MCOSTANDARD`に設定されて`Success`、ユーザーがオンライン ビジネスの Skype にアクセスできることを意味します。**ProvisioningStatus**設定されている場合`PendingInput`Office 365 のサービス要求がまだ処理することを意味します。ただし、ユーザー通常ログオンし、要求が処理を終了するときにサービスにアクセスします。(`YAMMER_ENTERPRISE`として常に表示される`PendingInput`が、[ok]: Yammer へのログオンからユーザーを停止をしない)。</span><span class="sxs-lookup"><span data-stu-id="07bc7-p113">But wait: there's more. As we learned in the article [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md), if the **ProvisioningStatus** is set to `Success` that means that the service has been fully enabled; for example if `MCOSTANDARD` is set to `Success` that means that the user can access Skype for Business Online. If the **ProvisioningStatus** is set to `PendingInput` that means that Office 365 is still processing the service request; however, the user can typically log on and access the service while the request finishes processing. ( `YAMMER_ENTERPRISE` will always be shown as `PendingInput`, but that's OK: that won't stop a user from logging on to Yammer).</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="07bc7-188">ユーザーがインストールし、新しい Office Professional Plus インストール中にアクティブにすることができます`OFFICESUBSCRIPTION`では、`PendingInput`の状態です。</span><span class="sxs-lookup"><span data-stu-id="07bc7-188">Users can install and activate a new Office Professional Plus installation while  `OFFICESUBSCRIPTION` is in the `PendingInput` state.</span></span>
  
<span data-ttu-id="07bc7-189">言うまでも、サービスに設定されて`Disabled`問題のサービスのユーザーが利用できるがないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="07bc7-189">And, needless to say, is a service is set to  `Disabled` that means that the service in question is not available to the user.</span></span>
  

### <a name="find-users-that-have-access-to-specific-office-365-powershell-services"></a><span data-ttu-id="07bc7-190">Office 365 の PowerShell の特定のサービスへのアクセス権を持つユーザーを検索します。</span><span class="sxs-lookup"><span data-stu-id="07bc7-190">Find users that have access to specific Office 365 PowerShell services</span></span>

<span data-ttu-id="07bc7-p114">別の資料では、サービスへのユーザー アクセスを無効にするのには、Office 365 の PowerShell を使用する方法を見られました。(場合は、その記事を参照してください[Office 365 の PowerShell を使用してサービスへのアクセスを無効にする](disable-access-to-services-with-office-365-powershell.md))。により次のような疑問が生じます: どの*ユーザー*を決定する方法はあります (は、複数のユーザー) が有効か無効にするサービスがあるでしょうか。</span><span class="sxs-lookup"><span data-stu-id="07bc7-p114">In a separate article, we saw how you can use Office 365 PowerShell to disable user access to services. (If you missed that article, see [Disable access to services with Office 365 PowerShell](disable-access-to-services-with-office-365-powershell.md)). That leads to an obvious question: is there any way to determine which  *users*  (that is, more than one user) have which services enabled or disabled?</span></span>
  
<span data-ttu-id="07bc7-p115">その他のご質問があると願っていました。その質問に解答するために最初に考えた[ライセンスを表示し Office 365 の PowerShell を使用してサービス](view-licenses-and-services-with-office-365-powershell.md)の記事で当社のみ使用可能なライセンス プランのサービスのテーブルを見てみましょう`litwareinc:ENTERPRISEPACK`。</span><span class="sxs-lookup"><span data-stu-id="07bc7-p115">We were hoping that someone would ask that. In order to answer that question, let's review the table of services that we first looked at in the article [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md) for our only available licensing plan `litwareinc:ENTERPRISEPACK`:</span></span>
  
|<span data-ttu-id="07bc7-196">****サービス プラン****</span><span class="sxs-lookup"><span data-stu-id="07bc7-196">****Service plan****</span></span>|<span data-ttu-id="07bc7-197">****説明****</span><span class="sxs-lookup"><span data-stu-id="07bc7-197">****Description****</span></span>|
|:-----|:-----|
| `SWAY` <br/> |<span data-ttu-id="07bc7-198">Sway</span><span class="sxs-lookup"><span data-stu-id="07bc7-198">Sway</span></span>  <br/> |
| `TEAMS1` <br/> |<span data-ttu-id="07bc7-199">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="07bc7-199">Microsoft Teams</span></span>  <br/> |
| `YAMMER_ENTERPRISE` <br/> |<span data-ttu-id="07bc7-200">Yammer</span><span class="sxs-lookup"><span data-stu-id="07bc7-200">Yammer</span></span>  <br/> |
| `RMS_S_ENTERPRISE` <br/> |<span data-ttu-id="07bc7-201">Azure Rights Management (RMS)</span><span class="sxs-lookup"><span data-stu-id="07bc7-201">Azure Rights Management (RMS)</span></span>  <br/> |
| `OFFICESUBSCRIPTION` <br/> |<span data-ttu-id="07bc7-202">Office Professional Plus</span><span class="sxs-lookup"><span data-stu-id="07bc7-202">Office Professional Plus</span></span>  <br/> |
| `MCOSTANDARD` <br/> |<span data-ttu-id="07bc7-203">Skype for Business Online</span><span class="sxs-lookup"><span data-stu-id="07bc7-203">Skype for Business Online</span></span>  <br/> |
| `SHAREPOINTWAC` <br/> |<span data-ttu-id="07bc7-204">Office Online</span><span class="sxs-lookup"><span data-stu-id="07bc7-204">Office Online</span></span>  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |<span data-ttu-id="07bc7-205">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="07bc7-205">SharePoint Online</span></span>  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |<span data-ttu-id="07bc7-206">Exchange Online プラン 2</span><span class="sxs-lookup"><span data-stu-id="07bc7-206">Exchange Online Plan 2</span></span>  <br/> |
   
<span data-ttu-id="07bc7-p116">サービス計画では、プログラミングの内部名は製品よりもそれ以上、思い出して、たとえば、 `OFFICESUBSCRIPTION`、1 つの名前には、Office Professional Plus の内部のプログラミングの名前です。場合`OFFICESUBSCRIPTION`として表示される`SUCCESS`ユーザーのサービス プランでは、上、つまり Office Professional Plus にアクセスするユーザーができることです。場合`EXCHANGE_S_ENTERPRISE`と表示されている`DISABLED`ユーザーは Exchange Online を使用できないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="07bc7-p116">As you might recall, the service plan is nothing more than the internal programming name for a product; for example,  `OFFICESUBSCRIPTION`, to name one, is the internal programming name for Office Professional Plus. If  `OFFICESUBSCRIPTION` shows up as `SUCCESS` on a user's service plan, then that means that the user is allowed to access Office Professional Plus. If `EXCHANGE_S_ENTERPRISE` is listed as `DISABLED` that means the user can't use Exchange Online.</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="07bc7-210">ユーザーがインストールし、新しい Office Professional Plus インストール中にアクティブにすることができます`OFFICESUBSCRIPTION`では、`PendingInput`の状態です。</span><span class="sxs-lookup"><span data-stu-id="07bc7-210">Users can install and activate a new Office Professional Plus installation while  `OFFICESUBSCRIPTION` is in the `PendingInput` state.</span></span>
  
<span data-ttu-id="07bc7-p117">今こそ、サービスの表示順序が非常に重要です。Windows PowerShell には、リスト内の各エントリにインデックス番号が割り当てられます。最初のエントリは 0 で、次のエントリは、1 というように。結果は、次の表で説明します。</span><span class="sxs-lookup"><span data-stu-id="07bc7-p117">Now is the time where the order in which the services appear is extremely important. Windows PowerShell assigns an index number to each entry in the list. The first entry is 0, the next entry is 1, and so on. The results are explained in the following table:</span></span>
  
|<span data-ttu-id="07bc7-215">インデックス番号。</span><span class="sxs-lookup"><span data-stu-id="07bc7-215">****Index number****</span></span>|<span data-ttu-id="07bc7-216">****サービス プラン****</span><span class="sxs-lookup"><span data-stu-id="07bc7-216">****Service plan****</span></span>|
|:-----|:-----|
|<span data-ttu-id="07bc7-217">0</span><span class="sxs-lookup"><span data-stu-id="07bc7-217">0</span></span>  <br/> | `SWAY` <br/> |
|<span data-ttu-id="07bc7-218">1</span><span class="sxs-lookup"><span data-stu-id="07bc7-218">1</span></span>  <br/> | `INTUNE_O365` <br/> |
|<span data-ttu-id="07bc7-219">2</span><span class="sxs-lookup"><span data-stu-id="07bc7-219">2</span></span>  <br/> | `YAMMER_ENTERPRISE` <br/> |
|<span data-ttu-id="07bc7-220">3</span><span class="sxs-lookup"><span data-stu-id="07bc7-220">3</span></span>  <br/> | `RMS_S_ENTERPRISE` <br/> |
|<span data-ttu-id="07bc7-221">4</span><span class="sxs-lookup"><span data-stu-id="07bc7-221">4</span></span>  <br/> | `OFFICESUBSCRIPTION` <br/> |
|<span data-ttu-id="07bc7-222">5</span><span class="sxs-lookup"><span data-stu-id="07bc7-222">5</span></span>  <br/> | `MCOSTANDARD` <br/> |
|<span data-ttu-id="07bc7-223">6</span><span class="sxs-lookup"><span data-stu-id="07bc7-223">6</span></span>  <br/> | `SHAREPOINTWAC` <br/> |
|<span data-ttu-id="07bc7-224">7</span><span class="sxs-lookup"><span data-stu-id="07bc7-224">7</span></span>  <br/> | `SHAREPOINTENTERPRISE` <br/> |
|<span data-ttu-id="07bc7-225">8</span><span class="sxs-lookup"><span data-stu-id="07bc7-225">8</span></span>  <br/> | `EXCHANGE_S_ENTERPRISE` <br/> |
   
<span data-ttu-id="07bc7-226">ご覧のように、`SWAY`最初のサービスがあるので、インデックス番号 0 が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="07bc7-226">As you can see,  `SWAY` is the first service listed, so it gets assigned index number 0.</span></span>
  
> [!CAUTION]
> <span data-ttu-id="07bc7-p118">理由 0 と 1 がありませんか。プログラミングのことです。プログラミング言語では、インデックスは、項目は「オフセット」配列の先頭からどれだけを指示します。最初の項目*が*のオフセットが 0 であるため、配列の先頭。2 番目の項目は、オフセットが 1 であるため、配列の先頭から 1 個のアイテムです。</span><span class="sxs-lookup"><span data-stu-id="07bc7-p118">Why 0 and not 1? That's a programming thing. In programming languages indices tell you how far an item is "offset" from the beginning of the array. The first item  *is*  the beginning of the array, so its offset is 0. The second item is 1 item from the beginning of the array, so its offset is 1.</span></span>
  
<span data-ttu-id="07bc7-p119">例を試してみましょう。ご Exchange Online を有効になっていないすべてのライセンスを付与されたユーザーの一覧があるとします。次のコマンドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="07bc7-p119">Let's try an example. Suppose we'd like a list of all the licensed users who have not been enabled for Exchange Online. To do that, we can use the following command:</span></span>
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true -and $_.Licenses[0].ServiceStatus[8].ProvisioningStatus -eq "Disabled"}
```

<span data-ttu-id="07bc7-p120">正直なところ、ある暗号のようなほとんどのコマンドのしくみを説明する 1 分を見てみましょう。これは、実際に次の 2 つのコマンドと、最初の部分は非常に単純な: 当社のすべての Office 365 ユーザーのコレクションを取得する**Get MsolUser**コマンドレットを使用しています (ライセンスおよびライセンスのない)。</span><span class="sxs-lookup"><span data-stu-id="07bc7-p120">Admittedly, that's a cryptic-looking little command, so let's take a minute to explain how it works. This is actually a two-part command, and the first part is very simple: we use the **Get-MsolUser** cmdlet to return a collection of all our Office 365 users (both licensed and unlicensed):</span></span>
  
```
Get-MsolUser
```

<span data-ttu-id="07bc7-p121">その情報は、 **Where-object**コマンドレットにパイプします。**場所オブジェクト**では、すべてのユーザー アカウントを経由し、次の条件の両方に一致するこれらのアカウントを探します。</span><span class="sxs-lookup"><span data-stu-id="07bc7-p121">That information is then piped to the **Where-Object** cmdlet. **Where-Object** goes through all the user accounts and looks for those accounts that meet both of the following criteria:</span></span>
  
- <span data-ttu-id="07bc7-p122">**IsLicensed**プロパティは ( `-eq`) `True` ( `$true`)。により、ライセンスのないユーザーを除外します。</span><span class="sxs-lookup"><span data-stu-id="07bc7-p122">The **isLicensed** property is equal to ( `-eq`)  `True` ( `$true`). That enables us to weed out the unlicensed users.</span></span>
    
- <span data-ttu-id="07bc7-p123">**ライセンス [0] の値です。サービス ステータス [8]。ProvisioningStatus**プロパティは ( `-eq`) `Disabled`。当社の当面の目的のこの扱いプロパティ名の重要な部分は、</span><span class="sxs-lookup"><span data-stu-id="07bc7-p123">The value of the **Licenses[0].ServiceStatus[8].ProvisioningStatus** property is equal to ( `-eq`)  `Disabled`. For our immediate purposes, the important part of this unwieldy property name is this:</span></span>
    
     `ServiceStatus[8]`
    
    <span data-ttu-id="07bc7-p124">`[8]` Exchange オンラインのインデックス番号を表します。(それがわかったから数分前にテーブルを参照)。Skype オンライン ビジネスの有効なすべてのユーザーを検索する場合はどうでしょうか。ビジネス オンラインの Skype のインデックス番号は、5、私たちには、この構文を使用するようにします。</span><span class="sxs-lookup"><span data-stu-id="07bc7-p124">The  `[8]` represents the index number for Exchange Online. (We know that from looking at the table a few minutes ago). What if we wanted to find all the users enabled for Skype for Business Online? Well, the index number for Skype for Business Online is 5, so we'd use this syntax:</span></span>
    
     `ServiceStatus[5]`
    
    <span data-ttu-id="07bc7-247">その他も同様です。</span><span class="sxs-lookup"><span data-stu-id="07bc7-247">Etc., etc.</span></span>
    
    <span data-ttu-id="07bc7-p125">ちなみに、`Licenses[0]`ライセンス計画を確認することを示します。1 つのライセンスについては、テスト ドメインであるためこれも関係ありません。ですが、2 つの異なるライセンス計画からライセンスが割り当てられているユーザーがあるとします。その場合は、 `Licenses[0]` 、ライセンスも最初のプランを表すと`Licenses[1]`2 つ目のライセンス プランを表します。</span><span class="sxs-lookup"><span data-stu-id="07bc7-p125">Incidentally,  `Licenses[0]` indicates the licensing plan that we want to look at. Since our test domain only has one licensing plan this doesn't matter much. But suppose we had a user who has been assigned licenses from two different licensing plans. In that case, `Licenses[0]` would represent the first licensing plan, and `Licenses[1]` would represent the second licensing plan.</span></span>
    
    <span data-ttu-id="07bc7-252">ユーザーに割り当てられているライセンス、およびライセンスがリストされる順序を調べるには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="07bc7-252">To find the licenses that are assigned to a user, and the order in which they are listed, run the following command:</span></span>
    
  ```
  Get-MsolUser -UserPrincipalName <Account>  | Format-List DisplayName,Licenses
  ```

<span data-ttu-id="07bc7-p126">どのように動作が発生するかOffice Professional Plus のインデックス番号は、4 です。したがって、このコマンドは、Office Professional Plus を有効になっていないすべてのユーザーの一覧を返します。</span><span class="sxs-lookup"><span data-stu-id="07bc7-p126">Do you see how this all works? The index number for Office Professional Plus is 4; therefore, this command returns a list of all the users who have not been enabled for Office Professional Plus:</span></span>
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true -and $_.Licenses.ServiceStatus[4].ProvisioningStatus -eq "Disabled"}
```

<span data-ttu-id="07bc7-p127">たい場合は*有効な*Office Professional Plus をされているユーザーのリストですか。そうまで有効になって場合、**サービス ステータス**を行うか、`PendingInput`または`Success`。**サービス ステータス**のつまり、等しく*ない*( `-ne`) `Disabled`。行うには、前のコマンドを実行して、スワップ アウトすることを意味する、`-eq`の演算子、`-ne`演算子。</span><span class="sxs-lookup"><span data-stu-id="07bc7-p127">And what if we wanted a list of users who have been  *enabled*  for Office Professional Plus? Well, if you've been enabled then your **ServiceStatus** will either be `PendingInput` or `Success`; in other words, your **ServiceStatus** will *not*  equal ( `-ne`)  `Disabled`. That means all we have to do is take our previous command and swap out the  `-eq` operator for the `-ne` operator:</span></span>
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true -and $_.Licenses.ServiceStatus[4].ProvisioningStatus -ne "Disabled"}
```

<span data-ttu-id="07bc7-p128">言っているように、そのコード可能性がありますされません勝利を収めて多くの利点を競う。真実のように設定、さらに多くのコードを取得できますタングル。たとえばが有効になって両方の Skype のオンライン ビジネス、オンラインの Exchange ユーザーを検索したいとします。</span><span class="sxs-lookup"><span data-stu-id="07bc7-p128">As the saying goes, that code probably won't win many beauty contests. And, truth be told, the code can get even more tangled. For example, suppose we want to look for users who have been enabled for both Skype for Business Online and Exchange Online:</span></span>
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true -and $_.Licenses.ServiceStatus[5].ProvisioningStatus -ne "Disabled" -and $_.Licenses.ServiceStatus[8].ProvisioningStatus -ne "Disabled"}
```

<span data-ttu-id="07bc7-p129">心配 gnarly 方法を次の方法が多すぎる: 重要なことですが、比較的少ない労力でこの情報を取得できます。Office 365 管理センターを使用するこれと同じ情報を取得できませんか。理論的には、[はい] ですが、具体的には、なし。Office 365 管理センターを使用するこれと同じ情報を取得するには、各ユーザーのライセンス情報を一度に 1 人のユーザーを確認し、手動での記録の*X*を有効になっているし、付け加えている必要があります。使用できますが、正直に: 10 または 11 を複数のユーザーであれば、しないことにこれを行う。すぎて手間と時間がかかるをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="07bc7-p129">But don't worry too much about how gnarly that might look: the important thing is that, with relatively little effort, you can retrieve this information. Can't you get at this same information using the Office 365 admin center? In theory, yes but, in practical terms, no. To get at this same information using the Office 365 admin center you'd need to look at the licensing information for each user, one user at a time, and then manually keep track of who'd been enabled for  *X*  and who hadn't. That would work, but let's be honest: if you have more than 10 or 11 users, you're not going to do this. It's way too tedious and time-consuming.</span></span>
  
<span data-ttu-id="07bc7-267">、言うまでもなく、あるため、Windows PowerShell がある: Windows PowerShell を節約するなどの手間と時間のかかるタスクからです。</span><span class="sxs-lookup"><span data-stu-id="07bc7-267">Which, of course, is why we have Windows PowerShell: Windows PowerShell helps save you from tedious and time-consuming tasks such as that.</span></span>
  
<span data-ttu-id="07bc7-268">そう思いますが、最終的なサービスの情報を表示するコマンドです。</span><span class="sxs-lookup"><span data-stu-id="07bc7-268">While we're at it, here's the ultimate command for viewing service information:</span></span>
  
```
Get-MsolUser | Select-Object DisplayName, @{Name="Sway";Expression={$_.Licenses[0].ServiceStatus[0].ProvisioningStatus}}, @{Name="MDM";Expression={$_.Licenses[0].ServiceStatus[1].ProvisioningStatus}}, @{Name="Yammer";Expression={$_.Licenses[0].ServiceStatus[2].ProvisioningStatus}}, @{Name="AD RMS";Expression={$_.Licenses[0].ServiceStatus[3].ProvisioningStatus}}, @{Name="OfficePro";Expression={$_.Licenses[0].ServiceStatus[4].ProvisioningStatus}}, @{Name="Skype";Expression={$_.Licenses[0].ServiceStatus[5].ProvisioningStatus}}, @{Name="OfficeWeb";Expression={$_.Licenses[0].ServiceStatus[6].ProvisioningStatus}}, @{Name="SharePoint";Expression={$_.Licenses[0].ServiceStatus[7].ProvisioningStatus}}, @{Name="Exchange";Expression={$_.Licenses[0].ServiceStatus[8].ProvisioningStatus}} | ConvertTo-Html > "C:\\My Documents\\Service Info.html"
```

<span data-ttu-id="07bc7-p130">非常に複雑に見えるコマンドです。ですが、すべてのユーザーとすべてのサービスのステータスの表示、CSV ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="07bc7-p130">And yes, that's a very crazy-looking command. But it creates a CSV file showing all of your users and all of their service statuses.</span></span>

  
## <a name="see-also"></a><span data-ttu-id="07bc7-271">関連項目</span><span class="sxs-lookup"><span data-stu-id="07bc7-271">See also</span></span>
<span data-ttu-id="07bc7-272"><a name="SeeAlso"> </a></span><span class="sxs-lookup"><span data-stu-id="07bc7-272"></span></span>

<span data-ttu-id="07bc7-273">Office 365 PowerShell でのユーザー管理に関する次の追加のトピックをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="07bc7-273">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="07bc7-274">Office 365 PowerShell を使用してユーザー アカウントを作成する</span><span class="sxs-lookup"><span data-stu-id="07bc7-274">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="07bc7-275">Office 365 PowerShell を使用したユーザー アカウントの削除と復元</span><span class="sxs-lookup"><span data-stu-id="07bc7-275">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="07bc7-276">Office 365 PowerShell でユーザー アカウントをブロックする</span><span class="sxs-lookup"><span data-stu-id="07bc7-276">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="07bc7-277">Office 365 PowerShell を使用してライセンスをユーザー アカウントに割り当てる</span><span class="sxs-lookup"><span data-stu-id="07bc7-277">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="07bc7-278">Office 365 PowerShell を使用してユーザー アカウントからライセンスを削除する</span><span class="sxs-lookup"><span data-stu-id="07bc7-278">Remove licenses from user accounts with Office 365 PowerShell</span></span>](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="07bc7-279">これらの手順で使用するコマンドレットの詳細については、次のトピックをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="07bc7-279">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="07bc7-280">Convertto-html コマンドレット</span><span class="sxs-lookup"><span data-stu-id="07bc7-280">ConvertTo-Html</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113290)
    
- [<span data-ttu-id="07bc7-281">形式リスト</span><span class="sxs-lookup"><span data-stu-id="07bc7-281">Format-List</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113302)
    
- [<span data-ttu-id="07bc7-282">Get-msoluser</span><span class="sxs-lookup"><span data-stu-id="07bc7-282">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="07bc7-283">Select-Object</span><span class="sxs-lookup"><span data-stu-id="07bc7-283">Select-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113387)
    
- [<span data-ttu-id="07bc7-284">Where-Object</span><span class="sxs-lookup"><span data-stu-id="07bc7-284">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

  
## <a name="new-to-office-365"></a><span data-ttu-id="07bc7-285">Office 365 を初めて使用する場合</span><span class="sxs-lookup"><span data-stu-id="07bc7-285">New to Office 365?</span></span>


[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]