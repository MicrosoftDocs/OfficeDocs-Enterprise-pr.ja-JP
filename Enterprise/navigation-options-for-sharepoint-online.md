---
title: SharePoint Online のナビゲーション オプション
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 4/7/2020
audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: adb92b80-b342-4ecb-99a1-da2a2b4782eb
description: この記事では、SharePoint Publishing が有効化されている SharePoint Online サイトのナビゲーション オプションについて説明します。 ナビゲーションの選択と構成は、SharePoint Online のサイトのパフォーマンスと拡張性に大きく影響します。 この記事は、従来のチーム サイトには適用されません。
ms.openlocfilehash: 410be307fca62c987baed39601e122717a6bebcc
ms.sourcegitcommit: b1042fa2d02f1bc74586751c542776325d3a170f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/07/2020
ms.locfileid: "43170655"
---
# <a name="navigation-options-for-sharepoint-online"></a>SharePoint Online のナビゲーション オプション

この記事では、SharePoint Publishing が有効化されている SharePoint Online サイトのナビゲーション オプションについて説明します。 ナビゲーションの選択と構成は、SharePoint Online のサイトのパフォーマンスとスケーラビリティに大きく影響します。 SharePoint 発行サイトテンプレートは、集中管理ポータルに必要な場合にのみ使用し、発行機能は特定のサイトに対してのみ有効にする必要があります。また、適切に使用しないと、必要な場合にのみ、パフォーマンスに影響することがあります。

>[!NOTE]
>メガメニュー、カスケードナビゲーション、ハブナビゲーションなどのモダン SharePoint ナビゲーションオプションを使用している場合、この記事はサイトに適用されません。 モダンな SharePoint サイトアーキテクチャは、よりフラット化されたサイト階層とハブアンドスポークモデルを活用します。 これにより、SharePoint 発行機能の使用を必要としない多くのシナリオを実現できます。

## <a name="overview"></a>概要

ナビゲーション プロバイダーの構成はサイト全体のパフォーマンスに大きな影響を与える可能性があるため、SharePoint サイトの要件を満たすように効果的に対応できるナビゲーション プロバイダーと構成を慎重に選択する必要があります。 2 つの既成のナビゲーション プロバイダーの他、ナビゲーションのカスタム実装が提供されています。

**サイトの構造ナビゲーションキャッシュを有効にする場合**、最初のオプションである[**構造ナビゲーション**](#using-structural-navigation-in-sharepoint-online)は、従来の Sharepoint サイトの sharepoint Online で推奨されるナビゲーションオプションです。 このナビゲーションプロバイダは、現在のサイトの下にあるナビゲーションアイテム、および必要に応じて現在のサイトとその兄弟を表示します。 これにより、セキュリティトリミングやサイト構造の列挙などの追加機能が提供されます。 キャッシュを無効にすると、パフォーマンスとスケーラビリティに悪影響を及ぼす可能性があり、調整の対象となる場合があります。

2番目のオプションである[**managed (メタデータ) ナビゲーション**](#using-managed-navigation-and-metadata-in-sharepoint-online)は、管理されたメタデータ用語セットを使用したナビゲーションアイテムを表します。 必要でない限り、セキュリティによるトリミングを無効にすることをお勧めします。 セキュリティ トリミングは既定によるセキュリティ保護としてこのナビゲーション プロバイダーで有効化されていますが、多くのサイトでは、サイトのすべてのユーザーに対して一貫性のあるナビゲーション要素を提供しているため、セキュリティ トリミングのオーバーヘッドは必要ありません。 推奨されているセキュリティトリミングを無効にする構成にした場合、このナビゲーション プロバイダーではサイト構造を列挙する必要がなく、パフォーマンスへの影響を許容範囲に抑えながら高い拡張性が提供されます。

既成のナビゲーション プロバイダーに加えて、多くのお客様が代替のカスタム ナビゲーション実装を正常に実装しています。 この記事の「[検索型クライアント側スクリプト](#using-search-driven-client-side-scripting)」を参照してください。
  
## <a name="pros-and-cons-of-sharepoint-online-navigation-options"></a>SharePoint Online ナビゲーション オプションの長所と短所

次の表は、各オプションの長所と短所をまとめたものです。

|構造ナビゲーション  |管理ナビゲーション  |検索型ナビゲーション  |カスタム ナビゲーション プロバイダー  |
|---------|---------|---------|---------|
|長所:<br/><br/>メンテナンスしやすい<br/>セキュリティ トリミングが行われる<br/>コンテンツが変更されたときに24時間以内に自動更新される<br/>     |長所:<br/><br/>メンテナンスしやすい<br/>|長所:<br/><br/>セキュリティ トリミングが行われる<br/>サイトが追加されると自動的に更新される<br/>読み込み時間が短く、ナビゲーション構造がローカルにキャッシュされている<br/>|長所:<br/><br/>使用可能なオプションの選択肢が広い<br/>キャッシュが正常に使用された場合、高速の読み込み<br/>多くのオプションが、応答性の高いページ デザインで適正に動作する<br/>|
|短所:<br/><br/>**キャッシュが無効な場合のパフォーマンスへの影響**<br/>調整の対象<br/>|短所:<br/><br/>サイト構造を反映するように自動的に更新されない<br/>**セキュリティによるトリミングが有効な場合**、またはナビゲーション構造が複雑な場合は、パフォーマンスに影響を与える<br/>|短所:<br/><br/>サイトの順序を簡単に変更できない<br/>マスター ページのカスタマイズが必要 (技術的なスキルが必要)<br/>|短所:<br/><br/>カスタム開発が必要<br/>外部データ ソース / 格納されたキャッシュが必要 (例: Azure)<br/>|

サイトに最適なオプションは、サイトの要件と技術的な能力に依存しています。 コンテンツが変更されたときに自動的に更新される、簡単に構成できるナビゲーションプロバイダが必要な場合は、[キャッシュが有効](https://support.office.com/article/structural-navigation-and-performance-f163053f-8eca-4b9c-b973-36b395093b43)な構造ナビゲーションを有効にすることをお勧めします。

>[!NOTE]
>Flatter の全体的なサイト構造を簡素化して、最新の SharePoint サイトと同じ原則を適用すると、階層構造ではない構造でパフォーマンスが向上し、最新の SharePoint サイトへの移行が簡単になります。 これは、数百のサイト (サブ web) を持つ単一のサイトコレクションを使用するのではなく、多くのサイトコレクションを非常に少数のサブサイト (サブ web) で使用するということです。

## <a name="analyzing-navigation-performance-in-sharepoint-online"></a>SharePoint Online でナビゲーションパフォーマンスを分析する

[Sharepoint 用ページ診断ツール](https://aka.ms/perftool)は、sharepoint Online モダンポータルと従来の発行サイトページの両方を分析する Microsoft Edge および Chrome ブラウザー用のブラウザー拡張機能です。 このツールは、SharePoint Online に対してのみ機能し、SharePoint システムページでは使用できません。

解析された各ページに対して、定義済みのルールセットに対してページがどのように表示されるかを示すレポートを生成し、テストの結果が基準値の範囲外にある場合に詳細情報を表示します。 SharePoint Online の管理者および設計者は、このツールを使用してパフォーマンス上の問題をトラブルシューティングして、新しいページが発行される前に最適化されるようにすることができます。

特に、 **Sprequestduration**は、SharePoint がページを処理するのにかかる時間です。 ヘビーナビゲーション (ナビゲーションにページを含めるなど)、複雑なサイト階層、およびその他の構成およびトポロジオプションは、長い期間に劇的に貢献します。

## <a name="using-structural-navigation-in-sharepoint-online"></a>SharePoint Online で構造ナビゲーションを使用する

これは既定で使用される既定のナビゲーションで、最も簡単なソリューションです。 カスタマイズの必要がなく、非技術者のユーザーでもアイテムの追加、アイテムの非表示、ナビゲーションの管理を [設定] ページから簡単に実行できます。 キャッシュを[有効にする](https://support.office.com/article/structural-navigation-and-performance-f163053f-8eca-4b9c-b973-36b395093b43)ことをお勧めします。それ以外の場合は、高価なパフォーマンスのトレードオフがあります。

### <a name="how-to-implement-structural-navigation-caching"></a>構造ナビゲーションキャッシュを実装する方法

[**サイト設定** > の**ルックアンドフィール** > **ナビゲーション**] で、グローバルナビゲーションまたは現在のナビゲーションのいずれかで構造ナビゲーションが選択されているかどうかを検証できます。 [**ページの表示]** を選択すると、パフォーマンスに悪影響を与えます。

![[サブサイトを表示する] が選択されている構造ナビゲーション](media/SPONavOptionsStructuredShowSubsites.png)

キャッシュは、サイトコレクションレベルおよびサイトレベルで有効または無効にできます。既定では、両方に対して有効になっています。 サイトコレクションレベルで有効にするには、サイト**設定** > **サイトコレクション管理** > **サイトコレクションナビゲーション**で、[**キャッシュを有効にする**] のチェックボックスをオンにします。

![サイトレベルでキャッシュを有効にする](media/structural-nav/structural-nav-caching-site-coll.png)

サイトレベルで有効にするには、[**サイトの設定** > ]**ナビゲーション**で、[**キャッシュを有効**にする] のチェックボックスをオンにします。

![サイトレベルでキャッシュを有効にする](media/structural-nav/structural-nav-caching-site.png)

## <a name="using-managed-navigation-and-metadata-in-sharepoint-online"></a>SharePoint Online で管理ナビゲーションおよび管理されたメタデータを使用する

別の既成のオプションとして管理ナビゲーションがあり、このオプションを使用して構造ナビゲーションの機能のほとんどを再現できます。 管理されたメタデータの構成では、セキュリティ トリミングは有効にも無効にもできます。 構成でセキュリティ トリミングが無効化されている場合、管理ナビゲーションは、一定数のサーバー呼び出しを使用してすべてのナビゲーション リンクを読み込むので、比較的効率的です。 ただし、セキュリティによるトリミングを有効にすると、管理ナビゲーションのパフォーマンス上の利点の一部を否定できます。

セキュリティによるトリミングを有効にする必要がある場合は、次のことをお勧めします。

- すべてのフレンドリ URL のリンクを簡単なリンクに更新する
- フレンドリ Url として必要なセキュリティトリミングノードを追加する
- ナビゲーションアイテムの数を100以下に制限し、深さが3レベルを超えないようにする

多くのサイトではセキュリティ トリミングは必要ありません。これは、サイトのすべてのユーザーのナビゲーション構造が多くの場合共通であるためです。 セキュリティ トリミングが無効になっていて、アクセス権を持たないユーザーもいるナビゲーションにリンクが追加された場合、リンクは表示されますが、アクセスが拒否されたというメッセージが表示されます。 コンテンツへの偶発的なアクセスが発生する危険はありません。

### <a name="how-to-implement-managed-navigation-and-the-results"></a>管理ナビゲーションと結果を実装する方法

管理ナビゲーションの詳細については、docs.microsoft.com にいくつかの記事があります。 例については、「 [SharePoint Server の管理ナビゲーションの概要](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation)」を参照してください。

管理ナビゲーションを実装するために、サイトのナビゲーション構造に対応する Url を使用して用語を設定します。 管理ナビゲーションは多くの場合、手動で監督することにより構造ナビゲーションと置き換えられます。 次に例を示します。

![SharePoint Online サイトの構造](media/SPONavOptionsListOfSites.png))

## <a name="using-search-driven-client-side-scripting"></a>検索型のクライアント側スクリプトを使用する

カスタム ナビゲーション実装の一般的なクラスの 1 つとして、ナビゲーション ノードのローカル キャッシュを格納するクライアント レンダリングによるデザイン パターンがあります。

これらのナビゲーション プロバイダーには、いくつかの大きな利点があります。

- これらのナビゲーション プロバイダーは通常、応答性の高いページ デザインに適しています。
- リソース コストをかけずにレンダリングできるため、拡張性が高く、高性能です (また、タイムアウト後にバックグラウンドでの更新が可能です)。
- これらのナビゲーション プロバイダーは、単純な静的構成からさまざまな動的データ プロバイダーまでを含む、さまざまな方法を使用してナビゲーション データを取得できます。

データ プロバイダーの例として、ナビゲーション ノードの列挙とセキュリティ トリミングの効率的な処理が可能な**検索型ナビゲーション**を使用する方法があります。

**カスタム ナビゲーション プロバイダー**を構築するための一般的なオプションは他にもあります。 カスタム ナビゲーション プロバイダーを構築する方法に関するより詳細なガイダンスついては、「[SharePoint Online ポータル用のナビゲーション ソリューション](https://docs.microsoft.com/sharepoint/dev/solution-guidance/portal-navigation)」を参照してください。

検索を使用すると、継続的クロールによってバックグラウンドでビルドされたインデックスを活用できます。 検索結果が検索インデックスから取り込まれ、結果はセキュリティ トリミングされます。 通常、セキュリティ トリミングが必要な場合は、既成のナビゲーション プロバイダーより高速です。 構造ナビゲーションで検索を使用すると、特に複雑なサイト構造がある場合は、ページの読み込み時間が大幅に短縮します。 管理ナビゲーションに対するこの方法の主な利点は、セキュリティ トリミングの恩恵を受けられることです。

このアプローチには、カスタム マスター ページの作成、既成のナビゲーション コードのカスタム HTML への置き換えなどが含まれます。 ファイル `seattle.html` のナビゲーション コードを置き換えるには、次の例に示す手順を実行します。 この例では、`seattle.html`ファイルを開き、`id="DeltaTopNavigation"` という要素全体をカスタム HTML コードで置き換えます。

### <a name="example-replace-the-out-of-the-box-navigation-code-in-a-master-page"></a>例: マスター ページの既成のナビゲーション コードを置き換える

1. [サイト設定] ページに移動します。
2. [**マスター ページ**] をクリックして、マスター ページ ギャラリーを開きます。
3. ここから、ライブラリ内を移動してファイル `seattle.master` をダウンロードできます。
4. テキスト エディターでコードを編集し、次のスクリーン ショットにあるコード ブロックを削除します。<br/>![示されたコードブロックを削除する](media/SPONavOptionsDeleteCodeBlock.png)<br/>
5. タグ `<SharePoint:AjaxDelta id="DeltaTopNavigation">` と `<\SharePoint:AjaxDelta>` の間のコードを削除し、次のスニペットに置き換えます。<br/>

```javascript
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
7. この HTML は、JavaScript のコードから返される検索結果によって入力される基本的なマークアップです。 次のスニペットで示すように、var root = "site collection URL" の値を変更するコードを編集する必要があります。<br/>

```javascript
var root = "https://spperformance.sharepoint.com/sites/NavigationBySearch";
```

<br/>
8. 結果は self.nodes 配列に割り当てられ、linq.js を使用してオブジェクトから階層が構築され、出力が配列 self.hierarchy に割り当てられます。 この配列は、HTML にバインドされているオブジェクトです。 これは、toggleView() 関数でセルフ オブジェクトを ko.applyBindings() 関数に渡すことにより実行されます。<br/>続いて、階層の配列が次の HTML にバインドされます。<br/>

```javascript
<div data-bind="foreach: hierarchy" class="noindex ms-core-listMenu-horizontalBox">
```

サブサイトのドロップダウン メニューを処理するために`mouseenter` および `mouseexit` のイベント ハンドラーがトップレベルのナビゲーションに追加されます。これは、`addEventsToElements()` 関数で実行されます。 

この複雑なナビゲーションの例では、ローカル キャッシュがない新しいページの読み込みにおいて、管理ナビゲーションのアプローチと似た結果を得るため、サーバーで費やした時間がベンチマークの構造ナビゲーションから短縮されたことを示しています。

### <a name="about-the-javascript-file"></a>JavaScript ファイルについて

>[!NOTE]
>カスタム JavaScript を使用する場合は、パブリック CDN が有効であり、ファイルが CDN の場所にあることを確認してください。

JavaScript ファイルの全体は次のとおりです。

```javascript
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

    // ByHierarchy method breaks the sorting in chrome and firefox
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

```javascript
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

[構造ナビゲーションのキャッシュとパフォーマンス](https://support.office.com/article/structural-navigation-and-performance-f163053f-8eca-4b9c-b973-36b395093b43)
