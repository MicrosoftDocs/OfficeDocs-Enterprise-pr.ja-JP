---
title: SharePoint Online のパフォーマンスを向上させるために、コンテンツのクエリ Web パーツの代わりにコンテンツ検索 Web パーツを使用する
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 4/20/2015
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- SPO160
ms.assetid: e8ce6b72-745b-464a-85c7-cbf6eb53391b
description: SharePoint Server 2013 および SharePoint Online のコンテンツクエリ Web パーツをコンテンツ検索 Web パーツに置き換えて、パフォーマンスを向上させる方法について説明します。
ms.openlocfilehash: 50706236c3ecdbdf915c257877990c4b9e51e22a
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/10/2020
ms.locfileid: "46603539"
---
# <a name="using-content-search-web-part-instead-of-content-query-web-part-to-improve-performance-in-sharepoint-online"></a>SharePoint Online のパフォーマンスを向上させるために、コンテンツのクエリ Web パーツの代わりにコンテンツ検索 Web パーツを使用する

この記事では、コンテンツクエリ Web パーツを SharePoint Server 2013 および SharePoint Online のコンテンツ検索 Web パーツに置き換えることによって、パフォーマンスを向上させる方法について説明します。
  
SharePoint Server 2013 と SharePoint Online の最も強力な新機能の1つは、コンテンツ検索 Web パーツ (CSWP) です。 この Web パーツは、検索インデックスを使用して、ユーザーに表示される結果をすばやく取得します。 ページのコンテンツクエリ Web パーツ (CQWP) の代わりにコンテンツ検索 Web パーツを使用して、ユーザーのパフォーマンスを向上させます。
  
コンテンツクエリ Web パーツを使用してコンテンツ検索 Web パーツを使用すると、ほとんどの場合、SharePoint Online でのページ読み込みのパフォーマンスが大幅に向上します。 適切なクエリを取得するには、さらに多くの構成がありますが、報奨はパフォーマンスが向上し、ユーザーの満足度が向上します。
  
## <a name="comparing-the-performance-gain-you-get-from-using-content-search-web-part-instead-of-content-query-web-part"></a>コンテンツクエリ Web パーツの代わりにコンテンツ検索 Web パーツを使用して得られるパフォーマンスの向上を比較する

次の例では、コンテンツクエリ Web パーツの代わりにコンテンツ検索 Web パーツを使用するときに表示される可能性があるパフォーマンスの向上を示します。 この効果は、複雑なサイト構造と非常に広範なコンテンツのクエリによって明確になります。
  
この例のサイトには、次のような特徴があります。
  
- サブサイトの8つのレベル。
    
- カスタムの "フルーツ" コンテンツタイプを使用してリストを作成します。
    
- Web パーツでは、コンテンツクエリは広範で、コンテンツタイプが "フルーツ" のすべてのアイテムを返します。
    
- この例では、8つのサイト全体で50アイテムのみを使用します。 この効果は、より多くのコンテンツがあるサイトに対してさらに顕著になります。
    
ここでは、コンテンツクエリ Web パーツの結果のスクリーンショットを示します。
  
![Web パーツのクエリ結果を示すグラフィック](media/b3d41f20-dfe5-46ed-9c0a-31057e82de33.png)
  
Internet Explorer で、F12 開発者ツールの [**ネットワーク**] タブを使用して、応答ヘッダーの詳細を確認します。 次のスクリーンショットでは、このページ読み込みの**Sprequestduration**の値は924ミリ秒です。 
  
![924 の要求時間が表示されているスクリーンショット](media/343571f2-a249-4de2-bc11-2cee93498aea.png)
  
 **Sprequestduration**は、ページを準備するためにサーバー上で実行された作業量を示します。 コンテンツを検索する Web パーツを使用してコンテンツをクエリ Web パーツに切り替えることで、ページのレンダリングにかかる時間が大幅に短縮されます。 対照的に、このスクリーンショットに示されているように、同じコンテンツ検索 Web パーツを持つページは、同じ数の結果が106ミリ秒の**Sprequestduration**値を返します。 
  
![106 の要求時間が表示されているスクリーンショット](media/b46387ac-660d-4e5e-a11c-cc430e912962.png)
  
## <a name="adding-a-content-search-web-part-in-sharepoint-online"></a>SharePoint Online でコンテンツ検索 Web パーツを追加する

コンテンツ検索 Web パーツの追加は、通常のコンテンツクエリ Web パーツによく似ています。 「 [SharePoint でコンテンツ検索 Web パーツを構成](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a)する」の「*コンテンツ検索 Web パーツを追加する」* セクションを参照してください。
  
## <a name="creating-the-right-search-query-for-your-content-search-web-part"></a>コンテンツ検索 Web パーツ用の適切な検索クエリを作成する

コンテンツ検索 Web パーツを追加したら、検索を絞り込み、必要なアイテムを返すことができます。 この手順の詳細については、「 [SharePoint でコンテンツ検索 Web パーツを構成](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a)する」の「コンテンツ*検索 web パーツの詳細なクエリを構成してコンテンツを表示*する」を参照してください。
  
## <a name="query-building-and-testing-tool"></a>クエリ構築およびテストツール

複雑なクエリを作成およびテストするツールについては、Codeplex の[検索クエリツール](https://sp2013searchtool.codeplex.com/)を参照してください。 
  

