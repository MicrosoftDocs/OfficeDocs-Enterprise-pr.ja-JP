---
title: "アクセス可能な図 - Microsoft SharePoint 2013 プラットフォーム オプション"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: b88200bf-ced0-4ae6-bbe5-5517377d1be1
description: "この記事は、「Microsoft SharePoint 2013 プラットフォームのオプション」という名前の図のアクセス可能なテキスト バージョンです。"
ms.openlocfilehash: 9cd282cc723376f85fe2cbc5a439ee24fd2ab883
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2017
---
# <a name="accessible-diagram---microsoft-sharepoint-2013-platform-options"></a>アクセス可能な図 - Microsoft SharePoint 2013 プラットフォーム オプション

**概要:** この記事は、「Microsoft SharePoint 2013 プラットフォームのオプション」という名前の図のアクセス可能なテキスト バージョンです。
  
ビジネス意思決定者 (BDM) とアーキテクトが Office 365、Microsoft Azure、およびオンプレミス 展開について知る必要があることは何でしょうか。 
  
このポスターには 2 つのセクションがあります。 
  
- SharePoint 2013 の 4 つの異なる展開の比較:Office 365 の SharePoint、SharePoint 2013、Azure のオンプレミス 展開と SharePoint 2013 の社内展開による Office 365 のハイブリッド。 
    
- Azure に移動する 3 つの一般的なワークロードの説明。 
    
## <a name="comparison-of-four-different-deployments-for-the-sharepoint-2013-platform"></a>SharePoint 2013 プラットフォームの 4 つの異なる展開の比較

比較により、以下の領域に関係する各展開オプションに関する情報が提供されます。 
  
- 各種の展開機能の概要 
    
- 各種類の展開が最適な場合 
    
- ライセンス要件 
    
- 実装に必要なアーキテクチャ タスク 
    
- 実装に対する IT 技術者の責任 
    
### <a name="overview"></a>概要

#### <a name="sharepoint-2013-in-office-365"></a>Office 365 での SharePoint 2013

Office 365 マルチテナント プランにより、効率を高めコストを最適化できます。 
  
付随図は、Azure Active Directory テナントを伴う SharePoint Online を示しています。これは、オンプレミス の Active Directory 環境と Azure Active Directory テナントの間で、アカウント名およびパスワードを同期させます。 
  
機能の説明: 
  
- サービスとしてのソフトウェア (SaaS)。 
    
- 豊富な機能セットは常に最新のものを利用できます。 
    
- Azure Active Directory テナント (他のアプリケーションと併用可能) が含まれます。 
    
- ディレクトリの統合には、オンプレミス Active Direcotry 環境と Azure Active Directory テナント間でアカウント名とパスワードを同期させることが含まれます。 
    
- シングル サインオン (SSO) が要件である場合、Active Directory フェデレーション サービス (AD FS) を実装できます。 
    
- 暗号化された認証済みアクセス (ポート 443) によるインターネット上のクライアント通信。 
    
- データ移行はインターネット上にアップロード可能なものに限られます。 
    
- カスタマイズ:Office 用アプリ、SharePoint、および SharePoint Designer 2013。 
    
#### <a name="hybrid-with-office-365"></a>Office 365 とのハイブリッド

Office 365 の利点を SharePoint 2013 のオンプレミス 展開と組み合わせます。 
  
付属図は、オンプレミスの SharePoint Server 2013 ファームに接続するために Business Connectivity Services (BCS) を使用する Office 365 および SharePoint Online を示しています。 
  
次の機能のいずれかを選択して統合します。 
  
SharePoint Search 
  
- ユーザーは、両方の環境から検索結果を確認できます。 
    
- エクストラネット ユーザーは、オンプレミス Active Directory アカウントによりリモートでログオンし、ハイブリッド機能をすべて使用できます。 
    
BCS
  
SharePoint Online から:ユーザーは、読み取りと書き込み両方の操作を実行できます。BCS サービスは、オンプレミスの SharePoint Server 2013 ファームに接続します。オンプレミス ファーム上で構成された BCS サービスは、オンプレミスの OData サービス エンドポイントへの接続を仲介します。 
  
Duet Enterprise Online 
  
SharePoint Online から、ユーザーは、オンプレミスの SAP システムに対して読み取りおよび書き込みの操作を実行できます。 
  
#### <a name="azure"></a>Azure

プラットフォームと機能のフル コントロールを維持しつつ、クラウドを活用します。 
  
付属図は、SharePoint 2013 ファーム、およびインターネット上でユーザーと接続するか、VPN トンネル経由でオンプレミスの Active Directory と接続する DNS を伴う Windows Server の Active Directory という 2 つのクラウド サービスを含む Azure を示しています。 
  
以下の機能があります。 
  
-  Azure は、SharePoint 2013 ファームをホストするのに必要なインフラストラクチャとアプリ サービスを提供するプラットフォームです。
    
- インフラストラクチャ サービス。 
    
- SQL Server および SharePoint にとって最適なネイティブ クラウド プラットフォームです。 
    
- 無料でコンピューティング リソースをほぼただちに利用できます。 
    
- データセンターやインフラストラクチャではなく、アプリケーションに焦点を合わせます。 
    
- 安価な開発およびテスト環境。 
    
- SharePoint ソリューションは、インターネットからアクセス可能にすることも、サイト間 VPN トンネルを介して企業環境のみからアクセス可能にすることもできます。 
    
- カスタマイズに制限はありません。 
    
#### <a name="on-premises"></a>オンプレミス

すべてを自ら所有しています。 
  
付属図は、すべてのデータベースおよび検索用の専用のアプリケーション サーバーと通信する Web サーバー、アプリケーション サーバー、および Active Directory を伴うオンプレミス 環境を示しています。 
  
以下の機能があります。 
  
- 容量計画とサイジング。 
    
- サーバーの購入とセットアップ。 
    
- 展開。 
    
- スケール アウト、修正、および操作。 
    
- データのバックアップ。 
    
- 障害回復環境の維持。 
    
- カスタマイズに制限はありません。 
    
### <a name="deployment-type-is-best-for---"></a>最適な展開の種類

#### <a name="sharepoint-2013-in-office-365"></a>Office 365 での SharePoint 2013

- 安全な外部共有とコラボレーション。(独自機能) 
    
- イントラネット — チーム サイト、個人用サイト、および内部コラボレーション。 
    
- クラウド内のドキュメント ストレージおよびバージョン管理。 
    
- 基本的な一般向け Web サイト。 
    
Office 365 の専用サブスクリプション プランによる追加機能: 
  
- 他の組織と共有ではない、自社組織専用の Microsoft データ センター機器。 
    
- お客様それぞれの環境は、物理的に別個のネットワーク上に存在します。 
    
- IPSec で保護された VPN またはお客様所有のプライベート接続におけるクライアント通信。2 要素認証はオプションです。 
    
- ITAR サポート プラン。 
    
#### <a name="hybrid-with-office-365"></a>Office 365 とのハイブリッド

- エクストラネット環境を設定する代わりに、外部共有およびコラボレーションに Office 365 を使用します。 
    
- 個人用サイト (OneDrive for Business) をクラウドに移動させ、ユーザーがリモートで簡単にファイルにアクセスできるようにします。 
    
- Office 365 で新しいチーム サイトを開始します。 
    
- Office 365 サイトをオンプレミスの BCS SharePoint 環境と統合します。 
    
#### <a name="azure"></a>Azure

- インターネット サイト向け SharePoint  一般向けサイト。顧客アカウントおよび認証において Azure AD を活用します。 
    
- 開発者環境、テスト環境、ステージング環境 — 環境全体のプロビジョニング (およびその解除) を迅速に行います。 
    
- ハイブリッド アプリケーション — データセンターとクラウドの両方に関係するアプリケーション。 
    
- 障害回復環境  障害から迅速に回復します。料金は使用した分にのみかかります。 
    
- 詳細なレポートまたは監査を必要とするファーム 
    
- Web 分析 
    
- 保存されたデータの暗号化 (データは SQL データベースで暗号化されます)。 
    
#### <a name="data-encryption-at-rest-data-is-encrypted-in-the-sql-databases"></a>保存されたデータの暗号化 (データは SQL データベースで暗号化されます)

- 国内ファーム (データを管轄内に置く必要がある場合)。 
    
- BI データの近くに置く必要のある複雑な BI ソリューション。 
    
- プライベート クラウド ソリューション 
    
- 高度にカスタマイズされたソリューション。 
    
- Azure インフラストラクチャ サービスでサポートされていないハードウェアおよびソフトウェアに依存するサード パーティ製コンポーネントを使用するレガシー ソリューション。 
    
- Active Directory アカウントと Azure Active Directory の同期 (Office 365 の要件) を妨げるプライバシー制限。 
    
- プラットフォームとソリューション全体のコントロールを好む組織。 
    
### <a name="license-requirements"></a>ライセンス要件

#### <a name="sharepoint-2013-in-office-365"></a>Office 365 での SharePoint 2013

サブスクリプション モデル。追加のライセンスは不要です。 
  
#### <a name="hybrid-with-office-365"></a>Office 365 とのハイブリッド

- Office 365  サブスクリプション モデル。追加のライセンスは不要です。 
    
- オンプレミス — すべてのオンプレミス ライセンスが適用されます。 
    
#### <a name="azure"></a>Azure

-  Azure サブスクリプション (サーバーのオペレーティング システムを含む)
    
- SQL Server 
    
- SharePoint 2013 サーバー ライセンス 
    
- SharePoint 2013 クライアント アクセス ライセンス 
    
#### <a name="on-premises"></a>オンプレミス

- サーバー オペレーティング システム 
    
- SQL Server 
    
- SharePoint 2013 サーバー ライセンス 
    
- SharePoint 2013 クライアント アクセス ライセンス 
    
### <a name="architecture-tasks"></a>アーキテクチャ タスク

#### <a name="sharepoint-2013-in-office-365"></a>Office 365 での SharePoint 2013

- ディレクトリ統合の計画と設計。オプションは 2 つあります。いずれのオプションも社内または Azure に展開できます: パスワード同期 (1 台の 64 ビット サーバーが必要)。 SSO (AD FS と複数のサーバーが必要)。 
    
- ファイアウォール、プロキシ サーバー、ゲートウェイ、および WAN リンク全体におけるネットワークの容量と可用性を確保します。 
    
- Office 365 サービス内容にエンタープライズ セキュリティを付加するために、サード パーティの SSL 証明書を取得します。 
    
- テナント名を計画し、サイト コレクション アーキテクチャとガバナンスを設計します。 
    
- SharePoint Online のカスタマイズ、ソリューション、およびアプリを計画します。 
    
- Internet Protocol 6 (IPv6) を使用して Office 365 に接続するかどうかを決定します。これは一般的ではありません。 
    
#### <a name="hybrid-with-office-365"></a>Office 365 とのハイブリッド

Office 365 と社内環境の両方のタスクに加えて: 
  
- どの程度の機能統合が必要かを見定め、ハイブリッド トポロジを選択します。このモデル ポスターを参照してください。どのハイブリッド トポロジを使用しますか。 
    
- 必要であれば、どのプロキシ サーバー デバイスを使用するかを見定めます。 
    
#### <a name="azure"></a>Azure

Azure ネットワーク環境の設計: 
  
- サブネットを含む Azure 内の仮想ネットワーク。 
    
- ドメイン環境およびオンプレミス サーバーとの統合。 
    
- IP アドレスと DNS。 
    
- アフィニティ グループとストレージ アカウント。 
    
Azure における SharePoint 環境の設計: 
  
- SharePoint ファーム トポロジと論理アーキテクチャ。 
    
-  Azure の可用性設定とドメインの更新。
    
- 仮想マシン サイズ。 
    
- 負荷分散エンドポイント。 
    
- パブリック アクセス用の外部エンドポイント (適切な場合)。 
    
- 障害復旧環境。 
    
#### <a name="on-premises"></a>オンプレミス

既存のオンプレミス環境における SharePoint 環境の設計: 
  
- SharePoint ファーム トポロジと論理アーキテクチャ。 
    
- サーバー ハードウェア。 
    
- 仮想環境 (使用している場合)。 
    
- 負荷分散。 
    
- AD DS と DNS の統合。 
    
- 障害復旧環境。 
    
### <a name="it-pro-responsibilities"></a>IT 技術者の責任

#### <a name="sharepoint-2013-in-office-365"></a>Office 365 での SharePoint 2013

- ユーザーのワークステーションが Office 365 クライアントの前提条件を満たしているかを確認します。 
    
- ディレクトリ統合計画を実行します。 
    
- 内部および外部の DNS レコードとルーティングを計画し、実装します。 
    
- Office 365 の IP アドレスおよび URL 要件に合わせてプロキシまたはファイアウォールを構成します。 
    
- サイト コレクションへのアクセス許可を作成して割り当てます。 
    
- SharePoint Online のカスタマイズ、ソリューション、およびアプリを実装します。 
    
- ネットワークの可用性を監視し、潜在的なボトルネックを識別します。 
    
#### <a name="hybrid-with-office-365"></a>Office 365 とのハイブリッド

Office 365 と社内環境の両方のタスクに加えて: 
  
- 必要であれば、プロキシ サーバー デバイスを構成します。 
    
- ハイブリッド ID 管理インフラストラクチャを構成します:SSO および 2 つの環境間のサーバー間認証。 
    
- 選択した機能の統合を構成します:検索、BCS、Duet Enterprise Online。 
    
#### <a name="azure"></a>Azure

Azure および SharePoint 環境を展開および管理します: 
  
- Azure ネットワーク環境を実装および管理します。 
    
- SharePoint 環境を展開します。 
    
- SharePoint ファーム サーバーを更新します。 
    
- ファームの使用状況に応じて、仮想マシンを追加または終了します。 
    
- 必要に応じて、仮想マシンのサイズを拡大または縮小します。 
    
- SharePoint 環境をバックアップします。 
    
- 障害回復環境およびプロトコルを実装します。 
    
#### <a name="on-premises"></a>オンプレミス

社内環境における SharePoint の展開と管理: 
  
- サーバーを準備します。 
    
- SharePoint 環境を展開します。 
    
- SharePoint ファーム サーバーを更新します。 
    
- ファームの使用状況に応じて、ファーム サーバーを追加または削除します。 
    
- SharePoint 環境をバックアップします。 
    
- 障害回復環境およびプロトコルを実装します。 
    
## <a name="three-typical-workloads-to-move-to-azure"></a>Azure に移動する 3 つの一般的なワークロード

### <a name="office-365-plus-directory-components-in-azure"></a>Office 365 および Azure のディレクトリ コンポーネント

Azure における Office 365 ディレクトリ統合コンポーネントの展開は、オンデマンドで仮想マシンを展開できるため、短時間で行えます。 
  
#### <a name="directory-synchronization-server-only"></a>ディレクトリ同期サーバーのみ

64 ビットのディレクトリ同期サーバーをオンプレミス環境に展開する代わりに、Azure に仮想マシンをプロビジョニングします。 
  
付随図は、Azure Active Directory テナントを伴う SharePoint Online を示しています。これは、オンプレミスの Active Directory 環境と Azure Active Directory テナントの間で、アカウント名およびパスワードを同期させます。 
  
#### <a name="directory-synchronization-plus-ad-fs"></a>ディレクトリ同期および AD FS

このオプションにより、オンプレミス インフラストラクチャにハードウェアを追加しなくても、Office 365 フェデレーション ID (SSO) をサポートできます。さらに、オンプレミス Active Directory 環境が使用できない場合に、回復性を提供します。 
  
- Azure に存在するディレクトリ統合コンポーネント。 
    
- Azure の AD FS プロキシを介してインターネットに AD FS が公開されます。 
    
- 任意の場所から接続するユーザーのためのクライアント認証トラフィックは、Azure で展開された AD FS サーバーおよびプロキシにより処理されます。 
    
### <a name="public-facing-internet-site-and-azure-ad-for-customer-authentication"></a>一般向けインターネット サイトおよび顧客認証用の Azure AD

インターネット サイトを Azure 上に配置することにより、必要に応じて簡単に拡大縮小できる機能を活用します。Azure AD を使用して顧客のアカウントを格納します。 
  
#### <a name="azure-advantages-for-internet-sites"></a>インターネット サイトにおける Azure の利点

- ファームの使用状況に基づいて仮想マシンの数を増減させることにより、必要なリソースに対してのみ料金を支払います。 
    
- 詳細なレポートおよび Web 分析を追加します。 
    
- インフラストラクチャの構築よりも優れたサイトの開発に注意を向けます。 
    
#### <a name="azure-ad"></a>Azure AD

Azure AD は、クラウド サービスに ID 管理機能とアクセス制御機能を提供します。機能には、クラウド ベースのディレクトリ データ ストアや ID サービスのコア セット (ユーザー ログオン プロセス、認証サービス、および AD FS を含む) があります。Azure AD に付属する ID サービスは、オンプレミス Active Directory の展開と簡単に統合でき、サード パーティの ID プロバイダーを十分にサポートしています。 
  
付属図は、インターネットに直接接続されたサイトにとって重要な領域と認証の構成を示しています。図は、Azure Active Directory テナントを示しています。これには、Azure の SharePoint ファームと次の 2 つのゾーンが含まれています: 
  
- インターネット ゾーン。ここでは、匿名の訪問者と認証済みの訪問者およびネットワーク外部の顧客とやり取りします。 
    
- 既定のゾーン。これには、クロール用の NTLM と、VPN トンネルを介してオンプレミス Active Directory 展開とやり取りする Windows 認証が含まれます。 
    
### <a name="on-premises-farm-plus-disaster-recovery-in-azure"></a>オンプレミス ファーム + Azure の障害復旧

ビジネス要件に合った障害復旧オプションを選択します。Azure は、障害回復をこれから始めようとする企業に対して基本レベルのオプションを提供するとともに、高い復元要件を持つ企業に対しては詳細なオプションを提供します。 
  
#### <a name="cold-standby"></a>コールド スタンバイ

- ファームは完全に構築されていますが、仮想マシンは停止状態です。(料金は仮想マシンの稼働時のみ発生します。) 
    
- 環境の保守には、仮想マシンを時折始動すること、環境への修正プログラムの適用、更新、検証が含まれます。 
    
- 障害発生時に、環境全体を開始します。 
    
#### <a name="warm-standby"></a>ウォーム スタンバイ

- これには、プロビジョニング済みで稼働中の小規模のファームが含まれます。 
    
- フェールオーバー時には、このファームがただちにユーザーに対応します。 
    
- 迅速にスケール アウトを実行して、ユーザー全体に対応します。 
    
#### <a name="hot-standby"></a>ホット スタンバイ

フルサイズのファームがプロビジョニングされ、スタンバイ状態で稼働しています。 
  
付属図は、Azure の SharePoint 災害復旧環境と相互作用するオンプレミスのファームを示しています。オンプレミス データベースは、VPN トンネルを介した SQL Server のログ配布を使用して、SharePoint 災害復旧環境にアクセスします。この環境には、SharePoint データベース、2 つの Web フロントエンド サーバー、および 2 つの SharePoint アプリケーション サーバーを含む 2 つの SQL データベース サーバーが含まれています。 
  

