---
title: SharePoint Online のナビゲーション オプション
ms.author: krowley
author: kccross
manager: laurawi
audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: adb92b80-b342-4ecb-99a1-da2a2b4782eb
description: この記事では、sharepoint Online で SharePoint の発行が有効になっているナビゲーションオプションサイトについて説明します。 ナビゲーションの選択と構成は、SharePoint Online のサイトのパフォーマンスとスケーラビリティに大きく影響します。
ms.openlocfilehash: 9bf2010000f14b173b63574fab4ee77cb772b3f4
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069943"
---
# <a name="navigation-options-for-sharepoint-online"></a>SharePoint Online のナビゲーション オプション

この記事では、sharepoint Online で SharePoint の発行が有効になっているナビゲーションオプションサイトについて説明します。 ナビゲーションの選択と構成は、SharePoint Online のサイトのパフォーマンスとスケーラビリティに大きく影響します。

## <a name="overview"></a>概要

ナビゲーションプロバイダーの構成は、サイト全体のパフォーマンスに大きな影響を与える可能性があります。また、SharePoint サイトの要件を効果的に拡大できるようにするナビゲーションプロバイダーと構成を選択するには、慎重に検討する必要があります。 すぐに使えるナビゲーションプロバイダー、およびカスタムナビゲーションの実装は、2つあります。

最初のオプションである [ [**Managed (Metadata)] ナビゲーション**](#using-managed-navigation-and-metadata-in-sharepoint-online)は推奨されており、SharePoint Online の既定のオプションの1つです。ただし、セキュリティによるトリミングは必要でない限り無効にすることをお勧めします。 セキュリティによるトリミングは、このナビゲーションプロバイダの既定の設定では有効になっています。ただし、多くのサイトでは、サイトのすべてのユーザーに対してナビゲーション要素の一貫性が保たれるため、セキュリティによるトリミングのオーバーヘッドが必要になることはありません。 セキュリティによるトリミングを無効にするために推奨される構成を使用すると、このナビゲーションプロバイダーはサイト構造の列挙を必要とせず、パフォーマンスへの影響が許容される高い拡張性を備えています。

2番目のオプションである[**構造ナビゲーション**](#using-structural-navigation-in-sharepoint-online)**は、SharePoint Online では推奨されていないナビゲーションオプションではありません**。 このナビゲーションプロバイダーは、オンプレミスのトポロジ向けに設計されており、SharePoint Online でのサポートに制限があります。 他のナビゲーションオプションに加えて、その他の機能のセットが提供されていますが、これらの機能 (セキュリティトリミングやサイト構造の列挙を含む) には、サーバー呼び出しのコストがかかり、使用時のスケーラビリティとパフォーマンスに影響を与えるものがあります。 過剰なリソースを消費する structed ナビゲーションを使用しているサイトは、調整の対象となる場合があります。

すぐに利用できるナビゲーションプロバイダーに加えて、多くのお客様は、代替のカスタムナビゲーション実装を適切に実装しています。 カスタムナビゲーション実装の一般的なクラスの1つとして、ナビゲーションノードのローカルキャッシュを格納するクライアントレンダリングの設計パターンがあります。 (この記事の「**[検索型クライアント側スクリプト](#using-search-driven-client-side-scripting)**」を参照してください)。

これらのナビゲーションプロバイダーには、主にいくつかの利点があります。 
- 通常は、応答性の高いページデザインに対して適切に動作します。
- リソースコストを使用せずにレンダリングでき、タイムアウト後にバックグラウンドで更新されるので、これらは非常にスケーラブルでパフォーマンスが向上します。 
- これらのナビゲーションプロバイダーは、単純な静的構成からさまざまな動的データプロバイダーまでのさまざまな戦略を使用してナビゲーションデータを取得できます。 

データプロバイダーの例としては、**検索型ナビゲーション**を使用して、ナビゲーションノードをより柔軟に列挙し、セキュリティによるトリミングを効率的に処理する方法があります。 

**カスタムナビゲーションプロバイダー**を構築するには、他にも一般的なオプションがあります。 カスタムナビゲーションプロバイダーを構築する方法については、「 [SharePoint Online ポータルのナビゲーションソリューション](https://docs.microsoft.com/sharepoint/dev/solution-guidance/portal-navigation)」を参照してください。
  
## <a name="pros-and-cons-of-sharepoint-online-navigation-options"></a>SharePoint Online ナビゲーションオプションの長所と短所

次の表に、各オプションの長所と短所の概要を示します。 


|管理ナビゲーション  |構造ナビゲーション  |検索型ナビゲーション  |カスタムナビゲーションプロバイダー  |
|---------|---------|---------|---------|
|専門<br/><br/>保守が容易<br/>推奨されるオプション<br/>     |専門<br/><br/>構成が容易<br/>セキュリティによるトリミング<br/>コンテンツが追加されたときに自動的に更新する<br/>|専門<br/><br/>セキュリティによるトリミング<br/>サイトが追加されたときに自動的に更新する<br/>高速読み込み時間とローカルにキャッシュされたナビゲーション構造<br/>|専門<br/><br/>利用可能なオプションの幅広い選択肢<br/>キャッシュが正しく使用されている場合の高速読み込み<br/>応答性の高いページデザインでは、多くのオプションが適切に機能します。<br/>|
|連続<br/><br/>サイトの構造を反映するように自動的に更新されません<br/>セキュリティによるトリミングが有効な場合のパフォーマンスへの影響<br/>|連続<br/><br/>**推奨されない**<br/>**パフォーマンスとスケーラビリティに影響を与える**<br/>**調整の対象**<br/>|連続<br/><br/>サイトを簡単に並べ替える機能がない<br/>マスターページのカスタマイズが必要 (技術的なスキルが必要)<br/>|連続<br/><br/>カスタム開発が必要<br/>Azure などの外部データソース/キャッシュが必要です。<br/>|

サイトに最適なオプションは、サイトの要件および技術的な機能によって異なります。 拡張可能なすぐに使用できるナビゲーションプロバイダーが必要な場合は、セキュリティによるトリミングを無効にした管理ナビゲーションは、非常に優れたオプションになります。 

管理ナビゲーションオプションは、構成によって維持でき、コードカスタマイズファイルは含まれません。構造ナビゲーションよりも大幅に高速です。 セキュリティによるトリミングが必要で、カスタムマスターページを使用して、SharePoint Online の既定のマスターページで発生する可能性のある変更を維持する機能がある場合は、検索ドリブンオプションの方が良い場合があります。ユーザーの利便性。 より複雑な要件がある場合は、カスタムナビゲーションプロバイダーが正しい選択になることがあります。 構造ナビゲーションは推奨されていません。

最後に、sharepoint は、よりフラット化されたサイト階層および SharePoint ハブサイトを使用したハブアンドスポークモデルを活用して、最新の SharePoint サイトアーキテクチャに対して追加のナビゲーションプロバイダーと機能を追加していることに注意する必要があります。 これにより、SharePoint 発行機能の使用を必要としないさまざまなシナリオを実現することができます。これらのナビゲーション構成は、SharePoint Online 内のスケーラビリティと遅延のために最適化されています。 同じ原則を適用することによって、SharePoint 発行サイトの全体的な構造を flatter 構造に簡素化することで、多くの場合、全体的なパフォーマンスとスケールにも役立つことに注意してください。 これは、数百のサイト (サブ web) を持つ単一のサイトコレクションを使用するのではなく、多くのサイトコレクションを非常に少数のサブサイト (サブ web) で使用するということです。


## <a name="using-managed-navigation-and-metadata-in-sharepoint-online"></a>SharePoint Online での管理ナビゲーションとメタデータの使用

管理ナビゲーションは、構造ナビゲーションと同じ機能のほとんどを再作成するための、すぐに使用できるもう1つのオプションです。 管理されたメタデータは、セキュリティによるトリミングを有効または無効にするように構成できます。 セキュリティによるトリミングが無効で構成されている場合、管理ナビゲーションは、一定数のサーバー呼び出しを使用してすべてのナビゲーションリンクを読み込むため、非常に効率的です。 ただし、セキュリティによるトリミングを有効にすると、管理ナビゲーションの利点の一部が否定され、お客様は最適なパフォーマンスとスケーラビリティを得るためにカスタムナビゲーションソリューションの1つを調査することを選択できます。

多くのサイトでは、サイトのすべてのユーザーに対してナビゲーション構造が一貫しているため、セキュリティによるトリミングは必要ありません。 セキュリティによるトリミングが無効で、すべてのユーザーがアクセスできないナビゲーションにリンクが追加されても、リンクは表示されますが、アクセス拒否メッセージになります。 コンテンツに偶発的にアクセスする危険性はありません。

### <a name="how-to-implement-managed-navigation-and-the-results"></a>管理ナビゲーションと結果を実装する方法

管理ナビゲーションの詳細については、「 [SharePoint Server の管理ナビゲーションの概要](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation)」を参照してください。たとえば、Docs.Microsoft.com に関する記事があります。

管理ナビゲーションを実装するために、サイトのナビゲーション構造に対応する Url を使用して用語を設定します。 管理ナビゲーションでは、多くの場合、構造ナビゲーションを手動で置き換えることもできます合わせ。 次に例を示します。

![SharePoint Online サイト構造](media/SPONavOptionsListOfSites.png)

次の例は、管理ナビゲーションを使用した複雑なナビゲーションのパフォーマンスを示しています。

![管理ナビゲーションを使用した複雑なナビゲーションのパフォーマンス](media/SPONavOptionsComplexNavPerf.png)

管理ナビゲーションを使用すると、構造ナビゲーション手法と比較してパフォーマンスが向上します。
  
## <a name="using-structural-navigation-in-sharepoint-online"></a>SharePoint Online で構造ナビゲーションを使用する

これは既定で使用される既定のナビゲーションですが、これは最も簡単な方法ですが、高コストのパフォーマンスのトレードオフがあります。 これはカスタマイズを必要とせず、技術的ではないユーザーも簡単にアイテムを追加したり、アイテムを非表示にしたり、設定ページからナビゲーションを管理したりすることができます。 ただし、管理ナビゲーションでは、管理ナビゲーションを使用することをお勧めします。これは、パフォーマンスの向上にも容易に管理および制御できるので、管理ナビゲーションを使用することをお勧めします。

![サブサイトの表示が選択された構造ナビゲーション](media/SPONavOptionsStructuredShowSubsites.png)
  
### <a name="turning-on-structural-navigation-in-sharepoint-online"></a>SharePoint Online で構造ナビゲーションを有効にする

構造ナビゲーションと [サブサイトの表示] オプションがオンになっている標準的な SharePoint Online ソリューションのパフォーマンスがどのように機能するかを説明します。 [ページ**サイトの設定** \> ]**ナビゲーション**にある設定のスクリーンショットを次に示します。
  
![サブサイトが表示されているスクリーンショット](media/5b6a8841-34ed-4f61-b6d3-9d3e78d393e7.png)
  
### <a name="analyzing-structural-navigation-performance-in-sharepoint-online"></a>SharePoint Online で構造ナビゲーションのパフォーマンスを分析する

SharePoint ページのパフォーマンスを分析するには、Internet Explorer の F12 開発者ツールの [**ネットワーク**] タブを使用します。 
  
![F12 開発者ツールの [ネットワーク] タブが表示されているスクリーンショット](media/SPONavOptionsNetworks.png)
  
1. [**ネットワーク**] タブで、読み込まれている .aspx ページをクリックし、[**詳細**] タブをクリックします。<br/> ![[詳細] タブが表示されているスクリーンショット](media/ad85cefb-7bc5-4932-b29c-25f61b4ceeb2.png)<br/>
2. [**応答ヘッダー**] をクリックします。 <br/>![[詳細] タブのスクリーンショット](media/c47770ac-5b2b-4941-9830-c57565dec4cc.png)<br/>SharePoint は、応答ヘッダーに有用な診断情報を返します。 
3. 最も有用な情報の1つは**Sprequestduration**で、サーバー上での要求の処理にかかった時間をミリ秒単位で示した値です。 次のスクリーンショットでは、構造ナビゲーションに対して [**サブサイトの表示]** がオフになっています。 これは、グローバルナビゲーションにサイトコレクションリンクのみが存在することを意味します。<br/>![要求時間として負荷時間が表示されているスクリーンショット](media/3422b2e8-15ec-4bb9-ba86-0965b6b49b01.png)<br/>
4. **Sprequestduration**キーの値は245ミリ秒です。 これは、要求を返すのにかかった時間を表します。 サイトにはナビゲーションアイテムが1つしか存在しないため、これは、SharePoint Online が大きなナビゲーションなしでどのように動作するかについて適切なベンチマークです。 次のスクリーンショットは、サブサイトへの追加がこのキーに与える影響を示しています。<br/>![2,502 ミリ秒の要求時間が表示されているスクリーンショット](media/618ee4e9-2ffa-4a22-b638-fa77b72292b8.png)<br/>
  
サブサイトを追加すると、この比較的単純なサンプルサイトのページ要求を返すのにかかる時間が大幅に増加しました。 ナビゲーション内のページやその他の構成およびトポロジオプションを含む、複雑なサイト階層は、この影響をさらに大きく増加させる可能性があります。

## <a name="using-search-driven-client-side-scripting"></a>検索型クライアント側スクリプトを使用する

検索を使用すると、継続的クロールを使用してバックグラウンドで構築されたインデックスを活用できます。 検索結果は検索インデックスから取り出され、結果はセキュリティによってトリミングされます。 通常、セキュリティによるトリミングが必要な場合は、標準のナビゲーションプロバイダーよりも高速です。 構造ナビゲーションで検索を使用すると、特に複雑なサイト構造の場合は、ページの読み込み時間が大幅に短縮されます。 この管理ナビゲーション全体の主な利点は、セキュリティによるトリミングによる恩恵を受けることです。

この方法では、カスタムマスターページを作成し、すぐに使用できないナビゲーションコードをカスタム HTML に置き換える必要があります。 次の例に示されている手順に従って、ファイル`seattle.html`のナビゲーションコードを置換します。 この例では、 `seattle.html`ファイルを開き、要素`id=”DeltaTopNavigation”`全体をカスタム HTML コードに置き換えます。

### <a name="example-replace-the-out-of-the-box-navigation-code-in-a-master-page"></a>例: マスターページですぐに使用するナビゲーションコードを置換する

1.  [サイトの設定] ページに移動します。
2.  [**マスター**ページ] をクリックして、マスターページギャラリーを開きます。
3.  ここから、ライブラリ内を移動して、ファイル`seattle.master`をダウンロードすることができます。
4.  テキストエディターを使用してコードを編集し、次のスクリーンショットのコードブロックを削除します。<br/>![表示されているコードブロックを削除する](media/SPONavOptionsDeleteCodeBlock.png)<br/>
5. タグとタグの間`<SharePoint:AjaxDelta id=”DeltaTopNavigation”>`のコードを削除し、次のスニペットに置き換えます。 `<\SharePoint:AjaxDelta>`<br/>

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
6. 読み込みイメージのアンカータグの URL を、サイトコレクションの読み込み中の画像へのリンクを使用して、先頭に置きます。 変更を行った後、ファイルの名前を変更して、マスターページギャラリーにアップロードします。 これにより、新しい .master ファイルが生成されます。<br/>
7. この HTML は、JavaScript コードから返される検索結果によって設定される基本的なマークアップです。 次のスニペットで示すように、var root = "site collection URL" の値を変更するコードを編集する必要があります。<br/>

```
var root = “https://spperformance.sharepoint.com/sites/NavigationBySearch”;
```
<br/>
8. 結果は、自身の nodes 配列に割り当てられ、そのオブジェクトから階層が構築されます。このオブジェクトには、出力を配列 self に割り当てるための linq を使用します。 この配列は、HTML にバインドされたオブジェクトです。 これは、ko-kr () 関数に self オブジェクトを渡すことによって、toggleView () 関数で行われます。<br/>これにより、階層配列が次の HTML にバインドされます。<br/>

```
<div data-bind=”foreach: hierarchy” class=”noindex ms-core-listMenu-horizontalBox”>
```

の`mouseenter`イベントハンドラーは、 `mouseexit` `addEventsToElements()`関数で実行されるサブサイトのドロップダウンメニューを処理するために、トップレベルのナビゲーションに追加されます。

複雑なナビゲーションの例では、ローカルキャッシュを使用せずに新しいページ読み込みを行うと、ベンチマーク構造ナビゲーションからサーバーにかかった時間が短縮され、管理ナビゲーション方法と同様の結果が得られることがわかります。

### <a name="about-the-javascript-file"></a>JavaScript ファイルについて...

JavaScript ファイル全体は次のようになります。

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

この`jQuery $(document).ready`関数の上記のコードを要約するには、 `viewModel object`が作成され`loadNavigationNodes()`ていて、そのオブジェクトの関数が呼び出されます。 この関数は、クライアントブラウザーの HTML5 ローカルストレージに格納されている、以前に作成したナビゲーション階層`queryRemoteInterface()`を読み込むか、または関数を呼び出します。

`QueryRemoteInterface()`スクリプト内で事前に`getRequest()`定義されたクエリパラメーターを使用して、関数を使用して要求を作成し、サーバーからデータを返します。 このデータは基本的に、サイトコレクション内のすべてのサイトの配列であり、さまざまなプロパティを持つデータ転送オブジェクトとして表されます。 

このデータは、以前に定義した`SPO.Models.NavigationNode` HTML に値`Knockout.js`をデータバインドすることによって使用される観測可能なプロパティを作成するために使用する、以前に定義したオブジェクトに解析されます。 

その後、オブジェクトは結果配列に格納されます。 この配列は、今後のページ読み込み時のパフォーマンスを向上させるために、ノックアウトを使用して JSON に解析され、ローカルブラウザーストレージに格納されます。

### <a name="benefits-of-this-approach"></a>このアプローチの利点

[このアプローチ](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page)の主な利点の1つは、HTML5 ローカルストレージを使用することによって、ユーザーが次回ページを読み込むときに、ナビゲーションがローカルに保存されることです。 構造化ナビゲーションで検索 API を使用することによって、パフォーマンスが大幅に向上しました。ただし、この機能を実行してカスタマイズするには、いくつかの技術的な機能が必要です。 

[実装例](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page)では、サイトは、すぐに使用できる構造ナビゲーションと同じ方法で並べられています。アルファベット順 この順序から逸脱する必要がある場合は、開発と管理がより複雑になります。 また、この方法では、サポートされているマスタページから逸脱する必要があります。 カスタムマスターページが保持されていない場合、サイトは、Microsoft がマスターページに加えた更新プログラムと機能強化を見逃さないようになります。

[上記のコード](#about-the-javascript-file)には、次のような依存関係があります。

- jQueryhttp://jquery.com/
- KnockoutJS -http://knockoutjs.com/
- Linq- http://linqjs.codeplex.com/、または github.com/neuecc/linq.js

LinqJS の現在のバージョンには、上記のコードで使用されている ByHierarchy メソッドは含まれていません。また、ナビゲーションコードが破損します。 この問題を解決するには、次のメソッドを Linq ファイルに追加し`Flatten: function ()`て、行の前に追加します。

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

