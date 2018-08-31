---
title: Skype for Business をオンプレミスで構成して、ハイブリッド先進認証を使用するには
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 6/4/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 522d5cec-4e1b-4cc3-937f-293570717bc6
description: 現代の認証より安全なユーザー認証と承認を提供する、ビジネス サーバー設置型 Exchange サーバー設置とビジネスの混成のドメインを分割 Skype の Skype の利用は、id 管理の方法です。
ms.openlocfilehash: 48ce10022e384ec88b88c0e8ec038bf201adc707
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541863"
---
# <a name="how-to-configure-skype-for-business-on-premises-to-use-hybrid-modern-authentication"></a>Skype for Business をオンプレミスで構成して、ハイブリッド先進認証を使用するには

現代の認証より安全なユーザー認証と承認を提供する、ビジネス サーバー設置型 Exchange サーバー設置とビジネスの混成のドメインを分割 Skype の Skype の利用は、id 管理の方法です。
  
 **重要です**現代認証 (MA) と、会社または組織で使用する方がよい理由の詳細を把握してもよろしいですか。概要については[このドキュメント](hybrid-modern-auth-overview.md)を確認してください。場合はビジネス ・ トポロジーは、ここに記載されている MA でサポートされているにどのような Skype を把握する必要があります。 
  
 **始める前に**、私を呼び出します。 
  
- 現代の認証\>MA
    
- ハイブリッド現代認証\>HMA
    
- オンプレミスの exchange \> EXCH
    
- オンライン交換\>EXO
    
- 設置型のビジネスの Skype\>デバイス
    
- オンライン ビジネスの Skype \> SFBO
    
また、* この資料の画像が灰色で**は**MA に固有の構成に含まれて表示されている要素のことを意味する '灰色' または '淡色表示されている' オブジェクトです。 * 
  
## <a name="read-the-summary"></a>サマリーを読む

この概要では、プロセスを要するに、実行中に失われた場合は取得可能性がありますし、プロセスであるかを追跡する全体的なチェック項目の手順にします。
  
1. まず、すべての前提条件を満たしていることを確認してください。
    
1. 以降、多く**の前提条件**は、ビジネスと[の前提条件チェックリストの概要記事を参照して](hybrid-modern-auth-overview.md)Exchange の両方の Skype の一般的なのです。この*前に*この資料の手順のいずれかを開始します。 
    
2. ファイル、または OneNote にする必要があるときなどに固有の情報を収集します。
    
3. 有効に現代の認証 EXO (それが入っていない場合既に)。
    
4. 有効に現代の認証 SFBO (それが入っていない場合既に)。
    
5. 設置型の Exchange ハイブリッド現代の認証をオンにします。
    
6. 設置型のビジネスには、Skype のハイブリッド現代の認証を有効にします。
    
次の手順を有効にする MA デバイス、SFBO、EXCH、EXO--は、HMA 構成でのデバイスと SFBO の (EXCH EXO との依存関係を含む) をサポートしているすべての製品に注意してください。つまり、ユーザーが置かれている場合、ハイブリッド (EXO + SFBO、EXO + デバイス、EXCH + SFBO、または EXCH + デバイス) の一部としてメールボックスを作成、完成品のようになります。
  
![ビジネス HMA トポロジの混在の 6 Skype を持っている MA の 4 つのすべての可能な場所。](media/ab89cdf2-160b-49ac-9b71-0160800acfc8.png)
  
ご覧の MA を有効にするのには 4 つの異なる場所があります。最高のユーザー エクスペリエンスでは、これらの場所のすべての 4 つの MA を有効にするをお勧めします。MA は、これらすべての場所でにことはできません、する場合は、MA は、環境に必要な場所でのみを有効にするように手順を調整します。
  
サポートされているトポロジについては、 [MA とビジネス用の Skype のサポートのトピック](https://technet.microsoft.com/en-us/library/mt803262.aspx)を参照してください。 
  
 **重要です**開始する前に、すべての前提条件が満たされていることを再確認してください。その情報については[ここで](hybrid-modern-auth-overview.md)。
  
## <a name="collect-all-hma-specific-info-youll-need"></a>必要がありますすべてのときなどに固有の情報を収集します。

現代の認証を使用する[前提条件](hybrid-modern-auth-overview.md)を満たすことをダブル チェックした後 (上記のメモ参照)、前の手順で、HMA を構成するための必要情報を保持するためにファイルを作成する必要があります。この資料で使用する例: 
  
- **SIP または SMTP ドメイン**
    
  - 例: contoso.com の (Office 365 とフェデレーションでは)
    
- **Tenant ID**
    
  - (Contoso.onmicrosoft.com のログイン) で、Office 365 のテナントを表す GUID です。
    
- **デバイス 2015 CU5 Web サービスの Url**
    
内部および外部の web サービスの URL は、展開のすべてのデバイスの 2015年プールの必要があります。これらを入手するには、ビジネス管理シェルの Skype から次を実行します。
  
Get CsService-web サーバー。選択オブジェクト PoolFqdn、InternalFqdn、ExternalFqdn。FL
  
- 例: 内部。https://lyncwebint01.contoso.com
    
- 例: 外部。https://lyncwebext01.contoso.com
    
Standard Edition サーバーを使用している場合、内部 URL は空白になります。この例では、内部 URL のプールの fqdn を使用します。
  
## <a name="turn-on-modern-authentication-for-exo"></a>EXO の最新の認証を有効にします。

ここに示す手順に従います: [Exchange オンライン: 最新の認証のため、テナントを有効にする方法です](https://social.technet.microsoft.com/wiki/contents/articles/32711.exchange-online-how-to-enable-your-tenant-for-modern-authentication.aspx)。
  
## <a name="turn-on-modern-authentication-for-sfbo"></a>SFBO 用の最新の認証を有効にします。

ここに示す手順に従います:[ビジネス オンラインの Skype: 最新の認証のため、テナントを有効にする](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx)。
  
## <a name="turn-on-hybrid-modern-authentication-for-exchange-on-premises"></a>設置型の Exchange ハイブリッド現代の認証を有効にします。

ここに示す手順に従います:[ハイブリッド現代の認証を使用するオンプレミスの Exchange Server を構成する方法](configure-exchange-server-for-hybrid-modern-authentication.md)です。
  
## <a name="turn-on-hybrid-modern-authentication-for-skype-for-business-on-premises"></a>設置型のビジネスに、Skype のハイブリッド現代の認証を有効に

### <a name="add-on-premises-web-service-urls-as-spns-in-azure-ad"></a>設置型は、Azure AD で Spn としてサービスの Url を web に追加します。

ここで SFBO のサービス ・ プリンシパルとして (収集された以前のバージョン) の Url を追加するのにはコマンドを実行する必要があります。
  
 **メモ**サービス プリンシパル名 (Spn) web サービスを識別して関連付けること (アカウント名またはグループ) などのセキュリティ プリンシパル、権限を持つユーザーの代わりに、サービスが機能するようです。クライアントがサーバーに対して認証を行うを利用情報に格納されている Spn のです。 
  
1. 最初に、[次の手順](https://docs.microsoft.com/en-us/powershell/azure/active-directory/install-adv2?view=azureadps-2.0)で AAD に接続します。
    
2. このコマンドを設置、デバイスの web サービスの Url の一覧を取得するを実行します。
    
  - Get-MsolServicePrincipal-AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 |-ExpandProperty ServicePrincipalNames を選択します。
    
    '00000004' で、AppPrincipalId が始まることに注意してください。これは、オンライン ビジネスの Skype に対応しています。
    
    メモ (および後で比較のスクリーン ショット)、SE と WS の URL が 00000004-0000-0ff1-ce00-000000000000 で始まる Spn のほとんどで構成されますが、このコマンドの出力を行うとします。
    
3. 内部**または**外部設置型からデバイスの Url が表示されない場合 (たとえば、https://lyncwebint01.contoso.comとhttps://lyncwebext01.contoso.com)がこの一覧にある特定のレコードを追加する必要があります。 
    
    [追加] コマンドで、実際の Url を持つ、下の*Url の例*を交換することを確認するには! 
    
  - $x = get MsolServicePrincipal-AppPrincipalId 00000004-0000-0ff1-ce00-000000000000
    
  - $x.ServicePrincipalnames.Add (" *https://lyncwebint01.contoso.com/* ") 
    
  - $x.ServicePrincipalnames.Add (" *https://lyncwebext01.contoso.com/* ") 
    
  - セット-MSOLServicePrincipal-AppPrincipalId の 00000004-0000-0ff1-ce00-000000000000 ・ ServicePrincipalNames $x.ServicePrincipalNames
    
4. 手順 2 から Get MsolServicePrincipal コマンドを再度実行して、出力を確認して、新しいレコードが追加されたことを確認します。一覧を比較/スクリーン ショットの前に新しい (必要な場合も、新しいリストのスクリーン ショットを記録用) の Spn の一覧にします。成功した場合は、リスト内の 2 つの新しい Url が表示されます。この例では、移動、Spn の一覧表示されます特定の Urlhttps://lyncweb01.contoso.comとhttps://autodiscover.contoso.com。
    
### <a name="create-the-evosts-auth-server-object"></a>EvoSTS 認証サーバー オブジェクトを作成します。

ビジネス管理シェルには、Skype で次のコマンドを実行します。
  
- 新しい-CsOAuthServer-の Id evoSTS - MetadataURL https://login.windows.net/common/FederationMetadata/2007-06/FederationMetadata.xml AcceptSecurityIdentifierInformation $true-タイプ AzureAD
    
### <a name="enable-hybrid-modern-authentication"></a>ハイブリッド現代の認証を有効にします。

これは、実際に MA を有効にする手順です。以前のすべての手順は、事前にクライアントの認証フローを変更することがなく実行できます。認証フローを変更する準備ができたらは、ビジネス管理シェルには、Skype でこのコマンドを実行します。 
  
- セット-CsOAuthConfiguration-ClientAuthorizationOAuthServerIdentity evoSTS
    
## <a name="verify"></a>[確認]

HMA を有効にすると、クライアントの次回のログインは、新しい認証フローを使用します。HMA を入れただけではありませんをトリガーする再認証のすべてのクライアントに注意してください。クライアントを再認証に基づく認証トークンや証明書の有効期間があります。
  
HMA に有効にした後に動作しているをテストするには、テスト デバイスの Windows クライアントからサインアウトし、[資格情報を削除] をクリックしてください。もう一度サインインします。現代の認証フローを使用してください、クライアントと '職場または学校' の**Office 365**のプロンプトと表示されます、ログイン アカウント、クライアントがサーバーに接続しログに記録する前に右に表示されます。 
  
'OAuth 機関' の Skype のビジネスのクライアントの構成情報をチェックする必要がありますもします。クライアント コンピューターには、するを右クリックし、Skype ビジネスのアイコンを Windows のトレイで同時に CTRL キーを押しします。構成情報が表示されるメニューでクリックします。デスクトップ上に表示される 'の構成についてはビジネス Skype' ウィンドウに、次の表示します。
  
![Skype の最新の認証を使用してビジネス クライアント用の構成情報は、Lync との EWS OAUTH 機関の URL を示しています。 https://login.windows.net/common/oauth2/authorize。](media/4e54edf5-c8f8-4e7f-b032-5d413b0232de.png)
  
また、(Windows の通知トレイ) にも Outlook クライアントのアイコンを右クリックすると同時に、CTRL キーを押し、[接続ステータス] をクリックしてください。に対して、各種の認証の種類のクライアントの SMTP アドレスを検索 ' ベアラー\*'、OAuth でベアラー トークンを表します。
  
## <a name="related-articles"></a>関連記事

[現代の認証の概要へのリンク](hybrid-modern-auth-overview.md)です。 
  
Skype のビジネス クライアントの最新の認証 (ADAL) を使用する方法を理解する必要がありますか。我々 の手順[は、ここ](https://technet.microsoft.com/en-us/library/mt710548.aspx)です。
  
Exchange Server に表示される次の手順を参照するを選択して、設置、デバイスを使用せずに実行しますか。これらの手順は、ここで使用できます。
  

