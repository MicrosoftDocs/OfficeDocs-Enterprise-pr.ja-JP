---
title: Office 365 向け ExpressRoute でのルーティング
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/7/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: e1da26c6-2d39-4379-af6f-4da213218408
description: Azure ExpressRoute を使用して Office 365 にトラフィックのルーティングを正しく理解するには、主要な ExpressRoute ルーティング要件を満たす ExpressRoute の回路とルーティング ドメインを確実に把握する必要があります。これらは、Office 365 のお客様が依存している ExpressRoute を使用するための基礎をレイアウトします。
ms.openlocfilehash: e80ce78c0b229881349a4d02c7708fb9509748a9
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541560"
---
# <a name="routing-with-expressroute-for-office-365"></a>Office 365 向け ExpressRoute でのルーティング

Azure ExpressRoute を使用して Office 365 にトラフィックのルーティングを正しく理解するには、中核となる[ExpressRoute ルーティング要件を満たす](https://azure.microsoft.com/documentation/articles/expressroute-routing/) [ExpressRoute の回路とルーティング ドメイン](https://azure.microsoft.com/documentation/articles/expressroute-circuit-peerings/)を確実に把握する必要があります。これらは、Office 365 のお客様が依存している ExpressRoute を使用するための基礎をレイアウトします。
  
上記の記事を理解する必要がある主な項目は次のとおりです。
  
- ExpressRoute 回路に特定の物理インフラストラクチャでは、マップされていないが、マイクロソフトとユーザーの代わりにピアリングのプロバイダーがピアリングの単一の場所で行われる論理的な接続。

- ExpressRoute 回路と顧客の s キーとの間の 1 対 1 マッピングがあります。

- 各回線として使用できるは、最大 3 つの独立したピアリング関係 (Azure パブリック ・ ピアリング、Azure のプライベート ・ ピアリング、および Microsoft のピアリング)。Office 365 は、マイクロソフトのピアリングを必要とします。

- 各回路は、すべてのピアリング関係の間で共有されている固定の帯域幅を持っています。

- 任意のパブリック IPv4 アドレスとパブリックに使用される番号として、ExpressRoute の回路必要があります検証によって、所有されているとまたはアドレスの範囲の所有者が排他的に割り当てられています。

- ExpressRoute の仮想回線冗長グローバルには、以下 BGP ルーティングの方法では。これは、ため、アクティブ/アクティブ構成では、プロバイダーに出口あたり 2 つの物理回線をお勧めします。

詳細については、サポートされているサービスで、コスト、および構成の詳細については[FAQ ページ](https://azure.microsoft.com/documentation/articles/expressroute-faqs/)を参照してください。マイクロソフト ピアリングのサポートを提供する接続プロバイダーの一覧については、 [ExpressRoute の場所の記事](https://azure.microsoft.com/documentation/articles/expressroute-locations/)を参照してください。概念をより詳細に説明するためにチャネル 9 の 10 部の[Office 365 のトレーニングの Azure ExpressRoute](https://channel9.msdn.com/series/aer)シリーズ記録しました。
  
## <a name="ensuring-route-symmetry"></a>ルートの対称性を確保します。

Office 365 のフロント エンド サーバーは、インターネットと ExpressRoute の両方にアクセスできます。これらのサーバーを両方が利用できる場合は、ExpressRoute 回線を介したルーティングを好みます。この可能性があるルートの非対称性、ネットワークからのトラフィックをインターネット回線を介したルーティングを希望する場合です。非対称のルートは、ステートフル パケット インスペクションを実行するデバイスが別のパスの後に外向きのパケットよりも後に続く戻り値のトラフィックをブロックできますので、問題です。
  
ExpressRoute またはインターネット経由で Office 365 への接続を開始するかどうかに関係なく、ソースが公的にルーティング可能なアドレスをする必要があります。多くの顧客は、マイクロソフトから直接ピアリング、重複除外がお客様の間で可能なプライベート アドレスを持つ実行できません。
  
Office 365 から、オンプレミスのネットワークへの通信を開始する場所のシナリオを次に示します。ネットワークの設計を簡素化、インターネット パス上でこれらのルーティングをお勧めします。
  
- サインインのパスワードの検証中に ADFS。

- [Exchange Server のハイブリッド展開](https://technet.microsoft.com/library/jj200581%28v=exchg.150%29.aspx)します。

- 設置型のホストに Exchange Online のテナントからのメール.

- オンライン メールの SharePoint は、SharePoint Online の設置型のホストに送信します。

- [SharePoint は、ハイブリッドの検索を統合](https://technet.microsoft.com/library/dn197174.aspx)します。

- [SharePoint ハイブリッド BCS](https://technet.microsoft.com/library/dn197239.aspx )。

- [ビジネスのハイブリッドの Skype](https://technet.microsoft.com/en-us/library/jj205403.aspx) 、 [Skype](https://technet.microsoft.com/library/skype-for-business-online-federation-and-public-im-conectivity.aspx)。

- [Skype ビジネス クラウド コネクタ](https://technet.microsoft.com/library/mt605227.aspx )です。

これらの双方向のトラフィック フローのネットワークにルーティングするのにはマイクロソフトは、マイクロソフトと、設置型デバイスに BGP 経路を共有する必要があります。
  
## <a name="deciding-which-applications-and-features-route-over-expressroute"></a>アプリケーションと機能は、ExpressRoute 経由でルーティングを決定します。

Microsoft ピアリング ルーティング ドメインを使用して、ピアリング関係を構成するし、適切なアクセスの承認は、ExpressRoute 経由で利用可能なすべての PaaS および SaaS のサービスを表示することができます。[BGP コミュニティ](https://aka.ms/bgpexpressroute365)や[ルート フィルター](https://docs.microsoft.com/azure/expressroute/how-to-routefilter-portal)は、ExpressRoute 用に設計された Office 365 サービスを管理できます。
  
Office 365 のビデオ、その他のアプリケーションは、Office 365 アプリケーションです。ただし、Office 365 のビデオは、の 3 つの異なるコンポーネント、ポータル、ストリーミング サービス、およびコンテンツ配信ネットワークで構成されます。Azure のメディア サービスのストリーミング サービス生活 SharePoint Online 内でポータルが存在しており、Azure CDN でコンテンツ配信ネットワークが存在します。次の表では、これらのコンポーネントについて説明します。
  
| |
|**コンポーネント**|**アプリケーションの基になります。**|**SharePoint オンライン BGP のコミュニティに含まれますか。**|**使用法**|
|:-----|:-----|:-----|:-----|
|Office 365 ビデオ ポータル  <br/> |SharePoint Online  <br/> |はい  <br/> |構成]、[アップロード  <br/> |
|Office 365 のビデオのストリーミング サービス  <br/> |Azure Media Services  <br/> |いいえ  <br/> |ストリーミング ビデオでは、CDN からイベントに使用されるサービス  <br/> |
|Office 365 のビデオ コンテンツ配信ネットワーク  <br/> |Azure CDN  <br/> |いいえ  <br/> |ビデオのダウンロードとストリーミングの主なソースです。[Office 365 のビデオ ネットワークについての詳細を表示](https://support.office.com/article/Office-365-Video-networking-Frequently-Asked-Questions-FAQ-2bed67a1-4052-49ff-a4ce-b7e6530eb98e)します。<br/> |

アプリケーションの種類と FQDN が[Office 365 の端点の資料](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2)のマイクロソフトのピアリングを使用して利用可能な Office 365 の機能一覧です。テーブルで、FQDN を使用する理由は、PAC ファイルまたはその他のプロキシ構成を使用してトラフィックを管理するには、PAC などの[Office 365 エンドポイントを管理する](https://aka.ms/manageo365endpoints)ファイルへのガイドを参照してお客様をできるようにすることです。
  
状況によっては 1 つまたは複数のサブ Fqdn がより高いレベルのワイルドカード ドメインとは異なる提供、ワイルドカード ドメインを使用しました。これは、ワイルドカードは、サーバーすべてに提供されている ExpressRoute とインターネットの間、インターネット、またはその逆に先の小さなサブのセットが提供されるだけの長いリストを表す場合に通常発生します。どこが異なっているかを理解するのには以下の表を参照してください。
  
このテーブルには、インターネットにのみ提供されている sub Fqdn と共に Azure ExpressRoute とインターネットの両方にワイルドカード提供されている Fqdn が表示されます。

|**ワイルドカード ドメインは、ExpressRoute とインターネット回線を提供**|**サブ FQDN は、インターネット回線のみを提供**|
|:-----|:-----|
|\*。 microsoftonline.com  <br/> |click.email.microsoftonline.com  <br/> portal.microsoftonline.com  <br/> provisioningapi.microsoftonline.com  <br/> adminwebservice.microsoftonline.com  <br/> |
|\*。 officeapps.live.com  <br/> |nexusRules.officeapps.live.com  <br/> nexus.officeapps.live.com  <br/> odc.officeapps.live.com  <br/> odc.officeapps.live.com  <br/> cdn.odc.officeapps.live.com  <br/> ols.officeapps.live.com  <br/> ocsredir.officeapps.live.com  <br/> ocws.officeapps.live.com  <br/> ocsa.officeapps.live.com  <br/> |

ネットワーク要求を ExpressRoute に送信する PAC ファイルは、通常回路に直接エンドポイントとプロキシを他のすべてのネットワーク要求を提供します。このような PAC ファイルを構成した場合は、次の順序で PAC ファイルを作成します。
  
1. プロキシへのトラフィックを送信する、PAC ファイルの上部には、上記の表に 2 つの列からサブの Fqdn が含まれます。[Office 365 エンドポイントを管理する](https://aka.ms/manageexpressroute365)上の記事で使用するサンプルの PAC ファイルを開発しています。

2. ExpressRoute 回路に直接トラフィックを送信する最初のセクションでは、以下[この資料](https://aka.ms/o365endpoints)で提供された ExpressRoute にマークされているすべて Fqdn が含まれます。

3. その他のネットワーク エンドポイントまたはプロキシへのトラフィックを送信するこれら 2 つのエントリを以下のルールが含まれます。

このテーブルには、Azure の ExpressRoute に提供されている sub Fqdn と共にのみインターネット回線とインターネット回線を提供されているワイルドカードのドメインが表示されます。PAC ファイル [2] 列に、Fqdn の上に、テーブルの下にこれらのファイル内のエントリの 2 番目のグループに追加すると、ExpressRoute を参照、リンクで提供されていると記載されています。

|**ワイルドカード ドメインは、インターネット回線のみを提供**|**サブ FQDN は、ExpressRoute とインターネット回線を提供**|
|:-----|:-----|
|\*。 office.com  <br/> |\*。 outlook.office.com  <br/> home.office.com  <br/> outlook.office.com  <br/> portal.office.com  <br/> www.office.com  <br/> |
|\*。 office.net  <br/> |agent.office.net  <br/> |
|\*。 office365.com  <br/> |outlook.office365.com  <br/> smtp.office365.com  <br/> |
|\*。 outlook.com  <br/> |\*。 protection.outlook.com  <br/> \*。 mail.protection.outlook.com  <br/> 自動検出・\<テナント\>. outlook.com  <br/> |
|\*。 準備完了  <br/> |login.windows.net  <br/> |

## <a name="routing-office-365-traffic-over-the-internet-and-expressroute"></a>ExpressRoute、インターネット経由で Office 365 のトラフィックをルーティング

Office 365 にルーティングするには、任意のアプリケーションがいくつかの重要な要因を決定する必要があります。
  
1. アプリケーション帯域幅の量が必要です。既存の使用率をサンプリングは、組織内でこれを決定する唯一の確実な方法です。

2. ネットワーク トラフィックをするどのような出口の場所からネットワークのままにします。パフォーマンスに影響を与えるこれは、Office 365 への接続のネットワーク ・ レーテンシーを最小限に抑える計画する必要があります。ビジネス用の Skype は、リアルタイムの音声およびビデオを使用するため、特に、不適切なネットワークの遅延が発生しやすいです。

3. すべてまたはサブセットの ExpressRoute を活用するのには、ネットワーク上の場所の場合。

4. どのような場所は、選択したネットワーク プロバイダーから ExpressRoute が提供しています。

これらの質問に対する回答を確認した後は、帯域幅と保存場所のニーズを満たす ExpressRoute の回路をプロビジョニングできます。について以上のネットワークでは、 [Office 365 のネットワーク ガイドの調整](https://aka.ms/tune)と[パフォーマンスの計画を Microsoft のハンドルがネットワーク上のケース ・ スタディ](https://aka.ms/tunemsit)を参照してください。
  
### <a name="example-1-single-geographic-location"></a>例 1: 1 つの地理的な場所
  
次の使用例は、シナリオは架空の会社 Trey Research と呼ばれる 1 つの地理的な場所を持っているのです。
  
Trey Research 社の従業員は、サービスとセキュリティ部門は、企業ネットワークと ISP の間に位置する発信プロキシのペアに明示的に許可されるインターネット上の web サイトへの接続にのみ許可されます。
  
Trey Research では、Office 365 の Azure ExpressRoute を使用することを計画し、コンテンツ配信ネットワークへのトラフィックなどのいくつかのトラフィックを Office 365 の接続の ExpressRoute 経由でルーティングすることができないことを認識します。以降、すべてのトラフィック既にプロキシ デバイスにルート既定では、これらの要求は引き続き、同様に機能します。Trey Research では、Azure ExpressRoute ルーティング要件を満たしていることを判断、進行状況が、接続を作成するには、ルーティング、および新しい ExpressRoute 回線を仮想ネットワークにリンクを構成します。適切な基本的な Azure ExpressRoute 構成を行った後は、Trey Research は[2 PAC ファイルを公開して](https://aka.ms/manageo365endpoints#ID0EACAAA=2._Proxies)トラフィックをルーティングする顧客の特定のデータを直接 ExpressRoute 経由で Office 365 の接続の。
  
次の図のように、Trey Research はルーティングと発信のプロキシ構成の変更の組み合わせを使用して ExpressRoute 経由でインターネットとのトラフィックのサブセットを Office 365 のトラフィックをルーティングするための要件を満たすために。
  
1. Azure ExpressRoute の独立したインターネットの出口ポイントを経由のトラフィックをルーティングする[2 PAC ファイルの公開](https://aka.ms/manageo365endpoints#ID0EACAAA=2._Proxies)を使用して、Office 365 の。

2. クライアントは、Trey Research のプロキシへの既定のルートで構成されます。

この例のシナリオでは、Trey Research は、アウト バウンド プロキシ デバイスを使用しています。同様に、Office 365 の Azure ExpressRoute を使用していないお客様は大量の既知のエンドポイントへのトラフィックを検査することのコストに基づいてトラフィックをルーティングするには、この手法を使用する場合があります。
  
最高ボリュームのオンラインの Exchange、SharePoint Online では、オンライン ビジネスの Skype の Fqdn 次のとおりです。
  
![ExpressRoute お客様のネットワークのエッジ](media/dab8cc42-b1d6-46d6-b2f6-d70f9e16d5ea.png)
  
- outlook.office365.com、outlook.office.com

- \<テナント名\>です sharepoint.com、\<テナント名\>-my.sharepoint.com、\<テナント名\>-\<アプリケーション\>です。 sharepoint.com。

- \*.TCP 以外のトラフィック用の IP の範囲と Lync.com

- \*broadcast.officeapps.live.com、 \*excel.officeapps.live.com、 \*onenote.officeapps.live.com、 \*powerpoint.officeapps.live.com、 \*view.officeapps.live.com、 \*visio.officeapps.live.com、 \*word の edit.officeapps.live.com、\*語 view.officeapps.live.com、office.live.com

[展開して Windows 8 でのプロキシ設定を管理して](https://blogs.technet.com/b/deploymentguys/archive/2013/05/08/windows-8-supporting-proxy-services-with-static-configurations-web-hosted-pac-files-and-domain-policy-configured-proxy.aspx)詳細[のプロキシによって調整されていない Office 365 のことを確認](https://blogs.technet.com/b/onthewire/archive/2014/03/28/ensuring-your-office-365-network-connection-isn-t-throttled-by-your-proxy.aspx)します。
  
ExpressRoute 回線、1 つでは、Trey Research の高可用性はありません。ExpressRoute 接続を処理しているエッジ ・ デバイスの Trey の冗長ペアが失敗すると、イベントはありませんへのフェイル オーバーの他の ExpressRoute 回路。これにより、Trey Research の状況でインターネットへのフェイル オーバーは手動の再設定を必要とし、場合によっては新しい IP アドレスとします。Trey は、高可用性を追加する必要がある場合は、場所ごとに追加の ExpressRoute 回路を追加し、アクティブ/アクティブ状態で回路を構成する最も簡単なソリューションです。
  
## <a name="routing-expressroute-for-office-365-with-multiple-locations"></a>複数の場所に Office 365 にルーティングの ExpressRoute

最後のシナリオでは、ExpressRoute 経由での Office 365 のトラフィックのルーティングより複雑なルーティングのアーキテクチャの基盤です。場所の数、それらの場所が存在する大陸の数、ExpressRoute の回路の数に関係なく ExpressRoute 経由でインターネットとある程度のトラフィックにいくつかのトラフィックをルーティングすることがされている必要があります。
  
複数の地域で複数の場所でお客様に回答する必要がありますその他の質問は次のとおりです。
  
1. すべての場所で、ExpressRoute の回路を必要とするでしょうか。ビジネス オンラインの Skype を使用した場合、または SharePoint Online または Exchange Online の遅延感度に不安がある場合、アクティブ/アクティブの ExpressRoute 回路の冗長ペアはそれぞれの場所でお勧めします。Skype のビジネス メディアの品質とネットワーク接続性ガイド」の詳細を参照してください。

2. ExpressRoute 回路が特定の地域で利用できない場合は Office 365 の宛てのトラフィック ルーティングする方法ですか。

3. 場合は多くの小さな場所でのネットワーク トラフィックを統合することに適した方法とは何ですか。

これらの各は、マイクロソフトから利用できるオプションと同様に、独自のネットワークを評価する必要がある独自の課題を説明します。

|**考慮事項**|**ネットワークのコンポーネントを評価するには**|
|:-----|:-----|
|複数の場所で回路  <br/> |最低 2 つの回路がアクティブ/アクティブのような構成のことをお勧めします。  <br/> コスト、遅延時間、および帯域幅のニーズを比較する必要があります。  <br/> 複数回線でのルーティングを管理するために BGP 経路のコスト、PAC ファイル、および NAT を使用します。  <br/> |
|離れた場所に、ExpressRoute 回路からルーティング  <br/> |出口と Office 365 の要求を開始する人に近いと、DNS の解像度をお勧めします。  <br/> 適切なエンドポイントを検出するのにはリモート ・ オフィスを許可するのには、DNS の転送を使用できます。  <br/> リモート オフィスのクライアントには、ExpressRoute 回路へのアクセスを提供する使用可能なルートが必要です。  <br/> |
|小規模オフィスの統合  <br/> |使用可能な帯域幅とデータの使用状況を入念に比較する必要があります。  <br/> |

> [!NOTE]
> マイクロソフトが物理的な場所に関係なく、ルートがある場合は、インターネット上で ExpressRoute を好みます。
  
これらの考慮事項の各は、各一意のネットワークに考慮する必要があります。例を次に示します。
  
### <a name="example-2-multi-geographic-locations"></a>例 2: 複数の地域
  
次の使用例は、複数の地理的な場所を持っている正しいという架空の会社のシナリオです。
  
ホタルは、世界中のオフィスを持つ地理的に分散しています。ネットワークに直接接続で、Office 365 のトラフィックの大半を保持するのには Office 365 の Azure ExpressRoute を実装します。ホタルは、他の 2 つの大陸にもオフィスを持っています。ExpressRoute は現実的でないリモート ・ オフィスの従業員は、ExpressRoute 接続を使用する主な機能の一方または両方にルーティングする必要があります。
  
基本原則では、マイクロソフトのデータ センターに送信される Office 365 のトラフィックをできるだけ迅速に取得します。この例では、正しい必要があるかどうかは、リモート ・ オフィスを経由の接続でかどうか、リモート ・ オフィスを Microsoft にアクセスする内部ネットワーク経由でルーティングする必要があります。 ので簡単に Microsoft データ センターにアクセスするインターネット経由でルーティングする必要があります。ExpressRoute 接続経由でデータ センター、できるだけ早くします。
  
マイクロソフトのデータ センター、ネットワーク、およびアプリケーションのアーキテクチャは、グローバルに分散した通信を行うし、可能な限り最も効率的な方法でそれらのサービスを提供する設計されています。これは、世界で最大規模のネットワークの 1 つです。必要以上に長くお客様のネットワークに残っている Office 365 に送信される要求はこのアーキテクチャを活用することはできません。
  
正しい保険の場合は、ExpressRoute を使用するアプリケーションによって進行する必要があります。いるビジネスのため、Skype オンライン顧客、またはビジネス オンラインのメディアの品質とネットワークの Skype で推奨されるデザイン、ビジネスのオンライン会議に外部 Skype に接続するときに ExpressRoute の接続を活用する場合の例接続性ガイドでは、3 番目の場所の他の ExpressRoute の回路を準備します。ネットワークの観点から高価な可能性があります。ただし、ルーティングは、要求 1 つの大陸から別にマイクロソフトのデータ センターに提供することがありますが低下または使用不能の経験 Skype 中にオンライン ビジネスの会議やコミュニケーションの前にします。
  
正しいが使用されていないか、オンライン ビジネスのどのような方法で Skype を活用する計画は、接続可能性があります、ExpressRoute の大陸に Office 365 の送信ネットワーク トラフィックをルーティング可能なも場合があります不必要な遅延または TCP混雑します。どちらの場合も、ルーティング インターネットのコンテンツ配信ネットワークを Office 365 を利用するのにはローカル ・ サイトでインターネットに送信されるトラフィックをお勧めに依存しています。
  
![ExpressRoute 複数の地理的な](media/98fdd883-2c5a-4df7-844b-bd28cd0b9f50.png)
  
正しいが、複数の地理的な戦略を計画するときは、多くの回路、回路、フェイル オーバーの数のサイズを考慮することがあります。
  
回路を使用する複数の領域を持つ 1 つの場所で ExpressRoute で正しいが、リモート ・ オフィスから Office 365 への接続は、本社に最も近い Office 365 のデータ センターに送信され、受信されることを確認するのには、本社所在地です。これを行うには、正しいは、ラウンド トリップとバック オフィスのインターネットの出口ポイントに最も近い Office 365 環境で適切な接続を確立するために必要な DNS 参照の数を減らすために DNS の転送を実装します。これは、クライアントがローカルのフロント エンド サーバーを解決することを防止され、正しい、ピアリング マイクロソフト本社の近くにユーザーが接続するフロント エンド サーバーでは。[条件付きフォワーダーのドメイン名を割り当てる](https://technet.microsoft.com/library/Cc794735%28v=WS.10%29.aspx)には参照することができます。
  
このシナリオでは、リモート ・ オフィスからのトラフィックは北アメリカで Office 365 のフロント エンドのインフラストラクチャを解決するには、Office 365 アプリケーションのアーキテクチャによってバックエンド サーバーに接続するのには Office 365 の活用たとえば、Exchange Online は北アメリカでの接続を終了し、テナントが存在していた場所にこれらのフロント エンド サーバーがバックエンド メールボックス サーバーに接続します。すべてのサービスでは、ユニキャストと anycast 先で構成されています前面ドアを広範囲に分散されたサービスが存在します。
  
Humongous では、複数の大陸に主要なオフィスが含まれる場合は、オンライン ビジネスの Skype などの機密性の高いアプリケーションの待ち時間を減らすために地域ごとの 2 つのアクティブ/アクティブ回路の最小が推奨されます。すべてのオフィスでは、1 つの大陸では、または、リアルタイムのコラボレーションを使用していない、ポイント統合データベースまたは分散型の出口は、お客様の特定の意思決定。複数の回線が使用できる場合は、BGP ルーティングにより、フェイル オーバーする必要があります 1 つの回路は、使用できなくなります。
  
サンプルの[ルーティング構成](https://azure.microsoft.com/documentation/articles/expressroute-config-samples-routing/)の詳細については、 [https://azure.microsoft.com/en-us/documentation/articles/expressroute-config-samples-nat/](https://azure.microsoft.com/documentation/articles/expressroute-config-samples-nat/)。
  
## <a name="selective-routing-with-expressroute"></a>ExpressRoute でのルーティング オプションを選択

ExpressRoute で選択したルーティングできなくなるさまざまな理由から、テスト、一部のユーザーに ExpressRoute を展開します。顧客が選択的に ExpressRoute 経由で Office 365 のネットワーク トラフィックをルーティングに使用するさまざまなツールがあります。
  
1. **ルートのフィルター処理と分離**のサブネットやルーターの一部に ExpressRoute 経由で Office 365 に BGP 経路を許可します。これは、お客様のネットワーク セグメントまたは物理的なオフィスの場所を選択的にルーティングします。これは一般に、Office 365 の ExpressRoute のロールアウトが膨大であり、BGP デバイスで構成されています。

2. **PAC ファイルまたは Url**から Office 365 を指示するには、fqdn では特定のパスにルーティングするのには特定のネットワーク トラフィックが送信されます。[PAC ファイルの配置](https://aka.ms/manageo365endpoints#ID0EACAAA=2._Proxies)によって識別されるように選択的にクライアント コンピューターでルーティングします。

3. **ルート フィルター** - [ルート フィルター](https://docs.microsoft.com/azure/expressroute/how-to-routefilter-portal)は、マイクロソフトのピアリングによってサポートされているサービスのサブセットを使用する方法です。

4. **BGP コミュニティ**- [BGP コミュニティ タグ](https://aka.ms/bgpexpressroute365)に基づいてフィルタ リングは、特定の Office 365 アプリケーションが ExpressRoute を通過し、インターネット上をスキャンする、顧客を使用できます。

戻るを使用することができます短いリンクを以下に示します。[https://aka.ms/erorouting](https://aka.ms/erorouting)
  
## <a name="related-topics"></a>関連項目

[Office 365 へのネットワーク接続](network-connectivity.md)
  
[Office 365 向け Azure ExpressRoute](azure-expressroute.md)
  
[Office 365 向け ExpressRoute の管理](managing-expressroute-for-connectivity.md)
  
[Office 365 向け ExpressRoute でのネットワーク計画](network-planning-with-expressroute.md)
  
[Office 365 向け ExpressRoute での実装](implementing-expressroute.md)
  
[メディアの品質とオンライン ビジネスの Skype でのネットワーク接続のパフォーマンス](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[Skype のオンライン ビジネスのネットワークを最適化します。](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)
  
[ExpressRoute とオンライン ビジネスの Skype での QoS](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[ExpressRoute を使用して通話フロー](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[ExpressRoute に BGP のコミュニティを使用して Office 365 シナリオ](bgp-communities-in-expressroute.md)
  
[ベースラインとパフォーマンス履歴を使用した、Office 365 のパフォーマンスのチューニング](performance-tuning-using-baselines-and-history.md)
  
[Office 365 のパフォーマンスに関するトラブルシューティングの計画](performance-troubleshooting-plan.md)
  
[Office 365 の URL と IP アドレス範囲](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Office 365 のネットワークとパフォーマンスの調整](network-planning-and-performance.md)
