---
title: Skype for business と Exchange からハイブリッド先進認証を削除または無効にする
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 11/3/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 5a91b9e3-1508-475b-93e0-710fa5d5cd2d
ms.collection:
- M365-security-compliance
description: ハイブリッドモダン認証 (HMA) を有効にして、現在の環境に適していないことを検出した場合は、hma を無効にすることができます。 この記事では、その方法について説明します。
ms.openlocfilehash: 4df044a8243bc6016f71c31d5b5cba7db901be98
ms.sourcegitcommit: 1d84e2289fc87717f8a9cd12c68ab27c84405348
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2019
ms.locfileid: "30372844"
---
# <a name="removing-or-disabling-hybrid-modern-authentication-from-skype-for-business-and-exchange"></a><span data-ttu-id="bc1e0-104">Skype for business と Exchange からハイブリッド先進認証を削除または無効にする</span><span class="sxs-lookup"><span data-stu-id="bc1e0-104">Removing or disabling Hybrid Modern Authentication from Skype for Business and Exchange</span></span>

<span data-ttu-id="bc1e0-105">ハイブリッドモダン認証 (HMA) を有効にして、現在の環境に適していないことを検出した場合は、hma を無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="bc1e0-105">If you've enabled Hybrid Modern Authentication (HMA) only to find it's unsuitable for your current environment, you can disable HMA.</span></span> <span data-ttu-id="bc1e0-106">この記事では、その方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="bc1e0-106">This article explains how.</span></span>
  
## <a name="who-is-this-article-for"></a><span data-ttu-id="bc1e0-107">この記事の対象読者</span><span class="sxs-lookup"><span data-stu-id="bc1e0-107">Who is this article for?</span></span>

<span data-ttu-id="bc1e0-108">Skype for business online、オンプレミス、または Exchange online またはオンプレミスで先進認証を有効にしている場合に、HMA を無効にするには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="bc1e0-108">If you've enabled Modern Authentication in Skype for Business Online or On-premises, and/or Exchange Online or On-premises and found you need to disable HMA, these steps are for you.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bc1e0-109">skype for business Online またはオンプレミスでトポロジが混在していて、開始する前にサポートされているトポロジを確認する必要がある場合は、「[先進認証でサポートされている skype for business トポロジ](https://technet.microsoft.com/en-us/library/mt803262.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bc1e0-109">See the '[Skype for Business topologies supported with Modern Authentication](https://technet.microsoft.com/en-us/library/mt803262.aspx)' article if you're in Skype for Business Online or On-premises, have a mixed-topology HMA, and need to look at supported topologies before you begin.</span></span>
  
## <a name="how-to-disable-hybrid-modern-authentication-exchange"></a><span data-ttu-id="bc1e0-110">ハイブリッド先進認証を無効にする方法 (Exchange)</span><span class="sxs-lookup"><span data-stu-id="bc1e0-110">How to disable Hybrid Modern Authentication (Exchange)</span></span>

1. <span data-ttu-id="bc1e0-111">**exchange オンプレミス**: exchange 管理シェルを開き、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="bc1e0-111">**Exchange On-premises**: Open the Exchange Management Shell and run the following commands:</span></span> 

```powershell
Set-OrganizationConfig -OAuth2ClientProfileEnabled $false
Set-AuthServer -Identity evoSTS -IsDefaultAuthorizationEndpoint $false
```

2. <span data-ttu-id="bc1e0-112">**exchange online**: リモート PowerShell を使用して[exchange online に接続](https://docs.microsoft.com/en-us/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell)します。</span><span class="sxs-lookup"><span data-stu-id="bc1e0-112">**Exchange Online**: [Connect to Exchange Online](https://docs.microsoft.com/en-us/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) with Remote PowerShell.</span></span> <span data-ttu-id="bc1e0-113">*OAuth2ClientProfileEnabled*フラグを ' false ' にするには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="bc1e0-113">Run the following command to turn your  *OAuth2ClientProfileEnabled*  flag to 'false':</span></span>

```powershell    
Set-OrganizationConfig -OAuth2ClientProfileEnabled:$false
```
    
## <a name="how-to-disable-hybrid-modern-authentication-skype-for-business"></a><span data-ttu-id="bc1e0-114">ハイブリッド先進認証を無効にする方法 (Skype for business)</span><span class="sxs-lookup"><span data-stu-id="bc1e0-114">How to disable Hybrid Modern Authentication (Skype for Business)</span></span>

1. <span data-ttu-id="bc1e0-115">**skype for business オンプレミス**: skype for business 管理シェルで次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="bc1e0-115">**Skype for Business On-premises**: Run the following commands in Skype for Business Management Shell:</span></span>

```powershell
Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity ""
```

2. <span data-ttu-id="bc1e0-116">**skype for business online**: リモート PowerShell を使用して[skype for business online に接続](https://docs.microsoft.com/en-us/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell)します。</span><span class="sxs-lookup"><span data-stu-id="bc1e0-116">**Skype for Business Online**: [Connect to Skype for Business Online](https://docs.microsoft.com/en-us/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell) with Remote PowerShell.</span></span> <span data-ttu-id="bc1e0-117">先進認証を無効にするには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="bc1e0-117">Run the following command to disable Modern Authentication:</span></span>

```powershell    
Set-CsOAuthConfiguration -ClientAdalAuthOverride Disallowed
```

<span data-ttu-id="bc1e0-118">[モダン認証の概要に戻る](hybrid-modern-auth-overview.md)</span><span class="sxs-lookup"><span data-stu-id="bc1e0-118">[Link back to the Modern Authentication overview](hybrid-modern-auth-overview.md) .</span></span> 
  

