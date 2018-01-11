---
title: "Microsoft クラウドのストレージを設計する"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 7e511118-1b75-413a-b959-ad0d3ffc9516
description: "概要: クラウド ストレージが必要な理由を理解し、一連の Microsoft のクラウド ストレージ オプションおよび主要なストレージ シナリオを確認します。"
ms.openlocfilehash: 199e385ea0238e8fb27c04153faf177df07e1025
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/11/2018
---
# <a name="designing-storage-for-the-microsoft-cloud"></a>Microsoft クラウドのストレージを設計する

 **概要:** クラウド ストレージが必要な理由を理解し、一連の Microsoft のクラウド ストレージ オプションおよび主要なストレージ シナリオを確認します。
  
ご使用のストレージを Microsoft のクラウド サービスと統合すると、広範なサービスとクラウド プラットフォームのオプションにアクセスできるようになります。
  
## <a name="why-cloud-storage"></a>クラウド ストレージを選ぶ理由

クラウド ストレージを使用する 2 つの主な理由
  
1. 市場投入のスピード：
    
  - 高可用性および障害復旧のための迅速な構成
    
  - ストレージ ハードウェアの購入が不要
    
  - Microsoft のクラウド製品による組み込みの設備
    
  - 世界中どこからでも利用可能
    
2. メンテナンス コストの削減: 
    
  - ストレージの需要に応じた柔軟な拡大および縮小
    
  - ストレージ ハードウェアのメンテナンスや移行が不要
    
  - Microsoft はインフラストラクチャのメンテナンスや改善のための組み込みの設備を提供
    
  - 継続的な改善による市場で最高のストレージ セキュリティ
    
## <a name="microsoft-cloud-storage-options"></a>Microsoft クラウドのストレージ オプション

さまざまなクラウド ストレージ オプションを理解するために、建設にたとえて表現しています。
  
### <a name="move-in-ready"></a>いつでも使用可能

既存のサービスに付属している、事前にパッケージ化された以下のソリューションを使用します。最小限の構成ですぐに使用できます。
  
- Office 365
    
- Microsoft Intune
    
- OneDrive for Business
    
- Dynamics 365
    
- Visual Studio Team Services
    
- Azure Site Recovery
    
- Yammer Site Sharing
    
- Azure Backup
    
各クラウド ストレージ オプションの詳細については、[いつでも使用可能](move-in-ready.md) を参照してください。
  
### <a name="some-assembly-required"></a>いくらかのアセンブリが必要

既存のサービスを、カスタム調整用の追加の構成やコーディングを伴うストレージ ソリューションの開始点として使用します。
  
- Azure Content Delivery Network
    
- Azure Media Services
    
- HdInsight
    
- Azure Redis Cache
    
- Azure SQL データベース
    
- Azure VM 内の SQL Server
    
- Azure Cosmos DB
    
- StorSimple
    
- Azure SQL Data Warehouse
    
- Azure Data Lake Store
    
各クラウド ストレージ オプションの詳細については、[いくらかのアセンブリが必要](some-assembly-required.md) を参照してください。
  
### <a name="build-from-the-ground-up"></a>新規に構築

これらのストレージ文書パーツとコードを使用して、独自のストレージ ソリューションまたはアプリを最初から作成します。
  
- Azure Storage (ファイル)
    
- Azure Storage (BLOB)
    
- Azure Storage (キュー)
    
- Azure Storage (テーブル)
    
各クラウド ストレージ オプションの詳細については、[新規に構築](build-from-the-ground-up.md) を参照してください。
  
## <a name="key-storage-scenarios"></a>キー ストレージのシナリオ

クラウド ベースのストレージを必要とする主要シナリオは以下のとおりです。
  
- データのキャッシュ
    
    高速キャッシュで保存することによって、使用頻度の高いデータへのアクセスを促進します。
    
- チーム メンバーとの共同作業
    
    複数のユーザーにクラウド ストレージのデータへアクセス許可を付与します。
    
- データ管理
    
    内部または外部のバルク データを保存、移動、または削除します。
    
- ソース コードの管理
    
    クラウド内のアプリケーション コア ファイルをアップロード、共同作業、および実行します。
    
- ファイルのバックアップ
    
    複数のクラウドの場所で、内部データまたはオフサイトの外部データのコピーを保存します。
    
- 会社の通信の公開
    
    内部または外部メッセージの 1 つの公開ポイントを作成します。
    
- 数百万のイベントの配信
    
    Web サイト、アプリケーション、デバイスからのテレメトリ取り込みのためのストレージを作成します。
    
- ビデオの管理と提供
    
    顧客または組織ユーザー向けのビデオ コンテンツを保存し、提供します。
    
## <a name="next-step"></a>次の手順

[いつでも使用可能](move-in-ready.md) クラウド ストレージ オプションを確認します。
  
## <a name="see-also"></a>関連項目

[エンタープライズ アーキテクトのための Microsoft クラウド ストレージ](microsoft-cloud-storage-for-enterprise-architects.md)
  
[Microsoft クラウド IT アーキテクチャのリソース](microsoft-cloud-it-architecture-resources.md)

[Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers]((https://sway.com/FJ2xsyWtkJc2taRD))


