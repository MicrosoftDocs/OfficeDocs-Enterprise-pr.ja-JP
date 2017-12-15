---
title: "アクセス可能な図 - オンプレミスの電子情報開示のフロー"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: b9dcd692-0485-4eec-870d-87ab6b89d97b
description: "この記事は、「オンプレミスの電子情報開示のフロー」という名前の図のアクセス可能なテキスト バージョンです。"
ms.openlocfilehash: de94fc2af94df47a83f4a7847a84cd18131f637e
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2017
---
# <a name="accessible-diagram---on-premises-ediscovery-flow"></a>アクセス可能な図 - オンプレミスの電子情報開示のフロー

**の概要:**この資料は、図の設置型電子的証拠開示の流れをという名前のアクセス可能なテキスト バージョンです。
  
このポスターは、サーバー製品間のデータのアーキテクチャとフローについて詳しく説明しています。 
  
## <a name="across-sharepoint-exchange-lync-and-file-shares"></a>SharePoint、Exchange、Lync、およびファイル共有にわたる流れ

図は、2 つのサーバー ファーム (SharePoint 2013 エンタープライズ アプリ ファーム、および SharePoint 2013 サービス ファーム) にアクセスするクエリを送信するユーザーを示しています。SharePoint 2013 サービス ファームは、SharePoint 2013 コンテンツ ファーム、Exchange Server 2013 (Lync 2013 と通信する)、および Windows ファイル共有と通信します。 
  
電子情報開示フロー リストには、データ フローおよび SharePoint、Exchange、Lync、およびファイル共有の間で電子情報開示クエリのアクションが発生する順序が記載されています。 
  
電子情報開示フロー リストは、最初に詳しい説明、続いて機能の詳細説明が図に表されて記載されています。 
  
### <a name="ediscovery-flow-list"></a>電子情報開示フロー リスト

このリストに記載されている各手順の番号は、図に表された手順と関係しています。図については、このドキュメントの後半で詳しく説明します。 
  
1. 電子情報開示のケースは、電子情報開示センター (EDC) で作成、管理、および使用されます。EDC は SharePoint 2013 のサイト コレクションです。 ここで、ケースの定義、追跡するソースの識別、クエリの発行、クエリ結果の確認、コンテンツ保留の設定/解除を実行します。 
    
2. 電子情報開示のクエリまたはアクション (保留、保留の解除、GetStatus など) は、EDC からエンタープライズ アプリ ファーム内の Search Service アプリケーション (SSA) プロキシへ中継されます。 次に、SSA プロキシは Services アプリ ファーム内の SSA へトラフィックを中継します。 この例における要求は、SharePoint コンテンツ ファーム内でファイル名に "CONTOSO" を含むものすべてを保留にすることです。 
    
3. 要求がケースのクエリを実行することである場合、SSA は検索インデックスを参照します。続いて、電子情報開示のクエリの結果セットが、EDC を介してユーザーに返されます。 
    
4. 要求が保留や保留の解除などのアクションである場合、そのアクションは SSA 管理データベース内の Actions_Table に書き込まれます。 この例では、SharePoint コンテンツ ファーム内で "CONTOSO" を含むものすべてに対する保留要求が Actions_Table に書き込まれます。 
    
5. コンテンツ ファームの eDiscovery インプレース保持タイマー ジョブは定期的に起動し、保留中のアクションに対して要求を生成します。さらに、SSA プロキシを通して SSA へステータス更新を送信します。 
    
6. 保留中のアクションに対するクエリは中央の SSA へ中継され、そこでコンテンツ ファームの保留中のアクションについて Action_Table を参照します。 さらに、コンテンツ ファームのインプレース保持タイマー ジョブは、受信したオブジェクトおよびアクションのステータス更新を送信し、それらは ActionsTable に書き込まれます。 
    
7. SharePoint 2013 コンテンツ ファーム内の、名前に "CONTOSO" を含むすべてのコンテンツに対する保留要求は、SSA によりコンテンツ ファーム内の電子情報開示のインプレース保持タイマー ジョブへ送信されます。 
    
8. 電子情報開示のインプレース保持タイマー ジョブは、"CONTOSO サイト" と "CONTOSO コンテンツ" を保留にします。 
    
9. 電子情報開示のインプレース保持タイマー ジョブは、エンタープライズ アプリケーション ファーム内で定期的に実行され、検出アクションのステータスの確認およびステータスの更新を行います。 
    
10. ステータス クエリは、エンタープライズ アプリケーション ファームの SSA プロキシを介して SharePoint Services ファームの SSA へ中継されます。 
    
11. SSA は、アクション テーブルからステータスを取得し、エンタープライズ アプリケーション ファーム内のタイマー ジョブへ返します。それから、ステータス更新が EDC へ送信されます。 
    
12. 電子情報開示ユーザーがメールボックスやアーカイブ済みの Lync コンテンツなどの Exchange ソースを検索 (またはアクションを実行) している場合、中央の SSA は Exchange Web Services (EWS) プロキシを使用して Exchange Web Services を照会します。 Exchange には独自の検索および電子情報開示インフラストラクチャがあり、すべての電子情報開示の呼び出しを内部で管理しています。 
    
13. Exchange Web サービスは、電子情報開示の検索結果により SSA に応答します。または、クエリベースの保留に対するステータス要求に応答して EDC へ中継します。 
    
#### <a name="prerequisites"></a>前提条件

- SharePoint エンタープライズ検索を設定する必要があり、コンテンツ ソース (SharePoint および Windows ファイル共有) の検索クロールが正常に実行され、すべてのコンテンツ ソースがインデックスにある。 
    
- SharePoint Services ファームと Exchange 間、および Exchange と Lync 間でサーバー間の信頼と認証を設定する必要がある。 
    
### <a name="description-of-components-in-the-diagram"></a>図中の構成要素の説明

図は、2 つのサーバー ファーム (SharePoint 2013 エンタープライズ アプリ ファーム、および SharePoint 2013 サービス ファーム) にアクセスするクエリを送信するユーザーを示しています。SharePoint Services ファームは、SharePoint 2013 コンテンツ ファーム、Exchange Server 2013 (Lync 2013 とインターフェイスする)、および Windows ファイル共有とインターフェイスします。 
  
#### <a name="sharepoint-2013-enterprise-app-farm"></a>SharePoint 2013 エンタープライズ アプリケーション ファーム

SharePoint 2013 エンタープライズ アプリケーション ファームには、次のコンポーネントが含まれています。 
  
- EDC
    
- SSA プロキシ 
    
- タイマー ジョブ 
    
ユーザーが送信するクエリまたはアクションは、エンタープライズ アプリケーション ファームの EDC に送信されます。次のアクションが実行されます。 
  
- クエリまたはアクションは、SSA プロキシに移動します。 
    
- SSA プロキシは、エンタープライズ アプリケーション ファームのタイマー ジョブにステータス クエリまたは応答を送信するとともに、SharePoint Services ファームの SSA サービスにもステータス クエリまたは応答を送信します。この結果として起こるアクションについては、SharePoint Services ファームに関するセクションで説明します。 
    
- タイマー ジョブは、応答を受信すると、SSA のプロキシと EDC に応答を送信します。 
    
- クエリまたはアクションの結果はすべて、EDC のユーザーに送信されます。 
    
#### <a name="sharepoint-2013-services-farm"></a>SharePoint 2013 Services ファーム

SharePoint 2013 Services ファームには、次のコンポーネントが含まれています。 
  
- SSA サービス 
    
- 検索インデックス データベース 
    
- SSA admin_db データベース。このデータベースのアクション テーブルには次が含まれます。 保留、保留の解除、GetStatus 
    
- EWS プロキシ 
    
SharePoint エンタープライズ アプリケーション ファームの SSA プロキシが SharePoint Services ファーム内の SSA にステータス クエリを送信すると、次のアクションが発生します。 
  
- 要求がクエリの場合、SSA は検索インデックスを参照します。検出の応答は SSA に返されてから、EDC を経由してユーザーに返されます。 
    
- 要求が書き込み操作の場合、SSA サービスは SSAadmin_db に書き込み操作を送信します。 
    
- クロールおよび結果応答要求は、SSA から SharePoint 2013 コンテンツ ファームに送信され、応答は SSA に返されます。 
    
- クロールおよび結果応答要求は、SSA から Windows ファイル共有に送信され、応答は SSA に返されます。 
    
- 保留中のアクションのクエリ、応答、またはステータスの更新は、SSA から SharePoint コンテンツ ファーム内の SSA に送信され、応答は SSA に返されます。 
    
- Exchange のアクションまたはステータス要求は、SSA から EWS プロキシに送信されます。EWS プロキシは、Exchange のクエリ操作またはステータス要求を、Exchange 2013 サーバーの Exchange Web Service に送信します。 
    
- ステータスのクエリまたは応答は、SSA から SSA admin_db に送信され、SSA に返されます。 
    
- 保留中のアクションのクエリまたは応答は、SSA から SSA admin_db に送信され、SSA に返されます。 
    
#### <a name="sharepoint-2013-content-farm"></a>SharePoint 2013 コンテンツ ファーム

SharePoint 2013 コンテンツ ファームには、次のコンポーネントが含まれています。 
  
- SSA プロキシ 
    
- タイマー ジョブ 
    
- Contoso SharePoint サイト 
    
- Contoso SharePoint のコンテンツ 
    
SharePoint Services ファームの SSA が SharePoint コンテンツ ファーム内の SSA プロキシにステータス クエリを送信すると、次のアクションが発生します。 
  
- SharePoint コンテンツ ファームの SSA プロキシは、保留中のアクションに対するクエリまたはステータス応答をタイマー ジョブに送信します。 
    
- タイマー ジョブは、Contoso の SharePoint コンテンツを確認する Contoso 社の SharePoint サイトに要求を送信します。 
    
- 保留中のアクションまたはステータスのクエリに対する応答は、タイマー ジョブから、SharePoint コンテンツ ファームの SSA のプロキシに送信されてから、SharePoint Services ファームの SSA サービスに送信されます。 
    
#### <a name="exchange-2013"></a>Exchange 2013

Exchange 2013 サーバー コンポーネントには、Exchange Web サービスが含まれ、以下を実行します。 
  
- サーバー間の信頼または Oauth が、SharePoint 2013 2013 コンテンツ ファームと Exchange 2013 の間で処理されます。 
    
- サーバー間の信頼または Oauth が、Exchange 2013 と Lync 2013 の間で処理されます。 
    
#### <a name="lync-2013"></a>Lync 2013

Lync 2013 コンポーネントは、Exchange 2013 に Lync のコンテンツをアーカイブします。 
  
#### <a name="windows-file-shares"></a>Windows ファイル共有

Windows ファイル共有コンポーネントは、SharePoint Services ファーム内の SSA にクロールの結果を提供します。 
  
### <a name="legend"></a>凡例

この図の凡例では、次のように異なる色を付けて、コンポーネント間に表された各種のトラフィックをグラフィカルに示しています。 
  
- 水色の線: クエリ/アクション - 電子情報開示のクエリまたはアクションのデータ 
    
- オレンジ色の線: 電子情報開示の応答 - 電子情報開示のクエリの応答データ 
    
- 緑色の線:ステータス クエリ/応答 - 電子情報開示のステータス クエリまたは応答のデータ 
    
- 紫色の線:Exchange のアクション/ステータス要求 - Exchange トラフィックのアクション状態の電子情報開示要求 
    
- 赤色の線:Exchange データ/ステータス応答 - Exchange からの電子情報開示クエリまたはステータス応答 
    
- 黒い点線:サーバー間の信頼/OAuth 
    
- 黒い実線:クロール/結果 
    

