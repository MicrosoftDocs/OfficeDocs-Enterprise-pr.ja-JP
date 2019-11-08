---
title: アクセス可能な図 - Microsoft Lync 2013 プラットフォーム オプション
ms.author: josephd
author: JoeDavies-MSFT
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 2858d1e7-be37-4484-b121-a99779742a38
description: この記事は、Microsoft Lync 2013 プラットフォーム オプションという名前のダイアグラム (技術ダイアグラム で利用できます) のアクセス可能なテキスト バージョンです。
ms.openlocfilehash: a62fb6d1e1ee7fbddb79b0aec4ddafea4b07b4fe
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/07/2019
ms.locfileid: "38030601"
---
# <a name="accessible-diagram---microsoft-lync-2013-platform-options"></a>アクセス可能な図 - Microsoft Lync 2013 プラットフォーム オプション

**概要:** この記事は、Microsoft Lync 2013 プラットフォーム オプションという名前のダイアグラム ([技術ダイアグラム](https://go.microsoft.com/fwlink/?LinkID=519139&amp;clcid=0x409)で利用できます) のアクセス可能なテキスト バージョンです。
  
このポスターは、ビジネスの意思決定者 (BDM) と設計者が Lync Online (Office 365) および Lync Server の展開に関して知る必要のある情報を説明しており、内容は次のとおりです。
  
- 4 つの異なる展開オプションの比較:Lync Online (Office 365)、Lync Online/Server ハイブリッド、Lync Server、およびプロバイダー ホスト型の Lync Server。 
    
- Lync 2013 を展開するための 2 つのシナリオ例。
    
## <a name="comparison-of-four-different-deployments-for-the-lync-2013-platform"></a>Lync 2013 プラットフォーム用の 4 つの異なる展開の比較

比較の結果は以下の領域での各展開オプションに関する情報を提供します。 
  
- 各種の展開機能の概要
    
- 各展開オプションを実装するメリット
    
- ライセンス要件
    
- 必要なアーキテクチャ タスク
    
- 各展開オプションを実装するための IT 技術者の責任
    
### <a name="overview"></a>概要

#### <a name="lync-online-office-365"></a>Lync Online (Office 365)

Office 365 マルチテナント プランを使用すると、効率を高めコストを最適化できます。
  
付随する図は Lync Online に伴う Azure Active Directory テナントを示しています。これは、オンプレミスの Active Directory ドメイン サービス (AD DS) 環境と Azure Active Directory テナントの間で、アカウント名およびパスワードを同期させます。 
  
フィーチャーと機能の説明:
  
- サービスとしてのソフトウェア (SaaS)。
    
- 常に最新の豊富な機能セット。
    
- 他のアプリケーションと共に使用できる、オンラインのアカウント用の Azure Active Directory テナントが含まれます。 
    
- ディレクトリの統合には、社内 Active Directory Domain Services (AD DS) 環境と Azure Active Directory テナント間でアカウント名とパスワードを同期させることが含まれます。
    
- シングル サインオン (SSO) が要件である場合、Active Directory フェデレーション サービス(AD FS) を実装する必要があります。 
    
- インターネット経由のクライアント通信は、暗号化されて認証されます。
    
- 従来の電話装置、公衆交換電話網 (PSTN)、接続は、サード パーティ プロバイダーを通じて利用可能です。
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a>Lync Online/Server ハイブリッド (ドメインを分割)

Office 365 の利点を Lync 2013 の社内展開と組み合わせることができます。
  
付属の図は、一部のユーザーは社内に配置され、一部のユーザーはオンラインに配置されている、Lync Online を使用する Office 365 を示しています。社内に展開されたエッジ サーバーも示されています。
  
フィーチャーと機能の説明:
  
- 一部のユーザーは社内に配置され、一部のユーザーはオンラインに配置されていますが、それらのユーザーは同じ SIP ドメイン (contoso.com など) を共有します。
    
- PSTN への接続など、既存の Lync Server 2013 インフラストラクチャを活用します。
    
- PSTN を必要としない場合は、新規の Lync オンライン ユーザーを簡単に追加します。
    
- スケジュールに従って、時の経過と共に Lync オンプレミスから Lync Online に移行します。
    
- Exchange Online や SharePoint Online など、他の Office 365 アプリケーションと統合します。
    
#### <a name="lync-server"></a>Lync Server

この展開では、自らすべてを所有しています。付随する図は、社内の Active Directory ドメイン サービス (AD DS) 環境を持つ Lync Server インフラストラクチャを示しています。ここでは、ユーザーは社内に配置されています。
  
フィーチャーと機能の説明:
  
- 容量計画とサイジング。
    
- サーバーの購入とセットアップ。
    
- 展開。
    
- スケール アウト、修正、および操作。
    
- データのバックアップ。
    
- フェールオーバーと障害復旧の保守。
    
- PSTN への Lync Server 2013 インフラストラクチャの接続。
    
- 構内交換機 (PBX) など、既存の電話機器との統合。
    
#### <a name="provider-hosted-lync-server"></a>プロバイダー ホスト型の Lync Server

この展開では、すべてをプロバイダーが所有します。付属の図は、社内環境に接続されたサーバと機器など、プロバイダーのネットワークを示しています。
  
フィーチャーと機能の説明:
  
- 容量計画とサイジング。
    
- サーバーの購入とセットアップ。
    
- 展開。
    
- スケール アウト、修正、および操作。
    
- データのバックアップ。
    
- フェールオーバーと障害復旧の保守。
    
- 構内交換機 (PBX) など、既存の電話機器との統合。
    
- さらに、プロバイダーは以下を行うことができます。
    
  - 自社の社内システムに接続するプロバイダー所有のネットワークに、サーバーや装置を設置する (実線)。
    
  - 自社の社内システムに、プロバイダー所有のサーバーを設置する (点線)。
    
### <a name="benefits-of-implementing-each-deployment-option"></a>各展開オプションを実装するメリット

#### <a name="lync-online-office-365"></a>Lync Online (Office 365)

- 社内サーバーやサーバー ソフトウェアを運用するときのような負荷はありません。
    
- クラウド ベースのサービスとしての Lync Server 2013 の通信機能。
    
- Lync プレゼンス、インスタント メッセージング、音声とビデオの通話、機能が豊富なオンライン会議、およびさまざまな Web 会議機能。
    
- 地理的に分散した組織や、主にモバイルの従業員によって使用されます。
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a>Lync Online/Server ハイブリッド (ドメインを分割)

- リモート ユーザーのため、およびビジネス パートナーとの統合のために Lync Online を使用。
    
- 社内の Lync から Lync Online への移行が容易。
    
- リモート サイトのサポートに、ブランチ オフィス アプライアンスが不要。
    
- 新規事業取得時の Lync サポートの追加が容易。
    
#### <a name="lync-server"></a>Lync Server

- プライベート クラウド ソリューション。
    
- 高度にカスタマイズされたソリューション。
    
- Lync Online でサポートされていないハードウェアおよびソフトウェアに依存するサード パーティ製コンポーネントを持つレガシー ソリューション。
    
- AD DS アカウントと Office 365 との同期を防止するプライバシー制限。
    
- プラットフォームとソリューション全体のコントロールを望む企業。
    
- PBX の Lync エンタープライズ VoIP への置き換え。
    
#### <a name="provider-hosted-lync-server"></a>プロバイダー ホスト型の Lync Server

- Lync Server の機能を必要としているものの、その展開と保守をアウトソース化することを希望する組織。
    
- プロバイダー ベースのソリューション。
    
- 高度にカスタマイズされたソリューション。
    
- Lync Online でサポートされていないハードウェアおよびソフトウェアに依存するサード パーティ製コンポーネントを持つレガシー ソリューション。
    
- PBX の Lync エンタープライズ VoIP への置き換え。
    
### <a name="license-requirements"></a>ライセンス要件

#### <a name="lync-online-office-365"></a>Lync Online (Office 365)

サブスクリプション モデル。
  
#### <a name="lync-onlineserver-hybrid-split-domain"></a>Lync Online/Server ハイブリッド (ドメインを分割)

- Office 365  サブスクリプション モデル。追加のライセンスは不要です。 
    
- オンプレミス — すべてのオンプレミス ライセンスが適用されます。 
    
#### <a name="lync-server"></a>Lync Server

- サーバー オペレーティング システム
    
- SQL Server
    
- Lync 2013 Server のライセンス
    
- Lync 2013 クライアント アクセスのライセンス
    
#### <a name="provider-hosted-lync-server"></a>プロバイダー ホスト型の Lync Server

コストは、Lync のソリューション プロバイダーとの契約に基づいて決まります。
  
### <a name="architecture-tasks"></a>アーキテクチャ タスク

ここでは各展開オプションのアーキテクチャのタスクを示します。
  
#### <a name="lync-online-office-365"></a>Lync Online (Office 365)

- ディレクトリ同期を計画および設計します。
    
- ファイアウォール、プロキシ サーバー、ゲートウェイ、および WAN リンク全体におけるネットワークの容量と可用性を確保します。
    
- Office 365 サービス内容にエンタープライズ セキュリティを付加するために、サード パーティの SSL 証明書を取得します。
    
- インターネット プロトコル バージョン 6 (IPv6) を使用して Office 365 に接続するかどうかを決めます。
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a>Lync Online/Server ハイブリッド (ドメインを分割)

Office 365 と社内環境の両方のタスクに加えて:
  
- Exchange Server や SharePoint のオンプレミス バージョンとオンライン バージョンのうち、どれほどの機能を統合するかを決めます。
    
- 必要な場合、Office 365 からの要求のためにどのプロキシ サーバー デバイスを使用するかを決めます。
    
#### <a name="lync-server"></a>Lync Server

既存の社内環境における Lync 環境の設計:
  
- 本店と支店での Lync のトポロジ。
    
- 仮想化を含む、サーバー ハードウェア。
    
- Active Directory ドメイン サービス (AD DS) と DNS の統合。
    
- Lync Server プールの負荷分散 。
    
- フェールオーバーと障害復旧。
    
#### <a name="provider-hosted-lync-server"></a>プロバイダー ホスト型の Lync Server

- クラウド ベースのインストールでは、サービス プロバイダーのネットワークへの接続を決めます。
    
- 社内インストールでは、プロバイダーの Lync サーバーをネットワーク内のどこに配置するかを決めます。
    
- どちらのタイプの場合も、AD DS と PBX 機器との統合を決めます。
    
### <a name="it-pro-responsibilities"></a>IT 技術者の責任

ここでは、各展開オプションについて、IT 担当者の責任を示します。
  
#### <a name="lync-online-office-365"></a>Lync Online (Office 365)

Lync Online の展開と管理 (Office 365):
  
- ディレクトリ同期の計画を実装します。
    
- 内部および外部の DNS レコードとルーティングを計画し、実装します。
    
- Office 365 の IP アドレスと URL 要件に合わせてプロキシまたはファイアウォールを構成します。
    
- ユーザー アカウントと Lync Online の設定を管理します。
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a>Lync Online/Server ハイブリッド (ドメインを分割)

Office 365 と社内環境の両方のタスクに加えて:
  
- 必要であれば、プロキシ サーバー デバイスを構成します。
    
- Exchange Server や SharePoint の社内バージョンとオンライン バージョンの機能統合を構成します。
    
#### <a name="lync-server"></a>Lync Server

社内環境で Lync Server を展開して管理します:
  
- サーバーを準備します。
    
- Lync トポロジを展開します。
    
- Lync サーバーを更新します。
    
- 使用状況に応じて、トポロジ サーバーを追加または削除します。
    
- フェイル オーバーと障害復旧環境を実装します。
    
#### <a name="provider-hosted-lync-server"></a>プロバイダー ホスト型の Lync Server

プロバイダーと協力して次のことを行います。
  
- Lync Server をネットワークに統合します。
    
- Lync Server を他の Microsoft 製品やカスタム ソリューションと統合します。
    
- プロバイダーのサービス レベル契約 (SLA) の遵守を監視します。
    
## <a name="two-example-scenarios-for-deploying-lync-2013"></a>Lync 2013 を展開するための 2 つのシナリオ例

### <a name="directory-synchronization-components-in-microsoft-azure"></a>Microsoft Azure のディレクトリ同期コンポーネント

Azure では仮想マシンをオンデマンドで展開できるため、Office 365 ディレクトリ統合コンポーネントをより速く展開できます。
  
付随する図は Lync Online に伴う Azure Active Directory テナントを示しています。これは、オンプレミスの Active Directory 環境と Azure Active Directory テナントの間で、アカウント名およびパスワードを同期させます。
  
 **ディレクトリ同期サーバーのみ**。64 ビットのディレクトリ同期サーバーを社内環境に展開する代わりに、仮想マシンをインターネット上で Azure にプロビジョニングします。
  
 **ディレクトリ同期 + AD FS**。このオプションにより、社内インフラストラクチャにハードウェアを追加しなくても、Office 365 フェデレーション ID (SSO) をサポートできます。さらに、社内の Active Directory 環境が使用できない場合に、回復性を提供します。このオプションには以下の機能が含まれます。
  
- Azure 仮想マシンとして実行するディレクトリ統合コンポーネント。
    
- AD FS は、Azure 仮想マシンとして実行している AD FS プロキシを介してインターネットに公開されます。
    
- 任意の場所から接続するユーザーのためのクライアント認証トラフィックは、Azure 仮想マシンとして展開された AD FS サーバーおよびプロキシにより処理されます。
    
### <a name="lync-integration-with-exchange-and-sharepoint-in-office-365"></a>Office 365 内での Lync と Exchange、SharePoint との統合

#### <a name="lync-server-with-exchange-online-and-sharepoint-online"></a>Lync Server を Exchange Online および SharePoint Online と併用する

付属の図は、Exchange Online や SharePoint Online が社内 Lync Server 2013 ファームに接続された Office 365 を示しています。
  
この展開の利点により、以下が可能になります。
  
- Lync Server 2013 のフル機能セットを使用できます。
    
- PBX などの既存の社内電話機器を活用できます。
    
- Exchange Online を電子メールに使用して、社内の電子メール サーバーとストレージの負荷を軽減します。
    
- SharePoint Online を共同作業に使用して、社内の SharePoint サーバーを保守する負荷を軽減します。
    
- Office 365 のユニファイド メッセージング (UM) など、Lync、Exchange、および SharePoint の統合機能を使用します。
    
#### <a name="exchange-server-with-lync-online"></a>Exchange Server と Lync Online

付属の図は、Lync Online が社内 Exchange Server ファームに接続された Office 365 を示しています。
  
この展開の利点により、以下が可能になります。
  
- 既存の Exchange のインフラストラクチャを活用します。
    
- Lync Online をプレゼンス、インスタント メッセージング、および会議の機能のために使用します。
    

