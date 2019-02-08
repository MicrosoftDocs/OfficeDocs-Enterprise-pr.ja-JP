---
title: Skype for Business および Exchange からのハイブリッド先進認証の削除または無効化
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
description: ハイブリッド現代認証 (HMA) が、現在の環境に適していない場合にのみ、有効にした場合は、HMA を無効にできます。この資料で説明する方法です。
ms.openlocfilehash: 802add6295edffe3ec80e70e9bd70663479ec61a
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2019
ms.locfileid: "25359029"
---
# <a name="removing-or-disabling-hybrid-modern-authentication-from-skype-for-business-and-exchange"></a><span data-ttu-id="24991-104">Skype for Business および Exchange からのハイブリッド先進認証の削除または無効化</span><span class="sxs-lookup"><span data-stu-id="24991-104">Removing or disabling Hybrid Modern Authentication from Skype for Business and Exchange</span></span>

<span data-ttu-id="24991-p102">ハイブリッド現代認証 (HMA) が、現在の環境に適していない場合にのみ、有効にした場合は、HMA を無効にできます。この資料で説明する方法です。</span><span class="sxs-lookup"><span data-stu-id="24991-p102">If you've enabled Hybrid Modern Authentication (HMA) only to find it's unsuitable for your current environment, you can disable HMA. This article explains how.</span></span>
  
## <a name="who-is-this-article-for"></a><span data-ttu-id="24991-107">この資料は誰ですか。</span><span class="sxs-lookup"><span data-stu-id="24991-107">Who is this article for?</span></span>

<span data-ttu-id="24991-108">ビジネス オンラインまたは設置型、Exchange のオンラインまたは設置型の Skype での最新の認証を有効にして、HMA を無効にする必要がありますが場合、は、する手順。</span><span class="sxs-lookup"><span data-stu-id="24991-108">If you've enabled Modern Authentication in Skype for Business Online or On-premises, and/or Exchange Online or On-premises and found you need to disable HMA, these steps are for you.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="24991-109">ビジネス オンラインまたはオンプレミスの Skype の場合は、'[最新の認証で Skype のビジネス ・ トポロジーがサポートされている](https://technet.microsoft.com/en-us/library/mt803262.aspx)' 記事を参照して、混在トポロジのときなど、ありを開始する前に、サポートされているトポロジを見る必要があります。</span><span class="sxs-lookup"><span data-stu-id="24991-109">See the '[Skype for Business topologies supported with Modern Authentication](https://technet.microsoft.com/en-us/library/mt803262.aspx)' article if you're in Skype for Business Online or On-premises, have a mixed-topology HMA, and need to look at supported topologies before you begin.</span></span>
  
## <a name="how-to-disable-hybrid-modern-authentication-exchange"></a><span data-ttu-id="24991-110">ハイブリッド現代認証 (Exchange) を無効にする方法</span><span class="sxs-lookup"><span data-stu-id="24991-110">How to disable Hybrid Modern Authentication (Exchange)</span></span>

1. <span data-ttu-id="24991-111">**Exchange 設置**: Exchange 管理シェルを開き、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="24991-111">**Exchange On-premises**: Open the Exchange Management Shell and run the following commands:</span></span> 

```powershell
Set-OrganizationConfig -OAuth2ClientProfileEnabled $false
Set-AuthServer -Identity evoSTS -IsDefaultAuthorizationEndpoint $false
```

2. <span data-ttu-id="24991-p103">**Exchange オンライン**: リモート PowerShell を使用して[オンラインの Exchange への接続](https://docs.microsoft.com/en-us/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell)をします。'False' に*OAuth2ClientProfileEnabled*フラグを有効にするのには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="24991-p103">**Exchange Online**: [Connect to Exchange Online](https://docs.microsoft.com/en-us/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) with Remote PowerShell. Run the following command to turn your  *OAuth2ClientProfileEnabled*  flag to 'false':</span></span>

```powershell    
Set-OrganizationConfig -OAuth2ClientProfileEnabled:$false
```
    
## <a name="how-to-disable-hybrid-modern-authentication-skype-for-business"></a><span data-ttu-id="24991-114">ハイブリッド現代認証 (ビジネス用の Skype) を無効にする方法</span><span class="sxs-lookup"><span data-stu-id="24991-114">How to disable Hybrid Modern Authentication (Skype for Business)</span></span>

1. <span data-ttu-id="24991-115">**設置型のビジネスの Skype**: Skype のビジネス管理シェルの次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="24991-115">**Skype for Business On-premises**: Run the following commands in Skype for Business Management Shell:</span></span>

```powershell
Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity ""
```

2. <span data-ttu-id="24991-p104">**オンライン ビジネスの Skype**: リモート PowerShell を使用して[オンライン ビジネスの Skype への接続](https://docs.microsoft.com/en-us/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell)をします。現代の認証を無効にするのには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="24991-p104">**Skype for Business Online**: [Connect to Skype for Business Online](https://docs.microsoft.com/en-us/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell) with Remote PowerShell. Run the following command to disable Modern Authentication:</span></span>

```powershell    
Set-CsOAuthConfiguration -ClientAdalAuthOverride Disallowed
```

<span data-ttu-id="24991-118">[現代の認証の概要へのリンク](hybrid-modern-auth-overview.md)です。</span><span class="sxs-lookup"><span data-stu-id="24991-118">[Link back to the Modern Authentication overview](hybrid-modern-auth-overview.md) .</span></span> 
  

