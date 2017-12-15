---
title: "トランザクション履歴データのクラウドへの移動"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: 3e9c405a-415b-4584-aa7e-f2489299c457
description: "概要: Contoso 社が SQL Server Stretch Database を実装することで、オンプレミスのデータ ストレージの必要性と毎日の運営コストを縮小した方法を示します。"
ms.openlocfilehash: f1a44a14da49c394974755f7c557013717c4ccef
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2017
---
# <a name="moving-historical-transaction-data-to-the-cloud"></a>トランザクション履歴データのクラウドへの移動

 **概要:** Contoso 社が SQL Server Stretch Database を実装することで、オンプレミスのデータ ストレージの必要性と毎日の運営コストを縮小した方法を示します。
  
Contoso 社のエンタープライズ ストレージ システムには大量のトランザクション履歴データが保存されています。その内容は、規制要件への準拠に関するデータや、支出の傾向のマーケティング調査と BI 分析に関するデータです。Contoso 社では、磁気テープからアーカイブ済みのデータを復元する必要もありますが、これは時間のかかるプロセスです。Contoso 社のエンタープライズ ストレージ システム内のハードウェアの寿命が近づいており、交換すると非常に高価になります。 
  
オンプレミスのデータセンターを縮小するという業務上の必要の一部として、Contoso 社は SQL Server 2016 へのアップグレードを選択しました。その理由は、Stretch Database のハイブリッド機能を使用でき、Azure とシームレスに統合できるからです。Contoso 社で Stretch Database を使用すると、テーブル内のコールド データをオンプレミスからクラウド ストレージに移動して、ローカル ディスク領域を解放したりメンテナンスを縮小したりできます。ホット データとコールド データが両方とも同じテーブル内にあり、アプリケーションとそのユーザーが常に利用可能で、バックアップや復元などのメンテナンスにも常に利用できます。図 1 は、Stretch Database を示しています。
  
**図 1:SQL Server Stretch Database**

![ハイブリッド データ ソリューションとしての SQL Server Stretch Database](images/Contoso_Poster/StretchDB01.png)
  
図 1 は、SQL クライアントから SQL Server 2016 を実行しているサーバーに T-SQL クエリを送信し、さらに Azure PaaS 内の Azure SQL Stretch Database に転送する方法を示しています。
  
詳細については、「[Stretch Database](https://msdn.microsoft.com/library/dn935011.aspx)」を参照してください。
  
Contoso 社では、次の手順を使用して、履歴データをクラウドに移動しました。
  
1. データベースの分析
    
    クラウドに移動しようとしているデータベース内のテーブルの分析を実行し、問題を修正しました。新しい Stretch Database Advisor により、SQL Server 2016 のすべての機能で行えることに関する全概要が示されます。たとえば、クラウドを伸縮するコールド データがどのテーブルにあるかを示す機能があります。
    
2. アップグレード
    
    パリ本社のデータセンター内の既存の SQL サーバーを SQL Server 2016 に更新しました。
    
3. コールド データのクラウドへの移行
    
    SQL Management Studio を使用して、伸縮対象のデータベースと、Azure 内の Stretch Database のインスタンスに移行するテーブルを識別しました。やがてバックグラウンドで、SQL Server 2016 は履歴データを Azure 内の Stretch Database に移動しました。
    
その結果、パリ本社の SQL Server 2016 を実行している 1 つのサーバーは次のように構成されました。
  
**図 2:Contoso 社のデータセンター内のサーバーに対する Stretch Database の使用状況**

![SQL Server を実行している 1 台のコンピューター向け Contoso 社の構成 SQL Server Stretch Database](images/Contoso_Poster/StretchDB02.png)

  
図 2 は、Contoso 社のデータセンター内のアプリケーション サーバーに対するユーザー クエリが、Azure PaaS 内の Azure SQL Stretch Database に渡される SQL クエリになる様子を示しています。
  
ユーザーは既存のアプリとクエリでデータにアクセスします。アクセス ポリシーは変わりません。作業を進める際に、テープのバックアップを取る必要はありません。メンテナンスは、ホット データのバックアップと復元から成ります。
  
Stretch Database の実装後、Contoso 社は次のような状況になりました。
  
- オンプレミスのデータ ストレージの必要性が 85% 縮小しました。
    
- エンタープライズ ストレージ システムが更新され、磁気テープのアーカイブに依存する必要性がなくなりました。
    
- 毎日の運営コストが大幅に縮小されました。
    
## <a name="see-also"></a>See Also

[Contoso Corporation のエンタープライズのシナリオ](enterprise-scenarios-for-the-contoso-corporation.md)
  
[Microsoft Cloud の Contoso](contoso-in-the-microsoft-cloud.md)
  
[Microsoft クラウド IT アーキテクチャのリソース](microsoft-cloud-it-architecture-resources.md)

[Stretch Database](https://msdn.microsoft.com/library/dn935011.aspx)
  
[Microsoft の Enterprise Cloud ロードマップ:IT の意思決定者向けのリソース](https://sway.com/FJ2xsyWtkJc2taRD)




