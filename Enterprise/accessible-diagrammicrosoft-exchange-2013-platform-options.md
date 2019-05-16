---
title: アクセス可能な図 - Microsoft Exchange 2013 プラットフォーム オプション
ms.author: josephd
author: JoeDavies-MSFT
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 129f4e45-647e-4cf1-92a6-4d86d8396e73
description: この記事は、Microsoft Exchange 2013 プラットフォーム オプションという名前のダイアグラム (技術ダイアグラム で利用できます) のアクセス可能なテキスト バージョンです。
ms.openlocfilehash: ddf215544b811257e6d43f212784a3a1e5aac7b0
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068593"
---
# <a name="accessible-diagram---microsoft-exchange-2013-platform-options"></a>アクセス可能な図 - Microsoft Exchange 2013 プラットフォーム オプション

**概要:** この記事は、Microsoft Exchange 2013 プラットフォーム オプションという名前のダイアグラム ([技術ダイアグラム](http://go.microsoft.com/fwlink/?LinkID=519139&amp;clcid=0x409)で利用できます) のアクセス可能なテキスト バージョンです。
  
このポスターは、ビジネスの意思決定者 (Bdm) と設計者が Exchange Online および Exchange Server の展開に関して知る必要のある情報を説明しており、内容は次のとおりです。 
  
- Exchange 2013 で使用可能な 4 つのプラットフォーム オプションの比較: Exchange Online (Office 365)、Exchange ハイブリッド、Exchange Server オンプレミス、プロバイダー向けのホスト型 Exchange。 
    
- Exchange 2013 での 3 つの新しいまたは更新された機能の説明。 
    
## <a name="comparison-of-four-different-deployments-for-the-exchange-2013-platform"></a>Exchange 2013 プラットフォーム用の 4 つの異なる展開の比較

比較の結果は以下の領域での各展開オプションに関する情報を提供します。 
  
- 各種の展開機能の概要 
    
- 各展開オプションを実装するメリット 
    
- ライセンス要件 
    
- 必要なアーキテクチャ タスク 
    
- 各展開オプションを実装するための IT 技術者の責任 
    
### <a name="overview"></a>概要

#### <a name="exchange-online-office-365"></a>Exchange Online (Office 365)

Office 365 によって効率を上げ、コストを下げられます。
  
付随する図は Exchange Online に伴う Azure Active Directory テナントを示しています。これは、オンプレミスの Active Directory ドメイン サービス (AD DS) 環境と Azure Active Directory テナントの間で、アカウント名およびパスワードを同期させます。シングル サインオンには Active Directory フェデレーション サービス (AD FS) が必要です。 
  
フィーチャーと機能の説明:
  
- サーバーおよびサーバー ソフトウェアの動作は、Microsoft によって処理されます。
    
- クラウドベースのサービスとしての Exchange Server 2013 の豊富な機能セット。
    
- 最新の機能で常に最新です。
    
- スパム対策およびマルウェア対策の保護のため、Exchange Online Protection (EOP) が組み込まれています。
    
- 99.9% のサービス レベル契約 (SLA) を実現する組み込みの高可用性。
    
- オンプレミスの Active Directory ドメイン サービス (AD DS) と Azure Active Directory テナントとの間でのパスワードの同期を含む Directory 同期。シングル サインオンには Active Directory フェデレーション サービス (AD FS) が必要です。
    
#### <a name="exchange-hybrid"></a>Exchange ハイブリッド

Exchange Server オンプレミスを維持しながら Office 365 の利点を活用できます。
  
付随する図は、一部のユーザーが社内に配置され、他のユーザーがオンラインに配置されている、Exchange Online での Office 365 を示しています。それには Azure Active Directory テナントも示されていますが、それは、オンプレミスの Active Directory ドメイン サービス (AD DS) 環境と Azure Active Directory テナントとの間でアカウント名およびパスワードを同期させます。
  
フィーチャーと機能の説明:
  
- 一部のユーザーは社内に配置され、他のユーザーはオンラインに配置されていて、それらのユーザーは同じ電子メール アドレス スペースを共有します。
    
- 既存の Exchange Server のインフラストラクチャを活用します。
    
- スケジュールに従って、時の経過と共に Exchange オンプレミスから Exchange Online に移行します。
    
- Lync Online や SharePoint Online など、他の Office 365 アプリケーションと統合します。
    
#### <a name="exchange-server-on-premises"></a>Exchange Server オンプレミス

独自の Exchange Server 2013 インフラストラクチャを設計して管理できます。
  
付随する図は、オンプレミスの Active Directory ドメイン サービス (AD DS) 環境を持つ Exchange Server インフラストラクチャを示しています。ここでは、ユーザーは社内に配置されています。
  
フィーチャーと機能の説明:
  
- ご使用の環境にとって最高度のコントロールとカスタマイズ。
    
- 負荷分散のレイヤーでセッション類似性を維持するための依存関係はありません。
    
- データベース可用性グループ (DAG) の使用によるシンプルな高可用性とサイト復元。
    
- 優れたユーザー エクスペリエンスを維持するのに役立つ、管理された可用性。
    
- 既存のハードウェアと記憶域インフラストラクチャを活用できます。
    
#### <a name="provider-hosted-exchange"></a>プロバイダー向けのホスト型 Exchange

Exchange Server ワークロードを Exchange Server ソリューション プロバイダーにアウトソースすることができます。
  
付随する図は、プロバイダーによって操作され、管理される Exchange Server 環境を示しています。
  
フィーチャーと機能の説明:
  
- サーバーおよびサーバー ソフトウェアの動作は、プロバイダーによって処理されます。
    
- Exchange Server インフラストラクチャの計画、サイズ変更、スケール、および保守は、プロバイダーに委任されます。
    
- サービスの保守は、プロバイダーによって処理されます。
    
- Exchange の機能セットは、プロバイダーで展開されているソフトウェアのバージョンに限定されます。
    
### <a name="benefits-of-implementing-each-deployment-option"></a>各展開オプションを実装するメリット

#### <a name="exchange-online-office-365"></a>Exchange Online (Office 365)

この展開オプションは次の場合に最適です。
  
- オンプレミスの Exchange 展開のための運用コストの削減を検討している組織。
    
- SharePoint Online や Lync Online など、他の Office 365 提供物を活用することを計画している組織。
    
#### <a name="exchange-hybrid"></a>Exchange ハイブリッド

この展開オプションは次の場合に最適です。
  
- Exchange オンプレミスから Exchange Online への移行を容易にします。
    
- 支店のインフラストラクチャに投資することなく、リモート サイトをサポートします。
    
- データを社内で保持する必要のある、子会社を持つ多国籍企業。
    
#### <a name="exchange-server-on-premises"></a>Exchange Server オンプレミス

この展開オプションは次の場合に最適です。
  
- 高度にカスタマイズされたソリューション。
    
- Exchange Online でサポートされていないハードウェアおよびソフトウェアに依存するサード パーティ製コンポーネントを使用するレガシー ソリューション。
    
- データを社内で保持することを必要とするデータ ガバナンス規制のもとにある組織。
    
- プラットフォームとソリューションの全体のコントールを維持することを求める組織。
    
#### <a name="provider-hosted-exchange"></a>プロバイダー向けのホスト型 Exchange

この展開オプションは次の場合に最適です。
  
- Exchange Server の機能を必要とするものの、その展開と保守を外部委託することを希望している組織。
    
- 個人用のサポート オプションが必要な組織。
    
- カスタマイズしたソリューションと、プロバイダーによって提供されるカスタム アプリケーションとの統合。
    
- Exchange Online でサポートされていないハードウェアおよびソフトウェアに依存するサード パーティ製コンポーネントを使用するレガシー ソリューション。
    
### <a name="license-requirements"></a>ライセンス要件

次の表は、各展開オプションのライセンス要件の詳細を示しています。
  
|**展開オプション**|**ライセンス要件**|
|:-----|:-----|
|Exchange Online (Office 365)  <br/> |サブスクリプション モデル  <br/> |
|Exchange ハイブリッド  <br/> | Office 365 - サブスクリプション モデル <br/>  オンプレミス - すべてのオンプレミス ライセンスが当てはまります (Exchanges Server オンプレミスのライセンスを確認してください) <br/>  ハイブリッド サーバー ライセンス * <br/> |
|Exchange Server オンプレミス  <br/> | サーバー オペレーティング システム <br/>  Exchange 2013 サーバー ライセンス <br/>  Exchange 2013 クライアント アクセス ライセンス <br/> |
|プロバイダー向けのホスト型 Exchange  <br/> |コストは、プロバイダーとの契約に基づきます  <br/> |
   
### <a name="architecture-tasks"></a>アーキテクチャ タスク

ここでは各展開オプションのアーキテクチャのタスクを示します。
  
#### <a name="exchange-online-office-365"></a>Exchange Online (Office 365)

- ディレクトリ同期を計画および設計します。
    
- ネットワーク容量を確認し、ファイアウォール、プロキシ サーバー、ゲートウェイ、および WAN リンクを介した接続を確認します。
    
#### <a name="exchange-hybrid"></a>Exchange ハイブリッド

Office 365 環境とオンプレミス環境の両方のアーキテクチャ タスクに加えて:
  
- シングル サインオン エクスペリエンスを提供するかどうかを決定します。
    
- 受信インターネット メールを社内組織を通してルーティングするか、 Exchange Online Protection を介してルーティングするかを決定します。
    
#### <a name="exchange-server-on-premises"></a>Exchange Server オンプレミス

- Exchange トポロジを設計します。
    
- サーバー ハードウェアの容量を計画します。
    
- メッセージのルーティング トポロジを設計します。
    
- クライアント アクセス サーバーの負荷分散を設計します。
    
- データベース可用性グループを使用して高可用性を計画します。
    
#### <a name="provider-hosted-exchange"></a>プロバイダー向けのホスト型 Exchange

ネットワーク容量を確認し、ファイアウォール、プロキシ サーバー、ゲートウェイ、および WAN リンクを介した可用性がプロバイダーで使用可能であることを確認します。
  
### <a name="it-pro-responsibilities"></a>IT 技術者の責任

ここでは、各展開オプションについて、IT 担当者の責任を示します。
  
#### <a name="exchange-online-office-365"></a>Exchange Online (Office 365)

- ディレクトリ同期の計画を実装します。
    
- 内部および外部の DNS レコードとルーティングを計画し、実装します。
    
- Office 365 の IP アドレスおよび URL の要件に合うように、プロキシ サーバーまたはファイアウォールを構成します。
    
- ユーザー アカウントと Exchange Online の設定を管理します。
    
#### <a name="exchange-hybrid"></a>Exchange ハイブリッド

Office 365 環境とオンプレミス環境の両方の IT 技術者の責任に加えて:
  
- Active Directory フェデレーション サービス (AD FS) をシングル サインオン用に構成します (希望する場合)。
    
- Exchange 2013 サーバーと Office 365 との保護された通信のために、Exchange 証明書を構成します。
    
- DNS レコードを、希望する受信インターネット メール パス向けに構成します。
    
#### <a name="exchange-server-on-premises"></a>Exchange Server オンプレミス

- Exchange サービスのために必要な証明書を構成します。
    
- サーバーを準備します。
    
- Exchange のメッセージ ルーティング トポロジを実装します。
    
- データベース可用性グループを実装します。
    
- Exchange サーバーを更新し、維持します。
    
- 使用率に応じて、必要なときにサーバーを追加または削除します。
    
#### <a name="provider-hosted-exchange"></a>プロバイダー向けのホスト型 Exchange

プロバイダーの責任は次のとおりです。
  
- システムとサービスの保守。
    
- 機能の展開。
    
- データの保護と災害復旧。
    
組織内の IT スタッフの責任には、ユーザー アカウントの作成と管理が含まれます。
  
#### <a name="more-information"></a>詳細情報

Exchange Online (Office 365) の詳細については、以下を参照してください:
  
- [Exchange Online サービスの説明](https://aka.ms/EXOSD)
    
- [TechNet の Exchange Online のライブラリ](https://aka.ms/EXOTN)
    
- [Exchange Online ポータル](https://aka.ms/EXO)
    
Exchange ハイブリッドの詳細については、以下を参照してください:
  
- [Exchange 2013 ハイブリッド展開](https://aka.ms/ExchangeHybrid)。ハイブリッド サーバーのライセンスが必要になるのは、以下のシナリオの場合だけです: Exchange 2013 のハイブリッド サーバーと共に Exchange 2010 を持つ組織。Exchange 2013 または Exchange 2010 のハイブリッド サーバーと共に Exchange 2007 を持つ組織。
    
- [Office 365 へのサインイン](https://aka.ms/HybridKey)
    
Exchange Server オンプレミスの詳細については、以下を参照してください:
  
- [TechNet の Exchange Server 2013 ライブラリ](https://aka.ms/Ex2013TN)
    
- [Exchange Server 2013 ポータル](https://aka.ms/Exchange2013)
    
- [Exchange Server 2013 のアーキテクチャ](https://aka.ms/Ex2013SP1ArchPoster)
    
プロバイダー向けのホスト型 Exchange の詳細については、以下を参照してください:
  
[Exchange Server 2013 のホスティングおよびマルチ テナント ソリューションとガイダンス](https://aka.ms/Ex2013Hosting)
  
## <a name="descriptions-of-three-new-or-updated-features-in-exchange-2013"></a>Exchange 2013 での 3 つの新規または更新された機能の説明

### <a name="exchange-online-protection"></a>Exchange Online Protection

Exchange Online Protection (EOP) は、データ センターのグローバルなネットワークにまたがって展開された保護機能の層を提供することによって、任意の展開のためのスパム対策およびマルウェア対策の保護を提供します。これにより、メッセージング環境の管理を簡略化することができます。EOP は Exchange Online のサブスクリプションに含まれていますが、ハイブリッド展開およびオンプレミス展開のためにそれを活用することもできます。
  
付随する図は、グローバル ネットワーク内に EOP を含む、Exchange Online、Exchange ハイブリッド、および Exchange オンプレミスの展開を示しています。
  
### <a name="exchange-server-deployment-assistant"></a>Exchange Server 展開アシスタント

Exchange Server 展開アシスタントは、現在の環境に関するいくつかの点に関して質問してから、カスタムのステップごとのチェックリストを生成することにより、各種のシナリオに対して Exchange Server を展開するのを支援する、Web ベースのツールです。以前のバージョンの Exchange から Exchange 2013 に移行しているか、Exchange Online に移行しているか、あるいはハイブリッド インフラストラクチャを計画しているかどうかに応じて、Exchange Server 展開アシスタントは、ご使用のシナリオ向けの、カスタマイズされた展開チェックリストを作成します。
  
付随するスクリーン ショットは、Exchange Server 展開アシスタントを使用して作成されたチェックリスト例を示しています。
  
### <a name="integration-with-lync-and-sharepoint"></a>Lync および SharePoint との統合

Exchange Server 2013 には、Lync Server 2013 および SharePoint Server 2013 と統合する多くの機能が含まれています。これらの製品が一緒になって、豊富な一連の機能が提供され、組織全体での共同作業が向上します。 
  
付随する図はサーバー間認証のポスターを示し、ポスターへのリンクが含まれています。 
  
- アーカイブ、保持、および電子情報開示
    
- サイト メールボックス
    
- 統合連絡先ストア
    
- 高解像度のユーザーの写真
    
- Outlook および Outlook Web App での Lync プレゼンス
    
- サーバー間認証
    
- ボイスメール
    
- ミーティングのレコーディング
    
- Exchange タスクの同期
    
付随する図は Exchange Server 2013 SP1 アーキテクチャのポスターを示し、ポスターへのリンクが含まれています。
  

