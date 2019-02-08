---
title: SharePoint Online でのオブジェクト キャッシュの使用
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 4/20/2015
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 38bc9c14-3826-449c-beb6-b1003bcbeaaf
description: この資料では、SharePoint Server 2013 設置し、SharePoint Online でのオブジェクト キャッシュを使用しての違いについて説明します。
ms.openlocfilehash: 59f3a69199893cb367d4d28c0c545ebd9dfd1236
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2019
ms.locfileid: "25769856"
---
# <a name="using-the-object-cache-with-sharepoint-online"></a>SharePoint Online でのオブジェクト キャッシュの使用

この資料では、SharePoint Server 2013 設置し、SharePoint Online でのオブジェクト キャッシュを使用しての違いについて説明します。
  
SharePoint Online の展開では、オブジェクト キャッシュに依存するという悪影響があります。SharePoint Online でのオブジェクト キャッシュの依存関係はすべて、ページの信頼性を低下させます。 
  
## <a name="how-the-sharepoint-online-and-sharepoint-server-2013-object-cache-works"></a>SharePoint Online と SharePoint Server 2013 オブジェクトのキャッシュのしくみ

SharePoint Server 2013 は、オンプレミスでホストされているが、お客様には、オブジェクト キャッシュをホストするプライベートのフロント エンド web サーバーが持っています。これは、キャッシュを選択し、1 人の顧客は、専用メモリの量は、使用可能で、オブジェクト キャッシュに割り当てられているによってのみ制限を意味します。設置型のシナリオで 1 つだけのお客様に配信されるためフロント エンド web サーバーはユーザーが同じサイトに要求を作成すると、何度でも通常あります。つまり、キャッシュが完全に迅速に取得し、クエリ結果のリストと、ユーザーが定期的に要求している SharePoint オブジェクトのフルのままです。
  
![オンプレミスのフロントエンド Web サーバーへのトラフィックと負荷を示しています](media/a0d38b36-4909-4abb-8d4e-4930814bb3de.png)
  
結果として、ユーザーが 2 回目にページにアクセスするとき、ページの読み込み時間が短縮します。同じページを 4 回以上読み込むと、ページはすべてのフロントエンド Web サーバーにキャッシュされます。
  
対照的に、SharePoint Online は、多くのより多くのサーバがより多くのサイトもいます。各ユーザーは、キャッシュ設定を設定していない別のフロント エンド web サーバーに接続できます。または、おそらくキャッシュが値を設定、サーバーが次のユーザーのページがそのフロント エンド web サーバーの要求を別のサイトから。または、場合でも、次のユーザーは、同じページを要求の場合、前回の訪問と、キャッシュ内にそのページを持たない別のフロント エンド web サーバーに負荷分散します。この最後の場合では、キャッシュ問題が解決しないユーザーにします。
  
次の図で、各ドットはユーザーが要求していて、キャッシュされているページを表しています。さまざまな色は、SaaS インフラストラクチャを共用しているさまざまな顧客を表します。
  
![SharePoint Online におけるオブジェクト キャッシュの結果を示します](media/25d04011-ef83-4cb7-9e04-a6ed490f63c3.png)
  
図からわかるように、スリムには特定のユーザーにそのページのキャッシュされたバージョンのサーバーの可能性があります。また、大規模なスループットとサーバーは、多くのサイト間で共有されるという事実、キャッシュは最後のだけ領域をキャッシュするため、使用のために長いです。
  
これらすべての理由から、ユーザーがキャッシュされたオブジェクトを取得するのに依存することは、SharePoint Online でユーザー体験とページの読み込み時間の品質を保証する効果的な方法ではありません。
  
## <a name="if-we-cant-rely-on-the-object-cache-to-improve-performance-in-sharepoint-online-what-do-we-use-instead"></a>SharePoint Online でパフォーマンスを向上させるためにオブジェクト キャッシュに依存できないとしたら、代わりに何を使用すればよいでしょうか。

SharePoint Online でのキャッシュに依存しないほうがよいため、オブジェクト キャッシュを使用する SharePoint のカスタマイズに関する代わりの設計アプローチを評価する必要があります。つまり、ユーザーに良い結果をもたらすため、オブジェクトのキャッシュに依存しないパフォーマンスの問題のアプローチを使用するということです。これについては、このシリーズの他の記事で説明しています。それらは次のとおりです。
  
- [SharePoint Online のナビゲーション オプション](navigation-options-for-sharepoint-online.md)
    
- [SharePoint Online での縮小とバンドル](minification-and-bundling-in-sharepoint-online.md)
    
- [コンテンツ配信ネットワークの使用](using-content-delivery-networks-with-sharepoint-online.md)
    
- [SharePoint Online での画像の読み込み遅延と JavaScript](delay-loading-images-and-javascript-in-sharepoint-online.md)
    

