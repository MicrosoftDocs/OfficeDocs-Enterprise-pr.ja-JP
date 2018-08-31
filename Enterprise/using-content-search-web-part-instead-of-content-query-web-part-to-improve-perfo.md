---
title: コンテンツ クエリ Web パーツではなくコンテンツ検索 Web パーツを使用して SharePoint Online でのパフォーマンスを向上させる
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 4/20/2015
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
ms.assetid: e8ce6b72-745b-464a-85c7-cbf6eb53391b
description: この資料では、コンテンツ クエリ Web パーツを SharePoint Server 2013 と SharePoint Online のコンテンツ検索 Web パーツで置き換えることによってパフォーマンスを向上させる方法について説明します。
ms.openlocfilehash: f86a4b75c4bf75ebaa99924411d017c7eb7b6760
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541831"
---
# <a name="using-content-search-web-part-instead-of-content-query-web-part-to-improve-performance-in-sharepoint-online"></a>コンテンツ クエリ Web パーツではなくコンテンツ検索 Web パーツを使用して SharePoint Online でのパフォーマンスを向上させる

この資料では、コンテンツ クエリ Web パーツを SharePoint Server 2013 と SharePoint Online のコンテンツ検索 Web パーツで置き換えることによってパフォーマンスを向上させる方法について説明します。
  
SharePoint Server 2013 と SharePoint Online の最も強力な新機能の 1 つは、コンテンツ検索 Web パーツ (CSWP) です。この Web パーツは、ユーザーに示されている結果を迅速に取得するのには、検索インデックスを使用します。ユーザーのパフォーマンスを向上させるためにではなく、コンテンツ クエリ Web パーツ (CQWP)、ページのコンテンツ検索 Web パーツを使用します。
  
コンテンツ クエリ Web パーツにコンテンツ検索 Web パーツを使用するほとんどの場合、SharePoint Online のページ読み込みのパフォーマンスを大幅に向上されます。右のクエリを取得するのには少し追加の構成がありますが、パフォーマンスを向上させるとすれば、ユーザーは。
  
## <a name="comparing-the-performance-gain-you-get-from-using-content-search-web-part-instead-of-content-query-web-part"></a>コンテンツ クエリ Web パーツではなくコンテンツ検索 Web パーツを使用してから取得したパフォーマンスの向上を比較します。

次の例では、コンテンツ クエリ Web パーツではなくコンテンツ検索 Web パーツを使用すると表示される相対的なパフォーマンス上の利点を示しています。効果は、複雑なサイト構造と非常に広範なコンテンツ クエリではわかりやすい。
  
この例のサイトには、次の特徴があります。
  
- サブサイトの 8 レベルです。
    
- 「フルーツ」のカスタム コンテンツ タイプを使用して一覧表示します。
    
- Web パーツでコンテンツのクエリは全体を見て、「フルーツ」のコンテンツ タイプのすべての項目を返すことです。
    
- のみ 8 のサイト間で 50 の項目を使用します。効果がもより顕著になるサイトのより多くのコンテンツを持つ。
    
コンテンツ クエリ Web パーツの結果のスクリーン ショットを次に示します。
  
![Web パーツのクエリ結果を示すグラフィック](media/b3d41f20-dfe5-46ed-9c0a-31057e82de33.png)
  
Internet Explorer では、F12 開発者ツールの [**ネットワーク**] タブを使用して、応答ヘッダーの詳細を確認します。次のスクリーン ショットでは、このページの読み込みの**SPRequestDuration**の値は、924 ミリ秒です。 
  
![924 の要求時間が表示されているスクリーンショット](media/343571f2-a249-4de2-bc11-2cee93498aea.png)
  
 **SPRequestDuration**では、ページを準備するのにはサーバー上で実行された作業量を示します。検索 Web パーツでコンテンツ クエリ Web パーツでコンテンツを大幅に切り替え、ページのレンダリングにかかる時間が減少します。対照的に、同等でコンテンツ検索 Web パーツをページには、106 時間をミリ秒単位でこのスクリーン ショットに示すように、 **SPRequestDuration**値が含まれて同じ数の結果を返します。 
  
![106 の要求時間が表示されているスクリーンショット](media/b46387ac-660d-4e5e-a11c-cc430e912962.png)
  
## <a name="adding-a-content-search-web-part-in-sharepoint-online"></a>SharePoint のオンライン コンテンツの検索 Web パーツを追加します。

コンテンツ検索 Web パーツを追加する、正規のコンテンツ クエリ Web パーツに似ています。セクションでは、 [SharePoint のコンテンツ検索 Web パーツを構成する](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a) *」、コンテンツ検索 Web パーツの追加」* を参照してください。
  
## <a name="creating-the-right-search-query-for-your-content-search-web-part"></a>コンテンツ検索 Web パーツの適切な検索クエリを作成します。

コンテンツ検索 Web パーツを追加すると、検索を絞り込むし、目的のアイテムを取得できます。これを行う方法の詳細については、 [SharePoint のコンテンツ検索 Web パーツの構成](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a)での *「コンテンツ検索 Web パーツでの高度なクエリを構成することでコンテンツ表示を」* のセクションを参照してください。
  
## <a name="query-building-and-testing-tool"></a>クエリを構築およびテスト ツール

ビルドし、複雑なクエリをテストするツール、Codeplex で[検索クエリ ツール](https://sp2013searchtool.codeplex.com/)を参照してください。 
  

