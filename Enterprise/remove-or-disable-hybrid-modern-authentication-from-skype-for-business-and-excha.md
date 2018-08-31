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
ms.openlocfilehash: fff9599641630386183ab9e1a0b8f597f0ba6e5b
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541755"
---
# <a name="removing-or-disabling-hybrid-modern-authentication-from-skype-for-business-and-exchange"></a>Skype for Business および Exchange からのハイブリッド先進認証の削除または無効化

ハイブリッド現代認証 (HMA) が、現在の環境に適していない場合にのみ、有効にした場合は、HMA を無効にできます。この資料で説明する方法です。
  
## <a name="who-is-this-article-for"></a>この資料は誰ですか。

ビジネス オンラインまたは設置型、Exchange のオンラインまたは設置型の Skype での最新の認証を有効にして、HMA を無効にする必要がありますが場合、は、する手順。
  
 **重要です**ビジネス オンラインまたはオンプレミスの Skype の場合は、'[最新の認証で Skype のビジネス ・ トポロジーがサポートされている](https://technet.microsoft.com/en-us/library/mt803262.aspx)' 記事を参照して、混在トポロジのときなど、ありを開始する前に、サポートされているトポロジを見る必要があります。
  
## <a name="how-to-disable-hybrid-modern-authentication-exchange"></a>ハイブリッド現代認証 (Exchange) を無効にする方法

1. **Exchange 設置**: Exchange 管理シェルを開き、次のコマンドを実行します。 
    
1. セット-OrganizationConfig-OAuth2ClientProfileEnabled $false
    
2. セット ・ AuthServer ・ アイデンティティ evoSTS IsDefaultAuthorizationEndpoint $false
    
2. **Exchange オンライン**: Exchange をリモート PowerShell でオンラインに接続します。'False' に*OAuth2ClientProfileEnabled*フラグを有効にするのには、次のコマンドを実行します。 
    
1. セット-OrganizationConfig-OAuth2ClientProfileEnabled: $false
    
## <a name="how-to-disable-hybrid-modern-authentication-skype-for-business"></a>ハイブリッド現代認証 (ビジネス用の Skype) を無効にする方法

1. **設置型のビジネスの Skype**: Skype のビジネス管理シェルの次のコマンドを実行します。
    
1. セット-CsOAuthConfiguration-ClientAuthorizationOAuthServerIdentity""
    
2. **オンライン ビジネスの Skype**: Skype への接続は、リモート PowerShell でビジネスをオンラインにします。現代の認証を無効にするのには、次のコマンドを実行します。 
    
1. セット CsOAuthConfiguration ClientAdalAuthOverride が許可されていません
    
[現代の認証の概要へのリンク](hybrid-modern-auth-overview.md)です。 
  

