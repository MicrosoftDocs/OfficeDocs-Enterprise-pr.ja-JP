---
title: SharePoint Online のナビゲーション オプション
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/27/2018
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: adb92b80-b342-4ecb-99a1-da2a2b4782eb
description: この資料では、クラシックの発行の管理または検索によるナビゲーションを使用して SharePoint Online のページの読み込み時間を改善する方法について説明します。
ms.openlocfilehash: 6b2ee613d0cc6a6df92eb9b53374087a0ac2e5b7
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541780"
---
# <a name="navigation-options-for-sharepoint-online"></a>SharePoint Online のナビゲーション オプション

この資料では、クラシックの発行の管理または検索によるナビゲーションを使用して SharePoint Online のページの読み込み時間を改善する方法について説明します。
  
SharePoint Online クラシックの発行を有効になっているが 2 つのナビゲーション領域です。グローバル ナビゲーションと現在のナビゲーションです。
  
グローバル ナビゲーションは、現在のナビゲーションは、側またはコンテキストで左/右のナビゲーション言語の構成と使用するマスター ページに依存しているときに上部のナビゲーション メニューです。
  
ナビゲーションできますパフォーマンスに悪影響全体のポータルのポータル全体での使用の構成は、多くの場合、任意の SharePoint サイトの重要な要素のようです。
  
構造のナビゲーションは、セキュリティ トリミングを使用する、設置型トポロジー向けに設計されて、このデザインはサーバーに過度な呼び出しが発生し、使用時のパフォーマンスに影響、SharePoint Online のナビゲーションの推奨されるオプションではありません。
  
簡素化された統合されたサイト階層を持つ、現代モダンの SharePoint サイトの導入によりデザインが変更されています。ナビゲーションに関連するパフォーマンスの問題を解消するには、簡略化された階層を使用したナビゲーションを簡素化しました。
  
SharePoint と同様に 3 分の 1、カスタムの検索ベースのアプローチの 2 つのメイン ・ ボックスのナビゲーション オプションがあります。または、4 つ目と非常によく使用されるオプションは、カスタム ナビゲーション プロバイダーを作成します。このガイドには、カスタム ナビゲーション プロバイダーの[オンラインの SharePoint ポータルのナビゲーション ソリューション](https://docs.microsoft.com/en-us/sharepoint/dev/solution-guidance/portal-navigation)を参照してください。 
  
各オプションには長所と短所を次の表で説明されています。
  
|**構造ナビゲーション**|**管理ナビゲーション**|**検索方式のナビゲーション**||**カスタム ナビゲーション プロバイダー**|
|:-----|:-----|:-----|:-----|:-----|
| 長所:  <br/>  構成しやすい  <br/>  セキュリティ トリミングされている  <br/>  サイトが追加されると自動的に更新する  <br/> | 長所:  <br/>  メンテナンスしやすい  <br/>  推奨オプション  <br/> | 長所:  <br/>  セキュリティ トリミングされている  <br/>  サイトが追加されると自動的に更新する  <br/>  読み込み時間が短く、ナビゲーション構造がローカルにキャッシュされている  <br/> || 長所:  <br/>    <br/>  選択の幅オプションを利用可能と  <br/>  正しく使用されてキャッシュする場合の高速読み込み  <br/> |
| 短所:  <br/> **非推奨** <br/> **パフォーマンスに与える影響** <br/> | 短所:  <br/>  サイト構造を反映するように自動的に更新されない  <br/>  セキュリティ トリミングが有効になっている場合は、パフォーマンスに与える影響  <br/> | 短所:  <br/>  サイトを簡単に並べ替えられない  <br/>  マスター ページのカスタマイズが必要 (技術的なスキルが必要)  <br/> || 短所:  <br/>  カスタム開発が必要  <br/>  外部データ ソース キャッシュの保存が必要なと Azure など  <br/> |
   
サイトの最適なオプションと技術的な機能をサイトの要件に依存します。カスタム マスター ページを使用して快適なしている SharePoint Online の既定のマスター ページで発生する変更内容を維持するために組織の一部の機能がある場合、[検索ベース] オプションの間で最高のユーザー エクスペリエンスが生成されます。ボックスの構造的なナビゲーションと検索の間の単純な妥協点を設定する場合、管理対象のナビゲーションは非常に良いオプションです。管理ナビゲーションのオプションを維持できる構成では、コードのカスタマイズ ファイルは関与しませんし、ボックスの構造上のナビゲーションよりも大幅に高速ですが。
  
現代と同様に、従来のポータルの全体的な構造の簡素化は、全体のパフォーマンスと拡張性にも同様のことができます。内容には、何百もの単一のサイト コレクションではなく/何千ものサイト (サブ)、適切なアプローチは、非常にいくつかサブサイト (サブ web) の多くのサイト コレクションです。
  
すべてのコンテンツを 1 つの巨大なデータベースに配置することを避けることができます、およびナビゲーションおよびさらに重要なセキュリティの柔軟性により、最終的にこのサービスの他の拡大・縮小オプションが用意されています。
  
## <a name="using-structural-navigation-in-sharepoint-online"></a>SharePoint Online で構造ナビゲーションを使用する

これは、既定で使用される、標準のナビゲーションと最も簡単なソリューションが、コスト パフォーマンスのトレードオフが。カスタマイズする必要がないと非技術的なユーザーことができますも簡単に項目を追加、アイテムを非表示しナビゲーションの設定] ページから管理します。管理のナビゲーションもできるとナビゲーションの管理を使用することを推奨するような場合は true がただしも容易にするこれは、管理し、同様に制御します。
  
### <a name="turning-on-structural-navigation-in-sharepoint-online"></a>SharePoint Online で構造ナビゲーションを有効にする

構造のナビゲーションと表示する場合は、標準的な SharePoint Online ソリューションのパフォーマンスでのオプションのサブサイトを説明するために有効にします。次の例を [**サイトの設定**] ページの設定\>**ナビゲーション**します。
  
![サブサイトが表示されているスクリーンショット](media/5b6a8841-34ed-4f61-b6d3-9d3e78d393e7.png)
  
### <a name="analyzing-structural-navigation-performance-in-sharepoint-online"></a>SharePoint Online で構造ナビゲーションのパフォーマンスを分析する

SharePoint のページのパフォーマンスを分析するには、Internet Explorer の F12 開発者ツールの **[ネットワーク]** タブを使用します。 
  
![F12 開発者ツールの [ネットワーク] タブが表示されているスクリーンショット](media/e2aed8af-0843-487a-8b68-4f5260a2685e.png)
  
**[ネットワーク]** タブで、読み込まれている .aspx ページ、**[詳細]** タブの順にクリックします。 
  
![[詳細] タブが表示されているスクリーンショット](media/ad85cefb-7bc5-4932-b29c-25f61b4ceeb2.png)
  
**[応答ヘッダー]** をクリックします。
  
![[詳細] タブのスクリーンショット](media/c47770ac-5b2b-4941-9830-c57565dec4cc.png)
  
SharePoint は、その応答ヘッダー内で、有益な診断情報を返します。最も便利な診断情報の 1 つは **SPRequestDuration** です。これは、サーバー上で要求の処理にかかった時間の値 (ミリ秒単位) です。 
  
次のスクリーン ショットの**サブサイトを表示するの**には構造のナビゲーションを確認です。これは、グローバル ナビゲーションにサイト コレクションのリンクがあることを意味します。 
  
![要求時間として負荷時間が表示されているスクリーンショット](media/3422b2e8-15ec-4bb9-ba86-0965b6b49b01.png)
  
**SPRequestDuration**キーには、245 のミリ秒単位の値があります。これは、要求を取得するにかかった時間を表します。サイトのナビゲーション アイテムを 1 つだけなので、これは、SharePoint Online を実行する方法なく大量のナビゲーションのための良いベンチマークです。次のスクリーン ショットでは、サブサイトに追加すると、このキーにどのように影響する方法を示します。 
  
![2,502 ミリ秒の要求時間が表示されているスクリーンショット](media/618ee4e9-2ffa-4a22-b638-fa77b72292b8.png)
  
サブサイトの追加により、ページ要求に返答するまでにかかる時間が大きく増加しました。
  
標準の構造化ナビゲーションを使用する利点は、することができます簡単に順番を整理する、サイトを非表示、ページを追加、セキュリティ トリミングされた結果は、SharePoint Online でサポートされているマスター ページから逸脱していないです。
  
## <a name="using-managed-navigation-and-managed-metadata-in-sharepoint-online"></a>SharePoint Online で管理ナビゲーションと管理されたメタデータを使用する

管理ナビゲーションは、構造ナビゲーションと同じ種類の機能を再作成するために使用できる別のそのまま使用できるオプションです。
  
マネージ メタデータを使用する利点は、サイトのナビゲーションを作成するクエリでのコンテンツを使用するよりもデータを取得するためにはるかに高速であります。高速にはセキュリティをトリムするための方法、結果が、ユーザーでは、特定のサイトにアクセスがない場合リンクは表示されますが、エラー メッセージに 。
  
 **管理ナビゲーションと結果を実装する方法**
  
上にある記事がいくつか TechNet 管理ナビゲーションの詳細については、 [SharePoint Server 2013 でのナビゲーションの管理の概要](https://go.microsoft.com/fwlink/?LinkId=708689)を参照してください。
  
管理ナビゲーションを実装するためには、用語ストア管理者のアクセス許可が必要です。サイト コレクションの構造と一致する URL 付き用語を設定すると、管理ナビゲーションを使用して構造ナビゲーションと置き換えることができます。例:
  
![Subsite1 の例のスクリーンショット](media/4155b4da-ccff-4e2a-92de-7803ac62982b.png)
  
次の例は、管理ナビゲーションを使用した複雑なナビゲーションのパフォーマンスを示しています。
  
![SPRequestDuration の例のスクリーンショット](media/72257528-0ec6-48b0-85a5-efeb7432db5b.png)
  
常に管理ナビゲーションを使用すると、クエリによるコンテンツの構造ナビゲーションのアプローチと比較してパフォーマンスが向上します。
  
## <a name="using-search-driven-client-side-scripting"></a>検索駆動のクライアント側スクリプトを使用する

検索を使用すると、継続的クロールによってバックグラウンドでビルドされたインデックスを活用できます。つまり、負荷の高いコンテンツのクエリはありません。検索結果が検索インデックスから取り込まれ、結果はセキュリティ トリミングされます。通常のコンテンツのクエリを使用するよりも高速です。構造のナビゲーション用の検索を使用すると、特に複雑なサイト構造がある場合は、ページの読み込み時間が大幅に短縮します。この管理ナビゲーションの主な利点は、セキュリティ トリミングの恩恵を受けられることです。
  
このアプローチには、カスタム マスター ページの作成、そのまま使用できるナビゲーションのコードのカスタム HTML への置き換えなどが含まれます。ファイル seattle.html のナビゲーション コードを置き換えるには、次の手順を実行します。
  
次の使用例では、seattle.html ファイルを開くし、全体の要素を置き換える**id ="DeltaTopNavigation"** カスタム HTML コードとします。 
  
 **例: マスター ページでそのまま使用できるナビゲーションのコードを置き換えるには**
  
1. **[サイト設定]** ページに移動します。 
    
2. **[マスター ページ]** をクリックして、マスター ページ ギャラリーを開きます。
    
3. ここから、ライブラリ内を移動してファイル **seattle.master** をダウンロードできます。
    
4. テキスト エディターでコードを編集し、次のスクリーン ショットにあるコード ブロックを削除します。
    
    ![削除する DeltaTopNavigation コードのスクリーンショット](media/70db2cd2-660d-4e0d-9d5c-a5df331c73b4.png)
  
5. 間のコードを削除する、 \<SharePoint:AjaxDelta id ="DeltaTopNavigation"\>と\<\SharePoint:AjaxDelta\>タグし、次のスニペットに置き換えます。
    
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

6. 読み込まれる URL を交換してイメージを読み込み、サイト コレクションのイメージへのリンクで、最初にアンカー タグです。変更を行った後は、ファイルの名前を変更し、マスター ページ ギャラリーにアップロードしています。新しい .master ファイルが生成されます。
    
7. この HTML は、JavaScript コードから返された検索結果が表示されますが、基本的なマークアップです。値を変更するのには次のコードを編集する必要がありますが、 `var root = "site collection URL"` 、次のスニペットで示すように。 
    
  ```
  var root = "https://spperformance.sharepoint.com/sites/NavigationBySearch";
  ```

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
  var query = baseUrl + "'contentClass=\"STS_Web\"+path:" + root + "'&amp;trimduplicates=false&amp;rowlimit=300";
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
              if (cachedNodes &amp;&amp; timeStamp) {
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
              if (elem.children &amp;&amp; elem.children.length > 0) {
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
  
  ```

     $("li.level1").mouseover (関数 () { 
  
var 位置 = $(this).position();
  
(この) $.find("ul.level2").css ({幅: 100、左: 上の position.left + 10: 50})。
    
     }) 
  
.mouseout (関数 () {
  
(この) $.find("ul.level2").css ({左:-99999、上部: 0})。
  
});
  
$("li.level2").mouseover (関数 () {
  
var 位置 = $(this).position();
  
console.log(JSON.stringify(position)) です。
  
(この) $.find("ul.level3").css ({幅: 100、左: position.left + 95 の場合、トップ: position.top})。
    
     }) 
  
.mouseout (関数 () {
  
(この) $.find("ul.level3").css ({左:-99999、上部: 0})。
  
});
    
    } _spBodyOnLoadFunctionNames.push("InitCustomNav");
    
    To summarize the code shown above in the jQuery **[$(document).ready]** function there is a **[viewModel]** object created and then the **[loadNavigationNodes()]** function on that object is called. This function either loads the previously built navigation hierarchy stored in the HTML5 local storage of the client browser or it calls the function **[queryRemoteInterface()]**. 
    
    **[QueryRemoteInterface()]** builds a request using the **[getRequest()]** function with the query parameter defined earlier in the script and then returns data from the server. This data is essentially an array of all the sites in the site collection represented as data transfer objects with various properties. This data is then parsed into the previously defined **[SPO.Models.NavigationNode]** objects which use Knockout.js to create observable properties for use by data binding the values into the HTML that we defined earlier. The objects are then put into a results array. This array is parsed into JSON using Knockout and stored in the local browser storage for improved performance on future page loads. 
    
8. 次に、結果は、 **[self.nodes]** の配列に割り当てられているし、linq.js は配列の **[self.heirarchy]** への出力の割り当てを使用してオブジェクト階層を構築します。この配列は、HTML にバインドされているオブジェクトです。Self オブジェクトを **[ko.applyBinding()]** 関数に渡すことによって **[toggleView()]** 関数の中でこれです。これは、し、次の HTML にバインドするのには階層構造の配列を発生します。 
    
  ```
  <div data-bind="foreach: hierarchy" class="noindex ms-core-listMenu-horizontalBox">
  ```

    最後に、 **[mouseenter]** と **[mouseexit]** のイベント ハンドラーは、 **[addEventsToElements()]** 関数の中でこれはサブサイトのドロップ ダウン メニューを処理するために最上位レベルのナビゲーションに追加されます。 
    
    ナビゲーションの結果は、以下のスクリーン ショットで確認できます。
    
    ![ナビゲーションの結果のスクリーン ショット](media/020d34d2-942a-431b-9b26-6d2c8a6fde30.png)
  
    この複雑なナビゲーションの例では、ローカル キャッシュがない新しいページの読み込みにおいて、管理ナビゲーションのアプローチと似た結果を得るため、サーバーで費やした時間がベンチマークの構造ナビゲーションから短縮されたことを示しています。
    
    ![SPRequestDuration 301 のスクリーンショット](media/307d7caf-e83a-40d9-a551-91d842521d03.png)
  
    このアプローチの主な利点の 1 つは、ナビゲーションが、HTML5 のローカルの記憶域を使用して、ユーザーによる次回のページの読み込みのため、ローカルに格納されることです。
    
構造ナビゲーション用に検索 API を使用することで、パフォーマンスが大きく向上します。ただし、この機能の実行とカスタマイズには技術的な能力が必要になります。実装の例では、サイトはそのまま使用できる構造ナビゲーションと同じ順序 (アルファベット順) に並べられています。この順序から逸脱する場合は、開発とメンテナンスがより複雑になります。また、このアプローチでは、サポートされているマスター ページから逸脱する必要があります。カスタム マスター ページをメンテナンスしないと、サイトは Microsoft がマスター ページに対して加える更新と改善を逃してしまいます。
  
上記のコードには、次の依存関係があります。
  
- jQuery[http://jquery.com/](http://jquery.com/)
    
- KnockoutJS-[http://knockoutjs.com/](http://knockoutjs.com/)
    
- Linq.js - [http://linqjs.codeplex.com/](http://linqjs.codeplex.com/)、または[github.com/neuecc/linq.js](https://github.com/neuecc/linq.js/)
    
LinqJS の現在のバージョンでは、上記のコードで使用されている ByHierarchy メソッドが含まれていないと、ナビゲーション コードが破損します。この問題を解決するには、行の前に Linq.js ファイルに次のメソッドを追加」平展開: () の機能」です。
  
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


