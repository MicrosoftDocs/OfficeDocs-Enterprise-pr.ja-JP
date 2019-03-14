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
# <a name="removing-or-disabling-hybrid-modern-authentication-from-skype-for-business-and-exchange"></a>Skype for business と Exchange からハイブリッド先進認証を削除または無効にする

ハイブリッドモダン認証 (HMA) を有効にして、現在の環境に適していないことを検出した場合は、hma を無効にすることができます。 この記事では、その方法について説明します。
  
## <a name="who-is-this-article-for"></a>この記事の対象読者

Skype for business online、オンプレミス、または Exchange online またはオンプレミスで先進認証を有効にしている場合に、HMA を無効にするには、次の手順を実行します。

> [!IMPORTANT]
> skype for business Online またはオンプレミスでトポロジが混在していて、開始する前にサポートされているトポロジを確認する必要がある場合は、「[先進認証でサポートされている skype for business トポロジ](https://technet.microsoft.com/en-us/library/mt803262.aspx)」を参照してください。
  
## <a name="how-to-disable-hybrid-modern-authentication-exchange"></a>ハイブリッド先進認証を無効にする方法 (Exchange)

1. **exchange オンプレミス**: exchange 管理シェルを開き、次のコマンドを実行します。 

```powershell
Set-OrganizationConfig -OAuth2ClientProfileEnabled $false
Set-AuthServer -Identity evoSTS -IsDefaultAuthorizationEndpoint $false
```

2. **exchange online**: リモート PowerShell を使用して[exchange online に接続](https://docs.microsoft.com/en-us/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell)します。 *OAuth2ClientProfileEnabled*フラグを ' false ' にするには、次のコマンドを実行します。

```powershell    
Set-OrganizationConfig -OAuth2ClientProfileEnabled:$false
```
    
## <a name="how-to-disable-hybrid-modern-authentication-skype-for-business"></a>ハイブリッド先進認証を無効にする方法 (Skype for business)

1. **skype for business オンプレミス**: skype for business 管理シェルで次のコマンドを実行します。

```powershell
Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity ""
```

2. **skype for business online**: リモート PowerShell を使用して[skype for business online に接続](https://docs.microsoft.com/en-us/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell)します。 先進認証を無効にするには、次のコマンドを実行します。

```powershell    
Set-CsOAuthConfiguration -ClientAdalAuthOverride Disallowed
```

[モダン認証の概要に戻る](hybrid-modern-auth-overview.md) 
  

