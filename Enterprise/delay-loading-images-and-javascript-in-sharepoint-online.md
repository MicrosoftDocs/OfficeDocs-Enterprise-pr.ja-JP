---
title: SharePoint Online での画像の読み込み遅延と JavaScript
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/3/2019
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 74d327e5-755f-4135-b9a5-7b79578c1bf9
description: この記事では、JavaScript を使用して画像の読み込みを遅延させることにより、SharePoint Online ページの読み込み時間を短縮する方法と、ページが読み込まれるまで重要でない JavaScript の読み込みを待機する方法について説明します。
ms.openlocfilehash: 86efb767e80927f7d3f5d8055676e6d99da4d667
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/07/2020
ms.locfileid: "41840564"
---
# <a name="delay-loading-images-and-javascript-in-sharepoint-online"></a>SharePoint Online での画像の読み込み遅延と JavaScript

この記事では、JavaScript を使用して画像の読み込みを遅延させることにより、SharePoint Online ページの読み込み時間を短縮する方法と、ページが読み込まれるまで重要でない JavaScript の読み込みを待機する方法について説明します。
  
SharePoint Online では、画像がページの読み込み速度に悪影響を及ぼす可能性があります。 既定では、ほとんどのモダンインターネットブラウザーは、HTML ページの読み込み時に画像を事前に取得します。 このため、ユーザーが下にスクロールするまで画像が画面に表示されない場合は、ページが不必要に読み込まれることがあります。 画像は、ページの可視部分を読み込むことをブラウザーにブロックできます。 この問題を回避するには、まず、JavaScript を使用して画像の読み込みをスキップします。 また、必須ではない JavaScript を読み込むと、SharePoint ページの読み込み時間が遅くなる可能性があります。 このトピックでは、SharePoint Online の JavaScript を使用してページの読み込み時間を向上させる方法について説明します。
  
## <a name="improve-page-load-times-by-delaying-image-loading-in-sharepoint-online-pages-by-using-javascript"></a>JavaScript を使用して SharePoint Online ページで画像の読み込みを遅延することで、ページの読み込み時間を短縮する

JavaScript を使用して、web ブラウザーが画像を事前に取得できないようにすることができます。 これにより、ドキュメント全体のレンダリングが高速化されます。 これを行うには、 \<img\>タグから src 属性の値を削除し、次のような data 属性のファイルへのパスに置き換えます。 次に例を示します。
  
```html
<img src="" data-src="/sites/NavigationBySearch/_catalogs/masterpage/media/microsoft-white-8.jpg" />
```

この方法を使用すると、ブラウザーはすぐに画像をダウンロードしません。 イメージがビューポートに既に含まれている場合、JavaScript はブラウザーに、データ属性から URL を取得して src 属性の値として挿入するよう指示します。 画像は、ユーザーがスクロールして表示されるときにのみ読み込まれます。
  
すべての操作を行うには、JavaScript を使用する必要があります。
  
テキストファイルで、 **Iselementinviewport ()** 関数を定義し、要素がブラウザーのユーザーに表示される部分にあるかどうかを確認します。
  
```javascript
function isElementInViewport(el) {
  if (!el)
    return false;
  var rect = el.getBoundingClientRect();
  return (
    rect.top >= 0 &amp;&amp;
    rect.left >= 0 &amp;&amp;
    rect.bottom <= (window.innerHeight || document.documentElement.clientHeight) &amp;&amp;
    rect.right <= (window.innerWidth || document.documentElement.clientWidth)
  );
}
```

次に、 **loadItemsInView ()** 関数で**Iselementinviewport ()** を使用します。 **LoadItemsInView ()** 関数は、データソース属性の値がユーザーに表示されるブラウザーの部分にある場合、その値を持つすべての画像を読み込みます。 テキストファイルに次の関数を追加します。
  
```javascript
function loadItemsInView() {
  //Select elements by the row id.
  $("#row [data-src]").each(function () {
      var isVisible = isElementInViewport(this);
      if (isVisible) {
          if ($(this).attr("src") == undefined) {
              $(this).attr("src", $(this).data("src"));
          }
      }
  });
}
```

最後に、次の例に示されているように、 **loadItemsInView ()** をウィンドウから呼び出し**ます。** これにより、ユーザーが必要とするときに、ビューポートに含まれるすべてのイメージが読み込まれるようになります。 次の内容をテキストファイルに追加します。
  
```javascript
//Example of calling loadItemsInView() from within window.onscroll()
$(window).on("scroll", function () {
    loadItemsInView();
});

```

SharePoint Online では、#s4 workspace \<div\>タグの scroll イベントに次の関数をアタッチする必要があります。 これは、リボンがページの上部に常に接続されていることを確認するために、ウィンドウイベントがオーバーライドされるためです。
  
```javascript
//Keep the ribbon at the top of the page
$('#s4-workspace').on("scroll", function () {
    loadItemsInView();
});
```

テキストファイルを拡張子 .js の JavaScript ファイルとして保存します。たとえば、: Delayloadimages.js) のようにします。
  
: Delayloadimages.js) の記述が終了したら、ファイルの内容を SharePoint Online のマスターページに追加できます。 これを行うには、マスターページのヘッダーにスクリプトリンクを追加します。 マスターページでは、そのマスターページレイアウトを使用する SharePoint Online サイトのすべてのページに JavaScript が適用されます。 または、サイトの1つのページでのみこれを使用する場合は、スクリプトエディター Web パーツを使用して JavaScript をページに埋め込みます。 詳細については、以下のトピックを参照してください。
  
- [[方法]: SharePoint Server 2013 のサイトにマスター ページを適用する](https://go.microsoft.com/fwlink/p/?LinkId=525627)

- [[方法]: SharePoint 2013 でページ レイアウトを作成する方法](https://go.microsoft.com/fwlink/p/?LinkId=525628)

### <a name="example-referencing-the-javascript-delayloadimagesjs-file-from-a-master-page-in-sharepoint-online"></a>例: SharePoint Online でマスターページから JavaScript の: Delayloadimages.js) ファイルを参照する
  
これを動作させるには、マスターページで jQuery を参照する必要もあります。 次の例では、最初のページの読み込みで、読み込まれたイメージは1つだけですが、ページ上にはさらにいくつかのページがあることがわかります。
  
![ページ上に読み込まれる 1 つのイメージが表示されたスクリーンショット](media/3d177ddb-67e5-43a7-b327-c9f9566ca937.png)
  
次のスクリーンショットは、スクロール後にダウンロードされた残りの画像を表示します。
  
![ページ上に読み込まれる複数のイメージが表示されたスクリーンショット](media/95eb2b14-f6a1-4eac-a5cb-96097e49514c.png)
  
JavaScript を使用して画像の読み込みを延期することは、パフォーマンスを向上させる効果的な手法になる可能性があります。ただし、この手法がパブリック web サイトに適用されている場合、検索エンジンは、通常の形式の画像をクロールするのと同じ方法で画像をクロールすることはできません。 これは、ページが読み込まれるまで画像自体のメタデータが実際には存在しないため、検索エンジンのランキングに影響する可能性があります。 検索エンジンのクローラーは HTML のみを読み取るため、画像はページ上のコンテンツとして表示されません。 画像は、検索結果内のページのランク付けに使用する要因の1つです。 これを回避する方法の1つは、画像の導入テキストを使用することです。
  
## <a name="github-code-sample-injecting-javascript-to-improve-performance"></a>GitHub コードサンプル: JavaScript を挿入してパフォーマンスを向上させる

GitHub で提供されている[JavaScript インジェクション](https://go.microsoft.com/fwlink/p/?LinkId=524759)に関する記事やコードサンプルを見逃さないようにしてください。
  
## <a name="see-also"></a>関連項目

[Office 2013 および Office 365 ProPlus でサポートされているブラウザー](https://support.office.com/article/57342811-0dc4-4316-b773-20082ced8a82)
  
[[方法]: SharePoint Server 2013 のサイトにマスター ページを適用する](https://go.microsoft.com/fwlink/p/?LinkId=525627)
  
[[方法]: SharePoint 2013 でページ レイアウトを作成する方法](https://go.microsoft.com/fwlink/p/?LinkId=525628)
