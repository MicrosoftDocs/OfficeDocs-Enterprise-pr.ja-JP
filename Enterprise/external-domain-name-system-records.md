---
title: Office 365 の外部ドメイン ネーム システムのレコード
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 2/14/2018
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: c0531a6f-9e25-4f2d-ad0e-a70bfef09ac0
description: '概要: Office 365 の展開を計画するときに使用する DNS レコードのリファレンス リスト。'
ms.openlocfilehash: c172275e43b4703172f58287c086562da352f5e9
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487260"
---
# <a name="external-domain-name-system-records-for-office-365"></a>Office 365 の外部ドメイン ネーム システムのレコード

 **概要:** Office 365 の展開を計画するときに使用する DNS レコードのリファレンス リスト。
  
|||
|:-----|:-----|
|![ドメイン](media/e05b1c78-1df0-4200-ba40-6e26b7ead68f.png)|**Office 365 組織のカスタマイズされた DNS レコードのリストを表示するには** Office 365 のドメイン用に [Office 365 DNS レコードを作成するために必要な情報を見つける](https://support.office.microsoft.com/ja-JP/article/Gather-the-information-you-need-to-create-Office-365-DNS-records-77f90d4a-dc7f-4f09-8972-c1b03ea85a67)ことができます。<br/> **GoDaddy や eNom などのドメインの DNS ホストでこれらのレコードを追加するための手順が必要な場合** [多くの一般的な DNS ホストでの詳しい操作手順へのリンクをご覧ください](https://go.microsoft.com/fwlink/?LinkId=286745)。<br/> 「[Office 365 のネットワーク計画とパフォーマンス チューニング](https://aka.ms/tune)」**に戻ります**。  <br/> |

 **そのまま残って自分のカスタムの展開用のリファレンス リストを使用する場合** 以下のリストは、Office 365 のカスタム展開用のリファレンスとして使用されます。組織に適用するレコードを選択して、適切な値を入力する必要があります。
  
SPF と MX レコードは、最も見つけ出すのが困難であることがよくあります。この記事の最後にある、SPF レコードのガイダンスを更新しました。*ドメインに対して持つことができる SPF レコードは 1 つのみである*と覚えておくことが重要です。MX レコードは複数持つことができますが、メール配信の際問題を引き起こすことがあります。1 つの MX レコードを持つことで電子メールを 1 つのメール システムに配信すると、起こりうる問題の多くを取り除くことができます。
  
以下のセクションは Office 365 のサービスごとに編成されています。ドメインに対する Office 365 DNS レコードのカスタマイズされたリストを表示するには、Office 365 にサインインして、「[Office 365 の DNS レコードの作成に必要な情報を収集する](https://support.office.com/article/77f90d4a-dc7f-4f09-8972-c1b03ea85a67)」をご覧ください。
  
## <a name="external-dns-records-required-for-office-365-core-services"></a>Office 365 に必要な外部の DNS レコード (コア サービス)
<a name="BKMK_ReqdCore"> </a>

すべての Office 365 のお客様は、外部の DNS に 2 つのレコードを追加する必要があります。最初の CNAME レコードは、Office 365 がワークステーションに適切な ID プラットフォームで認証を行うよう指定できるようにします。2 番目の必須レコードは、ドメイン名を所有していることを証明します。 
  
||||
|:-----|:-----|:-----|
|**DNS レコード** <br/> |**用途** <br/> |**使用する値** <br/> |
|**CNAME** <br/> **(スイート)** <br/> |正しい ID プラットフォームへの認証を指示するために Office 365 で使用されます。[詳細情報](https://go.microsoft.com/fwlink/p/?LinkId=322005) <br/> [!NOTE]  この CNAME は、21Vianet が運営する Office 365 にのみ適用されます。   |**エイリアス:** msoid  <br/> **対象:** clientconfig.microsoftonline-p.net  <br/> |
|**TXT** <br/> **(ドメインの確認)** <br/> |このレコードは、ドメインを所有していることを確認するためだけに Office 365 で使用されます。他のものには影響しません。  <br/> |**ホスト:** @ (または、一部の DNS ホスティング プロバイダーでは自分のドメイン名)  <br/> **TXT 値:** Office 365 "_から提供されるテキスト文字列_"  <br/> このレコードを作成するために使用する値は、Office 365 の**ドメイン セットアップ** ウィザードで指定されます。  <br/> |

## <a name="external-dns-records-required-for-email-in-office-365-exchange-online"></a>Office 365 でのメールに必要な外部 DNS レコード (Exchange Online)
<a name="BKMK_ReqdCore"> </a>

Office 365 でのメールには、複数の異なるレコードが必要です。すべてのお客様が使用する 3 つの主要なレコードは、自動検出、MX、および SPF レコードです。
  
- **自動検出レコード**では、クライアント コンピューターは自動的に Exchange を検索し、クライアントを正しく構成することができます。

- **MX レコード**は、ドメインの電子メールの送信先を他のメール システムに伝えます。"*ドメインの MX レコードを更新することによって、Office 365 へのメールを変更すると、そのドメインに送信されるすべてのメールは、Office 365 に送信されるようになります。*" (いくつかのメール アドレスを Office 365 に切り替えたいだけの場合は、[カスタム ドメインの少数のメール アドレスで Office 365 をパイロット](https://support.office.com/article/39cee536-6a03-40cf-b9c1-f301bb6001d7)できます。)

- **SPF の TXT レコード**は、受信側の電子メール システムが、電子メールの送信側のサーバーが承認されていることを検証するために使用します。これにより、メールのスプーフィングやフィッシングなどの問題を回避できます。レコードに含める必要があるものについて詳しくは、この記事の「[SPF に必要な外部 DNS レコード](external-domain-name-system-records.md#BKMK_SPFrecords)」をご覧ください。

Exchange フェデレーションを使用しているメールのお客様は、表の一番下に一覧表示されている追加の CNAME および TXT レコードも必要です。
  
||||
|:-----|:-----|:-----|
|**DNS レコード** <br/> |**用途** <br/> |**使用する値** <br/> |
|**CNAME** <br/> **(Exchange Online)** <br/> |このレコードを使用すると、Outlook クライアントが自動検出サービスを使用して Exchange Online サービスに簡単に接続できます。自動検出は、正しい Exchange Server ホストを自動的に検出し、ユーザーの Outlook を構成します。  <br/> |**エイリアス:** Autodiscover  <br/> **対象:** autodiscover.outlook.com  <br/> |
|**MX** <br/> **(Exchange Online)** <br/> |ドメインへの受信メールを Office 365 の Exchange Online サービスへ送信します。  <br/> [!NOTE] 電子メールが Exchange Online に流れたら、古いシステムを指定している MX レコードを削除する必要があります。   |**ドメイン:** 例: contoso.com  <br/> **対象電子メール サーバー:** \<MX トークン\>.mail.protection.outlook.com  <br/> **優先度:** その他すべての MX レコードより下 (これにより、メールが Exchange Online に確実に配信されます) - 例: 1 または "low"  <br/>  次の手順に従って \<MX トークン\> を検索します。  <br/>  Office 365 にサインインし、[Office 365 管理] \> [ドメイン] に移動します。  <br/>  ドメインの [アクション] 列で [問題の修正] を選択します。  <br/>  [MX レコード] セクションで、[何を修正しますか?] を選択します。  <br/>  MX レコードを更新するには、このページに表示される指示に従います。  <br/> [MX 優先度とは何ですか。](https://go.microsoft.com/fwlink/p/?LinkId=396471) <br/> |
|**SPF (TXT)** <br/> (Exchange Online)  <br/> |これは、自分のドメインを他人が使用してスパムなどの悪意のある電子メールを送信するのを防ぐのに役立ちます。Sender policy framework (SPF) レコードは、自分のドメインからメールを送信することを許可されているサーバーを特定することによって動作します。  <br/> |[SPF に必要な外部 DNS レコード](external-domain-name-system-records.md#BKMK_SPFrecords) <br/> |
|**TXT** <br/> **(Exchange フェデレーション)** <br/> |ハイブリッド展開のために Exchange フェデレーションに使用します。  <br/> |**TXT レコード 1:** たとえば、contoso.com および関連するカスタム生成されたもの、ドメイン証明ハッシュ テキスト (たとえば、Y96nu89138789315669824)  <br/> **TXT レコード 2:** たとえば、exchangedelegation.contoso.com および関連するカスタム生成されたもの、ドメイン証明ハッシュ テキスト (たとえば、Y3259071352452626169)  <br/> |
|**CNAME** <br/> ** (Exchange フェデレーション) ** <br/> |Exchange フェデレーションを使用している場合、自動検出サービスを使用して Exchange Online サービスに簡単に接続するために Outlook クライアントを支援します。自動検出は、自動的に正しい Exchange Server ホストを見つけ、Outlook を構成します。  <br/> |**エイリアス:** 例: Autodiscover.service.contoso.com  <br/> **対象:** autodiscover.outlook.com  <br/> |

## <a name="external-dns-records-required-for-skype-for-business-online"></a>Skype for Business Online に必要な外部 DNS レコード
<a name="BKMK_ReqdCore"> </a>

「[Office 365 の URL と IP アドレスの範囲](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2#BKMK_LYO)」でネットワークが正しく構成されていることを確認するときに実行する必要のある具体的な手順があります。
  
||||
|:-----|:-----|:-----|
|**DNS レコード** <br/> |**用途** <br/> |**使用する値** <br/> |
|**SRV** <br/> **(Skype for Business Online)** <br/> |SIP フェデレーションを有効にすることで、Office 365 ドメインが外部クライアントとインスタント メッセージング (IM) 機能を共有することができます。詳しくは、「[Office 365 の URL と IP アドレスの範囲 ](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2#BKMK_LYO)」をご覧ください。<br/> |**サービス:** _sipfederationtls  <br/> **プロトコル:** _TCP  <br/> **優先度:** 100  <br/> **重み:** 1  <br/> **ポート:** 5061  <br/> **対象:** Sipfed.online.lync.com  <br/> > [!NOTE]> ファイアウォールまたはプロキシ サーバーが外部 DNS の SRV ルックアップをブロックする場合、内部 DNS レコードにこのレコードを追加する必要があります。   |
|**SRV** <br/> **(Skype for Business Online)** <br/> |Lync クライアント間の情報の流れを調整するために Skype for Business で使用します。  <br/> |**サービス:** _sip  <br/> **プロトコル:** _TLS  <br/> **優先度:** 100  <br/> **重み:** 1  <br/> **ポート:** 443  <br/> **対象:** sipdir.online.lync.com  <br/> |
|**CNAME** <br/> **(Skype for Business Online)** <br/> |Skype for Business Online サービスを見つけてサインインするのを支援するために Lync クライアントで使用します。  <br/> |**エイリアス:** sip  <br/> **対象:** sipdir.online.lync.com  <br/> 詳しくは、「[Office 365 URL および IP アドレス範囲](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2#BKMK_LYO)」を参照してください。  <br/> |
|**CNAME** <br/> **(Skype for Business Online)** <br/> |Skype for Business Online サービスを見つけてサインインするのを支援するために Lync モバイル クライアントで使用します。  <br/> |**エイリアス:** lyncdiscover  <br/> **対象:** webdir.online.lync.com  <br/> |

## <a name="external-dns-records-required-for-sharepoint-online"></a>SharePoint Online に必要な外部 DNS レコード
<a name="BKMK_ReqdCore"> </a>

組織が SharePoint Online を使用して外部ユーザーにメールを送信する場合、SharePoint Online は DNS レコードのみが必要です。この場合は、メールが配信されるように [SPF に必要な外部 DNS レコード](external-domain-name-system-records.md#BKMK_SPFrecords)を設定します。
  
## <a name="external-dns-records-required-for-office-365-single-sign-on"></a>Office 365 シングル サインオンに必要な外部 DNS レコード
<a name="BKMK_ReqdCore"> </a>

||||
|:-----|:-----|:-----|
|**DNS レコード** <br/> |**用途** <br/> |**使用する値** <br/> |
|**ホスト (A)** <br/> |シングル サインオン (SSO) に使用されます。これによって社外ユーザー (必要に応じて、オンプレミスのユーザー) にエンドポイントを提供し、Active Directory フェデレーション サービス (AD FS)、フェデレーション サーバー プロキシ、または負荷分散仮想 IP (VIP) に接続できるようにします。  <br/> |**対象:** 例: sts.contoso.com  <br/> |

## <a name="external-dns-records-required-for-spf"></a>SPF に必要な外部 DNS レコード
<a name="BKMK_SPFrecords"> </a>

> [!IMPORTANT]
> SPF はスプーフィングを防止するために設計されていますが、SPF で防御できないスプーフィングの手法があります。これらから保護するために、SPF をセットアップすると、Office 365 用に DKIM と DMARC も構成する必要があります。始めるには「[Use DKIM to validate outbound email sent from your domain in Office 365](https://technet.microsoft.com/ja-JP/library/mt695945%28v=exchg.150%29.aspx)」をご覧ください。次は、「[Use DMARC to validate email in Office 365](https://technet.microsoft.com/ja-JP/library/mt734386%28v=exchg.150%29.aspx)」を参照してください。
  
SPF レコードは、他人が自分のドメインを使用してスパムなどの悪意のある電子メールを送信するのを防ぐのに役立つ TXT レコードです。Sender policy framework (SPF) レコードは、自分のドメインからメールを送信することを許可されているサーバーを特定することによって動作します。
  
ドメインに対して持つことができる SPF レコード (つまり、SPF を定義する TXT レコード) は 1 つだけです。その 1 つのレコードはいくつかの異なる管理対象を持つことができますが、結果の合計 DNS 参照は 10 より多くてもかまいません (これは、サービス拒否攻撃を防ぐのに役立ちます)。環境に適した SPF レコード値の作成または更新については、以下の表と他の例をご覧ください。
  
### <a name="structure-of-an-spf-record"></a>SPF レコードの構造

すべての SPF レコードには 3 つの部分 (SPF レコードである宣言、電子メールを送信するドメイン & IP アドレス、および強制ルール) があります。有効な SPF レコードには 3 つすべてが必要です。Exchange Online メールのみを使用するときの Office 365 の一般的な SPF レコードの例を次に示します。
  
```
TXT Name @
Values: v=spf1 include:spf.protection.outlook.com -all
```

ドメインからメールを受信するメール システムは SPF レコードを見て、メッセージを送信したメール サーバーが Office 365 サーバーの場合、メッセージは受け入れられます。古いメール システムまたはインターネット上の悪意のあるシステムがメッセージを送信したサーバーであった場合は、SPF の確認が失敗する可能性があり、メッセージは配信されません。このようなチェックは、スプーフィングとフィッシング メッセージの防止に役立ちます。
  
### <a name="choose-the-spf-record-structure-you-need"></a>必要な SPF レコードの構造を選択する

Office 365 に対して Exchange Online メールだけを使用するのではないシナリオの場合は (たとえば、SharePoint Online から送信されたメールも使用する場合)、次の表を使用して、レコードの値に含めるものを決定します。
  
> [!NOTE]
> たとえば、ファイアウォール経由のメール トラフィックを管理するためのエッジ メール サーバーを含む複雑なシナリオがある場合、より詳細な SPF レコードをセットアップします。[スプーフィングの防止に役立つ SPF レコードを Office 365 で設定する](https://go.microsoft.com/fwlink/?LinkId=787656)方法を学習してください。Office 365 での SPF の動作について詳しくは、「[Office 365 が Sender Policy Framework (SPF) を使用してスプーフィングを防止する方法](https://go.microsoft.com/fwlink/?LinkId=787065)」をご覧ください。
  
|||||
|:-----|:-----|:-----|:-----|
||使用対象  <br/> |用途  <br/> |以下を追加します。  <br/> |
|1  <br/> |すべてのメール システム (必須)  <br/> |この値で始まるすべての SPF レコード  <br/> |v=spf1  <br/> |
|2  <br/> |Exchange Online (一般的)  <br/> |Exchange Online だけで使用します  <br/> |include:spf.protection.outlook.com  <br/> |
|3  <br/> |SharePoint Online と Exchange Online (一般的)  <br/> |Exchange Online と SharePoint Online で使用します  <br/> |include:sharepointonline.com  <br/> |
|4  <br/> |サード パーティ製のメール システム (あまり一般的でない)  <br/> ||include:\<mail.contoso.com などのメール システム\>  <br/> |
|5  <br/> |オンプレミスのメール システム (あまり一般的でない)  <br/> |Exchange Online Protection または Exchange Online と別のメール システムを使用している場合に使用します  <br/> |ip4:\<0.0.0.0\>  <br/> ip6:\< : : \>  <br/> include:\<mail.contoso.com\>  <br/> 山かっこ (\<\>) 内の値は、自分のドメインにメールを送信する他のメール システムにする必要があります。  <br/> |
|6  <br/> |すべてのメール システム (必須)  <br/> ||-all  <br/> |

### <a name="example-adding-to-an-existing-spf-record"></a>例: 既存の SPF レコードへの追加
<a name="bkmk_addtospf"> </a>

SPF レコードが既にある場合は、Office 365 向けに値を追加または更新する必要があります。たとえば、contoso.com 用の既存の SPF レコードが次のようなものであるとします。
  
```
TXT Name @
Values: v=spf1 ip4:60.200.100.30 include:spf.protection.outlook.com -all
```

Office 365 用に SPF レコードを更新します。たとえば、SharePoint Online から送信されるメールを含めます。現在のレコードを編集し、必要な値を含む 1 つの SPF レコードを作成します。Office 365 の場合、SPF レコードの "sharepointonline.com" には Exchange Online (Outlook) と SharePoint Online 両方からのメールが含まれるので、元の値 "spf.protection.outlook.com" を置き換えます。
  
正しい:
  
```
TXT Name @
Values: v=spf1 ip4:60.200.100.30 include:sharepointonline.com -all
```

正しくない:
  
```
Record 1:
TXT Name @
Values: v=spf1 ip4:60.200.100.30 include:spf.protection.outlook.com -all
Record 2:
Values: v=spf1 include:sharepointonline.com -all
```

### <a name="more-examples-of-common-spf-values"></a>一般的な SPF 値の他の例
<a name="bkmk_addtospf"> </a>

完全な Office 365 スイートを使用し、かつ MailChimp を使用して代理としてマーケティングの電子メールを送信している場合、contoso.com の SPF レコードは次のようになります。ここでは上の表の行 1、3、4、6 を使用しています。行 1 と 6 は必須であり、"sharepointonline.com" には Exchange (Outlook) メールと SharePoint メールの両方が含まれます。
  
```
TXT Name @
Values: v=spf1 include:sharepointonline.com include:servers.mcsv.net -all
```

代わりに、電子メールが Office 365 およびオンプレミスのメール システムの両方から送信される Exchange のハイブリッド構成がある場合、contoso.com の SPF レコードは次のようになることがあります。
  
```
TXT Name @
Values: v=spf1 include:sharepointonline.com include:mail.contoso.com -all
```

メール用に Office 365 にドメインを追加するときに既存の SPF レコードを採用するのに役立つ一般的な例がいくつかあります。たとえば、ファイアウォール経由のメール トラフィックを管理するためのエッジ メール サーバーを含む複雑なシナリオがある場合、より詳細な SPF レコードをセットアップします。[スプーフィングの防止に役立つ SPF レコードを Office 365 で設定する](https://go.microsoft.com/fwlink/?LinkId=787656)方法を学習してください。
  
ここに戻る場合は、次の短いリンクをご利用ください: [https://aka.ms/o365edns](https://aka.ms/o365edns)
