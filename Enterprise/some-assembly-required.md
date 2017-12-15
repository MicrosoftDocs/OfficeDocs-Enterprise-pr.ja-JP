---
title: "いくらかのアセンブリが必要"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Top
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: ccf1b8b3-0d50-4c66-b314-f480245fad5e
description: "概要: 独自のストレージ ソリューションの作成に使用できる、クラウド ストレージ オプションのセットについての詳細を説明します。"
ms.openlocfilehash: bf6f7586b3a890cd25aba314e4892d5e2ac5bb34
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2017
---
# <a name="some-assembly-required"></a>いくらかのアセンブリが必要

 **概要:** 独自のストレージ ソリューションの作成に使用できる、クラウド ストレージ オプションのセットについての詳細を説明します。
  
「いくらかのアセンブリが必要な」ストレージ ソリューション:
  
- 開始点として、ストレージ ・ ソリューションの既存のサービスを使用します。
    
- いくつかの構成を必要とするか、コーディングします。
    
- お客様のニーズに合わせてカスタマイズできます。
    
次のセクションでは、各「いくつかのアセンブリが必要な」ストレージ ・ ソリューションの詳細について説明します。
  
## <a name="azure-content-delivery-network"></a>Azure Content Delivery Network

### <a name="features"></a>機能

- 高度なリアルタイムの分析
    
- DDoS に対する堅牢なセキュリティ
    
- 統合を設定した後で、Azure Web サイトまたは Azure クラウド サービスからコンテンツを自動的に取得
    
- Akamai との新たなパートナーシップ
    
- 突然のトラフィック スパイクや高負荷も処理が可能
    
### <a name="common-uses"></a>一般的な使用目的

- お客様に近いサーバーを利用して、音声、ビデオ、アプリケーション、画像、その他のファイルを高速かつ正確に配信
    
### <a name="key-storage-scenarios"></a>キー ストレージのシナリオ

- データ管理
    
- ビデオの管理
    
### <a name="resources"></a>リソース

追加情報については、[こちら](https://azure.microsoft.com/services/cdn/)をクリックしてください。
  
コストの情報については、[こちら](https://azure.microsoft.com/pricing/details/cdn/)をクリックしてください。
  
## <a name="hdinsight"></a>HdInsight

### <a name="features"></a>機能

- クラウド提供の Apache Hadoop ディストリビューション Data Lake サービス
    
- オンデマンドでペタバイトまで拡張
    
- 非構造化および半構造化データを処理 Java, .NET などによる開発
    
- ハードウェアの購入とメンテナンスが不要
    
- オンプレミスの Hadoop クラスターとクラウドを接続
    
- カスタム スクリプト (R、Giraph、Solr など) による任意の Hadoop プロジェクトの柔軟な展開
    
### <a name="common-uses"></a>一般的な使用目的

- データ分析のワークロード
    
- ビッグ データ (Spark) のメモリ内データ処理のフレームワーク
    
- リアルタイム ストリーム処理 (Storm)
    
- 非リレーショナル データ (HBase) の大規模なトランザクション処理 (OLTP)
    
### <a name="key-storage-scenarios"></a>キー ストレージのシナリオ

- データ管理
    
### <a name="resources"></a>リソース

追加情報については、[こちら](https://azure.microsoft.com/services/hdinsight/)をクリックしてください。
  
コストの情報については、[こちら](https://azure.microsoft.com/pricing/details/hdinsight/)をクリックしてください。
  
## <a name="azure-sql-database"></a>Azure SQL データベース

### <a name="features"></a>機能

- 管理とコスト削減のための最適化
    
- 自動的な可用性の向上、災害復旧、アップグレード
    
- サイズが 1 TB までの数百または数千のデータベースを管理する組織に推奨
    
- ストレージ増加に対して、シャーディング手法によるデータベース間でのデータ分割が可能
    
- Stretch Database および SQL Server 2016
    
### <a name="common-uses"></a>一般的な使用目的

- リレーショナル データを伴うクラウド設計の新しいアプリケーション
    
- 高度な構造化データ セットとリレーションシップの概略図によるデータ処理
    
- 空間データや豊富なデータ型
    
### <a name="key-storage-scenarios"></a>キー ストレージのシナリオ

- データ管理
    
### <a name="elastic-database"></a>Elastic Database

次の場合に、Azure SQL データベースの実質的に無制限のリソースを使用します。
  
- データ合計量が大きすぎ、単一データベースの制限内に収まらない場合。
    
- ワークロード全体のトランザクション スループットが単一のデータベースの容量を超えている場合。
    
- テナントが相互に物理的な分離を必要としており、各テナントに個別のデータベースが必要な場合。
    
- コンプライアンス、パフォーマンス、または地理的な理由により、データベースの複数のセクションを別の場所に置く必要がある場合。
    
垂直方向の拡大/縮小については、Azure データベース パフォーマンス レベル/エディションを変更するか、Elastic Database プールを利用できます。
  
![Azure SQL Database が提供する垂直方向のスケーリング。](images/Storage_Poster/CloudStor-VertScale.png)
  
水平方向の拡大/縮小については、必要に応じて、新しいデータベースを追加することができます。
  
![Azure SQL Database が提供する水平方向のスケーリング。](images/Storage_Poster/CloudStor-HorizScale.png)
  
詳細情報については、[こちら](https://docs.microsoft.com/azure/sql-database/sql-database-elastic-scale-introduction) をクリックしてください。
  
### <a name="stretch-database-with-sql-server-2016"></a>Stretch Database および SQL Server 2016

Stretch Database は SQL Server 2016 の機能であり、顧客の発注情報を含む大きなテーブル内の処理済みビジネス データなど、コールド データを Azure の SQL Stretch Database に透過的かつ安全に移動できます。 ストレッチ時には、SQL Server インスタンス、データベース、または単一のテーブルのコンテンツは、SQL Server 2016 サーバーのローカル データと Azure のリモート データとを組み合わせたものです。ストレッチの対象となるデータは、SQL Server 2016 によって Azure に自動的に移動されます。
  
![Stretch Database および SQL Server 2016。](images/Storage_Poster/CloudStor-Stretch.png)
  
履歴データを含むユーザー クエリは、Azure SQL Stretch Database に透過的に転送されます。テーブルがストレッチされても、クエリを書き換える必要はありません。
  
Stretch Database は、長期ストレージ、および履歴データへの透過的アクセスのためのコスト パフォーマンスに優れたオプションを提供します。テーブルが非常に大きくなると発生するパフォーマンスと可用性の問題も解決します。
  
詳細情報については、[こちら](https://msdn.microsoft.com/library/dn935011.aspx) をクリックしてください。
  
### <a name="resources"></a>リソース

追加情報については、[こちら](http://azure.microsoft.com/services/sql-database/)をクリックしてください。
  
コストの情報については、[こちら](http://azure.microsoft.com/pricing/details/sql-database/)をクリックしてください。
  
## <a name="azure-cosmos-db"></a>Azure Cosmos DB

### <a name="features"></a>機能

- 低待機時間を保証し、99.99% の可用性を持つ SLA。無制限の柔軟なスケールを持つストレージとスループット
    
- 透過的なフェイルオーバーと明確に定義された 4 つの整合性レベルにより、任意の数のリージョン間ですべてのデータをグローバルにレプリケート
    
- スキーマやセカンダリ インデックスを必要とせずに、すべてのデータのインデックスを自動的に作成
    
- 豊富な SQL と JavaScript クエリ、および複数項目のトランザクション
    
### <a name="common-uses"></a>一般的な使用目的

- IoT、モバイル、およびソーシャル
    
- ゲーム
    
- 小売
    
- コンテンツ管理
    
### <a name="key-storage-scenarios"></a>キー ストレージのシナリオ

- データ管理
    
### <a name="cosmos-db-vs-azure-tables-vs-azure-sql-database"></a>Cosmos DB、Azure Tables、Azure SQL データベースの比較

Cosmos DB、Azure Table ストレージ、および Azure SQL データベースの共通属性
  
- 99.99% の可用性の SLA
    
- 完全に管理されたデータベース サービス
    
- ISO 27001、HIPAA、および EU モデル条項に準拠
    
次の図は、Azure Cosmos DB、Azure Table ストレージ、Azure SQL データベースの共通でない属性を示しています。
  
![Cosmos DB、Azure Tables、Azure SQL Database に共通でない属性](images/Storage_Poster/CloudStor-Table.png)
  
### <a name="resources"></a>リソース

追加情報については、[こちら](http://azure.microsoft.com/services/documentdb/)をクリックしてください。
  
コストの情報については、[こちら](http://azure.microsoft.com/pricing/details/documentdb/)をクリックしてください。
  
## <a name="azure-media-services"></a>Azure Media Services

### <a name="features"></a>機能

- 拡大縮小が可能なライブおよびオン デマンド ビデオ (VOD) の配信
    
- 可用性の高いエンコーディングおよびストリーミング
    
- Flash、iOS、Android、HTML5、Xbox をサポート
    
- Studio 認定 DRM をサポート
    
- 豊富なコンテンツによる収益化
    
- 事前に統合されたパートナーによる広範なエコシステム
    
### <a name="common-uses"></a>一般的な使用目的

- 拡大縮小が可能な音声とビデオのエンコード、格納、およびストリーム
    
- リアルタイム ストリーミングおよび VOD
    
- 効率的なビデオ コンテンツ管理
    
### <a name="key-storage-scenarios"></a>主要なストレージ シナリオ

- ビデオの管理
    
### <a name="resources"></a>リソース

追加情報については、[こちら](https://azure.microsoft.com/services/media-services/)をクリックしてください。
  
コストの情報については、[こちら](http://azure.microsoft.com/pricing/details/media-services/)をクリックしてください。
  
## <a name="azure-redis-cache"></a>Azure Redis Cache

### <a name="features"></a>機能

- 可用性の高い安全な専用 Redis サーバー。Microsoft 管理によるデータ レプリケーションとフェイルオーバーが可能
    
- 高いスループットが必要なアプリに推奨
    
- 530 GB を超えるサイズで利用可能 (Premium および自動シャーディングを使用)
    
- Redis 永続化による Azure Storage へのメモリ内キャッシュ データの保持
    
- Redis クラスタリングによる最大スケールおよびスループットの実現
    
- Azure Virtual Network サポートによるセキュリティとネットワークの分離の強化
    
### <a name="common-uses"></a>一般的な使用目的

- Cosmos DB や Azure SQL データベースによる Azure でのストレージ サービス内データの逆引き参照
    
- その他のデータ ストアから同期されたコンテンツ
    
### <a name="key-storage-scenarios"></a>主要なストレージ シナリオ

- データのキャッシュ
    
- 高スループット アプリケーションのメッセージ ブローカー
    
### <a name="resources"></a>リソース

追加情報については、[こちら](http://azure.microsoft.com/services/cache/)をクリックしてください。
  
コストの情報については、[こちら](http://azure.microsoft.com/pricing/details/cache/)をクリックしてください。
  
## <a name="sql-server-on-an-azure-vm"></a>Azure VM 内の SQL Server

### <a name="features"></a>機能

- Azure 仮想マシンでインストールされたアプリケーションとして稼働する SQL Server
    
- インストールされた SQL Server でのギャラリー イメージの使用、または所有している SQL Server ライセンスの適用
    
### <a name="common-uses"></a>一般的な使用目的

- アプリケーションのデータ管理
    
### <a name="key-storage-scenarios"></a>キー ストレージのシナリオ

- データ管理
    
### <a name="resources"></a>リソース

追加情報については、[こちら](http://azure.microsoft.com/services/virtual-machines/)をクリックしてください。
  
コストの情報については、[こちら](http://azure.microsoft.com/pricing/details/virtual-machines/)をクリックしてください。
  
## <a name="storsimple"></a>StorSimple

### <a name="features"></a>機能

- 拡張性の高いエンタープライズ ハイブリッド SAN ストレージ。オンプレミスのハイブリッド ストレージ配列での SSD および HDD と、ソリューションの統合拡張としてのクラウド ストレージを使用。
    
- 非構造化および半構造化されたデータのインライン重複除外、圧縮、自動階層化、暗号化
    
- クラウドのスナップショットを使用したオフサイト データの自動的な保護
    
- 効率性に優れ、場所を問わない障害回復
    
- Azure の StorSimple Virtual Appliance による企業データのデータ モビリティ
    
### <a name="common-uses"></a>一般的な使用目的

- ファイル共有、アーカイブ、その他のデータ リポジトリに関連するデータ量の増加を管理
    
- ファイル共有、仮想マシン、SQL、および SharePoint のための (リモート BLOB ストレージを使用した) オフサイトのデータ保護と障害復旧
    
- クラウド スナップショットを利用した Azure 内のデータの複製、およびビジネスの機敏性向上
    
### <a name="key-storage-scenarios"></a>キー ストレージのシナリオ

- データ管理
    
- 共同作業
    
### <a name="resources"></a>リソース

追加情報については、[こちら](http://azure.microsoft.com/services/storsimple/)をクリックしてください。
  
コストの情報については、[こちら](http://azure.microsoft.com/pricing/details/storsimple/)をクリックしてください。
  
## <a name="azure-sql-data-warehouse"></a>Azure SQL Data Warehouse

### <a name="features"></a>機能

- ペタバイト規模まで拡張可能な柔軟なデータ ウェアハウス 最大 32 のクエリを同時実行
    
- 高速な分析による、大量の構造化データの管理 数秒で動的に拡張/縮小を計算
    
- 透過的なデータ暗号化をサポート
    
- 7 日間の 8 時間ごとのバックアップ
    
### <a name="common-uses"></a>一般的な使用目的

- 売上報告書
    
- 利用状況レポート
    
- 大量のデータ
    
### <a name="key-storage-scenarios"></a>キー ストレージのシナリオ

- データ管理
    
### <a name="resources"></a>リソース

追加情報については、[こちら](https://azure.microsoft.com/services/sql-data-warehouse/)をクリックしてください。
  
コストの情報については、[こちら](https://azure.microsoft.com/pricing/details/sql-data-warehouse/)をクリックしてください。
  
## <a name="azure-data-lake-store"></a>Azure Data Lake Store

### <a name="features"></a>機能

- ビッグ データ分析のワークロード向けの超大規模リポジトリ
    
- クラウド用の Hadoop 分散ファイル システム
    
- ファイル サイズに固定の制限なし
    
- アカウント サイズに固定の制限なし
    
- ネイティブ形式での非構造化データおよび構造化データ
    
- 分析パフォーマンスを向上させる高スループット
    
- 高い耐久性、可用性、信頼性 (99.9% のエンタープライズ レベル SLA と年中無休 24 時間のサポート)
    
- Azure Active Directory アクセス制御
    
### <a name="common-uses"></a>一般的な使用目的

- あらゆる種類のデータを 1 か所で収集するエンタープライズ規模のリポジトリ
    
### <a name="key-storage-scenarios"></a>キー ストレージのシナリオ

- データ管理
    
### <a name="resources"></a>リソース

追加情報については、[こちら](https://azure.microsoft.com/services/data-lake-store/)をクリックしてください。
  
コストの情報については、[こちら](https://azure.microsoft.com/pricing/details/data-lake-store/)をクリックしてください。
  
## <a name="next-step"></a>次の手順

[新規に構築](build-from-the-ground-up.md) クラウド ストレージ オプションを確認します。
  
## <a name="see-also"></a>See Also

[エンタープライズ アーキテクトのための Microsoft クラウド ストレージ](microsoft-cloud-storage-for-enterprise-architects.md)
  
[Microsoft クラウド IT アーキテクチャのリソース](microsoft-cloud-it-architecture-resources.md)

[Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers](https://sway.com/FJ2xsyWtkJc2taRD)



