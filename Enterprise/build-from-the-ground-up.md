---
title: "新規に構築"
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
ms.assetid: 84348d0c-d9d1-4a98-9b99-8433f9b70e45
description: "概要: は、クラウドの設定の詳細については独自のストレージ ・ サービスやソリューションの作成に使用できるストレージ構成要素を取得します。"
ms.openlocfilehash: be7ea3e7526115f1a983ec89f2afeb5d130daee1
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="build-from-the-ground-up"></a>新規に構築

 **の概要:**クラウドの設定の詳細については独自のストレージ ・ サービスやソリューションの作成に使用できるストレージ構成要素を取得します。
  
"新規に構築" ストレージ ソリューション:
  
- 独自のストレージ ・ ソリューションを最初から作成すること。 
    
- REST Api を使用してプログラミングする必要があります。
    
- 究極のカスタマイズと柔軟性を提供します。
    
次のセクションでは、"新規に構築" ストレージのそれぞれのオプションの詳細について説明します。
  
## <a name="azure-storage-files"></a>Azure Storage (ファイル)

### <a name="features"></a>機能

- レガシ アプリケーションからクラウドへの移行を促進
    
- 新しいアプリケーション向けに BLOB ストレージを推奨
    
- Azure 仮想マシンからマウントが可能
    
- SMB 3.0 でオンプレミスでのマウントが可能
    
- Linux および Windows で動作
    
- Azure AD ベースの認証または (Azure ストレージ アカウント キーは、認証およびファイル共有へのアクセスの認証を提供) の Acl をサポートしていません
    
### <a name="common-uses"></a>一般的な使用目的

- ファイル共有に依存しているレガシ アプリケーションのクラウドへの移行
    
- 開発およびテスト ツールの共有
    
- 分散アプリではログ、診断データ、クラッシュ ダンプの保存が可能
    
### <a name="key-storage-scenarios"></a>キー ストレージのシナリオ

- ファイルのバックアップ
    
### <a name="resources"></a>リソース

追加情報については、[こちら](https://msdn.microsoft.com/library/azure/dn166972.aspx)をクリックしてください。
  
コストの情報については、[こちら](http://azure.microsoft.com/pricing/details/storage/)をクリックしてください。
  
## <a name="azure-storage-blobs"></a>Azure Storage (BLOB)

### <a name="features"></a>機能

- 各ストレージ アカウントは、最大で 500 TB を保持できます (1 つのサブスクリプションは、複数のストレージ アカウントを持つことができます)
    
- ストレージ アカウントはストレージに構成され、そこでセキュリティを適用し、BLOB を含めることが可能
    
- ブロック BLOB は、200 GB までのクラウド オブジェクトのストリーミングと保管のために最適化済み
    
- ページ BLOB は、1 TB までの PaaS ディスクの表示とランダム書き込みのサポートのために最適化済み
    
- BLOB の追加は 195 GB までの追加操作のために最適化済み
    
- Premium Storage は SSD ストレージによる高速 IOPS を提供
    
### <a name="common-uses"></a>一般的な使用目的

- Web アプリケーションのファイル、コンピューター、データベース、およびデバイスのイメージとテキストのバックアップ
    
- クラウド アプリケーションの構成データ
    
- ログやその他の大規模なデータセットなどのビッグ データ
    
- Azure では、HDInsight や仮想マシン ディスクなど、独自のサービスに BLOG ストレージを使用
    
### <a name="key-storage-scenarios"></a>キー ストレージのシナリオ

- データ管理
    
### <a name="resources"></a>リソース

追加情報については、[こちら](https://msdn.microsoft.com/library/azure/dd179376.aspx)をクリックしてください。
  
コストの情報については、[こちら](http://azure.microsoft.com/pricing/details/storage/)をクリックしてください。
  
## <a name="azure-storage-queues"></a>Azure Storage (キュー)

### <a name="features"></a>機能

- ストレージ アカウントには任意の数のキューの登録が可能
    
- キューには任意の数のメッセージの登録が可能 (ストレージ アカウントの限界まで)
    
- キュー メッセージはアプリケーションによって取得または削除されない場合、7 日後に自動的に削除される
    
- メッセージ サイズは 64 KB まで
    
- ストレージ アカウント レベルのセキュリティ保護
    
- キューは生データではなく、コントロール メッセージを渡すために使用
    
### <a name="common-uses"></a>一般的な使用目的

- 非同期で処理する作業のバックログを作成
    
- ログ メッセージの処理
    
- アプリケーションの切り離し
    
### <a name="key-storage-scenarios"></a>キー ストレージのシナリオ

- イベント配信
    
### <a name="resources"></a>リソース

追加情報については、[こちら](https://msdn.microsoft.com/library/azure/dd179353.aspx)をクリックしてください。
  
コストの情報については、[こちら](http://azure.microsoft.com/pricing/details/storage/)をクリックしてください。
  
## <a name="azure-storage-tables"></a>Azure Storage (テーブル)

### <a name="features"></a>機能

- 半構造化データセットに最適
    
- 一般的に、従来の SQL より低コスト
    
- 値のクエリを実行する場合に低速のキー、クエリを実行する場合に非常に高速
    
- ストレージ アカウントの上限まで、テーブル数を大規模に拡張可能
    
- REST API、限定された oData プロトコル、.NET を介してアクセス可能
    
- 値はシリアル化する必要あり
    
### <a name="common-uses"></a>一般的な使用目的

- Web アプリケーションのユーザー データ
    
- アドレス帳
    
- デバイス情報
    
### <a name="key-storage-scenarios"></a>キー ストレージのシナリオ

- データ管理
    
### <a name="resources"></a>リソース

追加情報については、[こちら](https://msdn.microsoft.com/library/azure/dd179463.aspx)をクリックしてください。
  
コストの情報については、[こちら](http://azure.microsoft.com/pricing/details/storage/)をクリックしてください。
  
## <a name="microsoft-azure-storage-recommendations"></a>Microsoft Azure Storage の推奨事項

Azure Storage を使用してカスタム ストレージ ソリューションを設計するときは、以下の点に注意してください。
  
- 複数のストレージ アカウントを利用して、サイズ増加 (100 TB 以上) またはスループット向上 (1 秒あたり 5,000 以上の操作) に対応する拡張性を実現。
    
- コード変更ではなく、構成変更によるストレージ アカウントの追加を可能にする設計。
    
- テーブル ストレージのパーティショニング機能を慎重に選択し、挿入とクエリのパフォーマンスの面から必要な拡張を実現。
    
- メタデータ (プロパティ名) がインバンドに保存されるため、テーブル プロパティの短い形式の列名を選択 (列名も 1 MB の行サイズ制限に計上される)。
    
- 可能な場合は、バッチ操作もストレージに格納。
    
- 構成データベースのキャッシュ情報を積極的に分散キャッシュに格納。
    
- アプリケーションのパフォーマンスや信頼性が、キャッシュ内で利用できる特定のデータ セグメントに依存している場合、キャッシュにデータが入れられるまで、アプリケーションは着信要求を拒否する必要がある。
    
- データを垂直 (テーブル単位) または水平 (複数のシャードにおよぶセグメント テーブル) に分割し、負荷を複数のデータベースに分散。
    
## <a name="see-also"></a>関連項目

[エンタープライズ アーキテクトのための Microsoft クラウド ストレージ](microsoft-cloud-storage-for-enterprise-architects.md)
  
[Microsoft クラウド IT アーキテクチャのリソース](microsoft-cloud-it-architecture-resources.md)

[Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers](https://sway.com/FJ2xsyWtkJc2taRD)



