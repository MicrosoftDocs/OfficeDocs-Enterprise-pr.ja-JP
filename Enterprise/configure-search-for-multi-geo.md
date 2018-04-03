---
title: 複数地域の環境を管理します。
ms.author: tlarsen
author: tklarsen
manager: arnek
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: マルチ地域環境での検索を構成する方法について説明します。
ms.openlocfilehash: 0c5c8eaa981c31151c70507da54587a7269f98f5
ms.sourcegitcommit: 3f3d2de6c0c5225156cfba01bc980994cd9ae848
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/03/2018
---
# <a name="configure-search-for-onedrive-for-business-multi-geo"></a>ビジネスの複数の地域の OneDrive の検索を構成します。

マルチ Geo SharePoint オンライン (SPO) 環境で組織、1 つの Office 365 テナント、複数の地理的な場所に、SharePoint のコンテンツを格納する 1 つの場所と 1 つ以上サテライト地域の場所です。

各の地理的な場所では、独自の検索インデックスと検索センターがあります。ユーザーが検索してクエリは、すべてのインデックスさばいたが返される結果がマージされます。

などの地域の 1 つの場所のユーザーは、地域の別の場所に保存されたコンテンツまたは地域の別の場所に制限されている SharePoint サイト上のコンテンツを検索できます。このコンテンツへのアクセスをユーザーには、検索で結果が表示されます。

## <a name="which-search-clients-work-in-a-multi-geo-environment"></a>複数地域の環境でクライアントの作業を検索するでしょうか。

これらのクライアントでは、地域のすべての場所から結果を返すことができます。

-   OneDrive for Business

-   Delve

-   SharePoint ホーム ページ

-   検索センター

-   SharePoint 検索 API を使用するカスタムの検索アプリケーション

### <a name="onedrive-for-business"></a>OneDrive for Business

複数地域の環境が設定されているとすぐに OneDrive で検索するユーザーは、地域のすべての場所から結果を取得します。

### <a name="delve"></a>Delve

複数地域の環境が設定されているとすぐに Delve で検索するユーザーは、地域のすべての場所から結果を取得します。

Delve のフィード、プロファイルのカードは**中央**の場所に格納されているファイルのプレビューにのみ表示されます。サテライト地域の場所に格納されているファイルの場合は、代わりにファイルの種類のアイコンが表示されます。

### <a name="the-sharepoint-home-page"></a>SharePoint ホーム ページ

ユーザー複数地域の環境が設定されているとすぐには、ニュースが、SharePoint のホーム ページに複数の地域の場所からのリンクと最近のサイトに表示されます。SharePoint ホーム ページで [検索] ボックスを使用する場合にのみ結果を得る、地域の場所 SPHome からに検索インデックスがあります。

### <a name="the-search-center"></a>検索センター

複数の地域の後の環境が設定されて、各検索センターは引き続き表示結果だけが自分の地域の場所から。管理者は、[各検索センターの設定を変更する](#_Set_up_a_1)地域のすべての場所から結果を取得する必要があります。その後、検索センターで検索するユーザーは、地域のすべての場所から結果を取得します。

### <a name="custom-search-applications"></a>カスタムの検索アプリケーション

いつものように、カスタム検索アプリケーションは、既存の SharePoint 検索 REST Api を使用しての検索用のインデックスと対話します。全部または一部の地域の場所から結果を得るには、アプリケーション[API を呼び出すし複数地域の新しいクエリのパラメーターは、](#_Get_custom_search)要求で必要があります。これにより、地域のすべての場所へのクエリからのファンがトリガーされます。

### <a name="whats-different-about-search-in-a-multi-geo-environment"></a>マルチ地域環境での検索に関するさまざまなは何ですか。

いくつかの検索機能を学習し、する必要がありますが、複数地域環境で作業とは異なる。

<table>
<thead>
<tr class="header">
<th align="left"><strong>機能</strong></th>
<th align="left"><strong>どのように動作します。</strong></th>
<th align="left"><strong>回避策</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">昇格した結果</td>
<td align="left">クエリ ルールを作成するにはさまざまなレベルに昇格した結果: 全体のテナント、サイト コレクションまたはサイトです。マルチ地域環境では、地域の<strong>すべて</strong>の場所で検索センター結果を昇格する場合は、<strong>テナント</strong>のレベルに昇格した結果を定義します。場合<strong>のみ</strong>サイト コレクションまたはサイトの地域の場所にある検索センターでの結果を促進する、<strong>サイト コレクション</strong>または<strong>サイト</strong>レベルでの結果を定義します。</td>
<td align="left">個々 の地域の場所、旅をするなどの別のルールの異なる昇格した結果を必要としない場合は、テナントのレベルで結果を昇格を定義することをお勧めします。</td>
</tr>
<tr class="even">
<td align="left">検索の絞り込み条件</td>
<td align="left">検索では、テナントのすべての地域の場所から絞り込み条件が返されます、それが集計されます。集計は、絞り込み条件の数が 100% 正確な可能性がありますできないことを意味するよう、最善の努力です。ほとんどの検索ベースのシナリオでは、この精度で十分です。</td>
<td align="left">絞り込み条件の完全性に依存する検索駆動型アプリケーションを照会しない各地域拠点個別に複数地域のファンを使用せず。</td>
</tr>
<tr class="odd">
<td align="left"></td>
<td align="left">マルチ地域検索では、数値絞り込み条件の動的なバケットをサポートしていません。</td>
<td align="left">数値絞り込み条件の<a href="https://docs.microsoft.com/en-us/sharepoint/dev/general-development/query-refinement-in-sharepoint">「Discretize」パラメーター</a>を使用します。</td>
</tr>
<tr class="even">
<td align="left">ドキュメント Id</td>
<td align="left">ドキュメント Id に依存している、検索駆動型アプリケーションを開発する場合は、地域拠点に複数地域の環境でドキュメント Id は一意、geo の場所ごとに一意であることに注意してください。</td>
<td align="left">地域の場所を識別する列を追加しました。一意性を達成するためにこの列を使用します。この列を"GeoLocationSource"といいます。</td>
</tr>
<tr class="odd">
<td align="left">結果の数</td>
<td align="left">検索結果のページは、geo の場所からの結合された結果を示していますが、ページの 500 件の結果を超えることはできません。</td>
<td align="left"></td>
</tr>
</tbody>
</table>

### <a name="whats-not-supported-for-search-in-a-multi-geo-environment"></a>マルチ地域環境での検索の内容はサポートされていませんでしょうか。

複数地域の環境で学習し、する必要があります検索機能の一部がサポートされていません。

<table>
<thead>
<tr class="header">
<th align="left"><strong>検索機能</strong></th>
<th align="left"><strong>注</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">アプリケーション専用の認証</td>
<td align="left">マルチ地域検索では、アプリケーション専用の認証 (サービスからのアクセス権限) はサポートされていません。</td>
</tr>
<tr class="even">
<td align="left">ゲスト ユーザー</td>
<td align="left">ゲスト ユーザーは、検索をしている地域の場所からのみ結果を取得します。</td>
</tr>
</tbody>
</table>

### <a name="how-does-search-work-in-a-multi-geo-environment"></a>検索の動作方法、複数地域の環境で

**すべて**検索クライアントを使用して、既存の SharePoint 検索 REST Api 検索用のインデックスを操作します。

<table>
<thead>
<tr class="header">
<th align="left"><p><img src="media/configure-search-for-multi-geo_image1.png" /></p>
<p>図 1: 地域の 3 つの場所とテナント間での検索</p></th>
<th align="left"><p>検索のクライアントは、クエリのプロパティ EnableMultiGeoSearch を使用して検索 REST エンドポイントを呼び出す true です。</p>
<p>テナントのすべての地域の場所にクエリが送信されます。</p>
<p>各地域の場所から検索結果がマージされ、ランク付けされます。</p>
<p>クライアントでは、統合された検索結果を取得します。</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

<span id="_Set_up_a" class="anchor"><span id="_Ref501388384" class="anchor"></span></span>複数地域の検索は、各地域での検索の各エンドポイントを呼び出すことによって機能します。リモート移動要求を並列に実行されますが、発生をマージするには返信する前に、結合する最も低速な区間を待ちます。つまり、複数地域検索機能に追加の遅延を追加します。 <span id="_Set_up_a_1" class="anchor"><span id="_Ref505252370" class="anchor"></span></span> 
###地域のすべての場所からの結果を表示する検索センターを取得

各検索センターにはいくつかの業界を使用して個別にそれぞれの垂直方向を設定します。

1.  検索結果ページや検索結果の Web パーツを編集する権限を持つアカウントを使用して、次の手順を実行することを確認します。

2.  検索結果のページに移動します ([ボックスの一覧](https://support.office.com/article/174d36e0-2f85-461a-ad9a-8b3f434a4213)の検索結果のページを参照してください)

3.  設定し、上、右下の歯車アイコンの**設定**をクリックして、**ページの編集**] をクリックし、垂直方向を選択します。

> ![](media/configure-search-for-multi-geo_image2.png)
>
> 検索結果ページが編集モードで開きます。

1.  検索結果の Web パーツで、上にポインターを移動、Web パーツの右にある矢印をクリックし、メニューの [ **Web パーツの編集**] をクリックします。 ![](media/configure-search-for-multi-geo_image3.png)

> 上部のリボンの下の検索結果 Web パーツ ツール ウィンドウが開き、ページの右。

1.  Web パーツ ツール ウィンドウの [**設定**] セクションの**設定を制御する結果**を、下には、地域のすべての場所からの結果を表示する検索結果 Web パーツを取得するのには**複数の地域の表示結果**を選択します。

2.  変更を保存し、Web パーツ ツール ウィンドウを閉じるには、 **[ok]**をクリックします。

3.  メイン メニューの [ページ] タブの [**チェックイン**] をクリックして、検索結果 Web パーツに加えた変更を確認します。

4.  ページの上部にあるメモに記載されているリンクを使用して変更内容を発行します。

<span id="_Get_custom_search" class="anchor"><span id="_Ref501388387" class="anchor"></span></span>
### <a name="get-custom-search-applications-to-show-results-from-all-or-some-geo-locations"></a>すべてまたは一部の地域の場所からの結果を表示するカスタムの検索アプリケーションを取得します。

カスタムの検索アプリケーションは、SharePoint 検索 REST API への要求にクエリ パラメーターを指定することにより全部または一部、地域の場所からの結果を得る。クエリのパラメーターによって、地域のすべての場所に、またはいくつかの地域拠点に、クエリさばいた。などの関連情報を検索する場所を地域のサブセットのクエリを実行する場合は、これらだけにファンを制御できます。要求が成功すると、SharePoint の検索 REST API は応答データを返します。

### <a name="query-parameters"></a>クエリ パラメーター

**EnableMultiGeoSearch** - これは、クエリを複数地域テナントの他の地域の場所のインデックスさばいたものとするかどうかを指定するブール値です。に**true を指定**するクエリを設定します。**false を指定**しないクエリが 。既定値は、 **false を指定**します。このパラメーターを指定しない場合、クエリは、他の地域の場所に、**ない**さばいた。複数地域ではない環境で、パラメーターを使用する場合、パラメーターは無視されます。

**顧客タイプ**には、文字列です。検索アプリケーションごとに一意のクライアント名を入力します。このパラメーターを指定しない場合、クエリは、他の地域の場所に、**ない**さばいた。

**MultiGeoSearchConfiguration** - これは、どの地域の複数の地域での場所のテナント**EnableMultiGeoSearch**が**true**の場合に、クエリをファンに省略可能な一覧です。、このパラメーターを指定するか、空欄のままにしない、クエリはすべての地域の場所さばいた。各地域の場所では、JSON 形式で次の項目を入力します。

<table>
<thead>
<tr class="header">
<th align="left">項目</th>
<th align="left">説明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">DataLocation</td>
<td align="left">Geo 場所、たとえば名です。</td>
</tr>
<tr class="even">
<td align="left">エンドポイント</td>
<td align="left">たとえば、接続するエンドポイントhttps://contoso.sharepoint.com</td>
</tr>
<tr class="odd">
<td align="left">SourceId</td>
<td align="left">結果のソース、たとえば B81EAB55-3140-4312-B0F4-9459D1B4FFEE の GUID です。</td>
</tr>
</tbody>
</table>

DataLocation またはエンドポイントを省略した場合、または、DataLocation が重複している場合は、要求は失敗します。[Microsoft Graph を使用して、テナントの geo の場所のエンドポイントに関する情報を取得することができます](https://docs.microsoft.com/en-us/sharepoint/dev/solution-guidance/multigeo-discovery)。

### <a name="response-data"></a>応答データ

**MultiGeoSearchStatus** – これは、SharePoint Search API 要求への応答を返すプロパティです。プロパティの値は文字列であり、SharePoint Search API が返す結果をに関する次の情報を提供します。

<table>
<thead>
<tr class="header">
<th align="left">値</th>
<th align="left">説明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">完全</td>
<td align="left">地域の場所から<strong>すべて</strong>の結果の完全な。</td>
</tr>
<tr class="even">
<td align="left">一部</td>
<td align="left">1 つまたは複数の地域の場所からの部分的な結果です。結果では、一時的なエラーのため完了できません。</td>
</tr>
<tr class="odd">
<td align="left">なし</td>
<td align="left">クエリ複数地域のクエリとその他の地域の場所さばいたがありません。</td>
</tr>
</tbody>
</table>

### <a name="query-using-the-rest-service"></a>REST サービスを使用してクエリ

GET 要求では、URL にクエリ パラメーターを指定します。POST 要求では、JavaScript オブジェクト表記法 (JSON) 形式の本文にクエリのパラメーターを渡します。

#### <a name="request-headers"></a>要求ヘッダー

<table>
<thead>
<tr class="header">
<th align="left">名前</th>
<th align="left">値</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Content-Type</td>
<td align="left">アプリケーションまたは json; odata = 詳細</td>
</tr>
</tbody>
</table>

#### <a name="sample-get-request-thats-fanned-out-to-all-geo-locations"></a>地域の**すべて**の場所さばいたが GET 要求のサンプル

https://\<テナント\>/\_api/検索/query?querytext 'sharepoint' とプロパティを = 'EnableMultiGeoSearch:true' と顧客タイプを = =' 私\_クライアント\_id'

#### <a name="sample-get-request-to-fan-out-to-some-geo-locations"></a>サンプル GET 要求で**いくつか**の地域拠点に広がる

https:// <tenant>/_api/search/query?querytext 'site' & 顧客タイプを = 'my_client_id' とプロパティを = ='EnableMultiGeoSearch:true、MultiGeoSearchConfiguration: [{DataLocation\:「名前」\,エンドポイント\:"https\:contosoNAM.sharepoint.com"\,SourceId\:"B81EAB55-3140-4312-B0F4-9459D1B4FFEE"}\,{DataLocation\:」が「\,エンドポイント\:"https\://contosoCAN.sharepoint-df.com"}]'

#### <a name="sample-post-request-thats-fanned-out-to-all-geo-locations"></a>地域の**すべて**の場所さばいた、POST 要求のサンプル

    {
        "request": {
            "__metadata": {
            "type": "Microsoft.Office.Server.Search.REST.SearchRequest"
        },
        "Querytext": "sharepoint",
        "Properties": {
            "results": [
                {
                    "Name": "EnableMultiGeoSearch",
                    "Value": {
                        "QueryPropertyValueTypeIndex": 3,
                        "BoolVal": true
                    }
                }
            ]
        },
        "ClientType": "my_client_id"
        }
    }


#### <a name="sample-post-request-thats-fanned-out-to-some-geo-locations"></a>**いくつか**の地域拠点にさばいたは、POST 要求のサンプル


    {
        "request": {
            "Querytext": "SharePoint",
            "ClientType": "my_client_id",
            "Properties": {
                "results": [
                    {
                        "Name": "EnableMultiGeoSearch",
                        "Value": {
                            "QueryPropertyValueTypeIndex": 3,
                            "BoolVal": true
                        }
                    },
                    {
                        "Name": "MultiGeoSearchConfiguration",
                        "Value": {
                        "StrVal": "[{\"DataLocation\":\"NAM\",\"Endpoint\":\"https://contoso.sharepoint.com\",\"SourceId\":\"B81EAB55-3140-4312-B0F4-9459D1B4FFEE\"},{\"DataLocation\":\"CAN\",\"Endpoint\":\"https://contosoCAN.sharepoint.com\"}]",
                            "QueryPropertyValueTypeIndex": 1
                        }
                    }
                ]
            }
        }
    }

### <a name="query-using-csom"></a>CSOM を使用してクエリ

地域の**すべて**の場所さばいた、CSOM クエリの例を以下に示します。

    var keywordQuery = new KeywordQuery(ctx);
    keywordQuery.QueryText = query.SearchQueryText;
    keywordQuery.ClientType = <enter a string here>;
    keywordQuery["EnableMultiGeoSearch"] = true;