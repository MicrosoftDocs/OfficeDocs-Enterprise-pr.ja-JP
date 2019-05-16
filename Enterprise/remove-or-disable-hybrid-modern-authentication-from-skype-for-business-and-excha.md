---
title: Skype for Business および Exchange からのハイブリッド先進認証の削除または無効化
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 11/3/2017
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 5a91b9e3-1508-475b-93e0-710fa5d5cd2d
ms.collection:
- M365-security-compliance
description: ハイブリッドモダン認証 (HMA) を有効にして、現在の環境に適していないことを検出した場合は、HMA を無効にすることができます。 この記事では、その方法について説明します。
ms.openlocfilehash: 011e24c546fede11177e49ce8b36599d7d81d121
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070983"
---
# <a name="removing-or-disabling-hybrid-modern-authentication-from-skype-for-business-and-exchange"></a>Skype for Business および Exchange からのハイブリッド先進認証の削除または無効化

ハイブリッドモダン認証 (HMA) を有効にして、現在の環境に適していないことを検出した場合は、HMA を無効にすることができます。 この記事では、その方法について説明します。
  
## <a name="who-is-this-article-for"></a>この記事の対象読者

Skype for Business Online、オンプレミス、または Exchange Online またはオンプレミスで先進認証を有効にしている場合に、HMA を無効にするには、次の手順を実行します。

> [!IMPORTANT]
> Skype for business Online またはオンプレミスでトポロジが混在していて、開始する前にサポートされているトポロジを確認する必要がある場合は、「[先進認証でサポートされている skype For business トポロジ](https://technet.microsoft.com/en-us/library/mt803262.aspx)」を参照してください。
  
## <a name="how-to-disable-hybrid-modern-authentication-exchange"></a>ハイブリッド先進認証を無効にする方法 (Exchange)

1. **Exchange オンプレミス**: Exchange 管理シェルを開き、次のコマンドを実行します。 

```powershell
Set-OrganizationConfig -OAuth2ClientProfileEnabled $false
Set-AuthServer -Identity evoSTS -IsDefaultAuthorizationEndpoint $false
```

2. **Exchange online**: リモート PowerShell を使用して[exchange online に接続](https://docs.microsoft.com/en-us/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell)します。 *OAuth2ClientProfileEnabled*フラグを ' false ' にするには、次のコマンドを実行します。

```powershell    
Set-OrganizationConfig -OAuth2ClientProfileEnabled:$false
```
    
## <a name="how-to-disable-hybrid-modern-authentication-skype-for-business"></a>ハイブリッド先進認証を無効にする方法 (Skype for Business)

1. **Skype For Business オンプレミス**: skype For Business 管理シェルで次のコマンドを実行します。

```powershell
Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity ""
```

2. **Skype For Business online**: リモート PowerShell を使用して[Skype for business online に接続](https://docs.microsoft.com/en-us/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell)します。 先進認証を無効にするには、次のコマンドを実行します。

```powershell    
Set-CsOAuthConfiguration -ClientAdalAuthOverride Disallowed
```

[モダン認証の概要に戻る](hybrid-modern-auth-overview.md) 
  

