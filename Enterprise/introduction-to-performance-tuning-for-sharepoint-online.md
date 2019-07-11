---
title: SharePoint Online のパフォーマンス チューニングの概要
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/22/2018
audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 81c4be5f-327e-435d-a568-526d68cffef0
description: この記事では、SharePoint Online で最適なパフォーマンスを得るためにページを設計するときに考慮する必要がある具体的な事柄について説明します。
ms.openlocfilehash: d0dc4d6eac1a8711d1c93b97eccbf5474092d3af
ms.sourcegitcommit: 6b4c3a11ef7000480463d43a7a4bc2ced063efce
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "35616680"
---
# <a name="introduction-to-performance-tuning-for-sharepoint-online"></a>SharePoint Online のパフォーマンス チューニングの概要

この記事では、SharePoint Online で最適なパフォーマンスを得るためにページを設計するときに考慮する必要がある具体的な事柄について説明します。
     
## <a name="sharepoint-online-metrics"></a>SharePoint Online の指標

次の広範な SharePoint Online の指標は、パフォーマンスに関する現実世界のデータを提供します。
  
- 高速ページの読み込み方法
    
- ページごとに必要なラウンドトリップの数
    
- サービスに関する問題
    
- パフォーマンス低下の原因となるその他の要因
    
### <a name="conclusions-reached-because-of-the-data"></a>データのために到着した結論

データは次のように伝えます。
  
- ほとんどのページは SharePoint Online で適切に実行されます。
    
- カスタマイズされていないページは、非常に短時間で読み込まれます。
    
- OneDrive for Business、チームサイト、および _layouts などのシステムページはすべてすぐに読み込むことができます。
    
- SharePoint Online のページのうち、最低でも 1% の負荷は、5000ミリ秒を超えると読み込みが行われます。
    
1つの簡単なベンチマークテストを使用して、OneDrive for Business のホームページの読み込み時間と、カスタマイズされた一部の機能を使用することで、パフォーマンスを測定できます。 これは、多くの場合、ネットワークパフォーマンスの問題をトラブルシューティングするときに完了することを求める最初の手順のサポートになります。
  
## <a name="use-a-standard-user-account-when-checking-performance"></a>パフォーマンスをチェックするときに標準ユーザーアカウントを使用する

サイトコレクション管理者、サイト所有者、編集者、または投稿者は、追加のセキュリティグループに属し、追加のアクセス許可が与えられるため、SharePoint がページに読み込む追加要素を持つことになります。
  
これは、オンプレミスの sharepoint と SharePoint Online に適用されますが、オンプレミスのシナリオでは、相違点は SharePoint Online のように簡単にはわかりません。
  
ユーザーに対してページがどのように実行されるかを正しく評価するには、標準のユーザーアカウントを使用して、作成コントロールおよびセキュリティグループに関連する追加のトラフィックを読み込まないようにする必要があります。
  
## <a name="connection-categories-for-performance-tuning"></a>パフォーマンスチューニングの接続カテゴリ

サーバーとユーザーの間の接続を、3つの主要なコンポーネントに分類できます。 読み込み時間についての洞察を得るために SharePoint Online ページを設計する場合は、これらを考慮してください。
  
- **サーバー**Microsoft がデータセンターでホストするサーバー。
    
- **ネットワーク**データセンターとユーザーの間の Microsoft ネットワーク、インターネット、およびオンプレミスネットワーク。
    
- **ブラウザー**ページが読み込まれている場所。
    
これら3つの接続では、通常、5つの理由で、低速ページの 95% が発生します。 この記事では、これらの各理由について説明します。
  
- ナビゲーションの問題
    
- コンテンツロールアップ
    
- 大きなファイル
    
- サーバーへの多くの要求
    
- Web パーツの処理
    
### <a name="server-connection"></a>サーバー接続

SharePoint オンプレミスのパフォーマンスに影響する問題の多くは、SharePoint Online にも適用されます。
  
ご想像のとおり、サーバーがオンプレミスの SharePoint で実行する方法をより細かく制御できます。 SharePoint Online は少し異なります。 サーバーに対して実行する作業が多いほど、ページの表示に時間がかかります。 SharePoint では、この点で最も大きな原因は、複数の web パーツを持つ複雑なページです。
  
オンプレミスの SharePoint Server
  
![オンプレミスのサーバーのスクリーンショット](media/a8e9b646-cdff-4131-976a-b5f891da44ac.png)
  
SharePoint Online
  
![オンラインのサーバーのスクリーンショット](media/46b27ded-d8a4-4287-b3e0-2603a764b8f8.png)
  
SharePoint Online では、特定のページ要求が、実際には複数のサーバーを呼び出すことがあります。 個々の要求について、サーバー間の要求のマトリックスが表示されることがあります。 これらの相互作用は、ページの読み込みの観点から費用がかかり、処理が遅くなることがあります。
  
これらのサーバー間の相互作用の例を次に示します。
  
- Web サーバーと SQL Server
    
- Web からアプリケーションサーバーへ
    
他にも、サーバーとの通信を遅くすることができますが、キャッシュミスがあります。 オンプレミスの SharePoint とは異なり、以前に参照したページに対して同じサーバーがヒットする可能性が非常にスリムになります。これにより、オブジェクトキャッシュは廃止されます。
  
### <a name="network-connection"></a>ネットワーク接続

WAN を使用していないオンプレミスの SharePoint では、データセンターとエンドユーザーの間で高速接続を使用できます。 一般的に、ネットワークの観点からは管理が容易です。
  
SharePoint Online では、いくつかの要素を考慮する必要があります。例えば：
  
- Microsoft ネットワーク
    
- インターネット
    
- ISP
    
どのバージョンの SharePoint (およびどのネットワーク) を使用しているかに関係なく、通常、ネットワークのビジー状態になるのは次のような状況です。
  
- 大きなペイロード
    
- 多くのファイル
    
- サーバーへの物理的な距離が大きい
    
SharePoint Online で利用できる機能の1つに、Microsoft CDN (コンテンツ配信ネットワーク) があります。 CDN は基本的に、複数のデータセンターにまたがって展開されたサーバーの分散コレクションです。 CDN を使用すると、クライアントが元の SharePoint サーバーから離れている場合でも、ページ上のコンテンツをクライアントに近いサーバーでホストできます。 Microsoft では、カスタマイズできないページのローカルインスタンス (SharePoint Online 管理者のホームページなど) を格納するために、今後もこれを使用しています。 CDNs の詳細については、「[コンテンツ配信ネットワーク](https://docs.microsoft.com/en-us/office365/enterprise/content-delivery-networks)」を参照してください。
  
知っておく必要があるものの、多くのことを行うことができないものは、ISP の接続速度です。 簡単なスピードテストツールを使用すると、接続速度がわかります。
  
### <a name="browser-connection"></a>ブラウザー接続

パフォーマンスの観点から、web ブラウザーについて考慮するいくつかの要因があります。
  
複雑なページにアクセスすると、パフォーマンスに影響します。 ほとんどのブラウザーでは、25 mb (約 90 MB) のキャッシュしかありませんが、平均的な web ページは通常 1.6 MB です。 これを使用するには時間がかかります。
  
また、帯域幅が問題になることもあります。 たとえば、ユーザーが別のセッションのビデオを視聴している場合、SharePoint ページのパフォーマンスが低下します。 ユーザーがメディアをストリーミングするのを防ぐことはできませんが、ユーザーに対してページを読み込む方法を制御することができます。
  
最適なパフォーマンスを実現するのに役立つ、SharePoint Online ページのカスタマイズ方法やその他のベストプラクティスについては、次の記事を参照してください。
  
- 
  [SharePoint Online のナビゲーション オプション](navigation-options-for-sharepoint-online.md)
    
- [SharePoint Online のページ診断ツールを使用する](page-diagnostics-for-spo.md)
    
- [SharePoint Online のイメージの最適化](image-optimization-for-sharepoint-online.md)
    
- [SharePoint Online での画像の読み込み遅延と JavaScript](delay-loading-images-and-javascript-in-sharepoint-online.md)
    
- [SharePoint Online での縮小とバンドル](minification-and-bundling-in-sharepoint-online.md)
    
- [コンテンツ配信ネットワークの使用](using-content-delivery-networks-with-sharepoint-online.md)
    
- [SharePoint Online のパフォーマンスを向上させるために、コンテンツのクエリ Web パーツの代わりにコンテンツ検索 Web パーツを使用する](using-content-search-web-part-instead-of-content-query-web-part-to-improve-perfo.md)
    
- [SharePoint Online のキャパシティ プランニングとロード テスト](capacity-planning-and-load-testing-sharepoint-online.md)
    
- [SharePoint Online のパフォーマンスの問題の診断](diagnosing-performance-issues-with-sharepoint-online.md)
    
- [SharePoint Online でのオブジェクトキャッシュの使用](using-the-object-cache-with-sharepoint-online.md)
    
- [方法:SharePoint Online で調整またはブロックを回避する](https://msdn.microsoft.com/en-us/library/office/dn889829.aspx)
    

