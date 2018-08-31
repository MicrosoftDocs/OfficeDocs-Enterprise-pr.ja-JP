---
title: SharePoint Online のコンテンツ配信ネットワークを使用します。
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 5/8/2017
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
ms.assetid: 9a64268c-0b74-4eaa-b971-fb6380b1b165
description: '概要: この資料は、コンテンツ配信ネットワーク (Cdn) し、使用して SharePoint Online のパフォーマンスを向上する方法について説明します。'
ms.openlocfilehash: 63062c08d0c22518eb36ea0a6faa97106fd394b4
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541624"
---
# <a name="using-content-delivery-networks-with-sharepoint-online"></a>SharePoint Online のコンテンツ配信ネットワークを使用します。

 **の概要:** この資料では、コンテンツ配信ネットワーク (Cdn) し、使用して SharePoint Online のパフォーマンスを向上する方法について説明します。 
  
今日の web 開発コミュニティでは、SharePoint ソリューションに含める場合があります (JavaScript、CSS ファイルなど) の多くの一般的なライブラリがあります。これらの多くは、ASP の CDN にマイクロソフトによってホストされています。これは、これらの分散サーバーからこれらのライブラリを参照してインターネットの組み込み DNS ルーティング システムができるよう、ユーザーに最も近いサーバーを見つけることを意味します。この資料の例では、ASP CDN とオンラインの SharePoint サーバーから一般的なライブラリ jQuery をダウンロードする間の時間差が非常に大きくする方法をデモンストレーションします。ユーザーも既に CDN のバージョンがキャッシュされ、ローカル コンピューターのため、ファイルをダウンロードする必要はありません。SharePoint Online サイトをホストするデータ センターから世界と距離を分散するユーザーがいる場合に重要なことができます。
  
SharePoint Online のページを作成する場合、ユーザーと SharePoint Online インスタンスの場所の物理的な距離が待ち時間に影響を与えます。このことは、世界的に展開していて、サイトがある大陸にホストされ、世界の反対側にいるユーザーがそのコンテンツにアクセスする組織には特に重要になります。エンドユーザーの近くにある別の場所に特定の一般的な Web 資産をホストすることで、CDN はこのような状況を和らげます。
  
CDN は、同じファイルをホストする世界規模のサーバーのネットワークであるため、ユーザーに最も近いサーバーがファイルに対応するように、CDN に格納されたファイルのインターネットの URL がクライアントのコンピューターによって解釈されます。これにより、ネットワークのラウンド トリップによって発生する遅延が大きく低減します。
  
## <a name="the-challenge-of-hosting-sharepoint-online-sites-for-a-global-audience"></a>グローバルな対象ユーザー用の SharePoint Online サイトをホストする際の課題

SharePoint Online サイトは、Office 365 にサインアップしたときに選択された場所 (ユーザーが指定する) に関連するデータ センターにホストされます。たとえば、サイトが米国内のサーバー上にあり、ユーザーは東アジアからサイトにアクセスする場合、データが光ファイバー ケーブルで伝送する距離があるため、遅延の問題が発生することがあります。
  
既定の SharePoint ユーザー インターフェイスで使用される多くの静的なファイルは、既に Cdn のマイクロソフトの世界中のネットワークでホストされます。時間の経過とともにパフォーマンスが向上します。ただし (たとえば、一般的な JavaScript、CSS の資産を使用する場合、JQuery、Modernizr、ブートス トラップ、または ASP.NET Ajax) 自由に利用可能な Cdn を使用してこれらのファイルの読み込み時間を向上させることができます。
  
## <a name="advantages-of-using-cdns-to-improve-download-speed"></a>CDN を使用してダウンロード速度を向上させる利点

Cdn を使用すると、さまざまな理由からページの読み込み時間を改善できます。理由の 1 つは、SharePoint Online のインスタンスまでの距離よりも短い、CDN とユーザー間の距離である可能性があります。これらのネットワークは、広範囲にわたって分散し、の可用性と応答時間が非常に高いものも。理由の 1 つをされていると、CSS ファイルの一般的なライブラリを使用して、CDN と協力して、ユーザーはキャッシュ ライブラリに既にあり、ダウンロードする必要はありませんも場合。
  
次のスクリーン ショットでは、Cdn を使用する利点について説明します。Internet Explorer 11 の開発者ツールの [**ネットワーク**] タブでは、これらのスクリーン ショットです。これらのスクリーン ショットでは、人気のあるライブラリ jQuery の待機時間を表示します。Internet Explorer で、この画面を表示するのには**f12 キー**を押すし、Wi-fi のアイコンを導入するケースでは、 **[ネットワーク**] タブを選択します。 
  
![F12 ネットワークのスクリーンショット](media/930541fd-af9b-434a-ae18-7bda867be128.png)
  
このスクリーン ショットは、SharePoint Online サイト自体のマスター ページ ギャラリーにアップロードされたライブラリを示しています。ライブラリにアップロードするにかかった時間は、1.51 秒です。
  
![読み込み時間 1.51 秒のスクリーン ショット](media/64225c79-fa53-480f-81cd-0d351674320e.png)
  
2 番目のスクリーン ショットは、マイクロソフトによって提供される同じファイルを示しています CDN。この時間の遅延時間は、約 496 ミリ秒です。これは大きな改善であり、全体の 2 番目がページのコンテンツをダウンロードする時間を短縮ことを示しています。
  
![読み込み時間 469 ミリ秒のスクリーンショット](media/6a553cc3-25a0-42c1-aae7-4aebbc2eb4c3.png)
  
## <a name="using-cdns-with-sharepoint-server-2013"></a>SharePoint Server 2013 で CDN を使用する

Cdn を使用してだけは、SharePoint Online のコンテキストで意味が、SharePoint Server 2013 を避ける必要があります。地理的な場所の周囲の利点のすべてを保持しないサーバーがある設置型の場合は true または地理的に閉じるためにです。さらに、ホストされているサーバーへのネットワーク接続がある場合は、サイト インターネットに接続せずに使用することがあり、CDN のファイルを取得できません。それ以外の場合は利用可能なライブラリとファイルの安定性が必要な場合、サイトの CDN を使用してください。
  
## <a name="popular-cdns-and-how-to-use-them"></a>一般的な CDN とその使用方法

JQuery (およびすべての他のライブラリ) を含む一般的なライブラリのほとんどを提供する Microsoft Ajax CDN ASP.NET Ajax、ブートス トラップ、Knockout.js、および多く。
  
これらのスクリプトをプロジェクトに含めるには、CDN のアドレスをプロジェクト自体に含めるのではなく、一般的に利用可能なライブラリへの参照を CDN のアドレスへの参照に置き換えます。たとえば、次のコードを使用して jQuery にリンクさせます。
  
```
<script src=http://ajax.aspnetcdn.com/ajax/jquery-2.1.1.js> </script>
```

Cdn の詳細については、[コンテンツ配信ネットワーク](content-delivery-networks.md)を参照してください。
  
## <a name="more-topics-about-using-cdns-with-sharepoint"></a>SharePoint で Cdn を使用する方法のより多くのトピック

[Office 365 の CDN からクライアント側の web パーツをホストしています。](https://dev.office.com/sharepoint/docs/spfx/web-parts/get-started/hosting-webpart-from-office-365-cdn)
  

