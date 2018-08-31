---
title: SharePoint Online のパフォーマンス チューニングの概要
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/22/2018
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 81c4be5f-327e-435d-a568-526d68cffef0
description: この資料では、SharePoint Online での最適なパフォーマンスのページをデザインするときに考慮する必要がどのような特定の側面について説明します。
ms.openlocfilehash: 96aeec19a6b582d0dc8701cd2e99329ec8ce156b
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541521"
---
# <a name="introduction-to-performance-tuning-for-sharepoint-online"></a>SharePoint Online のパフォーマンス チューニングの概要

この資料では、SharePoint Online での最適なパフォーマンスのページをデザインするときに考慮する必要がどのような特定の側面について説明します。
  
## <a name="in-this-article"></a>この記事の内容

- [SharePoint Online の測定値](introduction-to-performance-tuning-for-sharepoint-online.md#spometrics)と[データのための結論に達すると](introduction-to-performance-tuning-for-sharepoint-online.md#data)
    
- [パフォーマンスをチェックするときに、標準ユーザー アカウントを使用します。](introduction-to-performance-tuning-for-sharepoint-online.md#standuser)
    
- [パフォーマンスをチューニングするための接続カテゴリ](introduction-to-performance-tuning-for-sharepoint-online.md#connect):[サーバー間の接続](introduction-to-performance-tuning-for-sharepoint-online.md#server)、[ネットワーク接続](introduction-to-performance-tuning-for-sharepoint-online.md#network)、および[ブラウザーの接続](introduction-to-performance-tuning-for-sharepoint-online.md#browser)
    
## <a name="sharepoint-online-metrics"></a>SharePoint Online のメトリックス
<a name="spometrics"> </a>

以下の SharePoint Online の広範なメトリックスには、パフォーマンスに関する実際のデータが記載されています。
  
- ページの読み取り速度
    
- ページごとに必要なラウンド トリップの数
    
- サービスの問題
    
- パフォーマンスの低下を引き起こすその他の事項
    
### <a name="conclusions-reached-because-of-the-data"></a>データからたどり着いた結論
<a name="data"> </a>

データは以下を示しています。
  
- ほとんどのページは SharePoint Online で良好に動作しています。
    
- カスタマイズされていないページは、非常に速く読み込まれています。
    
- OneDrive for Business、チーム サイト、_layouts などのシステムのページは、すべて速く読み込まれています。
    
- 1% の最も読み込み時間が長い SharePoint Online ページは、読み込みに 5,000 ミリ秒を超える時間がかかります。
    
使用できる 1 つの単純なベンチマーク テストは、自社のポータルの読み込み時間と OneDrive for Business のホーム ページの読み込み時間を比較してパフォーマンスを測定することです。OneDrive for Business のホーム ページではカスタマイズ機能がほとんど使用されないためです。これは、ネットワークのパフォーマンスの問題についてのトラブルシューティングを実行する際にサポート完了のためにお願いする最初の手順になることがよくあります。
  
## <a name="use-a-standard-user-account-when-checking-performance"></a>パフォーマンスをチェックするときに、標準ユーザー アカウントを使用します。
<a name="standuser"> </a>

サイト コレクションの管理者、サイト所有者、エディター、または共同作成者は、追加のセキュリティ グループに属しているし、追加のアクセス許可がある SharePoint は、ページに読み込まれるその他の要素があるため。
  
これは SharePoint 設置し、SharePoint Online に適用できるが、設置型のシナリオでの違いは簡単には気づかれない SharePoint Online のように。
  
ユーザーは、ページを実行する方法を正確に評価をするためにコントロールを作成し、セキュリティ グループに関連するその他のトラフィックが読み込まれないようにするのには、標準ユーザー アカウントを使用する必要があります。
  
## <a name="connection-categories-for-performance-tuning"></a>パフォーマンス チューニングの接続のカテゴリ
<a name="connect"> </a>

サーバーとユーザーの間の接続は、主な 3 つのコンポーネントに分類できます。読み込み時間の見通しについて SharePoint Online ページを設計する際は、これらのコンポーネントを考慮してください。
  
- **サーバーです**。マイクロソフトがデータ センターでホストするサーバーです。
    
- **ネットワークです**。Microsoft のネットワーク、インターネット、およびデータ センターとユーザーの間で、オンプレミスのネットワークです。
    
- **ブラウザー** 。ページが読み込まれます。
    
これら 3 つの接続内では、一般的に、読み込み時間が長いページのうち 95% は 5 つの理由によるものです。この記事では、それぞれの理由について説明します。
  
- ナビゲーションの問題
    
- コンテンツ ロールアップ
    
- 大きなファイル
    
- サーバーへの多数の要求
    
- Web パーツの処理
    
### <a name="server-connection"></a>サーバーの接続
<a name="server"> </a>

オンプレミスの SharePoint でのパフォーマンスに影響する問題の多くは、SharePoint Online にも該当します。
  
予想どおり、サーバーがオンプレミスの SharePoint で実行する内容にははるかに多くの制御があります。SharePoint Online では、作業は少し異なります。サーバーが実行する作業を多くすればするほど、ページの表示に時間がかかります。SharePoint では、この点において最大の原因は、複数の Web パーツを含む複雑なページです。
  
SharePoint Online
  
![オンラインのサーバーのスクリーンショット](media/a8e9b646-cdff-4131-976a-b5f891da44ac.png)
  
SharePoint
  
![オンプレミスのサーバーのスクリーンショット](media/46b27ded-d8a4-4287-b3e0-2603a764b8f8.png)
  
SharePoint Online では、特定のページの要求が、実際は複数のサーバーを呼び出すという結果になります。個別の要求に対し、結果的としてサーバー間で要求の表が生成されることがあります。この通信は、ページの読み込みの観点から費用がかかり、動作を遅くします。
  
サーバー間の通信の例は次のとおりです。
  
- Web サーバーと SQL サーバー
    
- Web サーバーとアプリケーション サーバー
    
サーバーの通信時間が長くなるもう 1 つの原因は、キャッシュ ミスです。オンプレミスの SharePoint とは異なり、以前アクセスしたページと同じサーバーに当たる機会は非常に少なくなり、オブジェクトのキャッシュが最新ではなくなります。
  
### <a name="network-connection"></a>ネットワーク接続
<a name="network"> </a>

設置がないため、wan を使用する、データ ・ センターとエンド ・ ユーザーとの間の高速接続を使用することがあります。一般に、点は、ネットワークの観点から管理が容易です。
  
SharePoint Online では、さらにいくつか考慮する要因があります。次に例を示します。
  
- Microsoft ネットワーク
    
- インターネット
    
- ISP
    
どのバージョンの SharePoint (およびどのネットワーク) を使用するかに関係なく、一般的にネットワークをビジー状態にするものには以下があります。
  
- 大きいペイロード
    
- 多数のファイル
    
- サーバーへの物理的な距離が長いこと
    
SharePoint Online で利用できる機能の 1 つは、マイクロソフトの CDN (コンテンツ配信ネットワーク) です。CDN は、基本的に複数のデータ センターに展開サーバーの分散型のコレクションです。、CDN ではクライアントが元の SharePoint サーバーからは遠く離れている場合でもにページ上のコンテンツ クライアントにサーバーでホストできます。マイクロソフトが使用しているより、将来的にページをカスタマイズできない、たとえば、SharePoint Online 管理ホーム ページのローカル インスタンスを格納します。Cdn の詳細については、[コンテンツ配信ネットワーク](https://support.office.com/article/Content-delivery-networks-0140f704-6614-49bb-aa6c-89b75dcd7f1f)を参照してください。
  
知っておく必要がありますがあまり多くはできないこととして、ISP の接続速度があります。単純な速度テスト ツールによって、接続速度が表示されます。
  
### <a name="browser-connection"></a>ブラウザーの接続
<a name="browser"> </a>

パフォーマンスの観点から、Web ブラウザーで考慮するいくつかの要因があります。
  
複雑なページを訪問するとパフォーマンスに影響します。ほとんどのブラウザーは、キャッシュを小さく (約 90 MB)、平均値の中にのみある web ページは、通常、約 1.6 MB です。これは、get 使用するのに時間はかかります。
  
帯域幅も問題となる場合があります。などの場合は、ユーザーは、別のセッションでビデオを鑑賞するが、この SharePoint ページのパフォーマンスに影響が。ストリーミング メディアからユーザーを防ぐことはできません、中には、ユーザーのページが読み込まれます方法を制御できます。
  
SharePoint Online のページの別のカスタマイズ方法については、以下の資料および他の最適なパフォーマンスを実現するためのベスト プラクティスを確認してください。
  
- [SharePoint Online のナビゲーション オプション](navigation-options-for-sharepoint-online.md)
    
- [SharePoint Online のページの診断ツールを使用してください。](page-diagnostics-for-spo.md)
    
- [SharePoint Online のイメージの最適化](image-optimization-for-sharepoint-online.md)
    
- [SharePoint Online での画像の読み込み遅延と JavaScript](delay-loading-images-and-javascript-in-sharepoint-online.md)
    
- [SharePoint Online での縮小とバンドル](minification-and-bundling-in-sharepoint-online.md)
    
- [コンテンツ配信ネットワークの使用](using-content-delivery-networks-with-sharepoint-online.md)
    
- [コンテンツ クエリ Web パーツではなくコンテンツ検索 Web パーツを使用して SharePoint Online でのパフォーマンスを向上させる](using-content-search-web-part-instead-of-content-query-web-part-to-improve-perfo.md)
    
- [容量計画および SharePoint Online のテスト負荷](capacity-planning-and-load-testing-sharepoint-online.md)
    
- [SharePoint Online のパフォーマンスの問題の診断](diagnosing-performance-issues-with-sharepoint-online.md)
    
- [SharePoint Online でのオブジェクト キャッシュの使用](using-the-object-cache-with-sharepoint-online.md)
    
- [SharePoint Online で調整またはブロックを回避する方法](https://msdn.microsoft.com/en-us/library/office/dn889829.aspx)
    

