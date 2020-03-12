---
title: Exchange 2007 のサポート終了ロードマップ
ms.author: dstrome
author: dstrome
manager: laurawi
ms.date: 1/31/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.assetid: c3024358-326b-404e-9fe6-b618e54d977d
f1.keywords:
- NOCSH
description: 2017年4月11日に、Exchange Server 2007 がサポートの終了に到達しました。 Exchange 2007 から Office 365 または Exchange 2016 への移行をまだ開始していない場合は、計画を開始する時間になります。
ms.openlocfilehash: 75bafe48b3b384430312ad0c0942c98732985073
ms.sourcegitcommit: 1c646afb10db9d3d1e6a346089b7845268b0c9d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "42605652"
---
# <a name="exchange-2007-end-of-support-roadmap"></a>Exchange 2007 のサポート終了ロードマップ

*この記事は、Office 365 Enterprise および Microsoft 365 Enterprise の両方に適用されます。*

**2017 年4月 11**日に、Exchange Server 2007 がサポートの終了に到達しました。 Exchange 2007 から Office 365 または Exchange 2016 への移行をまだ開始していない場合は、計画を開始する時間になります。 
  
## <a name="what-does-end-of-support-mean"></a>サポートが終了するとどうなるのか

Exchange Server は、ほぼすべての Microsoft 製品と同様に、新機能、バグ修正、セキュリティ修正プログラムなどを提供するためのライフサイクルを備えています。 このライフサイクルは通常、製品の最初のリリースから10年後に持続し、このライフサイクルの最後は製品のサポート終了と呼ばれます。 Exchange 2007 は、2017年4月11日にサポートの終了に達したため、Microsoft は提供しなくなりました。
  
- 発生する可能性のある問題のテクニカル サポート。
    
- サーバーの安定性と運用に影響を与える可能性のある問題が検出された場合のバグ修正プログラム。
    
- 検出された脆弱性に対するセキュリティの修正。これにより、サーバーがセキュリティ侵害に対して脆弱になる可能性があります。
    
- タイム ゾーンの更新。
    
Exchange 2007 のインストールは、この日付以降も引き続き実行されます。 ただし、上記の変更によって、Exchange 2007 からできるだけ早く移行することを強くお勧めします。
  
サポートの終了間近にある Office 2007 サーバーの詳細については、「 [Plan your upgrade From office 2007 servers and products](upgrade-from-office-2007-servers-and-products.md)」を参照してください。
  
## <a name="what-are-my-options"></a>使用できるオプション

Exchange 2007 のサポートが終了したので、オプションを調査して移行計画を準備することを強くお勧めします。 以下のことを実行できます。
  
- Office 365 に移行するには、カットオーバー、段階的、またはハイブリッドの移行を使用します。
    
- Exchange 2007 サーバーをオンプレミスサーバー上の新しいバージョンの Exchange に移行します。
    
次のセクションでは、それぞれのオプションについて詳しく説明します。
  
### <a name="migrate-to-office-365"></a>Office 365 への移行

メールを Office 365 に移行することは、Exchange 2007 の展開を廃止するのに役立つ最良かつ最も簡単なオプションです。 Office 365 への移行を使用すると、次のように、10年以上のテクノロジから、次のようなアート機能のための1つのホップを作成することができます。
  
- アイテム保持ポリシー、インプレースおよび訴訟ホールド、インプレース電子情報開示などのコンプライアンス機能。
    
- Office 365 グループ
    
- 優先受信トレイ。
    
- Delve Analytics;
    
- 電子メール、予定表、連絡先などへのプログラムによるアクセスを可能にする REST Api。
    
Office 365 では、最初に新機能とエクスペリエンスを取得し、ユーザーは通常、すぐに使用を開始することもできます。 新機能に加えて、次のことについて心配する必要はありません。
  
- ハードウェアの購入および保守。
    
- お客様のサーバーの暖房および冷却に関する支払い。
    
- 常に最新のセキュリティ、製品、タイムゾーンを更新します。
    
- コンプライアンス要件をサポートするためのストレージとソフトウェアの管理
    
- 新しいバージョンの Exchange にアップグレードする-Office 365 の Exchange の最新バージョンを常にご使用いただけます。
    
#### <a name="how-should-i-migrate-to-office-365"></a>Office 365 に移行する方法

組織によっては、Office 365 にアクセスするために役立ついくつかのオプションがあります。 移行オプションを選択する際には、移動する必要のある座席やメールボックスの数、移行を最後に実行する時間、オンプレミスのインストールと Office 365 との間でシームレスに統合する必要があるかどうかを考慮する必要があります。移行。 次の表に、移行オプションと、使用する方法を決定する最も重要な要素を示します。
  
| |
|**移行オプション**|**組織の規模**|**Duration**|
|:-----|:-----|:-----|
|一括移行  <br/> |座席数が150未満  <br/> |1週間以内  <br/> |
|段階的な移行  <br/> |150を超える座席  <br/> |数週間  <br/> |
|完全なハイブリッド移行  <br/> |数百から数千の座席  <br/> |数か月以上  <br/> |
   
次のセクションでは、これらの方法の概要について説明します。 「」を参照してください。各方法の詳細については、「[移行パスを決定](https://support.office.com/article/Decide-on-a-migration-path-0d4f2396-9cef-43b8-9bd6-306d01df1e27)する」を参照してください。 
  
#### <a name="cutover-migration"></a>一括移行

カットオーバー移行では、事前に選択した日時で、すべてのメールボックス、配布グループ、連絡先などを Office 365 に移行します。完了したら、オンプレミスの Exchange サーバーをシャットダウンして、Office 365 を排他的に使用します。
  
カットオーバー移行方法は、メールボックスの数があまり多くない小規模な組織で、Office 365 にすばやくアクセスして、他の方法のいくつかの複雑な処理を行わないようにする場合に適しています。 ただし、1週間以内に完了する必要があり、ユーザーが Outlook プロファイルを再構成する必要があるため、この方法も若干制限されています。 カットオーバー移行では最大2000のメールボックスを処理できますが、この方法では最大150のメールボックスを移行することを強くお勧めします。 150を超えるメールボックスを移行しようとすると、期限までにすべてのメールボックスを移行するのに時間がかかる可能性があり、IT サポートスタッフが Outlook を再構成する手助けをしてしまう可能性があります。
  
一括移行の実行を検討している場合は、次の点を考慮する必要があります。
  
- Office 365 は、TCP ポート443で Outlook Anywhere を使用して Exchange 2007 サーバーに接続する必要があります。
    
- すべてのオンプレミスメールボックスが Office 365 に移動されます。
    
- ユーザーのメールボックスの内容を読み取るためのアクセス権を持つオンプレミスの管理者アカウントが必要です。
    
- Office 365 で使用する Exchange 2007 の承認済みドメインは、サービスの検証済みドメインとして追加する必要があります。
    
- 移行を開始してから完了フェーズを開始するまでの間、Office 365 は定期的に Office 365 とオンプレミスのメールボックスを同期します。 これにより、オンプレミスのメールボックスに残った電子メールを気にすることなく、移行を完了できます。
    
- ユーザーが初めてメールボックスにログインしたときに変更する必要がある Office 365 アカウントの新しい一時パスワードをユーザーが受け取ります。
    
- 移行するユーザーメールボックスごとに、Exchange Online を含む Office 365 ライセンスが必要になります。
    
- ユーザーは、それぞれのデバイスに新しい Outlook プロファイルを設定して、電子メールをもう一度ダウンロードする必要があります。 Outlook がダウンロードするメールの量は異なる場合があります。 詳細については、「[オフラインで保持するメールの量を変更する](https://support.office.com/article/Change-how-much-mail-to-keep-offline-f3a1251c-6dd5-4208-aef9-7c8c9522d633?ui=en-US&amp;rs=en-US&amp;ad=US&amp;fromAR=1)」を参照してください。
    
カットオーバー移行の詳細については、以下を参照してください。
  
- [ Office 365 への一括メール移行について知っておくべきこと ](https://support.office.com/article/What-you-need-to-know-about-a-cutover-email-migration-to-Office-365-961978ef-f434-472d-a811-1801733869da)
    
- [Office 365 への電子メールの一括移行を実行する](https://support.office.com/article/Perform-a-cutover-migration-of-email-to-Office-365-9496e93c-1e59-41a8-9bb3-6e8df0cd81b4)
    
#### <a name="staged-migration"></a>段階的な移行

段階的な移行とは、Office 365 に移行する必要がある数百または数千のメールボックスがある場合、移行を完了するのに1週間以上かかることがあり、共有の空き時間情報予定表情報のような高度なハイブリッド移行機能は必要ありません。
  
段階的な移行は、メールボックスを Office 365 に移行するのに時間がかかるようにする必要がある組織に適していますが、数週間以内に移行を完了することを計画しています。 メールボックスを "バッチ" で移行することにより、特定の時間にどのメールボックスを移行するかを制御できます。 同じ部署のユーザーのメールボックスをバッチ処理することもできます。たとえば、すべてのユーザーが同時に移動されていることを確認します。 または、最新のバッチまでエグゼクティブメールボックスを残しておくこともできます。 カットオーバー移行の場合と同様に、ユーザーは Outlook プロファイルを再作成する必要があります。
  
段階的な移行を検討している場合は、次の点を考慮する必要があります。
  
- Office 365 は、TCP ポート443で Outlook Anywhere を使用して Exchange 2007 サーバーに接続する必要があります。
    
- ユーザーのメールボックスの内容を読み取るためのアクセス権を持つオンプレミスの管理者アカウントが必要です。
    
- Office 365 で使用する Exchange 2007 の承認済みドメインは、サービスの検証済みドメインとして追加する必要があります。
    
- バッチで移行する各メールボックスの完全な名前と電子メールアドレスを使用して CSV ファイルを作成する必要があります。 移行するメールボックスごとに新しいパスワードを指定して、それぞれのユーザーにパスワードを送信する必要もあります。 ユーザーが新しい Office 365 メールボックスに初めてログインしたときにパスワードを変更するように求めるメッセージが表示されます。
    
- 移行バッチを開始してから、完了フェーズを開始するまでの間、Office 365 は、バッチに含まれている Office 365 とオンプレミスのメールボックスを定期的に同期します。 これにより、オンプレミスのメールボックスに残った電子メールを気にすることなく、移行を完了できます。
    
- ユーザーは、メールボックスに初めてログインするときに変更する必要がある Office 365 アカウントの新しい一時パスワードを受信します。
    
- 移行するユーザーメールボックスごとに、Exchange Online を含む Office 365 ライセンスが必要になります。
    
- ユーザーは、それぞれのデバイスに新しい Outlook プロファイルを設定して、電子メールをもう一度ダウンロードする必要があります。 Outlook がダウンロードするメールの量は異なる場合があります。 詳細については、「[オフラインで保持するメールの量を変更する](https://support.office.com/article/Change-how-much-mail-to-keep-offline-f3a1251c-6dd5-4208-aef9-7c8c9522d633?ui=en-US&amp;rs=en-US&amp;ad=US&amp;fromAR=1)」を参照してください。
    
段階的な移行の詳細については、以下を参照してください。
  
- [Office 365 への段階的メール移行について知っておくべきこと](https://support.office.com/article/What-you-need-to-know-about-a-staged-email-migration-to-Office-365-7e2c82be-5f3d-4e36-bc6b-e5b4d411e207)
    
- [Office 365 へのメールの段階的な移行を実行する](https://support.office.com/article/Perform-a-staged-migration-of-email-to-Office-365-83bc0b69-de47-4cc4-a57d-47e478e4894e)
    
#### <a name="full-hybrid"></a>完全なハイブリッド

完全なハイブリッド移行とは、組織で数百から数千のメールボックスを使用しており、一部またはすべてを Office 365 に移動する必要がある場合です。 通常、これらの移行は長期間になるため、ハイブリッド移行によって次のことが可能になります。
  
- オンプレミスのユーザーに、Office 365 のユーザーの予定表の空き時間情報を表示します。その逆も同様です。
    
- オンプレミスと Office 365 の両方の受信者が含まれる統合グローバルアドレス一覧を参照してください。
    
- すべてのユーザーについて、オンプレミスであるか Office 365 であるかに関係なく、すべてのユーザーの完全な Outlook 受信者カードを表示します。
    
- オンプレミスの Exchange サーバーと Office 365 との間で、TLS と証明書を使用して電子メール通信をセキュリティで保護します。
    
- オンプレミスの Exchange サーバーと Office 365 間で送信されたメッセージを内部として処理し、次のことを可能にします。
    
  - 内部メッセージを対象とするトランスポートおよびコンプライアンスエージェントによって適切に評価および処理されます。
    
  - スパム対策フィルターをバイパスします。
    
完全なハイブリッド移行は、数か月以上のハイブリッド構成にとどまることが予想される組織に最適です。 このセクションで前述した機能に加えて、ディレクトリ同期、統合されたコンプライアンス機能、および Office 365 との間でメールボックスを移動する機能 (オンラインメールボックス移動を使用) を取得することができます。 Office 365 は、オンプレミスの組織の拡張機能になります。
  
完全なハイブリッド移行の実行を検討している場合は、次の点を考慮する必要があります。
  
- 完全なハイブリッド移行は、すべての種類の組織には適していません。 完全なハイブリッド移行は複雑であるため、数百のメールボックスを使用している組織では、通常、1つの設定に必要な労力とコストを正当化する利点は得られません。 このことが組織のように聞こえる場合は、代わりに一括移行または段階的移行を検討することを強くお勧めします。
    
- "ハイブリッドサーバー" として動作するように、Exchange 2007 組織に少なくとも1つの Exchange 2013 サーバーを展開する必要があります。 このサーバーは、Exchange 2007 サーバーに代わって Office 365 と通信します。
    
- Office 365 は、TCP ポート443で Outlook Anywhere を使用して、"ハイブリッドサーバー" に接続する必要があります。
    
- オンプレミスの Active Directory サーバーと Office 365 の間に、Azure Active Directory Connect (AADConnect) を使用してディレクトリ同期をセットアップする必要があります。
    
- ユーザーは、ローカルネットワークにログインするときに使用したのと同じユーザー名とパスワードを使用して Office 365 メールボックスにログインできます (パスワード同期または Active Directory フェデレーションサービスによる Azure Active Directory 接続が必要です)。
    
- 移行するユーザーメールボックスごとに、Exchange Online を含む Office 365 ライセンスが必要になります。
    
- ユーザーは、多くのデバイスで新しい Outlook プロファイルを設定する必要はありません (一部の古い Android 電話機では新しいプロファイルが必要になることがあります)、メールを再ダウンロードする必要はありません。
    
完全なハイブリッド移行が適切な場合は、移行に役立つ以下のリソースを参照してください。
  
- [Exchange 展開アシスタント](https://aka.ms/exdeploy)
    
- [Exchange Server のハイブリッド展開](https://technet.microsoft.com/library/jj200581%28v=exchg.150%29.aspx)
    
- [ハイブリッド構成ウィザード](https://technet.microsoft.com/library/hh529921%28v=exchg.150%29.aspx)
    
- [ハイブリッド構成ウィザードに関する FAQ](https://technet.microsoft.com/library/mt488940%28v=exchg.150%29.aspx)
    
- [ハイブリッド展開の前提条件](https://technet.microsoft.com/library/hh534377%28v=exchg.150%29.aspx)
    
### <a name="migrate-to-a-newer-version-of-exchange-server"></a>新しいバージョンの Exchange Server に移行する

Office 365 に移行することによって、最高の価値とユーザーの利便性を実現できるということは強く信じられませんが、一部の組織ではメールをオンプレミスで保持する必要があることがわかっています。 これは、規制要件によって、データが別の国にあるデータセンターに格納されていないことなどが考えられます。 メールをオンプレミスで保持することを選択した場合は、exchange 2007 環境を Exchange 2010、Exchange 2013、または Exchange 2016 に移行できます。
  
Office 365 に移行できない場合は、Exchange 2016 に移行することをお勧めします。 Exchange 2016 には、Exchange の以前のリリースに含まれていたすべての機能とダウン状態が含まれており、Office 365 で利用できる機能に最も近いものがあります (一部の機能は Office 365 でのみ利用可能です)。 不足しているもののいくつかを確認してください。
  
|**Exchange リリース**|**機能**|
|:-----|:-----|
|Exchange 2010  <br/> | 役割ベースのアクセス制御 (Acl のないアクセス許可)  <br/>  Outlook Web Access メールボックスポリシー  <br/>  組織間で空き時間情報を共有し、予定表を委任する機能  <br/> |
|Exchange 2013  <br/> | *Exchange 2010 の機能*  <br/>  サーバーの役割の数を少なくするための簡略化されたアーキテクチャ (メールボックス、クライアントアクセス、エッジトランスポート)  <br/>  機密情報を漏洩させないようにするデータ損失防止ポリシー (DLP)  <br/>  Outlook Web App の操作性が大幅に向上しました。  <br/> |
|Exchange 2016  <br/> | *Exchange 2013 の機能*  <br/>  メールボックスとエッジトランスポートだけのサーバーの役割をさらに簡素化する  <br/>  SharePoint との統合と共に DLP が向上しました。  <br/>  データベースの復元性の向上  <br/>  オンラインドキュメントのコラボレーション  <br/> |
   
#### <a name="which-version-should-i-migrate-to"></a>移行する必要があるのはどのバージョンですか?

最初に Exchange 2016 に移行することを前提とすることをお勧めします。 次に、以下の情報を使用して、前提条件を確認するか、Exchange 2016 を除外します。 何らかの理由で Exchange 2016 に移行できない場合は、Exchange 2013 で同じプロセスを実行します。
  
|**十分**|**詳細情報**|
|:-----|:-----|
|サポート終了日  <br/> | Exchange 2007 と同様に、Exchange の各バージョンのサポート終了日は次のようになります。  <br/> **Exchange 2010**年1月2020  <br/> **Exchange 2013** -2023 年4月  <br/> **Exchange 2016**年10月2025  <br/>  以前はサポート終了日よりも早く、もう一度移行を実行する必要があります。 2020年1月は、ご想像を超えるほど多くなります。  <br/> |
|Exchange 2010 および2013への移行パス  <br/> |ここでは、Exchange 2010 または Exchange 2013 に移行するための一般的なフェーズを示します。  <br/> 既存の Exchange 2007 組織への Exchange 2010 または2013への移動サービスとその他のインフラストラクチャへの exchange 2010 への移動サービスとその他のインフラストラクチャへの移行メールボックスとパブリックフォルダーを Exchange の2013または2010に移動するその他の Exchange 2013 サーバー |
|Exchange 2016 への移行パス  <br/> |ここでは、Exchange 2016 への移行の一般的なフェーズを示します。  <br/> 既存の Exchange 2007 組織の移動サービスとその他のインフラストラクチャへの Exchange 2013 のインストールを Exchange 2013 に移行するメールボックスとパブリックフォルダーを exchange に移動する残りの Exchange の使用停止サーバーに exchange の 2007 2013 をインストールする既存のExchange 2013 組織。 メールボックス、パブリックフォルダー、サービス、およびその他のインフラストラクチャを Exchange 2016 に移動します (順序は関係ありません)。 残りの Exchange 2013 サーバー > [!NOTE]> exchange 2013 から exchange 2016 に移行することは簡単です。 両方のバージョンには、ほぼ同じハードウェア要件があります。 この点と事実は、これらのバージョンには互換性があるため、Exchange 2013 用に購入したサーバーを再構築して、Exchange 2016 をインストールすることができます。 また、オンラインメールボックスの移動を使用すると、ほとんどのユーザーはメールボックスがサーバーから移動され、Exchange 2016 を使用して再構築された後、それらのメールボックスに戻ってくることはありません。           |
|バージョンの共存  <br/> | 移行する場合:  <br/> **Exchange 2016**Exchange 2007 サーバーを含む組織に exchange 2016 をインストールすることはできません。 最初に Exchange 2010 または2013に移行する必要があります (Exchange 2013 を推奨)、すべての Exchange 2007 サーバーを削除して、Exchange 2016 に移行します。  <br/> **Exchange 2010 または exchange 2013**既存の Exchange 2007 組織に Exchange 2010 または Exchange 2013 をインストールすることができます。 これにより、1つ以上の Exchange 2010 または2013サーバーをインストールして、移行を実行することができます。  <br/> |
|サーバー ハードウェア  <br/> | サーバーハードウェア要件が Exchange 2007 から変更されました。 使用しているハードウェアに互換性があることを確認する必要があります。 各バージョンのハードウェア要件の詳細については、以下を参照してください。  <br/> [Exchange 2016 のシステム要件](https://technet.microsoft.com/library/aa996719%28v=exchg.160%29.aspx) <br/> [Exchange 2013 のシステム要件](https://technet.microsoft.com/library/aa996719%28v=exchg.150%29.aspx) <br/> [Exchange 2010 のシステム要件](https://technet.microsoft.com/library/aa996719%28v=exchg.141%29.aspx) <br/>  Exchange のパフォーマンスが大幅に向上したこと、および新しいサーバーでのコンピューティングの電力と記憶域の容量が増加したことにより、同じ数のメールボックスをサポートするために必要なサーバーが少なくなる可能性があることがわかります。  <br/> |
|オペレーティング システムのバージョン  <br/> | 各バージョンでサポートされているオペレーティングシステムの最小バージョンは次のとおりです。  <br/> **Exchange 2016**Windows Server 2012  <br/> **Exchange 2013**Windows Server 2008 R2 SP1  <br/> **Exchange 2010**Windows Server 2008 SP2  <br/>  オペレーティングシステムのサポートの詳細については、「 [Exchange サポートのマトリックス](https://technet.microsoft.com/library/ff728623%28v=exchg.150%29.aspx)」を参照してください。  <br/> |
|Active Directory フォレストの機能レベル  <br/> | 各バージョンのサポートされている最小 Active Directory フォレストの機能レベルは次のとおりです。  <br/> **Exchange 2016**Windows Server 2008 R2 SP1  <br/> **Exchange 2013**Windows Server 2003  <br/> **Exchange 2010**Windows Server 2003  <br/>  フォレストの機能レベルのサポートの詳細については、「 [Exchange サポートのマトリックス](https://technet.microsoft.com/library/ff728623%28v=exchg.150%29.aspx)」を参照してください。  <br/> |
|Office クライアントのバージョン  <br/> | 各バージョンでサポートされている最小 Office クライアントバージョンは次のとおりです。  <br/> **Exchange 2016**Office 2010 (最新の更新プログラム)  <br/> **Exchange 2013**Office 2007 SP3  <br/> **Exchange 2010**Office 2003  <br/>  Office クライアントサポートの詳細については、「Exchange サポートの[マトリックス](https://technet.microsoft.com/library/ff728623%28v=exchg.150%29.aspx)」を参照してください。  <br/> |
   
#### <a name="how-do-i-migrate"></a>移行方法

メールをオンプレミスで保持することを決定した場合は、以下のリソースを使用して移行に役立てることができます。
  
- [Exchange 展開アシスタント](https://aka.ms/exdeploy)
    
- Exchange [2016](https://technet.microsoft.com/library/bb738144%28v=exchg.160%29.aspx)、 [2013](https://technet.microsoft.com/library/bb738144%28v=exchg.150%29.aspx)、 [2010](https://www.microsoft.com/download/en/details.aspx?displaylang=en&amp;id=5401)の Active Directory スキーマの変更
    
- Exchange [2016](https://technet.microsoft.com/library/aa996719%28v=exchg.160%29.aspx)、 [2013](https://technet.microsoft.com/library/aa996719%28v=exchg.150%29.aspx)、 [2010](https://technet.microsoft.com/library/aa996719%28v=exchg.141%29.aspx)のシステム要件
    
- Exchange [2016](https://technet.microsoft.com/library/bb691354%28v=exchg.160%29.aspx)、 [2013](https://technet.microsoft.com/library/bb691354%28v=exchg.150%29.aspx)、 [2010](https://technet.microsoft.com/library/bb691354%28v=exchg.141%29.aspx)の前提条件
    
## <a name="what-if-i-need-help"></a>サポートが必要な場合はどうすればよいですか?

Office 365 に移行している場合は、Microsoft FastTrack サービスを使用することができます。 FastTrack は、Office 365 を可能な限りシームレスに移行できるように、ベストプラクティス、ツール、およびリソースを提供します。 どのような場合も、最新のメールボックスを移行するすべての方法を計画し、設計することによって、移行を進めるための実際のサポートエンジニアが用意されています。 FastTrack の詳細を知りたい場合は、「 [Microsoft fasttrack](https://fasttrack.microsoft.com/)」を参照してください。
  
Office 365 への移行中に FastTrack を使用していない場合や、新しいバージョンの Exchange Server に移行している場合は、この記事に記載されている説明を参照してください。 使用できるリソースを次に示します。
  
- [テクニカル コミュニティ](https://social.technet.microsoft.com/Forums/office/home?category=exchangeserver)
    
- [カスタマー サポート](https://support.microsoft.com/gp/support-options-for-business)
    
## <a name="related-topics"></a>関連項目

[Office 2007 サーバーおよびクライアントのアップグレードに役立つリソース](upgrade-from-office-2007-servers-and-products.md)