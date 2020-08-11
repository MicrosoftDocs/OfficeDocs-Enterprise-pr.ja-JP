---
title: Skype for Business をオンプレミスで構成して、ハイブリッド先進認証を使用するには
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/3/2019
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 522d5cec-4e1b-4cc3-937f-293570717bc6
ms.collection:
- M365-security-compliance
f1.keywords:
- NOCSH
description: ハイブリッド先進認証 (HMA) を使用するように Skype for Business を構成する方法について説明します。これにより、ユーザーの認証と承認をより安全に提供できます。
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: e82325281341d35454161f03873acc30898ad536
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/10/2020
ms.locfileid: "46605763"
---
# <a name="how-to-configure-skype-for-business-on-premises-to-use-hybrid-modern-authentication"></a>Skype for Business をオンプレミスで構成して、ハイブリッド先進認証を使用するには

*この記事は、Microsoft 365 Enterprise および Office 365 Enterprise の両方に適用されます。*

先進認証は、ユーザーの認証と承認をより安全に提供する id 管理の方法であり、オンプレミスの Skype for Business server とオンプレミスの Exchange server、およびスプリットドメイン Skype for Business ハイブリッドで利用できます。
  
 **重要**モダン認証 (MA) の詳細と、会社や組織での使用を希望する理由は何ですか。 概要については、[このドキュメント](hybrid-modern-auth-overview.md)を確認してください。 MA でサポートされている Skype for Business のトポロジについて知る必要がある場合は、ここで説明します。
  
 **開始する前に**、次の用語を使用します。
  
- モダン認証 (MA)

- ハイブリッド先進認証 (HMA)

- Exchange オンプレミス (EXCH)

- Exchange Online (EXO)

- Skype for Business オンプレミス (SFB)

- Skype for Business Online (SFBO)

また、この記事の図に淡色表示されている、または淡色表示されているオブジェクトがある場合、グレーの要素は MA 固有の構成**に含まれてい**ないことを意味します。
  
## <a name="read-the-summary"></a>概要の読み取り

この概要では、実行中に失われる可能性のある手順にプロセスを分解します。また、プロセスのどこで作業しているかを全体的なチェックリストに記録することをお勧めします。
  
1. 最初に、すべての前提条件を満たしていることを確認してください。

1. Skype for Business と Exchange の両方に共通の**前提条件**が多数存在するため、[事前要件チェックリストの概要記事を参照してください](hybrid-modern-auth-overview.md)。 この手順を実行する*前*に、この記事の手順を開始する必要があります。

1. ファイルまたは OneNote で必要な HMA 固有の情報を収集します。

1. EXO のモダン認証を有効にします (まだ有効になっていない場合)。

1. SFBO の先進認証を有効にします (まだ有効になっていない場合)。

1. Exchange on-premises のハイブリッド先進認証を有効にします。

1. オンプレミスの Skype for Business のハイブリッドモダン認証を有効にします。

次の手順では、SFB、SFBO、EXCH、EXO に対して MA を有効にします。これは、SFB および SFBO (EXCH/EXO への依存関係を含む) の HMA 構成に参加できるすべての製品です。 言い換えると、ユーザーがハイブリッドの一部 (EXO + SFBO、EXO + SFB、EXCH + SFBO、または EXCH + SFB) で作成したメールボックスを持つ場合、完成した製品は次のようになります。
  
![混在した6つの Skype for business HMA トポロジは、可能なすべての場所で MA になります。](media/ab89cdf2-160b-49ac-9b71-0160800acfc8.png)
  
MA を有効にするには、4つの異なる場所が存在します。 最適なユーザー環境を実現するには、これらのすべての場所で MA をオンにすることをお勧めします。 これらのすべての場所で MA をオンにできない場合は、環境に必要な場所で MA のみを有効にするように手順を調整します。
  
サポートされているトポロジについては、「 [Skype for business での Skype For business のサポート」を](https://technet.microsoft.com/library/mt803262.aspx)参照してください。
  
 **重要**開始する前に、すべての前提条件を満たしていることをもう一度確認してください。 [ハイブリッド先進認証の概要と前提条件](hybrid-modern-auth-overview.md)に関する情報がわかります。
  
## <a name="collect-all-hma-specific-info-youll-need"></a>必要なすべての HMA 固有の情報を収集する

先進認証を使用するための[前提条件](hybrid-modern-auth-overview.md)を満たしていることを再度確認した後、前の手順で HMA を構成するために必要な情報を保持するためのファイルを作成しておく必要があります。 この記事で使用されている例:
  
- **SIP/SMTP ドメイン**

  - 渡し. contoso.com (Office 365 と連携している)

- **テナント ID**

  - Office 365 テナント (contoso.onmicrosoft.com のログイン時) を表す GUID。

- **SFB 2015 CU5 Web サービスの Url**

展開されたすべての SfB 2015 プールについて、内部および外部の web サービス Url が必要になります。 これらを取得するには、Skype for Business 管理シェルから次のように実行します。
  
```powershell
Get-CsService -WebServer | Select-Object PoolFqdn, InternalFqdn, ExternalFqdn | FL
```

- 渡し. 社外https://lyncwebint01.contoso.com

- 渡し. 社外https://lyncwebext01.contoso.com

Standard Edition サーバーを使用している場合、内部 URL は空白になります。 この場合は、内部 URL にプールの fqdn を使用します。
  
## <a name="turn-on-modern-authentication-for-exo"></a>EXO の先進認証を有効にする

「 [Exchange Online: テナントの先進認証を有効にする方法](https://social.technet.microsoft.com/wiki/contents/articles/32711.exchange-online-how-to-enable-your-tenant-for-modern-authentication.aspx)」の手順に従います。
  
## <a name="turn-on-modern-authentication-for-sfbo"></a>SFBO の先進認証を有効にする

「 [Skype For Business Online: テナントで先進認証を有効にする](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx)」の手順に従ってください。
  
## <a name="turn-on-hybrid-modern-authentication-for-exchange-on-premises"></a>Exchange on-premises のハイブリッド先進認証を有効にする

この記事の手順に従ってください:[ハイブリッド先進認証を使用するように Exchange Server をオンプレミスで構成する方法](configure-exchange-server-for-hybrid-modern-authentication.md)。
  
## <a name="turn-on-hybrid-modern-authentication-for-skype-for-business-on-premises"></a>オンプレミスの Skype for Business のハイブリッドモダン認証を有効にする

### <a name="add-on-premises-web-service-urls-as-spns-in-azure-active-directory"></a>Azure Active Directory の Spn としてオンプレミスの web サービス Url を追加する

ここで、SFBO のサービスプリンシパルとして、前の手順で収集した Url を追加するコマンドを実行する必要があります。
  
 **メモ**サービスプリンシパル名 (Spn) は、web サービスを識別し、それをセキュリティプリンシパル (アカウント名やグループなど) に関連付けて、サービスが権限のあるユーザーの代理として機能できるようにします。 クライアントがサーバーに対して認証を行うと、Spn に含まれる情報が利用されます。
  
1. 最初に、[これらの手順](https://docs.microsoft.com/powershell/azure/active-directory/overview?view=azureadps-1.0)を使用して Azure Active Directory (azure AD) に接続します。

2. このコマンドをオンプレミスで実行して、SFB web サービス Url の一覧を取得します。

   AppPrincipalId はから始まることに注意して `00000004` ください。 これは、Skype for Business Online に対応しています。

   このコマンドの出力では、SE と WS の URL が含まれていますが、ほとんどは、で始まる Spn から構成されていますのでメモを取り `00000004-0000-0ff1-ce00-000000000000/` ます。

```powershell
Get-MsolServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 | Select -ExpandProperty ServicePrincipalNames
```

3. オンプレミスの内部**または**外部の Sfb url が欠落している場合 (たとえば、である場合)、 https://lyncwebint01.contoso.com それらのレコードを https://lyncwebext01.contoso.com) このリストに追加する必要があります。

    次の*url の例は*、Add コマンドで実際の url に置き換えてください。
  
```powershell
$x= Get-MsolServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000
$x.ServicePrincipalnames.Add("https://lyncwebint01.contoso.com/")
$x.ServicePrincipalnames.Add("https://lyncwebext01.contoso.com/")
Set-MSOLServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $x.ServicePrincipalNames
```
  
4. 手順2で**new-msolserviceprincipal**コマンドを再度実行し、出力を調べて、新しいレコードが追加されたことを確認します。 リストまたはスクリーンショットを、Spn の新しいリストの前に比較します。 また、レコードの新しいリストのスクリーンショットを作成することもできます。 成功した場合は、2つの新しい Url が一覧に表示されます。 この例では、Spn の一覧に特定の Url とが含まれるようになりました https://lyncwebint01.contoso.com https://lyncwebext01.contoso.com/ 。

### <a name="create-the-evosts-auth-server-object"></a>EvoSTS 認証サーバーオブジェクトを作成する

Skype for Business 管理シェルで次のコマンドを実行します。
  
```powershell
New-CsOAuthServer -Identity evoSTS -MetadataURL https://login.windows.net/common/FederationMetadata/2007-06/FederationMetadata.xml -AcceptSecurityIdentifierInformation $true -Type AzureAD
```

### <a name="enable-hybrid-modern-authentication"></a>ハイブリッド先進認証を有効にする

これは、実際に MA を有効にする手順です。 以前のすべての手順は、クライアント認証フローを変更せずに、前もって実行することができます。 認証フローを変更する準備ができたら、Skype for Business 管理シェルで次のコマンドを実行します。

```powershell
Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity evoSTS
```

## <a name="verify"></a>ことを確認

HMA を有効にすると、クライアントの次のログインは新しい認証フローを使用します。 HMA を有効にするだけでは、クライアントの再認証はトリガーされないことに注意してください。 クライアントは、認証トークンまたは証明書の有効期間に基づいて再認証を行います。
  
HMA が機能していることを確認した後で、その機能が動作していることをテストするには、テスト用の SFB Windows クライアントからサインアウトし、[資格情報の削除] をクリックします。 もう一度サインインします。 クライアントは、最新の認証フローを使用するようになり、ログインに ' 職場または学校のアカウントに対する**Office 365**プロンプトが含まれるようになりました。これで、クライアントがサーバーに接続してログインする前に表示されます。
  
「OAuth Authority」については、「Skype for Business クライアント」の「構成情報」も確認してください。 クライアントコンピューターでこれを行うには、CTRL キーを押しながら、Windows 通知トレイの [Skype for Business] アイコンを右クリックします。 表示されるメニューの [**構成情報**] をクリックします。 デスクトップに表示される [Skype for Business の構成情報] ウィンドウで、次のものを探します。
  
![モダン認証を使用した Skype for Business クライアントの構成情報は、の Lync および EWS OAUTH Authority の URL を示して https://login.windows.net/common/oauth2/authorize います。](media/4e54edf5-c8f8-4e7f-b032-5d413b0232de.png)
  
また、CTRL キーを押しながら Outlook クライアントのアイコンを右クリックし、[接続の状態] をクリックしても同じことを行う必要があります。 OAuth で使用されるベアラートークンを表す、認証の種類 ' ベアラー ' に対してクライアントの SMTP アドレスを検索し \* ます。
  
## <a name="related-articles"></a>関連記事

[モダン認証の概要に戻る](hybrid-modern-auth-overview.md)
  
Skype for Business クライアントで先進認証 (ADAL) を使用する方法を知る必要がありますか。 [ここでは](https://technet.microsoft.com/library/mt710548.aspx)、手順を示しました。
