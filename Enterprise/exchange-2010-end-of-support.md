---
title: サポート ロードマップの Exchange 2010 の終了
ms.author: dstrome
author: dstrome
manager: laurawi
ms.date: 1/31/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.assetid: e150e7b9-c432-4c8d-a0ae-c11847129a7d
description: Exchange 2010 は、サポート終了に近づいています。オンライン Exchange または Exchange Server の設置型の新しいバージョンへのアップグレードを準備するのには、この計画のロードマップをガイドとして使用します。
ms.openlocfilehash: e655edcc38723acd622fc6abc62a00d3f3e36738
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915192"
---
# <a name="exchange-2010-end-of-support-roadmap"></a>サポート ロードマップの Exchange 2010 の終了

**2020 年 1 月 14日**に、[Exchange Server 2010 がサポート終了に達し。Office 365 に Exchange 2010 または Exchange 2016 からの移行をすでに開始していないしている場合はここで、計画を開始します。 
  
## <a name="what-does-end-of-support-mean"></a>サポートの平均の最後は何でしょうか。

Exchange Server では、ほとんどすべてのマイクロソフト製品と同様に、提供の新機能、バグ修正、セキュリティ修正プログラムなどのサポート ライフ サイクルがあります。このライフ サイクルは、通常製品の初期リリースの日付から 10 年間持続し、このライフ サイクルの最後は、製品のサポート終了と呼ばれます。。Exchange 2010 のサポートは 2020 年 1 月 14日に、上の最後に到達するとマイクロソフトは提供されなくなります。
  
- テクニカル サポートに問題が発生します。
    
- バグの修正で問題が検出され、サーバーの使いやすさと安定性に影響を及ぼす可能性があります。
    
- セキュリティ上の脆弱性が検出され、セキュリティ違反の影響を受けるサーバーを構成することがありますの修正プログラム
    
- タイム ゾーンを更新します。
    
Exchange 2010 のインストールに対しては、この日付より後に実行され続けます。ただし、変更のため、上の一覧に、強くお勧め、できるだけ早くに Exchange 2010 から移行することです。
  
サポートの終了が近づいている Office 2010 のサーバーの詳細については、 [2010 のサーバーとクライアントの Office からアップグレードするためのリソース](upgrade-from-office-2010-servers-and-products.md)を参照してください。
  
## <a name="what-are-my-options"></a>オプションを挙げてください。

Exchange 2010 のサポートは、その末尾に到達、これは、オプションを検索し、移行計画を準備するのには絶好の機会です。できます：
  
- カット オーバーの高速を使用して Office 365 または移行、ハイブリッドへの移行します。 
    
- オンプレミスのサーバー上の Exchange の新しいバージョンの Exchange 2010 サーバーに移行します。
    
次のセクションでは、詳細については、各オプションについて説明します。
  
### <a name="migrate-to-office-365"></a>Office 365 への移行

Exchange 2010 展開を中止するため、最適なと最も簡単なオプションは、電子メールを Office 365 に移行します。Office 365 への移行のような古い技術から、最先端の機能を単一のホップを行うことができます。
  
- 保存ポリシー、インプレース、訴訟、コンプライアンス機能、インプレース電子証拠開示などです。
    
- マイクロソフトのチームです。
    
- 電源双です。
    
- 受信トレイのフォーカスがあります。
    
- について分析します。 を
    
- 電子メール、予定表、連絡先、およびようにプログラムでアクセスするための Api を残りの部分。
    
Office 365 も新機能と取得経験最初、ユーザーが通常の使用を開始してすぐ.新しい機能に加えて、心配する必要はありません。
  
- 購入し、ハードウェアの保守
    
- 加熱と冷却、サーバーの料金を支払ってください。
    
- 最新に保つには、セキュリティ、製品、およびタイム ゾーンの修正。
    
- ストレージとコンプライアンスの要件をサポートするためにソフトウェアを維持します。
    
- アップグレードに新しいバージョンの Exchange の人が常に最新バージョンの Office 365 での交換にします。
    
#### <a name="how-should-i-migrate-to-office-365"></a>Office 365 に移行する必要がありますか

組織によっては、Office 365 を活用するお手伝いしますが、いくつかのオプションがあります。移行オプションを選択すると、数席またはメールボックスを移動する必要があります、最後に移行する時間の長さと、オンプレミスのインストールと実行中に Office 365 の間でシームレスに統合する必要があるかどうかのようないくつかの点を考慮する必要があります。移行します。移行オプションと使用する方法を決定しますが、最も重要な要因を示します。
  
|**移行オプション**|**組織のサイズ**|**Duration**|
|:-----|:-----|:-----|
|カットオーバー移行  <br/> |接続クライアント数が 150 未満  <br/> |1 週間以内  <br/> |
|高速移行  <br/> |接続クライアント数が 150 未満  <br/> |2 週間以内  <br/> |
|完全ハイブリッドの移行  <br/> |接続クライアント数が 150 件を超える  <br/> |数週間以上  <br/> |
   
次のセクションでは、これらのメソッドの概要を説明します。各方法の詳細を説明する[移行パスを決定する](https://support.office.com/en-us/article/Decide-on-a-migration-path-0d4f2396-9cef-43b8-9bd6-306d01df1e27)をご覧ください。 
  
#### <a name="cutover-migration"></a>カットオーバー移行

カット オーバー移行で事前に選択された日付と時刻では、ありますが移行されるすべてのメールボックス、配布グループ、連絡先、および、Office 365 です。確認が完了したら、したが、オンプレミスの Exchange サーバーをシャット ダウンし、Office 365 を排他的に使用を開始します。
  
カット オーバー移行メソッドでは、非常に多くのメールボックスを持たない小規模な組織が Office 365 に迅速に取得するし、いくつかの他の方法の複雑さに対処する必要があるな。ですのもある程度制限 1 週間で完了した、または小さいことが、ユーザーが自分の Outlook プロファイルを再構成する必要があります。カット オーバー移行には、最大 2,000 のメールボックスが処理されるときにこのメソッドを使用して最大 150 個のメールボックスを移行するを強くお勧めします。150 件を超えるメールボックスを移行しようとするの期限前にすべてのメールボックスに転送する時間がなくなってしまうことし、IT サポートのスタッフを得ることが支援に大敗のユーザーが Outlook を再構成します。
  
カット オーバー移行の操作を行っていると思う場合は、ここでは、いくつかの点に注意を検討してください。
  
- Office 365 は、Outlook Anywhere を使用して TCP ポート 443 は、Exchange 2010 サーバーに接続する必要があります。
    
- Office 365 は、設置型のすべてのメールボックスを移動します。
    
- 設置管理者アカウントをユーザーのメールボックスの内容の読み取りアクセス許可を持つ必要があります。
    
- Exchange 2010 サービスで検証済みのドメインとして追加するのには Office 365 の必要性に使用するドメインを許可します。
    
- 移行を開始するまでの間に、Office 365 は、Office 365 とオンプレミスのメールボックスを定期的に同期させる完了フェーズを開始するとします。残され、オンプレミスのメールボックスにメールを気にせずに移行を完了することができます。
    
- ユーザーを最初にメールボックスにログインするときに変更する必要があります、自分の Office 365 アカウントの新しい一時パスワードが表示されます。
    
- Office 365 のライセンスには、Exchange Online に移行する各ユーザーのメールボックスをする必要があります。
    
- ユーザーは、それぞれのデバイスの新しい Outlook プロファイルを設定し、自分の電子メールを再度ダウンロードする必要があります。Outlook でダウンロードされる電子メールの量が異なることができます。詳細についてを見て[オフラインを維持するのにはメールの量を変更](https://support.office.com/en-us/article/Change-how-much-mail-to-keep-offline-f3a1251c-6dd5-4208-aef9-7c8c9522d633?ui=en-US&amp;rs=en-US&amp;ad=US&amp;fromAR=1)します。
    
カット オーバー移行の詳細についてを見てください。
  
- [ Office 365 への一括メール移行について知っておくべきこと ](https://support.office.com/en-us/article/What-you-need-to-know-about-a-cutover-email-migration-to-Office-365-961978ef-f434-472d-a811-1801733869da)
    
- [Office 365 の電子メールのカット オーバー移行を実行します。](https://support.office.com/en-us/article/Perform-a-cutover-migration-of-email-to-Office-365-9496e93c-1e59-41a8-9bb3-6e8df0cd81b4)
    
#### <a name="express-migration"></a>高速移行

高速の移行は、数百のいくつかのメールボックスを Office 365 に移行して、2、3 週間以内に移行を完了することができますの空き/予約済み予定表情報の共有と同様に高度なハイブリッド移行機能を使用する必要があることがあります。
  
高速の移行は、自分のメールボックスを Office 365 に移行するが、2、3 週間以内に移行を完了しようとしても時間がかかる必要がある組織にとっては朗報。いくつかの利点より高度な完全ハイブリッドしない移行の複雑な作業の多くを取得します。数、および、どのメールボックスを制御することは、特定の時点で移行ユーザー名と、オンプレミス アカウントのパスワードが office 365 のメールボックスが作成されます。カット オーバー移行とは異なり、ユーザーが自分の Outlook プロファイルを再作成する必要はありません。
  
について段階的な移行を実行する場合は、いくつかの考慮事項を示します。
  
- Office 365 は、Outlook Anywhere を使用して TCP ポート 443 は、Exchange 2010 サーバーに接続する必要があります。
    
- Office 365 は、オンプレミスの Active Directory サーバーの間で 1 回限りのディレクトリ同期を実行する必要があります。
    
- ユーザーは同じユーザー名とユーザーのメールボックスが移行されたときに使用していたパスワードを使用して Office 365 メールボックスにログインすることになります
    
- Office 365 のライセンスには、Exchange Online に移行する各ユーザーのメールボックスをする必要があります。
    
- ユーザーは、(一部の古い Android 電話は新しいプロファイルである必要があります)、デバイスのほとんどの新しい Outlook プロファイルを設定する必要があるし、自分の電子メールを再度ダウンロードする必要はありません。
    
段階的な移行の詳細についてを見て[簡単に Office 365 に Exchange メールボックスを移行するのには最低限のハイブリッドを使用](https://support.office.com/article/Use-Minimal-Hybrid-to-quickly-migrate-Exchange-mailboxes-to-Office-365-fdecceed-0702-4af3-85be-f2a0013937ef)
  
#### <a name="full-hybrid"></a>完全ハイブリッド

完全ハイブリッド移行は、組織には何百も、最大で数万、メールボックスのそれらの一部またはすべてを Office 365 に移動します。このような移行は通常長期であるため、ハイブリッドに移行できるようにします。
  
- オンプレミス ユーザーが、Office 365 でのユーザーの予定表の空き時間情報を表示して、その逆です。
    
- 設置と Office 365; の両方の受信者が含まれている統合されたグローバル アドレス一覧を参照してください。
    
- 設置いるかどうかにかかわらず、または Office 365 は、すべてのユーザーのすべての Outlook 受信者カードを表示します。
    
- オンプレミスの Exchange サーバーと TLS や証明書を使用して Office 365 の間で通信をセキュリティで保護された電子メール
    
- 可能にすることとして、内部に、オンプレミスの Exchange サーバーと Office 365 の間で送信されるメッセージを処理します。
    
  - 正しく評価され、内部のメッセージを対象とするトランスポートとコンプライアンスのエージェントによって処理されました。
    
  - スパム対策フィルターをバイパスします。
    
完全ハイブリッドの移行は、数か月以上のハイブリッド構成を維持すると予想される企業に最適です。オンラインのメールボックスの移動を使用してこことディレクトリ同期より統合されたコンプライアンス機能、および Office 365 との間に、メールボックスを移動することで前述した機能が表示されます。Office 365 では、設置型の組織の拡張機能になります。
  
完全ハイブリッド移行の操作を行っていると思う場合の考慮事項をいくつか挙げます。
  
- 完全ハイブリッドの移行はされていないあらゆる種類の組織に適しています。完全ハイブリッドの移行は複雑であるため数百人未満の場合、いくつかのメールボックスを持つ組織は残存作業時間と 1 つのセットアップに必要なコストを正当化する利点を通常表示されません。場合は、組織のようなそうですが、これを強くお勧めは Cutover または段階的な移行を検討すること
    
- Office 365 は TCP ポート 443 は、Outlook Anywhere を使用して Exchange 2010 サーバーに接続する必要があります。
    
- Azure Active Directory に接続 (AADConnect) を使用して、Office 365 は、オンプレミスの Active Directory サーバーの間でディレクトリ同期を設定する必要があります。
    
- ユーザーは同じユーザー名とパスワード (必要があります Azure Active Directory 接続パスワード同期または Active Directory フェデレーション サービスを含む)、ローカル ネットワークにログインするときに使用して、Office 365 のメールボックスにログインすることになります
    
- Office 365 のライセンスには、Exchange Online に移行する各ユーザーのメールボックスをする必要があります。
    
- ユーザーは、(一部の古い Android 電話は新しいプロファイルである必要があります)、デバイスのほとんどの新しい Outlook プロファイルを設定する必要があるし、自分の電子メールを再度ダウンロードする必要はありません。
    
場合に合った完全ハイブリッド移行音、移行を支援するのには次のリソースを見てください。
  
- [Exchange 展開アシスタント](https://aka.ms/exdeploy)
    
- [Exchange Server のハイブリッド展開](https://technet.microsoft.com/en-us/library/jj200581%28v=exchg.150%29.aspx)
    
- [ハイブリッド構成ウィザード](https://technet.microsoft.com/en-us/library/hh529921%28v=exchg.150%29.aspx)
    
- [ハイブリッド構成ウィザードに関する FAQ](https://technet.microsoft.com/en-us/library/mt488940%28v=exchg.150%29.aspx)
    
- [ハイブリッド展開の前提条件](https://technet.microsoft.com/en-us/library/hh534377%28v=exchg.150%29.aspx)
    
### <a name="migrate-to-a-newer-version-of-exchange-server"></a>Exchange Server の新しいバージョンへの移行します。

Office 365 に移行することで最高の値とユーザー エクスペリエンスを実現できることを強く信じ、中に一部の組織は、電子メール、設置型を保持する必要があることをまた理解します。これは、規制要件を満たすのため、データを保証するために格納されていない、データ センターにもう 1 つの国というようにします。電子メールをオンプレミスに保持する場合は、Exchange 2013 または Exchange 2016 を Exchange 2010 環境を移行できます。
  
Office 365 に移行できない場合は、2016 を Exchange に移行することをお勧めします。Exchange 2016 には、すべての機能と、Exchange の以前のリリースに含まれている機能が含まれていて、それに最も近い経験を Office 365 で利用できる (ただし、一部の機能は、Office 365 でのみ使用可能)。しているされてのことのほんの一例をご覧ください。
  
|**Exchange のリリース**|**機能**|
|:-----|:-----|
|Exchange 2013  <br/> | 簡略化されたアーキテクチャをする 3 つのサーバーの役割の数を減らす (メールボックス、クライアント アクセス、エッジ トランスポート)  <br/>  リークが発生してから重要な情報を保つためにデータの損失防止ポリシー (DLP)  <br/>  大幅に強化された Outlook Web App の操作性  <br/> |
|Exchange 2016  <br/> | *Exchange 2013 の機能としています.*  <br/>  メールボックス、エッジ トランスポートだけをさらに簡略化されたサーバー ロール  <br/>  SharePoint との統合と強化された DLP  <br/>  改善されたデータベースの復元  <br/>  オンライン ドキュメントの共同作業  <br/> |
   
#### <a name="which-version-should-i-migrate-to"></a>バージョンに移行したでしょうか。

最初に想定する 2016 を Exchange に移行することがすることをお勧めします。または Exchange 2016 を除外するのには、前提データを確認するのには、次の情報を使用します。理由の 1 つまたは別の Exchange 2016 に移行することはできませんは同じ Exchange 2013 年を処理するとします。
  
|**考慮事項**|**詳細情報**|
|:-----|:-----|
|サポート終了日  <br/> | Exchange の各バージョンでは Exchange 2010 では、ような日のサポート終了があります。  <br/> **Exchange 2013** - 2023年 4 月  <br/> **Exchange 2016** - 2025年 10 月  <br/>  以前のバージョンのサポートの日の終わり、早くは別の移行を実行する必要があります。2023年 4 月と思うよりもずっと近いです。<br/> |
|Exchange 2013 または 2016 への移行パス  <br/> |Exchange 2013 に移行するための一般的な段階を以下に示します。  <br/> 2016 Exchange 2013 をインストール、既存の Exchange 2010 組織移動サービスと Exchange 2013 または 2016 移動メールボックスを他のインフラストラクチャと Exchange 2013 または 2016年の使用停止が残りの Exchange 2010 サーバーのパブリック フォルダーに |
|バージョンの共存  <br/> |Exchange 2013 または 2016 を Exchange に移行するときは、既存の Exchange 2010 組織にいずれかのバージョンをインストールできます。これにより、1 つまたは複数の Exchange 2013 または 2016 の Exchange サーバーをインストールし、移行を実行することができます。  <br/> |
|サーバー ハードウェア  <br/> | Exchange 2010 のサーバーのハードウェア要件が変更されました。使用しようとしているハードウェアに互換性があるかどうかを確認する必要があります。ここでは、各バージョンのハードウェア要件の詳細をご覧ください。<br/> [Exchange 2016 のシステム要件](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.160%29.aspx) <br/> [Exchange 2013 のシステム要件](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.150%29.aspx) <br/>  Exchange のパフォーマンスと処理能力の向上、大幅に向上と新しいサーバーのストレージ容量と、する可能性があります必要があります同じ数のメールボックスをサポートするために少数のサーバーにあります。  <br/> |
|オペレーティング システムのバージョン  <br/> | バージョンごとにサポートされているオペレーティング システムの最小バージョンは次のとおりです。  <br/> **Exchange 2016**Windows Server 2012  <br/> **Exchange 2013**Windows Server 2008 R2 SP1  <br/>  [Exchange サポート ・ マトリックス](https://technet.microsoft.com/en-us/library/ff728623%28v=exchg.150%29.aspx)にオペレーティング システムのサポートの詳細が表示されます。  <br/> |
|Active Directory フォレストの機能レベル  <br/> | 最低限サポートされている Active Directory フォレストの機能レベルの各バージョンは次のとおりです。  <br/> **Exchange 2016**Windows Server 2008 R2 SP1  <br/> **Exchange 2013**Windows Server 2003  <br/>  [Exchange サポート ・ マトリックス](https://technet.microsoft.com/en-us/library/ff728623%28v=exchg.150%29.aspx)でフォレストの機能レベルのサポートの詳細が表示されます。  <br/> |
|Office クライアントのバージョン  <br/> | バージョンごとにサポートされている Office クライアントの最小バージョンは次のとおりです。  <br/> **Exchange 2016**(最新の更新) を使用して Office 2010  <br/> **Exchange 2013**Office 2007 SP3  <br/>  [Exchange サポート ・ マトリックス](https://technet.microsoft.com/en-us/library/ff728623%28v=exchg.150%29.aspx)で Office クライアントのサポートの詳細が表示されます。  <br/> |
   
#### <a name="how-do-i-migrate"></a>移行する方法は?

電子メールをオンプレミスに保持することを決めたなら、移行時に次のリソースを使用できます。
  
- [Exchange 展開アシスタント](https://aka.ms/exdeploy)
    
- Exchange [2016](https://technet.microsoft.com/EN-US/library/bb738144%28v=exchg.160%29.aspx)、 [2013](https://technet.microsoft.com/EN-US/library/bb738144%28v=exchg.150%29.aspx)のアクティブなディレクトリ スキーマの変更
    
- Exchange [2016](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.160%29.aspx)、 [2013](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.150%29.aspx)のシステム要件
    
- Exchange [2016](https://technet.microsoft.com/en-us/library/bb691354%28v=exchg.160%29.aspx)、 [2013](https://technet.microsoft.com/en-us/library/bb691354%28v=exchg.150%29.aspx)の前提条件
    
## <a name="what-if-i-need-help"></a>ヘルプを必要な場合は?

Office 365 に移行する場合は、FastTrack の Microsoft サービスを使用する対象とする必要があります。FastTrack は、ベスト ・ プラクティス、ツール、および Office 365 に移行を可能な限りシームレスにするためにリソースを提供します。計画から、移行の手順と、最後のメールボックスの移行に至る設計、実際のサポート エンジニアが必要があります。FastTrack の詳細を知っている場合は、 [Microsoft FastTrack](https://fasttrack.microsoft.com/)を見てください。
  
Office 365 に移行中に問題に実行する、FastTrack、または Exchange Server の新しいバージョンへの移行を使用していない場合は、私たちは、支援をします。ここでは、いくつかのリソースを使用することができます。
  
- [テクニカル コミュニティ](https://social.technet.microsoft.com/Forums/office/en-US/home?category=exchangeserver)
    
- [カスタマー サポート](https://support.microsoft.com/en-us/gp/support-options-for-business)
    
## <a name="related-topics"></a>関連項目

[2010 のサーバーとクライアントの Office からアップグレードするためのリソース](upgrade-from-office-2010-servers-and-products.md)
  
[Office 退職グループ (マイクロソフト テクニカル コミュニティ)](https://go.microsoft.com/fwlink/?linkid=842065)
  

