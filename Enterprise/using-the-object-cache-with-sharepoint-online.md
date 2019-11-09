---
title: SharePoint Online でのオブジェクトキャッシュの使用
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 4/20/2015
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 38bc9c14-3826-449c-beb6-b1003bcbeaaf
description: この記事では、SharePoint Server 2013 オンプレミスと SharePoint Online でのオブジェクトキャッシュの使用との違いについて説明します。
ms.openlocfilehash: 4c6cd225bf0f7324dcb23c55adb87e2365d35472
ms.sourcegitcommit: 89ecf793443963b4c87cf1033bf0284cbfb83d9a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2019
ms.locfileid: "38078026"
---
# <a name="using-the-object-cache-with-sharepoint-online"></a>SharePoint Online でのオブジェクトキャッシュの使用

この記事では、SharePoint Server 2013 オンプレミスと SharePoint Online でのオブジェクトキャッシュの使用との違いについて説明します。
  
SharePoint Online 展開のオブジェクトキャッシュに依存することによって、重大な悪影響があります。 SharePoint Online のオブジェクトキャッシュに依存している場合は、ページの信頼性が低下します。 
  
## <a name="how-the-sharepoint-online-and-sharepoint-server-2013-object-cache-works"></a>SharePoint Online と SharePoint Server 2013 のオブジェクトキャッシュのしくみ

SharePoint Server 2013 がオンプレミスでホストされている場合、お客様は、オブジェクトキャッシュをホストする独自のフロントエンド web サーバーを備えています。 これは、キャッシュが1つの顧客専用となり、使用可能なメモリ容量によって制限されるだけで、オブジェクトキャッシュに割り当てることができることを意味します。 オンプレミスのシナリオでは1人の顧客のみが提供されるので、通常、フロントエンド web サーバーでは、同じサイトに対してユーザーが繰り返し要求を行うことになります。 これは、キャッシュが短時間でいっぱいになり、ユーザーが定期的に要求しているリストクエリの結果と SharePoint オブジェクトを完全に保持することを意味します。
  
![オンプレミスのフロントエンド Web サーバーへのトラフィックと負荷を示しています](media/a0d38b36-4909-4abb-8d4e-4930814bb3de.png)
  
その結果、ユーザーがページを訪問すると、ページの読み込み時間が短縮されます。 同じページの少なくとも4つの負荷の後、ページはすべてのフロントエンド web サーバーにキャッシュされます。
  
一方、SharePoint Online では、多くのサーバーがありますが、さらに多くのサイトもあります。 各ユーザーは、キャッシュが設定されていない別のフロントエンド web サーバーに接続することができます。 また、キャッシュがサーバーに対して設定されている場合もありますが、そのフロントエンド web サーバーの次のユーザーは別のサイトからページを要求します。 または、次のユーザーが前の訪問と同じページを要求した場合でも、そのページがキャッシュ内にない別のフロントエンド web サーバーに負荷分散されます。 この最後のケースでは、キャッシュを使用してユーザーをまったくサポートしていません。
  
次の図では、各ドットは、ユーザーが要求しているページと、キャッシュされた場所を表しています。 さまざまな色は、SaaS インフラストラクチャを共有するために使用するさまざまな顧客を表します。
  
![SharePoint Online におけるオブジェクト キャッシュの結果を示します](media/25d04011-ef83-4cb7-9e04-a6ed490f63c3.png)
  
図からわかるように、特定のユーザーがキャッシュされたページを使用してサーバーにヒットする可能性はスリムです。 また、スループットが大きく、サーバーが多数のサイト間で共有されているため、キャッシュが使用可能な領域が1つしかないため、キャッシュが最後まで長くなっているわけではありません。
  
これらのすべての理由から、ユーザーにキャッシュされたオブジェクトを取得することは、SharePoint Online でユーザーの品質を向上させるための効果的な方法ではありません。
  
## <a name="if-we-cant-rely-on-the-object-cache-to-improve-performance-in-sharepoint-online-what-do-we-use-instead"></a>SharePoint Online のパフォーマンスを向上させるためにオブジェクトキャッシュを使用できない場合は、どうすればよいでしょうか。

SharePoint Online ではキャッシュを使用しないようにする必要があるため、オブジェクトキャッシュを使用する SharePoint カスタマイズの代替デザイン方法を評価する必要があります。 これは、ユーザーにとって適切な結果を得るために、オブジェクトキャッシュに依存しないパフォーマンスの問題を解決する手法を使用することを意味します。 これについては、このシリーズの他の記事に記載されている内容を参照してください。
  
- [SharePoint Online のナビゲーション オプション](navigation-options-for-sharepoint-online.md)
    
- [SharePoint Online での縮小とバンドル](minification-and-bundling-in-sharepoint-online.md)
    
- [コンテンツ配信ネットワークの使用](using-content-delivery-networks-with-sharepoint-online.md)
    
- [SharePoint Online での画像の読み込み遅延と JavaScript](delay-loading-images-and-javascript-in-sharepoint-online.md)
    

