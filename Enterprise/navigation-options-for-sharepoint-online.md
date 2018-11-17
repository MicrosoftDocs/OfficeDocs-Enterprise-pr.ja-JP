---
title: SharePoint Online のナビゲーション オプション
ms.author: krowley
author: kccross
manager: laurawi
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: adb92b80-b342-4ecb-99a1-da2a2b4782eb
description: SharePoint Online で有効にし、SharePoint 発行のナビゲーション オプションのサイトについて説明します。選択とナビゲーションの構成は、パフォーマンスとスケーラビリティは、SharePoint Online サイトを大幅に影響します。
ms.openlocfilehash: 5a190ca643c20b6644ca1eecdac2a4a2e281a09e
ms.sourcegitcommit: 45633b7034ee98d0cd833db9743f283b638237f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "26547179"
---
# <a name="navigation-options-for-sharepoint-online"></a>SharePoint Online のナビゲーション オプション

SharePoint Online で有効にし、SharePoint 発行のナビゲーション オプションのサイトについて説明します。選択とナビゲーションの構成は、パフォーマンスとスケーラビリティは、SharePoint Online サイトを大幅に影響します。

## <a name="overview"></a>概要

ナビゲーション プロバイダーの構成は、サイト全体のパフォーマンスに大きく影響し、SharePoint サイトの要件に効果的にスケーリングするための構成とナビゲーション プロバイダーを選択するのには注意を払う必要があります。カスタム ナビゲーションの実装と同様に、2 つのボックスのナビゲーション プロバイダーがあります。

最初のオプションでは、[**マネージ (メタデータ) のナビゲーション**](#using-managed-navigation-and-metadata-in-sharepoint-online)をお勧めし、SharePoint online は既定のオプションの 1 つただし、必要な場合を除き、セキュリティ トリミングが無効にするをお勧めします。このナビゲーション プロバイダーのセキュリティで保護された既定の設定としてセキュリティ トリミングが有効になっています。ただし、多くのサイトには、セキュリティ トリミングのナビゲーション要素が多くの場合は、サイトのすべてのユーザーに対して一貫したためのオーバーヘッドは不要です。セキュリティ トリミングを無効にするのには推奨される構成、このナビゲーション プロバイダー サイトの構造体を列挙する必要はなく、、許容可能なパフォーマンスへの影響、拡張性の高い。

2 番目オプション、[**構造的なナビゲーション**](#using-structural-navigation-in-sharepoint-online)では、 **SharePoint Online のナビゲーションの推奨されるオプションではないのです**。このナビゲーション プロバイダーは、設置型のトポロジには、SharePoint Online でのサポートが限られているために設計されました。いくつか追加の機能とその他のナビゲーション オプションのセットが用意されています、セキュリティによるトリミングとサイト構造の列挙型を含む、これらの機能はコストがかかるサーバーに過度な呼び出しと影響のスケーラビリティとパフォーマンスの使用されている場合。Structed のナビゲーションを使用して、過剰なリソースを消費するサイトは、調整される場合があります。

だけでなく、標準のナビゲーション プロバイダーでは、多くのお客様が別のユーザー設定のナビゲーションの実装を実装しました。カスタム ナビゲーションの実装の 1 つの一般的なクラスでは、ナビゲーション ノードのローカル キャッシュを格納するクライアントに表示されるデザイン パターンを採用します。(参照**[検索ベースのクライアント側のスクリプト](#using-search-driven-client-side-scripting)** の「)。

これらのナビゲーション プロバイダーには、いくつかの重要な利点があります。 
- 一般に応答性の高いページ デザインでうまく動作します。
- 非常にスケーラブルな高性能なレンダリングされることができますのでとしないリソースのコスト (タイムアウトの後、バック グラウンドで更新)。 
- ナビゲーション プロバイダーは、単純な静的な構成からさまざまな動的なデータ プロバイダーに至るまで、さまざまな方法を使用してナビゲーション データを取得できます。 

データ プロバイダーの例では、**検索方式のナビゲーション**、ナビゲーション ノードを列挙して、セキュリティ トリミングを効率的に処理の柔軟性を許可するを使用します。 

**カスタム ナビゲーション プロバイダー**を構築する一般的なその他のオプションがあります。カスタム ナビゲーション プロバイダーの構築のための[SharePoint Online ポータルのナビゲーション ソリューション](https://docs.microsoft.com/sharepoint/dev/solution-guidance/portal-navigation)を参照してください。
  
## <a name="pros-and-cons-of-sharepoint-online-navigation-options"></a>ナビゲーション オプションの長所と SharePoint Online の短所

次の表は、長所と短所の各オプションをまとめたものです。 


|管理ナビゲーション  |構造ナビゲーション  |検索駆動型ナビゲーション  |カスタム ナビゲーション プロバイダー  |
|---------|---------|---------|---------|
|長所:<br/><br/>メンテナンスしやすい<br/>推奨オプション<br/>     |長所:<br/><br/>構成しやすい<br/>セキュリティによるトリミング<br/>コンテンツが追加されると自動的に更新されます。<br/>|長所:<br/><br/>セキュリティによるトリミング<br/>サイトが追加されると自動的に更新する<br/>読み込み時間が短く、ナビゲーション構造がローカルにキャッシュされている<br/>|長所:<br/><br/>使用可能なオプションの選択の幅<br/>正しく使用されてキャッシュする場合の高速読み込み<br/>多くのオプションで問題なく動作応答性の高いページ デザイン<br/>|
|短所:<br/><br/>サイト構造を反映するように自動的に更新されない<br/>セキュリティ トリミングが有効になっている場合は、パフォーマンスに与える影響<br/>|短所:<br/><br/>**非推奨**<br/>**パフォーマンスに与える影響と拡張性**<br/>**調整の対象となります。**<br/>|短所:<br/><br/>サイトを簡単に並べ替えられない<br/>マスター ページのカスタマイズが必要 (技術的なスキルが必要)<br/>|短所:<br/><br/>カスタム開発が必要<br/>外部データ ソース キャッシュの保存が必要なと Azure など<br/>|

サイトの最適なオプションと技術的な機能をサイトの要件に依存します。スケーラブルな標準のナビゲーション プロバイダーを設定する場合、セキュリティ トリミングが無効になっていると、管理ナビゲーションは非常に良いオプションです。 

管理ナビゲーションのオプションを維持できる構成では、コードのカスタマイズ ファイルは関与しませんし、構造的なナビゲーションよりも大幅に高速ですが。カスタム マスター ページを使用しても問題は、セキュリティによるトリミングを必要として、SharePoint Online の既定のマスター ページで発生する変更内容を維持するために組織の一部の機能がある、[検索ベース] オプションがありますより良いユーザー エクスペリエンスです。複雑な要件がある場合、カスタム ナビゲーション プロバイダー可能性があります、最適な選択肢です。構造のナビゲーションはお勧めしません。

最後に、SharePoint が追加のナビゲーション プロバイダーと統合された複数のサイト階層とハブ サイトのハブ アンド スポーク モデルを活用し最新の SharePoint サイトのアーキテクチャの機能を追加することに注意する重要です。これにより、さまざまなシナリオを実現するのには SharePoint 発行機能の使用を必要としないし、これらのナビゲーション構成は、拡張性と SharePoint Online 内での待機時間を最適化されました。フラットな構造では、SharePoint 発行サイトの全体的な構造を簡略化の同じ原則を適用する全体的なパフォーマンスでは、多くの場合に注意してくださいし、も拡大または縮小します。つまり単一のサイト コレクション数百のサイト (サブ) の代わりに、適切なアプローチが非常にいくつかサブサイト (サブ web) の多くのサイト コレクションにします。


## <a name="using-managed-navigation-and-metadata-in-sharepoint-online"></a>SharePoint Online のナビゲーションを管理し、メタデータを使用します。

管理ナビゲーションは、構造的なナビゲーションと同じ機能のほとんどを再作成に使用できるもう 1 つのボックスのオプションです。管理されたメタデータは、セキュリティ トリミングを有効または無効にして構成できます。セキュリティ トリミングが無効に設定されている場合、管理ナビゲーションは非常に効率的なサーバー呼び出しの数が一定のすべてのナビゲーション リンクが読み込まれます。ただし、セキュリティ トリミングを有効にすると、ナビゲーションの管理の利点の一部を無効にし、最適なパフォーマンスとスケーラビリティのカスタム ナビゲーション ソリューションのいずれかを確認していただくことがあります。

多くのサイトでは、ナビゲーション構造は、サイトのすべてのユーザーに対して一貫性のある、多くの場合、セキュリティ トリミングは必要ありません。セキュリティ トリミングが無効になっているし、すべてのユーザー アクセス権を持つナビゲーションにリンクを追加、リンクは表示されますが、アクセス拒否のメッセージに 。コンテンツへの偶発的なアクセスのリスクはありません。

### <a name="how-to-implement-managed-navigation-and-the-results"></a>管理ナビゲーションと結果を実装する方法

上にあるいくつかの記事 Docs.Microsoft.com、ナビゲーションの管理の詳細については、 [SharePoint サーバーの管理ナビゲーションの概要](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation)を参照してください。

管理ナビゲーションを実装するために条件を設定する Url を持つサイトのナビゲーション構造に対応します。管理ナビゲーションでも、多くの場合、構造的なナビゲーションを置き換える curated 手動でことができます。例えば：

![SharePoint Online サイトの構造](media/SPONavOptionsListOfSites.png)

次の例は、管理ナビゲーションを使用した複雑なナビゲーションのパフォーマンスを示しています。

![管理ナビゲーションを使用して、複雑なナビゲーションのパフォーマンス](media/SPONavOptionsComplexNavPerf.png)

一貫して管理されたナビゲーションを使用すると、ナビゲーションの構造的なアプローチと比較してパフォーマンスが向上します。
  
## <a name="using-structural-navigation-in-sharepoint-online"></a>SharePoint Online で構造ナビゲーションを使用する

これは、既定で使用される、標準のナビゲーションと最も簡単なソリューションが、コスト パフォーマンスのトレードオフが。カスタマイズする必要がないと非技術的なユーザーことができますも簡単に項目を追加、アイテムを非表示しナビゲーションの設定] ページから管理します。ただしもパフォーマンスの向上することも簡単に管理および制御にもと管理のナビゲーションとナビゲーションの管理を使用することを推奨するための true です。

![構造のナビゲーションを表示するサブサイトが選択されています。](media/SPONavOptionsStructuredShowSubsites.png)
  
### <a name="turning-on-structural-navigation-in-sharepoint-online"></a>SharePoint Online で構造ナビゲーションを有効にする

構造のナビゲーションと表示する場合は、標準的な SharePoint Online ソリューションのパフォーマンスでのオプションのサブサイトを説明するために有効にします。[**サイトの設定**] ページの設定のスクリーン ショットを次に示します\>**ナビゲーション**します。
  
![サブサイトが表示されているスクリーンショット](media/5b6a8841-34ed-4f61-b6d3-9d3e78d393e7.png)
  
### <a name="analyzing-structural-navigation-performance-in-sharepoint-online"></a>SharePoint Online で構造ナビゲーションのパフォーマンスを分析する

SharePoint ページのパフォーマンスを分析するには、Internet Explorer で、F12 開発者ツールの [**ネットワーク**] タブを使用します。 
  
![F12 開発者ツールの [ネットワーク] タブが表示されているスクリーンショット](media/SPONavOptionsNetworks.png)
  
1. **[ネットワーク]** タブで、読み込まれている .aspx ページ、**[詳細]** タブの順にクリックします。<br/> ![[詳細] タブが表示されているスクリーンショット](media/ad85cefb-7bc5-4932-b29c-25f61b4ceeb2.png)<br/>
2. **[応答ヘッダー]** をクリックします。 <br/>![[詳細] タブのスクリーンショット](media/c47770ac-5b2b-4941-9830-c57565dec4cc.png)<br/>SharePoint では、その応答のヘッダーにいくつかの有益な診断情報を返します。 
3. 要求でサーバー上のプロセスにかかる時間 (ミリ秒単位) の値である**SPRequestDuration**は、最も有用な情報の 1 つ。次のスクリーン ショットで**サブサイトを表示する**ナビゲーション構造のチェックはありません。これは、グローバル ナビゲーションにサイト コレクションのリンクがあることを意味します。<br/>![要求時間として負荷時間が表示されているスクリーンショット](media/3422b2e8-15ec-4bb9-ba86-0965b6b49b01.png)<br/>
4. **SPRequestDuration**キーには、245 のミリ秒単位の値があります。これは、要求を取得するにかかった時間を表します。サイトのナビゲーション アイテムを 1 つだけなので、これは、SharePoint Online を実行する方法なく大量のナビゲーションのための良いベンチマークです。次のスクリーン ショットでは、サブサイトに追加すると、このキーにどのように影響する方法を示します。<br/>![2,502 ミリ秒の要求時間が表示されているスクリーンショット](media/618ee4e9-2ffa-4a22-b638-fa77b72292b8.png)<br/>
  
サブサイトを追加するこの比較的簡単なサンプル サイトのページ要求を返すまでの時間が大幅に増加します。ページのナビゲーション、および他の構成とトポロジ オプションを含む、複雑なサイトの階層では、この影響は、さらに大幅に向上します。

## <a name="using-search-driven-client-side-scripting"></a>検索駆動のクライアント側スクリプトを使用する

検索の使用継続的なクロールを使用してバック グラウンドで組み込まれているインデックスを活用できます。検索結果が検索インデックスから引き出され、結果は、セキュリティ トリミングします。セキュリティによるトリミングが必要な場合、標準のナビゲーション プロバイダーよりも一般に高速です。構造を移動するための検索を使用すると、特に、複雑なサイトの構造がある場合を高速化ページの読み込み時間を大幅。このナビゲーションの管理上の主な利点は、セキュリティによるトリミングを享受することです。

このアプローチには、カスタム マスター ページを作成して、html 形式のカスタムのボックスのナビゲーション コードを置き換えることが含まれます。この手順でファイル内のナビゲーションのコードを置換する例を次に記載されている`seattle.html`。この例では開く、`seattle.html`ファイルし、全体の要素を置換`id=”DeltaTopNavigation”`カスタム HTML コードとします。

### <a name="example-replace-the-out-of-the-box-navigation-code-in-a-master-page"></a>例: マスター ページで、標準のナビゲーション コードを置換します。

1.  [サイト設定] ページに移動します。
2.  **[マスター ページ]** をクリックして、マスター ページ ギャラリーを開きます。
3.  ここから、ライブラリ内を移動してファイルをダウンロード`seattle.master`。
4.  テキスト エディターでコードを編集し、次のスクリーン ショットにあるコード ブロックを削除します。<br/>![表示されているコード ブロックを削除します。](media/SPONavOptionsDeleteCodeBlock.png)<br/>
5. 間のコードを削除する、`<SharePoint:AjaxDelta id=”DeltaTopNavigation”>`と`<\SharePoint:AjaxDelta>`タグし、次のスニペットに置き換えます。<br/>

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
6. 読み込まれる URL を交換してイメージを読み込み、サイト コレクションのイメージへのリンクで、最初にアンカー タグです。変更を行った後は、ファイルの名前を変更し、マスター ページ ギャラリーにアップロードしています。新しい .master ファイルが生成されます。<br/>
7. この HTML は、JavaScript コードから返された検索結果が表示されますが、基本的なマークアップです。ルートの var の値を変更するコードを編集する必要があります。 次のコード例に示すように"サイト コレクションの URL"を = します。<br/>

```
var root = “https://spperformance.sharepoint.com/sites/NavigationBySearch”;
```
<br/>
8. 結果は、self.nodes 配列に割り当てられているし、linq.js は、配列 self.hierarchy への出力の割り当てを使用してオブジェクト階層を構築します。この配列は、HTML にバインドされているオブジェクトです。Self オブジェクトを ko.applyBinding() 関数に渡すことによって toggleView() 関数の中でこれです。<br/>これは、し、次の HTML にバインドするのには階層構造の配列を発生します。<br/>

```
<div data-bind=”foreach: hierarchy” class=”noindex ms-core-listMenu-horizontalBox”>
```

イベント ハンドラーで`mouseenter`と`mouseexit`のサブサイトのドロップ ダウン メニューを処理するために最上位レベルのナビゲーションに追加されます、`addEventsToElements()`関数です。

この複雑なナビゲーションの例では、管理ナビゲーションのアプローチと同様の結果を取得するベンチマークの構造的なナビゲーションからサーバーに費やす時間が削減された番組をローカル キャッシュに新しいページを読み込みます。

### <a name="about-the-javascript-file"></a>JavaScript ファイルについて.

JavaScript ファイル全体は次のとおりです。

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

上記のコードを要約する、`jQuery $(document).ready`関数がありますが、`viewModel object`を作成し、`loadNavigationNodes()`オブジェクトに対して関数が呼び出されます。この関数はクライアントのブラウザーの HTML5 のローカル ストレージに格納されている以前にビルドされたナビゲーション階層を読み込みますか、または関数を呼び出し、 `queryRemoteInterface()`。

`QueryRemoteInterface()`ビルドの要求を使用して、 `getRequest()` 、クエリ パラメーターを持つ関数を選択し、スクリプトの前半で定義されているサーバーからデータを返します。このデータは、基本的にはさまざまなプロパティを使用してデータ転送オブジェクトとして表されるサイト コレクション内のすべてのサイトの配列です。 

このデータを解析し、以前に定義したに`SPO.Models.NavigationNode`を使用するオブジェクト`Knockout.js`で値のデータ バインディングの前に定義した HTML を使用するための観察可能なプロパティを作成します。 

オブジェクトは、結果の配列に出力されます。この配列はノックアウトを使用して JSON を解析し、将来のページの読み込みのパフォーマンスを向上させるブラウザーのローカル ストレージに格納されています。

### <a name="benefits-of-this-approach"></a>このアプローチのメリット

[このアプローチ](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page)の主な利点の 1 つでは、HTML5 のローカル ストレージを使用すると、ナビゲーション格納されているローカル ユーザーのページを読み込み、次にします。構造的なナビゲーションの検索 API を使用する主要なパフォーマンスの向上が得します。ただし、実行し、この機能をカスタマイズするいくつかの技術的な能力を要する。 

[実装の例](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page)では、サイトをボックスの構造上のナビゲーションと同じように順序付けします。アルファベット順です。次の順序とは異なる場合は、開発および保守するより複雑ながあります。また、このアプローチには、サポートされているマスター ページから逸脱する必要があります。独自のマスター ページが維持されない場合、サイトに更新され、マイクロソフトでは、マスター ページに、強化された機能です。

[コードの上](#about-the-javascript-file)には、次の依存関係を持ちます。

- jQueryhttp://jquery.com/
- KnockoutJS-http://knockoutjs.com/
- Linq.js - http://linqjs.codeplex.com/、または github.com/neuecc/linq.js

LinqJS の現在のバージョンでは、上記のコードで使用されている ByHierarchy メソッドが含まれていないと、ナビゲーション コードが破損します。この問題を解決するのには、行の前に Linq.js ファイルに次のメソッドを追加します`Flatten: function ()`。

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

