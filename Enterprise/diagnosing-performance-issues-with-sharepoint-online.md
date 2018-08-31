---
title: SharePoint Online のパフォーマンスの問題の診断
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 2/23/2018
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 3c364f9e-b9f6-4da4-a792-c8e8c8cd2e86
description: この資料は、Internet Explorer の開発者ツールを使用して SharePoint Online サイトに関する一般的な問題を診断する方法を示します。
ms.openlocfilehash: 89d4544bfabf6424b5f401bad7d63bd7fa41b5ca
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541668"
---
# <a name="diagnosing-performance-issues-with-sharepoint-online"></a>SharePoint Online のパフォーマンスの問題の診断

この資料は、Internet Explorer の開発者ツールを使用して SharePoint Online サイトに関する一般的な問題を診断する方法を示します。
  
SharePoint Online サイトのページにカスタマイズによるパフォーマンスの問題があることを識別する 3 つの異なる方法があります。
  
- F12 ツール バー ネットワーク モニター
    
- カスタマイズされていないベースラインとの比較
    
- SharePoint Online の応答ヘッダーのメトリックス
    
このトピックでは、パフォーマンスの問題を診断するためにこれらの各メソッドを使用する方法について説明します。解決策を見つけることができる上、SharePoint のパフォーマンス向上に関する記事を使用して作業することができます問題の原因を理解したなら、 http://aka.ms/tune。
  
## <a name="using-the-f12-tool-bar-to-diagnose-performance-in-sharepoint-online"></a>F12 ツール バーを使用して SharePoint Online のパフォーマンスを診断する
<a name="F12ToolInfo"> </a>

この記事では、Internet Explorer 11 を使用します。他のブラウザーにある F12 開発者ツールのバージョンには、外観が若干異なりますが同様の機能があります。F12 開発者ツールの詳細については、以下を参照してください。
  
- [F12 ツールの新機能](https://go.microsoft.com/fwlink/p/?LinkId=522545)
    
- [F12 開発者ツールを使用します。](https://go.microsoft.com/fwlink/p/?LinkId=522546)
    
開発者ツールを開くには、**F12** キーを押してから [Wi-Fi] アイコンをクリックします。 
 
  
![F12 開発者ツールの Wi-Fi アイコンのスクリーンショット](media/27acacbb-5688-459a-aa2f-5c8c5f17b76e.png)
  
**[ネットワーク]** タブで、緑色の再生ボタンをクリックすると、ページが読み込まれます。ユーザーが要求したページを取得するため、このツールは、ブラウザーが要求するファイルをすべて返します。次のスクリーン ショットは、このようなリストを示しています。 
  
![ページ要求で返されるファイル リストのスクリーンショット。](media/247a9422-76da-4b0c-bed3-ce77b05e4560.png)
  
スクリーン ショットに示すように、右側でファイルのダウンロード時間も確認することができます。
  
![SharePoint から要求されたページを読み込むのにかかる時間を示す図](media/d71ad1fa-9018-4fae-82eb-c1838e7db0ff.png)
  
このように、ファイルの読み込みにかかった時間が視覚的に表示されます。緑色の線は、ブラウザーによってページが表示される準備ができたときを表します。これにより、サイトでページの読み込み時間が長い可能性があるさまざまなファイルをすばやく見ることができます。


  
## <a name="setting-up-a-non-customized-baseline-for-sharepoint-online"></a>SharePoint Online のカスタマイズされていない基準計画の設定
<a name="F12ToolInfo"> </a>

サイトのパフォーマンスの弱点を判断する最良の方法は、SharePoint Online に完全にアウト-の-標準のサイト コレクションを設定すること。この方法のカスタマイズが、ページ上で取得できるものを使用してサイトのすべてのさまざまな側面を比較できます。ビジネス ホーム ページの OneDrive は、すべてのカスタマイズがあると思われる別のサイト コレクションの良い例です。
  
## <a name="viewing-sharepoint-response-header-information"></a>SharePoint の応答ヘッダーの情報を表示する
<a name="F12ToolInfo"> </a>

SharePoint Online と SharePoint Server 2013 では、各ファイルの応答ヘッダーで、ブラウザーに返信される情報にアクセスできます。パフォーマンスの問題を診断するのに最も役立つ 2 つの値は、SPRequestDuration と X-SharePointHealthScore です。
  
- **SPRequestDuration**
    
    サーバー上での要求の処理にかかる時間です。これは、要求が非常に高負荷でリソースを集中的に使用するかどうかを判断するのに役立ちます。ページを提供するためにどれくらいの操作をサーバーが実行しているかに関する最高の情報が得られます。
    
- **X SharePointHealthScore**
    
    これは、サーバー、または、SharePoint のインスタンスが実行されている、CPU の使用率を示します。この番号範囲は 0 から 10 の 0 が、サーバがアイドル状態を示し、10 サーバーを示しますが、非常にビジー状態であります。常に 9 または 10 である HealthScore は、サーバーで継続的なパフォーマンスの問題を可能性があります。その他の任意の数は、そのサーバーが予期される範囲内で動作を示します。
    
 **SharePoint の応答ヘッダーの情報を表示するには**
  
1. F12 ツールがインストールされているがあることを確認します。ダウンロードしてこれらのツールをインストールする方法については、 [F12 ツールの新機能としては、何](https://go.microsoft.com/fwlink/p/?LinkId=522545)を参照してください。
    
2. F12 ツールの **[ネットワーク]** タブで、緑色の再生ボタンを押してページを読み込みます。 
    
3. このツールによって返される .aspx ファイルのいずれかをクリックしてから、**[詳細]** をクリックします。 
    
    ![応答ヘッダーの詳細を示しています](media/1f8a044a-caf8-4613-be2b-7e064141ac8a.png)
  
4. **[応答ヘッダー]** をクリックします。 
    
    ![応答ヘッダーの URL を示す図](media/efc7076e-447e-447e-882a-ae3aa721e2c3.png)
  
## <a name="whats-causing-performance-issues-in-sharepoint-online"></a>SharePoint Online で何がパフォーマンスの問題を引き起こしているか
<a name="F12ToolInfo"> </a>

記事[SharePoint Online のナビゲーション オプション](navigation-options-for-sharepoint-online.md)は、複雑な構造のナビゲーションがページをサーバー上の処理に時間がかかる原因であるかを決定する SPRequestDuration の値を使用する例を示します。(カスタマイズ) を行わなくても基準計画のサイトの値によって、いずれのファイルの読み込みに時間がかかってかどうかを決定することは。[SharePoint Online のナビゲーション オプション](navigation-options-for-sharepoint-online.md)の使用例は、メインの .aspx ファイルです。そのファイルには、ページの読み込みを実行している ASP.NET のコードの大部分が含まれています。によっては、サイト テンプレートを使用するこれは、start.aspx、home.aspx、default.aspx、または別の名前、ホーム ページをカスタマイズする場合。この番号では、ベースラインのサイトよりもかなり高く場合、は、パフォーマンスの問題の原因となっているページで起こっている複雑なものがあることがわかりますが。 
  
サイト固有の問題を特定したら、パフォーマンスの低下を引き起こしているものを見つけ出す推奨方法は、ページのカスタマイズなど、あり得る原因をすべて排除してから、1 つずつサイトに戻すことです。ページが正常に実行しているカスタマイズを十分に削除したら、特定のカスタマイズを 1 つずつ戻していきます。
  
たとえば、非常に複雑なナビゲーションがある場合、ナビゲーションがサブサイトを表示しないように変更してみてください。その後、これが変化をもたらしたかどうかを開発者ツールで確認します。または、大量のコンテンツのロールアップがある場合は、ページから取り除き、状況が改善したか確認します。考えられる原因をすべて排除してから 1 つずつ追加すると、簡単にどの機能が最大の問題であるかを特定し、解決策を実行することができます。 

  

