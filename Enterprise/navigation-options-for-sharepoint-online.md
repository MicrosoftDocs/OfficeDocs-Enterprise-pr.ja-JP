---
title: SharePoint Online のナビゲーション オプション
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: adb92b80-b342-4ecb-99a1-da2a2b4782eb
description: この記事では、SharePoint Publishing が有効化されている SharePoint Online サイトのナビゲーション オプションについて説明します。 ナビゲーションの選択と構成は、SharePoint Online のサイトのパフォーマンスと拡張性に大きく影響します。 この記事は、従来のチーム サイトには適用されません。
ms.openlocfilehash: d86b0462e8ddb93c39eab0d42a24f3a94f785ecd
ms.sourcegitcommit: 89ecf793443963b4c87cf1033bf0284cbfb83d9a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2019
ms.locfileid: "38078312"
---
# <a name="navigation-options-for-sharepoint-online"></a>SharePoint Online のナビゲーション オプション

この記事では、SharePoint Publishing が有効化されている SharePoint Online サイトのナビゲーション オプションについて説明します。 ナビゲーションの選択と構成は、SharePoint Online のサイトのパフォーマンスとスケーラビリティに大きく影響します。

## <a name="overview"></a>概要

ナビゲーション プロバイダーの構成はサイト全体のパフォーマンスに大きな影響を与える可能性があるため、SharePoint サイトの要件を満たすように効果的に対応できるナビゲーション プロバイダーと構成を慎重に選択する必要があります。 2 つの既成のナビゲーション プロバイダーの他、ナビゲーションのカスタム実装が提供されています。

1 番目のオプションの[**管理 (メタデータ) ナビゲーション**](#using-managed-navigation-and-metadata-in-sharepoint-online)をお勧めします。これは、SharePoint Online の既定のオプションの 1 つでもあります。ただし、必要がない場合は、セキュリティ トリミングを無効にすることをお勧めします。 セキュリティ トリミングは既定によるセキュリティ保護としてこのナビゲーション プロバイダーで有効化されていますが、多くのサイトでは、サイトのすべてのユーザーに対して一貫性のあるナビゲーション要素を提供しているため、セキュリティ トリミングのオーバーヘッドは必要ありません。 推奨されているセキュリティトリミングを無効にする構成にした場合、このナビゲーション プロバイダーではサイト構造を列挙する必要がなく、パフォーマンスへの影響を許容範囲に抑えながら高い拡張性が提供されます。

2 番目のオプションの[**構造ナビゲーション**](#using-structural-navigation-in-sharepoint-online)は、**SharePoint Online で推奨されるナビゲーション オプションではありません**。  このナビゲーション プロバイダーは、オンプレミスのトポロジ用に設計されており、SharePoint Online でのサポートは限定的です。 このプロバイダーでは他のナビゲーション オプションで提供されていない追加の機能が提供されますが、このプロバイダーを使用する場合、セキュリティ トリミングやサイト構造の列挙などを含むこれらの機能は過度のサーバーの呼び出しやスケーラビリティおよびパフォーマンスの低下を引き起こします。 構造ナビゲーションを使用するサイトのうち、リソースの消費が過剰なサイトは調整の対象になる場合があります。

既成のナビゲーション プロバイダーに加えて、多くのお客様が代替のカスタム ナビゲーション実装を正常に実装しています。 カスタム ナビゲーション実装の一般的なクラスの 1 つとして、ナビゲーション ノードのローカル キャッシュを格納するクライアント レンダリングによるデザイン パターンがあります。 (この記事の「**[検索型クライアント側スクリプト ](#using-search-driven-client-side-scripting)**」を参照してください。)

これらのナビゲーション プロバイダーには、いくつかの大きな利点があります。 
- これらのナビゲーション プロバイダーは通常、応答性の高いページ デザインに適しています。
- リソース コストをかけずにレンダリングできるため、拡張性が高く、高性能です (また、タイムアウト後にバックグラウンドでの更新が可能です)。 
- これらのナビゲーション プロバイダーは、単純な静的構成からさまざまな動的データ プロバイダーまでを含む、さまざまな方法を使用してナビゲーション データを取得できます。 

データ プロバイダーの例として、ナビゲーション ノードの列挙とセキュリティ トリミングの効率的な処理が可能な**検索型ナビゲーション**を使用する方法があります。 

**カスタム ナビゲーション プロバイダー**を構築するための一般的なオプションは他にもあります。 カスタム ナビゲーション プロバイダーを構築する方法に関するより詳細なガイダンスついては、「[SharePoint Online ポータル用のナビゲーション ソリューション](https://docs.microsoft.com/sharepoint/dev/solution-guidance/portal-navigation)」を参照してください。
  
## <a name="pros-and-cons-of-sharepoint-online-navigation-options"></a>SharePoint Online ナビゲーション オプションの長所と短所

次の表は、各オプションの長所と短所をまとめたものです。 


|管理ナビゲーション  |構造ナビゲーション  |検索型ナビゲーション  |カスタム ナビゲーション プロバイダー  |
|---------|---------|---------|---------|
|長所:<br/><br/>メンテナンスしやすい<br/>推奨されるオプション<br/>     |長所:<br/><br/>構成しやすい<br/>セキュリティ トリミングが行われる<br/>コンテンツが追加されると自動的に更新される<br/>|長所:<br/><br/>セキュリティ トリミングが行われる<br/>サイトが追加されると自動的に更新される<br/>読み込み時間が短く、ナビゲーション構造がローカルにキャッシュされている<br/>|長所:<br/><br/>使用可能なオプションの選択肢が広い<br/>キャッシュが正常に使用された場合、高速の読み込み<br/>多くのオプションが、応答性の高いページ デザインで適正に動作する<br/>|
|短所:<br/><br/>サイト構造を反映するように自動的に更新されない<br/>セキュリティ トリミングが有効になっている場合、パフォーマンスが低下する<br/>|短所:<br/><br/>**非推奨**<br/>**パフォーマンスとスケーラビリティへの影響**<br/>**調整の対象**<br/>|短所:<br/><br/>サイトの順序を簡単に変更できない<br/>マスター ページのカスタマイズが必要 (技術的なスキルが必要)<br/>|短所:<br/><br/>カスタム開発が必要<br/>外部データ ソース / 格納されたキャッシュが必要 (例: Azure)<br/>|

サイトに最適なオプションは、サイトの要件と技術的な能力に依存しています。 スケーラブルな既成のナビゲーションプロバイダーが必要な場合は、セキュリティ トリミングを無効化した管理ナビゲーションが適しています。

管理ナビゲーション オプションは構成を介して管理でき、コードのカスタマイズ ファイルは必要ないため、構造ナビゲーションよりはるかに高速です。 セキュリ ティトリミングを必要とし、カスタム マスター ページを使用する能力があり、SharePoint Online の既定のマスター ページで発生する変更に対する管理能力が組織にある場合、検索型オプションを使用するとより優れたユーザー エクスペリエンスを構築できる可能性があります。 より複雑な要件がある場合は、カスタム ナビゲーションプロバイダーが適している可能性があります。 構造ナビゲーションは非推奨です。

最後に、SharePoint では、SharePoint ハブ サイトのよりフラットなサイト階層とハブアンドスポーク モデルを活用して、モダンな SharePoint サイト アーキテクチャ用に追加のナビゲーション プロバイダーや機能を追加しています。 これにより、SharePoint 発行機能を必要としないシナリオを多数実現できるようになります。これらのナビゲーション構成は、SharePoint Online 内の拡張性と遅延に合わせて最適化されています。 これと同じ、SharePoint 発行サイトの全体的な構造をよりフラットな構造にして簡素化するという原則を適用した場合、多くの場合、全体的なパフォーマンスと拡張性の向上にも役立ちます。 これは、大量のサイト (サブ Web) を含む単一のサイト コレクションを使用するのではなく、それぞれはごく少数のサブサイト (サブ Web) しか含まないサイト コレクションを多数使用する方が優れたアプローチであることを意味します。


## <a name="using-managed-navigation-and-metadata-in-sharepoint-online"></a>SharePoint Online で管理ナビゲーションおよび管理されたメタデータを使用する

別の既成のオプションとして管理ナビゲーションがあり、このオプションを使用して構造ナビゲーションの機能のほとんどを再現できます。 管理されたメタデータの構成では、セキュリティ トリミングは有効にも無効にもできます。 構成でセキュリティ トリミングが無効化されている場合、管理ナビゲーションは、一定数のサーバー呼び出しを使用してすべてのナビゲーション リンクを読み込むので、比較的効率的です。 一方、セキュリティ トリミングを有効化した場合は管理ナビゲーションの利点が打ち消されるため、最適なパフォーマンスとスケーラビリティを実現するには、いずれかのカスタム ナビゲーション ソリューションを試すという選択の方が有効である可能性があります。

多くのサイトではセキュリティ トリミングは必要ありません。これは、サイトのすべてのユーザーのナビゲーション構造が多くの場合共通であるためです。 セキュリティ トリミングが無効になっていて、アクセス権を持たないユーザーもいるナビゲーションにリンクが追加された場合、リンクは表示されますが、アクセスが拒否されたというメッセージが表示されます。 コンテンツへの偶発的なアクセスが発生する危険はありません。

### <a name="how-to-implement-managed-navigation-and-the-results"></a>管理ナビゲーションと結果を実装する方法

管理ナビゲーションの詳細については、Docs.Microsoft.com にいくつかの記事が掲載されています。たとえば、「[SharePoint Server の管理ナビゲーションの概要](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation)」を参照してください。

管理ナビゲーションを実装するには、サイトのナビゲーション構造に対応する URL を使用して用語を設定します。 管理ナビゲーションは多くの場合、手動で監督することにより構造ナビゲーションと置き換えられます。 次に例を示します。

![SharePoint Online サイトの構造](media/SPONavOptionsListOfSites.png)

次の例は、管理ナビゲーションを使用した複雑なナビゲーションのパフォーマンスを示しています。

![管理ナビゲーションを使用した複雑なナビゲーションのパフォーマンス](media/SPONavOptionsComplexNavPerf.png)

常に管理ナビゲーションを使用すると、構造ナビゲーションのアプローチと比較してパフォーマンスが向上します。
  
## <a name="using-structural-navigation-in-sharepoint-online"></a>SharePoint Online で構造ナビゲーションを使用する

これは既定で使用される既成のナビゲーションで、最も単純なソリューションですが、その反面、パフォーマンスが大きく低下するデメリットがあります。 カスタマイズの必要がなく、非技術者のユーザーでもアイテムの追加、アイテムの非表示、ナビゲーションの管理を [設定] ページから簡単に実行できます。 ただし、これは管理ナビゲーションの場合も同様です。この理由から、管理および制御が同じく簡単に行え、パフォーマンスも向上する管理ナビゲーションを使用することをお勧めします。

![[サブサイトを表示する] が選択されている構造ナビゲーション](media/SPONavOptionsStructuredShowSubsites.png)
  
### <a name="turning-on-structural-navigation-in-sharepoint-online"></a>SharePoint Online で構造ナビゲーションを有効にする

標準の SharePoint Online ソリューションで構造ナビゲーションを使用し、サブサイトを表示するオプションに設定した場合のパフォーマンスへの影響を示します。 以下は、[**サイトの設定**] \> [**ナビゲーション**] ページの設定のスクリーンショットです。
  
![サブサイトを示すスクリーンショット](media/5b6a8841-34ed-4f61-b6d3-9d3e78d393e7.png)
  
### <a name="analyzing-structural-navigation-performance-in-sharepoint-online"></a>SharePoint Online で構造ナビゲーションのパフォーマンスを分析する

SharePoint のページのパフォーマンスを分析するには、Internet Explorer の F12 開発者ツールの [**ネットワーク**] タブを使用します。 
  
![F12 開発者ツールの [ネットワーク] タブを示すスクリーンショット](media/SPONavOptionsNetworks.png)
  
1. [**ネットワーク**] タブで、読み込み中の .aspx ページをクリックして、[**詳細**] タブをクリックします。<br/> ![[詳細] タブを示すスクリーンショット](media/ad85cefb-7bc5-4932-b29c-25f61b4ceeb2.png)<br/>
2. [**応答ヘッダー**] をクリックします。 <br/>![[詳細] タブのスクリーンショット](media/c47770ac-5b2b-4941-9830-c57565dec4cc.png)<br/>SharePoint は、その応答ヘッダー内で、有益な診断情報を返します。 
3. 最も便利な情報の 1 つは **SPRequestDuration** です。これは、サーバー上で要求の処理にかかった時間の値 (ミリ秒単位) です。 次のスクリーン ショットでは、構造ナビゲーションの [**サブサイトを表示する**] のチェックがオフになっています。 これは、グローバル ナビゲーションにはサイト コレクションのリンクのみがあることを意味します。<br/>![要求時間として負荷時間を示すスクリーンショット](media/3422b2e8-15ec-4bb9-ba86-0965b6b49b01.png)<br/>
4. **SPRequestDuration** キーの値は 245 ミリ秒です。 これは、要求を返すまでにかかった時間を表します。 サイトにあるナビゲーション アイテムが 1 つのみであるため、これは高負荷のナビゲーションがない場合の SharePoint Online のパフォーマンスに関する優れたベンチマークです。 次のスクリーン ショットは、サブサイトを追加した場合に、このキーにどう影響するかを示しています。<br/>![2,502 ミリ秒の要求時間を示すスクリーンショット](media/618ee4e9-2ffa-4a22-b638-fa77b72292b8.png)<br/>
  
サブサイトの追加により、この比較的単純なサンプルサイトでページ要求に返答するまでにかかる時間が大きく増加しました。 ナビゲーションのページなどの複雑なサイト階層や、その他の構成およびトポロジ オプションを使用する場合は、影響がさらに大きくなります。

## <a name="using-search-driven-client-side-scripting"></a>検索型のクライアント側スクリプトを使用する

検索を使用すると、継続的クロールによってバックグラウンドでビルドされたインデックスを活用できます。 検索結果が検索インデックスから取り込まれ、結果はセキュリティ トリミングされます。 通常、セキュリティ トリミングが必要な場合は、既成のナビゲーション プロバイダーより高速です。 構造ナビゲーションで検索を使用すると、特に複雑なサイト構造がある場合は、ページの読み込み時間が大幅に短縮します。 管理ナビゲーションに対するこの方法の主な利点は、セキュリティ トリミングの恩恵を受けられることです。

このアプローチには、カスタム マスター ページの作成、既成のナビゲーション コードのカスタム HTML への置き換えなどが含まれます。 ファイル `seattle.html` のナビゲーション コードを置き換えるには、次の例に示す手順を実行します。 この例では、`seattle.html`ファイルを開き、`id=”DeltaTopNavigation”` という要素全体をカスタム HTML コードで置き換えます。

### <a name="example-replace-the-out-of-the-box-navigation-code-in-a-master-page"></a>例: マスター ページの既成のナビゲーション コードを置き換える

1.  [サイト設定] ページに移動します。
2.  [**マスター ページ**] をクリックして、マスター ページ ギャラリーを開きます。
3.  ここから、ライブラリ内を移動してファイル `seattle.master` をダウンロードできます。
4.  テキスト エディターでコードを編集し、次のスクリーン ショットにあるコード ブロックを削除します。<br/>![示されたコードブロックを削除する](media/SPONavOptionsDeleteCodeBlock.png)<br/>
5. タグ `<SharePoint:AjaxDelta id=”DeltaTopNavigation”>` と `<\SharePoint:AjaxDelta>` の間のコードを削除し、次のスニペットに置き換えます。<br/>

```
<div id="loading">
  <!--Replace with path to loading image.-->
  <div style="background-image: url(''); height: 22px; width: 22px; ">
  </div>
</div>
<!-- Main Content-->
<div id="navContainer" style="display:none">
    <div data-bind="foreach: hierarchy" class="noindex ms-core-listMenu-horizontalBox">
        <a class="dynamic menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" data-bind="attr: { href: item.Url, title: item.Title }">
            <span class="menu-item-text" data-bind="text: item.Title">
            </span>
        </a>
        <ul id="menu" data-bind="foreach: $data.children" style="padding-left:20px">
            <li class="static dynamic-children level1">
                <a class="static dynamic-children menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" data-bind="attr: { href: item.Url, title: item.Title }">
               
                 <!-- ko if: children.length > 0-->
                    <span aria-haspopup="true" class="additional-background ms-navedit-flyoutArrow dynamic-children">
                        <span class="menu-item-text" data-bind="text: item.Title">
                        </span>
                    </span>
                <!-- /ko -->
                <!-- ko if: children.length == 0-->   
                    <span aria-haspopup="true" class="ms-navedit-flyoutArrow dynamic-children">
                        <span class="menu-item-text" data-bind="text: item.Title">
                        </span>
                    </span>
                <!-- /ko -->   
                </a>
               
                <!-- ko if: children.length > 0-->                                                       
                <ul id="menu"  data-bind="foreach: children;" class="dynamic  level2" >
                    <li class="dynamic level2">
                        <a class="dynamic menu-item ms-core-listMenu-item ms-displayInline  ms-navedit-linkNode" data-bind="attr: { href: item.Url, title: item.Title }">
         
          <!-- ko if: children.length > 0-->
          <span aria-haspopup="true" class="additional-background ms-navedit-flyoutArrow dynamic-children">
           <span class="menu-item-text" data-bind="text: item.Title">
           </span>
          </span>
           <!-- /ko -->
          <!-- ko if: children.length == 0-->
          <span aria-haspopup="true" class="ms-navedit-flyoutArrow dynamic-children">
           <span class="menu-item-text" data-bind="text: item.Title">
           </span>
          </span>                 
          <!-- /ko -->   
                        </a>
          <!-- ko if: children.length > 0-->
         <ul id="menu" data-bind="foreach: children;" class="dynamic level3" >
          <li class="dynamic level3">
           <a class="dynamic menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" data-bind="attr: { href: item.Url, title: item.Title }">
            <span class="menu-item-text" data-bind="text: item.Title">
            </span>
           </a>
          </li>
         </ul>
           <!-- /ko -->
                    </li>
                </ul>
                <!-- /ko -->
            </li>
        </ul>
    </div>
</div>
```
<br/>
6. 冒頭の読み込みイメージのアンカー タグの URL を、サイト コレクションの読み込みイメージへのリンクに置き換えます。 変更を加えたら、ファイルの名前を変更し、マスター ページ ギャラリーにアップロードします。 これにより、新しい .master ファイルが生成されます。<br/>
7. この HTML は、JavaScript のコードから返される検索結果によって入力される基本的なマークアップです。 次のスニペットに示すとおり、var root = “site collection URL” の値を変更するためにコードを編集する必要があります。<br/>

```
var root = “https://spperformance.sharepoint.com/sites/NavigationBySearch”;
```
<br/>
8. 結果は self.nodes 配列に割り当てられ、linq.js を使用してオブジェクトから階層が構築され、出力が配列 self.hierarchy に割り当てられます。 この配列は、HTML にバインドされているオブジェクトです。 これは、toggleView() 関数でセルフ オブジェクトを ko.applyBindings() 関数に渡すことにより実行されます。<br/>続いて、階層の配列が次の HTML にバインドされます。<br/>

```
<div data-bind=”foreach: hierarchy” class=”noindex ms-core-listMenu-horizontalBox”>
```

サブサイトのドロップダウン メニューを処理するために`mouseenter` および `mouseexit` のイベント ハンドラーがトップレベルのナビゲーションに追加されます。これは、`addEventsToElements()` 関数で実行されます。 

この複雑なナビゲーションの例では、ローカル キャッシュがない新しいページの読み込みにおいて、管理ナビゲーションのアプローチと似た結果を得るため、サーバーで費やした時間がベンチマークの構造ナビゲーションから短縮されたことを示しています。

### <a name="about-the-javascript-file"></a>JavaScript ファイルについて

JavaScript ファイルの全体は次のとおりです。

```
//Models and Namespaces
var SPOCustom = SPOCustom || {};
SPOCustom.Models = SPOCustom.Models || {}
SPOCustom.Models.NavigationNode = function () {

    this.Url = ko.observable("");
    this.Title = ko.observable("");
    this.Parent = ko.observable("");

};

var root = "https://spperformance.sharepoint.com/sites/NavigationBySearch";
var baseUrl = root + "/_api/search/query?querytext=";
var query = baseUrl + "'contentClass=\"STS_Web\"+path:" + root + "'&trimduplicates=false&rowlimit=300";

var baseRequest = {
    url: "",
    type: ""
};


//Parses a local object from JSON search result.
function getNavigationFromDto(dto) {
    var item = new SPOCustom.Models.NavigationNode();
    if (dto != undefined) {

        var webTemplate = getSearchResultsValue(dto.Cells.results, 'WebTemplate');

        if (webTemplate != "APP") {
            item.Title(getSearchResultsValue(dto.Cells.results, 'Title')); //Key = Title
            item.Url(getSearchResultsValue(dto.Cells.results, 'Path')); //Key = Path
            item.Parent(getSearchResultsValue(dto.Cells.results, 'ParentLink')); //Key = ParentLink
        }

    }
    return item;
}

function getSearchResultsValue(results, key) {

    for (i = 0; i < results.length; i++) {
        if (results[i].Key == key) {
            return results[i].Value;
        }
    }
    return null;
}

//Parse a local object from the serialized cache.
function getNavigationFromCache(dto) {
    var item = new SPOCustom.Models.NavigationNode();

    if (dto != undefined) {

        item.Title(dto.Title);
        item.Url(dto.Url);
        item.Parent(dto.Parent);
    }

    return item;
}

/* create a new OData request for JSON response */
function getRequest(endpoint) {
    var request = baseRequest;
    request.type = "GET";
    request.url = endpoint;
    request.headers = { ACCEPT: "application/json;odata=verbose" };
    return request;
};

/* Navigation Module*/
function NavigationViewModel() {
    "use strict";
    var self = this;
    self.nodes = ko.observableArray([]);
    self.hierarchy = ko.observableArray([]);;
    self.loadNavigatioNodes = function () {
        //Check local storage for cached navigation datasource.
        var fromStorage = localStorage["nodesCache"];
        if (false) {
            var cachedNodes = JSON.parse(localStorage["nodesCache"]);

            if (cachedNodes && timeStamp) {
                //Check for cache expiration. Currently set to 3 hrs.
                var now = new Date();
                var diff = now.getTime() - timeStamp;
                if (Math.round(diff / (1000 * 60 * 60)) < 3) {

                    //return from cache.
                    var cacheResults = [];
                    $.each(cachedNodes, function (i, item) {
                        var nodeitem = getNavigationFromCache(item, true);
                        cacheResults.push(nodeitem);
                    });

                    self.buildHierarchy(cacheResults);
                    self.toggleView();
                    addEventsToElements();
                    return;
                }
            }
        }
        //No cache hit, REST call required.
        self.queryRemoteInterface();
    };

    //Executes a REST call and builds the navigation hierarchy.
    self.queryRemoteInterface = function () {
        var oDataRequest = getRequest(query);
        $.ajax(oDataRequest).done(function (data) {
            var results = [];
            $.each(data.d.query.PrimaryQueryResult.RelevantResults.Table.Rows.results, function (i, item) {

                if (i == 0) {
                    //Add root element.
                    var rootItem = new SPOCustom.Models.NavigationNode();
                    rootItem.Title("Root");
                    rootItem.Url(root);
                    rootItem.Parent(null);
                    results.push(rootItem);
                }
                var navItem = getNavigationFromDto(item);
                results.push(navItem);
            });
            //Add to local cache
            localStorage["nodesCache"] = ko.toJSON(results);

            localStorage["nodesCachedAt"] = new Date().getTime();
            self.nodes(results);
            if (self.nodes().length > 0) {
                var unsortedArray = self.nodes();
                var sortedArray = unsortedArray.sort(self.sortObjectsInArray);

                self.buildHierarchy(sortedArray);
                self.toggleView();
                addEventsToElements();
            }
        }).fail(function () {
            //Handle error here!!
            $("#loading").hide();
            $("#error").show();
        });
    };
    self.toggleView = function () {
        var navContainer = document.getElementById("navContainer");
        ko.applyBindings(self, navContainer);
        $("#loading").hide();
        $("#navContainer").show();

    };
    //Uses linq.js to build the navigation tree.
    self.buildHierarchy = function (enumerable) {
        self.hierarchy(Enumerable.From(enumerable).ByHierarchy(function (d) {
            return d.Parent() == null;
        }, function (parent, child) {
            if (parent.Url() == null || child.Parent() == null)
                return false;
            return parent.Url().toUpperCase() == child.Parent().toUpperCase();
        }).ToArray());

        self.sortChildren(self.hierarchy()[0]);
    };


    self.sortChildren = function (parent) {

        // sjip processing if no children
        if (!parent || !parent.children || parent.children.length === 0) {
            return;
        }

        parent.children = parent.children.sort(self.sortObjectsInArray2);

        for (var i = 0; i < parent.children.length; i++) {
            var elem = parent.children[i];

            if (elem.children && elem.children.length > 0) {
                self.sortChildren(elem);
            }
        }
    };

    // ByHierarchy method breaks the sorting in chrome and firefix 
    // we need to resort  as ascending
    self.sortObjectsInArray2 = function (a, b) {
        if (a.item.Title() > b.item.Title())
            return 1;
        if (a.item.Title() < b.item.Title())
            return -1;
        return 0;
    };


    self.sortObjectsInArray = function (a, b) {
        if (a.Title() > b.Title())
            return -1;
        if (a.Title() < b.Title())
            return 1;
        return 0;
    }
}

//Loads the navigation on load and binds the event handlers for mouse interaction.
function InitCustomNav() {
    var viewModel = new NavigationViewModel();
    viewModel.loadNavigatioNodes();
}

function addEventsToElements() {
    //events.
      $("li.level1").mouseover(function () {
          var position = $(this).position();
          $(this).find("ul.level2").css({ width: 100, left: position.left + 10, top: 50 });
      })
   .mouseout(function () {
     $(this).find("ul.level2").css({  left: -99999, top: 0 });
   
    });
   
     $("li.level2").mouseover(function () {
          var position = $(this).position();
          console.log(JSON.stringify(position));
          $(this).find("ul.level3").css({ width: 100, left: position.left + 95, top:  position.top});
      })
   .mouseout(function () {
     $(this).find("ul.level3").css({  left: -99999, top: 0 });
    });
} _spBodyOnLoadFunctionNames.push("InitCustomNav");

``` 

上記の `jQuery $(document).ready` 関数のコードの概要を説明するために `viewModel object` が作成され、次にそのオブジェクトに対する `loadNavigationNodes()` 関数が呼び出されています。 この関数は、クライアント ブラウザーの HTML5 ローカル ストレージに格納されている以前に作成されたナビゲーション階層を読み込むか、`queryRemoteInterface()` 関数を呼び出します。

`QueryRemoteInterface()` は、スクリプトの前の方で定義されているクエリ パラメーターを使用する `getRequest()` 関数を使用して要求を作成し、次にサーバーからのデータを返します。 このデータは基本的に、さまざまなプロパティを持つデータ転送オブジェクトとして表されるサイト コレクション内のすべてのサイトの配列です。 

その後、このデータは、解析されて既に定義されている `SPO.Models.NavigationNode` オブジェクトになります。このオブジェクトは、`Knockout.js` を使用して観測可能なプロパティを作成します。このプロパティは、上で定義した HTML に値をバインディングするデータによって使用されます。 

オブジェクトは結果の配列に格納されます。 この配列は、Knockout によって解析されて JSON になり、将来ページを読み込む際のパフォーマンス向上のため、ローカル ブラウザー ストレージに格納されます。

### <a name="benefits-of-this-approach"></a>このアプローチの利点

[このアプローチ](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page)の主な利点の 1 つは、ナビゲーションが、HTML5 のローカルの記憶域を使用して、ユーザーによる次回のページの読み込みのため、ローカルに格納されることです。 構造ナビゲーション用に検索 API を使用することで、パフォーマンスが大きく向上します。ただし、この機能の実行とカスタマイズには技術的な能力が必要になります。 

[実装の例](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page)では、サイトは既成の構造ナビゲーションと同じ順序 (アルファベット順) に並べられています。 これとは異なる順序を使用する場合は、開発とメンテナンスがより複雑になります。 また、このアプローチでは、サポートされているマスター ページから逸脱する必要があります。 カスタム マスター ページの管理が行われない場合、サイトは Microsoft がマスター ページに対して加える更新と改善を利用できません。

[上記のコード](#about-the-javascript-file)には次のような依存関係があります。

- jQuery - https://jquery.com/
- KnockoutJS - https://knockoutjs.com/
- Linq.js - https://linqjs.codeplex.com/、または github.com/neuecc/linq.js

LinqJS の現在のバージョンには、上記のコードで使用されている ByHierarchy メソッドが含まれておらず、ナビゲーション コードが機能しなくなります。 これを解決するには、Linq.js ファイルの `Flatten: function ()` の行の前に次のメソッドを追加します。

```
ByHierarchy: function(firstLevel, connectBy, orderBy, ascending, parent) {
     ascending = ascending == undefined ? true : ascending;
     var orderMethod = ascending == true ? 'OrderBy' : 'OrderByDescending';
     var source = this;
     firstLevel = Utils.CreateLambda(firstLevel);
     connectBy = Utils.CreateLambda(connectBy);
     orderBy = Utils.CreateLambda(orderBy);
    
     //Initiate or increase level
     var level = parent === undefined ? 1 : parent.level + 1;

    return new Enumerable(function() {
         var enumerator;
         var index = 0;

        var createLevel = function() {
                 var obj = {
                     item: enumerator.Current(),
                     level : level
                 };
                 obj.children = Enumerable.From(source).ByHierarchy(firstLevel, connectBy, orderBy, ascending, obj);
                 if (orderBy !== undefined) {
                     obj.children = obj.children[orderMethod](function(d) {
                         return orderBy(d.item); //unwrap the actual item for sort to work
                     });
                 }
                 obj.children = obj.children.ToArray();
                 Enumerable.From(obj.children).ForEach(function(child) {
                     child.getParent = function() {
                         return obj;
                     };
                 });
                 return obj;
             };

        return new IEnumerator(

        function() {
             enumerator = source.GetEnumerator();
         }, function() {
             while (enumerator.MoveNext()) {
                 var returnArr;
                 if (!parent) {
                     if (firstLevel(enumerator.Current(), index++)) {
                         return this.Yield(createLevel());
                     }

                } else {
                     if (connectBy(parent.item, enumerator.Current(), index++)) {
                         return this.Yield(createLevel());
                     }
                 }
             }
             return false;
         }, function() {
             Utils.Dispose(enumerator);
         })
     });
 },

```
  
## <a name="related-topics"></a>関連項目

[SharePoint Server の管理ナビゲーションの概要](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation)

