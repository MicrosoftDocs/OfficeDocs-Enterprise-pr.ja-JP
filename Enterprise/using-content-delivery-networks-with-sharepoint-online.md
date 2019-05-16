---
title: SharePoint Online でのコンテンツ配信ネットワークの使用
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 5/8/2017
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
ms.assetid: 9a64268c-0b74-4eaa-b971-fb6380b1b165
description: '概要: この記事では、コンテンツ配信ネットワーク (CDNs) と、それらを使用して SharePoint Online のパフォーマンスを向上させる方法について説明します。'
ms.openlocfilehash: 24b12ae60a8c089d8e32d2609957e8b0e3420510
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070583"
---
# <a name="using-content-delivery-networks-with-sharepoint-online"></a>SharePoint Online でのコンテンツ配信ネットワークの使用

 **概要:** この記事では、コンテンツ配信ネットワーク (CDNs) と、それらを使用して SharePoint Online のパフォーマンスを向上させる方法について説明します。 
  
今日の web 開発コミュニティには、SharePoint ソリューションに含めることができる一般的なライブラリ (JavaScript ファイルや CSS ファイルなど) が多数あります。 これらの多くは、Microsoft によって ASP CDN にホストされています。 これは、これらの配布サーバーからこれらのライブラリを参照し、インターネットの組み込みの DNS ルーティングシステムがユーザーに最も近いサーバーを検索できるようにすることを意味します。 この記事の例では、SharePoint Online server と ASP CDN の間で人気のあるライブラリ jQuery をダウンロードする際の時差が非常に重要であることを示しています。 ユーザーは、ファイルをダウンロードする必要がないように、既に CDN バージョンをローカルコンピューターにキャッシュしておくこともできます。 これは、ユーザーが世界中に分散されており、SharePoint Online サイトをホストするデータセンターから遠く離れている場合に重要になることがあります。
  
SharePoint Online のページを作成する場合、待機時間は、ユーザーと SharePoint Online インスタンスの場所の物理的な距離によって影響を受ける可能性があります。 これは、世界中のユーザーが自分のコンテンツにアクセスしているときに、ある大陸でサイトがホストされている場合に、グローバルなプレゼンスを持つ組織にとって特に重要です。 CDNs は、特定の人気のある web アセットをエンドユーザーに近い場所にホストすることで、このような状況を緩和するのに役立ちます。
  
CDN は、同じファイルをホストするサーバーの世界規模のネットワークであるため、CDNs に格納されているファイルのインターネット Url はクライアントコンピューターによって解釈されるため、ユーザーに最も近いサーバーがファイルを提供します。 これにより、ネットワークラウンドトリップによる遅延が大幅に軽減されます。
  
## <a name="the-challenge-of-hosting-sharepoint-online-sites-for-a-global-audience"></a>グローバルな対象ユーザーのために SharePoint Online サイトをホストするための課題

SharePoint Online サイトは、Office 365 でサインアップしたときに選択された場所 (ユーザーが指定) を基準にして、データセンターでホストされます。 たとえば、サイトが米国内のサーバー上にあり、ユーザーが東アジアからサイトにアクセスしている場合、データが光ファイバーケーブルを通過するために必要な距離が原因で、待機時間の問題が発生することがあります。
  
既定の SharePoint ユーザーインターフェイスで使用されている多くの静的ファイルは、既に Microsoft の世界規模の CDNs のネットワーク上にホストされています。 これにより、時間の経過とともにパフォーマンスが向上します。 ただし、一般的な JavaScript および CSS アセット (たとえば、次のようなもの) を使用している場合は、JQuery、Modernizr、ブートストラップ、または ASP.NET Ajax) フリーで利用可能な CDNs を使用して、これらのファイルの読み込み時間を短縮することができます。
  
## <a name="advantages-of-using-cdns-to-improve-download-speed"></a>ダウンロード速度を向上させるために CDNs を使用する利点

CDNs を使用すると、さまざまな理由からページの読み込み時間を短縮できます。 1つの理由は、CDN とユーザーの間の距離が、SharePoint Online インスタンスまでの距離よりも短くなる可能性があることです。 これらのネットワークは十分に分散化されており、非常に高い可用性と応答時間が得られるように設計されています。 もう1つの理由として、CSS ファイルの一般的なライブラリを CDN と共に使用している場合、ユーザーは既にライブラリをキャッシュしていて、そのライブラリをまったくダウンロードする必要がない場合があります。
  
次のスクリーンショットは、CDNs を使用する利点を示しています。 これらのスクリーンショットは、Internet Explorer 11 開発者ツールの [**ネットワーク**] タブにあります。 これらのスクリーンショットは、人気のあるライブラリ jQuery の待機時間を示しています。 この画面を表示するには、Internet Explorer で**F12**キーを押して、wi-fi アイコンで認識されている [**ネットワーク**] タブを選択します。 
  
![F12 ネットワークのスクリーンショット](media/930541fd-af9b-434a-ae18-7bda867be128.png)
  
このスクリーンショットは、SharePoint Online サイト自体のマスターページギャラリーにアップロードされたライブラリを示しています。 ライブラリのアップロードにかかった時間は1.51 秒です。
  
![読み込み時間 1.51 秒のスクリーン ショット](media/64225c79-fa53-480f-81cd-0d351674320e.png)
  
2番目のスクリーンショットは、Microsoft の CDN によって配信された同じファイルを示しています。 この時間が経過すると、遅延は約496ミリ秒になります。 これは大規模な改善で、ページコンテンツのダウンロードに合計時間が短縮されることを示しています。
  
![読み込み時間 469 ミリ秒のスクリーンショット](media/6a553cc3-25a0-42c1-aae7-4aebbc2eb4c3.png)
  
## <a name="using-cdns-with-sharepoint-server-2013"></a>SharePoint Server 2013 での CDNs の使用

CDNs の使用は SharePoint Online のコンテキストでのみ有効であり、SharePoint Server 2013 で回避する必要があります。 これは、サーバーが社内に設置されている場合や、地理的に閉じている場合は、地理的な場所に関するすべての利点が true を保持しないためです。 また、ホストされているサーバーへのネットワーク接続がある場合は、インターネット接続を使用せずにサイトが使用される可能性があるため、CDN ファイルを取得することはできません。 それ以外の場合は、使用可能で、サイトに必要なライブラリおよびファイルに対して安定したものがある場合は、CDN を使用する必要があります。
  
## <a name="popular-cdns-and-how-to-use-them"></a>一般的な CDNs とその使用方法

Microsoft の Ajax CDN では、jQuery (およびその他のすべてのライブラリ)、ASP.NET Ajax、ブートストラップ、ノックアウトなど、よく使用されるライブラリのほとんどが提供されています。
  
これらのスクリプトをプロジェクトに含めるには、プロジェクト自体に含めるのではなく、これらのパブリックなライブラリへの参照を CDN アドレスへの参照に置き換えます。 たとえば、次のコードを使用して jQuery にリンクします。
  
```
<script src=http://ajax.aspnetcdn.com/ajax/jquery-2.1.1.js> </script>
```

CDNs の詳細については、「[コンテンツ配信ネットワーク](content-delivery-networks.md)」を参照してください。
  
## <a name="more-topics-about-using-cdns-with-sharepoint"></a>SharePoint での CDNs の使用に関するその他のトピック

[Office 365 CDN からのクライアント側 web パーツのホスティング](https://dev.office.com/sharepoint/docs/spfx/web-parts/get-started/hosting-webpart-from-office-365-cdn)
  

