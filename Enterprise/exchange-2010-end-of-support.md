---
title: Exchange 2010 のサポート終了ロードマップ
ms.author: dstrome
author: dstrome
manager: laurawi
ms.date: 09/16/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.assetid: e150e7b9-c432-4c8d-a0ae-c11847129a7d
description: Exchange 2010 は、サポート終了間近に近づいています。 この計画ロードマップは、Exchange Online またはオンプレミスの Exchange Server の新しいバージョンへのアップグレードを準備するためのガイドとして使用してください。
ms.openlocfilehash: 28dcead19c1af1b5a641cae8f9d649b22fb36c95
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/07/2019
ms.locfileid: "38028831"
---
# <a name="exchange-2010-end-of-support-roadmap"></a>Exchange 2010 のサポート終了ロードマップ

**2020 年10月 13**日に、Exchange Server 2010 はサポート終了までに到達します。 Exchange 2010 から Office 365 または Exchange 2016 への移行をまだ開始していない場合は、計画を開始する時間になります。

## <a name="what-does-end-of-support-mean"></a>サポートが終了するとどうなるのか

Exchange Server は、ほぼすべての Microsoft 製品と同様に、新機能、バグ修正、セキュリティ修正プログラムなどを提供するためのライフサイクルを備えています。 このライフサイクルは通常、製品の最初のリリースから10年後に持続し、このライフサイクルの最後は製品のサポート終了と呼ばれます。
Exchange 2010 が2020年10月13日にサポートを終了すると、Microsoft から提供されなくなります。

- 発生する可能性のある問題のテクニカル サポート。
- サーバーの安定性と運用に影響を与える可能性のある問題が検出された場合のバグ修正プログラム。
- 検出された脆弱性に対するセキュリティの修正。これにより、サーバーがセキュリティ侵害に対して脆弱になる可能性があります。
- タイム ゾーンの更新。

Exchange 2010 のインストールは、この日付以降も引き続き実行されます。 ただし、上記の変更によって、Exchange 2010 からできるだけ早く移行することを強くお勧めします。

サポートの終了間近にある Office 2010 サーバーの詳細については、「 [office 2010 サーバーおよびクライアントからのアップグレードに役立つリソース](https://docs.microsoft.com/office365/enterprise/upgrade-from-office-2010-servers-and-products)」を参照してください。

## <a name="what-are-my-options"></a>使用できるオプション

Exchange 2010 がサポートの終了に到達すると、これは、オプションを調べて移行計画を準備するのに非常に時間がかかることになります。 以下のことを実行できます。

- 完全に Office 365 に移行します。 カットオーバー、最小ハイブリッド、または完全なハイブリッド移行を使用してメールボックスを移行し、オンプレミスの Exchange サーバーと Active Directory を削除します。
- オンプレミスサーバー上の exchange 2010 サーバーを Exchange 2016 に移行します。

> [!IMPORTANT]
> メールボックスを Office 365 に移行することを選択したものの、DirSync または Azure AD Connect を使用してオンプレミスの Active Directory からのユーザーアカウントの管理を続行する予定の場合は、少なくとも1つの Exchange server をオンプレミスで保持する必要があります。 最後の Exchange サーバーが削除された場合、exchange Online の Exchange 受信者を変更することはできません。 これは、権限のソースがオンプレミスの Active Directory に残っており、そこに変更を加える必要があるためです。 このシナリオでは、次のオプションを使用できます。

- (**推奨**)メールボックスを Office 365 に移行して、サーバーを2020年10月13日にアップグレードできる場合は、Exchange 2010 を使用して Office 365 に接続し、メールボックスを移行します。 次に、exchange 2010 を Exchange 2016 に移行し、残りの Exchange 2010 サーバーをすべて使用停止にします。
- 2020年10月13日に、メールボックスの移行とオンプレミスサーバーのアップグレードを完了できない場合は、オンプレミスの Exchange 2010 サーバーを最初に Exchange 2016 にアップグレードしてから、Exchange 2016 を使用して Office の365に接続し、メールボックスを移行します。

> [!NOTE]
> もう少し複雑ですが、オンプレミスの Exchange 2010 サーバーを Exchange 2016 に移行する際に、メールボックスを Office 365 に移行する場合もあります。

Exchange Server 2010 のサポート終了を回避するために実行できる3つのパスを次に示します。

![Exchange Server 2010 のアップグレードパス](./media/exchange-2010-end-of-support/exchange-2010-end-of-support-options.png)

次のセクションでは、それぞれのオプションについて詳しく説明します。

## <a name="migrate-to-office-365"></a>Office 365 への移行

メールを Office 365 に移行することは、Exchange 2010 の展開を廃止するのに役立つ最良かつ最も簡単なオプションです。 Office 365 への移行を使用すると、次のように、古いテクノロジから、次のような最新の機能までの単一ホップを作成できます。

- アイテム保持ポリシー、インプレースおよび訴訟ホールド、インプレース電子情報開示などのコンプライアンス機能。
- Microsoft Teams、
- Power BI;
- 優先受信トレイ。
- Delve Analytics;

Office 365 では、最初に新機能とエクスペリエンスを取得し、ユーザーは通常、すぐに使用を開始することもできます。 新機能に加えて、次のことについて心配する必要はありません。

- ハードウェアの購入および保守。
- お客様のサーバーの暖房および冷却に関する支払い。
- 常に最新のセキュリティ、製品、タイムゾーンを更新します。
- コンプライアンス要件をサポートするためのストレージとソフトウェアの管理
- 新しいバージョンの Exchange にアップグレードする-Office 365 の Exchange の最新バージョンを常にご使用いただけます。

### <a name="how-should-i-migrate-to-office-365"></a>Office 365 に移行する方法

組織によっては、Office 365 にアクセスするために役立ついくつかのオプションがあります。 移行オプションを選択する際には、移動する必要のある座席やメールボックスの数、移行を最後に実行する時間、オンプレミスのインストールと Office 365 との間でシームレスに統合する必要があるかどうかを考慮する必要があります。移行。 次の表に、移行オプションと、使用する方法を決定する最も重要な要素を示します。

| **移行オプション**     | **組織の規模** | **Duration**        |
|--------------------------|-----------------------|---------------------|
| 一括移行        | 座席数が150未満  | 1週間以内      |
| 最小限のハイブリッド移行 | 座席数が150未満  | 数週間以内 |
| 完全なハイブリッド移行    | 150を超える座席   | 数週間以上 |

次のセクションでは、これらの方法の概要について説明します。 「」を参照してください。各方法の詳細については、「[移行パスを決定](https://support.office.com/article/Decide-on-a-migration-path-0d4f2396-9cef-43b8-9bd6-306d01df1e27)する」を参照してください。

### <a name="cutover-migration"></a>一括移行

カットオーバー移行では、事前に選択した日時で、すべてのメールボックス、配布グループ、連絡先などを Office 365 に移行します。完了したら、オンプレミスの Exchange サーバーをシャットダウンして、Office 365 を排他的に使用します。

カットオーバー移行方法は、メールボックスの数があまり多くない小規模な組織で、Office 365 にすばやくアクセスして、他の方法のいくつかの複雑な処理を行わないようにする場合に適しています。 ただし、1週間以内に完了する必要があり、ユーザーが Outlook プロファイルを再構成する必要があるため、この方法も若干制限されています。 カットオーバー移行では最大2000のメールボックスを処理できますが、この方法では最大150のメールボックスを移行することを強くお勧めします。 150を超えるメールボックスを移行しようとすると、期限までにすべてのメールボックスを移行するのに時間がかかる可能性があり、IT サポートスタッフが Outlook を再構成する手助けをしてしまう可能性があります。

一括移行の実行を検討している場合は、次の点を考慮する必要があります。

- Office 365 は、TCP ポート443で Outlook Anywhere を使用して Exchange 2010 サーバーに接続する必要があります。
- すべてのオンプレミスメールボックスが Office 365 に移動されます。
- ユーザーのメールボックスの内容を読み取るためのアクセス権を持つオンプレミスの管理者アカウントが必要です。
- Office 365 で使用する Exchange 2010 の承認済みドメインは、サービスの検証済みドメインとして追加する必要があります。
- 移行を開始してから完了フェーズを開始するまでの間、Office 365 は定期的に Office 365 とオンプレミスのメールボックスを同期します。 これにより、オンプレミスのメールボックスに残った電子メールを気にすることなく、移行を完了できます。
- ユーザーが初めてメールボックスにログインしたときに変更する必要がある Office 365 アカウントの新しい一時パスワードをユーザーが受け取ります。
- 移行するユーザーメールボックスごとに、Exchange Online を含む Office 365 ライセンスが必要になります。
- ユーザーは、それぞれのデバイスに新しい Outlook プロファイルを設定して、電子メールをもう一度ダウンロードする必要があります。 Outlook がダウンロードするメールの量は異なる場合があります。 詳細については、「[オフラインで保持するメールの量を変更する](https://support.office.com/article/Change-how-much-mail-to-keep-offline-f3a1251c-6dd5-4208-aef9-7c8c9522d633?ui=en-US&rs=en-US&ad=US&fromAR=1)」を参照してください。

カットオーバー移行の詳細については、以下を参照してください。

- [Office 365 への一括メール移行について知っておくべきこと](https://support.office.com/article/What-you-need-to-know-about-a-cutover-email-migration-to-Office-365-961978ef-f434-472d-a811-1801733869da)
- [Office 365 への電子メールの一括移行を実行する](https://support.office.com/article/Perform-a-cutover-migration-of-email-to-Office-365-9496e93c-1e59-41a8-9bb3-6e8df0cd81b4)

### <a name="minimal-hybrid-migration"></a>最小限のハイブリッド移行

最低限のハイブリッド (高速) 移行とは、Office 365 に移行する必要がある数百のメールボックスがあり、数週間以内に移行を完了でき、空き時間情報の共有の予定表情報などの高度なハイブリッド移行機能を必要としないものです。

最小限のハイブリッド移行は、メールボックスを Office 365 に移行するのに時間がかかるようにする必要がある組織に適していますが、数週間以内に移行を完了することを計画しています。 多くの複雑な複雑な移行を行わずに、より高度なハイブリッド移行のメリットが得られます。 特定の時間に移行されるメールボックスの数と頻度を制御できます。Office 365 メールボックスは、オンプレミスのアカウントのユーザー名とパスワードを使用して作成されます。また、カットオーバー移行とは異なり、ユーザーは Outlook プロファイルを再作成する必要はありません。

最小限のハイブリッド移行を実行することを検討している場合は、次の点を考慮する必要があります。

- オンプレミスの Active Directory サーバーと Office 365 の間では、1回限りのディレクトリ同期を実行する必要があります。
- ユーザーは、自分のメールボックスが移行されたときに使用していたのと同じユーザー名とパスワードを使用して、Office 365 メールボックスにログインできるようになります。
- 移行するユーザーメールボックスごとに、Exchange Online を含む Office 365 ライセンスが必要になります。
- ユーザーは、多くのデバイスで新しい Outlook プロファイルを設定する必要はありません (一部の古い Android 電話機では新しいプロファイルが必要になることがあります)、メールを再ダウンロードする必要はありません。

最小限のハイブリッド移行の詳細については、「[最小限のハイブリッドを使用して Exchange メールボックスを Office 365 にすばやく移行する](https://support.office.com/article/Use-Minimal-Hybrid-to-quickly-migrate-Exchange-mailboxes-to-Office-365-fdecceed-0702-4af3-85be-f2a0013937ef)」を参照してください。

### <a name="full-hybrid"></a>完全なハイブリッド

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

- 完全なハイブリッド移行は、すべての種類の組織には適していません。 完全なハイブリッド移行は複雑であるため、数百のメールボックスを使用している組織では、通常、1つの設定に必要な労力とコストを正当化する利点は得られません。 これが組織のように聞こえる場合は、代わりに一括移行を一括して、または最小限に抑えることをお勧めします。
- オンプレミスの Active Directory サーバーと Office 365 の間に、Azure Active Directory Connect (AADConnect) を使用してディレクトリ同期をセットアップする必要があります。
- ユーザーは、ローカルネットワークにログインするときに使用したのと同じユーザー名とパスワードを使用して Office 365 メールボックスにログインできます (パスワード同期または Active Directory フェデレーションサービスによる Azure Active Directory 接続が必要です)。
- 移行するユーザーメールボックスごとに、Exchange Online を含む Office 365 ライセンスが必要になります。
- ユーザーは、多くのデバイスで新しい Outlook プロファイルを設定する必要はありません (一部の古い Android 電話機では新しいプロファイルが必要になることがあります)、メールを再ダウンロードする必要はありません。

> [!IMPORTANT]
> メールボックスを Office 365 に移行することを選択したものの、DirSync または Azure AD Connect を使用してオンプレミスの Active Directory からのユーザーアカウントの管理を続行する予定の場合は、少なくとも1つの Exchange server をオンプレミスで保持する必要があります。 最後の Exchange サーバーが削除された場合、exchange Online の Exchange 受信者を変更することはできません。 これは、権限のソースがオンプレミスの Active Directory に残っており、そこに変更を加える必要があるためです。

完全なハイブリッド移行が適切な場合は、移行に役立つ以下のリソースを参照してください。

- [Exchange 展開アシスタント](https://aka.ms/exdeploy)
- [Exchange Server のハイブリッド展開](https://technet.microsoft.com/library/jj200581%28v=exchg.150%29.aspx)
- [ハイブリッド構成ウィザード](https://technet.microsoft.com/library/hh529921%28v=exchg.150%29.aspx)
- [ハイブリッド構成ウィザードに関する FAQ](https://technet.microsoft.com/library/mt488940%28v=exchg.150%29.aspx)
- [ハイブリッド展開の前提条件](https://technet.microsoft.com/library/hh534377%28v=exchg.150%29.aspx)

## <a name="upgrade-to-a-newer-version-of-exchange-server-on-premises"></a>オンプレミスの Exchange Server の新しいバージョンにアップグレードする

完全に Office 365 に移行することによって、最高の価値とユーザーの利便性を実現できるということは強く信じられませんが、一部の組織では、一部の Exchange サーバーをオンプレミスのままにしておく必要があることも理解しています。 これは、規制要件により、データが別の国にあるデータセンターに格納されていない、またはクラウドでは対応できない固有の設定または要件がある、または単に Exchange が必要なものである可能性があるためです。クラウドメールボックスを管理するには、オンプレミスの Active Directory を引き続き使用する必要があります。 Exchange のオンプレミスを選択または保持する必要がある場合は、exchange 2010 環境が少なくとも Exchange 2013 または Exchange 2016 にアップグレードされており、サポートの終了日前に Exchange 2010 が削除されていることを確認する必要があります。

最良の結果を得るために、残りのオンプレミス環境を Exchange 2016 にアップグレードすることをお勧めします。 Exchange server 2010 から Exchange Server 2016 に直接移動する場合は、Exchange Server 2013 をインストールする必要はありません。

Exchange 2016 には、Exchange の以前のリリースに含まれていたすべての機能とダウン状態が含まれており、Office 365 で利用できる機能に最も近いものがあります (一部の機能は Office 365 でのみ利用可能です)。 不足しているもののいくつかを確認してください。

| **Exchange リリース**                     | **機能**                                                                                                                                                                                                                                         |
|------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Exchange 2013                            | サーバーの役割の数を少なくするための簡略化されたアーキテクチャ (メールボックス、クライアントアクセス、エッジトランスポート)                                                                                                                                        |
|                                          | 機密情報を漏洩させないようにするデータ損失防止ポリシー (DLP)                                                                                                                                                                |
|                                          | Outlook Web App の操作性が大幅に向上しました。                                                                                                                                                                                                    |
| Exchange 2016                            | *Exchange 2013 の機能*                                                                                                                                                                                                                   |
|                                          | メールボックスとエッジトランスポートだけのサーバーの役割をさらに簡素化する                                                                                                                                                                                   |
|                                          | SharePoint との統合と共に DLP が向上しました。                                                                                                                                                                                                  |
|                                          | データベースの復元性の向上                                                                                                                                                                                                                         |
|                                          | オンラインドキュメントのコラボレーション                                                                                                                                                                                                                        |

| **十分**                        | **詳細情報**                                                                                                                                                                                                                                        |
|------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| サポート終了日                     | Exchange 2010 と同様に、Exchange の各バージョンのサポート終了日は次のようになります。                                                                                                                                                                        |
|                                          | **Exchange 2013** -2023 年4月                                                                                                                                                                                                                       |
|                                          | **Exchange 2016**年10月2025                                                                                                                                                                                                                     |
|                                          | 以前はサポート終了日よりも早く、もう一度移行を実行する必要があります。 2023年4月は、ご想像を超えるほど多くなります。                                                                                                                 |
| Exchange 2013 または2016への移行パス  | Exchange 2010 から新しいバージョンへの移行パスは、Exchange 2013 または Exchange 2016 のどちらを選択する場合も同じです。                                                                                                                              |
|                                          | 既存の Exchange 2010 組織への Exchange 2013 または2016への移動サービスとその他のインフラストラクチャへの exchange 2013 への移動サービスとその他のインフラストラクチャへの移行メールボックスとパブリックフォルダーを Exchange の2016または2013に移動するその他の Exchange 2016 サーバー  |
| バージョンの共存                      | Exchange 2013 または Exchange 2016 に移行する場合は、いずれかのバージョンを既存の Exchange の2010組織にインストールできます。 これにより、1つ以上の Exchange 2013 または Exchange 2016 サーバーをインストールして、移行を実行することができます。             |
| サーバー ハードウェア                          | サーバーハードウェア要件が Exchange 2010 から変更されました。 使用しているハードウェアに互換性があることを確認する必要があります。 各バージョンのハードウェア要件の詳細については、以下を参照してください。                                      |
|                                          | [Exchange 2016 のシステム要件](https://technet.microsoft.com/library/aa996719%28v=exchg.160%29.aspx)                                                                                                                                      |
|                                          | [Exchange 2013 のシステム要件](https://technet.microsoft.com/library/aa996719%28v=exchg.150%29.aspx)                                                                                                                                      |
|                                          | Exchange のパフォーマンスが大幅に向上したこと、および新しいサーバーでのコンピューティングの電力と記憶域の容量が増加したことにより、同じ数のメールボックスをサポートするために必要なサーバーが少なくなる可能性があることがわかります。                       |
| オペレーティング システムのバージョン                 | 各バージョンでサポートされているオペレーティングシステムの最小バージョンは次のとおりです。                                                                                                                                                                                |
|                                          | **Exchange 2016**Windows Server 2012                                                                                                                                                                                                                |
|                                          | **Exchange 2013**Windows Server 2008 R2 SP1                                                                                                                                                                                                         |
|                                          | オペレーティングシステムのサポートの詳細については、「 [Exchange サポートのマトリックス](https://technet.microsoft.com/library/ff728623%28v=exchg.150%29.aspx)」を参照してください。                                                                        |
| Active Directory フォレストの機能レベル | 各バージョンのサポートされている最小 Active Directory フォレストの機能レベルは次のとおりです。                                                                                                                                                                |
|                                          | **Exchange 2016**Windows Server 2008 R2 SP1                                                                                                                                                                                                         |
|                                          | **Exchange 2013**Windows Server 2003                                                                                                                                                                                                                |
|                                          | フォレストの機能レベルのサポートの詳細については、「 [Exchange サポートのマトリックス](https://technet.microsoft.com/library/ff728623%28v=exchg.150%29.aspx)」を参照してください。                                                                 |
| Office クライアントのバージョン                   | 各バージョンでサポートされている最小 Office クライアントバージョンは次のとおりです。                                                                                                                                                                                   |
|                                          | **Exchange 2016**Office 2010 (最新の更新プログラム)                                                                                                                                                                                              |
|                                          | **Exchange 2013**Office 2007 SP3                                                                                                                                                                                                                    |
|                                          | Office クライアントサポートの詳細については、「Exchange サポートの[マトリックス](https://technet.microsoft.com/library/ff728623%28v=exchg.150%29.aspx)」を参照してください。                                                                           |

以下のリソースを使用して、移行に役立てることができます。

- [Exchange 展開アシスタント](https://aka.ms/exdeploy)
- Exchange [2016](https://technet.microsoft.com/library/bb738144%28v=exchg.160%29.aspx)の Active Directory スキーマの変更[2013](https://technet.microsoft.com/library/bb738144%28v=exchg.150%29.aspx)
- Exchange [2016](https://technet.microsoft.com/library/aa996719%28v=exchg.160%29.aspx)のシステム要件[2013](https://technet.microsoft.com/library/aa996719%28v=exchg.150%29.aspx)
- Exchange [2016](https://technet.microsoft.com/library/bb691354%28v=exchg.160%29.aspx)の前提条件[2013](https://technet.microsoft.com/library/bb691354%28v=exchg.150%29.aspx)

## <a name="summary-of-options-for-office-2010-client-and-servers-and-windows-7"></a>Office 2010 のクライアントおよびサーバーおよび Windows 7 のオプションの概要

Office 2010 のクライアントおよびサーバーおよび Windows 7 のアップグレード、移行、およびクラウドの移行オプションの視覚的な概要については、「[サポートの終了」ポスター](./media/upgrade-from-office-2010-servers-and-products/Office2010Windows7EndOfSupport.pdf)を参照してください。

![](./media/upgrade-from-office-2010-servers-and-products/office2010-windows7-end-of-support.png)

この1ページのポスターは、Office 2010 のクライアントおよびサーバー製品と Windows 7 のサポートが終了しないようにするために実行できるさまざまなパスを簡単に理解する方法です。 Microsoft 365 Enterprise では、優先パスとオプションのサポートが強調表示されています。

このポスターを[ダウンロード](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/enterprise/media/migration-microsoft-365-enterprise-workload/Office2010Windows7EndOfSupport.pdf)して、レター、リーガル、またはタブロイド (11 x 17) 形式で印刷することもできます。
      
## <a name="what-if-i-need-help"></a>サポートが必要な場合はどうすればよいですか?

Office 365 に移行している場合は、Microsoft FastTrack サービスを使用することができます。 FastTrack は、Office 365 を可能な限りシームレスに移行できるように、ベストプラクティス、ツール、およびリソースを提供します。 どのような場合も、最新のメールボックスを移行するすべての方法を計画し、設計することによって、移行を進めるための実際のサポートエンジニアが用意されています。 FastTrack の詳細を知りたい場合は、「 [Microsoft fasttrack](https://fasttrack.microsoft.com/)」を参照してください。

Office 365 への移行中に FastTrack を使用していない場合や、新しいバージョンの Exchange Server に移行している場合は、この記事に記載されている説明を参照してください。 使用できるリソースを次に示します。

- [テクニカル コミュニティ](https://social.technet.microsoft.com/Forums/office/home?category=exchangeserver)
- [カスタマー サポート](https://support.microsoft.com/gp/support-options-for-business)

## <a name="related-topics"></a>関連項目

[Office 2010 サーバーおよびクライアントからのアップグレードに役立つリソース](https://docs.microsoft.com/office365/enterprise/upgrade-from-office-2010-servers-and-products)

[Office の退職グループ (Microsoft Tech Community)](https://go.microsoft.com/fwlink/?linkid=842065)
