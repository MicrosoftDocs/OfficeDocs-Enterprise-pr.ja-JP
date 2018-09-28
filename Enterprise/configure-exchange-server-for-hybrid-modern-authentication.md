---
title: Exchange Server をオンプレミスで構成して、ハイブリッド先進認証を使用するには
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 3/23/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: cef3044d-d4cb-4586-8e82-ee97bd3b14ad
description: ハイブリッド現代認証 (HMA) より安全なユーザー認証と承認を提供し、Exchange サーバー設置型のハイブリッド展開を利用する id 管理の方法です。
ms.openlocfilehash: cfacb5661ddf4a2ac61054582f0c2043d8fe7a5a
ms.sourcegitcommit: 82219b5f8038ae066405dfb7933c40bd1f598bd0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/14/2018
ms.locfileid: "23975195"
---
# <a name="how-to-configure-exchange-server-on-premises-to-use-hybrid-modern-authentication"></a>Exchange Server をオンプレミスで構成して、ハイブリッド先進認証を使用するには

ハイブリッド現代認証 (HMA) より安全なユーザー認証と承認を提供し、Exchange サーバー設置型のハイブリッド展開を利用する id 管理の方法です。
  
## <a name="fyi"></a>ヒント

始める前に私を呼び出します。
  
- ハイブリッド現代認証\>HMA
    
- オンプレミスの exchange \> EXCH
    
- オンライン交換\>EXO
    
また、*図形ではこの資料はするには '灰色' または '淡色表示されている' つまり、HMA に固有の構成では灰色で表示する要素が含まれていないオブジェクト*にします。 
  
## <a name="enabling-hybrid-modern-authentication"></a>ハイブリッド現代の認証を有効にします。

手段には、HMA を有効にします。
  
1. 開始する前に、前提を満たしていることを確認します。
    
1. 以降、多く**の前提条件**は、両方の Skype ビジネスと Exchange では、[ハイブリッドの最新の認証の概要とでそれを使用するための前提条件、オンプレミス Skype ビジネスおよび Exchange サーバーの](hybrid-modern-auth-overview.md)ための一般的なのです。この資料の手順のいずれかを開始する前にこれを行います。
    
2. 追加設置 web サービスの Url のサービス プリンシパル名 (Spn) として Azure AD で。
    
3. HMA のすべての仮想ディレクトリのことを確認が有効になっています。
    
4. EvoSTS 認証サーバー オブジェクトのチェック
    
5. 為替で HMA を有効にします。
    
 **メモ**Office のバージョンは MA をサポートしますか。[Office 2013 および Office 2016 のクライアント アプリケーションの現在の認証のしくみ](modern-auth-for-office-2013-and-2016.md)を参照してください。
  
## <a name="make-sure-you-meet-all-the-pre-reqs"></a>すべての前提条件を満たしているかどうかを確認します。

ビジネスと Exchange の両方の Skype の一般的な多くの前提条件であるために、[ハイブリッド現代の認証の概要とビジネスと Exchange サーバーの設置型の Skype でそれを使用するための前提条件](hybrid-modern-auth-overview.md)を確認します。この*前に*この資料の手順のいずれかを開始します。 
  
## <a name="add-on-premises-web-service-urls-as-spns-in-azure-ad"></a>設置型は、Azure AD で Spn としてサービスの Url を web に追加します。

Azure AD Spn。 Spn が使っているクライアント コンピューターとデバイスの認証と承認の際に、設置型の web サービスの Url を割り当てるコマンドを実行します。AAD を (内部および外部の名前空間を含む) では、Azure Active Directory (AAD) に設置からの接続に使用されるすべての Url を登録してください。
  
まず、AAD に追加する必要があるすべての Url を収集します。これらのコマンドで設置型を実行します。
  
- Get MapiVirtualDirectory |FL サーバー、\*の url\*
    
- Get WebServicesVirtualDirectory |FL サーバー、\*の url\*
    
- **Get ActiveSyncVirtualDirectory |FL サーバー、\*の url\***
    
- Get OABVirtualDirectory |FL サーバー、\*の url\*
    
AAD での HTTPS サービス プリンシパル名として登録されている可能性がありますクライアント接続の Url を確認します。
  
1. 最初に、[次の手順](https://docs.microsoft.com/en-us/office365/enterprise/powershell/connect-to-office-365-powershell)で AAD に接続します。
    
2. Exchange 関連の Url は次のコマンドを入力します。
    
- Get-MsolServicePrincipal-AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 |-ExpandProperty ServicePrincipalNames を選択します。
    
メモ (および後で比較のスクリーン ショット)、https:// を含める必要があります、このコマンドの出力を行う * 自動検出します。*宛先** と*mail.yourdomain.com*の URL を https://、00000002-0000-0ff1-ce00-000000000000 で始まる Spn のほとんどで構成されますと。オンプレミスで不足しているから https:// の Url がある場合はこの一覧にある特定のレコードを追加する必要があります。 
  
3. このリストの内部および外部 MAPI 要求、EWS、ActiveSync、OAB、および自動検出レコードが表示されない場合、次のコマンドを使用して、追加する必要があります (この例の Url は、'`mail.corp.contoso.com`'と'`owa.contoso.com`'、**独自の Url の例を置換**する必要があるが、): <br/>
```
- $x= Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000   
- $x.ServicePrincipalnames.Add("https://mail.corp.contoso.com/")
- $x.ServicePrincipalnames.Add("https://owa.contoso.com/")
- $x.ServicePrincipalnames.Add("https://eas.contoso.com/")
- Set-MSOLServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $x.ServicePrincipalNames
```
 
4. 手順 2 から Get MsolServicePrincipal コマンドを再度実行して、出力を確認して、新しいレコードが追加されたことを確認します。一覧を比較/スクリーン ショットの前に新しい (必要な場合も、新しいリストのスクリーン ショットを記録用) の Spn の一覧にします。成功した場合は、リスト内の 2 つの新しい Url が表示されます。この例では、移動、Spn の一覧表示されます特定の Url`https://mail.corp.contoso.com`と`https://owa.contoso.com`。 
  
## <a name="verify-virtual-directories-are-properly-configured"></a>仮想ディレクトリは、適切に構成されていることを確認します。

か確認して OAuth が適切に有効になっている次のコマンドを実行して、すべての仮想ディレクトリの Outlook で Exchange を使用します。

```
Get-MapiVirtualDirectory | FL server,\*url\*,\*auth\* 
Get-WebServicesVirtualDirectory | FL server,\*url\*,\*oauth\*
Get-OABVirtualDirectory | FL server,\*url\*,\*oauth\*
Get-AutoDiscoverVirtualDirectory | FL server,\*oauth\*
```

これらの VDirs のそれぞれにチェックすることを確認して**OAuth**が有効になっている、次のようになります (およびを見ることは、'OAuth') です。 
  
 **[PS]C:\Windows\system32\>Get MapiVirtualDirectory |fl サーバー、\*url\*、\*認証\***
  
 **サーバー: EX1**
  
 **InternalUrl。`https://mail.contoso.com/mapi`**
  
 **ExternalUrl。`https://mail.contoso.com/mapi`**
  
 **IISAuthenticationMethods: {Ntlm、OAuth の交渉}**
  
 **InternalAuthenticationMethods: {Ntlm、OAuth の交渉}**
  
 **ExternalAuthenticationMethods: {Ntlm、OAuth の交渉}**
  
OAuth では、任意のサーバーと 4 つの仮想ディレクトリのいずれかに表示されない場合は、続行する前に関連するコマンドを使用して追加する必要があります。
  
## <a name="confirm-the-evosts-auth-server-object-is-present"></a>EvoSTS 認証サーバー オブジェクトが存在であることを確認します。

この最後のコマンドに、オンプレミスの Exchange 管理シェルに戻ります。これで、設置型では、evoSTS の認証プロバイダーのエントリがあるかを検証できます。
  
`Get-AuthServer | where {$_.Name -eq "EvoSts"}`
    
出力の名前 EvoSts、AuthServer を表示する必要があり、'有効' の状態が True にする必要があります。このメッセージが表示されない場合は、ダウンロードして、ハイブリッド構成ウィザードの最新バージョンを実行する必要があります。
  
 **重要です**環境内で Exchange 2010 を実行している場合は、EvoSTS の認証プロバイダーが作成されません。 
  
## <a name="enable-hma"></a>HMA を有効にします。

設置、Exchange 管理シェルで次のコマンドを実行します。

```
Set-AuthServer -Identity EvoSTS -IsDefaultAuthorizationEndpoint $true  
Set-OrganizationConfig -OAuth2ClientProfileEnabled $true
```
    
## <a name="verify"></a>[確認]

HMA を有効にすると、クライアントの次回のログインは、新しい認証フローを使用します。HMA を入れただけではありませんをトリガーする再認証のすべてのクライアントに注意してください。クライアントを再認証に基づく認証トークンや証明書の有効期間があります。
  
また、(Windows の通知トレイ) にも Outlook クライアントのアイコンを右クリックすると同時に、CTRL キーを押し、[接続ステータス] をクリックしてください。に対して、'認証' 型のクライアントの SMTP アドレスを検索 ' ベアラー\*'、OAuth でベアラー トークンを表します。
  
 **メモ**HMA にビジネス用の Skype を構成する必要がありますか。2 つの記事をする必要があります:[サポートされるトポロジ](https://technet.microsoft.com/en-us/library/mt803262.aspx)はの一覧が表示されると[、構成を行う方法](configure-skype-for-business-for-hybrid-modern-authentication.md)を示しています。
  

## <a name="related-topics"></a>関連項目

[ハイブリッド現代の認証の概要とビジネスと Exchange サーバーの設置型の Skype で使用するための前提条件](hybrid-modern-auth-overview.md) 
  

