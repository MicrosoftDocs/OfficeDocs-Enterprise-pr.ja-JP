---
title: SharePoint Online のパフォーマンスの問題の診断
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 7/9/2019
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 3c364f9e-b9f6-4da4-a792-c8e8c8cd2e86
description: この記事では、Internet Explorer 開発者ツールを使用して SharePoint Online サイトの一般的な問題を診断する方法について説明します。
ms.openlocfilehash: a4d66fd019a3b477a97dbf039144734dc7ee1288
ms.sourcegitcommit: cb338a74194ec9ba0913070e2b74c9f50caffb3b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/09/2019
ms.locfileid: "35605503"
---
# <a name="diagnosing-performance-issues-with-sharepoint-online"></a>SharePoint Online のパフォーマンスの問題の診断

この記事では、Internet Explorer 開発者ツールを使用して SharePoint Online サイトの一般的な問題を診断する方法について説明します。
  
SharePoint Online サイトのページに、カスタマイズに関するパフォーマンス上の問題があることを特定するには、3種類の方法があります。
  
- F12 ツールバーのネットワークモニター

- カスタマイズされていない基準を比較する

- SharePoint Online 応答ヘッダーの指標

このトピックでは、これらの各方法を使用して、パフォーマンスの問題を診断する方法について説明します。 問題の原因を特定したら、SharePoint のパフォーマンスの向上に関する記事を使用して、ソリューションに向かって作業することがhttp://aka.ms/tuneできます。
  
## <a name="using-the-f12-tool-bar-to-diagnose-performance-in-sharepoint-online"></a>F12 ツールバーを使用して SharePoint Online のパフォーマンスを診断する
<a name="F12ToolInfo"> </a>

この記事では、Internet Explorer 11 を使用します。 他のブラウザーの F12 開発者ツールのバージョンは、同様の機能を備えていますが、外観が若干異なる場合があります。 F12 開発者ツールの詳細については、以下を参照してください。
  
- [F12 ツールの新機能](https://go.microsoft.com/fwlink/p/?LinkId=522545)

- 
  [F12 開発者ツールの使用](https://go.microsoft.com/fwlink/p/?LinkId=522546)

開発者ツールを起動するには、 **F12**キーを押してから、wi-fi アイコンをクリックします。
  
![F12 開発者ツールの Wi-Fi アイコンのスクリーンショット](media/27acacbb-5688-459a-aa2f-5c8c5f17b76e.png)
  
[**ネットワーク**] タブで、緑色の再生ボタンを押してページをロードします。 このツールは、要求されたページを取得するために、ブラウザーが要求するすべてのファイルを返します。 次のスクリーンショットは、このような一覧を示しています。
  
![ページ要求で返されるファイル リストのスクリーンショット。](media/247a9422-76da-4b0c-bed3-ce77b05e4560.png)
  
このスクリーンショットに示されているように、右側のファイルのダウンロード時間を確認することもできます。
  
![SharePoint から要求されたページを読み込むのにかかる時間を示す図](media/d71ad1fa-9018-4fae-82eb-c1838e7db0ff.png)
  
これにより、ファイルの読み込みにかかった時間を視覚的に表現できます。 緑色の線は、ページがブラウザーでレンダリングできる状態になったことを表します。 これにより、サイトでのページの読み込みが低速になる原因となる可能性のあるさまざまなファイルを簡単に確認できます。
  
## <a name="setting-up-a-non-customized-baseline-for-sharepoint-online"></a>SharePoint Online のカスタマイズされていないベースラインの設定
<a name="F12ToolInfo"> </a>

サイトのパフォーマンスの強度を判断する最良の方法は、SharePoint Online に完全に使用されていないサイトコレクションをセットアップすることです。 このようにすると、サイトのさまざまな要素を、ページ上でカスタマイズしなくても、その内容と比較できます。 OneDrive for Business ホームページは、カスタマイズが必要となる可能性がある別のサイトコレクションの良い例です。
  
## <a name="viewing-sharepoint-response-header-information"></a>SharePoint 応答ヘッダー情報を表示する
<a name="F12ToolInfo"> </a>

SharePoint Online では、各ファイルの応答ヘッダーでブラウザーに送り返される情報にアクセスできます。 パフォーマンスの問題を診断するのに最も役立つ値は**Sprequestduration**で、サーバーで要求が処理されるのにかかった時間を表示します。 これにより、要求が非常に重いもので、リソースを大量に消費しているかどうかを判断できます。 これは、サーバーがページにサービスを提供するために実行している作業の量を理解するのに最適です。

### <a name="to-view-sharepoint-response-header-information"></a>SharePoint 応答ヘッダー情報を表示するには
  
1. F12 ツールがインストールされていることを確認します。 これらのツールのダウンロードとインストールの詳細については、「 [F12 ツールの新機能](https://go.microsoft.com/fwlink/p/?LinkId=522545)」を参照してください。

2. F12 ツールの [**ネットワーク**] タブで、緑色の再生ボタンを押してページを読み込みます。

3. ツールによって返される .aspx ファイルのいずれかをクリックし、[**詳細**] をクリックします。

    ![応答ヘッダーの詳細を示しています](media/1f8a044a-caf8-4613-be2b-7e064141ac8a.png)
  
4. [**応答ヘッダー**] をクリックします。

    ![応答ヘッダーの URL を示す図](media/efc7076e-447e-447e-882a-ae3aa721e2c3.png)
  
## <a name="whats-causing-performance-issues-in-sharepoint-online"></a>SharePoint Online でパフォーマンスの問題が発生する原因
<a name="F12ToolInfo"> </a>

「 [SharePoint Online のナビゲーションオプション](navigation-options-for-sharepoint-online.md)」では、SPRequestDuration 値を使用して、複雑な構造ナビゲーションによって、ページの処理に長い時間がかかることを判断する例を示します。 ベースラインサイト (カスタマイズなし) の値を取得することによって、特定のファイルの読み込みに時間がかかるかどうかを判断できます。 [SharePoint Online のナビゲーションオプション](navigation-options-for-sharepoint-online.md)で使用されている例は、主に .aspx ファイルです。 このファイルには、ページの読み込みに対して実行される ASP.NET コードの大部分が含まれています。 使用するサイトテンプレートによっては、ホームページをカスタマイズする場合、default.aspx、default.aspx、default.aspx、またはその他の名前の場合があります。 この数値がベースラインサイトよりかなり大きい場合は、パフォーマンスの問題を発生させる、ページに複雑な処理が発生していることを示しています。
  
サイトに固有の問題を特定した後、パフォーマンスが低下していることを確認するには、ページのカスタマイズなど、考えられるすべての原因を除去して、それらを1つずつサイトに追加することをお勧めします。 ページが正常に実行されているカスタマイズを削除すると、特定のカスタマイズを1つずつ追加することができます。
  
たとえば、非常に複雑なナビゲーションの場合は、サブサイトを表示しないようにナビゲーションを変更してから、開発者ツールをチェックして、それに違いがあるかどうかを確認します。 または、大量のコンテンツロールアップを使用している場合は、それらをページから削除して、問題が改善されるかどうかを確認します。 考えられる原因をすべて排除して、一度に1つずつ追加し直すと、どの機能が最大の問題であるかを簡単に特定して、ソリューションに向けて作業できます。
