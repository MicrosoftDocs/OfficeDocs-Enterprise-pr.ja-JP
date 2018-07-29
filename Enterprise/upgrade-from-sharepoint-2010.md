---
title: SharePoint 2010 からアップグレードします。
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 2/2/2018
ms.audience: ITPro
ms.topic: conceptual
ms.prod: office-online-server
localization_priority: Normal
ms.collection: Ent_O365
search.appverid:
- MET150
- WSU140
- OSU140
ms.assetid: 985a357f-6db7-401f-bf7a-1bafdf1f312c
description: SharePoint 2010 と SharePoint Server 2010 がサポート終了に近づいています。SharePoint Online または SharePoint のサーバーの設置型の新しいバージョンにアップグレードするのにはガイドとしてこの資料を使用します。
ms.openlocfilehash: c88c6010aa398d8076fce59976bf6f5c0aa1a743
ms.sourcegitcommit: a9c84d02e94c99ff6b1099b4a9ae695be08210e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/25/2018
ms.locfileid: "21169869"
---
# <a name="upgrading-from-sharepoint-2010"></a>SharePoint 2010 からアップグレードします。

2020 年 10 月 13日に、[Microsoft Office SharePoint Server 2010 サポートの末尾に到達します。この資料では、ユーザー、SharePoint Online に、既存の SharePoint Server 2010 のデータを移行するか、SharePoint サーバーの設置型のアップグレードを支援するためのリソースについて説明します。
  
## <a name="what-is-end-of-support"></a>サポート終了とは何ですか。

SharePoint Server 2010 と SharePoint Foundation 2010 のソフトウェアのサポート ライフ サイクル (新機能、バグ修正、セキュリティ修正プログラム、およびように、マイクロソフトが提供時間) の末尾に到達するとソフトウェアの 'サポート 'を終了と呼ばれることこれは、場合によっては、その '退職' です。製品のサポート (または EOS) の最後に、時に何も実際にシャット ダウンまたは停止します。ただし、ソフトウェアのサポートの最後に、マイクロソフトが提供されなくなります。
  
- テクニカル サポートに問題が発生します。
    
- バグの修正で問題が検出され、サーバーの使いやすさと安定性に影響を及ぼす可能性があります。
    
- セキュリティ上の脆弱性が検出され、セキュリティ違反の影響を受けるサーバーを構成することがありますの修正プログラム
    
- タイム ゾーンを更新します。
    
つまり、それ以上更新プログラム、修正プログラム、または修正プログラム (セキュリティ更新プログラムと修正プログラムを含む)、製品の出荷し、マイクロソフトのサポートが完全に移ってきています、サポートを行ってより新しいバージョンにします。SharePoint Server 2010 のサポート終了に近づくにつれて、機会、製品のアップグレードや、重要なデータを移行する前に不要なデータをトリムするのには利用する必要があります。
  
> [!NOTE]
> ソフトウェアのライフ サイクルは、通常製品の初期リリースの日付から 10 年間持続します。ソフトウェアの次のバージョンへのアップグレードまたは Office 365 移行 (またはその両方) を持つことができます[マイクロソフトのパートナー企業](https://go.microsoft.com/fwlink/?linkid=841249)を検索できます。Sharepoint を使用している SQL server のバージョンの特に重要な基盤となるテクノロジーにも、サポート期間の最後の注意をしていることを確認してください。 
  
## <a name="what-are-my-options"></a>オプションを挙げてください。

最初に、[製品のライフ サイクルのサイト](https://support.microsoft.com/en-us/lifecycle/search?alpha=SharePoint%20Server%202010)でのサポート終了する日付を確認してください。次に、この日のサポート技術情報を使用してアップグレードまたは移行の時間を計画することを確認します。製品を*動作を停止しない*日に記載されている場合、その利用を続けることができますが、インストールが不要になった更新プログラムを適用日以降後、ためにする戦略をよりスムーズに次のバージョンへの移行のことを忘れないでください。製品です。 
  
このマトリックスでは、移行する製品の機能とユーザー ・ データの場合に、コースを作成することができます。
  
|**製品のサポートの終了**|**中**|**高**|
|:-----|:-----|:-----|
|SharePoint Server 2010  <br/> |SharePoint Server 2013  <br/> |SharePoint Online  <br/> |
||SharePoint ハイブリッド  <br/> |SharePoint サーバー 2016 (設置型)  <br/> |
|||SharePoint のクラウドのハイブリッド検索  <br/> |
   
(オプション) のスケールのローエンドのオプションを選択すると、SharePoint Server 2010 の移行が完了した後すぐに別のアップグレード計画を開始する必要があります。(サポートのため、SharePoint Server 2010 と SharePoint Foundation 2010 のスケジュールが 2020 年 10 月 13日の*に注意してください*常にする必要がありますが、チェック終了[製品のライフ サイクルのサイト](https://support.microsoft.com/en-us/lifecycle)最も正確な日付を!) 
  
## <a name="where-should-i-go-next"></a>次移動する必要がありますでしょうか。

SharePoint Server 2013 と SharePoint Foundation 2013 には、インストールされている設置型の独自のサーバーを指定できます。を使用する場合は SharePoint Online では、Microsoft Office 365 の一部であるオンライン サービスであります。を選択できます。
  
- SharePoint Online に移行する
    
- SharePoint サーバーまたは SharePoint Foundation の設置型をアップグレードします。
    
- 上記の両方の操作を行います
    
- [SharePoint のハイブリッド](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx)ソリューションを実装します。 
    
非表示に伴うコストの今後は、サーバー ファームの管理を維持するか、カスタマイズを移行して SharePoint Server が依存しているハードウェアのアップグレードに注意します。場合に注意してくださいこれらのすべてを満たして、設置型のアップグレードを続行するのには容易になります。それ以外の場合、重いカスタマイズを行わなくても、従来の SharePoint サーバーに、ファームを実行する場合は、是非計画的な移行 SharePoint Online にします。オンプレミス ハードウェアの管理、データの設置型では、すべてを保持することの量を減らすために SharePoint Online の一部のデータを配置するのには SharePoint サーバーのショップを選択する場合のこともできます。SharePoint Online に、データの一部を移動するのにはより経済的な場合があります。
  
> [!NOTE]
> SharePoint 管理者可能性があります[、Office 365 のサブスクリプションを作成](https://go.microsoft.com/fwlink/?linkid=843152)、新しい SharePoint Online サイトを設定し、SharePoint Server 2010 から完全にカット新しい SharePoint Online サイトに最も重要なドキュメントのみを取得します。そこから、残りのデータ消耗する SharePoint Server 2010 サイトから設置型のアーカイブです。 
  
|**SharePoint オンライン (SPO)**|**SharePoint サーバー設置**|
|:-----|:-----|
|時間のコストが高い (計画と実行と検証)  <br/> |時間のコストが高い (計画と実行と検証)  <br/> |
|資金 (ハードウェアの購入なし) でのコストを削減  <br/> |(ハードウェアの購入) の資金のコストが高い  <br/> |
|移行での 1 回限りの料金  <br/> |将来の移行につき 1 回限りのコストが繰り返されます。  <br/> |
|低い総所有コストとメンテナンス  <br/> |高の総所有コストとメンテナンス  <br/> |
   
Office 365 に移行する場合、1 回だけ移動は時間の重いコストを設ける計画、事前 (中にデータを整理して、クラウドへの対処およびのままにするのにはどのような決定している)。ただし、データを移行すると、アップグレードできる、その時点から自動ハードウェアとソフトウェアの更新を管理する必要がないと、ファームのアップ時間は、Microsoft のサービス レベル契約 ([SLA](https://go.microsoft.com/fwlink/?linkid=843153)) によってバックアップするになります。
  
### <a name="migrate-to-sharepoint-online"></a>SharePoint Online に移行する

必ず、SharePoint Online に関連付けられているサービスの説明を確認して、必要なすべての機能を提供しています。すべての Office 365 サービスの説明へのリンクを以下に示します。
  
[Office 365 サービスの説明](https://go.microsoft.com/fwlink/?linkid=272060)
  
現在、直接移行できますから、SharePoint Server 2010 (SharePoint Foundation 2010) SharePoint Online に手段がない、手動作業のためだけです。これはすることによりデータをアーカイブ プルーニングを移動する前に、不要なサイトです。その他のデータは、ストレージにアーカイブできます。また、SharePoint Server 2010 と SharePoint Foundation 2010 のどちらも停止する作業のサポート、最後に管理者は、SharePoint がまだ実行中のデータの一部を移動するのには、お客様が忘れてしまった場合、期間を持つことができますので注意してください。
  
SharePoint Server 2013 または SharePoint サーバーの 2016年にアップグレードすると、SharePoint Online にデータを配置すること、移動も場合があります (OneDrive ビジネスのために情報を移行するには) を[SharePoint 移行 API](https://support.office.com/en-us/article/Upload-on-premises-content-to-SharePoint-Online-using-PowerShell-cmdlets-555049c6-15ef-45a6-9a1f-a1ef673b867c?ui=en-US&amp;rs=en-US&amp;ad=US)を使用します。 
  
|**オンライン Pro**|**オンライン詐欺**|
|:-----|:-----|
|Microsoft では、SPO のハードウェアおよびハードウェアのすべての管理を提供します。  <br/> |使用可能な機能は、SharePoint サーバーの設置型と SPO の間で異なる場合があります。  <br/> |
|グローバル管理者は、サブスクリプションのと、SPO のサイトに管理者を割り当てることがあります。  <br/> |設置型で SharePoint Server ファーム管理者に利用可能ないくつかのアクションが存在しない (または必要はありません)、SharePoint 管理者の役割で、Office 365 の管理] ページでサイト コレクションの管理、およびサイトの所有権は組織  <br/> |
|マイクロソフトは、修正プログラムを適用、修正し、基になるハードウェアとソフトウェア (SharePoint Online を実行する SQL サーバーを含む) を更新します。  <br/> |サービスの基になるファイル ・ システムへのアクセス権がないため、一部のカスタマイズが制限されています。  <br/> |
|マイクロソフトでは、[サービス レベル合意書](https://go.microsoft.com/fwlink/?linkid=843153)の発行し、サービス ・ レベルの問題を解決するのには迅速に移動します。  <br/> |バックアップと復元、およびその他のリカバリ ・ オプションは、SharePoint Online のサービスで自動化された - バックアップが上書きされるかどうかを使用します。  <br/> |
|セキュリティのテストとサーバーのパフォーマンスのチューニングを実施するサービスで継続的にマイクロソフトによって。  <br/> |ユーザー インターフェイスおよびその他の SharePoint の機能は、サービスがインストールされているし、オンとオフを切り替える必要がありますに変更します。  <br/> |
|Office 365 は、多くの業界標準を満たしている: [Office 365 のコンプライアンス](https://go.microsoft.com/fwlink/?linkid=843165)です。  <br/> |[FastTrack](https://go.microsoft.com/fwlink/?linkid=518597)移行支援は、制限されています。  <br/> アップグレードの多くは、手動または SPO の移行 API を使用して、 [SharePoint Online と OneDrive 移行コンテンツのロードマップ](https://go.microsoft.com/fwlink/?linkid=843184)に記載されています。  <br/> |
|マイクロソフト サポート エンジニアも、データ センター内の従業員に無制限に管理者のアクセス、サブスクリプション。  <br/> |ハードウェア ・ インフラストラクチャは、SharePoint の新しいバージョンをサポートするためにアップグレードする必要がある場合、またはセカンダリ ファームのアップグレードに必要な場合、追加のコストが存在することができます。  <br/> |
|SharePoint Online に、データを移行するための一時的なジョブ パートナーを支援できます。  <br/> |SharePoint Online にすべての変更は、コントロール内では。移行後に、デザインのメニューのライブラリ、およびその他の機能に影響が出て一時的に使いやすさ。  <br/> |
|オンラインの製品は、機能を廃止して可能性がありますがない本来のサポート ライフ サイクルの終了を意味するサービスの間で自動的に更新されます。  <br/> |基になる SQL サーバーと SharePoint のサーバー (SharePoint Foundation) のサポート ライフ サイクルの終了があります。  <br/> |
   
新しい Office 365 サイトを作成するし、手動で移行データには、必要に応じて、Office 365 のオプション権利をここで見ることができます。
  
[Office 365 プランのオプション](https://go.microsoft.com/fwlink/?linkid=843151)
  
### <a name="upgrade-sharepoint-server-on-premises"></a>アップグレードの SharePoint サーバーの設置型

SharePoint のオンプレミス製品 (SharePoint Server 2016) の最新バージョンの SharePoint サーバーのアップグレードが*連続して*移動する必要がありますと SharePoint サーバーの 2016年を直接 SharePoint Server 2010 からアップグレードする方法がないことを意味します。 
  
|||
|:-----|:-----|
||シリアル ・ アップグレードのパス: SharePoint Server 2010 **\>** SharePoint Server 2013 **\>** SharePoint サーバー 2016。 |
   
この時間がかかる場合は、SharePoint 2010 の SharePoint サーバーの 2016年を次のパス全体を選択すると、計画とします。アップグレードには、(SQL サーバーもアップグレードする必要があることに注意する)、アップグレードされたハードウェア、ソフトウェア、および管理の面でコストが含まれています。また、カスタマイズは、アップグレード、またはも破棄する必要があります。SharePoint サーバー ファームをアップグレードする前に、すべての重要なカスタマイズのメモを収集することを確認します。
  
> [!NOTE]
> 自分の側のサポート SharePoint 2010 ファームの管理、(別のファームでは、サイド バイ サイドを実行) のための新しいハードウェアは、[SharePoint のサーバーの 2016年ファームのインストール、計画し、(とコンテンツのダウンロードのコンテンツを再アップロードするを手動での移行を実行することはなど)。(ドキュメントなどから 2010 に、手動での移動を実行するアカウントのエイリアスを持つ現在最終修正されたアカウントを持つ)、手動でこれらの移動に潜在的な落とし穴があり、事前にいくつかの作業を行う必要があります (サイト、サブサイトのアクセス許可を再作成し、リスト構造の場合)。ストレージ、または不要になったを移動するデータが必要なものを検討するよい機会です。これは、移行の影響を削減できます。どちらの方法は、環境の前に、アップグレードをクリーニングします。既存のファームでは、アップグレードする前に機能し、解除する前に (確認) を特定します。 
  
**サポート対象およびサポートされていないアップグレード ・ パス**を確認するのには注意してください。 
  
- [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843156)
    
- [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843157)
    
**カスタマイズ**をした場合は、計画がある、ステップごとに、アップグレード、移行パスでが重要です。 
  
- [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843160)
    
- [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843162)
    
|**オンプレミス Pro**|**設置詐欺**|
|:-----|:-----|
|フル コントロール、SharePoint ファーム (およびその SQL) のすべての側面サーバーのハードウェアからをします。  <br/> |すべての破断や修正プログラムは、会社の責任 (ただし、マイクロソフトの有償サポートを依頼するには、お使いの製品サポートの端にある場合)。  <br/> |
|SharePoint サーバー設置型のハイブリッドを使用して SharePoint Online サブスクリプションに、オンプレミスのファームに接続するためのオプションの完全な機能セットです。  <br/> |アップグレード、修正プログラム、セキュリティ修正プログラム、ハードウェアのアップグレード、および SharePoint Server と SQL のファームのすべてのメンテナンスは、管理対象の設置型です。  <br/> |
|SharePoint online よりも大きい値のカスタマイズ オプションにアクセスできます。  <br/> |[Office 365 でサポートされているコンプライアンス基準](https://go.microsoft.com/fwlink/?linkid=843165)には、オンプレミスで手動で構成されている必要があります。  <br/> |
|セキュリティ テスト、およびサーバーのパフォーマンスのチューニング、お客様のサイト (コントロール)] の下で実行されます。  <br/> |Office 365 にすることが機能使用可能な SharePoint オンラインの SharePoint サーバーの設置型と相互運用できません。  <br/> |
|パートナーは、移行を支援できる SharePoint サーバーの (および外) は、次のバージョンへのデータ。  <br/> |SharePoint サーバーのサイトに自動的には使用されません[SSL や TLS](https://go.microsoft.com/fwlink/?linkid=843167)証明書 SharePoint Online] に表示されるように。  <br/> |
|名前付け規則、バックアップと復元、および SharePoint サーバーの設置型の場合は、他の回復オプションのフル コントロール。  <br/> |SharePoint サーバーの設置型は、製品のライフ サイクルに重要です。  <br/> |
   
### <a name="upgrade-resources"></a>リソースをアップグレードします。

ハードウェアとソフトウェアの要件を比較することによって開始します。現在のハードウェアのアップグレードのための基本的な要件を満たしていない場合、は、最初に、ファームまたは SQL サーバーのハードウェアをアップグレードする必要がありますまたはことは、サイトのいくつかの割合を SharePoint Online の '常緑' のハードウェアに移動することがでく可能性があります。に従って、評価を行った後に、アップグレード ・ パスやメソッドがサポートされています。
  
- **ハードウェア/ソフトウェアの要件**: 
    
    [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843204) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843206) | [SharePoint サーバー 2016年](https://go.microsoft.com/fwlink/?linkid=843207)
    
- **ソフトウェアの境界と制限**します。 
    
    [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843247) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843248) | [SharePoint サーバー 2016年](https://go.microsoft.com/fwlink/?linkid=843249)
    
- **のアップグレード プロセスの概要**: 
    
    [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843251) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843252) | [SharePoint サーバー 2016年](https://go.microsoft.com/fwlink/?linkid=843359)
    
### <a name="create-a-sharepoint-hybrid-solution-between-sharepoint-online-and-sharepoint-server-on-premises"></a>SharePoint Online と SharePoint サーバーの設置型の SharePoint のハイブリッド ソリューションを作成します。

(設置型といくつかの移行のためのオンラインの世界の両方の可能性がある必要があります) 別のオプションは、ハイブリッド、SharePoint のハイブリッドを作成する SharePoint Online に SharePoint Server 2013 または 2016 ファームを接続することができます: ハイブリッド ソリューションの SharePoint の[について](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx).
  
ハイブリッドの SharePoint サーバー ファームでは、移行の目標を決定する場合は、どのようなサイトとユーザーを計画する、オンラインに移動する必要があり、設置型を維持する必要があることを確認します。レビューと (高、中、または低の影響、会社には、どのようなデータを決定する)、SharePoint サーバー ファームのコンテンツのランク付けは、この決定を行うに役に立ちます。SharePoint Online で共有する必要がありますですだけが (a) ユーザーのアカウントのログイン、および (b)、SharePoint サーバーの検索インデックス--クリアできない可能性がありますこのサイトの使用方法を確認するまでがあります。Office 365 で SharePoint ファームの管理が行われ、残りのすべてのアカウントとデータをオンラインに移動して、設置型のファームを非コミッションに場合は、会社は、SharePoint Online に移行するすべてのコンテンツを後で決定したら、その時点からのコンソールです。
  
既存の型のハイブリッドと、設置型の SharePoint ファームと Office 365 サブスクリプション間の接続を構成する方法について理解しておくことを確認します。
  
ハイブリッドの SharePoint ファームの動作を確認する方法の 1 つは、 [Office 365 の開発/テスト環境](https://go.microsoft.com/fwlink/?linkid=843152)を作成することによってです。試用版があるか、Office 365 のサブスクリプションを購入するには、なりますようにデータを移行することができますし、SharePoint Online サイト コレクション、web、およびドキュメント ライブラリを作成する (使用するか、手動での移行 API、または移行する場合は、マイサイトのコンテンツのビジネス ・ OneDrive にハイブリッドのウィザードを使用)。
  
> [!NOTE]
> SharePoint Server 2010 ファームをアップグレードする必要が最初に注意してください、設置型、型、または SharePoint Server 2013 ハイブリッド オプションを使用する SharePoint サーバーの 2016年をします。SharePoint Foundation 2010 と SharePoint Foundation 2013 の場合は、SharePoint Online のハイブリッド接続を作成できません。 
  
## <a name="related-topics"></a>関連項目

[Office 2007 からアップグレードするか、2010 のサーバーとクライアントを支援するためのリソース](upgrade-from-office-2010-servers-and-products.md)
  
[Overview of the upgrade process from SharePoint 2010 to SharePoint 2013](https://technet.microsoft.com/en-us/library/mt493301%28v=office.16%29.aspx)
  
[SharePoint 2010 から SharePoint 2013 へのアップグレードのベスト プラクティス](https://technet.microsoft.com/en-us/library/mt493305%28v=office.16%29.aspx)
  
[SharePoint 2013 でのデータベース アップグレードの問題のトラブルシューティング](https://go.microsoft.com/fwlink/?linkid=843195)
  
[アップグレードを支援するマイクロソフトのパートナーの検索](https://go.microsoft.com/fwlink/?linkid=841249)
  
[更新された SharePoint 2013 製品サービス ポリシー](https://technet.microsoft.com/en-us/library/mt493253%28v=office.16%29.aspx)
  
[更新された SharePoint Server 2016 製品サービス ポリシー](https://technet.microsoft.com/en-us/library/mt782882%28v=office.16%29.aspx)
  

